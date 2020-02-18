---
title: 入门教程 - 2. 初始化你的项目和第一个应用程序
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: d3392df9bfad5938d71d3a01999be51834a98a5d
ms.sourcegitcommit: 87aca9c2b73b0e83cb70a46443dcdb08c3621005
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77373447"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化你的项目和第一个应用程序

## <a name="overview"></a>概述

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
在这第一个教程中，我们将了解<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 提供的一些功能，针对 HoloLens 2 启动第一个应用程序，并将其部署到设备上。

## <a name="objectives"></a>目标

* 配置用于 Hololens 开发的 Unity
* 导入资产并设置场景
* 空间映射网格、手部网格和帧率计数器的可视化

## <a name="prerequisites"></a>必备条件

* 一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一些基本的 C# 编程功能
* 一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块

> [!IMPORTANT]
> 建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。

## <a name="create-new-unity-project"></a>创建新的 Unity 项目

启动“Unity 中心”，  选择“项目”选项卡，  然后单击“新建”按钮旁边的**向下箭头**： 

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

选择上面[先决条件](#prerequisites)部分中指定的 Unity 版本：

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

在“创建新项目”窗口中执行以下操作：

* 确保将“模板”设置为“3D”  
* 输入合适的“项目名称”，例如“MRTK 教程”  
* 选择合适的“位置”来存储项目，例如“D:\MixedRealityLearning”  
* 单击“创建”按钮，创建并启动新的 Unity 项目 

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> 在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。 如果任何文件路径的长度超出 255 个字符，则 Unity 受这些限制影响，可能无法编译。 因此，强烈建议将 Unity 项目存储在尽可能靠近驱动器根目录的位置。

等待 Unity 创建项目：

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>配置用于 Windows Mixed Reality 的 Unity 项目

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

在此部分，我们将切换生成平台、启用虚拟现实并启用空间感知。

### <a name="1-switch-build-platform"></a>1.切换生成平台

在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口：  

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮：  

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

等待 Unity 完成平台切换操作：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

当 Unity 完成平台切换后，单击红色 **x** 图标，关闭“生成设置”窗口：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a>2.启用虚拟现实

> [!NOTE]
> “启用虚拟现实”功能也适用于混合现实和增强现实头戴显示设备，因为它指的是启用立体视觉，即：为每只眼睛渲染不同的图像。

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口：  

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

在“项目设置”窗口中选择“播放器” > “XR 设置”，展开“XR 设置”：  

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

在“XR 设置”中勾选“支持虚拟现实”复选框以启用虚拟现实，然后单击“+”图标并选择“Windows Mixed Reality”，以便添加 Windows Mixed Reality SDK：   

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

等待 Unity 完成添加 SDK 的操作：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

当 Unity 完成添加 SDK 的操作后，请优化 XR 设置，如下所示：

* 将 Windows Mixed Reality 的“深度格式”设置为“16 位深度”  
* 勾选 Windows Mixed Reality 的“启用深度共享”复选框 
* 将“立体渲染模式\*”更改为“单通道实例化”  

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> 若要详细了解如何为 Windows Mixed Reality 优化 Unity，可参阅[建议用于 Unity 的设置](recommended-settings-for-unity.md)文档。

### <a name="3-enable-spatial-perception"></a>3.启用空间感知

> [!NOTE]
> 可以通过空间感知在 Windows Mixed Reality 设备上可视化空间映射网格。

在“项目设置”窗口中选择“播放器” > “发布设置”，展开“发布设置”：  

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

在“发布设置”中，向下滚动到“功能”  部分，勾选“SpatialPerception”  复选框：

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

关闭“项目设置”窗口。

## <a name="import-textmesh-pro-essential-resources"></a>导入 TextMesh Pro 基本资源

> [!NOTE]
> 我们导入此包是因为混合现实工具包的 UI 元素需要此包。

在 Unity 菜单中，选择“窗口”   > “TextMeshPro”   >   “导入 TMP Pro 基本资源”：

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

在“导入 Unity 包”窗口中单击“全部”  按钮，确保选择所有资产，然后单击“导入”  按钮以导入资产：

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a>导入混合现实工具包

下载 Unity 自定义包：

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.2.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage)

在 Unity 菜单中选择“资产” > “导入包” > “自定义包...”，打开“导入包...”窗口：   

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

在“导入包...”窗口中，选择下载的 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage**，然后单击“打开”  按钮：

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

在“导入 Unity 包”窗口中单击“全部”  按钮，确保选择所有资产，然后单击“导入”  按钮以导入资产：

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a>配置用于混合现实工具包的 Unity 项目

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

在导入包后，应显示“MRTK 项目配置器”窗口。 如果未显示该窗口，请将其打开，方法是：在 Unity 菜单中选择“混合现实工具包”   > “实用程序”   >   “配置 Unity 项目”。

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

在“MRTK 项目配置器”窗口中，展开“修改配置”部分，<u>取消选中</u>“启用 MSBuild for Unity”复选框，确保勾选所有其他选项，然后单击“应用”按钮以应用设置：   

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> MSBuild for Unity 可能不支持你将使用的所有 SDK，在启用它后再禁用它可能比较困难。 因此，强烈建议不要启用 MSBuild for Unity。

## <a name="configure-the-mixed-reality-toolkit"></a>配置混合现实工具包
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

在 Unity 菜单中选择“混合现实工具包”   >   “添加到场景并配置...”，将混合现实工具包添加到当前场景：

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

在“层次结构”窗口中选择 MixedRealityToolkit 对象后，请在“检查器”窗口中将混合现实工具包配置文件更改为 **DefaultHoloLens2ConfigurationProfile**：

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口：  

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

在“保存场景”窗口中，导航到项目的 **Scenes** 文件夹中，为场景提供一个合适的名称（例如“入门”  ），然后单击“保存”  按钮以保存场景：

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a>在设备上构建应用程序

### <a name="1-build-the-unity-project"></a>1.生成 Unity 项目

在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口。  

在“生成设置”窗口中单击“添加打开的场景”  按钮，将当前场景添加到“生成中的场景”列表  ，然后单击“生成”  按钮以打开“生成通用 Windows 平台”窗口：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

在“生成通用 Windows 平台”窗口中，选择用于存储生成的适当位置（例如 _D:\MixedRealityLearning\Builds_），创建一个新文件夹并为其指定适当的名称（例如 _GettingStarted_），然后单击“选择文件夹”  按钮，启动生成过程：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

等待 Unity 完成生成过程：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.生成并部署应用程序

生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。 在文件夹内导航，然后双击解决方案文件，在 Visual Studio 中其打开：

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> 如果 Visual Studio 要求安装新组件，请花一点时间确保按照[安装工具](install-the-tools.md)文档中的说明安装所有必备组件。

通过选择“Master”配置或“发布”配置、“ARM”体系结构和“设备”作为目标，配置 Visual Studio for HoloLens 2。    

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

将 HoloLens 2 连接到计算机。

> [!IMPORTANT]
> 在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。 这两个步骤都可以按照[这些说明](using-visual-studio.md)来完成。

最后一步是选择“调试” > “在不调试的情况下启动”，以便生成相关内容并将其部署到设备：  

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

虽然这些说明假设你会将内容部署到 HoloLens 2 设备，但你也可以将内容部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)，或创建[用于旁加载的应用包](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)。

选择“在不调试的情况下启动”会导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中附加调试程序和显示调试信息。 这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。

若要在不自动启动应用程序的情况下将内容部署到设备，可以选择“生成”>“部署解决方案”。

## <a name="congratulations"></a>祝贺

<!-- TODO: Consider cleanup and adding in app screenshots -->
你现在已经部署了第一个 HoloLens 2 应用程序。 当你四处走动时，应该看到空间映射网格覆盖了 HoloLens 2 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用程序性能的帧速率计数器。 这些只是混合现实工具包中开箱即用的一些基本功能。 在接下来的教程中，我们将开始为场景添加更多的内容和交互性，以便充分探索 HoloLens 2 和混合现实工具包的功能。

> [!NOTE]
> 在应用中，你可能会注意到诊断探查器。可以使用语音命令“切换诊断”  来切换其可见性。 但是，通常建议在开发过程中让探查器始终保持可见状态，这样就可以了解何时对应用所做的更改会影响性能，例如，HoloLens 2 应用程序会[在 60 FPS 连续运行](understanding-performance-for-mixed-reality.md)。

[下一教程：3.创建用户界面并配置混合现实工具包](mrlearning-base-ch2.md)
