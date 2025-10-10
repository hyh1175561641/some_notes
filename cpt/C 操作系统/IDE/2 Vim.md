
Red Hat與 Fedora 的 ntsysv 與 setup 等，而
SuSE 則有 YAST 管理工具等等


https://neovim.io/


# vim

https://www.vim.org/



```bash
# 常用操作流程

**情景1：修改配置文件**

打开文件>光标移动到需要修改的地方>进入编辑模式>修改完毕>退出


**情景2：在一个文件内查找一个单词**


**情景3：**

```

```bash

# 基础操作
双层命令的操作，会在最下行的右侧显示一个符号：d >
### 文件

普通模式 编辑模式 可视模式 命令行模式



### 增删改查

**删除**
x和delete 删除光标处的字符
dd 删除一整行，包括换行符

**缩进**
>G 当前行到最后一行的缩进层级


在插入模式中移动光标会重置修改状态。
**修改状态的连环操作**
u撤销上次操作

点操作重复上次修改：普通模式下使用点操作，从进入编辑模式到退出编辑模式的一连串操作，可以用点号来快速操作。可以看做是一个宏。

```









# new

# 学习VI和VIM编辑器

《Vim实用技巧》[美]Drew Neil 著 人民邮电出版社 ISBN 978-7115338693
《学习vi和Vim编辑器》[美]罗宾斯 著 东南大学出版社 ISBN 978-7564126049


1 vi文本编辑器
2
3
4
5
6
7

vim实用技巧
1 技巧1
2



# vim

http://www.vim.orgs

行编辑器 ed与ex
全屏编辑器 vi emacs
emacs pico nano joe

有些软件的界面会调用vi(crontab,visudo,edquota等指令)

vi(visual editor)最有用的标准文本编辑器,有编程能力高亮代码显示,所有的类unix系统都会内置vi文本编辑器,全屏编辑器可以翻页,移动光标,删除一整行,插入文字等,而且能立刻看到修改结果.
vim是vi的高级版,会根据文件拓展名判断文件类型,甚至能识别一些Linux设定的文件内容语法,如/etc/fstab,/etc/services
vim具有正则搜索,多文件编辑,区块复制


命令模式(command mode),默认模式,可以查看文件内容,删除复制文件内容,移动光标
编辑模式(insert mode),ioaR进入编辑模式,编写删除复制粘贴等操作,信息栏显示INSERT或REPLACE等字样,ESC退出编辑模式
指令列模式(command line mode),一般模式中,摁下:/?三个键,光标移到最下面的一行,进入指令模式,ESC退出指令列模式







# 指令列功能

:w 保存
:q 退出
:wq 保存后退出
:q! 强制退出
:ZZ 保存文件并退出
:w filename 将文件保存成另一个文件
:r filename 把新文件的内容粘贴到光标之后
:n1,n2 w filename 把n1到n2行的内容保存成另一个文件
:! command 离开vi,执行Linux命令并显示结果













# 指令功能

i 光标处开始插入
I 当前列第一个非空白字符插入
a 字符之后追加内容
A 当前列的行尾插入字符
o 下一行插入内容
O 上一行开始插入内容
r 替换光标处的字符一次,修改一个字符
R 替换文本
cw 更改字词
u 还原上一个动作,撤销
Ctrl+r 重复前一个动作
. 小数点,重复前一个动作

:set nu 设定配置参数,显示行号


# 状态栏
路径和文件名
是否只读


列数和字符数
百分比 文件所处的大致位置



# 编辑功能
## 光标移动

hjkl 左下上右
30j 加上数字,向下移动30行

H 移动到屏幕最上面第一个字符
M 移动到屏幕中间的字符
L 移动到屏幕最下面的字符
G 移动到文件最后一列
20G 数字加G,移动到第几行
gg 移动到文件第一行第一个字符,相当于1G


Ctrl+f 向下移动一页,类似PageDown
Ctrl+b 向上移动一页,类似PageUp
Ctrl+d 向下移动半页
Ctrl+u 向上移动半页

+/- 光标移动到非空白字符的下一列/上一列
n<space> 数字加空格,向后移动n个字符,一行不够会到下一行
n<Enter> 数字加回车,向下移动n行

0 移动到这行的第一个字符,类似Home
$ 移动到这行的最后一个字符,类似End






## 文本选择

v 字符选择,光标处反色表示开启选择
V 列选择,光标经过的列反色,表示开启选择
Ctrl+v 区块选择,光标经过的矩形反色,表示开启选择

y 复制所选的内容
d 删除所选的内容
p 粘贴刚才复制的内容


## 删除复制粘贴

x/X 删除后面/前面的一个字符
nx 数字加x,连续删除n个字符
dd 删除一行
ndd 数字加dd,连续删除向下n列
d1G 删除光标处到第一列的所有内容
dG 删除光标处到文件末尾的所有内容
d$ 删除光标处到行尾的内容
d0 删除光标处到行首的内容
c 重复删除多个内容,向下删除10列,10cj

yy 复制一行
nyy 复制向下的n行
y1G 复制光标到第一行的所有内容
yG 复制光标到最后一行的所有内容
y0 复制光标到行首的内容
y$ 复制光标到行尾的内容

p 已复制的内容粘贴到下一行
P 已复制的内容粘贴到上一行

J 将光标所在的列与下一列合并,类似于删掉末尾的换行符



# 搜索替换

/word 向下搜索word这个单词
?word 向上搜索word这个单词
n 重复前一次的搜索动作
N 反向进行前一次的搜索动作


:n1,n2s/word1/word2/g 在n1与n2之间搜索word1这个字符,并替换成word2
:1,$s/word1/word2/g 从第一行到最后一行搜索word1并替换成word2
:1,$s/word1/word2/gc 第一行到最后一行搜索并替换,替换时提问是否进行操作

# 多文件编辑

vim a.c b.c c.c 开启多个文件

:n 编辑下一个文件
:N 编辑上一个文件
:files 列出当前打开的文件







# 视图功能


:sp 向下开启一个窗口,默认打开同一个文件

Ctrl+w 松开 j/下箭头 移动到下一个视图
Ctrl+w k/上箭头 移动到上一个视图


# 补全功能

Ctrl+x Ctrl+n 根据文件内容进行补全
Ctrl+x Ctrl+f 根据当前目录文件名进行补全
Ctrl+x Ctrl+o 根据文件拓展名内置关键字进行补全



# 配置文件

~/.viminfo 记录你的对vim的操作



~/.vimrc vim的配置参数 全局vim配置参数/etc/vimrc不建议修改,可以修改~/.vimrc文件,默认不存在,需要手动建立,写入你希望的参数设定
也可以在vi编辑器中,命令行列中输入这些设定参数
:set nu/nonu 显示/隐藏行号
:set hlsearch/nohlsearch 默认hlsearch,高亮查询(high light search),是否将搜索的字符串反色
:set autoindent/noautoindent 是否自动缩进<tab>
:set backup 默认nobackup,是否自动备份,如果开启,修改某个文件会自动备份filename~(文件末尾添加~)
:set ruler 是否显示状态列
:set showmode 是否显示--INSERT--之类的信息
:set backspace=(012) 一般情况i进入编辑模式可以删除任意字符,但是某些版本,值为2时可以删除任意字符,0或1仅能删除刚刚输入的字符,无法删除原本就已存在的文字
:set all 显示目前所有的环境参数(配置参数)的值
:set 显示与系统默认值不同的参数值,就是你自己设定的参数值
:syntax on/off 是否高亮显示不同文件的语法
:set bg=dark/light 可以显示不同的颜色主题,默认light

```vimrc
vim ~/.vimrc
"双引号是注释
set hlsearch            "高亮反色
set backspace=2         "可删除任意字符
set autoindent          "自动缩进
set ruler               "显示最后一列的状态
set showmode            "左下角一列的状态
set nu                  "显示行号
set bg=dark             "主题颜色
syntax on               "语法检查


```



# 恢复与警告




如果电脑死机或者发生意外,客户端与服务器断开连接
vim会在目录下建立一个暂存档,你的操作都放在.filename.swp文件中,开头点表示隐藏文件,末尾追加.swp后缀

```bash

cd /tmp/vitest
vim man_db.conf # Ctrl+z 挂起
ls -al # man_db.conf man_db.conf.swp暂存档
kill -9 %1 # 模拟vim断线停止工作
ls -al # man_db.conf.swp 暂存档依然存在

# 可能有其他用户或程序正在操作这个文件,找到那个人并进行沟通,或者只读模式打开
# 突发原因中断,R恢复原先的操作状态,保存好后自行删除.swp文件.D删除掉swp文件
vim man_db.conf # 会报错,然后询问你接下来的动作
[O]pen Read-Only, (E)dit anyway, (R)ecover, (D)elete it, (Q)uit, (A)bort:  
只读模式, 正常打开文件并编辑容易造成冲突, 挽救未保存的工作, 删掉暂存文件, 退出, 忽略编辑行为


```




# 其他问题

中文编码问题

Linux系统支持的语言与/etc/locale.conf有关
终端界面的语言与LANG,LC_ALL两个变量有关
你的文件原本的编码是什么
开启终端的软件,如GNOME窗口界面


换行符 CR(^M) LF($)
CRLF DOS
LF Linux
MaxOS

```bash
# 用光盘下载字符转换软件
su -
mount /dev/sr0/mnt
rpm -ivh /mnt/Packages/dos2unix-*
umount /mnt
exit


# dos2unix unix2dos
# -k 保留原本的mtime时间格式(不更新上次内容修改时间)
# -n 保留原本的文件,将转换后的内容输出到新文件
dos2unix -n old new # 输出新文件
dos2unix -k -n man_db.conf man_db.conf.linux # 保留原文件,生成新文件,保留修改时间
file man_db.conf* # CRLF换行
unix2dos -k man_db.conf # 把文件转换成dos格式,保留原文件修改时间
ll man_db.conf # 文件容量增大了

```


编码格式的转换

```bash
# iconv 转换编码
# -l --list 列出iconv支持的编码
# -f from来源,后接文件原本的编码格式
# -t to,新文件的编码是什么格式
# -o file 保留原文件,新文件指定名字
iconv -f big5 -t utf8 vi.big5 -o vi.utf8 # 把原来的big5转换成utf8格式,并指定新文件名
file vi* # vi.big5是ISO-8859 CRLF vi.utf8是UTF-8 Unicode CRLF格式

iconv -f utf8 -t big5 vi.utf8 | iconv -f big5 -t gb2312 | iconv -f gb2312 -t utf8 -o vi.gb.utf8 # utf8->big5->gb2312->utf8 繁体中文转换成简体中文




```





```






