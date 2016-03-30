---
layout: post
title:  "JAVA TCP通讯中文乱码"
date:   2016-03-29 22:00:15
keywords: Java,TCP,中文乱码
description: Java TCP协议中文乱码解决
categories: 
comment: true
duoshuokey: 20160329220015
---
## Java Socket通讯中中文乱码

今天写了一个Java 的Tcp小程序，调试时发现服务端接收到的中文显示为乱码。<br />
想了想，Java中对于输入输出都是流的概念。服务端也是通过

```java
socket.getInputStream();
```

获取信息。通常中文乱码就是字符集的问题。

综上，可以把输入流转换为`InputStreamReader`同时指定字符集来避免乱码的出现。

```java
BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(socket.getInputStream(),"UTF-8")); 
```
输出流同理

```java
BufferedWriter bufferWriter = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream(),"UTF-8"));
```

