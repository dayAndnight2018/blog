---
title: springBoot2-06-整合Mybatis
date: 2020-07-08 15:13:56
tags: spring-boot-2
---

## 配置数据源

1. 添加依赖

<img src='springBoot2-06-database\57a82970-1512-47cf-90fc-988c63c7ba90.jpg'>

2. 配置数据源

<pre style='background:#e6e6e6;padding=10px;'>
spring.datasource.url=jdbc:mysql://127.0.0.1:3306/test?useUnicode=true&characterEncoding=utf-8&serverTimezone=GMT%2B8

spring.datasource.username =root
spring.datasource.password=123456
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver


spring.datasource.type=org.apache.commons.dbcp2.BasicDataSource
spring.datasource.dbcp2.max-idle=10
spring.datasource.dbcp2.max-total=50
spring.datasource.dbcp2.max-wait-millis=10000
spring.datasource.dbcp2.initial-size=5
</pre>

3. 创建POJO

<img src='springBoot2-06-database\97d299b9-706e-4ca3-b4f7-8b580389b11b.jpg'>

这里存在一个枚举类型，需要转换器

4. 定义枚举类型

<img src='springBoot2-06-database\7381fa58-d677-4cd9-9138-9b4bf73b4ba8.jpg'>

5. 枚举转换器

<img src='springBoot2-06-database\52f6f8c9-fda3-49f6-ac7f-94b16240d947.jpg'>
<img src='springBoot2-06-database\4178b3bc-636c-4e55-b278-f3ba89c1db68.jpg'>

6.创建DAO接口

<img src='springBoot2-06-database\4a85918c-8827-4b1c-847f-9e30d52d2235.jpg'>

7. 创建对应的mapper文件

<img src='springBoot2-06-database\6cb5c6cb-6574-4634-88ab-2d97125f03c2.jpg'>

8. 创建服务层接口

<img src='springBoot2-06-database\7142c918-9be1-4b68-a957-da0a5ead6e83.jpg'>

9. 调用DAO层返回数据

<img src='springBoot2-06-database\6b5debef-9c22-472f-ba0a-341c85031f47.jpg'>

10. 控制器层注入服务层进行测试

<img src='springBoot2-06-database\3ab565ca-2629-4972-b143-cabc146f8851.jpg'>

11.添加mybatis配置信息

<pre style='background:#e6e6e6;padding=10px;'>
mybatis.mapper-locations=classpath:mappers/*.xml
mybatis.type-handlers-package=com.example.demo.typeHandlers
</pre>

12. 注解启动类，发起mapper接口扫描

<img src='springBoot2-06-database\c2031c37-db6f-442e-a5ff-0cdb27ead7bf.jpg'>

### 备注

如果出现serverTimeZone问题请检查数据库连接的url

如果出现找不到mapper，配置pom文件的build节点，将*.xml文件包含到目标路径。

<img src='springBoot2-06-database\f671863a-193b-43e5-9aec-d097c21915e0.jpg'>