


# Junit


https://junit.org/junit5/



https://mvnrepository.com/artifact/junit/junit/4.13.2
https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-api/5.10.2



JUnit是一个Java语言的单元测试框架






```java
public class UserTest { // 没有junit包的写法
    public static void main(String[] args) {
        UserTest.test1();
        UserTest.test2();
        UserTest.test3();
    }
    public static void test1() {}
    public static void test2() {}
    public static void test3() {}
}



//规范
被测包名: xxx.xx.pkg
测试包名: xxx.xx.test
被测类名: Hello
测试类名: HelloTest
被测方法名: add()
测试方法名: testAdd()
返回值: void 参数列表: 空参
给测试方法加注解@Test，被测包被测类被测方法都是正常写

//注解
@Before
public void init();//初始化
@After
public void close();//释放资源
@Test
//public String hello(String world){}
public void testHello();

//断言
Assert.assertEquals(正确的值, 真实的值);

public class CalculatorTest {
    @Before/@After
    public void init/close() {
        System.out.println("init/close");
    }
    @Test
    public void testAdd4() {
        Calculator c = new Calculator();
        int result = 0;
        result = c.add(1, 2, 3, 4);
        Assert.assertEquals(10, result);//断言
    }
}



```










# Spring Junit


https://docs.spring.io/spring-framework/reference/testing.html

https://mvnrepository.com/artifact/org.springframework/spring-test/6.1.13





# Boot Junit

https://junit.org/junit5/docs/current/user-guide/#running-tests-build-spring-boot

https://docs.spring.io/spring-boot/reference/testing/index.html


https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-test/3.3.3



```java


@SpringBootTest //后面可以指定启动类和引导类.class
@SpringBootTest(classes = SpringbootApplication.class)//可以写启动引导类
public class SpringBoot1Test {
//测试类如果在引导类所在的包或子包中，无需指定引导类
//否则需要指定引导类
}


```


