---
title: springBoot2-14-spring-security
date: 2020-07-09 14:19:01
tags: spring-boot-2
---

## Spring Security专门提供认证模块

### 引入依赖

<img src='springBoot2-14-spring-security\5a33a4c6-8024-42d0-a30a-3caf77de2615.jpg'>

### 基于数据库的认证

1. 创建角色表

<img src='springBoot2-14-spring-security\a1b61cb7-8790-4482-8a5a-1b3c5993e9b4.jpg'>

2. 创建用户表

<img src='springBoot2-14-spring-security\ec655a2b-1d95-474b-90ce-5e640a9a37f0.jpg'>

3. 创建用户角色映射表

<img src='springBoot2-14-spring-security\bc095ccb-6459-4fbf-b56e-71791df4c955.jpg'>

4. 创建WebSecurityConfigurerAdapter的子类，配置安全策略

<img src='springBoot2-14-spring-security\0190007e-762f-4b26-a8e0-b7fd65481dbb.jpg'>
<img src='springBoot2-14-spring-security\db909faa-369d-4f5c-9d21-b1f837dba091.jpg'>

5. 添加二次加密(附加功能)

配置密钥：

<img src='springBoot2-14-spring-security\ea6ee27f-2999-4cd0-8571-08729e955d92.jpg'>

替换BCryptPasswordEncoder为Pbkdf2PasswordEncoder:

<img src='springBoot2-14-spring-security\9ad8810d-265d-451d-a636-736735d7302f.jpg'>

### 用户自定义的认证方式

1. 实现UserDetailsService接口，提供loadUserByUsername方法。

<img src='springBoot2-14-spring-security\bafa99d5-67ab-4a4d-9071-115dfb9d984f.jpg'>
<img src='springBoot2-14-spring-security\6cc05b89-2733-42f8-9d7d-a5731fdd765f.jpg'>
<img src='springBoot2-14-spring-security\eed93d93-da48-4abb-93ec-6396ba4c66f7.jpg'>

这里，loadUserByUsername方法，输入用户名参数，通过自定义的用户及角色管理服务获取用户的信息及角色信息，通过changeToUser方法转换为UserDetails对象。

changeToUser方法提供了new User(String userName, String pwd, List<GrantedAuthority> authorities)方法创建UserDetails对象。

2. 将服务注册到WebSecurityConfigurerAdapter

<img src='springBoot2-14-spring-security\b540aa89-9d36-4994-97f2-4caaf24bb453.jpg'>
<img src='springBoot2-14-spring-security\68991321-5e4c-48d4-8128-2aa60b1915a3.jpg'>

配置AuthenticationManagerBuilder的userDetailsService()方法设定为自定义的服务。

## Spring鉴权

1. configure(HttpSecurity security)方法配置权限问题

<img src='springBoot2-14-spring-security\235a0e61-cf1a-4d5d-ad2f-d22a0bcefc7b.jpg'>

常用配置项：

<img src='springBoot2-14-spring-security\854d32d6-1bbe-4bbf-903a-330af86184a7.jpg'>

2. 也可以使用正则表达式

<img src='springBoot2-14-spring-security\4a39059d-37f4-42ae-a2c2-6d947d174778.jpg'>

3. access配合SPEL表达式

<img src='springBoot2-14-spring-security\2af71d9b-8f07-4db0-ae63-3ee941543077.jpg'>

常用的方法：

<img src='springBoot2-14-spring-security\74024b2c-36bc-4683-b357-c1dd0867b91d.jpg'>

4. 限定使用https

<img src='springBoot2-14-spring-security\988e632c-0c27-46b8-8f31-b76a3607e37b.jpg'>

requiresChannel().antMatchers(String express).requiresSecure()限定https

requiresChannel().antMatchers(String express).requiresInsecure()限定非https

5. 跨站请求伪造防御

默认开启跨站请求伪造防御，使用_csrf生成的隐藏字段进行防御：

<img src='springBoot2-14-spring-security\19cfcacd-1584-4df8-a690-54dda0ae3b18.jpg'>

6. 自定义登录页、开启记住我功能

<img src='springBoot2-14-spring-security\7b5af9ca-6887-4685-aa21-07ef58557c01.jpg'>

使用rememberMe()开启记住我功能，tokenValiditySeconds(int seconds)有效时长，key()是页面上的字段名称

formLogin()开启登录页，loginPage()设定登陆页面路由地址，defaultSuccessUrl()设定登陆成功页面

7. 自定义登出界面

<img src='springBoot2-14-spring-security\0a06d980-e7b9-47a4-bcea-a03fd6ec498d.jpg'>





