# OpenCV

OpenCV（Open Source Computer Vision Library）是一个开源的计算机视觉库，它提供了很多函数，这些函数非常高效地实现了计算机视觉算法（最基本的滤波到高级的物体检测皆有涵盖）。

OpenCV 的应用领域非常广泛，包括图像拼接、图像降噪、产品质检、人机交互、人脸识别、动作识别、动作跟踪、无人驾驶等。

OpenCV 还提供了机器学习模块，你可以使用正态贝叶斯、K最近邻、支持向量机、决策树、随机森林、人工神经网络等机器学习算法。

提升编程能力需要多练习编程，提升理论知识需要系统学习《数字图像处理》、《计算机视觉》和《模式识别》等课程，所有这些都不能一蹴而就，需要耐下心来认真修炼。 

## 历史

1999 年，Gary Bradski（加里·布拉德斯基）当时在英特尔任职，怀着通过为计算机视觉和人工智能的从业者提供稳定的基础架构并以此来推动产业发展的美好愿景，他启动了 OpenCV 项目。

OpenCV 库用C语言和 C++ 语言编写，可以在 Windows、Linux、Mac OS X 等系统运行。同时也在积极开发 Python、Java、Matlab 以及其他一些语言的接口，将库导入安卓和 iOS 中为移动设备开发应用。

OpenCV 自项目成立以来获得了来自英特尔和谷歌的大力支持，尤其需要感谢 Itseez，该公司完成了早期开发的大部分工作。此后，Arraiy 团队加入该项目并负责维护始终开源和免费的 OpenCV.org。

Itseez 是俄罗斯的一家视觉公司，专门从事计算机视觉算法。2016 年 5 月，英特尔收购该公司，以“帮助英特尔的用户打造创新型深度学习的 CV 应用，如果自动驾驶、数字安全监控和工业检测”（英特尔物联网总经理 Doug Dacies 如此说）。

OpenCV 设计用于进行高效的计算，十分强调实时应用的开发。它由 C++ 语言编写并进行了深度优化，从而可以享受多线程处理的优势。
OpenCV 的一个目标是提供易于使用的计算机视觉接口，从而帮助人们快速建立精巧的视觉应用。

因为计算机视觉和机器学习经常在一起使用，所以 OpenCV 也包含一个完备的、具有通用性的机器学习库（ML模块）。这个子库聚焦于统计模式识别以及聚类。ML 模块对 OpenCV 的核心任务（计算机视觉）相当有用，但是这个库也足够通用，可以用于任意机器学习问题。

## IPPICV 加速

如果希望得到更多在英特尔架构上的自动优化，可以购买英特尔的集成性能基元（IPP）库，该库包含了许多算法领域的底层优化程序。在库安装完毕的情况下 OpenCV 在运行的时候会自动调用合适的 IPP 库。
从 OpenCV 3.0 开始，英特尔许可 OpenCV 研发团队和 OpenCV 社区拥有一个免费的 IPP 库的子库（称 IPPICV），该子库默认集成在 OpenCV 中并在运算时发挥效用。

IPPICV 可以在编译阶段链接到 OpenCV，这样一来，会替代相应的低级优化的C语言代码（在 cmake 中设置 WITH_IPP = ON/OFF来开启或者关闭这一功能，默认情况为开启）。使用 IPP 获得的速度提升非常可观。

## OpenCV有哪些应用？

许多计算机科学家和经验丰富的程序员多多少少都了解计算机视觉的某些方面，但是很少有人熟谙计算机视觉的每一个应用。比如：

- 很多人了解计算机视觉在安保行业的应用；
- 一些人也知道它在网页端的图像和视频处理中的应用在逐渐增加。


但很少有人知道计算机视觉在游戏交互中的应用。同时，也很少有人认识到大部分航空图像和街景图像（比如说谷歌街景）已经大量应用相机校正和图像拼接技术。

有一些人略微知道一点视觉在自动监控、无人机或者生物制药分析上的应用，但很少有人知道计算机视觉早已经在制造业普遍使用。事实上，批量制造的所有东西都已经利用计算机视觉在进行某些方面的质检工作了。

自从测试版本在 1999 年 1 月发布以来， OpenCV已经广泛用于许多应用、产品以及科研工作中。这些应用包括在卫星和网络地图上拼接图像，图像扫描校准，医学图像的降噪，目标分析，安保以及工业检测系统，自动驾驶和安全系统，制造感知系统，相机校正，军事应用，无人空中、地面、水下航行器。

OpenCV 亦是斯坦福大学的机器人斯坦利（Sltaney）至关重要的一部分，这个机器人赢得了美国国防部高级研究计划署主持的 DARPA 机器人挑战赛野外机器人竞速的 200 万美元大奖。

DARPPA 机器人挑战赛（DRC）是机器人领域的一项重大赛事，堪称“机器人的奥林匹克”。

## OpenCV 使用开源许可证

OpenCV 的开源许可允许任何人利用 OpenCV 包含的任何组件构建商业产品。你也没有义务开源自己的产品或者对该产品所涉及领域进行反馈和改进，虽然我们希望你这样做。
在这种自由许可的影响下，项目有着极其庞大的用户社区，社区用户包括一些来自大公司的员工（IBM、微软、英特尔、索尼、西门子和谷歌等）以及一些研究机构（例如斯坦福大学、麻省理工学院、卡内基梅隆大学、剑桥大学以及法国国家信息与自动化研究所）。

OpenCV 在世界范围内都非常流行，尤其是在中国、日本、俄罗斯、欧洲和以色列有着庞大的用户社区。


# 开发环境

```
头文件：
opencv\build\include
opencv\build\include\opencv
opencv\build\include\opencv2
库文件：
opencv\build\x64\vc14\lib
链接器：
opencv_world310d.lib

添加环境变量
;/.../opencv/build/x64/vc14/bin
```




https://opencv.org OpenCV官网
https://docs.opencv.org OpenCV文档

https://docs.opencv.org/4.3.0/ OpenCV官方文档4.3

http://c.biancheng.net/view/1791.html OpenCV教程：超详细的OpenCV入门教程，值得收藏！

[中文站](http://www.opencv.org.cn)

[中文站论坛](http://www.opencv.org.cn/forum/)

[中文站文档](http://www.opencv.org.cn/opencvdoc/2.3.2/html/doc/tutorials/tutorials.html)

[中文站教程](http://www.opencv.org.cn/opencvdoc/2.3.2/html/doc/tutorials/tutorials.html)

[树莓派 OpenCV3.4.1 安装血泪史，分享如何规避各种坑](https://blog.csdn.net/jacka654321/article/details/80728795)

[利用树莓派来安装opencv从而来调动摄像头工作（没有坑，超超自己试过）](https://www.cnblogs.com/2142781703wangzhichao/p/10744185.html)

百度搜索“树莓派跑opencv卡不卡”

百度搜索“树莓派 人脸识别”

[Windows下载OpenCV](https://blog.csdn.net/maizousidemao/article/details/81474834)

[OpenCV下载和安装](http://c.biancheng.net/view/1104.html)

[OpenCV-python 博客园](https://www.cnblogs.com/silence-cho/p/10926248.html)











# OpenAI

https://www.openai.com OpenAI
https://beta.openai.com/docs/introduction/prompt-design-101 官网文档首页
https://openai.com/blog/emergent-tool-use/ 有趣的捉迷藏






https://www.opengl.org/ OpenGL

