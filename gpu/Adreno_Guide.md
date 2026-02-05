
## References

1. [Qualcomm Snapdragon Mobile Platform OpenCL General Programming and Optimization](https://developer.qualcomm.com/qfile/33472/80-nb295-11_c.pdf)
2. [Game Developer Guides](https://developer.qualcomm.com/sites/default/files/docs/adreno-gpu/developer-guide/gpu/gpu.html), [[webarchive](https://web.archive.org/web/20220104180856/https://developer.qualcomm.com/sites/default/files/docs/adreno-gpu/developer-guide/gpu/gpu.html)]

**Wiki/Specs**<br/>
1.1. [Wikipedia](https://en.wikipedia.org/wiki/Adreno)<br/>
1.2. [Namu wiki](https://en.namu.wiki/w/%ED%80%84%EC%BB%B4%20Adreno%20GPU)<br/>

**Hardware details**<br/>
2.1. [Mesa driver details](https://docs.mesa3d.org/drivers/freedreno.html)<br/>
2.2. [Low Resolution Z Buffer support on Turnip (2021)](https://blogs.igalia.com/siglesias/2021/04/19/low-resolution-z-buffer-support-on-turnip/)<br/>
2.3. [Low-resolution-Z on Adreno GPUs](https://blogs.igalia.com/dpiliaiev/adreno-lrz/)<br/>


## Notes

* Avoid discarding pixels in the fragment shader. [2]
	- In theory, if all pixels in a thread are killed, the GPU will stop processing that thread as soon as possible. In practice, discard operations can disable hardware optimizations.

* Avoid texture fetches in vertex shaders. [2]

* Prefer uniform buffers over shader storage buffers. [2]
	- This is true if the Uniform Buffer Objects are statically indexed in GLSL and are small enough that the driver or compiler can map them into the same hardware constant RAM that is used for the default uniform block uniforms.

* Keep UBOs as small as possible. [2]
	- UBOs which can fit in the 8k of constant memory will perform better than larger UBOs where each wave has to fetch from main memory.

* Sample textures in an efficient way. [2]
	- Avoid random access – Hardware operates on blocks of 2x2 fragments, so the shaders are more efficient if they access neighboring texels within a single block.
	- Avoid 3D textures – Fetching data from volume textures is expensive owing to the complex filtering that needs to be performed to compute the result value.
	- Limit the number of textures sampled from shaders – Usage of four samplers in a single shader is acceptable, but accessing more textures in a single shader stage could lead to performance bottlenecks.
	- Compress all textures – This allows better memory usage, translating to a lower number of texture stalls in the rendering pipeline.
	- Consider using mipmaps – Mipmaps help to coalesce texture fetches and can help improve performance at the cost of increased memory usage.

* What causes LRZ to be disabled: [2]
	- Writing depth in fragment shader
	- Any condition where direct rendering is required
	- Use of secondary command buffers (Vulkan) (Snapdragon 865 and newer will not disable LRZ based on this criteria)
	- Since LRZ is an early depth test, such test cannot be used when late-z is required. [2.1]
	- LRZ buffer could be formed only in one direction, changing depth comparison directions without disabling LRZ would lead to a malformed LRZ buffer. [2.1]
	- In tests LRZ shows 10% loss in back to front draw order even on small triangles. [[ref](https://github.com/azhirnov/AsEn-ShaderEditor/blob/main/papers/GeometryCulling-en.md#hardware-optimization)]

* LRZ:
	- The interesting part of this feature is that it allows applications to submit the vertices in any order. [2.1]
	- A Low Resolution Z (LRZ) pass is also referred to as draw order independent depth rejection. During the binning pass, a low resolution Z-buffer is constructed, and can reject LRZ-tile wide contributions to boost binning performance. This LRZ is then used during the rendering pass to reject pixels efficiently before testing against the full resolution Z-buffer. [2.1]
	- LRZ always uses Z16_UNORM. [2.1]
	- if depth comparison direction is GREATER - LRZ stores the lowest depth value of the block of pixels, if direction is LESS - it stores the highest value of the block. [2.3]
	- VK_COMPARE_OP_GREATER and VK_COMPARE_OP_GREATER_OR_EQUAL have same direction. [2.3]
	- VK_COMPARE_OP_LESS and VK_COMPARE_OP_LESS_OR_EQUAL have same direction. [2.3]
	- VK_COMPARE_OP_EQUAL and VK_COMPARE_OP_NEVER don’t have a direction, LRZ is temporally disabled. [2.3]
	- VK_COMPARE_OP_ALWAYS and VK_COMPARE_OP_NOT_EQUAL either temporally or completely disable LRZ, depending on depth being written. [2.3]

* LRZ per A650 (before gen3): [2.1]
	- The direction is fully tracked on CPU. In render pass LRZ starts with unknown direction, the direction is set first time when depth write occurs and if it does change afterwards then the direction becomes invalid and LRZ is disabled for the rest of the render pass.
	- Since the direction is not tracked by the GPU, it’s impossible to know whether LRZ is enabled during construction of secondary command buffers. For the same reason, it’s impossible to reuse LRZ between render passes.

* LRZ on A650+ (gen3+): [2.1]
	- LRZ direction can be tracked on GPU.
	- LRZ can be reused between render passes.

* LRZ on A7xx: [2.1]
	- introduces the concept of bidirectional LRZ where there are two LRZ buffers, one for each direction.

* LRZ Feedback: [2.1]
	- Some draws do write depth but cannot contribute to LRZ during the BINNING pass e.g. when fragment shader has “discard” in it, however they can contribute to LRZ during the RENDERING pass via LRZ feedback mechanism.

* Universal bandwidth compression. [2]<br/>
Universal bandwidth compression (UBWC) is supported by all A5x GPUs. UBWC is a unique predictive bandwidth compression scheme that improves effective throughput to system memory. By minimizing the bandwidth of data, significant power savings can be achieved.<br/>
UBWC works across many components in Snapdragon processors including GPU, Display, Video, and Camera. The compression supports YUV and RGB formats, and reduces memory bottlenecks.

* It is recommended to use VK_DESCRIPTOR_TYPE_COMBINED_IMAGE_SAMPLER because of how the Adreno GPU works with Bindless mode. When using a combined image sampler, the GPU can use Bindless mode which is more performant. When using separate samplers, it will fall back to a slower mode. Performance deltas have shown a decrease by 2-5% in the fill rate for separate samplers. [2]

* What is the recommended usage SSBO vs. UBO vs. Texture fetch. [2]
	- Never use descriptor types or STORAGE_BUFFER or STORAGE_IMAGE if the shader usage is “Read-only”. Reading data from SSBOs or Image buffers effectively become texture fetches so performance/latency would be similar.
	- There are 8k of constant memory per SP so reading from UBOs which fit within that 8k would perform better than SSBOs or Images. However, the situation shifts if UBO data is larger than 8k since UBO data will be read directly from system memory by each wave without the benefit of the texture cache which SSBOs and Images would have.

* Push constants: [2]
	- On A5X, GPUs push constants are not recommended.
	- Hardware changes on A6X GPUs resolved many of the issues, and push constants will perform better when used with frequently changing data.

* RGB10_A2 format is faster than FP16. [2]
* ASTC is compressed in L2 and decompressed in L1. ETC formats stay compressed in L1. [2]

* What depth buffer format provides the best performance? [2]<br/>
When possible, use D16. If more precision is needed and a stencil is not used, it is recommended to use D32 as D24. D24_S8 will take the same space as D32 in GMEM with less precision. Otherwise D24_S8 is a recommended as well. All these formats are supported by UBWC.

* What is the behavior on dynamic branching in fragment shaders? [2]<br/>
The wave will stall until every thread in it is ready to progress. Once every thread is ready, both branches are taken. The results are a selection using the mask generated from the branch.

* What is the performance of user clip planes? [2]<br/>
Bad. The one (1) prim/clock will turn into 50 cycles if you must clip the primitive. It will also stall the entire pipe.

* Which is better: vertex stream or attribute fetching in VS? [2]<br/>
Vertex stream is preferred. Adreno GPUs have specialized hardware for fetch and decode of these.

* FP16 inverse squareroot is 2x faster than FP32.

