---
title: "4行Python下载经济学人图表"
categories: ["analytics"]
tags: []
draft: false
slug: "download"
date: "2013-10-14 10:59:00"
---

经常做图表的同学应该知道经济学人，经济学人的图表简洁、专业值得学习。经济学人的图表是每周一期，大概有五十多期，可以借助 Python 下载。

思路：

1. 以一期为基础，将其 URL 按照日期形式 +/-7 拉出所有的 URL 并保存到 txt 中
2. 用 Python 读取 txt 中的 URL 地址并下载

Python 代码如下：
```python
import urllib
with open('d://url.txt', 'r') as f:
  for i,url in enumerate(f.readlines()):
  urllib.urlretrieve(url,'d://pdf/%s.pdf'%i)
```