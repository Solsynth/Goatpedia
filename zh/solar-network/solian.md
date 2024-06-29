---
title: Solian
description: Solian（索链）是由 Flutter 编写的全平台支持官方客户端。
published: true
date: 2024-06-29T17:19:50.791Z
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

## 自行构建

### 环境准备

构建 Solian 需要使用 Flutter SDK，请在官网下载最新版安装。也可以从中国镜像站下载安装。  
安装完成 Flutter 请根据官方文档下载其他对应平台需要的开发依赖，例如 Windows 需要 VS2022、Android 需要 Android Studio、iOS/macOS 我劝你还是用官方版本构建的吧。

除开安装 Flutter SDK，我们还需要使用 Rust 做系统级依赖支持。请从 Rust 官方下载最新版本。

现在我们有了 Flutter、Rust，还少一个东西，为了实现聊天及未来的其他模块本地数据库支持。  
Linux 版本还需要安装对应的 SQLite3 开发依赖。

```sh
# for ubuntu
sudo apt-get -y install libsqlite3-0 libsqlite3-dev
```

Windows 需要下载 [sqlite3.dll](https://github.com/tekartik/sqflite/raw/master/sqflite_common_ffi/lib/src/windows/sqlite3.dll) 放置在运行目录。  
macOS 及手机端构建不需要其他操作。

### 构建代码

之后就是构建代码的时候了。确保你在构建机器上安装了 `git` 版本管理工具。或者你想直接下载代码压缩档案也不是不行。
确保 `git` 安装之后可以使用以下命令克隆代码。

```sh
git clone https://git.solsynth.dev/Hydrogen/Solian.git
```

之后导航到对应目录，使用以下命令安装依赖。

```sh
flutter pub get
```

该操作会从 [pub.dev](https://pub.dev) 上下载依赖，而 pub.dev 是由 Google 托管提供。所以中国大陆的连接性要被打个问号。具体可以参考中国大陆镜像站点查询解决方案。

完成依赖获取后就可编译了，一行命令就搞定。

```sh
# for windows
flutter build windows
# for macos
flutter build macos
# for linux
flutter build linux
# for ios
flutter build ipa
# for android
flutter build apk
```

你也可以为 Android 平台构建 `aab` 等其他格式的应用包。但是对应签名素材请自行准备。