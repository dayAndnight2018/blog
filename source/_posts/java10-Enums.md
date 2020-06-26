---
title: java10 枚举
date: 2020-02-22 09:32:02
tags: java
---

## 枚举简介

枚举主要用于限制输入范围：

<img src='java10-Enums\bfea2293-b740-4f18-90e9-01812dca2000.jpg' >

枚举可以作为类的域变量出现：

<img src='java10-Enums\32fa17a6-e7ae-402a-82fd-87cbaf4c6e24.jpg'>

其初始化方法类似于静态变量：

<img src='java10-Enums\6c5029a4-e99a-4116-91b3-381f39a4e900.jpg'>

枚举也可以在类的内部定义：

<img src='java10-Enums\13a62aa4-cdd4-4655-9b0e-8f513647f534.jpg'>

## java.lang.Enum

1. 没有公共构造器，不能初始化变量

2. 默认静态

3. 可以调用方法进行迭代

## 构造函数初始化

<img src='java10-Enums\f98cb8ec-206e-4e32-9243-6d98b6451ed0.jpg' >

使用私有构造器初始化成员

## 迭代枚举值

可以获取枚举的values然后 使用foreach迭代：

<img src='java10-Enums\0ce8cc79-6e4a-49fa-98c5-b2fd4d2193fb.jpg'>

## Switch用法

可以使用枚举作为switch的条件：

<img src='java10-Enums\da448e44-4ab9-498c-ab8a-40b18f4152da.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>case的写法</code>一定要注意！！
