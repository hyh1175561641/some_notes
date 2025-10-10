












# GNU工具集

https://www.gnu.org/ GNU
https://www.fsf.org/ 推进自由软件发展的自由软件基金会(Free Software Foundation,FSF)
GNU项目是为了创建自由的类Unix系统, 也因此开发出来很多开源的系统工具, 其中非常著名的就是GCC(GNU Compiler Collection, GNU编译器套件)
在GNU工具集里面, 开发时常见到的如下, 这些工具通常位于/usr/bin/: 
gcc: GNU C 语言编译器
g++: GNU C++ 语言编译器
ld: GNU 链接器, 将目标文件和库文件链接起来, 创建可执行程序和动态链接库
ar: 生成静态库.a, 可以编辑和管理静态链接库
make: 生成器,可以根据makefile文件自动编译链接生成可执行程序或库文件
gdb: 调试器, 用于调试可执行程序
ldd: 查看可执行文件依赖的共享库, 扩展名.so, 也叫动态链接库


```shell
# g++编译过程
# 预处理: 替换宏, 消除注释, 插入头文件 .cpp->.i
g++ -E a.cpp -o a.i
# 编译: 生成汇编文件 .i->.s
g++ -s a.i -o a.s
# 汇编: 生成二进制文件.s->.o binary
g++ -c a.cpp -o a.o
# 链接: 将各个文件进行连接
# 将多个文件同时编译为一个可执行文件, 其本质上就是静态编译
g++ main.cpp a.cpp -o main
# libNAME.a 是静态库文件


```

静态链接: 静态链接库的后缀名为`.a`, 其本质就是将几个编译好的`.o`文件压缩打包而成。编译时把好多文件打包成一个大文件

动态编译: 可执行文件中没有库, 而是引用外部的动态库, 动态库被多个文件引用一般为 .so文件





# MinGW
https://www.mingw-w64.org/
https://sourceforge.net/projects/mingw/

https://zhuanlan.zhihu.com/p/76613134
找这句话Sources:Tarballs for the mingw-w64 sources are hosted on SourceForge.

原本 GNU 工具只在 Linux/Unix 系统里才有, 随着 Windows 系统的广泛使用,  为了在 Windows 系统里可以使用 GNU 工具, 诞生了 MinGW（Minimalist GNU for Windows） 项目, 利用 MinGW 就可以生成 Windows 里面的  exe 程序和 dll 链接库。

 需要注意的是, MinGW 与 Linux/Unix 系统里 GNU 工具集的有些区别: 

- MinGW 里面工具带有扩展名 .exe,  Linux/Unix 系统里工具通常都是没有扩展名的。
- MinGW 里面的生成器文件名为 mingw32-make.exe, Linux/Unix 系统里就叫 make。
- MinGW 在链接时是链接到 *.a 库引用文件, 生成的可执行程序运行时依赖 *.dll, 而 Linux/Unix 系统里链接时和运行时都是使用 *.so 。


另外 MinGW 里也没有 ldd 工具, 因为 Windows 不使用 .so 共享库文件。如果要查看 Windows  里可执行文件的依赖库, 需要使用微软自家的 Dependency Walker 工具。Windows 里面动态库扩展名为 .dll, MinGW  可以通过 dlltool 来生成用于创建和使用动态链接库需要的文件, 如 .def 和 .lib。

MinGW 原本是用于生成 32 位程序的, 随着 64 位系统流行起来,  从 MinGW 分离出来了 MinGW-w64 项目, 该项目同时支持生成 64 位和 32 位程序。Qt 的 MinGW 版本库就是使用 MinGW-w64 项目里面的工具集生成的。

**MSYS**

（Minimal SYStem）

另外提一下, 由于 MinGW 本身主要就是编译链接等工具和头文件、库文件, 并不包含系统管理、文件操作之类的 Shell 环境,  这对希望用类  Unix 命令的开发者来说还是不够用的。 所以 MinGW 官方又推出了 MSYS（Minimal SYStem）, 相当于是一个部署在  Windows 系统里面的小型 Unix 系统环境,  移植了很多 Unix/Linux 命令行工具和配置文件等等, 是对 MinGW 的扩展。

MSYS 对于熟悉 Unix/Linux 系统环境或者要尝试学习 Unix/Linux 系统的人都是一种便利。MSYS 和 MinGW 的安装升级都是通过其官方的 mingw-get 工具实现, 二者是统一下载安装管理的。

对于 MinGW-w64 项目, 它对应的小型系统环境叫 MSYS2（Minimal SYStem 2）, MSYS2 是 MSYS  的衍生版, 不仅支持 64 位系统和 32 位系统, 还有自己的独特的软件包管理工具, 它从 Arch Linux 系统里移植了 pacman  软件管理工具, 所以装了 MSYS2 之后, 可以直接通过 pacman 来下载安装软件, 而且可以自动解决依赖关系、方便系统升级等。装了 MSYS2 之后, 不需要自己去下载 MinGW-w64, 可以直接用 pacman 命令安装编译链接工具和 git 工具等。

MinGW 项目主页（含 MSYS）:  http://www.mingw.org/
MinGW-w64 项目主页:  https://sourceforge.net/projects/mingw-w64/
MSYS2 项目主页:  https://sourceforge.net/projects/msys2/

**CMake**

CMake（Cross platform Make）是一个开源的跨平台自动化构建工具,  可以跨平台地生成各式各样的 makefile 或者 project 文件,  支持利用各种编译工具生成可执行程序或链接库。

CMake 自己不编译程序,  它相当于用自己的构建脚本 CMakeLists.txt, 叫各种编译工具集去生成可执行程序或链接库。

一般用于编译程序的 makefile 文件比较复杂, 自己去编写比较麻烦,  而利用 CMake , 就可以编写相对简单的  CMakeLists.txt , 由 CMake 根据 CMakeLists.txt 自动生成 makefile, 然后就可以用 make  生成可执行程序或链接库。

本教程里面是使用 Qt 官方的 qmake 工具生成 makefile 文件, 没有用 CMake。这里之所以提 CMake, 是因为整个 KDE  桌面环境的茫茫多程序都是用 CMake 脚本构建的, 另外跨平台的程序/库如 Boost C++ Libraries、OpenCV http://c.biancheng.net/opencv/ 、LLVM、Clang 等也都是用 CMake 脚本构建的。以后如果接触到这些东西, 是需要了解 CMake 的。

CMake 项目主页: https://cmake.org/
KDE 项目主页: https://www.kde.org/

## Dynamic Link 和 Static Link

Dynamic Link 即动态链接, Static Link 即静态链接。

**静态链接库**

静态库就是将链接库的代码和自己编写的代码都编译链接到一块, 链接到静态库的程序通常比较大, 但好处是运行时依赖的库文件很少, 因为目标程序自己内部集成了很多库代码。

**动态链接库**

目标程序通常都不是独立个体, 生成程序时都需要链接其他的库, 要用到其他库的代码。对于多个程序同时运行而言, 内存中就可能有同一个库的多个副本, 占用了太多内存而干的活差不多。

 为了优化内存运用效率, 引入了动态链接库（Dynamic Link Library）, 或叫共享库（Shared  Object）。使用动态链接库时, 内存中只需要一份该库文件, 其他程序要使用该库文件时, 只要链接过来就行了。由于动态库文件外置, 链接到动态库的目标程序相对比较小, 因为剥离了大量库代码, 而只需要一些链接指针。

 使用动态库, 也意味着程序需要链接到如 *.dll 或 *.so 文件, 得提前装好动态库文件, 然后目标程序才能正常运行。

**库文件后缀**

Linux/Unix 系统里静态库扩展名一般是 .a, 动态库扩展名一般是 .so 。Windows 系统里 VC 编译器用的静态库扩展名一般是 .lib, 动态库扩展名一般是 .dll 。

MinGW 比较特殊, 是将 GNU 工具集和链接库从 Linux/Unix 系统移植到 Windows 里,  有意思的情况就出现了, MinGW  使用的静态库扩展名为 .a , 而其动态库扩展名则为 .dll,  .a 仅在生成目标程序过程中使用, .dll 则是在目标程序运行时使用。

linux命令: gcc g++ gdb ar nm ld

centos的版本是gcc 4.8.5, raspberry的版本是gcc8.3.0

## Explicit Linking 和 Implicit Linking

Explicit Linking 即显式链接, Implicit Linking 即隐式链接, 这两种都是动态链接库的使用方式。

动态链接库通常都有其导出函数列表,   告知其他可执行程序可以使用它的哪些函数。可执行程序使用这些导出函数有两种方式: 一是在运行时使用主动加载动态库的函数, Linux 里比如用  dlopen 函数打开并加载动态库, Windows 里一般用 LoadLibrary  打开并加载动态库, 只有当程序代码执行到这些函数时, 其参数里的动态库才会被加载, 这就是显式链接。显式链接方式是在运行时加载动态库, 其程序启动时并不检查这些动态库是否存在。

隐式链接是最为常见的, 所有的编译环境默认都是采用隐式链接的方式使用动态库。隐式链接会在链接生成可执行程序时就确立依赖关系, 在该程序启动时, 操作系统自动会检查它依赖的动态库, 并一一加载到该程序的内存空间, 程序员就不需要操心什么时候加载动态库了。比如 VC 编译环境, 链接时使用动态库对应的 .lib 文件（包含动态库的导出函数声明, 但没有实际功能代码）, 在 .exe  程序运行前系统会检查依赖的 .dll, 如果找不到某个动态库就会出现类似下图对话框: 



![找不到动态链接库。错误信息: 没有找到Qt5Cored.dll,因此这个应用程序未能启动。重新安装应用程序可能会修复此问题。] (http://c.biancheng.net/uploads/allimg/190530/1-1Z530100032603.gif)


MinGW 是将动态库的导出函数声明放在了 .a 文件里, 程序运行依赖的动态库也是 .dll 。

请注意, VC 链接器使用的 .lib 文件分两类, 一种是完整的静态库, 体积比较大, 另一种是动态库的导出声明, 体积比较小。MinGW 链接器使用的 .a 文件也是类似的, Qt 官方库都是按照动态库发布的, 静态库只有自己编译才会有。





