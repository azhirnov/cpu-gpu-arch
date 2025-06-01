
## Examples

* M3, M3 Pro, M3 Max
* A17 Pro
* M4

## References

1. [Explore GPU advancements in M3 and A17 Pro](https://developer.apple.com/videos/play/tech-talks/111375)
2. [Apple Announces M3 SoC Family: M3, M3 Pro, and M3 Max Make Their Marks](https://www.anandtech.com/show/21116/apple-announces-m3-soc-family-m3-m3-pro-and-m3-max-make-their-marks)


## Features

* Hardware ray tracing.
* Hardware mesh shading.
* Dynamic caching.


## Notes

* [1]
	- Dynamic shader core memory which allows an app to achieve better thread occupancy (2 virtual threads in one).
	- Flexible on-chip memory - 3 cache types now is dynamically allocated, if one type is not used - it will not be allocated.
	- fp32, fp16, int can execute in parallel (separate pipes).
	- Optimized for fp16.
	- Shader execution reordering.
	- In mesh shading: intermediate data from task shader now stored in the on-chip memory and accessed by mesh shader.
	- for situations where the source or destination variable of a math operation is not FP16 already, it can be converted to and from at no cost.


## Specs

* M3 10-core GPU:
	- max clock: 1600 MHz
	- 16 EU per core
	- 8x fp32 : 8x fp16 : 8x i32 ALUs per EU
	- 1280 total ALUs (FMA/cy)
	- theoretical fp32/fp16 performance: 1600 MHz * 1280 ALUs = 2048*10^9^ FMA/s = 4.096 TFLOPS
	- theoretical fp32+fp16 performance: 8.2 TFLOPS
	- Memory: LPDDR5-6400, 102.4 GB/s, 8 controllers

* M3 Pro 18-core GPU:
	- 2304 total ALUs (FMA/cy)
	- Memory: LPDDR5-6400, 153.6 GB/s

* M3 Max 40-core GPU:
	- 5120 total ALUs (FMA/cy)
	- Memory: LPDDR5-6400, 409.6 GB/s

* M3 Ultra 80-core GPU:
	- 10240 total ALUs (FMA/cy)
	- Memory: LPDDR5-6400, 819.3 GB/s

* M4 10-core GPU:
	- max clock: 1800 MHz
	- theoretical fp32/fp16 performance: 1800 MHz * 1280 ALUs = 2304*10^9^ FMA/s = 4.6 TFLOPS
	- theoretical fp32+fp16 performance: 9.2 TFLOPS
	- Memory: LPDDR5X 7500 MT/s, 120GB/s

* M4 Pro 20-core GPU:
	- Memory: LPDDR5X 8533 MT/s, 273GB/s

* M4 Max 40-core GPU:
	- Memory: LPDDR5X 8533 MT/s, 546GB/s

