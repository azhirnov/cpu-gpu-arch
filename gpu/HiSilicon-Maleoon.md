
# 91x-92x

## Examples

* Maleoon-910
* Maleoon-920

## References

1.1. [Vulkan features for Maleoon-910](https://vulkan.gpuinfo.org/listreports.php?devicename=Maleoon%20910), [Maleoon-920](https://vulkan.gpuinfo.org/listreports.php?devicename=Maleoon%20920)<br/>
1.2. [Best Practice in Maleoon GPUs](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-maleoon-gpu-best-practices)<br/>

## Features

* TBDR architecture. [1.2]
* tile shader (HUAWEI_subpass_shading). [1.1]

## Specs

### Maleoon-910

* Triangle Fillrate: 4024 MT/s
* Pixel Fillrate: 148 GP/s
* Clock: 750 MHz
* 256 threads per core
* 2048 threads in MP4 (1536 GFLOPS)

### Maleoon-920

* Clock: 840 MHz

## Notes

* used simd32 mode:
	- If the workgroup size is less than 32 (simd32), the hardware can ensure that all threads in the workgroup are in the same warp. Therefore, you can omit the workgroup-level barriers to improve performance. [1.2]
	- uses the big-core structure (SIMD32/SIMD64). [1.2]
	- simd64 when double issue (?)

* HEBC lossless render target compression. Requirements: [1.2]
	- 2D image
	- usage: color/depth attachment, sampled, transfer src/dst, input_attachment
	- formats: all 16bit, all 32bit, R16/RG16/RGB16/RGBA16 U/I/F, R32 U/I/F, D16, D24, D32, D24S8, D32S8


# 93x

## Examples

* Maleoon-935

## References

2.1. [Vulkan features for Maleoon-935](https://vulkan.gpuinfo.org/listreports.php?devicename=Maleoon%20935)<br/>

## Features

* Ray tracing. [2.1]
