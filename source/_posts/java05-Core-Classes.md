---
title: java05 核心类库
date: 2020-02-21 13:10:45
tags: java
---

## java.lang.Object

这个是Java的核心类，表示对象，任何类都直接或间接地继承着这个类。

<pre style='background:#e6e6e6;padding=10px;'>

//克隆方法，重写这个方法的类可以实现对象的复制。
protected Object clone()

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//对象的相等比较方法。
public boolean equals(Object obj)

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//资源释放的方法
protected void finalize()

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//获取类型的方法
public final Class getClass()

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//hashcode方法
public int hashCode()

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//类的描述方法
public String toString()

</pre>

## java.lang.String

字符串是存储文本的一种引用数据类型，同时，它是不可变的，进而是线程安全的。

字符串创建：

<img src='java05-Core-Classes\081eade3-4f91-401e-9b61-60ac9a15661e.jpg'>

等价于：

<img src='java05-Core-Classes\ebb445d9-d07a-4898-b47f-87397a039ea5.jpg'>

两种创建对象的方法有所区别：

使用new关键字创建的对象，将<code style='background:#ff3385;color:white;padding:5px;'>始终创建新的对象</code>，而直接赋值的方法将会从<code style='background:#ff3385;color:white;padding:5px;'>缓存池</code>获取已经存在的字符串对象。

### 字符串比较

<img src='java05-Core-Classes\0713ac84-9fad-4052-9904-9706bb8c3b37.jpg' >

返回的结果是相等的，s1和s2指向的是相同的地址。

<img src='java05-Core-Classes\9809a401-f79e-432a-a6f0-f5b7a725078c.jpg'>

返回的结果是不等，因为new始终创建新的对象，地址不同。

只比较文本内容，可以使用equals方法：

<img src='java05-Core-Classes\5dd979db-7e21-42e5-9d92-585fc4795854.jpg'>

防止空指针，可以使用：

<img src='java05-Core-Classes\f3805075-922d-4bcf-967b-24ec7a026377.jpg'>

### String字面量

<img src='java05-Core-Classes\bfd13fdf-a7d1-4c05-930e-4bdbe79ca776.jpg'>

这种换行方式是无法编译的，不允许这样换行。

使用+号进行连接是可以的：

<img src='java05-Core-Classes\d89cd4ca-0e97-452e-8597-4109c0373499.jpg'>

一个基本类型和一个String可以连接，一个对象与String连接会调用toString方法进行连接。

<img src='java05-Core-Classes\a6c8b92e-f118-401e-9ac4-09f796459d7a.jpg'>

### 转义字符

<img src='java05-Core-Classes\9482b9be-80fd-4546-b107-d92c971bc290.jpg'>

一些无法输入的字符可以使用转义字符表示。

### String可以用于switch方法

<img src='java05-Core-Classes\0e44bc35-2895-477e-8dcc-df3a7731f1c5.jpg'>

从java7开始，switch语句的条件可以使用String。

### String的构造函数

String的构造函数一定会创建新的对象，可以创建空的字符串、复制字符串、字符数组或字节数组。

<pre style='background:#e6e6e6;padding=10px;'>

//创建空字符串
public String()

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//创建副本
public String(String original)

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//字符数组
public String(char[] value)

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//字节数组
public String(byte[] bytes)

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//指定字节数组及编码方式
public String(byte[] bytes, String encoding)

</pre>

### String类的方法

<pre style='background:#e6e6e6;padding=10px;'>

//获取指定位置的字符
public char charAt(int index)

//连接字符串
public String concat(String s)

//相等判断
public boolean equals(String anotherString)

//结尾字符判断
public boolean endsWith(String suffix)

//字符位置判断
public int indexOf(String substring)

//从指定位置查找
public int indexOf(String substring, int fromIndex)

//最后一次出现
public int lastIndexOf(String substring)

public int lastIndexOf(String substring, int fromIndex)

//字符串截取
public String substring(int beginIndex)

public String substring(int beginIndex, int endIndex)

//替换字符
public String replace(char oldChar, char newChar)

//获取长度
public int length()

//判空
public boolean isEmpty()

//正则匹配分割
public String[] split(String regEx)

//开始判断
public boolean startsWith(String prefix)

//转换为字符数组
public char[] toCharArray()

//转小写
public String toLowerCase()

//转大写
public String toUpperCase()

//去除空格
public String trim()

</pre>

一些静态构造方法：

<img src='java05-Core-Classes\7c8d93d8-9c5f-44bb-8edf-e172f0f6e8a8.jpg'>

格式输出：

<img src='java05-Core-Classes\2ab1388d-2dac-484f-b6f6-2d97c429bf64.jpg'>

## StringBuilder & String Buffer

String Buffer是线程安全的，内部采用了同步措施，StringBuilder是非同步的，效率高。

### StringBuilder构造器

可以使用无参构造，或指定空间，或传入字符串。
<img src='java05-Core-Classes\b0b44b10-6f4a-4aac-b777-bde98537b22e.jpg'>

默认的容量是<code style='background:#ff3385;color:white;padding:5px;'>16</code>，超出大小再进行扩容。如果你预先知道空间占用，请预先指定容量。

### StringBuilder的方法

<pre style='background:#e6e6e6;padding=10px;'>

//获取容量
public int capacity()

//获取长度
public int length()

//追加字符串，可以使用很多基本类型数据
public StringBuilder append(String string)

//在指定位置插入字符串
public StringBuilder insert(int offset, String string)

//转换为字符串
public String toString()


</pre>

## 包装类型

<table cellpadding='8' border='1' style='background:#EAF2D3;text-align:center'>
<tr>
&nbsp;<td>
基本数据类型
&nbsp;</td>
&nbsp;<td>
包装类型
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
int
&nbsp;</td>
&nbsp;<td>
Integer
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
byte
&nbsp;</td>
&nbsp;<td>
Byte
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
short
&nbsp;</td>
&nbsp;<td>
Short
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
long
&nbsp;</td>
&nbsp;<td>
Long
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
float
&nbsp;</td>
&nbsp;<td>
Float
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
double
&nbsp;</td>
&nbsp;<td>
Double
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
boolean
&nbsp;</td>
&nbsp;<td>
Boolean
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
char
&nbsp;</td>
&nbsp;<td>
Character
&nbsp;</td>
</tr>

</table>

### Integer

最大值与最小值：

<pre style='background:#e6e6e6;padding=10px;'>

Integer.MIN_VALUE

Integer.MAX_VALUE

</pre>

构造器:

<pre style='background:#e6e6e6;padding=10px;'>

public Integer(int value)

public Integer(String value)

</pre>

字符串转换：

<pre style='background:#e6e6e6;padding=10px;'>

public static int parsetInt(String string)

public static String toString(int i)

</pre>

### Boolean

构造器：

<pre style='background:#e6e6e6;padding=10px;'>

public Boolean(boolean value)

public Boolean(String value)

</pre>

获取boolean:

<pre style='background:#e6e6e6;padding=10px;'>

public boolean booleanValue()

</pre>

字符串转换：

<pre style='background:#e6e6e6;padding=10px;'>

public static Boolean valueOf(String string)

public static String toString(boolean boolean)

</pre>

### Character

构造器：

<pre style='background:#e6e6e6;padding=10px;'>

public Character(char value)

</pre>

获取char:

<pre style='background:#e6e6e6;padding=10px;'>

public char charValue()

</pre>

数字判断：

<pre style='background:#e6e6e6;padding=10px;'>

public static boolean isDigit(char ch)

</pre>

大小写转换：

<pre style='background:#e6e6e6;padding=10px;'>

public static char toLowerCase(char ch)

public static char toUpperCase(char ch)

</pre>

## Arrays

一组相同的数据可以存储在数组里，数组的大小可以使用length获得，同时大小不可变。数组可以根据索引读写数据，索引从0开始。

没有元素的数组称为null:

<img src='java05-Core-Classes\de9134a7-140d-433e-b5b2-f3d860e2926f.jpg'>

数组的定义：

<img src='java05-Core-Classes\04f47d2c-207d-45b5-9518-6daec85902a7.jpg'>

不创建对象是不会分配内存空间的，可以这样创建对象：

<img src='java05-Core-Classes\6248cf32-4575-47cb-9464-df56e9301786.jpg'>

直接赋值，不用new关键字也可以创建对象：

<img src='java05-Core-Classes\97d4af7c-8920-4000-8898-128495ea178d.jpg'>

### 数组的迭代

可以使用for循环和索引迭代：

<img src='java05-Core-Classes\b7d1e97d-e131-4c39-9b4b-7a4a1ddce8e4.jpg' >

可以使用foreach循环：

<img src='java05-Core-Classes\d8e2f452-9664-4ce6-8a5d-72aa8569cc06.jpg'>

示例如下:

<img src='java05-Core-Classes\4a5cf78c-afb9-456a-8729-ba1a584266c4.jpg'>

### 数组的复制

for循环迭代读写：

<img src='java05-Core-Classes\5c3bdee7-b9b0-4084-b934-9b3d7267a6cd.jpg'>

使用Arrays的copyOf方法：

<img src='java05-Core-Classes\a8f7d299-5d9f-4b8d-b8e6-79b30e6d7d27.jpg'>

支持多种类型及泛型：

<img src='java05-Core-Classes\6361e788-082d-4c37-b654-906d5bed693a.jpg'>

当原数组是<code style='background:#ff3385;color:white;padding:5px;'>null</code>或者newLength为<code style='background:#ff3385;color:white;padding:5px;'>负值</code>，会<code style='background:#ff3385;color:white;padding:5px;'>抛出异常</code>。newLength指的是新数组的大小，可以<code style='background:#ff3385;color:white;padding:5px;'>大于</code>原数组，复制原数组的元素靠前插入，多余的位置补充默认值；可以<code style='background:#ff3385;color:white;padding:5px;'>等于</code>原数组，原样复制；可以<code style='background:#ff3385;color:white;padding:5px;'>小于</code>原数组，只复制前newLength个元素。

copyOfRange可以复制指定范围的元素：

<img src='java05-Core-Classes\a639119d-d7b4-448c-980f-17745c5a285e.jpg'>

## java.lang.Class

jvm创建对象的时候，会自动创建一个同类型的Class类的对象，所有相同的类的实例共享同一个class对象。

<img src='java05-Core-Classes\aaaf816b-9537-4f92-9ec8-ce0be05a66ed.jpg'>

可以使用class对象的getName方法获取全限定名称:

<img src='java05-Core-Classes\a2f64b02-975b-40b5-8326-05c1bdcf1fd8.jpg'>

根据全限定名称创建对象：

<img src='java05-Core-Classes\bb7e5c6e-7f6e-4cf4-a9db-b2ac6abd7b0d.jpg'>

示例：

<img src='java05-Core-Classes\1ed6bfb5-f43c-4abb-80f0-82b229f90352.jpg'>

## java.lang.System

三个流：

<img src='java05-Core-Classes\b6889dd7-1275-45eb-a427-a3562ddef058.jpg' >

可以通过out输出到控制台：

<img src='java05-Core-Classes\fa04b82c-6b50-4753-87fc-c50174203d0d.jpg'>

也可以使用println函数，自动换行。

输出错误信息：

<img src='java05-Core-Classes\6a0b2ce6-54cf-4e38-bafb-bdbb75f0f517.jpg'>

可以读取控制台输入：

<img src='java05-Core-Classes\01be6142-16f5-49f7-8e4b-18003d97ab00.jpg'>

可以使用arraycopy复制数组：

<img src='java05-Core-Classes\705950db-e69d-4eb8-a105-8eff1b275f0f.jpg'>

exit退出：

<img src='java05-Core-Classes\6d742284-9c2b-402e-b8b0-0937fe45fb81.jpg'>

0表示正常退出。

获取当前的时间：

<img src='java05-Core-Classes\674d0b59-7054-48b4-93fe-18a17193fb7a.jpg'>

一个更精准的时间表示：

<img src='java05-Core-Classes\81764b63-d232-479c-8df4-424af28a9c21.jpg'>

获取属性：

<img src='java05-Core-Classes\3afbcb0a-9a13-4c94-a8f5-698914798200.jpg'>

<img src='java05-Core-Classes\3995a06b-cab5-45d1-8640-c68458b3a56f.jpg'>

设置属性：

<img src='java05-Core-Classes\df3faa3d-4976-468c-b8d1-985504f12097.jpg'>

示例：

<img src='java05-Core-Classes\aeab86fb-4a8d-4cb1-a994-c91b56291008.jpg'>

获取所有系统属性：

<img src='java05-Core-Classes\d422e897-ee3a-4ba0-9bc4-3a8827946c24.jpg'>

## java.util.Scanner

可以对System.in进行包装，获取控制台输入：

<img src='java05-Core-Classes\4a841218-e5a9-4ad3-bb07-15bef25cbdf3.jpg'>

## 装箱与拆箱

装箱与拆箱是自动进行的，指的是基本数据类型和包装类的自动转换。

装箱：

<img src='java05-Core-Classes\822b2cc3-a69b-4b4a-a60c-93a4527a7aee.jpg' >

拆箱：

<img src='java05-Core-Classes\f61ad021-8259-4712-96bc-3f750ccdcec3.jpg'>

## 不定个数参数

<img src='java05-Core-Classes\48fc6552-d93c-416b-ab17-9c7d0785bba1.jpg'>

与数组参数类似

## 打印参数

可以使用format方法标准化字符串格式（String或：PrintStream均有）：

<img src='java05-Core-Classes\e0060425-5297-4d04-817f-db3fb7915119.jpg'>




