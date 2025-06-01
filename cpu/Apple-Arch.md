

# M1

1. [Brief notes on Apple M1 Firestorm microarchitecture](https://github.com/ocxtal/insn_bench_aarch64/blob/master/optimization_notes_apple_m1.md)
2. [Augury: Using Data Memory-Dependent Prefetchers to Leak Data at Rest](https://www.prefetchers.info/augury.pdf)

## Notes

* Instruction set: ARMv8.4-A
* CPU features (from `sysctl -a`):
	- SHA3, SHA2-256, SHA2-512, SHA1, AES
	- neon, neon_hpfp, neon_fp16
	- FEAT_FP16

* There are four execution ports in the SIMD/fp domain. All ports are capable of most of the arithmetic and logic instructions. [1]
	- All execution units, V0~V3, processes basic arithmetic and logical operations with a latency of two cycles and a throughput of four per clock cycle.
	- Most others are three-cycle instructions, such as saturating and rounding arithmetic, horizontal, high-narrow form, and absolute difference operations. It is noticeable that integer multiplication and multiply-accumulate are processed in three cycles, too.

* 8x fp32 FLOPS/cy on P-core (2cy latency 4/cy throughput)
* 4x fp32 FLOPS/cy on E-core

* Transfer between the scalar and SIMD/fp domains is intriguing. The forward transfer, scalar-to-SIMD/fp direction, uses a slot in the load units, and the reverse has dedicated paths. Latency appears to be six cycles in both directions. Throughput is three instructions every cycle for the forward and two for the opposite direction. [1]
* Conversion from integer to floating point is executed on all units. [1]

* Data memory-dependent prefetcher (DMP). [2]
	- These prefetchers are designed to allow prefetching of irregular address patterns such as pointer chases.
	- DMPs examine and use the contents of memory directly to determine which addresses to prefetch.
	- Processors possess an Array-of-Pointers (AoP) prefetcher that recognizes streaming and striding reads and dereferences over an array of pointers, and then prefetches the result of dereferencing future pointers.
	- As the AoP DMP operates only on a stream of memory accesses, and does not have any concept of array bounds, this prefetcher can overshoot the legal set of pointers to access and attempt a prefetch of unrelated memory addresses up to its prefetch depth.


# M2

## Notes

* Instruction set: ARMv8.6-A

# M3

## References

1. [Apple Announces M3 SoC Family](https://www.anandtech.com/show/21116/apple-announces-m3-soc-family-m3-m3-pro-and-m3-max-make-their-marks)

## Notes

* Instruction set: ARMv8.6-A

# M4

## References

1. [Apple Announces M4 SoC](https://www.anandtech.com/show/21387/apple-announces-m4-soc-latest-and-greatest-starts-on-ipad-pro)

## Notes

* Instruction set: ARMv9.2-A
