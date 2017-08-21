---
layout: post
title:  "PLSQL工具查询含有&符的SQL"
date:   2017-08-21 19:49:22
keywords: 
description: PLSQL工具查询含有&符的SQL
categories: 
comment: false
---
# plsql查询语句占位符提示输入值
```
select * from tmp where a = '&a';
```
![](resources/15033163076611.jpg)

 解决方式:
 把`&`替换成`chr(38) `
 
 ```
 select * from tmp where a = 'chr(38)a';
 ```

利用`&`可以将常用查询语句中的条件作为变量，每次执行SQL进行赋值，提高效率。

