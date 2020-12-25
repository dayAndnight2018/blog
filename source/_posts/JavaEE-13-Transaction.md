---
title: JavaEE-13-Transaction
date: 2020-06-21 22:03:07
tags: JavaEE
---

## 数据库事务管理器

事务管理器就是管理数据库事务的工具，对于Mybatis，常用的就是DataSourceTransactionManager

### xml方式配置

<img src='JavaEE-13-Transaction\a0849b76-18d6-46a0-94fe-fdcaa66c7f3b.jpg'>

### Java配置

需要实现TransactionManagerConfigurer接口的annotationDrivenTransactionManager方法，将返回的事务管理器作为项目的事务管理器。

<img src='JavaEE-13-Transaction\2d6c7c6d-0730-4875-82f4-3c1a34db5fd1.jpg'>

使用@EnableTransactionManagement表示遇到@Transactional时，使用本事务管理器管理事务。

重写annotationDrivenTransactionManager方法：

<img src='JavaEE-13-Transaction\a8695828-a310-401c-b68b-e99937c65fa0.jpg' >

## 事务类型

1. 编程式事务

2. 声明式事务

## 编程式事务

<img src='JavaEE-13-Transaction\18e583cc-b510-4472-8a32-ba32ae06f2da.jpg'>
<img src='JavaEE-13-Transaction\69368772-4cf0-4245-a8a3-bab6c9ad39a1.jpg'>

通过TransactionDefinition定义一个事务，采用transactionManager获取一个TransactionStatus状态对象，对状态进行提交或回滚。

编程式事务完全靠代码手动控制提交，回滚。

## 声明式事务

### @Transactional选项

<img src='JavaEE-13-Transaction\45cf8122-ade3-4821-8952-e123b67f5586.jpg' >
<img src='JavaEE-13-Transaction\5d5892f6-1440-44c1-94fc-9901c52bdfd6.jpg'>

### 开启注解驱动

<img src='JavaEE-13-Transaction\1ab2f8b7-9c6d-42fd-9470-d937305f115c.jpg'>

## 数据库隔离级别的选择

<img src='JavaEE-13-Transaction\7a656cc0-a18f-4f7c-b7bb-e0d607542815.jpg' >

对高并发场景一般采用读已提交级别，并发小的场景可采用序列化级别。

<img src='JavaEE-13-Transaction\f69d4cde-b4be-4ce8-bda2-eb155a28f7aa.jpg' >

<img src='JavaEE-13-Transaction\897a200f-2334-41f1-ab13-2acc0cdc3ea6.jpg' >

## 传播行为

### 什么是传播行为？

不同服务层方法调用时，事务的传递性原则称为事物的隔离级别。

例如：

PayBatchService批量支付服务，他需要循环调用PayService进行支付，正常来说，这个过程中，有一次支付失败，将回滚到第一个支付行为，不管前面已经支付成功。这样造成效率低的问题。我们希望：只回滚本次事务。

通过设置传播行为，可以解决回滚的粒度问题。

<img src='JavaEE-13-Transaction\88fd81f4-97f8-4f16-9c8e-4fa30f0ac466.jpg' >

### 几种传播行为

<img src='JavaEE-13-Transaction\10f7055c-fcb2-4384-afc1-502bb3ce7b4b.jpg'>

## 在SSM中使用事务

1. 开启注解驱动、开启包扫描，配置数据源

<img src='JavaEE-13-Transaction\956bf458-1520-478f-9305-86444ff140df.jpg' >

2. 配置SqlSessionBeanFactory

<img src='JavaEE-13-Transaction\2c9cdf74-c8f8-4113-93fb-f16a78c9c75d.jpg'>

3. 配置事务管理器

<img src='JavaEE-13-Transaction\c8b31f9d-b744-4e06-a905-5e268a430552.jpg' >

4. 配置注解驱动事务

<img src='JavaEE-13-Transaction\0ed66cd8-52cd-47b4-b728-2d9ee1daaade.jpg' >

5. 配置Mapper扫描机制

<img src='JavaEE-13-Transaction\bbf9489e-e3db-4587-b48c-9872429f2110.jpg' >

6. 事务使用

<img src='JavaEE-13-Transaction\a8c5c8e7-4082-4d85-bc0d-41fe3e9f89da.jpg' >

<img src='JavaEE-13-Transaction\94fcf187-0ba4-406a-98e7-066aa31e17a8.jpg' >

PayBatchService使用Requierd，PayService使用Requires_new传播

## 自调用失效问题

对静态、非public方法@Transactional失效

刚才的例子是不同的服务之间调用，事务传播行为有效，如果PayBatchService与PayService在相同类中，就会失效。因为基于动态代理实现的，相同类不会产生新的代理对象。

可以通过手动获取代理对象解决：

<img src='JavaEE-13-Transaction\a15d2b03-fd5a-470a-ac92-83ac5603aa88.jpg'>









