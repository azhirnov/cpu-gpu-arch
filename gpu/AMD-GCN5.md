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
6. [Vulkan features for Radeon VII](https://vulkan.gpuinfo.org/listreports.php?devicename=AMD%20Radeon%20VII)

## Notes


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

