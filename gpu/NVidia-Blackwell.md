Codename: GB100 (datacenter), GB20x (consumer)


## Examples

* RTX 50xx


## References

1. [Compute Capability 12.0](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#compute-capability-12-0)
2. [A Deeper Analysis of Nvidia RTX 50 Blackwell GPU Architecture](https://www.guru3d.com/review/technical-analysis-of-nvidia-rtx-50-blackwell-gpu-architecture/)
3. [NVIDIA RTX BLACKWELL GPU ARCHITECTURE (5090)](https://images.nvidia.com/aem-dam/Solutions/geforce/blackwell/nvidia-rtx-blackwell-gpu-architecture.pdf)

## Features

* DLSS 4, Multi Frame generation.
* GDDR7.
* PCIe Gen5.
* Tensor core with FP4 format.


## Notes

* SM architecture doubles INT32 bandwidth and throughput by enabling all shader cores to execute INT32 or FP32 instructions. [2]
	- Not supported parallel i32 and fp32 like in Turing.

* Shader Execution Reordering enhances the efficiency of shaders generating work for other shaders by doubling throughput. [2]
* Fourth-generation RT cores feature a triangle cluster intersection engine for efficient mega geometry processing. They include a compression format and lossless decompression engine for more efficient handling of complex scenes. [2]

* The shared memory capacity can be set to 0, 8, 16, 32, 64, or 100 KB. [1]
* Devices of compute capability 12.0 allow a single thread block to address up to 227 KB of shared memory. [1]

* doubles the performance of point-sampling textures per cycle compared to Ada. [3]
	- used in Stochastic Texture Filtering.

* Pixel Fill-rate (Gigapixels/sec) decreased from 443.5 (on RTX 4090) to 423.6. [3]
* RT TFLOPS increased from 191 (on RTX 4090) to 317.5 (+66%). [3]

* RT Core:
	- include a dedicated unit known as the Opacity Micromap Engine. [3]
	- includes a Triangle Cluster Intersection Engine, which further accelerates ray tracing of Mega Geometry. [3]
	- adds Linear Swept Spheres as a hardware-accelerated path to ray trace fine geometry like hair. [3]


## Specs

* ops/clock per SM: [1]
	- ? fp16 FMA
	- 128 fp32 FMA
	- 2 fp64 FMA
	- 64 i32
	- 16 SFU
	- 4 warp schedulers

* Tensor core formats: INT4, INT8, FP4, FP8, FP16, FP32, BF16, TF32

