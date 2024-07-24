
**SPM** - If the GPU overflows the parameter buffer during vertex processing it will enter smart parameter mode (SPM) and attempt to grow the parameter buffer.
**TDM** - texture data master ? (active on texture blit)
**HSR** - Hidden Surface Removal.
**ISP** - Image Synthesis Processor. ISP fetches the primitive data and performs Hidden Surface Removal (HSR), along with depth and stencil tests. The ISP only fetches screen-space position data for the geometry within the tile.
**RTU** - Ray Tracing unit. Accelerate ray-triangle, ray-box intersections.
**SHF** - (scene hierarchy f...) ?
**SHG** - takes the output of the SHF and is responsible for generating a scene hierarchy acceleration structure for the provided components which can later be used by the RTU.
**TA** - Tile Accelerator, determines which tiles contain each transformed primitive.
**2D** - 2D Core. Used for blit, post processing pass; (TLA) ?
**3D** - TBDR pass ?
**IMR** - Immediate Mode Renderer.
**TSP** - Texture and Shading Processor. Applies colouring operations, like fragment shaders, to the visible pixels.
**PB** - Parameter Buffer. Tile list and the transformed vertex data are both stored in an intermediate store PB.


## BXM-8-256

<details>

```
Frame time
Frames per second (FPS)
Geometry  active
Geometry  time per frame
Geometry  time
GPU clock speed
GPU memory interface load
GPU memory read bytes per second
GPU memory total bytes per second
GPU memory write bytes per second
Renderer active
Renderer time per frame
Renderer time
SPM active
TDM active
TDM time per frame
TDM time
Tiler/Triangle ratio
Tiler/Triangles input per frame
Tiler/Triangles input per second
Tiler/Triangles output per frame
Tiler/Triangles output per second
Tiler/Vertices per triangle
Renderer/HSR efficiency
Renderer/ISP pixel load
Renderer/ISP tiles in flight
Shader/Compute kernels per frame
Shader/Compute kernels per second
Shader/Cycles per compute kernel
Shader/Cycles per pixel
Shader/Cycles per vertex
Shader/Pipelines starved
Shader/Primary ALU Pipeline starved
Shader/Processing load: compute
Shader/Processing load: pixel
Shader/Processing load: vertex
Shader/Register overload: pixel
Shader/Register overload: vertex
Shader/Shaded pixels per frame
Shader/Shaded pixels per second
Shader/Shaded vertices per frame
Shader/Shaded vertices per second
Shader/Shader processing load
Texturing/Texture fetches per pixel
Texturing/Texture filter cycles per fetch
Texturing/Texture filter input load
Texturing/Texture filter load
Texturing/Texture read cycles per fetch
Texturing/Texture read stall
```
</details>
