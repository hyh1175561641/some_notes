

https://github.com/jiangxincode/cnblogs 学习路线


https://www.oracle.com/java/technologies/persistence-jsp.html JPA

# Java第三方包

Freemark,Thymeleaf Servlet Filter Listener Session Cookie EL表达式 JSTL JavBean


Lucene ZooKeeper 深入理解Java虚拟机 JUC并发编程全套教程 Kubernetes

netty
zookeeper


hive spark flink hbase flume scala

https://arthas.aliyun.com Java 应用诊断利器

HTMLXML Jsoup StaX
Web框架  GoogleWebToolkit Strips Tapestry

自然语言处理 OpenNLP StanfordParser
静态分析 EclipseJDT WALA
数据库 EclipseLink,JPA,JDO,JOOQ

运维部署
https://www.jenkins.io/ Jenkins

代码生成器
https://mapstruct.org/ 代码产生器
https://github.com/mapstruct/mapstruct






https://github.com/google/guava Google guava 谷歌集合库性能好
https://mvnrepository.com/artifact/com.google.guava/guava/33.3.1-jre

https://www.joda.org/joda-time/ Joda-Time 日期系统
https://mvnrepository.com/artifact/joda-time/joda-time/2.13.0

https://commons.apache.org/proper/commons-math/ Apache Commons Math 数学库
https://mvnrepository.com/artifact/org.apache.commons/commons-math/2.2
https://mvnrepository.com/artifact/org.apache.commons/commons-math3/3.6.1

https://sourceforge.net/projects/jts-topo-suite/ 数学库
https://mvnrepository.com/artifact/com.vividsolutions/jts/1.13
https://mvnrepository.com/artifact/com.vividsolutions/jts-core/1.14.0
https://mvnrepository.com/artifact/org.locationtech.jts/jts-core/1.20.0


持久层框架

Web框架
https://struts.apache.org/ Struts2 web框架
https://mvnrepository.com/artifact/org.apache.struts/struts2-core/6.6.1
Jetty servlet容器

Retrofit http客户端
httpclient 测试线上服务
Wiremock 模拟服务的测试框架

图表
http://www.jfree.org/jfreechart/
https://mvnrepository.com/artifact/org.jfree/jfreechart/1.5.5

https://community.jaspersoft.com/download-jaspersoft/community-edition/
https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports/7.0.1

http://www.jgrapht.org/
https://sourceforge.net/projects/jgrapht/
https://mvnrepository.com/artifact/org.jgrapht/jgrapht-core/1.5.2

XML解析
http://www.jdom.org/ JDOM
https://mvnrepository.com/artifact/org.jdom/jdom/1.1
https://mvnrepository.com/artifact/org.jdom/jdom2/2.0.6.1
DOM4J
Xerces
Jsoup 解析HTML页面

网络通信
netty 网络通信框架

并发框架
Disruptor 高性能并发框架，生产者消费者模型经常用
https://github.com/quartz-scheduler/quartz quartz调度器

Office类
Apache POI
docx4j
Jacob
Java2word
iText
FreeMarker 模板引擎
JAXB 生成XML或者JSON

假数据
Testcontainers.org 添加随机数据
https://github.com/DiUS/java-faker 假数据
Mock.java



# Java

https://www.oracle.com/java/
https://docs.oracle.com/javase/8/docs/index.html
https://docs.oracle.com/javase/8/docs/api/index.html
https://docs.oracle.com/javase/10/index.html
https://docs.oracle.com/javase/10/docs/api/overview-summary.html
https://docs.oracle.com/javase/tutorial/java/index.html
https://docs.oracle.com/en/java/javase/17/

https://www.oracle.com/java/technologies/javase-jdk8-doc-downloads.html





JavaEE: Java语言在企业级开发中使用的技术规范的总和, 一共规定了13项大的规范


http://java-decompiler.github.io/ JAD 反编译

http://www.java1234.com/
https://how2j.cn/
http://www.java1234.com/javaxuexiluxiantu.html
https://blog.csdn.net/Neuf_Soleil/article/details/80962686

https://www.lanqiao.cn/courses/?from_login_page=true
https://www.zuidaima.com/share/1737620634422272.htm
https://blog.csdn.net/sd09044901guic/article/details/79578486
https://github.com/halo-dev/halo
http://java.itheima.com/?jingjia-heima-pinpaici-pc-heimachengxuyuan
https://www.itheima.com/special/pythonzly/?jingjia-heima-pinpaici-pc-heimachengxuyuan




## 基础

### 安装与配置

```shell
# 打开系统级的配置文件profile
sudo vi /etc/profile
# 在文件的末尾添加如下的配置内容
"""/etc/profile
JAVA_HOME=/opt/jdk-14.0.1 # 配置内容
CLASSPATH=.
PATH=$JAVA_HOME/bin:$PATH
export JAVA_HOME CLASSPATH PATH
"""
#使修改的配置生效
source /etc/profile
#查看环境变量的值
echo $JAVA_HOME   
echo $CLASSPATH
echo $PATH

# Windows
JAVA_HOME=C:\Program Files\Java\jdk1.8.0_311
PATH=%JAVA_HOME%\bin
CLASSPATH=.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar
```

### 编译和运行

```sh
# java示例源代码
# hello.java
package org.hello
import java.util.Arrays
public class hello{
	public static void main(string[] args){
    	System.out.println("Hello,Java!")
        System.out.println("args = " + Arrays.deepToString(args))
	}
}

# 这样运行
$ javac hello.java;
$ javac hello.java -encoding utf-8;
$ java hello;
$ ...output...
    
# 当编译两个或多个java文件,执行主类即可,把包名去掉
javac Demo.java Order.java -encoding utf-8
java Demo
# 带包名的文件运行
javac -d . Kqcs.java -encoding utf-8
java demos08.Kqcs
    
# JDK中自带的native2ascii命令,可以将文字转换成Unicode编码形式
# C:\Program Files\Java\jdk1.8.0_311\bin\native2ascii.exe
$ native2ascii
计算机
\u8ba1\u7b97\u673a
System.out.println("\u8ba1\u7b97\u673a");

# Java源码和class
JavaSe类库的源码/jdk/src.zip;
JavaSE类库的字节码/jdk/jre/lib/rt.jar;


```

### 代码的组成

```java
// Java代码由关键字和标识符组成,标识符只有由数字,字母,_,$,象形文字符组成,不能含有其他符号.不能以数字开头,区分大小写,关键字不能做标识符,无长度限制
//标识符除了 数字 字母 下划线 美元符号,组成
//字面值是数据,如10,3.14,"abc",'q',true
//驼峰命名法,helloWorld,第二个单词首字母大写
//类名接口名,HelloWorld,第一个单词的首字母也要大写
//变量名,方法名,第二个单词首字母大写
//常量名,全部大写
//规范的代码根本看不出是谁写的,遵守规范使大家工作都顺利进行
//因为Java采用Unicode编码方式,所以中文韩文日文阿拉伯文的字符也能当作类名变量名函数名等标识符使用
```

### 变量类型

java当中没有无符号类型

```java
1Byte=8Bit; //1字节=8比特
        Byte kb Mb Gb Tb Pb
```

```java
// 字面值的进制
int a=10; // 十进制10
        int a=010; // 八进制8
        int a=0x10; // 十六进制16
```

8个基本数据类型

```java
//数据类型的作用就是指导虚拟机运行程序时给该数据分配多大的内存空间
// 成员变量,写在方法外面的变量,会初始化为默认值
byte 1字节（-128,127） 默认值0
        short 2字节（-32768,32767） 默认值0
        int 4字节(-21亿,21亿)(-2147483648,2147483647)默认值0
        long 8字节(-2^63,2^63-1)默认值0L

        float 4字节(6-7有效位)默认值0.0f
        double 8字节(15个有效位)默认值0.0d
        char 2字节(0,65535)默认值'\u0000'
        boolean 1字节 true/false 默认值fals

//byte short int long float double char boolean

```

```java
byte a=50;//50是int类型的字面值,不能赋值给byte,但是这里可以这样写,字面值范围没有超过类型的取值范围
        byte b=(byte)128;//强制类型转换之后,变成了负数

// long类型的字面值后面加上l/L,一般用大写字母L表示,小写字母l和数字1非常相似,所以避免使用
        long x=30000000000;//错误,字面值超过int类型的最大值
        long x=30000000000L;//加L
        long x=100L;
        int y=x;//编译错误,可能会损失精度
        int y=(int)x;//需要强制类型转换

```

```java
// 数字字面值默认当作int类型来处理

short s=3; //3当作是int类型,赋值时再自动转换为short类型
        long y=2147483648; //错误,变量超过int的最大值,添加2147483648L即可

        byte b=127+1; //编译器报错
        byte b=127;b+=1/b++; // 输出-128
        short b=65535/2;/*32767*/b++;/*-32768*/

//浮点型数据类型
        double d=4.0; //浮点数据类型,默认被当作double
        float f=3.0f/3.0F;//如果想创建float类型,字面值后面加f/F
//double的精度太低,不适合做财务软件,java.math.bigDecimal是精度类型更高的引用数据类型


//布尔类型
//boolean true false 占用1字节 底层存储false是0,true是1
//经常使用在逻辑运算符和条件控制语句当中
```

```java
//char类型表示字符,占2字节空间,

//一个问题是,如果.java源代码使用utf-8,可是char却使用2字节,那么输入中文的时候,char类型是怎么样工作呢,会不会不够用呢?
//编译Java代码文件时使用javac -encoding uft-8 Hello.java参数
//字符串需要双引号,单个字符型需要单引号
//单引号是字符,双引号是字符串
// 单引号是基本类型,双引号就是引用类型
char c='a';
        char c="a"; // 错误,类型不兼容
        char c='abc'; // 编译错误
// 一个中文占用2字节
        char c="类"; // 中文字符占用2字节

//转义字符
        "斜杠\\ 换行\n 制表符\t 单引号\' 双引号\"   "

//试一试会打印出什么
        for(char i='\u0000';i<'\uffff';i++){
        System.out.print(i);
        if(i%64==0)System.out.println();}

//String
        println("Hello"+" World"+"!"); // 字符串拼接

```

类型转换

```java
// 自动转换遵循保守的转换原则,由小容量向大容量转换
// 强制类型转换,由大容量向小容量转换,有可能损失精度,谨慎使用
// 任意浮点类型都比整数型容量大
// byte < short < int < long < float < double
// char 和short一样大
int a=(int)b+(int)c;
        (string)a; // 错误,int类型不能强制转换为String类型

//byte short char 混合运算时,各自转换成int类型再做运算

        long a=10;
        byte b=(byte)(int)(g/3);//先转换成int,再换成byte
        byte b=(byte)(int)g/3;//错误,g转成byte类型,3还是int类型




```

```java



```

运算符

```java
// 赋值运算符=
// 变量的赋值
int a; //此时变量a还没有分配内存空间,只声明不赋值只有指针没有内存空间更没有值
        a=1;a=100;//当a重新被赋值时,并不是改变内存空间里的值,而是重新指向了一个新的内存地址
        int a,b,c=100;//此时a,b没有赋值,c指向值为100的内存空间
        int a,b,c;//一行上可以同时声明多个变量
        a=b=c=100;//a b c都指向各自的值为100内存空间
        int a=3+4;//赋值运算符先执行右边的表达式,然后赋值给左边

// 基本算术运算符 + - * / % ++ --
// 复合算术运算符 += -= *= /= %=
// 关系运算符 > < >= <= == !=
// 逻辑运算符,如果前一个操作数已经能判断结果了,第二个操作数就不执行了
// && 短路与
// || 短路或
// 位运算符 & | 两个操作数都要执行完毕才能判断
// 条件运算符 is?true:false 三目运算符
        bol=(3>2?true:false);


```

```java
//运算符优先级

!>算术运算符>关系运算符>&&>||
```

### 语句

```java
// 语句是由完整的表达式组成
// 语句由分号结束
// return函数返回
```

选择语句

```java
if(isTrue){}
        if(isTrue){}else{}
        if(i<1){}else if(i<2){}else(i<3){}

//switch
//switch表达式只允许byte,short,int,char,String,枚举六种类型
        switch(r){
        case 1:
        code;break;
        case 2:
        code;break;
        case 3:
        code;break;
default:
        code;break;
        }

        int a=2;//输出2和3
        switch(a){
default: // default可以写在上面但是如果下面有匹配时,仍然优先执行下面
        System.out.println("default");
        case 4:
        System.out.println("1");
        case 2: // 没有break语句将继续向下执行
        System.out.println("2");
        case 3:
        System.out.println("3");
        }

```

```java
//判断a和b交叉的四种情况
boolean a=0;
        boolean b=0;
        if(a){
        if(b){codeaTbT;}else{codeaTbF;}
        }else{
        if(b){codeaFbT;}else{codeaFbF;}
        }mp
// 同效写法
        if(a==1||b==1){codeaTbT;}
        if(a==1||b==0){codeaTbF;}
        if(a==0||b==1){codeaFbT;}
        if(a==0||b==0){codeaFbF;}

// 当判断一段连续的区间时,最好按照顺序写,60分及格,70分合格,80分满意,90分优秀
        if(score<60){不及格}
        if(score>=60&&score<70){及格}
        if(score>=70&&score<80){合格}
        if(score>=80&&score<90){满意}
        if(score>=90){优秀}

        if(score<60){不及格}
        else if(score>=60&&score<70){及格}
        else if(score>=70&&score<80){合格}
        else if(score>=80&&score<90){满意}
        else(score>=90){优秀}


```

循环语句

```java
while(){} // while循环
        do{}while() // 先执行一次在循环
        for(初始化;判断条件;更新变量){} //
        for(;;){}//死循环

        for(int item:items){
        //循环遍历数组
        }

//break直接退出循环,继续执行循环后边的代码
//continue 跳出当次循环,进入下一次循环

```

```java
List<Double> =new ArrayList<>();
        Iterator<Double> i=list.iterator();
        while(i.hasNext()){
        System.out.println(i.next());}



```

### 数组

```java
//a变量存在栈内存当中
//数组的数据是一段连续的空间,存在堆内存当中

int[]a;
        int a[];//方括号一般写到数据类型后面
        int[]a={1,2,3,4};//数组声明
        int[]a=new int[3];//声明时标明大小
        int[]a=new int[];//x错误,声明时,要么标明大小要么初始化值
        a=new int[3]; // 数组赋值
        a=int[]{1,2,3}; // 数组赋值
        a=int[3]{1,2,3}; //错误,实例化时,小括号不能写内容
        a[0]=1;
        a[99]=2;//数组索引不能越界

//二维数组
        int[][]a=new int[5][4];//声明
        int[][]b=new int[5][];//里层数组未声明

        Arrays.sort(arr);//数组升序排序
        Arrays.toString(arr);//数组转化为字符串
        arrays.equals(arr1,arr2);//比较两个数组
        Arrays.copyOf(newarr,3);// 复制一个数组,后面是长度
        Arrays.binarySearch(arr,3);//查找3的索引,数组必须升序排序
        Arrays.fill(arr,999);//用指定值替换数组中的所有元素

        arr=Arrays.copyOf(arr,arr.length+1); // 把原数组容量扩大1



```

修饰符

```java
//final用来修饰常量,常量一般全部大写,多个单词用下划线分割
//常量的值不可以修改
final double PI=3.14;

// static用来修饰静态的值
// static 可以修饰代码块

```

全局变量与局部变量

```java
//全局变量是能够声明在类里面的变量


```

## 类

面向对象的三大特性:封装继承多态

```java
//导入一个类

import java.util.*;

// 创建一个对象
String str=new String("Hello");


//包名规则,当前所属文件夹

```

```java
//声明一个引用类型
String str=new String("Hello");
```

方法

```java
//定义一个方法
//返回值参数,形参实参

//构造方法


//方法重载

```

```java
//枚举
public enum Numbers {ONE, TWO, THREE;}//三个常量
println(Numbers.ONE)//输出ONE
public enum Numbers {
    ONE(10, "one"),
    TWO(20, "two"),
    THREE(30, "three");
    private int code;
    private String message;
    Numbers() {}//构造方法
    Numbers(int code, String message) {
        this.code = code;this.message = message;}
    public int getCode() {return code;}
    public String getMessage() {return message;}
    //获取所有对象
    public static String getMessage(int code) {
        Numbers[] num = Numbers.values();
        for (Numbers n : num){
            if (n.getCode() == code)
                return n.getMessage();}
        return null;}
}
Numbers.ONE;//ONE
Numbers.ONE.getCode()//10
Numbers.ONE.getMessage()//one
Numbers.getMessage(10)//one

```

```java
/*
0530
1,什么是对象?
对象是用来描述客观事物的一个实体.由属性和方法组成.
2,什么是类?
类是具有相同属性和方法的一组对象的集合.
3,类和对象的关系
类是对象的抽象
对象是类的具体

基本数据类型,操作传递的是变量的值,改变一个变量的值不会影响另一个变量的值.
引用数据类型（类,数组和接口）,赋值是把原对象的引用（可理解为内存地址）传递给另一个引用.

4,Java定义类.创建对象.调用属性和方法.
public class 类名{
    //属性
    //方法
}

类名  对象名 = new 类名();
对象名.属性名
对象名.方法名()

5,Java类中的方法
> 方法的语法
> 方法的返回值（有返回值；无返回值void）
> 方法的调用（同类间调用；不同类间调用-创建对象）

0602
一,构造方法
        构造方法:方法名与类名相同,没有返回值的方法；
        用来初始化对象,给对象的属性设定初始值.

        不显式声明构造方法,系统会给一个默认的无参构造方法.
        显式声明了有参构造方法,系统就不会再提供默认的无参构造方法；
        仍需要使用无参构造方法,需自行定义.


        二,方法重载
        方法重载:在同一个类中,方法名相同,参数类型或参数个数不同的一组方法,这种写法叫做方法重载.
        注意:与方法的返回值和访问修饰符无关.


        三,全局变量和局部变量的区别:
        1）定义的位置不同
        局部变量:定义在方法内部
        全局变量:定义在方法外部,直接写在类中
        2）作用域不同
        局部变量:仅限于定义它的方法
        全局变量:在整个类内部都是可见的
        3）初始值不同
        局部变量:无初始值
        全局变量:有默认值
        4）内存中存储的位置不同
        局部变量:栈内存
        全局变量:堆内存
        5）生命周期不同
        局部变量:随着方法的进栈诞生,随着方法的出栈消失
        全局变量:随着对象的创建诞生,随着对象被垃圾回收消失

0604
类的访问权限控制修饰符:
      public:任何地方都可以访问
      默认:同包的类中可以调用；不同包的类中不能调用
类成员（属性/方法）的访问权限控制修饰符:
                  本类     同包类      不同包的其他类     子类
      private:   可访问    不可访问     不可访问         不可访问
      默认:      可访问     可访问      不可访问         同包可以访问/不同包不可以访问
      protected: 可访问    可访问      不可访问          可以访问
      public:    可访问    可访问       可访问           可以访问

0606
一,静态变量
类变量:被static修饰的变量是静态变量,也叫类变量.类变量只有一份儿,所有对象共享.
                 访问:类名.静态变量名.
实例变量:没有被static修饰的变量是实例变量.实例变量每个对象有一份儿.
                 访问:对象.实例变量名.

应用场景:类变量主要应用于多个对象共享数据.


二,静态方法
静态方法:static修饰的方法,叫静态方法.
	   访问:类名.方法名()；
实例方法:没有被static修饰的方法,叫实例方法.
	   访问:对象.方法名()

在静态方法中,只能访问静态变量 和 静态方法（不能访问实例变量 和 实例方法）.
在静态方法中,不能使用this（当前类的对象）和super（父类的对象）.
静态方法必须实现,不能是抽象方法.

在实例方法中可以访问静态变量 和 静态方法.
在实例方法中不能定义静态变量.


三,静态代码块儿
存在多个代码块时,顺序执行
静态代码块在类加载时执行
静态代码块只执行一次

应用场景:静态代码块可用来在内存中一次性初始化一批数据.


四,继承
符合is-a关系的设计使用继承.
继承是实现代码重用的一种方式
Java中只支持单根继承,即一个类只能有一个直接父类.


五,子类可以继承父类什么?不可以继承父类什么?
（1）子类可以继承父类:
继承public和protected修饰的属性和方法,不管子类和父类是否在同一个包里.
继承默认权限修饰符修饰的属性和方法,但子类和父类必须在同一个包里.
（2）子类不可以继承父类:
父类的private成员.
子类与父类不在同包,父类中使用默认访问权限的成员.
父类的构造方法.


0608
一,继承（优化电子宠物）
符合is-a关系的设计使用继承.
继承是实现代码重用的一种方式
Java中只支持单根继承,即一个类只能有一个直接父类.

二,子类可以继承父类什么?不可以继承父类什么?
（1）子类可以继承父类:
继承public和protected修饰的属性和方法,不管子类和父类是否在同一个包里.
继承默认权限修饰符修饰的属性和方法,但子类和父类必须在同一个包里.
（2）子类不可以继承父类:
父类的private成员.
子类与父类不在同包,父类中使用默认访问权限的成员.
父类的构造方法.

三,super
super是在子类中,需要调用父类的成员 或者 构造方法时,使用.
	子类的方法中:        可以访问父类的属性/方法
	子类的构造方法中:可以访问父类的属性/方法/构造方法

super.属性           调用父类的属性
super.方法名()    调用父类的方法
super()                  访问父类的构造方法

四,在继承下的构造方法执行规则
1,子类的构造方法中没有显式调用其他构造方法时,系统默认先调用父类的无参构造方法
2,子类的构造方法中显式调用了父类的带参构造方法,系统不再默认调用父类的无参构造方法

五,重写
1,什么是方法重写?在子类中方法名相同,参数列表相同,返回值与父类相同或者是其子类,访问修饰符不能严于父类
2,什么时候用方法重写?在父子类继承关系中,子类方法有自己的特殊逻辑需求时,可以重写父类的方法.
3,在重写的方法中可以用super访问父类的属性/方法.
4,重写和重载的区别.


问题1:父类的什么方法可以重写?
父类的属性只能被隐藏,不能被覆盖.
父类的构造方法不能被重写.
父类的静态方法不能被重写.
可以重写父类的普通方法.

问题2:父类的所有普通方法都可以被重写吗?
也跟父类方法的访问权限控制修饰符有关


0609
一,Object类中equals方法和toString方法的重写:
Object类是所有类的直接或间接父类.

（1）Object的equals方法默认逻辑:与==一样,比较两个对象的地址是否相等,如果相等则认为是同一个对象
（2）可以根据特殊需求,重写Object类的equals方法（比如Student对象学号和姓名相同,则为同一个对象）
（3）String重写了Object的equals方法,把逻辑改为比较字符串的值是否相等
（4）字符串的比较,不要用==,要用equals方法

（1）Object的toString方法默认逻辑:输出对象的地址
（2）可以根据特殊需求,重写Object类的toString方法
（3）String重写了Object的toString方法,把逻辑改为了输出字符串的值
（4）直接输出对象时,默认会调用toString()方法

二,多态
1,多态:方法中传入同一个引用类型,调用方法时传入不同的实例而执行不同的操作.
      使用父类作为方法的形参,是java中实现和使用多态的主要方式（比如主人带宠物去看病）
      使用父类作为方法的返回值,也是java中实现和使用多态的主要方式

2,抽象方法:
1）抽象方法:（1）没有方法体  （2）用abstract关键字修饰
2）抽象类中可以没有抽象方法,但是有抽象方法的类必须是抽象类
3）父类中的抽象方法必须在子类中实现（如果子类中不实现,那子类必须是抽象类）

3,向上转型:父类引用指向子类对象,自动类型转换
父类 引用变量名 = new 子类()；
子类没有重写父类的方法:调用的是子类继承的方法
子类重写父类的方法:调用的是子类重写的方法
子类特有的方法:无法调用

4,向下转型:父类类型转换为子类类型,强制类型转换
子类 引用变量名 = (子类)父类的引用变量名.
子类特有的方法:可以调用



*/
```

## 包和模块

java包一般是JavaSE javax包一般是JavaEE

```java
//包,能类组织起来,主要原因是确保类名唯一性,不同的包之间毫无关系
//公司因特网的逆序形式作为包名,最大限度避免冲突
//先写package,再写import


//根目录下的 java/pkg1/Sort.java;
package pkg1;

class Sort {
};
javac pkg1/Sort.java // 编译时需要写路径
        java pkg.Sort // 这里可以点路径

```

```java
//导入其他包的类
//类可以使用本包的所有类,使用其他包的公有类需要导入

//使用其他包的类

java.util.Date today=new java.util.Date();
import java.util.*;//导入包的所有类,对编译后的大小没有影响
import java.util.Date;//导入包的特定类
Date today=new Date();

//只能用*导入一个包
import java.*;//错误
import java.*.*;//错误

```

```java
JNI:Java Native Interface
//native方法称为本地方法,在java源程序中用native声明,不提供函数体
//其实现使用C/C++语言在另外的文件中编写,编写的规则遵循Java本地接口的规范（简称JNI）
//简单来说就是Java中声明的可调用的使用C/C++实现的方法
//一般这些方法都是很底层,跟平台结合紧密,或者使用java实现性能很差
```


# 异常

子类不能比父类抛出更多的异常,如果父类没有抛出异常,子类重写方法不能抛更多

# 多线程



```java

// 线程生命周期
// 就绪状态,调用start方法,线程进入等待期,具有抢夺CPU时间片的权力
// 运行状态,当线程抢夺到CPU时间片之后,开始执行run方法
// 时间片用完会再次变成就绪状态
// 阻塞状态,线程执行遇到等待的事件,会放弃当前占用的CPU时间片,阻塞解除后,继续回到就绪状态
// 死亡状态,run结束

// 创建多线程有三种方法,继承Thread,实现Runnable接口,匿名内部类
// 新建一个类,继承Thread,重写run方法,然后new线程类,调用start方法
public class ThreadTest extends Thread {
    @Override
    public void run() {
        System.out.println("线程");}
}
public static void main(String[] args) {
    ThreadTest threadTest = new ThreadTest();
    // 在jvm开启新栈空间,代码完成后,start方法结束,线程启动成功,自动调用run方法
    threadTest.start();
    System.out.println("主进程");
}

//实现Runnable接口,这并不是线程类,只是一个可运行的类
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("线程");}
}
public static void main(String[] args) {
    // 创建一个可运行的对象
    MyRunnable r = new MyRunnable();
    // 将可运行的对象封装成一个线程对象
    Thread t = new Thread(r);
    t.start();
    System.out.println("主线程");
}

// 匿名内部类启动线程
public static void main(String[] args) {
    // 匿名内部类
    Thread t = new Thread(new Runnable() {
        @Override
        public void run() {
            System.out.println("线程");}
    });
    t.start();
    System.out.println("主线程");
}

```

```java

Thread t = new Thread(new MyRunnable());
t.setName("aaa"); // 设置线程的名字
System.out.println(t.getName()); // 获取线程的名字

// 获取当前线程对象
Thread thread = Thread.currentThread();
System.out.println(thread.getName());

//让当前线程进入休眠状态,进入阻塞状态
Thread.sleep(1000); // try{}catch(InterruptedException)

// 唤醒休眠中的线程
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        try {Thread.sleep(1000 * 60 * 60 * 24 * 365); // 睡眠一年
        } catch (InterruptedException e) {e.printStackTrace();}
        System.out.println(Thread.currentThread().getName());}
}
public static void main(String[] args) {
    Thread t = new Thread(new MyRunnable());
    t.start();
    //唤醒休眠的线程,依靠异常机制,使sleep抛出异常
    t.interrupt();
    System.out.println(Thread.currentThread().getName());
}

Thread t = new Thread(new MyRunnable());
t.start();
t.stop(); // 强行终止线程,已过时,不建议使用,会丢失数据,直接杀死线程

//合理的终止线程,可以保存数据
public class MyRunnable implements Runnable {
    boolean run = true;
    @Override
    public void run() {
        if (run) {try {
            Thread.sleep(1000 * 60 * 60 * 24 * 365); // 睡眠一年
          } catch (InterruptedException e) {e.printStackTrace();}
          System.out.println(Thread.currentThread().getName());
        } else {/*保存数据*/return;}}
}
    public static void main(String[] args) {
        MyRunnable r = new MyRunnable();
        Thread t = new Thread();
        t.start();
        r.run = false; // 逻辑终止线程,可以保存数据
        System.out.println(Thread.currentThread().getName());
    }

// 线程调度相关
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        try {
            Thread.sleep(1000 * 60 * 60 * 24 * 365); // 睡眠一年
        } catch (InterruptedException e) {
            e.printStackTrace();}
        System.out.println(Thread.currentThread().getName());}
}
    public static void main(String[] args) {
        Thread t = new Thread(new MyRunnable());
        t.start();
        // 线程优先级最高10,最低1,默认是5
        t.setPriority(6); // 设置线程优先级,不设置的话默认是5
        System.out.println(t.getPriority()); // 返回线程优先级
        // yield()方法的执行会让当前线程从"运行状态"回到"就绪状态",并不是阻塞方法
        Thread.yield(); // 暂停当前正在执行的线程对象,并执行其他线程
        System.out.println(Thread.currentThread().getName());
    }

// 将t线程合并到当前线程中,当前线程受阻塞,t线程执行直到结束,然后继续执行当前线程
t.join();







```





































# 反射

框架: 半成品软件.可以在框架的基础上进行软件开发，简化编码
反射: 将类的各个组成部分封装为其他对象.这就是反射机制

类的三个阶段
Source源代码阶段，字节码文件class文件
Class类对象阶段,加载进了内存
Runtime运行时阶段


```java

Class.forName("全类名");//将字节码文件加载进内存,返回Class对象
类名.class //返回Object 
类名.getClass(); //返回类的名字



```

# 注解
```java
// 注解是用来说明程序的
// 具体功能:
// 官方定义: 使用javadoc生成Java文档
// 官方定义: 编译检查,让编译器能够实现基本的编译检查
// 自定义: 通过代码里的标识的注解对代码进行分析,反射功能

@Override 检测是否继承自父类
@Oeprecated 表示这个方法已废弃
@SuppressWarning 压制警告
@SuppressWarning("all") 消除所有警告信息

格式 public @interface AnnotationName{}

注解本质上就是一个接口,默认继承
public interface MyAnno extends java.lang.annotation.Annotation {}


注解的注解:
@Target 描述注解能够作用的位置
@Retention 描述注解被保留的阶段
@Documented 描述注解是否被抽取到api文档中
@Inherited 描述注解是否被子类继承


```





# Java框架




spring java 书名可能错误 星空java未知书名 Java编程思想 Java核心技术1/2

4.7开头4.7.1导入别的包

动力节点 23-43





