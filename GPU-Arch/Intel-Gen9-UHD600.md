
## Examples

* UHD 630

## References

1. [Instruction Set Architecture](https://software.intel.com/sites/default/files/managed/89/92/Intel-Graphics-Architecture-ISA-and-microarchitecture.pdf)

## Notes

* Branches:<br/>
On hardware with structured control flow instructions such as Intel, the loop break instruction does not always jump to the end of the loop. Instead, it removes the active invocations from some sort of internal execution mask to ensure that they get disabled on the next iteration of the loop. Once the final invocation is disabled (the execution mask goes to zero), the hardware jumps to the end of the loop. [ref](https://www.collabora.com/news-and-blog/blog/2024/04/25/re-converging-control-flow-on-nvidia-gpus/)
