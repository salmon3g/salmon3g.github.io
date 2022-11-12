---
title: Bye Typecho, Hello hugo
description: 博客从Typecho转为hugo。
categories: [life]
tags: [hugo]
slug: bye-typecho-hello-hugo
draft: false
date: "2022-11-10 22:31:05"
---


再见 Typecho，你好 Hugo.

## 本地安装hugo

通过终端安装

```
brew install hugo
```

创建一个站点
```
hugo new site hugoblog
```

添加一个主题

```html
cd hugoblog
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
```

按主题介绍配置主题，具体操作略...

添加一篇文章

```
hugo new posts/hello.md
```

打开 hello.md，用 markdown 编辑文章，内容如下:

```yaml
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

启动服务

```
hugo server
```

然后访问 http://localhost:1313/ 便可以查看站点了。

生成静态文件

```
hogu
```

静态文件将会在 public 文件夹中。

## Github 部署

创建一个仓库，命名为 xxx.github.io (xxx必须为github用户名)。切到本地 hugo 所踪的目录，分别按顺序执行以下命令：

```bash
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:xxx/xxx.github.io.git
git push -u origin blog
```

如果一切正常，这是打开 xxx.github.io 就可以看到你的站点了。

另外一些常用的 git

```bash
/* Push an existing folder */
cd existing_folder
git init --initial-branch=main
git remote add origin xxxxxx
git add .
git commit -m "Initial commit"
git push -u origin main

/* Push an existing Git repository */
cd existing_repo
git remote rename origin old-origin
git remote add origin xxxxxxx
git push -u origin --all
git push -u origin --tags

/* 删除远程地址 */
git remote rm origin

```

## 自动化发布

自动化发布需要借助 Github Action 完成。所以需要将网站的源码和 public 下面的内容放在 xxx.github.io 仓库的不同分支，不过要保证主分支必须放的是 public 里面的内容。我这里的分支对应关系是 main 分支存放 public，blog 分支存放源码，其中 main 为主分支。

先来配置一下 action：

1. 去 xxx.github.io 仓库的 `Settings->Deploy keys` 添加一个新的 deploy key，这个 key 用你的 ssh 公钥即可，记得勾选 `Allow write access`。
2. 在 `Settings->Secrets` 下添加一个新的 Secrets，这里填写你的 ssh 密钥，名字为了与之后的脚本对应就设置为 `ACTIONS_DEPLOY_KEY`。
3. 在源码对应的分支下根目录下创建一个 `.github` 的目录，在 `.github` 下创建一个叫做 `workflows` 的目录，`workflows` 目录下创建一个 `public.yml` 的文件。简单来说就是 github action 会从分支根目录下寻找 .github/workflows 目录，这个目录下存放的就是你的一些 action，如果你有多个任务可以创建多个 action，不过这里就不多说了。

ssh 公钥秘钥说明：

> - 公钥：id_rsa.pub
> - 秘钥：id_rsa

public.yml 文件的内容如下

```yaml
name: Build and Publish Blog

on: 
  push:
    branches:
      - blog

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@master
        with:
          fetch-depth: 0
      - name: Disable quotePath
        run: git config --global core.quotePath false
      - name: setup hugo
        uses: peaceiris/actions-hugo@v2
        with:
            hugo-version: 'latest'
      - name: build hugo
        run: hugo --gc --minify --cleanDestinationDir
      - name: deploy hugo
        uses: peaceiris/actions-gh-pages@v2
        env:
          ACTIONS_DEPLOY_KEY: ${{ secrets.ACTIONS_DEPLOY_KEY }}
          PUBLISH_BRANCH: main
          PUBLISH_DIR: ./public
```



关键点说明：

1. branches 下指定的分支是网站源码所在的分支，如果指定错误这个 action 就无法运行
2. `ACTIONS_DEPLOY_KEY` 的值对应于之前在 `Settings->Secrets` 下添加的 `Secrets`，确保两者一致即可
3. `PUBLISH_BRANCH` 对应于主分支
4. `PUBLISH_DIR` 对应于执行 hugo 命令后生成文件的位置，一般默认就是 `./public`

做完这些之后再将内容推送到 blog 分支的时候，action 就会自动执行构建过程，然后将构建好的博客内容推送到 main 分支.
