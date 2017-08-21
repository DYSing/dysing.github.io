---
layout: post
title:  "JAVA split 分割 字符串"
date:   2017-08-21 19:59:29
keywords: 
description: JAVA split 分割 字符串
categories: 
comment: false
---
# JAVA split 分割 字符串

split在Java中肯定是个常用方法，用于字符串分割。用的多不代表用的好，一不小心就给自己挖坑了。

```
String tmp = "10.5.1.1";
String resultStrings[] = tmp.split(".");
if("1".equals(resultStrings[2]){
//Do Something
}
```
判断条件就是进不去，恩，调试一下发现，split没有正确分割。恍然大悟，原来是特殊字符的问题。
下面直接粘贴一段网上的内容吧：

### 【1】单个符号作为分隔符 

```
String address="上海|上海市|闵行区|吴中路";

String[]splitAddress=address.split("\\|");//如果以竖线为分隔符，则split的时候需要加上两个斜杠【\\】进行转义

System.out.println(splitAddress[0]+splitAddress[1]+splitAddress[2]+splitAddress[3]);


Stringaddress="上海*上海市*闵行区*吴中路";

String[]splitAddress=address.split("\\*");

System.out.println(splitAddress[0]+splitAddress[1]+splitAddress[2]+splitAddress[3]);


Stringaddress="上海:上海市:闵行区:吴中路";

String[]splitAddress=address.split("\\:");

System.out.println(splitAddress[0]+splitAddress[1]+splitAddress[2]+splitAddress[3]);


Stringaddress="上海.上海市.闵行区.吴中路";

String[]splitAddress=address.split("\\.");

System.out.println(splitAddress[0]+splitAddress[1]+splitAddress[2]+splitAddress[3]);

Stringaddress="上海^上海市^闵行区^吴中路";

String[]splitAddress=address.split("\\^");

System.out.println(splitAddress[0]+splitAddress[1]+splitAddress[2]+splitAddress[3]);


Stringaddress="上海@上海市@闵行区@吴中路";

String[]splitAddress=address.split("@");

System.out.println(splitAddress[0]+splitAddress[1]+splitAddress[2]+splitAddress[3]);


Stringaddress="上海,上海市,闵行区,吴中路";

String[]splitAddress=address.split(",");

System.out.println(splitAddress[0]+splitAddress[1]+splitAddress[2]+splitAddress[3]);
```

### 【2】多个符号作为分隔符

```
String address="上海^上海市@闵行区#吴中路";

String[]splitAddress=address.split("\\^|@|#");

System.out.println(splitAddress[0]+splitAddress[1]+splitAddress[2]+splitAddress[3]);
```
---
### 格式小提示
---

```
String address = newString("192.168.13.240");

String[] str = address.split("\\.");

for(String s : str){

System.out.println(s);

}

```
```
输出格式：

192

168

13

240
```
```
System.out.println(splitAddress[0]+splitAddress[1]+splitAddress[2]+splitAddress[3]);
```
```
输出格式：上海上海市闵行区吴中路
```
---


**总结：**

```
（1）split表达式，其实就是一个正则表达式。*  ^ |等符号在正则表达式中属于一种有特殊含义的字符，如果使用此种字符作为分隔符，必须使用转义符即\\\加以转义。

（2）如果使用多个分隔符则需要借助 |符号，如【2】所示，但需要转义符的仍然要加上分隔符进行处理。
```

[原文链接](http://blog.sina.com.cn/s/blog_b6487d470101g0hp.html)

