
## Examples

* A14
* M1


## References

1. [Discover Metal enhancements for A14 Bionic](https://developer.apple.com/videos/play/tech-talks/10858/)
2. [Mesa driver details](https://docs.mesa3d.org/drivers/asahi.html)
3. Dissecting the Apple M1 GPU: [1](https://rosenzweig.io/blog/asahi-gpu-part-1.html), [2](https://rosenzweig.io/blog/asahi-gpu-part-2.html), [3](https://rosenzweig.io/blog/asahi-gpu-part-3.html)
4. [M1 Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench-gpu/Apple_M1.md)
5. [M1 reverse engineering](https://github.com/AsahiLinux/docs/wiki/HW%3AAGX)
6. [iGPU Cache Setups Compared, Including M1](https://chipsandcheese.com/p/igpu-cache-setups-compared-including-m1)
7. [Reverse engineering the Apple G13 GPU architecture](https://dougallj.github.io/applegpu/docs.html)


## Notes

* FP16:
	- fp32 has same rate as fp16. [4]
	- that there is a penalty (of exactly one cycle) for switching between FP32 and FP16 operation. [ref](https://www.realworldtech.com/forum/?threadid=197759&curpostid=197855)
	- FP32 ALU rate is half of FP16 rate on A14 (and earlier chips). That has not changed on A14. F32 ALU rate relative to F16 increased on M1.


## Features

* Ray tracing (software).

## Specs

* Local memory (L1): [6]
	- size: 32KB
	- latency: 43ns
	- bandwidth: 671 GB/s

* L2 Cache: [6]
	- size: 1MB
	- latency: 76.3ns
	- bandwidth: 384 GB/s

* System level cache (L3): [6]
	- size: 8MB
	- latency: 266ns
	- bandwidth: 134 GB/s

* RAM: [6]
	- latency: 311ns
	- bandwidth: 50.4 GB/s

* CPU to GPU bandwidth: 17 GB/s [6]
* GPU to CPU bandwidth: 17.5 GB/s [6]

* M1 8-core GPU:
	- max clock: 1278 MHz
	- 16 EU per core
	- 8 fp32/fp16 ALU per EU
	- 2 SFU per EU [4]
	- 1024 total ALUs (FMA/cy)
	- theoretical fp32/fp16 performance: 1278 MHz * 1024 ALUs = 1308*10^9^ FMA/s = 2.6 TFLOPS
