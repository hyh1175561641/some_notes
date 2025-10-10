

# wordpress 环境搭建

https://developer.wordpress.org/advanced-administration/before-install/
PHP 7.4 or greater
MySQL 5.7 or MariaDB 10.3 or greater

https://downloads.mysql.com/archives/community/


https://zephyr.us-themes.com/
https://zephyr.us-themes.com/
https://wp-themes.com/astra/

```
apt-get update -y
apt-get upgrade -y

apt-get install vsftpd
apt-get install fcitx
apt-get install fcitx-googlepinyin

systemctl enable mysql
systemctl enable apache2.service
systemctl enable ssh.service

apt-get install phpmyadmin

```

select user,password from user;
alter user 'root'@'localhost' identified by 'kali';

cd /var/www/html
sudo chown www-data:www-data -R *
sudo chmod 755 -R *

/etc/php/php.ini
upload_max_filesize = 100M
post_max_size = 100M
max_execution_time = 300


wp-config.php
83行 define( 'FS_METHOD','direct');
define('FTP_USER', 'USERNAME');
define('FTP_PASS', 'PASSWORD');
define('FTP_HOST', 'FTP.EXAMPLE.COM');

define('WP_HOME', 'http://localhost');
define('WP_SITEURL', 'http://localhost');


# docker环境搭建

```md

docker pull wordpress
docker run -it --name wordpress -p 80:80 -d wordpress

docker ps

```


# http://bt.cn

CentOS 7.X
nginx 1.22
apache 2.4
mysql 5.7
pure ftp 1.0.49
php 7.4
phpmyadmin 5.2



# 购买的插件和主题

NG版，永久激活，不包更新
授权版，每年缴费，一直更新


ASTRA PRO主题

Astra Pro基础套餐
Essential Bundle套餐
Growth Bundle套餐，是最高阶的

8元包括
1.上传至主题启用astra4.5.0.zip
2.上传至插件启用astra pro4.5.0.zip
3.上传至插件启用astra-premium-sites3.4.4.zip
4.赠送---上传至插件启用 Astra Portfolio 1.11.7.zip

35元包括
Astra Pro 主题升级
Premium Template
WP Portfolio
Ultimate Addons for Elementor
Ultimate Addons for Beaver Builder
Schema Pro
Convert Pro

astra-premium-sites.zip (Premium Starter Templates)
astra-portfolio.zip (WP Portfolio)
astra-addon-pro.zip (Astra Pro)

wp-schema-pro.zip
ultimate-addon-bb.zip
ultimate-addon-ael.zip
spectra-pro.zip
convertpro.zip
convertpro-addon.zip


中英文切换插件 Polylang WPML



# SSL证书

https://help.aliyun.com/zh/ssl-certificate/user-guide/apply-for-a-single-domain-dv-certificate-for-free-trial?spm=a2c4g.11186623.0.i2

https://help.aliyun.com/zh/ssl-certificate/user-guide/installation-overview#concept-95505-zh

https://neijuli.cn/archives/21228.html/page/5




问你个问题,老板想让我开发一个控制面板,能够替代连接存储服务器的功能,但是我不知道用什么语言什么函数库,调用啥接口.

mac电脑操作步骤是 访达->前往->连接服务器->输入存储地址(smb://192.168.0.x)->账号认证 https://zhuanlan.zhihu.com/p/658896310
Windows操作步骤是 https://blog.csdn.net/qianshuiliyu/article/details/129162094 (其中访问的功能)



