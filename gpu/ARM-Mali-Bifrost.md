
# Bifrost Gen1

## Examples

* Mali-G31
* Mali-G51
* Mali-G71

## References

1.1. [ARM Unveils Next Generation Bifrost GPU Architecture & Mali-G71](https://www.anandtech.com/show/10375/arm-unveils-bifrost-and-mali-g71)<br/>
1.2. [Arm Mali-G71 Performance Counters Reference Guide](https://developer.arm.com/documentation/102641/0106), [pdf](../pdf/arm_mali-g71_performance_counters_reference_guide_102641_0105_en.pdf)<br/>

## Notes

* implement a single texel-per-clock and single pixel-per-clock shader core.
* G71: 4-wide SIMD per quad; 3x quads per core. 12 FMAs at the same time. These 3 quads are managed by a core's quad manager. [4]
* In both the Mali-G71 and G72, a quad is just that: a 4-wide SIMD unit, with each lane possessing separate FMA and ADD/SF pipes. [4]

# Bifrost Gen2

## Examples

* Mali-G52
* Mali-G72

## References

2.1. [ARM Announces Mali-G72](https://www.anandtech.com/show/11459/arm-announces-malig72-bifrost-refined-for-the-highend-soc)<br/>
2.2. [Arm Mali-G72 Performance Counters Reference Guide](https://developer.arm.com/documentation/102642/0106/), [pdf](../pdf/arm_mali-g72_performance_counters_reference_guide_102642_0106_en.pdf)<br/>

## Notes

* implement a single texel-per-clock and single pixel-per-clock shader core.

# Bifrost Gen3

## Examples

* Mali-G76

## References

3.1. [Arm Mali-G76 Performance Counters Reference Guide](https://developer.arm.com/documentation/102697/latest/), [pdf](../pdf/arm_mali-g76_performance_counters_reference_guide_102697_0106_en.pdf)<br/>

## Notes

* Implement a two texel-per-clock and two pixel-per-clock shader core, with an increase in arithmetic performance to compensate. Not every GPU doubled the available performance though.
* G76: 8-wide SIMD per quad, 3 quads per core. [4]


# Bifrost (all gens)

## References

1. [The Bifrost Shader Core](https://community.arm.com/developer/tools-software/graphics/b/blog/posts/the-mali-gpu-an-abstract-machine-part-4---the-bifrost-shader-core), [pdf](../pdf/the_bifrost_shader_core_102546_0100_02_en.pdf)
2. [The Bifrost GPU architecture](https://old.hotchips.org/wp-content/uploads/hc_archives/hc28/HC28.22-Monday-Epub/HC28.22.10-GPU-HPC-Epub/HC28.22.110-Bifrost-JemDavies-ARM-v04-9.pdf)
3. [Mesa driver details](https://docs.mesa3d.org/drivers/panfrost.html)
4. [Everything we learnt from hacking Arm Mali GPUs](https://github.com/fxlin/mali)

## Notes

* scalar
* Mali GPUs can contain many identical shader cores. Each shader core supports hundreds of concurrently executing threads. [4]
* Each shader core contains: [4]
	- One to three arithmetic pipelines or execution engines.
	- One load-store pipeline.
	- One texture pipeline.
