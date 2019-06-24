## <a name="lesson-4"></a>第 4 课

在第 4 章，我们将探讨意向的语音服务的功能。 我们将我们 Azure LUIS 门户设置、 设置我们目的/实体/谈话、 发布我们的意图资源，我们 Unity 应用连接到我们的意图资源，并使我们第一次意向 API 调用。

1. 允许您的计算机以启用听写，以执行此操作，请转到 Windows 设置，选择"隐私"，然后"speech，"并最后"墨迹书写和键入"开启语音服务和键入建议。

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> 注意： 有关如何执行此操作在 Mac/Macbook 上的信息，请单击[此处](linkgoeshere)。

2. 登录到[Azure 门户](https://portal.azure.com/)。 你登录后，单击创建资源，并搜索"语言理解"，并按 enter。

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. 选择创建按钮，以创建此服务的实例。 命名你的项目"Speech_SDK_Learning_Module"，然后选择"现用现付。"

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. 选择你的区域。  在本教程中，选择"（美国） West US"。 定价层，然后选择"F0"。 现在单击"创建"（位于左下角） 来创建资源。

   >  注意： 一旦你单击"创建"，必须要等待的时间来创建服务，这可能需要一分钟的时间。

5. 创建资源后，通知将显示在门户中。 单击此通知，然后选择"转到资源。"

6. 从"LUIS API"服务的"快速启动"页，导航到第一步，捕捉"密钥"，并单击"密钥"（也可以在此通过单击蓝色的超链接"密钥，"在下图中所示）。 此时会显示你的服务，"密钥"。 保存密钥中的一个的副本，以便可以更高版本的应用中使用它。

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. 返回部分 2b 下的"快速启动"页，单击"语言理解门户"（在上图中所示） 重定向到的网页将用来创建新服务，LUIS 应用程序中。

> 注意：一旦达到"语言理解门户"，您可能需要登录后，如果您尚不，使用 Azure 门户相同的凭据。 如果这是你首次使用 LUIS，您需要向下滚动到底部的欢迎页上，要找到并单击"创建 LUIS"应用程序按钮。

8. 登录后，单击我的应用 （如果您当前不是那一节中）。 然后可以单击创建新应用。 新应用命名为"语音 SDK 学习模块。" 将"语音 SDK 学习模块"添加到描述字段。 然后单击"完成"。

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> 注意：如果您的应用程序应以了解不同于英语语言，应将"区域性"更改为合适的语言。

9. 单击"生成"位于右上角。

10. 在左侧的应用程序资产下, 选择"意向"，然后单击"创建新意向"并将其"PressButton。"命名 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> 注意： 务必要使用的意图和使用在本教程中，因为 Lunarcom 应用将引用它们的实体按名称的名称。  对于其他项目，命名约定可以是你选择的任何内容。 
>
> 注意： 你现在应当有 2 个意向-"PressButton"和"None。

11. 在左侧的应用程序资产下, 选择"实体"并单击"创建新实体"和其命名为"Action"，保留为"简单"。 实体类型

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. 再次单击"创建新实体"和其命名为"目标"，也保留为"简单"实体类型。

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. 在左侧的应用程序资产下, 选择"意向"，然后单击你在步骤 10 中创建的"PressButton"目标。

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. 在右侧"查看选项"下拉列表中单击并选择"显示实体值"。 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)单击"输入示例..." 文本框中。 然后，输入以下言辞： 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. 在右侧"查看选项"下拉列表中单击并选择"显示实体名称"。

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. 确保每 10 个语音样本添加具有以下实体标签在下列位置 1。)单击标记有误的字词，并在弹出窗口中，选择"删除标签"和 2。）单击上应标记为的单词，并在弹出窗口中，选择相应的标签。

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. 现在，如果发布模型，单击右上角的"训练"。 然后，完成处理后，请在右上角单击"Test"。

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. 输入在"选择启动按钮"，在文本框中。

> 注意： 我们没有添加"选择"为一个操作中任何我们语音样本-但如果单击"检查"，该模型识别"选择"为操作实体。
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. 现在，单击右上角"发布"。 确保在下拉列表中显示"生产"，然后单击"发布"上的弹出窗口。 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. 发布后的绿色条应出现在页面顶部。  单击绿色栏转到"管理"页上。 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. 请单击"密钥和终结点上"在"应用程序设置"下的左侧。 然后，将下拉列表"发布到"设置为"生产"。 设置的时间区域以匹配自己，并选中复选框以包括所有预测的意向评分。 最后，单击"分配资源。"

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. 从第一个下拉列表中，选择租户和订阅名称下拉列表中选择"即用即付"。 在 LUIS 的资源名称，选择我们在步骤 1-5 中创建的资源。 然后，单击"分配资源。" 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> 注意： 请确保复制并保存与我们只需分配，以便进行下一节的轻松访问的资源关联的终结点 URL。
>
> 注意： 对于租户名称，将您的公司或创建此应用程序配置文件。

23. 现在，在 Unity 中打开新的应用，然后选择 Lunarcom_Base 对象层次结构中。 检查器面板中单击"添加组件"，搜索并选择"LunarcomIntentRecognizer。"

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. 在检查器面板中的"LunarcomIntentRecognizer"Luis 终结点字段中，输入在第 22 步中保存的终结点 URL。 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  注意：在检查器面板中的"LunarcomOfflineRecognizer"组件，请确保"禁用"选择了"SimulateOfflineMode"否则为测试该程序将不起作用。 

25. 在 Unity 编辑器中按播放按钮并单击火箭按钮以启动意图识别。 说话短语"选择启动火箭按钮"。

>  注意：应用程序识别所需的函数和激活火箭按钮。
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>祝贺

正式介绍了如何将语音命令添加从该的语音 SDK 程序 ！ 现在您的程序可以识别所有类型的变体的语音的命令。 它进行测试和有与它的一些乐趣 ！

[下一课：第 5 课语音 SDK](placeholderlink)

