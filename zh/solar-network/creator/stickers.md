---
title: 贴图及贴图包
description: Stickers, Emotes 和 Emoji
published: true
date: 2024-08-14T03:54:15.435Z
tags: solar network
editor: markdown
dateCreated: 2024-08-14T02:48:10.120Z
---

贴图可以帮助用户通过 Solar Network 更好的表达他们的情绪，这篇文章将会向你介绍如何上传、使用一个贴图

## 贴图包

贴图必须跟随一个贴图包，要创建一个贴图包，你首先需要获得创作者计划的权限，之后利用 cURL 工具向服务器发起一个 POST 请求来创建贴图包。

```http
POST https://api.sn.solsynth.dev/cgi/files/stickers/packs
Content-Type: application/json
Authorization: Bearer <your token here>

{
    "prefix": "solar",
    "name": "Solar Network Defaults",
    "description": "Solar Network official default sticker pack, with a bunch of useful and funny stickers."
}
```

这个 API Endpoint 将会返回一个 JSON 对象其中包括了你贴图包的详情信息，其中有一个 `"id"` 字段你需要格外留意，将其记下来。之后会用到。

贴图的其他操作可以使用对应的 PUT 和 DELETE API Endpoint，只是注意在对制定的贴图包进行操作的时候需要在 URL 后面添加 ID 例如 `/cgi/files/stickers/packs/1`

## 贴图

贴图的创建，你首先需要准备内容。建议为一个 512x512 像素大小（最小为 128x128 的大小，否则可能造成效果不佳）的 PNG 或 GIF 图片，透明背景或内容背景均可，但请不要使用纯色填充。大面积的白色填充可能会给暗色模式的用户带来闪光弹。

之后，请下载安装 Solian 或使用网页版，具体请转到 [Solian 介绍页面](/zh/solar-network/solian)。

登陆账号后，在账户页面可以找到一个「贴图」入口，点进去即可看到刚刚创建的贴图包，若没有数据，请检查自己的贴图包创建是否成功。

点击页面下方的加号按钮，完成内容表单，贴图包序号填写上文的 `"id"` 字段。别名需要遵守 CamelCase 规则为最佳。

## 使用

使用贴图，需要在你的内容中键入一个文字占位符，具体的组成为 `:<pack prefix><sticker alias>:`。例如一个贴图包的前缀（`prefix`）为 `solar`，一个该贴图包的的贴图别名（`alias`）为 `Hello`，组成出来的占位符为 `:solarHello:`

不过不明白也别担心，大多数情况我们都有自动提示。只需在 Solian 内文本框键入一个英文冒号，再开始键入占位符的一部分即可。

### 大小变化

在 Solar Network 中，你可能看到大小不同的贴图，这是因为 Smart Resize 在背后发功。具体规则如下。

1. 当仅有一个贴图，将使用 128x128 的大小
2. 当有三个及一下的题图，将使用 32x32 的大小
3. 当有三个以上的贴图，或贴图夹杂在文本内时，将使用 20x20 的大小

## FAQ

以下是一些常见问题及解决方案。

Q1: 我创建了贴图，但是发出来对方没有显示\
A1: 贴图资料的加载是在开屏阶段完成，后续只有在退出贴图管理界面时才会二次刷新，尝试重新启动，如果还是无效，检查贴图时候创建成功