
# 异步和多线程
https://zhuanlan.zhihu.com/p/350816301
最近在研究Spring Boot中的异步处理，发现涉及到异步和多线程的很多知识点，就先写几篇关于异步与多线程的文章，带大一起回顾或学习一下相关的知识点。下面开始正文内容：

前言
在本文中，我们通过一些通俗易懂的方式来解释异步编程和多线程编程，然后再介绍一下它们之间的区别。

什么是异步编程
首先来看一下异步模型。在异步模型中，允许同一时间发生（处理）多个事件。程序调用一个耗时较长的功能（方法）时，它并不会阻塞程序的执行流程，程序会继续往下执行。当功能执行完毕时，程序能够获得执行完毕的消息或能够访问到执行的结果（如果有返回值或需要返回值时）。

下面通过一个示例来看一下同步和异步的区别。示例中程序通过网络获取两个文件，并对两个文件进行合并处理：






上述示例，在异步系统当中的解决方案是开启一个额外的线程进行处理。第一个线程获取第一个文件，第二个线程获取第二个文件，第二个线程并不需要等待第一个线程执行完毕再执行。当两个线程都获得到对应的结果之后，再重新同步处理合并结果的操作。

再来看另外一个场景。单线程方法读取OS（操作系统）当中的文件并需要进行数学运算。而在异步系统中，程序发起读取OS中文件的请求，由于读取操作比较耗时，在等待读取文件时，程序会将控制器返回给CPU进行数学运算。

在异步编程中，通常会针对比较耗时的功能提供一个函数，函数的参数中包含一个额外的参数，用于回调。而这个函数往往称作回调函数。当比较耗时的功能执行完毕时，通过回调函数将结果返回。关于回调函数相关的知识可参考文章《两个经典例子让你彻底理解java回调机制》。

什么是多线程编程
多线程是指同时并发或并行执行多个指令（线程）。

在单核处理器上，多线程往往会给人程序是在并行执行的错觉。实际上，处理器是通过调度算法在多线程之间进行切换和调度。或者根据外部输入（中断）和线程的优先级的组合来进行线程的切换。

在多核处理器上，线程才是真正的并行运行。多个处理器同时执行多个线程，以达到更加高效的处理。

一个简单的示例就是：开启两个浏览器窗口同时下载两个文件。每个窗口都使用一个新的线程去下载文件，它们之间并不需要谁等待谁完成，而是并行进行下载。

下图展示了并发执行多线程应用程序的流程：






异步与多线程的区别
通过上面的介绍，我们可以看出多线程都是关于功能的并发执行。而异步编程是关于函数之间的非阻塞执行，我们可以将异步应用于单线程或多线程当中。

因此，多线程只是异步编程的一种实现形式。

比如，你和你的朋友决定一起做一顿午餐。“异步”就是你对朋友说：“你去商店买意大利面，回来的时候告诉我一声，然后一起做午餐。在你买意大利面的同时，我去准备番茄酱和饮料。”

而“线程”是：“你烧水，我加热番茄酱。当水烧开了，告诉我，我把意大利放进去。当番茄酱热了，你可以把奶酪添加进去。当两者都完成了，就可以坐下来一起吃晚餐。”在线程的示例中，我们可以看到“When，Do”的事件顺序，而这些顺序代表着每个人（线程）的指令集集合的顺序。

上述示例可以看出，多线程是与具体的执行者相关的，而异步是与任务相关的。

多线程是程序设计的逻辑层概念，它是进程中并发运行的一段代码，可以实现线程间的切换执行。

异步和同步是相对的，异步就是彼此独立，在等待某事件的过程中继续做自己的事，不需要等待这一事件完成后再工作。

多线程就是实现异步的一个方式。异步是让调用方法的主线程不需要同步等待另一线程的完成，从而可以让主线程干其它的事情。

所以本质上，异步和多线程并不是一个同等关系，异步是最终目的，多线程只是实现异步的一种手段。

如何选择
面对多线程和异步，我们该如何选择呢？其实，通常情况下选择的依据是主要取决于性能。

那么，同步/异步与单线程/多线程之间的所有组合，哪种模型表现更好？

简而言之，对于具有大量I/O操作和不同计算的大规模应用程序，使用异步多线程有利于充分利用计算资源，并且能够照顾到非阻塞函数。这也是所有操作系统所采用的线程模型。

编写异步操作的复杂程度较高，程序主要使用回调方式进行处理，与正常的思维方式有些出入，而且难以调试。而多线程的使用（滥用）会给系统带来上下文切换的额外负担，并且线程间的共享变量可能造成死锁。

因此在实现这两种模式时，往往需要处理资源竞争、死锁、共享资源和回调事件等问题。

小结
在本文中，我们讲解了异步编程和多线程编程的定义，然后是它们之间的区别。而本文中的所有术语和概念均与具体技术实现无关。后面我们会继续讲解多线程与异步相关的其他知识点，比如异步调用与回调等。



# java回调机制
https://mp.weixin.qq.com/s/2-XGeVHn972YNFCyvK137Q

原创 二师兄 程序新视界 2021-02-07 21:50
前言

先让我们通过一个生活中的场景来还原一下回调的场景：你遇到了一个技术难题（比如，1+1等于几？太难了！），于是你去咨询大牛，大牛说现在正在忙，待会儿告诉你结果。

此时，你可能会去刷朋友圈了，等大牛忙完之后，告诉你答案是2。

那么，这个过程中询问问题（调用对方接口），然后问题解决之后再告诉你（对方处理完再调用你，通知结果），这一过程便是回调。

系统调用的分类
应用系统模块之间的调用，通常分为：同步调用，异步调用，回调。

图片
同步调用
同步调用是最基本的调用方式。类A的a()方法调用类B的b()方法，类A的方法需要等到B类的方法执行完成才会继续执行。如果B的方法长时间阻塞，就会导致A类方法无法正常执行下去。

图片
异步调用
如果A调用B，B的执行时间比较长，那么就需要考虑进行异步处理，使得B的执行不影响A。通常在A中新起一个线程用来调用B，然后A中的代码继续执行。

异步通常分两种情况：第一，不需要调用结果，直接调用即可，比如发送消息通知；第二，需要异步调用结果，在Java中可使用Future+Callable实现。

图片
回调
通过上图我们可以看到回到属于一种双向的调用方式。回调的基本上思路是：A调用B，B处理完之后再调用A提供的回调方法（通常为callbakc()）通知结果。

通常回调分为：同步回调和异步回调。网络上大多数的回调案例都是同步回调。

其中同步回调与同步调用类似，代码运行到某一个位置的时候，如果遇到了需要回调的代码，会在这里等待，等待回调结果返回后再继续执行。

而异步回调与异步调用类似，代码执行到需要回调的代码的时候，并不会停下来，而是继续执行，当然可能过一会回调的结果会返回回来。

同步回调实例
下面我们以同步回调为例来讲解回调的Java代码实现。整个过程就模拟上面问答问题的场景。

首先，定义给一个CallBack的接口，将回调的功能进行单独抽离：

public interface CallBack {
    void callback(String string);
}
CallBack接口中提供了一个callback方法，用于回调时调用。

然后定义问问题的人Person：

public class Person implements CallBack {

    private Genius genius;

    public Person(Genius genius) {
        this.genius = genius;
    }

    @Override
    public void callback(String string) {
        System.out.println("收到答案：" + string);
    }

    public void ask() {
        genius.answer(this);
    }

}
由于Person要提供回调方法，因此实现CallBack接口及其方法，方法中主要针对回调结果进行处理。

同时，由于Person要调用Genius对应的方法，因此要持有Genius的引用，这里通过构造方法传入。

定义回答问题的大神Genius类：

public class Genius {

    public void answer(CallBack callBack) {
        System.out.println("在忙其他事...");
        try {
            Thread.sleep(2000);
            System.out.println("忙完其他事，开始计算...");
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("天才计算出答案为：2");
        // 回调告诉你
        callBack.callback("2");
    }
}
这模拟大神正在忙碌，线程睡眠2秒，忙碌完之后，开始帮忙计算答案，获得答案之后，调用CallBack接口的callback方法进行回调，通知结果。

通过Main方法进行测试：

public static void main(String[] args) {
    Genius genius = new Genius();
    Person you = new Person(genius);
    you.ask();
}
执行打印结果如下：

在忙其他事...
忙完其他事，开始计算...
天才计算出答案为：2
收到答案：2
上面的过程，就实现了一个同步回调的功能。当然，从程序设计上来说，可以对Person和Genius进一步抽象化处理，通过接口的形式呈现。

在上述回调机制的代码实现中，最核心的是在调用answer方法时传递了this参数，即调用者自身。

从本质上来说，回调是一种思想，是一种机制，至于具体如何实现，如何通过代码将回调实现得优雅、实现得可扩展性比较高，就需要八仙过海各显神通了。

异步回调实例
上面的实例演示了同步回调，很明显在调用的过受到Genius执行时长的影响，需要等到Genius处理完才能继续执行Person方法中的后续代码。

下面在上述示例上进行改进，Person提供一个支持异步回调的方法：

 public void askASyn() {
    System.out.println("创建新线程请教问题");
    new Thread(() -> genius.answer(this)).start();
    System.out.println("新线程已启动...");
}
在该方法内，新建了一个线程用来处理Genius#answer方法的调用，这样就能够跳过Genius#answer方法的阻塞，直接执行下面的操作（日志打印）。

在main方法中将调用的方法改为askASyn，打印结果如下：

创建新线程请教问题
新线程已启动...
在忙其他事...
忙完其他事，开始计算...
天才计算出答案为：2
收到答案：2
可以看出，直接打印了“新线程已启动...”，后续才打印出Genius#answer方法方法中处理日志和回调时callback方法接收到的信息。

基于Future的半异步
除了上述的同步，异步处理，还有一种介于同步和异步之间的基于Future的半异步处理。

在Java使用nio后无法立即拿到真实的数据，而是先得到一个"future"，可以理解为邮戳或快递单，为了获悉真正的数据我们需要不停的通过快递单号"future"查询快递是否真正寄到。

Futures是一个抽象的概念，它表示一个值，在某一点会变得可用。一个Future要么获得计算完的结果，要么获得计算失败后的异常。

通常什么时候会用到Future呢？一般来说，当执行一个耗时的任务时，使用Future就可以让线程暂时去处理其他的任务，等长任务执行完毕再返回其结果。

经常会使用到Future的场景有：1. 计算密集场景。2. 处理大数据量。3. 远程方法调用等。

Java在java.util.concurrent包中附带了Future接口，它使用Executor异步执行。

例如下面的代码，每传递一个Runnable对象到ExecutorService.submit()方法就会得到一个回调的Future，使用它检测是否执行，这种方法可以是同步等待线处理结果完成。

public class TestFuture {

    public static void main(String[] args) {

        //实现一个Callable接口
        Callable<User> c = () -> {
            //这里是业务逻辑处理

            //让当前线程阻塞1秒看下效果
            Thread.sleep(1000);
            return new User("张三");
        };

        ExecutorService es = Executors.newFixedThreadPool(2);

        // 记得要用submit，执行Callable对象
        Future<User> fn = es.submit(c);
        // 一定要调用这个方法，不然executorService.isTerminated()永远不为true
        es.shutdown();
        // 无限循环等待任务处理完毕  如果已经处理完毕 isDone返回true
        while (!fn.isDone()) {
            try {
                //处理完毕后返回的结果
                User nt = fn.get();
                System.out.println(nt.name);
            } catch (InterruptedException | ExecutionException e) {
                e.printStackTrace();
            }
        }
    }

    static class User {
        private String name;

        private User(String name) {
            this.name = name;
        }
    }
}
此种情况下虽然是创建了新线程来进行处理，但还是需要等待处理的结果。好处是可以将批量的处理，分为几个线程同时进行处理，最后对结果进行合并，达到提升处理效率的目的。

小结
经过这篇文章，想必大家对Java的回调机制已经有所了解，在各类开源框架中，其实也会经常看到回调的使用，活学活用。





# --------------





## java的native方法，谁能简明明确得讲下？
https://www.zhihu.com/question/28001771
(第一个回答)
native方法称为本地方法。在java源程序中以关键字“native”声明，不提供函数体。其实现使用C/C++语言在另外的文件中编写，编写的规则遵循Java本地接口的规范(简称JNI)。简而言就是Java中声明的可调用的使用C/C++实现的方法。
##### IT可乐：（第二个回答）
类似你说的Thread 类中的 private native start0() 方法；
又或者在JDK 源码 Object.class 类中的 getClass() 方法、hashCode()方法、clone() 方法，其中方法签名如下：
public final native Class<?> getClass();
public native int hashCode();
protected native Object clone() throws CloneNotSupportedException;
你敢说你没用过这些方法？如果你用过，那你就是一定用过不是Java语言编写的方法。
答案就是【native】关键词，用此关键词修饰的方法，多数情况就不是用Java实现的。
那么为什么要用 native 来修饰方法，这样做有什么用？

1、JNI：Java Native Interface
在介绍 native 之前，我们先了解什么是 JNI。
一般情况下，我们完全可以使用 Java 语言编写程序，但某些情况下，Java 可能会不满足应用程序的需求，或者是不能更好的满足需求，比如：
①、标准的 Java 类库不支持应用程序平台所需的平台相关功能。
②、我们已经用另一种语言编写了一个类库，如何用Java代码调用？
③、某些运行次数特别多的方法代码，为了加快性能，我们需要用更接近硬件的语言（比如汇编）编写。 　　上面这三种需求，其实说到底就是如何用 Java 代码调用不同语言编写的代码。那么 JNI 应运而生了。

从Java 1.1开始，Java Native Interface (JNI)标准就成为java平台的一部分，它允许Java代码和其他语言写的代码进行交互。JNI一开始是为了本地已编译语言，尤其是C和C++而设计 的，但是它并不妨碍你使用其他语言，只要调用约定受支持就可以了。使用java与本地已编译的代码交互，通常会丧失平台可移植性。但是，有些情况下这样做是可以接受的，甚至是必须的，比如，使用一些旧的库，与硬件、操作系统进行交互，或者为了提高程序的性能。JNI标准至少保证本地代码能工作在任何Java 虚拟机实现下。

　　通过 JNI，我们就可以通过 Java 程序（代码）调用到操作系统相关的技术实现的库函数，从而与其他技术和系统交互，使用其他技术实现的系统的功能；同时其他技术和系统也可以通过 JNI 提供的相应原生接口开调用 Java 应用系统内部实现的功能。
在windows系统上，一般可执行的应用程序都是基于 native 的PE结构，windows上的 JVM 也是基于native结构实现的。Java应用体系都是构建于 JVM 之上。

可能有人会问，Java不是跨平台的吗？如果用 JNI，那么程序不就将失去跨平台的优点?确实是这样的。

JNI 的缺点：
①、程序不再跨平台。要想跨平台，必须在不同的系统环境下重新编译本地语言部分。
②、程序不再是绝对安全的，本地代码的不当使用可能导致整个程序崩溃。一个通用规则是，你应该让本地方法集中在少数几个类当中。这样就降低了JAVA和C之间的耦合性。
目前来讲使用 JNI 的缺点相对于优点还是可以接受的，可能后面随着 Java 的技术发展，我们不在需要 JNI，但是目前 JDK 还是一直提供对 JNI 标准的支持。

3、用C语言编写程序本地方法
上面讲解了什么是 JNI，那么我们接下来就写个例子，如何用 Java 代码调用本地的 C 程序。
官方文档如下：https://docs.oracle.com/javase/8/docs/technotes/guides/jni/spec/jniTOC.html
步骤如下： 　　①、编写带有 native 声明的方法的java类，生成.java文件；(注意这里出现了 native 声明的方法关键字）
②、使用 javac 命令编译所编写的java类，生成.class文件；
③、使用 javah -jni java类名 生成扩展名为 h 的头文件，也即生成.h文件；
④、使用C/C++（或者其他编程想语言）实现本地方法，创建.h文件的实现，也就是创建.cpp文件实现.h文件中的方法；
⑤、将C/C++编写的文件生成动态连接库，生成dll文件；

下面我们通过一个 HelloWorld 程序的调用来完成这几个步骤。
注意：下面所有操作都是在所有操作都是在目录：D:\JNI 下进行的。
一、编写带有 native 声明的方法的java类
public class HelloJNI {
    //native 关键字告诉 JVM 调用的是该方法在外部定义
    private native void helloJNI();
    static{
        System.loadLibrary("helloJNI");//载入本地库
    }
    public static void main(String[] args) {
        HelloJNI jni = new HelloJNI();
        jni.helloJNI();}}
用 native 声明的方法表示告知 JVM 调用，该方法在外部定义，也就是我们会用 C 语言去实现。
System.loadLibrary("helloJNI");加载动态库，参数 helloJNI 是动态库的名字。我们可以这样理解：程序中的方法 helloJNI() 在程序中没有实现，但是我们下面要调用这个方法，怎么办呢？我们就需要对这个方法进行初始化，所以用 static 代码块进行初始化。

这时候如果我们直接运行该程序，会报“A Java Exception has occurred”错误：

二、使用 javac 命令编译所编写的java类，生成.class文件
D:\JNI>javac HelloJNI.java
执行上述命令后，生成 HelloJNI.class 文件：
HelloJNI.class
HelloJNI.java

三、使用 javah -jni java类名 生成扩展名为 h 的头文件
D:\JNI>javah -jni HelloJNI
执行上述命令后，在 D:/JNI 目录下多出了个 HelloJNI.h 文件：
HelloJNI.class
HelloJNI.h
HelloJNI.java

四、使用C语言实现本地方法  如果不想安装visual studio的，我们需要在windows平台安装 gcc。
安装教程如下：http://blog.csdn.net/altland/article/details/63252757
注意安装版本的选择，根据系统是32位还是64位来选择。64位点击下载。
安装完成之后注意配置环境变量，在 cmd 中输入 g++ -v，如果出现如下信息，则安装配置完成：
D:JNI>g++ -v
output一串信息
接着输入如下命令：
gcc -m64  -Wl,--add-stdcall-alias -I"C:\Program Files\Java\jdk1.8.0_152\include" -I"C:\Program Files\Java\jdk1.8.0_152\include\include\win32" -shared -o helloJNI.dll helloJNI.c

-m64表示生成dll库是64位的。后面的路径表示本机安装的JDK路径。生成之后多了一个helloJNI.dll 文件
HelloJNI.c
HelloJNI.class
HelloJNI.dll
HelloJNI.h
HelloJNI.java

最后运行 HelloJNI：输出 Hello JNI! 大功告成。
D:JNI>java HelloJNI
Hello JNI!（输出成功）


4、JNI调用C的流程图
（一张图片）
图片引用自：https://www.cnblogs.com/Qian123/p/5702574.html

5、native关键字
通过上面介绍了那么多JNI的知识，终于到介绍本篇文章的主角——native 关键字了。相信大家看完上面的介绍，应该也是知道什么是 native 了吧。
native 用来修饰方法，用 native 声明的方法表示告知 JVM 调用，该方法在外部定义，我们可以用任何语言去实现它。 简单地讲，一个native Method就是一个 Java 调用非 Java 代码的接口。
native 语法：
①、修饰方法的位置必须在返回类型之前，和其余的方法控制符前后关系不受限制。
②、不能用 abstract 修饰，也没有方法体，也没有左右大括号。
③、返回值可以是任意类型
我们在日常编程中看到native修饰的方法，只需要知道这个方法的作用是什么，至于别的就不用管了，操作系统会给我们实现。

6、小结
好了，这就是Java中对 native 关键词的介绍。
