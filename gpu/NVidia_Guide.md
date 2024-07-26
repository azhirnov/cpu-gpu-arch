
## References

1. [Triangle rasterization](https://developer.nvidia.com/content/life-triangle-nvidias-logical-pipeline)
2. [GPU architecture](https://simonschreibt.de/gat/renderhell-book2/)
3. [CUDA optimization](https://docs.nvidia.com/cuda/cuda-c-best-practices-guide/index.html)

**Shader Execution Reordering**
1.1. [Shader Execution Reordering: Nvidia Tackles Divergence](https://chipsandcheese.com/2023/05/16/shader-execution-reordering-nvidia-tackles-divergence/)
1.2. [Improve Shader Performance and In-Game Frame Rates with Shader Execution Reordering](https://developer.nvidia.com/blog/improve-shader-performance-and-in-game-frame-rates-with-shader-execution-reordering/)
1.3. [Whitepaper](https://developer.nvidia.com/sites/default/files/akamai/gameworks/ser-whitepaper.pdf)

**Subchannel switch**
2.1. [Advanced API Performance: Async Compute and Overlap](https://developer.nvidia.com/blog/advanced-api-performance-async-compute-and-overlap/)
2.2. [New Releases of NVIDIA Nsight Systems and Nsight Graphics Debut at SIGGRAPH 2022](https://developer.nvidia.com/blog/new-releases-of-nvidia-nsight-systems-and-nsight-graphics-debut-at-siggraph-2022/)

**Best Practices**
3.1. [Tips and Tricks: Vulkan Dos and Don’ts (2019)](https://developer.nvidia.com/blog/vulkan-dos-donts/)
3.2. [Tips and Tricks: Ray Tracing Best Practices (2019)](https://developer.nvidia.com/blog/rtx-best-practices/)
3.3. [Best Practices: Using NVIDIA RTX Ray Tracing (2020)](https://developer.nvidia.com/blog/best-practices-using-nvidia-rtx-ray-tracing/)
3.4. [Tips: Acceleration Structure Compaction (2021)](https://developer.nvidia.com/blog/tips-acceleration-structure-compaction/)



## Notes

* Only use signed integers (if possible), this can be faster. The compiler can optimize more aggressively with signed arithmetic than it can with unsigned arithmetic. [3]

* Constant/vertex/index buffers are faster with direct binds (A4Engine)

* In some cases compiler uses FP16 units to implement MOV (e.g. moving a number to a register by multiplying with zero and adding the value/constant it wants to move there). [nv forum]
* A warp scheduler in a modern GPU can schedule 2 instructions per cycle(using different pipelines). [3?]

* Nvidia has been using separate FP32 and FP64 units in their Streaming Multiprocessors (Pascal, Turing, Ampere) [?]

