
## References

1. [Apple Silicon CPU Optimization Guide](https://developer.apple.com/documentation/apple-silicon/cpu-optimization-guide), [[mirror](https://archive.org/details/apple-silicon-cpu-optimization-guide/page/7/mode/2up)]
2. [7-Zip LZMA Benchmark](https://www.7-cpu.com/cpu/Apple_M1.html)

## Notes

* M1 Cache and Memory Access Latencies: [1]
	- L1 Cache: 4cy (1.25ns)
	- L2 Cache: ~15cy (4.7ns)
	- Other Cluster Shared L2 Cache: ~50ns (160cy)
	- Memory Cache: ~35ns (112cy)
	- Main Memory (RAM): ~95ns (304cy)

* To be fully effective, software prefetches must launch memory requests a hundred or more cycles ahead of the natural use in the code. [1]
