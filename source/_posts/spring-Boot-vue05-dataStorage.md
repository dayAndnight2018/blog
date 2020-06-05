---
title: 'spring-Boot+vue05: 数据存储'
date: 2020-05-30 11:28:12
tags: spring-boot
---

## Spring Boot 整合Mybatis做数据持久化

1. 创建项目添加依赖

<img src='spring-Boot-vue05-dataStorage\75b3f913-5b99-410a-baea-75d04e65ac37.jpg'>

2. 创建数据表

<img src='spring-Boot-vue05-dataStorage\4ff13322-95de-416f-a1cb-6aa5e199eb8f.jpg'>

3. 创建实体类

<img src='spring-Boot-vue05-dataStorage\278987ac-44ec-4a0c-98bf-79c2be32ee45.jpg'>

4. 配置文件

<img src='spring-Boot-vue05-dataStorage\a9890d67-833e-4e93-9a9c-4ce98c2cce5f.jpg'>

5. 创建数据库映射层

即一个个接口方法，与xml一一对应

<img src='spring-Boot-vue05-dataStorage\5caf4fe4-287c-4ec2-8350-e757b0694478.jpg'>

6. 在相同目录下创建mapper映射文件

<img src='spring-Boot-vue05-dataStorage\02a148a3-579d-4ffa-a46b-569459878110.jpg'>

7. 创建服务层

<img src='spring-Boot-vue05-dataStorage\fa86ecc3-0645-45ce-917a-b9120d822054.jpg'>
<img src='spring-Boot-vue05-dataStorage\d99f701e-8cae-466b-8f50-2b8edc37ae04.jpg'>

8. 创建控制器层

<img src='spring-Boot-vue05-dataStorage\5cce11e8-dff6-432d-a268-73b4bb12927d.jpg'>

9. 配置pom

由于maven项目默认存储在src/main/resources目录下, mapper文件找不到，需要配置一下：

配置编译目录

<img src='spring-Boot-vue05-dataStorage\fe77e827-9f31-4867-8bb0-9c0dfa82b284.jpg'>
<img src='spring-Boot-vue05-dataStorage\2c6d0a3c-21e5-4eba-8822-c51fa3edc4ca.jpg'>

## 多数据源问题

实际开发中不可避免地操作多个数据库，如何同时配置多个数据源呢？

1. 创建数据库

<img src='spring-Boot-vue05-dataStorage\525f7701-46a0-4466-87f2-f0def97cd808.jpg'>

2. 配置连接

<img src='spring-Boot-vue05-dataStorage\e54e2d4a-3363-4384-8bad-43243f329e4c.jpg'>

针对不同的数据源给定不同的前缀。

3. 由于存在多个数据源，需要给出多个DataSource的实例

<img src='spring-Boot-vue05-dataStorage\91fa9a01-82e8-4c2b-8175-58fab91bf3a8.jpg'>
<img src='spring-Boot-vue05-dataStorage\49c67feb-e4ad-4c36-b792-6725e9d95840.jpg'>

4. 创建第一个数据源SqlSessionFactory

<img src='spring-Boot-vue05-dataStorage\14f65027-db1a-4933-84a5-8e461bdc6ae7.jpg'>

5. 创建第二个数据源SqlSessionFactory

<img src='spring-Boot-vue05-dataStorage\8240481f-3911-45fb-992b-b5c992d9691d.jpg'>
<img src='spring-Boot-vue05-dataStorage\3ba6e889-bad6-46bb-a15a-063347afac76.jpg'>

6. 创建mapper文件及接口

<img src='spring-Boot-vue05-dataStorage\10ab9768-791c-4583-9413-e02fdb7bf55c.jpg'>

<img src='spring-Boot-vue05-dataStorage\b09544a1-aea7-4b7c-98c9-22eecf9d4d9d.jpg'>

7. 注入使用

<img src='spring-Boot-vue05-dataStorage\d756b9aa-7711-4de7-856e-1983753c6d9c.jpg'>
<img src='spring-Boot-vue05-dataStorage\2224d21b-5422-4d37-ae7f-b53658be6b66.jpg' >

