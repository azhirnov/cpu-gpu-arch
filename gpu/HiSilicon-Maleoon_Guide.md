
## References

1. [Best Practice in Maleoon GPUs](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-maleoon-gpu-best-practices)


## Notes

* enables the Single InstanceID optimization: [1]
	- This optimization ensures that the InstanceID of each group of tasks are the same when the tasks are running. In this way, the load mem of each group of tasks can obtain the corresponding data of the entire group by executing the first thread once.
	- Further, if the size of all uniforms of the shader does not exceed 1024 bytes, the uniform buffer can be placed in the constant register.
	- When calculating the uniform buffer index value, do not use InstanceID in complex nesting.

## Notes

* YUV texture does not support anisotropic filtering.

* HEBC lossless render target compression. Requirements: [1]
	- 2D image
	- usage: color/depth attachment, sampled, transfer src/dst, input_attachment
	- formats: all 16bit, all 32bit, R16/RG16/RGB16/RGBA16 U/I/F, R32 U/I/F, D16, D24, D32, D24S8, D32S8

* Can convert some uniform data into the register of the shader core to reduce frequent uniform data load. [1]
	- Use a maximum of 1024 bytes of uniform data in a shader.
	- Avoid unnecessary uniform dynamic indexing.
	- Do not merge irrelevant dynamic data into uniform vector or uniform matrix.

* Uniform Expressions. [1]
	- The Maleoon GPU can complete some scalar operations on the coprocessor before the draw call is executed, mainly including calculation of expressions related to uniform and immediate. The calculation result is provided for the entire draw call. Therefore, the uniform expressions in the Maleoon GPU do not occupy the running time of the GPU.

