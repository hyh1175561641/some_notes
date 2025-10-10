https://blog.csdn.net/weixin_44454512/article/details/109877418
http://bbs.magicalcoder.com/
http://www.ibootstrap.cn/




Freemarker为模板引擎开发的代码生成器
自动生成Mapper,service Controller以及jsp文件



目录
FreeMarker
1.主要内容
2.FreeMarker概述
2.1. FreeMarker概念
2.2. FreeMarker特性
2.3. FreeMarker环境搭建
3.FreeMarker 数据类型
3.1. 布尔类型
3.2. 日期类型
3.3. 数值类型
3.4. 字符串类型
上面四种类型总的代码与截图
3.5. sequence 类型
3.6. hash 类型
上面两种一起运行总代码和运行结果
4.FreeMarker 常见指令
4.1.assign 自定义变量指令
4.2.if elseif else 逻辑判断指令
4.3.list 遍历指令
4.4.macro 自定义指令宏
4.5. nested 占位指令
4.6. import 导入指令
4.7. include 包含指令
5.FreeMarker 页面静态化
5.1. 定义模板
5.2. 加载模板
5.3. 生成对应的html文件
6.FreeMarker 运算符
6.1. 算术运算符
6.2. 逻辑运算符
6.3. 比较运算符
6.4. 空值运算符







FreeMarker详细介绍


FreeMarker
1. 主要内容
在这里插入图片描述

2.FreeMarker概述
2.1. FreeMarker概念
FreeMarker 是一款 模板引擎： 即一种基于模板和要改变的数据， 并用来生成输出文本(HTML网页，电子邮件，配置文件，源代码等)的通用工具。 是一个Java类库。


FreeMarker 被设计用来生成 HTML Web 页面，特别是基于 MVC 模式的应用程序，将视图从业务逻辑中抽离处理，业务中不再包括视图的展示，而是将视图交给 FreeMarker 来输出。虽然 FreeMarker 具有一些编程的能力，但通常由 Java 程序准备要显示的数据，由 FreeMarker 生成页面，通过模板显示准备的数据(如下图）。
在这里插入图片描述
FreeMarker不是一个Web应用框架，而适合作为Web应用框架一个组件。
FreeMarker与容器无关，因为它并不知道HTTP或Servlet。FreeMarker同样可以应用于非Web应用程序环境。
FreeMarker更适合作为Model2框架（如Struts）的视图组件，你也可以在模板中使用JSP标记库。

2.2. FreeMarker特性
2.2.1. 通用目标
能够生成各种文本：HTML、XML、RTF、Java 源代码等等
易于嵌入到你的产品中：轻量级；不需要 Servlet 环境
插件式模板载入器：可以从任何源载入模板，如本地文件、数据库等等
你可以按你所需生成文本：保存到本地文件；作为 Email 发送；从 Web 应用程序发送它返回给 Web浏览器
2.2.2. 强大的模板语言
所有常用的指令：include、if/elseif/else、循环结构
在模板中创建和改变变量
几乎在任何地方都可以使用复杂表达式来指定值
命名的宏，可以具有位置参数和嵌套内容
名字空间有助于建立和维护可重用的宏库，或将大工程分成模块，而不必担心名字冲突
输出转换块：在嵌套模板片段生成输出时，转换HTML转义、压缩、语法高亮等等；你可以定义自己的转换。
2.2.3. 通用数据模型
FreeMarker不是直接反射到Java对象，Java对象通过插件式对象封装，以变量方式在模板中显示，你可以使用抽象（接口）方式表示对象（JavaBean、XML文档、SQL查询结果集等等），告诉模板开发者使用方法，使其不受技术细节的打扰。

2.2.4. 为Web准备
在模板语言中内建处理典型Web相关任务（如HTML转义）的结构
能够集成到Model2 Web应用框架中作为JSP的替代
支持JSP标记库
为MVC模式设计：分离可视化设计和应用程序逻辑；分离页面设计员和程序员
2.2.5. 智能的国际化和本地化
字符集智能化（内部使用UNICODE）
数字格式本地化敏感
日期和时间格式本地化敏感
非US字符集可以用作标识（如变量名）
多种不同语言的相同模板
2.2.6. 强大的XML处理能力
<#recurse> 和 <#visit> 指令（2.3版本）用于递归遍历XML树。在模板中清楚和直接的访问XML对象模型。开源论坛 JForum 就是使用了 FreeMarker 做为页面模板。

2.3. FreeMarker环境搭建
2.3.1. 新建 Maven Web项目
在这里插入图片描述
在这里插入图片描述
在这里插入图片描述
在这里插入图片描述

2.3.2. 配置坐标依赖和部署插件
```xml
pom.xml

<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.suntao</groupId>
  <artifactId>freemarker</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>war</packaging>

  <name>freemarker Maven Webapp</name>
  <!-- FIXME change it to the project's website -->
  <url>http://www.example.com</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
  </properties>

  <dependencies>
    <!-- freemarker的坐标依赖 -->
    <dependency>
      <groupId>org.freemarker</groupId>
      <artifactId>freemarker</artifactId>
      <version>2.3.23</version>
    </dependency>

    <!-- servlet-api的坐标依赖 -->
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <version>3.0.1</version>
    </dependency>

    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
  </dependencies>

  <build>
    <finalName>freemarker</finalName>
    <!--
      插件地址：
        Tomcat
          http://tomcat.apache.org/maven-plugin-2.2/
        Jetty
          https://www.eclipse.org/jetty/documentation/current/jetty-mavenplugin.html
     -->
    <plugins>
      <!-- 配置jetty插件 -->
      <plugin>
        <groupId>org.eclipse.jetty</groupId>
        <artifactId>jetty-maven-plugin</artifactId>
        <version>9.2.1.v20140609</version>
      </plugin>
    </plugins>
  </build>
</project>
```
2.3.3. 修改配置文件 web.xml
在项目的webapp/WEB-INF目录下的web.xml文件中，添加freemarker 相关 servlet 配置
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app id="WebApp_ID" version="3.0"
         xmlns="http://java.sun.com/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd">
  <!-- FreeMarker 的Servlet配置 -->
  <servlet>
    <servlet-name>freemarker</servlet-name>
    <servlet-class>freemarker.ext.servlet.FreemarkerServlet</servlet-class>
    <init-param>
      <!-- 模板路径 -->
      <param-name>TemplatePath</param-name>
      <!-- 默认在webapp目录下查找对应的模板文件 -->
      <param-value>/</param-value>
    </init-param>
    <init-param>
      <!-- 模板默认的编码：UTF-8 -->
      <param-name>default_encoding</param-name>
      <param-value>UTF-8</param-value>
    </init-param>
  </servlet>
  <!-- 处理所有以.ftl结尾的文件；ftl是freemarker默认的文件后缀 -->
  <servlet-mapping>
    <servlet-name>freemarker</servlet-name>
    <url-pattern>*.ftl</url-pattern>
  </servlet-mapping>
</web-app>
```

2.3.4. 编写Servlet类
在main目录下新建Java目录，设置为Sources Root，新建包com.suntao.controllter,在包下创建FreeMarker01.java文件
```java
package com.suntao.controllter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet("/f01")
public class FreeMarker01 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //添加数据
        request.setAttribute("msg","Hello FreeMarker!");
        //请求跳转到ft1文件中
        request.getRequestDispatcher("template/f01.ftl").forward(request,response);
    }
}

```

2.3.5. 新建模板文件 ftl
在webapp目录下新建template文件夹，创建f01.ftl文件

```ftl
<#--
    html 注释语法
        浏览器中查看源码可见

-->
<#--
    freemarker 注释语法
        浏览器中查看源码可见（开发中推荐使用）
        1.在freemarker中，html所有标签均适用
        2.js、css均适用，语法一致
-->
<#--接收数据-->
${msg}

```

2.3.6. 启动项目
点击右上角Add Configuration(就是运行三角号左边那个出来这个页面，点击左上角加号，选择Maven
在这里插入图片描述
在这里插入图片描述
点击运行
在这里插入图片描述
运行后
在这里插入图片描述

2.3.7. 访问项目
浏览器地址栏输入：http://localhost:8989/f01
在这里插入图片描述
注：这是由freemarker生成的HTML网页，右键检查可以查看
在这里插入图片描述

3.FreeMarker 数据类型
Freemarker 模板中的数据类型由如下几种：

布尔型：等价于 Java 的 Boolean 类型，不同的是不能直接输出，可转换为字符串输出
日期型：等价于 java 的 Date 类型，不同的是不能直接输出，需要转换成字符串再输出
数值型：等价于 java 中的 int,float,double 等数值类型
有三种显示形式：数值型(默认)、货币型、百分比型
字符型：等价于 java 中的字符串，有很多内置函数
sequence 类型：等价于 java 中的数组，list，set 等集合类型
hash 类型：等价于 java 中的 Map 类型
3.1. 布尔类型
在Servlet中设置布尔类型的数据
// 布尔类型
```java
request.setAttribute("flag", true);
```

获取数据
```ftl
<#--
    数据类型：布尔类型
        在freemarker中布尔类型不能直接输出；如果输出要先转成字符串
        方式一：?c
        方式二：?string 或 ?string("true时的文本","false时的文本")
-->
${flag?c}<br>
${flag?string}<br>
${flag?string("yes","no")}<br>
```

注：
为换行，数据类型结束后会给出总的代码集运行结果

3.2. 日期类型
在Servlet中设置日期类型的数据

```ftl
// 日期类型  new Data()表示获取现在电脑的时间
request.setAttribute("createDate",new Date());
```


获取数据
```ftl
<#--
    数据类型：日期类型
        在freemarker中日期类型不能直接输出；如果输出要先转成日期型或字符串
        1. 年月日 ?date
        2. 时分秒 ?time
        3. 年月日时分秒 ?datetime
        4. 指定格式 ?string("自定义格式")
            y：年 M：月 d：日
            H：时 m：分 s：秒
-->
<#-- 输出日期格式 -->
${createDate?date} <br>
<#-- 输出时间格式 -->
${createDate?time} <br>
<#-- 输出日期时间格式 -->
${createDate?datetime} <br>
<#-- 输出格式化日期格式 -->
${createDate?string("yyyy年MM月dd日 HH:mm:ss")} <br>
```

3.3. 数值类型
在Servlet设置数值型的数据
```java
request.setAttribute("age",18); // 数值型
request.setAttribute("salary",10000); // 数值型
request.setAttribute("avg",0.545); // 浮点型
```
获取数据
```ftl
<#--
    数据类型：数值类型
        在freemarker中数值类型可以直接输出；
        1. 转字符串
            普通字符串 ?c
            货币型字符串 ?string.currency
            百分比型字符串 ?string.percent
        2. 保留浮点型数值指定小数位（#表示一个小数位）
            ?string["0.##"]
-->
<#-- 直接输出数值型 -->
${age} <br>
${salary} <br>
<#-- 将数值转换成字符串输出 -->
${salary?c} <br>
<#-- 将数值转换成货币类型的字符串输出 -->
${salary?string.currency} <br>
<#-- 将数值转换成百分比类型的字符串输出 -->
${avg?string.percent} <br>
<#-- 将浮点型数值保留指定小数位输出 （##表示保留两位小数） -->
${avg?string["0.##"]} <br>
```

3.4. 字符串类型
在Servlet中设置字符串类型的数据
```java
// 字符串类型
request.setAttribute("msg1","Hello ");
request.setAttribute("msg2","freemarker");
```

获取数据
```ftl
<#--
    数据类型：字符串类型
        在freemarker中字符串类型可以直接输出；
        1. 截取字符串（左闭右开） ?substring(start,end)
        2. 首字母小写输出 ?uncap_first
        3. 首字母大写输出 ?cap_first
        4. 字母转小写输出 ?lower_case
        5. 字母转大写输出 ?upper_case
        6. 获取字符串长度 ?length
        7. 是否以指定字符开头（boolean类型） ?starts_with("xx")?string
        8. 是否以指定字符结尾（boolean类型） ?ends_with("xx")?string
        9. 获取指定字符的索引 ?index_of("xx")
        10. 去除字符串前后空格 ?trim
        11. 替换指定字符串 ?replace("xx","xx")
-->
<#-- 直接输出 -->
${msg1} - ${msg2} <br>
${msg1?string} - ${msg2?string} <br>
<#-- 1. 截取字符串（左闭右开） ?substring(start,end) -->
${msg2?substring(1,4)} <br>
<#-- 2. 首字母小写输出 ?uncap_first -->
${msg1?uncap_first} <br>
<#-- 3. 首字母大写输出 ?cap_first -->
${msg2?cap_first} <br>
<#-- 4. 字母转小写输出 ?lower_case -->
${msg1?lower_case} <br>
<#-- 5. 字母转大写输出 ?upper_case -->
${msg1?upper_case} <br>
<#-- 6. 获取字符串长度 ?length -->
${msg1?length} <br>
<#-- 7. 是否以指定字符开头（boolean类型） ?starts_with("xx")?string -->
${msg1?starts_with("H")?string} <br>
<#-- 8. 是否以指定字符结尾（boolean类型） ?ends_with("xx")?string -->
${msg1?ends_with("h")?string} <br>
<#-- 9. 获取指定字符的索引 ?index_of("xxx") -->
${msg1?index_of("e")} <br>
<#-- 10. 去除字符串前后空格 ?trim -->
${msg1?trim?length} <br>
<#-- 11. 替换指定字符串 ?replace("xx","xxx") -->
${msg1?replace("o","a")}<br>

```

字符串空值情况处理
FreeMarker 的变量必须赋值，否则就会抛出异常。而对于 FreeMarker 来说，null 值和不存在的变量是完全一样的，因为 FreeMarker 无法理解 null 值。
FreeMarker 提供两个运算符来避免空值：
① ! ：指定缺失变量的默认值
${value!}：如果value值为空，则默认值是空字符串
${value!“默认值”}：如果value值为空，则默认值是字符串"默认值"
② ?? ：判断变量是否存在
如果变量存在，返回 true，否则返回 false
${(value??)?string}
```ftl
<#-- 如果值不存在，直接输出会报错 -->
<#--${str}-->
<#-- 使用!，当值不存在时，默认显示空字符串 -->
${str!}<br>
<#-- 使用!"xx"，当值不存在时，默认显示指定字符串 -->
${str!"这是一个默认值"}<br>
<#-- 使用??，判断字符串是否为空；返回布尔类型。如果想要输出，需要将布尔类型转换成字符串 -->
${(str??)?string}<br>

```

上面四种类型总的代码与截图
Servlet(FreeMarker01.java)中的代码

```java
package com.suntao.controllter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.Date;

@WebServlet("/f01")
public class FreeMarker01 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //添加数据
        request.setAttribute("msg","Hello FreeMarker!");

        //boolean（布尔）类型
        request.setAttribute("flag",true);

        // 日期类型  new Data()表示获取现在电脑的时间
        request.setAttribute("createDate",new Date());

        // 数值类型
        request.setAttribute("age",18); // 数值型
        request.setAttribute("salary",10000); // 数值型
        request.setAttribute("avg",0.545); // 浮点型

        // 字符串类型
        request.setAttribute("msg1","Hello ");
        request.setAttribute("msg2","freemarker");

        //请求跳转到ft1文件中
        request.getRequestDispatcher("template/f01.ftl").forward(request,response);
    }
}
```




f01中获取数据的代码
```ftl
<#--
    html 注释语法
        浏览器中查看源码可见

-->
<#--
    freemarker 注释语法
        浏览器中查看源码可见（开发中推荐使用）
        1.在freemarker中，html所有标签均适用
        2.js、css均适用，语法一致
-->
<#--接收数据-->
${msg}<br>
<br>
<#--
    数据类型：布尔类型
        在freemarker中布尔类型不能直接输出；如果输出要先转成字符串
        方式一：?c
        方式二：?string 或 ?string("true时的文本","false时的文本")
-->
${flag?c}<br>
${flag?string}<br>
${flag?string("yes","no")}<br>
<br>
<#--
    数据类型：日期类型
        在freemarker中日期类型不能直接输出；如果输出要先转成日期型或字符串
        1. 年月日 ?date
        2. 时分秒 ?time
        3. 年月日时分秒 ?datetime
        4. 指定格式 ?string("自定义格式")
            y：年 M：月 d：日
            H：时 m：分 s：秒
-->
<#-- 输出日期格式 -->
${createDate?date} <br>
<#-- 输出时间格式 -->
${createDate?time} <br>
<#-- 输出日期时间格式 -->
${createDate?datetime} <br>
<#-- 输出格式化日期格式 -->
${createDate?string("yyyy年MM月dd日 HH:mm:ss")} <br>
<br>

<#--
    数据类型：数值类型
        在freemarker中数值类型可以直接输出；
        1. 转字符串
            普通字符串 ?c
            货币型字符串 ?string.currency
            百分比型字符串 ?string.percent
        2. 保留浮点型数值指定小数位（#表示一个小数位）
            ?string["0.##"]
-->
<#-- 直接输出数值型 -->
${age} <br>
${salary} <br>
<#-- 将数值转换成字符串输出 -->
${salary?c} <br>
<#-- 将数值转换成货币类型的字符串输出 -->
${salary?string.currency} <br>
<#-- 将数值转换成百分比类型的字符串输出 -->
${avg?string.percent} <br>
<#-- 将浮点型数值保留指定小数位输出 （##表示保留两位小数） -->
${avg?string["0.##"]} <br>
<br>

<#--
    数据类型：字符串类型
        在freemarker中字符串类型可以直接输出；
        1. 截取字符串（左闭右开） ?substring(start,end)
        2. 首字母小写输出 ?uncap_first
        3. 首字母大写输出 ?cap_first
        4. 字母转小写输出 ?lower_case
        5. 字母转大写输出 ?upper_case
        6. 获取字符串长度 ?length
        7. 是否以指定字符开头（boolean类型） ?starts_with("xx")?string
        8. 是否以指定字符结尾（boolean类型） ?ends_with("xx")?string
        9. 获取指定字符的索引 ?index_of("xx")
        10. 去除字符串前后空格 ?trim
        11. 替换指定字符串 ?replace("xx","xx")
-->
<#-- 直接输出 -->
${msg1} - ${msg2} <br>
${msg1?string} - ${msg2?string} <br>
<#-- 1. 截取字符串（左闭右开） ?substring(start,end) -->
${msg2?substring(1,4)} <br>
<#-- 2. 首字母小写输出 ?uncap_first -->
${msg1?uncap_first} <br>
<#-- 3. 首字母大写输出 ?cap_first -->
${msg2?cap_first} <br>
<#-- 4. 字母转小写输出 ?lower_case -->
${msg1?lower_case} <br>
<#-- 5. 字母转大写输出 ?upper_case -->
${msg1?upper_case} <br>
<#-- 6. 获取字符串长度 ?length -->
${msg1?length} <br>
<#-- 7. 是否以指定字符开头（boolean类型） ?starts_with("xx")?string -->
${msg1?starts_with("H")?string} <br>
<#-- 8. 是否以指定字符结尾（boolean类型） ?ends_with("xx")?string -->
${msg1?ends_with("h")?string} <br>
<#-- 9. 获取指定字符的索引 ?index_of("xxx") -->
${msg1?index_of("e")} <br>
<#-- 10. 去除字符串前后空格 ?trim -->
${msg1?trim?length} <br>
<#-- 11. 替换指定字符串 ?replace("xx","xxx") -->
${msg1?replace("o","a")}<br>
<br>


<#-- 如果值不存在，直接输出会报错 -->
<#--${str}-->
<#-- 使用!，当值不存在时，默认显示空字符串 -->
${str!}<br>
<#-- 使用!"xx"，当值不存在时，默认显示指定字符串 -->
${str!"这是一个默认值"}<br>
<#-- 使用??，判断字符串是否为空；返回布尔类型。如果想要输出，需要将布尔类型转换成字符串 -->
${(str??)?string}<br>

```




运行结果
在这里插入图片描述
3.5. sequence 类型
在com.suntao.controllter包下新建一个FreeMarker02.java文件，在webapp下中的template包下新建f02.ftl文件，编写以下数据。
在com.suntao包下新建po包，po包下新建User.java文件，代码如下
User.java

```java
package com.suntao.po;

public class User {
    private int id;
    private String name;
    private int age;

    public User() {
    }

    public User(int id, String name, int age) {
        this.id = id;
        this.name = name;
        this.age = age;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```



在Servlet中设置序列类型的数据
```java
// 序列类型 （数组、List、Set）
        // 数组操作
        String[] stars = new String[]{"周杰伦","林俊杰","陈奕迅","五月天"};
        request.setAttribute("stars",stars);
        // List操作
        List<String> citys = Arrays.asList("上海","北京","杭州","深圳");
        request.setAttribute("cityList",citys);
        // JavaBean集合
        List<User> userList = new ArrayList<>();
        userList.add(new User(1,"zhangsan",22));
        userList.add(new User(2,"lisi",18));
        userList.add(new User(3,"wangwu",20));
        request.setAttribute("userList",userList);
```

获取数据
```ftl
<#--
    数据类型：序列类型 （数组、List、Set）
        通过list指令输出序列
            <#list 序列名 as 元素名>
                ${名称}
            </#list>
        获取序列的长度 ${序列名?size}
        获取序列元素的下标 ${元素名?index}
        获取第一个元素 ${序列名?first}
        获取最后一个元素 ${序列名?last}
        倒序输出 序列名?reverse
        升序输出 序列名?sort
        降序输出 序列名?sort?reverse
        指定字段名排序 序列名?sort_by("字段名")
            注：一般是JavaBean集合，对应的字段名需要提供get方法
-->
<#-- 数组操作 -->
<#list stars as star>
    下标：${star?index} -- 名字：${star} <br>
</#list>
数组的长度：${stars?size} <br>
<#-- 获取第一个元素 -->
第一个元素：${stars?first} <br>
<#-- 获取最后一个元素 -->
最后一个元素：${stars?last} <br>
<hr>
<#-- List操作 -->
<#list cityList as city >
    ${city} <br>
</#list>
List的size：${cityList?size} <br>
<#-- 倒序输出 -->
<#list cityList?reverse as city >
    ${city} -
</#list>
<#-- 升序输出 -->
<#list cityList?sort as city >
    ${city} -
</#list>
<br>
<#-- 降序输出 -->
<#list cityList?sort?reverse as city >
    ${city} -
</#list>
<hr>
<#-- JavaBean集合 -->
<#list userList as user>
    编号：${user.id}&nbsp;&nbsp;
    姓名：${user.name}&nbsp;&nbsp;
    年龄：${user.age}&nbsp;&nbsp;
    <br>
</#list>
<#-- 按照指定字段名排序 -->
<#list userList?sort_by("age") as user>
    ${user.name} |
</#list>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
3.6. hash 类型
在Servlet中设置hash类型的数据
// Map操作
        Map<String,String> cityMap = new HashMap<>();
        cityMap.put("sh","上海");
        cityMap.put("bj","北京");
        cityMap.put("sz","深圳");
        request.setAttribute("cityMap",cityMap);
1
2
3
4
5
6
获取数据
<#--
    数据类型：hash类型
        key遍历输出
            <#list hash?keys as key>
                ${key} -- ${hash[key]}
            </#list>
        value遍历输出
            <#list hash?values as value>
                ${value}
            </#list>
-->
<#-- key遍历输出 -->
<#list cityMap?keys as key>
    ${key} -- ${cityMap[key]} <br>
</#list>
<#-- value遍历输出 -->
<#list cityMap?values as value>
    ${value} |
</#list>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
上面两种一起运行总代码和运行结果
User.java

package com.suntao.po;

public class User {
    private int id;
    private String name;
    private int age;

    public User() {
    }

    public User(int id, String name, int age) {
        this.id = id;
        this.name = name;
        this.age = age;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
注：一般是JavaBean集合，对应的字段名需要提供get方法
FreeMarker02.java

package com.suntao.controllter;

import com.suntao.po.User;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.*;

@WebServlet("/f02")
public class FreeMarker02 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // 序列类型 （数组、List、Set）
        // 数组操作
        String[] stars = new String[]{"周杰伦","林俊杰","陈奕迅","五月天"};
        request.setAttribute("stars",stars);
        // List操作
        List<String> citys = Arrays.asList("上海","北京","杭州","深圳");
        request.setAttribute("cityList",citys);
        // JavaBean集合
        List<User> userList = new ArrayList<>();
        userList.add(new User(1,"zhangsan",22));
        userList.add(new User(2,"lisi",18));
        userList.add(new User(3,"wangwu",20));
        request.setAttribute("userList",userList);

        // Map操作
        Map<String,String> cityMap = new HashMap<>();
        cityMap.put("sh","上海");
        cityMap.put("bj","北京");
        cityMap.put("sz","深圳");
        request.setAttribute("cityMap",cityMap);

        //请求跳转到ft2文件中
        request.getRequestDispatcher("template/f02.ftl").forward(request,response);
    }
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
f02.ftl

<#--
    数据类型：序列类型 （数组、List、Set）
        通过list指令输出序列
            <#list 序列名 as 元素名>
                ${名称}
            </#list>
        获取序列的长度 ${序列名?size}
        获取序列元素的下标 ${元素名?index}
        获取第一个元素 ${序列名?first}
        获取最后一个元素 ${序列名?last}
        倒序输出 序列名?reverse
        升序输出 序列名?sort
        降序输出 序列名?sort?reverse
        指定字段名排序 序列名?sort_by("字段名")
            注：一般是JavaBean集合，对应的字段名需要提供get方法
-->
<#-- 数组操作 -->
<#list stars as star>
    下标：${star?index} -- 名字：${star} <br>
</#list>
数组的长度：${stars?size} <br>
<#-- 获取第一个元素 -->
第一个元素：${stars?first} <br>
<#-- 获取最后一个元素 -->
最后一个元素：${stars?last} <br>
<hr>
<#-- List操作 -->
<#list cityList as city >
    ${city} <br>
</#list>
List的size：${cityList?size} <br>
<#-- 倒序输出 -->
<#list cityList?reverse as city >
    ${city} -
</#list>
<#-- 升序输出 -->
<#list cityList?sort as city >
    ${city} -
</#list>
<br>
<#-- 降序输出 -->
<#list cityList?sort?reverse as city >
    ${city} -
</#list>
<hr>
<#-- JavaBean集合 -->
<#list userList as user>
    编号：${user.id}&nbsp;&nbsp;
    姓名：${user.name}&nbsp;&nbsp;
    年龄：${user.age}&nbsp;&nbsp;
    <br>
</#list>
<#-- 按照指定字段名排序 -->
<#list userList?sort_by("age") as user>
    ${user.name} |
</#list>
<hr>
<#--
    数据类型：hash类型
        key遍历输出
            <#list hash?keys as key>
                ${key} -- ${hash[key]}
            </#list>
        value遍历输出
            <#list hash?values as value>
                ${value}
            </#list>
-->
<#-- key遍历输出 -->
<#list cityMap?keys as key>
    ${key} -- ${cityMap[key]} <br>
</#list>
<#-- value遍历输出 -->
<#list cityMap?values as value>
    ${value} |
</#list>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
运行结果：
在这里插入图片描述

4.FreeMarker 常见指令
4.1.assign 自定义变量指令
在com.suntao.controllter包下新建一个FreeMarker03.java文件，在webapp下中的template包下新建f03.ftl文件，编写以下数据。
使用 assign 指令你可以创建一个新的变量， 或者替换一个已经存在的变量。

<#--
	assign 自定义变量指令
		语法：
			<#assign 变量名=值>
			<#assign 变量名=值 变量名=值> （定义多个变量）
-->
<#assign str="hello">
${str} <br>
<#assign num=1 names=["zhangsan","lisi","wangwu"] >
${num} -- ${names?join(",")}
1
2
3
4
5
6
7
8
9
10
4.2.if elseif else 逻辑判断指令
可以使用 if ， elseif 和 else 指令来条件判断是否满足某些条件。

<#--
   if, else, elseif 逻辑判断指令
   	格式：
   	<#if condition>
   			...
   		<#elseif condition2>
   			...
   		<#elseif condition3>
   			...
   		<#else>
   			...
   	</#if>
   	注：
   		1. condition, condition2等：将被计算成布尔值的表达式。
   		2. elseif 和 else 指令 是可选的。
-->
<#assign score = 80>
<#if score < 60>
   你个小渣渣！
   <#elseif score == 60>
   	分不在高，及格就行！
   <#elseif score gt 60 && score lt 80>
   	哎哟不错哦！
   <#else>
   	你很棒棒哦！
</#if>
<br>
<#-- 判断数据是否存在 -->
<#assign list="">
<#if list??>
   数据存在
   <#else>
   	数据不存在
</#if>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
4.3.list 遍历指令
可以使用 list 指令来对序列进行遍历。

<#--
    list指令
        格式1：
            <#list sequence as item>
            </#list>
        格式2：
            <#list sequence as item>
            <#else>
                当没有选项时，执行else指令
            </#list>
        注：
            1. else 部分是可选的
            2. sequence： 想要迭代的项，可以是序列或集合的表达式
            3. item： 循环变量 的名称
            4. 当没有迭代项时，才使用 else 指令， 可以输出一些特殊的内容而不只是空在那里
-->
<#assign users = ["张三","李四","王五"]>
<#-- 遍历序列 -->
<#list users as user>
    ${user}
</#list>
<br>
<#--判断数据不为空，再执行遍历 （如果序列不存在，直接遍历会报错）-->
<#if users2??>
    <#list users2 as user>
        ${user}
    </#list>
</#if>
<br>
<#assign users3 = []>
<#-- 当序列没有数据项时，使用默认信息 -->
<#list users3 as user>
    ${user}
<#else>
    当前没有数据！
</#list>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
4.4.macro 自定义指令宏
可以使用 macro 指令来自定义一些自定义指令。

<#--
    macro 自定义指令 （宏）
        1. 基本使用
        格式：
            <#macro 指令名>
                指令内容
            </#macro>
        使用：
            <@指令名></@指令名>
         2. 有参数的自定义指令
        格式：
            <#macro 指令名 参数名1 参数名2>
                指令内容
            </#macro>
        使用：
            <@指令名 参数名1=参数值1 参数名2=参数值2></@指令名>
    注：
        1. 指令可以被多次使用。
        2. 自定义指令中可以包含字符串，也可包含内置指令
-->
<#-- 定义基本的自定义指令 -->
<#macro address>
    © 1999–2015 The FreeMarker Project. All rights reserved.
</#macro>
<#-- 使用指令 -->
<@address></@address> <br>
<@address></@address>
<hr>
<#-- 定义有参数的自定义指令 -->
<#macro queryUserByName uname>
    通过用户名查询用户信息 - ${uname}
</#macro>
<#-- 使用指令，并传递参数 -->
<@queryUserByName uname="admin"></@queryUserByName> <br>
<#-- 定义有多个参数的自定义指令 -->
<#macro queryUserByParams uname uage>
    通过多个餐宿查询用户信息 - ${uname} - ${uage}
</#macro>
<#-- 使用指令，并传递多个参数 -->
<@queryUserByParams uname="admin" uage=18></@queryUserByParams> <br>
<hr>
<#-- 自定义指令中包含内置指令 -->
<#macro cfb>
    <#list 1..9 as i>
        <#list 1..i as j>
            ${j}*${i}=${j*i}&nbsp;
        </#list>
        <br>
    </#list>
</#macro>
<@cfb></@cfb>
<@cfb></@cfb>
<#-- 动态数据 -->
<#macro cfb2 num>
    <#list 1..num as i>
        <#list 1..i as j>
            ${j}*${i}=${j*i}&nbsp;
        </#list>
        <br>
    </#list>
</#macro>
<@cfb2 num=5></@cfb2>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
4.5. nested 占位指令
nested 指令执行自定义指令开始和结束标签中间的模板片段。嵌套的片段可以包含模板中任意合法的内容。

<#--
    nested 占位指令
        nested 相当于占位符,一般结合macro指令一起使用。
        可以将自定义指令中的内容通过nested指令占位，当使用自定义指令时，会将占位内容显示。
-->
<#macro test>
    这是一段文本！
    <#nested>
    <#nested>
</#macro>
<@test><h4>这是文本后面的内容！</h4></@test>
1
2
3
4
5
6
7
8
9
10
11
4.6. import 导入指令
import 指令可以引入一个库。也就是说，它创建一个新的命名空间， 然后在那个命名空间中执行给定路径的模板。可以使用引入的空间中的指令。
新建commons.ftl文件
commons.ftl

<#macro cfb>
	<#list 1..9 as i>
		<#list 1..i as j>
			${j}*${i}=${j*i}&nbsp;
		</#list>
		<br>
	</#list>
</#macro>
1
2
3
4
5
6
7
8
在其他ftl页面中通过import导入commons.ftl的命名空间，使用该命名空间中的指令
f03.ftl

<#-- 导入命名空间 -->
<#import "commons.ftl" as common>
<#-- 使用命名空间中的指令 -->
<@common.cfb></@common.cfb>
1
2
3
4
4.7. include 包含指令
可以使用 include 指令在你的模板中插入另外一个 FreeMarker 模板文件 。 被包含模板的输出格式是在 include 标签出现的位置插入的。 被包含的文件和包含它的模板共享变量，就像是被复制粘贴进去的一样。

<#--包含指令(引入其他页面文件) include-->
<#--html文件-->
<#include "test.html">
<#--freemarker文件-->
<#include "test.ftl">
<#--text文件-->
<#include "test.txt">
1
2
3
4
5
6
7
运行总结果：
在这里插入图片描述
在这里插入图片描述

5.FreeMarker 页面静态化
通过上述介绍可知 Freemarker 是一种基于模板的、用来生成输出文本的通用工具,所以
我们必须要定制符合自己业务的模板，然后生成自己的 html 页面。Freemarker 是通过
freemarker.template.Configuration 这个对象对模板进行加载的（它也处理创建和缓存预
解析模板的工作），然后我们通过 getTemplate 方法获得你想要的模板，有一点要记住
freemarker.template.Configuration 在你整个应用必须保证唯一实例。

5.1. 定义模板
news.ftl

<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<#-- 新闻标题 -->
<h1>${title}</h1>
<p>
    新闻来源：${source} &nbsp; 发布时间：${pubTime?string("yyyy-MM-dd HH:mm")}
</p>
<#-- 新闻内容 -->
<p>
    ${content}
</p>
1
2
3
4
5
6
7
8
9
10
5.2. 加载模板
package com.suntao.controllter;

import freemarker.template.Configuration;
import freemarker.template.Template;
import freemarker.template.TemplateException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Date;
import java.util.HashMap;


/**
 * 1.获取模板
 * 2.准备数据
 * 3.创建html文件，拿到文件流（文件名，文件存放目录）
 * 4.将数据填充到模板对象中生成html
 */
@WebServlet("/news")
public class NewsServlet extends HttpServlet {

    @Override
    protected void service(HttpServletRequest request, HttpServletResponse resp) throws ServletException, IOException {
        //获取模板
        //获取配置对象
        Configuration configuration = new Configuration();
        //设置编码格式
        configuration.setDefaultEncoding("UTF-8");
        //提供上下文环境，和模板存放的目录
        configuration.setServletContextForTemplateLoading(getServletContext(),"/template");
        //获取到具体的模板，生成模板对象
        Template template = configuration.getTemplate("news.ftl");

        //准备数据
        HashMap<String, Object> map = new HashMap<>();
        map.put("title", "特别就业季：稳就业情况如何? 哪些问题待解?");
        map.put("source", "人民日报");
        map.put("pubTime", new Date());
        map.put("content", "中共中央政治局常务委员会近日召开会议强调，" +
                "要有针对性地开展援企、稳岗、扩就业工作，" +
                "做好高校毕业生、农民工等重点群体就业工作，" +
                "积极帮助个体工商户纾困。疫情期间，稳就业情况如何？还有哪些问题待解？" +
                "记者采访了不同群体，记录这个特别的就业季。");


        //创建html文件（文件名，文件存放目录）
        String basePath = request.getServletContext().getRealPath("/");
        //配置文件存放的路径
        File filePath = new File(basePath + "/html");
        //判断文件夹是否存在，不存在则创建
        if(!filePath.exists()){
            filePath.mkdir();
        }
        //创建文件名
        String fileName = System.currentTimeMillis() + ".html";
        //获取文件的完整路径，生成file对象
        File file = new File(filePath, fileName);
        //获取目标文件的文件流
        FileWriter fileWriter = new FileWriter(file);

        try {
            //将数据填充到模板对象中生成html
            template.process(map,fileWriter);
            //生成html成功的信息
        } catch (TemplateException e) {
            e.printStackTrace();
            //生成html失败的信息
        }

    }
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
5.3. 生成对应的html文件
浏览器地址栏输入：
http://localhost:8989/news
生成的文件存放在当前项目的webapp目录下的html目录中
在这里插入图片描述
运行该文件
在这里插入图片描述

6.FreeMarker 运算符
6.1. 算术运算符
<!--
	算术运算
		+、-、*、/、%
-->
<#assign a1 = 8 a2 = 2 >
${a1} + ${a2} = ${a1 + a2} <br/>
${a1} - ${a2} = ${a1 - a2} <br/>
${a1} * ${a2} = ${a1 * a2} <br/>
${a1} / ${a2} = ${a1 / a2} <br/>
${a1} % ${a2} = ${a1 % a2} <br/>
<!--字符串运算-->
${"hello" + "," + "freemarker"}
1
2
3
4
5
6
7
8
9
10
11
12
6.2. 逻辑运算符
<#--
	逻辑运算符
		&&、||、!
-->
1
2
3
4
6.3. 比较运算符
<#--
	比较运算符
		> (gt): 大于号，推荐使用 gt
		< (lt)： 小于号，推荐使用 lt
		>= (gte): 大于等于， 推荐是用 gte
		<= (lte): 小于等于，推荐使用 lte
		== ： 等于
		!= : 不等于
-->
1
2
3
4
5
6
7
8
9
6.4. 空值运算符
<#--
	空值运算符
		1. ??:判断是否为空，返回布尔类型
		如果不为空返回 false， 如果为空返回 true，不能直接输出
		${(name??)?string}
	2. !: 设置默认值，如果为空，则设置默认值
		1. 设置默认为空字符串：
		${name!}
		2. 设置指定默认值
		${name!'zhangsan'}
-->
1
2
3
4
5
6
7
8
9
10
11
文章知识点与官方知识档案匹配，可进一步学习相关知识
Java技能树首页概览77529 人正在系统学习中

Trycol
关注

65


411
打赏

7




freemarker 详细介绍
zhang_adrian的博客
 1139

和业务运算， 之后模板显示已经准备好的数据。在模板中，主要用于如何展现数据， 而在模板之外注意于要展示什么数据
freemarker
最新发布
hnhroot的博客
 190











