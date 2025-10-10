






# Angular

https://angular.dev/







# Bootstrap

https://getbootstrap.com


Bootstrap是最受欢迎的HTML、CSS、JS框架，用于开发响应式布局、移动设备优先的WEB项目。特别适合那种没有设计师的团队，甚至没有前端的团队，可以快速出一个网页

```html
<!--使用X-UA-Compatible来设置IE浏览器兼容模式 最新的渲染模式-->
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<!--BootStrap移动设备优先
	viewpost表示用户是否可以缩放页面
	width和height指定视区的逻辑宽度和高度，他们的值是00px或是一个特殊的标记符号
	width指令值为device-width指示视区宽度应为设备的屏幕宽度
	height指令值为device-height指示视区高度应为设备的屏幕高度
	initial-scale指令用于设置web页面的初始缩放比例
	initial-scale=1则将显示未经缩放的web文档
-->
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0">

<link rel="stylesheet" type="text/css" href="css/bootstrap.min.css">
<!--先引入jquery，再引入bootstrap-->
<script type="text/javascript" src="jquery-1.12.4.js"></script>
<script type="text/javascript" src="js/bootstrap.min.js"></script>
bootstrap3版本要配合jQuery1.12.4版本使用，这样更稳定

CDN:

```

```
# 初始化
box-sizing: border-box;//怪异盒模型
```



**栅格系统**

栅格系统是一行有12列，当浏览器窗口收缩时，列会跟着折叠

```html
container容器 //三个阈值四个状态
阈值xs 768 sm 992 md 1200 lg
width:xsauto sm750  md970   lg1170

row行
col-xs sm md lg-x 列组合，列还能嵌套
//列偏移按照顺序往后移动，排在后面的元素一并向后移
col-md-offset-x 列偏移
//列排序是后面覆盖前面的，列排序只浮动当前元素，后面的元素不会变，但是写在后面的元素会覆盖写在前面的元素
//一个是左移3格一个是右移3格，但是写在后面的标签会覆盖前面的标签
col-md-9 col-md-push-3右移
col-md-3 col-md-pull-3左移


当使用列嵌套时,里面放一个div=row,里面仍然是12栅格

container-fluid流体容器
流体容器的宽度是auto

brown rosybrown navajowhite knaki palegreen teal darkblue blueviolet bisque mediumslateblue burlywood indianred darkturquoise
lightgoldenrodyyellow fuchsia azure burlywood darkcyan goldenrod
```

width auto 和100%的区别是如果加padding，auto不会撑大页面，100%的页面会永远比窗口大一点

```html
#文档结构
<h1>标题<small>小标题</small></h1>
<span class="h1">标题<small>小标题</small></span>
b/strong加粗 i/em斜体 small小号
<p class="lead强调 text-center left right juesify">这是一个段落</p>

<h1 class="text-muted浅灰 primary蓝色 success浅绿色 info浅蓝色 warning黄色 danger褐色"></h1>
<span class="badge">小气泡
<span class="glyphicon glyphicon-ok/heart">小图标
```



```html
# 语言代码
<kbd>Ctrl</kbd><kbd>Shift</kbd>
<code>一行代码</code>
<pre class="pre-scrollable">
这里写多行代码,大小于号用特殊符号
#include &lt;stdio.h&gt;
int main(){
    printf("Hello World!");
    return 0;
}
</pre>
```



```html
# 列表组件
ul class=list-unstyled去点 list-inline内联列表
li class=list-group-item

dl dl-horizontal水平定义列表
dt dt过长会添加省略号，最大宽度60px
dd


ul list-group列表组
li list-group-item列表组项 list-group-item-success绿色 warning黄色 danger红色 info天蓝色
```



```
# 表格
table class=table基础样式 table-bordered添加边框 table-striped隔行换色 table-hover鼠标悬停换色 table-condensed小号紧凑
tr/td/th class= active浅灰 success浅绿 info浅蓝 warning浅黄 danger浅红 一个小方块的颜色样式会覆盖整个行的颜色样式
```



```html
# 表单
form class=form-inline内联表单 form-horizontal横向表单
<!--内联表单是横向的一排，横向表单是常规的登录那种表单-->
表单组div把input-text和span标签包起来还能写 class=form-group表单组  has-success绿 warning黄 error红输入框颜色
<form active="#" class="form-inline/form-horizontal" roal="form">
    <div class="form-group">
        <label for="name" class="control-label col-md-2">姓名</label>
        <div class="col-md-8">
            <input type="text" id="name" class="form-control">
        </div>
    </div>
</form>


input-text class=form-control写这个才有样式 input-sm lg 输入框大小

input-button或<button> class=btn写了这个才有样式 没有样式是灰色btn-default白色黑字 info青色 success绿色 warning黄色 danger红色 primary蓝色 link白色蓝字 btn-lg sm xs是按钮大小
//class只是样式上禁用了按钮，并不是真正的禁用了按钮，还能点击
<button class="disabled">禁用按钮</button>
<button class="disabled" onclick="alert('hello')">禁用按钮但是还能点击</button>
//真正的禁用了按钮
<button disabled="disabled">禁用按钮</button>
普通标签也能做按钮
    <a href="#" class="btn btn-success"></a>
    <span class="btn btn-info"></span>
    <div class="btn btn-warning"></div>    
    
#输入框组 input-group
div class:input-group
input class:form-control
span input-group-addon
如果想写一个按钮span input-group-btn >button

select class=form-control multiple=multiple多选
	option class=active
textarea class=form-control
	
input-checkbox 
<div class="checkbox">水平显示
    <label><input type="checkbox">游戏</label>
    <label><input type="checkbox">游戏</label></div>
垂直显示
<div><label class="checkbox-inline"><input type="checkbox">跳舞</label>
	<label class="checkbox-inline"><input type="checkbox">唱歌</label></div>

input-radio
    水平显示
<div><label class="radio"><input type="radio">男</label>
    <label class="radio"><input type="radio">女</label></div>
    垂直显示
<div><label class="radio-inline"><input type="radio">男</label>
    <label class="radio-inline"><input type="radio">女</label></div>
```



```
# 图片
img class=img-responsive响应式 img-rounded圆角 img-circle圆形 img-thumbnail缩略图

# 图文混合
div: thumbnail > img
div: caption > h1&p
```



```
# 面板
div class=panel panel-success
  div class panel-heading  这里放标题
  div class panel-body  这里放内容
```



```html
# button下拉菜单列表
div class:dropdown/dropup open默认打开
button class:"btn btn-danger dropdown-toggle" data-toggle="dropdown"
span class:caret倒三角
ul class:dropdown-menu
li divider横线 dropdown-header下拉菜单头 active蓝色的 disabled禁用

#双button合并下拉列表
<div class="dropdown btn-group">按钮组
<button class="btn btn-danger">选择</button>
<button class="btn btn-danger dropdown-toggle" data-toggle="dropdown"><span class="caret"></span></button>
</div>

# 导航选项下拉列表
<li class="dropdown">
    <a href="#" data-toggle="dropdown">关于我们
        <span class="caret"></span></a>
    <ul class="dropdown-menu">
        <li><a href="#">下拉项一</a></li>
        <li><a href="#">下拉项二</a></li>
        <li><a href="#">下拉项三</a></li>
    </ul>
</li>
```



```html
# 导航列表,li中必须有a标签

# 选项卡导航列表
ul class:nav基础 nav-tabs选项卡导航 nav-justified自适应导航 nav-pills胶囊式选项卡 nav-stacked堆栈 breadcrumb面包屑式
li class:active 被选中

# 选页数列表
ul class:pagination页码导航 pager翻页导航
li class:active活跃的 disabled禁用 previous左边 next右边
```



```
# 导航条
nav class: navbar导航条基础样式 navbar-default/inverse白色黑色 navbar-fixed-top导航条置顶bottom置底
div-class:navbar-header a-class:navbar-brand
div-class:
ul class="nav navbar-nav"
li 导航条中的导航项和选项卡导航列表差不多,其中导航条中的元素:按钮navbar-btn,文本navbar-text,链接navbar-link
li-a navbar-link 
li-button class:btn navbar-btn
span class:navbar-text 导航条中的文本有专属样式
div把form包起来navbar-right
form class:navbar-form导航条表单样式 navbar-right右侧
<form class="navbar-form navbar-right" role="search">
    <input type="text" class="form-control">
    <input type="button" class="btn btn-primary">
</form>


# 响应式导航条需要添加一些东西
在导航头中添加横线按钮，展示导航栏
div navbar-header > <button class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
    <span class="icon-bar"></span></button>
在导航列表中添加collapse
<div class="collapse navbar-collapse navbar-left">
	<ul class="nav navbar-nav">
    	<li></li></ul></div>
```

collapse 倒闭，虚脱，破产

toggle 切换

role 角色

thumbnail 缩略图

dropdown 下拉列表

brand 牌子，烙印

```html
# 选项卡
选项卡导航
ul class="nav nav-pills"
li>a data-toggle="tab" href="#锚链接"
选项卡内容
div class="tab-content"
div  id="配合href的锚链接" class="tab-pane专属样式 fade淡入淡出效果 in active默认展示选项卡（两个单词配合使用）"

方法.tab("show")
事件show.bs.tab shown.bs.tab

为什么这样写？
$( function(){
	$("li>a").on({
		click: function(){$(this).tab("show")},
		"show.bs.tab":function(){console.log();}
		"shown.bs.tab":function(){console.log();}
	})
})
```



```html
# 模态框对话框

<button class="btn btn-primary btn-lg" data-toggle="modal" data-target="#myModal">展示模态框</button>

<div class="modal fade" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <button></button>
                
            </div>
             
        </div>
        
    </div>
</div>

```



```html
# 轮播图
外框div class:carousel slide data-ride:carousel自动轮播
里面三部分
图片div class:carousel-inner div:item img-src
图片-文字信息 div class:carousel-caption
索引点 ol class:carousel-indicators li:data-target:外框锚点 data-slide-to:索引值
箭头 a href:外框锚点 class:carousel-control left/right左右 data-slide="prev"

<div class="carousel slide" id="carouselTest">
 <div class="carousel-inner">
  <div class="item (active)">
   <img src="path"></div>
  <ol class="carousel-indicators">
   <li data-target="#carouselTest" data-slide-to="0"></li></ol>
  <a href="#carouselTest" class="carousel-control left/right" data-slide="prev/next">
   <span class="glyphicon glyphicon-chevron-left/right"></span></a>
 </div>
</div>

```

slide 幻灯片 滑动 滑道

indicators 指标



# Font Awesome

官网 https://fontawesome.com
Font Awesome 中文网 http://www.fontawesome.com.cn
Font Awesome 中文 https://fontawesome.dashgame.com
Font Awesome runoob https://www.runoob.com/font-awesome/fontawesome-tutorial.html

**CDN**

```css
<link rel="stylesheet" href="https://cdn.staticfile.org/font-awesome/4.7.0/css/font-awesome.css">
```

**本地文件**

```css
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<link rel="stylesheet" href="https://cdn.staticfile.org/font-awesome/4.7.0/css/font-awesome.css">
</head>
<body>

<i class="fa fa-car">汽车</i>
<i class="fa fa-car" style="font-size:48px;">指定字体大小</i>
<i class="fa fa-car" style="font-size:60px;color:red;">指定颜色</i>
<hr>大图标
<i class="fa fa-car fa-lg">汽车</i>
<i class="fa fa-car fa-2x"></i>
<i class="fa fa-car fa-3x"></i>
<i class="fa fa-car fa-4x"></i>
<i class="fa fa-car fa-5x"></i>
<hr>列表图标
<ul class="fa-ul">
  <li><i class="fa-li fa fa-check-square"></i>List icons</li>
  <li><i class="fa-li fa fa-spinner fa-spin"></i>List icons</li>
  <li><i class="fa-li fa fa-square"></i>List icons</li>
</ul>
<hr>边界和被拉的图标
<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>
菜鸟教程 -- 学的不仅是技术，更是梦想！！！<br>
菜鸟教程 -- 学的不仅是技术，更是梦想！！！<br>
菜鸟教程 -- 学的不仅是技术，更是梦想！！！<br>
菜鸟教程 -- 学的不仅是技术，更是梦想！！！
<hr>动态图标
<i class="fa fa-spinner fa-spin"></i>
<i class="fa fa-circle-o-notch fa-spin"></i>
<i class="fa fa-refresh fa-spin"></i>
<i class="fa fa-cog fa-spin"></i>
<i class="fa fa-spinner fa-pulse"></i>
<hr>旋转和翻转图标
<i class="fa fa-shield"></i>
<i class="fa fa-shield fa-rotate-90"></i>
<i class="fa fa-shield fa-rotate-180"></i>
<i class="fa fa-shield fa-rotate-270"></i>
<i class="fa fa-shield fa-flip-horizontal"></i>
<i class="fa fa-shield fa-flip-vertical"></i>
<hr>堆叠的图标
<span class="fa-stack fa-lg">
  <i class="fa fa-circle-thin fa-stack-2x"></i>
  <i class="fa fa-twitter fa-stack-1x"></i>
</span>
fa-twitter on fa-circle-thin<br>
 
<span class="fa-stack fa-lg">
  <i class="fa fa-circle fa-stack-2x"></i>
  <i class="fa fa-twitter fa-stack-1x fa-inverse"></i>
</span>
fa-twitter (inverse) on fa-circle<br>
 
<span class="fa-stack fa-lg">
  <i class="fa fa-camera fa-stack-1x"></i>
  <i class="fa fa-ban fa-stack-2x text-danger" style="color:red;"></i>
</span>
fa-ban on fa-camera
<hr>固定宽度图标
<div class="list-group">
  <a href="#" class="list-group-item"><i class="fa fa-home fa-fw"></i> Home</a>
  <a href="#" class="list-group-item"><i class="fa fa-book fa-fw"></i> Library</a>
  <a href="#" class="list-group-item"><i class="fa fa-pencil fa-fw"></i> Applications</a>
  <a href="#" class="list-group-item"><i class="fa fa-cog fa-fw"></i> Settings</a>
</div>
</body>
</html>
```





