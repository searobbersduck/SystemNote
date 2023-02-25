


## BLOG

1. [GPT-3难以复现，为什么说PyTorch走上了一条“大弯路”？](https://www.sohu.com/a/467324131_115128)
   * 据 NVIDIA 估算，如果要训练GPT-3 ，即使单个机器的显存/内存能装得下，用 8 张 V100 的显卡，训练时长预计要 36 年；即使用 512 张 V100 ，训练也需要将近 7 个月；如果拥有 1024 张 80GB A100， 那么完整训练 GPT-3 的时长可以缩减到 1 个月。
   * 除去硬件资源这个经济问题，在技术层面，意味着训练大模型一定是一个分布式问题。
   * 根据目前业界已有的分布式训练方案，即便你是一位非常优秀的数据科学家，知晓并能解决 Transformer 相关的所有算法问题，但如果你不知道如何解决分布式训练时上百台服务器之间的通信、拓扑、模型并行、流水并行等问题，你甚至都无法启动这次训练。
   * 开源的 GPT 模型库主要是 NVIDIA开发的 Megatron-LM 和经过微软深度定制开发的 DeepSpeed，其中，DeepSpeed 的模型并行等内核取自 Megatron，它们都是专门为支持 PyTorch 分布式训练 GPT 而设计。
   * NVIDIA 介绍了分布式训练超大规模模型的三种必须的并行技术：
     * 数据并行（Data Parallelism）
     * 模型并行（Tensor Model Parallelism）
     * 流水并行（Pipeline Model Parallelism）
   * 对于 1T 规模的模型，NVIDIA 一共使用了 384 台 DGX-A100 机器（每台装有 8 张 80GB A100 GPU），机器内部各 GPU 间使用超高速 NVLink 和 NVSwitch 互联，每台机器装有 8 个 200Gbps 的 InfiniBand (IB) 网卡，可以说是硬件集群顶配中的顶配。
   * 那么，这些机器是如何协同工作的？GPT 网络是由很多层 Transformer Layer 组成，每一层内部是一个由多层 MLP 和 attention 机制组成的子图，对于参数规模 1T 的 GPT 而言就有 128 层的 Transformer Layer，这个超大超深的网络被分割成了 64 个 stage （阶段），每个 stage 跑在 6 台 DGX-A100 上，其中 6 台机器之间进行数据并行，每台机器内部的 8 张卡之间做模型并行，整个集群的 3072 张 A100 按照机器拓扑被划分成了 [6 x 8 x 64] 的矩阵，同时使用数据并行 & 模型并行 & 流水并行进行训练。


2. [GPT模型介绍并且使用pytorch实现一个小型GPT中文闲聊系统](https://blog.csdn.net/weixin_44599230/article/details/124103879)
3. [Deploying a 1.3B GPT-3 Model with NVIDIA NeMo Megatron](https://developer.nvidia.com/blog/deploying-a-1-3b-gpt-3-model-with-nvidia-nemo-megatron/)
4. [分布式训练——Colossal AI](https://colossalai.org/zh-Hans/docs/concepts/distributed_training)
5. [Build a GitHub support bot with GPT3, LangChain, and Python](https://dagster.io/blog/chatgpt-langchain)
6. [狂飙的ChatGPT，为什么是OpenAI最先做出来？](https://www.huxiu.com/article/791645.html)
   * 在《纽约时报》的报道中，OpenAI发布ChatGPT还有另外一个理由：担心对手公司可能会在GPT-4 前发布他们的人工智能聊天机器人，因此要抢先发布。
   * 大模型背后离不开大数据、大算力。GPT-2用于训练的数据取自于Reddit上高赞的文章，数据集共有约800万篇文章，累计体积约40G；GPT-3模型的神经网络是在超过45TB的文本上进行训练的，数据相当于整个维基百科英文版的160倍。***这个45T不是高质量文本。***
   * 在算力方面，GPT-3.5在微软Azure AI超算基础设施（由V100GPU组成的高带宽集群）上进行训练，总算力消耗约3640PF-days（即每秒一千万亿次计算，运行3640天）。
   * 著名风投机构A16Z将生成式AI市场分成了三层：
     * 应用层：将第三方API或自有模型集成到面向用户的产品中，比如AI绘画应用Jasper、Midjourney；
     * 模型层：为应用层提供能力，比如闭源的GPT-3，或者开源的Stable diffusion；
     * 基础设施层：为生成人工智能模型运行培训和推断工作负载的云平台和硬件制造商。
7. [大模型训练一次200-1200万美元！ChatGPT多烧钱？](https://wallstreetcn.com/articles/3681850)

8. [NVIDIA Merlin Distributed-Embeddings轻松快速训练TB 级推荐模型](https://developer.nvidia.com/zh-cn/blog/fast-terabyte-scale-recommender-training-made-easy-with-nvidia-merlin-distributed-embeddings/)
9. [ChatGPT到底需要多少算力？未来的GPT-4还有指数型上升](https://xuangubao.cn/article/1023819)
10. [AI与城市｜Midjourney：建筑版ChatGPT设计的超现实世界 ](https://www.sohu.com/a/638649687_121123925)


<br><br>

## AGI

1. [通向AGI之路：大型语言模型（LLM）技术精要](https://zhuanlan.zhihu.com/p/597586623)



<br><br>

## PROMPT

1. [最新综述：基于语言模型提示学习的推理](https://posts.careerengine.us/p/63b65f47aed7e93d56c43faf?from=latestPostSidePanel)
2. [有了Chain of Thought Prompting，大模型能做逻辑推理吗？](https://zhuanlan.zhihu.com/p/589087074)
3. [谷歌提出Flan-T5，一个模型解决所有NLP任务](https://cloud.tencent.com/developer/article/2208141)

4. [Multimodal Chain-of-Thought Reasoning in Language Models]()


<br><br>

## PRETRAINED

1. [GLM-130B: An Open Bilingual Pre-Trained Model](https://github.com/THUDM/GLM-130B)
  * [GLM-130B：开源的双语预训练模型](https://models.aminer.cn/glm-130b/)
    * GLM-130B 是一个开源开放的双语（中文和英文）双向稠密模型，拥有 1300 亿参数，模型架构采用通用语言模型（GLM1）。它旨在支持在一台 A100（40G * 8） 或 V100（32G * 8）服务器上对千亿规模参数的模型进行推理。截至 2022 年 7 月 3 日，GLM-130B 已完成 4000 亿个文本标识符（中文和英文各 2000 亿）的训练；
    * 快速推理：支持用一台 A100 服务器使用 SAT 和 FasterTransformer 进行快速推理（提速最高可达 2.5 倍）。

2. [LLaMA: Open and Efficient Foundation Language Models](https://research.facebook.com/publications/llama-open-and-efficient-foundation-language-models/)
   * github: [facebookresearch/llama](https://github.com/facebookresearch/llama)
   * [这是Meta版ChatGPT雏形？开源、一块GPU就能跑，1/10参数量打败GPT-3](https://redian.news/wxnews/284622)
   * 


<br>

***

<br>


## Inference


1. [FlexGen](https://github.com/FMInference/FlexGen)
   * [跑ChatGPT体量模型，从此只需一块GPU：加速百倍的方法来了](https://www.51cto.com/article/747106.html)

<br>

***

<br>

## ECONOMICS

1. [The Economics of Large Language Models](https://sunyan.substack.com/p/the-economics-of-large-language-models)