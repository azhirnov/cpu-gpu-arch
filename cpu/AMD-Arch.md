**CCX** - Core Complexes<br/>
**CCD** - Core Complex Die<br/>
**IOD**, I/OD - Input/Output Die<br/>


# K10 (2007)

## Examples

* Phenom  
* Phenom II
* Athlon X2
* Athlon II
* Sempron
* Sempron X2

## References

## Notes

* 8x fp32 FLOPS/cy, 4x fp64 FLOPS/cy.


# Bulldozer (2011)

## Examples

* FX-8100, FX-6200, FX-4150

## References

1. [AMD’s Bulldozer Microarchitecture](https://www.realworldtech.com/bulldozer/)

## Notes

* AVX instructions.
* AES instructions.

* 16x fp32 FLOPS/cy, 8x fp64 FLOPS/cy.


# Piledriver (2012)

## Examples

* FX-9590, FX-8350, FX-4350
* A10-6800K, A8-6600K, A4-4000



# Steamroller (2014)



# Excavator (2015)

## Examples

* Athlon X4

## Notes

* AVX2 instructions.


# Zen (2017)

## Examples

## References

1. [Wiki Chip](https://en.wikichip.org/wiki/amd/microarchitectures/zen)
2. [7-Zip LZMA Benchmark](https://www.7-cpu.com/cpu/Zen.html)

## Notes

* SHA instructions.
* 16x fp32 FLOPS/cy, 8x fp64 FLOPS/cy.

# Zen+

## Examples

## References

1. [Wiki Chip](https://en.wikichip.org/wiki/amd/microarchitectures/zen%2B)


# Zen 2 (2019)

## Examples

* Ryzen 3000 series (Matisse)
* Ryzen 4000U/H series (Renoir)
* Ryzen 5000U series (Lucienne)
* Threadripper 3000 series
* Ryzen 5 7520U, Ryzen 3 7320U
* Xbox Series X and Series S
* PlayStation 5
* Steam Deck

## References

1. [Zen 2 wiki](https://en.wikipedia.org/wiki/Zen_2)
2. [Van Gogh, AMD’s Steam Deck APU](https://chipsandcheese.com/2023/03/05/van-gogh-amds-steam-deck-apu/)
3. [Wiki Chip](https://en.wikichip.org/wiki/amd/microarchitectures/zen_2)
4. [Ryzen 3900X, Wiki Chip](https://en.wikichip.org/wiki/amd/ryzen_9/3900x)
5. [AMD Zen 2 Microarchitecture Analysis](https://www.anandtech.com/show/14525/amd-zen-2-microarchitecture-analysis-ryzen-3000-and-epyc-rome)
6. [A Look At The AMD Zen 2 Core](https://fuse.wikichip.org/news/2458/a-look-at-the-amd-zen-2-core/)
7. [Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/CPU_Benchmarks.md)
8. [7-Zip LZMA Benchmark](https://www.7-cpu.com/cpu/Zen2.html)

## Notes

* FPU:
	- 32x fp32 FLOPS/cy, 16x fp64 FLOPS/cy. [3, 6]
	- The 36-entry out-of-order scheduler issues up to 4 micro-ops per cycle to the execution pipelines. [3]
	- float register file: 160 entry. [3]
	- The PRF has 8 read ports and 4 write ports for ALU results, each 256 bits wide and two additional write ports supporting up to two 256-bit load operations per cycle. [3]
	- The latency of fused multiply-add (FMA) instructions remains 5 cycles. [3]
	
* Integer unit: [3]
	- register file: 180
	- reorder buffer: 224
	- 8/16/32/64 bit signed integer division/modulo latency: 17/22/30/46 cycles.

* Cache:
	- L1I: 32KB, 4-way, 64B line, 32B/cy from L2. [3]
	- L1D: 32KB, 8-way. [3]
		* 4-5 cycles latency for Int [3]
		* 7-8 cycles latency for FP [3]
	- L2: 512KB, 8-way, ≥ 12 cycles latency. [3, 6]
	- L3: 16-way, 16MB per CCX (4 cores), 4x slices of 4MB, 64B line. [3]
	- Each core in CCX can access all L3 slices with the same average load-to-use latency of 39 cycles. [3]
	- L3 to L2: 32B. [3]
	- L2 to L1: 32B/cy. [3]

* LSU: [3]
	- Three largely independent pipelines can execute up to two 256-bit load operations and one 256-bit store per cycle. (64B/cy L1 read, 32B/cy L2 write?)
	- Aligned and unaligned load and store instructions (for example MOVUPS/MOVAPS) provide identical performance.
	- The DC load-to-use latency is 4 cycles to the integer unit, 7 cycles to the FPU.
	- Can track up to 22 in-flight cache misses, these are recorded in the miss address buffer (MAB).

* Ryzen 3900 performance: [7]
	- L1: ? *(64B/cy * 4.2 GHz = 269 GB/s)*
	- L2: 134.5 GB/s per core *(32B/cy * 4.2 GHz = 134 GB/s)*
	- L3: 93.6 GB/s per core?


# Zen 3 (2020)

## Examples

* Ryzen 9 5950X
* Ryzen 7 6800U
* Threadripper PRO 5995WX

## References

1. [Wiki Chip](https://en.wikichip.org/wiki/amd/microarchitectures/zen_3)
2. [GDC2022 AMD Ryzen Processor Software Optimization](https://gpuopen.com/gdc-presentations/2022/GDC_AMD_Ryzen_Processor_Software_Optimization.pdf), [[video](https://youtu.be/helEx02HN_I)], [[backup](../pdf/AMD-GDC_Ryzen_Processor_Software_Optimization.pdf)]

## Notes

* FPU: [1]
	- FMA latency reduced by 1 cycle from 5 to 4.
	- Fifth and sixth dedicated execution ports added for floating point store and FP-to-int transfer, no longer sharing 2nd FADD port.
	- Unified scheduler split into 1 scheduler per FMA/FADD/transfer port set.

* Integer unit: [1]
	- Integer register file: 192 entries.
	- Schedulers shared between pairs of ALU + AGU/branch ports instead of dedicated for each.
	- 8/16/32/64 bit signed integer division/modulo latency: 10/12/14/20 cycles.

* Cache: [1]
	- Increased L3 latency (~46 cycles).
	
* LSU: [1]
	- Load throughput increased from 2 to 3, if not 256b.
	- Store throughput increased from 1 to 2, if not 256b.

* New Instructions: VAES, VPCLMULQDQ. [1]


# Zen 4 (2022)

## Examples

**Desktop**
* Ryzen 9 7900X
* Threadripper 7980X

**Desktop APU**
* Ryzen 7 8700G

**Phenix APU**
* Ryzen 7 8700F

**Mobile Phenix**
* Ryzen 9 7940HS
* Ryzen 3 7440U
* Ryzen 5 7545U, Ryzen 3 7440U *(Phenix2 with Zen4c)*

**Mobile Dragon Range**
* Ryzen 9 7945HX

**Mobile Hawk Point** (Phenix refresh)
* Ryzen 9 8945HS
* Ryzen 7 8840U, 8745HS
* Ryzen 5 8540U, Ryzen 3 8440U *(with Zen4c)*

**Hawk Point Refresh**
* Ryzen 9 270
* Ryzen 7 Pro 250
* Ryzen 5 Pro 220, Ryzen 3 210 *(with Zen4c)*

## References

1. [AMD’s Zen 4 Part 1: Frontend and Execution Engine](https://chipsandcheese.com/2022/11/05/amds-zen-4-part-1-frontend-and-execution-engine/)
2. [AMD’s Zen 4, Part 2: Memory Subsystem and Conclusion](https://chipsandcheese.com/2022/11/08/amds-zen-4-part-2-memory-subsystem-and-conclusion/)
3. [AMD’s Zen 4, Part 3: System Level Stuff, and iGPU](https://chipsandcheese.com/2023/01/05/amds-zen-4-part-3-system-level-stuff-and-igpu/)
4. [Wiki Chip](https://en.wikichip.org/wiki/amd/microarchitectures/zen_4)
5. [GDC2023 AMD Ryzen Processor Software Optimization (Zen4)](https://gpuopen.com/gdc-presentations/2023/GDC-2023-AMD-Ryzen-Processor-Software-Optimization.pdf), [[backup](../pdf/AMD-GDC-2023-AMD-Ryzen-Processor-Software-Optimization.pdf)]
6. [AMD Ryzen 7 8700G and Ryzen 5 8600G Review](https://www.anandtech.com/show/21242/amd-ryzen-7-8700g-and-ryzen-5-8600g-review)
7. [AMD Ryzen Threadripper 7980X & 7970X Review](https://www.anandtech.com/show/21124/amd-ryzen-threadripper-7980x-and-7970x-review)
8. [AMD Unveils Ryzen 8000G Series Processors](https://www.anandtech.com/show/21208/amd-unveils-ryzen-8000g-series-processors-zen-4-apus-for-desktop-with-ryzen-ai)
9. [AMD Unveils Ryzen Mobile 7040U Series with Zen 4c](https://www.anandtech.com/show/21111/amd-unveils-ryzen-7040u-series-with-zen-4c-smaller-cores-bigger-efficiency)
10. [The ASUS ROG Strix Scar 17 (2023) Laptop Review: Mobile Ryzen 9 7945HX3D with 3D V-Cache Impresses](https://www.anandtech.com/show/20010/the-asus-rog-strix-scar-17-2023-laptop-review-ryzen-9-7945hx3d-with-3d-v-cache-impresses)
11. [AMD Zen 4 AVX-512 Performance Analysis On The Ryzen 9 7950X](https://www.phoronix.com/review/amd-zen4-avx512)
12. [Hiding x86 Port Latency for 330 GB/s/core Reductions](https://ashvardanian.com/posts/cpu-ports/)
13. [AMD Disables Zen 4's Loop Buffer](https://chipsandcheese.com/p/amd-disables-zen-4s-loop-buffer)

## Notes

* Cache: [4]
	- L1 Instruction: 32 KB per core, 8-way, 64 B/cy
	- L1 Data: 32 KB per core, 8-way, 32 B/cy
	- L2: 1 MB per core, 8-way, 32 B/cy, latency: 14cy
	- L3 desktop: 32 MB per CCD, 16-way, read: 32 B/cy, write: 16 B/cy, latency 50cy
	- L3 with 3D V-Cache: 96 MB per CCD
	- L3 APU: 16 MB
* reorder buffer: 320 entries. [4]
* floating-point register file: 192. [4]
* integer register file: 224. [4]
* Memory: DDR5-5200, LPDDR5X-7500
* 256 bit vector for AVX512
	- employed a 256-bit "double pumping" strategy. [11]
	- 26% - 100% performance improvement from tests. [11]
	- making use of the AVX-512 instructions led to around 59% higher performance. [11]
* AVX512 extensions: F, CD, VL, DQ, BW, IFMA, VBMI, VBMI2, VPOPCNTDQ, BITALG, VNNI, VPCLMULQDQ, GFNI, VAES, BF16
* FPU:
	- Some ALU operations on vector registers increased throughput from 2 to 3 ops/cycle. [4]
	- Some ALU operations on vector registers (VPABSx,VPHADDx,VPHSUBx,VPSLLx,VPSRLx,VPSRAx,VPACKx,VPSIGNx,VMAXx,VMINx) increased latency by 1 cycle. [4]

* `vaddps` instruction takes ports 2 and 3, and the `vfmadd132ps` instruction takes ports 0 and 1. [12]

* NPU (Ryzen AI) on XDNA architecture.

## Zen4c

* Smaller cores with the same IPC can use less power to give more performance below 15W. [9]
* L3 cache: 16MB per CCD instead of 32MB. [4]
* none of the Zen 4c chips clock higher than 3.1GHz. [9]
	- Zen 4 and Zen 4c are not identical CPU cores.
	- Zen 4c is for all practical purposes AMD’s efficiency core, and it needs to be treated as such. 
	- Phoenix 2 probably is more efficient – and thus higher scoring – in heavily multithreaded scenarios.


# Zen 5 (2024)

## Examples

**Desktop**
* Ryzen 9: 9950X, 9900X
* Ryzen 7: 9700X
* Ryzen 5: 9600X, 9600

**Desktop with 3D Cache**
* Ryzen 9 9950X3D
* Ryzen 7 9800X3D

**Mobile**
* Ryzen AI 9: HX 375, HX 370, 365
* Ryzen AI 7 360
* Ryzen AI 5 340


## References

1. [Discussing AMD’s Zen 5 at Hot Chips 2024](https://chipsandcheese.com/p/discussing-amds-zen-5-at-hot-chips-2024)
2. [The AMD Ryzen 9 9950X and Ryzen 9 9900X Review](https://www.anandtech.com/show/21524/the-amd-ryzen-9-9950x-and-ryzen-9-9900x-review)
3. [The AMD Ryzen AI 9 HX 370 Review](https://www.anandtech.com/show/21485/the-amd-ryzen-ai-hx-370-review)
4. [The AMD Ryzen 7 9700X and Ryzen 5 9600X Review](https://www.anandtech.com/show/21493/the-amd-ryzen-7-9700x-and-ryzen-5-9600x-review)
5. [The AMD Zen 5 Microarchitecture](https://www.anandtech.com/show/21469/amd-details-ryzen-ai-300-series-for-mobile-strix-point-with-rdna-35-igpu-xdna-2-npu)
6. [Quantifying The AVX-512 Performance Impact With AMD Zen 5](https://www.phoronix.com/review/amd-zen5-avx-512-9950x)
7. [Disabling Zen 5’s Op Cache and Exploring its Clustered Decoder](https://chipsandcheese.com/p/disabling-zen-5s-op-cache-and-exploring)
8. [AMD Strix Point SoC Reintroduces Dual-CCX CPU, Other Interesting Silicon Details Revealed](https://www.techpowerup.com/324872/amd-strix-point-soc-reintroduces-dual-ccx-cpu-other-interesting-silicon-details-revealed)

## Notes

* Cache:
	- L1 Instruction: 32 KB per core, 8-way, 64 B/cy
	- L1 Data: 48 KB per core, 12-way, 64 B/cy
	- L2: 1 MB per core, 16-way, 64 B/cy
	- L3 desktop: 32 MB per CCD, 16-way, read: 32 B/cy, write: 16 B/cy
	- L3 mobile: 24 MB
	- L3 with 3D V-Cache: 96 MB per CCD
* Cores:
	- desktop: 8 cores per CCD
	- mobile: 3-4 Zen5, 3-8 Zen5c
* 512 bit vector width.
	- Zen 5 AVX-512 implementation with the Ryzen 9 9950X saw its performance go up by 56% while the Ryzen 9 7950X Zen 4 with its "double pumped" AVX-512 implementation saw its performance go up by 41%. [6]
* AVX512 extensions: F, CD, VL, DQ, BW, IFMA, VBMI, VBMI2, VPOPCNTDQ, BITALG, VNNI, VPCLMULQDQ, GFNI, VAES, BF16, **VP2INTERSECT**
* AVX-VNNI instructions.
* Memory: DDR5-5600 DC 160bit (?) (112GB/s), LPDDR5X-7500 QC 128bit (120GB/s). [8]
* two-ahead branch prediction - try to predict two code paths ahead before they are executed.

## Zen 5c

