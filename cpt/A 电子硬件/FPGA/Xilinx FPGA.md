


官网：http://www.alinx.com
京东官方旗舰店：https://alinx.jd.com
京东旗舰店：https://alinx-xy.jd.com
天猫旗舰店：https://alinx.tmall.com
有问题可以联系店铺客服

服务热线：021-67676997
技术支持：support@alinx.com
公司地址：上海市松江区新桥镇漕松路1号1幢301室
工作时间：9:00-18:00 周一到周五















FPGA Xilinx Zynq 系列（一）https://cloud.tencent.com/developer/article/1766697

FPGA技术江湖https://cloud.tencent.com/developer/user/8131718




https://www.amd.com/zh-cn/products/adaptive-socs-and-fpgas/fpga.html
https://www.amd.com/en/products/adaptive-socs-and-fpgas/soc/zynq-7000.html
https://www.amd.com/zh-cn/products/adaptive-socs-and-fpgas/soc.html
https://docs.amd.com/r/en-US/ug585-zynq-7000-SoC-TRM search: UG585


# The Zynq Book ebook

第一章

基于含有 ARM® Cortex®-A9 的 Xilinx® Zynq®-7000 全可编程片上系统的嵌入式处理器

习题教材在本书的官方网站上发布 www.zynqbook.com

Zynq的名字很像化学元素Zn锌，这代表着Zynq芯片可以像锌元素一样可以与其他金属混合称为具有各种所需属性的合金一样。

```
All-Programmable: 全面可编程
System-on-Chip, SoC: 片上系统
APSoC: 全可编程SoC
Field Programmable Gate Array, FPGA: 现场可编程门阵列
Application Specific Integrated Circuit, ASIC: 专用集成电路
Advanced eXtensible Interface, AXI: 高级可拓展接口
Intellectual Property, IP: 知识产权
High Level Synthesis, HLS: 高级合成
Xilinx Vivado Design Suite: Xilinx Vivado设计套件
Embedded: 嵌入式
```

Zynq组合了ARM Cortex-A9处理器和一个FPGA逻辑部件

一块 SoC 可以组合上数字系统所有的功能:处理、高速逻辑、接口、存储器等。处理系统ps，可编程逻辑pl部分。

知识产权功能IP模块就是外设部件

软件系统，软件栈

1.4不懂，HLS是个啥

SoC设计流，第一步是定义所期望的系统行为。第二步是把期望的功能分成硬件和软件。第三步是按照规划阶段所定义的接口集成起来，做进一步的全系统测试。



第二章

PS和PL部分可以单独供电和断电，两者之间有AXI接口


```
Technical Reference Manual: 技术参考手册
Application Processor Unit: 应用处理器单元
Media Processing Engine, MPE: 媒体处理引擎
Floating Point Unit, FPU: 浮点单元
Memory Management Unit, MMU: 内存管理单元
On Chip Memory, OCM: 片上存储器
Snoop Control Unit, SCU: 一致性控制单元
```

处理器系统PS有APU，外设，cache，存储器接口，互联接口，时钟发生电路。

APU里面有什么? 2.1.1应用处理器单元

存储器分为指令和数据两个部分

SCU在ARM核和二级cache及OCM存储器之间形成了桥连接，这个单元还部分负责与PL对接













# 硬件介绍

Zynq7000 系列 XC7Z020-2CLG400I 作为核心处理器，采用 ARM+FPGA SOC 技术 将双核 ARM Cortex-A9 和 FPGA 可编程逻辑集成在一颗芯片上，在 ARM 和 FPGA 上分别具有丰富的 硬件资源和外围接口

芯片

Xilinx 公司的 Zynq7000 系列的芯片，型号XC7Z020-2CLG400I，400个引脚的FBGA封装

U1 XC7Z020

芯片分为：处理器系统部分 Processor System(PS)，集成了两个ARM Cortex™-A9处理器，AMBA®互连，内部存储器，外部存储器接口和外设。这些外设主要包括USB总线接口，以太网接口，SD/SDIO接口，I2C总线接口，CAN总线接口，UART接口，GPIO等。PS可以独立运行并在上电或复位下启动。

可编程逻辑部分 Programmable Logic(PL)



JTAG接口

AX7020开发板的JTAG调试接口, 在电路板上已经集成了JTAG的下载调试电路，所以用户无需购买额外的Xilinx下载器。只要一根USB线就能进行ZYNQ的开发和调试了。在AX7020开发板上通过一个FTDI的USB桥接芯片FT232HL实现PC的USB和ZYNQ的JTAG调试信号TCK,TDO,TMS,TDI进行数据通信

j1 JTAG紧挨着HDMI

U2 FT232HL 电池旁边的大芯片



引脚

启动配置：J13 三种启动模式，JTAG调试模式,QSPI FLASH和SD卡启动模式。J5 J6



电源

+5V电源输入，最大2A电流保护



时钟

AX7020开发板上分别为PS系统和PL逻辑部分提供了有源时钟，是PS系统和PL逻辑可以单独工作

PS时钟源：X1晶振为PS部分提供33.333MHz的时钟输入。主芯片上方BOSOE

PL时钟源：X3单端50MHz的PL系统时钟源，3.3V供电。LED4旁边BOSOE



PS端外设

处理器系统部分

QSPI Flash：一片256Mbit的Quad-SPI Flash，型号为W25Q256，可作为ZYNQ芯片的系统文件和用户数据的存储。U15 在主芯片上方，Winbond厂家

DDR3 DRAM：两片4Gbit高速DDR3 SDRAM，型号为H5TQ4G63AFR-PBC（兼容MT41J256M16RE-125）可作为ZYNQ芯片数据缓存，也可作为操作系统运行内存。U8 U9，厂家SK hynix

千兆以太网接口：Realtek RTL8211E-VL。u10以太网芯片，连接着一个晶振

USB2.0 HOST：j3鼠标键盘U盘的外设，USB3320C-EZK，U11 USB芯片，连接着一个晶振

USB2.0 SLAVE：j4作为USB的从设备，USB口连接电脑，usb slave 副USB接口

UART串口：j7  的USB转UART芯片。U16  Silicon Labs CP2102GM

SD卡：j8 SD卡槽。TXS02612电平转换器

PS PMOD连接器：J12 PS MIO

用户LED：2个灯。PS LED。E6,E8

用户按键：2个按键。PS KEY。B13,B9



PL端外设

可编程逻辑部分

HDMI接口：最高支持1080P@60Hz的输入。J9 HDMI接口

EEPROM 24LC04：一片EEPROM，型号为24LC04,容量为：4Kbit（2\*256\*8bit），由2个256byte的block组成。U13 板载EEPROM就是为了学习IIC总线的通信方式

实时时钟DS1302：一片实时时钟RTC芯片，型号DS1302，他的功能是提供到2099年内的日历功能，年月日时分秒还有星期。外部接一个32.768KHz的无源时钟，提供精确的时钟源给时钟芯。U14 DS1302

扩展口J10：扩展口J10为40管脚的2.54mm的双排连接

注意：切勿直接 切勿直接 跟 5V 设备直接连，以免烧坏 设备直接连，以免烧坏 设备直接连，以免烧坏 设备直接连，以免烧坏 设备直接连，以免烧坏 设备直接连，以免烧坏 FPGAFPGAFPGA 。如果要接 。如果要接 。如果要接 5V 设备，需要接电平转换芯片。 设备，需要接电平转换芯片。 设备，需要接电平转换芯片。 设备，需要接电平转换芯片。 设备，需要接电平转换芯片。

扩展口J11：40针

注意：切勿直接 切勿直接 跟 5V 设备直接连，以免烧坏 设备直接连，以免烧坏 设备直接连，以免烧坏 设备直接连，以免烧坏 设备直接连，以免烧坏 设备直接连，以免烧坏 FPGAFPGAFPGA 。如果要接 。如果要接 。如果要接 5V 设备，需要接电平转换芯片。 设备，需要接电平转换芯片。 设备，需要接电平转换芯片。 设备，需要接电平转换芯片。 设备，需要接电平转换芯片。

用户LED：4个LED。LED1-4 M14,M15,K16,J16

用户按键：4个按键。KEY1-4 N15,N16,T17,R17





# 店铺信息

黑金ALINX

芯驿电子科技（上海）有限公司

黑金FPGA开发板XILINX ZYNQ 7010 7020 PYNQ人工智能Python ALINX https://item.taobao.com/item.htm?spm=a230r.1.14.20.2b896892Rv7CeV&id=541458209006&ns=1&abbucket=9#detail

https://oshcn.taobao.com/?spm=a1z10.1-c-s.0.0.425d78d7Y49uCW

黑金FPGA开发板XILINX ZYNQ 7010 7020 PYNQ人工智能Python ALINX https://item.taobao.com/item.htm?spm=a1z10.5-c-s.w4002-21639808658.19.3ebc4b9eT39Drr&id=541458209006

AX7020开发板 https://space.bilibili.com/473639301/video



店家教程

【ALINX】FPGA ZYNQ视频教程——AX7010/AX7020教程——FPGA实验篇 https://www.bilibili.com/video/BV1JJ411u77d?spm_id_from=333.999.0.0

```
P101_Windows下安装vivado18:20
P202_Vivado初体验Led工程53:30
P303_Vivado下PLL实验33:31
P404_FPGA片内ROM测试实验11:42
P505_FPGA片内RAM读写测试实验35:00
P606_FPGA片内FIFO读写测试实验46:25
P707_Vivado下按键实验12:49
P808_按键消抖实验27:37
P909_PWM呼吸灯实验17:58
P1010_I2C接口EEPROM实验24:26
P1111_RS232实验27:04
P1212_RS422实验07:17
P1313_RS485实验17:31
P1414_HDMI输出测试13:17
P1515_HDMI字符显示实验13:43
P1616_HDMI时钟显示实验41:00
P1717_7寸液晶屏显示实验05:33
P1818_AD7606多通道波形显示实验15:37
P1919_ADDA测试实验09:30
P2020_AD9767双通道正弦波产生实验05:37
```



【ALINX】FPGA ZYNQ视频教程——AX7010/AX7020教程——SDK实验篇 https://www.bilibili.com/video/BV1EJ411u765?spm_id_from=333.999.0.0

```
P101_PS初体验ps_hello52:49
P202_PS的脉动定时器中断ps_timer15:34
P303_PS端MIO的使用34:34
P404_PS端EMIO的使用29:03
P505_PL端axi gpio的使用28:06
P606_lwip_net_test11:47
P707_自定义IP呼吸灯pwm_led28:44
P808_PS端UART读写控制25:46
P909_XADC的使用20:50
P1010_双核AMP的使用34:28
P1111_ZYNQ下使用Free RTOS06:54
P1212_PL读写PS端DDR数据23:23
P1313_通过BRAM实现PS与PL数据交互30:22
P1414_vdma视频入门第一步hdmi_out27:10
P1515_DMA环通测试36:00
P1616_DMA使用之DAC波形发生器(AN108)24:45
P1717_DMA使用之ADC示波器(AN108)38:15
P1818_DMA使用之ADC示波器(AN706)13:26
P1919_基于ADC模块的ScatterGather DMA的使用(AN108)21:33
P2020_基于DAC模块的ScatterGather DMA的使用(AN9767)15:45
P2121_OV5640双目摄像头模块的单目显示26:44
P2222_OV5640双目摄像头模块的双目显示10:05
P2323_双目摄像头以太网传输38:39
P2424_SD卡读写操作之BMP图片显示13:05
P2525_SD卡读写操作之摄像头抓拍12:23
P2626_基于音频模块的录音与播放28:04
P2727_7寸触摸屏模块的显示06:29
P2828_7寸触摸屏的GUI及触摸控制09:42
P2929_基于AN108模块的ADC采集以太网传输18:01
P3030_基于AN706模块的ADC采集以太网传输04:03
P3131_基于UDP和TCP的远程更新QSPI Flash15:20
```



【ALINX】FPGA ZYNQ视频教程——AX7010/AX7020教程——Linux实验篇 https://www.bilibili.com/video/BV1RJ411t7e8?spm_id_from=333.999.0.0

【ALINX】FPGA ZYNQ视频教程——PYNQ教程 https://www.bilibili.com/video/BV1tE411i7MD?spm_id_from=333.999.0.0

```
P101.PYNQ介绍05:52
P202.PYNQ入门10:47
P303.USB摄像头边缘检测人脸识别08:26
P404.自定义overlays寄存器10:33
P505.自定义overlays DMA09:53
P606.ADC 采集并显示波形07:05
```



Xilinx FPGA/Vivado 开发教程（中文，34讲全）https://www.bilibili.com/video/BV1r7411j79u

米联客XILINX_ZYNQ-7000系列（第一期）FPGA入门 https://www.bilibili.com/video/BV1Y7411F7Ct

页面介绍

ALINX产品覆盖Xilinx/Altera两大FPGA体系
广泛应用于人工智能、只能家居、安防监控、汽车电子、软硬件开发设计、机器视觉、智能制造、视频音频采集处理、智能工业自动化、光纤通信、医疗设备、仪器仪表、智能电网、数据中心等行业

资料链接

B站在线视频链接：
http://space.bilibili.com/473639301/channel/detail?cid=89526

Vivado 2017.4版
AX7010 教程及资料链接：
https://pan.baidu.com/s/1xr3D1EED4zb1eyJHYTGRHg 提取码：3zly 
AX7020 教程及资料链接：
https://pan.baidu.com/s/1ESyuVX13mOGj14fzNds7Uw 提取码：dsoc 
Vivado 2017.4软件包链接： 
https://pan.baidu.com/s/1RiolZAHIi8hCskJJGrmSjg  提取码：1w8y 
ZYNQ视频链接：
https://pan.baidu.com/s/11_oHUzEOZlBXWLllCdTf6A 提取码：3au6

Vitis 2019.2版
AX7010 教程及资料链接：
https://pan.baidu.com/s/1UdRfQSdsYw4W78TbOfdnNg  提取码：x3ad 
AX7020 教程及资料链接：
https://pan.baidu.com/s/1ygosi8ZLAmZ6ZsG5Qboegw 提取码：9497 
Vitis 2019.2 软件包链接：
https://pan.baidu.com/s/1_VyeV52YpMLJt-6JUNi-IA 提取码：erhw

店家链接

Vivado 2017.4版

AX7010 教程及资料

链接：https://pan.baidu.com/s/1xr3D1EED4zb1eyJHYTGRHg
提取码：3zly

AX7020 教程及资料

链接：https://pan.baidu.com/s/1ESyuVX13mOGj14fzNds7Uw
提取码：dsoc

Vivado 2017.4软件包

链接： https://pan.baidu.com/s/1RiolZAHIi8hCskJJGrmSjg 
提取码：1w8y 

ZYNQ视频

链接：https://pan.baidu.com/s/11_oHUzEOZlBXWLllCdTf6A
提取码：3au6

Vitis 2019.2版

AX7010 教程及资料

链接：https://pan.baidu.com/s/1UdRfQSdsYw4W78TbOfdnNg 
提取码：x3ad

AX7020 教程及资料

链接：https://pan.baidu.com/s/1ygosi8ZLAmZ6ZsG5Qboegw
提取码：9497

Vitis 2019.2 软件包

链接：https://pan.baidu.com/s/1_VyeV52YpMLJt-6JUNi-IA
提取码：erhw



其他店铺信息

正点原子领航者 https://detail.tmall.com/item.htm?spm=a1z10.5-b.w4011-22300975877.210.3ec461b1R0uF6y&id=609032204975&rn=3aa1a0f3badd4f3312c3550bed10a99c&abbucket=5&skuId=4283333461236

正点原子开发资料 http://www.openedv.com/docs/index.html

# 资讯

IP核到底是怎么样的存在

作者：Ems Yan
链接：https://www.zhihu.com/question/352256371/answer/1272233654
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



半导体IP核（知识产权）对于整个半导体行业都非常重要，尤其是在近年来产业高速发展及全球对知识产权越来越重视的情况下。
半导体IP核于上世纪70年代诞生，随着芯片设计的不断演进，IP核也发生不断的变化。最早，各半导体公司有一个内部的IP核部门，专门来开发维护特定功能的IP核，如接口IP，存储IP，安全IP等等。但伴随SoC设计复杂度上升与上市时间要求缩短，第三方IP供应商开始出现。由于economic of scale， 他们在成本、性能上具有优势明显，因此很多半导体公司开始采用外部第三方IP核，并消减内部在IP核上的研发投入，IP核产业从而不断壮大。
以下是IPnest发布2019年全球半导体IP厂商的营收排名：

&lt;img src="https://pica.zhimg.com/50/v2-61436083ad8a24706dfb8d2e54a5afbb_720w.jpg?source=1940ef5c" data-caption="" data-size="normal" data-rawwidth="1044" data-rawheight="402" class="origin_image zh-lightbox-thumb" width="1044" data-original="https://pic1.zhimg.com/v2-61436083ad8a24706dfb8d2e54a5afbb_r.jpg?source=1940ef5c"/&gt;![img](https://pica.zhimg.com/80/v2-61436083ad8a24706dfb8d2e54a5afbb_720w.jpg?source=1940ef5c)

过去10年来，IP核市场的年复合增长率超过10%。其增长主要伴随着市场上新应用、新产品产生但新需求-- 无人驾驶，AI芯片，5G，物联网，云计算等新兴技术发展，推动了IP核迅速且更加个性化的（针对应用）发展。IP核的复用（reuse）是提高片上系统的设计效率、缩短设计周期的关键。从整个市场来看，在没有全新IP核的情况下，整个行业的发展速度都将收到阻碍。
参考资源：《[从通用到专用，5G时代IP核的新故事] (https://link.zhihu.com/?target=https%3A//www.synopsys.com/blogs/smart-everything/zh-cn/2020/05/ip-application-5g/)》by *Manuel Mota*







# Vivado

FPGA

**安装**

版本选择，WebPACK是功能最少但是免费，Design Edition是设计版本，System Edition系统版本，Documentation Navigator文档版本。

选择组建，Design Tools是设计工具，Devices是设备，Installation Options安装选项。Devices中SoCs/Zynq-7000选项选中，其他都是别的型号，Engineering Sample Devices是工程样板官方提供。

**开发流程**

