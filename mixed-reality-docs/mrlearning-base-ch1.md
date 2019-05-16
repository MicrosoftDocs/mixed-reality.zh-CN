---
title: MR 学习基本模块的项目初始化并将其第一个应用程序
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity 中，教程，hololens 混合的现实
ms.openlocfilehash: 4546e4c8d973cbd4ce4190a974a4de9c01197e56
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730941"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>MR 学习基本模块的项目初始化并将其第一个应用程序

在此第一课中，您将学习一些混合现实工具包具有产品/服务、 启动第一个应用程序对于 HoloLens 2 中，并将其部署到设备的功能。

## <a name="objectives"></a>目标

* 优化 HoloLens 开发 Unity。
* 导入资产和设置场景。
* 空间网格、 手网格和帧速率计数器的可视化效果。

## <a name="instructions"></a>说明

### <a name="create-new-unity-project"></a>创建新的 Unity 项目

1. 启动 Unity。
2. 选择**新建**。
![Lesson1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)
3. 输入项目名称 （例如"MixedRealityBase")。
![Lesson1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)
4. 输入用于保存你的项目的位置。
![Lesson1 Chapter1 Step4](images/Lesson1Chapter1Step4.JPG)
5. 请确保项目设置为**3D**。
![Lesson1 Chapter1 Step5](images/Lesson1Chapter1Step5.JPG)
6. 单击**创建项目**。
![Lesson1 Chapter1 Step6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>针对 Windows Mixed Reality 配置 Unity 项目

1. 通过文件打开生成设置窗口 > 生成设置。
![Lesson1 第 4 章步骤 1](images/Lesson1Chapter4Step1.JPG)
2. 通过选择"通用 Windows 平台"切换到"通用 Windows 平台"，然后单击"切换平台"按钮以切换平台。 HoloLens 2 上运行的应用需要通用 Windows 平台 (UWP)。
![Lesson1 第 4 章步骤 2](images/Lesson1Chapter4Step2.JPG)
3. 通过单击生成窗口中的播放机设置中启用虚拟现实，然后在检查器面板中启用的 XR 设置下的"虚拟现实支持"复选框，如下图中所示。 请注意，您可能需要将"生成设置"窗口开拖动以查看检查器面板。 "虚拟现实支持"复选框也适用于混合现实 / AR 耳机因为它是指启用立体视觉 （呈现不同的映像的每只眼睛。）![Lesson1 第 4 章步骤 3](images/Lesson1Chapter4Step3.JPG)
4. 在相同的检查器窗格中，检查启用的功能部分中的"空间感知"复选框，在发布设置下。 空间感知将使我们能够可视化空间映射网格上的混合的现实设备如 HoloLens 2。 在检查器窗格中，上面的"XR 设置"和"其他设置。"下找到的发布设置
![Lesson1 第 4 章步骤 4](images/Lesson1Chapter4Step4.JPG)

> 注意：尽管不使用在本部分中，可能想要启用的一些其他常见的功能包括麦克风 （适用于语音命令） 和 InternetClient （适用于连接到需要网络连接的服务）

### <a name="import-the-mixed-reality-toolkit"></a>导入的混合的现实工具包

1. 下载[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage)unity 包，并在您的 PC 上将其保存到一个文件夹。

2. 通过单击资产上导入混合现实工具包包 > 导入 > 自定义包。 查找在步骤 1 中下载的混合现实工具包程序包并打开它，以开始导入进程。 请等待几分钟让导入进程。
    ![Lesson1 第 2 章 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 第 2 章 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. 在下一步的弹出窗口中，单击"导入"以开始导入混合现实工具包。 确保选中所有项，如图所示。 如果看到一个弹出对话框，询问要应用混合现实工具包默认设置，请单击"应用"。
    ![Lesson1 第 2 章 Step3](images/Lesson1Chapter2Step3.JPG) ![Lesson1 第 2 章步骤 3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>配置混合的现实工具包

1. 通过选择从菜单栏混合现实工具包来配置混合工具包 > 配置。 如果导入的混合的现实工具包后看不到此菜单项，请重新启动 Unity。
![Lesson1 第 3 章步骤 1](images/Lesson1Chapter3Step1.JPG)
2. 您的场景将现在包含几个新项和修改从混合现实工具包。 通过单击文件中保存您的场景下不同的名称 > 另存为并为您的场景提供一个名称，例如，BaseScene。 请通过将其保存到你的项目的 Assets 文件夹中的"场景"文件夹组织您的场景。
![Lesson1 第 3 章 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Lesson1 第 3 章 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>生成你的设备到应用程序

1. 如果关闭前一节生成设置窗口中，打开生成设置窗口再次转到文件 > 生成设置。
    ![Lesson1 第 5 章步骤 1](images/Lesson1Chapter5Step1.JPG)

2. 请确保你想要尝试的场景是在"生成中的场景"列表中通过单击"添加打开场景"按钮。

3. 按生成按钮以开始生成过程。
    ![Lesson1 第 5 章步骤 3](images/Lesson1Chapter5Step3.JPG)

4. 创建并命名为应用程序的新文件夹。 下面的文件夹名称的图中"应用"已创建以包含应用程序。 单击"选择文件夹"以开始新创建的文件夹中生成。 完成生成后，可能会关闭在 Unity 中的"生成设置"窗口。 
    ![Lesson1 第 5 章步骤 4](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果生成失败，尝试再次生成或重新启动 Unity 并再次生成。 如果你看到错误，如"错误：CS0246 = 找不到"XX"键入或命名空间名称 (是否缺少 using 指令或程序集引用？)"，则需要安装[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. 在生成完成后，打开新创建的文件夹包含新生成的应用程序文件。 双击"MixedRealityBase.sln"解决方案 （或相应的名称，如果使用你的项目的替代名称） 在 Visual Studio 中打开解决方案文件。

  > 注意：请务必打开新创建的文件夹 （即，"应用"文件夹中，如果从前面的步骤执行以下命名约定），因为会有外部是不会与生成文件夹中的.sln 文件混淆，该文件夹的类似名称的.sln 文件。 

![Lesson1 第 5 章步骤 5](images/Lesson1Chapter5Step5.JPG)

  > 注意：如果 Visual Studio 会要求你安装新组件，请花一些时间来确保为安装了所有必备组件中指定["安装工具"页](install-the-tools.md)

6. 插入到您的 PC 使用 USB 电缆 HoloLens 2。 虽然这些课程说明假设将部署使用 HoloLens 2 设备进行测试，但是您还可选择将部署到[HoloLens 2 模拟器](using-the-hololens-emulator.md)或选择创建[的旁加载应用包](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 生成前向你的设备，请确保在设备处于开发人员模式。 如果这是你第一次将部署到 HoloLens 2，Visual Studio 可能会要求你进行配对使用 pin 将 HoloLens 2。 请按照[这些说明](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)如果你需要启用开发人员模式或与 Visual Studio 配对。

8. 通过选择"发布"配置和"ARM"体系结构为构建到 HoloLens 2 配置 Visual Studio。
    ![Lesson1 第 5 章执行步骤 8](images/Lesson1Chapter5Step8.JPG)

9. 最后一步是向你的设备通过选择生成调试 > 启动但不调试。 选择"启动但不调试"将导致立即启动后成功生成，但不出现在 Visual Studio 中的调试信息的情况下在设备上的应用程序。 这也意味着，而无需停止应用程序在 HoloLens 2 上运行你的应用程序时，你可以断开连接您的 USB 电缆。 您还可以选择生成 > 部署解决方案，而无需自动启动该应用程序部署到你的设备。
    ![Lesson1 第 5 章步骤 9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>恭喜 ！

现在，你现在已部署首个 HoloLens 2 应用程序。 奔波，你应该看到空间网格覆盖已识别的 HoloLens 2 的所有曲面。 此外，您应查看的指示器上双手和手动跟踪的手指和帧速率计数器，用于对应用程序性能密切关注。 这些是只需几个基础部分，包括默认情况下，使用混合现实工具包。 在完成的课程，您将开始您的场景，添加更多的内容和交互功能，使您完全可以浏览 HoloLens 2 和混合现实工具包的功能。

>注意：您将了解如何切换使用语音命令中的帧速率计数器[第 5 课](mrlearning-base-ch5.md)

[下一课：用户界面，手动跟踪和混合现实工具包配置](mrlearning-base-ch2.md)
