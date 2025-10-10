# 6 Text Processing Services

re -Regular expression operations



regular expressions

[手册6.2](https://docs.python.org/zh-cn/3/library/re.html)

[how to](https://docs.python.org/zh-cn/3/howto/regex.html)

使用方法见Unix系统->string

[正则表达式用法](https://www.cnblogs.com/misswangxing/p/10736310.html)





# 21 Internet Protocols and Support

urllib.request-Extensible library for opening URLs

[urllib.request](https://docs.python.org/zh-cn/3/library/urllib.request.html#request-objects)

[how to](https://docs.python.org/zh-cn/3/howto/urllib2.html)

在手册的1176-1183页
英文单词
对常用方法的记录





库urllib.request

用于打开URL的可拓展库

源代码：Lib/urllib/request.py

Urllib.request模块定义了适用于在各种复杂情况下打开URL（主要为HTTP）的函数和类，例如基本认证、摘要认证、重定向、cookies及其他

Data

```python
urllib.request.__all__ = ['Request', 'OpenerDirector', 'BaseHandler', 'HTTPDefaultErrorHandler', 'HTTPRedirectHandler', 'HTTPCookieProcessor', 'ProxyHandler', 'HTTPPasswordMgr', 'HTTPPasswordMgrWithDefaultRealm', 'HTTPPasswordMgrWithPriorAuth', 'AbstractBasicAuthHandler', 'HTTPBasicAuthHandler', 'ProxyBasicAuthHandler', 'AbstractDigestAuthHandler', 'HTTPDigestAuthHandler', 'ProxyDigestAuthHandler', 'HTTPHandler', 'FileHandler', 'FTPHandler', 'CacheFTPHandler', 'DataHandler', 'UnknownHandler', 'HTTPErrorProcessor', 'urlopen', 'install_opener', 'build_opener', 'pathname2url', 'url2pathname', 'getproxies', 'urlretrieve', 'urlcleanup', 'URLopener', 'FancyURLopener', 'HTTPSHandler']
```



Functions

```python
build_opener()
getproxied()
pathname2url()
url2pathname()
urlcleanup()
urlopen()
urlretrieve()
```





英文单词



**0228**

request 请求，向服务器请求资源

in a complex world 复杂的世界

complete 完整的，完全的，彻底的

basic 基本的，基础的

digest 摘要，消化，吸收，融会贯通