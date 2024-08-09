5th generation Graphics Core Next architecture, code name: Vega.<br/>
9 generation of AMD GFX IP.

## Examples

* Radeon RX Vega 56, 64
* Radeon VII

## References

1. [Vega Instruction Set Architecture](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/vega-shader-instruction-set-architecture.pdf), [[backup](../pdf/vega-shader-instruction-set-architecture.pdf)]
2. [RDNA Architecture](https://gpuopen.com/wp-content/uploads/2019/08/RDNA_Architecture_public.pdf) - difference between GCN and RDNA
3. [The AMD Radeon VII Review](https://www.anandtech.com/show/13923/the-amd-radeon-vii-review)
4. [Vega Whitepaper](https://en.wikichip.org/w/images/a/a1/vega-whitepaper.pdf)
5. [Vega 7nm ISA](https://www.amd.com/content/dam/amd/en/documents/radeon-tech-docs/instruction-set-architectures/vega-7nm-shader-instruction-set-architecture.pdf)

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

