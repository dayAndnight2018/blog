---
title: spring02 绑定Bean
date: 2020-03-01 15:28:39
tags: spring
---

## 如何注册Bean？

1. 在XML中进行显式配置：通过xml配置文件注册Bean

2. 在Java中进行显式配置：通过java配置类注册Bean

3. 隐式的bean发现机制和自动装配：让spring自己去扫描（配合注解使用）


## 发现机制

发现机制就是Bean<code style='background:#ff3385;color:white;padding:5px;'>扫描机制</code>

1. 我们先来创建一个接口，表示CD:

<img src='spring02-Wiring-beans\e39447f3-9cca-4593-8593-bbeee49a23bc.jpg'>

2. 然后给出一种实现：

<img src='spring02-Wiring-beans\da0f5453-79e7-4967-a951-8dd33f04a2e7.jpg'>

我们把这个类进行了<code style='background:#ff3385;color:white;padding:5px;'>@Component</code>标记，这就告诉spring，他就是一个Bean

3. 在相同的包下，我们创建了一个配置类，扫描这个配置类所在的包及所有子包里的Bean。

<img src='spring02-Wiring-beans\2cd29d83-a440-47f9-a5c0-7e928186ccbf.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>@Configuration</code>表示这是一个配置类

<code style='background:#ff3385;color:white;padding:5px;'>@ComponentScan</code>表示开启Bean扫描机制

4. 然后可以进行测试了：

<img src='spring02-Wiring-beans\33301175-60c4-4673-9428-d1580b8f879f.jpg'>

@ContextConfiguration配置了对包扫描范围进行设定的那个配置类。

@Autowired实现自动绑定。

为Bean<code style='background:#ff3385;color:white;padding:5px;'>设置别名</code>：

<img src='spring02-Wiring-beans\ffc361e3-207b-40f8-80eb-c48dcd4c83d2.jpg'>

可以设置<code style='background:#ff3385;color:white;padding:5px;'>配置类</code>所在的位置：

<img src='spring02-Wiring-beans\ca29213c-8984-48e5-87c8-4e01df9a1fd6.jpg'>

## 自动装配

使用<code style='background:#ff3385;color:white;padding:5px;'>@Autowired</code>可以实现自动绑定，前面绑定了域，构造器也是可以的：

<img src='spring02-Wiring-beans\87401b8f-b9b1-4630-a212-1c9e86742905.jpg'>

setter方法也是可以的：

<img src='spring02-Wiring-beans\72142139-13cf-44a2-9946-fcd4f8a2c9d7.jpg'>

但是@Autowired有个缺点，如果Bean找不到，会抛出异常，为了避免，我们可以设置：

<img src='spring02-Wiring-beans\6e61e103-65e3-465a-a13d-330e8f4a20fe.jpg'>

设置required=false则说明，我不是非要找到这个Bean,你找不到不用跟我说。但是会带来其他风险，那就是空指针。

## Java Config

### 创建Bean

使用<code style='background:#ff3385;color:white;padding:5px;'>@Bean</code>注解一个方法，它的返回值就可以作为Bean注册到spring

<img src='spring02-Wiring-beans\427890fa-d2f8-41f2-afe5-4a8aeed89607.jpg'>

默认情况下，这个Bean的名称就是方法名称，我们可以为其重命名：

<img src='spring02-Wiring-beans\f28d709b-318d-4c74-953a-d1ec0428f10e.jpg'>

### 装配Bean

可以通过<code style='background:#ff3385;color:white;padding:5px;'>构造器</code>实现装配：

<img src='spring02-Wiring-beans\f05ee1d2-650b-4a03-963b-24fdc2cd1bbc.jpg'>

也可以通过<code style='background:#ff3385;color:white;padding:5px;'>参数</code>注入：

<img src='spring02-Wiring-beans\c599fc95-f151-4230-b187-8ea329f8c587.jpg'>

使用<code style='background:#ff3385;color:white;padding:5px;'>setter方法</code>注入：

<img src='spring02-Wiring-beans\fbc1c386-9d7c-4ea6-9ad9-d888da574ff7.jpg'>

## 使用xml文件配置Bean

### Bean文件规范

<img src='spring02-Wiring-beans\6a345622-5f96-4394-b310-0577f42dc8b8.jpg'>

### 创建一个Bean

<img src='spring02-Wiring-beans\71fb6444-e252-4147-af00-1de36cb12bc3.jpg'>

通过Bean标签创建一个Bean,class是Bean的<code style='background:#ff3385;color:white;padding:5px;'>全限定名称</code>，用来唯一获得Bean的位置

可以为Bean设置一个<code style='background:#ff3385;color:white;padding:5px;'>名称</code>：

<img src='spring02-Wiring-beans\6fb32f7b-768c-48a9-b2d8-e894cf70c056.jpg'>

id表示Bean的名称

### 使用构造器注入

使用<constructor-arg />构造器注入：

<img src='spring02-Wiring-beans\697b11a9-e120-45c8-bbab-2b9830f388e1.jpg'>

ref是引用的其他Bean(通过id名称)

### 使用构造器注入字面值

假如存在这样的Bean,怎么注入值呢？

<img src='spring02-Wiring-beans\a734495d-75e5-409a-9107-846bedbba5a2.jpg'>

使用<constructor-arg />的value字段设置字面值：

<img src='spring02-Wiring-beans\039e9d21-58b9-40d6-a8e9-1a8bc723a469.jpg'>

### 使用构造器注入集合

对于List这样的集合呢？

<img src='spring02-Wiring-beans\99bba038-b1c6-45e5-8e3c-1b6320f196af.jpg'>

可以注入null

<img src='spring02-Wiring-beans\e110e2a9-bf05-4a62-8288-60d87011f284.jpg'>

可以注入值：

<img src='spring02-Wiring-beans\9a5c8931-dc73-4434-a8de-d7e37fa14886.jpg'>

使用标签实现List集合的字面值注入

如果是对象，可以引用已经存在的Bean：

<img src='spring02-Wiring-beans\fa1ca96b-1413-4d6b-a66e-e2cb8da932af.jpg'>

对Set来说，用法类似，但是不允许重复：

<img src='spring02-Wiring-beans\d5a8079d-a020-461b-aa31-09edb39f49e7.jpg'>

### 通过setter方法注入

通过property标签实现setter方法注入：

<img src='spring02-Wiring-beans\81d97000-1fd0-4e40-a526-39e64884ca79.jpg'>

name指的是域的名称，ref是引用的已存在的Bean，字面值也可以使用value

注入字面值或集合的方法与构造器注入类似：

<img src='spring02-Wiring-beans\323bfc05-8cf1-456d-bde0-160d754cee36.jpg'>

## 在Java Config中加载Java Config

假设我们分离了这个配置：

<img src='spring02-Wiring-beans\e85bb101-f274-4d57-a575-e0228b55ee61.jpg'>

因为在另外一个Java Config类中用到了这个Bean,所以要使用@Import引入这个Bean

<img src='spring02-Wiring-beans\d9bc320c-6f2e-4605-9f92-3cbdbb12bc4a.jpg'>

另外一种高级做法就是将两个配置类再另外一层高级配置类引入到一起：

<img src='spring02-Wiring-beans\bd6e8b08-5593-4bee-b4bb-6926da59695c.jpg'>

## 在Java Config中加载xml

<img src='spring02-Wiring-beans\1af814d4-ea1f-4dd5-88b8-0ef7108b0cde.jpg'>

@ImportResource用于加载指定的xml配置文件，将Bean引入。

## 在XML配置中引用JavaConfig

在xml文件中，通过Bean的方式引入javaConfig所配置的Bean

<img src='spring02-Wiring-beans\3775de2c-ed5e-41d6-8fc7-cf8f60b5f99c.jpg'>

对于引用其他xml，可以通过import标签引入：

<img src='spring02-Wiring-beans\b72a97a6-a5b2-412a-838c-bf6a4567af60.jpg'>

## 通过xml开启扫描

<img src='spring02-Wiring-beans\80f6ddb2-f622-458f-9b7f-da43ca7b5fa0.jpg'>

使用component-scan开启扫描