---
title: "第一方cookie和第三方cookie"
categories: ["analytics"]
tags: []
draft: false
slug: "cookie"
date: "2011-11-25 10:59:00"
---

第一方cookie和第三方cookie都是相对当前访问的网站来说的，比如我访问了wangdongxing.com我的博客，而新浪（sina.com.cn）在我的博客中投放了一个广告（尽管不可能），并加入了它的数据监测代码，那么在我的电脑本地通常会产生两个cookie，cookie中记录如果是wangdongxing.com，那么这个cookie就是第一方cookie，如果记录的是sina.com.cn，那么这个cookie就是第三方cookie。

相反，如果我的博客（wangdongxing.com）在新浪上投放了一个广告（也有点不可能:P），并加入了数据监测代码，那么你在浏览新浪（sina.com.cn）的时候，在你的电脑本地生成两个cookie，如果cookie中记录的域名是sina.com.cn，那么这个cookie就是第一方cookie，如果是wangdongxing.com那么这个cookie就是第三方cookie。

第一方cookie和第三方cookie的最大区别就是针对不同人群有不同喜好，对应从事网站分析以及互联网监测者来说，是倾向第三方cookie，因为可以用它监测跨网站的访问行为；但是对于网站访问者了来说是不喜欢自己的浏览行为被其它网站监测，会考虑自己隐私是否被泄漏等。

通常我们接触的网站分析工具，比如Google Analytics、WebTrends也都是第一方cookie，而一些监测网络广告的会使用第三方cookie，不过默认情况下第三方cookie是被禁用的，如果想开启需要单独设置。
