---
title: 为 Windows Mixed Reality 配置新的 Unity 项目
description: 不 MRTK 配置 Unity 项目
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目
ms.openlocfilehash: 99c72f2d9d900c8a05fb7d8b9b8de10d657fdd13
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502648"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>为 Windows Mixed Reality 配置新的 Unity 项目 

（如果已将 MRTK v2 导入到 Unity 项目中，请跳过）

如果要在不导入混合现实工具包的情况下创建新的 Unity 项目，则需要为 Windows Mixed Reality 手动更改的一小一组 Unity 设置，分为两类：每个项目和每场景。

## <a name="per-project-settings"></a>每个项目的设置

若要面向 Windows Mixed Reality，首先需要将 Unity 项目设置为导出为通用 Windows 平台应用： 
1. 选择**文件 > 生成设置 ...**
2. 选择 "平台" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**"
3. 将**SDK**设置为**通用 10**
4. 将**目标设备**设置为**任何设备**以支持沉浸式耳机或切换到**HoloLens**
5. 将**生成类型**设置为**D3D**
6. 将**UWP SDK**设置为**安装的最新版本**

接下来，您需要让 Unity 知道您尝试导出的应用程序应创建[沉浸式视图](app-views.md)而不是2d 视图。 为此，请启用 "支持的虚拟现实"：
1. 从 "**生成设置 ...** " 窗口中，打开 "**播放机设置 ...** "
2. 选择通用 Windows 平台 "选项卡的**设置**
3. 展开 " **XR 设置**" 组
4. 在 " **XR 设置**" 部分中，选中 "**受支持的虚拟现实**" 复选框以添加 "**虚拟现实设备**" 列表。
5. 在 " **XR 设置**" 组中，确认 **"Windows Mixed Reality"** 列为受支持的设备。 （在早期版本的 Unity 中，这可能显示为 "Windows 全息"）

![Unity 质量设置](images/getting-started-unity-quality-settings.jpg)<br>
*Unity xr 设置*

现在，你的应用可以执行基本的全息呈现和空间输入。 若要进一步了解并利用某些功能，应用必须在其清单中声明相应的功能。 清单声明可以在 Unity 中进行，因此它们包含在每个后续的项目导出中。 这些设置位于 "**播放机设置" > "通用 Windows 平台 >" 发布设置 "> 功能**的" 设置 "。 为混合现实启用常用 Unity Api 的适用功能包括：

|  功能  |  需要功能的 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver （可以访问 HoloLens 上的[空间映射](spatial-mapping.md)网格）&mdash;*耳机的常规空间跟踪不需要的功能* | 
|  网络摄像头  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture （存储捕获的内容时） | 
|  麦克风  |  VideoCapture （捕获音频时）、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer （和使用 Unity 探查器） | 

**Unity 质量设置**

![Unity 质量设置](images/getting-started-unity-quality-settings.jpg)<br>
*Unity 质量设置*

HoloLens 具有移动类 GPU。 如果你的应用面向 HoloLens，你将希望优化质量设置以实现最快的性能，以确保保持完整的帧率：
1. 选择 "**编辑 > 项目设置 > 质量**"
2. 选择**Windows 应用商店**徽标下的**下拉列表**，并选择 "**非常低**"。 如果 Windows 应用商店列和**极低**的行中的框为绿色，则会知道设置正确应用。

## <a name="per-scene-settings"></a>每场景设置

**Unity 照相机设置**

![Unity 相机设置](images/Unitycamerasettings.png)<br>
*Unity 照相机设置*

启用 "受支持的虚拟现实" 复选框后， [Unity 相机](camera-in-unity.md)组件将处理[头跟踪和 stereoscopic 渲染](rendering.md)。 不需要将其替换为自定义相机即可执行此操作。

如果你的应用程序专门面向 HoloLens，则需要更改一些设置以优化设备的透明显示，因此你的应用程序将向物理环境显示：
1. 在**层次结构**中，选择**主相机**
2. 在 "**检查器**" 面板中，将转换**位置**设置为**0，0，0，** 以使用户头部的位置从 Unity 世界原点开始。
3. 将**清除标志**更改为**纯色**。
4. 将**背景**色更改为**RGBA 0，0，0，0**。 在 HoloLens 中，黑色呈现为透明。
5. 更改**剪辑平面-接近**于[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 （米）。

如果删除并创建新的相机，请确保将相机**标记**为 " **MainCamera**"。


## <a name="see-also"></a>另请参阅
* [混合现实工具包 v2](mrtk-getting-started.md)
* [Unity 开发概述](unity-development-overview.md)
