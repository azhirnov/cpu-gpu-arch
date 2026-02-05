
# Arc Battlemage (B-Series)

Generation: 13<br/>
Architecture: Xe2-HPG (high performance graphics)<br/>

## Examples

* Arc 5 B570, B580

## References

1.1. [Vulkan features for Arc B580](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel%28R%29+Arc%28TM%29+B580+Graphics)<br/>
1.2. [Intel Arc B570 Graphics Performance On Linux](https://www.phoronix.com/review/intel-arc-b570-linux)<br/>
1.3. [Intel’s Battlemage Architecture](https://chipsandcheese.com/p/intels-battlemage-architecture)<br/>
1.4. [Vulkan features for Arc B580](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel%28R%29+Arc%28TM%29+B580+Graphics), [B580 (Mesa)](https://vulkan.gpuinfo.org/listreports.php?property=devicename&value=Intel(R)%20Arc(tm)%20B580%20Graphics%20(BMG%20G21)&platform=linux)<br/>
1.5. [Xe2 and Lunar Lake GPU Deep Dive](https://cdrdv2-public.intel.com/824434/2024_Intel_Tech%2520Tour%2520TW_Xe2%2520and%2520Lunar%2520Lakes%2520GPU.pdf)<br/>

## Notes

* Parallel FP32 FMA and I32 IADD datapath. [1.3]
* Each Xe Core has eight TMUs, or texture samplers in Intel terminology. The samplers have a 32 KB texture cache, and can return 128 bytes/cycle to the XVEs. [1.3]
* L1 latency for a SIMD1 (scalar) access is about 15 cycles faster than a SIMD16 access. [1.3]
* SIMD32 accesses take one extra cycle when microbenchmarking, though that’s because the compiler generates two sets of SIMD16 instructions to calculate addresses across 32 lanes. [1.3]

* SIMD16 native ALU, support SIMD16 and SIMD32 ops. [1.5]
* Tensor core (Xe Matrix Engine) supports: FP16, BF16, int8, int4, int2. [1.5]
* 64bit atomic ops. [1.5]
* 2x throughput for sampling without filtering. [1.5]
* Out of order sampling with compressed textures. [1.5]
* Early HiZ culling of small primitives. [1.5]
* Render target prefetch to L2. [1.5]
* New 8:N compression. [1.5]

* In Xe2, Intel added the “Large GRF” mode which allows a thread to pick between 128 registers or 256 registers. [3.1]

## Specs

* 3-way co-issue. [1.3]

* integer performance: [1.3]
	- 1x i32 add
	- 1/2x i32 mul
	- 1/2x i64 add
	- 2x i16 add, mul
	- 2x i8 add, mul

* Xe Core (EU): [1.3]
	- 8x 512 bit Vector Engines (XVE)
	- 8x 2048 bit XMX Matrix Engines
	- 256KB shared L1 / SharedMemory(SLM)
	- 128 fp32 FLOPS/cy
	- XVE can track up to 8 threads
	- 64KB register file per XVE

* L1 bandwidth: 512B/cy (specs), ~256B/cy (bench) [1.3]

* ALU performance per Xe Core (8 XVE): [1.5]
	- FP32: 256 ops/clk
	- FP16: 512 ops/clk

* Tensor performance per Xe Core (8 XMX): [1.5]
	- FP16/BF16: 2048 ops/clk
	- int8: 4096 ops/clk
	- int4/int2: 8192 ops/clk

* Arc B580:
	- 20 Xe Cores (EU)
	- clock: 2670 MHz
	- fp16 Tensor TFLOPS: 109
	- i8 Tensor TOPS: 219
	- i4 Tensor TOPS: 437

# Intel Xe2-LPG

Generation: 13<br/>
CPU code name: Lunar Lake<br/>
Architecture: Xe2-LPG (low power graphics)

## Examples

* iGPU in Core Ultra 200V
* Arc 140V

## References

2.1. [Intel Unveils Lunar Lake Architecture: New P and E cores, Xe2-LPG Graphics, New NPU 4 Brings More AI Performance](https://www.anandtech.com/show/21425/intel-lunar-lake-architecture-deep-dive-lion-cove-xe2-and-npu4/6)<br/>
2.2. [Lunar Lake’s iGPU: Debut of Intel’s Xe2 Architecture](https://chipsandcheese.com/p/lunar-lakes-igpu-debut-of-intels)<br/>
2.3. [Vulkan features for Arc 130V](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Arc(TM)%20130V%20GPU%20(16GB)), [140V](https://vulkan.gpuinfo.org/listreports.php?devicename=Intel(R)%20Arc(TM)%20140V%20GPU%20(16GB))<br/>

## Notes

* iGPU supports up to 16GB memory.

## Specs

* 192KB shared L1 / SharedMemory(SLM). [3.1]

* Arc 140V:
	- 16 Xe Cores (EU)
	- clock: 1950 MHz
	- fp32 TFLOPS: 4
	- fp16 TFLOPS: 8
	- fp16 Tensor TFLOPS: 64
	- i8 Tensor TOPS: 128
	- i4 Tensor TOPS: 256


# Intel Xe3

CPU code name: Panther Lake<br/>

## References

3.1. [Panther Lake’s Reveal at ITT 2025](https://chipsandcheese.com/p/panther-lakes-reveal-at-itt-2025)<br/>

## Specs

* Xe Core (EU): [3.1]
	- 8x 512 bit Vector Engines (XVE)
	- 8x 2048 bit XMX Matrix Engines
	- 256KB shared L1 / SharedMemory(SLM)
	- 128 fp32 FLOPS/cy
	- XVE can track up to 10 threads
	- 64KB register file per XVE


## Notes

* one of the big changes in Xe3 is making the render slice capable of handling up to 6 Xe Cores from the 4 Xe Cores that the Xe2 render slice could support. [3.1]
* the amount of compute throughput that Xe3 has not changed compared to Xe2 with the same 8 512 bit Vector Engines and 8 2048 bit Matrix Engines per Xe Core but the L1/SLM capacity has increased from 192KB to 256KB. [3.1]
* Xe3 now allows a thread to allocate up to 256 registers in 32 register increments. [3.1]
* ray tracing units now capable of dynamic ray management. [3.1]

