
# Sandy Bridge (2010)

## References

1. [Wiki Chip](https://en.wikichip.org/wiki/Sandy_Bridge)
2. [Intel’s Sandy Bridge Microarchitecture](https://www.realworldtech.com/sandy-bridge/)
3. [7-Zip LZMA Benchmark](https://www.7-cpu.com/cpu/SandyBridge.html)

## Notes

* AVX support.


# Ivy Bridge (2011)

## References

1. [Wiki Chip](https://en.wikichip.org/wiki/intel/microarchitectures/ivy_bridge)
2. [7-Zip LZMA Benchmark](https://www.7-cpu.com/cpu/IvyBridge.html)

# Haswell (2013)

## References

1. [Wiki Chip](https://en.wikichip.org/wiki/Haswell)
2. [Intel’s Haswell CPU Microarchitecture](https://www.realworldtech.com/haswell-cpu/)
3. [7-Zip LZMA Benchmark](https://www.7-cpu.com/cpu/Haswell.html)
4. [Intel's Haswell Architecture Analyzed: Building a New PC and a New Intel](https://www.anandtech.com/show/6355/intels-haswell-architecture/10)

## Notes

* AVX2 support.
* DDR4 support.

* reorder buffer: 192 micro ops. [1]
* Integer register file: 168. [1]
* fp register file: 168. [1]

* Cache: [1]
	- L1I: 32KB, 8-way
	- L1D: 32KB, 8-way, load: 64B/cy, store: 32B/cy, latency: 4-5cy.
	- L2: 256KB, 8-way, to L1: 64B/cy, latency: 11-12cy.
	- L3: 2MB per core, latency: 36cy. [3]
	- L4: 128MB per package


# Broadwell (2014)
5th generation.<br/>

## References

1. [7-Zip LZMA Benchmark](https://www.7-cpu.com/cpu/Broadwell.html)



# Skylake (2015)
6th generation.<br/>

## References

1. [7-Zip LZMA Benchmark](https://www.7-cpu.com/cpu/Skylake.html), [Skylake_X](https://www.7-cpu.com/cpu/Skylake_X.html)

## Examples

**Skylake H**
* i5 6300HQ
* i7 6820HK

**Skylake U**
* i3 6100U
* i7 6600U

**Skylake S**
* i7 6700K


## References

1. [WikiChip](https://en.wikichip.org/wiki/intel/microarchitectures/skylake)

## Notes

* EU:
	* Most general purpose ALU operations execute at up to 4 ops/cycle for 8, 32 and 64-bit registers. (16-bit throughput varies per op, can be 4, 3.5 or 2 op/cycle). [1]
	* Vector moves have throughput of 4 op/cycle. [1]
	* Vector ALU ops are often "standardized" to latency of 4. [1]
	* Fused multiply-add ops have latency of 4 and throughput of 0.5 op/cycle. (32 FLOPS/cy) [1]
	* Throughput of vADDps, vSUBps, vCMPps, vMAXps, their scalar and double analogs is increased to 2 op/cycle. Lower latency SIMD FP-add unit on port 1 removed in favour of running all FP math on the FMA units. [1]
	* Throughput of vPSLxx and vPSRxx with immediate (i.e. fixed vector shifts) is increased to 2 op/cycle, along with VPSxxVx variable shifts. [1]
	* Throughput of vANDps, vANDNps, vORps, vXORps, their scalar and double analogs, vPADDx, vPSUBx is increased to 3 op/cycle. [1]
	* vDIVPD, vSQRTPD have approximately twice as good throughput: from 8 to 4 and from 28 to 12 cycles/op. [1]
	* Throughput of some MMX ALU ops (such as PAND mm1, mm2) is decreased to 2 or 1 op/cycle (users are expected to use wider SSE/AVX registers instead). [1]

* Cache:
	- L1: 32KB, 8-way, 4 cycles for fastest load-to-use
	- L2: 256KB, 4-way, 12 cycles for fastest load-to-use
	- L3: 2MB per core, 16-way
	- L2 to L3: 32B/cy read/write per core
	- L2 to L1 (load): 64B/cy
	- L1 to L2 (store): 32B/cy


# Kaby Lake (2016)
7th generation.<br/>
**Skylake** microarchitecture.

## Examples

**Desktop**
* Core i7 7700

**Desktop (Kaby Lake-X)**
* Core i7 7740X

**Mobile**
* Core i5 7440HQ, 7300HQ
* Core i7 7500U

## References

1. [WikiChip](https://en.wikichip.org/wiki/Kaby_Lake)


# Kaby Lake Refresh (2017)
8th generation.<br/>
**Skylake** microarchitecture.

## Examples

**Mobile**
* i5 8250U

## References

1. [WikiChip](https://en.wikichip.org/wiki/intel/cores/kaby_lake_r)

## Notes

* Dual-channel Memory, Up to DDR4-2400, LPDDR3-2133. [1]
* Everything up to AVX2 (SMM, FPU, NX, MMX, SSE, SSE2, SSE3, SSSE3, SSE4.1, SSE4.2, AES, AVX1, AVX2) [1]
* Graphics: UHD Graphics 620 (Gen9.5 GT2) [1]



# Gemini Lake (2017)
**Goldmont Plus** microarchitecture.

## Examples

**Desktop**
* Celeron J4105
* Pentium Silver J5005

**Mobile**
* Celeron N4000, N4100

**Mobile (Gemini Lake Refresh)**
* Celeron N4020


# Cannon Lake (2018)
9th generation.<br/>
**Skylake** microarchitecture.

## References

1. [Cannon Lake: Intel’s Forgotten Generation](https://chipsandcheese.com/2022/11/15/cannon-lake-intels-forgotten-generation/)

## Notes

* SHA instructions.
* AVX512 extensions: F, CD, VL, DQ, BW, IFMA, VBMI


# Ice Lake (2019)
10th generation.<br/>
**Sunny Cove** microarchitecture.

## References

1. [7-Zip LZMA Benchmark](https://www.7-cpu.com/cpu/Ice_Lake.html)

## Notes

* AVX512 extensions: F, CD, VL, DQ, BW, IFMA, VBMI, **VBMI2, VPOPCNTDQ, BITALG, VNNI, VPCLMULQDQ, GFNI, VAES**


# Tiger Lake (2020)
11th generation.<br/>
**Willow Cove** microarchitecture.

## Examples

* Core i7 1185G7
* Core i7 11800H

## Notes

* AVX512 extensions: F, CD, VL, DQ, BW, IFMA, VBMI, VBMI2, VPOPCNTDQ, BITALG, VNNI, VPCLMULQDQ, GFNI, VAES, **VP2INTERSECT**

## Tests

<details><summary>AIDA64</summary>

* Core i7 1185G7:
	- clock: 2.998 GHz
	- cores: 4
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 2'122 | 1'073 | 2'129 | 1.1  | 3  |
	  | L2 | 716   | 317   | 455   | 4.1  | 12 |
	  | L3 | 204   | 100   | 123   | 20.0 | 60 |

* Core i7 11800H:
	- clock: 4.2 GHz
	- cores: 8
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 4'080 | 2'054 | 4'133 | 1.2  | 5  |
	  | L2 | 1'176 | 646   | 903   | 4.5  | 19 |
	  | L3 | 268   | 144   | 136   | 19.4 | 81 |

</details>


# Rocket Lake (2021)
11th generation.<br/>
**Cypress Cove** microarchitecture.

## Examples

* Core i7 11700K

## References

1. [Was Rocket Lake Power Efficient?](https://chipsandcheese.com/2022/12/17/was-rocket-lake-power-efficient/)

## Notes

* SHA instructions.
* Celeron and Pentium processors supports AVX2.

## Tests

<details><summary>AIDA64</summary>

* Core i7 11700K:
	- clock: 4.888 GHz
	- cores: 8
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 4'513 | 2'280 | 4'572 | 1.0  | 5  |
	  | L2 | 1'554 | 666   | 1'058 | 2.7  | 13 |
	  | L3 | 312   | 205   | 243   | 12.0 | 59 |

</details>


# Alder Lake (2021)
12th-generation.<br/>
**Golden Cove** microarchitecture for performance core, **Gracemont** microarchitecture for efficiency core.

## Examples

**Alder Lake-S**
* Core i9 12900

**Alder Lake-U**
* Celeron 7300
* Pentium 8500
* Core i3 1210U
* Core i7 1265U

**Alder Lake-N**
* Core i3 N300
* Intel Processor N95, N100, N200

**Alder Lake-P**
* Core i7 1280P
* Core i5 1240P
* Core i3 1220P

**Alder Lake-H**
* Core i9 12900HK
* Core i7 12650H
* Core i5 12450H

**Alder Lake-HX**
* Core i9 12950HX
* Core i7 12800HX
* Core i5 12600HX

## References

1. [Wiki Chip](https://en.wikichip.org/wiki/intel/microarchitectures/alder_lake)
2. [Intel Details Golden Cove: Next-Generation Big Core For Client and Server SoCs](https://fuse.wikichip.org/news/6111/intel-details-golden-cove-next-generation-big-core-for-client-and-server-socs/)

## Notes

* Removed AVX512 support.
* E-core: without SMT.
* Some common integer ALU ops (CMP,TEST,AND,OR,XOR,LEA) increased throughput by 1 insn/cycle. [1]
* Vector floating point addition/subtraction latency decreased from 4 to 2 cycles. [1]
* Golden Cove: [1]
	- AI workload improvement (AMX)
	- Add one ALU and LEA for a total 5
* Gracemont: [1]
	- 4 ALU SIMD (32 FLOPS/cy ?)
	- AVX2
* AVX-IFMA instructions.

## Tests

<details><summary>AIDA64</summary>

* Core i9 12900H:
	- clock: 4.5 GHz
	- cores: 6P + 8E
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 2'737 | 1'049 | 3'140 | 1.1  | 5  |
	  | L2 | 769   | 355   | 669   | 4.0  | 18 |
	  | L3 | 310   | 275   | 344   | 18.7 | 84 |

* Core i3 12100:
	- clock: 4.3 GHz
	- cores: 4
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 1'400 | 1'020 | 1'740 | 1.2  | 5  |
	  | L2 | 643   | 260   | 450   | 4.2  | 18 |
	  | L3 | 344   | 185   | 254   | 15.8 | 68 |

* M95:
	- clock: 3.4 GHz
	- cores: 4
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 335 | 300 | 607 | 0.9  | 3 |
	  | L2 | 150 | 41  | 73  | 5.9  | 20 |
	  | L3 | 56  | 25  | 41  | 14.9 | 51 |

</details>


# Twin Lake (2024)
**Skymont** microarchitecture for efficiency core.<br/>
"Twin Lake" is codename for a line of low-power x86-64 processors.

## Examples

**Twin Lake-N**
* Intel Processor N150, N250, N350, N355

## References

1. [Intel Nx50 Series "Twin Lake" Pure E-core Processor Line Powered by "Skymont" Surfaces](https://www.techpowerup.com/330317/intel-nx50-series-twin-lake-pure-e-core-processor-line-powered-by-skymont-surfaces)
2. [Intel Details Skymont](https://chipsandcheese.com/p/intel-details-skymont)

## Notes

* AVX2, AVX-VNNI
* E-core: without SMT.
* two "Skymont" E-core clusters sharing an L3 cache. [1]
* iGPU with Xe-LPG graphics architecture. [1]


# Raptor Lake (2022)
13th generation.<br/>
**Raptor Cove** microarchitecture for performance cores, Enhanced **Gracemont** microarchitecture for efficient cores.

## Examples

**Raptor Lake-S**
* Core i9 13900K
* Core i5 13600K

**Raptor Lake-HX**
* Core i7 13850HX

**Raptor Lake-H**
* Core i5 13500H

**Raptor Lake-U**
* Core i7 1355U
* Core i5 1335U

## References

1. [Wiki Chip](https://en.wikichip.org/wiki/intel/microarchitectures/raptor_lake)

## Notes

* P-core Cache:
	- L1 Instruction: 32 KB per core
	- L1 Data: 48 KB per core
	- L2: 2 MB per core
* E-core Cache:
	- L1 Instruction: 64 KB per core
	- L1 Data: 32 KB per core
	- L2: 4 MB per cluster

* iGPU: UHD 7xx

## Tests

<details><summary>AIDA64</summary>

* Core i9 13900K:
	- clock: 5.5 GHz
	- cores: 8P + 16E
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 5'816 | 4'214 | 8'389 | 0.9  | 5  |
	  | L2 | 1'458 | 657   | 1'046 | 3.7  | 20 |
	  | L3 | 1'296 | 600   | 915   | 13.7 | 75 |

* Core i7 13620H:
	- clock: 4.5 GHz
	- cores: 6P + 4E
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 2'600 | 1'900 | 3'420 | 1.1  | 5  |
	  | L2 | 897   | 380   | 574   | 4.0  | 18 |
	  | L3 | 314   | 277   | 310   | 15.4 | 70 |

* Core i5 1335U:
	- clock: 4.3 GHz
	- cores: 2P + 8E
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 1'450 | 732 | 1'775 | 1.1  | 5  |
	  | L2 | 454   | 119 | 237   | 4.0  | 20 |
	  | L3 | 140   | 100 | 127   | 15.5 | 67 |

</details>


# Raptor Lake Refresh (2023)
14th generation.<br/>

## Examples

**Raptor Lake-U Refresh**
* Core 3 100U, 5 120U, 7 150U

**Raptor Lake-U Refresh**
* Core 7 250U
* Core 5 220U

**Raptor Lake-H Refresh**
* Core 9 270H
* Core 7 240H
* Core 5 210H

**Raptor Lake-S Refresh**
* Core i9 14900K
* Core i5 14500T

**Raptor Lake-HX Refresh**
* Core i9 14900HX

## References

1. [Intel Core i9-14900KS Review](https://www.anandtech.com/show/21378/intel-core-i9-14900ks-review-the-swan-song-of-raptor-lake-with-a-super-fast-6-2-ghz-turbo)
2. [Intel Core i9-14900K, Core i7-14700K and Core i5-14600K Review](https://www.anandtech.com/show/21084/intel-core-i9-14900k-core-i7-14700k-and-core-i5-14600k-review-raptor-lake-refreshed)

## Notes

* Cache: [from tests]
	- L1D: latency 5cy
	- L2: latency 20cy
	- L3: latency 74cy

## Tests

<details><summary>AIDA64</summary>

* Core i9 14900KF
	- clock: 5.6 GHz
	- cores: 8P + 16E
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 6'249 | 3'510 | 8'562 | 0.9  | 5  |
	  | L2 | 1'237 | 645   | 1'066 | 3.6  | 20 |
	  | L3 | 868   | 524   | 868   | 13.2 | 74 |

* Core i5 14600K:
	- clock: 6 GHz
	- cores: 6P + 8E
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 4'192 | 3'050 | 6'036 | 0.8  | 5  |
	  | L2 | 1'404 | 496   | 748   | 3.4  | 20 |
	  | L3 | 830   | 428   | 719   | 11.4 | 68 |

</details>


# Meteor Lake (2023)
Core Ultra Series 1.

## Examples

**Meteor Lake-H**
* Core Ultra 9 185H
* Core Ultra 7 155H, 165H
* Core Ultra 5 125H

**Meteor Lake-U**
* Core Ultra 5 115U, 125U, 135U
* Core Ultra 7 155U, 165U

## References

1. [The Intel Core Ultra 7 155H Review](https://www.anandtech.com/show/21282/intel-core-ultra-7-115h-review-meteor-lake-makes-makes-fresh-start-to-mobile-cpus)
2. [Intel Releases Core Ultra H and U-Series Processors](https://www.anandtech.com/show/21185/intel-releases-core-ultra-h-and-u-series-processors-meteor-lake-brings-ai-and-arc-to-ultra-thin-notebooks)
3. [Intel Meteor Lake Technical Deep Dive](https://www.techpowerup.com/review/intel-meteor-lake-technical-deep-dive/)
4. [Intel Details Skymont](https://chipsandcheese.com/p/intel-details-skymont) - compared with Crestmont

## Notes

* Arc Graphics (Xe-LPG)

* Memory: dual-channel DDR5-5600, dual-channel LPDDR5X-7467.
* AVX-IFMA instructions.

### Redwood Cove P-core

* Cache:
	- L1 Instruction: 64 KB per core
	- L1 Data: 48 KB per core
	- L2: 2 MB per core
	- L3: shared with E-cores, up to 24 MB

### Crestmont E-core

* Performance:
	- A FP multiply with a subnormal result costs over 280 cycles on Crestmont. [4]

* Cache:
	- L1 Instruction: 64 KB per core
	- L1 Data: 32 KB, read 2x 16B/cy [4]
	- L2: 2 MB per cluster
	- L3: shared with P-cores, up to 24 MB
	- L3 to L2: 16 B/cy [4]

### Crestmont LP E-core

* Cache:
	- L1 Instruction: 64 KB per core (per 2 cores?)
	- L1 Data: 32 KB
	- L2: 2 MB per cluster

## Tests

<details><summary>AIDA64</summary>

* Core Ultra 5 125H:
	- clock: 4.3 GHz (specs: 4.5 + 3.6 + 2.5)
	- cores: 4P + 8E + 2LP
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 1'210 | 1220 | 1'850 | 1.1  | 5   |
	  | L2 | 550   | 260  | 330   | 4.6  | 20  |
	  | L3 | 530   | 270  | 350   | 23.7 | 102 |

* Core Ultra 7 155H:
	- clock: 1.6 GHz (specs: 4.8 + 3.8 + 2.5)
	- cores: 6P + 8E + 2 LP
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 1'120 | 1'150 | 2'270 | 1.1  | 5  |
	  | L1 | 584   | 330   | 395   | 4.6  | 20 |
	  | L1 | 538   | 364   | 457   | 22.1 | 95 |

</details>


# Arrow Lake (2024)
Core Ultra Series 2.

## Examples

**Desktop**
* Core Ultra 9 285
* Core Ultra 5 245

**Arrow Lake-U**
* Core Ultra 7 265U
* Core Ultra 5 225U

**Arrow Lake-H**
* Core Ultra 9 285H
* Core Ultra 5 225H

**Arrow Lake-HX**
* Core Ultra 9 275HX
* Core Ultra 5 235HX

## References

1. [Examining Intel’s Arrow Lake, at the System Level](https://chipsandcheese.com/2024/12/04/examining-intels-arrow-lake-at-the-system-level/)
2. [Intel’s Lion Cove P-Core and Gaming Workloads](https://chipsandcheese.com/p/intels-lion-cove-p-core-and-gaming)
3. [Intel Core Ultra Arrow Lake Preview](https://www.techpowerup.com/review/intel-core-ultra-arrow-lake-preview/)
4. [Analyzing Lion Cove’s Memory Subsystem in Arrow Lake](https://old.chipsandcheese.com/2025/01/05/analyzing-lion-coves-memory-subsystem-in-arrow-lake/)
5. MicroBenchmarks: [cache](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench-cpu/MemAccess.md#Intel-Ultra-7-255H), [FLOPS](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench-cpu/SIMD_FLOPS.md#Intel-Ultra-7-255H-P-core)
6. [Skymont in Gaming Workloads](https://chipsandcheese.com/p/skymont-in-gaming-workloads)
7. [Intel Details Skymont](https://chipsandcheese.com/p/intel-details-skymont)

## Notes

* SHA-512, AVX-IFMA, AVX-VNNI instructions.
* Memory: DDR5-5600, DDR5-10000.

* Arrow Lake-S/HX with Xe-LPG
* Arrow Lake-H with Arc Graphics 130T, 140T (Xe-LPG+)
* 10-13 TOPS i8 NPU

### Lion Cove P-core

* Removed Simultaneous multithreading (SMT).
* AVX512 supported but disabled.

* performance:
	- 2x fp32 256-bit FMA pipes, 32 FLOPS/cy
	- 2x i32 256-bit pipes, 16 OPS/cy
	- in tests achieve only 60-70% of theoretical fp32 FMA performance [5]
	- 576 entry reorder buffer [6]

* Cache: [4]
	- L1 Instruction: 64 KB per core
	- L1 Data: 48 KB per core, read 128 B/cy, write 64 B/cy, 4cy
	- L1.5 Data: 192 KB per core, *64 B/cy ?*, 9cy
	- L2: 3 MB per core, *32 B/cy ?*, 17cy
	- L3: shared with E-cores, ~84cy

* L1.5 basically replaces the L2 as the primary data source for L1D misses. [4]

### Skymont E-core

* performance:
	- 4x fp32 128-bit FMA pipes, 32 FLOPS/cy [5, 7]
	- 4x i32 128-bit pipes, 16 OPS/cy
	- 8 micro-ops per cycle. [6, 7]
	- 416 entry reorder buffer [6]
	- in tests achieve 90% of theoretical fp32 FMA performance [5]
	- adds fast path hardware to handle subnormal floating point numbers. [7]

* Cache: [4, 5, 6]
	- L1 Instruction: 64 KB per core, read 3x 32B/cy [7]
	- L1 Data: 32 KB per core, read 3x 16B/cy, write 32 B/cy, 4cy [7]
	- L2: 4 MB per cluster (4 cores), read 64 B/cy per core, 128 B/cy total, 17cy [7]
	- L3 to L2: 32 B/cy [7]
	- L3: shared with P-cores


### Skymont LP E-core

* performance:
	- 2x fp32 128-bit FMA pipes, 16 FLOPS/cy [5]
	- 2x i32 128-bit pipes, 8 OPS/cy
	- 256-bit ops are split into 2x 128-bit uops internally.

* Cache:
	- L1 Instruction: 64 KB per core
	- L1 Data: 32 KB, read 64 B/cy, write 32 B/cy [5]
	- L2: 4 MB per cluster (4 cores), 64 B/cy


## Tests

<details><summary>AIDA64</summary>

* Core Ultra 7 265K:
	- clock: 5.186 GHz (5.4 + 4.6)
	- cores: 8P + 12E
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1   | 5'009 | 3'535 | 7'244 | 0.8  | 4   |
	  | L1.5 | 1'361 | 639   | 1'164 | 1.7  | 8   |
	  | L2   | 673   | 592   | 750   | 4.2  | 22  |
	  | L3   | 1'197 | 648   | 933   | 19.5 | 100 |

* Core Ultra 9 275HX:
	- clock: 5.19 GHz
	- cores: 8P + 16E
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1   | 4'920 | 3'580 | 6'800 | 0.8  | 4 |
	  | L1.5 | 1'190 | 572   | 873   | 1.8  | 9 |
	  | L2   | 549   | 588   | 750   | 4.3  | 22 |
	  | L3   | 700   | 640   | 700   | 20.9 | 108 |

</details>


# Lunar Lake (2024)
Core Ultra 200V Series.

## Examples

**Mobile**
* Core Ultra 9 288V
* Core Ultra 5 226V

## References

1. [Intel Unveils Lunar Lake Architecture: New P and E cores, Xe2-LPG Graphics, New NPU 4 Brings More AI Performance](https://www.anandtech.com/show/21425/intel-lunar-lake-architecture-deep-dive-lion-cove-xe2-and-npu4)

## Notes

* SHA-512, AVX-IFMA, AVX-VNNI instructions.
* Memory: LPDDR5X-8533
* Arc Graphics 130V, 140V (Xe2-LPG)
* 47-48 TOPS i8 NPU

### Lion Cove P-core

* Same as Arrow Lake

### Skymont E-core

* Same as Arrow Lake
* Lunar Lake's cluster of 4 Skymont E-cores exist on a 'Low Power Island' separate from the P-cores. As a result, the E-cores have their own dedicated L3 cache not accessible to the P-cores. [[wiki](https://en.wikipedia.org/wiki/Lunar_Lake)]

## Tests

<details><summary>AIDA64</summary>

* Core Ultra 9 288V:
	- clock: 4.6 GHz (5.1 + 3.7)
	- cores: 4P + 4E
	- | cache | read | write | copy | latency | cycles |
	  |---|---|---|---|---|---|
	  | L1 | 1'865 | 1'350 | 2'680 | 0.8  | 4 |
	  | L2 | 396   | 281   | 340   | 4.3  | 20 |
	  | L3 | 470   | 250   | 380   | 10.9 | 50 |

</details>


# Panther Lake (2025)
Core Ultra Series 3

## References

1. [Intel Panther Lake Technical Deep Dive](https://www.techpowerup.com/review/intel-panther-lake-technical-deep-dive/)
2. [Panther Lake’s Reveal at ITT 2025](https://chipsandcheese.com/p/panther-lakes-reveal-at-itt-2025)

* P-core: [1]
	- Cougar Cove architecture

* P-core cache: [1]
	- L1I: ?
	- L1D: 48 KB
	- L1.5D: 192 KB
	- L2: 3 MB per core
	- L3: up to 18MB shared

* E-core, LP-core: [1]
	- Darkmont architecture

* E-core cache: [1]
	- L1I: 64 KB
	- L1D: 32 KB
	- L2: 4 MB per cluster

* iGPU on Xe3 architecture. [1]
* NPU 5: [1]
	- up to 50 TOPS (i8 ?)
	- FP8

* Compute tile has the main CPU complex, the Low Power CPU complex, the ISP, the NPU, the Media engines, and the 8MB Memory Side Cache alongside the 128b memory bus. [2]
* Starting with the smallest Panther Lake configuration, we have 4 P-Cores and 4 LP E-Cores paired with 8MB Memory-side Cache on the Compute Tile. [2]
	- That Compute Tile is paired with a 4 core Xe3 iGPU.
* In middle configuration of Panther Lake the Compute Tile now has 4 P-Cores and 8 E-Cores which share a 18MB L3 cache with an extra 4 LP E-Cores, all of which can access the 8MB memory-side cache on board the Compute tile. [2]

* Intel had increased the TLB capacity by 50% compared to Lion Cove along with improving the branch predictor by increasing some of the structure sizes in the BPU along with porting over some of the novel BPU algorithms that Intel tested in Lunar Lake. [3.1]


# Future

* [Intel Unveils AVX10 and APX Instruction Sets: Unifying AVX-512 For Hybrid Architectures](https://www.anandtech.com/show/18975/intel-unveils-avx10-and-apx-isas-unifying-avx512-for-hybrid-architectures-)

