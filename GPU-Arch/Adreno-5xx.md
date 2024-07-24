
### Adreno 530
https://chipsandcheese.com/2024/01/20/inside-qualcomms-adreno-530-a-small-mobile-igpu/
* has 2 compute queues
* 1SP: 32x Fp32, 4x SFU; it means sqrt/sin/cos executes in 1/8 rate; int executed in 1/4 rate.


* Has low resolution Z pass:
 "During the binning pass, a low resolution Z-buffer is constructed, and can reject LRZ-tile wide contributions to boost binning performance. This LRZ is then used during the rendering pass to reject pixels efficiently before testing against the full resolution Z-buffer."
* Has forward pass for fullscreen quad/triangle.
