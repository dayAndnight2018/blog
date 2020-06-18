---
title: spring01 简介
date: 2020-03-01 12:12:14
tags: spring
---

## JavaBean

在spring中，都是一个个组件，这些组件我们可以称为<code style='background:#ff3385;color:white;padding:5px;'>Bean</code>，这些Bean由Spring来维护，你只需要提供业务功能。

<img src='spring01-introduction\9572c008-6497-483a-8ef9-19252bcdaa3d.jpg'>

这样一个<code style='background:#ff3385;color:white;padding:5px;'>POJO</code>就是一个Bean。

## 依赖注入

以往的代码中，我们需要<code style='background:#ff3385;color:white;padding:5px;'>主动</code>new一个对象，用来产生类的实例：

<img src='spring01-introduction\755e218b-fdf8-48b6-9fc6-4b3b57b8bf7a.jpg'>

依赖注入避免了这样的操作，spring负责为你管理，为你new对象，你要做的只是告诉他，<code style='background:#ff3385;color:white;padding:5px;'>我需要xxx</code>

<img src='spring01-introduction\6ffc1bc2-1fa6-4e66-b9bf-487b5090930e.jpg'>

这样，所有的依赖对象，都可以交给spring去new,如果设定为接口，可以实现抽插式<code>替换</code>。

<img src='spring01-introduction\d5a98ccf-5a4d-476a-a1a3-3f797a76c768.jpg'>

## 怎么告诉spring，你需要什么？

1. xml配置

通过xml配置文件，将一个个Bean注册给spring，Spring知道都有哪些Bean，与此同时，也要试图告诉spring，谁需要什么：

<img src='spring01-introduction\638d6418-d4e8-4d9b-b900-419fb1a2d6c4.jpg'>

2. java Config

<img src='spring01-introduction\68bc637f-9a6a-4d46-b4a0-be22621adc6f.jpg'>

通过注解，告诉spring，这个是一个配置类，里面的Bean你都要注册。

## 怎么获取我想要用的Bean？

<img src='spring01-introduction\94005c3b-7b17-45dd-81a4-2d991f33997d.jpg'>

创建Application Context的对象，通过它获取Bean的实例。

通过Class<?> getBean(Class class)获取相关的Bean对象。

然后就可以对实例进行任何操作了。

## 什么是AOP?

为了彻底让<code style='background:#ff3385;color:white;padding:5px;'>业务和组件分离</code>，让业务无需关注组件的额外操作，AOP出现了。

例如我们想要在某个方法执行前，打印一下，在他执行后，打印一下。

<img src='spring01-introduction\e20a5887-3322-42d6-b07d-a6f719b2645f.jpg'>

一种，我们可以<code style='background:#ff3385;color:white;padding:5px;'>显式地</code>在调用方法<code style='background:#ff3385;color:white;padding:5px;'>前后</code>分别打印：

<img src='spring01-introduction\428a29b9-4dfa-43a2-a7fa-1d8b58e6bf6a.jpg'>

这样的化，业务需要关注很多不必要的东西，比如打印这件事。避免业务代码显式地调用这样的功能组件，我们可以采取另外的思路（以xml配置为例）：

1. 我们先把打印组件注册到spring

<img src='spring01-introduction\a51f5a74-ecb5-48d5-a6c4-c8ecb48a804e.jpg'>

2. 有了打印功能，我们创建切面

<img src='spring01-introduction\b15b18e9-891d-4364-b602-194bebc9cf6c.jpg'>

切面就是<code style='background:#ff3385;color:white;padding:5px;'>组件功能</code>。

切点就是被<code style='background:#ff3385;color:white;padding:5px;'>监视</code>的那个方法。

在方法执行前，执行<code style='background:#ff3385;color:white;padding:5px;'>before</code>代码

在方法执行后，执行<code style='background:#ff3385;color:white;padding:5px;'>after</code>代码

这样，业务并不需要知道组件的存在，而组件的功能也得以实现。


## 消除样板代码

我们先来看一部分JDBC使用的代码：

<img src='spring01-introduction\1926b27d-4ed3-4f26-9380-ee63d8b405a4.jpg'>

眼花缭乱不是吗？真正有用的代码有多少？很少。

JDBCTemplate为我们简化了这些代码：

<img src='spring01-introduction\52fa307d-d699-4252-b32f-b62cb470830c.jpg' >

我们只需要关心如何处理表和对象的映射。

## Application Context的几种实现

AnnotationConfigApplicationContext：从一个或多个基于Java的配置类中加载Spring应用上下文

AnnotationConfigWebApplicationContext：从一个或多个基于Java的配置类中加载Spring Web应用上下文

ClassPathXmlApplicationContext：从类路径下的一个或多个XML配置文件中加载上下文定义，把应用上下文的定义文件作为类资源。

FileSystemXmlapplicationcontext：从文件系统下的一个或多个XML配置文件中加载上下文定义。

XmlWebApplicationContext：从Web应用下的一个或多个XML配置文件中加载上下文定义。

使用示例：

从文件系统的某个xml文件中注册Bean:

<img src='spring01-introduction\65c6c9fc-c146-48e1-b0bd-24a6cc080a65.jpg'>

从ClassPath读取xml注册Bean：

<img src='spring01-introduction\3e0952b6-f552-49a4-ae42-03dddab31f7a.jpg'>

JavaBeanconfig文件中注册Bean：

<img src='spring01-introduction\f2cf5d4b-7bcf-4b3e-ac3c-2a143b70ef86.jpg'>

## Spring组成部分

<img src='spring01-introduction\4acb1a26-3aa3-43ef-8b60-3bf5d88fb4c3.jpg'>





