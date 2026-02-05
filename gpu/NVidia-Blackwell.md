Codename: GB100 (datacenter), GB20x (consumer)


## Examples

* RTX 50xx


## References

1. [Compute Capability 12.0](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#compute-capability-12-0)
2. [A Deeper Analysis of Nvidia RTX 50 Blackwell GPU Architecture](https://www.guru3d.com/review/technical-analysis-of-nvidia-rtx-50-blackwell-gpu-architecture/)
3. [NVIDIA RTX BLACKWELL GPU ARCHITECTURE (5090)](https://images.nvidia.com/aem-dam/Solutions/geforce/blackwell/nvidia-rtx-blackwell-gpu-architecture.pdf)
4. [Blackwell: Nvidia’s Massive GPU](https://chipsandcheese.com/p/blackwell-nvidias-massive-gpu)
5. [Vulkan features for GTX 5080](https://vulkan.gpuinfo.org/listreports.php?devicename=NVIDIA%20GeForce%20RTX%205080)
6. [RTX 5070Ti Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench-gpu/NVidia_RTX5070Ti.md)

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

* added floating point instructions to uniform datapath. [4]
	- include adds, multiples, FMAs, min/max, and conversions between integer and floating point.


## Specs

* ops/clock per SM: [1,3]
	- 128 fp16 FMA (2xFP16 on 1 datapath)
	- 128 fp32 FMA (2 datapaths)
	- 2 fp64 FMA
	- 64 i32 (on 1 datapath)
	- 16 SFU
	- 4 warp schedulers
	- 4 Tensor cores

* Tensor core formats: INT4, INT8, FP4, FP8, FP16, FP32, BF16, TF32

* Tensor core ops/clock per SM (dense/sparse):
	- fp4: 4096 / 8192
	- fp8 with fp16 accum: 2048 / 4098
	- fp8 with fp32 accum: 1024 / 2048
	- fp16, bf16: 1024 / 2048
	- fp16, bf16 with fp32 accum: 512 / 1024
	- tf32: 256 / 512

* RTX 5090 performance: [3]
	- clock: 2407 MHz
	- SM: 170
	- fp32 TFLOPS: 104.8
	- fp16 TFLOPS: 104.8
	- bf16 TFLOPS: 104.8
	- i32 TOPS: 104.8
	- RT TOPS: 317.5
	- Tensor cores: 680
	- fp4 Tensor TFLOPS: 1676 / 3352
	- fp8 Tensor fp16 accum TFLOPS: 838 / 1676
	- fp8 Tensor fp32 accum TFLOPS: 419 / 838
	- fp16 Tensor TFLOPS: 419 / 838
	- fp16 Tensor fp32 accum TFLOPS: 209.5 / 419
	- tf32 Tensor TFLOPS: 104.8 / 209.5
	- Memory Bandwidth: 1792 GB/s
	- Pixel Fill-rate: 423.6 GigaPixels/s
	- Texel Fill-rate: 1636.8 GigaTexels/s
