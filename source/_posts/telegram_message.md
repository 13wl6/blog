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
date: null
description: null
highlight_shrink: null
katex: null
keywords: null
mathjax: null
swiper_index: 10
tags: []
title: 酒神电报私聊机器人部署教程
toc: null
toc_number: null
toc_style_simple: null
top: null
top_group_index: 10
top_img: null
updated: '2026-01-12T21:01:43.166+08:00'
---
## TG私聊机器人的优点

由机器人转发其他用户的私聊消息，通过回复机器人所转发的消息即可回复用户，有着防删消息的功能，同时还可以减少窗口的数量且也保障了自己一定的隐私问题。

## 搭建

* **创建机器人**

1、因为以前的消息还有用，所以我重新生成新的Token。打开BotFather（[@BotFather](https://www.nodeseek.com/member?t=BotFather)），回复 `/mybots `，选择你的转发机器人，选择`API Token`，再选择`Revoke current token`，此时会生成机器人新的Token。如果不想机器人被添加到群组，可以在BotFather发送`/setjoingroups`来禁止此Bot被添加到群组。

2、如是是新创建机器人，在BotFather（[@BotFather](https://www.nodeseek.com/member?t=BotFather)）创建自己的机器人，并记录Token。

* **获取uuid作为secret**

从[uuidgenerator](https://www.nodeseek.com/jump?to=https%3A%2F%2Fwww.uuidgenerator.net%2F)获取一个随机uuid作为secret(打码为了防止照抄uuid)

![8912c1a0f0cdfc8e3de58fc20b991176.jpeg](https://i.miji.bid/2025/03/10/8912c1a0f0cdfc8e3de58fc20b991176.jpeg)

* **获取TG用户ID**

从[username\_to\_id\_bot](https://www.nodeseek.com/jump?to=https%3A%2F%2Ft.me%2Fusername_to_id_bot) ([@username](https://www.nodeseek.com/member?t=username)\_to\_id\_bot)获取你的用户id

![5ee4bc5d552e811167d208c8b235e0c0.jpeg](https://i.miji.bid/2025/03/10/5ee4bc5d552e811167d208c8b235e0c0.jpeg)

* **登录cloudflare，创建一个workers**

![84a28024704c26419010ce899214e238.jpeg](https://i.miji.bid/2025/03/10/84a28024704c26419010ce899214e238.jpeg)

![acc8067f8220f0da1b595becc6c8355d.jpeg](https://i.miji.bid/2025/03/10/acc8067f8220f0da1b595becc6c8355d.jpeg)

![123422c0888996466e0c627e5a60f14b.jpeg](https://i.miji.bid/2025/03/10/123422c0888996466e0c627e5a60f14b.jpeg)

点击`Hello word后`，不要动其他的，直接拉到下方点击部署。

![c409d14f526d70b763cb4b53684f5b27.jpeg](https://i.miji.bid/2025/03/10/c409d14f526d70b763cb4b53684f5b27.jpeg)

* **配置workers的变量**

再次点击`Workers和Pages`，点击刚才部署好的workers

![fd933acb6ba533843a93f126cf7f6339.jpeg](https://i.miji.bid/2025/03/10/fd933acb6ba533843a93f126cf7f6339.jpeg)

点击设置

![a2ee3891ebba9edc08c557820bd6d868.jpeg](https://i.miji.bid/2025/03/10/a2ee3891ebba9edc08c557820bd6d868.jpeg)

找到`变量和机密`，点击添加

![23f2d3ce66838db14453b67842b0ab94.jpeg](https://i.miji.bid/2025/03/11/23f2d3ce66838db14453b67842b0ab94.jpeg)

增加一个`ENV_BOT_TOKEN`变量，数值为机器人的token
增加一个`ENV_BOT_SECRET`变量，数值为获取到的uuid作为secret
增加一个`ENV_ADMIN_UID`变量，数值为获得的用户id

![48464b0ff8ae00d33737f85a770aa2af.jpeg](https://i.miji.bid/2025/03/10/48464b0ff8ae00d33737f85a770aa2af.jpeg)

点击部署。

* **创建KV**

找到`存储和数据库`，然后点击`KV`

![eb0022edb67506d3fa9e772775977681.jpeg](https://i.miji.bid/2025/03/10/eb0022edb67506d3fa9e772775977681.jpeg)

点击创建，名称设置为`nfd`，然后添加

![8362582d3ccce1a5579ee62514b61eb1.jpeg](https://i.miji.bid/2025/03/10/8362582d3ccce1a5579ee62514b61eb1.jpeg)

* **绑定KV**

回到`Workers和Pages`，点击刚才部署好的workers，进入设置

![a2ee3891ebba9edc08c557820bd6d868.jpeg](https://i.miji.bid/2025/03/10/a2ee3891ebba9edc08c557820bd6d868.jpeg)

下拉找到`绑定`，点击添加

![010943bf3ac213729c97fde4cd1d7623.jpeg](https://i.miji.bid/2025/03/10/010943bf3ac213729c97fde4cd1d7623.jpeg)

点击`KV命名空间`

![8bd37a8457d0749b16dfc32f24da9846.jpeg](https://i.miji.bid/2025/03/10/8bd37a8457d0749b16dfc32f24da9846.jpeg)

前面写`nfd`，后面选择你刚才创建的`nfd`，然后部署

![e972114a36a29cc8b3c23651e13f0558.jpeg](https://i.miji.bid/2025/03/10/e972114a36a29cc8b3c23651e13f0558.jpeg)

* **编辑workers的代码**

回到`Workers和Pages`，点击刚才部署好的workers，点击右上角第三个图标编辑代码

![b0d8a13d82d902fdc6aa2dc456ee60a1.jpeg](https://i.miji.bid/2025/03/10/b0d8a13d82d902fdc6aa2dc456ee60a1.jpeg)

会看到以下界面

![b44d98e8ad63a43692efb874a3aef2e7.jpeg](https://i.miji.bid/2025/03/10/b44d98e8ad63a43692efb874a3aef2e7.jpeg)

选择左边的代码，ctrl+a全选然后删除

打开[这个网页](https://www.nodeseek.com/jump?to=https%3A%2F%2Fgithub.com%2FLloydAsp%2Fnfd%2Fblob%2Fmain%2Fworker.js) ，点击复制

![a58027c5556afad2a36d100f64146988.jpeg](https://i.miji.bid/2025/03/10/a58027c5556afad2a36d100f64146988.jpeg)

粘贴到左边，并点击部署

![a8ebeb50695fbe0c808ba4ba2b713289.jpeg](https://i.miji.bid/2025/03/10/a8ebeb50695fbe0c808ba4ba2b713289.jpeg)

## 验证

回到`Workers和Pages`，点击刚才部署好的workers，进入设置

![9c9aed7c72a5cee1050921296d5fc3bb.jpeg](https://i.miji.bid/2025/03/10/9c9aed7c72a5cee1050921296d5fc3bb.jpeg)

复制红色框中的内容，将这个网址粘贴到浏览器，在后面添加`/registerWebhook`，然后回车，网页中会出现OK。

自此，便部署好了私聊机器人。

## 机器人设置

部署好后，用户第一次向我发消息时，会有一些提示的消息，如果不想展示，可以通过修改代码取消通知。

把代码中的11行中的`true`改成`false`即可

![8df418091b5354df5e1c0ae6ef057cfb.jpeg](https://i.miji.bid/2025/03/11/8df418091b5354df5e1c0ae6ef057cfb.jpeg)

如果想保留骗子的提醒功能，又取消其他的通知，屏蔽第8和第9行代码即可，不用修改第11行代码

![3547bc9a4cdf53f106fce0cebb371ea1.jpeg](https://i.miji.bid/2025/03/11/3547bc9a4cdf53f106fce0cebb371ea1.jpeg)

```
/** 
 * const notificationUrl = 'https://raw.githubusercontent.com/LloydAsp/nfd/main/data/notification.txt'
 * const startMsgUrl = 'https://raw.githubusercontent.com/LloydAsp/nfd/main/data/startMessage.md';
*/
```

把以上内容替换第8和第9行代码，然后点击部署，然后验证即可。

