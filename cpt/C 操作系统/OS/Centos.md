


```bash
yum install zsh wget
```

# MySQL

```bash
# centos mysql deb-bundle安装

rpm -qa|grep mariadb # 卸载
rpm -e --nodeps 文件名
rpm -qa|grep mariadb # 是否卸载干净

mkdir mysql
wget https://downloads.mysql.com/archives/get/p/23/file/mysql-8.0.23-1.el7.x86_64.rpm-bundle.tar
tar -xvf XXXX.tar
# 必须安装
rpm -ivh mysql-community-common-8.0.16-2.el7.x86_64.rpm
rpm -ivh mysql-community-libs-8.0.16-2.el7.x86_64.rpm
rpm -ivh mysql-community-client-8.0.16-2.el7.x86_64.rpm
rpm -ivh mysql-community-server-8.0.16-2.el7.x86_64.rpm
# 非必须安装
rpm -ivh mysql-community-libs-compat-8.0.16-2.el7.x86_64.rpm
rpm -ivh mysql-community-embedded-compat-8.0.16-2.el7.x86_64.rpm
rpm -ivh mysql-community-devel-8.0.16-2.el7.x86_64.rpm
rpm -ivh mysql-community-test-8.0.16-2.el7.x86_64.rpm

yum install openssl-devel.x86_64 openssl.x86_64 -y
yum install perl.x86_64 perl-devel.x86_64 -y
yum install perl-JSON.noarch -y
yum -y install autoconf


# centos 安装后启动mysql服务
systemctl status mysqld
service mysqld stop
mysqld --initialize --console # 初始化数据库

# 目录授权
chown -R mysql:mysql /var/lib/mysql/

# 启动mysql服务
systemctl start mysqld
systemctl status mysqld

cat /var/log/mysqld.log # 查看临时密码
mysql -u root -p 回车键
alter USER 'root'@'localhost' IDENTIFIED BY '1234';
4、授权远程连接
命令：show databases;
命令：use mysql;
命令：select host, user, authentication_string, plugin from user;
命令：update user set host = "%" where user='root';
命令：select host, user, authentication_string, plugin from user;
命令：flush privileges;


```

# 最小化安装联网的问题

```bash
# 进入网络配置
root# cd /etc/sysconfig/network-scripts/
# 开启网卡启动
vi ifcfg-ens33   # 修改noboot=no 为 noboot=yes
# shift+zz关闭vim
# 重启网络服务
sudo service network restart
# 查看自己的ip
yum install net-tools


# 固定IP地址
# cd /etc/sysconfig/network-scripts/ 找到网卡
vi ifcfg-ens33
BOOTPROTO=static
ONBOOT=yes
IPADDR=192.168.1.112
NETMASK=255.255.255.0
GATEWAY=192.168.1.1

```




# 更换国内的centos源

```bash
# 备份原文件
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup

# 下载新配置文件并改名
cd /etc/yum.repos.d/
wget http://mirrors.163.com/.help/CentOS7-Base-163.repo
mv CentOS7-Base-163.repo CentOS-Base.repo

# 刷新缓存
yum makecache

# 更新系统
yum -y update

# 检查更新源情况
yum repolist

```



yum -y update ：升级所有包同时也升级软件和系统内核；
yum -y upgrade ：只升级所有包，不升级软件和系统内核。

查看软件包
  yum list all                     ##列出yum源仓库里面的所有可用的安装包 
  yum list installed               ##列出所有已经安装的安装包  
  yum list available               ##列出没有安装的安装包
安装软件
  yum install softwarename         ##安装指定的软件
  yum reinstall softarename        ##重新安装指定的软件
  yum localinstall 第三方software   ##安装第三方文件并且会解决软件的依赖关系
  yum remove  softwarename         ##卸装指定的软件
查找软件的信息  
  yum info software                ##查看软的信息
  yum search keywords              ##根据关键字查找到相关安装包软件的信息
  yum whatprovides filename        ##查找包含指定文件的相关安装包

对于软件组
   yum groups list             ##列出软件组
   yum groups install         ##安装一个软件组
   yum group remove           ##卸载一个软件组
   yum groups info            ##查看一个软件组的信息
查询源
   yum repolist  





# 关闭防火墙


查看防火墙状态：firewall-cmd --state 或者查看firewall服务状态：systemctl status firewalld
重新加载配置：firewall-cmd --reload
查看开放的端口：firewall-cmd --list-ports
关闭firewall：systemctl stop firewalld.service
重启firewall：systemctl restart firewalld.service
启动firewall：systemctl start firewalld.service
开启防火墙端口：firewall-cmd --zone=public --add-port=9000/tcp --permanent
关闭防火墙端口：firewall-cmd --zone=public --remove-port=9000/tcp --permanent
开机不启动防火墙: systemctl enable firewalld.service




