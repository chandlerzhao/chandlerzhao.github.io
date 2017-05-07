---
layout: default
title: 如何在Windows Server 2008上部署一个简单站点
---
# 如何在Windows Server 2008上部署一个简单站点
要开启的服务：IIS、FTP

1. 添加角色Web服务器(IIS)

2. 添加必要的角色服务:
静态内容、默认文档、目录浏览、HTTP错误、HTTP重定向  
HTTP日志记录、日志记录工具、请求筛选、静态内容压缩、IIS管理控制台、FTP Service  

3. 打开IIS管理器->FTP防火墙支持，数据通道端口范围如5000-5001,

4. 配置防火墙，开放20-21，5000-5001TCP端口
5. 配置VM的endpoint，同上
