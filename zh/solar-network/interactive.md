---
title: Interactive
description: Solar Network 中的社交平台
published: true
date: 2024-07-24T07:19:12.036Z
tags: solar network, interactive
editor: markdown
dateCreated: 2024-07-24T07:03:49.107Z
---

Interactive 译为互动，是 Solar Network 中的社交平台。

## 帖子

Post 帖子是 Interactive 上组成内容的基本单位。

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