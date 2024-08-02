
## References


## Notes

**Subslice** -<br/>
**EU** -<br/>
**FPU** -<br/>
**FPU0 pipe** -<br/>
**FPU1 pipe** -<br/>
**Send pipe** -<br/>
**GTI** -<br/>
**3D Pipe** - Contains: Input Assembler, VS, HS, DS, GS, Clipper, Rasterizer, PS, Output Merger.<br/>
**Output Merger** - blending?<br/>
**Command Streamer** - <br/>
**Resource Streamer** - <br/>
**Stream Output** - <br/>
**Color Cache** - <br/>
**Depth Cache** - <br/>
**Stencil Cache** - <br/>
**IC** - <br/>
**Thread Dispatcher** - <br/>

## UHD 620 (VK_KHR_performance_query)

<details>

| name | category | description |
|---|---|---|
| GpuTime | GPU | Time elapsed on the GPU during the measurement. |
| GpuCoreClocks | GPU | The total number of GPU core clocks elapsed during the measurement. |
| AvgGpuCoreFrequencyMHz | GPU | Average GPU Core Frequency in the measurement. |
| VsThreads | EU Array/Vertex Shader | The total number of vertex shader hardware threads dispatched. |
| HsThreads | EU Array/Hull Shader | The total number of hull shader hardware threads dispatched. |
| DsThreads | EU Array/Domain Shader | The total number of domain shader hardware threads dispatched. |
| GsThreads | EU Array/Geometry Shader | The total number of geometry shader hardware threads dispatched. |
| PsThreads | EU Array/Pixel Shader | The total number of pixel shader hardware threads dispatched. |
| CsThreads | EU Array/Compute Shader | The total number of compute shader hardware threads dispatched. |
| GpuBusy | GPU | The percentage of time in which the GPU has been processing GPU commands. |
| EuActive | EU Array | The percentage of time in which the Execution Units were actively processing. |
| EuStall | EU Array | The percentage of time in which the Execution Units were stalled. |
| EuFpuBothActive | EU Array/Pipes | The percentage of time in which both EU FPU pipelines were actively processing. |
| VsFpu0Active | EU Array/Vertex Shader | The percentage of time in which EU FPU0 pipeline was actively processing a vertex shader instruction. |
| VsFpu1Active | EU Array/Vertex Shader | The percentage of time in which EU FPU1 pipeline was actively processing a vertex shader instruction. |
| VsSendActive | EU Array/Vertex Shader | The percentage of time in which EU send pipeline was actively processing a vertex shader instruction. |
| PsFpu0Active | EU Array/Pixel Shader | The percentage of time in which EU FPU0 pipeline was actively processing a pixel shader instruction. |
| PsFpu1Active | EU Array/Pixel Shader | The percentage of time in which EU FPU1 pipeline was actively processing a pixel shader instruction. |
| PsSendActive | EU Array/Pixel Shader | The percentage of time in which EU send pipeline was actively processing a pixel shader instruction. |
| PsEuBothFpuActive | 3D Pipe/Pixel Shader | The percentage of time in which pixel shaders were processed actively on the both FPUs. |
| Sampler0Busy | Sampler | The percentage of time in which Sampler 0 has been processing EU requests. |
| Sampler1Busy | Sampler | The percentage of time in which Sampler 1 has been processing EU requests. |
| SamplersBusy | Sampler | The percentage of time in which samplers have been processing EU requests. |
| Sampler0Bottleneck | Sampler | The percentage of time in which Sampler 0 has been slowing down the pipe when processing EU requests. |
| Sampler1Bottleneck | Sampler | The percentage of time in which Sampler 1 has been slowing down the pipe when processing EU requests. |
| RasterizedPixels | 3D Pipe/Rasterizer | The total number of rasterized pixels. |
| HiDepthTestFails | 3D Pipe/Rasterizer/Hi-Depth Test | The total number of pixels dropped on early hierarchical depth test. |
| EarlyDepthTestFails | 3D Pipe/Rasterizer/Early Depth Test | The total number of pixels dropped on early depth test. |
| SamplesKilledInPs | 3D Pipe/Pixel Shader | The total number of samples or pixels dropped in pixel shaders. |
| PixelsFailingPostPsTests | 3D Pipe/Output Merger | The total number of pixels dropped on post-PS alpha, stencil, or depth tests. |
| SamplesWritten | 3D Pipe/Output Merger | The total number of samples or pixels written to all render targets. |
| SamplesBlended | 3D Pipe/Output Merger | The total number of blended samples or pixels written to all render targets. |
| SamplerTexels | Sampler/Sampler Input | The total number of texels seen on input (with 2x2 accuracy) in all sampler units. |
| SamplerTexelMisses | Sampler/Sampler Cache | The total number of texels lookups (with 2x2 accuracy) that missed L1 sampler cache. |
| SamplerL1Misses | Sampler/Sampler Cache | The total number of sampler cache misses in all LODs in all sampler units. |
| SlmBytesRead | L3/Data Port/SLM | The total number of GPU memory bytes read from shared local memory. |
| SlmBytesWritten | L3/Data Port/SLM | The total number of GPU memory bytes written into shared local memory. |
| ShaderMemoryAccesses | L3/Data Port | The total number of shader memory accesses to L3. |
| ShaderAtomics | L3/Data Port/Atomics | The total number of shader atomic memory accesses. |
| L3Lookups | L3/TAG | The total number of L3 cache lookup accesses w/o IC. |
| L3Misses | L3/TAG | The total number of L3 misses. |
| L3SamplerThroughput | L3/Sampler | The total number of GPU memory bytes transferred between samplers and L3 caches. |
| L3ShaderThroughput | L3/Data Port | The total number of GPU memory bytes transferred between shaders and L3 caches w/o URB. |
| ShaderBarriers | EU Array/Barrier | The total number of shader barrier messages. |
| GtiVfThroughput | GTI/3D Pipe | The total number of GPU memory bytes transferred between 3D Pipeline (Command Dispatch, Input Assembly and Stream Output) and GTI. |
| GtiDepthThroughput | GTI/Depth Cache | The total number of GPU memory bytes transferred between depth caches and GTI. |
| GtiRccThroughput | GTI/Color Cache | The total number of GPU memory bytes transferred between render color caches and GTI. |
| GtiL3Throughput | GTI/L3 | The total number of GPU memory bytes transferred between L3 caches and GTI. |
| GtiHdcLookupsThroughput | GTI/L3 | The total number of GPU memory bytes transferred between GTI and HDC, when HDC is doing TLB lookups. |
| GtiReadThroughput | GTI | The total number of GPU memory bytes read from GTI. |
| GtiWriteThroughput | GTI | The total number of GPU memory bytes written to GTI. |
| SamplerBottleneck | Sampler | The percentage of time in which samplers have been slowing down the pipe when processing EU requests. |
| Fpu0Active | EU Array/Pipes | The percentage of time in which EU FPU0 pipeline was actively processing. |
| Fpu1Active | EU Array/Pipes | The percentage of time in which EU FPU1 pipeline was actively processing. |
| EuAvgIpcRate | EU Array | The average rate of IPC calculated for 2 FPU pipelines. |
| EuSendActive | EU Array/Pipes | The percentage of time in which EU send pipeline was actively processing. |
| EuThreadOccupancy | EU Array | The percentage of time in which hardware threads occupied EUs. |
| TypedBytesRead | L3/Data Port | The total number of typed memory bytes read via Data Port. |
| TypedBytesWritten | L3/Data Port | The total number of untyped memory bytes written via Data Port. |
| UntypedBytesRead | L3/Data Port | The total number of typed memory bytes read via Data Port. |
| UntypedBytesWritten | L3/Data Port | The total number of untyped memory bytes written via Data Port. |
| VfBottleneck | 3D Pipe/Input Assembler | The percentage of time in which vertex fetch pipeline stage was slowing down the 3D pipeline. |
| VsBottleneck | 3D Pipe/Vertex Shader | The percentage of time in which vertex shader pipeline stage was slowing down the 3D pipeline. |
| HsBottleneck | 3D Pipe/Hull Shader | The percentage of time in which hull shader pipeline stage was slowing down the 3D pipeline. |
| DsBottleneck | 3D Pipe/Domain Shader | The percentage of time in which domain shader pipeline stage was slowing down the 3D pipeline. |
| GsBottleneck | 3D Pipe/Geometry Shader | The percentage of time in which geometry shader pipeline stage was slowing down the 3D pipeline. |
| SoBottleneck | 3D Pipe/Stream Output | The percentage of time in which stream output pipeline stage was slowing down the 3D pipeline. |
| ClBottleneck | 3D Pipe/Clipper | The percentage of time in which clipper pipeline stage was slowing down the 3D pipeline. |
| SfBottleneck | 3D Pipe/Rasterizer/Strip-Fans | The percentage of time in which strip-fans pipeline stage was slowing down the 3D pipeline. |
| HiDepthBottleneck | 3D Pipe/Rasterizer/Hi-Depth Test | The percentage of time in which early hierarchical depth test pipeline stage was slowing down the 3D pipeline. |
| EarlyDepthBottleneck | 3D Pipe/Rasterizer/Early Depth Test | The percentage of time in which early depth test pipeline stage was slowing down the 3D pipeline. |
| BcBottleneck | 3D Pipe/Rasterizer/Barycentric Calc | The percentage of time in which barycentric coordinates calculation pipeline stage was slowing down the 3D pipeline. |
| HsStall | 3D Pipe/Hull Shader | The percentage of time in which hull stall pipeline stage was stalled. |
| DsStall | 3D Pipe/Domain Shader | The percentage of time in which domain shader pipeline stage was stalled. |
| SoStall | 3D Pipe/Stream Output | The percentage of time in which stream-output pipeline stage was stalled. |
| ClStall | 3D Pipe/Clipper | The percentage of time in which clipper pipeline stage was stalled. |
| SfStall | 3D Pipe/Rasterizer/Strip-Fans | The percentage of time in which strip-fans pipeline stage was stalled. |
| GtiCmdStreamerMemoryReads | GTI/3D Pipe/Command Streamer | The total number of GTI memory reads from Command Streamer. |
| GtiRsMemoryReads | GTI/3D Pipe/Resource Streamer | The total number of GTI memory reads from Resource Streamer. |
| GtiVfMemoryReads | GTI/3D Pipe/Vertex Fetch | The total number of GTI memory reads from Vertex Fetch. |
| GtiRccMemoryReads | GTI/Color Cache | The total number of GTI memory reads from Render Color Cache (Render Color Cache misses). |
| GtiMscMemoryReads | GTI/Color Cache | The total number of GTI memory reads from Multisampling Color Cache (Multisampling Color Cache misses). |
| GtiHizMemoryReads | GTI/Depth Cache | The total number of GTI memory reads from Hierarchical Depth Cache (Hi-Depth Cache misses). |
| GtiStcMemoryReads | GTI/Depth Cache | The total number of GTI memory reads from Stencil Cache (Stencil Cache misses). |
| GtiRczMemoryReads | GTI/Depth Cache | The total number of GTI memory reads from Render Depth Cache (Render Depth Cache misses). |
| GtiMemoryReads | GTI | The total number of GTI memory reads. |
| GtiL3Bank0Reads | GTI/L3 | The total number of GTI memory reads from L3 Bank 0 (L3 Cache misses). |
| GtiL3Bank1Reads | GTI/L3 | The total number of GTI memory reads from L3 Bank 1 (L3 Cache misses). |
| GtiL3Bank2Reads | GTI/L3 | The total number of GTI memory reads from L3 Bank 2 (L3 Cache misses). |
| GtiL3Bank3Reads | GTI/L3 | The total number of GTI memory reads from L3 Bank 3 (L3 Cache misses). |
| GtiL3Reads | GTI/L3 | The total number of GTI memory reads from L3 (L3 Cache misses). |
| GtiRingAccesses | GTI | The total number of all accesses from GTI to the ring. |
| GtiCmdStreamerMemoryWrites | GTI/3D Pipe/Command Streamer | The total number of GTI memory writes from Command Streamer. |
| GtiSoMemoryWrites | GTI/3D Pipe/Stream Output | The total number of GTI memory writes from Stream Output. |
| GtiRccMemoryWrites | GTI/Color Cache | The total number of GTI memory writes from Render Color Cache (Render Color Cache invalidations). |
| GtiMscMemoryWrites | GTI/Color Cache | The total number of GTI memory writes from Multisampling Color Cache (Multisampling Color Cache invalidations). |
| GtiHizMemoryWrites | GTI/Depth Cache | The total number of GTI memory writes from Hierarchical Depth Cache. |
| GtiStcMemoryWrites | GTI/Depth Cache | The total number of GTI memory writes from Stencil Cache. |
| GtiRczMemoryWrites | GTI/Depth Cache | The total number of GTI memory writes from Render Depth Cache. |
| GtiMemoryWrites | GTI | The total number of GTI memory writes. |
| GtiL3Bank0Writes | GTI/L3 | The total number of GTI memory writes from L3 Bank 0 (L3 Bank 0 invalidations). |
| GtiL3Bank1Writes | GTI/L3 | The total number of GTI memory writes from L3 Bank 1 (L3 Bank 1 invalidations). |
| GtiL3Bank2Writes | GTI/L3 | The total number of GTI memory writes from L3 Bank 2 (L3 Bank 2 invalidations). |
| GtiL3Bank3Writes | GTI/L3 | The total number of GTI memory writes from L3 Bank 3 (L3 Bank 3 invalidations). |
| GtiL3Writes | GTI/L3 | The total number of GTI memory writes from L3 (L3 invalidations). |
| EuUntypedReads0 | L3/Data Port | The subslice 0 EU Untyped Reads subslice 0. |
| EuTypedReads0 | L3/Data Port | The subslice 0 EU Typed Reads subslice 0. |
| EuUntypedWrites0 | L3/Data Port | The subslice 0 EU Untyped Writes subslice 0. |
| EuTypedWrites0 | L3/Data Port | The subslice 0 EU Typed Writes subslice 0. |
| EuUntypedAtomics0 | L3/Data Port | The subslice 0 EU Untyped Atomics subslice 0. |
| EuTypedAtomics0 | L3/Data Port | The subslice 0 EU Typed Atomics subslice 0. |
| EuA64UntypedReads0 | L3/Data Port | The subslice 0 EU A64 Untyped Reads subslice 0. |
| EuA64UntypedWrites0 | L3/Data Port | The subslice 0 EU A64 Untyped Writes subslice 0. |
| TypedReads0 | L3/Data Port | The subslice 0 typed reads. |
| TypedWrites0 | L3/Data Port | The subslice 0 typed writes. |
| UntypedReads0 | L3/Data Port | The subslice 0 untyped reads (including SLM reads). |
| UntypedWrites0 | L3/Data Port | The subslice 0 untyped writes (including SLM writes). |
| TypedAtomics0 | L3/Data Port | The subslice 0 typed atomics. |
| TypedReadsPerCacheLine | L3/Data Port | The ratio of EU typed read requests to L3 cache line reads. |
| TypedWritesPerCacheLine | L3/Data Port | The ratio of EU typed write requests to L3 cache line writes. |
| UntypedReadsPerCacheLine | L3/Data Port | The ratio of EU untyped read requests to L3 cache line reads. |
| UntypedWritesPerCacheLine | L3/Data Port | The ratio of EU untyped write requests to L3 cache line writes. |
| TypedAtomicsPerCacheLine | L3/Data Port | The ratio of EU typed atomics requests to L3 cache line writes. |
| EuHybridFpu0Instruction | EU Array/Pipes/Instructions | The percentage of time in which execution units were actively processing hybrid instructions on FPU0. |
| EuHybridFpu1Instruction | EU Array/Pipes/Instructions | The percentage of time in which execution units were actively processing hybrid instructions on FPU1. |
| EuTernaryFpu0Instruction | EU Array/Pipes/Instructions | The percentage of time in which execution units were actively processing ternary instructions on FPU0. |
| EuTernaryFpu1Instruction | EU Array/Pipes/Instructions | The percentage of time in which execution units were actively processing ternary instructions on FPU1. |
| EuBinaryFpu0Instruction | EU Array/Pipes/Instructions | The percentage of time in which execution units were actively processing binary instructions on FPU0. |
| EuBinaryFpu1Instruction | EU Array/Pipes/Instructions | The percentage of time in which execution units were actively processing binary instructions on FPU1. |
| EuMoveFpu0Instruction | EU Array/Pipes/Instructions | The percentage of time in which execution units were actively processing move instructions on FPU0. |
| EuMoveFpu1Instruction | EU Array/Pipes/Instructions | The percentage of time in which execution units were actively processing move instructions on FPU1. |
| SamplerAccesses | Sampler | The total number of messages send to samplers. |
| L3Accesses | L3 | The total number of L3 accesses from all entities. |
| L3ShaderLookups | L3/TAG | The total number of L3 cache lookup accesses w/o IC. |
| L3TotalThroughput | L3 | The total number of GPU memory bytes transferred via L3. |
| L3Bank00Accesses | L3 | The total number of accesses to L3 Bank 00. |
| L3Bank01Accesses | L3 | The total number of accesses to L3 Bank 01. |
| L3Bank02Accesses | L3 | The total number of accesses to L3 Bank 02. |
| L3Bank03Accesses | L3 | The total number of accesses to L3 Bank 03. |
| L3Bank00IcAccesses | L3/IC | The total number of accesses to L3 Bank 00 from IC cache. |
| L3Bank00IcHits | L3/IC | The total number of hits in L3 Bank 00 from IC cache. |
| PolyDataReady | GPU/3D Pipe/Strip-Fans | The percentage of time in which geometry pipeline output is ready |
| NonSamplerShader00AccessStalledOnL3 | GPU/Data Port | Percentage of time when HDC has messges to L3, but it's stalled due to lack of credits (s0.ss0) |
| NonSamplerShader01AccessStalledOnL3 | GPU/Data Port | Percentage of time when HDC has messges to L3, but it's stalled due to lack of credits (s0.ss1) |
| NonSamplerShader02AccessStalledOnL3 | GPU/Data Port | Percentage of time when HDC has messges to L3, but it's stalled due to lack of credits (s0.ss2) |
| GTRequestQueueFull | GTI | The percentage of time when SQ is filled above a threshold (usually 48 entries) |
| L30Bank0Stalled | GTI/L3 | The percentage of time in which slice0 L3 bank0 is stalled |
| L30Bank1Stalled | GTI/L3 | The percentage of time in which slice0 L3 bank1 is stalled |
| L30Bank1Active | GTI/L3 | The percentage of time in which slice0 L3 bank1 is active |
| L30Bank0Active | GTI/L3 | The percentage of time in which slice0 L3 bank0 is active |
| L30Bank2Stalled | GTI/L3 | The percentage of time in which slice0 L3 bank2 is stalled |
| L30Bank2Active | GTI/L3 | The percentage of time in which slice0 L3 bank2 is active |
| L30Bank3Stalled | GTI/L3 | The percentage of time in which slice0 L3 bank3 is stalled |
| L30Bank3Active | GTI/L3 | The percentage of time in which slice0 L3 bank3 is active |
| PixelData0Ready | GPU/Rasterizer/Early Depth Test | The percentage of time in which slice0 post-EarlyZ pixel data is ready (after early Z tests have been applied) |
| Rasterizer0InputAvailable | GPU/Rasterizer | The percentage of time in which slice0 rasterizer input is available |
| PSOutput0Available | GPU/3D Pipe | The percentage of time in which slice0 PS output is available |
| PixelValues0Ready | GPU/3D Pipe | The percentage of time in which slice0 pixel values are ready |
| Rasterizer0OutputReady | GPU/Rasterizer | The percentage of time in which slice0 rasterizer output is ready |
| Sampler01InputAvailable | GPU/Sampler | The percentage of time in which slice0 subslice1 sampler input is available |
| Sampler02InputAvailable | GPU/Sampler | The percentage of time in which slice0 subslice2 sampler input is available |
| Sampler00InputAvailable | GPU/Sampler | The percentage of time in which slice0 subslice0 sampler input is available |
| Sampler02OutputReady | GPU/Sampler | The percentage of time in which slice0 subslice2 sampler output is ready |
| Sampler00OutputReady | GPU/Sampler | The percentage of time in which slice0 subslice0 sampler output is ready |
| Sampler01OutputReady | GPU/Sampler | The percentage of time in which slice0 subslice1 sampler output is ready |
| NonPSThread01ReadyForDispatch | GPU/Thread Dispatcher | The percentage of time in which non-PS thread is ready for dispatch on slice0 subslice1 thread dispatcher |
| PSThread00ReadyForDispatch | GPU/Thread Dispatcher | The percentage of time in which PS thread is ready for dispatch on slice0 subslice0 thread dispatcher |
| NonPSThread00ReadyForDispatch | GPU/Thread Dispatcher | The percentage of time in which non-PS thread is ready for dispatch on slice0 subslice0 thread dispatcher |
| PSThread02ReadyForDispatch | GPU/Thread Dispatcher | The percentage of time in which PS thread is ready for dispatch on slice0 subslice2 thread dispatcher |
| NonPSThread02ReadyForDispatch | GPU/Thread Dispatcher | The percentage of time in which non-PS thread is ready for dispatch on slice0 subslice2 thread dispatcher |
| PSThread01ReadyForDispatch | GPU/Thread Dispatcher | The percentage of time in which PS thread is ready for dispatch on slice0 subslice1 thread dispatcher |
| ThreadHeader01ReadyPort0 | GPU/Thread Dispatcher | The percentage of time in which thread header is ready on slice0 subslice1 thread dispatcher port 0 |
| ThreadHeader00ReadyPort1 | GPU/Thread Dispatcher | The percentage of time in which thread header is ready on slice0 subslice0 thread dispatcher port 1 |
| ThreadHeader00ReadyPort0 | GPU/Thread Dispatcher | The percentage of time in which thread header is ready on slice0 subslice0 thread dispatcher port 0 |
| ThreadHeader02ReadyPort1 | GPU/Thread Dispatcher | The percentage of time in which thread header is ready on slice0 subslice2 thread dispatcher port 1 |
| ThreadHeader02ReadyPort0 | GPU/Thread Dispatcher | The percentage of time in which thread header is ready on slice0 subslice2 thread dispatcher port 0 |
| ThreadHeader01ReadyPort1 | GPU/Thread Dispatcher | The percentage of time in which thread header is ready on slice0 subslice1 thread dispatcher port 1 |
| Fpu1ActiveAdjusted | EU Array/Pipes | The percentage of time in which EU FPU1 pipeline was actively processing including Extended Math processing |
| RenderBusy | GPU | The percentage of time when render command streamer was busy. |
| Vdbox0Busy | GPU | The percentage of time when Vdbox0 command streamer was busy. |
| VeboxBusy | GPU | The percentage of time when vebox command streamer was busy. |
| BlitterBusy | GPU | The percentage of time when blitter command streamer was busy. |
| AnyRingBusy | GPU | The percentage of time when any command streamer was busy. |
| StcPMAStall | GPU/Stencil Cache | Percentage of time when stencil cache line and an overlapping pixel are causing stalls |
| CsFpu0Active | EU Array | The percentage of time in which EU FPU0 pipeline was actively processing a compute shader instruction. |
| CsFpu1Active | EU Array | The percentage of time in which EU FPU1 pipeline was actively processing a compute shader instruction. |


</details>
