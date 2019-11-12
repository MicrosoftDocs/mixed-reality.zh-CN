---
title: MR 和 Azure 303-自然语言理解（LUIS）
description: 完成本课程以了解如何在混合现实应用程序中实现 Azure 语言理解智能服务（LUIS）。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，语言理解智能服务，luis，hololens，沉浸，vr
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926808"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。  因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。  这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR 和 Azure 303：自然语言理解（LUIS）

在本课程中，你将了解如何使用 Azure 认知服务将语言理解集成到混合现实应用程序中，语言理解 API。

![实验室结果](images/AzureLabs-Lab3-000.png)

*语言理解（LUIS）* 是一种 Microsoft Azure 服务，它使应用程序能够从用户输入中代替用户输入，例如通过提取用户可能需要的内容。 这是通过机器学习来实现的，它可以理解和学习输入信息，然后可以使用详细的相关信息进行回复。 有关详细信息，请访问[Azure 语言理解（LUIS）页](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。

完成本课程后，你将拥有一个混合现实沉浸式耳机应用程序，该应用程序将能够执行以下操作：

1.  使用连接到沉浸式耳机的麦克风捕获用户输入语音。 
2.  将捕获的听写发送到*Azure 语言理解智能服务*（*LUIS*）。 
3.  让 LUIS 从发送信息中提取含义，将对其进行分析，并尝试确定用户请求的意图。

开发过程包括创建一个应用程序，用户可以使用该应用程序来更改场景中对象的大小和颜色。 不会覆盖运动控制器的使用。

在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。 本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。 您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。

准备多次训练 LUIS，这将在第[12 章](#chapter-12--improving-your-luis-service)中介绍。 更好的结果是训练 LUIS 的次数越多。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 和 Azure 303：自然语言理解（LUIS）</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要侧重于 Windows Mixed Reality 沉浸（VR）耳机，但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。 在本课程中，你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。 使用 HoloLens 时，可能会在语音捕获过程中注意到某些回声。

## <a name="prerequisites"></a>必备条件

> [!NOTE]
> 本教程面向具有 Unity 和C#的基本经验的开发人员。 另外请注意，本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容（5月2018）。 您可以随意使用最新的软件（如[安装工具](install-the-tools.md)一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件：

- [与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发
- [Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式](install-the-tools.md)
- [最新的 Windows 10 SDK](install-the-tools.md)
- [Unity 2017。4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- 启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 带有内置麦克风的一组耳机（如果耳机没有内置麦克风和扬声器）
- Azure 安装和 LUIS 检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

1.  为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。 
2.  若要允许计算机启用听写，请转到 " **Windows 设置" > 隐私 > 语音 "、" 墨迹书写 & 键入**"和"**打开语音服务并键入建议**"按钮。
3.  本教程中的代码将允许你从计算机上的**默认麦克风设备**设置进行录制。 请确保将默认麦克风设备设置为要用于捕获语音的设备。
4.  如果耳机有内置麦克风，请确保在*混合现实门户*设置中启用 *"我戴上耳机，切换到耳机麦克风"* 选项。

    ![设置沉浸式耳机](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>第1章–设置 Azure 门户

若要在 Azure 中使用*语言理解*服务，你将需要配置服务的实例，使其可用于你的应用程序。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。

2.  登录后，单击左上角的 "**新建**"，搜索 "*语言理解*"，然后单击 " **Enter**"。 

    ![创建 LUIS 资源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > 在较新的门户中，可能已将 "**新建**" 一词替换为 "**创建资源**"。
 
3.  向右的新页将提供语言理解服务的说明。 在此页的左下角，选择 "**创建**" 按钮以创建此服务的实例。

    ![创建 LUIS 服务-法律声明](images/AzureLabs-Lab3-02.png)
 
4.  单击 "创建" 后：

    1. 为此服务实例插入所需的**名称**。
    2. 选择**订阅**。
    3. 选择适合你的**定价层**，如果这是第一次创建*LUIS 服务*，则你应该可以使用免费层（名为 F0）。 对于本课程，免费分配应该已经足够。
    4. 选择一个**资源组**，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。 

        > 若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 确定资源组的**位置**（如果要创建新的资源组）。 此位置理想情况下会在应用程序运行所在的区域中。 某些 Azure 资产仅在特定区域提供。
    6. 还需要确认是否已了解应用于此服务的条款和条件。
    7. 选择“创建”。

        ![创建 LUIS 服务-用户输入](images/AzureLabs-Lab3-03.png)
 
5.  单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。
6.  创建服务实例后，门户中将显示一个通知。 
 
    ![新的 Azure 通知映像](images/AzureLabs-Lab3-04.png)

7.  单击通知以浏览新服务实例。

    ![成功创建资源通知](images/AzureLabs-Lab3-05.png)
 
8.  单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。 你将转到新的 LUIS 服务实例。 
 
    ![访问 LUIS 项](images/AzureLabs-Lab3-06.png)

9.  在本教程中，你的应用程序将需要调用你的服务，这是通过使用你的服务的订阅密钥来完成的。
10. 在*LUIS API*服务的 "*快速启动*" 页上，导航到第一步，*获取你的密钥*，然后单击 "**密钥**" （也可以通过单击位于 "服务" 导航菜单中的蓝色超链接项（由键图标表示）来实现此目的。 这会显示你的服务*密钥*。
11. 复制其中一个所显示的密钥，因为稍后会在项目中使用此密钥。 
12. 在 "*服务*" 页上，单击 "*语言理解门户*" 以重定向到在 LUIS 应用中用于创建新服务的网页。 

## <a name="chapter-2--the-language-understanding-portal"></a>第2章–语言理解门户

在本部分中，你将了解如何在 LUIS 门户中创建 LUIS 应用程序。 

> [!IMPORTANT]
> 请注意，在本章中设置*实体*、*意向*和*最谈话*只是构建 LUIS 服务的第一步：你还需要多次重新训练服务，以便使其更准确。 本课程的[最后一章](#chapter-12--improving-your-luis-service)介绍了重新训练你的服务，因此请确保完成此操作。

1.  进入*语言理解门户*后，你可能需要登录（如果尚未登录），其凭据与 Azure 门户相同。 

    ![LUIS 登录页](images/AzureLabs-Lab3-07.png)
 
2.  如果这是你第一次使用 LUIS，则需要向下滚动到 "欢迎" 页的底部，查找并单击 "**创建 LUIS 应用**" 按钮。

    !["创建 LUIS 应用" 页](images/AzureLabs-Lab3-08.png)
 
3.  登录后，单击 **"我的应用**" （如果当前不在该部分中）。 然后，可以单击 "**创建新应用**"。

    ![LUIS-我的应用图像](images/AzureLabs-Lab3-09.png)
 
4.  为应用程序*命名*。
5.  如果你的应用程序应了解不同于英语的语言，则应将*区域性*更改为适当的语言。
6.  你还可以在此处添加新的 LUIS 应用的*描述*。

    ![LUIS-创建新应用](images/AzureLabs-Lab3-10.png)

7.  按下 "**完成**" 后，将进入新*LUIS*应用程序的 "*生成*" 页。
8.  此处有几个重要概念需要了解：

    -   *意向*，表示将从用户查询后调用的方法。 *意向*可以有一个或多个*实体*。
    -   *实体*，是描述与*意向*相关的信息的查询组件。
    -   *最谈话*是由开发人员提供的查询的示例，LUIS 将使用该查询来训练自身。

如果这些概念并不完全清晰，请不要担心，因为本课程将在本章中进一步阐明它们。

首先创建生成此课程所需的*实体*。

9.  在页面左侧，单击 "*实体*"，并单击 "**创建新实体**"。

    ![创建新实体](images/AzureLabs-Lab3-11.png)

10. 调用新的实体*颜色*，将其类型设置为 "*简单*"，并按 "**完成**"。

    ![创建简单实体-颜色](images/AzureLabs-Lab3-12.png)
 
11. 重复此过程以创建三个（3）个名更简单的实体：

    -   *降级*
    -   *缩小*
    -   *靶*

结果应如下图所示：

![实体创建的结果](images/AzureLabs-Lab3-13.png)
 
此时，你可以开始创建*意向*。 

> [!WARNING]
> 请勿删除 "**无**"。

12. 在页面左侧，单击 "选择 **"，然后**单击 "**创建新意向**"。

    ![创建新意向](images/AzureLabs-Lab3-14.png)

13. 调用新*意向* **ChangeObjectColor**。

    > [!IMPORTANT]
    > 本课程后面的代码中使用此*意向*名称，因此为了获得最佳结果，请完全按所提供的名称使用此名称。

确认名称后，将定向到 "意向" 页。

![LUIS 页](images/AzureLabs-Lab3-15.png)

你会注意到有一个文本框要求你键入5个或更多不同的*最谈话*。

> [!NOTE]
> LUIS 将所有最谈话都转换为小写。

14. 在顶部文本框中插入以下*查询文本*（当前文本*类型约为5个示例 ...* ），然后按**enter**：

```
The color of the cylinder must be red
```

你会注意到，新的*查询文本*将显示在下面的列表中。

按照相同的过程，插入以下六个（6）最谈话：

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

对于创建的每个查询文本，必须确定 LUIS 将哪些字词作为实体使用。 在此示例中，需要将所有颜色标记为一个*颜色*实体，并将所有可能的引用标记为*目标实体。*

15. 为此，请在第一个查询文本中单击 "*圆柱*"，然后选择 "*目标*"。

    ![标识查询文本目标](images/AzureLabs-Lab3-16.png)
 
16. 现在，在第一个查询文本中单击 "*红色*"，然后选择 "*颜色*"。

    ![标识查询文本实体](images/AzureLabs-Lab3-17.png)
 
17. 标记下一行，其中， *cube*应为*目标*，*黑色*应为一种*颜色*。 另请注意，我们提供了单词 *"this"* 、 *"it"* 和 *"this object"* ，因此还提供了非特定目标类型。 

18. 重复上述过程，直到所有最谈话都具有标记的实体。 如果需要帮助，请参阅下图。

    > [!TIP]
    > 选择字词以将其标记为实体时：
    > - 只需单击一下即可。
    > - 对于两个或多个单词的集合，请单击 "开始"，然后在集末尾单击。

    > [!NOTE]
    > 您可以使用 "*标记视图*" 切换按钮在**实体/标记视图**之间切换！

19. 结果应如下图所示，其中显示了 "**实体/标记" 视图**：

    ![标记 & 实体视图](images/AzureLabs-Lab3-18.png)
  
20. 此时，按页面右上角的 "**训练**" 按钮，并等待其上的小圆形指示器变为绿色。 这表示已成功训练 LUIS 以识别此目的。

    ![训练 LUIS](images/AzureLabs-Lab3-19.png)
 
21. 作为练习，使用实体*target*、*升迁*和*缩小*创建名为**ChangeObjectSize**的新意向。
22. 遵循与上一意向相同的过程，插入以下八个（8）最谈话*大小*更改：

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

    ![设置 ChangeObjectSize 令牌/实体](images/AzureLabs-Lab3-20.png) 

24. 一旦创建并训练了**ChangeObjectColor**和**ChangeObjectSize**，单击页面顶部的 "**发布**" 按钮。

    ![发布 LUIS 服务](images/AzureLabs-Lab3-21.png)

25. 在 "*发布*" 页上，您将完成并发布 LUIS 应用程序，以便您的代码可以访问它。

    1. 将下拉 "*发布到*" 设置为 "**生产**"。
    2. 将*时区*设置为时区。
    3. 选中 "**包括所有预测意向分数**" 框。
    4. 单击 "**发布到生产槽**"。

        ![发布设置](images/AzureLabs-Lab3-22.png)

26. 在 "*资源和密钥*" 部分中：

    1.  在 Azure 门户中选择为服务实例设置的区域。
    2.  你将注意到下面的一个**Starter_Key**元素，请将其忽略。
    3.  单击 "**添加密钥**"，并在创建服务实例时插入在 Azure 门户中获取的*密钥*。 如果你的 Azure 和 LUIS 门户登录到同一用户，你将向你提供 "*租户名称*"、"*订阅名称*" 和你想要使用的*密钥*的下拉菜单（与你之前在 Azure 门户中提供的名称相同）。

    > [!IMPORTANT] 
    > 在 "*终结点*" 下，获取与所插入的密钥对应的终结点副本，然后在代码中立即使用该副本。
 
## <a name="chapter-3--set-up-the-unity-project"></a>第3章–设置 Unity 项目

下面是使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。

1.  打开*Unity* ，并单击 "**新建**"。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab3-24.png)

2.  你现在需要提供 Unity 项目名称，插入**MR_LUIS**。 请确保 "项目类型" 设置为 " **3d**"。 将位置设置为合适的**位置**（请记住，更接近根目录更好）。 然后单击 "**创建项目**"。

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab3-25.png)
 
3.  当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "编辑 > 首选项"，然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab3-26.png)
 
4.  接下来，通过单击 "**切换平台**" 按钮转到 "**文件 > 生成设置**"，并将平台切换到**通用 Windows 平台**。

    ![生成设置窗口，将平台切换到 UWP。](images/AzureLabs-Lab3-27.png)
 
5.  请参阅**文件 > 生成设置**，并确保：

    1. **目标设备**设置为**任何设备**

        > 对于 Microsoft HoloLens，将 "**目标设备**" 设置为 " *hololens*"。

    2. **生成类型**设置为**D3D**
    3. **SDK**设置为 "**最新安装**"
    4. **Visual Studio 版本**设置为 "**最新安装**"
    5. "**生成并运行**" 设置为 "**本地计算机**"
    6. 保存场景并将其添加到生成中。

        1. 通过选择 "**添加打开的场景**" 来执行此操作。 将显示 "保存" 窗口。
        
            ![单击 "添加打开的场景" 按钮](images/AzureLabs-Lab3-28.png)

        2. 为此创建新文件夹，并为将来的任何场景创建一个新文件夹，然后选择 "**新建文件夹**" 按钮以创建新文件夹，将其命名为**场景**。

            !["创建新脚本" 文件夹](images/AzureLabs-Lab3-29.png)

        3. 打开新创建的**场景**文件夹，然后*在 "文件名：文本" 字段*中，键入**MR_LuisScene**，然后按 "**保存**"。

            ![为新场景指定名称。](images/AzureLabs-Lab3-30.png)

    7. 现在，"*生成设置*" 中的其余设置应保留为默认值。

6. 在 "*生成设置*" 窗口中，单击 "**播放机设置**" 按钮，这会在*检查器*所在的空间中打开相关面板。 

    ![打开播放机设置。](images/AzureLabs-Lab3-31.png) 
 
7. 在此面板中，需要验证几项设置：

    1. 在 "**其他设置**" 选项卡中：

        1. **脚本运行时版本**应**稳定**（与 .net 3.5 等效）。
        2. **脚本编写后端**应为 **.net**
        3. **API 兼容级别**应为 **.net 4.6**

            ![更新其他设置。](images/AzureLabs-Lab3-32.png)
      
    2. 在 "**发布设置**" 选项卡的 "**功能**" 下，检查：

        1. **InternetClient**
        2. **十分**

            ![正在更新发布设置。](images/AzureLabs-Lab3-33.png)

    3. 在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK** 。

        ![更新 X R 设置。](images/AzureLabs-Lab3-34.png)

8.  "返回*生成设置* _" C# Unity_项目不再灰显;勾选此的旁边的复选框。 
9.  关闭 "生成设置" 窗口。
10. 保存场景和项目（**file > SAVE 场景/file > SAVE Project**）。

## <a name="chapter-4--create-the-scene"></a>第4章-创建场景

> [!IMPORTANT]
> 如果希望跳过本课程的*Unity 设置*组件，并继续直接进入代码，可以下载[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，将其作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后从[第5章](#chapter-5--create-the-microphonemanager-class)继续。 

1.  右键单击 "*层次结构" 面板*的空白区域中的 " **3d 对象**" 下的 "添加**平面**"。

    ![创建平面。](images/AzureLabs-Lab3-35.png)

2.  请注意，在*层次结构*中再次右键单击以创建多个对象时，如果仍选择最后一个对象，则所选对象将是新对象的父对象。 避免在层次结构内的空白区域中左键单击，然后右键单击。

3.  重复上述过程以添加以下对象：

    1. *球面*
    2. *圆柱体*
    3. *Cube*
    4. *3D 文本*

4.  生成的场景*层次结构*应类似于下图所示：

    ![场景层次结构设置。](images/AzureLabs-Lab3-36.png)
 
5.  在**摄像机**上左键单击以选择它，查看 "*检查器" 面板*，其中包含其所有组件。
6.  单击位于 "*检查器" 面板*底部的 "**添加组件**" 按钮。

    ![添加音频源](images/AzureLabs-Lab3-37.png)
 
7.  搜索名为 "*音频源*" 的组件，如上所示。
8.  此外，请确保将摄像机的*转换*组件设置为（0，0，0），可以通过按下相机的*转换*组件旁边的**齿轮**图标，然后选择 "**重置**" 来完成此操作。 *转换*组件如下所示：

    1.  *位置*设置为**0，0，0**。
    2.  *旋转*设置为**0，0，0**。

    > [!NOTE] 
    > 对于 Microsoft HoloLens，你还需要更改以下内容，这是**相机**组件（位于你的**主摄像机**上）的一部分：
    > - **清除标志：** 纯色。
    > - **背景**"黑色，Alpha 0" –十六进制颜色： #00000000。

9.  在**平面**上单击以将其选中。 在 "*检查器" 面板*中，用以下值设置*转换*组件：

    |       | 转换*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X-blade** | **误差**                  | **Z** |
    | 0     | -1                     | 0     |


10. 左键单击**球体**将其选中。 在 "*检查器" 面板*中，用以下值设置*转换*组件：

    |       | 转换*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X-blade** | **误差**                  | **Z** |
    | 2     | 1                      | 2     |

11. 左键单击**圆柱体**以将其选中。 在 "*检查器" 面板*中，用以下值设置*转换*组件：

    |       | 转换*位置* |       |
    |:-----:|:----------------------:|:-----:|
    | **X-blade** | **误差**                  | **Z** |
    | -2    | 1                      | 2     |

12. 左键单击**多维数据集**以将其选中。 在 "*检查器" 面板*中，用以下值设置*转换*组件：

    |        | 转换*位置* |       |  \| |       | 转换-*旋转* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X-blade** | **误差**                   | **Z** |  \| | **X-blade** | **误差**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. 左键单击新的**文本**对象以将其选中。 在 "*检查器" 面板*中，用以下值设置*转换*组件：

    |       | 转换*位置* |       |  \| |       | 转换-*缩放* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X-blade** | **误差**                  | **Z** |  \| | **X-blade** | **误差**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. 在**文本网格**组件中将**字体大小**更改为**50**。
15. 将**文本网格**对象的*名称*更改为 "**听写文本**"。

    ![创建3D 文本对象](images/AzureLabs-Lab3-38.png)
 
16. 层次结构面板结构现在应如下所示：

    ![场景视图中的文本网格](images/AzureLabs-Lab3-38b.png)


17. 最终场景应如下图所示：

    ![场景视图。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>第5章–创建 MicrophoneManager 类

要创建的第一个脚本是*MicrophoneManager*类。 接下来，你将创建*LuisManager*和*行为*类，最后是一个*注视*类（现在可以自由地创建所有这些类，但在每个章节中将会介绍）。

*MicrophoneManager*类负责：

-   检测连接到耳机或计算机的记录设备（以默认值为准）。
-   捕获音频（语音）并使用听写将其存储为字符串。
-   暂停语音后，将听写提交到*LuisManager*类。 

若要创建此类： 

1.  右键单击 "*项目" 面板*，**创建 > 文件夹**。 调用文件夹**脚本**。 

    ![创建脚本文件夹。](images/AzureLabs-Lab3-40.png)
 
2.  创建**脚本**文件夹后，双击它以打开。 然后，在该文件夹中，右键单击，**创建 > C#脚本**。 将脚本命名为*MicrophoneManager*。 

3.  双击 " *MicrophoneManager* " 以通过*Visual Studio*打开它。
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  然后在*MicrophoneManager*类中添加以下变量：

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  现在需要添加*唤醒（）* 和*Start （）* 方法的代码。 当类初始化时，将调用以下内容：

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
 
7.  现在，你需要应用程序用来启动和停止语音捕获，并将其传递给*LuisManager*类的方法。 

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

8.  添加语音暂停时要调用的*听写处理程序*。 此方法会将听写文本传递给*LuisManager*类。

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
    > 删除*Update （）* 方法，因为此类将不会使用它。

9.  在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

    > [!NOTE]
    > 此时，你会注意到在*Unity 编辑器控制台面板*中出现错误。 这是因为代码引用了将在下一章中创建的*LuisManager*类。

## <a name="chapter-6--create-the-luismanager-class"></a>第6章–创建 LUISManager 类

你可以创建*LuisManager*类，它将调用 Azure LUIS 服务。 

此类的目的是接收来自*MicrophoneManager*类的听写文本，并将其发送到要分析的*Azure 语言理解 API* 。

此类将反序列化*JSON*响应并调用*行为*类的适当方法来触发操作。

若要创建此类： 

1.  双击 "**脚本**" 文件夹以将其打开。 
2.  右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。 将脚本命名为*LuisManager*。 
3.  双击脚本以通过 Visual Studio 打开它。
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  首先，在*LuisManager* **类中创建三个类（** 在与*Start （）* 方法相同的脚本文件中），该文件将表示来自 Azure 的反序列化 JSON 响应。

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

6.  接下来，在*LuisManager*类中添加以下变量：
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  请确保现在将 LUIS 终结点置于（将从 LUIS 门户中获得）。

8.  现在需要添加*唤醒（）* 方法的代码。 当类初始化时，将调用此方法：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  现在，你需要此应用程序用来将*MicrophoneManager*类收到的听写发送到*LUIS*的方法，然后接收并反序列化响应。 
10. 一旦确定了意向值和关联实体后，就会将这些值传递给*行为*类的实例，以触发预期的操作。

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
 
11. 创建一个名为*AnalyseResponseElements （）* 的新方法，该方法将读取生成的*AnalysedQuery*并确定实体。 确定这些实体后，它们将被传递到要在操作中使用的*行为*类的实例。

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

            // Depending on the topmost recognized intent, read the entities name
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
    > 删除*Start （）* 和*Update （）* 方法，因为此类将不会使用它们。

12. 在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

> [!NOTE]
> 此时，你会注意到在*Unity 编辑器控制台面板*中出现了几个错误。 这是因为代码引用了将在下一章中创建的*行为*类。

## <a name="chapter-7--create-the-behaviours-class"></a>第7章–创建行为类

*行为*类将使用*LuisManager*类提供的实体触发操作。

若要创建此类： 

1.  双击 "**脚本**" 文件夹以将其打开。 
2.  右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。 将脚本命名为*行为*。 
3.  双击脚本以通过*Visual Studio*打开它。
4.  然后在*行为*类中添加以下变量：

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  添加*唤醒（）* 方法代码。 当类初始化时，将调用此方法：

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  下面的方法由*LuisManager*类（先前创建）调用，以确定哪个对象是查询的目标，然后触发相应的操作。

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
 
7.  添加*FindTarget （）* 方法，以确定哪一个*Gameobject*是当前意向的目标。 如果实体中未定义显式目标，则此方法默认为 "gazed" 的*GameObject* 。

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
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
    > 删除*Start （）* 和*Update （）* 方法，因为此类将不会使用它们。

8.  在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-8--create-the-gaze-class"></a>第8章–创建注视类

完成此应用需要完成的最后一个类是 "*注视*类"。 此类将对当前用户视觉对象集中的*GameObject*的引用进行更新。

若要创建此类： 

1.  双击 "**脚本**" 文件夹以将其打开。 
2.  右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。 将脚本命名为 "*注视*"。 
3.  双击脚本以通过*Visual Studio*打开它。
4.  为此类插入以下代码：

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
 
5.  在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-9--completing-the-scene-setup"></a>第9章-完成场景设置

1.  若要完成场景的设置，请将已创建的每个脚本从 "脚本" 文件夹拖到 "*层次结构" 面板*中的 "**照相机**" 对象。
2.  选择**主摄像机**，查看*检查器面板*，您应该能够看到已附加的每个脚本，您会注意到每个脚本上都有一些参数还需要设置。

    ![设置照相机引用目标。](images/AzureLabs-Lab3-41.png)

3.  若要正确设置这些参数，请遵循以下说明：

    1. *MicrophoneManager*：

        - 从 "*层次结构" 面板*中，将 "**听写文本**" 对象拖到 "**听写文本**参数值" 框中。

    2. *行为*，从 "*层次结构" 面板*：

        - 将**球体**对象拖到 "*球*引用目标" 框中。
        - 将**圆柱体**拖到 "*圆柱形*引用目标" 框中。
        - 将**多维数据集**拖到 "*多维数据集*引用目标" 框中。

    3. *注视*：

        - 将 "*注视最大距离*" 设置为**300** （如果尚未安装）。 

4.  结果应如下图所示：

    ![当前设置了照相机引用目标。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>第10章–在 Unity 编辑器中测试

测试场景设置是否已正确实现。

请确保：

-   所有脚本都附加到**相机**对象上。 
-   *主相机检查器面板*中的所有字段均已正确分配。

1.  按下*Unity 编辑器*中的 "**播放**" 按钮。 应用应在附加的沉浸式耳机中运行。

2.  尝试一些最谈话，例如：

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > 如果在 Unity 控制台中看到有关默认音频设备变化的错误，场景可能无法按预期方式工作。 这是因为混合现实门户使用内置麦克风处理随附的耳机的方式。 如果看到此错误，只需停止场景并再次启动，应按预期方式工作。

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>第11章–构建和旁加载 UWP 解决方案

确保应用程序在 Unity 编辑器中运行后，便可以生成并部署了。

若要生成：

1.  单击 "**文件" > "保存**"，保存当前场景。
2.  请参阅**文件 > 生成设置**。
3.  勾选称为 " **Unity C#项目**" 的框（在创建 UWP 项目后，可用于查看和调试代码。
4.  单击 "**添加打开的场景**"，然后单击 "**生成**"。

    !["生成设置" 窗口](images/AzureLabs-Lab3-43.png)

4.  系统将提示您选择要在其中生成解决方案的文件夹。 

5.  创建一个*生成*文件夹，在该文件夹中创建另一个文件夹，其中包含所选的适当名称。 
6.  单击 "**选择文件夹**"，在该位置开始生成。
 
    ![创建生成文件夹](images/AzureLabs-Lab3-44.png)
    ![选择生成文件夹](images/AzureLabs-Lab3-45.png)
 
7.  Unity 完成生成后（可能需要一些时间），应在生成的位置打开**文件资源管理器**窗口。

在本地计算机上部署：

1.  在*Visual Studio*中，打开已在[上一章](#chapter-10--test-in-the-unity-editor)中创建的解决方案文件。
2.  在**解决方案平台**中，选择 " **X86**，**本地计算机**"。
3.  在**解决方案配置**中，选择 "**调试**"。

    > 对于 Microsoft HoloLens，你可能会发现将其设置为*远程计算机*会更容易，因此你不会受限到计算机上。 不过，还需要执行以下操作：
    > - 知道您的 HoloLens 的**IP 地址**，可在 "*设置" > 网络 & Internet > > "高级选项*" 中找到;IPv4 是应使用的地址。 
    > - 确保**开发人员模式**已**打开**;在 "设置" 中找到 *> 更新开发人员 & 安全 >* 。

    ![部署应用](images/AzureLabs-Lab3-46.png)
 
4.  请在 "**生成" 菜单**中，单击 "**部署解决方案**"，将应用程序旁加载到计算机上。
5.  应用现在应显示在已安装的应用列表中，可以启动了！
6.  启动后，应用会提示你授权访问_麦克风_。 使用*运动控制器*、*语音输入*或*键盘*按 **"是"** 按钮。 

## <a name="chapter-12--improving-your-luis-service"></a>第12章-改进 LUIS 服务

>[!IMPORTANT] 
> 本章非常重要，可能需要多次迭代，因为这将有助于提高 LUIS 服务的准确性：请确保完成此操作。

若要改进 LUIS 提供的理解级别，需要捕获新的最谈话，并使用它们重新训练 LUIS 应用。

例如，你可能已经训练了 LUIS 来理解 "增加" 和 "升迁"，但又不希望你的应用程序也知道 "放大" 等词呢？

一旦你使用了应用程序几次，你所说的一切将被 LUIS 收集，并在 LUIS 门户中可用。

1.  请按照以下[链接](https://www.luis.ai/home)打开门户应用程序，并登录。
2.  用 MS 凭据登录后，单击你的*应用名称*。
3.  单击页面左侧的 "**查看终结点最谈话**" 按钮。

    ![查看最谈话](images/AzureLabs-Lab3-47.png)
 
4.  将显示一个列表，其中包含已由混合现实应用程序发送到 LUIS 的最谈话。

    ![最谈话列表](images/AzureLabs-Lab3-48.png)
 
你会注意到一些突出显示的*实体*。 

通过将鼠标悬停在每个突出显示的单词上，你可以查看每个查询文本并确定哪些实体已正确识别，哪些实体出现错误以及哪些实体丢失。

在上面的示例中，发现 "鱼叉式" 一词已突出显示为目标，因此需要更正此错误，这是通过将鼠标悬停在单词上并单击 "**删除标签**" 来完成的。

![检查最谈话](images/AzureLabs-Lab3-49.png)
![删除标签图像](images/AzureLabs-Lab3-50.png)
 
5.  如果找到完全错误的最谈话，可以使用屏幕右侧的 "**删除**" 按钮删除它们。

    ![删除错误的最谈话](images/AzureLabs-Lab3-51.png)

6.  或者，如果您认为 LUIS 已正确解释查询文本，则可以使用 "**添加到对齐意向**" 按钮来验证其理解。

    ![添加到对齐意向](images/AzureLabs-Lab3-52.png)

7.  对所有显示的最谈话进行排序后，请尝试重新加载页面，查看是否有更多的可用功能。
8.  尽可能多地重复此过程以提高应用程序理解。 

**玩得愉快！**

## <a name="your-finished-luis-integrated-application"></a>已完成的 LUIS 集成应用程序

恭喜，你构建了一个使用 Azure 语言理解智能服务的混合现实应用，以了解用户所说的内容，并对该信息采取措施。

![实验室结果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

使用此应用程序时，您可能会注意到，如果注视地面对象并要求更改其颜色，则会这样做。 您可以如何阻止您的应用程序更改地面颜色？

### <a name="exercise-2"></a>练习2

尝试扩展 LUIS 和应用功能，为场景中的对象添加其他功能;例如，在注视点处创建新的对象，具体取决于用户所显示的内容，然后可以将这些对象和当前场景对象与现有的命令一起使用。 
