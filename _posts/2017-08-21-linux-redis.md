---
layout: post
title:  "Linux环境下Redis安装搭建"
date:   2017-08-21 19:11:50
keywords: 
description: Linux环境下Redis安装搭建
categories: Redis,Linux
comment: false
---
# Linux环境下Redis安装搭建

可以提前准备Redis安装包，下载地址如下：

`https://redis.io/download`
或者下载源码进行编译，以下为通过源码编译的步骤：

1、下载源码，解压缩后编译源码。

```
$ wget http://download.redis.io/releases/redis-4.0.1.tar.gz
$ tar xzf redis-4.0.1.tar.gz
$ cd redis-4.0.1
$ make
```
2、编译完成后，启动redis服务

`$ src/redis-server`

特别的，在一般的生产环境中，需要后台运行redis服务，所以需要修改redis配置文件方法如下： 
在安装redis之后，我们可以可以找到一个叫`redis.conf`的文件，通过`vi`命令打开：
```
vi redis.conf
```
找到`redis.conf`文件的`daemonize no`处 
修改为`daemonize yes`

然后启动redis服务（启动方式和之前不同）

`./redis-server ../redis.conf`

成功运行

**补充**：

```
Redis采用的是单进程多线程的模式。
当redis.conf中选项daemonize设置成yes时，代表开启守护进程模式。
在该模式下，redis会在后台运行，并将进程pid号写入至redis.conf选项pidfile设置的文件中，此时redis将一直运行，除非手动kill该进程。
但当daemonize选项设置成no时，当前界面将进入redis的命令行界面，exit强制退出或者关闭连接工具(putty,xshell等)都会导致redis进程退出。
```
**服务端开发的大部分应用都是采用后台运行的模式**


