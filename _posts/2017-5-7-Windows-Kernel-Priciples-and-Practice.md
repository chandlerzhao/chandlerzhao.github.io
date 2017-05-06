---
layout: default
title: Windows内核原理与实践读书笔记
---

# Windows内核原理与实践读书笔记


参考书目：  
《Windows Internals》(深入解析Windows操作系统 - (Mark Russinovich,David Solomon)  
辅助材料：  
Windows DDK  
Windows Research Kernel v1.2

## 概要
### 第一章
操作系统的基础概念、Windows操作系统的发展历史、Windows内核的发展

### 第二章
现代操作系统的基本模型、Windows的总体结构、WRK  
内核相关的基本概念

### 第三章
Windows中的进程和线程管理  
句柄表结构、进程和线程的创建和结束、系统的初始进程和线程  
线程调度

### 第四章
内存管理：页式内存管理和段式内存管理  
系统地址空间、进程地址空间、虚拟内存、内存区对象  
页面交换机制、物理内存管理、Windows工作集  

### 第五章
并发和同步机制、中断和异常处理机制、IRQL、DPC、APC、异常分发过程

### 第六章
IO模型：I/O管理器、即插即用管理器、电源管理器  
设备驱动程序的初始化  
驱动程序对象、设备对象、文件对象的数据结构  
设备的列举过程、电源IO请求的处理过程
驱动程序设备栈结构
IO处理：IRP的定义、IO请求的处理过程、IO完成处理

### 第七章
缓存管理器、卷的管理、文件系统  
RAW、FAT、NTFS的实现

### 第八章
系统服务  
用户模式代码如何调用内核模式系统服务  
系统服务分发机制  
跨进程通信系统服务：LPC、命名管道、邮件槽

### 第九章
网络结构、Windows子系统、内核日志

### 附录
编译、运行与调试WRK

## 
可信计算(Trustworthy Computing)  
从Windows Server 2003 和 Windows XP 开始引入64位版本  

下一代：Windows Server 2008、Windows Vista  
Windows Server 2008 不再的区分单处理器和多处理器版本
从此开始NTFS文件系统不用重新启动即可自我修复

下一代：Windows Server 2008 R2、Windows 7（与Windows Vista 完全兼容、注重性能提升、XPmode）
Windows Server 2008 R2 支持 64个物理处理器或256个逻辑处理器。

Windows XP - NT5.1
Windows XP SP2 /64位版本- NT5.2 (->WRK)
Windows Vista /SP1 - NT 6.0
Windows 7 - NT 6.1

WRK 可被编译成为一个EXE，替换到一个NT5.2系统中