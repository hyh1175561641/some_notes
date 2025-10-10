
# Lombok

https://projectlombok.org/
https://mvnrepository.com/artifact/org.projectlombok/lombok/1.18.30



```java

@Data: @Getter@Setter@ToString@EqualsAndHashCode

@Data
@NoArgsConstructor
@AllArgsConstructor
public class User implements Serializable {
    private Long id;
    private String username;
    private String password;
    private String name;
    private Integer age;
    private String email;
}


```


@RequiredArgsConstructor会生成一个包含常量，和标识了NotNull的变量的构造方法。生成的构造方法是私有的private。这个我用的很少。
@EqualsAndHashCode
(1).它会生成equals和hashCode方法
(2).默认使用非静态的属性
(3).可以通过exclude参数排除不需要生成的属性
(4).可以通过of参数来指定需要生成的属性
(5).它默认不调用父类的方法，只使用本类定义的属性进行操作，可以使用callSuper=true来解决，会在@Data中进行讲解。
————————————————
版权声明：本文为CSDN博主「Blue-Sea」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_43223307/article/details/121439376
@TableName("employee") //能够和底层的数据库表明进行对应：




# validation

https://beanvalidation.org

https://mvnrepository.com/artifact/javax.validation/validation-api/2.0.1.Final
https://mvnrepository.com/artifact/jakarta.validation/jakarta.validation-api/3.1.0


https://github.com/CodingDocs/springboot-guide/blob/master/docs/ spring-bean-validation.md 某人的文档
https://blog.csdn.net/whk_15502266662/article/details/107981940 使用 validation 验证参数


```java

// 依赖
// javax.validation:validation-api:1.1.0.Final
// validation 提供的注解
//@Null	被注释的元素_值必须为 null
//@NotNull	被注释的元素_值必须不为 null
//@Pattern(regex=)	被注释的元素字符串_必须符合指定的正则表达式
//@Size(max=, min=)	集合元素数量必须在min和max范围内
//@AssertTrue	被注释的元素必须为 true
//@AssertFalse	被注释的元素必须为 false
//@Min(value)	被注释的元素必须是一个数字，其值必须大于等于指定的最小值
//@Max(value)	被注释的元素必须是一个数字，其值必须小于等于指定的最大值
//@Range(min,max)	数字必须在min和max范围内
//@DecimalMin(value)	被注释的元素必须是一个数字，其值必须大于等于指定的最小值
//@DecimalMax(value)	被注释的元素必须是一个数字，其值必须小于等于指定的最大值
//@Digits (integer, fraction)	被注释的元素必须是一个数字，其值必须在可接受的范围内
//@Past	被注释的元素必须是一个过去的日期
//@Future	被注释的元素必须是一个将来的日期
//@Email	字符串必须是Email地址
//@SafeHtml	字符串必须是安全的html
//@URL	字符串必须是合法的URL
//@CreditCardNumber(ignoreNonDigitCharacters=)	字符串必须是信用卡号,按照美国的标准验证
//@Size(max,min)	限制字符长度必须在min到max之间

//Controller添加@Valid或者@Validated都可以
@RestController
@RequestMapping("/")
public class UserController {
    
    @RequestMapping("testValidation")
    public String testValidation(@Valid @RequestBody UserRequest userRequest) {
        return "success";
    }
}

//实体类添加校验注解
class Profile{
  @NotNull(message = "字段值不能为空")
  private String name;
  @NotNull
  private String sex;
  @Max(value = 20,message = "最大长度为20")
  private String address;
  @NotNull
  @Size(max=10,min=5,message = "字段长度要在5-10之间")
  private String fileName;
  @Pattern(regexp = "^[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+(\\.[a-zA-Z0-9-]+)*\\.[a-zA-Z0-9]{2,6}$",message = "不满足邮箱正则表达式")
  private String email;
  @AssertTrue(message = "字段为true才能通过")
  private boolean isSave;
  @Future(message = "时间在当前时间之后才可以通过")
  private Date date;
}




// hibernate-validator
// org.hibernate.validator:hibernate-validator:6.0.2.Final
// hibernate 提供的注解
//@NotBlank(message =)	验证字符串非null，且trim后长度必须大于0
//@Length(min=,max=)	被注释的字符串的大小必须在指定的范围内
//@NotEmpty	被注释的字符串的必须非空
//@Range(min=,max=,message=)	被注释的元素必须在合适的范围内
//@AssertFalse	校验false
//@AssertTrue	校验true
//@DecimalMax(value=,inclusive=)	小于等于value，
//inclusive=true	是小于等于
//@DecimalMin(value=,inclusive=)	与上类似
//@Max(value=)	小于等于value
//@Min(value=)	大于等于value
//@NotNull	检查Null
//@Past	检查日期
//@Pattern(regex=,flag=)	正则
//@Size(min=, max=)	字符串，集合，map限制大小
//@Valid	对po实体类进行校验


// spring-boot-starter-validation
// org.springframework.boot:spring-boot-starter-validation:1.4.0.RELEASE






```