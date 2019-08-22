---
layout: post
title:  "Ubuntu 下 Ansys 13.0 的安装过程"
date:   2016-01-11 20:12
categories: 技术文档
tags: Ansys Ubuntu
---

# Step 1
```shell
sudo apt-get install csh gfortran g++ lsb
sudo apt-get install xterm libstdc++6-4.4 libmotif libxtst libxt-dev libzip libxmu tcl8.5 tk8.5 
```

# Step 2
[参考链接](http://www.mobibrw.com/?p=639)
Ubuntu 13.10 的后续版本废弃了 ia32-libs。
解决方法：
```shell
sudo apt-get install lib32stdc++6
sudo apt-get install lib32z1
```

[参考链接](http://iwantyoutoloveme26.blog.163.com/blog/static/1976854520122209725109)
[参考链接](http://blog.csdn.net/maojun1986/article/details/38670047)

## 安装ia32-libs
进入apt源列表：
```
cd /etc/apt/sources.list.d
```
添加 Ubuntu 13.04 的源，因为 13.10 的后续版本废弃了 ia32-libs
新建文件 ia32-libs-raring.list：
```
sudo touch ia32-libs-raring.list
```
在文件中添加：
```
deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse
```
更新源并安装 ia32-libs：
```shell
sudo apt-get update
sudo apt-get install ia32-libs
```
恢复源：
```shell
sudo rm ia32-libs-raring.list
sudo apt-get update
```

# Step 3
- Login root.
- 安装 Ansys 16.0 到 `/usr/ansys_inc/`. **不要安装 ANSYS License Manager!**

# Step 4
- 解压 `_SolidSQUAD_/ansys16-SSQ.tar.gz`
- 复制 `ansysli_client` 到 `/usr/ansys_inc/shared_files/licensing/linx64/` 并覆盖原文件
- 复制 `ansyslmd.ini` 到 `/usr/ansys_inc/shared_files/licensing/`
- 复制 `license.dat` 到 `/usr/ansys_inc/shared_files/licensing/`
- Exit root

# Step 5
安装完成，启动 AnsysWB: `/usr/ansys_inc/v160/Framework/bin/Linux64/runwb2`

# Step 6
[参考链接](http://www.cfd-online.com/Forums/ansys-meshing/89147-error-when-starting-icem-cfd-ubuntu.html)

## 解决icem相关问题：
```shell
sudo apt-get install libmotif3 libmotif4
sudo apt-get install xfs xfstt
sudo apt-get install t1-xfree86-nonfree ttf-xfree86-nonfree ttf-xfree86-nonfree-syriac xfonts-75dpi xfonts-100dpi
xset +fp /usr/share/fonts/X11/75dpi/
xset +fp /usr/share/fonts/X11/100dpi/
```
将下面一行加入到 `/etc/bash.bashrc`
```
export LANG=en_US.UTF-8 XMODIFIERS=""
```

## 添加环境变量，以便实现命令行快速启动
打开配置文件：`sudo gedit ~/.bashrc`

添加如下内容到配置文件文末：
```shell
export PATH=/opt/ansys_inc/v121/ansys/bin:$PATH
export PATH=/opt/ansys_inc/v121/CFX/bin:$PATH
export PATH=/opt/ansys_inc/v121/fluent/bin:$PATH
export PATH=/opt/ansys_inc/v121/icemcfd/linux64_amd/bin:$PATH
export PATH=/opt/ansys_inc/v121/polyflow/bin:$PATH
export PATH=/opt/ansys_inc/v121/Framework/bin/Linux64:$PATH
export PATH=/opt/ansys_inc/v121/TurboGrid/bin:$PATH
export PATH=/opt/ansys_inc/shared_files/licensing/lic_admin:$PATH
```
依次为：ANSYS, CFX, FLUENT, ICEM, POLYFLOW, WORKBENCH, TurboGrid, ANSYS Sevice Manager.
执行代码: `sudo source .bashrc` 使 `.bashrc`文件生效
***
Cracked by Team-SolidSQUAD (SSQ)
