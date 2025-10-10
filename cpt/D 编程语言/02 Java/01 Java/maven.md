
https://ant.apache.org/
https://gradle.org/

# maven


https://maven.apache.org/
https://mvnrepository.com/


常见坐标
commons-beanutils::commons-beanutils::1.9.4



```bash
# maven的安装, 先下载tar.gz, 再解压, 然后添加路径
# linux安装目录默认为/usr/share/maven
# 必须有 JAVA_HOME=JDK安装目录
# PATH+=%JAVA_HOME%\bin;

# M2_HOME/MAVEN_HOME=Maven安装目录
# PATH+=%MAVEN_HOME%\bin;
# 或者直接添加PATH+=soft\mvn\bin 添加mvn的bin目录

mvn -v # 查看maven的版本

```


# 命令行

```bash
# maven的生命周期
# 执行后面的命令，其实把前面的命令也执行了
# 默认生命周期是 编译，测试，打包，安装，发布
清理 编译 测试 报告 打包 安装 部署

# maven对应的功能是一些插件是jar包和类
//执行一个插件之前可能要执行前面的插件
mvn clean # 删除以前生成的数据, 主要是target目录，当你接手了别人的项目时用这个命令
mvn resources # 资源插件, 把src/main/resources目录中的文件拷贝到target/classes目录中
mvn compile # 编译maven项目,把src/main/java目录中的java代码编译为class文件, 并复制到类路径中/target/classes中,同时执行resources
mvn test # 编译src/test/java目录中的源文件, copy -> target/test-classes目录, src/test/resources -> test-classes, 同时执行resource和compile
mvn test-compile # 同时执行resource和compile
mvn package # 打包, 把class文件和配置文件都放到一个压缩文件中, 默认压缩文件是jar, web应用是war类型, 同时执行resource,compile,test,jar
mvn jar # 执行打包的时候使用该插件,生成jar拓展名文件, 放在target目录下
mvn surefire # 测试时用的插件 
mvn install # 把生成的打包文件安装到mvn仓库之中,同时执行resource,compile,test,install
mvn deploy # 发布
mvn clean package # 可以多个命令连用

打包好的jar文件是src/main目录中的所有生成的class和配置文件, 和test无关

其他功能：validate verify site deploy

maven会把src/main/resources目录中的文件，拷贝到target/classes目录下
但是src/main/java目录中，只处理.java文件，不处理其他文件

```


# maven的目录结构

https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html

```java
maven自己的目录结构
bin 可执行命令
boot
conf 配置文件
lib
LICENSE
NOTICE
README.txt

maven项目的目录结构, 约定的目录结构
src和pom.xml是自己创建的, target是生成的
mavenHello/
    src
        main 主程序目录
            java 源代码
                com.example.Main.java
            resources 配置文件, 资源文件
    src/main/webapp页面资源目录
            // 单元测试--方法是测试的最小单位
        test 测试程序代码(开发人员自己写的测试代码)
            java 测试工作 junit单元测试
                com.example.TestMain.java
            resources 测试程序需要的配置文件
    target
        classes 类路径, classpath
            com.example.Main.class 
        generated-sources 生成源
            annotations 注释注解
        maven-status
            maven-compiler-plugin
                compile
                    default-compile
        test-classes
    pom.xml maven的配置文件, 核心文件


仓库的优先顺序,先找本项目的仓库, 再找本地仓库, 再找公司的私服, 最后找中央仓库镜像
maven的仓库在~/.m2/repository
修改默认的仓库的目录/conf/setting.xml文件, <localRopository>标签
修改本项目的仓库位置


```

# POM

https://maven.apache.org/guides/introduction/introduction-to-the-pom.html
https://maven.apache.org/pom.html

POM(project object model) 工程对象模型

```xml

<!-- pom.xml写法 -->
<!---->
<!-- 固定的内容 -->
<?xml version="1.0" encoding="UTF-8"?>
<!-- 命名空间 -->
<!--xsd是约束文件的拓展名,规定了这么多标签和属性怎么用-->
<project xmlns="http://maven.apache.org/POM/4.0.0"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
        http://maven.apache.org/xsd/maven-4.0.0.xsd">
         <!-- POM模型版本 -->
    <modelVersion>4.0.0</modelVersion>

    <!--坐标可以确定互联网上的唯一资源, 简称GAV-->
    <!-- 定义自己这个项目的坐标 -->
    <groupId>org.example</groupId><!--组织名称,倒写的域名-->
    <artifactId>test1</artifactId><!--项目名称-->
    <version>1.0-SNAPSHOT</version><!--版本,主版本.次版本号.小版本号-->
    <!--SNAPSHOP表示不稳定版本 RELEASE表示发布版本-->
    <!--打包类型, 所有代码, 可用的资源文件, 最终压缩成一个文件-->
    <packaging>jar</packaging><!--默认jar,其他war,rar,ear,pom-->


    <!--配置maven属性-->
    <properties>
        <java.version>1.8</java.version>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>



    <dependencies><!-- 所有依赖放这里 -->
    <!-- 使用其他jar包时,需要gav坐标 -->
      <dependency>
        <groupId>org.springframework</groupId>组织名称
        <artifactId>spring-context</artifactId>
        <version>5.0.5.RELEASE</version>
        <scope>provided</scope>
      </dependency>
    </dependencies>
<!-- scope表示依赖的范围，表示这个依赖在哪个范围起作用 -->
<!-- 主程序 测试程序 打包 部署 默认compile全部包括 test只包括测试程序 -->
<!-- provided包括主程序测试程序，项目自己不需要部署jar包，服务器自带了这个jar包 典型servlet和jsp包不需要 -->

  <!-- 设置构建项目相关的内容 -->
  <build>
    <plugins>
      <!-- 设置插件, 开发中经常设置编译插件的版本 -->
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.1</version>
        <configuration>
          <source>1.8</source>
          <target>1.8</target>
        </configuration>
      </plugin>
    </plugins>

    <!--  -->
    <resources>
      <resource><!-- 扫描这个目录下的properties和xml文件 -->
        <directory>src/main/java</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <!--filtering选项false不启用过滤器，properties已经起到过滤器的作用了-->
        <filtering>false</filtering>
      </resource>
      <resource>
        <directory>src/main/resources</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>false</filtering>
      </resource>
    </resources>


  </build>


</project>

```

```xml

<properties>
  <java.version>1.8</java.version>
  <maven.compiler.source>1.8</maven.compiler.source>编译源码的jdk版本
  <maven.compiler.target>1.8</maven.compiler.target>运行代码的jar版本

  <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>项目构建使用的编码
  <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>生成报告的编码

  <!-- 全局变量 -->
  <spring.version>4.3.10.RELEASE</spring.version>定义全局变量
</properties>

  <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-core</artifactId>
      <version>${spring.version}</version>使用全局变量
  </dependency>





```


Maven默认只是把src/main(test)/Resources文件夹中的内容复制到target中，而src/main/java目录下的资源文件不进行复制




# aaa

软件开发中的阶段
需求分析：分析项目的功能和需求
设计阶段：根据分析的结果, 具体怎么实现
开发阶段：实现具体的功能, 编译代码, 自我测试
测试阶段：专业的测试人员, 测试整个项目的功能, 是否符合测试的要求, 出测试报告
项目的打包发布阶段：给用户安装项目, 用户验收


maven的意思是专家内行，是个口语化的词语。
maven是一个项目管理工具，包含
1项目对象模型POM。
2一组标准集合。
3一个项目生命周期Project Lifecycle。
4一个依赖管理系统Dependency Management System。
5和用来运行定义在生命周期阶段phase中插件plugin目标goal的逻辑。
一个普通工程文件，占空间的大多数都是jar文件，而maven工程占用空间很小，jar包都放在maven仓库当中

maven的作用, 构建项目, 管理依赖
jar包的版本, 文档
创建项目, 编译代码, 测试程序, 打包, 部署等等



POM 清理 编译 测试 报告 打包 安装 部署
约定的目录结构
坐标
依赖管理

仓库管理
生命周期
插件和目标
继承
聚合








