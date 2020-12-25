---
title: JavaEE-18-Redis-Data-Structure
date: 2020-06-22 21:21:12
tags: JavaEE
---

## Redis常见数据结构

<img src='JavaEE-18-Redis-Data-Structure\db516e45-cd9d-4096-b168-ae4a9fec9fb8.jpg' >

## 字符串

### 字符串采用键值对存储

<img src='JavaEE-18-Redis-Data-Structure\e3800819-e45e-4a7f-a50a-c866395c5fde.jpg'>

### 常用的指令

<img src='JavaEE-18-Redis-Data-Structure\8289c92a-5f13-4715-baa0-55a32a689a00.jpg'>

### 使用示例

<img src='JavaEE-18-Redis-Data-Structure\0cdbf955-d53d-4a3a-95db-54faf74165a6.jpg'>

redisTemplate.opsForValue().get(String key)读取值

redisTemplate.opsForValue().set(String key, String value)设值

redisTemplate.opsForValue().append(String key, String value)追加值

redisTemplate.opsForValue().getAndset(String key, String value)设值读旧值

redisTemplate.delete(String delete)删除值

### 数值操作指令

<img src='JavaEE-18-Redis-Data-Structure\074c8846-8da7-4838-bb2c-3ec2c66d97a2.jpg'>

* incr key / incrby key val

* decr key / decrby key val

* incrbyfloat key val

不过类似的操作常常使用java代码操作，不常用

<img src='JavaEE-18-Redis-Data-Structure\669e6152-05d2-4b5e-b258-25ad0480a429.jpg'>

## 哈希

### 存储结构

<img src='JavaEE-18-Redis-Data-Structure\3641b579-aa73-4da9-8c72-19e480c7bcd2.jpg'>

### 常用的指令

<img src='JavaEE-18-Redis-Data-Structure\9512440c-6813-48b1-bd7a-f87cbe2ad930.jpg'>

### 使用实例

<img src='JavaEE-18-Redis-Data-Structure\00ce5ab5-53e4-47f7-94ae-327124fa7cb1.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\e690e0d7-17fb-4bf2-9770-d31bd8b6b703.jpg'>

redisTemplate.opsForHash().putAll(String key, Map<String,String>val)赋值

redisTemplate.opsForHash().put(String key, String field, String val)赋值

redisTemplate.opsForHash().hasKey(String key, String field)判断字段存在性

redisTemplate.opsForHash().entries(String key)获取键值对

redisTemplate.opsForHash().values(String key)获取键集合

redisTemplate.opsForHash().keys(String key)获取值集合

redisTemplate.opsForHash().multiGet(String key, List<String> fields)获取批量字段

redisTemplate.opsForHash().putIfAbsent(String key, String field, String val)不存在就赋值

redisTemplate.opsForHash().delete(String key, String ... fields)批量删除字段

<img src='JavaEE-18-Redis-Data-Structure\16341be0-0f36-4f44-9807-5ad59cf5ef02.jpg' >

redisTemplate.opsForHash().get(String key, String field)获取

## 链表

### 采用双向指针的链表

<img src='JavaEE-18-Redis-Data-Structure\fb3eebee-cf16-46cf-b6e6-a52dba95175c.jpg'>

### 常用指令

<img src='JavaEE-18-Redis-Data-Structure\d3ce093f-badc-404b-b93a-ddc14e270aa5.jpg'>

### 阻塞指令（并发场景）

<img src='JavaEE-18-Redis-Data-Structure\52c513be-3a34-4eea-be09-b01130988c68.jpg'>

### 使用实例

<img src='JavaEE-18-Redis-Data-Structure\3b210674-fd62-43d5-a3bb-9351b108fb99.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\f8d5d624-fd1d-4071-95d6-17a332a4f180.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\fe3db352-11c7-4076-bfd5-9b9d48eaef1f.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\79ceff00-7265-4d6f-a616-a2b20a68fded.jpg'>

redisTemplate.opsForList().delete(String key)删除list

redisTemplate.opsForList().leftPush(String key, String val);左插

redisTemplate.opsForList().rightPush(String key, String val)右插

redisTemplate.opsForList().leftPushAll(String key, List<String> val)左插集合

redisTemplate.opsForList().leftPushIfPresent(String key, String val);存在则左插

redisTemplate.opsForList().rightPushIfPresent(String key, String val)存在则右插

redisTemplate.opsForList().leftPop(String key)左弹

redisTemplate.opsForList().rightPop(String key)右弹

redisTemplate.opsForList().index(String key, int index)返回指定位置元素

redisTemplate.opsForList().range(String key, int start,int end)返回指定位置范围的元素

redisTemplate.opsForList().size(String key)获取元素数量

redisTemplate.getConnectionFactory().getConnection().lInsert(byte[] key, RedisListCommands.Position pos, byte[] refNode, byte[] newNode)指定元素前/后插入新元素

redisTemplate.opsForList().remove(String key, int count, String val)移除至多count个值为val的元素

redisTemplate.opsForList().set(String key, int index, String val)设置指定位置元素值

<img src='JavaEE-18-Redis-Data-Structure\7f06af70-8d69-4727-8e9f-90facd611872.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\156cf2d7-5c3a-4051-94d6-da6d38e0aa24.jpg'>

redisTemplate.opsForList().leftPop(String key,int timeout, TimeUnit unit)阻塞左弹

redisTemplate.opsForList().rightPop(String key, int timeout,TimeUnit unit)阻塞右弹

redisTemplate.opsForList().rightPopAndLeftPush(String key, String val, int timeout,TimeUnit unit)阻塞右弹左插

## 集合

### 常用指令

<img src='JavaEE-18-Redis-Data-Structure\8e8ff88c-0182-47d6-a793-538967d339e9.jpg' >
<img src='JavaEE-18-Redis-Data-Structure\dd775088-ce3f-41d9-8ef2-d3a5271b5c37.jpg'>

### 使用示例

<img src='JavaEE-18-Redis-Data-Structure\e130fba5-8a2d-4b55-87c1-995a4b7d5434.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\210f2351-e2f0-4323-a144-fa34c960bd46.jpg'>

redisTemplate.boundSetOps(String key).add(String ... vals)批量添加

redisTemplate.OpsForSet().size(String key)大小

redisTemplate.OpsForSet().difference(String key1, String key2)差

redisTemplate.OpsForSet().intersect(String key1, String key2)交

redisTemplate.OpsForSet().union(String key1, String key2)并

redisTemplate.OpsForSet().differenceAndStore(String key1, String key2, String key3)key1、key2差存key3

redisTemplate.OpsForSet().intersectAndStore(String key1, String key2, String key3)key1、key2交存key3

redisTemplate.OpsForSet().unionAndStore(String key1, String key2, String key3)key1、key2并存key3

redisTemplate.OpsForSet().isMember(String key, String val)存在判断

redisTemplate.OpsForSet().members(String key)所有元素

redisTemplate.OpsForSet().pop(String key)随机弹出一个元素

redisTemplate.OpsForSet().randomMember(String key)随机获取一个元素

redisTemplate.OpsForSet().randomMembers(String key，long n)随机获取n个元素

redisTemplate.OpsForSet().remove(String key，String... vals)移除元素

## 有序集合

### 常用指令

<img src='JavaEE-18-Redis-Data-Structure\9d3707be-0155-4665-8571-a40798caa102.jpg' >
<img src='JavaEE-18-Redis-Data-Structure\3b0ba18a-69c9-4091-9813-a3b7e23e0038.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\cb313c6f-8e60-40d2-967d-5ac8a421f44b.jpg'>

### 使用示例

<img src='JavaEE-18-Redis-Data-Structure\54338755-0f66-4b4c-afc3-b55144ff3f38.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\a9c1d5df-0ca8-4c65-b85d-555e980310fd.jpg' >
<img src='JavaEE-18-Redis-Data-Structure\da39244f-5aab-44fa-8c4f-c07ae755bd9c.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\f2302487-0e44-42a2-b3e7-c02910decf7b.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\06e6d0ce-9ea4-4350-a1ec-c9e1af848630.jpg'>
<img src='JavaEE-18-Redis-Data-Structure\54b7ee20-eba5-4892-9eb9-445fad7ac5c5.jpg'>

redisTemplate.OpsForZSet().add(String key, Set<TypedTuple> set)添加集合

redisTemplate.OpsForZSet().zCard(String key)集合大小

redisTemplate.OpsForZSet().count(String key, int low, int high)获取score指定范围的元素

redisTemplate.OpsForZSet().range(String key, int start, int count)获取指定start位置开始的count个元素

redisTemplate.OpsForZSet().rangeWithScores(String key, int low, int high)按分数排序后的集合

redisTemplate.OpsForZSet().intersectAndStore(String key1, String key2, String key3)key1、key2的差集存到key3

redisTemplate.OpsForZSet().rangeByLex(String key, Range range, Limit limit)限制查询

redisTemplate.OpsForZSet().rank(String key, String val)查询排名

redisTemplate.OpsForZSet().remove(String key, String ... vals)移除元素

redisTemplate.OpsForZSet().removeRange(String key, int low, int high)移除排名范围元素

redisTemplate.OpsForZSet().removeRangeByScore(String key, int low, int high)移除分数范围元素

redisTemplate.OpsForZSet().reverseRangeWithScore(String key, int low, int high)按分数范围逆序排序

## 基数

### 类似于最小完全子集

<img src='JavaEE-18-Redis-Data-Structure\e0f725a6-70e3-4383-9399-93eaf0a7e2a4.jpg'>

### 操作实例

<img src='JavaEE-18-Redis-Data-Structure\807b14a7-749a-47a5-bf65-98e023a68870.jpg'>

redisTemplate.OpsForHyperLogLog().add(String key, String val)添加元素

redisTemplate.OpsForHyperLogLog().size(String key)基数大小

redisTemplate.OpsForHyperLogLog().union(String key1, String key2, String key3)key1、key2的并集存到key3














