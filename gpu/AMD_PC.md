**AMD GPU Performance Counters**

## References

* [GPUPerfAPI](https://gpuopen.com/gpuperfapi/) - to get access to the performance counters.
* [GPUPerfAPI documentation](https://gpuopen.com/manuals/gpu_performance_api_manual/gpu_performance_api_manual-index/)
* [MI200 performance counters and metrics](https://hipfft.readthedocs.io/en/rocm-6.0.2/conceptual/gpu-arch/mi200-performance-counters.html)
* [MI300 and MI200 series performance counters and metrics](https://rocm.docs.amd.com/en/latest/conceptual/gpu-arch/mi300-mi200-performance-counters.html)
* [RDNA3 Graphics counters](https://gpuperfapi.readthedocs.io/en/latest/counters.html#rdna3-counters), [Compute counters](https://gpuperfapi.readthedocs.io/en/latest/counters.html#rdna3-counters-1)
* [RDNA2 Graphics counters](https://gpuperfapi.readthedocs.io/en/latest/counters.html#rdna2-counters), [Compute counters](https://gpuperfapi.readthedocs.io/en/latest/counters.html#rdna2-counters-1)
* [RDNA1 Graphics counters](https://gpuperfapi.readthedocs.io/en/latest/counters.html#rdna-counters), [Compute counters](https://gpuperfapi.readthedocs.io/en/latest/counters.html#rdna-counters-1)
* [GCN5 Graphics counters](https://gpuperfapi.readthedocs.io/en/latest/counters.html#vega-counters), [Compute counters](https://gpuperfapi.readthedocs.io/en/latest/counters.html#vega-counters-1)
* [GCN3/GCN4 Graphics counters](https://gpuperfapi.readthedocs.io/en/latest/counters.html#graphics-ip-v8-counters), [Compute couners](https://gpuperfapi.readthedocs.io/en/latest/counters.html#graphics-ip-v8-counters-1)

## Notes

**Arb** - Arbiter<br/>
**Command Queue** - <br/>
**CP** - Command Processor<br/>
**CPC** - Command Processor - Compute<br/>
**CPF** - Command Processor - Fetcher<br/>
**CU** - Compute Units. Contains ALU, LDS and memory access.<br/>
**CB** - color buffer? <br/>
**ColorBuffer** - ?<br/>
**CC** - Coherently Cached.<br/>
**CSC** - Compute Shader Controller.<br/>
**DCC** - delta color compression?<br/>
**DB** - depth buffer? <br/>
**DepthAndStencil** - ?<br/>
**ES** - ?<br/>
**EA** - Efficiency Arbiter.<br/>
**FLAT** - Flat Memory instructions read, or write, one piece of data into, or out of, VGPRs; they do this separately for each work-item in a wavefront. Flat instructions use a single flat address from the VGPR; this addresses memory as a single flat memory space. This memory space includes video memory, system memory, LDS memory, and scratch (private) memory. It does not include GDS memory. <br/>
**GDS** - Global Data Share. The GDS is a globally shared explicitly addressed memory that is similar to the LDS and can synchronize all wavefronts as well as fixed function hardware. The GDS also contains ALUs used for global atomic operations.<br/>
**GRBM** - Graphics Register Bus Management.<br/>
**GlobalMemory** - ?<br/>
**HiZ** - ?<br/>
**IOP** - Integer Operation.<br/>
**LDS** - Local Data Share. Which a low-latency and high-bandwidth explicitly addressed memory that is used for synchronization within a workgroup and for some graphics functions associated with texturing. Same as shared memory in CUDA.<br/>
**MemoryCache** - ?<br/>
**ME1** - Micro Engine, running packet processing firmware on CPC.<br/>
**MFMA** - Matrix Fused Multiply Add.<br/>
**NC** - Noncoherently Cached.<br/>
**PA** - Primitive Assembly. <br/>
**PA_SC** - ?<br/>
**PA_SU** - ?<br/>
**RW** - Coherently Cached with Write.<br/>
**SALU** - Scalar ALU. Can only be used for a limited set of operations, like integer and logical.<br/>
**SC** - shader core? <br/>
**SGPR** - Vector General Purpose Registers.<br/>
**Shader Engine** - <br/>
**SX** - ?<br/>
**SQ_CS** - ?<br/>
**SQ_HS** - ?<br/>
**SQ_LS** - ?<br/>
**SQ_PS** - ?<br/>
**SQ_VS** - ?<br/>
**SQ_GS** - ?<br/>
**SQ_ES** - ?<br/>
**SQ** - ?<br/>
**SPI** - Shader Processor Input.<br/>
**SH** - ?<br/>
**SMEM** - Scalar memory operations. SMEM transfers data between scalar registers and memory through scalar data cache. The SMEM instruction reads/writes consecutive DWORDs between SGPRs and memory.<br/>
**s​L1D** - Scalar Level-1 Data Cache.<br/>
**SQ** - Sequencer.<br/>
**TextureUnit** - ?<br/>
**TD** - Texture Data Unit.<br/>
**TC** - Texture Cache. <br/>
**TCC** - Texture Cache per Channel, known as L2 Cache, part of Texture Cache Blocks.<br/>
**TCI**, **TCIU** - Texture Cache Interface Unit, interface between CP and the memory system, part of Texture Cache Blocks.<br/>
**TCA** - Texture Cache Arbiter, part of Texture Cache Blocks.<br/>
**TCP** - Texture Cache per Pipe, known as vector L1 Cache, part of Texture Cache Blocks.<br/>
**TA** - Texture Addressing Unit.<br/>
**TMU** - texture mapping unit.<br/>
**UC** - Uncached.<br/>
**UTCL1**, **UTCL2** - Unified Translation Cache - Level X<br/>
**VGT** - ?<br/>
**VALU** - Vector ALU. <br/>
**VGPR** - Scalar General Purpose Registers. Represent a set of registers used to store data that is known to be uniform across the wavefront at compile-time. SGPRs are manipulated by the Scalar ALU (SALU). <br/>
**VMEM** - Vector memory operations. VMEM transfers data between vector registers and memory with each thread can provide a unique memory address.<br/>
**v​L1D** - Vector Level -1 Data Cache.<br/>
**wavefront** - warp, subgroup. 32 or 64 threads per warp.<br/>
**WGP** - workgroup processor.<br/>


## RX 570

<details>

| name | group | description |
|---|---|---|
| **Timing** | - | - |
| GPUTime | Timing | Time this API command took to execute on the GPU in nanoseconds from the time the previous command reached the bottom of the pipeline (BOP) to the time this command reaches the bottom of the pipeline (BOP). Does not include time that draw calls are processed in parallel. |
| ExecutionDuration | Timing | GPU command execution duration in nanoseconds, from the time the command enters the top of the pipeline (TOP) to the time the command reaches the bottom of the pipeline (BOP). Does not include time that draw calls are processed in parallel. |
| ExecutionStart | Timing | GPU command execution start time in nanoseconds. This is the time the command enters the top of the pipeline (TOP). |
| ExecutionEnd | Timing | GPU command execution end time in nanoseconds. This is the time the command reaches the bottom of the pipeline (BOP). |
| GPUBusy | Timing | The percentage of time GPU was busy. |
| GPUBusyCycles | Timing | Number of GPU cycles that the GPU was busy. |
| TessellatorBusy | Timing | The percentage of time the tessellation engine is busy. |
| TessellatorBusyCycles | Timing | Number of GPU cycles that the tessellation engine is busy. |
| VSBusy | Timing | The percentage of time the ShaderUnit has vertex shader work to do. |
| VSBusyCycles | Timing | Number of GPU cycles that the ShaderUnit has vertex shader work to do. |
| VSTime | Timing | Time vertex shaders are busy in nanoseconds. |
| HSBusy | Timing | The percentage of time the ShaderUnit has hull shader work to do. |
| HSBusyCycles | Timing | Number of GPU cycles that the ShaderUnit has hull shader work to do. |
| HSTime | Timing | Time hull shaders are busy in nanoseconds. |
| DSBusy | Timing | The percentage of time the ShaderUnit has domain shader work to do. |
| DSBusyCycles | Timing | Number of GPU cycles that the ShaderUnit has domain shader work to do. |
| DSTime | Timing | Time domain shaders are busy in nanoseconds. |
| GSBusy | Timing | The percentage of time the ShaderUnit has geometry shader work to do. |
| GSBusyCycles | Timing | Number of GPU cycles that the ShaderUnit has geometry shader work to do. |
| GSTime | Timing | Time geometry shaders are busy in nanoseconds. |
| PSBusy | Timing | The percentage of time the ShaderUnit has pixel shader work to do. |
| PSBusyCycles | Timing | Number of GPU cycles that the ShaderUnit has pixel shader work to do. |
| PSTime | Timing | Time pixel shaders are busy in nanoseconds. |
| CSBusy | Timing | The percentage of time the ShaderUnit has compute shader work to do. |
| CSBusyCycles | Timing | Number of GPU cycles that the ShaderUnit has compute shader work to do. |
| CSTime | Timing | Time compute shaders are busy in nanoseconds. |
| **VertexShader** | - | - |
| VSVerticesIn | VertexShader | The number of vertices processed by the VS. |
| VSVALUInstCount | VertexShader | Average number of vector ALU instructions executed in the VS. Affected by flow control. |
| VSSALUInstCount | VertexShader | Average number of scalar ALU instructions executed in the VS. Affected by flow control. |
| VSVALUBusy | VertexShader | The percentage of GPUTime vector ALU instructions are being processed by the VS. |
| VSVALUBusyCycles | VertexShader | Number of GPU cycles where vector ALU instructions are being processed by the VS. |
| VSSALUBusy | VertexShader | The percentage of GPUTime scalar ALU instructions are being processed by the VS. |
| VSSALUBusyCycles | VertexShader | Number of GPU cycles where scalar ALU instructions are being processed by the VS. |
| **HullShader** | - | - |
| HSPatches | HullShader | The number of patches processed by the HS. |
| HSVALUInstCount | HullShader | Average number of vector ALU instructions executed in the HS. Affected by flow control. |
| HSSALUInstCount | HullShader | Average number of scalar ALU instructions executed in the HS. Affected by flow control. |
| HSVALUBusy | HullShader | The percentage of GPUTime vector ALU instructions are being processed by the HS. |
| HSVALUBusyCycles | HullShader | Number of GPU cycles vector where ALU instructions are being processed by the HS. |
| HSSALUBusy | HullShader | The percentage of GPUTime scalar ALU instructions are being processed by the HS. |
| HSSALUBusyCycles | HullShader | Number of GPU cycles where scalar ALU instructions are being processed by the HS. |
| **DomainShader** | - | - |
| DSVerticesIn | DomainShader | The number of vertices processed by the DS. |
| DSVALUInstCount | DomainShader | Average number of vector ALU instructions executed in the DS. Affected by flow control. |
| DSSALUInstCount | DomainShader | Average number of scalar ALU instructions executed in the DS. Affected by flow control. |
| DSVALUBusy | DomainShader | The percentage of GPUTime vector ALU instructions are being processed by the DS. |
| DSVALUBusyCycles | DomainShader | Number of GPU cycles where vector ALU instructions are being processed by the DS. |
| DSSALUBusy | DomainShader | The percentage of GPUTime scalar ALU instructions are being processed by the DS. |
| DSSALUBusyCycles | DomainShader | Number of GPU cycles where scalar ALU instructions are being processed by the DS. |
| **GeometryShader** | - | - |
| GSPrimsIn | GeometryShader | The number of primitives passed into the GS. |
| GSVerticesOut | GeometryShader | The number of vertices output by the GS. |
| GSVALUInstCount | GeometryShader | Average number of vector ALU instructions executed in the GS. Affected by flow control. |
| GSSALUInstCount | GeometryShader | Average number of scalar ALU instructions executed in the GS. Affected by flow control. |
| GSVALUBusy | GeometryShader | The percentage of GPUTime vector ALU instructions are being processed by the GS. |
| GSVALUBusyCycles | GeometryShader | Number of GPU cycles where vector ALU instructions are being processed by the GS. |
| GSSALUBusy | GeometryShader | The percentage of GPUTime scalar ALU instructions are being processed by the GS. |
| GSSALUBusyCycles | GeometryShader | Number of GPU cycles where scalar ALU instructions are being processed by the GS. |
| **PrimitiveAssembly** | - | - |
| PrimitiveAssemblyBusy | Timing | The percentage of GPUTime that primitive assembly (clipping and culling) is busy. High values may be caused by having many small primitives; mid to low values may indicate pixel shader or output buffer bottleneck. |
| PrimitiveAssemblyBusyCycles | Timing | Number of GPU cycles the primitive assembly (clipping and culling) is busy. High values may be caused by having many small primitives; mid to low values may indicate pixel shader or output buffer bottleneck. |
| PrimitivesIn | PrimitiveAssembly | The number of primitives received by the hardware. This includes primitives generated by tessellation. |
| CulledPrims | PrimitiveAssembly | The number of culled primitives. Typical reasons include scissor, the primitive having zero area, and back or front face culling. |
| ClippedPrims | PrimitiveAssembly | The number of primitives that required one or more clipping operations due to intersecting the view volume or user clip planes. |
| PAStalledOnRasterizer | PrimitiveAssembly | Percentage of GPUTime that primitive assembly waits for rasterization to be ready to accept data. This roughly indicates for what percentage of time the pipeline is bottlenecked by pixel operations. |
| PAStalledOnRasterizerCycles | PrimitiveAssembly | Number of GPU cycles the primitive assembly waits for rasterization to be ready to accept data. Indicates the number of GPU cycles the pipeline is bottlenecked by pixel operations. |
| **PixelShader** | - | - |
| PSPixelsOut | PixelShader | Pixels exported from shader to color buffers. Does not include killed or alpha tested pixels; if there are multiple render targets, each render target receives one export, so this will be 2 for 1 pixel written to two RTs. |
| PSExportStalls | PixelShader | Pixel shader output stalls. Percentage of GPUBusy. Should be zero for PS or further upstream limited cases; if not zero, indicates a bottleneck in late Z testing or in the color buffer. |
| PSExportStallsCycles | PixelShader | Number of GPU cycles the pixel shader output stalls. Should be zero for PS or further upstream limited cases; if not zero, indicates a bottleneck in late Z testing or in the color buffer. |
| PSVALUInstCount | PixelShader | Average number of vector ALU instructions executed in the PS. Affected by flow control. |
| PSSALUInstCount | PixelShader | Average number of scalar ALU instructions executed in the PS. Affected by flow control. |
| PSVALUBusy | PixelShader | The percentage of GPUTime vector ALU instructions are being processed by the PS. |
| PSVALUBusyCycles | PixelShader | Number of GPU cycles where vector ALU instructions are being processed by the PS. |
| PSSALUBusy | PixelShader | The percentage of GPUTime scalar ALU instructions are being processed by the PS. |
| PSSALUBusyCycles | PixelShader | Number of GPU cycles where scalar ALU instructions are being processed by the PS. |
| **ComputeShader** | - | - |
| CSThreadGroups | ComputeShader | Total number of thread groups. |
| CSWavefronts | ComputeShader | The total number of wavefronts used for the CS. |
| CSThreads | ComputeShader | The number of CS threads processed by the hardware. |
| CSThreadGroupSize | ComputeShader | The number of CS threads within each thread group. |
| CSVALUInsts | ComputeShader | The average number of vector ALU instructions executed per work-item (affected by flow control). |
| CSVALUUtilization | ComputeShader | The percentage of active vector ALU threads in a wave. A lower number can mean either more thread divergence in a wave or that the work-group size is not a multiple of 64. Value range: 0% (bad), 100% (ideal - no thread divergence). |
| CSSALUInsts | ComputeShader | The average number of scalar ALU instructions executed per work-item (affected by flow control). |
| CSVFetchInsts | ComputeShader | The average number of vector fetch instructions from the video memory executed per work-item (affected by flow control). |
| CSSFetchInsts | ComputeShader | The average number of scalar fetch instructions from the video memory executed per work-item (affected by flow control). |
| CSVWriteInsts | ComputeShader | The average number of vector write instructions to the video memory executed per work-item (affected by flow control). |
| CSFlatVMemInsts | ComputeShader | The average number of FLAT instructions that read from or write to the video memory executed per work item (affected by flow control). Includes FLAT instructions that read from or write to scratch. |
| CSVALUBusy | ComputeShader | The percentage of GPUTime vector ALU instructions are processed. Value range: 0% (bad) to 100% (optimal). |
| CSVALUBusyCycles | ComputeShader | Number of GPU cycles where vector ALU instructions are processed. |
| CSSALUBusy | ComputeShader | The percentage of GPUTime scalar ALU instructions are processed. Value range: 0% (bad) to 100% (optimal). |
| CSSALUBusyCycles | ComputeShader | Number of GPU cycles where scalar ALU instructions are processed. |
| CSMemUnitBusy | ComputeShader | The percentage of GPUTime the memory unit is active. The result includes the stall time (MemUnitStalled). This is measured with all extra fetches and writes and any cache or memory effects taken into account. Value range: 0% to 100% (fetch-bound). |
| CSMemUnitBusyCycles | ComputeShader | Number of GPU cycles the memory unit is active. The result includes the stall time (MemUnitStalled). This is measured with all extra fetches and writes and any cache or memory effects taken into account. |
| CSMemUnitStalled | ComputeShader | The percentage of GPUTime the memory unit is stalled. Try reducing the number or size of fetches and writes if possible. Value range: 0% (optimal) to 100% (bad). |
| CSMemUnitStalledCycles | ComputeShader | Number of GPU cycles the memory unit is stalled. Try reducing the number or size of fetches and writes if possible. |
| CSWriteUnitStalled | ComputeShader | The percentage of GPUTime the write unit is stalled. |
| CSWriteUnitStalledCycles | ComputeShader | Number of GPU cycles the write unit is stalled. |
| CSGDSInsts | ComputeShader | The average number of GDS read or GDS write instructions executed per work item (affected by flow control). |
| CSLDSInsts | ComputeShader | The average number of LDS read/write instructions executed per work-item (affected by flow control). |
| CSFlatLDSInsts | ComputeShader | The average number of FLAT instructions that read from or write to LDS executed per work item (affected by flow control). |
| CSALUStalledByLDS | ComputeShader | The percentage of GPUTime ALU units are stalled by the LDS input queue being full or the output queue being not ready. If there are LDS bank conflicts, reduce them. Otherwise, try reducing the number of LDS accesses if possible. Value range: 0% (optimal) to 100% (bad). |
| CSALUStalledByLDSCycles | ComputeShader | Number of GPU cycles the ALU units are stalled by the LDS input queue being full or the output queue being not ready. If there are LDS bank conflicts, reduce them. Otherwise, try reducing the number of LDS accesses if possible. |
| CSLDSBankConflict | ComputeShader | The percentage of GPUTime LDS is stalled by bank conflicts. Value range: 0% (optimal) to 100% (bad). |
| CSLDSBankConflictCycles | ComputeShader | Number of GPU cycles the LDS is stalled by bank conflicts. Value range: 0 (optimal) to GPUBusyCycles (bad). |
| **TextureUnit** | - | - |
| TexUnitBusy | Timing | The percentage of GPUTime the texture unit is active. This is measured with all extra fetches and any cache or memory effects taken into account. |
| TexUnitBusyCycles | Timing | Number of GPU cycles the texture unit is active. This is measured with all extra fetches and any cache or memory effects taken into account. |
| TexTriFilteringPct | TextureUnit | Percentage of pixels that received trilinear filtering. Note that not all pixels for which trilinear filtering is enabled will receive it (e.g. if the texture is magnified). |
| TexTriFilteringCount | TextureUnit | Count of pixels that received trilinear filtering. Note that not all pixels for which trilinear filtering is enabled will receive it (e.g. if the texture is magnified). |
| NoTexTriFilteringCount | TextureUnit | Count of pixels that did not receive trilinear filtering. |
| TexVolFilteringPct | TextureUnit | Percentage of pixels that received volume filtering. |
| TexVolFilteringCount | TextureUnit | Count of pixels that received volume filtering. |
| NoTexVolFilteringCount | TextureUnit | Count of pixels that did not receive volume filtering. |
| TexAveAnisotropy | TextureUnit | The average degree of anisotropy applied. A number between 1 and 16. The anisotropic filtering algorithm only applies samples where they are required (e.g. there will be no extra anisotropic samples if the view vector is perpendicular to the surface) so this can be much lower than the requested anisotropy. |
| **DepthAndStencil** | - | - |
| DepthStencilTestBusy | Timing | Percentage of time GPU spent performing depth and stencil tests relative to GPUBusy. |
| DepthStencilTestBusyCycles | Timing | Number of GPU cycles spent performing depth and stencil tests. |
| HiZTilesAccepted | DepthAndStencil | Percentage of tiles accepted by HiZ and will be rendered to the depth or color buffers. |
| HiZTilesAcceptedCount | DepthAndStencil | Count of tiles accepted by HiZ and will be rendered to the depth or color buffers. |
| HiZTilesRejectedCount | DepthAndStencil | Count of tiles not accepted by HiZ. |
| PreZTilesDetailCulled | DepthAndStencil | Percentage of tiles rejected because the associated prim had no contributing area. |
| PreZTilesDetailCulledCount | DepthAndStencil | Count of tiles rejected because the associated primitive had no contributing area. |
| PreZTilesDetailSurvivingCount | DepthAndStencil | Count of tiles surviving because the associated primitive had contributing area. |
| HiZQuadsCulled | DepthAndStencil | Percentage of quads that did not have to continue on in the pipeline after HiZ. They may be written directly to the depth buffer, or culled completely. Consistently low values here may suggest that the Z-range is not being fully utilized. |
| HiZQuadsCulledCount | DepthAndStencil | Count of quads that did not have to continue on in the pipeline after HiZ. They may be written directly to the depth buffer, or culled completely. Consistently low values here may suggest that the Z-range is not being fully utilized. |
| HiZQuadsAcceptedCount | DepthAndStencil | Count of quads that did continue on in the pipeline after HiZ. |
| PreZQuadsCulled | DepthAndStencil | Percentage of quads rejected based on the detailZ and earlyZ tests. |
| PreZQuadsCulledCount | DepthAndStencil | Count of quads rejected based on the detailZ and earlyZ tests. |
| PreZQuadsSurvivingCount | DepthAndStencil | Count of quads surviving detailZ and earlyZ tests. |
| PostZQuads | DepthAndStencil | Percentage of quads for which the pixel shader will run and may be postZ tested. |
| PostZQuadCount | DepthAndStencil | Count of quads for which the pixel shader will run and may be postZ tested. |
| PreZSamplesPassing | DepthAndStencil | Number of samples tested for Z before shading and passed. |
| PreZSamplesFailingS | DepthAndStencil | Number of samples tested for Z before shading and failed stencil test. |
| PreZSamplesFailingZ | DepthAndStencil | Number of samples tested for Z before shading and failed Z test. |
| PostZSamplesPassing | DepthAndStencil | Number of samples tested for Z after shading and passed. |
| PostZSamplesFailingS | DepthAndStencil | Number of samples tested for Z after shading and failed stencil test. |
| PostZSamplesFailingZ | DepthAndStencil | Number of samples tested for Z after shading and failed Z test. |
| ZUnitStalled | DepthAndStencil | The percentage of GPUTime the depth buffer spends waiting for the color buffer to be ready to accept data. High figures here indicate a bottleneck in color buffer operations. |
| ZUnitStalledCycles | DepthAndStencil | Number of GPU cycles the depth buffer spends waiting for the color buffer to be ready to accept data. Larger numbers indicate a bottleneck in color buffer operations. |
| DBMemRead | DepthAndStencil | Number of bytes read from the depth buffer. |
| DBMemWritten | DepthAndStencil | Number of bytes written to the depth buffer. |
| **ColorBuffer** | - | - |
| CBMemRead | ColorBuffer | Number of bytes read from the color buffer. |
| CBColorAndMaskRead | ColorBuffer | Total number of bytes read from the color and mask buffers. |
| CBMemWritten | ColorBuffer | Number of bytes written to the color buffer. |
| CBColorAndMaskWritten | ColorBuffer | Total number of bytes written to the color and mask buffers. |
| CBSlowPixelPct | ColorBuffer | Percentage of pixels written to the color buffer using a half-rate or quarter-rate format. |
| CBSlowPixelCount | ColorBuffer | Number of pixels written to the color buffer using a half-rate or quarter-rate format. |
| **MemoryCache** | - | - |
| L0TagConflictReadStalledCycles | MemoryCache | The number of cycles read operations from the L0 cache are stalled due to tag conflicts. |
| L0TagConflictWriteStalledCycles | MemoryCache | The number of cycles write operations to the L0 cache are stalled due to tag conflicts. |
| L0TagConflictAtomicStalledCycles | MemoryCache | The number of cycles atomic operations on the L0 cache are stalled due to tag conflicts. |
| **GlobalMemory** | - | - |
| FetchSize | GlobalMemory | The total bytes fetched from the video memory. This is measured with all extra fetches and any cache or memory effects taken into account. |
| WriteSize | GlobalMemory | The total bytes written to the video memory. This is measured with all extra fetches and any cache or memory effects taken into account. |
| CacheHit | GlobalMemory | The percentage of fetch, write, atomic, and other instructions that hit the data cache. Value range: 0% (no hit) to 100% (optimal). |
| CacheMiss | GlobalMemory | The percentage of fetch, write, atomic, and other instructions that miss the data cache. Value range: 0% (optimal) to 100% (all miss). |
| CacheHitCount | GlobalMemory | Count of fetch, write, atomic, and other instructions that hit the data cache. |
| CacheMissCount | GlobalMemory | Count of fetch, write, atomic, and other instructions that miss the data cache. |
| MemUnitBusy | GlobalMemory | The percentage of GPUTime the memory unit is active. The result includes the stall time (MemUnitStalled). This is measured with all extra fetches and writes and any cache or memory effects taken into account. Value range: 0% to 100% (fetch-bound). |
| MemUnitBusyCycles | GlobalMemory | Number of GPU cycles the memory unit is active. The result includes the stall time (MemUnitStalledCycles). This is measured with all extra fetches and writes and any cache or memory effects taken into account. |
| MemUnitStalled | GlobalMemory | The percentage of GPUTime the memory unit is stalled. Try reducing the number or size of fetches and writes if possible. Value range: 0% (optimal) to 100% (bad). |
| MemUnitStalledCycles | GlobalMemory | Number of GPU cycles the memory unit is stalled. |
| WriteUnitStalled | GlobalMemory | The percentage of GPUTime the Write unit is stalled. Value range: 0% to 100% (bad). |
| WriteUnitStalledCycles | GlobalMemory | Number of GPU cycles the Write unit is stalled. |
| **VGT** | - | - |
| VGT0_PERF_VGT_SPI_ESVERT_VALID | VGT0 | ES Vert is valid |
| VGT0_PERF_VGT_SPI_GSPRIM_VALID | VGT0 | ES GS Primitive send is active |
| VGT0_PERF_VGT_SPI_VSVERT_SEND | VGT0 | VS vert send |
| VGT0_PERF_VGT_SPI_LSVERT_VALID | VGT0 | LS Vert is valid. Sensitive to PERF_SEID_IGNORE_MASK |
| VGT0_PERF_VGT_SPI_HSVERT_VALID | VGT0 | HS Vert is valid. Sensitive to PERF_SEID_IGNORE_MASK |
| VGT0_PERF_VGT_TE11_BUSY | VGT0 | Counts number of cycles the TE11 block is busy. (DX11 Tessellation Fixed Function Logic) |
| VGT1_PERF_VGT_SPI_ESVERT_VALID | VGT1 | ES Vert is valid |
| VGT1_PERF_VGT_SPI_GSPRIM_VALID | VGT1 | ES GS Primitive send is active |
| VGT1_PERF_VGT_SPI_VSVERT_SEND | VGT1 | VS vert send |
| VGT1_PERF_VGT_SPI_LSVERT_VALID | VGT1 | LS Vert is valid. Sensitive to PERF_SEID_IGNORE_MASK |
| VGT1_PERF_VGT_SPI_HSVERT_VALID | VGT1 | HS Vert is valid. Sensitive to PERF_SEID_IGNORE_MASK |
| VGT1_PERF_VGT_TE11_BUSY | VGT1 | Counts number of cycles the TE11 block is busy. (DX11 Tessellation Fixed Function Logic) |
| VGT2_PERF_VGT_SPI_ESVERT_VALID | VGT2 | ES Vert is valid |
| VGT2_PERF_VGT_SPI_GSPRIM_VALID | VGT2 | ES GS Primitive send is active |
| VGT2_PERF_VGT_SPI_VSVERT_SEND | VGT2 | VS vert send |
| VGT2_PERF_VGT_SPI_LSVERT_VALID | VGT2 | LS Vert is valid. Sensitive to PERF_SEID_IGNORE_MASK |
| VGT2_PERF_VGT_SPI_HSVERT_VALID | VGT2 | HS Vert is valid. Sensitive to PERF_SEID_IGNORE_MASK |
| VGT2_PERF_VGT_TE11_BUSY | VGT2 | Counts number of cycles the TE11 block is busy. (DX11 Tessellation Fixed Function Logic) |
| VGT3_PERF_VGT_SPI_ESVERT_VALID | VGT3 | ES Vert is valid |
| VGT3_PERF_VGT_SPI_GSPRIM_VALID | VGT3 | ES GS Primitive send is active |
| VGT3_PERF_VGT_SPI_VSVERT_SEND | VGT3 | VS vert send |
| VGT3_PERF_VGT_SPI_LSVERT_VALID | VGT3 | LS Vert is valid. Sensitive to PERF_SEID_IGNORE_MASK |
| VGT3_PERF_VGT_SPI_HSVERT_VALID | VGT3 | HS Vert is valid. Sensitive to PERF_SEID_IGNORE_MASK |
| VGT3_PERF_VGT_TE11_BUSY | VGT3 | Counts number of cycles the TE11 block is busy. (DX11 Tessellation Fixed Function Logic) |
| **PA_SU** | - | - |
| PA_SU0_PERF_PAPC_PA_INPUT_PRIM | PA_SU0 | PERF_PAPC_PA_INPUT_PRIM Number of Primitives input to PA; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_CLPR_CULL_PRIM | PA_SU0 | PERF_PAPC_CLPR_CULL_PRIM Number of Prims Culled by Clipper for VV, UCP, VTX_KILL, VTX_NAN; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; combined with _CLPR_VVUCP_CULL_PRIM , _CLPR_VV_CULL_PRIM, _VV_CULL_PRIM ,_UCP_CULL_PRIM, _VTX_KILL_CULL_PRIM, _VTX_NAN_CULL_PRIM |
| PA_SU0_PERF_PAPC_CLPR_VVUCP_CLIP_PRIM | PA_SU0 | PERF_PAPC_CLPR_VVUCP_CLIP_PRIM Number of Prims Clipped by Clipper for VV and/or UCP; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_SU_ZERO_AREA_CULL_PRIM | PA_SU0 | PERF_PAPC_SU_ZERO_AREA_CULL_PRIM Number of primitives culled due to zero area; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_SU_BACK_FACE_CULL_PRIM | PA_SU0 | PERF_PAPC_SU_BACK_FACE_CULL_PRIM Number of back-face primitives culled due to facedness; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_SU_FRONT_FACE_CULL_PRIM | PA_SU0 | PERF_PAPC_SU_FRONT_FACE_CULL_PRIM Number of front-face primitives culled due to facedness; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_SU_POLYMODE_FACE_CULL | PA_SU0 | PERF_PAPC_SU_POLYMODE_FACE_CULL Number of polymode cull-determination primitives culled; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_SU_OUTPUT_PRIM | PA_SU0 | PERF_PAPC_SU_OUTPUT_PRIM Number of primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_SU_OUTPUT_CLIP_PRIM | PA_SU0 | PERF_PAPC_SU_OUTPUT_CLIP_PRIM Number of clipped primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_SU_OUTPUT_PRIM_DUAL | PA_SU0 | PERF_PAPC_SU_OUTPUT_PRIM_DUAL Number of dual gradient primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_SU_OUTPUT_CLIP_PRIM_DUAL | PA_SU0 | PERF_PAPC_SU_OUTPUT_CLIP_PRIM_DUAL Number of dual gradient clipped primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU0_PERF_PAPC_CLIP_BUSY | PA_SU0 | PERF_PAPC_CLIP_BUSY Number of clocks Clip is Busy; range-1/clk;it can potentially be used to detect bad performance;all instances report the same result; can be used to detect bottlenecks in combination with other signals |
| PA_SU0_PERF_PAPC_SU_STALLED_SC | PA_SU0 | PERF_PAPC_SU_STALLED_SC Number of clocks Setup is stalled by SC; range-1/clk;it can potentially be used to detect bad performance;all instances report the same result |
| PA_SU1_PERF_PAPC_PA_INPUT_PRIM | PA_SU1 | PERF_PAPC_PA_INPUT_PRIM Number of Primitives input to PA; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_CLPR_CULL_PRIM | PA_SU1 | PERF_PAPC_CLPR_CULL_PRIM Number of Prims Culled by Clipper for VV, UCP, VTX_KILL, VTX_NAN; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; combined with _CLPR_VVUCP_CULL_PRIM , _CLPR_VV_CULL_PRIM, _VV_CULL_PRIM ,_UCP_CULL_PRIM, _VTX_KILL_CULL_PRIM, _VTX_NAN_CULL_PRIM |
| PA_SU1_PERF_PAPC_CLPR_VVUCP_CLIP_PRIM | PA_SU1 | PERF_PAPC_CLPR_VVUCP_CLIP_PRIM Number of Prims Clipped by Clipper for VV and/or UCP; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_SU_ZERO_AREA_CULL_PRIM | PA_SU1 | PERF_PAPC_SU_ZERO_AREA_CULL_PRIM Number of primitives culled due to zero area; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_SU_BACK_FACE_CULL_PRIM | PA_SU1 | PERF_PAPC_SU_BACK_FACE_CULL_PRIM Number of back-face primitives culled due to facedness; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_SU_FRONT_FACE_CULL_PRIM | PA_SU1 | PERF_PAPC_SU_FRONT_FACE_CULL_PRIM Number of front-face primitives culled due to facedness; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_SU_POLYMODE_FACE_CULL | PA_SU1 | PERF_PAPC_SU_POLYMODE_FACE_CULL Number of polymode cull-determination primitives culled; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_SU_OUTPUT_PRIM | PA_SU1 | PERF_PAPC_SU_OUTPUT_PRIM Number of primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_SU_OUTPUT_CLIP_PRIM | PA_SU1 | PERF_PAPC_SU_OUTPUT_CLIP_PRIM Number of clipped primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_SU_OUTPUT_PRIM_DUAL | PA_SU1 | PERF_PAPC_SU_OUTPUT_PRIM_DUAL Number of dual gradient primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_SU_OUTPUT_CLIP_PRIM_DUAL | PA_SU1 | PERF_PAPC_SU_OUTPUT_CLIP_PRIM_DUAL Number of dual gradient clipped primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU1_PERF_PAPC_CLIP_BUSY | PA_SU1 | PERF_PAPC_CLIP_BUSY Number of clocks Clip is Busy; range-1/clk;it can potentially be used to detect bad performance;all instances report the same result; can be used to detect bottlenecks in combination with other signals |
| PA_SU1_PERF_PAPC_SU_STALLED_SC | PA_SU1 | PERF_PAPC_SU_STALLED_SC Number of clocks Setup is stalled by SC; range-1/clk;it can potentially be used to detect bad performance;all instances report the same result |
| PA_SU2_PERF_PAPC_PA_INPUT_PRIM | PA_SU2 | PERF_PAPC_PA_INPUT_PRIM Number of Primitives input to PA; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_CLPR_CULL_PRIM | PA_SU2 | PERF_PAPC_CLPR_CULL_PRIM Number of Prims Culled by Clipper for VV, UCP, VTX_KILL, VTX_NAN; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; combined with _CLPR_VVUCP_CULL_PRIM , _CLPR_VV_CULL_PRIM, _VV_CULL_PRIM ,_UCP_CULL_PRIM, _VTX_KILL_CULL_PRIM, _VTX_NAN_CULL_PRIM |
| PA_SU2_PERF_PAPC_CLPR_VVUCP_CLIP_PRIM | PA_SU2 | PERF_PAPC_CLPR_VVUCP_CLIP_PRIM Number of Prims Clipped by Clipper for VV and/or UCP; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_SU_ZERO_AREA_CULL_PRIM | PA_SU2 | PERF_PAPC_SU_ZERO_AREA_CULL_PRIM Number of primitives culled due to zero area; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_SU_BACK_FACE_CULL_PRIM | PA_SU2 | PERF_PAPC_SU_BACK_FACE_CULL_PRIM Number of back-face primitives culled due to facedness; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_SU_FRONT_FACE_CULL_PRIM | PA_SU2 | PERF_PAPC_SU_FRONT_FACE_CULL_PRIM Number of front-face primitives culled due to facedness; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_SU_POLYMODE_FACE_CULL | PA_SU2 | PERF_PAPC_SU_POLYMODE_FACE_CULL Number of polymode cull-determination primitives culled; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_SU_OUTPUT_PRIM | PA_SU2 | PERF_PAPC_SU_OUTPUT_PRIM Number of primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_SU_OUTPUT_CLIP_PRIM | PA_SU2 | PERF_PAPC_SU_OUTPUT_CLIP_PRIM Number of clipped primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_SU_OUTPUT_PRIM_DUAL | PA_SU2 | PERF_PAPC_SU_OUTPUT_PRIM_DUAL Number of dual gradient primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_SU_OUTPUT_CLIP_PRIM_DUAL | PA_SU2 | PERF_PAPC_SU_OUTPUT_CLIP_PRIM_DUAL Number of dual gradient clipped primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU2_PERF_PAPC_CLIP_BUSY | PA_SU2 | PERF_PAPC_CLIP_BUSY Number of clocks Clip is Busy; range-1/clk;it can potentially be used to detect bad performance;all instances report the same result; can be used to detect bottlenecks in combination with other signals |
| PA_SU2_PERF_PAPC_SU_STALLED_SC | PA_SU2 | PERF_PAPC_SU_STALLED_SC Number of clocks Setup is stalled by SC; range-1/clk;it can potentially be used to detect bad performance;all instances report the same result |
| PA_SU3_PERF_PAPC_PA_INPUT_PRIM | PA_SU3 | PERF_PAPC_PA_INPUT_PRIM Number of Primitives input to PA; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_CLPR_CULL_PRIM | PA_SU3 | PERF_PAPC_CLPR_CULL_PRIM Number of Prims Culled by Clipper for VV, UCP, VTX_KILL, VTX_NAN; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; combined with _CLPR_VVUCP_CULL_PRIM , _CLPR_VV_CULL_PRIM, _VV_CULL_PRIM ,_UCP_CULL_PRIM, _VTX_KILL_CULL_PRIM, _VTX_NAN_CULL_PRIM |
| PA_SU3_PERF_PAPC_CLPR_VVUCP_CLIP_PRIM | PA_SU3 | PERF_PAPC_CLPR_VVUCP_CLIP_PRIM Number of Prims Clipped by Clipper for VV and/or UCP; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_SU_ZERO_AREA_CULL_PRIM | PA_SU3 | PERF_PAPC_SU_ZERO_AREA_CULL_PRIM Number of primitives culled due to zero area; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_SU_BACK_FACE_CULL_PRIM | PA_SU3 | PERF_PAPC_SU_BACK_FACE_CULL_PRIM Number of back-face primitives culled due to facedness; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_SU_FRONT_FACE_CULL_PRIM | PA_SU3 | PERF_PAPC_SU_FRONT_FACE_CULL_PRIM Number of front-face primitives culled due to facedness; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_SU_POLYMODE_FACE_CULL | PA_SU3 | PERF_PAPC_SU_POLYMODE_FACE_CULL Number of polymode cull-determination primitives culled; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_SU_OUTPUT_PRIM | PA_SU3 | PERF_PAPC_SU_OUTPUT_PRIM Number of primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_SU_OUTPUT_CLIP_PRIM | PA_SU3 | PERF_PAPC_SU_OUTPUT_CLIP_PRIM Number of clipped primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_SU_OUTPUT_PRIM_DUAL | PA_SU3 | PERF_PAPC_SU_OUTPUT_PRIM_DUAL Number of dual gradient primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_SU_OUTPUT_CLIP_PRIM_DUAL | PA_SU3 | PERF_PAPC_SU_OUTPUT_CLIP_PRIM_DUAL Number of dual gradient clipped primitives output from the Setup block; increment rate-one per clock ; range-1/clk;it does not indicate bad performance; no bottleneck detection;all instances report the same result; no combinations |
| PA_SU3_PERF_PAPC_CLIP_BUSY | PA_SU3 | PERF_PAPC_CLIP_BUSY Number of clocks Clip is Busy; range-1/clk;it can potentially be used to detect bad performance;all instances report the same result; can be used to detect bottlenecks in combination with other signals |
| PA_SU3_PERF_PAPC_SU_STALLED_SC | PA_SU3 | PERF_PAPC_SU_STALLED_SC Number of clocks Setup is stalled by SC; range-1/clk;it can potentially be used to detect bad performance;all instances report the same result |
| **PA_SC** | - | - |
| PA_SC0_QZ0_QUAD_COUNT | PA_SC0 | SC_QZ0_QUAD_COUNT quad count; quad-z pipe 0 |
| PA_SC0_QZ1_QUAD_COUNT | PA_SC0 | SC_QZ1_QUAD_COUNT quad count; quad-z pipe 1 |
| PA_SC0_QZ2_QUAD_COUNT | PA_SC0 | SC_QZ2_QUAD_COUNT quad count; quad-z pipe 2 |
| PA_SC0_QZ3_QUAD_COUNT | PA_SC0 | SC_QZ3_QUAD_COUNT quad count; quad-z pipe 3 |
| PA_SC0_P0_HIZ_QUAD_COUNT | PA_SC0 | SC_P0_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 0 |
| PA_SC0_P1_HIZ_QUAD_COUNT | PA_SC0 | SC_P1_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 1 |
| PA_SC0_P2_HIZ_QUAD_COUNT | PA_SC0 | SC_P2_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 2 |
| PA_SC0_P3_HIZ_QUAD_COUNT | PA_SC0 | SC_P3_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 3 |
| PA_SC0_EARLYZ_QUAD_COUNT | PA_SC0 | SC_EARLYZ_QUAD_COUNT total quads surviving early-z |
| PA_SC1_QZ0_QUAD_COUNT | PA_SC1 | SC_QZ0_QUAD_COUNT quad count; quad-z pipe 0 |
| PA_SC1_QZ1_QUAD_COUNT | PA_SC1 | SC_QZ1_QUAD_COUNT quad count; quad-z pipe 1 |
| PA_SC1_QZ2_QUAD_COUNT | PA_SC1 | SC_QZ2_QUAD_COUNT quad count; quad-z pipe 2 |
| PA_SC1_QZ3_QUAD_COUNT | PA_SC1 | SC_QZ3_QUAD_COUNT quad count; quad-z pipe 3 |
| PA_SC1_P0_HIZ_QUAD_COUNT | PA_SC1 | SC_P0_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 0 |
| PA_SC1_P1_HIZ_QUAD_COUNT | PA_SC1 | SC_P1_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 1 |
| PA_SC1_P2_HIZ_QUAD_COUNT | PA_SC1 | SC_P2_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 2 |
| PA_SC1_P3_HIZ_QUAD_COUNT | PA_SC1 | SC_P3_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 3 |
| PA_SC1_EARLYZ_QUAD_COUNT | PA_SC1 | SC_EARLYZ_QUAD_COUNT total quads surviving early-z |
| PA_SC2_QZ0_QUAD_COUNT | PA_SC2 | SC_QZ0_QUAD_COUNT quad count; quad-z pipe 0 |
| PA_SC2_QZ1_QUAD_COUNT | PA_SC2 | SC_QZ1_QUAD_COUNT quad count; quad-z pipe 1 |
| PA_SC2_QZ2_QUAD_COUNT | PA_SC2 | SC_QZ2_QUAD_COUNT quad count; quad-z pipe 2 |
| PA_SC2_QZ3_QUAD_COUNT | PA_SC2 | SC_QZ3_QUAD_COUNT quad count; quad-z pipe 3 |
| PA_SC2_P0_HIZ_QUAD_COUNT | PA_SC2 | SC_P0_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 0 |
| PA_SC2_P1_HIZ_QUAD_COUNT | PA_SC2 | SC_P1_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 1 |
| PA_SC2_P2_HIZ_QUAD_COUNT | PA_SC2 | SC_P2_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 2 |
| PA_SC2_P3_HIZ_QUAD_COUNT | PA_SC2 | SC_P3_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 3 |
| PA_SC2_EARLYZ_QUAD_COUNT | PA_SC2 | SC_EARLYZ_QUAD_COUNT total quads surviving early-z |
| PA_SC3_QZ0_QUAD_COUNT | PA_SC3 | SC_QZ0_QUAD_COUNT quad count; quad-z pipe 0 |
| PA_SC3_QZ1_QUAD_COUNT | PA_SC3 | SC_QZ1_QUAD_COUNT quad count; quad-z pipe 1 |
| PA_SC3_QZ2_QUAD_COUNT | PA_SC3 | SC_QZ2_QUAD_COUNT quad count; quad-z pipe 2 |
| PA_SC3_QZ3_QUAD_COUNT | PA_SC3 | SC_QZ3_QUAD_COUNT quad count; quad-z pipe 3 |
| PA_SC3_P0_HIZ_QUAD_COUNT | PA_SC3 | SC_P0_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 0 |
| PA_SC3_P1_HIZ_QUAD_COUNT | PA_SC3 | SC_P1_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 1 |
| PA_SC3_P2_HIZ_QUAD_COUNT | PA_SC3 | SC_P2_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 2 |
| PA_SC3_P3_HIZ_QUAD_COUNT | PA_SC3 | SC_P3_HIZ_QUAD_COUNT total quads surviving hi-z; db pipe 3 |
| PA_SC3_EARLYZ_QUAD_COUNT | PA_SC3 | SC_EARLYZ_QUAD_COUNT total quads surviving early-z |
| **SPI** | - | - |
| SPI0_PERF_VS_BUSY | SPI0 | Number of clocks with outstanding waves (SPI or SH). |
| SPI0_PERF_VS_WAVE | SPI0 | Number of waves |
| SPI0_PERF_GS_BUSY | SPI0 | Number of clocks with outstanding waves (SPI or SH). |
| SPI0_PERF_GS_WAVE | SPI0 | Number of waves |
| SPI0_PERF_ES_BUSY | SPI0 | Number of clocks with outstanding waves (SPI or SH). |
| SPI0_PERF_ES_WAVE | SPI0 | Number of waves |
| SPI0_PERF_HS_BUSY | SPI0 | Number of clocks with outstanding waves (SPI or SH). |
| SPI0_PERF_HS_WAVE | SPI0 | Number of waves |
| SPI0_PERF_LS_BUSY | SPI0 | Number of clocks with outstanding waves (SPI or SH). |
| SPI0_PERF_LS_WAVE | SPI0 | Number of waves |
| SPI0_PERF_CSG_BUSY | SPI0 | Number of clocks with outstanding waves (SPI or SH). |
| SPI0_PERF_CSG_NUM_THREADGROUPS | SPI0 | Number of threadgroups launched |
| SPI0_PERF_CSG_WAVE | SPI0 | Number of waves |
| SPI0_PERF_CSN_BUSY | SPI0 | Number of clocks with outstanding waves (SPI or SH). |
| SPI0_PERF_CSN_NUM_THREADGROUPS | SPI0 | Number of threadgroups launched |
| SPI0_PERF_CSN_WAVE | SPI0 | Number of waves |
| SPI0_PERF_PS_CTL_BUSY | SPI0 | Number of clocks with outstanding waves (SPI or SH). |
| SPI0_PERF_PS_CTL_WAVE | SPI0 | Number of waves |
| SPI1_PERF_VS_BUSY | SPI1 | Number of clocks with outstanding waves (SPI or SH). |
| SPI1_PERF_VS_WAVE | SPI1 | Number of waves |
| SPI1_PERF_GS_BUSY | SPI1 | Number of clocks with outstanding waves (SPI or SH). |
| SPI1_PERF_GS_WAVE | SPI1 | Number of waves |
| SPI1_PERF_ES_BUSY | SPI1 | Number of clocks with outstanding waves (SPI or SH). |
| SPI1_PERF_ES_WAVE | SPI1 | Number of waves |
| SPI1_PERF_HS_BUSY | SPI1 | Number of clocks with outstanding waves (SPI or SH). |
| SPI1_PERF_HS_WAVE | SPI1 | Number of waves |
| SPI1_PERF_LS_BUSY | SPI1 | Number of clocks with outstanding waves (SPI or SH). |
| SPI1_PERF_LS_WAVE | SPI1 | Number of waves |
| SPI1_PERF_CSG_BUSY | SPI1 | Number of clocks with outstanding waves (SPI or SH). |
| SPI1_PERF_CSG_NUM_THREADGROUPS | SPI1 | Number of threadgroups launched |
| SPI1_PERF_CSG_WAVE | SPI1 | Number of waves |
| SPI1_PERF_CSN_BUSY | SPI1 | Number of clocks with outstanding waves (SPI or SH). |
| SPI1_PERF_CSN_NUM_THREADGROUPS | SPI1 | Number of threadgroups launched |
| SPI1_PERF_CSN_WAVE | SPI1 | Number of waves |
| SPI1_PERF_PS_CTL_BUSY | SPI1 | Number of clocks with outstanding waves (SPI or SH). |
| SPI1_PERF_PS_CTL_WAVE | SPI1 | Number of waves |
| SPI2_PERF_VS_BUSY | SPI2 | Number of clocks with outstanding waves (SPI or SH). |
| SPI2_PERF_VS_WAVE | SPI2 | Number of waves |
| SPI2_PERF_GS_BUSY | SPI2 | Number of clocks with outstanding waves (SPI or SH). |
| SPI2_PERF_GS_WAVE | SPI2 | Number of waves |
| SPI2_PERF_ES_BUSY | SPI2 | Number of clocks with outstanding waves (SPI or SH). |
| SPI2_PERF_ES_WAVE | SPI2 | Number of waves |
| SPI2_PERF_HS_BUSY | SPI2 | Number of clocks with outstanding waves (SPI or SH). |
| SPI2_PERF_HS_WAVE | SPI2 | Number of waves |
| SPI2_PERF_LS_BUSY | SPI2 | Number of clocks with outstanding waves (SPI or SH). |
| SPI2_PERF_LS_WAVE | SPI2 | Number of waves |
| SPI2_PERF_CSG_BUSY | SPI2 | Number of clocks with outstanding waves (SPI or SH). |
| SPI2_PERF_CSG_NUM_THREADGROUPS | SPI2 | Number of threadgroups launched |
| SPI2_PERF_CSG_WAVE | SPI2 | Number of waves |
| SPI2_PERF_CSN_BUSY | SPI2 | Number of clocks with outstanding waves (SPI or SH). |
| SPI2_PERF_CSN_NUM_THREADGROUPS | SPI2 | Number of threadgroups launched |
| SPI2_PERF_CSN_WAVE | SPI2 | Number of waves |
| SPI2_PERF_PS_CTL_BUSY | SPI2 | Number of clocks with outstanding waves (SPI or SH). |
| SPI2_PERF_PS_CTL_WAVE | SPI2 | Number of waves |
| SPI3_PERF_VS_BUSY | SPI3 | Number of clocks with outstanding waves (SPI or SH). |
| SPI3_PERF_VS_WAVE | SPI3 | Number of waves |
| SPI3_PERF_GS_BUSY | SPI3 | Number of clocks with outstanding waves (SPI or SH). |
| SPI3_PERF_GS_WAVE | SPI3 | Number of waves |
| SPI3_PERF_ES_BUSY | SPI3 | Number of clocks with outstanding waves (SPI or SH). |
| SPI3_PERF_ES_WAVE | SPI3 | Number of waves |
| SPI3_PERF_HS_BUSY | SPI3 | Number of clocks with outstanding waves (SPI or SH). |
| SPI3_PERF_HS_WAVE | SPI3 | Number of waves |
| SPI3_PERF_LS_BUSY | SPI3 | Number of clocks with outstanding waves (SPI or SH). |
| SPI3_PERF_LS_WAVE | SPI3 | Number of waves |
| SPI3_PERF_CSG_BUSY | SPI3 | Number of clocks with outstanding waves (SPI or SH). |
| SPI3_PERF_CSG_NUM_THREADGROUPS | SPI3 | Number of threadgroups launched |
| SPI3_PERF_CSG_WAVE | SPI3 | Number of waves |
| SPI3_PERF_CSN_BUSY | SPI3 | Number of clocks with outstanding waves (SPI or SH). |
| SPI3_PERF_CSN_NUM_THREADGROUPS | SPI3 | Number of threadgroups launched |
| SPI3_PERF_CSN_WAVE | SPI3 | Number of waves |
| SPI3_PERF_PS_CTL_BUSY | SPI3 | Number of clocks with outstanding waves (SPI or SH). |
| SPI3_PERF_PS_CTL_WAVE | SPI3 | Number of waves |
| **SQ** | - | - |
| SQ0_PERF_SEL_WAVES | SQ0 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ0_PERF_SEL_ITEMS | SQ0 | Number of valid items per wave. (per-simd, global) |
| SQ0_PERF_SEL_INSTS_VALU | SQ0 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ0_PERF_SEL_INSTS_VMEM_WR | SQ0 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ0_PERF_SEL_INSTS_VMEM_RD | SQ0 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ0_PERF_SEL_INSTS_SALU | SQ0 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ0_PERF_SEL_INSTS_SMEM | SQ0 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ0_PERF_SEL_INSTS_FLAT | SQ0 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ0_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ0 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ0_PERF_SEL_INSTS_LDS | SQ0 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ0_PERF_SEL_INSTS_GDS | SQ0 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ0_PERF_SEL_WAIT_INST_LDS | SQ0 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ0_PERF_SEL_INST_CYCLES_VALU | SQ0 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ0_PERF_SEL_INST_CYCLES_SALU | SQ0 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ0_PERF_SEL_THREAD_CYCLES_VALU | SQ0 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ0_PERF_SEL_LDS_BANK_CONFLICT | SQ0 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ1_PERF_SEL_WAVES | SQ1 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ1_PERF_SEL_ITEMS | SQ1 | Number of valid items per wave. (per-simd, global) |
| SQ1_PERF_SEL_INSTS_VALU | SQ1 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ1_PERF_SEL_INSTS_VMEM_WR | SQ1 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ1_PERF_SEL_INSTS_VMEM_RD | SQ1 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ1_PERF_SEL_INSTS_SALU | SQ1 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ1_PERF_SEL_INSTS_SMEM | SQ1 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ1_PERF_SEL_INSTS_FLAT | SQ1 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ1_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ1 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ1_PERF_SEL_INSTS_LDS | SQ1 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ1_PERF_SEL_INSTS_GDS | SQ1 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ1_PERF_SEL_WAIT_INST_LDS | SQ1 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ1_PERF_SEL_INST_CYCLES_VALU | SQ1 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ1_PERF_SEL_INST_CYCLES_SALU | SQ1 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ1_PERF_SEL_THREAD_CYCLES_VALU | SQ1 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ1_PERF_SEL_LDS_BANK_CONFLICT | SQ1 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ2_PERF_SEL_WAVES | SQ2 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ2_PERF_SEL_ITEMS | SQ2 | Number of valid items per wave. (per-simd, global) |
| SQ2_PERF_SEL_INSTS_VALU | SQ2 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ2_PERF_SEL_INSTS_VMEM_WR | SQ2 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ2_PERF_SEL_INSTS_VMEM_RD | SQ2 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ2_PERF_SEL_INSTS_SALU | SQ2 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ2_PERF_SEL_INSTS_SMEM | SQ2 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ2_PERF_SEL_INSTS_FLAT | SQ2 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ2_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ2 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ2_PERF_SEL_INSTS_LDS | SQ2 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ2_PERF_SEL_INSTS_GDS | SQ2 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ2_PERF_SEL_WAIT_INST_LDS | SQ2 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ2_PERF_SEL_INST_CYCLES_VALU | SQ2 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ2_PERF_SEL_INST_CYCLES_SALU | SQ2 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ2_PERF_SEL_THREAD_CYCLES_VALU | SQ2 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ2_PERF_SEL_LDS_BANK_CONFLICT | SQ2 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ3_PERF_SEL_WAVES | SQ3 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ3_PERF_SEL_ITEMS | SQ3 | Number of valid items per wave. (per-simd, global) |
| SQ3_PERF_SEL_INSTS_VALU | SQ3 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ3_PERF_SEL_INSTS_VMEM_WR | SQ3 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ3_PERF_SEL_INSTS_VMEM_RD | SQ3 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ3_PERF_SEL_INSTS_SALU | SQ3 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ3_PERF_SEL_INSTS_SMEM | SQ3 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ3_PERF_SEL_INSTS_FLAT | SQ3 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ3_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ3 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ3_PERF_SEL_INSTS_LDS | SQ3 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ3_PERF_SEL_INSTS_GDS | SQ3 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ3_PERF_SEL_WAIT_INST_LDS | SQ3 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ3_PERF_SEL_INST_CYCLES_VALU | SQ3 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ3_PERF_SEL_INST_CYCLES_SALU | SQ3 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ3_PERF_SEL_THREAD_CYCLES_VALU | SQ3 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ3_PERF_SEL_LDS_BANK_CONFLICT | SQ3 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| **SQ_ES** | - | - |
| SQ_ES0_PERF_SEL_WAVES | SQ_ES0 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_ES0_PERF_SEL_ITEMS | SQ_ES0 | Number of valid items per wave. (per-simd, global) |
| SQ_ES0_PERF_SEL_INSTS_VALU | SQ_ES0 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_ES0_PERF_SEL_INSTS_VMEM_WR | SQ_ES0 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES0_PERF_SEL_INSTS_VMEM_RD | SQ_ES0 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES0_PERF_SEL_INSTS_SALU | SQ_ES0 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_ES0_PERF_SEL_INSTS_SMEM | SQ_ES0 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_ES0_PERF_SEL_INSTS_FLAT | SQ_ES0 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_ES0_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_ES0 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_ES0_PERF_SEL_INSTS_LDS | SQ_ES0 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES0_PERF_SEL_INSTS_GDS | SQ_ES0 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_ES0_PERF_SEL_WAIT_INST_LDS | SQ_ES0 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_ES0_PERF_SEL_INST_CYCLES_VALU | SQ_ES0 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_ES0_PERF_SEL_INST_CYCLES_SALU | SQ_ES0 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_ES0_PERF_SEL_THREAD_CYCLES_VALU | SQ_ES0 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_ES0_PERF_SEL_LDS_BANK_CONFLICT | SQ_ES0 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_ES1_PERF_SEL_WAVES | SQ_ES1 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_ES1_PERF_SEL_ITEMS | SQ_ES1 | Number of valid items per wave. (per-simd, global) |
| SQ_ES1_PERF_SEL_INSTS_VALU | SQ_ES1 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_ES1_PERF_SEL_INSTS_VMEM_WR | SQ_ES1 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES1_PERF_SEL_INSTS_VMEM_RD | SQ_ES1 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES1_PERF_SEL_INSTS_SALU | SQ_ES1 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_ES1_PERF_SEL_INSTS_SMEM | SQ_ES1 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_ES1_PERF_SEL_INSTS_FLAT | SQ_ES1 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_ES1_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_ES1 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_ES1_PERF_SEL_INSTS_LDS | SQ_ES1 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES1_PERF_SEL_INSTS_GDS | SQ_ES1 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_ES1_PERF_SEL_WAIT_INST_LDS | SQ_ES1 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_ES1_PERF_SEL_INST_CYCLES_VALU | SQ_ES1 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_ES1_PERF_SEL_INST_CYCLES_SALU | SQ_ES1 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_ES1_PERF_SEL_THREAD_CYCLES_VALU | SQ_ES1 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_ES1_PERF_SEL_LDS_BANK_CONFLICT | SQ_ES1 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_ES2_PERF_SEL_WAVES | SQ_ES2 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_ES2_PERF_SEL_ITEMS | SQ_ES2 | Number of valid items per wave. (per-simd, global) |
| SQ_ES2_PERF_SEL_INSTS_VALU | SQ_ES2 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_ES2_PERF_SEL_INSTS_VMEM_WR | SQ_ES2 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES2_PERF_SEL_INSTS_VMEM_RD | SQ_ES2 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES2_PERF_SEL_INSTS_SALU | SQ_ES2 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_ES2_PERF_SEL_INSTS_SMEM | SQ_ES2 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_ES2_PERF_SEL_INSTS_FLAT | SQ_ES2 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_ES2_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_ES2 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_ES2_PERF_SEL_INSTS_LDS | SQ_ES2 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES2_PERF_SEL_INSTS_GDS | SQ_ES2 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_ES2_PERF_SEL_WAIT_INST_LDS | SQ_ES2 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_ES2_PERF_SEL_INST_CYCLES_VALU | SQ_ES2 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_ES2_PERF_SEL_INST_CYCLES_SALU | SQ_ES2 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_ES2_PERF_SEL_THREAD_CYCLES_VALU | SQ_ES2 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_ES2_PERF_SEL_LDS_BANK_CONFLICT | SQ_ES2 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_ES3_PERF_SEL_WAVES | SQ_ES3 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_ES3_PERF_SEL_ITEMS | SQ_ES3 | Number of valid items per wave. (per-simd, global) |
| SQ_ES3_PERF_SEL_INSTS_VALU | SQ_ES3 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_ES3_PERF_SEL_INSTS_VMEM_WR | SQ_ES3 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES3_PERF_SEL_INSTS_VMEM_RD | SQ_ES3 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES3_PERF_SEL_INSTS_SALU | SQ_ES3 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_ES3_PERF_SEL_INSTS_SMEM | SQ_ES3 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_ES3_PERF_SEL_INSTS_FLAT | SQ_ES3 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_ES3_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_ES3 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_ES3_PERF_SEL_INSTS_LDS | SQ_ES3 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_ES3_PERF_SEL_INSTS_GDS | SQ_ES3 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_ES3_PERF_SEL_WAIT_INST_LDS | SQ_ES3 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_ES3_PERF_SEL_INST_CYCLES_VALU | SQ_ES3 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_ES3_PERF_SEL_INST_CYCLES_SALU | SQ_ES3 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_ES3_PERF_SEL_THREAD_CYCLES_VALU | SQ_ES3 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_ES3_PERF_SEL_LDS_BANK_CONFLICT | SQ_ES3 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| **SQ_GS** | - | - |
| SQ_GS0_PERF_SEL_WAVES | SQ_GS0 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_GS0_PERF_SEL_ITEMS | SQ_GS0 | Number of valid items per wave. (per-simd, global) |
| SQ_GS0_PERF_SEL_INSTS_VALU | SQ_GS0 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_GS0_PERF_SEL_INSTS_VMEM_WR | SQ_GS0 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS0_PERF_SEL_INSTS_VMEM_RD | SQ_GS0 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS0_PERF_SEL_INSTS_SALU | SQ_GS0 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_GS0_PERF_SEL_INSTS_SMEM | SQ_GS0 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_GS0_PERF_SEL_INSTS_FLAT | SQ_GS0 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_GS0_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_GS0 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_GS0_PERF_SEL_INSTS_LDS | SQ_GS0 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS0_PERF_SEL_INSTS_GDS | SQ_GS0 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_GS0_PERF_SEL_WAIT_INST_LDS | SQ_GS0 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_GS0_PERF_SEL_INST_CYCLES_VALU | SQ_GS0 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_GS0_PERF_SEL_INST_CYCLES_SALU | SQ_GS0 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_GS0_PERF_SEL_THREAD_CYCLES_VALU | SQ_GS0 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_GS0_PERF_SEL_LDS_BANK_CONFLICT | SQ_GS0 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_GS1_PERF_SEL_WAVES | SQ_GS1 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_GS1_PERF_SEL_ITEMS | SQ_GS1 | Number of valid items per wave. (per-simd, global) |
| SQ_GS1_PERF_SEL_INSTS_VALU | SQ_GS1 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_GS1_PERF_SEL_INSTS_VMEM_WR | SQ_GS1 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS1_PERF_SEL_INSTS_VMEM_RD | SQ_GS1 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS1_PERF_SEL_INSTS_SALU | SQ_GS1 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_GS1_PERF_SEL_INSTS_SMEM | SQ_GS1 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_GS1_PERF_SEL_INSTS_FLAT | SQ_GS1 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_GS1_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_GS1 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_GS1_PERF_SEL_INSTS_LDS | SQ_GS1 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS1_PERF_SEL_INSTS_GDS | SQ_GS1 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_GS1_PERF_SEL_WAIT_INST_LDS | SQ_GS1 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_GS1_PERF_SEL_INST_CYCLES_VALU | SQ_GS1 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_GS1_PERF_SEL_INST_CYCLES_SALU | SQ_GS1 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_GS1_PERF_SEL_THREAD_CYCLES_VALU | SQ_GS1 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_GS1_PERF_SEL_LDS_BANK_CONFLICT | SQ_GS1 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_GS2_PERF_SEL_WAVES | SQ_GS2 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_GS2_PERF_SEL_ITEMS | SQ_GS2 | Number of valid items per wave. (per-simd, global) |
| SQ_GS2_PERF_SEL_INSTS_VALU | SQ_GS2 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_GS2_PERF_SEL_INSTS_VMEM_WR | SQ_GS2 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS2_PERF_SEL_INSTS_VMEM_RD | SQ_GS2 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS2_PERF_SEL_INSTS_SALU | SQ_GS2 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_GS2_PERF_SEL_INSTS_SMEM | SQ_GS2 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_GS2_PERF_SEL_INSTS_FLAT | SQ_GS2 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_GS2_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_GS2 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_GS2_PERF_SEL_INSTS_LDS | SQ_GS2 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS2_PERF_SEL_INSTS_GDS | SQ_GS2 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_GS2_PERF_SEL_WAIT_INST_LDS | SQ_GS2 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_GS2_PERF_SEL_INST_CYCLES_VALU | SQ_GS2 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_GS2_PERF_SEL_INST_CYCLES_SALU | SQ_GS2 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_GS2_PERF_SEL_THREAD_CYCLES_VALU | SQ_GS2 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_GS2_PERF_SEL_LDS_BANK_CONFLICT | SQ_GS2 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_GS3_PERF_SEL_WAVES | SQ_GS3 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_GS3_PERF_SEL_ITEMS | SQ_GS3 | Number of valid items per wave. (per-simd, global) |
| SQ_GS3_PERF_SEL_INSTS_VALU | SQ_GS3 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_GS3_PERF_SEL_INSTS_VMEM_WR | SQ_GS3 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS3_PERF_SEL_INSTS_VMEM_RD | SQ_GS3 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS3_PERF_SEL_INSTS_SALU | SQ_GS3 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_GS3_PERF_SEL_INSTS_SMEM | SQ_GS3 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_GS3_PERF_SEL_INSTS_FLAT | SQ_GS3 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_GS3_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_GS3 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_GS3_PERF_SEL_INSTS_LDS | SQ_GS3 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_GS3_PERF_SEL_INSTS_GDS | SQ_GS3 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_GS3_PERF_SEL_WAIT_INST_LDS | SQ_GS3 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_GS3_PERF_SEL_INST_CYCLES_VALU | SQ_GS3 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_GS3_PERF_SEL_INST_CYCLES_SALU | SQ_GS3 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_GS3_PERF_SEL_THREAD_CYCLES_VALU | SQ_GS3 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_GS3_PERF_SEL_LDS_BANK_CONFLICT | SQ_GS3 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| **SQ_VS** | - | - |
| SQ_VS0_PERF_SEL_WAVES | SQ_VS0 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_VS0_PERF_SEL_ITEMS | SQ_VS0 | Number of valid items per wave. (per-simd, global) |
| SQ_VS0_PERF_SEL_INSTS_VALU | SQ_VS0 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_VS0_PERF_SEL_INSTS_VMEM_WR | SQ_VS0 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS0_PERF_SEL_INSTS_VMEM_RD | SQ_VS0 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS0_PERF_SEL_INSTS_SALU | SQ_VS0 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_VS0_PERF_SEL_INSTS_SMEM | SQ_VS0 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_VS0_PERF_SEL_INSTS_FLAT | SQ_VS0 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_VS0_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_VS0 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_VS0_PERF_SEL_INSTS_LDS | SQ_VS0 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS0_PERF_SEL_INSTS_GDS | SQ_VS0 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_VS0_PERF_SEL_WAIT_INST_LDS | SQ_VS0 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_VS0_PERF_SEL_INST_CYCLES_VALU | SQ_VS0 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_VS0_PERF_SEL_INST_CYCLES_SALU | SQ_VS0 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_VS0_PERF_SEL_THREAD_CYCLES_VALU | SQ_VS0 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_VS0_PERF_SEL_LDS_BANK_CONFLICT | SQ_VS0 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_VS1_PERF_SEL_WAVES | SQ_VS1 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_VS1_PERF_SEL_ITEMS | SQ_VS1 | Number of valid items per wave. (per-simd, global) |
| SQ_VS1_PERF_SEL_INSTS_VALU | SQ_VS1 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_VS1_PERF_SEL_INSTS_VMEM_WR | SQ_VS1 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS1_PERF_SEL_INSTS_VMEM_RD | SQ_VS1 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS1_PERF_SEL_INSTS_SALU | SQ_VS1 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_VS1_PERF_SEL_INSTS_SMEM | SQ_VS1 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_VS1_PERF_SEL_INSTS_FLAT | SQ_VS1 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_VS1_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_VS1 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_VS1_PERF_SEL_INSTS_LDS | SQ_VS1 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS1_PERF_SEL_INSTS_GDS | SQ_VS1 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_VS1_PERF_SEL_WAIT_INST_LDS | SQ_VS1 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_VS1_PERF_SEL_INST_CYCLES_VALU | SQ_VS1 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_VS1_PERF_SEL_INST_CYCLES_SALU | SQ_VS1 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_VS1_PERF_SEL_THREAD_CYCLES_VALU | SQ_VS1 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_VS1_PERF_SEL_LDS_BANK_CONFLICT | SQ_VS1 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_VS2_PERF_SEL_WAVES | SQ_VS2 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_VS2_PERF_SEL_ITEMS | SQ_VS2 | Number of valid items per wave. (per-simd, global) |
| SQ_VS2_PERF_SEL_INSTS_VALU | SQ_VS2 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_VS2_PERF_SEL_INSTS_VMEM_WR | SQ_VS2 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS2_PERF_SEL_INSTS_VMEM_RD | SQ_VS2 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS2_PERF_SEL_INSTS_SALU | SQ_VS2 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_VS2_PERF_SEL_INSTS_SMEM | SQ_VS2 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_VS2_PERF_SEL_INSTS_FLAT | SQ_VS2 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_VS2_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_VS2 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_VS2_PERF_SEL_INSTS_LDS | SQ_VS2 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS2_PERF_SEL_INSTS_GDS | SQ_VS2 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_VS2_PERF_SEL_WAIT_INST_LDS | SQ_VS2 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_VS2_PERF_SEL_INST_CYCLES_VALU | SQ_VS2 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_VS2_PERF_SEL_INST_CYCLES_SALU | SQ_VS2 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_VS2_PERF_SEL_THREAD_CYCLES_VALU | SQ_VS2 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_VS2_PERF_SEL_LDS_BANK_CONFLICT | SQ_VS2 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_VS3_PERF_SEL_WAVES | SQ_VS3 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_VS3_PERF_SEL_ITEMS | SQ_VS3 | Number of valid items per wave. (per-simd, global) |
| SQ_VS3_PERF_SEL_INSTS_VALU | SQ_VS3 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_VS3_PERF_SEL_INSTS_VMEM_WR | SQ_VS3 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS3_PERF_SEL_INSTS_VMEM_RD | SQ_VS3 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS3_PERF_SEL_INSTS_SALU | SQ_VS3 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_VS3_PERF_SEL_INSTS_SMEM | SQ_VS3 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_VS3_PERF_SEL_INSTS_FLAT | SQ_VS3 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_VS3_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_VS3 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_VS3_PERF_SEL_INSTS_LDS | SQ_VS3 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_VS3_PERF_SEL_INSTS_GDS | SQ_VS3 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_VS3_PERF_SEL_WAIT_INST_LDS | SQ_VS3 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_VS3_PERF_SEL_INST_CYCLES_VALU | SQ_VS3 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_VS3_PERF_SEL_INST_CYCLES_SALU | SQ_VS3 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_VS3_PERF_SEL_THREAD_CYCLES_VALU | SQ_VS3 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_VS3_PERF_SEL_LDS_BANK_CONFLICT | SQ_VS3 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| **SQ_PS** | - | - |
| SQ_PS0_PERF_SEL_WAVES | SQ_PS0 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_PS0_PERF_SEL_ITEMS | SQ_PS0 | Number of valid items per wave. (per-simd, global) |
| SQ_PS0_PERF_SEL_INSTS_VALU | SQ_PS0 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_PS0_PERF_SEL_INSTS_VMEM_WR | SQ_PS0 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS0_PERF_SEL_INSTS_VMEM_RD | SQ_PS0 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS0_PERF_SEL_INSTS_SALU | SQ_PS0 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_PS0_PERF_SEL_INSTS_SMEM | SQ_PS0 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_PS0_PERF_SEL_INSTS_FLAT | SQ_PS0 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_PS0_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_PS0 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_PS0_PERF_SEL_INSTS_LDS | SQ_PS0 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS0_PERF_SEL_INSTS_GDS | SQ_PS0 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_PS0_PERF_SEL_WAIT_INST_LDS | SQ_PS0 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_PS0_PERF_SEL_INST_CYCLES_VALU | SQ_PS0 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_PS0_PERF_SEL_INST_CYCLES_SALU | SQ_PS0 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_PS0_PERF_SEL_THREAD_CYCLES_VALU | SQ_PS0 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_PS0_PERF_SEL_LDS_BANK_CONFLICT | SQ_PS0 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_PS1_PERF_SEL_WAVES | SQ_PS1 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_PS1_PERF_SEL_ITEMS | SQ_PS1 | Number of valid items per wave. (per-simd, global) |
| SQ_PS1_PERF_SEL_INSTS_VALU | SQ_PS1 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_PS1_PERF_SEL_INSTS_VMEM_WR | SQ_PS1 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS1_PERF_SEL_INSTS_VMEM_RD | SQ_PS1 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS1_PERF_SEL_INSTS_SALU | SQ_PS1 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_PS1_PERF_SEL_INSTS_SMEM | SQ_PS1 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_PS1_PERF_SEL_INSTS_FLAT | SQ_PS1 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_PS1_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_PS1 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_PS1_PERF_SEL_INSTS_LDS | SQ_PS1 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS1_PERF_SEL_INSTS_GDS | SQ_PS1 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_PS1_PERF_SEL_WAIT_INST_LDS | SQ_PS1 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_PS1_PERF_SEL_INST_CYCLES_VALU | SQ_PS1 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_PS1_PERF_SEL_INST_CYCLES_SALU | SQ_PS1 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_PS1_PERF_SEL_THREAD_CYCLES_VALU | SQ_PS1 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_PS1_PERF_SEL_LDS_BANK_CONFLICT | SQ_PS1 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_PS2_PERF_SEL_WAVES | SQ_PS2 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_PS2_PERF_SEL_ITEMS | SQ_PS2 | Number of valid items per wave. (per-simd, global) |
| SQ_PS2_PERF_SEL_INSTS_VALU | SQ_PS2 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_PS2_PERF_SEL_INSTS_VMEM_WR | SQ_PS2 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS2_PERF_SEL_INSTS_VMEM_RD | SQ_PS2 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS2_PERF_SEL_INSTS_SALU | SQ_PS2 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_PS2_PERF_SEL_INSTS_SMEM | SQ_PS2 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_PS2_PERF_SEL_INSTS_FLAT | SQ_PS2 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_PS2_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_PS2 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_PS2_PERF_SEL_INSTS_LDS | SQ_PS2 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS2_PERF_SEL_INSTS_GDS | SQ_PS2 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_PS2_PERF_SEL_WAIT_INST_LDS | SQ_PS2 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_PS2_PERF_SEL_INST_CYCLES_VALU | SQ_PS2 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_PS2_PERF_SEL_INST_CYCLES_SALU | SQ_PS2 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_PS2_PERF_SEL_THREAD_CYCLES_VALU | SQ_PS2 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_PS2_PERF_SEL_LDS_BANK_CONFLICT | SQ_PS2 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_PS3_PERF_SEL_WAVES | SQ_PS3 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_PS3_PERF_SEL_ITEMS | SQ_PS3 | Number of valid items per wave. (per-simd, global) |
| SQ_PS3_PERF_SEL_INSTS_VALU | SQ_PS3 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_PS3_PERF_SEL_INSTS_VMEM_WR | SQ_PS3 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS3_PERF_SEL_INSTS_VMEM_RD | SQ_PS3 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS3_PERF_SEL_INSTS_SALU | SQ_PS3 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_PS3_PERF_SEL_INSTS_SMEM | SQ_PS3 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_PS3_PERF_SEL_INSTS_FLAT | SQ_PS3 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_PS3_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_PS3 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_PS3_PERF_SEL_INSTS_LDS | SQ_PS3 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_PS3_PERF_SEL_INSTS_GDS | SQ_PS3 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_PS3_PERF_SEL_WAIT_INST_LDS | SQ_PS3 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_PS3_PERF_SEL_INST_CYCLES_VALU | SQ_PS3 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_PS3_PERF_SEL_INST_CYCLES_SALU | SQ_PS3 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_PS3_PERF_SEL_THREAD_CYCLES_VALU | SQ_PS3 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_PS3_PERF_SEL_LDS_BANK_CONFLICT | SQ_PS3 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| **SQ_LS** | - | - |
| SQ_LS0_PERF_SEL_WAVES | SQ_LS0 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_LS0_PERF_SEL_ITEMS | SQ_LS0 | Number of valid items per wave. (per-simd, global) |
| SQ_LS0_PERF_SEL_INSTS_VALU | SQ_LS0 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_LS0_PERF_SEL_INSTS_VMEM_WR | SQ_LS0 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS0_PERF_SEL_INSTS_VMEM_RD | SQ_LS0 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS0_PERF_SEL_INSTS_SALU | SQ_LS0 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_LS0_PERF_SEL_INSTS_SMEM | SQ_LS0 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_LS0_PERF_SEL_INSTS_FLAT | SQ_LS0 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_LS0_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_LS0 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_LS0_PERF_SEL_INSTS_LDS | SQ_LS0 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS0_PERF_SEL_INSTS_GDS | SQ_LS0 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_LS0_PERF_SEL_WAIT_INST_LDS | SQ_LS0 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_LS0_PERF_SEL_INST_CYCLES_VALU | SQ_LS0 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_LS0_PERF_SEL_INST_CYCLES_SALU | SQ_LS0 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_LS0_PERF_SEL_THREAD_CYCLES_VALU | SQ_LS0 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_LS0_PERF_SEL_LDS_BANK_CONFLICT | SQ_LS0 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_LS1_PERF_SEL_WAVES | SQ_LS1 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_LS1_PERF_SEL_ITEMS | SQ_LS1 | Number of valid items per wave. (per-simd, global) |
| SQ_LS1_PERF_SEL_INSTS_VALU | SQ_LS1 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_LS1_PERF_SEL_INSTS_VMEM_WR | SQ_LS1 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS1_PERF_SEL_INSTS_VMEM_RD | SQ_LS1 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS1_PERF_SEL_INSTS_SALU | SQ_LS1 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_LS1_PERF_SEL_INSTS_SMEM | SQ_LS1 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_LS1_PERF_SEL_INSTS_FLAT | SQ_LS1 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_LS1_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_LS1 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_LS1_PERF_SEL_INSTS_LDS | SQ_LS1 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS1_PERF_SEL_INSTS_GDS | SQ_LS1 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_LS1_PERF_SEL_WAIT_INST_LDS | SQ_LS1 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_LS1_PERF_SEL_INST_CYCLES_VALU | SQ_LS1 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_LS1_PERF_SEL_INST_CYCLES_SALU | SQ_LS1 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_LS1_PERF_SEL_THREAD_CYCLES_VALU | SQ_LS1 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_LS1_PERF_SEL_LDS_BANK_CONFLICT | SQ_LS1 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_LS2_PERF_SEL_WAVES | SQ_LS2 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_LS2_PERF_SEL_ITEMS | SQ_LS2 | Number of valid items per wave. (per-simd, global) |
| SQ_LS2_PERF_SEL_INSTS_VALU | SQ_LS2 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_LS2_PERF_SEL_INSTS_VMEM_WR | SQ_LS2 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS2_PERF_SEL_INSTS_VMEM_RD | SQ_LS2 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS2_PERF_SEL_INSTS_SALU | SQ_LS2 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_LS2_PERF_SEL_INSTS_SMEM | SQ_LS2 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_LS2_PERF_SEL_INSTS_FLAT | SQ_LS2 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_LS2_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_LS2 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_LS2_PERF_SEL_INSTS_LDS | SQ_LS2 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS2_PERF_SEL_INSTS_GDS | SQ_LS2 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_LS2_PERF_SEL_WAIT_INST_LDS | SQ_LS2 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_LS2_PERF_SEL_INST_CYCLES_VALU | SQ_LS2 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_LS2_PERF_SEL_INST_CYCLES_SALU | SQ_LS2 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_LS2_PERF_SEL_THREAD_CYCLES_VALU | SQ_LS2 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_LS2_PERF_SEL_LDS_BANK_CONFLICT | SQ_LS2 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_LS3_PERF_SEL_WAVES | SQ_LS3 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_LS3_PERF_SEL_ITEMS | SQ_LS3 | Number of valid items per wave. (per-simd, global) |
| SQ_LS3_PERF_SEL_INSTS_VALU | SQ_LS3 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_LS3_PERF_SEL_INSTS_VMEM_WR | SQ_LS3 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS3_PERF_SEL_INSTS_VMEM_RD | SQ_LS3 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS3_PERF_SEL_INSTS_SALU | SQ_LS3 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_LS3_PERF_SEL_INSTS_SMEM | SQ_LS3 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_LS3_PERF_SEL_INSTS_FLAT | SQ_LS3 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_LS3_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_LS3 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_LS3_PERF_SEL_INSTS_LDS | SQ_LS3 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_LS3_PERF_SEL_INSTS_GDS | SQ_LS3 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_LS3_PERF_SEL_WAIT_INST_LDS | SQ_LS3 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_LS3_PERF_SEL_INST_CYCLES_VALU | SQ_LS3 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_LS3_PERF_SEL_INST_CYCLES_SALU | SQ_LS3 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_LS3_PERF_SEL_THREAD_CYCLES_VALU | SQ_LS3 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_LS3_PERF_SEL_LDS_BANK_CONFLICT | SQ_LS3 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| **SQ_HS** | - | - |
| SQ_HS0_PERF_SEL_WAVES | SQ_HS0 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_HS0_PERF_SEL_ITEMS | SQ_HS0 | Number of valid items per wave. (per-simd, global) |
| SQ_HS0_PERF_SEL_INSTS_VALU | SQ_HS0 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_HS0_PERF_SEL_INSTS_VMEM_WR | SQ_HS0 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS0_PERF_SEL_INSTS_VMEM_RD | SQ_HS0 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS0_PERF_SEL_INSTS_SALU | SQ_HS0 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_HS0_PERF_SEL_INSTS_SMEM | SQ_HS0 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_HS0_PERF_SEL_INSTS_FLAT | SQ_HS0 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_HS0_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_HS0 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_HS0_PERF_SEL_INSTS_LDS | SQ_HS0 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS0_PERF_SEL_INSTS_GDS | SQ_HS0 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_HS0_PERF_SEL_WAIT_INST_LDS | SQ_HS0 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_HS0_PERF_SEL_INST_CYCLES_VALU | SQ_HS0 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_HS0_PERF_SEL_INST_CYCLES_SALU | SQ_HS0 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_HS0_PERF_SEL_THREAD_CYCLES_VALU | SQ_HS0 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_HS0_PERF_SEL_LDS_BANK_CONFLICT | SQ_HS0 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_HS1_PERF_SEL_WAVES | SQ_HS1 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_HS1_PERF_SEL_ITEMS | SQ_HS1 | Number of valid items per wave. (per-simd, global) |
| SQ_HS1_PERF_SEL_INSTS_VALU | SQ_HS1 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_HS1_PERF_SEL_INSTS_VMEM_WR | SQ_HS1 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS1_PERF_SEL_INSTS_VMEM_RD | SQ_HS1 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS1_PERF_SEL_INSTS_SALU | SQ_HS1 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_HS1_PERF_SEL_INSTS_SMEM | SQ_HS1 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_HS1_PERF_SEL_INSTS_FLAT | SQ_HS1 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_HS1_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_HS1 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_HS1_PERF_SEL_INSTS_LDS | SQ_HS1 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS1_PERF_SEL_INSTS_GDS | SQ_HS1 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_HS1_PERF_SEL_WAIT_INST_LDS | SQ_HS1 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_HS1_PERF_SEL_INST_CYCLES_VALU | SQ_HS1 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_HS1_PERF_SEL_INST_CYCLES_SALU | SQ_HS1 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_HS1_PERF_SEL_THREAD_CYCLES_VALU | SQ_HS1 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_HS1_PERF_SEL_LDS_BANK_CONFLICT | SQ_HS1 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_HS2_PERF_SEL_WAVES | SQ_HS2 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_HS2_PERF_SEL_ITEMS | SQ_HS2 | Number of valid items per wave. (per-simd, global) |
| SQ_HS2_PERF_SEL_INSTS_VALU | SQ_HS2 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_HS2_PERF_SEL_INSTS_VMEM_WR | SQ_HS2 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS2_PERF_SEL_INSTS_VMEM_RD | SQ_HS2 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS2_PERF_SEL_INSTS_SALU | SQ_HS2 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_HS2_PERF_SEL_INSTS_SMEM | SQ_HS2 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_HS2_PERF_SEL_INSTS_FLAT | SQ_HS2 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_HS2_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_HS2 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_HS2_PERF_SEL_INSTS_LDS | SQ_HS2 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS2_PERF_SEL_INSTS_GDS | SQ_HS2 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_HS2_PERF_SEL_WAIT_INST_LDS | SQ_HS2 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_HS2_PERF_SEL_INST_CYCLES_VALU | SQ_HS2 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_HS2_PERF_SEL_INST_CYCLES_SALU | SQ_HS2 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_HS2_PERF_SEL_THREAD_CYCLES_VALU | SQ_HS2 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_HS2_PERF_SEL_LDS_BANK_CONFLICT | SQ_HS2 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_HS3_PERF_SEL_WAVES | SQ_HS3 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_HS3_PERF_SEL_ITEMS | SQ_HS3 | Number of valid items per wave. (per-simd, global) |
| SQ_HS3_PERF_SEL_INSTS_VALU | SQ_HS3 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_HS3_PERF_SEL_INSTS_VMEM_WR | SQ_HS3 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS3_PERF_SEL_INSTS_VMEM_RD | SQ_HS3 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS3_PERF_SEL_INSTS_SALU | SQ_HS3 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_HS3_PERF_SEL_INSTS_SMEM | SQ_HS3 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_HS3_PERF_SEL_INSTS_FLAT | SQ_HS3 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_HS3_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_HS3 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_HS3_PERF_SEL_INSTS_LDS | SQ_HS3 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_HS3_PERF_SEL_INSTS_GDS | SQ_HS3 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_HS3_PERF_SEL_WAIT_INST_LDS | SQ_HS3 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_HS3_PERF_SEL_INST_CYCLES_VALU | SQ_HS3 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_HS3_PERF_SEL_INST_CYCLES_SALU | SQ_HS3 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_HS3_PERF_SEL_THREAD_CYCLES_VALU | SQ_HS3 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_HS3_PERF_SEL_LDS_BANK_CONFLICT | SQ_HS3 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| **SQ_CS** | - | - |
| SQ_CS0_PERF_SEL_WAVES | SQ_CS0 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_CS0_PERF_SEL_ITEMS | SQ_CS0 | Number of valid items per wave. (per-simd, global) |
| SQ_CS0_PERF_SEL_INSTS_VALU | SQ_CS0 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_CS0_PERF_SEL_INSTS_VMEM_WR | SQ_CS0 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS0_PERF_SEL_INSTS_VMEM_RD | SQ_CS0 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS0_PERF_SEL_INSTS_SALU | SQ_CS0 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_CS0_PERF_SEL_INSTS_SMEM | SQ_CS0 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_CS0_PERF_SEL_INSTS_FLAT | SQ_CS0 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_CS0_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_CS0 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_CS0_PERF_SEL_INSTS_LDS | SQ_CS0 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS0_PERF_SEL_INSTS_GDS | SQ_CS0 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_CS0_PERF_SEL_WAIT_INST_LDS | SQ_CS0 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_CS0_PERF_SEL_INST_CYCLES_VALU | SQ_CS0 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_CS0_PERF_SEL_INST_CYCLES_SALU | SQ_CS0 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_CS0_PERF_SEL_THREAD_CYCLES_VALU | SQ_CS0 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_CS0_PERF_SEL_LDS_BANK_CONFLICT | SQ_CS0 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_CS1_PERF_SEL_WAVES | SQ_CS1 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_CS1_PERF_SEL_ITEMS | SQ_CS1 | Number of valid items per wave. (per-simd, global) |
| SQ_CS1_PERF_SEL_INSTS_VALU | SQ_CS1 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_CS1_PERF_SEL_INSTS_VMEM_WR | SQ_CS1 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS1_PERF_SEL_INSTS_VMEM_RD | SQ_CS1 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS1_PERF_SEL_INSTS_SALU | SQ_CS1 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_CS1_PERF_SEL_INSTS_SMEM | SQ_CS1 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_CS1_PERF_SEL_INSTS_FLAT | SQ_CS1 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_CS1_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_CS1 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_CS1_PERF_SEL_INSTS_LDS | SQ_CS1 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS1_PERF_SEL_INSTS_GDS | SQ_CS1 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_CS1_PERF_SEL_WAIT_INST_LDS | SQ_CS1 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_CS1_PERF_SEL_INST_CYCLES_VALU | SQ_CS1 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_CS1_PERF_SEL_INST_CYCLES_SALU | SQ_CS1 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_CS1_PERF_SEL_THREAD_CYCLES_VALU | SQ_CS1 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_CS1_PERF_SEL_LDS_BANK_CONFLICT | SQ_CS1 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_CS2_PERF_SEL_WAVES | SQ_CS2 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_CS2_PERF_SEL_ITEMS | SQ_CS2 | Number of valid items per wave. (per-simd, global) |
| SQ_CS2_PERF_SEL_INSTS_VALU | SQ_CS2 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_CS2_PERF_SEL_INSTS_VMEM_WR | SQ_CS2 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS2_PERF_SEL_INSTS_VMEM_RD | SQ_CS2 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS2_PERF_SEL_INSTS_SALU | SQ_CS2 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_CS2_PERF_SEL_INSTS_SMEM | SQ_CS2 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_CS2_PERF_SEL_INSTS_FLAT | SQ_CS2 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_CS2_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_CS2 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_CS2_PERF_SEL_INSTS_LDS | SQ_CS2 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS2_PERF_SEL_INSTS_GDS | SQ_CS2 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_CS2_PERF_SEL_WAIT_INST_LDS | SQ_CS2 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_CS2_PERF_SEL_INST_CYCLES_VALU | SQ_CS2 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_CS2_PERF_SEL_INST_CYCLES_SALU | SQ_CS2 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_CS2_PERF_SEL_THREAD_CYCLES_VALU | SQ_CS2 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_CS2_PERF_SEL_LDS_BANK_CONFLICT | SQ_CS2 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| SQ_CS3_PERF_SEL_WAVES | SQ_CS3 | Count number of waves sent to SQs. (per-simd, emulated, global) |
| SQ_CS3_PERF_SEL_ITEMS | SQ_CS3 | Number of valid items per wave. (per-simd, global) |
| SQ_CS3_PERF_SEL_INSTS_VALU | SQ_CS3 | Number of VALU instructions issued. (per-simd, emulated) |
| SQ_CS3_PERF_SEL_INSTS_VMEM_WR | SQ_CS3 | Number of VMEM write instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS3_PERF_SEL_INSTS_VMEM_RD | SQ_CS3 | Number of VMEM read instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS3_PERF_SEL_INSTS_SALU | SQ_CS3 | Number of SALU instructions issued. (per-simd, emulated) |
| SQ_CS3_PERF_SEL_INSTS_SMEM | SQ_CS3 | Number of SMEM read instructions issued. (per-simd, emulated) |
| SQ_CS3_PERF_SEL_INSTS_FLAT | SQ_CS3 | Number of FLAT instructions issued. (per-simd, emulated) |
| SQ_CS3_PERF_SEL_INSTS_FLAT_LDS_ONLY | SQ_CS3 | Number of FLAT instructions issued that read/wrote only from/to LDS (only works if EARLY_TA_DONE is enabled). (per-simd, emulated) |
| SQ_CS3_PERF_SEL_INSTS_LDS | SQ_CS3 | Number of LDS instructions issued (including FLAT). (per-simd, emulated) |
| SQ_CS3_PERF_SEL_INSTS_GDS | SQ_CS3 | Number of GDS instructions issued. (per-simd, emulated) |
| SQ_CS3_PERF_SEL_WAIT_INST_LDS | SQ_CS3 | Number of wave-cycles spent waiting for LDS instruction issue. In units of 4 cycles. (per-simd, nondeterministic) |
| SQ_CS3_PERF_SEL_INST_CYCLES_VALU | SQ_CS3 | Number of cycles needed to execute VALU instructions. (per-simd, emulated) |
| SQ_CS3_PERF_SEL_INST_CYCLES_SALU | SQ_CS3 | Number of cycles needed to execute non-memory read scalar operations. (per-simd, emulated) |
| SQ_CS3_PERF_SEL_THREAD_CYCLES_VALU | SQ_CS3 | Number of thread-cycles used to execute VALU operations (similar to INST_CYCLES_VALU but multiplied by number of active threads). (per-simd) |
| SQ_CS3_PERF_SEL_LDS_BANK_CONFLICT | SQ_CS3 | Number of cycles LDS is stalled by bank conflicts. (emulated) |
| **SX** | - | - |
| SX0_PERF_SEL_DB0_PIXELS | SX0 | Number of pixels sent to the DB0 |
| SX0_PERF_SEL_DB0_PIXEL_STALL | SX0 | Number of cycles where pixel traffic is stalled due to the DB0 |
| SX0_PERF_SEL_DB1_PIXELS | SX0 | Number of pixels sent to the DB1 |
| SX0_PERF_SEL_DB1_PIXEL_STALL | SX0 | Number of cycles where pixel traffic is stalled due to the DB1 |
| SX0_PERF_SEL_DB2_PIXELS | SX0 | Number of pixels sent to the DB2 |
| SX0_PERF_SEL_DB2_PIXEL_STALL | SX0 | Number of cycles where pixel traffic is stalled due to the DB2 |
| SX0_PERF_SEL_DB3_PIXELS | SX0 | Number of pixels sent to the DB3 |
| SX0_PERF_SEL_DB3_PIXEL_STALL | SX0 | Number of cycles where pixel traffic is stalled due to the DB3 |
| SX1_PERF_SEL_DB0_PIXELS | SX1 | Number of pixels sent to the DB0 |
| SX1_PERF_SEL_DB0_PIXEL_STALL | SX1 | Number of cycles where pixel traffic is stalled due to the DB0 |
| SX1_PERF_SEL_DB1_PIXELS | SX1 | Number of pixels sent to the DB1 |
| SX1_PERF_SEL_DB1_PIXEL_STALL | SX1 | Number of cycles where pixel traffic is stalled due to the DB1 |
| SX1_PERF_SEL_DB2_PIXELS | SX1 | Number of pixels sent to the DB2 |
| SX1_PERF_SEL_DB2_PIXEL_STALL | SX1 | Number of cycles where pixel traffic is stalled due to the DB2 |
| SX1_PERF_SEL_DB3_PIXELS | SX1 | Number of pixels sent to the DB3 |
| SX1_PERF_SEL_DB3_PIXEL_STALL | SX1 | Number of cycles where pixel traffic is stalled due to the DB3 |
| SX2_PERF_SEL_DB0_PIXELS | SX2 | Number of pixels sent to the DB0 |
| SX2_PERF_SEL_DB0_PIXEL_STALL | SX2 | Number of cycles where pixel traffic is stalled due to the DB0 |
| SX2_PERF_SEL_DB1_PIXELS | SX2 | Number of pixels sent to the DB1 |
| SX2_PERF_SEL_DB1_PIXEL_STALL | SX2 | Number of cycles where pixel traffic is stalled due to the DB1 |
| SX2_PERF_SEL_DB2_PIXELS | SX2 | Number of pixels sent to the DB2 |
| SX2_PERF_SEL_DB2_PIXEL_STALL | SX2 | Number of cycles where pixel traffic is stalled due to the DB2 |
| SX2_PERF_SEL_DB3_PIXELS | SX2 | Number of pixels sent to the DB3 |
| SX2_PERF_SEL_DB3_PIXEL_STALL | SX2 | Number of cycles where pixel traffic is stalled due to the DB3 |
| SX3_PERF_SEL_DB0_PIXELS | SX3 | Number of pixels sent to the DB0 |
| SX3_PERF_SEL_DB0_PIXEL_STALL | SX3 | Number of cycles where pixel traffic is stalled due to the DB0 |
| SX3_PERF_SEL_DB1_PIXELS | SX3 | Number of pixels sent to the DB1 |
| SX3_PERF_SEL_DB1_PIXEL_STALL | SX3 | Number of cycles where pixel traffic is stalled due to the DB1 |
| SX3_PERF_SEL_DB2_PIXELS | SX3 | Number of pixels sent to the DB2 |
| SX3_PERF_SEL_DB2_PIXEL_STALL | SX3 | Number of cycles where pixel traffic is stalled due to the DB2 |
| SX3_PERF_SEL_DB3_PIXELS | SX3 | Number of pixels sent to the DB3 |
| SX3_PERF_SEL_DB3_PIXEL_STALL | SX3 | Number of cycles where pixel traffic is stalled due to the DB3 |
| **TA** | - | - |
| TA0_PERF_SEL_TA_BUSY | TA0 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA0_PERF_SEL_MIP_1_CYCLE_PIXELS | TA0 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA0_PERF_SEL_MIP_2_CYCLE_PIXELS | TA0 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA0_PERF_SEL_VOL_1_CYCLE_PIXELS | TA0 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA0_PERF_SEL_VOL_2_CYCLE_PIXELS | TA0 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA0_PERF_SEL_ANISO_1_CYCLE_QUADS | TA0 | Number of quads requiring 1 aniso sample. |
| TA0_PERF_SEL_ANISO_2_CYCLE_QUADS | TA0 | Number of quads requiring 2 aniso sample. |
| TA0_PERF_SEL_ANISO_4_CYCLE_QUADS | TA0 | Number of quads requiring 4 aniso sample. |
| TA0_PERF_SEL_ANISO_6_CYCLE_QUADS | TA0 | Number of quads requiring 6 aniso sample. |
| TA0_PERF_SEL_ANISO_8_CYCLE_QUADS | TA0 | Number of quads requiring 8 aniso sample. |
| TA0_PERF_SEL_ANISO_10_CYCLE_QUADS | TA0 | Number of quads requiring 10 aniso sample. |
| TA0_PERF_SEL_ANISO_12_CYCLE_QUADS | TA0 | Number of quads requiring 12 aniso sample. |
| TA0_PERF_SEL_ANISO_14_CYCLE_QUADS | TA0 | Number of quads requiring 14 aniso sample. |
| TA0_PERF_SEL_ANISO_16_CYCLE_QUADS | TA0 | Number of quads requiring 16 aniso sample. |
| TA0_PERF_SEL_FLAT_READ_WAVEFRONTS | TA0 | Number of flat opcode reads processed by the TA. |
| TA0_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA0 | Number of flat opcode writes processed by the TA. |
| TA1_PERF_SEL_TA_BUSY | TA1 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA1_PERF_SEL_MIP_1_CYCLE_PIXELS | TA1 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA1_PERF_SEL_MIP_2_CYCLE_PIXELS | TA1 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA1_PERF_SEL_VOL_1_CYCLE_PIXELS | TA1 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA1_PERF_SEL_VOL_2_CYCLE_PIXELS | TA1 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA1_PERF_SEL_ANISO_1_CYCLE_QUADS | TA1 | Number of quads requiring 1 aniso sample. |
| TA1_PERF_SEL_ANISO_2_CYCLE_QUADS | TA1 | Number of quads requiring 2 aniso sample. |
| TA1_PERF_SEL_ANISO_4_CYCLE_QUADS | TA1 | Number of quads requiring 4 aniso sample. |
| TA1_PERF_SEL_ANISO_6_CYCLE_QUADS | TA1 | Number of quads requiring 6 aniso sample. |
| TA1_PERF_SEL_ANISO_8_CYCLE_QUADS | TA1 | Number of quads requiring 8 aniso sample. |
| TA1_PERF_SEL_ANISO_10_CYCLE_QUADS | TA1 | Number of quads requiring 10 aniso sample. |
| TA1_PERF_SEL_ANISO_12_CYCLE_QUADS | TA1 | Number of quads requiring 12 aniso sample. |
| TA1_PERF_SEL_ANISO_14_CYCLE_QUADS | TA1 | Number of quads requiring 14 aniso sample. |
| TA1_PERF_SEL_ANISO_16_CYCLE_QUADS | TA1 | Number of quads requiring 16 aniso sample. |
| TA1_PERF_SEL_FLAT_READ_WAVEFRONTS | TA1 | Number of flat opcode reads processed by the TA. |
| TA1_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA1 | Number of flat opcode writes processed by the TA. |
| TA2_PERF_SEL_TA_BUSY | TA2 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA2_PERF_SEL_MIP_1_CYCLE_PIXELS | TA2 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA2_PERF_SEL_MIP_2_CYCLE_PIXELS | TA2 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA2_PERF_SEL_VOL_1_CYCLE_PIXELS | TA2 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA2_PERF_SEL_VOL_2_CYCLE_PIXELS | TA2 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA2_PERF_SEL_ANISO_1_CYCLE_QUADS | TA2 | Number of quads requiring 1 aniso sample. |
| TA2_PERF_SEL_ANISO_2_CYCLE_QUADS | TA2 | Number of quads requiring 2 aniso sample. |
| TA2_PERF_SEL_ANISO_4_CYCLE_QUADS | TA2 | Number of quads requiring 4 aniso sample. |
| TA2_PERF_SEL_ANISO_6_CYCLE_QUADS | TA2 | Number of quads requiring 6 aniso sample. |
| TA2_PERF_SEL_ANISO_8_CYCLE_QUADS | TA2 | Number of quads requiring 8 aniso sample. |
| TA2_PERF_SEL_ANISO_10_CYCLE_QUADS | TA2 | Number of quads requiring 10 aniso sample. |
| TA2_PERF_SEL_ANISO_12_CYCLE_QUADS | TA2 | Number of quads requiring 12 aniso sample. |
| TA2_PERF_SEL_ANISO_14_CYCLE_QUADS | TA2 | Number of quads requiring 14 aniso sample. |
| TA2_PERF_SEL_ANISO_16_CYCLE_QUADS | TA2 | Number of quads requiring 16 aniso sample. |
| TA2_PERF_SEL_FLAT_READ_WAVEFRONTS | TA2 | Number of flat opcode reads processed by the TA. |
| TA2_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA2 | Number of flat opcode writes processed by the TA. |
| TA3_PERF_SEL_TA_BUSY | TA3 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA3_PERF_SEL_MIP_1_CYCLE_PIXELS | TA3 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA3_PERF_SEL_MIP_2_CYCLE_PIXELS | TA3 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA3_PERF_SEL_VOL_1_CYCLE_PIXELS | TA3 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA3_PERF_SEL_VOL_2_CYCLE_PIXELS | TA3 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA3_PERF_SEL_ANISO_1_CYCLE_QUADS | TA3 | Number of quads requiring 1 aniso sample. |
| TA3_PERF_SEL_ANISO_2_CYCLE_QUADS | TA3 | Number of quads requiring 2 aniso sample. |
| TA3_PERF_SEL_ANISO_4_CYCLE_QUADS | TA3 | Number of quads requiring 4 aniso sample. |
| TA3_PERF_SEL_ANISO_6_CYCLE_QUADS | TA3 | Number of quads requiring 6 aniso sample. |
| TA3_PERF_SEL_ANISO_8_CYCLE_QUADS | TA3 | Number of quads requiring 8 aniso sample. |
| TA3_PERF_SEL_ANISO_10_CYCLE_QUADS | TA3 | Number of quads requiring 10 aniso sample. |
| TA3_PERF_SEL_ANISO_12_CYCLE_QUADS | TA3 | Number of quads requiring 12 aniso sample. |
| TA3_PERF_SEL_ANISO_14_CYCLE_QUADS | TA3 | Number of quads requiring 14 aniso sample. |
| TA3_PERF_SEL_ANISO_16_CYCLE_QUADS | TA3 | Number of quads requiring 16 aniso sample. |
| TA3_PERF_SEL_FLAT_READ_WAVEFRONTS | TA3 | Number of flat opcode reads processed by the TA. |
| TA3_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA3 | Number of flat opcode writes processed by the TA. |
| TA4_PERF_SEL_TA_BUSY | TA4 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA4_PERF_SEL_MIP_1_CYCLE_PIXELS | TA4 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA4_PERF_SEL_MIP_2_CYCLE_PIXELS | TA4 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA4_PERF_SEL_VOL_1_CYCLE_PIXELS | TA4 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA4_PERF_SEL_VOL_2_CYCLE_PIXELS | TA4 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA4_PERF_SEL_ANISO_1_CYCLE_QUADS | TA4 | Number of quads requiring 1 aniso sample. |
| TA4_PERF_SEL_ANISO_2_CYCLE_QUADS | TA4 | Number of quads requiring 2 aniso sample. |
| TA4_PERF_SEL_ANISO_4_CYCLE_QUADS | TA4 | Number of quads requiring 4 aniso sample. |
| TA4_PERF_SEL_ANISO_6_CYCLE_QUADS | TA4 | Number of quads requiring 6 aniso sample. |
| TA4_PERF_SEL_ANISO_8_CYCLE_QUADS | TA4 | Number of quads requiring 8 aniso sample. |
| TA4_PERF_SEL_ANISO_10_CYCLE_QUADS | TA4 | Number of quads requiring 10 aniso sample. |
| TA4_PERF_SEL_ANISO_12_CYCLE_QUADS | TA4 | Number of quads requiring 12 aniso sample. |
| TA4_PERF_SEL_ANISO_14_CYCLE_QUADS | TA4 | Number of quads requiring 14 aniso sample. |
| TA4_PERF_SEL_ANISO_16_CYCLE_QUADS | TA4 | Number of quads requiring 16 aniso sample. |
| TA4_PERF_SEL_FLAT_READ_WAVEFRONTS | TA4 | Number of flat opcode reads processed by the TA. |
| TA4_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA4 | Number of flat opcode writes processed by the TA. |
| TA5_PERF_SEL_TA_BUSY | TA5 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA5_PERF_SEL_MIP_1_CYCLE_PIXELS | TA5 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA5_PERF_SEL_MIP_2_CYCLE_PIXELS | TA5 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA5_PERF_SEL_VOL_1_CYCLE_PIXELS | TA5 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA5_PERF_SEL_VOL_2_CYCLE_PIXELS | TA5 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA5_PERF_SEL_ANISO_1_CYCLE_QUADS | TA5 | Number of quads requiring 1 aniso sample. |
| TA5_PERF_SEL_ANISO_2_CYCLE_QUADS | TA5 | Number of quads requiring 2 aniso sample. |
| TA5_PERF_SEL_ANISO_4_CYCLE_QUADS | TA5 | Number of quads requiring 4 aniso sample. |
| TA5_PERF_SEL_ANISO_6_CYCLE_QUADS | TA5 | Number of quads requiring 6 aniso sample. |
| TA5_PERF_SEL_ANISO_8_CYCLE_QUADS | TA5 | Number of quads requiring 8 aniso sample. |
| TA5_PERF_SEL_ANISO_10_CYCLE_QUADS | TA5 | Number of quads requiring 10 aniso sample. |
| TA5_PERF_SEL_ANISO_12_CYCLE_QUADS | TA5 | Number of quads requiring 12 aniso sample. |
| TA5_PERF_SEL_ANISO_14_CYCLE_QUADS | TA5 | Number of quads requiring 14 aniso sample. |
| TA5_PERF_SEL_ANISO_16_CYCLE_QUADS | TA5 | Number of quads requiring 16 aniso sample. |
| TA5_PERF_SEL_FLAT_READ_WAVEFRONTS | TA5 | Number of flat opcode reads processed by the TA. |
| TA5_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA5 | Number of flat opcode writes processed by the TA. |
| TA6_PERF_SEL_TA_BUSY | TA6 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA6_PERF_SEL_MIP_1_CYCLE_PIXELS | TA6 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA6_PERF_SEL_MIP_2_CYCLE_PIXELS | TA6 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA6_PERF_SEL_VOL_1_CYCLE_PIXELS | TA6 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA6_PERF_SEL_VOL_2_CYCLE_PIXELS | TA6 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA6_PERF_SEL_ANISO_1_CYCLE_QUADS | TA6 | Number of quads requiring 1 aniso sample. |
| TA6_PERF_SEL_ANISO_2_CYCLE_QUADS | TA6 | Number of quads requiring 2 aniso sample. |
| TA6_PERF_SEL_ANISO_4_CYCLE_QUADS | TA6 | Number of quads requiring 4 aniso sample. |
| TA6_PERF_SEL_ANISO_6_CYCLE_QUADS | TA6 | Number of quads requiring 6 aniso sample. |
| TA6_PERF_SEL_ANISO_8_CYCLE_QUADS | TA6 | Number of quads requiring 8 aniso sample. |
| TA6_PERF_SEL_ANISO_10_CYCLE_QUADS | TA6 | Number of quads requiring 10 aniso sample. |
| TA6_PERF_SEL_ANISO_12_CYCLE_QUADS | TA6 | Number of quads requiring 12 aniso sample. |
| TA6_PERF_SEL_ANISO_14_CYCLE_QUADS | TA6 | Number of quads requiring 14 aniso sample. |
| TA6_PERF_SEL_ANISO_16_CYCLE_QUADS | TA6 | Number of quads requiring 16 aniso sample. |
| TA6_PERF_SEL_FLAT_READ_WAVEFRONTS | TA6 | Number of flat opcode reads processed by the TA. |
| TA6_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA6 | Number of flat opcode writes processed by the TA. |
| TA7_PERF_SEL_TA_BUSY | TA7 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA7_PERF_SEL_MIP_1_CYCLE_PIXELS | TA7 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA7_PERF_SEL_MIP_2_CYCLE_PIXELS | TA7 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA7_PERF_SEL_VOL_1_CYCLE_PIXELS | TA7 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA7_PERF_SEL_VOL_2_CYCLE_PIXELS | TA7 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA7_PERF_SEL_ANISO_1_CYCLE_QUADS | TA7 | Number of quads requiring 1 aniso sample. |
| TA7_PERF_SEL_ANISO_2_CYCLE_QUADS | TA7 | Number of quads requiring 2 aniso sample. |
| TA7_PERF_SEL_ANISO_4_CYCLE_QUADS | TA7 | Number of quads requiring 4 aniso sample. |
| TA7_PERF_SEL_ANISO_6_CYCLE_QUADS | TA7 | Number of quads requiring 6 aniso sample. |
| TA7_PERF_SEL_ANISO_8_CYCLE_QUADS | TA7 | Number of quads requiring 8 aniso sample. |
| TA7_PERF_SEL_ANISO_10_CYCLE_QUADS | TA7 | Number of quads requiring 10 aniso sample. |
| TA7_PERF_SEL_ANISO_12_CYCLE_QUADS | TA7 | Number of quads requiring 12 aniso sample. |
| TA7_PERF_SEL_ANISO_14_CYCLE_QUADS | TA7 | Number of quads requiring 14 aniso sample. |
| TA7_PERF_SEL_ANISO_16_CYCLE_QUADS | TA7 | Number of quads requiring 16 aniso sample. |
| TA7_PERF_SEL_FLAT_READ_WAVEFRONTS | TA7 | Number of flat opcode reads processed by the TA. |
| TA7_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA7 | Number of flat opcode writes processed by the TA. |
| TA8_PERF_SEL_TA_BUSY | TA8 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA8_PERF_SEL_MIP_1_CYCLE_PIXELS | TA8 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA8_PERF_SEL_MIP_2_CYCLE_PIXELS | TA8 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA8_PERF_SEL_VOL_1_CYCLE_PIXELS | TA8 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA8_PERF_SEL_VOL_2_CYCLE_PIXELS | TA8 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA8_PERF_SEL_ANISO_1_CYCLE_QUADS | TA8 | Number of quads requiring 1 aniso sample. |
| TA8_PERF_SEL_ANISO_2_CYCLE_QUADS | TA8 | Number of quads requiring 2 aniso sample. |
| TA8_PERF_SEL_ANISO_4_CYCLE_QUADS | TA8 | Number of quads requiring 4 aniso sample. |
| TA8_PERF_SEL_ANISO_6_CYCLE_QUADS | TA8 | Number of quads requiring 6 aniso sample. |
| TA8_PERF_SEL_ANISO_8_CYCLE_QUADS | TA8 | Number of quads requiring 8 aniso sample. |
| TA8_PERF_SEL_ANISO_10_CYCLE_QUADS | TA8 | Number of quads requiring 10 aniso sample. |
| TA8_PERF_SEL_ANISO_12_CYCLE_QUADS | TA8 | Number of quads requiring 12 aniso sample. |
| TA8_PERF_SEL_ANISO_14_CYCLE_QUADS | TA8 | Number of quads requiring 14 aniso sample. |
| TA8_PERF_SEL_ANISO_16_CYCLE_QUADS | TA8 | Number of quads requiring 16 aniso sample. |
| TA8_PERF_SEL_FLAT_READ_WAVEFRONTS | TA8 | Number of flat opcode reads processed by the TA. |
| TA8_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA8 | Number of flat opcode writes processed by the TA. |
| TA9_PERF_SEL_TA_BUSY | TA9 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA9_PERF_SEL_MIP_1_CYCLE_PIXELS | TA9 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA9_PERF_SEL_MIP_2_CYCLE_PIXELS | TA9 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA9_PERF_SEL_VOL_1_CYCLE_PIXELS | TA9 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA9_PERF_SEL_VOL_2_CYCLE_PIXELS | TA9 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA9_PERF_SEL_ANISO_1_CYCLE_QUADS | TA9 | Number of quads requiring 1 aniso sample. |
| TA9_PERF_SEL_ANISO_2_CYCLE_QUADS | TA9 | Number of quads requiring 2 aniso sample. |
| TA9_PERF_SEL_ANISO_4_CYCLE_QUADS | TA9 | Number of quads requiring 4 aniso sample. |
| TA9_PERF_SEL_ANISO_6_CYCLE_QUADS | TA9 | Number of quads requiring 6 aniso sample. |
| TA9_PERF_SEL_ANISO_8_CYCLE_QUADS | TA9 | Number of quads requiring 8 aniso sample. |
| TA9_PERF_SEL_ANISO_10_CYCLE_QUADS | TA9 | Number of quads requiring 10 aniso sample. |
| TA9_PERF_SEL_ANISO_12_CYCLE_QUADS | TA9 | Number of quads requiring 12 aniso sample. |
| TA9_PERF_SEL_ANISO_14_CYCLE_QUADS | TA9 | Number of quads requiring 14 aniso sample. |
| TA9_PERF_SEL_ANISO_16_CYCLE_QUADS | TA9 | Number of quads requiring 16 aniso sample. |
| TA9_PERF_SEL_FLAT_READ_WAVEFRONTS | TA9 | Number of flat opcode reads processed by the TA. |
| TA9_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA9 | Number of flat opcode writes processed by the TA. |
| TA10_PERF_SEL_TA_BUSY | TA10 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA10_PERF_SEL_MIP_1_CYCLE_PIXELS | TA10 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA10_PERF_SEL_MIP_2_CYCLE_PIXELS | TA10 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA10_PERF_SEL_VOL_1_CYCLE_PIXELS | TA10 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA10_PERF_SEL_VOL_2_CYCLE_PIXELS | TA10 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA10_PERF_SEL_ANISO_1_CYCLE_QUADS | TA10 | Number of quads requiring 1 aniso sample. |
| TA10_PERF_SEL_ANISO_2_CYCLE_QUADS | TA10 | Number of quads requiring 2 aniso sample. |
| TA10_PERF_SEL_ANISO_4_CYCLE_QUADS | TA10 | Number of quads requiring 4 aniso sample. |
| TA10_PERF_SEL_ANISO_6_CYCLE_QUADS | TA10 | Number of quads requiring 6 aniso sample. |
| TA10_PERF_SEL_ANISO_8_CYCLE_QUADS | TA10 | Number of quads requiring 8 aniso sample. |
| TA10_PERF_SEL_ANISO_10_CYCLE_QUADS | TA10 | Number of quads requiring 10 aniso sample. |
| TA10_PERF_SEL_ANISO_12_CYCLE_QUADS | TA10 | Number of quads requiring 12 aniso sample. |
| TA10_PERF_SEL_ANISO_14_CYCLE_QUADS | TA10 | Number of quads requiring 14 aniso sample. |
| TA10_PERF_SEL_ANISO_16_CYCLE_QUADS | TA10 | Number of quads requiring 16 aniso sample. |
| TA10_PERF_SEL_FLAT_READ_WAVEFRONTS | TA10 | Number of flat opcode reads processed by the TA. |
| TA10_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA10 | Number of flat opcode writes processed by the TA. |
| TA11_PERF_SEL_TA_BUSY | TA11 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA11_PERF_SEL_MIP_1_CYCLE_PIXELS | TA11 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA11_PERF_SEL_MIP_2_CYCLE_PIXELS | TA11 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA11_PERF_SEL_VOL_1_CYCLE_PIXELS | TA11 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA11_PERF_SEL_VOL_2_CYCLE_PIXELS | TA11 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA11_PERF_SEL_ANISO_1_CYCLE_QUADS | TA11 | Number of quads requiring 1 aniso sample. |
| TA11_PERF_SEL_ANISO_2_CYCLE_QUADS | TA11 | Number of quads requiring 2 aniso sample. |
| TA11_PERF_SEL_ANISO_4_CYCLE_QUADS | TA11 | Number of quads requiring 4 aniso sample. |
| TA11_PERF_SEL_ANISO_6_CYCLE_QUADS | TA11 | Number of quads requiring 6 aniso sample. |
| TA11_PERF_SEL_ANISO_8_CYCLE_QUADS | TA11 | Number of quads requiring 8 aniso sample. |
| TA11_PERF_SEL_ANISO_10_CYCLE_QUADS | TA11 | Number of quads requiring 10 aniso sample. |
| TA11_PERF_SEL_ANISO_12_CYCLE_QUADS | TA11 | Number of quads requiring 12 aniso sample. |
| TA11_PERF_SEL_ANISO_14_CYCLE_QUADS | TA11 | Number of quads requiring 14 aniso sample. |
| TA11_PERF_SEL_ANISO_16_CYCLE_QUADS | TA11 | Number of quads requiring 16 aniso sample. |
| TA11_PERF_SEL_FLAT_READ_WAVEFRONTS | TA11 | Number of flat opcode reads processed by the TA. |
| TA11_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA11 | Number of flat opcode writes processed by the TA. |
| TA12_PERF_SEL_TA_BUSY | TA12 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA12_PERF_SEL_MIP_1_CYCLE_PIXELS | TA12 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA12_PERF_SEL_MIP_2_CYCLE_PIXELS | TA12 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA12_PERF_SEL_VOL_1_CYCLE_PIXELS | TA12 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA12_PERF_SEL_VOL_2_CYCLE_PIXELS | TA12 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA12_PERF_SEL_ANISO_1_CYCLE_QUADS | TA12 | Number of quads requiring 1 aniso sample. |
| TA12_PERF_SEL_ANISO_2_CYCLE_QUADS | TA12 | Number of quads requiring 2 aniso sample. |
| TA12_PERF_SEL_ANISO_4_CYCLE_QUADS | TA12 | Number of quads requiring 4 aniso sample. |
| TA12_PERF_SEL_ANISO_6_CYCLE_QUADS | TA12 | Number of quads requiring 6 aniso sample. |
| TA12_PERF_SEL_ANISO_8_CYCLE_QUADS | TA12 | Number of quads requiring 8 aniso sample. |
| TA12_PERF_SEL_ANISO_10_CYCLE_QUADS | TA12 | Number of quads requiring 10 aniso sample. |
| TA12_PERF_SEL_ANISO_12_CYCLE_QUADS | TA12 | Number of quads requiring 12 aniso sample. |
| TA12_PERF_SEL_ANISO_14_CYCLE_QUADS | TA12 | Number of quads requiring 14 aniso sample. |
| TA12_PERF_SEL_ANISO_16_CYCLE_QUADS | TA12 | Number of quads requiring 16 aniso sample. |
| TA12_PERF_SEL_FLAT_READ_WAVEFRONTS | TA12 | Number of flat opcode reads processed by the TA. |
| TA12_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA12 | Number of flat opcode writes processed by the TA. |
| TA13_PERF_SEL_TA_BUSY | TA13 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA13_PERF_SEL_MIP_1_CYCLE_PIXELS | TA13 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA13_PERF_SEL_MIP_2_CYCLE_PIXELS | TA13 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA13_PERF_SEL_VOL_1_CYCLE_PIXELS | TA13 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA13_PERF_SEL_VOL_2_CYCLE_PIXELS | TA13 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA13_PERF_SEL_ANISO_1_CYCLE_QUADS | TA13 | Number of quads requiring 1 aniso sample. |
| TA13_PERF_SEL_ANISO_2_CYCLE_QUADS | TA13 | Number of quads requiring 2 aniso sample. |
| TA13_PERF_SEL_ANISO_4_CYCLE_QUADS | TA13 | Number of quads requiring 4 aniso sample. |
| TA13_PERF_SEL_ANISO_6_CYCLE_QUADS | TA13 | Number of quads requiring 6 aniso sample. |
| TA13_PERF_SEL_ANISO_8_CYCLE_QUADS | TA13 | Number of quads requiring 8 aniso sample. |
| TA13_PERF_SEL_ANISO_10_CYCLE_QUADS | TA13 | Number of quads requiring 10 aniso sample. |
| TA13_PERF_SEL_ANISO_12_CYCLE_QUADS | TA13 | Number of quads requiring 12 aniso sample. |
| TA13_PERF_SEL_ANISO_14_CYCLE_QUADS | TA13 | Number of quads requiring 14 aniso sample. |
| TA13_PERF_SEL_ANISO_16_CYCLE_QUADS | TA13 | Number of quads requiring 16 aniso sample. |
| TA13_PERF_SEL_FLAT_READ_WAVEFRONTS | TA13 | Number of flat opcode reads processed by the TA. |
| TA13_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA13 | Number of flat opcode writes processed by the TA. |
| TA14_PERF_SEL_TA_BUSY | TA14 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA14_PERF_SEL_MIP_1_CYCLE_PIXELS | TA14 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA14_PERF_SEL_MIP_2_CYCLE_PIXELS | TA14 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA14_PERF_SEL_VOL_1_CYCLE_PIXELS | TA14 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA14_PERF_SEL_VOL_2_CYCLE_PIXELS | TA14 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA14_PERF_SEL_ANISO_1_CYCLE_QUADS | TA14 | Number of quads requiring 1 aniso sample. |
| TA14_PERF_SEL_ANISO_2_CYCLE_QUADS | TA14 | Number of quads requiring 2 aniso sample. |
| TA14_PERF_SEL_ANISO_4_CYCLE_QUADS | TA14 | Number of quads requiring 4 aniso sample. |
| TA14_PERF_SEL_ANISO_6_CYCLE_QUADS | TA14 | Number of quads requiring 6 aniso sample. |
| TA14_PERF_SEL_ANISO_8_CYCLE_QUADS | TA14 | Number of quads requiring 8 aniso sample. |
| TA14_PERF_SEL_ANISO_10_CYCLE_QUADS | TA14 | Number of quads requiring 10 aniso sample. |
| TA14_PERF_SEL_ANISO_12_CYCLE_QUADS | TA14 | Number of quads requiring 12 aniso sample. |
| TA14_PERF_SEL_ANISO_14_CYCLE_QUADS | TA14 | Number of quads requiring 14 aniso sample. |
| TA14_PERF_SEL_ANISO_16_CYCLE_QUADS | TA14 | Number of quads requiring 16 aniso sample. |
| TA14_PERF_SEL_FLAT_READ_WAVEFRONTS | TA14 | Number of flat opcode reads processed by the TA. |
| TA14_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA14 | Number of flat opcode writes processed by the TA. |
| TA15_PERF_SEL_TA_BUSY | TA15 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA15_PERF_SEL_MIP_1_CYCLE_PIXELS | TA15 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA15_PERF_SEL_MIP_2_CYCLE_PIXELS | TA15 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA15_PERF_SEL_VOL_1_CYCLE_PIXELS | TA15 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA15_PERF_SEL_VOL_2_CYCLE_PIXELS | TA15 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA15_PERF_SEL_ANISO_1_CYCLE_QUADS | TA15 | Number of quads requiring 1 aniso sample. |
| TA15_PERF_SEL_ANISO_2_CYCLE_QUADS | TA15 | Number of quads requiring 2 aniso sample. |
| TA15_PERF_SEL_ANISO_4_CYCLE_QUADS | TA15 | Number of quads requiring 4 aniso sample. |
| TA15_PERF_SEL_ANISO_6_CYCLE_QUADS | TA15 | Number of quads requiring 6 aniso sample. |
| TA15_PERF_SEL_ANISO_8_CYCLE_QUADS | TA15 | Number of quads requiring 8 aniso sample. |
| TA15_PERF_SEL_ANISO_10_CYCLE_QUADS | TA15 | Number of quads requiring 10 aniso sample. |
| TA15_PERF_SEL_ANISO_12_CYCLE_QUADS | TA15 | Number of quads requiring 12 aniso sample. |
| TA15_PERF_SEL_ANISO_14_CYCLE_QUADS | TA15 | Number of quads requiring 14 aniso sample. |
| TA15_PERF_SEL_ANISO_16_CYCLE_QUADS | TA15 | Number of quads requiring 16 aniso sample. |
| TA15_PERF_SEL_FLAT_READ_WAVEFRONTS | TA15 | Number of flat opcode reads processed by the TA. |
| TA15_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA15 | Number of flat opcode writes processed by the TA. |
| TA16_PERF_SEL_TA_BUSY | TA16 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA16_PERF_SEL_MIP_1_CYCLE_PIXELS | TA16 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA16_PERF_SEL_MIP_2_CYCLE_PIXELS | TA16 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA16_PERF_SEL_VOL_1_CYCLE_PIXELS | TA16 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA16_PERF_SEL_VOL_2_CYCLE_PIXELS | TA16 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA16_PERF_SEL_ANISO_1_CYCLE_QUADS | TA16 | Number of quads requiring 1 aniso sample. |
| TA16_PERF_SEL_ANISO_2_CYCLE_QUADS | TA16 | Number of quads requiring 2 aniso sample. |
| TA16_PERF_SEL_ANISO_4_CYCLE_QUADS | TA16 | Number of quads requiring 4 aniso sample. |
| TA16_PERF_SEL_ANISO_6_CYCLE_QUADS | TA16 | Number of quads requiring 6 aniso sample. |
| TA16_PERF_SEL_ANISO_8_CYCLE_QUADS | TA16 | Number of quads requiring 8 aniso sample. |
| TA16_PERF_SEL_ANISO_10_CYCLE_QUADS | TA16 | Number of quads requiring 10 aniso sample. |
| TA16_PERF_SEL_ANISO_12_CYCLE_QUADS | TA16 | Number of quads requiring 12 aniso sample. |
| TA16_PERF_SEL_ANISO_14_CYCLE_QUADS | TA16 | Number of quads requiring 14 aniso sample. |
| TA16_PERF_SEL_ANISO_16_CYCLE_QUADS | TA16 | Number of quads requiring 16 aniso sample. |
| TA16_PERF_SEL_FLAT_READ_WAVEFRONTS | TA16 | Number of flat opcode reads processed by the TA. |
| TA16_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA16 | Number of flat opcode writes processed by the TA. |
| TA17_PERF_SEL_TA_BUSY | TA17 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA17_PERF_SEL_MIP_1_CYCLE_PIXELS | TA17 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA17_PERF_SEL_MIP_2_CYCLE_PIXELS | TA17 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA17_PERF_SEL_VOL_1_CYCLE_PIXELS | TA17 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA17_PERF_SEL_VOL_2_CYCLE_PIXELS | TA17 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA17_PERF_SEL_ANISO_1_CYCLE_QUADS | TA17 | Number of quads requiring 1 aniso sample. |
| TA17_PERF_SEL_ANISO_2_CYCLE_QUADS | TA17 | Number of quads requiring 2 aniso sample. |
| TA17_PERF_SEL_ANISO_4_CYCLE_QUADS | TA17 | Number of quads requiring 4 aniso sample. |
| TA17_PERF_SEL_ANISO_6_CYCLE_QUADS | TA17 | Number of quads requiring 6 aniso sample. |
| TA17_PERF_SEL_ANISO_8_CYCLE_QUADS | TA17 | Number of quads requiring 8 aniso sample. |
| TA17_PERF_SEL_ANISO_10_CYCLE_QUADS | TA17 | Number of quads requiring 10 aniso sample. |
| TA17_PERF_SEL_ANISO_12_CYCLE_QUADS | TA17 | Number of quads requiring 12 aniso sample. |
| TA17_PERF_SEL_ANISO_14_CYCLE_QUADS | TA17 | Number of quads requiring 14 aniso sample. |
| TA17_PERF_SEL_ANISO_16_CYCLE_QUADS | TA17 | Number of quads requiring 16 aniso sample. |
| TA17_PERF_SEL_FLAT_READ_WAVEFRONTS | TA17 | Number of flat opcode reads processed by the TA. |
| TA17_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA17 | Number of flat opcode writes processed by the TA. |
| TA18_PERF_SEL_TA_BUSY | TA18 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA18_PERF_SEL_MIP_1_CYCLE_PIXELS | TA18 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA18_PERF_SEL_MIP_2_CYCLE_PIXELS | TA18 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA18_PERF_SEL_VOL_1_CYCLE_PIXELS | TA18 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA18_PERF_SEL_VOL_2_CYCLE_PIXELS | TA18 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA18_PERF_SEL_ANISO_1_CYCLE_QUADS | TA18 | Number of quads requiring 1 aniso sample. |
| TA18_PERF_SEL_ANISO_2_CYCLE_QUADS | TA18 | Number of quads requiring 2 aniso sample. |
| TA18_PERF_SEL_ANISO_4_CYCLE_QUADS | TA18 | Number of quads requiring 4 aniso sample. |
| TA18_PERF_SEL_ANISO_6_CYCLE_QUADS | TA18 | Number of quads requiring 6 aniso sample. |
| TA18_PERF_SEL_ANISO_8_CYCLE_QUADS | TA18 | Number of quads requiring 8 aniso sample. |
| TA18_PERF_SEL_ANISO_10_CYCLE_QUADS | TA18 | Number of quads requiring 10 aniso sample. |
| TA18_PERF_SEL_ANISO_12_CYCLE_QUADS | TA18 | Number of quads requiring 12 aniso sample. |
| TA18_PERF_SEL_ANISO_14_CYCLE_QUADS | TA18 | Number of quads requiring 14 aniso sample. |
| TA18_PERF_SEL_ANISO_16_CYCLE_QUADS | TA18 | Number of quads requiring 16 aniso sample. |
| TA18_PERF_SEL_FLAT_READ_WAVEFRONTS | TA18 | Number of flat opcode reads processed by the TA. |
| TA18_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA18 | Number of flat opcode writes processed by the TA. |
| TA19_PERF_SEL_TA_BUSY | TA19 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA19_PERF_SEL_MIP_1_CYCLE_PIXELS | TA19 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA19_PERF_SEL_MIP_2_CYCLE_PIXELS | TA19 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA19_PERF_SEL_VOL_1_CYCLE_PIXELS | TA19 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA19_PERF_SEL_VOL_2_CYCLE_PIXELS | TA19 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA19_PERF_SEL_ANISO_1_CYCLE_QUADS | TA19 | Number of quads requiring 1 aniso sample. |
| TA19_PERF_SEL_ANISO_2_CYCLE_QUADS | TA19 | Number of quads requiring 2 aniso sample. |
| TA19_PERF_SEL_ANISO_4_CYCLE_QUADS | TA19 | Number of quads requiring 4 aniso sample. |
| TA19_PERF_SEL_ANISO_6_CYCLE_QUADS | TA19 | Number of quads requiring 6 aniso sample. |
| TA19_PERF_SEL_ANISO_8_CYCLE_QUADS | TA19 | Number of quads requiring 8 aniso sample. |
| TA19_PERF_SEL_ANISO_10_CYCLE_QUADS | TA19 | Number of quads requiring 10 aniso sample. |
| TA19_PERF_SEL_ANISO_12_CYCLE_QUADS | TA19 | Number of quads requiring 12 aniso sample. |
| TA19_PERF_SEL_ANISO_14_CYCLE_QUADS | TA19 | Number of quads requiring 14 aniso sample. |
| TA19_PERF_SEL_ANISO_16_CYCLE_QUADS | TA19 | Number of quads requiring 16 aniso sample. |
| TA19_PERF_SEL_FLAT_READ_WAVEFRONTS | TA19 | Number of flat opcode reads processed by the TA. |
| TA19_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA19 | Number of flat opcode writes processed by the TA. |
| TA20_PERF_SEL_TA_BUSY | TA20 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA20_PERF_SEL_MIP_1_CYCLE_PIXELS | TA20 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA20_PERF_SEL_MIP_2_CYCLE_PIXELS | TA20 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA20_PERF_SEL_VOL_1_CYCLE_PIXELS | TA20 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA20_PERF_SEL_VOL_2_CYCLE_PIXELS | TA20 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA20_PERF_SEL_ANISO_1_CYCLE_QUADS | TA20 | Number of quads requiring 1 aniso sample. |
| TA20_PERF_SEL_ANISO_2_CYCLE_QUADS | TA20 | Number of quads requiring 2 aniso sample. |
| TA20_PERF_SEL_ANISO_4_CYCLE_QUADS | TA20 | Number of quads requiring 4 aniso sample. |
| TA20_PERF_SEL_ANISO_6_CYCLE_QUADS | TA20 | Number of quads requiring 6 aniso sample. |
| TA20_PERF_SEL_ANISO_8_CYCLE_QUADS | TA20 | Number of quads requiring 8 aniso sample. |
| TA20_PERF_SEL_ANISO_10_CYCLE_QUADS | TA20 | Number of quads requiring 10 aniso sample. |
| TA20_PERF_SEL_ANISO_12_CYCLE_QUADS | TA20 | Number of quads requiring 12 aniso sample. |
| TA20_PERF_SEL_ANISO_14_CYCLE_QUADS | TA20 | Number of quads requiring 14 aniso sample. |
| TA20_PERF_SEL_ANISO_16_CYCLE_QUADS | TA20 | Number of quads requiring 16 aniso sample. |
| TA20_PERF_SEL_FLAT_READ_WAVEFRONTS | TA20 | Number of flat opcode reads processed by the TA. |
| TA20_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA20 | Number of flat opcode writes processed by the TA. |
| TA21_PERF_SEL_TA_BUSY | TA21 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA21_PERF_SEL_MIP_1_CYCLE_PIXELS | TA21 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA21_PERF_SEL_MIP_2_CYCLE_PIXELS | TA21 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA21_PERF_SEL_VOL_1_CYCLE_PIXELS | TA21 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA21_PERF_SEL_VOL_2_CYCLE_PIXELS | TA21 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA21_PERF_SEL_ANISO_1_CYCLE_QUADS | TA21 | Number of quads requiring 1 aniso sample. |
| TA21_PERF_SEL_ANISO_2_CYCLE_QUADS | TA21 | Number of quads requiring 2 aniso sample. |
| TA21_PERF_SEL_ANISO_4_CYCLE_QUADS | TA21 | Number of quads requiring 4 aniso sample. |
| TA21_PERF_SEL_ANISO_6_CYCLE_QUADS | TA21 | Number of quads requiring 6 aniso sample. |
| TA21_PERF_SEL_ANISO_8_CYCLE_QUADS | TA21 | Number of quads requiring 8 aniso sample. |
| TA21_PERF_SEL_ANISO_10_CYCLE_QUADS | TA21 | Number of quads requiring 10 aniso sample. |
| TA21_PERF_SEL_ANISO_12_CYCLE_QUADS | TA21 | Number of quads requiring 12 aniso sample. |
| TA21_PERF_SEL_ANISO_14_CYCLE_QUADS | TA21 | Number of quads requiring 14 aniso sample. |
| TA21_PERF_SEL_ANISO_16_CYCLE_QUADS | TA21 | Number of quads requiring 16 aniso sample. |
| TA21_PERF_SEL_FLAT_READ_WAVEFRONTS | TA21 | Number of flat opcode reads processed by the TA. |
| TA21_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA21 | Number of flat opcode writes processed by the TA. |
| TA22_PERF_SEL_TA_BUSY | TA22 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA22_PERF_SEL_MIP_1_CYCLE_PIXELS | TA22 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA22_PERF_SEL_MIP_2_CYCLE_PIXELS | TA22 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA22_PERF_SEL_VOL_1_CYCLE_PIXELS | TA22 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA22_PERF_SEL_VOL_2_CYCLE_PIXELS | TA22 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA22_PERF_SEL_ANISO_1_CYCLE_QUADS | TA22 | Number of quads requiring 1 aniso sample. |
| TA22_PERF_SEL_ANISO_2_CYCLE_QUADS | TA22 | Number of quads requiring 2 aniso sample. |
| TA22_PERF_SEL_ANISO_4_CYCLE_QUADS | TA22 | Number of quads requiring 4 aniso sample. |
| TA22_PERF_SEL_ANISO_6_CYCLE_QUADS | TA22 | Number of quads requiring 6 aniso sample. |
| TA22_PERF_SEL_ANISO_8_CYCLE_QUADS | TA22 | Number of quads requiring 8 aniso sample. |
| TA22_PERF_SEL_ANISO_10_CYCLE_QUADS | TA22 | Number of quads requiring 10 aniso sample. |
| TA22_PERF_SEL_ANISO_12_CYCLE_QUADS | TA22 | Number of quads requiring 12 aniso sample. |
| TA22_PERF_SEL_ANISO_14_CYCLE_QUADS | TA22 | Number of quads requiring 14 aniso sample. |
| TA22_PERF_SEL_ANISO_16_CYCLE_QUADS | TA22 | Number of quads requiring 16 aniso sample. |
| TA22_PERF_SEL_FLAT_READ_WAVEFRONTS | TA22 | Number of flat opcode reads processed by the TA. |
| TA22_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA22 | Number of flat opcode writes processed by the TA. |
| TA23_PERF_SEL_TA_BUSY | TA23 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA23_PERF_SEL_MIP_1_CYCLE_PIXELS | TA23 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA23_PERF_SEL_MIP_2_CYCLE_PIXELS | TA23 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA23_PERF_SEL_VOL_1_CYCLE_PIXELS | TA23 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA23_PERF_SEL_VOL_2_CYCLE_PIXELS | TA23 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA23_PERF_SEL_ANISO_1_CYCLE_QUADS | TA23 | Number of quads requiring 1 aniso sample. |
| TA23_PERF_SEL_ANISO_2_CYCLE_QUADS | TA23 | Number of quads requiring 2 aniso sample. |
| TA23_PERF_SEL_ANISO_4_CYCLE_QUADS | TA23 | Number of quads requiring 4 aniso sample. |
| TA23_PERF_SEL_ANISO_6_CYCLE_QUADS | TA23 | Number of quads requiring 6 aniso sample. |
| TA23_PERF_SEL_ANISO_8_CYCLE_QUADS | TA23 | Number of quads requiring 8 aniso sample. |
| TA23_PERF_SEL_ANISO_10_CYCLE_QUADS | TA23 | Number of quads requiring 10 aniso sample. |
| TA23_PERF_SEL_ANISO_12_CYCLE_QUADS | TA23 | Number of quads requiring 12 aniso sample. |
| TA23_PERF_SEL_ANISO_14_CYCLE_QUADS | TA23 | Number of quads requiring 14 aniso sample. |
| TA23_PERF_SEL_ANISO_16_CYCLE_QUADS | TA23 | Number of quads requiring 16 aniso sample. |
| TA23_PERF_SEL_FLAT_READ_WAVEFRONTS | TA23 | Number of flat opcode reads processed by the TA. |
| TA23_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA23 | Number of flat opcode writes processed by the TA. |
| TA24_PERF_SEL_TA_BUSY | TA24 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA24_PERF_SEL_MIP_1_CYCLE_PIXELS | TA24 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA24_PERF_SEL_MIP_2_CYCLE_PIXELS | TA24 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA24_PERF_SEL_VOL_1_CYCLE_PIXELS | TA24 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA24_PERF_SEL_VOL_2_CYCLE_PIXELS | TA24 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA24_PERF_SEL_ANISO_1_CYCLE_QUADS | TA24 | Number of quads requiring 1 aniso sample. |
| TA24_PERF_SEL_ANISO_2_CYCLE_QUADS | TA24 | Number of quads requiring 2 aniso sample. |
| TA24_PERF_SEL_ANISO_4_CYCLE_QUADS | TA24 | Number of quads requiring 4 aniso sample. |
| TA24_PERF_SEL_ANISO_6_CYCLE_QUADS | TA24 | Number of quads requiring 6 aniso sample. |
| TA24_PERF_SEL_ANISO_8_CYCLE_QUADS | TA24 | Number of quads requiring 8 aniso sample. |
| TA24_PERF_SEL_ANISO_10_CYCLE_QUADS | TA24 | Number of quads requiring 10 aniso sample. |
| TA24_PERF_SEL_ANISO_12_CYCLE_QUADS | TA24 | Number of quads requiring 12 aniso sample. |
| TA24_PERF_SEL_ANISO_14_CYCLE_QUADS | TA24 | Number of quads requiring 14 aniso sample. |
| TA24_PERF_SEL_ANISO_16_CYCLE_QUADS | TA24 | Number of quads requiring 16 aniso sample. |
| TA24_PERF_SEL_FLAT_READ_WAVEFRONTS | TA24 | Number of flat opcode reads processed by the TA. |
| TA24_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA24 | Number of flat opcode writes processed by the TA. |
| TA25_PERF_SEL_TA_BUSY | TA25 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA25_PERF_SEL_MIP_1_CYCLE_PIXELS | TA25 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA25_PERF_SEL_MIP_2_CYCLE_PIXELS | TA25 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA25_PERF_SEL_VOL_1_CYCLE_PIXELS | TA25 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA25_PERF_SEL_VOL_2_CYCLE_PIXELS | TA25 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA25_PERF_SEL_ANISO_1_CYCLE_QUADS | TA25 | Number of quads requiring 1 aniso sample. |
| TA25_PERF_SEL_ANISO_2_CYCLE_QUADS | TA25 | Number of quads requiring 2 aniso sample. |
| TA25_PERF_SEL_ANISO_4_CYCLE_QUADS | TA25 | Number of quads requiring 4 aniso sample. |
| TA25_PERF_SEL_ANISO_6_CYCLE_QUADS | TA25 | Number of quads requiring 6 aniso sample. |
| TA25_PERF_SEL_ANISO_8_CYCLE_QUADS | TA25 | Number of quads requiring 8 aniso sample. |
| TA25_PERF_SEL_ANISO_10_CYCLE_QUADS | TA25 | Number of quads requiring 10 aniso sample. |
| TA25_PERF_SEL_ANISO_12_CYCLE_QUADS | TA25 | Number of quads requiring 12 aniso sample. |
| TA25_PERF_SEL_ANISO_14_CYCLE_QUADS | TA25 | Number of quads requiring 14 aniso sample. |
| TA25_PERF_SEL_ANISO_16_CYCLE_QUADS | TA25 | Number of quads requiring 16 aniso sample. |
| TA25_PERF_SEL_FLAT_READ_WAVEFRONTS | TA25 | Number of flat opcode reads processed by the TA. |
| TA25_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA25 | Number of flat opcode writes processed by the TA. |
| TA26_PERF_SEL_TA_BUSY | TA26 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA26_PERF_SEL_MIP_1_CYCLE_PIXELS | TA26 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA26_PERF_SEL_MIP_2_CYCLE_PIXELS | TA26 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA26_PERF_SEL_VOL_1_CYCLE_PIXELS | TA26 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA26_PERF_SEL_VOL_2_CYCLE_PIXELS | TA26 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA26_PERF_SEL_ANISO_1_CYCLE_QUADS | TA26 | Number of quads requiring 1 aniso sample. |
| TA26_PERF_SEL_ANISO_2_CYCLE_QUADS | TA26 | Number of quads requiring 2 aniso sample. |
| TA26_PERF_SEL_ANISO_4_CYCLE_QUADS | TA26 | Number of quads requiring 4 aniso sample. |
| TA26_PERF_SEL_ANISO_6_CYCLE_QUADS | TA26 | Number of quads requiring 6 aniso sample. |
| TA26_PERF_SEL_ANISO_8_CYCLE_QUADS | TA26 | Number of quads requiring 8 aniso sample. |
| TA26_PERF_SEL_ANISO_10_CYCLE_QUADS | TA26 | Number of quads requiring 10 aniso sample. |
| TA26_PERF_SEL_ANISO_12_CYCLE_QUADS | TA26 | Number of quads requiring 12 aniso sample. |
| TA26_PERF_SEL_ANISO_14_CYCLE_QUADS | TA26 | Number of quads requiring 14 aniso sample. |
| TA26_PERF_SEL_ANISO_16_CYCLE_QUADS | TA26 | Number of quads requiring 16 aniso sample. |
| TA26_PERF_SEL_FLAT_READ_WAVEFRONTS | TA26 | Number of flat opcode reads processed by the TA. |
| TA26_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA26 | Number of flat opcode writes processed by the TA. |
| TA27_PERF_SEL_TA_BUSY | TA27 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA27_PERF_SEL_MIP_1_CYCLE_PIXELS | TA27 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA27_PERF_SEL_MIP_2_CYCLE_PIXELS | TA27 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA27_PERF_SEL_VOL_1_CYCLE_PIXELS | TA27 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA27_PERF_SEL_VOL_2_CYCLE_PIXELS | TA27 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA27_PERF_SEL_ANISO_1_CYCLE_QUADS | TA27 | Number of quads requiring 1 aniso sample. |
| TA27_PERF_SEL_ANISO_2_CYCLE_QUADS | TA27 | Number of quads requiring 2 aniso sample. |
| TA27_PERF_SEL_ANISO_4_CYCLE_QUADS | TA27 | Number of quads requiring 4 aniso sample. |
| TA27_PERF_SEL_ANISO_6_CYCLE_QUADS | TA27 | Number of quads requiring 6 aniso sample. |
| TA27_PERF_SEL_ANISO_8_CYCLE_QUADS | TA27 | Number of quads requiring 8 aniso sample. |
| TA27_PERF_SEL_ANISO_10_CYCLE_QUADS | TA27 | Number of quads requiring 10 aniso sample. |
| TA27_PERF_SEL_ANISO_12_CYCLE_QUADS | TA27 | Number of quads requiring 12 aniso sample. |
| TA27_PERF_SEL_ANISO_14_CYCLE_QUADS | TA27 | Number of quads requiring 14 aniso sample. |
| TA27_PERF_SEL_ANISO_16_CYCLE_QUADS | TA27 | Number of quads requiring 16 aniso sample. |
| TA27_PERF_SEL_FLAT_READ_WAVEFRONTS | TA27 | Number of flat opcode reads processed by the TA. |
| TA27_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA27 | Number of flat opcode writes processed by the TA. |
| TA28_PERF_SEL_TA_BUSY | TA28 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA28_PERF_SEL_MIP_1_CYCLE_PIXELS | TA28 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA28_PERF_SEL_MIP_2_CYCLE_PIXELS | TA28 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA28_PERF_SEL_VOL_1_CYCLE_PIXELS | TA28 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA28_PERF_SEL_VOL_2_CYCLE_PIXELS | TA28 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA28_PERF_SEL_ANISO_1_CYCLE_QUADS | TA28 | Number of quads requiring 1 aniso sample. |
| TA28_PERF_SEL_ANISO_2_CYCLE_QUADS | TA28 | Number of quads requiring 2 aniso sample. |
| TA28_PERF_SEL_ANISO_4_CYCLE_QUADS | TA28 | Number of quads requiring 4 aniso sample. |
| TA28_PERF_SEL_ANISO_6_CYCLE_QUADS | TA28 | Number of quads requiring 6 aniso sample. |
| TA28_PERF_SEL_ANISO_8_CYCLE_QUADS | TA28 | Number of quads requiring 8 aniso sample. |
| TA28_PERF_SEL_ANISO_10_CYCLE_QUADS | TA28 | Number of quads requiring 10 aniso sample. |
| TA28_PERF_SEL_ANISO_12_CYCLE_QUADS | TA28 | Number of quads requiring 12 aniso sample. |
| TA28_PERF_SEL_ANISO_14_CYCLE_QUADS | TA28 | Number of quads requiring 14 aniso sample. |
| TA28_PERF_SEL_ANISO_16_CYCLE_QUADS | TA28 | Number of quads requiring 16 aniso sample. |
| TA28_PERF_SEL_FLAT_READ_WAVEFRONTS | TA28 | Number of flat opcode reads processed by the TA. |
| TA28_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA28 | Number of flat opcode writes processed by the TA. |
| TA29_PERF_SEL_TA_BUSY | TA29 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA29_PERF_SEL_MIP_1_CYCLE_PIXELS | TA29 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA29_PERF_SEL_MIP_2_CYCLE_PIXELS | TA29 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA29_PERF_SEL_VOL_1_CYCLE_PIXELS | TA29 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA29_PERF_SEL_VOL_2_CYCLE_PIXELS | TA29 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA29_PERF_SEL_ANISO_1_CYCLE_QUADS | TA29 | Number of quads requiring 1 aniso sample. |
| TA29_PERF_SEL_ANISO_2_CYCLE_QUADS | TA29 | Number of quads requiring 2 aniso sample. |
| TA29_PERF_SEL_ANISO_4_CYCLE_QUADS | TA29 | Number of quads requiring 4 aniso sample. |
| TA29_PERF_SEL_ANISO_6_CYCLE_QUADS | TA29 | Number of quads requiring 6 aniso sample. |
| TA29_PERF_SEL_ANISO_8_CYCLE_QUADS | TA29 | Number of quads requiring 8 aniso sample. |
| TA29_PERF_SEL_ANISO_10_CYCLE_QUADS | TA29 | Number of quads requiring 10 aniso sample. |
| TA29_PERF_SEL_ANISO_12_CYCLE_QUADS | TA29 | Number of quads requiring 12 aniso sample. |
| TA29_PERF_SEL_ANISO_14_CYCLE_QUADS | TA29 | Number of quads requiring 14 aniso sample. |
| TA29_PERF_SEL_ANISO_16_CYCLE_QUADS | TA29 | Number of quads requiring 16 aniso sample. |
| TA29_PERF_SEL_FLAT_READ_WAVEFRONTS | TA29 | Number of flat opcode reads processed by the TA. |
| TA29_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA29 | Number of flat opcode writes processed by the TA. |
| TA30_PERF_SEL_TA_BUSY | TA30 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA30_PERF_SEL_MIP_1_CYCLE_PIXELS | TA30 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA30_PERF_SEL_MIP_2_CYCLE_PIXELS | TA30 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA30_PERF_SEL_VOL_1_CYCLE_PIXELS | TA30 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA30_PERF_SEL_VOL_2_CYCLE_PIXELS | TA30 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA30_PERF_SEL_ANISO_1_CYCLE_QUADS | TA30 | Number of quads requiring 1 aniso sample. |
| TA30_PERF_SEL_ANISO_2_CYCLE_QUADS | TA30 | Number of quads requiring 2 aniso sample. |
| TA30_PERF_SEL_ANISO_4_CYCLE_QUADS | TA30 | Number of quads requiring 4 aniso sample. |
| TA30_PERF_SEL_ANISO_6_CYCLE_QUADS | TA30 | Number of quads requiring 6 aniso sample. |
| TA30_PERF_SEL_ANISO_8_CYCLE_QUADS | TA30 | Number of quads requiring 8 aniso sample. |
| TA30_PERF_SEL_ANISO_10_CYCLE_QUADS | TA30 | Number of quads requiring 10 aniso sample. |
| TA30_PERF_SEL_ANISO_12_CYCLE_QUADS | TA30 | Number of quads requiring 12 aniso sample. |
| TA30_PERF_SEL_ANISO_14_CYCLE_QUADS | TA30 | Number of quads requiring 14 aniso sample. |
| TA30_PERF_SEL_ANISO_16_CYCLE_QUADS | TA30 | Number of quads requiring 16 aniso sample. |
| TA30_PERF_SEL_FLAT_READ_WAVEFRONTS | TA30 | Number of flat opcode reads processed by the TA. |
| TA30_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA30 | Number of flat opcode writes processed by the TA. |
| TA31_PERF_SEL_TA_BUSY | TA31 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA31_PERF_SEL_MIP_1_CYCLE_PIXELS | TA31 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA31_PERF_SEL_MIP_2_CYCLE_PIXELS | TA31 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA31_PERF_SEL_VOL_1_CYCLE_PIXELS | TA31 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA31_PERF_SEL_VOL_2_CYCLE_PIXELS | TA31 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA31_PERF_SEL_ANISO_1_CYCLE_QUADS | TA31 | Number of quads requiring 1 aniso sample. |
| TA31_PERF_SEL_ANISO_2_CYCLE_QUADS | TA31 | Number of quads requiring 2 aniso sample. |
| TA31_PERF_SEL_ANISO_4_CYCLE_QUADS | TA31 | Number of quads requiring 4 aniso sample. |
| TA31_PERF_SEL_ANISO_6_CYCLE_QUADS | TA31 | Number of quads requiring 6 aniso sample. |
| TA31_PERF_SEL_ANISO_8_CYCLE_QUADS | TA31 | Number of quads requiring 8 aniso sample. |
| TA31_PERF_SEL_ANISO_10_CYCLE_QUADS | TA31 | Number of quads requiring 10 aniso sample. |
| TA31_PERF_SEL_ANISO_12_CYCLE_QUADS | TA31 | Number of quads requiring 12 aniso sample. |
| TA31_PERF_SEL_ANISO_14_CYCLE_QUADS | TA31 | Number of quads requiring 14 aniso sample. |
| TA31_PERF_SEL_ANISO_16_CYCLE_QUADS | TA31 | Number of quads requiring 16 aniso sample. |
| TA31_PERF_SEL_FLAT_READ_WAVEFRONTS | TA31 | Number of flat opcode reads processed by the TA. |
| TA31_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA31 | Number of flat opcode writes processed by the TA. |
| TA32_PERF_SEL_TA_BUSY | TA32 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA32_PERF_SEL_MIP_1_CYCLE_PIXELS | TA32 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA32_PERF_SEL_MIP_2_CYCLE_PIXELS | TA32 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA32_PERF_SEL_VOL_1_CYCLE_PIXELS | TA32 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA32_PERF_SEL_VOL_2_CYCLE_PIXELS | TA32 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA32_PERF_SEL_ANISO_1_CYCLE_QUADS | TA32 | Number of quads requiring 1 aniso sample. |
| TA32_PERF_SEL_ANISO_2_CYCLE_QUADS | TA32 | Number of quads requiring 2 aniso sample. |
| TA32_PERF_SEL_ANISO_4_CYCLE_QUADS | TA32 | Number of quads requiring 4 aniso sample. |
| TA32_PERF_SEL_ANISO_6_CYCLE_QUADS | TA32 | Number of quads requiring 6 aniso sample. |
| TA32_PERF_SEL_ANISO_8_CYCLE_QUADS | TA32 | Number of quads requiring 8 aniso sample. |
| TA32_PERF_SEL_ANISO_10_CYCLE_QUADS | TA32 | Number of quads requiring 10 aniso sample. |
| TA32_PERF_SEL_ANISO_12_CYCLE_QUADS | TA32 | Number of quads requiring 12 aniso sample. |
| TA32_PERF_SEL_ANISO_14_CYCLE_QUADS | TA32 | Number of quads requiring 14 aniso sample. |
| TA32_PERF_SEL_ANISO_16_CYCLE_QUADS | TA32 | Number of quads requiring 16 aniso sample. |
| TA32_PERF_SEL_FLAT_READ_WAVEFRONTS | TA32 | Number of flat opcode reads processed by the TA. |
| TA32_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA32 | Number of flat opcode writes processed by the TA. |
| TA33_PERF_SEL_TA_BUSY | TA33 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA33_PERF_SEL_MIP_1_CYCLE_PIXELS | TA33 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA33_PERF_SEL_MIP_2_CYCLE_PIXELS | TA33 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA33_PERF_SEL_VOL_1_CYCLE_PIXELS | TA33 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA33_PERF_SEL_VOL_2_CYCLE_PIXELS | TA33 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA33_PERF_SEL_ANISO_1_CYCLE_QUADS | TA33 | Number of quads requiring 1 aniso sample. |
| TA33_PERF_SEL_ANISO_2_CYCLE_QUADS | TA33 | Number of quads requiring 2 aniso sample. |
| TA33_PERF_SEL_ANISO_4_CYCLE_QUADS | TA33 | Number of quads requiring 4 aniso sample. |
| TA33_PERF_SEL_ANISO_6_CYCLE_QUADS | TA33 | Number of quads requiring 6 aniso sample. |
| TA33_PERF_SEL_ANISO_8_CYCLE_QUADS | TA33 | Number of quads requiring 8 aniso sample. |
| TA33_PERF_SEL_ANISO_10_CYCLE_QUADS | TA33 | Number of quads requiring 10 aniso sample. |
| TA33_PERF_SEL_ANISO_12_CYCLE_QUADS | TA33 | Number of quads requiring 12 aniso sample. |
| TA33_PERF_SEL_ANISO_14_CYCLE_QUADS | TA33 | Number of quads requiring 14 aniso sample. |
| TA33_PERF_SEL_ANISO_16_CYCLE_QUADS | TA33 | Number of quads requiring 16 aniso sample. |
| TA33_PERF_SEL_FLAT_READ_WAVEFRONTS | TA33 | Number of flat opcode reads processed by the TA. |
| TA33_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA33 | Number of flat opcode writes processed by the TA. |
| TA34_PERF_SEL_TA_BUSY | TA34 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA34_PERF_SEL_MIP_1_CYCLE_PIXELS | TA34 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA34_PERF_SEL_MIP_2_CYCLE_PIXELS | TA34 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA34_PERF_SEL_VOL_1_CYCLE_PIXELS | TA34 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA34_PERF_SEL_VOL_2_CYCLE_PIXELS | TA34 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA34_PERF_SEL_ANISO_1_CYCLE_QUADS | TA34 | Number of quads requiring 1 aniso sample. |
| TA34_PERF_SEL_ANISO_2_CYCLE_QUADS | TA34 | Number of quads requiring 2 aniso sample. |
| TA34_PERF_SEL_ANISO_4_CYCLE_QUADS | TA34 | Number of quads requiring 4 aniso sample. |
| TA34_PERF_SEL_ANISO_6_CYCLE_QUADS | TA34 | Number of quads requiring 6 aniso sample. |
| TA34_PERF_SEL_ANISO_8_CYCLE_QUADS | TA34 | Number of quads requiring 8 aniso sample. |
| TA34_PERF_SEL_ANISO_10_CYCLE_QUADS | TA34 | Number of quads requiring 10 aniso sample. |
| TA34_PERF_SEL_ANISO_12_CYCLE_QUADS | TA34 | Number of quads requiring 12 aniso sample. |
| TA34_PERF_SEL_ANISO_14_CYCLE_QUADS | TA34 | Number of quads requiring 14 aniso sample. |
| TA34_PERF_SEL_ANISO_16_CYCLE_QUADS | TA34 | Number of quads requiring 16 aniso sample. |
| TA34_PERF_SEL_FLAT_READ_WAVEFRONTS | TA34 | Number of flat opcode reads processed by the TA. |
| TA34_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA34 | Number of flat opcode writes processed by the TA. |
| TA35_PERF_SEL_TA_BUSY | TA35 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA35_PERF_SEL_MIP_1_CYCLE_PIXELS | TA35 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA35_PERF_SEL_MIP_2_CYCLE_PIXELS | TA35 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA35_PERF_SEL_VOL_1_CYCLE_PIXELS | TA35 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA35_PERF_SEL_VOL_2_CYCLE_PIXELS | TA35 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA35_PERF_SEL_ANISO_1_CYCLE_QUADS | TA35 | Number of quads requiring 1 aniso sample. |
| TA35_PERF_SEL_ANISO_2_CYCLE_QUADS | TA35 | Number of quads requiring 2 aniso sample. |
| TA35_PERF_SEL_ANISO_4_CYCLE_QUADS | TA35 | Number of quads requiring 4 aniso sample. |
| TA35_PERF_SEL_ANISO_6_CYCLE_QUADS | TA35 | Number of quads requiring 6 aniso sample. |
| TA35_PERF_SEL_ANISO_8_CYCLE_QUADS | TA35 | Number of quads requiring 8 aniso sample. |
| TA35_PERF_SEL_ANISO_10_CYCLE_QUADS | TA35 | Number of quads requiring 10 aniso sample. |
| TA35_PERF_SEL_ANISO_12_CYCLE_QUADS | TA35 | Number of quads requiring 12 aniso sample. |
| TA35_PERF_SEL_ANISO_14_CYCLE_QUADS | TA35 | Number of quads requiring 14 aniso sample. |
| TA35_PERF_SEL_ANISO_16_CYCLE_QUADS | TA35 | Number of quads requiring 16 aniso sample. |
| TA35_PERF_SEL_FLAT_READ_WAVEFRONTS | TA35 | Number of flat opcode reads processed by the TA. |
| TA35_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA35 | Number of flat opcode writes processed by the TA. |
| TA36_PERF_SEL_TA_BUSY | TA36 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA36_PERF_SEL_MIP_1_CYCLE_PIXELS | TA36 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA36_PERF_SEL_MIP_2_CYCLE_PIXELS | TA36 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA36_PERF_SEL_VOL_1_CYCLE_PIXELS | TA36 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA36_PERF_SEL_VOL_2_CYCLE_PIXELS | TA36 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA36_PERF_SEL_ANISO_1_CYCLE_QUADS | TA36 | Number of quads requiring 1 aniso sample. |
| TA36_PERF_SEL_ANISO_2_CYCLE_QUADS | TA36 | Number of quads requiring 2 aniso sample. |
| TA36_PERF_SEL_ANISO_4_CYCLE_QUADS | TA36 | Number of quads requiring 4 aniso sample. |
| TA36_PERF_SEL_ANISO_6_CYCLE_QUADS | TA36 | Number of quads requiring 6 aniso sample. |
| TA36_PERF_SEL_ANISO_8_CYCLE_QUADS | TA36 | Number of quads requiring 8 aniso sample. |
| TA36_PERF_SEL_ANISO_10_CYCLE_QUADS | TA36 | Number of quads requiring 10 aniso sample. |
| TA36_PERF_SEL_ANISO_12_CYCLE_QUADS | TA36 | Number of quads requiring 12 aniso sample. |
| TA36_PERF_SEL_ANISO_14_CYCLE_QUADS | TA36 | Number of quads requiring 14 aniso sample. |
| TA36_PERF_SEL_ANISO_16_CYCLE_QUADS | TA36 | Number of quads requiring 16 aniso sample. |
| TA36_PERF_SEL_FLAT_READ_WAVEFRONTS | TA36 | Number of flat opcode reads processed by the TA. |
| TA36_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA36 | Number of flat opcode writes processed by the TA. |
| TA37_PERF_SEL_TA_BUSY | TA37 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA37_PERF_SEL_MIP_1_CYCLE_PIXELS | TA37 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA37_PERF_SEL_MIP_2_CYCLE_PIXELS | TA37 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA37_PERF_SEL_VOL_1_CYCLE_PIXELS | TA37 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA37_PERF_SEL_VOL_2_CYCLE_PIXELS | TA37 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA37_PERF_SEL_ANISO_1_CYCLE_QUADS | TA37 | Number of quads requiring 1 aniso sample. |
| TA37_PERF_SEL_ANISO_2_CYCLE_QUADS | TA37 | Number of quads requiring 2 aniso sample. |
| TA37_PERF_SEL_ANISO_4_CYCLE_QUADS | TA37 | Number of quads requiring 4 aniso sample. |
| TA37_PERF_SEL_ANISO_6_CYCLE_QUADS | TA37 | Number of quads requiring 6 aniso sample. |
| TA37_PERF_SEL_ANISO_8_CYCLE_QUADS | TA37 | Number of quads requiring 8 aniso sample. |
| TA37_PERF_SEL_ANISO_10_CYCLE_QUADS | TA37 | Number of quads requiring 10 aniso sample. |
| TA37_PERF_SEL_ANISO_12_CYCLE_QUADS | TA37 | Number of quads requiring 12 aniso sample. |
| TA37_PERF_SEL_ANISO_14_CYCLE_QUADS | TA37 | Number of quads requiring 14 aniso sample. |
| TA37_PERF_SEL_ANISO_16_CYCLE_QUADS | TA37 | Number of quads requiring 16 aniso sample. |
| TA37_PERF_SEL_FLAT_READ_WAVEFRONTS | TA37 | Number of flat opcode reads processed by the TA. |
| TA37_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA37 | Number of flat opcode writes processed by the TA. |
| TA38_PERF_SEL_TA_BUSY | TA38 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA38_PERF_SEL_MIP_1_CYCLE_PIXELS | TA38 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA38_PERF_SEL_MIP_2_CYCLE_PIXELS | TA38 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA38_PERF_SEL_VOL_1_CYCLE_PIXELS | TA38 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA38_PERF_SEL_VOL_2_CYCLE_PIXELS | TA38 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA38_PERF_SEL_ANISO_1_CYCLE_QUADS | TA38 | Number of quads requiring 1 aniso sample. |
| TA38_PERF_SEL_ANISO_2_CYCLE_QUADS | TA38 | Number of quads requiring 2 aniso sample. |
| TA38_PERF_SEL_ANISO_4_CYCLE_QUADS | TA38 | Number of quads requiring 4 aniso sample. |
| TA38_PERF_SEL_ANISO_6_CYCLE_QUADS | TA38 | Number of quads requiring 6 aniso sample. |
| TA38_PERF_SEL_ANISO_8_CYCLE_QUADS | TA38 | Number of quads requiring 8 aniso sample. |
| TA38_PERF_SEL_ANISO_10_CYCLE_QUADS | TA38 | Number of quads requiring 10 aniso sample. |
| TA38_PERF_SEL_ANISO_12_CYCLE_QUADS | TA38 | Number of quads requiring 12 aniso sample. |
| TA38_PERF_SEL_ANISO_14_CYCLE_QUADS | TA38 | Number of quads requiring 14 aniso sample. |
| TA38_PERF_SEL_ANISO_16_CYCLE_QUADS | TA38 | Number of quads requiring 16 aniso sample. |
| TA38_PERF_SEL_FLAT_READ_WAVEFRONTS | TA38 | Number of flat opcode reads processed by the TA. |
| TA38_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA38 | Number of flat opcode writes processed by the TA. |
| TA39_PERF_SEL_TA_BUSY | TA39 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA39_PERF_SEL_MIP_1_CYCLE_PIXELS | TA39 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA39_PERF_SEL_MIP_2_CYCLE_PIXELS | TA39 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA39_PERF_SEL_VOL_1_CYCLE_PIXELS | TA39 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA39_PERF_SEL_VOL_2_CYCLE_PIXELS | TA39 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA39_PERF_SEL_ANISO_1_CYCLE_QUADS | TA39 | Number of quads requiring 1 aniso sample. |
| TA39_PERF_SEL_ANISO_2_CYCLE_QUADS | TA39 | Number of quads requiring 2 aniso sample. |
| TA39_PERF_SEL_ANISO_4_CYCLE_QUADS | TA39 | Number of quads requiring 4 aniso sample. |
| TA39_PERF_SEL_ANISO_6_CYCLE_QUADS | TA39 | Number of quads requiring 6 aniso sample. |
| TA39_PERF_SEL_ANISO_8_CYCLE_QUADS | TA39 | Number of quads requiring 8 aniso sample. |
| TA39_PERF_SEL_ANISO_10_CYCLE_QUADS | TA39 | Number of quads requiring 10 aniso sample. |
| TA39_PERF_SEL_ANISO_12_CYCLE_QUADS | TA39 | Number of quads requiring 12 aniso sample. |
| TA39_PERF_SEL_ANISO_14_CYCLE_QUADS | TA39 | Number of quads requiring 14 aniso sample. |
| TA39_PERF_SEL_ANISO_16_CYCLE_QUADS | TA39 | Number of quads requiring 16 aniso sample. |
| TA39_PERF_SEL_FLAT_READ_WAVEFRONTS | TA39 | Number of flat opcode reads processed by the TA. |
| TA39_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA39 | Number of flat opcode writes processed by the TA. |
| TA40_PERF_SEL_TA_BUSY | TA40 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA40_PERF_SEL_MIP_1_CYCLE_PIXELS | TA40 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA40_PERF_SEL_MIP_2_CYCLE_PIXELS | TA40 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA40_PERF_SEL_VOL_1_CYCLE_PIXELS | TA40 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA40_PERF_SEL_VOL_2_CYCLE_PIXELS | TA40 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA40_PERF_SEL_ANISO_1_CYCLE_QUADS | TA40 | Number of quads requiring 1 aniso sample. |
| TA40_PERF_SEL_ANISO_2_CYCLE_QUADS | TA40 | Number of quads requiring 2 aniso sample. |
| TA40_PERF_SEL_ANISO_4_CYCLE_QUADS | TA40 | Number of quads requiring 4 aniso sample. |
| TA40_PERF_SEL_ANISO_6_CYCLE_QUADS | TA40 | Number of quads requiring 6 aniso sample. |
| TA40_PERF_SEL_ANISO_8_CYCLE_QUADS | TA40 | Number of quads requiring 8 aniso sample. |
| TA40_PERF_SEL_ANISO_10_CYCLE_QUADS | TA40 | Number of quads requiring 10 aniso sample. |
| TA40_PERF_SEL_ANISO_12_CYCLE_QUADS | TA40 | Number of quads requiring 12 aniso sample. |
| TA40_PERF_SEL_ANISO_14_CYCLE_QUADS | TA40 | Number of quads requiring 14 aniso sample. |
| TA40_PERF_SEL_ANISO_16_CYCLE_QUADS | TA40 | Number of quads requiring 16 aniso sample. |
| TA40_PERF_SEL_FLAT_READ_WAVEFRONTS | TA40 | Number of flat opcode reads processed by the TA. |
| TA40_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA40 | Number of flat opcode writes processed by the TA. |
| TA41_PERF_SEL_TA_BUSY | TA41 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA41_PERF_SEL_MIP_1_CYCLE_PIXELS | TA41 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA41_PERF_SEL_MIP_2_CYCLE_PIXELS | TA41 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA41_PERF_SEL_VOL_1_CYCLE_PIXELS | TA41 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA41_PERF_SEL_VOL_2_CYCLE_PIXELS | TA41 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA41_PERF_SEL_ANISO_1_CYCLE_QUADS | TA41 | Number of quads requiring 1 aniso sample. |
| TA41_PERF_SEL_ANISO_2_CYCLE_QUADS | TA41 | Number of quads requiring 2 aniso sample. |
| TA41_PERF_SEL_ANISO_4_CYCLE_QUADS | TA41 | Number of quads requiring 4 aniso sample. |
| TA41_PERF_SEL_ANISO_6_CYCLE_QUADS | TA41 | Number of quads requiring 6 aniso sample. |
| TA41_PERF_SEL_ANISO_8_CYCLE_QUADS | TA41 | Number of quads requiring 8 aniso sample. |
| TA41_PERF_SEL_ANISO_10_CYCLE_QUADS | TA41 | Number of quads requiring 10 aniso sample. |
| TA41_PERF_SEL_ANISO_12_CYCLE_QUADS | TA41 | Number of quads requiring 12 aniso sample. |
| TA41_PERF_SEL_ANISO_14_CYCLE_QUADS | TA41 | Number of quads requiring 14 aniso sample. |
| TA41_PERF_SEL_ANISO_16_CYCLE_QUADS | TA41 | Number of quads requiring 16 aniso sample. |
| TA41_PERF_SEL_FLAT_READ_WAVEFRONTS | TA41 | Number of flat opcode reads processed by the TA. |
| TA41_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA41 | Number of flat opcode writes processed by the TA. |
| TA42_PERF_SEL_TA_BUSY | TA42 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA42_PERF_SEL_MIP_1_CYCLE_PIXELS | TA42 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA42_PERF_SEL_MIP_2_CYCLE_PIXELS | TA42 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA42_PERF_SEL_VOL_1_CYCLE_PIXELS | TA42 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA42_PERF_SEL_VOL_2_CYCLE_PIXELS | TA42 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA42_PERF_SEL_ANISO_1_CYCLE_QUADS | TA42 | Number of quads requiring 1 aniso sample. |
| TA42_PERF_SEL_ANISO_2_CYCLE_QUADS | TA42 | Number of quads requiring 2 aniso sample. |
| TA42_PERF_SEL_ANISO_4_CYCLE_QUADS | TA42 | Number of quads requiring 4 aniso sample. |
| TA42_PERF_SEL_ANISO_6_CYCLE_QUADS | TA42 | Number of quads requiring 6 aniso sample. |
| TA42_PERF_SEL_ANISO_8_CYCLE_QUADS | TA42 | Number of quads requiring 8 aniso sample. |
| TA42_PERF_SEL_ANISO_10_CYCLE_QUADS | TA42 | Number of quads requiring 10 aniso sample. |
| TA42_PERF_SEL_ANISO_12_CYCLE_QUADS | TA42 | Number of quads requiring 12 aniso sample. |
| TA42_PERF_SEL_ANISO_14_CYCLE_QUADS | TA42 | Number of quads requiring 14 aniso sample. |
| TA42_PERF_SEL_ANISO_16_CYCLE_QUADS | TA42 | Number of quads requiring 16 aniso sample. |
| TA42_PERF_SEL_FLAT_READ_WAVEFRONTS | TA42 | Number of flat opcode reads processed by the TA. |
| TA42_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA42 | Number of flat opcode writes processed by the TA. |
| TA43_PERF_SEL_TA_BUSY | TA43 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA43_PERF_SEL_MIP_1_CYCLE_PIXELS | TA43 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA43_PERF_SEL_MIP_2_CYCLE_PIXELS | TA43 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA43_PERF_SEL_VOL_1_CYCLE_PIXELS | TA43 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA43_PERF_SEL_VOL_2_CYCLE_PIXELS | TA43 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA43_PERF_SEL_ANISO_1_CYCLE_QUADS | TA43 | Number of quads requiring 1 aniso sample. |
| TA43_PERF_SEL_ANISO_2_CYCLE_QUADS | TA43 | Number of quads requiring 2 aniso sample. |
| TA43_PERF_SEL_ANISO_4_CYCLE_QUADS | TA43 | Number of quads requiring 4 aniso sample. |
| TA43_PERF_SEL_ANISO_6_CYCLE_QUADS | TA43 | Number of quads requiring 6 aniso sample. |
| TA43_PERF_SEL_ANISO_8_CYCLE_QUADS | TA43 | Number of quads requiring 8 aniso sample. |
| TA43_PERF_SEL_ANISO_10_CYCLE_QUADS | TA43 | Number of quads requiring 10 aniso sample. |
| TA43_PERF_SEL_ANISO_12_CYCLE_QUADS | TA43 | Number of quads requiring 12 aniso sample. |
| TA43_PERF_SEL_ANISO_14_CYCLE_QUADS | TA43 | Number of quads requiring 14 aniso sample. |
| TA43_PERF_SEL_ANISO_16_CYCLE_QUADS | TA43 | Number of quads requiring 16 aniso sample. |
| TA43_PERF_SEL_FLAT_READ_WAVEFRONTS | TA43 | Number of flat opcode reads processed by the TA. |
| TA43_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA43 | Number of flat opcode writes processed by the TA. |
| TA44_PERF_SEL_TA_BUSY | TA44 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA44_PERF_SEL_MIP_1_CYCLE_PIXELS | TA44 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA44_PERF_SEL_MIP_2_CYCLE_PIXELS | TA44 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA44_PERF_SEL_VOL_1_CYCLE_PIXELS | TA44 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA44_PERF_SEL_VOL_2_CYCLE_PIXELS | TA44 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA44_PERF_SEL_ANISO_1_CYCLE_QUADS | TA44 | Number of quads requiring 1 aniso sample. |
| TA44_PERF_SEL_ANISO_2_CYCLE_QUADS | TA44 | Number of quads requiring 2 aniso sample. |
| TA44_PERF_SEL_ANISO_4_CYCLE_QUADS | TA44 | Number of quads requiring 4 aniso sample. |
| TA44_PERF_SEL_ANISO_6_CYCLE_QUADS | TA44 | Number of quads requiring 6 aniso sample. |
| TA44_PERF_SEL_ANISO_8_CYCLE_QUADS | TA44 | Number of quads requiring 8 aniso sample. |
| TA44_PERF_SEL_ANISO_10_CYCLE_QUADS | TA44 | Number of quads requiring 10 aniso sample. |
| TA44_PERF_SEL_ANISO_12_CYCLE_QUADS | TA44 | Number of quads requiring 12 aniso sample. |
| TA44_PERF_SEL_ANISO_14_CYCLE_QUADS | TA44 | Number of quads requiring 14 aniso sample. |
| TA44_PERF_SEL_ANISO_16_CYCLE_QUADS | TA44 | Number of quads requiring 16 aniso sample. |
| TA44_PERF_SEL_FLAT_READ_WAVEFRONTS | TA44 | Number of flat opcode reads processed by the TA. |
| TA44_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA44 | Number of flat opcode writes processed by the TA. |
| TA45_PERF_SEL_TA_BUSY | TA45 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA45_PERF_SEL_MIP_1_CYCLE_PIXELS | TA45 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA45_PERF_SEL_MIP_2_CYCLE_PIXELS | TA45 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA45_PERF_SEL_VOL_1_CYCLE_PIXELS | TA45 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA45_PERF_SEL_VOL_2_CYCLE_PIXELS | TA45 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA45_PERF_SEL_ANISO_1_CYCLE_QUADS | TA45 | Number of quads requiring 1 aniso sample. |
| TA45_PERF_SEL_ANISO_2_CYCLE_QUADS | TA45 | Number of quads requiring 2 aniso sample. |
| TA45_PERF_SEL_ANISO_4_CYCLE_QUADS | TA45 | Number of quads requiring 4 aniso sample. |
| TA45_PERF_SEL_ANISO_6_CYCLE_QUADS | TA45 | Number of quads requiring 6 aniso sample. |
| TA45_PERF_SEL_ANISO_8_CYCLE_QUADS | TA45 | Number of quads requiring 8 aniso sample. |
| TA45_PERF_SEL_ANISO_10_CYCLE_QUADS | TA45 | Number of quads requiring 10 aniso sample. |
| TA45_PERF_SEL_ANISO_12_CYCLE_QUADS | TA45 | Number of quads requiring 12 aniso sample. |
| TA45_PERF_SEL_ANISO_14_CYCLE_QUADS | TA45 | Number of quads requiring 14 aniso sample. |
| TA45_PERF_SEL_ANISO_16_CYCLE_QUADS | TA45 | Number of quads requiring 16 aniso sample. |
| TA45_PERF_SEL_FLAT_READ_WAVEFRONTS | TA45 | Number of flat opcode reads processed by the TA. |
| TA45_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA45 | Number of flat opcode writes processed by the TA. |
| TA46_PERF_SEL_TA_BUSY | TA46 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA46_PERF_SEL_MIP_1_CYCLE_PIXELS | TA46 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA46_PERF_SEL_MIP_2_CYCLE_PIXELS | TA46 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA46_PERF_SEL_VOL_1_CYCLE_PIXELS | TA46 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA46_PERF_SEL_VOL_2_CYCLE_PIXELS | TA46 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA46_PERF_SEL_ANISO_1_CYCLE_QUADS | TA46 | Number of quads requiring 1 aniso sample. |
| TA46_PERF_SEL_ANISO_2_CYCLE_QUADS | TA46 | Number of quads requiring 2 aniso sample. |
| TA46_PERF_SEL_ANISO_4_CYCLE_QUADS | TA46 | Number of quads requiring 4 aniso sample. |
| TA46_PERF_SEL_ANISO_6_CYCLE_QUADS | TA46 | Number of quads requiring 6 aniso sample. |
| TA46_PERF_SEL_ANISO_8_CYCLE_QUADS | TA46 | Number of quads requiring 8 aniso sample. |
| TA46_PERF_SEL_ANISO_10_CYCLE_QUADS | TA46 | Number of quads requiring 10 aniso sample. |
| TA46_PERF_SEL_ANISO_12_CYCLE_QUADS | TA46 | Number of quads requiring 12 aniso sample. |
| TA46_PERF_SEL_ANISO_14_CYCLE_QUADS | TA46 | Number of quads requiring 14 aniso sample. |
| TA46_PERF_SEL_ANISO_16_CYCLE_QUADS | TA46 | Number of quads requiring 16 aniso sample. |
| TA46_PERF_SEL_FLAT_READ_WAVEFRONTS | TA46 | Number of flat opcode reads processed by the TA. |
| TA46_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA46 | Number of flat opcode writes processed by the TA. |
| TA47_PERF_SEL_TA_BUSY | TA47 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA47_PERF_SEL_MIP_1_CYCLE_PIXELS | TA47 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA47_PERF_SEL_MIP_2_CYCLE_PIXELS | TA47 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA47_PERF_SEL_VOL_1_CYCLE_PIXELS | TA47 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA47_PERF_SEL_VOL_2_CYCLE_PIXELS | TA47 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA47_PERF_SEL_ANISO_1_CYCLE_QUADS | TA47 | Number of quads requiring 1 aniso sample. |
| TA47_PERF_SEL_ANISO_2_CYCLE_QUADS | TA47 | Number of quads requiring 2 aniso sample. |
| TA47_PERF_SEL_ANISO_4_CYCLE_QUADS | TA47 | Number of quads requiring 4 aniso sample. |
| TA47_PERF_SEL_ANISO_6_CYCLE_QUADS | TA47 | Number of quads requiring 6 aniso sample. |
| TA47_PERF_SEL_ANISO_8_CYCLE_QUADS | TA47 | Number of quads requiring 8 aniso sample. |
| TA47_PERF_SEL_ANISO_10_CYCLE_QUADS | TA47 | Number of quads requiring 10 aniso sample. |
| TA47_PERF_SEL_ANISO_12_CYCLE_QUADS | TA47 | Number of quads requiring 12 aniso sample. |
| TA47_PERF_SEL_ANISO_14_CYCLE_QUADS | TA47 | Number of quads requiring 14 aniso sample. |
| TA47_PERF_SEL_ANISO_16_CYCLE_QUADS | TA47 | Number of quads requiring 16 aniso sample. |
| TA47_PERF_SEL_FLAT_READ_WAVEFRONTS | TA47 | Number of flat opcode reads processed by the TA. |
| TA47_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA47 | Number of flat opcode writes processed by the TA. |
| TA48_PERF_SEL_TA_BUSY | TA48 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA48_PERF_SEL_MIP_1_CYCLE_PIXELS | TA48 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA48_PERF_SEL_MIP_2_CYCLE_PIXELS | TA48 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA48_PERF_SEL_VOL_1_CYCLE_PIXELS | TA48 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA48_PERF_SEL_VOL_2_CYCLE_PIXELS | TA48 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA48_PERF_SEL_ANISO_1_CYCLE_QUADS | TA48 | Number of quads requiring 1 aniso sample. |
| TA48_PERF_SEL_ANISO_2_CYCLE_QUADS | TA48 | Number of quads requiring 2 aniso sample. |
| TA48_PERF_SEL_ANISO_4_CYCLE_QUADS | TA48 | Number of quads requiring 4 aniso sample. |
| TA48_PERF_SEL_ANISO_6_CYCLE_QUADS | TA48 | Number of quads requiring 6 aniso sample. |
| TA48_PERF_SEL_ANISO_8_CYCLE_QUADS | TA48 | Number of quads requiring 8 aniso sample. |
| TA48_PERF_SEL_ANISO_10_CYCLE_QUADS | TA48 | Number of quads requiring 10 aniso sample. |
| TA48_PERF_SEL_ANISO_12_CYCLE_QUADS | TA48 | Number of quads requiring 12 aniso sample. |
| TA48_PERF_SEL_ANISO_14_CYCLE_QUADS | TA48 | Number of quads requiring 14 aniso sample. |
| TA48_PERF_SEL_ANISO_16_CYCLE_QUADS | TA48 | Number of quads requiring 16 aniso sample. |
| TA48_PERF_SEL_FLAT_READ_WAVEFRONTS | TA48 | Number of flat opcode reads processed by the TA. |
| TA48_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA48 | Number of flat opcode writes processed by the TA. |
| TA49_PERF_SEL_TA_BUSY | TA49 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA49_PERF_SEL_MIP_1_CYCLE_PIXELS | TA49 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA49_PERF_SEL_MIP_2_CYCLE_PIXELS | TA49 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA49_PERF_SEL_VOL_1_CYCLE_PIXELS | TA49 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA49_PERF_SEL_VOL_2_CYCLE_PIXELS | TA49 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA49_PERF_SEL_ANISO_1_CYCLE_QUADS | TA49 | Number of quads requiring 1 aniso sample. |
| TA49_PERF_SEL_ANISO_2_CYCLE_QUADS | TA49 | Number of quads requiring 2 aniso sample. |
| TA49_PERF_SEL_ANISO_4_CYCLE_QUADS | TA49 | Number of quads requiring 4 aniso sample. |
| TA49_PERF_SEL_ANISO_6_CYCLE_QUADS | TA49 | Number of quads requiring 6 aniso sample. |
| TA49_PERF_SEL_ANISO_8_CYCLE_QUADS | TA49 | Number of quads requiring 8 aniso sample. |
| TA49_PERF_SEL_ANISO_10_CYCLE_QUADS | TA49 | Number of quads requiring 10 aniso sample. |
| TA49_PERF_SEL_ANISO_12_CYCLE_QUADS | TA49 | Number of quads requiring 12 aniso sample. |
| TA49_PERF_SEL_ANISO_14_CYCLE_QUADS | TA49 | Number of quads requiring 14 aniso sample. |
| TA49_PERF_SEL_ANISO_16_CYCLE_QUADS | TA49 | Number of quads requiring 16 aniso sample. |
| TA49_PERF_SEL_FLAT_READ_WAVEFRONTS | TA49 | Number of flat opcode reads processed by the TA. |
| TA49_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA49 | Number of flat opcode writes processed by the TA. |
| TA50_PERF_SEL_TA_BUSY | TA50 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA50_PERF_SEL_MIP_1_CYCLE_PIXELS | TA50 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA50_PERF_SEL_MIP_2_CYCLE_PIXELS | TA50 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA50_PERF_SEL_VOL_1_CYCLE_PIXELS | TA50 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA50_PERF_SEL_VOL_2_CYCLE_PIXELS | TA50 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA50_PERF_SEL_ANISO_1_CYCLE_QUADS | TA50 | Number of quads requiring 1 aniso sample. |
| TA50_PERF_SEL_ANISO_2_CYCLE_QUADS | TA50 | Number of quads requiring 2 aniso sample. |
| TA50_PERF_SEL_ANISO_4_CYCLE_QUADS | TA50 | Number of quads requiring 4 aniso sample. |
| TA50_PERF_SEL_ANISO_6_CYCLE_QUADS | TA50 | Number of quads requiring 6 aniso sample. |
| TA50_PERF_SEL_ANISO_8_CYCLE_QUADS | TA50 | Number of quads requiring 8 aniso sample. |
| TA50_PERF_SEL_ANISO_10_CYCLE_QUADS | TA50 | Number of quads requiring 10 aniso sample. |
| TA50_PERF_SEL_ANISO_12_CYCLE_QUADS | TA50 | Number of quads requiring 12 aniso sample. |
| TA50_PERF_SEL_ANISO_14_CYCLE_QUADS | TA50 | Number of quads requiring 14 aniso sample. |
| TA50_PERF_SEL_ANISO_16_CYCLE_QUADS | TA50 | Number of quads requiring 16 aniso sample. |
| TA50_PERF_SEL_FLAT_READ_WAVEFRONTS | TA50 | Number of flat opcode reads processed by the TA. |
| TA50_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA50 | Number of flat opcode writes processed by the TA. |
| TA51_PERF_SEL_TA_BUSY | TA51 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA51_PERF_SEL_MIP_1_CYCLE_PIXELS | TA51 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA51_PERF_SEL_MIP_2_CYCLE_PIXELS | TA51 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA51_PERF_SEL_VOL_1_CYCLE_PIXELS | TA51 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA51_PERF_SEL_VOL_2_CYCLE_PIXELS | TA51 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA51_PERF_SEL_ANISO_1_CYCLE_QUADS | TA51 | Number of quads requiring 1 aniso sample. |
| TA51_PERF_SEL_ANISO_2_CYCLE_QUADS | TA51 | Number of quads requiring 2 aniso sample. |
| TA51_PERF_SEL_ANISO_4_CYCLE_QUADS | TA51 | Number of quads requiring 4 aniso sample. |
| TA51_PERF_SEL_ANISO_6_CYCLE_QUADS | TA51 | Number of quads requiring 6 aniso sample. |
| TA51_PERF_SEL_ANISO_8_CYCLE_QUADS | TA51 | Number of quads requiring 8 aniso sample. |
| TA51_PERF_SEL_ANISO_10_CYCLE_QUADS | TA51 | Number of quads requiring 10 aniso sample. |
| TA51_PERF_SEL_ANISO_12_CYCLE_QUADS | TA51 | Number of quads requiring 12 aniso sample. |
| TA51_PERF_SEL_ANISO_14_CYCLE_QUADS | TA51 | Number of quads requiring 14 aniso sample. |
| TA51_PERF_SEL_ANISO_16_CYCLE_QUADS | TA51 | Number of quads requiring 16 aniso sample. |
| TA51_PERF_SEL_FLAT_READ_WAVEFRONTS | TA51 | Number of flat opcode reads processed by the TA. |
| TA51_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA51 | Number of flat opcode writes processed by the TA. |
| TA52_PERF_SEL_TA_BUSY | TA52 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA52_PERF_SEL_MIP_1_CYCLE_PIXELS | TA52 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA52_PERF_SEL_MIP_2_CYCLE_PIXELS | TA52 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA52_PERF_SEL_VOL_1_CYCLE_PIXELS | TA52 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA52_PERF_SEL_VOL_2_CYCLE_PIXELS | TA52 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA52_PERF_SEL_ANISO_1_CYCLE_QUADS | TA52 | Number of quads requiring 1 aniso sample. |
| TA52_PERF_SEL_ANISO_2_CYCLE_QUADS | TA52 | Number of quads requiring 2 aniso sample. |
| TA52_PERF_SEL_ANISO_4_CYCLE_QUADS | TA52 | Number of quads requiring 4 aniso sample. |
| TA52_PERF_SEL_ANISO_6_CYCLE_QUADS | TA52 | Number of quads requiring 6 aniso sample. |
| TA52_PERF_SEL_ANISO_8_CYCLE_QUADS | TA52 | Number of quads requiring 8 aniso sample. |
| TA52_PERF_SEL_ANISO_10_CYCLE_QUADS | TA52 | Number of quads requiring 10 aniso sample. |
| TA52_PERF_SEL_ANISO_12_CYCLE_QUADS | TA52 | Number of quads requiring 12 aniso sample. |
| TA52_PERF_SEL_ANISO_14_CYCLE_QUADS | TA52 | Number of quads requiring 14 aniso sample. |
| TA52_PERF_SEL_ANISO_16_CYCLE_QUADS | TA52 | Number of quads requiring 16 aniso sample. |
| TA52_PERF_SEL_FLAT_READ_WAVEFRONTS | TA52 | Number of flat opcode reads processed by the TA. |
| TA52_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA52 | Number of flat opcode writes processed by the TA. |
| TA53_PERF_SEL_TA_BUSY | TA53 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA53_PERF_SEL_MIP_1_CYCLE_PIXELS | TA53 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA53_PERF_SEL_MIP_2_CYCLE_PIXELS | TA53 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA53_PERF_SEL_VOL_1_CYCLE_PIXELS | TA53 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA53_PERF_SEL_VOL_2_CYCLE_PIXELS | TA53 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA53_PERF_SEL_ANISO_1_CYCLE_QUADS | TA53 | Number of quads requiring 1 aniso sample. |
| TA53_PERF_SEL_ANISO_2_CYCLE_QUADS | TA53 | Number of quads requiring 2 aniso sample. |
| TA53_PERF_SEL_ANISO_4_CYCLE_QUADS | TA53 | Number of quads requiring 4 aniso sample. |
| TA53_PERF_SEL_ANISO_6_CYCLE_QUADS | TA53 | Number of quads requiring 6 aniso sample. |
| TA53_PERF_SEL_ANISO_8_CYCLE_QUADS | TA53 | Number of quads requiring 8 aniso sample. |
| TA53_PERF_SEL_ANISO_10_CYCLE_QUADS | TA53 | Number of quads requiring 10 aniso sample. |
| TA53_PERF_SEL_ANISO_12_CYCLE_QUADS | TA53 | Number of quads requiring 12 aniso sample. |
| TA53_PERF_SEL_ANISO_14_CYCLE_QUADS | TA53 | Number of quads requiring 14 aniso sample. |
| TA53_PERF_SEL_ANISO_16_CYCLE_QUADS | TA53 | Number of quads requiring 16 aniso sample. |
| TA53_PERF_SEL_FLAT_READ_WAVEFRONTS | TA53 | Number of flat opcode reads processed by the TA. |
| TA53_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA53 | Number of flat opcode writes processed by the TA. |
| TA54_PERF_SEL_TA_BUSY | TA54 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA54_PERF_SEL_MIP_1_CYCLE_PIXELS | TA54 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA54_PERF_SEL_MIP_2_CYCLE_PIXELS | TA54 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA54_PERF_SEL_VOL_1_CYCLE_PIXELS | TA54 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA54_PERF_SEL_VOL_2_CYCLE_PIXELS | TA54 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA54_PERF_SEL_ANISO_1_CYCLE_QUADS | TA54 | Number of quads requiring 1 aniso sample. |
| TA54_PERF_SEL_ANISO_2_CYCLE_QUADS | TA54 | Number of quads requiring 2 aniso sample. |
| TA54_PERF_SEL_ANISO_4_CYCLE_QUADS | TA54 | Number of quads requiring 4 aniso sample. |
| TA54_PERF_SEL_ANISO_6_CYCLE_QUADS | TA54 | Number of quads requiring 6 aniso sample. |
| TA54_PERF_SEL_ANISO_8_CYCLE_QUADS | TA54 | Number of quads requiring 8 aniso sample. |
| TA54_PERF_SEL_ANISO_10_CYCLE_QUADS | TA54 | Number of quads requiring 10 aniso sample. |
| TA54_PERF_SEL_ANISO_12_CYCLE_QUADS | TA54 | Number of quads requiring 12 aniso sample. |
| TA54_PERF_SEL_ANISO_14_CYCLE_QUADS | TA54 | Number of quads requiring 14 aniso sample. |
| TA54_PERF_SEL_ANISO_16_CYCLE_QUADS | TA54 | Number of quads requiring 16 aniso sample. |
| TA54_PERF_SEL_FLAT_READ_WAVEFRONTS | TA54 | Number of flat opcode reads processed by the TA. |
| TA54_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA54 | Number of flat opcode writes processed by the TA. |
| TA55_PERF_SEL_TA_BUSY | TA55 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA55_PERF_SEL_MIP_1_CYCLE_PIXELS | TA55 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA55_PERF_SEL_MIP_2_CYCLE_PIXELS | TA55 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA55_PERF_SEL_VOL_1_CYCLE_PIXELS | TA55 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA55_PERF_SEL_VOL_2_CYCLE_PIXELS | TA55 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA55_PERF_SEL_ANISO_1_CYCLE_QUADS | TA55 | Number of quads requiring 1 aniso sample. |
| TA55_PERF_SEL_ANISO_2_CYCLE_QUADS | TA55 | Number of quads requiring 2 aniso sample. |
| TA55_PERF_SEL_ANISO_4_CYCLE_QUADS | TA55 | Number of quads requiring 4 aniso sample. |
| TA55_PERF_SEL_ANISO_6_CYCLE_QUADS | TA55 | Number of quads requiring 6 aniso sample. |
| TA55_PERF_SEL_ANISO_8_CYCLE_QUADS | TA55 | Number of quads requiring 8 aniso sample. |
| TA55_PERF_SEL_ANISO_10_CYCLE_QUADS | TA55 | Number of quads requiring 10 aniso sample. |
| TA55_PERF_SEL_ANISO_12_CYCLE_QUADS | TA55 | Number of quads requiring 12 aniso sample. |
| TA55_PERF_SEL_ANISO_14_CYCLE_QUADS | TA55 | Number of quads requiring 14 aniso sample. |
| TA55_PERF_SEL_ANISO_16_CYCLE_QUADS | TA55 | Number of quads requiring 16 aniso sample. |
| TA55_PERF_SEL_FLAT_READ_WAVEFRONTS | TA55 | Number of flat opcode reads processed by the TA. |
| TA55_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA55 | Number of flat opcode writes processed by the TA. |
| TA56_PERF_SEL_TA_BUSY | TA56 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA56_PERF_SEL_MIP_1_CYCLE_PIXELS | TA56 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA56_PERF_SEL_MIP_2_CYCLE_PIXELS | TA56 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA56_PERF_SEL_VOL_1_CYCLE_PIXELS | TA56 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA56_PERF_SEL_VOL_2_CYCLE_PIXELS | TA56 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA56_PERF_SEL_ANISO_1_CYCLE_QUADS | TA56 | Number of quads requiring 1 aniso sample. |
| TA56_PERF_SEL_ANISO_2_CYCLE_QUADS | TA56 | Number of quads requiring 2 aniso sample. |
| TA56_PERF_SEL_ANISO_4_CYCLE_QUADS | TA56 | Number of quads requiring 4 aniso sample. |
| TA56_PERF_SEL_ANISO_6_CYCLE_QUADS | TA56 | Number of quads requiring 6 aniso sample. |
| TA56_PERF_SEL_ANISO_8_CYCLE_QUADS | TA56 | Number of quads requiring 8 aniso sample. |
| TA56_PERF_SEL_ANISO_10_CYCLE_QUADS | TA56 | Number of quads requiring 10 aniso sample. |
| TA56_PERF_SEL_ANISO_12_CYCLE_QUADS | TA56 | Number of quads requiring 12 aniso sample. |
| TA56_PERF_SEL_ANISO_14_CYCLE_QUADS | TA56 | Number of quads requiring 14 aniso sample. |
| TA56_PERF_SEL_ANISO_16_CYCLE_QUADS | TA56 | Number of quads requiring 16 aniso sample. |
| TA56_PERF_SEL_FLAT_READ_WAVEFRONTS | TA56 | Number of flat opcode reads processed by the TA. |
| TA56_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA56 | Number of flat opcode writes processed by the TA. |
| TA57_PERF_SEL_TA_BUSY | TA57 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA57_PERF_SEL_MIP_1_CYCLE_PIXELS | TA57 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA57_PERF_SEL_MIP_2_CYCLE_PIXELS | TA57 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA57_PERF_SEL_VOL_1_CYCLE_PIXELS | TA57 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA57_PERF_SEL_VOL_2_CYCLE_PIXELS | TA57 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA57_PERF_SEL_ANISO_1_CYCLE_QUADS | TA57 | Number of quads requiring 1 aniso sample. |
| TA57_PERF_SEL_ANISO_2_CYCLE_QUADS | TA57 | Number of quads requiring 2 aniso sample. |
| TA57_PERF_SEL_ANISO_4_CYCLE_QUADS | TA57 | Number of quads requiring 4 aniso sample. |
| TA57_PERF_SEL_ANISO_6_CYCLE_QUADS | TA57 | Number of quads requiring 6 aniso sample. |
| TA57_PERF_SEL_ANISO_8_CYCLE_QUADS | TA57 | Number of quads requiring 8 aniso sample. |
| TA57_PERF_SEL_ANISO_10_CYCLE_QUADS | TA57 | Number of quads requiring 10 aniso sample. |
| TA57_PERF_SEL_ANISO_12_CYCLE_QUADS | TA57 | Number of quads requiring 12 aniso sample. |
| TA57_PERF_SEL_ANISO_14_CYCLE_QUADS | TA57 | Number of quads requiring 14 aniso sample. |
| TA57_PERF_SEL_ANISO_16_CYCLE_QUADS | TA57 | Number of quads requiring 16 aniso sample. |
| TA57_PERF_SEL_FLAT_READ_WAVEFRONTS | TA57 | Number of flat opcode reads processed by the TA. |
| TA57_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA57 | Number of flat opcode writes processed by the TA. |
| TA58_PERF_SEL_TA_BUSY | TA58 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA58_PERF_SEL_MIP_1_CYCLE_PIXELS | TA58 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA58_PERF_SEL_MIP_2_CYCLE_PIXELS | TA58 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA58_PERF_SEL_VOL_1_CYCLE_PIXELS | TA58 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA58_PERF_SEL_VOL_2_CYCLE_PIXELS | TA58 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA58_PERF_SEL_ANISO_1_CYCLE_QUADS | TA58 | Number of quads requiring 1 aniso sample. |
| TA58_PERF_SEL_ANISO_2_CYCLE_QUADS | TA58 | Number of quads requiring 2 aniso sample. |
| TA58_PERF_SEL_ANISO_4_CYCLE_QUADS | TA58 | Number of quads requiring 4 aniso sample. |
| TA58_PERF_SEL_ANISO_6_CYCLE_QUADS | TA58 | Number of quads requiring 6 aniso sample. |
| TA58_PERF_SEL_ANISO_8_CYCLE_QUADS | TA58 | Number of quads requiring 8 aniso sample. |
| TA58_PERF_SEL_ANISO_10_CYCLE_QUADS | TA58 | Number of quads requiring 10 aniso sample. |
| TA58_PERF_SEL_ANISO_12_CYCLE_QUADS | TA58 | Number of quads requiring 12 aniso sample. |
| TA58_PERF_SEL_ANISO_14_CYCLE_QUADS | TA58 | Number of quads requiring 14 aniso sample. |
| TA58_PERF_SEL_ANISO_16_CYCLE_QUADS | TA58 | Number of quads requiring 16 aniso sample. |
| TA58_PERF_SEL_FLAT_READ_WAVEFRONTS | TA58 | Number of flat opcode reads processed by the TA. |
| TA58_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA58 | Number of flat opcode writes processed by the TA. |
| TA59_PERF_SEL_TA_BUSY | TA59 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA59_PERF_SEL_MIP_1_CYCLE_PIXELS | TA59 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA59_PERF_SEL_MIP_2_CYCLE_PIXELS | TA59 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA59_PERF_SEL_VOL_1_CYCLE_PIXELS | TA59 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA59_PERF_SEL_VOL_2_CYCLE_PIXELS | TA59 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA59_PERF_SEL_ANISO_1_CYCLE_QUADS | TA59 | Number of quads requiring 1 aniso sample. |
| TA59_PERF_SEL_ANISO_2_CYCLE_QUADS | TA59 | Number of quads requiring 2 aniso sample. |
| TA59_PERF_SEL_ANISO_4_CYCLE_QUADS | TA59 | Number of quads requiring 4 aniso sample. |
| TA59_PERF_SEL_ANISO_6_CYCLE_QUADS | TA59 | Number of quads requiring 6 aniso sample. |
| TA59_PERF_SEL_ANISO_8_CYCLE_QUADS | TA59 | Number of quads requiring 8 aniso sample. |
| TA59_PERF_SEL_ANISO_10_CYCLE_QUADS | TA59 | Number of quads requiring 10 aniso sample. |
| TA59_PERF_SEL_ANISO_12_CYCLE_QUADS | TA59 | Number of quads requiring 12 aniso sample. |
| TA59_PERF_SEL_ANISO_14_CYCLE_QUADS | TA59 | Number of quads requiring 14 aniso sample. |
| TA59_PERF_SEL_ANISO_16_CYCLE_QUADS | TA59 | Number of quads requiring 16 aniso sample. |
| TA59_PERF_SEL_FLAT_READ_WAVEFRONTS | TA59 | Number of flat opcode reads processed by the TA. |
| TA59_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA59 | Number of flat opcode writes processed by the TA. |
| TA60_PERF_SEL_TA_BUSY | TA60 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA60_PERF_SEL_MIP_1_CYCLE_PIXELS | TA60 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA60_PERF_SEL_MIP_2_CYCLE_PIXELS | TA60 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA60_PERF_SEL_VOL_1_CYCLE_PIXELS | TA60 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA60_PERF_SEL_VOL_2_CYCLE_PIXELS | TA60 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA60_PERF_SEL_ANISO_1_CYCLE_QUADS | TA60 | Number of quads requiring 1 aniso sample. |
| TA60_PERF_SEL_ANISO_2_CYCLE_QUADS | TA60 | Number of quads requiring 2 aniso sample. |
| TA60_PERF_SEL_ANISO_4_CYCLE_QUADS | TA60 | Number of quads requiring 4 aniso sample. |
| TA60_PERF_SEL_ANISO_6_CYCLE_QUADS | TA60 | Number of quads requiring 6 aniso sample. |
| TA60_PERF_SEL_ANISO_8_CYCLE_QUADS | TA60 | Number of quads requiring 8 aniso sample. |
| TA60_PERF_SEL_ANISO_10_CYCLE_QUADS | TA60 | Number of quads requiring 10 aniso sample. |
| TA60_PERF_SEL_ANISO_12_CYCLE_QUADS | TA60 | Number of quads requiring 12 aniso sample. |
| TA60_PERF_SEL_ANISO_14_CYCLE_QUADS | TA60 | Number of quads requiring 14 aniso sample. |
| TA60_PERF_SEL_ANISO_16_CYCLE_QUADS | TA60 | Number of quads requiring 16 aniso sample. |
| TA60_PERF_SEL_FLAT_READ_WAVEFRONTS | TA60 | Number of flat opcode reads processed by the TA. |
| TA60_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA60 | Number of flat opcode writes processed by the TA. |
| TA61_PERF_SEL_TA_BUSY | TA61 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA61_PERF_SEL_MIP_1_CYCLE_PIXELS | TA61 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA61_PERF_SEL_MIP_2_CYCLE_PIXELS | TA61 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA61_PERF_SEL_VOL_1_CYCLE_PIXELS | TA61 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA61_PERF_SEL_VOL_2_CYCLE_PIXELS | TA61 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA61_PERF_SEL_ANISO_1_CYCLE_QUADS | TA61 | Number of quads requiring 1 aniso sample. |
| TA61_PERF_SEL_ANISO_2_CYCLE_QUADS | TA61 | Number of quads requiring 2 aniso sample. |
| TA61_PERF_SEL_ANISO_4_CYCLE_QUADS | TA61 | Number of quads requiring 4 aniso sample. |
| TA61_PERF_SEL_ANISO_6_CYCLE_QUADS | TA61 | Number of quads requiring 6 aniso sample. |
| TA61_PERF_SEL_ANISO_8_CYCLE_QUADS | TA61 | Number of quads requiring 8 aniso sample. |
| TA61_PERF_SEL_ANISO_10_CYCLE_QUADS | TA61 | Number of quads requiring 10 aniso sample. |
| TA61_PERF_SEL_ANISO_12_CYCLE_QUADS | TA61 | Number of quads requiring 12 aniso sample. |
| TA61_PERF_SEL_ANISO_14_CYCLE_QUADS | TA61 | Number of quads requiring 14 aniso sample. |
| TA61_PERF_SEL_ANISO_16_CYCLE_QUADS | TA61 | Number of quads requiring 16 aniso sample. |
| TA61_PERF_SEL_FLAT_READ_WAVEFRONTS | TA61 | Number of flat opcode reads processed by the TA. |
| TA61_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA61 | Number of flat opcode writes processed by the TA. |
| TA62_PERF_SEL_TA_BUSY | TA62 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA62_PERF_SEL_MIP_1_CYCLE_PIXELS | TA62 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA62_PERF_SEL_MIP_2_CYCLE_PIXELS | TA62 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA62_PERF_SEL_VOL_1_CYCLE_PIXELS | TA62 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA62_PERF_SEL_VOL_2_CYCLE_PIXELS | TA62 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA62_PERF_SEL_ANISO_1_CYCLE_QUADS | TA62 | Number of quads requiring 1 aniso sample. |
| TA62_PERF_SEL_ANISO_2_CYCLE_QUADS | TA62 | Number of quads requiring 2 aniso sample. |
| TA62_PERF_SEL_ANISO_4_CYCLE_QUADS | TA62 | Number of quads requiring 4 aniso sample. |
| TA62_PERF_SEL_ANISO_6_CYCLE_QUADS | TA62 | Number of quads requiring 6 aniso sample. |
| TA62_PERF_SEL_ANISO_8_CYCLE_QUADS | TA62 | Number of quads requiring 8 aniso sample. |
| TA62_PERF_SEL_ANISO_10_CYCLE_QUADS | TA62 | Number of quads requiring 10 aniso sample. |
| TA62_PERF_SEL_ANISO_12_CYCLE_QUADS | TA62 | Number of quads requiring 12 aniso sample. |
| TA62_PERF_SEL_ANISO_14_CYCLE_QUADS | TA62 | Number of quads requiring 14 aniso sample. |
| TA62_PERF_SEL_ANISO_16_CYCLE_QUADS | TA62 | Number of quads requiring 16 aniso sample. |
| TA62_PERF_SEL_FLAT_READ_WAVEFRONTS | TA62 | Number of flat opcode reads processed by the TA. |
| TA62_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA62 | Number of flat opcode writes processed by the TA. |
| TA63_PERF_SEL_TA_BUSY | TA63 | TA block is busy. Perf_Windowing not supported for this counter. |
| TA63_PERF_SEL_MIP_1_CYCLE_PIXELS | TA63 | Number of pixels requiring sampler state machine to take 1 cycle due to mip filter. |
| TA63_PERF_SEL_MIP_2_CYCLE_PIXELS | TA63 | Number of pixels requiring sampler state machine to take 2 cycle due to mip filter. |
| TA63_PERF_SEL_VOL_1_CYCLE_PIXELS | TA63 | Number of pixels requiring sampler state machine to take 1 cycle due to z filter. |
| TA63_PERF_SEL_VOL_2_CYCLE_PIXELS | TA63 | Number of pixels requiring sampler state machine to take 2 cycle due to z filter. |
| TA63_PERF_SEL_ANISO_1_CYCLE_QUADS | TA63 | Number of quads requiring 1 aniso sample. |
| TA63_PERF_SEL_ANISO_2_CYCLE_QUADS | TA63 | Number of quads requiring 2 aniso sample. |
| TA63_PERF_SEL_ANISO_4_CYCLE_QUADS | TA63 | Number of quads requiring 4 aniso sample. |
| TA63_PERF_SEL_ANISO_6_CYCLE_QUADS | TA63 | Number of quads requiring 6 aniso sample. |
| TA63_PERF_SEL_ANISO_8_CYCLE_QUADS | TA63 | Number of quads requiring 8 aniso sample. |
| TA63_PERF_SEL_ANISO_10_CYCLE_QUADS | TA63 | Number of quads requiring 10 aniso sample. |
| TA63_PERF_SEL_ANISO_12_CYCLE_QUADS | TA63 | Number of quads requiring 12 aniso sample. |
| TA63_PERF_SEL_ANISO_14_CYCLE_QUADS | TA63 | Number of quads requiring 14 aniso sample. |
| TA63_PERF_SEL_ANISO_16_CYCLE_QUADS | TA63 | Number of quads requiring 16 aniso sample. |
| TA63_PERF_SEL_FLAT_READ_WAVEFRONTS | TA63 | Number of flat opcode reads processed by the TA. |
| TA63_PERF_SEL_FLAT_WRITE_WAVEFRONTS | TA63 | Number of flat opcode writes processed by the TA. |
| **TCP** | - | - |
| TCP0_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP0 | TCP stalls TA data interface. Now Windowed. |
| TCP0_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP0 | Tagram conflict stall on a read |
| TCP0_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP0 | Tagram conflict stall on a write |
| TCP0_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP0 | Tagram conflict stall on an atomic |
| TCP1_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP1 | TCP stalls TA data interface. Now Windowed. |
| TCP1_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP1 | Tagram conflict stall on a read |
| TCP1_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP1 | Tagram conflict stall on a write |
| TCP1_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP1 | Tagram conflict stall on an atomic |
| TCP2_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP2 | TCP stalls TA data interface. Now Windowed. |
| TCP2_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP2 | Tagram conflict stall on a read |
| TCP2_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP2 | Tagram conflict stall on a write |
| TCP2_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP2 | Tagram conflict stall on an atomic |
| TCP3_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP3 | TCP stalls TA data interface. Now Windowed. |
| TCP3_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP3 | Tagram conflict stall on a read |
| TCP3_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP3 | Tagram conflict stall on a write |
| TCP3_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP3 | Tagram conflict stall on an atomic |
| TCP4_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP4 | TCP stalls TA data interface. Now Windowed. |
| TCP4_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP4 | Tagram conflict stall on a read |
| TCP4_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP4 | Tagram conflict stall on a write |
| TCP4_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP4 | Tagram conflict stall on an atomic |
| TCP5_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP5 | TCP stalls TA data interface. Now Windowed. |
| TCP5_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP5 | Tagram conflict stall on a read |
| TCP5_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP5 | Tagram conflict stall on a write |
| TCP5_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP5 | Tagram conflict stall on an atomic |
| TCP6_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP6 | TCP stalls TA data interface. Now Windowed. |
| TCP6_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP6 | Tagram conflict stall on a read |
| TCP6_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP6 | Tagram conflict stall on a write |
| TCP6_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP6 | Tagram conflict stall on an atomic |
| TCP7_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP7 | TCP stalls TA data interface. Now Windowed. |
| TCP7_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP7 | Tagram conflict stall on a read |
| TCP7_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP7 | Tagram conflict stall on a write |
| TCP7_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP7 | Tagram conflict stall on an atomic |
| TCP8_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP8 | TCP stalls TA data interface. Now Windowed. |
| TCP8_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP8 | Tagram conflict stall on a read |
| TCP8_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP8 | Tagram conflict stall on a write |
| TCP8_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP8 | Tagram conflict stall on an atomic |
| TCP9_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP9 | TCP stalls TA data interface. Now Windowed. |
| TCP9_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP9 | Tagram conflict stall on a read |
| TCP9_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP9 | Tagram conflict stall on a write |
| TCP9_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP9 | Tagram conflict stall on an atomic |
| TCP10_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP10 | TCP stalls TA data interface. Now Windowed. |
| TCP10_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP10 | Tagram conflict stall on a read |
| TCP10_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP10 | Tagram conflict stall on a write |
| TCP10_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP10 | Tagram conflict stall on an atomic |
| TCP11_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP11 | TCP stalls TA data interface. Now Windowed. |
| TCP11_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP11 | Tagram conflict stall on a read |
| TCP11_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP11 | Tagram conflict stall on a write |
| TCP11_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP11 | Tagram conflict stall on an atomic |
| TCP12_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP12 | TCP stalls TA data interface. Now Windowed. |
| TCP12_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP12 | Tagram conflict stall on a read |
| TCP12_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP12 | Tagram conflict stall on a write |
| TCP12_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP12 | Tagram conflict stall on an atomic |
| TCP13_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP13 | TCP stalls TA data interface. Now Windowed. |
| TCP13_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP13 | Tagram conflict stall on a read |
| TCP13_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP13 | Tagram conflict stall on a write |
| TCP13_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP13 | Tagram conflict stall on an atomic |
| TCP14_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP14 | TCP stalls TA data interface. Now Windowed. |
| TCP14_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP14 | Tagram conflict stall on a read |
| TCP14_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP14 | Tagram conflict stall on a write |
| TCP14_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP14 | Tagram conflict stall on an atomic |
| TCP15_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP15 | TCP stalls TA data interface. Now Windowed. |
| TCP15_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP15 | Tagram conflict stall on a read |
| TCP15_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP15 | Tagram conflict stall on a write |
| TCP15_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP15 | Tagram conflict stall on an atomic |
| TCP16_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP16 | TCP stalls TA data interface. Now Windowed. |
| TCP16_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP16 | Tagram conflict stall on a read |
| TCP16_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP16 | Tagram conflict stall on a write |
| TCP16_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP16 | Tagram conflict stall on an atomic |
| TCP17_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP17 | TCP stalls TA data interface. Now Windowed. |
| TCP17_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP17 | Tagram conflict stall on a read |
| TCP17_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP17 | Tagram conflict stall on a write |
| TCP17_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP17 | Tagram conflict stall on an atomic |
| TCP18_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP18 | TCP stalls TA data interface. Now Windowed. |
| TCP18_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP18 | Tagram conflict stall on a read |
| TCP18_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP18 | Tagram conflict stall on a write |
| TCP18_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP18 | Tagram conflict stall on an atomic |
| TCP19_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP19 | TCP stalls TA data interface. Now Windowed. |
| TCP19_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP19 | Tagram conflict stall on a read |
| TCP19_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP19 | Tagram conflict stall on a write |
| TCP19_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP19 | Tagram conflict stall on an atomic |
| TCP20_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP20 | TCP stalls TA data interface. Now Windowed. |
| TCP20_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP20 | Tagram conflict stall on a read |
| TCP20_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP20 | Tagram conflict stall on a write |
| TCP20_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP20 | Tagram conflict stall on an atomic |
| TCP21_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP21 | TCP stalls TA data interface. Now Windowed. |
| TCP21_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP21 | Tagram conflict stall on a read |
| TCP21_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP21 | Tagram conflict stall on a write |
| TCP21_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP21 | Tagram conflict stall on an atomic |
| TCP22_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP22 | TCP stalls TA data interface. Now Windowed. |
| TCP22_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP22 | Tagram conflict stall on a read |
| TCP22_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP22 | Tagram conflict stall on a write |
| TCP22_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP22 | Tagram conflict stall on an atomic |
| TCP23_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP23 | TCP stalls TA data interface. Now Windowed. |
| TCP23_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP23 | Tagram conflict stall on a read |
| TCP23_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP23 | Tagram conflict stall on a write |
| TCP23_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP23 | Tagram conflict stall on an atomic |
| TCP24_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP24 | TCP stalls TA data interface. Now Windowed. |
| TCP24_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP24 | Tagram conflict stall on a read |
| TCP24_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP24 | Tagram conflict stall on a write |
| TCP24_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP24 | Tagram conflict stall on an atomic |
| TCP25_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP25 | TCP stalls TA data interface. Now Windowed. |
| TCP25_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP25 | Tagram conflict stall on a read |
| TCP25_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP25 | Tagram conflict stall on a write |
| TCP25_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP25 | Tagram conflict stall on an atomic |
| TCP26_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP26 | TCP stalls TA data interface. Now Windowed. |
| TCP26_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP26 | Tagram conflict stall on a read |
| TCP26_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP26 | Tagram conflict stall on a write |
| TCP26_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP26 | Tagram conflict stall on an atomic |
| TCP27_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP27 | TCP stalls TA data interface. Now Windowed. |
| TCP27_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP27 | Tagram conflict stall on a read |
| TCP27_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP27 | Tagram conflict stall on a write |
| TCP27_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP27 | Tagram conflict stall on an atomic |
| TCP28_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP28 | TCP stalls TA data interface. Now Windowed. |
| TCP28_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP28 | Tagram conflict stall on a read |
| TCP28_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP28 | Tagram conflict stall on a write |
| TCP28_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP28 | Tagram conflict stall on an atomic |
| TCP29_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP29 | TCP stalls TA data interface. Now Windowed. |
| TCP29_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP29 | Tagram conflict stall on a read |
| TCP29_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP29 | Tagram conflict stall on a write |
| TCP29_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP29 | Tagram conflict stall on an atomic |
| TCP30_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP30 | TCP stalls TA data interface. Now Windowed. |
| TCP30_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP30 | Tagram conflict stall on a read |
| TCP30_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP30 | Tagram conflict stall on a write |
| TCP30_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP30 | Tagram conflict stall on an atomic |
| TCP31_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP31 | TCP stalls TA data interface. Now Windowed. |
| TCP31_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP31 | Tagram conflict stall on a read |
| TCP31_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP31 | Tagram conflict stall on a write |
| TCP31_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP31 | Tagram conflict stall on an atomic |
| TCP32_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP32 | TCP stalls TA data interface. Now Windowed. |
| TCP32_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP32 | Tagram conflict stall on a read |
| TCP32_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP32 | Tagram conflict stall on a write |
| TCP32_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP32 | Tagram conflict stall on an atomic |
| TCP33_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP33 | TCP stalls TA data interface. Now Windowed. |
| TCP33_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP33 | Tagram conflict stall on a read |
| TCP33_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP33 | Tagram conflict stall on a write |
| TCP33_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP33 | Tagram conflict stall on an atomic |
| TCP34_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP34 | TCP stalls TA data interface. Now Windowed. |
| TCP34_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP34 | Tagram conflict stall on a read |
| TCP34_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP34 | Tagram conflict stall on a write |
| TCP34_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP34 | Tagram conflict stall on an atomic |
| TCP35_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP35 | TCP stalls TA data interface. Now Windowed. |
| TCP35_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP35 | Tagram conflict stall on a read |
| TCP35_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP35 | Tagram conflict stall on a write |
| TCP35_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP35 | Tagram conflict stall on an atomic |
| TCP36_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP36 | TCP stalls TA data interface. Now Windowed. |
| TCP36_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP36 | Tagram conflict stall on a read |
| TCP36_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP36 | Tagram conflict stall on a write |
| TCP36_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP36 | Tagram conflict stall on an atomic |
| TCP37_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP37 | TCP stalls TA data interface. Now Windowed. |
| TCP37_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP37 | Tagram conflict stall on a read |
| TCP37_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP37 | Tagram conflict stall on a write |
| TCP37_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP37 | Tagram conflict stall on an atomic |
| TCP38_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP38 | TCP stalls TA data interface. Now Windowed. |
| TCP38_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP38 | Tagram conflict stall on a read |
| TCP38_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP38 | Tagram conflict stall on a write |
| TCP38_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP38 | Tagram conflict stall on an atomic |
| TCP39_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP39 | TCP stalls TA data interface. Now Windowed. |
| TCP39_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP39 | Tagram conflict stall on a read |
| TCP39_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP39 | Tagram conflict stall on a write |
| TCP39_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP39 | Tagram conflict stall on an atomic |
| TCP40_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP40 | TCP stalls TA data interface. Now Windowed. |
| TCP40_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP40 | Tagram conflict stall on a read |
| TCP40_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP40 | Tagram conflict stall on a write |
| TCP40_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP40 | Tagram conflict stall on an atomic |
| TCP41_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP41 | TCP stalls TA data interface. Now Windowed. |
| TCP41_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP41 | Tagram conflict stall on a read |
| TCP41_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP41 | Tagram conflict stall on a write |
| TCP41_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP41 | Tagram conflict stall on an atomic |
| TCP42_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP42 | TCP stalls TA data interface. Now Windowed. |
| TCP42_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP42 | Tagram conflict stall on a read |
| TCP42_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP42 | Tagram conflict stall on a write |
| TCP42_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP42 | Tagram conflict stall on an atomic |
| TCP43_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP43 | TCP stalls TA data interface. Now Windowed. |
| TCP43_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP43 | Tagram conflict stall on a read |
| TCP43_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP43 | Tagram conflict stall on a write |
| TCP43_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP43 | Tagram conflict stall on an atomic |
| TCP44_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP44 | TCP stalls TA data interface. Now Windowed. |
| TCP44_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP44 | Tagram conflict stall on a read |
| TCP44_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP44 | Tagram conflict stall on a write |
| TCP44_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP44 | Tagram conflict stall on an atomic |
| TCP45_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP45 | TCP stalls TA data interface. Now Windowed. |
| TCP45_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP45 | Tagram conflict stall on a read |
| TCP45_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP45 | Tagram conflict stall on a write |
| TCP45_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP45 | Tagram conflict stall on an atomic |
| TCP46_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP46 | TCP stalls TA data interface. Now Windowed. |
| TCP46_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP46 | Tagram conflict stall on a read |
| TCP46_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP46 | Tagram conflict stall on a write |
| TCP46_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP46 | Tagram conflict stall on an atomic |
| TCP47_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP47 | TCP stalls TA data interface. Now Windowed. |
| TCP47_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP47 | Tagram conflict stall on a read |
| TCP47_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP47 | Tagram conflict stall on a write |
| TCP47_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP47 | Tagram conflict stall on an atomic |
| TCP48_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP48 | TCP stalls TA data interface. Now Windowed. |
| TCP48_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP48 | Tagram conflict stall on a read |
| TCP48_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP48 | Tagram conflict stall on a write |
| TCP48_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP48 | Tagram conflict stall on an atomic |
| TCP49_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP49 | TCP stalls TA data interface. Now Windowed. |
| TCP49_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP49 | Tagram conflict stall on a read |
| TCP49_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP49 | Tagram conflict stall on a write |
| TCP49_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP49 | Tagram conflict stall on an atomic |
| TCP50_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP50 | TCP stalls TA data interface. Now Windowed. |
| TCP50_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP50 | Tagram conflict stall on a read |
| TCP50_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP50 | Tagram conflict stall on a write |
| TCP50_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP50 | Tagram conflict stall on an atomic |
| TCP51_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP51 | TCP stalls TA data interface. Now Windowed. |
| TCP51_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP51 | Tagram conflict stall on a read |
| TCP51_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP51 | Tagram conflict stall on a write |
| TCP51_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP51 | Tagram conflict stall on an atomic |
| TCP52_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP52 | TCP stalls TA data interface. Now Windowed. |
| TCP52_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP52 | Tagram conflict stall on a read |
| TCP52_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP52 | Tagram conflict stall on a write |
| TCP52_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP52 | Tagram conflict stall on an atomic |
| TCP53_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP53 | TCP stalls TA data interface. Now Windowed. |
| TCP53_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP53 | Tagram conflict stall on a read |
| TCP53_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP53 | Tagram conflict stall on a write |
| TCP53_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP53 | Tagram conflict stall on an atomic |
| TCP54_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP54 | TCP stalls TA data interface. Now Windowed. |
| TCP54_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP54 | Tagram conflict stall on a read |
| TCP54_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP54 | Tagram conflict stall on a write |
| TCP54_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP54 | Tagram conflict stall on an atomic |
| TCP55_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP55 | TCP stalls TA data interface. Now Windowed. |
| TCP55_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP55 | Tagram conflict stall on a read |
| TCP55_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP55 | Tagram conflict stall on a write |
| TCP55_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP55 | Tagram conflict stall on an atomic |
| TCP56_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP56 | TCP stalls TA data interface. Now Windowed. |
| TCP56_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP56 | Tagram conflict stall on a read |
| TCP56_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP56 | Tagram conflict stall on a write |
| TCP56_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP56 | Tagram conflict stall on an atomic |
| TCP57_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP57 | TCP stalls TA data interface. Now Windowed. |
| TCP57_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP57 | Tagram conflict stall on a read |
| TCP57_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP57 | Tagram conflict stall on a write |
| TCP57_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP57 | Tagram conflict stall on an atomic |
| TCP58_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP58 | TCP stalls TA data interface. Now Windowed. |
| TCP58_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP58 | Tagram conflict stall on a read |
| TCP58_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP58 | Tagram conflict stall on a write |
| TCP58_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP58 | Tagram conflict stall on an atomic |
| TCP59_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP59 | TCP stalls TA data interface. Now Windowed. |
| TCP59_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP59 | Tagram conflict stall on a read |
| TCP59_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP59 | Tagram conflict stall on a write |
| TCP59_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP59 | Tagram conflict stall on an atomic |
| TCP60_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP60 | TCP stalls TA data interface. Now Windowed. |
| TCP60_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP60 | Tagram conflict stall on a read |
| TCP60_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP60 | Tagram conflict stall on a write |
| TCP60_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP60 | Tagram conflict stall on an atomic |
| TCP61_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP61 | TCP stalls TA data interface. Now Windowed. |
| TCP61_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP61 | Tagram conflict stall on a read |
| TCP61_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP61 | Tagram conflict stall on a write |
| TCP61_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP61 | Tagram conflict stall on an atomic |
| TCP62_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP62 | TCP stalls TA data interface. Now Windowed. |
| TCP62_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP62 | Tagram conflict stall on a read |
| TCP62_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP62 | Tagram conflict stall on a write |
| TCP62_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP62 | Tagram conflict stall on an atomic |
| TCP63_PERF_SEL_TCP_TA_DATA_STALL_CYCLES | TCP63 | TCP stalls TA data interface. Now Windowed. |
| TCP63_PERF_SEL_READ_TAGCONFLICT_STALL_CYCLES | TCP63 | Tagram conflict stall on a read |
| TCP63_PERF_SEL_WRITE_TAGCONFLICT_STALL_CYCLES | TCP63 | Tagram conflict stall on a write |
| TCP63_PERF_SEL_ATOMIC_TAGCONFLICT_STALL_CYCLES | TCP63 | Tagram conflict stall on an atomic |
| **TCC** | - | - |
| TCC0_PERF_SEL_HIT | TCC0 | Number of cache hits. |
| TCC0_PERF_SEL_MISS | TCC0 | Number of cache misses. UC reads count as misses. |
| TCC0_PERF_SEL_MC_WRREQ | TCC0 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC0_PERF_SEL_MC_WRREQ_STALL | TCC0 | Number of cycles a write request was stalled. |
| TCC0_PERF_SEL_MC_RDREQ | TCC0 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC1_PERF_SEL_HIT | TCC1 | Number of cache hits. |
| TCC1_PERF_SEL_MISS | TCC1 | Number of cache misses. UC reads count as misses. |
| TCC1_PERF_SEL_MC_WRREQ | TCC1 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC1_PERF_SEL_MC_WRREQ_STALL | TCC1 | Number of cycles a write request was stalled. |
| TCC1_PERF_SEL_MC_RDREQ | TCC1 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC2_PERF_SEL_HIT | TCC2 | Number of cache hits. |
| TCC2_PERF_SEL_MISS | TCC2 | Number of cache misses. UC reads count as misses. |
| TCC2_PERF_SEL_MC_WRREQ | TCC2 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC2_PERF_SEL_MC_WRREQ_STALL | TCC2 | Number of cycles a write request was stalled. |
| TCC2_PERF_SEL_MC_RDREQ | TCC2 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC3_PERF_SEL_HIT | TCC3 | Number of cache hits. |
| TCC3_PERF_SEL_MISS | TCC3 | Number of cache misses. UC reads count as misses. |
| TCC3_PERF_SEL_MC_WRREQ | TCC3 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC3_PERF_SEL_MC_WRREQ_STALL | TCC3 | Number of cycles a write request was stalled. |
| TCC3_PERF_SEL_MC_RDREQ | TCC3 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC4_PERF_SEL_HIT | TCC4 | Number of cache hits. |
| TCC4_PERF_SEL_MISS | TCC4 | Number of cache misses. UC reads count as misses. |
| TCC4_PERF_SEL_MC_WRREQ | TCC4 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC4_PERF_SEL_MC_WRREQ_STALL | TCC4 | Number of cycles a write request was stalled. |
| TCC4_PERF_SEL_MC_RDREQ | TCC4 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC5_PERF_SEL_HIT | TCC5 | Number of cache hits. |
| TCC5_PERF_SEL_MISS | TCC5 | Number of cache misses. UC reads count as misses. |
| TCC5_PERF_SEL_MC_WRREQ | TCC5 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC5_PERF_SEL_MC_WRREQ_STALL | TCC5 | Number of cycles a write request was stalled. |
| TCC5_PERF_SEL_MC_RDREQ | TCC5 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC6_PERF_SEL_HIT | TCC6 | Number of cache hits. |
| TCC6_PERF_SEL_MISS | TCC6 | Number of cache misses. UC reads count as misses. |
| TCC6_PERF_SEL_MC_WRREQ | TCC6 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC6_PERF_SEL_MC_WRREQ_STALL | TCC6 | Number of cycles a write request was stalled. |
| TCC6_PERF_SEL_MC_RDREQ | TCC6 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC7_PERF_SEL_HIT | TCC7 | Number of cache hits. |
| TCC7_PERF_SEL_MISS | TCC7 | Number of cache misses. UC reads count as misses. |
| TCC7_PERF_SEL_MC_WRREQ | TCC7 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC7_PERF_SEL_MC_WRREQ_STALL | TCC7 | Number of cycles a write request was stalled. |
| TCC7_PERF_SEL_MC_RDREQ | TCC7 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC8_PERF_SEL_HIT | TCC8 | Number of cache hits. |
| TCC8_PERF_SEL_MISS | TCC8 | Number of cache misses. UC reads count as misses. |
| TCC8_PERF_SEL_MC_WRREQ | TCC8 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC8_PERF_SEL_MC_WRREQ_STALL | TCC8 | Number of cycles a write request was stalled. |
| TCC8_PERF_SEL_MC_RDREQ | TCC8 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC9_PERF_SEL_HIT | TCC9 | Number of cache hits. |
| TCC9_PERF_SEL_MISS | TCC9 | Number of cache misses. UC reads count as misses. |
| TCC9_PERF_SEL_MC_WRREQ | TCC9 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC9_PERF_SEL_MC_WRREQ_STALL | TCC9 | Number of cycles a write request was stalled. |
| TCC9_PERF_SEL_MC_RDREQ | TCC9 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC10_PERF_SEL_HIT | TCC10 | Number of cache hits. |
| TCC10_PERF_SEL_MISS | TCC10 | Number of cache misses. UC reads count as misses. |
| TCC10_PERF_SEL_MC_WRREQ | TCC10 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC10_PERF_SEL_MC_WRREQ_STALL | TCC10 | Number of cycles a write request was stalled. |
| TCC10_PERF_SEL_MC_RDREQ | TCC10 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC11_PERF_SEL_HIT | TCC11 | Number of cache hits. |
| TCC11_PERF_SEL_MISS | TCC11 | Number of cache misses. UC reads count as misses. |
| TCC11_PERF_SEL_MC_WRREQ | TCC11 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC11_PERF_SEL_MC_WRREQ_STALL | TCC11 | Number of cycles a write request was stalled. |
| TCC11_PERF_SEL_MC_RDREQ | TCC11 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC12_PERF_SEL_HIT | TCC12 | Number of cache hits. |
| TCC12_PERF_SEL_MISS | TCC12 | Number of cache misses. UC reads count as misses. |
| TCC12_PERF_SEL_MC_WRREQ | TCC12 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC12_PERF_SEL_MC_WRREQ_STALL | TCC12 | Number of cycles a write request was stalled. |
| TCC12_PERF_SEL_MC_RDREQ | TCC12 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC13_PERF_SEL_HIT | TCC13 | Number of cache hits. |
| TCC13_PERF_SEL_MISS | TCC13 | Number of cache misses. UC reads count as misses. |
| TCC13_PERF_SEL_MC_WRREQ | TCC13 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC13_PERF_SEL_MC_WRREQ_STALL | TCC13 | Number of cycles a write request was stalled. |
| TCC13_PERF_SEL_MC_RDREQ | TCC13 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC14_PERF_SEL_HIT | TCC14 | Number of cache hits. |
| TCC14_PERF_SEL_MISS | TCC14 | Number of cache misses. UC reads count as misses. |
| TCC14_PERF_SEL_MC_WRREQ | TCC14 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC14_PERF_SEL_MC_WRREQ_STALL | TCC14 | Number of cycles a write request was stalled. |
| TCC14_PERF_SEL_MC_RDREQ | TCC14 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| TCC15_PERF_SEL_HIT | TCC15 | Number of cache hits. |
| TCC15_PERF_SEL_MISS | TCC15 | Number of cache misses. UC reads count as misses. |
| TCC15_PERF_SEL_MC_WRREQ | TCC15 | Number of 32-byte transactions going over the TC_MC_wrreq interface. Atomics may travel over the same interface and are generally classified as write requests. |
| TCC15_PERF_SEL_MC_WRREQ_STALL | TCC15 | Number of cycles a write request was stalled. |
| TCC15_PERF_SEL_MC_RDREQ | TCC15 | Number of 32-byte reads. The hardware actually does 64-byte reads but the number is adjusted to provide uniformity. |
| **DB** | - | - |
| DB0_PERF_SEL_SC_DB_TILE_TILES | DB0 | Tiles sent over interface |
| DB0_PERF_SEL_DB_SC_TILE_CULLED | DB0 | Tiles culled in total |
| DB0_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB0 | Number of detail killed tiles |
| DB0_PERF_SEL_DB_CB_LQUAD_STALLS | DB0 | Cycles Interface is stalled |
| DB0_PERF_SEL_TILE_RD_SENDS | DB0 | HTile reads. Each is 256B |
| DB0_PERF_SEL_QUAD_RD_32BYTE_REQS | DB0 | Number of 32 Byte quad read requests |
| DB0_PERF_SEL_TILE_WR_SENDS | DB0 | 32 Byte HTile writes |
| DB0_PERF_SEL_QUAD_WR_SENDS | DB0 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB0_PERF_SEL_OP_PIPE_BUSY | DB0 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB0_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB0 | Samples passing Z test during a PostZ pass |
| DB0_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB0 | Samples failing Z test during a PostZ pass |
| DB0_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB0 | Samples failing Stencil test during a PostZ pass |
| DB0_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB0 | Samples passing Z test during a PreZ pass |
| DB0_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB0 | Samples failing Z test during a PreZ pass |
| DB0_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB0 | Samples failing Stencil test during a PreZ pass |
| DB1_PERF_SEL_SC_DB_TILE_TILES | DB1 | Tiles sent over interface |
| DB1_PERF_SEL_DB_SC_TILE_CULLED | DB1 | Tiles culled in total |
| DB1_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB1 | Number of detail killed tiles |
| DB1_PERF_SEL_DB_CB_LQUAD_STALLS | DB1 | Cycles Interface is stalled |
| DB1_PERF_SEL_TILE_RD_SENDS | DB1 | HTile reads. Each is 256B |
| DB1_PERF_SEL_QUAD_RD_32BYTE_REQS | DB1 | Number of 32 Byte quad read requests |
| DB1_PERF_SEL_TILE_WR_SENDS | DB1 | 32 Byte HTile writes |
| DB1_PERF_SEL_QUAD_WR_SENDS | DB1 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB1_PERF_SEL_OP_PIPE_BUSY | DB1 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB1_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB1 | Samples passing Z test during a PostZ pass |
| DB1_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB1 | Samples failing Z test during a PostZ pass |
| DB1_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB1 | Samples failing Stencil test during a PostZ pass |
| DB1_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB1 | Samples passing Z test during a PreZ pass |
| DB1_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB1 | Samples failing Z test during a PreZ pass |
| DB1_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB1 | Samples failing Stencil test during a PreZ pass |
| DB2_PERF_SEL_SC_DB_TILE_TILES | DB2 | Tiles sent over interface |
| DB2_PERF_SEL_DB_SC_TILE_CULLED | DB2 | Tiles culled in total |
| DB2_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB2 | Number of detail killed tiles |
| DB2_PERF_SEL_DB_CB_LQUAD_STALLS | DB2 | Cycles Interface is stalled |
| DB2_PERF_SEL_TILE_RD_SENDS | DB2 | HTile reads. Each is 256B |
| DB2_PERF_SEL_QUAD_RD_32BYTE_REQS | DB2 | Number of 32 Byte quad read requests |
| DB2_PERF_SEL_TILE_WR_SENDS | DB2 | 32 Byte HTile writes |
| DB2_PERF_SEL_QUAD_WR_SENDS | DB2 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB2_PERF_SEL_OP_PIPE_BUSY | DB2 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB2_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB2 | Samples passing Z test during a PostZ pass |
| DB2_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB2 | Samples failing Z test during a PostZ pass |
| DB2_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB2 | Samples failing Stencil test during a PostZ pass |
| DB2_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB2 | Samples passing Z test during a PreZ pass |
| DB2_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB2 | Samples failing Z test during a PreZ pass |
| DB2_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB2 | Samples failing Stencil test during a PreZ pass |
| DB3_PERF_SEL_SC_DB_TILE_TILES | DB3 | Tiles sent over interface |
| DB3_PERF_SEL_DB_SC_TILE_CULLED | DB3 | Tiles culled in total |
| DB3_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB3 | Number of detail killed tiles |
| DB3_PERF_SEL_DB_CB_LQUAD_STALLS | DB3 | Cycles Interface is stalled |
| DB3_PERF_SEL_TILE_RD_SENDS | DB3 | HTile reads. Each is 256B |
| DB3_PERF_SEL_QUAD_RD_32BYTE_REQS | DB3 | Number of 32 Byte quad read requests |
| DB3_PERF_SEL_TILE_WR_SENDS | DB3 | 32 Byte HTile writes |
| DB3_PERF_SEL_QUAD_WR_SENDS | DB3 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB3_PERF_SEL_OP_PIPE_BUSY | DB3 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB3_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB3 | Samples passing Z test during a PostZ pass |
| DB3_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB3 | Samples failing Z test during a PostZ pass |
| DB3_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB3 | Samples failing Stencil test during a PostZ pass |
| DB3_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB3 | Samples passing Z test during a PreZ pass |
| DB3_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB3 | Samples failing Z test during a PreZ pass |
| DB3_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB3 | Samples failing Stencil test during a PreZ pass |
| DB4_PERF_SEL_SC_DB_TILE_TILES | DB4 | Tiles sent over interface |
| DB4_PERF_SEL_DB_SC_TILE_CULLED | DB4 | Tiles culled in total |
| DB4_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB4 | Number of detail killed tiles |
| DB4_PERF_SEL_DB_CB_LQUAD_STALLS | DB4 | Cycles Interface is stalled |
| DB4_PERF_SEL_TILE_RD_SENDS | DB4 | HTile reads. Each is 256B |
| DB4_PERF_SEL_QUAD_RD_32BYTE_REQS | DB4 | Number of 32 Byte quad read requests |
| DB4_PERF_SEL_TILE_WR_SENDS | DB4 | 32 Byte HTile writes |
| DB4_PERF_SEL_QUAD_WR_SENDS | DB4 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB4_PERF_SEL_OP_PIPE_BUSY | DB4 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB4_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB4 | Samples passing Z test during a PostZ pass |
| DB4_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB4 | Samples failing Z test during a PostZ pass |
| DB4_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB4 | Samples failing Stencil test during a PostZ pass |
| DB4_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB4 | Samples passing Z test during a PreZ pass |
| DB4_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB4 | Samples failing Z test during a PreZ pass |
| DB4_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB4 | Samples failing Stencil test during a PreZ pass |
| DB5_PERF_SEL_SC_DB_TILE_TILES | DB5 | Tiles sent over interface |
| DB5_PERF_SEL_DB_SC_TILE_CULLED | DB5 | Tiles culled in total |
| DB5_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB5 | Number of detail killed tiles |
| DB5_PERF_SEL_DB_CB_LQUAD_STALLS | DB5 | Cycles Interface is stalled |
| DB5_PERF_SEL_TILE_RD_SENDS | DB5 | HTile reads. Each is 256B |
| DB5_PERF_SEL_QUAD_RD_32BYTE_REQS | DB5 | Number of 32 Byte quad read requests |
| DB5_PERF_SEL_TILE_WR_SENDS | DB5 | 32 Byte HTile writes |
| DB5_PERF_SEL_QUAD_WR_SENDS | DB5 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB5_PERF_SEL_OP_PIPE_BUSY | DB5 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB5_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB5 | Samples passing Z test during a PostZ pass |
| DB5_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB5 | Samples failing Z test during a PostZ pass |
| DB5_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB5 | Samples failing Stencil test during a PostZ pass |
| DB5_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB5 | Samples passing Z test during a PreZ pass |
| DB5_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB5 | Samples failing Z test during a PreZ pass |
| DB5_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB5 | Samples failing Stencil test during a PreZ pass |
| DB6_PERF_SEL_SC_DB_TILE_TILES | DB6 | Tiles sent over interface |
| DB6_PERF_SEL_DB_SC_TILE_CULLED | DB6 | Tiles culled in total |
| DB6_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB6 | Number of detail killed tiles |
| DB6_PERF_SEL_DB_CB_LQUAD_STALLS | DB6 | Cycles Interface is stalled |
| DB6_PERF_SEL_TILE_RD_SENDS | DB6 | HTile reads. Each is 256B |
| DB6_PERF_SEL_QUAD_RD_32BYTE_REQS | DB6 | Number of 32 Byte quad read requests |
| DB6_PERF_SEL_TILE_WR_SENDS | DB6 | 32 Byte HTile writes |
| DB6_PERF_SEL_QUAD_WR_SENDS | DB6 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB6_PERF_SEL_OP_PIPE_BUSY | DB6 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB6_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB6 | Samples passing Z test during a PostZ pass |
| DB6_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB6 | Samples failing Z test during a PostZ pass |
| DB6_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB6 | Samples failing Stencil test during a PostZ pass |
| DB6_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB6 | Samples passing Z test during a PreZ pass |
| DB6_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB6 | Samples failing Z test during a PreZ pass |
| DB6_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB6 | Samples failing Stencil test during a PreZ pass |
| DB7_PERF_SEL_SC_DB_TILE_TILES | DB7 | Tiles sent over interface |
| DB7_PERF_SEL_DB_SC_TILE_CULLED | DB7 | Tiles culled in total |
| DB7_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB7 | Number of detail killed tiles |
| DB7_PERF_SEL_DB_CB_LQUAD_STALLS | DB7 | Cycles Interface is stalled |
| DB7_PERF_SEL_TILE_RD_SENDS | DB7 | HTile reads. Each is 256B |
| DB7_PERF_SEL_QUAD_RD_32BYTE_REQS | DB7 | Number of 32 Byte quad read requests |
| DB7_PERF_SEL_TILE_WR_SENDS | DB7 | 32 Byte HTile writes |
| DB7_PERF_SEL_QUAD_WR_SENDS | DB7 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB7_PERF_SEL_OP_PIPE_BUSY | DB7 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB7_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB7 | Samples passing Z test during a PostZ pass |
| DB7_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB7 | Samples failing Z test during a PostZ pass |
| DB7_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB7 | Samples failing Stencil test during a PostZ pass |
| DB7_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB7 | Samples passing Z test during a PreZ pass |
| DB7_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB7 | Samples failing Z test during a PreZ pass |
| DB7_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB7 | Samples failing Stencil test during a PreZ pass |
| DB8_PERF_SEL_SC_DB_TILE_TILES | DB8 | Tiles sent over interface |
| DB8_PERF_SEL_DB_SC_TILE_CULLED | DB8 | Tiles culled in total |
| DB8_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB8 | Number of detail killed tiles |
| DB8_PERF_SEL_DB_CB_LQUAD_STALLS | DB8 | Cycles Interface is stalled |
| DB8_PERF_SEL_TILE_RD_SENDS | DB8 | HTile reads. Each is 256B |
| DB8_PERF_SEL_QUAD_RD_32BYTE_REQS | DB8 | Number of 32 Byte quad read requests |
| DB8_PERF_SEL_TILE_WR_SENDS | DB8 | 32 Byte HTile writes |
| DB8_PERF_SEL_QUAD_WR_SENDS | DB8 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB8_PERF_SEL_OP_PIPE_BUSY | DB8 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB8_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB8 | Samples passing Z test during a PostZ pass |
| DB8_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB8 | Samples failing Z test during a PostZ pass |
| DB8_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB8 | Samples failing Stencil test during a PostZ pass |
| DB8_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB8 | Samples passing Z test during a PreZ pass |
| DB8_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB8 | Samples failing Z test during a PreZ pass |
| DB8_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB8 | Samples failing Stencil test during a PreZ pass |
| DB9_PERF_SEL_SC_DB_TILE_TILES | DB9 | Tiles sent over interface |
| DB9_PERF_SEL_DB_SC_TILE_CULLED | DB9 | Tiles culled in total |
| DB9_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB9 | Number of detail killed tiles |
| DB9_PERF_SEL_DB_CB_LQUAD_STALLS | DB9 | Cycles Interface is stalled |
| DB9_PERF_SEL_TILE_RD_SENDS | DB9 | HTile reads. Each is 256B |
| DB9_PERF_SEL_QUAD_RD_32BYTE_REQS | DB9 | Number of 32 Byte quad read requests |
| DB9_PERF_SEL_TILE_WR_SENDS | DB9 | 32 Byte HTile writes |
| DB9_PERF_SEL_QUAD_WR_SENDS | DB9 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB9_PERF_SEL_OP_PIPE_BUSY | DB9 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB9_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB9 | Samples passing Z test during a PostZ pass |
| DB9_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB9 | Samples failing Z test during a PostZ pass |
| DB9_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB9 | Samples failing Stencil test during a PostZ pass |
| DB9_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB9 | Samples passing Z test during a PreZ pass |
| DB9_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB9 | Samples failing Z test during a PreZ pass |
| DB9_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB9 | Samples failing Stencil test during a PreZ pass |
| DB10_PERF_SEL_SC_DB_TILE_TILES | DB10 | Tiles sent over interface |
| DB10_PERF_SEL_DB_SC_TILE_CULLED | DB10 | Tiles culled in total |
| DB10_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB10 | Number of detail killed tiles |
| DB10_PERF_SEL_DB_CB_LQUAD_STALLS | DB10 | Cycles Interface is stalled |
| DB10_PERF_SEL_TILE_RD_SENDS | DB10 | HTile reads. Each is 256B |
| DB10_PERF_SEL_QUAD_RD_32BYTE_REQS | DB10 | Number of 32 Byte quad read requests |
| DB10_PERF_SEL_TILE_WR_SENDS | DB10 | 32 Byte HTile writes |
| DB10_PERF_SEL_QUAD_WR_SENDS | DB10 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB10_PERF_SEL_OP_PIPE_BUSY | DB10 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB10_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB10 | Samples passing Z test during a PostZ pass |
| DB10_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB10 | Samples failing Z test during a PostZ pass |
| DB10_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB10 | Samples failing Stencil test during a PostZ pass |
| DB10_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB10 | Samples passing Z test during a PreZ pass |
| DB10_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB10 | Samples failing Z test during a PreZ pass |
| DB10_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB10 | Samples failing Stencil test during a PreZ pass |
| DB11_PERF_SEL_SC_DB_TILE_TILES | DB11 | Tiles sent over interface |
| DB11_PERF_SEL_DB_SC_TILE_CULLED | DB11 | Tiles culled in total |
| DB11_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB11 | Number of detail killed tiles |
| DB11_PERF_SEL_DB_CB_LQUAD_STALLS | DB11 | Cycles Interface is stalled |
| DB11_PERF_SEL_TILE_RD_SENDS | DB11 | HTile reads. Each is 256B |
| DB11_PERF_SEL_QUAD_RD_32BYTE_REQS | DB11 | Number of 32 Byte quad read requests |
| DB11_PERF_SEL_TILE_WR_SENDS | DB11 | 32 Byte HTile writes |
| DB11_PERF_SEL_QUAD_WR_SENDS | DB11 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB11_PERF_SEL_OP_PIPE_BUSY | DB11 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB11_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB11 | Samples passing Z test during a PostZ pass |
| DB11_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB11 | Samples failing Z test during a PostZ pass |
| DB11_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB11 | Samples failing Stencil test during a PostZ pass |
| DB11_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB11 | Samples passing Z test during a PreZ pass |
| DB11_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB11 | Samples failing Z test during a PreZ pass |
| DB11_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB11 | Samples failing Stencil test during a PreZ pass |
| DB12_PERF_SEL_SC_DB_TILE_TILES | DB12 | Tiles sent over interface |
| DB12_PERF_SEL_DB_SC_TILE_CULLED | DB12 | Tiles culled in total |
| DB12_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB12 | Number of detail killed tiles |
| DB12_PERF_SEL_DB_CB_LQUAD_STALLS | DB12 | Cycles Interface is stalled |
| DB12_PERF_SEL_TILE_RD_SENDS | DB12 | HTile reads. Each is 256B |
| DB12_PERF_SEL_QUAD_RD_32BYTE_REQS | DB12 | Number of 32 Byte quad read requests |
| DB12_PERF_SEL_TILE_WR_SENDS | DB12 | 32 Byte HTile writes |
| DB12_PERF_SEL_QUAD_WR_SENDS | DB12 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB12_PERF_SEL_OP_PIPE_BUSY | DB12 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB12_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB12 | Samples passing Z test during a PostZ pass |
| DB12_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB12 | Samples failing Z test during a PostZ pass |
| DB12_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB12 | Samples failing Stencil test during a PostZ pass |
| DB12_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB12 | Samples passing Z test during a PreZ pass |
| DB12_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB12 | Samples failing Z test during a PreZ pass |
| DB12_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB12 | Samples failing Stencil test during a PreZ pass |
| DB13_PERF_SEL_SC_DB_TILE_TILES | DB13 | Tiles sent over interface |
| DB13_PERF_SEL_DB_SC_TILE_CULLED | DB13 | Tiles culled in total |
| DB13_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB13 | Number of detail killed tiles |
| DB13_PERF_SEL_DB_CB_LQUAD_STALLS | DB13 | Cycles Interface is stalled |
| DB13_PERF_SEL_TILE_RD_SENDS | DB13 | HTile reads. Each is 256B |
| DB13_PERF_SEL_QUAD_RD_32BYTE_REQS | DB13 | Number of 32 Byte quad read requests |
| DB13_PERF_SEL_TILE_WR_SENDS | DB13 | 32 Byte HTile writes |
| DB13_PERF_SEL_QUAD_WR_SENDS | DB13 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB13_PERF_SEL_OP_PIPE_BUSY | DB13 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB13_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB13 | Samples passing Z test during a PostZ pass |
| DB13_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB13 | Samples failing Z test during a PostZ pass |
| DB13_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB13 | Samples failing Stencil test during a PostZ pass |
| DB13_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB13 | Samples passing Z test during a PreZ pass |
| DB13_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB13 | Samples failing Z test during a PreZ pass |
| DB13_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB13 | Samples failing Stencil test during a PreZ pass |
| DB14_PERF_SEL_SC_DB_TILE_TILES | DB14 | Tiles sent over interface |
| DB14_PERF_SEL_DB_SC_TILE_CULLED | DB14 | Tiles culled in total |
| DB14_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB14 | Number of detail killed tiles |
| DB14_PERF_SEL_DB_CB_LQUAD_STALLS | DB14 | Cycles Interface is stalled |
| DB14_PERF_SEL_TILE_RD_SENDS | DB14 | HTile reads. Each is 256B |
| DB14_PERF_SEL_QUAD_RD_32BYTE_REQS | DB14 | Number of 32 Byte quad read requests |
| DB14_PERF_SEL_TILE_WR_SENDS | DB14 | 32 Byte HTile writes |
| DB14_PERF_SEL_QUAD_WR_SENDS | DB14 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB14_PERF_SEL_OP_PIPE_BUSY | DB14 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB14_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB14 | Samples passing Z test during a PostZ pass |
| DB14_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB14 | Samples failing Z test during a PostZ pass |
| DB14_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB14 | Samples failing Stencil test during a PostZ pass |
| DB14_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB14 | Samples passing Z test during a PreZ pass |
| DB14_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB14 | Samples failing Z test during a PreZ pass |
| DB14_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB14 | Samples failing Stencil test during a PreZ pass |
| DB15_PERF_SEL_SC_DB_TILE_TILES | DB15 | Tiles sent over interface |
| DB15_PERF_SEL_DB_SC_TILE_CULLED | DB15 | Tiles culled in total |
| DB15_PERF_SEL_SC_DB_QUAD_KILLED_TILES | DB15 | Number of detail killed tiles |
| DB15_PERF_SEL_DB_CB_LQUAD_STALLS | DB15 | Cycles Interface is stalled |
| DB15_PERF_SEL_TILE_RD_SENDS | DB15 | HTile reads. Each is 256B |
| DB15_PERF_SEL_QUAD_RD_32BYTE_REQS | DB15 | Number of 32 Byte quad read requests |
| DB15_PERF_SEL_TILE_WR_SENDS | DB15 | 32 Byte HTile writes |
| DB15_PERF_SEL_QUAD_WR_SENDS | DB15 | Cycles quad is sending write requests to the memory interface block of the DB |
| DB15_PERF_SEL_OP_PIPE_BUSY | DB15 | Cycles the quad OP pipe of the DB is busy (including memory fetches, but not initial startup) |
| DB15_PERF_SEL_POSTZ_SAMPLES_PASSING_Z | DB15 | Samples passing Z test during a PostZ pass |
| DB15_PERF_SEL_POSTZ_SAMPLES_FAILING_Z | DB15 | Samples failing Z test during a PostZ pass |
| DB15_PERF_SEL_POSTZ_SAMPLES_FAILING_S | DB15 | Samples failing Stencil test during a PostZ pass |
| DB15_PERF_SEL_PREZ_SAMPLES_PASSING_Z | DB15 | Samples passing Z test during a PreZ pass |
| DB15_PERF_SEL_PREZ_SAMPLES_FAILING_Z | DB15 | Samples failing Z test during a PreZ pass |
| DB15_PERF_SEL_PREZ_SAMPLES_FAILING_S | DB15 | Samples failing Stencil test during a PreZ pass |
| **CB** | - | - |
| CB0_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB0 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB0_PERF_SEL_CM_MC_WRITE_REQUEST | CB0 | Number of 32-byte cmask mc write requests. |
| CB0_PERF_SEL_FC_MC_WRITE_REQUEST | CB0 | Number of 32-byte fmask mc write requests. |
| CB0_PERF_SEL_CC_MC_WRITE_REQUEST | CB0 | Number of 32-byte color mc write requests. |
| CB0_PERF_SEL_CM_MC_READ_REQUEST | CB0 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB0_PERF_SEL_FC_MC_READ_REQUEST | CB0 | Number of 32-byte fmask mc read requests. |
| CB0_PERF_SEL_CC_MC_READ_REQUEST | CB0 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB0_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB0 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB0_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB0 | Number of 32-byte fmask mc DCC write requests. |
| CB0_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB0 | Number of 32-byte fmask mc DCC read requests. |
| CB1_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB1 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB1_PERF_SEL_CM_MC_WRITE_REQUEST | CB1 | Number of 32-byte cmask mc write requests. |
| CB1_PERF_SEL_FC_MC_WRITE_REQUEST | CB1 | Number of 32-byte fmask mc write requests. |
| CB1_PERF_SEL_CC_MC_WRITE_REQUEST | CB1 | Number of 32-byte color mc write requests. |
| CB1_PERF_SEL_CM_MC_READ_REQUEST | CB1 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB1_PERF_SEL_FC_MC_READ_REQUEST | CB1 | Number of 32-byte fmask mc read requests. |
| CB1_PERF_SEL_CC_MC_READ_REQUEST | CB1 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB1_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB1 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB1_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB1 | Number of 32-byte fmask mc DCC write requests. |
| CB1_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB1 | Number of 32-byte fmask mc DCC read requests. |
| CB2_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB2 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB2_PERF_SEL_CM_MC_WRITE_REQUEST | CB2 | Number of 32-byte cmask mc write requests. |
| CB2_PERF_SEL_FC_MC_WRITE_REQUEST | CB2 | Number of 32-byte fmask mc write requests. |
| CB2_PERF_SEL_CC_MC_WRITE_REQUEST | CB2 | Number of 32-byte color mc write requests. |
| CB2_PERF_SEL_CM_MC_READ_REQUEST | CB2 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB2_PERF_SEL_FC_MC_READ_REQUEST | CB2 | Number of 32-byte fmask mc read requests. |
| CB2_PERF_SEL_CC_MC_READ_REQUEST | CB2 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB2_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB2 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB2_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB2 | Number of 32-byte fmask mc DCC write requests. |
| CB2_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB2 | Number of 32-byte fmask mc DCC read requests. |
| CB3_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB3 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB3_PERF_SEL_CM_MC_WRITE_REQUEST | CB3 | Number of 32-byte cmask mc write requests. |
| CB3_PERF_SEL_FC_MC_WRITE_REQUEST | CB3 | Number of 32-byte fmask mc write requests. |
| CB3_PERF_SEL_CC_MC_WRITE_REQUEST | CB3 | Number of 32-byte color mc write requests. |
| CB3_PERF_SEL_CM_MC_READ_REQUEST | CB3 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB3_PERF_SEL_FC_MC_READ_REQUEST | CB3 | Number of 32-byte fmask mc read requests. |
| CB3_PERF_SEL_CC_MC_READ_REQUEST | CB3 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB3_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB3 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB3_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB3 | Number of 32-byte fmask mc DCC write requests. |
| CB3_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB3 | Number of 32-byte fmask mc DCC read requests. |
| CB4_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB4 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB4_PERF_SEL_CM_MC_WRITE_REQUEST | CB4 | Number of 32-byte cmask mc write requests. |
| CB4_PERF_SEL_FC_MC_WRITE_REQUEST | CB4 | Number of 32-byte fmask mc write requests. |
| CB4_PERF_SEL_CC_MC_WRITE_REQUEST | CB4 | Number of 32-byte color mc write requests. |
| CB4_PERF_SEL_CM_MC_READ_REQUEST | CB4 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB4_PERF_SEL_FC_MC_READ_REQUEST | CB4 | Number of 32-byte fmask mc read requests. |
| CB4_PERF_SEL_CC_MC_READ_REQUEST | CB4 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB4_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB4 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB4_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB4 | Number of 32-byte fmask mc DCC write requests. |
| CB4_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB4 | Number of 32-byte fmask mc DCC read requests. |
| CB5_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB5 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB5_PERF_SEL_CM_MC_WRITE_REQUEST | CB5 | Number of 32-byte cmask mc write requests. |
| CB5_PERF_SEL_FC_MC_WRITE_REQUEST | CB5 | Number of 32-byte fmask mc write requests. |
| CB5_PERF_SEL_CC_MC_WRITE_REQUEST | CB5 | Number of 32-byte color mc write requests. |
| CB5_PERF_SEL_CM_MC_READ_REQUEST | CB5 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB5_PERF_SEL_FC_MC_READ_REQUEST | CB5 | Number of 32-byte fmask mc read requests. |
| CB5_PERF_SEL_CC_MC_READ_REQUEST | CB5 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB5_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB5 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB5_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB5 | Number of 32-byte fmask mc DCC write requests. |
| CB5_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB5 | Number of 32-byte fmask mc DCC read requests. |
| CB6_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB6 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB6_PERF_SEL_CM_MC_WRITE_REQUEST | CB6 | Number of 32-byte cmask mc write requests. |
| CB6_PERF_SEL_FC_MC_WRITE_REQUEST | CB6 | Number of 32-byte fmask mc write requests. |
| CB6_PERF_SEL_CC_MC_WRITE_REQUEST | CB6 | Number of 32-byte color mc write requests. |
| CB6_PERF_SEL_CM_MC_READ_REQUEST | CB6 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB6_PERF_SEL_FC_MC_READ_REQUEST | CB6 | Number of 32-byte fmask mc read requests. |
| CB6_PERF_SEL_CC_MC_READ_REQUEST | CB6 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB6_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB6 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB6_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB6 | Number of 32-byte fmask mc DCC write requests. |
| CB6_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB6 | Number of 32-byte fmask mc DCC read requests. |
| CB7_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB7 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB7_PERF_SEL_CM_MC_WRITE_REQUEST | CB7 | Number of 32-byte cmask mc write requests. |
| CB7_PERF_SEL_FC_MC_WRITE_REQUEST | CB7 | Number of 32-byte fmask mc write requests. |
| CB7_PERF_SEL_CC_MC_WRITE_REQUEST | CB7 | Number of 32-byte color mc write requests. |
| CB7_PERF_SEL_CM_MC_READ_REQUEST | CB7 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB7_PERF_SEL_FC_MC_READ_REQUEST | CB7 | Number of 32-byte fmask mc read requests. |
| CB7_PERF_SEL_CC_MC_READ_REQUEST | CB7 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB7_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB7 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB7_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB7 | Number of 32-byte fmask mc DCC write requests. |
| CB7_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB7 | Number of 32-byte fmask mc DCC read requests. |
| CB8_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB8 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB8_PERF_SEL_CM_MC_WRITE_REQUEST | CB8 | Number of 32-byte cmask mc write requests. |
| CB8_PERF_SEL_FC_MC_WRITE_REQUEST | CB8 | Number of 32-byte fmask mc write requests. |
| CB8_PERF_SEL_CC_MC_WRITE_REQUEST | CB8 | Number of 32-byte color mc write requests. |
| CB8_PERF_SEL_CM_MC_READ_REQUEST | CB8 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB8_PERF_SEL_FC_MC_READ_REQUEST | CB8 | Number of 32-byte fmask mc read requests. |
| CB8_PERF_SEL_CC_MC_READ_REQUEST | CB8 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB8_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB8 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB8_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB8 | Number of 32-byte fmask mc DCC write requests. |
| CB8_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB8 | Number of 32-byte fmask mc DCC read requests. |
| CB9_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB9 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB9_PERF_SEL_CM_MC_WRITE_REQUEST | CB9 | Number of 32-byte cmask mc write requests. |
| CB9_PERF_SEL_FC_MC_WRITE_REQUEST | CB9 | Number of 32-byte fmask mc write requests. |
| CB9_PERF_SEL_CC_MC_WRITE_REQUEST | CB9 | Number of 32-byte color mc write requests. |
| CB9_PERF_SEL_CM_MC_READ_REQUEST | CB9 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB9_PERF_SEL_FC_MC_READ_REQUEST | CB9 | Number of 32-byte fmask mc read requests. |
| CB9_PERF_SEL_CC_MC_READ_REQUEST | CB9 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB9_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB9 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB9_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB9 | Number of 32-byte fmask mc DCC write requests. |
| CB9_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB9 | Number of 32-byte fmask mc DCC read requests. |
| CB10_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB10 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB10_PERF_SEL_CM_MC_WRITE_REQUEST | CB10 | Number of 32-byte cmask mc write requests. |
| CB10_PERF_SEL_FC_MC_WRITE_REQUEST | CB10 | Number of 32-byte fmask mc write requests. |
| CB10_PERF_SEL_CC_MC_WRITE_REQUEST | CB10 | Number of 32-byte color mc write requests. |
| CB10_PERF_SEL_CM_MC_READ_REQUEST | CB10 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB10_PERF_SEL_FC_MC_READ_REQUEST | CB10 | Number of 32-byte fmask mc read requests. |
| CB10_PERF_SEL_CC_MC_READ_REQUEST | CB10 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB10_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB10 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB10_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB10 | Number of 32-byte fmask mc DCC write requests. |
| CB10_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB10 | Number of 32-byte fmask mc DCC read requests. |
| CB11_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB11 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB11_PERF_SEL_CM_MC_WRITE_REQUEST | CB11 | Number of 32-byte cmask mc write requests. |
| CB11_PERF_SEL_FC_MC_WRITE_REQUEST | CB11 | Number of 32-byte fmask mc write requests. |
| CB11_PERF_SEL_CC_MC_WRITE_REQUEST | CB11 | Number of 32-byte color mc write requests. |
| CB11_PERF_SEL_CM_MC_READ_REQUEST | CB11 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB11_PERF_SEL_FC_MC_READ_REQUEST | CB11 | Number of 32-byte fmask mc read requests. |
| CB11_PERF_SEL_CC_MC_READ_REQUEST | CB11 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB11_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB11 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB11_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB11 | Number of 32-byte fmask mc DCC write requests. |
| CB11_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB11 | Number of 32-byte fmask mc DCC read requests. |
| CB12_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB12 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB12_PERF_SEL_CM_MC_WRITE_REQUEST | CB12 | Number of 32-byte cmask mc write requests. |
| CB12_PERF_SEL_FC_MC_WRITE_REQUEST | CB12 | Number of 32-byte fmask mc write requests. |
| CB12_PERF_SEL_CC_MC_WRITE_REQUEST | CB12 | Number of 32-byte color mc write requests. |
| CB12_PERF_SEL_CM_MC_READ_REQUEST | CB12 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB12_PERF_SEL_FC_MC_READ_REQUEST | CB12 | Number of 32-byte fmask mc read requests. |
| CB12_PERF_SEL_CC_MC_READ_REQUEST | CB12 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB12_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB12 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB12_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB12 | Number of 32-byte fmask mc DCC write requests. |
| CB12_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB12 | Number of 32-byte fmask mc DCC read requests. |
| CB13_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB13 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB13_PERF_SEL_CM_MC_WRITE_REQUEST | CB13 | Number of 32-byte cmask mc write requests. |
| CB13_PERF_SEL_FC_MC_WRITE_REQUEST | CB13 | Number of 32-byte fmask mc write requests. |
| CB13_PERF_SEL_CC_MC_WRITE_REQUEST | CB13 | Number of 32-byte color mc write requests. |
| CB13_PERF_SEL_CM_MC_READ_REQUEST | CB13 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB13_PERF_SEL_FC_MC_READ_REQUEST | CB13 | Number of 32-byte fmask mc read requests. |
| CB13_PERF_SEL_CC_MC_READ_REQUEST | CB13 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB13_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB13 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB13_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB13 | Number of 32-byte fmask mc DCC write requests. |
| CB13_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB13 | Number of 32-byte fmask mc DCC read requests. |
| CB14_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB14 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB14_PERF_SEL_CM_MC_WRITE_REQUEST | CB14 | Number of 32-byte cmask mc write requests. |
| CB14_PERF_SEL_FC_MC_WRITE_REQUEST | CB14 | Number of 32-byte fmask mc write requests. |
| CB14_PERF_SEL_CC_MC_WRITE_REQUEST | CB14 | Number of 32-byte color mc write requests. |
| CB14_PERF_SEL_CM_MC_READ_REQUEST | CB14 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB14_PERF_SEL_FC_MC_READ_REQUEST | CB14 | Number of 32-byte fmask mc read requests. |
| CB14_PERF_SEL_CC_MC_READ_REQUEST | CB14 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB14_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB14 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB14_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB14 | Number of 32-byte fmask mc DCC write requests. |
| CB14_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB14 | Number of 32-byte fmask mc DCC read requests. |
| CB15_PERF_SEL_DRAWN_QUAD_FRAGMENT | CB15 | This is the number of drawn quad fragments. Use CB_PERF_SEL_DRAWN_BUSY as denominator to get per clock rates. Filtering using CB_PERFCOUNTER_FILTER fields has an effect in this mode. |
| CB15_PERF_SEL_CM_MC_WRITE_REQUEST | CB15 | Number of 32-byte cmask mc write requests. |
| CB15_PERF_SEL_FC_MC_WRITE_REQUEST | CB15 | Number of 32-byte fmask mc write requests. |
| CB15_PERF_SEL_CC_MC_WRITE_REQUEST | CB15 | Number of 32-byte color mc write requests. |
| CB15_PERF_SEL_CM_MC_READ_REQUEST | CB15 | Number of 32-byte cmask mc read requests. Cmask does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB15_PERF_SEL_FC_MC_READ_REQUEST | CB15 | Number of 32-byte fmask mc read requests. |
| CB15_PERF_SEL_CC_MC_READ_REQUEST | CB15 | Number of 32-byte color mc read requests. Color does not make 32-byte requests, so the counter will report the equivalent number of 32-byte requests. |
| CB15_PERF_SEL_EXPORT_32_ABGR_QUAD_FRAGMENT | CB15 | Number of EXPORT_32_ABGR quad fragments. It takes two clocks to send the src color data for these. |
| CB15_PERF_SEL_FC_MC_DCC_WRITE_REQUEST | CB15 | Number of 32-byte fmask mc DCC write requests. |
| CB15_PERF_SEL_FC_MC_DCC_READ_REQUEST | CB15 | Number of 32-byte fmask mc DCC read requests. |
| **GRBM** | - | - |
| GRBM_PERF_SEL_COUNT | GRBM | Tie High - Count Number of Clocks |
| GRBM_PERF_SEL_GUI_ACTIVE | GRBM | The GUI is Active |
| **GPUTime** | - | - |
| GPUTime_BOTTOM_TO_BOTTOM_DURATION | GPUTime | delta between the previous command reaching bottom of pipe and the current command reaching bottom of pipe, will not include latency of first data to travel through pipeline, best for large data sets. |
| GPUTime_BOTTOM_TO_BOTTOM_START | GPUTime | time of the previous command reaching bottom of pipe |
| GPUTime_BOTTOM_TO_BOTTOM_END | GPUTime | time of the current command reaching bottom of pipe |
| GPUTime_TOP_TO_BOTTOM_DURATION | GPUTime | execution duration of the current command from top of pipe to bottom of pipe, may include overhead of time in queue |
| GPUTime_TOP_TO_BOTTOM_START | GPUTime | time that the current command reaches the top of pipe |
| GPUTime_TOP_TO_BOTTOM_END | GPUTime | time that the current command reaches the bottom of pipe |

</details>
