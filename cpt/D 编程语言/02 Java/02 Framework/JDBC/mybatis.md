






mybatis前身是ibatis

orm框架，实体和数据库映射





# mybatis

https://blog.mybatis.org/
https://mybatis.org/mybatis-3/
https://github.com/mybatis/mybatis-3



https://mvnrepository.com/artifact/org.mybatis/mybatis/3.5.16


```java

//org.example.pojo
public class User {
    private int id;
    private String name;
    private Date birth;}

```



## config.xml

```xml

<!-- mybatis配置文件 -->

<!-- file:jdbc.properties
jdbc.driver=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/db_smbms
jdbc.username=root
jdbc.password=0000
-->

<!-- mybatis-config.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <!-- 配置文件 -->
    <properties resource="jdbc.properties"/>
    <!-- 设置 -->
    <settings>
        <setting name="logImpl" value="LOG4J"/>
        <setting name="autoMappingBehavior" value="FULL"/>
        <!-- 二级缓存 -->
        <setting name="cacheEnabled" value="true"/>
    </settings>
    <!-- 指定数据库映射 -->
    <typeAliases>
        <!-- 别称 -->
        <typeAlias alias="User" type="com.example.pojo.User" />
        <!-- 指定数据库映射类路径 -->
        <package name="com.example.pojo"/>
    </typeAliases>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC" />
            <dataSource type="POOLED">
                <property name="driver" value="${jdbc.driver}"/>
                <property name="url" value="${jdbc.url}"/>
                <property name="username" value="${jdbc.username}"/>
                <property name="password" value="${jdbc.password}"/>
            </dataSource>
        </environment>
    </environments>
    <mappers>
        <!--配置文件的映射地址-->
        <mapper resource="mybatis/userMapper.xml"/>
        <!--使用注解，使用class属性指定被注解的mapper全类名-->
        <!--<mapper class="com.itheima.mapper.UserMapper"></mapper>-->
    </mappers>
</configuration>

```





## mapper.xml

```java
public interface UserDao {
    List<User> findAll();
    int count();
    User findOne(int id);
    int saveUser(@Param("user") User user);
    int updateUser(@Param("user") User user);
    int deleteUser(@Param("user") int id);
}

```


```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.bdqn.firstboot.controller.dao.UserMapper">
    <select id="findAll" resultType="com.bdqn.firstboot.controller.bean.User">
        select * from User
    </select>
    <select id="count" resultType="int">
        select count(*) from User
    </select>
    <select id="findOne" parameterType="int" resultType="com.bdqn.firstboot.controller.bean.User">
        select * from User where id = #{id}
    </select>
    <insert id="saveUser" parameterType="com.bdqn.firstboot.controller.bean.User">
        insert into User(id, name, age) values (#{id}, #{name}, #{age})
    </insert>
    <update id="updateUser" parameterType="com.bdqn.firstboot.controller.bean.User">
        update user set name=#{name}, age=#{age} where id = #{id}
    </update>
    <delete id="deleteUser" parameterType="int">
        delete from User where id = #{id}
    </delete>
</mapper>


```



```xml
<!-- mybatis-mapper.xml -->
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.bdqn.smbms.dao.UserMapper">


    <resultMap id="userList" type="SmbmsUser">
        <result property="id" column="id"></result>
        <result property="userName" column="userName"></result>
        <result property="userCode" column="userCode"></result>
        <result property="userRole" column="userRole"></result>
        <!--底下映射的内容是表中有roleName字段，SmbmsUser类中额外添加一个userRoleName属性-->
        <result property="roleName" column="roleName"/>
    </resultMap>

    <!--    where 1=1-->
    <!--    trim用单表,where if 用多表-->
    <select id="queryUserByNameAndRole" resultMap="userList" parameterType="map">
        select * from smbms_user as u

        <trim prefix="where" prefixOverrides="and | or">
            <if test="userName!=null">
                and u.userName like concat('%', #{userName}, '%')
            </if>
            <if test="roleName!=null">
                and u.userRole = #{roleName};
            </if>
        </trim>
    </select>


    <!--<select id="queryUserByNameAndRole" resultMap="userList" parameterType="map">
        select u.*, r.roleName
        from smbms_user as u
        inner join smbms_role as r
        on u.userRole = r.id
        <where>
            <if test="userName != null">
                and u.userName like concat('%', #{userName}, '%')
            </if>
            <if test="roleName != null">
                and r.roleName = #{roleName};
            </if>
        </where>
    </select>-->
    <update id="update" parameterType="SmbmsUser">
        update smbms_user
        <trim prefix="set" suffixOverrides="," suffix="where id = #{id}">
            <if test="userCode!=null">
                userCode = #{userCode},
            </if>
            <if test="userName!=null">
                userName = #{userName},
            </if>
            <if test="userPassword!=null">
                userPassword = #{userPassword},
            </if>
        </trim>
        <!--        <set>
                </set>
                where id = #{id}-->
    </update>

    <!--<update id="update" parameterType="SmbmsUser">
        update smbms_user
        set userCode     = #{userCode},
            userName     = #{userName},
            userPassword = #{userPassword}
        where id = #{id}
    </update>-->


    <select id="queryUserByRoleList" resultType="SmbmsUser">
        SELECT * FROM smbms_user WHERE userRole in
        <foreach collection="list" open="(" item="roleIdList" separator="," close=")">
            #{roleIdList}
        </foreach>
    </select>

    <select id="queryUserByRoleArray" resultType="SmbmsUser">
        SELECT * FROM smbms_user WHERE userRole in
        <foreach collection="array" open="(" item="roleIds" separator="," close=")">
            #{roleIds}
        </foreach>
    </select>

    <select id="queryUserByRoleMap" resultType="SmbmsUser">
        SELECT * FROM smbms_user WHERE userRole in
        <foreach collection="roleIdMap" open="(" item="roleMap" separator="," close=")">
            #{roleMap}
        </foreach>
    </select>

    <select id="queryUserByGenderAndRoleMap" resultType="SmbmsUser">
        SELECT * FROM smbms_user WHERE gender = #{gender} AND userRole in
        <foreach collection="rMap" open="(" item="roleMap" separator="," close=")">
            #{roleMap}
        </foreach>
    </select>

    <select id="queryUserByMoreCondition" resultType="SmbmsUser">
        SELECT * FROM smbms_user WHERE 1=1
        <choose>
            <when test="userName!=null and userName!=''">
                AND userName LIKE CONCAT('%',#{userName},'%')
            </when>
            <when test="userCode!=null and userCode!=''">
                AND userCode LIKE CONCAT('%',#{userCode},'%')
            </when>
            <when test="userRole!=null">
                AND userRole = #{userRole}
            </when>
            <otherwise>
                AND gender = #{gender}
            </otherwise>
        </choose>
    </select>
</mapper>


```

```java
@Test
public void testMybatis(){
    String config = "mybatis-config.xml";
    InputStream resource = Resources.getResourceAsStream(config);
    SqlSessionFactoryBuilder sqlSessionFactoryBuilder = new SqlSessionFactoryBuilder();
    SqlSessionFactory sqlSessionFactory = sqlSessionFactoryBuilder.build(resource);
    SqlSession sqlSession = sqlSessionFactory.openSession();
    ProviderMapper providerMapper = sqlSession.getMapper(ProviderMapper.class);
    int count = providerMapper.queryProviderCount();
    System.out.println(count);
    sqlSession.close();
}

```












# 注解

```java
public interface UserMapper {
    @Select("select * from User")
    List<User> findAll();
    @Select("select count(*) from User")
    int count();
    @Select("select * from User where id = #{id}")
    User findOne(int id);
    @Insert("insert into user(id, username, birthday, sex, address) values (#{id},#{username},#{birthday},#{sex},#{address})")
    int saveUser(User user);
    @Update("update user set username = #{username},birthday = #{birthday},sex = #{sex},address = #{address} where id = #{id}")
    int updateUser(User user);
    @Delete("delete from user where id = #{id}")
    int deleteUser(int id);
}    

```




# Impl

```java
public class UserTest {
    static Logger logger = Logger.getLogger(UserTest.class);

    public static void main(String[] args) {
//        UserTest.testUserCount();
//        UserTest.testUserOne();
        UserTest.testUserList();


    }

    public static void testUserCount() {
        SqlSession sqlSession = null;
        try {
            sqlSession = MybatisUtil.createSqlSession();
            int count = sqlSession.getMapper(UserMapper.class)
                    .queryUserCount();
//            System.out.println(count);

        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            MybatisUtil.closeSqlSession(sqlSession);
        }
    }

    public static void testUserOne() {
        SqlSession sqlSession = null;
        try {
            sqlSession = MybatisUtil.createSqlSession();
            SmbmsUser smbmsUser = sqlSession.getMapper(UserMapper.class)
                    .queryUserOne("admin", "admin");
            System.out.println(smbmsUser);
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            MybatisUtil.closeSqlSession(sqlSession);
        }
    }

    public static void testUserList() {
        SqlSession sqlSession = null;
        try {
            sqlSession = MybatisUtil.createSqlSession();
            List<SmbmsUser> smbmsUserList = sqlSession.getMapper(UserMapper.class)
                    .queryUserList();
            logger.debug(smbmsUserList.size());
//            System.out.println(smbmsUserList.size());
//            for (SmbmsUser smbmsUser : smbmsUserList) System.out.println(smbmsUser);
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            MybatisUtil.closeSqlSession(sqlSession);
        }
    }


    public static void t1() throws IOException, SQLException {
        String config = "mybatis-config.xml";
        InputStream resource = Resources.getResourceAsStream(config);

        SqlSessionFactoryBuilder builder = new SqlSessionFactoryBuilder();
        SqlSessionFactory factory = builder.build(resource);
        SqlSession sqlSession = factory.openSession();

        System.out.println((Integer) sqlSession.selectOne("com.bdqn.smbms.dao.user.UserMapper.queryUserCount"));
//        System.out.println((int) sqlSession.selectOne("com.bdqn.smbms.dao.user.UserMapper.queryUserCount"));

//        SmbmsUser temp = new SmbmsUser().SmbmsUserCP("admin", "admin");
//        System.out.println((SmbmsUser) sqlSession.selectOne("com.bdqn.smbms.dao.user.UserMapper.queryUserOne", temp));

        UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
        System.out.println((SmbmsUser) userMapper.queryUserOne("admin", "admin"));
        System.out.println((SmbmsUser) userMapper.queryUserOne("test9", "test9"));
        sqlSession.close();
    }
}


```



















# Util
```java
// 工具类
public class MybatisUtil {
    private static SqlSessionFactory factory;
    static {
        String config = "mybatis-config.xml";
        try {
            InputStream inputStream = Resources.getResourceAsStream(config);
            factory = new SqlSessionFactoryBuilder().build(inputStream);
        } catch (IOException e) {e.printStackTrace();}
    }
    public static SqlSession createSqlSession() {return factory.openSession(false);}
    public static void closeSqlSession(SqlSession sqlSession) {
        if (sqlSession != null) sqlSession.close();}
    public static void main(String[] args) {
        System.out.println(MybatisUtil.factory);
        System.out.println(MybatisUtil.createSqlSession());
        MybatisUtil.closeSqlSession(MybatisUtil.createSqlSession());}
}

```



# log4j.properties

```properties
## Set root category priority to INFO and its only appender to CONSOLE
##log4j.rootCategory=INFO,CONSOLE             debug   info   warn error fatal
#log4j.rootCategory=debug, CONSOLE, LOGFILE
#
## Set the enterprise logger category to FATAL and its only appender to CONSOLE
#log4j.logger.org.apache.axis.enterprise=FATAL, CONSOLE
#
## CONSOLE is set to be a ConsoleAppender using a PatternLayout.
#log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender
#log4j.appender.CONSOLE.layout=org.apache.log4j.PatternLayout
#log4j.appender.CONSOLE.layout.ConversionPattern=%d{ISO8601} %-6r [%15.15t] %-5p %30.30c %x - %m\n
#
## LOGFILE is set to be a File appender using a PatternLayout.
#log4j.appender.LOGFILE=org.apache.log4j.FileAppender
#log4j.appender.LOGFILE.File=d:\axis.log
#log4j.appender.LOGFILE.Append=true
#log4j.appender.LOGFILE.layout=org.apache.log4j.PatternLayout
#log4j.appender.LOGFILE.layout.ConversionPattern=%d{ISO8601} %-6r [%15.15t] %-5p %30.30c %x - %m\n


log4j.rootLogger=DEBUG,CONSOLE,file
#log4j.rootLogger=ERROR,ROLLING_FILE
#log4j.logger.cn.smbms.dao=debug
log4j.logger.com.bdqn.smbms.dao.user=debug
log4j.logger.com.ibatis=debug 
log4j.logger.com.ibatis.common.jdbc.SimpleDataSource=debug 
log4j.logger.com.ibatis.common.jdbc.ScriptRunner=debug 
log4j.logger.com.ibatis.sqlmap.engine.impl.SqlMapClientDelegate=debug 
log4j.logger.java.sql.Connection=debug 
log4j.logger.java.sql.Statement=debug 
log4j.logger.java.sql.PreparedStatement=debug 
log4j.logger.java.sql.ResultSet=debug 
log4j.logger.org.tuckey.web.filters.urlrewrite.UrlRewriteFilter=debug

######################################################################################
# Console Appender  \u65e5\u5fd7\u5728\u63a7\u5236\u8f93\u51fa\u914d\u7f6e
######################################################################################
log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender
log4j.appender.Threshold=error
log4j.appender.CONSOLE.Target=System.out
log4j.appender.CONSOLE.layout=org.apache.log4j.PatternLayout
log4j.appender.CONSOLE.layout.ConversionPattern= [%p] %d %c - %m%n


######################################################################################
# DailyRolling File  \u6bcf\u5929\u4ea7\u751f\u4e00\u4e2a\u65e5\u5fd7\u6587\u4ef6\uff0c\u6587\u4ef6\u540d\u683c\u5f0f:log2009-09-11
######################################################################################
log4j.appender.file=org.apache.log4j.DailyRollingFileAppender
log4j.appender.file.DatePattern=yyyy-MM-dd
log4j.appender.file.File=log.log
log4j.appender.file.Append=true
log4j.appender.file.Threshold=error
log4j.appender.file.layout=org.apache.log4j.PatternLayout
log4j.appender.file.layout.ConversionPattern=%d{yyyy-M-d HH:mm:ss}%x[%5p](%F:%L) %m%n


log4j.logger.com.opensymphony.xwork2=error  

```

```properties
log4j.rootLogger=DEBUG,CONSOLE,file
#log4j.rootLogger=ERROR,ROLLING_FILE
log4j.logger.cn.smbms.dao=debug
log4j.logger.com.ibatis=debug 
log4j.logger.com.ibatis.common.jdbc.SimpleDataSource=debug 
log4j.logger.com.ibatis.common.jdbc.ScriptRunner=debug 
log4j.logger.com.ibatis.sqlmap.engine.impl.SqlMapClientDelegate=debug 
log4j.logger.java.sql.Connection=debug 
log4j.logger.java.sql.Statement=debug 
log4j.logger.java.sql.PreparedStatement=debug 
log4j.logger.java.sql.ResultSet=debug 
log4j.logger.org.tuckey.web.filters.urlrewrite.UrlRewriteFilter=debug

######################################################################################
# Console Appender  \u65e5\u5fd7\u5728\u63a7\u5236\u8f93\u51fa\u914d\u7f6e
######################################################################################
log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender
log4j.appender.Threshold=error
log4j.appender.CONSOLE.Target=System.out
log4j.appender.CONSOLE.layout=org.apache.log4j.PatternLayout
log4j.appender.CONSOLE.layout.ConversionPattern= [%p] %d %c - %m%n

######################################################################################
# DailyRolling File  \u6bcf\u5929\u4ea7\u751f\u4e00\u4e2a\u65e5\u5fd7\u6587\u4ef6\uff0c\u6587\u4ef6\u540d\u683c\u5f0f:log2009-09-11
######################################################################################
log4j.appender.file=org.apache.log4j.DailyRollingFileAppender
log4j.appender.file.DatePattern=yyyy-MM-dd
log4j.appender.file.File=log.log
log4j.appender.file.Append=true
log4j.appender.file.Threshold=error
log4j.appender.file.layout=org.apache.log4j.PatternLayout
log4j.appender.file.layout.ConversionPattern=%d{yyyy-M-d HH:mm:ss}%x[%5p](%F:%L) %m%n

log4j.logger.com.opensymphony.xwork2=error  

```


```properties
# 黑马视频里的log4j文件
# Set root category priority to INFO and its only appender to CONSOLE
#log4j.rootCategory=INFO,CONSOLE             debug   info   warn error fatal
log4j.rootCategory=debug, CONSOLE, LOGFILE

# Set the enterprise logger category to FATAL and its only appender to CONSOLE
log4j.logger.org.apache.axis.enterprise=FATAL, CONSOLE

# CONSOLE is set to be a ConsoleAppender using a PatternLayout.
log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender
log4j.appender.CONSOLE.layout=org.apache.log4j.PatternLayout
log4j.appender.CONSOLE.layout.ConversionPattern=%d{ISO8601} %-6r [%15.15t] %-5p %30.30c %x - %m\n

# LOGFILE is set to be a File appender using a PatternLayout.
log4j.appender.LOGFILE=org.apache.log4j.FileAppender
log4j.appender.LOGFILE.File=d:\axis.log
log4j.appender.LOGFILE.Append=true
log4j.appender.LOGFILE.layout=org.apache.log4j.PatternLayout
log4j.appender.LOGFILE.layout.ConversionPattern=%d{ISO8601} %-6r [%15.15t] %-5p %30.30c %x - %m\n


```



# Spring MyBatis

https://mybatis.org/spring/
https://mvnrepository.com/artifact/org.mybatis/mybatis-spring/3.0.3
https://docs.spring.io/spring-data/relational/reference/jdbc/mybatis.html
https://docs.spring.io/spring-data/jdbc/docs/current/api/org/springframework/data/jdbc/mybatis/MyBatisDataAccessStrategy.html




# SpringBoot MyBatis


https://mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/
https://mvnrepository.com/artifact/org.mybatis.spring.boot/mybatis-spring-boot-starter/3.0.3


```java



/*
# 配置数据源
spring.datasource.name=dev
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/test
spring.datasource.username=root
spring.datasource.password=123456


# mapper配置文件
mybatis.mapper-locations=classpath:/mapper/*.xml
# pojo实体类类路径
mybatis.type-aliases-package=com.example.mybatisspringboot.pojo

*/
//启动类
@MapperScan(basePackages = "com.example.mybatisspringboot.mapper")

@Mapper
public interface UserMapper(){
    @Select("select * from user")
    List<User> findAll();
}

@RunWith(SpringRunner.class)
@SpringBootTest
class MybatisSpringbootApplicationTests {
    @Autowired
    private UserMapper userMapper;
    @Test
    void contextLoads() {
        List<User> userList = userMapper.findAll();
        System.out.println(userList);
    }
}


```




# PageHelper


https://mybatis.io/
https://mybatis.io/plugins.html
https://pagehelper.github.io/
https://github.com/pagehelper/Mybatis-PageHelper/blob/master/wikis/zh/HowToUse.md
https://cloud.tencent.com/developer/article/1781228



MyBatis 分页插件

```java

public void test1() {
    PageHelper.startPage(1, 3);
    List<User> users = userMapper.findAll();
    PageInfo<User> pageInfo = new PageInfo<>(users);
    System.out.println(pageInfo.getList());
}

```


```xml
<!-- 普通依赖 -->
<!-- maven com.github.pagehelper pagehelper 4.1.4 -->

<!-- plugins标签在environments标签之前 -->
<plugins>
    <!-- 配置拦截器 -->
    <plugin interceptor="com.github.pagehelper.PageInterceptor">
        <!-- 设置数据库类型，六大数据库之一，Oracle,Mysql,MariaDB,SQLite,Hsqldb,PostgreSQL -->
        <property name="helperDialect" value="mysql"/>
    </plugin>
    
</plugins>


<!-- 详细版本 -->
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE configuration
    PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
    "http://mybatis.org/dtd/mybatis-3-config.dtd">

<configuration>
  <plugins>
    <plugin interceptor="com.github.pagehelper.PageInterceptor">
      <!-- 该参数默认为false -->
      <!-- 设置为true时，会将RowBounds第一个参数offset当成pageNum页码使用 -->
      <!-- 和startPage中的pageNum效果一样-->
      <property name="offsetAsPageNum" value="true"/>
      <!-- 该参数默认为false -->
      <!-- 设置为true时，使用RowBounds分页会进行count查询 -->
      <property name="rowBoundsWithCount" value="true"/>
      <!-- 设置为true时，如果pageSize=0或者RowBounds.limit = 0就会查询出全部的结果 -->
      <!-- （相当于没有执行分页查询，但是返回结果仍然是Page类型）-->
      <property name="pageSizeZero" value="true"/>
      <!-- 3.3.0版本可用 - 分页参数合理化，默认false禁用 -->
      <!-- 启用合理化时，如果pageNum<1会查询第一页，如果pageNum>pages会查询最后一页 -->
      <!-- 禁用合理化时，如果pageNum<1或pageNum>pages会返回空数据 -->
      <property name="reasonable" value="true"/>
      <!-- 3.5.0版本可用 - 为了支持startPage(Object params)方法 -->
      <!-- 增加了一个`params`参数来配置参数映射，用于从Map或ServletRequest中取值 -->
      <!-- 可以配置pageNum,pageSize,count,pageSizeZero,reasonable,orderBy,不配置映射的用默认值 -->
      <!-- 不理解该含义的前提下，不要随便复制该配置 -->
      <property name="params" value="pageNum=start;pageSize=limit;"/>
      <!-- 支持通过Mapper接口参数来传递分页参数 -->
      <property name="supportMethodsArguments" value="true"/>
      <!-- always总是返回PageInfo类型,check检查返回类型是否为PageInfo,none返回Page -->
      <property name="returnPageInfo" value="check"/>
    </plugin>
  </plugins>
</configuration>

```


```xml
<!-- spring 配置 -->
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
  <!-- 注意其他配置 -->
  <property name="plugins">
    <array>
      <bean class="com.github.pagehelper.PageInterceptor">
          <property name="properties">
              <!--使用下面的方式配置参数，一行配置一个 -->
              <value>
                  params=value1
              </value>
          </property>
      </bean>
    </array>
  </property>
</bean>


```

```properties

springBoot 配置
com.github.pagehelper:pagehelper-spring-boot-starter:1.4.3

springboot不需要配置pagehelper就能生效
pagehelper.propertyName=propertyValue
pagehelper.reasonable=false
pagehelper.defaultCount=true


```


# 源码分析


mybatis-3-mybatis-3.5.4.zip
spring-mybatis-spring-2.0.4.zip

下载3.5.4解压并用idea打开,删掉licenses.txt文件编译便能通过





