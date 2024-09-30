
## References

1. [Qualcomm Snapdragon Mobile Platform OpenCL General Programming and Optimization](https://developer.qualcomm.com/qfile/33472/80-nb295-11_c.pdf)
2. [Game Developer Guides](https://developer.qualcomm.com/sites/default/files/docs/adreno-gpu/developer-guide/gpu/gpu.html), [[webarchive](https://web.archive.org/web/20220104180856/https://developer.qualcomm.com/sites/default/files/docs/adreno-gpu/developer-guide/gpu/gpu.html)]

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

* Universal bandwidth compression. [2]<br/>
Universal bandwidth compression (UBWC) is supported by all A5x GPUs. UBWC is a unique predictive bandwith compression scheme that improves effective throughput to system memory. By minimizing the bandwidth of data, significant power savings can be achieved.<br/>
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


