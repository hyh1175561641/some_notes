



https://spring.io/projects/spring-boot
https://docs.spring.io/spring-boot/index.html
https://docs.spring.io/spring-boot/api/java/index.html

https://mvnrepository.com/artifact/org.springframework.boot

https://start.spring.io
https://start.aliyun.com

# 搭建空项目

```xml
<!-- spring.io -->

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
<parent>
org.springframework.boot:spring-boot-starter-parent:2.3.7.RELEASE
  <relativePath/> <!-- lookup parent from repository -->
</parent>

dependencies:
https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter/3.3.3
org.springframework.boot spring-boot-starter-test scope:test

build > plugins > plugin:
    org.springframework.boot:spring-boot-maven-plugin
</project>

<!-- application.properties
spring.application.name=mybatis-springboot
-->

<!--
@SpringBootApplication
public class MybatisSpringbootApplication {
  public static void main(String[] args) {
    SpringApplication.run(MybatisSpringbootApplication.class, args);
  }
}

@SpringBootTest
class MybatisSpringbootApplicationTests {
  @Test
  void contextLoads() {}
}
-->


```




# Spring Boot



```java
//起步引导类，环境搭建的组成部分，放在跟目录下面
package com.itheima;
@SpringBootApplication
public class MySpringBootApplication {
    public static void main(String[] args) {
        //run方法表示运行springboot的引导类，参数是引导类的字节码对象
        ConfigurableApplicationContext run = SpringApplication.run(MySpringBootApplication.class);
        //ConfigurableApplicationContext run = SpringApplication.run(BootBean.class);
        System.out.println(run);
    }
}

package com.itheima.controller;
//最基本的springmvc项目
@Controller
public class QuickController {
    @RequestMapping("/quick")
    @ResponseBody
    //编写/quick页面
    public String quick() {
        return "hello springboottt";
    }
}

```





# Boot 配置

properties最优先，其次yml,其次yaml.当这些文件共存的时候，相互叠加相互覆盖

```yaml

# 配置查询信息 https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html#application-properties

# SpringBoot的名称
spring:
  applications:
    name: springBootTest
  main:
    #修改banner启动logo
    banner-mode: console
  banner:
    image:
      #修改banner启动logo
      location: github.jpeg
      width: 200
  datasource:
    # 配置数据源
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/test
    username: root
    password: 0000
    type: com.alibaba.druid.pool.DruidDataSource

# Tomcat
server:
  port: 80
  address:
  servlet:
    context-path: /demo



# 环境配置
spring.profiles.active=test # 当前配置环境


```





# 热部署

```xml
<!--工程热部署,自动编译更新代码-->
<!--idea需要配置热部署，默认不会自动编译，需要对idea进行配置自动编译
旧版配置方法
第一步Settings->Build,Execution,Deployment->Compiler->Build project automatically打对勾
第二步ctrl+shift+alt+/->Maintenance->registry->compiler.automake.allow.when.app.runing打对勾
新版配置方法
第一步Settings->Build,Execution,Deployment->Compiler->Build project automatically打对勾
第二步:Settings->AdvancedSettings->Compiler->Allow auto-make to start even if developed application is currently running打对勾
-->
<!--web功能的起步依赖-->
org.springframework.boot:spring-boot-starter-web
org.springframework.boot:spring-boot-devtools:optional true


<!--配置下面的maven-compiler-plugin的插件spring boot热部署(不配置也行)-->
<plugin>
gav:org.apache.maven.plugins:maven-compiler-plugin:3.8.0
<configuration>
  <source>1.8</source>
  <target>1.8</target>
  <encoding>UTF-8</encoding>
  <!--配置热加载-->
  <executable>true</executable>
  <fork>true</fork>
</configuration>
</plugin>

<!--  application.properties开启热加载 -->
spring.devtools.restart.enabled=true

```





# 打包运行

```bash
# package进行打包,得到一个jar文件
mvn package
java -jar boot-0.1.jar

```





