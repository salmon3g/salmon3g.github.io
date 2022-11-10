---
title: "GA流量来源分类及覆盖规则"
categories: ["analytics"]
tags: []
draft: false
slug: "source-overwrite"
date: "2012-01-19 11:31:00"
---

Google Analytics 中对流量来源各渠道进行了分类，同时各类流量来源优先级也不相同，也就存在各流量来源渠道的覆盖规则。Google Analytics 流量来源渠道分类如下：

一、市场投放（Campaigns）

多指广告活动流量，最常见的是 PPC 广告，Google 的 Adwords（无需单独标记），百度的关键词推广，还可以对其他广告进行标记（标记工具：URL Builder）。

注意：Google Analytics 主要靠媒介信息（Campaign Medium）对流量进行分类。None 是直接流量，referral 是推介流量，organic 是自然流量（SEO），cpc,cpm,cpa,cpp,ppc 等是付费搜索（SEM）流量，其余的是 campain 流量。特别说明：cpc 是 Google Adwords 特有标记，其他搜索引擎可以使用 ppc 标记。

二、自然搜索（Organic）

通过搜索引擎检索关键词，点击自然排名带来的流量（SEO流量），国内大部分搜索引擎需要单独添加识别搜索引擎的代码（参考：Google Analytics 识别国内搜索引擎），否则会将这部分流量划分到推介网站（Referral）中去。

三、推介网站（Referral）

指来自其他网站中的链接到达自己网站的流量，比如友情链接、其他网站内容中的链向自己网站的超链接等。

四、直接流量（Direct）

直接流量指没有推荐来源的流量，通常包括直接在浏览器地址栏输入网址、点击收藏夹、客户端软件（如MSN、QQ、旺旺等）和标记丢失无法判断的流量。

## Google Analytics 流量覆盖规则

Google Analytics 不同渠道的优先级不同，优先级高的渠道会覆盖掉优先级低的渠道，规则如下图：

![][1]


  [1]: https://ww4.sinaimg.cn/large/86a751acjw1eb59ttgxctj20jz0b7gmu.jpg
