---
title: Unity 开发概述
description: 在 Unity 中构建混合现实应用入门。
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目，移植，功能，照相机，模拟，仿真，文档
ms.openlocfilehash: f9b314bfc7c58e72b11ecfd76fe7293ef2f6c11e
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926698"
---
# <a name="unity-development-overview"></a>Unity 开发概述

构建[混合现实应用](app-views.md)的最快途径是使用[Unity](https://unity.com)。 建议你花时间浏览[Unity 教程](https://unity3d.com/learn/tutorials)。 如果需要资产，Unity 有一个全面的[资产存储区](https://www.assetstore.unity3d.com/)。 构建基本的 Unity 理解后，可以访问这些[教程](tutorials.md)，了解使用 unity 进行混合现实开发的细节。 请务必访问[Unity 混合现实论坛](https://forum.unity3d.com/forums/hololens.102/)，与在 Unity 中构建混合现实应用的其他社区合作，查找可能遇到的问题的解决方案。

若要开始通过 Unity 构建混合现实应用，请先[安装这些工具](install-the-tools.md)。 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>带有混合现实工具包的新 Unity 项目 

在 Unity 中开发的最简单方法是利用混合现实工具包。 这将帮助您自动设置该项目，并提供一组混合现实功能以加速开发。 请查看[混合现实工具包 v2](mrtk-getting-started.md)以了解详细信息并开始。 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>将现有 Unity 应用移植到 Windows Mixed Reality

如果你有要移植到 Windows Mixed Reality 的现有 Unity 项目，请按照[Unity 迁移指南](porting-guides.md)中的步骤开始操作。

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>为 Windows Mixed Reality 配置新的 Unity 项目

如果要在不导入混合现实工具包的情况下创建新的 Unity 项目，则需要为 Windows Mixed Reality 手动更改的一小组 Unity 设置。 这些分类分为两类：每个项目和每场景。 有关为[Windows Mixed Reality 配置新 Unity 项目](Configure-Unity-Project.md)的分步指导，请参阅此处。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>添加混合现实功能和输入

设置 MRTK V2 与你的项目或配置项目（如上所述）后，标准 Unity 游戏对象（如相机）会立即为**固定规模的体验**亮起，照相机的位置会自动更新为用户将其头部移到世界各地。

添加对 Windows Mixed Reality 功能的支持，例如[空间阶段](coordinate-systems.md#spatial-coordinate-systems)、[手势、动作控制器](gestures-and-motion-controllers-in-unity.md)或[语音输入](voice-input-in-unity.md)，使用直接内置于 Unity 的 api 实现。 

首先，请查看应用程序可以面向的[体验规模](coordinate-systems.md)：
* 如果希望构建**仅限方向**或**固定规模的体验**，则需要将 Unity 的跟踪空间类型设置为 "[静态](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)"。
* 如果希望构建**大规模**或**房间规模的体验**，则需要确保 Unity 的跟踪空间类型已成功设置为[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果你希望在 HoloLens 上构建可让用户漫游超过5米的**全球规模**体验，则需要使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)组件。

混合现实应用程序的所有核心构建基块的公开方式与其他 Unity Api 一致。 它们还可通过混合现实工具包获得。
* [摄像头](camera-in-unity.md)
* [坐标系统](coordinate-systems-in-unity.md)
* [凝视](gaze-in-unity.md)
* [手势和运动控制器](gestures-and-motion-controllers-in-unity.md)
* [语音输入](voice-input-in-unity.md)
* [保持](persistence-in-unity.md)
* [空间音效](spatial-sound-in-unity.md)
* [空间映射](spatial-mapping-in-unity.md)

许多混合现实应用程序还需要使用其他重要功能，这些功能也会公开给 Unity 应用：
* [共享体验](shared-experiences-in-unity.md)
* [可定位相机](locatable-camera-in-unity.md)
* [焦点](focus-point-in-unity.md)
* [跟踪丢失](tracking-loss-in-unity.md)
* [键盘](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>在实际或模拟设备上运行 Unity 项目

完成全息 Unity 项目以进行测试后，下一步就是[导出并构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)。

使用该 VS 解决方案，可以通过以下三种方式之一运行应用程序：使用实设备或模拟设备：
* [部署到真实的 HoloLens 或 Windows Mixed Reality 沉浸式耳机](using-visual-studio.md)
* [部署到 HoloLens 模拟器](using-the-hololens-emulator.md)
* [部署到 Windows Mixed Reality 沉浸式耳机模拟器](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 文档

除了 docs.microsoft.com 上提供的此文档，Unity 还随 Unity 编辑器一起安装 Windows Mixed Reality 功能的文档。 Unity 提供的文档包括两个单独的部分：
1. **Unity 脚本参考**
    * 文档的本节包含 Unity 提供的脚本编写 API 的详细信息。
    * 可以通过 "**帮助" > 脚本参考来**访问 Unity 编辑器
2. **Unity 手册**
    * 本手册旨在帮助你了解如何使用 Unity，从基本到高级的技术。
    * 可从 Unity 编辑器通过**Help > 手动**访问

## <a name="see-also"></a>另请参阅
* [混合现实工具包 v2](mrtk-getting-started.md)
* [MR 要点100： Unity 入门](holograms-100.md)
* [建议用于 Unity 的设置](recommended-settings-for-unity.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [将 Windows 命名空间与 Unity 应用配合用于 HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳做法](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 播放模式](unity-play-mode.md)
* [移植指南](porting-guides.md)
