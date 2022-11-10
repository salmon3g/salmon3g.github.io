---
title: "商业智能和数据可视化领导者：Tableau"
categories: [PM]
tags: ["BI","数据可视化"]
draft: false
slug: "tableau"
date: "2018-12-17 08:33:00"
---

[Tableau][1] 成立于 2003 年，是斯坦福大学一个计算机科学项目的成果，该项目旨在改善分析流程并让人们能够通过可视化更轻松地使用数据。Tableau 连续 6 年在 Gartner 分析和商业智能魔力象限中被评为领导者，BI(商业智能)和可视化方面十分优秀。

<img src="https://tva1.sinaimg.cn/large/e6c9d24ely1h3hyz20o11j20u00u0abe.jpg" width="520px" />

下面是我在公司(滴滴)负责 Tableau 平台的一些信息：

- 产品：1人(我)，负责平台二次开发(权限系统打通、审批流程设计)，日常运营(问题答疑、权限管控、使用手册撰写、定期培训等)
- 开发：1-2人，负责定制开发，数仓维护、系统健康度管控
- 业务部门：整个滴滴公司10+业务部门使用
- 人数：日均用户数1800+
- 使用产品：Tableau Desktop + Tableau Server，永久授权版
- 费用：几百万/年

Tableau主要产品线

1. Tableau Desktop：本地计算机数据分析、数据探索、可视化神器，也可以将制作好的图表、看板发布到 Server 端，与别人共享。
2. Tableau Server：用于发布和管理Tableau Desktop制作的仪表盘，实现视图共享，需要把它部署到服务器上，展开协作并共享自己的仪表板中的结果。
3. Tableau Online：完全托管式云端解决方案。准备数据、制作、分析、协作、发布和共享，都可在 Tableau Online中一站完成。申请账号就能使用，不用自己部署server，适用于有协作需求，但不想部署server的场景。
4. Tableau Public：免费的服务产品，可把自己创建的视图发布到Public上，公开展示和分享数据。Tableau Public 有非常丰富的数据可视化库，可参考学习和找数据灵感。
5. Tableau Prep：可视化ETL神器，能更快地对数据进行合并、组织和清理等前期数据预处理工作。处理完的数据可直接导入Desktop，无缝衔接。

## 特点 & 优势

能长期稳坐BI领域领导者，Tableau有太多的优点，下面简单列举几个：

1、支持丰富的数据源。

市面上用的数据源，常用不常用的，Tableau基本都支持

![](https://tva1.sinaimg.cn/large/e6c9d24ely1h3i5zaepo9j20re0jmacn.jpg)

2、超强的数据可视化能力。

作为数据可视化起家的Tableau，你能想到的图表、看板样式，Tableau基本都能满足，如果不能满足说明你对Tableau的使用还不熟练。我当时参加一位台湾老师的初、中培训课程，看了他对Tableau的使用，惊为天人，当然，这样说明Tableau在数据可视化方面的能力。

想学习更多看板设计，可以在Public网站上找灵感，地址为：https://public.tableau.com/app/discover/viz-of-the-day

![](https://tva1.sinaimg.cn/large/e6c9d24ely1h3i6ac8n31j20gm0e9abd.jpg)

3、便捷的交互式可视化设计。

准备好数据源后，只需简单拖拉拽便可以立刻生成漂亮的图表，Tableau会根据你的选择的维度和指标，智能的帮你生成更便于分析的图表。带有条件选择的看板以及多表关联，也可以通过简单配置快速实现。

![](https://help.tableau.com/current/pro/desktop/zh-cn/Img/addfield7.gif)

4、强悍的数据处理能力。

一般计算机配置，用Excel基本很难打开百万行数据的文件，但是把数据导入Tableau，便可以轻松应对，甚至很流畅的进行数据分析探索。这可能和Tableau获得专利的基础技术 VizQL 有直接关系。

5、协作方便。

用户可以将自己创建好的看板发布到自己所在组织的空间里，同组织的同学便可以直接查看和使用。也可以将自己设计好的文件导出分享，别人可在此基础上继续使用和设计。

6、鼓励交互探索。

Tableau看板的设计理念除了让制作者交互分析外，更鼓励查看者通过交互进行探索，不论通过增加筛选项，还是多表联动，还是将看板制作成story，都能很好的实现。而非仅仅像查看图片一样，把它当做一份静止的数据看板。

常用的数据故事类型如时间序列、逐层下钻、横向对比等等。

![](https://help.tableau.com/current/pro/desktop/zh-cn/Img/animations.gif)

7、支持脚本语言。

为了避免性能问题并在Tableau中进行复杂的表计算, 用户可以包括Python或R。使用Python脚本, 可以通过对数据包执行数据清理任务来减轻软件的负担。

## 确定 & 不足

金无足赤，Tableau也有一些不足。例如

- 看板不能自适应屏幕。如果仪表板是在1920 X 1080的屏幕分辨率上创建的，在2560 X 1440上查看不会自动响应。
- 二次开发不够灵活。很多功能是黑盒，不过毕竟是商业产品而非开源产品，这个可以理解。
- 价格昂贵。租赁方式，Server是每个用户每年420美金，Desktop是每个用户每年840美金。滴滴的Desktop是买的永久的，每年续费维保400美金，Server买的是本地部署8core的(这种据说现在没有了)，加上每个Desktop的license，算下来一年几百万，确实贵

## 其他

平台架构 & 功能简介

![](https://tva1.sinaimg.cn/large/e6c9d24ely1h3hz973su7j21gy0u0gqh.jpg)

![](https://tva1.sinaimg.cn/large/e6c9d24ely1h3hzat1lcrj21h50u0juq.jpg)

除了滴滴外，国内还有很多中大型企业、互联网公司在使用Tableau，例如：银行、航空公司、头条、乐视、华为、首汽。对于数据驱动文化很强的企业来说，在没有足够的人力、时间来自己开发一套BI系统前，采购成熟的商业产品可能效率是最高的。如果Tableau超预算了，也可以考虑其他类似的产品。


  [1]: https://www.tableau.com/
