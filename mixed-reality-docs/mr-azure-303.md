---
title: MR 和 Azure 303 的自然语言理解 (LUIS)
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 语言理解智能服务 (LUIS)。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 语言理解智能服务，luis，沉浸式、 hololens、 vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592605"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR 和 Azure 303:自然语言理解 (LUIS)

在本课程中，您将学习如何将语言理解集成到 Azure 认知服务，与语言理解 API 结合使用的混合的现实应用程序。

![实验结果](images/AzureLabs-Lab3-000.png)

*语言理解 (LUIS)* 是应用程序提供的功能以便利用用户输入，如通过提取一个人可能想什么，用他们自己的话说是 Microsoft Azure 服务。 这被通过机器学习，它能够理解和学习的输入的信息，并将其可以反馈详细的相关信息。 有关详细信息，请访问[Azure 语言理解 (LUIS) 页](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。

已完成本课程，会创建一个混合的现实沉浸式头戴式应用程序，将能够执行以下操作：

1.  捕获用户输入的语音，使用附加到沉浸式耳机式麦克风。 
2.  发送捕获的听写*Azure 语言理解智能服务*(*LUIS*)。 
3.  具有 LUIS 提取这意味着从发送信息，它将进行分析，并尝试确定将所做的用户的请求。

开发将包括用户将能够使用语音和/或注视若要更改的大小和场景中对象的颜色的应用的创建。 将不再重复介绍 motion 控制器使用。

在您的应用程序，它是取决于您关于如何将与您的设计集成结果。 本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。 它是作业以使用此课程以增强混合的现实应用程序中获取的知识。

请做好准备定型 LUIS 到几次，此内容中进行介绍[第 12 章](#chapter-12--improving-your-luis-service)。 你将获得更佳结果定型 LUIS 的更多时间。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>MR 和 Azure 303:自然语言理解 (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。 按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。 使用 HoloLens，您可能注意到某些 echo 语音捕获过程。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。 你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.

我们建议以下硬件和软件本课程：

- 开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md)
- [最新的 Windows 10 SDK](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- 一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式
- 一组的耳机使用内置的麦克风 （如果耳机没有内置的麦克风和扬声器）
- Internet 访问的 Azure 设置和 LUIS 检索

## <a name="before-you-start"></a>开始之前

1.  若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。 
2.  若要允许您的计算机以启用听写，请转到**Windows 设置 > 隐私 > 语音，墨迹书写和键入**按按钮**启用语音服务和键入建议**。
3.  在本教程中的代码将允许从录制**默认麦克风设备**在计算机上设置。 请确保默认麦克风设备设置为想要用于捕获您的声音。
4.  如果您的头戴式有内置麦克风，确保将选项 *"当我 wear 我耳机时，切换到耳机式麦克风"* 中开启*混合现实门户*设置。

    ![设置沉浸式头戴式](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>第 1 章 – 设置 Azure 门户

若要使用*语言理解*服务在 Azure 中，你将需要配置要成为可用于应用程序的服务的实例。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**新建**在左上角，并搜索*语言理解*，然后单击**Enter**。 

    ![创建 LUIS 资源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > 单词**新建**可能已替换**创建资源**，较新的门户网站中。
 
3.  右侧的新页将提供语言理解服务的说明。 在左下角此页上，选择**创建**按钮，创建此服务的实例。

    ![LUIS 服务创建-法律声明](images/AzureLabs-Lab3-02.png)
 
4.  一次单击在创建：

    1. 插入所需**名称**此服务实例。
    2. 选择**订阅**。
    3. 选择**定价层**适合您，如果这是第一个时间来创建*LUIS 服务*，应可供你免费层 （名为 F0）。 免费分配应足以应付此课程。
    4. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些课程） 相关联的所有 Azure 服务）。 

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 确定**位置**为资源组 （如果要创建新的资源组）。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。
    6. 您还需要确认你已了解的条款和条件应用于此服务。
    7. 选择“创建”。

        ![创建 LUIS 服务-用户输入](images/AzureLabs-Lab3-03.png)
 
5.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。
6.  创建服务实例后，在门户中将显示一条通知。 
 
    ![新的 Azure 通知图像](images/AzureLabs-Lab3-04.png)

7.  单击通知以了解新的服务实例。

    ![成功的资源创建通知](images/AzureLabs-Lab3-05.png)
 
8.  单击**转到资源**通知探索新的服务实例中的按钮。 你将转到新的 LUIS 服务实例。 
 
    ![访问 LUIS 密钥](images/AzureLabs-Lab3-06.png)

9.  在本教程中，你的应用程序将需要对你的服务，通过使用服务的订阅密钥来完成进行调用。
10. 从*快速入门*页上的你*LUIS API*服务，，请导航到的第一步*捕捉密钥*，然后单击**密钥**（也可以实现此目的通过单击蓝色超链接密钥，位于服务导航菜单中，由密钥图标表示）。 此时会显示你的服务*密钥*。
11. 需要一份某个显示的密钥，因为你将需要此更高版本中您的项目。 
12. 在中*服务*页上，单击*语言理解门户*重定向到的网页将用来创建新服务，LUIS 应用程序中的。 

## <a name="chapter-2--the-language-understanding-portal"></a>第 2 章-语言理解门户

在本部分中将了解如何在 LUIS 门户上进行 LUIS 应用。 

> [!IMPORTANT]
> 请特别注意，该设置*实体*，*意向*，并*语音样本*这一章中只是第一步构建 LUIS 服务： 你还将需要重新训练服务，几次，因此若要使其更准确。 中介绍了你的服务重新训练[最后一章](#chapter-12--improving-your-luis-service)的本课程中，因此请确保完成它。

1.  一旦达到*语言理解门户*，您可能需要登录，如果您尚不，使用 Azure 门户相同的凭据。 

    ![LUIS 登录页](images/AzureLabs-Lab3-07.png)
 
2.  如果这是你首次使用 LUIS，您将需要向下滚动到要查找，然后单击欢迎页的底部**创建 LUIS 应用**按钮。

    ![创建 LUIS 应用程序页](images/AzureLabs-Lab3-08.png)
 
3.  登录后，单击**我的应用**（如果您当前不是那一节中）。 您可以单击**创建新应用**。

    ![LUIS-我的应用的映像](images/AzureLabs-Lab3-09.png)
 
4.  为提供您的应用程序*名称*。
5.  如果您的应用程序应以了解不同于英语语言，应更改*区域性*为合适的语言。
6.  此处您还可以添加*说明*新 LUIS 应用程序。

    ![LUIS-创建新的应用](images/AzureLabs-Lab3-10.png)

7.  按下后**完成**，将进入*构建*将新的页*LUIS*应用程序。
8.  有几个需要了解此处的重要概念：

    -   *意向*，表示将从用户以下查询调用的方法。 *意向*可能具有一个或多个*实体*。
    -   *实体*，是说明与相关的信息的查询的组件*意向*。
    -   *语音样本*，提供由开发人员，该 LUIS 将用于定型本身是查询的示例。

如果这些概念并不完全清除，请不要担心，因为此课程将进行它们做进一步说明这一章中。

将首先创建*实体*需生成此课程。

9.  在左侧和右侧的页上，单击*实体*，然后单击**创建新实体**。

    ![创建新实体](images/AzureLabs-Lab3-11.png)

10. 调用新的实体*颜色*，将其类型设置为*简单*，然后按**完成**。

    ![创建简单的实体的颜色](images/AzureLabs-Lab3-12.png)
 
11. 重复此过程以创建三 （3） 更多简单实体名为：

    -   *upsize*
    -   *downsize*
    -   *target*

结果应类似于下图所示：

![创建实体时的结果](images/AzureLabs-Lab3-13.png)
 
现在可以开始创建*意向*。 

> [!WARNING]
> 不要删除**None**意向。

12. 在左侧和右侧的页上，单击**意向**，然后单击**创建新的意向**。

    ![创建新的 intents](images/AzureLabs-Lab3-14.png)

13. 调用新*意向* **ChangeObjectColor**。

    > [!IMPORTANT]
    > 这*意向*使用名称中的代码更高版本中此课程，因此对于获得最佳结果，使用此名称完全按原样。

一旦确认系统会定向到意向页的名称。

![LUIS 的意向页](images/AzureLabs-Lab3-15.png)

您会注意到没有要求你为 5 或更多个不同类型的 textbox*语音样本*。

> [!NOTE]
> LUIS 将所有查询文本转换为小写。

14. 插入以下*语音样本*顶部的文本框中 (当前具有文本*键入大约 5 示例...* )，然后按**Enter**:

```
The color of the cylinder must be red
```

您将注意到，新*语音样本*会在下方列表中。

按照相同的过程中，插入以下六 （6） 言辞：

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

对于已创建的每个查询文本，必须标识哪些字词应用作 luis 实体。 在此示例中您需要为所有颜色*颜色*实体，并且对作为目标的所有可能引用*目标*实体。

15. 若要执行此操作，请尝试单击的词*柱状体*第一个查询文本，然后选择*目标*。

    ![识别语音样本目标](images/AzureLabs-Lab3-16.png)
 
16. 现在，单击单词*红色*第一个查询文本，然后选择*颜色*。

    ![确定查询文本实体](images/AzureLabs-Lab3-17.png)
 
17. 此外，标记的下一行其中*多维数据集*应*目标*，并*黑色*应为*颜色*。 另请注意使用的某些词 *'this'*， *it*，并 *'此对象*，我们提供，因此还具有可用的非特定于目标类型。 

18. 重复上述过程，直到所有语音样本已标记为的实体。 请参阅下图，如果需要帮助。

    > [!TIP]
    > 当选择单词以作为实体标记它们：
    > - 为单个词只需单击它们。
    > - 两个或多个单词的一组，请单击开头和，然后在集的末尾。

    > [!NOTE]
    > 可以使用*令牌视图*切换按钮来切换**实体 / 令牌视图**！

19. 结果应如中所示下, 图中显示**实体 / 令牌视图**:

    ![令牌和实体视图](images/AzureLabs-Lab3-18.png)
  
20. 此时按**训练**页面的右上按钮并等待的小型倒圆角的指示符，它才会变为绿色。 这表示，LUIS 成功定型识别此意向。

    ![定型 LUIS](images/AzureLabs-Lab3-19.png)
 
21. 为你的练习，创建名为新意向**ChangeObjectSize**，使用实体*目标*，*升迁*，以及*缩小*。
22. 遵循与前一意图，相同的进程插入以下 8 个语音样本添加有关*大小*更改：

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. 结果应类似于下图所示：

    ![设置 ChangeObjectSize 令牌 / 实体](images/AzureLabs-Lab3-20.png) 

24. 一次这两种意图**ChangeObjectColor**并**ChangeObjectSize**，已创建并定型，单击**发布**页面顶部的按钮。

    ![发布 LUIS 服务](images/AzureLabs-Lab3-21.png)

25. 上*发布*将完成并发布 LUIS 应用，以便其可以访问你的代码页。

    1. 向下设置下拉*发布到*作为**生产**。
    2. 设置*时区*到您所在的时区。
    3. 选中复选框**包括所有预测意向分数**。
    4. 单击**发布到生产槽**。

        ![发布设置](images/AzureLabs-Lab3-22.png)

26. 在部分*资源和密钥*:

    1.  选择在 Azure 门户中的服务实例设置的区域。
    2.  你会注意到**Starter_Key**元素下面，将其忽略。
    3.  单击**添加密钥**，并插入*密钥*创建您的服务实例时获得在 Azure 门户中。 如果你的 Azure 和 LUIS 门户登录到同一用户中，将提供的下拉列表菜单*租户名称*，*订阅名称*，并*密钥*你想要使用 （将具有相同的名称，如前面在 Azure 门户中提供。

    > [!IMPORTANT] 
    > 其下方*终结点*，复制的键对应的终结点已插入，很快将在代码中使用它。
 
## <a name="chapter-3--set-up-the-unity-project"></a>第 3 章 – 设置 Unity 项目

以下是一组典型使用混合现实中，进行开发，并在这种情况下，是合适的模板的其他项目。

1.  打开*Unity*然后单击**新建**。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab3-24.png)

2.  现在将需要提供 Unity 项目的名称，插入**MR_LUIS**。 请确保项目类型设置为**3D**。 设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![提供新的 Unity 项目的详细信息。](images/AzureLabs-Lab3-25.png)
 
3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到编辑 > 首选项，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab3-26.png)
 
4.  接下来，请转到**文件 > 生成设置**，并切换到平台**通用 Windows 平台**，单击**切换平台**按钮。

    ![生成设置窗口中，切换到 UWP 的平台。](images/AzureLabs-Lab3-27.png)
 
5.  转到**文件 > 生成设置**并确保选中：

    1. **设备为目标**设置为**任一设备**

        > 对于 Microsoft HoloLens，设置**目标设备**到*HoloLens*。

    2. **生成的类型**设置为**D3D**
    3. **SDK**设置为**最新安装**
    4. **Visual Studio 版本**设置为**最新安装**
    5. **生成并运行**设置为**本地计算机**
    6. 保存场景，并将其添加到生成。

        1. 选择执行此**添加打开场景**。 保存窗口将显示。
        
            ![单击添加打开场景按钮](images/AzureLabs-Lab3-28.png)

        2. 创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![创建新的 scripts 文件夹](images/AzureLabs-Lab3-29.png)

        3. 打开新建**场景**文件夹，然后在*文件名*： 文本字段中，键入**MR_LuisScene**，然后按**保存**。

            ![为新的场景提供一个名称。](images/AzureLabs-Lab3-30.png)

    7. 中的剩余设置，*生成设置*，应暂时保留为默认值。

6. 在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。 

    ![打开播放器设置。](images/AzureLabs-Lab3-31.png) 
 
7. 在此面板中，需要验证几个设置：

    1. 在中**其他设置**选项卡：

        1. **脚本运行时版本**应**稳定**（.NET 3.5 等效）。
        2. **脚本编写后端**应为 **.NET**
        3. **API 兼容性级别**应为 **.NET 4.6**

            ![更新其他设置。](images/AzureLabs-Lab3-32.png)
      
    2. 内**发布设置**选项卡上，在**功能**，检查：

        1. **InternetClient**
        2. **Microphone**

            ![正在更新的发布设置。](images/AzureLabs-Lab3-33.png)

    3. 中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。

        ![更新的 X R 设置。](images/AzureLabs-Lab3-34.png)

8.  回到*生成设置* _Unity C#_ 项目不再灰显; 选中它旁边的复选框。 
9.  关闭生成设置窗口。
10. 保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。

## <a name="chapter-4--create-the-scene"></a>第 4 章-创建场景

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，将其导入项目中，作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 5 章：](#chapter-5--create-the-microphonemanager-class)。 

1.  在空白区域中单击右键*层次结构面板*下**三维对象**，将添加**平面**。

    ![创建一个平面。](images/AzureLabs-Lab3-35.png)

2.  请注意，当在中右键单击*层次结构*再次以创建更多的对象，如果您仍然可以选择的最后一个对象，所选的对象将新对象的父对象。 在层次结构中的空白空间中单击鼠标左键，然后右键单击可以避免此问题。

3.  重复上述过程添加以下对象：

    1. *Sphere*
    2. *Cylinder*
    3. *Cube*
    4. *三维文字*

4.  生成场景*层次结构*应类似于下图所示：

    ![场景层次结构的设置。](images/AzureLabs-Lab3-36.png)
 
5.  在单击鼠标左键**Main Camera**若要选择它，请查看*检查器面板*您将看到所有相机对象及其组件。
6.  单击**添加组件**按钮位于最底部*检查器面板*。

    ![添加音频源](images/AzureLabs-Lab3-37.png)
 
7.  搜索调用的组件*音频源*，如上所示。
8.  此外，请确保*转换*Main Camera 组件设置为 (0,0,0)，这可以通过按**齿轮**照相机的旁边的图标*转换*组件并选择**重置**。 *转换*组件应如下所示：

    1.  *位置*设置为**0，0，0**。
    2.  *旋转*设置为**0，0，0**。

    > [!NOTE] 
    > 对于 Microsoft HoloLens，您将需要还可以更改以下内容，属于**照相机**组件，它位于您**Main Camera**:
    > - **清除标志：** 纯色。
    > - **背景**黑色、 Alpha 0 – 十六进制颜色: #00000000。

9.  在单击鼠标左键**平面**以将其选中。 在中*检查器面板*设置*转换*组件使用以下值：

    |       | 转换的*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. 在单击鼠标左键**球体**以将其选中。 在中*检查器面板*设置*转换*组件使用以下值：

    |       | 转换的*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. 在单击鼠标左键**柱状体**以将其选中。 在中*检查器面板*设置*转换*组件使用以下值：

    |       | 转换的*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | -2    | 1                      | 2     |

12. 在单击鼠标左键**多维数据集**以将其选中。 在中*检查器面板*设置*转换*组件使用以下值：

    |        | 转换的*位置* |       |  \| |       | 转换的*旋转* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. 在单击鼠标左键**新文本**对象以将其选中。 在中*检查器面板*设置*转换*组件使用以下值：

    |       | 转换的*位置* |       |  \| |       | 转换的*规模* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. 更改**字号**中**文本 Mesh**组件**50**。
15. 更改*名称*的**文本 Mesh**对象传递给**听写文本**。

    ![创建三维文本对象](images/AzureLabs-Lab3-38.png)
 
16. 层次结构面板结构现在应如下所示：

    ![文本在场景视图中的网格](images/AzureLabs-Lab3-38b.png)


17. 最后一个场景应如下图所示：

    ![场景视图中。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>第 5 章-创建 MicrophoneManager 类

要创建的第一个脚本是*MicrophoneManager*类。 接着，您将创建*LuisManager*，则*行为*类，并最后*注视*类 （可随时创建所有这些目前为止，但将为您介绍访问每一章）。

*MicrophoneManager*类负责：

-   检测到耳机或 （二者是为默认值） 的计算机随附的录制设备。
-   捕获音频 （语音），并使用听写将其存储为字符串。
-   一旦语音已暂停，提交到听写*LuisManager*类。 

若要创建此类： 

1.  在中右击*项目面板*，**创建 > 文件夹**。 将该文件夹**脚本**。 

    ![创建脚本的文件夹。](images/AzureLabs-Lab3-40.png)
 
2.  与**脚本**创建文件夹，双击它，以打开。 然后，在该文件夹中，右键单击，**创建 >C#脚本**。 脚本命名为*MicrophoneManager*。 

3.  双击*MicrophoneManager*以打开其与*Visual Studio*。
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  然后添加以下变量内的*MicrophoneManager*类：

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  为代码*Awake()* 并*start （)* 方法现在需要添加。 类初始化时将会调用：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  现在，您需要应用用于启动和停止语音捕获，并将其传递给方法*LuisManager*类，您很快就会生成。 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  添加*听写处理程序*语音暂停时，将调用的。 此方法将传递到的听写文本*LuisManager*类。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > 删除*update （)* 方法因为此类不会使用它。

9.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

    > [!NOTE]
    > 此时你会注意到出现在错误*Unity 编辑器控制台面板*。 这是因为该代码引用*LuisManager*将在下一章中创建的类。

## <a name="chapter-6--create-the-luismanager-class"></a>第 6 章-创建 LUISManager 类

是为您创建的时候*LuisManager*类，该类将对 Azure LUIS 服务的调用。 

此类的目的是接收从听写文本*MicrophoneManager*类，并将其发送到*Azure 语言理解 API*若要对其进行分析。

此类将反序列化*JSON*响应并调用相应的方法的*行为*类，以触发操作。

若要创建此类： 

1.  双击**脚本**文件夹，将其打开。 
2.  内右击**脚本**文件夹中，单击**创建 >C#脚本**。 脚本命名为*LuisManager*。 
3.  双击要使用 Visual Studio 中打开的脚本。
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  将首先创建三个类**内** *LuisManager*类 (在相同的脚本文件中，上面*start （)* 方法)，将表示的反序列化从 Azure 的 JSON 响应。

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  接下来，添加以下变量内的*LuisManager*类：
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  请确保现在将放置在你 LUIS 的终结点 （它必须从 LUIS 门户）。

8.  为代码*Awake()* 方法现在需要添加。 类初始化时，将会调用此方法：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  现在，你需要此应用程序用来发送来自听写的方法*MicrophoneManager*类来*LUIS*，然后接收和反序列化响应。 
10. 一旦已确定的值的意向和关联的实体，它们传递到的实例*行为*类，以触发所需的操作。

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. 创建一个名为的新方法*AnalyseResponseElements()* ，它将读取生成*AnalysedQuery*并确定实体。 这些实体确定后，它们将被传递到的实例*行为*类，以在操作中使用。

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognised intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > 删除*start （)* 并*update （)* 方法，因为此类不会使用它们。

12. 请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

> [!NOTE]
> 此时你会注意到出现在多个错误*Unity 编辑器控制台面板*。 这是因为该代码引用*行为*将在下一章中创建的类。

## <a name="chapter-7--create-the-behaviours-class"></a>第 7 章 – 创建行为类

*行为*类将触发的操作，使用提供的实体*LuisManager*类。

若要创建此类： 

1.  双击**脚本**文件夹，将其打开。 
2.  内右击**脚本**文件夹中，单击**创建 >C#脚本**。 脚本命名为*行为*。 
3.  双击要将其与打开的脚本*Visual Studio*。
4.  然后添加以下变量内的*行为*类：

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  添加*Awake()* 方法代码。 类初始化时，将会调用此方法：

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  调用以下方法*LuisManager*类 （先前已创建） 来确定哪些对象是查询的目标，然后触发相应的措施。

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  添加*FindTarget()* 方法来确定哪些*GameObjects*是当前的意向的目标。 此方法将默认为目标*GameObject*正在"gazed"如果未明确指定目标定义实体中。

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > 删除*start （)* 并*update （)* 方法，因为此类不会使用它们。

8.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-8--create-the-gaze-class"></a>章 8 – 创建的视线移动类

将需要完成此应用的最后一个类是*注视*类。 此类将更新对引用*GameObject*当前在用户的可视焦点。

若要创建此类： 

1.  双击**脚本**文件夹，将其打开。 
2.  内右击**脚本**文件夹中，单击**创建 >C#脚本**。 脚本命名为*注视*。 
3.  双击要将其与打开的脚本*Visual Studio*。
4.  插入此类的以下代码：

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-9--completing-the-scene-setup"></a>第 9 章 – 完成场景设置

1.  若要完成场景的安装程序，将脚本文件夹中创建每个脚本**Main Camera**对象中*层次结构面板*。
2.  选择**Main Camera**并查看*检查器面板*，您应该能够看到已附加，每个脚本，会注意到有尚设置每个脚本参数。

    ![设置照相机引用目标。](images/AzureLabs-Lab3-41.png)

3.  若要正确设置这些参数，请按照这些说明操作：

    1. *MicrophoneManager*:

        - 从*层次结构面板*，拖动**听写文本**对象插入**听写文本**参数值。

    2. *行为*，从*层次结构面板*:

        - 拖动**球体**对象插入*球体*引用目标。
        - 拖动**柱状体**成*柱状体*引用目标。
        - 拖动**多维数据集**成*多维数据集*引用目标。

    3. *注视*:

        - 设置*注视最大距离*到**300** （如果还没有的话）。 

4.  结果应类似于下图所示：

    ![显示相机引用目标，现在设置。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>第 10 章-测试在 Unity 编辑器

测试场景设置正确地实现。

请确保：

-   所有脚本都附加到**Main Camera**对象。 
-   中的所有字段*主相机检查器面板*正确分配。

1.  按**播放**按钮*Unity 编辑器*。 应用程序应在附加的沉浸式头戴式内运行。

2.  尝试一些查询文本，例如：

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > 如果看到有关更改默认音频设备 Unity 控制台中的错误，场景可能无法按预期方式。 这是由于混合的现实门户内置麦克风耳机具有它们的处理的方式。 如果看到此错误，只需停止场景并重新启动它，并且应该可以正常为预期。

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>第 11 章 – 生成和旁加载 UWP 解决方案

一旦你可确保应用程序使用在 Unity 编辑器中，已准备好生成和部署。

若要生成：

1.  通过单击保存当前场景**文件 > 保存**。
2.  转到**文件 > 生成设置**。
3.  选中名为框**UnityC#项目**（用于查看和创建 UWP 项目后调试代码。
4.  单击**添加打开场景**，然后单击**生成**。

    ![生成设置窗口](images/AzureLabs-Lab3-43.png)

4.  系统将提示您选择你想要生成解决方案的文件夹。 

5.  创建*生成*文件夹并在该文件夹中创建另一个文件夹，与所选的适当的名称。 
6.  单击**选择文件夹**若要开始在该位置的生成。
 
    ![创建内部版本文件夹](images/AzureLabs-Lab3-44.png)
    ![选择生成文件夹](images/AzureLabs-Lab3-45.png)
 
7.  一次 Unity 已完成的生成 （它可能需要一些时间），它应打开**文件资源管理器**窗口在生成的位置。

若要在本地计算机上部署：

1.  在中*Visual Studio*，打开已在中创建的解决方案文件[上一章](#chapter-10--test-in-the-unity-editor)。
2.  在中**解决方案平台**，选择**x86**，**本地计算机**。
3.  在中**解决方案配置**选择**调试**。

    > 对于 Microsoft HoloLens，您可能会发现它更轻松地将其设置为*远程计算机*，因此您不已接入到你的计算机。 不过，需要还执行以下操作：
    > - 知道**IP 地址**的你 HoloLens，在中找到*设置 > 网络和 Internet > Wi-fi > 高级选项*; IPv4 是应使用的地址。 
    > - 请确保**开发人员模式**是**上**; 中找到*设置 > 更新和安全 > 面向开发人员*。

    ![将应用部署](images/AzureLabs-Lab3-46.png)
 
4.  转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。
5.  你的应用现在应出现在列表中的已安装的应用，准备好启动 ！
6.  启动后，应用将提示你授予访问权限_麦克风_。 使用*运动控制器*，或*语音输入*，或*键盘*按**是**按钮。 

## <a name="chapter-12--improving-your-luis-service"></a>第 12 章-提高 LUIS 服务

>[!IMPORTANT] 
> 这一章非常重要，可能需要为 interated 后几次，这会有助于提高准确性 LUIS 服务： 请确保完成此操作。

若要改进的级别提供的 LUIS 理解需要捕获新查询文本并使用它们来重新训练 LUIS 应用程序。

例如，你可能具有经过培训 LUIS 了解"Increase"和"降级"，但不希望您的应用程序，以便了解"放大"等单词？

在使用你的应用程序几次，所有内容你说将收集的 LUIS，LUIS 门户中提供。

1.  转到门户应用以下这[链接](https://www.luis.ai/home)，和日志中。
2.  一旦使用 MS 凭据登录，单击你*应用名称*。
3.  单击**查看终结点语音样本**页面左侧的按钮。

    ![查看查询文本](images/AzureLabs-Lab3-47.png)
 
4.  将显示一系列在混合现实应用程序发送到 LUIS 语音样本。

    ![查询文本的列表](images/AzureLabs-Lab3-48.png)
 
你会注意到一些突出显示*实体*。 

悬停在每个突出显示单词时，可以查看每个语音样本，并确定哪些实体具有已正确识别，这是错误的实体，哪些实体会丢失。

在上面的示例中，它已找到，"鱼叉式"一词有已突出显示为目标，因此它可以纠正该错误，可以悬停在该单词设置为鼠标，然后单击所需**删除标签**。

![检查语音样本](images/AzureLabs-Lab3-49.png)
![删除标签图像](images/AzureLabs-Lab3-50.png)
 
5.  如果发现有完全错误时的语音样本，则可以删除它们使用**删除**屏幕右侧的按钮。

    ![删除错误的查询文本](images/AzureLabs-Lab3-51.png)

6.  或如果您认为 LUIS 已正确解释语音样本，您可以通过使用验证其对理解**添加到对齐意向**按钮。

    ![将添加到对齐意向](images/AzureLabs-Lab3-52.png)

7.  已排序的显示语音样本后, 重试并重新加载页后，可以查看的详细信息是否可用。
8.  它是重复多次以尽可能提高应用程序了解此过程非常重要。 

**玩得愉快！**

## <a name="your-finished-luis-integrated-application"></a>完成的 LUIS 集成应用程序

祝贺你，构建利用 Azure 语言理解智能服务，以了解用户显示和处理该信息的混合的现实应用。

![实验结果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

使用此应用程序时可能会注意到，是否您注视 Floor 对象，并要求更改其颜色，它都会这样。 您可以推断出如何停止您的应用程序更改基底的颜色？

### <a name="exercise-2"></a>练习 2

请尝试将 LUIS 和应用程序功能，在场景; 中添加对象的附加功能扩展例如，在提供注视命中的点，具体取决于哪些用户显示，并便能够使用这些对象，以及当前场景对象，使用现有的命令创建新对象。 
