---
title: Azure 语音服务教程-4。 设置意向和自然语言理解
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 8805fa6410e882bce2f0fe8da780dfd5f794cc74
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553987"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. 设置意向和自然语言理解

在本课中，您将了解 Azure 语音服务的意图功能。 使用意向功能，您可以使用 AI 功能的语音命令为应用程序提供支持，用户可以在其中说出非特定的语音命令，并使系统理解其意图。 在本课程中，我们将设置 Azure LUIS 门户，设置我们的意向/实体/最谈话，发布我们的意图资源，将我们的 Unity 应用连接到我们的意图资源，并进行第一次意向 API 调用。

## <a name="objectives"></a>目标

- 了解如何在应用程序中设置意向和自然语言理解
- 了解如何设置 Azure 的 LUIS 门户
- 了解如何在 Azure 上设置意向、实体和最谈话

## <a name="instructions"></a>说明

1. 允许您的计算机启用听写。 为此，请转到 "Windows 设置"，选择 "隐私"，然后选择 "语音"，然后依次单击 "墨迹 & 键入" 和 "输入建议"。

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. 登录到[Azure 门户](https://portal.azure.com/)。 登录后，单击 "创建资源"，搜索 "语言理解"，然后单击 "Enter"。

    ![mrlearning-speech-ch4-1-step2 .png](images/mrlearning-speech-ch4-1-step2.png)

3. 单击 "**创建**" 按钮以创建此服务的实例。

    ![mrlearning-speech-ch4-1-step3a .png](images/mrlearning-speech-ch4-1-step3a.png)

    为资源提供**名称**，例如，*语音-SDK-学习模块*。 对于 "**订阅**"，选择 "即用*即付*" 或 "*免费*"。 接下来，单击 **"新建" 链接创建**新的**资源组**，输入名称（例如，" *HoloLens-2-资源组*"），然后单击 **"确定"** 按钮。

    ![mrlearning-speech-ch4-1-step3b .png](images/mrlearning-speech-ch4-1-step3b.png)

4. 选择**创作位置**和**运行时位置**。 出于本教程的目的，请使用 *（美国） "美国西部*"，然后选择 "**创作" 定价层**和 "**运行时" 定价层**的*F0 （每秒5个调用，每月10000个调用）* 。 最后，单击 "**创建**" 按钮以创建资源，以及新资源组。

    ![mrlearning-speech-ch4-1-step4 .png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    >单击 "创建" 按钮后，必须等待创建服务，这可能需要几分钟时间。

5. 资源创建过程完成后，你将看到**部署已完成**的消息。

    ![mrlearning-speech-ch4-1-step5 .png](images/mrlearning-speech-ch4-1-step5.png)

6. 使用相同的用户帐户登录到[语言理解智能服务（LUIS）](https://www.luis.ai/)门户，选择你的国家/地区，并同意使用条款。

    >[!NOTE]
    >到达语言理解门户后，你可能需要登录（如果尚未登录），其凭据与 Azure 门户相同。 如果这是你第一次使用 LUIS，则需要向下滚动到 "欢迎" 页的底部，查找并单击 "创建 LUIS" 应用按钮。

7. 登录后，单击 "我的应用" （如果当前不在该部分中）。 然后，可以单击 "创建新应用"。 将新应用命名为 "语音 SDK 学习模块"。 同时将 "语音 SDK 学习模块" 添加到 "说明" 字段。 然后单击 "完成"。

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    >如果你的应用程序应了解不同于英语的语言，则应将 "Culture" 改为适当的语言。

8. 单击右上方的 "生成"。

9. 在左侧的 "应用资产" 下，选择 "方法"，然后单击 "创建新意向" 并将其命名为 "PressButton"。

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    >使用本教程中使用的意向和实体的名称很重要，因为 Lunarcom 应用程序将按名称引用它们。

    >[!NOTE]
    >现在应有2个意向-"PressButton" 和 "None"。

10. 在左侧的 "应用资产" 下，选择 "实体"，单击 "新建实体"，将其命名为 "Action"，并将实体类型保留为 "Simple"。

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. 再次单击 "创建新实体" 并将其命名为 "Target"。 将实体类型保留为 "简单"。

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. 在左侧的 "应用资产" 下，选择 "方法"，然后单击你在步骤10中创建的 "PressButton" 意向。

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. 单击右侧的 "查看选项" 下拉列表，然后选择 "显示实体值"。

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    单击 "输入示例 ..." 文本框中。 然后输入以下最谈话：

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. 单击右侧的 "查看选项" 下拉列表，然后选择 "显示实体名称"。

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. 确保10最谈话中的每一个都在以下位置有1个实体标签。）单击网文的词，然后在弹出窗口中选择 "删除标签" 和2。）单击应标记为的单词，然后在弹出窗口中选择相应的标签。

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. 现在，若要发布模型，请单击右上方的 "训练"。 完成处理后，单击右上方的 "测试"。

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. 在文本框中输入 "选择启动按钮"。

    >[!NOTE]
    >我们未将 "select" 添加为最谈话中任何一项的操作，但如果单击 "检查"，则模型被识别为 "选择" 作为操作实体。
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. 单击右上方的 "发布"。 确保下拉列表中显示 "生产"，并在弹出窗口中单击 "发布"。

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. 发布后，页面顶部会显示一个绿色栏。 单击绿色条以查看 "管理" 页。

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. 在左侧的 "应用程序设置" 下，单击 "密钥和终结点"。 然后，将下拉 "发布到" 设置为 "生产"。 设置要匹配的时区，并选中复选框以包括所有预测意向分数。 最后，单击 "分配资源"。

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. 从第一个下拉列表中选择 "租户"，然后在 "订阅名称" 下拉列表中选择 "即用即付"。 在 "LUIS 资源名称" 下，选择前面在步骤1-5 中创建的资源。 然后，单击 "分配资源"。

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    >请确保复制并保存与我们刚刚分配的资源相关联的终结点 URL，以便在下一部分可以轻松访问该 URL。

    >[!NOTE]
    >对于租户名称，请将为此应用程序创建的公司或配置文件放入其中。

22. 现在，请在 Unity 中打开新应用，并选择层次结构中的 Lunarcom_Base 对象。 单击 "检查器" 面板中的 "添加组件"，搜索并选择 "LunarcomIntentRecognizer"。

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. 在 "检查器" 面板中的 "LunarcomIntentRecognizer" 的 "Luis 终结点" 字段中，输入你在步骤21中保存的终结点 URL。

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    >在 "检查器" 面板中的 "LunarcomOfflineRecognizer" 组件中，请确保已为 "SimulateOfflineMode" 选择 "禁用"，否则测试程序将不起作用。

24. 在项目窗口中，导航到 "资产" > "MRTK"。GettingStarted > Prototyping > RocketLauncher 文件夹中，将 RocketLauncher_Complete prefab 拖到 "层次结构" 窗口，并将其放置在 Lunarcom_Base 对象的前面。

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing01.png)

25. 在 "层次结构" 窗口中，选择 "Lunarcom_Base" 对象并找到 "Lunarcom 意向识别器（脚本）" 组件，然后展开 "RocketLauncher_Complete" > "按钮对象，并将每个按钮对象分配给相应的农历启动器按钮定义域.

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing02.png)

26. 按 Unity 编辑器中的 "播放" 按钮，然后单击 "火箭" 按钮，开始意图识别。 Utter "选择启动火箭" 按钮。

    >[!NOTE]
    >应用已识别所需的函数并激活了 "火箭" 按钮。
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>祝贺你

在本课中，您学习了如何添加 AI 功能的语音命令。 现在，你的程序可以识别用户的意图，即使它们不 utter 精确的语音命令也是如此！
