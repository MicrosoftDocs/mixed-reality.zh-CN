---
title: 入门教程-2。 初始化项目和首个应用程序
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 3bf218b42ea8abed45a80c0dd048e791cdd8372b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926889"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. 初始化项目和首个应用程序

在第一课中，您将了解到[混合现实工具包（MRTK）]()必须提供的某些功能，启动 HoloLens 2 的第一个应用程序，并将其部署到设备。

## <a name="objectives"></a>目标

* 针对 Hololens 开发优化 Unity。
* 导入资产并设置场景。
* 空间映射网格、手动网格和帧速率计数器的可视化。

## <a name="instructions"></a>说明

### <a name="create-new-unity-project"></a>创建新的 Unity 项目

1. 启动 Unity。
2. 选择**新建**。
![学习 Section1 步骤 2](images/mrlearning-base-ch1-1-step2.JPG)

3. 输入项目名称（例如 "MixedRealityBase"）。
![学习 Section1 步骤 3](images/mrlearning-base-ch1-1-step3.JPG)
4. 输入保存项目的位置。
![学习 Section1 步骤 4](images/mrlearning-base-ch1-1-step4.JPG)
5. 请确保将项目设置为“3D”。
![学习 Section1 步骤 5](images/mrlearning-base-ch1-1-step5.JPG)
6. 单击“创建项目”。
![学习 Section1 步骤 6](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>配置用于 Windows Mixed Reality 的 Unity 项目

1. 转到 "**文件** > **生成设置**"，打开 "*生成设置*" 窗口。
![学习 Section2 步骤 1](images/mrlearning-base-ch1-2-step1.JPG)
2. 选择 "*通用 Windows 平台*"，然后单击 "**切换平台**" 按钮切换平台。 在 HoloLens 2 上运行的应用程序需要与通用 Windows 平台（UWP）兼容。
![学习 Section2 步骤 2](images/mrlearning-base-ch1-2-step2.JPG)
3. 通过单击 "生成" 窗口中的 "**播放机设置**" 按钮启用虚拟现实，并在 "检查器" 面板中的 "XR 设置" 下启用 "*支持虚拟现实*" 复选框，如下图所示。 请注意，您可能需要将 "*生成设置*" 窗口拖出，以查看检查器面板。 "*受支持的虚拟现实*" 复选框还适用于混合现实和增加的现实耳机，因为它指的是启用 stereoscopic 视觉（每个眼睛呈现不同的图像） ![学习 Section2 步骤 3](images/mrlearning-base-ch1-2-step3.JPG)
4. 同时，在 XR 设置下，将*立体声渲染模式*改为*单步实例*。 此[呈现管道样式](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)对于 HoloLens 2 而言通常是最高性能的。 如果对 Unity 环境的其他性能配置感兴趣，请遵循[这些说明](recommended-settings-for-unity.md)。
![学习 Section2 步骤 4](images/mrlearning-base-ch1-2-step4.jpg)
5. 在相同的检查器面板中，确保在 "*发布设置*" 下启用 "功能" 部分中的 "*空间感知*" 复选框。 空间感知使我们能够在混合现实设备上（如 HoloLens 2）直观显示空间映射网格。 发布设置可在 "检查器" 面板中的 "XR 设置" 和 "其他设置" 下找到。
![学习 Section2 步骤 5](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > 虽然本部分未使用，但你可能想要启用的其他一些常见功能包括用于语音命令的*麦克风*，以及用于连接到需要网络连接的服务的*InternetClient* 。

### <a name="import-the-mixed-reality-toolkit"></a>导入混合现实工具包

1. 下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)Unity [foundation 包版本 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) ，并将其保存到电脑上的文件夹中。

2. 导入在上一步中下载的*混合现实工具包*包。 首先，单击 "**资产**" > **导入** > **自定义包**"，然后选择*unitypackage*并打开它以开始导入过程。 请等待几分钟，以便完成导入过程。
    ![学习 Section3 Step2a](images/mrlearning-base-ch1-3-step2a.JPG) ![学习 Section3 Step2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. 在下一个弹出窗口中，单击 "**导入**"，开始将所选包导入 Unity 项目。 确保所有项都已选中，如图所示。
    ![学习 Section3 步骤 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > 如果你看到一个弹出对话框，要求应用混合现实工具包默认设置，请单击 "**应用**"。 MRTK 在为自动安装导入时，分析你的项目中是否缺少建议的设置。 根据您的设置，popup 可能看上去与下图有所不同。

    ![学习 Section3 步骤 4 Note1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>配置混合现实工具包

1. 通过选择 "**混合现实工具包**" > "**添加到场景" 并配置**，将*混合现实工具包*添加到当前场景。 从菜单栏中。 如果在导入混合现实工具包后没有看到此菜单项，请重启 Unity。
    ![学习 Section4 步骤 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > 你可能会看到一个弹出对话框，用于为[混合现实工具包选择配置文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。 双击名为*DefaultHoloLens2ConfigurationProfile*的配置文件，将其选中。

2. 场景将包含多个新的项目和修改。 单击 "**文件**" > "**另存为 ...** "，并为场景指定名称（如*BaseScene*），以其他名称保存场景。 通过将场景保存到项目的 "*资产*" 文件夹中的*场景*文件夹，使场景保持井然有序。
    ![学习 Section4 Step2a](images/mrlearning-base-ch1-4-step2a.JPG) ![学习 Section4 Step2b](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>在设备上构建应用程序

1. 如果关闭了前面几节中的 "*生成设置*" 窗口，请通过转到 "**文件** > **生成设置**"，重新打开 "*生成设置*" 窗口。
    ![学习 Section5 步骤 1](images/mrlearning-base-ch1-5-step1.JPG)

2. 如果场景在 Unity 中打开，请单击 "**添加打开的场景**" 按钮，确保刚刚创建的场景在 "*生成*" 列表中的场景中。

3. 按 "**生成**" 按钮开始生成过程。
    ![学习 Section5 步骤 3](images/mrlearning-base-ch1-5-step3.JPG)

4. 为应用程序创建一个新文件夹并为其命名。 在下图中，创建了一个包含应用程序的名称为 "应用程序" 的文件夹。 单击 "**选择文件夹**"，开始生成到新创建的文件夹。 完成生成后，可以关闭 Unity 中的 "*生成设置*" 窗口。
    ![学习 Section5 步骤 4](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > 如果生成失败，尝试再次生成或重启 Unity 并再次生成。 如果看到错误，如 "错误： CS0246 = 类型或命名空间名称" XX "（是否缺少 using 指令或程序集引用？）。 如果是这样，则可能需要安装[Windows 10 SDK （10.0.18362.0）](https://developer.microsoft.com//windows/downloads/windows-10-sdk)

5. 生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。 双击 " *MixedRealityBase* " 解决方案或相应的名称（如果你使用的是项目的备用名称）以在 Visual Studio 中打开解决方案文件。

    > [!NOTE]
    > 如果遵循前面步骤中的命名约定，请确保打开新创建的文件夹（即*App*文件夹），因为在该文件夹外，不会与 build 文件夹内的 .sln 文件混淆的名称类似。 文件夹结构应类似于下图。
    >
    > 如果 Visual Studio 要求你安装新组件，请花一点时间确保按照[“安装工具”页面](install-the-tools.md)中的说明安装所有必备组件

    ![学习 Section5 步骤5](images/mrlearning-base-ch1-5-step5.JPG)

6. 将 HoloLens 2 连接到您的 PC。 尽管这些说明假设你将部署到 HoloLens 2 设备，但你也可以选择部署到[hololens 2 模拟器](using-the-hololens-emulator.md)，或选择创建[用于旁加载的应用包](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

    > [!IMPORTANT]
    > 在生成到设备之前，设备必须处于*开发人员模式*并与开发计算机配对。 可以按照以下[说明](using-visual-studio.md)完成这两个步骤

7. 将 Visual Studio 配置为通过选择 "*发布*" 或 "*主*" 配置、 *ARM*体系结构和 "目标 *" 作为 "* 目标"，为你的 HoloLens 2 生成。
    ![学习 Section5 Step8](images/mrlearning-base-ch1-5-step7.JPG)

8. 最后一步是通过选择 "**调试**" > "开始执行（**不调试**）" 来生成并部署到设备。 如果选择 "*启动但不调试*"，则会导致应用程序在成功生成后立即在设备上启动，但不会附加调试器，而且会在 Visual Studio 中显示信息。 这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。

    > [!NOTE]
    > 你还可以选择 "**生成**" > **部署解决方案**以部署到设备，而无需应用程序自动启动。

    ![学习 Section5 Step9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>祝贺

现在，你已部署了第一个 HoloLens 2 应用程序。 在四处浏览时，应会看到一个空间映射网格，其中包含已由 HoloLens 2 检测到的所有表面。 此外，你应该看到手指和抓手指，以及用于跟踪应用程序性能的帧速率计数器。 这些只是混合现实工具包中开箱即用的一些基本功能。 在即将推出的课程中，您将开始向场景中添加更多内容和交互性，以便您可以充分探索 HoloLens 2 的功能和混合现实工具包。

> [!NOTE]
> 在应用程序中，你可能会注意到可视化探查器。 你将在[第5课](mrlearning-base-ch5.md)中介绍如何使用语音命令切换帧速率计数器。 通常建议在开发过程中始终保持可视化探查器的可见性，以了解代码更改可能会影响性能。 HoloLens 2 应用程序应[持续运行 60 FPS](understanding-performance-for-mixed-reality.md)。

[下一课： 3. 创建用户界面和配置混合现实工具包](mrlearning-base-ch2.md)
