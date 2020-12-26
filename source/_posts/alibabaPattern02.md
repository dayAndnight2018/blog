---
title: 阿里巴巴开发手册02  常量定义
date: 2020-01-05 23:35:12
tags: alibaba
---

## 常量定义

1. `不允许`出现魔法值，直接作为常量使用

<img src='alibabaPattern02\d3fd5dce-8233-4236-8322-610f96af15b8.jpg' style='margin:30px;display:block' alt='title'>

2. long类型的值定义时，`需要`使用大写L

3. 对常亮`要求`使用多个常量类分别管理

4. 常量的复用

跨应用复用：常量放置在两方的类库中

应用内共享：放置在某类库中

子工程内部共享：放在在子工程的constant目录下

包内共享：放置在当前包的constant目录下

类内共享：类内部使用private static final 定义

5. 若变量范围较小，包含固定的几个值，如第一季度，第二季度，第三季度，第四季度，则使用枚举
<img src='alibabaPattern02\f45019bd-5af1-4182-85b5-5349b63e3d83.jpg' style='margin:30px;display:block' alt='title'>