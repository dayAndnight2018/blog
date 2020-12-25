---
title: spring03 Bean高级装配
date: 2020-03-01 19:49:10
tags: spring
---

## 注解设置配置环境

dev环境

<img src='spring03-Advanced-wiring\1124a14b-ef8b-491d-8a5a-4229d679f52f.jpg'>

prod环境

<img src='spring03-Advanced-wiring\fea0b06a-d5f5-4de0-88dc-fa449573555e.jpg'>

也可以对方法进行注解：

<img src='spring03-Advanced-wiring\d8326d58-8fe2-4ff1-9f65-6de4ea55d210.jpg'>

## xml配置环境

<img src='spring03-Advanced-wiring\39c1e8ce-d77d-4c48-bd2f-5370b2dec4cb.jpg'>

对Beans标签进行设置profile属性。

Beans内部可以包含其他Beans：

<img src='spring03-Advanced-wiring\918bcf51-1d6c-4e3f-93b6-6ad2ecc2ead4.jpg'>

## 激活Profile

在测试时，使用@ActiveProfile注解启动指定配置

<img src='spring03-Advanced-wiring\8f3352a1-1d68-4734-adad-d09f82084bb9.jpg'>

有多种方式实现配置设置：

* 作为DispatcherServlet的初始化参数；
* 作为Web应用的上下文参数；
* 作为JNDI条目；
* 作为环境变量；
* 作为JVM的系统属性；
* 在集成测试类上，使用@ActiveProfiles注解设置。

## 条件化创建Bean

<img src='spring03-Advanced-wiring\2c0137c1-df9c-4c92-8bad-e31a833584f8.jpg'>

使用@Conditional注解配置Bean方法用于决定释放创建Bean到spring中，所指定的类需要实现Condition接口，重写matches方法：

<img src='spring03-Advanced-wiring\ae91e41f-180f-4d66-8382-e9b0600e3db6.jpg'>

当matches方法返回true，配置激活，否则配置不激活。

## qualifier与primary

采用自动装配时，如果出现某接口的<code style='background:#ff3385;color:white;padding:5px;'>实现类有多个</code>，将会出现问题。使用primary将会<code style='background:#ff3385;color:white;padding:5px;'>优先</code>采用标记的Bean。

当采用<code style='background:#ff3385;color:white;padding:5px;'>自动扫描</code>的方法时：

<img src='spring03-Advanced-wiring\be40cc4d-4aff-437c-ac31-fe80883bd8e7.jpg'>

对component进行标记

还可以对<code style='background:#ff3385;color:white;padding:5px;'>javaConfig</code>方法进行标记：

<img src='spring03-Advanced-wiring\81eb2556-9f7a-4d04-9c50-d28a00131796.jpg'>

对<code style='background:#ff3385;color:white;padding:5px;'>xml配置</code>进行标记：

<img src='spring03-Advanced-wiring\dff2ae93-c682-4c97-8aef-b0695a31ea31.jpg'>

也可以使用@qualifier标记注明注入的实际实现类：

<img src='spring03-Advanced-wiring\e56657d0-fb31-42d6-acf1-840db63c6f9e.jpg'>

## Bean的作用域

* 单例（Singleton）：在整个应用中，只创建bean的一个实例。
* 原型（Prototype）：每次注入或者通过Spring应用上下文获取的时候，都会创建一个新的bean实例。
* 会话（Session）：在Web应用中，为每个会话创建一个bean实
例。
* 请求（Rquest）：在Web应用中，为每个请求创建一个bean实
例。

### 自动绑定设置Bean的周期

使用@Scope注解标记自动扫描式Bean

<img src='spring03-Advanced-wiring\5d950547-88ff-4d57-84fc-b4d4351f5f73.jpg'>

### JavaConfig式Bean设置Bean的周期

<img src='spring03-Advanced-wiring\43773bd7-a127-4c98-8a91-64dcf0ad73b3.jpg'>

### xml式Bean设置Bean的周期

<img src='spring03-Advanced-wiring\bb1d2734-3249-4a1f-812d-8c1b8773ca70.jpg'>

### 注解会话session周期

<img src='spring03-Advanced-wiring\58256ea8-3768-47a1-b52f-4c4502f28f5b.jpg'>

proxyMode有两种：

* 基于接口实现的代理ScopedProxyMode.INTERFACES

* 基于类实现的代理ScopedProxyMode.TARGET_CLASS

### xml配置session周期

<img src='spring03-Advanced-wiring\60d83cb3-ce46-46fe-afe6-cc9d94972cb7.jpg'>

设置<code style='background:#ff3385;color:white;padding:5px;'>scope</code>属性，并使用scoped-proxy配置代理模式，<code style='background:#ff3385;color:white;padding:5px;'>默认是类模式</code>，可以改为接口：

<img src='spring03-Advanced-wiring\b008b43f-f3aa-4b08-9b20-c89de04220db.jpg'>

设置proxy-target-class设置为<code style='background:#ff3385;color:white;padding:5px;'>false</code>即可改为<code style='background:#ff3385;color:white;padding:5px;'>接口代理</code>模式。

aop的前缀：

<img src='spring03-Advanced-wiring\f2dcec33-68d4-423c-96f1-3ccfcb28e5b6.jpg'>

## 运行时值注入

我们知道字面值可以通过xml、javaConfig注入，但是带来了硬编码的问题：

java Config:

<img src='spring03-Advanced-wiring\af74c1f7-b1c3-45f8-92b5-be164a3aaefd.jpg'>

xml:

<img src='spring03-Advanced-wiring\7ac5e01e-d757-40db-a6ee-9c818f82154c.jpg'>

假如我们有个配置文件：

<img src='spring03-Advanced-wiring\00657686-0d79-4c3b-b7ea-81e94e97ec3d.jpg'>

可以@PropertyResource获取配置文件，加载到Environment，获取属性使用：

<img src='spring03-Advanced-wiring\4d1e3db7-0105-411f-8b85-9d5063c61236.jpg'>

## spring占位符注入

Spring支持使用占位符注入字面值：

1. 使用占位符，需要配置PropertySourcesPlaceholderConfigurer:

java Config:

<img src='spring03-Advanced-wiring\84202fa7-bb30-4cbb-bc12-c7c1c7a84b16.jpg'>

xml:

<img src='spring03-Advanced-wiring\20925dd6-4a86-4a11-9462-3639398aab4a.jpg'>

2.占位符注入

xml:

<img src='spring03-Advanced-wiring\ba4637c6-6de8-4b44-9e77-e8e12258bddd.jpg'>

自动绑定：

<img src='spring03-Advanced-wiring\c4171c34-a982-457b-bfba-d8dbb0826e16.jpg'>


## Spring表达式语言

1. SpEL表达式要放到“#{ ... }”之中

2. 属性占位符需要放到“${ ... }”之中

表达式符号：

<img src='spring03-Advanced-wiring\f06d52fb-366f-4daa-a91d-c6f17e348c96.jpg'>

表达式示例：

<pre style='background:#e6e6e6;padding=10px;'>

//常量
#{1}
#{3.14159}
#{9.87E4}
#{'Hello'}
#{false}

//当前时间
#{T(System).currentTimeMillis()}

//获取bean的属性
#{sgtPeppers.artist}

//获取bean的方法
#{artistSelector.selectArtist()}
#{artistSelector.selectArtist()?.toUpperCase()}

//运算符
#{2 * T(java.lang.Math).PI * circle.radius}
#{T(java.lang.Math).PI * circle.radius ^ 2}
#{disc.title + ' by ' + disc.artist}
#{counter.total == 100}
#{scoreboard.score > 1000 ? "Winner!" : "Loser"}
#{disc.title ?: 'Rattle and Hum'}

//正则匹配
#{admin.email matches '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.com'}

//集合
#{jukebox.songs[4].title}
#{jukebox.songs[T(java.lang.Math).random() * jukebox.songs.size()].title}
#{'This is a test'[3]}

//查询过滤
#{jukebox.songs.?[artist eq 'Aerosmith']}
//首个匹配
#{jukebox.songs.^[artist eq 'Aerosmith']}
//最后匹配
#{jukebox.songs.$[artist eq 'Aerosmith']}

//投影
#{jukebox.songs.![title]}

//环境变量
#{systemProperties['disc.title']}

</pre>

对于静态方法或常量需要使用T:

<img src='spring03-Advanced-wiring\cfd4d75c-a349-4ea6-8843-ab402933b606.jpg'>

通过spring表达式注入配置字面值：

自动装配：

<img src='spring03-Advanced-wiring\1ec19800-eeac-4e78-ba6f-9f9af5ecbee8.jpg'>

xml:

<img src='spring03-Advanced-wiring\c070836e-909d-4a38-a6f8-de4f610544c2.jpg'>

