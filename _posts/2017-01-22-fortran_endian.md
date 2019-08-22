---
layout: post
title:  "Fortran相关问题"
date:   2017-01-22 13:18
categories: 随笔
tags: Fortran
---

#little_endian和big_endian的区别以及fortran runtime error 

##Big and Little Endian

##Fortran Runtime Error
编译时出现`In call to SUB, an array temporary was created for argument #1`，是因为传递的数组里面的值得地址是不连续的。

***
参考链接：
[Big and Little Endian](https://www.cs.umd.edu/class/sum2003/cmsc311/Notes/Data/endian.html)
[Inter Developer Zone](https://software.intel.com/en-us/forums/intel-visual-fortran-compiler-for-windows/topic/273874)
[stackoverflow](http://stackoverflow.com/questions/28859524/fortran-runtime-warning-temporary-array)