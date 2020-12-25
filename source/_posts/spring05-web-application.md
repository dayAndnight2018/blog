---
title: spring05- spring web 应用
date: 2020-06-16 22:07:50
tags: spring
---

## 用户请求跟踪

<img src='spring05-web-application\13d61bab-e338-4080-ac29-271e29da5ff1.jpg'>

1. 请求到达服务端，首先进入DispatcherServlet

前端控制器将请求转发到其他组件处理，起到拦截的作用，在这里，DispatcherServlet就是前端控制器

2. 通过处理器映射获取下一站

处理器映射相当于门牌号，前端控制器根据请求地址信息，查询处理器映射信息，获取下一站(控制器)的地址。

3. 控制器

控制器接受请求，获取请求信息并进行处理，处理结束后，将数据返回，并选择合适的页面渲染。

4. 模型和逻辑视图

模型里存储的是返回的数据信息，逻辑视图就是渲染数据所使用的页面

5. 视图解析器

视图解析器获取数据及视图模板，将数据渲染到页面

6. 视图

生成的视图用于展示给用户

## 配置Spring MVC相关

1. 使用代码创建DispatcherServlet和Spring上下文

创建配置类，继承AbstractAnnotationConfigDispatcherServletInitializer

<img src='spring05-web-application\b7590079-f482-45d8-985a-7262e78c0140.jpg'>

第一个方法是getServletMappings()：用于配置前端控制器拦截路径

GetServlet-ConfigClasses()：用于配置前端控制器用到的Bean

getRootConfigClasses(): 用于ContextLoaderListener用到的Bean

2. 配置WebConfig

<img src='spring05-web-application\2de537b2-0a37-4f11-961d-8c1ed2f1b9d8.jpg'>

继承WebMvcConfigurerAdapter类，实现DispatcherServlet相关的配置。

3. 配置RootConfig

根配置不是本章节的重点，简单配置包扫描，去除对WebConfig的扫描即可

<img src='spring05-web-application\2f758f8d-39c2-41f9-97e3-d7ee194d04d7.jpg'>

## 写个简单的控制器

### 测试控制器

1. 创建一个简单的控制器

<img src='spring05-web-application\f7abeca9-9b81-422f-ad08-f35516721a18.jpg'>

采用@Controller注解表名这是一个控制器Bean

@RequestMapping表示请求地址和动作方法

返回的"home"是视图的名称。

2. JSP页面展示

<img src='spring05-web-application\fce8de81-6548-4b22-88fc-89ac634d921f.jpg'>

3. 测试

<img src='spring05-web-application\be40d188-e7ed-4b64-ae01-42c9d59cfc60.jpg'>

简单测试方法，直接断言：

<img src='spring05-web-application\abce45cd-a3c1-464a-aeee-87a6723c3c7a.jpg'>

使用MockMVC:

<img src='spring05-web-application\fc8ae99e-a060-47a7-a963-564881c6fd53.jpg'>

### RequestMapping的拆分

<img src='spring05-web-application\5b4d6c14-7c83-46bd-b893-08cd7dc50d67.jpg'>

将RequestMapping加到类上，添加类级别的限定。

### 映射多个路由

RequestMapping可以对多个路由映射，也就是对多个url进行响应

<img src='spring05-web-application\74d9329e-c623-4f7a-9ca1-bd01ed364375.jpg'>

### 返回模型数据

<img src='spring05-web-application\b642bfa9-803c-4fcb-8b41-b099dcc31165.jpg'>

使用Model作为方法参数，通过addAttribute方法添加数据，并通过spittles视图名的模板渲染：

<img src='spring05-web-application\04e141fc-a699-488d-bac5-0505b1d22dbd.jpg'>


## 处理输入

输入信息有三种：

* 查询参数（Query Parameter） 
* 表单参数（Form Parameter） 
* 路径变量（Path Variable） 

### 查询参数

当请求为

<img src='spring05-web-application\d42b2a05-bd7f-412d-86db-8bf1e41c4ea6.jpg'>

此时可以通过@RequestParam获取查询参数

<img src='spring05-web-application\fdbf6da8-0a59-4cc1-a617-163db6df5070.jpg'>

如果请求中没有给出参数，需要给默认值：

<img src='spring05-web-application\602df014-be62-421b-92dd-884d4a6d8788.jpg'>

因为默认传入的是String类型，所以默认值也需要是字符串。这里存在一个常量转换：

<img src='spring05-web-application\4ad7f548-e6ae-4bb1-ae2e-f9b040912719.jpg'>

### 路由参数

当请求为

<img src='spring05-web-application\f6bf183f-210f-42f8-a6bb-f69f2eedf3b4.jpg'>

使用{variable}作为路径，使用PathVariable注解获取路由参数

<img src='spring05-web-application\eb4555cf-1c3c-4b97-bc61-f30820814dc3.jpg'>

### form参数

通过form提交的参数，可以通过POJO接收

<img src='spring05-web-application\cea005b7-c0c6-43bd-959e-a555ebc199ee.jpg'>

需要对输入参数进行校验

<img src='spring05-web-application\f16583d5-66c0-45c0-848d-b07eb961a78d.jpg'>

使用@Valid注解强制校验，校验结果存储到Errors对象里：

<img src='spring05-web-application\844c0671-9998-41ca-beec-4317690a335c.jpg'>

### 常用的表单参数验证注解

<img src='spring05-web-application\90ff8eaa-c9bc-445b-af92-0d148fc31def.jpg'>
<img src='spring05-web-application\3c58b607-3471-4272-9b19-4c8983a91e12.jpg' >
<img src='spring05-web-application\5bbc9905-5bd7-49fb-a933-5c6b077ede5c.jpg'>





