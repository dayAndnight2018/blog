---
title: java08 数字与日期
date: 2020-02-21 20:42:50
tags: java
---

## 数字转换

可以使用包装类对字符串进行转换：

<img src='java08-Numbers-and-Dates\aff10aec-de35-46f0-a060-504240ad3abf.jpg'>

<table cellpadding='8' border='1' style='background:#EAF2D3;text-align:center'>
<tr>
&nbsp;&nbsp;<td>
包装类
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
解析方法
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
Byte
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
parseByte
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
Short
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
parseShort
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
Integer
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
parseInteger
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
Long
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
parseLong
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
Float
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
parseFloat
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
Double
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
parseDouble
&nbsp;&nbsp;</td>
</tr>

</table>

## NumberFormat

<img src='java08-Numbers-and-Dates\d7aa545e-7b26-4bbc-b2c1-661f4f796b94.jpg'>

使用Locale指定区域：

<img src='java08-Numbers-and-Dates\5451f997-3721-4d84-9d1a-06a41ba53a5b.jpg'>

使用NumberFormat可以格式化：

<img src='java08-Numbers-and-Dates\974b6b1f-9243-4f81-96b4-ffd09005e93b.jpg'>

## parse转换

<img src='java08-Numbers-and-Dates\48b6b6f8-91ad-4116-b666-64722415959a.jpg' >

NumberFormat对象获取到number类型

## The java.lang.Math

<pre style='background:#e6e6e6;padding=10px;'>

//e
Math.E

//圆周率
Math.PI

//绝对值
public static double abs(double a)

//反余弦
public static double acos(double a)

//反正弦
public static double asin(double a)

//反正切
public static double atan(double a)

//余弦
public static double cos(double a)

//指数
public static double exp(double a)

//对数
public static double log(double a)

public static double log10(double a)

//最大值
public static double max(double a, double b)

//最小值
public static double min(double a, double b)

</pre>

## java.util.Date

构造器：

<img src='java08-Numbers-and-Dates\4eef6829-889c-43f8-94c8-a58957c93b23.jpg'>

比较两个时间先后：

<img src='java08-Numbers-and-Dates\c872cfbf-41c6-4d59-932e-fec3d7068b09.jpg'>

getDate, getMonth, getYear方法已过时

## java.util.Calendar

构造器：

<img src='java08-Numbers-and-Dates\5c411482-7f34-4a58-ae14-50c070d472a7.jpg'>

可以获取时间，是一个Date对象：

<img src='java08-Numbers-and-Dates\791fdfbd-4538-49fe-8fc7-1e79c43e98c2.jpg'>

对年月日的获取：

<img src='java08-Numbers-and-Dates\48ee1d52-7276-4849-b3c3-fa4f9892dff6.jpg'>

Calendar.YEAR

Calendar.MONTH

Calendar.DATE

Calendar.HOUR

Calendar.MINUTE

Calendar.SECOND

Calendar.MILLISECOND

对于月份，需要特别注意，0代表1月。

可以使用setTime对date进行构造：

<img src='java08-Numbers-and-Dates\7d364947-4adc-466a-b2f7-40b1cab712ca.jpg'>

对指定的域设置：

<img src='java08-Numbers-and-Dates\226d1298-5ebb-4139-9185-df2532c9092a.jpg'>

也可以使用重载函数：

<img src='java08-Numbers-and-Dates\f4f37205-1c2f-4b52-bffd-28388a185438.jpg'>

## 日期格式化

<table cellpadding='8' border='1' style='background:#EAF2D3;text-align:center'>
<tr>
&nbsp;&nbsp;<td>
格式
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
结果
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
DateFormat.SHORT
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
12/2/11
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
DateFormat.MEDIUM
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Dec 2, 2011
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
DateFormat.LONG
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
December 2, 2011
&nbsp;&nbsp;</td>
</tr>

<tr>
&nbsp;&nbsp;<td>
DateFormat.FULL
&nbsp;&nbsp;</td>
&nbsp;&nbsp;<td>
Friday, December 2, 2011
&nbsp;&nbsp;</td>
</tr>

</table>

静态构造器：

<img src='java08-Numbers-and-Dates\2749668b-0cd4-4e91-a98e-13e6296eed77.jpg'>

格式化获取字符串：

<img src='java08-Numbers-and-Dates\86cb05ba-5c49-4790-9ca6-a594b84ebd5f.jpg'>

解析日期：

<img src='java08-Numbers-and-Dates\78aa5456-2f3c-4c5e-a6e9-dee4b28841dc.jpg'>

## SimpleDateFormat

可自定义格式进行格式化：

<img src='java08-Numbers-and-Dates\a6f0d9af-ba1a-405f-940d-029b63a681ea.jpg'>

使用字符串模式：

<img src='java08-Numbers-and-Dates\0ea6aaad-b65d-4f6a-ac40-db54801ede0f.jpg'>

例如：

dd/MM/yyyy

dd-MM-yyyy

MM/dd/yyyy

yyyy-MM-dd

格式化：

<img src='java08-Numbers-and-Dates\9326dab4-e5f0-437e-bc66-c372b01ee364.jpg'>

解析：

<img src='java08-Numbers-and-Dates\cafcb530-cee1-4ed2-a526-85d9f7ce581b.jpg'>

## LocalDate、LocalTime、LocalDateTime(Java 8)

### 构造

三者都是不可变的：

<img src='java08-Numbers-and-Dates\9942b1e7-5444-49a6-9ccf-899bc8c6de43.jpg'>

采用now()构造实例

也可以通过of()方法获取实例：

<img src='java08-Numbers-and-Dates\3c65e93a-3d38-416f-91ba-2cea88959ec1.jpg'>

参数取值范围：

<img src='java08-Numbers-and-Dates\89c3af28-dce4-4e77-9238-fa62e82c9c2f.jpg'>

使用示例：

<img src='java08-Numbers-and-Dates\7a378ce7-fe29-49b7-a517-8b2f094fc5a2.jpg'>

### 格式化及解析

使用DateTimeFormatter格式化：

<img src='java08-Numbers-and-Dates\1e5664c0-45cf-4f53-b04d-5c01e76cf7c8.jpg'>

解析器：

<img src='java08-Numbers-and-Dates\58ee4b7e-a8d7-431d-af74-3a8505cf02d9.jpg'>

使用示例：

<img src='java08-Numbers-and-Dates\7fe2e8b2-b935-4c01-93cf-55363afb631b.jpg'>
<img src='java08-Numbers-and-Dates\637e0369-9e50-40a0-bc7a-deddb3342374.jpg'>






