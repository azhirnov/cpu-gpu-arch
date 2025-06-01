Codename: GA10x

## Examples

* RTX 30xx
* RTX Ax000
* Orin
* MX570

## References

1. [Tuning CUDA Applications for NVIDIA Ampere GPU Architecture](https://docs.nvidia.com/cuda/ampere-tuning-guide/)
2. [Ampere Architecture In-Depth](https://developer.nvidia.com/blog/nvidia-ampere-architecture-in-depth/)
3. [Architecture Whitepaper](https://www.nvidia.com/content/PDF/nvidia-ampere-ga-102-gpu-architecture-whitepaper-v2.pdf), [[backup](../pdf/NV-ampere-ga-102-gpu-architecture-whitepaper-v2.pdf)]
4. [Compute Capability 8.7](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#compute-capability-8-x)
5. [Vulkan features for RTX 3090](https://vulkan.gpuinfo.org/listreports.php?devicename=NVIDIA%20GeForce%20RTX%203090)
6. [Demystifying the Nvidia Ampere Architecture through Microbenchmarking and Instruction-level Analysis](https://arxiv.org/pdf/2208.11174), [[backup](../pdf/NV-ampere_microbench.pdf)]
7. [Dissecting the Ampere GPU Architecture through Microbenchmarking](https://www.nvidia.com/en-us/on-demand/session/gtcspring21-s33322/), [[backup](../pdf/NV-ampere_microbench2.pdf)]


## Features

* Work graphs.
* AV1.
* PCIe Gen4.
* New Tensor Core with TF32, DF16 formats.

## Notes

* SM continues to support double-speed FP16 (HFMA) operations which are supported in Turing. [1]
* Added BF16 type. [1]
* fp32 : fp16 : bf16 has same TOp/s. [1]
* fp32 : i32 has 2:1 rate. [1]

* Includes FP32 processing on both datapaths, doubling the peak processing rate for FP32 operations. One datapath in each partition consists of 16 Ampere GPU Architecture In-Depth NVIDIA Ampere GA102 GPU Architecture 13 FP32 CUDA Cores capable of executing 16 FP32 operations per clock. Another datapath consists of both 16 FP32 CUDA Cores and 16 INT32 Cores, and is capable of executing either 16 FP32 operations OR 16 INT32 operations per clock. [1]

* Tensor core with 128 FMA per cycle, 256 for sparse matrix. [3]

* On Ampere, you can also dispatch concurrent compute workloads by dispatching it on both the DIRECT and ASYNC_COMPUTE queue. [ref](https://docs.nvidia.com/nsight-graphics/AdvancedLearning/index.html)


## Specs

* ops/clock per SM: [4]
	- 128 fp16 FMA (2xFP16 on 1 datapath)
	- 128 fp32 FMA (2 datapaths)
	- 2 fp64 FMA
	- 64 i32 (on 1 datapath)
	- 16 SFU

* RTX 3080 specs:
	- shaderSMCount: 68 [vk]
	- shaderWarpsPerSM: 48 [vk] (32?)
	- warp size: 32 [vk]
	- Shading Units: 8704 [specs] *(68 * 32 * 4 ???)*
	- total threads: 69 632 [calc] *(68 * 32 * 32)*
	- Clock: 1440 MHz / 1710 MHz [specs]
	- FP32 TFLOPS: 29.77 [specs], 37.6 [calc] *{104.4K threads * 1.44GHz / (4cycles (5?) for ADD/MUL/FMA)}*

* SM:
	- 4 Tensor Cores

* GeForce RTX 3080 L1 bandwidth: 219 GB/s
