---
layout: default
title: 在Windows Server 2008上安装git服务器
---

# 在Windows Server 2008上安装git服务器
首先安装Cygwin，安装openssh, git, bash-completion以及bash-compelion-devel  
管理员权限运行bash，执行ssh-host-config  
1. *** Query: Should StrictModes be used? (yes/no)
 这里选择yes
2. *** Query: Should privilege separation be used? (yes/no)
 这里选择yes, Cygwin会为我们建立一个特殊的windows账户用来执行sshd服务.
3. *** Query: Do you want to install sshd as a service?
    *** Query: (Say "no" if it is already installed as a service) (yes/no)
 选择yes, 会注册一个sshd的服务, 以执行server.
4. *** Query: Enter the value of CYGWIN for the daemon: []
 这里写ntsec
5. *** Info: This script plans to use 'cyg_server'.
*** Info: 'cyg_server' will only be used by registered services.
*** Query: Do you want to use a different name? (yes/no)
 Cygwin要建立一个cyg_server账户以运行sshd服务, 这里可以选择为该账户另取名字或者使用default. 我们选择no.
6. *** Query: Create new privileged user account 'xxx\cyg_server' (Cygwin name: 'cyg_server')? (yes/no)
 yes, 确定建立账户. 之后输入密码, 完成config.  
 **注意Windows Server下的密码策略可能会要求包含大写、小写字母、数字,除非在组策略gpedit.msc，计算机配置->Windows设置->安全设置->账户策略->密码策略，禁用“密码必须符合复杂性要求”**

设定完毕后, 在/etc下面多出来一个sshd_config文件, 打开该文件, 将如下item的注释取消,
RSAAuthentication              yes
PubkeyAuthentication         yes

然后, 我们需要生成public和private key. 执行
ssh-keygen -t rsa
然后一路回车即可. 这时在我们的当前账户下就会多出来一个.ssh文件夹, 内部包含id_rsa和id_rsa.pub两个密钥文件.

cmd下net start sshd:
```bash
CYGWIN sshd 服务正在启动 .
CYGWIN sshd 服务已经启动成功。
```

建立一个专门的账号以登陆git服务器. 因此这里可以先建立一个windows下的账户, 例如名字就叫git, 密码为git
```bash
net user git git /add
命令成功完成。
```


将该git账户添加到管理员组当中.
```bash
net localgroup administrators git /add
命令成功完成。
```

ssh登录测试一下，注意开放防火墙的22端口

建立仓库:
```bash
git init --bare
```

切换到客户端git bash
```bash
ssh-keygen -t rsa
```
生成客户机器的public和private key, 之后我们需要将该机器的public key注册到服务器上, 以实现免密码登陆.

```bash
ssh-copy-id git@xxx.xxx.xxx.xxx
```

根据提示输入登陆密码, 就会将客户机的public key写入到服务器端git账户.ssh文件夹下的authorized_keys

```bash
git remote add origin git@webvr.chinacloudapp.cn: /cygdrive/d/xampp/htdocs/webvr.git
```
参考：[http://blog.csdn.net/vector03/article/details/53243436](http://blog.csdn.net/vector03/article/details/53243436)