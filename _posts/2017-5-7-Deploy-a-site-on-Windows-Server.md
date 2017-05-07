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

4. 添加FTP站点、添加用户、设置设置目录，注意绑定要选择**全部未分配**  

5. 设置ftp服务器中对应用户的授权规则

6. 打开gpedit.msc,计算机配置，Windows设置，安全设置，本地策略，用户权限分配，从网络访问此计算机加入对应的用户或组。  
本地策略，安全选项，设置“网络访问：本地账户的共享和安全模式”为经典模式  
参考：[MSDN:从网络访问此计算机](https://support.microsoft.com/zh-cn/help/823659/client,-service,-and-program-issues-can-occur-if-you-change-security-settings-and-user-rights-assignments)  
[如何处理iis ftp有权限用户不能登录问题](http://blog.sina.com.cn/s/blog_436d85c101000by4.html)

6. 配置高级安全Windows防火墙，开放入站21，出站20，入站出站5000-5001TCP端口
7. 配置VM的endpoint，同上
