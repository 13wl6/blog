---
abbrlink: ''
ai: null
aplayer: null
aside: null
background: '#fff'
categories: []
comments: null
copyright: null
copyright_author: null
copyright_author_href: null
copyright_info: null
copyright_url: null
date: '2026-01-12T21:04:33.853+08:00'
description: null
highlight_shrink: null
katex: null
keywords: null
mathjax: null
swiper_index: 10
tags: []
title: 第一期： 零基础快速搭建个人博客， Hexo + GitHub Pages + Cloudflare Pages 全流程指南， 免费部署超详
toc: null
toc_number: null
toc_style_simple: null
top: null
top_group_index: 10
top_img: null
updated: '2026-01-12T21:04:33.853+08:00'
---
## 1. 前期准备工作

Node (必备)
Git (必备)
VSCode (可选)
域名, 建议配置一个域名以避免被 “防火墙” 阻挡, 国内域名需要备案，备案周期较长
配置 Cloudflare, 托管域名
Hexo 官方主题展示: Themes

### 1.1 安装 Node

从 Node 官网 找到适合自己系统的版本 建议 nvm 可以多版本管理

### 1.2 安装 Git

从 Git 官网 找到适合自己系统的版本 配置 Git 密钥并连接 Github

显示当前 Git 配置文件中的所有配置项

```shell
git config -l
```

显示系统级（适用于所有用户）的 Git 配置文件中的配置项

```shell
git config --system --list
```

显示全局（用户级） Git 配置文件中的配置项

```shell
git config --global --list
```

配置用户名和邮箱

```shell
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"
# 通过 git config -l 验证是否成功
```

#### 配置公钥连接 Github

生成 SSH 公钥

```shell
ssh-keygen -t rsa -C "你的邮箱"
```

一路回车生成密钥，进入 .ssh 文件夹复制 id_rsa.pub 公钥内容，配置到 Github 的 SSH 设置中

```shell
cd .ssh

ls

cat id_rsa.pub
```

将 SSH KEY 配置到 Github

进入 GitHub，点击右上角头像 选择 settings，进入设置页选择 SSH and GPG keys，名字随便起，公钥填入 key 那一栏。测试连接

```shell
ssh -T git@github.com
```

### 1.3 域名

这里推荐  https://domain.qqwl.org/ 免实名域名

### 1.4 Cloudflare

注册账号 登录

## 2 安装 Hexo

```shell
npm install hexo-cli -g[](https://hexo.io/zh-cn/docs/)

#创建文件
hexo new post [文章别名]
```

具体的可以看文档

https://hexo.io/zh-cn/docs/

### 上传到 GitHub

首先 打开GitHub 的主页 添加一个新的仓库

```shell
git init 
```

### 部署

打开 cf 网站

首先要把域名 托管的 cf 中 打开侧边的 计算与AI 中的 page

![](https://wkphoto.bj.bcebos.com/83025aafa40f4bfb2112a303134f78f0f63618a2.jpg)

最下面的  [Get started](https://dash.cloudflare.com/81777ae5d0299c5855abdb26dd606045/workers-and-pages/create/pages)
