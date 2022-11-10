---
title: "GA电子商务追踪设置"
categories: ["analytics"]
tags: []
draft: false
slug: "tracking-ecommerce"
date: "2012-07-07 10:10:00"
---

一、启用电子商务追踪

在 Google Analytics 配置文件中启用电子商务追踪功能。

二、定制电子商务追踪代码

将下面电子商务追踪代码添加到订单成功页面。

    <script type=”text/javascript”>
    var _gaq = _gaq || [];
      _gaq.push(['_setAccount', 'UA-XXXXX-X']); 
      _gaq.push(['_setDomainName', 'wangdongxing.com']);
      _gaq.push(['_setAllowLinker', true]);
      _gaq.push(['_trackPageview']);
      _gaq.push(['_addTrans',
         '1234',           // transaction ID - required
         'Womens Apparel', // affiliation or store name
         '28.28',          // total - required
         '1.29',           // tax
         '15.00',          // shipping
         'San Jose',       // city
         'California',     // state or province
         'USA'             // country
      ]);
      _gaq.push(['_addItem',
         '1234',           // transaction ID - necessary to associate item with transaction
         'DD44',           // SKU/code - required
         'T-Shirt',        // product name
         'Olive Medium',   // category or variation
         '11.99',          // unit price - required
         '1'               // quantity - required
      ]);
      _gaq.push(['_trackTrans']);
    
      (function() {
        var ga = document.createElement(‘script’); ga.type = ‘text/javascript’; ga.async = true;
        ga.src = (‘https:’ == document.location.protocol ? ‘https://ssl’ : ‘http://www’) + ‘.google-analytics.com/ga.js’;
        var s = document.getElementsByTagName(‘script’)[0]; s.parentNode.insertBefore(ga, s);
      })();
    </script>

Google Analytics 主要靠 _addTrans()、_addItem() 和_trackTrans() 三个主力方法来完成对电子商务的追踪，其中 _addTrans() 通过 8 个参数（两个必填加五个选填）从交易级别统计数据，包括订单ID，总金额，运费和城市等信息。_addItem() 通过 6 个参数（四个必填加两个选填）从产品级别统计数据，包括产品ID，产品单价和产品数量等信息。_addTrans() 和_addItem() 像是数据库中的两张表，通过订单ID（orderID），将交易和产品关联起来。_trackTrans() 将交易和产品的所有数据，提交给 Google Analytics 服务器。

三、注意事项：

1. 将电子商务追踪代码加到订单完成页面。
2. _addTrans()和_addItem()中的订单ID(orderID)要保证相同。
3. 交易涉及到跨域（比如支付跳转到第三方支付平台）要根据 Google Analytics 跨域进行设置，确保 cookie 能正确记录来源。
