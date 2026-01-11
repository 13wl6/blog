---
title: Electron环境搭建
swiper_index: 10
top_group_index: 10
background: '#fff'
date:
updated:
tags:
categories:
keywords:
description:
top:
top_img:
comments:
toc:
toc_number:
toc_style_simple:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
aside:
ai:
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