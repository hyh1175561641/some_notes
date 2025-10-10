


# Swagger

https://swagger.io

https://www.cnblogs.com/progor/p/13297904.html
https://zhuanlan.zhihu.com/p/98560871
https://blog.csdn.net/hadues/article/details/123753888

打开网页查看接口
http://localhost:8080/swagger-ui.html
http://localhost:8080/v2/api-docs


前后端分离需要定义接口标准,前端测试接口用postman,后端提供接口用swagger,
号称世界上最流行的API框架,RESTFul API文档在线自动生成工具=>API文档与API定义同步更新,可以在线测试API接口,



```java

// 导入依赖, 注意:springboot2.6以上版本不兼容2.9.2
//io.springfox:springfox-swagger2:2.9.2
//io.springfox:springfox-swagger-ui:2.9.2

//com.example.config.SwaggerConfig.java 配置类可以什么都不写,会显示默认值
@Configuration //配置swagger2
@EnableSwagger2 //开启swagger2
public class SwaggerConfig {
    //配置了Swagger的Docket的bean实例
    @Bean
    public Docket createRestApi() {
        return new Docket(DocumentationType.SWAGGER_2)
        .groupName("分布式系统")
        .apiInfo(apiInfo())
        .select()
        .apis(RequestHandlerSelectors.basePackage("com.itheima.boot.controller"))
        .paths(PathSelectors.any())
        .build();
    }
    //配置Swagger信息,apiInfo
    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
        .title("XX项目API")
        .description("XX项目SwaggerAPI管理")
        .termsOfServiceUrl("")
        .version("1.0")
        .build();
    }
}



```




```java

// 从ry框架复制过来的

// application.yml
// # Swagger配置
// swagger:
//   # 是否开启swagger
//   enabled: true


@Configuration
public class SwaggerConfig
{
    // 是否开启swagger
    @Value("${swagger.enabled}")
    private boolean enabled;
    
    // 创建API
    @Bean
    public Docket createRestApi()
    {
        return new Docket(DocumentationType.OAS_30)
                // 是否启用Swagger
                .enable(enabled)
                // 用来创建该API的基本信息，展示在文档的页面中（自定义展示的信息）
                .apiInfo(apiInfo())
                // 设置哪些接口暴露给Swagger展示
                .select()
                // 扫描所有有注解的api，用这种方式更灵活
                .apis(RequestHandlerSelectors.withMethodAnnotation(ApiOperation.class))
                // 扫描指定包中的swagger注解
                //.apis(RequestHandlerSelectors.basePackage("com.ruoyi.project.tool.swagger"))
                // 扫描所有 .apis(RequestHandlerSelectors.any())
                .paths(PathSelectors.any())
                .build();
    }

    // 添加摘要信息
    private ApiInfo apiInfo()
    {
        // 用ApiInfoBuilder进行定制
        return new ApiInfoBuilder()
                // 设置标题
                .title("标题：若依管理系统_接口文档")
                // 描述
                .description("描述：用于管理集团旗下公司的人员信息,具体包括XXX,XXX模块...")
                // 作者信息
                .contact(new Contact(RuoYiConfig.getName(), null, null))
                // 版本
                .version("版本号:" + RuoYiConfig.getVersion())
                .build();
    }
}


```


















