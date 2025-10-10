

https://hibernate.org/ Hibernate 持久层框架



# mysql-connector-j

https://docs.oracle.com/javase/8/docs/api/index.html?java/sql/DriverManager.html
https://blog.csdn.net/m0_62314761/article/details/131078526
https://blog.csdn.net/qq_60955261/article/details/126737615


com.mysql:mysql-connector-j:8.3.0

```java
DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver());
// Class.forName("com.mysql.cj.jdbc.Driver");// 黑马30个文件夹spring 第一天 09程序的耦合和解耦思路分析
Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/eesy", "root", "0000");
PreparedStatement preparedStatement = connection.prepareStatement("select * from account;");
ResultSet resultSet = preparedStatement.executeQuery();
while (resultSet.next()) {
    System.out.println(resultSet.getString("id")+" ");
    System.out.println(resultSet.getString("name")+" ");
    System.out.println(resultSet.getString("money"));
}
resultSet.close();
preparedStatement.close();
connection.close();

```


```java
//如果没有jar包，这个语句编译期间就报错
DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver());
//切换成这个语句，可以编译通过，仅仅是运行期间才会报错
Class.forName("com.mysql.cj.jdbc.Driver");
Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/eesy", "root", "0000");
PreparedStatement preparedStatement = connection.prepareStatement("select * from account");
ResultSet resultSet = preparedStatement.executeQuery();
while (resultSet.next()){System.out.print(resultSet.getString("name"));}
resultSet.close();
preparedStatement.close();
connection.close();

```


```java
//utils
public class JDBCUtils {
    protected static String driver = null;
    protected static String url = null;
    protected static String username = null;
    protected static String password = null;

    protected Connection connection = null;
    protected PreparedStatement preparedStatement = null;
    protected ResultSet resultSet = null;

    static {
        init("db.properties");
    }

    public static void init(String mysqlProperties) {
        Properties properties = new Properties();
        InputStream inputStream = BaseDao.class.getClassLoader().getResourceAsStream(mysqlProperties);
        try {
            properties.load(inputStream);
        } catch (IOException e) {
            e.printStackTrace();
        }
        driver = properties.getProperty("jdbc.driver");
        url = properties.getProperty("jdbc.url");
        username = properties.getProperty("jdbc.username");
        password = properties.getProperty("jdbc.password");
    }

    public Connection createConnection() {
        try {
            Class.forName(driver);
            connection = DriverManager.getConnection(url, username, password);
        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        }
        return connection;
    }

    public void closeResources(ResultSet resultSet, PreparedStatement preparedStatement, Connection connection) {
        if (resultSet != null) {
            try {
                resultSet.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        if (preparedStatement != null) {
            try {
                preparedStatement.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        if (connection != null) {
            try {
                connection.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }

    public int update(String sql, Object... params) {
        int count = 0;
        this.createConnection();
        try {
            preparedStatement = connection.prepareStatement(sql);
            if (params != null) {
                for (int i = 0; i < params.length; i++) {
                    preparedStatement.setObject(i + 1, params[i]);
                }
            }
            count = preparedStatement.executeUpdate();
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            closeResources(null, preparedStatement, connection);
        }
        return count;
    }

    public ResultSet query(String sql, Object... params) {
        this.createConnection();
        try {
            preparedStatement = connection.prepareStatement(sql);
            if (params != null) {
                for (int i = 0; i < params.length; i++) {
                    preparedStatement.setObject(i + 1, params[i]);
                }
            }
            resultSet = preparedStatement.executeQuery();
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return resultSet;
    }
}


```


# JDBC数据源配置

```xml

<!-- 

file:jdbc.properties
jdbc.driver=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/db_smbms?serverTimezone=Asia/Shanghai
jdbc.username=root
jdbc.password=0000

?serverTimezone=UTC
?useUnicode=true&characterEncoding=utf8&autoReconnect=true&allowMultiQueries=true&useSSL=false
-->

```




# Commons


https://commons.apache.org/proper/commons-pool/
https://mvnrepository.com/artifact/commons-pool/commons-pool/1.6
https://mvnrepository.com/artifact/org.apache.commons/commons-pool2/2.11.1





https://commons.apache.org/proper/commons-dbcp/
https://mvnrepository.com/artifact/commons-dbcp/commons-dbcp/1.4
https://mvnrepository.com/artifact/org.apache.commons/commons-dbcp2/2.12.0


https://commons.apache.org/proper/commons-dbutils/
https://commons.apache.org/proper/commons-dbcp/index.html DBCP



commons-dbutils::commons-dbutils::1.4

```java
/*配置数据源*/
ComboPooledDataSource dataSource = new ComboPooledDataSource();
dataSource.setDriverClass("com.mysql.cj.jdbc.Driver");
dataSource.setJdbcUrl("jdbc:mysql://localhost:3306/eesy");
dataSource.setUser("root");
dataSource.setPassword("0000");


/*spring内置数据源*/
import org.springframework.jdbc.datasource.DriverManagerDataSource;
DriverManagerDataSource ds = new DriverManagerDataSource();
ds.setDriverClassName("com.mysql.cj.jdbc.Driver");
ds.setUrl("jdbc:mysql://localhost:3366/test");
ds.setUsername("root");
ds.setPassword("0000");

```

```java
/**/
import com.mchange.v2.c3p0.ComboPooledDataSource;
import org.apache.commons.dbutils.QueryRunner;
public void test(){
    ComboPooledDataSource dataSource = new ComboPooledDataSource();
    dataSource.setDriverClass("com.mysql.cj.jdbc.Driver");
    dataSource.setJdbcUrl("jdbc:mysql://localhost:3306/eesy");
    dataSource.setUser("root");
    dataSource.setPassword("0000");
    QueryRunner runner = new QueryRunner(dataSource);
    List<Account> findAll = runner.query("select * from account", new BeanListHandler<Account>(Account.class));
    System.out.println(findAll);
    Account findOne = runner.query("select * from account where id = ?", new BeanHandler<Account>(Account.class), 1);
    System.out.println(findOne);
    Account account = new Account();
    account.setId(4);
    account.setName("ddd");
    account.setMoney(1000.0f);
    int insert = runner.update("insert into account(name,money) values (?, ?)", account.getName(), account.getMoney());
    System.out.println(insert);
    account.setMoney(2000.0f);
    int update = runner.update("update account set name = ?, money = ? where id = ?", account.getName(), account.getMoney(), account.getId());
    System.out.println(update);
    int delete = runner.update("delete from account where id = ?", 4);
    System.out.println(delete);
}

```


# HikariCP

https://mvnrepository.com/tags/pool
https://mvnrepository.com/artifact/com.zaxxer/HikariCP/5.0.1
https://github.com/brettwooldridge/HikariCP



# BoneCP

https://github.com/wwadge/bonecp
https://mvnrepository.com/artifact/com.jolbox/bonecp/0.8.0.RELEASE

# c3p0

https://www.mchange.com/projects/c3p0/
https://mvnrepository.com/artifact/com.mchange/c3p0/0.9.5.5


```java
// c3p0数据源
import com.mchange.v2.c3p0.ComboPooledDataSource;
/*配置数据源*/
ComboPooledDataSource dataSource = new ComboPooledDataSource();
dataSource.setDriverClass("com.mysql.cj.jdbc.Driver");
dataSource.setJdbcUrl("jdbc:mysql://localhost:3306/eesy");
dataSource.setUser("root");
dataSource.setPassword("0000");


```


# Druid


https://github.com/alibaba/druid
https://mvnrepository.com/artifact/com.alibaba/druid/1.2.23



# H2 Database Engine


https://h2database.com/html/main.html
https://mvnrepository.com/artifact/com.h2database/h2/2.2.224

Java SQL Database



# Spring JDBC

https://spring.io/projects/spring-data

https://mvnrepository.com/artifact/org.springframework.data
https://mvnrepository.com/artifact/org.springframework/spring-jdbc/6.1.13

spring框架有很多操作模板类
关系型JdbcTemplate HibernateTemplate
nosql数据库 RedisTemplate
操作消息队列 JmsTemplate

```java
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration("classpath:applicationContext.xml")
public class JdbcTemplateCRUDTest {
    @Autowired
    private JdbcTemplate jdbcTemplate;

@Test //代码使用版
public void test1() throws Exception {
    // import com.mchange.v2.c3p0.ComboPooledDataSource; 
    ComboPooledDataSource dataSource = new ComboPooledDataSource();
    dataSource.setDriverClass("com.mysql.cj.jdbc.Driver");
    dataSource.setJdbcUrl("jdbc:mysql://localhost:3306/test");
    dataSource.setUser("root");
    dataSource.setPassword("0000");

    /*spring内置数据源
    import org.springframework.jdbc.datasource.DriverManagerDataSource;
    DriverManagerDataSource ds = new DriverManagerDataSource();
    ds.setDriverClassName("com.mysql.cj.jdbc.Driver");
    ds.setUrl("jdbc:mysql://localhost:3366/test");
    ds.setUsername("root");
    ds.setPassword("0000");*/

    JdbcTemplate jdbcTemplate = new JdbcTemplate();
    jdbcTemplate.setDataSource(dataSource);
    // 不带参数的sql执行语句
    jdbcTemplate.execute("insert into test(string) values ('string')");
    // 查询所有
    List<Account> accountList = jdbcTemplate.query("select * from test", new BeanPropertyRowMapper<Account>(Account.class)); System.out.println(accountList);
    // 查询一个
    Account account = jdbcTemplate.queryForObject("select * from test where id=?", new BeanPropertyRowMapper<Account>(Account.class), 1); System.out.println(account);
    // 查询总数
    Long count = jdbcTemplate.queryForObject("select count(*) from test", Long.class); System.out.println(count);
    // 获取第一个匹配的数据
    List<Account> accounts = jdbcTemplate.query("select * from account where name= ?", new BeanPropertyRowMapper<Account>(Account.class), "John");
    if (accounts.size() >= 1) accounts.get(0);//获取第一个匹配的数据
    // 更新数据
    int row = jdbcTemplate.update("update test set string=? where id=?", "修改", 17); System.out.println(row);
    // 插入数据
    int row = jdbcTemplate.update("insert into test(string) values (?)", "string001"); System.out.println(row);
}}

```

```xml
<!-- 配置信息版
jdbc.driver=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/test
jdbc.username=root
jdbc.password=0000
-->
<!-- 扫描properties文件 -->
<context:property-placeholder location="classpath:jdbc.properties"/>
<bean id="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource">
    <property name="driverClass" value="${jdbc.driver}"/>
    <property name="jdbcUrl" value="${jdbc.url}"/>
    <property name="user" value="${jdbc.username}"/>
    <property name="password" value="${jdbc.password}"/>
</bean>
<bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
    <property name="dataSource" ref="dataSource"/>
</bean>
<!--
ApplicationContext app = new ClassPathXmlApplicationContext("applicationContext.xml");
JdbcTemplate jdbcTemplate = app.getBean("jdbcTemplate", JdbcTemplate.class);
-->

```


```java
// JdbcDaoSupport是impl的支持写法，但是需要配置数据源
public class AccountDaoImpl extends JdbcDaoSupport implements AccountDao {
    public AccountDaoImpl() {
        System.out.println("init");
        DriverManagerDataSource dataSource = new DriverManagerDataSource();
        dataSource.setDriverClassName("com.mysql.cj.jdbc.Driver");
        dataSource.setUrl("jdbc:mysql://localhost:3306/test");
        dataSource.setUsername("root");
        dataSource.setPassword("0000");
        super.setDataSource(dataSource);
        //省略掉配置数据源方法可以这样写
        /*<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
            <property name="driverClassName" value="${jdbc.driver}"/>
            <property name="url" value="${jdbc.url}"/>
            <property name="username" value="${jdbc.username}"/>
            <property name="password" value="${jdbc.password}"/>
        </bean>
        <bean id="accountDao" class="com.itheima.dao.AccountDaoImpl">
            <property name="dataSource" ref="ds2"/>
        </bean>*/
    }
    @Override
    public List<Account> findAll() {
        List<Account> query = super.getJdbcTemplate().query("select * from test", new BeanPropertyRowMapper<Account>(Account.class));
        return query;
    }
}


```












# SpringBoot



https://mvnrepository.com/artifact/com.alibaba/druid-spring-boot-starter/1.2.23



```yml
spring:
  datasource:
    # 配置数据源
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/test
    username: root
    password: 0000
    type: com.alibaba.druid.pool.DruidDataSource


# 或者
spring:
  datasource:
    druid: 
      # druid专用配置数据源
      driver-class-name: com.mysql.cj.jdbc.Driver
      url: jdbc:mysql://localhost:3306/test
      username: root
      password: 0000

```






