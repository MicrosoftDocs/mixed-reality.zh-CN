---
title: Unity 开发概述
description: 在 Unity 中构建混合现实应用入门。
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合现实, 开发, 入门, 新项目, 移植, 功能, 相机, 模拟, 仿真, 文档
ms.openlocfilehash: e0fe775f5fe891416145d91e52a5a801e049c568
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "81433413"
---
# <a name="unity-development-overview"></a>Unity 开发概述

构建[混合现实应用](app-views.md)的最快途径是使用 [Unity](https://unity.com)。 建议你花一些时间浏览 [Unity 教程](https://unity3d.com/learn/tutorials)。 如果你需要资产，Unity 有一个包罗万象的[资产商店](https://www.assetstore.unity3d.com/)。 有了对 Unity 的基本了解以后，即可访问[教程](tutorials.md)，了解使用 Unity 进行混合现实开发的具体细节。 若要与社区的其他人员交流在 Unity 中构建混合现实应用的心得，以及查找可能遇到的问题的解决方案，请务必访问 [Unity 混合现实论坛](https://forum.unity3d.com/forums/hololens.102/)。

若要开始使用 Unity 构建混合现实应用，请先[安装工具](install-the-tools.md)。 

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>使用混合现实工具包新建 Unity 项目 

若要在 Unity 中进行开发，最简单的方法是使用混合现实工具包。 这样你就可以在项目中自动进行设置，并利用提供的一组混合现实功能来加快开发速度。 请查看[混合现实工具包 v2](mrtk-getting-started.md) 以了解详情并开始操作。 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>将现有的 Unity 应用移植到 Windows Mixed Reality

若要将现有的 Unity 项目移植到 Windows Mixed Reality，请按照 [Unity 移植指南](porting-guides.md)开始操作。

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>配置用于 Windows Mixed Reality 的全新 Unity 项目

若要在不导入混合现实工具包的情况下创建新的 Unity 项目，需针对 Windows Mixed Reality 手动更改一小组 Unity 设置。 这些设置分为两个类别：按项目设置和按场景设置。 请查看此文档，获取[为 Windows Mixed Reality 配置全新 Unity 项目](Configure-Unity-Project.md)的分步指南

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>添加混合现实功能和输入

在项目中设置 MRTK V2 或按上述说明配置项目以后，标准的 Unity 游戏对象（例如相机）就会立即启动，为你带来**坐定式体验**。当用户在空间中移动其头部时，相机的位置会自动进行更新。

可以使用直接内置到 Unity 中的 API，添加对 Windows Mixed Reality 功能（例如[空间舞台](coordinate-systems.md#spatial-coordinate-systems)、[手势、运动控制器](gestures-and-motion-controllers-in-unity.md)或[语音输入](voice-input-in-unity.md)）的支持。 

首先，请查看应用程序可能面对的[体验规模](coordinate-systems.md)：
* 若要构建**仅限方向的体验**或**坐定式体验**，需将 Unity 的跟踪空间类型设置为 [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 若要构建**站姿体验**或**房间规模的体验**，需确保将 Unity 的跟踪空间类型成功设置为 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 若要在 HoloLens 上构建**世界规模**的体验，让用户在 5 米之外漫游，需使用 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 组件。

混合现实应用程序的所有核心构建基块的公开方式与其他 Unity API 一致。 它们也可通过混合现实工具包获得。
* [摄像头](camera-in-unity.md)
* [坐标系统](coordinate-systems-in-unity.md)
* [凝视](gaze-in-unity.md)
* [手势和运动控制器](gestures-and-motion-controllers-in-unity.md)
* [语音输入](voice-input-in-unity.md)
* [持久性](persistence-in-unity.md)
* [空间音效](spatial-sound-in-unity.md)
* [空间映射](spatial-mapping-in-unity.md)

还有其他供许多混合现实应用程序使用的重要功能，这些功能也公开给 Unity 应用：
* [共享体验](shared-experiences-in-unity.md)
* [可定位相机](locatable-camera-in-unity.md)
* [焦点](focus-point-in-unity.md)
* [失跟](tracking-loss-in-unity.md)
* [键盘](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>在实际设备或模拟设备上运行 Unity 项目

准备好对全息 Unity 项目进行测试以后，下一步是[导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)。

有了该 VS 解决方案以后，即可使用真实的或模拟的设备通过下述三种方式之一运行应用程序：
* [部署到真实的 HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备](using-visual-studio.md)
* [部署到 HoloLens 仿真器](using-the-hololens-emulator.md)
* [部署到 Windows Mixed Reality 沉浸式头戴显示设备模拟器](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 文档

除了 docs.microsoft.com 上提供的此文档，Unity 还配置了适用于 Windows Mixed Reality 功能和 Unity 编辑器的文档。 Unity 提供的文档包括两个单独的部分：
1. **Unity 脚本参考**
    * 此部分文档包含 Unity 提供的脚本 API 的详细信息。
    * 可以在 Unity 编辑器中通过“帮助”>“脚本参考”进行访问 
2. **Unity 手册**
    * 此手册旨在介绍如何使用 Unity，既有基本技术，又有高级技术。
    * 可以在 Unity 编辑器中通过“帮助”>“手册”进行访问 

## <a name="see-also"></a>另请参阅
* [混合现实工具包 v2](mrtk-getting-started.md)
* [MR 基础知识 100：Unity 入门](holograms-100.md)
* [建议用于 Unity 的设置](recommended-settings-for-unity.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [将 Windows 命名空间与 Unity 应用配合用于 HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳做法](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 播放模式](unity-play-mode.md)
* [移植指南](porting-guides.md)
