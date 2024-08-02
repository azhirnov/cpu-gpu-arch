
## References

1. [Arm GPU Best Practices Developer Guide](https://developer.arm.com/documentation/101897/latest/), [backup](../pdf/arm_gpu_best_practices_developer_guide_101897_0302_04_en.pdf)
2. [Arm GPU Datasheet](https://developer.arm.com/documentation/102849/latest/), [backup](../pdf/Arm_GPU_Data_Sheet.pdf)
3. [AFBC](https://developer.arm.com/Architectures/Arm%20Frame%20Buffer%20Compression)

**Guide**<br/>
1.1. [Accelerating 2D Applications](https://developer.arm.com/documentation/102524/0100/Overview)<br/>
1.2. [Tile-Based Rendering](https://developer.arm.com/documentation/102662/0100/Overview)<br/>
1.3. [Principles of High Performance guide](https://developer.arm.com/documentation/102544/0100/Overview)<br/>
1.4. [Workload Pipelining](https://developer.arm.com/documentation/102521/0100/Overview)<br/>
1.5. [GPU Processing Budget Approach to Game Development](https://community.arm.com/arm-community-blogs/b/graphics-gaming-and-vr-blog/posts/gpu-processing-budget-approach-to-game-development), [webarchive](https://web.archive.org/web/20220810172906/https://community.arm.com/arm-community-blogs/b/graphics-gaming-and-vr-blog/posts/gpu-processing-budget-approach-to-game-development)

**Real-time 3D Art Best Practices**<br/>
2.1. [Geometry Guide](https://developer.arm.com/documentation/102448/0200/Overview)<br/>
2.2. [Lighting Guide](https://developer.arm.com/documentation/102109/0100/Overview)<br/>
2.3. [Materials and Shaders Guide](https://developer.arm.com/documentation/102471/0200/Overview)<br/>
2.4. [Texturing Guide](https://developer.arm.com/documentation/102449/0200/Overview)<br/>

## Notes

* Arm Frame Buffer Compression (AFBC). In such cases it reduces the overall system level bandwidth and power cost of transferring spatially coordinated image data throughout the system by up to 50%. [arm]
* Arm Fixed Rate Compression (AFRC). Is a lossy image compression format. AFRC can be used for compressing external texture inputs and framebuffer outputs from the GPU. Configurable compression ratio provides guaranteed bandwidth reduction for such surfaces and memory footprint saving. [arm]
* Transaction Elimination spots the identical pixel blocks between two consecutive render targets and performs a partial update to the frame buffer with the changed pixel blocks only, which reduces memory bandwidth and thus energy. [arm]
* Smart Composition extends the concept of Transaction Elimination to every stage of UI composition. Identical pixel blocks of input surfaces are not read, not processed for composition and not written to final frame buffer. [arm]
* Foveated Rendering allows VR application to specify the shading rate to be used in each part of the screen. This helps the developer to reduce the workload of VR applications by selectively define the part of the screen that require less work from the GPU due to distortion introduced by the VR headset lenses. (fragment density in Vulkan). [arm]

