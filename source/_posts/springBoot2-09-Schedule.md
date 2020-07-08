---
title: springBoot2-09-定时任务
date: 2020-07-08 20:19:22
tags: spring-boot-2
---

定时任务是很常见的，每间隔一定时间循环执行，或固定某时间点执行等等。

## 开始定时任务

1. 使用@EnableScheduling开启定时任务（配置类或入口类）

2. 使用@Scheduled标记方法，可以定时执行

<img src='springBoot2-09-Schedule\eb2bce37-d884-4455-962f-01395d4a421f.jpg'>

@Async表示使用线程池执行

<img src='springBoot2-09-Schedule\936355af-6b57-4087-af9e-c7eea46eb110.jpg'>

### 几种属性

fixedDelay ：以上一次任务完成时刻为起点，延迟一定时间再次执行。

fixedRate：以固定的时间间隔执行，不管上一次有没有完成。

initialDelay ： 首次执行前的间隔时间。

### cron表达式

秒| 分| 时| 天| 月| 星期| 年

<img src='springBoot2-09-Schedule\450e1235-9075-409b-b038-45c514698322.jpg'>
<img src='springBoot2-09-Schedule\196ddac6-1315-4ff6-8a9f-e86ae0dfc432.jpg'>

### cron使用举例

<img src='springBoot2-09-Schedule\5dc54825-6a31-42f0-bc3c-33c78d2b97ee.jpg'>
