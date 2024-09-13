---
title: 优化 macOS Stage Manager 开启后新开窗口后屏幕左侧有空隙的问题
date: 2024-09-13 20:39:29
subtitle: 
categories: macOS
tags:
  - macOS
cover: file-20240913142421625.jpg
description: 开启 Stage Manager 后，即使 Show recent apps in Stage Manager 关闭，新建应用全屏窗口后，屏幕左侧仍然存在很小的间隙，可以使用这行命令进行关闭。
---
macOS 中的 Stage Manager 提供了一种高效的窗口管理方式，使用户能够轻松组织和切换应用程序窗口。然而，当开启 Stage Manager 功能后，即使关闭了"Show recent apps in Stage Manager"选项，新创建的最大化应用窗口仍会在屏幕左侧留下一个小间隙。这篇文章将介绍如何通过命令行工具来彻底消除该间隙，从而优化应用程序窗口最大化的体验。
<!--more-->
## 问题描述

在启用 Stage Manager 后，即使关闭了显示最近使用应用的选项，新创建的最大化应用窗口仍会在屏幕左侧留有一个细小的间隙。如下图所示：
![Stage Manager 左侧间隙](file-20240913142548293.jpg)


## 解决方案

可以通过在终端中输入特定的命令来关闭这个多余的间隙，该命令通过更改系统设置来实现。

### 一、打开终端

首先，需要打开终端应用程序。可以通过以下几种方式打开终端：

- 使用 Spotlight 搜索：按下 `Command + Space`，输入 "Terminal"，然后按下 `Return` 键。
- 通过 Finder：前往 `Applications > Utilities > Terminal`。

### 二、输入命令

在终端中输入以下命令，并按下 `Return` 键：

```bash
defaults write com.apple.WindowManager StageFrameMinimumHorizontalInset -int 0
```

> 最后的 0 可以调整为 [-2147483647...2147483647] 之间的任意整数
### 三、重启 Stage Manager 或者重启电脑

输入完成后，可能需要重启 Stage Manager 或者重启电脑以使更改生效。

> 不过我这边是即时生效的。

## 效果验证

执行上述命令并重启系统或 Stage Manager 后，新创建的最大化应用窗口将不会再在屏幕左侧留下间隙。如下图所示：
![新建最大化窗口无间隙效果](file-20240913142622260.jpg)

