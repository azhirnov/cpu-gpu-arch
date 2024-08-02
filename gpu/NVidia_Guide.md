
## References

1. [Triangle rasterization](https://developer.nvidia.com/content/life-triangle-nvidias-logical-pipeline)
2. [GPU architecture](https://simonschreibt.de/gat/renderhell-book2/)
3. [CUDA Best Practices Guide](https://docs.nvidia.com/cuda/cuda-c-best-practices-guide/index.html)
4. [CUDA Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html)

**Shader Execution Reordering**<br/>
1.1. [Shader Execution Reordering: Nvidia Tackles Divergence](https://chipsandcheese.com/2023/05/16/shader-execution-reordering-nvidia-tackles-divergence/)<br/>
1.2. [Improve Shader Performance and In-Game Frame Rates with Shader Execution Reordering](https://developer.nvidia.com/blog/improve-shader-performance-and-in-game-frame-rates-with-shader-execution-reordering/)<br/>
1.3. [Whitepaper](https://developer.nvidia.com/sites/default/files/akamai/gameworks/ser-whitepaper.pdf)<br/>

**Subchannel switch**<br/>
2.1. [Advanced API Performance: Async Compute and Overlap](https://developer.nvidia.com/blog/advanced-api-performance-async-compute-and-overlap/)<br/>
2.2. [New Releases of NVIDIA Nsight Systems and Nsight Graphics Debut at SIGGRAPH 2022](https://developer.nvidia.com/blog/new-releases-of-nvidia-nsight-systems-and-nsight-graphics-debut-at-siggraph-2022/)<br/>

**Ray Tracing**<br/>
3.2. [Tips and Tricks: Ray Tracing Best Practices (2019)](https://developer.nvidia.com/blog/rtx-best-practices/)<br/>
3.4. [Tips: Acceleration Structure Compaction (2021)](https://developer.nvidia.com/blog/tips-acceleration-structure-compaction/)<br/>
3.3. [Best Practices: Using NVIDIA RTX Ray Tracing (2020)](https://developer.nvidia.com/blog/best-practices-using-nvidia-rtx-ray-tracing/)<br/>

**Mesh Shader**<br/>
4.1. [Advanced API Performance: Mesh Shaders (2021)](https://developer.nvidia.com/blog/advanced-api-performance-mesh-shaders/)<br/>

**Best Practices**<br/>
5.1. [Tips and Tricks: Vulkan Dos and Don’ts (2019)](https://developer.nvidia.com/blog/vulkan-dos-donts/)<br/>
5.2. [Measuring the GPU Occupancy of Multi-stream Workloads (2024)](https://developer.nvidia.com/blog/measuring-the-gpu-occupancy-of-multi-stream-workloads/)<br/>

**Advanced API Performance**<br/>
6.1. [Memory and Resources (2021)](https://developer.nvidia.com/blog/advanced-api-performance-memory-and-resources/)<br/>
6.2. [Async Copy (2021)](https://developer.nvidia.com/blog/advanced-api-performance-async-copy/)<br/>
6.3. [Barriers (2021)](https://developer.nvidia.com/blog/advanced-api-performance-barriers/)<br/>
6.4. [Command Buffers (2021)](https://developer.nvidia.com/blog/advanced-api-performance-command-buffers/)<br/>
6.5. [Async Compute and Overlap (2021)](https://developer.nvidia.com/blog/advanced-api-performance-async-compute-and-overlap/)<br/>
6.6. [Vulkan Clearing and Presenting (2022)](https://developer.nvidia.com/blog/advanced-api-performance-vulkan-clearing-and-presenting/)<br/>
6.7. [Clears (2022)](https://developer.nvidia.com/blog/advanced-api-performance-clears/)<br/>
6.8. [Variable Rate Shading (2022)](https://developer.nvidia.com/blog/advanced-api-performance-variable-rate-shading/)<br/>
6.9. [CPUs (2023)](https://developer.nvidia.com/blog/advanced-api-performance-cpus/)<br/>
6.10. [Pipeline State Objects (2023)](https://developer.nvidia.com/blog/advanced-api-performance-pipeline-state-objects/)<br/>
6.11. [Shaders (2023)](https://developer.nvidia.com/blog/advanced-api-performance-shaders/)<br/>
6.12. [Synchronization (2023)](https://developer.nvidia.com/blog/advanced-api-performance-synchronization/)<br/>
6.13. [Sampler Feedback (2023)](https://developer.nvidia.com/blog/advanced-api-performance-sampler-feedback/)<br/>
6.14. [Debugging (2023)](https://developer.nvidia.com/blog/advanced-api-performance-debugging/)<br/>
6.15. [Descriptors (2023)](https://developer.nvidia.com/blog/advanced-api-performance-descriptors/)<br/>
6.16. [Intrinsics (2023)](https://developer.nvidia.com/blog/advanced-api-performance-intrinsics/)<br/>
6.17. [Swap Chains (2023)](https://developer.nvidia.com/blog/advanced-api-performance-swap-chains/)<br/>


## Notes

* Only use signed integers (if possible), this can be faster. The compiler can optimize more aggressively with signed arithmetic than it can with unsigned arithmetic. [3]

* Constant/vertex/index buffers are faster with direct binds (A4Engine)

* In some cases compiler uses FP16 units to implement MOV (e.g. moving a number to a register by multiplying with zero and adding the value/constant it wants to move there). [nv forum]
* A warp scheduler in a modern GPU can schedule 2 instructions per cycle(using different pipelines). [3?]

* Nvidia has been using separate FP32 and FP64 units in their Streaming Multiprocessors (Pascal, Turing, Ampere) [?]

