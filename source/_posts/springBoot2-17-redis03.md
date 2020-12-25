---
title: springBoot2-17-redis03
date: 2020-07-10 15:36:49
tags: spring-boot-2
---

## Redis缓存

1. 配置redis缓存

<img src='springBoot2-17-redis03\9aba6c58-9599-4c04-ae04-b991c850d5df.jpg'>

这里spring.cache.type=REDIS

spring.cache.cache-names=redisCache

2. spring boot将自动创建RedisCacheManager

<img src='springBoot2-17-redis03\a7a36c59-7596-4679-b3b0-d58e601a827c.jpg'>

开启@EnableCaching即可使用Redis进行缓存了

3. 配置mysql数据源、mybatis、redis、日志、

<img src='springBoot2-17-redis03\85b7d9c7-2c66-44ef-a199-7e18a4084cf7.jpg'>

4. 配置缓存

<img src='springBoot2-17-redis03\acc6c226-6d55-479c-939a-567816b8cd87.jpg'>

5. 创建POJO

<img src='springBoot2-17-redis03\d0f312be-f2f8-4abc-a166-142e0cdc79e5.jpg'>

6. 创建DAO接口

<img src='springBoot2-17-redis03\53803a63-f915-4acf-b1d2-b55f57858181.jpg'>

7. 创建Mapper文件

<img src='springBoot2-17-redis03\de74ed7e-4328-4f2f-91f2-5befd1c6ada3.jpg'>
<img src='springBoot2-17-redis03\2ae95c4c-af8f-42ad-a9c3-0996d61c8406.jpg'>

8. 创建服务层接口

<img src='springBoot2-17-redis03\28c499eb-dc89-4577-9f89-c169ab06fe7e.jpg'>

9. 创建实现类

<img src='springBoot2-17-redis03\b33a005a-552c-431a-a63a-adf1cb00379a.jpg'>
<img src='springBoot2-17-redis03\fed76443-c665-462f-9c35-0d4141de1568.jpg'>
<img src='springBoot2-17-redis03\d8330988-4f13-4d6e-8e89-fc8fee342b3a.jpg'>

CachePut用于将结果存入缓存

Cacheable先查缓存，不存在则将方法结果存入缓存

CacheEvict擦除缓存

beforeInvocation表示是否在方法执行前擦除，默认false

key表示缓存的键，#id表示输入参数#result.id表示返回值对象的id属性。condition表示缓存条件，符合条件才执行相关操作。

对于更新操作，请优先查询数据库，不要轻信缓存，容易出现脏数据。

## 设置超时时间

设定超时是保障数据实时更新的方式：

<img src='springBoot2-17-redis03\ff524a62-3816-4f79-827a-62963757af8e.jpg'>

或者自定义缓存管理器

<img src='springBoot2-17-redis03\4687f99c-101b-4306-a4c2-4321544b1f4f.jpg'>