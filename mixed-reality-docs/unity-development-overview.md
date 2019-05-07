---
title: Unity 开发概述
description: 获取开始的生成混合现实应用在 Unity 中。
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity 中，混合现实、 开发、 入门、 新的项目、 移植、 功能、 照相机、 模拟、 仿真、 文档
ms.openlocfilehash: 2cdcd5e997ab7e3f6d340377464e453a8e7c025c
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64874002"
---
# <a name="unity-development-overview"></a>Unity 开发概述

生成最快的途径[mixed 的 reality 应用](app-views.md)是与[Unity](http://aka.ms/HoloLensUnity)。 我们建议你花些时间浏览[Unity 教程](https://unity3d.com/learn/tutorials)。 如果你需要将资产，Unity 广[资产存储库](https://www.assetstore.unity3d.com/)。 一旦已建立的 Unity 一个基本的了解，您可以访问[教程](tutorials.md)若要了解使用 Unity 的混合的现实开发的详细信息。 请确保访问[Unity 混合现实论坛](http://forum.unity3d.com/forums/hololens.102/)与社区构建在 Unity 中的混合的现实应用的其余部分，并找到可能会遇到的问题的解决方案。


若要开始构建使用 Unity，混合的现实应用首先[安装的工具](install-the-tools.md)。 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>混合的现实工具包使用新的 Unity 项目 

在 Unity 中进行开发的最简单方法是混合现实工具包的帮助。 它将自动，可帮助安装程序项目，并提供一组的混合现实功能，从而加速开发。 请查看[混合现实 Toolkit v2](mrtk-getting-started.md)若要了解详细信息并开始。 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>移植到 Windows Mixed Reality 现有的 Unity 应用

如果有现有的 Unity 项目正在移植到 Windows Mixed Reality 的请按照[Unity 移植指南](porting-guides.md)若要开始。

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>为 Windows Mixed Reality 配置新的 Unity 项目

如果你想要创建新的 Unity 项目没有导入混合现实工具包，有少量的 Unity 设置，将需要手动更改 Windows Mixed Reality，划分为两个类别： 每个项目和每个场景。 有关分步指南请参阅此处[配置新 Unity 项目的 Windows Mixed Reality](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>添加混合的现实功能和输入

一旦项目后，已设置 MRTK V2 或配置你的项目，如上文所述，标准的 Unity 游戏对象 （如照相机） 将亮起立即用于**装规模体验**，具有更新的照相机的位置自动为用户将其头转到世界。

添加对 Windows Mixed Reality 功能的支持，如[空间阶段](coordinate-systems.md#spatial-coordinate-systems)，[手势、 运动控制器](gestures-and-motion-controllers-in-unity.md)或[语音输入](voice-input-in-unity.md)使用直接内置 Api 实现Unity。 

第一步应查看[体验刻度](coordinate-systems.md)可面向您的应用程序：
* 如果您要建立**方向限**或**固定缩放体验**，将需要设置 Unity 的跟踪到的空间类型[保持静止](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您要建立**现有规模**或**聊天室规模体验**，将需要确保 Unity 的跟踪空间类型已成功设置为[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您要建立**世界级**上 HoloLens，体验让用户超出 5 米漫游，您将需要使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)组件。

所有混合的现实应用程序的核心构建基块以与其他 Unity Api 一致的方式公开。 此外，还提供通过混合现实工具包。
* [摄像头](camera-in-unity.md)
* [坐标系统](coordinate-systems-in-unity.md)
* [凝视](gaze-in-unity.md)
* [手势和动作控制器](gestures-and-motion-controllers-in-unity.md)
* [语音输入](voice-input-in-unity.md)
* [暂留](persistence-in-unity.md)
* [空间音效](spatial-sound-in-unity.md)
* [空间映射](spatial-mapping-in-unity.md)

有，许多混合的现实应用程序将需要使用，这还公开到 Unity 应用其他主要功能：
* [共享的体验](shared-experiences-in-unity.md)
* [可定位相机](locatable-camera-in-unity.md)
* [焦点](focus-point-in-unity.md)
* [跟踪丢失](tracking-loss-in-unity.md)
* [键盘](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>在真实或模拟设备上运行你的 Unity 项目

一旦您购买了全息 Unity 项目准备好测试，在下一步是向[导出并构建 Unity 的 Visual Studio 的解决方案](exporting-and-building-a-unity-visual-studio-solution.md)。

掌握该 VS 解决方案，然后，可以运行您的应用程序中有三种方法，使用真实或模拟设备：
* [将部署到实际 HoloLens 或 Windows Mixed Reality 沉浸式头戴式耳机](using-visual-studio.md)
* [将部署到 HoloLens 仿真器](using-the-hololens-emulator.md)
* [将部署到 Windows Mixed Reality 沉浸式头戴式模拟器](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 文档

除了此文档可在 Windows 开发人员中心，Unity 将安装 Windows Mixed Reality 功能以及 Unity 编辑器中的文档。 Unity 提供文档包括两个单独的部分：
1. **Unity 脚本参考**
    * 文档的此部分包含 Unity 提供了脚本编写 API 的详细信息。
    * 可与 Unity 编辑器通过访问**帮助 > 脚本参考**
2. **Unity 手动**
    * 此手册旨在帮助您了解如何使用 Unity 中，从基本到高级方法。
    * 可与 Unity 编辑器通过访问**帮助 > 手动**

## <a name="see-also"></a>请参阅
* [混合现实 Toolkit v2](mrtk-getting-started.md)
* [MR 基础知识 100：Unity 入门](holograms-100.md)
* [建议用于 Unity 的设置](recommended-settings-for-unity.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [将 Windows 命名空间与 Unity 应用配合用于 HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳做法](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 播放模式](unity-play-mode.md)
* [移植指南](porting-guides.md)
