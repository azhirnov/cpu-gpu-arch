
# Intel Xe

CPU code name: Tiger Lake, Rocket Lake, Alder Lake, Raptor Lake.
Architecture: Xe-LPG (low power graphics)

## Examples

* Intel UHD Graphics 730, 770
* Iris Xe Graphics G7

## References

1.1. [Intel Processor Graphics Architecture](https://cdrdv2-public.intel.com/686065/the-architecture-of-intel-processor-graphics-gen11-r1new.pdf), [[backup](../pdf/Intel-the-architecture-of-intel-processor-graphics-gen11-r1new.pdf)]<br/>
1.2. [Intel Processor Graphics Xᵉ-LP API Developer and Optimization Guide](https://www.intel.com/content/www/us/en/developer/articles/guide/lp-api-developer-optimization-guide.html), [[webarchive](https://web.archive.org/web/20230623012301/https://www.intel.com/content/www/us/en/developer/articles/guide/lp-api-developer-optimization-guide.html)]<br/>
1.3. [Vulkan features for Iris Xe](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Iris(R)%20Xe%20Graphics), [UHD Graphics 770](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20UHD%20Graphics%20770)<br/>
1.4. [Intel’s Ambitious Meteor Lake iGPU](https://chipsandcheese.com/p/intels-ambitious-meteor-lake-igpu)

## Notes

* A XVE can have up to eight threads in flight. [1.4]
* Statically allocates register file capacity for in-flight threads. [1.4]
	- Every thread gets 128 registers, regardless of whether it needs them all. Occupancy (live threads) can’t be limited by register file capacity.
* Xe-LPG’s vector width ranges from 1-wide to 32-wide and is specified per-instruction. [1.4]

## Specs

* Xe Core (EU): [1.4]
	- 128 fp32 FLOPS/cy
	- 16x 256 bit Vector engines


# Arc Alchemist (Gen 12.7)

CPU code name: Meteor Lake, Lunar Lake.<br/>
Architecture: Xe-HPG (high performance graphics)

## Examples

### Meteor Lake

**Desktop**
* Arc 3: A310, A380
* Arc 5: A580
* Arc 7: A750

**Mobile**
* Arc 3: A350M, A370M
* Arc 5: A530M, A550M, A570M
* Arc 7: A730M, A770M

### Lunar Lake

**Mobile**
* Arc 140V


## References

2.1. [Raytracing on Meteor Lake’s iGPU](https://chipsandcheese.com/2024/04/15/raytracing-on-meteor-lakes-igpu/)<br/>
2.2. [Intel’s Ambitious Meteor Lake iGPU](https://chipsandcheese.com/2024/04/08/intels-ambitious-meteor-lake-igpu/)<br/>
2.3. [Vulkan features for Arc A380](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Arc(TM)%20A380%20Graphics)<br/>

## Notes

* Parallel FP32 FMA and I32 IADD datapath. [3.3]
* Each Xe Core has eight TMUs, or texture samplers in Intel terminology. The samplers have a 32 KB texture cache, and can return 128 bytes/cycle to the XVEs. [3.3]

## Features

* Hardware ray tracing.
* Neural supersampling.
* Mesh shading.

## Specs

* integer performance: [3.3]
	- x i32 add
	- 1/2x i32 mul
	- 1/3x i64 add
	- 2x i16 add, mul
	- 1/3x i8 add, mul


# Arc Battlemage (B-Series)

Architecture: Xe2-HPG (high performance graphics)

## Examples

* Arc 5 B570, B580

## References

3.1. [Vulkan features for Arc B580](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel%28R%29+Arc%28TM%29+B580+Graphics)<br/>
3.2. [Intel Arc B570 Graphics Performance On Linux](https://www.phoronix.com/review/intel-arc-b570-linux)<br/>
3.3. [Intel’s Battlemage Architecture](https://chipsandcheese.com/p/intels-battlemage-architecture)<br/>

## Notes

* Parallel FP32 FMA and I32 IADD datapath. [3.3]
* Each Xe Core has eight TMUs, or texture samplers in Intel terminology. The samplers have a 32 KB texture cache, and can return 128 bytes/cycle to the XVEs. [3.3]
* L1 latency for a SIMD1 (scalar) access is about 15 cycles faster than a SIMD16 access. [3.3]
* SIMD32 accesses take one extra cycle when microbenchmarking, though that’s because the compiler generates two sets of SIMD16 instructions to calculate addresses across 32 lanes. [3.3]

## Specs

* 3-way co-issue. [3.3]

* integer performance: [3.3]
	- x i32 add
	- 1/2x i32 mul
	- 1/2x i64 add
	- 2x i16 add, mul
	- 2x i8 add, mul

* Xe Core (EU): [3.3]
	- 8x 512 bit Vector Engines
	- 8x 2048 bit XMX Engines
	- 256KB shared L1 / SharedMemory(SLM)
	- 128 fp32 FLOPS/cy

* L1 bandwidth: 512B/cy (specs), ~256B/cy (bench) [3.3]

