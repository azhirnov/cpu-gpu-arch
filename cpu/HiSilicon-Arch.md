

# Taishan

## Examples

* TaishanV110, TaishanV120, TaishanV123

## References

1.1. [Huawei Expands Kunpeng Server CPUs, Plans SMT, SVE For Next Gen](https://fuse.wikichip.org/news/2274/huawei-expands-kunpeng-server-cpus-plans-smt-sve-for-next-gen/)
1.2. [Huawei's Kunpeng 920 and TaiShan v110 CPU Architecture](https://chipsandcheese.com/p/huaweis-kunpeng-920-and-taishan-v110)

## Notes

* TaishanV110:
	- Each core is a 4-way out-of-order superscalar that implements the ARMv8.2-A ISA. [1.1]
	- compared to Arm’s Cortex cores, Taishan core features an improved memory subsystem, a larger number of execution units, and a better branch predictor. [1.1]

* Taishan V121 instructions:
	- SVE: sve, svei8mm, svebf16
	- Other: wfxt, ecv, amu, bti, dgh, bf16, i8mm, frint, flagm2, dcpodp, pacg, paca, sb, ssbs, flagm, ilrcpc, uscat, dit, asimdfhm, sha512, asimddp, sm4, sm3, sha3, dcpop, lrcpc, fcma, jscvt, asimdrdm, cpuid, asimdhp, fphp, atomics, crc32, sha2, sha1, pmull, aes, evtstrm, asimd, fp

* Kirin 9030 Pro instructions:
	- SVE: sve, svei8mm, svebf16, **sve2, sveaes, svepmull, svebitperm, svesha3, svesm4**
	- Other: hbc, rpres, afp, wfxt, ecv, bti, dgh, bf16, i8mm, frint, flagm2, dcpodp, pacg, paca, sb, ssbs, flagm, ilrcpc, uscat, dit, asimdfhm, sha512, asimddp, sm4, sm3, sha3, dcpop, lrcpc, fcma, jscvt, asimdrdm, cpuid, asimdhp, fphp, atomics, crc32, sha2, sha1, pmull, aes, evtstrm, asimd, fp

## Specs

* Kirin 8020:
	- 1x Taishan V121 2.29 GHz
	- 3x Taishan V121 2.05 GHz
	- 4× Taishan Little 1.3 GHz

* Kirin 9010s:
	- 1x TaiShan V121 2.5 GHz
	- 3x TaiShan V120 2.05 GHz
	- 4x Cortex-A510 1.5 GHz

* Kirin 9030 Pro:
	- 1x 2.75 GHz
	- 4x 2.27 GHz
	- 4x 1.7 2GHz

* Kirin T92:
	- 4x 1.53 GHz
	- 6x 2.15 GHz
	- 2x 2.49 GHz
	- sve, i8mm
	- Maleoon 920 ?

* Kirin T82C:
	- 2x 2.3 GHz
	- 4x 2 GHz
	- 3x 1.6 GHz
	- Maleoon 920А
