---
title: crazySSM02-常见的注解
date: 2020-04-19 20:47:21
tags: SSM
---

## Controller

控制器注解表明本类是一个控制器，当开启了自动扫描时，使用该注解的类被认定为Bean。

<img src='crazySSM02-commonAnnotations\d9d2bc44-9716-4b2e-b2b7-c01a9959850d.jpg'>

使用示例：

<img src='crazySSM02-commonAnnotations\79f8e9d8-ca69-408a-9c27-f88007f8430c.jpg' >

这里返回类型由ModelAndView改为String，用来表示返回的字符串即视图模板的名称。方法参数Model要求框架生成Model对象传递进来。方法返回的只是模板名称，需要在springmvc-config.xml中配置模板处理器：

<img src='crazySSM02-commonAnnotations\428017a0-ab1a-48ef-959b-e8dbabfce4bb.jpg' >

### 我的学习

1. 修改springmvc-config.xml配置文件：

<img src='crazySSM02-commonAnnotations\540081f8-f95d-41ca-baee-39a96b273dd1.jpg'>

2. 修改控制器源码

<img src='crazySSM02-commonAnnotations\c89d1706-b6c8-45ef-af84-8c9e1f205dbf.jpg'>

3. 效果

<img src='crazySSM02-commonAnnotations\bcfda4e0-dc67-4635-a51c-1b51ef0957f3.jpg'>

## RequestMapping

可以对类进行注解，表示本类内所有的方法的前缀：

<img src='crazySSM02-commonAnnotations\b7e973bd-8146-43bb-a572-6b2ea3aa4c70.jpg'>

常用的属性：

<img src='crazySSM02-commonAnnotations\a27b9aaf-0a54-4dc4-b66e-6d7f703e4f1b.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>value</code>即路由，可指定路由地址

<img src='crazySSM02-commonAnnotations\b01588d3-146a-4224-b484-8fd282a408ce.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>name</code>即别名

<code style='background:#ff3385;color:white;padding:5px;'>method</code>表示映射的方法类型，没有则默认支持任何方法

<img src='crazySSM02-commonAnnotations\f07acd6f-85f7-4984-a2ab-89bf200ab44c.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>consumes</code>表示支持的数据类型

<img src='crazySSM02-commonAnnotations\a339adbf-6bd9-44eb-bb69-0210a572f0bd.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>produces</code>表示返回的数据类型

<img src='crazySSM02-commonAnnotations\5c93418c-0ef6-4f12-9155-2d8fc8cbfc22.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>params</code>含有指定参数才可以处理

<img src='crazySSM02-commonAnnotations\06107059-8ce9-4967-90e0-ed1ca8e52b75.jpg'>

<code style='background:#ff3385;color:white;padding:5px;'>headers</code>含有指定header才可以处理

<img src='crazySSM02-commonAnnotations\e312466e-11d6-48c6-a334-2c7f6a0ca871.jpg'>

### Action方法可以出现的参数类型

1. HttpServletRequest

<img src='crazySSM02-commonAnnotations\037ec880-93e7-4199-ad98-1fd3ab64e9c1.jpg'>

2. HttpSession

<img src='crazySSM02-commonAnnotations\3198ee3e-cf0b-47a9-ac5d-d5923e44471d.jpg'>

3. 其他

HttpServletResponse

WebRequest

NativeWebRequest

Locale

InputStream / OutputStream

Reader / Writer

Principal

HttpEntity<?>

Map

Model

ModelMap

RedirectAttrbutes

Errors

BindingResult

SessionStatus

UriComponentsBuilder

@PathVariable

@MatrixVariable

@RequestParam

@RequestHeader

@RequestBody

@RequestPart

### Action方法可以出现的返回值类型

Model

ModelAndView

Map<k,v>

View

String 

HttpEntity / ResponseEntity

Callable

DeferredResult

void

### 数据从控制器传递到视图的方式

Model

ModelMap

ModelAndView

@SessionAttributes

@ModelAttribute

### Model 与 ModelMap

Model 与 ModelMap均可以传递数据，区别在于ModelMap实现了Map接口：

<img src='crazySSM02-commonAnnotations\40b1bab1-8e8e-4b83-a37e-58a7fd2a8f69.jpg'>

使用Model:

<img src='crazySSM02-commonAnnotations\012e01ee-df26-4101-a8ed-bf82990a068a.jpg'>

使用ModelMap:

<img src='crazySSM02-commonAnnotations\903d32ef-6642-42b3-bc91-9e15105efd85.jpg'>

### ModelAndView

可以添加数据：

<img src='crazySSM02-commonAnnotations\c94e5dc0-f58e-4a8c-ab27-42ca03145adc.jpg'>

可以设置视图：

<img src='crazySSM02-commonAnnotations\49a363cb-3d39-483a-8b95-c818d38cd275.jpg'>

使用示例：

<img src='crazySSM02-commonAnnotations\b48b165a-92b2-4bf4-bbb6-45f440a035d5.jpg'>

## RequestParam

用来获取请求url中的参数：

<img src='crazySSM02-commonAnnotations\cb150eac-b5e5-4e3d-89f5-a5fd8361e995.jpg'>

对应请求地址：

<img src='crazySSM02-commonAnnotations\7a4a06a4-0717-4047-a44b-eb95ff381609.jpg'>

常用的属性：

<img src='crazySSM02-commonAnnotations\e7a9749f-66cb-48f1-b91b-73ca245eeadf.jpg'>

name / value 对应参数名称

required表示是否为可选参数

defaultValue表示默认值

示例：

<img src='crazySSM02-commonAnnotations\70efc4b2-c635-4008-9e01-665ee33fcbf6.jpg'>

## PathVariable

<img src='crazySSM02-commonAnnotations\37b69493-974b-485d-a5f4-473a33b3b397.jpg'>

对路由参数进行绑定，默认匹配同名参数：

<img src='crazySSM02-commonAnnotations\b339b2bb-4163-42ab-a8a8-5d65a07d3357.jpg'>

将1绑定给userId

## RequestHeader

对请求头的参数进行绑定

<img src='crazySSM02-commonAnnotations\f3853c2c-eb28-4f78-b265-d5b81d8a9bd7.jpg'>

获取指定的请求头：

<img src='crazySSM02-commonAnnotations\374e062f-e152-4b03-95a2-360ae1ec6962.jpg'>

## CookieValue

获取指定的cookie:

<img src='crazySSM02-commonAnnotations\86255635-65a9-4f34-ab37-fc2689fd08fb.jpg'>

获取jsessionid：

<img src='crazySSM02-commonAnnotations\6c5a63ca-0e08-4d13-bc59-5e3208b8093d.jpg'>

## SessionAttributes

把Model中指定的参数传入session:

<img src='crazySSM02-commonAnnotations\b1c61209-cc16-4fef-8b0d-f63947c25713.jpg'>

只可以对类修饰。

<img src='crazySSM02-commonAnnotations\472826a1-d0be-4758-9485-9692aaea3210.jpg'>

将Model中追加的user加入到session

也可以指定类型：

<img src='crazySSM02-commonAnnotations\e6cc6d4a-b070-4272-a713-5028260e1c75.jpg'>

## ModelAttribute

1. 将方法返回值添加到Model

<img src='crazySSM02-commonAnnotations\8e6c873d-1176-4678-99cc-5fbf02466fe8.jpg'>

2. 优先执行的方法，将数据注入到Model

<img src='crazySSM02-commonAnnotations\4fd7eb09-fde2-4fe3-839e-50fa69c3f502.jpg'>

3. 优先执行，根据返回类型确定Model的键, 值为返回值

<img src='crazySSM02-commonAnnotations\8378db7a-0e24-4c9d-8a5d-6af66785c839.jpg'>

4. 被RequestMapping和ModelAttribute同时给注解

<img src='crazySSM02-commonAnnotations\41595368-75c9-4e1c-9a1c-59a00803ce99.jpg'>

默认添加指定的Model参数，ModelAttribute的value为键，返回值即值。
Request Mapping指定的链接即视图名称，也就是/login4

5. 使用ModelAttribute作为参数注解，会将Model中的数据注入到方法

<img src='crazySSM02-commonAnnotations\44ac34bc-ca49-429b-bb6b-3762292e68fa.jpg'>

## RequestBody与ResponseBody

RequestBody用于注解参数，将json绑定到参数

<img src='crazySSM02-commonAnnotations\25b4e7b2-c1b9-4f02-88ad-2b6c3628a7b3.jpg'>

使用ObjectMapper的writeValueAsString转为字符串:

<img src='crazySSM02-commonAnnotations\b2c1ba05-1978-4763-a945-003176b07161.jpg'>

返回json使用ResponseBody注解方法即可：

<img src='crazySSM02-commonAnnotations\7b388e9e-ac4d-422e-a649-e051e4502279.jpg'>


