---
title: MR 学习 ASA 模块上 HoloLens 2 Azure 空间的定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327402"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon （更正我如果我是错误）

在本课中， 

目标：

* 了解如何 ___

* 了解如何 ___

  

## <a name="instructions"></a>说明

### <a name="setting-up-photon"></a>Photon 设置

1. 设置[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帐户。 执行此操作将包含输入你的电子邮件和经过一些验证步骤。
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. 一旦您注册了，单击 Sdk。 后该页面上，单击"服务器"，并确保它说，"自我托管。" 然后向下滚动并单击"服务器"中第二张插图所示。

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. 这将导致文本框中，以便显示标记，"读取我。" 请继续并读取它。 完成后，单击"downloadSDK"若要下载它旁边的链接。


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. 完成下载后，双击单击的文件夹。  在文件资源管理器打开后显示的 SDK 文件夹，将 SDK 文件夹复制。
   
   - 下一步是转到 windows c： 驱动器并创建新的文件夹名为 server。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - 现在打开文件夹，并粘贴先前复制的 SDK 文件夹。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. 完成后，打开 SDK 文件夹并转到"部署"然后"bin_Win64，"，然后双击"photon 控制"。


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> 注意：如果有任何疑问 IP 地址或任何其他类似问题，您可以在工具栏中发现你的信息的大部分，（如下图所示）。
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. 现在，设置并启动服务器，回到 Photon 网站并单击配置文件图标 （如下图中装箱） 并选择"在应用程序"。
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. 通过单击"创建新的应用程序"按钮创建一个应用程序 ID。

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - 从"photon 类型。"下的下拉列表菜单中选择"Photon 运行" 然后为其提供一个名称，（这会记住）。 在此示例中，我们其命名为"HoloLensPhotonProject。" 完成后，单击"创建"。

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. 完成后，返回到应用程序页，并应看到类似于下面的图片。 单击应用程序 id 并将其复制。 粘贴是可以轻松访问的某个位置。  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. 创建新的 unity 项目。 打开 Unity 中心，然后单击"new。 其命名为"HLSharingProject。" 然后单击创建。 

   > 注意：这可能需要 2 分钟的时间来加载，请根据您的计算机的速度。

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> 注意： 选择一个位置来保存在计算机中的项目，通过更改"位置"选项。 将其保存到您能记住并轻松访问的位置。

10. 项目加载后，单击"资产 store"。 然后，在搜索框中显示下图中，键入"双关语"并选择"Photon 双关语 2 免费"资产。 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. 下载并导入 ！
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**设置 Unity 项目** 

11. 下载新的资产所需设置 Photon Unity 中通过单击[此处。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. 在 Unity 中，单击资产菜单并选择"导入资产，"，然后单击"自定义的资产。"

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. 选择您刚从在步骤 1 中提供的链接下载 Unity 包。 后的导入按钮出现在 Unity 中，单击它。

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> 注意： 下载到包的任何位置将在哪里找到它。 上图没有描绘出将在何处找到程序包。

14. 创建新的场景 (这可以是已通过使用控件 / 命令 + N 或通过单击"文件"并选择"新的场景。")。 将场景另存为"HLSharedProjectMain。"

> 注意： 可能会收到一个弹出窗口，它看起来类似于下图所示。 现在，只需单击"否"。
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. 在"混合现实 Toolkit"单击"将添加到场景和配置"。

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. 完成后完成后，新的配置文件将出现，让您选择自定义配置文件。 单击"复制和自定义"。

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. 向下滚动并取消选中"启用诊断系统。" 这将使更方便地设置此项目。

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. 打开生成设置 （控制 + shift + B）。 请注意，该程序当前在"电脑、 Mac 和 Linux 独立"平台设置。 对于此项目，将设置为"通用 windows 平台。"的平台 选择它，然后单击"切换平台"。

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. 完成后，单击框，其中显示"添加打开的场景。 现在请转到检查器面板，并确保右侧的"支持的虚拟现实"复选框 （如在下图中所示） 已选中。 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> 注意：此外请确保也选中"场景/HLSharedProjectMain"旁边的复选框。

20. 在检查器面板中的"发布设置"向下滚动到"功能"，并确保标记仅以下复选框：

- internet 客户端
- internet 客户端服务器
- 专用网络客户端服务器
- camera/webcam
- 麦克风

21. 就像步骤 12 中下, 一步是导入另一个名为"第 2 课"可以在 [此处]。 下载的自定义包[此处显示 lesson2.unitypackage 链接]导入该包。

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. 现在，在项目面板中，转到"预设"文件夹，因为下一步的几个步骤中您将执行向场景的几个预设。 在"预设"文件夹中，单击并拖动预设可在层次结构"DebugWindow"。 完成后，保存项目 (单击文件，然后保存，或控制 + S)

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> 注意：您可能注意到一个弹出窗口，显示当您单击预设可，询问您 TMP Essentials。 单击"导入 TMP Essentials"，因为将需要它们。
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**将多个用户连接**

23. 步骤 22 的"预设"文件夹中的项目面板中，正如下一步是拖放到层次结构删除"NetworkLobby"预设。 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. 当您打开父预设，"NetworkLobby，"应该会看到子预设，"NetworkRoom。" 使用它选择，请转到检查器面板并单击"添加组件"。 搜索"PhotonView"并添加该组件。

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. 在层次结构 （右键单击在层次结构中，选择"空"） 中创建一个新的空游戏对象。 确保将位置设置为 x = 0，y = 0，z = 0，命名该对象，"PhotonUser。"

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>祝贺



