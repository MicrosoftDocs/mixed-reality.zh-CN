---
title: Azure Speech Services 教程-1。 集成和使用语音识别与脚本
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 501e8bc2e70248a4ca8a79f90d74d30129830701
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701954"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1.集成和使用语音识别与脚本

本教程将创建一个混合现实应用程序, 该应用程序探讨如何将 Azure 认知服务语音 SDK 与 HoloLens 2 一起使用。 完成本系列教程后, 你将能够使用设备的麦克风实时将语音转录到文本, 将语音翻译成其他语言, 并利用语音 SDK 的意图功能理解语音命令人工智能。

## <a name="objectives"></a>目标

- 了解如何将 Azure Speech SDK 集成到 HoloLens 2 应用程序
- 了解如何使用语音命令
- 了解如何使用语音到文本功能

## <a name="instructions"></a>说明

### <a name="getting-started"></a>入门

1. 启动 Unity, 并创建一个新项目。 输入项目名称语音 SDK 学习模块。 选择保存项目的位置。 然后单击 "创建项目"。

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> 注意:请确保将模板设置为 "三维", 如上图所示。

2. 下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage)Unity 包, 并将其保存到电脑上的文件夹中。 将包导入 Unity 项目。 有关如何执行此操作的详细说明, 请参阅[基本模块第1课](mrlearning-base-ch1.md)。 

3. 下载并导入用于 Unity 资产包的 Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage) 。 通过单击 "资产", 选择 "导入包", 然后选择 "自定义包" 来导入语音 SDK 包。 找到先前下载的语音 SDK 包, 并打开它以开始导入过程。 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. 在下一个弹出窗口中, 单击 "导入" 以开始导入语音 SDK 包。 请确保选中所有项, 如下图所示。

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. 通过单击[此链接](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2), 下载语音 SDK 模块资产包, 也称为 Lunarcom package。 Lunarcom 资产包是为本课系列开发的资产和脚本的集合, 旨在展示 Azure 语音 SDK 的实际使用情况。 它是一个语音命令终端, 最终将与[基本模块教程](mrlearning-base-ch6.md)中开发的农历模块组装体验进行交互。

6. 按照导入混合现实工具包和语音 SDK 所用的类似步骤, 将 Lunarcom 资产包导入 Unity 项目。
7. 配置混合现实工具包 (MRTK)。 为此, 请在窗口顶部单击 "混合现实工具包" 面板, 然后选择 "添加到场景" 并配置。

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. 你的场景现在有多个 MRTK 中的新项。 单击 "文件", 然后单击 "另存为", 然后将场景命名为 "SpeechScene", 以其他名称保存场景。 

> 注意:如果在将 MRTK 添加到项目中后按下了场景, 而不进入播放模式, 则可能需要重新启动 Unity。 

9. 在层次结构中选择 MixedRealityToolkit 对象后, 单击 "检查器" 面板中的 "复制" 和 "自定义"。

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. 同时, 在 "检查器" 面板 (在层次结构中选择 MixedRealityToolkit 对象) 中, 通过取消选中 "启用诊断系统" 右侧的框来禁用诊断系统。

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. 若要启用语音命令, 请选择要自定义的新创建的 MRTK 配置文件。 在本教程中, 我们将使用用于语音识别和脚本的输入语音命令。 允许克隆输入配置文件以更改语音设置。

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. 克隆输入配置文件后, 请转到语音命令并克隆语音命令。

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. 现在, 在 "语音命令" 下, 转到 "常规设置", 并将 "启动行为" 设置为 "手动启动"

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. 在 "项目" 面板中, 展开 "Lunarcom" 文件夹, 然后将 "Lunarcom_Base" prefab 拖到层次结构中。

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. 选择层次结构中的 Lunarcom_Base 对象, 并确保将位置设置为 x = 0、y = 0、z = 0, 以及将旋转设置为 x = 0、y = 0 和 z = 0。 将刻度设置为 read x = 0.008, y = 0.008, z = 0.01。

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. 单击 "添加组件", 搜索并选择 "LunarcomController"。 此脚本包含在步骤6中导入的 Lunarcom 资产包中。

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. 若要将应用程序连接到 Azure 认知服务, 必须为语音服务输入订阅密钥 (也称为 API 密钥)。 按照[此处](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started)的说明获取免费订阅密钥。 获取订阅密钥后, 请在 "检查器" 面板中的 LunarcomController 组件的 "语音服务 API 密钥" 字段中输入该密钥, 如下图所示。

18. 将订阅密钥注册到 "检查器" 面板中 LunarcomController 组件的 "语音服务区域" 字段时, 请输入所选的区域。 例如, 对于区域 "美国西部", 键入 "westus"

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. 在层次结构中, 单击 "Lunarcom_Base" 对象左侧的箭头将其展开。 然后对其子对象 "终端" 执行相同的操作, 如下图所示。

20. 选择 Lunarcom_Base 时, 在 "检查器" 面板中单击 "Lunarcom 文本" 并将其拖到 "LunarcomController" 组件中的 "输出文本" 槽, 如下图所示。

21. 对终端槽执行相同的操作, 并对连接轻型控制器槽执行相同的操作。

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. 单击 "检查器" 面板中 "LunarcomController" 脚本的 "Lunarcom 按钮" 部分旁边的箭头, 将大小更改为3。 按 Enter 或 Return。 这将导致显示三个新元素字段。

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. 在层次结构中单击其旁边的箭头, 展开 "Lunarcom" 按钮, 并使用上述相同过程, 分别将 Mic、卫星和火箭 gameobject 拖到元素0、1和2引用, 并在检查器面板。 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. 在层次结构中选择 "Lunarcom_Base" 对象。 单击 "检查器" 面板中的 "添加组件", 搜索并选择 "LunarcomWakeWordRecognizer"。

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. 在 "唤醒单词" 槽中, 键入 "激活终端"。 在 "消除字" 槽中, 键入 "消除终端"。

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a>在设备上构建应用程序

1. 转到 "文件 > 生成设置", 再次打开 "生成设置" 窗口。

![学习 Chapter5 步骤1](images/Lesson1Chapter5Step1.JPG)

2. 通过单击“添加打开的场景”按钮，确保要尝试的场景位于“生成中的场景”列表中。

3. 按“生成”按钮开始生成过程。

![学习 Chapter5 步骤3](images/Lesson1Chapter5Step3.JPG)

4. 为应用程序创建一个新文件夹并为其命名。 在下图中，创建了一个名为“应用”的文件夹以包含该应用程序。 单击“选择文件夹”，开始生成新创建的文件夹。 生成完成后，可以关闭 Unity 中的“生成设置”窗口。 

![学习 Chapter5 步骤4](images/Lesson1Chapter5Step4.JPG)

> 注意：如果生成失败，尝试再次生成或重启 Unity 并再次生成。 如果看到错误，如“错误：CS0246 = 找不到类型或命名空间名称“XX”（是否缺少 using 指令或程序集引用？）”，可能需要安装 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)

5. 生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。 双击 ".sln" 解决方案文件, 在 Visual Studio 中打开解决方案文件。

> 注意:请务必打开新创建的文件夹（即“应用”文件夹，如果遵循前面步骤中的命名约定），因为在该文件夹之外会有一个类似名称的 .sln 文件，不能将其与“生成”文件夹内的 .sln 文件混淆。 

![第 1 课 第 5 章 第 5 步](images/Lesson1Chapter5Step5.JPG)

> 注意:如果 Visual Studio 要求你安装新组件，请花一点时间确保按照[“安装工具”页面](install-the-tools.md)中的说明安装所有必备组件

6. 使用 USB 电缆将 HoloLens 2 插入电脑。 虽然这些课程说明假设你将使用 HoloLens 2 设备部署测试，但你也可以选择部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或选择创建[应用包以进行旁加载](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 在生成到设备之前，请确保设备处于开发者模式。 如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。 如果需要启用开发者模式或与 Visual Studio 配对，请按照[这些说明](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)进行操作。

8. 通过选择“发布”配置和“ARM”体系结构，配置 Visual Studio 以生成到 HoloLens 2。

![学习 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. 最后一步是通过选择“调试”>“在不调试的情况下启动”来生成到你的设备。 选择“在不调试的情况下启动”将导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中显示调试信息。 这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。 也可以选择“生成”>“部署解决方案”以部署到你的设备，而无需自动启动应用程序。

![学习 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>祝贺

你已在应用程序中设置了语音识别, 由 Azure 提供支持。 运行应用程序以确保所有功能和功能都正常工作。 首先说到你在步骤22中键入的唤醒字词, 然后激活终端。 选择麦克风按钮启动语音识别。 开始说话。 你会在说话时看到你的转录。 再次按下麦克风按钮以停止语音识别。 说关闭终端, 隐藏 Lunarcom 终端。 在下一课中, 我们将学习如何在 Azure 语音 SDK 由于 HoloLens 2 处于脱机状态而无法使用的情况下动态切换到使用设备支持的语音识别。

[下一教程:2.为本地语音到文本翻译添加脱机模式](mrlearning-speechSDK-ch2.md)

