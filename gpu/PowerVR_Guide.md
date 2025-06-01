
## References

1. [PowerVR Performance Recommendations (2021)](https://web.archive.org/web/20220514055613/http://cdn.imgtec.com/sdk-documentation/PowerVR_Performance_Recommendations.pdf), [[backup](../pdf/PowerVR-Performance_Recommendations.pdf)]
2. [PowerVR Hardware Architecture Overview for Developers (2015)](https://powervr-graphics.github.io/WebGL_SDK/WebGL_SDK/Documentation/Architecture%20Guides/PowerVR%20Hardware.Architecture%20Overview%20for%20Developers.pdf)
3. [PVRTune Counter List and Description (2018)](https://cdn.imgtec.com/sdk-documentation/PVRTune.Counter%20List%20and%20Description.pdf), [[backup](../pdf/PowerVR-PVRTune_Counter_List_and_Description.pdf)]
4. [Introduction to PowerVR for Developers (2021)](https://imagination-technologies-cloudfront-assets.s3.eu-west-1.amazonaws.com/website-files/documents/Introduction_to_PowerVR_for_Developers.pdf?dlm-dp-dl-force=1&dlm-dp-dl-nonce=5021498b5e), [backup](../pdf/PowerVR-Introduction_to_PowerVR_for_Developers.pdf)
5. [Architecture Overview (2017)](https://docs.imgtec.com/starter-guides/powervr-architecture/html/architecture-overview-index.html), [[backup](../pdf/PowerVR-Hardware.Architecture+Overview+for+Developers.pdf)]
6. [PowerVR Low Level GLSL Optimisation (2017)](https://web.archive.org/web/20220511080902/http://cdn.imgtec.com/sdk-documentation/PowerVR%20Low%20level%20GLSL%20Optimisation.pdf), [[backup](../pdf/PowerVR-Low-level-GLSL-Optimisation.pdf)]
7. [PowerVR Instruction Set Reference (2020)](https://web.archive.org/web/20200923012922/https://cdn.imgtec.com/sdk-documentation/PowerVR+Instruction+Set+Reference.pdf), [[backup](../pdf/PowerVR-Instruction+Set+Reference.pdf)]
8. [Rendering Roblox Vulkan Optimisations on PowerVR](https://ubm-twvideo01.s3.amazonaws.com/o1/vault/gdc2020/presentations/ImaginationTechnologies_Rendering_Roblox_Vulkan_Alhuwalia_Maya_slides.pdf)


## Notes


* With PowerVR TBDR, Hidden Surface Removal (HSR) will completely remove overdraw regardless of draw call submission order. [4]
* Do Not Use Depth Pre-pass. Depth pre-pass is redundant on deferred rendering architectures. [4]

* With the Hidden Surface Removal (HSR) feature on PowerVR hardware it is not necessary to submit geometry in depth-order to reduce overdraw. By freeing applications from this restriction they can focus on sorting draws by render state, ensuring state changes are minimised. [4]

* Rasterization and pixel colouring are performed on a per-tile basis with the following steps: [4]
	1. When a tile operation begins, the corresponding tile list is retrieved from the Parameter Buffer (PB) to identify the screen-space primitive data that needs to be fetched.
	2. The Image Synthesis Processor (ISP) fetches the primitive data and performs Hidden Surface Removal (HSR), along with depth and stencil tests. The ISP only fetches screen-space position data for the geometry within the tile.
	3. The Tag Buffer contains information about which triangle is on top for each pixel.
	4. The Texture and Shading Processor (TSP) then applies colouring operations, like fragment shaders, to the visible pixels.
	5. Alpha testing and subsequently alpha blending is then carried out.
	6. Once the tile’s render is complete, the colour data is written to the frame buffer in system memory.

* PowerVR shader engine: [4]
	- It is hardware-managed and load-balanced by using a data driven execution model to ensure the highest possible utilisation efficiency.
	- This approach schedules tasks based on data availability, and enables switching between independent processing tasks to ensure that data dependency stalls are avoided at all costs.




### PowerVR Rogue (vector arch?)

* PowerVR Rogue architecture delivers a variety of options for executing multiple instructions in the USC ALU pipeline within a single cycle. [6]
	- It is possible to execute two F16 SOP instructions plus the F32 <-> F16 conversions, plus the mov/output/pack instruction in one cycle.
	- One could execute an FP32 MAD and an FP32/INT32 MAD/UNPACK instruction plus a test (conditional) instruction plus the mov/output/pack instruction in one cycle.
	- If there is bitwise work to be done, it is possible to issue a bitwise SHIFT/COUNT, a bitwise logical operation, a bitwise shift, a test, and the mov/output/pack instructions in one cycle.
	- It is also possible to execute a single complex operation (ie. rcp) and a mov/output/pack instruction in one cycle.
	- One can execute an interpolate/sample instruction plus the usual mov/output/pack instruction in one cycle

* Writing expressions in MAD form. Use the MAD form results in a 50% cycle cost reduction. [6]
* Division. It is usually beneficial to write division math in reciprocal form. [6]
* Rcp/rsqrt/sqrt: [6]
	- rcp, rsqrt - 1 cycle
	- sqrt - 2 cycles
* Abs/Neg/Saturate: [6]
	- abs() and neg() are free if they are used on an input to an operation.<br/>
	  `abs(t.x) * abs(t.y)` faster than `abs(t.x * t.y)`<br/>
	  `dot(-t.xyz, t.yzx)` faster than `-dot(t.xyz, t.yzx)`<br/>
	  but `-normalize(t.xyz)` faster than `normalize(-t.xyz)` because `normalize` decomposed into multiple instructions.
	- saturate() on the other hand turns into a free modifier when used on the output of an operation.<br/>
	  `clamp(1.0 - t.x, 0.0, 1.0)` faster than `1.0 - clamp(t.x, 0.0, 1.0)`
	- saturate() is not free when used on a texture sampling output, or on a complex instruction output.
	- It is also beneficial to use clamp(…, 0.0, 1.0) instead of min(…, 1.0) and max(…, 0.0. This changes test instruction to a saturate modifier.
* Exp/Log: [6]
	- exp2, log2 - 1 cycle
	- exp, log - 2 cycles
	- pow - 3 cycles
* Sin/Cos/Sinh/Cosh: [6]
	- sin/cos - 4 cycles
	- sinh/cosh - 3 cycles
* Asin/Acos/Atan: [6]
	- Asin - 67 cycles
	- Acos - 79 cycles
	- Atan - 12 cycles
* vector x matrix: [6]
	- 4x4 - 8 cycles
	- 3x3 - 4 cycles

* Optimal work-group size on PowerVR is 32. [8]

