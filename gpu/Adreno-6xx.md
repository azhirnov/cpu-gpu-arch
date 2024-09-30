
## Examples

* 640, 660

* Oculus Quest 2, Meta Quest Pro, Pico 4 (Adreno 650)


## References

1. [Mesa driver details](https://docs.mesa3d.org/drivers/freedreno.html)
2. [Qualcomm Details The Snapdragon 888](https://www.anandtech.com/show/16271/qualcomm-snapdragon-888-deep-dive)
3. [Inside the Snapdragon 855’s iGPU](https://chipsandcheese.com/2024/05/01/inside-the-snapdragon-855s-igpu/)
4. [Correction on Qualcomm iGPUs](https://chipsandcheese.com/2024/05/06/correction-on-qualcomm-igpus/)
5. [Vulkan features for Adreno 660](https://vulkan.gpuinfo.org/listreports.php?devicename=Adreno%20(TM)%20660)
6. [Qualcomm Announces Snapdragon 865 and 765(G)](https://www.anandtech.com/show/15178/qualcomm-announces-snapdragon-865-and-765-5g-for-all-in-2020-all-the-details)
7. [Adreno 660 Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench/Adreno_660.md)


## Notes

* Has low resolution Z pass:
 "During the binning pass, a low resolution Z-buffer is constructed, and can reject LRZ-tile wide contributions to boost binning performance. This LRZ is then used during the rendering pass to reject pixels efficiently before testing against the full resolution Z-buffer."
* Has forward pass (immediate mode rendering) for fullscreen quad/triangle.
* Supports wave64 and wave128 execution. In Vulkan has maxSubgroupSize = 128.

* Adreno 660 core config:
	- 384 ALU
	- 900 MHz
	-  384 fp64 / clock,  345.6 gflops, 1/4x fp32
	- 1536 fp32 / clock, 1382.4 gflops
	- 3072 fp16 / clock, 2764.8 gflops, 2x fp32


* Adreno 640 core config:
	- freq: 585 MHz
	- pipelines: 2 (queues?)
	- Shading units: 384
	- Total shaders: 768
	- FLOPS: 898.5 Gflops
	- 384 ALU
	- 9.4 GPixels/s
	- 898.5 FP32 GFLOPS
	- 1797.1 FP16 GFLOPS

* Adreno 640 config: [3,4]
	- 2MB system level cache (between L2 and RAM).
	- 128KB L2 cache.
	- 1MB gmem
	- 2x Shader Processors.
	- per Shader Processor:
		* 32 KB local memory
		* 16 KB instruction cache
		* 3x Micro Shader Processor Texture Processor (uSPTP).
		* ROPs (2x 64 KB *part of gmem?*)
	- per uSPTP:
		* 1KB texture cache (L1)
		* 4x texture units
		* 16 KB instruction cache
		* 2x scheduler partitions
	- per uSPTP scheduler partition:
		* Scheduler with 8 entry (?)
		* 32 KB register file (?)
		* 128x FP16
		* 64x FP32
		* 32x INT32
		* 8x IMUL
		* 8x SFU
	- 6x uSPTPs.
	- 12x uSPTP scheduler partitions.
	- 768x FP32 units.

	![](https://i0.wp.com/chipsandcheese.com/wp-content/uploads/2024/05/s855_a640_updated.png)<br/>
	[[backup](../img/chipsandcheese_adreno640_arch.jpg)]

	![](https://i0.wp.com/chipsandcheese.com/wp-content/uploads/2024/05/adreno_usptp.png)<br/>
	[[backup](../img/chipsandcheese_adreno640_usptp.jpg)]

* Adreno 640 performace: [3]
	- 408 GOPS FP32 Add (898.5 from specs)
	- 407 GOPS FP32 FMA
	-  55 GOPS FP32 Reciprocal
	-  55 GOPS FP32 InvSqrt
	- 432 GOPS FP16 FMA (incorrect [4]) (1797.1 from specs)
	- 461 GOPS FP16 Add (incorrect [4])
	-  84 GOPS INT64 Add
	-  10 GOPS INT64 Mul
	- 188 GOPS INT32 Add
	-  62 GOPS INT32 Mul
	- 218 GOPS INT16 Add
	- 208 GOPS INT16 Mul
	- 229 GOPS INT8 Add
	- 215 GOPS INT8 Mul
	- 88 GB/s local memory bandwidth
	- 37ns local memory latency
	- 192 GB/s texture cache bandwidth
	- 47 cycles L2 cache latency
	- Snapdragon 855’s system level cache offers about 40 GB/s, while main memory bandwidth is a touch below 30 GB/s.
	- In Slingshot Extreme, Adreno 640’s shaders are busy around 90% of the time, while ALU capacity sees 30-40% utilization.

* new mixed-precision dot product as well as FP16/FP32 wave matrix-multiply instructions. [2]
* Adreno 640 lets code allocate up to 32 KB of local memory per workgroup, but can only have 64 KB of local memory active at a time across the GPU. Therefore, it probably has one 32 KB local memory instance per 3 SPs. [3]
* Fully utilizing the FP16 ALU requires wave128. [4]
* each uSPTP should be capable of tracking 16 wave128 threads, or 8 per ALU partition. [4]

