
## References

* [libGPUCounters](https://github.com/ARM-software/libGPUCounters) - to get access to the performance counters.
* [5th Gen Performance Counters](https://developer.arm.com/documentation/108081/0104), [[backup](../pdf/arm_immortalis-g720_and_arm_mali-g720_performance_counters_reference_guide_108081_0103_en.pdf)]
* [Valhall (4th Gen) Performance Counters Reference Guide](https://developer.arm.com/documentation/107775/0106), [[backup](../pdf/arm_mali-g615_performance_counters_reference_guide_107775_0105_en.pdf)]
* [Bifrost (3rd Gen) Performance Counters Reference Guide](https://developer.arm.com/documentation/102697/latest/), [[backup](../pdf/arm_mali-g76_performance_counters_reference_guide_102697_0106_en.pdf)]
* [Midgard (2nd Gen) Performance Counters Reference Guide](https://developer.arm.com/documentation/108059/latest/), [[backup](../pdf/arm_mali-t820_and_arm_mali-t830_performance_counters_reference_guide_108059_0102_en.pdf)]
* [Mesa driver details](https://docs.mesa3d.org/drivers/panfrost.html)

## Notes

**ALU** - arithmetic unit in the execution engine, contains pipes: **FMA**, **CVT**, **SFU**, **MSG**.<br/>
**AXI bus**, **ExtBus** - interface between L2 slice and external memory (RAM).<br/>
**Binning phase** - includes vertex position shading, culling, and primitive binning.<br/>
**Back-end** - queue which placed after Execution core, only fragment queue has backend.<br/>
**JM** - frontend type before Valhall gen2<br/>
**CSF** - Command Stream Front-end, added to Valhall gen3.<br/>
**CS0** - ?<br/>
**CEU** - ?<br/>
**DVFS** - Dynamic Voltage and Frequency Scaling.<br/>
**Diverged instructions** - in 'false' branch.<br/>
**E/L ZS** - early/late depth stencil test.<br/>
**EC** - Execution Core.<br/>
**FPK** - Forward Pixel Kill.<br/>
**Front-end** - queue which placed before Execution core, can be NonFragFrontend / FragFrontend.<br/>
**Fragment Task** - region of 32x32 for Valhall, 64x64 for 5th Gen.<br/>
**IRQ** - Interrupt Queue.<br/>
**Job** - GPU command, executed on Job Manager, it tracks inter-job dependencies, distributes jobs across shader cores, splits jobs into per-core tasks.<br/>
**Load/store unit (LS, LSU)** - used for general-purpose memory accesses, and includes vertex attribute access, buffer access, work group shared memory access, and stack access, also implements imageLoad/Store and atomic access functionality. (The load/store pipeline handles all non-texture memory access, including buffer access, image access, and atomic operations.)<br/>
**MCU** - GPU command stream microcontroller.<br/>
**MMU** - Memory management unit.<br/>
**Main phase** - includes any deferred vertex processing and all fragment shading.<br/>
**PE** - Processing Engine.<br/>
**Quad** - 2x2 pixels<br/>
**RTU** - Ray Tracing Unit.<br/>
**SCBus** - Bus between L2 cache and LSU, texture unit, front-end unit, tile unit.<br/>
**Task** - part of job, executed on core.<br/>
**Tiler** - responsible for coordinating geometry processing and providing the fixed-function tiling needed for the tile-based rendering pipeline. It can run in parallel to vertex shading and fragment shading.<br/>
**TLB** -  Translation Look-aside Buffer ?<br/>
**Varying unit (V)** - The varying pipeline is a dedicated pipeline which implements the varying interpolator.<br/>
**Vertex position shading** - part of vertex shader which outputs only vertex position.<br/>
**Warp** - group of 4-16 threads.<br/>


Execution core / Processing unit / ALU:<br/>
- **FMA pipe** - Arithmetic fused multiply accumulate unit (FMA). The FMA pipelines are the main arithmetic pipelines, implementing the floating-point multipliers that are widely used in shader code. Each FMA pipeline implements a 16-wide warp, and can issue a single 32-bit operation or two 16-bit operations per thread and per clock cycle. Most programs that are arithmetic-limited are limited by the performance of the FMA pipeline.<br/>
- **CVT pipe** - Arithmetic convert unit (CVT). The CVT pipelines implement simple operations, such as format conversion and integer addition. Each CVT pipeline implements a 16-wide warp, and can issue a single 32-bit operation or two 16-bit operations per thread and per clock cycle.<br/>
- **SFU pipe** - Arithmetic special functions unit (SFU). The SFU pipelines implement a special functions unit for computation of complex functions such as reciprocals and transcendental functions. Each SFU pipeline implements a 4-wide issue path, executing a 16-wide warp over 4 clock cycles.<br/>
- **MSG pipe** - memory access ?<br/>


## Mali G57

<details>

```
GPU family:       Valhall
Product Id:       G57-2
AXI bus width:    256 bits
Num cores:        2
Exec engines:     1
L2 slices * size: 512 Kb (1 * 512 Kb)
Tile size:        16x16 px
Warp width:       16 threads
```

| counter |description | units |  comments |
|---|---|--------|--------|
| GPUCyPerPix | Average cycles per pixel | cycles |
| GPUPix | Pixels | pixels |
| SCBusTileWrBy | Tile unit write bytes | bytes |
| SCBusLSWrByPerWr | Load/store unit bytes written to L2 per access cycle | bytes |
| SCBusLSWrBy | Load/store unit write bytes | bytes |
| SCBusLSWrBt | Load/store unit write beats to L2 memory system | beats |
| SCBusTexExtRdByPerRd | Texture unit bytes read from external memory per texture cycle | bytes |
| SCBusTexExtRdBy | Texture unit read bytes from external memory | bytes |
| SCBusTexL2RdByPerRd | Texture unit bytes read from L2 per texture cycle | bytes |
| SCBusTexL2RdBy | Texture unit read bytes from L2 cache | bytes |
| SCBusLSExtRdByPerRd | Load/store unit bytes read from external memory per access cycle | bytes |
| SCBusLSExtRdBy | Load/store unit read bytes from external memory | bytes |
| SCBusLSL2RdByPerRd | Load/store unit bytes read from L2 per access cycle | bytes |
| SCBusLSL2RdBy | Load/store unit read bytes from L2 cache | bytes |
| SCBusFFEExtRdBy | Front-end unit read bytes from external memory | bytes |
| SCBusFFEL2RdBy | Front-end unit read bytes from L2 cache | bytes |
| VarUtil | Varying unit utilization | percent |
| VarIssueCy | Varying unit issue cycles | cycles |
| Var16IssueCy | 16-bit interpolation active cycles | cycles |
| Var32IssueCy | 32-bit interpolation active cycles | cycles |
| LSUtil | Load/store unit utilization | percent |
| LSIssueCy | Load/store unit issue cycles | cycles |
| LSWrCy | Load/store unit write issues | cycles |
| LSRdCy | Load/store unit read issues | cycles |
| TexFiltFullRate | Texture full speed filtering percentage | percent |
| TexOutBusUtil | Texture output bus utilization | percent |
| TexInBusUtil | Texture input bus utilization | percent |
| TexIssueCy | Texture unit issue cycles | cycles |
| TexQuads | Texture quads | quads |
| TexUtil | Texture unit utilization | percent |
| TexCPI | Texture filtering cycles per instruction | cycles |
| TexSample | Texture samples | requests |
| ALUUtil | Arithmetic unit utilization | percent |
| EngSWBlendRate | Shader blend percentage | percent |
| EngDivergedInstrRate | Warp divergence percentage | percent |
| EngArithInstr | Arithmetic instruction issue cycles | instructions |
| EngSFUPipeUtil | SFU pipe utilization | percent |
| EngCVTPipeUtil | CVT pipe utilization | percent |
| EngFMAPipeUtil | FMA pipe utilization | percent |
| CoreFullWarpRate | Full warp percentage | percent |
| CoreAllRegsWarpRate | All registers warp percentage | percent |
| FragThread | Fragment threads | threads |
| NonFragThread | Non-fragment threads | threads |
| CoreUtil | Execution core utilization | percent |
| FragTileKillRate | Unchanged tile kill percentage | percent |
| FragOverdraw | Fragments per pixel | threads | Number of fragments shaded per output pixel. GPU processing cost per pixel accumulates with the layer count. High overdraw can build up to a significant processing cost, especially when rendering to a high-resolution framebuffer. Minimize overdraw by rendering opaque objects front-to-back and minimizing use of blended transparent layers. *Note: 32 primitives per pixel equal to 2.0* |
| FragRastPartQdRate | Partial coverage percentage | percent |
| FragFPKBUtil | Fragment FPK buffer utilization | percent |
| TilerUtil | Tiler utilization | percent |
| ExtBusWrOTQ4 | Output external outstanding writes 75-100% | transactions |
| ExtBusRdOTQ4 | Output external outstanding reads 75-100% | transactions |
| ExtBusRdLat384 | Output external read latency 384+ cycles | beats |
| ExtBusWrStallRate | Output external write stall percentage | percent |
| ExtBusRdStallRate | Output external read stall percentage | percent |
| ExtBusWrBy | Output external write bytes | bytes |
| ExtBusRdBy | Output external read bytes | bytes |
| L2CacheWrMissRate | L2 cache write miss percentage | percent |
| L2CacheRdMissRate | L2 cache read miss percentage | percent |
| NonFragQueueUtil | Non-fragment queue utilization | percent |
| FragQueueUtil | Fragment queue utilization | percent |
| GPUIRQUtil | Interrupt pending utilization | percent |
| TilerVarShadStallCy | Tiler varying shading stall cycles | cycles |
| GeomVarShadTask | Tiler varying shading requests | requests |
| TilerVarCacheMiss | Varying cache misses | requests |
| TilerVarCacheHit | Varying cache hits | requests |
| TilerPosCacheMiss | Position cache miss requests | requests |
| TilerPosCacheHit | Position cache hit requests | requests |
| TilerPosShadFIFOFullCy | Tiler position FIFO full cycles | cycles |
| TilerPosShadStallCy | Tiler position shading stall cycles | cycles |
| GeomPosShadTask | Tiler position shading requests | requests |
| TilerRdBt | Output internal read beats | beats |
| GeomSampleCullPrim | Sample test culled primitives | primitives |
| GeomZPlaneCullPrim | Z plane culled primitives | primitives |
| GeomFaceXYPlaneCullPrim | Facing or XY plane test culled primitives | primitives |
| GeomVisiblePrim | Visible primitives | primitives |
| GeomBackFacePrim | Visible back-facing primitives | primitives |
| GeomPointPrim | Point primitives | primitives |
| GeomTrianglePrim | Triangle primitives | primitives |
| TilerActiveCy | Tiler active cycles | cycles |
| SCBusLSWBWrBt | Load/store unit write-back write beats | beats |
| SCBusTileWrBt | Tile unit write beats to L2 memory system | beats |
| SCBusLSOtherWrBt | Load/store unit other write beats | beats |
| SCBusOtherL2RdBt | Miscellaneous read beats from L2 cache | beats |
| SCBusTexExtRdBt | Texture unit read beats from external memory | beats |
| SCBusTexL2RdBt | Texture unit read beats from L2 cache | beats |
| SCBusLSExtRdBt | Load/store unit read beats from external memory | beats |
| SCBusLSL2RdBt | Load/store unit read beats from L2 cache | beats |
| SCBusFFEExtRdBt | Fragment front-end read beats from external memory | beats |
| SCBusFFEL2RdBt | Fragment front-end read beats from L2 cache | beats |
| AttrInstr | Attribute instructions | instructions |
| Var16IssueSlot | 16-bit interpolation slots | issues |
| Var32IssueSlot | 32-bit interpolation slots | issues |
| VarInstr | Varying unit instructions | requests |
| LSAtomic | Load/store unit atomic issues | cycles |
| LSPartWr | Load/store unit partial write issues | cycles |
| LSFullWr | Load/store unit full write issues | cycles |
| LSPartRd | Load/store unit partial read issues | cycles |
| LSFullRd | Load/store unit full read issues | cycles |
| FragLZSKillRate | Late ZS killed thread percentage | percent |
| TexOutBt | Texture message write beats | beats |
| FragLZSTestRate | Late ZS tested thread percentage | percent |
| TexOutMsg | Texture messages | issues |
| FragEZSKillRate | Early ZS killed quad percentage | percent |
| TexFullTriFiltCy | Texture filtering cycles using full trilinear | cycles |
| FragEZSTestRate | Early ZS tested quad percentage | percent |
| TexFullBiFiltCy | Texture filtering cycles using full bilinear | cycles |
| TexFiltIssueCy | Texture filtering cycles | cycles |
| TexFiltStallCy | Texture filtering stall cycles | cycles |
| FragThroughputCy | Average cycles per fragment thread | cycles |
| TexDataFetchStallCy | Texture fetch stall cycles | cycles |
| FragUtil | Fragment utilization | percent |
| TexDescStallCy | Texture descriptor stall cycles | cycles |
| NonFragThroughputCy | Average cycles per non-fragment thread | cycles |
| TexInBt | Texture message read beats | beats |
| NonFragUtil | Non-fragment utilization | percent |
| EngSWBlendInstr | Blend shader instructions | instructions |
| EngStarveCy | Execution engine starvation cycles | cycles |
| GeomZPlaneCullRate | Z plane test cull percentage | percent |
| EngICacheMiss | Instruction cache misses | requests |
| EngDivergedInstr | Diverged instructions | instructions |
| GeomFaceXYPlaneCullRate | Facing or XY plane test cull percentage | percent |
| EngSFUInstr | Arithmetic SFU pipe instructions | instructions |
| GeomTotalCullPrim | Culled primitives | primitives |
| EngCVTInstr | Arithmetic CVT pipe instructions | instructions |
| GeomVisibleRate | Visible primitive percentage | percent |
| EngFMAInstr | Arithmetic FMA pipe instructions | instructions |
| CoreActiveCy | Execution core active cycles | cycles |
| NonFragWarp | Non-fragment warps | warps |
| NonFragTask | Non-fragment core tasks | tasks |
| NonFragActiveCy | Non-fragment active cycles | cycles |
| GeomFrontFacePrim | Visible front-facing primitives | primitives |
| CoreFullWarp | Full warps | warps |
| FragOpaqueQd | Occluding quads | quads |
| FragTileKill | Killed unchanged tiles | tiles |
| GeomLinePrim | Line primitives | primitives |
| CoreAllRegsWarp | Warps using more than 32 registers | warps |
| FragTile | Tiles | tiles |
| FragLZSKillQd | Late ZS killed quads | quads |
| FragLZSTestQd | Late ZS tested quads | quads |
| FragEZSKillQd | Early ZS killed quads | quads |
| FragEZSUpdateQd | Early ZS updated quads | quads |
| GeomTotalPrim | Total input primitives | primitives |
| FragRastPartQd | Partial rasterized fine quads | quads |
| FragEZSTestQd | Early ZS tested quads | quads |
| FragWarp | Fragment warps | warps |
| FragFPKActiveCy | Forward pixel kill buffer active cycles | cycles |
| FragRastQd | Rasterized fine quads | quads |
| FragRastPrim | Rasterized primitives | primitives |
| FragRdPrim | Fragment primitives loaded | primitives |
| FragActiveCy | Fragment active cycles | cycles |
| ExtBusWrStallCy | Output external write stall cycles | cycles |
| FragEZSUpdateRate | Early ZS updated quad percentage | percent |
| ExtBusWrBt | Output external write beats | beats |
| FragFPKKillRate | FPK killed quad percentage | percent |
| ExtBusRdStallCy | Output external read stall cycles | cycles |
| FragFPKKillQd | FPK killed quads | quads |
| ExtBusRdBt | Output external read beats | beats |
| ExtBusRdUnique | Output external ReadUnique transactions | transactions |
| ExtBusRdNoSnoop | Output external ReadNoSnoop transactions | transactions |
| ExtBusRd | Output external read transactions | transactions |
| L2CacheSnpLookup | Input external snoop lookup requests | requests |
| L2CacheIncSnpStallCy | Input external snoop stall cycles | cycles |
| L2CacheWrLookup | Write lookup requests | requests |
| L2CacheIncSnp | Input external snoop transactions | transactions |
| L2CacheRdLookup | Read lookup requests | requests |
| ExtBusWrOTQ3 | Output external outstanding writes 50-75% | transactions |
| L2CacheLookup | Any lookup requests | requests |
| L2CacheL1Wr | Output internal write requests | requests |
| L2CacheL1RdStallCy | Output internal read stall cycles | cycles |
| L2CacheL1Rd | Output internal read requests | requests |
| L2CacheSnpStallCy | Input internal snoop stall cycles | cycles |
| L2CacheSnp | Input internal snoop requests | requests |
| L2CacheWrStallCy | Input internal write stall cycles | cycles |
| L2CacheWr | Input internal write requests | requests |
| L2CacheRdStallCy | Input internal read stall cycles | cycles |
| L2CacheRd | Input internal read requests | requests |
| MMUS2L2Hit | MMU stage 2 L2 lookup TLB hits | requests |
| MMUS2L3Hit | MMU stage 2 L3 lookup TLB hits | requests |
| MMUS2L2Rd | MMU stage 2 L2 lookup requests | requests |
| MMUS2L3Rd | MMU stage 2 L3 lookup requests | requests |
| MMUS2Lookup | MMU stage 2 lookup requests | requests |
| ExtBusWrSnoopPart | Output external WriteSnoopPartial transactions | transactions |
| MMUL2Hit | MMU L2 lookup TLB hits | requests |
| MMUL3Hit | MMU L3 lookup TLB hits | requests |
| ExtBusWrOTQ1 | Output external outstanding writes 0-25% | transactions |
| MMUL2Rd | MMU L2 table read requests | requests |
| MMUL3Rd | MMU L3 table read requests | requests |
| ExtBusWrOTQ2 | Output external outstanding writes 25-50% | transactions |
| MMULookup | MMU lookup requests | requests |
| FragTransparentQd | Non-occluding quads | quads |
| ResQueueJob | Reserved queue jobs | jobs |
| L2CacheFlush | L2 cache flush requests | requests |
| ExtBusWrSnoopFull | Output external WriteSnoopFull transactions | transactions |
| ResQueueWaitFinishCy | Reserved queue job finish wait cycles | cycles |
| ExtBusWrNoSnoopPart | Output external WriteNoSnoopPartial transactions | transactions |
| ResQueueWaitDepCy | Reserved queue job dependency wait cycles | cycles |
| ExtBusWrNoSnoopFull | Output external WriteNoSnoopFull transactions | transactions |
| ResQueueWaitIssueCy | Reserved queue job issue wait cycles | cycles |
| ExtBusWr | Output external write transactions | transactions |
| ResQueueWaitRdCy | Reserved queue job descriptor read wait cycles | cycles |
| ExtBusRdLat320 | Output external read latency 320-383 cycles | beats |
| NonFragQueueWaitFinishCy | Non-fragment queue job finish wait cycles | cycles |
| ExtBusRdLat256 | Output external read latency 256-319 cycles | beats |
| NonFragQueueWaitDepCy | Non-fragment queue job dependency wait cycles | cycles |
| ExtBusRdLat192 | Output external read latency 192-255 cycles | beats |
| NonFragQueueWaitIssueCy | Non-fragment queue job issue wait cycles | cycles |
| ResQueueActiveCy | Reserved active cycles | cycles |
| FragOpaqueQdRate | Occluding quad percentage | percent |
| NonFragQueueActiveCy | Non-fragment queue active cycles | cycles |
| ResQueueWaitFlushCy | Reserved queue cache flush wait cycles | cycles |
| ExtBusRdLat128 | Output external read latency 128-191 cycles | beats |
| NonFragQueueWaitRdCy | Non-fragment queue job descriptor read wait cycles | cycles |
| NonFragQueueWaitFlushCy | Non-fragment queue cache flush wait cycles | cycles |
| TilerVarCacheHitRate | Varying cache hit percentage | percent |
| NonFragQueueTask | Non-fragment tasks | tasks |
| FragQueueWaitFlushCy | Fragment queue cache flush wait cycles | cycles |
| GeomVarShadThreadPerPrim | Varying threads per input primitive | threads |
| NonFragQueueJob | Non-fragment jobs | jobs |
| GeomVarShadThread | Varying shader thread invocations | threads |
| FragQueueActiveCy | Fragment queue active cycles | cycles |
| FragShadedQd | Shaded coarse quads | quads |
| ResQueueTask | Reserved queue tasks | tasks |
| ExtBusRdLat0 | Output external read latency 0-127 cycles | beats |
| FragQueueWaitFinishCy | Fragment queue job finish wait cycles | cycles |
| ExtBusRdOTQ3 | Output external outstanding reads 50-75% | transactions |
| FragQueueWaitDepCy | Fragment queue job dependency wait cycles | cycles |
| TilerPosCacheHitRate | Position cache hit percentage | percent |
| FragQueueTask | Fragment tasks | tasks |
| GeomPosShadThreadPerPrim | Position threads per input primitive | threads |
| FragQueueJob | Fragment jobs | jobs |
| ExtBusRdOTQ2 | Output external outstanding reads 25-50% | transactions |
| FragQueueWaitIssueCy | Fragment queue job issue wait cycles | cycles |
| GeomPosShadThread | Position shader thread invocations | threads |
| GPUIRQActiveCy | GPU interrupt pending cycles | cycles |
| ExtBusRdOTQ1 | Output external outstanding reads 0-25% | transactions |
| FragQueueWaitRdCy | Fragment queue job descriptor read wait cycles | cycles |
| GeomSampleCullRate | Sample test cull percentage | percent |
| GPUActiveCy | GPU active cycles | cycles |


from libGPUCounters prop_decoder:
```
product_id:						37011
version_status:					0
minor_revision:					1
major_revision:					0
gpu_freq_khz_max:				5000 ???
log2_program_counter_size:		24
texture_features_0:				4160619518
texture_features_1:				3288332287
texture_features_2:				3219259295
texture_features_3:				4294
gpu_available_memory_size:		3867762688
num_exec_engines:				0
l2_log2_line_size:				6 -> 64
l2_log2_cache_size:				19 -> 512 Kb
l2_num_l2_slices:				1
tiler_bin_size_bytes:			512 b
tiler_max_active_levels:		8
max_threads:					1024
max_workgroup_size:				512
max_barrier_size:				512
max_registers:					32768 -> 32K
max_task_queue:					4
max_thread_group_split:			0
impl_tech:						0
tls_alloc:						1024
raw_shader_present:				5
raw_tiler_present:				1
raw_l2_present:					1
raw_stack_present:				5
raw_l2_features:				135463430 | x08'13'02'06 |		top 8 bits - log2 bus width = 256
raw_core_features:				0
raw_mem_features:				1
raw_mmu_features:				10288
raw_as_present:					255
raw_js_present:					7
raw_js_features_0:				526
raw_js_features_1:				7326
raw_js_features_2:				30
raw_tiler_features:				2057
raw_texture_features_0:			4160619518
raw_texture_features_1:			3288332287
raw_texture_features_2:			3219259295
raw_texture_features_3:			4294
raw_gpu_id:						2425552912
raw_thread_max_threads:			1024
raw_thread_max_workgroup_size:	512
raw_thread_max_barrier_size:	512
raw_thread_features:			294912
raw_coherency_mode:				0
raw_coherency_mode:				31
raw_gpu_features:				0
coherency_num_groups:			1
coherency_num_core_groups:		1 - count of coherency_group_*
coherency_coherency:			1
coherency_group_0:				5 -> 0101 -- shader core bit mask
```

</details>

