
## References

* [A5xx enums](https://github.com/freedreno/envytools/blob/master/registers/adreno/a5xx.xml)
* [A6xx enums](https://github.com/freedreno/envytools/blob/master/registers/adreno/a6xx.xml)

## Notes

**RBBM** - Render backend ***(bus/busy?) manager ?<br/>
**PFP** - Prefetch Parser<br/>
**ME** - Microcode Engine, handles most **PM4** commands.<br/>
**SQE** - a6xx+ replacement for **PFP**/**ME**. This is the microcontroller that runs the microcode which actually processes the command stream and writes to the hardware registers.<br/>
**ROQ** - **DMA** engine used by the **SQE** for reading memory, with some prefetch buffering.<br/>
**DMA** - Direct memory access.<br/>
**TSE** - Triangle Setup Engine<br/>
**RAS** - Rasterizer. Responsible for generating PS invocations from primitives, also does **LRZ**.<br/>
**vsd** - ?<br/>
**HLSQ** - High Level Sequencer. Manages state for the **SP**s, batches up PS invocations between primitives, is involved in preemption.<br/>
**VBIF** - ?<br/>
**VFD** - Vertex Fetch and Decode.<br/>
**VPC** - Varying/Position Cache. Hardware block that stores shaded vertex data for primitive assembly.<br/>
**UCHE** - Unified L2 cache. Cache behind the vertex fetch, **VSC** writes, texture L1, **LRZ**, and storage image accesses. Misses and flushes access system memory.<br/>
**RBuffer** - ?<br/>
**PC** - ?<br/>
**LRZ** - Low resolution Z. A low resolution area of the depth buffer that can be initialized during the binning pass to contain the worst-case (farthest) Z values in a block, and then used to early reject fragments during rasterization.<br/>
**maskgen** - ?<br/>
**SP** - shader processor<br/>
**GMEM** - on-chip memory, used to store attachments during tiled rendering<br/>
**VSC** - Visibility Stream Compressor<br/>
**EFU** - Elementary Function Unit ?. The EFU will have all the necessary instructions to speed up calculations and 3D rendering. (sin, cos, arctan, dot, rasterization, Min / Max, Clip, Culling , Sorting etc etc).<br/>
**wave** - warp, 32/64<br/>
**GM** - gmem ?<br/>
**GPR** - (mem/cache) ?<br/>
**LM** - load manager (load/store/atomic) ?<br/>
**PM4** - AMD Radeon’s command packet format.<br/>
**TP** - Texture Processor.<br/>
**CCU** - Color Cache Unit. Separate cache used by 2D blits and sysmem render target access (and also for resolves to system memory when in **GMEM** mode).<br/>
**PVS** - Primitive Visibility Stream.<br/>
**FE** - Front End. Index buffer and vertex attribute fetch cluster. Includes **PC**, **VFD**, **VPC**.<br/>
**PC_VS** - Cluster where varyings are read from VPC and assembled into primitives to feed **RAS**.<br/>
**VS** - Vertex Shader. Responsible for generating VS/GS/tess invocations.<br/>
**RB** - Render Backend. Performs both early and late Z testing, blending, and attachment stores of output of the PS.<br/>
**draw 2D** - blit, fullscreen post process without TBDR ?<br/>
**draw 3D** - TBDR pass ?<br/>


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
RAS: prim killed invisilbe

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

```
group | counter, packed GC, name
0|0, 0		Command Parser: always count
0|1, 1		Command Parser: busy gfx core idle
0|2, 2		Command Parser: busy cycles
0|3, 3		Command Parser: pfp idle
0|4, 4		Command Parser: pfp busy working
0|5, 5		Command Parser: pfp stall cycles any
0|6, 6		Command Parser: pfp starve cycles any
0|7, 7		Command Parser: pfp icache miss

1|0, 256	RBBM: always count
1|1, 257	RBBM: always ON
1|2, 258	RBBM: TSE busy

2|0, 512	PC: busy cycles
2|1, 513	PC: working cycles
2|2, 514	PC: stall cycles VFD
2|3, 515	PC: stall cycles TSE
2|4, 516	PC: stall cycles VPC
2|5, 517	PC: stall cycles UCHE
2|6, 518	PC: stall cycles tess
2|7, 519	PC: stall cycles TSE only

3|0, 768	VFD: busy cycles
3|1, 769	VFD: stall cycles UCHE
3|2, 770	VFD: stall cycles VPC alloc
3|3, 771	VFD: stall cycles miss VB
3|4, 772	VFD: stall cycles miss Q
3|5, 773	VFD: stall cycles SP info
3|6, 774	VFD: stall cycles SP attr
3|7, 775	VFD: stall cycles vfdp VB

4|0, 1024	High Level SeQuencer: busy cycles
4|1, 1025	High Level SeQuencer: stall cycles UCHE
4|2, 1026	High Level SeQuencer: stall cycles SP state
4|3, 1027	High Level SeQuencer: stall cycles SP FS stage
4|4, 1028	High Level SeQuencer: UCHE latency cycles
4|5, 1029	High Level SeQuencer: UCHE latency count
4|6, 1030	High Level SeQuencer: FS stage 32 waves
4|7, 1031	High Level SeQuencer: FS stage 64 waves

5|0, 1280	VPC: busy cycles
5|1, 1281	VPC: working cycles
5|2, 1282	VPC: stall cycles UCHE
5|3, 1283	VPC: stall cycles VFD wack

6|0, 1536	Triangle Setup Engine: busy cycles
6|1, 1537	Triangle Setup Engine: clipping cycles
6|2, 1538	Triangle Setup Engine: stall cycles RAS
6|3, 1539	Triangle Setup Engine: stall cycles LRZ baryplane

7|0, 1792	RAS: busy cycles
7|1, 1793	RAS: supertile active cycles
7|2, 1794	RAS: stall cycles LRZ
7|3, 1795	RAS: starve cycles TSE

8|0, 2048	Unified L2 Cache: busy cycles
8|1, 2049	Unified L2 Cache: stall cycles VBIF
8|2, 2050	Unified L2 Cache: VBIF latency cycles
8|3, 2051	Unified L2 Cache: VBIF latency samples
8|4, 2052	Unified L2 Cache: VBIF read beats TP
8|5, 2053	Unified L2 Cache: VBIF read beats VFD
8|6, 2054	Unified L2 Cache: VBIF read beats HLSQ
8|7, 2055	Unified L2 Cache: VBIF read beats LRZ

9|0, 2304	Texture Processor: busy cycles
9|1, 2305	Texture Processor: stall cycles UCHE
9|2, 2306	Texture Processor: latency cycles
9|3, 2307	Texture Processor: latency trans
9|4, 2308	Texture Processor: flag cache request samples
9|5, 2309	Texture Processor: flag cache request latency
9|6, 2310	Texture Processor: L1 cacheline requests
9|7, 2311	Texture Processor: L1 cacheline misses

a|0, 2560	Shader/Streaming Processor: busy cycles
a|1, 2561	Shader/Streaming Processor: ALU working cycles
a|2, 2562	Shader/Streaming Processor: EFU working cycles
a|3, 2563	Shader/Streaming Processor: stall cycles VPC
a|4, 2564	Shader/Streaming Processor: stall cycles TP
a|5, 2565	Shader/Streaming Processor: stall cycles UCHE
a|6, 2566	Shader/Streaming Processor: stall cycles RB
a|7, 2567	Shader/Streaming Processor: scheduler non working
a|8, 2568	Shader/Streaming Processor: wave contexts
a|9, 2569	Shader/Streaming Processor: wave context cycles
a|a, 2570	Shader/Streaming Processor: FS stage wave cycles
a|b, 2571	Shader/Streaming Processor: FS stage wave samples

b|0, 2816	RB: busy cycles
b|1, 2817	RB: stall cycles CCU
b|2, 2818	RB: stall cycles HLSQ
b|3, 2819	RB: stall cycles fifo0 full
b|4, 2820	RB: stall cycles fifo1 full
b|5, 2821	RB: stall cycles fifo2 full
b|6, 2822	RB: starve cycles SP
b|7, 2823	RB: starve cycles LRZ tile

c|1, 3073	???

d|0, 3328	VBIF: axi read requests ID 0
d|1, 3329	VBIF: axi read requests ID 1
d|2, 3330	VBIF: axi read requests ID 2
d|55, 3413	VBIF: axi data beats total

e|0, 3584	???
e|1, 3585	???
e|2, 3586	???

17|0, 5888	VSC: busy cycles
17|1, 5889	VSC: working cycles

18|0, 6144	Cache and Compression Unit: busy cycles
18|1, 6145	Cache and Compression Unit: stall cycles RB depth return
18|2, 6146	Cache and Compression Unit: stall cycles RB color return
18|3, 6147	Cache and Compression Unit: starve cycles flag return

19|TODO
```
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
RAS: prim killed invisilbe
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

```
TODO
```
</details>
