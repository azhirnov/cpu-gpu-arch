
# Arc Alchemist

Generation: 12.7<br/>
CPU code name: Meteor Lake, Lunar Lake.<br/>
Architecture: Xe-HPG (high performance graphics)<br/>

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

1.1. [Raytracing on Meteor Lake’s iGPU](https://chipsandcheese.com/2024/04/15/raytracing-on-meteor-lakes-igpu/)<br/>
1.2. [Intel’s Ambitious Meteor Lake iGPU](https://chipsandcheese.com/2024/04/08/intels-ambitious-meteor-lake-igpu/)<br/>
1.3. [Vulkan features for Arc A380](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Arc(TM)%20A380%20Graphics)<br/>
1.4. [Intel’s Battlemage Architecture](https://chipsandcheese.com/p/intels-battlemage-architecture) - compared with Arc<br/>

## Features

* Hardware ray tracing.
* Neural supersampling.
* Mesh shading.
* Async compute queue.
* Async transfer queue.

## Notes

* Parallel FP32 FMA and I32 IADD datapath. [1.4]
* Each Xe Core has eight TMUs, or texture samplers in Intel terminology. The samplers have a 32 KB texture cache, and can return 128 bytes/cycle to the XVEs. [1.4]

## Specs

* integer performance: [1.4]
	- 1x i32 add
	- 1/2x i32 mul
	- 1/3x i64 add
	- 2x i16 add, mul
	- 1/3x i8 add, mul

	
# Intel Xe-LPG

CPU code name: Tiger Lake, Rocket Lake, Alder Lake, Raptor Lake.<br/>
Architecture: Xe-LPG (low power graphics)

## Examples

* Intel UHD Graphics 730, 770
* Iris Xe Graphics G7

## References

2.1. [Intel Processor Graphics Architecture](https://cdrdv2-public.intel.com/686065/the-architecture-of-intel-processor-graphics-gen11-r1new.pdf), [[backup](../pdf/Intel-the-architecture-of-intel-processor-graphics-gen11-r1new.pdf)]<br/>
2.2. [Intel Processor Graphics Xᵉ-LP API Developer and Optimization Guide](https://www.intel.com/content/www/us/en/developer/articles/guide/lp-api-developer-optimization-guide.html), [[webarchive](https://web.archive.org/web/20230623012301/https://www.intel.com/content/www/us/en/developer/articles/guide/lp-api-developer-optimization-guide.html)]<br/>
2.3. [Vulkan features for Iris Xe](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Iris(R)%20Xe%20Graphics), [UHD Graphics 770](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20UHD%20Graphics%20770)<br/>
2.4. [Intel’s Ambitious Meteor Lake iGPU](https://chipsandcheese.com/p/intels-ambitious-meteor-lake-igpu)<br/>

## Notes

* A XVE can have up to eight threads in flight. [2.4]
* Statically allocates register file capacity for in-flight threads. [2.4]
	- Every thread gets 128 registers, regardless of whether it needs them all. Occupancy (live threads) can’t be limited by register file capacity.
* Xe-LPG’s vector width ranges from 1-wide to 32-wide and is specified per-instruction. [2.4]

## Specs

* Xe Core (EU): [2.4]
	- 128 fp32 FLOPS/cy
	- 16x 256 bit Vector engines
