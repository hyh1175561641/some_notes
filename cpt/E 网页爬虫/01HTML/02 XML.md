# XML



http://x-stream.github.io/
https://mvnrepository.com/artifact/com.thoughtworks.xstream/xstream/1.4.20




Extensible Markup Language XML 可扩展标记语言
World Wide Web Consortium: 万维网联盟

XML标签自定义的，语法很严格，用来存储数据

XML的运用
XML可以用来当配置文件使用(properties,JSON)
XML可以在在网络中传输

```XML
<?xml version="1.0" encoding="UTF-8/GBK" ?> <!--文档声明只能写在第一行，不能有空格回车-->
<?xml version="版本号必须的属性" encoding="编码默认值：ISO-8859-1" standalone="是否独立是否依赖于其他文件取值无效yes/no,一般情况不使用这个属性" ?>
<users> <!--有且只有一个根标签-->
  <user id="1"> <!--属性值必须使用单/双引号引起来-->
    <name>zhangsan</name> <!--标签必须正确关闭或者自闭合<br/>-->
    <age>23</age> <!--标签名称区分大小写-->
    <gender>male</gender> <!--标签名由字母数字其他字符组成,不能由数字或标点符号开头-->
  </user> <!--名称不能以字母xml(包含大写组合),名称不能包含空格-->
  <user id="2"> <!--id属性的值是唯一的-->
    <name>lisi</name>
    <age>25</age>
    <gender>female</gender>
  </user>
</users>

<area>写入一段字符包括特殊字符
  <!-- 使用转义字符 -->
  <code>if(a &lt; b &amp;&amp; a &gt; c)</code> <!-- if(a > b && a > c){} -->
  <!-- 使用<![CDATA[]] -->
  <code>
    <![CDATA[
      if(a < b && a > C) {}
    ]]>
  </code>
</area>
```

```xml
<!-- xml也可以使用样式 -->
<!-- a.css -->
name{color:red;}
<!-- xxx.xml -->
<?xml version="1.0" encoding="UTF-8/GBK" ?>
<?xml-stylesheet type="text/css" href="a.css" ?>
<users>
  <user id="1">
    <name>zhangsan</name>
    <age>23</age>
    <gender>male</gender>
  </user>
  <user id="2">
    <name>lisi</name>
    <age>25</age>
    <gender>female</gender>
  </user>
</users>

```


# 约束
在用户编写和程序解析的时候，制定一些规范，规定xml文档的书写规则
软件编写约束文档，程序员遵循约束文档

DTD: 简单的约束技术
Schema: 一种复杂的约束技术

```xml
<!-- 引入xml约束文档 -->

```



# XML解析器
JAXP: sun公司提供的解析器，支持dom和sax两种思想
DOM4J
jsoup: 是一款Java的HTML解析器，可直接解析某个URL地址，HTML文本内容，可通过DOMCSS以及类似jQuery的操作方法来读取和操作数据
PULL: Android内置的解析器, sax方式的解析









# SVG

runoob SVG教程 https://www.runoob.com/svg/svg-tutorial.html

rect方形

ellipse椭圆

