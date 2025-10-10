


https://shiro.apache.org/


https://blog.csdn.net/MinggeQingchun/article/details/126414384








# Shiro

Apache旗下的轻量级权限控制框架,在Web环境下一些特定的需求需要手动编写代码定制

Apache Shiro is a powerful and easy-to-use Java security framework that performs authentication, authorization, cryptography, and session management. With Shiro’s easy-to-understand API, you can quickly and easily secure any application – from the smallest mobile applications to the largest web and enterprise applications.
Shiro是一个功能强大且易于使用的Java安全框架，它执行身份验证，授权，加密和会话管理。使用Shiro易于理解的API，您可以快速轻松地保护任何应用程序从最小的移动应用程序到最大的web和企业应用程序。

权限管理框架：基本上涉及到用户参与的系统都要进行权限管理，权限管理属于系统安全的范畴，权限管理实现对用户访问系统的控制，安装安全规则或者安全策略控制用户可以访问而且只能访问自己被授权的资源。
认证和授权：权限管理包括用户身份认证和授权两部分，简称认证授权。对于需要访问控制的资源用户首先经过身份认证，认证通过后用户具有该资源的访问权限方可访问。
身份认证：身份认证，就是判断一个用户是否为合法用户的处理过程，最常用的简单身份认证方式是系统通过核对用户输入的用户名和口令，看其是否与系统中存储的该用户的用户名和口令一致，来判断用户身份是否正确，对于采用指纹等系统，则出示指纹，对于硬件key等刷卡系统，则需要刷卡。
授权：授权访问控制，控制谁能访问哪些资源。主体进行身份认证后需要分配权限方可访问系统的资源，对于某些资源没有权限是无法访问的。


详细架构：后续添加





```java
/*
org.apache.shiro shiro-core 1.4.0/1.3.2/1.8.0

*/

```


shiro-all
shiro-aspectj
shiro-cache
shiro-config-core
shiro-config-ogdl
shiro-core
shiro-crypto-cipher
shiro-crypto-core
shiro-crypto-hash
shiro-ehcache
shiro-event
shiro-hazelcast
shiro-guice
shiro-lang
shiro-quartz
shiro-spring
shiro-web





```java

// 基本流程
//创建安全管理器对象
DefaultSecurityManager securityManager = new DefaultSecurityManager();
//创建Realm提供数据
IniRealm iniRealm = new IniRealm("classpath:shiro.ini");
//给安全管理器设置realm
securityManager.setRealm(iniRealm);
//全局安全工具类SecurityUtils设置安全管理器
SecurityUtils.setSecurityManager(securityManager);
//关键对象subject主体
Subject subject = SecurityUtils.getSubject();
//创建令牌,身份信息(账号),凭证信息(密码)
UsernamePasswordToken usernamePasswordToken = new UsernamePasswordToke("xiaochen", "123");
System.out.println(usernamePasswordToken);
try {
    System.out.println("认证状态之前" + subject.isAuthenticated());
    //用户认证
    subject.login(usernamePasswordToken);
    System.out.println("认证状态之后" + subject.isAuthenticated());
} catch (UnknownAccountException e) {
    System.out.println("用户名认证失败");
} catch (IncorrectCredentialsException e) {
    System.out.println("密码认证失败");
} catch (Exception e) {
    e.printStackTrace();
}


```



```java



```

```java



```






# Spring





# SpringBoot












# Source Code

```bash

git clone https://github.com/apache/shiro.git


```





