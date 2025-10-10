











```bash


# netstat 网络监控
# -a 将系统上所有连接, 监听, Socket都列出来
# -t 列出tcp信息
# -u 列出udp信息
# -n 不以程序服务名称, 以端口号来显示
# -l 列出目前正在网络监听的服务
# -p 列出该网络服务进程的PID
netstat # 列出系统已经建立的网络连接与Socket状态
# 由两部分组成, 第一部分是与网络相关的部分
# Proto 网络封包协议, 主要是TCP与UDP
# Recv-Q 由使用者程序连接到socket总bytes数量
# Send-Q 由远程主机发送过来的总bytes数量
# Local Address 本地段的IP: port
# Foreign Address 远端主机的IP: port
# State 连线状态, 主要有建立(ESTABLISED)和监听(LISTEN)
# 第二部分是与进程自己相关的部分, socket可以让两个进程沟通
# Proto 一般是unix
# RefCnt 连接到此socket程序数量
# Flags 连线的旗帜
# Type socket类型, 主要有确认连线(STREAM)与不需确认(DGRAM)
# State 若为CONNECTED表示多个程序之间已经建立连接
# Path 连接到此socket的路径, 或者是相关数据输出路径
netstat -tulnp # 目前系统上已经再监听的网络连线及PID
kill -9 PID # 关闭某个端口的服务
killall -9 avahi-daemon # 关闭某个端口的服务






```












































