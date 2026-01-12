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
date: '2026-01-12T21:05:39.241+08:00'
description: null
highlight_shrink: null
katex: null
keywords: null
mathjax: null
swiper_index: 10
tags: []
title: Electron环境搭建
toc: null
toc_number: null
toc_style_simple: null
top: null
top_group_index: 10
top_img: null
updated: '2026-01-12T21:05:39.241+08:00'
---
Electron是一个使用 JavaScript、HTML 和 CSS 构建桌面应用程序的框架。 Electron 将 Chromium 和 Node.js 嵌入到了一个二进制文件中，因此它允许你仅需一个代码仓库，就可以撰写支持 Windows、macOS 和 Linux 的跨平台应用。

```shell
Node.js 
Git
```

测试代码

```shell
 git clone https://github.com/electron/electron-quick-start   
```

启动项目

```
npm i && npm run start
```

npm 安装失败

```
npm install -g cnpm --registry=https://registry.npmmirror.com
```
