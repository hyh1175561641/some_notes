

Apache log4j 日志打印

Logback 比log4j更新是log4j替代者



http://www.codeceo.com/article/log4j-usage.html
https://www.jianshu.com/p/f2d4a54f9c41
https://www.jianshu.com/p/6d91c352b4e9

# 日志
开发阶段发现程序的问题,排除错误,产品阶段,可以记录系统运行的一些状态信息,程序运行的状态;
System.out.println的局限性:不能在运行时打开或者关闭,不能选择包或者类,在运行的时候打开或者关闭,输出的信息没有分级,只能输出文本信息,不能改变输出位置

# log4j

https://logging.apache.org/log4j/2.x/index.html


https://mvnrepository.com/artifact/log4j/log4j/1.2.17
https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-core/2.23.1
https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-api/2.24.1
https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-log4j2/3.3.3

Log4j是一个由Java编写可靠、灵活的日志框架，是Apache旗下的一个开源项目；在apache网站：jakarta.apache.org/log4j可以免费下载到Log4j最新版本的软件包。现如今，Log4j已经被移植到了C、C++、Python等语言中，服务更多的Developer；
使用Log4j，我们更加方便的记录了日志信息，它不但能控制日志输出的目的地，也能控制日志输出的内容格式；通过定义不同的日志级别，可以更加精确的控制日志的生成过程，从而达到我们应用的需求；这一切，都得益于一个灵活的配置文件，并不需要我们更改代码。

在Log4j中，主要由三个重要组件构成：
Logger：日志对象，负责捕捉日志记录信息；
Logger对象是用来取代System.out或者System.err的日志输出器，负责日志信息的输出；其中，log4j日志框架提供了info、error、debug等API供Developer使用；
与commons-logging相同，log4j也有日志等级的概念；每一个logger对象都会分配一个等级，未被分配等级的logger则继承根logger的级别，进行日志的输出；每个日志对象方法的请求也有一个等级，如果方法请求的等于大于当前logger对象的等级，则该请求会被处理输出，否则该请求被忽略；

log4j的特性:线程安全,log4j是经过优化速度的,log4j是基于一个名为记录器的层次结构,log4j的支持每个记录器多输出追加器(appender),log4j支持国际化,log4j并不限于一组预定义的设备,日志行为可以使用配置文件在运行时设置,log4j设计从一开始就是处理java异常,log4j有多个级别,通过控制这些级别可以实现将某些不想输出的信息过滤掉,日志输出的格式可以通过拓展Layout类容易的改变,日志输出的目标,以及在写入策略可通过实现Appender程序接口改变,log4j会故障停止,然而,尽管它肯定努力确保传递,log4j不保证每个日志语句将被传递到目的地

log4j的主要组成部分:
loggers:负责捕获记录信息
appenders:负责发布日志信息,以不同的首选目的地
layouts:负责格式化不同风格的日志信息

Log4j由三个重要的组件构成：日志信息的优先级，日志信息的输出目的地，日志信息的输出格式。
日志信息的优先级从高到低有ERROR、WARN、INFO、DEBUG，分别用来指定这条日志信息的重要程度
日志信息的输出目的地指定了日志将打印到控制台还是文件中
输出格式则控制了日志信息的显示内容

```xml
<!-- 新建一个Java工程，导入Log4j包，pom文件中对应的配置代码如下 -->
<!--log4jsupport-->
<dependency>
  <groupId>log4j</groupId>
  <artifactId>log4j</artifactId>
  <version>1.2.17</version>
</dependency>
<dependency><!--mybatis乱码加这个DefaultVFS依赖-->
  <groupId>org.jboss</groupId>
  <artifactId>jboss-vfs</artifactId>
  <version>3.2.16.Final</version>
</dependency>
<!-- import org.apache.log4j.Logger; -->
```

```java
public class log4jDemo{
    Logger log = Logger.getLogger(log4jDemo.class);
    private static final Logger logger = LoggerFactory.getLogger(Log4JTest.class);
    @Test
    public void test(){
        log.trace("TraceMessage!");
        log.debug("DebugMessage!");
        log.info("InfoMessage!");
        log.warn("WarnMessage!");
        log.error("ErrorMessage!");
        log.fatal("FatalMessage!");}
}

```

```java
// 在代码中使用Log4j,获取记录器,这个记录器将负责控制日志信息
public static Logger getLogger(Stringname)
// 通过指定的名字获得记录器，如果必要的话，则为这个名字创建一个新的记录器,Name一般取本类的名字，比如：
static Logger logger=Logger.getLogger(ServerWithLog4j.class.getName())
// 读取配置文件

// 当获得了日志记录器之后，第二步将配置Log4j环境，其语法为：
BasicConfigurator.configure()：自动快速地使用缺省Log4j环境。
PropertyConfigurator.configure(StringconfigFilename)：读取使用Java的特性文件编写的配置文件。
DOMConfigurator.configure(Stringfilename)：读取XML形式的配置文件。
// 插入记录信息（格式化日志信息）
// 当上两个必要步骤执行完毕，您就可以轻松地使用不同优先级别的日志记录语句插入到您想记录日志的任何地方，其语法如下：
Logger.debug(Objectmessage);
Logger.info(Objectmessage);
Logger.warn(Objectmessage);
Logger.error(Objectmessage);

//上面这些级别是定义在org.apache.log4j.Level类中。Log4j只建议使用4个级别，优先级从高到低分别是error,warn,info和debug。通过使用日志级别，可以控制应用程序中相应级别日志信息的输出。例如，如果使用b了info级别，则应用程序中所有低于info级别的日志信息(如debug)将不会被打印出来。

```

```bash
# 最后，在classpath下声明配置文件：log4j.properties或者log4j.xml；
# log4j.properties

log4j.rootLogger=INFO,FILE,CONSOLE

log4j.appender.FILE=org.apache.log4j.FileAppender
log4j.appender.FILE.File=e:/log.out
log4j.appender.FILE.ImmediateFlush=true
log4j.appender.FILE.Threshold=DEBUG
log4j.appender.FILE.Append=true
log4j.appender.FILE.layout=org.apache.log4j.PatternLayout
log4j.appender.FILE.layout.conversionPattern=%d{ABSOLUTE}%5p%c{1}:%L-%m%n

log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender
log4j.appender.CONSOLE.Target=System.out
log4j.appender.CONSOLE.ImmediateFlush=true
log4j.appender.CONSOLE.Threshold=DEBUG
log4j.appender.CONSOLE.layout=org.apache.log4j.PatternLayout
log4j.appender.CONSOLE.encoding=UTF-8
log4j.appender.CONSOLE.layout.conversionPattern=%d{ABSOLUTE}%5p%c{1}:%L-%m%n


# %d{ABSOLUTE} %5p %c{1}:%L %m%n
# 12:10:25,016  INFO HelloControllerTest:29 infomessage

# %d-%c-%-4r[%t]%-5p%x-%m%n
# 2022-10-24 12:10:57,933-com.bdqn.firstboot.controller.HelloControllerTest-0   [main]INFO -infomessage

# spring-boot风格的输出字符串 
# 2022-10-24 12:17:05.071  INFO 6124 --- [       Thread-3] o.s.s.concurrent.ThreadPoolTaskExecutor  : Shutting down ExecutorService 'applicationTaskExecutor'

# junit风格的输出字符串
# 12:16:58.571 [main] DEBUG org.springframework.test.context.junit4.SpringJUnit4ClassRunner - SpringJUnit4ClassRunner constructor called with [class com.bdqn.firstboot.controller.HelloControllerTest]

# spring-boot-mvc的字符串
# 2022-10-24 12:09:47.499  INFO 8864 --- [  restartedMain] com.bdqn.firstboot.FirstbootApplication  : Started FirstbootApplication in 4.62 seconds (JVM running for 7.006)


```

```xml
<!-- log4j.xml -->
<!-- 配置文件:log4j中的xml配置文件要优先于properties文件; -->
<?xml version="1.0"encoding="UTF-8"?>
<!DOCTYPE log4j:configurationSYSTEM "log4j.dtd">
<log4j:configuration>

<appender name="CONSOLE" class="org.apache.log4j.ConsoleAppender">
<param name="target" value="System.out"/>
<param name="immediateFlush" value="true"/>
<param name="threshold" value="DEBUG"/>
<param name="append" value="true"/>
<layout class="org.apache.log4j.PatternLayout">
<param name="ConversionPattern" value="%d-%c-%-4r[%t]%-5p%x-%m%n"/>
</layout>
</appender>

<appender name="FILE" class="org.apache.log4j.FileAppender">
<param name="File" value="e:/log.out"/>
<param name="ImmediateFlush" value="true"/>
<param name="Threshold" value="DEBUG"/>
<param name="Append" value="true"/>
<layout class="org.apache.log4j.PatternLayout">
<param name="ConversionPattern" value="%d{ABSOLUTE}%5p%c{1}:%L-%m%n"/>
</layout>
</appender>

<category name="com.jiaboyan" additivity="false">
<level value="error"></level>
<appender-refref="CONSOLE"/>
</category>

<root>
<priority value="info"/>
<appender-refref="CONSOLE"/>
<appender-refref="FILE"/>
</root>

</log4j:configuration>

```


```bash
# resources目录下创建log4j.properties文件
log4j.rootLogger=debug,stdout,D,E

#输出信息到控制抬
log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.Target=System.out
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=[%-5p]%d{yyyy-MM-ddHH:mm:ss,SSS}method:%l%n%m%n

#输出DEBUG级别以上的日志到=/home/duqi/logs/debug.log
log4j.appender.D=org.apache.log4j.DailyRollingFileAppender
log4j.appender.D.File=/home/duqi/logs/debug.log
log4j.appender.D.Append=true
log4j.appender.D.Threshold=DEBUG
log4j.appender.D.layout=org.apache.log4j.PatternLayout
log4j.appender.D.layout.ConversionPattern=%-d{yyyy-MM-ddHH:mm:ss}[%t:%r]-[%p]%m%n

#输出ERROR级别以上的日志到=/home/admin/logs/error.log
log4j.appender.E=org.apache.log4j.DailyRollingFileAppender
log4j.appender.E.File=/home/admin/logs/error.log
log4j.appender.E.Append=true
log4j.appender.E.Threshold=ERROR
log4j.appender.E.layout=org.apache.log4j.PatternLayout
log4j.appender.E.layout.ConversionPattern=%-d{yyyy-MM-ddHH:mm:ss}[%t:%r]-[%p]%m%n

```



# properties 注释说明版

```bash 101713.38

# 配置rootLogger log4j.rootLogger=[level],appenderName,...
# level有七个级别 ALL TRACE DEBUG INFO WARN ERROR FATAL OFF
# log4j在Level类中定义了7个等级(从小到大):
# Level.ALL< Level.DEBUG< Level.INFO< Level.WARN< Level.ERROR< Level.FATAL< Level.OFF
# A:ALL:各级包括自定义级别,打开所有日志
# B:TRACE:指定细粒度比DEBUG更低的信息事件
# C:DEBUG:调试级别,适用于代码调试期间,一般用于细粒度级别上
# D:INFO:表明消息在粗粒度级别上突出强调应用程序，强调应用程序的运行全程,也就是输出一些提示信息适用于代码运行期间
# E:WARN:输出潜在的有可能出错的情形,也就是输出警告信息
# F:ERROR:指出发生的不影响系统继续运行的错误信息
# G:FATAL:指出严重的错误,这些错误将会导致系统终止运行
# H:OFF:为最高级别,用于关闭所有日志信息的输出
# 核心规则:log4j只会输出级别大于或者等于指定级别的信息
# log4j推荐只使用四个级别,优先级从高到低分别是ERROR,WARN,INFO,DEBUG
# appenderName指的是根logger对象的日志信息输出目的地，在此可以指定多个输出目的地，名称自定义
log4j.rootLogger=ALL,CONSOLE,FILE,DRFILE,RFILE

# CONSOLE CONSOLE START
# CONSOLE CONSOLE START
# CONSOLE CONSOLE START
# 配置输出地,名称自定义,与appenderName同名
# CONSOLE=org.apache.log4j.ConsoleAppender(控制台)
# FILE=org.apache.log4j.FileAppender(将日志信息输出到对应的磁盘文件中)
# org.apache.log4j.DailyRollingFileAppender(按照一定的频度滚动产生日志记录文件,默认每天产生一个日志文件)
# org.apache.log4j.RollingFileAppender(文件大小到达指定尺寸的时候产生一个新的文件)
# org.apache.log4j.WriterAppender(将日志信息以流格式发送到指定的位置)
log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender

# 每个appenderName和一个Layout相对应,appende负责把日志信息输出到指定的地点,而Layout则负责把日志信息按照格式化的要求展示出来
# 配置日志信息的格式或者布局layout以及布局的各项属性
# log4j.appender.appenderName.layout=fully.qualified.name.of.appender.class
# log4j.appender.appenderName.layout.option1=value
# 注意:log4j中提供的layout有以下几种:
# org.apache.log4j.HTMLLayout(以HTML表格形式布局)
# org.apache.log4j.PatternLayout(可以灵活的指定布局模式,需要配置layout.ConversionPattern属性)
# org.apache.log4j.SimpleLayout(包含日志信息的级别和信息字符串)
# org.apache.log4j.TTCCLayout(包含日志产生的时间,线程,类别等等信息)
log4j.appender.CONSOLE.layout=org.apache.log4j.PatternLayout
# 搭配layout的PatternLayout属性,自定义输出信息
log4j.appender.CONSOLE.layout.conversionPattern=%d{ABSOLUTE}%5p%c{1}:%L-%m%n
# 输出java文件名称和行号，默认值false,搭配html表格形式布局
log4j.appender.CONSOLE.layout.LocationInfo=true

# rootLogger里配置debug,然后某个文件专门存储error以及更高级别的错误信息,那么就在这个配置这个文件的时候指定Threshold属性为error
# 指定日志输出的最低级别，默认为DEBUG;如果日志请求的级别低于此级别，则不会输出此请求日志信息
# log4j.appender.appenderName.Threshold=error
log4j.appender.CONSOLE.Threshold=ALL

# 默认值是true,意味着所有的消息都会被立即输出,false则是不输出
# log4j.appender.appenderName.ImmediateFlush=true
log4j.appender.CONSOLE.ImmediateFlush=true

# 默认值为System.out,输出到控制台,还可以取值System.err,当做错误信息输出,输出的信息全部为红色
# log4j.appender.appenderName.target=System.out
log4j.appender.CONSOLE.Target=System.out

# 设置日志输出的编码
log4j.appender.CONSOLE.encoding=UTF-8

# conversionPattern使用方法，假设当前java文件名为Test,所在包名为log4j:
# 显示类名格式%c显示当前logger全类名,例如:log4j.Test，输出所属的类目，通常就是所在类的全名
# %c{层数}:最内层的java文件为第一层,例如:%c{1},显示为Test,当层数大于实际存在的最大层数时,显示最大实际存在层数
# %10c:若名字空间长度小于10,则在左边将欠缺的长度用空格补齐,该种情况为默认的右对齐方式
# %-10c:若名字空间长度小于10,则在右边将欠缺的长度用空格补齐,该种情况为默认的左对齐方式
# %.3c:从空间名最右边开始显示指定的长度,超出该长度的部分将被截取
# %10.15c:若空间名长度小于10,则左边将欠缺的长度用空格补齐,若长度超过15,则将多余部分截取
# %-10.15c:若空间名长度小于10,则右边将欠缺的长度用空格补齐,若长度超过15,则将多余部分截取
# 显示时间格式%d显示日志记录时间,默认时间格式为ISO8601定义的日期格式
# %d{yyyy-MM-ddHH:mm:ss,SSS}:按照指定的时间格式显示日期
# %d{ABSOLUTE}:22:15:30,076
# %d{DATE}:12Oct201822:15:30,076
# %d{ISO8601}:2018-07-2022:23:30,076
# 单个选项
# %C:输出日志信息所属的类目,输出日志信息所属的日志对象,也就是getLogger()中的内容
# %F:显示调用logger的源文件名,例如:Test.java
# %l:输出日志事件的发生位置,包括类目名,发生的线程,以及在代码中的行数,是%c.%M(%F:%L)的组合,例如:log4j.log4jTest.main(log4jTest.java:40)
# %L:输出代码中的行号
# %m:显示输出消息
# %M:显示调用logger的方法名
# %n:换行符
# %p:显示该条目的优先级, %10p:字符占用长度向右对齐
# %r:显示从程序启动时到记录该条日志时已经经过的时间,单位毫秒
# %t:显示产生该日志条目的线程名
# %x:按NDC(NestedDiagnosticContext,线程堆栈):顺序输出日志,输出和当前线程相关联的NDC(嵌套诊断环境)，尤其用到像java servlets这样的多客户多线程的应用中
# %X:按MDC(MappedDiagnosticContext,线程映射表)输出日志,通常用于多个客户端连接同一个服务器,方便服务器区分是哪个客户端访问留下来的日志
# %%:显示一个百分号
log4j.appender.CONSOLE.layout.ConversionPattern=%d{ABSOLUTE}%5p%c{1}:%L-%m%n


# 分级过滤器
# LevelRangeFilter(分级过滤器)如果想要实现不同级别的日志分别输出到不同的位置 , 可以在properties配置文件中加入如下语句进行限制 , 例如 :
log4j.appender.appenderName.Threshold=debug
# 将最低输出级别LevelMin和最高输出级别LevelMax都设置为debug,那么就只能输出debug级别的日志信息了
log4j.appender.appenderName.filter.filterName=org.apache.log4j.varia.LevelRangeFilter
log4j.appender.appenderName.filter.filterName.LevelMin=debug
log4j.appender.appenderName.filter.filterName.LevelMax=debug




# CONSOLE CONSOLE STOP
# CONSOLE CONSOLE STOP
# CONSOLE CONSOLE STOP



# FILE FILE START
# FILE FILE START
# FILE FILE START
log4j.appender.FILE=org.apache.log4j.FileAppender

# log4j.appender.appenderName.File=../logs/log.appenderName.txt
# 指定日志输出到指定位置,用的是相对于配置文件根目录的相对路径
log4j.appender.FILE.File=log.log

# 默认值是true,即将消息追加到指定文件中,如果取值为false,则会覆盖之前的日志内容
# log4j.appender.appenderName.File.Append=true
log4j.appender.FILE.Append=true

# 请求的日志消息不会立即输出，存储到缓存当中，当缓存满了后才输出到磁盘文件中，默认为false,此时ImmediateFlush应当设置为false)
log4j.appender.FILE.BufferedIO=true
# 缓存大小,默认为8k
log4j.appender.FILE.BufferSize=8192

log4j.appender.FILE.ImmediateFlush=true
log4j.appender.FILE.Threshold=DEBUG
log4j.appender.FILE.layout=org.apache.log4j.PatternLayout
log4j.appender.FILE.layout.conversionPattern=%d{ABSOLUTE}%5p%c{1}:%L-%m%n

# 后缀可以是KB,MB,GB,当日志文件的大小到达指定大小后,将会自动滚动,即将原来的内容移到fileName.1文件中,用记事本打开该文件即可看到原来的内容,改属性只能在appender=org.apache.log4j.RollingFileAppender时使用
# log4j.appender.appenderName.MaxFileSize=20MB
#log4j.appender.FILE.MaxFileSize=

# 指定可以产生滚动文件的最大数量,与RollingFileAppender和MaxFileSize属性一起使用,当MaxBackupIndex=n的时候,最大日志存在数量为n+1,即log.txt,log.txt.1,...,log.txt.n,当在服务器上运行的时候,如果对日志数量没有限制,那么随之时间的推移,日志文件会越来越多,占用的内存也将越来越多,直到占满整个盘
# log4j.appender.appenderName.MaxBackupIndex=10
#log4j.appender.FILE.MaxBackupIndex=





# FILE FILE STOP
# FILE FILE STOP
# FILE FILE STOP


# DRFILE DRFILE START
# DRFILE DRFILE START
# DRFILE DRFILE START

# 将输出的日志信息，每天产生一个日志文件，与上面FileAppender不同
log4j.appender.DRFILE=org.apache.log4j.DailyRollingFileAppender

# 该属性在log4j.appender.appenderName=org.apache.log4j.DailyRollingFileAppender时使用,DailyRollingFileAppender默认的频度是每天产生一个日志记录文件,可以在DatePattern属性值中指定其他的频度,常用的几个频度如下:
# '.'yyyy-MM:每月产生一个日志记录文件;
# '.'yyyy-ww:每周产生一个日志记录文件;
# '.'yyyy-MM-dd:每天产生一个日志记录文件;
# '.'yyyy-MM-dd-a:每半天产生一个日志记录文件;
# '.'yyyy-MM-dd-HH:每小时产生一个日志记录文件;
# '.'yyyy-MM-dd-HH-mm:每分钟产生一个日志记录文件;
# 注意:该属性指定值之后,将会按照指定的频度来生成日志记录文件,假设指定生成一个名为log.txt的文件,频度指定为每分钟产生一个日志记录文件,当达到指定频度后,会将log.txt文件中记录的之前的日志记录,重新写入一个名为log.txt.yyyy-MM-dd-HH-mm的文件中,而此时log.txt文件中存放的是新生成的日志信息,该过程循环往复;
log4j.appender.DRFILE.DatePattern='.'yyyy-MM-dd


log4j.appender.DRFILE.File=e:/log.out
log4j.appender.DRFILE.ImmediateFlush=true
log4j.appender.DRFILE.Threshold=DEBUG
log4j.appender.DRFILE.Append=true

# DRFILE DRFILE STOP
# DRFILE DRFILE STOP
# DRFILE DRFILE STOP


# RFILE RFILE START
# RFILE RFILE START
# RFILE RFILE START

# 在日志文件达到指定的大小后，再产生新的文件继续记录日志
log4j.appender.RFILE=org.apache.log4j.RollingFileAppender

# 指定日志文件切割大小，默认10MB，单位KB/MB/GB；当日志文件达到指定大小后，将当前日志文件内容剪切到新的日志文件中，新的文件默认以“原文件名+.1”、“原文件名+.2”的形式命名)
log4j.appender.RFILE.MaxFileSize=100KB
# 产生的切割文件最大数量，如果第二个文件超过了指定大小，那么第一个文件将会被删除
log4j.appender.RFILE.MaxBackupIndex=2

log4j.appender.RFILE.Threshold=DEBUG
log4j.appender.RFILE.File=e:/log.log
log4j.appender.RFILE.encoding=UTF-8
log4j.appender.RFILE.Append=false
log4j.appender.RFILE.ImmediateFlush=true
# RFILE RFILE STOP
# RFILE RFILE STOP
# RFILE RFILE STOP











```





# 未处理

原网页 https://www.jianshu.com/p/6d91c352b4e9

Category

配置子logger的输出级别，以及输出目的地：

<categoryname="com.jiaboyan"additivity="false">
<levelvalue="error"></level>
<appender-refref="CONSOLE"/>
</category>
其中，name指的是子loggger的名称，对应的就是我们程序中类的路径；level指定子logger的级别，appender-ref指的是子logger的输出目的地。
而additivity指的是子logger在输出完日志后，是否把输出信息传递给上一层，true为传递，false为不传递；如果传递的话，则会输出两遍相同的日志信息。值得一提的是，如果将日志输出信息传递给上一层，但是程序并不会在去判断上一层的日志输出级别，而是直接进行输出；

1.5性能优化
在我们的应用中，日志操作几乎是每个方法中必备的行为，不管是记录请求的信息，还是辅助问题的定位，日志信息都起着重要的作用，极大的方便了程序开发。

但与之俱来的是，由于频繁的IO和磁盘的读写，应用的性能也随之降低。并且，java的IO是阻塞式，加锁后导致也同样降低性能。因此对于日志的调优，就成了必备功课。

首先，抛开频繁的IO和磁盘读写不谈，就单纯讨论log4j的性能而言，在高并发的情况下，log4j的锁也会导致应用的性能下降，究其原因，还是看以下的代码：

Category类的callAppenders方法：

//日志对象唤起日志输出目的地Appender:进行日志打印
publicvoidcallAppenders(LoggingEventevent){
intwrites=0;
//遍历日志对象集合
for(Categoryc=this;c!=null;c=c.parent){
//Category是Logger的父类，此处的c就是请求的日志对象本身：
synchronized(c){
//此处加锁了：
if(c.aai!=null){
writes+=c.aai.appendLoopOnAppenders(event);
}
if(!c.additive){
break;
}
}
}
if(writes==0){
repository.emitNoAppenderWarning(this);
}
}

通过以上代码，我们可以发现，为了获得对应日志对象的Appender,会在每次获取之前都加上synchronized同步锁。无论多少个线程进行请求，到此处都需要进行获取锁的操作，才可以进行日志的打印。这也就是说，线程越多，并发越大，此处的锁的竞争越激烈，进而导致系统性能的降低。

其次，我们再回过头来看下IO和磁盘读写的问题。在实际的生产环境下，系统所产生的日志信息需要保存在磁盘文件中，以便日后进行系统分析，或者系统问题的查找。

之前，我们说过Java的IO是阻塞式的，下面就来看下实际的代码：

JDK1.7中的sun.nio.cs.StreamEncoder类：

publicvoidwrite(charcbuf[],intoff,intlen)throwsIOException{
synchronized(lock){
ensureOpen();
if((off<0)||(off>cbuf.length)||(len<0)||
((off+len)>cbuf.length)||((off+len)<0)){
thrownewIndexOutOfBoundsException();
}elseif(len==0){
return;
}
implWrite(cbuf,off,len);
}
}

可以看到，在java-IO流最终输出阶段，也同样加了synchronized同步锁。这也就是我们所说的java阻塞式IO。

1.5.1log4j性能测试
在2.3节中，笔者提到了FileAppender，该类主要功能就是将日志信输出到磁盘文件中。其中，有ImmediateFlush、BufferedIO、BufferSize这三个属性尤为值得关注；

当ImmediateFlush=true时候，表示每一条打印日志请求都会被立即输出，也就是立刻同步到磁盘中去。在高并发下，系统性能受到很大的影响，IO和磁盘读写数大大提升。

当ImmediateFlush=false时候，与上面正好相反，表示每一条打印日志请求不会被立即输出，会使用java.io.OutputStreamWriter的缓存，缓存大小为1024字节。

当ImmediateFlush=false、BufferedIO=true、BufferSize=8192时候，表示使用java.io.BufferedWriter缓存，缓存大小为默认8192字节，每一条打印请求不会立即输出，当缓存达到8192字节后才会落盘操作。这样一来，大大减少了IO和磁盘读写操作，提升了系统的性能。

测试代码：

publicclasslog4jDemo{
Loggerlog=Logger.getLogger(log4jDemo.class);

@Test
publicvoidtest()throwsInterruptedException{
for(intx=0;x<20;x++){
longstart=System.currentTimeMillis();
for(inty=0;y<50;y++){
log.info("InfoMessage!");
}
longtime=System.currentTimeMillis()-start;
System.out.println(time);
}
}
}

例子1：当ImmediateFlush=true时

配置文件：
<log4j:configuration>
<appendername="FILE"class="org.apache.log4j.FileAppender">
<paramname="File"value="e:/log.out"/>
<paramname="ImmediateFlush"value="false"/>
<layoutclass="org.apache.log4j.PatternLayout">
<paramname="ConversionPattern"value="%d{ABSOLUTE}%5p%c{1}:%L-%m%n"/>
</layout>
</appender>
<root>
<priorityvalue="info"/>
<appender-refref="FILE"/>
</root>
</log4j:configuration>

例子1测试结果：(单位毫秒)

931631372371374371371383376439376383372416393368368366376376394384373396371380368382373369373379374370381367371379372385381379375398409415392371403406

例子2：当ImmediateFlush=false时

配置文件：
<log4j:configuration>
<appendername="FILE"class="org.apache.log4j.FileAppender">
<paramname="File"value="e:/log.out"/>
<paramname="ImmediateFlush"value="true"/>
<layoutclass="org.apache.log4j.PatternLayout">
<paramname="ConversionPattern"value="%d{ABSOLUTE}%5p%c{1}:%L-%m%n"/>
</layout>
</appender>
<root>
<priorityvalue="info"/>
<appender-refref="FILE"/>
</root>
</log4j:configuration>

例子2测试结果：(单位毫秒)

845693344338353340372373345337332341345352346332336333379359333330356338333341346331341337339329341339339334341328331329328330329336334332332331333330

例子3：当ImmediateFlush=false、BufferedIO=true、BufferSize=8192时

配置文件：
<log4j:configuration>
<appendername="FILE"class="org.apache.log4j.FileAppender">
<paramname="File"value="e:/log.out"/>
<paramname="ImmediateFlush"value="false"/>
<paramname="bufferedIO"value="true"/>
<paramname="bufferSize"value="8192"/>
<layoutclass="org.apache.log4j.PatternLayout">
<paramname="ConversionPattern"value="%d{ABSOLUTE}%5p%c{1}:%L-%m%n"/>
</layout>
</appender>
<root>
<priorityvalue="info"/>
<appender-refref="FILE"/>
</root>
</log4j:configuration>

例子3测试结果：(单位毫秒)

731853356332336334334334334331332344331330332332330331340334329333331335334334332331336335331354334333334354331333334332333331347332333330332330333331

例子4：使用AsyncAppender异步处理

配置文件：
<log4j:configuration>
<appendername="FILE"class="org.apache.log4j.FileAppender">
<paramname="File"value="e:/log.out"/>
<paramname="bufferedIO"value="true"/>
<paramname="bufferSize"value="8192"/>
<layoutclass="org.apache.log4j.PatternLayout">
<paramname="ConversionPattern"value="%d{ABSOLUTE}%5p%c{1}:%L-%m%n"/>
</layout>
</appender>

<appendername="AsyncAppender"class="org.apache.log4j.AsyncAppender">
<appender-refref="FILE"/>
</appender>

<root>
<priorityvalue="info"/>
<appender-refref="AsyncAppender"/>
</root>
</log4j:configuration>

例子4测试结果：(单位毫秒)

29217814617721627821514713610292969793939593949293979394939594961079491939499989695959810295939291107155137110989393

通过以上4个例子，我们可以看出，性能最差的是ImmediateFlush=true的时候，而性能最好的就是开启日志异步AsyncAppender处理的时候；

1.5.2log4j钩子程序
上一小节，我们提到了log4j的缓存，通过测试结果来看，在开启缓存的情况下，log4j的性能得到了大幅度提升。既然缓存的优势这么明显，为什么log4j不默认开启缓存呢？

缓存的存在，有利有弊。利，提升系统响应性能；弊，当系统因为异常而崩溃，又或者jvm被强行关闭，从而导致缓存中的数据丢失，日志不存在，无法及时确定异常原因。我想，这个才是log4j并没有默认开启缓存的原因！

日志的存在，一方面为了记录系统请求的信息；另一方面，帮助develpoer及时发现、排除错误原因。如果连日志的完整性都不能保留，那么日志存在的意义又是什么？所以，log4j并没有将缓存设置为默认开启，只是提供了一个选项；

那么，我们如何使鱼和熊掌可以兼得呢？在log4j提供的api中暂时无法实现此需求，不过jvm向我们提供了一个方法，可以帮助我们实现，这就是jvm关闭钩子程序；

在jvm中注册一个钩子程序，当jvm关闭的时候，会执行系统中已经设置的所有通过方法addShutdownHook添加的钩子，当系统执行完这些钩子后，jvm才会关闭。

那么，在我们的日志中，如何实现钩子程序呢？请看下面的实现：

测试代码：

publicclasslog4jDemo{
Loggerlog=Logger.getLogger(log4jDemo.class);
@Test
publicvoidtest()throwsInterruptedException{
log.info("InfoMessage!");
}
}

配置文件：（没有开启缓存，立即刷入磁盘）

<appendername="FILE"class="org.apache.log4j.FileAppender">
<paramname="File"value="e:/log.out"/>
<paramname="ImmediateFlush"value="true"/>关闭缓存
<layoutclass="org.apache.log4j.PatternLayout">
<paramname="ConversionPattern"value="%d{ABSOLUTE}%5p%c{1}:%L-%m%n"/>
</layout>
</appender>

结果：（程序运行结束后，生成日志文件信息）

image
立刻刷入，日志信息落盘；

接下来，修改配置文件信息，开启缓存,不立刻刷入磁盘；

<appendername="FILE"class="org.apache.log4j.FileAppender">
<paramname="File"value="e:/log.out"/>
<paramname="ImmediateFlush"value="false"/>开启缓存
<layoutclass="org.apache.log4j.PatternLayout">
<paramname="ConversionPattern"value="%d{ABSOLUTE}%5p%c{1}:%L-%m%n"/>
</layout>
</appender>

结果：（程序运行结束后，生成日志文件信息）

image
jvm运行结束，日志信息没有保存到磁盘中来，日志丢失；

最后，我们添加钩子程序，看看结果如何？

创建新的Appender,继承FileAppender，在构造中添加钩子程序代码：
publicclassHookFileAppenderextendsFileAppender{
publicHookFileAppender(){
super();
//添加钩子程序：
Runtime.getRuntime().addShutdownHook(newLog4jHockThread());
}
publicHookFileAppender(Layoutlayout,Stringfilename)throwsIOException{
super(layout,filename);
//添加钩子程序：
Runtime.getRuntime().addShutdownHook(newLog4jHockThread());
}
publicHookFileAppender(Layoutlayout,Stringfilename,booleanappend)throwsIOException{
super(layout,filename,append);
//添加钩子程序：
Runtime.getRuntime().addShutdownHook(newLog4jHockThread());
}
publicHookFileAppender(Layoutlayout,Stringfilename,booleanappend,booleanbufferedIO,
intbufferSize)throwsIOException{
super(layout,filename,append,bufferedIO,bufferSize);
Runtime.getRuntime().addShutdownHook(newLog4jHockThread());
}

classLog4jHockThreadextendsThread{
@Override
publicvoidrun(){
//jvm结束之前，运行flush操作，将日志落盘；
if(qw!=null){
qw.flush();
}
}
}

}

配置文件修改：（新的appender，开启缓存)

<appendername="HOOKFILE"class="com.jiaboyan.logDemo.HookFileAppender">
<paramname="File"value="e:/log.out"/>
<paramname="ImmediateFlush"value="false"/>
<!--<paramname="bufferedIO"value="true"/>-->
<!--<paramname="bufferSize"value="8192"/>-->
<layoutclass="org.apache.log4j.PatternLayout">
<paramname="ConversionPattern"value="%d{ABSOLUTE}%5p%c{1}:%L-%m%n"/>
</layout>
</appender>
<root>
<priorityvalue="info"/>
<appender-refref="HOOKFILE"/>
</root>

结果为：

image
在jvm结束之前，开启了Log4jHockThread线程，将缓存中的日志进行落盘操作，避免了日志的丢失。









# slf4j

http://www.slf4j.org/

https://mvnrepository.com/artifact/org.slf4j/slf4j-api/2.0.16


# logback

https://mvnrepository.com/artifact/ch.qos.logback/logback-classic/1.5.6


# Apache Logging

https://commons.apache.org/proper/commons-logging/
https://mvnrepository.com/artifact/commons-logging/commons-logging/1.2
https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-logging/3.3.3




# Spring中使用Log4J

一般是在web.xml配置文件中配置Log4j监听器和log4j.properties文件，代码如下：

<context-param>
<param-name>log4jConfigLocation</param-name>
<param-value>classpath:/config/log4j.properties</param-value>
</context-param>
<context-param>
<param-name>log4jRefreshInterval</param-name>
<param-value>60000</param-value>
</context-param>
<listener>
<listener-class>org.springframework.web.util.Log4jConfigListener</listener-class>
</listener>
在之前的SpringInAction系列文章中，我都是以JavaConfig文件为例进行总结，则对应的Log4J的配置如下：

//todo
四、实战经验总结
在商业项目中，日志可用于数据化运营，需要记录关键的业务数据；开发过程中必须准确记录业务日志，如果丢失业务数据则是很严重的故障。

日志信息的打印会影响到服务的性能（吞吐量和响应时间），在业务逻辑简单的服务中更加明显。举个例子，我最近负责的一个会话管理的模块，在性能压测的时候发现TPS只能达到250左右，被这个问题困扰了很久。首先找出性能的瓶颈：缓存操作和数据库操作

发现在缓存操作中有一行打印日志的语句使用了JSON库，例如JSON.toJsonString(obj)，这个对象非常复杂，导致一个读取缓存的操作可以达到300ms左右，而实际上应该在10ms左右；
发现数据库操作非常耗时，但是经过分析，在系统稳定后，压力并不是很大时，数据库操作也比较正常；但是一旦并发数增高，则RT迅速增大，通过链路分析工具，查看在系统负载变高的过程中的指标发现CallAppenders()方法占据了将近40%以上的CPU时间，因此我才考虑到需要将日志级别调整为ERROR级别——不打印DEBUG级别的日志，至此，这个问题算是解决了。
本号专注于后端技术、JVM问题排查和优化、Java面试题、个人成长和自我管理等主题，为读者提供一线开发者的工作和成长经验，期待你能在这里有所收获。





# spring boot



```yaml


# log
logging:
  # 配置日志级别
  level: # trace 不写root也能配置
    # 配置日志级别
    root: info
  #具体指定包下面的级别
    level.com.itheima.controller: info


# properties
# 配置日志级别
# logging.level.root=info
# 指定具体包下面的级别
# logging.level.com.example.mybatisspringboot.mapper=info
```

# Apache Commons Logging

https://commons.apache.org/proper/commons-logging/
https://mvnrepository.com/artifact/commons-logging/commons-logging/1.2



















