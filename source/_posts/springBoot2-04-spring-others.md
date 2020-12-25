---
title: springBoot2-04-spring-others
date: 2020-07-07 09:56:29
tags: spring-boot-2
---

## 使用配置文件

1. 添加依赖

<img src='springBoot2-04-spring-others\82bc16ae-3989-4732-89d9-dca1ae17ae71.jpg'>

2. 添加配置

默认使用application.properties

<img src='springBoot2-04-spring-others\cef014e8-a48e-405d-955a-ecc19d200b78.jpg'>

3. 使用@Value注入

<img src='springBoot2-04-spring-others\1587f209-dfe6-49f3-8fdd-040380b5919e.jpg'>

可以对字段，set方法进行注解

4. 使用ConfigurationProperties简化

<img src='springBoot2-04-spring-others\e6e36f31-f788-406e-876f-d8a5709e5ea5.jpg'>

指定起始database

## 配置文件分离

单纯使用application.properties很杂乱，可以将配置分离出去，使用PropertySource指定配置文件的位置

<img src='springBoot2-04-spring-others\fda12423-9300-40cd-98be-5fd6f0d81de5.jpg'>

引入配置文件

<img src='springBoot2-04-spring-others\73e29f75-5dd2-4aca-a6b2-eceb26a3528a.jpg'>

使用ConfigurationProperties简化

<img src='springBoot2-04-spring-others\fa093558-1090-4720-a710-17c78d002be8.jpg'>

添加依赖

<img src='springBoot2-04-spring-others\1957105e-fc30-4cac-b25e-6df7bec9e1e3.jpg'>


## 条件装配

满足条件则装配，不满足则不装配。

1. 设计条件类，实现Condition接口，重写matches方法

<img src='springBoot2-04-spring-others\1b392eb3-4af8-4299-b6ac-c5366c36886f.jpg'>

2. 使用@Conditional注解指定条件类

<img src='springBoot2-04-spring-others\c31fc6ee-1fbb-4c84-ae28-8e071c24f688.jpg'>

## Bean的作用域类型

<img src='springBoot2-04-spring-others\6f7cfb68-b955-4a84-971d-00fb2cca0ae0.jpg'>

使用ConfigurableBeanFactory指定singleton或prototype类型

<img src='springBoot2-04-spring-others\18210e39-2b5e-43d6-9cae-e610951e1271.jpg'>

或使用WebApplicationContext指定session request或application类型

<img src='springBoot2-04-spring-others\f46903a4-6a6b-48e4-ae50-aec37f34b19b.jpg'>

## Profile--解决不同开发环境的问题

使用@Profile注解标记Bean的有效环境，使用spring.profiles.active激活。

<img src='springBoot2-04-spring-others\4ee2a669-f0bd-4c6e-992f-1f6c9f4cb3f8.jpg'>

## 引入xml配置的Bean

对于某个Bean：

<img src='springBoot2-04-spring-others\cae39590-76c8-4d4d-95ef-f21afb4601ae.jpg'>

使用xml注册到容器：

<img src='springBoot2-04-spring-others\ffee5a36-94a5-4a22-8818-59343381634e.jpg'>

配置类中使用@ImportResource加载Bean：

<img src='springBoot2-04-spring-others\698d912c-a34f-40cd-8a9c-c4418a05f00e.jpg'>

## EL表达式

1. 读取属性用$

<img src='springBoot2-04-spring-others\72641c4a-ae42-4643-b7ef-a453448ced8f.jpg'>

2. 操作属性用#

<img src='springBoot2-04-spring-others\b93f26b2-cbfe-491a-89ee-70224b7c4892.jpg'>

3. 赋值

<img src='springBoot2-04-spring-others\2795c692-baac-4987-8d4b-652506d8e18a.jpg'>

4. 获取其他Bean的属性并注入

<img src='springBoot2-04-spring-others\7456e0ab-4877-4fdb-85b9-a339975a02a5.jpg'>

进一步操作：

<img src='springBoot2-04-spring-others\db0f1570-ce03-475c-ba63-782064a78750.jpg'>

5. 其他计算

<img src='springBoot2-04-spring-others\f8e87cd3-4d3c-4f94-bb9e-cc83f8be17d9.jpg'>


