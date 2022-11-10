---
title: "Google Analytics cookie"
categories: ["analytics"]
tags: []
draft: false
slug: "ga-cookie"
date: "2012-01-02 09:21:00"
---

Google Analytics cookie 是访问添加过 Google Analytics 监测的网站时生成的， Google Analytics cookie 最为常见的有四个：__utma、__utmb、__utmc 和 __utmz。

__utma：默认有效期两年，用来识别访问者和访问次数。包含 6 个字段，从左到右分别代表域哈希值、访问者 ID（唯一）、首次访问时间、上次访问时间、本次访问开始时间和访问次数。

（注：访问时间数值为 Unix 系统时间，从1970年1月1日0点0分0秒开始计算）

__utmb：默认有效期 30 分钟，用来判断新的访问。包含 4 个字段，从左到右分别代表域哈希值、本次访问产生的页面浏览量、不详和本次访问开始时间。

__utmc：Google Analytics V5 版以后可忽略。

__utmz：默认有效期为 6 个月，用来储存流量来源信息。从左到右分别代表域哈希值、本次访问开始时间、访问次数、Campaign 次数和 Campaign 信息，Campaign 信息中包含以下参数：

    utmcsr = source
    utmcmd = medium
    utmccn = campaign name
    utmctr = campaign keyword
    utmcct = campaign content
    utmgclid = Adwords 跟踪识别ID


