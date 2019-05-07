---
title: 针对 Windows Mixed Reality 配置新的 Unity 项目
description: 配置而无需 MRTK Unity 项目
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity 中，混合现实、 开发、 开始、 新建项目
ms.openlocfilehash: 4ee81eca25109da428d7b3addf59e102ddc5c5cf
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993542"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>针对 Windows Mixed Reality 配置新的 Unity 项目 

（如果你已导入 Unity 项目 MRTK v2，请跳过）

如果你想要创建新的 Unity 项目没有导入混合现实工具包，有少量的 Unity 设置，将需要手动更改 Windows Mixed Reality，划分为两个类别： 每个项目和每个场景。

## <a name="per-project-settings"></a>每个项目设置

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
2. 选择**下拉列表中**下**Windows 应用商店**徽标，然后选择**非常低**。 您将知道当正确应用了设置 Windows 应用商店列中的框并**非常低**行都显示为绿色。

## <a name="per-scene-settings"></a>每个场景设置

**Unity 照相机设置**

![Unity 照相机设置](images/Unitycamerasettings.png)<br>
*Unity 照相机设置*

可以在"虚拟现实支持"复选框，一旦[Unity 照相机](camera-in-unity.md)组件句柄[头跟踪和立体呈现](rendering.md)。 没有无需将其替换为自定义在相机上以执行此操作。

如果您的应用程序专门面向 HoloLens，有几个需要更改以使您的应用程序将通过显示物理世界的设备的透明显示优化的设置：
1. 在中**层次结构**，选择**Main Camera**
2. 在**Inspector**面板中，将转换**位置**到**0，0，0**以便用户头位置始于 Unity 世界原点。
3. 更改**清除标志**到**纯色**。
4. 更改**背景**颜色**RGBA 0,0,0,0**。 黑色将呈现为透明的 HoloLens。
5. 更改**剪裁平面的附近**到[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 （米）。

如果你删除并创建一个新的照相机，请确保您的照相机**标记**作为**MainCamera**。


## <a name="see-also"></a>请参阅
* [混合现实 Toolkit v2](mrtk-getting-started.md)
* [Unity 开发概述](unity-development-overview.md)
