
## Examples

* GTX 9xx
* Titan X
* Quadro Mxxxx
* Tegra X1
* Nintendo Switch
* Shield TV
* MX110, MX130

## References

1. [CUDA Tuning Guide](https://developer.download.nvidia.com/assets/cuda/secure/CUDA60/RC/docs/Maxwell_Tuning_Guide.pdf)
2. [Architecture Whitepaper](https://www.techpowerup.com/gpu-specs/docs/nvidia-gtx-980.pdf), [[backup](../pdf/nvidia-gtx-980.pdf)]
3. [Dissecting GPU Memory Hierarchy through Microbenchmarking](https://arxiv.org/pdf/1509.02308)
4. [Examining the Nintendo Switch (Tegra X1) Video Engine](https://chipsandcheese.com/2024/06/28/examining-the-nintendo-switch-tegra-x1-video-engine/)
5. [Maxwell: Nvidia’s Silver 28nm Hammer](https://chipsandcheese.com/2024/01/08/maxwell-nvidias-silver-28nm-hammer/)
6. [Nintendo Switch’s iGPU: Maxwell Nerfed Edition](https://chipsandcheese.com/2023/12/23/nintendo-switchs-igpu-maxwell-nerfed-edition/)
7. [Compute Capability 5.x](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#compute-capability-5-x)
8. [Tegra X1 Whitepaper](https://international.download.nvidia.com/pdf/tegra/Tegra-X1-whitepaper-v1.0.pdf)

## Notes

* FP16 data storage.
* Unified L1/Texture cache.
* Native shared memory atomic operations for 32-bit integer arithmetic, along with native 32 or 64-bit compare-and-swap (CAS).
* Async transfer queue.

* instructions IMAD and IMUL have a long latency because they are emulated. [ref](https://arxiv.org/pdf/1903.07486)


## Specs

* ops/clock per SM: [7]
	- 128 fp32 FMA
	- 4 fp64 FMA
	- 32 fp32 rcp, rsqrt, log2, exp2, sin, cos
	- 32 i32 add/sub
	- 64 i32 shift
	- 64 cmp, min, max
	- 64 i32 bit reverse
	- 64 i32 bit extract, insert
	- 128 i32 and, or, xor
	- 32 MSB
	- 32 pop count
	- 32 i8/i16 to i32
	- 4 to/from i64/fp64
	- 32 type conversions

