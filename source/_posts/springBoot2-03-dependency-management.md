---
title: springBoot2-03-依赖管理
date: 2020-07-07 08:28:41
tags: spring-boot-2
---

## 使用Java配置文件配置Bean

1. 创建POJO

<img src='springBoot2-03-dependency-management\7ae8708f-8f18-4ab3-9a3e-fb8581484b96.jpg'>

这就是一个简单的类，我们接下来通过配置类将它注册到容器中用于使用。

2. 配置类使用@Bean注册Bean

<img src='springBoot2-03-dependency-management\bdf1a5bd-514d-42d7-aec3-5ee72fcb739b.jpg'>

3. 使用Bean

<img src='springBoot2-03-dependency-management\71b3ede5-df8c-4164-a598-0d0754707f17.jpg'>

通过Autowired注入Bean，并打印姓名。

输出窗口显示了姓名：张三

<img src='springBoot2-03-dependency-management\ecf2dd48-34c0-4cbb-a754-1df8081f7209.jpg'>

## 通过Component扫描注册Bean

1. 创建组件类

<img src='springBoot2-03-dependency-management\4c8023fd-c7c9-47f1-a05a-17cfefc8f3c9.jpg'>

这里采用注解注入值，使用@Component标记本类，这样可以通过扫描直接注册到容器

2. 配置扫描

<img src='springBoot2-03-dependency-management\4c4f1483-c0a1-4f5e-9d3f-6405cf7975c1.jpg'>

在配置类上添加注解，设置扫描的范围。

<code style='background:#ff3385;color:white;padding:5px;'>注意</code>当不想扫描某些组件时，可以使用excludeFilters：

<img src='springBoot2-03-dependency-management\23ba4112-a1d2-4a83-8101-095786afa407.jpg'>

3. 注入使用

<img src='springBoot2-03-dependency-management\1577e67a-a342-4cb3-b969-43a181277cb6.jpg'>

## 二者有何区别？何时使用Component,何时使用配置类？

一般来说，对于自己设计的Bean，自己有源码的，使用@Component更简单，对于第三方提供的，没有源码，只能通过配置类注册Bean了。

## 依赖注入冲突

当我们采用接口-实现类方式时，存在多个实现类时，自动绑定找不到Bean.（默认基于类型注入）

此时，我们只需要在注入的位置使用@Qualifier注解标记就可以了

<img src='springBoot2-03-dependency-management\60ee5ca3-e7d0-4bfa-920e-37808025b370.jpg'>

### 示例

1. 接口

<img src='springBoot2-03-dependency-management\76fc8a75-f0e0-4dc8-a2a5-1170b0b82eef.jpg'>

2. Dog实现类，注册为Bean

<img src='springBoot2-03-dependency-management\52832a7f-aee9-46aa-bda5-fb810b36f0c0.jpg'>

3. Cat实现类，注册为Bean

<img src='springBoot2-03-dependency-management\70ef0ff4-b745-4e06-ac45-48026faf9c3f.jpg'>

4. 注入使用

<img src='springBoot2-03-dependency-management\b5387e0f-328b-4aad-bf9d-6287a638323c.jpg'>

5. 输出

<img src='springBoot2-03-dependency-management\113b95cd-bcd9-4a1b-888d-3351f88b5330.jpg'>

## 三种注入方式

1. 字段注入（上面已经用到了）

2. 构造器注入

对于没有无参构造函数的Bean，采用构造器注入

<img src='springBoot2-03-dependency-management\8f1dd3d7-9cb5-40e7-8cad-f7ee52858ab7.jpg'>

使用方法类似：

<img src='springBoot2-03-dependency-management\3676da43-c6ba-421d-af10-309265960778.jpg'>

输出

<img src='springBoot2-03-dependency-management\e968fb82-0a48-4084-bb04-ebaeae6e4a68.jpg'>

3. set方法注入

对于有无参构造函数，字段没有注入，可以使用set方法注入

<img src='springBoot2-03-dependency-management\c3f00aae-b259-4969-b89c-46abc2f298a2.jpg'>

输出

<img src='springBoot2-03-dependency-management\70205619-096d-46fd-be19-7c244162f249.jpg'>


## 生命周期介入

对构造后，销毁前进行介入

<img src='springBoot2-03-dependency-management\77003eba-6fe9-494c-990f-ac92759c32fd.jpg'>

使用@PostConstruct @PreDestory注解方法，可以对Bean注册销毁流程介入

可以使用initMethod destoryMethod指定Bean的初始化及销毁方法

<img src='springBoot2-03-dependency-management\9bf63a32-f1a0-48f5-b01d-28e40e3317d6.jpg'>



