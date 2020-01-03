---
title: Spring MVC创建一个项目
date: 2020-01-03 21:16:03
tags: spring mvc
---

## 在STS中创建项目

1. 通过File-New-Project创建一个Maven项目

<img src='springMVC02\41d6b37a-2ffe-4532-85b3-8d9e2e646e52.jpg' style='margin:30px;display:block' alt='title'>

2. 填写相关信息，结束创建

<img src='springMVC02\b70b4f0c-020b-42ae-8cf2-01e5b3654a84.jpg' style='margin:30px;display:block' alt='title'>

GroupID即组织ID，一般以公司域名倒置填写，ArtifactID一般用项目名称，因为我们想要部署到tomcat中，因此打包方式设置为war包。

3. 生成的项目结构如图所示

<img src='springMVC02\b087dbe1-46b4-4d22-8411-bdc8bec172e6.jpg' style='margin:30px;display:block' alt='title'>

## 添加Spring依赖

1. 打开pom.xml文件，并添加依赖，输入Spring MVC的相关信息

<img src='springMVC02\f1e6eea8-2f58-4720-b995-5da786b2fb55.jpg' style='margin:30px;display:block' alt='title'>

groupID 为<code style='background:#ff3385;color:white;padding:5px;'>org.springframework</code>，ArtifactID为<code style='background:#ff3385;color:white;padding:5px;'>spring-webmvc</code>，版本为<code style='background:#ff3385;color:white;padding:5px;'>4.0.3.RELEASE</code>,范围选择<code style='background:#ff3385;color:white;padding:5px;'>编译</code>。

2. 同样的，为了显示页面，需要添加JSTL依赖

groupID 为<code style='background:#ff3385;color:white;padding:5px;'>javax.servlet</code>，ArtifactID为<code style='background:#ff3385;color:white;padding:5px;'>jstl</code>，版本为<code style='background:#ff3385;color:white;padding:5px;'>1.2</code>,范围选择<code style='background:#ff3385;color:white;padding:5px;'>编译</code>。

3. 添加Servlet-api依赖

groupID 为<code style='background:#ff3385;color:white;padding:5px;'>javax.servlet</code>，ArtifactID为<code style='background:#ff3385;color:white;padding:5px;'>javax.servlet-api</code>，版本为<code style='background:#ff3385;color:white;padding:5px;'>3.1.0</code>,范围选择<code style='background:#ff3385;color:white;padding:5px;'>Provided</code>。

4. 依赖添加完毕

<img src='springMVC02\83a94160-538d-400e-b64e-5cea5156fe1b.jpg' style='margin:30px;display:block' alt='title'>

在此对依赖添加作出解释：Maven是一种包管理机制，会解决包之间的依赖关系和版本问题。我们制定组名、包名、版本即可告诉Maven我们想要什么包，它自动完成下载和相关依赖包的下载。
编译期间需要打入包内的是编译包，不需要打入的是提供包，因为tomcat里面有servlet-api，所以无需打包。

## JAVA小配置

打开pom.xml文件，在底部找到overView视图，找到properties并添加属性：maven.compiler.source=1.7

<img src='springMVC02\17f8b5f1-24bf-4ed2-af8d-7cb75a51e973.jpg' style='margin:30px;display:block' alt='title'>

同时，设置目标版本maven.compiler.target=1.7

## 创建一个欢迎界面

1. 在src/main/webapp下面创建WEB-INF/jsp路径，并创建welcome.jsp文件

<img src='springMVC02\54109039-f24e-4cc4-bf74-2554c652b1c3.jpg' style='width:600px;height:400px;margin:30px;display:block' alt='title'>

页面很简单，就是显示一个greeting和一个tagline字段

2. 在src/main/java路径下创建一个com.packt.webstore.controller包，并在本包下创建HomeController.java文件

<img src='springMVC02\4335d3b6-81aa-4fa4-855f-a10641331ea6.jpg' style='margin:30px;display:block' alt='title'>

在jsp文件中，有两个jstl标签，用于显示两个变量的值：

<img src='springMVC02\d1245300-444a-4015-a538-7a3ab3e74936.jpg' style='margin:30px;display:block' alt='title'>

这两个值来自于控制器存储到model中的数据

<img src='springMVC02\59fc7aa2-0133-4147-8db2-10251b26448b.jpg' style='margin:30px;display:block' alt='title'>

3. 配置DispatcherServlet

没有这个是无法访问的，DispatcherServlet将会拦截用户的请求，根据实际请求地址映射到相关的controller，甚至具体的action。在src/main/webapp/WEB-INF/路径下创建web.xml配置文件：

<img src='springMVC02\fab7cdf7-eb8b-4cba-aac5-b42a9d8d1fec.jpg' style='margin:30px;display:block' alt='title'>

创建servlet用于拦截前端请求，servlet-mapping用于配置映射路径，一般拦截全部请求，所以url-pattern是/，表示所有路径

4. 在src/main/webapp/WEB-INF/路径下，创建另外一个配置文件DefaultServlet-servlet.xml

<img src='springMVC02\9da14ede-34bc-4b83-9479-5e1b6f6dd5f4.jpg' style='margin:30px;display:block' alt='title'>

这个配置文件配置了注解扫描、组件扫描的包路径，并配置了前端页面的存储位置，在/WEB-INF/jsp文件夹下，并且以.jsp结尾

5. 通过run as 即可选择tomcat部署运行

<img src='springMVC02\12a0d456-f3da-49f0-9ca8-326ddd297de9.jpg' style='margin:30px;display:block' alt='title'>

我们可以打开浏览器访问了

<img src='springMVC02\2a261bff-3bb2-404d-9fbd-bfbaa600846d.jpg' style='margin:30px;display:block' alt='title'>