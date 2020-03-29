---
title: java21 反射
date: 2020-03-01 09:53:20
tags: java
---

## java.lang.Class

可以调用实例的getClass()方法获取Class对象，也可以直接使用.class:

<img src='java21-Reflection\734edc18-1b3b-411c-a341-a0225ae01df1.jpg'>

相关方法：


<pre style='background:#e6e6e6;padding=10px;'>

//反射获取
public static Class<?> forName(String className) throws ClassNotFoundException

//获取公共构造器
public java.lang.reflect.Constructor<?>[] getConstructors() throws SecurityException

//获取指定的公共构造器
public java.lang.reflect.Constructor<T> getConstructor(Class<?>...parameterTypes) throws NoSuchMethodException,SecurityException

//获取公共域
public java.lang.reflect.Field[] getFields() throws SecurityException

//获取指定公共域
public java.lang.reflect.Field getField(String fieldName) throws NoSuchFieldException, SecurityException

//获取本类公共域
public java.lang.reflect.Field[] getDeclaredFields() throws SecurityException

//获取本类指定公共域
public java.lang.reflect.Field getDeclaredField(String fieldName) throws NoSuchFieldException, SecurityException

//获取公共方法
public java.lang.reflect.Method[] getMethods() throws SecurityException

//获取指定公共方法
public java.lang.reflect.Method getMethod(String methodName, Class<?>... parameterTypes) throws NoSuchFieldException, SecurityException

//获取本类公共方法
public java.lang.reflect.Method[] getDeclaredMethods() throws SecurityException

//获取本类指定公共方法
public java.lang.reflect.Method getDeclaredMethod(String methodName, Class<?>... parameterTypes) throws NoSuchMethodException, SecurityException

</pre>

## 反射法创建对象

1. 使用class对象的newInstance方法

<img src='java21-Reflection\043f067d-f926-433c-9e2d-71b76aea0480.jpg'>

2. 获取构造器，使用构造器调用newInstance方法

<img src='java21-Reflection\a590dd3a-53c7-4ed9-8486-b44fdeb49687.jpg'>

## 反射法创建数组

使用Array的newInstance方法：

<img src='java21-Reflection\fdf0d9e1-f89f-4b72-9119-4e2aab427e79.jpg' >

设置指定位置的值（Array的set方法）：

<img src='java21-Reflection\a18d03cf-9e27-4df3-bf31-fba5f1f68095.jpg'>

获取指定位置的值（Array的get方法）：

<img src='java21-Reflection\179b04e7-8a64-4b31-831e-92568c8dc363.jpg'>

## 域

获取的域，可以获取或设置值：

getXXX (getByte,getInt, getShort, getLong···）

<img src='java21-Reflection\156d702d-7ee4-45a9-bc80-707e63501bcf.jpg'>

setXXX (setBoolean, setChar, setFloat···）

<img src='java21-Reflection\6b122ec3-82ad-4b68-b6ba-5cb635102e2d.jpg'>

## 方法

获取方法名称：

<img src='java21-Reflection\80650428-d467-4b61-8b27-09d4f48c171a.jpg'>

获取访问修饰符：

<img src='java21-Reflection\2e22d374-577f-4ce4-90a0-d60b26288a42.jpg'>

获取声明这个方法的类（可能来自于继承）：

<img src='java21-Reflection\cfd05863-50f3-4902-9409-53a333d14ba3.jpg'>

获取返回值类型：

<img src='java21-Reflection\8aa9920e-e796-48ed-ae8e-3f0ad8373c41.jpg'>

获取参数类型：

<img src='java21-Reflection\2d22c7d2-2f53-4216-8687-7e9bf3ed2b83.jpg'>

执行方法：

<img src='java21-Reflection\ddb72d6c-1e56-46bc-8236-59f6244c4c08.jpg'>

静态方法的第一个参数可以为null。

