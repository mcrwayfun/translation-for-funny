## Container Overview

> 原文：[Container Overview](https://docs.spring.io/spring/docs/5.1.3.RELEASE/spring-framework-reference/core.html#beans)
>
> 译者：mcrwayfun

The `org.springframework.context.ApplicationContext` interface represents the Spring IoC container and is responsible for instantiating, configuring, and assembling the beans. The container gets its instructions on what objects to instantiate, configure, and assemble by reading configuration metadata. The configuration metadata is represented in XML, Java annotations, or Java code. It lets you express the objects that compose your application and the rich interdependencies between those objects.

`org.springframework.context.ApplicationContext`  这个接口表示 Spring IoC 容器并且负责初始，配置和组装 beans。容器通过读取配置文件的元数据来去初始化，配置和组装对象。配置元数据体现在 XML 文件，Java 注解或者 Java 代码中。它（配置元数据）可以组成程序的对象以及对象之间的依赖关系。

------

Several implementations of the `ApplicationContext` interface are supplied with Spring. In stand-alone applications, it is common to create an instance of [`ClassPathXmlApplicationContext`](https://docs.spring.io/spring-framework/docs/5.1.3.RELEASE/javadoc-api/org/springframework/context/support/ClassPathXmlApplicationContext.html) or [`FileSystemXmlApplicationContext`](https://docs.spring.io/spring-framework/docs/5.1.3.RELEASE/javadoc-api/org/springframework/context/support/FileSystemXmlApplicationContext.html). While XML has been the traditional format for defining configuration metadata, you can instruct the container to use Java annotations or code as the metadata format by providing a small amount of XML configuration to declaratively enable support for these additional metadata formats.

Spring 为 `ApplicationContext` 接口提供了几种实现。在单例应用中，通常使用 [`ClassPathXmlApplicationContext`](https://docs.spring.io/spring-framework/docs/5.1.3.RELEASE/javadoc-api/org/springframework/context/support/ClassPathXmlApplicationContext.html) 或者 [`FileSystemXmlApplicationContext`](https://docs.spring.io/spring-framework/docs/5.1.3.RELEASE/javadoc-api/org/springframework/context/support/FileSystemXmlApplicationContext.html) 来创建一个实例。相比于使用传统格式： XML 文件来定义配置元数据，你可以使用 Java 注解或者代码作为元数据格式（通过提供少量的 XML 文件，以声明的方式支持其他数据配置元数据）来构造容器。

------

In most application scenarios, explicit user code is not required to instantiate one or more instances of a Spring IoC container. For example, in a web application scenario, a simple eight (or so) lines of boilerplate web descriptor XML in the `web.xml` file of the application typically suffices (see [Convenient ApplicationContext Instantiation for Web Applications](https://docs.spring.io/spring/docs/5.1.3.RELEASE/spring-framework-reference/core.html#context-create)). If you use the [Spring Tool Suite](https://spring.io/tools/sts) (an Eclipse-powered development environment), you can easily create this boilerplate configuration with a few mouse clicks or keystrokes.

在绝大多数的应用场景中，不需要使用硬编码的方式来初始化一个 Spring IoC 的容器。举个例子，在web 应用中，`web.xml` 中简单的8行配置就足够描述容器了（详见 [Convenient ApplicationContext Instantiation for Web Applications](https://docs.spring.io/spring/docs/5.1.3.RELEASE/spring-framework-reference/core.html#context-create) ）。如果你使用  [Spring Tool Suite](https://spring.io/tools/sts) ，只需要点击几下鼠标或按键，就可以轻松的创建此样板配置。

------

The following diagram shows a high-level view of how Spring works. Your application classes are combined with configuration metadata so that, after the `ApplicationContext` is created and initialized, you have a fully configured and executable system or application.

下面的图标展示了 Spring 的工作原理。 `ApplicationContext` 被创建和初始化后，应用类与配置元数据相结合，此时你拥有一个可配置和可操作的程序或应用。

![](https://github.com/mcrwayfun/translation-for-funny/blob/master/static/201914-104439.jpg)