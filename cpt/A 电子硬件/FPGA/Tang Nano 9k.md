

# Tang Nano 9K

https://item.taobao.com/item.htm?id=679566506652&spm=a21m98.27004841
https://item.taobao.com/item.htm?id=666055424174

https://sipeed.com/
https://wiki.sipeed.com/
https://wiki.sipeed.com/hardware/zh/tang/Tang-Nano-9K/Nano-9K.html

Tang Nano 9K
2.54mm 排针
Type-c 数据线
1.14寸SPI屏 135*240
4.3寸裸屏 480*272
5寸裸屏 800*480
7寸裸屏 800*480


# doc
https://wiki.sipeed.com/hardware/zh/tang/Tang-Nano-9K/Nano-9K.html

简介
Tang Nano 9K 是基于高云半导体 GW1NR-9 FPGA芯片设计的精简型开发板。它搭载的HDMI连接器、RGB接口屏幕连接器、SPI屏幕连接器、SPI FLASH和6个LED使得用户可以方便且快速地进行FPGA验证，RISC-V软核验证和功能样机验证。GW1NR-9拥有的8640 LUT4 逻辑单元除了可以用来设计各种复杂的逻辑电路，还可以运行完整的PicoRV软核，满足了用户学习FPGA、验证软核和深度设计的各种需求。

产品参数
类别 数值
逻辑单元(LUT4) 8640
寄存器(FF) 6480
分布式静态随机存储器SSRAM(bits) 17280
块状静态随机存储器B-SRAM(bits) 468K
块状静态随机存储器数目BSRAM（个） 26
用户闪存(bits) 608K
PSRAM(bits) 64M
高性能DSP模块 支持9x9,18x18,36x36bit的乘法运算和54bit累加器
乘法器(18 x 18 Multiplier) 20
SPI FLASH 32M-bits
灵活的PLL资源 2个锁相环（PLLs）
显示屏幕接口 HDMI接口, SPI屏幕接口和RGB屏幕接口
调试器 板载BL702芯片，为GW1NR-9提供USB-JTAG下载和USB-UART串口打印功能
IO 支持4mA、8mA、16mA、24mA等驱动能力, 对每个I/O提供独立的Bus Keeper、上拉/下拉电阻及Open Drain输出选项
连接器 TF卡座子, 2x24P 2.54mm 排针焊盘
按键 2个用户可编程按键
LED 板载6个可编程LED

板载功能框图
GW1NR-9 FPGA
32Mbit SPI FLASH
3ch DC-CD
BL702 USB-JTAG&UART
USB Type-C (BL702)
LED Water
27Mhz
HDMI Connector
RGB LCD Connector
SPI LCD

Pic:板子引脚图

前代对比
Tang Nano 9K 是 Sipeed 所推出的第五款 FPGA 开发板，与在售前代产品参数对比如下：
版型 Tang Nano 1K Tang Nano 4K Tang Nano 9K
逻辑单元 (LUT4) 1152 4608 8640
硬核处理器 Cortex M3
板载晶振 27MHZ 27MHZ 27MHZ
屏幕接口 RGB 屏幕接口 HDMI 接口 HDMI 接口,RGB 屏幕接口,SPI 屏幕接口
摄像头接口 默认 OV2640
外部存储 仅预留焊盘 32Mbits SPI flash 32Mbits SPI flash
TF 卡槽 有
下载器 板载 USB-JTAG 板载 USB-JTAG 板载 USB-JTAG & USB-UART

适用人群
用法 FPGA MCU FPGA+MCU
语言 Verilog HDL/Verilog C/C++ Verilog HDL/Verilog/C/C++
简介 上板验证用户HDL 用户将软核的比特流文件下载到芯片后可将GW1NR-9当做普通的MCU来使用 烧入软核后可以进行双核开发
适用人群 初学者FPGA开发者 RISC-V开发者Cortex-M开发者 资深软硬件工程师

上手指引

安装IDE和填写正确的License：点击这里
https://wiki.sipeed.com/soft/Tang/zh/Tang-Nano-Doc/get_started/install-the-ide.html
阅读：SUG100-2.6_Gowin云源软件用户指南.pdf
阅读这个教程完成点灯实验。
建议新手在完成这一步之后，自己重新独立新建项目、编写代码，完成这个实验，并且按自己的想法修改点灯程序，增强对FPGA和硬件描述语言的理解。
建议在这个过程阅读以下内容，阅读完才进入下一步：
Verilog代码规范（自行搜索，从初学就培养良好的代码规范是非常必要的）

下面的这些内容对于初学者来说是非常有用的，对未来深入学习 FPGA 很有帮助。
SUG100-2.6_Gowin云源软件用户指南.pdf
SUG949-1.1_Gowin_HDL编码风格用户指南.pdf
UG286-1.9.1_Gowin时钟资源(Clock)用户指南.pdf
SUG940-1.3_Gowin设计时序约束用户指南.pdf
SUG502-1.3_Gowin_Programmer用户指南.pdf
SUG114-2.5_Gowin在线逻辑分析仪用户指南.pdf
上面的都已经打包进了下载站点我跳转。可以点击压缩包全都下载下来

其他学习链接：
在线免费教程：菜鸟教程（学习Verilog）https://www.runoob.com/w3cnote/verilog-tutorial.html
在线免费FPGA教程：Verilog https://www.asic-world.com/verilog/index.html
在线高云半导体官方视频教程：点击这里 https://www.gowinsemi.com.cn/video_complex.aspx?FId=n15:15:26

按照这个教程进行5寸RGB屏驱动实验（其他尺寸屏幕自行修改一下）https://wiki.sipeed.com/hardware/zh/tang/Tang-Nano-9K/examples/LCD.html
如果用户自行无法完成这个实验，可以下载我们9K例程 https://github.com/sipeed/TangNano-9K-example （适配9K板子+5寸屏）查看哪个步骤没做正确
注意：屏幕接线时需要注意排线的1脚对应连接器旁的1脚丝印

需要阅读的文档：
rPLL IP核的说明文档：在IDE里>Tools>IP Core Generator>Hard Module>CLOCK>rPLL>点击弹出界面右下角的Help按键就会弹出说明文档
点开查看说明位置
SUG284-2.1E_Gowin IP Core Generator User Guide.pdf
5寸屏规格书：(主要是获取CLK是33.3Mhz这个信息)

例程汇总
访问 相关例程 https://wiki.sipeed.com/hardware/zh/tang/Tang-Nano-Doc/examples.html 查看所有说明

硬件资料
规格书 1_Specification
原理图 2_Schematic
位号图 3_Bit_number_map
尺寸图 4_Dimensional_drawing
3D 模型文件 5_3D_file
部分手册 6_Chip_Manual
硬件资料总链接：点击这里 https://dl.sipeed.com/shareURL/TANG/Nano%209K

注意事项
如果有什么疑问，欢迎加群 834585530, 或者直接在本页下方留言讨论。
有问题的话先去 常见问题https://wiki.sipeed.com/hardware/zh/tang/Tang-Nano-Doc/questions.html 自查。
避免使用JTAG、MODE、DONE等引脚。如果一定要使用这些引脚，请查看 UG292-1.0原理图指导手册
请注意避免静电打到PCBA上；接触PCBA之前请把手的静电释放掉
每个GPIO的工作电压已经在原理图中标注出来，请不要让GPIO的实际工作的电压超过额定值，否则会引起PCBA的永久性损坏
在连接FPC软排线的时候，请确保排线无偏移、完整地插入到排线中，且线序正确没有接反
请在上电过程中，避免任何液体和金属触碰到PCBA上的元件的焊盘，否则会导致短路，烧毁PCBA
使用途中需要注意复用的 IO，比如 HDMI 的 IO 默认被外部上拉，因此在排针上使用相关引脚的时候可能会与自己想要的结果不符。
nano_9k_hdmi_io

