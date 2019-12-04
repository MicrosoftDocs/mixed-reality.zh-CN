---
title: 旁观视图
description: 在外部设备中将全息影像可视化，通过这种方式在外部显示器上演示混合现实体验，或者录制混合现实体验的视频。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 旁观视图, iPhone, iOS, iPad, OpenCV, 相机, ARKit, HoloLens, 混合现实, MixedRealityToolkit, 演示, 录制
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491161"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens 和 HoloLens 2 的旁观视图

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>概述

戴上 HoloLens 时，我们通常会忘记这样一件事：没有戴上它的人无法体验到我们所能体验到的神奇感受。 旁观视图可以让他人在 2D 屏幕上观看 HoloLens 用户在其世界中看到的东西。
有了旁观视图，就可以通过快速且经济的方式在移动设备中录制高清全息影像。 有了它，还可以通过摄像机对全息影像进行专业质量的录制。

## <a name="key-resources"></a>重要资源

* [**GitHub 上的旁观视图**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**旁观视图文档**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**旁观视图示例**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>用例
* 可以使用 iPhone 或 Android 设备录制混合现实体验。 以全高清进行录制，对全息影像甚至阴影应用抗锯齿效果。 这样可以经济高效且快速地捕获全息影像的视频。
* 将实时混合现实体验直接从 iPhone 或 iPad 流式传输到 Apple TV，没有任何延迟！
* 与来宾共享此体验：让非 HoloLens 用户直接在其手机或平板电脑上体验全息影像。

## <a name="current-features"></a>当前功能

* 对全息影像进行空间同步，使每个人都能在完全相同的位置观看全息影像。
* iOS（支持 ARKit 的设备）和 Android（支持 ARCore 的设备）支持。
多个 iOS 来宾。
录制视频 + 全息影像 + 环境音效 + 全息音效。
共享表，用于保存视频、通过电子邮件发送视频或将其与其他支持应用共享。

![标记](images/SpecViewPhoneDemo.jpg)
![标记](images/hololensspectatorview-500px.jpg) ![标记](images/spectatorview-300px.png)

下表显示了不同的旁观视图功能。 请选择最符合你的视频录制需求的选项：

|                                      | 移动版                  |                    摄像机              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| 高清质量                           |         全高清         |        专业质量摄影（取决于摄像机）      |
| 相机移动轻松                 |            ✔            |                      ✔                      |
| 第三人称视图                    |            ✔            |                      ✔                      |
| 可以流式传输到屏幕           |            ✔            |                      ✔                      |
| 可移植                             |            ✔            |                                             |
| 无线                             |            ✔            |                                             |
| 其他必需硬件         |     Android 手机、iPhone    | HoloLens + 支架 + 三脚架 + 摄像机 + 电脑 + Unity |
| 硬件投资                  |           低            |                     高                    |
| 跨平台                       |           Android、iOS   |                                             |
| 同步的内容                 |            ✔            |                      ✔                      |
| 运行时设置持续时间               |         即时          |                     慢                    |
## <a name="see-also"></a>另请参阅

* [混合现实捕获](mixed-reality-capture.md) 
* [面向开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)
* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
