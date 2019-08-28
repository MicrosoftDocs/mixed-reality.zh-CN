---
title: Spectator 视图
description: 从外部设备中可视化全息影像, 这是一种演示混合现实体验中的混合现实体验的方式。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, 摄像, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, demo, 记录
ms.openlocfilehash: 708ed694af3769f16d5dce0595e026f9a348d754
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047177"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens 和 HoloLens 2 的 Spectator 视图

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>概述

在戴上 HoloLens 时, 我们经常忘记, 没有 it 人员的人不能绑住。 Spectator 视图允许其他人在二维屏幕上看到一个 HoloLens 用户在其世界中看到的内容。
Spectator 视图提供了一种快速且经济实惠的方法, 用于通过移动设备录制高清影像。 它还通过视频相机提供一种专业的影像质量记录。

## <a name="key-resources"></a>关键资源

* [**GitHub 上的 Spectator 视图**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Spectator 视图文档**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Spectator 视图示例**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>用例
* 可以使用 iPhone 或 Android 设备记录混合现实体验。 以完整 HD 记录, 并将抗锯齿应用于全息影像甚至阴影。 这是一种经济高效的方法, 可用于捕获影像的视频。
* 直接从 iPhone 或 iPad, 将实时混合现实体验流式处理到 Apple TV 中, 无滞后!
* 与来宾分享体验:让非 HoloLens 用户直接从手机或平板电脑体验全息影像。

## <a name="current-features"></a>当前功能

* 全息影像的空间同步, 因此所有人都能在完全相同的位置看到全息影像。
* iOS (启用 ARKit 的设备) 和 Android (启用 ARCore 的设备) 支持。
多个 iOS 来宾。
视频 + 全息影像 + 环境音效 + 全息影像声音。
共享工作表, 以便您可以保存视频、向其发送电子邮件或与其他支持应用共享。

![](images/SpecViewPhoneDemo.jpg)
标记标记](images/hololensspectatorview-500px.jpg) ![ ![](images/spectatorview-300px.png)

下表显示了不同的 Spectator 视图功能及其功能。 选择最适合您的视频录制需求的选项:

|                                      | 移动电话                  |                    视频摄像机              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 质量                           |         完整高清         |        专业质量与 (由视频相机确定)      |
| 轻松移动相机                 |            ✔            |                      ✔                      |
| 第三人员视图                    |            ✔            |                      ✔                      |
| 可以流式传输到屏幕           |            ✔            |                      ✔                      |
| 可移植                             |            ✔            |                                             |
| 无线                             |            ✔            |                                             |
| 其他必需硬件         |     Android 手机, iPhone    | HoloLens + Rig + "装备 + 视频相机 + PC + Unity" |
| 硬件投资                  |           低            |                     高                    |
| 跨平台                       |           Android、iOS   |                                             |
| 同步内容                 |            ✔            |                      ✔                      |
| 运行时安装持续时间               |         速递          |                     慢速                    |
## <a name="see-also"></a>请参阅

* [混合现实捕获](mixed-reality-capture.md) 
* [面向开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)
* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
