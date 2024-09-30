
## Examples

* 504, 505, 506, 510 with LPDDR3
* 508, 509 with LPDDR4
* 512, 530, 540 with LPDDR4X

* Oculus Quest (Adreno 540)
* Oculus Go (Adreno 530)


## References

1. [Mesa driver details](https://docs.mesa3d.org/drivers/freedreno.html)
2. [Inside Qualcomm’s Adreno 530](https://chipsandcheese.com/2024/01/20/inside-qualcomms-adreno-530-a-small-mobile-igpu/)
3. [Correction on Qualcomm iGPUs](https://chipsandcheese.com/2024/05/06/correction-on-qualcomm-igpus/)
4. [Vulkan features for Adreno 540](https://vulkan.gpuinfo.org/listreports.php?devicename=Adreno%20(TM)%20540)
5. [Game Developer Guides](https://developer.qualcomm.com/sites/default/files/docs/adreno-gpu/developer-guide/gpu/gpu.html), [[webarchive](https://web.archive.org/web/20220104180856/https://developer.qualcomm.com/sites/default/files/docs/adreno-gpu/developer-guide/gpu/gpu.html)]
6. [Adreno 505 Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench/Adreno_505.md)


## Notes

* Has low resolution Z pass: [1]<br/>
 "During the binning pass, a low resolution Z-buffer is constructed, and can reject LRZ-tile wide contributions to boost binning performance. This LRZ is then used during the rendering pass to reject pixels efficiently before testing against the full resolution Z-buffer."
* Has forward pass for fullscreen quad/triangle.

* Starting on A5X GPUs, an LRZ pass happens in binning and can discard tile wide contributions. [5]
* On A5X, GPUs push constants are not recommended. [5]
* On A5X GPUs, one (1) texture per fragment at full rate is equivalent to 16 full precision ALUs. [5]

* Adreno 660 core config:
	- 48 ALU
	- 650 MHz
	- fp64:  15.6 gflops, 1/4 fp32
	- fp32:  62.4 gflops
	- fp16: 124.8 gflops, 2x fp32

**Adreno 530**:
* has 2 compute queues. [2]
* 1SP: 32x Fp32, 4x SFU; it means sqrt/sin/cos executes in 1/8 rate; int executed in 1/4 rate. [2]
