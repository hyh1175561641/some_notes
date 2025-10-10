
















https://ipython.org/ IPython Jupyter




https://www.anaconda.com/
https://www.anaconda.com/docs/main





C:\ProgramData\anaconda3
C:\ProgramData\anaconda3\Library\usr\bin
C:\ProgramData\anaconda3\Library\mingw-w64
C:\ProgramData\anaconda3\Library\bin
C:\ProgramData\anaconda3\Scripts





# introduction

简介

Python是一种解释型、面向对象、动态数据类型的高级程序设计语言。

Python 是一个高层次的结合了解释性、编译性、互动性和面向对象的脚本语言。 

Python 的设计具有很强的可读性，相比其他语言经常使用英文关键字，其他语言的一些标点符号，它具有比其他语言更有特色语法结构。

- Python 是一种解释型语言： 这意味着开发过程中没有了编译这个环节。类似于PHP和Perl语言。
- Python 是交互式语言： 这意味着，您可以在一个 Python 提示符 >>> 后直接执行代码。
- Python 是面向对象语言: 这意味着Python支持面向对象的风格或代码封装在对象的编程技术。
- Python 是初学者的语言：Python 对初级程序员而言，是一种伟大的语言，它支持广泛的应用程序开发，从简单的文字处理到 WWW 浏览器再到游戏。

## 历史

Python由Guido van Rossum于1989年底发明，第一个公开发行版发行于1991年。Python源代码遵循GPL(GUN General Public License) 协议。（在八十年代末和九十年代初，在荷兰国家数学和计算机科学研究所设计出来的）

Python2.0于2000年10月16日发布，增加了实现完整的垃圾回收，并且支持Unicode

Python 3.0 于 2008 年 12 月 3 日发布，此版不完全兼容之前的 Python 源代码。不过，很多新特性后来也被移植到旧的Python 2.6/2.7版本

Python2.7被确定为最后一个Python2.x版本

Python3.0版本，常被称为Python3000，或简称Py3k。相当于Python的早期版本，这是一个较大的升级。Python3.0在设计的时候没有考虑向下兼容

官方宣布，2020 年 1 月 1 日， 停止 Python 2 的更新。

## 运行环境

安装Python3

配置环境变量

```
安装模块
python3 -m pip install xxx
```



## 开发环境

**Anconda**

Anaconda包括Conda、Python以及一大堆安装好的工具包

conda是一个开源的包、环境管理器，可以用于在同一个机器上安装不同版本的软件包及其依赖，并能够在不同的环境之间切换

vim emacs sublime

PyCharm

Eclipse with Pydev

Komodo Edit

Wing

PyScripter

The Eric Python IDE

Interactive Editor for Python

[官网收集的Python IDE](https://wiki.python.org/moin/PythonEditors)

# 基础语法

[Python入门指南](https://docs.python.org/3/tutorial/appetite.html)      [Python入门指南 中文手册](https://www.runoob.com/manual/pythontutorial3/docs/html/)

## 命令行

**命令行交互式编程**

略，用处不大

检测一个包是否成功安装时，import引入一下



**脚本文件**

```python
#!/usr/bin/python3
#!/usr/bin/env python3
# -*- coding: utf-8 -*-  指定编码
print("Hello World!")
```
```bash
$ python3 hello.py #执行脚本
$ chmod +x hello.py #授予权限
$ ./hello.py #执行脚本
```

**命令行参数**

```bash
$ python3


-d #在解析时显示调试信息
-O #生成优化代码(.pyo文件)
-S #启动时不引入查找Python路径的位置
-V #输出Python版本号
-X #已过时
-c cmd #执行Python脚本，并将运行结果作为cmd字符串
file #执行给定文件
```

[命令行参数](https://www.runoob.com/python3/python3-command-line-arguments.html)

```
$ python3 --help
usage: /usr/local/Cellar/python/3.7.6_1/Frameworks/Python.framework/Versions/3.7/Resources/Python.app/Contents/MacOS/Python [option] ... [-c cmd | -m mod | file | -] [arg] ...
Options and arguments (and corresponding environment variables):
-b     : issue warnings about str(bytes_instance), str(bytearray_instance)
         and comparing bytes/bytearray with str. (-bb: issue errors)
-B     : don't write .pyc files on import; also PYTHONDONTWRITEBYTECODE=x
-c cmd : program passed in as string (terminates option list)
-d     : debug output from parser; also PYTHONDEBUG=x
-E     : ignore PYTHON* environment variables (such as PYTHONPATH)
-h     : print this help message and exit (also --help)
-i     : inspect interactively after running script; forces a prompt even
         if stdin does not appear to be a terminal; also PYTHONINSPECT=x
-I     : isolate Python from the user's environment (implies -E and -s)
-m mod : run library module as a script (terminates option list)
-O     : remove assert and __debug__-dependent statements; add .opt-1 before
         .pyc extension; also PYTHONOPTIMIZE=x
-OO    : do -O changes and also discard docstrings; add .opt-2 before
         .pyc extension
-q     : don't print version and copyright messages on interactive startup
-s     : don't add user site directory to sys.path; also PYTHONNOUSERSITE
-S     : don't imply 'import site' on initialization
-u     : force the stdout and stderr streams to be unbuffered;
         this option has no effect on stdin; also PYTHONUNBUFFERED=x
-v     : verbose (trace import statements); also PYTHONVERBOSE=x
         can be supplied multiple times to increase verbosity
-V     : print the Python version number and exit (also --version)
         when given twice, print more information about the build
-W arg : warning control; arg is action:message:category:module:lineno
         also PYTHONWARNINGS=arg
-x     : skip first line of source, allowing use of non-Unix forms of #!cmd
-X opt : set implementation-specific option
--check-hash-based-pycs always|default|never:
    control how Python invalidates hash-based .pyc files
file   : program read from script file
-      : program read from stdin (default; interactive mode if a tty)
arg ...: arguments passed to program in sys.argv[1:]

Other environment variables:
PYTHONSTARTUP: file executed on interactive startup (no default)
PYTHONPATH   : ':'-separated list of directories prefixed to the
               default module search path.  The result is sys.path.
PYTHONHOME   : alternate <prefix> directory (or <prefix>:<exec_prefix>).
               The default module search path uses <prefix>/lib/pythonX.X.
PYTHONCASEOK : ignore case in 'import' statements (Windows).
PYTHONUTF8: if set to 1, enable the UTF-8 mode.
PYTHONIOENCODING: Encoding[:errors] used for stdin/stdout/stderr.
PYTHONFAULTHANDLER: dump the Python traceback on fatal errors.
PYTHONHASHSEED: if this variable is set to 'random', a random value is used
   to seed the hashes of str, bytes and datetime objects.  It can also be
   set to an integer in the range [0,4294967295] to get hash values with a
   predictable seed.
PYTHONMALLOC: set the Python memory allocators and/or install debug hooks
   on Python memory allocators. Use PYTHONMALLOC=debug to install debug
   hooks.
PYTHONCOERCECLOCALE: if this variable is set to 0, it disables the locale
   coercion behavior. Use PYTHONCOERCECLOCALE=warn to request display of
   locale coercion and locale compatibility warnings on stderr.
PYTHONBREAKPOINT: if this variable is set to 0, it disables the default
   debugger. It can be set to the callable of your debugger of choice.
PYTHONDEVMODE: enable the development mode.
```





pip

```bash
pip install re # 在线安装
pip install re.whl # 源码安装 
这里下载whl文件https://pypi.org/project/redis/#description
```



## 规则

**标识符**

- 区分大小写
- 第一个字符是字母表中的字母或下划线_
- 其他部分字符是由字母、数字和下划线组成
- 变量名采用C风格，用下划线隔开不同的单词

**保留字**

```bash
# 保留字即是关键字，不能与标识符起冲突
# Python标准库提供了一个keyword模块,可以输出当前版本的所有关键字
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

**缩进**

Python用缩进来表示代码块，不需要使用大括号{}

缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数

**多行语句**

```python
# Python语句如果很长，可以用反斜杠来实现多行语句
total = item_one + \
        item_two + \
        item_three

# 在(),[],{}中的多行语句，不需要使用反斜杠
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

**注释**

```python
# Python中单行注释以#开头

'''
多行注释可以用''' '''和"""  """
'''
```



**编程规范**

[编码规范](https://www.runoob.com/w3cnote/google-python-styleguide.html)



## 数据类型

可以使用del语句删除一些数字对象的引用

```python
del var, var1, var2
```



### Number 数字

Python数字数据类型用于存储数值

**int整数**

```python
var a=10;
var 
```

**bool布尔值**

**float浮点数**

**complex复数**

**十六进制八进制二进制**

```
0xAF # 175
010 # 8
0b1011010010 # 722
```





**复合数据类型**

Python支持一种数据结构的基本概念，名为容器(container)。容器基本上就是可包含其 他对象的对象。

两种主要的容器是序列(如列表和元组)和映射(如字典)。在序列中， 每个元素都有编号，而在映射中，每个元素都有名称(也叫键)。 有一种既不是序列也不是映射的容器，它就是集合(set) 。

**Sequence序列**

python中有三种序列，列表元组字符串

```python
# 通用序列操作，包括索引、切片、相加、相乘、成员资格检查。另外，python还提供了一些内置函数，可用于确定序列的长度以及找出序列中最大和最小元素
# 索引，序列的编号从0开始递增，取负值时从右边开始取值
greeting = 'Hello'
greeting[0] #'H'
greeting[-1] # 'o'
'Hello'[1] # 'e' 可以直接对字符串字面量进行操作

>>> fourth = input('Year: ')[3]
Year: 2005
>>> fourth
'5' # 可以直接对函数的返回值进行操作
```

```python
# 切片，访问特定范围内的元素，使用两个索引，用冒号分隔
tag = '<a href="http://www.python.org">Python web site</a>'
tag[9:30] # 'http://www.python.org'
tag[32:-4] # 'Python web site'

numbers = [1,2,3,4,5,6,7,8,9,10]
numbers[3:6] # [4,5,6]
numbers[0:1] # [1]  第一个元素包含在内，第二个不包含
numbers[7:10] # [8,9,10] 索引10并不存在，但是要这样写
numbers[-3:0] # [] 如果第一个索引在第二个的后面，则空
numbers[-3:] # [8,9,10] 省略第二个索引到最后
numbers[:3] # [1,2,3] 省略第一个索引从开始到索引
numbers[:] # [1,...,10] 复制整个索引两个都省略

numbers[0:10:1] # [1,...,10] 步长是1
numbers[0:10:2] # [1,3,5,7,9] 步长是2
numbers[::4] # [1,5,9] 步长是4
numbers[8:3:-1] # [9,8,7,6,5] 步长为负数，从右向左提取元素
numbers[10:0:-2] # [10,8,6,4,2]
numbers[0:10:-2] # []
numbers[::-2] # [10,8,6,4,2]
numbers[5::-2] # [6,4,2] 起点索引是5，逐步减2
numbers[:5:-2] # [10,8] 终点索引是5，逐步减2
```

```python
# 序列相加
[1,2,3] + [4,5,6] # [1,2,3,4,5,6]
'Hello,' + 'World!' # 'Hello,World!'
[1,2,3] + 'Hello' # 错误，不能拼接不同类型的序列

# 乘法
'python' * 5 # 'pythonpythonpythonpythonpython'
[42] * 10 # [42,42,42,42,42,42,42,42,42,42]
[None] * 10 # [None,...,None] 包含10个元素的列表

# 成员资格，检查特定的值是否包含在序列中，可使用运算符in
'w' in 'rw' # True
'x' in 'rw' # False
'mlh' in ['mlh','foo','bar'] # True 
'$$$' in '$$$ Get rich now!!! $$$'# True 不仅仅是字符，还能检查子字符串

# 内置函数 长度 最小值 最大值
numbers = [100,34,678]
len(numbers) # 3
max(numbers) # 678
min(numbers) # 34
max(2,3) # 3 可以直接将数作为实参
min(9,3,2,5) # 2
```



### String 字符串

标准序列操作（索引 切片 乘法 成员资格检查 长度 最小值 最大值）都适用于字符串

字符串还有拆分 合并 查找等功能

```python
# 字符串是不可变的，不能元素赋值和切片赋值
website = 'http://www.python.org'
website[-3:] = 'com' # 错误

# 字符串格式，类C风格的printf
# 可以使用单个值(如字符串或数字)，可使用元组(如果要设置多个值的格式)，还可使用字典，但最常用的是元组
format = "Hello, %s. %s enough for ya?"
values = ('world', 'Hot')
format % values#'Hello, world. Hot enough for ya?'

# 模板字符串，类似于UNIX shell的格式
# 包含等号的参数称为关键字参数
from string import Template
tmpl = Template("Hello, $who! $what enough for ya?") tmpl.substitute(who="Mars", what="Dusty")
  #'Hello, Mars! Dusty enough for ya?'

# 字符串方法format，用花括号括起替换字段，其中包含名称
"{}, {} and {}".format("first", "second", "third") 
  # 'first, second and third'
"{0}, {1} and {2}".format("first", "second", "third")
  # 'first, second and third' 把索引当做名称
"{3} {0} {2} {1} {3} {0}".format("be","not","or","to") 
  # 'to be or not to be' 索引不需要排列
from math import pi
"{name} is approximately {value:.2f}.".format(value=pi, name="π")
  # 'π is approximately 3.14.' 命名字段
"{name} is approximately {value}.".format(value=pi, name="π")
  # 'π is approximately 3.141592653589793.' 上一个例子，不指定2f




#



```

```python
# 字符串方法
```

```python
encode 转换编码格式
decode 解码，把二进制的字符串解开
```




```python




# capitalize
# casefold
# center 在两边添加填充字符让字符居中
"The Middle by Jimmy Eat World".center(39)
  # '     The Middle by Jimmy Eat World     '
"The Middle by Jimmy Eat World".center(39, "*")
  # '*****The Middle by Jimmy Eat World*****'

# count
# encode
# endswith
# expandtabs
# find 在字符串中查找子串，如果找到则返回索引，没找到返回-1
# 注意：字符串返回0是找到了字符串，所以不能用作布尔判断
'With a moo-moo here, and a moo-moo there'.find('moo') # 7
title = "Monty Python's Flying Circus"
title.find('Monty') # 0
title.find('Python') # 6
title.find('Flying') # 15
title.find('Zirquss') # -1
subject = '$$$ Get rich now!!! $$$'
subject.find('$$$') # 0
subject.find('$$$', 1) # 只指定了起点 20
subject.find('!!!') # 16
subject.find('!!!', 0, 16) # -1 同时指定了起点和终点
  # 起点值和终点值，包含起点，但不包含终点

# format
# format_map
# index

# 判断字符串是否满足特定条件
# isalnum
# isalpha
# isdecimal
# isdight
# isidentifier
# islower
# isnumeric
# isprintable
# isspace
# istitle
# isupper


# join 合并序列的元素
seq = [1, 2, 3, 4, 5]
sep = '+'
sep.join(seq) # 错误，不能合并整形列表
seq = ['1', '2', '3', '4', '5']
sep.join(seq) # '1+2+3+4+5' 合并一个字符串列表
dirs = '', 'usr', 'bin', 'env'
'/'.join(dirs) # '/usr/bin/env'
print('C:' + '\\'.join(dirs)) # C:\usr\bin\env双斜杠是转义字符




# ljust
# lower 返回字符串的小写版本
'Trondheim Hammer Dance'.lower()
  # 'trondheim hammer dance'


# lstrip
# str.maketrans
# partition
# replace 将指定字符串替换为另一个字符串，并返回结果
'This is a test'.replace('is', 'eez')
  # 'Theez eez a test'

# rfind
# rindex
# rjust
# rpartition
# rstrip
# rsplit
# split 将字符拆分成序列，作用与join相反
# 如果没有指定分隔符，默认在单个或多个空白字符处进行拆分
'1+2+3+4+5'.split('+') #['1', '2', '3', '4', '5']
'/usr/bin/env'.split('/') #['','usr','bin','env']
'Using the default'.split() #['Using','the','default']

# splitlines
# startswith
# strip 将开头和末尾的空白删除，并返回删除后的结果
'   internal whitespace is kept   '.strip() 
  #'internal whitespace is kept'
'*** SPAM * for * everyone!!! ***'.strip(' *!')
  #'SPAM * for * everyone'指定删除的字符，开头和结尾

# swapcase
# title 词首大写，另一种方法是String函数中的capwords
"that's all folks".title() # "That'S All, Folks"

# translate 单字符替换，replace是多字符替换，效率更高
# 转换之前需要转换表
table = str.maketrans('cs', 'kz')
  # Unicode码点之间的映射，c变成k，s变成z
'this is an incredible test'.translate(table)
  #'thiz iz an inkredible tezt'
table = str.maketrans('cs', 'kz', ' ') #将指定字母删除
'this is an incredible test'.translate(table)
  #'thizizaninkredibletezt'

# upper
# zfill
```



```python
# 如果想像修改列表那样修改字符串，可使用list()
list('Hello') # ['H','e','l','l','o']
# 如果像将字符列表转换为字符串
''.join(somelist)
```





### List 列表

列表可以修改，而元组不可以

索引 切片 步长 相加 相乘 成员资格 方法见**容器**和**序列**

```python
# 修改元素的值
x = [1,1,1]
x[1] = 2 # [1,2,1]

# 删除元素，del语句还可以删除字典和变量
names = ['Alice','Beth','Cecil','Dee-Dee','Earl']
del names[2] # ['Alice','Beth','Dee-Dee','Earl']

# 给切片赋值
name = list('Prel') # 覆盖切片
name[2:] = list('ar') # ['P','e','a','r']
name = list('Prel') # 长度不同的序列
name[1:] =list('ython')#['P','y','t','h','o','n']
numbers = [1,5]
numbers[1,5] = [2,3,4] #[1,2,3,4,5] 相当于插入新元素
numbers[1:4] = [] # [1,5] 相当于删除元素
del numbers[1:4] # 与上一句等效
```



```python
# append直接修改旧列表，不会返回修改后的新列表
lst = [1,2,3]
lst.append(4) # [1,2,3,4] 末尾添加对象

# clear就地清空列表内容
lst = [1,2,3]
lst.clear() # [] 类似于lst[:] =[]

# copy复制列表
a = [1,2,3]
b = a # 直接复制只是关联另一个名称到列表
b[1] = 4 # [1,4,3]
a = [1,2,3]
b = a.copy() # 复制a的副本

# count计算指定元素在列表中出现了多少次
['to','be','or','not','to','be'].count('to') # 2
x = [[1, 2], 1, 1, [2, 1, [1, 2]]]
x.count(1) # 2
x.count([1, 2]) # 1

# extend让多个值附加到列表末尾
a = [1,2,3]
b = [4,5,6]
a.extend(b) # [1,2,3,4,5,6] 这里的a列表被修改了
a + b # [1,2,3,4,5,6] 拼接 这里的列表没有被修改
a = a + b # 这个能起到相同效果，但是效率比extend低
a[len(a):] = b # 切片赋值 这个也可行，但是可读性低

# index查找指定值第一次出现的索引
k=['We','are','the','knights','who','say','ni'] 
k.index('who') # 4
k[4] # 'who'

# insert 将一个对象插入列表
numbers = [1,2,3,5,6,7]
numbers.insert(3,'four')#[1,2,3,'four',5,6,7]
numbers[3:3] = ['four'] # 同上,可读性差
numbers[3:3]='four'#[1,2,3,'f','o','u','r',4,5,6]

# pop 从末尾删除一个元素，这是唯一既修改列表又返回一个非None值的列表方法
# 使用pop与append可以实现栈(stack)(后进先出LIFO)
# 如果想创建(先进先出FIFO)可以使用insert(0,...)代替append，或者使用pop(0)代替pop()
x = [1, 2, 3]
x.pop() # 3
x # [1, 2]
x.pop(0) # 1
x # [2]

# remove 删除第一个指定元素，remove是就地修改且不返回值的方法之一
x = ['to','be','or','not','to','be']
x.remove('be')
x # ['to','or','not','to','be']

# reverse 按相反的顺序排列列表中的元素，修改列表但不返回任何值
x = [1, 2, 3]
x.reverse() # [3, 2, 1]
# 如果要按相反的顺序迭代序列，可使用函数reversed。这个函数不返回列表，而是返回一个迭代器。你可使用list将返回的对象转换为列表
x = [1, 2, 3]
list(reversed(x)) # [3, 2, 1]

# sort 给列表排序，修改原来的列表，不返回值，不返回副本
x = [4, 6, 2, 1, 7, 9]
x.sort()
x # [1, 2, 4, 6, 7, 9]
# 副本排序
x = [4, 6, 2, 1, 7, 9]
y = x.copy()
y.sort()
# 函数sorted()，返回副本
x = [4, 6, 2, 1, 7, 9]
y = sorted(x)
x # [4, 6, 2, 1, 7, 9]
y # [1, 2, 4, 6, 7, 9]
# 可用于任何可迭代的对象，总是返回一个列表
sorted('Python') # ['P','h','n','o','t','y']
# 可以给sort指定不同的参数，key和reverse

# 数据结构
```













### Tuple 元组

当元组用作字典键的时候，不能用列表代替

列表可以修改，而元组不可以

有些内置函数和方法返回元组

```python
# 将一些值用逗号隔开，就能创建元组
1,2,3 # (1,2,3)
# 但是一般使用括号括起来
(1,2,3) #  (1,2,3)
# 两个括号的空元祖
()
# 一个值的元组，需要一个逗号
42, # (42,)
3 * (40 + 2) # 126
3 * (40 + 2,) # (42,42,42)
# 元素的索引和切片
x = 1,2,3
x[1] # 2
x[0:2] # (1,2)

```



### Dictionary 字典

字典这种数据结构映射 (mapping)，字典可以快速翻到任何一页

字典由键及其相应的值组成，这种键-值对称为项 (item)

键可以是任何不变的类型 如整数、字符串或元组，键必须是独一无二的。

```python
# 字典操作方法
# 字典的创建
phonebook = {'Alice':'2341','Beth':'9102'}
{} # 空字典

# 函数dict
items = [('name','Gumby'),('age',42)]#键值对序列
d = dict(item) # {'age':42,'name':'Gumby'}
d = dict(name='Gumbt',age=42)#关键字参数


# len(d)返回字典d包含的项（键值对数量）
# d[k]返回与键k相关联的值
# d[k]=v 将值v关联到键k
# del d[k] 删除键为k的项
# k in d  检查字典d是否包含键为k的项，查找的是键，不是值
# v in l  value和list 查找的是值，不是索引
# 相比于检查列表是否包含指定的值，检查字典是否包含指定的键的效率更高。数据结构越大，效率差距就越大
```



```python
# 字典方法

# clear 删除所有字典项，就地执行，不返回值
d = {'age'=42,'name'='Gumby'}
d.clear()
d # {}

# copy 返回一个新字典，这个执行的是浅复制
x={'username':'admin','machines':['foo','bar','baz']}
y = x.copy()
y['username'] = 'mlh'
y['machines'].remove('bar')
y #{'username': 'mlh', 'machines': ['foo', 'baz']}
x #{'username': 'admin', 'machines': ['foo', 'baz']}
# 深复制的方法
from copy import deepcopy
d = {'names':['Alfred','Bertrand']}
c = d.copy()
dc = deepcopy(d)
d['name'].append('Clive')
c # {'names':['Alfred','Bertrand','Clive']}
dc # {'names':['Alfred','Bertrand']}

# fromkeys 指定多个键，对应的值是None
{}.fromkeys(['name','age']) # {'age':None,'name':None}
dict.fromkeys(['name','age']) # {'age':None,'name':None}
dict.fromkeys(['name','age'],'(unknown)')
  #{'age':'(unknown)','name':'(unknown)'}

# get 给字典提供了宽松的环境，如果字典里没有这一项，不会引发错误
d = {}
print(d['name']) # 错误
print(d.get('name')) # None
d.get('name','N/A') # 'N/A' 指定值
d['name'] = 'Eric'
d.get('name') # 'Eric' 和普通的字典查找相同

# items 返回一个包含所有字典项的列表，返回一个字典视图，可用于迭代
d={'title':'Python Web Site','url':'http://www.python.org','spam':0}
d.items() # dict_items([('url','http://www.python.org'),('spam',0),('title','Python Web Site')])
it = d.items()
len(it) # 3
('spam',0) in it # True
# 视图不是复制，始终反映底层字典的反应
d['spam'] = 1
('spam',0) in it # False
d['spam'] = 0
('spam',1) in it # True
# 把字典项复制到列表中
list(d.items()) # [('url','http://www.python.org'),('spam',0),('title','Python Web Site')]

# iterkeys
# keys 返回一个字典视图，包含指定字典中的键
d = {'age':42}
d.keys() # dict_keys(['age'])
type(d.keys()) # <class 'dict_keys'> # 字典视图

# pop
d = {'x':1,'y':2}
d.pop('x') # 1
d # {'y':2}

# popitem 随机弹出一个字典项，比上一个函数高效，因为这样无需先获取列表
d={'url':'http://www.python.org','spam':0,'title':'Python Web Site'}
d.popitem() # ('url', 'http://www.python.org')
d # {'spam': 0, 'title': 'Python Web Site'}
# 如果希望方法popitem以可预测的顺序弹出字典项，请参阅模块collections中的OrderedDict类

# setdefault 如果有值则获取，如果没有则添加，默认的值是None
d = {}
d.setdefault('name','N/A') # 'N/A'
d # {'name':'N/A'}
d['name'] = 'Gumby'
d.setdefault('name','N/A') # 'Gumby'
d # {'name':'Gumby'}
# 如果希望有用于整个字典的全局默认值，请参阅模块collections中的defaultdict类

# update 使用一个字典中的项更新另一个字典
# 可以像调用dict函数那样调用update，可向它提供一个映射{k:v}、一个由键-值对组成的序列(k,v)(或其他可迭代对象)或关键字参数k=v
d = {'title': 'Python Web Site','url': 'http://www.python.org','changed': 'Mar 14 22:09:15 MET 2016'}
x = {'title':'Python Language Website'}
d.update(x)
d # {'url':'http://www.python.org','changed':'Mar 14 22:09:15 MET 2016', 'title':'Python Language Website'}

# values 返回一个字典值的字典视图，可能包含重复的值
d = {}
d[1] = 1
d[2] = 2
d[3] = 3
d[4] = 1
d.values() # dict_values([1, 2, 3, 1])
```



### Set 集合





### 数据类型转换

**检测数据类型**

```python
# type可以检测数据类型
type(()) # <type 'tuple'>
a = 5.5
type(a) == type(3.3) # True

#第二种检测数据类型的方法
names = ["aaa","bbb"]
isinstance(name, list) # True
a = "ccc"
isinstance(a, str) # 这里的String类型是str

# type返回的类型有以下几种
# 元组类型是tuple
# 字典视图类型
```





## 运算符

算术，比较，赋值，逻辑，位运算，成员运算符，身份运算符

```python
# 算术运算符
+加法
-减法
*乘法
**幂
/除法
//取整数
%取模
# 例子：取模将向下园整
 10% 3  #  1
 10%-3  # -2
-10% 3  #  2
-10%-3  # -1
 10// 3  #  3
 10//-3  # -3
-10// 3  #  3
-10//-3  # -3

# 比较运算符
==
!=
>
<
>=
<=

# 赋值运算符
=
+=
-=
*=
/=
%=
**=
//=
:=海象运算符（3.8版本新增）
  
# 位运算符
&与
|或
^异或
~取反
<<左移
>>右移

# 逻辑运算符
and与
or或
not非

# 成员运算符
in在指定序列中找到值返回True，否则返回False
not in在指定序列中没有找到值返回True，否则返回False

# 身份运算符
is判断两个标识符是不是引用自同一个对象
is not判断两个标识符是不是引用自不同的对象

# 优先级

```

注意：python中没有自增自减运算符

## 语句

```python
# Python可以在同一行中使用多条语句，语句之间使用分号(;)分割

#!/usr/bin/python3 
import sys; x = 'runoob'; sys.stdout.write(x + '\n')

# 缩进相同的一组语句构成一个代码块，我们称之代码组
# 像if、while、def和class这样的复合语句，首行以关键字开始，以冒号( : )结束，该行之后的一行或多行代码构成代码组。我们将首行及后面的代码组称为一个子句(clause)

```



### 条件语句

```python
# python中用elif代替了else if
if condition_1:
  statement_block_1
elif condition_2:
  statement_block_2
else:
  statement_block_3
  
# 使用冒号:
# 使用缩进来划分语句块
# python没有switch-case语句
```



### 循环语句

```python
while condition:
  statements
# python中没有do while循环

# while else在条件语句为false时执行的语句块
while expr:
  statement
else:
  additional_statement

# for循环可以遍历任何序列的项目，列表或字符串
for variable in sequence:
  statements
else:
  statements

# rang()函数生成数字序列0,1,2,3,4,5...
for i in range(5):
  print(i) # 循环5次，0,1,2,3,4
range(5,9) # 指定区间 5,6,7,8
range(0,10,3) # 指定增量 0,3,6,9
a = ['Google','Baidu','Runoob','Taobao','QQ']
for i in range(len(a)):
  print(i, a[i]) # range()和len()结合使用
  
# break 和 continue
break跳出循环
continue进入下一次迭代

# else字句，在列表穷尽或者条件false时执行，但是遇到break时不执行
```

### pass语句

python pass是空语句，为了保持程序结构的完整性，不做任何事情，一般用做占位语句

### 迭代器与生成器

[以后再看](https://www.runoob.com/python3/python3-iterator-generator.html)





### with as语句

[python with as用法](https://www.cnblogs.com/zhangbao003/p/8926366.html)

[给大家带来一篇python with as的用法](https://www.jianshu.com/p/1a02a5b63c88)

## 函数

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

空行与代码缩进不同，空行并不是Python语法的一部分。书写时不插入空行，Python解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

记住：空行也是程序代码的一部分。

### 函数

### 参数

形参：

实参：

### 返回值



### 内置函数

**换行输出**

```python
# print默认输出是换行的，如果要实现不换行需要在变量末尾加上 end=""：

#!/usr/bin/python3 
x="a"
y="b"
# 换行输出
print( x )
print( y )

print('---------')
# 不换行输出
print( x, end=" " )
print( y, end=" " )
print()

输出为：
a
b
---------
a b
```



**内置函数列表**

```python
# 数学函数
abs(-10) # 绝对值
pow(2,3) # 幂函数，2的3次方 8
round(2/3) # 把小数化为整数，四舍五入

# 类型转换，类型检测
# list,tuple,str,dict根本就不是函数，而是一个类
type() # 类型检测
bool() # 布尔
int() # 整形
float() # 浮点
complex() # 复数
str() # 字符串
list() # 列表
tuple() # 元组
dict() # 字典
set() # 集合

# 长度检测，最大值最小值
sorted() # 排序，可用于任何序列，但总是返回一个列表
reversed() # 反向迭代序列
len() # 长度
max() # 最大值
min() # 最小值

# 输入输出，文件IO
print() # 输出字符串
input("提示信息") # 输入字符串
open() #打开文件


# 其他
all
any
ascii # 创建指定对象的ASCII表示
bin
breakpoint
bytearray
bytes
callable
chr
classmethod
compile
delattr
dir
divmod
enumerate
eval
exec
filter
format
frozenset
getattr
globals
hasattr
hash
help
hex
id
isinstance
issubclass
iter
locals
map
memoryview
next
object
oct
ord
property
range
repr
setattr
slice
staticmethod
sum
super
vars
zip
__import__
```





## 模块

**引入模块**

```python
# 在python中用 import 或者 from...import 来导入相应的模块
# 将整个模块(somemodule)导入
import somemodule

# 从某个模块中导入某个函数
from somemodule import somefunction

# 从某个模块中导入多个函数
from somemodule import firstfunc, secondfunc, thirdfunc

# 将某个模块中的全部函数导入
from somemodule import *
```




```python
# 导入sys模块
import sys
# 导入sys模块的argv,path成员
from sys import argv,path
```







## 作用域





# 面向对象



### 多态

### 封装

### 异常

### 迭代器










# 其他

# python编译并打包器

[python下编译py成pyc和pyo](https://www.cnblogs.com/dkblog/archive/2009/04/16/1980757.html)

```sh
# 编译成二进制文件，但不是可执行文件
# 隐藏了源代码


```



[python如何编译成exe](https://www.py.cn/faq/python/12039.html)

[python编译成exe](https://blog.csdn.net/qq_42231605/article/details/85304273)



```sh
pyinstall -F hello.py # 把脚本文件打包成exe文件，build目录是日志文件和中间流程，dist目录是可执行文件
```

[setuptools官网](https://setuptools.readthedocs.io/en/latest/#)

[setuptools详解](https://www.jianshu.com/p/ea9973091fdf)

```sh
# setuptools
# 创建setup.py 
# 引入from setuptools import setup,find_packages
python setup.py install
```





# 问题

为什么要写这样一句话

```python
if __name__=="__main__":
	pass
```







# 参考书目

《Python基础教程》[挪]海特兰德 著 人民邮电出版社 ISBN 978-7115353528

4.2.3看不懂

[随书源码第二版](https://www.apress.com/cn/book/9781590599822)

[随书源码第三版](https://www.apress.com/cn/book/9781484200292)

[随书源码第三版Github地址](https://github.com/apress/beginning-python-3ed)



# 链接

[Python官网主页](https://www.python.org/) 

[Scrapy | A Fast and Powerful Scraping and Web Crawling Framework](https://scrapy.org/) 

[python -m pip install xxx](http://www.runoob.com/w3cnote/python-pip-install-usage.html) 

[爬虫 - 标签 - python修行路 - 博客园](https://www.cnblogs.com/zhaof/tag/爬虫/default.html?page=2) 

[优秀博客 - 简书](https://www.jianshu.com/p/5d7366ac16ec) 



[Documentation中文文档](https://docs.python.org/zh-cn/3/index.html)

[Tutorial中文入门教程](https://docs.python.org/zh-cn/3/tutorial/index.html)

[Library中文标准库](https://docs.python.org/zh-cn/3/library/index.html)

[Reference中文语言参考](https://docs.python.org/zh-cn/3/reference/index.html)