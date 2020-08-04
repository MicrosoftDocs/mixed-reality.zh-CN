---
title: 入门教程 - 2. 初始化项目并部署第一个应用程序
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5cac7d6f776619cbc2a0e0891b7915b656708726
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376649"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2.初始化项目并部署第一个应用程序

## <a name="overview"></a>概述

在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 开发，以及如何导入 MRTK。 你还将演练如何配置和生成基本 Unity 示例场景，并将其从 Visual Studio 部署到 HoloLens 2 或模拟器。

## <a name="objectives"></a>目标

* 了解如何配置用于 HoloLens 开发的 Unity
* 了解如何生成应用并将其部署到 HoloLens
* 体验空间映射网格、手部网格和帧率计数器

## <a name="creating-the-unity-project"></a>创建 Unity 项目

启动“Unity 中心”，选择“项目”选项卡，然后单击“新建”按钮旁边的**向下箭头**：

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

在下拉列表中，选择[先决条件](mr-learning-base-01.md#prerequisites)中指定的 Unity 版本：

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> 如果 Unity Hub 没有特定的 Unity 版本，可以从 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下载存档</a>启动安装。

在“创建新项目”窗口中执行以下操作：

* 确保将“模板”设置为“3D” 
* 输入合适的“项目名称”，例如“MRTK 教程”
* 选择合适的“位置”来存储项目，例如“D:\MixedRealityLearning”
* 单击“创建”按钮，创建并启动新的 Unity 项目

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> 在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。 因此，应将 Unity 项目保存到驱动器的根目录附近。

等待 Unity 创建项目：

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>切换生成平台

在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口： 

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮： 

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

等待 Unity 完成平台切换操作：

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

当 Unity 完成平台切换后，单击红色 **x** 图标，关闭“生成设置”窗口：

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>导入 TextMeshPro 基本资源

在 Unity 菜单中，选择“窗口” > “TextMeshPro” > “导入 TMP 基本资源”以打开“导入 Unity 包”窗口  ：

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> MRTK 的 UI 元素需要 TextMeshPro 基本资源。 如果你不打算在项目中使用 MRTK 的 UI 元素，则可以跳过此步骤。

## <a name="importing-the-mixed-reality-toolkit"></a>导入混合现实工具包

下载 Unity 自定义包：

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

在 Unity 菜单中选择“资产” > “导入包” > “自定义包...”，打开“导入包...”窗口：  

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

在“导入包…”窗口中，选择下载的 Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage，然后单击“打开”按钮 ：

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>配置 Unity 项目

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1.应用 MRTK 项目配置器设置

Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。 如果未显示，请转到 Unity 菜单，并选择“混合现实工具包” > “实用工具” > “配置 Unity 项目”  ：

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

在“MRTK 项目配置器”窗口中，展开“修改配置”部分，确保勾选所有选项，然后单击“应用”按钮以应用设置 ：

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a>2.配置其他项目设置

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： 

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

在“项目设置”窗口中，选择“播放器” > “XR 设置”，单击 + 图标，然后选择“Windows Mixed Reality”以添加 Windows Mixed Reality SDK  ：

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。 如果未显示，请使用 Unity 菜单打开它。

在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

在“项目设置”窗口中，选择“播放器” > “XR 设置”，然后使用“深度格式”下拉列表选“16 位深度”   ：

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> “包名称”是应用的唯一标识符。 在部署应用之前应更改此标识符，以免覆盖以前安装的应用。

> [!TIP]
> “产品名称”是在 HoloLens“开始”菜单中显示的名称。 要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。

## <a name="creating-and-configuring-the-scene"></a>创建和配置场景

在 Unity 菜单中，选择“文件” > “新建场景”，以创建新场景 ：

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

在 Unity 菜单中，选择“混合现实工具包” > “添加到场景并配置…”，将 MRTK 添加到当前场景 ：

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

仍在“层次结构”窗口中选中 MixedRealityToolkit 对象，在“检查器”窗口中验证 MixedRealityToolkit 配置文件是否已设置为 DefaultMixedRealityToolkitConfigurationProfile  ：

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> 通常，在针对 HoloLens 进行开发时会使用 DefaultHoloLens2ConfigurationProfile。 但在本教程中，将使用 DefaultMixedRealityToolkitConfigurationProfile，在下一教程（[配置 MRTK 配置文件](mr-learning-base-03.md)）中，将改用 DefaultHoloLens2ConfigurationProfile。

在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口： 

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

在“保存场景”窗口中，导航到项目的 **Scenes** 文件夹中，为场景提供一个合适的名称（例如“GettingStarted”），然后单击“保存”按钮以保存场景：

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>将应用程序构建到 HoloLens 2

### <a name="1-build-the-unity-project"></a>1.生成 Unity 项目

在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口。 

在“生成设置”窗口中单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表，然后单击“生成”按钮以打开“生成通用 Windows 平台”窗口：

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

在“生成通用 Windows 平台”窗口中，选择用于存储生成的适当位置（例如 _D:\MixedRealityLearning\Builds_），创建一个新文件夹并为其指定适当的名称（例如 _GettingStarted_），然后单击“选择文件夹”按钮，启动生成过程：

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

等待 Unity 完成生成过程：

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.生成并部署应用程序

生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。 在文件夹内导航，然后双击解决方案文件，在 Visual Studio 中其打开：

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> 如果 Visual Studio 要求安装新组件，请花一点时间确保拥有[安装工具](install-the-tools.md)文档中的所有必备组件。

通过选择“Master”配置或“发布”配置、ARM64 体系结构和“设备”作为目标，配置 Visual Studio for HoloLens   ：

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> 如果要部署到 HoloLens（第一代），请选择 x86 体系结构。

> [!NOTE]
> 对于 HoloLens，通常是针对 ARM 体系结构进行生成。 但是，在 Unity 2019.3 中有一个 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知问题</strong></a>，即在 Visual Studio 中选择 ARM 作为生成体系结构时会导致错误。 建议的解决方法是针对 ARM64 进行生成。 如果该方法不可行，请前往“编辑”>“项目设置”>“播放器”>“其他设置”并禁用“图形作业” 。

> [!NOTE]
> 如果目标选项中没有“设备”，则可能需要将 Visual Studio 解决方案的启动项目从 IL2CPP 项目更改为 UWP 项目。 在“解决方案资源管理器”中，右键单击“YourProjectName (通用 Windows)”并选择“设为启动项目”。

将 HoloLens 连接到计算机，然后选择“调试” > “启动但不调试”，以生成并部署到你的设备 ：

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> 在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。 这两个步骤都可以按照[这些说明](using-visual-studio.md)来完成。

> [!TIP]
> 你还可以部署到 [HoloLens 模拟器](using-the-hololens-emulator.md)或创建[应用包](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)用于旁加载。

使用“启动但不调试”会自动启动设备上的应用，而不会连接 Visual Studio 调试器。

选择“生成”>“部署解决方案”，在不自动启动应用的情况下将内容部署到设备。

> [!NOTE]
>在应用中，你可能会注意到诊断探查器，可以使用语音命令“切换诊断”来切换其可见性。 我们建议你在开发过程中使探查器在大部分时间都可见，以便了解何时更改应用可能会影响性能。 例如，HoloLens 应用应以 [60 Fps 连续运行](understanding-performance-for-mixed-reality.md)。

## <a name="congratulations"></a>祝贺

现在，你已经部署了第一个 HoloLens 2 应用。 四处浏览一下，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。 这些只是 MRTK 附带的几个基础功能。 在接下来的教程中，我们将向场景添加内容，以探索 HoloLens 和 MRTK 的各种功能。

[下一教程：3.配置 MRTK 配置文件](mr-learning-base-03.md)
