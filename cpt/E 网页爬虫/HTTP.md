

RFC 2616 https://www.w3.org/Protocols/rfc2616/rfc2616.html

RFC 2616 HTTP/1.1 ietf txt https://www.ietf.org/rfc/rfc2616.txt

百度搜索"rfc 2616"

HTTP指南  腾讯云开发者文档 https://cloud.tencent.com/developer/section/1189824

《HTTP权威指南》[美]David Gourley   Brian Totty   Marjorie Sayer   Sailu Reddy   Anshu Aggarwal著 人民邮电出版社 ISBN 978-7-115-28148-7 运行实例：Joe的五金商店 http://joes-hardware.com

这本书的附录有丰富的MIME类型，MIME国际字符集，各国语言缩写代码 还有URL编码还没补齐全，以后学爬虫再写吧 iana官网 http://www.iana.org/assignments/media-types/media-types.xhtml

MIME类型 http://tool.oschina.net/commons





# 爬虫助手

User-Agent收集
[浏览器的userAgent归纳](https://blog.csdn.net/luanxiyuan/article/details/99570457)
[各个组成部分-HTTP请求头之User-Agent](https://www.jianshu.com/p/c5cf6a1967d1)
https://www.jianshu.com/p/da6a44d0791e
https://www.jianshu.com/p/88c79d769b02
https://blog.csdn.net/jamesaonier/article/details/89003053

```python
User-Agent:Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.76 Mobile Safari/537.36

User-Agent:
  
IE

IE6 User-Agent:Mozilla/4.0 (Windows; MSIE 6.0; Windows NT 5.2)
IE7 User-Agent:Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)
IE8 User-Agent:Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0; Trident/4.0)
IE9 User-Agent:Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Trident/5.0)
IE10 User-Agent:Mozilla/5.0 (compatible; WOW64; MSIE 10.0; Windows NT 6.2)
IE11 User-Agent:Mozilla/5.0 (Windows NT 6.3; Trident/7.0; rv 11.0) like Gecko

Edge User-Agent : Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2486.0 Safari/537.36Edge/13.10586

Windows phone

Windows phone 7

User-Agent:Mozilla/4.0 (compatible; MSIE 7.0; Windows Phone OS 7.0; Trident/3.1; IEMobile/7.0; LG; GW910)

Windows phone 7.5

User-Agent:Mozilla/5.0 (compatible; MSIE 9.0; Windows Phone OS 7.5; Trident/5.0; IEMobile/9.0; SAMSUNG; SGH-i917)

Windows phone 8

User-Agent:Mozilla/5.0 (compatible; MSIE 10.0; Windows Phone 8.0; Trident/6.0; IEMobile/10.0; ARM; Touch; NOKIA; Lumia 920)

Chrome

Chrome on windows

User-Agent:Mozilla/5.0 (Windows NT 6.2; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.94 Safari/537.36

Chrome on iphone

User-Agent:Mozilla/5.0 (iPhone; CPU iPhone OS 6_1_4 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) CriOS/27.0.1453.10 Mobile/10B350 Safari/8536.25

Chrome on mac

User-Agent:Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.93 Safari/537.36

Chrome on ubantu

User-Agent:Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/535.11 (KHTML, like Gecko)Ubuntu/11.10 Chromium/27.0.1453.93 Chrome/27.0.1453.93 Safari/537.36

Chrome on android mobile

User-Agent:Mozilla/5.0 (Linux; Android 4.0.4; Galaxy Nexus Build/IMM76B) AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.133 Mobile Safari/535.19

Chrome on android tablet

User-Agent:Mozilla/5.0 (Linux; Android 4.1.2; Nexus 7 Build/JZ054K) AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.166 Safari/535.19

Safari

Safari on mac

User-Agent:Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_6_6; en-US) AppleWebKit/533.20.25 (KHTML, like Gecko) Version/5.0.4 Safari/533.20.27

Safari on windows

User-Agent:Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US) AppleWebKit/533.20.25 (KHTML, like Gecko) Version/5.0.4 Safari/533.20.27

Safari on IPad

User-Agent:Mozilla/5.0 (iPad; CPU OS 5_0 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9A334 Safari/7534.48.3

Safari on iphone

User-Agent:Mozilla/5.0 (iPhone; CPU iPhone OS 5_0 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9A334 Safari/7534.48.3

IOS

IPad

User-Agent:Mozilla/5.0 (iPad; CPU OS 8_1_3 like Mac OS X) AppleWebKit/600.1.4 (KHTML, like Gecko) Version/8.0 Mobile/12B466 Safari/600.1.4

IPhone

User-Agent:Mozilla/5.0 (iPhone; CPU iPhone OS 8_0_2 like Mac OS X) AppleWebKit/600.1.4 (KHTML, like Gecko) Version/8.0 Mobile/12A366 Safari/600.1.4

IPod

User-Agent:Mozilla/5.0 (iPod; CPU iPhone OS 5_1_1 like Mac OS X) AppleWebKit/534.46 (KHTML, like Gecko) Version/5.1 Mobile/9B206 Safari/7534.48.3

FireFox 

FireFox on android mobile

User-Agent:Mozilla/5.0 (Android; Mobile; rv:14.0) Gecko/14.0 Firefox/14.0

FireFox on android tablet

User-Agent:Mozilla/5.0 (Linux; Android 4.1.2; Nexus 7 Build/JZ054K) AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.166 Safari/535.19

FireFox on mac

User-Agent:Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:21.0) Gecko/20100101 Firefox/21.0

FireFox on ubantu

User-Agent:Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:21.0) Gecko/20130331 Firefox/21.0

FireFox on windows

User-Agent:Mozilla/5.0 (Windows NT 6.2; WOW64; rv:21.0) Gecko/20100101 Firefox/21.0

Opera

Opera on mac

User-Agent:Opera/9.80 (Macintosh; Intel Mac OS X 10.6.8; U; en) Presto/2.9.168 Version/11.52

Opera on windows

User-Agent:Opera/9.80 (Windows NT 6.1; WOW64; U; en) Presto/2.10.229 Version/11.62

补充:

关于Edge浏览器有一些特殊情况，周知的情况目前Edge正在转向chromium内核，官网已经发布dev版本。也有说新版的Edge会随着网页内容动态更改userAgent，whatever, 我们需要做一些额外处理：

chromium内核
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.18 Safari/537.36 Edg/75.0.139.4

原始内核
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.140 Safari/537.36 Edge/17.17134

Android下的edge
Mozilla/5.0 (Linux; Android 9; BKL-AL20 Build/HUAWEIBKL-AL20) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.140 Mobile Safari/537.36 EdgA/42.0.0.2741
————————————————
版权声明：本文为CSDN博主「luanxiyuan」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/luanxiyuan/article/details/99570457


```





# User-Agent字段解释

详细版解释：[谈谈 UserAgent 字符串的规律和伪造方法](https://link.jianshu.com/?t=https://cli.ee/archives/useragent.html)

简要版解释：

我用的Chrome浏览器，查看User-Agent的结果：



```undefined
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/60.0.3100.0 Safari/537.36
```

User-Agent通常格式：



```undefined
Mozilla/5.0 (平台) 引擎版本 浏览器版本号
```

第一部分：Mozilla/5.0

由于历史上的浏览器大战，当时想获得图文并茂的网页，就必须宣称自己是 Mozilla 浏览器。此事导致如今User-Agent里通常都带有Mozilla字样，出于对历史的尊重，大家都会默认填写该部分。

第二部分：平台这部分可由多个字符串组成，用英文半角分号分开

Windows NT 10.0是指我使用的操作系统的版本，比如我使用的win10对应的就是Windows NT 10.0，如果我使用win7对应的就是Windows NT 6.1。
Win64; x64是指我的操作系统是64位的

Windows系统下：



```cpp
Windows NT 5.0 // 如 Windows 2000 
Windows NT 5.1 // 如 Windows XP
Windows NT 6.0 // 如 Windows Vista 
Windows NT 6.1 // 如 Windows 7
Windows NT 6.2 // 如 Windows 8
Windows NT 6.3 // 如 Windows 8.1
Windows NT 10.0 // 如 Windows 10
Win64; x64 // Win64 on x64
WOW64 // Win32 on x64
```

Linux系统下：



```csharp
X11; Linux i686; // Linux 桌面，i686 版本
X11; Linux x86_64; // Linux 桌面，x86_64 版本
X11; Linux i686 on x86_64 // Linux 桌面，运行在 x86_64 的 i686 版本
```

macOS系统下：



```cpp
Macintosh; Intel Mac OS X 10_9_0 // Intel x86 或者 x86_64
Macintosh; PPC Mac OS X 10_9_0 // PowerPC
Macintosh; Intel Mac OS X 10.12; // 不用下划线，用点
```

第三部分：引擎版本

AppleWebKit/537.36 (KHTML, like Gecko)...Safari/537.36，历史上，苹果依靠了WebKit内核开发出Safari浏览器，WebKit包含了WebCore引擎，而WebCore又从KHTML衍生而来。由于历史原因，KHTML引擎需要声明自己是“类似Gecko”的，因此引擎部分这么写。再后来，Google开发Chrome也是用了WebKit内核，于是也跟着这么写。借用Littern的一句话：“Chrome 希望能得到为Safari编写的网页，于是决定装成Safari，Safari使用了WebKit渲染引擎，而WebKit呢又伪装自己是KHTML，KHTML呢又是伪装成Gecko的。同时所有的浏览器又都宣称自己是Mozilla。”。不过，后来Chrome 28某个版本改用了blink内核，但还是保留了这些字符串。而且，最近的几十个版本中，这部分已经固定，没再变过

第四部分：浏览器版本

本人用的是Chrome浏览器，其中60.0 是大版本，3100是持续增大的一个数字，而0则是修补漏洞的小版本。

关于Firefox与IE/Edge的讲解：[谈谈 UserAgent 字符串的规律和伪造方法](https://link.jianshu.com/?t=https://cli.ee/archives/useragent.html)

最后，居然有大佬封装了不同操作系统不同浏览器的User-Agent：[User-Agent封装使用教程](https://link.jianshu.com/?t=https://github.com/hellysmile/fake-useragent)















# 简介

HTTP (Hypertext Transfer Protocol，超文本传输协议)是在万维网上进行通信时所使用的协议方案。HTTP是Web客户端与服务器交互文档和信息时所使用的协议

HTTP的应用不仅仅是浏览Web内容，尤其是采用SOAP和XML-RPC这样的Web服务



HTTP是无连接：无连接的含义是限制每次连接只处理一个请求。服务器处理完客户的请求，并收到客户的应答后，即断开连接。采用这种方式可以节省传输时间。

HTTP是媒体独立：这意味着，只要客户端和服务器知道如何处理数据内容，任何类型的数据都可以通过HTTP发送

HTTP是无状态：HTTP协议是无状态协议。无状态是指协议对于事务处理没有记忆能力。缺少状态意味着如果后续处理需要前面的信息，则它必须重传，这样可能导致每次连接传送的数据量增大。另一方面，在服务器不需要先前信息时它的应答就较快





# 基础内容

## URL-统一资源定位符

URI是一类更通用的资源标识符，URL是它的一个子集。由两个主要的子集URL和URN构成，URL是通过描述资源的位置来标识资源的，而URN则是通过名字来识别资源的，与他们所处位置无关。

URL是因特网资源的标准化名称，是浏览器寻找信息是所需的资源位置。通过URL，人类和应用程序才能找到、使用并共享因特网上的大量数据资源。

**语法规则**

一个统一资源定位器URL用于定位万维网上的文档。第一部分是URL方案(scheme)，告知Web客户端怎样访问资源。第二部分是指服务器的位置，告知Web客户端资源位于何处。第三部分是资源路径，说明了请求的是服务器上的哪个特定的本地资源。

Mailto , ftp, rtsp,sftp,smtp,smb

大多数URL方案都是建立在由这9个部分构成的通用格式上：

`scheme://user:password@host.domain:port/path;params?query#frag`

```text
┌────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                              href                                              │
├──────────┬──┬─────────────────────┬────────────────────────┬───────────────────────────┬───────┤
│ protocol │  │        auth         │          host          │           path            │ hash  │
│          │  │                     ├─────────────────┬──────┼──────────┬────────────────┤       │
│          │  │                     │    hostname     │ port │ pathname │     search     │       │
│          │  │                     │                 │      │          ├─┬──────────────┤       │
│          │  │                     │                 │      │          │ │    query     │       │
"  https:   //    user   :   pass   @ sub.example.com : 8080   /p/a/t/h  ?  query=string   #hash "
│          │  │          │          │    hostname     │ port │          │                │       │
│          │  │          │          ├─────────────────┴──────┤          │                │       │
│ protocol │  │ username │ password │          host          │          │                │       │
├──────────┴──┼──────────┴──────────┼────────────────────────┤          │                │       │
│   origin    │                     │         origin         │ pathname │     search     │ hash  │
├─────────────┴─────────────────────┴────────────────────────┴──────────┴────────────────┴───────┤
│                                              href                                              │
└────────────────────────────────────────────────────────────────────────────────────────────────┘
(All spaces in the "" line should be ignored. They are purely for formatting.)
```

- scheme方案-使用什么协议

scheme定义因特网服务的类型，使用什么协议，方案组件必须以一个字母符号开始，与第一个冒号隔开，方案名与大小写无关。比如http https ftp file smtp mailto rtsp sftp

- user用户

某些方案访问资源时需要用户名，后面用@分隔。比如ftp，如果没有指定用户名和密码，浏览器自动插入一个用户名和密码（IE浏览器发送IEUser，网景浏览器发送mozilla）

- password密码

用户名后面可能要包含密码，中间由冒号分隔

- host定义域主机

资源宿主服务器的主机名或点分IP地址，用点分隔。比如http默认主机是www

- domain定义因特网域名，比如google.com
- :port定义主机上的端口号，比如http默认端口号是80
- path定义服务器上的路径，由斜杠分开，如果省略则表示根目录
- params参数

为应用程序提供了访问资源所需的所有附加信息参数为名/值对。URL可以包含多个参数字段，相互之间以及与路径的其余部分之间用分号分隔

```
ftp://prep.ai.mit.edu/pub/gnu;type=d
有一个参数type=d，参数名为type，值为d

http://www.joes-hardware.com/hammers;sale=false/index.html;graphics=true
hammers/index.html，这个路径段都分别有一个参数
```

- query查询

传递参数，用问号与其余部分分隔开来，可以包含多个名/值对，用&分隔，比如数据库的查询，通过提问或查询来缩小请求资源类型的范围

- frag片段

一小片或一部分资源的名字，不会将frag传递给服务器，而是客户端自己使用，用井字符分隔开来

**相对URL**

绝对URL：包含有访问资源所需要的全部信息

相对URL：是不完整的，必须从另一个基础 (base) URL进行解析，这保持一组资源的便携性，搬移一组文档的同时，仍然保持链接的有效性

```
若一个URL是http://www.joes-hardware.com/tools.html
则可以使用./hammers.html来代表另一个页面
```

基础URL：是作为相对URL的参考点使用的。可以出自这几个地方1.\<base\>标签，2.所属资源的URL，3.没有URL，有可能是不完整或损坏的URL

解析相对URL，拆分组件，继承父组件。详细方法见HTTP权威指南

**扩充URL**

有时用户不必输入完整的URL，浏览器自动扩展URL。

主机名扩展，比如输入yahoo.com，自动扩展www

历史扩展，把以前输入过的URL储存起来。

**URL编码**

URL编码会将字符转换为可通过因特网传输的格式

URL只能使用ASCII字符集，通过因特网发送

如果URL包含ASCII以外的字符，必须转换为有效的ASCII格式

URL使用%后面跟随两位十六进制的数来替换非ASCII字符

URL不能包含空格，通常使用+来替代空格

编码字符集并未规定，但一般使用utf-8

[编码到底用的是什么字符集](http://www.ruanyifeng.com/blog/2010/02/url_encoding.html)



**URL编码函数**

JavaScript、PHP、ASP 都提供了对字符串进行URL编码的函数。

JavaScript 中使用 encodeURI() 函数，PHP 中使用rawurlencode() 函数，ASP 中使用 Server.URLEncode() 函数。

备注：JavaScript函数将空格编码成%20



## 报文

HTTP报文是在HTTP应用程序之间发送的数据块。这些数据块以一些文本形式的元信息 (meta-information) 开头，这些信息描述了报文的内容及含义，后面跟着可选的数据部分。这些报文在客户端、服务器和代理之间流动。

HTTP报文是简单的格式化数据块，每条报文都包含一条来自客户端的请求，或者一条来自服务器的响应。有三部分组成：对报文进行描述的起始行 (start line) 、包含属性的首部 (header) 块、以及可选的包含数据的主体 (body) 部分。

换行符由两个字符组成，回车符(\r)和换行符(\n)，ASCII码分别是13和10，这个行的终止序列可以写作CRLF

其中entity-body是可选的部分，主体可包含文本或二进制数据，也可以为空

## 请求报文

请求报文向Web请求一个动作

request message 请求报文的组成：

请求依次的顺序是：请求方法，请求路径，协议版本，请求首部，空行，请求内容

```
<method> <request-URL> <version>
<headers>

<entity-body>

例子
GET /img/g.gif HTTP/1.0
Host: www.host.com
```

### 方法

客户端希望服务器对资源执行的动作
GET: 是最常用的方法，通常用于请求服务器发送某个资源,数据最多只有1024字节,GET请求是在URL中发送的
HEAD: HEAD方法与GET方法类似，但服务器只返回首部，不返回主体。主要用来对首部进行检验，判断资源类型，查看对象状态码，测试资源是否被修改
POST: 用来向服务器输入数据，通常用来支持HTML表单，对长度没有限制,POST请求是在HTTP消息主体中发送的
PUT: PUT方法会向服务器写入文档，允许用户创建Web页面
TRACE: TRACE对可能经过代理服务器传送到服务器上去的报文进行追踪，用法不明确，具体内容查书
OPTIONS: OPTIONS方法请求Web服务器告知其支持的各项功能
DELETE: DELETE方法是请求服务器删除请求URL所指定的资源
CONNECT: 把服务器当做跳板，主要用于测试或诊断

**拓展方法**

WebDAV HTTP扩展

LOCK允许用户锁定资源，防止别人同时对其进行修改
MKCOL允许用户创建资源
COPY便于在服务器上复制资源
MOVE在服务器上移动资源
注意：如果一台服务器要与HTTP 1.1兼容，只要为其资源实现GET方法和HEAD方法就可以了

请求URL: 命名了所请求的资源，或者URL路径组件的完整URL，一般是服务器的绝对路径
版本: 报文所使用的HTTP版本，主要版本号和次要版本号

HTTP/\<major\>.\<minor\>

**请求首部**

见后文

**请求报文主体部分**

实体的主体部分包含任意数据的数据块。可以省略

## 响应报文

响应报文将请求的结果返回客户端

response message 响应报文的组成：

响应依次的顺序是：协议版本，状态码，状态信息，响应首部，空行，响应内容

```
<version> <status> <reason-phrase>
<headers>

<entity-body>

例子
HTTP/1.0 200 OK
Content-Type: image/gif
Content-Length: 8888

(二进制的图片流...)


```

**版本**

见请求报文

### 状态码

状态码为客户端提供了一种理解事务处理结果的便捷方式。

三位数字描述了请求过程中发生的情况，状态码的第一位数字描述一般类别

HTTP状态码被分成了五大类

**100-199信息提示**

100 - Continue 继续 服务器收到了一部分，正在等待其余部分

101 - Switching Protocols

**200-299成功**

200 - OK  成功 服务器成功处理了请求

201 - Created

202 - Accepted

203 - Non-Authoritative Information

204 - No Content

205 - Reset Content

206 - Partial Content

**300-399重定向表示资源已经被移走了**

300 - Multiple Choices

301 - Moved Permanently

302 - Found

303 - See Other

304 - Not Modified

305 - Use Proxy

307 - Temporary Redirect

**400-499客户端错误**

400 - Bad Request 错误请求 用于告知客户端发送了一个错误的请求

401 - Unauthorized 未授权 需要输入用户名和密码，身份验证没有通过

402 - Payment Required

403 - Forbidden 禁止访问 服务器拒绝此请求

404 - Not Found 未找到 找不到文件或目录

405 - Method Not Allowed

406 - Not Acceptable

407 - Proxy Authentication Required

408 - Request Timeout

409 - Conflict

410 - Gone

411 - Length Required

412 - Precondition Failed

413 - Request Entity Too Large

414 - Request URI Too Long

415 - Unsupported Media Type

416 - Requested Range Not Satisfiable

417 - Expectation Failed

**500-599服务器错误**

500 - Internal Server Error  内部服务器错误 服务器遇到错误，无法完成请求

501 - Not Implemented  无法实现

502 - Bad Gateway

503 - Service Unavailable

504 - Gateway Timeout

505 - HTTP Version Not Supported

**原因短语**

原因短语和状态码总是成对出现，是数字状态码的可读版本，只对人类有意义

**响应首部**

主要内容见下面

**响应报文主体部分**

见后文

## 首部

首部和方法配合工作，共同决定了客户端和服务器能做什么事情

可以有零个或多个首部，每个首部都包含一个名字，后面跟着一个冒号，然后是一个可选的空格，接着是一个值，最后是一个CRLF。首部最后有一个空行CRLF结束，和实体主体隔开。有些版本要求有效的请求或响应报文中必须含有特定的首部

首部可以分成以下几类：通用首部，请求首部，响应首部，实体首部，扩展首部

```
首部延续行，可以提高可读性，多出来行前面要有一个空格或tab
Server: Test Server
	Version 1.0
等价于
Server: Test Server Version 1.0
```



**通用首部**

客户端和服务器都可以使用的首部

```
通用的信息性首部
Connection
Date 报文创建的时间
MIME-Version
Trailer
Transfer-Encoding
Update
Via


通用缓存首部
Cache-Control
Pragma
```



**请求首部**

请求首部只在请求报文中才有意义，用于说明谁在发送请求，客户端的喜好及能力。服务端收到这些信息，为客户端提供更好的响应

```
请求信息首部
Client-IP
From
Host 给出了接收请求的服务器的主机名和端口号，1.1版必须
Referer 标识这个请求是从哪个页面发过来的，可以做来源统计，防盗链处理等
UA-Color
UA-CPU
UA-Disp
UA-OS
UA-Pixels
User-Agent 将发起请求的操作系统 浏览器 应用程序的名称告知服务器


Accept首部 告知服务器客户端需要什么样的信息
Accept 请求报头域，用于指定客户端可接受哪些类型的信息
Accept-Charset 客户端可接受的字符集
Accept-Encoding 客户端可接受的内容编码
Accept-Language 客户端可接受的语言
TE


条件请求首部
Expect
If-Match
If-Modified-Since
If-None-Match
If-Range
If-Unmodified-Since
Range


安全请求首部，对请求进行质询或响应认证
Authorization
Cookie 也常用复数形式cookies，认证信息
Cookie2


代理请求首部
Max-Forward
Proxy-Authorization
Proxy-Connection
```



**响应首部**

```
响应信息首部
Age
Public
Retry-After
Server 包含服务器的信息，比如名称版本号等
Title
Warning


协商首部
Accept-Ranges
Vary


安全响应首部
Proxy-Authenticate
Set-Cookie 设置cookies
Set-Cookie2
WWW-Authenticate
```

实例：

```
server:nginx
       apache
       Tengine(淘宝网发起的Web服务器项目)
       nginx/1.16.1
```



**实体首部**

```
实体信息首部
Allow
Location


内容首部
Content-Base
Content-Encoding 内容的编码
Content-Language
Content-Length
Content-Location
Content-MD5
Content-Range
Content-Type MIME类型 媒体类型信息


实体缓存首部
ETag
Expires 指定响应的过期时间，可以使代理服务器或浏览器将加载的内容更新到缓存中，如果再次访问，可以直接从缓存中加载，降低服务器负载，缩短加载时间
Last-Modified 指定资源的最后修改时间
```



**扩展首部**

```

```



**其他首部**

```
refresh 刷新网页 这是一个响应头
refresh:5;URL=跳转到的网址  自动跳转到网址
```

```

```





Content-Type说明主体是什么，MIME类型

Content-Length主体的长度



## 主体部分

主体部分就是HTTP要传输的内容，图片 视频 HTML文档 软件应用程序 信用卡事务 电子邮件

在请求报文中，请求报文主体一般承载的内容是POST请求中的表单数据，而对于GET请求，请求体则为空。



## 示例

在用POST方式登录github时，主体部分发送表单数据，头部的Content-Type只有正确指定了类型application/x-www-form-urlencoded，主体才会以表单类型提交，否则服务器响应无效

```
application/x-www-form-urlencoded 表单数据
multipart/form-data 表单文件上传
application/json 序列化JSON数据
text/xml XML数据
```







# 爬虫

把互联网比作一张大网，蜘蛛从一个节点爬到另一个节点，直到将整个网站全部爬完，整个网站的数据就可以被抓取下来了

获取网页

获取源代码，提取有用的信息。构造一个有用的请求发送给服务器，返回的响应体便是网页源代码

提取信息

分析网页源代码，提取想要的数据。使用正则或者网页节点属性，CSS选择器，XPath提取网页信息

保存数据

既可以保存到TXT或JSON，也可以保存到数据库MySQL，MongoDB



只要是基于HTTP或HTTPS协议的，HTML代码，JSON字符串，图片视频音频，各种普通的文件，都可以抓取下来



如果网页和显示的不一样，可以使用JavaScript渲染。如Selenium，Splash



# Cookies和Session
https://baijiahao.baidu.com/s?id=1705430412910145531&wfr=spider&for=pc
https://blog.csdn.net/xat2099/article/details/120805102?utm_medium=distribute.pc_feed_404.none-task-blog-2~default~BlogCommendFromBaidu~Rate-1-120805102-blog-null.pc_404_mixedpudn&depth_1-utm_source=distribute.pc_feed_404.none-task-blog-2~default~BlogCommendFromBaidu~Rate-1-120805102-blog-null.pc_404_mixedpud



某些网站为了辨别用户身份、进行session跟踪而储存在用户本地终端上的数据

最新规范RFC6265

实际是由服务器发送给客户端的特殊信息，这些信息以文本文件的方式存放在客户端，客户端每次向服务器发送请求的时候都会带上这些特殊的信息。服务器在接收到Cookie以后，会验证Cookie的信息，以此来辨别用户的身份



**Session**

一个浏览器窗口从打开到关闭这个期间

服务器用来识别客户状态，





# HTTPS

HTTPS 全称(Hyper Text Transfer Protocol over Secure Socket Layer或Hypertext Transfer Protocol Secure, 超文本传输安全协议)，是以安全为目标的HTTP通道

在HTTP下加了一层SSL/TLS协议，数据传输是加密的

默认端口443


guides 指南
redirect 重新寄送 再直接的 在直接询问 重定向
handler 处理者 管理者 处理程序
clipper 大剪刀 剪削者 理发剪 斩波器 截波器 限制器








# 自动化测试工具

Apifox = Postman + Swagger + Mock + JMeter


WEB UI自动化：	 selenium、robotframework
接口自动化： 	Jmeter、Postman、soapUI、requests、httprunner
App自动化：	Appium、Monkey、Monkeyrunner、UIautomation，UIAutomator，Robotium，macaca，airtest
PC端自动化：	QTP(UFT)
云测平台  	Testin、百度云测
性能测试： 	Jmeter、LoadRunner
安全测试：	Appscan
持续集成：	Jenkins











# Chrome

https://zh.wikipedia.org/zh-cn/Google_Chrome

https://baike.baidu.com/item/Google%20Chrome/5638378

```http
//chrome内部协议
chrome://chrome-urls/ 内部URL列表
chrome://version 显示版本
chrome://dino 小恐龙
chrome://bookmarks 书签
chrome://downloads 下载

```

Mozilla Firefox

```
//firefox内部协议
about:about


```



