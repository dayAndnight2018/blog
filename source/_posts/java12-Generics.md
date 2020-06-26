---
title: java12 泛型
date: 2020-02-22 11:46:56
tags: java
---
如果不使用泛型，在List中读取数据 就需要频繁的强制转化，类型不合适还会出现异常：

<img src='java12-Generics\5fdfbb8d-8708-4ec7-92de-fc60ebf99989.jpg' >

## 泛型方法举例

泛型列表：

<img src='java12-Generics\dc8f804a-12a9-4bc2-9d1a-56ee64026ff2.jpg'>

插入和获取元素方法：

<img src='java12-Generics\1caed39d-ecf3-4ef6-8b53-770a2f38d863.jpg'>

实例化：

<img src='java12-Generics\458e0721-cc8c-4221-aad3-f40fb04983ff.jpg'>

Map:

<img src='java12-Generics\e2c8dea5-3a7a-4dbb-8c32-d595f30cf43d.jpg'>

插入、获取：

<img src='java12-Generics\d2b8a1d7-2a64-473a-908f-1c88ca35ef81.jpg'>

泛型列表嵌套：

<img src='java12-Generics\ecf519cf-be8d-4cfe-9790-1b94bb57f8e0.jpg'>

使用示例：

<img src='java12-Generics\ee20de0a-a4ef-43d5-8146-59caaf986892.jpg'>

hashMap使用示例：

<img src='java12-Generics\2720dff5-de6c-494a-8986-0158b2598f45.jpg'>

## List<?>类型通配

在List中可以传入自身的对象或者子类对象。但是List<String>传入List<Object>是无法编译的：

<img src='java12-Generics\ce5c869b-164a-449e-b43f-00976ab09a20.jpg'>

替换为List<?>即可接受任意类型的列表：

<img src='java12-Generics\eaf9d52e-fcee-4196-bd70-0305a87bac8b.jpg'>

还可以限定类型属于某类型或其子类型：

<img src='java12-Generics\8c3d32d5-cdab-44b7-9337-52c5b9007567.jpg'>

使用List<? extends Number>可以限定部分类型可用：

<img src='java12-Generics\c44e6327-6c3d-4c47-9335-d46bea9dd31c.jpg'>

## 自定义泛型类

<img src='java12-Generics\3aa8deb3-cd86-4198-b43b-6aed1d83322a.jpg'>

使用T表示泛型类型。

使用时需要指定泛型的具体类型：

<img src='java12-Generics\af41f68d-325d-4516-a044-e2f8577f7749.jpg'>

泛型类实例:

<img src='java12-Generics\c639ca42-af50-437e-8ee6-2aa5116bdf2a.jpg'>

调用：

<img src='java12-Generics\b4252769-d21b-4795-bd54-ca3c390170f9.jpg'>

## 泛型接口

接口：

<img src='java12-Generics\1227586d-9791-492b-b57b-944a050807ba.jpg'>

实现类：

<img src='java12-Generics\95c52984-08b6-42b5-9e40-bc10bdfc303d.jpg'>

## 泛型方法

<img src='java12-Generics\9ccb87e8-e59a-4306-9a05-3ccba6cad2f9.jpg'>

对泛型方法参数进行限定：

<img src='java12-Generics\822f29e0-21fc-4f1d-8357-fb1022af8efb.jpg'>

