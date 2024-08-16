---
title: 嵌入式组件
description: 使用 iFrame 将 Solar Network 上的内容嵌入到你的网页内
published: true
date: 2024-08-16T18:04:07.836Z
tags: solar network, project open
editor: markdown
dateCreated: 2024-08-16T17:51:27.720Z
---

嵌入式组件（Embed Widget）是借助 iFrame 实现的网页小组件，你可以用其展示 Solar Network 上的内容。

## 用途

- 你可以用该组件将你管理的领域嵌入到你的网页，好展示你们领域内的近期活动。
- 你可以用该组件嵌入一个帖子，作为上下文阐述一个事件

## 用法

<iframe src="https://solsynth.dev/embed/posts/888" width="480" height="640" frameborder="0" style="border:none"></iframe>

以上你可以看见一个 480x640 的小组件里面放 #888 号帖子，讲的是我们使用 Cloudflare 的故事。

这就是嵌入小组件，用法非常简单，上面的事例代码如下

```html
<iframe src="https://solsynth.dev/embed/posts/888" width="480" height="640" frameborder="0" style="border:none"></iframe>
```

你可能注意到了嵌入式组件的链接就是一个正常的帖子链接前加上 `/embed`，是的没错，嵌入式组件的命名规则就是如此，页脚的在网站中打开也是在 URL 中去除前缀来工作的。你可以尝试在一个正常链接的前面加上 `/embed` 来看看其时候支持嵌入。如果可以的话，大胆去嵌吧！

## 客制化

部分嵌入式组件支持客制化，你可以在下面看到一些详情，但是部分嵌入式组件可能需要转到其子页面才会显示可用选项，所以还请善用搜索。

### 帖子列表

所有帖子列表组件都支持以下选项，你可以在浏览器内尝试一下。

### 不显示开头区域

添加参数 `no-title=1`（任意值均可）

<iframe src="https://solsynth.dev/embed/posts?no-title=1" width="480" height="640" frameborder="0" style="border:none"></iframe>

```html
<iframe src="https://solsynth.dev/embed/posts?no-title=1" width="480" height="640" frameborder="0" style="border:none"></iframe>
```

### 自定义标题显示

添加参数 `title` 与 `caption`

<iframe src="https://solsynth.dev/embed/posts?title=岁月史书&caption=翻开这本厚重的岁月史书，去探索岁月的痕迹" width="480" height="640" frameborder="0" style="border:none"></iframe>

```html
<iframe src="https://solsynth.dev/embed/posts?title=岁月史书&caption=翻开这本厚重的岁月史书，去探索岁月的痕迹" width="480" height="640" frameborder="0" style="border:none"></iframe>
```