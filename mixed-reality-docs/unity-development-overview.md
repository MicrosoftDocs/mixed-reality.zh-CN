---
title: Unity 开发概述
description: 获取开始的生成混合现实应用在 Unity 中。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity 中，混合现实、 开发、 入门、 新的项目、 移植、 功能、 照相机、 模拟、 仿真、 文档
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592957"
---
# <a name="unity-development-overview"></a>Unity 开发概述

生成最快的途径[mixed 的 reality 应用](app-views.md)是与[Unity](http://aka.ms/HoloLensUnity)。 我们建议你花些时间浏览[Unity 教程](https://unity3d.com/learn/tutorials)。 如果你需要将资产，Unity 广[资产存储库](https://www.assetstore.unity3d.com/)。 一旦已建立的 Unity 一个基本的了解，您可以访问[混合现实学院](academy.md)若要了解使用 Unity 的混合的现实开发的详细信息。 请确保访问[Unity 混合现实论坛](http://forum.unity3d.com/forums/hololens.102/)与社区构建在 Unity 中的混合的现实应用的其余部分，并找到可能会遇到的问题的解决方案。

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>移植到 Windows Mixed Reality 现有的 Unity 应用

如果有现有的 Unity 项目正在移植到 Windows Mixed Reality 的请按照[Unity 移植指南](porting-guides.md)若要开始。

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a>为 Windows Mixed Reality 配置新的 Unity 项目

若要开始构建使用 Unity，混合的现实应用首先[安装的工具](install-the-tools.md)。 如果你将面向 Windows Mixed Reality 沉浸式耳机而不是 HoloLens，将现在需要 Unity 的特殊版本。

如果只需创建新的 Unity 项目后，有少量的 Unity 设置，将需要更改 Windows Mixed Reality，划分为两个类别： 每个项目和每个场景。

### <a name="per-project-settings"></a>每个项目设置

若要针对 Windows Mixed Reality，首先需要设置你的 Unity 项目以导出为通用 Windows 平台应用：
1. 选择**文件 > 生成设置...**
2. 选择**通用 Windows 平台**在平台中列表，并单击**交换机平台**
3. 设置**SDK**到**通用 10**
4. 设置**目标设备**到**任一设备**以支持沉浸式耳机或切换到**HoloLens**
5. 设置**生成的类型**到**D3D**
6. 设置**UWP SDK**到**最新安装**

然后，我们需要让 Unity 知道我们尝试导出该应用应创建[沉浸式视图](app-views.md)而不是二维视图。 我们通过启用"虚拟现实支持"中执行的操作：
1. 从**生成设置...** 窗口中，打开**播放器设置...**
2. 选择**通用 Windows 平台的设置**选项卡
3. 展开**XR 设置**组
4. 在中**XR 设置**部分中，选择**受支持的虚拟现实**复选框以添加**虚拟现实设备**列表。
5. 在中**XR 设置**组中，确认 **"Windows Mixed Reality"** 被列为受支持的设备。 （这可能显示为"Windows Holographic"在较旧版本的 Unity）

您的应用程序现在可以执行基本全息呈现和空间的输入。 若要更进一步，充分利用特定功能，你的应用必须声明其清单中的相应功能。 可以在 Unity 中进行的清单的声明，以便将它们包括在每个后续项目导出。 该设置位于**播放器设置 > 通用 Windows 平台的设置 > 发布设置 > 功能**。 启用的常用的 Unity Api 的混合现实适用的功能包括：

|  功能  |  Api，需要功能 | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (访问权限[空间映射](spatial-mapping.md)网格上 HoloLens)&mdash;*所需的常规空间头戴式跟踪没有任何功能* | 
|  网络摄像头  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture 或 VideoCapture，分别 （时存储捕获的内容） | 
|  麦克风  |  VideoCapture （时捕获音频）、 DictationRecognizer、 GrammarRecognizer 和 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer （并使用 Unity Profiler） | 

**Unity 质量设置**

![Unity 质量设置](images/unityqualitysettings-350px.png)<br>
*Unity 质量设置*

HoloLens 有移动类 GPU。 如果您的应用程序面向 HoloLens，则需要针对最快的性能优化的质量设置以确保我们保持完整的帧速率：
1. 选择**编辑 > 项目设置 > 质量**
2. 选择**下拉列表中**下**Windows 应用商店**徽标，然后选择**Fastest**。 您将知道当正确应用了设置 Windows 应用商店列中的框并**Fastest**行都显示为绿色。

### <a name="per-scene-settings"></a>每个场景设置

**Unity 照相机设置**

![Unity 照相机设置](images/unitycamerasettings.png)<br>
*Unity 照相机设置*

可以在"虚拟现实支持"复选框，一旦[Unity 照相机](camera-in-unity.md)组件句柄[头跟踪和立体呈现](rendering.md)。 没有无需将其替换为自定义在相机上以执行此操作。

如果您的应用程序专门面向 HoloLens，有几个需要更改以使您的应用程序将通过显示物理世界的设备的透明显示优化的设置：
1. 在中**层次结构**，选择**Main Camera**
2. 在**Inspector**面板中，将转换**位置**到**0，0，0**以便用户头位置始于 Unity 世界原点。
3. 更改**清除标志**到**纯色**。
4. 更改**背景**颜色**RGBA 0,0,0,0**。 黑色将呈现为透明的 HoloLens。
5. 更改**剪裁平面的附近**到[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 （米）。

如果你删除并创建一个新的照相机，请确保您的照相机**标记**作为**MainCamera**。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>添加混合的现实功能和输入

一旦您已配置你的项目，如上文所述，标准 Unity 游戏对象 （如照相机） 将亮起立即用于**固定缩放体验**，使用自动更新以用户身份的照相机的位置将移动通过世界其头。

添加对 Windows Mixed Reality 功能的支持，如[空间阶段](coordinate-systems.md#spatial-coordinate-systems)，[手势、 运动控制器](gestures-and-motion-controllers-in-unity.md)或[语音输入](voice-input-in-unity.md)使用直接内置 Api 实现Unity。

第一步应查看[体验刻度](coordinate-systems.md)可面向您的应用程序：
* 如果您要建立**方向限**或**固定缩放体验**，将需要设置 Unity 的跟踪到的空间类型[保持静止](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您要建立**现有规模**或**聊天室规模体验**，将需要确保 Unity 的跟踪空间类型已成功设置为[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。
* 如果您要建立**世界级**上 HoloLens，体验让用户超出 5 米漫游，您将需要使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)组件。

中与其他 Unity Api 一致的方式公开所有混合的现实应用程序的核心构建基块：
* [摄像头](camera-in-unity.md)
* [坐标系统](coordinate-systems-in-unity.md)
* [Gaze](gaze-in-unity.md)
* [手势和动作控制器](gestures-and-motion-controllers-in-unity.md)
* [语音输入](voice-input-in-unity.md)
* [暂留](persistence-in-unity.md)
* [空间声音](spatial-sound-in-unity.md)
* [空间映射](spatial-mapping-in-unity.md)

有，许多混合的现实应用程序将需要使用，这还公开到 Unity 应用其他主要功能：
* [共享的体验](shared-experiences-in-unity.md)
* [可定位照相机](locatable-camera-in-unity.md)
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
* [MR 基础知识 100:开始使用 Unity](holograms-100.md)
* [Unity 的推荐的设置](recommended-settings-for-unity.md)
* [Unity 的性能建议](performance-recommendations-for-unity.md)
* [导出和构建 Unity 的 Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [适用于 Unity 应用的 Windows 命名空间用于 HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳实践](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 游戏模式](unity-play-mode.md)
* [移植指南](porting-guides.md)
