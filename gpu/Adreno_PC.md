**Qualcomm Adreno Performance Counters**

## References

* [A5xx enums](https://github.com/freedreno/envytools/blob/master/registers/adreno/a5xx.xml) - `a5xx_***_perfcounter_select` - counter id
* [A6xx enums](https://github.com/freedreno/envytools/blob/master/registers/adreno/a6xx.xml) - `a6xx_***_perfcounter_select` - counter id
* [HardwarePerfCounter](https://github.com/google/hardware-perfcounter/) - to get access to the performance counters.
* [Mesa driver details](https://docs.mesa3d.org/drivers/freedreno.html)
* [Freedreno wiki](https://github.com/freedreno/freedreno/wiki)
* [A6xx SP](https://gitlab.freedesktop.org/freedreno/freedreno/-/wikis/A6xx-SP)
* [Android/Linux GPU Drivers: Internals and Resources](https://www.lei.chat/posts/android-linux-gpu-drivers-internals-and-resources/)
* [Kernel code for Samsung Galaxy S21 (Snapdragon 888)](https://github.com/antiagainst/SM-G991U/tree/main/drivers/gpu/msm), [msm in linux](https://github.com/torvalds/linux/tree/master/drivers/gpu/drm/msm)


## Notes

**Cluster** - A group of hardware registers, often with multiple copies to allow pipelining. There is an M:N relationship between hardware blocks that do work and the clusters of registers for the state that hardware blocks use.<br/>
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
**ME** - Microcode Engine, handles most **PM4** commands. Adreno 2xx-4xx CP component.<br/>
**maskgen** - ?<br/>
**PC** - ?<br/>
**PFP** - Prefetch Parser. Adreno 2xx-4xx CP component.<br/>
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
**IOMMU** - Memory management unit.<br/>

### Timings

Vulkan adds implicit barriers when used timestamps, it prevent commands to overlap and can not be used to measure small tasks. Only large passes or group of passes can execute without influence of time measurements.

### Access to performance counters

Warning: some devices requires root to access performance counters.<br/>
Other devices requires to enable performance counters from adb, which may requires root: [ref](https://github.com/google/agi/issues/1113#issuecomment-1165786744)
```sh
adb shell "echo 1 > /sys/class/kgsl/kgsl-3d0/perfcounter"
```

| Device | Adreno GPU | without root | reference |
|---|---|---|---|
| Redmi 7A                      | 505 | yes | [[az](https://github.com/azhirnov)] |
| Motorola Defy                 | 610 | yes | [[az](https://github.com/azhirnov)] |
| Asus ROG Phone 3              | 650 | **no** | [ref](https://github.com/google/agi/issues/1343) |
| Asus ROG Phone 5              | 660 | **no** | [[az](https://github.com/azhirnov)] |
| Asus ROG Phone 6              | 730 | **no** | [ref](https://github.com/google/agi/issues/1113#issuecomment-1228880530) |
| Asus Zenfone 9                | 730 | **no** | [ref](https://github.com/google/agi/issues/1113#issuecomment-1228880530) |
| OnePlus 7 Pro                 | 640 | yes (?) | [ref](https://chipsandcheese.com/2024/05/01/inside-the-snapdragon-855s-igpu/) |
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
| Galaxy Tab S9                 | 740 | ?  | [ref](https://github.com/google/agi/issues/1403) |
| samsung SM-X710               | 740 | ?  | [ref](https://github.com/google/agi/issues/1402) |
| Quest 3                       | 740 | no | ? |
| Pcio 4 Ultra                  | 740 | no | ? |


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

*description from LLM*
| group, counter | name | desc |
|---|---|---|
| - | **Command Parser** | - |
| 0, 0 | always count | Reference counter: total measured cycles for this group (denominator for utilization). |
| 0, 1 | busy gfx core idle | Cycles where command front-end considers “graphics busy” while the rest of the core is idle (front-end active / backend idle symptom). |
| 0, 2 | busy cycles | Cycles where the GPU is busy executing work (typical utilization numerator). |
| 0, 3 | pfp idle | Cycles the **PFP** (prefetch parser) is idle (no work). |
| 0, 4 | pfp busy working | Cycles the PFP is actively parsing / prefetching commands. |
| 0, 5 | pfp stall cycles any | Cycles the PFP is stalled for any reason (backpressure, waits, etc.). |
| 0, 6 | pfp starve cycles any | Cycles the PFP is starved (has nothing to do / waiting for input work to arrive). |
| 0, 7 | pfp icache miss | PFP instruction-cache misses (event count). |
| 0, 8 | pfp icache hit | PFP instruction-cache hits (event count). |
| 0, 9 | pfp match pm4 pkt profile | Count of PM4 packets matching a “profiled” type/class (packet classification counter). |
| 0, 10 | ME busy working | Cycles the **ME** (microcode engine) is executing/dispatching commands. |
| 0, 11 | ME idle | Cycles the ME is idle. |
| 0, 12 | ME starve cycles any | Cycles the ME is starved (no commands available from upstream). |
| 0, 13 | ME fifo empty pfp idle | Cycles ME FIFO is empty while PFP is idle (no work generated). |
| 0, 14 | ME fifo empty pfp busy | Cycles ME FIFO is empty while PFP is busy (PFP not producing ME-ready work yet / bubbles). |
| 0, 15 | ME fifo full ME busy | Cycles ME FIFO is full while ME is busy (dispatch queue full under load). |
| 0, 16 | ME fifo full ME non working | Cycles ME FIFO is full while ME is not working (blocked condition/backpressure). |
| 0, 17 | ME stall cycles any | Cycles ME is stalled for any reason (waiting on resources/sync). |
| 0, 18 | ME icache miss | ME instruction-cache misses (event count). |
| 0, 19 | ME icache hit | ME instruction-cache hits (event count). |
| 0, 20 | num preemptions | Number of GPU preemption events. |
| 0, 21 | preemption reaction delay | Cycles from preemption request to acknowledged/serviced (latency). |
| 0, 22 | preemption switch out time | Cycles to save/switch-out current context. |
| 0, 23 | preemption switch IN time | Cycles to restore/switch-in the new context. |
| 0, 24 | dead draws IN bin render | Draws killed/culled during binning/render (no contributing fragments). |
| 0, 25 | predicated draws killed | Draws skipped due to predication/conditional rendering evaluating false. |
| 0, 26 | mode switch | Number of pipeline mode switches (e.g., binning↔rendering / state modes). |
| 0, 27 | zpass done | Count of completed Z-pass operations (depth pass completion events). |
| 0, 28 | context done | Number of completed contexts (context-end events). |
| 0, 29 | cache flush | Number of cache flush events issued/processed. |
| 0, 30 | long preemptions | Count of “long” preemptions (exceeding an internal threshold). |
| - | **RBBM** | - |
| 1, 0 | always count | Reference cycles for the RBBM (top-level) domain. |
| 1, 1 | always ON | Cycles the GPU domain is powered/clocked on (may equal 1,0 depending on gating). |
| 1, 2 | TSE busy | Cycles **TSE** (triangle setup) block is busy. |
| 1, 3 | RAS busy | Cycles **RAS** (rasterizer) block is busy. |
| 1, 4 | PC dcall busy | Cycles **PC** is busy handling draw-call related work. |
| 1, 5 | PC vsd busy | Cycles **PC** is busy handling vertex/stream/dispatch-side work (vertex/stream distribution). |
| 1, 6 | status masked | Cycles where busy status is masked/ignored due to power/clock gating or debug mask. |
| 1, 7 | com busy | Cycles “COM” (command/control fabric) is busy (internal control/command interconnect). |
| 1, 8 | dcom busy | Cycles “DCOM” (data command/control path) is busy (data-side control fabric). |
| 1, 9 | VBIF busy | Cycles **VBIF** (bus interface) is busy servicing memory transactions. |
| 1, 10 | VSC busy | Cycles **VSC** (visibility stream compressor) is busy. |
| 1, 11 | tess busy | Cycles tessellation pipeline is busy. |
| 1, 12 | UCHE busy | Cycles **UCHE** (unified cache/L2 front) is busy. |
| 1, 13 | HLSQ busy | Cycles **HLSQ** (high-level sequencer) is busy. |
| - | **PC** | - |
| 2, 0 | busy cycles | Cycles the **Primitive/Param Cache (PC)** block is busy (active in any state). |
| 2, 1 | working cycles | Cycles PC is doing useful work (excluding stalls/starvation). |
| 2, 2 | stall cycles VFD | Cycles PC stalled waiting on **VFD** (vertex fetch/decode) output/resources. |
| 2, 3 | stall cycles TSE | Cycles PC stalled due to **TSE** backpressure or dependency. |
| 2, 4 | stall cycles VPC | Cycles PC stalled waiting for **VPC** (varying/position cache) availability. |
| 2, 5 | stall cycles UCHE | Cycles PC stalled on UCHE/L2/cache transactions/returns. |
| 2, 6 | stall cycles tess | Cycles PC stalled due to tessellation stage dependency/backpressure. |
| 2, 7 | stall cycles TSE only | Cycles stalled *only* because of TSE (exclusive stall attribution). |
| 2, 8 | stall cycles VPC only | Cycles stalled *only* because of VPC (exclusive stall attribution). |
| 2, 9 | pass1 TF stall cycles | Cycles tess-factor (TF) pass1 stalls (tess-factor generation/consumption bottleneck). |
| 2, 10 | starve cycles for index | Cycles starved waiting for index data/stream. |
| 2, 11 | starve cycles for tess factor | Cycles starved waiting for tessellation factors. |
| 2, 12 | starve cycles for viz stream | Cycles starved waiting for visibility stream data. |
| 2, 13 | starve cycles for position | Cycles starved waiting for position/vertex position stream. |
| 2, 14 | starve cycles DI | Cycles starved waiting for draw/dispatch input (“DI”: draw input/indirect). |
| 2, 15 | vis streams loaded | Number of visibility stream loads/blocks loaded. |
| 2, 16 | instances | Instance count processed (sum of instance invocations across draws). |
| 2, 17 | VPC primitives | Number of primitives sent to/processed by VPC. |
| 2, 18 | dead prim | Primitives rejected/culled before reaching raster (e.g., clip/cull/zero-area). |
| 2, 19 | live prim | Primitives surviving and forwarded downstream. |
| 2, 20 | vertex hits | Vertex cache hits (event count). |
| 2, 21 | IA vertices | Input Assembler vertices fetched/consumed (pre-VS). |
| 2, 22 | IA primitives | Input Assembler primitives assembled (pre-setup). |
| 2, 23 | GS primitives | Primitives output by geometry shader stage (if used). |
| 2, 24 | HS invocations | Hull shader invocations (tess control shader calls). |
| 2, 25 | DS invocations | Domain shader invocations (tess eval shader calls). |
| 2, 26 | VS invocations | Vertex shader invocations. |
| 2, 27 | GS invocations | Geometry shader invocations. |
| 2, 28 | DS primitives | Primitives generated post-domain stage (tessellated primitives). |
| 2, 29 | VPC pos data transaction | Position data transactions to VPC (writes/exports). |
| 2, 30 | 3D drawcalls | Number of 3D draw calls seen by PC. |
| 2, 31 | 2D drawcalls | Number of 2D/blit draw calls seen by PC. |
| 2, 32 | non drawcall global events | Non-draw events (state updates, sync, clears, flushes, etc.). |
| 2, 33 | tess busy cycles | Cycles tessellation sub-pipeline is busy (within PC domain). |
| 2, 34 | tess working cycles | Cycles tessellation sub-pipeline is doing useful work. |
| 2, 35 | tess stall cycles PC | Tessellation stalled due to PC-side backpressure/dependency. |
| 2, 36 | tess starve cycles PC | Tessellation starved for PC-provided input. |
| - | **Vertex Fetch and Decode** | - |
| 3, 0 | busy cycles | Cycles VFD is active (fetch/decode pipeline running). |
| 3, 1 | stall cycles UCHE | Cycles VFD stalled waiting on UCHE/L2 data/returns. |
| 3, 2 | stall cycles VPC alloc | Cycles stalled waiting for VPC allocation/space. |
| 3, 3 | stall cycles miss VB | Cycles stalled due to missing vertex buffer data (cache miss / memory wait). |
| 3, 4 | stall cycles miss Q | Cycles stalled due to queue miss/empty (internal fetch/decode queue). |
| 3, 5 | stall cycles SP info | Cycles stalled waiting for SP shader info/metadata. |
| 3, 6 | stall cycles SP attr | Cycles stalled waiting for SP attribute consumption/readiness. |
| 3, 7 | stall cycles vfdp VB | Cycles VFD prefetch path stalled on vertex buffer access. |
| 3, 8 | stall cycles vfdp Q | Cycles VFD prefetch path stalled on internal queueing. |
| 3, 9 | decoder packer stall | Cycles decode/pack stage stalled (format conversion/packing bottleneck). |
| 3, 10 | starve cycles UCHE | Cycles starved due to lack of UCHE requests/returns to process (bubble attribution). |
| 3, 11 | rbuffer full | Cycles stalled because result buffer is full (cannot write decoded output). |
| 3, 12 | attr info fifo full | Cycles stalled because attribute-info FIFO is full. |
| 3, 13 | decoded attribute bytes | Total bytes of vertex attributes decoded/unpacked. |
| 3, 14 | num attributes | Number of attributes processed (attribute elements). |
| 3, 15 | instructions | Micro-ops/instructions executed by VFD (format/decode ops). |
| 3, 16 | upper shader fibers | Count of “upper” shader fibers/threads launched for VFD-related work. |
| 3, 17 | lower shader fibers | Count of “lower” shader fibers/threads launched for VFD-related work. |
| 3, 18 | mode 0 fibers | Fiber count in mode 0 (implementation-defined decoding mode). |
| 3, 19 | mode 1 fibers | Fiber count in mode 1. |
| 3, 20 | mode 2 fibers | Fiber count in mode 2. |
| 3, 21 | mode 3 fibers | Fiber count in mode 3. |
| 3, 22 | mode 4 fibers | Fiber count in mode 4. |
| 3, 23 | total vertices | Total vertices fetched/decoded. |
| 3, 24 | num attr miss | Number of attribute fetch misses (cache miss events for attributes). |
| 3, 25 | 1 burst req | Number of single-burst memory requests issued (small fetches). |
| 3, 26 | vfdp stall cycles VFD | Prefetch path stalled due to VFD backpressure. |
| 3, 27 | vfdp stall cycles VFD index | Prefetch stalled due to index-stream related backpressure. |
| 3, 28 | vfdp stall cycles VFD prog | Prefetch stalled due to program/state related backpressure. |
| 3, 29 | vfdp starve cycles PC | Prefetch starved waiting for PC to request/provide work. |
| 3, 30 | vfdp VS stage 32 waves | Number of VS waves issued in wave32 mode via VFD prefetch/issue path. |
| - | **High Level SeQuencer** | - |
| 4, 0 | busy cycles | Cycles HLSQ is active (scheduling/dispatching waves). |
| 4, 1 | stall cycles UCHE | Cycles stalled waiting on UCHE/L2 for data (loads, state, etc.). |
| 4, 2 | stall cycles SP state | Cycles stalled waiting on SP state (program/state upload, register state). |
| 4, 3 | stall cycles SP FS stage | Cycles stalled due to fragment-shader stage backpressure/availability. |
| 4, 4 | UCHE latency cycles | Sum of cycles spent waiting on UCHE/L2 (latency accumulator). |
| 4, 5 | UCHE latency count | Number of UCHE/L2 latency samples/transactions counted by 4,4. |
| 4, 6 | FS stage 32 waves | Fragment shader waves launched/executed in wave32 mode. |
| 4, 7 | FS stage 64 waves | Fragment shader waves launched/executed in wave64 mode. |
| 4, 8 | quads | Total pixel quads (2x2) scheduled/processed by FS stage. |
| 4, 9 | SP state copy trans FS stage | Transactions copying SP state for FS stage (state upload/mem moves). |
| 4, 10 | SP state copy trans VS stage | Transactions copying SP state for VS stage. |
| 4, 11 | TP state copy trans FS stage | Transactions copying texture processor state for FS stage. |
| 4, 12 | TP state copy trans VS stage | Transactions copying texture processor state for VS stage. |
| 4, 13 | CS invocations | Total compute shader thread invocations (work-items). |
| 4, 14 | compute drawcalls | Number of compute dispatches. |
| - | **Varying/Position Cache** | - |
| 5, 0 | busy cycles | Cycles VPC block is active. |
| 5, 1 | working cycles | Cycles VPC is doing useful work (not stalled). |
| 5, 2 | stall cycles UCHE | Cycles stalled waiting on UCHE/L2 for reads/writes. |
| 5, 3 | stall cycles VFD wack | Cycles stalled waiting on VFD (writeback/acknowledge handshake). |
| 5, 4 | stall cycles HLSQ prim alloc | Cycles stalled waiting for primitive allocation/credits from HLSQ. |
| 5, 5 | stall cycles PC | Cycles stalled due to PC backpressure/dependency. |
| 5, 6 | stall cycles SP LM | Cycles stalled due to SP local-memory (LM) path constraints (LM exports/reads). |
| 5, 7 | pos export stall cycles | Cycles stalled while exporting position data downstream. |
| 5, 8 | starve cycles SP | Cycles starved waiting for SP-produced data. |
| 5, 9 | starve cycles LRZ | Cycles starved waiting for LRZ consumer/producer handshake. |
| 5, 10 | PC primitives | Primitives received from PC into VPC. |
| 5, 11 | SP components | Number of varying components exported/handled from SP (varyings). |
| 5, 12 | SP LM primitives | Primitives whose varyings/positions were routed via SP local memory path. |
| 5, 13 | SP LM components | Varying components routed via SP local memory. |
| 5, 14 | SP LM dwords | Dwords transferred via SP local memory path. |
| 5, 15 | streamout components | Components written to stream-out/transform feedback. |
| 5, 16 | grant phases | Number of VPC arbitration/grant phases (internal scheduling rounds). |
| - | **Triangle Setup Engine** | - |
| 6, 0 | busy cycles | Cycles TSE is active. |
| 6, 1 | clipping cycles | Cycles spent in clipping work. |
| 6, 2 | stall cycles RAS | Cycles stalled due to rasterizer backpressure. |
| 6, 3 | stall cycles LRZ baryplane | Cycles stalled waiting on LRZ barycentric plane related dependency. |
| 6, 4 | stall cycles LRZ zplane | Cycles stalled waiting on LRZ Z-plane related dependency. |
| 6, 5 | starve cycles PC | Cycles starved waiting for PC to provide primitives. |
| 6, 6 | input prim | Number of input primitives into TSE. |
| 6, 7 | input null prim | Input null/degenerate primitives (no-op primitives). |
| 6, 8 | trival rej prim | Trivially rejected primitives (fast reject). |
| 6, 9 | clipped prim | Primitives that required clipping / were clipped. |
| 6, 10 | zero area prim | Zero-area primitives (degenerate after setup). |
| 6, 11 | faceness culled prim | Primitives culled by facing (backface culling). |
| 6, 12 | zero pixel prim | Primitives that cover zero pixels (after setup/raster rules). |
| 6, 13 | output null prim | Null primitives output (discarded) from TSE. |
| 6, 14 | output visible prim | Visible primitives output downstream to rasterizer. |
| 6, 15 | cinvocation | Clipping invocation count (clipper calls). |
| 6, 16 | cprimitives | Clipping primitive count (primitives processed by clipper). |
| 6, 17 | 2D input prim | 2D primitives input (blits/rects). |
| 6, 18 | 2D alive clcles | Cycles 2D path is active/alive in TSE domain. |
| - | **Rasterizer** | - |
| 7, 0 | busy cycles | Cycles rasterizer is active. |
| 7, 1 | supertile active cycles | Cycles processing supertiles (bin/render tile units). |
| 7, 2 | stall cycles LRZ | Cycles stalled due to LRZ backpressure/dependency. |
| 7, 3 | starve cycles TSE | Cycles starved waiting for TSE to deliver primitives. |
| 7, 4 | super tiles | Number of supertiles processed (large tile bins covering many 8x4 tiles). |
| 7, 5 | 8x4 tiles | Number of 8x4 micro-tiles processed. |
| 7, 6 | maskgen active | Cycles mask generation is active (coverage mask generation). |
| 7, 7 | fully covered super tiles | Supertiles fully covered (all samples covered by primitives). |
| 7, 8 | fully covered 8x4 tiles | 8x4 tiles fully covered. |
| 7, 9 | prim killed invisible | Primitives killed as invisible during raster (coverage/visibility rejection). |
| - | **Unified L2 Cache** | - |
| 8, 0 | busy cycles | Cycles UCHE/L2 interface is active. |
| 8, 1 | stall cycles VBIF | Cycles stalled waiting on VBIF/memory fabric (external memory). |
| 8, 2 | VBIF latency cycles | Accumulated latency cycles waiting on VBIF. |
| 8, 3 | VBIF latency samples | Number of latency samples/transactions counted in 8,2. |
| 8, 4 | VBIF read beats TP | Read data beats returned for TP clients. |
| 8, 5 | VBIF read beats VFD | Read data beats returned for VFD clients. |
| 8, 6 | VBIF read beats HLSQ | Read data beats returned for HLSQ clients. |
| 8, 7 | VBIF read beats LRZ | Read data beats returned for LRZ clients. |
| 8, 8 | VBIF read beats SP | Read data beats returned for SP clients. |
| 8, 9 | read requests TP | Read requests issued by TP to UCHE/VBIF. |
| 8, 10 | read requests VFD | Read requests issued by VFD. |
| 8, 11 | read requests HLSQ | Read requests issued by HLSQ. |
| 8, 12 | read requests LRZ | Read requests issued by LRZ. |
| 8, 13 | read requests SP | Read requests issued by SP. |
| 8, 14 | write requests LRZ | Write requests issued by LRZ. |
| 8, 15 | write requests SP | Write requests issued by SP. |
| 8, 16 | write requests VPC | Write requests issued by VPC. |
| 8, 17 | write requests VSC | Write requests issued by VSC. |
| 8, 18 | evicts | L2 cache evictions (lines/blocks evicted). |
| 8, 19 | bank req0 | Requests to L2 bank 0 (banked distribution). |
| 8, 20 | bank req1 | Requests to L2 bank 1. |
| 8, 21 | bank req2 | Requests to L2 bank 2. |
| 8, 22 | bank req3 | Requests to L2 bank 3. |
| 8, 23 | bank req4 | Requests to L2 bank 4. |
| 8, 24 | bank req5 | Requests to L2 bank 5. |
| 8, 25 | bank req6 | Requests to L2 bank 6. |
| 8, 26 | bank req7 | Requests to L2 bank 7. |
| 8, 27 | VBIF read beats ch0 | Read beats on memory channel 0. |
| 8, 28 | VBIF read beats ch1 | Read beats on memory channel 1. |
| 8, 29 | gmem read beats | Read beats from GMEM (on-chip tile memory) path. |
| 8, 30 | flag count | Number of “flag” transactions/events (compression/CCU flag traffic) observed at UCHE. |
| - | **Texture Processor** | - |
| 9, 0 | busy cycles | Cycles TP is active. |
| 9, 1 | stall cycles UCHE | Cycles TP stalled waiting for UCHE/L2/memory (texture fetch returns). |
| 9, 2 | latency cycles | Accumulated texture fetch latency cycles. |
| 9, 3 | latency trans | Number of texture fetch latency transactions sampled in 9,2. |
| 9, 4 | flag cache request samples | Number of flag-cache (compression metadata) request samples. |
| 9, 5 | flag cache request latency | Accumulated latency for flag-cache requests. |
| 9, 6 | L1 cacheline requests | Texture L1 cache line fetch requests (event count). |
| 9, 7 | L1 cacheline misses | Texture L1 cache line misses (event count). |
| 9, 8 | SP TP trans | Transactions from SP to TP (texture instruction issue / requests). |
| 9, 9 | TP SP trans | Transactions from TP back to SP (returns / responses). |
| 9, 10 | output pixels | Total filtered texel results output (pixel/texel results produced). |
| 9, 11 | filter workload 16bit | 16-bit filtering workload (texels filtered at 16bpp/FP16 formats; vendor-defined weighting). |
| 9, 12 | filter workload 32bit | 32-bit filtering workload (texels filtered at 32bpp/FP32 formats; vendor-defined weighting). |
| 9, 13 | quads received | Quads received for texturing (2x2 pixel groups). |
| 9, 14 | quads offset | Quads using texel offset addressing mode. |
| 9, 15 | quads shadow | Quads using shadow compare sampling. |
| 9, 16 | quads array | Quads sampling array textures. |
| 9, 17 | quads gradient | Quads using explicit gradients. |
| 9, 18 | quads 1D | Quads sampling 1D textures. |
| 9, 19 | quads 2D | Quads sampling 2D textures. |
| 9, 20 | quads buffer | Quads sampling buffer textures. |
| 9, 21 | quads 3D | Quads sampling 3D textures. |
| 9, 22 | quads cube | Quads sampling cubemaps. |
| 9, 23 | state cache requests | Texture state-cache requests (sampler/texture state fetches). |
| 9, 24 | state cache misses | Texture state-cache misses. |
| 9, 25 | divergent quads received | Quads with divergence (threads in quad take different texture paths/coords). |
| 9, 26 | bindless state cache requests | Requests to bindless texture/sampler state cache. |
| 9, 27 | bindless state cache misses | Misses in bindless state cache. |
| 9, 28 | prt non resident events | Partially resident texture (PRT) non-resident page events. |
| 9, 29 | output pixels point | Results produced using point sampling. |
| 9, 30 | output pixels bilinear | Results produced using bilinear filtering. |
| 9, 31 | output pixels mip | Results produced requiring mipmapping. |
| 9, 32 | output pixels aniso | Results produced using anisotropic filtering. |
| 9, 33 | output pixels zero lod | Results produced with LOD=0 (base level) sampling. |
| 9, 34 | flag cache requests | Total flag-cache requests (compression metadata accesses). |
| 9, 35 | flag cache misses | Flag-cache misses. |
| 9, 36 | L1 5 L2 requests | L1→L2 requests (texture L1 misses that go to L2/UCHE). |
| 9, 37 | 2D output pixels | Output results from the dedicated 2D path (blit/2D engine texture outputs). |
| 9, 38 | 2D output pixels point | 2D-path point-sampled outputs. |
| 9, 39 | 2D output pixels bilinear | 2D-path bilinear outputs. |
| 9, 40 | 2D filter workload 16bit | 2D-path 16-bit filtering workload. |
| 9, 41 | 2D filter workload 32bit | 2D-path 32-bit filtering workload. |
| - | **Shader/Streaming Processor** | - |
| 10, 0 | busy cycles | Cycles SP core is active (any wave present/executing). |
| 10, 1 | ALU working cycles | Cycles executing main ALU/FMA pipelines (arithmetic). |
| 10, 2 | EFU working cycles | Cycles executing EFU/special function unit instructions. |
| 10, 3 | stall cycles VPC | Cycles stalled waiting for VPC (varying/position I/O). |
| 10, 4 | stall cycles TP | Cycles stalled waiting for texture results (texture pipe dependency). |
| 10, 5 | stall cycles UCHE | Cycles stalled on memory ops via UCHE/L2 (SSBO/image/global loads). |
| 10, 6 | stall cycles RB | Cycles stalled waiting for render backend (export/ROP backpressure). |
| 10, 7 | scheduler non working | Cycles scheduler has no runnable wave (all waves blocked). |
| 10, 8 | wave contexts | Number of wave contexts allocated/used (waves in flight). |
| 10, 9 | wave context cycles | Sum of cycles wave contexts are resident (occupancy integral). |
| 10, 10 | FS stage wave cycles | Sum of cycles FS waves are active (occupancy integral for FS). |
| 10, 11 | FS stage wave samples | Number of FS wave samples contributing to 10,10. |
| 10, 12 | VS stage wave cycles | Sum of cycles VS waves are active. |
| 10, 13 | VS stage wave samples | Number of VS wave samples contributing to 10,12. |
| 10, 14 | FS stage duration cycles | Total duration cycles spent executing FS work (aggregate). |
| 10, 15 | VS stage duration cycles | Total duration cycles spent executing VS work (aggregate). |
| 10, 16 | wave ctrl cycles | Cycles spent on control-flow management (branch/exec mask, wave control). |
| 10, 17 | wave load cycles | Cycles spent executing load instructions (memory pipeline busy). |
| 10, 18 | wave emit cycles | Cycles spent emitting exports (varyings/colors/pos) from waves. |
| 10, 19 | wave nop cycles | Cycles where issued instruction is NOP (bubbles). |
| 10, 20 | wave wait cycles | Cycles waves are waiting (scoreboard wait on dependency). |
| 10, 21 | wave fetch cycles | Cycles fetching instructions (I-cache/pipe fetch activity). |
| 10, 22 | wave idle cycles | Cycles wave slots are idle (no wave ready). |
| 10, 23 | wave end cycles | Cycles spent on wave end/termination handling. |
| 10, 24 | wave long sync cycles | Cycles spent in long synchronization (barriers/expensive waits). |
| 10, 25 | wave short sync cycles | Cycles spent in short synchronization. |
| 10, 26 | wave join cycles | Cycles spent joining reconverging control flow (join points). |
| 10, 27 | LM load instructions | Count of local-memory (shared/LDS) load instructions. |
| 10, 28 | LM store instructions | Count of local-memory (shared/LDS) store instructions. |
| 10, 29 | LM atomics | Count of local-memory atomic instructions. |
| 10, 30 | GM load instructions | Count of global memory load instructions. |
| 10, 31 | GM store instructions | Count of global memory store instructions. |
| 10, 32 | GM atomics | Count of global memory atomic instructions. |
| 10, 33 | VS stage tex instructions | Texture instruction count issued by VS stage. |
| 10, 34 | VS stage cflow instructions | Control-flow instruction count in VS (branches, calls, etc.). |
| 10, 35 | VS stage EFU instructions | EFU instruction count in VS. |
| 10, 36 | VS stage full ALU instructions | “Full-rate” ALU instruction count in VS (implementation-defined throughput class). |
| 10, 37 | VS stage half ALU instructions | “Half-rate/half-precision” ALU instruction count in VS (often FP16-packed class). |
| 10, 38 | FS stage tex instructions | Texture instruction count in FS stage. |
| 10, 39 | FS stage cflow instructions | Control-flow instruction count in FS. |
| 10, 40 | FS stage EFU instructions | EFU instruction count in FS. |
| 10, 41 | FS stage full ALU instructions | Full-rate ALU instruction count in FS. |
| 10, 42 | FS stage half ALU instructions | Half-rate/half-precision ALU instruction count in FS. |
| 10, 43 | FS stage bary instructions | Barycentric/interpolation instruction count in FS (varying interpolation ops). |
| 10, 44 | VS instructions | Total VS instruction count executed. |
| 10, 45 | FS instructions | Total FS instruction count executed. |
| 10, 46 | addr lock count | Address-register/addr calculation lock/stall events (address dependency conflicts). |
| 10, 47 | UCHE read trans | UCHE read transactions initiated by SP (SSBO/image/UBO reads via UCHE path). |
| 10, 48 | UCHE write trans | UCHE write transactions initiated by SP (SSBO/image stores/atomics writebacks). |
| 10, 49 | export VPC trans | Export transactions from SP to VPC (varyings/positions). |
| 10, 50 | export RB trans | Export transactions from SP to RB (color/depth/stencil exports). |
| 10, 51 | pixels killed | Pixels killed in shader (discard/kill) or late-kill attribution (implementation-defined). |
| 10, 52 | icl1 requests | Instruction cache L1 requests (event count). |
| 10, 53 | icl1 misses | Instruction cache L1 misses. |
| 10, 54 | icl0 requests | Instruction cache L0 requests (event count). |
| 10, 55 | icl0 misses | Instruction cache L0 misses. |
| 10, 56 | HS instructions | Hull shader instruction count. |
| 10, 57 | DS instructions | Domain shader instruction count. |
| 10, 58 | GS instructions | Geometry shader instruction count. |
| 10, 59 | CS instructions | Compute shader instruction count. |
| 10, 60 | GPR read | General-purpose register file read operations (event count). |
| 10, 61 | GPR write | General-purpose register file write operations (event count). |
| 10, 62 | LM ch0 requests | Local-memory channel 0 requests (bank/channel traffic). |
| 10, 63 | LM ch1 requests | Local-memory channel 1 requests. |
| 10, 64 | LM bank conflicts | Local-memory bank conflict events (serialization due to bank collisions). |
| - | **Render backend** | - |
| 11, 0 | busy cycles | Cycles RB/ROP backend is active. |
| 11, 1 | stall cycles CCU | Cycles stalled waiting on CCU (compression/GMEM interface). |
| 11, 2 | stall cycles HLSQ | Cycles stalled waiting on HLSQ/SP to provide fragments/exports. |
| 11, 3 | stall cycles fifo0 full | Cycles stalled because RB FIFO0 is full (backpressure). |
| 11, 4 | stall cycles fifo1 full | Cycles stalled because RB FIFO1 is full. |
| 11, 5 | stall cycles fifo2 full | Cycles stalled because RB FIFO2 is full. |
| 11, 6 | starve cycles SP | Cycles starved waiting for SP exports (no incoming fragments). |
| 11, 7 | starve cycles LRZ tile | Cycles starved waiting for LRZ/tile visibility results. |
| 11, 8 | starve cycles CCU | Cycles starved waiting for CCU/GMEM interface availability. |
| 11, 9 | starve cycles Z plane | Cycles starved waiting for Z-plane data (depth plane). |
| 11, 10 | starve cycles bary plane | Cycles starved waiting for barycentric plane data (coverage/interp planes). |
| 11, 11 | Z workload | Depth test workload metric (event count; often pixels/samples processed for Z). |
| 11, 12 | HLSQ active | Cycles where RB sees HLSQ actively feeding it (front-to-backend active correlation). |
| 11, 13 | Z read | Depth buffer read traffic (bytes or beats; implementation-defined). |
| 11, 14 | Z write | Depth buffer write traffic (bytes or beats). |
| 11, 15 | C read | Color buffer read traffic (bytes or beats; for blending/ROP reads). |
| 11, 16 | C write | Color buffer write traffic (bytes or beats). |
| 11, 17 | total pass | Total fragments/pixels passing through RB (pixels/samples processed). |
| 11, 18 | Z pass | Pixels/samples passing depth test. |
| 11, 19 | Z fail | Pixels/samples failing depth test. |
| 11, 20 | S fail | Pixels/samples failing stencil test. |
| 11, 21 | blended fxp components | Components blended in fixed-point formats (count of blended components). |
| 11, 22 | blended fp16 components | Components blended in FP16 formats (count of blended components). |
| 11, 23 | reserved | Reserved/unused counter slot. |
| 11, 24 | 2D alive cycles | Cycles 2D backend path active. |
| 11, 25 | 2D stall cycles a2d | Cycles stalled in 2D path due to A2D (2D accelerator) dependency/backpressure. |
| 11, 26 | 2D starve cycles src | Cycles starved waiting for 2D source reads. |
| 11, 27 | 2D starve cycles SP | Cycles starved waiting for SP/producer in 2D flow. |
| 11, 28 | 2D starve cycles dst | Cycles starved waiting for 2D destination availability/writes. |
| 11, 29 | 2D valid pixels | Number of valid pixels processed in 2D path. |
| - | **VBIF** | - |
| 13, 0 | axi read requests ID 0 | AXI read request count tagged with ID0. |
| 13, 1 | axi read requests ID 1 | AXI read request count tagged with ID1. |
| 13, 2 | axi read requests ID 2 | AXI read request count tagged with ID2. |
| 13, 3 | axi read requests ID 3 | AXI read request count tagged with ID3. |
| 13, 4 | axi read requests ID 4 | AXI read request count tagged with ID4. |
| 13, 5 | axi read requests ID 5 | AXI read request count tagged with ID5. |
| 13, 6 | axi read requests ID 6 | AXI read request count tagged with ID6. |
| 13, 7 | axi read requests ID 7 | AXI read request count tagged with ID7. |
| 13, 8 | axi read requests ID 8 | AXI read request count tagged with ID8. |
| 13, 9 | axi read requests ID 9 | AXI read request count tagged with ID9. |
| 13, 10 | axi read requests ID 10 | AXI read request count tagged with ID10. |
| 13, 11 | axi read requests ID 11 | AXI read request count tagged with ID11. |
| 13, 12 | axi read requests ID 12 | AXI read request count tagged with ID12. |
| 13, 13 | axi read requests ID 13 | AXI read request count tagged with ID13. |
| 13, 14 | axi read requests ID 14 | AXI read request count tagged with ID14. |
| 13, 15 | axi read requests ID 15 | AXI read request count tagged with ID15. |
| 13, 16 | axi0 read requests total | Total AXI read requests on AXI port/channel 0. |
| 13, 17 | axi1 read requests total | Total AXI read requests on AXI port/channel 1. |
| 13, 18 | axi2 read requests total | Total AXI read requests on AXI port/channel 2. |
| 13, 19 | axi3 read requests total | Total AXI read requests on AXI port/channel 3. |
| 13, 20 | axi read requests total | Total AXI read requests (all IDs/ports). |
| 13, 21 | axi write requests ID 0 | AXI write request count tagged with ID0. |
| 13, 22 | axi write requests ID 1 | AXI write request count tagged with ID1. |
| 13, 23 | axi write requests ID 2 | AXI write request count tagged with ID2. |
| 13, 24 | axi write requests ID 3 | AXI write request count tagged with ID3. |
| 13, 25 | axi write requests ID 4 | AXI write request count tagged with ID4. |
| 13, 26 | axi write requests ID 5 | AXI write request count tagged with ID5. |
| 13, 27 | axi write requests ID 6 | AXI write request count tagged with ID6. |
| 13, 28 | axi write requests ID 7 | AXI write request count tagged with ID7. |
| 13, 29 | axi write requests ID 8 | AXI write request count tagged with ID8. |
| 13, 30 | axi write requests ID 9 | AXI write request count tagged with ID9. |
| 13, 31 | axi write requests ID 10 | AXI write request count tagged with ID10. |
| 13, 32 | axi write requests ID 11 | AXI write request count tagged with ID11. |
| 13, 33 | axi write requests ID 12 | AXI write request count tagged with ID12. |
| 13, 34 | axi write requests ID 13 | AXI write request count tagged with ID13. |
| 13, 35 | axi write requests ID 14 | AXI write request count tagged with ID14. |
| 13, 36 | axi write requests ID 15 | AXI write request count tagged with ID15. |
| 13, 37 | axi0 write requests total | Total AXI write requests on AXI port/channel 0. |
| 13, 38 | axi1 write requests total | Total AXI write requests on AXI port/channel 1. |
| 13, 39 | axi2 write requests total | Total AXI write requests on AXI port/channel 2. |
| 13, 40 | axi3 write requests total | Total AXI write requests on AXI port/channel 3. |
| 13, 41 | axi write requests total | Total AXI write requests (all IDs/ports). |
| 13, 42 | axi total requests | Total AXI requests (reads + writes). |
| 13, 43 | axi read data beats ID 0 | AXI read data beats returned with ID0. |
| 13, 44 | axi read data beats ID 1 | AXI read data beats returned with ID1. |
| 13, 45 | axi read data beats ID 2 | AXI read data beats returned with ID2. |
| 13, 46 | axi read data beats ID 3 | AXI read data beats returned with ID3. |
| 13, 47 | axi read data beats ID 4 | AXI read data beats returned with ID4. |
| 13, 48 | axi read data beats ID 5 | AXI read data beats returned with ID5. |
| 13, 49 | axi read data beats ID 6 | AXI read data beats returned with ID6. |
| 13, 50 | axi read data beats ID 7 | AXI read data beats returned with ID7. |
| 13, 51 | axi read data beats ID 8 | AXI read data beats returned with ID8. |
| 13, 52 | axi read data beats ID 9 | AXI read data beats returned with ID9. |
| 13, 53 | axi read data beats ID 10 | AXI read data beats returned with ID10. |
| 13, 54 | axi read data beats ID 11 | AXI read data beats returned with ID11. |
| 13, 55 | axi read data beats ID 12 | AXI read data beats returned with ID12. |
| 13, 56 | axi read data beats ID 13 | AXI read data beats returned with ID13. |
| 13, 57 | axi read data beats ID 14 | AXI read data beats returned with ID14. |
| 13, 58 | axi read data beats ID 15 | AXI read data beats returned with ID15. |
| 13, 59 | axi0 read data beats total | Total AXI read data beats on AXI port/channel 0. |
| 13, 60 | axi1 read data beats total | Total AXI read data beats on AXI port/channel 1. |
| 13, 61 | axi2 read data beats total | Total AXI read data beats on AXI port/channel 2. |
| 13, 62 | axi3 read data beats total | Total AXI read data beats on AXI port/channel 3. |
| 13, 63 | axi read data beats total | Total AXI read data beats (all ports). |
| 13, 64 | axi write data beats ID 0 | AXI write data beats sent with ID0. |
| 13, 65 | axi write data beats ID 1 | AXI write data beats sent with ID1. |
| 13, 66 | axi write data beats ID 2 | AXI write data beats sent with ID2. |
| 13, 67 | axi write data beats ID 3 | AXI write data beats sent with ID3. |
| 13, 68 | axi write data beats ID 4 | AXI write data beats sent with ID4. |
| 13, 69 | axi write data beats ID 5 | AXI write data beats sent with ID5. |
| 13, 70 | axi write data beats ID 6 | AXI write data beats sent with ID6. |
| 13, 71 | axi write data beats ID 7 | AXI write data beats sent with ID7. |
| 13, 72 | axi write data beats ID 8 | AXI write data beats sent with ID8. |
| 13, 73 | axi write data beats ID 9 | AXI write data beats sent with ID9. |
| 13, 74 | axi write data beats ID 10 | AXI write data beats sent with ID10. |
| 13, 75 | axi write data beats ID 11 | AXI write data beats sent with ID11. |
| 13, 76 | axi write data beats ID 12 | AXI write data beats sent with ID12. |
| 13, 77 | axi write data beats ID 13 | AXI write data beats sent with ID13. |
| 13, 78 | axi write data beats ID 14 | AXI write data beats sent with ID14. |
| 13, 79 | axi write data beats ID 15 | AXI write data beats sent with ID15. |
| 13, 80 | axi0 write data beats total | Total AXI write data beats on AXI port/channel 0. |
| 13, 81 | axi1 write data beats total | Total AXI write data beats on AXI port/channel 1. |
| 13, 82 | axi2 write data beats total | Total AXI write data beats on AXI port/channel 2. |
| 13, 83 | axi3 write data beats total | Total AXI write data beats on AXI port/channel 3. |
| 13, 84 | axi write data beats total | Total AXI write data beats (all ports). |
| 13, 85 | axi data beats total | Total AXI data beats (read + write). |
| - | **Visibility Stream Compressor** | - |
| 23, 0 | busy cycles | Cycles VSC is active. |
| 23, 1 | working cycles | Cycles VSC is doing useful work (not stalled). |
| 23, 2 | stall cycles UCHE | Cycles VSC stalled waiting on UCHE/L2. |
| 23, 3 | eot num | Number of end-of-tile (EOT) events/records produced. |
| - | **Cache and Compression Unit** | - |
| 24, 0 | busy cycles | Cycles CCU is active (GMEM + compression metadata handling). |
| 24, 1 | stall cycles RB depth return | Cycles stalled waiting for RB depth data return/handshake. |
| 24, 2 | stall cycles RB color return | Cycles stalled waiting for RB color data return/handshake. |
| 24, 3 | starve cycles flag return | Cycles starved waiting for compression “flag” metadata returns. |
| 24, 4 | depth blocks | Depth blocks processed (typically 4x4 blocks). |
| 24, 5 | color blocks | Color blocks processed (typically 4x4 blocks). |
| 24, 6 | depth block hit | Depth block cache hits (metadata/data reuse). |
| 24, 7 | color block hit | Color block cache hits. |
| 24, 8 | partial block read | Partial block reads (read-modify-write or partial coverage). |
| 24, 9 | gmem read | GMEM read traffic (bytes/beats; implementation-defined). |
| 24, 10 | gmem write | GMEM write traffic (bytes/beats). |
| 24, 11 | depth read flag0 count | Count of depth reads with flag state 0 (compression state class 0). |
| 24, 12 | depth read flag1 count | Count of depth reads with flag state 1. |
| 24, 13 | depth read flag2 count | Count of depth reads with flag state 2. |
| 24, 14 | depth read flag3 count | Count of depth reads with flag state 3. |
| 24, 15 | depth read flag4 count | Count of depth reads with flag state 4. |
| 24, 16 | color read flag0 count | Count of color reads with flag state 0. |
| 24, 17 | color read flag1 count | Count of color reads with flag state 1. |
| 24, 18 | color read flag2 count | Count of color reads with flag state 2. |
| 24, 19 | color read flag3 count | Count of color reads with flag state 3. |
| 24, 20 | color read flag4 count | Count of color reads with flag state 4. |
| 24, 21 | 2D busy cycles | Cycles CCU 2D path is active. |
| 24, 22 | 2D RD req | Number of 2D read requests. |
| 24, 23 | 2D WR req | Number of 2D write requests. |
| 24, 24 | 2D reorder starve cycles | Cycles starved due to 2D reorder queue (dependency / ordering). |
| 24, 25 | 2D pixels | Number of pixels processed via 2D path. |
| - | **Low Resolution Z pass** | - |
| 25, 0 | busy cycles | Cycles LRZ block is active. |
| 25, 1 | starve cycles RAS | Cycles LRZ starved waiting for rasterizer/tile input. |
| 25, 2 | stall cycles RB | Cycles LRZ stalled due to RB dependency/backpressure. |
| 25, 3 | stall cycles VSC | Cycles LRZ stalled due to VSC dependency/backpressure. |
| 25, 4 | stall cycles VPC | Cycles LRZ stalled due to VPC dependency. |
| 25, 5 | stall cycles flag prefetch | Cycles stalled while prefetching compression flags/metadata. |
| 25, 6 | stall cycles UCHE | Cycles stalled waiting for UCHE/L2 transactions/returns. |
| 25, 7 | LRZ read | LRZ buffer read operations/traffic (events or beats). |
| 25, 8 | LRZ write | LRZ buffer write operations/traffic. |
| 25, 9 | read latency | Accumulated latency for LRZ reads (cycles). |
| 25, 10 | merge cache updating | Events/cycles updating LRZ merge cache (hierarchical Z merge). |
| 25, 11 | prim killed BY maskgen | Primitives killed by mask generator (coverage/visibility mask). |
| 25, 12 | prim killed BY LRZ | Primitives killed by LRZ early-Z reject. |
| 25, 13 | visible prim after LRZ | Primitives remaining visible after LRZ culling. |
| 25, 14 | full 8x8 tiles | Number of fully covered 8x8 tiles processed. |
| 25, 15 | partial 8x8 tiles | Number of partially covered 8x8 tiles processed. |
| 25, 16 | tile killed | Tiles rejected/killed by LRZ (no visible samples). |
| 25, 17 | total pixel | Total pixels/samples considered by LRZ. |
| 25, 18 | visible pixel after LRZ | Pixels/samples remaining visible after LRZ. |
| - | **CMP** | - |
| 26, 0 | cmpdecmp stall cycles VBIF | Cycles compression/decompression unit stalled waiting on VBIF/memory. |
| 26, 1 | cmpdecmp VBIF latency cycles | Accumulated VBIF latency cycles for cmp/decmp traffic. |
| 26, 2 | cmpdecmp VBIF latency samples | Number of VBIF latency samples for cmp/decmp. |
| 26, 3 | cmpdecmp VBIF read data CCU | Read data beats returned from VBIF into CCU via cmp/decmp path. |
| 26, 4 | cmpdecmp VBIF write data CCU | Write data beats sent to VBIF from CCU via cmp/decmp path. |
| 26, 5 | cmpdecmp VBIF read request | Number of VBIF read requests issued by cmp/decmp path. |
| 26, 6 | cmpdecmp VBIF write request | Number of VBIF write requests issued by cmp/decmp path. |
| 26, 7 | cmpdecmp VBIF read data | Total VBIF read data beats for cmp/decmp (all sinks). |
| 26, 8 | cmpdecmp VBIF write data | Total VBIF write data beats for cmp/decmp (all sources). |
| 26, 9 | cmpdecmp flag fetch cycles | Cycles spent fetching compression flags/metadata. |
| 26, 10 | cmpdecmp flag fetch samples | Number of flag-fetch samples/transactions. |
| 26, 11 | cmpdecmp depth write flag1 count | Count of depth writes with compression flag state 1. |
| 26, 12 | cmpdecmp depth write flag2 count | Count of depth writes with compression flag state 2. |
| 26, 13 | cmpdecmp depth write flag3 count | Count of depth writes with compression flag state 3. |
| 26, 14 | cmpdecmp depth write flag4 count | Count of depth writes with compression flag state 4. |
| 26, 15 | cmpdecmp color write flag1 count | Count of color writes with compression flag state 1. |
| 26, 16 | cmpdecmp color write flag2 count | Count of color writes with compression flag state 2. |
| 26, 17 | cmpdecmp color write flag3 count | Count of color writes with compression flag state 3. |
| 26, 18 | cmpdecmp color write flag4 count | Count of color writes with compression flag state 4. |
| 26, 19 | cmpdecmp 2D stall cycles VBIF req | 2D cmp/decmp cycles stalled on VBIF request issue. |
| 26, 20 | cmpdecmp 2D stall cycles VBIF WR | 2D cmp/decmp cycles stalled on VBIF write path. |
| 26, 21 | cmpdecmp 2D stall cycles VBIF return | 2D cmp/decmp cycles stalled waiting for VBIF return data/acks. |
| 26, 22 | cmpdecmp 2D RD data | 2D cmp/decmp read data beats/transactions. |
| 26, 23 | cmpdecmp 2D WR data | 2D cmp/decmp write data beats/transactions. |

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

*description from LLM*
| group, counter | name | desc |
|---|---|---|
| - | **Command Parser** | - |
| 0, 0 | always count | Constant 1s counter (sanity/normalization reference). |
| 0, 1 | busy gfx core idle | Cycles CP/SQE is “busy” while graphics core is otherwise idle (front-end occupied, back-end not progressing). |
| 0, 2 | busy cycles | Cycles command processor/queue engine is busy processing commands. |
| 0, 3 | num preemptions | Number of GPU preemption events (context switches triggered by scheduler). |
| 0, 4 | preemption reaction delay | Cycles from preempt request to when GPU begins reacting (latency to acknowledge). |
| 0, 5 | preemption switch out time | Cycles spent saving state and switching out the preempted context. |
| 0, 6 | preemption switch IN time | Cycles spent restoring state and switching in the new context. |
| 0, 7 | dead draws IN bin render | Draws that were binned but later discarded before/during render pass (killed work). |
| 0, 8 | predicated draws killed | Draws suppressed by predication/conditional rendering (predicate evaluated false). |
| 0, 9 | mode switch | Number of pipeline mode switches (e.g., switching between 3D/compute/2D or binning/render modes). |
| 0, 10 | zpass done | Count of completed Z-pass / depth-only style passes signaled done. |
| 0, 11 | context done | Number of completed contexts/ringbuffer submissions (end-of-context events). |
| 0, 12 | cache flush | Number of cache flush events initiated by CP (coherency/visibility maintenance). |
| 0, 13 | long preemptions | Number of “long” preemptions (preemptions exceeding an internal threshold). |
| 0, 14 | sqe I cache starve | Cycles SQE starved waiting on its instruction cache (I-cache miss/latency). |
| 0, 15 | sqe idle | Cycles SQE has no work to execute (front-end idle). |
| 0, 16 | sqe pm4 starve RB IB | Cycles SQE stalled waiting for PM4 stream due to ringbuffer/indirect-buffer fetch starvation. |
| 0, 17 | sqe pm4 starve sds | Cycles SQE stalled because PM4 stream is waiting on SDS (state/data store) availability. |
| 0, 18 | sqe mrb starve | Cycles SQE stalled waiting for “MRB” (micro/ring buffer) input. |
| 0, 19 | sqe rrb starve | Cycles SQE stalled waiting for “RRB” (ring/raster related buffer) input. |
| 0, 20 | sqe vsd starve | Cycles SQE stalled waiting for VSD (VSC/VSD decode/path) related input. |
| 0, 21 | vsd decode starve | Cycles VSD decode stage is starved (no input / blocked upstream). |
| 0, 22 | sqe pipe out stall | Cycles SQE cannot push work downstream due to pipe-out backpressure. |
| 0, 23 | sqe sync stall | Cycles SQE stalled on synchronization primitives (barriers, waits). |
| 0, 24 | sqe pm4 wfi stall | Cycles SQE stalled due to PM4 WFI (wait-for-idle) command. |
| 0, 25 | sqe sys wfi stall | Cycles SQE stalled due to system-level WFI/wait condition. |
| 0, 26 | sqe T4 exec | Number of executed T4 packets/operations (internal CP micro-op class). |
| 0, 27 | sqe load state exec | Number of executed “load state” operations (register/state restore). |
| 0, 28 | sqe save sds state | Number of times SQE saved SDS-related state (typically for preempt/context save). |
| 0, 29 | sqe draw exec | Number of executed draw dispatch operations (draw packet execution count). |
| 0, 30 | sqe ctxt reg bunch exec | Number of executed context-register “bunch” loads/writes (bulk state programming). |
| 0, 31 | sqe exec profiled | Cycles/occurrences where SQE execution is within a profiled window (internal profiling gate). |
| 0, 32 | memory pool empty | Times/cycles CP memory pool ran empty (no space/allocations available). |
| 0, 33 | memory pool sync stall | Cycles stalled due to synchronization around CP memory pool management. |
| 0, 34 | memory pool above thresh | Time/cycles memory pool usage above a threshold (pressure indicator). |
| 0, 35 | ahb WR stall pre draws | Cycles stalled on AHB writes before issuing draws (bus write congestion). |
| 0, 36 | ahb stall sqe gmu | Cycles SQE stalled due to AHB transactions with GMU (power/management interface). |
| 0, 37 | ahb stall sqe WR other | Cycles SQE stalled due to other AHB write traffic. |
| 0, 38 | ahb stall sqe RD other | Cycles SQE stalled due to other AHB read traffic. |
| 0, 39 | cluster0 empty | Cycles/occurrences where cluster 0 work queue is empty (no work). |
| 0, 40 | cluster1 empty | Cycles/occurrences where cluster 1 work queue is empty. |
| 0, 41 | cluster2 empty | Cycles/occurrences where cluster 2 work queue is empty. |
| 0, 42 | cluster3 empty | Cycles/occurrences where cluster 3 work queue is empty. |
| 0, 43 | cluster4 empty | Cycles/occurrences where cluster 4 work queue is empty. |
| 0, 44 | cluster5 empty | Cycles/occurrences where cluster 5 work queue is empty. |
| 0, 45 | pm4 data | Number of PM4 data DWORDs processed (payload words). |
| 0, 46 | pm4 headers | Number of PM4 packet headers processed. |
| 0, 47 | vbif read beats | Total read data beats observed at VBIF interface (bandwidth in beats). |
| 0, 48 | vbif write beats | Total write data beats observed at VBIF interface. |
| 0, 49 | sqe instr counter | Number of SQE micro-instructions executed (front-end instruction count). |
| - | **RBBM** | - |
| 1, 0 | always count | Constant 1s counter (sanity/normalization reference). |
| 1, 1 | always ON | Cycles RBBM domain is powered/clocked on. |
| 1, 2 | TSE busy | Cycles Triangle Setup Engine is busy. |
| 1, 3 | RAS busy | Cycles Rasterizer is busy. |
| 1, 4 | PC dcall busy | Cycles Primitive/Parameter (PC) busy doing draw-call related work. |
| 1, 5 | PC vsd busy | Cycles PC busy with VSD-related work (visibility stream/decode path). |
| 1, 6 | status masked | Cycles status/busy reporting is masked (power/clock gating or debug mask active). |
| 1, 7 | com busy | Cycles “COM” block busy (command/compute orchestrator domain; internal). |
| 1, 8 | dcom busy | Cycles “DCOM” block busy (data/dispatch command domain; internal). |
| 1, 9 | vbif busy | Cycles VBIF is busy (actively servicing memory transactions). |
| 1, 10 | VSC busy | Cycles Visibility Stream Compressor is busy. |
| 1, 11 | tess busy | Cycles tessellation front-end is busy. |
| 1, 12 | UCHE busy | Cycles Unified Cache (UCHE) is busy. |
| 1, 13 | HLSQ busy | Cycles High Level Sequencer (HLSQ) is busy. |
| - | **PC** | - |
| 2, 0 | busy cycles | Cycles PC block is busy (active). |
| 2, 1 | working cycles | Cycles PC is doing useful work (not stalled). |
| 2, 2 | stall cycles VFD | Cycles PC stalled waiting for Vertex Fetch/Decode. |
| 2, 3 | stall cycles TSE | Cycles PC stalled waiting for Triangle Setup Engine. |
| 2, 4 | stall cycles VPC | Cycles PC stalled waiting for Varying/Position Cache. |
| 2, 5 | stall cycles UCHE | Cycles PC stalled due to UCHE/cache effects (requests/returns). |
| 2, 6 | stall cycles tess | Cycles PC stalled due to tessellation stage/backpressure. |
| 2, 7 | stall cycles TSE only | Stall cycles attributable only to TSE (no other simultaneous stall reason). |
| 2, 8 | stall cycles VPC only | Stall cycles attributable only to VPC. |
| 2, 9 | pass1 TF stall cycles | Cycles pass-1 tess-factor path stalled (tess-factor generation/consumption). |
| 2, 10 | starve cycles for index | Cycles PC starved waiting for index data. |
| 2, 11 | starve cycles for tess factor | Cycles PC starved waiting for tessellation factor data. |
| 2, 12 | starve cycles for viz stream | Cycles PC starved waiting for visibility stream input. |
| 2, 13 | starve cycles for position | Cycles PC starved waiting for position stream data. |
| 2, 14 | starve cycles DI | Cycles PC starved waiting for DI (draw/dispatch input) stream. |
| 2, 15 | vis streams loaded | Number of visibility streams loaded/consumed by PC. |
| 2, 16 | instances | Number of instances processed (instanced draws). |
| 2, 17 | VPC primitives | Number of primitives emitted toward VPC. |
| 2, 18 | dead prim | Primitives killed/culled before becoming “live” (backface/clip/degenerate/etc.). |
| 2, 19 | live prim | Primitives that survive and proceed down the pipeline. |
| 2, 20 | vertex hits | Vertex reuse “hits” (cache hits / reused vertices depending on mode). |
| 2, 21 | IA vertices | Input Assembler vertices consumed. |
| 2, 22 | IA primitives | Input Assembler primitives assembled. |
| 2, 23 | GS primitives | Geometry shader primitives output/processed. |
| 2, 24 | HS invocations | Hull shader (tess control) invocations. |
| 2, 25 | DS invocations | Domain shader (tess eval) invocations. |
| 2, 26 | VS invocations | Vertex shader invocations. |
| 2, 27 | GS invocations | Geometry shader invocations. |
| 2, 28 | DS primitives | Domain-shader generated primitives. |
| 2, 29 | VPC pos data transaction | Transactions sending position data to VPC. |
| 2, 30 | 3D drawcalls | Number of 3D draw calls processed. |
| 2, 31 | 2D drawcalls | Number of 2D/blit draw calls processed. |
| 2, 32 | non drawcall global events | Non-draw global events (state changes, barriers, flushes) seen by PC. |
| 2, 33 | tess busy cycles | Cycles tessellation unit is busy (as viewed from PC). |
| 2, 34 | tess working cycles | Cycles tessellation unit doing useful work (not stalled). |
| 2, 35 | tess stall cycles PC | Tessellation stalled due to PC backpressure/dependency. |
| 2, 36 | tess starve cycles PC | Tessellation starved waiting for PC input. |
| 2, 37 | TSE transaction | Transactions between PC and TSE (primitive/setup handoff). |
| 2, 38 | TSE vertex | Vertices delivered toward TSE. |
| 2, 39 | tess PC UV trans | Tessellation-related UV transactions through PC. |
| 2, 40 | tess PC UV patches | Number of tessellation UV patches processed. |
| 2, 41 | tess factor trans | Tess factor transactions (reads/writes/hand-offs). |
| - | **Vertex Fetch and Decode** | - |
| 3, 0 | busy cycles | Cycles VFD is busy. |
| 3, 1 | stall cycles UCHE | Cycles VFD stalled waiting on UCHE/memory for vertex fetches. |
| 3, 2 | stall cycles VPC alloc | Cycles VFD stalled waiting for VPC allocation/space. |
| 3, 3 | stall cycles SP info | Cycles VFD stalled waiting for SP-provided info/state. |
| 3, 4 | stall cycles SP attr | Cycles VFD stalled waiting for SP attribute consumption/readiness. |
| 3, 5 | starve cycles UCHE | Cycles VFD starved due to UCHE not providing data/credits. |
| 3, 6 | rbuffer full | Cycles/occurrences where VFD ring/return buffer is full (backpressure). |
| 3, 7 | attr info fifo full | Cycles/occurrences attribute-info FIFO is full (cannot enqueue). |
| 3, 8 | decoded attribute bytes | Total bytes of vertex attributes decoded/unpacked. |
| 3, 9 | num attributes | Total number of attributes processed/decoded. |
| 3, 10 | upper shader fibers | Number of “upper” shader fibers generated (micro-batches/lanes groupings). |
| 3, 11 | lower shader fibers | Number of “lower” shader fibers generated. |
| 3, 12 | mode 0 fibers | Fibers generated in mode 0 (vertex fetch/format mode variant). |
| 3, 13 | mode 1 fibers | Fibers generated in mode 1. |
| 3, 14 | mode 2 fibers | Fibers generated in mode 2. |
| 3, 15 | mode 3 fibers | Fibers generated in mode 3. |
| 3, 16 | mode 4 fibers | Fibers generated in mode 4. |
| 3, 17 | total vertices | Total vertices fetched/decoded. |
| 3, 18 | vfdp stall cycles VFD | VFD prefetch (VFDP) stalled due to VFD internal backpressure. |
| 3, 19 | vfdp stall cycles VFD index | VFDP stalled waiting specifically for index-related path. |
| 3, 20 | vfdp stall cycles VFD prog | VFDP stalled due to programmable/format/program path constraints. |
| 3, 21 | vfdp starve cycles PC | VFDP starved waiting for PC to provide work/requests. |
| 3, 22 | vfdp VS stage waves | Waves launched attributable to VFD prefetch feeding VS stage. |
| - | **High Level SeQuencer** | - |
| 4, 0 | busy cycles | Cycles HLSQ is busy (front-end sequencing active). |
| 4, 1 | stall cycles UCHE | Cycles HLSQ stalled waiting on UCHE/cache/memory. |
| 4, 2 | stall cycles SP state | Cycles HLSQ stalled waiting on SP state/availability. |
| 4, 3 | stall cycles SP FS stage | Cycles HLSQ stalled due to fragment-shader stage backpressure/availability. |
| 4, 4 | UCHE latency cycles | Accumulated cycles waiting on UCHE (latency sum). |
| 4, 5 | UCHE latency count | Number of UCHE latency samples/transactions counted. |
| 4, 6 | FS stage 1X waves | Number of FS waves launched in 1X rate mode. |
| 4, 7 | FS stage 2X waves | Number of FS waves launched in 2X rate mode. |
| 4, 8 | quads | Number of pixel quads generated/issued toward FS/TP. |
| 4, 9 | CS invocations | Compute shader invocations (threads/workitems) issued. |
| 4, 10 | compute drawcalls | Compute dispatches/drawcalls issued. |
| 4, 11 | FS data wait programming | Cycles/occurrences programming FS “data wait” (waiting on inputs/exports). |
| 4, 12 | dual FS prog active | Cycles dual-issue/dual-program fragment mode active. |
| 4, 13 | dual VS prog active | Cycles dual-issue/dual-program vertex mode active. |
| 4, 14 | FS batch count zero | Occurrences where FS batch count is zero (no FS work in batch). |
| 4, 15 | VS batch count zero | Occurrences where VS batch count is zero. |
| 4, 16 | wave pending NO quad | Waves pending because no quads are available yet. |
| 4, 17 | wave pending NO prim base | Waves pending because primitive base/metadata not ready. |
| 4, 18 | stall cycles VPC | Cycles HLSQ stalled waiting on VPC outputs/credits. |
| 4, 19 | pixels | Number of pixels generated/processed at HLSQ level (pre-RB). |
| 4, 20 | draw mode switch vsfs sync | Occurrences/cycles of draw-mode switch requiring VS/FS synchronization. |
| - | **Varying/Position Cache** | - |
| 5, 0 | busy cycles | Cycles VPC is busy. |
| 5, 1 | working cycles | Cycles VPC is making forward progress (not stalled). |
| 5, 2 | stall cycles UCHE | Cycles VPC stalled waiting on UCHE/memory. |
| 5, 3 | stall cycles VFD wack | Cycles stalled due to VFD “WACK”/ack/handshake backpressure. |
| 5, 4 | stall cycles HLSQ prim alloc | Cycles stalled waiting for HLSQ primitive allocation/credits. |
| 5, 5 | stall cycles PC | Cycles stalled due to PC dependency/backpressure. |
| 5, 6 | stall cycles SP LM | Cycles stalled due to SP local memory (LM) interactions. |
| 5, 7 | starve cycles SP | Cycles VPC starved waiting for SP consumption/requests. |
| 5, 8 | starve cycles LRZ | Cycles starved due to LRZ path (mask/visibility) dependencies. |
| 5, 9 | PC primitives | Primitives received from PC into VPC. |
| 5, 10 | SP components | Varying components delivered toward SP (interpolants/components). |
| 5, 11 | stall cycles vpcram pos | Cycles stalled due to VPC RAM position storage access/contension. |
| 5, 12 | LRZ assign primitives | Primitives assigned for LRZ evaluation. |
| 5, 13 | RB visible primitives | Primitives marked visible and sent toward RB. |
| 5, 14 | LM transaction | Transactions with local memory / parameter memory. |
| 5, 15 | streamout transaction | Stream-out (transform feedback) transactions. |
| 5, 16 | VS busy cycles | Cycles VPC busy in VS-related activity. |
| 5, 17 | PS busy cycles | Cycles VPC busy in PS/FS-related activity. |
| 5, 18 | VS working cycles | Useful VS-related cycles in VPC. |
| 5, 19 | PS working cycles | Useful PS-related cycles in VPC. |
| 5, 20 | starve cycles RB | Cycles VPC starved because RB cannot accept data (downstream backpressure). |
| 5, 21 | num vpcram read pos | Number of VPC RAM reads of position data. |
| 5, 22 | wit full cycles | Cycles “WIT” (work/item table) is full (cannot allocate). |
| 5, 23 | vpcram full cycles | Cycles VPC RAM is full (allocation/backpressure). |
| 5, 24 | LM full wait for intp end | Cycles waiting because LM full until interpolation/end condition. |
| 5, 25 | num vpcram write | Number of VPC RAM write operations. |
| 5, 26 | num vpcram read SO | Number of VPC RAM reads for stream-out. |
| 5, 27 | num attr req LM | Number of attribute requests to local memory. |
| - | **Triangle Setup Engine** | - |
| 6, 0 | busy cycles | Cycles TSE is busy. |
| 6, 1 | clipping cycles | Cycles spent performing clipping (clipper active). |
| 6, 2 | stall cycles RAS | Cycles TSE stalled due to rasterizer backpressure. |
| 6, 3 | stall cycles LRZ baryplane | Cycles stalled waiting on LRZ barycentric plane setup. |
| 6, 4 | stall cycles LRZ zplane | Cycles stalled waiting on LRZ Z-plane setup. |
| 6, 5 | starve cycles PC | Cycles TSE starved waiting for PC primitives. |
| 6, 6 | input prim | Number of input primitives accepted by TSE. |
| 6, 7 | input null prim | Number of “null” input primitives (degenerate/no-op markers). |
| 6, 8 | trival rej prim | Primitives trivially rejected (fast reject). |
| 6, 9 | clipped prim | Primitives that required/underwent clipping. |
| 6, 10 | zero area prim | Degenerate primitives with zero area. |
| 6, 11 | faceness culled prim | Primitives culled by face direction (backface/frontface culling). |
| 6, 12 | zero pixel prim | Primitives producing zero covered pixels (after setup/raster rules). |
| 6, 13 | output null prim | Null primitives output downstream (markers/degenerate). |
| 6, 14 | output visible prim | Visible primitives output to rasterization. |
| 6, 15 | cinvocation | Clipper invocations (number of clip operations launched). |
| 6, 16 | cprimitives | Primitives processed by clipper. |
| 6, 17 | 2D input prim | 2D primitives fed to TSE/2D path. |
| 6, 18 | 2D alive cycles | Cycles 2D path is active in TSE. |
| 6, 19 | clip planes | Number of clip planes processed/evaluated. |
| - | **Rasterizer** | - |
| 7, 0 | busy cycles | Cycles rasterizer is busy. |
| 7, 1 | supertile active cycles | Cycles supertile rasterization/processing is active. |
| 7, 2 | stall cycles LRZ | Cycles rasterizer stalled due to LRZ backpressure/dependency. |
| 7, 3 | starve cycles TSE | Cycles rasterizer starved waiting for TSE output. |
| 7, 4 | super tiles | Number of supertiles generated/processed. |
| 7, 5 | 8x4 tiles | Number of 8x4 tiles generated/processed. |
| 7, 6 | maskgen active | Cycles mask generator is active (coverage masks). |
| 7, 7 | fully covered super tiles | Supertiles fully covered by primitives (no partial coverage). |
| 7, 8 | fully covered 8x4 tiles | 8x4 tiles fully covered. |
| 7, 9 | prim killed invisible | Primitives killed because determined invisible (cull/coverage/LRZ). |
| 7, 10 | supertile gen active cycles | Cycles spent generating supertiles. |
| 7, 11 | LRZ intf working cycles | Cycles LRZ interface is working (handshake/transactions). |
| 7, 12 | blocks | Number of raster blocks (block-level work units) produced/processed. |
| - | **Unified L2 Cache** | - |
| 8, 0 | busy cycles | Cycles UCHE/L2 is busy. |
| 8, 1 | stall cycles arbiter | Cycles stalled due to UCHE arbiter contention (request arbitration). |
| 8, 2 | vbif latency cycles | Total cycles waiting on VBIF (external memory) returns. |
| 8, 3 | vbif latency samples | Number of VBIF latency samples taken. |
| 8, 4 | vbif read beats TP | Read data beats for texture processor clients. |
| 8, 5 | vbif read beats VFD | Read data beats for vertex fetch/decode clients. |
| 8, 6 | vbif read beats HLSQ | Read data beats for HLSQ clients. |
| 8, 7 | vbif read beats LRZ | Read data beats for LRZ clients. |
| 8, 8 | vbif read beats SP | Read data beats for shader processor clients. |
| 8, 9 | read requests TP | Read requests issued on behalf of TP. |
| 8, 10 | read requests VFD | Read requests issued on behalf of VFD. |
| 8, 11 | read requests HLSQ | Read requests issued on behalf of HLSQ. |
| 8, 12 | read requests LRZ | Read requests issued on behalf of LRZ. |
| 8, 13 | read requests SP | Read requests issued on behalf of SP. |
| 8, 14 | write requests LRZ | Write requests issued on behalf of LRZ. |
| 8, 15 | write requests SP | Write requests issued on behalf of SP. |
| 8, 16 | write requests VPC | Write requests issued on behalf of VPC. |
| 8, 17 | write requests VSC | Write requests issued on behalf of VSC. |
| 8, 18 | evicts | Number of UCHE cache line evictions. |
| 8, 19 | bank req0 | Requests to UCHE bank 0 (bank-level pressure). |
| 8, 20 | bank req1 | Requests to UCHE bank 1. |
| 8, 21 | bank req2 | Requests to UCHE bank 2. |
| 8, 22 | bank req3 | Requests to UCHE bank 3. |
| 8, 23 | bank req4 | Requests to UCHE bank 4. |
| 8, 24 | bank req5 | Requests to UCHE bank 5. |
| 8, 25 | bank req6 | Requests to UCHE bank 6. |
| 8, 26 | bank req7 | Requests to UCHE bank 7. |
| 8, 27 | vbif read beats ch0 | Read beats returned on memory channel 0. |
| 8, 28 | vbif read beats ch1 | Read beats returned on memory channel 1. |
| 8, 29 | gmem read beats | Read beats from GMEM (tile memory) path. |
| 8, 30 | tph ref full | Cycles/occurrences texture page handler “ref” queue full. |
| 8, 31 | tph victim full | Cycles/occurrences TPH victim queue full. |
| 8, 32 | tph ext full | Cycles/occurrences TPH external queue full. |
| 8, 33 | vbif stall write data | Cycles stalled because VBIF cannot accept write data (write-data backpressure). |
| 8, 34 | dcmp latency samples | Number of decompression latency samples (dcmp path). |
| 8, 35 | dcmp latency cycles | Total decompression latency cycles accumulated. |
| 8, 36 | vbif read beats PC | Read beats for PC client. |
| 8, 37 | read requests PC | Read requests issued on behalf of PC. |
| 8, 38 | ram read req | UCHE internal RAM read requests. |
| 8, 39 | ram write req | UCHE internal RAM write requests. |
| - | **Texture Processor** | - |
| 9, 0 | busy cycles | Cycles texture processor is busy. |
| 9, 1 | stall cycles UCHE | Cycles TP stalled waiting on UCHE/L2. |
| 9, 2 | latency cycles | Total cycles spent waiting on texture memory responses (latency sum). |
| 9, 3 | latency trans | Number of texture transactions sampled for latency accounting. |
| 9, 4 | flag cache request samples | Number of samples/transactions involving TP flag cache requests. |
| 9, 5 | flag cache request latency | Accumulated latency for TP flag cache requests. |
| 9, 6 | L1 cacheline requests | Texture L1 cache line fetch requests. |
| 9, 7 | L1 cacheline misses | Texture L1 cache misses (cacheline not present). |
| 9, 8 | SP TP trans | Transactions from SP to TP (texture/sampler requests). |
| 9, 9 | TP SP trans | Transactions from TP back to SP (returned texels/data). |
| 9, 10 | output pixels | Number of pixels/texels output by TP to consumers (typically FS). |
| 9, 11 | filter workload 16bit | Filtering work units for 16-bit formats (weighted cost). |
| 9, 12 | filter workload 32bit | Filtering work units for 32-bit formats. |
| 9, 13 | quads received | Number of quads received for texturing. |
| 9, 14 | quads offset | Quads using offset addressing mode. |
| 9, 15 | quads shadow | Quads using shadow compare sampling. |
| 9, 16 | quads array | Quads sampling array textures. |
| 9, 17 | quads gradient | Quads using explicit gradients (ddx/ddy). |
| 9, 18 | quads 1D | Quads sampling 1D textures. |
| 9, 19 | quads 2D | Quads sampling 2D textures. |
| 9, 20 | quads buffer | Quads sampling buffer textures. |
| 9, 21 | quads 3D | Quads sampling 3D textures. |
| 9, 22 | quads cube | Quads sampling cube maps. |
| 9, 23 | divergent quads received | Quads where lanes diverge in texture coordinates/control (less coherent). |
| 9, 24 | prt non resident events | Partially Resident Texture events where requested page is non-resident. |
| 9, 25 | output pixels point | Output pixels sampled with point filtering. |
| 9, 26 | output pixels bilinear | Output pixels sampled with bilinear filtering. |
| 9, 27 | output pixels mip | Output pixels involving mipmapping. |
| 9, 28 | output pixels aniso | Output pixels involving anisotropic filtering. |
| 9, 29 | output pixels zero lod | Output pixels forced to LOD 0 (base level). |
| 9, 30 | flag cache requests | Number of TP flag cache requests. |
| 9, 31 | flag cache misses | TP flag cache misses. |
| 9, 32 | L1 5 L2 requests | Requests from L1 to L2/UCHE. |
| 9, 33 | 2D output pixels | Output pixels for 2D textures specifically. |
| 9, 34 | 2D output pixels point | 2D point-filtered output pixels. |
| 9, 35 | 2D output pixels bilinear | 2D bilinear-filtered output pixels. |
| 9, 36 | 2D filter workload 16bit | 2D filtering workload for 16-bit formats. |
| 9, 37 | 2D filter workload 32bit | 2D filtering workload for 32-bit formats. |
| 9, 38 | tpa2tpc trans | Transactions between texture prefetch/address (TPA) and texture pipe/cache (TPC). |
| 9, 39 | L1 misses astc 1tile | L1 misses for ASTC requests of 1 tile. |
| 9, 40 | L1 misses astc 2tile | L1 misses for ASTC requests of 2 tiles. |
| 9, 41 | L1 misses astc 4tile | L1 misses for ASTC requests of 4 tiles. |
| 9, 42 | L1 5 L2 compress reqs | L1→L2 requests for compressed blocks. |
| 9, 43 | L1 5 L2 compress miss | Misses when requesting compressed blocks from L2. |
| 9, 44 | L1 bank conflict | Cycles/occurrences of L1 bank conflicts (structural hazard). |
| 9, 45 | L1 5 miss latency cycles | Total latency cycles for L1 misses. |
| 9, 46 | L1 5 miss latency trans | Number of L1-miss transactions sampled. |
| 9, 47 | quads constant multiplied | Quads using constant-multiply optimization/step (implementation-specific). |
| 9, 48 | frontend working cycles | Useful cycles in TP front-end (request/issue). |
| 9, 49 | L1 tag working cycles | Useful cycles in L1 tag pipeline. |
| 9, 50 | L1 data write working cycles | Useful cycles writing L1 data arrays. |
| 9, 51 | pre L1 decom working cycles | Useful cycles in pre-L1 decompression stage. |
| 9, 52 | backend working cycles | Useful cycles in TP back-end (filter/return). |
| 9, 53 | flag cache working cycles | Useful cycles in flag cache logic. |
| 9, 54 | L1 5 cache working cycles | Useful cycles in L1 cache pipeline overall. |
| 9, 55 | starve cycles SP | Cycles TP starved because SP isn’t issuing/feeding requests. |
| 9, 56 | starve cycles UCHE | Cycles TP starved because UCHE cannot accept/serve requests (credits/returns). |
| - | **Shader/Streaming Processor** | - |
| 10, 0 | busy cycles | Cycles SP is busy (any stage). |
| 10, 1 | ALU working cycles | Cycles ALU pipelines are executing ALU instructions. |
| 10, 2 | EFU working cycles | Cycles EFU (special function/extended function) units are executing. |
| 10, 3 | stall cycles VPC | Cycles SP stalled waiting for VPC inputs (varyings/params). |
| 10, 4 | stall cycles TP | Cycles SP stalled waiting for texture results. |
| 10, 5 | stall cycles UCHE | Cycles SP stalled waiting for UCHE/memory (loads/stores). |
| 10, 6 | stall cycles RB | Cycles SP stalled due to render backend backpressure (exports/targets). |
| 10, 7 | non execution cycles | Cycles SP not executing instructions (overhead, stalls, bubbles). |
| 10, 8 | wave contexts | Number of wave contexts created/active (waves resident). |
| 10, 9 | wave context cycles | Sum of cycles waves are resident (context occupancy). |
| 10, 10 | FS stage wave cycles | Cycles waves are in fragment stage. |
| 10, 11 | FS stage wave samples | Samples/occurrences of fragment-stage wave activity. |
| 10, 12 | VS stage wave cycles | Cycles waves are in vertex stage. |
| 10, 13 | VS stage wave samples | Samples/occurrences of vertex-stage wave activity. |
| 10, 14 | FS stage duration cycles | Total duration cycles for FS waves (lifetime sum). |
| 10, 15 | VS stage duration cycles | Total duration cycles for VS waves. |
| 10, 16 | wave ctrl cycles | Cycles spent in wave control (bookkeeping/control-flow handling). |
| 10, 17 | wave load cycles | Cycles loading waves (state/context load). |
| 10, 18 | wave emit cycles | Cycles emitting/launching waves. |
| 10, 19 | wave nop cycles | Cycles executing NOPs (bubbles). |
| 10, 20 | wave wait cycles | Cycles waves are waiting (dependencies/barriers). |
| 10, 21 | wave fetch cycles | Cycles fetching instructions (I-fetch). |
| 10, 22 | wave idle cycles | Cycles wave slots are idle (no wave scheduled). |
| 10, 23 | wave end cycles | Cycles spent ending/retiring waves. |
| 10, 24 | wave long sync cycles | Cycles stalled on long-latency sync events. |
| 10, 25 | wave short sync cycles | Cycles stalled on short-latency sync events. |
| 10, 26 | wave join cycles | Cycles spent on join/reconvergence operations. |
| 10, 27 | LM load instructions | Number of local-memory (shared/LMEM) load instructions. |
| 10, 28 | LM store instructions | Number of local-memory store instructions. |
| 10, 29 | LM atomics | Number of local-memory atomic operations. |
| 10, 30 | GM load instructions | Number of global-memory load instructions. |
| 10, 31 | GM store instructions | Number of global-memory store instructions. |
| 10, 32 | GM atomics | Number of global-memory atomic operations. |
| 10, 33 | VS stage tex instructions | Texture/sampler instructions executed in VS stage. |
| 10, 34 | VS stage EFU instructions | EFU instructions executed in VS stage. |
| 10, 35 | VS stage full ALU instructions | Full-precision ALU instructions executed in VS stage. |
| 10, 36 | VS stage half ALU instructions | Half-precision ALU instructions executed in VS stage. |
| 10, 37 | FS stage tex instructions | Texture/sampler instructions executed in FS stage. |
| 10, 38 | FS stage cflow instructions | Control-flow instructions executed in FS stage. |
| 10, 39 | FS stage EFU instructions | EFU instructions executed in FS stage. |
| 10, 40 | FS stage full ALU instructions | Full-precision ALU instructions executed in FS stage. |
| 10, 41 | FS stage half ALU instructions | Half-precision ALU instructions executed in FS stage. |
| 10, 42 | FS stage bary instructions | Barycentric/interpolation-related instructions in FS stage. |
| 10, 43 | VS instructions | Total VS instructions executed (all types). |
| 10, 44 | FS instructions | Total FS instructions executed (all types). |
| 10, 45 | addr lock count | Number of address lock/contention events (addressing/resource hazard). |
| 10, 46 | UCHE read trans | UCHE read transactions issued by SP. |
| 10, 47 | UCHE write trans | UCHE write transactions issued by SP. |
| 10, 48 | export VPC trans | Export transactions from SP to VPC (varying/pos outputs). |
| 10, 49 | export RB trans | Export transactions from SP to RB (color/depth outputs). |
| 10, 50 | pixels killed | Pixels killed/discarded in shader (discard/kill). |
| 10, 51 | icl1 requests | Instruction cache L1 requests. |
| 10, 52 | icl1 misses | Instruction cache L1 misses. |
| 10, 53 | HS instructions | Hull shader instructions executed. |
| 10, 54 | DS instructions | Domain shader instructions executed. |
| 10, 55 | GS instructions | Geometry shader instructions executed. |
| 10, 56 | CS instructions | Compute shader instructions executed. |
| 10, 57 | GPR read | General-purpose register file reads. |
| 10, 58 | GPR write | General-purpose register file writes. |
| 10, 59 | FS stage half EFU instructions | Half-precision EFU instructions in FS stage. |
| 10, 60 | VS stage half EFU instructions | Half-precision EFU instructions in VS stage. |
| 10, 61 | LM bank conflicts | Local-memory bank conflicts (shared memory structural hazard). |
| 10, 62 | tex control working cycles | Useful cycles in texture control pipeline within SP. |
| 10, 63 | load control working cycles | Useful cycles in load/store control pipeline. |
| 10, 64 | flow control working cycles | Useful cycles in flow-control (branch/reconvergence) pipeline. |
| 10, 65 | LM working cycles | Useful cycles in local-memory pipeline. |
| 10, 66 | dispatcher working cycles | Useful cycles in wave/warp dispatcher. |
| 10, 67 | sequencer working cycles | Useful cycles in instruction sequencer. |
| 10, 68 | low efficiency starved BY TP | Cycles of low efficiency caused by being starved on texture results. |
| 10, 69 | starve cycles HLSQ | Cycles SP starved because HLSQ didn’t provide work (no waves to run). |
| 10, 70 | non execution LS cycles | Non-execution cycles specifically in load/store subsystem. |
| 10, 71 | working EU | Cycles where at least one execution unit is working (active). |
| 10, 72 | any EU working | Samples/cycles indicating any EU active (often similar to 71 but different gating). |
| 10, 73 | working EU FS stage | Cycles EUs working on FS stage. |
| 10, 74 | any EU working FS stage | Samples/cycles of any EU active in FS stage. |
| 10, 75 | working EU VS stage | Cycles EUs working on VS stage. |
| 10, 76 | any EU working VS stage | Samples/cycles of any EU active in VS stage. |
| 10, 77 | working EU CS stage | Cycles EUs working on CS stage. |
| 10, 78 | any EU working CS stage | Samples/cycles of any EU active in CS stage. |
| 10, 79 | GPR read prefetch | GPR prefetch reads (speculative/early reads). |
| 10, 80 | GPR read conflict | Conflicts/hazards on GPR reads (port/bank conflict). |
| 10, 81 | GPR write conflict | Conflicts/hazards on GPR writes. |
| 10, 82 | GM load latency cycles | Total latency cycles waiting on global-memory loads. |
| 10, 83 | GM load latency samples | Number of global-memory load latency samples. |
| 10, 84 | executable waves | Number of waves eligible to execute (ready/runnable). |
| - | **Render backend** | - |
| 11, 0 | busy cycles | Cycles RB is busy. |
| 11, 1 | stall cycles HLSQ | Cycles RB stalled waiting for HLSQ/inputs. |
| 11, 2 | stall cycles fifo0 full | Cycles stalled because RB FIFO0 is full. |
| 11, 3 | stall cycles fifo1 full | Cycles stalled because RB FIFO1 is full. |
| 11, 4 | stall cycles fifo2 full | Cycles stalled because RB FIFO2 is full. |
| 11, 5 | starve cycles SP | Cycles RB starved waiting for SP exports (color/depth data). |
| 11, 6 | starve cycles LRZ tile | Cycles RB starved waiting for LRZ tile/mask info. |
| 11, 7 | starve cycles CCU | Cycles RB starved waiting for CCU returns/availability. |
| 11, 8 | starve cycles Z plane | Cycles RB starved on Z-plane data/dependency. |
| 11, 9 | starve cycles bary plane | Cycles RB starved on barycentric plane/interp dependency. |
| 11, 10 | Z workload | Depth (Z) processing workload units (implementation-defined). |
| 11, 11 | HLSQ active | Cycles/occurrences where HLSQ is actively feeding RB. |
| 11, 12 | Z read | Depth buffer read operations. |
| 11, 13 | Z write | Depth buffer write operations. |
| 11, 14 | C read | Color buffer read operations (blending/ROPs reading dest). |
| 11, 15 | C write | Color buffer write operations. |
| 11, 16 | total pass | Total depth/stencil tests passed (combined). |
| 11, 17 | Z pass | Z test passed count. |
| 11, 18 | Z fail | Z test failed count. |
| 11, 19 | S fail | Stencil test failed count. |
| 11, 20 | blended fxp components | Number of blended fixed-point components processed. |
| 11, 21 | blended fp16 components | Number of blended FP16 components processed. |
| 11, 22 | PS invocations | Pixel shader invocations reaching RB (fragments processed). |
| 11, 23 | 2D alive cycles | Cycles RB 2D/blit path is active. |
| 11, 24 | 2D stall cycles a2d | 2D path stall cycles due to a2d (2D accelerator interface) backpressure. |
| 11, 25 | 2D starve cycles src | 2D path starved waiting for source reads. |
| 11, 26 | 2D starve cycles SP | 2D path starved waiting for SP (if shader-assisted blits). |
| 11, 27 | 2D starve cycles dst | 2D path starved waiting for destination availability/returns. |
| 11, 28 | 2D valid pixels | Number of valid pixels processed by 2D path. |
| 11, 29 | 3D pixels | Number of 3D pixels/fragments processed by RB. |
| 11, 30 | blender working cycles | Useful cycles of blending hardware. |
| 11, 31 | zproc working cycles | Useful cycles of Z/stencil processing hardware. |
| 11, 32 | cproc working cycles | Useful cycles of color processing hardware. |
| 11, 33 | sampler working cycles | Useful cycles of RB sampler/resolve path (implementation-specific). |
| 11, 34 | stall cycles CCU color read | Cycles stalled waiting for CCU on color read returns. |
| 11, 35 | stall cycles CCU color write | Cycles stalled waiting for CCU on color write path. |
| 11, 36 | stall cycles CCU depth read | Cycles stalled waiting for CCU on depth read returns. |
| 11, 37 | stall cycles CCU depth write | Cycles stalled waiting for CCU on depth write path. |
| 11, 38 | stall cycles VPC | Cycles RB stalled due to VPC dependency/backpressure. |
| 11, 39 | 2D input trans | 2D path input transactions into RB. |
| 11, 40 | 2D output RB dst trans | 2D output transactions writing destination via RB. |
| 11, 41 | 2D output RB src trans | 2D output transactions reading source via RB. |
| 11, 42 | blended fp32 components | Number of blended FP32 components processed. |
| 11, 43 | color pix tiles | Number of color pixel tiles processed (tile-level color ops). |
| 11, 44 | stall cycles CCU | Cycles RB stalled due to CCU (generic, any reason). |
| 11, 45 | early Z arb3 grant | Grants from early-Z arbiter (channel 3) (depth-path scheduling). |
| 11, 46 | late Z arb3 grant | Grants from late-Z arbiter (channel 3). |
| 11, 47 | early Z skip grant | Early-Z “skip” grants (work skipped due to early-z optimization). |
| - | **VBIF** | - |
| 13, 34 | ??? | Undocumented VBIF counter (SoC/firmware dependent); typically related to external memory read/write/latency or QoS arbitration. |
| 13, 35 | ??? | Undocumented VBIF counter (SoC/firmware dependent); likely a traffic/credit/stall metric. |
| 13, 46 | ??? | Undocumented VBIF counter (SoC/firmware dependent); possibly read channel beats/requests by client class. |
| 13, 47 | ??? | Undocumented VBIF counter (SoC/firmware dependent); possibly write channel beats/requests by client class. |
| - | **Visibility Stream Compressor** | - |
| 23, 0 | busy cycles | Cycles VSC is busy. |
| 23, 1 | working cycles | Cycles VSC doing useful work (not stalled). |
| 23, 2 | stall cycles UCHE | Cycles VSC stalled waiting for UCHE/memory. |
| 23, 3 | eot num | Number of end-of-tile/end-of-transmission (EOT) events. |
| 23, 4 | input tiles | Number of input tiles processed by VSC. |
| - | **Cache and Compression Unit** | - |
| 24, 0 | busy cycles | Cycles CCU is busy. |
| 24, 1 | stall cycles RB depth return | Cycles CCU stalled returning depth data to RB (return path blocked). |
| 24, 2 | stall cycles RB color return | Cycles CCU stalled returning color data to RB. |
| 24, 3 | starve cycles flag return | Cycles CCU starved waiting for compression flag return data. |
| 24, 4 | depth blocks | Number of depth blocks processed (compressed block units). |
| 24, 5 | color blocks | Number of color blocks processed. |
| 24, 6 | depth block hit | Depth block cache hits in CCU. |
| 24, 7 | color block hit | Color block cache hits in CCU. |
| 24, 8 | partial block read | Partial block reads (sub-block accesses, read-modify-write scenarios). |
| 24, 9 | gmem read | GMEM reads performed by CCU. |
| 24, 10 | gmem write | GMEM writes performed by CCU. |
| 24, 11 | depth read flag0 count | Depth reads with compression flag state 0. |
| 24, 12 | depth read flag1 count | Depth reads with compression flag state 1. |
| 24, 13 | depth read flag2 count | Depth reads with compression flag state 2. |
| 24, 14 | depth read flag3 count | Depth reads with compression flag state 3. |
| 24, 15 | depth read flag4 count | Depth reads with compression flag state 4. |
| 24, 16 | depth read flag5 count | Depth reads with compression flag state 5. |
| 24, 17 | depth read flag6 count | Depth reads with compression flag state 6. |
| 24, 18 | depth read flag8 count | Depth reads with compression flag state 8 (often “uncompressed/clear/invalid” encoding). |
| 24, 19 | color read flag0 count | Color reads with compression flag state 0. |
| 24, 20 | color read flag1 count | Color reads with compression flag state 1. |
| 24, 21 | color read flag2 count | Color reads with compression flag state 2. |
| 24, 22 | color read flag3 count | Color reads with compression flag state 3. |
| 24, 23 | color read flag4 count | Color reads with compression flag state 4. |
| 24, 24 | color read flag5 count | Color reads with compression flag state 5. |
| 24, 25 | color read flag6 count | Color reads with compression flag state 6. |
| 24, 26 | color read flag8 count | Color reads with compression flag state 8. |
| 24, 27 | 2D RD req | 2D path read requests handled by CCU. |
| 24, 28 | 2D WR req | 2D path write requests handled by CCU. |
| - | **Low Resolution Z pass** | - |
| 25, 0 | busy cycles | Cycles LRZ unit is busy. |
| 25, 1 | starve cycles RAS | Cycles LRZ starved waiting for rasterizer input. |
| 25, 2 | stall cycles RB | Cycles LRZ stalled due to RB backpressure/dependency. |
| 25, 3 | stall cycles VSC | Cycles LRZ stalled due to VSC dependency/backpressure. |
| 25, 4 | stall cycles VPC | Cycles LRZ stalled due to VPC dependency/backpressure. |
| 25, 5 | stall cycles flag prefetch | Cycles stalled waiting for LRZ/CCU flag prefetch. |
| 25, 6 | stall cycles UCHE | Cycles stalled waiting on UCHE/memory. |
| 25, 7 | LRZ read | Number of LRZ buffer reads. |
| 25, 8 | LRZ write | Number of LRZ buffer writes/updates. |
| 25, 9 | read latency | Accumulated LRZ read latency (cycles). |
| 25, 10 | merge cache updating | Occurrences/cycles merge cache is updating (combining updates). |
| 25, 11 | prim killed BY maskgen | Primitives killed by mask generator (coverage/visibility). |
| 25, 12 | prim killed BY LRZ | Primitives killed by LRZ (occluded by low-res Z). |
| 25, 13 | visible prim after LRZ | Primitives deemed visible after LRZ test. |
| 25, 14 | full 8x8 tiles | Fully covered 8x8 tiles processed. |
| 25, 15 | partial 8x8 tiles | Partially covered 8x8 tiles processed. |
| 25, 16 | tile killed | Tiles rejected/killed by LRZ. |
| 25, 17 | total pixel | Total pixels considered in LRZ stage. |
| 25, 18 | visible pixel after LRZ | Pixels that remain visible after LRZ. |
| 25, 19 | fully covered tiles | Count of tiles fully covered by primitives. |
| 25, 20 | partial covered tiles | Count of partially covered tiles. |
| 25, 21 | feedback accept | LRZ feedback events accepted (feedback path success). |
| 25, 22 | feedback discard | LRZ feedback events discarded. |
| 25, 23 | feedback stall | Cycles stalled due to LRZ feedback path backpressure. |
| 25, 24 | stall cycles RB zplane | Cycles stalled waiting for RB on Z-plane related ops. |
| 25, 25 | stall cycles RB bplane | Cycles stalled waiting for RB on bary-plane related ops. |
| 25, 26 | stall cycles VC | Cycles stalled due to VC (visibility cache/collector) dependency (implementation-specific). |
| 25, 27 | RAS mask trans | Transactions of raster mask data between RAS and LRZ. |
| - | **CMP** | - |
| 26, 0 | cmpdecmp stall cycles arb | Cycles compress/decompress engine stalled due to arbiter contention. |
| 26, 1 | cmpdecmp vbif latency cycles | Total VBIF latency cycles seen by compress/decompress path. |
| 26, 2 | cmpdecmp vbif latency samples | Number of VBIF latency samples for compress/decompress path. |
| 26, 3 | cmpdecmp vbif read data CCU | VBIF read data beats/units for CCU via cmp/decmp path. |
| 26, 4 | cmpdecmp vbif write data CCU | VBIF write data beats/units for CCU via cmp/decmp path. |
| 26, 5 | cmpdecmp vbif read request | VBIF read requests issued by cmp/decmp block. |
| 26, 6 | cmpdecmp vbif write request | VBIF write requests issued by cmp/decmp block. |
| 26, 7 | cmpdecmp vbif read data | Total VBIF read data beats/units for cmp/decmp. |
| 26, 8 | cmpdecmp vbif write data | Total VBIF write data beats/units for cmp/decmp. |
| 26, 9 | cmpdecmp flag fetch cycles | Cycles spent fetching compression flags/metadata. |
| 26, 10 | cmpdecmp flag fetch samples | Number of flag fetch transactions sampled. |
| 26, 11 | cmpdecmp depth write flag1 count | Depth writes with compression flag state 1. |
| 26, 12 | cmpdecmp depth write flag2 count | Depth writes with compression flag state 2. |
| 26, 13 | cmpdecmp depth write flag3 count | Depth writes with compression flag state 3. |
| 26, 14 | cmpdecmp depth write flag4 count | Depth writes with compression flag state 4. |
| 26, 15 | cmpdecmp depth write flag5 count | Depth writes with compression flag state 5. |
| 26, 16 | cmpdecmp depth write flag6 count | Depth writes with compression flag state 6. |
| 26, 17 | cmpdecmp depth write flag8 count | Depth writes with compression flag state 8. |
| 26, 18 | cmpdecmp color write flag1 count | Color writes with compression flag state 1. |
| 26, 19 | cmpdecmp color write flag2 count | Color writes with compression flag state 2. |
| 26, 20 | cmpdecmp color write flag3 count | Color writes with compression flag state 3. |
| 26, 21 | cmpdecmp color write flag4 count | Color writes with compression flag state 4. |
| 26, 22 | cmpdecmp color write flag5 count | Color writes with compression flag state 5. |
| 26, 23 | cmpdecmp color write flag6 count | Color writes with compression flag state 6. |
| 26, 24 | cmpdecmp color write flag8 count | Color writes with compression flag state 8. |
| 26, 25 | cmpdecmp 2D stall cycles vbif req | 2D path stall cycles waiting to issue VBIF requests in cmp/decmp. |
| 26, 26 | cmpdecmp 2D stall cycles vbif WR | 2D path stall cycles on VBIF write path in cmp/decmp. |
| 26, 27 | cmpdecmp 2D stall cycles vbif return | 2D path stall cycles waiting for VBIF returns in cmp/decmp. |
| 26, 28 | cmpdecmp 2D RD data | 2D path read data beats/units through cmp/decmp. |
| 26, 29 | cmpdecmp 2D WR data | 2D path write data beats/units through cmp/decmp. |
| 26, 30 | cmpdecmp vbif read data UCHE ch0 | VBIF read data for UCHE channel 0 through cmp/decmp. |
| 26, 31 | cmpdecmp vbif read data UCHE ch1 | VBIF read data for UCHE channel 1 through cmp/decmp. |
| 26, 32 | cmpdecmp 2D output trans | 2D output transactions produced by cmp/decmp path. |
| 26, 33 | cmpdecmp vbif write data UCHE | VBIF write data for UCHE through cmp/decmp. |
| 26, 34 | cmpdecmp depth write flag0 count | Depth writes with compression flag state 0. |
| 26, 35 | cmpdecmp color write flag0 count | Color writes with compression flag state 0. |
| 26, 36 | cmpdecmp color write flagalpha count | Color writes for alpha plane/alpha flags (alpha-specific compression metadata). |
| 26, 37 | cmpdecmp 2D busy cycles | Cycles cmp/decmp hardware is busy on 2D operations. |
| 26, 38 | cmpdecmp 2D reorder starve cycles | Cycles 2D path starved due to reorder queue/engine constraints. |
| 26, 39 | cmpdecmp 2D pixels | Number of 2D pixels processed through cmp/decmp path. |

</details>
