---
title: java09 接口与抽象类
date: 2020-02-22 08:56:44
tags: java
---

## 接口的概念

接口就是定义的一组规范，例如，电脑打印机功能，提供了一组接口：

<img src='java09-Interfaces-and-Abstract-Classes\f52cc5bf-434d-433a-9ec2-8a0c6c403667.jpg'>

不同厂家可以根据接口规范给出不同的实现：

<img src='java09-Interfaces-and-Abstract-Classes\5388d7b6-be64-4ca2-b3c0-c2182bc23b79.jpg'>

## 接口的定义

接口的定义与类类似：

<code style='background:#ff3385;color:white;padding:5px;'>访问权限符</code>+<code style='background:#ff3385;color:white;padding:5px;'>interface</code>+<code style='background:#ff3385;color:white;padding:5px;'>名称</code>

<img src='java09-Interfaces-and-Abstract-Classes\8777d801-d4ad-42bb-a83b-5090cb33bf73.jpg'>

可以给接口定义域或者方法，但默认都是public的。

接口可以被具体类实现：

<img src='java09-Interfaces-and-Abstract-Classes\52e93f8f-66c0-4112-b42a-600513ee50f9.jpg'>

接口的实现使用关键字<code style='background:#ff3385;color:white;padding:5px;'>implements</code>，同时一个类可以实现<code style='background:#ff3385;color:white;padding:5px;'>多个</code>接口（但只能继承<code style='background:#ff3385;color:white;padding:5px;'>一个</code>类）。实现类必须实现接口的<code style='background:#ff3385;color:white;padding:5px;'>全部方法</code>。

接口不能初始化，可以初始化它的实现类。同时接口和实现类之间也是is-a关系：

<img src='java09-Interfaces-and-Abstract-Classes\96a96bab-ac76-423d-851c-75f514ccd164.jpg'>

接口也可以继承：

<img src='java09-Interfaces-and-Abstract-Classes\3d0a4988-994f-4b68-b2be-902b335b7903.jpg'>

## 接口的域

接口的域默认是public / static / final，即<code style='background:#ff3385;color:white;padding:5px;'>公共静态常量</code>。以下几种定义方式等价：

<img src='java09-Interfaces-and-Abstract-Classes\9f6beb88-c67f-47d8-86df-60742f6b4950.jpg'>

## 接口的方法

接口方法默认是public / abstract的，即<code style='background:#ff3385;color:white;padding:5px;'>公开抽象</code>方法，<code style='background:#ff3385;color:white;padding:5px;'>没有方法体</code>。

<img src='java09-Interfaces-and-Abstract-Classes\30d23729-df67-437d-9480-5ec35c9b5b57.jpg'>

## Base Class

什么是base class?当我们定义了一个接口，这个接口定义了很多方法的时候，实现类需要实现全部方法，但是很多时候带有很多重复代码，因为没必要。因此，我们定义一个实现类实现这个接口，给出默认的实现方法。再由具体的类继承这个类去重写所需的方法，这个类就叫base class.

在Servlet中，实现接口：

<img src='java09-Interfaces-and-Abstract-Classes\4b55316e-3417-4b88-b97e-0759b7668159.jpg'>

继承base类：

<img src='java09-Interfaces-and-Abstract-Classes\51216969-671e-4f4f-969f-076dc0ad0581.jpg'>

相比之下，还是继承类更简单。

## 抽象类

抽象类与接口类似，但是对于抽象类的方法，可以定义必须重写的方法，也可以定义不需要重写的一般方法：

<img src='java09-Interfaces-and-Abstract-Classes\686a391c-56cf-4053-b0ad-e4e6d4ac0415.jpg'>

在实现类中，只需要实现抽象方法即可：

<img src='java09-Interfaces-and-Abstract-Classes\fcff07e4-264a-4072-a7c9-09ef174822c0.jpg'>

抽象类的实现类必须实现全部抽象方法，否则它也是一个抽象类。

抽象类用斜体表示：

<img src='java09-Interfaces-and-Abstract-Classes\3ff522fa-1c83-434b-9ed4-1035cc6c62c3.jpg'>









