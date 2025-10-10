





https://www.8kmm.com/dev
http://www.fhdq.net/
https://www.sojson.com/rgb.html
https://www.bootcss.com/
https://codepen.io/pen/
https://www.w3school.com.cn
https://www.runoob.com
https://www.runoob.com/tags/ref-byfunc.html，https://www.w3school.com.cn/tags/index.asp
https://www.runoob.com/cssref/css-reference.html，https://www.w3school.com.cn/cssref/index.asp
https://developer.mozilla.org/zh-CN/docs/Web/HTML
https://blog.csdn.net/qq_39197547/article/details/82789464
https://www.w3schools.com/
https://www.lanrenzhijia.com/




《HTML5权威指南》[美]Adam Freeman 人民邮电出版社 IBSN 978-7-115-33836-5
《HTML5与CSS3权威指南》 陆凌牛 机械工业出版社 IBSN 978-7-111-51442-8


https://tool.lu/
https://tool.oschina.net/
https://www.jyshare.com/front-end/53/



http://web.itheima.com/#navkcdg
https://www.jianshu.com/p/5ba253651c3b
https://www.itheima.com/course/phptext.html?jingjia-heima-pinpaici-pc-heimachengxuyuan


前端原型图
https://www.axure.com/ Axure
https://modao.cc/ 墨刀
https://mastergo.com/ 莫高



浏览器支持



```html
<!--写代码技巧-->
<meta http-equiv="refresh" content="3"><!--3秒刷新-->
<style>*{outline:1px dashed #aaa;}</style>

<!-- 跨域:未知的问题 -->
<link crossorigin="anonymous">
<script crossorigin="anonymous">
```







# HTML

超文本标记语言

**背景知识**



# 基础标签

## 代码结构

```html
<!DOCTYPE>定义文档类型，告知Web浏览器使用了哪种HTML版本
<html>告知浏览器这是一个HTML文档
<head>
<body>定义文档的主体，包含文档的所有内容
<!--...-->注释
```

## 文档布局

body内容的组织结构，语义化标签

是不是还有\<container\>标签

`<hgroup>`

```html
<main></main>指定文档的主体内容，此元素是唯一的
<header></header>定义文档或者文档的一部分区域的页眉，介绍内容或者导航链接栏的容器
<nav></nav>定义导航栏链接部分，标注导航栏链接
<section></section>定义了文档的某个区域，如章节，头部，底部或者文档的其他区域
<article></article>定义独立的内容，必须是有意义的且必须是独立于文档的其余部分。论坛帖子，博客文章，新闻故事，评论
<aside></aside>定义article标签外的内容，与附近的内容相关，可用作文章的侧栏
<footer></footer>文档或者文档的一部分区域的页脚，包含文档作者的姓名，文档的版权信息，使用条款的链接，联系信息
<details open打开底下的内容></details>用户可见的或者隐藏的需求的补充细节，与summary配合使用
<summary></summary>此元素应该是details元素的第一个子元素，为details定义一个可见的标题，用户点击标题时会显示出详细信息
<figure></figure>规定独立的流内容，元素的位置相对于主内容是独立的
<figcaption></figcaption>为figure定义标题
<dialog open可以与用户交互></dialog>定义一个对话框，确认框或窗口
```



## 头部标签,元数据

```html
<head>所有头部元素的容器
<title>定义文档的标题，显示在浏览器工具栏中，页面添加到收藏夹，搜索引擎结果的标题

<meta	名称="值"
      charset="文档的字符编码，字符集"
      name="元数据的名称 application-name(页面代表Web应用程序的名称) author(文档作者的名字) description(页面的描述) generator(生成文档的一个软件包) keywords(关键词列表)"
      http-equiv="把content属性关联到HTTP头部 content-type(文档的字符编码) default-style(预定义的样式表) refresh(自动刷新)"
      content="给出了name或http-equiv相关的值"
      ><!--文档的元数据，会被浏览器和搜索引擎解析-->
<link rel="当前文档与被链接资源的关系 stylesheet(样式表) author(文档的作者) alternate(该文档的替代版本) help(帮助文档) icon(该文档的图标) license(版权信息) search(链接到针对文档的搜索工具) next(文档集合的下一部分) prev(文档集合的上一部分) prefetch(应该对目标资源进行缓存)"
      type="MIME_type类型 文档的类型"
      href="外部资源的URL"
      hreflang="外部资源的文本语言 language_code"
      media="链接文档显示在什么设备上，有点复杂不写了，不同媒介不同类型，通常与CSS样式表一起使用"
      HTML5
      sizes="icon的尺寸，浏览器都不支持"
      ><!--定义外部资源-->
<base	href="URL页面所有相对链接的基准"
      target="何处打开链接"><!--页面上所有相对链接规定默认URL或默认目标-->


<实例：>
<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript"><!--定义文档关键词，用于搜索引擎-->
<meta name="description" content="Free Web tutorials on HTML and CSS"><!--定义页面描述-->
<meta name="author" content="Hege Refsnes"><!--定义页面作者-->
<meta http-equiv="refresh" content="3"><!--每隔3秒刷新一次网页-->
<meta http-equiv="refresh" content="0;url=http://www.baidu.com"><!--立刻跳转到百度首页-->

<link rel="stylesheet" type="text/css" href="styles.css"><!--链接样式表-->
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
```


## 样式
```html
<style	type="MIME_type(常用text/css)"
       media="太复杂，略"
       scoped样式仅仅应用到 style 元素的父元素及其子元素>
</style><!--文档样式信息-->
<div></div><!--块级元素，用css进行格式化-->
<span></span><!--行内元素，用css进行格式化-->
```

## 文档格式

呈现内容的组织结构

```html
<h1>-<h6>文档的标题
<p>文档的段落
<br>简单的换行符
<hr>一行水平线
```








## 文本格式
**文本格式化**

```
small小号文本
strong重要文本粗体字，b粗体字
em被强调斜体字，i斜体字，dfn定义项目斜体字，var变量斜体字
ins被插入的文本下划线,u下划线
del删除中划线，s中划线

code代码，samp计算机样本，kdb键盘输入

abbr缩略语，title属性解释内容的全称
pre保留空格和换行等宽字体
address作者和联系方式
```





`<b>`加粗文本

`strong`加重文本

`em`着重文字，被强调的文本

`i`斜体字，表示科技术语，俗语，想法，名字等

`small`小号字，表示小型文本和旁注

`sub`下标，可以表示化学公式。于当前文本流中字符高度的一半为基准线的下方，但与文本中文字的字体和字号都是一样的

`sup`上标，可以表示数学乘方。于当前文本流中字符高度的一半为基准线的上方，但与文本中文字的字体和字号都是一样的

`u`下划线。表示单词拼写错误，HTML5 规范建议开发者尽量使用其他元素替代u元素

`ins`插入字，下划线。有cite和datetime属性

`s`中划线。定义那些不正确的文本

`del`删除字，中划线。有cite和datetime属性

- 标题应该用 `<h1>-<h6>`标签表示，被强调的文本应该用`<em>`标签表示，重要的文本应该用`<strong>`标签表示，被标记的或者高亮显示的文本应该用`<mark>`标签表示。
- strong强调不仅可以用加粗表现，也可使用下划线，字体加大，其他颜色等方式，而b标签只能加粗标签

**计算机输出**

`code`计算机代码

`kbd`键盘码

`samp`计算机程序的样本文件

`var`定义变量，和pre code配合使用

`pre`预格式化的文本，通常会保留空格和换行符，文本也会呈现等宽字体，常用来表示计算机的源代码。

**引文，引用，及标签定义**

`abbr`缩写，用title标记（鼠标悬停显示），为浏览器或搜索引擎提供有用信息

`address`地址，文档作者/所有者的联系信息

`bdo dir="ltr rtl"`文字方向。left to right从左到右

`blockquote`摘自另一个源的块引用。有cite属性。看不懂。

`q`短的行引用。有cite属性。看不懂。

`cite`定义作品的标题，比如书籍、歌曲、电影、电视节目、绘画、雕塑

`dfn`定义项目

- 短语标签em strong dfn code samp kbd var 

**HTML5新标签**

`bdi`指的是 bidi 隔离（Bi-directional Isolation），设置一段新文本，脱离父元素的文本方向设置

`mark`带记号的文本

`ruby` `rp` `rt`搞不懂，在东亚使用，显示的是东亚字符的发音

`wbr`规定在文本中何处适合添加换行符

```html
<time	datetime="YYYY-MM-DDThh:mm:ssTZD">
年月日（T是必须的分隔符）时分秒 TZD是时区标识符
</time><!--时间/日期-->
<meter	value="必需，规定度量的当前值"
       min="规定范围最小值，默认0"
       max="规定范围最大值，默认1"
       optimum="规定度量的最优值"
       high="被界定为高的值的范围"
       low="被界定为低的值的范围"
       form="规定所属的表单，暂无浏览器支持">
</meter><!--度量衡，这些数都是浮点数-->
<progress	value="规定总共需要多少任务"
          max="规定已经完成多少任务">
</progress><!--运行中的任务进度-->
```





## 超链接
```html
<a	href="URL #id_name(锚点)"
   target="_blank(在新窗口打开) _self(默认，在相同的框架打开) _parent(在父框架集中打开) _top(整个窗口打开) framename(框架常用)"
   hreflang="双字符语言代码"
   type="MIME_type"
   rel="当前文档与被链接文档的关系。太多了，略"
   HTML5:
   download="定义了下载链接的地址"
   media="太复杂，略"
   ></a>
```

- 锚点 4种锚点方法 https://blog.csdn.net/this_ITBoy/article/details/76020658

## 表单

```html
<form	action="把表单提交到指定位置"
      method="GET(默认，数据添加到URL中) POST(数据添加到HTTP请求内)"
      name="名字"
      target="_self(默认统一窗口打开) _blank(新窗口/选卡打开) _parent(在父框架打开) _top(在整个窗口打开) framename(在指定的iframe中打开)"
      enctype="将表单数据发送到服务器之前如何对其进行编码"
      accept-charset="UNKNOWN(默认，包含form的文档) 提交表单的字符编码"
      HTML5:
      autocomplete="on默认。规定启用自动完成功能 off"
      novalidate(当提交表单时不对表单数据（输入）进行验证)
      ></form><!--表单-->
<input	type="button(按钮) checkbox(复选框，打对勾) file(文件上传) hidden(隐藏输入字段) image(图像按钮) password(输入密码) radio(单选按钮) reset(重置，表单所有值为默认的) submit(提交按钮) text(默认，文本) HTML5: color(拾色器) date(date控件) datetime(date和time控件) datetime-local(date和time控件) email(邮箱地址) month(month和year控件) number(输入数字) range(输入精确值不重要的输入) search(搜索字符串) tel(电话号码) time(输入时间) url(输入URL) week(输入week和year控件)"
       name="名称"
       value="文本的默认值，按钮的值"
       size="默认值20输入框的可见宽度"
       maxlength="输入框的最大字符数"
       alt="图像无法查看时的替代文本"
       src="提交按钮的图像URL只针对type=image，会上传点击图像的位置信息"
       accept="文件上传的服务器可接受类型只针对type=file audio/* video/* image/* MIME_type"
       checked="页面加载时被预先选定的input元素只针对type=checkbox或radio"
       readonly输入字段是只读的，可以选中可以复制不能修改
       disabled禁用该元素不能用不能点击
       HTML5:
       autocomplete="on(启用自动完成) off(禁用自动完成)"
       autofocus="获得焦点"
       form="所属的表单id 以空格分隔"
       formaction="提交到指定位置，覆盖form的action属性"
       formenctype="覆盖form的enctype属性"
       formmethod="覆盖form的method属性"
       formnovalidate覆盖form的novalidate属性
       formtarget="覆盖form的target属性，可以与submit和image配合使用"
       width="针对type=image的宽度"
       height="针对type=image的高度"
       list="绑定到input元素的datalist的id"
       max="数字或者日期的最大值"
       min="数字或者日期的最小值"
       multiple可以多选，适用于email和file
       pattern="正则表达式"
       placeholder="预期值，简短的描述信息，显示在文本框中"
       required必填字段
       step="合法数字间隔，比如3（合法值是-3 0 3 6 9）"
       ><!--用户可以输入数据的输入字段-->
<textarea	rows="默认值是2，可见高度，行数"
          cols="默认值是20，可见宽度，字数"
          name="名称"
          readonly文本区域为只读
          disabled被禁用的文本区域既不可用，文本也不可选择（不能被复制）
          HTML5:
          autofocus自动获得焦点
          form="form的id"
          maxlength="文本区域的最大长度，最多能写多少个字"
          placeholder="简短的描述，期望这里写什么"
          required规定这个区域是必填的
          wrap="soft(默认，提交表单文本不换行) hard(提交表单文本换行，使用此值必须指定cols属性)"
          ></textarea><!--多行的文本控件-->
<button	type="submit(默认，提交按钮) button(可点击的按钮) reset(重置按钮，清除表单数据)"
        value="值，提交给表单的值，用input属性代替"
        name="名称，不同的按钮可以共享相同的名称"
        disabled禁用按钮
        HTML5:
        form="form的id"
        autofocus页面加载时按钮应当自动地获得焦点
        formaction="见form属性"
        formenctype="见form属性"
        formmethod="见form属性"
        formnovalidate见form属性
        formtarget="见form属性"
        ></button><!--定义一个按钮-->
<select	size="默认是1，如果设置multiple，默认是4。下拉列表可见数目"
        name="名称"
        disabled禁用，不可用不可点击
        multiple可以同时多选，使用复选框代替
        HTML5:
        autofocus获得焦点
        form="form的id"
        required浏览器都不支持，规定这个区域是必填的
        ></select><!--创建下拉列表-->
<optgroup	label="选项组规定标签/描述"
          disabled禁用，不可用不可点击
          ></optgroup><!--下拉列表的相关选项组合在一起-->
<option	label="下拉列表会显示更短的版本"
        value="提交表单的值"
        selected默认值，预选的，下拉列表最前面的位置
        disabled禁用，不可用不可点击
        ></option><!--下拉菜单的条目-->
<label	for="绑定元素的id"
       form="表单的id">
</label><!--input元素的标记，鼠标点击该元素会关联到input元素上-->
<fieldset	form="表单id，浏览器都不支持"
          name="名称"
          disabled禁用></fieldset><!--围绕表单元素的边框-->
<legend></legend><!--fieldset元素的标题-->
<HTML5:>
<datalist></datalist><!--input元素可能的选项列表，使用input的list属性绑定此元素-->
<keygen><!--表单的密钥生成器的字段，新标准已废弃-->
<output for="元素id" form="" name=""></output><!--计算结果输出显示-->
```

- form元素包含一个或多个input，textarea，button，select，option，optgroup，fieldset，label表单元素
- 如果在 HTML 表单中使用 button 元素，不同的浏览器会提交不同的值。Internet Explorer 将提交 \<button\> 与 \<button/\> 之间的文本，而其他浏览器将提交 value 属性的内容。请在 HTML 表单中使用 input 元素来创建按钮。



## 列表

```html
<ol type="1(数字)A(大写)a(小写)I(罗马大小写)i"
    start="n(有序列表起始值)"
    reversed<!--规定列表为降序-->
    ></ol><!--有序列表-->
<ul type="disc(默认实心圆) circle(空心圆) square(实心方块)"></ul><!--无序列表-->
<li type="1Aail disc circle square"
    value="当前项的数字"></li><!--列表项-->
<dl 定义列表：一前一后的一种样式></dl><!--有序列表起始值-->
<dt 定义列表的项目></dt>
<dd 定义列表的描述></dd>
```



```
ul是unordered lists的缩写 (无序列表)
li是list item的缩写 （列表项目）
ol是ordered lists的缩写（有序列表）
dl是definition lists的英文缩写 (自定义列表)
dt是definition term的缩写 (自定义列表组)
dd是definition description的缩写（自定义列表描述）
nl是navigation lists的英文缩写 （导航列表）
tr是table row的缩写 （表格中的一行）
th是table header cell的缩写 （表格中的表头）
td是table data cell的缩写 （表格中的一个单元格）
```



## 表格

```html

<table border="1(这个属性可以不写，可以用于布局)"></table><!--定义一个表格-->
<tr></tr><!--列表行-->
<th colspan="横跨的列数，等于0时情况特殊"
    rowspan="横跨的行数"
    headers="关联表头单元格 name"
    scope="col(单元格是列的表头) row(行的表头) colgroup(列组的表头) rowgroup(行组的表头)"
    ></th><!--表头单元格，第一行用此元素，通常是粗体居中-->
<td colspan="横跨的列数，等于0时情况特殊"
    rowspan="横跨的行数"
    headers="关联表头单元格 name"></td><!--标准单元格，通常是左对齐文本-->
<caption></caption><!--定义表格的标题，直接放在table之后-->
<colgroup	span="横跨的列数"></colgroup><!--对表格的列进行组合，对其格式化-->
<col	span="横跨的列数"><!--规定了colgroup内部每一列的属性-->
<!--可以向整个列应用样式，而不需要重复为每个单元格或每一行设置样式-->
<thead></thead><!--组合表格表头的内容-->
<tbody></tbody><!--组合表格主体的内容-->
<tfoot></tfoot><!--组合表格页脚的内容-->
<!--当包含多个页面的长的表格被打印时，表格的表头和页脚可被打印在包含表格数据的每张页面上-->
```
```html
<table border="1">
	<tr>
  	<th></th>
  	<th></th>
  </tr>
  <tr>
  	<td></td>
    <td></td>
  </tr>
</table>
```

- col 列，竖起来的
- row 行，横着数的

## 框架

`<frame>` `<frameset>` `<noframes>`HTML5已废弃元素

```html 
<iframe	src="文档地址"
        width="宽度 px"
        height="高度 px"
        name="可以让链接target到框架里"
        HTML5
        srcdoc="必需是有效的HTML语法，几个简短的HTML元素"
        sandbox="以后再看吧"
        seamless 浏览器支持的不多
        ></iframe>
<!--src、sandbox和seamless常常一起用-->

<!--示例-->
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<a href="www.baidu.com" target="iframe_a">baidu.com</a>
<!--点击链接时，在框架内打开了链接地址-->
```

## 图像

svg和canvas到时候一起看，还有mathML数学公式，还有图片拖放

```html
<img src="必须属性，图像的URL"
     alt="必须属性，图像无法显示时的替代文本"
     title="鼠标悬停"
     width="写数字，单位是px"
     height="写数字，单位是px"
     ismap服务器端图像映射，点击图像会发送服务器坐标
     usemap="将图像定义为客户端图像映射 #mapname"
     crossorigin="图像的跨域属性，不懂"><!--页面中的图片-->
<map	name="必需，绑定img的usemap属性"></map><!--带有可点击区域的一副图像-->
<area	shape="区域的形状 default(默认全部区域) rect(矩形区域) circle(圆形区域) poly(多边形区域)"
      coords="区域的坐标，与shape配合使用 左上角是0,0[shape为rect,规定右上角和左下角的坐标(x1,y1,x2,y2)][shape为circ,规定圆心坐标和半径(x,y,radius)][shape为poly,规定多边形顶点的值(x1,y1,x2,y2,..,xn,yn)]"
      alt="图片无法显示时的替代文本"
      href="见a标签，锚"
      target="见a标签"
      HTML5:
      media="太复杂，略"
      rel="见a标签"
      hreflang="双字符的语言代码"
      type="MIME_type"
      ><!--图像内部的可点击区域始终嵌套在map内部-->
```
canvas

```html
<canvas	width="像素宽度"
        height="像素高度">
</canvas><!--画布，js绘制图形，当像素宽高发生变化，内容会被清空-->
```
- 图像无法显示时用alt属性值替代图片
- 不要用height和width属性来缩放图像，这样用户必须下载大容量的图像。最好通过软件把图像处理为合适的尺寸

## 媒体
```html
<audio	src="音频文件的URL"
       preload="auto(载入整个音频) meta(只载入元数据) none(加载后不载入音频) 如果设置了autoplay则忽略该值"
       autoplay音频就绪马上播放
       controls音频控件的显示方式
       loop循环播放
       muted静音></audio><!--定义声音，其他音频流MP3-->
<source	src="媒体文件的URL"
        type="MIME_type video/ogg video/mp4 video/webm audio/ogg audio/mpeg"
        media="浏览器都不支持"><!--定义媒体资源，多个源-->
<track	src="轨道的URL"
       kind="轨道的种类 captions(将在播放器中显示的简短说明) chapters(章节，导航媒介资源) descriptions(描述，用于通过音频描述媒介的内容，假如内容不可播放或不可见) metadata(脚本使用的内容) subtitles(字幕，在视频中显示字幕)"
       srclang="如果kind=subtitles，则必须使用此属性，双字母的语言代码"
       label="文本轨迹的标题"
       default用户应该使用这个轨道><!--外部文本轨道，字幕-->
```

视频

```html
<video	src="视频文件的URL"
       preload="auto(一旦页面加载，就开始加载视频) metadata(只载入元数据) none(加载后不载入视频) 如果设置了autoplay则忽略该值"
       width="宽度，单位是像素"
       height="高度，单位是像素"
       poster="视频正在下载时显示的图像，直到用户点击播放按钮"
       autoplay视频就绪马上播放
       controls视频控件的显示方式
       loop循环播放
       muted静音></video><!--定义音频或视频MP4-->
```



## 编程脚本

`<applet>`

```html
<script type="MIME-type(text/javascript默认 text/ecmascript application/ecmascript application/javascript text/vbscript)"
        src="外部脚本URL，避免了重复编写脚本"
        charset="外部脚本的字符编码，当外部脚本与文档编码不同时，使用该属性"
        defer当页面完全加载后，才会执行脚本，仅适用于外部脚本
        async一旦脚本可用，则会异步执行，仅适用外部脚本>
</script><!--定义客户端脚本，可以使用src指向外部脚本-->
<noscript></noscript><!--浏览器不支持脚本，则会显示这个内容-->
<embed	src="外部文件地址"
       width="宽度，单位是像素"
       height="高度，单位是像素"
       type="MIME_type"><!--定义了一个容器，嵌入外部应用或者插件-->
<object	data="所用资源的URL"
        width="宽度，单位是像素"
        height="高度，单位是像素"
        name="名称"
        type="MIME_type"
        usemap="与对象一起使用的图像映射名称 #mapname"
        form="浏览器都不支持 所属的表单form_id"></object><!--嵌入的对象-->
<param	name="名称"
       value="值"><!--对象的参数与object一起使用-->
```

- 有多种执行外部脚本的方法：
  - 如果 async="async"：脚本相对于页面的其余部分异步地执行（当页面继续进行解析时，脚本将被执行）
  - 如果不使用 async 且 defer="defer"：脚本将在页面完成解析时执行
  - 如果既不使用 async 也不使用 defer：在浏览器继续解析页面之前，立即读取并执行脚本

## 全局属性

```html
<tag accesskey="访问元素的键盘快捷键"
     class="类名"
     dir="文本方向"
     id="唯一id名"
     lang="元素内容的语言代码"
     style="行内样式"
     tabindex="元素Tab键的控制次序"
     title="鼠标悬停显示的内容"
     HTML5:
     contenteditable="是否可编辑元素的内容"
     contextmenu="一个元素的上下文菜单，用户右击该元素，出现上下文菜单"
     data-* ="储存页面的自定义数据"
     draggable="某个元素是否可以拖动"
     dropzone="是否将数据复制，移动，或链接，或删除"
     hidden="规定对元素进行隐藏"
     spellcheck="是否拼写错误"
     translate="是否一个元素的值在页面载入时是否需要翻译"></tag>
```
title属性鼠标悬停时显示此段文字”是\<form\>\<a\>元素的常用属性

## 事件属性

HTML事件是发生在HTML元素上的事情，当在HTML页面中使用JavaScript时，JavaScript可以触发这些事件。

HTML事件可以是浏览器行为，也可以是用户行为，当页面完成加载时，input字段改变时，按钮被点击时，当JavaScript触发时可以执行一段代码

```html
<buttom onclick="this.innerHTML=Date()">时间？</buttom>
```



```html
<!--常见的HTML事件的列表-->
onchange
onclick
onmouseover
onmouseout
onkeydown
onload
```




# 组件

```html
<!--对话框-->
<dialog open>
    <p>Greetings, one and all!</p>
    <form method="dialog">
        <button>OK</button>
    </form>
</dialog>




```



# 其他

# 长度单位
绝对长度
px像素
cm厘米，mm毫米
in英寸(=96px)
pt  (72pt=1in)
pc (=12pt)

相对长度
em (=16px默认值)适应于当前字体尺寸
% 百分号 适应于当前字体的百分比
ex 适应于当前字体字母x的高度
ch 数字0的宽度
rem 根元素\<html\>的font-size
vw 浏览器宽度的1% viewport width
vh 浏览器高度的1% viewport height
vmin 浏览器宽和高较小的那个的1%
vmax 浏览器宽和高较大的那个的1%


# SEO三大标签

```html
<title>这里写标题（百度28个字）</title>
<meta name="description" content="这里写描述(不超过120个汉字)" />
<meta name="Ketwords" content="这里写关键字（限制在6~8个词左右）" />
```
description是搜索结果的简述



#  ico图标

Favicon.ico放在根目录底下
```html
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon"/>
<!-- http://www.jd.com/favicon.ico --> 

```
ico制作网站www.bitbug.net

# 特殊符号实体

[字符实体](https://www.runoob.com/html/html-entities.html)



# 对HTML的总结

html构成了一套完整而丰富的文档内容，由以下内容构成
文本格式，粗细，样式
文档格式，标题，段落，折行，水平线
文档大纲，头部，主体，页头，页主，页脚等
超链接，超链接，外部资源link
表单，输入框，按钮，下拉列表，
列表表格，有序无序，行列，表头，表行
图音影，外部图像，绘制图像，声音
框架，内联框架
元信息，meta
样式，div，span，css
脚本，js
以上这些元素，不仅仅是在网页中存在，办公文档，桌面UI设计也是由类似的元素组成









grid  栅(shān)格




# Web前端企业开发命名规范

烟波煮雨 CSDN博客

https://blog.csdn.net/qq_37275680/article/details/78283303

(一)网页内容类

标题: title 
摘要: summary 
箭头： arrow 
商标： label 
网站标志： logo 
转角/圆角： corner 
横幅广告： banner 
子菜单： subMenu 
搜索： search 
搜索框： searchBox 
登录： login 
登录条：loginbar 
工具条： toolbar 
下拉： drop 
标签页： tab 
当前的： current 
列表： list 
滚动： scroll 
服务： service 
提示信息： msg 
热点：hot 
新闻： news 
小技巧： tips 
下载： download 
栏目标题： title 
热点： hot 
加入： joinus 
注册： regsiter 
指南： guide 
友情链接： friendlink 
状态： status 
版权： copyright 
按钮： btn 
合作伙伴： partner 
投票： vote 
左右中：left right center

**(二)注释的写法:**

/* Footer */ 
内容区 
/* End Footer */

**(三)id的命名:**

(1)页面结构

容器: container 
页头：header 
内容：content/container 
页面主体：main 
页尾：footer 
导航：nav 
侧栏：sidebar 
栏目：column 
页面外围控制整体布局宽度：wrapper 
左右中：left right center

(2)导航

导航：nav 
主导航：mainnav 
子导航：subnav 
顶导航：topnav 
边导航：sidebar 
左导航：leftsidebar 
右导航：rightsidebar 
菜单：menu 
子菜单：submenu 
标题: title 
摘要: summary

(3)功能

标志：logo 
广告：banner 
登陆：login 
登录条：loginbar 
注册：regsiter 
搜索：search 
功能区：shop 
标题：title 
加入：joinus 
状态：status 
按钮：btn 
滚动：scroll 
标签页：tab 
文章列表：list 
提示信息：msg 
当前的: current 
小技巧：tips 
图标: icon 
注释：note 
指南：guild 
服务：service 
热点：hot 
新闻：news 
下载：download 
投票：vote 
合作伙伴：partner 
友情链接：link 
版权：copyright

**(四)class的命名:**

(1)颜色:使用颜色的名称或者16进制代码,如

.red { color: red; } 
.f60 { color: #f60; } 
.ff8600 { color: #ff8600; }

(2)字体大小,直接使用”font+字体大小”作为名称,如

.font12px { font-size: 12px; } 
.font9pt {font-size: 9pt; }

(3)对齐样式,使用对齐目标的英文名称,如

.left { float:left; } 
.bottom { float:bottom; }

(4)标题栏样式,使用”类别+功能”的方式命名,如

.barnews { } 
.barproduct { }

**注意事项:**

1.一律小写; 
2.尽量用英文; 
3.不加中杠和下划线; 
4.尽量不缩写，除非一看就明白的单词.

推荐的 CSS 书写顺序 
//显示属性 
display 
list-style 
position 
float 
clear

//自身属性 
width 
height 
margin 
padding 
border 
background

//文本属性 
color 
font 
text-decoration 
text-align 
vertical-align 
white-space 
other text 
content



