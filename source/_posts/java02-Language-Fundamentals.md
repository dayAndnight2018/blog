---
title: java02 语言基础
date: 2020-02-18 12:08:37
tags: java
---

## 常用的java标点符号

<img src='java02-Language-Fundamentals\fe269627-bfed-4f39-b940-bcbc82a7aed3.jpg'>

## 八大基本数据类型

<img src='java02-Language-Fundamentals\e4f8600a-4bdc-4442-829a-0c2107aab57a.jpg'>

其中，byte,short, int, long, float, double表示数值，其位数和数值范围如表所示。

以byte为例做出解释：

占用8位，也就是2^8 = 256个数值,前128个数值为-128——-1，0占一个，剩余127个为正数。所以它的范围是-128——127

在选择数据类型的时候，要尽可能的<code style='background:#ff3385;color:white;padding:5px;'>小</code>，因为大范围的数值类型分配的空间更大，会造成内存的<code style='background:#ff3385;color:white;padding:5px;'>浪费</code>。

byte, short, int, long用于存储整数，float和double用于存储小数。

char 类型允许存储一个Unicode字符

Boolean用于存储两种结果：true 或者 false

## 变量

在Java中存在两种变量：

1. 引用变量：存储的是对象的引用

2. 基本变量：存储的基本数据类型

变量除了具有指定的数据类型外，还具有名称（标识符），其命名规则必须遵循以下几种要求：

1. 变量名称可以是有限长度的字母、数字、下划线、美元符号组成，需要以字母或下划线开头。

2. 变量名称不得与关键字重复

3. 变量名符合作用域要求。

以下是Java的关键字列表：

<img src='java02-Language-Fundamentals\a3c64e8d-26fc-4fff-bb00-85d00de9e114.jpg' >

## 变量的定义格式

类型 + 变量名称 + ";"

<img src='java02-Language-Fundamentals\e72ed210-af26-4b78-970a-0d7117dad16b.jpg' >

分别定义了byte类型的x、int类型的rowCount、char类型的c

也可以在一行中定义多个相同类型的变量：

<img src='java02-Language-Fundamentals\b6680e0c-bc4d-4f65-8528-766d31104f0a.jpg' >

在变量声明的同时，也可以完成赋值：

<img src='java02-Language-Fundamentals\3910afb2-3a36-4e25-b7b2-a536d7f0e2aa.jpg'>

## 常量

常量指的是一旦赋值不再更改的变量。常常用final修饰定义，全部使用大写，使用下划线分隔：

<img src='java02-Language-Fundamentals\7633e333-f92b-4317-a4ef-9c3c22e67afb.jpg'>

## Integer字面值

分为十进制，八进制，十六进制，二进制字面值，默认是十进制，八进制以0开头，十六进制以0X开头，二进制以0B开头。

<pre style='background:#e6e6e6;padding=10px;'>

int a = 100;
int b = 0100;
int c = 0X100;
int d = 0B100;

</pre>

对于合适的数据类型，不要超过其数值范围。

在定义long类型的数据时，需要在数值末尾使用L作为备注标记。

<img src='java02-Language-Fundamentals\6961d166-e05a-4b9a-9327-20ff37d3bbed.jpg' >

对于较大的数值，可以使用下划线分隔表示，不影响数值大小，且放置位置任意。（从Java 7开始）

<img src='java02-Language-Fundamentals\169d0faa-511f-48db-80cc-a4f734877a82.jpg' >

## 浮点类型字面值

包括float和double两种，分别为32位和64位。分为整数部分 、小数部分、E指数部分。默认是double类型，float类型需要以F作为标记。

以下均为有效的float浮点型字面值表示：

<img src='java02-Language-Fundamentals\3b7aa78c-d1c4-4c83-8dd5-92092dc42fc5.jpg' >

以下均为有效的double浮点型字面值表示：

<img src='java02-Language-Fundamentals\49dd3158-4507-4e5f-947a-eedbac37edf4.jpg' >

## 布尔类型字面值

只有true和false两种：

<img src='java02-Language-Fundamentals\d8876135-9f3d-47c8-a002-ea0fecadfd23.jpg' >

## 字符类型字面值

字符类型的字面值包含单个引号表示的单个Unicode字符：

<img src='java02-Language-Fundamentals\ab7f5eca-59f2-48da-8323-531796f4dbb5.jpg' >

或者某些转义字符：

<img src='java02-Language-Fundamentals\b6e13caf-d4af-4375-b9e6-6d833a6dc15e.jpg'>

对于键盘无法输入的特殊ASCII字符，可以使用\uxxxx方式表示：

例如，\u2299表示

<img src='java02-Language-Fundamentals\4bf22b19-22d1-4a01-b4cf-34612aff6f65.jpg' >

## 基本数据类型转换

自动转型：

以下几种数据类型的转换是自动的，

<img src='java02-Language-Fundamentals\d2db3944-b88e-4c4d-95d0-f5a7480f5ccb.jpg' >

无需在代码中做任何额外的工作：

<img src='java02-Language-Fundamentals\1da1369e-84f1-4c05-a45a-efe562b9892a.jpg' >

强制转型：

以下数据类型的转换容易出现精度损失：

<img src='java02-Language-Fundamentals\5bb1ec56-2ceb-42e2-8427-39d7984dfc82.jpg' >

没有精度损失：

<img src='java02-Language-Fundamentals\de223479-b56e-44e0-ab0e-11e1efa65e74.jpg' >

损失精度：

<img src='java02-Language-Fundamentals\afdc21f4-0d83-4e86-ac54-58df9687e5d8.jpg' >

## 操作符

java常见的操作符：

<img src='java02-Language-Fundamentals\6489416e-4e8b-47f7-97f7-4a5cfc6947a9.jpg' >

### 一元操作符

1. “-” 表示相反数。

<img src='java02-Language-Fundamentals\f042feab-b605-4856-be34-18b18d41a808.jpg' >

2. “+”表示正数

<img src='java02-Language-Fundamentals\6cd696dc-e69f-41e8-8770-bff4372af431.jpg'>

3. “++”表示自增1

<img src='java02-Language-Fundamentals\0e7797fd-e917-46ed-88fa-11d4f227cc4d.jpg'>

<img src='java02-Language-Fundamentals\7995a187-a7d2-4985-91d4-5580ef6eeb4a.jpg'>

<img src='java02-Language-Fundamentals\7f2ba6c8-78b6-4473-bd01-7230add2407f.jpg'>

++在前先做自增，后参与表达式运算。++在后，先参与表达式运算，后自增。

4. “--”自减1

<img src='java02-Language-Fundamentals\37f60070-e0ff-4c3e-8d9a-d4a1f31c26f9.jpg'>

<img src='java02-Language-Fundamentals\b1fa1ea6-4b79-4162-b041-88454131669f.jpg'>

区别同自增运算符。

5. “！”非运算

<img src='java02-Language-Fundamentals\d5e1e471-eec0-4b9e-afad-883750c2bafd.jpg'>

6. “~”按位取反

<img src='java02-Language-Fundamentals\e4ce0951-6c79-41f7-a60e-03a6df06f17b.jpg'>

### 算术操作符

1. “+”求和

<img src='java02-Language-Fundamentals\998f06cd-f15c-4951-97fb-0caf4260fac4.jpg' >

2. “-”求差

<img src='java02-Language-Fundamentals\59f05262-f6e8-48e1-b350-2d98b6ae7710.jpg'>

3. “*”求积

<img src='java02-Language-Fundamentals\389d1446-c8f3-408b-8c2d-ffaf1999ef25.jpg'>

4. “/”求商

<img src='java02-Language-Fundamentals\47e13e00-6d3c-4ffa-bdcd-13b0f61c7446.jpg'>

<img src='java02-Language-Fundamentals\dd5c5bf0-b166-4a57-ad5b-8b71c03d6107.jpg'>

5. “%”取余

<img src='java02-Language-Fundamentals\465562ae-49d4-412f-b394-f2a605ed93af.jpg'>

6. “==” 、“！=”相等判断

<img src='java02-Language-Fundamentals\865c46eb-5ad6-4395-b8ff-5af9122f1cb8.jpg'>

<img src='java02-Language-Fundamentals\a0178f80-6981-4360-9513-8f44cbe7fe75.jpg'>

### 关系运算符

<  <=  >  >= 所得结果均是Boolean类型

### 逻辑运算符

“&&”表示并且

<img src='java02-Language-Fundamentals\948309d3-f3b0-446e-8ee2-bb9b9ba43bee.jpg' >

“||”表示或者

<img src='java02-Language-Fundamentals\16d97a50-85b7-4ad8-81b8-09b0e248f336.jpg'>

“？：”表示三元运算

<img src='java02-Language-Fundamentals\0854e07f-0a8d-45d4-9aa5-46172adc3021.jpg'>

“&”与、“|”或、"^"异或

<img src='java02-Language-Fundamentals\a6ff2622-77c0-42c1-b9a0-fd99651e0728.jpg'>

### 位运算符

“<<”左移

<img src='java02-Language-Fundamentals\f331b50e-ab98-4558-92b6-545d3126c615.jpg' >

“>>”右移

有符号右移，补符号位

<img src='java02-Language-Fundamentals\b709373b-51f5-44c2-86ca-7700f8ea241c.jpg'>

“>>>”无符号右移

无符号右移，最左侧补0

“&”位与、"|"位或、"^"异或

<img src='java02-Language-Fundamentals\3524caaf-19cd-49d7-8ce1-46fb665fcc7d.jpg'>

### 赋值运算符

<img src='java02-Language-Fundamentals\63e53d0a-2610-4163-a39e-40969787e22c.jpg' >

上述赋值运算符属于复合型赋值运算符，例如：

<img src='java02-Language-Fundamentals\59b9b2fd-3cdb-49aa-bfe7-f20b588e8107.jpg'>


### 类型提升问题

一元运算符，在byte、short、char操作的时候，操作结果是int类型，有类型提升。

<img src='java02-Language-Fundamentals\bf3dd85b-e21d-48a9-a76e-b4bf406623b1.jpg'>

应手动做强转:

<img src='java02-Language-Fundamentals\9eab97d0-02f1-472f-adf6-5bbc94b8c81d.jpg' >

对于二元操作符：

1.如有任一操作数是byte或short类型，类型自动提升为int，操作结果也为int 

2.如有任一操作数是double类型，类型自动提升为double，操作结果也为double

3. 如有任一操作数是float类型，类型自动提升为float，操作结果也为float

4.如有任一操作数是long类型，类型自动提升为long，操作结果也为long


### 注释

两种注释方式：

1. // code

2. /*  code  */

### 文档注释

对类进行注释：

<img src='java02-Language-Fundamentals\6b066dda-a9f5-4a8f-ab80-6abbd0586704.jpg'>

对方法进行注释：

<img src='java02-Language-Fundamentals\f6cd50d5-68d6-4faa-ad8a-eff58fe8bc77.jpg'>

常用注解：

<img src='java02-Language-Fundamentals\e613fa6e-9d5e-46b5-b954-cd715ddfd7fe.jpg'>

生成文档：

<pre style='background:#e6e6e6;padding=10px;'>
javadoc -d directory xxx.java
</pre>

### 地标注释

// TODO 需要完善

// FIXME 需要补充

// XXX 建议备忘











