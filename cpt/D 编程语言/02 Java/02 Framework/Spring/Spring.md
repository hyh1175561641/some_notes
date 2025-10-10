


微服务论文 https://martinfowler.com/articles/microservices.html
论文翻译 https://www.kuangstudy.com/bbs/1364150595472072706






https://spring.io/
https://spring.io/projects/spring-framework


https://mvnrepository.com/artifact/org.springframework
https://mvnrepository.com/artifact/org.springframework/spring-aop/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-aspects/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-beans/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-context/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-context-indexer/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-context-support/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-core/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-jcl/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-test/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-tx/6.1.13


https://mvnrepository.com/artifact/org.springframework/spring-instrument/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-jms/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-messaging/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-orm/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-oxm/6.1.13





# Spring DI

```xml
<!-- 包括DI和AOP -->
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:p="http://www.springframework.org/schema/p"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xmlns:tx="http://www.springframework.org/schema/tx"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:task="http://www.springframework.org/schema/cache"

       xsi:schemaLocation="http://www.springframework.org/schema/beans
	http://www.springframework.org/schema/beans/spring-beans.xsd

	http://www.springframework.org/schema/aop 
	http://www.springframework.org/schema/aop/spring-aop.xsd

	http://www.springframework.org/schema/tx 
	http://www.springframework.org/schema/tx/spring-tx.xsd

	http://www.springframework.org/schema/context
	http://www.springframework.org/schema/context/spring-context.xsd 

    http://www.springframework.org/schema/cache
    http://www.springframework.org/schema/cache/spring-cache.xsd">
    <!-- beans用来创建类，依赖注入 -->
    <!-- context用来加载外部properties文件 -->
    <!-- file:jdbc.properties
    jdbc.driver=com.mysql.cj.jdbc.Driver
    jdbc.url=jdbc:mysql://localhost:3306/db_smbms
    jdbc.username=root
    jdbc.password=0000
    -->
    <!-- 使用context使用properties文件 -->
    <context:property-placeholder location="classpath:jdbc.properties"/>
    <bean id="userDao" class="com.itheima.dao.impl.UserDaoImpl">
        <property name="driver" value="${jdbc.driver}"/>
        <property name="url" value="${jdbc.url}"/>
        <property name="user" value="${jdbc.username}"/>
        <property name="pass" value="${jdbc.password}"/>
    </bean>

    <!-- 1.注解扫描器 包掃描  -->
    <context:component-scan base-package="com.chaiyi">
        <!--排除Controller注解   不扫描Controller注解-->
        <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
    </context:component-scan>

    <!--2.指定外部属性文件的位置/引入properties文件 -->
    <context:property-placeholder location="classpath:jdbc.properties"/>

    <!--3. 使用jdbc数据源 连接池 -->
    <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
        <property name="driverClassName" value="${jdbc.driver}"></property>
        <property name="url" value="${jdbc.url}"></property>
        <property name="password" value="${jdbc.password}"></property>
        <property name="username" value="${jdbc.username}"></property>
    </bean>

    <!--4.配置mybatis sqlsessionFactory -->
    <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
        <!--注入数据源-->
        <property name="dataSource" ref="dataSource"></property>
        <!--关联mybatis配置文件-->
        <property name="configLocation" value="classpath:mybatis.xml"></property>
        <property name="typeAliasesPackage" value="com.chaiyi.entity"></property>
        <!--将mpper.xml的配置文件放在resources中的mappers里-->
        <property name="mapperLocations" value="classpath:mapper/*.xml"></property>
        <!--<property name="plugins">
         <array>
            <bean class="com.github.pagehelper.PageInterceptor">
               <property name="properties"   value="mysql"></property>  鏈接mysql數據庫
            </bean>
         </array>
       </property> -->
    </bean>

    <!--5.配置jdbc事务管理器 -->
    <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        <property name="dataSource" ref="dataSource"></property>
    </bean>

    <!--事务模板 编程式事务 -->
    <bean id="transactionTemplate" class="org.springframework.transaction.support.TransactionTemplate">
        <property name="transactionManager" ref="transactionManager"></property>
    </bean>

    <!-- 声明式事务  基于注解(事务注解驱动) -->
    <tx:annotation-driven transaction-manager="transactionManager"/>

    <!--定时任务注解驱动-->
    <!--	<task:annotation-driven></task:annotation-driven>-->

    <!--6.配置事务 transaction-manager:表示关联的事务管理器是谁 声明式 基于aop -->
    <tx:advice transaction-manager="transactionManager" id="txa">
        <!--事务属性配置-->
        <tx:attributes>
            <!-- find select get开头的方法为只读事务,用来提高数据库,用来提高数据库的性能
            所有添加修改删除操作不能以下列字符串开头-->
            <tx:method name="find*" read-only="true"/>
            <tx:method name="select*" read-only="true"/>
            <tx:method name="get*" read-only="true"/>
            <tx:method name="load*" read-only="true"/>
            <tx:method name="list*" read-only="true"/>
            <tx:method name="login*" read-only="true"/>
            <!--其他的方法为默认事务-->
            <tx:method name="*" isolation="DEFAULT" propagation="REQUIRED"/>
            <!--    <tx:method name="find*"  read-only="true"/> -->
        </tx:attributes>
    </tx:advice>
    <!--7.配置aop-->
    <aop:config>
        <!--配置切点表达式  tx(pointcut),txa(txAdvice)-->
        <aop:pointcut expression="execution(* com.chaiyi.service.Impl.*.*(..))" id="tx"/>
        <!--关联事务-->
        <aop:advisor advice-ref="txa" pointcut-ref="tx"/>
    </aop:config>

    <!-- aop 切面注解 -->
    <aop:aspectj-autoproxy></aop:aspectj-autoproxy>

    <!--8.扫描mapper/dao接口掃描  -->
    <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
        <!--basePackage:mapper接口所在的包-->
        <property name="basePackage" value="com.chaiyi.dao"></property>
    </bean>
    <!--9.引入spring-redis2.xml文件-->
    <import resource="classpath:spring-redis.xml"></import>
    <!--10.引入生产者spring-kafka-producer.xml文件-->
    <import resource="classpath:spring-kafka-producer.xml"></import>
    <!--11.引入消费者spring-kafka-consumer.xml文件-->
    <import resource="classpath:spring-kafka-consumer.xml"></import>
    <!--9.引入spring-es.xml文件-->
    <import resource="classpath:spring-es.xml"></import>
</beans>

<!-- 版权声明：本文为CSDN博主「大风~刮过」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。原文链接：https://blog.csdn.net/qq_55428258/article/details/123398356 -->


```



# Spring IoC



Data Access/Integration: JDBC ORM OXM JMS Transactions
Web: Web Portlet
AOP Aspects Instrumentation Messaging
Core Container: 

```
这些包都相互依赖，梳理一下包之间的依赖关系，core是其他框架运行的核心基础

```

```dir
docs 文档
libs jar包
schema 约束
license.txt
notice.txt
readme.txt
```


https://repo.spring.io/ui/native/libs-release-local/org/springframework/spring/


高内聚，低耦合

类之间的依赖ioc解决
方法之间的依赖aop解决






Inversion of Control: IoC控制反转 把创建对象的权力交给框架
IoC包括依赖注入和依赖查找 Dependency Injection DI依赖注入，Dependency Lookup依赖查找
明确IoC的作用，消减计算机程序的耦合，解除我们代码中的依赖关系
Aspect Oriented Programming: AOP面向切面编程 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       http://www.springframework.org/schema/context/spring-context.xsd">

<!--
    Spring注解：
    <context:component-scan base-package="com.itheima"/>启动扫描
   
    <bean id="userDao" class="com.itheima.dao.UserDaoImpl"
    scope="singleton/prototype" init-method="init" destroy-method="destroy"/>

    1用于创建对象
    @Component("userDao") 相当于id属性，默认值是当前类名首字母小写，写在类名上面
    @Controller 与Component一样，写在表现层
    @Service 与Component一样，写在业务层
    @Repository 与Component一样，写在持久层
    
    2用于注入数据 相当于property标签 写在成员变量上面或者方法参数前面
    @Autowired 自动按照类型注入，只要容器中有唯一bean对象就能注入，先比较类型，后比较变量名和id
    @Qualifier("userDaoImpl") 不能单独使用，在Autowired基础上再按照名称注入，类成员不能单独使用，给方法参数可以单独使用
    @Resource("userDaoImpl") 直接按照id注入，Autowired和Qualifier的合体，可以独立使用
    @Value() 用于注入基本类型和String类型，可以使用spring的SpEL(EL表达式) SpEL写法 ${}
    
    3用于改变作用范围
    @Scope("prototype") 默认singleton，写在类名上面

    4生命周期注解
    @PostConstruct 相当于init-method="init" 写在方法上面
    @PreDestroy 相当于destroy-method="destroy" 调用app.close()执行销毁方法

    集合类型只能通过xml实现

    新注解看下面
 -->
    <!-- scope单例/多例, init初始化方法, destroy销毁方法-->
    <bean id="userDao" class="com.itheima.dao.UserDaoImpl"
    scope="singleton单例/prototype多例/request web请求/session web会话/global-session 集群环境的会话范围，当不是集群时，他就是session"
    init-method="init" destroy-method="destroy">
        <constructor-arg value="构造方法"/>
    </bean>
    <!-- 
    单例对象：容器创建时，对象创建，容器销毁对象销毁
    多例对象：对象使用时创建，JVM自动销毁
    -->
    <bean id="userDao" class="com.itheima.dao.UserDaoImpl" 
    init-method="init" destroy-method="destroy"></bean>

    <!-- 依赖注入 -->
    <!-- 正常获取Bean对象，可以注入的对象有三类，基本类型，String，其他在注解中配置的Bean类型，复杂类型，集合类型 -->
    <!-- 注入的方式：构造函数注入，使用set方法提供，使用注解提供 -->
    <bean id="userDao" class="com.itheima.dao.UserDaoImpl"/>
    <bean id="userService" class="com.itheima.service.UserServiceImpl">
        <property name="userDao" ref="userDao"/>
    </bean>

    <!-- 获取Bean对象的值, 经常使用jar包中的类 -->
    <!--想要通过这个工厂方法获取userDao并存入Spring容器中-->
    <!--InstanceFactory factory = new InstanceFactory();-->
    <!--UserDao userDao = factory.getUserDao();-->
    <bean id="instanceFactory" class="com.itheima.factory.InstanceFactory"/>
    <bean id="userDaoImpl" factory-bean="instanceFactory" factory-method="getUserDao"></bean>
    <!-- 获取静态工厂方法当中的对象 -->
    <!--UserDao userDao = StaticFactory.getUserDao();-->
    <bean id="userDao" class="com.itheima.factory.StaticFactory" factory-method="getUserDao"/>
    
    <!-- 构造方法注入参数 type index name value ref 
    type 指定参数的类型，一般写全类名
    index 指定第几个参数，从0开始，但是一般用name
    name 指定构造函数的参数名称
    value 参数的值 ref 参数的引用-->
    <bean class="com.itheima.dao.UserDaoImpl" id="userDaoImpl">
        <constructor-arg type="java.lang.String" name="name" value="aaa"/>
        <constructor-arg type="java.lang.Integer" name="age" value="23"/>
        <constructor-arg type="java.util.Date" name="birthday" ref="now"/>
    </bean><bean id="now" class="java.util.Date"/>
    
    <!-- set方法注入 private String name;
    private Integer age;private Date birthday;-->
    <bean class="com.itheima.dao.UserDaoImpl" id="userDaoImpl">
        <property name="name" value="John"/>
        <property name="age" value="24"/>
        <property name="birthday" ref="now"/>
    </bean><bean id="now" class="java.util.Date"/>

<!--    private String[] strings;
        private List<String> list;
        private Set<String> set;
        private Map<String, String> map;
        private Properties properties; 
        结构相同的标签<list> <array> <set>可以互换
        entry标签也能呼唤 <set> <prop>-->
    <bean class="com.itheima.dao.UserDaoImpl" id="userDaoImpl">
        <property name="strings">
            <array>
                <value>string1</value>
                <value>string2</value>
                <value>string3</value>
            </array>
        </property>
        <property name="list">
            <list>
                <value>list1</value>
                <value>list2</value>
                <value>list3</value>
            </list>
        </property>
        <property name="set">
            <set><!--这里可以换成list标签-->
                <value>set1</value>
                <value>set2</value>
                <value>set3</value>
            </set>
        </property>
        <property name="map">
            <map>
                <entry key="key1" value="value1"/>
                <entry key="key2">
                    <value>value2</value>
                </entry>
                <entry key="key3" value="value3"/>
            </map>
        </property>
        <property name="properties">
            <props>
                <prop key="jdbc.driver">com.mysql.cj.jdbc.Driver</prop>
                <prop key="jdbc.url">jdbc:mysql://localhost:3306/test?serverTimezone=Asia/Shanghai</prop>
                <prop key="jdbc.username">root</prop>
                <prop key="jdbc.password">1234</prop>
            </props>
        </property>
    </bean>
</beans>

```

```java
//第一步是创建核心容器对象
//BeanFactory是ApplicationContext的父接口，采取的策略是延迟加载，使用对象时才创建对象
Resource resource = new ClassPathResource("bean.xml");
BeanFactory app = new XmlBeanFactory(resource);
//ApplicationContext，采用了立即加载的策略，读取了配置文件就创建了对象
//获取核心容器对象，常用ClassPathXml来开发
ApplicationContext applicationContext = new ClassPathXmlApplicationContext("bean.xml");//加载类路径下的核心文件
ApplicationContext app = new FileSystemXmlApplicationContext("C:\\Users\\Administrator\\bean.xml");//加载磁盘下的绝对路径
ApplicationContext app = new AnnotationConfigApplicationContext(SpringConfiguration.class);//根据注解创建容器

//第二步是获取对象的方法
//根据id,获取bean对象两种获取bean的方法
((UserDao) applicationContext.getBean("userDao")).save();
applicationContext.getBean("userService", UserService.class).save();

```

```java
// 注解配置
/*  <context:component-scan base-package="com.itheima"/>
    <bean id="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource">
        <property name="driverClass" value="com.mysql.cj.jdbc.Driver"/>
        <property name="jdbcUrl" value="jdbc:mysql://localhost:3306/eesy"/>
        <property name="user" value="root"/>
        <property name="password" value="0000"/>
    </bean>
    <bean id="queryRunner" class="org.apache.commons.dbutils.QueryRunner" scope="prototype">
        <constructor-arg name="ds" ref="dataSource"/>
    </bean>*/
@Configuration //指定当前类是一个配置类
//basePackages和value作用是一样的
@ComponentScan(basePackages = "com.itheima")//配置要扫描的包
//classpath表示类路径下，如果有包 com/itheima/jdbc.properties
@PropertySource("classpath:jdbc.properties")//指定properties文件的路径
public class SpringConfiguration {//这是一个配置类，它的作用和bean.xml是一样的
    
    @Value("${jdbc.driver}")
    private String driver;
    @Value("${jdbc.url}")
    private String url;
    @Value("${jdbc.username}")
    private String username;
    @Value("${jdbc.password}")
    private String password;

    @Bean("queryRuner")//把当前方法的返回值作为bean对象存入容器中,默认值是方法名
    @Scope("prototype")
    public QueryRunner createQueryRunner(@Qualifier("dataSource") DataSource dataSource) {
        return new QueryRunner(dataSource);}

    @Bean("dataSource")
    public DataSource createDataSource() {
        try {
            ComboPooledDataSource dataSource = new ComboPooledDataSource();
            /* jdbc.properties
            jdbc.driver=com.mysql.cj.jdbc.Driver
            jdbc.url=jdbc:mysql://localhost:3306/eesy
            jdbc.username=root
            jdbc.password=0000*/
            dataSource.setDriverClass(driver);
            dataSource.setJdbcUrl(url);
            dataSource.setUser(username);
            dataSource.setPassword(password);
            return dataSource;
        } catch (PropertyVetoException e) {
            throw new RuntimeException(e);}}
}
//获取配置信息
ApplicationContext app = new AnnotationConfigApplicationContext(SpringConfiguration.class);
accountService = app.getBean("accountService", AccountServiceImpl.class);

```




