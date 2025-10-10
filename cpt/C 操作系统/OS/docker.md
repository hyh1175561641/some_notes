
https://kubernetes.io/






https://www.docker.com/
https://hub.docker.com/
https://docs.docker.com/
https://github.com/docker/docker


https://www.zentao.net/book/zentaopms/38.html#0

```bash
docker pull ubuntu centos busybox alpine fedora
httpd nginx tomcat maven alpine/git
java openjdk python nodejs golang php gcc
mysql:8 redis mongoDB postgres phpmyadmin
hello-world docker/getting-started
registry portainer/portainer

```


# Docker

Docker是基于Ubuntu开发的，建议在Ubuntu下安装.centos下不支持最新一些补丁包，CentOS6会有问题，建议安装CentOS7上面


```shell
# 安装与启动
$ sudo yum update
# yum-util提供yum-config-manager功能，剩下两个devicemapper驱动依赖
$ sudo yum install -y yum-utils device-mapper-persistent-data lvm2
# 设置阿里云为yum源
$ sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
$ sudo yum install docker-ce
$ docker -v

# 配置文件添加docker源
$ vi /etc/docker/daemon.json
{"registry-mirrors":["https://docker.mirrors.ustc.edu.cn"]}

# 服务的启动与关闭
systemctl start docker
systemctl stop docer
systemctl restart docker
systemctl status docker

systemctl enable docker # 开机启动

```


```bash
# Docker CentOS
# 目前，CentOS 仅发行版本中的内核支持 Docker。Docker 运行在 CentOS 7 上，要求系统为64位、系统内核版本为 3.10 以上。Docker 运行在 CentOS-6.5 或更高的版本的 CentOS 上，要求系统为64位、系统内核版本为 2.6.32-431 或者更高版本。
# uname -r 3.10.0-327.el7.x86_64
yum -y install docker
service docker start
docker run hello-world

# 脚本安装
sudo yum update
curl -fsSL https://get.docker.com/ | sh
sudo service docker start
sudo docker run hello-world
docker run -d -p 80:80 docker/getting-started

```







# Command

```shell
docker info
docker --help

# 镜像相关的命令
$ docker images # 查看已下载的镜像
镜像名称 镜像标签 镜像ID 镜像创建日期 镜像大小，这些镜像都在/var/lib/docker目录下
REPOSITORY               TAG       IMAGE ID       CREATED         SIZE
redis                    latest    2460522297a1   12 days ago     117MB

$ docker search centos # 搜索镜像名称中包含centos的镜像
镜像名称 镜像描述 用户评价 是否官方 自动构建(表示该镜像由DockerHub自动构建流程创建的)

$ docker pull 镜像名称:镜像标签 # 拉取镜像 下载镜像
$ docker rmi 镜像名称或镜像ID # 删除镜像
$ docker rmi `docker images -q` # 删除所有镜像


# 容器相关的命令

$ docker ps # 查看正在运行的容器 -a所有的 -l最后一次运行的
# -a 列出所有正在运行的容器
# -l 显示最近创建的容器
# -n 显示最近创建的n个容器
# -q 静默模式,只显示容器编号
# --no-trunc 不截断输出
容器ID 容器名称 容器命令 容器创建时间 容器状态 端口号 自定义容器名称
$ docker ps -f status=exited # 查看停止的容器

$ docker run # 运行新的容器 参数顺序不能乱，参数在前镜像在后
# -i 表示运行容器,以交互式运行
# -t 进入命令行 -it容器创建后就能登录进去，分配一个伪终端
# --name 为创建的容器命名
# -v 表示目录映射关系，共享一个目录
# -d 创建守护式容器在后台运行
# -p 表示端口映射，前者是主机端口，后者是容器端口
# -P 随机端口
$ docker run ubuntu:15.10 /bin/echo "Hello world"

# docker run -it --name=RUNNAME IMGNAME:TAGNAME # 交互式创建容器
$ docker run -it --name=myubuntu ubuntu:15.10 /bin/bash
# docker run -id --name=RUNNAME IMGNAME:TAGNAME # 守护式容器
$ docker run -id --name=myubuntu ubuntu:15.10
d9f1e91122f8f8602002682d5ff009b74c705fc7ec67f2b30b7f7218b75eb918
$ docker exec -it myubuntu /bin/bash # 进入守护进程，退出后守护线依然运行
# 目录挂载，将本地机与容器内的目录进行映射,权限不足 --privileged=true
$ docker run -di -v /home/aaa/dk:/root/dk --name=myubuntu ubuntu

# docker exec RUNNAME
$ docker exec -it myubuntu /bin/bash

# 想要进入停止的linux容器，先start然后exec
# docker start RUNNAME # 启动停止的容器
$ docker start -i myubuntu

# docker stop RUNNAME # 停止容器
$ docker stop -i myubuntu

# 把文件上传到docker本地，然后复制文件进入到docker，容器必须加载，状态可以是停止
# docker cp FILE myubuntu:PATH # 把本地文件复制到docker中里面
$ docker cp a.txt myubuntu:/usr/local
$ docker cp myubuntu:/usr/local a.txt # 把容器的文件复制到本地

# docker inspect RUNNAME(RUNID) 查看容器运行的各种数据
$ docker inspect myubuntu
$ docker inspect --format='{{.NetworkSettings.IPAddress}}' myubuntu # 查看docker IP地址

# docker rm RUNNAME 删除容器 -f删除运行中的容器
$ docker rm myubuntu

# docker stats 查看容器使用资源

# docker logs 查看容器日志
# -f
docker logs -f # 查看容器日志



```

```shell
# 备份与迁移

# docker commit RUNNAME IMGNAME # 容器名称 镜像名称
$ docker commit mynginx mynginx_i # 把运行中的容器保存为镜像

# docker save -o FILE.tar IMGNAME # 保存容器为tar文件 -o参数表示output
$ docker save -o mynginx.tar  mynginx_i # 将镜像备份为tar文件

# docker load -i FILE.tar # 导入文件成为镜像 -i参数表示input
$ docker load -i mynginx.tar # 将tar文件恢复成镜像


```





# Network

```bash



```




# Example

```shell
# 运行经典实例
docker run hello-world
docker run -d -p 80:80 docker/getting-started


# 数据库
docker pull centos/mysql-57-centos7 # 拉取mysql数据库
# -e 表示添加环境变量，是root的登录密码
docker run -di --name=mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 centos/mysql-57-centos7 # 创建容器
docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql
docker exec -it mysql /bin/bash
mysql -uroot -p

docker pull redis # 拉取redis数据库
docker run -di --name=redis -p 6379:6379 redis

# mongodb
docker run -itd --name mongo -p 27017:27017 mongo --auth # 无效
docker run -d --network mongonetwork --name mongo -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=admin -p 27017:27017 mongo
docker exec -it mongo mongo admin
docker exec -it mongo mongosh admin # 6.0及以上版本
# 创建一个名为 admin，密码为 123456 的用户。
>  db.createUser({ user:'admin',pwd:'123456',roles:[ { role:'userAdminAnyDatabase', db: 'admin'},"readWriteAnyDatabase"]});
# 尝试使用上面创建的用户信息进行连接。
> db.auth('admin', '123456')

# PHPMyAdmin
环境变量的存在会PMA_ARBITRARY导致显示服务器连接表单
docker run -d --name phpmyadmin -e PMA_ARBITRARY=1 -p 8080:80 phpmyadmin

# ElasticSearch
docker pull elasticsearch:7.7.0
docker run --name elasticsearch -d -e ES_JAVA_OPTS="-Xms512m -Xmx512m" -e "discovery.type=single-node" -p 9200:9200 -p 9300:9300 elasticsearch:7.8.0
# 访问ip:9200有信息说明安装成功


# web服务器
docker pull tomcat:7-jre7 # 拉取tomcat镜像
docker run -di --name=mytomcat -p 8080:8080 -v /usr/local/webapps:/usr/local/tomcat/webapps tomcat:7-jre7

docker pull nginx # 拉取nginx镜像
docker run -di --name=mynginx -p 80:80 nginx


# 编译软件
docker run -itd -p 9090:9090 -v C:/Users/Administrator/docker/go:/go --name golang golang

# Linux内核
docker run ubuntu:15.10 /bin/echo "Hello world"
docker run -itd --name ubuntu -p 80:80 ubuntu
docker exec -it ubuntu
docker run -itd --name centos -p 80:80 centos:centos7

# RabbitMQ
docker run --name rabbitmq -d -p 15672:15672 -p 5672:5672 rabbitmq
# 输入ip:15672可以访问管理页面 guest guest docker中添加账户查看rabbitmq文档

```

# Dockerfile

```dockerfile
FROM image_name:tag  基于某个镜像构建，如果不存在会立马下载镜像
MAINTAINER user_name 声明镜像的创建者
ENV key value 设置环境变量(可以写多条)
RUN command 是Dockerfile的核心部分(可以写多条)
ADD source_dir/file dest_dir/file 将本地机的文件复制到容器内，如果是压缩文件，复制后自动解压
COPY source_dir/file dest_dir/file 和ADD类似，但是如果有压缩文件不能解压，dest目标目录
WORKDIR path_dir 设置工作目录，基础目录，指令都基于基础目录工作

```

```dockerfile
# 搭建一个jdk8的centos的docker镜像
$ mkdir -p /usr/local/dockerjdk8 在此目录构建dockerfile文件
$ cp jdk-8u171-linux-x64.tar.gz /usr/local/dockerjdk8/ 复制java到工作目录
$ cd /usr/local/dockerjdk8/ & ls -al
$ vi Dockerfile 必须用这个文件名
FROM centos:7
MAINTAINER itheima
WORKDIR /usr
RUN mkdir /usr/local/java
ADD jdk-8u171-linux-x64.tar.gz /usr/local/java

ENV JAVA_HOME /usr/local/java/jdk1.8.0_171
ENV JRE_HOME $JAVA_HOME/jre
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib:$CLASSPATH
ENV PATH $JAVA_HOME/bin:$PATH

$ dir 
Dockerfile jdk-8u171-linux-x64.tar.gz
$ docker build -t='jdk1.8' .  # 在当前目录构建jdk8镜像
$ docker images # 可以查看到出现了jdk1.8镜像



```



# 私有仓库

```shell

# 黑马30个文件夹的docker最后三个视频，拉取一个镜像当作服务器，经过一系列配置，然后可以共享自己的镜像，有需要再看吧
# 还可以上传自己的私有镜像

docker pull registry #私有仓库镜像
docker run -di --name=registry -p 5000:5000 registry # 启动服务器
http://192.168.184.141:5000/v2/_catalog 





```









# Portainer

https://www.portainer.io/
Portainer是一个可视化的容器镜像的图形管理工具，利用Portainer可以轻松构建，管理和维护Docker环境。 而且完全免费，基于容器化的安装方式，方便高效部署。



docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
password: 123456123456

```bash
docker search portainer |head -n 3
docker volume create portainer_data
docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer



#拉取镜像
docker pull portainer/portainer-ce:latest 
#启动容器
docker run -d  --name portainer -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v /app/portainer_data:/data --restart always --privileged=true portainer/portainer-ce:latest

docker run -d -p 9000:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock --name prtainer \portainer/portainer

```

用浏览器访问：http://localhost:9000可以看到以下界面
设置admin用户密码，需要输入两次相同的密码
以下界面中，选择local，再点击Connect


管理镜像
可以拉取，上传，构建等管理镜像
管理容器
可以创建，删除启动和停止容器等


Swarm
Docker Swarm 和 Docker Compose 一样，都是 Docker 官方容器编排项目，但不同的是，Docker Compose 是一个在单个服务器或主机上创建多个容器的工具，而 Docker Swarm 则可以在多个服务器或主机上创建容器集群服务，对于微服务的部署，显然 Docker Swarm 会更加适合。

Node Status Down
节点一直处于Down Status
尝试重启该节点的Docker，但是无效。然后从Swarm集群中移除该节点，再次Join到集群，解决问题。

#从master node 移除节点
docker node rm [ID]
#在node节点join集群
docker swarm join --token [TOKEN] [master node ip]:2377

Node Label
swarm 集群节点标签，用于容器部署的时候，根据Label部署到指定的服务器上。
另一篇文章，详细写了Label的使用：东小西：Node Label节点标签与服务约束

docker node update --label-add role=base kvm-10-115-80-116

Services & Stacks
在开发过程中，遇到的任何问题，大家都可以先从官方的Docker Docs寻找答案，切勿直接采用度娘的博客的答案，Docker Docs，真的YYDS！！！！
https://docs.docker.com/engine/reference/run/

https://docs.docker.com/compose/compose-file/

下面通过Service和Stack两种方式部署服务

Service
docker service create --name test-service \
--mount type=volume,source=service-logs,destination=/app/logs \
--network host \
-e TZ="Asia/Shanghai" \
-e SPRING.PROFILES.ACTIVE=dev \
-e LOG.HOME=/app/logs \
--mode replicated \
--replicas 2 \
--replicas-max-per-node=1 \
--constraint 'node.labels.role == service' \
192.168.2.100:5000/test-service:latest
--mount： 挂载Voluem。type有volume,bind,tmpfs, ornpipe，常用的是volume和bind。需要注意的type=bind的时候，宿主机必须存在挂载目录。
--network：当前使用Host模式，采用宿主机网络。
--mode：部署模式 (replicated or global)(默认"replicated")，global模式会在可部署的节点有且仅部署一个容器。
-e：环境变量，比如说时区，springboot配置参数等。
--replicas：副本数。
--replicas-max-per-node ：每个节点的最大任务数（默认值0=无限制）
--constraint：放置约束，根据Label部署到指定的服务器上。

Stack
docker-compose.yml编写过程中，有任何的问题，可以查看官方Docker Docs








