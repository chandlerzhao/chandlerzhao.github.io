---
layout: default
title: OpenGL学习笔记
---
# OpenGL学习笔记
参考书：《计算机图形学（OpenGL版）（第三版）》，清华大学出版社  
OpenGL Programming Guide  
GPU Gems 1 (GPU精粹1)  
GPU Gems 2 (GPU精粹2)  
GPU Gems 3 (GPU精粹3)，清华大学出版社 

后面三本是比较高阶的书，不建议初学者使用


首先安装好显卡驱动
官网上这样说：
> In all three major desktop platforms (Linux, macOS, and Windows), OpenGL more or less comes with the system. However, you will need to ensure that you have downloaded and installed a recent driver for your graphics hardware.  

所以不用单独安装OpenGL库了。操作系统都自带的。但是你要安装一个<u>Windows SDK</u>，里面包含了OpenGL的头文件  
准备一个C/C++开发环境，这里~~准备使用Dev-C++~~   
暂时使用Visual Studio，DevC++的include路径补全功能暂时不太好用。。。

## 事件驱动编程
流程：  
系统“什么也不做，等待事件发生，事件发生再做指定的事”
系统维护一个事件队列，比如“按下J键”、“单击鼠标”、“重新调整窗口的大小”等，按照先来先服务的顺序处理这些信息  
### 什么叫回调函数
程序员编写一种函数，函数中包括事件发生时做什么事情的代码，这些函数在指定类型的事件发生时执行，这类函数被称为回调函数  
即：函数不立即执行，发生事件时再“回头执行”

## 注册回调函数 
回调函数和特定事件的关联过程称为注册回调函数，不同操作系统的接口与实现有所不同，不过OpenGL的实用工具包（glut）提供了一个统一的方式。如：
glutMouseFunc(myMouse);
myMouse是一个程序员编写的回调函数，glutMouseFunc是注册鼠标事件的函数

目前主要用到四种OpenGL库：

1. 基本GL库，提供OpenGL的基本函数，函数名都以gl开头。   
2. GLUT库(the GL Utility Toolkit, GL实用工具包),用来打开窗口、开发和管理菜单、管理事件等。
3. GLU库（the GL Utility Library，GL实用库），提供一些较高级别的例程，如绘制二次曲面等  
4. GLUI库（the User Interface Library，用户接口库），是GLUT的基础

与glutMouseFunc想类似的函数还有：  glutDisplayFunc(myDisplay)  
<i>当系统决定重画一个屏幕窗口的时候，myDisplay被调用。</i>
glutReshapeFunc(myReshape)
<i>当窗口形状被改变时（即拉伸窗口的角时），myReshape