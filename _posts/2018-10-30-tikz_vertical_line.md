---
layout: post
title:  "How to plot vertical line in flowchart by tikz"
date:   2018-10-30 10:22
categories: 技术文档
tags: tikz
---

#How to plot vertical line in flowchart by tikz

(a-|b)表示和a在同一水平线上且和b在同一竖直线上的坐标点，例如：


```
\draw (A.south) -- (A.south|-B.north);
```

---
[1](https://tex.stackexchange.com/questions/111365/tikzpicture-vertical-line-from-one-node-to-the-other?noredirect=1&lq=1)
[2](https://tex.stackexchange.com/questions/96550/drawing-a-vertical-line-between-two-nodes-in-tikz?noredirect=1&lq=1) 