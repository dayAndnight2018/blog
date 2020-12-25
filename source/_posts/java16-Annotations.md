---
title: java16 注解
date: 2020-02-29 11:35:17
tags: java
---

注解就是一种标记作用的特性。

## 注解的类型

注解类型是 一种<code style='background:#ff3385;color:white;padding:5px;'>模板</code>，注解是注解模板的<code style='background:#ff3385;color:white;padding:5px;'>具体实例</code>。

注解类型可以包含键值对，没有键值对的叫<code style='background:#ff3385;color:white;padding:5px;'>标记注解</code>，有单个键值对的叫<code style='background:#ff3385;color:white;padding:5px;'>单值注解</code>。

## 注解的使用

不带参数：

<img src='java16-Annotations\85551201-69c0-4f08-83d5-63ed991b4bbd.jpg'>

带参数：

<img src='java16-Annotations\ed377e91-6510-4fca-bad3-7b2db24c3a6e.jpg'>

不带参数使用示例：

<img src='java16-Annotations\d1e77ed3-6a17-419c-a249-22a3bdb515a4.jpg'>

带参数使用示例：

<img src='java16-Annotations\c6419b07-8952-42b7-b317-d783a4e47ced.jpg'>

对于单值注解，可以省略键：

<img src='java16-Annotations\fa8eb52d-254f-424f-8f79-fb7806810f48.jpg'>

等价于，

<img src='java16-Annotations\78f0c90e-406b-4b82-bf6c-5c7784f218ee.jpg'>

## 标准注解

Override,Deprecated, and SuppressWarnings是java5添加的标准注解

### Override

这个注解主要用于<code style='background:#ff3385;color:white;padding:5px;'>方法</code>，表面此方法是用于重写父类的方法。

<img src='java16-Annotations\a5b3a8de-7c9b-491b-9214-122c9a3f8149.jpg'>

### Deprecated

这个注解主要用于提醒调用方，这个<code style='background:#ff3385;color:white;padding:5px;'>方法</code> / <code style='background:#ff3385;color:white;padding:5px;'>类</code> / <code style='background:#ff3385;color:white;padding:5px;'>接口</code>是不推荐使用的，过时的。

<img src='java16-Annotations\a04c5e34-af4f-4621-bdde-fe62bd1b19ed.jpg'>

### SuppressWarnings

压制<code style='background:#ff3385;color:white;padding:5px;'>编译</code>错误，可以用于类型,构造器, 方法, 域, 参数, 局部变量.

<img src='java16-Annotations\4201b15f-fb89-4bfb-af7d-18b4e7566a4e.jpg'>

参数类型：

unchecked 未检查

path 位置不存在

serial 序列化id

finally 方法不能正常结束

fallthrough 对switch贯穿代码的压制

示例（压制unchecked 和serial ）：

<img src='java16-Annotations\187f442a-d231-4b11-bccd-c9ddd3a5b8f0.jpg'>

## 元注解

元注解就是用来注解注解类型的注解。Documented, Inherited, Retention, and Target

### Documented

表示这个注解要写入javaDoc文档。

@Deprecated注解是带有@Documented修饰的，因此，在JavaDoc文档中包含注释，而@Override没有@Documented修饰，在文档中没有呈现。

<img src='java16-Annotations\b9794ec9-c2a8-4954-ad91-b69419c40c03.jpg'>

### Inherited

对此标记的注解，凡是标记了注解的类，其子类将继承这个注解。

### Retention

表示注解的有效范围，有效值：

SOURCE.源码级别，编译器将忽略。

CLASS默认级别，jvm忽略。

RUNTIME可以使用反射，运行时级别。

以下表明有效范围是源码级：

<img src='java16-Annotations\4478e252-6345-42ac-9acc-7852132303d6.jpg'>

### Target

指向的注解对象。

▪ ANNOTATION_TYPE 注解定义

▪ CONSTRUCTOR. 构造器

▪ FIELD. 域

▪ LOCAL_VARIABLE. 局部变量

▪ METHOD. 方法

▪ PACKAGE. 包

▪ PARAMETER. 参数

▪ TYPE. 类型

使用示例：

<img src='java16-Annotations\3824930a-1ee7-437e-a301-4b64d358625e.jpg'>

## 自定义注解

<pre style='background:#e6e6e6;padding=10px;'>

public @interface CustomAnnotation {
}

</pre>

注解定义示例：

<img src='java16-Annotations\8afcad6c-f6c7-4dd0-889a-451ef07bbbb9.jpg'>

注解使用：

<img src='java16-Annotations\74f95d1b-b42c-464f-8026-95e267000877.jpg'>

## 注解的反射用法

<pre style='background:#e6e6e6;padding=10px;'>

//获取注解,没有则为null
public <A extends java.lang.annotation.Annotation> A getAnnotation (Class<A> annotationClass)

//获取所有注解
public java.lang.annotation.Annotation[] getAnnotations()

//判断是否为注解类
public boolean isAnnotation()

//判断是否包含注解
public boolean isAnnotationPresent(Class<? extends java.lang.annotation.Annotation> annotationClass)

</pre>

使用示例：

<img src='java16-Annotations\5a50e87a-c532-41b9-a069-f2c423b95c51.jpg'>



