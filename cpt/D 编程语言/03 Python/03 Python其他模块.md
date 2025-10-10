

# Chardet

简介：编码

安装

```
$ pip install chardet
```

[chardet模块](https://www.liaoxuefeng.com/wiki/1016959663602400/1183255880134144)

# NumPy

NumPy 官网 http://www.numpy.org/
NumPy 源代码：https://github.com/numpy/numpy
SciPy 官网：https://www.scipy.org/
SciPy 源代码：https://github.com/scipy/scipy
Matplotlib 教程：[Matplotlib 教程](https://www.runoob.com/matplotlib/matplotlib-tutorial.html)
Matplotlib 官网：https://matplotlib.org/
Matplotlib 源代码：https://github.com/matplotlib/matplotlib

**应用**

NumPy 通常与 SciPy（Scientific Python）和 Matplotlib（绘图库）一起使用， 这种组合广泛用于替代 MatLab，是一个强大的科学计算环境，有助于我们通过 Python 学习数据科学或者机器学习。

SciPy 是一个开源的 Python 算法库和数学工具包。

SciPy 包含的模块有最优化、线性代数、积分、插值、特殊函数、快速傅里叶变换、信号处理和图像处理、常微分方程求解和其他科学与工程中常用的计算。

Matplotlib 是 Python 编程语言及其数值数学扩展包 NumPy 的可视化操作界面。它为利用通用的图形用户界面工具包，如 Tkinter, wxPython, Qt 或 GTK+ 向应用程序嵌入式绘图提供了应用程序接口（API）。

# YOLOv5

图像识别




# 复制到python

Python Libraries and Frameworks

Machine Learning
Numpy
TensorFlow
Theano
Pandas
PyTorch
Polars
Keras
Scikit-Learn
Matplotlib
Scipy
Seaborn

Web Development
Djangp
Flask
Bottle
CherryPy
Pyramid
Fast API
Web2Py
TurboGears
CubicWeb
Dash
Falcon

Automation Testing
Pyunit
Behave
Splinter
Robot
Pytest

Image Processing
OpenCV
Mahotas
Pgmagick
SimplelTK
Scikit-Image

Game Development
Panda3D
PyGame
PyOpenGL
PyGlet
Arcade

Web Scrapping
Ixml
Requests
Selenium
Scrapy
Beautiful Soup


























# 资讯

https://blog.csdn.net/weixin_39677203/article/details/110788579

原标题：机器视觉、模式识别库汇总

机器视觉是一种综合应用，要用到图像处理、三维几何变换之类的，有的需要模式识别。模式识别是一种算法，就是如何分类和识别。可以用到很多地方，文字、语音、图像的智能识别。下面瑞视特科技整理了一份机器视觉、模式识别库汇总，方便大家学习。

一、开源生物特征识别库 OpenBR

OpenBR 是一个用来从照片中识别人脸的工具。还支持推算性别与年龄。

使用方法：$ br -algorithm FaceRecognition -compare me.jpg you.jpg

二、计算机视觉库 OpenCV

OpenCV 是 Intel 开源计算机视觉库。它由一系列 C 函数和少量 C++ 类构成，实现了图像处理和计算机视觉方面的很多通用算法。

OpenCV 拥有包括 300 多个C函数的跨平台的中、高层 API。它不依赖于其它的外部库——尽管也可以使用某些外部库。

OpenCV 对非商业应用和商业应用都是免费(FREE)的。(细节参考 license)。

OpenCV 为Intel Integrated Performance Primitives (IPP) 提供了透明接口。 这意味着如果有为特定处理器优化的的 IPP 库， OpenCV 将在运行时自动加载这些库。

三、人脸识别 faceservice.cgi

faceservice.cgi 是一个用来进行人脸识别的 CGI 程序， 你可以通过上传图像，然后该程序即告诉你人脸的大概坐标位置。faceservice是采用 OpenCV 库进行开发的。

四、Java视觉处理库 JavaCV

JavaCV 提供了在计算机视觉领域的封装库，包括：OpenCV、ARToolKitPlus、libdc1394 2.x 、PGR FlyCapture和FFmpeg。此外，该工具可以很容易地使用Java平台的功能。

JavaCV  还带有硬件加速的全屏幕图像显示(CanvasFrame)，易于在多个内核中执行并行代码(并行)，用户友好的几何和色彩的相机和投影仪校准(GeometricCalibrator，ProCamGeometricCalibrator，ProCamColorCalibrator  )，检测和特征点(ObjectFinder)，一类是实现投影，摄像系统(直接图像对齐设置匹配主要GNImageAligner，ProjectiveTransformer，ProjectiveGainBiasTransformer，ProCamTransformer 和ReflectanceInitializer)，以及在 JavaCV 类杂项功能。

五、视频监控系统 OpenVSS

OpenVSS - 开放平台的视频监控系统 - 是一个系统级别的视频监控软件视频分析框架(VAF)的视频分析与检索和播放服务，记录和索引技术。它被设计成插件式的支持多摄像头平台，多分析仪模块(OpenCV的集成)，以及多核心架构。

六、OpenCV的.NET版 OpenCVDotNet

OpenCVDotNet 是一个 .NET 对 OpenCV 包的封装。

七、人脸检测算法 jViolajones

jViolajones是人脸检测算法Viola-Jones的一个Java实现，并能够加载OpenCV XML文件。

示例代码：http://www.oschina.net/code/snippet_12_2033

八、手势识别 hand-gesture-detection

手势识别，用OpenCV实现

九、人脸检测与跟踪库 asmlibrary

Active Shape Model Library (ASMLibrary©) SDK, 用OpenCV开发，用于人脸检测与跟踪。

![img](https://blog.csdn.net/weixin_39677203/article/details/110788579)

十、开放模式识别项目 OpenPR

Pattern Recognition project(开放模式识别项目)，致力于开发出一套包含图像处理、计算机视觉、自然语言处理、模式识别、机器学习和相关领域算法的函数库。

十一、运动检测程序 QMotion

QMotion 是一个采用 OpenCV 开发的运动检测程序，基于 QT。

十二、图像特征提取 cvBlob

cvBlob 是计算机视觉应用中在二值图像里寻找连通域的库.能够执行连通域分析与特征提取。

十三、OpenCV的.Net封装 OpenCVSharp

OpenCVSharp 是一个OpenCV的.Net wrapper，应用最新的OpenCV库开发，使用习惯比EmguCV更接近原始的OpenCV，有详细的使用样例供参考。

![img](https://blog.csdn.net/weixin_39677203/article/details/110788579)

十四、人脸检测识别 mcvai-tracking

提供人脸检测、识别与检测特定人脸的功能，示例代码

十五、视频捕获 API VideoMan

VideoMan 提供一组视频捕获 API 。支持多种视频流同时输入(视频传输线、USB摄像头和视频文件等)。能利用 OpenGL 对输入进行处理，方便的与 OpenCV，CUDA 等集成开发计算机视觉系统。

![img](https://blog.csdn.net/weixin_39677203/article/details/110788579)

十六、基于QT的计算机视觉库 QVision

基于 QT 的面向对象的多平台计算机视觉库。可以方便的创建图形化应用程序，算法库主要从 OpenCV，GSL，CGAL，IPP，Octave 等高性能库借鉴而来。

十七、开源视线跟踪软件 ITU Gaze Tracker

哥本哈根大学开源视线跟踪软件

The ITU Gaze Tracker is an open-source eye tracker that aims to  provide a low-cost alternative to commercial gaze tracking systems and  to make this technology more accessible. It is developed by the Gaze  Group at theIT University of Copenhagen and other contributors from the  community, with the support of theCommunication by Gaze Interaction  Association (COGAIN).

十八、图像处理和计算机视觉常用算法库 LTI-Lib

LTI-Lib 是一个包含图像处理和计算机视觉常用算法和数据结构的面向对象库，提供 Windows 下的 VC 版本和 Linux 下的 gcc 版本，主要包含以下几方面内容：

1、线性代数

2、聚类分析

3、图像处理

4、可视化和绘图工具

十九、实时图像/视频处理滤波开发包 GShow

GShow is a real-time image/video processing filter development kit.  It successfully integrates DirectX11 with DirectShow framework. So it  has the following features:

GShow 是实时 图像/视频 处理滤波开发包，集成DiretX11。

二十、C++计算机视觉库 Integrating Vision Toolkit

Integrating Vision Toolkit (IVT) 是一个强大而迅速的C++计算机视觉库，拥有易用的接口和面向对象的架构，并且含有自己的一套跨平台GUI组件，另外可以选择集成OpenCV

二十一、OpenCV的Python封装 pyopencv

OpenCV的Python封装，主要特性包括：

提供与OpenCV 2.x中最新的C++接口极为相似的Python接口，并且包括C++中不包括的C接口

提供对OpenCV 2.x中所有主要部件的绑定：CxCORE (almost complete), CxFLANN  (complete), Cv (complete), CvAux (C++ part almost complete, C part in  progress), CvVidSurv (complete), HighGui (complete), and ML (complete)

在Python中访问C++中的数据结构

完善的内存管理，使用者无须担心内存的问题

可以在 OpenCV 的 Mat 与 wxWidgets, PyGTK, and PIL 中使用的 arrays 互相转换

二十二、模式识别和视觉库 RAVL

Recognition And Vision Library (RAVL) 是一个通用 C++ 库，包含计算机视觉、模式识别等模块。

二十三、OpenSURF

利用OpenCV和C++编写的SURF算法，作者Christopher Evans是首个利用OpenCV和C++结合的方法实现SURF算法

二十四、人脸识别库 rpflex

rpflex 是一个 Flex 开发的库，用来识别照片中的人脸、眼镜和脖子。

二十五、OpenCV优化 opencv-dsp-acceleration

优化了OpenCV库在DSP上的速度。

二十六、Java 计算机视觉库 BoofCV

BoofCV 是一个 Java 的全新实时的计算机视觉库，BoofCV  易于使用而且具有非常高的性能。它提供了一系列从低层次的图像处理、小波去噪功能以及更高层次的三维几何视野。使用 BSD  许可证可在商业应用中使用。这里有篇英文文章用来介绍 BoofCV 的使用。

![img](https://blog.csdn.net/weixin_39677203/article/details/110788579)

二十七、计算机视觉库 SimpleCV

SimpleCV  将很多强大的开源计算机视觉库包含在一个便捷的Python包中。使用SimpleCV，你可以在统一的框架下使用高级算法，例如特征检测、滤波和模式识别。使用者不用清楚一些细节，比如图像比特深度、文件格式、颜色空间、缓冲区管理、特征值还有矩阵和图像的存储。

语法简洁，可读性强是它的特点，通过下面的例子可以看出使用SimpleCV时多么的容易:

from SimpleCV import Camera

image = Camera().getImage()

image.show()

二十八、3D视觉库 fvision2010

基于OpenCV构建的图像处理和3D视觉库。

二十九、视觉快速开发平台 qcv

计算机视觉快速开发平台，提供测试框架，使开发者可以专注于算法研究。

三十、计算机视觉算法 OpenVIDIA

OpenVIDIA 项目使用 OpenGL 、Cg 和 CUDA-C 在拥有单GPU或多GPU的图形硬件上实现了计算机视觉算法，很快将要发布支持 OpenGL 和 Direct Compute API 的例程。

三十一、C++计算机视觉库 ICL

ICL (Image Component Library) 是一种新型的C + +计算机视觉库，由比勒费尔德大学神经信息学组和CITEC开发。它兼顾了性能和用户友好性。 ICL提供了一个易于使用的类和函数的集合，可以开发复杂的计算机视觉应用。

在不到15行的C + +代码(见例子)可以写成一个简单的图像采集和可视化应用。

三十二、Matlab计算机视觉包 mVision

Matlab 的计算机视觉包，包含用于观察结果的 GUI 组件，貌似也停止开发了，拿来做学习用挺不错的。

三十三、Lua视觉开发库 libecv

ECV 是 lua 的计算机视觉开发库(目前只提供linux支持)

三十四、OpenCV的扩展库 ImageNets

ImageNets 是对OpenCV 的扩展，提供对机器人视觉算法方面友好的支持，使用Nokia的QT编写界面。

三十五、图像捕获 libv4l2cam

对函数库v412的封装，从网络摄像头等硬件获得图像数据，支持YUYV裸数据输出和BGR24的OpenCV IplImage输出。

三十六、高斯模型点集配准算法 gmmreg

实现了基于混合高斯模型的点集配准算法，该算法描述在论文： A Robust Algorithm for Point Set  Registration Using Mixture of Gaussians, Bing Jian and Baba C. Vemuri.  ，实现了C++/Matlab/Python接口。

三十七、Scilab的计算机视觉库 SIP

SIP 是 Scilab(一种免费的类Matlab编程环境)的图像处理和计算机视觉库。SIP 可以读写 JPEG/PNG/BMP 格式的图片。具备图像滤波、分割、边缘检测、形态学处理和形状分析等功能。

三十八、计算机视觉和机器人技术的工具包 EGT

Matlab 的计算机视觉和机器人技术的工具包，貌似现在已经停止开发了，但是其功能已经比较完善，比直接用 Matlab 本身的函数来得方便一些，有兴趣的可以拿去做二次开发。

三十九、计算机视觉库 BazAR

BazAR 是基于特征点检测和匹配的计算机视觉库。 它能够快速检测和匹配图像中的已知物体，并且能够用于增强现实，它是计算机视觉研究的先进成果。

四十、计算机视觉库 VLFeat

一个开源的计算机视觉库，实现了 SIFT,MSER, k-means, hierarchical k-means,  agglomerative information bottleneck, quick  shift等算法。由C语言编写,提供MATLAB接口，文档详细。支持跨平台。

四十一、STAIR Vision Library

STAIR Vision Library (SVL) 最初是为支持斯坦福智能机器人设计的，提供对计算机视觉、机器学习和概率统计模型的支持。

四十二、Scilab Image Processing Toolbox

SIP 提供了图像处理、模式识别以及计算机视觉处理。

四十三、3D计算机视觉库 openvis3d

这个项目的目的是提供一个高效的3D计算机视觉库，用于图像和视频处理。它包括深度立体匹配、光流(运动)估计、遮挡检测和运动平台估计

四十四、libvideogfx

视频处理、计算机视觉和计算机图形学的快速开发库。

四十五、go-opencv

Go-OpenCV 是 Go 语言版的 OpenCV 封装。

四十六、Java图形绘制库 Toxiclibs.js

Toxiclibs.js 是一个开源的计算机图形设计库，无需外部依赖，使用 元素进行图形绘制。

四十七、OpenCL 封装库 CLOGS

CLOGS 是 OpenCL C++ API 的高级封装库，其设计目的是集成其他 OpenCL 代码，包括同步 OpenCL 事件，当前支持两个操作：基数排序和独立扫描。

四十八、openvgr

OpenVGR 包含以下几个实时处理模块 (基于 OpenRTM-1.0):

立体相机采集 (对于 IEEE 1394b 相机),

立体图像浏览器,

3-D 点云重建 (使用 OpenCV),

基于边缘的 3-D 物体检测

四十九、sparse-stereo-vision

使用 OpenCV 函数, 这个项目能从成对的立体图像中重建场景。

五十、PIV图形软件包 Fluere

Fluere是粒子图像测速(PIV)的图形软件包。 Fluere是高度优化的并行处理，并在多个平台上运行。该项目的目标是提供高质量的测速软件，采用PIV技术处理的最新进展的研究人员和教育工作者，而所使用的算法的完整的知识。

五十一、stereoview
