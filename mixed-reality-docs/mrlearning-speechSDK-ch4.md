---
title: MR SpeechSDK Module-语音识别和脚本
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b434b9c79a702067a9c3db6fb25b0f75cdc6030d
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485778"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4.设置意向和自然语言理解

在本课程中, 我们将探讨 Azure 语音服务的目的功能。 使用意向功能, 我们可以使用 AI 功能的语音命令为应用程序提供支持, 其中用户可以说出非特定的语音命令, 并使系统能够理解其意图。 在本课程中, 我们将设置 Azure LUIS 门户, 设置我们的意向/实体/最谈话, 发布我们的意图资源, 将我们的 Unity 应用连接到我们的意图资源, 并进行第一次意向 API 调用。

## <a name="objectives"></a>目标

- 了解如何在应用程序中设置意向和自然语言理解
- 了解如何设置 Azure 的 LUIS 门户
- 了解如何在 Azure 上设置意向、实体和最谈话

## <a name="instructions"></a>说明
1. 允许计算机启用听写, 若要执行此操作, 请转到 "Windows 设置", 选择 "隐私", 然后选择 "语音", 最后 "墨迹 & 键入", 然后打开语音服务和键入建议。

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. 登录到[Azure 门户](https://portal.azure.com/)。 登录后, 单击 "创建资源", 搜索 "语言理解", 然后单击 "enter"。

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. 选择 "创建" 按钮, 创建此服务的实例。 将项目命名为 "Speech_SDK_Learning_Module", 并选择 "即用即付"。

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. 选择区域。  对于本教程, 请选择 "(美国) 美国西部"。 然后选择 "F0" 作为 "定价层"。 现在, 单击 "创建" (位于左下角) 以创建资源。

>  注意: 单击 "创建" 后, 必须等待创建服务, 这可能需要一分钟时间。

5. 创建资源后, 门户中将显示一条通知。 单击此通知, 然后选择 "中转到资源"。

6. 从 "LUIS API" 服务的 "快速入门" 页中, 导航到第一步, 获取 "密钥", 然后单击 "密钥" (也可以通过单击下图中显示的蓝色超链接 "键" 来实现此目的)。 这会显示你的服务 "密钥"。 保存其中一个密钥的副本, 以便以后可以在应用中使用它。

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. 返回到第2b 节中的 "快速入门" 页, 单击 "语言理解门户" (如上图所示), 将重定向到 LUIS 应用程序中将用于创建新服务的网页。

> 注意:到达 "语言理解门户" 时, 你可能需要登录 (如果尚未登录), 其凭据与 Azure 门户相同。 如果这是你第一次使用 LUIS, 则需要向下滚动到 "欢迎" 页的底部, 查找并单击 "创建 LUIS" 应用按钮。

8. 登录后, 单击 "我的应用" (如果当前不在该部分中)。 然后, 可以单击 "创建新应用"。 将新应用命名为 "语音 SDK 学习模块"。 同时将 "语音 SDK 学习模块" 添加到 "说明" 字段。 然后单击 "完成"。

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> 纪录如果你的应用程序应了解不同于英语的语言, 则应将 "Culture" 改为适当的语言。

9. 单击右上方的 "生成"。

10. 在左侧的 "应用资产" 下, 选择 "方法", 然后单击 "创建新意向" 并将其命名为 "PressButton"。 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> 注意:使用本教程中使用的意向和实体的名称很重要, 因为 Lunarcom 应用程序将按名称引用它们。 
>
> 注意: 现在应有2个意向-"PressButton" 和 "None"。

11. 在左侧的 "应用资产" 下, 选择 "实体", 并单击 "创建新实体" 并将其命名为 "Action", 并将实体类型保留为 "Simple"。

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. 再次单击 "创建新实体" 并将其命名为 "Target", 并将实体类型保留为 "简单"。

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. 在左侧的 "应用资产" 下, 选择 "方法", 然后单击你在步骤10中创建的 "PressButton" 意向。

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. 单击右侧的 "查看选项" 下拉列表, 然后选择 "显示实体值"。 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)单击 "输入示例 ..." 工具箱. 然后输入以下最谈话: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. 单击右侧的 "查看选项" 下拉列表, 然后选择 "显示实体名称"。

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. 确保10最谈话中的每一个都在以下位置有1个实体标签。)单击网文的词, 然后在弹出窗口中选择 "删除标签" 和2。)单击应标记为的单词, 然后在弹出窗口中选择相应的标签。

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. 现在, 若要发布模型, 请单击右上方的 "训练"。 完成处理后, 单击右上方的 "测试"。

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. 在文本框中输入 "选择启动按钮"。

> 注意: 我们未将 "select" 添加为最谈话中任何一项操作, 但如果单击 "检查", 则模型将 "select" 识别为操作实体。
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. 现在, 单击右上方的 "发布"。 确保下拉列表中显示 "生产", 并在弹出窗口中单击 "发布"。 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. 发布后, 页面顶部会显示一个绿色栏。  单击绿色栏转到 "管理" 页。 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. 在左侧的 "应用程序设置" 下, 单击 "密钥和终结点"。 然后, 将下拉 "发布到" 设置为 "生产"。 设置要匹配的时区, 并选中复选框以包括所有预测意向分数。 最后, 单击 "分配资源"。

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. 从第一个下拉列表中选择 "租户", 然后在 "订阅名称" 下拉列表中选择 "即用即付"。 在 "LUIS 资源名称" 下, 选择前面在步骤1-5 中创建的资源。 然后, 单击 "分配资源"。 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> 注意:请确保复制并保存与我们刚刚分配的资源相关联的终结点 URL, 以便在下一部分可以轻松访问该 URL。
>
> 注意:对于租户名称, 请将为此应用程序创建的公司或配置文件放入其中。

23. 现在, 请在 Unity 中打开新应用, 并选择层次结构中的 Lunarcom_Base 对象。 单击 "检查器" 面板中的 "添加组件", 搜索并选择 "LunarcomIntentRecognizer"。

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. 在 "检查器" 面板中的 "LunarcomIntentRecognizer" 的 "Luis 终结点" 字段中, 输入在步骤22中保存的终结点 URL。 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  注意:在 "检查器" 面板中的 "LunarcomOfflineRecognizer" 组件中, 请确保已为 "SimulateOfflineMode" 选择 "禁用", 否则测试程序将不起作用。 

25. 按 Unity 编辑器中的 "播放" 按钮, 然后单击 "火箭" 按钮, 开始意图识别。 Utter "选择启动火箭" 按钮。

>  注意:应用已识别所需的函数并激活了 "火箭" 按钮。
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>祝贺

在本课中, 我们学习了如何添加 AI 功能的语音命令! 即使您的程序没有 utter 精确的语音命令, 也可以识别用户的意图。

