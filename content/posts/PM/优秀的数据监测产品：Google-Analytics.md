---
title: "优秀的数据监测产品：Google Analytics"
categories: [PM]
tags: []
draft: false
slug: "GA-1"
date: "2015-05-09 12:10:00"
---

数据监测产品有很多，我使用过的，就有十几款，价格也是从免费到十几万人民币，到大几十万人民币，以及百万人民币不等。作为「介绍数据监测产品系列」第一篇，就一定要介绍一款优秀的产品 —— Google Analytics.

Google Analytics 是一款网站数据监测系统(产品)，也就是我们常说的 Google Analytics. Google Analytics 前身是 Urchin，于 2005 年 3 月时被 Google 收购；同年 11 月，Google 在 Urchin 基础上开发了 Google Analytics.

![请输入图片描述][1]
（图：Urchin 产品界面）

> 题外话：Google Analytics 的渠道追踪参数 UTM 便是从 Urchin 继承过来，是 Urchin Traffic
> Monitor 的缩写。国内有些数据分析产品的渠道追踪参数也使用了 UTM，原因猜测有二：
> 
> 1、用 Google Analytics 的网站太多了，便于替换；
> 2、直接 Copy, 并不知道 UTM 是什么的意思 :)

2011 年 3 月 Google Analytics 升级为 v5 版，2012 年 10 月 Google Analytics 最后一个版本被命名为 Universal Analytics。与 Google Analytics 最大的不同是 Universal Analytics 推出了 UserID，通过 UserID 进行跨终端追踪，和自定义维度和指标。Google 官方已经宣布不继续对旧版 Google Analytics 升级和维护，绝大多数使用 Google Analytics 的网站也已经升级为了 Universal Analytics, 所以下文提到的 Google Analytics 均为 Universal Analytics 版本。

Google Analytics 有两个版本：免费版和付费版(Premium)。付费版 15w 美元/年，除了数据不抽样外，付费版可以使用 BigQuery、DoubleClick Campaign Manager 和 DoubleClick Bid Manager。BigQuery 是 Google 云端的数据仓库，直接写 SQL 即可快速查询数据。据说，查询几十 G 的数据仅需几秒钟。目前国内使用 Google Analytics 的企业有很多，大型网站如：京东、豆瓣、知乎、蘑菇街、丁香园，小型网站更是不计其数。

绝大多数朋友在谈论 Google Analytics 时都是谈论的免费版本，比如「Google Analytics 和百度统计哪个好？」、「Google Analytics 如何设置跨域监测？」等，所以以下内容侧重免费版 Google Analytics(付费版包括免费版全部优点).

## Google Analytics 有哪些优点

对于免费的网站数据监测产品，Google Analytics 绝对是最优秀的。如果使用得当，Google Analytics 的价值远超国内几十万的付费产品。

1.几乎适合所有人使用
不论你是刚接触网站数据分析的新人，还是经验师经验丰富的数据分析专家，均可用来做数据分析。如果你是负责公司营销推广的运营人员，你可用来监测各个推广渠道的推广效果，优化推广策略。如果你是产品经理或者负责 UED，你可用来做用户行为监测，A/B Testing, 不断优化产品用户体验。如果你是 CEO, 你可选择你最关心的数据指标及自定义报表，定期为你发送定制的邮件。

2.灵活、功能齐全
Google Analytics 的操作非常灵活，功能也非常全面，国内很多数据监测产品的功能设计均有参考 Google Analytics. 我们最常用的如：随处可进行的高级细分、用户行为路径分析、归因模型、转化漏斗分析、实时数据、自定义指标和维度、自定义事件、自定义报告、自定义 Dashboard、账户分配与权限控制、报告共享、A/B Testing、跨屏监测、数据发送与下载、智能提醒、数据注释…

![请输入图片描述][2]
(图：高级细分使用案例)

3.支持全平台
Google Analytics 除了支持监测 Web 和 Wap 外，还支持监测 App.

4.技术一流
Google 的技术无需多说，Google Analytics 中数据计算及响应速度更是可以碾压国内绝大多数同类产品(用过的朋友定有感触)。

![请输入图片描述][3]
(图：配置高级细分过程中，数据实时呈现)
5.数据安全
Google 号称「不作恶」，也不用担心数据会被泄露。

6.资料丰富
Google Analytics 的帮助文档非常详细(绝对是业界良心)，有数据计算逻辑说明，有图文详解，也有视频教学；如果还有问题，Google 一下，几乎都能解决。

7.优秀的用户体验
轻松实现跨域追踪、随意细分数据仍能快速呈现、不同指标快速对比、维度可切换和下钻、多种图表类型随意选择、为不同人配置不同的 Dashboard、根据需要可配合过滤器建立多张数据视图…

8.API
Google Analytics 为用户提供了三种 API：Collection API、Management API、Data Export API，可以根据自己的需要结合 Excel、Tableau 等工具进行数据导出。

## Google Analytics 有哪些缺点
没有完美的产品，Google Analytics 也一样。在讨论 Google Analytics 缺点时，常被提及的又如下几点：

1.数据抽样
为了提高报告处理速度，超过一定限制，免费版 Google Analytics 将会采用数据抽样。例如：每月页面浏览量 1000 万次、多渠道路径报告以 100 万次等情况，数据报表将会抽样。

作者注：抽样被广泛用于统计分析中，抽样后的数据并不影响数据体现趋势，与完整数据集结果类似。Google Analytics 更加强调数据趋势，而不是像企业内部 BI 系统要求精确到个体。

2.Google Analytics 不能访问
由于特殊原因，在大陆访问 Google Analytics 查看数据需要「翻墙」。

作者注：「翻墙」其实很简单，而且也是互联网从业者应该具备的「技能」:) 。

3.Google Analytics 丢失数据
这个锅 Google Analytics 不应该背。国内有些企业为了宣传自己的产品，因为 Google Analytics 不能直接访问，就故意说 Google Analytics 丢数。

作者注：Google Analytics 收集数据和查看数据的服务器并不是同一台，查看数据的服务器大陆确实不能直接访问，需要「翻墙」，但是收集数据服务器并没有被「墙」。

总结
作为一款免费的数据监测产品，Google Analytics 非常真诚。如果业务不是非常复杂，或者对数据没有特殊要求，完全可以使用 Google Analytics，把节省下来的钱用来找优秀的数据分析师，不是更好吗？


  [1]: https://pic3.zhimg.com/80/4aafb484659745af84473bcd4c9ffd1e_720w.png
  [2]: https://pic3.zhimg.com/80/bf9ad5daee21a1032928ef06339112fa_720w.png
  [3]: https://pic3.zhimg.com/80/49863186fefe84d8e1f54d8f05ec8cfa_720w.png
