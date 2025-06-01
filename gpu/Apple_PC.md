**Apple GPU Performance Counters**<br/>
Only for ARM-based Apple GPU.


## References


## Notes

### Timings

In Metal API each pass is mapped to the specific hardware queue: vertex, fragment, compute.
Time measurements supported only for whole pass, render pass contains 2 passes: vertex shader with tile binning which executed in vertex queue and tile rasterization pass with fragment shader which executed in fragment queue.
Metal API contains implicit render graph which can reorder passes and overlap they execution, so time measurement for multiple passes can be implemented as sum of intervals or as min/max time of all passes, depends on what information you need.
