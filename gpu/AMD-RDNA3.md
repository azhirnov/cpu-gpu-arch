3rd generation of AMD RDNA architecture, code name: Navi 3X.<br/>
11 generation of AMD GFX IP.

## Examples

**Navi 31 (N5)**:
* RX 7900 GRE, RX 7900 XT, RX 7900 XTX
* RX 7900M

**Navi 32 (N5)**:
* RX 7700 XT, RX 7800 XT

**Navi 33 (N6)**:
* RX 7600, RX 7600 XT
* RX 7600S, RX 7600M, RX 7600M XT, RX 7700S

**Custom**
* Steam Machine (28CU)

**Integrated (N4P)**:
* 740M, 760M, 780M
* Z1 (740M), Z1 Extreme (780M), Z2 (780M)
* Ryzen 7x40
* Ryzen 8x40, 8x45
* Ryzen 8x00G (Desktop)

**RDNA 3.5**
* Radeon 880M, 890M
* GPU in Ryzen AI 3xx
* Radeon 8060S
* Ryzen Z2 Extreme (16CU)


## References

1. [Beyond the current gen](https://gpuopen.com/presentations/2023/RDNA3_Beyond-the-current-gen-v4.pdf), [[backup](../pdf/AMD-RDNA3_Beyond-the-current-gen-v4.pdf)]
2. [Architecture Deep Dive](https://www.tomshardware.com/news/amd-rdna-3-gpu-architecture-deep-dive-the-ryzen-moment-for-gpus)
3. [Instruction Set Architecture](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/rdna3-shader-instruction-set-architecture-feb-2023_0.pdf), [[backup](../pdf/AMD-rdna3_isa.pdf)]
4. [Micro Engine Scheduler Specification](https://gpuopen.com/download/documentation/micro_engine_scheduler.pdf), [[backup](../pdf/AMD-rdna3_micro_engine_scheduler.pdf)]
6. [Ryzen Z1’s Tiny iGPU](https://chipsandcheese.com/2024/02/25/ryzen-z1s-tiny-igpu/)
7. [Latency Testing is Hard (RDNA 3 Power Saving)](https://chipsandcheese.com/2023/06/14/latency-testing-is-hard-rdna-3-power-saving/)
8. [AMD’s RX 7600: Small RDNA 3 Appears](https://chipsandcheese.com/2023/06/04/amds-rx-7600-small-rdna-3-appears/)
9. [Microbenchmarking AMD’s RDNA 3 Graphics Architecture](https://chipsandcheese.com/2023/01/07/microbenchmarking-amds-rdna-3-graphics-architecture/)
10. [AMD RDNA3 mesh shading with RADV](https://timur.hu/blog/2024/rdna3-mesh-shading)
11. [AMD Reveals Radeon RX 7900 XTX and 7900 XT](https://www.anandtech.com/show/17638/amd-reveals-radeon-rx-7900-xtx-and-7900-xt-first-rdna-3-parts-to-hit-shelves-in-december)
12. [Vulkan features for RX 7900 XT](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD%20Radeon%20RX%207900%20XT), [Radeon 780M](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD%20Radeon%20780M%20Graphics), [RADV 780M](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD+Radeon+780M+Graphics+%28RADV+PHOENIX%29&platform=linux)
13. [How to accelerate AI applications on RDNA 3 using WMMA](https://gpuopen.com/learn/wmma_on_rdna3/)


**RDNA 3.5**
2.1. [Vulkan features for Radeon 890M](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD+Radeon%28TM%29+890M+Graphics), [8060S](https://vulkan.gpuinfo.org/listreports.php?property=devicename&value=AMD%20Radeon(TM)%208060S%20Graphics&platform=all), [RADV 890M](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD+Radeon+890M+Graphics+%28RADV+GFX1150%29&platform=linux)<br/>
2.2. ["RDNA3.5" Instruction Set Architecture](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/rdna35_instruction_set_architecture.pdf), [[backup](../pdf/AMD-rdna3_5_isa.pdf)<br/>
2.3. [AMD RDNA 3.5’s LLVM Changes](https://chipsandcheese.com/2024/02/04/amd-rdna-3-5s-llvm-changes/)<br/>
2.4. [AMD’s Radeon 890M: Strix Point’s Bigger iGPU](https://chipsandcheese.com/2024/08/24/amds-radeon-890m-strix-points-bigger-igpu/)

## Features

* Work graphs.
* Tensor Core with fp32, fp64, fp16, bf16, i8, i4 formats.


## Notes

* If the compiler determines that a loaded value is constant across a wavefront, it can tell the GPU to use the scalar datapath. (for all RDNA) [9]

* LDS supports 64 atomics for fast access across the WGP (1.2.2.1)[3]
* GDS supports 2 atomics for fast access (1.2.2.2)[3]
* wave64 (subgroupSize=64) mode dual issue instructions with x2 performance (2.1)[3]
* CU and WGP modes for work-group (2.3)[3]
* WMMA instructions for fp16 16x16 matrices (7.9)[3]
* 16bit derivatives (10.4)[3]
* 64bit atomics on images (10.4)[3]

* Registers allocated for the worst case.

* 2xfp16 instructions: [3]
	- V_PK_FMA_F16, V_PK_ADD_F16, V_PK_MUL_F16, V_PK_MIN_F16, V_PK_MAX_F16.
	- V_PK_FMAC_F16 -- Multiply packed FP16 values and accumulate with destination.
	- V_CVT_PK_RTZ_F16_F32 -- Convert two single-precision floats into a packed FP16 result and always round to zero (ignore the current rounding mode).
	- V_DOT2ACC_F32_F16
	- V_DUAL_DOT2ACC_F32_F16, V_DUAL_DOT2ACC_F32_F16
	- V_DOT2_F16_F16
	- CVT_PKNORM_I16_F16, CVT_PKNORM_U16_F16 -- Convert two FP16 values into packed unsigned normalized shorts.
	- V_DOT2_F32_F16 -- Dot product of packed FP16 values.
	- V_WMMA_F32_16X16X16_F16, V_WMMA_F16_16X16X16_F16.
* MIX instructions: [3]
	- allow to combine fp32 and fp16, fp16_lo and fp16_hi.
	- V_FMA_MIX_F32, V_FMA_MIXLO_F16, V_FMA_MIXHI_F16.

* Ray tracing instructions: [3]
	- Box BVH nodes perform 4x Ray/Box intersection, sorts the 4 children based on intersection distance and returns the child pointers and hit status.
	- Triangle nodes perform 1 Ray/Triangle intersection test and returns the intersection point and triangle ID.

* RDNA 3 introduces dual issue capability for a variety of common FP32 instructions, doubling the theoretical FP32 throughput. [6]
	- Shader programs can leverage its dual issue capability by using wave64 mode or special dual issue instructions in wave32 mode.
	- On RDNA hardware, pixel shaders often use wave64 mode, in which 2048-bit vectors execute on the WGP’s 1024-bit execution units over 2 clock cycles, but achieve 1 instruction per cycle throughput on operations with dual issue support.
	- Wave32 mode lets individual threads (waves) finish faster as 1 instruction per cycle throughput becomes the general case. However, taking advantage of RDNA 3’s extra FP32 units in wave32 mode requires the compiler to find dual issue pairs. That requires instruction-level parallelism within a basic block, and could be upended by register cache source port or result bus limitations.
	- The dual issue shader array allows the scheduler to issue two wavefronts per cycle to different execution units within the WGP, improving utilization of the ALU resources.

* A WGP with four SIMDs can thus track up to 64 independent instruction streams. [6]

* Dual issue: [3]
	- X and Y opcodes can run in parallel.
	- X opcodes:
		* V_DUAL_FMAC_F32 - Multiply two floating point inputs and accumulate the result into the destination register using fused multiplyadd.
		* V_DUAL_CNDMASK_B32 - Copy data from one of two inputs based on the vector condition code and store the result into a vector register.
		* V_DUAL_FMAAK_F32 - Multiply two single-precision floats and add a literal constant using fused multiply-add.
		* V_DUAL_FMAMK_F32 - Multiply a single-precision float with a literal constant and add a second single-precision float using fused multiply-add.
		* V_DUAL_MAX_F32 - Select the maximum of two floating point inputs and store the result into a vector register.
		* V_DUAL_MIN_F32 - Select the minimum of two floating point inputs and store the result into a vector register.
		* V_DUAL_MUL_F32 - Multiply two floating point inputs and store the result into a vector register.
		* V_DUAL_DOT2ACC_F32_F16 - Dot product of packed FP16 values, accumulate with destination. The initial value in D is used as S2.
		* V_DUAL_DOT2ACC_F32_BF16 - Dot product of packed brain-float values, accumulate with destination. The initial value in D is used as S2.
		* V_DUAL_ADD_F32 - Add two floating point inputs and store the result into a vector register.
		* V_DUAL_SUB_F32 - Subtract the second floating point input from the first input and store the result into a vector register.
		* V_DUAL_MOV_B32 - Move data from a vector input into a vector register.
		* V_DUAL_SUBREV_F32 - Subtract the first floating point input from the second input and store the result into a vector register.
	- Y opcodes:
		* all X opcodes
		* V_DUAL_ADD_NC_U32 - Add two unsigned inputs and store the result into a vector register. No carry-in or carry-out support.
		* V_DUAL_LSHLREV_B32 - Given a shift count in the first vector input, calculate the logical shift left of the second vector input and store the result into a vector register.
		* V_DUAL_AND_B32 - Calculate bitwise AND on two vector inputs and store the result into a vector register.

* RDNA3 changes how shader outputs work on pre-rasterization stages (including VS, TES, GS, MS). [10]
	- The parameter cache was removed from RDNA3 in favour of the attribute ring which is basically a buffer in VRAM.
	- Shaders must now store their outputs to attribute ring buffer and after rasterization, the HW reads the attributes from the attribute ring and stores them to the LDS space of fragment shaders.
	- In the ideal access pattern, each attribute store would overwrite a full cache line so the shader won’t actually touch VRAM.
	- In mesh shader: Any invocation can now truly write generic attributes of any other invocation without restrictions, because these are just a memory write. The shader compiler now has to worry about memory access patterns.

* iGPU supports max 16GB memory.
* Radeon 8060S supports max 96GB memory with quad channel LPDDR5X.


## Specs

* cumulative bandwidth between the MCDs and GCD is 5.3TB/s 5.3TB/s [11]

* Cache on RX 7900 XTX: [9]
	- L0: 64KB per WGP, 32-Way, read L1: 128B/cy, write L1: 32B/cy, bandwidth 32TB/s *(128B * CUs * GPUClock ?)*
	- Instruction Cache: 32KB per WGP, 4-way, read only: 32B/cy
	- K Cache (Scalar cache): 16KB per WGP, 4-way, read only: 32B/cy
	- L1: 256KB per array, 16-way, read/write to L2: 3072B/cy, bandwidth 18TB/s
	- L2: 6MB, 16-way, read/write to L3: 2304B/cy, bandwidth 9TB/s
	- L3 (Infinity cache): 96MB, bandwidth 3.6TB/s, 128ns latency for scalar [7], 150ns latency for vector [7]
	- VRAM: bandwidth 895GB/s (theoretical: 960.0 GB/s)
	- GPU clock: 2498 MHz, CU: 96, WGP: 48, ShaderArrays: 12

* Cache on Z1 Extreme (780M): [6]
	- L0: 32KB per WGP, bandwidth 3TB/s, latency ~30ns
	- L1: 128KB per array, bandwidth 2TB/s, latency ~50ns
	- L2: 8MB, bandwidth 1.5TB/s, scalar latency ~65ns, vector latency ~80ns
	- L3: 16MB
	- Memory: 16GB, bandwidth 25 GB/s, scalar latency 218ns, vector latency 233ns
	- GPU clock: 2700MHz, CU: 12, WGP: 6, ShaderArrays: 2

* Tensor core ops per CU: [13]
	- fp32: 256
	- fp64: 4
	- fp16: 512
	- bf16: 512
	- i8: 512
	- i4: 1024

* Geometry performance: 12 primitive/clock
* Rasterization: 6 primitives/clock, 192 pix/clock

* Shader Array or Data-parallel processor (DPP) array:
	- L1 cache: 128KB
	- variable number of WGP (with 2x CU), computeUnitsPerShaderArray in Vulkan.

* WGP config: [12]
	- The basic unit of shader computation hardware.
	- L0 cache: 32KB
	- LDS: ?
	- 4x SIMDs or 2x CU

* CU config: [12]
	- 2x SIMDs (simdPerComputeUnit)
	- Ray tracing accelerator
	- L0 vector cache: 16 KB
	- Matrix core with: [link](https://gpuopen.com/learn/matrix_core_amd_rdna4/)
		* 512 fp16 FLOPS/clk
		* 512 bf16 FLOPS/clk
		* 512 i8 FLOPS/clk

* SIMD config: [12]
	- 32x FMA
	- VGPR: 128 KB, vgprsPerSimd: 1024 (VGPR size = vgprsPerSimd * 4 *(32bit register)* * 32 *(32 threads per SIMD)*)
	- SGPR: 8KB?, sgprsPerSimd: 2048 (SGPR size = sgprsPerSimd * 4 *(32bit register)*)
	- max 16 wavefronts (wavefrontsPerSimd in Vulkan)
	- wavefront can be 32 or 64 threads (Vulkan: minSubgroupSize=32, maxSubgroupSize=64, wavefrontSize=64)
