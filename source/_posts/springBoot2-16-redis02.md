---
title: springBoot2-16-redis02
date: 2020-07-10 14:56:26
tags: spring-boot-2
---

## Redis事务

<img src='springBoot2-16-redis02\86ddc5ad-1b32-40b5-91d2-56ecc8445c13.jpg'>

使用redisTemplate.execute方法执行事务。

1. 监视变量

redisOperations.watch(String key)

2. 开启事务

redisOperations.multi();

3. 提交

redisOperations.exec();

<code style='background:#ff3385;color:white;padding:5px;'>注意</code>对于变量值变化，是可以实现事务的，但由于语法错误，导致抛出异常的话，是无法实现事务的。

## 流水线

流水线集中发送执行多条语句，实现批量提交。

<img src='springBoot2-16-redis02\0bc80bee-d3a1-4794-b7e3-930bc85c6d41.jpg'>

采用redisTemplate.executePimplined（）方法执行流水线操作。

需要注意的是，单次执行的数量不宜过大，否则返回的List容易导致内存溢出。

## 订阅及发布

1. 创建订阅者对象，并注册为Bean

<img src='springBoot2-16-redis02\3f1e6791-a0f9-4428-897f-d4fa94237d7d.jpg'>

实现MessageListener接口实现onMessage方法

2. 注册一个RedisMessageListenerContainer

<img src='springBoot2-16-redis02\2ab5e606-17e0-4536-8446-fb1c06d9fb35.jpg'>
<img src='springBoot2-16-redis02\61ce831b-e2ab-4691-b1b1-60ddf9771524.jpg'>

创建了一个异步线程池，用于接收消息。

创建了一个RedisMessageListenerContainer的Bean，配置了ConnectionFactory，TaskExecutor，并注册了监听者及对应的ChannelTopic

3. 测试

spring中可以使用redisTemplate.convertAndSend()发送数据

<img src='springBoot2-16-redis02\859287a9-713c-4285-ba59-91d452af9dae.jpg'>

也可以使用命令：

<img src='springBoot2-16-redis02\edcd8161-9539-40f1-b34d-1af720fd4d17.jpg'>

## Lua脚本

1. 简单脚本

<img src='springBoot2-16-redis02\d1bc95ad-d52a-4d92-bdff-6ab9358c36e0.jpg'>

2. 带参数的脚本

<img src='springBoot2-16-redis02\2b4dac40-5921-455f-bad5-c57008fa16f0.jpg'>

KEYS[1]表示第一个键

ARGV[1]表示第一个值

<img src='springBoot2-16-redis02\67e82d61-e315-4bec-8fb5-eebd330a3db5.jpg'>

