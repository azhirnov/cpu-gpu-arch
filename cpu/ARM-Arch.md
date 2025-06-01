Content:
* [ARMv8-A](#ARMv8-A)
* [ARMv8.2-A](#ARMv82-A)
* [ARMv9.0-A](#ARMv90-A)
* [ARMv9.2-A](#ARMv92-A)


# ARMv8-A

## Examples

* Cortex: A35, A53, A57
* Cortex: A72, A73

## References

1.1. [ARM Reveals Cortex-A72 Architecture Details](https://www.anandtech.com/show/9184/arm-reveals-cortex-a72-architecture-details)<br/>
1.2. [Cortex A57, Nintendo Switch’s CPU](https://chipsandcheese.com/2023/12/12/cortex-a57-nintendo-switchs-cpu/)<br/>
1.3. [ARM’s Cortex A72: aarch64 for the Masses](https://chipsandcheese.com/2023/11/10/arms-cortex-a72-aarch64-for-the-masses/)<br/>
1.4. [ARM’s Cortex A53: Tiny But Important](https://chipsandcheese.com/2023/05/28/arms-cortex-a53-tiny-but-important/)<br/>
1.5. [Cortex A73’s Not-So-Infinite Reordering Capacity](https://chipsandcheese.com/2024/08/04/cortex-a73s-not-so-infinite-reordering-capacity/)<br/>

## Notes



# ARMv8.2-A

## Examples

* Cortex: A55, A75, A76, A77, A78, X1
* Neoverse N1

## References

2.1. [Exploring DynamIQ and ARM’s New CPUs: Cortex-A75, Cortex-A55](https://www.anandtech.com/show/11441/dynamiq-and-arms-new-cpus-cortex-a75-a55)<br/>
2.2. [Arm's New Cortex-A77 CPU Micro-architecture](https://www.anandtech.com/show/14384/arm-announces-cortexa77-cpu-ip)<br/>
2.3. [Arm's New Cortex-A78 and Cortex-X1 Microarchitectures](https://www.anandtech.com/show/15813/arm-cortex-a78-cortex-x1-cpu-ip-diverging)<br/>
2.4. [Arm Cortex-A78 Core Software Optimization Guide](https://developer.arm.com/documentation/102160/latest/)<br/>
2.5. [Arm Cortex-X1 Core Software Optimization Guide](https://documentation-service.arm.com/static/5f15a74720b7cf4bc5247c06)<br/>
2.6. [Deep Diving Neoverse N1](https://chipsandcheese.com/2021/10/22/deep-diving-neoverse-n1/)<br/>
2.7. [Arm Cortex-X1: The First From The Cortex-X Custom Program](https://fuse.wikichip.org/news/3543/arm-cortex-x1-the-first-from-the-cortex-x-custom-program/)<br/>
2.8. [Arm Unveils the Cortex-A78: When Less Is More](https://fuse.wikichip.org/news/3536/arm-unveils-the-cortex-a78-when-less-is-more/)<br/>
2.9. [Arm Unveils Cortex-A77, Emphasizes Single-Thread Performance](https://fuse.wikichip.org/news/2339/arm-unveils-cortex-a77-emphasizes-single-thread-performance/)<br/>

## Notes

* Optional FP16, BF16 support
* NEON: [2.3]
	- X1: 4x128b NEON bandwidth
	- A78: 2x128b NEON bandwidth
	- Arm's current ISA doesn't allow for individual vectors to be larger than 128b

# ARMv9.0-A

## Examples

* Cortex: A510, A710, A715, X2, X3
* Neoverse: E2, N2, V2

## References

3.1. [Arm Announces Mobile Armv9 CPU Microarchitectures: Cortex-X2, Cortex-A710 & Cortex-A510](https://www.anandtech.com/show/16693/arm-announces-mobile-armv9-cpu-microarchitectures-cortexx2-cortexa710-cortexa510)<br/>
3.2. [Arm Announces Armv9 Architecture](https://www.anandtech.com/show/16584/arm-announces-armv9-architecture)<br/>
3.3. [Arm’s Cortex A510: Two Kids in a Trench Coat](https://chipsandcheese.com/2023/10/01/arms-cortex-a510-two-kids-in-a-trench-coat/)<br/>
3.4. [Cortex X2: Arm Aims High](https://chipsandcheese.com/2023/10/27/cortex-x2-arm-aims-high/)<br/>
3.5. [Hot Chips 2023: Arm’s Neoverse V2](https://chipsandcheese.com/2023/09/11/hot-chips-2023-arms-neoverse-v2/)<br/>
3.6. [ARM’s Cortex A710: Winning by Default](https://chipsandcheese.com/2023/08/11/arms-cortex-a710-winning-by-default/)<br/>
3.7. [ARM’s Neoverse N2: Cortex A710 for Servers](https://chipsandcheese.com/2023/08/18/arms-neoverse-n2-cortex-a710-for-servers/)<br/>
3.8. [Correction for A710/Neoverse N2’s FP Scheduler Layout](https://chipsandcheese.com/2023/08/19/correction-for-a710-neoverse-n2s-fp-scheduler-layout/)<br/>
3.9. [Arm Refreshes The Cortex-A510, Squeezes Higher Efficiency](https://fuse.wikichip.org/news/6842/arm-refreshes-the-cortex-a510-squeezes-higher-efficiency/)<br/>
3.10. [Arm Unveils Next-Gen Flagship Core: Cortex-X3](https://fuse.wikichip.org/news/6855/arm-unveils-next-gen-flagship-core-cortex-x3/)<br/>
3.11. [Arm Introduces The Cortex-A715](https://fuse.wikichip.org/news/6853/arm-introduces-the-cortex-a715/)<br/>
3.12. [Arm Unveils Next-Gen Armv9 Little Core: Cortex-A510](https://fuse.wikichip.org/news/5268/arm-unveils-next-gen-armv9-little-core-cortex-a510/)<br/>
3.13. [Arm Launches Its New Flagship Performance Armv9 Core: Cortex-X2](https://fuse.wikichip.org/news/5269/arm-launches-its-new-flagship-performance-armv9-core-cortex-x2/)<br/>
3.14. [Arm Unveils Next-Gen Armv9 Big Core: Cortex-A710](https://fuse.wikichip.org/news/5267/arm-unveils-next-gen-armv9-big-core-cortex-a710/)<br/>

## Notes

* X3:
	- 11 cycle mispredict penalty
	
* A715:
	- 12 cycle mispredict penalty
	- 10 cycle latency to access L2
	
* A520:
	- 3x ALU pipelines


# ARMv9.2-A

## Examples

* Cortex: A520, A720, A725, X4, X925

## References

4.1. [Arm Unveils 2023 Mobile CPU Core Designs: Cortex-X4, A720, and A520](https://www.anandtech.com/show/18871/arm-unveils-armv92-mobile-architecture-cortex-x4-a720-and-a520-64bit-exclusive)<br/>
4.2. [Arm Cortex-A520 Core Software Optimization Guide](https://developer.arm.com/documentation/PJDOC-1505342170-671342/latest)<br/>
4.3. [Arm Cortex-X4 Core Software Optimization Guide](https://developer.arm.com/documentation/PJDOC1505342170538636/latest/)<br/>
4.4. [Arm Cortex-X4 Core Technical Reference Manual](https://developer.arm.com/documentation/102484/0002/The-Cortex-X4--core)<br/>
4.5. [Arm Unveils 2024 CPU Core Designs, Cortex X925, A725 and A520](https://www.anandtech.com/show/21399/arm-unveils-2024-cpu-core-designs-cortex-x925-a725-and-a520-arm-v9-2-redefined-for-3nm-)<br/>
4.6. [Arm Launches Next-Gen Big-Core: Cortex-A725](https://fuse.wikichip.org/news/7829/arm-launches-next-gen-big-core-cortex-a725/)<br/>
4.7. [Arm Launches Next-Gen Flagship Cortex-X925](https://fuse.wikichip.org/news/7761/arm-launches-next-gen-flagship-cortex-x925/)<br/>
4.8. [Arm Introduces A New Big Core, The Cortex-A720](https://fuse.wikichip.org/news/7529/arm-introduces-a-new-big-core-the-cortex-a720/)<br/>
4.9. [Arm Introduces The Cortex-X4, Its Newest Flagship Performance Core](https://fuse.wikichip.org/news/7531/arm-introduces-the-cortex-x4-its-newest-flagship-performance-core/)<br/>
4.10. [Arm Launches Next-Gen Efficiency Core; Cortex-A520](https://fuse.wikichip.org/news/7527/arm-launches-next-gen-efficiency-core-cortex-a520/)<br/>

# All

## References


## Notes

* Optional support for fp8 (E5M2, E4M3).

* X4: [4.1]
	- 10 cycle mispredict penalty
	- branch mispredict penalty is down from 11 cycles to 10.
	- increased the number of ALUs from 6 to 8.

* A720: [4.1]
	- 11 cycle mispredict penalty
	- Pipelined FDIV/FSQRT - concurrent executions of both FDI and FSQRT can improve instruction throughput.
	- 9 cycle latency to access L2
	- 2x memset bandwidth in L2

* A520: [4.1]
	- can be merged in pairs to share pipelines and improve efficiency.
	- allow to share single SVE between two cores.
	- removed third ALU
