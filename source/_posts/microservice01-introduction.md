---
title: microservice01-微服务简介
date: 2020-04-03 14:59:38
tags: microservice
---

## 早期的单体架构

早期的单体架构采用war包，普通java类库以jar包形式存在于war包内，架构简单：

<img src='microservice01-introduction\97f09461-5de2-4787-84eb-44b96339c9e7.jpg'>

在用户量较少的时候，单个服务器即可满足需求，一旦用户数增大，可以采用水平扩展的方法（即：将war包复制部署到多个服务器，通过负载均衡转发到不同的服务器承担压力）

<img src='microservice01-introduction\f41696a6-e1d3-4580-9002-ccda7111e547.jpg'>

当然，数据是共享的。

但是，这样的架构会带来一些问题：

1. 维护困难，功能繁杂的单体应用难以重构二次开发。

2. 资源浪费。水平扩展就是简单的复制，对不同的服务的需求可能存在差异，对不需要扩展的服务进行扩展造成资源浪费。

3. 影响开发效率。应用越来越大，开发调试困难。

4. 可靠性差。单体应用是一整个war包，单个模块出现问题将影响整个war包。

5. 影响技术更新。整个技术栈必须一致，更新换代很麻烦。

总体来说就是因为<code style='background:#ff3385;color:white;padding:5px;'>所有的模块都在一个war包里</code>。

## SOA

<img src='microservice01-introduction\edcb4bc0-08e4-444c-b38e-c6a6c92371e4.jpg'>

SOA是一种对单体应用的改进。

将大系统分成多个子模块进行开发，通过服务总线获取相关的服务提供相关的功能，进而实现简单的解耦。

在部署时，类似于一个tomcat下部署多个应用。

## 微服务

微服务要求系统按照功能拆分成更细小的部分，对外提供api进行服务。

将传统的单体架构拆分成多个服务，每个服务相互独立，服务可以访问数据库，服务之间也可以相互调用。

<img src='microservice01-introduction\72f84ca2-771d-4afd-82ed-02eaabddfd08.jpg'>

### 微服务的优势

1. 复杂度可控。单个团队即可完成开发维护任务。

2. 独立部署。单个服务可以独立部署，多个模块可以互不影响地维护。

3. 独立扩展。进行扩展时可以有针对性的进行扩展。

### 微服务的缺点

1. 开发工具主要面向单体应用，缺少微服务的工具

2. 开发测试困难。服务之间采用接口调用，依赖关系维护较难。

3. 考虑分布式事务

4. 内存消耗大。单个服务部署在单个节点，，单个节点由单个JVM管理，内存消耗较大。

## 微服务与SOA对比

<img src='microservice01-introduction\af3cc9fa-177c-4b5a-aeed-0e57ecbfd15c.jpg'>

## 微服务拆分

1. 根据业务的功能进行分割。

2. 对域进行分割。

3. 使用动词设计，如完成订单的航运功能。

4. 对特定实体操作的服务，如账户服务。

## 微服务组件

1. 服务注册中心

服务注册中心就是注册所有服务的地方。

2. 服务注册

服务提供方将自己的调用地址注册到服务注册中心，以便调用方可以调用。

3. 服务发现

服务调用方从服务注册中心获取到服务的调用地址。

4. 负载均衡

服务一般横向扩展多节点提供服务，负载均衡可以实现压力分配

5. 服务容错

通过熔断器实现对异常服务调用时的快速响应，避免大量的同步等待。

6. 服务网关

即API网关，服务调用的唯一入口。可以在此实现鉴权、动态路由、灰度发布、负载限流等。

7. 分布式配置中心

将本地配置文件配置到配置中心，以便无差别调试。

<img src='microservice01-introduction\c28915a5-0177-457e-a728-9953c450638e.jpg'>

## 微服务架构的技术选型

<table cellpadding='8' border='1' style='background:#EAF2D3;text-align:center'>
<tr>
&nbsp;&nbsp;<td>
开发
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Spring Boot、WildFly Swarm、KumuluzEE
&nbsp;&nbsp;</td>
</tr>
<tr>
&nbsp;&nbsp;<td>
服务注册与发现
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Spring Cloud Eureka、Apache ZooKeeper、Consul、Etcd、Dubbo
&nbsp;&nbsp;</td>
</tr>
<tr>
&nbsp;&nbsp;<td>
负载均衡
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Spring Cloud Ribbon、Dubbo
&nbsp;&nbsp;</td>
</tr>
<tr>
&nbsp;&nbsp;<td>
服务容错
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Spring Cloud Hystrix
&nbsp;&nbsp;</td>
</tr>
<tr>
&nbsp;&nbsp;<td>
API网关
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Spring Cloud Zuul、Spring Reactor、Netty、NodeJS
&nbsp;&nbsp;</td>
</tr>
<tr>
&nbsp;&nbsp;<td>
分布式配置中心
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Spring Cloud Config
&nbsp;&nbsp;</td>
</tr>
<tr>
&nbsp;&nbsp;<td>
调试
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Swagger
&nbsp;&nbsp;</td>
</tr>
<tr>
&nbsp;&nbsp;<td>
部署
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Docker
&nbsp;&nbsp;</td>
</tr>
<tr>
&nbsp;&nbsp;<td>
持续集成
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Jenkins
&nbsp;&nbsp;</td>
</tr>

</table>

<img src='microservice01-introduction\e72bbd8b-9c18-4374-911f-2cbfa73505c1.jpg'>


