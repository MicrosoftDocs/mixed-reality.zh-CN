---
title: 在 Unity 中的照相机
description: 如何使用 Unity 的主照相机的 Windows Mixed Reality 开发进行全息呈现
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 全息呈现、 全息版的沉浸式，焦点、 深度缓冲区、 仅限方向、 位置、 不透明且透明的剪辑
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590150"
---
# <a name="camera-in-unity"></a>在 Unity 中的照相机

Wear 混合的现实耳机，它就成为 holographic 世界的中心。 Unity[照相机](http://docs.unity3d.com/Manual/class-Camera.html)组件将会自动处理立体呈现，随着将遵循磁头的移动和旋转时你的项目具有"虚拟现实受支持的"选择"Windows Mixed Reality"中的设备 （Windows 应用商店播放器设置的其他设置部分中）。 这可能被列为"Windows Holographic"中的 Unity 的较旧版本。

但是，为了全面优化视觉质量并[全息图稳定性](hologram-stability.md)，应设置如下所述的照相机设置。

>[!NOTE]
>这些设置需要应用于您的应用程序的每个场景中的照相机。
>
>默认情况下，在 Unity 中，创建新的场景时它将包含一个主相机 GameObject 包括照相机组件，但不具有正确应用下面的设置在层次结构中。

## <a name="holographic-vs-immersive-headsets"></a>与沉浸式耳机全息版

Unity 照相机组件上的默认设置适用于传统的三维应用程序需要类似于 skybox 的背景，因为没有现实世界的。
* 运行时**[沉浸式头戴式](immersive-headset-hardware-details.md)**、 呈现所有内容的用户会看到，并因此可能会希望保留 skybox。
* 但是，运行时**holographic 耳机**等[HoloLens](hololens-hardware-details.md)，实际应显示隐藏所有内容照相机呈现。 若要执行此操作，设置照相机背景是透明 （在 HoloLens，黑色将呈现为透明) 而不是 Skybox 纹理：
    1. 在层次结构面板中选择 Main Camera
    2. 在检查器窗格中，找到此照相机组件并将清除标志下拉列表中从 Skybox 更改为纯色
    3. 选择背景颜色选取器和 RGBA 值更改为 （0，0，0，0）

可以使用脚本代码来确定在运行时将耳机通过检查是否是沉浸式还是 holographic [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)。


## <a name="positioning-the-camera"></a>定位照相机

它将是用户的更轻松地布置您的应用程序，如果您想象的起始位置为 （x:0，Y:0，Z:0). 因为 Main Camera 正在跟踪的用户的头移动，可以通过设置 Main Camera 的起始位置设置用户的起始位置。
1. 在层次结构面板中选择 Main Camera
2. 在检查器窗格中，查找转换组件和更改数据的位置 （x:0，Y:1，z:-10） 到 （x:0，Y:0，Z:0)

   ![在 Unity 中的检查器窗格中的照相机](images/maincamera-350px.png)<br>
   *在 Unity 中的检查器窗格中的照相机*

## <a name="clip-planes"></a>剪辑平面

太接近呈现内容的用户可以是混合现实中令人不舒服。 您可以调整[近和远修剪平面](hologram-stability.md#hologram-render-distances)照相机组件上。
1. 在层次结构面板中选择 Main Camera
2. 在检查器窗格中，找到照相机组件中的剪辑平面并从 0.3 更改 Near 文本框中，为.85。 呈现甚至更接近内容可能会导致用户不适，应当避免每个[呈现距离准则](hologram-stability.md#hologram-render-distances)。

## <a name="multiple-cameras"></a>多个照相机

当场景中存在多个照相机组件时，Unity 知道要用于立体呈现的照相机，并且通过检查哪个 GameObject 头跟踪有 MainCamera 标记。

## <a name="recentering-a-seated-experience"></a>Recentering 关注的体验

如果您正在构建[装规模体验](coordinate-systems.md)，你可以通过调用用户的当前头位置处的自动 Unity 的世界原点**[XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。

## <a name="reprojection-modes"></a>Reprojection 模式

HoloLens 和沉浸式耳机将 reproject 您的应用程序呈现时发出 photons 调整用户的实际头位置的任何预测的每个帧。

默认情况下：

* **沉浸式耳机**将执行位置 reprojection，调整位置和方向，预测你全息，如果应用程序为给定的框架提供了深度缓冲区。  如果未提供深度缓冲区，系统将仅更正方向中的错误。
* **Holographic 耳机**如 HoloLens 将执行位置 reprojection 是否应用程序或不提供其深度缓冲区。  呈现通常会是稀疏具有稳定的背景提供的实际位置 reprojection 可能而无需在 HoloLens 上深度缓冲区。

如果您知道您构建[仅限方向的体验](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)严格锁定正文的内容 （例如 360 度视频内容），您可以显式设置 reprojection 模式仅通过设置为方向[HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)到[HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)。

## <a name="sharing-your-depth-buffers-with-windows"></a>与 Windows 共享深度缓冲区

你共享的每个帧将您的应用程序为一个提供两个提升全息图稳定性，根据耳机类型中的 Windows 应用的深度缓冲区的呈现：
* **沉浸式耳机**调整位置和方向的预测你全息提供深度缓冲区时可以执行位置 reprojection。
* **Holographic 耳机**例如，将自动选择 HoloLens[关注点](focus-point-in-unity.md)提供深度缓冲区时，优化全息图稳定性沿相交最内容的平面。

若要设置的 Unity 应用将向 Windows 提供深度缓冲区：
1. 转到**编辑** > **项目设置** > **播放机** > **通用 Windows 平台选项卡**  >  **XR 设置**。
2. 展开**Windows 混合现实 SDK**项。
3. 选中或取消选中**启用深度缓冲区共享**复选框。  默认情况下，对于已升级的较旧项目创建，因为此功能已添加到 Unity 并将取消选择的新项目中默认情况下将选中此项。

向 Windows 提供深度缓冲区可以提高视觉质量，只要 Windows 可以准确地映射深度缓冲区中的规范化的每个像素深度值回距离以米为单位，使用在 Unity 中设置主照相机的近和远平面。  如果您呈现器将传递的句柄的深度中的典型方法的值，您通常最好在这里，尽管半透明的呈现器将写传递给深度缓冲区时通过对现有的显示颜色像素可以混淆 reprojection。  如果您知道，呈现阶段将保留的最后一个深度像素许多不准确的深度值，您很可能获得更好的视觉质量，通过取消选中"启用深度缓冲区共享"。

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a>混合的现实工具包自动场景安装程序
当您导入[MRTK 发布 Unity 包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或从克隆项目[GitHub 存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，要在 Unity 中查找新菜单混合现实工具包。 在配置菜单中，你会看到菜单应用混合现实场景设置。 当您单击它时，它默认照相机中删除，并添加基础组件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，并[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。

![MRTK 场景设置菜单](images/MRTK_Input_Menu.png)<br>
*MRTK 场景设置菜单*

![自动场景中 MRTK 的安装程序](images/MRTK_HowTo_Input1.png)<br>
*自动场景中 MRTK 的安装程序*

## <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera 预设
您可以手动添加这些项目面板中。 您可以找到这些组件作为预设。 当您搜索**MixedRealityCamera**，你将能够看到两个不同的照相机预设。 其差异是， **MixedRealityCamera**才照相机 prefab 而**MixedRealityCameraParent**包括如 Teleportation，Motion 沉浸式耳机的其他组件控制器和，边界。

![在 MRTK 照相机预设](images/MRTK_HowTo_Input2.png)<br>
*在 MRTK 照相机预设*

**MixedRealtyCamera**支持 HoloLens 和沉浸式头戴式耳机。 它检测到的设备类型，并优化了清除标志和 Skybox 等属性。 可以在下面查找一些有用的属性可以自定义光标，Motion 控制器模型，如自定义和 Floor。

![游标和 Floor 运动控制器属性](images/MRTK_HowTo_Input3.png)<br>
*游标和 Floor 运动控制器属性*

## <a name="see-also"></a>请参阅
* [全息图稳定性](hologram-stability.md)
* [MixedRealityToolkit Main Camera.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
