---
layout: default
title: 如何在Cent OS下部署httpd服务
---

# 如何在Cent OS下部署httpd服务

在General或Minimal的CentOS安装下是没有安装httpd的。终端直接执行httpd会返回如下信息：
```bash
httpd start
bash: httpd: command not found...
```

那么就需要安装Apache httpd了。这里我们选择不安装全套的如lamp的bundle，而是单独安装httpd。
官网：
[http://httpd.apache.org/download.cgi](http://httpd.apache.org/download.cgi)

在download页面下载2.4.25版本的源代码包httpd-2.4.25.tar.bz2，我们决定自己编译。
官网上只有欧洲和美国的镜像，没有中国的，所以有必要科学上网
一般来说，相同的文件.tar.bz2比.tar.gz体积要小，网速慢的话会带来一些好处。

与此相关还要下载三个依赖包：
> **1. Apache Portable Runtime - 1.5.2**  
> **2. Apache Portable Runtime Utility - 1.5.4**  
> **3. PCRE**

下载地址：[http://apr.apache.org/download.cgi](http://apr.apache.org/download.cgi)

用WinSCP等工具传到服务器上去，我传到了主目录home下，分别解压缩
```bash
tar -xvf httpd-2.4.25.tar.bz2  
tar -xvf apr-1.5.2.tar.bz2  
tar -xvf apr-util-1.5.4.tar.bz2
```

运行：
```bash
su 
```

输入当前用户密码后，提升为root权限。

## 一、安装apr
进入apr目录，执行：
```bash 
./configure  
make  
make install
```
其中configure 的 --prefix=/usr/local/apr 可以不用加，因为configure脚本里的默认前缀是/usr/local，对于其他二者也是一样。

## 二、安装apr-utils
进入apr-utils目录，执行：
```bash
./configure  --with-apr=/usr/local/apr  
make

```


## 三、安装PRCE
直接
```bash
yum -y install pcre-devel 
```
安装之前可以运行一下
```bash
yum makecache fast
```
作用不知道是什么。。。更新缓存之类的。。。

## 四、安装httpd
```bash
./configure
make
make install
```

## 五、运行httpd
```bash
./httpd -k start
```

具体的httpd.conf配置先不写了。