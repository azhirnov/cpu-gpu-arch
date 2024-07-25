
## Examples

* 504, 505, 506, 510 with LPDDR3
* 508, 509 with LPDDR4
* 512, 530, 540 with LPDDR4X

## References

1. [Mesa driver details](https://docs.mesa3d.org/drivers/freedreno.html)
2. [Inside Qualcomm’s Adreno 530, a Small Mobile iGPU](https://chipsandcheese.com/2024/01/20/inside-qualcomms-adreno-530-a-small-mobile-igpu/)

## Notes

* Has low resolution Z pass: [1]
 "During the binning pass, a low resolution Z-buffer is constructed, and can reject LRZ-tile wide contributions to boost binning performance. This LRZ is then used during the rendering pass to reject pixels efficiently before testing against the full resolution Z-buffer."
* Has forward pass for fullscreen quad/triangle.


**Adreno 530**:
* has 2 compute queues. [2]
* 1SP: 32x Fp32, 4x SFU; it means sqrt/sin/cos executes in 1/8 rate; int executed in 1/4 rate. [2]
