
# X86, X64

## References

1.1. [What Every Programmer Should Know About Memory (2007)](https://www.akkadia.org/drepper/cpumemory.pdf), [[backup](../pdf/cpumemory.pdf)]<br/>
  [How much of 'What Every Programmer Should Know About Memory' is still valid?](https://stackoverflow.com/a/47714514)<br/>
1.2. [Fast and slow if-statements: branch prediction in modern processors (2010)](https://igoro.com/archive/fast-and-slow-if-statements-branch-prediction-in-modern-processors/)<br/>
1.3. [Optimizing software in C++ (2004-2024)](https://www.agner.org/optimize/optimizing_cpp.pdf), [[backup](../pdf/CPU-optimizing_cpp.pdf)]<br/>
1.4. [Optimizing subroutines in assembly language (1996-2023)](https://www.agner.org/optimize/optimizing_assembly.pdf), [[backup](../pdf/CPU-optimizing_assembly.pdf)]<br/>
1.5. [Intel Optimization Reference Manual](https://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-optimization-manual.pdf)<br/>
1.6. [Reading privileged memory with a side-channel](https://googleprojectzero.blogspot.com/2018/01/reading-privileged-memory-with-side.html), [Spectre Attacks: Exploiting Speculative Execution](https://spectreattack.com/spectre.pdf)<br/>


## Notes


# ARM

## References

2.1. [Instruction latency & throughput profiler for AArch64](https://github.com/ocxtal/insn_bench_aarch64)<br/>

## Notes


# All Architectures

## References

1. [Benchmarks](https://github.com/azhirnov/as-en/blob/dev/AE/docs/papers/CPU_Benchmarks.md)
2. [Unlocking Modern CPU Power - Next-Gen C++ Optimization Techniques - Fedor G Pikus - C++Now 2024](https://youtu.be/wGSSUSeaLgA)
3. [Performance Optimization in Software Development](https://youtu.be/kv6yqNjCjMM)


## Notes

* There are a couple of factors which influence TLB performance. [1.1]
	- Obviously, the larger a page is, the more instructions or data objects will fit into it. So a larger page size reduces the overall number of address translations which are needed, meaning that fewer entries in the TLB cache are needed.

* Optimizing TLB Usage: [1.1]
	- reduce the number of pages a program has to use.
	- make the TLB lookup cheaper by reducing the number higher level directory tables which must be allocated.  Fewer tables means less memory is used which can result in higher cache hit rates for the directory lookup.

* Optimizing Level 1 Instruction Cache Access. [1.1]
	- Code has the advantage that it is linear between jumps. In these periods the processor can prefetch memory efficiently.
	- Jumps disturb this nice picture because:
		* the jump target might not be statically determined;
		* and even if it is static the memory fetch might take a long time if it misses all caches.
	- To achieve the best L1i use programmers should look out for at least the following aspects of code generation:
		* reduce the code footprint as much as possible. This has to be balanced with optimizations like loop unrolling and inlining.
		* code execution should be linear without bubbles.
		* aligning code when it makes sense.
	- A larger code size means higher pressure on the L1i (and also L2 and higher level) caches. This can lead to less performance. Smaller code can be faster.
	- where alignment of code is most useful:
		* at the beginning of functions;
		* at the beginning of basic blocks which are reached only through jumps;
		* to some extent, at the beginning of loops.

* `[[likely]]` attributes in C++: [1]
	- compiler place hot/likely path as linear code.
	- cold/unlikely path is placed under the hot path.
	- compiler may ignore `[[unlikely]]` if code in cold path is too small, but it cause performance penalty on high-loaded code.

* Programs can use the _mm_prefetch intrinsic on any pointer in the program. [1.1]
	- Most processors (certainly all x86 and x86-64 processors) ignore errors resulting from invalid pointers which makes the life of the programmer significantly easier.
	-  If the passed pointer references valid memory, the prefetch unit will be instructed to load the data into cache and, if necessary, evict other data.

* Prefetching with a null pointer seems silly, but it's also costly: evidently every such prefetch on x86 machines (and, seemingly, ARM as well) causes a translation lookaside buffer miss and a pipeline stall. Each null prefetch cost about 20 processor cycles. [The problem with prefetch](https://lwn.net/Articles/444336/)

* As long as predictions hold, CPU executes a static instruction sequence: [2]
	- Instructions are read, decoded, scheduled, executed, and retired.
	- Predictions are confirmed long after the conditional jump was executed.
	- Pipelining is near-perfect (conditional instructions still must be executed).

* Anything that cannot be discarded must be undone: [2]
	- Out-of-bounds memory reads / writes.
	- Memory writes.
	- Null dereferencing.

* Branch prediction predicts the branch target and enables the processor to begin executing instructions long before the branch true execution path is known. [1.5, 1.6]

* Implicit Caching. [1.5, 1.6]
	- Implicit caching occurs when a memory element is made potentially cacheable, although the element may never have been accessed in the normal von Neumann sequence.
	- Implicit caching occurs on the P6 and more recent processor families due to aggressive prefetching, branch prediction, and TLB miss handling.
	- If memory size is uncached, the processor can speculatively load data from outside of memory region. This is an out-of-bounds read. That should not matter because the processor will effectively roll back the execution state when the branch has executed; none of the speculatively executed instructions will retire (e.g. cause registers etc. to be affected). [1.6]
	- Meltdown and Spectre immune hardware: ARM A55 and older; Snapdragon 630, 626, 4xx. Branch prediction cannot be trained? Doesn't support speculative execution or pipeline is short?
	- Meltdown immune hardware: ARM A72, A73, A57; all AMDs.
