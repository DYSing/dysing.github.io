---
layout: post
title:  "异常处理Property 'name' has no getter method"
date:   2017-08-22 14:24:30
keywords: 
description: 异常处理Property 'name' has no getter method
categories: JAVA,JSON,Exception
comment: false
---
# 异常处理Property 'name' has no getter method

在项目中进行json解析的时候遇到一个异常，网上找到一篇相关的文章，记录一下。

---

在处理一个json的时候，发现一个很怪的异常。

`Java.lang.NoSuchMethodException: Property 'name' has no getter method`

```
  import org.apache.commons.beanutils.PropertyUtils;  
   import java.util.Map;  
   publicclass Hello {  
   publicstaticvoid main(String[] args) throws Exception {  
      Map map = PropertyUtils.describe(new A("a"));  
    }  
   }  
   class A {  
   private String name;  
   public A(String name) {  
   this.name = name;  
    }  
   public A() {  
    }  
   public String getName() {  
   return name;  
    }  
   publicvoid setName(String name) {  
   this.name = name;  
    }  
   }  
```
发现这个异常来自`org.apache.commons.beanutils.PropertyUtils`类。
这个很怪的异常，可能来自3个原因：

1. **类需要定义为public**
2. **类可能需要定义一个包**
3. **Bean类需要序列化**

遇该问题对症下药即可。

[原文链接](http://blog.csdn.net/xiciliu/article/details/5788182)

