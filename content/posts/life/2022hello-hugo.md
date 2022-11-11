---
title: Bye Typecho, Hello hugo
description: 博客从Typecho转为hugo。
categories: [life]
tags: [hugo]
slug: bye-typecho-hello-hugo
date: "2022-11-11 22:31:05"
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

打开 hello.md，用 markdown 编辑文章，内容如下:

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

启动服务

```
hugo server
```

然后访问 http://localhost:1313/ 便可以查看站点了

生成静态文件

```
hogu
```

静态文件将会在 public 文件夹中

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

如果一切正常，这是打开 xxx.github.io 就可以看到你的站点了。

## 自动化发布

为了这个自动化的过程，你需要将网站的源码和 public 下面的内容放在 xxx.github.io 仓库的不同分支，不过要保证主分支必须放的是 public 里面的内容。我这里的分支对应关系是 main 分支存放 public，blog 分支存放源码，其中 main 为主分支。

这个自动化的过程需要结合 github action 来完成。

首先我们先来配置一下 action。

1. 去 xxx.github.io 仓库的 `Settings->Deploy keys` 添加一个新的 deploy key，这个 key 用你的 ssh 公钥即可，记得勾选 `Allow write access`。
2. 在 `Settings->Secrets` 下添加一个新的 Secrets，这里填写你的 ssh 密钥，名字为了与之后的脚本对应就设置为 `ACTIONS_DEPLOY_KEY`。
3. 在源码对应的分支下根目录下创建一个 `.github` 的目录，在 `.github` 下创建一个叫做 `workflows` 的目录，`workflows` 目录下创建一个 `public.yml` 的文件。简单来说就是 github action 会从分支根目录下寻找 .github/workflows 目录，这个目录下存放的就是你的一些 action，如果你有多个任务可以创建多个 action，不过这里就不多说了。

ssh 秘钥获取方式：

首先点击 github 头像在下拉栏里进入 Setting-Developer Settings-Personal access tokens，选择 Generate new token。在上方填入名字，并勾选 repo 和 admin:repo_hook 里的所有选项，点击 Generate token 生成token，并先复制保存该token。

public.yml 文件的内容如下

```
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



这里只介绍其中几个比较关键的点：

1. branches 下指定的分支是你网站源码所在的分支，如果指定错误这个 action 就无法运行
2. `ACTIONS_DEPLOY_KEY` 的值对应于你之前在 `Settings->Secrets` 下添加的 `Secrets`，确保两者一致即可
3. `PUBLISH_BRANCH` 对应于你的主分支
4. `PUBLISH_DIR` 对应于执行 hugo 命令后生成文件的位置，一般默认就是 `./public`

做完这些之后再将内容推送到 blog 分支的时候，action 就会自动执行构建过程，然后将构建好的博客内容推送到 main 分支.