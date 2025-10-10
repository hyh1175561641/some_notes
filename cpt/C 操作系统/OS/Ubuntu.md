






https://mxlinux.org/


https://www.itheima.com/course/linuxtext.html?jingjia-heima-pinpaici-pc-heimachengxuyuan
https://www.itheima.com/?jingjia-heima-pinpaici-pc-heimachengxuyuan










https://ubuntu.com/
https://wiki.ubuntu.com/
https://www.debian.org/



```bash
update.sh
apt-get update/upgrade
apt-get install



mplayer
libreoffice
chromium
transmission

vim vim-gtk3
emacs emacs-gtk

virtualbox
qemu-system qemu-user-static 无效




gcc g++ qt
openjdk-11-jdk maven
python3 thonny
golang-go
lua
tcl8.6 tk8.6 (wish tcl)
nodejs npm



mysql-server
Redis mongodb

git apache nginx

ssh
wireshark


npm install
jquery axios bootstrap vue @vue/cli react threejs less sass
python3 -m pip install pip




snap install --classic
sublime-text
code



```

```bash
# Google-pinyin
apt-get install fcitx fcitx-googlepinyn
fcitx-config-gtk3 # Input Method Google Pinyin

```



其他软件手动安装:qt java lua go python eclipse sublime typora

# Others

著名软件 https://linux.cn/article-7712-1.html

LLVM Rust Go PHP Ruby Node.js Squid Mutt nginx CockpitWeb

myplayer
framebuffer
aview
libcaca
fbterm
w3m
weechat
init 3
smplayer

komodo edit



# virtual machine manager
virtual machine manager
sudo apt update && sudo apt install virt-manager





baidu virtual machine manager快捷键
快捷键 https://wenku.baidu.com/view/666a1ef766ce0508763231126edb6f1aff007102.html?_wkts_=1671338937531&bdQuery=virtual+machine+manager%E5%BF%AB%E6%8D%B7%E9%94%AE

https://zhuanlan.zhihu.com/p/83331819


https://www.qemu.org/download/
https://www.qemu.org/docs/master/




baidu linux kvm
http://www.lzhpo.com/article/65
https://blog.csdn.net/weixin_53678904/article/details/125950867
http://t.zoukankan.com/lk-fxtx-p-7692773.html
https://www.cnblogs.com/jingsshao/p/16542318.html
https://zhuanlan.zhihu.com/p/545575214
https://blog.csdn.net/weixin_30527151/article/details/116762455








# KVM QEMU
https://www.kali.org/docs/virtualization/install-qemu-guest-vm/

http://www.lzhpo.com/article/65
https://blog.csdn.net/weixin_53678904/article/details/125950867

Kernel-based Virtual Machine的简称，是一个开源的系统虚拟化模块，自Linux 2.6.20之后集成在Linux的各个主要发行版本中。它使用Linux自身的调度器进行管理，所以相对于Xen，其核心源码很少。KVM已成为学术界的主流VMM之一。
KVM的虚拟化需要硬件支持（如Intel VT技术或者AMD V技术)。是基于硬件的完全虚拟化。而Xen早期则是基于软件模拟的Para-Virtualization，新版本则是基于硬件支持的完全虚拟化。但Xen本身有自己的进程调度器，存储管理模块等，所以代码较为庞大。广为流传的商业系统虚拟化软件VMware ESX系列是基于软件模拟的Full-Virtualization。

KVM相关安装包
qemu-kvm 主要的KVM程序包
python-virtinst 创建虚拟机所需要的命令行工具和程序库
virt-manager GUI虚拟机管理工具
virt-top 虚拟机统计命令
virt-viewer GUI连接程序，连接到已配置好的虚拟机
libvirt C语言工具包，提供libvirt服务
libvirt-client 虚拟客户机提供的C语言工具包
virt-install 基于libvirt服务的虚拟机创建命令
bridge-utils 创建和管理桥接设备的工具


kali虚拟机，virt打开图形化软件


```bash
# 查看主机信息
cat /proc/cpuinfo | grep vmx # 查看cpu是否支持虚拟化
grep vmx /proc/cpuinfo # 同上
lsmod | grep kvm # 查看是否加载了KVM模块
# 如果没有加载模块，下面三条命令加载kvm模块
#modprobe kvm
#modprobe kvm-intel
#lsmod | grep kvm
ll /dev/kvm # 查看内核导出了一个kvm设备，


# 配置桥接网络
yum install bridge-urils # 安装桥接工具集
systemctl restart network # 重启网络
cd /etc/sysconfig/network-scripts/ # 配置KVM网桥模式
cp ifcfg-ens33 ifcfg-br0 # 复制桥接网络配置
cat /etc/sysconfig/network-scripts/ifcfg-br0 # 桥接网络
  ## 修改为Bridge(桥接模式)
  TYPE=Bridge
  PROXY_METHOD=none
  BROWSER_ONLY=no
  BOOTPROTO=static
  DEFROUTE=yes
  IPV4_FAILURE_FATAL=no
  IPV6INIT=yes
  IPV6_AUTOCONF=yes
  IPV6_DEFROUTE=yes
  IPV6_FAILURE_FATAL=no
  IPV6_ADDR_GEN_MODE=stable-privacy
  ## 修改为br0
  NAME=br0
  ## 注释掉UUID
  #UUID=9d8b6a36-4495-4f9c-96f6-5bf4cc32dc3c
  ## 修改为br0
  DEVICE=br0
  ONBOOT=yes
  
  IPADDR=192.168.200.125
  NETMASK=255.255.255.0
  GATEWAY=192.168.200.2
  DNS1=8.8.8.8
cat /etc/sysconfig/network-script/ifcfg-ens33 # 主机网络
  TYPE=Ethernet
  PROXY_METHOD=none
  BROWSER_ONLY=no
  BOOTPROTO=static
  DEFROUTE=yes
  IPV4_FAILURE_FATAL=no
  IPV6INIT=yes
  IPV6_AUTOCONF=yes
  IPV6_DEFROUTE=yes
  IPV6_FAILURE_FATAL=no
  IPV6_ADDR_GEN_MODE=stable-privacy
  NAME=ens33
  UUID=9d8b6a36-4495-4f9c-96f6-5bf4cc32dc3c
  DEVICE=ens33
  ONBOOT=yes
  
  ## 注释掉这下面几行
  #IPADDR=192.168.200.125
  #NETMASK=255.255.255.0
  #GATEWAY=192.168.200.2
  #DNS1=8.8.8.8
  
  ## 添加下面这行
  BRIDGE=br0
systemctl restart network # 重启网络
brctl show # 查看网卡
ping baidu.com # 查看能否连接外网



# 正式安装KVM QEUM
# libvirt是管理虚拟机的API库
yum -y install libcanberra-gtk2
qemu-kvm.x86_64 qemu-kvm-tools.x86_64
libvirt.x86_64 libvirt-cim.x86_64 libvirt-client.x86_64 libvirt-java.noarch  libvirt-python.x86_64 libiscsi-1.7.0-5.el6.x86_64
dbus-devel virt-clone tunctl virt-manager libvirt libvirt-python python-virtinst

# virt-manager图形化安装虚拟机




```











# wine

tiankong_hut https://blog.csdn.net/qq_34638161/article/details/81271977

sudo apt-get install wine

wine的设置：支持到win8

wine安装软件（三种）：
       wine  xxx.exe
       ./ xxx.exe
      直接双击软件包
winecfg （wine的设置~）
wine  taskmgr （任务管理器）
wine  uninstaller （卸载软件）
wine  regedit （注册表）
wine  notepad （记事本）
wineboot （ 重启wine）


Linux的虚拟终端（tty）实现中文显示和中文输入以及图片查看
前言
因为Linux系统的tty好像是不能直接支持中文显示的，所以要在另外一个程序中运行tty，我的操作系统是kali-linux5.4.0，基于debian的发行版，所以应该会ubuntu、debian是一样的操作

1.先要安装fbterm，才能在tty下显示中文字符，而且只有进入了fbterm，才能切换中文
aptitude install fbterm
如果你的linux版本的库里面没有fbterm，请参考该文章

安装好后，直接在tty界面下输入fbterm就可以进入

2.安装yong输入法
直接百度搜索小小输入法（就是yong输入法），下载压缩包，解压
住：7z文件的解压命令：7za x 你的压缩文件明 -r -o/xxx/xxx
x代表压缩文件，并且按原始目录解压，-r代表递归解压缩所有子文件夹，-o指定目录，-o后面没有空格，直接接目录
进入到解压好的文件目录
运行yong-tool.sh即可
./yong-tool.sh --install

相关的参数
–install
–uninstall
–select

安装好了之后，注销一下重新进入，终端输入：

yong &
让其在后台运行

或者在这个目录下添加一个可执行文件，名称随意

/etc/X11/Xsession.d

里面的内容就是yong &

注：yong输入法不能在xfce4的终端下运行，但是可以在fbterm虚拟终端下运行，运行yong输入法时不能切换ibus输入法工具，所以要切换回原来的ibus，需要卸载yong输入法，注销后重新登录
./yong-tool.sh --uninstall

需要用到yong输入法时，重新安装、登录即可。

3.安装fbv可以在tty下查看图片，支持多张图片查看(fbterm下不能使用fbv，因为fbterm不是tty)
fbv xxx.png xxx.jpeg

我这里写出安装fbv的坑，后来人可以借鉴以下！！！
下载安装fbv压缩包的网址——>s-tech.elsat.net.pl/fbv
1.安装fbv时需要几个依赖工具
可以在解压后的包里面参考这个

cat README
里面有这样几段话
2. REQUIREMENTS
Linux, configured to provide the framebuffer device interface
(/dev/fb0 or /dev/fb/0)
libungif for GIF support
libjpeg for JPEG support
libpng for PNG support

第一个插件 libungif：
我用的kali5.4.0系统，刚开始用apt直接安装libungif-bin，发现fbv在运行./configure的时候是没有检测到libungif的，所以要从源安装，在这里去下载tar.gz文件，安装过程不再赘述
第二个插件libjpeg
直接apt安装即可，aptitude install libjpeg-dev
第三个插件libpng
aptitude install libpng-dev，然后还有一个必然的插件libpng16-16。注：这里开始出现了坑
2.开始安装fbv
安装好上三个插件后再运行./configure发现都支持了，然后运行make指令
这时候据出现了错误，导致编译失败

error: dereferencing pointer to incomplete type
if (setjmp (png_ptr->jmpbuf))
                                 ^

并且问题是出在png.c这个源文件的if (setjmp (png_ptr->jmpbuf))语句，报错类型是指针指向不完整的结构类型，作为一个程序员就要找到原因所在：

首先查看png_ptr这个指针的定义，看到这个指针的在每个函数的声明为：
png_structp png_ptr;
在vim里面搜索png_structp的定义，发现没有，但是在包含头文件中有这一行
/#include<png.h>;包含了这样一个库函数，这些库函数所在的文件目录为/usr/include这个文件夹中
所以我们去看一下png.h这个头文件中是不是png_structp这个结构体不完整
结果发现这个头文件有对png_structp的模板定义，
所以猜测是不是png_ptr这个png_structp的指针没有jmpbuf成员，
所以在png.h中搜索jmpbuf，发现了这个宏定义，是这样的：
/#define png_jmpbuf(png_ptr)

好的，问题就出在这里，我们之前下的libpng库是——>libpng16-16，如果系统是之前的下的是libpng12-dev不会出现这个问题，最新的libpng16对jmpbuf重新定义了一下，而fbv已经很久没有更新了所以我们需要把解压后的fbv文件夹中的png.c中的所有if(setjmp (png_ptr->jmpbuf))改成png.h中定义的指针调用改成即可：
if(setjmp(png_jmpbuf(png_ptr)))

注：png_ptr是在png.c中定义的结构指针，名字可能随着以后fbv的更新而有所不同哦(但开发人员应该不会去改)，程序员自己细品

现在重新make，发现成功了，然后make install即可，结束！！！
更新
安装fbgrab在tty下可以截图
aptitude install fbgrab
注：fbgrab只能在tty下截图，比如fbgrab -c 1 xxx.png，-c表示选择第几个tty，这里是tty1
————————————————
版权声明：本文为CSDN博主「Scar~let」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/weixin_43669969/article/details/104577615






# Goldendict
Stardict https://pan.baidu.com/s/11hqBiGCqY2f1mdhsGhaj2w code:5pgg
离线词典包 http://download.huzheng.org/ http://download.huzheng.org/zh_CN/

```shell
sudo apt-get install goldendict goldendict-wordnet

tar -xjvf a.bar.bz2 #a.bar.bz2是下载词典文件压缩包的名称
mv a /usr/share/goldendict/dict #dict是新建的词典文件的文件夹

在线词典
有道词典：编辑->词典来源->网站->添加 Youdao http://dict.youdao.com/search?q=%GDWORD%&ue=utf8
海词词典：编辑->词典来源->网站->添加 Haici http://dict.cn/%GDWORD%
海词词典：编辑->词典来源->网站->添加 iCIBA https://www.iciba.com/word?w=%GDWORD%

离线词典 
编辑->词典来源->文件->添加 添加离线文件目录
Oxford Advanced Learner’s Dictionary 8th edition(En-En)-牛津高阶词典(英英)第8版，含图片及英式发音和美式发音
Merriam-Webster’s Collegiate 11th edition(En-En)-韦氏大学词典(英英)第11版，含图片及发音
Longman DOCE5-Longman Dictinary of Contemporary English 5th edition(En-En)-朗文当代第五版英英词典，含发音和图片，大部分例句也带有朗读，很强悍！！！
Longman Pronunciation Dictionary 3rd edition(En-En)-朗文发声辞典第三版，词典中有英音、美音，并对于“多音”的词，配有preference poll图表，即不同的发音在不同地区、不同年龄层里所占的比例。不得不说，这个碉堡了！！！
Longman DOCE5 Extras(En-En)-不包含单词发音和图片，但是包含了该词汇的各种搭配，和牛津搭配词典类似
牛津高阶英汉双解 第四版(En-zh_CN)-英汉双解，我想这个对于国人是必不可少的吧？bgl的格式，排版很美观，无发音
版权声明：本文为CSDN博主「www_helloworld_com」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/www_helloworld_com/article/details/85019862
stardict-cedict-gb-2.4.2.tar.bz2 CEDICT汉英辞典
stardict-chengyuda-2.4.2.tar.bz2 中华成语大词典 2.1
stardict-chibigenc-2.4.2.tar.bz2 汉语大词典 离线版
stardict-dbkqs-2.4.2.tar.bz2 中国大百科全书2.0版
stardict-gaojihanyudacidian-2.4.2.tar.bz2 高级汉语大词典
stardict-gaojihanyudacidian_fix-2.4.2.tar.bz2 高级汉语大词典
stardict-ghycyzzd-2.4.2.tar.bz2 古汉语常用字字典
stardict-guojibiaozhunhanzidacidian-2.4.2.tar.bz2 国际标准汉字大辞典
stardict-hanyuchengyucidian-2.4.2.tar.bz2 汉语成语词典
stardict-HanYuChengYuCiDian-new_colors-2.4.2.tar.bz2 汉语成语词典
stardict-hanyuchengyucidian_fix-2.4.2.tar.bz2 汉语成语词典
stardict-hanzim-2.4.2.tar.bz2 Hanzi Master 1.3
stardict-hycihai-2.4.2.tar.bz2 汉语辞海
stardict-kdic-computer-gb-2.4.2.tar.bz2 计算机词汇
stardict-langdao-ce-gb-2.4.2.tar.bz2 朗道汉英词典5.0
stardict-langdao-ec-gb-2.4.2.tar.bz2 朗道英汉字典5.0
stardict-oxford-gb-2.4.2.tar.bz2 牛津现代英汉双解词典
stardict-oxfordjm-ec-2.4.2.tar.bz2 牛津简明英汉袖珍辞典
stardict-poemstory-2.4.2.tar.bz2 诗词典故词典
stardict-ProECCE-2.4.2.tar.bz2 英汉汉英专业词典
stardict-xhzd-2.4.2.tar.bz2 新华字典
stardict-xiandaihanyucidian-2.4.2.tar.bz2 现代汉语词典
stardict-xiandaihanyucidian_fix-2.4.2.tar.bz2 现代汉语词典
stardict-zigenzidian-2.4.2.tar.bz2 英文字根字典

```



