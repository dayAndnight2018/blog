---
title: java14 内部类
date: 2020-02-29 10:14:01
tags: java
---

## 内部类的定义

内部类就是在其它类内部的类：

<img src='java14-Nested-and-Inner-Classes\425b4d6b-c0ac-4f45-acd5-43fc21d894bc.jpg'>

如果你喜欢，可以在内部类内部再定义内部类：

<img src='java14-Nested-and-Inner-Classes\77548d4e-f647-4ec1-b0ff-12772c2c6e07.jpg'>

内部类类似于域、方法，可以有四种访问修饰符：public / private / default / protected

## 静态内部类和内部类区别

1. 静态内部类可以包含静态域，内部类不行。

2. 实例内部类可以访问外部的静态、实例域，方法，包括私有的。静态内部类仅可以访问外部的静态资源。

3. 静态内部类可以不用创建外部类，直接创建实例。实例内部类需要先创建外部类的实例。

## 静态内部类

创建静态类：

<img src='java14-Nested-and-Inner-Classes\25086175-1c78-46e0-a853-f926856d4629.jpg' >

使用其创建对象：

<img src='java14-Nested-and-Inner-Classes\b3f347ef-65f7-4c9a-a359-5442cc7ba493.jpg'>

外部类.内部类 创建对象。

## 实例内部类

<img src='java14-Nested-and-Inner-Classes\e8c232a2-322d-454b-aff6-fc045f14adfc.jpg'>

内部类创建实例：

<img src='java14-Nested-and-Inner-Classes\fa5fd1c3-2901-40f0-a476-55a4ac516e25.jpg'>

需要外部类的实例.new 内部类

## 局部内部类

<img src='java14-Nested-and-Inner-Classes\ffab32ff-27e6-4ffb-bb41-663d8afbcb01.jpg'>

在方法的内部定义内部类称为局部内部类。

布局内部类可以使用方法的参数，但是只能使用final参数：

<img src='java14-Nested-and-Inner-Classes\90a27107-e989-4239-909e-5d7b8d11fa3e.jpg'>

## 匿名内部类

创建接口：

<img src='java14-Nested-and-Inner-Classes\18bc7bef-c670-419c-ad33-f90063c79ead.jpg'>

创建接口的匿名内部类：

<img src='java14-Nested-and-Inner-Classes\46969a31-64a7-4f7f-b06c-269ef48f89a3.jpg'>

抽象类也可以：

<img src='java14-Nested-and-Inner-Classes\acd4f4f7-84c2-42db-be94-39dffe751bec.jpg'>

