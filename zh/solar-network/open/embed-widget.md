---
title: 嵌入式组件
description: 使用 iFrame 将 Solar Network 上的内容嵌入到你的网页内
published: true
date: 2024-08-16T17:51:27.720Z
tags: solar network, project open
editor: markdown
dateCreated: 2024-08-16T17:51:27.720Z
---

嵌入式组件（Embed Widget）是借助 iFrame 实现的网页小组件，你可以用其展示 Solar Network 上的内容。

## 用途

- 你可以用该组件将你管理的领域嵌入到你的网页，好展示你们领域内的近期活动。
- 你可以用该组件嵌入一个帖子，作为上下文阐述一个事件

## 用法

<iframe src="https://solsynth.dev/embed/posts/888" width="480" height="640" frameborder="0" />

以上你可以看见一个 480x640 的小组件里面放 #888 号帖子，讲的是我们使用 Cloudflare 的故事。

这就是嵌入小组件，用法非常简单，上面的事例代码如下

```html
<iframe src="https://solsynth.dev/embed/posts/888" width="480" height="640" frameborder="0" />
```
