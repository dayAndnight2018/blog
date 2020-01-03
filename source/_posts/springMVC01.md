---
title: Spring MVC开发环境配置
date: 2020-01-01 19:57:30
tags: spring mvc
---

## 配置JAVA


1. 从[JAVA开发环境下载地址](http://www.oracle.com/technetwork/java/javase/downloads/index.html)下载JDK开发环境

2. 如图所示，安装JDK，在JDK中已经包含JRE

<img src='springMVC01\8cf53021-eff0-4987-992e-fab6acb0ca80.jpg' style='margin:30px;display:block' alt='title'> 

3. 将JDK路径配置到环境变量

<img src='springMVC01\263d9a58-e2a4-407e-a77c-5c1b0a7bf9f1.jpg' style='margin:30px;display:block' alt='title'>

4. 测试JDK

<pre style='background:#e6e6e6;padding=10px;'>
   
     java -version

</pre>

<img src='springMVC01\e7965238-9843-4ff9-b3d5-2d24cb125cd8.jpg' style='margin:30px;display:block' alt='title'>


***


## Maven


1. 从[Maven下载地址](http://maven.apache.org/download.cgi)下载Maven安装包

2. 解压后，添加环境变量

<img src='springMVC01\9753ca75-5f7a-4495-a95a-1e1294c877f1.jpg' style='margin:30px;display:block' alt='title'>

3. 测试Maven

<pre style='background:#e6e6e6;padding=10px;'>

     mvn -version

</pre>

<img src='springMVC01\1baafde0-0eae-430e-9404-bebfb1980253.jpg' style='margin:30px;display:block' alt='title'>


***

## Tomcat

1. 从[此处](http://tomcat.apache.org/)下载安装包

2. 一直下一步，安装即可。

<img src='springMVC01\0589c8d1-7aa8-41ca-8e1f-9fac1b24a840.jpg' style='margin:30px;display:block' alt='title'>


***


## STS

1. 由[此处](http://spring.io/tools/sts/all)下载STS安装包

2. 一直next安装即可。在某个步骤需要配置JDK路径。

<img src='springMVC01\f8522a20-4d79-4604-8a4e-73dcfa566bac.jpg' style='margin:30px;display:block' alt='title'>

3. 打开STS，找到<code style='background:#ff3385;color:white;padding:5px;'>window</code>-<code style='background:#ff3385;color:white;padding:5px;'>preferences</code>-<code style='background:#ff3385;color:white;padding:5px;'>Server</code>-<code style='background:#ff3385;color:white;padding:5px;'>Runtime Environment</code> 添加tomcat服务器

<img src='springMVC01\3f41ff6f-5fab-436a-8af1-3d280485e8d8.jpg' style='margin:30px;display:block' alt='title'>

4. 选择合适的版本，并将tomcat的安装路径配置好

<img src='springMVC01\d04bf7a4-b479-498b-a16e-69a4c04070c5.jpg' style='margin:30px;display:block' alt='title'>

5. 打开STS，找到<code style='background:#ff3385;color:white;padding:5px;'>window</code>-<code style='background:#ff3385;color:white;padding:5px;'>preferences</code>-<code style='background:#ff3385;color:white;padding:5px;'>Maven</code>-<code style='background:#ff3385;color:white;padding:5px;'>Installations</code>添加Maven的安装路径到STS

<img src='springMVC01\e7bb906e-4b94-48fc-8f06-233144dd2a55.jpg' style='margin:30px;display:block' alt='title'>



***

至此，Spring MVC开发环境配置完毕。