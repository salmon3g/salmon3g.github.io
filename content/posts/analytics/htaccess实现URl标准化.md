---
title: "htaccess实现URl标准化"
categories: ["analytics"]
tags: []
draft: false
slug: "URL"
date: "2010-12-06 09:06:00"
---

URL标准化在SEO中是一个比较重要的环节，同时存在不同的网址版本，不但可能造成复制，还不能正确的集中权重。目前大多数网站，绑定域名都有带WWW和不带两个版本，甚至很多网站同时绑定多个域名。经过处理（跳转、CNAME……），对于访问者来说可能没有任何影响，看到的都是同样的内容；但对于搜索引擎，就无法确定哪一个网址是真正的主页。

可控因素，网站内容链接应该保持同一个版本，比如整站中，返回首页的地址为固定的一个版本。但还有一个不可控的因素，就是别人链到你的网站，所使用的网址。很多自发链接或交换链接时，别人可能会省略掉WWW，或采用绑定的另一域名。外界因素不可控，我们可以从网站内部来控制。利用 Apache 的 .htaccess，使用301重定向，规范网址。

新建一个空文件，文件名 .htaccess（如果网站根目录有就不用了），填入重定向规则后，上传到网站根目录。用301将不带 WWW 的域名重定向。

    rewriteEngine on
    rewriteCond %{http_host} ^example.com [NC]
    rewriteRule ^(.*)$ http://www.example.com/$1 [R=301,L]

用301将绑定的其他域名重定向到主域名

    RewriteEngine on
    RewriteCond %{HTTP_HOST} ^其他域名.com$ [OR]
    RewriteCond %{HTTP_HOST} ^www.其他域名.com$
    RewriteRule ^(.*)$ http://www.主域名.com/$1 [R=301,L]

当然，也可以再扩展一下，将index.html、index.php等也重定向一下：

    RewriteEngine on
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9} /index.php HTTP/
    RewriteRule ^index.php$ http://www.example.com/ [R=301,L]

检查工具：
[点击使用URL标准化监测工具][1]


  [1]: http://www.internetofficer.com/seo-tool/redirect-check
