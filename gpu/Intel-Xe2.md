
# Arc Battlemage (B-Series)

Architecture: Xe2-HPG (high performance graphics)<br/>

## Examples

* Arc 5 B570, B580

## References

1.1. [Vulkan features for Arc B580](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel%28R%29+Arc%28TM%29+B580+Graphics)<br/>
1.2. [Intel Arc B570 Graphics Performance On Linux](https://www.phoronix.com/review/intel-arc-b570-linux)<br/>
1.3. [Intel’s Battlemage Architecture](https://chipsandcheese.com/p/intels-battlemage-architecture)<br/>
1.4. [Vulkan features for Arc B580](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel%28R%29+Arc%28TM%29+B580+Graphics)<br/>

## Notes

* Parallel FP32 FMA and I32 IADD datapath. [1.3]
* Each Xe Core has eight TMUs, or texture samplers in Intel terminology. The samplers have a 32 KB texture cache, and can return 128 bytes/cycle to the XVEs. [1.3]
* L1 latency for a SIMD1 (scalar) access is about 15 cycles faster than a SIMD16 access. [1.3]
* SIMD32 accesses take one extra cycle when microbenchmarking, though that’s because the compiler generates two sets of SIMD16 instructions to calculate addresses across 32 lanes. [1.3]

## Specs

* 3-way co-issue. [1.3]

* integer performance: [1.3]
	- x i32 add
	- 1/2x i32 mul
	- 1/2x i64 add
	- 2x i16 add, mul
	- 2x i8 add, mul

* Xe Core (EU): [1.3]
	- 8x 512 bit Vector Engines
	- 8x 2048 bit XMX Engines
	- 256KB shared L1 / SharedMemory(SLM)
	- 128 fp32 FLOPS/cy

* L1 bandwidth: 512B/cy (specs), ~256B/cy (bench) [1.3]

