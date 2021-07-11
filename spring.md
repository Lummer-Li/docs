#### Spring

### Spring概述

#### 简介

- Spring: 春天—>给软件行业带来了春天
- 2002, 首次推出了Spring框架的雏形: interface21框架
- Spring框架即以interface21框架为基础, 经过重新设计, 并不断丰富其内涵, 于2004年3月24日, 发布了1.0正式版本
- Rod Johnson, Spring Framework创始人, 著名作者. 很难想象Rod Johnson的学历, 真的让好多人大吃一惊, 他是悉尼大学的博士, 然而他的专业不是计算机, 而是音乐学
- Spring理念: 使现有的技术更加容易使用, 本身是一个大杂烩, 整合了现有的技术框架



- SSH: Struct2 + Spring + Hibernate
- SSM: SpringMVC + Spring + Mybatis



官网: https://spring.io/projects/spring-framework#overview

官方下载地址: https://repo.spring.io/release/org/springframework/spring/

Github: https://github.com/spring-projects/spring-framework

```xml
  <!-- https://mvnrepository.com/artifact/org.springframework/spring-webmvc -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.3.5</version>
</dependency>
<!-- https://mvnrepository.com/artifact/org.springframework/spring-webmvc -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>5.3.5</version>
</dependency>

```

#### 优点

- Spring是一个开源的免费的框架(容器)
- Spring是一个轻量级的, 非入侵式的框架
- 控制反转(IOC), 面向切面编程(AOP)
- 支持事务的处理, 对框架整合的支持

==总而言之, Spring就是一个轻量级的控制反转(IOC)和面向切面编程的(AOP)的框架==

#### 组成

![img](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210331152952.jpg)

#### 扩展

在Spring的官网有这个介绍: 现代化的Java开发. 说白了就是基于Spring的开发

- Spring: the source for modern Java
	- Spring Boot -> 构建一切
	- Spring Cloud -> 协调一切
	- Spring Cloud Data Flow -> 连接一切
- Spring Boot
	- 一个快速开发的脚手架
	- 基于SpringBoot可以快速的开发单个微服务
	- 约定大于配置
- Spring Cloud
	- SpringCloud是基于SpringBoot实现的

因为现在大多数公司都在使用SpringBoot进行快速开发, 学习SpringBoot的前提, 需要完全掌握Spring及SpringMVC. 承上启下的作用

**SpringBoot的弊端: 发展了太久之后, 也违背了原来的理念, 配置十分繁琐, 人称: “配置地狱“**

### IOC理论推导(Inversion Of Control)

1. UserDao 接口
2. UserDaoImpl 实现类
3. UserService 业务接口
4. UserServiceImpl 业务实现类

<img src="https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210401172448.png" alt="截屏2021-04-01 下午5.24.45" style="zoom:50%;" />

在我们之前的业务中, 用户的需求可能会影响我们原来的代码, 我们需要根据用户的需求去修改源代码, 如果程序代码量十分大, 修改一次的成本代价十分昂贵

我们使用一个set接口实现, 已经发生了革命性的变化

```java
// 利用set进行动态实现值的注入
public void setUserDao(UserDao userDao) {
  this.userDao = userDao;
}
```

- 之前, 程序是主动创建对象, 控制权在程序员手上
- 使用了set注入之后, 程序不再具有主动性, 而是变成了被动的接受对象

这种思想, 从本质上解决了问题, 我们程序猿再也不用去管理对象的创建了. 系统的耦合性大大降低, 可以更加专注的在业务的实现上, 这是IOC的原型

<img src="https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210401172428.png" alt="截屏2021-04-01 下午5.24.24" style="zoom:50%;" />

#### IOC 本质

控制反转(Inversion of Control), 是一种设计思想, DI(依赖注入)是实现IOC的一种方法, 也有人认为DI只是IOC的另一种说法, 没有IOC的程序中, 我们使用面向对象编程, 对象的创建与对象间的依赖关系完全硬编码在程序中, 对象的创建由程序自己控制, 控制反转后将对象的创建转移给第三方, 个人认为所谓控制反转就是: 获得依赖对象的方式反转了

采用XML方式配置Bean的时候, Bean的定义信息是和实现分离的, 而采用注解的方式可以把两者合为一体, Bean的定义信息直接以注解的形式定义在实现类中, 从而达到了零配置的目的

**控制反转是一种通过描述(XML或注解)并通过第三方去生产或获取特定对象的方式. 在Spring中实现控制反转的IOC容器, 其实现方法是依赖注入(Dependency Injection, DI)**

<img src="https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210401171829.png" alt="img" style="zoom: 67%;" />

### HelloSpring

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">

    <!-- 使用Spring创建对象， 在Spring中这些均称为Bean

    类型 变量名 = new 类型()
    Hello hello = new Hello();

    bean = 对象空间
    id = 变量名
    class = new 的对象
    property 相当于给对象中的属性赋值

    -->
    <bean id="hello" class="com.lummer.pojo.Hello">
        <property name="str" value="Spring"/>
    </bean>

</beans>
```

```java
@Test
public void test(){

  // 获取Spring的上下文对象
  ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
  // 我们的对象现在都在Spring的管理中， 我们要使用，直接去里面取出来就行
  Hello hello = (Hello) context.getBean("hello");
  System.out.println(hello.toString());
}
```

#### 思考问题?

- `Hello` 对象是谁创建的

	`Hello` 对象是由Spring创建的

- `Hello` 对象的属性是怎么设置的

	`Hello` 对象的属性是由`Spring`容器设置的

这个过程就叫做**控制反转**

**控制**: 谁来控制对象的创建, 传统应用程序的对象是由程序本身控制创建的, 使用`Spring`后, 对象由`Spring`来创建

**反转**: 程序本身不创建对象, 而变成被动的接收对象

**依赖注入**: 就是利用`set`方法进行注入

`IOC`是一种编程思想, 由主动的编程变成被动的接收

可以通过`new ClassPathXmlApplicationContext()`去浏览一下底层源码

所以现在, 要实现不同的操作, 只需要在`XML`配置文件中进行修改即可. 所谓的`IOC`, 一句话搞定: 对象由`Spring`来创建、管理、装配

### IOC创建对象的方式

1. 使用无参构造创建函数, 默认

2. 假设我们要使用有参构造创建对象

	1. 下标赋值

		```xml
		<!-- 第一种，下标赋值 -->
		<bean id="user" class="com.lummer.pojo.User">
		  <constructor-arg index="0" value="lummer"/>
		</bean>
		```

	2. 类型赋值

		```xml
		<!-- 第二种，通过类型创建，但不建议使用 -->
		<bean id="user" class="com.lummer.pojo.User">
		  <constructor-arg type="java.lang.String" value="Spring"/>
		</bean>
		```

	3. 参数名赋值

		```xml
		<!-- 第三种，直接通过参数名赋值-->
		<bean id="user" class="com.lummer.pojo.User">
		  <constructor-arg name="name" value="Spring"/>
		</bean>
		```

总结: 在配置文件加载的时候, 容器中管理的对象就已经初始化了

### Spring配置说明

#### 别名

```xml
<!--别名, 如果使用了别名, 我们也可以使用别名获取这个对象-->
<alias name="user" alias="user2"/>
```

#### Bean的配置

```xml
<!--
    id: bean的唯一标识符，也就是相当于我们学的对象名
    class: bean 对象所对应的全限定名： 包名 + 类型
    name：也是别名, 而且name更高级，可以取多个别名
-->
<bean id="userT" class="com.lummer.pojo.UserT" name="userT2 u2,u3;u4">
  <property name="name" value="Spring"/>
</bean>
```

#### Import

这个`import`, 一般用于团队开发使用, 可以将多个配置文件, 导入合并为一个

假设, 现在项目中有多个人开发, 这三个人负责不同的类开发, 不同的类需要注册在不同的bean中, 我们可以利用import将所有人的beans.xml合并为一个总的

- 张三
- 李四
- 王五
- applicationContext.xml

```xml
<import resource="beans.xml"/>
<import resource="beans2.xml"/>
<import resource="beans3.xml"/>
```

使用的时候, 直接使用总的配置文件就可以了

### DI依赖注入

#### 构造器注入

前面已经说过了



#### Set方式注入[重点]

- 依赖注入: set注入
	- 依赖: bean对象的创建依赖于容器
	- 注入: bean对象中的所有属性, 由容器来注入

[环境搭建]

1. 复杂类型

	```java
	public class Address {
	    private String address;
	
	    public String getAddress() {
	        return address;
	    }
	
	    public void setAddress(String address) 		 {
	        this.address = address;
	    }
	}
	
	```

2. 真实测试对象

	```java
	public class Student {
	    private String name;
	    private Address address;
	    private String[] books;
	    private List<String> hobby;
	    private Map<String, String> card;
	    private Set<String> games;
	    private String wife;
	    private Properties info;
	}
	```

3. Beans.xml

	```xml
	<?xml version="1.0" encoding="UTF-8"?>
	<beans xmlns="http://www.springframework.org/schema/beans"
	       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	       xsi:schemaLocation="http://www.springframework.org/schema/beans
	        http://www.springframework.org/schema/beans/spring-beans.xsd">
	
	  <bean id="student" class="com.lummer.pojo.Student">
	    <property name="name" value="Spring"/>
	  </bean>
	</beans>
	```

4. 测试类

	```java
	@Test
	public void test(){
	  ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
	  Student stu = (Student) context.getBean("student");
	  System.out.println(stu.getName());
	}
	```

5. 测试成功

完善注入信息

```xml
<bean id="student" class="com.lummer.pojo.Student">
  <!-- 第一种：普通值注入，value -->
  <property name="name" value="Spring"/>
  <!-- 第二种：Bean注入，value -->
  <property name="address" ref="address"/>
  <!-- 第三种：数组注入，ref -->
  <property name="books">
    <array>
      <value>西游记</value>
      <value>红楼梦</value>
      <value>水浒站</value>
      <value>三国演义</value>
    </array>
  </property>
  <!-- 第四种：List注入 -->
  <property name="hobby">
    <list>
      <value>听歌</value>
      <value>敲代码</value>
      <value>看电影</value>
    </list>
  </property>
  <!-- 第五种：Map注入 -->
  <property name="card">
    <map>
      <entry key="身份证" value="123456123456781234"></entry>
      <entry key="银行卡" value="6754212334525678"></entry>
    </map>
  </property>
  <!-- 第六种：Set注入 -->
  <property name="games">
    <set>
      <value>LOL</value>
      <value>COC</value>
      <value>BOB</value>
    </set>
  </property>
  <!-- 第七种：null注入 -->
  <property name="wife">
    <null/>
  </property>
  <!-- 第八种：Properties注入 -->
  <property name="info">
    <props>
      <prop key="driver">20190525</prop>
      <prop key="url">/</prop>
      <prop key="username">lummer</prop>
      <prop key="password">123456</prop>
    </props>
  </property>
</bean>
```

#### 拓展方式注入

我们可以使用p命令空间和c命令空间进行注入

官方解释

- p命名空间

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:p="http://www.springframework.org/schema/p"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean name="classic" class="com.example.ExampleBean">
        <property name="email" value="[emailprotected]"/>
    </bean>

    <bean name="p-namespace" class="com.example.ExampleBean"
        p:email="[emailprotected]"/>
</beans>
```

- c命名空间

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:c="http://www.springframework.org/schema/c"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="thingOne" class="x.y.ThingTwo"/>
    <bean id="thingTwo" class="x.y.ThingThree"/>

    <!-- traditional declaration -->
    <bean id="thingOne" class="x.y.ThingOne">
        <constructor-arg ref="thingTwo"/>
        <constructor-arg ref="thingThree"/>
        <constructor-arg value="[emailprotected]"/>
    </bean>

    <!-- c-namespace declaration -->
    <bean id="thingOne" class="x.y.ThingOne" c:thingTwo-ref="thingTwo" c:thingThree-ref="thingThree" c:email="[emailprotected]"/>

</beans>
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:p="http://www.springframework.org/schema/p"
       xmlns:c="http://www.springframework.org/schema/c"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">

    <!-- p命名空间注入，可以直接注入属性的值 -->
    <bean id="user" class="com.lummer.pojo.User" p:name="lummer" p:age="18"/>

    <!-- c命名空间注入，可以通过构造器注入：construct-args -->
    <bean id="user2" class="com.lummer.pojo.User" c:name="lummer2" c:age="17"/>
</beans>
```

测试

```java
@Test
public void user(){
  ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
  User user = context.getBean("user2", User.class);
  System.out.println(user);
}
```

注意点: p命名空间和c命名空间不能直接使用, 需要导入xml约束

```xml
xmlns:p="http://www.springframework.org/schema/p"
xmlns:c="http://www.springframework.org/schema/c"
```

#### bean的作用域

| Scope                                                        | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [singleton](https://www.docs4dev.com/docs/zh/spring-framework/5.1.3.RELEASE/reference/core.html#beans-factory-scopes-singleton) | (默认)将每个 Spring IoC 容器的单个 bean 定义范围限定为单个对象实例。 |
| [prototype](https://www.docs4dev.com/docs/zh/spring-framework/5.1.3.RELEASE/reference/core.html#beans-factory-scopes-prototype) | 将单个 bean 定义的作用域限定为任意数量的对象实例。           |
| [request](https://www.docs4dev.com/docs/zh/spring-framework/5.1.3.RELEASE/reference/core.html#beans-factory-scopes-request) | 将单个 bean 定义的范围限定为单个 HTTP 请求的生命周期。也就是说，每个 HTTP 请求都有一个在单个 bean 定义后面创建的 bean 实例。仅在可感知网络的 Spring `ApplicationContext`中有效。 |
| [session](https://www.docs4dev.com/docs/zh/spring-framework/5.1.3.RELEASE/reference/core.html#beans-factory-scopes-session) | 将单个 bean 定义的范围限定为 HTTP `Session`的生命周期。仅在可感知网络的 Spring `ApplicationContext`上下文中有效。 |
| [application](https://www.docs4dev.com/docs/zh/spring-framework/5.1.3.RELEASE/reference/core.html#beans-factory-scopes-application) | 将单个 bean 定义的范围限定为`ServletContext`的生命周期。仅在可感知网络的 Spring `ApplicationContext`上下文中有效。 |
| [websocket](https://www.docs4dev.com/docs/zh/spring-framework/5.1.3.RELEASE/reference/web.html#websocket-stomp-websocket-scope) | 将单个 bean 定义的范围限定为`WebSocket`的生命周期。仅在可感知网络的 Spring `ApplicationContext`上下文中有效。 |

1. 单例模式(Spring默认机制): 从容器中get的时候, 是同一个对象

```xml
<bean id="user2" class="com.lummer.pojo.User" c:name="lummer2" c:age="17" scope="singleton"/>
```

2. 原型模式: 每次从容器中get的时候, 都会产生一个新的对象

```xml
<bean id="accountService" class="com.something.DefaultAccountService" scope="prototype"/>
```

3. 其余的request、session、application, 这些只能够在web开发中使用到

### Bean的自动装配

- 自动装配是Spring满足bean依赖的一种方式
- Spring会在上下文中自动寻找, 并自动给bean装配属性



在Spring中有三种装配的方式

1. 在 xml 中显示的配置
2. 在 Java 中显示配置
3. 隐式的自动装配bean[重要]

#### 测试

环境搭建: 一个人有两个宠物

#### ByName自动装配

```xml
<!-- byName: 会自动在容器上下文中寻找， 与自己对象set方法后面的值对应的 beanid -->
<bean id="people" class="com.lummer.pojo.People" autowire="byName">
  <property name="name" value="xiaolummer"/>
</bean>
```

####  ByType自动装配

```xml
<bean id="cat" class="com.lummer.pojo.Cat"/>
<bean id="dog111" class="com.lummer.pojo.Dog"/>

<!--
        byName: 会自动在容器上下文中寻找， 与自己对象set方法后面的值对应的 beanid
        byType: 会自动在容器上下文中寻找， 与自己对象属性类型相同的 bean
     -->
<bean id="people" class="com.lummer.pojo.People" autowire="byType">
  <property name="name" value="xiaolummer"/>
</bean>
```

小结

- byname的时候, 需要保证所有的bean的id唯一, 并且这个bean需要和自动注入的属性的set方法的值一致
- bytype的时候, 需要保证所有的bean的class唯一, 并且这个bean需要和自动注入的属性的类型一致

#### 使用注解自动装配

JDK 1.5 开始支持注解 , Spring 2.5 开始支持注解

使用注解须知

1. 导入约束: context 约束
2. ==配置注解的支持: <context:annotation-config/>==

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
         http://www.springframework.org/schema/context/spring-context.xsd">

    <context:annotation-config/>

</beans>
```



**@AutoWired**

直接在属性上使用即可, 也可以在set方法上使用

使用AutoWired, 我们可以不用编写Set方法了, 前提是自动装配的属性在IOC(Spring)容器中存在, 且符合名字byname

科普:

```
@Nullable	标记了这个注解, 说明这个注解可以为null;
```

```
public @interface Autowired {
	boolean required() default true;
}

// 如果在注解上使用 @Autowired的require属性为false, 说明这个对象可以为null, 否则不允许为空
public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Autowired(required = false)
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

    // ...
}
```

如果@Autowired自动装配的环境比较复杂, 自动装配无法通过一个注解[@AutoWired]完成的时候, 我们可以使用@Qualifier[value=“XXX”]去配置@Autowired的使用, 指定一个唯一的bean对象注入

```java
public class People {

    @Autowired
    @Qualifier(value="cat111")
    private Cat cat;
    
    @Autowired
    @Qualifier(value="dog222")
    private Dog dog;
    
    private String name;
}
```



**@Resource注解 **

```java
public class People {

    @Resource(name="cat1")
    private Cat cat;
  
    @Resource
    private Dog dog;

}
```

**小结**

@Resource和@AutoWired的区别

- 都是用来自动装配的, 都可以放在属性字段上
- @AutoWired 通过 byType 的方式来实现, 而且必须要求这个对象存在[常用]
- @Resource 默认通过 byname 的方式实现, 如果找不到名字, 则通过 byType 的方式实现, 如果两个都找不到的情况下, 则报错
- 执行顺序不同
	- @Autowired 通过 byType 的方式来实现
	- @Resource 默认通过 byName 的方式实现



### 使用注解开发

在Spring4之后, 要使用注解开发, 必需要保证 aop 的包导入了

![截屏2021-05-16 下午5.10.15](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210516171018.png)

使用注解需要导入context的约束, 增加注解的支持!

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
        http://www.springframework.org/schema/context/spring-context.xsd">

    <!-- 开启注解支持 -->
    <context:annotation-config/>

</beans>
```



1. bean

2. 属性如何注入

	```java
	// 等价于 <bean id="user" class="com.lummer.pojo.User"/>
	@Component
	public class User {
	    
	    public String name;
	    
	    // 相当于 <property name="name" value="lummer123"/>
	    @Value("lummer123")
	    public void setName(String name) {
	        this.name = name;
	    }
	}
	```

	

3. 衍生的注解

	@Component 有几个衍生注解, 我们在web开发中,会按照mvc三层架构分层

	- dao[@Repository]
	- service[@Service]
	- controller[@Controller]
	- 这四个注解功能都是一样的, 都是代表将某个类注册到Spring中, 装配 bean

4. 自动装配

	```xml
	- @Autowired： 自动装配通过类型、名字
	    - 如果Autowired不能唯一自动装配上属性， 则需要@Qualifier[value=“XXX”]
	- @Nullable	标记了这个注解, 说明这个注解可以为null
	- @Resource： 自动装配通过名字、类型
	```

5. 作用域

	```java
	// 等价于 <bean id="user" class="com.lummer.pojo.User"/>
	@Component
	/*@Scope("singleton")*/
	@Scope("prototype")
	public class User {
	
	    public String name;
	
	    // 相当于 <property name="name" value="lummer123"/>
	    @Value("lummer123")
	    public void setName(String name) {
	        this.name = name;
	    }
	}
	
	```

6. 小结

	xml 与 注解

	- xml 更加万能, 适用于任何场合, 维护简单方便
	- 注解不是自己类使用不了, 维护相对复杂

	xml 与 注解最佳实践

	- xml 用来管理 bean
	- 注解只负责完成属性的注入
	- 我们在使用的过程中, 只需要注意一个问题; 必须让注解生效, 就需要开启注解的支持

	```xml
	<!-- 指定要扫描的包， 这个包下面的注解会生效 -->
	<context:component-scan base-package="com.lummer"/>
	<!-- 开启注解支持 -->
	<context:annotation-config/>
	```


### 使用JavaConfig实现配置

我们现在完全不使用Spring的xml配置, 全权交给Java来做

javaConfig 是 Spring 的一个子项目, 在 Spring 4 之后, 他成为了一个核心功能

**实体类**

```java
// 这个注解的意思， 就是说这个类被Spring接管了， 注册到了容器中
@Component
public class User {
    private String name;

    public String getName() {
        return name;
    }

    @Value("lummer")    // 属性注入值
    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

**配置文件**

```java
package com.lummer.config;

import com.lummer.pojo.User;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Import;

// 这个也会被Spring容器托管， 注册到容器中， 因为他本来就是一个Component
// @Configuration代表这是一个配置类， 就和我们之前看的beans.xml是一样的
@Configuration
@ComponentScan("com.lummer.pojo")
@Import(Config2.class)
public class Config {

    // 注册一个bean，就相当于我们之前写的bean标签
    // 这个方法的名字就相当于我们之前bean标签中的id属性
    // 这个方法的返回值就相当于我们之前的class属性
    @Bean
    public User getUser(){
        return new User();  // 返回要注入到bean中的对象
    }
}
```

**测试类**

```java
public class MyTest {
    @Test
    public void test()
    {
        // 如果完全使用了配置类方式去做，我们就只能通过 AnnotationConfigApplicationContext 上下文来获取容器， 通过配置类的 class 对象加载
        ApplicationContext context = new AnnotationConfigApplicationContext(Config.class);
        User user = context.getBean("getUser", User.class);
        System.out.println(user.toString());
    }
}
```

这种纯Java的配置方式, 在SpringBoot中随处可见

### 代理模式

#### 为什么要学习代理模式

因为这既是SpringAOP的底层 [SpringAOP 和 SpringMVC]

代理模式的分类

- 静态代理
- 动态代理

![image-20210522222044680](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210522222226.png)

#### 静态代理

**角色分析**

- 抽象角色: 一般会使用接口或者抽象类来解决
- 真实角色: 被代理的角色
- 代理角色: 代理真实角色, 代理真实角色后, 我们一般会做一些附属操作
- 客户: 访问代理对象的人

 

**代码步骤**

1. 接口

	```java
	// 租房
	public interface Rent {
	    public void rent();
	}
	```

2. 真实角色

	```java
	// 房东
	public class Host implements Rent{
	    public void rent(){
	        System.out.println("出租房子");
	    }
	}
	```

3. 代理角色

	```java
	public class Proxy implements Rent{
	    private Host host;
	
	    public Proxy(){
	
	    }
	    public Proxy(Host host){
	        seeHouse();
	        this.host = host;
	        contract();
	        fee();
	    }
	    public void rent(){
	        host.rent();
	
	    }
	    // 看房
	    public void seeHouse(){
	        System.out.println("中介带你看房");
	    }
	    // 签合同
	    public void contract(){
	        System.out.println("签租赁合同");
	    }
	    // 收中介费
	    public void fee(){
	        System.out.println("Agency Fees");
	    }
	
	}
	```

4. 客户端访问代理角色

	```java
	public class Client {
	    public static void main(String[] args) {
	        Host host = new Host();
	
	        // 代理, 中介帮房东租房子，但是代理一般会有一些附属操作
	        Proxy proxy = new Proxy(host);
	        // 不用面对房东，只找中介就可以了
	        proxy.rent();
	    }
	}
	```

	

**代理模式的好处**

- 可以使真实角色的操作更加纯粹, 不用关注一些公共的业务
- 公共也就交给了代理角色, 实现了业务的分工
- 公共业务发生扩展的时候, 方便集中管理

**代理模式的缺点**

- 一个真实角色就会产生一个代理角色, 代码量会翻倍~开发效率会变低



#### 加深理解

代码实现

1. 接口

	```java
	public interface UserService {
	    public void add();
	    public void delete();
	    public void update();
	    public void query();
	}
	```

2. 真实对象

	```java
	public class UserServiceImpl implements UserService {
	    public void add() {
	        System.out.println("add");
	    }
	
	    public void delete() {
	        System.out.println("delete");
	    }
	
	    public void query() {
	        System.out.println("query");
	    }
	
	    public void update() {
	        System.out.println("update");
	    }
	}
	```

3. 代理对象

	```java
	public class UserServiceProxy implements UserService {
	
	    UserServiceImpl userService;
	    public UserServiceProxy(){}
	    public UserServiceProxy(UserServiceImpl userService){
	        this.userService = userService;
	    }
	
	    public void add() {
	        log("add");
	        userService.add();
	    }
	
	    public void delete() {
	        log("delete");
	        userService.delete();
	    }
	
	    public void update() {
	        log("update");
	        userService.update();
	    }
	
	    public void query() {
	        log("query");
	        userService.query();
	    }
	
	    // 改动原有的代码，在公司是大忌
	    // 日志方法
	    public void log(String msg){
	        System.out.println(msg);
	    }
	}
	```

4. 客户端

	```java
	public class Client {
	
	    public static void main(String[] args) {
	        UserServiceImpl userService = new UserServiceImpl();
	        UserServiceProxy proxy = new UserServiceProxy(userService);
	        proxy.add();
	    }
	
	}
	```

	

聊聊AOP

![截屏2021-05-22 下午10.56.34](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210522225655.png)

#### 动态代理

- 动态代理和静态代理角色一样
- 动态代理的代理类是动态生成的, 不是我们直接写好的
- 动态代理分为两大类
	- 基于接口——JDK动态代理[我们使用]
	- 基于类: cglib
	- Java 字节码实现: JAVAssist



需要了解两个类: Proxy 代理、 InvocationHandler 调用处理程序



动态代理的优势

- 可以使真实角色的操作更加纯粹, 不用去关注一些公共的业务
- 公共也就交给代理角色, 实现了业务的分工
- 公共业务发生扩展的时候, 方便集中管理
- 一个动态代理类代理的是一个接口, 一般对应一类业务
- 一个动态代理类可以代理多个类, 只要是实现了同一个接口即可



### AOP

#### 什么是AOP

AOP(Aspect Oriented Programming) 意为: 面向切面编程, 通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术. AOP 是 OOP 的延续, 是软件开发中的一个热点, 也是 Spring 框架的一个重要内容, 是函数式编程的一种衍生型范型. 利用 AOP 可以对业务逻辑的各个部分进行隔离, 从而使得业务逻辑各部分之间的耦合度降低, 提高程序的可重用性, 同时提高了开发的效率

![image-20210606203123044](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210606203320.png)

#### Aop在Spring中的作用

==提供声明式事务, 允许用户自定义切面==

- 横切关注点: 跨越应用程序多个模块的方法或功能. 即是, 与我们业务逻辑无关的, 但是我们需要关注的部分, 就是横切关注点, 如日志、安全、缓存、事务等等…...
- 切面(ASPECT): 横切关注点被模块化的特殊对象(它是一个类)  Log
- 通知(Advice): 切面必须要完成的工作. 即它是类中的一个方法
- 目标(Target): 被通知对象
- 代理(Proxy): 向目标对象应用通知之后创建的对象
- 切入点(PointCut): 切面通知执行的“地点”的定义
- 连接点(JointPoint): 与切入点匹配的执行点

![image-20210606204359896](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210606204402.png)

#### 使用Spring实现Aop

[重点]使用AOP织入, 需要导入一个依赖包

```xml
<!-- https://mvnrepository.com/artifact/org.aspectj/aspectjweaver -->
<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
    <version>1.9.6</version>
</dependency>
```



方式一: 使用Spring的API接口[主要是SpringAPI接口实现]

方式二: 自定义来实现AOP[主要是切面定义]

方式三: 使用注解实现

### 整合Mybatis

步骤

1. 导入相关jar包
	- junit
	- mybatis
	- mysql数据库
	- spring相关的
	- aop织入
	- mybatis-spring [new]
2. 编写配置文件
3. 测试

#### 回忆mybatis

1. 编写实体类
2. 编写核心配置文件
3. 编写接口
4. 编写Mapper.xml
5. 测试

#### Mybatis-spring

1. 编写数据源
2. sqlSessionFactory
3. sqlSessionTemplate
4. 需要给接口加实现类
5. 将自己写的实现类, 注入到Spring中
6. 测试

### 声明式事务

#### 回顾事务

- 把一组业务当成一个业务来做, 要么都成功, 要么都失败
- 事务在项目开发中, 十分的重要, 涉及到数据的一致性问题, 不能马虎
- 确保完整性和一致性



事务ACID原则

- 原子性
- 一致性
- 隔离性
	- 多个事务可能操作同一个资源, 防止数据损坏
- 持久性
	- 事务一旦提交, 无论系统发生什么问题, 结果都不会再被影响, 将持久化的写到存储器中

####   Spring中的事务管理

- 声明式事务
- 编程式事务: 需要在代码中, 进行事务的管理



思考

为什么需要事务

- 如果不配置事务, 可能存在数据提交不一致的情况下
- 如果我们不在Spring中去配置声明式事务, 我们就需要在代码中手动配置事务
- 事务在项目的开发中十分重要, 涉及到数据的一致性和完整性问题, 不容马虎

