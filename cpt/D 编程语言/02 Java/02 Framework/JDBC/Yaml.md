
# Yaml

https://yaml.org/
https://yaml.org/spec/1.2.2/
https://github.com/yaml/

https://bitbucket.org/snakeyaml/snakeyaml
org.yaml:snakeyaml:2.2

https://docs.spring.io/spring-boot/reference/features/external-config.html#features.external-config.yaml


```yaml

# YAML(YAML Ain't Markuo Language) 数据序列化格式
# yml容易阅读,与脚本语言交互,以数据为核心,重数据轻格式,比较于xml是以格式为中心,properties,
# 拓展名是yml,也可以写成yaml
# 区分大小写,层级关系用多行描述,每行结尾使用冒号结束,只能使用空格,同级关系左侧对齐,属性值前面添加空格,#注释
# 数据要和冒号隔开

# 字面值表示方式
boolean: TRUE # 大小写均可
float: 3.14 # 6.8523015e+5 支持科学计数法
int: 123 # 0b1010_0111 二进制
null: ~ # 表示null
string: Hello # 字符串可以直接书写
string2: "Hello" # 也可以加引号写字符串
date: 2020-01-01 # 日期格式必须是 yyyy-MM-dd
datetime: 2020-01-01T15:02:31+08:00 # 日期和时间用T连接，最后使用+代表时区

# 数据结构表示方式
# 描述层级关系
a:
  b:
    c: ccc

# 描述多个数据
list:
  - a
  - b
  - c

# 数组
like: [ game,music,sleep ]

# 多个对象
user:
  - name: zhangsan
    age: 20
  - name: lisi
    age: 21

user2: [ { name:zhangsan,age:20 },{ name:lisi,age:21 } ]

```


# SpringBoot读取yaml的值

```yaml
city: shanghai;
user:
  name: zhangsan
  age: 20
likes:
  - game
  - music
  - sleep
baseDir: /home/user
tempDir: ${baseDir}/temp # /home/user/temp
tempDir2: "${baseDir}/temp" # /home/user <tab> emp 字符串\t是转义字符

datasource:
  driver: com.mysql.cj.jdbc.Driver
  url: jdbc:mysql://localhost:3306/test
  username: root
  password: 0000

```

```java
@Value("${city}")//读取yml的数据
private String ct;
@Value("${user.name}")
private String username;
@Value("${likes[1]}")
private String liks1;
@Value("${tempDir}")
private String tempdir; // /home/user/temp
@Autowired

Environment env;// 读取application.yml中的属性
Environment.getProperty("server.port")

// 获取yaml中部分数据封装到类中
// 事实上yaml中的各种数据都封装在了对应的类中，server封装在了Server类中
@Component //定义为Bean
@ConfigurationProperties(prefix = "datasource")//前缀为datasource
class Jdbc(){//创建一个封装对象的类
    private String driver;
    private String url;
    private String username;
    private String password;}

private Jdbc jdbc;
jdbc.toString();

```








