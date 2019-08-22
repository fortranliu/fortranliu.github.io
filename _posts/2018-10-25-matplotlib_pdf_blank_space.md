---
layout: post
title:  "matplotlib生成pdf有白边的解决办法"
date:   2018-10-25 10:22
categories: 技术文档
tags: matplotlib
---

#matplotlib生成pdf有白边的解决办法

##自动裁剪
matplotlib输出结果时有白边（blank space or margin），常用方法皆不好使。生成pdf后，通过一句Latex自带命令可以裁剪掉pdf周围的白边。

```
pdfcrop input.pdf output.pdf
```

该命令即可自动生成一个裁剪过的pdf文件。若不指定输出文件名，会自动生成一个带后缀的pdf文件，如`foo-crop.pdf`（原文件为`foo.pdf`）。

##进阶

###查询包围有效区域的boundingbox大小
通过`pdfcrop --verbose foo.pdf`命令可以得到pdf文件中白边boundingbox的范围

```
engchuhandeMacBook-Pro:eps fengchuhan$ pdfcrop --verbose foo_B.pdf
PDFCROP 1.38, 2012/11/02 - Copyright (c) 2002-2012 by Heiko Oberdiek.
* PDF header: %PDF-1.4
* Running ghostscript for BoundingBox calculation ...
GPL Ghostscript 9.23 (2018-03-21)
Copyright (C) 2018 Artifex Software, Inc.  All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.
Processing pages 1 through 1.
Page 1
%%BoundingBox: 7 7 432 268
* Page 1: 7 7 432 268
%%HiResBoundingBox: 7.164000 7.164000 431.971440 267.659992
* Running pdfTeX ...
This is pdfTeX, Version 3.14159265-2.6-1.40.19 (TeX Live 2018) (preloaded format=pdftex)
entering extended mode
(./tmp-pdfcrop-88489.tex [1 <./foo_B.pdf>] )
Output written on tmp-pdfcrop-88489.pdf (1 page, 102295 bytes).
Transcript written on tmp-pdfcrop-88489.log.
==> 1 page written on `foo_B-crop.pdf'.
```

其中，`7.164000 7.164000 431.971440 267.659992`即为boundingbox从左手开始顺时针方向各边的坐标，坐标原点位于左上角。

###精确裁剪
通过命令`pdfcrop --bbox '6.5 6.5 446 268' foo.pdf`即可精确裁剪空白区域的大小

```
engchuhandeMacBook-Pro:eps fengchuhan$ pdfcrop --bbox '6.5 6.5 446 268' foo_B.pdf
PDFCROP 1.38, 2012/11/02 - Copyright (c) 2002-2012 by Heiko Oberdiek.
==> 1 page written on `foo_B-crop.pdf'.
```
