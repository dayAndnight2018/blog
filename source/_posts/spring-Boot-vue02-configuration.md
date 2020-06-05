---
title: 'spring-Boot+vue02: 基础配置'
date: 2020-05-29 13:28:05
tags: spring-boot
---

## 替换starter-parent

spring-boot-starter-parent提供了一些默认配置：

<img src='spring-Boot-vue02-configuration\fbb66fb2-134d-4e07-b054-75acb3e127f3.jpg'>

添加java版本配置：

<img src='spring-Boot-vue02-configuration\70d271db-0358-408d-88a4-02a61c07a47d.jpg'>

添加maven-compiler-plugin插件，配置源码和生成目标版本1.8

配置编码为utf-8:

<img src='spring-Boot-vue02-configuration\70788151-655a-48cf-b9e8-2f05e88d1e58.jpg'>

添加依赖管理：

<img src='spring-Boot-vue02-configuration\0ac09445-220c-49ed-89b6-fb31f21b14ee.jpg'>

## 配置Tomcat

默认使用tomcat，给出进一步配置：

<img src='spring-Boot-vue02-configuration\8b24bc04-2461-4e6e-a1b0-28e3194cc35b.jpg'>

配置https:

<img src='spring-Boot-vue02-configuration\15b3d92c-cffd-4d41-b0f6-2c61110fbdac.jpg'>

配置http到https的自动转发：

<img src='spring-Boot-vue02-configuration\3cecdc0e-4cff-49db-91a5-70f364566ac2.jpg'>
<img src='spring-Boot-vue02-configuration\195c643a-181c-4ca5-b001-874dabe43f81.jpg'>

## 配置Jetty

<img src='spring-Boot-vue02-configuration\f4436b07-b9e3-48ac-9ea6-18401bccaf96.jpg'>

在spring-boot-starter-parent中排除tomcat，添加jetty

## 配置undertow

<img src='spring-Boot-vue02-configuration\a38cfb58-4852-4bea-b092-7069473a3925.jpg'>

在spring-boot-starter-parent中排除tomcat，添加undertow

## yaml配置

采用缩进表示层级关系，支持集合：

<img src='spring-Boot-vue02-configuration\c81b43a9-6dc1-4cbf-9658-a0f96e2c3fec.jpg'>

以上等价于：

<img src='spring-Boot-vue02-configuration\dba29287-7c09-4d96-9f90-518bf9c284ef.jpg'>

支持集合：

<img src='spring-Boot-vue02-configuration\cf90c393-b14f-47be-b3d4-93eb4079913a.jpg'>

## 不同环境的配置

※使用application.propries配置：

<img src='spring-Boot-vue02-configuration\dca47b2f-6be2-4875-ad65-051066347e15.jpg'>

表示加载application-dev.propries作为配置

※使用代码在启动类中配置：

<img src='spring-Boot-vue02-configuration\5174d0da-bf14-422a-800f-d90a6b24f041.jpg'>

※可以在启动时配置：

<img src='spring-Boot-vue02-configuration\5e50d2af-659d-4f09-bc2d-c6d33d285014.jpg'>


