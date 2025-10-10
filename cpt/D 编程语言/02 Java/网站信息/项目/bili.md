







DAO MySQL MyBatis Redis ElasticSearch FastDFS
mysql:mysql-connector-java:8.0.26
org.mybatis.spring.boot:mybatis-spring-boot-starter:2.2.0
org.springframework.boot:spring-boot-starter-data-redis:2.2.2.RELEASE
org.springframework.boot:spring-boot-starter-data-elasticsearch:2.5.1
com.github.tobato:fastdfs-client:1.27.2




MVC
org.springframework.boot:spring-boot-starter-web:2.5.1
org.springframework.boot:spring-boot-starter-websocket:2.5.1
com.auth0:java-jwt:3.18.2
eu.bitwalker:UserAgentUtils:1.21



CLOUD RocketMq Eureka OpenFeign Hystrix
org.apache.rocketmq:rocketmq-client:4.9.1
org.springframework.cloud:spring-cloud-starter-netflix-eureka-client
org.springframework.cloud:spring-cloud-starter-openfeign
org.springframework.cloud:spring-cloud-starter-netflix-hystrix:2.2.10.RELEASE




UTILS
org.springframework.boot:spring-boot-devtools:2.5.1
com.alibaba:fastjson:1.2.78
org.springframework.boot:spring-boot-starter-aop:2.5.1
commons-codec:commons-codec:1.14
org.bytedeco:javacv:1.4.3
org.bytedeco.javacpp-presets:ffmpeg-platform:4.0.2-1.4.3


<!--引入推荐引擎mahout，注意要先全部引入，再使用exclusion标签-->
org.apache.mahout:mahout-mr:0.12.2
<exclusions>
org.slf4j:slf4j-api
org.slf4j:slf4j-jcl
org.apache.lucene:lucene-core
org.apache.lucene:lucene-analyzers-common
log4j:log4j
org.slf4j:slf4j-log4j12
jersey-client:com.sun.jersey
jersey-core:com.sun.jersey
jersey-apache-client4:com.sun.jersey.contribs
</exclusions>



<dependencyManagement>
org.springframework.cloud:spring-cloud-dependencies:2020.0.5
</dependencyManagement>









# Database


```sql
t_auth_element_operation
id
elementName
elementCode
operationType
createTime
updateTime

t_auth_menu
t_auth_role
t_auth_role_element_operation
t_auth_role_menu

t_collection_group
t_danmu
t_file
t_following_group
t_refresh_token
t_tag

t_user
t_user_coin
t_user_following
t_user_info
t_user_moments
t_user_role

t_video
t_video_binary_picture
t_video_coin
t_video_collection
t_video_comment
t_video_like
t_video_operation
t_video_tag
t_video_view



```




