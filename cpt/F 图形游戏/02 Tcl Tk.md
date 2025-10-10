Tcl Developer Site https://www.tcl.tk
Tcl Developer Site http://www.tcl-lang.org/
source http://www.tcl-lang.org/software/tcltk/download.html
vue5 http://www.vue5.com/tcl-tk/tcl-tk.html


# TCL
tclsh是命令行脚本
wish (windowing shell)是图形界面脚本
tk库



```tcl
# 安装

```

```tcl
# 运行脚本文件

# 开头的两种方式,在现代Unix中，可以使用这两种方式
#!/usr/local/bin/wish
#!/usr/bin/env wish

# 如果脚本文件的第一行超过32个字符，系统会出现错误，最好不要让wish安装位置的全路径长于27个字符
# 三行开头

#!/bin/sh
# Tcl ignores the next line but 'sh' doesn't \
exec wish "$0" "$@"

# 更复杂更健壮的三行代码
#!/bin/sh
# Tcl ignores the next line but 'sh' doesn't \
exec wish "$0" ${1+"$@"}
```
```tcl
# hello.tcl
button .b -text "Hello World!" -command exit
pack .b

# 使用wish解释器执行脚本，wish hello.tcl
chmod +x hello.tcl 可以直接执行脚本文件
```

**解释器中运行文件**

开发者用来调试的时候，一边使用脚本，一边查看命令

```sh
$ wish
% source hello.tcl # 交互式解释器运行脚本
% destroy .b # 删除已经存在的按钮
% source hello.tcl
```



# 基本语法

```tcl
#命令和单词
命令相当于语句，通过换行符或者分号隔开
第一个单词是命令名，其他的单词是命令的参数
单词通过空格或制表符隔开，这种符号通常被称为空白符或空白

```

```tcl
# 用换行符或者分号隔开
set a 10
set b 20; set c 30;
```

## 处理命令

处理命令分为解析和执行

解析：把命令用简单的字符串方法分解为单词，并把部分单词进行替换（类似于宏替换）

执行：如果命令已经被定义，则根据参数执行所定义的过程



```tcl
# 这是单行注释
# 注释可以帮助开发人员调试代码
```

# 变量

```tcl
# command
append varName value ?value? 
set varName ?value? #设置变量


```

```tcl
# tcl变量有两种，简单变量和关联数组
# 变量名可以是任意字符串，区分大小写,通常是字母数字下划线组成
# 简单变量可以代表：整数 实数 名称 列表 以及tcl脚本
# 储存tcl变量时，只是简单的存储为字符串，使用的时候才对其解析
# 如果程序在字符串和变量来回转换，应该使用特别的命令，见书31页

set a 12.6 # 返回a的值
set a {Hello World Hello World}
set a [expr $a + 1.2] # set命令可以覆盖以前的值
append valName ?value? #在后面追加一段字符串
set a 3.14;append a 15926 # $a 3.1415926

# 数组内部是一个大哈希表
set arr(a) 11
set arr(b) 22
set arr(c) 33
$arr(a) # 11
```

```tcl
# 变量替换
# $后面的变量名将被替换成字符串
# 第一个不是字母数字下划线的字符表示$变量名的结束
# 如果$后面接的不是字母数字下划线，$当作文本处理

54页
```

```tcl

expr 运算

```

# TK组件
Perl,Python,Ruby都采用了tk。
tk组件可以为已有的 应用程序添加用户界面，Tcl解释器可以嵌入应用程序， 可以用Tcl命令来驱动一个命令行应用程序，然后用Tk 组件来引入一个用户界面
许多新主题组件不能提供早期组件的全部功能

```tcl
# 经典TK组件三要素：配置选项 组件命令 默认绑定
# 配置选项是状态信息，如按钮的颜色字体文本
button .top -text "Top Button"


```
```tcl
# 安排组件
grid
```



TclTk入门经典
1x
2x
3v 3.2 3.3 3.4


18








