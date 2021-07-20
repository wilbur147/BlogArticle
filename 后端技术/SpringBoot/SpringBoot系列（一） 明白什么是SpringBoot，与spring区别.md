## 一、[Spring Boot](https://www.weiye.link/category/rear/sringboot/) 、 Spring MVC 、Spring对比

首先你需求理解一件事情：[Spring Boot](https://www.weiye.link/category/rear/sringboot/)项目意图并不是替换Spring、SpringMVC，而是使他们用起来愈加简略。

**Spring 结构**

Spring结构最中心的特性便是依靠注入DI（Dependency Injecttion）和操控回转IOC（Inversion Of Control）。假如你能够合理的运用DI和IOC，能够开宣布松耦合、扩展性好的的应用程序。

<img src="https://img.kancloud.cn/c9/e7/c9e705add7da2caec95188ef6495352b_343x343.png" alt="img" style="zoom:200%;" />

**Spring MVC**

Spring MVC供给了一种友爱的方法来开发Web应用程序。 通过运用诸如Dispatcher Servlet，ModelAndView和View Resolver，能够轻松开发Web应用程序。

**[Spring Boot](https://www.weiye.link/category/rear/sringboot/)**

Spring 和 Spring MVC最大的弊端在于存在很多的装备，并且这些装备在不同的项目中具有很高的相似性。从而导致重复装备，繁琐并且凌乱！

<img src="https://img.kancloud.cn/d7/c1/d7c1c5ad4ff55fdd89aa119c470ae7c2_635x232.png" alt="img"  />

[Spring Boot](https://www.weiye.link/category/rear/sringboot/)希望通过结合主动装备和starters来处理了这个问题。 另外，[Spring Boot](https://www.weiye.link/category/rear/sringboot/)还供给了一些功用，能够更快地构建可用于生产环境的应用程序。

## 二、[Spring Boot](https://www.weiye.link/category/rear/sringboot/) 主动装备

Spring和Spring MVC应用程序里面有很多的XML或Java Bean装备。[Spring Boot](https://www.weiye.link/category/rear/sringboot/)为处理这个问题，供给一种新的处理计划，新的思维方法。
<img src="https://img.kancloud.cn/e0/f3/e0f386d1c8916f4926946d42bf151337_956x578.png" alt="img"  />
springboot考虑的方法：是不是能够愈加智能一点，当Spring中加入一些新的jar包，加入一些装备，能够主动的影响应用内的bean的加载。 比方：Spring MVC JAR坐落类途径中时，主动装备Dispatcher Servlet。当然，当这些主动的默许装备不符合我们的要求的时分，我们能够修正。修正之前加载的这一些Bean，装备修正之后会主动加载另外一些Bean。

## 三、什么是[Spring Boot](https://www.weiye.link/category/rear/sringboot/) Starter？

[Spring Boot](https://www.weiye.link/category/rear/sringboot/) Starter是一组被依靠第三方类库的调集。

假如你要开发一个web应用程序，就通过包办理工具(如maven)引进spring-boot-starter-web就能够了，而不必别离引进下面这么多依靠类库，spring-boot-starter-web一次性帮你引进下面的这些常用类库。

- Spring — spring 中心, beans, context上下文, AOP面向切面
- Web MVC — Spring MVC
- Jackson — JSON数据的序列化与反序列化
- Validation — Hibernate参数校验及校验API
- 嵌入式 Servlet Container — Tomcat
- 日志结构Logging — logback, slf4j

<img src="https://img.kancloud.cn/17/c6/17c6abe1c379cb541484b6844e6b4093_603x545.png" alt="img"  />

## 四、什么是[Spring Boot](https://www.weiye.link/category/rear/sringboot/) Starter Parent

一切的[Spring Boot](https://www.weiye.link/category/rear/sringboot/)项目默许运用spring-boot-starter-parent作为应用程序的父项目。

```xml
<parent>
	<groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.0.0.RELEASE</version>
</parent> 
```

继承父项意图优点在于： 统一java版别装备和其他的一些依靠类库的版别。也便是说，你引进的第三方类库不要加版别号，父项目替你办理版别，并且是经过兼容性测验的。比你自己随意引进一个版别兼容性更好。

> 当然父项目只能帮你办理一些常用类库的版别，假如你引进一些不常用的jar，还是要自己办理版别号及兼容性！

## 五、嵌入式web容器

Spring boot打成jar包，默许包含嵌入式的web容器：tomcat。你能够简略的运用如下指令发动一个web服务：

```bash
java -jar springboot-demo.jar
```

这更有利于微服务的部署及微服务的构建、发动、扩容。[Spring Boot](https://www.weiye.link/category/rear/sringboot/)还支撑Jetty和Undertow作为web容器。

## 六、Spring Data

![img](https://img.kancloud.cn/71/5b/715bd18bdaf7ca530da4857c8da14881_591x305.png)

Spring Data的方针是供给一种更友爱的方法或者是API来存取数据。包括对于联系型数据库和NOSQL数据的支撑。比方：

- Spring Data JPA — 联系型数据库操作的API，友爱且易于运用
- Spring Data MongoDB -MongoDB的操作API
- Spring Data REST — 从持久层Repositories主动生成服务层API，暴露 REST APIs 接口。超级好用！

当然，Spring Data还有更多好用的特性和支撑等待你去探究！

## 七、spring boot2.x新特性

### 7.1.基础环境晋级

- 最低 JDK 8，支撑 JDK 9，不再支撑 Java 6 和 7。[Spring Boot](https://www.weiye.link/category/rear/sringboot/) 2.0 要求 Java 8 作为最低版别，许多现有的 API 已更新，以运用 Java 8 的特性。
  例如，接口上的默许方法，函数回调以及新的 API，如 javax.time。
- 假如你正在运用 Java 7 或更早版别，则在开发 [Spring Boot](https://www.weiye.link/category/rear/sringboot/) 2.0 应用程序之前，需求晋级你的 JDK。

### 7.2.依靠组件晋级

- Jetty 9.4，Jetty 是一个开源的 Servlet 容器，它为基于 Java 的 Web 内容，例如 JSP 和 Servlet 供给运转环境。Jetty 是运用 Java 语言编写的，它的 API 以一组 JAR 包的形式发布。
- Tomcat 8.5，Apache Tomcat 8.5.x 旨在取代 8.0.x，完全支撑 Java 9。
- Flyway 5，Flyway 是独立于数据库的应用、办理并盯梢数据库改变的数据库版别办理工具。用浅显的话讲，Flyway 能够像 SVN 办理不同人的代码那样，办理不同人的 SQL 脚本，从而做到数据库同步。
- Hibernate 5.2，Hibernate 是一款非常盛行的 ORM 结构。
- Gradle 3.4，[Spring Boot](https://www.weiye.link/category/rear/sringboot/) 的 Gradle 插件在很大程度上已被重写，有了严重的改进。
- Thymeleaf 3.0，Thymeleaf 3 相对于 Thymeleaf 2 有非常大的性能提升。

### 7.3. 默许软件替换

- 默许数据库衔接池已从 Tomcat 切换到 HikariCP，HikariCP 是一个高性能的 JDBC 衔接池，Hikari 是日语“光”的意思。
- redis客户端默许运用 Lettuce，替换掉Jedis.Lettuce 是一个可弹性的线程安全的 Redis 客户端，用于同步、异步和反应运用。多个线程能够共享同一个 RedisConnection，它运用优秀 Netty NIO 结构来高效地办理多个衔接，支撑先进的 Redis 功用，如 Sentinel、集群、流水线、主动从头衔接和 Redis 数据模型。

### 7.4.新技术的引进

- 响应式编程WebFlux,重要的变革，后续章节会详细展示
- 支撑 Quartz,[Spring Boot](https://www.weiye.link/category/rear/sringboot/) 1.0 并没有供给对 Quartz 的支撑，之前出现了各种集成计划，[Spring Boot](https://www.weiye.link/category/rear/sringboot/) 2.0 给出了最简略的集成方法。
- 对Kotlin 的支撑
- JOOQ 的支撑,JOOQ 是基于 Java 拜访联系型数据库的工具包。JOOQ 既吸取了传统 ORM 操作数据的简略性和安全性，又保留了原生 SQL 的灵活性，它更像是介于 ORMS 和 JDBC 的中间层。

### 7.5.彩蛋

在 [Spring Boot](https://www.weiye.link/category/rear/sringboot/) 1.0 项目中 src/main/resources 途径下新建一个 banner.txt 文件，文件中写入一些字符，发动项目时就会发现默许的 Banner 被替换了，到了 [Spring Boot](https://www.weiye.link/category/rear/sringboot/) 2.0 现在能够支撑 Gif 文件的打印，[Spring Boot](https://www.weiye.link/category/rear/sringboot/) 2.0 在项目发动的时分，会将 Gif 图片的每一个画面，依照次序打印在日志中，一切的画面打印结束后，才会发动 [Spring Boot](https://www.weiye.link/category/rear/sringboot/) 项目。