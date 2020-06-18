---
title: spring06- 视图渲染
date: 2020-06-17 14:50:05
tags: spring
---

视图渲染属于视图层的任务，常用的就是Thymeleaf（JSP不建议使用）

## Thymeleaf视图解析器

1. ThymeleafViewResolver视图解析器，用于将视图名称解析为视图模板。

2. SpringTemplateEngine渲染引擎，用于渲染数据

3. TemplateResolver模板处理器，用于加载模板

### 使用代码配置

<img src='spring06-spring-web-view\664d3e62-ce19-4c2b-94fc-5fb1f9840781.jpg'>

先配置TemplateResolver，然后配置TemplateEngine，最后是ViewResolver

### 使用xml配置

<img src='spring06-spring-web-view\b0149925-3ee7-44e4-9154-5b81704ce40c.jpg'>

## Thymeleaf模板定义

### 一个简单的模板

<img src='spring06-spring-web-view\6652af90-41a8-4a2f-9ed2-c8e1976101a5.jpg'>

通过引入th前缀，对html的标签属性进行修饰，动态绑定数据。这里th修饰了href属性，用于动态绑定超链接，并使用@{}计算路由地址。

### 域绑定

<img src='spring06-spring-web-view\3ddfad59-b0d2-45aa-b22c-f0863a2c9042.jpg'>

通过th:field绑定合适的域，*{firstname}则是域对应的属性。

通过th:class条件修饰input标签，用于配置不同的css类，采用spring的表达式计算，根据结果渲染。

### 绑定域模型

通过th:object绑定模型

<img src='spring06-spring-web-view\5faef54e-7837-4c0a-9c65-24ff934f8613.jpg' >

### 条件渲染

<img src='spring06-spring-web-view\161546be-688f-4357-8357-0fd00113a588.jpg'>

通过th:if条件渲染

### 遍历集合渲染

使用th:each遍历集合渲染

<img src='spring06-spring-web-view\ef3ae15e-9275-4180-85f0-b472ee740a8d.jpg'>








