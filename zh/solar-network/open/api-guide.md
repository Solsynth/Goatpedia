---
title: API 准则
description: 在设计 Solar Network 服务 API 时惯用的准则
published: true
date: 2024-08-18T05:59:25.471Z
tags: solar network
editor: markdown
dateCreated: 2024-08-18T05:46:02.121Z
---

这篇文章是关于我们平时在设计 Solar Network API 时的范式是怎样的，能够帮助你更好的调用我们的 API 来进行第二次开发

## 最小化

我们的 API 一般追求极简，不像某些大平台的 API 一样除了数据之外的格式还有一大堆什么状态码、信息、请求 ID 什么的。这些信息我们都选择放在 HTTP 的 Header 部分。HTTP 的响应体就是纯粹的数据，无其他信息（需要分页的数据接口会额外返回一个数据总数）。

## 增删查改

我们的 API 基本上都是遵循 RESTful 设计范式的，如果你不知道什么是 RESTful，可以看以下我们理解的实践的 RESTful

### 请求方法

- `GET` 查询
- `POST` 创建、进行某种操作
- `PUT` 更新（虽在 RESTful 中也被定义为创建数据的行为，但是我们不使用）
- `PATCH` 更新（不常用）
- `DELETE` 删除

### 路径映射

假如你 POST 了一个地址来创建数据，那么用 GET 方法访问相同的地址大概就是列出数据的列表。
在其后面加上 `/<id>` 就是单独读取某个数据，将请求方法改成 PUT 便是更新该条数据，改成 DELETE 就是删除该条数据。
如果在 `/<id>` 再加上东西基本上就是 POST 方法来执行某个操作。
例如以下是我们帖子的路径映射

*注：`:id` 系路径参数*

- `GET /posts` 获取帖子列表（分页）
- `GET /posts/:id` 获取单个帖子
- `GET /posts/:id/replies` 获取单个帖子的回复（分页）
- `POST /posts` ~~创建帖子~~（于新版本因为引入帖子类型移除，需使用对应类型的创建接口）
- `PUT /posts/:id` ~~更新帖子~~（于新版本因为引入帖子类型移除，需使用对应类型的更新接口）
- `DELETE /posts/:id` 删除帖子
- `POST /posts/:id/pin` 置顶帖子
- `POST /posts/:id/react` 对帖子作出反应

## 错误处理

我们不理解为什么 HTTP 有给一套完善的状态码系统，其他大厂却仍选择自立门户。关于响应的 HTTP 状态码，以下是一些常用的含义代表。

- `500` 服务器内部错误 —— 你不用管，如果多见记得抛 issue
- `400` 请求参数错误 —— 看文档，核查请求体
- `404` 数据不存在或是接口路径不对
- `403` 没有权限
- `200` 成功
- `204` 无内容 —— 常见于删除 *虽然后时候写 API 会忘记删除内容时改成这个*

如果响应不是 `2xx` 的状态码，一般我们都不会返回 `application/json` 的数据，而是一个 `plain/text`，一行简单的文字来代表你犯了什么错。

> 如果你是英语白痴，遇到报错别老来问我们，用用翻译好吗？不然我们写报错信息干嘛。
{.is-warning}

## 超级网关

超级网关指的是我们的 [Hydrogen.Dealer](https://git.solsynth.dev/Hydrogen/Dealer)，一般情况下你都不会直接访问我们的服务，都是走 Dealer 的网关转发的。虽然我们也不知道为什么写了个这个东西。

我们 API 的地址为 `api.sn.solsynth.dev`，怎么用呢？很简单。访问 `/cgi/<service name>` 即可，这样的地址会被转发到对应服务的 `/api` 端点。新版本我们还给这些服务加了点别名，这样你的 URL 可以变得更好看点。

- `/cgi/id` 或 `/cgi/auth` —— 授权服务 [Hydrogen.Passport](https://git.solsynth.dev/Hydrogen/Passport)
- `/cgi/uc` 或 `/cgi/files` —— 附件服务 [Hydrogen.Paperclip](https://git.solsynth.dev/Hydrogen/Paperclip)
- `/cgi/co` 或 `/cgi/interactive` —— 帖子服务 [Hydrogen.Interactive](https://git.solsynth.dev/Hydrogen/Interactive)
- `/cgi/im` 或 `/cgi/messaging` —— 聊天服务 [Hydrogen.Messaging](https://git.solsynth.dev/Hydrogen/Messaging)

> 冷知识：你可能注意到了我们新配置的别名其实就是之前没有超级网关时他们使用的子域名。
{.is-info}
