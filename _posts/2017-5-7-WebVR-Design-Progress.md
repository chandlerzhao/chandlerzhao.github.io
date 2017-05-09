---
layout: default
title: WebVR毕业设计进度
---
# WebVR毕业设计进度

采用Three.js框架  
场景采用午门.obj，大小为13711KB，服务器位于北京Azure云  
场景完全加载时间为1~1.3分钟，这对于用户来说是不可忍受的

pathping 测试路由情况

需要搭建一台git服务器做版本管理。

使用了jquery.avgrund.js UI框架

~~在Windows Server 2008上安装Cygwin(简直是脱裤子放屁。。。)~~
（已经暂时放弃搭建git服务器）

IIS 日志分析器：Log Parser，Log Parser Studio，微软官方出品，  
下载地址（按顺序安装）：
1. [Log Parser](https://www.microsoft.com/en-us/download/details.aspx?displaylang=en&id=24659)
2. [Log Parser Studio 2.0](https://gallery.technet.microsoft.com/Log-Parser-Studio-cd458765)

安装完1后运行2中的LPS.exe，右下角<u>No Logs Specified!Click here to set!</u>中选择Add Files（这个软件有bug，亲测Add Folder不好用）。

如果要分析IIS日志，加入C:\inetpub\logs\LogFiles\W3SVC1中的日志文件
File菜单中新建一个查询，在查询窗口上方选择Log Type，此时LPS会帮你自动把对应的日志类型高亮出来。支持SQL语法。

场景采用cs_assault.obj

轨迹追踪服务器应该与可视化服务器分开运行，降低耦合度，方便调试。