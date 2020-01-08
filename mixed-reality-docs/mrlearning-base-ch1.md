---
title: 入门教程 - 2. 初始化你的项目和第一个应用程序
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334412"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化你的项目和第一个应用程序

## <a name="overview"></a>概述

在第一堂课中，你将了解<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 提供的一些功能，针对 HoloLens 2 启动你的第一个应用程序，并将其部署到设备上。

## <a name="objectives"></a>目标

* 配置 Unity 以便进行 Hololens 开发。
* 导入资产并设置场景。
* 空间映射网格、手部网格和帧率计数器的可视化。

## <a name="create-new-unity-project"></a>创建新的 Unity 项目

1. 启动 Unity。

2. 选择“新建”  。

    ![第 1 课第 1 部分步骤 2](images/mrlearning-base-ch1-1-step2.JPG)

3. 输入项目名称（例如“MixedRealityBase”）。

    ![第 1 课第 1 部分步骤 3](images/mrlearning-base-ch1-1-step3.JPG)

4. 输入保存项目的位置。

    ![第 1 课第 1 部分步骤 4](images/mrlearning-base-ch1-1-step4.JPG)

5. 请确保将项目设置为“3D”  。

    ![第 1 课第 1 部分步骤 5](images/mrlearning-base-ch1-1-step5.JPG)

6. 单击“创建项目”  。

    ![第 1 课第 1 部分步骤 6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>配置用于 Windows Mixed Reality 的 Unity 项目

1. 转到“文件” > “生成设置”，打开“生成设置”窗口。   

    ![第 1 课第 2 部分步骤 1](images/mrlearning-base-ch1-2-step1.JPG)

2. 选择“通用 Windows 平台”，然后单击“切换平台”按钮以切换平台。   在 HoloLens 2 上运行的应用程序必须兼容通用 Windows 平台 (UWP)。

    ![第 1 课第 2 部分步骤 2](images/mrlearning-base-ch1-2-step2.JPG)

3. 通过单击“生成”窗口中的“播放器设置”按钮启用虚拟现实，然后在检查器面板中启用“XR 设置”下的“支持虚拟现实”复选框，如下图所示。   请注意，可能需要将“生成设置”窗口拖动到旁边，以便查看检查器面板。  “支持虚拟现实”复选框也适用于混合现实和增强现实头戴显示设备，因为它指的是启用立体视觉（为每只眼睛渲染不同的图像）。 

    ![第 1 课第 2 部分步骤 3](images/mrlearning-base-ch1-2-step3.JPG)

4. 另外，请在“XR 设置”下将“立体渲染模式”更改为“单通道实例化”。   对于 HoloLens 2 来说，此[渲染管道样式](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)通常是性能最强的。 如果对适合 Unity 环境的其他高性能配置感兴趣，请按照[这些说明](recommended-settings-for-unity.md)操作。

    ![第 1 课第 2 部分步骤 4](images/mrlearning-base-ch1-2-step4.jpg)

5. 在同一个检查器面板中，确保在“发布设置”下启用“功能”部分的“空间感知”复选框。   通过“空间感知”功能，我们可以在混合现实设备（如 HoloLens 2）上可视化空间映射网格。 可以在检查器面板的“XR 设置”上方和“其他设置”下方找到“发布设置”。

    ![第 1 课第 2 部分步骤 5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    >你可能希望启用一些其他的常用功能（虽然本部分未使用到），包括“麦克风”（用于语音命令）和 *InternetClient*（用于连接到需要网络连接的服务）。 

## <a name="import-the-mixed-reality-toolkit"></a>导入混合现实工具包

1. 下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation 包版本 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) 并将其保存到电脑上的文件夹。

2. 导入在上一步下载的混合现实工具包  。 一开始请单击“资产”   >   “导入” >   “自定义包”，然后选择 *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* 并将其打开，开始导入过程。 等待几分钟，以便该导入过程完成。

    ![第 1 课第 3 部分步骤 2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![第 1 课第 3 部分步骤 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. 在下一个弹出窗口中单击“导入”，开始将所选包导入 Unity 项目。  请确保选中所有项，如图所示。

    ![第 1 课第 3 部分步骤 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > 如果看到一个弹出式对话框，要求应用混合现实工具包默认设置，请单击“应用”。  在导入后进行自动设置时，MRTK 会分析项目中是否缺少建议的设置。 弹出式对话框看起来可能不同于下图，具体取决于你的设置。

    ![第 1 课第 3 部分步骤 4 说明 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a>配置混合现实工具包

1. 将混合现实工具包添加到当前场景，方法是：  从菜单栏选择“混合现实工具包”   >   “添加到场景并配置...”。 如果在导入混合现实工具包后没有看到此菜单项，请重启 Unity。

    ![第 1 课第 4 部分步骤 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > 可能会看到一个弹出式对话框，用于选择[混合现实工具包的配置文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。 请双击名为 *DefaultHoloLens2ConfigurationProfile* 的配置文件，将其选中。

2. 你的场景会有多个新项和修改项。 单击“文件” > “另存为”，使用其他名称保存场景并为场景命名，例如 *BaseScene*。   将场景保存到项目的 *Assets* 文件夹中的 *Scenes* 文件夹，以保持场景的有序性。

    ![第 1 课第 4 部分步骤 2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![第 1 课第 4 部分步骤 2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a>在设备上构建应用程序

1. 如果在前面的部分关闭了“生成设置”窗口，请转到“文件” > “生成设置”，再次打开“生成设置”窗口。    

    ![第 1 课第 5 部分步骤 1](images/mrlearning-base-ch1-5-step1.JPG)

2. 当场景在 Unity 中处于打开状态时，请单击“添加打开的场景”按钮，确保刚创建的场景位于“生成中的场景”列表中。  

3. 按“生成”按钮，开始生成过程。 

    ![第 1 课第 5 部分步骤 3](images/mrlearning-base-ch1-5-step3.JPG)

4. 为应用程序创建一个新文件夹并为其命名。 在下图中，我们创建了一个名为 App 的文件夹，用于存储该应用程序。 请单击“选择文件夹”，开始生成到新创建的文件夹。  生成完成后，可以关闭 Unity 中的“生成设置”窗口。 

    ![第 1 课第 5 部分步骤 4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    >如果生成失败，尝试再次生成或重启 Unity 并再次生成。 如果看到错误，如“错误:CS0246 = 找不到类型或命名空间名称 “XX” (是否缺少 using 指令或程序集引用?)”， 可能需要安装 [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)

5. 生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。 双击“MixedRealityBase.sln”解决方案或相应的名称（如果使用了项目的替代名称），在 Visual Studio 中打开解决方案文件。 

    >[!NOTE]
    >请务必打开新创建的文件夹（即 *App* 文件夹，如果遵循前面步骤中的命名约定），因为在该文件夹之外会有一个类似名称的 .sln 文件，不能将其与生成文件夹内的 .sln 文件混淆。 文件夹结构看起来应该类似于下图。
    >
    >如果 Visual Studio 要求你安装新组件，请花一点时间确保按照[“安装工具”页面](install-the-tools.md)中的说明安装所有必备组件

    ![第 1 课第 5 部分步骤 5](images/mrlearning-base-ch1-5-step5.JPG)

6. 将 HoloLens 2 连接到电脑中。 虽然这些说明假设你会部署到 HoloLens 2 设备，但你也可以选择部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或选择创建[用于旁加载的应用包](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

    >[!IMPORTANT]
    >在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。  这两个步骤都可以按照[这些说明](using-visual-studio.md)来完成

7. 通过选择“发布”配置或“Master”配置、“ARM”体系结构和“设备”作为目标，配置 Visual Studio 以生成到 HoloLens 2。    

    ![第 1 课第 5 部分步骤 8](images/mrlearning-base-ch1-5-step7.JPG)

8. 最后一步是选择“调试” > “在不调试的情况下启动”，以便生成并部署到你的设备。   选择“在不调试的情况下启动”会导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中附加调试程序和显示调试信息。  这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。

    > [!NOTE]
    > 也可以选择“生成” > “部署解决方案”以部署到你的设备，而无需自动启动应用程序。  

    ![第 1 课第 5 部分步骤 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>祝贺

你现在已经部署了第一个 HoloLens 2 应用程序。 当你四处走动时，应该看到空间映射网格覆盖了 HoloLens 2 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用程序性能的帧速率计数器。 这些只是混合现实工具包中开箱即用的一些基本功能。 在接下来的课程中，你将开始为场景添加更多的内容和交互性，以便充分探索 HoloLens 2 和混合现实工具包的功能。

> [!NOTE]
> 在应用中，你可能会注意到可视探查器。 [第 5 课](mrlearning-base-ch5.md)会介绍如何使用语音命令切换帧速率计数器。 通常建议在开发过程中让可视探查器始终保持可见状态，这样就可以了解何时代码更改会影响性能。 HoloLens 2 应用程序应该[持续在 60 FPS 运行](understanding-performance-for-mixed-reality.md)。

[下一课：3.创建用户界面并配置混合现实工具包](mrlearning-base-ch2.md)
