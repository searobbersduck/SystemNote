## [NVIDIA Rivermax SDK](https://developer.nvidia.com/networking/rivermax)

参考链接：[NVIDIA Rivermax SDK](https://developer.nvidia.com/networking/rivermax)
* 需要先申请使用
* ![](./images/rivermax_get_started.JPG)
* 申请使用后，点击"Get Started"进入如下页面：[Rivermax Getting Started](https://developer.nvidia.com/networking/rivermax-getting-started)



<br><br>

## 常见问题

1. JT-NM测试是什么？
   * [JOINT TASKFORCE ON NETWORK MEDIA](https://www.jt-nm.org/)
     * JT-NM: OINT TASKFORCE ON NETWORK MEDIA, 网络媒体联合工作组 (JT-NM)
     * Our mission is to help drive development of a packet-based network infrastructure for the professional media industry by bringing together manufacturers, broadcasters and industry organizations to create, store, transfer and stream professional media.
     * 我们的使命是通过汇集制造商、广播公司和行业组织来创建、存储、传输和流式传输专业媒体，帮助推动专业媒体行业基于数据包的网络基础设施的发展。
   * [JT-NM Reference Architecture](https://static.jt-nm.org/RA-1.0/JT-NMReferenceArchitecturev1.0%20150904%20FINAL.pdf)
     * What is JT-NM?
     * Purpose, Motivation and Scope
       * The mission of the Joint Task Force on Networked Media is as follows: In an open, participatory environment, help to drive development of an interoperable packet-based network infrastructure for the professional media industry by bringing together manufacturers, broadcasters and industry organizations with the objective to create, store, transfer and stream professional media.
       * That said, this is not a Standard upon which systems will be based, but rather a collection of best practices, recommendations, and frameworks which readers may choose to implement. It is expected that this Reference Architecture will evolve over time. However, those considering implementing professional networked media infrastructures are encouraged to review the suggestions contained in this document and to begin implementing them as soon as practical. 
       * 也就是说，这不是系统所依据的标准，而是读者可以选择实施的最佳实践、建议和框架的集合。 预计该参考架构将随着时间的推移而发展。 但是，我们鼓励那些考虑实施专业网络媒体基础设施的人员查看本文档中包含的建议，并在可行的情况下尽快开始实施。


<br><br>

2. 基于IP的视频，所谓的IP是指什么？
   * [什么是IP视频及其工作原理？](https://zh-cn.fmuser.net/content/?7456.html)
     * IP视频中的“ IP”代表“ Internet协议”。
   * [基于TCP/IP的音视频传输](https://van23li.github.io/2021/09/22/%E5%9F%BA%E4%BA%8ETCP-IP%E7%9A%84%E9%9F%B3%E8%A7%86%E9%A2%91%E4%BC%A0%E8%BE%93/)
     * 一个完整的视频文件，包括音频、视频和基础元信息，我们常见的视频文件如mp4、mov、flv、avi、rmvb等视频文件，就是一个容器的封装，里面包含了音频和视频两部分，并且都是通过一些特定的编码算法，进行编码压缩过后的。
     * H264、Xvid等就是视频编码格式，MP3、AAC等就是音频编码格式。例如：将一个Xvid视频编码文件和一个MP3音频编码文件按AVI封装标准封装以后，就得到一个AVI后缀的视频文件。
     * 数据编码
       * 使用相关硬件或软件对音视频原始数据进行编码处理（数字化）及加工（如音视频混合、打包封装等），得到可用的音视频数据
       * 涉及技术或协议：
            * 编码方式：CBR、VBR
            * 编码格式：
              * 视频：H.265、H.264、MPEG-4等，封装容器有TS、MKV、AVI、MP4等
            *   音频：G.711μ、AAC、Opus等，封装有MP3、OGG、AAC等
      * 将编码完成后的音视频数据进行传输，早期的音视频通过同轴电缆之类的线缆进行传输，IP网络发展后，使用IP网络优传输;
    * [H.264视频压缩技术](https://van23li.github.io/2021/09/22/%E5%9F%BA%E4%BA%8ETCP-IP%E7%9A%84%E9%9F%B3%E8%A7%86%E9%A2%91%E4%BC%A0%E8%BE%93/#3h264%E8%A7%86%E9%A2%91%E5%8E%8B%E7%BC%A9%E6%8A%80%E6%9C%AF):为实现在较低宽带环境下实现图像的快速传输，ITU-T和IEO/IEC两大国际标准化组织联手制定了这新一代视频压缩标准，即H.264视频压缩标准。其压缩性能好于 MEPG-4，应用目标范围宽，满足不同速率解析度；编码效率上，在相同的重建图像质量下，能够比 h.263 节约 50%的码率；在传输上，能够在有限带宽的 TCP/IP 网络中以较低的数据速率传输视频流，并且在压缩效率，数据包恢复能力以及视频质量超越现有的视频编码方式。




<br><br>



