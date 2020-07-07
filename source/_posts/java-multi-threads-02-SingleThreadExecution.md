---
title: java-multi-threads-02-SingleThreadExecution
date: 2020-06-30 16:55:37
tags: java
---

## 非独木桥模式

<img src='java-multi-threads-02-SingleThreadExecution\2619ea40-d1b6-48e0-a5d0-93568cd7aacb.jpg'>

<img src='java-multi-threads-02-SingleThreadExecution\ae265d24-1343-4378-a3f4-fbbcec2b2466.jpg'>

### 多线程情况下无法保证数据读写的原子性

<img src='java-multi-threads-02-SingleThreadExecution\bc9de022-6c79-4685-9010-3697d18e2070.jpg'>

或者

<img src='java-multi-threads-02-SingleThreadExecution\563bf6c6-7ac4-4ac9-b8f9-b1d7273b1b13.jpg'>

## 独木桥模式

改进Gate类，使用同步方法：

<img src='java-multi-threads-02-SingleThreadExecution\f06854ea-8525-4f9a-ac27-56c8639997bf.jpg'>

数据的写入成为原子操作：

<img src='java-multi-threads-02-SingleThreadExecution\5152a815-bfff-4225-8eca-bafd4f97d700.jpg'>

独木桥模式对临界资源使用同步方法进行保护，使得同步方法称为原子步骤，数据写入是一致完成的。

<img src='java-multi-threads-02-SingleThreadExecution\bd246f40-e3a1-448b-bcbd-f42a485c2a59.jpg'>

## 独木桥模式使用情景

1. 单线程无需使用。

2. 多线程下，无共享资源，无需使用。

3. 多线程情况下，当共享资源实例的状态固定不变时(例如只读)，无需使用。

4. 多线程情况下，需要确保实例的状态的一执性，则使用独木桥模式。

一些线程安全的集合：

<img src='java-multi-threads-02-SingleThreadExecution\63c5aa12-e48e-4523-8a8f-72b0f674aae3.jpg'>

### 注意

1. 基本类型和引用类型的赋值和引用是原子操作

2. long和double的赋值和引用是非原子的

3. long、double的数据共享时，需要同步操作，或者使用volatile。

同时，java提供了AtomicInteger、AtomicLong、AtomicIntegerArray、AtomicLongArray用于进行原子操作。

### 信号量

使用Semaphore定义信号量，用于限定最大共享线程数。

日志类：

<img src='java-multi-threads-02-SingleThreadExecution\df4d53b5-f828-4a97-b2cb-be3d876712d7.jpg'>

共享资源类：

<img src='java-multi-threads-02-SingleThreadExecution\48519950-9920-4c93-8f50-796e2298f376.jpg'>
<img src='java-multi-threads-02-SingleThreadExecution\81ec581e-145e-4d9b-a8a9-9688353daf1b.jpg'>

多线程：

<img src='java-multi-threads-02-SingleThreadExecution\513a5a14-181f-481c-9658-c1cb092a7d4f.jpg'>
<img src='java-multi-threads-02-SingleThreadExecution\1cb2f187-4014-4e1c-8a92-ad3dee2d53ca.jpg'>

使用十个线程测试：

<img src='java-multi-threads-02-SingleThreadExecution\3c7018a5-1011-4a39-937e-c927d789d98f.jpg'>

始终最大由三个线程处理：

<img src='java-multi-threads-02-SingleThreadExecution\efd50d25-536d-4535-8818-a5b015f08bf7.jpg'>








