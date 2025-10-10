



http://nginx.org/
http://nginx.org/en/docs/
http://nginx.org/en/docs/njs/index.html


Nginx是反向代理服务器.代理其实就是中间人,客户端通过代理发送请求到互联网上的服务器,从而获取想要的资源.
主要用途: 反向代理,负载均衡
特点: 跨平台,配置简单易上手,高并发,内存消耗小,稳定性高

正向代理的特点: 服务端不知道客户端,客户端知道代理端
反向代理的特点: 服务端知道客户端,客户端不知道代理端










# 安装

CentOS和Debian的依赖包下载方式有所不同
http://www.pcre.org/
http://www.zlib.net/
https://www.openssl.org/


```bash
# CentOS安装nginx
https://nginx.org/en/download.html
下载Legacy versions nginx-1.20.2.pgp文件
yum install gcc-c++
yum install pcre* openssl* zlib*
  pcre是Perl库，包括perl兼容的正则表达式。nginx的http模块用pcre解析正则表达式
  zlib提供了压缩和解压缩方式，nginx使用zlib对http包进行gzip
  openssl是强大的安全套接字层密码库，囊括主要的密码算法，常用的密钥和证书封装管理功能及ssl协议，提供丰富的应用程序供测试或其他目的使用，nginx不仅支持http协议，还支持https在ssl协议上传输http，所以需要在linux上安装openssl库

centos安装
yum install ‐y pcre pcre‐devel
yum install ‐y zlib zlib‐devel
yum install ‐y openssl openssl‐devel



tar -zxvf nginx-1.14.2.tar.gz
cp -r ./nginx-1.14.2 /usr/local
cd /usr/local/nginx-1.14.2
./configure
./configure --help
make
make install

生成的/usr/local/nginx/sbin/nginx即为需要的nginx


# ubuntu安装openssl库
sudo apt-get install libpcre3 libpcre3-dev
sudo apt-get install openssl libssl-dev
sudo apt-get install libpcre3 libpcre3-dev zlib1g-dev libssl-dev build-essential
# 下载openssl
wget http://www.openssl.org/source/openssl-1.0.2a.tar.gz
# 解压
sudo tar -zxvf openssl-1.0.2a.tar.gz -C /usr/local/src/
cd /usr/local/src/openssl-1.0.2a/
# 配置
sudo ./config
# 编译安装
sudo make && sudo make install

# 下载nginx
# 下载版本与地址参考官网：http://nginx.org/en/download.html
wget  http://nginx.org/download/nginx-1.8.0.tar.gz
# 解压
sudo tar -zxvf nginx-1.8.0.tar.gz -C /usr/local/src/
cd /usr/local/src/nginx-1.8.0
# 配置
sudo ./configure --prefix=/usr/local/nginx --with-openssl=/usr/include/openssl
# 其中以--without开头为默认安装选项，以PATH结尾是手动指定依赖库源码目录选项，更详细需要参考官网文档。
# 编译安装
sudo make && sudo make install 

```


# 配置

```bash
# 配置服务脚本，开机服务
sudo vim /etc/init.d/nginx
#!/bin/sh

### BEGIN INIT INFO
# Provides:          nginx
# Required-Start:    $local_fs $remote_fs $network $syslog
# Required-Stop:     $local_fs $remote_fs $network $syslog
# Short-Description: starts the nginx web server
# Description:       starts nginx using start-stop-daemon
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/nginx/sbin
# 设置nginx的启动路径 
DAEMON=/usr/local/nginx/sbin
NAME=nginx
DESC=nginx

if [ -f /etc/default/nginx ]; then
   . /etc/default/nginx
fi

test -x $DAEMON || exit 0

set -e

. /lib/lsb/init-functions

test_nginx_config() {
   if $DAEMON -t $DAEMON_OPTS >/dev/null 2>&1; then
      return 0
   else
      $DAEMON -t $DAEMON_OPTS
      return $?
   fi
}

case "$1" in
   start)
      echo -n "Starting $DESC: "
      test_nginx_config
      if [ -n "$ULIMIT" ]; then
         ulimit $ULIMIT
      fi
      start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
          --exec $DAEMON -- $DAEMON_OPTS || true
      echo "$NAME."
      ;;

   stop)
      echo -n "Stopping $DESC: "
      start-stop-daemon --stop --quiet --pidfile /var/run/$NAME.pid \
          --exec $DAEMON || true
      echo "$NAME."
      ;;

   restart|force-reload)
      echo -n "Restarting $DESC: "
      start-stop-daemon --stop --quiet --pidfile \
          /var/run/$NAME.pid --exec $DAEMON || true
      sleep 1
      test_nginx_config
      if [ -n "$ULIMIT" ]; then
         ulimit $ULIMIT
      fi
      start-stop-daemon --start --quiet --pidfile \
          /var/run/$NAME.pid --exec $DAEMON -- $DAEMON_OPTS || true
      echo "$NAME."
      ;;

   reload)
      echo -n "Reloading $DESC configuration: "
      test_nginx_config
      start-stop-daemon --stop --signal HUP --quiet --pidfile /var/run/$NAME.pid \
          --exec $DAEMON || true
      echo "$NAME."
      ;;

   configtest|testconfig)
      echo -n "Testing $DESC configuration: "
      if test_nginx_config; then
         echo "$NAME."
      else
         exit $?
      fi
      ;;

   status)
      status_of_proc -p /var/run/$NAME.pid "$DAEMON" nginx && exit 0 || exit $?
      ;;
   *)
      echo "Usage: $NAME {start|stop|restart|reload|force-reload|status|configtest}" >&2
      exit 1
      ;;
esac

exit 0

# 2、设置文件权限并增加到系统服务
# sudo chmod +x ./nginx
# sudo update-rc.d nginx defaults
# 3、启动nginx
# sudo /etc/init.d/nginx
```

```bash


/usr/local/nginx/sbin/nginx -v # 通过查看nginx的版本信息查看
/usr/local/nginx/sbin/nginx # 启动Nginx服务
ps -ef | grep nginx # 查看Nginx进程信息
# master process 主要读取和评估配置，维护worker process。
# worker process数量在配置文件中定义，负责请求的实际处理。Nginx主要基于试讲的模型和依赖操作系统的机制来高效的在worker process之间分配请求。

# 关闭Nginx服务
停止进程：kill-QUIT 主进程号
快速停止：kill-TERM 主进程号
强行停止：pkill -9 nginx

netstat -ntulp | grep 80 # 测试80端口


localhost:80 或 ip:80 # 浏览器访问测试会显示ngix的欢迎界面

# Nginx配置
Nginx安装目录：/usr/local/nginx
# 环境变量配置
vim /etc/profile
添加Nginx执行文件的路径
export PATH=$PATH:/usr/local/nginx/sbin
使立即生效：source /etc/profile
测试命令：nginx -v

```
