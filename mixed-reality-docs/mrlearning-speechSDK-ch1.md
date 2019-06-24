# <a name="speech-sdk-learning-module"></a>语音 SDK 学习模块

在本教程将创建一个混合现实应用程序，探讨如何使用 Azure 认知服务语音 SDK，HoloLens 2。 当完成了本系列教程，你将能够使用你的设备的麦克风转录语音转文本在真实时间中，将语音翻译成其他语言，并利用语音 SDK 的意向功能，若要了解使用语音命令人工智能。

目标：

- 了解如何将 Azure 语音 SDK 集成到 HoloLens 2 应用程序
- 了解如何使用语音命令
- 了解如何使用语音转文本功能

## <a name="instructions"></a>说明

### <a name="getting-started"></a>入门

1. 启动 Unity 并创建一个新的项目。 输入项目名称"语音 SDK 学习模块。" 选择你的项目的保存位置的位置。 然后单击"创建项目"。

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> 注意：确保模板将设置为"3D"，在上图中所示。

2. 下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage)Unity 包，并在您的 PC 上将其保存到一个文件夹。 将包导入 Unity 项目。 有关如何执行此操作的详细说明，请参阅[的基本模块第 1 课](mrlearning-base-ch1.md)。 

3. 下载并导入 Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) Unity 资产包。 通过单击"资产"选择"导入包"然后选择"自定义包。"上导入的语音 SDK 包 查找前面下载的语音 SDK 包和打开它，以开始导入进程。 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. 在下一步的弹出窗口中，单击"导入"以开始导入的语音 SDK 包。 确保选中所有项，如下图中所示。

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. 下载[Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage)资产包。 Lunarcom 资产包是一系列资产并在本课程系列开发的脚本来展示 Azure 的语音 SDK 的实际用途。 它是最终将与之农历模块程序集体验开发中的语音命令终端[基本模块教程。](mrlearning-base-ch6.md)
6. 按照类似步骤采用的混合现实工具包和语音 SDK 导入 Lunarcom 资产包导入 Unity 项目。
7. 配置混合的现实工具包 (MRTK)。 要执行此操作，在窗口右上角的"混合现实 Toolkit"面板中单击并选择"将添加到场景和配置"。

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. 您的场景将现在包含几个新项从 MRTK。 保存您的场景通过单击"文件"以其他名称，然后"另存为"和"SpeechScene"命名您的场景。 

   > 注意：如果 MRTK 添加到项目，并且它不会进入"播放"模式后，可在您的场景中按播放按钮，您可能需要重新启动 Unity。 

9. "MixedRealityToolkit"选定对象层次结构中，单击"复制和自定义"检查器面板中。

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. 此外在 （与你的层次结构中选择的"MixedRealityToolkit"对象） 的检查器窗格中，通过取消选中"启用诊断 System"右侧的框禁用诊断系统。

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. 在项目面板中，展开"Lunarcom"文件夹并将"Lunarcom_Base"预设可拖放到你的层次结构。

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. 在层次结构中选择"Lunarcom_Base"对象，并确保该位置设置为 x = 0，y = 0，并且 z = 0，以及旋转将设置为 x = 0，y = 0，并且 z = 0。 设置要读取的比例 x = 0.008，y = 0.008 和 z = 0.01。

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. 单击"添加组件"，搜索并选择"LunarcomController。" 此脚本包含你在步骤 6 中导入 Lunarcom 资产包中。

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. 我们的应用程序连接到 Azure 认知服务，你必须输入"订阅密钥"也称为"API 密钥"的语音服务。 按照的说明[此链接](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started)以获取免费订阅密钥。 一旦您获取订阅密钥，请将其输入中的检查器面板中，"LunarcomController"组件的"语音服务 API 密钥"字段中如下图所示。

15. 输入你注册时选择你的订阅密钥置于"LunarcomController"组件检查器面板中的"语音服务区域"字段的区域。

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. 在层次结构中展开"Lunarcom_Base"对象，通过单击它，左侧的箭头，然后执行它的子对象"终端"，如下图中所示相同的。

17. 选择"Lunarcom_Base"后，单击并在检查器窗格中，拖动"Lunarcom Text"层次结构中的"输出文本"插槽"LunarcomController"组件中，如下图中所示。
18. 现在到"终端"槽中，"连接 Light Controller"槽的"连接 Light"对象执行与"终端"的对象相同的操作。

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. 单击检查器面板中的"LunarcomController"脚本"Lunarcom 按钮"部分旁边的箭头并将大小更改为 3 和键盘上按 Enter 键或 Return 键。 这会导致要显示的三个新"Element"字段。

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. 展开"Lunarcom 按钮"通过单击层次结构中其旁边的箭头，然后使用与上述相同的进程，将分别在组件中的"LunarcomController"组件是 0、 1 和 2 的元素引用到 Mic、 附属和火箭 gameobjects检查器面板。 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. 在层次结构中选择"Lunarcom_Base"对象。 检查器面板中单击"添加组件"，搜索并选择"LunarcomWakeWordRecognizer。"

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. 在"唤醒单词"槽中，键入在"激活终端"。 此外，在"关闭 Word"槽中，键入"解除终端"。

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a>祝贺

已由 Azure 提供支持，在应用程序中设置语音识别 ！ 运行应用程序以确保所有函数都正常都工作。 开始说步骤 22，"激活终端。"中键入唤醒文字 然后，选择麦克风按钮以启动语音识别，并开始说话。 你将看到您一边说一边转录在终端中的单词。 按第二次的麦克风按钮停止语音识别。 说"消除终端"若要隐藏 Lunarcom 终端。 在下一课中，我们将了解如何动态切换到 Azure 的语音 SDK 不是由于处于脱机状态 HoloLens 2 可用的情况下使用提供设备支持语音识别。

[下一课：第 2 课语音 SDK](mrlearning-speechSDK-ch2.md)

