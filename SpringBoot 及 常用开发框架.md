# SpringBoot 及常用开发框架

## SpringBoot

### 概念

用于简化Spring应用的初始搭建一级开发过程，使用特定的方式进行配置(properties/yml)

创建独立的SpringAOP引用程序 通过main方法运行

嵌入的Tomcat无需部署war文件

简化maven配置

自动配置Spring添加对应功能starter自动化配置

### Springboot的优点

简单 快速开发 避免使用xml 不需要单独的web服务器

### 配置加载顺序

1. properties
2. YAML
3. 系统环境变量
4. 命令行参数

### 读取配置的方式

- @PropertySource
- @value
- @Environment
- @ConfigurationProperties

### 热部署方式

- Spring loaded
- Spring-boot-devtools

### Springboot中的Starters

各种启动器，包含了一系列可以集成到应用里面的依赖包

可根据需要进行自定义配置

### Spring & SpringBoot常用注解

- @SpringBootApplication

  Springboot项目的基石，默认在主类。等于@Configuration + @EnableAutoConfiguration + @oOmponentScan的集合

- @Component、@Repository、@Service、@Controller

  注解自动装配的bean

- @RestController

   等于@Controller + @ResponseBody。REST风格Controller

- @Scope

  声明Spring Bean的作用域

- @Configuration

  声明配置类

---

#### 前后端传值

- @PathVariable @RequestParam

  @PathVariable 获取路径参数 /user/{userId}

  @RequestParam 获取查询参数 /user?userId=123

- @RequestBody

  用于读取Request请求的body部分（Content-type为application/json的数据），自动绑定到java对象

---

#### 读取配置文件

- @Value
- @@ConfigurationProperties
- PropertySource 

---

#### 参数校验（JSR注解）

- 字段验证

  @NotEmpty 被注释的字符串的不能为 null 也不能为空

  @NotBlank 被注释的字符串非 null，并且必须包含一个非空白字符

  @Null 被注释的元素必须为 null

  @NotNull 被注释的元素必须不为 null

  @AssertTrue 被注释的元素必须为 true

  @AssertFalse 被注释的元素必须为 false

  @Pattern(regex=,flag=) 被注释的元素必须符合指定的正则表达式

  @Email 被注释的元素必须是 Email 格式。

  @Min(value) 被注释的元素必须是一个数字，其值必须大于等于指定的最小值

  @Max(value) 被注释的元素必须是一个数字，其值必须小于等于指定的最大值

  @DecimalMin(value) 被注释的元素必须是一个数字，其值必须大于等于指定的最小值

  @DecimalMax(value) 被注释的元素必须是一个数字，其值必须小于等于指定的最大值

  @Size(max=, min=) 被注释的元素的大小必须在指定的范围内

  @Digits (integer, fraction) 被注释的元素必须是一个数字，其值必须在可接受的范围内

  @Past 被注释的元素必须是一个过去的日期

  @Future 被注释的元素必须是一个将来的日期

- @Valid @validated

---

#### 全局异常控制

- @ControllerAdvice 定义全局异常处理类
- @ExceptionHandler 声明异常处理方法

## Mybatis



## Mybatis插件

### 	Mybatis-plus



### 	Mybatis Generator



### 	PageHelper



## Hutool



## Guava



## Joda-Time



