---
title: java18 数据库操作
date: 2020-02-29 16:18:35
tags: java
---

## 四个步骤获取数据

1. 加载JDBC驱动

2. 获取JDBC连接

3. 创建SQL 语句实例java.sql.Statement

4. 获取数据java.sql.ResultSet

5. 释放连接

### 加载JDBC驱动

<pre style='background:#e6e6e6;padding=10px;'>

Class.forName("com.mysql.jdbc.Driver");

</pre>

为了防止无法找到，捕获异常

<pre style='background:#e6e6e6;padding=10px;'>

try {
    Class.forName("com.mysql.jdbc.Driver");
} catch (ClassNotFoundException e) {
    // process the exception or re-throw it
}

</pre>

### 获取JDBC连接

<pre style='background:#e6e6e6;padding=10px;'>

public static Connection getConnection(java.lang.String url) throws SQLException

public static Connection getConnection(java.lang.String url,java.lang.String userName, java.lang.String password) throws SQLException

</pre>

连接字符串示例：

<img src='java18-Java-Database-Connectivity\70610e18-1d9d-4352-a6a5-a9ea25fce062.jpg'>

### 创建SQL 语句实例java.sql.Statement

创建sql语句以便于数据库执行。

<pre style='background:#e6e6e6;padding=10px;'>

Statement statement = connection.createStatement();

</pre>

两种执行方式：查询与执行。

<img src='java18-Java-Database-Connectivity\88984ac3-c304-4db5-8e92-bcd14d595b6a.jpg'>

executeUpdate执行插入、删除、修改操作

executeQuery执行查询操作


PreparedStatement<code style='background:#ff3385;color:white;padding:5px;'>更好</code>：

<pre style='background:#e6e6e6;padding=10px;'>

PreparedStatement pStatement = connection.prepareStatement(java.lang.String sql);

</pre>

### 获取数据java.sql.ResultSet

ResultSet是查询数据的存储结果，开始时，其内部指针指向第0行，next可以移动指针到下一行，如果存在返回true，否则返回false

可以通过 getInt, getLong, getShort等获取列的值。GetString也是很常用的。

<img src='java18-Java-Database-Connectivity\ec7a8a04-9b10-427f-b713-eb5444339795.jpg'>

### 释放连接

安全释放连接的方法：

<pre style='background:#e6e6e6;padding=10px;'>

Connection connection = null;
PreparedStatement pStatement = null;
ResultSet resultSet = null;
try {
    connection = getConnection();
    pStatement = connection.prepareStatement(sql);
    resultSet = pStatement.executeQuery();
    while (resultSet.next()) {
        // manipulate the data here
    }
} catch (SQLException e) {
    throw newException;
} finally {
//此处捕获的异常，防止关闭时出现错误
    if (resultSet != null) {
        try {
            resultSet.close();
        } catch (Exception e) {
        }
    }
    if (statement != null) {
        try {
            statement.close();
        } catch (Exception e) {
        }
    }
    if (connection != null) {
        try {
            connection.close();
        } catch (Exception e) {
        }
    }
}

</pre>

在java7以后，更方便的方式即可实现自动释放：

<img src='java18-Java-Database-Connectivity\bbbbbd7e-e90c-45bc-a6a1-9ea1b6926e23.jpg'>

## java.sql.ResultSetMetaData

元数据就是数据表的格式数据

可以使用ResultSet对象获取元数据：

<pre style='background:#e6e6e6;padding=10px;'>

public ResultSetMetaData getMetaData() throws SQLException

</pre>

### 获取列数

<pre style='background:#e6e6e6;padding=10px;'>

public int getColumnCount() throws SQLException

</pre>

### 获取列名称

<pre style='background:#e6e6e6;padding=10px;'>

public java.lang.String getColumnName(int columnIndex)throws SQLException

</pre>

### 获取列类型

<pre style='background:#e6e6e6;padding=10px;'>

public int getColumnType(int columnIndex) throws SQLException

</pre>

