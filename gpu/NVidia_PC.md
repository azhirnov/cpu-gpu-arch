**NVidia GPU Performance Counters**

## References

1. [Kernel Profiling Guide](https://docs.nvidia.com/nsight-compute/ProfilingGuide/#metrics-decoder)
2. [Migrating from Range Profiler to GPU Trace in Nsight Graphics](https://developer.nvidia.com/blog/migrating-from-range-profiler-to-gpu-trace-in-nsight-graphics/)
3. [NVIDIA Nsight Perf SDK](https://developer.nvidia.com/nsight-perf-sdk) - to get access to the performance counters.
4. [NVIDIA Management Library (NVML)](https://developer.nvidia.com/management-library-nvml), [[header](https://github.com/nvpro-samples/nvpro_core/blob/master/third_party/binaries/nvml/nvml.h)]

## Notes

### Units
**dram** - Device (main) memory, where the GPUs global and local memory resides.<br/>
**fbpa** - The FrameBuffer Partition is a memory controller which sits between the level 2 cache (LTC) and the DRAM. The number of FBPAs varies across GPUs.<br/>
**fe** - The Frontend unit is responsible for the overall flow of workloads sent by the driver. FE also facilitates a number of synchronization operations.<br/>
**gpc** - The General Processing Cluster contains SM, Texture and L1 in the form of TPC(s). It is replicated several times across a chip.<br/>
**gpu** - The entire Graphics Processing Unit.<br/>
**gr** - Graphics Engine is responsible for all 2D and 3D graphics, compute work, and synchronous graphics copying work.<br/>
**idc** - The InDexed Constant Cache is a subunit of the SM responsible for caching constants that are indexed with a register.<br/>
**l1tex** - The Level 1 (L1)/Texture Cache is located within the GPC. It can be used as directed-mapped shared memory and/or store global, local and texture data in its cache portion. l1tex__t refers to its Tag stage. l1tex__m refers to its Miss stage. l1tex__d refers to its Data stage.<br/>
**ltc** - The Level 2 cache.<br/>
**ltcfabric** - The LTC fabric is the communication fabric for the L2 cache partitions.<br/>
**lts** - A Level 2 (L2) Cache Slice is a sub-partition of the Level 2 cache. lts__t refers to its Tag stage. lts__m refers to its Miss stage. lts__d refers to its Data stage.<br/>
**mcc** - Memory controller channel of MSS. The Memory Subsystem (MSS) provides access to local DRAM, SysRAM, and provides a SyncPoint Interface for interprocessor signaling. MCC includes the row sorter/arbiter and DRAM controllers.<br/>
**pm** - Performance monitor.<br/>
**sm** - The Streaming Multiprocessor handles execution of a kernel as groups of 32 threads, called warps. Warps are further grouped into cooperative thread arrays (CTA), called blocks in CUDA. All warps of a CTA execute on the same SM. CTAs share various resources across their threads, e.g. the shared memory.<br/>
**smsp** - Each SM is partitioned into four processing blocks, called SM sub partitions. The SM sub partitions are the primary processing elements on the SM. A sub partition manages a fixed size pool of warps.<br/>
**sys** - Logical grouping of several units.<br/>
**tpc** - Thread Processing Clusters are units in the GPC. They contain one or more SM, Texture and L1 units, the Instruction Cache (ICC) and the Indexed Constant Cache (IDC).<br/>
**TLB** -  Translation Look-aside Buffer<br/>

### Subunits
**aperture_device** - Memory interface to local device memory (dram)<br/>
**aperture_peer** - Memory interface to remote device memory<br/>
**aperture_sysmem** - Memory interface to system memory<br/>
**global** - Global memory is a 49-bit virtual address space that is mapped to physical memory on the device, pinned system memory, or peer memory. Global memory is visible to all threads in the GPU. Global memory is accessed through the SM L1 and GPU L2.<br/>
**lg** - Local/Global memory<br/>
**local** - Local memory is private storage for an executing thread and is not visible outside of that thread. It is intended for thread-local data like thread stacks and register spills. Local memory has the same latency as global memory.<br/>
**lsu** - Load/Store unit<br/>
**lsuin** - Load/Store input<br/>
**mio** - Memory input/output<br/>
**mioc** - Memory input/output control<br/>
**shared** - Shared memory is located on chip, so it has much higher bandwidth and much lower latency than either local or global memory. Shared memory can be shared across a compute CTA.<br/>
**surface** - Surface memory<br/>
**texin** - TEXIN<br/>
**texture** - Texture memory<br/>
**xbar** - The Crossbar (XBAR) is responsible for carrying packets from a given source unit to a specific destination unit.<br/>

### Pipelines
**adu** - Address Divergence Unit. The ADU is responsible for address divergence handling for branches/jumps. It also provides support for constant loads and block-level barrier instructions.<br/>
**alu** - Arithmetic Logic Unit. The ALU is responsible for execution of most bit manipulation and logic instructions. It also executes integer instructions, excluding IMAD and IMUL. On NVIDIA Ampere architecture chips, the ALU pipeline performs fast FP32-to-FP16 conversion.<br/>
**cbu** - Convergence Barrier Unit. The CBU is responsible for warp-level convergence, barrier, and branch instructions.<br/>
**fma** - Fused Multiply Add/Accumulate. The FMA pipeline processes most FP32 arithmetic (FADD, FMUL, FMAD). It also performs integer multiplication operations (IMUL, IMAD), as well as integer dot products. On GA10x, FMA is a logical pipeline that indicates peak FP32 and FP16x2 performance. It is composed of the FMAHeavy and FMALite physical pipelines.<br/>
**fmaheavy** - Fused Multiply Add/Accumulate Heavy. FMAHeavy performs FP32 arithmetic (FADD, FMUL, FMAD), FP16 arithmetic (HADD2, HMUL2, HFMA2), integer multiplication operations (IMUL, IMAD), and integer dot products.<br/>
**fmalite** - Fused Multiply Add/Accumulate Lite. FMALite performs FP32 arithmetic (FADD, FMUL, FMA) and FP16 arithmetic (HADD2, HMUL2, HFMA2).<br/>
**fp16** - Half-precision floating-point. On Volta, Turing and NVIDIA GA100, the FP16 pipeline performs paired FP16 instructions (FP16x2). It also contains a fast FP32-to-FP16 and FP16-to-FP32 converter. Starting with GA10x chips, this functionality is part of the FMA pipeline.<br/>
**fp64** - Double-precision floating-point. The implementation of FP64 varies greatly per chip.<br/>
**lsu** - Load Store Unit. The LSU pipeline issues load, store, atomic, and reduction instructions to the L1TEX unit for global, local, and shared memory. It also issues special register reads (S2R), shuffles, and CTA-level arrive/wait barrier instructions to the L1TEX unit.<br/>
**tex** - Texture Unit. The SM texture pipeline forwards texture and surface instructions to the L1TEX unit’s TEXIN stage. On GPUs where FP64 or Tensor pipelines are decoupled, the texture pipeline forwards those types of instructions, too.<br/>
**tma** - Tensor Memory Access Unit. Provides efficient data transfer mechanisms between global and shared memories with the ability to understand and traverse multidimensional data layouts.<br/>
**uniform** - Uniform Data Path (UDP). This scalar unit executes instructions where all threads use the same input and generate the same output.<br/>
**xu** - Transcendental and Data Type Conversion Unit. The XU pipeline is responsible for special functions such as sin, cos, and reciprocal square root. It is also responsible for int-to-float, and float-to-int type conversions.<br/>

### Quantities
**instruction** - An assembly (SASS) instruction. Each executed instruction may generate zero or more requests.<br/>
**request** - A command into a HW unit to perform some action, e.g. load data from some memory location. Each request accesses one or more sectors.<br/>
**sector** - Aligned 32 byte-chunk of memory in a cache line or device memory. An L1 or L2 cache line is four sectors, i.e. 128 bytes. Sector accesses are classified as hits if the tag is present and the sector-data is present within the cache line. Tag-misses and tag-hit-data-misses are all classified as misses.<br/>
**tag** - Unique key to a cache line. A request may look up multiple tags, if the thread addresses do not all fall within a single cache line-aligned region. The L1 and L2 both have 128 byte cache lines. Tag accesses may be classified as hits or misses.<br/>
**wavefront** - Unique “work package” generated at the end of the processing stage for requests. All work items of a wavefront are processed in parallel, while work items of different wavefronts are serialized and processed on different cycles. At least one wavefront is generated for each request.<br/>

