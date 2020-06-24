---
title: JavaEE-10-Spring-Bean-Load
date: 2020-06-20 19:49:52
tags: JavaEE
---

## 依赖注入的三种方式

1. 构造器注入

2. set方法注入

3. 接口注入

### 构造器注入

通过类的构造函数注入需要的其他数据及对象

<img src='JavaEE-10-Spring-Bean-Load\1f5925f3-fb16-4399-8492-11ad2a6eb56b.jpg'>

xml描述

<img src='JavaEE-10-Spring-Bean-Load\ee883871-b15e-409e-bde3-12d9379e806f.jpg'>

构造器注入方法简单，但是对参数较多的情况下显得很繁杂。

### set方法注入

使用默认的构造器创建对象，对参数通过set方法注入

<img src='JavaEE-10-Spring-Bean-Load\1251f90c-9e9c-4932-838c-ff37eee8a5c6.jpg'>

### 接口注入

对于外界提供的服务，Spring在使用的时候需要接口注入。例如tomcat管理的数据库连接池资源，Spring通过JNDI获取：

打开tomcat的context.xml文件

<img src='JavaEE-10-Spring-Bean-Load\13dd24c7-54b4-43e9-a8f4-c2508f8ceb52.jpg'>
<img src='JavaEE-10-Spring-Bean-Load\62a52869-1152-4244-94e0-5d5beb123c14.jpg'>

Spring的配置

<img src='JavaEE-10-Spring-Bean-Load\93bd421c-e9f7-4531-9627-a5c883c55adf.jpg'>

## 装配的具体实现

1. xml配置

2. JavaConfig

3. 自动发现及自动装配

一般约定优于配置，优先使用自动装配，其次是JavaConfig，最后是xml

## XML装配

### xml配置文件头

一个xml配置的基本格式：

<img src='JavaEE-10-Spring-Bean-Load\a6538e72-1445-47e5-a072-0427f07dc405.jpg'>

### 装配简单值

通过Set方法直接注入值

<img src='JavaEE-10-Spring-Bean-Load\2d613fbd-22fe-4193-9791-47b58ddaa007.jpg'>

id是Bean的名称

class是Bean的全限定名称

property指的是通过set方法注入

name指的是域的名称

value即注入的值

### 装配对象

将一个Bean装配到另一个Bean里

<img src='JavaEE-10-Spring-Bean-Load\75df32f4-6ede-4185-9cb6-dcff8318dfa5.jpg'>

通过ref指定已经存在的Bean的id

### 装配集合

对于域中存在的集合需要装配：

<img src='JavaEE-10-Spring-Bean-Load\6c6db7c6-3f9f-4724-927d-67193bc7beb3.jpg'>

装配List

<img src='JavaEE-10-Spring-Bean-Load\507196fd-8f11-485c-b90d-7aad38d97a58.jpg'>

装配map

<img src='JavaEE-10-Spring-Bean-Load\2cec3eda-7522-4780-bd81-65467e2a6a58.jpg'>

装配properties

<img src='JavaEE-10-Spring-Bean-Load\4c1d1f83-4118-4b6f-8f10-3931b7724ff7.jpg'>

装配set

<img src='JavaEE-10-Spring-Bean-Load\4b38ab87-ff77-4264-b122-745804156f2b.jpg'>

装配数组

<img src='JavaEE-10-Spring-Bean-Load\ff6218a0-2dc2-4c22-beab-14a3a6dddd65.jpg'>

### 装配复杂对象

角色对象

<img src='JavaEE-10-Spring-Bean-Load\d7a5d401-47b1-45fe-8d1e-14423bee598f.jpg'>

用户对象

<img src='JavaEE-10-Spring-Bean-Load\927be890-9d85-4d4d-ac13-aaebd6bac409.jpg'>

复杂对象

<img src='JavaEE-10-Spring-Bean-Load\3fc307c2-e801-4041-bcb9-cfdcc0807026.jpg'>

装配

<img src='JavaEE-10-Spring-Bean-Load\08584157-2dc8-4608-85d7-992c7887d0a7.jpg'>
<img src='JavaEE-10-Spring-Bean-Load\11078aa8-7090-40f3-8229-f72d7efa9066.jpg'>

使用ref标签指定已经存在的Bean对象，bean属性指向已存在的Bean的id

## 组件扫描与自动装配

### 使用@Component注解装配

<img src='JavaEE-10-Spring-Bean-Load\42d2bb8d-f080-4eec-8cec-451dad1b0dcd.jpg'>

通过value指定Bean的名称。

通过@Component标记为Bean

通过@Value注解注入值

在相同包下创建配置类，开启包扫描：

<img src='JavaEE-10-Spring-Bean-Load\1fcfeeef-3441-4c75-9fe5-abd99673e8b3.jpg'>

创建AnnotationConfigureApplicationContext对象管理Bean：

<img src='JavaEE-10-Spring-Bean-Load\36dead9b-a304-43a6-a6fd-5778f5b9c1f1.jpg'>

### 通过basepackages指定所在包

<img src='JavaEE-10-Spring-Bean-Load\9af78e5c-0a8f-495d-b4a0-df4427b3eec5.jpg'>

### 使用@AutoWired自动装配

通过@AutoWired注解的域，Spring将自动注入进来对象

<img src='JavaEE-10-Spring-Bean-Load\adb93fd1-a218-4ab5-911d-e39550901ce5.jpg'>

对于找不到的对象，会报错，可以通过required属性指定false解决

<img src='JavaEE-10-Spring-Bean-Load\cda54d83-e0fd-4952-87eb-676866c7939e.jpg'>

但此时，会容易出现空指针异常

与此同时@AutoWired可以注解到set方法、构造函数上

<img src='JavaEE-10-Spring-Bean-Load\a0ffdf09-2a44-4a51-98ab-cb4a216bb27b.jpg'>

### @Primary与@Qualifier

我们看到类中引用的对象是父接口的对象，便于抽插式替换。当某个接口出现多个实现类的时候，就会出现问题。

解决方式一：

使用@Primary标记某个实现类，优先注入这个实现类的对象

<img src='JavaEE-10-Spring-Bean-Load\6ac4c62e-d111-4661-a95a-e7c6113264ba.jpg'>

解决方式二：

在自动绑定的位置使用@Qualifier指定具体注入的实现类

<img src='JavaEE-10-Spring-Bean-Load\03ba9c6f-018d-48b9-88cd-258ad5ba84b9.jpg'>

### 使用@AutoWired注入带参数的构造函数

<img src='JavaEE-10-Spring-Bean-Load\2160c5a3-1709-426d-9c3e-1efc202158f2.jpg' >

### 通过JavaConfig方式将方法返回值注入为Bean

<img src='JavaEE-10-Spring-Bean-Load\f829838f-64f0-4bd2-a6d1-d559754656d0.jpg'>

@Bean可以注解方法，对于name属性指定Bean的名称，实例是方法的返回值。

### 通过@Bean注解指定创建及销毁方法

<img src='JavaEE-10-Spring-Bean-Load\38ed28da-2125-48ad-aff9-f70e188bf6ca.jpg'>

通过initMethod及destoryMethod指定Bean的初始化及销毁方法。

## 装配的混合使用

将xml配置的Bean加载到配置类中：

<img src='JavaEE-10-Spring-Bean-Load\3b317505-81ae-4c95-b622-71190c74e891.jpg'>

加载其他配置类：

<img src='JavaEE-10-Spring-Bean-Load\1b050dc9-1f8c-4378-a2e6-205b05cee749.jpg'>

xml引入其他xml

<img src='JavaEE-10-Spring-Bean-Load\71b65610-fccb-4d88-8d89-9c39da1064e5.jpg'>

使用xml开启注解：

<img src='JavaEE-10-Spring-Bean-Load\4127f521-a90d-492d-ae60-8e619168a81e.jpg'>

## Profile

### 通过注解

使用@Profile注解指定环境

<img src='JavaEE-10-Spring-Bean-Load\956d3136-0b29-4711-98dc-9f583801846b.jpg'>
<img src='JavaEE-10-Spring-Bean-Load\c9fc44f6-0979-483e-8268-2efdeaee0bd4.jpg'>

### 使用xml指定Profile

<img src='JavaEE-10-Spring-Bean-Load\8cc59a0e-96fa-47db-b0b1-9dab9b8e20f7.jpg'>

也可以只对Beans标签指定

<img src='JavaEE-10-Spring-Bean-Load\7234bf7a-78f9-4545-9b78-3c91559ddc5a.jpg'>

### 启动Profile

1. 测试使用@ActiveProfiles

<img src='JavaEE-10-Spring-Bean-Load\7861cafc-8a8b-4026-b5b9-2ce5fe242c35.jpg'>

2. 配置虚拟机参数spring.profiles.active

<img src='JavaEE-10-Spring-Bean-Load\5bf5885f-7449-459e-92a0-763f52601e35.jpg'>

3. spring mvc环境下，使用contextParam或DispatcherServlet参数设定

<img src='JavaEE-10-Spring-Bean-Load\b5671a9a-e653-49d7-9367-7659c65316e6.jpg'>

<img src='JavaEE-10-Spring-Bean-Load\77f0ceab-d29a-439b-933c-f01695ac22e7.jpg'>

## 加载配置文件

### 注解加载配置文件

<img src='JavaEE-10-Spring-Bean-Load\d20879c8-929e-4489-bc1f-4f774ab0498b.jpg'>

使用PropertySource注解导入配置

通过Environment获取配置

<img src='JavaEE-10-Spring-Bean-Load\f1791c99-5594-4456-a0cc-ab8610e4c924.jpg'>

通过PropertySourcesPlaceHolderConfigurer开启占位符

<img src='JavaEE-10-Spring-Bean-Load\d364d96f-8df2-4c1b-90ef-1457ed61b2a0.jpg'>

通过@Value注入属性值

<img src='JavaEE-10-Spring-Bean-Load\b8017c77-40f0-4c11-9986-c2343156a7d0.jpg'>

### 使用xml引入配置

<img src='JavaEE-10-Spring-Bean-Load\fb58e538-c3c8-4bb7-9b96-93fa2f9a038b.jpg' >

使用context:property-placeholder开启，location指定配置文件

多个配置文件需要加载时，可以使用逗号分隔开，也可以：

<img src='JavaEE-10-Spring-Bean-Load\bedfacd2-4890-416d-ac83-e0e51068c8d8.jpg'>

## 条件化装配

使用@Conditional注解Bean，满足条件才装配

<img src='JavaEE-10-Spring-Bean-Load\116ac573-8280-4875-b543-d56fd5b07a30.jpg'>

条件类实现Condition接口，重写matches方法，根据返回值判断是否装配Bean

<img src='JavaEE-10-Spring-Bean-Load\e9762ffd-0af9-4758-9f22-89c289dc7b26.jpg'>

## Bean的作用域

Spring有四种作用域：

<img src='JavaEE-10-Spring-Bean-Load\998affde-201d-4ca4-9486-2dd7f20686f3.jpg'>

可以使用@Scope注解配置作用域：

<img src='JavaEE-10-Spring-Bean-Load\f4e2a108-5cb2-4271-8284-bb32963b9c02.jpg'>

## SPEL

### 通过SPEL注入字面量

<img src='JavaEE-10-Spring-Bean-Load\70a94b76-55fb-4762-9604-2e37a71a4997.jpg'>

使用#{}注入

### 通过名称注入Bean

<img src='JavaEE-10-Spring-Bean-Load\9f225a98-a847-4f0b-860d-e93b64dec52a.jpg'>

### 静态常量注入

<img src='JavaEE-10-Spring-Bean-Load\f3969325-6e49-4555-9bdb-3ed2bf842904.jpg'>

<img src='JavaEE-10-Spring-Bean-Load\4865618a-ba01-42c6-8a6a-d39b8e02345f.jpg'>

<img src='JavaEE-10-Spring-Bean-Load\9a5dd250-4c8f-4f77-8147-86ba1c204287.jpg' >

### SPEL运算

数值计算

<img src='JavaEE-10-Spring-Bean-Load\0a65e598-9051-4b11-9dad-f80de9e16b7a.jpg'>

连接字符串

<img src='JavaEE-10-Spring-Bean-Load\6cff97c0-2e3d-4996-8130-c1d3d1e5dc0a.jpg'>

布尔运算

<img src='JavaEE-10-Spring-Bean-Load\8275d4f5-2369-4599-a601-5883ed1ca04c.jpg'>

三元运算

<img src='JavaEE-10-Spring-Bean-Load\a485647d-fb66-4f17-ad9e-61f593d57423.jpg'>



