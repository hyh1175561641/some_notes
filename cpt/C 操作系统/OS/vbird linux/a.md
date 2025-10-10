





# XShell 23 chapter

Linux还可以进行排版, 美图, 制作, 多媒体应用上, 这些都需要图形界面(Graphical User Interface,GUI), 所以有X Window System,
X Window最早由MIT发展而来, 在Unix的System V这个操作系统版本上发展来的, 与硬件没有太大的相关性









# 程序与进程

当我们执行一个可执行文件或执行一个指令, 系统触发任何一个事件, 都会启动一个实例, 并且给予这个程序一个ID, 称为PID, 同时开启这个程序的使用者相关属性, 给予一组相关权限配置, 这个程序在系统上的动作, 就跟这个PID权限有关了, 这个程序的子程序权限与父程序相关
程序(program), binary program, 放在存储盘中如硬盘光碟软碟磁带, 是实际的文件
进程(process), 程序被触发, 执行者的权限与属性, 程序的二进制码与相关数据加载进内存中, 操作系统给这个内存单元一个识别码PID, 进程就是一个正在运行的程序
父进程触发的程序叫子进程, 如执行/usr/bin/passwd时会让父进程bash沉睡, 每个进程有PPID就是父进程的PID, 子进程可以继承父进程的环境变量, 如果杀掉一个子进程又莫名其妙启动了, 需要杀掉父进程才可以
程序的互相调用执行, Linux中父进程先fork复制一个一模一样的子程序, 然后子程序在exec来执行实际要进行的程序
系统或网络服务一直保留在内存中, daemon一直在执行, 还有些负责网络连接服务的在监听端口, 提供外部的client连接使用

Linux的每个用户都有自己的环境, 每个账号都有特殊的权限, 除root外其他人都受到了限制, 每个人登录后获取的shell PID都不同
CPU能在各个进程之间进行切换, 从而提升整体效能, 这就是多人分时操作系统
程序卡死时, 切换tty然后kill掉进程, 系统又能恢复正常

程序的查看与管理

```bash
# ps 显示进程列表, ps的man page不好看, 为了符合不同版本, 手册写的非常庞大
# -A 所有的process都显示出来, 与-e有同样效果
# -a 所有process, 默认只列出与terminal有关的进程
# -u 有效使用者相关的process
# x 通常与a一起使用列出完整资料
# l 列出较长较详细的PID数据
# j 工作的格式 jobs format
# -f 做一个更为完整的输出
ps -l # 仅查看自己的bash相关程序
# F 代表这个程序的flag, 4表示程序权限为root, 1表示子程序仅fork而没有exec
# S 代表这个程序的状态(STAT), R(Running)程序正在运行, S(Sleep)程序目前正在睡眠,但可以被唤醒, D不可被唤醒的睡眠状态,通常程序在等待I/O情况, T(stop)停止状态,可能是背景暂停或除错(traced)状态, Z(Zombie)僵死状态,程序已经终止但无法被移除内存外
# UID/PID/PPID 程序的拥有者,进程号码,父进程的PID号码
# C代表CPU使用率, 单位为百分比
# PRN/NI Priority/Nice缩写, 程序被CPU执行的优先顺序, 数字越小越快被执行
# ADDR/SZ/WCHAN 与内存有关, ADDR是kernel function, 指程序在内存哪个部分, 如果是running程序, 一般显示-, SZ代表此程序用掉多少内存, WCHAN表示目前程序是否在运行中,若为-表示正在运行
# TTY 登录者的终端位置, 若为远程登录则使用动态终端界面(pts/n)
# TIME 使用掉的CPU时间, 此程序实际花费CPU运行的时间, 而不是系统时间
# CMD command的缩写, 造成此程序的触发程序指令是什么
ps aux # 观察系统所有程序数据
# USER 进程的使用者
# PID 进程号码
# %CPU CPU使用率
# %MEM 内存实际百分比
# VSZ 虚拟内存使用量Kbytes
# RSS 固定内存使用量Kbytes
# TTY tty1-6是本机用户, pts/0是远程连接, ?表示与终端机无关
# STAT 程序目前的状态, 状态显示与ps -l的标志相同R/S/T/Z
# START 该进程被触发启动的时间
# TIME 进程实际使用CPU运行时间
# COMMAND 进程实际指令是什么
ps -lA # 能够观察所有系统信息
ps axjf # 程序树状显示
ps aux | egrep '(cron|rsyslog)' # 找到两个服务的PID号码
# 僵尸程序会在指令后面跟<defunct>, 记得用父进程kill或者直接reboot

# top 持续检查程序状态
# -d 后接秒数, 程序更新描述
# -b 以批次方式执行top, 通常搭配管道来输出成为文件
# -n 与-b搭配, 意思是需要进行几次top输出
# -p 指定某些PID来观察检测
# 按键指令, 默认使用CPU使用率排序
# ? 显示在top中可以输入的指令
# P 以CPU使用资源排序显示
# M 以Memory使用率排序显示
# N 以PID排序
# T 由该Process使用的CPU时间累计(TIME+)排序
# k 给予某个PID一个信号
# r 给予某个PID重新制定一个nice值
# q 离开top软件的按键
top -d 2 # 每两秒更新一次
# 第一行 当前时间, 开机时长, 登录系统人数, 系统平均负载1/5/15分钟,越小系统越闲置,大于1就表示太频繁
# 第二行 目前程序总量与状态情况, 最后的僵尸程序需要注意
# 第三行 显示CPU整体负载, 每项可使用?查看, wa-I/Owait, 按键数字1可以切换成多个CPU负载
# 第四行 表示目前的内存的情况
# 第五行 表示目前虚拟内存的情况, 量太大说明内存不够
# 第六行 输入指令时显示的地方
# PID Process ID
# USER 使用者
# PR Priority 程序的优先执行顺序, 越小越早被执行
# NI Nice 与Priority有关, 越小越早被执行
# %CPU CPU使用率
# %MEM 内存使用率
# TIME CPU使用时间累加
top -b -n 2 > /tmp/top.txt # 输出结果写入文件
echo $$ # 当前bash的PID 14836
top -d 2 -p 14836 # 观察单一的程序
top -> r -> 14836 -> 10 # 重新修改14836进程nice值为10

# pstree 程序显示呈现树状
# -A 各程序树之间以ASCII字符连接
# -U 各程序树之间以Unicode字符连接, 某些终端可能有错
# -p 同时列出每个process的PID
# -u 列出每个process的所属账号名称, 与父进程不同就会列出名称
pstree -A # 列出程序树
pstree -Aup # 列出PID与users

# kill 发送信号给进程
# -l 查看信号的类型, 也可以通过man 7 signal查询
# 后接工作号码%number 或者后接PID
# 1 SIGHUP 启动被终止的程序, 重新读取配置文件, 类似重新启动reload
# 2 SIGNT 相当于键盘Ctrl-c来中断程序
# 9 SIGKILL 强制中断一个程序, 程序进行到一半没有保存就关闭了
# 15 SIGTREM 以正常结束程序来终止程序, 如果程序发生问题, 这个信号无效
# 19 SIGSTOP相当于用键盘输入Ctrl-z暂停程序
ps aux | grep 'rsyslogd' | grep -v 'grep' | awk '{print $2}' # 找到rsyslogd的PID
kill -SIGHUP $(ps aux | grep 'rsyslogd' | grep -v 'grep' | awk '{print $2}') # 发送信号给rsyslogd进程
tail -5 /var/log/messages # 说明软件重新启动了
kill -9 1234 # 强制关闭某个进程, 比如某个用户的pts终端

# killall 发送信号给某个指令名称
# -i interactive 交互式, 删除需要确认
# -e exact缩写, 后接command name要一致, 完整指令不能超过15字符
# -I 指令名称忽略大小写
killall -1 rsyslogd # 给进程发送信号
killall -9 httpd # 强制关闭所有进程
killall -i -9 bash # 依次询问是否关闭

# free 内存情况观察
# -b/k/m/g/h 默认显示单位是Kbytes, 还有bytes/Mbytes/Gbytes, 或者自己指定单位
# -t 输出最终结果, 显示内存swap总量
# -s 每隔几秒输出一次
# -c 与-s同时处理, 列出几次
free -m # 目前内存容量
# Mem是实际内存的量, Swap是虚拟内存, total是总量, used是已被使用的量, free是剩余可用的量, 后面shared/buffers/cached是已被使用的量中可以被释放继续使用

# uname 系统信息
# -a 所有信息
# -s 系统内核名称
# -r 内核版本
# -m 系统的硬件名称
# -p CPU类型, 与-m类似, 只是显示CPU类型
# -i 硬件的平台(ix86)
uname -a # 查看所有信息

# uptime 系统启动时间和工作负载
uptime # top第一行的信息, 开机时间, 登录用户数, 1/5/15平均负载

# dmesg 开机时内核产生的信息
dmesg | more # 输出所有内核开机的信息
dmesg | grep -i vda

# vmstat 检测系统资源变化, 检测CPU/内存/磁盘IO状态
# -a 使用inactive/active取代buffer/cache内存输出信息
# -f 开机到目前为止, 系统复制fork程序数
# -s 将一些事件(开机到现在)导致的内存变化情况列表说明
# -S 后面可以接单位, 显示的数据有单位, K/N取代bytes
# -d 磁盘读写统计表
# -p 后面列出分割槽, 显示该分割槽的读写总量统计表
vmstat 5 # 5秒一次, 一直循环
vmstat 1 3 # 每秒一次, 共计3次
# procs r等待运行中的程序数量, b不可被唤醒的程序数量, 这两项越多系统越忙碌
# memory swpd虚拟内存被使用量, free未被使用的内存容量, buff用于缓存的内存容量, cache用于缓存的内存量
# swap si磁盘中将程序取出的量, so内存不足二写入到磁盘的量, 数值越大, 说明内存数据交换频繁, 效能越差
# io bi磁盘读取区块数量, bo写入到磁盘的区块数量, 代表系统I/O忙碌
# system in每秒被中断的程序次数, cs每秒进行的事件切换次数, 数值越大, 代表系统与周围设备沟通频繁, 包括光盘,网卡,时钟等
# CPU项目 us非内核层的CPU使用状态, sy内核层的CPU状态, id闲置状态, wa等待IO所耗费的CPU状态, st被虚拟机(virtual machine)所占用的CPU状态
vmstat -d # 系统上所有磁盘的读写状态

```


程序的优先执行顺序, CPU每秒可以执行数G的微指令, CPU切换运行各个进程, 操作系统将优先执行紧急短小的程序
PRI(优先执行顺序priority), 值越低代表越优先, 由内核动态调整, 使用者无法直接调整PRI值
NI(Nice), PRI=PRI+nice, nice值有正负值, PRI越小越早被执行, nice为负数时, 程序就会降低PRI值, 进程优先处理, nice范围是-20-19, root可以随意调整任何nice值, 一般使用者仅可以调整自己的nice值范围是0-19, 一般使用者仅可将nice值越调越高, nice为5时只能往高调

```bash

# nice 给新指令给予新的nice值
# -n 后接数值, 原本的nice加上新数值, 修改后最终数值范围为-20-19
nice -n -5 vim & # 减少5再执行
ps -l # NI变成5, 原本为10
kill -9 %1 # 关闭进程

# renice 重新调整已经存在的进程
ps -l # 选定PID为14836的进程
renice -5 14836 # 重新调整进程的nice值, 子进程也跟着改变了值

```

登录一个bash后, 用户想要边复制文件, 边查询数据, 边进行编译, 还要编辑vim, 这就是工作管理job control, 有时候用户可能只能获取一个连接数
让你操作的文字提示符环境就称为前景(foreground)其他工作放在背景(background)暂停或运行, 放在背景的工作不能够与使用者交互, 也不能用Ctrl+c终止,但是这些工作必须是你当前shell的子程序

```bash
# & 程序放在背景中继续执行
tar -zpcf /tmp/etc.tar.gz /etc & # 程序放在背景中继续执行
[1] 123 # 工作号码, PID
tar -zpcvf /tmp/etc.tar.gz /etc > /tmp/log.txt 2>&1 & # 输出的信息导入到/tmp/log.txt中

# Ctrl+z # 把当前工作暂停到背景中
vim ~/.bashrc # Ctrl+z 暂停工作
find / -print # Ctrl+z 暂停工作

# jobs 显示当前背景工作状态
# -l 除了列出job number与指令外, 还列出PID
# -r 显示正在背景运行中的工作
# -s 显示正在背景中暂停的工作
jobs -l # +代表第一个工作, -代表当前第二个工作, 第三四个没有符号

# fg (foreground)将背景工作拿到前面来处理
fg # 取出+那个工作
fg 1 # 
fg %1 # 指定job number
fg - # 取出第二个工作

# bg 让背景中暂停的工作变成运行
bg %3 # 让该工作在背景中执行, 指令后面多了一个&

# kill 给予工作一个信号来管理工作
kill -9 %2 # 终止2号背景工作

```

如果你远程连接Linux, 想要断开连接后仍然工作, 需要使用离线工作nohup命令, 或者at命令

```bash
# nohup 在终端断线后继续工作, 不支持bash内置指令, 必须是外部指令才行
nohup command # 在终端前工作
nohup command & # 在终端背景中工作
vim sleep500.sh # 编辑文件
#!/bin/bash
/bin/sleep 500s
/bin/echo "I have slept 500 seconds."
chmod a+x sleep500.sh
nohup ./sleep500.sh & # 放到背景执行
exit # 退出终端, 重新登录后发现程序还在运行

```

特殊的文件与程序

```bash
# 程序都写入到内存中, 内存的数据写入到/proc/*目录下
# /proc/*代表的意义
ll /proc # 主机的程序PID以目录状态存在的
ll /proc/1 # 第一个程序systemd的PID是1, cmdline程序被启动的指令串, environ程序的环境变量内容
cat /proc/1/cmdline # 这个指令选项参数启动的systemd, 与某个特定的PID有关内容
# 针对整个Linux相关参数, 就是在/proc目录下的文件, 与对应的内容
/proc/cmdline 加载kernel时下达的相关指令与参数, 查看文件可了解指令是如何启动的
/proc/cpuinfo 本机的CPU相关信息, 包含时间,类型与运算功能
/proc/devices 这个文件记录了系统各个主要设备的主要设备代号, 与mknod有关
/proc/filesystems 目前系统已经载入的文件系统
/proc/interrupts 目前系统上面的IRQ分配状态
/proc/ioports 目前系统上各个装置所配置的IO地址
/proc/kcore 这个就是内存大小, 不要读取它,文件很大
/proc/loadavg top与uptime, 上面三个平均值记录在这里
/proc/meminfo 使用free列出内存信息,
/proc/modules 目前Linux已经载入模块列表, 驱动程序
/proc/mounts 系统已经挂载的数据, mount指令调用的数据
/proc/swaps 系统挂载的内存, 用掉的partition记录在这里
/proc/partitions 使用fdisk -l 会出现所有的partition.
/proc/uptime 用uptime出现的信息
/proc/version 内核的版本, 用uname -a 显示的内容
/proc/bus/* 一些总线设备, USB设备记录这里

# fuser 系统正在使用的文件或程序
# -u 
# -m
# -v
# -k
# -i
# -

16.4.3








```











# 17 daemons

service服务进程在开机就加载到内存中, 始终保持开启, 比如网络服务, 邮箱服务, atd/crond, 这样的程序称为daemon.
daemon是守护之意, 开启的daemon会占用port, daemon程序一般以后面加d命名


传统的System V的init服务启动的脚本放在/etc/init.d下, 都是script脚本, 可以启动/关闭/重启/查看状态/etc/init.d/daemon start/stop/restart/status. 其他指令有init, chkconfig, service, setup
init服务分类有两种, 独立启动(stand alone)服务启动后加载进内存, 供其他用户使用. 总管程序(super daemon), 由特殊的xinetd和inetd总管程序提供socket对应或port对应的管理, 当用户调用对应的socket或port时,xinetd总管唤醒对应的服务进程,用户结束调用后,程序也被关闭.
init开机执行等级(runlevel), 共有7个等级0,1,2...6, 1单人维护模式, 3纯文字模式, 5文字图形界面, 启动脚本是通过/etc/rc.d/rc[0-6]/SXXdaemon链接到/etc/init.d/daemon, 开机按顺序依次启动所需要的服务
切换执行等级, 如果现在是init3, 只要执行命令init 5即可切换


systemctl取代了传统的System V的init, 优点有, 并发执行所有服务而非依次启动, 任何要求(on-demand)都可以启动后续的daemon启动任务, 自动启动依赖的服务, daemon将服务分为多个服务单位(unit)service/socket/target/path/snapshot/timer等不同类型, 多个daemons集合成为一个target用来建设不同的操作环境, systemd兼容init启动脚本. 缺点有, runlevel135没有完全对应systemd的target类型, systemd全部都用systemctl管理程序语法有限不能与脚本自定义参数相比, 手动启动的服务systemctl无法检测与管理, systemd启动不能与用户交互.

systemd把过去的daemon执行脚本变成一个服务单位(unit), 根据功能划分不同类型, 提供不同执行等级分类的操作环境(target)
/usr/lib/systemd/system/ 每个服务最主要的启动脚本配置, 类似过去/etc/init.d下的文件
/run/systemd/system/ 系统执行过程产生的服务脚本, 比/usr/lib/systemd/system/高
/etc/systemd/system/ 管理员根据主机建立的脚本, 这个目录有点像/etc/rc.d/rc5.d/Sxx功能, 执行优先比/run/systemd/system/高
系统执行服务由/etc/systemd/system/决定, 目录下都是链接, 实际由/usr/lib/systemd/system/执行
/etc/sysconfig/* 几乎所有服务的初始化配置参数写入到这里
/var/lib 一些产生数据的服务会将数据写入到这里, Mariadb数据库数据默认写入到/var/lib/mysql/
/run 放置很多daemon缓存文件, 包括lock file以及PID file

ls -l /usr/lib/systemd/system, 根据文件扩展名看服务类型.
.service 主要是系统服务类型, 如本机服务和网络服务, 最常见的类型
.socket 内部程序数据套接字服务, IPC(inter-process communication)的传输信息套接字文件功能, 一般用于本机服务较多, 如图形界面软件交换信息
.target 执行环境类型, 一群unit集合, 如multi-user.target, 其实是执行了一堆其他的.service和.socket
.mount/.automount 文件系统挂载服务, 与文件系统相关的程序, 如网络自动挂载, NFS文件系统挂载等
.path 检测特定文件或目录, 检测特定目录来提供服务, 如打印服务
.timer 循环执行的服务, 由systemd提供, 比anacrontab更有弹性



```bash

# systemctl [command] [unit] 管理systemd启动服务机制
# start 启动
# stop 停止
# restart 重启
# reload 不关闭, 重新载入配置文件
# enable 开机自动启动
# disable 关闭开机自启
# status 查看状态
# is-active 目前有没有正在运行
# is-enabled 开机时有没有默认要启用
systemctl status atd.service # atd服务的状态
systemctl stop atd.service # 关闭服务, 不要用kill, 否则systemctl无法继续监测
systemctl enable sshd.service # 开机自启, 创建链接
systemctl disable sshd.service # 关闭自启动, 删除链接
# status常见的状态
# active(running)正在有一个或多个程序正在系统中执行, 如vsftpd
# active(exited)仅执行一次就正常结束的服务, 目前没有执行, 如开机挂载一次的quotaon, 脚本写的小型服务
# active(waiting) 正在执行中, 等待其他事件执行之后才能处理, 如打印服务需要有执行队列
# inactive(dead) 目前没有运行
# 默认状态的类型
# enable 开机启动, 在对应位置添加一条链接
# disable 开机不启动, 在对应位置删除一条链接
# static 不可以enable, 可能被其他enabled服务唤醒
# mask 无法启动的服务, 被注销, 通过systemctl unmask改回原本状态

# 示范, 办公室没有打印机, 关闭cups服务
systemctl status cups.service # 查看状态
systemctl stop cups.service 
systemctl disable cups.service # 彻底关闭
netstat -tlunp | grep cups # 没有信息
systemctl start cups.socket # 启动cups.socket监听用户端的需求
systemctl status cups.service cups.socket cups.path # 只有cups.socket在启动,其他都关闭
echo "testing" | lp # 没有打印机
systemctl status cups.service # 服务被唤醒了, 打印服务开启631端口
systemctl stop cups.service # 关闭打印服务
systemctl mask cups.service # 注销服务, 其实是链接到了/dev/null
systemctl status cups.service # loaded:masked(/dev/null) 状态都变了, 再也无法被唤醒了
systemctl unmask cups.service # 取消注销服务, 又能被唤醒了

# 查看共有多少服务
systemctl [command] [--type=TYPE] [--all]
# list-units 列出目前启动的unit, 加--all再列出没启动的
# list-unit-files 根据/usr/lib/systemd/system内的文件, 将所有文件列表说明
# --type=TYPE 主要有service, socket, target
systemctl # 系统上启动的unit, 不加参数默认是list-units
# UNIT 项目名称, 包括类别
# LOAD 开机是否启动, 默认显示加载的项目
# ACTIVE 目前状态, 与后续的SUB搭配
# DESCRIPTION 详细描述
systemctl list-unit-files # 打印已安装的unit
systemctl list-units --type=service --all # 仅打印service项目
systemctl list-units --type=service --all | grep cpu # 电源管理机制的服务

# 管理不同的操作环境(target unit)
# graphical.target 文字与图形界面
# multi-user.target 纯文字模式
# rescue.target 无法使用root登录的情况下, systemd开机额外加一个暂时系统, 取得root权限来维护系统, 可能需要chroot
# emergency.target 紧急处理系统错误, 如果rescue.target无法使用, 可以尝试这种模式
# shutdown.target 关机流程
# getty.target 设置你需要几个tty, 可以配置tty参数
systemctl list-units --type=target --all # 查看target类型
# get-default 获取目前的target
# set-default 设置后面接的target为默认模式
# isolate 后接target, 切换到该模式
systemctl get-default # 当前模式是图形界面
systemctl set-default multi-user.target # 默认设置为文字界面
systemctl get-default # 关掉图形界面
systemctl isolate multi-user.target # 不重启情况下, 改为文字界面, 关掉图形界面
systemctl isolate graphical.target # 重新开启图形界面
# 快捷操作的指令
systemctl poweroff # 系统关机
systemctl reboot # 重启
systemctl suspend # 进入暂停模式, 系统状态信息保存到内存中, 关掉大部分系统硬件, 响应速度较快
systemctl hibernate # 进入休眠模式, 系统状态保存到硬盘中, 关掉电脑, 响应速度与硬盘有关
systemctl rescue # 强制进入救援模式
systemctl emergency # 强制进入紧急救援模式

# systemctl服务之间的依赖关系
# --reverse 谁依赖此服务
systemctl list-dependencies # 显示依赖关系
systemctl get-default # multi-user.target 文字模式
systemctl list-dependencies multi-user.target # 它依赖哪些服务
systemctl list-dependencies multi-user.target --reverse # 谁用到了这个服务

# 关闭网络端口
# IP与Port共同组成Socket
# systemd里有很多本机用到的socket服务, 这些文件的位置
systemctl list-sockets # 正在监听本机服务需求的socket file文件位置
cat /etc/services # 服务与端口号绑定在一起的配置文件
# 一直监听端口的程序, 可以称为网络服务
netstat -tlunp # 查看网络端口, 想要关闭avahi-daemon服务
systemctl list-units --all | grep avahi-daemon # 查看想要关闭的服务, 类似于网络邻居的服务
systemctl stop avahi-daemon.service # 关闭service
systemctl stop avahi-daemon.socket # 关闭socket监听
systemctl disable avahi-daemon.service avahi-daemon.socket # 关闭服务
netstat -tlunp # 查看信息发现成功关闭

# 循环(特定条件下)执行某个服务

```


systemctl针对service的配置, 取代旧版的在/etc/init.d建立对应的bash shell script
Red Hat官方文件建议, /usr/lib/systemd/system/目录内容是原本软件的配置不要修改, 要修改的文件放在/etc/systemd/system目录内
/usr/lib/systemd/system/vsftpd.service 官方的默认配置文件
/etc/systemd/system/vsftpd.service.d/custom.conf 服务名后面加.d后缀, 配置文件以.conf结尾. 这个目录下的文件追加其他配置进入到/usr/lib/systemd/system/vsftpd.service内
/etc/systemd/system/vsftpd.service.wants/* 此目录内的文件为链接文件, 依赖服务的链接, 启动vsftpd.service后再启动这里建议的服务, 可能要用到的服务
/etc/systemd/system/vsftpd.service.requires/* 此目录内的文件为链接文件, 依赖服务的链接, 启动vsftpd.service前需要事先启动的服务


```bash
cat /usr/lib/systemd/system/sshd.service # sshd.service配置文件内容
# 配置项目可以重复比如两个After后面的配置项覆盖前面的配置项, After=后面什么都没有可以将项目归零(reset)
# 配置参数有布尔值, 可以用1/yes/true/on代表启动, 用0/no/false/off关闭
# 空白行,开头为#或;都是注解
[Unit] # 描述项目, 依赖相关内容
Description=给系统管理员看的简述
Documentation=提供给系统管理员看的进一步文件查询功能
After=启动之前的程序,说明启动顺序,并不强制要求启动
Before=启动之后的程序,规范启动顺序,不强制要求启动
Requires=必须要依赖的项目,没有这些程序就启动不了
Wants=启动之后在启动,主要是希望建立良好的操作环境
Conflicts=冲突的服务,如果后面的服务已经启动,这个就无法启动

[Service/Socket/Timer/Mount/Path...] #指定类型,与实际执行的指令参数有关, 服务启动脚本,环境设定文件名,重启方式等
Type=这个daemon的启动方式,默认simple启动后加载进内存,forking由ExecStart启动的程序通过spawns延伸出来的子程序为主要服务,原本的父程序启动结束后就被终止,oneshot与simple类似,这个程序在工作完成后就结束了不会留在内存中,dbus与simple类似,必须获取一个D-Bus名称后才会运行,配置此项也要配置BusName=,idle与simple类似,执行这个daemon必须要所有工作顺利执行完毕才会执行,通常是开机到最后才执行的服务.大多数服务需要forking子程序,还有更多的动作只执行一次
EnvironmentFile=启动脚本的环境配置文件,后接多个不同的Shell变量
ExecStart=实际执行的daemon指令或脚本,想要支持完整语法,使用Type=oneshot
ExecStop=与systemctl_stop指令有关,关闭服务执行的指令
ExecReload=与systemctl_reload指令有关
Restart=设定Restart=1,当服务被关闭时,又会重新开启一个新的实例,除非systemctl强制关闭
RemainAfterExit=设定值=1时,当这个服务所有程序终止后,此服务再次重新启动,对Type=oneshot有帮助
TimeoutSec=启动或者关闭无法顺利进行,等待一段时间强制结束
KillMode=process/control-group/none,process服务终止时只会终止主要程序ExecStart后接的,control-group会终止由此产生的其他control-group程序,none则没有程序会被关闭
RestartSec=默认100ms毫秒,与Restart相关,服务被关闭持续多久重新启动

[Install] # 说明此unit要挂载到哪个target下面
WantedBy=后接.target,这个unit本身是依赖于这个下面,linux系统大多数服务都依赖于multi-user.target
Also=当这个unit被enable,后接的unit也enable,具有依赖性的服务写在这里
Alias=链接的别名,当unitenable时,链接的名字被制定成这个


# 范例 启动两个vsftpd实例
# 默认 端口21  /etc/vsftpd/vsftpd.conf配置文件,  /usr/lib/systemd/system/vsftpd.service脚本
# 特殊 端口555 /etc/vsftpd/vsftpd2.conf配置文件, /etc/systemd/system/vsftpd2.service脚本
# 修改配置文件
cd /etc/vsftpd
cp vsftpd.conf vsftpd2.conf
vim vsftpd.conf # 修改#listen_port=555
diff vsftpd.conf vsftpd2.conf # 只有一行不同,监听端口555
# 开始处理启动脚本
cd /etc/systemd/system
cp /usr/lib/systemd/system/vsftpd.service vsftpd2.service
vim vsftpd2.service # 修改了ExecStart参数, 启动配置文件改为第二项配置文件
# 重新载入systemd的配置文件内容
systemctl daemon-reload
systemctl list-unit-files --all | grep vsftpd # 两个daemon都被载入了
systemctl status vsftpd2.service # 关闭状态
systemctl restart vsftpd.service vsftpd2.service
systemctl enable  vsftpd.service vsftpd2.service
systemctl status  vsftpd.service vsftpd2.service
netstat -tlnp # 两个端口都在监听

# 多重重复设置方式,getty为例

17.3.4 后续以后写


```


```bash

# CentOS 7.x默认启动的服务简单说明
systemctl list-unit-files --type=service # 查询更多信息

# 默认启动的服务, 许多针对桌面版本的服务可以关掉
abrtd
accounts-daemon
alsa-X
atd
auditd
avahi-daemon
brandbot rhel-*
chronyd ntpd ntpdate
cpupower
crond
cups
dbus
dm-event multipathd
dmraid-activation mdmonitor
dracut-shutdown
ebtables
emergency rescue
firewalld
gdm
getty@
hyper* ksm* libvirt* vmtoolsd
irqbalance
iscsi*
kdump
lvm2-*
microcode
ModemManager network NetworkManager*
quotaon
rc-local
rsyslog
smartd
sysstat
systemd-*
plymount* upower


# 默认关闭的服务
dovecot
httpd
named
nfs nfs-server
smb nmb
vsftpd
sshd
rpcbind
postfix


```







# 计划任务和日常维护

日常每天都进行的任务,让系统准时执行,一套标准的流程.
如果把工作分为两种: 例行性的工作, 突发性的工作.

Linux自动进行线上更新(on-line-update),自动进行updatedb更新文件名内容库,自动的作登录文件分析logwatch信息,系统会分析多少例行性工作,与软件多少有关.linux常见的例行性任务有:
进行登录的轮替log rotate主动记录系统发生的各种信息,将新旧登录信息有效分开,避免文件过大
分析logwatch任务,系统发生软件,硬件,安全问题,大部分内容都被记录到登陆文件中,logwatch主动分析登录信息,root总是收到logwatch信件
locate文件库,locate通过已经存在的文件目录来查询文件名称,文件名资料库放到/var/lib/mlocate,系统通过updatedb进行自动更新
man page查询文件库, 可以快速查询man page db文件库, 使用man page文件库时,mandb才建立起来,man page文件库也是透过系统的例行性工作排程来自动执行的.
RPM软件登录档建立,RPM是一种软件管理机制,系统经常更新软件,会记录软件,来重新建立RPM文件库
移除临时文件, 某些软件在运行过程中产生临时文件,软件结束后,用tmpwatch来删除数据失效的临时文件
与网络服务有关的分析行为,如果安装类似于www服务器软件,系统会分析该软件的日志,







```bash


# at 执行一次就结束,需要atd服务的支持,事先写好指令放到/var/spool/at目录内
# systemctl restart/enable/status atd 重新启动/开机自动启动/查看状态
# 考虑系统安全原因,先寻找/etc/at.allow文件,写在文件中的使用者才能使用at,不在文件中的不能使用at
# 如果/etc/at.allow不存在,寻找/etc/at.deny文件,写在at.deny的使用者不能使用at,没写在at.deny中可以使用at
# 如果两个文件都不存在,只有root才能使用at这个指令./etc/at.allow比较严格,/etc/at.deny比较松散
# -m 当任务完成后,发送邮箱通知使用者工作完成
# -l at -l相当于atq,列出当前系统该用户的日程
# -d at -d相当于atrm,取消一个在at日程中的工作
# -v 可以使用比较明显的时间格式列出at日程中的工作列表
# -c 后面可以列出接的该项工作的实际指令内容
# HH:MM 04:00 下一个4点执行任务,如果今天时间已过,则明天执行
# HH:MM YYYY-MM-DD 04:00 2015-07-30 某一时刻执行
# HH:MM[am|pm][Month][Date] 04pm July 30 某一时刻执行
# HH:MM[am|pm] + number[minutes|hours|days|weeks] now+5minutes 04pm+3days 在某个时间点再加几个时间后再执行

at now+5minutes
> /bin/mail -s "testing at job" root < /root/.bashrc 
> <EOT(Ctrl+d)> # 代表结束,进入所谓的at shell环境,让你下达多重指令
# 再过5分钟,将/root/.bashrc发送给root自己,显示任务编号和时间

at -c 2 # 将上述的第2项内容列出来查阅,末尾三行表示文件名称,在/var/spool/at/目录下

at 23:00 2015-08-04 # 机房检修,到点关机
at> /bin/sync
at> /bin/sync
at> /sbin/shutdown -h now
at> <EOT(Ctrl+d)>










# crontab 会一直循环执行下去,间隔一定时间
# 可以通过编辑/etc/crontab来支持,需要crond支持




```

















