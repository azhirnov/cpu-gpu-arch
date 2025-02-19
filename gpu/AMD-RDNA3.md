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

**Integrated (N4P)**:
* 740M, 760M, 780M
* Z1, Z1 Extreme
* Ryzen 7x40
* Ryzen 8x40, 8x45
* Ryzen 8x00G (Desktop)

**RDNA 3.5**
* AMD Radeon 880M, 890M
* GPU in Ryzen AI 3xx

## References

1. [Beyond the current gen](https://gpuopen.com/presentations/2023/RDNA3_Beyond-the-current-gen-v4.pdf), [[backup](../pdf/AMD-RDNA3_Beyond-the-current-gen-v4.pdf)]
2. [Architecture Deep Dive](https://www.tomshardware.com/news/amd-rdna-3-gpu-architecture-deep-dive-the-ryzen-moment-for-gpus)
3. [Instruction Set Architecture](https://gpuopen.com/rdna3-isa-guide-now-available/), [[backup](../pdf/AMD-rdna3_isa.pdf)]
4. [Micro Engine Scheduler Specification](https://gpuopen.com/download/documentation/micro_engine_scheduler.pdf), [[backup](../pdf/AMD-rdna3_micro_engine_scheduler.pdf)]
5. [AMD RDNA 3.5’s LLVM Changes](https://chipsandcheese.com/2024/02/04/amd-rdna-3-5s-llvm-changes/)
6. [Ryzen Z1’s Tiny iGPU](https://chipsandcheese.com/2024/02/25/ryzen-z1s-tiny-igpu/)
7. [Latency Testing is Hard (RDNA 3 Power Saving)](https://chipsandcheese.com/2023/06/14/latency-testing-is-hard-rdna-3-power-saving/)
8. [AMD’s RX 7600: Small RDNA 3 Appears](https://chipsandcheese.com/2023/06/04/amds-rx-7600-small-rdna-3-appears/)
9. [Microbenchmarking AMD’s RDNA 3 Graphics Architecture](https://chipsandcheese.com/2023/01/07/microbenchmarking-amds-rdna-3-graphics-architecture/)
10. [AMD RDNA3 mesh shading with RADV](https://timur.hu/blog/2024/rdna3-mesh-shading)
11. [AMD Reveals Radeon RX 7900 XTX and 7900 XT](https://www.anandtech.com/show/17638/amd-reveals-radeon-rx-7900-xtx-and-7900-xt-first-rdna-3-parts-to-hit-shelves-in-december)
12. [Vulkan features for RX 7900 XT](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD%20Radeon%20RX%207900%20XT), [Radeon 890M](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD+Radeon%28TM%29+890M+Graphics)
13. ["RDNA3.5" Instruction Set Architecture](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/rdna35_instruction_set_architecture.pdf), [[backup](../pdf/AMD-rdna3_5_isa.pdf)


## Notes

* Uses aggressive power saving techniques. [7]

* If the compiler determines that a loaded value is constant across a wavefront, it can tell the GPU to use the scalar datapath. (for all RDNA) [9]

* LDS supports 64 atomics for fast access across the WGP (1.2.2.1)[3]
* GDS supports 2 atomics for fast access (1.2.2.2)[3]
* wave64 (subgroupSize=64) mode dual issue instructions with x2 performance (2.1)[3]
* CU and WGP modes for work-group (2.3)[3]
* WMMA instructions for fp16 16x16 matrices (7.9)[3]
* 16bit derivatives (10.4)[3]
* 64bit atomics on images (10.4)[3]

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

## Features

* Work graphs.


## Specs

* cumulative bandwidth between the MCDs and GCD is 5.3TB/s 5.3TB/s [11]

* Cache on RX 7900 XTX: [9]
	- L0: 32KB per WGP, 32-Way, read: 128B/cy, write: 32B/cy, bandwidth 32TB/s
	- Instruction Cache: 32KB per WGP, 4-way, read only: 32B/cy
	- K Cache (Scalar cache): 16KB per WGP, 4-way, read only: 32B/cy
	- L1: 256KB, 16-way, read/write to L2: 3072B/cy, bandwidth 18TB/s
	- L2: 6MB, 16-way, read/write to L3: 2304B/cy, bandwidth 9TB/s
	- L3 (Infinity cache): 96MB, bandwidth 3.6TB/s, 128ns latency for scalar [7], 150ns latency for vector [7]
	- VRAM: bandwidth 895GB/s

