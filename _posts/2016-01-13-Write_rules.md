---
layout: post
title:  "Farbox 写作规范"
date:   2016-01-13 15:42
categories: 技术文档
tags: Farbox
---

# Farbox

文件开头可用如下格式：
```
Date: 2016-01-01 11:11
Title: 我是文章的标题
Tags: 标签1, 标签2
Status: draft
URL： this-is-my-first-post
```

- **Date** 可以设置文章发表时间
- **Title** 可以设置文章的标题（如果不想用文件名做标题）
- **Tags** 可以设置文章的标签。如果标签中没有连词的，直接使用空格；如果有连词的话，使用英文状态下的,进行分割即可
- **Status** 表示文章的状态，默认的是public。日志列表内输出的一般都是public 属性的文章，像上面示例中draft则表示不在网站里出现。
- **URL** 用来自定义文章的地址，如无必要，请不要定制。

然后开始用 Markdown 格式写正文。

# Mathjax

## 行内公式

行内公式由两端的 $ 包括在其中，如：
> `...根据 $\alpha+\beta=\gamma$ 可得...`
> ... 根据 $\alpha+\beta=\gamma$ 可得...

## 行间公式

行内公式由两端的 $$ 包括在其中，如：
> `...根据 $$\alpha+\beta=\gamma$$ 可得...`
> 或者
> `...根据`
> `$$\alpha+\beta=\gamma$$`
> `可得...`
> 或者
> `...根据`
> ````mathjax`
> `\alpha+\beta=\gamma`
> `````
> `可得...`
> ... 根据 $$\alpha+\beta=\gamma$$ 可得...
> `````

>  ...根据
> ```mathjax
> \alpha+\beta=\gamma
> ```
> 可得...

***
参考链接：
[Farbox 写作规则](http://help.farbox.com/read/basic-writting)
[Farbox 模板规则文档](http://doc.farbox.com/read/get-data#)