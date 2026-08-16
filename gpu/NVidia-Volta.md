
## Examples

* Volta

## References

1. [Dissecting the NVIDIA Volta GPU Architecture via Microbenchmarking](https://arxiv.org/pdf/1804.06826), [[backup](../pdf/NV-Volta_microbench.pdf)]
2. [Inside Volta](https://developer.nvidia.com/blog/inside-volta/)
3. [VOLTA Architecture and performance optimization](https://web.archive.org/web/20210423140749/https://on-demand.gputechconf.com/gtc/2018/presentation/s81006-volta-architecture-and-performance-optimization.pdf)


## Notes


* Shared Memory Bank Conflicts: [3]
	- A bank conflict occurs when, inside a warp: 2 or more threads access within different 4B words in the same bank. Think: 2 or more threads access different “rows” in the same bank.
	- N-way bank conflict: N threads in a warp conflict:
		* Increases latency
		* Worst case: 32-way conflict → 31 replays
		* Each replay adds a few cycles of latency
	- There is no bank conflict if:
		* Several threads access the same 4-byte word
		* Several threads access different bytes of the same 4-byte word
