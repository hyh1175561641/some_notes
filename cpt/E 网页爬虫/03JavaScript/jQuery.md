
H5+JS+CSS3实现七夕言情 https://www.imooc.com/video/8983



# JQuery


serialize()//把表单数据序列化成字符串

https://jquery.com
https://api.jquery.com
http://jquery.cuishifeng.cn
https://www.runoob.com/jquery/jquery-tutorial.html

jQuery 是一个 JavaScript 库。jQuery 极大地简化了JavaScript编程。目前jQuery兼容于所有主流浏览器, 包括Internet Explorer 6!
可以通过多种方法在网页中添加 jQuery。 您可以使用以下方法：
jquery.com http://jquery.com/download/
从 CDN 中载入 jQuery, 如从 Google 中加载 jQuery
官网下载方法 https://jquery.com/download/
两个版本，一个精简压缩，一个未压缩
Production version - 用于实际的网站中，已被精简和压缩。
Development version - 用于测试和开发（未压缩，是可读的代码）



baidu: Sizzle选择器引擎原理分析

配置

cdnjs https://cdnjs.com



1.12.4是常用版本？？？有一种说法
```html



<!-- 下载 -->



<!-- 本地引用 -->
<script src="jquery-1.10.2.min.js"></script>
<!-- CDN（内容分发网络） -->
<script src="https://code.jquery.com/jquery-3.4.1.js"></script>
<!-- 百度CDN -->
<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>

```

使用 Staticfile CDN、百度、又拍云、新浪、谷歌或微软的 jQuery，有一个很大的优势：许多用户在访问其他站点时，已经从百度、又拍云、新浪、谷歌或微软加载过 jQuery。所以结果是，当他们访问您的站点时，会从缓存中加载 jQuery，这样可以减少加载时间。同时，大多数 CDN 都可以确保当用户向其请求文件时，会从离用户最近的服务器上返回响应，这样也可以提高加载速度。





在浏览器输入$.fn.jquery查看版本

基础操作

jQuery库包含以下功能：

HTML 元素选取
HTML 元素操作
HTML DOM 遍历和修改
HTML 事件函数
CSS 操作
JavaScript 特效和动画
AJAX
Utilities

选择器

jQuery 选择器基于元素的 id、类、类型、属性、属性值等"查找"（或选择）HTML 元素。 它基于已经存在的 CSS 选择器

```javascript
//$("p").css() // 这里的修改css，暗藏了隐式迭代
$("*")通配符选择器
$(this)当前HTML元素
$("p")标签选择器
$("#id")id选择器
$(".class")类选择器
$("[href]")属性选择器,具体使用看手册
$(":buttom")选取所有 type="button"的<input>元素和<button>元素
$("div,p,.title")并集选择器，选取所有div p 和.title的元素
还有后代，子>，相邻元素+，兄弟~选择器。一次选好几个

$("body,p,ul,li").css({ // 可以选中多个元素写多个样式
    "margin":"0px",
    "padding":"0px"
})

$("p").css("color")//可以获取到p标签的颜色样式

// 添加删除切换判断类名
$("p").addClass("pBorder");//添加一个类
$("p").removeClass("pBorder");//删除一个类
$("p").toggleClass("pBorder");//有无切换
$("p").hasClass("pBorder");//判断有无此类

// 修改移除属性值
$("img").attr("src")//获取属性值，如果多个仅收到一个
$("img").attr("src","./img/p.png")//设置属性值，设置全部
$("img").removeAttr("width");//移除属性

//获取内容
$("p").html()//获取的是第一个元素的html内容
$("p").html("<u>i</u>")//修改标签内的HTML值
$("p").text()//获取的是所有元素的文本
$("p").text("<u>i</u>")//修改文本，HTML会原封写出来
$("input").val()//获取元素的值，只是第一个元素的值
$("input").val("value");//修改value的值
```



```js
// 工厂函数$(html)用来创建或获取节点
$("p1").css(); //$(selector)选择器
$(element)//把原生js的DOM节点转化成jQuery节点
var newNode = $("<li>A<li>");//$(html)创建节点
```



```js
//创建一个新节点
var div1 = document.createElement("div");//原生js创建新节点
var newNode = $("<div></div>");//新的div节点
newNode.css({"height":"100px","width":"100px","background-color":"blue"});
$("#divv").append(newNode);//把新结点添加到id=divv中
newNode.appendTo("#divv");//和上面的效果一样，添加新节点到divv中

$("#divv").prepend(newNode);//把新节点放在最前面
newNode.prependTo("#divv");//同上

$("#divv").after(newNode);//插入到同辈元素之后
newNode.insertAfter("#divv");//同上
$("#divv").before(newNode);//插入到同辈元素之前
newNode.insertBefore("#divv");//同上

$("#divv").replaceWith($newNode);//替换节点
newNode.replaceAll("#divv");//被替换节点

```



```js
//删除节点
var delNode = document.getElementById("first");
delNode.parentNode.removeChild(delNode);
//替换节点
var oldNode = document.getElementById("second");
var newNode = document.createElement("img");
newNode.setAttribute("src","image/f03.jpg");
oldNode.parentNode.replaceChild(newNode,oldNode);

//
var imgNew = $("<img src='img/src.jpg'>");
var imgOld = $("#img1");
imgOld.replaceAll(imgNew);


```



```js
//复制节点
var div1 = document.getElementById("div1");
var div2 = div1.cloneNode(true);//是不是要复制标签里面的内容
var body1 = document.getElementsByTagName("body")[0];
body.appendChild(div2);

//jQuery的用法
$(selector).clone(true/false);
$(this).clone(false)//不复制事件处理
```



```js
var img1 = document.getElementById("img1");
div1.removeChild(img1);
$("img").remove();//移除元素
$("div").empty();//清空元素


```



```js
// 过滤选择器
$("li:eq(1)").css
:eq(index) 选择等于index的元素
:gt(index) 选择大于index的元素
:lt(index) 选择小于index的元素
:header 选择所有标题元素
:focus 选择当前获取焦点的元素

<input type="text">
// script:
$("input").focus();
$(":focus").css("background-color","yellow");
或者是
<input type="text" onclick="test()">
test=function(){$(":focus").css("background-color","yellow")};
```



```js
# 子元素
children() 获取所有子元素

# 遍历同辈元素
next() 后边的同辈
prev() 前边的同辈
sibings() 所有的同辈元素，前后都获取

# 遍历前辈元素
parent() 获取元素的父级元素
parents() 元素的祖先元素

# 其他遍历元素方法
$("li").each(function(){//each函数
	var eachli = $(this).append('(li)')
})
.end 结束当前链条中的最近的筛选操作，将匹配元素还原为之前的状态
$("#li3").first().css("color","red");
$("#li3").last().css("color","blue");
//将("li3")选择到的元素还原成li3
$("#li3").first().css("color","red").end().last().css("color","blue");
// 链式编程可以一直调用点运算符函数
```





## 事件

页面对不同访问者的响应叫做事件。

```javascript
//鼠标事件
click()
dblclick()
mouseover()//指针移过
mouseout()//指针移出
mouseenter()//指针进入
mouseleave()//指针离开
hover()
//mouseover和mouseenter都是鼠标在元素上有事件
//mouseover鼠标经过该元素及其子元素时都触发该事件,事件触发的比较多,搭配mouseout
//mouseenter鼠标经过该元素时触发，搭配mouseleave

//window事件

//键盘事件
keypress() //输入有效字符时才会触发
keydown() //键盘按下时触发，不放手会一直触发
keyup() //键盘抬起时触发
$(document).keydown(function (e) {
    if(e.keyCode == '13'){//13代表回车键
    console.log("回车键摁下")}
})

//表单事件
submit()
change()
focus()
blur()
onblue()

//文档事件
load()
resize()
scroll()
unload()

```



## 效果

```javascript
//基本


//滑动

//淡入淡出

//自定义

//设置
```



## AJAX

```js
//JQuery的加载执行不必等待页面全部完成才加载，而原生js需要等待图片视频音频加载好才执行，原生window.onload多写会被覆盖，jQuery能编写多个

window.onload = function(){/*js版本，加载完才执行*/}
$(document).ready(function (){
	//当页面dom元素加载完成之后，才执行js代码;
})
$(function (){
    //简写形式，当页面dom元素加载完成之后，才执行js代码;
})
```



同步就是按照次序依次进行，异步就是多件事情同时进行，ajax默认一般是异步的

```js
//Jquery-ajax
.ajax()
$(function () {
    $.ajax({
        type: "post",
        url: "test.txt",//获取数据的地址/接口地址
        data: {id:1,name:'zzz'}//传输给服务器的键值对
        dataType:"text/json",//json类型必须与服务器返回的类型一致，否则执行error函数
        timeout:2000,
        success: function (data) {
            $('#p1').append(data);
            console.log(data);
        },
        error: function (data1,data2,data3) {
            console.log(data1,data2,data3);
            //data1.status 状态码
        },
        headers:{c:300,d:400}
    })
    var r = $.ajax({
        url:'text.txt',
        async:false//如果后面的的命令依赖于这个数据，那就设置成同步来使这行代码执行完之后再往后执行
    });
    console.log(r);//这里返回一个ajax对象
    console.log(r.responseText);//未定义，这里是异步执行，上面还没执行这里就开始执行了
})

//默认Get请求，默认异步，error处理没有
$("#p1").load("text.txt",{id:1,name:'zhang'},function(){$(this).css("color","red")});//把文件内容加载到p1上

//get请求数据
//$.get(URL,callback);
//$.post(URL,data,callback);
$.get/.post("text.txt",function(data){console.log(data);})

$.get("http://localhost:8080/server",
      {a:100,b:200},
      function(data){console.log(data);},
      'json')

$.post("http://localhost:8080/server",
       {a:100,b:200},
       function(data){console.log(data);},
       'json')

```



```js
//两个对象合并
var user = {id:1,name:'zhang'};
var address = {add:"beijing"};
$.extend(user,address)//关于对象把第二个加到第一个里面，第二个不变
//如果有重复的键值对，则会覆盖，舍弃第一个选择第二个

var user = [1,2,3];//数组合并会这样
var address = [4];//[4,2,3]
$.extend(a,b,c);//多个对象的合并，b,c不变，a拓展了
$.extend(true,a,b,c);//深度合并，保证对象里的对象也被合并而不是简单的替换

```



```js
//Jquery方法拓展，自定义方法
$.fn.extend({
    set: function(){},
    get: function(){}
})
$("input").set();
$("input").get();


```



























# Axios

https://axios-http.com/
https://github.com/axios/axios
Axios是一个基于promise网络请求库,作用于node.js和浏览器中.它是isomorphic的(即同一套代码可以运行在浏览器和node.js中).在服务端它使用原生node.js http模块,而在客户端(浏览端)则使用XMLHttpRequests

```javascript
//还能使用npm，bower，yarn安装
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"><script>
<script src="https://unpkg.com/axios/dist/axios.min.js"><script>
```

```javascript
axios.get(url).then().catch()

axios.get(address?key=value&k2=v2)
.then(function(response){},function(err){})
.catch()

axios.post(address,params:{key:value&k2:v2},headers:{token:'123'})
.then(function(response){},function(err){})
.catch()


```



```js
var that = this;//在axios中this代表着axios函数而不是vue函数，在axios中先把this赋值给that，然后在axios中才能使用你想要的this

document.querySelector(".get").onclick = function(){}
// get请求
axios.get("http://autumnfish.cn/api/joke/list?num=6",{
    params:{id:100},headers:{name:'name',age:20}
          }).then(function (response){console.log(response);},
		  function(err){console.log(err);})

// post请求
axios.post("https://autumnfish.cn/api/user/reg",{username:""},
           { params:{},headers:{},data:{} 
           }).then(function(response){console.log(response);})
```



```javascript
axios({
    method:'POST',
    url:'http:www.a.com',
    params:{vip:10,level:30},
    headers:{a:100,b:200},
    data:{user:'admin',pass:'admin'}
}).then(response=>{
    console.log(response);
    console.log(response.status);
    console.log(response.statusText);
    console.log(response.header);
    console.log(response.data);
})


```



```
Axios响应组成
data:{},服务端返回的数据
status:200,状态码
statusText: 'OK',状态码信息
headers:{},响应头
config:{} axios请求配置
request:{}请求

```


https://www.jianshu.com/p/b0694dd72343

https://autumnfish.cn/api/joke



保罗格雷厄姆巴黎艺术学院学画画，华尔街投资顾问，大学是计算机专业，1980

比尔盖茨学法律的，小红书，28岁退休





