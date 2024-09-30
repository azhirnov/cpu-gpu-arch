Bifrost is a 4th generation of Mali GPU architecture.

Content:
* [Gen1](#Bifrost-Gen1)
* [Gen2](#Bifrost-Gen2)
* [Gen3](#Bifrost-Gen3)
* [All gens](#Bifrost-(all-gens))

# Bifrost Gen1

## Examples

* Mali-G31
* Mali-G51
* Mali-G71

* Rockchip RK3326 (Mali-G31)

## References

1.1. [ARM Unveils Next Generation Bifrost GPU Architecture & Mali-G71](https://www.anandtech.com/show/10375/arm-unveils-bifrost-and-mali-g71)<br/>
1.2. [Arm Mali-G71 Performance Counters Reference Guide](https://developer.arm.com/documentation/102641/0106), [[backup](../pdf/arm_mali-g71_performance_counters_reference_guide_102641_0105_en.pdf)]<br/>
1.3. [Vulkan features for Mali-G71](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G71)<br/>

## Notes

* implement a single texel-per-clock and single pixel-per-clock shader core.
* G71: 4-wide SIMD per quad; 3x quads per core. 12 FMAs at the same time. These 3 quads are managed by a core's quad manager. [4]
* In both the Mali-G71 and G72, a quad is just that: a 4-wide SIMD unit, with each lane possessing separate FMA and ADD/SF pipes. [4]
* 128 bits per pixel of tile buffer color storage. [5]
* AFBC: [5]
	- G71: partial support
	- G31, G51: full support

# Bifrost Gen2

## Examples

* Mali-G52
* Mali-G72

* Rockchip RK3562, RK3566, RK3568 (Mali-G52-2EE)

## References

2.1. [ARM Announces Mali-G72](https://www.anandtech.com/show/11459/arm-announces-malig72-bifrost-refined-for-the-highend-soc)<br/>
2.2. [Arm Mali-G72 Performance Counters Reference Guide](https://developer.arm.com/documentation/102642/0106/), [[backup](../pdf/arm_mali-g72_performance_counters_reference_guide_102642_0106_en.pdf)]<br/>
2.3. [Mali-G52](https://developer.arm.com/Processors/Mali-G52)<br/>
2.4. [Vulkan features for Mali-G52](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G52)<br/>

## Notes

* implement a single texel-per-clock and single pixel-per-clock shader core.
* 256 bits per pixel of tile buffer color storage. [5]


# Bifrost Gen3

## Examples

* Mali-G76

## References

3.1. [Arm Mali-G76 Performance Counters Reference Guide](https://developer.arm.com/documentation/102697/latest/), [[backup](../pdf/arm_mali-g76_performance_counters_reference_guide_102697_0106_en.pdf)]<br/>
3.2. [Vulkan features for Mali-G76](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G76)<br/>

## Notes

* Implement a two texel-per-clock and two pixel-per-clock shader core, with an increase in arithmetic performance to compensate. Not every GPU doubled the available performance though.
* G76: 8-wide SIMD per quad, 3 quads per core. [4]
* AFBC full support [5]
* 8 threads per warp [3.1]


# Bifrost (all gens)

## References

1. [The Bifrost Shader Core](https://community.arm.com/developer/tools-software/graphics/b/blog/posts/the-mali-gpu-an-abstract-machine-part-4---the-bifrost-shader-core), [[backup](../pdf/the_bifrost_shader_core_102546_0100_02_en.pdf)]
2. [The Bifrost GPU architecture](https://old.hotchips.org/wp-content/uploads/hc_archives/hc28/HC28.22-Monday-Epub/HC28.22.10-GPU-HPC-Epub/HC28.22.110-Bifrost-JemDavies-ARM-v04-9.pdf)
3. [Mesa driver details](https://docs.mesa3d.org/drivers/panfrost.html)
4. [Everything we learnt from hacking Arm Mali GPUs](https://github.com/fxlin/mali)
5. [Arm GPU Best Practices Developer Guide](https://developer.arm.com/documentation/101897/latest/), [[backup](../pdf/arm_gpu_best_practices_developer_guide_101897_0302_04_en.pdf)]
6. [Arm GPU Datasheet](https://developer.arm.com/documentation/102849/0700/), [[backup](../pdf/Arm_GPU_Datasheet_v3.pdf)]

## Notes

* scalar
* Mali GPUs can contain many identical shader cores. Each shader core supports hundreds of concurrently executing threads. [4]
* Each shader core contains: [4]
	- One to three arithmetic pipelines or execution engines.
	- One load-store pipeline.
	- One texture pipeline.

* AFBC (v1.2) with 4x4 block.
* Transaction Elimination with 16x16 pixel block size.

* From Bifrost onwards float blending is enabled. [5]

* AFBC compatible formats: [5]
	- VK_FORMAT_R4G4B4A4_UNORM_PACK16
	- VK_FORMAT_B4G4R4A4_UNORM_PACK16
	- VK_FORMAT_R5G6B5_UNORM_PACK16
	- VK_FORMAT_R5G5B5A1_UNORM_PACK16
	- VK_FORMAT_B5G5R5A1_UNORM_PACK16
	- VK_FORMAT_A1R5G5B5_UNORM_PACK16
	- VK_FORMAT_B8G8R8_UNORM
	- VK_FORMAT_B8G8R8A8_UNORM
	- VK_FORMAT_B8G8R8A8_SRGB
	- VK_FORMAT_A8B8G8R8_UNORM
	- VK_FORMAT_A8B8G8R8_SRGB
	- VK_FORMAT_A8R8G8B8_SRGB
	- VK_FORMAT_B10G10R10A2_UNORM
	- VK_FORMAT_R4G4B4A4_UNORM
	- VK_FORMAT_R5G6B5_UNORM
	- VK_FORMAT_R5G5B5A1_UNORM
	- VK_FORMAT_R8_UNORM
	- VK_FORMAT_R8G8_UNORM
	- VK_FORMAT_R8G8B8_UNORM
	- VK_FORMAT_R8G8B8A8_UNORM
	- VK_FORMAT_R8G8B8A8_SRGB
	- VK_FORMAT_A8R8G8B8_UNORM
	- VK_FORMAT_R10G10B10A2_UNORM
	- VK_FORMAT_D24_UNORM_S8_UINT
	- VK_FORMAT_D16_UNORM
	- VK_FORMAT_D32_SFLOAT

