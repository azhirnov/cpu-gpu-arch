

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

* Firestorm (A14 / M1): [llm]
	- fp32 FLOPS/cy:  32 (4 × 128-bit FMA)
	- i32 ops/cy:     16
	- L1 latency:      3 cy
	- L1 bandwidth:   96 B/cy (3×128-bit loads + 3×128 stores)
	- L2 latency:      8 cy
	- L2 bandwidth:   96 B/cy
	- Vector formats: fp32, fp16, bf16, int8/16/32, dotprod
	- Extra: AMX (matrix) 8 k × 8 k B tiles, fp16/bf16/int8

* Icestorm (A14/M1): [llm]
	- fp32 FLOPS/cy:  8 (1 × 128-bit FMA)
	- i32 ops/cy:     4
	- L1 latency:     3 cy
	- L1 bandwidth:  32 B/cy
	- L2 latency:     9 cy (shared 4 MB with all E-cores)
	- L2 bandwidth:  32 B/cy
	- Vector formats: fp32, fp16, int8/16/32, dotprod

* NPU with 11 TOPS on i8 (?)


# M2

## Notes

* Instruction set: ARMv8.6-A

* Avalanche (A15 / M2): [llm]
	- fp32 FLOPS/cy:  32
	- i32 ops/cy:     16
	- L1 latency:      3 cy
	- L1 bandwidth:   128 B/cy (4×128-bit ld + 4×128 st)
	- L2 latency:     7-8 cy
	- L2 bandwidth:   128 B/cy
	- Vector formats: fp32, fp16, bf16, int8/16/32, dotprod
	- Extra: AMX v2, adds fp32 accumulation

* Blizzard (A15/M2): [llm]
	- fp32 FLOPS/cy:  8
	- i32 ops/cy:     4
	- L1 latency:     3 cy
	- L1 bandwidth:  32 B/cy
	- L2 latency:     8 cy
	- L2 bandwidth:  32 B/cy
	- Vector formats: fp32, fp16, bf16, int8/16/32, dotprod


# M3

## References

1. [Apple Announces M3 SoC Family](https://www.anandtech.com/show/21116/apple-announces-m3-soc-family-m3-m3-pro-and-m3-max-make-their-marks)

## Notes

* Instruction set: ARMv8.7-A

* Everest (A16 / A17 Pro / M3): [llm]
	- fp32 FLOPS/cy:  48 (6 × 128-bit FMA)
	- i32 ops/cy:     24
	- L1 latency:      3 cy
	- L1 bandwidth:   128 B/cy
	- L2 latency:     6-7 cy
	- L2 bandwidth:   128 B/cy
	- Vector formats: fp32, fp16, bf16, int8/16/32, dotprod
	- Extra: AMX v3 with fp8 & int4 support

* Sawtooth (A16/A17/M3): [llm]
	- fp32 FLOPS/cy:   8
	- i32 ops/cy:      4
	- L1 latency:      3 cy
	- L1 bandwidth:   32 B/cy
	- L2 latency:      7 cy
	- L2 bandwidth:   32 B/cy
	- Vector formats: fp32, fp16, bf16, int8/16/32, dotprod, fp8 (via AMX)


# M4

## References

1. [Apple Announces M4 SoC](https://www.anandtech.com/show/21387/apple-announces-m4-soc-latest-and-greatest-starts-on-ipad-pro)

## Notes

* Instruction set: ARMv9.2-A

* NPU with 38 TOPS on i8


# M5

## Notes

* RAM bandwidth 156 GB/s

