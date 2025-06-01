5th generation of Mali GPU architecture.

Content:
* [Gen1](#Gen1)
* [Gen2](#Gen2)
* [All gens](#All-gens)


# Gen1

## Examples

* Mali-G620
* Mali-G720
* Immortalis-G720

## References

1.1. [Arm Mali-G620 Performance Counters Reference Guide](https://developer.arm.com/documentation/108080/0104)<br/>
1.2. [Arm Immortalis-G720 and Arm Mali-G720 Performance Counters Reference Guide](https://developer.arm.com/documentation/108081/0104), [[backup](../pdf/arm-immortalis-g720_and_arm_mali-g720_performance_counters_reference_guide_108081_0103_en.pdf)]<br/>
1.3. [Vulkan features for Mali-G720](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G720-Immortalis%20MC12)<br/>

## Features

* Deferred Vertex Shading - optimization for small triangles.


## Notes

* G720 core config [2]:
	- 4 ALU
	- 512 fp16/cy (128 per ALU)
	- 256 fp32/cy (64 per ALU)
	- 4 frag/cy
	- 4 pix/cy
	- 8 tex/cy

* Immortalis-G720 MC12 VK_ARM_shader_core_builtins, VK_ARM_shader_core_properties [1.3]:
	- shaderCoreCount: 12
	- shaderWarpsPerCore: 64 -- maximum number of simultaneously executing warps on a shader core
	- fmaRate: 128 -- maximum number of single-precision fused multiply-add operations per clock per shader core.
	- pixelRate: 4 -- maximum number of pixels output per clock per shader core.
	- texelRate: 8 -- maximum number of texels per clock per shader core.


# Gen2

## Examples

* Mali-G625
* Mali-G725
* Immortalis-G925

## References

2.1. [Arm Immortalis-G925 and Arm Mali-G725 Performance Counters Reference Guide](https://developer.arm.com/documentation/109793/0100), [[backup](../pdf/arm-immortalis-g925_and_arm_mali-g725_performance_counters_reference_guide_109793_0100_en.pdf)]<br/>
2.2. [Arm Mali-G625 Performance Counters Reference Guide](https://developer.arm.com/documentation/109780/0100/)<br/>
2.3. [Vulkan features for Mali-G925-Immortalis MC12](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G925-Immortalis%20MC12)<br/>
2.4. [Hidden Surface Removal in Immortalis-G925: The Fragment Prepass](https://community.arm.com/arm-community-blogs/b/graphics-gaming-and-vr-blog/posts/immortalis-g925-the-fragment-prepass), [[webarchive](https://web.archive.org/web/20241202033355/https://community.arm.com/arm-community-blogs/b/graphics-gaming-and-vr-blog/posts/immortalis-g925-the-fragment-prepass)]<br/>

## Features

* Fragment Pre-pass - hardware depth pre-pass.
* VK_ARM_pipeline_opacity_micromap

## Notes

* G725 core config [2]:
	- 4 ALU
	- 512 fp16/cy (128 per ALU)
	- 256 fp32/cy (64 per ALU)
	- 4 frag/cy
	- 4 pix/cy
	- 8 tex/cy


* Immortalis-G925-Immortalis MC12 VK_ARM_shader_core_builtins, VK_ARM_shader_core_properties [2.3]:
	- shaderCoreCount: 12
	- shaderWarpsPerCore: 64 -- maximum number of simultaneously executing warps on a shader core
	- fmaRate: 128 -- maximum number of single-precision fused multiply-add operations per clock per shader core.
	- pixelRate: 4 -- maximum number of pixels output per clock per shader core.
	- texelRate: 8 -- maximum number of texels per clock per shader core.


# All gens

## References

1. Deferred Vertex Shading: [slide 1](../img/arm-dvs-1.jpg), [slide 2](../img/arm-dvs-2.jpg)
2. [Arm GPU Datasheet](https://developer.arm.com/documentation/102849/0700/), [[backup](../pdf/Arm-GPU_datasheet_v7.pdf)]
3. [Vulkanised 2025: Vulkan Best Practices for Mobile Development ](https://youtu.be/fWeR4ECVcW8) 


## Notes

* Deferred Vertex Shading.
	- Brings vertex and fragment shading together to keep intermediate data local. [1]
	- The Tiles chooses which triangles to defer and which to shade upfront, to prevent excessive re-shading. [1]
	- Larger tiles mean each triangle spans fewer tiles, so less re-shading and more triangles can be deferred (DVS). [1]
	- During the tiling phase, Arm GPUs do not write out position data for small triangles. [2.4]
	- During the fragment phase, Arm GPUs will execute a full vertex shader for small triangles. [2.4]
	- Vertex dependencies now released later. [3]

* Added a 2x MSAA module, as previously when a developer would request 2x MSAA from the GPU, it would automatically jump to 4x MSAA.
* Fragment Task with 64x64 pixels region.

* Fragment Pre-pass.
	- Is a Hidden Surface Removal (HSR) technique that does a first pass over the fragments to find out which fragments are going to be visible in the result.
	  When that is done, it loops back and renders only the visible ones. [2.4]
	- Same as depth prepass but without double draw (double fill rate). [3]

* Tile size:
	- 64x64 if <= 128 bits per pixel
	- 64x32 if <= 256 bpp
	- 32x32 if > 256 bpp

* Dedicated transfer stream. [3]

