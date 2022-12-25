# Spring

------



## 概念

```
Spring - 开源的 轻量级Java开发框架
特点 - 支持IoC AOP 方便集成第三方组件 支持单元测试 支持RESTful 
```

---



## IoC - Inverse of Control 控制反转

一种设计思想，将原本在程序中手动创建的对象的控制权，交由Spring框架管理。

控制 - 对象创建（实例化、管理）的权力

反转 - 空号职权交给外部环境（Spring框架，IoC容器）

### SpringBean

被IoC容器管理的对象 

eg：被 @Component @Repository @Service @Controller修饰的类

#### @Component 和 @Bean的区别

- @Component作用于类 @Bean作用于方法

- @Component 通常是通过类路径扫描来⾃动侦测以及⾃动装配到 Spring 容器中（我们可以使⽤

  @ComponentScan 注解定义要扫描的路径从中找出标识了需要装配的类⾃动装配到 Spring 的

  bean 容器中）。 @Bean 注解通常是我们在标有该注解的⽅法中定义产⽣这个 bean, @Bean

  告诉了 Spring 这是某个类的实例，当我需要⽤它的时候还给我。

- @Bean 注解⽐ @Component 注解的⾃定义性更强，⽽且很多地⽅我们只能通过 @Bean 注

  解来注册 bean。⽐如当我们引⽤第三⽅库中的类需要装配到 Spring 容器时，则只能通过

  @Bean 来实现。

eg:

```java
@Configuration
public class AppConfig {
@Bean
public TransferService transferService() {
return new TransferServiceImpl();
 }
}

@Bean
public OneService getService(status) {
case (status) {
when 1:
return new serviceImpl1();
when 2:
return new serviceImpl2();
when 3:
return new serviceImpl3();
 }
}
```

### 可以注入bean的注解

@Autowired Spring内置

@Resource JDK内置

@Inject

#### @Autowired @Resource 的区别

Autowired默认的注入方式为byType 若接口有多个实现类，无法正确注入对象 可以通过@Qualifier注解指定名称进行注入

Resource属于JDK提供的注解 默认注入方式为byName 无法通过名称匹配到对应bean时 注入方式变为byType

### Bean的作用域

- singleton
- prototype
- request
- session
- application/global-session
- websocket

如何配置bean的作用域 

XML

```xml
<bean id="..." class="..." scope="singleton"></bean>
```

注解方式

```java
@Bean
@Scope(value = ConfigurableBeanFactory.SCOPE_PROTOTYPE)
public Person personPrototype() {
return new Person();
}
```

### Bean的初始化

- if BeanFactoryAware -> setBeanFactory()
- If xxxAware -> setXxx()
- If BeanPsotProcessor -> postProcessBeforeInitialization()
- if InitializingBean -> afterPropertiesSet()
- if init-method -> 执行对应方法
- if BeanPostProcessor -> postProcessAfterInitialization()
- 当Bean销毁时，if DisposableBean -> destory()
- 当Bean销毁时，ifdestory-method -> 执行对应方法



## Sprinp AOP

---

AOP(Aspect-Orirnted Programming:面向切面编程)，能够将与业务无关，却为业务模块所共同调用的逻辑或责任，如事务处理、日志管理、权限控制等封装起来，减少系统的重复代码，降低模块间耦合度，提高可拓展性 可维护性。

SpringAOP基于动态代理，如果代理的对象，实现了某个接口，那么SpringAOP会使用JDK PRoxy去创建对象。没有实现接口的对象，SpringAOP会使用Cglib生成代理对象的子类作为代理。



*可通过@Order定义切面顺序

*AspectJ比SpringAOP更强大，SpringAOP更简单

