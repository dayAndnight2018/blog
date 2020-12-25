---
title: Spring MVC03 详解Spring MVC
date: 2020-01-06 11:42:19
tags: spring mvc
---

## 详解Spring MVC

### DispatcherServlet

DispatcherServlet读取请求，找到合适的控制器方法提供服务调用。将特定的URL映射到特定的控制器的方法叫做路由映射。可以使用@RequestMapping注解来实现

如果你使用http://localhost:8080/webstore/welcome进行访问，将会出现一个404页面：

<img src='springMVC03\09f4028d-0dcd-404a-9849-b0a6faad8116.jpg' style='margin:30px;display:block' alt='title'>

如果打开HomeController，将@RequestMapping的值修改为/welcome，重新打开页面将会得到正确页面:

<img src='springMVC03\1b431e13-f7f2-4d3b-b417-dc38340710d3.jpg' style='margin:30px;display:block' alt='title'>

### 请求地址

我们将请求地址分为五个部分：

<img src='springMVC03\d4371253-d11e-4fa5-83c5-af64c59a3869.jpg' style='margin:30px;display:block' alt='title'>

Schema指的是协议类型，如http或https

HostName指的是主机名称

application Name指的是项目名称

Request path是项目下的地址

parameters指的是提交的参数

### web 应用上下文

在Spring的项目中，应用的对象由对象容器进行管理。这个容器称为web应用的上下文。上下文通过DI技术管理Bean的创建及依赖管理。Bean就是一个个POJO类，可以通过xml配置，或者java配置类，甚至基于注解注册到容器。









