
## References

1. [YouTube: AMD Developer Central](https://www.youtube.com/@AMDDevCentral/videos)

**Performance**<br/>
1.1. [Understanding GPU context rolls (2018)](https://gpuopen.com/learn/understanding-gpu-context-rolls/)<br/>
1.2. [Optimizing GPU occupancy and resource usage with large thread groups (2017)](https://gpuopen.com/learn/optimizing-gpu-occupancy-resource-usage-large-thread-groups/)<br/>
1.3. [Getting the Most Out of Delta Color Compression (2016)](https://gpuopen.com/learn/dcc-overview/)<br/>
1.4. [Life of triangle (2020)](https://gpuopen.com/wp-content/uploads/2021/01/AMD_Graphics_pipeline_GIC2020.pdf), [[video](https://youtu.be/Y2KG_4OxDBg)], [[backup](../pdf/AMD-Graphics_pipeline_GIC2020.pdf)]<br/>

**GCN**<br/>
2.1. [ADVANCED SHADER PROGRAMMING ON GCN](https://gpuopen.com/wp-content/uploads/2017/03/GDC2017-Advanced-Shader-Programming-On-GCN.pdf), [[backup](../pdf/AMD-GDC2017-Advanced-Shader-Programming-On-GCN.pdf)]

**RDNA**<br/>
3.1. [RDNA Performance guide](https://gpuopen.com/performance/)<br/>
3.2. [How mesh shaders are implemented in an AMD driver](https://timur.hu/blog/2022/how-mesh-shaders-are-implemented)<br/>
3.3. [Task shader driver implementation on AMD HW](https://timur.hu/blog/2022/how-task-shaders-are-implemented)<br/>
3.4. [What is NGG and shader culling on AMD RDNA GPUs?](https://timur.hu/blog/2022/what-is-ngg)<br/>
3.5. [Occupancy explained through Insert picture the AMD RDNA architecture](https://gpuopen.com/presentations/2024/GPC24_Occupancy_explained.pdf), [[backup](../pdf/AMD-GPC24_Occupancy_explained.pdf)]<br/>
3.6. [The hidden cost of shader instructions](https://interplayoflight.wordpress.com/2025/01/19/the-hidden-cost-of-shader-instructions/)

**Wiki/Specs**<br/>
4.1. [List of AMD graphics processing units](https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units)<br/>
4.2. [Namu wiki, GCN](https://en.namu.wiki/w/Graphics%20Core%20Next)<br/>
4.3. [Namu wiki, RDNA](https://en.namu.wiki/w/RDNA)<br/>

**Pre-GCN**<br/>
5.1. [Depth In-depth (2007)](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=ef95d232b78146cc16e6212cc062fb622136f3f3) - HiZ


## Notes

### Performance

* In AMD GPUs, a high number of concurrent wavefronts running on the same Compute Unit (CU) enables the GPU to hide the time spent in accessing global memory, which is higher than the time needed to perform a compute operation, with operations performed by other wavefronts.

### GCN

* GCN devices have both vector (SIMD) units, which maintain different state for each thread in a wave, and a scalar unit, which contains a single state common to all threads within a wave. For each SIMD wave, there is one additional scalar thread running, with its own SGPR file. The scalar registers contain a single value for the whole wave. Thus, SGPRs have 64x lower on-chip storage cost. [1.2]

* Hardware have 7 context rolls for parallel execution of draw commands with different render states. [1.1]

### RDNA

* This flexibility allows the driver to implement every vertex/geometry processing stage using NGG. Vertex, tess eval and geometry shaders can all be compiled to NGG “primitive shaders”. [3.2]
* Task shaders are executed on an async compute queue. Because task shaders are executed on a different HW queue, there is some overhead. [3.3]

* Waterfall loop happens when used array of buffers/textures and index is not the same for all threads. The compiler will add extra code to batch resource access by index. [3.6]
* RDNA GPUs LDS is divided in 32 banks and the optimal access pattern is for each thread to access a different bank. [3.6]
	- Divergence from this access pattern can introduce conflicts and increased instruction latency, in the following extreme case where consecutive threads attempt to access the same memory bank. This will serialise access and can increase the instruction latency by 32 times.
