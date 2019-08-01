---
title: 入门教程-2。 初始化项目和首个应用程序
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: f003bebf51859122b679162f41797bff1becd3fb
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702063"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化项目和首个应用程序

在第一课中, 您将了解到混合现实工具包 (MRTK) 必须提供的某些功能, 启动 HoloLens 2 的第一个应用程序, 并将其部署到设备。

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

1. 转到 "文件 > 生成设置", 打开 "生成设置" 窗口。
![第 1 课 第 4 章 第 1 步](images/Lesson1Chapter4Step1.JPG)
2. 通过选择通用 Windows 平台切换到通用 Windows 平台。 单击 "切换平台" 按钮切换平台。 在 HoloLens 2 上运行的应用程序需要与通用 Windows 平台 (UWP) 兼容。
![第 1 课 第 4 章 第 2 步](images/Lesson1Chapter4Step2.JPG)
3. 通过单击 "生成" 窗口中的 "播放机设置" 启用虚拟现实, 然后在 "检查器" 面板中的 "XR 设置" 下启用 "支持虚拟现实" 复选框, 如下图所示。 请注意, 您可能需要将 "生成设置" 窗口拖出, 以查看检查器面板。 "受支持的虚拟现实" 复选框还适用于混合现实和增加的现实耳机, 因为它指的是启用 stereoscopic 视觉效果 (每个眼睛呈现不同的图像)。![第 1 课 第 4 章 第 3 步](images/Lesson1Chapter4Step3.JPG)
4. 在相同的检查器面板中, 确保在 "发布设置" 下启用 "功能" 部分中的 "空间感知" 复选框。 空间感知使我们能够在混合现实设备上 (如 HoloLens 2) 直观显示空间映射网格。 发布设置可在 "检查器" 面板中的 "XR 设置" 和 "其他设置" 下找到。
![第 1 课 第 4 章 第 4 步](images/Lesson1Chapter4Step4.JPG)

> 注意：虽然本部分未使用, 但你可能想要启用的其他一些常见功能包括用于语音命令的麦克风, 以及用于连接到需要网络连接的服务的 InternetClient。

### <a name="import-the-mixed-reality-toolkit"></a>导入混合现实工具包

1. 下载[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage)Unity 包, 并将其保存到电脑上的文件夹中。

2. 通过单击“资产”>“导入”>“自定义包”导入混合现实工具包。 找到步骤 1 中下载的混合现实工具包并将其打开以开始导入过程。 导入过程需几分钟。
    ![第 1 课 第 2 章 第 2a 步](images/Lesson1Chapter2Step2a.JPG) ![第 1 课 第 2 章 第 2b 步](images/Lesson1Chapter2Step2b.JPG)

3. 在下一个弹出窗口中, 单击 "导入" 以开始导入混合现实工具包。 确保所有项都已选中, 如图所示。 如果你看到一个弹出对话框, 要求应用混合现实工具包默认设置, 请单击 "应用"。
    ![第 1 课 第 2 章 第 3 步](images/Lesson1Chapter2Step3.JPG) ![第 1 课 第 2 章 第 3 步](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>配置混合现实工具包

1. 通过从菜单栏中选择 "混合现实工具包" > "配置" 来配置 MRTK。 如果在导入混合现实工具包后没有看到此菜单项，请重启 Unity。
  ![第 1 课 第 3 章 第 1 步](images/Lesson1Chapter3Step1.JPG)

  > 注意:你可能会看到一个弹出对话框, 要求为混合现实工具包选择一个配置文件。 如果是, 请选择 "确定", 然后选择名为 "DefaultMixedRealityToolkitConfigurationProfile" 的配置文件。

2. 你的场景将在 MRTK 中有多个新项和修改。 单击 "文件" > "另存为", 将场景保存在其他名称下, 并为场景指定名称, 例如 BaseScene。 通过将场景保存到项目的 "资产" 文件夹中的场景文件夹, 使场景保持井然有序。
  ![第 1 课 第 3 章 第 2a 步](images/Lesson1Chapter3Step2a.JPG)
  ![第 1 课 第 3 章 第 2b 步](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>在设备上构建应用程序

1. 如果关闭了前面几节中的 "生成设置" 窗口, 请通过转到 "文件 > 生成设置", 重新打开 "生成设置" 窗口。
    ![第 1 课 第 5 章 第 1 步](images/Lesson1Chapter5Step1.JPG)

2. 单击 "添加打开的场景" 按钮, 确保你想要尝试的场景处于 "生成" 列表中的场景中。

3. 按“生成”按钮开始生成过程。
    ![第 1 课 第 5 章 第 3 步](images/Lesson1Chapter5Step3.JPG)

4. 为应用程序创建一个新文件夹并为其命名。 在下图中, 创建了一个包含应用程序的名称为 "应用程序" 的文件夹。 单击 "选择文件夹", 开始生成到新创建的文件夹。 完成生成后, 可以关闭 Unity 中的 "生成设置" 窗口。 
    ![第 1 课 第 5 章 第 4 步](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果生成失败，尝试再次生成或重启 Unity 并再次生成。 如果看到错误, 如 "错误:CS0246 = 找不到类型或命名空间名称 "XX" (是否缺少 using 指令或程序集引用？)。 如果是这样, 则可能需要安装[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. 生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。 双击 "MixedRealityBase" 解决方案或相应的名称 (如果你使用的是项目的备用名称) 以在 Visual Studio 中打开解决方案文件。

  > 注意:如果遵循前面步骤中的命名约定, 请确保打开新创建的文件夹 (即 App 文件夹), 因为在该文件夹外, 不会与 build 文件夹内的 .sln 文件混淆的名称相同的 .sln 文件。 

![第 1 课 第 5 章 第 5 步](images/Lesson1Chapter5Step5.JPG)

  > 注意:如果 Visual Studio 要求你安装新组件，请花一点时间确保按照[“安装工具”页面](install-the-tools.md)中的说明安装所有必备组件

6. 将 HoloLens 2 连接到您的 PC。 尽管这些说明假设你要使用 HoloLens 2 设备部署测试, 但你也可以选择将部署到[hololens 2 模拟器](using-the-hololens-emulator.md), 或选择创建[用于旁加载的应用包](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 在生成到设备之前，请确保设备处于开发者模式。 如果这是你首次部署到 HoloLens 2, 则 Visual Studio 可能会要求你将 HoloLens 2 与 PIN 配对。 如果需要启用开发者模式或与 Visual Studio 配对，请按照[这些说明](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)进行操作。

8. 通过选择 "发布" 配置和 ARM 体系结构, 将 Visual Studio 配置为生成到 HoloLens 2。
    ![第 1 课 第 5 章 第 8 步](images/Lesson1Chapter5Step8.JPG)

9. 最后一步是通过选择 "调试" > "开始执行 (不调试)" 来生成设备。 如果选择 "启动但不调试", 则会导致应用程序在成功生成后立即开始, 但不会在 Visual Studio 中显示调试信息。 这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。 你还可以选择 "生成" > 部署解决方案以部署到设备, 而无需应用程序自动启动。
    ![第 1 课 第 5 章 第 9 步](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>祝贺

现在, 你已部署了第一个 HoloLens 2 应用程序。 浏览时, 应该会看到一个空间网格, 其中包含已由 HoloLens 2 检测到的所有表面。 此外, 你应该看到手指和抓手指, 以及用于跟踪应用程序性能的帧速率计数器。 这些只是混合现实工具包中开箱即用的一些基本功能。 在接下来的课程中, 您开始向场景添加更多内容和交互性, 以便您可以充分探索 HoloLens 2 的功能和混合现实工具包。

>注意:[第 5 课](mrlearning-base-ch5.md)将介绍如何使用语音命令切换帧速率计数器

[下一课：3.创建用户界面并配置混合现实工具包](mrlearning-base-ch2.md)
