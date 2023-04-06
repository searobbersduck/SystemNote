# [NVIDIA Deep Learning TensorRT Documentation](https://docs.nvidia.com/deeplearning/tensorrt/developer-guide/index.html#types-precision)

pdf: [NVIDIA TensorRT](https://docs.nvidia.com/deeplearning/tensorrt/pdf/TensorRT-Developer-Guide.pdf)

<br>

***

<br>

**错误**

```
---------------------------------------------------------------------------
ModuleNotFoundError                       Traceback (most recent call last)
Cell In[19], line 1
----> 1 from cuda import cuda

ModuleNotFoundError: No module named 'cuda'
```

**解决方案**

```
# ref: https://nvidia.github.io/cuda-python/install.html

pip install cuda-python
```


<br>

***

<br>


**错误**
```
---------------------------------------------------------------------------
LogicError                                Traceback (most recent call last)
Cell In[21], line 15
     13 if engine.binding_is_input(binding):
     14     input_buf = np.ascontiguousarray(resized_img)
---> 15     input_mem = cuda.mem_alloc(resized_img.nbytes)
     16     bindings.append(int(input_mem))
     17 else:

LogicError: explicit_context_dependent failed: invalid device context - no currently active context?
```

**解决方案**

```
# ref: https://stackoverflow.com/questions/60372729/get-logicerror-explicit-context-dependent-failed-invalid-device-context-no

import pycuda.autoinit
```

<br>

***

<br>


**错误**
```
---------------------------------------------------------------------------
LogicError                                Traceback (most recent call last)
Cell In[19], line 27
     25 context.execute_async_v2(bindings=bindings, stream_handle=stream.handle)
     26 cuda.memcpy_dtoh_async(output_buf, output_mem, stream)
---> 27 stream.synchronize()

LogicError: cuStreamSynchronize failed: an illegal memory access was encountered
```

**解决方案**

```
#ref: https://github.com/NVIDIA/DALI/issues/4163


I found the reason, because the model needs float type, my dali data output is int.

```


<br>

***

<br>

### [Why does a TensorRT engine need to "warmUp" to get accurate inference profiling?](https://stackoverflow.com/questions/75563420/why-does-a-tensorrt-engine-need-to-warmup-to-get-accurate-inference-profiling)
* GPU could be in idle mode and the driver needs some time to go to an acceptable performance mode for profiling. You could use nvidia-smi to see the current mode.
* on some configuration, the driver is not in persistant mode and should be loaded when calling the first CUDA function
* in some cases, the driver needs to compile the PTX code found in the executable to get the BIN corresponding to the target architecture.


<br>

***

<br>

ref: https://github.com/NVIDIA/TensorRT/blob/main/quickstart/SemanticSegmentation/tutorial-runtime.ipynb