---
title: 阿里巴巴开发手册04 OOP约定
date: 2020-01-06 09:35:29
tags: alibaba
---

## OOP约定

1. 对于静态变量，<code style='background:#ff3385;color:white;padding:5px;'>要求</code>直接使用类名调用

2. 方法重写<code style='background:#ff3385;color:white;padding:5px;'>需要</code>添加@Override注解

3. <code style='background:#ff3385;color:white;padding:5px;'>避免使用</code>可变参数和object类型参数接收

4. 对于被其他地方使用的接口，<code style='background:#ff3385;color:white;padding:5px;'>禁止</code>变更方法签名，如有需要，使用@Deprecated注解注释

5. <code style='background:#ff3385;color:white;padding:5px;'>禁止</code>使用过时的类或方法

6. Object的equals方法容易抛出异常，<code style='background:#ff3385;color:white;padding:5px;'>建议</code>使用常量的equals方法

<img src='alibabaPattern04\217a6cd3-af60-4ea0-88c3-e2cecf90fdca.jpg' style='margin:30px;display:block' alt='title'>

7. <code style='background:#ff3385;color:white;padding:5px;'>推荐</code>使用equals方法判断包装类对象的值

8. 基本数据类型与包装类：

POJO类的属性，使用<code style='background:#ff3385;color:white;padding:5px;'>包装类型</code>

RPC的方法参数与返回值使用<code style='background:#ff3385;color:white;padding:5px;'>包装类型</code>

局部变量使用<code style='background:#ff3385;color:white;padding:5px;'>基本数据类型</code>

9. 对于DO、DTO、VO等POJO类，其定义<code style='background:#ff3385;color:white;padding:5px;'>不要设置</code>属性的默认值

10. 序列号新增属性时，<code style='background:#ff3385;color:white;padding:5px;'>不要修改</code>序列化ID

11. 构造函数中<code style='background:#ff3385;color:white;padding:5px;'>禁止</code>加入业务逻辑，如有必要，放到init方法中

12. POJO类<code style='background:#ff3385;color:white;padding:5px;'>必须</code>带有toString方法

13. 使用String的split方法时，<code style='background:#ff3385;color:white;padding:5px;'>注意避免</code>分隔符为空的时候，划分结果的问题。

<img src='alibabaPattern04\44706ed7-e51f-4938-8913-1397417786cd.jpg' style='margin:30px;display:block' alt='title'>

14. 包含多个构造函数时，<code style='background:#ff3385;color:white;padding:5px;'>按顺序放置在一起</code>，便于阅读，多个同名方法也是

15. 类内方法的<code style='background:#ff3385;color:white;padding:5px;'>定义顺序</code>，公有方法或保护方法->私有方法->getter或setter方法

16. setter方法参数<code style='background:#ff3385;color:white;padding:5px;'>建议</code>使用与成员变量相同的名称，不要添加业务逻辑

<img src='alibabaPattern04\df00936f-8ad5-4752-9306-5449c015ece6.jpg' style='margin:30px;display:block' alt='title'>

17. 循环内的字符串连接，<code style='background:#ff3385;color:white;padding:5px;'>要求</code>使用StringBuilder的append方法

18. final 的使用

不允许继承的类，使用final定义

不允许修改引用的域对象，使用final定义

不允许重写的方法，使用final定义

不允许重新赋值的局部变量，使用final定义

避免上下文重复使用一个变量，使用final可以强制重新定义一个变量

19. <code style='background:#ff3385;color:white;padding:5px;'>谨慎</code>使用Object类的clone方法

20. 类成员与方法访问控制从严

如果不允许外部直接new对象，构造方法<code style='background:#ff3385;color:white;padding:5px;'>需要</code>使用private

工具类<code style='background:#ff3385;color:white;padding:5px;'>禁止</code>出现public或default构造方法

非静态方法与子类共享，<code style='background:#ff3385;color:white;padding:5px;'>必须</code>是protected

非静态方法本类使用，<code style='background:#ff3385;color:white;padding:5px;'>必须</code>是private

静态变量在本类使用，<code style='background:#ff3385;color:white;padding:5px;'>必须</code>是private

如果是静态变量，请<code style='background:#ff3385;color:white;padding:5px;'>考虑</code>final

仅供本类使用的成员方法，<code style='background:#ff3385;color:white;padding:5px;'>必须</code>private



与子类共享的成员方法，<code style='background:#ff3385;color:white;padding:5px;'>必须</code>protected

