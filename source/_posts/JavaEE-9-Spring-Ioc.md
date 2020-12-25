---
title: JavaEE-9-Spring-Ioc
date: 2020-06-20 19:03:43
tags: JavaEE
---

## 主动创建对象

我们假设制造果汁的过程：添加原料，使用搅拌机搅拌得到果汁。

### 搅拌机

<img src='JavaEE-9-Spring-Ioc\d93673aa-786f-470a-bc0e-d006bf0e9428.jpg' >

### 果汁制作

<img src='JavaEE-9-Spring-Ioc\9c12c902-9bbb-4587-b912-5a443fc2dfb6.jpg' >

## 被动创建对象

### 原料

<img src='JavaEE-9-Spring-Ioc\3e4f2450-9a5c-4563-8b41-f721a4f17a9e.jpg'>

### 制作果汁

<img src='JavaEE-9-Spring-Ioc\eb6e36c4-4ed4-44a1-a6a9-ce2e657bf9f6.jpg'>

### 使用xml文件描述

原料：

<img src='JavaEE-9-Spring-Ioc\4687ea60-012d-4abc-ad4c-a03f302aec52.jpg'>

果汁制作：

<img src='JavaEE-9-Spring-Ioc\21eec3f1-73c8-487b-8d90-cd980a84656a.jpg'>
<img src='JavaEE-9-Spring-Ioc\efe6f012-3468-4862-b226-c71f7fdf7055.jpg'>

## 在Spring中的实现

### 创建xml文件

<img src='JavaEE-9-Spring-Ioc\6cd06f4e-390d-458d-affa-53829fe988c7.jpg'>
<img src='JavaEE-9-Spring-Ioc\1ceae184-2dd9-49d9-834e-1ba90c0b18d9.jpg'>

### 通过ApplicationContext处理Bean

<img src='JavaEE-9-Spring-Ioc\bd440462-b0ba-4894-a884-4dca4f7ae6ab.jpg'>

## Spring Bean的生命周期

<img src='JavaEE-9-Spring-Ioc\a33f4de9-dbf6-4cfd-aef5-3b585301ceaa.jpg'>

对生命周期初始化和销毁方法进行配置：

<img src='JavaEE-9-Spring-Ioc\ea0710f0-248a-475e-922a-1e911ec7197d.jpg'>

