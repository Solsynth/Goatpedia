---
title: Solian
description: Solian（索链）是由 Flutter 编写的全平台支持官方客户端。
published: true
date: 2024-06-29T17:08:57.449Z
tags: solar network, solian
editor: markdown
dateCreated: 2024-06-29T16:12:53.290Z
---

Solian 是由 Flutter 编写的全平台 Solar Network 客户端，也是我们目前唯一的前端。

# 使用

想要使用 Solian，你可以下载客户端，也可以直接在浏览器中打开。得益于 Flutter 的全平台支持，你可以在 https://lian.solsynth.dev 访问到 Solian 网页版。但由于浏览器限制，部分功能可能欠缺或受到影响。

## 下载

下载 Solsynth 的方式很多，但一定请从官方认证的渠道下载。

1. 官方仓库发布的正式版本 https://git.solsynth.dev/Hydrogen/Solian/releases
2. 官方文件托管柜发布的测试版本 https://files.solsynth.dev/media01/package/solian
3. 官方 TestFlight (iOS 与少量 macOS) https://testflight.apple.com/join/YJ0lmN6O

Windows 版本系免安装版本，放置于一个您熟悉的目录即可使用。  
Web 版本同时支持 PWA 渐进式网页应用，可以替代一部分桌面端使用。

## 安装

以下是个平台安装 Solian 的技术要领。

### Android

推荐从**文件托管柜**下载最新测试版，版本最新，修复最全，最稳定。~~测试版比稳定版稳定~~

下载下来的 APK 档案可以直接打开安装。中国版手机可能需要额外步骤验证，但请不要使用自带应用商店搜索下载。

### iOS/macOS

使用 TestFlight 安装。可以点击上方链接首先下载安装 TestFlight App。再点击上方链接的第二部开始测试来参加测试。

TestFlight 的测试名额有限，等到时机成熟我们会将 Solian 发布于非中国区的 App Store，可以前往 App Store 搜索下载。

### Windows

Windows 从任意可信渠道下载后解压到一个目录即可使用。

**注意：** Windows 版本不知是否属于 Flutter 的支持问题，在第一次启动加载时总是会卡好一会才弹出主窗口。不用反复点击，请耐心等待，可能会使用 5 到 30 秒。如果多次点击可能会打开多个窗口。

### Linux

请自行构建。我相信你们可以的，加油哦~