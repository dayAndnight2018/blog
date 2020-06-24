---
title: JavaEE-11-Spring-Aop
date: 2020-06-20 22:38:50
tags: JavaEE
---

## AOP术语

### 切面

切面就是引入的代码，比如，记录日志，自动关闭JDBC连接等等

### 通知

切面里的方法就是通知，

<img src='JavaEE-11-Spring-Aop\c1a1722b-86f0-4d90-b095-bf28ec49106f.jpg'>

### 引入

为现有的类增强方法

### 切点

被拦截的方法就是切点

### 连接点

用于判定切点的方法

### 织入

生成动态代理的过程

## 四种实现Aop的方式

<img src='JavaEE-11-Spring-Aop\b6337517-6b00-489b-9737-178be3c3c932.jpg'>

## 使用@AspectJ注解开发Aop

### 选择合适的切点

选定拦截谁

1. 创建一个接口

<img src='JavaEE-11-Spring-Aop\bd83b016-5b3f-4016-8980-d1385ad10fb7.jpg'>

2. 实现这个接口

<img src='JavaEE-11-Spring-Aop\d16b7c49-93be-4386-bcb9-18bd2e8d1a34.jpg'>

我们确定把printRole这个方法作为切点，拦截他。

### 创建切面

怎么拦截？

创建Aspect类，对切点进行拦截

<img src='JavaEE-11-Spring-Aop\b5b33ce9-f4e9-4821-959f-35b6a4bff413.jpg'>

可能用到的注解：

<img src='JavaEE-11-Spring-Aop\11f734e9-1961-490b-b5a7-e9610a2cc2bd.jpg'>

### 连接点

确定准确的拦截位置

<img src='JavaEE-11-Spring-Aop\dc13d182-1c70-4800-ab09-ad248c0c3930.jpg'>

execution表示方法执行时触发切面方法

*代表任意返回类型

com.ss.chapter11.aop.service.impl.RoleServiceImpl.printRole是确定的方法

(..)表示任意参数

其他常用的参数

<img src='JavaEE-11-Spring-Aop\2b63a252-ef5f-4aa5-b373-b23abbd5741b.jpg'>

可以使用PointCut简化切面的定义

<img src='JavaEE-11-Spring-Aop\e7db1664-718c-4b22-b51b-78dcabe02ac6.jpg'>

### 测试Aop

将定义的切面注册为Bean，并在配置类上开启AspectJ，方法调用时会执行相关的切面方法

<img src='JavaEE-11-Spring-Aop\b3cd4872-9d0e-43e8-96b8-0e9bc47c9b1b.jpg'>

也可以使用xml开启aop

<img src='JavaEE-11-Spring-Aop\c621279b-1939-4a71-b182-408912721323.jpg'>

### 环绕通知

<img src='JavaEE-11-Spring-Aop\1a0202ff-6808-41f7-a940-2144cf1b9332.jpg'>

### 切面方法传参

对于带参数的切点

<img src='JavaEE-11-Spring-Aop\0324ffb2-5bd2-49d8-b6ac-424ff56752f4.jpg'>

可以使用args(xx,xx)指定参数

<img src='JavaEE-11-Spring-Aop\e0f61ea6-e326-4ac1-9b82-41926d8aed7e.jpg'>

## 引入

通过接口方法对类增强。

1. 定义增强接口

<img src='JavaEE-11-Spring-Aop\eeaaafd9-35ee-4264-ac69-cfd68144e9a4.jpg'>

2. 定义增强接口的实现

<img src='JavaEE-11-Spring-Aop\fd30df5b-4aac-45b1-89a1-0776d48589bc.jpg'>

在切面中增加增强接口的实例，添加@DeclearParents注解

<img src='JavaEE-11-Spring-Aop\d1edbf83-2c2e-4659-904e-8da5f208b97e.jpg'>

通过value指定被增强的接口，defaultImpl指定默认的增强接口的实现类。

3. 测试

<img src='JavaEE-11-Spring-Aop\1d862b1b-6241-4abd-bb44-5f557c77e431.jpg'>

## 使用xml配置Aop

### 常用的标记

<img src='JavaEE-11-Spring-Aop\377f71e0-9b09-43a0-a5f2-0b1a4e8f9849.jpg'>

### 实例

1. 定义接口

<img src='JavaEE-11-Spring-Aop\4cbe6dc1-022f-4371-ba2a-f5bd2549670a.jpg'>

2. 实现类

<img src='JavaEE-11-Spring-Aop\ab61694d-cde5-44d8-8468-434884883d70.jpg'>

3. 切面类

<img src='JavaEE-11-Spring-Aop\1c8b2103-8a95-4bc1-92f8-32c98f624326.jpg'>

4. xml配置

<img src='JavaEE-11-Spring-Aop\73229d23-27d2-41ba-aafc-1e43d57efa81.jpg'>

使用PonitCut简化

<img src='JavaEE-11-Spring-Aop\86c63023-d359-49e7-8569-fc816ec72eb5.jpg'>

### 通知传参

带参方法：

<img src='JavaEE-11-Spring-Aop\e15e5cbd-b127-4eec-aea3-00d8546b253d.jpg'>

使用args():

<img src='JavaEE-11-Spring-Aop\0c23dda2-2151-458e-aba4-2eca874ec0d8.jpg'>

### 引入

1. 为切面添加增强接口实例

2. 配置declearParents

<img src='JavaEE-11-Spring-Aop\514fc807-5600-40f1-bd2b-fc62222b4131.jpg'>

types-maching匹配待增强接口

implement-interface匹配增强接口

default-impl匹配默认实现类

## 为多个切面排序

### 使用@Order

<img src='JavaEE-11-Spring-Aop\0460c1e1-966b-4186-8099-e0926ff5f398.jpg'>

### 实现Ordered接口

<img src='JavaEE-11-Spring-Aop\dd225124-e9ad-45f6-88e1-d578cb12522f.jpg'>

### xml配置

<img src='JavaEE-11-Spring-Aop\ce181adf-5080-4876-aac4-b107dc0dab1a.jpg'>





