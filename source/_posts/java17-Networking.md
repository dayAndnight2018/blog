---
title: java17 网络
date: 2020-02-29 14:28:36
tags: java
---
## URL解析

<img src='java17-Networking\d17276fe-9b57-4c87-addb-5635055776fe.jpg'>

## java.net.URL

### 构造器

<pre style='background:#e6e6e6;padding=10px;'>

public URL(java.lang.String spec)
public URL(java.lang.String protocol, java.lang.String host,java.lang.String file)
public URL(java.lang.String protocol, java.lang.String host, int port, java.lang.String file)
public URL(URL context, String spec)

</pre>

使用示例：

<img src='java17-Networking\68a76d94-d17c-415d-8fa5-2eaaf17508c5.jpg'>

### 解析URL地址

<pre style='background:#e6e6e6;padding=10px;'>

//获取文件
public java.lang.String getFile()
//获取host
public java.lang.String getHost()
//获取path
public java.lang.String getPath()
//获取port
public int getPort()
//获取协议
public java.lang.String getProtocol()
//获取查询字符串
public java.lang.String getQuery()

</pre>

### 读取资源

使用openStream获取资源：

<img src='java17-Networking\bbef70f3-feed-4501-a61e-bd07237d475c.jpg'>

## java.net.URLConnection

采用Url实例的openConnection可以获取URLConnection对象。

### 设置读取和写入

<pre style='background:#e6e6e6;padding=10px;'>

public void setDoInput(boolean value)
public void setDoOutput(boolean value)

</pre>

### 获取读取和写入

<pre style='background:#e6e6e6;padding=10px;'>

public boolean getDoInput()
public boolean getDoOutput()

</pre>

### 获得读取流

<img src='java17-Networking\655ab8b3-20c3-481c-a94b-5d124903429b.jpg'>

### 其他相关方法

<pre style='background:#e6e6e6;padding=10px;'>

//获取请求头
public java.lang.String getHeaderField(java.lang.String headerName)

//获取请求头时间
public long getHeaderFieldDate(java.lang.String headerName, long default)

//获取请求头键值对
public java.util.Map getHeaderFields()

//获取编码格式
public java.lang.String getContentEncoding()

//获取内容长度
public int getContentLength()

//获取内容类型
public java.lang.String getContentType()

//获取日期
public long getDate()

//获取过期时间
public long getExpiration()

</pre>

### 写入流

<img src='java17-Networking\93b5b1ca-d270-4468-ba88-f159b9359716.jpg'>

通过UrlConnection的对象getOutputStream()获取输出流.

## java.net.Socket

### 构造器

<pre style='background:#e6e6e6;padding=10px;'>

public Socket(java.lang.String host, int port)

</pre>

使用示例：

<img src='java17-Networking\299a105c-fbaa-4614-bddc-f061f586351c.jpg'>

### 读写Socket

getInputStream获取读取流，getOutputStream获取输出流

<img src='java17-Networking\2a0eaa8a-740d-4de6-b406-c7b2b420ec6c.jpg'>

## java.net.ServerSocket

### 构造器


<pre style='background:#e6e6e6;padding=10px;'>

public ServerSocket(int port, int backLog, InetAddress bindingAddress);

</pre>

使用示例：

<img src='java17-Networking\6a792bc5-8a5e-4bb9-984b-2c2fd9572a92.jpg'>

通过accept接受连接过来的Socket

其后的操作方法与Socket类似。

