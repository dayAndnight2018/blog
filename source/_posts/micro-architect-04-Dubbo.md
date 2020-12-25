---
title: micro-architect-04-Dubbo
date: 2020-06-24 16:23:51
tags: microservice
---

## Dubbo基本结构

<img src='micro-architect-04-Dubbo\81a93761-6add-47ee-a368-bdcec4d9d6bf.jpg'>

## 注册中心

### 单个服务配置

注册中心推荐使用ZooKeeper，解决分布式环境下的数据管理问题，如：统一命名服务、状态同步服务、集群管理、分布式应用配置项。

解压后进入conf文件夹，修改zoo_sample.cfg为zoo.cfg

<img src='micro-architect-04-Dubbo\ac05ccdd-bad5-4d4e-ac47-892a17d7a1f7.jpg'>

### 集群配置

<img src='micro-architect-04-Dubbo\19f7e6a5-d034-4a3c-83e6-736db81ec7ba.jpg'>

server:A:B:C:D

A为名称，B为Ip，C和D分别为仲裁与Leader的端口号。

### 启动Zookeeper

<img src='micro-architect-04-Dubbo\8c54295c-3600-4dd3-9ef8-52c2fdee8c1d.jpg'>

## 接口工程

Dubbo是基于接口进行约定的，因此，创建接口工程，为服务端和消费端提供约定。

<img src='micro-architect-04-Dubbo\95ae7f46-a387-457c-9b71-7bf8bbaec989.jpg'>

## 服务端项目

1. 创建Spring Boot项目

<img src='micro-architect-04-Dubbo\be48446e-d278-4eab-871b-2735352279e8.jpg'>

2. 添加依赖（Dubbo、接口项目）

<img src='micro-architect-04-Dubbo\27c33106-9653-4574-9d0f-f120d42298b6.jpg'>

3. 编写接口的实现类

<img src='micro-architect-04-Dubbo\385a5693-f4d5-491a-a737-0732613201c2.jpg'>

@Service用于标志为Dubbo服务。可配置属性：

<table cellpadding='8' border='1' style='background:#EAF2D3;text-align:center'>
<thead>
&nbsp;<tr>
&nbsp;&nbsp;<td>
参数
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
含义
&nbsp;&nbsp;</td>
&nbsp;</tr>
</thead>
&nbsp;<tr>
&nbsp;&nbsp;<td>
version
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
服务版本
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
group
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
服务分组，当接口存在多种实现时，使用group划分
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
cache
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
缓存策略：lru(最近最少使用) threadlocal（当前线程缓存）
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
async
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
非阻塞调用
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
delay
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
服务延迟暴露时间
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
timeout
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
服务超时时间
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
retries
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
重试次数
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
token
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
令牌验证
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
dynamic
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
服务动态注册
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
register
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
是否注册到中心
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
deprecated
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
是否过时
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
accesslog
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
是否输出日志
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
executes
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
服务端并发执行
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
actives
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
客户端并发执行
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
loadbalance
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
负载均衡策略：random / roundrobin / leastactive
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
connections
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
限制连接数
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
protocol
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
使用协议：Dubbo、Hessian、RMI、HTTP、WebService、Thrif
&nbsp;&nbsp;</td>
&nbsp;</tr>
&nbsp;<tr>
&nbsp;&nbsp;<td>
mock
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
使用接口名+mork作为类名，服务调用后调用，local在服务调用前调用。
&nbsp;&nbsp;</td>
&nbsp;</tr>
</table>






