---
title: JavaEE-17-Redis-introduction
date: 2020-06-22 20:06:44
tags: JavaEE
---

## Redis应用场景

Redis是一种内存数据库，存储方式类似于Map结构，键值对形式。读取速度非常快，常用于高并发场景。

1. 数据缓存

对一些热点数据，读到内存中，使用Redis缓存，可以避免数据库的频繁读取，Redis常用来缓存。

2. 高速读写。

高并发场景下，类似于抢购、抢红包场景，数据读写速度要求高，因此使用数据库难以支撑。数据库读写数据的速度较慢，是对硬盘的直接读写，速度受限。当大量用户并发访问需要大量数据库连接进行读写时，系统会崩掉。借助于Redis的快速读写的特性（数据存于内存）

## 缓存

### 内存大小有限，我们不能什么都存Redis

1. 热点数据

对读取频率非常高的数据进行缓存

2. 数据读取多还是写入多？频繁写入的数据不适合缓存。

3. 数据大小如何？Redis不适合存数据较大的东西。

### Redis缓存后数据读取的流程

<img src='JavaEE-17-Redis-introduction\a2133681-bb42-4444-a6a0-7c5eae675076.jpg'>

### Redis缓存时数据写入流程

<img src='JavaEE-17-Redis-introduction\bf48ccae-4a29-485a-aa32-067c32e651b5.jpg'>

## 高速读写场合

对于商品抢购，抢红包类似的活动，用户并发访问的数量很大，如果单纯地使用数据库，很快就会宕机。

常采用的方式是，对数据库进行异步写入，用户的操作数据先存到Redis，等到合适的时机（如抢购活动结束），批量将数据写入数据库。在这里，Redis承担临时数据库的角色。

<img src='JavaEE-17-Redis-introduction\695fe0a5-0390-443a-b761-b86335f88209.jpg'>

每次请求过来，发起抢购操作，所有的数据都是对Redis操作，读写速度很快，因而响应速度快，解决并发访问量的问题。同时，每次抢购后都要判断是否操作结束，如商品数量剩余0，此时将批量写入数据库。

## Redis在win操作系统下的安装使用

1. 下载Redis

[点击此处下载Redis](https://github.com/ServiceStack/redis-windows/tree/master/downloads)

2. 启动命令行

<pre style='background:#e6e6e6;padding=10px;'>
redis-server redis.windows.conf
</pre>

3. 打开客户端工具

redis-cli.exe

## Redis在Linux下的安装使用

1. 下载解压

<pre style='background:#e6e6e6;padding=10px;'>
cd /usr/
mkdir redis
cd redis
wget http://download.redis.io/releases/redis-3.2.4.tar.gz
tar xzf redis-3.2.4.tar.gz
cd redis-3.2.4
make
</pre>

2. 运行服务端

<pre style='background:#e6e6e6;padding=10px;'>
src/redis-server
</pre>

3. 运行客户端

<pre style='background:#e6e6e6;padding=10px;'>
cd /usr/redis/redis-3.2.4
src/redis-cli
</pre>

## 使用Java操作Redis

1. 下载Jedis.jar

[点击此处下载Jedis](http://mvnrepository.com/artifact/redis.clients/jedis)

2. 使用Jedis操作

<img src='JavaEE-17-Redis-introduction\4de741c1-0c09-46a6-8505-6f5966ec1980.jpg'>

Jedis(String url, int port)构造Jedis客户端

auth(String password)用于输入密码

set(String key, String value)写入键值对

close()关闭连接

3. 使用连接池

<img src='JavaEE-17-Redis-introduction\ed889d86-f16a-4427-9f2a-823790f4105f.jpg'>

使用JedisPoolConfig创建连接池配置，使用配置创建JedisPool连接池，通过getResource()方法获取Jedis连接。其他方法与上面类似。

## Spring中使用Redis

1. 下载spring-data-redis

spring对Jedis的操作封装在spring-data-redis下的RedisTemplate中

[点击此处下载spring-data-redis](http://mvnrepository.com/artifact/org.springframework.data/spring-data-redis)

2. 配置Jedis连接池配置类

<img src='JavaEE-17-Redis-introduction\5dd774f9-02b4-4065-8cfd-d3e39c91fabf.jpg'>

3. 配置Jedis工厂

<img src='JavaEE-17-Redis-introduction\69509692-f685-403a-a618-4a6e56e1f797.jpg'>

4. 配置键序列化器、值序列化器、RedisTemplate

<img src='JavaEE-17-Redis-introduction\2836667e-a4af-45b8-ab7b-69163889f3c2.jpg'>

键使用StringRedisSerializer，值使用JdkSerializationRedisSerializer

5. 测试

对象需要实现Serializable接口(使用JDK序列化器)

<img src='JavaEE-17-Redis-introduction\c8ec944a-a590-4735-be3d-850998c6824d.jpg'>

读写操作：

<img src='JavaEE-17-Redis-introduction\aeabd851-8577-4c9f-9b55-f0cb8af7196c.jpg'>

redisTemplate.opsForValue().set(String key, object value)写入

redisTemplate.opsForValue().get(String key)读取

使用SessionCallback保证相同的Redis连接下操作：

<img src='JavaEE-17-Redis-introduction\5e68b1a2-300b-4ee1-ba26-9efe4fb8d037.jpg'>

redisOperations.boundValueOps(String key).set(object value)写入

redisOperations.boundValueOps(String key).get()读取

## Redis的六种数据类型

<img src='JavaEE-17-Redis-introduction\347ca6ac-597d-40a7-872f-a3f0ad5d1375.jpg'>







