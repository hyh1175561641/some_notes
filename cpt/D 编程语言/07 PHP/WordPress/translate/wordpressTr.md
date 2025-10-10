



# Handbook
https://developer.wordpress.org/advanced-administration/

Wordpress 高级管理员手册
WordPress Advanced Administration Handbook

TOPICS 话题 题目标题

欢迎来到Wordpress 高级管理员手册
Welcome to the WordPress Advanced Administration Handbook! 

这里你将寻找到Wordpress 高级文档
Here you will find WordPress advanced documentation.
使用内容菜单 在左侧的导航顶部
Use the “Contents” menu on the left to navigate topics.
navigate 导航

为什么 高级管理员手册
Why Advanced Administration?
不是所有的Wordpress使用者 都不得不 了解科技细节, 所以这个文档里面 不应该 出现任何一个 并且开发者不必知道 高级系统配置
Not all users who use WordPress have to know about technology, and therefore in its documentation should not appear either, and developers do not have to know certain advanced system configurations.
technology 科技
therefore 因此 因而 所以
appear 出现
either 任何一个
developers 开发者
certain 确信无疑
advanced 先进的 高级的
configurations 布局结构构造

With this in mind, all the more technically complex documentation has been included in this documentation so that it can be used by more or less technical people.
mind
technically
complex
technical


Where can I be involved?
The Documentation Team meets in the WordPress Slack, in the #docs channel. The conversations are in English. Check out the WordPress Meeting calendar for the current schedule.

Advanced Administration Handbook managers
This documentation is managed by @javiercasares, @lucp, and @milana_cap. Also, the Documentation Team and Hosting Team are involved in this.

Note:If you’re interested in improving this handbook, check the Github Handbook repo, the Documentation Issue tracked, or leave a message in the #hosting-community channel at WordPress Slack.

Top ↑

Changelog
2023-01-15: Minor fixes, and reviewed.
2022-08-16: First version.






# Before You Install
https://developer.wordpress.org/advanced-administration/before-install/


安装WordPress之前，你需要检查你的虚拟主机提供商是否提供必要的软件和条件。此外，你必须有登陆服务器的账号和一些工具

服务器端需求
PHP7.4 MySQL5.7 HTTPS
有关您的虚拟主机的详细要求列表，参考官方需求页面和服务器环境页面

本地需求

## Creating Database for WordPress

https://developer.wordpress.org/advanced-administration/before-install/creating-database/

如果你安装WordPress在你自己网站服务器上，跟随者下面的指示之一去创建你的WordPress数据库和用户账号。

使用MySQL客户端
你可以创建MySQL用户和数据库快速简单，通过在shell中运行mysql。这个语法展示在下面并且美元符号是命令提示符。
```mysql
mysql准备
CREATE DATABASE databasename;
CREATE USER "wordpressusername"@"hostname" IDENTIFIED BY "password";
GRANT ALL PRIVLEGES ON databasename.* TO "wordpressusername"@"hostname";
FLUSH PRIVILEGES;
EXIT
```

The example shows:这个例子展示了:

这个root也是adminusername。
It is a safer practice to choose a so-called “mortal” account as your mysql admin, so that you are not entering the command “mysql” as the root user on your system. 
(Any time you can avoid doing work as root you decrease your chance of being exploited.) 
The name you use depends on the name you assigned as the database administrator using mysqladmin.

wordpress或blog是好值对数据库名字来说。

wordpress is a good value for wordpressusername but you should realize that, since it is used here, the entire world will know it, too.

hostname will usually be localhost. 
If you don’t know what this value should be, check with your system administrator if you are not the admin for your WordPress host. 
If you are the system admin, consider using a non-root account to administer your database.

password should be a difficult-to-guess password, ideally containing a combination of upper- and lower-case letters, numbers, and symbols. 
One good way of avoiding the use of a word found in a dictionary is to use the first letter of each word in a phrase that you find easy to remember.

If you need to write these values somewhere, avoid writing them in the system that contains the things protected by them. 
你需要记住值用于数据库名称 wordpress用户名 主机名 密码
Of course, since they are already (or will be shortly) in your wp-config.php file, there is no need to put them somewhere else, too.当然，自从他们


## How to install WordPress

