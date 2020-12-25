---
title: JavaEE-12-Spring-DB
date: 2020-06-21 09:50:24
tags: JavaEE
---
## Spring 与 JDBC

### 配置数据源

1. 采用SimpleDriverDataSource配置非池化数据源

<img src='JavaEE-12-Spring-DB\83f3fb45-6092-444a-a8cf-d05fc178d53b.jpg'>

2. 采用DBCP连接池

<img src='JavaEE-12-Spring-DB\ee325ff4-9294-4fe2-89e8-bcd8a5c46f3c.jpg'>

3. JNDI数据源

<img src='JavaEE-12-Spring-DB\ddc60546-652e-419b-b3a4-0d7977f1e347.jpg'>

### 配置JDBCTemplate

<img src='JavaEE-12-Spring-DB\5a12d916-2029-467e-900e-060ea463362b.jpg'>

### 使用JDBCTemplate查询数据

<img src='JavaEE-12-Spring-DB\1912d9b0-69db-47ad-a29c-bd02ee6fe9ab.jpg'>
<img src='JavaEE-12-Spring-DB\05fe729c-6be3-48c1-b432-3792b1f6043b.jpg'>

也可以使用lambda表达式简化：

<img src='JavaEE-12-Spring-DB\9fc06733-9bcc-4b1f-8687-e66a04502fc3.jpg'>

### JDBCTemplate增删改查

增：

<img src='JavaEE-12-Spring-DB\6c079d35-35e1-4fd4-b454-015c27db6a75.jpg'>

删：

<img src='JavaEE-12-Spring-DB\938feb54-34bc-4bf4-b13d-3bd6a2cb15c8.jpg' >

改：

<img src='JavaEE-12-Spring-DB\6a9dbff1-eec6-479b-8a0c-7e292f00129e.jpg'>

查：

<img src='JavaEE-12-Spring-DB\a6337126-ac2f-4054-bb97-ca5c594fd242.jpg'>
<img src='JavaEE-12-Spring-DB\46f50c1b-a57f-4045-8351-2739d2588558.jpg'>

### 执行多条语句

使用ConnectionCallback回调：

<img src='JavaEE-12-Spring-DB\32d102eb-6ae3-403d-972a-e97cec322e79.jpg'>
<img src='JavaEE-12-Spring-DB\86857a3c-9842-4894-9277-78fd0358a819.jpg'>

使用StatementCallback回调:

<img src='JavaEE-12-Spring-DB\c225b152-9b32-4cbe-9f4d-685a0ba1088b.jpg'>

## Mybatis

Mybatis的使用：

1. 配置数据源

2. 配置SqlSessionFactory

3. 配置Mapper


### 配置SqlSessionFactoryBean

SqlSessionFactoryBean用于产生SqlSessionFactory

<img src='JavaEE-12-Spring-DB\f4c84972-e90f-47f0-95e5-3466540cb5de.jpg' >

配置了dataSource数据源，配置文件位置。

mybatis配置文件:

<img src='JavaEE-12-Spring-DB\e1f1f48a-a95e-4fae-b1c4-89601b94fdf1.jpg'>

Mapper.xml是映射的sql语句：

<img src='JavaEE-12-Spring-DB\b905d1e0-ff5e-4144-b3c9-9d16dcd9e732.jpg' >

Mapper接口和sql是一一对应的：

<img src='JavaEE-12-Spring-DB\5819c8e0-6242-403c-9ea4-d5461ace3bac.jpg'>


### Mapper接口扫描

1. 使用@Repository注解注释Mapper接口，以便扫描

<img src='JavaEE-12-Spring-DB\d30b8807-8f0f-4008-bbaf-39965aaefb0d.jpg' >

2. 配置MapperScannerConfigurer

<img src='JavaEE-12-Spring-DB\ec1314c7-a60a-4875-8156-8a0d5f71a809.jpg'>
<img src='JavaEE-12-Spring-DB\5379b5e6-85e4-4dc5-b054-c0e93bf4bbf9.jpg' >

basepackage用于扫描。

SqlSessionFactoryBeanName用于配置SqlSessionFactory

annotationClass表示指定的注解。

3. 操作Mapper进行数据处理

<img src='JavaEE-12-Spring-DB\433d74f0-b221-475b-877f-07dfba932f18.jpg'>















