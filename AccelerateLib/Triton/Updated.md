## [Power Your AI Inference with New NVIDIA Triton and NVIDIA TensorRT Features](https://developer.nvidia.com/blog/power-your-ai-inference-with-new-nvidia-triton-and-nvidia-tensorrt-features/) (blog time: Mar 23, 2023)

* ### [Native Python support with PyTriton](https://github.com/triton-inference-server/pytriton)
  * This approach eliminates the need to set up model repositories and convert model formats. You can use existing inference pipeline code without modification. To try it, visit [triton-inference-server/pytriton](https://github.com/triton-inference-server/pytriton) on GitHub. 

* ### [Model analyzer](https://github.com/triton-inference-server/model_analyzer/tree/main/docs)
  * Model analyzer is a tool that helps find the best NVIDIA Triton model configuration—like batch size, model concurrency, and precision—to deploy efficient inference. 
  * Now, in addition to standalone models to support modern inference workloads with preprocessing and postprocessing requirements, model analyzer supports model ensembles (also called model pipelines) and multiple model analysis. You can run the model analyzer for the entire ML pipeline. 
* ### [NVIDIA Triton Management Service](https://developer.nvidia.com/tms-early-access)
  * NVIDIA Triton Management Service provides model orchestration functionality for efficient multimodel inference. This functionality, which runs as a production service, loads models on demand and unloads models when not in use. 
  * It efficiently allocates GPU resources by placing as many models as possible on a single GPU server and helps to optimally group models from different frameworks for efficient memory use. It now supports autoscaling of NVIDIA Triton instances based on high utilization from inference and encrypted (AES-256) communication with applications. 