---
title: java06 继承
date: 2020-02-21 19:25:16
tags: java
---

## 一个类与类的继承关系

<img src='java06-Inheritance\a330115e-2589-40a2-bbd3-a82cf60961db.jpg'>

一个类派生一个类，称为继承关系。原类叫<code style='background:#ff3385;color:white;padding:5px;'>父类</code>，新类叫<code style='background:#ff3385;color:white;padding:5px;'>子类</code>。

### extends

父类与子类的关系表示：

<img src='java06-Inheritance\a041167d-222e-41eb-9ef1-0dc97747e384.jpg'>

继承：

<img src='java06-Inheritance\cfd77337-4a83-4e05-b5d6-d40b1d0c4d6e.jpg'>

### is-a关系

<img src='java06-Inheritance\4a8e963b-6690-4fb9-9c3b-511f64786685.jpg'>

子类是一种特殊的父类。

父类：

<img src='java06-Inheritance\0b46928b-5862-480e-918a-dde4b9e313db.jpg'>

子类：

<img src='java06-Inheritance\2e855500-f268-4418-937d-ef0381df4091.jpg'>

子类继承父类的字段，weight和eat方法。同时扩展了numberOfLegs和walk

创建子类对象，调用继承自父类的方法：

<img src='java06-Inheritance\d4871851-89c4-4644-8f06-6ad88e8aed4c.jpg'>

父类变量可以引用子类的对象，反之不行：

<img src='java06-Inheritance\b8cd62bc-8ce9-40bc-96ec-2cdcf8a246ef.jpg'>

## 可见性

子类可以访问父类的public及protected方法，而不是private方法：

<img src='java06-Inheritance\af677728-8161-4e6b-909e-fb3bb4e5efdf.jpg'>

## 方法重写

子类可以重写父类的public及protected方法，重写就是子类对父类的相同方法的一个重新定义或者覆盖。

例如，重写toString方法：

<img src='java06-Inheritance\b177ccb3-7fca-42c8-9cfe-574f9cfa7d25.jpg'>

## 调用父类的构造器

当你调用子类的构造函数进行创建对象时，会自动调用父类的无参构造函数，直至object。

实际上，默认在子类的构造器中，调用了super():

<img src='java06-Inheritance\c222c892-9c1b-4838-af67-3ca8c18ae003.jpg'>

你也可以手动添加父类构造器调用语句，但必须在子类构造器里的第一句：

<img src='java06-Inheritance\d3ffc95b-bc01-4b34-b999-92873611d382.jpg'>

## 使用Super调用父类的域或方法

<img src='java06-Inheritance\685278cf-5b60-4dae-84f9-7960a90986e6.jpg'>

可以通过super调用父类的域或方法，前提是这些域或方法在子类可见。

## 类型转换

子类对象可以赋值给父类变量：

<img src='java06-Inheritance\22d18a8c-7195-4261-a38e-170c979128ff.jpg'>

可以对子类对象的父类引用进行向下转型：

<img src='java06-Inheritance\d05639b0-cd1e-46d1-b11d-f628c4008dbf.jpg'>

## 不可变类

对不允许继承的类可以进行扩展：

<img src='java06-Inheritance\ec286afa-b10f-4fef-95bb-0926d4b36b49.jpg'>

## instance of

可以使用instance of判断对象的类型，进而安全向下转型：

<img src='java06-Inheritance\e27c5ced-66dd-44f0-8fd0-c19683a0efe5.jpg'>

## 方法访问限定符

<img src='java06-Inheritance\98c14577-9d30-4340-acde-8cf1dd76f2b7.jpg'>



