---
title: java01 准备工作
date: 2020-02-16 18:28:29
tags: java
---

## 一次编写代码，到处运行。

java代码是跨平台的，其实现跨平台的方式通过不同的平台上的虚拟机实现的。

<img src='java01-preparement\7754be56-0683-4562-9d97-51799af7e589.jpg' >

## 第一行java代码

<pre style='background:#e6e6e6;padding=10px;'>

class MyFirstJava{
    public static void main(String[] args){
        System.out.println("Hello Java!");
    }
}

</pre>

注意，类名和文件要一致，文件扩展名必须是java

## 编译你的代码

1. 在MyFirstJava.java文件所在的目录打开控制台

2. 执行命令 <code style='background:#ff3385;color:white;padding:5px;'>javac MyFirstJava.java</code>

执行成功后，在相同的目录下会生成类文件：MyFirstJava.class

## 运行你的代码

1. 在MyFirstJava.class文件所在的目录打开控制台

2. 执行命令 <code style='background:#ff3385;color:white;padding:5px;'>java MyFirstJava</code>

执行成功后控制台输出Hello java

当然，你也可以带着参数运行程序：

<img src='java01-preparement\2d2fb8f9-8791-45b8-963a-fef5036d7cde.jpg' >

arg-1代表第一个参数，arg-2代表第二个参数

## 挑选一个你喜欢的IDE吧

<img src='java01-preparement\2dc63515-6af4-4fe1-86ef-904216a7743d.jpg'>

红色框选是常用的几个。
