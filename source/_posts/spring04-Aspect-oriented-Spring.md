---
title: spring04 面向切面的Spring
date: 2020-03-02 18:18:27
tags: spring
---
## 几个定义

<code style='background:#ff3385;color:white;padding:5px;'>切面</code>：用于提供额外功能的中间件叫做切面。

<code style='background:#ff3385;color:white;padding:5px;'>通知</code>：切面执行的方法叫通知。

<img src='spring04-Aspect-oriented-Spring\c64b7c74-85e6-42d4-97f8-e7b6a5cd8b65.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>连接点</code>：连接点就是通知切入的一些时机。

<code style='background:#ff3385;color:white;padding:5px;'>切点</code>：切点就是不同的织入的方法。

<code style='background:#ff3385;color:white;padding:5px;'>切面</code>：切面就是切点和通知的集合。

<code style='background:#ff3385;color:white;padding:5px;'>引入</code>：对现有类的方法或属性进行扩展。无需改动现有的类，而添加额外的功能。

<code style='background:#ff3385;color:white;padding:5px;'>织入</code>：切面植入到切点生成代理的过程。

## 注意

Spring AOP是基于动态代理实现的，只适用于方法而不是字段和构造器。若使用字段和构造器切入，可以使用AspectJ

## 切点的定义

Spring Aop借助于AspectJ的注解创建切点：

<img src='spring04-Aspect-oriented-Spring\7385c942-3ba5-43fd-ba75-6e4e545a63c1.jpg'>

定义一个业务功能点接口

<img src='spring04-Aspect-oriented-Spring\f926f52e-8ddd-41a0-9cbc-c83bfde15f28.jpg'>

构建注解匹配方法：

<img src='spring04-Aspect-oriented-Spring\d4678178-4bed-44a5-83cc-1e53fc2c76ae.jpg'>

如果需要限定包名：

<img src='spring04-Aspect-oriented-Spring\56011dbe-8bdc-4a03-97a4-041f8aa1f89a.jpg'>

如果限定Bean的名称：

<img src='spring04-Aspect-oriented-Spring\887ef2e3-11b3-4a2a-b1c3-8a4681f45b81.jpg'>

排除法：

<img src='spring04-Aspect-oriented-Spring\1b322723-f1d8-419e-a23a-6e2fe2e31087.jpg'>

## 切面的定义

使用AspectJ的一些标记进行切面的定义，所谓切面就是监听到切点方法执行的时候，所执行的嵌入的代码。

<img src='spring04-Aspect-oriented-Spring\cbed781f-3322-4b51-8543-2f91dc69cd98.jpg'>

首先使用@Aspect标记了切面类，然后分别使用不同的注解表名不同方法执行的时机。

<img src='spring04-Aspect-oriented-Spring\bc95ae3b-6e8e-4ebd-9bea-d7ba365bc4c2.jpg'>

可以使用Pointcut进行切点引用，并实现切点的复用：

<img src='spring04-Aspect-oriented-Spring\e3ff83ab-2ea0-431d-8fbf-f9aaf68463f6.jpg'>

将切面配置为Bean，并设置开启AspectJ自动代理：

<img src='spring04-Aspect-oriented-Spring\7d19c545-4d73-4e5a-a784-9e4f308443df.jpg'>

也可以使用xml配置aop:aspectj-autoproxy开启：

<img src='spring04-Aspect-oriented-Spring\88360916-71af-4e63-8e08-103d49e06832.jpg'>

## 环绕代码

<img src='spring04-Aspect-oriented-Spring\8680967a-1c74-425c-9f72-ba14e0534cd1.jpg'>

需要一个PRoceedingJoinPoint参数，用来调用方法proceed方法执行切点方法。

传参数：

当方法有参数时候，怎么截取参数传递到切面呢？

<img src='spring04-Aspect-oriented-Spring\7c1466a4-1c94-49a4-adb8-8d73b9e78686.jpg'>

此处出现两个变动：

1. pointcut体现参数类型

2. 使用args()拦截参数

<img src='spring04-Aspect-oriented-Spring\9f93f4ae-7070-4666-bece-ad4550c6e42b.jpg'>

切入点定义时，设置的参数名称要与切面方法参数保持一致。

## 引入

我们想在Performance的基础上实现另外的接口方法：

<img src='spring04-Aspect-oriented-Spring\56c7f07e-7e22-4443-8476-10a454496ba0.jpg' >

但是源码我们没法修改，怎么引入这个新的接口方法呢？

创建新的切面

<img src='spring04-Aspect-oriented-Spring\beb218e8-3c8d-4f54-8b1e-2bb11cd672fd.jpg'>

在内部声明一个静态的接口变量引用。并使用DeclareParents注解进行标记。

value属性指定了哪种类型的<code style='background:#ff3385;color:white;padding:5px;'>bean要引入</code>该接口。在本例中，也就是所有实现Performance的类型。（标记符后面的加号表示是Performance的所有<code style='background:#ff3385;color:white;padding:5px;'>子类型</code>，而不是Performance本身。）

defaultImpl属性指定了为引入功能<code style='background:#ff3385;color:white;padding:5px;'>提供实现的类</code>。在这里，我们指定的是DefaultEncoreable提供实现。

@DeclareParents注解所标注的静态属性指明了<code style='background:#ff3385;color:white;padding:5px;'>要引入了接口</code>。在这里，我们所引入的是Encoreable接口。

这样，所以实现了Performance接口的子类，都多出来了Encoreable接口的方法。

## 使用xml配置切面

### 切面所涉及的标签

<img src='spring04-Aspect-oriented-Spring\d939a402-47fa-4fd0-91e1-fb7400f0b1e7.jpg'>

接上文：

<img src='spring04-Aspect-oriented-Spring\e21999cb-2e6b-420f-8bb8-dfd824502c00.jpg'>

### 重写切面POJO类

<img src='spring04-Aspect-oriented-Spring\a9cbc369-23f6-4daa-9779-d8a4520cc8e9.jpg'>

<img src='spring04-Aspect-oriented-Spring\fe6c3d7f-e5ca-4236-9cb1-a32a7c2e868f.jpg'>

aop:config代表一个切面配置

aop:aspect表示切面

aop:before前置通知

aop:after-returning成功执行

aop:after-throwing抛出异常执行

同样，我们可以使用aop:pointcut复用连接点方法：

<img src='spring04-Aspect-oriented-Spring\c9b9c3d0-97b5-4fc3-af71-0975aa34ad70.jpg'>

在xml中配置参数传递是一样的：

<img src='spring04-Aspect-oriented-Spring\7ca5de4b-6e04-462c-bec0-7aa8e6f8173d.jpg'>

### xml引入的实现

<img src='spring04-Aspect-oriented-Spring\0bf7c997-57cf-4c0f-b781-c06457138d1b.jpg'>

types-matching指明<code style='background:#ff3385;color:white;padding:5px;'>连接点方法</code>

implement-interface指明<code style='background:#ff3385;color:white;padding:5px;'>扩展接口</code>

default-impl指明<code style='background:#ff3385;color:white;padding:5px;'>默认实现类</code>

也可以使用delegate-ref指明默认实现的bean

<img src='spring04-Aspect-oriented-Spring\21f64518-e009-4e51-a043-0fcd7a880087.jpg'>

引用的bean(实现类):

<img src='spring04-Aspect-oriented-Spring\f7ed6ef4-8fc4-4470-9764-4ab537a56fe1.jpg'>


















