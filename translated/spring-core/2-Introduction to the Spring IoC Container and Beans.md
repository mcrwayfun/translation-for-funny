## Introduction to the Spring IoC Container and Beans

> 原文：[Introduction to the Spring IoC Container and Beans](https://docs.spring.io/spring/docs/5.1.3.RELEASE/spring-framework-reference/core.html#beans)
>
> 译者：mcrwayfun

This chapter covers the Spring Framework implementation of the Inversion of Control (IoC) principle. (See [Inversion of Control](https://docs.spring.io/spring/docs/5.1.3.RELEASE/spring-framework-reference/overview.html#background-ioc).) IoC is also known as dependency injection (DI). It is a process whereby objects define their dependencies (that is, the other objects they work with) only through constructor arguments, arguments to a factory method, or properties that are set on the object instance after it is constructed or returned from a factory method. The container then injects those dependencies when it creates the bean. This process is fundamentally the inverse (hence the name, Inversion of Control) of the bean itself controlling the instantiation or location of its dependencies by using direct construction of classes or a mechanism such as the Service Locator pattern.

本章节覆盖了 Spring Framework 反转控制（IoC）的实现原理（详情查看 [Inversion of Control](https://docs.spring.io/spring/docs/5.1.3.RELEASE/spring-framework-reference/overview.html#background-ioc).）IoC 也被称为依赖注入（DI）。这是一个对象定义其依赖关系（如何与其他对象协同工作）的过程，通过构造函数参数，工厂方法的参数或属性（对象实例化中设置，该对象由实例化或者从工厂方法中返回）。容器会在创建bean 时注入这些依赖。这个过程从根本上控制了 bean 不再由它本身实例化和定位，而是使用类的直接构造或者服务定位模式之类的机制。



The `org.springframework.beans` and `org.springframework.context` packages are the basis for Spring Framework’s IoC container. The [`BeanFactory`](https://docs.spring.io/spring-framework/docs/5.1.3.RELEASE/javadoc-api/org/springframework/beans/factory/BeanFactory.html) interface provides an advanced configuration mechanism capable of managing any type of object.[`ApplicationContext`](https://docs.spring.io/spring-framework/docs/5.1.3.RELEASE/javadoc-api/org/springframework/context/ApplicationContext.html) is a sub-interface of `BeanFactory`. It adds:

- Easier integration with Spring’s AOP features
- Message resource handling (for use in internationalization)
- Event publication
- Application-layer specific contexts such as the `WebApplicationContext` for use in web applications.

`org.springframework.beans` 和 `org.springframework.context` 是 IoC 容器最基本的包。BeanFactory 接口提供一种高级的配置机制能够管理任何对象。 ApplicationContext 是 BeanFactory 的一个子类，它提供了：

- 更容易集成 Spring's AOP 的功能
- 消息资源处理（用于国际化）
- 事件发布
- 应用层指定上下文环境，比如用于 web 应用的 `WebApplicationContext`



In short, the `BeanFactory` provides the configuration framework and basic functionality, and the `ApplicationContext` adds more enterprise-specific functionality. The `ApplicationContext` is a complete superset of the `BeanFactory` and is used exclusively in this chapter in descriptions of Spring’s IoC container. For more information on using the `BeanFactory` instead of the `ApplicationContext,` see [The `BeanFactory`](https://docs.spring.io/spring/docs/5.1.3.RELEASE/spring-framework-reference/core.html#beans-beanfactory).

简而言之，`BeanFactory` 提供了配置框架和基本功能， `ApplicationContext` 则添加了更多的企业应用功能。`ApplicationContext` 是 `BeanFactory` 的一个完整的超集，在本章节专门用于 Spring's IoC 容器的描述。想查看更多关于 `BeanFactory` 替代 `ApplicationContext` 的信息，详情见于 [The BeanFactory](https://docs.spring.io/spring/docs/5.1.3.RELEASE/spring-framework-reference/core.html#beans-beanfactory)。



In Spring, the objects that form the backbone of your application and that are managed by the Spring IoC container are called beans. A bean is an object that is instantiated, assembled, and otherwise managed by a Spring IoC container. Otherwise, a bean is simply one of many objects in your application. Beans, and the dependencies among them, are reflected in the configuration metadata used by a container.

在 Spring 中，那些由 Spring IoC 容器管理的，来自应用中的对象被称为 beans。bean 是一种由 Spring IoC 容器实例化，组装并且管理的对象。此外，bean 只是应用程序众多对象之一。Beans 与它们之间的依赖关系体现在容器使用的配置元数据中。