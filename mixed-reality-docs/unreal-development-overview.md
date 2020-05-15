---
title: Unreal 开发概述
description: 使用 Unreal Engine 4 进行混合现实开发概述
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 流式传输, 远程处理, 混合现实, 开发, 入门, 功能, 新项目, 仿真器, 文档, 指南, 功能, 全息影像
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851561"
---
# <a name="unreal-development-overview"></a>Unreal 开发概述

Unreal Engine 4 现完全支持针对 Windows 混合现实 (VR) 和 HoloLens 2 (AR) 设备进行开发！ 如果不熟悉 Unreal 开发，不妨浏览一下 <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Unreal Engine 4 入门</a>页面。 如果你需要资产，Unreal 有一个包罗万象的<a href="https://www.unrealengine.com/marketplace//store" target="_blank">市场</a>。 

掌握了 Unreal 开发的基本知识后，请参阅教程的下一节，了解如何在 HoloLens 上构建和运行应用。 若要与在 Unreal 中构建混合现实应用的社区人员交流心得，请务必访问 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 混合现实论坛</a>。 那里是一个求教解惑的好去处。

## <a name="tutorial"></a>教程

遵循我们的端到端教程，你可学习如何针对 HoloLens 2 [生成和部署一款简单的象棋应用](unreal-uxt-ch1.md)。 本教程使用 UX Tools 插件来加速开发包含交互式 UX 组件（包括按钮和操控器）的应用。 有关 UX Tools 插件的详细信息，请参阅下一节关于 MRTK 的内容。 

## <a name="mixed-reality-toolkit-for-unreal"></a>适用于 Unreal 的混合现实工具包

[适用于 Unreal 的混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unreal)是一组组件，包含插件、示例和文档，旨在加快使用 Unreal Engine 开发混合现实应用程序的速度。 作为此工具包的一部分，第一个发布的组件是[适用于 Unreal 的 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)，此插件可添加到 HoloLens 2 项目，为 HoloLens 2 应用程序提供 UX 功能。 可在相应的 GitHub 存储库中找到有关适用于 Unreal 的混合现实工具包和 UX Tools 的文档。 

## <a name="performance"></a>性能

HoloLens 2 应用必须以每秒 60 帧的速度运行，才能使全息影像稳定显示且快速响应。 若要在应用中实现此目的，强烈建议遵循我们[针对 Unreal 的性能建议](performance-recommendations-for-unreal.md)。 

## <a name="guides-to-specific-features"></a>特定功能指南

要了解如何使用 Unreal 中的特定功能，请查看以下指南： 
* [手部跟踪](unreal-hand-tracking.md)
* [眼动跟踪](unreal-gaze-input.md)
* [空间映射](unreal-spatial-mapping.md)
* [空间定位点](unreal-spatial-anchors.md)
* [语音输入](unreal-voice-input.md)
* [HoloLens 摄像头](unreal-hololens-camera.md)
* [QR 码](unreal-qr-codes.md)

## <a name="supported-features"></a>支持的功能

| HoloLens 2 功能 | 最早支持的 Unreal Engine 版本 |
| ----------- | ----------- |
| ARM64 支持 | 4.23 |
| 从电脑进行流式传输 | 4.23 |
| 空间映射 | 4.23 |
| 手动和联合跟踪 | 4.23 |
| 眼动跟踪 | 4.23 |
| 语音输入 | 4.23 |
| 空间定位点 | 4.23 |
| 摄像头访问 | 4.23 |
| QR 码 | 4.23 |
| 空间音频 | 4.23 |
| Spectator Screen 支持流式传输 | 4.24 |
| 通过流式传输的平面 LSR | 4.24 |
| 示例应用（[HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 和[任务 AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)） | 4.24 |
| 移动多视图：性能达到 60 fps | 4.25 |
| 第三人称摄像机渲染 | 4.25 |
| 从打包的桌面应用进行流式传输 | 4.25 |
| 面向 HoloLens 2 的 Azure 空间定位点 (beta) | 4.25 |
| OpenXR 支持 (beta) | 4.25 |
| UX Tools 支持 (0.8) | 4.25 |
| 开发人员文档和教程 | 4.25 |

## <a name="see-also"></a>另请参阅
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">关于流式传输、部署到仿真器和设备的 Unreal 文档</a>
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">移动设备的 Unreal 性能指南</a>
