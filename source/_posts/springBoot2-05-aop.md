---
title: springBoot2-05-aop
date: 2020-07-07 13:46:56
tags: spring-boot-2
---

## 自定义AOP

1. 创建被监视接口

<img src='springBoot2-05-aop\8b19be56-dbbd-48fe-a2f9-e52eec4c529b.jpg'>

2. 创建实现类，并注册为服务

<img src='springBoot2-05-aop\7515b9c9-5f52-4871-96e7-632053c97a39.jpg'>

3. 创建切面

<img src='springBoot2-05-aop\5c7498e7-e5d1-4228-a8f0-4aaa60853a1a.jpg'>
<img src='springBoot2-05-aop\9535bd6a-6ea0-492f-aa07-4c66988c2dbd.jpg'>

4. 将切面注册为Bean

<img src='springBoot2-05-aop\dddebe2b-31b3-42a4-ba04-fab17dcb2c57.jpg'>

5. 测试结果

<img src='springBoot2-05-aop\da70ed1b-e382-4258-9953-ca8be89d8779.jpg'>

## 引入

1. 设计增强接口

<img src='springBoot2-05-aop\aa274e7c-5f58-4a5f-9876-d5eda076a290.jpg'>

2. 设计增强接口的实现类

<img src='springBoot2-05-aop\b995e87e-96bf-4149-bddd-bc094f8c1b95.jpg'>

3. 在切面中声明public类型的增强接口的实例

<pre style='background:#e6e6e6;padding=10px;'>
 @DeclareParents(defaultImpl = com.example.learnspring.services.Auditor.class,value = "com.example.learnspring.services.IPrinter+")
 public IAuditor auditor;
</pre>

4. 强转为增强接口对象

<img src='springBoot2-05-aop\ed102ead-ce06-4d6f-be43-1fa7f3ab7899.jpg'>

## 多个切面执行前后顺序

可以使用@Order注解标记次序，越小越靠前

<img src='springBoot2-05-aop\72b2e5b1-3780-4678-a1dd-78779d16f365.jpg'>