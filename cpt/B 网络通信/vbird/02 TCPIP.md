


# 网络

网络是由电脑主机透过网线或无线技术连接起来的技术.
历史上出现的全录Ethernet,IBMToken-ring技术,这两种技术互不兼容.
ARPANET/TCPIP技术,用软件技术将硬件整合.
Internet通用网络技术,但是没有任何阻碍和保障,可以畅通无阻全世界遨游.
IEEE标准规范,以太网标准,仅需要查看以太网卡支持的标准就知道硬件功能有哪些.
早期Linux在开发时就是透过POSIX这个标准来设计内核的,标准相当重要
TCP/IP协议也有标准,大部分都是通过RFC形式发布的

电脑网络的组成: 一般PC,网络打印机,Linux服务器,路由器,ADSL,因特网
node节点: 具有IP地址的设备
server服务器主机: 提供数据给用户的主机
workstation工作站: 任何可以在电脑网络输入的设备都是工作站
client: 主动发起连线请求数据的是客户端
Network Interface Card,NIC网卡: 内置或插卡在外部的主机设备,主要是提供网络连接的设备,一般有RJ-45接头,达到网络连接的功能.
网络界面: loopback(lo)测试界面
topology网络拓扑: 物理连接方式,网络拓扑
route/gateway网关: 可以连接两个以上不同的网段设备

局域网(Local Area Network,LAN),节点之间的传输距离较近,如大楼内,学校内,使用高品质光纤,用于集群系统,分散系统,云端负荷分担系统.
广域网(Wide Area Network,WAN),传输距离远,城市与城市传输的距离,可靠性较低,用于email,FTP,WWW等功能
城市网络(Metropolitan Area Network),近年来很少提及.



# 七层OSI

节点之间通信透过标准协议进行通信,但是硬件,软件与数据包和应用程序互相连接,需要将整个网络连接的过程分层,每一层都有独立的功能.
依照定义来说,越接近硬件的为底层,越接近应用程序的为高层,不论是客户端还是服务端,每一层只识别对方的统一层资料,上下层传递需要经过封包拆包,包头信息含有来自哪里,去哪里,接受者,校验码等信息.
七层OSI仅是一个参考模型(model),目前的网络并没有如此复杂.



7 应用层(Application Layer,AH DATA) 应用层本身并不属于应用程序所有,而是定义应用程序如何进入这一层界面,用于将资料接受或传输给应用程序,最终展示给使用者.
6 表现层(Presentation Layer,PH DATA) 将本地端应用程序的资料格式转换或者重新编码成网络标准格式,然后在传递给下一层进行协议进行处理,这一层主要定义的是网络服务或程序之间的数据格式的转换,包括数据加解密也是在这一层去处理的.
5 会话层(Session Layer,SH DATA) 这一层定义了两个地址之间的连接通道的连接与挂断.应用程序之间的对话,提供其他加强型服务如网络管理,签到签退,对话控制等.传输层是在判断资料包是否正确到达目的地,那么会话层是在确定的网络服务建立连线的确认.
4 传输层(Transport Layer,TH DATA) 定义了发送端与连接端的连接技术(TCP,UDP),同时包括该技术的封装格式,传输,流程控制,传输过程的检测,复原重新发送等.保证各个资料封包可以正确无误的传输到目的地.
3 网络层(Network Layer,NH DATA) 经常提及的IP(Internet Protocol)层就是在这一层定义的,定义出建立连接,终止与保存,传输路径选择.还有能否到达目的地的路由(Route)概念.
2 链接层(Data-Link Layer,FAC DATA CHK),这一层又可以分为两层,一层是偏硬件部分主要是MAC(Media Access Control),这个包裹为MAC frame,MAC是网络设备所能处理的主要包裹,MAC必须要通过通信协议来获取媒体应用,目前最常用的是IEEE 802.3以太网协议.另一层是偏向软件的逻辑链接层(Logical Link Control,LLC)来控制,主要在多环境处理来自上层封包(packet)并转换成MAC格式,主要负责信息交换,流量控制,校验问题.
1 实体层(Physical Layer,一串0或1),网络通信只能传输0或1这两位信号,需要定义设备之间电信号的编码,来回发送和接收信号.







# 四层架构

由ARPANET发展而来的TCP/IP协议简化为四层,在结构上面没有七层这么严谨,程序书写比较容易.

应用层 HTTP FTP SMTP POP3 NFS SSH DNS
传输层 TCP UDP
网络层 IP ICMP
链接层 LAN:Ethernet,Token Ring WAN:Modem,ISDN,ATM,Serial ARP








# 链路层
链路层协议主要与硬件有关系,CSMA/CD以太网协议,以及MAC通信框架

广域网使用的设备价格较低,但是数量却非常多,一般用户连接广域网主要是通过ADSL或光纤,第四代Cable宽频等.早期网络通过电话线PPP协议(Point-to-Point Protocol,PPP)上网,支持TCP/IP,NetBEUI,IPX/SPX协议,使用度非常广.整合服务数位网络(Integrated Services Digital Network,ISDN)利用现有的电话线来连接,但是两端需要ISDN设备,可以整个多个通道,速度成倍增长.非对称数位用路回路(Asymmetric Digital Subscriber Line,ADSL)通过PPPoE协议,使用电话线高频部分进行通信,上网的同时还可以打电话,由于上传下载的带宽不同,因此叫做非对称回路,将PPP模拟在以太网卡上,因此需要一张网卡来连接到设备.总线数据机(Cable modem)通过有线电视使用的同轴电缆作为通信媒介,同样需要数据机设备来连接到ISP,以获取网络参数上网,Cable modem的带宽是分享型的,通常具有区域性.
同轴电缆,双绞线(Twisted Pair Ethernet)

局域网使用的设备,以太网,在IEEE802.3的IEEE10BASE5中定义的10表示传输速度为10Mbps,BASE表示采用基频信号来进行传输,5表示每个节点之间最长可达500公尺.由于网络的传输信号就是0与1,数据传输单位为每秒多少bit,M bits/second,Mbps.

当今的网络通信商(Internet Serices Provider,ISP)宣传他们的ADSL传输速度可以达到下载/上传2Mbps/123Kbps(Kbits per second),Kb值得不是Bytes而是bits,2M/128K在实际文件传输速度上来说256KBps/16KBps,所以正常下载速度约在每秒100-200KBytes之间.同理,在网卡或者一些网络设备上面宣传自己的产品速度可达10/100Mbps(Mega-bits per second),实际需要处以8才是我们常用的文件容量计算单位bytes.

后面不想写了,都是通信工程的内容


CSMA/CD
MAC封装格式
MTU最大传输单位
集线器,交换机相关的机制



# 网络层

IP协议:有广泛应用的IPv4(Internet Protocol version 4),与未来版的IPv6两个版本的协议,IPv4有32位字节,IPv6有128位字节.

IPv4协议

封装格式,IP包可以达到65535Bytes大小

每行占32位
Version 4(单位bits), IHL 4, Type of Service 8, Total Length 16
Identification 16, Flags 3, Fragmentation Offset 13
Time To Live 8, Protocol 8, Header Checksum 16
Source Address 32
Destination Address 32
Options 19, Padding 13
Data

Version版本: IP版本.
IHL(Internet Header Length)IP表头的长度,这个表头的长度,单位是word,1word=4bytes.
Type of Service服务类型,内容为PPPDTRUU,表示这个IP包中,PPP表示IP包的优先度,D为0表示一般延迟1位低延迟,T为0表示一般传输量1位高传输量,R为0表示一般可靠度1表示高可靠度,UU保留未使用.gigabit以太网络种种相关规格可以让IP包加速且降低延迟.
Total Length总长度: 指IP包总长度,包括表头与数据部分,最大可达65535bytes.
Identification辨别码: 如果MAC将IP包拆分,通过这个来识别MAC包裹属于哪一个IP包裹.
Flags特殊标志: 0DM,D为0表示可以分段1表示不可以分段,M为0表示此IP为最后分段为1表示非最后分段.
Fragment Offset分段偏移: 表示目前分段在原始IP包中所占的位置,有这个才能把拆分的IP组合起来.
Time To Live,TTL存活时间: 表示IP包的存活时间,范围是0-255,当这个IP包通过一个路由器时,TTL减一,当TTL为0时,这个数据包会被丢弃
Protocol Number协议代码: 记录来自传输层的协议代码,1ICMP(Internet Control Message Protocol), 2IGMP(Internet Group Management Protocol), 3GGP(Gateway-to-Gateway Protocol), 4IP(IP in IP encapsulation), 6TCP(Transmission Control Protocol), 8EGP(Exterior Gateway Protocol), 17UDP(User Datagram Protocol),常见的还是6TCP,17UDP,1ICMP
Header Checksum表头检查码: 用来检查IP表头校验码
Source Address: 来源的IP地址,32位
Destination Address: 目标IP地址,32位
Options: 其他参数,包括安全处理机制,路由记录,时间戳,严格宽松来源路由
Padding: 补齐项目,由于Options的内容不知道多大,但是IP每个数据都必须是32bits,不够时补齐



IP地址的分级







```bash

# route



```




ICMP协议
网际网络信息控制协议(Internet Control Message Protocol,ICMP),ICMP是一个错误检测与回报机制,最大的功能就是可以确保网络连接状态与连接的正确性,ICMP也是网络层的重要封装之一,ICMP透过IP封包来进行资料传输
常见的ICMP类型
0 Echo Reply表示一个回应信息
3 Destination Unreachable表示目的地不可到达
4 Source Quench 当router负载过高,此类型码可以用来让发送端停止发送信息
5 Redirect 用来重定向路由路径的信息
8 Echo Request 请求回应信息
11 Time Exceeded for a Datagram 当数据包在某些路由传送的现象中造成过时状态,此类型码可告知来源该数据包已被忽略的信息
12 Parameter Problem on a Datagram 当一个ICMP包裹重复之前的错误时,会回复来源主机关于参数错误的信息
13 Timestamp Request 要求对方发送时间信息,用来计算路由时间差,满足同步性协定的要求
14 Timestamp Reply 此信息是回应Timestamp Request用的
15 Information Request 在RARP协议应用之前,此信息是用来在开机时取得网络信息
16 Information Reply 用来回应Information Request信息
17 Address Mask Request 这个信息是用来查询子网络mask设定信息
18 Address Mask Reply 回应子网络mask查询信息的

```bash
# ICMP检测网络状态,确认与主机的状态,设定防火墙不要忘记ICMP包裹,8需要关闭
# ping

# traceroute

```

# 传输层

TCP
三次握手



UDP


# 应用层






































