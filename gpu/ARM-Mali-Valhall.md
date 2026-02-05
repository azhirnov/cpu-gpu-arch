Valhall is a 4th generation of Mali GPU architecture.

Content:
* [Gen1](#Valhall-Gen1)
* [Gen2](#Valhall-Gen2)
* [Gen3](#Valhall-Gen3)
* [Gen4](#Valhall-Gen4)
* [All gens](#Valhall-(all-gens))


# Valhall Gen1

## Examples

* Mali-G57
* Mali-G77

## References

1.1. [Arm's New Mali-G77 & Valhall GPU Architecture](https://www.anandtech.com/show/14385/arm-announces-malig77-gpu)<br/>
1.2. [Arm Mali-G77 Performance Counters Reference Guide](https://developer.arm.com/documentation/102730/latest/), [[backup](../pdf/arm-mali-g77_performance_counters_reference_guide_102730_0106_en.pdf)]<br/>
1.3. [Vulkan features for Mali-G57](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G57)<br/>
1.4. [Mali-G57 Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench-gpu/ARM_Mali_G57.md)<br/>

## Notes

* 2 work queues: non-fragment, fragment. [1.2]
* fragment density map

* One subgroup can fill multiple triangles, but only with the same instanceIndex. [1.4]
* AFBC new formats: [1.4]
	- B10G11R11_UFLOAT_PACK32
	- RG16F
	- RG16_UNorm

* core config [4]:
	- 2 ALU
	- 128 fp16/cy (64 per ALU)
	- 64 fp32/cy (32 per ALU)
	- 2 frag/cy
	- 2 pix/cy
	- 4 tex/cy

* Tile size: [1.4]
	- 16x16 if <= 256 bits per pixel
	- 16x8  if <= 512 bpp
	- 8x8   if > 512 bpp


# Valhall Gen2

## Examples

* Mali-G68
* Mali-G78

### SoC
* Google Tensor (Mali-G78 MP20)

## References

2.1. [Arm Announces The Mali-G78 GPU](https://www.anandtech.com/show/15816/arm-announces-the-malig78-evolution-to-24-cores)<br/>
2.2. [Mali-G78 Performance Counters Reference Guide](https://developer.arm.com/documentation/102626/0100), [[backup](../pdf/arm-mali-g78_performance_counters_reference_guide_102626_0106_en.pdf)]<br/>
2.3. [Vulkan features for Mali-G78](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G78)<br/>
2.4. [Reverse-engineering the Mali G78](https://www.collabora.com/news-and-blog/news-and-events/reverse-engineering-the-mali-g78.html)<br/>

## Notes

* VK_ARM_rasterization_order_attachment_access
* core config [4]:
	- 2 ALU
	- 128 fp16/cy (64 per ALU)
	- 64 fp32/cy (32 per ALU)
	- 2 frag/cy
	- 2 pix/cy
	- 4 tex/cy

* Mali-G78 MP20 VK_ARM_shader_core_builtins, VK_ARM_shader_core_properties [2.3]:
	- shaderCoreCount: 20
	- shaderWarpsPerCore: 32 -- maximum number of simultaneously executing warps on a shader core
	- fmaRate: 32 -- maximum number of single-precision fused multiply-add operations per clock per shader core.
	- pixelRate: 2 -- maximum number of pixels output per clock per shader core.
	- texelRate: 4 -- maximum number of texels per clock per shader core.


# Valhall Gen3

## Examples

* Mali-G310
* Mali-G510
* Mali-G610
* Mali-G710

### SoC
* Rockchip RK 3588 (Mali-G610 MC4)
* Google Tensor G2 (Mali-G710 MP7)

## References

3.1. [Arm Mali-G610 Performance Counters Reference Guide](https://developer.arm.com/documentation/102812/0108/), [[backup](../pdf/arm-mali-g610_performance_counters_reference_guide_102812_0107_en.pdf)]<br/>
3.2. [Arm Announces New Mali-G710, G610, G510 & G310 Mobile GPU Families](https://www.anandtech.com/show/16694/arm-announces-new-malig710-g610-g510-g310-mobile-gpu-families)<br/>
3.3. [Mali-G510](https://developer.arm.com/Processors/Mali-G510)<br/>
3.4. [Vulkan features for Mali-G710](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G710), [G710 MC10](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G710%20MC10), [G610](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G610), [G610 MC6](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G610%20MC6)<br/>
3.5. [Vulkan subpasses: the good, the bad, and the ugly](https://developer.arm.com/community/arm-community-blogs/b/mobile-graphics-and-gaming-blog/posts/vulkan-subpasses-the-good-the-bad-and-the-ugly)<br/>

## Notes

* G610, G710 L2 cache: Configurable 512KB – 2MB, 2 or 4 slices of 256K or 512K
* Scalability: 7 to 16 cores

* Added Command Stream Front-end (CSF) instead of Job Manager.
* 3 hardware work queues: compute, vertex, fragment.
* Arm Fixed Rate Compression (AFRC), 4x4 block lossy compression for textures and framebuffer. [3.3]

* All RGBA16 formats are compatible with AFBC. [3]

* 128 GFlops per core at 1000MHz

* G710 core config [4]:
	- 4 ALU
	- 256 fp16/cy (64 per ALU)
	- 128 fp32/cy (32 per ALU)
	- 4 frag/cy
	- 4 pix/cy
	- 8 tex/cy

* Mali-G710 MP7 VK_ARM_shader_core_builtins, VK_ARM_shader_core_properties [3.4]:
	- shaderCoreCount: 7
	- shaderWarpsPerCore: 64 -- maximum number of simultaneously executing warps on a shader core
	- fmaRate: 64 -- maximum number of single-precision fused multiply-add operations per clock per shader core.
	- pixelRate: 4 -- maximum number of pixels output per clock per shader core.
	- texelRate: 8 -- maximum number of texels per clock per shader core.


# Valhall Gen4

## Examples

* Mali-G615
* Mali-G715
* Immortalis-G715

### SoC
* Google Tensor G3, G4 (Mali-G715 MP7)

## References

4.1. [Arm Mali-G615 Performance Counters Reference Guide](https://developer.arm.com/documentation/107775/0106), [[backup](../pdf/arm-mali-g615_performance_counters_reference_guide_107775_0105_en.pdf)]<br/>
4.2. [The Valhall Shader Core](https://developer.arm.com/documentation/102203/0100/Fourth-generation-Mali-GPU-architecture), [[backup](../pdf/ARM-the_valhall_gen4_shader_core_guide_102203_0100_03_en.pdf)]<br/>
4.3. [Vulkan features for Mali-G715](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G715), [Mali-615 MC6](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G615%20MC6)<br/>

## Notes

* The FMA and SVT pipelines are 16-wide, the SFU pipeline is 4-wide and runs at one quarter of the throughput of the other two. [4.2]
* Valhall maintains native support for int8, int16, and fp16 data types. These data types can be packed using SIMD instructions to fill each 32-bit data processing lane. This arrangement maintains the power efficiency and performance that is provided by the types that are narrower than 32-bits. [4.2]
* A single 16-wide warp maths unit can therefore perform 32x fp16/int16 operations per clock cycle, or 64x int8 operations per clock cycle. [4.2]
* Fragment shading rate (VRS)
* Cooperative matrix support on Google Tensor. [4.3]

## Specs

* LSU: [4.2]
	- 64-byte cache line.
	- 16KB L1 data cache per core
	- Warp unit accesses are optimized to reduce unique cache access requests. Data can be returned in a single cycle if all threads access data inside the same cache line.
* varying unit can interpolate 32 bits for every thread in a warp. [4.2]
* Variable rate shading (VRS).

* G715 core config [4]:
	- 4 ALU
	- 512 fp16/cy (128 per ALU)
	- 256 fp32/cy (64 per ALU)
	- 4 frag/cy
	- 4 pix/cy
	- 8 tex/cy

* Mali-G715 MP7 VK_ARM_shader_core_builtins, VK_ARM_shader_core_properties [4.3]:
	- shaderCoreCount: 7
	- shaderWarpsPerCore: 64 -- maximum number of simultaneously executing warps on a shader core
	- fmaRate: 128 -- maximum number of single-precision fused multiply-add operations per clock per shader core.
	- pixelRate: 4 -- maximum number of pixels output per clock per shader core.
	- texelRate: 8 -- maximum number of texels per clock per shader core.

* Mali-G615 MC6 VK_ARM_shader_core_builtins, VK_ARM_shader_core_properties [4.3]:
	- shaderCoreCount: 6
	- shaderWarpsPerCore: 64 -- maximum number of simultaneously executing warps on a shader core
	- fmaRate: 128 -- maximum number of single-precision fused multiply-add operations per clock per shader core.
	- pixelRate: 4 -- maximum number of pixels output per clock per shader core.
	- texelRate: 8 -- maximum number of texels per clock per shader core.


# Valhall (all gens)

## References

1. [Instruction Set Architecture](https://rosenzweig.io/Valhall-Documentation.pdf), [[backup](../pdf/ARM-Valhall-Documentation.pdf)]
2. [Mesa driver details](https://docs.mesa3d.org/drivers/panfrost.html)
3. [Arm GPU Best Practices Developer Guide](https://developer.arm.com/documentation/101897/latest/), [[backup](../pdf/arm-gpu_best_practices_developer_guide_3_3.pdf)]
4. [Arm GPU Datasheet](https://developer.arm.com/documentation/102849/0700/), [[backup](../pdf/Arm-GPU_datasheet_v7.pdf)]
5. [PanCSF: A new DRM driver for Mali CSF-based GPUs](https://www.collabora.com/news-and-blog/news-and-events/pancsf-a-new-drm-driver-for-mali-csf-based-gpus.html)
6. [Writing an open source GPU driver - without the hardware](https://www.collabora.com/news-and-blog/blog/2022/01/27/writing-an-open-source-gpu-driver-without-the-hardware/)
7. [reverse-engineered Mali Valhall ISA](https://gitlab.freedesktop.org/panfrost/valhall-docs/-/blob/main/Overview.md)


## Notes

* scalar
* 16 threads per warp. [1.2, 4.2]
* Fragment Task with 32x32 pixels region. [1.2]
* MSAA: 4x, 8x, 16x
* AFBC (v1.3) with 4x4 block.
* Transaction Elimination with 16x16 pixel block size.

* All Valhall GPU cores implement a 4 texel-per-clock and 2 pixel-per-clock shader core.
* Mali Valhall GPU shader cores allow variable numbers of threads to be created, depending on the number of work registers that are used by the in-flight shader programs.
	- 0-32 registers - Maximum thread capacity
	- 33-64 registers - Half thread capacity
* A Valhall core can perform 32 FP32 FMAs, read 4 bilinear filtered texture samples, blend 2 fragments, and write 2 pixels per clock. [4.2]

* Each Processing Engine (PE) executes the programmable shader instructions. [4.2]
* Each PE includes 3 arithmetic processing pipelines: [4.2]
	- FMA pipeline with is used for complex maths operations
	- CVT pipeline which is used for simple maths operations
	- SFU pipeline which is used for special functions

* Has accelerated hardware blending for FP16 and R11G11B10 formats. Simple blends of those formats are accelerated, but advanced blends (logic/min/max) are not. [3]

* AFBC compatible with any 32 bit or smaller formats. [3]

* Branching:
	- Divergence of threads within a warp carries a performance penalty. Divergence is handled in hardware, but the compiler must insert some hints to ensure divergence is handled correctly. [7]
	- Indirect access to attributes and texture handles must not be divergent. If divergent access is required, the compiler must lower to an if-chain predicated on lane ID. [7]

* Texturing:
	- Usually, helper threads do not need to execute texture instructions once the level-of-detail has been selected. Skipping texturing on helper threads can save memory bandwidth. [7]
	- Texture projection is not supported. [7]

* Uniform/constant restrictions: [7]
	- An instruction may access no more than a single 64-bit uniform slot.
	- An instruction may access no more than 64-bits of combined uniforms and constants.
	- An instruction may only access uniforms in the default immediate mode.
	- An instruction may access no more than a single special immediate (e.g. lane_id).

