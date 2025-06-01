
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

## Notes

* AVX512 extensions: F, CD, VL, DQ, BW, IFMA, VBMI, VBMI2, VPOPCNTDQ, BITALG, VNNI, VPCLMULQDQ, GFNI, VAES, **VP2INTERSECT**


# Rocket Lake (2021)
11th generation.<br/>
**Cypress Cove** microarchitecture.

## References

1. [Was Rocket Lake Power Efficient?](https://chipsandcheese.com/2022/12/17/was-rocket-lake-power-efficient/)

## Notes

* SHA instructions.
* Celeron and Pentium processors supports AVX2.



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
* Intel Processor N100, N200

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


# Twin Lake (2024)
**Skymont** microarchitecture for efficiency core.<br/>
"Twin Lake" is codename for a line of low-power x86-64 processors.

## Examples

**Twin Lake-N**
* Intel Processor N150, N250, N350, N355

## References

1. [Intel Nx50 Series "Twin Lake" Pure E-core Processor Line Powered by "Skymont" Surfaces](https://www.techpowerup.com/330317/intel-nx50-series-twin-lake-pure-e-core-processor-line-powered-by-skymont-surfaces)

## Notes

* AVX2, AVX-VNNI
* E-core: without SMT.
* two "Skymont" E-core clusters sharing an L3 cache. [1]



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

## Notes

* Arc Graphics

* P-core Cache:
	- L1 Instruction: 64 KB per core
	- L1 Data: 48 KB per core
	- L2: 2 MB per core
* E-core and LP E-core Cache:
	- L1 Instruction: 64 KB per core (per 2 cores?)
	- L1 Data: 32 KB
	- L2: 2 MB per cluster
* Memory: dual-channel DDR5-5600, dual-channel LPDDR5X-7467.
* AVX-IFMA instructions.


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

## Notes

* SHA-512, AVX-IFMA instructions.
* Memory: DDR5-5600, DDR5-10000.

* Lion Cove P-core:
	* Removed Simultaneous multithreading (SMT).
	* AVX512 supported but disabled.


# Lunar Lake (2024)
Core Ultra 200V Series.

## Examples

**Mobile**
* Core Ultra 9 288V
* Core Ultra 5 226V

## References

1. [Intel Unveils Lunar Lake Architecture: New P and E cores, Xe2-LPG Graphics, New NPU 4 Brings More AI Performance](https://www.anandtech.com/show/21425/intel-lunar-lake-architecture-deep-dive-lion-cove-xe2-and-npu4)

## Notes

* SHA-512 instructions.
* Memory: LPDDR5X-8533


# Sapphire Rapids (2023)
Server CPU.<br/>
**Golden Cove** microarchitecture.

## Examples

* Xeon Max 9480
* Xeon Platinum 8400
* Xeon Gold 5400, 6400
* Xeon Silver 4400

## Notes

* AVX512 extensions: F, CD, VL, DQ, BW, IFMA, VBMI, VBMI2, BITALG, VNNI, GFNI, VPOPCNTDQ, VPCLMULQDQ, VAES, BF16, FP16


# Granite Rapids (2024)
Server CPU.<br/>

## Notes

* AVX10.1 instructions.


# Future

* [Intel Unveils AVX10 and APX Instruction Sets: Unifying AVX-512 For Hybrid Architectures](https://www.anandtech.com/show/18975/intel-unveils-avx10-and-apx-isas-unifying-avx512-for-hybrid-architectures-)

