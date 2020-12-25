---
title: java20 并发包
date: 2020-02-29 19:42:57
tags: java
---

## 原子变量

AtomicBoolean, AtomicInteger, AtomicLong，AtomicReference等都属于原子变量，提供原子操作。

提供了很多原子操作方法：addAndGet, decrementAndGet,getAndIncrement, incrementAndGet

getAndIncrement 与 incrementAndGet是有区别的，在于自增在前还是在后。

自增在后：

<img src='java20-Concurrency-Utilities\e9c1af03-edd8-408b-8d9a-35534a4a9ca4.jpg' >

自增在前：

<img src='java20-Concurrency-Utilities\01782e20-eb2e-4761-b4b5-eaf9a35f93a2.jpg' >

这样，即便是不再使用同步标志，也可以实现线程安全，因为所有的操作都是原子的。

<img src='java20-Concurrency-Utilities\9f2f8203-2cdd-424e-b464-7a0c0463693a.jpg'>

## Executor & ExecutorService

建议使用Executor替换Thread执行Runnable多线程方法：

<img src='java20-Concurrency-Utilities\66a977eb-b924-4f5d-b46b-1892e2c66df5.jpg'>

也可以使用Executors的辅助方法创建ExecutorService：

<img src='java20-Concurrency-Utilities\ef4a52bc-5793-4014-83e3-d62b02c15541.jpg'>

newSingleThreadExecutor只包含一个thread，只能同时执行一个线程。

newCacheThreadPool 只要内存足够就创建线程，容易out of memory

newFixedThreadPool 创建指定个数线程

提交到Executor:

<img src='java20-Concurrency-Utilities\e74042da-7958-4d54-b092-bb08f36d4708.jpg'>

Callable类似于Runnable，但是可以有返回值，也可以抛出异常。其执行的方法是call()

可以通过ExecutorService的submit方法传递Callable对象：

<img src='java20-Concurrency-Utilities\5c611e1e-8d7e-424a-8f38-3c7dee84a69a.jpg'>

Future可以中止线程，或者获取返回值。

<img src='java20-Concurrency-Utilities\d0ef58c6-d21f-4a6c-9f91-78dc25fc1c38.jpg'>

也可以获取返回值：

<img src='java20-Concurrency-Utilities\01d743fa-0f0b-4696-b669-e3837cdc12b6.jpg'>

判断任务被取消或已完成：

<img src='java20-Concurrency-Utilities\5373625c-7f12-4ce4-a29b-8b7addbb68d7.jpg'>

获取结果：

<img src='java20-Concurrency-Utilities\42a2e30c-bf10-44fe-9c63-4289b4c51eb1.jpg'>

## 锁可以实现随时锁定和释放

<img src='java20-Concurrency-Utilities\2738e76b-cdd4-4de5-b46e-b955329656b4.jpg'>

ReentrantLock是其中一种实现，lock用于锁定，unlock解锁。


