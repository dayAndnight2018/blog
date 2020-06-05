---
title: crazySSM05-文件上传与下载
date: 2020-06-04 22:40:12
tags: SSM
---

## 文件上传

1. 配置CommonsMutipartFileResolver

在springmvc-config.xml中配置：

<img src='crazySSM05-File\a79f9a98-b144-4f78-b255-33bf4f02beb7.jpg'>

2. 使用MutipartFile接收文件

<img src='crazySSM05-File\7979fbdf-da5a-4a54-874d-b3f49619968b.jpg'>

MultipartFile常用方法：

<img src='crazySSM05-File\dd19c720-61e3-40b9-b3e4-163b50f5147b.jpg'>

## 文件下载

给定链接点击下载：

<img src='crazySSM05-File\a914d515-eb89-4f7a-9e66-0da14493b565.jpg' >

## 拦截器

主要用于实现对控制器请求过程中的拦截，以拦截登陆为例：

1. 登陆方法

<img src='crazySSM05-File\7bb13b24-e985-4aa3-850f-125b47470876.jpg'>

2. 拦截器，实现HandlerInceptor接口

<img src='crazySSM05-File\1760f463-6f2e-47f2-9acc-2c57e0fdf509.jpg'>
<img src='crazySSM05-File\3c168eb0-e520-4f79-be06-e63deb60facf.jpg'>

在preHandle方法中，获取RequestDispatcher并进行转发。

3. 注册拦截器

<img src='crazySSM05-File\718c6703-0563-413d-a0a4-587cbf5b9dd8.jpg'>