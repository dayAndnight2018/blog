---
title: springBoot2-12-websocket
date: 2020-07-08 21:35:37
tags: spring-boot-2
---

Websocket提供全双工通信

## 纯websocket

1. 添加依赖

<img src='springBoot2-12-websocket\601b94b1-77bd-4b27-970d-19af181a2a17.jpg'>

2. 注册ServerEndpointExporter为Bean

<img src='springBoot2-12-websocket\3a195650-2b35-43b3-986b-e765b2edcfbc.jpg'>

3. 服务节点设计

<img src='springBoot2-12-websocket\78a20651-dcb1-4d55-8dc7-2aa9fadd9c37.jpg'>
<img src='springBoot2-12-websocket\60cc868d-a440-41df-b1a5-19d03714d348.jpg'>
<img src='springBoot2-12-websocket\cf6f2266-411d-4cc2-a741-69f4808f18cf.jpg'>
<img src='springBoot2-12-websocket\cb91bba2-24c7-42a1-a57e-7d1909a2cf7e.jpg'>
<img src='springBoot2-12-websocket\acc8412c-4698-4507-b92f-3ae02ade8388.jpg'>

@OnOpen建立连接时调用

@OnMessage有消息时调用

@OnClose关闭连接时调用

@OnError出错时调用

