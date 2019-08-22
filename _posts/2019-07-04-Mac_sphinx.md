---
layout: post
title:  "Mac下安装sphinx注意事项"
date:   2019-07-04 10:22
categories: 技术文档
tags: Mac sphinx
---

#Mac下安装sphinx注意事项

使用`brew install sphinx`命令安装后任然提示找不到sphinx，重新用`sudo easy_install -U sphinx`命令安装后解决问题。



运行`make html`后提示`exception: No module named 'sphinx.ext.pngmath'`，因为sphinx 1.7之后弃用了pngmath而改用imgmath，故在`conf.py`文件中将`sphinx.ext.pngmath`改为`sphinx.ext.imgmath`即可解决问题。



运行`make html`后提示`exception: No module named 'numpydoc'`，运行`pip3 install numpydoc`安装numpydoc即可。