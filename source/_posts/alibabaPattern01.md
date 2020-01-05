---
title: 阿里巴巴开发手册01 命名风格
date: 2020-01-05 22:44:31
tags: alibaba
---

## 命名风格

1. <code style='background:#ff3385;color:white;padding:5px;'>禁止</code>命名以_或$开始或结束

2. <code style='background:#ff3385;color:white;padding:5px;'>禁用</code>拼音、中文命名方式

3. 类名<code style='background:#ff3385;color:white;padding:5px;'>需要</code>首字母大写，驼峰命名。除DO、BO、DTO、VO、AO、PO、UID之外

4. 方法名称、参数名称、成员变量、局部变量<code style='background:#ff3385;color:white;padding:5px;'>需要</code>统一使用驼峰命名。

5. 常量<code style='background:#ff3385;color:white;padding:5px;'>需要</code>用全大写，单词之间用下划线连接

6. 抽象类<code style='background:#ff3385;color:white;padding:5px;'>需要</code>以Abstract开头，异常以Exception结尾，测试类以测试类名称开始，以Test结尾

7. 数组符号与类型<code style='background:#ff3385;color:white;padding:5px;'>需要</code>紧挨着，如：int[] array

8. POJO类中的布尔类型，<code style='background:#ff3385;color:white;padding:5px;'>禁止</code>以is开头

9. 包名<code style='background:#ff3385;color:white;padding:5px;'>需要</code>保持小写，单数语义，类名<code style='background:#ff3385;color:white;padding:5px;'>可以</code>使用复数

10. <code style='background:#ff3385;color:white;padding:5px;'>禁止</code>不规范的缩写

11. <code style='background:#ff3385;color:white;padding:5px;'>需要</code>使用完整的单词组合

12. 模块、接口、类、方法使用设计模式，<code style='background:#ff3385;color:white;padding:5px;'>需要</code>体现出设计模式：OrderFactory、LoginProxy、ResourceObserver

13. 接口类方法上<code style='background:#ff3385;color:white;padding:5px;'>不要</code>添加修饰，<code style='background:#ff3385;color:white;padding:5px;'>避免</code>在接口中定义变量。

14. Service或DAO接口，<code style='background:#ff3385;color:white;padding:5px;'>要求</code>使用xxxService、xxxServiceImpl命名接口和实现类。普通接口，以形容词为接口名称，Translatable接口或AbstractTranslator实现类

15. 枚举<code style='background:#ff3385;color:white;padding:5px;'>要求</code>使用Enum后缀，枚举成员用大写，下划线连接。

16. Service/DAO层命名<code style='background:#ff3385;color:white;padding:5px;'>要求</code>：

获取单个对象用get前缀

获取多个对象用list做前缀，复数形式结尾如：listObjects

获取数量count做前缀

插入用insert做前缀

删除用delete做前缀

修改用update做前缀

17. 领域数据模型命名<code style='background:#ff3385;color:white;padding:5px;'>要求</code>：

数据对象使用DO作后缀

数据传输对象以DTO做后缀

视图对象以VO做后缀



