---
title: Azure Speech Services 教程-1。 集成和使用语音识别与脚本
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 05728cf090b2e998e92980816943a2c3bef18dfb
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334290"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. 集成和使用语音识别与脚本

## <a name="overview"></a>概述

本教程将创建一个混合现实应用程序，该应用程序探讨如何将 Azure 认知服务语音 SDK 与 HoloLens 2 一起使用。 完成本系列教程后，你将能够使用设备的麦克风实时转录语音，将语音翻译成其他语言，并利用语音 SDK 的意图功能来理解使用化.

## <a name="objectives"></a>目标

* 了解如何将 Azure Speech SDK 集成到 HoloLens 2 应用程序
* 了解如何使用语音命令
* 了解如何使用语音到文本功能

## <a name="prerequisites"></a>先决条件

>[!TIP]
>如果尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。

* 使用安装了正确的[工具](install-the-tools.md)配置的 WINDOWS 10 电脑
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一些基本C#编程功能
* [为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备

>[!IMPORTANT]
>本系列教程需要<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a> ，建议的版本是 unity 2019.1.14。 这将取代上述先决条件中所述的任何 Unity 版本要求或建议。

## <a name="getting-started"></a>入门

1. 启动 Unity，并创建一个新项目。 输入项目名称语音 SDK 学习模块。 选择保存项目的位置。 单击 "创建项目"。

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    >请确保将模板设置为 "三维"，如上图所示。

2. 下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation 包版本 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) 并将其保存到电脑上的文件夹。 将包导入 Unity 项目。 有关如何执行此操作的详细说明，请参阅[入门教程-第2课。正在初始化项目和首个应用程序](mrlearning-base-ch1.md)。

3. 下载并导入用于 Unity 资产包的 Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage) 。 通过单击 "资产"，选择 "导入包"，然后选择 "自定义包" 来导入语音 SDK 包。 找到先前下载的语音 SDK 包，并打开它以开始导入过程。

    ![mrlearning-speech-ch1-1-step3a .png](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-speech-ch1-1-step3b .png](images/mrlearning-speech-ch1-1-step3b.png)

4. 在下一个弹出窗口中，单击 "导入" 以开始导入语音 SDK 包。 确保选中所有项，如下图所示。

    ![mrlearning-speech-ch1-1-step4 .png](images/mrlearning-speech-ch1-1-step4.png)

5. 单击[此链接](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)，下载语音 SDK 模块资产包（也称为 Lunarcom 包）。 Lunarcom 资产包是为本课系列开发的资产和脚本的集合，旨在展示 Azure 语音 SDK 的实际使用情况。 它是一个语音命令终端，最终将与[入门教程-第7课中开发的农历模块组装体验进行交互。创建农历模块示例应用程序](mrlearning-base-ch6.md)。

6. 按照导入混合现实工具包和语音 SDK 所用的类似步骤，将 Lunarcom 资产包导入 Unity 项目。

7. 配置混合现实工具包（MRTK）。

    为此，请在窗口顶部单击 "混合现实工具包" 面板，然后选择 "添加到场景" 并配置。

    ![mrlearning-speech-ch1-1-step7a .png](images/mrlearning-speech-ch1-1-step7a.png)

    在出现的弹出窗口中，选择 "DefaultHoloLens2ConfigurationProfile" 以使其成为混合现实工具包的活动配置文件。

    ![mrlearning-speech-ch1-1-step7b .png](images/mrlearning-speech-ch1-1-step7b.png)

8. 你的场景现在有多个 MRTK 中的新项。 单击 "文件"，然后单击 "另存为"，然后将场景命名为 "SpeechScene"，以其他名称保存场景。

    >[!NOTE]
    >如果在将 MRTK 添加到项目中后按下了场景，而不进入播放模式，则可能需要重新启动 Unity。

9. 在场景层次结构中选择 MixedRealityToolkit 对象后，单击 "检查器" 面板中的 "复制 & 自定义"，以打开 "克隆配置文件" 弹出窗口。 在 "克隆配置文件" 弹出窗口中，为自定义配置文件输入合适的名称，例如 "自定义 HoloLens2ConfigurationProfile"。 单击 "克隆" 创建自定义配置文件，并将其设置为活动配置文件。

    ![mrlearning-speech-ch1-1-step9 .png](images/mrlearning-speech-ch1-1-step9.png)

10. 同时，在 "检查器" 面板（在层次结构中选择 MixedRealityToolkit 对象）中，通过取消选中 "启用诊断系统" 右侧的框来禁用诊断系统。

    ![mrlearning-speech-ch1-1-step10 .png](images/mrlearning-speech-ch1-1-step10.png)

11. 在本教程中，我们将使用用于语音识别和脚本的输入语音命令。 我们会克隆输入配置文件，以更改语音设置。

    在场景层次结构中，MixedRealityToolkit 对象仍处于选中状态，单击 "检查器" 面板中的 "小型克隆" 按钮，打开克隆配置文件弹出窗口。 在 "克隆配置文件" 弹出窗口中，为自定义配置文件输入合适的名称，例如 "自定义 HoloLens2InputSystemProfile"，然后单击 "克隆" 以创建自定义输入系统配置文件，并将其设置为活动配置文件。

    ![mrlearning-speech-ch1-1-step11 .png](images/mrlearning-speech-ch1-1-step11.png)

12. 克隆输入配置文件后，展开 "语音" 部分并按照上一步骤中所述的相同过程来克隆语音命令配置文件。

    ![mrlearning-speech-ch1-1-step12 .png](images/mrlearning-speech-ch1-1-step12.png)

13. 在语音部分下，转到 "常规设置"，并将 "开始行为" 更改为手动启动。

    ![mrlearning-speech-ch1-1-step13 .png](images/mrlearning-speech-ch1-1-step13.png)

14. 在 "项目" 面板中，展开 "Lunarcom" 文件夹并将 Lunarcom_Base "prefab" 拖动到场景层次结构。

    ![mrlearning-speech-ch1-1-step14 .png](images/mrlearning-speech-ch1-1-step14.png)

15. 选择层次结构中的 Lunarcom_Base 对象，并确保将位置设置为 x = 0、y = 0、z = 0，以及将旋转设置为 x = 0、y = 0 和 z = 0。 将刻度设置为 read x = 0.008，y = 0.008，z = 0.01。

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. 单击 "添加组件"，搜索并选择 "Lunarcom 控制器"。 此脚本包含在步骤6中导入的 Lunarcom 资产包中。

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. 若要将应用程序连接到 Azure 认知服务，必须为语音服务输入订阅密钥（也称为 API 密钥）。 按照[此处](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)的说明获取免费订阅密钥。 获取订阅密钥后，请在 "检查器" 面板中的 LunarcomController 组件的 "语音服务 API 密钥" 字段中输入该密钥，如下图所示。

18. 将订阅密钥注册到 "检查器" 面板中 LunarcomController 组件的 "语音服务区域" 字段时，请输入所选的区域。 例如，对于美国西部，请在 "westus" 中键入。

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. 在层次结构中，通过单击其左侧的箭头展开 "Lunarcom_Base" 对象。 然后对其子对象 "终端" 执行相同的操作，如下图所示。

20. 选择 Lunarcom_Base 时，请在 "检查器" 面板中单击 "Lunarcom"，并将其从层次结构拖到 "LunarcomController" 组件中的 "输出文本" 槽，如下图所示。

21. 对终端槽执行相同的操作，并对连接轻型控制器槽执行相同的操作。

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. 单击 "检查器" 面板中 "LunarcomController" 脚本的 "Lunarcom 按钮" 部分旁边的箭头，将大小更改为3。 按 Enter 或 Return。 这将导致显示三个新元素字段。

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. 在层次结构中单击其旁边的箭头，展开 "Lunarcom" 按钮，并使用上述相同过程，分别将 Mic、卫星和火箭 gameobject 拖到元素0、1和2引用，并在检查器面板。

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. 选择层次结构中的 Lunarcom_Base "对象。 单击 "检查器" 面板中的 "添加组件"，搜索并选择 Lunarcom 语音识别器。 重复相同的步骤添加 Lunarcom 唤醒词识别器。

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. 在 "唤醒单词" 槽中，键入 "激活终端"。 在 "消除字" 槽中，键入 "消除终端"。

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="build-your-application-to-your-device"></a>在设备上构建应用程序

1. 转到 "文件 > 生成设置"，再次打开 "生成设置" 窗口。

    ![images/mrlearning-ch1-2-步骤1](images/mrlearning-speach-ch1-2-step1.jpg)

2. 通过单击“添加打开的场景”按钮，确保要尝试的场景位于“生成中的场景”列表中。

3. 按 "播放机设置" 按钮，并单击 "发布设置"。 在 "功能" 下，启用： Internet、Internet 客户端服务器、专用网络客户端服务器、麦克风和空间感知。

4. 在相同的播放机设置中，选择 "XR 设置"，并选择 "支持的虚拟现实"。

5. 按“生成”按钮开始生成过程。

    ![mrlearning-ch1-步骤5](images/mrlearning-speach-ch1-2-step5.jpg)

6. 为应用程序创建一个新文件夹并为其命名。 在下图中，创建了一个名为“应用”的文件夹以包含该应用程序。 单击“选择文件夹”，开始生成新创建的文件夹。 生成完成后，可以关闭 Unity 中的“生成设置”窗口。

    ![mrlearning-ch1-步骤6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    >如果生成失败，尝试再次生成或重启 Unity 并再次生成。 如果你看到错误，如 "错误： CS0246 = 无法找到类型或命名空间名称" XX "（是否缺少 using 指令或程序集引用？）"，你可能需要安装[Windows 10 SDK （10.0.18362.0）](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)

7. 生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。 双击 ".sln" 解决方案文件，在 Visual Studio 中打开解决方案文件。

    >[!NOTE]
    >如果遵循前面步骤中的命名约定，则请确保打开新创建的文件夹（即 "App" 文件夹），因为该文件夹外的命名 .sln 文件与 build 文件夹内的 .sln 文件不同。 

    ![mrlearning-ch1-step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    >如果 Visual Studio 要求你安装新组件，请确保按照["安装工具" 页中的](install-the-tools.md)指定安装所有必备组件。

8. 使用 USB 电缆将 HoloLens 2 插入电脑。 虽然这些课程说明假设你将使用 HoloLens 2 设备部署测试，但你也可以选择部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或选择创建[应用包以进行旁加载](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

9. 在生成到设备之前，请确保设备处于开发者模式。 如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。 如果需要启用开发者模式或与 Visual Studio 配对，请按照[这些说明](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)进行操作。

10. 通过选择“发布”配置和“ARM”体系结构，配置 Visual Studio 以生成到 HoloLens 2。

    ![mrlearning-ch1-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. 最后一步是通过选择“调试”>“在不调试的情况下启动”来生成到你的设备。 选择“在不调试的情况下启动”将导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中显示调试信息。 这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。 也可以选择“生成”>“部署解决方案”以部署到你的设备，而无需自动启动应用程序。

    ![mrlearning-ch1-step11.JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a>祝贺

你已在应用程序中设置了语音识别，由 Azure 提供支持。 运行应用程序以确保所有功能和功能都正常工作。 首先说到你在步骤22中键入的唤醒字词，然后激活终端。 选择麦克风按钮启动语音识别。 开始说话。 你会在说话时看到你的转录。 再次按下麦克风按钮以停止语音识别。 说关闭终端，隐藏 Lunarcom 终端。 在下一课中，您将学习如何使用设备支持的语音识别来实现 Azure 语音 SDK 不可用的情况，因为 HoloLens 2 处于脱机状态。

[下一教程： 2. 为本地语音到文本转换添加脱机模式](mrlearning-speechSDK-ch2.md)
