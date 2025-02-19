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

## Features

* Hardware ray tracing.
* Mesh shading.
* AV1.

## Specs

