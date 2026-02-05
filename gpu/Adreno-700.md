
## Examples

* 730, 740
* 741, X (X Elite)

**SoC/Device**
* Meta Quest 3, Pico 4 Ultra (Adreno 740)
* Snapdragon XR2 Gen 2 (Adreno 740)
* Snapdragon 8 Gen 3 (Adreno 750)

## References

1. [The Snapdragon X Elite’s Adreno iGPU](https://chipsandcheese.com/2024/07/04/the-snapdragon-x-elites-adreno-igpu/)
2. [Sizing up Qualcomm’s 8cx Gen 3 iGPU](https://chipsandcheese.com/2024/04/24/sizing-up-qualcomms-8cx-gen-3-igpu/)
3. [Inside Snapdragon 8+ Gen 1’s iGPU: Adreno Gets Big](https://chipsandcheese.com/2024/03/05/inside-snapdragon-8-gen-1s-igpu-adreno-gets-big/)
4. [Freedreno wiki: A7xx ray tracing](https://gitlab.freedesktop.org/freedreno/freedreno/-/wikis/a7xx-ray-tracing)
5. [Freedreno wiki: AQE](https://gitlab.freedesktop.org/freedreno/freedreno/-/wikis/AQE)
6. [Vulkan features for Adreno 740](https://vulkan.gpuinfo.org/listreports.php?devicename=Adreno%20(TM)%20740), [X1-85](https://vulkan.gpuinfo.org/listreports.php?devicename=Qualcomm(R)%20Adreno(TM)%20X1-85%20GPU)
7. [Correction on Qualcomm iGPUs](https://chipsandcheese.com/2024/05/06/correction-on-qualcomm-igpus/)


## Features

* Hardware ray tracing. [6]
* Sparse memory. [6]
* fragment interlock. [6]
* mesh shader. [6]
* image atomic int64. [6]
* cooperative matrix. [6]
* fragment shader barycentric. [6]

## Notes

* Adreno 7xx tries to speed up this work *(sequential binning and per tile rasterization)* by introducing concurrency in the command processor. Adreno 6xx’s SQE gets split into two microcontrollers, called BV and BR. BV handles the binning pass, and BR renders the tiles. [8]

* L1 cache:
	- 2 KB texture cache (L1) private to each uSPTP. [1]
	- 916 GB/s bandwidth from tests. [1]

* Cluster cache (between L1 and L2)
	- 128KB for each cluster of 2x SP or 4x uSPTP.


## Specs

* XR2 Gen2:
	- GPU Heavy: 600MHz GPU, 1.6GHz CPU
	- CPU heavy: 490MHz GPU, 2.0GHz CPU
	- Adreno 740:
		* 256 SIMD, 1536 threads
		* 3.1 TFLOPS
		* GMem: 3 MB
	- 4x Cortex A78C 2.36GHz, 2x Cortex A78C 2.05GHz
	- LPDDR5X quad-channel, 64bit, 76.8 GB/s

* X1:
	- X1-45 TFLOPS: 1.7 - 2.1
	- X1-45 MegaTris/s: 1.1
	- X1-85 TFLOPS: 3.8 - 4.6
	- X1-85 MegaTris/s: 2.5
	- RAM: LPDDR5X-8448, 128-bit, 135 GB/s
