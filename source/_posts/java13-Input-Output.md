---
title: java13 输入输出
date: 2020-02-22 12:35:29
tags: java
---

## File

### 构造函数

<img src='java13-Input-Output\6e474c70-40a0-442a-8a83-c69d4c79bdf3.jpg'>

当path为路径，则为文件夹，为文件，则为文件。

### 获取文件名称、路径、绝对路径、父路径

<img src='java13-Input-Output\c63c27b9-c26c-4ea1-aa6e-94d0e8bbf758.jpg'>

### 文件存在性、文件及路径、读写权限判断

<img src='java13-Input-Output\01a13b80-c274-4b41-a18b-ca86408d835e.jpg'>

### 文件删除、重命名、上一次修改时间、文件大小

<img src='java13-Input-Output\6337cf92-17e1-4c25-89d7-5dc520ac3ade.jpg'>

### 创建目录、列出文件

<img src='java13-Input-Output\1e0420cd-1c35-4e3e-bc20-db54b5175d11.jpg'>

FileNameFilter对文件名称过滤：

<img src='java13-Input-Output\634b5026-4b00-45a7-9694-f3f6473969c9.jpg'>

FileFilter对文件过滤：

<img src='java13-Input-Output\39d024e7-6d59-4209-8455-4db1d20ffcec.jpg'>

### 使用案例

<img src='java13-Input-Output\e292d599-5224-4e6b-95fe-0817f5b6cca8.jpg'>

自定义过滤器:

<img src='java13-Input-Output\3ba4e6d9-6a93-4e04-a5f5-309761717047.jpg'>

## File Systems and Paths

FileSystem代表一个文件系统。它是一个抽象类。

### 获取FileSystem对象

<img src='java13-Input-Output\2b912a34-df1d-41d1-a1aa-e522dd575f4f.jpg' >

### 获取分割符

<img src='java13-Input-Output\ae620946-4f88-4327-94ef-5cb232cca4ee.jpg'>

win下是\，Linux下是/

### 获取根目录

<img src='java13-Input-Output\6c777170-1972-4c5c-bfe4-98f0d1ef2abf.jpg' >

获取到一个Iterable<Path>

### 获取一个路径

<img src='java13-Input-Output\de2eb829-01c9-43a4-9c2a-7d574a879b2c.jpg'>

后续的参数可以用于拼接

<img src='java13-Input-Output\cc37d25e-0add-4e45-9bd0-1c48242cbf92.jpg'>

java.nio.file.Paths也提供了类似的方法：

<img src='java13-Input-Output\acbba703-b077-4b47-bd49-5d5939b7c05f.jpg' >

<pre style='background:#e6e6e6;padding=10px;'>

//获取名称
Path getName(int index)

Path path = Paths.get("/home/user/images");
System.out.println(path.getNameCount()); // prints 3
System.out.println(path.getName(0)); // prints home
System.out.println(path.getName(1)); // prints user
System.out.println(path.getName(2)); // prints images

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

//获取文件名
Path getFileName()

//获取父目录
Path getParent()

//获取根目录
Path getRoot()

</pre>

## 文件目录操作

<code style='background:#ff3385;color:white;padding:5px;'>Files</code>类的方法：

### 创建文件

<img src='java13-Input-Output\45740644-0457-4b80-a7e0-e385448a3343.jpg'>

### 创建路径

<img src='java13-Input-Output\c5579496-a47a-456a-b246-a889d3c64d77.jpg'>

### 删除文件、路径、链接

<img src='java13-Input-Output\4138a502-0afb-454d-bb08-9c7de77517d8.jpg'>

如果路径不存在将抛出异常，为此，可以使用以下方法：

<img src='java13-Input-Output\1a302b1c-bc59-4d1b-898f-0fa774117f13.jpg' >

### 操作目录

<img src='java13-Input-Output\c31932b7-052d-4677-a187-60cd99cb4689.jpg'>

使用<code style='background:#ff3385;color:white;padding:5px;'>DirectoryStream</code>对目录进行遍历(注意资源释放)：

<pre style='background:#e6e6e6;padding=10px;'>

Path parent = ...
try (DirectoryStream<Path> children =
&nbsp;&nbsp;Files.newDirectoryStream(parent)) {
&nbsp;&nbsp;&nbsp;&nbsp;for (Path child : children) {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;System.out.println(child);
&nbsp;&nbsp;}
} catch (IOException e) {
&nbsp;&nbsp;e.printStackTrace();
}

</pre>

### 文件复制

<pre style='background:#e6e6e6;padding=10px;'>

public static Path copy(Path source, Path target,CopyOption... options)

</pre>

StandardCopyOption包含以下几种枚举：

ATOMIC_MOVE（原子操作）

COPY_ATTRIBUTES（复制文件属性）

REPLACE_EXISTING（覆盖已有文件）

示例代码：

<img src='java13-Input-Output\2e3fdbef-974e-4e02-ab5d-10d2a6ed1162.jpg'>

### 文件移动

<pre style='background:#e6e6e6;padding=10px;'>

public static Path move(Path source, Path target,CopyOption... options) throws java.io.IOException

</pre>

示例代码：

<img src='java13-Input-Output\9341c8e5-24bf-4fea-a2b4-03b8d14c069f.jpg'>

## 读写文件

Files类可以读写小型文本或二进制文件。

### 读取

读取<code style='background:#ff3385;color:white;padding:5px;'>二进制</code>文件：

<pre style='background:#e6e6e6;padding=10px;'>

public static byte[] readAllBytes(Path path)
         throws java.io.IOException

</pre>

读取<code style='background:#ff3385;color:white;padding:5px;'>字符串</code>文本：

<pre style='background:#e6e6e6;padding=10px;'>

public static List<String> readAllLines(Path path,java.nio.charset.Charset charset)   
         throws java.io.IOException

</pre>

### 写入

写入<code style='background:#ff3385;color:white;padding:5px;'>二进制</code>：

<pre style='background:#e6e6e6;padding=10px;'>

public static Path write(Path path, byte[] bytes,OpenOption... options) 
          throws java.io.IOException

</pre>

写入<code style='background:#ff3385;color:white;padding:5px;'>文本</code>：

<pre style='background:#e6e6e6;padding=10px;'>

public static Path write(Path path, java.lang.Iterable<? extends CharSequence> lines, java.nio.charset.Charset charset,OpenOption... options)
           throws java.io.IOException

</pre>

StandardOpenOption选项：

APPEND追加

CREATE如果不存在则创建

CREATE_NEW不存在则创建，否则抛出异常

DELETE_ON_CLOSE文件关闭时，删除

READ读取

WRITE写入

TRUNCATE_EXISTING文件存在则清空内容

SPARSE稀疏文件

SYNC同步内容和元数据写入

DSYNC同步内容写入

编码方法：

<img src='java13-Input-Output\4e138aef-9edf-4e05-b947-284f5451cbbb.jpg'>

读写示例：

<img src='java13-Input-Output\e220392e-3c3e-43eb-a79e-cdf41b7db454.jpg'>

## 输入输出流

<img src='java13-Input-Output\3b9e05b0-7244-4023-a0a1-8733fa097ec4.jpg'>

<table cellpadding='8' border='1' style='background:#EAF2D3;text-align:center'>
<tr>
&nbsp;<td>
类型
&nbsp;</td>
&nbsp;<td>
描述
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
Reader
&nbsp;</td>
&nbsp;<td>
读取字符
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
Writer
&nbsp;</td>
&nbsp;<td>
写入字符
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
InputStream
&nbsp;</td>
&nbsp;<td>
二进制读取流
&nbsp;</td>
</tr>

<tr>
&nbsp;<td>
OutputStream
&nbsp;</td>
&nbsp;<td>
二进制输出流
&nbsp;</td>
</tr>

</table>

### 二进制流

InputStream:

<img src='java13-Input-Output\76ed70e6-16c6-4881-9af1-af9df7b6bda5.jpg'>

OutputStream:

<img src='java13-Input-Output\6b7aa4d8-2d11-4f08-b119-268000c9638b.jpg'>

<img src='java13-Input-Output\ef6ac255-9855-4e3a-8c98-a476d7e22e67.jpg'>

### 字符流

<img src='java13-Input-Output\a226164e-7872-41c1-900a-0a25c20f7c8a.jpg'>



## 读取二进制数据

### FileInputStream

<img src='java13-Input-Output\c16c89c0-7343-4838-bf4c-171d00f5f162.jpg'>

### FileOutputStream

<img src='java13-Input-Output\91be83ec-a19d-432a-a44d-5e68e3fa71d2.jpg'>

通过append参数判定是否追加数据

### BufferedInputStream

<img src='java13-Input-Output\78e52ea7-1795-4291-ba3a-a9eeb3693420.jpg'>

### BufferedOutputStream

<img src='java13-Input-Output\49b59bf5-9f97-42c0-85b2-6617102afeea.jpg'>

<img src='java13-Input-Output\11740d87-f39e-4e0e-813a-016fc199d413.jpg'>

java7之前可以new一个FileInputStream，现在也可以使用Files类创建：

<img src='java13-Input-Output\9d766191-db65-498b-9989-a1bbca527a91.jpg'>

示例代码：

<pre style='background:#e6e6e6;padding=10px;'>

Path path = ...
try (InputStream inputStream = Files.newInputStream(path,
&nbsp;&nbsp;StandardOpenOption.READ) {
&nbsp;&nbsp;// manipulate inputStream
} catch (IOException e) {
&nbsp;&nbsp;// do something with e
}

</pre>

为了提升效率，使用BufferedInputStream:

<pre style='background:#e6e6e6;padding=10px;'>

Path path = ...
try (InputStream inputStream = Files.newInputStream(path,StandardOpenOption.READ);
&nbsp;&nbsp;&nbsp;&nbsp;BufferedInputStream buffered = new BufferedInputStream(inputStream)) {
&nbsp;&nbsp;// manipulate buffered, not inputStream
} catch (IOException e) {
&nbsp;&nbsp;// do something with e
}

</pre>

### 读取数据

<img src='java13-Input-Output\b9a52e27-41ad-4839-bdcb-4b6ed85e83b4.jpg'>

到达流的末尾时，返回-1

### 获取可读取数据大小

<img src='java13-Input-Output\8ef3fdca-8683-4667-b354-4bef867b081f.jpg'>

### 跳过指定个数字节

<img src='java13-Input-Output\e2d061c2-e47e-4d26-a60f-b7887650b9a2.jpg'>

### 标记位置

<img src='java13-Input-Output\02fd782e-ede8-4972-8feb-2fe62f6dedd7.jpg'>

### 返回标记处

<img src='java13-Input-Output\5950ae67-ccbd-4aa1-9cf2-90d16b7f8659.jpg'>

### 关闭流

<img src='java13-Input-Output\c04ec6cd-888b-4186-9e8c-89f5b5ef9053.jpg'>

## 写入二进制数据

<img src='java13-Input-Output\11f79073-169c-4005-a6f2-b3e8143ee5e1.jpg'>

java7之前可以new一个FileOutputStream，现在也可以使用Files类创建：

<img src='java13-Input-Output\1f99320b-e33b-4607-a396-0d39b70f94cb.jpg'>

示例代码：

<pre style='background:#e6e6e6;padding=10px;'>

Path path = ...
try (OutputStream outputStream = Files.newOutputStream(path,
StandardOpenOption.CREATE, StandardOpenOption.APPEND) {
&nbsp;&nbsp;// manipulate outputStream
} catch (IOException e) {
&nbsp;&nbsp;// do something with e
}

</pre>

为了提高效率，使用缓冲流：

<img src='java13-Input-Output\800a89fd-2c2d-437d-bbd4-08e34bf6146d.jpg'>

### 写入数据

<img src='java13-Input-Output\7790c7f6-7eec-4472-a942-f58c66b7f292.jpg'>

### 关闭流、刷新流

close用于关闭，一般使用try结构即可。

flush方法用于将数据刷新写入。

数据写入示例：

使用Files创建输入输出流：

<img src='java13-Input-Output\072c515d-ac0d-4184-9713-09f7f080e0e4.jpg'>

FileInputStream、FileOutputStream：

<img src='java13-Input-Output\a45c178e-a249-4634-842a-a8f963e13b4d.jpg'>

使用BufferInputStream、BufferedOutputStream:

<img src='java13-Input-Output\c170c7bc-7453-48d9-8110-e5beaf909f81.jpg'>

## 写文本

<img src='java13-Input-Output\629ef8df-1105-457f-ade2-ad223636ddb0.jpg'>

## Writer

### 写入文本

<img src='java13-Input-Output\291d4940-4cbb-4970-a2bd-b240667aec9f.jpg'>

也可以写入字符串：

<img src='java13-Input-Output\3c52b39e-36e1-4422-a1c7-3503a3c1ea01.jpg'>

### FileWriter

<img src='java13-Input-Output\2895d9db-f7e2-4e78-b36a-45eed77b9277.jpg'>

### OutputStreamWriter

<img src='java13-Input-Output\a6443ff0-3374-48bf-af0e-f7b3f1449244.jpg'>

按照指定的编码方式进行写入。

写入文件时，可以使用OutputStream和OutputStreamWriter包装：

<pre style='background:#e6e6e6;padding=10px;'>

OutputStream os = Files.newOutputStream(path, openOption);
OutputStreamWriter writer = new OutputStreamWriter(os, charset);

</pre>

使用示例：

<img src='java13-Input-Output\c457a25f-a193-41b6-b2a3-6729737c5b03.jpg'>

### PrintWriter

相比来说，PrinterWriter更好用：

<img src='java13-Input-Output\442af3ce-b0f4-40d4-911d-ba258babea27.jpg'>

它的print方法支持大量类型：

<img src='java13-Input-Output\fe3ed325-c039-4c8d-b19e-3d388181d86d.jpg'>

同样，它也包含大量println方法，自动换行。

为了提升性能，包装一层缓冲流：

<img src='java13-Input-Output\271d3878-73b2-4735-bfff-a178a3050fbc.jpg'>

使用示例：

<pre style='background:#e6e6e6;padding=10px;'>

PrintWriter pw = new PrintWriter(new BufferedWriter(writer));

</pre>

完整示例：

<img src='java13-Input-Output\c0e9ba62-9190-461e-a8a4-7be61b8e9e0c.jpg'>

## 读取文本

<img src='java13-Input-Output\c753ffc8-f23c-4ac5-9180-941e891c2163.jpg'>

### 读取文本数据

<img src='java13-Input-Output\43cebc83-18d2-4a27-aa14-e6411a72e75d.jpg'>

直接读取char[]数组数据。

也可以将数据读入NIO的CharBuffer:

<img src='java13-Input-Output\9890dbaf-7e9c-406e-bb5d-aec4877eb4f3.jpg'>

### FileReader

<img src='java13-Input-Output\c8f3572f-bcaa-4063-879c-eff58e4c06ee.jpg'>

## InputStreamReader

可以读取二进制流，按照指定的编码格式转换成字符。

<img src='java13-Input-Output\b3d3ee62-7c53-4887-ad79-a46fb6c9c6e7.jpg'>

使用示例：

<pre style='background:#e6e6e6;padding=10px;'>

Path path = ...
Charset charset = ...
//创建InputStream
InputStream inputStream = Files.newInputStream(path,StandardOpenOption.READ);
//构造InputStreamReader
InputStreamReader reader = new InputStreamReader(inputStream, charset);

</pre>

## BufferedReader

使用BufferedReader可以提升读取性能。

<img src='java13-Input-Output\ffba17e2-88d1-4b9b-8abd-869e67071911.jpg'>

在NIO中，Files提供了以下构造方法：

<pre style='background:#e6e6e6;padding=10px;'>

public static java.io.BufferedReader newBufferedReader(Path path,java.nio.charset.Charset charset)

</pre>

使用示例：

<pre style='background:#e6e6e6;padding=10px;'>

Path path = ...
BufferedReader br = Files.newBufferedReader(path, charset);
String line = br.readLine();
while (line != null) {
    System.out.println(line);
    line = br.readLine();
}

</pre>

也可以包装InputStreamReader:

<pre style='background:#e6e6e6;padding=10px;'>

public static String getUserInput() {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    try {
        return br.readLine();
    } catch (IOException ioe) {
    }
    return null;
}

</pre>

## BufferedWriter

<img src='java13-Input-Output\6c57c813-ccd4-4fce-ad37-b239c045e61d.jpg'>

使用缓冲读写器可以提高读写效率。

使用实例：

<img src='java13-Input-Output\872e9643-2312-4717-9a0d-d9c0eb6ebd0e.jpg'>

### 使用OutputStreamWriter及BufferedWriter高效读写文本

<img src='java13-Input-Output\463d9f75-5767-45ab-a2d0-2c8bd564832a.jpg'>


## PrintStream

PrintStream是一种输出流，类似于PrintWriter,构造函数如下：

<pre style='background:#e6e6e6;padding=10px;'>

public PrintStream(OutputStream out)
public PrintStream(OutputStream out, boolean autoFlush)
public PrintStream(OutputStream out, boolean autoFlush,String encoding)

</pre>

<img src='java13-Input-Output\6eb26a88-d7cc-41bc-b27c-e7be21f73b74.jpg' >

建立<code style='background:#ff3385;color:white;padding:5px;'>OutputStream</code>，操作文件。使用<code style='background:#ff3385;color:white;padding:5px;'>Print Stream</code>包装一层。将System的<code style='background:#ff3385;color:white;padding:5px;'>标准输出</code>设置为PrintStream。

## Random Access Files

随机读取文件的需求如下：

对文件的随机读取是对文件的指定位置的随机访问而不是从头到尾依次读取，类似于List和LinkedList的区别。
实现文件的随机访问有两种方式：

1. RandomAccessFile

2. SeekableByteChannel

<pre style='background:#e6e6e6;padding=10px;'>

SeekableByteChannel sbc = Files.newByteChannel(Path path, OpenOption... options);

//设置读写权限
SeekableByteChannel readOnlyByteChannel = Files.newByteChannel(path1, EnumSet.of(READ)));
SeekableByteChannel writableByteChannel = Files.newByteChannel(path2, EnumSet.of(CREATE,APPEND));

</pre>

获取当前指针的位置：

<pre style='background:#e6e6e6;padding=10px;'>

long position() throws java.io.IOException

</pre>

切换位置：

<pre style='background:#e6e6e6;padding=10px;'>

SeekableByteChannel position(long newPosition) throws java.io.IOException

</pre>

获取文件大小：

<pre style='background:#e6e6e6;padding=10px;'>

long size() throws java.io.IOException

</pre>

读取写入：

<pre style='background:#e6e6e6;padding=10px;'>

int read(java.nio.ByteBuffer buffer) throws java.io.IOException

int write(java.nio.ByteBuffer buffer) throws java.io.IOException

</pre>

## 使用FileWriter、FileReader文本读写

<img src='java13-Input-Output\fca0299a-e830-4df4-92ff-9f1cc15d16ce.jpg'>

## ByteBuffer

ByteBuffer是Buffer的一种实现，还有CharBuffer, DoubleBuffer, FloatBuffer, IntBuffer, LongBuffer, ShortBuffer

ByteBuffer的一种简单的构造方法：

<img src='java13-Input-Output\503b5f71-6570-40de-8d51-b5cd1f91bced.jpg' >

示例：

<pre style='background:#e6e6e6;padding=10px;'>

ByteBuffer byteBuffer = ByteBuffer.allocate(100);

</pre>

在ByteBuffer内部维护了一个Byte Array，可以通过以下方法获得：

<img src='java13-Input-Output\b446df6a-bc89-4c42-bbf4-b0cafc16e565.jpg'>

ByteBuffer的几种读写方法：

<pre style='background:#e6e6e6;padding=10px;'>

//直接添加
public abstract ByteBuffer put(byte b)
//在指定位置添加
public abstract ByteBuffer put(int index, byte b)
//添加数组
public ByteBuffer put(byte[] src)
//添加数组的一部分
public ByteBuffer put(byte[] src, int offset, int length)

//添加指定类型
public abstract ByteBuffer putInt(int value)
public abstract ByteBuffer putInt(int index, int value)

//读取
public abstract byte get()
public abstract byte get(int index)
public abstract float getFloat()
public abstract float getFloat(int index)

</pre>

SeekableByteChannel操作完整示例：

1. 创建ByteBuffer并添加数据

<img src='java13-Input-Output\12aecef2-9d59-48ac-92b5-e9ed03fc2036.jpg'>

2. 创建SeekableByteChannel，写入数据

<img src='java13-Input-Output\b05dbf43-b103-4db5-8310-0b8462b4ba3d.jpg'>


## 对象的序列化

对对象进行序列化可以用于存储对象状态，通过网络进行传输。再进行反序列化即可还原。对象进行序列化，需要实现Serializable接口。

1. 构造ObjectOutputStream

<pre style='background:#e6e6e6;padding=10px;'>

public ObjectOutputStream(OutputStream out)

</pre>

2. 添加数据

<pre style='background:#e6e6e6;padding=10px;'>

public void writeBoolean(boolean value)
public void writeByte(int value)
public void writeBytes(String value)
public void writeChar(int value)
public void writeChars(String value)
public void writeDouble(double value)
public void writeFloat(float value)
public void writeInt(int value)
public void writeLong(long value)
public void writeShort(short value)
public void writeObject(java.lang.Object value)

</pre>

反序列化的过程：

1. 构造ObjectInputStream

<pre style='background:#e6e6e6;padding=10px;'>

public ObjectInputStream(InputStream in)

</pre>

2. 读取数据

<pre style='background:#e6e6e6;padding=10px;'>

public boolean readBoolean()
public byte readByte()
public char readChar()
public double readDouble()
public float readFloat()
public int readInt()
public long readLong()
public short readShort()
public java.lang.Object readObject()

</pre>

完整示例：

序列化：

<img src='java13-Input-Output\82b2ad15-e3ea-4a99-a10b-b23c2badf47f.jpg'>

反序列化：

<img src='java13-Input-Output\d6aa4170-5154-4ee6-90b0-cc0ca64a4a1c.jpg'>









