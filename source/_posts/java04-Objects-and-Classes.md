---
title: java04 对象与类
date: 2020-02-19 13:30:35
tags: java
---
## 对象的两大属性

1. 特征（域）

2. 动作（方法）

例如，一辆车可以有以下特征：

<img src='java04-Objects-and-Classes\d9d0ce1e-32a9-4ef8-8d31-18c6998c3d33.jpg' >

有颜色，轮胎数量，方向盘数量，阀门数量等等。

可以有以下几种动作：

<img src='java04-Objects-and-Classes\51f3d56c-b59e-4b89-8c42-8f551c74caa6.jpg'>

行驶和刹车

## 类

如何创建对象？需要模板，这个模板就是类。如果你有Car类，就可以创建数个Car对象。一个类有什么域和方法，他的对象就有什么域和方法，不多不少。

### 类的组成

类由三部分组成：<code style='background:#ff3385;color:white;padding:5px;'>类名</code>、<code style='background:#ff3385;color:white;padding:5px;'>域</code>、<code style='background:#ff3385;color:white;padding:5px;'>方法</code>。

### 类的基本结构

<img src='java04-Objects-and-Classes\242bd98a-05c9-4c1f-8ccf-4190e539835e.jpg'>

### 域

域就是一些变量，这些变量 可以是基本数据类型，也可以是引用类型。域的名称一般采用<code style='background:#ff3385;color:white;padding:5px;'>驼峰命名</code>方式。

<img src='java04-Objects-and-Classes\ae4bbba1-c01d-47f1-8547-15cbba6f75b4.jpg' >

引用Address

<img src='java04-Objects-and-Classes\cc4f1db4-e2a8-4a06-b939-f64be78bd99f.jpg'>

### 方法

方法包括<code style='background:#ff3385;color:white;padding:5px;'>方法声明</code>和<code style='background:#ff3385;color:white;padding:5px;'>方法体</code>两部分。

方法声明包括，<code style='background:#ff3385;color:white;padding:5px;'>返回值类型</code>，<code style='background:#ff3385;color:white;padding:5px;'>方法名</code>，<code style='background:#ff3385;color:white;padding:5px;'>参数列表</code>。

<img src='java04-Objects-and-Classes\3a5fb204-87a8-4d44-bf85-cfa81961ac47.jpg' >

方法的返回值可以是<code style='background:#ff3385;color:white;padding:5px;'>基本数据类型</code>、<code style='background:#ff3385;color:white;padding:5px;'>引用类型</code>或<code style='background:#ff3385;color:white;padding:5px;'>void</code>.

方法体是方法的具体内容。

方法的定义：

<img src='java04-Objects-and-Classes\14ecbf32-49fc-456a-b5d4-7d596a140571.jpg' >

带返回值的方法：

<img src='java04-Objects-and-Classes\ee9f1555-1687-4457-95af-0ba96c26958c.jpg' >

带参数和返回值的方法：

<img src='java04-Objects-and-Classes\6c6c9a33-8386-4906-a14c-ff58fd688cee.jpg' >

不定个数参数方法：

<img src='java04-Objects-and-Classes\bf62d6a1-3a74-410e-8cec-d4f9267b0d84.jpg' >

使用...表示不定个数参数

### 构造器

构造器是用于生产对象的方法，每个类需要包含至少一个构造器。这个方法结构：

<img src='java04-Objects-and-Classes\60bb4f16-bf5a-4088-ba5f-20ed4f6e568b.jpg'>

构造器的参数可以 有多个，也可以一个没有。构造器的参数用于初始化对象的域。

有参构造函数存在时，编译器不会自动添加无参构造函数，若没有构造函数，则默认添加一个无参构造函数。

<img src='java04-Objects-and-Classes\06e97cea-1022-4498-8d9d-2b39c22298dc.jpg'>

### 类的UML表示方法

<img src='java04-Objects-and-Classes\8770f04d-752f-4459-bd42-b5b58b195031.jpg'>

域采用名称+类型的方式表示，方法采用名称和参数列表+返回值类型的方式表示。

## 创建对象

如何创建对象？有了模板，就可以根据模板创建对象了：

<img src='java04-Objects-and-Classes\32824e0c-ee26-46a9-bcc3-0abd2bdc4af7.jpg'>

我们可以使用一个变量来引用这个对象（类型要一致）：

<img src='java04-Objects-and-Classes\f9a03d8c-0de4-465c-94d0-8bd74ddc1b96.jpg' >

有了对象，就可以调用类的方法和域了：

<img src='java04-Objects-and-Classes\0cb9cebf-1044-4578-8a02-a8655e8f8537.jpg'>

对象创建内部操作：

<img src='java04-Objects-and-Classes\34b3c47c-bfa4-4c8c-8c2b-ddbf2d9ee4a9.jpg'>

对象的引用：

<img src='java04-Objects-and-Classes\38675e86-54d9-4390-95c4-e88abd797534.jpg'>

多个变量引用同一个对象

<img src='java04-Objects-and-Classes\33d6dd43-4164-43ba-80f2-c6bf08e8ade0.jpg'>

## Null

创建一个全局的对象的变量，而没有赋值初始化的时候，他默认是null:

<img src='java04-Objects-and-Classes\85720cf3-24da-4e54-ba0d-beee37f81426.jpg'>

局部变量需要手动赋初值，否则出现编译错误：

<img src='java04-Objects-and-Classes\b53a0c70-e610-4a81-bff2-687262933e8b.jpg' >

对于空对象，你是无法访问它的域或者方法的：

<img src='java04-Objects-and-Classes\7c189b5c-ff57-46e4-a6d9-eba3e353a116.jpg'>

需要在调用前做好判断：

<img src='java04-Objects-and-Classes\42c8f66f-0355-44bf-86ac-fdf82b912374.jpg'>

## 内存分配

程序运行时，分为两个部分存储：栈和堆。

<code style='background:#ff3385;color:white;padding:5px;'>基本数据类型</code>的变量空间分配在<code style='background:#ff3385;color:white;padding:5px;'>栈</code>空间上，<code style='background:#ff3385;color:white;padding:5px;'>引用类型</code>变量空间分配在<code style='background:#ff3385;color:white;padding:5px;'>堆</code>内存。

定义一个引用变量，对象的<code style='background:#ff3385;color:white;padding:5px;'>数据</code>存储在<code style='background:#ff3385;color:white;padding:5px;'>堆</code>空间，对象的<code style='background:#ff3385;color:white;padding:5px;'>引用地址</code>存储在<code style='background:#ff3385;color:white;padding:5px;'>栈</code>空间上。

同一个对象，可以被<code style='background:#ff3385;color:white;padding:5px;'>多个变量引用</code>：

<img src='java04-Objects-and-Classes\ba03a72c-eb55-4f6e-b333-17b314dd6e26.jpg'>

这个时候，两个变量引用的是同一个对象：

<img src='java04-Objects-and-Classes\61298a7d-cb08-465d-9d35-122640928129.jpg'>

若分别创建对象，则引用的是不同的对象：

<img src='java04-Objects-and-Classes\c2859d8a-7719-4ead-8fb8-2652329e14e9.jpg'>

现在存在两个对象：

<img src='java04-Objects-and-Classes\472a9d71-a64e-49e4-83ee-2d75b97b7ffb.jpg' >

## Java包

Java的包主要用于将功能模块进行划分，便于区别和管理。同时，不同的包的类名不会发生冲突。

包的定义：

<img src='java04-Objects-and-Classes\ebed479d-b71d-4fed-b8ee-f064443c54c0.jpg'>

使用package+包名将类包含在指定的包内。包名通常以域名倒置开始。

类的全限定名称：

包名 + 类名

com.brainysoftware.common.MathUtil

在包含在包内的类的编译、运行，需要使用全限定名称：

<img src='java04-Objects-and-Classes\668e1694-bacc-46e7-9488-e2e3be810bd5.jpg'>

运行

<img src='java04-Objects-and-Classes\68ad9684-bf54-41a8-80d6-a9d4077bdd78.jpg'>

## 类的访问修饰符

类的访问修饰符：<code style='background:#ff3385;color:white;padding:5px;'>public</code>和<code style='background:#ff3385;color:white;padding:5px;'>default</code>

public类在<code style='background:#ff3385;color:white;padding:5px;'>任何位置</code>都可以访问：

<img src='java04-Objects-and-Classes\421ae2b5-568b-4f27-8668-839786dbf9cd.jpg'>

没有访问修饰符就是default：

<img src='java04-Objects-and-Classes\77027f1e-192c-4482-b664-f0ca1236f26d.jpg'>

只有在<code style='background:#ff3385;color:white;padding:5px;'>相同的包内</code>才可以访问。

## 类成员访问修饰符

类成员修饰符，指的是对<code style='background:#ff3385;color:white;padding:5px;'>域</code>、<code style='background:#ff3385;color:white;padding:5px;'>方法</code>、<code style='background:#ff3385;color:white;padding:5px;'>构造器</code>的修饰符，包括<code style='background:#ff3385;color:white;padding:5px;'>public</code>、<code style='background:#ff3385;color:white;padding:5px;'>private</code>、<code style='background:#ff3385;color:white;padding:5px;'>protected</code>、<code style='background:#ff3385;color:white;padding:5px;'>default</code>四种。

<img src='java04-Objects-and-Classes\b4ba3980-9e69-4988-be0d-c12664d0453a.jpg'>

public在<code style='background:#ff3385;color:white;padding:5px;'>任意</code>位置都可以访问

private<code style='background:#ff3385;color:white;padding:5px;'>只有类内</code>可以访问

default可以在<code style='background:#ff3385;color:white;padding:5px;'>包内</code>，<code style='background:#ff3385;color:white;padding:5px;'>类内</code>访问

protected可以在<code style='background:#ff3385;color:white;padding:5px;'>包内</code>，<code style='background:#ff3385;color:white;padding:5px;'>类内</code>，<code style='background:#ff3385;color:white;padding:5px;'>子类</code>访问

## UML的表示方法

<img src='java04-Objects-and-Classes\1bc05e3c-4be1-404c-8aa5-7dcbb9b8b313.jpg'>

public使用+

private使用-

protected使用#

default没有标记

## this关键词

this可以调用本类的域或方法：

<img src='java04-Objects-and-Classes\a7328294-7ce7-4bdb-898d-ee868535e4e9.jpg'>

使用this可以明确是域还是参数，避免混淆。

## 使用其他类

使用其他类，如果是相同的包内，可以直接使用，不同的包的时候需要导包：

<img src='java04-Objects-and-Classes\e5e78ec8-1853-4595-8d67-1d6893ab45b0.jpg' >

导包语句需要在类声明之前，在package之后。

一次性导入同一个包下的多个类时，使用<code style='background:#ff3385;color:white;padding:5px;'>*</code>:

<img src='java04-Objects-and-Classes\ae3d288f-cbf8-4454-9aff-12719f540bd0.jpg'>

不导包，可以使用<code style='background:#ff3385;color:white;padding:5px;'>全限定名称</code>代替:

<img src='java04-Objects-and-Classes\a775c481-37b4-4a5e-9e36-0ab58a9a8101.jpg' >

当出现引用不同的包<code style='background:#ff3385;color:white;padding:5px;'>出现类名冲突</code>时，需要使用全限定名称。

## 常量

常量使用final定义，可以是局部常量也可以是全局常量：

<img src='java04-Objects-and-Classes\582f4685-a032-4819-829d-45eb89c110f5.jpg'>

一旦赋值，将不可再赋值，否则会编译失败。

## 静态成员

类似于System.out，类的静态成员可以在<code style='background:#ff3385;color:white;padding:5px;'>不创建实例</code>的情况下直接通过<code style='background:#ff3385;color:white;padding:5px;'>类名</code>调用。那么，入口函数，main方法就是在未创建任何实例之前，直接执行的方法。

静态成员的定义使用static关键字，与访问修饰符顺序可变：

<img src='java04-Objects-and-Classes\00cdcd9a-6070-472e-860b-11191c002b2d.jpg'>

也可以定义一个静态方法：

<img src='java04-Objects-and-Classes\d5e1c3e9-3ece-4312-8ef0-c404f60a7dcf.jpg' >

调用时，直接使用类名调用：

<img src='java04-Objects-and-Classes\1700c2ea-445b-48d0-b12b-79f4aa6a459b.jpg'>

在静态方法中，只能调用<code style='background:#ff3385;color:white;padding:5px;'>静态方法</code>和<code style='background:#ff3385;color:white;padding:5px;'>静态域</code>，不可以调用<code style='background:#ff3385;color:white;padding:5px;'>实例方法</code>和<code style='background:#ff3385;color:white;padding:5px;'>实例域</code>。

静态对象可以创建，一般用于共享同一个对象。

<img src='java04-Objects-and-Classes\c91ff6f1-96c8-4660-97d5-c59023519b09.jpg' >

### UML表示法

在uml中，使用下划线表示静态方法：

<img src='java04-Objects-and-Classes\30bb1244-a4a0-4e28-88b8-346d353ffeaf.jpg'>

## 静态常量

静态常量常用于存储数据，一般可以用枚举代替

<img src='java04-Objects-and-Classes\b8bb72a1-1edd-45f2-a055-b8bfda819119.jpg' >

静态常引用：

<img src='java04-Objects-and-Classes\7350eb2e-6118-4b12-bc09-272a8cc763a4.jpg'>

它的引用地址不能再发生变化，它的域值可以改变。

<img src='java04-Objects-and-Classes\17cb9cd0-1ab7-4d91-acc1-518b6d868100.jpg'>

值可以变：

<img src='java04-Objects-and-Classes\523b78f0-a567-4e33-b1ec-23ab664ba3d2.jpg'>

## 方法重载

两个方法功能类似，方法名称相同，参数列表不同，可以构成重载：

<img src='java04-Objects-and-Classes\a7b9eafc-c14f-4d1e-b863-85bdd15e0ead.jpg'>

如果仅返回值不同，不构成重载：

<img src='java04-Objects-and-Classes\8934a757-eec8-4aa0-a3a6-d3f800a96a56.jpg'>


## 值引用&地址引用

基本类型的变量和引用类型变量均可以传递给方法作为参数使用，区别是基本类型的变量传递给函数时，jvm会<code style='background:#ff3385;color:white;padding:5px;'>拷贝</code>一份给函数，而不是变量本身。引用类型传递的是<code style='background:#ff3385;color:white;padding:5px;'>地址</code>，函数操作了引用变量的域后，原来变量也会随之改变。

## 类的加载、链接、初始化

**加载**：

当你使用命令运行程序时，jvm首先加载class文件到内存中，并进行缓存。若找不到class，将抛出异常。

**链接**：

链接阶段有三个步骤：验证、准备、处理。

验证阶段主要是对class文件的有效性进行验证。

准备阶段为静态变量分配内存，准备运行class所需要的其他数据结构。

处理阶段主要对运行类文件所需的其他类或接口进行查找和处理。

**初始化**：

类的初始化优先初始化父类，对静态变量进行赋值，没有赋值语句的赋默认值。

<img src='java04-Objects-and-Classes\eaee83c9-0b5f-4fef-875c-fa0dafd524b8.jpg'>

静态代码块也会依次执行：

<img src='java04-Objects-and-Classes\0f991961-68d3-41b7-9137-e380a7e04e83.jpg'>

## 类的初始化

1. 为对象分配内存，包含自身的域和父类的域。

2. 调用构造器。为构造器的参数分配空间，赋值。

3. 如果引用其他构造器，将调用其他构造器。

4. 实例初始化及实例域初始化。

5. 返回实例的引用。

## 实例的比较

两个实例使用==比较，对于引用类型比较的是<code style='background:#ff3385;color:white;padding:5px;'>地址</code>，对于基本数据类型比较的是<code style='background:#ff3385;color:white;padding:5px;'>值</code>，这个需要注意区分。如果想改变默认的比较方式，需要重写<code style='background:#ff3385;color:white;padding:5px;'>equals</code>方法和<code style='background:#ff3385;color:white;padding:5px;'>hashCode</code>方法。

## 垃圾回收

对于不再有引用的变量，或超出变量域作用范围的，将由垃圾回收机自动回收内存。

## 内部类

非静态内部类

<img src='java04-Objects-and-Classes\694d7fdc-93ab-4731-96e5-f2eb75863209.jpg' >

非静态内部类可以访问外部类的<code style='background:#ff3385;color:white;padding:5px;'>所有字段和方法</code>，而静态内部类只能直接使用<code style='background:#ff3385;color:white;padding:5px;'>静态方法和静态字段</code>，对实例字段和方法需要通过外部类的<code style='background:#ff3385;color:white;padding:5px;'>对象</code>调用。

<code style='background:#ff3385;color:white;padding:5px;'>外部类不能直接访问内部类的方法和字段！</code>




