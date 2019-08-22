---
layout: post
title:  "Tecplot中zonetype类型"
date:   2018-09-07 10:22
categories: 技术文档
tags: Tecplot
---

#Tecplot中zonetype类型

##ordered
按顺序存储

##finite element
先存储浮点类型的数据，再存储与该数据相关联的element编号

```
1.0 0.4 0.3
1.0 0.2 0.0
1 2
2 3
3 4
4 10
5 6
6 7
7 8
8 9

```
