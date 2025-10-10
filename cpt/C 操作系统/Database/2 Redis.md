

unstable 不稳定的,动荡的,异变的(官网download)
stable 稳定的
refuse 拒绝
refused 遭到拒绝的
connection 连接,关系,人脉
connection refused 连接被拒绝(Redis连接未指定端口)
Strict  严格的,绝对的,精确的,详细的


https://redis.io
http://www.redis.cn
http://redis.net.cn
https://www.runoob.com/redis/redis-tutorial.html
https://www.jianshu.com/p/56999f2b8e3b
http://doc.redisfans.com/index.html

《Redis实战》[美]Josiah L. Carlson 人民邮电出版社 ISBN 978-7-115-40284-4 中文支持网站和源代码 http://redisinaction.com


# Redis

Redis(Remote Dictionary Server ),即远程字典服务
Redis是一种NoSQL技术,它的性能十分优越,可以支持每秒几十万次的读写操作,性能远超数据库,并且还支持集群,分布式,主从同步等配置,原则上可以无限扩展,让更多的数据存储在内存中,更让人欣慰的是它还支持一定的事务能力,这保证了高并发的场景下数据的安全和一致性
NoSQL (not only SQL)技术：不支持SQL语法,存储结构都是采用key-value形式,没有通用的语言.这是一种基于内存的数据库,且提供一定的持久化功能.Redis和MongoDB是当前使用最广泛的NoSQL
关系型数据库和NoSQL数据库的比较：适用的场景不同,sql数据库适合用于关系特别复杂的数据查询场景,nosql则反之.SQL对事务的支持非常完善,而NoSQL基本不支持事务,两者不断的取长补短,呈现融合趋势.事务,一组sql操作,要么都成功,要么都失败

Redis是远程的：有客户端和服务端两个部分,可以部署在不同的两个机器上,可以使用自定义的协议进行传输和交互.通常说的Redis是指服务端,特殊情况才说Redis客户端.

Redis是基于内存的：所有的数据和结构都存储在内存中,操作非常高速,性能远远优于硬盘MySQL,比较吃内存的软件.支持数据持久化,可以将内存中的数据保存在磁盘中,重启的时候可以再次加载进行使用

Redis是非关系型数据库：关系型数据库在存储之前必须定义好数据字典,后续的存储数据按照数据字典进行存储,而Redis不需要定义数据字典.支持主从模式的数据备份,即master-slave模式

应用场景：
1)当做缓存 (ehcache/memcached)：当系统接口速度慢的时候,缓存某些数据,再次使用数据的时候,就不需要再使用MySQL的操作了,直接到Redis缓存中取数据,这是提升系统性能最常用的方法之一
2)当做队列：Redis提供一个list结构,pop和push操作,Redis保证这两个操作是原子性,基于这个特性,可以把Redis当做队列来使用
3)当做数据存储：直接把Redis当做数据存储来使用,所有的增删改查都直接从Redis中操作.这样操作的基础是因为有非常完备的硬盘持久化机制,有两个配合的机制,可以定期持久化到硬盘中,这样就保证了Redis数据的完整性和安全性
4)历史: 在Redis in Active这本书中,Redis的发明者Salvatore Sanfilippo.因为找不到合适的工具来解决手头上的问题而发明的



安装与配置

```bash
# 源码安装：在linux系统中,下载源码,预装软件gcc  tcl (是一门语言)
# 服务端的安装
`tar -xf redis-x.x.x.tar.gz`或`tar -zxvf redis-x.x.x.tar.gz`
如果讲究的话,sudo mv ./redis-x.x.x  /usr/local/redis
cd redis目录
make
这里可以make test测试依赖
在src文件下有redis-cli和redis-server,还有redis-benchmark性能测试工具,redis-check-aof AOF文件修复工具,redis-check-rdb RDB文件检索工具(Redis持久化文件就是RDB文件)
sudo make install,将生成的二进制文件放到/usr/local/bin目录下
which redis-server 检测命令的位置
redis/src/redis.conf 配置文件
拷贝到/home/user/config/redis/redis.conf或/etc/redis目录下
ls /usr/local/bin redis命令放置的地方


# 修改配置文件redis.conf
`bind 127.0.0.1` 绑定ip
修改文件的配置项`daemonize no/yes`前台启动no还是yes后台启动,是否以守护进程yes运行
`port 6379`修改成7200,启动的端口
`dbfilename dump.rdb`数据持久化写入的文件
`dir /var/lib/redis`数据文件存储路径,记得创建好文件
`logfile /var/log/redis/redis-server.log`日志文件
`database 16`数据库默认有16个
`slaveof`主从复制,类似于双机备份,搭建主从需要
还可以设置密码 https://www.cnblogs.com/aspsea/articles/10964606.html

requirepass 自定义密码
bind 0.0.0.0 设置成允许所有IP访问
protected-mode no 关闭保护模式


```


```bash
# 启动服务端
启动服务端命令：redis-server redis-conf
ps aux|grep redis-server 检测启动项
如果可以使用sudo service redis start/stop/restart启动和停止最好
kill -9 pid

```

```bash
# 客户端
which redis-cli
接下来使用redis-cli登录redis-server
如果直接登录redis-cli则报错,Connection refused,默认端口是6379,默认ip是本机
redis-cli -p 7200 -h 127.0.0.1   如果修改了端口,则要指定端口
光标变成127.0.0.1:7200>

127.0.0.1:7200> info # 服务器信息
127.0.0.1:7200> ping
PONG # 连接成功
127.0.0.1:7200> select 5 # 默认连接到0号数据库,切换到5号
OK
127.0.0.1:7200[5]> # 提示符会变

```



# Redis数据类型
string 字符串
hash 哈希类型 存储键值对 kvkvkv
list 列表可重复添加 按照插入顺序排序
set 集合不可重复 顺序不确定
sortedset 排序集合 不可重复,分数排序

字符串runoob https://www.runoob.com/redis/redis-strings.html
```bash
# 字符串String
# key-value (string/int/float)
# key是字符串
# 每条数据都是一个键对值,键是字符串,而且键的类型不能重复.可以存储的值是字符串,整数或浮点,统称为元素.可以存储二进制,任何格式的数据,如JPEG图像数据或JSON对象描述信息等.最多可容纳的数据长度是512M,可以对字符串进行操作,对整数类型加减

> set string1 yeyeye  #设置字符串
> get string1  # 获取字符串
> del string1 # 删除字符串

> mset a1 python a2 java a3 c # 设置多个键多个值
> mget a1 a2 a3 # 获取多个值

> append a1 haha # 在字符串后面追加一段值

> incr string2 # 整形自增1
> decrby string2 2 # 整形减法

> setex sring3 3 aa # 设置过期时间,3秒后不可用


APPEND # 字符串后面追加一段值
BITCOUNT
BITFIELD
BITOP
BITPOS
DECR
DECRBY # 整形减法
GET # 获取字符串
GETBIT
GETRANGE
GETSET
INCR # 整形自增
INCRBY
INCRBYFLOAT
MGET # 获取多个键
MSET # 设置多个值
MSETNX
PSETEX
SET # 设置字符串
SETBIT
SETEX # 设置过期时间
SETNX
SETRANGE
STRLEN

```






哈希 https://www.runoob.com/redis/redis-hashes.html
```bash
# 散列Hashes
有key-value的散列组,其中key是字符串,value是元素.按照key进行增加删除,key必须是惟一的.散列结构要求键必须不一样,但是值可以相等.key-[key-value (string/int/float),key-value (string/int/float)]

>hset hash1 key1 12 # 插入散列键值 key1-12
>hget hash1 key1 # 获取散列hash1中的key1
>hgetall key1 #获取所有的键值对,单数为键,偶数为值 

>hmset hash1 key1 13 key2 14 # 设置多个值
>hmget hash1 key1 key2 # 一次性获取get的值

>hlen hash1 # 查看散列有多少元素
>hkeys hash1 # 获取指定键所有的属性

>hvals hash1 # 获取所有属性的值
>hdel hash1 # 删除散列的键,如果使用del命令,会删除整个散列表


HDEL # 删除散列的键
HEXISTS
HGET # 获取散列值
HINCRBY
HINCRBYFLOAT
HKEYS # 获取指定键所有的属性
HLEN # 查看散列有多少元素
HMGET # 获取多个散列值
HMSET # 设置多个散列值
HSCAN
HSET # 插入散列值
HSETNX
HSTRLEN
HVALS # 获取所有属性的值
```

```
注意：如果出现了这个错误
MISCONF Redis is configured to save RDB snapshots, but is currently not able to persist on disk. Commands that may modify the data set are disabled. Please check Redis logs for details about the error.
Redis被配置为保存数据库快照,但它目前不能持久化到硬盘.用来修改集合数据的命令不能用.hset修改集合不能用
原因：强制关闭Redis快照导致不能持久化
将stop-writes-on-bgsave-error设置为no
127.0.0.1:6379> config set stop-writes-on-bgsave-error no

```

[Redis修改hash报错解决方案 https://www.jianshu.com/p/3aaf21dd34d6)






列表 https://www.runoob.com/redis/redis-lists.html
```bash
# 列表Lists
# list中的元素可以是重复的,但是集合没有重复的
# List集合是一个有序的列表.一个序列集合且每个节点都包好了一个元素.可以对序列两端推入,或弹出元素修剪,查找或移除元素.列表分左右,(左边推入,右边弹出是队列)(左边推入和弹出是栈空间)

key-[value (string/int/float),value (string/int/float)]
>lpush list1 12 # 左边插入,在同一侧插入弹出是栈空间
>lpop list1 # 左边弹出
>rpush list1 13 # 右边插入,一侧插入另一侧弹出是队列
>rpop list1 # 右边弹出
>linsert list1 before 13 12.5 # 在13前面插入12.5,遇到的第一个
>linsert list1 after 12 12.5 # 在12后面插入12.5

# 设置指定元素,第一个元素是0,-1表示末尾的元素
>lset l1 1 14

# 查找元素命令
>llen list2 # 列出list中元素的个数
>lrange l1 0 4 # 列出列表的从哪到哪的数据
>lrange l1 0 -1 # 查看列表所有数据,-1表示末尾的数据,-2表示倒数第二的数据

# 删除指定的元素,正数从左到右删除,负数从末尾删除,0删除所有,值相同的元素
>lrem l1 3 12.5


BLPOP
BRPOP
BRPOPLPUSH
LINDEX
LINSERT # 在某个元素的前面或后面插入数据,第一个遇到的
LLEN # 列出元素的个数
LPOP # 列表左侧弹出数据
LPUSH # 列表左侧插入数据
LPUSHX
LRANGE # 列出区间内的数据
LREM # 删除指定的元素
LSET # 设置元素的值
LTRIM
RPOP # 列表右侧弹出数据
RPOPLPUSH
RPUSH # 列表右侧插入数据
RPUSHX
```






集合 https://www.runoob.com/redis/redis-sets.html
```bash
# 集合Sets
使用无序的方式存储多个不相同的元素,对于集合没有修改的操作.从集合中插入或者删除元素.每个元素都不一样,可以对元素中的值进行添加和删除,检查一个元素是否在这个集合中
key-[value (string/int/float),value (string/int/float)]

>sadd set1 12 # 插入元素

>scard set1 # 查看有多少元素
>smembers set1 # 获取所有元素

>sismember set1 12 # 判断13是否在这个集合中

>srem set1 12 # 从集合中删除13

SCARD # 查看有多少元素
SDIFF
SDIFFSTORE
SINTER
SINTERSTORE
SISMEMBER # 判断元素是否在集合中
SMEMBERS # 获取所有元素
SMOVE
SPOP
SRANDMEMBER
SREM # 从集合删除元素
SSCAN
SUNION
SUNIONSTORE
```



```bash
有序集合 https://www.runoob.com/redis/redis-sorted-sets.html

# 有序集合Sorted Sets
也叫有序分数集合,和散列很相似,也存储一个映射,分数和元素的映射,score可以看做是一个排行榜,排行榜还隐藏一个排行的属性,每个元素都有一个排行属性rank,从0开始表示分数值是最小的,随着score的变大而变大.带分数的score-value有序集合,其中score为浮点,如果score的值一样,则按照value的字母顺序排列,value为元素,value必须是全局唯一.集合插入删除,按照分数范围查找

key-[value (string/int/float)-score,value (string/int/float)-score]

>zadd zset1 10.1 val1 # score为10.1 value为val1的元素

>zcard zset1 # 查看有多少元素
>zrange zset1 0 2 withscores # 打印0-2的元素,附带分数,0 -1表示最后一个元素,返回的值是排列好的
>zrangebyscore zset1 min max # 打印score一定范围内的值,边缘值包括在内
>zscore zset1 val1 # 查看某个元素的score值
>zrank zset1 val2 # 查看一下val2的排名

>zrem zset1 val1 # 删除指定元素
>zremrangebyscore zset1 min max # 删除一定范围内的值


BZPOPMAX
BZPOPMIN
ZADD # 添加有序集合
ZCARD # 查看有多少元素
ZCOUNT
ZINCRBY
ZINTERSTORE
ZLEXCOUNT
ZPOPMAX
ZPOPMIN
ZRANGE # 打印元素,排列好的
ZRANGEBYLEX
ZRANGEBYSCORE # 打印一定范围内元素的值
ZRANK # 查看元素的排名
ZREM # 删除指定元素
ZREMRANGEBYLEX
ZREMRANGEBYRANK
ZREMRANGEBYSCORE # 删除一定范围内的值
ZREVRANGE
ZREVRANGEBYLEX
ZREVRANGEBYSCORE
ZREVRANK
ZSCAN
ZSCORE # 查看某个元素的score值
ZUNIONSTORE
```





# Redis命令

```bash
# 键 keys

keys * # 查找所有的keys,可以使用正则  (keys a* 查找a开头的键)
del key1 key2 ...# 删除指定的key(一个或多个)
exists key # 查询一个key是否存在 存在返回1 不存在返回0
type a1 # 获取key的存储类型
# 如果没有指定过期时间,值则一直存在,直到使用del移除
expire a1 3 # 设置一个key的过期秒数
ttl a1# 获取key的有效时间,过期的键返回-2



dump key # 导出key的值
expireat key timestamp # 设置一个UNIX时间戳的过期时间
migrate#原子性的将key从Redis的一个实例移到另一个实例
move 移动一个key到另一个数据库
object # 检查内部的再分配对象
persist # 移除key的过期时间
pexpire # 设置key的有效时间以毫秒为单位
pexpireat # 设置key的到期UNIX时间戳以毫秒为单位
pttl # 获取key的有效毫秒数
randomkey # 返回一个随机的key
rename # 将一个key重命名
renamenx # 重命名一个key,新的key必须是不存在的key
restore #
sort # 对序列,集合,有序集合排序
wait # 
scan # 增量迭代key
```





```bash
DEL
DUMP
EXISTS
EXPIRE
EXPIREAT
KEYS
MIGRATE
MOVE
OBJECT
PERSIST
PEXPIRE
PEXPIREAT
PTTL
RANDOMKEY
RENAME
RENAMENX
RESTORE
SCAN
SORT
TOUCH
TTL
TYPE
UNLINK
WAIT
```


```bash
# 事务 Transactions
DISCARD
EXEC
MULTI
UNWATCH
WATCH
```

```bash
# 脚本 Scripting
EVAL
EVALSHA
SCRIPT DEBUG
SCRIPT EXISTS
SCRIPT FLUSH
SCRIPT KILL
SCRIPT LOAD
```


```bash
# 连接 Connection
AUTH
ECHO
PING
QUIT
SELECT
SWAPDB
```

```bash
# 服务器 Server
> config get loglevel # 查看配置
> config get * # 查看所有配置
> config set loglevel "notice" # 修改配置

> save # 当前数据库的备份
```

参数说明 https://www.runoob.com/redis/redis-conf.html
数据库的备份 https://www.runoob.com/redis/redis-backup.html

```bash
BGREWRITEAOF
BGSAVE
CLIENT GETNAME
CLIENT ID
CLIENT KILL
CLIENT LIST
CLIENT PAUSE
CLIENT REPLY
CLIENT SETNAME
CLIENT UNBLOCK
COMMAND
COMMAND COUNT
COMMAND GETKEYS
COMMAND INFO
CONFIG GET
CONFIG RESETSTAT
CONFIG REWRITE
CONFIG SET
DBSIZE
DEBUG OBJECT
DEBUG SEGFAULT
FLUSHALL
FLUSHDB
INFO
LASTSAVE
MEMORY DOCTOR
MEMORY HELP
MEMORY MALLOC-STATS
MEMORY PURGE
MEMORY STATS
MEMORY USAGE
MONITOR
REPLICAOF
ROLE
SAVE # 备份数据
SHUTDOWN
SLAVEOF
SLOWLOG
SYNC
TIME
```


```bash
# Cluster
CLUSTER ADDSLOTS
CLUSTER COUNT-FAILURE-REPORTS
CLUSTER COUNTKEYSINSLOT
CLUSTER DELSLOTS
CLUSTER FAILOVER
CLUSTER FORGET
CLUSTER GETKEYSINSLOT
CLUSTER INFO
CLUSTER KEYSLOT
CLUSTER MEET
CLUSTER NODES
CLUSTER REPLICAS
CLUSTER REPLICATE
CLUSTER RESET
CLUSTER SAVECONFIG
CLUSTER SET-CONFIG-EPOCH
CLUSTER SETSLOT
CLUSTER SLAVES
CLUSTER SLOTS
READONLY
READWRITE
```


```bash
# Geo
GEOADD
GEODIST
GEOHASH
GEOPOS
GEORADIUS
GEORADIUSBYMEMBER
```


















```bash
# 发布订阅Pub/Sub
PSUBSCRIBE
PUBLISH
PUBSUB
PUNSUBSCRIBE
SUBSCRIBE
UNSUBSCRIBE
```




```bash
# Streams
XACK
XADD
XCLAIM
XDEL
XGROUP
XINFO
XLEN
XPENDING
XRANGE
XREAD
XREADGROUP
XREVRANGE
XTRIM
```

# 持久化
redis是基于缓存的数据库,服务器关闭则数据丢失,可以将redis内存中数据持久化到硬盘文件中.

```bash
# RDB 默认机制,一定的时间间隔,监测key的变化情况,然后持久化数据,对性能影响低.
# redis.windows.conf文件
save 900 1 # 15分钟之后,有一个key被改变,则写入
save 300 10 # 5分钟之后,有10个key被改变,则写入
save 60 10000 # 1分钟之后,有1万个key被改变,则写入
自定义 save 10 5 # 10秒钟有5个key被改变
> redis-server.exe redis.windows.conf # 用配置打开redis服务
会把数据存储在dump.rdb文件中.

# AOF 日志记录方式,可以记录每一条命令的操作,每一次命令操作后,持久化数据,对性能影响较严重
# redis.windows.conf文件
appendonly no # 改为yes,开启aof机制
# appendfsync always # 默认关闭 每次操作都进行持久化
appendfsync everysec # 默认开启 每隔一秒都进行持久化
# appendfsync no # 默认关闭 不进行持久化,redis是一个相当大的map集合


```


# benchmark
redis压力测试工具

```bash
# redis-benchmark 压力测试结果报告
# -h 主机名 -p 端口号
# -c 默认连接的客户端数量,并行连接,默认50
# -n 请求的数量,默认10万
# -d 数据的大小,默认是3个字节
# -k 布尔值,1表示一直保持连接,0表示断开并重新连接
# -t 测试命令,后面可接set,lpush,sadd等指定的命令,用逗号分隔
# -q 只显示总数性报告
redis-benchmark -h 127.0.0.1 -p 6379 -c 100 -n 5000














```

# HyperLog Log

从2.8.9引入的一种新数据类型,其意义是hyperlog log(超级日志记录),该数据类型可以简单理解为一个set集合,集合元素为字符串.实际上是一种基数计数概率算法,该算法可以利用极小的内存完成独立总数的统计.其相关命令是对这个set集合的操作.为了纪念算法设计者,使用PF作为命令的前缀.HyperLogLog是一个纯数学算法.

可对数据量庞大的日志数据做不精确的去重计数统计,比如平台上每个页面每天的UV数据.

```bash

# HyperLogLog
PFADD
PFCOUNT
PFMERGE

```







# 主从服务器

master用来写数据,slave用来读数据,网站的读写比是1：10
一个master可以用有多个slave,一个slave又可以拥有多个slave,如此下去,形成了强大的多级服务器集群架构
slave备份主服务的数据,通过主从配置可以实现读写分离

主配置
修改配置文件,IP绑定bind

从配置
复制一份主配置文件,重命名为slave.conf
IP绑定bind,确保能和主通信
从配置中的端口port不能和主端口冲突(如果主从在同一台机器上)
`slaveof 192.168.0.1 6379`主服务器的地址和端口

启动服务
主 redis-server redis.conf
从 redis-server slave.conf
Redis-cli -h 192.168.0.1 -p 6379 info Replication 查看信息,主从都能看
用redis-cli登录,主能读写,从只读







# 集群






# Jedis

```xml
<dependency>
  <groupId>redis.clients</groupId>
  <artifactId>jedis</artifactId>
  <version>2.9.0</version>
</dependency>
<dependency>
  <groupId>org.apache.commons</groupId>
  <artifactId>commons-pool2</artifactId>
  <version>2.4.2</version>
</dependency>

```

```java
@Test // jedis对象
public void jedisTest() {
  Jedis jedis = new Jedis(); // 默认本机6379
  //Jedis jedis= new Jedis("127.0.0.1",6379);
  System.out.println(jedis.set("username", "zhangsan"));
  System.out.println(jedis.get("username"));
  System.out.println(jedis.hset("h1","aa","bb"));
  System.out.println(jedis.hset("h1","cc","dd"));
  System.out.println(jedis.hset("h1","ee","ff"));
  System.out.println(jedis.hgetAll("h1"));
  System.out.println(jedis.type("h1"));
  System.out.println(jedis.keys("*"));
  jedis.close();
}

```

```java
@Test // 连接池基本使用
public void jedisTest() {
  //JedisPool jedisPool = new JedisPool();
  JedisPoolConfig config = new JedisPoolConfig();
  config.setMaxTotal(50); //最大允许连接数
  config.setMaxIdle(10); //最大空闲连接
  JedisPool jedisPool = new JedisPool(config,"127.0.0.1",6379);
  Jedis jedis = jedisPool.getResource();
  System.out.println(jedis.set("user", "zhangsan"));
  System.out.println(jedis.get("user"));
  //归还到连接池中
  jedis.close();
}




```

```java
/*
#最大活动对象数     
redis.pool.maxTotal=1000    
#最大能够保持idel状态的对象数      
redis.pool.maxIdle=100  
#最小能够保持idel状态的对象数   
redis.pool.minIdle=50    
#当池内没有返回对象时,最大等待时间    
redis.pool.maxWaitMillis=10000    
#当调用borrow Object方法时,是否进行有效性检查    
redis.pool.testOnBorrow=true    
#当调用return Object方法时,是否进行有效性检查    
redis.pool.testOnReturn=true  
#“空闲链接”检测线程,检测的周期,毫秒数.如果为负值,表示不运行“检测线程”.默认为-1.  
redis.pool.timeBetweenEvictionRunsMillis=30000  
#向调用者输出“链接”对象时,是否检测它的空闲超时；  
redis.pool.testWhileIdle=true  
# 对于“空闲链接”检测线程而言,每次检测的链接资源的个数.默认为3.  
redis.pool.numTestsPerEvictionRun=50  
#redis服务器的IP    
redis.ip=xxxxxx  
#redis服务器的Port    
redis1.port=6379   
*/

// 工具类
class JedisPoolUtils {
    /* jedis.properties
    resis.host=127.0.0.1
    resis.port=6379
    resis.maxTotal=50
    resis.maxIdle=10
    */
    private static JedisPool jedisPool;

    static {
        InputStream resourceAsStream = JedisPoolUtils.class.getClassLoader().getResourceAsStream("jedis.properties");
        Properties properties = new Properties();
        try {
            properties.load(resourceAsStream);
        } catch (IOException e) {
            e.printStackTrace();
        }
        String host = properties.getProperty("redis.host");
        String port = properties.getProperty("redis.port");
        String maxTotal = properties.getProperty("redis.maxTotal");
        String maxIdle = properties.getProperty("redis.maxIdle");

        JedisPoolConfig config = new JedisPoolConfig();
        config.setMaxTotal(Integer.parseInt(maxTotal));
        config.setMaxIdle(Integer.parseInt(maxIdle));
        jedisPool = new JedisPool(config, host, Integer.parseInt(port));
    }

    public static Jedis getJedis() {
        return jedisPool.getResource();
    }

    public static void close(Jedis jedis) {
        if (jedis != null) jedis.close();
    }
}
@Test // 工具类的使用
public void jedisTest() {
  Jedis jedis = JedisPoolUtils.getJedis();
  System.out.println(jedis.set("user", "zhangsan"));
  System.out.println(jedis.get("user"));
  //归还到连接池中
  JedisPoolUtils.close(jedis);
}


public class RedisUtil {
  //获取时长的值
  public static String getvalue(String key) {
    Jedis R = new Jedis("127.0.0.1");
    return R.get(key);
  }
  //设定时长
  public static void setValue(String key, int time, String value) {
    Jedis R = new Jedis("127.0.0.1");
    R.setex(key, time, value);
  }
}






```


# springboot

```xml
org.springframework.boot:spring-boot-starter-data-redis



```


```yml

# 配置地址
spring:
  redis:
    host: 127.0.0.1
    port: 6379
    lettuce:
      pool:
        # redis线程池
        max-active: 8
        max-idle: 8
        min-idle: 8
        max-wait: -1

```

```java

//redis操作工具类
@Component
public class RedisService {
    @Resource
    private StringRedisTemplate stringRedisTemplate;
    public void putValue(String key, String value) {
        ValueOperations<String, String> operations = stringRedisTemplate.opsForValue();
        operations.set(key, value);
        System.out.println(key + "" + value);
    }
}


@Resource
private RedisService redisService;
@Test
public void redisTest(){
    redisService.putValue("os","windows");
}


```


# php-Redis

安装
php -m 可以查看php有哪些拓展.还需要查看是否安装了phpize和php-config
yum install php-devel(PHP的拓展开发包)
wget https://github.com/phpredis/phpredis/archive/develop.zip
(PHP Redis拓展)
安装源码步骤
unzip develop.zip
Phpize
./configure --with-php-config=/usr/bin/php-config
Make/make install
php.ini -- extension=redis.so
具体步骤看 慕课网Redis教程 https://www.imooc.com/video/14335



# python

https://pypi.org/project/redis/#description
https://github.com/andymccurdy/redis-py
https://redis-py.readthedocs.io/en/latest/
手册还可以在pydoc命令中找到
使用python操作redis https://www.jianshu.com/p/2639549bedc8
3.40

安装Redis包
Pip3 install redis
pip freeze 
安装好Redis的python包之后,有许多命令可以和Redis交互,函数类似于Redis命令

```python
import redis
>>> r = redis.Redis(host='localhost', port=6379, db=0)
>>> r.set('foo', 'bar')
True
>>> r.get('foo')
'bar'
```








# UI client

redis的可视化客户端目前较流行的有三个：Redis Client ; Redis Desktop Manager ; Redis Studio.


收费版 https://resp.app/
免费版 https://github.com/uglide/RedisDesktopManager/releases/tag/0.9.3
https://blog.csdn.net/m0_55070913/article/details/123677891

Redis Desktop Manager2022是一款非常专业的可以跨平台的redis可视化工具,一款基于Qt5的跨平台Redis桌面管理软件,用于Windows,Linux,MacOS和iPadOS等操作系统,主要的功能就是分析,并可视化你的Redis服务器内存使用情况,通过批量删除来删除过时的数据,来缓解memcached这类key/value存储的不足的情况.软件的界面非常的简单直观,所有功能信息一目了然,用户通过可视化操作界面对数据库进行各方面工作,让你可以轻松轻松且快速的查看与操控整个数据库.





https://github.com/microsoftarchive/redis/releases








