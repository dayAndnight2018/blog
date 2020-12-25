---
title: microservice02-Spring Boot
date: 2020-04-03 20:11:13
tags: microservice
---

## Spring Boot的优势

1. 构建独立运行的jar

2. 内嵌Servlet容器,可以直接运行

3. pom.xml依赖管理

4. 简化配置，自动化Bean

## 项目结构图

<img src='microservice02-Spring-Boot\2d18439d-8523-413f-84a9-1991a5ec49eb.jpg' style="width:480px;height:400px">

## 创建一个测试类

<img src='microservice02-Spring-Boot\333b2856-b628-4620-8726-fb402c638eb9.jpg' style="width:560px;height:240px">

RestController指明返回的是API数据而不是视图。
RequestMapping指明方法的路径

<img src='microservice02-Spring-Boot\a35d0e0d-1582-4269-bef8-31e2bb665931.jpg' >

## 集成Mybatis

### 准备数据库

在mysql中创建microservice数据库及tb_user数据表：

<img src='microservice02-Spring-Boot\a4f1b514-5fe6-4c82-98da-b2576d8a585a.jpg' style='width:480px;height:200px;'>

### 添加依赖

添加一个依赖Web模块的Spring Boot项目，并向pom.xml添加mybatis及mysql依赖：

<img src='microservice02-Spring-Boot\80eda36e-4d2b-4ffd-ba7a-d2d890c0b6af.jpg' style='width:480px;height:200px;'>

### 添加配置

追加数据库连接配置及日志配置：

<img src='microservice02-Spring-Boot\c866e517-2e97-4a46-b4ba-9f8c5e716165.jpg' style='width:480px;height:160px;'>

### 创建实体类

<img src='microservice02-Spring-Boot\9d089ead-e637-4bbf-be3f-cda626eba249.jpg'>

### 编写Mapper

通过接口及注解方法编写mapper

<img src='microservice02-Spring-Boot\020b8191-d578-44bf-9f08-cb6a696863af.jpg'>

### 编写Service接口

<img src='microservice02-Spring-Boot\615df9ee-fb60-4b06-ba50-a4f5f1f9c580.jpg'>

### 编写Service实现类

<img src='microservice02-Spring-Boot\ee3ebdd1-8b33-4204-99ff-aedd7fb100c3.jpg'>

### 编写控制器类

<img src='microservice02-Spring-Boot\00b671a4-32f4-4338-b005-db9f93eaf20d.jpg'>

### 前端页面

<img src='microservice02-Spring-Boot\06fc79b7-c41f-4111-ae35-9f3d46134e53.jpg'>

显示效果：

<img src='microservice02-Spring-Boot\04d7e7e0-f967-4659-880b-2dad442e859e.jpg'>

### 使用yml配置

也可以使用yml配置替换properties

<img src='microservice02-Spring-Boot\206d13ad-fdfe-4f83-961f-ef9d817580d1.jpg'>

## 集成Redis缓存

Redis通常作为缓存和消息代理。

### 添加依赖

<img src='microservice02-Spring-Boot\36791540-f7e4-45aa-871c-364de7bcf432.jpg' >

### 开启缓存

<img src='microservice02-Spring-Boot\6f86177f-415a-43ad-a85b-eda28a8a5523.jpg'>

<img src='microservice02-Spring-Boot\d8c0beb0-fd29-4695-9b77-ccbeb5cfe077.jpg'>

### 实体类需要可序列化

<img src='microservice02-Spring-Boot\8feffb88-d681-4cd5-8b9e-d63f16f88637.jpg'>

### 添加缓存服务器配置

<img src='microservice02-Spring-Boot\a8e9f905-7f0d-4b6b-8023-9902fba19c15.jpg'>

### 清除缓存

<img src='microservice02-Spring-Boot\2908b92b-7bf2-40f0-a01a-cbe4d8929e7a.jpg'>

## 集成ActiveMQ

spring对消息服务具有支持。

### 添加依赖

<img src='microservice02-Spring-Boot\91237d4f-c66e-4673-8dd6-fc16f5b46e9c.jpg'>

### 创建消息队列Bean

<img src='microservice02-Spring-Boot\02096089-bfd7-4128-8f94-0df6710488b8.jpg'>

### 发送消息

使用JmsMessagingTemplate发送消息。同时需要注入队列的Bean

<img src='microservice02-Spring-Boot\b0c15479-ee5e-44f8-aca2-15eddb5bf543.jpg'>

### 消费消息

JmsListener监听

<img src='microservice02-Spring-Boot\82b0b13e-54ac-47ca-9b8c-097caa91e4b4.jpg'>

### 配置远程activeMQ地址

<img src='microservice02-Spring-Boot\62dbbbe1-2524-4f79-ac11-bd0e4613d570.jpg'>

### 测试

<img src='microservice02-Spring-Boot\caa049f8-cfb2-48ee-b8a2-633cbd9dd3af.jpg'>

## Spring Boot项目打包

### Jar包

使用Maven的package命令即可打包。

运行：

<img src='microservice02-Spring-Boot\7a94f230-ffa3-4fdc-898d-0f1aa48b4a59.jpg'>

<img src='microservice02-Spring-Boot\b68b3a4d-e759-4626-a69f-cdc6e07c7da2.jpg'>

### WAR包

将tomcat配置provided:

<img src='microservice02-Spring-Boot\ffb288b1-fb0f-4719-af72-03f51ff42633.jpg'>

创建继承了SpringBootServletInitializer的子类，重写configure方法：

<img src='microservice02-Spring-Boot\cbbae934-1b67-45a2-96a7-263e73df61da.jpg'>

使用Maven的package命令即可打包。









