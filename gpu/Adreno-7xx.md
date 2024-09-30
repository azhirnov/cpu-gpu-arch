
## Examples

* 741, X (X Elite)

* Meta Quest 3 (Adreno 740)

## References

1. [The Snapdragon X Elite’s Adreno iGPU](https://chipsandcheese.com/2024/07/04/the-snapdragon-x-elites-adreno-igpu/)
2. [Sizing up Qualcomm’s 8cx Gen 3 iGPU](https://chipsandcheese.com/2024/04/24/sizing-up-qualcomms-8cx-gen-3-igpu/)
3. [Inside Snapdragon 8+ Gen 1’s iGPU: Adreno Gets Big](https://chipsandcheese.com/2024/03/05/inside-snapdragon-8-gen-1s-igpu-adreno-gets-big/)
4. [Freedreno wiki: A7xx ray tracing](https://gitlab.freedesktop.org/freedreno/freedreno/-/wikis/a7xx-ray-tracing)
5. [Freedreno wiki: AQE](https://gitlab.freedesktop.org/freedreno/freedreno/-/wikis/AQE)
6. [Vulkan features for Adreno 740](https://vulkan.gpuinfo.org/listreports.php?devicename=Adreno%20(TM)%20740)
7. [The Snapdragon X Elite’s Adreno iGPU](https://chipsandcheese.com/2024/07/04/the-snapdragon-x-elites-adreno-igpu/)
8. [Correction on Qualcomm iGPUs](https://chipsandcheese.com/2024/05/06/correction-on-qualcomm-igpus/)


## Notes

* Adreno 7xx tries to speed up this work *(sequential binning and per tile rasterization)* by introducing concurrency in the command processor. Adreno 6xx’s SQE gets split into two microcontrollers, called BV and BR. BV handles the binning pass, and BR renders the tiles. [8]
