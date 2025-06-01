
## References

1. [Neon Programmer Guide for Armv8-A Coding for Neon](https://developer.arm.com/documentation/102159/0400)
2. [Arm SoC features](https://gpages.juszkiewicz.com.pl/arm-socs-table/arm-socs.html), [source](https://github.com/hrw/arm-socs-table/tree/main/cpuinfo-data)
3. [Memory Management in AArch64 (2021)](https://developer.arm.com/documentation/101811/latest/), [[backup](../pdf/ARM-Learn_the_Architecture_Memory_Management_101811_0102_00_en.pdf)]
4. [SVE Optimization Guide](https://developer.arm.com/documentation/102699/latest/)


## Notes

* Memory Management: [3]
	- The Memory Management Unit (MMU) is responsible for the translation of virtual addresses used by software to physical addresses used in the memory system.
	- A virtual address must be translated to a physical address before a memory access can take place.
	  This need for translation also applies to cached data, because on Armv6 and later processors, the data caches store data using the physical address.  Therefore, the address must be translated before a cache lookup can complete.
	- Large blocks require fewer levels of reads to translate than small blocks. Plus, large blocks are more efficient to cache in the TLBs.
	- Small blocks give software fine-grain control over memory allocation. However, small blocks are less efficient to cache in the TLBs. Caching is less efficient because small blocks require multiple reads through the levels to translate.

	| Level of table | 4kb granule | 16kb granule | 64kb granule |
	|---|---|---|---|
	| 0 | 512GB | 128TB |   -   |
	| 1 | 1GB   | 64GB  | 4TB   |
	| 2 | 2MB   | 32MB  | 512MB |
	| 3 | 4KB   | 16KB  | 64kb  |
