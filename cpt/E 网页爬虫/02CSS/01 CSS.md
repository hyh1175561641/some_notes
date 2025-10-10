

w3school https://www.w3school.com.cn/css/index.asp

caniuse https://www.caniuse.com 浏览器支持





# CSS

# 外部样式

``````css
<link rel="stylesheet" herf="css/index.css">
@charset "utf-8";/* 如果css文件有中文，设置字符集*/
``````

# 选择器
```css
<h1 class="js css" id="icss" title="悬停显示">css</h1>
*{}/*通配符选择器*/
p{}元素选择器
.css类选择器，.js.css 选择类名中同时都有的元素 .c .css 选择a类中包含b类的元素
#icss选择器
h1[title="悬停显示"]属性选择器
/*组合选择器*/
后代选择器
子元素选择器
兄弟选择器
邻居选择器

```



**选择器权重**

1. 下面选择器由权重由轻到重排序
2. 写在后面的选择器覆盖前面的选择器
3. 通配符选择器<标签选择器<类选择器<属性选择器<id选择器(单个选择器)
4. id名字只能出现一次，犹如身份证号



组合选择器权重

id选择器多的权重高

id选择器一样的，比类选择器

类选择器一样的，比标签选择器



测试实例

```html
<!-- h.html -->
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <link rel="stylesheet" href="c.css">
	<title></title>
  <style>
    *{
      width:100px;
      height:100px;
    }
    div{
      background-color:#001;
    }
    .box{
      background-color:#002;
    }
    [name=one]{
      background-color:#003;
    }
    #zoo{
      background-color:#004;
    }
    
    
  </style>
</head>
<body>
  <div class="box" id="zoo" name="one" style="background-color:reed;"></div>
</body>
</html>
```


```css
/*c.css*/
div{
  background-color:#005;
}
.box{
  background-color:#006;
}
[name=one]{
  background-color:#007;
}
#zoo{
  background-color:#008;
}
```

**组合选择器**

后代选择器，用空格键隔开，
子元素选择器，用>隔开，不可跨代
兄弟选择器，用~隔开，只能选择下面的兄弟(所有兄弟)
邻居选择器，用+隔开，选择下边第一个邻居
选择器分组，用,隔开，设置共同的样式



**伪选择器**

```css
a:link{未访问的链接}
a:visited{已访问的链接}
a:hover{鼠标悬停时}
a:active{鼠标点击时}

input:focus{获得焦点的input元素}
p:first-letter{}
p:first-line{}
:before 在每个节点之前插入内容，用content属性指定插入的内容
:after 在元素后面插入内容
:lang(language){}
:root
:empty
:target{链接后面带有#锚，文档内某个具体元素被链接的元素就是目标元素，target选择器选取当前活动的目标元素。}
:enabled
:disabled
:checked
:not()
::selection

:first-of-type{}
:last-of-type{}
:only-of-type{}
:only-child{}
:nth-child{n}
:nth-last-child{n}
:nth-of-type{n}
:nth-last-of-type{n}
:first-child{}
:last-child{}

```

[:after和:before的用法，可以清除浮动](https://blog.csdn.net/qq_21225505/article/details/80967680)



# 基本样式



## 背景

```css
div{
	background:color image repeat attachment position;/*复合样式*//*按上面的顺序来写*/
		background-color:red transparent;/*背景的颜色*/
  	background-position:(top+ center+ bottom)x (left+ center+ right)  % %  15px 15px;/*背景的位置左右，上下*/
  	background-size:15px 15px  % %  cover(图片比元素大) contain(元素比图片大);/*宽度，高度*/
  	background-repeat: repeat(默认) repeat-x(水平重复) repeat-y(垂直重复) no-repeat(不重复);/*背景的重复*/
  	background-orgin:padding-box(内边距框) border-box(边框盒子) content-box(内容框);/*定位起始点框*/
  	background-clip:border-box(边框有背景) padding-box(内边距有背景) content-box(内容有背景);/*背景的裁剪*/
  	background-attachment:scroll(默认 背景滚动) fixed(背景不动) inherit(继承);/*页面滚动和背景滚动*/
  	background-image:none(默认) /*背景图像*/
      url('URL') 
      linear-gradient()/*线性渐变*/
      radial-gradient()/*径向渐变*/
      repeating-linear-gradient()/*重复线性渐变*/
      repeating-radial-gradient()/*重复径向渐变*/;
}
```

- 背景的颜色包括元素的内容，内边距和边框区域，如果边框是虚线，则可以看到虚线背后的背景色
- Background-position属性要写两个值，如果设置第一个值，第二个值是center或50%
- background-size属性的百分比是以元素的大小为基准，不是以图片的大小为准，如果设置了第一个值宽度，第二个高度值是auto

**渐变**

[css3渐变](https://www.runoob.com/css3/css3-gradients.html)

```css
body{
  background-image: linear-gradient(direction, color-stop1, color-stop2, ...);
  background-image: linear-gradient(angle, color-stop1, color-stop2);
}
线性渐变，默认从上到下
方向
linear-gradient(red,blue);上红下蓝
linear-gradient(to right,red,yellow);左红右黄
linear-gradient(to bottom right,red,yellow);左上红右下黄
linear-gradient(to top right,red,yellow);左下红右上黄
linear-gradient(to bottom,red,yellow);默认值
角度
linear-gradient(90deg,red,blue);左红右黄
linear-gradient(180deg,red,blue);上红下黄
linear-gradient(-90deg,red,blue);左黄右红
透明
linear-gradient(to right,rgba(255,0,0,0),rgba(255,0,0,1));
repeating-linear-gradient(red, yellow 10%, green 20%);重复渐变

body{
  background-image: radial-gradient(shape size at position, start-color, ..., last-color);
}
径向渐变，
radial-gradient();
repeating-linear-gradient()/*重复线性渐变*/;
repeating-radial-gradient()/*重复径向渐变*/;

```









## 文本

文本是不同的字组成的一个句子



1. text-indent:注意：一般来说，可以为所有块级元素应用 text-indent，但无法将该属性应用于行内元素，图像之类的替换元素上也无法应用 text-indent 属性。不过，如果一个块级元素（比如段落）的首行中有一个图像，它会随该行的其余文本移动。
   提示：如果想把一个行内元素的第一行“缩进”，可以用左内边距或外边距创造这种效果

2. white-space:

   | 值       | 空白符 | 换行符 | 自动换行 |
   | :------- | :----- | :----- | :------- |
   | pre-line | 合并   | 保留   | 允许     |
   | normal   | 合并   | 忽略   | 允许     |
   | nowrap   | 合并   | 忽略   | 不允许   |
   | pre      | 保留   | 保留   | 不允许   |
   | pre-wrap | 保留   | 保留   | 允许     |

3. 行内元素的概念，顶线(text-top) 中线(middle) 基线(baseline) 底线(text-bottom) 行框(border) 顶端(top) 低端(bottom)



**基线对齐**

[css行高](https://www.cnblogs.com/huchong-bk/p/11504834.html)

行高line-height：一行文字的最小高度，设置行高与盒子高度一致 使文字垂直居中

文字内容font-size：

文字基线：字母x的底线

行间距：上下留着空白的地方，两行文字之间的距离

半行间距：行间距的一半

```css
p{
color:;/*文本颜色*/
direction:ltr,rtl;/*文本阅读方向，向右对齐，标点符号反了，字的顺序没变*/
line-height:normal,15px,%,数字(与当前数字相乘);/*行高*/
letter-spacing:normal,10px;/*字母间隔，可取负值*/
text-align:left,right,center;/*水平对齐，还有一个justify不常用值*/
text-decoration:none,overline,line-through,
  underline,blink;/*文本一条线修饰，可以多个值同时使用*/
	a{text-decoration: none;}
text-indent:50px,50%;/*文本缩进，可负值*/
text-transform:none,uppercase,lowercase,capitalize;/*大小写转换*/
unicode-bidi:;/**/
white-space:normal/*默认值，合并空白符成一个，忽略换行符*/
  								/*处理空白符，空格、换行和 tab 字符*/
						pre/*空白被保留，类似<pre>标签*/
						nowrap/*文本不换行*/
						pre-wrap/*空白符保留，换行符保留*/
						pre-line;/*合并空白符，换行符保留*/
word-spacing:normal,10px;/*字（单词）间隔，可取负值，单词之间间距为5px*/

vertical-align:baseline(基线对齐) middle(中部对齐，x的交叉点) text-top(与父元素字体顶端对齐) text-bottom(与父元素字体底端对齐) sub(对齐下标) super(对齐上标) top(顶端对齐) bottom(底端对齐) 15px %;/*垂直对齐，基线是字母x的底边*/
  
/*css3*/
text-shadow:15px(左右位置，可负) 15px(上下位置，可负) 15px(模糊距离) color(颜色);/*文本阴影效果*/
word-wrap:normal(默认) break-word(对长单词或URL地址内部换行);/*允许拆分长单词分割换行*/
text-overflow:clip(修剪文本) ellipsis(末尾显示省略号) 字符串(代替被修剪的文本);/*文本溢出显示方式*/
word-break:;
}

p{/*省略号三部曲*/
  overflow:hidden;
  white-space:nowrap;
  text-overflow:ellipsis;
}

text-emphasis
hanging-punctuation
punctuation-trim

text-align-last
text-justify
text-outline
text-overflow
text-shadow
text-wrap
word-break
word-wrap
```





wrap 包，缠绕，外套，围巾



## 字体

字体是单个的字

默认字体大小是16px 默认最小12px

```css
p{font:16px/1.5;}
p{
font:;
	font-style:normal,italic,oblique;/*斜体*/
	font-weight:normal/*粗细*/
							bold/*粗体*/
							bolder/*更粗的字体*/
							lighter/*更细的字体*/
							100-900/*400等同于normal，700等同于bold*/;
	font-stretch:normal;/**/
	line-height:normal;/*行高*/
	font-size:medium 16px,small 13px,large 18px,x-small 10px,/*大小*/
						x-large 24px,xx-small 9px,xx-large 32px/*7个级别，绝对大小值*/
						smaller/*比父元素更小，相对大小值*/
						larger/*比父元素更大，相对大小值*/
						16px/*固定单位大小*/
						100%/*百分比大小*/;
	font-size-adjust:none;/**/
	font-family:"行楷-简";/*字体系列，两个单词用引号括起来*/
	font-variant:normal,small-caps;/*字母异性*/
		font-variant-caps:normal;
		font-variant-alternates:normal;
		font-variant-east-asian:normal;
		font-variant-ligatures:normal;
		font-variant-numeric:normal;
		font-variant-position:normal;
		font-vatiant-settings:normal;
font-kerning:auto;/**/
font-optical-sizing:auto;/**/
font-language-override:normal;/**/
font-feature-settings:normal;/**/
```






1. italic让文字斜体，oblique使没有斜体属性的文字倾斜（通过计算得到）（不太支持）
2. Serif(有衬线)，大量文字内容区域。Sans Serif(无衬线)，标题，醒目的区域。
```css
/*引用外部字体*/
@font-face{
  font-family:userDefinedFont;
  src:url('userDefinedFont.ttf');
}
p{
  font-family:userDefinedFont;
}
<p>这里使用自定义字体</p>
```







## 链接

```css
div{
target:;
	target-name:;
	target-new:;
	target-position:;
}
```

## 列表

```css
div{
list-style:square inside url('img');
	list-style-type:disc(默认，实心圆) none(无标记) circle(空心圆) square(实心方块) decimal(数字) 其他样式见手册;/*列表前面的标记*/
	list-style-position:outside(默认) inside inherit;/*标记的位置*/
	list-style-image:none url("img.png") inherit;/*图像作为标记*/
}
```

- 始终规定一个list-style-type以防图像不可用



## 表格

```css
div{
border-collapse:;
border-spacing:;
caption-side:;
empty-cells:;
table-layout:;
}
```



## 多列

```css
div{
columns:;
  columns-count:;
  columns-fill:;
  columns-gap:;
  columns-rule:;
	  columns-rule-color:;
	  columns-rule-style:;
  	columns-rule-width:;
  columns-span:;
  columns-width:;
}
```

## 其他

元素的透明度

```css
div{
  opacity:0-1;/*元素的透明度，值可以是小数*/
}
```



网格属性

分页属性

用户外观属性

[runoob css文档内容](https://www.runoob.com/cssref/css-reference.html)



## 内容生成属性

```css
/*常与:after,:before使用，来插入生成的内容*/
content:none(设置Content,如果指定成Nothing)
        normal(设置Content,如果指定的话，正常，默认是"none"(该是nothing))
        counter(设定计数器的内容)
        attr(设置Content作为选择器的属性之一)
        string(设置Content到你指定的文本)
        open-quote(设置Content是开口引号)
        close-quote(设置Content是闭合引号)
        no-open-quote(如果指定，移除内容的开始引号)
        no-close-quote(如果指定，移除内容的闭合引号)
        url(url)(设置某种媒体(图像声音视频等内容))
        inherit;
conter-increment:none(没有计数器递增)
                 id()
                 inherit;
conter-reset:;
```

```css
示例：
p:after{
  content:"";
  display:inline-block;
  width:0px;
  height:0px;
  border:8px solid black;
  border-left:8px solid red;
  position:relative;
  top:3px;
  left:0px;
}
<p>小三角</p>
```

可以使用url插入图像（CSS3还能插入音频文件，视频文件，浏览器暂不支持）

```css
/*追加图像文件的两种方法*/
h1.ha:before{content:url(new.gif);}
h1.hb{
  background-image:url(new.gif);
  background-repeat:no-repeat;
  padding-left:28px;
}

<h1 class="ha">标题A</h1>
<h1 class="hb">标题B</h1>

/*可以在文字后面插入图片，但是不能在图片后面插入文字
  可以使用p标签包裹img标签*/
img:after{content:'Pic';}/*无效*/
<img src="j.jpg">/*<p><img></p>*/
```

```css
/*对项目追加连续的编号*/
h1{counter-increment:name;}
h1:before{content:counter(name);}
<h1>标题</h1><h1>标题</h1><h1>标题</h1>
```



# 盒子模型

**尺寸**

```css
div{
	height:100px;
	width:100px;
	max-height:100px;
	max-width:100px;
	min-height:100px;
	min-width:100px;
}

```

**display**

定位允许你定义元素框相对于正常位置应该出现的位置。

``` css
div{
display:none(不显示)/*元素生成的框类型*/
  			block(转换成块级元素)
  			inline(默认值，显示为内联元素)
			  inline-block(行内块元素)
  			list-item(作为列表显示)
				run-in(根据上线文作为块元素或内联元素显示)
			  compact(已删除)
			  marker(已删除)
			  table(块级表格 类似<table>)
			  inline-table(内联表格 类似<table>)
			  table-row-group(作为一或多个行的分组显示 类似<tbody>)
			  table-header-group(同上，类似<tbody>)
				table-footer-group(同上，类似<tbody>)
  			table-row(作为一个表格行显示 类似<tr>)
  			table-column-group(作为一个或多个列的分组来显示 类似<colgroup>)
  			table-column(作为一个单元格列显示 类似<col>)
			  table-cell(作为一个表格单元格显示 类似<td><th>)
  			table-caption(作为一个表格标题显示 类似<caption>)
        inherit(继承display属性的值);
visibility:visible(默认，可见) hidden(不可见，仍然占位) collapse(删除一行或一列表格，但是不影响表格布局);/*元素是否可见*/
```

元素生成的框类型block可以任意修改大小，inline的大小根据行高决定，但是inline-block即是行内元素，又能任意修改大小

**Flex**

2009年，W3C提出了一种新的方案—-Flex布局，可以简便、完整、响应式地实现各种页面布局。

采用Flex布局的元素，称为Flex容器（flex container），简称”容器”。它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称”项目”。

```css
/*Flex布局语法*/
.box{
  display: -webkit-flex; /* Safari,webkit内核加前缀 */
  display:flex;
  
/*容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。
  主轴的开始位置（与边框的交叉点）叫做main start，
  结束位置叫做main end；
  交叉轴的开始位置叫做cross start，结束位置叫做cross end。
  项目默认沿主轴排列。
  单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。*/
  
  /*容器的6个属性*/
  flex-flow: <flex-direction> <flex-wrap>;/*下边两个属性的简写形式*/
    flex-direction:/*容器内元素的排列方向*/
      row默认，主轴为水平方向，起点在左边
      row-reverse水平方向，起点在右边
      column垂直方向，起点在上沿
      column-reverse垂直方向，起点在下沿;
    flex-wrap:/*如果一条线排不下，如何换行*/
      nowrap默认，不换行
      wrap换行，多余的在下一行
      wrap-reverse换行，第一行在上方;
  
  justify-content:/*水平主轴的对齐方式*/
    flex-start默认左对齐
    flex-end右对齐
    center居中
    space-between两端对齐，项目之间的间隔都相等
    space-around每个项目两侧的间隔相等，项目之间的间隔比项目与边框的间隔大一倍;

  align-items:/*垂直交叉轴的对齐方式*/
    flex-start上端对齐
    flex-end下端对齐
    center中间对齐
    baseline项目中的文字基线对齐
    stretch默认，占满容器的高度;
  align-content:/*多跟水平轴线的对齐方式，如果只有一根轴线，该属性不起作用*/
    flex-start上端对齐
    flex-end下端对齐
    center居中对齐
    space-between上下对齐，水平轴之间的间隔相等
    space-around每个轴的间隔相等
    stretch默认，轴线占满容器高度;
}
/*容器里面项目的属性*/
.item{
  order:整数，默认0，数值越小，越靠前;
  
  flex:默认0 1 auto，flex-grow,flex-shrink,flex-basis的缩写;
    flex-grow:数字，默认0，放大比例;
    flex-shrink:数字，默认1，缩小比例，空间不足，首先缩小;
    flex-basis:长度35px，默认auto;
  
  align-self:/*单独定义对齐方式，可以覆盖align-items属性*/
    auto继承父元素
    flex-start
    flex-end
    center
    baseline
    stretch;
}


```

注意，设为Flex布局以后，子元素的float、clear和vertical-align属性将失效

[Flex 布局语法教程](https://www.runoob.com/w3cnote/flex-grammar.html)

flex 折曲，弯曲，收缩，弹性工作制

flow 流动，流通

reverse 颠倒，反转

direction 方向，指导，趋势，用法说明

justify 证明合法，整理版面，替...辩护，文本对齐

content 内容，目录，满意的，使满足

align 使结盟，排列，排成一行，匹配

stretch 伸展 拉紧 延长 夸大 延续 伸张 弹性 可拉伸



**Grid**

[B站Grid布局动画讲解 2分钟掌握CSS Grid布局](https://www.bilibili.com/video/BV18p411A7JB)



**盒子属性**

```css
overflow-x:;
overflow-y:;
overflow-style:;
rotation:;
rotation-point:;
```



**边框**

```css
div{
border:width style color;
	border-width:15px thin(1px) medium(3px) thick(5px);
  	border-top-width:none(无边框) hidden(表格专用) dotted(点状) dashed(虚线) solid(实线) double(双线) groove(3D凹槽) ridge(3D垄状) inset(3Dinset边框) outset(3Doutset边框);
  	border-right-width:;
  	border-bottom-width:;
  	border-left-width:;
	border-style:上 右 下 左（上 两边 下）（上下 两边）;
  	border-top-style:;
  	border-right-style:;
  	border-bottom-style:;
  	border-left-style:;
	border-color:color transparent;/*边框颜色可以是透明*/
  	border-top-color:;
  	border-right-color:;
  	border-bottom-color:;
  	border-left-color:;
  
	border-top:;
		border-top-color:;
		border-top-style:;
		border-top-width:;
	border-right:;
		border-right-color:;
		border-right-style:;
		border-right-width:;
	border-bottom:;
		border-bottom-color:;
		border-bottom-style:;
		border-bottom-width:;
	border-left:;
		border-left-color:;
		border-left-style:;
		border-left-width:;

/*css3*/
border-radius:左上右下  右上左下;
border-radius:左上  右上左下  右下;
border-radius:左上  右上  右下  左下;
border-radius:15px %;/*border圆角边框*/
	border-top-left-radius:上 左;
	border-top-right-radius:上 右;
	border-bottom-right-radius:下 右;
	border-bottom-left-radius:下 右;

border-image:;
	border-image-outset:;
	border-image-repeat:;
	border-image-slice:;
	border-image-source:;
	border-image-width:;
box-shadow:向右偏移量 向下偏移量 模糊程度 颜色;
}
```

1. 如果样式是none，那么宽度永远是0。
2. border默认width是3px。
3. border边框颜色随着文字颜色变化而变化。
4. 如果边框是透明的，那么内容的背景会延伸出来，与外边距为界。
5. 边框如果横竖交叉，一条边上的边框会变成梯形。

**轮廓**

```css
div{
outline:color style width;
	outline-color:invert;/*默认。执行颜色反转（逆向的颜色）。可使轮廓在不同的背景颜色中都是可见。*/
	outline-style:none,dotted(点状),dashed(虚线框),solid(实线框),double(双线框),groove(凹槽),ridge(凸槽),inset(凹边),outset(凸边);
	outline-width:thin,medium,thick,15px;
	
outline-offset:15px;/*css3,轮廓偏离*/
}
```

1. 如果样式是none，轮廓不会出现，宽度为0。
2. 始终在outline-color之前声明outline-style。元素只有获得轮廓以后才能改变其轮廓的颜色。
3. 轮廓和边框的区别，轮廓不占用空间，轮廓可能是非矩形。

**New Word**

- offset 抵消，补偿，偏离量

**内边距**

```css
div{
padding:上下 两边;
padding:上  两边  下;
padding:top right bottom left;/*不可取负值*/
	padding-bottom:15px,%;
	padding-left:;
	padding-right:;
	padding-top:;
}
```

1. 上下内边距的百分数相对于父元素宽度设置，而不是相对于高度。

**外边距**

```css
div{
margin:上下  两边;
margin:上  两边  下;
margin:top right bottom left;/*可取负值*/
	margin-top:15px,%;
	margin-right:;
	margin-bottom:;
	margin-left:;
}
```


1. 上下内边距的百分数相对于父元素宽度设置，而不是相对于高度。

**外边距合并**

一上一下的两个外边距，两个元素的垂直外边距相遇时，外边距会合并成两者的较大者。如果想避免这种问题，可以在之间加一个边框线

一里一外的外边距合并，两个嵌套元素的上下外边距会合并（如果外边的元素里面没有内容，里面的元素会左上角对齐，外边距选大的）（为了避免这种问题，1可以在父元素加外边距，2给父亲添加padding，3给父元素添加overflow:hidden）

```html
<head>
<style>
body{margin:0;}
.w{
  background:pink;
  width:200px;
  height:200px;
  margin-top:50px;
}
.n{
  background:skyblue;
  width:40px;
  height:40px;
  margin-top:150px;/*如果内元素的外边距大于外元素的，则以这里为准*/
}
</style>
</head>
<body>
<div class="w">a<!--如果这里没有内容，外边距会合并-->
  <div class="n">aaa</div>
</div>
</body>
```



在同一个元素内，如果内容为空，外边距也会自己合并

如果这个空内容的元素，上面还有一个外边距，也会发生合并

只有普通块元素的垂直外边距会发生合并，行内元素，浮动框或绝对定位之间的外边距不会合并。

**用户界面css3**

```css
/**/  /**/
div{
resize:/*用户可调整盒子尺寸*/
  none(不可调)
  horizontal(调宽)
  vertical(调高)
  both;
box-sizing:/*宽高容纳的范围*/
  content-box(内边距和边框另外计算，买东西另外购买) 
  border-box(包括了边框和内边距，赠送了大礼包);
}
```

# Mask

### clip-path

Clip-path可以显示一个剪切的区域，区域内部显示，外部隐藏

左上角是原点

[clip-path MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/clip-path)

[clip-path介绍 csdn](https://blog.csdn.net/weixin_44116302/article/details/98882841)

[CSS3--clip-path练习](https://www.cnblogs.com/liangdecha/p/9629150.html)

可以写三种属性

Clip-source = url

basic-shape = inset矩形 circle圆形 ellipse椭圆 polygon多边形

Geometry-box = shape-box fill-box stroke-box view-box

```css
.shape{
  clip-path:
    none;
}
```



详细参数百度“clip-path”

```css
<style>
.outer{
  width:100px;
  height: 100px;
  background:orange;
  clip-path:inset(0px 0px 0px 0px round 50px)矩形;
  clip-path:circle(30% at 150px 120px)圆形;
  clip-path:ellipse(30% 45% at 50% 50%)椭圆;
  clip-path:polygon(50% 0,100% 50%,0 100%)多边形;
  clip-path:polygon(40% 0%, 40% 20%, 100% 20%, 100% 80%, 40% 80%, 40% 100%, 0% 50%)左箭头;
  clip-path:polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%)星星;
  clip-path:polygon(20% 0%, 0% 20%, 30% 50%, 0% 80%, 20% 100%, 50% 70%, 80% 100%, 100% 80%, 70% 50%, 100% 20%, 80% 0%, 50% 30%)叉号×;
  clip-path:polygon(
    0% 0%, 
    0% 100%, 
    25% 100%, 
    25% 25%, 
    75% 25%, 
    75% 75%, 
    25% 75%, 
    25% 100%, 
    100% 100%, 
    100% 0%)空心矩形;
}

</style>

<div class="outer"></div>

```

clip-path 动画虽然美好，但是存在一定的局限性，那就是进行过渡的两个状态，坐标顶点的数量必须一致。









# 定位

css有三种定位方式：普通流，浮动和绝对定位

普通流：从上至下一个接一个的排列，框之间的垂直距离是由框的垂直外边距计算出来的。

## 定位


```css
/*绝对定位：*/
position:static(普通流，默认值)
         absolute(绝对定位，相对于static以外的第一个父元素)
         relative(相对定位，保留原来的空间)
         fixed(固定定位，相对浏览器窗口);
         sticky(相对定位，超出则是固定定位)/*元素的定位类型*/
top:auto % 15px;
right:;
bottom:;
left:;
overflow:visible(默认，内容溢出呈现在框外) 
		 hidden(溢出部分被隐藏) 
		 scroll(溢出部分会显示滚动条) 
		 auto(溢出有滚动条);/*内容溢出时*/
clip:rect(top,right,bottom,left) auto(不裁剪，默认值);/*裁剪绝对定位的元素*/
z-index:auto(默认) (写一个具体的数字);/*图层前后顺序*/

cursor:;/*鼠标形状，共17种，见手册*/
}
```

- 相对定位仍保留原来的位置， 绝对定位的盒模型全部消失

相对决定定位的元素，层级提高，会覆盖普通流元素和浮动元素

- 绝对定位之后变成块级元素
- 绝对定位的元素的位置相对于最近的已定位祖先元素，父元素被定位才被参考，父元素浮动的就不行
- 绝对定位元素时，尽量使用left和top属性定位。
- 绝对定位时用right和bottom是相对于浏览器窗口定位的。底部是参照浏览器窗口而不是整个很长的网页。浏览器窗口变化时首屏也会变化。

fixed的定位，如果设置top left永远是相对于浏览器定位，不受父元素影响，不设置top left则会在原来的地方定位

cursor 光标，游标，指针

flex 折曲，弯曲，收缩，弹性

fixed 确定的 固定的

fix 修理 固定 确定 安排 困境

## 浮动

当一个元素浮动时，盒子模型脱离普通流，下面的元素将向上，浮动的元素覆盖底下的元素

[以后再看吧](https://www.w3school.com.cn/css/css_positioning_floating.asp)

当元素浮动起来时，不会叠加和碰撞。浮动的元素会把普通流元素覆盖起来，clear样式会取消这样的覆盖效果。

```css
/*浮动定位*/
float:none(默认，不浮动) left(向左浮动) right(向右浮动);/*浮动*/
clear:none(默认) left(左侧不允许浮动) right(右侧不允许浮动) both(两边不允许浮动);/*清除浮动*/
```



```css
/*浮动边框塌陷，用overflow:hidden解决问题，具体尚原因不清楚，还可以在最后设置一个空元素并清除浮动*/
<div style="border:9px solid red; width:500px; overflow: hidden;">
	<div style="background-color: orange; width: 100px; height: 100px; float: left;"></div>
	<div style="background-color: yellow; width: 100px; height: 100px; float: left;"></div>
	<div style="background-color: green;  width: 100px; height: 100px; float: left;"></div>
	<div style="background-color: cyan;   width: 100px; height: 100px; float: left;"></div>
	<div style="background-color: purple; width: 100px; height: 100px; float: left;"></div>
</div>
<div style="border:9px solid red; width:500px;">
	<div style="background-color: orange; width: 100px; height: 100px; float: left;"></div>
	<div style="background-color: yellow; width: 100px; height: 100px; float: left;"></div>
	<div style="background-color: green;  width: 100px; height: 100px; float: left;"></div>
	<div style="background-color: cyan;   width: 100px; height: 100px; float: left;"></div>
	<div style="background-color: purple; width: 100px; height: 100px; float: left;"></div>
	<div style="clear: left;"></div>
</div>
```





**内联元素行内元素和块级元素**

1. 行内元素只能包含数据和其他行内元素；块级元素可以包含行内元素和其他块级元素。块级元素占据一行，行内元素只包含几个字。块级元素创建比行内元素更”大型“的结构。块级元素会新起一行，行内元素会跟在同一行的后面。
2. 内联元素在一行中可以使用内边距，边框和外边距调整间距，但是不影响内联元素的高度，设置行高可以增加内联元素的高度。
3. 由一行形成的水平框称为行框(Line Box)。



# 变换

## 2D转换

通过 CSS3 转换，我们能够对元素进行移动、缩放、转动、拉长或拉伸

转换是使元素改变形状、尺寸和位置的一种效果。



```css
div{
transform:
  translate(X,Y)(left,top)/*坐标平移，可负值*/
  	translateX(X)
  	translateY(Y)
  rotate(9deg)/*中心旋转，可负值*/
  scale(X,Y)/*放大倍数*/
  	scaleX(X)
  	scaleY(Y)
  skew(X,Y)/*元素倾斜的角度*/
  	skewX(X)
  	skewY(Y)
  matrix(nx6)/*6个参数，2D转换组合方法*/
  none/*不转换*/;
}

transform-origin
transform-style
perspective
perspective-origin
backface-visibility
```

判断坐标平移时，盯着左上角顶点，先确定X轴，再确定Y轴

旋转中心为元素的中心点

元素的放大倍数，先确定宽度倍数，再确定高度倍数，中心点位置不变

坐标轴不发生倾斜，先确定竖线角度，再确定横线角度

## 3D转换

3D转换是在2D转换上的扩充

css转换仍然是一种静态的变换，搭配过渡才能动起来，但是转换提供了一个具体过程

```css
div{
transform:
  translate3d(X,Y,Z)/*空间坐标移动，可负值*/
  	translateX(X)
  	translateY(Y)
  	translateZ(Z)
  scale3d(X,Y,Z)/*缩放倍数*/
  	scaleX(X)
  	scaleY(Y)
  	scaleZ(Z)
  rotate3d(X,Y,Z,deg)/*中心旋转，可负值*/
  	rotateX(X)/*沿竖轴旋转*/
  	rotateY(Y)/*沿横轴旋转*/
  	rotateZ(Z)/*2D旋转*/
  perspective()/*3D透视图，使用方法以后再学*/
  matrix3d(nx16)/*组合方法，16个参数*/
	none;/*不转换*/
}
```



## css3过渡

过渡必须指明效果指定的CSS属性，时间长

```css
transition:width 1s linear 2s;
	transition-property:width; --none --all --property
	transition-duration:1s; --time
	transition-timing-function:linear; --ease --ease-in --ease-out --ease-in-out --cubic-bezier(n,n,n,n)
	transition-delay:2s;

<!DOCTYPE html>
<html>
<head>
<style> 
div{
width:100px;
height:100px;
background:yellow;
transition-property:width 1s linear 2s;
}
div:hover{
width:200px;
}
</style>
</head>
<body>
	<div></div>
</body>
</html>
```

1. 部分没有被写的属性变换将在一瞬间完成。
2. timing-function最常用的是linear

**New Word**

- transition 过渡转变
- property 属性 ，财产
- duration 持续，持续的时长
- timing 定时，调速，时间选择
- function 功能，函数
- delay 延期 推迟 耽搁
- ease 容易，舒适，减轻，缓解

## css3动画

动画将一套CSS样式逐渐变化为另一套样式

```css
div{
  animation:name duration timing-function delay iteration-count direction;/*动画的6个属性，必写名字和时间*/
  	animation-name:none name;/*关键帧的名字*/
  	animation-duration:2s;/*时间长度*/
  	animation-timing-function:linear(线性的)ease(默认，先慢后快)ease-in(先慢)ease-out(后慢)ease-in-out(前后都慢)cubic-bezier(n,n,n,n);/*速度曲线，贝塞尔曲线*/
  	animation-delay:2s;/*动画延迟一段时间再开始*/
  	animation-iteration-count:infinite(无限次) 3;/*动画播放的次数*/
  	animation-direction:normal(默认不反向)alternate;/*轮流反向播放动画*/
  
	animation-play-state:paused(暂停)running(运行);/*动画运行还是暂停*/
	animation-fill-mode:none forwards backwards both;/*动画在播放之前或之后，动画的状态，翻手册*/
  	
  @keyframes name/*定义动画 关键帧*/
  {
    from{css:;}/*0%*/
    to{css:;}/*100%*/
    或者是
    0%{top:0px;}
		25%{top:200px;}
		50%{top:100px;}
		75%{top:200px;}
		100%{top:0px;}
  }
  
}
```

css函数

```
attr()
calc()
cubic-bezier()
hsl()
hsla()
linear-gradient()
radial-gradient()
repeating-linear-gradient()
repeating-radial-gradient()
rgb()
rgba()
var()
```







# 其他

## css样式初始化

**浏览器原始样式**

- body元素外边距为8px
- h1~h6标题，p有外边距
- h1~h6标题自动加粗

**css reset类库样式重置**

```css
body,p,h1,h2,h3,h4,h5,h6,ul,ol,dl,dt,dd{
  margin:0;
  padding:0;
}
ul,ol{
  list-style:none;
}
a{
  color:#000;
  text-decoration:none;
}
```

- normalize.css



## 浏览器前缀

[浏览器前缀MDN](https://developer.mozilla.org/zh-CN/docs/Glossary/Vendor_Prefix)

[浏览器前缀](https://www.cnblogs.com/cwzqianduan/p/8880021.html)

```html
-webkit- 谷歌浏览器，Safari浏览器
-ms- IE浏览器
-moz- 火狐浏览器
-o- 欧朋浏览器
```





```
transparent 透明的，显然的，坦率地，易懂的
decoration 装饰，装潢，修饰（下划线，上划线，中划线）
outline 轮廓，大纲，框
```



