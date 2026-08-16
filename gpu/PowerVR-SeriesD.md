
## Examples

* Google Pixel 10

## References

1. [IMG DXT GPU: Is DXT still a Level 4 ray tracing solution?](https://youtu.be/0lbZM-x7VOU)
2. [IMG DXT - Bringing immersive visuals to mobile with ray tracing and FSR](https://youtu.be/J-Iu6l4g2QM)
3. [Vulkan features for DXT-48-1536](http://vulkan.gpuinfo.org/listreports.php?devicename=PowerVR%20D-Series%20DXT-48-1536%20MC1), [all](https://vulkan.gpuinfo.org/listdevicescoverage.php?extensionname=VK_KHR_driver_properties&extensionproperty=driverName&extensionpropertyvalue=PowerVR%20D-Series%20Vulkan%20Driver&platform=all)
4. [Pixel 10's Tensor G5 deep dive: All the info Google didn't tell us about its new chip](https://www.androidauthority.com/google-tensor-g5-benchmarks-3590355/)
5. [Imagination’s IMG DXT GPU unlocks scalable, premium ray tracing for all mobile gamers](https://www.imaginationtech.com/news/imaginations-img-dxt-gpu-unlocks-scalable-premium-ray-tracing-for-all-mobile-gamers/)
6. [Imagination takes efficiency up a level with latest D-Series GPU IP](https://www.imaginationtech.com/news/taking-efficiency-up-a-level-with-latest-d-series-gpu-ip/)

## Notes

* Level 4 ray tracing. [1]
	- its mean BVH traversal and full coherency sorting in hardware

* Fragment Shading Rate (FSR, *same as VRS or fragment density, not a AMD's FSR*) [2]

* 2D Dual-rate texturing allows post-processing effects in DXT to run much more efficiently, effectively increasing the performance of denoising.

* new triple Universal Shader Cluster (USC) design (3x ALU/TPU units). [5]

## Specs

* PowerVR DXT-48-1536:
	- FP32 TFLOPS: 1.7
	- clock: 1100 MHz
	- 1536 FP32 FLOPs/Clock
	- 48 texels / clock (?)


