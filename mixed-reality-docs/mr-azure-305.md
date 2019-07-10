---
title: MR 和 Azure 305-函数和存储
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 存储和函数。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 函数、 存储、 hololens，令人着迷，vr
ms.openlocfilehash: 5f3d0c6990249bc32e4c0f55c72dd884c4c2214e
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694559"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR 和 Azure 305:函数和存储

![最终产品-启动](images/AzureLabs-Lab5-00.png)

在本课程中，您将学习如何创建和使用 Azure Functions 以及如何使用 Azure 存储资源，在混合的现实应用程序中存储数据。

*Azure Functions*是一个 Microsoft 服务，它允许开发人员运行小段代码，函数，在 Azure 中。 这使您能够将工作委托给云，而不是本地应用程序，它可以有许多好处。 *Azure Functions*支持多种开发语言，包括 C\#，F\#，Node.js、 Java 和 PHP。 有关详细信息，请访问[Azure Functions 项目](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

*Azure 存储*是 Microsoft 云服务，使开发人员可以使用存储数据，它将是高度可用、 安全、 持久、 可缩放和冗余的保险。 这意味着，Microsoft 将为您处理所有维护和关键问题。 有关详细信息，请访问[Azure 存储文章](https://docs.microsoft.com/azure/storage/common/storage-introduction)。

已完成本课程，会创建一个混合的现实沉浸式头戴式应用程序，将能够执行以下操作：

1.  允许用户看围绕一个场景。
2.  触发生成的对象，当用户在一个三维 'button' gazes。
3.  生成的对象将选择的 Azure 函数。
4.  在生成的每个对象，该应用程序会将存储在中的对象类型*Azure 文件*，它位于*Azure 存储*。
5.  在加载第二次*Azure 文件*将检索数据，并将其用它来重播从应用程序的前一个实例的生成操作。

在您的应用程序，它是取决于您关于如何将与您的设计集成结果。 本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。 它是作业以使用此课程以增强你的混合的现实应用程序中获取的知识。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 和 Azure 305:函数和存储</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。 按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。 你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.

我们建议以下硬件和软件本课程：

- 开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式
- 对用于创建 Azure 资源的 Azure 帐户的订阅
- 用于 Azure 的安装程序和数据检索的 Internet 访问权限

## <a name="before-you-start"></a>开始之前

若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。

## <a name="chapter-1---the-azure-portal"></a>第 1 章-Azure 门户

若要使用**Azure 存储服务**，将需要创建和配置**存储帐户**在 Azure 门户中。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**新建**在左上角，并搜索*存储帐户*，然后单击**Enter**。

    ![azure 存储空间搜索](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > 单词**新建**可能已替换**创建资源**，较新的门户网站中。

3.  该新页面将提供的说明*Azure 存储帐户*服务。 在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。

    ![创建服务](images/AzureLabs-Lab5-02.png)

4.  一旦你单击**创建**:

    1.  插入*名称*对于你的帐户，请注意此字段仅接受数字和小写字母。

    2.  有关*部署模型*，选择**资源管理器**。

    3.  有关*帐户类型*，选择**存储 (常规用途 v1)** 。

    4.  确定*位置*为资源组 （如果要创建新的资源组）。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。

    5.  有关*复制*选择**读取-访问-异地冗余存储 (RA-GRS)** 。

    6.  有关*性能*，选择**标准**。

    7.  将保留*需要安全传输*作为**禁用**。

    8.  选择*订阅*。

    9. 选择*资源组*或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。 

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 您还需要确认你已了解的条款和条件应用于此服务。

    11. 选择“创建”  。

        ![输入的服务信息](images/AzureLabs-Lab5-03.png)

5.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。

6.  创建服务实例后，在门户中将显示一条通知。

    ![在 azure 门户中的新通知](images/AzureLabs-Lab5-04.png)

7.  单击通知以了解新的服务实例。

    ![转到资源](images/AzureLabs-Lab5-05.png)

8.  单击**转到资源**通知探索新的服务实例中的按钮。 你将会转到新*存储帐户*服务实例。

    ![访问密钥](images/AzureLabs-Lab5-06.png)

9.  单击*访问密钥*，以显示此云服务的终结点。 使用*记事本*或类似，供以后使用其中一个密钥复制到。 另请注意*连接字符串*值，因为它将在中使用*azure 服务*类，该类将更高版本创建。

    ![复制连接字符串](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>第 2 章-设置 Azure 函数

现在，您将编写**Azure** **函数**Azure 服务中。

可以使用**Azure Function**来执行几乎所有操作，你将处理经典函数在代码中，不同之处在于，此函数可由任何应用程序有访问你的 Azure 帐户的凭据。

若要创建 Azure 函数：

1.  从你*Azure 门户*，单击**新建**在左上角，并搜索*Function App*，然后单击**Enter**。

    ![创建 function app](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > 单词**新建**可能已替换**创建资源**，较新的门户网站中。

2.  该新页面将提供的说明*Azure Function App*服务。 在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。

    ![函数应用信息](images/AzureLabs-Lab5-09.png)

3.  一旦你单击**创建**:

    1.  提供*应用名称*。 可以在此处使用字母和数字 （允许使用大写或小写）。

    2.  选择首选*订阅*。

    3. 选择*资源组*或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。 

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  对于此练习中，选择*Windows*作为所选**OS**。

    5.  选择*消耗计划*有关**托管计划**。

    6.  确定*位置*为资源组 （如果要创建新的资源组）。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。 为了获得最佳性能的存储帐户中选择的同一区域。

    7.  有关*存储*，选择**使用现有**，然后使用下拉列表菜单中，找到你之前创建的存储。

    8.  将保留*Application Insights*关闭对于此练习。

        ![输入的函数应用的详细信息](images/AzureLabs-Lab5-10.png)

4.  单击“创建”  按钮。

5.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。

6.  创建服务实例后，在门户中将显示一条通知。

    ![新 azure 门户通知](images/AzureLabs-Lab5-11.png)

7.  单击通知以了解新的服务实例。 

    ![转到资源函数应用](images/AzureLabs-Lab5-12.png)

8.  单击**转到资源**通知探索新的服务实例中的按钮。 你将会转到新*Function App*服务实例。

9.  上*Function App*仪表板中，将鼠标悬停*函数*，在左侧面板中找到，然后单击 **+ （加）** 符号。

    ![创建新的函数](images/AzureLabs-Lab5-13.png)

10. 在下一页上，确保**Webhook + API**已选中，并为*选择一种语言，* 选择**CSharp**，因为它是本教程中使用的语言。 最后，单击**创建此函数**按钮。

    ![选择 web 挂钩 csharp](images/AzureLabs-Lab5-14.png)

11. 应会转到代码页 (run.csx)，否则，单击左侧面板内的函数列表中新创建的函数。

    ![打开新的函数](images/AzureLabs-Lab5-15.png)

12. 将以下代码复制到你的函数。 此函数只需将返回介于 0 和 2 调用时之间的随机整数。 不要担心现有代码，可随意将粘贴到顶部。

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. 选择“保存”。 

14. 结果应如下图所示。

15. 单击**获取函数 URL**并记下*终结点*显示。 将需要将其插入到*azure 服务*将稍后在本课程中创建的类。

    ![获取函数终结点](images/AzureLabs-Lab5-16.png)

    ![获取函数终结点](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>第 3 章 — 设置 Unity 项目

以下是一组典型使用 Mixed Reality 开发并在这种情况下，是合适的模板的其他项目。

设置和测试您的混合的现实沉浸式头戴式。

> [!NOTE]
> 你将**不**此课程需要运动控制器。 如果需要支持沉浸式头戴式设置，请[访问混合的现实设置文章](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  打开 Unity，然后单击**新建**。

    ![创建新的 unity 项目](images/AzureLabs-Lab5-17.png)

2.  现在，需要提供 Unity 项目的名称。 插入**MR_Azure_Functions**。 请确保项目类型设置为**3D**。 设置*位置*到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![为新的 unity 项目提供一个名称](images/AzureLabs-Lab5-18.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑** > **首选项**，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![设置 visual studio 为脚本编辑器](images/AzureLabs-Lab5-19.png)

4.  接下来，请转到**文件** > **生成设置**，并切换到平台**通用 Windows 平台**，通过单击**切换平台**按钮。

    ![切换到 uwp 的平台](images/AzureLabs-Lab5-20.png)

5.  转到**文件** > **生成设置**并确保选中：

    1. **设备为目标**设置为**任一设备**。

        > 对于 Microsoft HoloLens**目标设备**到*HoloLens*。

    2. **生成的类型**设置为**D3D**

    3. **SDK**设置为**最新安装**

    4. **Visual Studio 版本**设置为**最新安装**

    5. **生成并运行**设置为**本地计算机**

    6. 保存场景，并将其添加到生成。

        1.  选择执行此**添加打开场景**。 保存窗口将显示。

            ![添加打开场景](images/AzureLabs-Lab5-21.png)

        2.  创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![创建场景文件夹](images/AzureLabs-Lab5-22.png)

        3.  打开新建**场景**文件夹，然后在**文件名：** 文本字段中，键入**FunctionsScene**，然后按**保存**。

            ![保存函数场景](images/AzureLabs-Lab5-23.png)

6.  中的剩余设置，**生成设置**，应暂时保留为默认值。

    ![保存函数场景](images/AzureLabs-Lab5-24.png)

7.  在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。

    ![检查器中的播放机设置](images/AzureLabs-Lab5-25.png)

8.  在此面板中，需要验证几个设置：

    1.  在中**其他设置**选项卡：

        1.  **脚本运行时版本**应**实验**（.NET 4.6 等效），这将触发需要重新启动编辑器。
        2.  **脚本编写后端**应为 **.NET**
        3.  **API 兼容性级别**应为 **.NET 4.6**

    2.  内**发布设置**选项卡上，在**功能**，检查：
        
        -  **InternetClient**

            ![组功能](images/AzureLabs-Lab5-26.png)

    3.  中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows Mixed RealitySDK**添加。

        ![设置 XR 设置](images/AzureLabs-Lab5-27.png)

9.  回到*生成设置* *UnityC#项目*不再灰显; 选中它旁边的复选框。

    ![刻度线的 c# 项目](images/AzureLabs-Lab5-28.png)

10.  关闭生成设置窗口。

11. 保存您的场景和项目 (**文件** > **保存场景文件** > **保存项目**)。

## <a name="chapter-4---setup-main-camera"></a>第 4 章-安装程序主照相机

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)，并将其导入项目中，作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)。 这还将包含下一章中的 Dll。 导入后，继续从[第 7 章](#chapter-7---create-the-azureservices-class)。 

1.  在中*层次结构面板*，您会发现一个名为对象**Main Camera**，"内部"应用程序后，此对象表示"head"的观点。

2.  准备好 Unity 仪表板中，选择**主相机 GameObject**。 您会注意*检查器面板*（通常右侧，在仪表板中找到） 将显示的各种组件*GameObject*，与*转换*在顶部后, 接*照相机*，而另一些其他组件。 你将需要重置的转换的 Main Camera，使其正确定位。

3.  若要执行此操作，请选择**齿轮**旁的摄像机*转换*组件，然后选择**重置**。

    ![重置转换](images/AzureLabs-Lab5-29.png)

4.  然后更新**转换**组件如下所示：

    |         |    转换的位置   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | 转换的旋转 |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | 转换-横向 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![集相机转换](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>第 5 章-设置在 Unity 场景

1.  在空白区域中单击右键*层次结构面板*下**三维对象**，将添加**平面**。

    ![创建新计划](images/AzureLabs-Lab5-31.png)

2.  与**平面**对象选择，更改中的以下参数*检查器面板*:

    |       | 转换的位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | 转换-横向 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![设置平面位置和缩放](images/AzureLabs-Lab5-32.png)

    ![平面的场景视图](images/AzureLabs-Lab5-33.png)

3.  在的空白区域中单击右键*层次结构面板*下**三维对象**，将添加**多维数据集**。

    1.  重命名为多维数据集**GazeButton** （选定的多维数据集，按 F2）。

    2.  更改中的以下参数*检查器面板*:

        |       | 转换的位置 |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![集的视线移动按钮转换](images/AzureLabs-Lab5-34.png)

        ![对此按钮场景视图](images/AzureLabs-Lab5-35.png)

    3.  单击**标记**下拉列表按钮，然后单击**添加标记**以打开*标记和图层窗格*。

        ![添加新标记](images/AzureLabs-Lab5-36.png)

        ![选择加号](images/AzureLabs-Lab5-37.png)

    4.  选择 **+ （加）** 按钮，然后在*新标记名称*字段中，输入**GazeButton**，然后按**保存**。

        ![新的用户名标记](images/AzureLabs-Lab5-38.png)

    5.  单击**GazeButton**对象中*层次结构面板*，然后在*检查器面板*，将分配新创建**GazeButton**标记。

        ![分配新标记的视线移动按钮](images/AzureLabs-Lab5-39.png)

4.  右键单击**GazeButton**对象，在*层次结构面板*，并添加**空的 GameObject** (这将添加为*子*对象的名称。

5.  选择新的对象，并将其重命名**ShapeSpawnPoint**。

    1.  更改中的以下参数*检查器面板*:

        |       | 转换的位置 |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![更新形状生成点转换](images/AzureLabs-Lab5-40.png)

        ![形状生成点场景视图](images/AzureLabs-Lab5-41.png)

6.  接下来将创建**三维文字**对象以提供有关 Azure 服务的状态的反馈。

    右键单击**GazeButton**层次结构中面板再次并添加**3D 物体** > **三维文字**对象作为*子*。

    ![创建新的三维文字对象](images/AzureLabs-Lab5-42.png)

7.  重命名**三维文字**对象传递给**AzureStatusText**。

8.  更改**AzureStatusText**对象转换为如下所示：

    |       | 转换的位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | 转换-横向 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > 如果它似乎是关闭中心，因为这将在修复时不用再担心文本网格下方组件已更新。

9.  更改**文本 Mesh**组件以匹配下面：

    ![设置文本网格组件](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > 所选的颜色是十六进制颜色：**000000FF**，但可随意选择你自己，只需确保它是可读。

10. 层次结构面板结构现在应如下所示：

    ![文本在场景视图中的网格](images/AzureLabs-Lab5-43b.png)

10. 您的场景现在应如下所示：

    ![文本在场景视图中的网格](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>第 6 章-为 Unity 中导入 Azure 存储

您将使用 Azure 存储于 Unity （其本身使用.Net 的 Azure SDK）。 你可以阅读更多有关此[Unity 项目的 Azure 存储](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。

这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。 这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。

若要导入您自己的项目的 SDK，请确保已下载最新[从 GitHub.unitypackage](https://aka.ms/azstorage-unitysdk)。 然后，执行以下操作：

1.  添加 **.unitypackage**通过使用到 Unity 文件**资产** > **导入包** > **自定义包**菜单选项。

2.  在中**导入 Unity 程序包**框，弹出，你可以选择下的所有内容**插件** > **存储**。 取消选中其他任何内容，因为它不需要此课程。

    ![导入包](images/AzureLabs-Lab5-45.png)

3.  单击**导入**按钮将项添加到你的项目。

4.  转到*存储*下的文件夹*插件*，在项目视图中，选择以下插件*仅*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![取消选中任何平台](images/AzureLabs-Lab5-46.png)

5.  与*这些特定插件*选择，**取消选中** *Any 平台*并**取消选中** *WSAPlayer*然后单击**应用**。

    ![应用平台 dll](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > 我们将会使这些特定的插件，只使用在 Unity 编辑器中。 这是因为存在不同版本的项目会导出从 Unity 后，将使用 WSA 文件夹中的同一个插件。

6.  在中*存储*插件文件夹中，只选择：

    -   Microsoft.Data.Services.Client

        ![组不处理的 dll](images/AzureLabs-Lab5-48.png)

7.  检查**不进程**框下*平台设置*然后单击**应用**。

    ![应用不会进行处理](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > 我们会将标记此插件"不处理"因为 Unity 程序集 patcher 有处理此插件的难度。 即使未处理，该插件仍将起作用。

## <a name="chapter-7---create-the-azureservices-class"></a>章 7-创建 azure 服务类

要创建的第一个类是*azure 服务*类。

*Azure 服务*类将负责：

-   将 Azure 帐户凭据的存储。

-   调用 Azure 函数应用。

-   上传和下载数据文件在 Azure 云存储中。

若要创建此类：

1.  在中右击*资产*文件夹中，在项目面板中，位于**创建** > **文件夹**。 将文件夹命名为**脚本**。

    ![创建新文件夹](images/AzureLabs-Lab5-50.png)

    ![将文件夹的脚本](images/AzureLabs-Lab5-51.png)

2.  双击刚创建的文件夹，以将其打开。

3.  在文件夹中，右键单击**创建** >   **C#脚本**。 调用脚本*azure 服务*。

4.  双击新*azure 服务*类以打开其与*Visual Studio*。

5.  将以下命名空间添加到顶部*azure 服务*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  添加以下检查器字段内*azure 服务*类：

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  然后添加以下成员变量内的*azure 服务*类：

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > 请确保您替换*终结点*并*连接字符串*在 Azure 门户中找到的值与 Azure 存储的值

8.  为代码*Awake()* 并*start （)* 方法现在需要添加。 类初始化时，将会调用这些方法：

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > 我们的代码中将填充*CallAzureFunctionForNextShape()* 中[未来一章](#chapter-10---completing-the-azureservices-class)。

9.  删除*update （)* 方法因为此类不会使用它。

10. 在 Visual Studio 中，保存所做的更改，然后返回到 Unity。

11. 单击并拖动*azure 服务*从脚本文件夹中的 Main Camera 对象的类*层次结构面板*。

12. 选择主相机，然后抓取**AzureStatusText**从下方的子对象**GazeButton**对象，并将其内放置**AzureStatusText**引用目标字段中*Inspector*，以提供对引用*azure 服务*脚本。

    ![分配 azure 状态文本引用目标](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>章 8-创建 ShapeFactory 类

若要创建，下一个脚本是*ShapeFactory*类。 此类角色是请求时，创建新形状，并保留历史记录中创建形状*形状历史记录列表*。 每次创建形状时，*形状历史记录列表*中更新*AzureService*类，并随后将存储在你*Azure 存储*。 在应用程序启动时，如果存储的文件中找到你*Azure 存储*，则*形状历史记录列表*检索并将其重播，具有**三维文字**对象提供生成的形状是否从存储，或新。

若要创建此类：

1.  转到**脚本**之前创建的文件夹。

2.  在文件夹中，右键单击**创建** >   **C#脚本**。 调用脚本*ShapeFactory*。

3.  双击新*ShapeFactory*脚本以将其与打开*Visual Studio*。

4.  请确保*ShapeFactory*类包括以下命名空间：

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  添加到如下所示的变量*ShapeFactory*类，并替换*start （)* 并*Awake()* 与下面的函数：

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  *CreateShape()* 方法将生成基于所提供的基元形状*整数*参数。 用于指定当前创建的形状是从存储，或新的布尔参数。 将以下代码中的您*ShapeFactory*类，以前的方法如下：

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  请确保在返回到 Unity 之前的 Visual Studio 中保存所做的更改。

8.  返回在 Unity 编辑器中，单击并拖动*ShapeFactory*类派生**脚本**文件夹**Main Camera**对象中*层次结构面板*.

9. 您会发现与所选 Main Camera *ShapeFactory*脚本组件缺少*衍生点*引用。 若要修复它，请拖动**ShapeSpawnPoint**对象从*层次结构面板*到**衍生点**引用目标。

    ![组形状工厂引用目标](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>章 9-创建的视线移动类

若要创建所需的最后一个脚本是*注视*类。

此类负责创建**Raycast**将从 Main Camera，以检测用户正在通过哪个对象向前投影的。 在这种情况下，Raycast 将需要确定如果用户寻求**GazeButton**对象在场景中，并触发一个行为。

若要创建此类：

1.  转到**脚本**之前创建的文件夹。

2.  在项目面板中，右键单击**创建** >   **C#脚本**。 调用脚本*注视*。

3.  双击新*注视*脚本以将其与打开*Visual Studio。*

4.  请确保以下命名空间是包括在脚本顶部：

    ```csharp
        using UnityEngine;
    ```

5.  然后添加以下变量内的*注视*类：

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> 其中一些变量将能够在中进行编辑*编辑器*。

6.  为代码*Awake()* 并*start （)* 方法现在需要添加。

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  添加以下代码，将创建游标对象处开始，连同*update （)* 方法，将运行 Raycast 方法，以及在其中切换 GazeEnabled 布尔值：

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. 接下来，添加*UpdateRaycast()* 方法，它将项目 Raycast 并检测命中的目标。

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. 最后，将添加*ResetFocusedObject()* 方法，它将切换 GazeButton 对象当前颜色，指示它是否创建一个新的形状。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  返回到 Unity 之前，Visual Studio 中保存所做的更改。

11.  单击并拖动*注视*到脚本文件夹中的类**Main Camera**对象中*层次结构面板*。

## <a name="chapter-10---completing-the-azureservices-class"></a>第 10 章-完成 azure 服务类

与其他脚本中的位置，现在就可以*完整* *azure 服务*类。 将通过实现此目的：

1.  添加名为的新方法*CreateCloudIdentityAsync()* ，若要设置用于与 Azure 进行通信所需的身份验证变量。

    > 此方法还将检查存在包含形状列表的以前存储文件。
    >
    > **如果找到该文件**，它将禁用的用户*注视*，并触发形状创建过程中，根据形状的模式，如存储在**Azure 存储文件**。 用户可以看到这一点，作为**文本 Mesh**将提供显示存储或 New，具体取决于形状原点。
    >
    > **如果未找到文件**，它可实现*注视*，使用户可以在查看时创建的形状**GazeButton**场景中的对象。

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  下一步的代码片段是从*start （)* 方法; 其中一个调用将对*CreateCloudIdentityAsync()* 方法。 可随意复制您的当前*start （)* 方法中，使用如下：

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  方法的代码中填写*CallAzureFunctionForNextShape()* 。 您将使用之前创建*Azure Function App*来请求一个形状的索引。 此方法后收到新形状时，会将发送到形状*ShapeFactory*类，以在场景中创建新的形状。 使用下面的代码来完成的正文*CallAzureFunctionForNextShape()* 。

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  添加一个方法来创建字符串，通过串联整数存储在形状历史记录列表中，并保存在你*Azure 存储文件*。

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  添加一个方法以便检索存储在文件中的文本你*Azure 存储文件*并*反序列化*到列表。

6.  完成此过程后，该方法将重新启用的视线移动，以便用户可以向场景添加更多的形状。

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  返回到 Unity 之前，Visual Studio 中保存所做的更改。

## <a name="chapter-11---build-the-uwp-solution"></a>第 11 章 — 生成 UWP 解决方案

若要开始生成过程：

1.  转到**文件** > **生成设置**。

    ![生成应用](images/AzureLabs-Lab5-54.png)

2.  单击“生成”  。 将启动 unity*文件资源管理器*窗口中，需要创建，然后选择要生成该应用程序的文件夹。 现在，创建该文件夹并将其命名*应用*。 然后使用*应用程序*文件夹选择，按**选择文件夹**。

3.  Unity 将开始构建您的项目*应用*文件夹。

4.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开*文件资源管理器*窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。

## <a name="chapter-12---deploying-your-application"></a>第 12 章 — 部署应用程序

若要部署你的应用程序：

1.  导航到*应用程序*文件夹中创建[最后一章](#chapter-11---build-the-uwp-solution)。 您将查看你的应用名称，使用.sln 扩展，则您应该双击了文件，因此，若要中打开它*Visual Studio*。

2.  在中**解决方案平台**，选择**x86，本地计算机**。

3.  在中**解决方案配置**选择**调试**。

    > 对于 Microsoft HoloLens，您可能会发现它更轻松地将其设置为*远程计算机*，因此您不已接入到你的计算机。 不过，需要还执行以下操作：
    > - 知道**IP 地址**的你 HoloLens，在中找到**设置** > **网络和 Internet**  >  **Wi-fi** > **高级选项**; IPv4 是应使用的地址。 
    > - 请确保**开发人员模式**是**上**; 中找到**设置** > **更新和安全** >  **面向开发人员**。

    ![部署解决方案](images/AzureLabs-Lab5-55.png)

4.  转到**构建**菜单，并单击**部署解决方案**旁加载到计算机中，应用程序。

5.  你的应用现在应已安装的应用，准备好进行启动和测试的列表中显示 ！

## <a name="your-finished-azure-functions-and-storage-application"></a>你已完成的 Azure 函数和存储应用程序

祝贺你，构建利用 Azure Functions 和 Azure 存储服务的混合的现实应用。 您的应用程序将能够利用存储的数据，并提供一个操作基于该数据。

![最终产品的最终](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

创建第二个生成点和记录的生成的点从创建了一个对象。 当数据文件加载时，重播正在从最初创建它们的位置生成的形状。

### <a name="exercise-2"></a>练习 2

创建应用程序中，而不是无需重新打开它每次重新启动的方法。 **正在加载场景**是启动操作的好地方。 执行这些操作之后, 创建一种方法来清除中的存储的列表*Azure 存储*，以便它可以轻松地重置从您的应用程序。 
