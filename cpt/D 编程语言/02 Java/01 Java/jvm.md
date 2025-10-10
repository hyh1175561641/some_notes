
梧桐、
黑马程序员Java教程及资料
全套学习路线图下载地址：
https://pan.baidu.com/s/1LxIxcHDO7SYB96SE-GZfuQ 提取码：dor4









# JVM

Java 虚拟机规范,java的实现手册


Java组成结构

Java ClassJava二进制码, ClassLoader类加载器
JVM内存结构: Method Area方法区, Heap堆, JVM Stacks虚拟机栈, PC Register程序计数器, Native Method Stacks本地方法栈
执行引擎: Interpreter解释器, JIT Compiler即时编译器, GC垃圾回收, Native本地方法接口

# 二进制字节码
Java源代码编译成二进制字节码,然后通过程序计数器一步一步执行.变量储存在内存空间中

# 内存管理

Java有内存动态分配和垃圾回收技术,不需要为new配对一个delete/free代码.而C++自己管理内存.

运行时数据区域: 方法区(Method Area),堆(Heap),虚拟机栈(VM Stack),本地方法栈(Native Method Stack),程序计数器(Program Counter Register)

## 程序计数器
程序计数器(Program Counter Register)
当前线程的行号指针
线程独有
分支循环跳转异常处理线程恢复等功能都是依赖计数器完成.


## 虚拟机栈

虚拟机栈(VM Stack): 存储局部变量表,操作数栈,动态连接,方法出口等信息.
生命周期与线程相同.
方法执行完毕,栈帧出栈.
存放了基本数据类型和引用指针类型

栈帧: 每个方法运行时需要的内存.参数,局部变量,返回地址.一个栈由多个栈帧组成

栈空间越大,会使线程数量变得越来越少

## 本地方法栈
本地方法栈(Native Method Stack): 执行本地方法服务使用的栈.


## 堆
堆(Heap): 存放对象实例,被所有线程共享,虚拟机启动时创建.


## 方法区
方法区(Method Area)




# 垃圾回收机制



内存泄漏和溢出等方面的问题.

垃圾回收内存分配

性能监控故障处理

调优案例

类文件结构



# 类文件结构


# JVM字节码