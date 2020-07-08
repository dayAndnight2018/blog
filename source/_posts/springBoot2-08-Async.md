---
title: springBoot2-08-异步线程池
date: 2020-07-08 19:44:53
tags: spring-boot-2
---

## 异步操作

对于网络或本地文件IO容易出现阻塞情况，对于web应用，卡顿情况更加明显。

<img src='springBoot2-08-Async\596a55d2-e03b-4550-92d0-92e533b430c8.jpg'>

对于耗时操作，我们一般采用异步方式进行处理，采用线程池的方式实现对任务的异步操作。

<img src='springBoot2-08-Async\e48d196a-82ee-4588-ab47-5f3ef2ecee43.jpg'>

## Spring实现异步任务

1. 配置线程池

使用@EnableAsync开启异步线程池，实现AsyncConfigurer接口，重写getAsyncExecutor方法

<img src='springBoot2-08-Async\058fe614-bce9-4baa-903e-19ec51a52ba7.jpg'>

2. 定义异步服务接口

<img src='springBoot2-08-Async\6abae681-b57a-44d3-b6d4-7408e476c4ee.jpg'>

3. 定义异步服务实现类

使用@Async注解异步方法

<img src='springBoot2-08-Async\a9cab3ca-689b-42b0-9d02-ab1b24e04ebe.jpg'>

4. 异步方法在调用上无异

<img src='springBoot2-08-Async\a85a299a-cf7c-4ff9-b7f1-2c7fe0e62005.jpg'>

区别在于，二者不在相同的线程里执行，因而不会出现阻塞的情况。


