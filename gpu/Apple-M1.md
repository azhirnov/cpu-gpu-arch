
## Examples

* A14
* M1


## References

1. [Discover Metal enhancements for A14 Bionic](https://developer.apple.com/videos/play/tech-talks/10858/)
2. [Mesa driver details](https://docs.mesa3d.org/drivers/asahi.html)
3. Dissecting the Apple M1 GPU: [1](https://rosenzweig.io/blog/asahi-gpu-part-1.html), [2](https://rosenzweig.io/blog/asahi-gpu-part-2.html), [3](https://rosenzweig.io/blog/asahi-gpu-part-3.html)

## Notes

* fp32 has same rate as fp16
* that there is a penalty (of exactly one cycle) for switching between FP32 and FP16 operation. [ref](https://www.realworldtech.com/forum/?threadid=197759&curpostid=197855)
* FP32 ALU rate is half of FP16 rate on A14 (and earlier chips). That has not changed on A14. F32 ALU rate relative to F16 increased on M1.


## Features

* Ray tracing (software).

## Specs

