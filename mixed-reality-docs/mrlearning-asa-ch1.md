---
title: Azure 空间锚点教程-1。 Azure 空间定位点入门
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: fb7074849c5a07a95b370b5bfa75228fac36ba5b
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105967"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Azure 空间定位点入门

欢迎使用 HoloLens 2 教程的第二个模块。 在开始之前，请确保所有[先决条件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)都已完成。 如果尚未完成第一个、[基本模块](mrlearning-base.md)，则建议先完成该模块。 如果从新的 Unity 项目开始，请在[基本模块](mrlearning-base.md)中执行新的项目创建步骤。 

## <a name="objectives"></a>目标

* 了解通过 Azure 空间锚点与 HoloLens 2 一起开发的基础知识

* 创建、上传和下载空间锚

## <a name="instructions"></a>说明

### <a name="downloading-and-importing-assets"></a>下载和导入资产
开始之前，请先下载并导入以下资产：

[Azure 空间锚1.1。0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[HoloLens2. GettingStarted. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

[HoloLens2. AzureSpatialAnchor. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchor-v2.1.0.0/Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage)

[混合现实工具包基础包2.1。0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. 在项目中创建新场景。 右键单击场景文件夹，单击 "创建"，然后单击 "场景"。 将新场景命名为 "ASALearningModule"。

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. 双击 "ASALearningmodule" 场景，查看一些预定义的项以及新场景。 
3. 为混合现实开发配置场景。 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 注意：你可能会看到一个弹出对话框，用于选择[混合现实工具包的配置文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。 双击名为*DefaultHoloLens2ConfigurationProfile*的配置文件，将其选中。

4. 选择 MRTK 的文件时，请选择 "DefaultMixedRealityToolkitConfigurationProfile"。

> 注意：如果你有自己的配置文件，可以改为随意使用该配置文件。
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

现在为混合现实配置场景。 请确保保存场景（用 control/command + S 执行此操作，或单击 "文件"，然后单击 "保存"）。 

5. 导入在步骤1中下载的[Azure 空间锚 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity 包。 为此，请单击 "资产"，然后向下移动到 "导入包"。 然后单击 "自定义包 ..."您的计算机文件将打开。 当他们执行此操作时，请在 Azure 空间锚定包的保存位置，并将其选中。 然后单击 "打开"。

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

此时将显示一个弹出窗口，其中提供工具和设置的列表，并询问您要导入的内容。 选择***所有***可用选项，然后单击 "导入"。

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> 注意：请耐心等待，导入需要几分钟时间。 

6. 接下来导入[HoloLens2。 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) 。 与步骤5非常类似，返回到 Unity，单击 "资产"，并将鼠标悬停在 "导入包" 上。 单击 "自定义包 ..."您的计算机文件将再次出现。 中转到存储基本模块资产包的位置。 并选择它。 单击“打开”。

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> 注意：此模块后面可能需要更多资产。 按照以下步骤导入从此点开始提到的任何资产。 

7. 导入[ASA module pack 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage) ，使用与导入其他先前包相同的步骤。

### <a name="configuring-your-scene"></a>配置场景

在本部分中，我们将 prototyping 和脚本添加到场景中，以创建一系列按钮，这些按钮演示了本地锚点和 Azure 空间锚点在应用程序中的行为方式。

8. 在 "项目" 选项卡上的 "资产" 文件夹下，单击 "ASAmoduleAssets"。 选择后，将看到两个 prototyping： ButtonParent 和 ParentAnchor。

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. 将这两个 prototyping 拖放到场景中。 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

注意：将 ButtonParent 添加到场景后，将显示一个弹出窗口，要求你导入 TMP 资产。 导入 "TMP Essentials"。 此后，如果在场景中看到任何大字体文本，请删除 ButtonParent 对象，并从 ASAmoduleAssets 文件夹再次添加它。

注意：如果要检查 HoloLens 中的调试日志，则为。 可以将 DebugWindow prefab 从 ASAModuleAssets 文件夹拖放到场景中。 在 DebugWindow 检查器面板中附加 DebugWindowMessaging 脚本，并启用 "调试窗口已启用" 选项。 然后，将 DebugWindow prefab 拖放到 DebugText 空字段。 你还可以根据需要调整 DebugWindow 位置。

10. 为了放大场景，请双击层次结构中的父定位点，并调整视图，以查看所需的整个场景。 目前，ParentAnchor 是一个仅用于演示目的的彩色多维数据集。 最终，我们将隐藏该多维数据集，并将内容作为 ParentAnchor 的子元素。 

11. 现在，让我们配置用于操作场景的按钮。 为此，请展开 "ButtonParent" prefab，并注意多个标记的按钮。 这些按钮是从 MRTK 的 PressableButton prototyping 中创建的。 了解有关如何从[基本模块](mrlearning-base-ch2.md)创建 PressableButton 的详细信息。 若要运行这些按钮，我们需要添加一个事件，当用户按下或选择各个按钮时将触发该事件。 

- 对于名为 "StartAzureSession" 的按钮，请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。 将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 StartAzureSession （）方法，如以下屏幕截图所示。
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- 对于按钮名称 StopAzureSession，请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。 将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 StopAzureSession （）方法。

- 对于名为 "CreateAnchor" 的按钮，请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。 将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 CreateAzureAnchor （）方法。  **然后，将 ParentAnchor 再次拖动到下一个空的 "游戏对象" 字段中。**

- 对于名为的按钮，请开始查找定位点，在 "按下" 事件触发器和 On Click 事件触发器下，创建一个新事件。 将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 FindAzureAnchor （）方法。

- 对于名为 "DeleteAzureAnchor" 的按钮，请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。 将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 DeleteAzureAnchor （）方法。  

- 对于名为的按钮，删除本地定位点，在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。 将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 RemoveLocalAnchor （）方法。 **然后，将 ParentAnchor 对象再次拖动到下一个空 "游戏对象" 字段中。**

12. 若要设置 Azure 空间锚，请转到 "资产" 文件夹中的 AzureSpatialAnchorsPlugin 文件夹，然后导航到示例-> 资源-> AzureSpatialAnchorsDemoConfig 文件。 在 "检查器" 面板中，添加之前创建的 Azure 帐户 ID 和帐户密钥。 如果尚未创建或没有，请遵循[先决条件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)。 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a>构建并演示基本应用程序

现在，你的场景已配置为演示 Azure 空间锚的基本知识，我们将构建并演示 Azure 空间锚的基本行为。 

1. 转到 "文件 > 生成设置"，再次打开 "生成设置" 窗口。
    ![mrlearning-ch1-3-步骤 1](images/mrlearning-asa-ch1-3-step1.jpg)
2. 单击 "添加打开的场景" 按钮，确保你想要尝试的场景处于 "生成" 列表中的场景中。
3. 验证平台是否设置为通用 Windows 平台。 否则，请将其设置为相同的。
4. 按 "播放机设置" 按钮，并单击 "发布设置"。 在 "功能" 下，启用： Internet、Internet 客户端服务器、专用网络客户端服务器、可移动存储、网络摄像机、麦克风和空间感知。
5. 在相同的播放机设置中，选择 "XR 设置"，并选择 "支持的虚拟现实"。
6. 按“生成”按钮开始生成过程。
   ![mrlearning-ch1-3-步骤 6](images/mrlearning-asa-ch1-3-step6.jpg)
7. 为应用程序创建一个新文件夹并为其命名。 在下图中，创建了一个包含应用程序的名称为 "应用程序" 的文件夹。 单击 "选择文件夹"，开始生成到新创建的文件夹。 完成生成后，可以关闭 Unity 中的 "生成设置" 窗口。

    ![mrlearning-ch1-step7](images/mrlearning-asa-ch1-3-step7.jpg)

    > 注意：如果生成失败，请尝试重新生成或重新启动 Unity 并再次生成。 如果你看到错误，如 "错误： CS0246 = 无法找到类型或命名空间名称" XX "（是否缺少 using 指令或程序集引用？）。 你可能需要安装[Windows 10 SDK （10.0.18362.0）](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) 


8. 即使在成功生成后，你可能会收到如下所示的错误，但如果生成成功，则可以忽略这些错误，并继续执行后续步骤。

    ![mrlearning-ch1-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. 生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。 双击 "MixedRealityBase" 解决方案或对应的名称。 如果你在 Visual Studio 中为你的项目使用了替代名称来打开解决方案文件。

    > 注意：如果遵循前面步骤中的命名约定，请确保打开新创建的文件夹（即 App 文件夹），因为在该文件夹之外，不会与 build 文件夹内的 .sln 文件相混淆的名称相同。

    ![mrlearning-ch1-step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > 注意：如果 Visual Studio 要求安装新组件，请花点时间确保所有必备组件都按照["安装工具" 页中的](install-the-tools.md)特定方式进行安装


9. 使用 USB 电缆将 HoloLens 2 插入电脑。 虽然这些课程说明假设你要使用 HoloLens 2 设备部署测试，但你也可以选择将部署到[hololens 2 模拟器](using-the-hololens-emulator.md)，或选择创建[用于旁加载的应用程序包](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

10. 在生成到设备之前，请确保设备处于开发者模式。 如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。 如果需要使用 Visual Studio 启用开发人员模式或配对，请遵循[这些说明](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)。

11. 将 Visual Studio 配置为通过选择 "发布" 配置和 ARM 体系结构生成到 HoloLens 2。

    ![mrlearning-ch1-step11](images/mrlearning-asa-ch1-3-step11.jpg)


12. 最后一步是通过选择 "调试" > "开始执行（不调试）" 来生成设备。 选择 "启动但不调试" 会导致应用程序在成功生成时立即在设备上启动，而不会在 Visual Studio 中显示调试信息。 这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。 你还可以选择 "生成" > 部署解决方案以部署到设备，而无需应用程序自动启动。

    ![mrlearning-ch1-step12](images/mrlearning-asa-ch1-3-step12.jpg)

>注意： Azure 空间锚点使用 internet 保存和加载定位点数据，因此，在测试 ASA 应用之前，请确保你的设备已连接到 internet。

13. 按照说明操作。 
    当应用程序在你的设备上运行时，请按照屏幕上的说明进行操作。 按以下步骤对应的场景按钮。 如果按照前面的步骤中所述添加了 "调试" 窗口，则可以查看单个按钮按下的反馈以及与 Azure 空间定位点相关的各个操作的进度。

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. 启动空间锚点会话。
    
    2. 将多维数据集移到其他位置。
    
    3. 将 Azure 空间锚点保存在多维数据集的位置。
    
    4. 停止 Azure 空间锚点会话。
    
    5. 删除多维数据集上的本地定位点，以允许用户移动多维数据集。
    
    6. 将多维数据集移到其他位置。
    
    7. 启动 Azure 空间锚点会话。
    
    8. 查找 Azure 空间锚。 
    你应返回到创建定位点时将其放入的原位置。
    
    9. 删除 Azure 空间锚。
    
    10. 停止 Azure 会话。

### <a name="anchoring-an-experience"></a>定位体验

在前面的部分中，已了解 Azure 空间锚的基础知识。 我们已使用多维数据集来表示父游戏对象并将其可视化。 在本部分中，你将了解如何通过将整个体验放置为 ParentAnchor 对象的子项来定位整个体验。 在此示例中，我们使用在[基础模块第6课](mrlearning-base-ch6.md)中创建的农历模块程序集演示应用程序。

1. 搜索 "火箭启动器 Complete" prefab，并将其作为对象的子级拖到层次结构中，如下图所示。

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 定位模块程序集体验，使多维数据集仍公开，如下图所示。 在应用程序中，用户可以通过移动多维数据集来重新定位整个体验。 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> 注意：有各种用户体验流程可用于重定位体验，包括使用按钮切换环绕体验的边界框、使用重定位对象（如此步骤中使用的多维数据集）、位置和旋转gizmos 等。

## <a name="congratulations"></a>祝贺
在本教程中，已了解 Azure 空间锚的基础知识。 本课程提供多个按钮，使你可以浏览启动和停止 Azure 会话所需的各种步骤，以及在单个设备上创建、上传和下载 azure 锚。 在下一课中，我们将了解如何将 Azure 定位 Id 保存到 HoloLens 2 以便检索，甚至在应用程序重新启动后也是如此。 在此系列中，你还将了解如何在多个设备之间传输定位点 Id 以实现空间对齐，并了解多用户共享会话，作为共享教程的一部分。

[下一课： 2. 保存、检索和共享 Azure 空间锚](mrlearning-asa-ch2.md)

