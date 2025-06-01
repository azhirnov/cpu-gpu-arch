2nd generation of AMD RDNA architecture, code name: Navi 2X.<br/>
10.3 generation of AMD GFX IP.

## Examples

**Discrete**:
* N6 fab: RX 6400 - 6500
* N7 fab: RX 6600 - 6900

**Integrated**:
* Radeon 610M, 680M
* Ryzen 6xxx / 7x20 / 7x35 / 7x45
* PS5 (36 CU)
* SteamDeck (8 CU)
* Ryzen Z2 Go (12 CU)

**Integrated in desktop CPU:**
* Ryzen 9x00X, 9x00X3D
* Ryzen 7x00, 7x00X, 7x00X3D

## References

1. [Instruction Set Architecture](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/rdna2-shader-instruction-set-architecture.pdf), [[backup](../pdf/AMD-rdna2_isa.pdf)]
2. [Van Gogh, AMD’s Steam Deck APU](https://chipsandcheese.com/2023/03/05/van-gogh-amds-steam-deck-apu/)
3. [Raytracing on AMD’s RDNA 2/3, and Nvidia’s Turing and Pascal](https://chipsandcheese.com/2023/03/22/raytracing-on-amds-rdna-2-3-and-nvidias-turing-and-pascal/)
4. [AMD’s HD 6950 vs RX 6900 XT](https://chipsandcheese.com/2023/04/01/amds-hd-6950-vs-rx-6900-xt-what-does-adding-50-do/)
5. [AMD’s RDNA 2: Shooting For the Top](https://chipsandcheese.com/2023/02/19/amds-rdna-2-shooting-for-the-top/)
6. [AMD’s Zen 4, Part 3: System Level Stuff, and iGPU](https://chipsandcheese.com/2023/01/05/amds-zen-4-part-3-system-level-stuff-and-igpu/)
7. [Vulkan features for RX 6700 XT](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD%20Radeon%20RX%206700%20XT)

## Features

* Hardware ray tracing.
* Mesh shading.
* AV1.


## Notes

* 2xfp16 instructions: [1]
	- V_PK_FMA_F16, V_PK_ADD_F16, V_PK_MUL_F16, V_PK_MIN_F16, V_PK_MAX_F16.
	- V_PK_FMAC_F16 -- Multiply packed FP16 values and accumulate with destination.
	- CVT_PKNORM_I16_F16, CVT_PKNORM_U16_F16 -- Convert two FP16 values into packed unsigned normalized shorts.
	- V_CVT_PKRTZ_F16_F32 -- Convert two single-precision floats into a packed FP16 result and always round to zero (ignore the current rounding mode).
	- V_DOT2C_F32_F16, V_DOT2_F32_F16 -- Dot product of packed FP16 values.
* MIX instructions: [1]
	- allow to combine fp32 and fp16, fp16_lo and fp16_hi.
	- V_FMA_MIX_F32, V_FMA_MIXLO_F16, V_FMA_MIXHI_F16.

* Ray tracing instructions: [1]
	- Box BVH nodes perform 4x Ray/Box intersection, sorts the 4 children based on intersection distance and returns the child pointers and hit status.
	- Triangle nodes perform 1 Ray/Triangle intersection test and returns the intersection point and triangle ID.

* The RDNA command processor reads commands that the host has written to memory-mapped RDNA registers in the system-memory address space. The command processor sends hardware-generated interrupts to the host when the command is completed. [1]
* The RDNA processor hides memory latency by keeping track of potentially hundreds of workitems in various stages of execution, and by overlapping compute operations with memory access operations. [1]


## Specs

* WGP config: [5]
	- The basic unit of shader computation hardware.
	- L0 scalar cache: 16 KB, 4-way, 64B line, 4x16 B/cy to SIMDs
	- LDS: 128 KB, 4x128 B/cy to SIMDs
	- 4x SIMDs or 2x CU

* CU config: [5]
	- 2x SIMDs (simdPerComputeUnit)
	- Ray tracing accelerator
	- L0 vector cache: 16 KB

* SIMD config: [5, 7]
	- 32x FMA
	- VGPR: 128 KB, vgprsPerSimd: 1024 (VGPR size = vgprsPerSimd * 4 *(32bit register)* * 32 *(32 threads per SIMD)*)
	- SGPR: 8KB, sgprsPerSimd: 2048 (SGPR size = sgprsPerSimd * 4 *(32bit register)*)
	- max 16 wavefronts (wavefrontsPerSimd in Vulkan)
	- wavefront can be 32 or 64 threads (Vulkan: minSubgroupSize=32, maxSubgroupSize=64, wavefrontSize=64)

* 6900 XT performance: [5]
	- Ray/box: 15 GRays/s
	- Ray/triangle: 2.8 GRays/s

* PS5: [specs](https://www.techpowerup.com/gpu-specs/playstation-5-gpu.c3480)
	- Memory: 16 GB, 256bit, GDDR6, 448GB/s
	- GPU with 36 CU, 2.2GHz
	- GPU perf: 10.3 TFLOPS
	- L2 Cache: 4 MB
	- Pixel Rate: 142.9 GPixel/s
	- Texture Rate: 321.6 GTexel/s

* SteamDeck: [specs](https://www.techpowerup.com/gpu-specs/steam-deck-gpu.c3897)
	- Memory: 16GB, LPDDR5, 128 bit, 88GB/s, (72 GB/s from tests [2]) 
	- GPU with 8 CU, 1.6GHz
	- L0 Cache: 32 KB per WGP, latency: 54ns, bandwidth: 1.4TB/s [2]
	- L1 Cache: 128 KB per Array, latency: 80ns, bandwidth: 823 GB/s [2]
	- L2 Cache: 1024 KB, latency: 128ns, bandwidth: 446 GB/s [2]
	- L3 Cache: 8 MB, latency: 395ns [2]
	- GPU perf: 1.6 TFLOPS
	- Pixel Rate: 25.60 GPixel/s
	- Texture Rate: 51.20 GTexel/s
	- GPU to CPU, copy engine: 43.8 GB/s, compute shader: 34.8 GB/s [2]
	- CPU to GPU, copy engine: 43.7 GB/s, compute shader: 34.6 GB/s [2]

