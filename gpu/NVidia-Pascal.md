
## Examples

* GTX 10xx
* GTX 10xx Max-Q
* Titan X
* Titan Xp
* Quadro Pxxx
* MX150
* MX230, MX250
* MX330, MX350
* Tegra X2


## References

1. [Architecture Whitepaper (Tesla P100)](https://images.nvidia.com/content/pdf/tesla/whitepaper/pascal-architecture-whitepaper.pdf)
2. [GTX 1080 Whitepaper](https://www.es.ele.tue.nl/~heco/courses/ECA/GPU-papers/GeForce_GTX_1080_Whitepaper_FINAL.pdf), [[backup](../pdf/GeForce_GTX_1080_Whitepaper_FINAL.pdf)]
3. [Tuning CUDA Applications for Pascal](https://docs.nvidia.com/cuda/pascal-tuning-guide/index.html)
4. [Compute Capability 6.x](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#compute-capability-6-x)
5. [Tile-based Rasterization in Nvidia GPUs](https://www.realworldtech.com/tile-based-rasterization-nvidia-gpus/)

## Notes

* Adds support for native FP16 instructions. [3]
* Peak FP16 throughput is attained by using a paired operation to perform two FP16 instructions per core simultaneously. [3]
* Unified Memory: An extended 49-bit virtual addressing space allows Pascal GPUs to address the full 48-bit virtual address space of modern CPUs as well as the memories of all GPUs in the system through a single virtual address space, not limited by the physical memory sizes of any one processor. [3]
* Includes a significantly enhanced delta color compression capability: [2]
	- 2:1 compression has been enhanced to be effective more often
	- A new 4:1 delta color compression mode has been added to cover cases where the per pixel deltas are very small and are possible to pack into ¼ of the original storage
	- A new 8:1 delta color compression mode combines 4:1 constant color compression of 2x2 pixel blocks with 2:1 compression of the deltas between those blocks
* Supports Pixel-Level Graphics Preemption, also has enhanced preemption support for compute workloads. [2]<br/>
	When a preemption request is received, the rasterizer, triangle shading and command pushbuffer processor will all stop and save off their current position. Pixels that have already been rasterized will finish pixel shading and then the GPU is ready to take on the new high priority workload.
* Simultaneous Multi-Projection Engine - responsible for generating multiple projections of a single geometry stream. [2]

* Executing integer instructions blocked floating-point instructions from issuing. [?]

* [ref](https://arxiv.org/pdf/1903.07486):
	- instructions IMAD and IMUL have a long latency because they are emulated.
	- most integer and single-precision instructions have a latency of 6 cycles; double-precision instructions have a latency of 8 cycles; more complex instructions, some of which run on the SFU, require 14 cycles.


## Features

* Tile based rasterization (TBR). [5]
* Async compute queue. [2]
* Software ray tracing.

## Specs

* ops/clock per SM: [4]
	- 128 fp16 FMA
	- 64 fp32 FMA
	- 32 fp64 FMA
	- 16 fp32 rcp, rsqrt, log2, exp2, sin, cos
	- 64 i32 add/sub
	- 32 i32 shift
	- 32 cmp, min, max
	- 32 i32 bit reverse
	- 32 i32 bit extract, insert
	- 64 i32 and, or, xor
	- 16 MSB
	- 16 pop count
	- 16 i8/i16 to i32
	- 16 to/from i64/fp64
	- 16 type conversions
