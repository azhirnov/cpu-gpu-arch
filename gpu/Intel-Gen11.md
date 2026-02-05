CPU code name: Ice Lake.

## Examples

### Ice Lake
* UHD Graphics


## References

1. [Developer and Optimization Guide for Intel Processor Graphics Gen11 API](https://www.intel.com/content/www/us/en/developer/articles/guide/developer-and-optimization-guide-for-intel-processor-graphics-gen11-api.html), [[webarchive](https://web.archive.org/web/20230319150934/https://www.intel.com/content/www/us/en/developer/articles/guide/developer-and-optimization-guide-for-intel-processor-graphics-gen11-api.html)]
2. [Vulkan features for UHD Graphics](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20HD%20Graphics%20Gen11), [Iris+ (Mesa driver)](https://vulkan.gpuinfo.org/listreports.php?property=devicename&value=Intel(R)%20Iris(R)%20Plus%20Graphics%20(ICL%20GT2)&platform=linux)
3. [Intel Processor Graphics Gen11 Architecture](https://software.intel.com/content/dam/develop/external/us/en/documents/the-architecture-of-intel-processor-graphics-gen11-r1new.pdf), [[backup](../pdf/Intel-the-architecture-of-intel-processor-graphics-gen11-r1new.pdf)]

## Features

* Tile-based rendering. [3]
* Adaptive sync.


## Notes

* Architecture Highlights [1]
	- Compute capabilities that deliver up to a teraflop of performance
	- Significantly lower shared local memory (SLM) latency
	- Larger L3 cache size
	- Increased memory bandwidth
	- Improved multisample anti-aliasing (MSAA) performance

* Position Only Shading Tile Based Rendering (PTBR) [3]
	- Adds a parallel geometry pipeline that acts as a tile binning engine. It is used ahead of the render pipeline for visibility binning pre-pass per tile. It loops over geometry per tile and consumes visibility stream for that tile.
	- This collapses all the memory reads and writes within the L3 cache theredy reducing the external bandwidth.

## Specs

* Each EU contains 2 x 128-bit FPUs.
* One FPU supports 32-bit and 64-bit integer, FP16, FP32, FP64, and transcendental math functions.
* Other FPU supports only 32-bit and 64-bit integer, FP16 and FP32.
* Each Subslice contains 8 EUs and a sampler (4 tex/clk), and has 64 KB shared memory.
