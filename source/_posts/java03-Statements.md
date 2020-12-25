---
title: java03 语句
date: 2020-02-18 20:09:37
tags: java
---

## 表达式和语句的区别

1. 一个显著的区别就是有没有“;”

2. 表达式是一个式子,语句是一个完整的操作


## if语句

if是一种分支结构：

<img src='java03-Statements\8774e518-46de-4ae1-966b-5794f513017d.jpg' >

if条件成立则执行，不成立则执行else或不执行。

可以包含多个else if :

<img src='java03-Statements\059f7254-4e18-40a8-86b7-03f75ce7ee36.jpg'>

对于布尔类型的表达式，不需要使用==判断，直接使用：

<img src='java03-Statements\48ef7620-0fb8-48a7-9834-8b70214e64d3.jpg' >

## while语句

while语句是一种循环语句，重复执行指定的代码：

<img src='java03-Statements\070b6e2a-2d49-4d2b-8b8a-cbe9b6735d56.jpg'>

也可以使用break在指定条件下退出循环：

<img src='java03-Statements\6d380d56-33f8-4e35-aee0-de7b699b5cc1.jpg' >

## do...while语句

一种特殊的while循环，先执行一次循环，再做判断：

<img src='java03-Statements\b7df12e7-5fa6-4623-a108-0801a00b1919.jpg' >

## for循环

指定次数的循环语句:

<img src='java03-Statements\ad0c818a-5e6f-40e7-a338-2b53e25aae1e.jpg' >

for语句也可以使用break退出循环：

<img src='java03-Statements\5882a9cd-5734-422f-ae83-846e18a607a9.jpg'>

continue将停止本轮循环，进行下一轮:

<img src='java03-Statements\7efcef65-fc79-485e-b76f-fd00c8dc7364.jpg' >

增强foreach循环

<img src='java03-Statements\db2f1d92-c008-47a7-95c7-ea30b628a380.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>注意增强for内部内容只读，赋值是无效的，内容不变。</code>

<img src='java03-Statements\a92b0c51-e7f4-4227-84da-52e72daf1abb.jpg'>

多维数组的遍历

<img src='java03-Statements\48b17671-cd52-45d6-aa96-5f55fb2941fc.jpg'>

## switch语句

switch语句用于解决多个else if的繁琐问题，其条件可以是int/String/Enum类型：

<img src='java03-Statements\eaeacef4-ca86-4816-a6f8-03e1a9869aea.jpg' >

忘记使用break,将会导致多个case依次得到执行。




