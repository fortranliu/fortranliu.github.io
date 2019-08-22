---
layout: post
title:  "Pointwise-extrude-smooth_factors"
date:   2018-11-16 10:22
categories: 学习
tags: Pointwise
---

#Pointwise-extrude-smooth_factors

##Explicit
range: 0~10
prevent crossing of grid lines.

##Implicit
range: 0~\infty, but double the value of explicit.

##Kinsey Barth
prevent crossing of the grid lines in the marching direction.

range: 3~\infty when the front includes severe concavities, default value is 0(OFF).

##Volume
range:0~1
determine how rapidly the grid clustering on the front relaxes as the extrusion steps forward.