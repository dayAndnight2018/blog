---
title: 'spring-Boot+vue04: 整合web开发'
date: 2020-05-29 15:20:53
tags: spring-boot
---

## 返回JSON数据

默认添加web模块后，自动使用jackson-databind处理：

<img src='spring-Boot-vue04-web\28ce6150-cfdf-412f-b2f3-775322bfd220.jpg'>

添加一个pojo:

<img src='spring-Boot-vue04-web\f5910f79-a35d-4641-b36f-0d4e5f80eaa6.jpg'>

直接返回实体：

<img src='spring-Boot-vue04-web\32a2830b-286f-4328-9809-fb6519fc44b3.jpg'>

### 配置Gson替换jackson-databind

去除jackson-databind添加gson

<img src='spring-Boot-vue04-web\1f295ceb-7519-4dbb-9777-11ec3a0324bd.jpg'>

配置Date格式化及忽略字段：

<img src='spring-Boot-vue04-web\84bfcbae-84df-4e83-a4ce-bce27bd929c3.jpg'>

### 配置fastjson替换jackson-databind

去除jackson-databind添加fastjson

<img src='spring-Boot-vue04-web\ff21b4fa-6201-4779-9ebf-b1c7d4c0f524.jpg'>

配置相关信息：

<img src='spring-Boot-vue04-web\0b534d0d-2a13-41c3-a06d-6f2d53419608.jpg'>

配置编码：

<img src='spring-Boot-vue04-web\f2bccf28-40e9-423a-9b29-2e3215348872.jpg'>

## 静态资源

1. 配置静态资源路径

<img src='spring-Boot-vue04-web\f1a419ff-4137-4009-930f-7c5dcae5c871.jpg'>

2. 通过WebMvcConfigurer设置

<img src='spring-Boot-vue04-web\bfa9a14c-32f8-4d28-8bd8-2346a57e03f5.jpg'>

## 文件上传

1. 创建项目添加web依赖

2. 添加上传页面

<img src='spring-Boot-vue04-web\59b5fb28-61e8-4ff2-8936-48561d3377f9.jpg' style='width:480px;height:320px;margin:30px auto;display:block' alt='title'>

3. 处理文件

<img src='spring-Boot-vue04-web\f9dcbf9a-ec2b-44ff-ace6-a41cf76d9610.jpg'>

4. 更多配置

<img src='spring-Boot-vue04-web\f323f886-7435-4e69-af9d-f716a76caf93.jpg'>

5. 多文件上传

修改上传页面

<img src='spring-Boot-vue04-web\857c3faa-eee7-4232-8a4d-3f516290195b.jpg'>

控制器接受MutilpartFile数组

<img src='spring-Boot-vue04-web\5b2a63c0-dada-46ab-864e-2423fa91ccb4.jpg'>

## ControllerAdvice

### 全局异常处理

1. 添加自定义异常处理类，并给ControllerAdvice注解

<img src='spring-Boot-vue04-web\fe65a1e8-567a-4a39-b46e-10d479b4d5ff.jpg'>

出现异常时，将根据ExceptionHandler注解指定的类型查找处理方法。

处理方法参数可以是：

HttpServletResponse、XXXException、HttpServletRequest、Model

处理方法返回值可以是：

Json、ModelAndView、视图名称等等

### 添加全局数据

1. 创建全局数据处理类，使用ModelAttribute注解

<img src='spring-Boot-vue04-web\102b4bc9-c4e6-4339-9870-f220467203a8.jpg'>

ModelAttribute注解的value就是Model中添加的键，方法返回值就是值。

2. 在任意的控制器方法中可以获取这些数据

<img src='spring-Boot-vue04-web\e50607d8-b28a-4d8a-b471-661eaa0f020a.jpg'>

### 数据预绑定

1. 假设有pojo需要接收

<img src='spring-Boot-vue04-web\388c6c53-e691-4d9c-a065-362584877fbe.jpg'>

2. 如果不使用注解，二者相同的参数名称会引发问题。

<img src='spring-Boot-vue04-web\432b1f79-cc46-4369-9890-d59fa72e87e1.jpg'>

3. 使用ModelAttribute添加标记

<img src='spring-Boot-vue04-web\fcf66810-7907-46ad-aef1-923572e65e3e.jpg'>

4. 在ControllerAdvice标记的类中处理

<img src='spring-Boot-vue04-web\e7aea350-6687-4e2e-9e85-38a0662ccfa3.jpg'>

5. 请求

根据前缀即可绑定

<img src='spring-Boot-vue04-web\1ba8e663-6f3e-4959-864e-d8511ee86e91.jpg'>

## 自定义错误页面

ControllerAdvice用于对控制器的增强，无法捕捉全局异常信息。

对于404或500页面，spring boot有默认的页面提示：

<img src='spring-Boot-vue04-web\5a306fb5-b62f-425a-9b1c-8ba648f1a8cf.jpg'>

### 配置静态错误页面

可以在static目录下创建error文件夹，下面放置静态的错误页面：

<img src='spring-Boot-vue04-web\96ff1cee-6034-42e4-9a7e-260152d894a4.jpg'>

### 配置错误详情页

在templates下创建error文件夹，下面放置错误页面模板：

<img src='spring-Boot-vue04-web\0e04ec6e-3243-4f0b-8c0d-8029f196c1e3.jpg'>

可以显示一些错误信息：

timestamp、status、error、message、path

<img src='spring-Boot-vue04-web\f6233531-b2de-4e47-879d-b32f706c8ee9.jpg'>

### 自定义错误信息

通过继承DefaultErrorAttributes自定义错误信息：

<img src='spring-Boot-vue04-web\daf17349-ed61-4ace-97c3-4a322e77c80b.jpg'>

效果：

<img src='spring-Boot-vue04-web\7fa48bac-8f6f-458b-8683-9ea064a96a57.jpg'>

### 自定义错误视图

可以实现ErrorViewResolver定制错误数据和错误模板：

<img src='spring-Boot-vue04-web\2ec8df96-5cff-4eca-981f-f2eed3f3608e.jpg'>

### 完全自定义

可以实现ErrorController接口，或者继承BasicErrorController

<img src='spring-Boot-vue04-web\b0a11131-b2aa-4578-923d-7b32dd6fb43e.jpg'>

## 跨域

### 细粒度注解跨域

<img src='spring-Boot-vue04-web\1bfdf17f-ef82-4070-b5c6-ede6631543b8.jpg'>

### WebMvcConfigurer配置跨域

<img src='spring-Boot-vue04-web\f5b9b58b-7cdb-4ba1-828a-b52532425cb7.jpg'>
<img src='spring-Boot-vue04-web\80a7b56a-17be-4561-8727-d58133708f6a.jpg'>

## Java配置及xml配置

一个Bean：

<img src='spring-Boot-vue04-web\cfba4a78-a0fb-4b94-9de2-719489062051.jpg'>

通过xml注册：

<img src='spring-Boot-vue04-web\ee8db474-eb86-40da-b83d-c73bfec62818.jpg'>

在配置类可以使用ImportResource导入：

<img src='spring-Boot-vue04-web\e00eee13-d910-4674-bd8d-d4a2976254cd.jpg'>

使用方法不变：

<img src='spring-Boot-vue04-web\a56f9a53-8561-4559-aa2e-5f3493f7687f.jpg'>

## 拦截器

通过实现HandlerInterceptor创建拦截器：

<img src='spring-Boot-vue04-web\9ea2c145-abc0-4399-b08b-eb7bf24a8fc5.jpg'>
<img src='spring-Boot-vue04-web\b837cf23-f950-4205-aa1f-8a9037d257a1.jpg'>

提供preHandle、PostHandle、afterHandle不同节点的拦截。

注册拦截器：

<img src='spring-Boot-vue04-web\04e8c7e1-7af1-47f6-9cb3-99fea5c5521c.jpg'>

## 系统任务

### CommandLineRunner

实现CommandLineRunner重写run方法

<img src='spring-Boot-vue04-web\e5662a15-99c1-4839-a7ae-fd8da8be6cc7.jpg'>

order注解表示执行次序。

### ApplicationRunner

实现ApplicationRunner接口重写run方法

<img src='spring-Boot-vue04-web\10bcf7e8-6f34-43f4-a09f-f309e3a8315b.jpg'>

NonOptionArgs表示main方法参数，OptionValues表示项目启动参数。

<img src='spring-Boot-vue04-web\5b6fffaf-8813-4d07-889f-3f242b268fd2.jpg'>

## 整合Servlet、Filter、Listener

Servlet：

<img src='spring-Boot-vue04-web\c4f13e62-1319-4e28-926d-cd2a4cacde26.jpg'>

Filter:

<img src='spring-Boot-vue04-web\d08394a4-57eb-4967-8c35-13b71d46e141.jpg'>
<img src='spring-Boot-vue04-web\fbc992c6-b895-4b50-8b79-6736aa9725ea.jpg'>

Listener:

<img src='spring-Boot-vue04-web\ebdbfe3b-3a2c-4cd1-adf8-8f22e9a52f99.jpg'>

也支持HttpSessionListener、ServletContextListener

需要在启动类开启ServletComponentScan注解：

<img src='spring-Boot-vue04-web\f10e8d74-b065-4600-a831-d08c5ade1654.jpg'>

## 路径映射

为了提高反应速度，可以对无需数据的页面配置路由映射，实现WebMvcConfigurer接口，重写addViewControllers方法：

<img src='spring-Boot-vue04-web\4b14fe59-2c46-4b9d-bc92-895dae243e27.jpg'>

## Aop

### 使用aop

1. 添加aop依赖

<img src='spring-Boot-vue04-web\53aecb6a-eeed-4e95-863f-34d32093e9f7.jpg'>

2. 创建被监听服务

<img src='spring-Boot-vue04-web\6d52f476-2487-4786-9566-d672b30f2c7a.jpg'>

3. 创建切面

<img src='spring-Boot-vue04-web\bf370db6-9ad2-4ee0-a8b4-99eba47e4e38.jpg'>

服务调用时，相关的切面方法也会执行。

## 自定义图标

将favico.ico放在static目录下即可。

## 去除默认配置

1. 使用EnableAutoConfiguration注解去除

<img src='spring-Boot-vue04-web\e1c01c85-34da-460e-8124-8a058707e2fb.jpg'>

2. 使用配置去除

<img src='spring-Boot-vue04-web\220f9af5-a2d1-4a97-9357-6ad2f4080ffc.jpg'>



















