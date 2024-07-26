
# Valhall Gen1

## Examples

* Mali-G57
* Mali-G77

## References

1.1. [Arm's New Mali-G77 & Valhall GPU Architecture](https://www.anandtech.com/show/14385/arm-announces-malig77-gpu/2)<br/>
1.2. [Arm Mali-G77 Performance Counters Reference Guide](https://developer.arm.com/documentation/102730/latest/), [pdf](../pdf/arm_mali-g77_performance_counters_reference_guide_102730_0106_en.pdf)<br/>

## Notes

* Static branching or early termination is not supported.
* Fragment Task with 32x32 pixels region.


# Valhall Gen2

## Examples

* Mali-G68
* Mali-G78

## References

2.1. [Arm Announces The Mali-G78 GPU](https://www.anandtech.com/show/15816/arm-announces-the-malig78-evolution-to-24-cores/2)<br/>
2.2. [Mali-G78 Performance Counters Reference Guide](https://developer.arm.com/documentation/102626/0100), [pdf](../pdf/arm_mali-g78_performance_counters_reference_guide_102626_0106_en.pdf)<br/>


# Valhall Gen3

## Examples

* Mali-G310
* Mali-G510
* Mali-G610
* Mali-G710

## References

3.1. [Arm Mali-G610 Performance Counters Reference Guide](https://developer.arm.com/documentation/102812/0108/), [pdf](../pdf/arm_mali-g610_performance_counters_reference_guide_102812_0107_en.pdf)<br/>


# Valhall Gen4

## Examples

* Mali-G615
* Mali-G715
* Immortalis-G715

## References

4.1. [Arm Mali-G615 Performance Counters Reference Guide](https://developer.arm.com/documentation/107775/0106), [pdf](../pdf/arm_mali-g615_performance_counters_reference_guide_107775_0105_en.pdf)<br/>


# Valhall Gen5

## Examples

* Mali-G620
* Mali-G720
* Immortalis-G720

## References

5.1. [Arm Mali-G620 Performance Counters Reference Guide](https://developer.arm.com/documentation/108080/0104)<br/>
5.2. [Arm Immortalis-G720 and Arm Mali-G720 Performance Counters Reference Guide](https://developer.arm.com/documentation/108081/0104), [pdf](../pdf/arm_immortalis-g720_and_arm_mali-g720_performance_counters_reference_guide_108081_0103_en.pdf)<br/>
5.3. Deferred Vertex Shading: [slide 1](../img/arm-dvs-1.jpg), [slide 2](../img/arm-dvs-2.jpg)<br/>

## Notes

* Deferred Vertex Shading. [ref](https://t.me/cg_cpp_dev/131) - TODO
* Added a 2x MSAA module, as previously when a developer would request 2x MSAA from the GPU, it would automatically jump to 4x MSAA.
* Fragment Task with 64x64 pixels region.


# Valhall (all gens)

## References

1. [Instruction Set Architecture](https://rosenzweig.io/Valhall-Documentation.pdf), [pdf](../pdf/Valhall-Documentation.pdf)
2. [The Valhall Shader Core](https://developer.arm.com/documentation/102203/0100/Fourth-generation-Mali-GPU-architecture), [pdf](../pdf/the_valhall_shader_core_guide_102203_0100_03_en.pdf)
3. [Mesa driver details](https://docs.mesa3d.org/drivers/panfrost.html)



## Notes

* scalar
* All Valhall GPU cores implement a four texel-per-clock and two pixel-per-clock shader core.
* Mali Valhall GPU shader cores allow variable numbers of threads to be created, depending on the number of work registers that are used by the in-flight shader programs.<br/>
	0-32 registers - Maximum thread capacity
	33-64 registers - Half thread capacity
