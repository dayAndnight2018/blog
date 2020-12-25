---
title: java07 异常处理
date: 2020-02-21 20:07:52
tags: java
---

## 异常继承树

<img src='java07-Error-Handling\bee2b6a1-614e-42f0-bca1-2737cfc6accb.jpg'>

## 异常捕获

可以使用try+catch+finally捕获并处理异常：

<img src='java07-Error-Handling\585f8f5d-7c51-4c49-a420-62a2aa8a7054.jpg'>

对于parseDouble方法需要使用throws标记异常:

<img src='java07-Error-Handling\4fb5b4e1-4880-4261-9435-ba03398c7fe7.jpg'>

## 没有catch

<img src='java07-Error-Handling\f65842e4-eddf-4409-92a0-9b226bc77435.jpg'>

对于不使用catch的代码常用于释放资源，为了确保资源释放代码能够执行。

JDK7优化了这一点，使用try带上资源，表示资源释放，资源需要实现java.lang.AutoCloseable：

<img src='java07-Error-Handling\f6242861-91ae-4c88-9793-7707a8c1f144.jpg'>

例如数据库连接：

<img src='java07-Error-Handling\7c837beb-b401-4fd9-8853-7fe3f28e9aa7.jpg'>


## 捕获多个异常

使用|捕获多个异常：

<img src='java07-Error-Handling\4f7eedd1-0aa4-4c97-8b05-7c93f523735e.jpg'>

## The java.lang.Exception

toString获取异常描述：

<pre style='background:#e6e6e6;padding=10px;'>

public String toString()

</pre>

打印位置信息：

<pre style='background:#e6e6e6;padding=10px;'>

public void printStackTrace()

</pre>

## 方法抛出异常

对于代码中可能出现异常问题，要么try捕获，要么抛出异常：

<img src='java07-Error-Handling\9b7ffb4a-91f2-4962-a896-93c730199453.jpg'>

## 用户自定义异常

<img src='java07-Error-Handling\80ef8fc9-7abe-4bdd-97f5-0417bc73e4c7.jpg'>

继承自Exception，覆盖toString方法

不要过分依赖异常处理，例如空指针异常，可以先判断：

<img src='java07-Error-Handling\51f3bba5-84cf-4972-9790-c986938d59ef.jpg'>







