---
title: "Mac下安装和使用GitBook"
description: GitBook 是一款基于 Node.js 的命令行工具，配合 Markdown 写文档简直是一大「神器」。很多互联网产品的帮助文档都在使用 GitBook 编写，也有好多人用它来写电子书。
categories: ["life"]
tags: []
draft: false
slug: "mac-gitbook"
date: "2016-06-11 12:28:00"
---

GitBook 是一款基于 Node.js 的命令行工具，配合 Markdown 写文档简直是一大「神器」。很多互联网产品的帮助文档都在使用 GitBook 编写，也有好多人用它来写电子书。

## Mac下安装 GitBook
1、安装 Node.js

打开 Node.js 官网(www.nodejs.org)下载并安装 Node.js。安装完在终端检验：

```
node -v
v5.7.1
```

有版本提示，说明 Node.js 安装成功了。

2、安装 GitBook

```
npm install -g gitbook-cli
```

检验：

```
gitbook -V
v2.1.2
```

有版本提示，说明 GitBook 安装成功了。

## Mac 下使用 GitBook 写文档
打开终端，切换到预放置文档目录，使用 mkdir 命令创建文件夹，使用 init 初始化

```
mkdir Help
cd Help
gitbook init
```

初始化后的 Help 目录中会生成 README.md(简介)和SUMMARY.md(导航目录)两个文件。README.md 主要是文档的简单介绍，SUMMARY.md 是文档的导航和目录，每新增一个文件就要向此文件中添加一条记录，格式如下：

```
Summary

[简介](README.md)
[H5 活动监测](H5.md)
    [使用指南](H5_1.md)
    [分页监测](H5_2.md)
```

文档写好后，可以使用 build 命令将 .md 文件 生成 html 文件

```
gitbook build
```

生成完毕后，Help 目录中出现一个名为 「_book」的文件夹。进入该文件夹，可以直接用浏览器打开 index.html 进行预览，或使用 serve 命令：

```
gitbook serve
```

然后在浏览器中输入  [http://localhost:4000](http://localhost:4000/)  预览，按 Ctrl + C 结束。
是不是很方便 :) 更多问题请参考  [GitBook 帮助文档](http://help.gitbook.com/) 。
