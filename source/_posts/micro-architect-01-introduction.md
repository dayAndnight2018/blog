---
title: micro-architect-01-微服务简介
date: 2020-06-23 19:25:44
tags: microservice
---

## 什么是微服务

<code style='background:#ff3385;color:white;padding:5px;'>微服务</code>就是将功能模块进行拆分，各部分独立编译、部署，作为独立的功能模块对外提供服务，各部分之间 相互配合共同构成系统的整体。

微服务各模块之间采用RPC或HTTP进行通信。

## 微服务与垂直架构的对比

<table cellpadding='8' border='1' style='background:#EAF2D3;text-align:center'>
<thead>
&nbsp;<tr>
&nbsp;&nbsp;<td>
层面/架构
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
单体垂直结构
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
微服务
&nbsp;&nbsp;</td>
&nbsp;</tr>
</thead>
&nbsp;<tr>
&nbsp;&nbsp;<td>
代码维护
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
代码集中，维护不便
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
分模块开发，维护方便
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
部署
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
整体编译、部署
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
分模块编译部署，模块之间互不影响
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
资源控制
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
采用横向扩展，部署集群，反向代理进行负载均衡
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
仅对需求高的模块进行扩展即可
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
稳定性
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
单个模块出现问题，整个应用会受影响
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
一般单个模块不会影响整个应用的运行。
&nbsp;&nbsp;</td>
&nbsp;</tr>
</table>

## 一个简单的微服务框架

<img src='micro-architect-01-introduction\d16e22fd-1c3f-4bbc-ad2a-b245a043cfd2.jpg'>

客户端发起请求，将请求内容<code style='background:#ff3385;color:white;padding:5px;'>序列化</code>后经网络发送至服务端，服务端接收请求后<code style='background:#ff3385;color:white;padding:5px;'>反序列化</code>并执行相关的服务调用，将结果<code style='background:#ff3385;color:white;padding:5px;'>序列化</code>后经网络返回客户端。

### 1. 基于接口约定服务端与客户端之间的接口调用

这里使用Maven技术构建jar包：

<img src='micro-architect-01-introduction\b59e8cd3-fe8d-416a-95fa-e9e4cddc2547.jpg'>

通过接口约定服务方法：

<img src='micro-architect-01-introduction\62700d0f-683b-49ce-a8ed-1e8bd2afbf5d.jpg'>

### 2. 服务端设计

通过Maven构建服务端：

<img src='micro-architect-01-introduction\42b0446b-3fd6-421e-87a6-3af7e09ed005.jpg'>

引入刚才约定的服务接口项目jar包：

<img src='micro-architect-01-introduction\4373b5fa-a3cf-4617-aa52-7baccdca7265.jpg'>

实现约定的服务接口：

<img src='micro-architect-01-introduction\52347422-a865-4df1-bf8e-878f9925611f.jpg'>

服务管理类：

<img src='micro-architect-01-introduction\d082814a-d249-4165-a578-7b07c3726fb6.jpg'>
<img src='micro-architect-01-introduction\df894cae-7c43-4a8c-b34e-2e74eca1c463.jpg'>
<img src='micro-architect-01-introduction\6b0c5191-aa4f-4a61-bfb2-0431b5c12a17.jpg' >

基本流程如下：

1. 提供register方法便于注册服务。

2. 通过start方法开启服务端Socket, 等待客户端连接，接收连接后，获取服务调用的接口名、方法名、参数类型、参数列表

3. 通过服务映射表获取服务实现类

4. 通过反射获取指定方法名、指定参数类型的方法

5. 调用方法，获取结果

6. 将结果序列化后返回Socket


注册服务，启动服务端：

<img src='micro-architect-01-introduction\867bab5a-8759-43c6-a24e-4a145e5e7059.jpg'>

### 3. 客户端设计

创建Maven项目：

<img src='micro-architect-01-introduction\0eae3730-a2cb-4718-9d3f-b722a4965339.jpg'>

引入接口jar包：

<img src='micro-architect-01-introduction\164f5409-67a0-4bb4-86ef-2d71d2fcb9c9.jpg'>

创建服务调用类：

<img src='micro-architect-01-introduction\c4aa479c-93d9-4da1-970c-0606483da0f9.jpg'>
<img src='micro-architect-01-introduction\c3880f5d-eb80-4e75-ba7c-8bcc58d3d8cd.jpg'>
<img src='micro-architect-01-introduction\40c8ce28-1e50-4385-9adb-836fbcb00296.jpg'>

基本流程如下：

1. 基于给定的接口和远程服务Socket地址，构建反向代理

2. 创建客户端接口连接服务端，将接口名称、方法名称、参数类型、参数序列化后发送给服务端，并接收服务端返回的结果。

3. 返回结果。

调用测试：

<img src='micro-architect-01-introduction\dbc80ab4-729e-4c91-ade8-a81457c9f79c.jpg'>

## 服务框架介绍

### Dubbo(RPC)

<img src='micro-architect-01-introduction\f7c5f813-8893-4f0a-b9c6-cf104ae2a95e.jpg'>

<img src='micro-architect-01-introduction\51ba9d14-9386-46c2-b204-a01ffeb14272.jpg'>

### Spring Cloud(HTTP)

<img src='micro-architect-01-introduction\35a5057c-63ae-4928-8de3-9cd6500756dd.jpg'>

Eureka：提供服务注册与发现，负载均衡功能。

Hystrix：提供服务熔断机制，服务不可用时及时响应。

Zuul：提供动态路由、监控、弹性服务。

Config Server：配置文件管理

Spring Boot：便捷式开发




