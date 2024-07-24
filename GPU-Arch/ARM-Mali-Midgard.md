
# Midgard Gen1

## Examples

* Mali-T604
* Mali-T658

# Midgard Gen2

## Examples

* Mali-T622
* Mali-T624
* Mali-T628
* Mali-T678

# Midgard Gen3

## Examples

* Mali-T720
* Mali-T760

# Midgard Gen4

## Examples

* Mali-T820
* Mali-T830
* Mali-T860
* Mali-T880

## References

* [ARM Announces Mali 800 Series GPUs](https://www.anandtech.com/show/8649/arm-announces-mali-800-series-gpus-t860-t830-t820)


# Midgard (all gens)

## References

* http://fileadmin.cs.lth.se/cs/Education/EDAN35/guestLectures/ARM-Mali.pdf
* https://www.hotchips.org/wp-content/uploads/hc_archives/hc28/HC28.22-Monday-Epub/HC28.22.10-GPU-HPC-Epub/HC28.22.110-Bifrost-JemDavies-ARM-v04-9.pdf
* http://malideveloper.arm.com/downloads/ARM_Game_Developer_Days/PDFs/2-Mali-GPU-architecture-overview-and-tile-local-storage.pdf
* (https://www.anandtech.com/show/8234/arms-mali-midgard-architecture-explored)


## Notes

* Unified shader model
* SIMD ISA (vector)

* Mali Midgard GPU shader cores allow variable numbers of threads to be created, depending on the number of work registers that are used by the in-flight shader programs.<br/>
	0-4 registers - Maximum thread capacity
	5-8 registers - Half thread capacity
	8-16 registers - Quarter thread capacity
