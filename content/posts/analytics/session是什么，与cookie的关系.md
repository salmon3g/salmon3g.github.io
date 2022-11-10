---
title: "session是什么，与cookie的关系"
categories: ["analytics"]
tags: []
draft: false
slug: "session"
date: "2011-11-23 08:21:00"
---

session 的中文译名叫做“会话”，原意指有始有终的一系列动作消息，比如我们从拨通电话到挂掉电话的一系列过程可以称之为一个 session 。session 是表示一个持续连接的状态，一般指访客打开浏览器浏览一个网站开始到关闭浏览器（即浏览器的进程从开启到结束）。session 更多的是表示一个访问的过程，是网站分析的访问度量。

session 可以追踪用户在网站上的活动，比如我们网上购物，我们是先将商品放入购物车，然后再一起支付。在我们整个过程中购物车一直扮演着临时存贮被选商品的角色，这就是 session 的作用，它可以用于用户身份认证，程序状态记录，页面之间参数传递等。session 的实现中采用 cookie 技术，session 会在客户端保存一个包含 session id（session 编号）的 cookie；在服务器端保存其他 session 变量，比如 session name 等等。当用户请求服务器时也把session id 一起发送到服务器，通过 session id 提取所保存在服务器端的变量，就能识别用户是谁了。

session 失效时间分两方面：浏览器端和服务端。对于浏览器端而言，session 与访问进程直接相关，当浏览器被关闭时，session 也随之消失；而服务器端的 session 失效时间一般是人为设置的，目的是能定期地释放内存空间，减小服务器压力，一般的设置为当会话处于非活动状态达 20 或 30 分钟时清除该 session（多数网站分析工具默认时间均为 30 分钟），所以浏览器端和服务端的 session 并非同时消失的，session 的中断也并不一定意味着用户一定离开了该网站。

## session 和 cookie 的关系

session 通过 cookie ，在客户端保存 session id ，而将用户的其他会话消息保存在服务端的 session 对象中。session 和 cookie 的最大区别在于 session 是保存在服务端的内存里面，而 cookie 保存于浏览器或客户端文件里面；session 是基于访问的进程，记录了一个访问的开始到结束，当浏览器或进程关闭之后，session 也就“消失”了，而 cookie 更多地被用于标识用户，它可以是长久的，用于用户跟踪和识别唯一用户。
