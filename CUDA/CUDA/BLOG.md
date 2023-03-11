# xx

## blog

*  [CUDA 编程手册系列第二章: CUDA 编程模型概述](https://developer.nvidia.com/zh-cn/blog/cuda-model-intro-cn/)
    * 设备的Compute Capability由版本号表示，有时也称其“SM版本”。该版本号标识GPU硬件支持的特性，并由应用程序在运行时使用，以确定当前GPU上可用的硬件特性和指令。
    * Compute Capability包括一个主要版本号X和一个次要版本号Y，用X.Y表示
    * 主版本号相同的设备具有相同的核心架构。设备的主要修订号是8，为NVIDIA Ampere GPU的体系结构的基础上,7基于Volta设备架构,6设备基于Pascal架构,5设备基于Maxwell架构,3基于Kepler架构的设备,2设备基于Fermi架构,1是基于Tesla架构的设备。
    * 注意:特定GPU的计算能力版本不应与CUDA版本(如CUDA 7.5、CUDA 8、CUDA 9)混淆，CUDA版本指的是CUDA软件平台的版本。CUDA平台被应用开发人员用来创建运行在许多代GPU架构上的应用程序，包括未来尚未发明的GPU架构。尽管CUDA平台的新版本通常会通过支持新的GPU架构的计算能力版本来增加对该架构的本地支持，但CUDA平台的新版本通常也会包含软件功能。
    * 从CUDA 7.0和CUDA 9.0开始，不再支持Tesla和Fermi架构。


* [技术博客: Ken He](https://developer.nvidia.com/zh-cn/blog/author/ken-he/)
  * 相当不错的官方博客，可以细看；
  * CUDA/TENSORRT

* [Matching CUDA arch and CUDA gencode for various NVIDIA architectures](https://arnon.dk/matching-sm-architectures-arch-and-gencode-for-various-nvidia-cards/)
  * 各种GPU架构的最优配置，几句有参考价值；

* [CUDA架构及对应编译参数](https://www.cnblogs.com/phillee/p/12049208.html)

