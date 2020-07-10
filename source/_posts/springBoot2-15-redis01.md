---
title: springBoot2-15-redis01
date: 2020-07-10 09:47:57
tags: spring-boot-2
---

Redis是一种高性能内存数据库，支持硬盘持久化数据。具有高读写速度，常用于高并发及缓存。

## Redis基础使用

1. 添加依赖

<img src='springBoot2-15-redis01\dd684114-8c3e-4b7e-954a-409a690cad3e.jpg'>

2. 配置RedisConnectionFactory

<img src='springBoot2-15-redis01\0d5cbc3a-58ae-48cf-9c86-75d2e68a2006.jpg'>

3. 配置RedisTemplate

配置了序列化器及连接池管理

<img src='springBoot2-15-redis01\bc473038-847e-4561-943a-0ce186a95f95.jpg'>

4. 对不同类型的封装方法

<img src='springBoot2-15-redis01\49cd4336-9f9e-4a60-98e3-dfac4c2a928a.jpg'>

5. 获取不同类型的操作

<img src='springBoot2-15-redis01\293bd4c1-730d-480f-beec-930ed56d1b24.jpg'>

6. 绑定不同类型的操作

<img src='springBoot2-15-redis01\b9c22eb0-cece-4c39-b482-5e0baf1b65c1.jpg'>

7. 使用同一条连接操作

SessionCallback及RedisCallback均可以实现多条语句在一条连接里执行。

<img src='springBoot2-15-redis01\401559f1-5a47-4a67-9aea-2acdc10c2266.jpg'>

## 在Spring boot中使用Redis

1. 配置连接池及连接信息

<img src='springBoot2-15-redis01\9cb2e2ce-f2de-4180-9166-67a95d46bbfc.jpg'>

2. 在启动类上配置序列化器

<img src='springBoot2-15-redis01\16c651a4-27d6-4f19-9955-4f0b8e48e15b.jpg'>

3. 常用的操作

<img src='springBoot2-15-redis01\50259d1c-90a2-43dd-b81e-6d5a08f7a8a0.jpg'>

List

<img src='springBoot2-15-redis01\63106093-3b8d-4cf4-b8cf-77d888d10d4f.jpg'>

Set

<img src='springBoot2-15-redis01\158722b9-fb8b-41c9-98dc-eec800086613.jpg'>

ZSet

<img src='springBoot2-15-redis01\2f1b1d62-cf05-4066-ad74-2965dd47a966.jpg'>