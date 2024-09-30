Midgard is a 2nd generation of Mali GPU architecture.

Content:
* [Gen1](#Midgard-Gen1)
* [Gen2](#Midgard-Gen2)
* [Gen3](#Midgard-Gen3)
* [Gen4](#Midgard-Gen4)
* [All gens](#Midgard-(all-gens))

# Midgard Gen1

## Examples

* Mali-T604
* Mali-T658

## Notes

* Hierarchical Tiling system. [2]

# Midgard Gen2

## Examples

* Mali-T622
* Mali-T624
* Mali-T628
* Mali-T678

## Notes

* Forward Pixel Kill

# Midgard Gen3

## Examples

* Mali-T720
* Mali-T760

* Rockchip RK3288 (Mali-T760 MP4)

## References

3.1. [Vulkan features for Mali-T760](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-T760)<br/>

## Notes

# Midgard Gen4

## Examples

* Mali-T820
* Mali-T830
* Mali-T860
* Mali-T880

* Rockchip RK3399 (Mali-T860)

## References

4.1. [ARM Announces Mali 800 Series GPUs](https://www.anandtech.com/show/8649/arm-announces-mali-800-series-gpus-t860-t830-t820)<br/>
4.2. [Arm Mali-T820 and Arm Mali-T830 Performance Counters Reference Guide](https://developer.arm.com/documentation/108059/latest/), [[backup](../pdf/arm_mali-t820_and_arm_mali-t830_performance_counters_reference_guide_108059_0102_en.pdf)]<br/>
4.3. [Arm Mali-T860 and Arm Mali-T880 Performance Counters Reference Guide](https://developer.arm.com/documentation/108061/0103)<br/>
4.4. [Vulkan features for Mali-T880](https://vulkan.gpuinfo.org/listreports.php?devicename=Mali-T880)<br/>
4.5. [Mali-T880 is set to Deliver the Premium Mobile Experience of 2016](https://community.arm.com/arm-community-blogs/b/graphics-gaming-and-vr-blog/posts/mali-t880-is-set-to-deliver-the-premium-mobile-experience-of-2016)<br/>
4.6. [Mali-T830 Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench/ARM_Mali_T830.md)<br/>

## Notes

* core config: [5]
	- 1 fragment per cycle
	- 1 pixel per cycle
	- T820: 1 ALU, 28 fp16/cy, 16 fp32/cy
	- T830: 2 ALU, 56 fp16/cy, 32 fp32/cy
	- T860: 2 ALU, 52 fp16/cy, 28 fp32/cy
	- T880: 3 ALU, 78 fp16/cy, 42 fp32/cy

* T830: no AFBC [4.6]


# Midgard (all gens)

## References

1. [Midgard Architecture](https://fileadmin.cs.lth.se/cs/Education/EDAN35/guestLectures/ARM-Mali.pdf), [[backup](../pdf/ARM-Mali-Midgard.pdf)]
2. [ARM’s Mali Midgard Architecture Explored](https://www.anandtech.com/show/8234/arms-mali-midgard-architecture-explored)
3. [The Midgard Shader Core](https://developer.arm.com/documentation/102560/latest/Midgard-GPU-Architecture), [[backup](../pdf/learn_the_basics_-_the_midgard_shader_core_102560_0100_02_en.pdf)]
4. [Mesa driver details](https://docs.mesa3d.org/drivers/panfrost.html)
5. [Arm GPU Datasheet](https://developer.arm.com/documentation/102849/0700/), [[backup](../pdf/Arm_GPU_Datasheet_v3.pdf)]

## Notes

* Unified shader model
* SIMD ISA (vector)

* Mali Midgard GPU shader cores allow variable numbers of threads to be created, depending on the number of work registers that are used by the in-flight shader programs.<br/>
	0-4 registers - Maximum thread capacity
	5-8 registers - Half thread capacity
	8-16 registers - Quarter thread capacity
