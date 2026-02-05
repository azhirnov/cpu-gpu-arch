
## Examples

* Adreno 810, 830, 840
* Adreno X2

**SoC/Device**
* Snapdragon 8 Elite / Gen 4 (Adreno 830)
* Snapdragon 8 Elite 2 / Gen 5 (Adreno 840)


## References

1. [Vulkan features for Adreno 830](https://vulkan.gpuinfo.org/listreports.php?devicename=Adreno%20(TM)%20830)
2. [Diving into Qualcomm's Upcoming Adreno X2 GPU with Eric Demers](https://chipsandcheese.com/p/diving-into-qualcomms-upcoming-adreno)
3. [Qualcomm’s Snapdragon X2 Elite](https://chipsandcheese.com/p/qualcomms-snapdragon-x2-elite)


## Features

* Immediate mode rendering instead of TBDR
* Universal Bandwidth Compression v6

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


## Specs

* X2-90:
	- fp32 TFLOPS: 7
	- RAM: LPDDR5X-9523 128bit/192bit, 152-228 GB/s
	- GMem/HPM: 21 MB


