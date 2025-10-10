



https://micrometer.io/
https://github.com/micrometer-metrics/micrometer
https://mvnrepository.com/artifact/io.micrometer/micrometer-observation/1.13.6



# Tomcat

https://tomcat.apache.org

https://mvnrepository.com/artifact/org.apache.tomcat/tomcat-servlet-api/10.1.31

https://mvnrepository.com/artifact/org.apache.tomcat.embed/tomcat-embed-core/10.1.31
https://mvnrepository.com/artifact/org.apache.tomcat.embed/tomcat-embed-websocket/10.1.31
https://mvnrepository.com/artifact/org.apache.tomcat.embed/tomcat-embed-el/10.1.31

https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-tomcat/3.3.5














黑窗口一闪而过: 没有配置JAVA_HOME环境变量


常见的Java相关的web服务器软件
webLogic: oracle公司, 大型的JavaEE服务器, 支持所有的JavaEE规范, 收费
webSphere: IBM公司  JBOSS: JBOSS公司
Tomcat: Apache基金组织, 中小型JavaEE服务器,仅仅支持少量的JavaEE规范servlet/jsp。开源的免费的


netstat -ano 显示端口信息


启动和关闭

/bin.shutdown.bat 正常关闭
ctrl+c 命令行窗口会输出关闭信息

```xml
<!-- 修改配置文件conf/server.xml -->
    <Connector port="8080" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443" />
```

部署项目的方式：
直接将项目放到webapps目录下
/hello: 项目的访问路径-->虚拟目录
把war包放到webapps目录下会自动解压缩

```xml
<!-- 部署其他文件的项目 Host标签体中配置 这种在conf/server.xml中配置项目并不安全-->
<!-- docBase项目存放的路径 path虚拟目录 -->
<Context docBase="D:\hello" path="/haha">
<!-- conf/Catalina/localhost新建x.xml -->
<Context docBase="D:\hello"> <!-- 虚拟目录是文件名 -->


Java动态项目的目录结构
  项目的根目录
    WEB-INF目录
      web.xml: web项目的核心配置文件
      classes: 放置字节码文件的目录
      lib: 放置依赖jar包




```








## Servlet

https://jakarta.ee/specifications/servlet/6.0/
https://jakarta.ee/specifications/servlet/6.0/jakarta-servlet-spec-6.0

https://mvnrepository.com/artifact/javax.servlet/servlet-api/2.5
https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api/4.0.1
https://mvnrepository.com/artifact/jakarta.servlet/jakarta.servlet-api/6.0.0



Servlet (Server Applet): 运行在服务端的小程序
Servlet就是一个接口,定义了Java类被浏览器访问到(tomcat识别)的规则




配置资源
```xml
<!-- web.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    
    <!-- 欢迎页面 -->
    <welcome-file-list>
        <welcome-file>test</welcome-file>
    </welcome-file-list>

    <servlet> <!-- 获取资源路径 -->
        <servlet-name>名字</servlet-name>
        <servlet-class>全类名</servlet-class>
    </servlet>
    <servlet-mapping> <!-- 解析请求URL路径 -->
        <servlet-name>名字</servlet-name>
        <url-pattern>虚拟路径</url-pattern>
    </servlet-mapping>

    <servlet>
        <servlet-name>名字</servlet-name>
        <servlet-class>全类名</servlet-class>
        <!-- 默认值：第一次被访问创建,值为负数 -->
        <!-- 在服务器启动时创建,值为0或正数 0-10之间 -->
        <load-on-startup>5</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>名字</servlet-name>
        <url-pattern>虚拟路径</url-pattern>
    </servlet-mapping>
</web-app>
```



```java
@WebServlet(urlPatterns = {"/"})
public class UserServlet extends HttpServlet {
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
		req.setCharacterEncoding("utf-8");
        resp.setCharacterEncoding("utf-8");
        resp.setContentType("text/html;charset=utf-8");
        req.getRequestDispatcher("/index.jsp").forward(req, resp);}
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        this.doPost(req, resp);}
}


```


```java
// 从Servlet3.0开始,支持注解配置替换xml配置
@WebServlet("/demo1") // 可以不写
@WebServlet(urlPatterns="/demo1")
public class ServletDemo implements Servlet{}


```


```java
// 用户自定义一个类,实现Servlet接口,实现其中的方法
// Servlet: public interface Servlet
// GenericServlet: public abstract class GenericServlet implements Servlet, ServletConfig, Serializable
// HttpServlet: public abstract class HttpServlet extends GenericServlet
public class MyServlet implements Servlet{}//实现其中的方法,这个一般不用,Tomcat反射调用自定义类调用service方法
// servlet是单例的,内存中之存在一个对象,可能存在线程安全问题,尽量不要在servlet中定义成员变量,或者不要修改成员变量的值
init()//在servlet被创建时执行, 只会执行一次
getServletConfig()//servlet配置对象
service()//提供服务,每次被访问都执行
getServletInfo()//获取servlet的信息,版本,作者
destroy()//在服务器正常关闭时,在销毁之前执行一次,用于释放资源



```


```java
//request
// ServletRequest: public interface ServletRequest
// HttpServletRequest: public interface HttpServletRequest extends ServletRequest
// RequestDispatcher: public interface RequestDispatcher

//转发,重定向在response
RequestDispatcher getRequestDispatcher(String var1);
void forward(ServletRequest var1, ServletResponse var2);
request.getRequestDispatcher("/otherpage").forward(req,resp);//转发的写法,目标路径是服务器视角写法,不需要加虚拟目录,服务端路径
String getContextPath();//获取虚拟目录,一般用来加一段字符串组成新目录





```

```java
//Response,转发在request
// ServletResponse: public interface ServletResponse
// HttpServletResponse: public interface HttpServletResponse extends ServletResponse
//设置响应消息
String getCharacterEncoding()
void setCharacterEncoding(String var1)

//设置响应行HTTP/1.1 200 OK
setStatus(int sc) 设置状态码
//设置响应头
setHeader(String name, String value)
//设置响应体,获取输出流
PrintWriter getWriter();//字符输出流
ServletOutputStream getOutputStream();//字节输出流

//重定向
response.setStatus("302");response.setHead("location","/otherpage");//普通写法
void sendRedirect(String var1)//正常写法,客户端路径,需要加虚拟路径,需要动态获取虚拟路径

//forwar和redirect的区别
//重定向：让浏览器自己找新资源,地址栏发生变化,可以访问其他站点资源,是两次请求,不能使用request对象共享数据<a><form>都是客户端的内容
//转发: 服务器帮忙找到新资源传给浏览器,转发只能访问当前服务器,转发只能访问当前服务器,转发是一次请求,可以使用request对象共享数据
// 相对路径：找到当前资源和目标资源的关系,不推荐使用

```



```java
String userName = req.getParameter("userName");
String password = req.getParameter("password");
System.out.println("LoginServlet" + "--" + userName + "--" + password);
if ("zhangsan".equals(userName) && "123123".equals(password)) {
    req.getSession().setAttribute("user", userName);
    req.getRequestDispatcher("admin.jsp").forward(req, resp);
} else {resp.sendRedirect("login.jsp");}

```








## JSP

https://jakarta.ee/specifications/pages/4.0/
https://jakarta.ee/specifications/pages/4.0/jakarta-server-pages-spec-4.0

https://github.com/eclipse-ee4j/jsp-api
https://projects.eclipse.org/projects/ee4j.jsp
https://mvnrepository.com/artifact/javax.servlet.jsp/jsp-api/2.1
https://mvnrepository.com/artifact/javax.servlet.jsp/javax.servlet.jsp-api/2.3.3
https://mvnrepository.com/artifact/jakarta.servlet.jsp/jakarta.servlet.jsp-api/4.0.0



## EL

https://jakarta.ee/specifications/expression-language/6.0/
https://jakarta.ee/specifications/expression-language/6.0/jakarta-expression-language-spec-6.0

https://jakartaee.github.io/expression-language/
https://projects.eclipse.org/projects/ee4j.el
https://github.com/jakartaee/expression-language
https://mvnrepository.com/artifact/javax.el/el-api/2.2
https://mvnrepository.com/artifact/javax.el/javax.el-api/3.0.0
https://mvnrepository.com/artifact/jakarta.el/jakarta.el-api/6.0.1




Expression Language EL表达式，使开发人员无需在jsp页面中嵌入Java代码
可以在不同的作用域内取得属性值，page,request,session,application等

```jsp
//使用EL表达式使代码更简便
<%查看员工的计算机的厂商信息
Employee employee = (Employee) request.getAttribute("employee");
Computer comp = employee.getComputer();
String manufacturer = comp.getManufacturer();
%>
可以写成: ${requestScope.employee.computer.manufacturer}
```




```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
<%@ taglib prefix="x" uri="http://java.sun.com/jsp/jstl/xml" %>
<%@ taglib prefix="sql" uri="http://java.sun.com/jsp/jstl/sql" %>
<%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions" %>




<!-- 判断 -->
<c:if test="${empty isLogin}">
    <c:redirect url="login.jsp"/>
</c:if>



<!-- 循环 -->
<c:forEach var="news" item="${requestScope.newsList}">
  <h1>${news.getId()}</h1>
  <h1>${news.id}</h1>
  <h1>${news["id"]}</h1><!--如果属性名字使用了点或杠操作符，就需要使用这个操作符-->
</c:forEach>

<!-- String[] array={"a","b","c"}; -->
<!-- req.setAttribute("array", array); -->
<h1>${array[1]}</h1><!-- 如果遇到数组,也可以根据索引值访问其中元素 -->


```

```jsp
<!-- 运算符 -->
==  eq  等于
!=  ne  不等于
<   lt  小于
>   gt  大于
<=  le  小于等于
>=  ge  大于等于
&&  and 与
||  or  或
!   not 非
${Empty a} <!--Empty操作符监测变量值是否为空,字符串长度为0,集合长度为0-->



```


可以下载Jakarta包 http://archive.apache.org/dist/jakarta/taglibs/standard/binaries/


## WebSocket

https://jakarta.ee/specifications/websocket/2.1/
https://jakarta.ee/specifications/websocket/2.1/jakarta-websocket-spec-2.1
https://projects.eclipse.org/projects/ee4j.websocket

https://mvnrepository.com/artifact/javax.websocket/javax.websocket-api/1.1
https://mvnrepository.com/artifact/jakarta.websocket/jakarta.websocket-api/2.2.0
https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-websocket/3.3.3



## Annotations

https://jakartaee.github.io/common-annotations-api/
https://mvnrepository.com/artifact/jakarta.annotation/jakarta.annotation-api/2.1.1



https://projects.eclipse.org/projects/ee4j.ca
https://jakarta.ee/specifications/annotations/3.0/
https://jakarta.ee/specifications/annotations/3.0/annotations-spec-3.0
https://github.com/jakartaee/common-annotations-api



https://mvnrepository.com/artifact/javax.annotation/javax.annotation-api/1.3.2
https://mvnrepository.com/artifact/jakarta.annotation/jakarta.annotation-api/3.0.0

## Authentication

https://jakarta.ee/specifications/authentication/2.0/
https://jakarta.ee/specifications/authentication/2.0/jakarta-authentication-spec-2.0

https://mvnrepository.com/artifact/jakarta.authentication/jakarta.authentication-api/3.1.0


# User-agent
https://www.bitwalker.eu/software/user-agent-utils
https://mvnrepository.com/artifact/eu.bitwalker/UserAgentUtils/1.21


# JWT
https://github.com/auth0/java-jwt com.auth0:java-jwt:4.4.0
https://mvnrepository.com/artifact/com.auth0/java-jwt/4.4.0

# FileUpLoad



SpringMVC用MultipartResolver实现上传文件,在spring-mvc.xml中注册相应的MultipartResolver即可
MultipartResolver的实现类有两个
CommonsMultipartResolver 需要使用commons-fileupload包支持,servlet低版本也能用
StandardServletMultipartResolver servlet内置功能,需要3.0版本以上使用



https://commons.apache.org/proper/commons-fileupload/
https://mvnrepository.com/artifact/commons-fileupload/commons-fileupload/1.5



# Spring MVC

https://docs.spring.io/spring-framework/reference/web.html

https://mvnrepository.com/artifact/org.springframework/spring-web/6.1.12
https://mvnrepository.com/artifact/org.springframework/spring-webmvc/6.1.12
https://mvnrepository.com/artifact/org.springframework/spring-webflux/6.1.13
https://mvnrepository.com/artifact/org.springframework/spring-expression/6.1.12
https://mvnrepository.com/artifact/org.springframework/spring-websocket/6.1.13

黑马mvc教程 https://blog.csdn.net/qq_58168493/article/details/122634493
创建MVC项目步骤: Java Enterprise -> 默认选择，Project template选择webapplication -> 第二步有一个Servlet

Q: MVC是什么
MVC Model View Controller 模型 视图 控制器
Model: 数据模型，一般用来封装数据 JavaBean
View: jsp或html,一般用来展示数据 JSP
Contriller: 处理交互, 处理逻辑程序的, Servlet 

Q: 表现层有什么
表现层功能: 接受客户端请求，向客户端响应结果
表现层包括展示层和控制层: 控制层接受请求，展示层展示结果

Q: MVC角色划分
前端控制器（DispatcherServlet）发任何请求都会经过前端控制器
请求到处理器映射（HandlerMapping） 请求查询Handler返回处理器执行链HandlerExecutionChain
处理器适配器（HandlerAdapter）处理器请求Handler，返回ModelAndView
视图解析器（ViewResolver）返回视图View
处理器或页面控制器（Controller）
验证器（ Validator）
命令对象（Command 请求参数绑定到的对象就叫命令对象）
表单对象（Form Object 提供给表单展示和提交到的对象就叫表单对象）








```xml
<!-- pom.xml -->
<!--Spring坐标-->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>5.0.5.RELEASE</version>
</dependency>
<!--SpringMVC坐标-->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.0.5.RELEASE</version>
</dependency>
<!--Servlet坐标-->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>servlet-api</artifactId>
    <version>2.5</version>
</dependency>
<!--Jsp坐标-->
<dependency>
    <groupId>javax.servlet.jsp</groupId>
    <artifactId>jsp-api</artifactId>
    <version>2.0</version>
</dependency>



<!-- webapp/WEB-INF/web.xml
第一步配置前端控制器 -->
<servlet>
  <servlet-name>SpringMVC</servlet-name>
  <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <!--配置springmvc-->
    <init-param>
      <param-name>contextConfigLocation</param-name>
      <param-value>classpath:springmvc.xml</param-value>
    </init-param>
  <!--前端控制器的servlet优先启动，在应用程序启动后首先加载，然后处理用户发起的各种请求-->
    <!-- <load-on-startup>1</load-on-startup>的作用 -->
    <!--1)load-on-startup元素标记容器是否在启动的时候就加载这个servlet(实例化并调用其init()方法)。-->
    <!--2)它的值必须是一个整数，表示servlet应该被载入的顺序-->
    <!--3)当值为0或者大于0时，表示容器在应用启动时就加载并初始化这个servlet；-->
    <!--4)当值小于0或者没有指定时，则表示容器在该servlet被选择时才会去加载。-->
    <!--5)正数的值越小，该servlet的优先级越高，应用启动时就越先加载。-->
    <!--6)当值相同时，容器就会自己选择顺序来加载。-->
  <load-on-startup>1</load-on-startup>
</servlet>
<servlet-mapping>
  <servlet-name>SpringMVC</servlet-name>
  <url-pattern>/</url-pattern>
</servlet-mapping>




<!-- 配置springmvc.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       http://www.springframework.org/schema/context/spring-context.xsd
       http://www.springframework.org/schema/mvc
       http://www.springframework.org/schema/mvc/spring-mvc.xsd">
    <!-- 扫描注解并开启MVC框架注解支持 -->
    <context:component-scan base-package="com.bdqn.controller"/>
    <mvc:annotation-driven/>

    <bean class="com.bdqn.controller.IndexController" name="/home.html"/>
    <!-- 视图解析器, 跳转到你指定的页面 -->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver"
          id="internalResourceViewResolver">
        <!--视图的类型和路径-->
        <property name="prefix" value="/WEB-INF/jsp/"/> <!--前缀名称-->
        <property name="suffix" value=".jsp"/> <!--后缀名称-->
    </bean>


</beans>

```




```java

// 手动写法
// IndexController类
// <bean class="com.bdqn.controller.IndexController" name="/home.html"/>
public class IndexController extends AbstractController {
    @Override
    protected ModelAndView handleRequestInternal(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse) throws Exception {
        System.out.println("IndexController.handleRequestInternal()");
        //返回home拼接成 /WEB-INF/jsp/home.jsp /home.html
        return new ModelAndView("home");
    }
}




// 第二步，编写java类和加入注解
// 注解


@Controller//控制器类，表示一个Bean，加到spring容器中
@ResponseBody //表示返回值是请求体
@RestController//返回值都是响应体的body@Controller@ResponseBody的合体
@RequestMapping(value = "/user")//请求映射，可以写在类上面
public class SpringController {
    @RequestMapping(value = "/user", method = RequestMethod.GET)//请求映射，请求方式params=""请求参数的限制条件，比如params={'accountName'}表示请求参数必须有accountName,params={"money!100"}参数中money不能是100
    @GetMapping("/user") //@RequestMapping(method = RequestMethod.GET)简写形式
    @PostMapping //@RequestMapping(method = RequestMethod.POST)简写形式
    @ResponseBody //表示返回值是请求体，请求体必须是json格式
    public String index(//localhost:8080/index/{id}?name=2
        @RequestParam(value = "name", required = false) String name,//接收url地址传参或表单数据
        @RequestBody String body,//返回值是响应体的body
        @PathVariable String id //路径参数
    ) {
        String aaa = "aaa";
        return aaa;
    }

}



//如果没有@ResponseBody或@RestController，返回值表示一个页面，通过ModelAndView对象返回
@Controller //UserController类
public class UserController {
    // /list
    @GetMapping("/list")
    public String queryUserList() {
        System.out.println("UserController.queryUserList()");
        //拼接成 /WEB-INF/jsp/userList.jsp /list
        return "userList";
        return "redirect:userList" //重定向
    }

    //queryUserByName?userName=bigData
    @RequestMapping(value = "/queryUserByName", method = RequestMethod.GET, params = "name")//params和底下的value选择其中一个
    public String queryUserByName(@RequestParam(value = "name", required = false) String userName) {
        System.out.println("UserController.queryUserByName(" + userName + ")");
        //拼接成 /WEB-INF/jsp/userDetails.jsp /queryUserByName
        return "userDetails";
    }
}





//未处理
@Controller
public class TestController {
    // /mv?username=java
    @RequestMapping(value = "/mv", method = RequestMethod.GET)
    public ModelAndView test(@RequestParam(value = "username") String userName) {
        System.out.println("TestController.test(" + userName + ")");
        ModelAndView mv = new ModelAndView();
        mv.setViewName("test");
        mv.addObject("username", userName);// jsp: ${username}
        return mv;
    }

    // /m?username=model
    @RequestMapping(value = "/m", method = RequestMethod.GET)
    public String test(@RequestParam(value = "username") String userName, Model model) {
        System.out.println("TestController.test(" + userName + ", " + model + ")");
        //使用model对象绑定数据模型
        model.addAttribute("usernameModel", userName); // jsp: ${usernameModel}
        //返回视图名称 /WEB-INF/jsp/test.jsp /m
        return "test";
    }

    // /map?username=map
    @RequestMapping(value = "/map", method = RequestMethod.GET)
    public String test(@RequestParam(value = "username") String userName, Map<String, Object> map) {
        System.out.println("TestController.test(" + userName + ", " + map + ")");
        //使用model对象绑定数据模型

        User user = new User();
        user.setId(100);
        user.setUsername("success");
        map.put("username", userName); // jsp: ${username}
        map.put("user", user); // jsp: ${user}

        //返回视图名称 /WEB-INF/jsp/test.jsp /map
        return "test";
    }
}



```

# cookies
https://blog.csdn.net/allenjsl/article/details/121081266

```java
//读取HTTP Cookie
//Spring框架提供@CookieValue注释来获取HTTP cookie的值，此注解可直接用在控制器方法参数中。
//如果没有设置默认值，并且没有找到名称为username的Cookie，Spring将抛出java.lang.IllegalStateException异常。
@GetMapping("/")
public String readCookie(@CookieValue(value = "username",defaultValue = "Atta") String username) {
  return "Hey! My username is " + username;
}


//设置HTTP Cookie
//要在Spring Boot中设置cookie，我们可以使用HttpServletResponse类的方法addCookie()。您需要做的就是创建一个新的Cookie对象并将其添加到响应中。
@GetMapping("/change-username")
public String setCookie(HttpServletResponse response) {
    // 创建一个 cookie对象
    Cookie cookie = new Cookie("username", "Jovan");
    //将cookie对象加入response响应
    response.addCookie(cookie);
    return "Username is changed!";
}

//读取所有Cookie[]
//除了使用@CookieValue注解，我们还可以使用HttpServletRequest类作为控制器方法参数来读取所有cookie。此类提供了getCookies()方法，该方法以数组形式返回浏览器发送的所有cookie。
 
@GetMapping("/all-cookies")
public String readAllCookies(HttpServletRequest request) {
    Cookie[] cookies = request.getCookies();
    if (cookies != null) {
        return Arrays.stream(cookies).map(c -> c.getName() + "=" + c.getValue()).collect(Collectors.joining(", "));
    }
    return "No cookies";
}

//为Cookie设置过期时间
//如果没有为cookie指定过期时间，则其生命周期将持续到Session过期为止。这样的cookie称为会话cookie。会话cookie保持活动状态，直到用户关闭其浏览器或清除其cookie。但是您可以覆盖此默认行为，并使用类的setMaxAge()方法设置cookie的过期时间。
//现在，usernameCookie不会因为Seesion结束到期，而是会在接下来的7天保持有效。传递给setMaxAge()方法的到期时间以秒为单位。到期日期和时间是相对于设置cookie的客户端而不是服务器而言的。
// 创建一个 cookie对象
Cookie cookie = new Cookie("username", "Jovan");
cookie.setMaxAge(7 * 24 * 60 * 60 * 1); // 7天过期 秒数
// 1 秒
// 60 分
// 60*60 小时
// 24*60*60 天
// 7*24*60*60 周
//将cookie对象加入response响应
response.addCookie(cookie);
 
// Https与Cookie
//我们需要了解一个概念：什么的安全的Cookies？安全的cookie是仅可以通过加密的HTTPS连接发送到服务器的cookie。无法通过未加密的HTTP连接将cookie发送到服务器。也就是说，如果设置了setSecure(true)，该Cookie将无法在Http连接中传输，只能是Https连接中传输。
// 创建一个 cookie对象
Cookie cookie = new Cookie("username", "Jovan");
cookie.setSecure(true);  //Https 安全cookie
//将cookie对象加入response响应
response.addCookie(cookie);
 

//HttpOnly Cookie
//HttpOnly cookie用于防止跨站点脚本（XSS）攻击，也就是说设置了Http Only的Cookie不能通过JavaScript的Document.cookieAPI访问，仅能在服务端由服务器程序访问。
// 创建一个 cookie对象
Cookie cookie = new Cookie("username", "Jovan");
cookie.setHttpOnly(true);  //不能被js访问的Cookie
//将cookie对象加入response响应
response.addCookie(cookie);


//删除Cookie
// 要删除Cookie，需要将Max-Age设置为0，并且将Cookie的值设置为null。不要将Max-Age指令值设置为-1负数。否则，浏览器会将其视为会话cookie。 
// 将Cookie的值设置为null
Cookie cookie = new Cookie("username", null);
//将`Max-Age`设置为0
cookie.setMaxAge(0);
 
response.addCookie(cookie);



```


# 拦截器

```xml
<!-- springmvc-servlet.xml -->
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xmlns:p="http://www.springframework.org/schema/p"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="
        http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd
        http://www.springframework.org/schema/mvc
        http://www.springframework.org/schema/mvc/spring-mvc.xsd">

    <!-- 使用注解的包，包括子集 -->
    <context:component-scan base-package="cn.qy.controller"/>
    <context:property-placeholder location="classpath:*.properties" ignore-unresolvable="true"/>

    <mvc:annotation-driven>
        <mvc:message-converters>
            <bean class="org.springframework.http.converter.StringHttpMessageConverter">
                <property name="supportedMediaTypes">
                    <list>
                        <value>application/json;charset=UTF-8</value>
                    </list>
                </property>
            </bean>
            <bean class="com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter">
                <property name="supportedMediaTypes">
                    <list>
                        <value>text/html;charset=UTF-8</value>
                        <value>application/json</value>
                    </list>
                </property>
                <property name="features">
                    <list>
                        <value>WriteDateUseDateFormat</value>
                    </list>
                </property>
            </bean>
        </mvc:message-converters>
    </mvc:annotation-driven>

    <mvc:resources location="/statics/" mapping="/statics/**"/>

    <!-- 配置多视图解析器 -->
    <bean id="contentNegotiationManager" class="org.springframework.web.accept.ContentNegotiationManagerFactoryBean">
        <!-- 是否启用参数支持，默认为true（支持），即xxx?format=json、xml等形式。 -->
        <property name="favorParameter" value="true"/>
        <!-- favorPathExtension:是否支持扩展名，默认为true（支持），扩展名指xxx.json、xxx.xml等形式 -->
        <property name="favorPathExtension" value="true"/>
        <!-- 默认ContentType -->
        <property name="defaultContentType" value="text/html"/>
        <!-- 配置映射关系 -->
        <!--扩展名到MIME的映射；favorPathExtension, favorParameter是true时起作用  -->
        <property name="mediaTypes">
            <value>
                json=application/json
                xml=application/xml
                html=text/html
            </value>
        </property>
    </bean>

    <!-- 完成视图的对应 -->
    <!-- 对转向页面的路径解析。prefix:前缀， suffix:后缀 -->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="order" value="0"/>
        <property name="prefix" value="/WEB-INF/jsp/"/>
        <property name="suffix" value=".jsp"/>
    </bean>

    <mvc:view-controller path="/" view-name="login"/>

    <!-- 配置文件上传  MultipartResolver-->
    <bean id="multipartResolver" class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
        <property name="maxUploadSize" value="500000000"/>
        <property name="defaultEncoding" value="UTF-8"/>
    </bean>
    
    <!--配置拦截器，当解析这个路径时，执行下面的类-->
    <mvc:interceptors>
        <mvc:interceptor>
            <mvc:mapping path="/auth/**"/>
            <bean class="cn.qy.interceptor.AuthInterceptor"/>
        </mvc:interceptor>
    </mvc:interceptors>

</beans>

```

```java
package cn.qy.interceptor;
/*登录拦截器*/
public class AuthInterceptor extends HandlerInterceptorAdapter{
    @Override
    public boolean preHandle(HttpServletRequest request,
                             HttpServletResponse response,
                             Object handler) throws Exception {
        //获取session
        HttpSession session=request.getSession();
        //在session中获取usersession的值
        Object sysUser=session.getAttribute(Constants.USER_SESSION);
        //如果存在值则放过，如果不存在则跳到403页
        if(!EmptyUtils.isEmpty(sysUser)){
            return true;
        }
        response.sendRedirect(request.getContextPath()+"/403.jsp");
        return false;
    }
}




```



# SpringBoot MVC

https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-web/3.3.3



```java
// 系统的异常处理
@ControllerAdvice
public class BaseExceptionHandler{
    @ExceptionHandler(Exception.class)
    @ResponseBody
    public Result error(Exception e){
        e.printStackTrace();
        System.out.println("调用了异常处理");
        return new Result(1,e.getMessage());
    }
}



```

```java
//org.springframework.boot:spring-boot-starter-web:2.5.1

@CrossOrigin //开启跨域


```


```java

//转发
@RequestMapping(value=``"/test/test01/{name}", method = RequestMethod.GET) 
public String test(@PathVariable String name) {
  //request.getRequestDispatcher("/ceng/hello.html").forward(request,response);
  return "forward:/ceng/hello.html";
}

//重定向

@RequestMapping(value="/test/test01/{name}" , method = RequestMethod.GET) 
public String test(@PathVariable String name) {
  //response.sendRedirect("/ceng/hello.html");
  return "redirect:/ceng/hello.html";
}


//拦截器
//config/WebConfig
@Configuration
public class WebConfig implements WebMvcConfigurer {
  //添加Web项目的拦截器
  @Override
  public void addInterceptors(InterceptorRegistry registry) {
    //对所有访问路径，都通过AdminInterceptor类型的拦截器进行拦截
    registry.addInterceptor(new AdminInterceptor())
    .addPathPatterns("/qy/admin/**")
    .excludePathPatterns("/", "/login", "/index.html", 
    "/user/login", "/css/**", "/images/**", "/js/**", "/fonts/**");
  }
}
//拦截判断类
public class AdminInterceptor extends HandlerInterceptorAdapter {
  @Override
  public boolean preHandle(HttpServletRequest request,
                            HttpServletResponse response,
                            Object handler) throws Exception {
    HttpSession httpSession = request.getSession();
    System.out.println("AdminInterceptor");
    Object sysUser = httpSession.getAttribute("username");
    if (EmptyUtil.isNotEmpty(sysUser)) {
        return true;
    }
    response.sendRedirect(request.getContextPath() + "/403.html");
    return false;
  }
}
@Component
public class LoginInterceptor implements HandlerInterceptor {
  /**
    * 目标方法执行前
    * 该方法在控制器处理请求方法前执行，其返回值表示是否中断后续操作
    * 返回 true 表示继续向下执行，返回 false 表示中断后续操作
    */
  @Override
  public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
      Object loginUser = request.getSession().getAttribute("loginUser");
      if (loginUser == null) {
          //未登录，返回登陆页
          request.setAttribute("msg", "您没有权限进行此操作，请先登陆！");
          request.getRequestDispatcher("/index.html").forward(request, response);
          return false;
      } else {
          //放行
          return true;
      }
  }
  /**
    * 目标方法执行后
    * 该方法在控制器处理请求方法调用之后、解析视图之前执行
    * 可以通过此方法对请求域中的模型和视图做进一步修改
    */
  @Override
  public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
      log.info("postHandle执行{}", modelAndView);
  }
  /**
    * 页面渲染后
    * 该方法在视图渲染结束后执行
    * 可以通过此方法实现资源清理、记录日志信息等工作
    */
  @Override
  public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
      log.info("afterCompletion执行异常{}", ex);
  }
}
————————————————
版权声明:本文为CSDN博主「A袁城」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接:https://blog.csdn.net/weixin_52120555/article/details/123327175
```










# RESTful

REST(Representational State Transfer),表述性状态转换,访问网络资源的格式,REST指的是一组架构约束条件和原则.
RESTful表述的是资源的状态性转移,在Web中资源就是URI(Uniform Resource Identifier).
REST与RESTful的区别: 根据REST风格对资源进行访问称为RESTful,描述形式被称为REST形式，访问资源叫RESTful.
幂等性: 执行操作对数据的影响,重复执行添加操作对数据的影响是每次都有结果POST不具备幂等性,查询删除更新操作对数据的影响每次都是相同的PUT操作具备幂等性.

原始风格和REST风格
http://localhost/user/getById?id=1 http://localhost/user/1
http://localhost/user/saveUser http://localhost/user

隐藏资源的访问行为，无法通过地址得知对资源是何种操作，书写也变得简化
GET    http://localhost/users   查询全部用户信息
GET    http://localhost/users/1 查询指定用户信息
POST   http://localhost/users   添加用户信息  
PUT    http://localhost/users   修改用户信息,如果没有数据可以进行创建
DELETE http://localhost/users/1 删除用户信息
按照访问路径和行为动作对资源进行了何种操作。这种方式是一种约定而不是规范，可以被打破，所以被称为REST风格
描述模块的名称通常使用复数，比如users,books,accounts。表示此类资源







# IDEA 配置 JSP
新建项目
添加框架
配置tomcat启动,添加war包

IDEA会为每一个tomcat部署的项目单独配置一份配置文件, 通过IDEA界面修改配置, 相应的文件也被修改了
控制台log:Using CATALINA_BASE:"{IDEA_HOME}\bin\IdeaConfig\system\tomcat\hash"






















This part of the documentation covers support for Servlet-stack web applications built on the Servlet API and deployed to Servlet containers. Individual chapters include Spring MVC, View Technologies, CORS Support, and WebSocket Support. For reactive-stack web applications, see Web on Reactive Stack.







