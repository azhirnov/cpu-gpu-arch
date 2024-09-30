
## Examples

Without RTX:
* GTX 16xx
* GTX 16xx Max-Q
* Quadro Txxx
* MX450, MX550 (?)

With RTX:
* RTX 20xx
* Quadro RTX x000

## References

1. [Tuning CUDA Applications for Turing](https://docs.nvidia.com/cuda/turing-tuning-guide/)
2. [Turing Architecture In-Depth](https://developer.nvidia.com/blog/nvidia-turing-architecture-in-depth/)
3. [Architecture Whitepaper](https://images.nvidia.com/aem-dam/en-zz/Solutions/design-visualization/technologies/turing-architecture/NVIDIA-Turing-Architecture-Whitepaper.pdf), [[backup](../pdf/NVIDIA-Turing-Architecture-Whitepaper.pdf)]
4. [Dissecting the NVidia Turing T4 GPU via Microbenchmarking](https://arxiv.org/pdf/1903.07486), [[backup](../pdf/Turing-Microbenchmarking.pdf)]
5. [Re-converging control flow on NVIDIA GPUs](https://www.collabora.com/news-and-blog/blog/2024/04/25/re-converging-control-flow-on-nvidia-gpus/)
6. [Implementing DRM format modifiers in NVK](https://www.collabora.com/news-and-blog/news-and-events/implementing-drm-format-modifiers-in-nvk.html)
7. [Dissecting the Turing GPU Architecture through Microbenchmarking](https://developer.download.nvidia.com/video/gputechconf/gtc/2019/presentation/s9839-discovering-the-turing-t4-gpu-architecture-with-microbenchmarks.pdf)
8. [Compute Capability 7.5](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#compute-capability-7-x)
9. [Vulkan features for RTX 2080](https://vulkan.gpuinfo.org/listreports.php?devicename=NVIDIA%20GeForce%20RTX%202080)
10. [RTX 2080 Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/bench/NVidia_RTX2080.md)

## Notes

### SM
* Independent Thread Scheduling.
	- On recent NVIDIA hardware, the two sides of an `if` may even be executed simultaneously since the two sides act on disjoint sets of invocations. [5]
	- TODO [7]
	- Scheduler operate on threads instead of warps. So when things diverged, the scheduler serialised the divergent components. Do divergent block `A` till completion, then `B`. [?]
	- Each L0 instruction cache is private to one scheduler/processing block. [4]

* Instruction Scheduling: [1]
	- Each Turing SM includes 4 warp-scheduler units. Each scheduler handles a static set of warps and issues to a dedicated set of arithmetic instruction units. Instructions are performed over two cycles, and the schedulers can issue independent instructions every cycle. Dependent instruction issue latency for core FMA math operations is four clock cycles, like Volta, compared to six cycles on Pascal. As a result, execution latencies of core math operations can be hidden by as few as 4 warps per SM, assuming 4-way instruction-level parallelism ILP per warp, or by 16 warps per SM without any instuction-level parallelism.
	- Each of the four SM processing blocks (also called partitions) had two primary datapaths, but only one of the two could process FP32 operations. The other datapath was limited to integer operations.

* Independent integer datapath:
	- Applications can interleave pointer arithmetic with floating-point computations. [1]
	- Index math and pointer math instructions can run in parallel with FP instructions. [7]
	- Profiling many workloads shows an average of 36 integer operations for every 100 floating point operations. [2]
	- fp32:i32 rate:  1:1 - not supported, 2:1 - supported, only IADD. [10]

* Warp mapping: [4]
	- Warps are mapped to schedulers (and processing blocks) according to the same, simple rule: `scheduler_id = warp_id%4`.
	- This is demonstrated with a benchmark composed of 8 warps running on a single SM simultaneously, of which only 2 are active with loops of FFMA instructions, while the remaining 6 are idle.
	- These results indicate that every block of your workload must use at least 128 threads to fully utilize the processing units on one SM.
* The SM memory path has been redesigned to unify shared memory, texture caching, and memory load caching into one unit. [1]

* Uniform Data Path. This design is intended to accelerate numerical, array-based, computebound workloads that occupy the main datapaths almost completely with floating-point instructions, typically FFMA or HMMA, but also contain a few integer operations, typically updating array indices, loop indices or pointers; or performing array or loop boundary checks. These few integer instructions spoil the instruction mix, and prevent the main datapaths from ingesting a 100% pure stream of FFMA or HMMA. In these circumstances, even a small fraction of integer instructions can hurt the overall arithmetic throughput, lowering it significantly from its theoretical maximum. [4]

* fp16 performance: HADD2, HMUL2, HFMA2 has same performance, MAD has 2 instructions, so HFMA2 should be used instead. [10]
* SM bound to one or multiple render target regions with tile size 16x16 (or lower on high register usage) [10]


### Memory

* On NVIDIA GPUs, however, a small amount of information about the image is encoded into the page tables. Each combination of format, sample count, and compression node maps to an 8-bit PTE kind. On Turing (RTX 2000-series and GTX 1600-series) and later GPUs, there are three PTE kinds for all color images and two for each depth/stencil format. [6]

* The combination of raw bandwidth increases, and traffic reduction translates to a 50% increase in effective bandwidth on Turing compared to Pascal. [3]


## Features

* Hardware ray tracing (RT core). [2]
* Mesh shaders. [2]
* Variable Rate Shading. [2]
* Texture-Space Shading. [2]
* Multi-View Rendering. [2]
* Tensor core. [2]
* higher L1/L2 cache and global memory bandwidth. [7]
* higher arithmetic throughput for matrix math. [7]
* new L0 instruction cache. [7]

## Specs

* Occupancy: [1]
	- The maximum number of concurrent warps per SM is 32.
	- The register file size is 64k 32-bit registers per SM.
	- The maximum registers per thread is 255.
	- The maximum number of thread blocks per SM is 16.
	- Shared memory capacity per SM is 64KB.
* SM: [1]
	- 64 FP32 cores
	- 64 INT32 (dedicated) cores
	- 2 FP64 cores
	- 8 improved mixed-precision Tensor Cores
	- 4 warps
* [7]
	- 4 Load/Store Units (LSU) per scheduler
	- 1024 threads per SM
	- upper limit of total registers is 256, including both regular and uniform registers 
* registers:
	- use a physical register file of 16 384, 32-bit elements in each processing block [4]
	- 64 uniform registers per thread [7]
	- 64 KiB registers, 16 KiB L0 instruction cache - per SM [4]
* L1 data cache: [4]
	- 96 KiB L1 data cache / shared memory - per SM
	- 32B line
	- 32 cycles hit latency
	- 32B load granularity
	- 128B update granularity
	- 58.83 bytes/cycle/SM actual bandwidth
	- 116 GiB/s bandwidth (RTX 2080) [1]
* L1 const cache: [4]
	- 64B line
	- 2 KiB L1 constant cache per SM
* L1.5 const cache: [4]
	- 256B line
	- ~46 KiB L1.5 constant cache / L1 instruction cache - per SM
* L2 cache: [4]
	- 64B line
	- 188 cycles hit latency
	- 4096 KiB L2 data cache / L2 constant cache / L2 instruction cache - per SM
* VRAM [4]
	- 320 GiB/s theoretical bandwidth
	- 220 GiB/s actual bandwidth

* Instruction Latency: [4]
	- 4: IADD3, SHF, LOP3, SEL, MOV, FADD, FFMA, FMUL, ISETP, FSET, FSETP
	- 5: IMAD, FMNMX, DSET, DSETP
	- 6: HADD2, HMUL2, HFMA2
	- ~15: POPC, FLO, BREV, MUFU
	- ~48: DADD, DMUL
	- ~54: DFMA, DSET, DSETP
	- integer and single precision instructions have 4-cycle latency [7]

* Atomics: [4]
	- 1.5 GiB/s global memory throughput when 1024 threads accessing the same address
	- 8..69 cycle latency on shared memory
	- 76..116 cycles latency on global memory

* GeForce RTX 2080 Ti Founders Edition: [2]
	- 14.2 TFLOPS of peak single precision (FP32) performance
	- 28.5 TFLOPS of peak half precision (FP16) performance
	- 14.2 TIPS concurrent with FP, through independent integer execution units
	- 113.8 Tensor TFLOPS
	- 10 Giga Rays/sec
	- 78 Tera RTX-OPS

* TU102 GPU (RTX 2080 Ti / Quadro RTX 6000): [2]
	- 6 Graphics Processing Clusters (GPCs)
	- 36 Texture Processing Clusters (TPCs)
	- 72 Streaming Multiprocessors (SMs)
	- Each GPC includes a dedicated raster engine and six TPCs
	- Each TPC including two SMs
	- Each SM contains:
		* 64 CUDA Cores
		* 8 Tensor Cores
		* 256 KB register file
		* 4 texture units
		* 96 KB of L1/shared memory
		* RT Core processing engine
	- Tied to each memory controller are 8 ROP units and 512 KB of L2 cache.
	- SM is partitioned into 4 processing blocks, each with:
		* 16 FP32 Cores
		* 16 INT32 Cores
		* 2 Tensor Cores
		* 1 warp scheduler [2,4]
		* 1 dispatch unit [2,4]
		* includes a new L0 instruction cache and a 64 KB register file.
	- Traditional graphics workloads partition the 96 KB L1/shared memory as 64 KB of dedicated graphics shader RAM and 32 KB for texture cache and register file spill area.
	- Compute workloads can divide the 96 KB into 32 KB shared memory and 64 KB L1 cache, or 64 KB shared memory and 32 KB L1 cache.

* ops/clock per SM: [8]
	- 128 fp16 FMA
	- 64 fp32 FMA
	- 2 fp64 FMA
	- 16 fp32 rcp, rsqrt, log2, exp2, sin, cos
	- 64 i32 add/sub/mad
	- 64 i32 shift
	- 64 cmp, min, max
	- 16 i32 bit reverse
	- 64 i32 and, or, xor
	- 16 MSB
	- 16 pop count
	- 64 i8/i16 to i32
	- 16 to/from i64/fp64
	- 16 type conversions

* Render target compression:
	- block size: 4x4 pix [10]
