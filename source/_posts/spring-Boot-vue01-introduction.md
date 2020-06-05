---
title: 'spring-Boot+vue01: spring boot简介'
date: 2020-05-29 12:49:12
tags: spring-boot
---

## Spring Boot 简化配置

spring boot极大简化了xml的配置，基于约定优于配置。可以打包为war，在tomcat中执行，也可以打包为jar在容器中执行，倾向于云原生开发。

<img src='spring-Boot-vue01-introduction\a1239d7d-1b8c-4571-b915-e246dcfbb846.jpg'>
<img src='spring-Boot-vue01-introduction\59de2b05-cc04-4889-9299-c05aea636539.jpg'>

## 创建一个Spring boot项目

1. 创建maven项目

<img src='spring-Boot-vue01-introduction\4caeef5e-745c-4ea3-a82f-20a5711a8dc2.jpg'>

2. 脚手架选择

<img src='spring-Boot-vue01-introduction\cfe4540a-73d3-4935-922d-eab20a9c69a4.jpg'>

3. 填写项目信息，完成创建

<img src='spring-Boot-vue01-introduction\2edd6e64-7beb-4e8f-9595-dab6d11a8512.jpg'>

## 依赖添加

1. pom.xml中添加parent节点配置

<img src='spring-Boot-vue01-introduction\303c49bc-4551-4f2f-a95b-7b0b1d331a1d.jpg'>
<img src='spring-Boot-vue01-introduction\e41304bc-eed2-4a67-bb1d-df5250bc8369.jpg'>

parent节点提供了很多starter基础配置服务。

2. 添加web依赖

<img src='spring-Boot-vue01-introduction\6196e5d4-6f22-4df3-ac83-bc31371c393b.jpg'>

dependencies是依赖包集合。

3. 创建启动类

<img src='spring-Boot-vue01-introduction\bab238ed-9ef6-4fb8-b289-8ba666cf20a6.jpg'>

EnableAutoConfiguration注解开启了spring及spring mvc的自动配置。

4. 创建测试控制器

<img src='spring-Boot-vue01-introduction\fcf5fb9e-86b5-4e3e-b042-e0b64315971a.jpg'>

5. 为启动类添加自动扫描注解

<img src='spring-Boot-vue01-introduction\4659abe6-e705-4336-b01e-060865af657a.jpg'>

EnableAutoConfiguration和ComponentScan注解可以合并为SpringBootApplication注解。

<img src='spring-Boot-vue01-introduction\a83426b9-8fc6-4f5c-a7f6-fa4bffd70485.jpg'>

## 项目启动

1. maven指令

<code style='background:#ff3385;color:white;padding:5px;'>mvn spring-boot:run</code>

2. 运行启动类

启动类包含入口方法main函数，直接运行。

3. jar包启动

添加打包插件：

<img src='spring-Boot-vue01-introduction\75ad27c7-2deb-4f89-8591-11163927d882.jpg'>

使用maven指令打包：

<code style='background:#ff3385;color:white;padding:5px;'>mvn package</code>

使用java指令运行：

<code style='background:#ff3385;color:white;padding:5px;'>java -jar xxx.jar</code>


