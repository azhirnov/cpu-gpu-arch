
## Examples

* RTX 30xx
* RTX Ax000
* Orin
* MX570

## References

1. [Tuning CUDA Applications for NVIDIA Ampere GPU Architecture](https://docs.nvidia.com/cuda/ampere-tuning-guide/)
2. [Ampere Architecture In-Depth](https://developer.nvidia.com/blog/nvidia-ampere-architecture-in-depth/)
3. [Architecture Whitepaper](https://www.nvidia.com/content/PDF/nvidia-ampere-ga-102-gpu-architecture-whitepaper-v2.pdf)
4. [Compute Capability 8.x](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#compute-capability-8-x)

## Notes

* SM continues to support double-speed FP16 (HFMA) operations which are supported in Turing. [1]
* Added BF16 type. [1]
* fp32 : fp16 : bf16 has same tflops. [1]
* fp32 : i32 has 2:1 rate. [1]

* Includes FP32 processing on both datapaths, doubling the peak processing rate for FP32 operations. One datapath in each partition consists of 16 Ampere GPU Architecture In-Depth NVIDIA Ampere GA102 GPU Architecture 13 FP32 CUDA Cores capable of executing 16 FP32 operations per clock. Another datapath consists of both 16 FP32 CUDA Cores and 16 INT32 Cores, and is capable of executing either 16 FP32 operations OR 16 INT32 operations per clock. [1]
* GeForce RTX 3080 L1 bandwidth: 219 GB/sec

* Work graphs.


## Specs

* ops/clock per SM: [4]
	- TODO

