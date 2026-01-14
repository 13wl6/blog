---
abbrlink: ''
ai: null
aplayer: null
aside: null
background: '#fff'
categories:
- - Node
comments: null
copyright: null
copyright_author: null
copyright_author_href: null
copyright_info: null
copyright_url: null
date: '2026-01-14T19:33:29.942+08:00'
description: null
highlight_shrink: null
katex: null
keywords: null
mathjax: null
swiper_index: 10
tags:
- telegram
title: TG机器人搭建教程Node.js
toc: null
toc_number: null
toc_style_simple: null
top: null
top_group_index: 10
top_img: null
updated: '2026-01-14T19:33:29.942+08:00'
---
### 创建机器人

这个步骤网上有很多方案，直接采用即可（通过`botfather`创建）

这里只讲开发 不讲创建 浪费各位的时间了

### 开发机器人

github 上有很多开源的  如 `grammY`、`telegramsjs`、`node-telegram-bot-api` 等

使用 `node-telegram-bot-api` 做演示

### 使用 `node-telegram-bot-api` 实现自动回复（`Node.js`）

github搜索`node-telegram-bot-api`，查看README文档使用快速入门方案

```typescript
npm i node-telegram-bot-api
# 使用TypeScript开发时需要用到的类型声明
npm install --save-dev @types/node-telegram-bot-api
# 快速入门（创建index.ts编写以下代码）
const TelegramBot = require('node-telegram-bot-api');

// replace the value below with the Telegram token you receive from @BotFather
const token = 'YOUR_TELEGRAM_BOT_TOKEN';

// Create a bot that uses 'polling' to fetch new updates
const bot = new TelegramBot(token, {polling: true});

// Matches "/echo [whatever]"
bot.onText(/\/echo (.+)/, (msg, match) => {
  // 'msg' is the received Message from Telegram
  // 'match' is the result of executing the regexp above on the text content
  // of the message

  const chatId = msg.chat.id;
  const resp = match[1]; // the captured "whatever"

  // send back the matched "whatever" to the chat
  bot.sendMessage(chatId, resp);
});

// Listen for any kind of message. There are different kinds of
// messages.
bot.on('message', (msg) => {
  const chatId = msg.chat.id;

  // send a message to the chat acknowledging receipt of their message
  bot.sendMessage(chatId, 'Received your message');
});
```

注意需要把token换成自己机器人的token

原本以为这部分可以顺利完成，结果运行node .\index.ts后卡住，控制台与tg聊天框均没有反应，通过查找与询问发现tg被国内墙了，

虽然已经使用🪜可以使用tg，但是程序并没法发送请求到api.telegram.org服务器，所以需要在程序中使用代理服务，这里以使用V2rayN为例，

首先在V2rayN的参数设置中设定好本地socks监听端口（一般默认为10808），然后修改程序添加代理服务

```typescript
const { SocksProxyAgent } = require('socks-proxy-agent');

// 使用 socks 代理
const agent = new SocksProxyAgent('socks://127.0.0.1:10808');
const token = 'YOUR_TELEGRAM_BOT_TOKEN'; // 检查你的 token 是否正确

const bot = new TelegramBot(token, {
  polling: true,  // 启用 polling
  request: {
    agent,  // 使用代理进行请求
  },
});

bot.onText(/\/ping/, (msg) => {
  const chatId = msg.chat.id;
  bot.sendMessage(chatId, 'pong');
});

// 启动 bot
bot.on('polling_error', (error) => console.log('Polling error:', error));  // 打印错误
```

注意，在使用代理服务时我原先在bot配置里加入了`testEnvironment: true`参数，

导致运行时程序以为我在模拟环境中测试，并没有与实际的`telegarm API`服务器通信，

从而报错 `error: [polling_error] {"code":"ETELEGRAM","message":"ETELEGRAM: 401 Unauthorized"}`
踩过各种坑之后运行`node .\index.ts`终于成功了

![](https://wkphoto.bj.bcebos.com/342ac65c10385343b7edb4768313b07eca808842.jpg)

