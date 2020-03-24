---
title: Azure 语音服务教程 - 4. 设置意向和自然语言理解
description: 请完成本课程来了解如何在混合现实应用程序中实施 Azure 语音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b2342e7d0d502af2787ca311d18a44f8726acf2d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028458"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4.设置意向和自然语言理解

本教程探讨 Azure 语音服务的意向识别。 使用意向识别可以在我们的应用程序中配备 AI 驱动的语音命令，在其中，即使用户讲出非特定的语音命令，系统也仍能识别其意向。

## <a name="objectives"></a>目标

* 了解如何在 LUIS 门户中设置意向、实体和言语
* 了解如何在应用程序中实现意向和自然语言理解

## <a name="preparing-the-scene"></a>准备场景

在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 意向识别器(脚本)”组件添加到 Lunarcom 对象中：   

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

在“项目”窗口中导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件” > “RocketLauncher”文件夹，将“RocketLauncher_Complete”预制件拖放到“层次结构”窗口中，并将其放在相机前面的适当位置，例如：     

* 变换**位置** X = 0，Y = -0.4，Z = 1
* 变换**位置** X = 0，Y = 90，Z = 0

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

在“层次结构”窗口中再次选择“Lunarcom”对象，展开“RocketLauncher_Complete” > “Button”对象，并将“Button”对象的每个子对象分配到相应的“Lunar Launcher 按钮”字段中：     

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a>创建 Azure 语言理解资源

在本部分，你将为要在下一部分创建的语言理解智能服务 (LUIS) 应用创建 Azure 预测资源。

登录到 <a href="https://portal.azure.com" target="_blank">Azure</a> 并单击“创建资源”。  然后搜索并选择“语言理解”： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

单击“创建”按钮创建此服务的实例： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

在“创建”页上，单击“预测”选项并输入以下值： 

* 对于“订阅”，如果你有试用版订阅，请选择“免费试用”，否则请选择其他订阅之一  
* 对于“资源组”，请单击“新建”链接，输入适当的名称（例如 *MRKT-Tutorials*），然后单击“确定”   

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> 截至编写本文时，无需创建创作资源，因为在下一部分创建语言理解智能服务 (LUIS) 时，系统会在 LUIS 中自动生成一个创作试用密钥。

> [!TIP]
> 如果 Azure 帐户中已有另一个适当的资源组（例如，如果已完成 [Azure 空间定位点](mrlearning-asa-ch1.md)教程），则可以使用此资源组，而无需创建新资源组。

仍在“创建”页上，输入以下值：

* 对于“名称”，请输入服务的适当名称，例如 *MRTK-Tutorials-AzureSpeechServices* 
* 对于“预测位置”，请选择与应用用户的实际位置靠近的位置，例如“(美国)美国西部”  
* 对于“预测定价层”，根据本教程的目的，请选择“F0 (每秒 5 次调用，每月 1 万次调用)”  

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

接下来，转到“查看 + 创建”选项卡，复查详细信息，然后单击页面底部的“创建”按钮，以创建资源和新资源组（如果配置为创建资源组）：  

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> 单击“创建”按钮后，必须等待服务创建完成，这可能需要几分钟时间。

资源创建过程完成后，将看到消息“部署完成”： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a>创建语言理解智能服务 (LUIS)

在本部分，你将创建一个 LUIS 应用，配置并训练其预测模型，然后将其连接到在上一步骤中创建的 Azure 预测资源。

具体而言，你将创建以下意向：如果用户讲出要执行某项操作，该应用将对场景中的三个红色按钮之一（具体取决于用户引用的按钮）触发 Interactable.OnClick() 事件。

例如，如果用户讲出“继续发射火箭”，则该应用将预测出“继续”表示应执行某项“操作”，而“目标”Interactable.OnClick() 事件发生在“发射”按钮上。     

若要实现此目的，请执行以下主要步骤：

1. 创建 LUIS 应用
2. 创建意向
3. 创建示例言语
4. 创建实体
5. 将实体分配到示例言语
6. 训练、测试并发布应用
7. 将 Azure 预测资源分配到应用

### <a name="1-create-a-luis-app"></a>1.创建 LUIS 应用

使用在上一部分创建 Azure 资源时所用的同一用户帐户登录到 <a href="https://www.luis.ai" target="_blank">LUIS</a>，选择所在的国家/地区，然后同意使用条款。 在下一步骤中看到“链接 Azure 帐户”的提示时，请选择“继续使用试用密钥”，以改用 Azure 创作资源。  

> [!NOTE]
> 如果你已注册 LUIS 但创作试用密钥已过期，可以参阅[迁移到 Azure 资源创作密钥](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring)文档，将 LUIS 创作资源切换到 Azure。

登录后，导航到“我的应用”页，然后单击“创建新应用”并在“创建新应用”弹出窗口中输入以下值：   

* 对于“名称”，请输入适当的名称，例如 *MRTK Tutorials - AzureSpeechServices* 
* 对于“区域性”，请选择“英语”  
* 对于“说明”，请选择性地输入适当的说明 

然后单击“完成”按钮创建新应用： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

创建新应用后，你将转到该应用的“仪表板”页： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a>2.创建意向

在“仪表板”页上，导航到“生成”>“应用资产”>“意向”页，然后单击“创建新意向”，并在“创建新意向”弹出窗口中输入以下值：   

* 对于“意向名称”，请输入 **PressButton** 

然后单击“完成”按钮创建新意向： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> 在本教程中，Unity 项目将按名称（即“PressButton”）引用此意向。 因此，为意向指定完全相同的名称极其重要。

创建新意向后，你将转到该意向的页面：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a>3.创建示例言语

将以下示例言语添加到 **PressButton** 意向的“示例言语”列表中： 

* 激活发射顺序
* 显示位置提示
* 启动发射顺序
* 按下位置提示按钮
* 给予提示
* 按下发射按钮
* 我需要提示
* 按下重置按钮
* 重置体验的时间
* 继续发射火箭

添加所有示例言语后，PressButton 意向页应如下所示：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> 在本教程中，Unity 项目将引用词语“提示”、“重置”和“发射”。 因此，以完全相同的方式拼写这些词语极其重要。

### <a name="4-create-entities"></a>4.创建实体

从 PressButton 意向页导航到“生成”>“应用资产”>“实体”页，然后单击“创建新实体”，并在“创建新实体”弹出窗口中输入以下值：   

* 对于“实体名称”，请输入 **Action** 
* 对于“实体类型”，请选择“简单”  

然后单击“完成”按钮创建新实体： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

**重复**上述步骤创建名为 **Target** 的另一个实体，因此现在有名为 Action 和 Target 的两个实体：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> 在本教程中，Unity 项目将按名称（即“Action”和“Target”）引用这些实体。 因此，为实体指定完全相同的名称极其重要。

### <a name="5-assign-entities-to-the-example-utterances"></a>5.将实体分配到示例言语

从“实体”页导航回到 **PressButton** 意向页。

返回到 PressButton 意向页后，依次单击单词“继”和“续”，然后从上下文弹出菜单中选择“Action (简单)”，将“继续”标记为 **Action** 实体值：    

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

短语“继续”现在定义为 **Action** 实体值。  如果将鼠标光标悬停在 Action 实体名称上，可以看到关联的 Action 实体值：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> 上图中标签下方的红线表示尚未预测实体值，在下一部分训练模型时将解决此问题。

接下来单击词语“发射”，然后从上下文弹出菜单中选择“Target (简单)”，将“发射”标记为 **Target** 实体值：   

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

词语“发射”现在定义为 **Target** 实体值。  如果将鼠标光标悬停在 Target 实体名称上，可以看到关联的 Target 实体值：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

PressButton 意向示例言语“继续发射火箭”现已配置为按如下所示进行预测：

* 意向：PressButton
* Action 实体：继续
* Target 实体：发射

**重复**上述两步过程，将 Action 和 Target 实体标签分配到每个示例言语，请记住，应将以下词语标记为 **Target** 实体：

* **提示**（针对 Unity 项目中的 HintsButton）
* **提示**（针对 Unity 项目中的 HintsButton）
* **重置**（针对 Unity 项目中的 ResetButton）
* **发射**（针对 Unity 项目中的 LaunchButton）

标记所有示例言语后，PressButton 意向页应如下所示：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

若要通过另一种方式仔细检查是否分配了正确的实体，请单击“视图选项”菜单，然后将视图切换为“显示实体值”：  

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

现在，在将视图设置为显示实体值后，可将鼠标光标悬停在标记的单词和短语上，以快速验证分配的实体名称：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a>6.训练、测试并发布应用

若要训练应用，请单击“训练”按钮并等待训练过程完成： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> 在上图中可以发现，所有标签下面的红线都已删除，这表示已预测所有实体值。 另外可以看到，“训练”按钮左侧的状态图标颜色已从红色变为绿色。

处理完训练后，单击“测试”按钮，然后键入“继续发射火箭”并按 Enter 键：  

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

处理测试言语后，单击“检查”以查看测试结果： 

* 意向：PressButton（98.5% 确定性）
* Action 实体：继续
* Target 实体：发射

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

若要发布应用，请单击右上方的“发布”按钮，然后在“选择发布槽和设置”弹出窗口中，选择“生产”并单击“发布”按钮：    

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

等待发布过程完成：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a>7.将 Azure 预测资源分配到应用

导航到“管理”>“应用程序设置”>“Azure 资源”页： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

在“Azure 资源”页上，单击“添加预测资源”按钮，并在“将资源分配到应用”弹出窗口中选择以下值：  

* 对于“租户名称”，请选择你的租户名称 
* 对于“订阅名称”，请选择前面在[创建 Azure 语言理解资源](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)时使用的同一订阅 
* 对于“LUIS 资源名称”，请选择前面在[创建 Azure 语言理解资源](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)时创建的预测资源 

然后单击“分配资源”按钮，将 Azure 预测资源分配到应用： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

分配资源后，Azure 资源页应如下所示：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a>将 Unity 项目连接到 LUIS 应用

在“管理”>“应用程序设置”>“Azure 资源”页上，单击“复制”图标复制“示例查询”：   

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

返回到 Unity 项目，在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，找到“Lunarcom 意向识别器(脚本)”组件，并按如下所述对其进行配置：  

* 在“LUIS 终结点”字段中，粘贴在上一步骤中复制的“示例查询”：  

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a>测试和改善意向识别

若要在 Unity 编辑器中直接使用意向识别，必须允许开发计算机使用听写。 若要验证此设置，请打开 Windows 的“设置”，然后选择“隐私” > “语音”，并确保启用“在线语音识别”：    

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

如果现在进入“游戏”模式，可以先按火箭按钮来测试意向识别。 假设计算机上配备了麦克风，当你讲出第一个示例言语“继续发射火箭”时，将会看到 LunarModule 发射到了太空： 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

尝试所有**示例言语**，然后尝试**示例言语的一些变体**，以及一些**随机言语**。

接下来，返回到 <a href="https://www.luis.ai" target="_blank">LUIS</a> 并导航到“生成”>“改善应用性能”>“查看终结点言语”页，使用**切换**按钮从默认的“实体视图”切换到“标记视图”，然后查看言语：  

* 在“言语”列中，根据需要更改和删除分配的标签，使之与意向相符 
* 在“对齐的意向”列中，检查意向是否正确 
* 在“添加/删除”列中，单击绿色的勾选按钮添加言语，或单击红色的 X 按钮删除言语 

检查所需数目的言语后，单击“训练”按钮以重新训练模型，然后单击“发布”按钮重新发布更新的应用：  

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> 如果某个终结点言语与 PressButton 意向不一致，但你希望模型知道该言语不包含意向，可将“对齐的意向”更改为“无”。

**重复**此过程任意次，以改善应用模型。

## <a name="congratulations"></a>祝贺

现已在项目中包含了 AI 驱动的语音命令，即使用户没有讲出准确的命令，应用程序也能识别用户的意向。 请在设备上运行该应用程序，以确保功能正常。
