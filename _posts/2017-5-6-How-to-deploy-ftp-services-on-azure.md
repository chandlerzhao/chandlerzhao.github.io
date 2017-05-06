---
layout: default
title: 如何在Windows Azure上部署FTP服务
---

## 如何在Windows Azure上部署FTP服务

最近做项目需要把项目部署到公有云上面去（其实是有一千多块的Azure的优惠券可以使用，不用白不用），传文件就成了一个问题。
我使用的是Windows Server 2008虚拟机，为了避免在centos上无法使用forever将nodejs服务器驻留至后台，nohup命令也不是那么好用，故改用Windows Server 2008，相比2012更简单一些。

> 这里多说一句。centos下学长建议我用WinSCP传文件，我所知道的一个最明显的好处就是会对数据进行加密。但是带来的一个麻烦是：如果你使用httpd服务器，更改默认的文档根目录/var/www/html下的文件需要root权限，WinSCP没有办法单独

在Azure经典管理界面创建好虚拟机之后，我们可以直接单击页面下方的connect按钮下载自动生成的rdp远程桌面配置文件。
可惜的是远程桌面并未提供文件的传输服务，也就无法直接通过拖拽的方式上传。

自然想到了ftp。

Ftp其实是一个挺复杂的协议，并不仅仅是开放一个21端口那么简单。
