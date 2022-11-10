---
title: "企业级开源可视化报表平台：Superset"
categories: [PM]
tags: ["BI","数据产品"]
draft: false
slug: "superset"
date: "2020-03-14 13:46:00"
---

[Apache Superset][1] 是一款由 Python 语言为主开发的企业级数据探索分析以及可视化的报表平台，由 Airbnb 开源，后面进入 Apache 软件基金会孵化。支持丰富的数据源和可视化图表样式，国内外已经有很多知名企业在使用了，如Airbnb、Netflix、Dropbox、Twitter、去哪儿、B站、豆瓣、腾讯音乐等。

## 特征
* 开源，轻量级、高可用，使用维护简单且便于二次开发
* 可视化方面非常出色，报表、看板等表现力很好
* 操作便捷，拖拉拽简单操作便可无代码生成可视化图表
* 图表类型丰富，有时间序列、组合图、分布图、关系图、GEO地理位置、词汇云、等40多种图表类型
* 支持数据源丰富，包括Clickhouse、Presto、Durid、Kylin、Impala、Hive、MySQL、Oracle等30多种数据源
* 先进的SQL IDE，底层配合Clickhouse，自助SQL跑数神器
* 支持灵活添加自定义可视化插件的能力

## 实操

我请我同事帮忙写了一份入门教程，具体操作如下：

1、添加database
<img src='http://cn.ip7.ltd/img/6v9333.png' alt='6v9333'/>
<img src='http://cn.ip7.ltd/img/gZ4BXz.png' alt='gZ4BXz'/>

2、添加Table
<img src='http://cn.ip7.ltd/img/8R0Bsa.png' alt='8R0Bsa'/>

3、SQL查询(生成视图表)
<img src='http://cn.ip7.ltd/img/EwOBfp.png' alt='EwOBfp'/>

4、绘图
<img src='http://cn.ip7.ltd/img/KGy9Ri.png' alt='KGy9Ri'/>

5、设计Dashboad
<img src='http://cn.ip7.ltd/img/082pjO.png' alt='082pjO'/>

6、共享Dashboard

方法1：添加DB权限。为观看者添加Charts的DB权限，会自动包含Table(原生表+视图表)的接入权限，则可观看对应Charts和Dashboard的权限。此时，Dashboard添加同DB下的Chart，不需要重新授权。

方法2：添加表权限。如果在Dashbaord新增了Charts，则需要编辑保存授权。

为用户添加表权限或者DB权限
先为角色添加权限。有DB权限会自动有表权限，可仅授予表权限
<img src='http://cn.ip7.ltd/img/hlCRLV.png' alt='hlCRLV'/>

在将角色绑定到用户
<img src='http://cn.ip7.ltd/img/iLMIiz.png' alt='iLMIiz'/>

## 其他
通过二次开发，可以将看板推送到企微群，例如团队内日报群，运维报警群等。
<img src='http://cn.ip7.ltd/img/79mNbG.png' alt='79mNbG'/>

异步查询架构
<img src='http://cn.ip7.ltd/img/lx23aed.png' alt='lx23aed'/>

Echart Demo
<img src='http://cn.ip7.ltd/img/ptnyQ7.png' alt='ptnyQ7'/>
<img src='http://cn.ip7.ltd/img/Pw52qH.png' alt='Pw52qH'/>
<img src='http://cn.ip7.ltd/img/rbcrik.png' alt='rbcrik'/>


  [1]: https://superset.apache.org/
