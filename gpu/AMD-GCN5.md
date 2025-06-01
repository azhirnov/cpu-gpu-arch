5th generation Graphics Core Next architecture, code name: Vega.<br/>
9 generation of AMD GFX IP.

## Examples

* Radeon RX Vega 56, 64
* Radeon VII

**APU:**
* Ryzen 2xxx - 5xxx
* Ryzen 7x30

**Integrated in desktop CPU:**
* Ryzen 2x00G
* Ryzen 3x00G
* Ryzen 4x00G
* Ryzen 5600G, 5700G

## References

1. [Vega Instruction Set Architecture](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/vega-shader-instruction-set-architecture.pdf), [[backup](../pdf/AMD-vega-shader-instruction-set-architecture.pdf)]
2. Difference between GCN and RDNA: [RDNA Architecture](https://gpuopen.com/wp-content/uploads/2019/08/RDNA_Architecture_public.pdf), [[webarchive](https://web.archive.org/web/20240306074306/https://www.amd.com/system/files/documents/rdna-whitepaper.pdf)], [[backup](../pdf/AMD-rdna-whitepaper.pdf)]
3. [The AMD Radeon VII Review](https://www.anandtech.com/show/13923/the-amd-radeon-vii-review)
4. [Vega Whitepaper](https://en.wikichip.org/w/images/a/a1/vega-whitepaper.pdf), [[backup](../pdf/AMD-vega-whitepaper.pdf)]
5. [Vega 7nm ISA](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/vega-7nm-shader-instruction-set-architecture.pdf), [[backup](../pdf/AMD-vega-shader-instruction-set-architecture.pdf)]
6. [Vulkan features for Radeon VII](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD%20Radeon%20VII), [RX Vega](https://vulkan.gpuinfo.org/listreports.php?devicename=Radeon%20RX%20Vega)
7. [The AMD Vega GPU Architecture Teaser: Higher IPC, Tiling, & More, Coming in H1’2017](https://www.anandtech.com/show/11002/the-amd-vega-gpu-architecture-teaser/3)

## Notes

* Draw-Stream Binning Rasterizer (DSBR): [4]
	- The DSBR works by first dividing the image to be rendered into a grid of bins or tiles in screen space and then collecting a batch of primitives to be rasterized in the scan converter. The bin and batch sizes can be adjusted dynamically to optimize for the content being rendered. 
	The DSBR then traverses the batched primitives one bin at a time, determining which ones are fully or partially covered by the bin. Geometry is processed once, requiring one clock cycle per primitive in the pipeline.
	There are no restrictions on when binning can be enabled, and it is fully compatible with tessellation and geometry shading.
	- This design economizes on-chip memory bandwidth by keeping all the data necessary to rasterize geometry for a bin in fast on-chip memory (i.e., the L2 cache).
	The data in on-chip memory only needs to be accessed once and can then re-used before moving on to the next bin.

* Deferred pixel processing works by using a scoreboard for color samples prior to executing pixel shaders on them.
  If a later sample occludes or overwrites an earlier sample, the earlier sample can be discarded before any pixel shading is done on it.
  The scoreboard has limited depth, so it is most powerful when used in conjunction with binning. [4]

## Specs

* Cache: [2]
	- Instruction Cache: 32KB per 4 CUs, line: 32B, Read-only
	- Scalar Cache: 16KB per 4 CUs, line: 32B, Read-only
	- L1 Cache: 16KB per CU, line: 64B, Read-only
	- L2 Cache: 4MB, line: 64B, Read/Write

* Compressed read from: CU (storage image), Render Backend (texture sampling). [2]
* Compressed write from: Render Backend (render target). [2]
* Decompression: write to storage image, in present queue. [2]

* Texture Unit: [2]
	- Load addressing: 4 to 16 (coalesced) addresses/clk
	- Load data processing: 4 to 16 (coalesced) dwords/clk
	- Store addressing: 4 to 16 (coalesced) addresses/clk
	- Store data processing: 4 to 16 (coalesced) dwords/clk
	- Filtering 64bit texels: 2 components/clk

