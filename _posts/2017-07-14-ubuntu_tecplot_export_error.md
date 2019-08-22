---
layout: post
title:  "Ubuntu 14.04下报错"
date:   2017-07-14 10:22
categories: 技术文档
tags: Ubuntu
---

#Ubuntu 14.04下报错

export选择PNG,JPEG等，导出时显示`Unable to render offscreen image`，提示无法渲染图片，可能是显卡驱动的问题。导出为wmf格式没有问题，但在windows下查看wmf是黑白的。

不完全解决方法：启动tecplot时用`tec360 -mesa`，可关掉硬件加速，然后即可导出PNG，JPEG等格式。但是导入layout后实时显示的图像质量有所下降。