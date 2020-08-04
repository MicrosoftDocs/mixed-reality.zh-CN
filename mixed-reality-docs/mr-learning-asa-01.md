---
title: Azure 空间定位点教程 - 1. 简介
description: 完成本课程可以了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: f273c573d40b1e65e325bd31b5dd9e14c1ee66ec
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376549"
---
# <a name="1-introduction"></a>1.简介

## <a name="overview"></a>概述

欢迎学习 Azure 空间定位点教程！ 通过本系列教程，你将了解 <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure 空间定位点</a>的基础知识，学习如何在真实世界中创建定位空间的混合现实体验。 你还将了解如何将项目部署到 Android 和 iOS。

本系列教程：

1. [简介](mr-learning-asa-01.md)
2. [Azure 空间定位点入门](mr-learning-asa-02.md)
3. [保存、检索和共享 Azure 空间定位点](mr-learning-asa-03.md)
4. [显示 Azure 空间定位点反馈](mr-learning-asa-04.md)
5. [适用于 Android 和 iOS 的 Azure 空间定位点](mr-learning-asa-05.md)

## <a name="objectives"></a>目标

* 了解如何创建空间定位点并从 Azure 中获取它们
* 了解如何在应用会话之间实现空间对齐
* 了解如何在多台设备之间实现空间对齐
* 了解如何准备、生成项目并将其部署到 Android 和 iOS 上

## <a name="prerequisites"></a>先决条件

* 一台 Windows 10 计算机，其中已[安装](install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一台[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 并添加了通用 Windows 平台生成支持模块
* 已完成[创建空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分（位于[快速入门：创建使用 Azure 空间定位点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程中）
* 已完成[入门教程](mr-learning-base-01.md)系列，或者之前有一些使用 Unity 和 MRTK 的基本经验
* 已完成 [Azure 空间定位点教程](mr-learning-asa-01.md)系列，或者之前有创建 Azure 空间定位点帐户的经验
* 如果打算部署到 Android 和 HoloLens
  * <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">开发人员实现</a>且<a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">支持 ARCore</a>的 Android 设备，该设备通过 USB 与 Windows 或 macOS 计算机相连接
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 且已添加 Android 生成支持模块
* 如果打算部署到 iOS 和 HoloLens
  * 一台已安装最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 计算机
  * <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">与 ARKit 兼容</a>且通过 USB 连接到 macOS 计算机的 iOS 设备
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 且已添加 iOS 生成支持模块

> [!CAUTION]
> 建议对本系列教程使用混合现实工具包版本 MRTK 2.4.0。

> [!CAUTION]
> 建议对本系列教程使用 Unity 2019.3.15。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求。

[下一教程：2.开始使用 Azure 空间定位点](mr-learning-asa-02.md)
