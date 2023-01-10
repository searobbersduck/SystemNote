# Nsight

<br>

## Nsight Systems

1. [NVIDIA Nsight Systems](https://developer.nvidia.com/nsight-systems)
   * 此链接请具体参见原文
   * key features
     * Visualize CPU-GPU interactions
       * Nsight Systems latches on to a target application to expose GPU and CPU activity, events, annotations, throughput, and performance metrics in a chronological timeline. With low overhead, this data can be visualized accurately and in parallel for ease of understanding. GPU workloads are further correlated with in-application CPU events, allowing for performance blockers to be easily identified and remedied.
       * Nsight Systems 锁定目标应用程序，以按时间顺序显示 GPU 和 CPU 活动、事件、注释、吞吐量和性能指标。 通过低开销，可以准确并行地可视化此数据，以便于理解。 GPU 工作负载与应用程序内 CPU 事件进一步相关，从而可以轻松识别和修复性能阻塞因素。
     * Track GPU activity
       * To further explore the GPU, toggling on GPU Metrics Sampling will plot low-level input/output (IO) activity such as PCIe throughput, NVIDIA NVLink®, and dynamic random-access memory (DRAM) activity. GPU Metrics Sampling also exposes SM utilization, Tensor Core activity, instruction throughput, and warp occupancy. Every workload and their CPU origin can be readily tracked to support performance tuning.
       * 为了进一步探索 GPU，打开 GPU 指标采样将绘制低级输入/输出 (IO) 活动，例如 PCIe 吞吐量、NVIDIA NVLink® 和动态随机存取存储器 (DRAM) 活动。 GPU Metrics Sampling 还公开了 SM 利用率、Tensor Core 活动、指令吞吐量和 warp 占用率。 可以轻松跟踪每个工作负载及其 CPU 来源，以支持性能调整。
     * Trace GPU workloads
       * For compute tasks, Nsight Systems supports investigating the CUDA API and tracing CUDA libraries, including cuBLAS, cuDNN, and NVIDIA TensorRT™. For graphics computing, Nsight Systems supports profiling Vulkan, OpenGL, DirectX 11, DirectX 12, DXR, and NVIDIA OptiX™ APIs.
       * 对于计算任务，Nsight Systems 支持调查 CUDA API 和跟踪 CUDA 库，包括 cuBLAS、cuDNN 和 NVIDIA TensorRT™。 对于图形计算，Nsight Systems 支持分析 Vulkan、OpenGL、DirectX 11、DirectX 12、DXR 和 NVIDIA OptiX™ API。
     * Detect frame stutter and bottlenecks
       * Nsight Systems automatically detects slow frames (by highlighting frame times higher than a target) as well as local stutter frames (by highlighting frames with higher times than neighboring frames). It also automatically reports CPU times per frame and API calls that are likely candidates for causing stutters. This equips developers with plenty of information to locate and resolve the causes of frame drops and inconsistent frame timing.
       * Nsight Systems 自动检测慢帧（通过突出显示帧时间高于目标的帧）以及局部卡顿帧（通过突出显示时间高于相邻帧的帧）。 它还会自动报告每帧的 CPU 时间和可能导致卡顿的 API 调用。 这为开发人员提供了大量信息来定位和解决掉帧和帧时序不一致的原因。
       * [Using Nsight Systems for Fixing Stutters in Games](https://developer.nvidia.com/blog/using-nsight-systems-for-fixing-stutters-in-games/)
         * 使用 Nsight 系统修复游戏中的卡顿
     * Experience a tool built for flexibility
       * Nsight Systems has a GUI, but it can also be used through the command line. For those who prefer automation, features like the Expert System provide automatic analysis to uncover performance blockers and recommend fixes. Nsight Systems can be leveraged by a solo hobbyist or a full team of engineers, from the scale of servers down to SoCs. Nsight Systems is built for every developer.
       * Nsight Systems 有一个 GUI，但也可以通过命令行使用。 对于那些喜欢自动化的人，专家系统等功能提供自动分析以发现性能障碍并提出修复建议。 Nsight Systems 可以由单独的爱好者或整个工程师团队使用，从服务器规模到 SoC。 Nsight Systems 专为每个开发人员打造。




2. [Installation Guide](https://docs.nvidia.com/nsight-systems/InstallationGuide/index.html)

3. [具体使用案例](https://docs.nvidia.com/nsight-systems/UserGuide/index.html#example-single-command-lines)
   *  详细内容请参见上述链接
   *  举个例子，如果要分析一个pytorch的mnist分类的例子：
    ```
    (base) rtx@rtxA6000:~/workspace/code/demo/pytorch/examples/mnist$ nsys profile python main.py

    # report1.nsys-rep为上一步自动生成的文件
    (base) rtx@rtxA6000:~/workspace/code/demo/pytorch/examples/mnist$ nsys stats report1.nsys-rep


    Generating SQLite file report1.sqlite from report1.nsys-rep
    Exporting 640388 events: [=================================================100%]
    Using report1.sqlite for SQL queries.
    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/nvtxsum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain NV Tools Extension (NVTX) data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/osrtsum.py report1.sqlite]...

    Time (%)  Total Time (ns)  Num Calls    Avg (ns)      Med (ns)    Min (ns)     Max (ns)      StdDev (ns)            Name
    --------  ---------------  ---------  ------------  ------------  ---------  -------------  -------------  ----------------------
        34.4   80,286,890,757      2,283  35,167,275.8  17,405,396.0      1,273  3,114,620,366   72,088,635.2  poll
        18.1   42,217,530,902      1,230  34,323,195.9      20,314.5      1,000    517,806,231  126,219,368.5  pthread_cond_timedwait
        17.0   39,703,337,774      2,031  19,548,664.6  18,154,632.0      3,104  3,145,583,687   70,096,750.8  sem_wait
        16.3   38,148,678,138      3,312  11,518,320.7   1,476,545.5      6,116    990,511,476   37,750,284.1  pthread_cond_wait
        12.3   28,742,662,262      1,789  16,066,328.8  14,551,298.0      2,554    107,862,251    6,682,644.5  sem_timedwait
        1.1    2,626,801,993      3,494     751,803.7      15,072.0      1,001    134,589,661    9,590,313.7  ioctl
        0.3      599,316,306         28  21,404,153.8  22,457,635.0  9,370,069     23,358,485    2,875,666.5  fork
        0.2      553,247,451     16,784      32,962.8      18,765.0      1,000     12,895,474      109,292.3  read
        0.1      211,410,987      3,993      52,945.4      10,777.0      1,029        332,390       59,821.1  munmap
        0.1      122,906,660      3,584      34,293.2      28,989.5      1,044        201,780       21,364.5  recvmsg
        0.0       66,726,957          7   9,532,422.4  14,291,841.0      4,747     14,564,678    6,806,275.1  futex
        0.0       29,197,315          4   7,299,328.8   2,779,684.5     43,389     23,594,557   11,084,883.9  pthread_rwlock_wrlock
        0.0       21,346,040     10,675       1,999.6       1,844.0      1,000         27,204          884.6  write
        0.0       19,041,263         17   1,120,074.3       2,086.0      1,195     18,503,509    4,481,208.0  fopen
        0.0       13,187,823         25     527,512.9      53,084.0     51,981     11,890,787    2,367,351.5  sleep
        0.0       12,808,681      3,470       3,691.3       3,710.0      1,019         23,818        1,659.4  connect
        0.0       12,693,096      4,389       2,892.0       3,157.0      1,001         85,709        1,649.7  pthread_cond_signal
        0.0       10,870,018      3,394       3,202.7       2,850.5      1,000         28,487        1,775.2  socket
        0.0        9,668,368      3,419       2,827.8       2,656.0      1,000        271,668        4,805.8  mmap64
        0.0        3,916,331        128      30,596.3      31,775.0      7,155         59,370       13,116.8  pthread_create
        0.0        1,455,793        672       2,166.4       1,639.0      1,001         32,079        2,000.6  open64
        0.0        1,223,276         25      48,931.0      54,683.0      9,194         73,476       18,277.9  fgets
        0.0        1,091,351         21      51,969.1       2,382.0      2,030        901,625      195,833.0  pthread_join
        0.0          983,918         82      11,999.0       6,323.0      1,000        101,404       18,409.1  pthread_mutex_lock
        0.0          710,876        305       2,330.7       1,258.0      1,041         72,987        4,496.7  mmap
        0.0          548,168          9      60,907.6       3,389.0      1,415        523,430      173,450.3  open
        0.0          347,507         28      12,411.0      12,353.0      3,469         20,881        3,756.7  waitpid
        0.0          249,652         94       2,655.9       1,696.5      1,004          8,733        1,836.1  pipe2
        0.0           67,116         28       2,397.0       2,382.5      1,487          3,360          479.5  waitid
        0.0           36,819         16       2,301.2       2,318.5      1,032          4,280          911.5  fflush
        0.0           36,156         22       1,643.5       1,130.5      1,005          4,616        1,159.6  fcntl
        0.0           12,616          4       3,154.0       2,544.5      1,791          5,736        1,760.4  fopen64
        0.0            7,911          3       2,637.0       2,187.0      1,766          3,958        1,163.2  fread
        0.0            6,383          4       1,595.8       1,322.5      1,122          2,616          699.6  fclose
        0.0            5,692          5       1,138.4       1,077.0      1,018          1,462          184.1  dup
        0.0            3,972          2       1,986.0       1,986.0      1,010          2,962        1,380.3  sigaction
        0.0            3,580          3       1,193.3       1,080.0      1,077          1,423          198.9  pthread_mutex_trylock
        0.0            2,955          1       2,955.0       2,955.0      2,955          2,955            0.0  bind

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/cudaapisum.py report1.sqlite]...

    Time (%)  Total Time (ns)  Num Calls    Avg (ns)     Med (ns)   Min (ns)    Max (ns)      StdDev (ns)                Name
    --------  ---------------  ---------  -------------  ---------  --------  -------------  -------------  -------------------------------
        34.2    2,781,618,372    249,116       11,166.0    4,790.0     1,392  1,587,613,933    3,180,848.4  cudaLaunchKernel
        16.9    1,376,055,464     11,854      116,083.6      550.0       209  1,368,340,792   12,567,867.9  cudaStreamIsCapturing_v10000
        15.3    1,243,646,784          8  155,455,848.0    1,613.5       330    923,405,608  320,799,518.1  cudaFree
        12.3      999,367,661      4,040      247,368.2   13,172.5       731      4,642,656      311,866.1  cudaStreamSynchronize
        12.0      976,856,879      4,040      241,796.3   11,244.5     1,472      4,472,544      814,703.7  cudaMemcpyAsync
        5.7      459,241,432        311    1,476,660.6  339,812.0     2,755    132,524,991   10,528,521.7  cuModuleUnload
        1.4      117,777,534         16    7,361,095.9    1,113.5       585    117,748,497   29,436,640.4  cudaStreamCreateWithFlags
        1.2       99,326,188          9   11,036,243.1  754,206.0    16,235     67,496,292   22,505,962.8  cudaHostAlloc
        0.5       42,658,417      8,506        5,015.1    4,666.5     1,218         29,912        2,533.3  cudaMemsetAsync
        0.2       18,213,472     10,486        1,736.9    1,576.0       377         26,962          989.3  cudaEventRecord
        0.1        5,378,421      1,946        2,763.8    2,771.0       443         10,880        1,073.7  cudaEventQuery
        0.0        2,680,331      3,948          678.9      524.0       144          6,786          526.0  cudaStreamGetCaptureInfo_v10010
        0.0        2,021,191         30       67,373.0   31,414.5     1,596        320,638       82,805.9  cudaMalloc
        0.0          302,715      1,849          163.7      106.0        56         27,120          660.5  cuGetProcAddress
        0.0           81,271          8       10,158.9      787.5       608         74,080       25,833.7  cudaStreamCreateWithPriority
        0.0           42,205         96          439.6      216.5       188          2,552          499.8  cudaEventCreateWithFlags
        0.0            6,221          5        1,244.2      921.0       649          2,964          974.3  cuInit

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/gpukernsum.py report1.sqlite]...

    Time (%)  Total Time (ns)  Instances  Avg (ns)   Med (ns)   Min (ns)  Max (ns)  StdDev (ns)                                                  Name
    --------  ---------------  ---------  ---------  ---------  --------  --------  -----------  ----------------------------------------------------------------------------------------------------
        10.2      988,839,080      1,652  598,570.9  602,564.0   125,217   609,444     43,704.9  ampere_scudnn_winograd_128x128_ldg1_ldg4_relu_tile148t_nt_v1
        8.9      865,430,063      4,956  174,622.7  191,746.0     2,208   336,579    135,142.0  void at::native::vectorized_elementwise_kernel<(int)4, at::native::BinaryFunctor<float, float, floa…
        8.7      844,970,939      1,652  511,483.6  514,723.0   124,033   531,012     35,768.3  void cutlass_cudnn::Kernel<cutlass_tensorop_s1688wgrad_optimized_tf32_64x128_16x6_nhwc>(T1::Params)
        8.7      841,373,696      6,888  122,150.7  131,457.0     3,232   257,282     80,580.7  void cudnn::ops::nchwToNhwcKernel<float, float, float, (bool)0, (bool)1, (cudnnKernelDataType_t)2>(…
        7.1      688,894,660      5,376  128,142.6  133,025.0     2,368   437,859    104,571.5  void at::native::vectorized_elementwise_kernel<(int)4, at::native::<unnamed>::launch_clamp_scalar(a…
        7.1      684,354,987      3,584  190,947.3  224,290.0    27,232   435,203     68,514.5  void at::native::elementwise_kernel<(int)128, (int)2, void at::native::gpu_kernel_impl<at::native::…
        6.2      600,226,581      1,778  337,585.3  315,650.0   306,754   610,948     78,470.4  void cutlass_cudnn::Kernel<cutlass_tensorop_s1688fprop_optimized_tf32_64x64_16x10_nhwc>(T1::Params)
        6.2      597,836,849      1,652  361,886.7  364,195.0    71,936   366,404     26,799.4  void at::native::<unnamed>::max_pool_backward_nchw<float, float>(const T1 *, const long *, int, int…
        4.5      433,124,102      3,444  125,761.9  222,530.0     2,912   434,948    124,559.7  void cudnn::ops::nhwcToNchwKernel<float, float, float, (bool)1, (bool)0, (cudnnKernelDataType_t)0>(…
        3.9      374,664,618      1,792  209,076.2  195,810.0    40,225   386,562     51,704.6  void at::native::<unnamed>::max_pool_forward_nchw<float, float>(int, const T1 *, int, int, int, int…
        3.8      369,706,851      1,652  223,793.5  224,657.5    52,640   249,666     16,855.9  void wgrad_alg0_engine<float, (int)128, (int)5, (int)5, (int)3, (int)3, (int)3, (bool)0, (int)512>(…
        3.6      349,846,241      3,304  105,885.7   83,280.5    22,272   149,633     27,230.0  void at::native::reduce_kernel<(int)512, (int)1, at::native::ReduceOp<float, at::native::func_wrapp…
        2.7      265,928,530      1,638  162,349.5  162,337.0   159,841   174,689        903.4  ampere_sgemm_128x64_tn
        2.6      247,068,109      1,792  137,872.8  129,537.0    28,864   247,074     32,810.6  void implicit_convolve_sgemm<float, float, (int)1024, (int)5, (int)5, (int)3, (int)3, (int)3, (int)…
        2.3      227,119,760     18,180   12,492.8    2,432.0     2,016   109,441     30,200.9  void at::native::vectorized_elementwise_kernel<(int)4, at::native::FillFunctor<float>, at::detail::…
        1.4      139,005,989     26,424    5,260.6    2,880.0     1,984    23,584      6,189.2  void at::native::vectorized_elementwise_kernel<(int)4, at::native::CUDAFunctor_add<float>, at::deta…
        1.2      119,608,909     26,432    4,525.2    2,720.0     1,920    18,881      4,714.6  void at::native::vectorized_elementwise_kernel<(int)4, at::native::addcmul_cuda_kernel(at::TensorIt…
        1.2      117,686,600      3,304   35,619.4    9,424.0     3,200    69,377     31,641.2  void at::native::<unnamed>::fused_dropout_kernel_vec<float, float, unsigned int, (int)1, (int)4, bo…
        1.2      111,397,822      3,304   33,716.0    8,544.5     2,208    66,400     30,984.8  void at::native::vectorized_elementwise_kernel<(int)4, void at::native::<unnamed>::masked_scale_ker…
        1.2      111,377,745      1,638   67,996.2   68,000.0    66,400    80,352        461.9  ampere_sgemm_128x64_nn
        1.1      107,570,246     26,432    4,069.7    2,720.0     1,983    17,024      3,690.4  void at::native::vectorized_elementwise_kernel<(int)4, at::native::BUnaryFunctor<float, float, floa…
        1.1      107,071,129      1,638   65,367.0   65,313.0    64,321    67,104        355.5  ampere_sgemm_128x64_nt
        1.1      106,312,637     26,432    4,022.1    2,688.0     1,888    17,057      3,612.7  void at::native::vectorized_elementwise_kernel<(int)4, at::native::CUDAFunctorOnSelf_add<float>, at…
        0.9       84,561,631     26,432    3,199.2    2,720.0     1,952    26,592      1,276.8  void at::native::vectorized_elementwise_kernel<(int)4, at::native::sqrt_kernel_cuda(at::TensorItera…
        0.6       61,687,931     13,216    4,667.7    2,880.0     1,984    18,176      4,771.7  void at::native::vectorized_elementwise_kernel<(int)4, at::native::BinaryFunctor<float, float, floa…
        0.6       61,634,194     13,216    4,663.6    2,593.0     1,887    20,320      5,423.1  void at::native::vectorized_elementwise_kernel<(int)4, at::native::BinaryFunctor<float, float, floa…
        0.3       30,350,715      1,652   18,372.1   18,464.0     7,392    29,600      1,074.3  void at::native::reduce_kernel<(int)128, (int)4, at::native::ReduceOp<float, at::native::func_wrapp…
        0.2       22,575,050        140  161,250.4  161,073.0   159,265   174,401      1,689.4  ampere_sgemm_64x64_tn
        0.2       21,733,182      1,652   13,155.7   13,185.0     5,279    29,344        918.2  ampere_sgemm_32x32_sliced1x4_nt
        0.2       21,181,918      1,792   11,820.3   11,232.0     3,584    20,448      2,386.4  void at::native::<unnamed>::nll_loss_forward_reduce_cuda_kernel_2d<float, float, long>(T1 *, T1 *, …
        0.2       14,987,145      3,584    4,181.7    4,128.0     2,400     6,880        891.6  void at::native::elementwise_kernel<(int)128, (int)2, void at::native::gpu_kernel_impl<at::native::…
        0.1       12,836,291      1,792    7,163.1    7,040.0     6,048     9,249        419.4  ampere_sgemm_32x32_sliced1x4_tn
        0.1       10,727,579      1,652    6,493.7    6,496.0     3,616     7,168        303.0  void at::native::<unnamed>::nll_loss_backward_reduce_cuda_kernel_2d<float, long>(T1 *, T1 *, T2 *, …
        0.1        9,242,663      1,652    5,594.8    5,568.0     4,576     8,512        289.6  void at::native::reduce_kernel<(int)256, (int)2, at::native::ReduceOp<float, at::native::func_wrapp…
        0.1        8,482,839      1,652    5,134.9    5,088.0     4,064     5,856        154.9  ampere_sgemm_32x128_nn
        0.1        6,868,277      1,652    4,157.6    3,936.5     3,648     5,344        379.9  void cudnn::winograd::generateWinogradTilesKernel<(int)0, float, float>(cudnn::winograd::GenerateWi…
        0.1        5,191,274      1,792    2,896.9    2,880.0     2,176     3,488         93.8  void <unnamed>::softmax_warp_forward<float, float, float, (int)4, (bool)1, (bool)0>(T2 *, const T1 …
        0.0        4,670,474      1,652    2,827.2    2,784.0     2,208     3,456        107.7  void <unnamed>::softmax_warp_backward<float, float, float, (int)4, (bool)1, (bool)0>(T2 *, const T1…
        0.0          838,917         14   59,922.6   59,520.5    58,561    64,288      1,407.4  void cutlass_cudnn::Kernel<cutlass_tensorop_s1688fprop_optimized_tf32_128x64_16x6_nhwc>(T1::Params)
        0.0          758,091        140    5,414.9    5,377.0     5,280     5,920        101.3  void at::native::reduce_kernel<(int)512, (int)1, at::native::ReduceOp<float, at::native::ArgMaxOps<…
        0.0          666,090        140    4,757.8    4,736.0     3,808     5,376        142.8  void at::native::reduce_kernel<(int)512, (int)1, at::native::ReduceOp<long, at::native::func_wrappe…
        0.0          612,737        140    4,376.7    4,352.0     4,288     4,864         83.3  void at::native::unrolled_elementwise_kernel<at::native::<unnamed>::direct_copy_kernel_cuda(at::Ten…
        0.0          402,140        140    2,872.4    2,816.0     2,752     3,360        113.3  void at::native::vectorized_elementwise_kernel<(int)4, at::native::BinaryFunctor<long, long, bool, …
        0.0          346,242         14   24,731.6   24,704.0    24,448    25,056        198.0  ampere_sgemm_128x32_sliced1x4_tn
        0.0          305,346         14   21,810.4   21,760.5    21,345    22,208        225.2  ampere_sgemm_128x32_nt
        0.0          285,825         14   20,416.1   20,320.5    20,128    20,928        217.0  ampere_sgemm_128x32_nn
        0.0          107,903         28    3,853.7    3,920.0     2,848     5,120        922.5  void splitKreduce_kernel<float, float, float, float, (bool)1, (bool)0>(cublasSplitKParams<T3>, cons…

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/gpumemtimesum.py report1.sqlite]...

    Time (%)  Total Time (ns)  Count  Avg (ns)   Med (ns)  Min (ns)  Max (ns)   StdDev (ns)      Operation
    --------  ---------------  -----  ---------  --------  --------  ---------  -----------  ------------------
        98.6      934,118,920  3,592  260,055.4   2,240.0     1,376  1,431,562    274,934.0  [CUDA memcpy HtoD]
        1.3       12,128,482  8,506    1,425.9   1,377.0     1,280      4,096        137.7  [CUDA memset]
        0.1          908,549    448    2,028.0   1,984.0     1,024      2,720        142.2  [CUDA memcpy DtoH]

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/gpumemsizesum.py report1.sqlite]...

    Total (MB)  Count  Avg (MB)  Med (MB)  Min (MB)  Max (MB)  StdDev (MB)      Operation
    ----------  -----  --------  --------  --------  --------  -----------  ------------------
    3,085.920  3,592     0.859     0.008     0.000     4.719        0.910  [CUDA memcpy HtoD]
        2.769  8,506     0.000     0.000     0.000     0.016        0.001  [CUDA memset]
        0.002    448     0.000     0.000     0.000     0.000        0.000  [CUDA memcpy DtoH]

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/openmpevtsum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain OpenMP event data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/khrdebugsum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain KHR Extension (KHR_DEBUG) data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/khrdebuggpusum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain GPU KHR Extension (KHR_DEBUG) data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/vulkanmarkerssum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain Vulkan Debug Extension (Vulkan Debug Util) data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/vulkangpumarkersum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain GPU Vulkan Debug Extension (GPU Vulkan Debug markers) data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/dx11pixsum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain DX11 CPU debug markers.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/dx12gpumarkersum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain DX12 GPU debug markers.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/dx12pixsum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain DX12 CPU debug markers.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/wddmqueuesdetails.py report1.sqlite]... SKIPPED: report1.sqlite does not contain WDDM context data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/unifiedmemory.py report1.sqlite]... SKIPPED: report1.sqlite does not contain CUDA Unified Memory CPU page faults data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/unifiedmemorytotals.py report1.sqlite]... SKIPPED: report1.sqlite does not contain CUDA Unified Memory CPU page faults data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/umcpupagefaults.py report1.sqlite]... SKIPPED: report1.sqlite does not contain CUDA Unified Memory CPU page faults data.

    Running [/usr/local/cuda-11.7/nsight-systems-2022.1.3/target-linux-x64/reports/openaccsum.py report1.sqlite]... SKIPPED: report1.sqlite does not contain OpenACC event data.

    ```


<br>

## [NVIDIA Nsight Visual Studio Edition](https://developer.nvidia.com/nsight-visual-studio-edition)


## [Profiling and Optimizing Deep Neural Networks with DLProf and PyProf](https://developer.nvidia.com/blog/profiling-and-optimizing-deep-neural-networks-with-dlprof-and-pyprof/)
    
1. [Profiling and Optimizing Deep Neural Networks with DLProf and PyProf](https://developer.nvidia.com/blog/profiling-and-optimizing-deep-neural-networks-with-dlprof-and-pyprof/)
   * 具体内容请参见原文
   * 简单的可以通过nvidia-smi相关的命令：
     * `nvidia-smi`
     * `nvidia-smi dmon`: 会显示如下统计信息
       * Power consumption (pwr)
       * GPU temperature (gtemp)
       * Memory temperature (mtemp)
       * Memory utilization (mem)
       * Encoder utilization (enc)
       * Decoder utilization (dec)
       * Memory clock rate (mclk)
       * Processor clock rate (pclk)
     * `nvidia-smi topo -m`: 可以显示GPU之间的互联，比如nvlink等
    * TensorFlow and DLProf
      * 请参见原文
      * Deep Learning Profiler (DLProf) provides support for TensorBoard so that you can visually inspect your models.
      * TF32 uses fewer bits in the matrix multiplications while providing the same model accuracy and therefore yields faster iterations.
      * TF32 is enabled by default in the NVIDIA NGC TensorFlow and PyTorch containers and is controlled with the NVIDIA_TF32_OVERRIDE=0 and NVIDIA_TF32_OVERRIDE=1 environment variables.
      * The average iteration time is reduced to 399 ms from 588 ms when you switch to the TF32 precision. This is a great speed up with switching one environment variable. 
      * DLProf not only provides plenty of information about your model, it also makes suggestions on how you can improve it. In this case, it is suggesting that you enable XLA and AMP (automatic mixed precision).
      * To summarize, you first employed TF32 precision and reduced the training time. Then, you enabled AMP and XLA and further reduced the training time while using DLProf to help profile.
    * PyTorch and PyProf
      * You can still use DLProf and TensorBoard for profiling PyTorch models, as DLProf supports PyTorch as well. However, we wanted to show you alternate ways of profiling.
      * pytorch分析也可以使用DLProf，也可以在pytorch代码里加入PyProf代码，用Nsight进行分析，具体请参见原文
      * By toggling the NVIDIA_TF32_OVERRIDE environment variable, you can take advantage of the TF32 precision type.
      * You got used to doing optimization on TensorFlow, and now you are optimizing code on PyTorch. You have one more step to go: Enable mixed precision and see if you can further optimize your code.
      * That said, PyTorch operates on the [n, h, w, c] format. The batch-norm like layers are processed faster in the [n, h, w, c] format. The most time-consuming operations were batch normalization (as in Figure 14). Furthermore, Tensor Cores natively use the [n, h, w, c] format. Basically, by changing the memory format, you can save some time while processing batch-norm–like layers as well as avoiding some format conversion time inside the CUDNN kernels.
      * 这里有疑惑，我试了下，pytorch的resnet直接接受的输入就是[n,c,h,w]的格式。
    * Nsight Systems for profiling
      * [Nsight Systems User Guide](https://docs.nvidia.com/nsight-systems/UserGuide/index.html)
  

2. [Deep Learning Profiler (DLProf)](https://docs.nvidia.com/deeplearning/frameworks/dlprof-user-guide/index.html)
   - [ ] 需要详细看一下文档: [TODO]



