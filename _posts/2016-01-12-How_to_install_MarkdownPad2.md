---
layout: post
title:  "MarkdownPad 2 安装及设置"
date:   2016-01-12 14:42
categories: 技术文档
tags: MarkdownPad2 
---

# 1. 激活
这里通过输入注册码来激活，注册码来源于 [MarkdownPad2.5 注册码](http://www.jianshu.com/p/9e5cd946696d)。
如果无效，请寻找其他激活方式。
点击`Help` -> `MarkdownPad Pro`，输入邮箱及授权密钥。
## 1.1 邮箱：
```
Soar360@live.com
```
## 1.2 授权秘钥：
（这一行只是为了网页排版，请忽略。）
（这一行也是为了网页排版，请忽略。）
（这一行也是为了网页排版，请忽略。）
（这一行也是为了网页排版，请忽略。）
（这一行也是为了网页排版，请忽略。）
（这一行也是为了网页排版，请忽略。）
（这一行也是为了网页排版，请忽略。）
```
GBPduHjWfJU1mZqcPM3BikjYKF6xKhlKIys3i1MU2eJHqWGImDHzWdD6xhMNLGVpbP2M5SN6bnxn2kSE8qHqNY5QaaRxmO3YSMHxlv2EYpjdwLcPwfeTG7kUdnhKE0vVy4RidP6Y2wZ0q74f47fzsZo45JE2hfQBFi2O9Jldjp1mW8HUpTtLA2a5/sQytXJUQl/QKO0jUQY4pa5CCx20sV1ClOTZtAGngSOJtIOFXK599sBr5aIEFyH0K7H4BoNMiiDMnxt1rD8Vb/ikJdhGMMQr0R4B+L3nWU97eaVPTRKfWGDE8/eAgKzpGwrQQoDh+nzX1xoVQ8NAuH+s4UcSeQ==
```

# 2. 设置
## 2.1 代码换行
设置通过回车键实现代码换行，点击`Tools` -> `Options` -> `Markdown`，在`Markdown Processor`下选择`GitHub Flavored Markdown (Offline)`即可。

## 2.2 Mathjax 配置

实现在MarkdownPad中支持数学公式。

点击`Tools` -> `Options` -> `Advanced` -> `HTML Head Editor`，这个是自定义头文件。添加下列内容：
```javascript:n
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
```
按 F6 键即可在网页中预览结果。

***
[MarkDownPad2 实现数学公式的 live preview 的精彩瞬间](http://blog.csdn.net/stereohomology/article/details/46398249)
[使用 Markdown + MathJax 在博客里插入数学公式](http://blog.kamidox.com/write-math-formula-with-mathjax.html)
[Mathjax and $\rm\LaTeX$ math formula](http://www.zyymat.com/mathjax-and-latex-math-formula.html)