---
title: java22-lambda表达式
date: 2020-06-25 22:03:16
tags: java
---

## 一个常规问题的实现

我们定义一个通用方法实现两个int值的计算：

1. 定义接口

<img src='java22-lambda\ccee4d44-bbd3-4753-8c32-5e2074271c84.jpg'>

只有一个方法，输入两个值，返回结果。

2. 通过工厂模式实现

根据输入操作符的不同，给出接口的不同实现：

<img src='java22-lambda\5f11e389-7bbc-4a4d-9464-138299369723.jpg'>

3.  测试

先构造接口对象，再调用接口方法

<img src='java22-lambda\9d8473f0-f436-4374-9e10-6fba0008fcea.jpg'>

## 改用lambda实现

<img src='java22-lambda\c82d16f9-5de5-49a9-af93-a99699a3c90a.jpg'>

替换匿名内部类的方式是合理的。

通过lambda表达式实现的匿名内部类的简化，要求必须是函数式接口，即：此接口只能包含一个抽象方法。

## lambda的简化

### 简化参数类型

缩掉参数类型：

<img src='java22-lambda\ca17d4a0-32a7-4bd9-9204-48eb54b2e578.jpg'>

只有一个参数是，可以省略小括号(不建议)：

<img src='java22-lambda\34bed390-25cf-4e3c-8bf7-e5603f879450.jpg'>

若实现只有一句话，可以省略大括号及“return”:

<img src='java22-lambda\c4042c14-129c-45bb-bc00-f6af12812860.jpg'>

## lambda可以作为参数传递

参数是函数式接口时，可以将lambda表达式作为参数传递。

<img src='java22-lambda\2ace4eaf-8d08-4a56-b95b-7ac09845ed04.jpg'>

## lambda可以使用并修改全局变量及全局静态变量

<img src='java22-lambda\f7c0b65e-8c4c-4e1a-958c-8a77ccf0dfc3.jpg'>

## lambda可以捕获局部变量，只能读取不能修改

<img src='java22-lambda\dd850819-c2df-4273-a38e-6eb76d5a44e0.jpg'>

## ::方法引用的使用

采用与函数式接口类似的方法参数及返回类型的方法均可以代替函数式接口参数传入：

<img src='java22-lambda\0b9a0ca0-a730-455c-9665-266e68bb9c93.jpg'>

使用方法：

<img src='java22-lambda\e3face43-b305-4106-a986-018d744e8de0.jpg'>


