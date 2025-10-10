

https://www.mysql.com/
https://dev.mysql.com/downloads
https://dev.mysql.com/doc/
https://dev.mysql.com/doc/mysql-router/8.4/en/



https://mariadb.com/





https://www.runoob.com/mysql/mysql-tutorial.html



http://www.360doc.com/content/24/0311/20/84327566_1116866483.shtml MySQL基础
https://blog.csdn.net/m0_63758722/article/details/140888034 Mysql详细教程（建议收藏）
https://blog.csdn.net/m0_64192735/article/details/140469716 MySQL 教程（超详细，零基础可学、第一篇）
https://zhuanlan.zhihu.com/p/399359715 数据库-MySQL操作汇总
https://zhuanlan.zhihu.com/p/651953894 详解mysql/InnoDB索引/锁/事务/缓存池
https://blog.csdn.net/2301_80224556/article/details/142716150 【MySQL】数据库基础 原理介绍


MySQL必知必会 英 Ben Forta著 人民邮电出版社
数据库系统:面向应用的方法
数据库系统基础
navicat 




# mysql

数据库管理系统:(Database-Management System,DBMS)
数据库database:数据库是一些关联表的集合,数据库有数据表,数据表里才是数据
数据表table:表是数据的矩阵,看起来像一张完整的表格
模式(schema) :关于数据库和表的布局及特性的信息。 
字段:一列column,相同类型的数据
记录:一行row,一组完整的数据用来描述一个事物的各个属性
冗余:存储两倍的数据,冗余降低了性能,但是提高了数据的安全性

主键primary key:主键是惟一的,主要用来查询数据
外键:用来关联两个表
复合键:将多个列作为一个索引键,一般用于复合索引
索引:使用索引可快速访问数据库表中的特定信息。索引是对数据库表中一列或多列的值进行排序的一种结构。类似于书籍的目录
参照完整性:参照的完整性要求关系中不允许引用不存在的实体。与实体完整性是关系模型必须满足的完整性约束条件,目的是保证数据的一致性
表头:每一列的名称
值:行的具体信息
键:键的值在当前列中具有唯一性

事务:一组sql操作,要么都成功,要么都失败



```bash

# windows安装mysql
net start/stop mysql # 开启或关闭mysql服务
services.msc # 打开系统服务列表




```
```bash

# ubuntu安装配置mysql
# 安装服务器
sudo apt-get install mysql-server
sudo service mysql start # 启动MySQL
sudo service mysql stop # 停止MySQL
sudo service mysql restart # 重启MySQL
ps aux|grep mysql # 查看进程是否有mysql服务

# 客户端安装
sudo apt-get install mysql-client

```


https://www.cnblogs.com/nickchen121/p/11145123.html Mac安装MySQL

```bash
# Mac安装和配置
在~目录下的./.bash_profile文件末尾添加两行
export PATH=$PATH:/usr/local/mysql/bin
export PATH=$PATH:/usr/local/mysql/support-files
# 输入"source ~/.bash_profile"让配置文件生效
$ echo $PATH

sudo mysql.server stop # 停止MySQL服务
sudo mysql.server restart # 重启MySQL服务
sudo mysql.server status # 查看MySQL服务状态

```

```bash

# my.ini MySQL数据库配置文件
# C:\ProgramData\MySQL\MySQL Server 8.0\my.ini
# sudo vim /etc/mysql/mysqld.cnf
# macOS/usr/local/mysql/support-files/my-default.cnf
[mysqld]
# 设置3306端口
port=3306

# 设置mysql的安装目录
basedir="C:/Program Files/MySQL/MySQL Server 8.0/"
# 设置mysql数据库的数据的存放目录
datadir=C:/ProgramData/MySQL/MySQL Server 8.0\Data

# 允许最大连接数
max_connections=200
# 允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10
# 服务端使用的字符集默认为UTF8
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB

[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8

[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8


# Linux配置
/etc/mysql/mysql.cnf
Bind-address 默认是127.0.0.1服务器绑定
port 默认是3306,端口
datadir 默认是/var/lib/mysql 数据库目录
general_log_file 默认是/var/log/mysql/mysql.log 普通日志目录
log_error 默认是/var/log/mysql/error.log 表示错误日志


```

```bash

mysql --help
mysql -V # 版本
mysql -h 127.0.0.1 -P 3306 -u root -p passwd -D databaseName # 登录
> quit/exit/Ctrl+d 退出
mysqld --initialize --console # 初始化数据库


# 修改密码
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '新密码';
alter USER 'root'@'localhost' IDENTIFIED BY '1234';


# 修改字符集




# 数据库备份
mysqldump -uroot -p123456 > dump.sql # 导出数据

```



# 数据类型

原则:够用就行,尽量使用取值范围小的,而不用大的,这样可以更多的节省存储空间

https://www.cnblogs.com/-xlp/p/8617760.html 具体数据类型


对于图片、音频、视频等文件,不存储在数据库中,而是上传到某个服务器上,然后把媒体路径存储在数据库中

```sql

-- 整数
BIT 1位(八分之一字节) 只能存0或1 BIT(8)8个比特
TINYINT 1字节 unsigned 255  signed -128-127
SMALLINT 2字节 unsigned 65536  signed -32768~32767
MEDIUMINT 3字节 unsigned 16777215  signed -8388608~8388607
INT/INTEGER 4字节 unsigned 4294967295  signed
BIGINT 8字节 unsigned 18446744073709551615
NUMERIC
FIXED
DOUBLE PRECISION
REAL


-- 浮点
FLOAT 4字节 
DOUBLE 8字节
DECIMAL 表示浮点数,如decimal(5,2)表示共存5位数,小数占2位
DEC

-- 日期时间
DATE,4字节,如'2020-01-01'
TIME,3字节,如'12:29:59'
DATETIME,8字节,如'2020-01-01 12:29:59'
TIMESTAMP,4字节,如'1970-01-01 00:00:01'UTC~'2038-01-19 03:14:07' UTC
YEAR,1字节,如'2017'

-- 字符串
CHAR 表示定长字符串,大小255,如char(3),'ab'会补一个空格'ab '
VARCHAR 可变长度的字符串,大小255,如varchar(3),'ab'会存成'ab'
TEXT 字符串表示存储大文本,大小65536,当字符大于4000时推荐使用
VARCHAR 0-65535 字节 变长字符串                      
TINYBLOB 0-255字节 不超过 255 个字符的二进制字符串  
TINYTEXT 0-255字节 短文本字符串                    
BLOB 0-65 535字节 二进制形式的长文本数据
TEXT 0-65 535字节 长文本数据 大量的文本，原封不动的，博客文章源代码
MEDIUMBLOB 0-16 777 215字节 二进制形式的中等长度文本数据     
MEDIUMTEXT 0-16 777 215字节 中等长度文本数据                
LONGBLOB 0-4 294 967 295字节 二进制形式的极大文本数据         
LONGTEXT 0-4 294 967 295字节 极大文本数据                    
binary
varbinary
char varying
character
character varying
VARCHARACTER
NATIONAL CHAR
NATIONAL VARCHAR
NVARCHAR
NCHAR
LONG

-- 枚举和集合
enum把可能出现的结果列举出来,如性别,语言.索引值从1开始. -- 枚举类型
SET

-- 空间数据类型
bool
boolean
GEOMETRY, 2007
GEOMETRYCOLLECTION, 2007
LINESTRING, 2007
MULTILINESTRING, 2007
MULTIPOINT, 2007
MULTIPOLYGON, 2007
POINT, 2007
POLYGON, 2007

-- 其他类型
choosing
json
numeric
real

```

```sql

-- 数据属性
NULL
NOT NULL
DEFAULT
PRIMARY KEY
AUTO_INCREMENT
UNSIGNED
CHARACTERSET char_set_name 指定字符集


```



# MySQL语句

baidu:结构化查询语言
DQL数据查询语言: 对数据库中的数据进行查询 select
DML数据操作语言: 操作数据库中所包含的数据增删改 insert update delete
DDL数据定义语言: 创建和删除数据库对象等 create drop alter
DCL数据控制语言: 控制数据库组件的存取许可、存取权限 grant commit rollback
TCL事务控制语言: 


数据库约束
在表中为了更加准确的存储数据,保证数据的正确有效,在创建表的时候,为表添加一些强制性的验证,包括数据字段的类型,约束
主键 primary key:物理上存储的顺序
自动增长 AUTO_INCREMENT
非空 not null:此字段不允许填写空值
唯一unique:此字段的值不允许重复
默认default:当不填写此值时会使用默认值,如果填写时以填写为准
外键foreign key:对关系字段进行约束,当为关系字段填写值时,会到关联的表中查询此值是否存在。外键约束虽然可以保证数据的有效性,在数据crud（增改删查）时,会降低数据库的性能,不推荐使用,建议一般在逻辑层进行控制


表的属性
注释 COMMENT
字符集 CHARSET
引擎
常见的9种存储引擎类型 InnoDB MyISam
SHOW VARIABLES LIKE '%STORAGE%'; -- #MySQL存储引擎类型


```sql
--这是单行注释
/*
这是多行注释
*/

-- 不能使用关键字命名库名,表名,列名和其他数据库对象,关键字必知必会附录E


-- 数据库操作
-- 数据库数据存放在/var/lib/mysql文件夹下
-- 如果想重命名一个数据库,最好的办法是重新建立一个新的数据库
SHOW CREATE DATABASE test; -- 查看建库语句
/*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */
-- 默认字符集设置utf8mb4 字段utf8mb40900aici 默认加密是'N'

SHOW DATABASES; -- 显示所有的数据库列表
USE test; -- 使用数据库
CREATE DATABASE test; -- 创建数据库
CREATE DATABASE test charset=utf8; -- 指定字符集
DROP DATABASE test; -- 删除数据库




-- 数据表操作
SHOW CREATE TABLE students; --显示创建表结构
SHOW COLUMNS FROM tt; -- 查看表的结构
DESC tt; -- 同上,查看表结构


SHOW TABLES test; -- 显示库中所有表

-- 创建表,指定字段(字段 类型 约束[,字段 类型 约束])
-- 两个字段,并且指定类型
-- 约束的内容
-- primary key -- 主键
-- not null -- 不为空
-- auto_increment -- 自动增长
-- default 0 -- 默认值
CREATE TABLE test(id int, name varchar(30));
CREATE TABLE tpid( -- 设置一个id主键
  id int unsigned primary key not null auto_increment,
  name varchar(30)
);
-- 例子
CREATE TABLE students(
  id int unsigned not null auto_increment primary key,
  name varchar(30),
  age tinyint unsigned default 0,
  high decimal(5,2),
  gender enum("男","女","中性","保密") default "保密",
  cls_id int unsigned
);


CREATE TABLE `students` (
  `id` int unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(30) DEFAULT NULL,
  `age` tinyint unsigned DEFAULT '0',
  `high` decimal(5,2) DEFAULT NULL,
  `gender` enum('男','女','中性','保密') DEFAULT '保密',
  `cls_id` int unsigned DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci         
1 row in set (0.00 sec)
-- ENGINE默认引擎
-- AUTO_INCREMENT自动增长的值

ALTER TABLE students RENAME TO stu; -- 修改表名
DROP TABLE tt; -- 删除表


-- 修改已有的表结构
ALTER TABLE students ADD birthday datetime; -- 添加字段
ALTER TABLE students DROP birthday; -- 删除字段

-- 重命名字段 change 原名 新名 类型及约束
ALTER TABLE students CHANGE birthday birth datetime not null;
ALTER TABLE students CHANGE birthday birth date default "2000-01-01";

-- 修改字段 modify 字段名 类型及约束
ALTER TABLE students MODIFY birth date not null;








-- 数据行操作
-- 插入数据 students(id,name,age,high,gender,cls_id);
-- 这里省略字段名,值必须按照先后顺序依次全部填写
INSERT INTO students VALUES(0,"老王",18,175.00,"男",2);
 -- 主键可以插入0/null/default,都会自动增长
 -- gender枚举类型可以填下标1/2/3/4代替字符串
 
-- 插入数据指定字段,可以为null和有默认值的字段可以不填
INSERT INTO students 
  (id,name,age,high,gender,cls_id)
  VALUES
  (0,"老王",18,175.00,"男",2);
  
-- 多行数据插入,
INSERT INTO students VALUES(0,"老李",18,175.00,"男",2),(0,"老赵",18,175.00,"男",2);
INSERT INTO students (name, gender) VALUES("老李",1),("老赵",1);



-- 更新数据
UPDATE students SET gender=1; -- 慎用,更改表中所有数据
UPDATE students SET gender=2 WHERE name="老李";
UPDATE students SET gender=2 WHERE id=3; --主键确定唯一值
UPDATE students SET gender=2,age=33 WHERE id=3;



-- 删除数据
DELETE FROM students; -- 慎用,清空数据表
DELETE FROM students WHERE name="老王"; -- 条件删除
-- 在真实使用环境中,使用一个字段来表示数据是否作废,而不是真正的删除这些数据
ALTER TABLE students ADD is_delete bit default 0; -- 添加软删除
UPDATE students SET is_delete=1 WHERE id=6;




```






```sql

-- 待整理
ALTER TABLE tb_temp01 ADD CONSTRAINI pk_temp_id PRIMARY KEY tb_temp01(`id`);#给表tb_temp01添加主键

CREATE TABLE [IF NOT EXISTS] 表名 (
  字段1 数据类型 [字段属性|约束][索引][注释],
  ......
  字段n 数据类型 [字段属性|约束][索引][注释]
) [表类型][表字符集][注释];
CREATE TABLE `student` (
  `student_no` INT ( 4 ) PRIMARY KEY NOT NULL auto_increment COMMENT '学号', 
  `student_name` VARCHAR ( 50 ) COMMENT '学生姓名',
	`identity_card` CHAR(18) UNIQUE KEY COMMENT '身份证号',
	`gender` char(2) DEFAULT '男' COMMENT '性别'
) COMMENT='学生表' CHARSET=utf8mb4;



主键所在的表是主表。
外键所在的表是从表。
主表的主键是从表的外键
主表是独立的，表中字段的值不依赖与任何它表
从表中某个（某些）字段的值依赖于它表字段的值

如:课程表有一个教师id，为教师的主键，为课程的外键，所以教师是主表，课程表为从表。
desc tb_temp01; -- 给表tb_temp01添加主键
alter table tb_temp01 add CONSTRAINT pk_temp_id PRIMARY KEY tb_temp01(`id`);

create table tb_temp02(
	id int(4) PRIMARY KEY NOT NULL,
	name varchar(20) not null,
	t_id int(4) not null
);
desc tb_temp02; -- 给从表添加外键
alter table tb_temp02 add CONSTRAINT fk_id FOREIGN KEY (`t_id`) REFERENCES `tb_temp01`(`id`);

主键:主关键字是表中的一个或多个字段，它的值用于唯一地标识表中的某一条记录。又可称为主键、主码，其列不能包含空值。主关键字是可选的，并且可在 CREATE TABLE 或 ALTER TABLE 语句中定义。

公共关键字:如果两个关系中具有相容或相同的属性或属性组，那么这个属性或属性组被称为这两个关系的公共关键字。

外键:如果公共关键字在一个关系中是主关键字，那么这个公共关键字被称为另一个关系的外键。由此可见，外键表示了两个关系之间的相关联系。外键又称作外关键字。

外键的作用:保持数据一致性，完整性，主要目的是控制存储在外键表中的数据，使两张表形成关联。外键只能引用外表中的列的值或使用空值。

主表、从表:以另一个关系的外键作主关键字的表被称为主表，具有此外键的表被称为主表的从表。主键表是被引用的表，外键表是引用其他表的表。

实体完整性:实体完整性要求每一个表中的主键字段都不能为空或者重复的值。实体完整性指表中行的完整性，要求表中的所有行都有唯一的标识符，称为主关键字。主关键字是否可以修改，或整个列是否可以被删除，取决于主关键字与其他表之间要求的完整性
检查违约:
（1）检查主码值是否唯一，如果不唯一则拒绝插入或修改。
（2）检查主码的各个属性是否为空，只要有一个为空就拒绝插入或修改。
从而保证了实体完整性。


```






# 数据查询

```sql
-- 查询数据
SELECT * FROM students; -- 选择数据库查询所有数据
SELECT * FROM test.tt; -- 数据库库下的数据表的所有数据
SELECT id,name,gender FROM students; -- 指定字段查询
SELECT students.name,students.gender FROM students; --指定数据表和字段

SELECT name as 姓名,gender as 性别 FROM students; -- 字段别名
SELECT s.name, s.gender FROM students as s; -- 表的别名
SELECT test.user.id AS i,test.user.name AS n FROM test.user; -- 各种指定别名

SELECT DISTINCT gender FROM students; -- 消除重复行

-- WHERE条件查询,> < >= <= = !=
SELECT * FROM students WHERE id>6; -- 比较运算符>
SELECT name,age FROM students WHERE id>6; -- 显示的字段可以不同于查询的条件

-- 逻辑查询 and or not
SELECT name,age FROM students WHERE age>18 and age<28;

-- 模糊查询,很少使用 %替换零个或多个 _替换1个
SELECT name FROM students WHERE name="小";
SELECT name FROM students WHERE name LIKE "小%"; -- 小字开头的值 "%小%"名字包含小字
SELECT name FROM students WHERE name LIKE "__";-- 两个字的名字
SELECT name FROM students WHERE name LIKE "___";-- 三个字的名字
SELECT name FROM students WHERE name LIKE "__%";-- 至少两个字的名字

-- 正则查询
-- .   : 匹配任意单个字符
-- *   : 匹配0个或多个前一个得到的字符
-- []  : 匹配任意一个[]内的字符,[ab]*可匹配空串、a、b、或者由任意个a和b组成的字符串。
-- ^   : 匹配开头,如^s匹配以s或者S开头的字符串。
-- $   : 匹配结尾,如s$匹配以s结尾的字符串。
-- {n} : 匹配前一个字符反复n次。
SELECT name FROM students WHERE name RLIKE "^周.*";-- 周开头的值 "^周.*伦$"周开头伦结尾中间随意

-- 范围查询
-- in(1,3,8)表示在一个非连续的范围内
SELECT name FROM students WHERE age IN(12,18,34);
-- not in(1,3,8)表示在一个不在 非连续的范围内
SELECT name FROM students WHERE age NOT IN(12,18,34);
                          WHERE age BETWEEN 18 AND 34;-- between and 表示在一个连续的范围内
                          WHERE age NOT BETWEEN 18 AND 34; -- 表示不在一个连续范围内
                          WHERE age NOT (BETWEEN 18 AND 34); -- 错误,这里不能加括号
                          WHERE NOT age BETWEEN 18 AND 34;-- 两截,NOT跟着范围查询

-- 空判断 is null,  is not null
SELECT name FROM students WHERE height IS NULL;-- 空值
SELECT name FROM students WHERE height IS NOT NULL;-- 不为空

-- order by支持多个字段排序
-- 数据排序,DESC降序,ASC升序
SELECT * FROM students ORDER BY age;
SELECT * FROM students ORDER BY age ASC/ DESC;
SELECT * FROM students WHERE gender=1 ORDER BY score;
SELECT * FROM students ORDER BY age ASC, id DESC; -- 先按照age排序,后按照id排序
SELECT * FROM students ORDER BY age ASC, height DESC;

-- 聚合函数,一般会得出一个结论
SELECT COUNT(*) FROM students WHERE gender=1; -- count()总数
SELECT MAX(age) FROM students WHERE gender=2; -- max()最大值
SELECT MAX(age) FROM students WHERE gender=2; -- min()最小值
SELECT SUM(age) FROM students; -- sum()总和
-- avg()平均值,银行为了精确存储数据,可以先乘以100再存储,计算完成之后再还原小数点
SELECT AVG(age) FROM students;
SELECT SUM(age)/ COUNT(*) FROM students;-- 与AVG(age)效果相同
SELECT ROUND((SUM(age)/COUNT(*)),2) FROM students; -- round()保留2位小数,四舍五入

-- 分组,要和聚合函数一起用
SELECT gender,COUNT(*) FROM students GROUP BY gender;-- 各性别的人数
SELECT gender,AVG(age) FROM students GROUP BY gender;-- 各性别的平均年龄
-- group_concat()
SELECT gender,GROUP_CONCAT(name) FROM students GROUP BY gender;-- 各性别人的名字
SELECT gender,COUNT(*) FROM students WHERE gender=1 GROUP BY gender;-- 男性的人数
SELECT gender,GROUP_CONCAT(name) FROM students WHERE gender=1 GROUP BY gender;-- 男性的名字
SELECT gender,GROUP_CONCAT(name,"_",age," ",id) FROM students WHERE gender=1 GROUP BY gender;-- 男性的名字,年龄,id
-- having
SELECT gender,GROUP_CONCAT(name),avg(age) FROM students GROUP BY gender HAVING AVG(age)>30;-- 平均年龄超过30的性别和其中的人
SELECT gender,GROUP_CONCAT(name) FROM students GROUP BY gender HAVING COUNT(*)>2;-- 性别中人数多于2的信息

-- 分页



```


# 数据库函数

https://www.cnblogs.com/luxd/p/9916677.html 数据库函数
https://www.cnblogs.com/xuedognqing/p/5080057.html MySQL函数大全

```sql
-- 数学函数
select ABS(); -- 绝对值
-- 字符串函数
-- 日期时间函数
select NOW(); -- 显示当前时间
-- 条件判断函数
-- 系统信息函数
SELECT VERSION(); -- 显示版本信息
SELECT DATABASE(); -- 显示当前数据库名
SELECT USER(); -- 显示当前用户名
SELECT STATUS(); -- 显示服务器状态
SELECT VARIABLES(); -- 显示服务器配置变量
-- 加密函数
-- 格式化函数

```

# 视图

数据库发生变化,程序没有变化,这时相应的需要原先的表来使用,视图则可以生成程序需要的表.
视图的表数据来自于数据库数据.
视图是对若干张基本表的引用,一张虚拟表,查询语句执行的结果.修改视图数据,其实是对数据库数据的修改
视图是用来查询的,修改删除不好使.

```sql


-- 创建视图
CREATE VIEW u2 AS
SELECT
	t_user.id AS id, 
	t_user.user_name AS user_name
FROM
	t_user

--示例
-- 查询三张表的信息,主表是商品信息,两张副表代表分类和品牌
SELECT * FROM goods AS g 
LEFT JOIN goods_cates AS c ON g.cate_id=c.id 
LEFT JOIN goods_brands AS b ON g.brand_id=b.id;
-- 用具体字段显示上面的结果
SELECT g.*, c.name AS cate_name, b.name AS brand_name FROM goods AS g 
LEFT JOIN goods_cates AS c ON g.cate_id=c.id 
LEFT JOIN goods_brands AS b ON g.brand_id=b.id;
-- 创建所需的视图
CREATE VIEW v_goods_info AS
SELECT g.*, c.name AS cate_name, b.name AS brand_name FROM goods AS g 
LEFT JOIN goods_cates AS c ON g.cate_id=c.id 
LEFT JOIN goods_brands AS b ON g.brand_id=b.id;
-- 查询视图信息
SHOW TABLES;
DESC v_goods_info;
SELECT * FROM v_goods_info;
DROP VIEW v_goods_info;








```



# 事务

一般来说,事务是必须满足4个条件（ACID）::原子性（Atomicity,或称不可分割性）、一致性（Consistency）、隔离性（Isolation,又称独立性）、持久性（Durability）。

原子性:一个事务（transaction）中的所有操作,要么全部完成,要么全部不完成,不会结束在中间某个环节。事务在执行过程中发生错误,会被回滚（Rollback）到事务开始前的状态,就像这个事务从来没有执行过一样。
一致性:在事务开始之前和事务结束以后,数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则,这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。
隔离性:数据库允许多个并发事务同时对其数据进行读写和修改的能力,隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别,包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。
持久性:事务处理结束后,对数据的修改就是永久的,即便系统故障也不会丢失。








# Connector/Python

```python

# 创建Connection连接
conn = connect(host='localhost', port=3306, user='root', password='mysql', database='python1', charset='utf8')
# 得Cursor对象
cs = conn.cursor()
# 更新
# sql = 'update students set name="刘邦" where id=6'
# 删除
# sql = 'delete from students where id=6'
# 执行select语句,并返回受影响的行数:查询一条学生数据
sql = 'select id,name from students where id=7'
# sql = 'SELECT id,name FROM students WHERE id=7'
count = cs.execute(sql)
# 打印受影响的行数
print(count)


```




