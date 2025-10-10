



# Font Family 字体族
如何选择字体(font-family) https://blog.csdn.net/SmCai/article/details/86304808

Font&Typeface：font是指某套具有同样样式、尺寸的字形；typeface则是一或多个font在一或多个尺寸的集合。
字体样式：有衬线(Serif)，大量文字内容区域。无衬线(Sans Serif)，标题，醒目的区域。等宽字体(Monospace)，显示代码。
字形：常规体(regular)，细体(light)，粗体(bold)，斜体(italic)，黑体(black)
字体类型：TureType&OpenType.（OpenType更强大，遇到时特别标注）

常用字体名称

通用字体
"Times" 泰晤士报首次采用，之后博得大众青睐(times.ttc,times.ttf)
"Time New Roman" 可以使用"Times"替代 (times.ttf) OpenType
"Courier"  世界上最知名的字形
"Courier New"  常用于代码显示，可以使用"Courier"替代 (cour.ttf) OpenType

其他常见的字体：黑体 宋体 新宋体 仿宋 楷体 华文黑体 华文楷体 华文宋体 隶书 幼圆 Verdana Tahoma

Windows 10字体
"Arial"  Microsoft Monotype 无衬线(arial.ttf) OpenType
"SimSun"  中易宋体(simsun.ttc) OpenType
"MingLiu"  细明体 华康科技(mingliu.ttc) TrueType
"Microsoft Yahei UI"  微软雅黑 无衬线黑体 方正版权(msyh.ttc) OpenType
"Microsoft Yahei UI Bold"  微软雅黑Bold 无衬线黑体 方正版权(msyhbd.ttc) OpenType
"Microsoft Yahei UI Light"  微软雅黑Light 无衬线黑体 方正版权(msyhl.ttc) OpenType

MacOS字体
"Helvetica"  Apple(Helvetica.ttc) TrueType  Helvetica是苹果电脑的默认字体，与微软常用的Arial字体相似
Hiragino Sans GB 冬青黑体 苹果电脑默认字体(Hiragino Sans GB.ttc) OpenType PostScript
"STSong"  华文宋体(Songti.ttc) TrueType

Linux字体
文泉驿微米黑

Android字体
Droid Sans 安卓系统中默认的西文字体，是一款人文主义无衬线字体
Droid Sans Fallback 是包含汉字、日文假名、韩文的文字扩展支持

其他变体
Comic Sans MS 拟手写字体，是微软系统最常用的字体之一
JetBrainsMono 为开发者设计的编程字体

```css
小米网站的字体
font:14px/1.5 Helvetica Neue,Helvetica,Arial,Microsoft Yahei,Hiragino Sans GB,Heiti SC,WenQuanYi Micro Hei,sans-serif;
```



字体特征和用法

1. Georgia,Times New Roman属于Serif(有衬线)字体
2. Arial,Tahoma,Verdana,属于Sans Serif(无衬线)字体
3. Courier New属于等宽字体，写代码的编辑器使用该字体
4. 宋体，细明体属于有衬线字体
5. 黑体，幼圆体属于无衬线字体
6. 正文Serif，标题Sans Serif
7. font-family默认采用Tahoma. Tahoma是英文Windows操作系统的默认字体，这个字体比较均衡，显示中英文混排很不错，是经久耐看的一款字体
8. Mac OS X系统有一款比Tahoma更典雅的系统默认字体：Helvetica，非Mac系统的Helvetica字体都是Rip版
9. Arial是早期Windows英文系统的默认字体，XP和Vista上都是Tahoma
10. 最后的sans-serif是针对强悍的Linux DIY族。Linux默认只有kernel，字体完全由用户自定义，针对这部分用户，sans-serif可能能派上用场
11. 最后，无论在XP还是Vista下，不指定网页的中文字体时，默认就是宋体。因此font-family里的'宋体'是多余的，可以省去
12. [百度搜索"Serif和Sans-serif字体的区别"](baidu.com)


常见字体公司
Microsoft：美国微软公司(Microsoft Corporation)
Apple：美国苹果电脑公司(Apple Computer, Inc.)
Monotype：蒙纳字体(The Monotype Corporation)
中易：北京中易中标电子信息技术有限公司(Beijing ZhongYi Electronics,Co.)
北大方正 Founder ：北京北大方正电子有限公司(Beijing Founder Electronics Co.,Ltd.)
华文SinoType：常州华文印刷新科技有限公司(Changzhou SinoType Technology Co.,Ltd.)
华康科技DynaComware：（今名“威锋数位”）(DynaComware Corp.)
蒙纳香港Monotype：(Monotype Hong Kong Ltd. and Monotype Imaging Inc.)
Diwan：英国Diwan公司(Diwan Science and Information Technology Ltd.)


New Word
- bold  黑体的，大胆的，厚颜无耻的，英勇的
- condensed  浓缩的，扼要的，窄体
- regular  定期的，整齐的，普通的，经常的
- italic  斜体的，斜体字
- expanded  扩体，展开的
- monospace 等宽，等宽字体，单间隔，单间隔字体













# 字号
字号又叫字体大小：单位是px，一行文本的最高点到最低点

八号字  5
七号字  5.5
小六    6.5
六号    7.5
小五    9
五号    10.5
小四    12
四号    14
小三    15
三号    16
小二   18
二号   22
小一    24
一号    26
小初    36
初号    42

备注：
腾讯文档中，标题1是二号字，标题2是小二字，正文是小四字
word软件中，标题是二号字，正文是五号字

# 字体文件格式
WOFF
WOFF是Web Open Font Format几个词的首字母简写。这种字体格式专门用于网上，由Mozilla联合其它几大组织共同开发。WOFF字体通常比其它字体加载的要快些，因为使用了OpenType (OTF)和TrueType (TTF)字体里的存储结构和压缩算法。这种字体格式还可以加入元信息和授权信息。这种字体格式有君临天下的趋势，因为所有的现代浏览器都开始支持这种字体格式。【支持的浏览器：IE9+,Firefox3.5+,Chrome6+,Safari3.6+,Opera11.1+】

SVG / SVGZ
Scalable Vector Graphics (Font). SVG是一种用矢量图格式改进的字体格式，体积上比矢量图更小，适合在手机设备上使用。【支持的浏览器：Chrome4+,Safari3.1+,Opera10.0+,iOS Mobile Safari3.2+】

EOT
Embedded Open Type。这是微软创造的字体格式。这种格式只在IE6-IE8里使用。【支持的浏览器：IE4+】

OTF / TTF
OpenType Font 和 TrueType Font。部分的因为这种格式容易被复制(非法的)，这才催生了WOFF字体格式。然而，OpenType有很多独特的地方，受到很多设计者的喜爱。【支持的浏览器：IE9+,Firefox3.5+,Chrome4+,Safari3+,Opera10+,iOS Mobile Safari4.2+】

IE6-8仅支持 embedded-opentype（.eot）
firefox3.5支持truetype（.ttf）、opentype（.otf）
firefox3.6支持truetype（.ttf）和opentype（.otf）、WOFF（.woff）
chrome支持truetype（.ttf）、opentype（.otf）、WOFF（.woff）、svg（.svg）
safari支持truetype（.ttf）、opentype（.otf）、WOFF（.woff）、svg（.svg）
opera支持truetype（.ttf）、opentype（.otf）、WOFF（.woff）、svg（.svg）

认识 Iconfont 以及什么是 .eot、.woff、.ttf、.svg https://www.jianshu.com/p/0fc36e7f7d2e
CSS3 @font-face属性 https://www.jianshu.com/p/c0301e632a01
iconfont字体图标的使用方法--超简单! https://www.cnblogs.com/hjvsdr/p/6639649.html




# 外部字体

阿里字体 https://www.iconfont.cn/ 我的收藏和我的项目里面有使用历史，下载素材有svg，ai，esp三种格式文件，下载代码是字体ttf文件
Bootstrap 的图标是 Font-Awsome
icomoon https://icomoon.io
选择合适的字体并下载（阿里图标）

```
下载内容目录
/Alibaba/font/iconfont
├─┬ deomo_index.html
│ ├ demo.css
│ ├ iconfont.css
│ ├ iconfont.eot
│ ├ iconfont.js
│ ├ iconfont.json
│ ├ iconfont.svg
│ ├ iconfont.ttf
│ ├ iconfont.woff
│ ├ iconfont.woff2

```

```css
/*字体引用*/
/*引用外部字体*/
@font-face {
  font-family: 'iconfont';
  src: url('iconfont.eot');/* IE9 */
  src: url('iconfont.eot?#iefix') format('embedded-opentype'),/* IE6-IE8 */
      url('iconfont.woff2') format('woff2'),
      url('iconfont.woff') format('woff'),
      url('iconfont.ttf') format('truetype'), /*chrome, firefox, opera, Safari, Android, iOS4.2+*/
      url('iconfont.svg#iconfont') format('svg'); /*iOS4.1-*/
}
/*定义样式*/
.iconfont {
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/*页面展示*/
<span class="iconfont">&#x33;</span>


```

