






# Mybatis Plus

https://mybatis.plus
https://mp.baomidou.com
https://mybatis.plus/guide
https://github.com/baomidou/mybatis-plus




https://mvnrepository.com/artifact/com.baomidou/mybatis-plus/3.5.7
https://mvnrepository.com/artifact/com.baomidou/mybatis-plus-boot-starter/3.5.5





Mybatis-Plus是一个Mybatis的增强工具,在MyBatis的基础上只做增强不做改变,简化开发提高效率。

特点：第三集
只做增强不做改变,不会对现有的工程产生影响
内置通用Mapper,通用Service,仅通过少量配置即可实现单表大部分CRUD操作,更强大的条件构造器
支持Lambda调用,方便编写各类查询条件,无需担心字段写错
支持MySQL,MariaDB,Oracle,DB2,H2,HSQL,SQLite,Postgre,SQLServer2005,SQLServer等多种数据库
支持主键自动生成，内含分布式唯一ID生成器Sequence，可自由配置，完美解决逐渐问题
支持XML热加载，Mapper对应的XML支持热加载，



架构：
mybatis-plus-boot-starter 为spring boot整体提供的模块
annotation注解模块 extension拓展模块 core核心模块 generator生成代码模块

执行过程：
ScanEntity扫描实体->(反射)Analysis Table Name Column分析字段->(生成SQL语句)注入到Mybatis容器中->通过mybatis进行执行

作者是苞米豆组织开发并且开源的，组织大概有50个人
https://gitee.com/organization/baomidou



整合方式：Mybatis+MP, Spring+Mybatis+MP, SpringBoot+Mybatis+MP


```java
//BaseMapper的方法
selectById
selectBatchIds
selectByMap
selectOne
selectCount
selectList
selectMaps
selectObjs
selectPage
selectMapsPage

insert
updateById
update
deleteById
deleteByMap
delete
deleteBatchIds

```


# 代码生成器

```bash
# com.baomidou mybatis-plus-generator 3.3.1
3.5.1以前的版本包结构
com.baomidou.mybatisplus.generator.
  AutoGenerator 代码生成器类
  config.*Config 各种配置类
    
  engine 三种引擎 Beetl Freemarker Velocity
  templates 三种模板 btl ftl vm

```

```java

package com.atguigu;
//生成器3.3.1
import com.baomidou.mybatisplus.annotation.DbType;
import com.baomidou.mybatisplus.generator.AutoGenerator;
import com.baomidou.mybatisplus.generator.config.DataSourceConfig;
import com.baomidou.mybatisplus.generator.config.GlobalConfig;
import com.baomidou.mybatisplus.generator.config.PackageConfig;
import com.baomidou.mybatisplus.generator.config.StrategyConfig;
import com.baomidou.mybatisplus.generator.config.rules.NamingStrategy;

public class CodeGet {
    public static void main(String[] args) {
        //创建代码生成器
        AutoGenerator mpg = new AutoGenerator();

        //全局配置
        GlobalConfig gc = new GlobalConfig();
        String projectPath = System.getProperty("user.dir");
        gc.setOutputDir("C:\\Users\\Administrator\\Desktop\\ggkt\\mycode\\ggkt\\service\\service_vod\\src\\test\\java\\code");
        // 去掉Service接口的首字母I
        gc.setServiceName("%sService");
        gc.setAuthor("atguigu");
        gc.setOpen(false);
        mpg.setGlobalConfig(gc);

        //数据源配置
        DataSourceConfig dsc = new DataSourceConfig();
        dsc.setUrl("jdbc:mysql://localhost:3306/glkt_live");
        dsc.setDriverName("com.mysql.cj.jdbc.Driver");
        dsc.setUsername("root");
        dsc.setPassword("123456");
        dsc.setDbType(DbType.MYSQL);
        mpg.setDataSource(dsc);

        //包配置
        PackageConfig pc = new PackageConfig();
        pc.setParent("com.atguigu.ggkt");
        pc.setModuleName("live"); // 模块名
        pc.setController("controller");
        pc.setEntity("entity");
        pc.setService("service");
        pc.setMapper("mapper");
        mpg.setPackageInfo(pc);

        //策略配置
        StrategyConfig strategy = new StrategyConfig();
        strategy.setInclude("live_visitor",
                "live_course_goods",
                "live_course_description",
                "live_course_config",
                "live_course_account",
                "live_course");
        //数据库表映射到实体的命名策略
        strategy.setNaming(NamingStrategy.underline_to_camel);
        //数据库表字段映射到实体的命名策略
        strategy.setColumnNaming(NamingStrategy.underline_to_camel);
        //lombok模型 @Accessors(chain=true)setter链式操作
        strategy.setEntityLombokModel(true);
        //restful api风格控制器
        strategy.setRestControllerStyle(true);
        //url中驼峰转连字符
        strategy.setControllerMappingHyphenStyle(true);
        mpg.setStrategy(strategy);

        //执行
        mpg.execute();
    }
}











```




# 主键策略
实体类的主键生成方法

ASSIGN_ID 默认值,生成19位数字
ASSIGN_UUID uuid值
AUTO 自动增长
INPUT 手动设置主键值
NONE


```java



@KeySequence(value = "SEQ_ORACLE_STRING_KEY", clazz = String.class)
public class YourEntity {

    @TableId(value = "ID_STR", type = IdType.INPUT)
    private String idStr;

    @TableId(type = IdType.AUTO)
    private Long id;



}





```



# Spring Mybatis Plus

```xml
<!-- 比较简单的方法：https://start.aliyun.com 阿里云才有国人开发的mp-->
<!-- 传统方法是创建start.spring.io工程自己写坐标 -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.4.RELEASE</version>
    </parent>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter</artifactId>
            <exclusions>
                <exclusion>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-starter-logging</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
            <exclusions>
                <exclusion>
                    <groupId>org.junit.vintage</groupId>
                    <artifactId>junit-vintage-engine</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.1.1</version>
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.23</version>
        </dependency>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-log4j12</artifactId>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.2</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <version>2.1.4.RELEASE</version>
            </plugin>
        </plugins>
    </build>


```

```yml
spring:
  datasource:
    # 配置数据源
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/test
    username: root
    password: 0000

mybatis-plus:
  global-config:
    db-config:
      table-prefix: tb_ # 前缀数据库表比实体类多一个前缀

# mybatis日志输出
mybatis-plus:
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl

# application.properties
spring.application.name=springbootmybatisplus
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/mp
spring.datasource.username=root
spring.datasource.password=0000
# log4j.properties
log4j.rootLogger=DEBUG,A1
log4j.appender.A1=org.apache.log4j.ConsoleAppender
log4j.appender.A1.layout=org.apache.log4j.PatternLayout
log4j.appender.A1.layout.ConversionPattern=[%t] [%c]-[%p] %m%n

```



```java

//User.java
@Data
@NoArgsConstructor
@AllArgsConstructor
@TableName("tb_user")
public class User {
    private Long id;
    private String username;
    private String password;
    private String name;
    private int age;
    private String email;
}

//MybatisPlusApplication.java
@MapperScan("com.itheima.mapper")
@SpringBootApplication
public class PlusApplication {
    public static void main(String[] args) {
        SpringApplication.run(PlusApplication.class, args);
    }
}
//UserMapper.java
@Mapper
public interface UserMapper extends BaseMapper<User>(){
    //自带常用的方法
}


//UserTest.java
@RunWith(SpringRunner.class)
@SpringBootTest
public class UserTest {
    @Resource
    UserMapper userMapper;
    @Test
    public void test1() {
        for (User user : userMapper.selectList(null))
            System.out.println(user);
    }
}

```











```xml
com.baomidou
mybatis-plus
3.1.1

<dependency>
  <groupId>com.baomidou</groupId>
  <artifactId>mybatis-plus</artifactId>
  <version>3.1.1</version>
</dependency>
<dependency>
  <groupId>org.jboss</groupId>
  <artifactId>jboss-vfs</artifactId>
  <version>3.2.16.Final</version>
</dependency>


    <!-- 数据库驱动 -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>
        <!-- lombok 简化set get toString -->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
        </dependency>
        <!-- mybatis-plus -->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.4.3.1</version>
        </dependency>
————————————————
版权声明：本文为CSDN博主「有头发还能学」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/CodeInCoke/article/details/121030290


spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/mybatis_plus?useUnicode=true&useSSL=false&characterEncoding=utf8&serverTimezone=Asia/Shanghai
    username: root
    password: 123456
#其中url中，数据库名称？是否使用安全链接，字符集编码，是否使用解码，设置时区

#mysql数据库用的是gbk编码，而项目数据库用的是utf-8编码。这时候如果添加了useUnicode=true&characterEncoding=UTF-8
#存数据时：
#数据库在存放项目数据的时候会先用UTF-8格式将数据解码成字节码，然后再将解码后的字节码重新使用GBK编码存放到数据库中。
#取数据时：
#在从数据库中取数据的时候，数据库会先将数据库中的数据按GBK格式解码成字节码，然后再将解码后的字节码重新按UTF-8格式编码数据，最后再将数据返回给客户端。
————————————————
版权声明：本文为CSDN博主「有头发还能学」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/CodeInCoke/article/details/121030290



```

















无侵入：只做增强不做改变，引入它不会对现有工程产生影响，如丝般顺滑
损耗小：启动即会自动注入基本 CURD，性能基本无损耗，直接面向对象操作，BaseMapper
强大的 CRUD 操作：内置通用 Mapper、通用 Service，仅仅通过少量配置即可实现单表大部分 CRUD 操作，更有强大的条件构造器，满足各类使用需求，简单的CRUD操作不用自己编写。
支持 Lambda 形式调用：通过 Lambda 表达式，方便的编写各类查询条件，无需再担心字段写错
支持主键自动生成：支持多达 4 种主键策略（内含分布式唯一 ID 生成器 - Sequence），可自由配置，完美解决主键问题
支持 ActiveRecord 模式：支持 ActiveRecord 形式调用，实体类只需继承 Model 类即可进行强大的 CRUD 操作
支持自定义全局通用操作：支持全局通用方法注入（ Write once, use anywhere ）
内置代码生成器：采用代码或者 Maven 插件可快速生成 Mapper 、 Model 、 Service 、 Controller 层代码，支持模板引擎，更有超多自定义配置等您来使用（自动生成代码）
内置分页插件：基于 MyBatis 物理分页，开发者无需关心具体操作，配置好插件之后，写分页等同于普通 List 查询
分页插件支持多种数据库：支持 MySQL、MariaDB、Oracle、DB2、H2、HSQL、SQLite、Postgre、SQLServer 等多种数据库
内置性能分析插件：可输出 SQL 语句以及其执行时间，建议开发测试时启用该功能，能快速揪出慢查询
内置全局拦截插件：提供全表 delete 、 update 操作智能分析阻断，也可自定义拦截规则，预防误操作
————————————————
版权声明：本文为CSDN博主「有头发还能学」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/CodeInCoke/article/details/121030290




DROP TABLE IF EXISTS user;

CREATE TABLE user
(
	id BIGINT(20) NOT NULL COMMENT '主键ID',
	name VARCHAR(30) NULL DEFAULT NULL COMMENT '姓名',
	age INT(11) NULL DEFAULT NULL COMMENT '年龄',
	email VARCHAR(50) NULL DEFAULT NULL COMMENT '邮箱',
	PRIMARY KEY (id)
);
-- 真实开发中，version(乐观锁)、deleted(逻辑删除)、gmt_create(创建时间)、gmt_modified(修改时间)

INSERT INTO user (id, name, age, email) VALUES
(1, 'Jone', 18, 'test1@baomidou.com'),
(2, 'Jack', 20, 'test2@baomidou.com'),
(3, 'Tom', 28, 'test3@baomidou.com'),
(4, 'Sandy', 21, 'test4@baomidou.com'),
(5, 'Billie', 24, 'test5@baomidou.com');
————————————————
版权声明：本文为CSDN博主「有头发还能学」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/CodeInCoke/article/details/121030290







在启动类加上@mapper注解,扫描mapper文件夹
@SpringBootApplication
@MapperScan("com.jdw.mapper")


mapper接口
//在对应的Mapper 接口上 基础基本的 BaseMapper<T> T是对应的pojo类
@Repository   //告诉容器你是持久层的 @Repository是spring提供的注释，能够将该类注册成Bean
public interface UserMapper extends BaseMapper<User> {
    //所有的crud都编写完成了
}
————————————————
版权声明：本文为CSDN博主「有头发还能学」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/CodeInCoke/article/details/121030290

支持，mybatis-plus已经配置完成，可以直接使用，CRUD。




使用测试类@Test测试
//继承了BaseMapper ,所有方法来自父类，可扩展
@Autowired
private UserMapper userMapper;

@Test
void contextLoads() {
    System.out.println(("----- selectAll method test 测试查询所有用户方法 ------"));
    //selectList 的参数wrapper 是条件构造器，可以先写null
    List<User> userList = userMapper.selectList(null);
    //forEach 的参数是 Consumer类型的 语法糖
    userList.forEach(System.out::println);
}
————————————————
版权声明：本文为CSDN博主「有头发还能学」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/CodeInCoke/article/details/121030290
思考,我们没有写sql就查询了结果，那么，sql谁写的，方法哪来的？答案都是mybatis-plus.



日志配置
使用yml添加日志配置项
mybatis-plus:
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl



插入测试
插入及日志分析
//测试插入
@Test
public void testInsert(){
    User user = new User();
    user.setName("小蒋");
    user.setAge(3);
    user.setEmail("2474950959@qq.com");
    //没有设置ID却自动生成的ID
    int result = userMapper.insert(user);
    System.out.println("result = " + result);
    System.out.println("user = " + user);
}
————————————————
版权声明：本文为CSDN博主「有头发还能学」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/CodeInCoke/article/details/121030290






我们可以看到，并没有给user设置id，数据库自动插入了id=1453311479846608897，

注意，数据库插入的默认值是全局唯一的id,这个id看起来也太奇怪了，到底是怎么生成的呢？

主键生成策略
因为在最开始建表的sql语句中就指明了，id是数据库的主键，主键不能唯一，

常见的数据库中主键自动设置方法有（uuid、自增id、雪花算法、redis生成、zookeeper生成）

详情见：分布式系统唯一ID生成方案

雪花算法
这里生成的id默认采用的是雪花算法：

snowflake是Twitter开源的分布式ID生成算法，结果是一个long型的ID。其核心思想是：使用41bit作为毫秒数，10bit作为机器的ID（5个bit是数据中心，5个bit的机器ID），12bit作为毫秒内的流水号（意味着每个节点在每毫秒可以产生 4096 个 ID），最后还有一个符号位，永远是0。具体实现的代码可以参看https://github.com/twitter/snowflake。雪花算法支持的TPS可以达到419万左右（2^22*1000）,几乎保证全球唯一。

雪花算法在工程实现上有单机版本和分布式版本。单机版本如下，分布式版本可以参看美团leaf算法：https://github.com/Meituan-Dianping/Leaf

可以在User类的id属性上加入注解TableId更改和查看策略

type = IdType.ASSIGN_ID，全局唯一id，雪花算法
1
public class User {
    @TableId(type = IdType.ASSIGN_ID,value = "id")//枚举注解,使用ID_WORKER策略,全局唯一ID，数据库设置自增也没用
    private Long id;
    private String name;
    private Integer age;
    private String email;
}
1
2
3
4
5
6
7
进入这个注解

@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target({ElementType.FIELD})  //枚举注解
public @interface TableId {
    //可以设置以下两个参数
    String value() default "";
    IdType type() default IdType.NONE; //ID策略
}
1
2
3
4
5
6
7
8
主键自增策略
要是自增策略，在id上加入下列代码

@TableId(type = IdType.AUTO)
private Long id;
1
2
同时数据库设计时，一定要将id设计为自增，这样自增id会设置在最大值上加1

其他策略
public enum IdType {
    /**
     * 数据库ID自增
     * <p>该类型请确保数据库设置了 ID自增 否则无效</p>
     */
    AUTO(0),
    /**
     * 该类型为未设置主键类型(注解里等于跟随全局,全局里约等于 INPUT)
     */
    NONE(1),
    /**
     * 用户输入ID
     * <p>该类型可以通过自己注册自动填充插件进行填充</p>
     */
    INPUT(2),

    /* 以下3种类型、只有当插入对象ID 为空，才自动填充。 */
    /**
     * 分配ID (主键类型为number或string）,
     * 默认实现类 {@link com.baomidou.mybatisplus.core.incrementer.DefaultIdentifierGenerator}(雪花算法)
     *
     * @since 3.3.0
     */
    ASSIGN_ID(3),
    /**
     * 分配UUID (主键类型为 string)
     * 默认实现类 {@link com.baomidou.mybatisplus.core.incrementer.DefaultIdentifierGenerator}(UUID.replace("-",""))
     */
    ASSIGN_UUID(4);

    private final int key;

    IdType(int key) {
        this.key = key;
    }
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
更新测试
更新及日志分析
	//更新测试
	@Test
    public void testUpdateByID() {
        User user = new User();
        user.setId(7L);
        user.setName("小小");
        user.setAge(18);//这一行后加
        int i = userMapper.updateById(user);//受影响的行数,参数是一个user不是id,点击看源码
        System.out.println("i = " + i);
    }
1
2
3
4
5
6
7
8
9
10
我可以发现，先只更新了名字，后面更新名字和年龄。mybatis-plus通过条件自动把我们进行了动态sql拼接，



自动填充
创建时间、更新时间！这个操作是自动化完成的，不要手动更新！

gmt_create、gmt_modified几乎在所有表都要配置上，而且自动化填充。gmt是时间时间的意思

方式一、数据库级别（不建议）
在数据库种添加字段gmt_create、gmt_modified，然后在pojo类中添加这两个属性，下次就可以查看了.(博主使用的是Navigat)



private Data gmtCreate;
private Data gmtModified;
1
2
方式二、代码级别
1、在数据库中删除掉根据当前时间戳更新的选项



2、在实体类的成员变量上添加注解@TableField

@TableField字段注解描述

    //字段添加填充内容
    @TableField(fill = FieldFill.INSERT ,value = "create_time")
    private LocalDateTime createTime;
    @TableField(fill = FieldFill.INSERT_UPDATE ,value = "update_time")
    private LocalDateTime updateTime;

1
2
3
4
5
6
public @interface TableField { //源码
   .....

    
    /**
     * 字段自动填充策略
     * <p>
     * 在对应模式下将会忽略 insertStrategy 或 updateStrategy 的配置,等于断言该字段必有值
     */
    FieldFill fill() default FieldFill.DEFAULT;

    ...
}

1
2
3
4
5
6
7
8
9
10
11
12
13
14
//填充策略
public enum FieldFill {
    /**
     * 默认不处理
     */
    DEFAULT,
    /**
     * 插入时填充字段
     */
    INSERT,
    /**
     * 更新时填充字段
     */
    UPDATE,
    /**
     * 插入和更新时填充字段
     */
    INSERT_UPDATE
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
3、编写处理器来处理这个注解

官方填充处理器写法

@Slf4j //日志
@Component//以组件的形式把这个处理器注册到IOC容器中
public class MyMetaObjectHandler implements MetaObjectHandler {

    //插入时启动  第三个参数 LocalDateTime 一定要和 createTime成员变量的值的类型一致，不然是null 如果是date就都设置date
    @Override
    public void insertFill(MetaObject metaObject) {
        log.info("start insert fill ....");
        this.strictInsertFill(metaObject, "createTime", LocalDateTime.class, LocalDateTime.now()); // 起始版本 3.3.0(推荐使用)
        this.strictUpdateFill(metaObject, "updateTime", LocalDateTime.class, LocalDateTime.now()); // 起始版本 3.3.0(推荐)
    }

    //更新时候启动
    @Override
    public void updateFill(MetaObject metaObject) {
        log.info("start update fill ....");
        this.strictUpdateFill(metaObject, "updateTime", LocalDateTime.class, LocalDateTime.now()); // 起始版本 3.3.0(推荐)
    }
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
4、接下来的代码执行插入、更新时都会自动设置时间了

乐观锁
乐观锁原理
乐观锁：顾名思义十分乐观，他总是认为不会出现问题，无论干什么都不会上锁！如果出现了问题，就再次更新值加锁处理

悲观锁：顾名思义十分悲观，他总是认为无论干什么都会出现问题，所以都会上锁，再操作！

官方乐观锁写法

乐观锁（OptimisticLockerInnerInterceptor）机制:

当要更新一条记录的时候，希望这条记录没有被别人更新

乐观锁实现方式：

取出记录时，获取当前version
更新时，带上这个version
执行更新时， set version = newVersion where version = oldVersion
如果version不对，就更新失败
相当于给每一个记录都加一个version字段。当我们要改记录时，把version字段拿出来看一看，对比一下这个version 有没有在你操作数据时被其他线程更改，如果依然等于oldVersion，你就对数据进行操作同时把 version = newVersion 更新（比如+1），以此你在改数据的途中告诉其他线程不要读了脏数据。

--A 线程
update user set name = "jdw" ,version = version + 1   --version = newVersion  version有默认值比如1 
where id = 2 and version = 1  -- version = oldVersion
--B 线程 抢先完成，此时version=2,导致A线程的  version = oldVersion 不匹配A的oldVersion A将会修改失败,防止数据库产生脏数据
update user set name = "jdw" ,version = version + 1   --version = newVersion  version有默认值比如1 
where id = 2 and version = 1  -- version = oldVersion
1
2
3
4
5
6
乐观锁的应用
测试更新
1、在数据库添加version字段，int型,默认0,长度10,不自增

2、在User类中添加对应属性：

@Version //乐观锁注解
private int version;
1
2
说明: Version

支持的数据类型只有:int,Integer,long,Long,Date,Timestamp,LocalDateTime
整数类型下 newVersion = oldVersion + 1
newVersion 会回写到 entity 中
仅支持 updateById(id) 与 update(entity, wrapper) 方法
在 update(entity, wrapper) 方法下, wrapper 不能复用!!!
3、在config下注册组件，开启乐观锁拦截器

@EnableTransactionManagement  //开启事务
@Configuration  //配置类注解
public class MybatisPlusConfig {
    @Bean
    public MybatisPlusInterceptor mybatisPlusInterceptor() {
        MybatisPlusInterceptor mybatisPlusInterceptor = new MybatisPlusInterceptor();
        mybatisPlusInterceptor.addInnerInterceptor(new OptimisticLockerInnerInterceptor());//乐观锁插件拦截器OptimisticLockerInnerInterceptor
        return mybatisPlusInterceptor;
    }
}
1
2
3
4
5
6
7
8
9
10
4.测试乐观锁

@Test
public void testOptimisticLocker(){
    //1、查询用户信息
    User user = userMapper.selectById(1L);
    //2、修改用户信息
    user.setEmail("123@qq.com");
    user.setName("小垃圾");
    //3、更新操作
    userMapper.updateById(user);
}
1
2
3
4
5
6
7
8
9
10
在测试代码中我们并没有更新version数据库的version已经变成2了，下面是日志分析：



5.模拟多线程下乐观锁失败案例

 @Test
    public void testOptimisticLocker2(){
        //模拟多线程
        User user = userMapper.selectById(3L);
        user.setEmail("123jdw@qq.com");
        user.setName("帅小伙111");//我们在这里对线程1修改值

        //线程2插队
        User user2 = userMapper.selectById(3L);
        user2.setEmail("321jdw@qq.com");
        user2.setName("帅小伙222");
        userMapper.updateById(user2); //线程2抢先提交

        userMapper.updateById(user);//线程1失败，乐观锁在这种情况下防止了脏数据存在，没有乐观锁就会有覆盖掉线程2的操作
    }
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
测试查询
1、查询单用户

//查询单用户
@Test
public void testSelectBatchId(){
    User user = userMapper.selectById(1L);
    System.out.println(user);
}
1
2
3
4
5
6
2、多用户查询

//查询指定多用户
@Test
public void testSelectBatchIds() {
    //Arrays.asList()创建了一个固定大小的集合   
    List<User> users = userMapper.selectBatchIds(Arrays.asList(1, 2, 3));//参数Collection的集合
    users.forEach(System.out::println);
}
1
2
3
4
5
6
7
Arrays.asList()详解

//  selectBatchIds 源码
/**
 * 查询（根据ID 批量查询）
 *
 * @param idList 主键ID列表(不能为 null 以及 empty)
 */
List<T> selectBatchIds(@Param(Constants.COLLECTION) Collection<? extends Serializable> idList);
1
2
3
4
5
6
7
日志分析：内部解析的是一个 IN 条件



3、条件查询

//条件查询，-- HashMap
@Test
public void testSelectByMap() {
    HashMap<String, Object> map = new HashMap<>();
    //定义查询条件
    map.put("name", "小蒋"); //where k = v
    map.put("age",3);
    List<User> users = userMapper.selectByMap(map);
    users.forEach(System.out::println);
}
1
2
3
4
5
6
7
8
9
10
日志分析



分页查询
官方分页插件写法

1、配置拦截器

public class MybatisPlusConfig {
    @Bean
    public MybatisPlusInterceptor mybatisPlusInterceptor() {
        MybatisPlusInterceptor mybatisPlusInterceptor = new MybatisPlusInterceptor();
        mybatisPlusInterceptor.addInnerInterceptor(new OptimisticLockerInnerInterceptor());//创建乐观锁拦截器 OptimisticLockerInnerInterceptor
        mybatisPlusInterceptor.addInnerInterceptor(new PaginationInnerInterceptor(DbType.MYSQL)); //插件分页拦截器，我的是mysql
        return mybatisPlusInterceptor;
    }
}
1
2
3
4
5
6
7
8
9
2、使用page对象即可

    //测试分页查询
    @Test
    public void testPage() {
        Page<User> page = new Page<>(1,5); //开启拦截器后，会注册一个page对象  当前页，每页条数
        //方法源码：   <P extends IPage<T>> P selectPage(P page, @Param(Constants.WRAPPER) Wrapper<T> queryWrapper);
        userMapper.selectPage(page,null); //分页查询
        page.getRecords().forEach(System.out::println); //获取分页后的数据 打印
        System.out.println(page.getTotal()); //获取记录总数
    }
1
2
3
4
5
6
7
8
9
/**源码
 * 分页构造函数
 *
 * @param current 当前页
 * @param size    每页显示条数
 */
public Page(long current, long size) {
    this(current, size, 0);
}
1
2
3
4
5
6
7
8
9
日志分析



底层也是把他转化成limit

删除测试
常见删除
    //删除测试
    @Test
    public void testDeleteById(){
        userMapper.deleteById(1453324799370616833L);
    	// userMapper.delete(null); //全部删除
    }
1
2
3
4
5
6
从上往下分别是：根据id删除，根据 entity 条件删除记录，通过多个id批量删除，根据map条件删除



逻辑删除
物理删除：在数据库中移除

逻辑删除：数据库中没有移除，而是在代码中使用一个变量来使他失效！(如：delete = 0 => delete = 1; )

就比如，管理员可以查看被删除的记录！防止数据丢失。类似于回收站。用户就没法查看删除记录。

逻辑删除官网链接

1、在数据库添加deleted字段



2、同步实体类中，同时添加@TableLogic//逻辑删除注解

@TableLogic//逻辑删除
private Integer deleted;
1
2
3、在配置文件yml中配置

mybatis-plus:
  global-config:
    db-config:
      logic-delete-field: flag  # 全局逻辑删除的实体字段名(since 3.3.0,配置后可以不加步骤2的注解)
      logic-delete-value: 1 # 逻辑已删除值(默认为 1)
      logic-not-delete-value: 0 # 逻辑未删除值(默认为 0)
1
2
3
4
5
6
4、测试删除

执行删除操作，实际上是执行更新操作，把deleted字段改为1了

        @Test
    public void testDeleteById(){
        userMapper.deleteById(1L);
    	// userMapper.delete(null); //全部删除
    }
1
2
3
4
5


数据库中也是没被上，改了值而已



如果我们再去查询这个id=1的用户发现，查不到，mybatis-plus 自动拼接了deleted字段在where中判断。

@Test
public void testSelectBatchId() {
    User user = userMapper.selectById(1L);
    System.out.println(user);
}
1
2
3
4
5


性能分析插件
官方使用的p6spy性能有损耗，推荐使用其他第三方性能分析插件，比如阿里巴巴的Druid。

条件构造器Wrapper（重点）
之前我们写crud时候经常碰到一个参数叫做wrapper，我们写的都是null，他到底是什么。

官方链接，条件构造器

我们之前一直是增删改查，没有一个是带条件的，而这个条件构造器就相当于sql中加了一个where,

QueryWrapper和 UpdateWrapper,分别是用于生成查和改 的 sql 的 where 条件

例如, 查询多条记录与单条记录

    @Test
    void contextLoads() {
        //----------查询多个
        //查询一个复杂的，比如查询用户name、邮箱不为空，年龄大于20的用户
        QueryWrapper<User> wrapper = new QueryWrapper<>(); //首先新建一个 QueryWrapper
        //链式编程 添加查询条件
        wrapper.isNotNull("name")
                .eq("email","2455555659@qq.com")
                .ge("age",12);  
        userMapper.selectList(wrapper).forEach(System.out::println); 
		//----------查询单个
        User user = userMapper.selectOne(wrapper); //出现多个结果会报错，查询一个
        System.out.println("user = " + user);
    }
	//        eq相等   ne不相等，   gt大于，    lt小于         ge大于等于       le 小于等于
	//        equal/ not equal/ greater than/ less than/ less than or equal/ great than or equal/
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
日志分析，就是在where中添加了多个条件



区间查询与计数，between()，selectCount()

@Test
void test2() {
    //查询区间内的记录
    QueryWrapper<User> wrapper = new QueryWrapper<>();
    wrapper.between("age",20,30);
    Integer count = userMapper.selectCount(wrapper);
    System.out.println("count = " + count);
}
1
2
3
4
5
6
7
8
[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-Z14L81qV-1635498303245)(C:/Users/Dell/AppData/Roaming/Typora/typora-user-images/image-20211028220327420.png)]

模糊查询

@Test
void test3() {
    //模糊查询
    QueryWrapper<User> wrapper = new QueryWrapper<>();
    wrapper.like("name",99)         //  名字中 存在 99
            .notLike("name",6)      //  名字中 不存在 6
            .likeRight("email",2)   //  邮箱 最右边是m  %m
            .likeLeft("email","m"); //  邮箱 最左边是2  2%
    userMapper.selectMaps(wrapper);
}
1
2
3
4
5
6
7
8
9
10


子查询（多表查询）

void test4() {
    //子查询
    QueryWrapper<User> wrapper = new QueryWrapper<>();
    wrapper.inSql("id","select id from table where id <2");
    userMapper.selectObjs(wrapper).forEach(System.out::println);
}
1
2
3
4
5
6


排序

@Test
void test5() {
    //排序 
    QueryWrapper<User> wrapper = new QueryWrapper<>();
    wrapper.orderByAsc("id");  //根据id升序排列   降序orderByDesc()略
    userMapper.selectList(wrapper).forEach(System.out::println);
}
1
2
3
4
5
6
7


分组，条件

@Test
void test7() {
    //分组排序
    QueryWrapper<User> wrapper = new QueryWrapper<>();
    wrapper.groupBy("version").having("version = 1");
    userMapper.selectList(wrapper).forEach(System.out::println);
}
1
2
3
4
5
6
7


其他warpper条件见官网官方链接，条件构造器

代码自动生成器（重点）
AutoGenerator 是 MyBatis-Plus 的代码生成器，通过 AutoGenerator 可以快速生成 Entity、Mapper、Mapper XML、Service、Controller 等各个模块的代码，极大的提升了开发效率。

使用步骤

配置依赖，添加如下依赖，当然，不要忘记还要 快速开始第一章节的依赖

		<!-- mp 代码生成器 依赖 -->
		<dependency>
			<groupId>com.baomidou</groupId>
			<artifactId>mybatis-plus-generator</artifactId>
			<version>3.4.1</version>
		</dependency>
		<!-- 导入swagger -->
        <dependency>
            <groupId>io.swagger</groupId>
            <artifactId>swagger-annotations</artifactId>
            <version>1.5.20</version>
        </dependency>
		<!-- 添加模板引擎，thymeleaf 还有freemarker都是模板引擎 -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-freemarker</artifactId>
		</dependency>
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
在任意文件夹新建立一个类进行配置

类的代码如下

package com.jdw;

import com.baomidou.mybatisplus.annotation.DbType;
import com.baomidou.mybatisplus.annotation.FieldFill;
import com.baomidou.mybatisplus.annotation.IdType;
import com.baomidou.mybatisplus.core.exceptions.MybatisPlusException;
import com.baomidou.mybatisplus.core.toolkit.StringPool;
import com.baomidou.mybatisplus.core.toolkit.StringUtils;
import com.baomidou.mybatisplus.generator.AutoGenerator;
import com.baomidou.mybatisplus.generator.InjectionConfig;
import com.baomidou.mybatisplus.generator.config.*;
import com.baomidou.mybatisplus.generator.config.po.TableFill;
import com.baomidou.mybatisplus.generator.config.po.TableInfo;
import com.baomidou.mybatisplus.generator.config.rules.DateType;
import com.baomidou.mybatisplus.generator.config.rules.NamingStrategy;
import com.baomidou.mybatisplus.generator.engine.FreemarkerTemplateEngine;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

// 演示例子，执行 main 方法控制台输入模块表名回车自动生成对应项目目录中
public class CodeGenerator {

    /**
     * <p>
     * 读取控制台内容
     * </p>
     */
    public static String scanner(String tip) {
        Scanner scanner = new Scanner(System.in);
        StringBuilder help = new StringBuilder();
        help.append("请输入" + tip + "：");
        System.out.println(help.toString());
        if (scanner.hasNext()) {
            String ipt = scanner.next();
            if (StringUtils.isNotBlank(ipt)) {
                return ipt;
            }
        }
        throw new MybatisPlusException("请输入正确的" + tip + "！");
    }

    public static void main(String[] args) {
        // 代码生成器
        //构建一个代码自动生成器对象
        AutoGenerator mpg = new AutoGenerator();

        // 1、创建全局配置类的对象
        GlobalConfig gc = new GlobalConfig();
        //获取当前项目路径
        String projectPath = System.getProperty("user.dir");
        System.out.println("projectPath = " + projectPath);
        //自动生成代码存放的路径
        gc.setOutputDir(projectPath + "/src/main/java");
        //设置 --作者注释
        gc.setAuthor("jdw");
        //是否打开文件夹
        gc.setOpen(false);
        //是否覆盖已有文件
        gc.setFileOverride(false);
        //各层文件名称方式，例如： %sAction 生成 UserAction  %s占位符
        gc.setServiceName("%sService");
        //设置日期策略  date类型
        gc.setDateType(DateType.ONLY_DATE);
        //设置主键策略 雪花算法
        gc.setIdType(IdType.ASSIGN_ID);
        //设置开启 swagger2 模式
        gc.setSwagger2(true);
        //把全局配置放入代码生成器
        mpg.setGlobalConfig(gc);

        // 2、数据源配置
        DataSourceConfig dsc = new DataSourceConfig();
        dsc.setUrl("jdbc:mysql://localhost:3306/vueblog?useUnicode=true&useSSL=false&characterEncoding=utf8&serverTimezone=Asia/Shanghai");
        dsc.setDriverName("com.mysql.cj.jdbc.Driver");
        dsc.setUsername("root");
        dsc.setPassword("123456");
        dsc.setDbType(DbType.MYSQL);
        mpg.setDataSource(dsc); //把数据源配置加入到代码生成器

        // 3、包配置
        PackageConfig pc = new PackageConfig();
        pc.setParent("com.jdw");
        pc.setEntity("entity");
        pc.setMapper("mapper");
        pc.setService("service");
        pc.setController("controller");
        // ...  有默认值，点击查看源码
        mpg.setPackageInfo(pc);//包加入代码生成器

        // 4、策略配置
        StrategyConfig strategy = new StrategyConfig();
        //下划线转驼峰命名  表
        strategy.setNaming(NamingStrategy.underline_to_camel);
        // 下划线转驼峰命名字段
        strategy.setColumnNaming(NamingStrategy.underline_to_camel);
        //实体类是否加上lombok注解
        strategy.setEntityLombokModel(true);
        //控制层采用RestControllerStyle注解
        strategy.setRestControllerStyle(true);
        // RequestMapping中 驼峰转连字符 -
        strategy.setControllerMappingHyphenStyle(true);
        //要映射的数据库表名  （重点）
        strategy.setInclude(scanner("表名，多个英文逗号分割").split(","));
        //添加表名前缀
        //strategy.setTablePrefix("m_"); //自动拼接上m_
        //逻辑删除字段名
        strategy.setLogicDeleteFieldName("deleted");
        //乐观锁字段名
        strategy.setVersionFieldName("version");
        // -------自动填充策略
        ArrayList<TableFill> fillList = new ArrayList<>();
        fillList.add(new TableFill("createTime", FieldFill.INSERT));
        fillList.add(new TableFill("updateTime",FieldFill.INSERT_UPDATE));
        // 参数是 List<TableFill> 的链表
        strategy.setTableFillList(fillList);
        mpg.setStrategy(strategy);

        //---------------------------------
        // 自定义配置
        InjectionConfig cfg = new InjectionConfig() {
            @Override
            public void initMap() {
                // to do nothing
            }
        };

        // 如果模板引擎是 freemarker
        String templatePath = "/templates/mapper.xml.ftl";
        // 如果模板引擎是 velocity
        // String templatePath = "/templates/mapper.xml.vm";

        // 自定义输出配置
        List<FileOutConfig> focList = new ArrayList<>();
        // 自定义配置会被优先输出
        focList.add(new FileOutConfig(templatePath) {
            @Override 
            //输出了 静态资源下的 Mapper
            public String outputFile(TableInfo tableInfo) {
                // 自定义输出文件名 ， 如果你 Entity 设置了前后缀、此处注意 xml 的名称会跟着发生变化！！
                return projectPath + "/src/main/resources/mapper/" + pc.getModuleName()
                        + "/" + tableInfo.getEntityName() + "Mapper" + StringPool.DOT_XML;
            }
        });

        cfg.setFileOutConfigList(focList);
        mpg.setCfg(cfg);

        //        FreemarkerTemplateEngine模板引擎
        mpg.setTemplateEngine(new FreemarkerTemplateEngine());
        mpg.execute();
    }
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
93
94
95
96
97
98
99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
写在后面
感谢你看到这篇博客，博主目前是一名大四的在校生，目前也是处于学习阶段，希望我们一起进步。

对于mybatis plus的使用，如果各位有什么疑问欢迎骚扰，有时间我会回复，你的支持是我学习最大的动力，谢谢!

代码已经开源GitHub：本博客全部代码地址

文章知识点与官方知识档案匹配，可进一步学习相关知识
————————————————
版权声明：本文为CSDN博主「有头发还能学」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/CodeInCoke/article/details/121030290































# 整合mybatis plus



```xml
<dependencies>
  <dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>${spring.version}</version>
  </dependency>
  <dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>${spring.version}</version>
  </dependency>
  <dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-test</artifactId>
    <version>${spring.version}</version>
  </dependency>
  <dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.23</version>
  </dependency>
  <dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus</artifactId>
    <version>3.5.2</version>
  </dependency>
  <dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>1.2.8</version>
  </dependency>
  <dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.22</version>
  </dependency>
 
 
</dependencies>

<!--  jdbc.properties
jdbc.driver=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/mp?serverTimezone=Asia/Shanghai
jdbc.username=root
jdbc.password=0000-->
<!-- Bean.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       http://www.springframework.org/schema/context/spring-context.xsd">
  <!--MybatisPlus数据源构建等工作就交给了Spring管理-->
    <context:property-placeholder location="jdbc.properties"/>
    <!--定义数据源-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="driverClassName" value="${jdbc.driver}"/>
        <property name="url" value="${jdbc.url}"/>
        <property name="username" value="${jdbc.username}"/>
        <property name="password" value="${jdbc.password}"/>
        <property name="maxActive" value="10"/>
        <property name="minIdle" value="5"/>
    </bean>
    <!--使用mp提供的sqlSessionFactory,完成spring与mp的整合-->
    <bean id="sqlSessionFactory" class="com.baomidou.mybatisplus.extension.spring.MybatisSqlSessionFactoryBean">
        <property name="dataSource" ref="dataSource"/>
    </bean>
    <!--扫描mapper接口，依然使用mybatis原生的扫描器-->
    <bean id="mapperScannerConfigurer" class="org.mybatis.spring.mapper.MapperScannerConfigurer">
        <property name="basePackage" value="com.itheima.mapper"/>
    </bean>

</beans>



```


```java
// User.java
@Data
@NoArgsConstructor
@AllArgsConstructor
@TableName("tb_user")
public class User {
    private Long id;
    private String username;
    private String password;
    private String name;
    private int age;
    private String email;
}
// UserMapper.java
@Mapper
public interface UserMapper extends BaseMapper<User> {
}

//Test.java
userMapper.selectList(null);

```






