
## References

1. [Modern Mobile Rendering at HypeHype (2023)](https://enginearchitecture.realtimerendering.com/downloads/reac2023_modern_mobile_rendering_at_hypehype.pdf)
2. [Mobile Rendering Architecture](https://advances.realtimerendering.com/s2023/AaltonenHypeHypeAdvances2023.pdf)

## Notes

* Min spec 2023: 95% of our users have Vulkan 1.0 + Android 9, 2GB memory (1.4GB usable). [1]
```
	**Android**
	OS: Android 9
	CPU: 32 bit + 64 bit
	ARM: Mali-G series (Bifrost)
	Qualcomm: Adreno 500 series
	PowerVR: 8000 series (Rogue)
	6 years old hardware
	**Apple**
	OS: iOS 13
	CPU: 64 bit
	iPhone 6s (A9) / iPad Air 2 (A8X)
	7 years old hardware
```

* Some operation performance: [1]
	- Fast generic memory load/store - Mobile: 16KB uniform buffers! SSBOs are slow!
	- Fast & big groupshared memory - Mobile: Small or emulated
	- Fast local/global atomics and wave intrinsics - Mobile: Wave intrinsic support <10%
	- Big register files and big generic caches - Mobile: Avoid complex shaders
	- 64 bit atomics - Mobile: No 64 bit integers at all!

* One FS warp can contain multiple primitives. [2]
* Push constants emulated on some GPUs. [2]
* The reason is that instance ID is dynamic offset. GPUs pack multiple instances in the same vertex wave, meaning that all data indexed by instance ID must use vector registers and vector loads. This is a lot of extra register bloat for loading 4x4 matrices and similar. [2]
* Base instance on the other hand is a static per-draw offset. Every lane loads from the same location. This means that compilers can scalar code paths and/or use fast constant buffer hardware. [2]
* Specialization constants: Poor support on some devices: Mostly low end mobile; Dead branch elimination appears to work, but loops based on SCs don’t flatten. [2]
