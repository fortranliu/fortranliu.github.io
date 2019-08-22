---
layout: post
title:  "在 Ubuntu 下安装 Dropbox（墙内）"
date:   2016-01-11 20:22
categories: 技术文档
tags: 技术 Dropbox Ubuntu
---

# 下载 Dropbox
如果您想在 Ubuntu 桌面上使用 Dropbox，请安装程序包 (.deb)：[64-bit（墙内）](http://pan.baidu.com/s/1bottMBd)。

**注意**：这些程序包安装了一个开放源码的帮助应用。此应用的版本不像 Dropbox 主应用一样频繁地更改。这些程序包总会安装 Dropbox Linux 版的最新版本。

[查看版本说明（墙外）](https://www.dropbox.com/release_notes)

## 通过命令行安装无外设模式的 Dropbox
Dropbox 守护程序可在所有 32 位与 64 位 Linux 服务器上正常运行。若要安装，请在 Linux 终端运行下列命令。

32-bit:
```
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -
```
64-bit:
```
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
```
接着，从新建的 .dropbox-dist 文件夹运行 Dropbox 守护程序。
```
~/.dropbox-dist/dropboxd
```

如果是首次在服务器上运行 Dropbox，系统会要求您将链接复制并粘贴到运行的浏览器中，以便创建一个新的帐户或将服务器附加到现有帐户上。操作完成后，系统会在您的主目录中创建 Dropbox 文件夹。下载这个 [Python（墙内）](http://pan.baidu.com/s/1jGPtuXw) 脚本，通过命令行控制 Dropbox。为了方便访问，请在 PATH 中的任何地方放入此脚本的符号链接。
***
内容来源：[Dropbox帮助（墙外）](https://www.dropbox.com/install?os=lnx)
打包下载：[Dropbox.rar（墙内）](http://pan.baidu.com/s/1dEaYN3V)