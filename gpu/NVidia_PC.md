**NVidia GPU Performance Counters**

## References

1. [Kernel Profiling Guide](https://docs.nvidia.com/nsight-compute/ProfilingGuide/#metrics-decoder)
2. [Migrating from Range Profiler to GPU Trace in Nsight Graphics](https://developer.nvidia.com/blog/migrating-from-range-profiler-to-gpu-trace-in-nsight-graphics/)
3. [NVIDIA Nsight Perf SDK](https://developer.nvidia.com/nsight-perf-sdk) - to get access to the performance counters.
4. [NVIDIA Management Library (NVML)](https://developer.nvidia.com/management-library-nvml), [[header](https://github.com/nvpro-samples/nvpro_core/blob/master/third_party/binaries/nvml/nvml.h)]
5. [NSight Systems User Guide](https://docs.nvidia.com/nsight-systems/UserGuide/index.html)
6. [NSight Graphics Advanced Learning](https://docs.nvidia.com/nsight-graphics/AdvancedLearning/index.html)

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
**fma** - Fused Multiply Add/Accumulate. The FMA pipeline processes most FP32 arithmetic (FADD, FMUL, FMAD). It also performs integer multiplication operations (IMUL, IMAD), as well as integer dot products. On Ampere, FMA is a logical pipeline that indicates peak FP32 and FP16x2 performance. It is composed of the FMAHeavy and FMALite physical pipelines.<br/>
**fmaheavy** - Fused Multiply Add/Accumulate Heavy. FMAHeavy performs FP32 arithmetic (FADD, FMUL, FMAD), FP16 arithmetic (HADD2, HMUL2, HFMA2), integer multiplication operations (IMUL, IMAD), and integer dot products.<br/>
**fmalite** - Fused Multiply Add/Accumulate Lite. FMALite performs FP32 arithmetic (FADD, FMUL, FMA) and FP16 arithmetic (HADD2, HMUL2, HFMA2).<br/>
**fp16** - Half-precision floating-point. On Volta, Turing and NVIDIA GA100, the FP16 pipeline performs paired FP16 instructions (FP16x2). It also contains a fast FP32-to-FP16 and FP16-to-FP32 converter. Starting with Ampere chips, this functionality is part of the FMA pipeline.<br/>
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


### NSight System Metrics [5]

**GR Active** - The percentage of cycles the graphics/compute engine is active. The graphics/compute engine is active if there is any work in the graphics pipe or if the compute pipe is processing work.<br/>
**Draw Started** - The ratio of draw calls issued to the graphics pipe to the maximum sustained rate of the graphics pipe. *The percentage will always be very low as the front end can issue draw calls significantly faster than the pipe can execute the draw call. The rendering of this row will be changed to help indicate when draw calls are being issued.*<br/>
**Dispatch Started** - The ratio of compute grid launches (dispatches) to the compute pipe to the maximum sustained rate of the compute pipe. *The percentage will always be very low as the front end can issue grid launches significantly faster than the pipe can execute the draw call. The rendering of this row will be changed to help indicate when grid launches are being issued.*<br/>
**Vertex/Tess/Geometry Warps in Flight** - The ratio of active vertex, geometry, tessellation, and meshlet shader warps resident on the SMs to the maximum number of warps per SM as a percentage.<br/>
**Pixel Warps in Flight** - The ratio of active pixel/fragment shader warps resident on the SMs to the maximum number of warps per SM as a percentage.<br/>
**Compute Warps in Flight** - The ratio of active compute shader warps resident on the SMs to the maximum number of warps per SM as a percentage.<br/>
**Active SM Unused Warp Slots** - The ratio of inactive warp slots on the SMs to the maximum number of warps per SM as a percentage. This is an indication of how many more warps may fit on the SMs if occupancy is not limited by a resource such as max warps of a shader type, shared memory, registers per thread, or thread blocks per SM.<br/>
**Idle SM Unused Warp Slots** - The ratio of inactive warps slots due to idle SMs to the the maximum number of warps per SM as a percentage. This is an indicator that the current workload on the SM is not sufficient to put work on all SMs. This can be due to: 1. CPU starving the GPU. 2. Current work is too small to saturate the GPU. 3. Current work is trailing off but blocking next work.<br/>
**SMs Active** - The ratio of cycles SMs had at least 1 warp in flight (allocated on SM) to the number of cycles as a percentage. A value of 0 indicates all SMs were idle (no warps in flight). A value of 50% can indicate some gradient between all SMs active 50% of the sample period or 50% of SMs active 100% of the sample period.<br/>
**SM Issue** - The ratio of cycles that SM sub-partitions (warp schedulers) issued an instruction to the number of cycles in the sample period as a percentage.<br/>
**Tensor Active** - The ratio of cycles the SM tensor pipes were active issuing tensor instructions to the number of cycles in the sample period as a percentage.<br/>
**Tensor Active / FP16 Active** - The ratio of cycles the SM tensor pipes or FP16x2 pipes were active issuing tensor instructions to the number of cycles in the sample period as a percentage.<br/>
**DRAM Read Bandwidth / VRAM Read Bandwidth** - The ratio of cycles the DRAM interface was active reading data to the elapsed cycles in the same period as a percentage.<br/>
**DRAM Write Bandwidth / VRAM Write Bandwidth** - The ratio of cycles the DRAM interface was active writing data to the elapsed cycles in the same period as a percentage.<br/>
**PCIe Read Throughput** - The ratio of bytes received on the PCIe interface to the maximum number of bytes receivable in the sample period as a percentage. The theoretical value is calculated based upon the PCIe generation and number of lanes. This value includes protocol overhead.<br/>
**PCIe Write Throughput** - The ratio of bytes transmitted on the PCIe interface to the maximum number of bytes receivable in the sample period as a percentage. The theoretical value is calculated based upon the PCIe generation and number of lanes. This value includes protocol overhead.<br/>
**PCIe Read Requests to BAR1 / PCIe Write Requests to BAR1** - BAR1 is a PCI Express (PCIe) interface used to allow the CPU or other devices to directly access GPU memory. The GPU normally transfers memory with its copy engines, which would not show up as BAR1 activity. The GPU drivers on the CPU do a small amount of BAR1 accesses, but heavier traffic is typically coming from other technologies.<br/>
On Linux, technologies like GPU Direct, GPU Direct RDMA, and GPU Direct Storage transfer data across PCIe BAR1. In the case of GPU Direct RDMA, that would be an Ethernet or InfiniBand adapter directly writing to GPU memory.<br/>
On Windows, Direct3D12 resources can also be made accessible directly to the CPU via NVAPI functions to support small writes or reads from GPU buffers, in this case too many BAR1 accesses can indicate a performance issue, like it has been demonstrated in the Optimizing DX12 Resource Uploads to the GPU Using CPU-Visible VRAM technical blog post.<br/>


### NSight Graphics [6]

| Unit | Pipeline Area | Description |
|---|---|---|
| SM | Shader | The Streaming Multiprocessor executes shader code. |
| L1TEX | Memory | The L1TEX unit contains the L1 data cache for the SM, and two parallel pipelines: the LSU or load/store unit, and TEX for texture lookups and filtering. |
| L2 | Memory | The L2 cache serves all units on the GPU, and is a central point of coherency. |
| PD | World Pipe | The Primitive Distributor fetches indices from the index buffer, and sends triangles to the vertex shader. |
| VAF | World Pipe | The Vertex Attribute Fetch unit reads attribute values from memory and sends them to the vertex shader. VAF is part of the Primitive Engine. |
| PES+VPC | World Pipe | The Primitive Engine orchestrates the flow of primitive and attribute data across all world pipe shader stages (Vertex, Tessellation, Geometry). PES contains the stream (transform feedback) unit. The VPC unit performs clip and cull. |
| RASTER | Screen Pipe | The Raster units receives primitives from the world pipe, and outputs pixels (fragments) and samples (coverage masks) for the PROP, Pixel Shader, and ROP to process. |
| PROP | Screen Pipe | The Pre-ROP unit orchestrates the flow of depth and color pixels (fragments) and samples, for final output. PROP enforces the API ordering of pixel shading, depth testing, and color blending. Early-Z and Late-Z modes are handled in PROP. |
| ZROP | Screen Pipe | The Depth Raster Operation unit performs depth tests, stencil tests, and depth/stencil buffer updates. |
| CROP | Screen Pipe | The Color Raster Operation unit performs the final color blend and render-target updates. CROP implements the “advanced blend equation” |

**Warp Can’t Launch Reasons**<br>
When a draw call or compute dispatch enqueues more work than can fit onto the SMs all-at-once, the SMs will report that “additional warps can’t launch”. We can graph these signals over time to determine the limiting factor.

3D warps may not launch due to the following reasons:
* Register Allocation
* Warp Allocation
* Attribute Allocation (ISBEs for VTG, or TRAM for PS)

Compute Shaders Compute warps may not launch due to the following reasons:
* Register Allocation
* Warp Allocation
* CTA Allocation
* Shared Memory Allocation

**SM Throughput**<br/>
SM Throughput reveals the most common computational pipeline limiters in shader code:
* Issue Active : instruction-issue limited
* ALU Pipe : INT other than multiply, bit manipulation, lower frequency FP32 like comparison and min/max.
* FMA Pipe : FP32 add & multiply, integer multiply.
* FP16+Tensor : FP16 instructions which execute a vec2 per instruction, and Tensor ops used by deep learning.
* SFU Pipe : transcendentals (sqrt, rsqrt, sin, cos, log, exp, …)
* Pipes not covered in the SM Throughput: IPA, LSU, TEX, CBU, ADU, RTCORE, UNIFORM.
	- LSU and TEX are never limiters in the SM; see L1 Throughput instead.
	- IPA traffic to TRAM is counted as part of LSU
	- RTCORE has its own Throughput metric
	- UNIFORM and CBU are unaccounted for, but rarely a limiter

**L1 Throughput**

memory & texture requests follow these paths:
* Local/Global Instruction → LSUIN → T-Stage → LSU Data → LSU Writeback → SM
* Shared Memory Instruction → LSUIN → LSU Data → LSU Writeback → RF
	- Includes compute shared memory and 3D shader attributes
	- A few non-memory ops like HLSL Wave Broadcast are counted here
* Texture/Surface Read → TEXIN → T-Stage → TEX Data → Filter → Writeback → SM
	- Includes texture fetches, texture loads, surface loads, and surface atomics
* Surface Write → TEXIN… → T-Stage → LSU Data → Writeback → RF
	- Surface writes cross over to the LSU Data path
* Memory Barriers → LSUIN & TEXIN → … flows through both sides of the pipe
* Primitive Engine attribute writes to (ISBE, TRAM) → LSU Data
* Primitive Engine attribute reads from ISBE → LSU Data
* Local/Global/Texture/Surface→ T-Stage [miss!] → M-Stage → XBAR → L2 → XBAR → M-Stage → Cache Data SRAM

Turing Problem Solving<br/>
Turing reports the following activity:
* Throughput of LSU Data and TEX Data
* Separate counters in LSU Data for Local/Global vs. Shared memory
* Throughput of LSU Writeback, and TEX Filter

By comparing the values of the available throughputs, we can draw the following conclusions:
* All values are equal : most likely request limited
* TEX Data > others : Bandwidth limited; cachelines/instruction > 1
* TEX Filter > others : expensive filtering (Trilinear/Aniso) OR Texture writeback limited due to a wide sampler format (or surface format when sampler disabled)
* LSU Data > others : Possibilities are:
	- Pure bandwidth limited
	- Cachelines per instruction > 1, causing serialization
	- Shared memory bank conflicts, causing serialization
	- Vectored shared memory accesses (64-bit, 128-bit) requiring multi-cycle access
	- Heavy use of SHFL (HLSL Wave Broadcast)
* LSU Writeback > others : limited by coalesced wide loads (64-bit or 128-bit)
	- Note: this implies efficient use of LSU Data
* LSU LG Data or TEX Data close to 100% : implies a high hit-rate
* If Sector Hit Rate is low : may imply latency-bound by L2 or VRAM accesses

Ampere Problem Solving<br/>
Ampere reports the following activity:
* Throughput of LSU Data and TEX Data
* Separate counters in LSU Data per Local/Global, Surface, and Shared memories
* Throughput of LSU Writeback, TEX Filter, and TEX Writeback
* L1TEX Sector Hit-Rate - Reports the collective hit-rate for Local, Global, Texture, Surface - Note that shared memory and 3D attributes do not contribute to the hit-rate

By comparing the values of the available throughputs, we can draw the following conclusions:
* All values are equal : most likely request limited
* TEX Data > others : Bandwidth limited; cachelines/instruction > 1
* TEX Filter > others : expensive filtering (Trilinear/Aniso)
* TEX Writeback > others : limited wide sampler format (or surface format when sampler disabled)
* LSU Data > others : Possibilities are
	- Pure bandwidth limited
	- Cachelines per instruction > 1, causing serialization
	- Shared memory bank conflicts, causing serialization
	- Vectored shared memory accesses (64-bit, 128-bit) requiring multi-cycle access
	- Heavy use of HLSL Wave Broadcast
* LSU Writeback > others : limited by coalesced wide loads (64-bit or 128-bit)
	- Note: this implies efficient use of LSU Data
* LSU LG Data or TEX Data close to 100% : implies a high hit-rate; cross-check against the L1TEX Sector Hit Rate
* If Sector Hit Rate is low : may imply being latency-bound by L2 or VRAM accesses


### Timings

Vulkan adds implicit barriers when used timestamps, it prevent commands to overlap and can not be used to measure small tasks. Only large passes or group of passes can execute without influence of time measurements.


### Stall reasons

[[link](https://docs.nvidia.com/nsight-graphics/UserGuide/#stall-reasons)]<br/>
Stall reasons explain why a warp was unable to issue an instruction. Each stall reason is provoked by a distinct set of conditions or instructions; by eliminating those conditions or transforming code from one set of instructions to another, you can reduce stalls.

* __Barrier__ : Compute warps are waiting for sibling warps at a GroupSync.
	- If the thread group size is 512 threads or greater, consider splitting it into smaller groups. This can increase eligible warps without affecting occupancy, unless shared memory becomes a new occupancy limiter.
	- Review whether all GroupSyncs are really necessary.

* __Dispatch Stall__ : A pipeline interlock prevented instruction dispatch for a selected warp.
	- If dispatch stalls are higher than 5%, please file a bug to NVIDIA with reproducible.

* __Drain__ : Exited warp is waiting to drain memory writes and pixel export.
* __LG Throttle__ : Input FIFO to the LSU pipe for local and global memory instructions is full.
	- Avoid using thread-local memory.
		* Are dynamically indexed arrays declared in local scope?
		* Does the shader have excess register pressure causing spills?
	- Eliminate redundant global memory accesses (UAV accesses).
	- Data organization: pack UAV or SRV data to allow 64-bit or 128-bit accesses in place of multiple 32-bit accesses.

* __Long Scoreboard__ : Waiting on data dependency for local, global, texture, or surface load.
	- Find the instruction or line of code that produces the data being waited upon; that instruction is the culprit.
	- Consider transforming a lookup table into a calculation.
	- Consider transforming global reads in which all threads read the same address into constant buffer reads.
	- If L1 hit rate is low, try to improve spatial locality (coalesced accesses).
	- If VRAM Throughput is high, try to improve spatial locality (coalesced accesses).

* __Math Pipe Throttle__ : A math pipe input FIFO is full (FMA, ALU, FP16+Tensor).
	- This stall reason implies being computationally bound. Use GPU Trace to best determine how to move computation to a different execution unit.

* __Membar__ : Waiting for a memory barrier to return.
	- Memory barriers are issued by GroupMemoryBarrier, DeviceMemoryBarrier, AllMemoryBarrier, and their GroupSync variants.
	- Review whether the specified scope of each barrier in the shader is really needed. Group-level barriers resolve much faster than Device-level.
	- Review whether a memory barrier is needed at all. A compute shader where each thread writes to a unique UAV location does not require a memory barrier.

* __MIO Throttle__ : The input FIFO to MIO is full.
	- May be triggered by local, global, shared, attribute, IPA, indexed constant loads (LDC), and decoupled math.

* __Misc__ : A stall reason not covered elsewhere.
* __Not Selected__ : Warp was eligible but not selected, because another warp was.
	- High “not selected” could indicate an opportunity to increase register or shared memory usage (lowering occupancy) without impacting performance. Opening the doors to greater shader complexity or improved quality.

* __Selected__ : Warp issued an instruction. Technically not a stall.
* __Short Scoreboard__ : Waiting for short latency MIO or RTCORE data dependency.
	- Includes 3D attribute load/store, pixel attribute interpolation, compute shared memory load/store, indexed constant loads, transcendentals (rcp, rsqrt, …) through the SFU pipe (aka XU pipe), VOTE, and a few other infrequent instructions.

* __TEX Throttle__ : The TEXIN input FIFO is full.
	- Try issuing fewer texture fetches, surface loads, surface stores, or decoupled math operations.
	- Check whether the shader is using decoupled math (usually to be avoided).
	- Consider converting texture lookups or surface loads into global memory lookups (UAVs). Texture can accept 4 threads’ requests per cycle, whereas global accepts 32 threads.

* __Wait__ : Waiting for coupled math data dependency (FMA, ALU, FP16+Tensor).


[ref](https://chipsandcheese.com/p/starfield-on-the-rx-6900-xt-rx-7600-and-rtx-2060-mobile)
TODO
