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
1.2. [Arm Immortalis-G720 and Arm Mali-G720 Performance Counters Reference Guide](https://developer.arm.com/documentation/108081/0104), [[backup](../pdf/arm_immortalis-g720_and_arm_mali-g720_performance_counters_reference_guide_108081_0103_en.pdf)]<br/>
1.4. [Arm Mali-G620 Performance Counters Reference Guide](https://developer.arm.com/documentation/108080/0104)<br/>
1.5. [Vulkan features for Mali-G720](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-G720-Immortalis%20MC12)

## Notes

* G720 core config [2]:
	- 4 ALU
	- 512 fp16/cy (128 per ALU)
	- 256 fp32/cy (64 per ALU)
	- 4 frag/cy
	- 4 pix/cy
	- 8 tex/cy

* Immortalis-G720 MC12 VK_ARM_shader_core_builtins, VK_ARM_shader_core_properties [1.5]:
	- shaderCoreCount: 12
	- shaderWarpsPerCore: 64 -- maximum number of simultaneously executing warps on a shader core
	- shaderCoreMask: 0, 1, 3, 4, 5, 7, 16, 17, 18, 20, 21, 22
	- fmaRate: 128 -- maximum number of single-precision fused multiply-add operations per clock per shader core.
	- pixelRate: 4 -- maximum number of pixels output per clock per shader core.
	- texelRate: 8 -- maximum number of texels per clock per shader core.

# Gen2

## Examples

* Mali-G625
* Mali-G725
* Immortalis-G925

## References

2.1. [Arm Immortalis-G925 and Arm Mali-G725 Performance Counters Reference Guide](https://developer.arm.com/documentation/109793/0100), [[backup](../pdf/arm_immortalis-g925_and_arm_mali-g725_performance_counters_reference_guide_109793_0100_en.pdf)]<br/>
2.2. [Arm Mali-G625 Performance Counters Reference Guide](https://developer.arm.com/documentation/109780/0100/)<br/>

## Notes

* G725 core config [2]:
	- 4 ALU
	- 512 fp16/cy (128 per ALU)
	- 256 fp32/cy (64 per ALU)
	- 4 frag/cy
	- 4 pix/cy
	- 8 tex/cy

# All gens

## References

1. Deferred Vertex Shading: [slide 1](../img/arm-dvs-1.jpg), [slide 2](../img/arm-dvs-2.jpg)
2. [Arm GPU Datasheet](https://developer.arm.com/documentation/102849/0700/), [[backup](../pdf/Arm_GPU_datasheet_v7.pdf)]


## Notes

* Deferred Vertex Shading. [1]
	- Brings vertex and fragment shading together to keep intermediate data local.
	- The Tiles chooses which triangles to defer and which to shade upfront, to prevent excessive re-shading.
	- Larger tiles mean each triangle spans fewer tiles, so less re-shading and more triangles can be deferred (DVS).

* Added a 2x MSAA module, as previously when a developer would request 2x MSAA from the GPU, it would automatically jump to 4x MSAA.
* Fragment Task with 64x64 pixels region.
