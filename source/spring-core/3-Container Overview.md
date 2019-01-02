## Container Overview

> 原文：[Container Overview](https://docs.spring.io/spring/docs/5.1.3.RELEASE/spring-framework-reference/core.html#beans)
>
> 译者：mcrwayfun

The `org.springframework.context.ApplicationContext` interface represents the Spring IoC container and is responsible for instantiating, configuring, and assembling the beans. The container gets its instructions on what objects to instantiate, configure, and assemble by reading configuration metadata. The configuration metadata is represented in XML, Java annotations, or Java code. It lets you express the objects that compose your application and the rich interdependencies between those objects.

`org.springframework.context.ApplicationContext`  这个接口表示 Spring IoC 容器并且负责初始，配置和组装 beans。容器通过读取配置文件的元数据来去初始化，配置和组装对象。配置元数据体现在 XML 文件，Java 注解或者 Java 代码中。它（配置元数据）可以组成程序的对象以及对象之间的依赖关系。