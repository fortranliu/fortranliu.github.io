---
layout: post
title:  "Fortran编译包含ifdef时报错"
date:   2019-07-30 10:22
categories: 技术文档
tags: Fortran
---

编译fortran，含`#ifdef`时，报错，提示`bad # preprocessor line`。

原因：

The message

> warning #5117: Bad # preprocessor line

is potentially a little misleading. It suggests that the code has been passed through the preprocessor and it's the preprocessor that's unhappy. That isn't always the case: ifort also produces this warning message when preprocessor directives occur in the source file but the preprocessor isn't invoked.

To ensure that the preprocessor is run you have a couple of options:

- add the flag `-fpp` (or `-cpp`) to the compilation command;
- name the free-form source file with the suffix `.F90` (note the capital).