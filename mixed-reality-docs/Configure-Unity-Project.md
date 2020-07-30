---
title: 为 Windows Mixed Reality 配置新的 Unity 项目
description: 有关为 Windows Mixed Reality 配置 Unity 项目的说明
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目
ms.openlocfilehash: 64f7006bf212f49ab1c478d5dbb1fc1f5ab15497
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390095"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>为 Windows Mixed Reality 配置新的 Unity 项目 

## <a name="overview"></a>概述

Windows Mixed Reality （WMR）是作为 Windows 10 操作系统的一部分引入的 Microsoft 平台。 WMR 平台使你能够生成在全息和 VR 显示设备上呈现数字内容的应用程序。

设置 WMR 时，可以采用两个路径。 第一种方法是安装[混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)（MRTK） v2，这将自动设置 WMR 环境。 第二种方法是手动更改一些 Unity 设置以使用 WMR 进行滚动。 

> [!NOTE]
> 你始终可以在以后导入 MRTK，因此，不会产生要首先进行手动路由的损失。

如果选择 WMR 手动设置，则需要更改的设置将分为两个类别：每个项目和每场景。

## <a name="per-project-settings"></a>每个项目的设置

需要为 WMR 更改的第一个设置是项目平台： 
1. 选择**文件 > 生成设置 ...**
2. 选择 "平台" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**"
3. 将**SDK**设置为**通用 10**
4. 将**目标设备**设置为**任何设备**以支持沉浸式耳机或切换到**HoloLens**
5. 将**生成类型**设置为**D3D**
6. 将**UWP SDK**设置为**安装的最新版本**

![Unity XR 设置](images/unity-uwp-settings.png)<br>
*Unity XR 设置*

正确配置平台后，需要让 Unity 知道应用在导出时应创建[沉浸式视图](app-views.md)而不是2d 视图：
1. 从 "**生成设置 ...** " 窗口中，打开 "**播放机设置 ...** "
2. 选择通用 Windows 平台 "选项卡的"**设置**"，然后展开" **XR 设置**"组
3. 在 " **XR 设置**" 部分中，选中 "**受支持的虚拟现实**" 复选框以添加 "**虚拟现实设备**" 列表。
4. 在 " **XR 设置**" 组中，确认 **"Windows Mixed Reality"** 列为受支持的设备。 （在旧版 Unity 中，此选项可能显示为 " **Windows 全息**版"）

![Unity UWP 设置](images/xrsettings.png)<br>
*Unity XR 设置*

### <a name="updating-the-manifest"></a>更新清单

您的应用程序现在可以处理全息呈现和空间输入。 但是，你的应用程序需要在其清单中声明相应的功能，才能利用某些功能。 可以通过转到 "**播放机设置" > "通用 Windows 平台 >" 发布设置 "> 功能**，找到项目功能。 

建议在 Unity 中创建清单声明，以将其包含在所有以后导出的项目中。 为混合现实启用常用 Unity Api 的适用功能包括：

|  功能  |  需要功能的 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver （在 HoloLens 上访问[空间映射](spatial-mapping.md)网格） &mdash; *不需要对耳机进行常规空间跟踪* | 
|  网络摄像头  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture （存储捕获的内容时） | 
|  麦克风  |  VideoCapture （捕获音频时）、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer （和使用 Unity 探查器） | 

### <a name="quality-settings"></a>质量设置

HoloLens 具有移动类 GPU。 如果你的应用面向 HoloLens，你需要调整应用中的质量设置以实现最快的性能，以确保它保持完整的帧速率：
1. 选择 "**编辑 > 项目设置 > 质量**"
2. 选择**Windows 应用商店**徽标下的**下拉列表**，并选择 "**非常低**"。 如果 Windows 应用商店列和**极低**的行中的框为绿色，则会知道设置正确应用。

![Unity 质量设置](images/getting-started-unity-quality-settings.jpg)<br>
*Unity 质量设置*

## <a name="per-scene-settings"></a>每场景设置

### <a name="unity-camera-settings"></a>Unity 照相机设置

如果选中 "**支持虚拟现实**"，则[Unity 相机](camera-in-unity.md)组件会处理[头跟踪和 stereoscopic 呈现](rendering.md)。 这意味着不需要使用自定义相机替换主相机对象。

如果你的应用程序专门面向 HoloLens，则需要更改一些设置以优化设备的透明显示。 这些设置允许你的全息内容透过物理环境显示：
1. 在**层次结构**中，选择**主相机**
2. 在 "**检查器**" 面板中，将转换**位置**设置为**0，0，0，** 以使用户头部的位置从 Unity 世界原点开始。
3. 将**清除标志**更改为**纯色**。
4. 将**背景**色更改为**RGBA 0，0，0，0**。 在 HoloLens 中，黑色呈现为透明。
5. 更改**剪辑平面-接近**于[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 （米）。

![Unity 照相机设置](images/Unitycamerasettings.png)<br>
*Unity 照相机设置*

> [!IMPORTANT]
> 如果删除并创建新相机，请确保将新相机标记为 " **MainCamera**"。

## <a name="see-also"></a>另请参阅
* [混合现实工具包 v2](mrtk-getting-started.md)
* [Unity 开发概述](unity-development-overview.md)
