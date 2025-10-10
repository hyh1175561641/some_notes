
https://busybox.net/ Unix小工具集合, 三百多个常用的Linux命令和工具的软件







10 10.2.7
12*

# shell/BASH

通过shell来跟内核沟通,完成想要达到的工作.硬件提供功能,内核提供驱动程序,程序提供指令,通过shell来完成整体调用(指令列模式).常见的shell有,sh,bash,zsh以及图形界面.
文字界面,各个发行版都是一样的,速度快,不容易断线,信息丢失少,效率很高.图形界面对使用者来说,比较亲善,功能强大,并非是一个完整的套件.
shell的功能,查询系统信息,监测系统信息.
shell的种类,Bourne SHell(sh),Sun公司默认的C SHell,商业常用的K SHell,TCSH,Linux常用的Bourne Again SHell(bash是sh的增强版本,也是基于GNU架构发展出来的).

/etc/shells可以查看常用的shell,可以填入不存在的shell避免网络攻击./etc/passwd文件中最后一列是用户登录时用到的shell, /sbin/nologin是不想让用户获取到shell
tab第一个单词后面命令补全,第二个单词后面是文件名补全
在输入指令的末尾加上反斜线\会转义Enter键,可以在接下来的下一行继续输入指令
快捷键 ctrl+a光标移到开头 ctrl+e光标移到末尾 ctrl+u向前删除 ctrl+k向后删除

```bash

# history 记录你输入过的命令,内容记录在~/.bash_history中,当你登出系统之后,才会被记录,如果多个人登录同一账号,那么最后退出的会覆盖之前的记录内容,仅仅记录命令的内容却无法记录命令的时间, 列出最近使用过的命令,对应 ~/.history
# 键盘上下键翻阅前几次的目录,默认能记录1000个记录,追踪你下达过的指令记录,echo ${HISTSIZE}
# n 数字,列出最近的n个命令列表
# -c 将目前的shell中所有history内容清除
# -a 将目前新增history指令写入histfile中,默认写入~/.bash_history
# -r 将histfile内容读取到shell的history中
# -w 将目前history内容写入histfiles中
history 3 # 输出三条
history -w # 将目前history写入到文件中,默认是~/.bash_history
# number 执行第几笔命令
# command 查询最近的开头为command的命令,并执行
# !! 执行上一条指令,相当于上箭头翻出指令,然后再执行
!65 # 执行第65条命令
!al # 执行al开头的命令,最近的那个


# alias 命令别名设定功能
# \ls 加上\可以忽略alias功能
alias lm='ls -al|more' # 显示当前目录下的文件列表
# unalias 取消命令别名的设置


# type 查询是否为bash内置指令,与找文件的which有区别
# -t 显示file为外部指令,显示alias表示为别名指令,显示builtin表示为bash内置指令
# -p 后面接name为外部指令,才会显示完整文件名
# -a 会由PATH变量定义的路径中,列出所有指令,包含alias
type ls # 列出指令的主要使用情况
type -t ls # 列出命令的类型
type -a ls # 所有指令
type cd # 内置指令






# sleep 30s 睡眠30秒





```


# 环境变量

环境变量$PATH /usr/lib64/qt-3.3/bin : /usr/local/sbin : /usr/local/bin : /usr/sbin : /usr/bin : /root/bin 变量名一般大写,用冒号分隔,如果两个命令名相同排在前面的路径先执行,不同用户使用的PATH值不同.
/bin目录下的指令可以在任何路径都能执行


```bash

# 变量的作用域,环境变量是全局变量,自定义变量是局域变量,环境变量的值能继承给子程序,自定义变量不继承给子程序
# 全局变量(global variable),局域变量(local variable)


PATH="${PATH}:/root" # 添加环境变量

# env environment环境的缩写,列出目前shell环境下的所有环境变量及其内容
HOSTNAME # 主机名称
TERM # 终端机环境类型
SHELL # shell程序,一般是/bin/bash
HISTSIZE # 可记录多少条历史命令
OLDPWD # 上一个工作目录
LC_ALL # 语系设定
USER # 使用者名称
LS_COLORS # 颜色显示
MAIL # mailbox位置
PATH # 可执行命令目录
PWD # 当前工作目录
LANG # 与语系有关
HOME # 用户主目录
LONGNAME # 登录者用来登录的账户名称
_ # 上一次使用指令的最后一个参数或指令
RANDOM # 随机数

# set 所有的变量,包含环境变量和自定义变量
HISTFILE # 记录历史命令文件位置
PS1 # 命令提示符
PS2 # 转义字符加回车,第二行输入提示符
$ # 目前shell所用的PID, echo $$
? # 上一个命令的返回值, echo $?
OSTYPE HOSTTYPE MACHTYPE # 主機硬體與核心的等級

PS1='[\u@\h \W]\$ ' # 命令提示符
PS2='> ' # 转义字符加回车,第二行输入提示符
man PS1 # 手册
# \d 显示星期月日的日期格式,如'Mon Feb 2'
# \H 完整的主机名称
# \h 主机名的第一个单词部分
# \t 显示时间,24小时格式的 HH:MM:SS
# \T 显示时间,12小时格式的 HH:MM:SS
# \A 显示时间,24小时格式的 HH:MM
# \@ 显示时间,12小时格式的 am/pm格式
# \u 目前使用者账户名称
# \v bash版本号
# \w 完整路径,从/起,家目录用~替代
# \W 用basename函数获取工作目录名称,仅列出最后一个目录名
# \# 下达的第几个指令
# \$ 提示字符,root用户#,普通用户$
PS1='[\u@\h \w \A #\#]\$' user1@ubuntu /root/bin 22:23 #15]$ 

# unset 取消变量的值
unset name # 取消变量

# export 把自定义变量转换成环境变量
export # 显示所有的环境变量
export PATH # 使新设定的PATH生效
NAME=VBird; bash; echo $NAME; exit; # 进入到bash子程序,变量值还存在



```


```bash

# locale 显示结果的语言,LANG,LC_ALL是两个主要参数
# /usr/lib/locale存放支持的语系,/etc/locale.conf存放当前语系的值
locale # 查看当前系统语系的值,文字,数字,时间,比较排序,货币格式,信息显示等
locale -a # 查看Linux支持的语系



```

# 交互

```bash

# read 读取键盘的值
# -p 后面接提示字符
# -t 后面接等待的秒数,长时间未输入会怎么怎么样
read atest # 把输入的内容存到变量中
echo ${atest} # 读取用户输入的内容
read -p "Please keyin your name: " -t 30 named # 提示字符和30秒内等待时间
echo ${named} # 输出读取的内容


# declare/typeset 变量的类型
# -a 将后面的variable值定义为array类型
# -i 将后面的variable值定义为integer类型
# -x 与export一样,将后面的值变成环境变量
# -r 将变量设置为readonly类型,该变量不可被更改,不能unset
declare # 输出所有变量名和变量值
sum=100+300+50 # sum=100+300+50
declare -i sum=100+300+50 # sum=450


```


# script

shell脚本不需要进行编译就能写出类似于程序一样的东西,类似于Windows的批处理命令.一般用shell脚本来进行服务器检测
追踪与管理系统工作: /etc/init.d/系统启动服务都在这个目录下,都是script./etc/init.d/rsyslogd restart其中的rsyslogd就是script.如今的/etc/init.d/*这个脚本启动方式被systemd所取代,但是个别服务启动还要使用shell script机制.
入侵检测功能: 系统异常时,会被记录下来,系统登陆档,定时去分析登陆档,若有异常,立刻加强防火墙设定,如果有人想要尝试登陆,应该立刻封掉其IP地址
连续指令一键执行: 直接执行一连串shell指令,防火墙规则设定,比如开机载入程序的项目/etc/rc.d/rc.local里的script
简易文本处理:可以处理文本数据资料
跨平台:几乎所有类unix都能运行script
CentOS早期软件用script来启动服务/etc/init.d,现在使用systemctl命令来管理服务





```bash




# 区分大小写





```








## script基础





```bash

# 指令的执行顺序是从上而下,从左往右执行
# 指令和选项参数之间的多个空白会被忽略
# 空行也被忽略,并且tab键被视为空格键
# 读取到一个CR符号,就尝试开始执行该行命令
# 如果一行内容太多,使用回车延伸至下一行
# 井号注释


# 写一个shell脚本
# 第一行告诉脚本使用的shell名称,并能加载~/.bashrc运行脚本
# 注释一般由内容与功能,版本信息,作者和联系方式,版权,创建日期修改日期,历史记录,版本号
# 环境变量PATH与LANG比较重要,这样程序运行时,可以直接使用外部命令,而不必写绝对路径
# 程序主体写好就行
# 返回值运行结果告知系统,$?可以得知程序运行成功与否
mkdir bin; cd bin
vim hello.sh
#!/bin/bash 
# Program:
#       This program shows "Hello World!" in your screen.
# History:
# 2015/07/16	VBird	First release
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin:~/bin
export PATH
echo -e "Hello World! \a \n"
exit 0


# 执行一个脚本必须要rx权限
# 使用绝对路径相对路径或者sh/bash执行脚本时,会在子程序执行的,子程序的变量和动作不影响父进程
/home/ubuntu/shell.sh # 绝对路径执行脚本
./shell.sh # 假设当前目录在家目录
shell.sh # PATH变量,将shell.sh的目录地址放在PATH目录中,如~/bin/
sh/bash shell.sh # 以sh或bash来执行shell.sh文件,这种情况shell仅需r权限即可执行
# source执行脚本,在父进程中执行
source set_val.sh
echo ${firstname} ${lastname} # 设置的变量会加载到环境变量中


# sh 检测shell脚本语法是否正确
# -c 后加字符串指令, 执行指令
# -n 不执行script,仅检查语法问题
# -v 执行script前,先将script的内容输出到屏幕上
# -x 将执行的script内容显示到屏幕上,跟踪执行过程
sh -c "echo 'Hello World!'"
sh -n shell.sh # 跟踪检查shell.sh语法是否正确
sh -x shell.sh # 显示shell.sh的执行指令过程




```


```bash

# 交互式脚本
vim showname.sh
read -p "Please input your first name: " firstname # 提示用户输入
read -p "Please input your last name: " lastname # 提示用户输入
echo -e "\nYour full name is: ${firstname} ${lastname}" # 结果输出


# 随时间变化的脚本
vim create3filename.sh
# 让使用者输入文件名称,并取得fileuser这个变量
echo -e "I will use 'touch' command to create 3 files." # 文字提示
read -p "Please input your filename: " fileuser # 提示用户输入
# 为了避免用户误按Enter,用变量检查是否有设置
filename=${fileuser:-"filename"} # 判断是否设置了文件名,没有则用默认值filename
# 用date指令指定部分文件名
date1=$(date --date='2 days ago' +%Y%m%d)  # 两天前的日期
date2=$(date --date='1 days ago' +%Y%m%d)  # 昨天的日期
date3=$(date +%Y%m%d)                      # 今天的日期
file1=${filename}${date1}                  # 设置文件名
file2=${filename}${date2}
file3=${filename}${date3}
# 建立文件名称
touch "${file1}" # 创建文件
touch "${file2}"
touch "${file3}"

# 数值运算
echo -e "You SHOULD input 2 numbers, I will multiplying them! \n"
read -p "first number:  " firstnu
read -p "second number: " secnu
total=$((${firstnu}*${secnu}))
echo -e "\nThe result of ${firstnu} x ${secnu} is ==> ${total}"
# declare -i total=${fistnu}*${secnu} 实现上面程序的功能
declare -i number=$RANDOM*10/32768 ; echo $number # 随机变成0-9之间的数值


# 用bc计算pi的值
vim cal_pi.sh
echo -e "This program will calculate pi value. \n"
echo -e "You should input a float number to calculate pi value.\n"
read -p "The scale number (10~10000) ? " checking
num=${checking:-"10"}           # 開始判斷有否有輸入數值
echo -e "Starting calculate pi value.  Be patient."
time echo "scale=${num}; 4*a(1)" | bc -lq
# 4*a(1)提供计算pi的函数


```



## 变量与运算


```bash
# 变量就是以一组文字或符号等,取代一些设定或者是一串文本,变量名通常大写
# MYNAME=VBird 变量设置不能有空格
# 变量名由数字和字母组成,但不能以数字开头,变量的值若有空白字符,用单引号或双引号括起来,单引号不会解析变量,双引号会解析变量
var="lang is $LANG" # lang is en_US.UTF-8 
var='lang is $LANG' # lang $LANG
# 在PATH后面追加值,三种方法都可以
PATH=$PATH:/home/dmtsai/bin
PATH="$PATH":/home/dmtsai/bin
PATH=${PATH}:/home/dmtsai/bin
# 转移符号\会转义特殊字符,'"\$`
NAME="VBird's name" # 需要用双引号括单引号
NAME=VBird\'s\ name # 转义单引号和空格
# 反单引号``,$(),可以提取命令的结果,
version=$(uname -r);echo $version; # Linux内核版本
# 进入内核模块,先用uname -r输出命令,再进入对应的目录
cd /lib/modules/`uname -r`/kernel
cd /lib/modules/$(uname -r)/kernel # 建议写法



# echo 输出一段文字或是变量
echo $PATH # 命令路径
echo ${PATH} # 另一种较推荐的格式
MYNAME=VBird
echo ${MYNAME} # VBird

"${HOME}" # 双引号内的变量用大括号
'This is it.' "Hello World" # 双引号或单引号来包含空格


# $((运算内容)) 计算式+-*/% echo $(( 13 % 3 )) 取余数
# declare 定义变量类型
# declare -i total=${fistnu}*${secnu} 实现上面程序的功能

# 运算小数
echo "123.123*55.9" | bc # 运算小数
echo {1..50}
echo $(seq 1 100)


```


## 条件判断



```bash

# test 测试指令
# 测试文件是否存在,测试文件类型
# -e 文件是否存在
# -f 是否存在,是否为文件
# -d 是否存在,是否为目录
# -b 是否存在,是否为block device
# -c 是否存在,是否为character device
# -S 是否存在,是否为Socket
# -p 是否存在,是否为FIFO
# -L 是否存在,是否为链接文件
test -e /opt/java && echo "exist" || echo "Not exist"
# 测试文件权限
# -r 是否存在,是否为可读
# -w 是否存在,是否为可写
# -x 是否存在,是否为可执行
# -u 是否存在,是否具有SUID属性
# -g 是否存在,是否具有SGID属性
# -k 是否存在,是否具有Sticjy bit属性
# -s 是否存在,是否为非空白文件
test -r filename
# 两个文件比较
# -nt 判断file1是否比file2新
# -ot 判断file1是否比file2旧
# -ef 判断file1与file2是否为同一个文件,可用在判断hardlink上面,判定是否指向一个inode
test file1 -nt file2
# 判断两个整数
# -eq 两数值相等
# -ne 两数值不等
# -gt n1大于n2
# -lt n1小于n2
# -ge n1大于等于n2
# -le n1小于等于n2
test n1 -eq n2
# 判断字符串
test -z string # 判断字符串是否为0,若string为空,则为true
test -n string # 判断字符串是否非0,若string为空,则为false,可省略
test str1 == str2 # 判断str1是否等于str2,若相等,则为true
test str1 != str2 # 判断str1是否不等于str2,若相等,则为false
# 多重条件判断
# -a 两种状况同时成立,如test -r file -a -x file,则file同时具有rx权限才返回true
# -o 两种状况任何一个成立,如test -r file -o -x file,则file具有r或x返回true
# ! 相反状态,如test ! -x file,当file不具有x,返回true
test -r filename -a -x filename


# 判断一个文件是否存在,并输出文件类型,权限信息,建议使用普通用户来执行脚本,root用户权限无效
vim file_perm.sh
# 用户输入文件名,判断用户是否输入内容
echo -e "Please input a filename, I will check the filename's type and permission. \n\n"
read -p "Input a filename : " filename
test -z ${filename} && echo "You MUST input a filename." && exit 0
# 判断文件是否存在,若不存在结束脚本
test ! -e ${filename} && echo "The filename '${filename}' DO NOT exist" && exit 0
# 判断文件类型与属性
test -f ${filename} && filetype="regulare file"
test -d ${filename} && filetype="directory"
test -r ${filename} && perm="readable"
test -w ${filename} && perm="${perm} writable"
test -x ${filename} && perm="${perm} executable"
# 输出信息
echo "The filename: ${filename} is a ${filetype}"
echo "And the permissions for you are : ${perm}"


```



```bash
# $? && || 判断式

[] # 判断符合,中括号两端有空格区分
[ -z "${HOME}" ] ; echo $? # 判断HOME变量是否为空

NAME="Hello World!" # 设定变量
[ ${NAME} == "Hello World!" ] # 判断式有误, [ Hello World! == "Hello World!"]
[ "${NAME}" == "Hello World!" ] # 加上双引号才能正确判断结果


# 判断用户输入的Y/N
vim ans_yn.sh
read -p "Please input (Y/N): " yn
[ "${yn}" == "Y" -o "${yn}" == "y" ] && echo "OK, continue" && exit 0
[ "${yn}" == "N" -o "${yn}" == "n" ] && echo "Oh, interrupt!" && exit 0
echo "I don't know what your choice is" && exit 0


```


```bash

# 脚本选择参数
# $0是执行命令的软件或脚本
# $1/2/... 第一/二/...个参数
# $# 参数的总个数
# $@ 表示 "$1" "$2" "$3" "$4" 中间每个变量时独立的,当参数中含有双引号时,建议使用"$@"
# $* 表示 "$1c$2c$3c$4" c表示分隔符,默认是空格

vim how_paras.sh
echo "The script name is        ==> ${0}"
echo "Total parameter number is ==> $#"
[ "$#" -lt 2 ] && echo "The number of parameter is less than 2.  Stop here." && exit 0
echo "Your whole parameter is   ==> '$@'"
echo "The 1st parameter         ==> ${1}"
echo "The 2nd parameter         ==> ${2}"
shift 3 # 可以进行参数偏移
echo "$@" # 拿掉了前三个参数

bash how_paras.sh theone haha qout

```


```bash

# && 表示 AND,先执行第一个,如果为false则退出,为true则执行后一个
# || 表示 OR,先执行第一个,如果为true则退出,为false则执行后一个

if [ 条件判断 ] ; then
    程序正文
fi

if [ 条件判断 ] ; then
    程序正文
elif [ 条件判断 ] ; then
    程序正文
else
    程序正文
fi


# 判断用户输入的Y/N
read -p "Please input (Y/N): " yn
if [ "${yn}" == "Y" ] || [ "${yn}" == "y" ]; then
	echo "OK, continue"
elif [ "${yn}" == "N" ] || [ "${yn}" == "n" ]; then
	echo "Oh, interrupt!"
else
	echo "I don't know what your choice is"
fi


# 判断用户输入的参数是否合法
if [ "${1}" == "hello" ] ; then
    echo "Hello, how are you ?"
elif [ "${1}" == "" ] ; then
    echo "You MUST input parameters,ex> {${0} someword}"
else
    echo "The only parameter is 'hello',ex> {${0} hello}"
fi



```




```bash

# netstat -tuln 获取当前开放的端口


# 检测端口开放情况 21 22 25 80
# 发出警告信息
echo "Now, I will detect your Linux server's services!"
echo -e "The www, ftp, ssh, and mail(smtp) will be detected! \n"
# 检测端口是否开启
testfile=/dev/shm/netstat_checking.txt
netstat -tuln > ${testfile}          # 把信息保存在文件,避免重复调用netstat命令
testing=$(grep ":80 " ${testfile})   # 检测80端口
if [ "${testing}" != "" ]; then
	echo "WWW is running in your system."
fi
testing=$(grep ":22 " ${testfile})   # 检测22端口
if [ "${testing}" != "" ]; then
	echo "SSH is running in your system."
fi
testing=$(grep ":21 " ${testfile})   # 检测21端口
if [ "${testing}" != "" ]; then
	echo "FTP is running in your system."
fi
testing=$(grep ":25 " ${testfile})   # 检测25端口
if [ "${testing}" != "" ]; then
	echo "Mail is running in your system."
fi

```



```bash

# 计算两个日期之间的天数差
# 输出信息,指定输入日期格式
echo "This program will try to calculate :"
echo "How many days before your demobilization date..."
read -p "Please input your demobilization date (YYYYMMDD ex>20150716): " date2
# 检测输入内容是否正确
date_d=$(echo ${date2} |grep '[0-9]\{8\}')   # 八位数
if [ "${date_d}" == "" ]; then
	echo "You input the wrong date format...."
	exit 1
fi
# 3. 開始計算日期囉～
declare -i date_dem=$(date --date="${date2}" +%s)      # 结束日期秒数
declare -i date_now=$(date +%s)                        # 当前日期秒数
declare -i date_total_s=$((${date_dem}-${date_now}))   # 剩余秒数统计
declare -i date_d=$((${date_total_s}/60/60/24))        # 转为天数
if [ "${date_total_s}" -lt "0" ]; then                 # 判断时间是否到期
	echo "You had been demobilization before: " $((-1*${date_d})) " ago"
else
	declare -i date_h=$(($((${date_total_s}-${date_d}*60*60*24))/60/60))
	echo "You will demobilize after ${date_d} days and ${date_h} hours."
fi



```



```bash

# case in case

# 检测变量值是否为hello
case $变量名 in
    "hello") # 变量内容用双引号括起来,关键字为小括号
        echo "Hello, how are you?"
        ;; # 结尾用;;处理
    "")
        echo "You MUST input parameters,ex> {${0} someword}"
        ;;
    *) # 用*代表其他值
        echo "Usage ${0} {hello}"
        ;;
esac




# 检测第一个参数参数的值
echo "This program will print your selection !"
# read -p "Input your choice: " choice   # 与用户交互的形式检测
# case ${choice} in                      # 用参数的值进行检测
case ${1} in                             # 第一个参数
  "one")
	echo "Your choice is ONE"
	;;
  "two")
	echo "Your choice is TWO"
	;;
  "three")
	echo "Your choice is THREE"
	;;
  *)
	echo "Usage ${0} {one|two|three}"
	;;
esac

```








## 循环


```bash

# 条件成立就一直执行
while [ condition ]
do
    程序体
done

# 条件不成立则一直执行
until [ condition ]
do
    程序体
done

# 循环n次,第一次var为con1,第二次var为con2,第三次var为con3
for var in con1 con2 con3
do
    程序体
done
# 循环10次
for var in $(seq 1 10)
do
    程序体
done
# 循环10次另一种写法
for (( i=1; i<=${nu}; i=i+1 ))
do
    程序体
done


```


```bash
# 查看这个目录是否存在
read -p "Please input a directory: " dir
if [ "${dir}" == "" -o ! -d "${dir}" ]; then
    echo "The ${dir} is NOT exist in your system."
    exit 1
fi
# 开始测试目录
filelist=$(ls ${dir}) # 列出该目录下的所有文件名
for filename in ${filelist}
do
    perm=""
    test -r "${dir}/${filename}" && perm="${perm} readable"
    test -w "${dir}/${filename}" && perm="${perm} writable"
    test -x "${dir}/${filename}" && perm="${perm} executable"
    echo "The file ${dir}/${filename}'s permission is ${perm} "
done



```



## 函数

```bash

# 函数要放在脚本的最前面
function fname() {
    程序体
}

function fname(one,two,three) {
    程序体
    $0 # 函数名
    $1 # 第一个参数
    $2 # 第二个参数
    $3 # 第三个参数
}


# 函数
function printit(){
    echo -n "Your choice is " # -n 表示不换行输出,后面的内容在末尾接上
}
echo "This program will print your selection !"
case ${1} in
  "one")
    printit; echo ${1} | tr 'a-z' 'A-Z'  # 转化参数大小写
    ;;
  "two")
    printit; echo ${1} | tr 'a-z' 'A-Z'
    ;;
  "three")
    printit; echo ${1} | tr 'a-z' 'A-Z'
    ;;
  *)
    echo "Usage ${0} {one|two|three}"
    ;;
esac


# 函数的参数
function fname(){
    echo $0 # 函数名称
    echo $1 # 函数的第一个参数
    echo $2 # 函数的第二个参数
}

echo "Hello World!"
fname 1 2 3


```

