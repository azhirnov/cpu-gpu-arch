**Qualcomm Adreno Performance Counters**

## References

* [A5xx enums](https://github.com/freedreno/envytools/blob/master/registers/adreno/a5xx.xml) - `a5xx_***_perfcounter_select` - counter id
* [A6xx enums](https://github.com/freedreno/envytools/blob/master/registers/adreno/a6xx.xml) - `a6xx_***_perfcounter_select` - counter id
* [HardwarePerfCounter](https://github.com/google/hardware-perfcounter/) - to get access to the performance counters.
* [Mesa driver details](https://docs.mesa3d.org/drivers/freedreno.html)
* [Freedreno wiki](https://github.com/freedreno/freedreno/wiki)

## Notes

**CCU** - Color Cache Unit. Separate cache used by 2D blits and sysmem render target access (and also for resolves to system memory when in **GMEM** mode).<br/>
**CMP** - Compression and Decompression?<br/>
**DMA** - Direct memory access.<br/>
**draw 2D** - blit, fullscreen post process without TBDR ?<br/>
**draw 3D** - TBDR pass ?<br/>
**EU** - execution unit?<br/>
**EFU** - Elementary Function Unit ?. The EFU will have all the necessary instructions to speed up calculations and 3D rendering. (sin, cos, arctan, dot, rasterization, Min / Max, Clip, Culling , Sorting etc etc).<br/>
**FE** - Front End. Index buffer and vertex attribute fetch cluster. Includes **PC**, **VFD**, **VPC**.<br/>
**GMEM** - on-chip memory, used to store attachments during tiled rendering, or as shared memory for compute, or color/depth cache in immediate rendering.<br/>
**GM** - Global memory (RAM).<br/>
**GPR** - General Purpose Registers ?<br/>
**HLSQ** - High Level Sequencer. Manages state for the **SP**s, batches up PS invocations between primitives, is involved in preemption.<br/>
**ICL** - ?<br/>
**LRZ** - Low resolution Z. A low resolution area of the depth buffer that can be initialized during the binning pass to contain the worst-case (farthest) Z values in a block, and then used to early reject fragments during rasterization.<br/>
**LM** - Local memory. GMEM for compute is used as shared memory for waves.<br/>
**ME** - Microcode Engine, handles most **PM4** commands.<br/>
**maskgen** - ?<br/>
**PC** - ?<br/>
**PFP** - Prefetch Parser<br/>
**PM4** - AMD Radeon’s command packet format.<br/>
**ROQ** - **DMA** engine used by the **SQE** for reading memory, with some prefetch buffering.<br/>
**RAS** - Rasterizer. Responsible for generating PS invocations from primitives, also does **LRZ**.<br/>
**RBBM** - Render backend ***(bus/busy?) manager ?<br/>
**RBuffer** - render/read buffer?<br/>
**RB** - Render Backend. Performs both early and late Z testing, blending, and attachment stores of output of the PS.<br/>
**SQE** - a6xx+ replacement for **PFP**/**ME**. This is the microcontroller that runs the microcode which actually processes the command stream and writes to the hardware registers.<br/>
**SP** - shader processor<br/>
**TSE** - Triangle Setup Engine<br/>
**TP** - Texture Processor.<br/>
**PVS** - Primitive Visibility Stream.<br/>
**PC_VS** - Cluster where varyings are read from **VPC** and assembled into primitives to feed **RAS**.<br/>
**UCHE** - Unified L2 cache. Cache behind the vertex fetch, **VSC** writes, texture L1, **LRZ**, and storage image accesses. Misses and flushes access system memory.<br/>
**VSD** - ?<br/>
**VBIF** - ?<br/>
**VFD** - Vertex Fetch and Decode.<br/>
**VPC** - Varying/Position Cache. Hardware block that stores shaded vertex data for primitive assembly.<br/>
**VSC** - Visibility Stream Compressor<br/>
**VS** - Vertex Shader. Responsible for generating VS/GS/tess invocations.<br/>
**VFDP** - ?<br/>
**wave** - warp, 32/64<br/>
**UBWC** - universal bandwidth compression.<br/>
**uSPTP** - Micro Shader Processor Texture Processor.<br/>
**com** - ?<br/>
**dcom** - ?<br/>
**color/depth blocks** - block of 4x4 pixels which will be compressed before transfer from GMem to global memory.<br/>


Warning: some devices requires root to access performance counters.

Some devices requires to enable performance counters from adb, which requires root on some devices: [ref](https://github.com/google/agi/issues/1113#issuecomment-1165786744)
```
adb shell "echo 1 > /sys/class/kgsl/kgsl-3d0/perfcounter"
```

| device | adreno gpu | perf counters without root | reference |
|---|---|---|---|
| Redmi 7A                      | 505 | yes | [[az](https://github.com/azhirnov)] |
| Motorola Defy                 | 610 | yes | [[az](https://github.com/azhirnov)] |
| Asus ROG Phone 3              | 650 | **no** | [ref](https://github.com/google/agi/issues/1343) |
| Asus ROG Phone 5              | 660 | **no** | [[az](https://github.com/azhirnov)] |
| Asus ROG Phone 6              | 730 | **no** | [ref](https://github.com/google/agi/issues/1113#issuecomment-1228880530) |
| Asus Zenfone 9                | 730 | **no** | [ref](https://github.com/google/agi/issues/1113#issuecomment-1228880530) |
| OnePlus 7 Pro                 | 640 | yes | [ref](https://chipsandcheese.com/2024/05/01/inside-the-snapdragon-855s-igpu/) |
| Xiaome Poco X3 Pro            | 640 | **no** | [ref](https://github.com/google/agi/issues/1348) |
| Google Pixel 4 (Pro)          | 640 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| Google Pixel 4a               | 618 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| Google Pixel 4a 5G            | 620 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| Google Pixel 5                | 620 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| Samsung Galaxy S10 series     | 640 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| Samsung Galaxy S20 series     | 650 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| Samsung Galaxy S23            | 740 | **no** | [ref](https://github.com/google/agi/issues/1310) |
| Samsung Galaxy Note 10 series | 640 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| Samsung Galaxy Note 20 series | 650 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| Samsung Galaxy S21 series     | 660 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| Samsung Galaxy Tab S8         | 730 | **no** | [ref](https://github.com/google/agi/issues/1113#issuecomment-1183004666) |
| OPPO Find X3 Pro              | 660 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| OPPO Find X3                  | 650 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| OPPO Reno 6 Pro+              | 650 | yes | [ref](https://developer.android.com/agi/supported-devices) |
| OnePlus 9R                    | 650 | yes | [ref](https://developer.android.com/agi/supported-devices) |


## A5xx

<details>

```
Command Parser: always count
Command Parser: busy gfx core idle
Command Parser: busy cycles
Command Parser: pfp idle
Command Parser: pfp busy working
Command Parser: pfp stall cycles any
Command Parser: pfp starve cycles any
Command Parser: pfp icache miss
Command Parser: pfp icache hit
Command Parser: pfp match pm4 pkt profile
Command Parser: ME busy working
Command Parser: ME idle
Command Parser: ME starve cycles any
Command Parser: ME fifo empty pfp idle
Command Parser: ME fifo empty pfp busy
Command Parser: ME fifo full ME busy
Command Parser: ME fifo full ME non working
Command Parser: ME stall cycles any
Command Parser: ME icache miss
Command Parser: ME icache hit
Command Parser: num preemptions
Command Parser: preemption reaction delay
Command Parser: preemption switch out time
Command Parser: preemption switch IN time
Command Parser: dead draws IN bin render
Command Parser: predicated draws killed
Command Parser: mode switch
Command Parser: zpass done
Command Parser: context done
Command Parser: cache flush
Command Parser: long preemptions

RBBM: always count
RBBM: always ON
RBBM: TSE busy
RBBM: RAS busy
RBBM: PC dcall busy
RBBM: PC vsd busy
RBBM: status masked
RBBM: com busy
RBBM: dcom busy
RBBM: VBIF busy
RBBM: VSC busy
RBBM: tess busy
RBBM: UCHE busy
RBBM: HLSQ busy

PC: busy cycles
PC: working cycles
PC: stall cycles VFD
PC: stall cycles TSE
PC: stall cycles VPC
PC: stall cycles UCHE
PC: stall cycles tess
PC: stall cycles TSE only
PC: stall cycles VPC only
PC: pass1 TF stall cycles
PC: starve cycles for index
PC: starve cycles for tess factor
PC: starve cycles for viz stream
PC: starve cycles for position
PC: starve cycles DI
PC: vis streams loaded
PC: instances
PC: VPC primitives
PC: dead prim
PC: live prim
PC: vertex hits
PC: IA vertices
PC: IA primitives
PC: GS primitives
PC: HS invocations
PC: DS invocations
PC: VS invocations
PC: GS invocations
PC: DS primitives
PC: VPC pos data transaction
PC: 3D drawcalls
PC: 2D drawcalls
PC: non drawcall global events
PC: tess busy cycles
PC: tess working cycles
PC: tess stall cycles PC
PC: tess starve cycles PC

VFD: busy cycles
VFD: stall cycles UCHE
VFD: stall cycles VPC alloc
VFD: stall cycles miss VB
VFD: stall cycles miss Q
VFD: stall cycles SP info
VFD: stall cycles SP attr
VFD: stall cycles vfdp VB
VFD: stall cycles vfdp Q
VFD: decoder packer stall
VFD: starve cycles UCHE
VFD: rbuffer full
VFD: attr info fifo full
VFD: decoded attribute bytes
VFD: num attributes
VFD: instructions
VFD: upper shader fibers
VFD: lower shader fibers
VFD: mode 0 fibers
VFD: mode 1 fibers
VFD: mode 2 fibers
VFD: mode 3 fibers
VFD: mode 4 fibers
VFD: total vertices
VFD: num attr miss
VFD: 1 burst req
VFD: vfdp stall cycles VFD
VFD: vfdp stall cycles VFD index
VFD: vfdp stall cycles VFD prog
VFD: vfdp starve cycles PC
VFD: vfdp VS stage 32 waves

High Level SeQuencer: busy cycles
High Level SeQuencer: stall cycles UCHE
High Level SeQuencer: stall cycles SP state
High Level SeQuencer: stall cycles SP FS stage
High Level SeQuencer: UCHE latency cycles
High Level SeQuencer: UCHE latency count
High Level SeQuencer: FS stage 32 waves
High Level SeQuencer: FS stage 64 waves
High Level SeQuencer: quads
High Level SeQuencer: SP state copy trans FS stage
High Level SeQuencer: SP state copy trans VS stage
High Level SeQuencer: TP state copy trans FS stage
High Level SeQuencer: TP state copy trans VS stage
High Level SeQuencer: CS invocations
High Level SeQuencer: compute drawcalls

VPC: busy cycles
VPC: working cycles
VPC: stall cycles UCHE
VPC: stall cycles VFD wack
VPC: stall cycles HLSQ prim alloc
VPC: stall cycles PC
VPC: stall cycles SP LM
VPC: pos export stall cycles
VPC: starve cycles SP
VPC: starve cycles LRZ
VPC: PC primitives
VPC: SP components
VPC: SP LM primitives
VPC: SP LM components
VPC: SP LM dwords
VPC: streamout components
VPC: grant phases

Triangle Setup Engine: busy cycles
Triangle Setup Engine: clipping cycles
Triangle Setup Engine: stall cycles RAS
Triangle Setup Engine: stall cycles LRZ baryplane
Triangle Setup Engine: stall cycles LRZ zplane
Triangle Setup Engine: starve cycles PC
Triangle Setup Engine: input prim
Triangle Setup Engine: input null prim
Triangle Setup Engine: trival rej prim
Triangle Setup Engine: clipped prim
Triangle Setup Engine: zero area prim
Triangle Setup Engine: faceness culled prim
Triangle Setup Engine: zero pixel prim
Triangle Setup Engine: output null prim
Triangle Setup Engine: output visible prim
Triangle Setup Engine: cinvocation
Triangle Setup Engine: cprimitives
Triangle Setup Engine: 2D input prim
Triangle Setup Engine: 2D alive clcles

RAS: busy cycles
RAS: supertile active cycles
RAS: stall cycles LRZ
RAS: starve cycles TSE
RAS: super tiles
RAS: 8x4 tiles
RAS: maskgen active
RAS: fully covered super tiles
RAS: fully covered 8x4 tiles
RAS: prim killed invisible

Unified L2 Cache: busy cycles
Unified L2 Cache: stall cycles VBIF
Unified L2 Cache: VBIF latency cycles
Unified L2 Cache: VBIF latency samples
Unified L2 Cache: VBIF read beats TP
Unified L2 Cache: VBIF read beats VFD
Unified L2 Cache: VBIF read beats HLSQ
Unified L2 Cache: VBIF read beats LRZ
Unified L2 Cache: VBIF read beats SP
Unified L2 Cache: read requests TP
Unified L2 Cache: read requests VFD
Unified L2 Cache: read requests HLSQ
Unified L2 Cache: read requests LRZ
Unified L2 Cache: read requests SP
Unified L2 Cache: write requests LRZ
Unified L2 Cache: write requests SP
Unified L2 Cache: write requests VPC
Unified L2 Cache: write requests VSC
Unified L2 Cache: evicts
Unified L2 Cache: bank req0
Unified L2 Cache: bank req1
Unified L2 Cache: bank req2
Unified L2 Cache: bank req3
Unified L2 Cache: bank req4
Unified L2 Cache: bank req5
Unified L2 Cache: bank req6
Unified L2 Cache: bank req7
Unified L2 Cache: VBIF read beats ch0
Unified L2 Cache: VBIF read beats ch1
Unified L2 Cache: gmem read beats
Unified L2 Cache: flag count

Texture Processor: busy cycles
Texture Processor: stall cycles UCHE
Texture Processor: latency cycles
Texture Processor: latency trans
Texture Processor: flag cache request samples
Texture Processor: flag cache request latency
Texture Processor: L1 cacheline requests
Texture Processor: L1 cacheline misses
Texture Processor: SP TP trans
Texture Processor: TP SP trans
Texture Processor: output pixels
Texture Processor: filter workload 16bit
Texture Processor: filter workload 32bit
Texture Processor: quads received
Texture Processor: quads offset
Texture Processor: quads shadow
Texture Processor: quads array
Texture Processor: quads gradient
Texture Processor: quads 1D
Texture Processor: quads 2D
Texture Processor: quads buffer
Texture Processor: quads 3D
Texture Processor: quads cube
Texture Processor: state cache requests
Texture Processor: state cache misses
Texture Processor: divergent quads received
Texture Processor: bindless state cache requests
Texture Processor: bindless state cache misses
Texture Processor: prt non resident events
Texture Processor: output pixels point
Texture Processor: output pixels bilinear
Texture Processor: output pixels mip
Texture Processor: output pixels aniso
Texture Processor: output pixels zero lod
Texture Processor: flag cache requests
Texture Processor: flag cache misses
Texture Processor: L1 5 L2 requests
Texture Processor: 2D output pixels
Texture Processor: 2D output pixels point
Texture Processor: 2D output pixels bilinear
Texture Processor: 2D filter workload 16bit
Texture Processor: 2D filter workload 32bit

Shader/Streaming Processor: busy cycles
Shader/Streaming Processor: ALU working cycles
Shader/Streaming Processor: EFU working cycles
Shader/Streaming Processor: stall cycles VPC
Shader/Streaming Processor: stall cycles TP
Shader/Streaming Processor: stall cycles UCHE
Shader/Streaming Processor: stall cycles RB
Shader/Streaming Processor: scheduler non working
Shader/Streaming Processor: wave contexts
Shader/Streaming Processor: wave context cycles
Shader/Streaming Processor: FS stage wave cycles
Shader/Streaming Processor: FS stage wave samples
Shader/Streaming Processor: VS stage wave cycles
Shader/Streaming Processor: VS stage wave samples
Shader/Streaming Processor: FS stage duration cycles
Shader/Streaming Processor: VS stage duration cycles
Shader/Streaming Processor: wave ctrl cycles
Shader/Streaming Processor: wave load cycles
Shader/Streaming Processor: wave emit cycles
Shader/Streaming Processor: wave nop cycles
Shader/Streaming Processor: wave wait cycles
Shader/Streaming Processor: wave fetch cycles
Shader/Streaming Processor: wave idle cycles
Shader/Streaming Processor: wave end cycles
Shader/Streaming Processor: wave long sync cycles
Shader/Streaming Processor: wave short sync cycles
Shader/Streaming Processor: wave join cycles
Shader/Streaming Processor: LM load instructions
Shader/Streaming Processor: LM store instructions
Shader/Streaming Processor: LM atomics
Shader/Streaming Processor: GM load instructions
Shader/Streaming Processor: GM store instructions
Shader/Streaming Processor: GM atomics
Shader/Streaming Processor: VS stage tex instructions
Shader/Streaming Processor: VS stage cflow instructions
Shader/Streaming Processor: VS stage EFU instructions
Shader/Streaming Processor: VS stage full ALU instructions
Shader/Streaming Processor: VS stage half ALU instructions
Shader/Streaming Processor: FS stage tex instructions
Shader/Streaming Processor: FS stage cflow instructions
Shader/Streaming Processor: FS stage EFU instructions
Shader/Streaming Processor: FS stage full ALU instructions
Shader/Streaming Processor: FS stage half ALU instructions
Shader/Streaming Processor: FS stage bary instructions
Shader/Streaming Processor: VS instructions
Shader/Streaming Processor: FS instructions
Shader/Streaming Processor: addr lock count
Shader/Streaming Processor: UCHE read trans
Shader/Streaming Processor: UCHE write trans
Shader/Streaming Processor: export VPC trans
Shader/Streaming Processor: export RB trans
Shader/Streaming Processor: pixels killed
Shader/Streaming Processor: icl1 requests
Shader/Streaming Processor: icl1 misses
Shader/Streaming Processor: icl0 requests
Shader/Streaming Processor: icl0 misses
Shader/Streaming Processor: HS instructions
Shader/Streaming Processor: DS instructions
Shader/Streaming Processor: GS instructions
Shader/Streaming Processor: CS instructions
Shader/Streaming Processor: GPR read
Shader/Streaming Processor: GPR write
Shader/Streaming Processor: LM ch0 requests
Shader/Streaming Processor: LM ch1 requests
Shader/Streaming Processor: LM bank conflicts

RB: busy cycles
RB: stall cycles CCU
RB: stall cycles HLSQ
RB: stall cycles fifo0 full
RB: stall cycles fifo1 full
RB: stall cycles fifo2 full
RB: starve cycles SP
RB: starve cycles LRZ tile
RB: starve cycles CCU
RB: starve cycles Z plane
RB: starve cycles bary plane
RB: Z workload
RB: HLSQ active
RB: Z read
RB: Z write
RB: C read
RB: C write
RB: total pass
RB: Z pass
RB: Z fail
RB: S fail
RB: blended fxp components
RB: blended fp16 components
RB: reserved
RB: 2D alive cycles
RB: 2D stall cycles a2d
RB: 2D starve cycles src
RB: 2D starve cycles SP
RB: 2D starve cycles dst
RB: 2D valid pixels

VBIF: axi read requests ID 0
VBIF: axi read requests ID 1
VBIF: axi read requests ID 2
VBIF: axi read requests ID 3
VBIF: axi read requests ID 4
VBIF: axi read requests ID 5
VBIF: axi read requests ID 6
VBIF: axi read requests ID 7
VBIF: axi read requests ID 8
VBIF: axi read requests ID 9
VBIF: axi read requests ID 10
VBIF: axi read requests ID 11
VBIF: axi read requests ID 12
VBIF: axi read requests ID 13
VBIF: axi read requests ID 14
VBIF: axi read requests ID 15
VBIF: axi0 read requests total
VBIF: axi1 read requests total
VBIF: axi2 read requests total
VBIF: axi3 read requests total
VBIF: axi read requests total
VBIF: axi write requests ID 0
VBIF: axi write requests ID 1
VBIF: axi write requests ID 2
VBIF: axi write requests ID 3
VBIF: axi write requests ID 4
VBIF: axi write requests ID 5
VBIF: axi write requests ID 6
VBIF: axi write requests ID 7
VBIF: axi write requests ID 8
VBIF: axi write requests ID 9
VBIF: axi write requests ID 10
VBIF: axi write requests ID 11
VBIF: axi write requests ID 12
VBIF: axi write requests ID 13
VBIF: axi write requests ID 14
VBIF: axi write requests ID 15
VBIF: axi0 write requests total
VBIF: axi1 write requests total
VBIF: axi2 write requests total
VBIF: axi3 write requests total
VBIF: axi write requests total
VBIF: axi total requests
VBIF: axi read data beats ID 0
VBIF: axi read data beats ID 1
VBIF: axi read data beats ID 2
VBIF: axi read data beats ID 3
VBIF: axi read data beats ID 4
VBIF: axi read data beats ID 5
VBIF: axi read data beats ID 6
VBIF: axi read data beats ID 7
VBIF: axi read data beats ID 8
VBIF: axi read data beats ID 9
VBIF: axi read data beats ID 10
VBIF: axi read data beats ID 11
VBIF: axi read data beats ID 12
VBIF: axi read data beats ID 13
VBIF: axi read data beats ID 14
VBIF: axi read data beats ID 15
VBIF: axi0 read data beats total
VBIF: axi1 read data beats total
VBIF: axi2 read data beats total
VBIF: axi3 read data beats total
VBIF: axi read data beats total
VBIF: axi write data beats ID 0
VBIF: axi write data beats ID 1
VBIF: axi write data beats ID 2
VBIF: axi write data beats ID 3
VBIF: axi write data beats ID 4
VBIF: axi write data beats ID 5
VBIF: axi write data beats ID 6
VBIF: axi write data beats ID 7
VBIF: axi write data beats ID 8
VBIF: axi write data beats ID 9
VBIF: axi write data beats ID 10
VBIF: axi write data beats ID 11
VBIF: axi write data beats ID 12
VBIF: axi write data beats ID 13
VBIF: axi write data beats ID 14
VBIF: axi write data beats ID 15
VBIF: axi0 write data beats total
VBIF: axi1 write data beats total
VBIF: axi2 write data beats total
VBIF: axi3 write data beats total
VBIF: axi write data beats total
VBIF: axi data beats total

VSC: busy cycles
VSC: working cycles
VSC: stall cycles UCHE
VSC: eot num

Cache and Compression Unit: busy cycles
Cache and Compression Unit: stall cycles RB depth return
Cache and Compression Unit: stall cycles RB color return
Cache and Compression Unit: starve cycles flag return
Cache and Compression Unit: depth blocks
Cache and Compression Unit: color blocks
Cache and Compression Unit: depth block hit
Cache and Compression Unit: color block hit
Cache and Compression Unit: partial block read
Cache and Compression Unit: gmem read
Cache and Compression Unit: gmem write
Cache and Compression Unit: depth read flag0 count
Cache and Compression Unit: depth read flag1 count
Cache and Compression Unit: depth read flag2 count
Cache and Compression Unit: depth read flag3 count
Cache and Compression Unit: depth read flag4 count
Cache and Compression Unit: color read flag0 count
Cache and Compression Unit: color read flag1 count
Cache and Compression Unit: color read flag2 count
Cache and Compression Unit: color read flag3 count
Cache and Compression Unit: color read flag4 count
Cache and Compression Unit: 2D busy cycles
Cache and Compression Unit: 2D RD req
Cache and Compression Unit: 2D WR req
Cache and Compression Unit: 2D reorder starve cycles
Cache and Compression Unit: 2D pixels

Low Resolution Z: busy cycles
Low Resolution Z: starve cycles RAS
Low Resolution Z: stall cycles RB
Low Resolution Z: stall cycles VSC
Low Resolution Z: stall cycles VPC
Low Resolution Z: stall cycles flag prefetch
Low Resolution Z: stall cycles UCHE
Low Resolution Z: LRZ read
Low Resolution Z: LRZ write
Low Resolution Z: read latency
Low Resolution Z: merge cache updating
Low Resolution Z: prim killed BY maskgen
Low Resolution Z: prim killed BY LRZ
Low Resolution Z: visible prim after LRZ
Low Resolution Z: full 8x8 tiles
Low Resolution Z: partial 8x8 tiles
Low Resolution Z: tile killed
Low Resolution Z: total pixel
Low Resolution Z: visible pixel after LRZ

CMP: cmpdecmp stall cycles VBIF
CMP: cmpdecmp VBIF latency cycles
CMP: cmpdecmp VBIF latency samples
CMP: cmpdecmp VBIF read data CCU
CMP: cmpdecmp VBIF write data CCU
CMP: cmpdecmp VBIF read request
CMP: cmpdecmp VBIF write request
CMP: cmpdecmp VBIF read data
CMP: cmpdecmp VBIF write data
CMP: cmpdecmp flag fetch cycles
CMP: cmpdecmp flag fetch samples
CMP: cmpdecmp depth write flag1 count
CMP: cmpdecmp depth write flag2 count
CMP: cmpdecmp depth write flag3 count
CMP: cmpdecmp depth write flag4 count
CMP: cmpdecmp color write flag1 count
CMP: cmpdecmp color write flag2 count
CMP: cmpdecmp color write flag3 count
CMP: cmpdecmp color write flag4 count
CMP: cmpdecmp 2D stall cycles VBIF req
CMP: cmpdecmp 2D stall cycles VBIF WR
CMP: cmpdecmp 2D stall cycles VBIF return
CMP: cmpdecmp 2D RD data
CMP: cmpdecmp 2D WR data
```
</details>

### Adreno 505

<details>

| group, counter | name | desc |
|---|---|---|
| - | **Command Parser** | - |
| 0, 0 | always count | All cycles (?) |
| 0, 1 | busy gfx core idle | Cycles where Gfx is busy but Core is idle (?) |
| 0, 2 | busy cycles | Only busy cycles. `utilization = busy_cycles / always_count` (?) |
| 0, 3 | pfp idle | Prefetch parser idle (cycles?) |
| 0, 4 | pfp busy working | Prefetch parser busy (cycles?) |
| 0, 5 | pfp stall cycles any | Prefetch parser stall cycles. |
| 0, 6 | pfp starve cycles any |
| 0, 7 | pfp icache miss | Prefetch parser instruction cache miss (count?) |
| 0, 8 | pfp icache hit | Prefetch parser instruction cache hit (count?) |
| 0, 9 | pfp match pm4 pkt profile |
| 0, 10 | ME busy working | Microcode Engine busy (cycles?) |
| 0, 11 | ME idle | Microcode Engine idle (cycles?) |
| 0, 12 | ME starve cycles any |
| 0, 13 | ME fifo empty pfp idle |
| 0, 14 | ME fifo empty pfp busy |
| 0, 15 | ME fifo full ME busy |
| 0, 16 | ME fifo full ME non working |
| 0, 17 | ME stall cycles any |
| 0, 18 | ME icache miss | Microcode Engine instruction cache miss (count?) |
| 0, 19 | ME icache hit | Microcode Engine instruction cache hit (count?) |
| 0, 20 | num preemptions |
| 0, 21 | preemption reaction delay |
| 0, 22 | preemption switch out time |
| 0, 23 | preemption switch IN time |
| 0, 24 | dead draws IN bin render |
| 0, 25 | predicated draws killed |
| 0, 26 | mode switch |
| 0, 27 | zpass done |
| 0, 28 | context done |
| 0, 29 | cache flush |
| 0, 30 | long preemptions |
| - | **RBBM** | - |
| 1, 0 | always count | All cycles (?) |
| 1, 1 | always ON | Busy cycles (?) |
| 1, 2 | TSE busy | (cycles?) |
| 1, 3 | RAS busy | (cycles?) |
| 1, 4 | PC dcall busy | (cycles?) |
| 1, 5 | PC vsd busy | (cycles?) |
| 1, 6 | status masked | (cycles?) |
| 1, 7 | com busy | (cycles?) |
| 1, 8 | dcom busy | (cycles?) |
| 1, 9 | VBIF busy | (cycles?) |
| 1, 10 | VSC busy | (cycles?) |
| 1, 11 | tess busy | (cycles?) |
| 1, 12 | UCHE busy | (cycles?) |
| 1, 13 | HLSQ busy | (cycles?) |
| - | **PC** | - |
| 2, 0 | busy cycles |
| 2, 1 | working cycles |
| 2, 2 | stall cycles VFD |
| 2, 3 | stall cycles TSE |
| 2, 4 | stall cycles VPC |
| 2, 5 | stall cycles UCHE |
| 2, 6 | stall cycles tess |
| 2, 7 | stall cycles TSE only |
| 2, 8 | stall cycles VPC only |
| 2, 9 | pass1 TF stall cycles |
| 2, 10 | starve cycles for index |
| 2, 11 | starve cycles for tess factor |
| 2, 12 | starve cycles for viz stream |
| 2, 13 | starve cycles for position |
| 2, 14 | starve cycles DI |
| 2, 15 | vis streams loaded |
| 2, 16 | instances | Number of instances in draw call (?) |
| 2, 17 | VPC primitives | Varying/Position Cache primitives (?) |
| 2, 18 | dead prim | Invisible primitives (?) |
| 2, 19 | live prim | Visible primitives (?) |
| 2, 20 | vertex hits | Vertex cache hit. `utilization = vertex_hits / IA_vertices` (?) |
| 2, 21 | IA vertices | Input vertices (?) |
| 2, 22 | IA primitives | Input primitives (?) |
| 2, 23 | GS primitives |
| 2, 24 | HS invocations |
| 2, 25 | DS invocations |
| 2, 26 | VS invocations |
| 2, 27 | GS invocations |
| 2, 28 | DS primitives |
| 2, 29 | VPC pos data transaction |
| 2, 30 | 3D drawcalls |
| 2, 31 | 2D drawcalls |
| 2, 32 | non drawcall global events |
| 2, 33 | tess busy cycles |
| 2, 34 | tess working cycles |
| 2, 35 | tess stall cycles PC |
| 2, 36 | tess starve cycles PC |
| - | **Vertex Fetch and Decode** | - |
| 3, 0 | busy cycles |
| 3, 1 | stall cycles UCHE |
| 3, 2 | stall cycles VPC alloc |
| 3, 3 | stall cycles miss VB |
| 3, 4 | stall cycles miss Q |
| 3, 5 | stall cycles SP info |
| 3, 6 | stall cycles SP attr |
| 3, 7 | stall cycles vfdp VB |
| 3, 8 | stall cycles vfdp Q |
| 3, 9 | decoder packer stall |
| 3, 10 | starve cycles UCHE |
| 3, 11 | rbuffer full |
| 3, 12 | attr info fifo full |
| 3, 13 | decoded attribute bytes |
| 3, 14 | num attributes |
| 3, 15 | instructions |
| 3, 16 | upper shader fibers |
| 3, 17 | lower shader fibers |
| 3, 18 | mode 0 fibers |
| 3, 19 | mode 1 fibers |
| 3, 20 | mode 2 fibers |
| 3, 21 | mode 3 fibers |
| 3, 22 | mode 4 fibers |
| 3, 23 | total vertices |
| 3, 24 | num attr miss |
| 3, 25 | 1 burst req |
| 3, 26 | vfdp stall cycles VFD |
| 3, 27 | vfdp stall cycles VFD index |
| 3, 28 | vfdp stall cycles VFD prog |
| 3, 29 | vfdp starve cycles PC |
| 3, 30 | vfdp VS stage 32 waves |
| - | **High Level SeQuencer** | - |
| 4, 0 | busy cycles |
| 4, 1 | stall cycles UCHE |
| 4, 2 | stall cycles SP state |
| 4, 3 | stall cycles SP FS stage |
| 4, 4 | UCHE latency cycles | L2 latency cycles |
| 4, 5 | UCHE latency count |
| 4, 6 | FS stage 32 waves | Number of waves with 32 threads. |
| 4, 7 | FS stage 64 waves | Number of waves with 64 threads. |
| 4, 8 | quads | Number of 2x2 pixel quads. |
| 4, 9 | SP state copy trans FS stage |
| 4, 10 | SP state copy trans VS stage |
| 4, 11 | TP state copy trans FS stage |
| 4, 12 | TP state copy trans VS stage |
| 4, 13 | CS invocations | Compute shader total threads. |
| 4, 14 | compute drawcalls | Dispatch count. |
| - | **Varying/Position Cache** | - |
| 5, 0 | busy cycles |
| 5, 1 | working cycles |
| 5, 2 | stall cycles UCHE |
| 5, 3 | stall cycles VFD wack |
| 5, 4 | stall cycles HLSQ prim alloc |
| 5, 5 | stall cycles PC |
| 5, 6 | stall cycles SP LM | stall cycles on Streaming Processor Local Memory (?) |
| 5, 7 | pos export stall cycles |
| 5, 8 | starve cycles SP |
| 5, 9 | starve cycles LRZ |
| 5, 10 | PC primitives |
| 5, 11 | SP components |
| 5, 12 | SP LM primitives | Streaming Processor Local Memory primitive count (?) |
| 5, 13 | SP LM components |
| 5, 14 | SP LM dwords |
| 5, 15 | streamout components |
| 5, 16 | grant phases |
| - | **Triangle Setup Engine** | - |
| 6, 0 | busy cycles |
| 6, 1 | clipping cycles |
| 6, 2 | stall cycles RAS |
| 6, 3 | stall cycles LRZ baryplane |
| 6, 4 | stall cycles LRZ zplane |
| 6, 5 | starve cycles PC |
| 6, 6 | input prim |
| 6, 7 | input null prim |
| 6, 8 | trival rej prim |
| 6, 9 | clipped prim |
| 6, 10 | zero area prim |
| 6, 11 | faceness culled prim |
| 6, 12 | zero pixel prim |
| 6, 13 | output null prim |
| 6, 14 | output visible prim |
| 6, 15 | cinvocation |
| 6, 16 | cprimitives |
| 6, 17 | 2D input prim |
| 6, 18 | 2D alive clcles |
| - | **Rasterizer** | - |
| 7, 0 | busy cycles |
| 7, 1 | supertile active cycles |
| 7, 2 | stall cycles LRZ |
| 7, 3 | starve cycles TSE |
| 7, 4 | super tiles | Large tiles from 32x32px to 256x256 and greater. Use all GMem to store attachments. |
| 7, 5 | 8x4 tiles | tiles inside super tile? |
| 7, 6 | maskgen active |
| 7, 7 | fully covered super tiles | All pixels in tile are filled. |
| 7, 8 | fully covered 8x4 tiles | All pixels in tile are filled. |
| 7, 9 | prim killed invisible |
| - | **Unified L2 Cache** | - |
| 8, 0 | busy cycles |
| 8, 1 | stall cycles VBIF |
| 8, 2 | VBIF latency cycles |
| 8, 3 | VBIF latency samples |
| 8, 4 | VBIF read beats TP |
| 8, 5 | VBIF read beats VFD |
| 8, 6 | VBIF read beats HLSQ |
| 8, 7 | VBIF read beats LRZ |
| 8, 8 | VBIF read beats SP |
| 8, 9 | read requests TP |
| 8, 10 | read requests VFD |
| 8, 11 | read requests HLSQ |
| 8, 12 | read requests LRZ |
| 8, 13 | read requests SP |
| 8, 14 | write requests LRZ |
| 8, 15 | write requests SP |
| 8, 16 | write requests VPC |
| 8, 17 | write requests VSC |
| 8, 18 | evicts |
| 8, 19 | bank req0 |
| 8, 20 | bank req1 |
| 8, 21 | bank req2 |
| 8, 22 | bank req3 |
| 8, 23 | bank req4 |
| 8, 24 | bank req5 |
| 8, 25 | bank req6 |
| 8, 26 | bank req7 |
| 8, 27 | VBIF read beats ch0 |
| 8, 28 | VBIF read beats ch1 |
| 8, 29 | gmem read beats |
| 8, 30 | flag count |
| - | **Texture Processor** | - |
| 9, 0 | busy cycles |
| 9, 1 | stall cycles UCHE |
| 9, 2 | latency cycles |
| 9, 3 | latency trans |
| 9, 4 | flag cache request samples |
| 9, 5 | flag cache request latency |
| 9, 6 | L1 cacheline requests |
| 9, 7 | L1 cacheline misses |
| 9, 8 | SP TP trans |
| 9, 9 | TP SP trans |
| 9, 10 | output pixels |
| 9, 11 | filter workload 16bit | fp16 or 16bit per texel? |
| 9, 12 | filter workload 32bit | fp32 or 32bit per texel? |
| 9, 13 | quads received |
| 9, 14 | quads offset |
| 9, 15 | quads shadow |
| 9, 16 | quads array |
| 9, 17 | quads gradient |
| 9, 18 | quads 1D |
| 9, 19 | quads 2D |
| 9, 20 | quads buffer |
| 9, 21 | quads 3D |
| 9, 22 | quads cube |
| 9, 23 | state cache requests |
| 9, 24 | state cache misses |
| 9, 25 | divergent quads received |
| 9, 26 | bindless state cache requests |
| 9, 27 | bindless state cache misses |
| 9, 28 | prt non resident events |
| 9, 29 | output pixels point |
| 9, 30 | output pixels bilinear |
| 9, 31 | output pixels mip |
| 9, 32 | output pixels aniso |
| 9, 33 | output pixels zero lod |
| 9, 34 | flag cache requests |
| 9, 35 | flag cache misses |
| 9, 36 | L1 5 L2 requests |
| 9, 37 | 2D output pixels |
| 9, 38 | 2D output pixels point |
| 9, 39 | 2D output pixels bilinear |
| 9, 40 | 2D filter workload 16bit |
| 9, 41 | 2D filter workload 32bit |
| - | **Shader/Streaming Processor** | - |
| 10, 0 | busy cycles |
| 10, 1 | ALU working cycles | Cycles during FMA instructions |
| 10, 2 | EFU working cycles | Cycles during EFU (special) instructions. |
| 10, 3 | stall cycles VPC |
| 10, 4 | stall cycles TP |
| 10, 5 | stall cycles UCHE |
| 10, 6 | stall cycles RB |
| 10, 7 | scheduler non working |
| 10, 8 | wave contexts |
| 10, 9 | wave context cycles |
| 10, 10 | FS stage wave cycles |
| 10, 11 | FS stage wave samples |
| 10, 12 | VS stage wave cycles |
| 10, 13 | VS stage wave samples |
| 10, 14 | FS stage duration cycles |
| 10, 15 | VS stage duration cycles |
| 10, 16 | wave ctrl cycles |
| 10, 17 | wave load cycles |
| 10, 18 | wave emit cycles |
| 10, 19 | wave nop cycles |
| 10, 20 | wave wait cycles |
| 10, 21 | wave fetch cycles |
| 10, 22 | wave idle cycles |
| 10, 23 | wave end cycles |
| 10, 24 | wave long sync cycles |
| 10, 25 | wave short sync cycles |
| 10, 26 | wave join cycles |
| 10, 27 | LM load instructions | Local memory load instruction count |
| 10, 28 | LM store instructions | Local memory store instruction count |
| 10, 29 | LM atomics | Local memory atomic instruction count |
| 10, 30 | GM load instructions | Global memory load instruction count |
| 10, 31 | GM store instructions | Global memory store instruction count |
| 10, 32 | GM atomics | Global memory atomic instruction count |
| 10, 33 | VS stage tex instructions |
| 10, 34 | VS stage cflow instructions |
| 10, 35 | VS stage EFU instructions | EFU instruction count in Vertex shader |
| 10, 36 | VS stage full ALU instructions | Full ALU instruction count in Vertex shader (wave64 / dual issue?) |
| 10, 37 | VS stage half ALU instructions | Half ALU instruction count in Vertex shader (fp16 & fp32) |
| 10, 38 | FS stage tex instructions |
| 10, 39 | FS stage cflow instructions |
| 10, 40 | FS stage EFU instructions | EFU instruction count in Fragment shader |
| 10, 41 | FS stage full ALU instructions | Full ALU instruction count in Fragment shader (wave64 / dual issue?) |
| 10, 42 | FS stage half ALU instructions | Half ALU instruction count in Fragment shader (fp16 & fp32) |
| 10, 43 | FS stage bary instructions | Interpolation instructions (?) |
| 10, 44 | VS instructions | Vertex shader instruction count |
| 10, 45 | FS instructions | Fragment shader instruction count |
| 10, 46 | addr lock count |
| 10, 47 | UCHE read trans | Unified L2 cache read transactions (in pixels or group of pixels). It is buffer/image storage load operation. |
| 10, 48 | UCHE write trans | Unified L2 cache write transactions (in pixels or group of pixels). It is buffer/image storage store operation. |
| 10, 49 | export VPC trans |
| 10, 50 | export RB trans |
| 10, 51 | pixels killed |
| 10, 52 | icl1 requests |
| 10, 53 | icl1 misses |
| 10, 54 | icl0 requests |
| 10, 55 | icl0 misses |
| 10, 56 | HS instructions |
| 10, 57 | DS instructions |
| 10, 58 | GS instructions |
| 10, 59 | CS instructions | Compute shader instruction count |
| 10, 60 | GPR read | Register read (count?) |
| 10, 61 | GPR write | Register write (count?) |
| 10, 62 | LM ch0 requests |
| 10, 63 | LM ch1 requests |
| 10, 64 | LM bank conflicts |
| - | **Render backend** | - |
| 11, 0 | busy cycles |
| 11, 1 | stall cycles CCU |
| 11, 2 | stall cycles HLSQ |
| 11, 3 | stall cycles fifo0 full |
| 11, 4 | stall cycles fifo1 full |
| 11, 5 | stall cycles fifo2 full |
| 11, 6 | starve cycles SP |
| 11, 7 | starve cycles LRZ tile |
| 11, 8 | starve cycles CCU |
| 11, 9 | starve cycles Z plane |
| 11, 10 | starve cycles bary plane |
| 11, 11 | Z workload |
| 11, 12 | HLSQ active | cycles? |
| 11, 13 | Z read | bytes |
| 11, 14 | Z write | bytes |
| 11, 15 | C read | bytes |
| 11, 16 | C write | bytes |
| 11, 17 | total pass | pixels |
| 11, 18 | Z pass | pixels |
| 11, 19 | Z fail | pixels |
| 11, 20 | S fail | pixels |
| 11, 21 | blended fxp components | pixels? |
| 11, 22 | blended fp16 components | pixels? |
| 11, 23 | reserved |
| 11, 24 | 2D alive cycles |
| 11, 25 | 2D stall cycles a2d |
| 11, 26 | 2D starve cycles src |
| 11, 27 | 2D starve cycles SP |
| 11, 28 | 2D starve cycles dst |
| 11, 29 | 2D valid pixels |
| - | **VBIF** | - |
| 13, 0 | axi read requests ID 0 |
| 13, 1 | axi read requests ID 1 |
| 13, 2 | axi read requests ID 2 |
| 13, 3 | axi read requests ID 3 |
| 13, 4 | axi read requests ID 4 |
| 13, 5 | axi read requests ID 5 |
| 13, 6 | axi read requests ID 6 |
| 13, 7 | axi read requests ID 7 |
| 13, 8 | axi read requests ID 8 |
| 13, 9 | axi read requests ID 9 |
| 13, 10 | axi read requests ID 10 |
| 13, 11 | axi read requests ID 11 |
| 13, 12 | axi read requests ID 12 |
| 13, 13 | axi read requests ID 13 |
| 13, 14 | axi read requests ID 14 |
| 13, 15 | axi read requests ID 15 |
| 13, 16 | axi0 read requests total |
| 13, 17 | axi1 read requests total |
| 13, 18 | axi2 read requests total |
| 13, 19 | axi3 read requests total |
| 13, 20 | axi read requests total |
| 13, 21 | axi write requests ID 0 |
| 13, 22 | axi write requests ID 1 |
| 13, 23 | axi write requests ID 2 |
| 13, 24 | axi write requests ID 3 |
| 13, 25 | axi write requests ID 4 |
| 13, 26 | axi write requests ID 5 |
| 13, 27 | axi write requests ID 6 |
| 13, 28 | axi write requests ID 7 |
| 13, 29 | axi write requests ID 8 |
| 13, 30 | axi write requests ID 9 |
| 13, 31 | axi write requests ID 10 |
| 13, 32 | axi write requests ID 11 |
| 13, 33 | axi write requests ID 12 |
| 13, 34 | axi write requests ID 13 |
| 13, 35 | axi write requests ID 14 |
| 13, 36 | axi write requests ID 15 |
| 13, 37 | axi0 write requests total |
| 13, 38 | axi1 write requests total |
| 13, 39 | axi2 write requests total |
| 13, 40 | axi3 write requests total |
| 13, 41 | axi write requests total |
| 13, 42 | axi total requests |
| 13, 43 | axi read data beats ID 0 |
| 13, 44 | axi read data beats ID 1 |
| 13, 45 | axi read data beats ID 2 |
| 13, 46 | axi read data beats ID 3 |
| 13, 47 | axi read data beats ID 4 |
| 13, 48 | axi read data beats ID 5 |
| 13, 49 | axi read data beats ID 6 |
| 13, 50 | axi read data beats ID 7 |
| 13, 51 | axi read data beats ID 8 |
| 13, 52 | axi read data beats ID 9 |
| 13, 53 | axi read data beats ID 10 |
| 13, 54 | axi read data beats ID 11 |
| 13, 55 | axi read data beats ID 12 |
| 13, 56 | axi read data beats ID 13 |
| 13, 57 | axi read data beats ID 14 |
| 13, 58 | axi read data beats ID 15 |
| 13, 59 | axi0 read data beats total |
| 13, 60 | axi1 read data beats total |
| 13, 61 | axi2 read data beats total |
| 13, 62 | axi3 read data beats total |
| 13, 63 | axi read data beats total |
| 13, 64 | axi write data beats ID 0 |
| 13, 65 | axi write data beats ID 1 |
| 13, 66 | axi write data beats ID 2 |
| 13, 67 | axi write data beats ID 3 |
| 13, 68 | axi write data beats ID 4 |
| 13, 69 | axi write data beats ID 5 |
| 13, 70 | axi write data beats ID 6 |
| 13, 71 | axi write data beats ID 7 |
| 13, 72 | axi write data beats ID 8 |
| 13, 73 | axi write data beats ID 9 |
| 13, 74 | axi write data beats ID 10 |
| 13, 75 | axi write data beats ID 11 |
| 13, 76 | axi write data beats ID 12 |
| 13, 77 | axi write data beats ID 13 |
| 13, 78 | axi write data beats ID 14 |
| 13, 79 | axi write data beats ID 15 |
| 13, 80 | axi0 write data beats total |
| 13, 81 | axi1 write data beats total |
| 13, 82 | axi2 write data beats total |
| 13, 83 | axi3 write data beats total |
| 13, 84 | axi write data beats total |
| 13, 85 | axi data beats total |
| - | **Visibility Stream Compressor** | - |
| 23, 0 | busy cycles |
| 23, 1 | working cycles |
| 23, 2 | stall cycles UCHE |
| 23, 3 | eot num |
| - | **Cache and Compression Unit** | - |
| 24, 0 | busy cycles |
| 24, 1 | stall cycles RB depth return |
| 24, 2 | stall cycles RB color return |
| 24, 3 | starve cycles flag return |
| 24, 4 | depth blocks | number of 4x4 pixel blocks |
| 24, 5 | color blocks | number of 4x4 pixel blocks |
| 24, 6 | depth block hit |
| 24, 7 | color block hit |
| 24, 8 | partial block read |
| 24, 9 | gmem read | bytes? |
| 24, 10 | gmem write | bytes? |
| 24, 11 | depth read flag0 count |
| 24, 12 | depth read flag1 count |
| 24, 13 | depth read flag2 count |
| 24, 14 | depth read flag3 count |
| 24, 15 | depth read flag4 count |
| 24, 16 | color read flag0 count |
| 24, 17 | color read flag1 count |
| 24, 18 | color read flag2 count |
| 24, 19 | color read flag3 count |
| 24, 20 | color read flag4 count |
| 24, 21 | 2D busy cycles |
| 24, 22 | 2D RD req |
| 24, 23 | 2D WR req |
| 24, 24 | 2D reorder starve cycles |
| 24, 25 | 2D pixels |
| - | **Low Resolution Z pass** | - |
| 25, 0 | busy cycles |
| 25, 1 | starve cycles RAS |
| 25, 2 | stall cycles RB |
| 25, 3 | stall cycles VSC |
| 25, 4 | stall cycles VPC |
| 25, 5 | stall cycles flag prefetch |
| 25, 6 | stall cycles UCHE |
| 25, 7 | LRZ read |
| 25, 8 | LRZ write |
| 25, 9 | read latency |
| 25, 10 | merge cache updating |
| 25, 11 | prim killed BY maskgen |
| 25, 12 | prim killed BY LRZ |
| 25, 13 | visible prim after LRZ |
| 25, 14 | full 8x8 tiles |
| 25, 15 | partial 8x8 tiles |
| 25, 16 | tile killed |
| 25, 17 | total pixel |
| 25, 18 | visible pixel after LRZ |
| - | **CMP** | - |
| 26, 0 | cmpdecmp stall cycles VBIF |
| 26, 1 | cmpdecmp VBIF latency cycles |
| 26, 2 | cmpdecmp VBIF latency samples |
| 26, 3 | cmpdecmp VBIF read data CCU |
| 26, 4 | cmpdecmp VBIF write data CCU |
| 26, 5 | cmpdecmp VBIF read request |
| 26, 6 | cmpdecmp VBIF write request |
| 26, 7 | cmpdecmp VBIF read data |
| 26, 8 | cmpdecmp VBIF write data |
| 26, 9 | cmpdecmp flag fetch cycles |
| 26, 10 | cmpdecmp flag fetch samples |
| 26, 11 | cmpdecmp depth write flag1 count |
| 26, 12 | cmpdecmp depth write flag2 count |
| 26, 13 | cmpdecmp depth write flag3 count |
| 26, 14 | cmpdecmp depth write flag4 count |
| 26, 15 | cmpdecmp color write flag1 count |
| 26, 16 | cmpdecmp color write flag2 count |
| 26, 17 | cmpdecmp color write flag3 count |
| 26, 18 | cmpdecmp color write flag4 count |
| 26, 19 | cmpdecmp 2D stall cycles VBIF req |
| 26, 20 | cmpdecmp 2D stall cycles VBIF WR |
| 26, 21 | cmpdecmp 2D stall cycles VBIF return |
| 26, 22 | cmpdecmp 2D RD data |
| 26, 23 | cmpdecmp 2D WR data |
</details>

## A6xx

<details>

```
Command Parser: always count
Command Parser: busy gfx core idle
Command Parser: busy cycles
Command Parser: num preemptions
Command Parser: preemption reaction delay
Command Parser: preemption switch out time
Command Parser: preemption switch IN time
Command Parser: dead draws IN bin render
Command Parser: predicated draws killed
Command Parser: mode switch
Command Parser: zpass done
Command Parser: context done
Command Parser: cache flush
Command Parser: long preemptions
Command Parser: sqe I cache starve
Command Parser: sqe idle
Command Parser: sqe pm4 starve RB IB
Command Parser: sqe pm4 starve sds
Command Parser: sqe mrb starve
Command Parser: sqe rrb starve
Command Parser: sqe vsd starve
Command Parser: vsd decode starve
Command Parser: sqe pipe out stall
Command Parser: sqe sync stall
Command Parser: sqe pm4 wfi stall
Command Parser: sqe sys wfi stall
Command Parser: sqe T4 exec
Command Parser: sqe load state exec
Command Parser: sqe save sds state
Command Parser: sqe draw exec
Command Parser: sqe ctxt reg bunch exec
Command Parser: sqe exec profiled
Command Parser: memory pool empty
Command Parser: memory pool sync stall
Command Parser: memory pool above thresh
Command Parser: ahb WR stall pre draws
Command Parser: ahb stall sqe gmu
Command Parser: ahb stall sqe WR other
Command Parser: ahb stall sqe RD other
Command Parser: cluster0 empty
Command Parser: cluster1 empty
Command Parser: cluster2 empty
Command Parser: cluster3 empty
Command Parser: cluster4 empty
Command Parser: cluster5 empty
Command Parser: pm4 data
Command Parser: pm4 headers
Command Parser: vbif read beats
Command Parser: vbif write beats
Command Parser: sqe instr counter

RBBM: always count
RBBM: always ON
RBBM: TSE busy
RBBM: RAS busy
RBBM: PC dcall busy
RBBM: PC vsd busy
RBBM: status masked
RBBM: com busy
RBBM: dcom busy
RBBM: vbif busy
RBBM: VSC busy
RBBM: tess busy
RBBM: UCHE busy
RBBM: HLSQ busy

PC: busy cycles
PC: working cycles
PC: stall cycles VFD
PC: stall cycles TSE
PC: stall cycles VPC
PC: stall cycles UCHE
PC: stall cycles tess
PC: stall cycles TSE only
PC: stall cycles VPC only
PC: pass1 TF stall cycles
PC: starve cycles for index
PC: starve cycles for tess factor
PC: starve cycles for viz stream
PC: starve cycles for position
PC: starve cycles DI
PC: vis streams loaded
PC: instances
PC: VPC primitives
PC: dead prim
PC: live prim
PC: vertex hits
PC: IA vertices
PC: IA primitives
PC: GS primitives
PC: HS invocations
PC: DS invocations
PC: VS invocations
PC: GS invocations
PC: DS primitives
PC: VPC pos data transaction
PC: 3D drawcalls
PC: 2D drawcalls
PC: non drawcall global events
PC: tess busy cycles
PC: tess working cycles
PC: tess stall cycles PC
PC: tess starve cycles PC
PC: TSE transaction
PC: TSE vertex
PC: tess PC UV trans
PC: tess PC UV patches
PC: tess factor trans

VFD: busy cycles
VFD: stall cycles UCHE
VFD: stall cycles VPC alloc
VFD: stall cycles SP info
VFD: stall cycles SP attr
VFD: starve cycles UCHE
VFD: rbuffer full
VFD: attr info fifo full
VFD: decoded attribute bytes
VFD: num attributes
VFD: upper shader fibers
VFD: lower shader fibers
VFD: mode 0 fibers
VFD: mode 1 fibers
VFD: mode 2 fibers
VFD: mode 3 fibers
VFD: mode 4 fibers
VFD: total vertices
VFD: vfdp stall cycles VFD
VFD: vfdp stall cycles VFD index
VFD: vfdp stall cycles VFD prog
VFD: vfdp starve cycles PC
VFD: vfdp VS stage waves

High Level SeQuencer: busy cycles
High Level SeQuencer: stall cycles UCHE
High Level SeQuencer: stall cycles SP state
High Level SeQuencer: stall cycles SP FS stage
High Level SeQuencer: UCHE latency cycles
High Level SeQuencer: UCHE latency count
High Level SeQuencer: FS stage 1X waves
High Level SeQuencer: FS stage 2X waves
High Level SeQuencer: quads
High Level SeQuencer: CS invocations
High Level SeQuencer: compute drawcalls
High Level SeQuencer: FS data wait programming
High Level SeQuencer: dual FS prog active
High Level SeQuencer: dual VS prog active
High Level SeQuencer: FS batch count zero
High Level SeQuencer: VS batch count zero
High Level SeQuencer: wave pending NO quad
High Level SeQuencer: wave pending NO prim base
High Level SeQuencer: stall cycles VPC
High Level SeQuencer: pixels
High Level SeQuencer: draw mode switch vsfs sync

VPC: busy cycles
VPC: working cycles
VPC: stall cycles UCHE
VPC: stall cycles VFD wack
VPC: stall cycles HLSQ prim alloc
VPC: stall cycles PC
VPC: stall cycles SP LM
VPC: starve cycles SP
VPC: starve cycles LRZ
VPC: PC primitives
VPC: SP components
VPC: stall cycles vpcram pos
VPC: LRZ assign primitives
VPC: RB visible primitives
VPC: LM transaction
VPC: streamout transaction
VPC: VS busy cycles
VPC: PS busy cycles
VPC: VS working cycles
VPC: PS working cycles
VPC: starve cycles RB
VPC: num vpcram read pos
VPC: wit full cycles
VPC: vpcram full cycles
VPC: LM full wait for intp end
VPC: num vpcram write
VPC: num vpcram read SO
VPC: num attr req LM

Triangle Setup Engine: busy cycles
Triangle Setup Engine: clipping cycles
Triangle Setup Engine: stall cycles RAS
Triangle Setup Engine: stall cycles LRZ baryplane
Triangle Setup Engine: stall cycles LRZ zplane
Triangle Setup Engine: starve cycles PC
Triangle Setup Engine: input prim
Triangle Setup Engine: input null prim
Triangle Setup Engine: trival rej prim
Triangle Setup Engine: clipped prim
Triangle Setup Engine: zero area prim
Triangle Setup Engine: faceness culled prim
Triangle Setup Engine: zero pixel prim
Triangle Setup Engine: output null prim
Triangle Setup Engine: output visible prim
Triangle Setup Engine: cinvocation
Triangle Setup Engine: cprimitives
Triangle Setup Engine: 2D input prim
Triangle Setup Engine: 2D alive cycles
Triangle Setup Engine: clip planes

RAS: busy cycles
RAS: supertile active cycles
RAS: stall cycles LRZ
RAS: starve cycles TSE
RAS: super tiles
RAS: 8x4 tiles
RAS: maskgen active
RAS: fully covered super tiles
RAS: fully covered 8x4 tiles
RAS: prim killed invisible
RAS: supertile gen active cycles
RAS: LRZ intf working cycles
RAS: blocks

Unified L2 Cache: busy cycles
Unified L2 Cache: stall cycles arbiter
Unified L2 Cache: vbif latency cycles
Unified L2 Cache: vbif latency samples
Unified L2 Cache: vbif read beats TP
Unified L2 Cache: vbif read beats VFD
Unified L2 Cache: vbif read beats HLSQ
Unified L2 Cache: vbif read beats LRZ
Unified L2 Cache: vbif read beats SP
Unified L2 Cache: read requests TP
Unified L2 Cache: read requests VFD
Unified L2 Cache: read requests HLSQ
Unified L2 Cache: read requests LRZ
Unified L2 Cache: read requests SP
Unified L2 Cache: write requests LRZ
Unified L2 Cache: write requests SP
Unified L2 Cache: write requests VPC
Unified L2 Cache: write requests VSC
Unified L2 Cache: evicts
Unified L2 Cache: bank req0
Unified L2 Cache: bank req1
Unified L2 Cache: bank req2
Unified L2 Cache: bank req3
Unified L2 Cache: bank req4
Unified L2 Cache: bank req5
Unified L2 Cache: bank req6
Unified L2 Cache: bank req7
Unified L2 Cache: vbif read beats ch0
Unified L2 Cache: vbif read beats ch1
Unified L2 Cache: gmem read beats
Unified L2 Cache: tph ref full
Unified L2 Cache: tph victim full
Unified L2 Cache: tph ext full
Unified L2 Cache: vbif stall write data
Unified L2 Cache: dcmp latency samples
Unified L2 Cache: dcmp latency cycles
Unified L2 Cache: vbif read beats PC
Unified L2 Cache: read requests PC
Unified L2 Cache: ram read req
Unified L2 Cache: ram write req

Texture Processor: busy cycles
Texture Processor: stall cycles UCHE
Texture Processor: latency cycles
Texture Processor: latency trans
Texture Processor: flag cache request samples
Texture Processor: flag cache request latency
Texture Processor: L1 cacheline requests
Texture Processor: L1 cacheline misses
Texture Processor: SP TP trans
Texture Processor: TP SP trans
Texture Processor: output pixels
Texture Processor: filter workload 16bit
Texture Processor: filter workload 32bit
Texture Processor: quads received
Texture Processor: quads offset
Texture Processor: quads shadow
Texture Processor: quads array
Texture Processor: quads gradient
Texture Processor: quads 1D
Texture Processor: quads 2D
Texture Processor: quads buffer
Texture Processor: quads 3D
Texture Processor: quads cube
Texture Processor: divergent quads received
Texture Processor: prt non resident events
Texture Processor: output pixels point
Texture Processor: output pixels bilinear
Texture Processor: output pixels mip
Texture Processor: output pixels aniso
Texture Processor: output pixels zero lod
Texture Processor: flag cache requests
Texture Processor: flag cache misses
Texture Processor: L1 5 L2 requests
Texture Processor: 2D output pixels
Texture Processor: 2D output pixels point
Texture Processor: 2D output pixels bilinear
Texture Processor: 2D filter workload 16bit
Texture Processor: 2D filter workload 32bit
Texture Processor: tpa2tpc trans
Texture Processor: L1 misses astc 1tile
Texture Processor: L1 misses astc 2tile
Texture Processor: L1 misses astc 4tile
Texture Processor: L1 5 L2 compress reqs
Texture Processor: L1 5 L2 compress miss
Texture Processor: L1 bank conflict
Texture Processor: L1 5 miss latency cycles
Texture Processor: L1 5 miss latency trans
Texture Processor: quads constant multiplied
Texture Processor: frontend working cycles
Texture Processor: L1 tag working cycles
Texture Processor: L1 data write working cycles
Texture Processor: pre L1 decom working cycles
Texture Processor: backend working cycles
Texture Processor: flag cache working cycles
Texture Processor: L1 5 cache working cycles
Texture Processor: starve cycles SP
Texture Processor: starve cycles UCHE

Shader/Streaming Processor: busy cycles
Shader/Streaming Processor: ALU working cycles
Shader/Streaming Processor: EFU working cycles
Shader/Streaming Processor: stall cycles VPC
Shader/Streaming Processor: stall cycles TP
Shader/Streaming Processor: stall cycles UCHE
Shader/Streaming Processor: stall cycles RB
Shader/Streaming Processor: non execution cycles
Shader/Streaming Processor: wave contexts
Shader/Streaming Processor: wave context cycles
Shader/Streaming Processor: FS stage wave cycles
Shader/Streaming Processor: FS stage wave samples
Shader/Streaming Processor: VS stage wave cycles
Shader/Streaming Processor: VS stage wave samples
Shader/Streaming Processor: FS stage duration cycles
Shader/Streaming Processor: VS stage duration cycles
Shader/Streaming Processor: wave ctrl cycles
Shader/Streaming Processor: wave load cycles
Shader/Streaming Processor: wave emit cycles
Shader/Streaming Processor: wave nop cycles
Shader/Streaming Processor: wave wait cycles
Shader/Streaming Processor: wave fetch cycles
Shader/Streaming Processor: wave idle cycles
Shader/Streaming Processor: wave end cycles
Shader/Streaming Processor: wave long sync cycles
Shader/Streaming Processor: wave short sync cycles
Shader/Streaming Processor: wave join cycles
Shader/Streaming Processor: LM load instructions
Shader/Streaming Processor: LM store instructions
Shader/Streaming Processor: LM atomics
Shader/Streaming Processor: GM load instructions
Shader/Streaming Processor: GM store instructions
Shader/Streaming Processor: GM atomics
Shader/Streaming Processor: VS stage tex instructions
Shader/Streaming Processor: VS stage EFU instructions
Shader/Streaming Processor: VS stage full ALU instructions
Shader/Streaming Processor: VS stage half ALU instructions
Shader/Streaming Processor: FS stage tex instructions
Shader/Streaming Processor: FS stage cflow instructions
Shader/Streaming Processor: FS stage EFU instructions
Shader/Streaming Processor: FS stage full ALU instructions
Shader/Streaming Processor: FS stage half ALU instructions
Shader/Streaming Processor: FS stage bary instructions
Shader/Streaming Processor: VS instructions
Shader/Streaming Processor: FS instructions
Shader/Streaming Processor: addr lock count
Shader/Streaming Processor: UCHE read trans
Shader/Streaming Processor: UCHE write trans
Shader/Streaming Processor: export VPC trans
Shader/Streaming Processor: export RB trans
Shader/Streaming Processor: pixels killed
Shader/Streaming Processor: icl1 requests
Shader/Streaming Processor: icl1 misses
Shader/Streaming Processor: HS instructions
Shader/Streaming Processor: DS instructions
Shader/Streaming Processor: GS instructions
Shader/Streaming Processor: CS instructions
Shader/Streaming Processor: GPR read
Shader/Streaming Processor: GPR write
Shader/Streaming Processor: FS stage half EFU instructions
Shader/Streaming Processor: VS stage half EFU instructions
Shader/Streaming Processor: LM bank conflicts
Shader/Streaming Processor: tex control working cycles
Shader/Streaming Processor: load control working cycles
Shader/Streaming Processor: flow control working cycles
Shader/Streaming Processor: LM working cycles
Shader/Streaming Processor: dispatcher working cycles
Shader/Streaming Processor: sequencer working cycles
Shader/Streaming Processor: low efficiency starved BY TP
Shader/Streaming Processor: starve cycles HLSQ
Shader/Streaming Processor: non execution LS cycles
Shader/Streaming Processor: working EU
Shader/Streaming Processor: any EU working
Shader/Streaming Processor: working EU FS stage
Shader/Streaming Processor: any EU working FS stage
Shader/Streaming Processor: working EU VS stage
Shader/Streaming Processor: any EU working VS stage
Shader/Streaming Processor: working EU CS stage
Shader/Streaming Processor: any EU working CS stage
Shader/Streaming Processor: GPR read prefetch
Shader/Streaming Processor: GPR read conflict
Shader/Streaming Processor: GPR write conflict
Shader/Streaming Processor: GM load latency cycles
Shader/Streaming Processor: GM load latency samples
Shader/Streaming Processor: executable waves

RB: busy cycles
RB: stall cycles HLSQ
RB: stall cycles fifo0 full
RB: stall cycles fifo1 full
RB: stall cycles fifo2 full
RB: starve cycles SP
RB: starve cycles LRZ tile
RB: starve cycles CCU
RB: starve cycles Z plane
RB: starve cycles bary plane
RB: Z workload
RB: HLSQ active
RB: Z read
RB: Z write
RB: C read
RB: C write
RB: total pass
RB: Z pass
RB: Z fail
RB: S fail
RB: blended fxp components
RB: blended fp16 components
RB: PS invocations
RB: 2D alive cycles
RB: 2D stall cycles a2d
RB: 2D starve cycles src
RB: 2D starve cycles SP
RB: 2D starve cycles dst
RB: 2D valid pixels
RB: 3D pixels
RB: blender working cycles
RB: zproc working cycles
RB: cproc working cycles
RB: sampler working cycles
RB: stall cycles CCU color read
RB: stall cycles CCU color write
RB: stall cycles CCU depth read
RB: stall cycles CCU depth write
RB: stall cycles VPC
RB: 2D input trans
RB: 2D output RB dst trans
RB: 2D output RB src trans
RB: blended fp32 components
RB: color pix tiles
RB: stall cycles CCU
RB: early Z arb3 grant
RB: late Z arb3 grant
RB: early Z skip grant

VSC: busy cycles
VSC: working cycles
VSC: stall cycles UCHE
VSC: eot num
VSC: input tiles

Cache and Compression Unit: busy cycles
Cache and Compression Unit: stall cycles RB depth return
Cache and Compression Unit: stall cycles RB color return
Cache and Compression Unit: starve cycles flag return
Cache and Compression Unit: depth blocks
Cache and Compression Unit: color blocks
Cache and Compression Unit: depth block hit
Cache and Compression Unit: color block hit
Cache and Compression Unit: partial block read
Cache and Compression Unit: gmem read
Cache and Compression Unit: gmem write
Cache and Compression Unit: depth read flag0 count
Cache and Compression Unit: depth read flag1 count
Cache and Compression Unit: depth read flag2 count
Cache and Compression Unit: depth read flag3 count
Cache and Compression Unit: depth read flag4 count
Cache and Compression Unit: depth read flag5 count
Cache and Compression Unit: depth read flag6 count
Cache and Compression Unit: depth read flag8 count
Cache and Compression Unit: color read flag0 count
Cache and Compression Unit: color read flag1 count
Cache and Compression Unit: color read flag2 count
Cache and Compression Unit: color read flag3 count
Cache and Compression Unit: color read flag4 count
Cache and Compression Unit: color read flag5 count
Cache and Compression Unit: color read flag6 count
Cache and Compression Unit: color read flag8 count
Cache and Compression Unit: 2D RD req
Cache and Compression Unit: 2D WR req

Low Resolution Z: busy cycles
Low Resolution Z: starve cycles RAS
Low Resolution Z: stall cycles RB
Low Resolution Z: stall cycles VSC
Low Resolution Z: stall cycles VPC
Low Resolution Z: stall cycles flag prefetch
Low Resolution Z: stall cycles UCHE
Low Resolution Z: LRZ read
Low Resolution Z: LRZ write
Low Resolution Z: read latency
Low Resolution Z: merge cache updating
Low Resolution Z: prim killed BY maskgen
Low Resolution Z: prim killed BY LRZ
Low Resolution Z: visible prim after LRZ
Low Resolution Z: full 8x8 tiles
Low Resolution Z: partial 8x8 tiles
Low Resolution Z: tile killed
Low Resolution Z: total pixel
Low Resolution Z: visible pixel after LRZ
Low Resolution Z: fully covered tiles
Low Resolution Z: partial covered tiles
Low Resolution Z: feedback accept
Low Resolution Z: feedback discard
Low Resolution Z: feedback stall
Low Resolution Z: stall cycles RB zplane
Low Resolution Z: stall cycles RB bplane
Low Resolution Z: stall cycles VC
Low Resolution Z: RAS mask trans

CMP: cmpdecmp stall cycles arb
CMP: cmpdecmp vbif latency cycles
CMP: cmpdecmp vbif latency samples
CMP: cmpdecmp vbif read data CCU
CMP: cmpdecmp vbif write data CCU
CMP: cmpdecmp vbif read request
CMP: cmpdecmp vbif write request
CMP: cmpdecmp vbif read data
CMP: cmpdecmp vbif write data
CMP: cmpdecmp flag fetch cycles
CMP: cmpdecmp flag fetch samples
CMP: cmpdecmp depth write flag1 count
CMP: cmpdecmp depth write flag2 count
CMP: cmpdecmp depth write flag3 count
CMP: cmpdecmp depth write flag4 count
CMP: cmpdecmp depth write flag5 count
CMP: cmpdecmp depth write flag6 count
CMP: cmpdecmp depth write flag8 count
CMP: cmpdecmp color write flag1 count
CMP: cmpdecmp color write flag2 count
CMP: cmpdecmp color write flag3 count
CMP: cmpdecmp color write flag4 count
CMP: cmpdecmp color write flag5 count
CMP: cmpdecmp color write flag6 count
CMP: cmpdecmp color write flag8 count
CMP: cmpdecmp 2D stall cycles vbif req
CMP: cmpdecmp 2D stall cycles vbif WR
CMP: cmpdecmp 2D stall cycles vbif return
CMP: cmpdecmp 2D RD data
CMP: cmpdecmp 2D WR data
CMP: cmpdecmp vbif read data UCHE ch0
CMP: cmpdecmp vbif read data UCHE ch1
CMP: cmpdecmp 2D output trans
CMP: cmpdecmp vbif write data UCHE
CMP: cmpdecmp depth write flag0 count
CMP: cmpdecmp color write flag0 count
CMP: cmpdecmp color write flagalpha count
CMP: cmpdecmp 2D busy cycles
CMP: cmpdecmp 2D reorder starve cycles
CMP: cmpdecmp 2D pixels
```
</details>


### Adreno 660

<details>

| group, counter | name | desc |
|---|---|---|
| - | **Command Parser** | - |
| 0, 0 | always count |
| 0, 1 | busy gfx core idle |
| 0, 2 | busy cycles |
| 0, 3 | num preemptions |
| 0, 4 | preemption reaction delay |
| 0, 5 | preemption switch out time |
| 0, 6 | preemption switch IN time |
| 0, 7 | dead draws IN bin render |
| 0, 8 | predicated draws killed |
| 0, 9 | mode switch |
| 0, 10 | zpass done |
| 0, 11 | context done |
| 0, 12 | cache flush |
| 0, 13 | long preemptions |
| 0, 14 | sqe I cache starve |
| 0, 15 | sqe idle |
| 0, 16 | sqe pm4 starve RB IB |
| 0, 17 | sqe pm4 starve sds |
| 0, 18 | sqe mrb starve |
| 0, 19 | sqe rrb starve |
| 0, 20 | sqe vsd starve |
| 0, 21 | vsd decode starve |
| 0, 22 | sqe pipe out stall |
| 0, 23 | sqe sync stall |
| 0, 24 | sqe pm4 wfi stall |
| 0, 25 | sqe sys wfi stall |
| 0, 26 | sqe T4 exec |
| 0, 27 | sqe load state exec |
| 0, 28 | sqe save sds state |
| 0, 29 | sqe draw exec |
| 0, 30 | sqe ctxt reg bunch exec |
| 0, 31 | sqe exec profiled |
| 0, 32 | memory pool empty |
| 0, 33 | memory pool sync stall |
| 0, 34 | memory pool above thresh |
| 0, 35 | ahb WR stall pre draws |
| 0, 36 | ahb stall sqe gmu |
| 0, 37 | ahb stall sqe WR other |
| 0, 38 | ahb stall sqe RD other |
| 0, 39 | cluster0 empty |
| 0, 40 | cluster1 empty |
| 0, 41 | cluster2 empty |
| 0, 42 | cluster3 empty |
| 0, 43 | cluster4 empty |
| 0, 44 | cluster5 empty |
| 0, 45 | pm4 data |
| 0, 46 | pm4 headers |
| 0, 47 | vbif read beats |
| 0, 48 | vbif write beats |
| 0, 49 | sqe instr counter |
| - | **RBBM** | - |
| 1, 0 | always count |
| 1, 1 | always ON |
| 1, 2 | TSE busy |
| 1, 3 | RAS busy |
| 1, 4 | PC dcall busy |
| 1, 5 | PC vsd busy |
| 1, 6 | status masked |
| 1, 7 | com busy |
| 1, 8 | dcom busy |
| 1, 9 | vbif busy |
| 1, 10 | VSC busy |
| 1, 11 | tess busy |
| 1, 12 | UCHE busy |
| 1, 13 | HLSQ busy |
| - | **PC** | - |
| 2, 0 | busy cycles |
| 2, 1 | working cycles |
| 2, 2 | stall cycles VFD |
| 2, 3 | stall cycles TSE |
| 2, 4 | stall cycles VPC |
| 2, 5 | stall cycles UCHE |
| 2, 6 | stall cycles tess |
| 2, 7 | stall cycles TSE only |
| 2, 8 | stall cycles VPC only |
| 2, 9 | pass1 TF stall cycles |
| 2, 10 | starve cycles for index |
| 2, 11 | starve cycles for tess factor |
| 2, 12 | starve cycles for viz stream |
| 2, 13 | starve cycles for position |
| 2, 14 | starve cycles DI |
| 2, 15 | vis streams loaded |
| 2, 16 | instances |
| 2, 17 | VPC primitives |
| 2, 18 | dead prim |
| 2, 19 | live prim |
| 2, 20 | vertex hits |
| 2, 21 | IA vertices |
| 2, 22 | IA primitives |
| 2, 23 | GS primitives |
| 2, 24 | HS invocations |
| 2, 25 | DS invocations |
| 2, 26 | VS invocations |
| 2, 27 | GS invocations |
| 2, 28 | DS primitives |
| 2, 29 | VPC pos data transaction |
| 2, 30 | 3D drawcalls |
| 2, 31 | 2D drawcalls |
| 2, 32 | non drawcall global events |
| 2, 33 | tess busy cycles |
| 2, 34 | tess working cycles |
| 2, 35 | tess stall cycles PC |
| 2, 36 | tess starve cycles PC |
| 2, 37 | TSE transaction |
| 2, 38 | TSE vertex |
| 2, 39 | tess PC UV trans |
| 2, 40 | tess PC UV patches |
| 2, 41 | tess factor trans |
| - | **Vertex Fetch and Decode** | - |
| 3, 0 | busy cycles |
| 3, 1 | stall cycles UCHE |
| 3, 2 | stall cycles VPC alloc |
| 3, 3 | stall cycles SP info |
| 3, 4 | stall cycles SP attr |
| 3, 5 | starve cycles UCHE |
| 3, 6 | rbuffer full |
| 3, 7 | attr info fifo full |
| 3, 8 | decoded attribute bytes |
| 3, 9 | num attributes |
| 3, 10 | upper shader fibers |
| 3, 11 | lower shader fibers |
| 3, 12 | mode 0 fibers |
| 3, 13 | mode 1 fibers |
| 3, 14 | mode 2 fibers |
| 3, 15 | mode 3 fibers |
| 3, 16 | mode 4 fibers |
| 3, 17 | total vertices |
| 3, 18 | vfdp stall cycles VFD |
| 3, 19 | vfdp stall cycles VFD index |
| 3, 20 | vfdp stall cycles VFD prog |
| 3, 21 | vfdp starve cycles PC |
| 3, 22 | vfdp VS stage waves |
| - | **High Level SeQuencer** | - |
| 4, 0 | busy cycles |
| 4, 1 | stall cycles UCHE |
| 4, 2 | stall cycles SP state |
| 4, 3 | stall cycles SP FS stage |
| 4, 4 | UCHE latency cycles |
| 4, 5 | UCHE latency count |
| 4, 6 | FS stage 1X waves |
| 4, 7 | FS stage 2X waves |
| 4, 8 | quads |
| 4, 9 | CS invocations |
| 4, 10 | compute drawcalls |
| 4, 11 | FS data wait programming |
| 4, 12 | dual FS prog active |
| 4, 13 | dual VS prog active |
| 4, 14 | FS batch count zero |
| 4, 15 | VS batch count zero |
| 4, 16 | wave pending NO quad |
| 4, 17 | wave pending NO prim base |
| 4, 18 | stall cycles VPC |
| 4, 19 | pixels |
| 4, 20 | draw mode switch vsfs sync |
| - | **Varying/Position Cache** | - |
| 5, 0 | busy cycles |
| 5, 1 | working cycles |
| 5, 2 | stall cycles UCHE |
| 5, 3 | stall cycles VFD wack |
| 5, 4 | stall cycles HLSQ prim alloc |
| 5, 5 | stall cycles PC |
| 5, 6 | stall cycles SP LM |
| 5, 7 | starve cycles SP |
| 5, 8 | starve cycles LRZ |
| 5, 9 | PC primitives |
| 5, 10 | SP components |
| 5, 11 | stall cycles vpcram pos |
| 5, 12 | LRZ assign primitives |
| 5, 13 | RB visible primitives |
| 5, 14 | LM transaction |
| 5, 15 | streamout transaction |
| 5, 16 | VS busy cycles |
| 5, 17 | PS busy cycles |
| 5, 18 | VS working cycles |
| 5, 19 | PS working cycles |
| 5, 20 | starve cycles RB |
| 5, 21 | num vpcram read pos |
| 5, 22 | wit full cycles |
| 5, 23 | vpcram full cycles |
| 5, 24 | LM full wait for intp end |
| 5, 25 | num vpcram write |
| 5, 26 | num vpcram read SO |
| 5, 27 | num attr req LM |
| - | **Triangle Setup Engine** | - |
| 6, 0 | busy cycles |
| 6, 1 | clipping cycles |
| 6, 2 | stall cycles RAS |
| 6, 3 | stall cycles LRZ baryplane |
| 6, 4 | stall cycles LRZ zplane |
| 6, 5 | starve cycles PC |
| 6, 6 | input prim |
| 6, 7 | input null prim |
| 6, 8 | trival rej prim |
| 6, 9 | clipped prim |
| 6, 10 | zero area prim |
| 6, 11 | faceness culled prim |
| 6, 12 | zero pixel prim |
| 6, 13 | output null prim |
| 6, 14 | output visible prim |
| 6, 15 | cinvocation |
| 6, 16 | cprimitives |
| 6, 17 | 2D input prim |
| 6, 18 | 2D alive cycles |
| 6, 19 | clip planes |
| - | **Rasterizer** | - |
| 7, 0 | busy cycles |
| 7, 1 | supertile active cycles |
| 7, 2 | stall cycles LRZ |
| 7, 3 | starve cycles TSE |
| 7, 4 | super tiles |
| 7, 5 | 8x4 tiles |
| 7, 6 | maskgen active |
| 7, 7 | fully covered super tiles |
| 7, 8 | fully covered 8x4 tiles |
| 7, 9 | prim killed invisible |
| 7, 10 | supertile gen active cycles |
| 7, 11 | LRZ intf working cycles |
| 7, 12 | blocks |
| - | **Unified L2 Cache** | - |
| 8, 0 | busy cycles |
| 8, 1 | stall cycles arbiter |
| 8, 2 | vbif latency cycles |
| 8, 3 | vbif latency samples |
| 8, 4 | vbif read beats TP |
| 8, 5 | vbif read beats VFD |
| 8, 6 | vbif read beats HLSQ |
| 8, 7 | vbif read beats LRZ |
| 8, 8 | vbif read beats SP |
| 8, 9 | read requests TP |
| 8, 10 | read requests VFD |
| 8, 11 | read requests HLSQ |
| 8, 12 | read requests LRZ |
| 8, 13 | read requests SP |
| 8, 14 | write requests LRZ |
| 8, 15 | write requests SP |
| 8, 16 | write requests VPC |
| 8, 17 | write requests VSC |
| 8, 18 | evicts |
| 8, 19 | bank req0 |
| 8, 20 | bank req1 |
| 8, 21 | bank req2 |
| 8, 22 | bank req3 |
| 8, 23 | bank req4 |
| 8, 24 | bank req5 |
| 8, 25 | bank req6 |
| 8, 26 | bank req7 |
| 8, 27 | vbif read beats ch0 |
| 8, 28 | vbif read beats ch1 |
| 8, 29 | gmem read beats |
| 8, 30 | tph ref full |
| 8, 31 | tph victim full |
| 8, 32 | tph ext full |
| 8, 33 | vbif stall write data |
| 8, 34 | dcmp latency samples |
| 8, 35 | dcmp latency cycles |
| 8, 36 | vbif read beats PC |
| 8, 37 | read requests PC |
| 8, 38 | ram read req |
| 8, 39 | ram write req |
| - | **Texture Processor** | - |
| 9, 0 | busy cycles |
| 9, 1 | stall cycles UCHE |
| 9, 2 | latency cycles |
| 9, 3 | latency trans |
| 9, 4 | flag cache request samples |
| 9, 5 | flag cache request latency |
| 9, 6 | L1 cacheline requests |
| 9, 7 | L1 cacheline misses |
| 9, 8 | SP TP trans |
| 9, 9 | TP SP trans |
| 9, 10 | output pixels |
| 9, 11 | filter workload 16bit |
| 9, 12 | filter workload 32bit |
| 9, 13 | quads received |
| 9, 14 | quads offset |
| 9, 15 | quads shadow |
| 9, 16 | quads array |
| 9, 17 | quads gradient |
| 9, 18 | quads 1D |
| 9, 19 | quads 2D |
| 9, 20 | quads buffer |
| 9, 21 | quads 3D |
| 9, 22 | quads cube |
| 9, 23 | divergent quads received |
| 9, 24 | prt non resident events |
| 9, 25 | output pixels point |
| 9, 26 | output pixels bilinear |
| 9, 27 | output pixels mip |
| 9, 28 | output pixels aniso |
| 9, 29 | output pixels zero lod |
| 9, 30 | flag cache requests |
| 9, 31 | flag cache misses |
| 9, 32 | L1 5 L2 requests |
| 9, 33 | 2D output pixels |
| 9, 34 | 2D output pixels point |
| 9, 35 | 2D output pixels bilinear |
| 9, 36 | 2D filter workload 16bit |
| 9, 37 | 2D filter workload 32bit |
| 9, 38 | tpa2tpc trans |
| 9, 39 | L1 misses astc 1tile |
| 9, 40 | L1 misses astc 2tile |
| 9, 41 | L1 misses astc 4tile |
| 9, 42 | L1 5 L2 compress reqs |
| 9, 43 | L1 5 L2 compress miss |
| 9, 44 | L1 bank conflict |
| 9, 45 | L1 5 miss latency cycles |
| 9, 46 | L1 5 miss latency trans |
| 9, 47 | quads constant multiplied |
| 9, 48 | frontend working cycles |
| 9, 49 | L1 tag working cycles |
| 9, 50 | L1 data write working cycles |
| 9, 51 | pre L1 decom working cycles |
| 9, 52 | backend working cycles |
| 9, 53 | flag cache working cycles |
| 9, 54 | L1 5 cache working cycles |
| 9, 55 | starve cycles SP |
| 9, 56 | starve cycles UCHE |
| - | **Shader/Streaming Processor** | - |
| 10, 0 | busy cycles |
| 10, 1 | ALU working cycles |
| 10, 2 | EFU working cycles |
| 10, 3 | stall cycles VPC |
| 10, 4 | stall cycles TP |
| 10, 5 | stall cycles UCHE |
| 10, 6 | stall cycles RB |
| 10, 7 | non execution cycles |
| 10, 8 | wave contexts |
| 10, 9 | wave context cycles |
| 10, 10 | FS stage wave cycles |
| 10, 11 | FS stage wave samples |
| 10, 12 | VS stage wave cycles |
| 10, 13 | VS stage wave samples |
| 10, 14 | FS stage duration cycles |
| 10, 15 | VS stage duration cycles |
| 10, 16 | wave ctrl cycles |
| 10, 17 | wave load cycles |
| 10, 18 | wave emit cycles |
| 10, 19 | wave nop cycles |
| 10, 20 | wave wait cycles |
| 10, 21 | wave fetch cycles |
| 10, 22 | wave idle cycles |
| 10, 23 | wave end cycles |
| 10, 24 | wave long sync cycles |
| 10, 25 | wave short sync cycles |
| 10, 26 | wave join cycles |
| 10, 27 | LM load instructions |
| 10, 28 | LM store instructions |
| 10, 29 | LM atomics |
| 10, 30 | GM load instructions |
| 10, 31 | GM store instructions |
| 10, 32 | GM atomics |
| 10, 33 | VS stage tex instructions |
| 10, 34 | VS stage EFU instructions |
| 10, 35 | VS stage full ALU instructions |
| 10, 36 | VS stage half ALU instructions |
| 10, 37 | FS stage tex instructions |
| 10, 38 | FS stage cflow instructions |
| 10, 39 | FS stage EFU instructions |
| 10, 40 | FS stage full ALU instructions |
| 10, 41 | FS stage half ALU instructions |
| 10, 42 | FS stage bary instructions |
| 10, 43 | VS instructions |
| 10, 44 | FS instructions |
| 10, 45 | addr lock count |
| 10, 46 | UCHE read trans |
| 10, 47 | UCHE write trans |
| 10, 48 | export VPC trans |
| 10, 49 | export RB trans |
| 10, 50 | pixels killed |
| 10, 51 | icl1 requests |
| 10, 52 | icl1 misses |
| 10, 53 | HS instructions |
| 10, 54 | DS instructions |
| 10, 55 | GS instructions |
| 10, 56 | CS instructions |
| 10, 57 | GPR read |
| 10, 58 | GPR write |
| 10, 59 | FS stage half EFU instructions |
| 10, 60 | VS stage half EFU instructions |
| 10, 61 | LM bank conflicts |
| 10, 62 | tex control working cycles |
| 10, 63 | load control working cycles |
| 10, 64 | flow control working cycles |
| 10, 65 | LM working cycles |
| 10, 66 | dispatcher working cycles |
| 10, 67 | sequencer working cycles |
| 10, 68 | low efficiency starved BY TP |
| 10, 69 | starve cycles HLSQ |
| 10, 70 | non execution LS cycles |
| 10, 71 | working EU |
| 10, 72 | any EU working |
| 10, 73 | working EU FS stage |
| 10, 74 | any EU working FS stage |
| 10, 75 | working EU VS stage |
| 10, 76 | any EU working VS stage |
| 10, 77 | working EU CS stage |
| 10, 78 | any EU working CS stage |
| 10, 79 | GPR read prefetch |
| 10, 80 | GPR read conflict |
| 10, 81 | GPR write conflict |
| 10, 82 | GM load latency cycles |
| 10, 83 | GM load latency samples |
| 10, 84 | executable waves |
| - | **Render backend** | - |
| 11, 0 | busy cycles |
| 11, 1 | stall cycles HLSQ |
| 11, 2 | stall cycles fifo0 full |
| 11, 3 | stall cycles fifo1 full |
| 11, 4 | stall cycles fifo2 full |
| 11, 5 | starve cycles SP |
| 11, 6 | starve cycles LRZ tile |
| 11, 7 | starve cycles CCU |
| 11, 8 | starve cycles Z plane |
| 11, 9 | starve cycles bary plane |
| 11, 10 | Z workload |
| 11, 11 | HLSQ active |
| 11, 12 | Z read |
| 11, 13 | Z write |
| 11, 14 | C read |
| 11, 15 | C write |
| 11, 16 | total pass |
| 11, 17 | Z pass |
| 11, 18 | Z fail |
| 11, 19 | S fail |
| 11, 20 | blended fxp components |
| 11, 21 | blended fp16 components |
| 11, 22 | PS invocations |
| 11, 23 | 2D alive cycles |
| 11, 24 | 2D stall cycles a2d |
| 11, 25 | 2D starve cycles src |
| 11, 26 | 2D starve cycles SP |
| 11, 27 | 2D starve cycles dst |
| 11, 28 | 2D valid pixels |
| 11, 29 | 3D pixels |
| 11, 30 | blender working cycles |
| 11, 31 | zproc working cycles |
| 11, 32 | cproc working cycles |
| 11, 33 | sampler working cycles |
| 11, 34 | stall cycles CCU color read |
| 11, 35 | stall cycles CCU color write |
| 11, 36 | stall cycles CCU depth read |
| 11, 37 | stall cycles CCU depth write |
| 11, 38 | stall cycles VPC |
| 11, 39 | 2D input trans |
| 11, 40 | 2D output RB dst trans |
| 11, 41 | 2D output RB src trans |
| 11, 42 | blended fp32 components |
| 11, 43 | color pix tiles |
| 11, 44 | stall cycles CCU |
| 11, 45 | early Z arb3 grant |
| 11, 46 | late Z arb3 grant |
| 11, 47 | early Z skip grant |
| - | **VBIF** | - |
| 13, 34 | ??? |
| 13, 35 | ??? |
| 13, 46 | ??? |
| 13, 47 | ??? |
| - | **Visibility Stream Compressor** | - |
| 23, 0 | busy cycles |
| 23, 1 | working cycles |
| 23, 2 | stall cycles UCHE |
| 23, 3 | eot num |
| 23, 4 | input tiles |
| - | **Cache and Compression Unit** | - |
| 24, 0 | busy cycles |
| 24, 1 | stall cycles RB depth return |
| 24, 2 | stall cycles RB color return |
| 24, 3 | starve cycles flag return |
| 24, 4 | depth blocks |
| 24, 5 | color blocks |
| 24, 6 | depth block hit |
| 24, 7 | color block hit |
| 24, 8 | partial block read |
| 24, 9 | gmem read |
| 24, 10 | gmem write |
| 24, 11 | depth read flag0 count |
| 24, 12 | depth read flag1 count |
| 24, 13 | depth read flag2 count |
| 24, 14 | depth read flag3 count |
| 24, 15 | depth read flag4 count |
| 24, 16 | depth read flag5 count |
| 24, 17 | depth read flag6 count |
| 24, 18 | depth read flag8 count |
| 24, 19 | color read flag0 count |
| 24, 20 | color read flag1 count |
| 24, 21 | color read flag2 count |
| 24, 22 | color read flag3 count |
| 24, 23 | color read flag4 count |
| 24, 24 | color read flag5 count |
| 24, 25 | color read flag6 count |
| 24, 26 | color read flag8 count |
| 24, 27 | 2D RD req |
| 24, 28 | 2D WR req |
| - | **Low Resolution Z pass** | - |
| 25, 0 | busy cycles |
| 25, 1 | starve cycles RAS |
| 25, 2 | stall cycles RB |
| 25, 3 | stall cycles VSC |
| 25, 4 | stall cycles VPC |
| 25, 5 | stall cycles flag prefetch |
| 25, 6 | stall cycles UCHE |
| 25, 7 | LRZ read |
| 25, 8 | LRZ write |
| 25, 9 | read latency |
| 25, 10 | merge cache updating |
| 25, 11 | prim killed BY maskgen |
| 25, 12 | prim killed BY LRZ |
| 25, 13 | visible prim after LRZ |
| 25, 14 | full 8x8 tiles |
| 25, 15 | partial 8x8 tiles |
| 25, 16 | tile killed |
| 25, 17 | total pixel |
| 25, 18 | visible pixel after LRZ |
| 25, 19 | fully covered tiles |
| 25, 20 | partial covered tiles |
| 25, 21 | feedback accept |
| 25, 22 | feedback discard |
| 25, 23 | feedback stall |
| 25, 24 | stall cycles RB zplane |
| 25, 25 | stall cycles RB bplane |
| 25, 26 | stall cycles VC |
| 25, 27 | RAS mask trans |
| - | **CMP** | - |
| 26, 0 | cmpdecmp stall cycles arb |
| 26, 1 | cmpdecmp vbif latency cycles |
| 26, 2 | cmpdecmp vbif latency samples |
| 26, 3 | cmpdecmp vbif read data CCU |
| 26, 4 | cmpdecmp vbif write data CCU |
| 26, 5 | cmpdecmp vbif read request |
| 26, 6 | cmpdecmp vbif write request |
| 26, 7 | cmpdecmp vbif read data |
| 26, 8 | cmpdecmp vbif write data |
| 26, 9 | cmpdecmp flag fetch cycles |
| 26, 10 | cmpdecmp flag fetch samples |
| 26, 11 | cmpdecmp depth write flag1 count |
| 26, 12 | cmpdecmp depth write flag2 count |
| 26, 13 | cmpdecmp depth write flag3 count |
| 26, 14 | cmpdecmp depth write flag4 count |
| 26, 15 | cmpdecmp depth write flag5 count |
| 26, 16 | cmpdecmp depth write flag6 count |
| 26, 17 | cmpdecmp depth write flag8 count |
| 26, 18 | cmpdecmp color write flag1 count |
| 26, 19 | cmpdecmp color write flag2 count |
| 26, 20 | cmpdecmp color write flag3 count |
| 26, 21 | cmpdecmp color write flag4 count |
| 26, 22 | cmpdecmp color write flag5 count |
| 26, 23 | cmpdecmp color write flag6 count |
| 26, 24 | cmpdecmp color write flag8 count |
| 26, 25 | cmpdecmp 2D stall cycles vbif req |
| 26, 26 | cmpdecmp 2D stall cycles vbif WR |
| 26, 27 | cmpdecmp 2D stall cycles vbif return |
| 26, 28 | cmpdecmp 2D RD data |
| 26, 29 | cmpdecmp 2D WR data |
| 26, 30 | cmpdecmp vbif read data UCHE ch0 |
| 26, 31 | cmpdecmp vbif read data UCHE ch1 |
| 26, 32 | cmpdecmp 2D output trans |
| 26, 33 | cmpdecmp vbif write data UCHE |
| 26, 34 | cmpdecmp depth write flag0 count |
| 26, 35 | cmpdecmp color write flag0 count |
| 26, 36 | cmpdecmp color write flagalpha count |
| 26, 37 | cmpdecmp 2D busy cycles |
| 26, 38 | cmpdecmp 2D reorder starve cycles |
| 26, 39 | cmpdecmp 2D pixels |

</details>
