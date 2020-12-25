---
title: java-multi-threads-03-Immutable
date: 2020-06-30 19:15:36
tags: java
---
## 除了构造函数，无法赋值

<img src='java-multi-threads-03-Immutable\733c61c9-27f5-4cca-8417-a1f28a11956e.jpg'>

将字段设置为final类型，字段一旦初始化就不再赋值。

使用多线程来读取person信息：

<img src='java-multi-threads-03-Immutable\57be253c-2e6d-490d-89fb-de6fe39db027.jpg'>

测试：

<img src='java-multi-threads-03-Immutable\aafa54ab-e1d1-417b-aa8d-b3e319b3197a.jpg'>

由于只能读取，不能赋值，因此数据是可信的。

## 使用场景

1. 对象创建后，基本不发生改变。

2. 对象是共享的，频繁读取，而不是赋值。

## ArrayList的并发读写问题

在ArrayList多线程情况下，并发读写会引发异常信息。

<img src='java-multi-threads-02-SingleThreadExecution\c321f193-7a5e-48e2-a811-a30932a402f5.jpg'>

<img src='java-multi-threads-02-SingleThreadExecution\2fe06788-5660-4f74-b2b1-ba807817697b.jpg'>

当同时读取和写入会引发异常ConcurrentModifyException。

### 使用synchronizedList

<img src='java-multi-threads-02-SingleThreadExecution\75efc6cc-99c0-4de0-8544-58d13817a02b.jpg'>

将其同步即可实现并发读写。

### 使用CopyOnWrite

<img src='java-multi-threads-02-SingleThreadExecution\61f59bff-80b1-4e9a-a3f0-53e0d4015a2d.jpg'>

在有写入时，对数组完成复制再进行写入，读取的是副本。每次写入时，都需要复制，对于频繁写入的情景不适用。

