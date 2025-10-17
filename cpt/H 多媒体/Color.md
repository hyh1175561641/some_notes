

配色网站
https://www.sohu.com/a/234226326_100112198
https://www.0to255.com/
https://color.adobe.com/zh/create/color-wheel/
https://paletton.com/
http://brandcolors.net/
https://materialui.co/colors
https://bjango.com/mac/skalacolor/
https://coolors.co/




https://htmlcolors.com/color-theory 完整颜色理论




菜鸟工具
https://www.runoob.com/tags/html-colorname.html 颜色名
https://www.runoob.com/tags/html-colorpicker.html 拾色器
https://www.runoob.com/tags/colors-mixer.html 颜色混搭

https://www.jyshare.com/front-end/55/ RGB HEX 进制工具
https://www.jyshare.com/front-end/868/ RGB HSV 转换
https://www.jyshare.com/front-end/870/ RGB CMYK 转换工具
https://www.jyshare.com/front-end/873/ HEX CMYK 转换工具
https://www.jyshare.com/front-end/875/ HEX HSV 转换工具
https://www.jyshare.com/front-end/877/ HSV CMYK 转换工具



https://www.jyshare.com/front-end/5449/ HTML 取色器
https://www.jyshare.com/front-end/6210/ 取色器
https://www.jyshare.com/front-end/6214/ 图片取色器/拾色器
https://www.jyshare.com/front-end/6327/ 调色板
https://www.jyshare.com/front-end/6656/ 颜色选择器
https://www.jyshare.com/front-end/9072/ 随机颜色生成器





百度百科
https://baike.baidu.com/item/%E8%89%B2%E5%BD%A9/7998511 色彩
https://baike.baidu.com/item/%E9%A2%9C%E8%89%B2%E6%A8%A1%E5%9E%8B/7558583 颜色模型
https://baike.baidu.com/item/%E4%B8%89%E5%8E%9F%E8%89%B2%E5%85%89%E6%A8%A1%E5%BC%8F/6833363 三原色光模式














# 光谱

光谱, 红橙黄绿青蓝紫
光柱, 从白到黑的渐变
圆形光谱加黑白光柱, 可以表示任意颜色



色相是指光谱中各种颜色, 光谱中的颜色
纯度是指色彩的纯净程度, 纯度低显灰色, 纯度高显单色调
明度是指色彩的明亮程度, 是物体反射光量的区别, 产生颜色的明暗强弱, 灯光的照射决定



# 颜色模型


## RGB

RGB是相加混色模式, 每种颜色分量越多, 得到的颜色越亮, 每种颜色的取值范围为0~255; RGB常用于计算机显示方面.

RGB表示法, Red红, Green绿, Blue蓝
255, 0, 0 红色
0, 255, 0 绿色
0, 0, 255 蓝色
255, 255, 0 黄色
0, 255, 255 青色
255, 0, 255 紫色
靠左红 靠右蓝 中间绿 左中黄 右中青 两边紫
红橙黄绿青蓝紫



## CMYK

CMY是CMYK相减混色模式, 用这种方法产生的颜色之所以称为相减色, 乃是因为它减少了为视觉系统识别颜色所需要的反射光. 
由于彩色墨水和颜料的化学特性, 用三种基本色得到的黑色不是纯黑色, 因此在印刷术中, 常常加一种真正的黑色(black ink), 这种模型称为CMYK模型, 广泛应用于印刷术. 每种颜色分量的取值范围为0~100; CMYK常用于纸张彩色打印方面. 

CMY表示法, cyan青, Magenta品红, yellow黄
CMYK表示法, cyan青,Magenta品红, yellow黄, black黑

转换方法相当复杂, 需要用到Lab空间和矩阵的知识, 不过这一切Photoshop都为我们做好了, 在Photoshop里, 输入一个颜色的RGB值, 即可获取它的CMYK信息. 


## HSV/HSL/HSB




HSV HSVA
HSV是圆锥模型, 圆形边缘是H色调hue, 半径是S饱和度saturation, 高度是明度Value, 中柱竖线上白到中灰到尖黑 
V是指明度, 0是黑色, 100是白色
实际应用: Win画图
一般是, 数轴色调, 坐标是横轴纯度, 竖轴明度
https://www.jyshare.com/front-end/868/


HSL HSLA
Hue 是色盘上的度数(0-360 0/360是红色, 120是绿色, 240是蓝色). Saturation是饱和度, 0%意味着灰色, 100%是全彩. Lightness是亮度, 0%是黑色, 50%是单色调, 100%是白色. 
H色调 0-359度, S饱和度 0-100%, V值 0-100%
实际应用: HTML5取色器



HSB HSBA
跟HSV没区别
H色调0-359度, S是饱和度Saturation, B是黑色Black
实际应用: PS取色器






## Lab

L是亮度, 0是黑, 100是白
a -128绿色 127红色
b -128黄色 127蓝色



# 表示法

name 颜色名字 red

RGB
rgb(x,x,x)  十进制 rgb(255, 0, 0)
rgba(x,x,x,alpha) 透明度 rgba(255, 0, 0, 0)
rgb(x%,x%,x%)  百分之几 rgb(100%,0%,0%)
#rrggbb  十六进制 #FF0000

HSVA
hsl(hue,saturation,lightness)
hsla(h,s,l,a)



# 常用颜色名

aqua(浅绿)
black
blue
fuchsia
gray(灰)
green
lime(绿黄)
maroon
navy
olive
orange
purple
red
silver
teal(蓝绿色)

white
yellow
brown(棕色)
pink
indigo(靛青)
cyan(蓝绿)
sand(沙色)
khaki(卡其色)
amber(琥珀色)
淡蓝色(50, 215, 230)




