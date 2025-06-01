4th generation of AMD RDNA architecture.

## Examples

**RDNA 3.5**
* Radeon 880M, 890M
* GPU in Ryzen AI 3xx
* Radeon 8060S
* Ryzen Z2 Extreme (16CU)

**Navi 48**
* Radeon RX 9070, RX 9070 XT

## References

1. [Examining AMD’s RDNA 4 Changes in LLVM](https://chipsandcheese.com/2024/01/28/examining-amds-rdna-4-changes-in-llvm/)
2. [Instruction Set Architecture](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/rdna4-instruction-set-architecture.pdf)
3. [AMD RDNA 4 architecture deep dive](https://www.notebookcheck.net/AMD-RDNA-4-architecture-deep-dive-A-64-CU-monolithic-design-with-all-round-improvements-to-compute-media-encode-decode-ray-tracing-and-AI.969593.0.html)
4. ["RDNA3.5" Instruction Set Architecture](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/rdna35_instruction_set_architecture.pdf), [[backup](../pdf/AMD-rdna3_5_isa.pdf)
5. [RDNA 4's "Out-of-Order" Memory Accesses](https://chipsandcheese.com/p/rdna-4s-out-of-order-memory-accesses)
6. [Vulkan features for RX 9070 XT](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD+Radeon+RX+9070+XT)
7. [RDNA 4’s Raytracing Improvements](https://chipsandcheese.com/p/rdna-4s-raytracing-improvements)
8. [Dynamic Register Allocation on AMD's RDNA 4 GPU Architecture](https://chipsandcheese.com/p/dynamic-register-allocation-on-amds)

## Features

* Tensor Core with fp32, fp64, fp16, bf16, i8, i4, **fp8, bf8** formats.
* Ray tracing with oriented bounding boxes (OBB).
* Dynamic registers.

## Notes

* introduces new SWMMAC (Sparse Wave Matrix Multiply Accumulate) instructions to take advantage of sparsity. [1]

* Shaders have the option to allocate registers dynamically. [3]
	- Compute Shaders may be launched in a mode where they can dynamically allocate and deallocate VGPRs; [2]
	- dynamic VGPRs is not supported for graphics-shaders. [2]
	- Dynamic VGPRs are supported only for wave32, not wave64. [2]
	- if any workgroup is using dynamic VGPRs, only dynamic VGPR enabled workgroups or waves may be running on that WGP. [2]
	- Dynamically allocating VGPRs can lead to deadlock when all VGPRs have been allocated but every wave needs to allocate more VGPRs to make progress. [2]

* fp32 scalar ops. [3]
	- The SALU supports a set of floating point operations to offload uniform value calculation from the VALU pipe. [2]
	- fp32 ops: add, sub, min, max, mul, ceil, floor, trunc, round, fma, cmp, conversion. [2]
	- fp16 ops: add, sub, min, max, mul, ceil, floor, trunc, round, fma, cmp. [2]

* LDS: [2]
	- 64 banks, each with 512 entries of 4 bytes
	- A single work-group may allocate up to 64kB of LDS space.
	- The shared memory contains 64 integer atomic units to enable fast, unordered atomic operations.

* Ray tracing instructions: [2]
	- Box BVH nodes perform 4x Ray/Box intersection, sorts the 4 children based on intersection distance and returns the child pointers and hit status.
	- Triangle nodes perform 1 Ray/Triangle intersection test and returns the intersection point and triangle ID.


## Specs

* WGP config: [2, 3]
	- 4x SIMD cores (2x CU)
	- Scalar Cache: 16KB
	- Instruction Cache: 32 KB
	- Shared Memory: 128 KB
	- 2x Ray Accelerators (8 ray/box, 2 ray/triangle)
	- 2x L0: 32 KB
	- LDS: 128 KB

* SIMD Core config: [2, 3, 6]
	- 32x FMA SIMD Unit
	- 32x FMA/Int SIMD Unit
	- 8x Transcendental Logic Unit (TLU)
	- Scalar Unit
	- AI Accelerator
	- Vector GPR: 192 KB, vgprsPerSimd: 1536 (VGPR size = vgprsPerSimd * 4 *(32bit register)* * 32 *(32 threads per SIMD)*)
	- Scalar GPR: 8 KB, sgprsPerSimd: 2048 (SGPR size = sgprsPerSimd * 4 *(32bit register)*)
	- max 16 wavefronts (wavefrontsPerSimd in Vulkan)
	- wavefront can be 32 or 64 threads (Vulkan: minSubgroupSize=32, maxSubgroupSize=64, wavefrontSize=64)

* RX 9070 XT theoretical performance:
	- fp32 FLOPS: 64 WGP * 4 * 32 FMA * 2.97 GHz = 24.3T FMA = 48.66 TFLOPS
	- Ray/triangle: 64 WGP * 2 RA * 1 ray/tri * 2.97 GHz = 380 GRays/s
	- Ray/Box: 64 WGP * 2 RA * 4 ray/box * 2,97 GHz = 1.5 TRays/s
	- AI:
	- Pixel Rate: 380.2 GPixel/s [specs]
	- Texture Rate: 760.3 GTexel/s [specs]

* Tensor core ops per CU (dense/sparse): [3]
	- fp32: 256
	- fp64: 4
	- fp16, bf16: 1024 / 2048
	- fp8, bf8: 2048 / 4096
	- i8: 2048 / 4096
	- i4: 4096 / 8192

