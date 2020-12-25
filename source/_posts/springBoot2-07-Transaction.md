---
title: springBoot2-07-Transaction
date: 2020-07-10 09:00:34
tags: spring-boot-2
---

数据库事务是保证操作原子性的方式。

## 使用起来非常方便

只需要在服务层实现类的方法上添加@Transactional即可

<img src='springBoot2-07-Transaction\e7ec5ea4-663f-4f7d-b3df-21fb1885fe79.jpg'>

## 事务存在隔离级别

事务的隔离级别指的是不同事务之间的数据共享的问题。可以通过Transactional注解的isolation属性进行设置。

也可以通过配置文件设置默认的事务级别：

<img src='springBoot2-07-Transaction\a3dcc4af-6141-4065-8551-fda76161843b.jpg'>

## 事务的传播行为

事务的传播行为指的是子服务调用时，是否在相同的事务里执行的问题。

<img src='springBoot2-07-Transaction\c5d21903-1844-49c7-95a6-4f1ae3a7095a.jpg'>

<img src='springBoot2-07-Transaction\ae382efa-709d-4522-be29-48ed7a1420fa.jpg'>

<img src='springBoot2-07-Transaction\12cf066b-05d4-4427-a6db-620c66fa89f5.jpg'>

nested与requires_new的区别在于，nested沿用父服务的隔离级别及锁特性，优先使用保存点技术实现。而requires_new则有独立的隔离级别及锁特性。

## 自调用失效问题

在同一个服务内，子服务采用requires_new，父服务调用本服务内的子服务，出现不会开启新事务的问题。

<img src='springBoot2-07-Transaction\ac491659-af5e-460b-a01c-fe27f3fbacf0.jpg'>

解决思路：

1. 将服务分离到不同的服务。

2. 采用注入ApplicationContext的方式，每次调用子服务时，都采用来自context获取的新子服务实例。

<img src='springBoot2-07-Transaction\604bd5da-e103-4b02-aef0-a264bb57baae.jpg'>