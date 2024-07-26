
## References

1. [Optimizing GPU occupancy and resource usage with large thread groups (2017)](https://gpuopen.com/learn/optimizing-gpu-occupancy-resource-usage-large-thread-groups/)
2. [Life of triangle (2020)](https://gpuopen.com/wp-content/uploads/2021/01/AMD_Graphics_pipeline_GIC2020.pdf), [video](https://youtu.be/Y2KG_4OxDBg), [pdf](../pdf/AMD_Graphics_pipeline_GIC2020.pdf)
3. [Getting the Most Out of Delta Color Compression (2016)](https://gpuopen.com/learn/dcc-overview/)
4. [How mesh shaders are implemented in an AMD driver](https://timur.hu/blog/2022/how-mesh-shaders-are-implemented)
5. [Task shader driver implementation on AMD HW](https://timur.hu/blog/2022/how-task-shaders-are-implemented)
6. [Understanding GPU context rolls (2018)](https://gpuopen.com/learn/understanding-gpu-context-rolls/)
7. [RDNA Performance guide](https://gpuopen.com/performance/)

## Notes

* GCN devices have both vector (SIMD) units, which maintain different state for each thread in a wave, and a scalar unit, which contains a single state common to all threads within a wave. For each SIMD wave, there is one additional scalar thread running, with its own SGPR file. The scalar registers contain a single value for the whole wave. Thus, SGPRs have 64x lower on-chip storage cost. [1]



