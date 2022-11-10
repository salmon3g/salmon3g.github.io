---
title: "GA跨域追踪"
categories: ["analytics"]
tags: []
draft: false
slug: "cross-domain-tracking"
date: "2012-03-03 08:23:00"
---

Google Analytics 跨域追踪设置用到四个方法有：_setDomainName()、_setAllowLinker()、_link()和 _linkByPost()。_setDomainName() 用来设置 GATC cookies 的域名名字，下面是允许跨域追踪的设置，如果不允许跨域可设置为_gaq.push(['_setDomainName', 'none']); 。_setAllowLinker() 是启用跨域追踪的链接功能标志的一部分，默认设置为 false 链接是被禁用的，_link(), _linkByPost() 配合_setAllowLinker()使用。详细设置如下：

跨域追踪主域名及其子域名

在 _gaq.push(['_trackPageview']); 前加 _gaq.push(['_setDomainName', 'example.com']);即可，如下：

    <script>
    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-12345-1']);
    _gaq.push(['_setDomainName', 'example.com']);
    _gaq.push(['_trackPageview']);
    </script>

注：_setAllowHash 在最新 Google Anlaytics 中已经弃用，所以旧版帮助中心中 _gaq.push(['_setAllowHash', false]) 可以删掉了。

跨域追踪两个主域名

A：www.A.com
B：www.B.com
A 中设置追踪代码

    <script>
    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-12345-1']);
    _gaq.push(['_setDomainName', 'a.com']);
    _gaq.push(['_setAllowLinker', true]);
    _gaq.push(['_trackPageview']);
    </script>
    
    <a href="www.B.com"
       onclick="_gaq.push(['_link', 'www.B.com']); return false;">To B</a>
    
    <form name="f" method="post" onsubmit="_gaq.push(['_linkByPost', this]);">

注：_setAllowLinker，true 启用跨域追踪，并允许通过链接、表单在地址参数中传输 Cookie 数据；_link()、_linkByPost() 分别用于跨域追踪中链接、表单的 Cookie 数据传输。

B 中设置追踪代码：

    <script>
    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-12345-1']);
    _gaq.push(['_setDomainName', 'B.com']);
    _gaq.push(['_setAllowLinker', true]);
    _gaq.push(['_trackPageview']);
    </script>

    <a href="www.A.com"
       onclick="_gaq.push(['_link', 'www.A.com']); return false;">
       See my pet store</a>

    <form name="f" method="post" onsubmit="_gaq.push(['_linkByPost', this]);">

注：_setAllowLinker 为 true 时，启用跨域追踪，并允许通过链接、表单在地址参数中传输 Cookie 数据；_link()、_linkByPost() 分别用于跨域追踪中链接、表单的 Cookie 数据传输。

跨域追踪主域名与另一主域名的子目录

A:www.A.com
B:www.b.com/blog
A中设置追踪代码

    <script>
    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-12345-1']);
    _gaq.push(['_setAllowLinker', true]);
    _gaq.push(['_setDomainName', 'A.com']);
    _gaq.push(['_trackPageview']);
    </script>
    ...
    <a href="www.B.com/blog"
       onclick="_gaq.push(['_link', 'www.B.com/blog']); return false;">
       View My Blog</a>
    ...
    <form name="f" method="post" onsubmit="_gaq.push(['_linkByPost', this]);">

注：_setDomainName()、_setAllowLinker()、_link()和_linkByPost() 同上。

B 子目录追踪代码

    <script>
    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-12345-1']);
    _gaq.push(['_setDomainName', 'B.com']);
    _gaq.push(['_setAllowLinker', true]);
    _gaq.push(['_trackPageview']);
    </script>
    ...
    <a href="www.A.com"
       onclick="_gaq.push(['_link', 'www.A.com']); return false;">
       View My Site</a>
    ...
    <form name="f" method="post" onsubmit="_gaq.push(['_linkByPost', this]);">

注：_setDomainName()、_setAllowLinker()、_link()和_linkByPost() 同上

追踪单个子目录

    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-12345-1']);
    _gaq.push(['_setCookiePath', '/myBlog']);
    _gaq.push(['_trackPageview']); 

追踪相同域名下不同的两个子目录

    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-12345-1']);
    _gaq.push(['_setCookiePath', '/myStore/']);
    _gaq.push(['_trackPageview']);
    _gaq.push(['_cookiePathCopy', '/myCart/']);

_cookiePathCopy 的作用复制 cookie 信息到另外一个相同域名下的目录

跨 iframes 追踪

跨 iframes 追踪参照“跨域追踪主域名及其子域名”的同时加上如下代码。

    _gaq.push(function() {
      var pageTracker = _gat._getTrackerByName();
      var iframe = document.getElementById('myIFrame');
      iframe.src = pageTracker._getLinkerUrl('http://www.my-example-iframecontent.com/');
    });

最后更新于：2013.11.16
