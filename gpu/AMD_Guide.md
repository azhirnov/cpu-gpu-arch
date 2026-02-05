
## References

1. [YouTube: AMD Developer Central](https://www.youtube.com/@AMDDevCentral/videos)

**Performance**<br/>
1.3. [Getting the Most Out of Delta Color Compression (2016)](https://gpuopen.com/learn/dcc-overview/)<br/>
1.5. [OpenCL Optimization Guide (2015)](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/programmer-references/AMD_OpenCL_Programming_Optimization_Guide2.pdf)<br/>

**GCN**<br/>
2.1. [ADVANCED SHADER PROGRAMMING ON GCN (2017)](https://gpuopen.com/wp-content/uploads/2017/03/GDC2017-Advanced-Shader-Programming-On-GCN.pdf), [[backup](../pdf/AMD-GDC2017-Advanced-Shader-Programming-On-GCN.pdf)]
2.2. [Unlock the Rasterizer with Out-of-Order Rasterization (2016)](https://gpuopen.com/learn/unlock-the-rasterizer-with-out-of-order-rasterization/)<br/>
2.3. [Understanding GPU context rolls (2018)](https://gpuopen.com/learn/understanding-gpu-context-rolls/)<br/>
2.4. [Optimizing GPU occupancy and resource usage with large thread groups (2017)](https://gpuopen.com/learn/optimizing-gpu-occupancy-resource-usage-large-thread-groups/)<br/>

**RDNA**<br/>
3.1. [RDNA Performance guide](https://gpuopen.com/performance/)<br/>
3.2. [How mesh shaders are implemented in an AMD driver](https://timur.hu/blog/2022/how-mesh-shaders-are-implemented)<br/>
3.3. [Task shader driver implementation on AMD HW](https://timur.hu/blog/2022/how-task-shaders-are-implemented)<br/>
3.4. [What is NGG and shader culling on AMD RDNA GPUs?](https://timur.hu/blog/2022/what-is-ngg)<br/>
3.5. [Occupancy explained through Insert picture the AMD RDNA architecture](https://gpuopen.com/presentations/2024/GPC24_Occupancy_explained.pdf), [[backup](../pdf/AMD-GPC24_Occupancy_explained.pdf)]<br/>
3.6. [The hidden cost of shader instructions](https://interplayoflight.wordpress.com/2025/01/19/the-hidden-cost-of-shader-instructions/)<br/>
3.7. [Fast GPU Matrix multiplication](https://seb-v.github.io/optimization/update/2025/01/20/Fast-GPU-Matrix-multiplication.html)<br/>
3.8. [Compute shaders (RDNA2)(2021)](https://gpuopen.com/presentations/2021/ComputeShaders-final.pdf)<br/>
3.9. [Mesh shaders Optimization and best practices](https://gpuopen.com/learn/mesh_shaders/mesh_shaders-optimization_and_best_practices/)<br/>
3.10. [GDC 2024 - Mesh Shaders in AMD RDNA™ 3 Architecture](https://youtu.be/MQv76-q2cm8)<br/>
3.11. [RDNA Performance guide](https://gpuopen.com/learn/rdna-performance-guide/)<br/>
3.12. [Life of triangle (2020)](https://gpuopen.com/wp-content/uploads/2021/01/AMD_Graphics_pipeline_GIC2020.pdf), [[video](https://youtu.be/Y2KG_4OxDBg)], [[backup](../pdf/AMD-Graphics_pipeline_GIC2020.pdf)]<br/>

**Wiki/Specs**<br/>
4.1. [List of AMD graphics processing units](https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units)<br/>
4.2. [Namu wiki, GCN](https://en.namu.wiki/w/Graphics%20Core%20Next)<br/>
4.3. [Namu wiki, RDNA](https://en.namu.wiki/w/RDNA)<br/>

**Pre-GCN**<br/>
5.1. [Depth In-depth (2007)](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=ef95d232b78146cc16e6212cc062fb622136f3f3), [[webarchive](https://web.archive.org/web/20230107202352/http://developer.amd.com/wordpress/media/2012/10/Depth_in-depth.pdf)] - HiZ<br/>

**Driver details**<br/>
6.1. [Mesa: Primitive Ordered Pixel Shading](https://docs.mesa3d.org/drivers/amd/hw/pops.html)<br/>


## Notes

### Performance

* Wavefront:
	- In AMD GPUs, a high number of concurrent wavefronts running on the same Compute Unit (CU) enables the GPU to hide the time spent in accessing global memory, which is higher than the time needed to perform a compute operation, with operations performed by other wavefronts.
	- Wavefront - A collection of 32 or 64 work-items that execute in parallel on a single GCN/RDNA processor.
	- A wavefront executes a number of work-items in lock step relative to each other.
	- Each GPU wavefront has its own register state, which enables the fast singlecycle switching between threads. [1.5]
	- On a GPU, hardware schedules groups of work-items, called wavefronts, onto compute units; thus, work-items within a wavefront execute in lock-step; the same instruction is executed on different data. [1.5]

* Wavefront-based scheduling:
	- It is different from NV's fixed warp-to-SM assignment.
	- A single compute shader dispatch can have its wavefronts spread across all CUs, and this mapping can change during execution.
	- Dynamic Wavefront Dispatch: hw scheduler can dispatch wavefronts to any available CU.
	- Work Stealing: Idle CUs can "steal" work from busy CUs' queues.
	- Wavefronts redistributed based on memory controller load.
	- Work moved from hot CUs to cooler ones.
	- Large wavefronts can be split across CUs. Small, related wavefronts can be fused onto same CU for better data sharing.


### Pre-GCN

* HiZ: [5.1]
	- For each tile HiZ stores a low resolution minimum or maximum depth value depending on the depth comparison the application uses.
	- Since it only stores one of the values changing the comparison direction in the middle of a frame makes the existing values in the buffer unusable. Thus HiZ will have to be disabled until the buffer is either cleared or the application changes the comparison direction back to the original.
	- Since the stored HiZ values are low resolution the effectiveness depends on the amount of range covered. Keeping a low far/near plane ratio can help HiZ to throw away more hidden tiles.


### GCN

* GCN devices have both vector (SIMD) units, which maintain different state for each thread in a wave, and a scalar unit, which contains a single state common to all threads within a wave. For each SIMD wave, there is one additional scalar thread running, with its own SGPR file. The scalar registers contain a single value for the whole wave. Thus, SGPRs have 64x lower on-chip storage cost. [2.4]

* Each GCN compute unit (CU) includes four SIMD units that consist of 16 ALUs; each SIMD executes a full wavefront instruction over four clock cycles.

* Hardware have 7 context rolls for parallel execution of draw commands with different render states. [2.3]

* Each GCN rasterizer can read one triangle per clock and produce up to 16 pixels per clock. Because of this, small triangles are extremely inefficient to rasterize. [[page 51](https://gdcvault.com/play/1023109/Optimizing-the-Graphics-Pipeline-With)]


### RDNA

* This flexibility allows the driver to implement every vertex/geometry processing stage using NGG. Vertex, tess eval and geometry shaders can all be compiled to NGG “primitive shaders”. [3.2]
* Task shaders are executed on an async compute queue. Because task shaders are executed on a different HW queue, there is some overhead. [3.3]

* Waterfall loop happens when used array of buffers/textures and index is not the same for all threads. The compiler will add extra code to batch resource access by index. [3.6, 3.8]
* RDNA GPUs LDS is divided in 32 banks and the optimal access pattern is for each thread to access a different bank. [3.6]
	- Divergence from this access pattern can introduce conflicts and increased instruction latency, in the following extreme case where consecutive threads attempt to access the same memory bank. This will serialise access and can increase the instruction latency by 32 times.

* Drivers opted for wave32 mode on RDNA 2, while RDNA 3 used wave64. That’s important because RDNA 3’s dual issue capability works very well with wave64. Because a wave64 instruction addresses pairs of 32-bit registers. [ref](https://chipsandcheese.com/p/starfield-on-the-rx-6900-xt-rx-7600-and-rtx-2060-mobile)

* Texture access: [3.8]
	- Contiguous reads and writes are faster than scattered.
	- Writes to UAV's: preferably contiguous writes of whole 256byte blocks per wave. Can help maximizing bandwidth in compute shaders.
	- Rule of thumb:
		* 8x8 thread group writes 8x8 block of pixels.
		* Write to all channels if possible.
	- A thread group size of 8x8 writing out 16x16 texels: use offset 8 instead of 1

* Scan Converter (SC): [3.12]
	- Determine pixels covered by each triangle.
	- Contains 2 levels: coarse and fine.
	- Scan Conversion only on a coarse level.
	- On a fine level (4x4 pixels) test against the triangle edges.
	- Forwards quads to the Shader Processor Input. (SPI).

* Shader Processor Input (SPI): [3.12]
	- Gets enough quads from the Scan Converter.
	- Chooses Dual Compute Unit, sets it up.

* Dual Compute Units:
	- Work can migrate between paired CUs without performance penalty.
