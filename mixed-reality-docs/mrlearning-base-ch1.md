---
title: MR 学习基本模块 - 项目初始化和第一个应用程序
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "65814014"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>MR 学习基本模块 - 项目初始化和第一个应用程序

在第一堂课中，你将了解混合现实工具包提供的一些功能，针对 HoloLens 2 启动你的第一个应用程序，并将其部署到设备上。

## <a name="objectives"></a>目标

* 针对 Hololens 开发优化 Unity。
* 导入资产并设置场景。
* 空间网格、手部网格和帧率计数器的可视化。

## <a name="instructions"></a>说明

### <a name="create-new-unity-project"></a>创建新的 Unity 项目

1. 启动 Unity。
2. 选择“新建”  。
![第 1 课 第 1 章 第 2 步](images/Lesson1Chapter1Step2.JPG)
3. 输入项目名称（例如“MixedRealityBase”）。
![第 1 课 第 1 章 第 3 步](images/Lesson1Chapter1Step3.JPG)
4. 输入保存项目的位置。
![第 1 课 第 1 章 第 4 步](images/Lesson1Chapter1Step4.JPG)
5. 请确保将项目设置为“3D”  。
![第 1 课 第 1 章 第 5 步](images/Lesson1Chapter1Step5.JPG)
6. 单击“创建项目”  。
![第 1 课 第 1 章 第 6 步](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>配置用于 Windows Mixed Reality 的 Unity 项目

1. 通过转到“文件”>“生成设置”打开生成设置窗口。
![第 1 课 第 4 章 第 1 步](images/Lesson1Chapter4Step1.JPG)
2. 通过选择“通用 Windows 平台”切换到“通用 Windows 平台”，然后单击“切换平台”按钮切换平台。 在 HoloLens 2 上运行的应用必须是通用 Windows 平台 (UWP)。
![第 1 课 第 4 章 第 2 步](images/Lesson1Chapter4Step2.JPG)
3. 通过单击“生成窗口”中的播放机设置启用虚拟现实，然后在检查器面板中启用 XR 设置下的“支持虚拟现实”复选框，如下图所示。 请注意，可能需要将“生成设置”窗口拖动到旁边，以便查看检查器面板。 “支持虚拟现实”复选框也适用于混合现实/增强现实头戴显示设备，因为它指的是启用立体视觉（为每只眼睛呈现不同的图像）。![第 1 课 第 4 章 第 3 步](images/Lesson1Chapter4Step3.JPG)
4. 在同一个检查器面板中，检查“发布设置”下是否启用了“功能”部分中的“空间感知”复选框。 通过“空间感知”功能，我们可以在混合现实设备（如 HoloLens 2）上可视化空间映射网格。 可以在检查器面板的“XR 设置”上方和“其他设置”下方找到发布设置。
![第 1 课 第 4 章 第 4 步](images/Lesson1Chapter4Step4.JPG)

> 注意：虽然本节未使用到，但你可能希望启用其他一些常用功能，包括麦克风（用于语音命令）和 InternetClient（用于连接到需要网络连接的服务）

### <a name="import-the-mixed-reality-toolkit"></a>导入混合现实工具包

1. 下载[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) unity 包并将其保存到电脑上的文件夹中。

2. 通过单击“资产”>“导入”>“自定义包”导入混合现实工具包。 找到步骤 1 中下载的混合现实工具包并将其打开以开始导入过程。 导入过程需几分钟。
    ![第 1 课 第 2 章 第 2a 步](images/Lesson1Chapter2Step2a.JPG) ![第 1 课 第 2 章 第 2b 步](images/Lesson1Chapter2Step2b.JPG)

3. 在下一个弹出窗口中，单击“导入”以开始导入混合现实工具包。 请确保选中所有项目，如图所示。 如果看到一个弹出式对话框，提示应用混合现实工具包默认设置，请单击“应用”。
    ![第 1 课 第 2 章 第 3 步](images/Lesson1Chapter2Step3.JPG) ![第 1 课 第 2 章 第 3 步](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>配置混合现实工具包

1. 通过从菜单栏中选择“混合现实工具包”>“配置”，配置混合工具包。 如果在导入混合现实工具包后没有看到此菜单项，请重启 Unity。
![第 1 课 第 3 章 第 1 步](images/Lesson1Chapter3Step1.JPG)
2. 现在，你的场景具有来自混合现实工具包的一些新项目和修改。 单击“文件”>“另存为”，使用其他名称保存场景，并为场景命名，例如 BaseScene。 将场景保存到项目资产文件夹中的“场景”文件夹中，以保持场景的有序性。
![第 1 课 第 3 章 第 2a 步](images/Lesson1Chapter3Step2a.JPG)
![第 1 课 第 3 章 第 2b 步](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>在设备上构建应用程序

1. 如果在前面的部分关闭了“生成设置”窗口，请转到“文件”>“生成设置”，再次打开生成设置窗口。
    ![第 1 课 第 5 章 第 1 步](images/Lesson1Chapter5Step1.JPG)

2. 通过单击“添加打开的场景”按钮，确保要尝试的场景位于“生成中的场景”列表中。

3. 按“生成”按钮开始生成过程。
    ![第 1 课 第 5 章 第 3 步](images/Lesson1Chapter5Step3.JPG)

4. 为应用程序创建一个新文件夹并为其命名。 在下图中，创建了一个名为“应用”的文件夹以包含该应用程序。 单击“选择文件夹”，开始生成新创建的文件夹。 生成完成后，可以关闭 Unity 中的“生成设置”窗口。 
    ![第 1 课 第 5 章 第 4 步](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果生成失败，尝试再次生成或重启 Unity 并再次生成。 如果看到错误，如“错误：CS0246 = 找不到类型或命名空间名称“XX”（是否缺少 using 指令或程序集引用？）”，可能需要安装 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. 生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。 双击“MixedRealityBase.sln”解决方案（或相应的名称，如果你使用项目的替代名称）在 Visual Studio 中打开解决方案文件。

  > 注意：请务必打开新创建的文件夹（即“应用”文件夹，如果遵循前面步骤中的命名约定），因为在该文件夹之外会有一个类似名称的 .sln 文件，不能将其与“生成”文件夹内的 .sln 文件混淆。 

![第 1 课 第 5 章 第 5 步](images/Lesson1Chapter5Step5.JPG)

  > 注意：如果 Visual Studio 要求你安装新组件，请花一点时间确保按照[“安装工具”页面](install-the-tools.md)中的说明安装所有必备组件

6. 使用 USB 电缆将 HoloLens 2 插入电脑。 虽然这些课程说明假设你将使用 HoloLens 2 设备部署测试，但你也可以选择部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或选择创建[应用包以进行旁加载](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 在生成到设备之前，请确保设备处于开发者模式。 如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。 如果需要启用开发者模式或与 Visual Studio 配对，请按照[这些说明](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)进行操作。

8. 通过选择“发布”配置和“ARM”体系结构，配置 Visual Studio 以生成到 HoloLens 2。
    ![第 1 课 第 5 章 第 8 步](images/Lesson1Chapter5Step8.JPG)

9. 最后一步是通过选择“调试”>“在不调试的情况下启动”来生成到你的设备。 选择“在不调试的情况下启动”将导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中显示调试信息。 这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。 也可以选择“生成”>“部署解决方案”以部署到你的设备，而无需自动启动应用程序。
    ![第 1 课 第 5 章 第 9 步](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>祝贺你

你现在已经部署了第一个 HoloLens 2 应用程序。 当你四处走动时，应该看到空间网格覆盖了 HoloLens 2 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。 这些只是混合现实工具包中开箱即用的一些基本功能。 在接下来的课程中，你将开始为场景添加更多的内容和交互性，以便充分探索 HoloLens 2 和混合现实工具包的功能。

>注意：[第 5 课](mrlearning-base-ch5.md)将介绍如何使用语音命令切换帧速率计数器

[下一课：用户界面、手跟踪和混合现实工具包配置](mrlearning-base-ch2.md)
