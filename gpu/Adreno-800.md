
## Examples

* Adreno 810, 830, 840
* Adreno X2

**SoC/Device**
* Snapdragon 8 Elite / Gen 4 (Adreno 830)
* Snapdragon 8 Elite 2 / Gen 5 (Adreno 840)


## References

1. [Vulkan features for Adreno 830](https://vulkan.gpuinfo.org/listreports.php?devicename=Adreno%20(TM)%20830), [Adreno 840](https://vulkan.gpuinfo.org/listreports.php?devicename=Adreno%20(TM)%20840)
2. [Diving into Qualcomm's Upcoming Adreno X2 GPU with Eric Demers](https://chipsandcheese.com/p/diving-into-qualcomms-upcoming-adreno)
3. [Qualcomm’s Snapdragon X2 Elite](https://chipsandcheese.com/p/qualcomms-snapdragon-x2-elite)
4. [Vulkan features for X2-90](https://vulkan.gpuinfo.org/listreports.php?devicename=Qualcomm(R)%20Adreno(TM)%20X2-90%20GPU)


## Features

* Immediate mode rendering instead of TBDR
* Universal Bandwidth Compression v6
* VK_ARM_tensors, VK_ARM_data_graph

## Notes

* lossy compression. [1]

* HPM - high performance memory, replaces GMem. [2, 3]
	- HPM 4TB/s bandwidth
	- 5.25 MB per slice
	- So particularly for the X2 Extreme Edition we can do a QHD+ resolution or 1600p resolution, 2K resolutions, all natively on die and all that rendering, so the color ROPs, all the Z-buffer, all of that is done at full speed on die and doesn’t use any DRAM bandwidth. [2]
	- You have random access to the whole surface from any of the slices. We have a full crossbar at full bandwidth that allows the HPM to be used by any of the slices, even though it is physically implemented inside the slice. [2]

* There’s two micro-SPs per SP and then there’s two SPs per slice. [2]
* Each uSP has a Ray Tracing Unit which supports either 4 ray-triangles or 8 ray-box intersections per cycle. [2]
* each slice has a 128 KB cluster cache (L1?) which is then backed by a unified 2 MB L2 cache. This L2 can then spill into the 8 MB System Level Cache (SLC) which then is backed by the up to 228 GB/s memory subsystem. [2]

* Cooperative matrix size on Adreno 840: [[ref](https://allenkuo.medium.com/building-a-high-performance-ai-frame-interpolation-pipeline-on-android-with-vulkan-ncnn-rife-8f279cef51cd)]
	- Tile size: 64x64x16 fp16
	- Subgroup: 64

* cooperative matrix:
	- `16x64 * 16x64 + 64x64` size for fp16
	- `16x64 * 16x32 + 64x32` size for fp16
	- `16x64 * 16x16 + 64x16` size for fp16
	- `64x32 * 32x64 + 64x64` size for i8


## Specs

* X2-90:
	- clock: 1.7 - 1.85 GHz
	- 4 slices, 2048 ALU
	- fp32 TFLOPS: 7.5
	- RAM: LPDDR5X-9523, 128bit/192bit, 152-228 GB/s
	- HPM: 21 MB
	- GigaTris/s: 7.4
	- GigaPix/s: 118
	- GigaTexel/s: 236

* Adreno 840:
	- clock: 1.2 GHz
	- 3 slices, 1536 ALU
	- fp32 TFLOPS: 3.6
	- RAM: LPDDR5X, 64-bit, 5300 MHz, 84.8 GB/s
	- HPM: 18 MB
	- GigaPix/s: 57
	- GigaTexel/s: 115

* SoC:
	- X2E-96-100 (Adreno X2-90 with 1.85GHz and 228GB/s, 53MB shared cache)
	- X2E-88-100 (Adreno X2-90 with 1.7GHz and 152GB/s, 53MB shared cache)
	- X2E-80-100 (Adreno X2-85 with 1.7GHz and 152GB/s, 34MB shared cache)
	- Elite Gen 5 (Adreno 840, 2+6 core CPU up to 4.7GHz)
	- Elite Gen 5 for Galaxy (Adreno 840)
	- 8 Gen 5 (Adreno 829)

