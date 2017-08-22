---
layout: post
title:  "Soapui导入wsdl报错"
date:   2017-08-22 14:24:30
keywords: 
description: Soapui导入wsdl报错method
categories: Soapui,wsdl
comment: false
---
# Soupui导入wsdl报错

![A simpleContent extension must define a base type](/resources/15033859071220.jpg)



**发现问题**：测试Webservice接口，发现soapui导入报错，报错内容见上图；

`A simpleContent extension must define a base type`

**问题原因**：wsdl中定义有问题，在simplecontent中必须有extension或者restriction内容，见[http://www.voidcn.com/blog/caolaosanahnu/article/p-4657179.html](http://www.voidcn.com/blog/caolaosanahnu/article/p-4657179.html)；全文搜索simplecontent，发现问题wsdl中有如下段

```
<complexTypename="Version">
    <simpleContent>
        <extension/>
    <simpleContent>
</complexType>
```
**解决方法**：下载wsdl文件，将以上内容修改为

```
<complexTypename="Version">
    <simpleContent>
        <extensionbase="xsd:string"/>
    </simpleContent>
</complexType>
```

通过修改后的文件导入成功。

