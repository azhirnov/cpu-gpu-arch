
# Arc Alchemist

Generation: 12.7<br/>
Architecture: Xe-HPG (high performance graphics)<br/>

## Examples

**Desktop**
* Arc 3: A310, A380
* Arc 5: A580
* Arc 7: A750

**Mobile**
* Arc 3: A350M, A370M
* Arc 5: A530M, A550M, A570M
* Arc 7: A730M, A770M


## References

1.1. [Raytracing on Meteor Lake’s iGPU](https://chipsandcheese.com/2024/04/15/raytracing-on-meteor-lakes-igpu/)<br/>
1.2. [Intel’s Ambitious Meteor Lake iGPU](https://chipsandcheese.com/2024/04/08/intels-ambitious-meteor-lake-igpu/)<br/>
1.3. [Vulkan features for Arc A380](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Arc(TM)%20A380%20Graphics), [A310 LP](https://vulkan.gpuinfo.org/listreports.php?property=devicename&value=Intel(R)%20Arc(TM)%20A310%20LP%20Graphics], [A380 (Mesa driver)](https://vulkan.gpuinfo.org/listreports.php?property=devicename&value=Intel(R)%20Arc(tm)%20A380%20Graphics%20(DG2)&platform=linux)<br/>
1.4. [Intel’s Battlemage Architecture](https://chipsandcheese.com/p/intels-battlemage-architecture) - compared with Arc<br/>
1.5. [Xe-HPG Architecture White Paper](https://cdrdv2-public.intel.com/758302/introduction-to-the-xe-hpg-architecture-white-paper.pdf)<br/>

## Features

* Hardware ray tracing.
* Neural supersampling.
* Mesh shading.
* Async compute queue.
* Async transfer queue.
* Sampler feedback.
* Cooperative matrix.
* Removed ASTC format.

## Notes

* Parallel FP32 FMA and I32 IADD datapath. [1.4]
* Each Xe Core has eight TMUs, or texture samplers in Intel terminology. The samplers have a 32 KB texture cache, and can return 128 bytes/cycle to the XVEs. [1.4]

* In Xe1 and prior Intel GPUs, a thread would be allocated 128 registers regardless of if that thread needed all 128 registers or not. [[ref](https://chipsandcheese.com/p/panther-lakes-reveal-at-itt-2025)]

## Specs

* integer performance: [1.4]
	- 1x i32 add
	- 1/2x i32 mul
	- 1/3x i64 add
	- 2x i16 add, mul
	- 1/3x i8 add, mul


# Intel Xe-LP

CPU code name: Tiger Lake, Rocket Lake, Alder Lake, Raptor Lake, Twin Lake.<br/>
Architecture: Xe-LP (low power)

## Examples

* Intel UHD Graphics 730, 770
* Iris Xe Graphics G7

## References

2.2. [Intel Processor Graphics Xᵉ-LP API Developer and Optimization Guide](https://www.intel.com/content/www/us/en/developer/articles/guide/lp-api-developer-optimization-guide.html), [[webarchive](https://web.archive.org/web/20230623012301/https://www.intel.com/content/www/us/en/developer/articles/guide/lp-api-developer-optimization-guide.html)]<br/>
2.3. [Vulkan features for Iris Xe](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Iris(R)%20Xe%20Graphics), [UHD Graphics 770](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20UHD%20Graphics%20770), [RaptorLake-S](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20RaptorLake-S%20Mobile%20Graphics%20Controller), [N150 (UHD Graphics 730)](https://vulkan.gpuinfo.org/displayreport.php?id=39319)<br/>
2.4. [Intel’s Ambitious Meteor Lake iGPU](https://chipsandcheese.com/p/intels-ambitious-meteor-lake-igpu)<br/>
2.5. [Intel Meteor Lake Technical Deep Dive](https://www.techpowerup.com/review/intel-meteor-lake-technical-deep-dive/)<br/>

## Features

* Fragment shading rate.
* Vulkan video decode.
* Fragment shader interlock.
* Sampler feedback.
* ASTC format still supported.

## Notes

* iGPU without ray tracing and mesh shading. [1.5]

* Independent scheduling queues.
* A XVE can have up to eight threads in flight. [2.4]
* Statically allocates register file capacity for in-flight threads. [2.4]
	- Every thread gets 128 registers, regardless of whether it needs them all. Occupancy (live threads) can’t be limited by register file capacity.
* Xe-LPG’s vector width ranges from 1-wide to 32-wide and is specified per-instruction. [2.4]

## Specs

* Xe Core (EU): [2.4]
	- 128 fp32 FLOPS/cy
	- 16x 256 bit Vector engines


# Intel Xe-LPG

CPU code name: Arrow Lake, Meteor Lake.<br/>
Architecture: Xe-LPG / Xe-LPG+ (low power graphics)

## Examples

* iGPU in Core Ultra 100 (Meteor Lake)
* iGPU in Core Ultra 200 (Arrow Lake) except 200V (Lunar Lake)
* Arc 130T, 140T

## References

3.1. [Vulkan features for Arc 140T 32GB](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Arc(TM)%20140T%20GPU%20(32GB)), [16GB](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Arc(TM)%20140T%20GPU%20(16GB))<br/>
3.2. [Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench-gpu/Intel_Arc140T.md)

## Features

* Arrow Lake-H with Xe-LPG+: XeSS super resolution, frame generation, low latency
* Arrow Lake-S, Meteor Lake with Xe-LPG: XeSS super resolution, low latency

## Specs

* Xe core (EU):
	- 8 XMX engines

* XMX Engine (Tensor core) FP16: 128 ops/cy ? [3.2]

* Cache (Arc 140T): [3.2]
	- L1 cache: 128KB per cluster, 520 GB/s
	- L2 cache: 8MB shared, 160 GB/s

## Notes

* iGPU supports up to 32GB memory.
* Same features as in Xe-HPG
* XMX engine (only Xe-LPG+ / Arrow Lake-H ?)

* LPG+ gets support for DPAS (dot product accumulate systolic). DPAS enables FP16, BF16, and INT4 multiplication with 16 or 32 bits accumulate. [[ref](https://www.techpowerup.com/319499/intels-desktop-and-mobile-arrow-lake-chips-feature-different-versions-of-xe-lpg)]

* cooperative matrix:
	- `8x16 * 16x8 + 8x8` size for fp16, differs from NV/AMD with `16x16 * 16x16`
	- `8x32 * 32x8 + 8x8` size for i8, differs from NV with `16x32 * 32x16 + 16x16` and AMD with `16x16 * 16x16`

* In fragment shader: on high register count used simd8 mode, otherwise used simd16 mode. [3.2]
* In vertex shader: always used simd8 mode. [3.2]
* In compute pipeline supported subgroup size: 8, 16, 32. [3.1]
