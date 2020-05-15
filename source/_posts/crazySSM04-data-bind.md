---
title: crazySSM04-数据绑定
date: 2020-04-23 19:08:57
tags: SSM
---

## 数据绑定流程

<img src='crazySSM04-data-bind\7cd5c153-df74-4404-9983-2339047f3fd7.jpg'>

完成数据绑定主要任务的是<code style='background:#ff3385;color:white;padding:5px;'>DataBinder</code>, 接收请求转为<code style='background:#ff3385;color:white;padding:5px;'>ServletRequest</code>对象，根据反射获取数据及处理方法的参数，通过<code style='background:#ff3385;color:white;padding:5px;'>ConversionService</code>转换数据，然后通过<code style='background:#ff3385;color:white;padding:5px;'>Validator</code>验证数据的格式，最终将数据绑定的结果保存到<code style='background:#ff3385;color:white;padding:5px;'>BindingResult</code>对象中。

## spring支持的数据转换器

### ConversionService

实现以下三种中的任意一种接口即可实现自定义的转换逻辑:

1. 将S类型的数据转为T

<img src='crazySSM04-data-bind\8a9fbc9c-92c6-4e50-ab6f-9a04088754ee.jpg'>

重写方法：

<img src='crazySSM04-data-bind\4a08d00b-a1b3-4c47-b3cc-10fc6aad60fb.jpg' >

2. 将S转为R的子类T

<img src='crazySSM04-data-bind\81c7ab52-6478-4c1e-872d-e0d9c7cb76af.jpg'>

重写方法：

<img src='crazySSM04-data-bind\b5bb6a3e-4b5d-4be6-8fe3-ba1fd7a12f8d.jpg'>

3. 基于上下文信息的转换

<img src='crazySSM04-data-bind\49673d27-6f87-4b8b-bcdf-b63b514e623f.jpg'>

重写方法：

<img src='crazySSM04-data-bind\339dbbb7-b11f-4257-8281-1cc2ae4aba2b.jpg'>

使用示例：

页面中存在生日信息，格式为xxxx-xx-xx

<img src='crazySSM04-data-bind\8f7e5ebc-024a-4084-bb3c-1da4652148af.jpg'>

POJO格式

<img src='crazySSM04-data-bind\994ce6f6-28de-4580-bd3e-042d03d56bc9.jpg'>

直接绑定数据会出错。

定义数据转换器：

<img src='crazySSM04-data-bind\3d652fd0-1239-47b5-a9a3-4726291bbf97.jpg'>
<img src='crazySSM04-data-bind\59d1b419-7549-447c-b112-380a905fd7c9.jpg'>

使用最简单的Converter<S,T>进行转换。

将定义的转换器注册到conversionServiceFactoryBean

<img src='crazySSM04-data-bind\e9d0eb90-b5a9-48e0-8df2-d45bf75135b4.jpg'>

### PropertyEditor

通过继承PropertyEditorSupport实现setAsText方法，实现数据转换。

<img src='crazySSM04-data-bind\e8476241-1baf-417a-bee1-dc49e17dddbc.jpg'>

怎么注册到框架？

1. 通过InitBind注册到控制器

<img src='crazySSM04-data-bind\24abfc74-20d9-4c59-989f-2082bdadbe7e.jpg'>

2. 全局转换器

<img src='crazySSM04-data-bind\4c4788f4-9039-42f8-b732-5ca5e2201c90.jpg'>

实现WebBindingInitializer接口，重写initBinder方法，注册转换器

3. 将全局转换器注册为Bean

<img src='crazySSM04-data-bind\343622d0-b991-403b-9bdf-65d6dccedc47.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>优先级是@InitBinder > ConversionService > WebBindingInitilizer</code>

## 数据格式化器

数据格式化其主要面向于web层的数据转化，完成的是String类型的数据与java类型数据的转换，适用范围较小，粒度小。

包含以下接口：

<img src='crazySSM04-data-bind\c97edcf0-9cca-46bc-ae75-c4c2c347f37e.jpg'>

实现方法

<img src='crazySSM04-data-bind\969a45a6-c633-4fd0-86bc-03c309592492.jpg'>

本接口实现的是T类型到String类型的转换。

<img src='crazySSM04-data-bind\8a07f701-9445-4d20-a412-53c21a7cdc78.jpg'>

实现方法

<img src='crazySSM04-data-bind\b94a1a0f-f759-459b-890c-1b08a1a3f2c7.jpg'>

本接口实现的是String到T类型的转换。

<img src='crazySSM04-data-bind\76760459-a24c-4be5-8606-50a996c5ebf4.jpg'>

继承了Printer<T>及Parser<T>接口，包含完整转换。

<img src='crazySSM04-data-bind\51657190-831f-4cab-9682-c898b9037798.jpg'>

用于注册格式化器。

<img src='crazySSM04-data-bind\2d1ccb4a-8c87-4cf1-8e00-5ed771571097.jpg'>

基于注解的格式化器

<img src='crazySSM04-data-bind\f50be5b1-b24d-4d58-8f33-f3a2c5aaa0ee.jpg'>

使用示例：

<img src='crazySSM04-data-bind\9f7e5ada-5662-453c-92eb-43ce91ad5ec2.jpg'>

注册到Bean

<img src='crazySSM04-data-bind\be39150e-7c75-4499-8914-bab45f79827a.jpg'>

这个FormattingConversionServiceFactoryBean包含一个converters和一个formatters属性，可以接受转换器和格式化器。

也可以通过FormatterRegister接口实现格式化器注册：

<img src='crazySSM04-data-bind\8246fbed-8ef5-45db-b885-c1f72e5909d4.jpg'>

注册到Bean

<img src='crazySSM04-data-bind\b8155d37-07a0-40c4-b402-f6d464012643.jpg'>

### 基于注解的格式化器

<img src='crazySSM04-data-bind\c35139cc-19f2-42fa-9e9a-f75e006fbb21.jpg'>

## 数据验证

数据验证包含格式，合法性等验证。

### Validator

示例：

POJO

<img src='crazySSM04-data-bind\76a9655a-9010-41b3-bbab-51aa03c1bc9b.jpg'>

验证器

<img src='crazySSM04-data-bind\168e8598-d3e8-46d3-8c8f-5f5e8d0922a4.jpg'>
<img src='crazySSM04-data-bind\d630dc57-5bf3-4052-ae5e-6a429918e2e7.jpg'>

控制器

<img src='crazySSM04-data-bind\19c79e1e-b748-4222-8301-a4634e381491.jpg'>

### JSR 303（常用）

<img src='crazySSM04-data-bind\6e92aa55-4def-4610-8741-f1854d4a6720.jpg'>
<img src='crazySSM04-data-bind\739db0a0-b1af-4a23-821b-55858787d4fe.jpg'>
<img src='crazySSM04-data-bind\f17ca3bc-076c-4a3e-9ef2-da059e997c06.jpg'>

使用示例：

<img src='crazySSM04-data-bind\5c0eef67-3e49-40db-b8ad-fa97b7277195.jpg'>

验证数据

<img src='crazySSM04-data-bind\d92e75c7-db7e-44c8-832f-f182cd779e2e.jpg'>


















