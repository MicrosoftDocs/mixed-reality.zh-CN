---
title: Unreal 开发概述
description: 使用 Unreal Engine 4 进行混合现实开发概述
author: hferrone
ms.author: v-haferr
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 流式传输, 远程处理, 混合现实, 开发, 入门, 功能, 新项目, 仿真器, 文档, 指南, 功能, 全息影像, 游戏开发
ms.openlocfilehash: ecf982eb5d8128734c862bac2d8be29c1554edfe
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303618"
---
# <a name="unreal-development-overview"></a>Unreal 开发概述

开始使用<a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="混合现实文档">混合现实应用程序</a>是一个重大任务。 新概念、平台和前沿硬件看似都障碍重重。 但是，如果你是 Unreal 的开发人员，那么你很幸运。 对 <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality 文档">Windows Mixed Reality</a> (VR) 和 <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2 文档">HoloLens 2</a> (AR) 的支持现已包含在 Unreal Engine 的最新 <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 发行说明">版本</a>中。 此更新包括：
* 混合现实 UX Tools 插件支持
* OpenXR 支持
* 桌面应用中的应用远程处理
* 更好的性能
* 混合现实捕获
* 对 Azure 空间定位点的初始支持

如果你不熟悉 Unreal 开发，请勿直接跳转。 探索 Unreal <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">教程系列</a>，以快速了解和查找 Unreal <a href="https://www.unrealengine.com/marketplace/store" target="_blank">市场</a>和混合现实<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">论坛</a>中的资产和支持。 这些资源是指向当今混合现实市场中的构建者和问题解决者的社区的链接。

## <a name="mixed-reality-toolkit-for-unreal"></a>适用于 Unreal 的混合现实工具包

[适用于 Unreal 的混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unreal)是一组设计用于在 Unreal 中加快开发速度的组件。 每个组件都包含用于设置沉浸式体验的插件、示例和文档。 

[适用于 Unreal 的 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) 是第一个要发布的组件，目前仅在 HoloLens 2 上受支持。 组件插件包括常见 UX 功能的代码、蓝图和示例资产，包括：
* 输入模拟
* 手势交互 Actor
* 可按按钮组件
* 操控器组件
* 跟踪行为组件

有关功能的详细信息和设置项目的信息，可以深入了解[适用于 Unreal 的 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) GitHub 存储库。

## <a name="hololens-2-platform-support"></a>HoloLens 2 平台支持
如果这是你第一次为 HoloLens 创建或部署 Unreal 应用，则需要从 Epic Launcher [下载支持平台支持文件](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。

## <a name="tutorial"></a>教程

亲自进行构建是学习新技能的最佳方式。 了解如何为具有 UX Tools 插件的 HoloLens 2 [生成和部署简单的象棋应用](unreal-uxt-ch1.md)是一个良好的开端。 

本端到端教程系列提供常见交互式 UX 组件和方案的动手实践。 你将完成项目设置，即，将交互添加到场景，并部署到设备或模拟器。 只需 Windows 10、模拟器和 Visual Studio 2019 即可。

## <a name="debugging"></a>调试

若要使用 Visual Studio 调试在 HoloLens 2 上运行的应用，请按照此处针对[调试远程设备上安装的 UWP 应用](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package?view=vs-2019#remote)的说明操作。

## <a name="performance"></a>性能

混合现实开发附带依赖于平台的性能检查点。 HoloLens 2 应用必须以每秒 60 帧的速度运行，才能使全息影像稳定显示且快速响应。 幸运的是，我们提供了有关在 Unreal 应用程序中实现这种效果的[性能建议](performance-recommendations-for-unreal.md)。

## <a name="guides-to-specific-features"></a>特定功能指南

有几项混合现实开发的重要功能在教程系列中未涉及。 有关详细信息和实际运用，请参阅以下指南： 
* [眼动跟踪](unreal-gaze-input.md)
* [手部跟踪](unreal-hand-tracking.md)
* [HoloLens 摄像头](unreal-hololens-camera.md)
* [空间定位点](unreal-spatial-anchors.md)
* [空间映射](unreal-spatial-mapping.md)
* [空间音频](unreal-spatial-audio.md)
* [流式处理](unreal-streaming.md)
* [语音输入](unreal-voice-input.md)
* [QR 码](unreal-qr-codes.md)
* [性能建议](performance-recommendations-for-unreal.md)

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
| 示例应用（[HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 和[任务 AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)） | 4.24 |
| 移动多视图：性能达到 60 fps | 4.25 |
| 第三人称摄像机渲染 | 4.25 |
| 从打包的桌面应用进行流式传输 | 4.25.1 |
| 面向 HoloLens 2 的 Azure 空间定位点 (beta) | 4.25 |
| OpenXR 支持 (beta) | 4.25 |
| UX Tools 支持 (0.8) | 4.25 |
| 开发人员文档和教程 | 4.25 |

## <a name="see-also"></a>另请参阅
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">关于流式传输、部署到仿真器和设备的 Unreal 文档</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">移动设备的 Unreal 性能指南</a>
