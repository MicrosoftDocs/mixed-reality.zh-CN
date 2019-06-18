---
title: MR 和 Azure 309-Application insights
description: 完成此课程以了解如何收集有关在混合的现实应用程序中的用户行为，请使用 Azure Application Insights 服务的分析。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 应用程序见解，沉浸式、 hololens、 vr
ms.openlocfilehash: 838dbe38724d29f4c5987e2f6ac7a07231015c82
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593002"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR 和 Azure 309:应用程序见解

![最终产品-启动](images/AzureLabs-Lab309-00.png)

在本课程中，您将学习如何将 Application Insights 功能添加到混合的现实应用程序，使用 Azure Application Insights API 收集有关用户行为分析。

Application Insights 是 Microsoft 服务，从而允许开发人员从其应用程序收集分析数据和从易于使用门户管理。 分析可以是任何内容，从你想要收集的自定义信息的性能。 有关详细信息，请访问[Application Insights 页](https://azure.microsoft.com/services/application-insights/)。

已完成本课程，会创建一个混合的现实沉浸式头戴式应用程序，将能够执行以下操作：

1.  允许用户注视和场景中移动。
2.  触发的分析，以发送*Application Insights 服务*、 通过使用提供注视和邻近场景中的对象。
3.  应用还将在提取信息有关的对象已被用户，最接近过去 24 小时内的服务时调用。 该对象将更改其颜色为绿色。

本课程将介绍如何为基于 Unity 的示例应用程序从 Application Insights 服务，获取结果。 它将取决于您要应用于您可能要构建一个自定义应用程序的这些概念。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 309:应用程序见解</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。 按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。 使用 HoloLens，您可能注意到某些 echo 语音捕获过程。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。 你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。

我们建议以下硬件和软件本课程：

- 开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式
- 一组的耳机使用内置的麦克风 （如果耳机不具有内置的麦克风和扬声器）
- Internet 访问的 Azure 设置和 Application Insights 数据检索

## <a name="before-you-start"></a>开始之前

若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。

> [!WARNING] 
> 请注意，将数据*Application Insights*花费的时间，因此请耐心等待。 如果你想要检查此服务已收到你的数据，请查看[第 14 章](#chapter-14---the-application-insights-service-portal)，这将向您演示如何在门户中导航。

## <a name="chapter-1---the-azure-portal"></a>第 1 章-Azure 门户

若要使用*Application Insights*，将需要创建和配置*Application Insights 服务*在 Azure 门户中。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**新建**在左上角，并搜索*Application Insights*，然后单击**Enter**。

    > [!NOTE]
    > 单词**新建**可能已替换**创建资源**，较新的门户网站中。

    ![Azure 门户](images/AzureLabs-Lab309-01.png)

3.  向右该新页面将提供的说明*Azure Application Insights*服务。 在左下角此页上，选择**创建**按钮，以创建与此关联服务。

    ![Azure 门户](images/AzureLabs-Lab309-02.png)

4.  一旦你单击**创建**:

    1.  插入所需**名称**此服务实例。

    2.  作为**应用程序类型**，选择**常规**。

    3.  选择相应**订阅**。

    4.  选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5.  选择**位置**。

    6.  您还需要确认你已了解的条款和条件应用于此服务。

    7.  选择“创建”  。

        ![Azure 门户](images/AzureLabs-Lab309-03.png)

5.  一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。

6.  创建服务实例后，在门户中将显示一条通知。

    ![Azure 门户](images/AzureLabs-Lab309-04.png)

7.  单击通知以了解新的服务实例。

    ![Azure 门户](images/AzureLabs-Lab309-05.png)

8.  单击**转到资源**通知探索新的服务实例中的按钮。 你将会转到新*Application Insights 服务*实例。

    ![Azure 门户](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  保持此 web 页面打开并且易于访问，你将返回到此处通常以查看收集的数据。

    > [!IMPORTANT]
    > 若要实现 Application Insights，你将需要使用三 （3） 的特定值：**检测密钥**，**应用程序 ID**，和**API 密钥**。 下面您将了解如何从你的服务中检索这些值。 请务必记下这些值在空白*记事本*页上，因为在代码中，将很快使用它们。

9.  若要查找**检测密钥**，将需要向下滚动服务函数列表，然后单击**属性**，显示选项卡将显示**服务密钥**。

    ![Azure 门户](images/AzureLabs-Lab309-07.png)

10. 有点下面**属性**，将为您**API 访问**，您需要单击。 右侧面板将提供**应用程序 ID**的您的应用程序。

    ![Azure 门户](images/AzureLabs-Lab309-08.png)

11. 与**应用程序 ID**面板保持打开，单击**创建 API 密钥**，这将打开*创建 API 密钥*面板。

    ![Azure 门户](images/AzureLabs-Lab309-09.png)

12. 现在打开内*创建 API 密钥*面板中，键入描述，并**选中三个框**。

13. 单击**生成密钥**。 你**API 密钥**将创建并显示。 

    ![Azure 门户](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > 这是唯一一次你**服务密钥**将显示，因此请确保您现在制作一份。

## <a name="chapter-2---set-up-the-unity-project"></a>第 2 章-设置 Unity 项目

以下是一组典型使用混合现实中，进行开发，并在这种情况下，是合适的模板的其他项目。

1.  打开*Unity*然后单击**新建**。

    ![设置 Unity 项目](images/AzureLabs-Lab309-11.png)

2.  现在将需要提供 Unity 项目的名称，插入**MR\_Azure\_应用程序\_Insights**。 请确保*模板*设置为**3D**。 设置*位置*到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![设置 Unity 项目](images/AzureLabs-Lab309-12.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑\>首选项**，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![设置 Unity 项目](images/AzureLabs-Lab309-13.png)

4.  接下来，请转到**文件\>生成设置**，并切换到平台**通用 Windows 平台**，通过单击**切换平台**按钮。

    ![设置 Unity 项目](images/AzureLabs-Lab309-14.png)

5.  转到**文件\>生成设置**并确保选中：

    1.  **设备为目标**设置为**任何设备**

        > 对于 Microsoft HoloLens，设置**目标设备**到*HoloLens*。

    2.  **生成的类型**设置为**D3D**

    3.  **SDK**设置为**最新安装**

    4.  **生成并运行**设置为**本地计算机**

    5.  保存场景，并将其添加到生成。

        1.  选择执行此**添加打开场景**。 保存窗口将显示。

            ![设置 Unity 项目](images/AzureLabs-Lab309-15.png)

        2. 为此，和任何将来的场景，创建新文件夹，然后单击**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![设置 Unity 项目](images/AzureLabs-Lab309-16.png)

        3. 打开新建**场景**文件夹，然后在*文件名：* 文本字段中，键入**ApplicationInsightsScene**，然后单击**保存**.

            ![设置 Unity 项目](images/AzureLabs-Lab309-17.png)

6.  中的剩余设置，**生成设置**，应暂时保留为默认值。

7.  在**生成设置**窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。

    ![设置 Unity 项目](images/AzureLabs-Lab309-18.png)

8. 在此面板中，需要验证几个设置：

    1.  在中**其他设置**选项卡：

        1.  **脚本编写** **运行时版本**应**实验 （.NET 4.6 等效）** ，这将触发需要重新启动编辑器。

        2.  **脚本编写后端**应为 **.NET**

        3.  **API 兼容性级别**应为 **.NET 4.6**

        ![设置 Unity 项目](images/AzureLabs-Lab309-19.png)

    2.  内**发布设置**选项卡上，在**功能**，检查：

        - **InternetClient**     

            ![设置 Unity 项目](images/AzureLabs-Lab309-20.png)

    3.  中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows Mixed RealitySDK**添加。

        ![设置 Unity 项目](images/AzureLabs-Lab309-21.png)

9.  回到**生成设置**， **Unity C\#项目**不再灰显; 选中它旁边的复选框。

10.  关闭生成设置窗口。

11.  保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。


## <a name="chapter-3---import-the-unity-package"></a>第 3 章-导入 Unity 程序包

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[Azure MR 309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)，将其导入项目中，作为[**自定义软件包**](https://docs.unity3d.com/Manual/AssetPackages.html)。 这还将包含下一章中的 Dll。 导入后，继续从[**第 6 章**](#chapter-6---create-the-applicationinsightstracker-class)。

> [!IMPORTANT]
> 若要使用 Application Insights 在 Unity 中，需要导入 DLL，以及 Newtonsoft DLL。 这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。 这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。

若要导入到你自己的项目的 Application Insights，请确保你有[下载.unitypackage，包含插件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)。 然后，执行以下操作：

1.  添加 **.unitypackage**到使用 Unity**资产\>导入包\>自定义包**菜单选项。

2.  在中**导入 Unity 程序包**弹出框、 下 （其中包含） 确保一切**插件**处于选中状态。

    ![导入 Unity 程序包](images/AzureLabs-Lab309-22.png)

3.  单击**导入**按钮，将项添加到你的项目。

4.  转到**Insights**下的文件夹**插件**项目中查看并选择以下插件*仅*:

    -   Microsoft.ApplicationInsights

    ![导入 Unity 程序包](images/AzureLabs-Lab309-23.png)

5.  与此*插件*选择，确保**Any 平台**是**未选中**，然后确保**WSAPlayer**也是**取消选中**，然后单击**应用**。 执行此操作是只是为了确认正确配置文件。

    ![导入 Unity 程序包](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > 将标记此类的插件，将它们配置为仅使用在 Unity 编辑器中。 有一组不同的 Dll 从 Unity 项目会导出后，将使用 WSA 文件夹中。

6.  接下来，您需要打开**WSA**文件夹，在**Insights**文件夹。 您将看到刚配置的相同文件的副本。 选择此文件，然后再检查器中，请确保**Any 平台**是**取消选中**，然后确保**仅** **WSAPlayer**是**检查**。 单击 **“应用”** 。

    ![导入 Unity 程序包](images/AzureLabs-Lab309-25.png)

7. 现在需要遵循**步骤 4-6**，但对于*Newtonsoft*插件相反。 请参阅下面的屏幕快照的结果应如下所示。

    ![导入 Unity 程序包](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>第 4 章-设置相机和用户控件

在这一章中您将设置照相机和控件允许用户查看和在场景中移动。

1.  右键单击空白区域在层次结构窗格中，然后**创建 > 空**。

    ![设置相机和用户控件](images/AzureLabs-Lab309-26.png)

2.  重命名为新的空 GameObject**照相机父**。

    ![设置相机和用户控件](images/AzureLabs-Lab309-27.png)

3.  右键单击空白区域在层次结构窗格中，然后**3D 物体**，然后在**球体**。

4.  重命名为球体**右侧**。

5.  设置**转换规模**的向右**0.1，0.1，0.1**

    ![设置相机和用户控件](images/AzureLabs-Lab309-28.png)

6.  删除**球体碰撞体**组件从通过单击右侧**齿轮**中*球体碰撞体*组件，然后**删除组件**.

    ![设置相机和用户控件](images/AzureLabs-Lab309-29.png)

7.  在层次结构面板拖动**Main Camera**并**右下**对象上**照相机父**对象。

    ![设置相机和用户控件](images/AzureLabs-Lab309-30.png)

8.  设置**转换位置**两个**Main Camera**并**右侧**对象传递给**0，0，0**。

    ![设置相机和用户控件](images/AzureLabs-Lab309-31.png)

    ![设置相机和用户控件](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>第 5 章-设置在 Unity 场景中的对象

现在将为您的场景，用户可与之交互创建一些基本形状。

1.  在中的空白区域中单击右键*层次结构面板*，然后在**3D 物体**，然后选择**平面**。

2.  设置在平面**转换位置**到**0，-1，0**。

3.  设置在平面**转换规模**到**5、 1、 5**。

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-33.png)

4.  创建基本材料要用于你**平面**对象，以便更轻松地查看其他形状。 导航到您*项目面板*，右键单击，然后**创建**后, 跟**文件夹**，以创建新的文件夹。 其命名为**材料**。

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-34.png) ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-35.png)

5.  打开**材料**文件夹，然后右键单击，单击**创建**，然后**材料**，以创建新材料。 其命名为**蓝色**。

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-36.png) ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-37.png)

6.  与新**蓝色**材料，看在选择*Inspector*，然后单击矩形窗口中的以及**Albedo**。 选择蓝色颜色 (如下一个图是**十六进制颜色：\#3592FFFF**)。 选择后，请单击关闭按钮。

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-38.png)

7.  将从你新材料**材料**文件夹中的，拖动到新创建**平面**，在您的场景中 (或将其放在**平面**对象内*层次结构*)。

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-39.png)

8.  在中的空白区域中单击右键*层次结构面板*，然后在**三维对象、 Capsule**。

    -  与**Capsule**选择，更改其**转换** *位置*到： **-10、 1、 0**。

9.  在中的空白区域中单击右键*层次结构面板*，然后在**三维对象、 多维数据集**。

    -  与**多维数据集**选择，更改其**转换** *位置*到：**0, 0, 10**.

10. 在中的空白区域中单击右键*层次结构面板*，然后在**三维对象、 球体**。

    -  与**球体**选择，更改其**转换***位置*到：**10, 0, 0**.

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > 这些*位置*的值为*建议*。 你可以随意设置对象的位置为喜好，但如果对象距离是不与相机距离太远，则应用程序的用户更容易。

11. 当运行你的应用程序时，它需要能够识别中的场景，来实现此目的的对象，它们需要进行标记。 选择一个对象，并在*Inspector*面板中，单击**添加标记...** ，这会交换*Inspector*与**标记和分层式**面板。

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. 单击 **+ （加）** 符号，然后键入标记名称作为**ObjectInScene**。

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > 如果使用你的标记的不同名称，您需要确保还进行此更改*DataFromAnalytics*， *ObjectTrigger*，并*注视*，更高版本，脚本，以便你对象发现，并检测到，在您的场景。

13. 使用创建的标记，现在需要将其应用于所有这三个对象。 从*层次结构*，保存**Shift**键，然后单击**Capsule**，**多维数据集**，并**球体**，对象，然后在*Inspector*，单击旁边的下拉列表菜单**标记**，然后单击*ObjectInScene*标记创建。

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>章 6-创建 ApplicationInsightsTracker 类

您需要创建的第一个脚本是**ApplicationInsightsTracker**，负责：

1.  创建基于用户交互要提交到 Azure Application Insights 的事件。

2. 正在创建相应的事件名称，具体取决于用户交互。

3. 正在提交到 Application Insights 服务实例的事件。

若要创建此类：

1.  在中右击*项目面板*，然后**创建 > 文件夹**。 将文件夹命名为**脚本**。

    ![创建 ApplicationInsightsTracker 类](images/AzureLabs-Lab309-46.png)  ![创建 ApplicationInsightsTracker 类](images/AzureLabs-Lab309-47.png)

2.  与**脚本**创建文件夹，双击它，以打开。 然后，在该文件夹中，右键单击，**创建 > C\#脚本**。 脚本命名为**ApplicationInsightsTracker**。

3.  双击新**ApplicationInsightsTracker**脚本以将其与打开**Visual Studio**。

4.  更新的脚本在顶部的命名空间如下所示：

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  在类中插入以下变量：

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > 设置**instrumentationKey，applicationId 和 API_Key**相应地，使用值*服务密钥*从 Azure 门户中所述[第 1 章](#chapter-1---the-azure-portal)，步骤 9及更高版本。

6.  然后添加**start （)** 并**Awake()** 类初始化时将调用的方法：

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  添加负责发送的事件和指标注册你的应用程序的方法：

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-7---create-the-gaze-script"></a>章 7-创建的视线移动脚本

要创建的下一步脚本位于**注视**脚本。 此脚本负责创建*Raycast*会从转发投影的*Main Camera*，以检测用户查看的对象。 在这种情况下， *Raycast*需要确定如果用户正在查看的对象**ObjectInScene**标记，并将然后计算时间用户*gazes*在该对象。

1.  双击**脚本**文件夹，将其打开。

2.  内右击**脚本**文件夹中，单击**创建** > **C\#脚本**。 脚本命名为**注视**。

3.  双击要使用 Visual Studio 中打开的脚本。

4.  现有代码替换为以下：

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  为代码**Awake()** 并**start （)** 方法现在需要添加。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  内部**注视**类中，添加下面的代码**update （)** 到项目的方法*Raycast*和检测对目标的影响：

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  添加**ResetFocusedObject()** 方法，以将数据发送到**Application Insights**时用户已介绍了一个对象。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  现在已完成**注视**脚本。 保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-8---create-the-objecttrigger-class"></a>章 8-创建 ObjectTrigger 类

若要创建所需的下一个脚本是**ObjectTrigger**，负责：

- 添加到 Main Camera 冲突所需的组件。
- 检测相机是否标记为的对象附近**ObjectInScene**。

若要创建脚本：

1.  双击**脚本**文件夹，将其打开。

2.  内右击**脚本**文件夹中，单击**创建** **C\# > 脚本**。 脚本命名为**ObjectTrigger**。

3.  双击要使用 Visual Studio 中打开的脚本。 现有代码替换为以下：

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-9---create-the-datafromanalytics-class"></a>章 9-创建 DataFromAnalytics 类

您现在需要创建**DataFromAnalytics**脚本，它负责：

- 正在提取有关哪些对象具有已接近相机最多的分析数据。
- 使用*服务密钥*，允许与 Azure Application Insights 服务实例的通信。
- 排序的对象在场景中，根据其具有最高的事件计数。
- 为更改材料的颜色，最额对象的*绿色*。

若要创建脚本：

1.  双击**脚本**文件夹，将其打开。

2.  内右击**脚本**文件夹中，单击**创建** **C\# > 脚本**。 脚本命名为**DataFromAnalytics**。

3.  双击要使用 Visual Studio 中打开的脚本。

4.  插入以下命名空间：

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  在脚本内插入以下：

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  内**DataFromAnalytics**类中，右键后**start （)** 方法中，添加以下方法调用**FetchAnalytics()** 。 此方法负责使用填充的键/值对列表*GameObject*和占位符事件计数数量。 然后初始化**GetWebRequest()** 协同例程。 对调用的查询结构*Application Insights*可在此方法内找到此外，作为*查询 URL*终结点。

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  下方**FetchAnalytics()** 方法中，添加一个名为方法**GetWebRequest()** ，它将返回*IEnumerator*。 此方法负责请求的一个事件，具有特定相对应的次数*GameObject*，已调用内*Application Insights*。 当发送的所有查询均都返回时， **DetermineWinner()** 调用方法。

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  下一个方法是**DetermineWinner()** ，该对的列表进行排序*GameObject*并*Int*对，根据最高的事件计数。 然后，它更改材料的颜色*GameObject*到*绿色*（作为它是否具有最高的计数的反馈）。 这将显示包含分析结果的消息。

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  添加类结构，用于反序列化 JSON 对象，从收到*Application Insights*。 在最底部的添加这些类您**DataFromAnalytics**类文件**外部**类定义。

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. 请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-10---create-the-movement-class"></a>章 10-创建移动类

**移动**脚本是下一步将需要创建的脚本。 它负责：

- 要移动根据方向照相机 Main Camera。
- 将所有其他脚本添加到场景对象。

若要创建脚本：

1.  双击**脚本**文件夹，将其打开。

2.  内右击**脚本**文件夹中，单击**创建** > **C\#脚本**。 脚本命名为**移动**。

3.  要将其与打开的脚本上双击*Visual Studio*。

4.  现有代码替换为以下：

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  内**移动**类，*如下*空**update （)** 方法中，插入允许用户使用现有控制器移动虚拟空间中的以下方法：

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  最后添加的方法调用中**update （)** 方法。

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-11---setting-up-the-scripts-references"></a>第 11 章 — 设置脚本引用

您需要将放在本章**移动**拖到编写脚本**照相机父**，并设置其引用目标。 然后，该脚本将处理放置他们需要为其他脚本。

1.  从**脚本**文件夹中的*项目面板*，将**移动**脚本到**照相机父**位于中的对象*层次结构面板*。

    ![设置在 Unity 场景中的脚本引用](images/AzureLabs-Lab309-48.png)

2.  单击**照相机父**。 中*层次结构面板*，拖动**右下**对象*层次结构面板*引用目标**控制器**中*检查器面板*。 设置**用户速度**到**5**，如下图中所示。

    ![设置在 Unity 场景中的脚本引用](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>第 12 章 — 生成 Unity 项目

此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。

1.  导航到**生成设置**， **(文件 >...生成设置)** .

2.  从**生成设置**窗口中，单击**生成**。

    ![生成 Unity 项目到 UWP 的解决方案](images/AzureLabs-Lab309-50.png)

3.  一个**文件资源管理器**窗口将弹出窗口，提示您指定用于生成的位置。 创建一个新文件夹 (通过单击**新文件夹**左上角)，并将其命名**生成**。

    ![生成 Unity 项目到 UWP 的解决方案](images/AzureLabs-Lab309-51.png)

    1.  打开新**生成**文件夹，并创建另一个文件夹 (使用**新的文件夹**一次)，并将其命名**MR\_Azure\_应用程序\_Insights**。

        ![生成 Unity 项目到 UWP 的解决方案](images/AzureLabs-Lab309-52.png)

    2.  与**MR\_Azure\_应用程序\_Insights**文件夹选择，单击**选择文件夹**。 该项目将花大约一分钟生成。

4.  遵循*构建*，**文件资源管理器**将显示新项目的位置。

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>第 13 章 — MR_Azure_Application_Insights 应用部署到你的计算机

若要部署**MR\_Azure\_应用程序\_Insights**在本地计算机上的应用：

1.  打开解决方案文件的应用**MR\_Azure\_应用程序\_Insights**中的应用**Visual Studio**。

2.  在中**解决方案平台**，选择**x86，本地计算机**。

3.  在中**解决方案配置**选择**调试**。

    ![生成 Unity 项目到 UWP 的解决方案](images/AzureLabs-Lab309-53.png)

4.  转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。

5.  你的应用现在应出现在已安装的应用，准备好启动列表中。

6. 启动混合的现实应用程序。

7. 接近对象并查看它们，场景中移动时*Azure Insight 服务*已收集足够的事件数据，它将设置已接近最大到绿色的对象。

> [!IMPORTANT] 
> 尽管的平均等待时间*事件和指标*要收集的服务需要大约 15 分钟，在某些场合下，这可能需要最多 1 小时。

## <a name="chapter-14---the-application-insights-service-portal"></a>第 14 章 — 在 Application Insights 服务门户

已在场景周围漫游并在多个对象 gazed 可以看到中收集的数据后*Application Insights 服务*门户。

1.  请返回到 Application Insights 服务门户。

2.  单击*指标资源管理器*。

    ![查看收集的数据](images/AzureLabs-Lab309-54.png)

3.  它将在包含图表示的选项卡中打开*事件和指标*与应用程序相关。 如上所述，则可能要在图表中显示的数据需要一些时间 （最多 1 小时）

    ![查看收集的数据](images/AzureLabs-Lab309-55.png)

4.  单击*事件栏*中*的事件总数*由应用程序版本，若要查看其名称与事件的详细的明细。

    ![查看收集的数据](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>在完成的 Application Insights 服务应用程序

祝贺你，构建利用 Application Insights 服务来监视您的应用程序中的用户的活动的混合的现实应用。

![课程结果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Bonus 练习

**练习 1**

请尝试生成，而不是手动创建 ObjectInScene 对象并设置其坐标在脚本中的平面。 这样一来，你也可以要求 Azure 最热门对象时 （不管是从结果中的视线移动或邻近性） 和 spawn*额外*这些对象之一。

**练习 2**

在 Application Insights 对结果进行排序的时间，以便获取最相关的数据，并在应用程序中实现该时间敏感数据。

