
# Valhall Gen1

## Examples

* Mali-G57
* Mali-G77

## References

1. [Arm's New Mali-G77 & Valhall GPU Architecture](https://www.anandtech.com/show/14385/arm-announces-malig77-gpu/2)

## Notes

* Static branching or early termination is not supported.


# Valhall Gen2

## Examples

* Mali-G68
* Mali-G78

## References

2. [Arm Announces The Mali-G78 GPU](https://www.anandtech.com/show/15816/arm-announces-the-malig78-evolution-to-24-cores/2)

## Notes



# Valhall Gen3

## Examples

* Mali-G310
* Mali-G510
* Mali-G610
* Mali-G710

## Notes


# Valhall Gen4

## Examples

* Mali-G615
* Mali-G715
* Immortalis-G715

## Notes



# Valhall Gen5

## Examples

* Mali-G620
* Mali-G720
* Immortalis-G720

## Notes

* Deferred Vertex Shading.
* Added a 2x MSAA module, as previously when a developer would request 2x MSAA from the GPU, it would automatically jump to 4x MSAA.


# Valhall (all gens)

## References

3. TODO (Mali Valhall architecture.pdf)

## Notes

* scalar
* All Valhall GPU cores implement a four texel-per-clock and two pixel-per-clock shader core.
* Mali Valhall GPU shader cores allow variable numbers of threads to be created, depending on the number of work registers that are used by the in-flight shader programs.<br/>
	0-32 registers - Maximum thread capacity
	33-64 registers - Half thread capacity
