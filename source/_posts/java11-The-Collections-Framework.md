---
title: java11 集合
date: 2020-02-22 09:45:26
tags: java
---

## 一张图认识集合的关系

集合用于分组处理对象。

<img src='java11-The-Collections-Framework\7a0985f1-46c8-4aa0-8a61-424c5af6d082.jpg'>

Collection的继承接口是List / Queue / Set

Map用于存储键值对。

ArrayList是List的非同步实现，Vector是同步实现。

SortedMap是排序了的Map

HashMap是一种基于哈希算法的键值对实现

Comparator用于实现排序

Iterator用于实现迭代

## Collection

Collection用于存储不同数据类型的数据，同时大小可变。

<table cellpadding='8' border='1' style='background:#EAF2D3;text-align:center'>
<tr>
&nbsp;<td>
方法
&nbsp;</td>
&nbsp;<td>
备注
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
add
&nbsp;</td>
&nbsp;<td>
添加元素
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
addAll
&nbsp;</td>
&nbsp;<td>
添加其他Collection里的元素
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
clear
&nbsp;</td>
&nbsp;<td>
移除所有元素
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
size
&nbsp;</td>
&nbsp;<td>
获取元素个数
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
isEmpty
&nbsp;</td>
&nbsp;<td>
判空
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
toArray
&nbsp;</td>
&nbsp;<td>
转换为数组
&nbsp;</td>
</tr>


</table>

## List and ArrayList

List是有序的集合，使用索引操作元素。

### 添加元素

<img src='java11-The-Collections-Framework\1853c8bc-ea6b-4ab0-9dcd-135034b3b819.jpg'>

可以在末尾插入元素，插入成功返回true，否则false

### 插入元素

<img src='java11-The-Collections-Framework\e3352fc9-c386-436f-8d8e-b4cd9549c57e.jpg'>

允许在指定的位置插入元素

### 修改某位置的元素

<img src='java11-The-Collections-Framework\6ce21df3-97cb-4f88-a244-2cc22fc2f4cf.jpg'>

修改指定位置的元素

### 移除元素

<img src='java11-The-Collections-Framework\d4892479-6209-40e6-a16e-a28c935c2d9a.jpg'>

移除指定位置的元素

### 创建对象

<img src='java11-The-Collections-Framework\1956dec7-9c00-424b-8a4c-a02bd710925b.jpg'>

也可以指定容量：

<img src='java11-The-Collections-Framework\605ab093-cbc6-4bda-bbf9-f7052e8ceff9.jpg'>

### 查找元素

<img src='java11-The-Collections-Framework\401c4685-e036-44a6-aeeb-cdb937ee7b9b.jpg'>

### 附加方法

<img src='java11-The-Collections-Framework\d10be918-3dfc-4658-a65c-046f88ad441f.jpg'>


## Collection元素迭代

### 使用迭代器

<img src='java11-The-Collections-Framework\21048bda-6e9e-49dc-9839-c03f48efb434.jpg'>

### Foreach

<img src='java11-The-Collections-Framework\97e57903-ff50-46ea-94d9-411e80465cb8.jpg'>

## Set and HashSet

Set不允许出现两个相同的对象插入。

<img src='java11-The-Collections-Framework\2e3b508a-c51f-45ba-ac8a-e8558e0b897b.jpg'>

支持多个null

不维护插入次序，相比LinkedHashSet及TreeSet速度要快。

## Queue

先进先出序列：

<table cellpadding='8' border='1' style='background:#EAF2D3;text-align:center'>
<tr>
&nbsp;<td>
方法
&nbsp;</td>
&nbsp;<td>
备注
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
offer ★
&nbsp;</td>
&nbsp;<td>
区别于add,插入失败不会抛出异常
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
remove
&nbsp;</td>
&nbsp;<td>
移除队头元素
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
poll ★
&nbsp;</td>
&nbsp;<td>
移除队头元素，不会抛出异常
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
element
&nbsp;</td>
&nbsp;<td>
获取队头元素
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
peek ★
&nbsp;</td>
&nbsp;<td>
获取队头元素，但不会抛异常
&nbsp;</td>
</tr>


</table>

示例：

<img src='java11-The-Collections-Framework\10c37da0-be7d-47c6-a4d8-87f8f86d14ed.jpg' >


## 类型转换

<img src='java11-The-Collections-Framework\a4862048-31c8-454b-8939-116e912d5316.jpg'>

均接受父类对象进行构造，因此可以转换。

Queue转Array List：

<img src='java11-The-Collections-Framework\07630ed3-fd95-4183-882c-debf27f1ff38.jpg'>

ArrayList转Hash Set：

<img src='java11-The-Collections-Framework\e19ab2b4-f8d9-4632-a7ab-88afbd213ab0.jpg'>

## Map and HashMap

### 插入元素

<img src='java11-The-Collections-Framework\cbe301c0-451a-4740-bac6-9652996b1d72.jpg'>

以键值对形式插入。

插入另一个Map中的元素：

<img src='java11-The-Collections-Framework\5d1ac712-6eef-4b2e-92c2-ce00d324d4a0.jpg'>

### 移除元素

<img src='java11-The-Collections-Framework\b82a9d67-5e0b-421a-9b3f-1fc59431e4d4.jpg'>

根据键移除元素。

### 查询元素

<img src='java11-The-Collections-Framework\6e63ffc5-c5b5-4c50-a7ff-33f16e4754c8.jpg'>

根据键获取元素。

### 迭代

keys获取键set

values获取值集合

entrySet获取键值对，getKey获取键,getValue获取值

HashMap和HashTable的区别是前者非同步，后者同步。

<img src='java11-The-Collections-Framework\1ca1e0cc-2c81-4fda-8c3d-f600b9633095.jpg'>

## java.lang.Comparable

Arrays提供了一个静态比较方法：

<img src='java11-The-Collections-Framework\6fea8441-d9df-4801-ab4b-b0b87566e391.jpg'>

对于自定义类的比较，需要实现接口：

<img src='java11-The-Collections-Framework\d81af4a2-b976-4944-89c2-987051123a64.jpg'>

重写CompareTo方法：

<img src='java11-The-Collections-Framework\42ff7494-b9cb-41de-8c3c-5add23d41b5b.jpg'>

使用：

<img src='java11-The-Collections-Framework\e1f02509-3ed7-4ead-86e9-ecb4a544d39b.jpg'>

## Comparator

对于Comparable，提供了一种排序方法。

对于不同的排序方式实现，需要使用Comparator。重写compare方法即可：

<img src='java11-The-Collections-Framework\6a7b1350-7e34-468a-88a9-7ada3350cd95.jpg'>

示例1：

<img src='java11-The-Collections-Framework\934a3db6-454a-40f4-93f3-dc06f5a91c12.jpg'>

示例2：

<img src='java11-The-Collections-Framework\5154bc08-543e-4766-851a-71215ffa2b3c.jpg'>

使用时，传入Comparator具体实现即可：

<img src='java11-The-Collections-Framework\9bc3d361-26f6-4ddc-85ea-145e6246a117.jpg'>

also,

<img src='java11-The-Collections-Framework\1ee5896a-a99b-461c-98d0-0fa52a64f3f3.jpg'>



