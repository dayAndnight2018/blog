---
title: java-multi-threads-01-introduction
date: 2020-06-30 15:28:19
tags: java
---

## 单线程程序

<img src='java-multi-threads-01-introduction\a54678ce-50ba-4f2d-b610-bd2e7e8d238c.jpg'>

对上图的程序，只有一个线程，循环语句依次执行。

<img src='java-multi-threads-01-introduction\f57a09b6-2fe1-45a1-a133-2682e2c6ac6f.jpg'>

## 多线程程序

1. 搜索文本的同时，响应按钮操作

2. 文件及网络的IO是非常耗时的操作，使用多线程提高cpu效率

3. 服务端对多个客户端进行处理

### 使用Thread实例

设计一个多线程实现类，用于打印Nice

<img src='java-multi-threads-01-introduction\f2f3a6bc-bd46-4f28-bae4-9d944e02bd8d.jpg'>

主线程开启线程打印Nice，并自己打印Good

<img src='java-multi-threads-01-introduction\39a3599b-8d71-4f35-85bf-c7d3d2ff3a1e.jpg'>

通过thread.start()方法启动线程。

### 使用Runnable实例

<img src='java-multi-threads-01-introduction\d37edae9-1a59-4ec3-99a4-903dfe1fa24a.jpg'>
<img src='java-multi-threads-01-introduction\abf3c38f-4126-4518-a314-09dd62d37016.jpg'>

使用新的Thread实例包装Runnable接口的实现类，使用start()启动。

### 使用Executor的defaultThreadFactory创建多线程实例

<img src='java-multi-threads-01-introduction\c27abf3e-9cfe-485b-a43e-6a1077791018.jpg'>

## 线程睡眠

线程让渡cpu进行休眠Thread.sleep的方式：

<img src='java-multi-threads-01-introduction\74556cba-9ea3-4533-923d-0240691fa137.jpg'>

此种方法需要捕获InterrupException

主线程间隔1秒打印good

## 线程互斥

在银行取款逻辑中，需要先确定账户的余额大于0：

<img src='java-multi-threads-01-introduction\6bdd3f18-2a2d-466e-a737-7be9e93b43c3.jpg'>

但是，在多线程情况下，两个线程同时执行这段代码，可能出现余额为负数的情况。

因为多线程情况下，各线程执行代码的情况无法控制，若存在以下情况，则会出现余额小于0的情况：

<img src='java-multi-threads-01-introduction\d2a8c5bc-4144-4d3d-b9f2-a3e254b2c2f3.jpg'>

为了解决多个线程执行混乱的问题，使用互斥解决以上问题。

### 使用synchronized

使用该标记的方法默认为同步方法（单个时刻只能由一个线程执行）

<img src='java-multi-threads-01-introduction\a0bea4e0-f940-4b4b-9b0e-b6897be7a196.jpg'>

不同类型的方法的访问示意图：

<img src='java-multi-threads-01-introduction\0557c90d-fc2f-49ea-9795-f2fecab058f1.jpg'>

### 使用同步代码块

通过同步代码块实现：

<img src='java-multi-threads-01-introduction\dcb445eb-528e-4e50-bbea-715aaf70b1df.jpg'>

对于实例方法，相当于锁定当前的对象：

<img src='java-multi-threads-01-introduction\526c6605-73d9-4885-a81b-8814511df56e.jpg'>

对于静态方法，相当于锁定Class：

<img src='java-multi-threads-01-introduction\3fb686a7-d746-4e90-9a3d-f1b237aaf8ae.jpg'>

## 线程协作

我们要解决一个存取快递的问题。快递员取快递，用户存快递。快递柜只有一个，用户存了快递就不能再存，通知快递员取快递。快递员取了快递就不能再取，除非用户重新放入了快递。

线程执行wait方法后进入等待队列：

<img src='java-multi-threads-01-introduction\c4b8a759-66cc-4ba5-9785-31780538b24e.jpg'>

此时，其他线程可以访问同步方法：

<img src='java-multi-threads-01-introduction\e73cab0d-8a16-475e-a66e-ef348091fd43.jpg'>

当其他线程处理结束，条件允许后，可以通知其他线程：

<img src='java-multi-threads-01-introduction\6921a74a-524d-404a-8535-6d8bc3058b2b.jpg'>

线程B退出后，就可以继续执行A线程了。

<img src='java-multi-threads-01-introduction\bf230c76-8235-4d2e-acfb-ef8bf1215dc9.jpg'>






