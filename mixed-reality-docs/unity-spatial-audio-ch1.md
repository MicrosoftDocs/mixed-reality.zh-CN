---
title: 空间音频教程-1。 向项目添加空间音频
description: 将 Microsoft Spatializer 插件添加到 Unity 项目以访问 HoloLens 2 HRTF 硬件卸载。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合现实、unity、教程、hololens2、空间音频
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182794"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>将空间音频添加到 Unity 项目

欢迎使用 HoloLens2 上适用于 Unity 的空间音频 tutioral。 本教程序列显示：
* 如何在 Unity 中的 HoloLens 2 上使用 HRTF 卸载
* 如何在使用 HRTF 卸载时启用回响

[Microsoft Spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)包含此教程序列的已完成 Unity 项目。 

有关 spatialize 声音非常有用的建议，请参阅[空间音效设计](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)。

## <a name="objectives"></a>目标
在第一章中，你将：
* 创建 Unity 项目并导入 MRTK
* 导入 Microsoft spatializer 插件
* 启用 Microsoft spatializer 插件
* 启用开发人员工作站上的空间音频

## <a name="create-a-project-and-add-nuget-for-unity"></a>创建项目并为 Unity 添加 NuGet
从空 Unity 项目开始，为 Unity 添加并配置 NuGet：
1. 下载最新的[NuGetForUnity. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. 在 Unity 菜单栏中，单击 "**资产-> 导入包-> 自定义包 ...** " 并安装 NuGetForUnity 包：

![导入自定义包](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>添加 Windows Mixed Reality 包
Unity 2019 和更高版本中的 Windows Mixed Reality 支持包含在一个可选的包中。 若要将其添加到项目，请从 Unity 菜单栏中打开 " **> 包管理器**"：

![程序包管理器菜单](images/spatial-audio/package-manager-menu.png)

然后查找并安装**Windows Mixed Reality**包：

!["程序包管理器" 窗口](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>安装 MRTK 和 Microsoft Spatializer
使用 NuGet for Unity，安装 MRTK 和 Microsoft Spatializer 插件：
1. 在 Unity 菜单栏中，单击 " **nuget-> 管理 Nuget 包**"。

![管理 NuGet 程序包](images/spatial-audio/manage-nuget-packages.png)

2. 在 "**搜索**" 框中，输入 "MixedReality" 并安装 MRTK 核心包： **MixedReality**

![MRTK NuGet 包](images/spatial-audio/mrtk-nuget-package.png)

[MRTK NuGet 包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html)具有其他上下文和详细信息。

4. 在**搜索**框中，输入 "SpatialAudio"，并安装 microsoft Spatializer Package： **SpatialAudio. Spatializer**

![Spatializer 插件 NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>在项目中设置 MRTK

1. 转到 "**文件 > 生成设置**"，打开 "生成设置" 窗口。

2. 选择 "_通用 Windows 平台_"，然后单击 "**切换平台**"。

3. 单击 "**生成" 窗口**中的 "**播放机设置**"，在 "**检查器**" 窗格中打开**播放机设置**属性。
    * 在 " **XR 设置**" 下，选中 "**支持虚拟现实**" 复选框
    * 在 " **XR 设置**" 下，将**立体声渲染模式**更改为**单步实例**。
    * 在 "**发布设置**" 下的 "**功能**" 部分中，选中 "**空间感知**" 复选框

4. 在菜单栏上，单击 "**混合现实工具包-> 添加到场景并配置 ...** "。 将 MRTK 添加到场景中。

有关其他指南，包括如何生成应用并将其部署到 HoloLens 2，请参阅[尊敬的学习基础模块第1章](mrlearning-base-ch1.md)。

## <a name="enable-the-microsoft-spatializer-plugin"></a>启用 Microsoft Spatializer 插件
启用**Microsoft Spatializer**插件。 打开 **> 项目设置-> 音频**"，然后将**Spatializer 插件**更改为" Microsoft Spatializer "。 **项目设置**的 "**音频**" 部分现在将如下所示：

![显示 spatializer 插件的项目设置](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>启用工作站上的空间音频
在桌面版本的 Windows 上，默认情况下禁用空间音频。 右键单击任务栏中的音量图标即可启用此项。 若要获得有关在 HoloLens 2 上收到的内容的最佳表示，请选择 "**空间音效-> Windows Sonic 用于耳机**"。

![桌面空间音频设置](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> 仅当计划在 Unity 编辑器中测试项目时，才需要此设置。

## <a name="next-steps"></a>后续步骤
继续到[Unity 空间音频第2章](unity-spatial-audio-ch2.md)，spatialize 按钮交互声音。

