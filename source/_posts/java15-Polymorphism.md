---
title: java15 多态
date: 2020-02-29 11:01:58
tags: java
---

## 什么是多态？

<pre style='background:#e6e6e6;padding=10px;'>

A a = new B();

</pre>

如上所示的定义方法是允许的，条件如下：

1. B是A的子类

2. B是A接口的具体实现

有什么特别之处呢？

当<code style='background:#ff3385;color:white;padding:5px;'>编译</code>时，a的类型是A，这个时候，只允许调用在A类中定义的方法。在<code style='background:#ff3385;color:white;padding:5px;'>运行</code>时，a变成了类型B，所以，

<pre style='background:#e6e6e6;padding=10px;'>

a.getClass().getName()  //结果是B

</pre>

那么，假设A有个play方法，B重写了这个方法，调用a.play()是调的是谁？<code style='background:#ff3385;color:white;padding:5px;'>调用B的方法</code>。这个调用在运行时决定。

假如，A有个方法stop，而B<code style='background:#ff3385;color:white;padding:5px;'>没有</code>重写这个方法（B不是直接继承或实现A），那么调用a.stop(),调用的是谁？调用<code style='background:#ff3385;color:white;padding:5px;'>B的父类</code>的方法，能具体则具体，找到父类的重写方法进行调用。

## 多态的一个应用场景

假如我们有个订单服务Order,有个处理订单的接口OrderHandler

但是对于订单的处理，如：接受订单，处理订单需要不同的持久化工具，如Sql Server,MySql, Oracle等等

为了实现不同数据库的适配，需要定义不同的实现类，SqlServerOrderHandler, MySqlOrderHandler, OracleOrderHandler。

到底使用哪个呢？需要根据运行时决定。

<img src='java15-Polymorphism\d3158b32-219e-4097-8254-4afb87484899.jpg'>

或者

<img src='java15-Polymorphism\ca1ae812-cc61-456b-b753-1c14def49d84.jpg'>

通过反射，动态的根据输入参数创建实现类的实例：

<img src='java15-Polymorphism\4d6add47-fb4a-403a-a973-40c0ef0408ce.jpg'>
