**Imagination Technologies PowerVR Performance Counters**

## References

* [Native SDK](https://github.com/powervr-graphics/Native_SDK) - to get access to the performance counters.
* [PVRTune Counter List and Description (2018)](https://cdn.imgtec.com/sdk-documentation/PVRTune.Counter%20List%20and%20Description.pdf), [[backup](../pdf/PVRTune_Counter_List_and_Description.pdf)].
* [PVRTune and PVRScope Documentation](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/configComplete/index.html)

## Notes

**2D** - 2D Core (TLA). The purpose of the 2D core is to perform efficient blitting operations. For example, OS composition may utilize the 2D core so that the rest of the GPU pipeline can be dedicated to application rendering. Used for: buffer copy, image copy, image blit.<br/>
**3D** - TBDR pass ?<br/>
**FBA** - Frame Buffer Accumulate unit.<br/>
**HSR** - Hidden Surface Removal.<br/>
**ISP** - Image Synthesis Processor. ISP fetches the primitive data and performs Hidden Surface Removal (**HSR**), along with depth and stencil tests. The ISP only fetches screen-space position data for the geometry within the tile. (Rasterizer?)<br/>
**IMR** - Immediate Mode Renderer.<br/>
**MCU** - Multi-level Memory Cache Unit.<br/>
**PB** - Parameter Buffer. Tile list and the transformed vertex data are both stored in an intermediate store PB.<br/>
**RTU** - Ray Tracing unit. Accelerate ray-triangle, ray-box intersections.<br/>
**Renderer task** - ?<br/>
**SPM** - If the GPU overflows the parameter buffer during vertex processing it will enter smart parameter mode (SPM) and attempt to grow the parameter buffer.<br/>
**SHF** - (scene hierarchy fetch) ?<br/>
**SHG** - Scene Hierarchy Generator. Takes the output of the **SHF** and is responsible for generating a scene hierarchy acceleration structure for the provided components which can later be used by the RTU.<br/>
**TDM** - texture data master? Time-division multiplexing (high-speed TDM I/O) - mem bus? T* Display Manager ? (active on texture blit)<br/>
**TA** - Tile Accelerator, determines which tiles contain each transformed primitive.<br/>
**TLA** - ?<br/>
**TSP** - Texture and Shading Processor. Applies colouring operations, like fragment shaders, to the visible pixels.<br/>


## BXM-8-256

<details>

| name | units | desc |
|---|---|---|
| Frame time | seconds | Average time it has taken the GPU to process a frame over the selected period. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/frame-time.html)] |
| Frames per second (FPS) | 1/seconds | [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/frames-per-second.html)] |
| Geometry active | % | [Tiler active?](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/tiler-active.html) |
| Geometry time per frame | seconds | [Tiles time per frame?](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/tiler-time-per-frame.html) |
| Geometry time | seconds | |
| GPU clock speed | MHz | On many modern devices, the GPU clock speed will be change dynamically depending on the workload of the GPU and the thermal limits of the chip. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/gpu-clock-speed.html)] |
| GPU memory interface load | % | Total utilisation of the GPU memory bus, for both read and write memory operations over the GPU memory interface within the current period. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/gpu-memory-interface-load.html)] |
| GPU memory read bytes per second | bytes/second | GPU is reading data from the system memory bus in bytes/sec. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/gpu-memory-read-rate.html)] |
| GPU memory total bytes per second | bytes/second | GPU is reading or writing data over the system memory bus in bytes/sec. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/gpu-memory-total-rate.html)] |
| GPU memory write bytes per second | bytes/second | GPU is writing data to the system memory bus in bytes/sec. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/gpu-memory-write-rate.html)] |
| Renderer active | % | Percentage of time that Renderer tasks were active. Renderer time refers to any time that is spent processing pixels and shading them. This includes the ISP (Image Synthesis Processor), Texturing and Shader Processor units. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/renderer-active.html)] |
| Renderer time per frame | seconds | Time spent processing Renderer tasks (in seconds) during the specified period. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/renderer-time-per-frame.html)] |
| Renderer time | seconds | |
| SPM active | % | Percentage of Renderer task which are due to SPM. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/spm-active.html)] |
| TDM active | seconds | |
| TDM time per frame | seconds | |
| TDM time | seconds | |
| **Tiler** | - |
| Triangle ratio | % | Ratio of triangles output from the Tiler over triangles input to the Tiler. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/triangle-ratio.html)] |
| Triangles input per frame |  | Total number of triangles submitted to the Tiler per frame. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/triangles-input-per-frame.html)] |
| Triangles input per second | 1/seconds | Total number of triangles submitted to the Tiler per second. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/triangles-input-per-second.html)] |
| Triangles output per frame | | Total triangles written to the Parameter Buffer per-frame after back-face, off-screen and sub-pixel culling. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/triangles-output-per-frame.html)] |
| Triangles output per second | 1/seconds | Total triangles written to the Parameter Buffer per-second after back-face, off-screen and sub-pixel culling. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/triangles-output-per-second.html)] |
| Vertices per triangle | | Average number of vertices per triangle. This is calculated as the number of input vertices processed divided by the number of input triangles processed. This counter gives an indication of how efficiently transformed vertices are shared between triangles. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/vertices-per-triangle.html)] |
| **Renderer** | - |
| HSR efficiency | % | Effectiveness of the Hidden Surface Removal (HSR) engine, rejecting obscured pixels before they get processed. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/hsr-efficiency.html)] |
| ISP pixel load | % | Percentage of the time that the Image Synthesis Processor (ISP) pixel-processing is busy. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/isp-pixel-load.html)] |
| ISP tiles in flight | % | |
| **Shader** | - |
| Compute kernels per frame |  | Number of compute invocations per frame. [[az](https://github.com/azhirnov)] |
| Compute kernels per second | 1/seconds | Number of compute invocations per second. [[az](https://github.com/azhirnov)] |
| Cycles per compute kernel | Hz? | Average number of cycles that the Shader Processor has spent processing compute kernels (compute shader invocations). [[az](https://github.com/azhirnov)] |
| Cycles per pixel | Hz? | Average number of cycles that the Shader Processor has spent processing fragments. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/cycles-per-pixel.html)] |
| Cycles per vertex | Hz? | Average number of clock cycles that the Shader Engine has spent processing vertices. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/cycles-per-vertex.html)] |
| Pipelines starved | % | Tiles, Rasterizer, ... has not work? |
| Primary ALU Pipeline starved | % | ALU has no work because of memory access? |
| Processing load: compute | % | Average compute workload of the Shader Processor. A high value indicates that a large percentage of the Shader’s workload has been spent executing compute kernels. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/processing-load-compute.html)] |
| Processing load: pixel | % | Average pixel workload of the Shader Processor. A high value indicates that a large percentage of the Shader’s workload has been spent shading fragments. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/processing-load-pixel.html)] |
| Processing load: vertex | % | Average vertex workload of the Shader Processor. A high value indicates that a large percentage of the Shader’s workload has been spent shading vertices. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/processing-load-vertex.html)] |
| Register overload: pixel<br/> Register overload: vertex | % | This counter indicates when the hardware is under register pressure. Register pressure means we cannot queue as many tasks to the hardware due to register requirements being too high. This reduces latency and bandwidth tolerance because we have less tasks available to switch to - hiding these stalls. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/register-overload.html)] |
| Shaded pixels per frame | | Total number of pixels that the Shader unit has processed per frame. This includes the number of pixels visible and blended. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/shaded-pixels-per-frame.html)] |
| Shaded pixels per second | 1/seconds | Total number of pixels that the Shader unit has processed per second. This includes the number of pixels visible and blended. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/shaded-pixels-per-second.html)] |
| Shaded vertices per frame |  | Total number of vertices that the Shader unit has processed per frame. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/shaded-vertices-per-frame.html)] |
| Shaded vertices per second | 1/seconds | Total number of vertices that the Shader unit has processed per second. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/shaded-vertices-per-second.html)] |
| Shader processing load | % | Average workload of the Shader Processor, i.e. when it is processing vertices, pixels or compute. [[ref](https://docs.imgtec.com/tools-manuals/pvrtune-manual/html/pvrtune-manual/topics/counters/shader-processing-load.html)] |
| **Texturing** | - |
| Texture fetches per pixel | | |
| Texture filter cycles per fetch | Hz? | |
| Texture filter input load | % | |
| Texture filter load | % | |
| Texture read cycles per fetch | Hz? | |
| Texture read stall | % | |

</details>
