
On Windows use `wpr -pmcsources` to get list of performance counters.


# AMD Ryzen 9 3900X

<details>

**description from LLM**

| Id  | Name                                                        | Interval | Min   | Max          | Description |
|-----|-------------------------------------------------------------|----------|-------|--------------|---|
| 0   | Timer                                                       | 10000    | 1221  | 1000000      | Periodic time-based sampling tick used to drive profile interrupts; not a hardware event. |
| 2   | TotalIssues                                                 | 65536    | 4096  | 2147483647   | Total micro-ops dispatched/issued from the scheduler to execution units (all pipes). Indicates backend utilization. Includes speculative issues. |
| 6   | BranchInstructions                                          | 65536    | 4096  | 2147483647   | Retired branch instructions of all types: conditional/unconditional jumps, calls, returns, and far control transfers. |
| 8   | DcacheMisses                                                | 65536    | 4096  | 2147483647   | L1 data cache demand misses (loads/stores that miss in L1 D$). May include misses satisfied by L2/L3 or memory. |
| 9   | IcacheMisses                                                | 65536    | 4096  | 2147483647   | L1 instruction cache misses on fetch. Misses that require an L2/L3 or memory refill. |
| 11  | BranchMispredictions                                        | 65536    | 4096  | 2147483647   | Retired branch instructions that were resolved as mispredicted (direction or target). Includes returns mispredicted by RAS. |
| 13  | FpInstructions                                              | 65536    | 4096  | 2147483647   | Floating-point/SIMD instructions executed (x87, MMX, SSE family). Typically counts at dispatch/execute, not just retired. |
| 20  | IcacheIssues                                                | 65536    | 4096  | 2147483647   | Instruction fetch requests issued by the frontend to L1 I$. Reflects fetch pressure; includes demand fetches. |
| 21  | DcacheAccesses                                              | 65536    | 4096  | 2147483647   | All L1 data cache accesses (hits + misses) due to loads, stores, and RFOs. |
| 25  | FPDispatchedFPUOps                                          | 65536    | 4096  | 2147483647   | Total floating-point/SIMD operations dispatched to the FPU pipelines (speculative + non-speculative). |
| 26  | FPDispatchedFPUOpsAddExcludeJunk                            | 65536    | 4096  | 2147483647   | Dispatched FP/SIMD add/subtract class operations that were not later squashed (excludes canceled “junk” uops). |
| 27  | FPDispatchedFPUOpsMulExcludeJunk                            | 65536    | 4096  | 2147483647   | Dispatched FP/SIMD multiply class operations that were not later squashed (excludes canceled uops). |
| 28  | FPDispatchedFPUOpsStoreExcludeJunk                          | 65536    | 4096  | 2147483647   | Dispatched FP/SIMD moves/stores/shuffles that were not later squashed (excludes canceled uops). |
| 29  | FPDispatchedFPUOpsAddJunk                                   | 65536    | 4096  | 2147483647   | FP/SIMD add/subtract class operations that were dispatched but subsequently canceled/squashed (“junk”). |
| 30  | FPDispatchedFPUOpsMulJunk                                   | 65536    | 4096  | 2147483647   | FP/SIMD multiply class operations that were dispatched but subsequently canceled/squashed. |
| 31  | FPDispatchedFPUOpsStoreJunk                                 | 65536    | 4096  | 2147483647   | FP/SIMD move/store/shuffle operations dispatched but subsequently canceled/squashed. |
| 32  | FPCyclesNoFPUOpsRetired                                     | 65536    | 4096  | 2147483647   | Core cycles in which no FPU operation retired. Indicates FPU pipeline underutilization/bubbles. |
| 33  | FPDispathedFPUOpsWithFastFlag                               | 65536    | 4096  | 2147483647   | Dispatched FP/SIMD operations that used the “fast flag” optimization path for condition codes/flags generation. |
| 34  | LSSegmentRegisterLoad                                       | 65536    | 4096  | 2147483647   | Total architectural segment register loads (any segment). Usually triggered by MOV/POP to segment, far branches, task changes. |
| 35  | LSSegmentRegisterLoadES                                     | 65536    | 4096  | 2147483647   | ES segment register load (architectural write). |
| 36  | LSSegmentRegisterLoadCS                                     | 65536    | 4096  | 2147483647   | CS segment register load (e.g., far JMP/CALL/IRET). |
| 37  | LSSegmentRegisterLoadSS                                     | 65536    | 4096  | 2147483647   | SS segment register load. |
| 38  | LSSegmentRegisterLoadDS                                     | 65536    | 4096  | 2147483647   | DS segment register load. |
| 39  | LSSegmentRegisterLoadFS                                     | 65536    | 4096  | 2147483647   | FS segment register load (including WRMSR to FS.base via system instructions). |
| 40  | LSSegmentRegisterLoadGS                                     | 65536    | 4096  | 2147483647   | GS segment register load (including WRMSR to GS.base or SWAPGS effects). |
| 41  | LSSegmentRegisterLoadHS                                     | 65536    | 4096  | 2147483647   | Hidden segment descriptor load/update (segment descriptor cache reload). |
| 42  | LSResyncBySelfModifyingCode                                 | 65536    | 4096  | 2147483647   | Pipeline flush/resynchronizations due to self-modifying code or I$ line invalidated by a recent store. |
| 43  | LSResyncBySnoop                                             | 65536    | 4096  | 2147483647   | Pipeline resyncs caused by external snoop/coherence activity invalidating lines used by in-flight instructions. |
| 44  | LSBuffer2Full                                               | 65536    | 4096  | 2147483647   | Stalls because the second Load/Store buffer/queue is full (structure backpressure). |
| 45  | LSLockedOperation                                           | 65536    | 4096  | 2147483647   | LOCK-prefixed operations executed (atomic read-modify-write). Typically serialize the pipeline and hold cache line in exclusive state. |
| 46  | LSLateCancelOperation                                       | 65536    | 4096  | 2147483647   | Loads/stores that were canceled late (after issuance) due to faults, redirects, or address conflicts. |
| 47  | LSRetiredCFLUSH                                             | 65536    | 4096  | 2147483647   | Retired CLFLUSH/CLFLUSHOPT instructions (explicit cache line flush). |
| 48  | LSRetiredCPUID                                              | 65536    | 4096  | 2147483647   | Retired CPUID instructions. These serialize the core. |
| 49  | DCAccess                                                    | 65536    | 4096  | 2147483647   | Total L1 D$ accesses from demand loads/stores and write-allocations (hits + misses). |
| 50  | DCMiss                                                      | 65536    | 4096  | 2147483647   | L1 D$ misses on demand accesses (excludes certain hardware prefetch hits). |
| 51  | DCRefillFromL2                                              | 65536    | 4096  | 2147483647   | L1 D$ line refills sourced from L2 (any coherence state). |
| 52  | DCRefillFromL2Invalid                                       | 65536    | 4096  | 2147483647   | L1 D$ refills from L2 where the line was in Invalid state (I) and fetched anew. |
| 53  | DCRefillFromL2Shared                                        | 65536    | 4096  | 2147483647   | L1 D$ refills from L2 lines in Shared (S) state. |
| 54  | DCRefillFromL2Exclusive                                     | 65536    | 4096  | 2147483647   | L1 D$ refills from L2 lines in Exclusive (E) state. |
| 55  | DCRefillFromL2Owner                                         | 65536    | 4096  | 2147483647   | L1 D$ refills from L2 lines in Owner (O) state. |
| 56  | DCRefillFromL2Modified                                      | 65536    | 4096  | 2147483647   | L1 D$ refills from L2 lines in Modified (M) state. |
| 57  | DCRefillFromSystem                                          | 65536    | 4096  | 2147483647   | L1 D$ refills that bypassed L2 hit and were satisfied by “system” (L3/other core/DRAM/fabric). |
| 58  | DCRefillFromSystemInvalid                                   | 65536    | 4096  | 2147483647   | L1 D$ refills from system where coherence state was Invalid (new fetch). |
| 59  | DCRefillFromSystemShared                                    | 65536    | 4096  | 2147483647   | L1 D$ refills from system with line in Shared (S) state. |
| 60  | DCRefillFromSystemExclusive                                 | 65536    | 4096  | 2147483647   | L1 D$ refills from system with line in Exclusive (E) state. |
| 61  | DCRefillFromSystemOwner                                     | 65536    | 4096  | 2147483647   | L1 D$ refills from system with line in Owner (O) state. |
| 62  | DCRefillFromSystemModified                                  | 65536    | 4096  | 2147483647   | L1 D$ refills from system with line in Modified (M) state. |
| 63  | DCRefillCopyBack                                            | 65536    | 4096  | 2147483647   | Copy-back refills into L1 D$: line obtained while another line is written back (cache replacement path). |
| 64  | DCRefillCopyBackInvalid                                     | 65536    | 4096  | 2147483647   | Copy-back refill where incoming line is Invalid state. |
| 65  | DCRefillCopyBackShared                                      | 65536    | 4096  | 2147483647   | Copy-back refill where incoming line is Shared. |
| 66  | DCRefillCopyBackExclusive                                   | 65536    | 4096  | 2147483647   | Copy-back refill where incoming line is Exclusive. |
| 67  | DCRefillCopyBackOwner                                       | 65536    | 4096  | 2147483647   | Copy-back refill where incoming line is Owner. |
| 68  | DCRefillCopyBackModified                                    | 65536    | 4096  | 2147483647   | Copy-back refill where incoming line is Modified. |
| 69  | DCL1DTLBMissL2DTLBHit                                       | 65536    | 4096  | 2147483647   | Load/store address translation missed in L1 DTLB but hit in L2 TLB. |
| 70  | DCL1DTLBMissL2DTLBMiss                                      | 65536    | 4096  | 2147483647   | L1 and L2 DTLB miss (page walk required). High counts indicate TLB pressure. |
| 71  | DCMisalignedDataReference                                   | 65536    | 4096  | 2147483647   | Misaligned load/store accesses (crossing alignment boundary). Often cause additional micro-ops or penalties. |
| 72  | DCLateCancelOfAnAccess                                      | 65536    | 4096  | 2147483647   | Data cache access canceled late (after tag/data access started) due to redirect or squash. |
| 73  | DCEarlyCancelOfAnAccess                                     | 65536    | 4096  | 2147483647   | Data cache access canceled early (before data return) due to dependency resolution or redirect. |
| 74  | DCOneBitECCError                                            | 65536    | 4096  | 2147483647   | Correctable single-bit ECC/parity error detected on L1 D$ access (corrected on the fly). |
| 75  | DCOneBitECCErrorScrubberError                               | 65536    | 4096  | 2147483647   | Correctable ECC error detected by background scrubber activity in the D$ hierarchy. |
| 76  | DCOneBitECCErrorPiggybackScrubberError                      | 65536    | 4096  | 2147483647   | Correctable ECC error detected by piggyback scrubbing (opportunistic scrub on demand access). |
| 77  | DCDispatchedPrefetchInstructions                            | 65536    | 4096  | 2147483647   | Software prefetch instructions (any type) accepted and dispatched by the LS unit. |
| 78  | DCDispatchedPrefetchInstructionsLoad                        | 65536    | 4096  | 2147483647   | PREFETCHT0/T1/T2 (load prefetch) instructions dispatched. |
| 79  | DCDispatchedPrefetchInstructionsStore                       | 65536    | 4096  | 2147483647   | Store prefetch (write prefetch/RFO-style) instructions dispatched. |
| 80  | DCDispatchedPrefetchInstructionsNTA                         | 65536    | 4096  | 2147483647   | PREFETCHNTA (non-temporal) instructions dispatched. |
| 81  | BUInternalL2Request                                         | 65536    | 4096  | 2147483647   | Backend internal requests sent to L2 (aggregate): ICFill, DCFill, TLB reloads, tag snoops, etc. |
| 82  | BUInternalL2RequestICFill                                   | 65536    | 4096  | 2147483647   | Internal L2 requests for instruction cache refills. |
| 83  | BUInternalL2RequestDCFill                                   | 65536    | 4096  | 2147483647   | Internal L2 requests for data cache refills. |
| 84  | BUInternalL2RequestTLBReload                                | 65536    | 4096  | 2147483647   | Internal L2 requests associated with TLB page table walks/reloads. |
| 85  | BUInternalL2RequestTagSnoopRequest                          | 65536    | 4096  | 2147483647   | L2 tag-only snoop/lookups initiated internally (coherence/tag state checks). |
| 86  | BUInternalL2RequestCancelledRequest                         | 65536    | 4096  | 2147483647   | Internal L2 requests that were canceled before completion (due to redirect, merge, or hit-under-miss conditions). |
| 87  | BUFillRequestMissedInL2                                     | 65536    | 4096  | 2147483647   | Fill requests (I or D) that missed in L2 (had to be satisfied by L3/other core/memory). |
| 88  | BUFillRequestMissedInL2ICFill                               | 65536    | 4096  | 2147483647   | Instruction cache line fills that missed in L2. |
| 89  | BUFillRequestMissedInL2DCFill                               | 65536    | 4096  | 2147483647   | Data cache line fills that missed in L2. |
| 90  | BUFillRequestMissedInL2TLBLoad                              | 65536    | 4096  | 2147483647   | TLB page table walk requests that missed in L2 (had to access memory). |
| 91  | BUFillIntoL2                                                | 65536    | 4096  | 2147483647   | Lines filled into L2 cache from lower levels or peer cores. |
| 92  | BUFillIntoL2DirtyL2Victim                                   | 65536    | 4096  | 2147483647   | L2 fill caused eviction of a dirty victim line (write-back needed). |
| 93  | BUFillIntoL2VictimFromL1                                    | 65536    | 4096  | 2147483647   | Lines evicted from L1 and inserted into L2 as victims. |
| 94  | ICFetch                                                     | 65536    | 4096  | 2147483647   | Instruction fetches issued by the frontend (fetch blocks/lines requested). |
| 95  | ICMiss                                                      | 65536    | 4096  | 2147483647   | L1 I$ misses (demand) requiring a line refill. |
| 96  | ICRefillFromL2                                              | 65536    | 4096  | 2147483647   | L1 I$ line refills satisfied by L2. |
| 97  | ICRefillFromSystem                                          | 65536    | 4096  | 2147483647   | L1 I$ refills satisfied beyond L2 (L3/peer/memory/fabric). |
| 98  | ICL1TLBMissL2TLBHit                                         | 65536    | 4096  | 2147483647   | Instruction fetch translation missed in L1 ITLB but hit in L2 TLB. |
| 99  | ICL1TLBMissL2TLBMiss                                        | 65536    | 4096  | 2147483647   | ITLB miss in both L1 and L2 (page walk performed). |
| 100 | ICResyncBySnoop                                             | 65536    | 4096  | 2147483647   | Frontend resyncs due to snoop/coherence invalidating instruction lines. |
| 101 | ICInstructionFetchStall                                     | 65536    | 4096  | 2147483647   | Core cycles where instruction fetch is stalled (I$ miss, ITLB miss, queue full, or redirection penalties). |
| 102 | ICReturnStackHit                                            | 65536    | 4096  | 2147483647   | Return Address Stack (RAS) predictions that hit (return target predicted correctly). |
| 103 | ICReturnStackOverflow                                       | 65536    | 4096  | 2147483647   | RAS overflows (call depth exceeded stack size), degrading return prediction quality. |
| 104 | FRRetiredx86Instructions                                    | 65536    | 4096  | 2147483647   | Total retired x86 instructions (macro-instructions), excluding microcode assists unless they retire as instructions. |
| 105 | FRRetireduops                                               | 65536    | 4096  | 2147483647   | Retired micro-operations (uops). Ratio to instructions indicates average instruction complexity. |
| 106 | FRRetiredBranches                                           | 65536    | 4096  | 2147483647   | Retired branch macro-instructions (all types). |
| 107 | FRRetiredBranchesMispredicted                               | 65536    | 4096  | 2147483647   | Retired branches that were mispredicted (direction or target). Causes pipeline flushes. |
| 108 | FRRetiredTakenBranches                                      | 65536    | 4096  | 2147483647   | Retired branches that were taken. Useful to compute taken rate. |
| 109 | FRRetiredTakenBranchesMispredicted                          | 65536    | 4096  | 2147483647   | Retired taken branches that were mispredicted (typically target mispredict). |
| 110 | FRRetiredFarControlTransfers                                | 65536    | 4096  | 2147483647   | Retired far jumps/calls/returns/task switches that change CS or privilege level. Heavier cost than near transfers. |
| 111 | FRRetiredResyncsNonControlTransferBranches                  | 65536    | 4096  | 2147483647   | Retired resynchronizations not caused by control-transfer branches (e.g., exceptions, SMC, serializing events). |
| 112 | FRRetiredNearReturns                                        | 65536    | 4096  | 2147483647   | Retired near return instructions (RET). |
| 113 | FRRetiredNearReturnsMispredicted                            | 65536    | 4096  | 2147483647   | Retired near returns that were mispredicted by the RAS. |
| 114 | FRRetiredTakenBranchesMispredictedByAddressMiscompare       | 65536    | 4096  | 2147483647   | Mispredicted taken branches due to wrong target (address miscompare), not direction. |
| 115 | FRRetiredFPUInstructions                                    | 65536    | 4096  | 2147483647   | Retired floating-point/SIMD instructions (aggregate across x87/MMX/SSE classes). |
| 116 | FRRetiredFPUInstructionsx87                                 | 65536    | 4096  | 2147483647   | Retired x87 FP instructions. |
| 117 | FRRetiredFPUInstructionsMMXAnd3DNow                         | 65536    | 4096  | 2147483647   | Retired MMX and 3DNow! instructions. |
| 118 | FRRetiredFPUInstructionsPackedSSEAndSSE2                    | 65536    | 4096  | 2147483647   | Retired packed SSE/SSE2 (vector) instructions. |
| 119 | FRRetiredFPUInstructionsScalarSSEAndSSE2                    | 65536    | 4096  | 2147483647   | Retired scalar SSE/SSE2 instructions. |
| 120 | FRRetiredFastpathDoubleOpInstructions                       | 65536    | 4096  | 2147483647   | Retired “fastpath double-op” sequences decoded in a single cycle (two simple ops fused/handled efficiently). |
| 121 | FRRetiredFastpathDoubleOpInstructionsLowOpInPosition0       | 65536    | 4096  | 2147483647   | Fastpath double-op with the low-complexity op placed in decode slot/position 0. |
| 122 | FRRetiredFastpathDoubleOpInstructionsLowOpInPosition1       | 65536    | 4096  | 2147483647   | Fastpath double-op with the low-complexity op placed in position 1. |
| 123 | FRRetiredFastpathDoubleOpInstructionsLowOpInPosition2       | 65536    | 4096  | 2147483647   | Fastpath double-op with the low-complexity op placed in position 2. |
| 124 | FRInterruptsMaskedCycles                                    | 65536    | 4096  | 2147483647   | Core cycles where interrupts were masked (IF=0 or similar conditions), preventing delivery. |
| 125 | FRInterruptsMaskedWhilePendingCycles                        | 65536    | 4096  | 2147483647   | Cycles where an interrupt was pending but masked (not delivered yet). |
| 126 | FRTakenHardwareInterrupts                                   | 65536    | 4096  | 2147483647   | Hardware interrupts taken (delivered and serviced). |
| 127 | FRNothingToDispatch                                         | 65536    | 4096  | 2147483647   | Cycles with no uops available to dispatch (frontend starvation or dependency chains). |
| 128 | FRDispatchStalls                                            | 65536    | 4096  | 2147483647   | Total cycles the core could not dispatch uops due to any stall reason. |
| 129 | FRDispatchStallsFromBranchAbortToRetire                     | 65536    | 4096  | 2147483647   | Stalls spanning from a branch abort/redirect until the mispredicted instruction retires. |
| 130 | FRDispatchStallsForSerialization                            | 65536    | 4096  | 2147483647   | Dispatch stalls caused by serializing operations (e.g., CPUID, WRMSR) and pipeline serialization points. |
| 131 | FRDispatchStallsForSegmentLoad                              | 65536    | 4096  | 2147483647   | Stalls while loading/validating segment descriptors and updating hidden state. |
| 132 | FRDispatchStallsWhenReorderBufferFull                       | 65536    | 4096  | 2147483647   | Dispatch blocked because the reorder buffer (ROB) is full. |
| 133 | FRDispatchStallsWhenReservationStationsFull                 | 65536    | 4096  | 2147483647   | Dispatch blocked because reservation stations/scheduler queues are full. |
| 134 | FRDispatchStallsWhenFPUFull                                 | 65536    | 4096  | 2147483647   | Dispatch blocked by lack of available FPU execution resources. |
| 135 | FRDispatchStallsWhenLSFull                                  | 65536    | 4096  | 2147483647   | Dispatch blocked by full load/store queues or memory ordering resources. |
| 136 | FRDispatchStallsWhenWaitingForAllQuiet                      | 65536    | 4096  | 2147483647   | Stalls waiting for “all-quiet” memory state (all prior memory ops globally visible/retired). |
| 137 | FRDispatchStallsWhenFarControlOrResyncBranchPending         | 65536    | 4096  | 2147483647   | Stalls due to pending far control transfer or pipeline resynchronization. |
| 138 | FRFPUExceptions                                             | 65536    | 4096  | 2147483647   | Floating-point exceptions/traps (aggregate). |
| 139 | FRFPUExceptionsx87ReclassMicroFaults                        | 65536    | 4096  | 2147483647   | x87 exceptions handled as reclass micro-faults (converted to microarchitectural faults). |
| 140 | FRFPUExceptionsSSERetypeMicroFaults                         | 65536    | 4096  | 2147483647   | SSE exceptions retyped as micro-faults. |
| 141 | FRFPUExceptionsSSEReclassMicroFaults                        | 65536    | 4096  | 2147483647   | SSE exceptions reclassified as micro-faults. |
| 142 | FRFPUExceptionsSSEAndx87MicroTraps                          | 65536    | 4096  | 2147483647   | SSE/x87 micro-traps taken (precise exceptions handled via microcode). |
| 143 | FRNumberOfBreakPointsForDR0                                 | 65536    | 4096  | 2147483647   | Hardware debug breakpoint matches using DR0 (any type configured). |
| 144 | FRNumberOfBreakPointsForDR1                                 | 65536    | 4096  | 2147483647   | Hardware debug breakpoint matches using DR1. |
| 145 | FRNumberOfBreakPointsForDR2                                 | 65536    | 4096  | 2147483647   | Hardware debug breakpoint matches using DR2. |
| 146 | FRNumberOfBreakPointsForDR3                                 | 65536    | 4096  | 2147483647   | Hardware debug breakpoint matches using DR3. |
| 147 | NBMemoryControllerPageAccessEvent                           | 65536    | 4096  | 2147483647   | DRAM page access activity (aggregate of hits, misses, conflicts) observed by the memory controller. |
| 148 | NBMemoryControllerPageAccessEventPageHit                    | 65536    | 4096  | 2147483647   | DRAM accesses that hit an already-open row (page hit). Lowest latency. |
| 149 | NBMemoryControllerPageAccessEventPageMiss                   | 65536    | 4096  | 2147483647   | DRAM accesses requiring activation of a different row (page miss). |
| 150 | NBMemoryControllerPageAccessEventPageConflict               | 65536    | 4096  | 2147483647   | DRAM accesses that conflict with an open row, requiring precharge + activate (worst case). |
| 151 | NBMemoryControllerPageTableOverflow                         | 65536    | 4096  | 2147483647   | Memory controller internal page-tracking table overflow events (excessive open pages/requests). |
| 152 | NBMemoryControllerDRAMCommandSlotsMissed                    | 65536    | 4096  | 2147483647   | Times a ready DRAM command could not be issued because the slot/turn was missed (timing or contention). |
| 153 | NBMemoryControllerTurnAround                                | 65536    | 4096  | 2147483647   | Bus turnaround events on the DRAM interface (direction or rank/bank changes incurring dead cycles). |
| 154 | NBMemoryControllerTurnAroundDIMM                            | 65536    | 4096  | 2147483647   | Turnarounds specifically attributable to DIMM/rank constraints (tRTW/tWTR, rank switching). |
| 155 | NBMemoryControllerTurnAroundReadToWrite                     | 65536    | 4096  | 2147483647   | Read-to-write direction changes on the DRAM bus (incurs tRTW penalty). |
| 156 | NBMemoryControllerTurnAroundWriteToRead                     | 65536    | 4096  | 2147483647   | Write-to-read direction changes on the DRAM bus (incurs tWTR penalty). |
| 157 | NBMemoryControllerBypassCounter                             | 65536    | 4096  | 2147483647   | Requests bypassing normal MC queues/scheduling (aggregate). Indicates QoS/priority effects. |
| 158 | NBMemoryControllerBypassCounterHighPriority                 | 65536    | 4096  | 2147483647   | High-priority requests that bypassed standard queueing (isochronous/isoc or urgent traffic). |
| 159 | NBMemoryControllerBypassCounterLowPriority                  | 65536    | 4096  | 2147483647   | Low-priority requests bypasses (rare; platform/firmware-dependent). |
| 160 | NBMemoryControllerBypassCounterDRAMControllerInterface      | 65536    | 4096  | 2147483647   | Bypass events at the DRAM controller interface (issued directly to PHY scheduling). |
| 161 | NBMemoryControllerBypassCounterDRAMControllerQueue          | 65536    | 4096  | 2147483647   | Bypass events within MC request queues (skipped ahead of older entries). |
| 162 | NBSizedCommands                                             | 65536    | 4096  | 2147483647   | Northbridge command traffic categorized by size/type (aggregate over read/write classes below). |
| 163 | NBSizedCommandsNonPostWrSzByte                              | 65536    | 4096  | 2147483647   | Non-posted byte-sized write commands sent on the fabric/HT (require completion). |
| 164 | NBSizedCommandsNonPostWrSzDword                             | 65536    | 4096  | 2147483647   | Non-posted dword-sized write commands sent (require completion). |
| 165 | NBSizedCommandsWrSzByte                                     | 65536    | 4096  | 2147483647   | Posted byte-sized write commands (do not require immediate completion). |
| 166 | NBSizedCommandsWrSzDword                                    | 65536    | 4096  | 2147483647   | Posted dword-sized write commands. |
| 167 | NBSizedCommandsRdSzByte                                     | 65536    | 4096  | 2147483647   | Byte-sized read commands issued on the fabric/HT. |
| 168 | NBSizedCommandsRdSzDword                                    | 65536    | 4096  | 2147483647   | Dword-sized read commands issued. |
| 169 | NBSizedCommandsRdModWr                                      | 65536    | 4096  | 2147483647   | Read-modify-write commands (atomic sequences) observed by the NB. |
| 170 | NBProbeResult                                               | 65536    | 4096  | 2147483647   | Coherence probe outcomes summary (aggregate). See breakdown below. |
| 171 | NBProbeResultMiss                                           | 65536    | 4096  | 2147483647   | Coherence probe miss (no matching line found in probed caches). |
| 172 | NBProbeResultHit                                            | 65536    | 4096  | 2147483647   | Coherence probe hit on a clean (S/E) line. |
| 173 | NBProbeResultHitDirtyWithoutMemoryCancel                    | 65536    | 4096  | 2147483647   | Probe hit on a dirty (O/M) line; memory request not canceled (data may still come from memory). |
| 174 | NBProbeResultHitDirtyWithMemoryCancel                       | 65536    | 4096  | 2147483647   | Probe hit on a dirty line and the outstanding memory request was canceled (data sourced from peer). |
| 175 | NBHyperTransportBus0Bandwidth                               | 65536    | 4096  | 2147483647   | HT link 0 bandwidth utilization (aggregate of command/data/nop/release packets). |
| 176 | NBHyperTransportBus0BandwidthCommandSent                    | 65536    | 4096  | 2147483647   | HT0 command packets sent. |
| 177 | NBHyperTransportBus0BandwidthDataSent                       | 65536    | 4096  | 2147483647   | HT0 data payload flits sent. |
| 178 | NBHyperTransportBus0BandwidthBufferReleaseSent              | 65536    | 4096  | 2147483647   | HT0 buffer release packets sent (credit returns). |
| 179 | NBHyperTransportBus0BandwidthNopSent                        | 65536    | 4096  | 2147483647   | HT0 NOP/idle packets sent (indicates unused bandwidth). |
| 180 | NBHyperTransportBus1Bandwidth                               | 65536    | 4096  | 2147483647   | HT link 1 bandwidth utilization (aggregate). |
| 181 | NBHyperTransportBus1BandwidthCommandSent                    | 65536    | 4096  | 2147483647   | HT1 command packets sent. |
| 182 | NBHyperTransportBus1BandwidthDataSent                       | 65536    | 4096  | 2147483647   | HT1 data payload flits sent. |
| 183 | NBHyperTransportBus1BandwidthBufferReleaseSent              | 65536    | 4096  | 2147483647   | HT1 buffer release packets sent. |
| 184 | NBHyperTransportBus1BandwidthNopSent                        | 65536    | 4096  | 2147483647   | HT1 NOP/idle packets sent. |
| 185 | NBHyperTransportBus2Bandwidth                               | 65536    | 4096  | 2147483647   | HT link 2 bandwidth utilization (aggregate). |
| 186 | NBHyperTransportBus2BandwidthCommandSent                    | 65536    | 4096  | 2147483647   | HT2 command packets sent. |
| 187 | NBHyperTransportBus2BandwidthDataSent                       | 65536    | 4096  | 2147483647   | HT2 data payload flits sent. |
| 188 | NBHyperTransportBus2BandwidthBufferReleaseSent              | 65536    | 4096  | 2147483647   | HT2 buffer release packets sent. |
| 189 | NBHyperTransportBus2BandwidthNopSent                        | 65536    | 4096  | 2147483647   | HT2 NOP/idle packets sent. |
| 190 | BUCleanToDirty                                              | 65536    | 4096  | 2147483647   | Cache line state transition to Dirty from Clean (E) in BU/L2 (due to write). Indicates write activity. |
| 191 | BUSharedToDirty                                             | 65536    | 4096  | 2147483647   | Cache line state transition to Dirty from Shared (S) in BU/L2 (write to a shared line causing upgrade). |

Notes:
- “From System” generally means beyond the local L2: L3/another core/IO or DRAM via the fabric.
- Coherence states refer to MOESI (Modified, Owner, Exclusive, Shared, Invalid).
- Some counters are core-local (IC/DC/LS/FR/FP/BU) while NB/HT events are from the northbridge/memory controller domain and may require package-wide PMUs on some families.

</details>
