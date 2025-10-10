


https://cplusplus.com/
https://en.cppreference.com/w/
https://learn.microsoft.com/zh-cn/cpp/cpp/?view=msvc-170
https://www.cprogramming.com/
https://www.learncpp.com/
http://www.hal9k.com/cug/
https://www.thefreecountry.com/sourcecode/cpp.shtml
http://www.sunistudio.com/cppfaq/
https://isocpp.org/


https://www.gnu.org/software/make/
https://cmake.org/




https://www.runoob.com/cprogramming/c-standard-library.html C标准库参考手册
https://www.cnblogs.com/zhoug2020/p/5918307.html 值得学习的C语言开源项目
http://www.jyguagua.com/?p=3838 【整理】值得推荐学习的C/C++开源项目






C++ Primer Plus 第六版中文版
9.3
C++ Primer 第五版






# 基础语法





# 函数

# 作用域

变量对程序而言可见的范围被称为作用域(scope)

函数中声明的变量, 作用域在其代码块中
函数外面声明的全局变量, 作用域是其所在的文件



命名空间, 使用多个不同厂商的类库时, 有可能导致名称冲突

```cpp

# include <iostream>
using namespace std; // 使用std命名空间


// 创建命名空间, 两者名称并不冲突, 命名空间可以嵌套, 但不能位于代码块中
namespace Jack{
    double pail; 
}

namespace Jill{
    double pail; 
}





```




# 面向对象




## Class

构造函数



析构函数








继承

```c++
class Base
{};
class Derive:public Base//公有继承
{}；
class Derive2:protected Base //保护继承
{};
class Derive3:private Base//私有继承，默认
{};
class Derive3:Base{}//私有继承
//上面的代码中，Derive，Derive2，Derive3都继承自Base基类
//区别就是继承方式不同
```

```c++
//派生类可以是公共的，私有的，默认私有属性
class Derived: public/private/protected Base{}

Derived::derived(type1 x, type2 y):base(x,y) //initializer list
{}

//基类的指针可以指向派生类,但是只能调用基类方法
Derived d;
Base & b = d;
Base * b = &d;
```



```c++
//Lambda表达式;
[=](){cout << "c++"}();
int one=1;cout << [one](int a = 3){cout<<"C++"<<one<<a; return "std";}();//"C++13std"
```



















13面向对象的目的之一是提供可重用代码；厂商提供了库但是没有源代码，或者不想改源代码；想要继续增加一些方法，不想白手起家，于是有了派生类；不需要访问源代码，只需要类方法的头文件和编译后代码，仍然可以派生出新的类；在不公开实现的情况下分发给他人，允许他们添加新特性。 13.1讲解了派生类如何创建，在基类的上拓展更多的成员；成员初始化列表，快速给变量赋值，用的都是复制函数；派生类有三种publiic/private/protected派生方式。 13.1.4基类指针指向派生类，但是只能访问积累的成员，派生成员无法访问；可以把派生类对象赋值给函数中的基类形参；基类初始化可以使用派生对象；派生对象可以赋值到基类中，其中嵌套在派生类中的基类对象。 13.2派生类有三种publiic/private/protected派生方式。 is-a关系，午餐有水果和香蕉有水果属性是两回事，午餐的数据成员包含水果是属于has-a关系；律师像鲨鱼属于is-like-a关系，可以设计一个吃人类，然后分别派生为鲨鱼和律师两个类；is-implemented-as-a作为什么来实现，数组可以实现栈，可以把数组当作栈类的私有对象成员；电脑和打印机属于uses-a关系，可以使用友元函数处理两个类之间的通信。
13.3
13.4
13.5
13.6
13.7
13.8

构造函数有时在继承时会发生问题，可以把构造函数写在init()函数中,这样可以在创造子类时，避免父类构造不想要的东西。
构造函数之初始化自己这个类的东西。经典案例是cocox







# Library





栈stack
```cpp
template <class T, class Container = deque<T> > class stack;
顶层元素访问，推入元素，弹出元素，查看大小，判断是否为空。
```
队列queue
```cpp
template <class T, class Container = deque<T> > class queue;
访问两端元素，尾部插入，顶端弹出，查看大小，判断是否为空
```
链表list
树Tree
图Graph
堆Heap
散列表Hash


进制表

binary，octal，decimal，hexadecimal

进制表示法，二进制 0010B，八进制056 0o56，十进制79，十六进制0x3E 3EH

```python
def bodx(i):
    print('%#d'%i,end='\t')
    print('{0:b}'.format(i)+'B \b',end='\t')
    print("%#o\t%#x" % (i,i))

i=0
while(i<10):
    bodx(i)
    i+=1;
    bodx(27)
```













