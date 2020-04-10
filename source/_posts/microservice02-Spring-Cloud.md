---
title: microservice03-Spring Cloud
date: 2020-04-04 10:24:42
tags: microservice
---

Spring Boot用于开发微服务应用，而实际的微服务架构不仅仅包含应用，还有服务注册、服务发现等部分：

<img src='microservice02-Spring-Cloud\30350f6f-9169-4e7d-815f-8d9a719fb85f.jpg'>

下面以Dalston SR3为例进行介绍Spring Cloud.

## 服务发现

### 服务发现介绍

服务发现主要采用Spring Cloud Netflix中的Eureka。

主要包括Eureka Server（服务端发现组件）和Eureka Client（客户端发现组件）两个部分。

<img src='microservice02-Spring-Cloud\92197523-a6f0-43b9-8a78-279ec85e2107.jpg'>

Eureka Server定时检测服务的可用性。

Eureka Client将服务注册到服务管理中心。

服务发现中，服务消费者、服务管理中心，服务提供者的关系：

<img src='microservice02-Spring-Cloud\83a0a45d-172a-4225-a13a-8895fcfa362c.jpg'>

服务消费者与服务管理中心维持心跳，更新最新调用地址。


### 实现

1. 新建Maven项目，添加Spring Cloud的依赖

<img src='microservice02-Spring-Cloud\4c0ea19c-621c-4b7c-babc-3ec315f570d1.jpg'>

2. 创建服务端工程子模块

a. 创建Server子工程，添加eureka server依赖：

<img src='microservice02-Spring-Cloud\60bdd203-2d65-4201-aea4-a8984868a618.jpg'>

b. 为eureka server添加配置文件：

<img src='microservice02-Spring-Cloud\9bdd2f1d-0d10-4d95-aa26-adef46bd4522.jpg'>

配置文件中配置了项目的端口号8761，实例名称为localhost, register-with-eukera与fetch-registry都是服务发现客户端需要做的，配置为false，并设置服务发现服务端地址。

c. 为启动类添加EnableEukeraServer注解

<img src='microservice02-Spring-Cloud\a1d32b50-4763-4dad-b89e-38d572398a22.jpg'>

d. 测试

<img src='microservice02-Spring-Cloud\f698027b-10db-4d97-870a-6cf4dfcacc8d.jpg'>

3. 创建客户端工程子模块

a. 创建客户端子项目，添加依赖

<img src='microservice02-Spring-Cloud\c349af84-4c38-4913-bca3-3d3538e7bdf3.jpg'>

b. 添加配置信息

<img src='microservice02-Spring-Cloud\344a56cc-91c9-466f-b937-ca7f52bb86ed.jpg'>

配置客户端端口，显示主机ip,配置服务端地址，配置客户端应用名称。

c. 为启动类添加EnableEukeraClient注解

<img src='microservice02-Spring-Cloud\ea09111b-7337-4e37-b904-8bc8dc25c0d8.jpg' >

d. 测试

<img src='microservice02-Spring-Cloud\20267eb7-bc0e-42df-94f2-db74737b5d6f.jpg'>

### 服务间调用

测试订单与用户服务之间的调用。

1. 添加订单服务项目：

a. 添加依赖

<img src='microservice02-Spring-Cloud\1e13f4a5-1cb1-4d72-bf75-a5293f6e2248.jpg'>

b. 添加配置

<img src='microservice02-Spring-Cloud\d20d33b7-a221-404d-8793-d2ce30206092.jpg'>

c. 添加POJO

<pre style='background:#e6e6e6;padding=10px;'>
public class Order{
    private String id;
    private Double price;
    private String receiverName;
    private String receiverAddress;
    private String receiverPhone;
    /**getters and setters**/
}
</pre>

d. 添加控制器类

<img src='microservice02-Spring-Cloud\042af9fc-15c5-42d1-8817-c075d61a02d6.jpg'>

e. 在引导类上添加EnableEukeraClient注解

2. 为用户服务添加RestTemplate的Bean

<img src='microservice02-Spring-Cloud\04ca9d88-89d3-4ec1-bd7c-d3d880d524c2.jpg'>

3. 添加控制器类

<img src='microservice02-Spring-Cloud\4f00d874-e74f-48b2-b228-a7a7bfed4f31.jpg'>
<img src='microservice02-Spring-Cloud\78ece87b-60d3-4651-a71d-2b6e28a64267.jpg'>

restTemplate将完成远程调用，获取订单信息。

4. 测试

<img src='microservice02-Spring-Cloud\16854ff4-b648-4b02-a092-2b0466c84f08.jpg'>

## 客户端负载均衡

客户端负载均衡采用Ribbon实现。

在Eukera中内置了Ribbon，只需要在配置RestTemplate时添加LoadBalanced注解：

<img src='microservice02-Spring-Cloud\98e1ad20-1488-4676-a647-b93f722e9c97.jpg'>

在调用服务时，取消主机+端口调用，而直接使用服务的实例名称：

<img src='microservice02-Spring-Cloud\0a8c2ffa-4279-4d8e-b83e-5037d2a9aa18.jpg'>

## 服务容错

多个服务层之间调用关系会存在级联的关系：

<img src='microservice02-Spring-Cloud\10a0eedb-4d1f-4a7c-9f80-a8c7c9ef02a2.jpg'>

一旦某个服务出现故障，将会出现故障传递。

### 熔断器的三种状态

关闭、打开、半开：

<img src='microservice02-Spring-Cloud\0b2567a3-8504-4f58-9d94-26ed2c1fab75.jpg'>

服务健康状况 = (请求失败数 / 请求总数) 和 设定阈值（默认10秒内20次失败）

健康值高于域值熔断器关闭，否则熔断器打开，阻止请求。打开后一定的时间窗内，将恢复半开。半开状态只允许一个请求，若请求成功则关闭，否则继续回到打开状态。

服务调用失败时，若有fallback方法，将执行fallback：

<img src='microservice02-Spring-Cloud\b7715133-2ef6-485c-8716-05c84edd2a7c.jpg' >

### 实现

原有的父项目及订单服务可以复用，新建熔断user项目：

1. 添加依赖

<img src='microservice02-Spring-Cloud\89319af8-3612-4106-a28d-eb73372d978d.jpg'>

除了eukera还需要hystrix.

2. 配置信息与上面类似

<img src='microservice02-Spring-Cloud\6acddc2f-811f-4588-9962-c6f91dfce09d.jpg'>

3. 配置启动类

添加EnableCircuitBreaker及EnableEukeraClient注解

<img src='microservice02-Spring-Cloud\c4b6f6dc-31da-4685-a9b2-20a3c83fc71c.jpg'>

4. 新建控制器

<img src='microservice02-Spring-Cloud\a98442b4-4b47-4f70-9cef-3ca41ab1ad8c.jpg'>

为动作方法添加HystrixCommand注解，指定调用失败的方法，二者参数列表应当一致。

<img src='microservice02-Spring-Cloud\d22c1367-1e90-483a-ac96-41a3ef998cbe.jpg'>

5. 测试

使用ribbon进行负载均衡时，会对订单服务进行轮询，将其中一个服务停掉，再次轮询到时会进入fallback方法：

<img src='microservice02-Spring-Cloud\ec161863-0240-42cc-8510-47741de9a100.jpg'>
























