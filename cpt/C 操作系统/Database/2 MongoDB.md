









https://www.mongodb.com
https://docs.mongodb.com/manual/
https://www.mongodb.com/try/download/community-edition
https://www.runoob.com/mongodb/mongodb-tutorial.html


relational   关系型(数据库),相关的,亲属的


# MongoDB

MongoDB是用C++语言编写的非关系型数据库。高性能、易部署、易使用,存储数据十分方便

NoSQL非关系型数据库
关系型relational数据库有各种相互关联的表格
非关系型数据库可以想象成一个json格式的大字典
MySQL拓展性差,大数据下IO压力大,表结构更改困难
MongoDB易拓展,大数据量高性能,灵活的数据模型,高可用 https://www.cnblogs.com/shizhiyi/p/7750530.html（HA  High Availability）
缺点：数据重复存储,占用大量的空间



```bash
# MongoDB 偶数版是稳定版,奇数版为开发版
# win安装
msi安装包安装
https://www.mongodb.com/try/download/community-edition

# ubuntu安装
sudo apt-get install -y mongodb-org

# 源码安装
https://fastdl.mongodb.org/src/mongodb-src-r6.0.3.tar.gz
tar zxvf mongodb-linux-ubuntu.tgz
sudo mv -r mongodb-linux-ubuntu/  /usr/local/mongodb
Export PATH=/usr/local/mongodb/bin:$PATH
sudo mongod --config /usr/local/mongodb/mongod.conf

## 配置 
sudo service mongodb start
sudo service mongodb stop
sudo service mongodb restart
ps ajx | grep mongod
/etc/mongod.conf
Port : 27017
日志：/var/log/mongodb/mongod.log
mkdir ~/data
mongod --dbpath ~/data

# 启动服务 在指定位置创建数据库数据,指定端口号
mongod --dbpath ~/data --port 27017
# 命令行
./mongo -h
mongosh # 6.0版本以上用

```

# 概念
Database: 就是一组collection,类似关系型数据库的库,单个实例可以支持多个库,每一个db都有自己的集合和权限.
Collection: 集合,就是一组document,类似关系型数据库的一个表.没有格式要求,用来存放文档的.
Document: 是MongoDB中数据的基本单位,类似关系型数据库表的行,但是比行要复杂多.也类似于JS中的对象,在MongoDB中每一条数据都是一个文档.存储和操作的内容都是文档
Key是document中的键的名称,类似关系型数据库中表的列,但是这个key不想关系数据库那样子被限定.
每个document都有一个特殊的键 _id ,这个键值是唯一的,相当于关系型数据库中的表的主键.

MongoDB存储的数据库是以BSON（Binary JSON）的格式的,BSON是一种二进制的json数据。通过BSON,MongoDB可以方便地存储无模式（scheme）数据.

# 数据类型

Object ID ：文档的id
String： 字符串,最常用,必须是utf-8
Boolean：布尔值,true 或者false
Integer：整数
Double：浮点数
Arrays：数组或者列表,多个值存储到一个键
Object：用于嵌入文档,即一个值为一个文档
Null：存储null值
Timestamp：时间戳
Date：存储当前日期或时间unix时间格式


Double	1	“double”	
String	2	“string”	
Object	3	“object”	
Array	4	“array”	
Binary data	5	“binData”	
Undefined	6	“undefined”	Deprecated.
ObjectId	7	“objectId”	
Boolean	8	“bool”	
Date	9	“date”	
Null	10	“null”	
Regular Expression	11	“regex”	
DBPointer	12	“dbPointer”	Deprecated.
JavaScript	13	“javascript”	
Symbol	14	“symbol”	Deprecated.
JavaScript (with scope)	15	“javascriptWithScope”	
32-bit integer	16	“int”	
Timestamp	17	“timestamp”	
64-bit integer	18	“long”	
Decimal128	19	“decimal”	New in version 3.4.
Min key	-1	“minKey”	
Max key	127	“maxKey”

ObjectId
具有12字节的唯一标识。MongoDB中,每条记录都有一个类似关系型数据库主键标识的_id字段来标识此条记录,如果没有设定文档记录的_id值,则通过ObjectId来生成_id。其具体组成如下：

4字节,Unix的时间戳
5字节,随机数值
3字节,计数器,从随机的起始值开始
String
BSON的字符串编码为UTF-8,UTF-8可以更好地支持各种语言文字,一般每种编程语言的MongoDB驱动会帮助处理字符串编码以符合要求。

Timestamps
BSON中的时间戳比较特别,他并不能直接对应到Date类型,而是通过如下方式组织64位数据：

前32位是从Unix纪元（1970.1.1）开始计算到现在时间的秒数
后32位是一秒内的操作序数
在一个单实例MongoDB中,时间戳是唯一的。如果对一个一级timestamp类型字段插入了空值,MongoDB会将空值替换成当前时间戳（从2.6版开始,之前的版本只会替换前两个字段）。
Date
BSON日期是一个64位的字段类型,存放了从Unix纪元（1970.1.1）开始计算的毫秒数计数时间。BSON日期是有符号类型的,负值代表1970.1.1之前的时间。



# 基本命令

```bash
# 数据库操作
show databases # 显示所有数据库
show dbs # 简写
use test # 切换到dddd数据库
db # 显示当前数据库
db.dropDatabase() # 删除当前数据库

# 集合操作
# 手动创建集合,也可以不创建集合,插入第一条数据自动创建集合
db.createCollection(NAME,OPTIONS) # 写上名字和选项
db.createCollection("stu",{capped:true,size:10})
  # capped选项false表示不设置上限,true表示设置上限
  # size当capped值为true时,表示上限大小,当文件到达上限时,覆盖之前的数据,单位是字节
show collections # 显示集合
# 删除集合
db.stu.drop()








# 文档的CRUD
# 添加数据
# mongodb不需要创建数据库数据表,只要有操作就自动建立库和表
db.stus.insert({name:'aaa'}) # 已废弃
db.stus.insertOne() # 添加一条数据
db.stus.insertOne({name:'zhangsan',age:18})
db.stus.insertOne({_id:"hello",name:'zhangsan',age:18}) # 自己指定主键
db.stus.insertMany() # 添加数组,多条数据
db.stus.insertMany([{name:'zhangsan',age:18},{name:'lisi',age:27}])

# 修改删除数据
db.stus.update({name:"沙和尚"},{age:28}); # 完全替换符合条件的数据
db.stus.updateOne({name:"沙和尚"},{$set:{age:28}}) # 修改指定属性
db.stus.updateOne({name:"沙和尚"},{$unset:{age:28}}) # 删除指定属性
db.stus.updateMany({name:"沙和尚"},{$set:{age:28}},{multi:true}) # 修改所有符合的属性,多个修改
db.stus.replaceOnt() # 替换一个文档

# 删除数据





# 查询数据
# _id是一个ObjectId()对象,根据时间戳生成,总共24长度的16进制字符串,对应12字节,long类型只有8字节64位,长度16
db.stus.find() # 查询所有结果
db.stus.find({}).count/length() # 显示总数
db.stus.find({name:"aaa"})[1].name # 查询符合条件的结果,并显示值
db.stus.findOne() # 查询符合条件的第一个结果
db.stus.findOne().name # 查询结果的值





```















