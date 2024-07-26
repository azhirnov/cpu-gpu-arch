
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
2. [Architecture Whitepaper](https://www.techpowerup.com/gpu-specs/docs/nvidia-gtx-980.pdf), [pdf](../pdf/nvidia-gtx-980.pdf)
3. [Dissecting GPU Memory Hierarchy through Microbenchmarking](https://arxiv.org/pdf/1509.02308)
4. [Examining the Nintendo Switch (Tegra X1) Video Engine](https://chipsandcheese.com/2024/06/28/examining-the-nintendo-switch-tegra-x1-video-engine/)
5. [Maxwell: Nvidia’s Silver 28nm Hammer](https://chipsandcheese.com/2024/01/08/maxwell-nvidias-silver-28nm-hammer/)
6. [Nintendo Switch’s iGPU: Maxwell Nerfed Edition](https://chipsandcheese.com/2023/12/23/nintendo-switchs-igpu-maxwell-nerfed-edition/)

## Notes

* FP16 data storage.
* Unified L1/Texture cache.
* Native shared memory atomic operations for 32-bit integer arithmetic, along with native 32 or 64-bit compare-and-swap (CAS).
* Async transfer queue.
