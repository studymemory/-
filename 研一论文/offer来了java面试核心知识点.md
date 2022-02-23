# 1.Spring原理及应用

## 1.1Spring的特性

Spirng是基于J2EE技术实现了一套轻量级的javawebservice系统应用框架，他有很多优秀的特性，很多公司都选择把Spring作为产品或者项目的基础开发架构，Spring的特性包括轻量，控制反转IOC，面向容器，面向切面AOP和框架灵活，具体如

1.1.1轻量

从JAR包的大小来说，spring是一个轻量级的框架，其核心jar包Spring-web-5.2.0.rELEASE 。jar和spring-core-5.2.0release.jar的大小均为1.4MB左右从系统资源的使用上来说，Spring运行只需要少量的操作系统资源内存和cpu，另外，spring还是模块化的，应用程序在使用过程中根据需要引入模块以jar包依赖的形势来实现引入不同的功能，

1.1.2控制反转

是指一个对象依赖的其他对象会在容器的初始化完成后主动将其依赖的对象传递给他，而不需要这个对象自己创建或者查找其依赖的对象，Spring基于控制反转技术实现系统对象之间依赖的解耦。

1.1.3

spring实现了对象的配置化生成和对象的生命周期管理，因此，可以理解为其是面向容器的，通过Spring的xml文件或者注解方法，应用程序可以配置每个Bean对象被创建和销毁的时间，以及Bean对象创建的先后顺序和依赖关系Spring中的实例对象可以使全局唯一的单例模式，也可以在每次需要时都重新生成一个新的实例，具体以哪一种方式创建bean对象由bean对象的周期决定，通过prototype属性来决定

## 1.2Spring的模块

核心容器层core container 

数据访问层data access

web应用层 web access

除此以外spring还包括Aop，aspects,instrumentation

messaging和Test

corecontainer由spring bean spring core spring context和spelspring expression spring表达式语言来完成。

spring-beans模块基于工厂模式对实现对象的创建，springbeans通过xml配置文件实现了声明式的的对象管理，将对象之间的复杂的依赖关系从实际编码逻辑中解耦出来。。

spring-core是spring的核心模块，具体包括控制反转和依赖注入，是指在一个bean实例当中引用另一个bean实例时，spring容器会自动创建其所依赖的bean实例，并将该bean实例注入，传递到对应的bean中





## 1.3Spring的核心JAR包

spring基于模块化实现，每个模块都对应于不同的jar包，要全面了解spring，首先应该从jar包开始，但是spring的常用jar包

spring Core

Spring Beans

Spring Context

Spring Aspects

Spring Context Support

Sping Expression language

Spring Framework Bean

Spring Instrument

Spring  JDBC

Spring  JMS

Spring Messaging

Spring OrM

Spring  OXM

Spring Test

Spring TX 



## 1.4Spring的注解

将应用程序中的Bean的定义和Bean之间的复杂的复杂依赖关系的配置从xml配置当中解放出来，应用程序只需要在某些服务或者功能时，使用注解依赖注入即可，具体Bean的定义和依赖关系由Spring的自动装配完成这使得Spring的使用更加方便。

1.4.1Spring注解的使用首先导入命名规范，然后指定IOC的扫描包，最后在java类中直接使用注解依赖注入需要的资源即可

1.导入命名空间及规范

在spring的applicationContext.xml配置文件中导入命名空间及规范。代码如下

```
xsi：schemaLocaiton=“http：//www.springframework.org/schema/beans”
    http://www.springframework.rog/schema/beans/spring-beans-3.0.xsd
    http://www.springframework.org/schema/context
    http://www.springframework.rog/schema/context/spring-context.xsd"
```

2.配置扫描包。

在applicationContext.xml配置文件中配置需要扫描的包，如下代码开启了自动扫描com.alex.spring 包下的所有类，也就是说，只有在com.alexspring包中的注解才能生效。

```
<!--指定Spring IOC容器扫描的包>
<context:component-scan base-package="com.alex.spring">
</context:component-scan>
```

完整的Spring注解配置文件如下。。

<?xml version = "1.0" encoding = "UTF-8">

<beans xmlns = "http://www.springframework.org/schema/beans"

xmlns:xsi = "http://www.w3"

<!--配置扫描包，自动扫描代码中的注释--->

使用注解使用注解比较简单，直接在java类中用@按需使用即可，具体代码如下

@Controller//使用@Controller注释声明一个控制器

public class restController｛

@Autowired//使用@Autowird注解依赖注入resttemplate

resttemplate rest;

//使用@requestMappiing 注释声明一个服务，服务的地址为rest

@requestMapping(value="/rest")

pubic String rest(){

return "rest";

}

｝

## 1.5SpringIOC原理

Spring通过配置一个文件描述Bean和Bean之间的依赖关系，利用Java的反射功能实例化Bean并且建立Bean之间的依赖关系，Spring的IOC容器在完成这些底层工作的基础上，还提供了Bean实例缓存管理，Bean生命周期管理。Bean实例代理，

## 1.6SpringAOP原理

## 1.7SpringMVC原理

## 1.8事物

## 1.9MyBatis的缓存

## 1.10Spring的生态

# 2.SpringCloud的原理及应用

## 2.1Spring boot

## 2.2Spring Cloud Config

## 2.3Spring Cloud Eureka

## 2.4Spring Cloud Consul

## 2.5Spring Cloud Feign

## 2.6Spring Cloud Hystrix

## 2.7Spring Cloud Zuul

## 2.8Spring Cloud 的链路监控

# 3.Netty网络编程原理及应用

## 3.1Reactor线程模型

## 3.2Netty的架构

## 3.3Netty的特性

## 3.4Netty的使用

# 4.ZooKeeper原理及应用

## 4.1ZooKeeper原理

## 4.2ZooKeeper应用

# 5.kafka原理及应用

## 5.1kafka的原理

## 5.2kafka的应用

# 6.Hadoop原理及应用

## 6.1HDFS

## 6.2MapReduce

## 6.3YARN

## 6.4Hadoop的原理及应用

# 7.HBase原理及应用

## 7.1HBase的原理

## 7.2HBase的应用

# 8.Cassandra原理及应用

## 8.1Cassandra的原理

## 8.2Cassandra的应用

# 9.ElasticSearch原理及应用

## 9.1ElasticSearch的概念和原理

## 9.2ElasticSearch的应用

# 10.Spark原理及应用

# 11.Flink原理及应用

