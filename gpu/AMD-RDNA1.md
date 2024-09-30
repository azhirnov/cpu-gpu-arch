1st generation of AMD RDNA (Radeon DNA) architecture, code name: Navi.<br/>
10 generation of AMD GFX IP.

## Examples

* RX 5300 - 5700

## References

1. [Architecture](https://gpuopen.com/wp-content/uploads/2019/08/RDNA_Architecture_public.pdf)
2. [Whitepaper](https://www.amd.com/system/files/documents/rdna-whitepaper.pdf)
3. [Instruction Set Architecture](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/rdna-shader-instruction-set-architecture.pdf), [[backup](../pdf/AMD_rdna_isa.pdf)]
4. [Optimization](https://gpuopen.com/wp-content/uploads/slides/GPUOpen_Let%E2%80%99sBuild2020_Optimizing%20for%20the%20Radeon%20RDNA%20Architecture.pdf)
5. [(video) Optimizing for the Radeon RDNA Architecture](https://www.youtube.com/watch?v=7eEKLUhoTQs)
6. [AMD Announces Radeon RX 5700 XT & RX 5700](https://www.anandtech.com/show/14528/amd-announces-radeon-rx-5700-xt-rx-5700-series)
7. [Vulkan features for RX 5700 XT](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD%20Radeon%20RX%205700%20XT%20(RADV%20NAVI10))

## Notes

* Supports DCC when writing to image in compute shader.

* The RDNA processor consists of: [3]
	- A scalar ALU, which operates on one value per wavefront (common to all work items).
	- A vector ALU, which operates on unique values per work-item.
	- Local data storage, which allows work-items within a workgroup to communicate and share data.
	- Scalar memory, which can transfer data between SGPRs and memory through a cache.
	- Vector memory, which can transfer data between VGPRs and memory, including sampling texture maps.
* Every wavefront is allocated a fixed number of SGPRs: [3]
	- 106 normal SGPRs
	- VCCh and VCCl (stored in SGPRs 106 and 107)
	- 16 Trap-temporary SGPRs, meant for use by the trap handler

* All float-16 math uses FMA instead of MAD. [3]
* Transcendental instructions (rcp/rsqrt/sqrt/log/exp/sin/cos) are 1/4 rate. Non-transcendental instructions can execute in parallel. [1]
	- example: FMA executed in parallel with SFU.

* 1 cycle instruction issue. Instruction level parallelism. [1]
	- example: 1 FFMA took 4 cycles, but 4 FFMA took 7 cycles if hasn't dependencies between them.
	- 3 piles can run in parallel: fp32/fp16/i32 FMA, fp64/i64 FMA, TU (Transcendental unit).

* Wave32<br/>
	- Previous generations used a wavefront size of 64 threads (work items). This generation supports both wavefront sizes of 32 and 64 threads. [3]
	- Wave64 via dual-issue. [1]
	- Compute and vertex shaders usually as Wave32, pixel shaders usually as Wave64. [1]
* Workgroup Processors [3]<br/>
	Previously the shader hardware was grouped into "compute units" ("CUs") which contained ALU, LDS and memory access. Now the "workgroup processor" ("WGP") replaces the compute unit as the basic unit of computing. This allows significantly more compute power and memory bandwidth to be directed at a single workgroup.

* WGP requires 4*32 = 128 threads to be able to reach 100% ALU utilization [1]
	- Only achieved with high instruction level parallelism (ILP)
	- Graphics workloads often have 3 independent streams (RGB / XYZ)
	- 256 threads / WGP often reach >90% ALU utilization in practice (in games)

* Prefer coalesced stores of at least 256B per wave for full efficiency. [1]
	- otherwise it will be decompression -> update -> compression -> L2 loop.
	- Fully overwrite 256B blocks on store.

* Non atomic stores are now true “fire and forget”. [1]

* Texture Unit has low latency path for Loads. [1]
	- don't combine image load with texture sampling.
	- replace all sampling by image load.
	- Separate Loads and Samples if feasible.

* Asynchronous Compute Tunneling: [1]
	- RDNA architecture can completely suspend execution of shaders, freeing up all compute units for a high-priority task.

* The primitive units assemble triangles from vertices and are also responsible for fixed-function tessellation. Each primitive unit has been enhanced and supports culling up to two primitives per clock. One primitive per clock is output to the rasterizer. The work distribution algorithm in the command processor has also been tuned to distribute vertices and tessellated polygons more evenly between the different shader arrays, boosting throughput for geometry. [2]
* The rasterizer in each shader engine performs the mapping from the geometry-centric stages of the graphics pipeline to the pixel-centric stages. Each rasterizer can process one triangle, test for coverage, and emit up to sixteen pixels per clock. As with other fixed-function hardware, the screen is subdivided and each portion is distributed to one rasterizer. [2]
* The final fixed-function graphics stage is the Render Backend (RB), which performs depth, stencil, and alpha tests and blends pixels for anti-aliasing. Each of the RBs in the shader array can test, sample, and blend pixels at a rate of four output pixels per clock. The RBs primarily access data through the graphics L1 cache, which reduces the pressure on the L2 cache and saves power by moving less data. [2]

* Instruction cache can deliver 32B (typically 2-4 instructions) every clock to each of the SIMDs. [2]
* Each SIMD has a separate instruction pointer and a 20-entry wavefront controller, for a total of 80 wavefronts per WGP. Wavefronts can be from a different work-group or kernel, although the WGP maintains 32 work-groups simultaneously. [2]
* Front-end can issue four instructions every cycle to every SIMD, which include a combination of vector, scalar, and memory pipeline. The scalar pipelines are typically used for control flow and some address calculation. [2]
* The scalar ALU accesses the scalar register file and performs basic 64-bit arithmetic operations. The scalar ALU is used for a variety of control purposes, such as calculating values that will be broadcast across an entire wavefront, managing predicates for the wavefront, and computing branch targets. In addition, the scalar ALU is used for address calculation when reading or writing data in the scalar data cache. [2]
* When a wavefront is initiated, the scalar register file can preload up to 32 user registers to pass constants, avoiding explicit load instructions and reducing the launch time for wavefronts. (descriptor sets, push constants ?) [2]

* Every SIMD has a 32-wide request bus that can transmit an address for each work-item in a wavefront to the memory hierarchy; for store operations, the request bus will instead provide 32x4B of write data. The requested data is transmitted back via a 32-wide return bus and can be provided directly to the ALUs or the vGPRs. The request and return bus generally work with 128-byte cache lines and fan out to the explicitly addressed LDS, cached memory and the texturing units. For efficiency, pairs of SIMDs share a request and return bus, although an individual SIMD can actually receive two 128-byte cache lines per clock – one from the LDS and the other from the L0 cache. [2]

* Each LDS bank includes an ALU that performs atomic operations including FP min and max. [2]
* The LDS includes a crossbar to move data between wavefront lanes and banks and can also broadcast or replicate data. Typically, all accesses from a wavefront will complete in a single cycle; however, the hardware automatically detects conflicts and will serialize multiple accesses to a single bank of the LDS. [2]

* VALU:
	- The individual lanes have been redesigned for fused multiply-accumulate (FMA) operations, which improves the accuracy of computation and reduces power consumption compared to the previous generation’s multiply-add units. [2]
	- Mixed precision FMA that computes 16-bit multiplication and accumulates into a 32-bit result to avoid losing any precision for integer or FP data. [2]
	- Full rate fp32 FMA, mixed precision fp32/fp16 FMA. [2]
	- Full rate i24/i32 MAD. [2]
	- 2x rate for fp16 FMA and i16 MAD. [2]

* Image and buffer loads are much faster that texture sampling. [2]
* Graphics textures are stored in the L0 vector cache, and accessed similarly to data. However, the results are first passed to the texture mapping unit, which can perform filtering for up to eight texture addresses per clock. [2]
* The export unit in each WGP can send up to 4 vGPRs to the primitive units, RBs, or the GDS. [2]

* SALU: [3]
	- Special codes for constants: 0.5, 1.0, 2.0, 4.0, 1/2Pi
	- Ops: Add, Sub, Min, Max, Abs, AbsDiff, Mul (only signed i32), And, Or, Xor, Shift, BitCount, ...
	- Can set round mode and denorm mode.
	- Round Modes:
		* 0 = nearest even;
		* 1 = +infinity;
		* 2 = -infinity, 3= toward zero.
	- Denormal modes:
		* 0 = Flush input and output denorms.
		* 1 = Allow input denorms, flush output denorms.
		* 2 = Flush input denorms, allow output denorms.
		* 3 = Allow input and output denorms.

* VALU: [3]
	- Special codes for integer inline constants: 1..64, -1..-16
	- Special codes for constants: 0.5, 1.0, 2.0, 4.0, 1/2Pi
	- Optionally, the result can be clamped (CLAMP field) to the range [0.0, +1.0]. (zero overhead clamp?)
	- Some instructions:
		* V_FMA_{F16, F32, F64}, V_MAD_LEGACY_F32
		* V_MAD_{I16,U16,F32}, V_MAD_{U64_U32,I64_I32}, V_MAD_I32_I16, V_MAD_I32_I24
		* V_MAX3_{F16,I16,U16}, V_MAX3_{F32,I32,U32}, V_MED3_, V_MIN3_
		* V_LERP_U8
		* V_MAD_MIX_F32 - perform a single MAD operation on a mixture of 16- and 32-bit inputs.
	- Packed instructions:
		* V_PK_MAD_I16, V_PK_MIN_I16, V_PK_ADD_I16, ...
		* V_PK_MUL_F16, V_PK_MIN_F16, V_PK_FMA_F16, ...
	-  Data Parallel Processing (DPP)
		* DPP8 allows arbitrary swizzling between groups of 8 lanes
		* DPP16 allows a set of predefined swizzles between groups of 16 lanes
		* These operations take the SP multiple instruction cycles (at least 8 times what an ADD_F32 takes).


## Features

* Next Generation Geometry (NGG) - primitive shader.
* Asynchronous Compute Tunneling.


## Specs

* LDS
	- 128 KB per workgroup processor
	- Read / write / atomic throughput of up to 32 dwords per cycle. [1]

* Cache: [1][2]
	- Instruction Cache: 32KB per WGP, line: 64B, Read-only, 4-way set-associative, 4 banks of 128 cache lines
	- Scalar Cache: 16KB per WGP, line: 64B, Read-only, 4-way associative, 2 banks of 128 cache lines.
	- L0 Cache: 2x 16KB per WGP, line: 128B, Read-only, 4-way set associative, LRU.
	- L1 Cache: 128KB per shader array, line: 128B, Read-only, s 16-way set associative, 4 banks.
	- L2 Cache: 4MB, line: 128B, Read/Write, 16-way set-associative.
	- Independent loads and stores
	- L1 - L2 bus: 4x 64B per clock
	- L2 - VMEM bus: 16x 32B per clock
	- L0 - L1 bus: 128B/clock read, 64B/clock write.
	- Instruction Cache - L1 bus: 32B/clock read.
	- Scalar Cache - L1 bus:32B/clock read/write.

* Compressed read from: WGP (storage image), Render Backend (texture sampling), Present Queue. [1]
* Compressed write from: WGP (storage image), Render Backend (render target). [1]

* Texture Unit: [1]
	- Load addressing: 32 addresses/clk
	- Load data processing: 32 dwords/clk
	- Store addressing: 32 addresses/2 clk
	- Store data processing: 32 dwords/2 clk
	- Filtering 64bit texels: 4 components/clk

* WGP contains: [1][2]
	- 4x SIMD32 (VALU + SALU)
	- 32KB Instruction Cache
	- 16KB Scalar Cache
	- 2x 16KB L0 Cache
	- 2x Local Data Share (LDS)
	- 2x texture addresser
	- 2x texture data

* SIMD contains: [2]
	- 10KB scalar register file, with 128 entries for each of the 20 wavefronts.
	- Branch pipe. It handles conditional branches and interrupts.
	- 32x ALU (fp32 FMA, i32 MAD, 2x fp16 FMA, 2x i16 MAD)
	- 8x Transcendental unit (rcp/rsqrt/sqrt/log/exp/sin/cos).
	- 2-16x Double Precision unit.
	- Scalar cache can deliver 16B per clock to the scalar register file in each SIMD.
	- 1024x VGPRs
	- 256 FLOPs/cy

* vGPR contains: [2]
	- 32 lanes 32-bits wide registers.
	- Natively support packed data including two half-precision (16-bit) FP values, four 8-bit integers, or eight 4-bit integers.

* LDS: [2]
	- 2x 64KB arrays with 32 banks per array. Each bank includes 512 entries that are 32-bits wide and can sustain a read and write every cycle.

* Radeon RX 5700 XT: [2]
	- Triangles rasterized ∆/s: 7620
	- Triangle cull rate ∆/s: 15240
	- Pixel Fill Rate GPixels/s: 121.92
	- CUs: 40
	- FP32 Performance TFLOP/s: 9.75
	- INT8 Texturing GTexels/s: 304.8
	- FP16 Texturing GTexels/s: 304.8
	- L0 Bandwidth TB/s: 9.76
	- L1 Bandwidth TB/s: 3.90
	- L2 Bandwidth TB/s: 1.95
	- Total Cache Bandwidth TB/s: 15.61
	- Total Cache Bandwidth/FLOP: 1.6
