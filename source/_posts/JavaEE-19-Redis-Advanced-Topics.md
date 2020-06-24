---
title: JavaEE-19-Redis-Advanced-Topics
date: 2020-06-23 09:06:48
tags: JavaEE
---

## Redis事务

### Redis事务指令

<img src='JavaEE-19-Redis-Advanced-Topics\b437183d-5e81-4043-9852-7ed34abe9d72.jpg'>

Redis的multi指令后，指令会添加到队列，直到exec，discard用于回滚。

### 使用实例

通过SessionCallback实现批量指令执行，同时使用execute执行SessionCallback指令

<img src='JavaEE-19-Redis-Advanced-Topics\3c17762d-fa70-4145-9d87-f50f2ada0809.jpg'>

### 事务回滚

自动事务回滚是在指令格式出错情况下回滚，若因其他原因，如incr指令使用浮点数操作，此类不会导致回滚，前后指令正常执行。

### watch监控事务

使用watch监视字段

<img src='JavaEE-19-Redis-Advanced-Topics\3fba7df4-bbf5-4f0a-8f9a-a80da27ac788.jpg'>

采用CAS的方式实现，但不存在ABA问题。

若字段没有发生变化，将会提交

<img src='JavaEE-19-Redis-Advanced-Topics\4822e0ef-42b9-47b9-8f66-4a0acc7acc14.jpg'>

若字段被修改，自动回滚

<img src='JavaEE-19-Redis-Advanced-Topics\bf3164c1-c3a0-447e-ae42-9bbea7cb889b.jpg'>

## 流水线

流水线采用批量执行指令的方式，提高效率。

<img src='JavaEE-19-Redis-Advanced-Topics\b013d773-35f9-4d4d-85a0-853b685f4035.jpg'>

Spring使用RedisTemplate执行时，差异不大。

<img src='JavaEE-19-Redis-Advanced-Topics\070e7f9a-2bbb-4681-8abf-259ad40b772f.jpg'>

## 发布与订阅

观察者模式的实现

<img src='JavaEE-19-Redis-Advanced-Topics\8c530925-68e2-4e55-83d4-cfd3472b982e.jpg'>

1. client1监听频道

<pre style='background:#e6e6e6;padding=10px;'>
SUBSCRIBE channel
</pre>

2. client2发布消息

<pre style='background:#e6e6e6;padding=10px;'>
publish channel message
</pre>

### java实现

1. 消息订阅者

<img src='JavaEE-19-Redis-Advanced-Topics\131c81f4-e7b8-4268-bf9c-f24779798322.jpg'>

2. 消息订阅容器

<img src='JavaEE-19-Redis-Advanced-Topics\20893852-3163-47c5-8ee6-43eafeb8db6f.jpg'>

3. 消息发布测试

<img src='JavaEE-19-Redis-Advanced-Topics\8c1b94f0-0ad2-46d2-91b6-a34ad843022f.jpg'>

## Redis超时指令

<img src='JavaEE-19-Redis-Advanced-Topics\3564b87e-9de8-414f-b85d-7a42fe2247a4.jpg'>
<img src='JavaEE-19-Redis-Advanced-Topics\abe68ebf-d98f-42c2-bce3-6f634ea6c2d0.jpg'>

expire(String key, int timeout, TimeUnit unit)指定有效时间

expire(String key,Date date)指定过期时间

persist(String key)永久有效

## Lua脚本

Redis支持Lua脚本，可以弥补Redis的计算性能

### 使用指令

<img src='JavaEE-19-Redis-Advanced-Topics\666bf7a7-3694-438e-a4e2-36ca6e9dbdc2.jpg'>

如：

<pre style='background:#e6e6e6;padding=10px;'>
eval "return 'hello Lua' " 0
</pre>

<pre style='background:#e6e6e6;padding=10px;'>
eval "redis.call('set',KEYS[1],ARGV[1])" 1 lua-key lua-value
</pre>

### 执行脚本

1. 加载脚本

<pre style='background:#e6e6e6;padding=10px;'>
script load "return 'hello lua'"
</pre>

返回脚本的sha值

2. 执行脚本

<pre style='background:#e6e6e6;padding=10px;'>
evalsha sha key-num [key1 key2···] [param1 param2···]
</pre>

<img src='JavaEE-19-Redis-Advanced-Topics\a96c9b3f-355e-4b16-91b8-39c9b0140e1e.jpg'>

### 使用Spring执行脚本

<img src='JavaEE-19-Redis-Advanced-Topics\88935773-cb5f-47b9-84fd-f0056a6589e9.jpg'>

jedis.eval(String script)执行脚本

jedis.eval(String script, int keyNum, String ... keyParam)带参数脚本

jedis.scriptLoad(String script)加载脚本

jedis.evalsha(String sha, int keyNum, String ... keyParam)执行

### 使用Spring执行对象脚本

<img src='JavaEE-19-Redis-Advanced-Topics\ba6a6942-a257-45de-adfb-73372c79db2b.jpg'>

使用DefaultRedisScript配置

setScriptText(String script)设置脚本内容

getSha1()获取签名

setResultType(Class class)设置返回值类型

execute(DefaultRedisScript script, RedisSerializer paramSerializer, RedisSerializer resultSerializer, List keyList, object param)执行

### 执行lua文件

<img src='JavaEE-19-Redis-Advanced-Topics\22a88ac0-f411-4a91-a862-bcebe33d9ce2.jpg'>
