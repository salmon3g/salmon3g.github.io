---
title: "Google Analytics 代码部署"
categories: ["analytics"]
tags: []
draft: false
slug: "GA-js"
date: "2011-03-01 07:59:00"
---

Google Analytics 早在 2009 年就推出异步加载的方式了，不但保证了网页能更快的加载跟踪代码，对网站打开速度也不会产生影响了，下面是常见的部署 GATC（Google Analytics 监测代码）方式，可根据实际情况进行部署。

## 方式一：

将 GATC 放到网站所有要监测的网页的 </head> 标签前。

    <script type="text/javascript">
    
      var _gaq = _gaq || [];
      _gaq.push(['_setAccount', 'UA-XXXXX-X']);
      _gaq.push(['_trackPageview']);
    
      (function() {
        var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
        ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
        var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
      })();
    
    </script>

## 方式二：

将 ga.js 放到底部。

    <html>
    <head>
      <script type="text/javascript">
        var _gaq = _gaq || [];
        _gaq.push(['_setAccount', 'UA-XXXXX-X']);
        _gaq.push(['_trackPageview']);
      </script>
    </head>
    
    <body>
      <p>Page Content</p>
      <p>……</p>
    
      <script type="text/javascript">  (function() {
        var ga = document.createElement('script');     ga.type = 'text/javascript'; ga.async = true;
        ga.src = ('https:'   == document.location.protocol ? 'https://ssl'   : 'http://www') + '.google-analytics.com/ga.js';
        var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
        })();
       </script>
    </body>
    </html>

## 方式三：

将 GATC 放到单独的 js 文件中，如下。

      var _gaq = _gaq || [];
      _gaq.push(['_setAccount', 'UA-XXXXX-X']);
      _gaq.push(['_trackPageview']);
    
      (function() {
        var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
        ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
        var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
      })();

然后再在 </head> 前引用 ga_code.js。

    <script type="text/javascript" src="http://webname.com/js/ga_code.js"></script>

Tips：如果网站所有 URL 均使用的是 http 协议，可以简化 ga.js 的地址判断将

    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';

改为：

    ga.src = 'http://www.google-analytics.com/ga.js';

参考资料：https://developers.google.com/analytics/devguides/collection/gajs/
