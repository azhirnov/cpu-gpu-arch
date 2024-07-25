
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
3. [Architecture Whitepaper](https://images.nvidia.com/aem-dam/en-zz/Solutions/design-visualization/technologies/turing-architecture/NVIDIA-Turing-Architecture-Whitepaper.pdf)
4. [Dissecting the NVidia Turing T4 GPU via Microbenchmarking](https://arxiv.org/pdf/1903.07486)
5. [Re-converging control flow on NVIDIA GPUs](https://www.collabora.com/news-and-blog/blog/2024/04/25/re-converging-control-flow-on-nvidia-gpus/)
6. [Implementing DRM format modifiers in NVK](https://www.collabora.com/news-and-blog/news-and-events/implementing-drm-format-modifiers-in-nvk.html)

## Notes

* Independent Thread Scheduling. [1]
	- On recent NVIDIA hardware, the two sides of an `if` may even be executed simultaneously since the two sides act on disjoint sets of invocations. [5]
* Instruction Scheduling: [1]
	- Each Turing SM includes 4 warp-scheduler units. Each scheduler handles a static set of warps and issues to a dedicated set of arithmetic instruction units. Instructions are performed over two cycles, and the schedulers can issue independent instructions every cycle. Dependent instruction issue latency for core FMA math operations is four clock cycles, like Volta, compared to six cycles on Pascal. As a result, execution latencies of core math operations can be hidden by as few as 4 warps per SM, assuming 4-way instruction-level parallelism ILP per warp, or by 16 warps per SM without any instuction-level parallelism.
	- Like Volta, the Turing SM provides 64 FP32 cores, 64 INT32 cores and 8 improved mixed-precision Tensor Cores. Turing has a lower double precision throughput than Volta with only 2 FP64 cores.
* Occupancy: [1]
	- The maximum number of concurrent warps per SM is 32.
	- The register file size is 64k 32-bit registers per SM.
	- The maximum registers per thread is 255.
	- The maximum number of thread blocks per SM is 16.
	- Shared memory capacity per SM is 64KB.
	
* New independent integer datapath that can execute instructions concurrently with the floating-point math datapath. [?]
* The SM memory path has been redesigned to unify shared memory, texture caching, and memory load caching into one unit. [?]
* Each of the four SM processing blocks (also called partitions) had two primary datapaths, but only one of the two could process FP32 operations. The other datapath was limited to integer operations. [?]
* RTX 2080 L1 bandwidth: 116 GB/sec. [?]
* SM bound to one or multiple render target regions with tile size 32x32 (or lower on high register usage)... [?]
* Scheduler operate on threads instead of warps. So when things diverged, the scheduler serialised the divergent components. Do divergent block `A` till completion, then `B`. [?]
* Added Uniform Data Path. This design is intended to accelerate numerical, array-based, computebound workloads that occupy the main datapaths almost completely with floating-point instructions, typically FFMA or HMMA, but also contain a few integer operations, typically updating array indices, loop indices or pointers; or performing array or loop boundary checks. These few integer instructions spoil the instruction mix, and prevent the main datapaths from ingesting a 100% pure stream of FFMA or HMMA. In these circumstances, even a small fraction of integer instructions can hurt the overall arithmetic throughput, lowering it significantly from its theoretical maximum. [4]
* On NVIDIA GPUs, however, a small amount of information about the image is encoded into the page tables. Each combination of format, sample count, and compression node maps to an 8-bit PTE kind. On Turing (RTX 2000-series and GTX 1600-series) and later GPUs, there are three PTE kinds for all color images and two for each depth/stencil format. [6]

* Hardware ray tracing.
* Mesh shaders.
