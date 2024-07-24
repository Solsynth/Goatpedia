---
title: Interactive
description: Solar Network 中的社交平台
published: true
date: 2024-07-24T07:38:53.655Z
tags: solar network, interactive
editor: markdown
dateCreated: 2024-07-24T07:03:49.107Z
---

Interactive 译为互动，是 Solar Network 中的社交平台。

## 帖子

Post 帖子是 Interactive 上组成内容的基本单位。用户可以借助帖子来表达他们的观点、情绪、分享生活中发生的事情。

用户可以通过主界面的「添加」按钮创建帖子，前提用户需要拥有 `CreatePosts` 权限节点。
帖子可以接受回复、转贴，详细的帖子操作可以长按帖子展开帖子操作。

帖子还可以接受「反应」，该功能维护帖子内容下方的 “快速操作” 区的帖子评论旁边。反应可以被添加和移除，只需点击对应想添加或移除的反应即可。

### 结构定义

```typescript
export interface Post {
    id:              number;
    created_at:      Date;
    updated_at:      Date;
    deleted_at?:     Date;
    type:            string;
    body:            any;
    language:        string;
    tags:            any[];
    categories:      any[];
    reactions:       { [ id: string ]: number };
    replies:         Post[];
    reply_id?:       number;
    repost_id?:      number;
    realm_id?:       number;
    reply_to?:       Post;
    repost_to?:      Post;
    realm?:          Realm;
    is_draft:        boolean;
    published_at:    Date;
    published_until?:Date;
    author_id:       number;
    author:          Account;
    metric:          Metric;
}
```