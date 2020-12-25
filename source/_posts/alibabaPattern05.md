---
title: 阿里巴巴开发手册05 集合处理
date: 2020-01-06 10:11:17
tags: alibaba
---

## 集合处理

1. hashcode与equals

只要重写equals，<code style='background:#ff3385;color:white;padding:5px;'>必须</code>重写hashcode

使用set存储的类，<code style='background:#ff3385;color:white;padding:5px;'>必须</code>重写hashcode和equals

使用自定义对象作为Map的键，<code style='background:#ff3385;color:white;padding:5px;'>必须</code>重写hashcode和equals

2. ArrayList的subList结果<code style='background:#ff3385;color:white;padding:5px;'>不可以</code>强转ArrayList，原集合的元素增加删除均会对子列表的遍历、增加、删除产生异常

3. 使用集合转数组，<code style='background:#ff3385;color:white;padding:5px;'>必须</code>使用toArray(T[] array)，传入的是类型完全一样的数组，大小就是list.size()

4. 使用工具类Arrays.asList()把数组转为集合时，<code style='background:#ff3385;color:white;padding:5px;'>不能</code>使用修改集合的方法（add remove clear）

5. 泛型通配符<? extends T>来接收的数据，不能使用add方法。使用<? super T>接收的数据不能使用get方法。所以，频繁读取的<code style='background:#ff3385;color:white;padding:5px;'>使用</code><? extends T>，频繁插入的<code style='background:#ff3385;color:white;padding:5px;'>使用</code><? super T>

6. 在foreach中<code style='background:#ff3385;color:white;padding:5px;'>禁止</code>remove和add操作，remove<code style='background:#ff3385;color:white;padding:5px;'>需要</code>使用Iterator，如果并发，<code style='background:#ff3385;color:white;padding:5px;'>需要</code>对Iterator加锁

<img src='alibabaPattern05\9c5442aa-1310-4aca-99b2-4162e735e5b9.jpg' style='margin:30px;display:block' alt='title'>

7. Comparator<code style='background:#ff3385;color:white;padding:5px;'>需要</code>满足以下条件：

x，y的比较结果与y, x的比较结果相反

x > y, y > z，则x > z

x = y, 则比较x, z的结果与y, z的结果相同

8. <code style='background:#ff3385;color:white;padding:5px;'>推荐</code>在泛型集合定义时，使用diamond格式

<img src='alibabaPattern05\b5598902-0e50-4ecd-87ac-4f3dce253de1.jpg' style='margin:30px;display:block' alt='title'>

9. <code style='background:#ff3385;color:white;padding:5px;'>建议</code>在集合初始化时，指定大小。Capacity = (存储个数/负载因子) + 1，若不明确，请设置16

10. <code style='background:#ff3385;color:white;padding:5px;'>建议</code>使用EntrySet而不是KeySet对Map集合进行遍历

11. Map集合空值问题

<img src='alibabaPattern05\7ab63e0c-b81a-457a-a06a-e4321ade5d46.jpg' style='margin:30px;display:block' alt='title'>

12. <code style='background:#ff3385;color:white;padding:5px;'>合理利用</code>集合的有序性和稳定性

13. 利用Set的唯一性可以实现快速去重，<code style='background:#ff3385;color:white;padding:5px;'>避免</code>List的contains方法



 