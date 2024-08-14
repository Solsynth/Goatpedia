---
title: 贴图及贴图包
description: Stickers, Emotes 和 Emoji
published: true
date: 2024-08-14T02:48:10.120Z
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