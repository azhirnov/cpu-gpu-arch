
## Examples

* M3
* A17 Pro

## References

1. [Explore GPU advancements in M3 and A17 Pro](https://developer.apple.com/videos/play/tech-talks/111375)

## Notes

* [1]
	- Dynamic shader core memory which allows an app to achieve better thread occupancy (2 virtual threads in one).
	- Flexible on-chip memory - 3 cache types now is dynamically allocated, if one type is not used - it will not be allocated.
	- fp32, fp16, int can execute in parallel.
	- Optimized for fp16.
	- Shader execution reordering.
	- In mesh shading: intermediate data from task shader now stored in the on-chip memory and accessed by mesh shader.


## Features

* Hardware ray tracing.

