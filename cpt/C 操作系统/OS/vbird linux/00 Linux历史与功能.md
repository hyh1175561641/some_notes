





netstat -tlunp | grep cups # 查看是否有打印机






/usr/share/doc linux Linux本身的文档
https://tldp.org/ LTDP linux documentation
/var/log 查询log信息

https://www.centos.org/
https://wiki.centos.org/

https://www.masswerk.at/jsuix/index.html

《鸟哥的Linux私房菜 基础学习篇（第四版）》鸟哥著，人民邮电出版社 ISBN 978-7115472588 (4*)
http://linux.vbird.org

https://linux.cn/ linux中国
https://www.linuxidc.com/ linux公社
http://www.chinaunix.net/ ChinaUnix
http://www.178linux.com/ linux运维部落
https://www.runoob.com/linux/linux-tutorial.html
https://www.w3cschool.cn/linux/
https://www.linuxcool.com/
https://www.lanqiao.cn/courses/
https://www.runoob.com/linux/linux-command-manual.html
https://www.linuxprobe.com/tools



# 0-24
装系统
0 pci内容不熟悉
1 Linux历史有空再看看
2 硬盘分区再看看
3*
4 零碎的技巧, 有空整理一下

硬盘和分区
7*
8* 部分没整理
14

文件和权限
5*
6*
13* 部分没整理

进程和服务
15
16
17 写一半
18
19
20

软件与编译
21*
22*
23
24

文本
9*
11*

bash
10
12*





# 电脑

桌面电脑, 笔记本电脑, 平板电脑, 移动终端都可以被称为电脑
计算器, GPS定位器, ATM, 可穿戴设备都属于计算机

算数逻辑单元, 控制单元 主记忆体 外部储存装置 输入输出单元

指令集
精简指令集(Reduced Instruction Set Computer, RISC), Oracle公司的SPARC, IBM公司的Power Architecture PowerPC, ARM Holdings的ARM CPU. SPARC常用在学术领域和大型工作站和银行金融体系的服务器, PowerPC有Sony的Play Station 3 PS3 PowerPC架构的Cell服务器, ARM有移动终端, PDA, 导航系统, 网络设备交换机路由器等
复杂指令集(Complex Instruction Set Computer, CISC), AMD, Intel, VIA等x86架构, 主要用于个人电脑
多媒体微指令集: MMX SSE SSE2 SSE3 SSE4 AMD-3DNow!
虚拟化微指令集: Intel-VT, AMD-SVM
省电功能: Intel-SPeedStep, AMD-PowerNow!
64/32位相容技术: AMD-AMD64, Intel-EM64T

系统单元: PCI-E网卡, 磁盘阵列, 显卡
记忆单元: 内存RAM, 硬盘,软盘,光碟,磁带
输入输出单元: 鼠标键盘,读卡器,扫描器,手写板,触控屏幕 显示器,打印机,音响喇叭,HDMI电视,投影机,蓝牙耳机
电源: 提供足够的电压

集群电脑系统Cluster: 将工作分成多份, 交给多部主机去运算, 再将结果收集起来
超级计算机Supercomputer 用于高速计算,如国防军事,气象预测,太空科技,模拟领域
大型计算机Mainframe Computer 用来处理大量资料与复杂运算,如大企业主机,全国性证券交易,大型企业的资料库服务器
迷你电脑Minicomputer 用于科学研究,工程分析,工厂流程管理
工作站Workstation 个人电脑性能不佳时设计,用于学术研究,工程分析
微电脑Microcomputer 桌面电脑,笔记本电脑

容量单位
bit 比特 0和1
1 Byte = 8 bits 字节
1 Kilo = 1024 Byte
1 Mega = 1024 K
1 Giga = 1024 M
1 Tera = 1024 G
1 Peta = 1024 T
1 Exa = 1024 P
1 Zetta = 1024 E

速度单位
HZ 秒分之一
MHz
GHz
3.6GHz 一秒可以工作3.6x10^9次

通信单位
bit
Mbps Mbit per second 比特/秒
如 20M/5M 2.5Mbyte/625Kbyte 下载/上传

二进制 binary
八进制
十进制 
十六进制

字符集编码
ASCII
UTF-8


# 设备元件
芯片
北桥芯片, 整合在CPU里, 连接速度较快的装置 CPU 内存 显卡
南桥芯片, 连接速度较慢的装置 硬盘, USB口, 网卡

频率 超频 倍频 外频 Intel QPI turbo AMD Hyper Transport
超线程(Hyper-Threading, HT)
FSB(Front Side Bus) 前端总线

CPU等级
Intel Pentium MMX 与 AMD K6 i586等级
Intel Celeron 与 AMD Athlon(K7) 32位 i686等级
64位CPU称为 x86_64等级

主记忆体(main memory), 动态随机存取记忆体(Dynamic Random Access Memory, DRAM), 通电才能使用, 断电信息丢失. 静态随机存取记忆体(Static Random Access Memory, SRAM) 价格昂贵, 容量小,速度块, 集成在CPU内部L2
DDR(Double Data Rate) 双倍资料传输速度
SDRAM DDRSDRAM DDR DDR2 DDR3 DDR4
DDR3 电压1.5V DDR3L 低电压版1.35V
双通道设计, 两块64位内存可以达到128位

只读记忆体(ROM, Read Only Memory)
CMOS, 绑定在硬件上的控制软件 记录主板上的重要参数
BIOS(Basic Input Output System), 快闪记忆体Flash EEPROM, 在开机的时候执行,载入CMOS中的数据, 尝试调用硬盘的开机程序, 进入操作系统

显卡
VGA(Video Graphics Array)
GPU
显存容量
PCI -> AGP -> PCI-Express(PCIe) 插槽升级
D-Sub(VGA端口), 15针连接
DVI DVI-D DVI-I 总共有4种类型
HDMI 可以同时传输图像和声音
Display port 与HDMI功能类似

硬盘与存储设备 硬盘,软盘,MO,CD,DVD,磁带机,随身碟(快闪记忆体),蓝光光碟,大型机器的区域网络储存设备(SAN,NAS)等
硬盘 3.5寸 2.5寸 圆形磁盘, 机械臂, 磁头, 主轴马达

圆形磁盘
扇区sector, 最基本的单位, 512byte 4Kbyte
磁轨track, 一圈扇区组成的同心圆就是磁轨
磁柱cylinder, 多个磁盘正反两面, 同一位置的扇区组成的就是磁柱
外圈的面积更大, 所以会有更多的扇区. 磁碟转一圈能够读写的量比内圈多, 因此默认从外圈开始写
磁碟分割有老式的MSDOS模式磁柱号码, 与新式的GPT模式扇区号码
SATA, SAS(Serial Attached SCSI, SAS 串列式SCSI), IDE(被SATA取代)与SCSI(被SAS取代)等 还有USB, eSATA
USB1.0 1.5Mbyte/s USB2.0 60Mbyte/s  USB3.0 500Mbyte/s USB3.1 1000Mbyte/s
传统硬盘(Hard Disk Drive, HDD)
固态硬盘(Solid State Disk, SSD), 快闪记忆体制作的高容量设备

扩充卡
PCI AGP PCI-X PCIe

设备IO和IRQ中断通道
IRQ(Interrupt)

PS/2 鼠标键盘, USB, 耳机和麦克风, RJ-45网络口, HDMI

Power 古代230W 现代500W
能耗转换率 能耗 = 主机能耗/实际能耗 能耗越接近1越好

电脑运行不稳定的原因
CPU超频, 电源供应不足, 内存负荷过高, 系统过热


# 系统软件与应用程序

CPU有指令集, 编写让CPU读取的指令码给CPU执行, 就能够给CPU运行了
需要了解机器语言
需要了解所有硬件相关的功能函数
程序不具有可移植性
程序具有单一性

高级编程语言, 由编译器转化为机器语言
C, C++, Java, Fortran

操作系统(Operating System, OS), 管理电脑所有活动以及驱动系统中的所有硬件
内核(Kernel), 从开机加载到内存中一直留在内存中
系统调用(System Call), 应用程序调用内核的功能
软件与内核关系较大,与硬件关系不大. 硬件与内核关系较大. 用户与软件关系较大.

内核功能
系统调用接口(System call interface)
程序管理(Process control)
记忆体管理(Memory management)
文件系统管理(Filesystem management)
设备驱动(Device drivers)

应用程序让用户使用



# Linux

unix与Linux历史在鸟哥的第一章

自由软件: 可以自由的修改使用软件, 但不可占为己有或售卖
自由软件协议
Apache License 2.0
BSD 3-Clause "New" or "Revised" license
BSD 2-Clause "Simplified" or "FreeBSD" license
GUN General Public License (GPL)
GUN Library or "Lesser" General Public License (LGPL)
MIT license
Mozilla Public License 2.0
Common Development and Distribution License

专利软件(close source): 仅发布二进制程序(binary program), 有专人维护, 可以向他人出售, 拥有版权
免费软件(Freeware): 免费使用, 但是不出售源代码, 有可能盗取本地数据
共享软件(Shareware): 在使用初期是免费的, 过了试用期限之后, 开始收费, 欢迎用户提供建议或者上报漏洞

Linux是由l1991年因为爱好而编写的类unix系统. 386系统
Linux遵循POSIX规范
POSIX(Portable Operating System Interface)规范, 可移植操作系统接口

Linux内核版本
3.10.0-123.e17.x86_64
主版本.次版本.发布版本-修改版本
uname -r 查询内核版本
主线版本, 长期维护版本 https://www.kernel.org/releases.html

Linux distribution 由商业公司或非营利组织, 将Kernel + Softwares + Tools + 可完整安装程序 整合在一块打包发布的操作系统
LSB(Linux Standard Base), 为了规范Linux发行版差异不要太大 http://www.linuxbase.org/
FHS(File system Hierarchy Standard), 目录架构的标准规范 http://www.pathname.com/fhs/



RPM  Fedora: https://getfedora.org/
RPM  Red Hat: http://www.redhat.com
RPM  CentOS: http://www.centos.org/
RPM  SuSE: https://www.suse.com
RPM  OpenSuSE
DPKG Debian: http://www.debian.org/
DPKG Ubuntu: http://www.ubuntu.com/
DPKG B2D台湾发行版
Other Gentoo: http://www.gentoo.org/

Linux用途
企业环境, 大公司的支持, 金融数据库, 大企业网管环境
学术机构的高性能运算
桌面环境, 窗口界面, 办公环境
移动终端, 手机平板
嵌入式系统, 家电产品, 手机PAD, 数码相机, 其他微型电脑
云端运用, 虚拟化产品




# 安装Linux前的准备
要提前了解硬件是否跟软件匹配
了解Linux发行版与硬件的支持情况, 去官网查看
https://hardware.redhat.com/?pagename=hcl Redhat
http://en.opensuse.org/Hardware?LANG=en_UK OpenSuSE
http://www.linux-laptop.net/ Linux对笔记本的支持
http://www.openprinting.org/ Linux对打印机的支持

选择Linux distribution
Red Hat Enterprise Linux SuSE Enterprise Linux 服务器 更新幅度小 支持时间长
CentOS

硬盘分区设计方案, 重要文件做好备份
方案一:大分区/ 和 Swap 即可
注意: /boot, /, /home, /var, Swap容量大且读写频繁
注意: /usr是可执行程序和文件存放的目录, 容量会逐渐增大

主机的服务规划和硬件关系
桌面级Linux, 确定驱动是否能用
NAT(IP分析器的功能), 全公司全学校用一根网线, 设置内网, 因为流量大所以网卡要选好的, 可以进行流量分析, 控制使用频率
SAMBA(加入Windows网络邻居), 文件服务器, 互相分享文件, 因为容量大, 所以需要磁盘阵列, 内网速度也很大, /home文件可以独立出来
Mail(邮箱服务器), 私人公司或者公司内部交流, 硬盘容量和内网速度加大, /var目录可以独立出来
Web(WWW服务器), 几乎所有的服务器都需要Web功能, 很多分析软件也需要用WWW来展示数据, 如果有数据库,CPU不能太低,RAM也需要适当
DHCP(用户自动获取IP的功能), 客户端自动分配IP地址, 只需要在服务器设置一下即可, 对硬件要求不高
FTP(网络资料传输), 大专院校分享免费资源, 非法组织传输非法文件, 硬盘容量和网卡要求较高

# 图形化安装CentOS

系统默认MBR模式, 使用GPT需要加入一些参数, 笔记本电脑安装还需要加额外电源参数
BIOS boot 2MB 系统自定义 主分区
/boot 1GB xfs 主分区
/ 10GB xfs LVM方式
/home 5GB xfs LVM方式
swap 1GB swap LVM方式

开机管理程序(boot loader)是默认grub2软件,并且安装到MBR上面

鸟哥第三章, 分割磁盘需要再看看, 其他都没啥用

BIOS Boot: GPT分区需要用到
vfat: 同时被Linux和Windows支持的文件系统类型, 可以用来交换资料


安装光盘还可以进行内存检测和烧录

安装双系统 linux来管理MBR, Linux在第一个分区, Windows在后面


































































































