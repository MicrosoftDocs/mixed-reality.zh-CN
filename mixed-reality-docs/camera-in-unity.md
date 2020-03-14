---
title: Unity 中的照相机
description: 如何使用 Unity 用于 Windows Mixed Reality 开发的主照相机进行全息渲染
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，全息呈现，全息，沉浸式，聚焦点，深度缓冲区，仅限方向，位置，不透明，透明，剪辑
ms.openlocfilehash: 1a2e66d5c028109a58ea8682668521f50158add9
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375584"
---
# <a name="camera-in-unity"></a>Unity 中的照相机

当你磨损混合现实耳机时，它将成为你的全息世界的中心。 如果你的项目将 "Windows Mixed Reality" 选择为 "受支持的虚拟现实" 作为设备（在 Windows 应用商店播放机设置的 "其他设置" 部分），则 Unity[相机](https://docs.unity3d.com/Manual/class-Camera.html)组件会自动处理 stereoscopic 渲染，并遵循打印头运动和旋转。 在较旧版本的 Unity 中，这可能作为 "Windows 全息" 列出。

但是，若要完全优化视觉质量和[全息图稳定性](hologram-stability.md)，应设置以下描述的相机设置。

>[!NOTE]
>需要在应用的每个场景中将这些设置应用到相机。
>
>默认情况下，当你在 Unity 中创建新场景时，它将包含层次结构中的一个主相机 GameObject，其中包括相机组件，但未正确应用下面的设置。

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a>带有混合现实工具包 v2 的自动场景和照相机设置

按照将混合现实工具包 v2 添加到 Unity[项目中的分步指南操作](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)，它将自动配置你的项目。

你还可以通过以下部分中的指南手动配置项目，而无需 MRTK。

## <a name="holographic-vs-immersive-headsets"></a>全息和沉浸式耳机

Unity 相机组件上的默认设置适用于需要 skybox 的背景的传统3D 应用程序，因为这些应用程序不是真实的。

* 在 **[沉浸式头戴式耳机](immersive-headset-hardware-details.md)** 上运行时，会呈现用户看到的所有内容，因此你可能需要保留 skybox。
* 但是，当在**全息耳机**（如[HoloLens](hololens-hardware-details.md)）上运行时，真实环境应显示在照相机呈现的所有内容之后。 为此，请将相机背景设置为透明（在 HoloLens、黑色呈现为透明）而不是 Skybox 纹理：
    1. 选择 "层次结构" 面板中的主相机
    2. 在 "检查器" 面板中，找到照相机组件，并将 "清除标志" 下拉列表从 "Skybox" 更改为纯色
    3. 选择背景色选取器并将 RGBA 值更改为（0，0，0，0）

您可以使用脚本代码，通过检查[HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)来确定头戴式耳机是沉浸还是全息。

## <a name="positioning-the-camera"></a>定位照相机

如果将用户的起始位置想像为（X：0，Y：0，Z：0），则可以更轻松地对应用进行布局。 由于摄像机正在跟踪用户的头移动，因此可以通过设置主摄像机的开始位置来设置用户的起始位置。

1. 选择 "层次结构" 面板中的 "主相机"
2. 在检查器面板中，找到转换组件，并将位置（X：0，Y：1，Z：-10）更改为（X：0，Y：0，Z：0）

   Unity](images/maincamera-350px.png) 中的 "检查器" 窗格中的 ![照相机  
   *Unity 中的 "检查器" 窗格中的照相机*

## <a name="clip-planes"></a>剪辑平面

在混合现实中，向用户呈现的内容太接近。 可以在相机组件上调整[近和远的剪辑平面](hologram-stability.md#hologram-render-distances)。

1. 选择 "层次结构" 面板中的主相机
2. 在 "检查器" 面板中，找到 "照相机" 组件剪辑平面，并将 "Near" 文本框从0.3 更改为85。 呈现更近的内容可能导致用户 discomfort，应根据[渲染距离准则](hologram-stability.md#hologram-render-distances)加以避免。

## <a name="multiple-cameras"></a>多个照相机

如果场景中有多个照相机组件，则通过检查哪些 GameObject 具有 MainCamera 标记，Unity 知道哪个照相机要用于 stereoscopic 渲染和打印头跟踪。

## <a name="recentering-a-seated-experience"></a>Recentering 体验

如果要构建大规模的[体验](coordinate-systems.md)，可以通过调用 XR，在用户的当前头部位置 recenter Unity 的世界原点 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。

## <a name="reprojection-modes"></a>Reprojection 模式

HoloLens 和沉浸式耳机都将 reproject 你的应用程序呈现的每个帧，以便在发出 photons 时，对用户实际头位置的任何 misprediction 进行调整。

默认情况下：

* **沉浸式耳机**将执行位置 reprojection，如果应用为给定帧提供深度缓冲区，则在位置和方向调整你的全息影像。  如果未提供深度缓冲区，则系统只会方向上的 mispredictions。
* 如果应用程序提供了深度缓冲区，就像 HoloLens 这样的**全息耳机**会执行位置 reprojection。  在不使用 HoloLens 上的深度缓冲区的情况下，可能会出现位置 reprojection，因为呈现通常是由真实世界提供的稳定背景稀疏的。

如果你知道要使用严格的正文锁定内容（例如，360度视频内容）构建[仅限方向的体验](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)，则可以通过将[ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)设置为[HolographicReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)，将 reprojection 模式显式设置为 "方向"。

## <a name="sharing-your-depth-buffers-with-windows"></a>与 Windows 共享你的深度缓冲区

将应用的深度缓冲区共享到 Windows 每个框架都将根据要呈现的耳机类型为应用程序提供以下两个增强功能之一：

* 当提供了深度缓冲区时，**沉浸式耳机**可以执行位置 reprojection，同时调整 misprediction 在位置和方向上的影像。
* **全息耳机**具有几种不同的方法。 当提供了深度缓冲区时，HoloLens 1 将自动选择[焦点](focus-point-in-unity.md)，同时优化与最大内容相交的平面上的全息图稳定性。 HoloLens 2 将使用[深度 LSR （请参阅备注）](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)稳定内容。

设置 Unity 应用是否将向 Windows 提供深度缓冲区：

1. 请参阅**编辑** > **项目设置** > **Player** > **通用 Windows 平台选项卡** > **XR 设置**。
2. 展开 " **Windows Mixed REALITY SDK** " 项。
3. 选中或取消选中 "**启用深度缓冲共享**" 复选框。  默认情况下，在新创建的项目中将选中此功能，因为此功能已添加到 Unity，并且默认情况下将为升级的旧项目取消选中。

向 Windows 提供深度缓冲区可以提高视觉质量，只要 Windows 可以使用在主摄像机上的 Unity 中已设置的近和远的平面，将深度缓冲区中的规范化的每像素深度值准确地映射回米的距离。  如果您的呈现器通过使用典型的方式来处理深度值，则通常情况下，您应该非常好，但是，在显示到现有颜色像素时，写入深度缓冲区的半透明渲染传递可能会混淆 reprojection。  如果你知道，你的 render pass 会使很多最终深度像素具有不准确的深度值，则你可能会通过取消选中 "启用深度缓冲区共享" 获得更好的视觉质量。

## <a name="see-also"></a>另请参阅

* [全息影像稳定性](hologram-stability.md)
* [MixedRealityToolkit prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
