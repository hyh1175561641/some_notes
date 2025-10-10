
https://spring.io/projects/spring-cloud

gitee
zentao 禅道  跟踪项目进度下任务
confluence 管理开发文档
jenkins 测试部署


# 微服务

比如有四个功能：订单模块，用户功能，商品功能，支付功能
单体架构：将业务的所有功能集中在一个项目中开发，打成一个包部署。优点架构简单部署成本低，缺点耦合度高，边界模糊，不利于开发大型项目
分布式架构：根据业务功能对系统进行拆分，每个业务模块作为独立项目开发，称为一个服务。优点降低服务耦合，有利于服务升级拓展。缺点：部署复杂，远程调用。

微服务：是一种经过良好架构设计的分布式架构方案，实现高内聚低耦合
优点：单一职责：拆分粒度更小，每个服务对应唯一的业务能力，避免重复开发
面向服务：对外暴露接口
自治：团队独立，技术独立，数据独立，部署独立。每个服务有自己独立的数据库
隔离性强：服务调用做好隔离，容错，降级，避免出现级联的问题

分布式架构的最佳实践方案就是微服务：其中最知名的是SpringClouud,和阿里巴巴的Dubbo


微服务的结构：
服务集群：多个微服务模块
远程调用：服务之间相互调用
注册中心：维护微服务每个节点的信息并监控这些节点的状态
配置中心：同意管理微服务群的配置，通知的方式实现热更新
服务网关：用户访问入口，请求路由到微服务群，能够做到负载均衡

微服务技术实现：
Dubbo：zookeeper,Redis Dubbo协议，dubbo-admin
SpringCloud：Eureka,Consul,Feign,SpringCloudConfig,springCloudGateway,Zuul,Hystrix
SpringCloudAlibaba:实现了统一的技术接口，同时兼容Dubbo和SpringCloud两种接口


# Spring Cloud
是微服务的一种实现

SpringCloud整合了其他公司开源的组件:
服务注册发现：Eureka,Nacos,Consul
服务远程调用：OpenFeign,Dubbo
服务链路监控：Zipkin,Sleuth
负载均衡组件：Ribbon
统一配置管理：springCloudConfig,Nacos
统一网关路由：SpringCloudGateway,Zuul
流控、降级、保护：Hystix,Sentinel
服务保护组件：Hystrix、Sentinel
并基于SpringBoot实现了这些组件的自动装配，从而提供了良好的开箱即用的体验

SpringCloud与SpringBoot版本也需要互相兼容,详细信息网上查找
视频上用的是Hoxton.SR10版本，对应的SpringBooot版本是2.3.x版本

服务拆分的注意事项：
不同的微服务，不要重复开发相同业务
微服务数据独立，不要访问其他微服务的数据库
微服务可以将自己的业务暴露为接口，供其他微服务调用


# spring cloud简介
Spring cloud是一个基于Spring Boot实现的服务治理工具包,在微服务架构中用于管理和协调服务的微服务:就是把一个单体项目,拆分为多个微服务,每个微服务可以独立技术选型,独立开发,独立部署,独立运维.并且多个服务相互协调,相互配合,最终完成用户的价值. Spring Cloud是一系列框架的有序集合。其主要的设施有，服务发现与注册，配置中心，消息总线，负载均衡，断路器，数据监控等，通过Spring Boot的方式，可以实现一键启动，和部署。
Spring 没有重新造车轮，只是把各家的应用给综合起来。最后给开发者遗留下了一个足够简单的，相当容易部署的，相当容易学习的Spring 体系。至于为什么要学习Spring Cloud的体系，因为原先的体系过于复杂了，导致开发的环境艰难，正是由于开发的环境的艰难，Spring Cloud 的是Spring体系的简化版，简化了原有的复杂。


搭建父工程
点击file - new - project按钮创建一个新的项目
设置GroupId和项目名称和项目路径
本步骤中的项目路径需要自己手动设置,以免找不到项目存放位置的尴尬情况
点击Finish按钮结束项目的创建
这时我们进入IDEA以后会发现我们项目只有Springcloud_Demo一个父项目，下面我问会创建Eureka，Zuul，Service等子模块对项目进行创建来实现微服务。




https://blog.csdn.net/weixin_40205234/article/details/124408609?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166737814516782425135354%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=166737814516782425135354&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-124408609-null-null.142^v62^pc_search_tree,201^v3^control_2,213^v1^t3_control2&utm_term=spring%20cloud%E6%90%AD%E5%BB%BA%E6%95%99%E7%A8%8B&spm=1018.2226.3001.4187






# 分布式事务框架


http://seata.io/zh-cn/index.html

seata




