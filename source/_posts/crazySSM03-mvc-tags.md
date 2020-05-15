---
title: crazySSM03-Spring MVC 常用标签
date: 2020-04-23 10:31:33
tags: SSM
---

spring MVC的标签库主要用于处理使用JSP进行数据显示的工作。

## 表单标签库

表单标签库的实现类位与spring-webmvc.jar, 说明文档在spring-form.tld

使用表单标签库需要添加声明：

<%@ taglib prefix="form" uri="http://www.springframework.org/tags/form" %>

表单标签库支持的标签：

<img src='crazySSM03-mvc-tags\c0fc464b-1f50-40be-bcd2-5df3ef0d8e25.jpg' >

### form标签

form标签用于绑定JavaBean，同时支持除get、post以外的请求方法。commandName用于指定JavaBean的名称，默认为command

<img src='crazySSM03-mvc-tags\e1e7577e-469c-4fd8-b89e-83903150e02f.jpg'>

### input标签

用于渲染一个输入框，用于数据绑定。通过path属性绑定JavaBean的某个属性值

<img src='crazySSM03-mvc-tags\08129ed7-d5dc-4dd1-8873-754e4035541a.jpg'>

使用示例：

<img src='crazySSM03-mvc-tags\64171e24-890c-4815-bbbf-113883b91ecf.jpg'>

默认获取JavaBean的command属性，绑定username、sex、age三个字段。

<img src='crazySSM03-mvc-tags\5255f975-1bbf-4ee2-b61a-0998e576ad5d.jpg'>

<img src='crazySSM03-mvc-tags\928781e1-cdf5-4aa9-ae35-f8f8b5de3207.jpg'>

也可以使用ModelAttribute或commandName指定绑定javaBean的名称：

<img src='crazySSM03-mvc-tags\c084021f-32cd-4e82-9cac-a94f2b364daa.jpg'>

### password标签

生成一个password标签：

<img src='crazySSM03-mvc-tags\ca066583-cd3a-460a-b1e8-7f26f078386b.jpg'>

示例：

<img src='crazySSM03-mvc-tags\288a9db3-b12b-4123-83f7-52f7bf53894d.jpg'>

### hidden标签

生成一个隐藏域：

<img src='crazySSM03-mvc-tags\82ab39c5-78fb-42c3-aa08-6ee7c17dd9b0.jpg'>

示例：

<img src='crazySSM03-mvc-tags\0f1f05fe-bb88-42a3-8123-fcb305fc0f07.jpg'>

### textarea

生成多行输入域：

<img src='crazySSM03-mvc-tags\4f583f36-7bba-496a-9bc7-3366236f56e0.jpg'>

示例:

<img src='crazySSM03-mvc-tags\adc3af63-9e69-4b19-98f8-561aa200b146.jpg'>

### checkbox标签

生成checkbox标签：

<img src='crazySSM03-mvc-tags\3f146d81-7c7d-44fa-9713-12387c8b7e49.jpg'>

可以绑定Boolean或数组、list、set类型数据，当value与数据一致，则选中，否则非选中，同时label表示要显示的提示文字：

<img src='crazySSM03-mvc-tags\fa0d98a6-1713-4d94-8ebf-d8e8eb2c0465.jpg'>

控制器存储数据：

<img src='crazySSM03-mvc-tags\6acb52cc-b90d-4a2b-a953-881ddc826a5a.jpg'>

效果：

<img src='crazySSM03-mvc-tags\df49bf39-ba0f-4993-8102-3954e5b0e474.jpg'>

### checkboxes标签

用于渲染多个checkbox

<img src='crazySSM03-mvc-tags\2a253d80-b0ba-4564-941c-d3e40cabbdee.jpg'>

path是选中的那些选项，items是所有可选项。

示例：

学生选课

<img src='crazySSM03-mvc-tags\1af2553f-9ac1-4cc0-9b4c-bd7169f5220a.jpg'>

控制器

<img src='crazySSM03-mvc-tags\27ec2930-586f-44e8-8608-cc7e07ebb6bb.jpg'>

jsp

<img src='crazySSM03-mvc-tags\c8dca2ba-b55c-422e-a372-68a544ed222e.jpg'>

显示效果

<img src='crazySSM03-mvc-tags\16265276-0af3-4bb3-adb2-dc76661deef5.jpg'>

为了不同的标签的value与label个性化，可以使用Map绑定items，其key是value，value是label,也可以通过对象的itemLabel与itemValue设置对应的属性。

### radiobutton标签

用于渲染单选按钮

<img src='crazySSM03-mvc-tags\6550c306-c84d-4887-8d4b-3f631568e156.jpg'>

示例：

<img src='crazySSM03-mvc-tags\4dcffd6c-0c63-46a5-9165-b0bf7ade55db.jpg'>

绑定string类型的sex属性

<img src='crazySSM03-mvc-tags\4e5ae4d0-35ef-4cd8-aa48-9cf73c2593fc.jpg'>

path指定绑定的属性，value与之一致则选中。

### radiobuttons

生成一组radiobutton

<img src='crazySSM03-mvc-tags\b88731a2-03c6-44ee-a0a0-a85cea4b1104.jpg'>

示例：

<img src='crazySSM03-mvc-tags\1dd99174-0e7b-4b6d-bf7f-a88bda49fa7f.jpg'>

path是选中的项目，items是可选项：

<img src='crazySSM03-mvc-tags\ec8c1473-c584-4f0a-bf01-159c3320b5e8.jpg'>

### select标签

生成select标签

<img src='crazySSM03-mvc-tags\75958d55-8aa4-4bcb-b3a5-1c9d8cd78e2b.jpg'>

### option标签

生成select的一个选项

<img src='crazySSM03-mvc-tags\5bd633a6-0be1-42e9-b0eb-97aa68578545.jpg'>

### options标签

生成多个option标签

<img src='crazySSM03-mvc-tags\5bf6cf64-28e6-46be-bd24-10782d1a85e2.jpg'>

使用option示例：

给定int值

<img src='crazySSM03-mvc-tags\97ad845c-f35c-4730-a56a-cf3dfbfad7ed.jpg'>

手动挨个渲染option

<img src='crazySSM03-mvc-tags\8644e45e-b8a3-4150-91f7-9c3c6ad46f2d.jpg'>

绑定的path的值与option的value一致的被选中。

使用items示例：

输入绑定的items为Map类型，显示所有选项：

<img src='crazySSM03-mvc-tags\9da5fef4-ee1c-4045-aec7-c87dcbdd10e6.jpg'>

select的被选项是path, 所有待选项在items

<img src='crazySSM03-mvc-tags\841afef5-499f-4fa7-b72a-9d07f58bff7e.jpg'>

也可以使用options的items选项渲染

<img src='crazySSM03-mvc-tags\380e9b16-15c4-48b9-8a71-ea403ed43917.jpg'>

使用itemLabel及itemValue示例：

JavaBean

<img src='crazySSM03-mvc-tags\6d18df89-44af-4536-a9fb-0c62732897df.jpg'>

控制器

<img src='crazySSM03-mvc-tags\ef9326e1-581e-429a-8e25-bb6ac90a3e83.jpg'>

渲染

<img src='crazySSM03-mvc-tags\d168eed6-e6a1-4399-8c21-ba5f2e17881c.jpg'>

### Errors

渲染错误信息

<img src='crazySSM03-mvc-tags\9f00265b-d470-416a-aeac-817d53593885.jpg'>

path是渲染的错误属性

<img src='crazySSM03-mvc-tags\ed414a52-34e5-4ee2-95c3-9a8b641180b2.jpg'>

验证器：

<img src='crazySSM03-mvc-tags\672b21a8-249f-4d74-b84e-9a4afadf4c3f.jpg'>
<img src='crazySSM03-mvc-tags\51011f41-2509-4dd0-b75c-42a9d498dd46.jpg'>

控制器：

<img src='crazySSM03-mvc-tags\64da165a-e344-409a-8fd3-04b5aee1836b.jpg'>

渲染：

<img src='crazySSM03-mvc-tags\655f56dd-6012-466c-ac7b-110769029849.jpg'>










