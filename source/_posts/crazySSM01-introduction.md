---
title: crazySSM01-简介
date: 2020-04-07 20:01:49
tags: SSM
---

## JavaEE应用分层

Domain Objects: 领域对象层，由POJO组成。

DAO: 数据操作层， 对数据库进行CURD。（JDBC、Mybatis、Hibernate）

Service: 服务层，调用DAO层实现相关的业务逻辑。

Controller: 控制器层，接受请求，调用服务层处理并返回视图层。（Spring MVC）

View: 视图层，用于数据显示。（JSP、Velocity、FreeMaker、Thymeleaf）

<img src='crazySSM01-introduction\8f7fea39-3a82-43e6-bfe5-84c780b7da33.jpg' style="width: 480px;height: 360px;">


## 安装及准备

1.下载安装spring

[spring下载链接](http://repo.springsource.org/libs-release-local/)  下载spring压缩包。

解压后，获得四个部分：

* docs: 相关文档
* libs: 类库
* schemas: 配置文件头
* readme、notice、license等文档

将class文件复制到项目，并添加到类加载路径。

2.下载安装common-logging

[common-logging下载地址](http://commons.apache.org)

下载解压后得到common-logging的jar包，复制到项目并添加到类加载路径

<img src='crazySSM01-introduction\fa981f70-fd7e-420b-b30f-13c23d1e2f29.jpg'>

3. 配置前端控制器

在WEB-INF下的web.xml文件中，配置前端控制器。

<img src='crazySSM01-introduction\3345209b-222b-4642-a0c0-80ef42ef8327.jpg'>

这里加载的配置文件，为了生成ApplicationContext，对Bean进行管理，对于web项目会自动加载并生成，java项目需要手动读取配置文件生成ApplicationContext实例。

4. 配置文件springmvc-config.xml

<img src='crazySSM01-introduction\234f5337-0af6-49b8-876f-255141bbbe53.jpg'>

5. 添加测试

使用@Controller注解

<img src='crazySSM01-introduction\e6d076d2-f971-4dc9-b702-7211087bc11b.jpg'>

6. 测试结果

<img src='crazySSM01-introduction\ff5b1062-4a4f-47c0-b8cc-05678d674e84.jpg'>



















