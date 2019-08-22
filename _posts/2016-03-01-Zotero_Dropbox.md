---
layout: post
title:  "Zotero 设置和 Dropbox 同步 "
date:   2016-01-13 18:49
categories: 技术文档
tags: Zotero Dropbox
---

# 说明
举例来说，我的 Zoreto 安装在了 C 盘的 program file 中，数据文件存放在 
 `C:\Users\用户名\AppData\Roaming\Zotero\Zotero\Profiles\******.default\zotero\` 中，内含 `locate`、`storage` 、`styles` 、`tmp` 和 `translators` 这些文件夹及其他文件，其中 `storage` 是存放文献pdf的文件夹。

在我的 Dropbox 同步盘（ `E:\Dropbox` ）下新建一个叫做 `literature` 的文件夹用于存放 `storage` 中的内容，同时，该 `literature` 中的文件将被dropbox实时更新到云端。 

按照上述方法，需要将 C 盘下的 `storage` 变成类似快捷方式的链接，该链接指向 Dropbox 同步盘下的 `literature` 文件夹。 

# 做法
具体做法是（针对 Win7 系统，XP 系统的做法请参看后面附的参考链接）： 
1. 将 C 盘 `C:\Users\用户名\AppData\Roaming\Zotero\Zotero\Profiles\******.default\zotero\` 中的 `storage` 文件夹“剪切”（剪切前最好先备份 `storage` 文件夹）到 `E:\Dropbox\literature`中
2. 找到 `cmd.exe` 文件，右键“以管理员身份运行”，之后输入下述命令（中间均用空格分开）： 
```
Mklink /j C:\Users\Mec\AppData\Roaming\Zotero\Zotero\Profiles\ejs4k27r.default\zotero\storage E:\Dropbox\literature\storage
```

# 注
## `mklink`命令，参数 `/d` 和参数 `/j` 的区别
目录符号链接 `/d` 和软链接 `/j` 的区别在于：软链接在创建时会自动引用目标目录的绝对路径，而符号链接允许相对路径的引用，如分别用 `mklink /d dira tdir` 和 `mklink /j dirb tdir` 创建 `dira`、`dirb` 对 `tdir` 的符号链接和软链接，之后将 `dira`、`dirb` 移动到其它目录下，则访问 `dira` 时会提示“位置不可用”，访问 `dirb` 时仍然正常指向 `tdir`；而分别用 `mklink /d dira c:\demo\tdir` 和 `mklink /j dirb c:\demo\tdir` 创建 `c:\demo\tdir` 的符号链接和软链接，再将这两个目录链接移动到其它目录下，则 `dira` 和 `dirb` 均可正常指向 `c:\demo\tdir`；由此可见当创建目录链接时对目标目录使用绝对路径，/d 和 /j 两个参数实现的目录链接效果是一样的。

***
参考链接：
[Zotero同步不足的解决方案](http://www.douban.com/group/topic/48495741/)
[科研文献资料的高效管理](http://blog.sina.com.cn/s/blog_6daf1c5b0100z8nn.html)
[Zotero文献管理、科研笔记不完全教程](http://blog.sina.com.cn/s/blog_565e747c01014toj.html)
[Syncing Zotero with Dropbox and Between Several Computers](http://remembereverything.org/syncing-zotero-with-dropbox-and-several-computers/)