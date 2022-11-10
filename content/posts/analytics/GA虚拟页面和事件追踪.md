---
title: "GA虚拟页面和事件追踪"
categories: ["analytics"]
tags: []
draft: false
slug: "virtual-page-event-track"
date: "2012-05-13 10:59:00"
---

有时，我们需要监测一些不能产生页面浏览的行为，比如点击友情链接跳转到其他网站、点击下载网站附件以及点击 Flash 等内容。Google Analytics 监测类似这些内容常用的统计方法是虚拟页面和事件追踪。

1、Google Analytics 虚拟页面

虚拟页面顾名思义就是制作一个并非真实的页面，就用到的 Google Analytics 的方法 _trackPageview()，_trackPageview() 方法会将点击数据发送到服务器，并在报告中展示。虚拟页面并非真是存在，所以在配置过程中要做好归类，便于识别。

如果对友情链接点击数据进行监测，可在每条链接上加如下代码：

    <a href="" onClick="_gaq.push(['_trackPageview','/virtual/links-xxx']);" >xxx</a>

注：由于虚拟页面产生的流量并非是网站本身的，所以比正常流量会多一些。

2、Google Analytics 事件追踪

由于虚拟页面会使网站流量虚高，所以建议使用 Google Analytics 的事件追踪。事件追踪用到了 Google Analytics 的_trackEvent() 方法，详细参数如下：

    _trackEvent(category, action, opt_label, opt_value, opt_noninteraction)

如果想对某条链接使用事件追踪，只需在链接中调用_trackEvent() 方法即可，代码如下：

    <a href="#" onClick="_gaq.push(['_trackEvent', 'category', 'action', 'label', 'value', 'true']);">link</a>

其中 category、action 是必须要填写的，category 是事件追踪的分类，action 是可根据实际需求来设置，以监测视频为例：

    _gaq.push(['_trackEvent', 'Videos', 'Play', 'Gone With the Wind']);
    _gaq.push(['_trackEvent', 'Videos', 'Pause', 'Gone With the Wind']);
    _gaq.push(['_trackEvent', 'Videos', 'Download', 'Gone With the Wind']);

对 Gone With the Wind 视频进行了事件追踪，将事件归类到 Videos，并对 Play、Pause、Download 三个动作进行了监测。需要注意的是 每个事件中的 action 相对 category 是独立的，也就是如果还有一个 Music 分类也使用了 Play 作为 action，那么 action 中 Play 的数据是两个分类的汇总。

另外，action 并非是只能用来监测“动作”，比如我们有一个分类是下载，那么 action 就可以是不同类型的文件（pdf/doc/xls…）。所以在实际使用中，要根据需求灵活应用。

opt_label、opt_value 和 opt_noninteraction 都是可选参数。opt_label 可以用来对监测内容命名，如视频名字。opt_value 与其他参数不同之处是它是一个整数型，可以用它来统计播放器加载时长，如下：

    _gaq.push(['_trackEvent', 'Videos', 'Video Load Time', 'Gone With the Wind', downloadTime]);

这样就可以监测 Gone With the Wind 加载的时长了，还可以算多次加载的平均时长。

opt_noninteration 参数是布尔类型（ture 或者是 false），这个参数可以定义包含事件追踪的页面的跳出率。缺省默认是 false，事件点击会作为一次“互动点击”，即不算跳出；如果是 true，事件点击将不会作为一次“互动点击”。

更多详细信息参见：developers.google.com

最后更新于：2016.12
