




# Spring Security

https://docs.spring.io/spring-boot/reference/web/spring-security.html

https://mvnrepository.com/artifact/org.springframework.security

web应用安全性框架
安全的两大方面是认证Authentication和授权Authorization
认证是指用户名和密码是否能通过
授权是指是否有权限去做某些事情

新版本对整个框架进行了分层抽取,分为核心模块和Web模块,单独引入核心模块就可以脱离Web环境


SSM + shiro, 使用简单但功能强大
SpringBoot / SpringCloud + Spring Security






# Spring boot

引入依赖后,自动配置好信息,默认用户名user,默认密码在控制台输出中
org.springframework.boot:spring-boot-starter-security:


org.springframework.boot:spring-boot-starter-security:2.3.7.RELEASE
org.springframework.security:spring-security-config:5.3.6.RELEASE
org.springframework.security:spring-security-core:5.3.6.RELEASE
org.springframework.security:spring-security-web:5.3.6.RELEASE





源码刨析

安全框架本质是过滤器链,类似于网关的一个东西

需要对javaWeb的底层源码较为熟悉才能看懂

spring-security-web-5.3.6.RELEASE.jar包下
org.springframework.security.web.access.intercept.FilterSecurityInterceptor 方法级权限过滤器,显示哪些方法能够访问,哪些方法不能访问,位于过滤链的最底层

org.springframework.security.web.access.ExceptionTranslationFilter 是异常过滤器,用来处理在认证授权过程中抛出的异常

org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter 对/login的POST请求做拦截,校验表单中用户名密码










