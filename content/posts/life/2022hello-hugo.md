title: Bye Typecho, Hello hugo
description: 博客从Typecho转为hugo。
categories: [life]
tags: [hugo]
slug: bye-typecho-hello-hugo
date: "2022-11-11 22:31:05"
---

再见Typecho，你好Hugo.

## 安装hugo

通过终端安装

```
brew install hugo
```

创建一个站点

```
hugo new site hugoblog
```

添加一个主题

```
cd quickstart
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
```

按主题介绍配置主题，略...

添加一篇文章

```
hugo new posts/hello.md
```

打开hello.md，用markdown编辑文章，内容如下:

```
---
title: Bye Typecho, Hello hugo
description: 博客从Typecho转为hugo。
categories: [life]
tags: [hugo]
slug: bye-typecho-hello-hugo
date: "2022-11-11 22:31:05"
---

再见Typecho，你好Hugo.
...
```



## Github 部署

创建一个仓库，命名为 xxx.github.io (xxx必须为github用户名)

```git
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:xxx/xxx.github.io.git
git push -u origin blog
```