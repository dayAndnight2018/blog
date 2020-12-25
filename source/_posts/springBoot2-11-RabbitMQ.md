---
title: springBoot2-11-RabbitMQ
date: 2020-07-08 21:09:32
tags: spring-boot-2
---

RabbitMQ基于RMQP服务进行消息传递，对客户端及开发语言屏蔽。

## RabbitMQ使用

1. 添加依赖

<img src='springBoot2-11-RabbitMQ\e187c167-35c5-49f1-870e-4f9bac5144c1.jpg'>

2. 配置application.properties

<img src='springBoot2-11-RabbitMQ\cd7ed0a8-aafe-4fda-b839-7c7d58070629.jpg'>
<img src='springBoot2-11-RabbitMQ\e06d202f-91ff-4b77-9c20-12d327c084a9.jpg'>

3. 将两个队列注册为Bean

<img src='springBoot2-11-RabbitMQ\c2602b2b-6de4-4ed1-98ea-1945cb9aa55b.jpg'>

4. 消息发送接口

<img src='springBoot2-11-RabbitMQ\a9556313-d6cd-477a-9f55-aa7a932221e5.jpg'>

5. 消息发送实现类

<img src='springBoot2-11-RabbitMQ\6f4a7b20-1ffa-4af0-8ffb-df1559445e60.jpg'>
<img src='springBoot2-11-RabbitMQ\7f06d2e9-a9de-4f04-b0e8-9d63a98e0339.jpg'>
<img src='springBoot2-11-RabbitMQ\718a40ab-4a3d-476d-aaa3-72e328842c0c.jpg'>

6. 消息订阅者

<img src='springBoot2-11-RabbitMQ\070dd276-d6c9-4d26-8795-6525c28dba86.jpg'>

