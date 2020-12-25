---
title: springBoot2-13-rest
date: 2020-07-09 10:34:23
tags: spring-boot-2
---

Rest是一种设计风格。

## 常用的几种动作方法

<img src='springBoot2-13-rest\8f07a60d-2cc7-4c5a-924f-f2d6c8f861c9.jpg'>

<img src='springBoot2-13-rest\060e7cca-6936-46b0-b814-fd63265c8e0d.jpg'>

## Spring中的Rest

### 几种映射方法

<img src='springBoot2-13-rest\82ace12b-d0d2-4486-8910-6de6e9d85df8.jpg'>

### Spring的rest端点

1. get

<img src='springBoot2-13-rest\ba5704f8-d1f1-4f20-bfc5-2a9dd64fd69e.jpg'>

2. post（来自body）

<img src='springBoot2-13-rest\70618c03-f91d-4bbb-b549-9bb3b498fee4.jpg'>

3. url参数绑定

<img src='springBoot2-13-rest\b78993f7-630e-42b1-9587-6218883e6b8e.jpg'>

多个参数：

<img src='springBoot2-13-rest\5d431ac0-1b61-4c14-9694-bfdc48d93d33.jpg'>

4. put 混合url参数及请求体

<img src='springBoot2-13-rest\98349ed2-1256-4374-a511-d45c7059fc0d.jpg'>

5. patch

<img src='springBoot2-13-rest\c5474e7b-d306-46a4-9d28-a8c81d088962.jpg'>

6. delete

<img src='springBoot2-13-rest\7cf17a85-9c60-49dd-ad1d-e3e2eacc62a1.jpg'>

7. rest方法和视图方法的区别

<img src='springBoot2-13-rest\5ebc054d-93c5-4337-9edc-539844504419.jpg'>

## 使用RestController默认使用Rest返回json数据

<img src='springBoot2-13-rest\09846f02-4c8e-46fb-958d-f2c79cc1304e.jpg'>

避免了方法单独使用@ResponseBody的麻烦

## 设定响应的状态码及其他信息

可以使用ResponseEntity<?>来细致地返回相关信息。

@ResponseStatus可以指定状态码

<img src='springBoot2-13-rest\b0dbf6a0-510d-487c-97e4-016443fdba55.jpg'>

## 使用ControllerAdvice处理异常

<img src='springBoot2-13-rest\7cc3c9dd-7390-4691-b088-128d546753bd.jpg'>

指定包和拦截类型

@ExceptionHandler指定异常类型

## 使用RestTemplate请求服务

1. 简单地get

<img src='springBoot2-13-rest\a03a6ffa-c821-4b38-8685-86580626f75d.jpg'>

getForObject(String url, class result, object ... params)

2. 多个参数，获取数组

<img src='springBoot2-13-rest\db6b2e58-2006-46e0-90cd-5ddd77bff38e.jpg'>

使用HashMap封装参数

getForEntity(String url, class result, HashMap<String, object> params)

获取到一个ResponseEntity实例，并使用getBody()获取结果。

3. 提交数据

<img src='springBoot2-13-rest\0ff1caf3-2526-4552-80e2-41c0e15c7173.jpg'>

使用HttpEntity封装请求数据及请求头

HttpEntity<class>(object data, HttpHeaders header);

postForObject(String url, HttpEntity<class> request, class result)

4. delete

<img src='springBoot2-13-rest\2c403bd9-a6d5-4dc5-b3d5-9416b33f7d51.jpg'>

## 获取状态码及请求头信息

<img src='springBoot2-13-rest\6098beb1-d354-4a5a-a0eb-7023a133033d.jpg'>
<img src='springBoot2-13-rest\5cce85b7-cf0c-4297-8e3c-d986a6f2dab7.jpg'>

根据ResponseEntity获取相关信息：请求头、状态码

## 使用灵活地exchange

<img src='springBoot2-13-rest\6fbc3eb6-69db-445b-a021-6218453c8195.jpg'>

exchange(String url, HttpMethod method, HttpEntity<?> data, Class result, object... params)


