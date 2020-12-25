---
title: springBoot2-10-ActiveMQ
date: 2020-07-08 20:45:20
tags: spring-boot-2
---

## 异步消息

点对点：当前系统将消息发送到指定的消息系统。

发布-订阅：实现一对多的消息发布，订阅方获取消息后可以自由处理。

## ActiveMQ的下载安装

1. [点击此处下载](http://activemq.apache.org/download)

2. linux执行.sh文件，win执行bat文件

3. 登陆http://localhost:8161/admin

账户admin，密码admin

## spring整合ActiveMQ

1. 添加依赖

<img src='springBoot2-10-ActiveMQ\181253f1-1b65-461c-9965-a0a5791afe9f.jpg'>

2.application.properties

<img src='springBoot2-10-ActiveMQ\0226d06b-f5c6-4c99-a741-074a8178d048.jpg'>

3. 定义消息服务接口

<img src='springBoot2-10-ActiveMQ\32cbe12e-8f82-4b33-a88f-8ad9b2e27f45.jpg'>

4. 定义消息服务实现类

<img src='springBoot2-10-ActiveMQ\2c988013-463e-4195-be6b-e7e4c8197dd5.jpg'>
<img src='springBoot2-10-ActiveMQ\1332872a-f03d-4ce9-ad78-4878c2560f00.jpg'>

使用@JmsListener注解标记消息来源

5. 发送POJO

定义POJO

<img src='springBoot2-10-ActiveMQ\ddc86846-62d2-4592-803b-cadfb8bea0ca.jpg'>

添加服务方法

<img src='springBoot2-10-ActiveMQ\5ba03acd-3c59-4d6f-b048-b6ce9fe7edf3.jpg'>

配置信任的包

<img src='springBoot2-10-ActiveMQ\a7b42fdc-364c-41f2-adc2-5909f4eeca2f.jpg'>


