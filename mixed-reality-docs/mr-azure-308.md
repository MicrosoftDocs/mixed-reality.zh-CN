---
title: MR 以及 Azure 308 的跨设备通知
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 通知中心、 Azure Functions 和 Azure 存储和表。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 通知、 函数、 表、 通知中心，沉浸式、 hololens、 vr
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694604"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR 和 Azure 308:跨设备通知

![最终产品-启动](images/AzureLabs-Lab8-00.png)

在本课程中，您将学习如何将通知中心功能添加到使用 Azure 通知中心、 Azure 表和 Azure Functions 的混合的现实应用程序。

**Azure 通知中心**是 Microsoft 服务，这样，开发人员将有针对性的个性化推送通知发送到任何平台上，所有这些都在云中。 这可以有效地允许开发人员与最终用户进行通信或甚至各种应用程序，具体取决于方案之间进行通信。 有关详细信息，请访问**Azure 通知中心**[页面](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)。

**Azure Functions**是一个 Microsoft 服务，它允许开发人员运行小段代码，函数，在 Azure 中。 这使您能够将工作委托给云，而不是本地应用程序，它可以有许多好处。 **Azure Functions**支持多种开发语言，包括 C\#，F\#，Node.js、 Java 和 PHP。 有关详细信息，请访问**Azure Functions** [页面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

**Azure 表**一个 Microsoft 云服务，它允许开发人员能够在云中存储结构化非 SQL 数据，使其可以轻松访问任意位置。 该服务实现了无架构设计，根据需要允许为表的演变，因此非常灵活。 有关详细信息，请访问**Azure 表**[页](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

已完成本课程，将具有混合的现实耳机沉浸式应用程序中和一个桌面 PC 应用程序，将能够执行以下操作：

1. 桌面 PC 应用程序将允许用户在 2D 空间 （X 和 Y） 中移动对象使用鼠标。

2. 移动 PC 应用程序内的对象将发送到云使用 JSON，这将以字符串的形式，其中包含的对象 ID，类型和转换 （X 和 Y 坐标） 的信息。 

3. 从通知中心服务 （这只是已通过台式计算机应用更新），混合的现实应用，具有到桌面应用程序相同的场景，将收到有关对象移动的通知。 

4. 收到通知，它将包含对象 ID、 类型和转换的信息，mixed 的 reality 应用将向其自身场景应用收到的信息。

在您的应用程序，它是取决于您关于如何将与您的设计集成结果。 本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。 它是作业以使用此课程以增强混合的现实应用程序中获取的知识。 此过程是不直接涉及任何其他混合现实实验室的自包含的教程。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 308:跨设备通知</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。 按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。 使用 HoloLens，您可能注意到某些 echo 语音捕获过程。

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
- 为 Azure 设置和访问通知中心的 Internet 访问

## <a name="before-you-start"></a>开始之前

- 若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。
- 您必须是 Microsoft 开发人员门户和你的应用程序注册门户的所有者，否则不会有权访问的应用程序中[第 2 章](#chapter-2---retrieve-your-new-apps-credentials)。

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>第 1 章-Microsoft 开发人员门户中创建应用程序

若要使用**Azure 通知中心**服务，你将需要创建应用程序在 Microsoft 开发人员门户中，因为你的应用程序将需要进行注册，以便它可以发送和接收通知。

1.  登录到[Microsoft 开发人员门户](https://developer.microsoft.com/dashboard)。

    > 你将需要登录到你的 Microsoft 帐户。

2.  从仪表板，单击**创建新的应用**。

    ![创建应用](images/AzureLabs-Lab8-01.png)

3.  将出现一个弹出窗口，其中需要以保留新应用的名称。 在文本框中，插入适当的名称;如果选择的名称不可用，刻度线将显示右侧的文本框中。 插入的可用名称后，单击**保留产品名称**弹出框的左下角的按钮。

    ![反向名称](images/AzureLabs-Lab8-02.png)

4.  现在创建的应用程序，已准备好移动到下一章。

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>第 2-章中检索新的应用凭据

登录到应用程序注册门户，其中新应用程序将列出和检索的凭据将用于记录的安装程序**通知中心服务**内**Azure 门户**。

1.  导航到[应用程序注册门户](http://apps.dev.microsoft.com)。

    ![应用程序注册门户](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > 需要使用你的 Microsoft 帐户登录。  
    > 这**必须**是在以前使用 Microsoft 帐户[章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)，与 Windows 应用商店开发人员门户。

2.  您会发现您的应用程序下**我的应用程序**部分。 找到它后, 单击它，将转到新页面具有的应用名加上**注册**。

    ![新注册的应用](images/AzureLabs-Lab8-04.png)

3.  向下注册页面以查找滚动你**应用程序机密**部分并**程序包 SID**为你的应用。 复制用于设置**Azure 通知中心服务**中下一章。

    ![应用程序机密](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>章节 3-安装 Azure 门户： 创建通知中心服务

使用你的应用的凭据检索到，你将需要转到 Azure 门户中，将在其中创建 Azure 通知中心服务。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE] 
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**新建**在左上角，并搜索**通知中心**，然后单击***Enter***。

    ![通知中心的搜索](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > 单词***新建***可能已替换**创建资源**，较新的门户网站中。

3.  该新页面将提供的说明*通知中心*服务。 在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。

    ![创建通知中心实例](images/AzureLabs-Lab8-07.png)

4.  一旦你单击***创建***:

    1.  插入此服务实例所需的名称。

    2.  提供**命名空间**其中你将能够将与此应用相关联。

    3.  选择**位置。**

    4.  选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。

        > 如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。 

    5.  选择相应**订阅**。

    6.  您还需要确认你已了解的条款和条件应用于此服务。

    7. 选择“创建”  。

        ![服务详细信息中填充](images/AzureLabs-Lab8-08.png)

5.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。

6.  创建服务实例后，在门户中将显示一条通知。

    ![通知](images/AzureLabs-Lab8-09.png)

7.  单击**转到资源**通知探索新的服务实例中的按钮。 你将会转到新**通知中心**服务实例。

    ![转到资源](images/AzureLabs-Lab8-10.png)
    
8.  从概述页中，中途页上，单击**Windows (WNS)。** 在右侧面板将更改为显示两个文本字段，这需要你**程序包 SID**并**安全密钥**，从以前设置的应用。

    ![新创建的中心服务](images/AzureLabs-Lab8-11.png)

9. 一旦到了正确的字段复制的详细信息，请单击**保存**，并已成功更新通知中心时，你将收到通知。

    ![复制安全的详细信息](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>章 4-设置 Azure 门户： 创建表服务

创建通知中心服务实例后，导航回到 Azure 门户中，您将创建的存储资源创建 Azure 表服务。

1.  如果尚未登录，登录到[Azure 门户](https://portal.azure.com)。

2.  登录后，单击**新建**在左上角，并搜索**存储帐户**，然后单击**Enter**。

    > [!NOTE] 
    > 单词***新建***可能已替换**创建资源**，较新的门户网站中。

3.  选择**存储帐户-blob、 文件、 表、 队列**从列表中。

    ![搜索存储帐户](images/AzureLabs-Lab8-13.png)

4.  该新页面将提供的说明**存储帐户**服务。 在左下角此提示符下，选择**创建**按钮，创建此服务的实例。

    ![创建存储实例](images/AzureLabs-Lab8-14.png)

5.  一旦你单击**创建**，将显示一个面板：

    1. 插入所需**名称**（必须全部小写） 此服务实例。

    2. 有关**部署模型**，单击**资源管理器**。

    3.  有关**帐户类型**，使用下拉列表菜单，选择**存储 (常规用途 v1)** 。

    4. 选择相应**位置**。
    
    5.  有关**复制**下拉列表菜单中，选择**读取-访问-异地冗余存储 (RA-GRS)** 。

    6.  有关**性能**，单击**标准**。

    7.  内**需要安全传输**部分中，选择**禁用**。

    8.  从**订阅**下拉菜单中，选择相应的订阅。

    9.  选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。

        > 如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 将保留**虚拟网络**作为**禁用**如果这是为你的选项。

    11. 单击“创建”  。

        ![填写存储详细信息](images/AzureLabs-Lab8-15.png)

6.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。

7.  创建服务实例后，在门户中将显示一条通知。 单击通知以了解新的服务实例。

    ![新的存储通知](images/AzureLabs-Lab8-16.png)

8.  单击**转到资源**通知探索新的服务实例中的按钮。 你将转到新的存储服务实例概述页。

    ![转到资源](images/AzureLabs-Lab8-17.PNG)

9. 从概述页上，到右侧，单击**表**。
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. 在右侧面板将更改为显示**表服务**其中所需添加一个新表的信息。 执行此操作通过单击 **+** **表**左上角的按钮。

    ![打开表](images/AzureLabs-Lab8-19.png)

11. 将显示一个新页面，其中你需要输入**表名称**。 这是将用于指代应用程序中后面的章节中的数据的名称。 插入适当的名称，然后单击**确定**。

    ![创建新表](images/AzureLabs-Lab8-20.png)    

12. 一旦创建新表后，你将能够看到它在**表服务**页 （底部）。

    ![创建新表](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>第 5 章-完成 Visual Studio 中的 Azure 表

现在，你**表服务**存储帐户已被安装程序，即可将数据添加到它，将用于存储和检索信息。 编辑你的表，可通过完成**Visual Studio**。

1.  打开**Visual Studio**。

2.  从菜单中，单击**视图** > **云资源管理器**。

    ![打开 cloud explorer](images/AzureLabs-Lab8-22.png)

3.  **云资源管理器**以停靠项 （如加载可能需要时间，则请耐心等待，） 将打开。

    > [!NOTE] 
    > 如果用于创建订阅你*存储帐户*不可见，请确保您具有： 
    > - 登录到 Azure 门户使用的同一个帐户。
    > - （您可能需要从你的帐户设置应用筛选器） 在帐户管理页上选择你的订阅：  
    >
    >   ![查找订阅](images/AzureLabs-Lab8-22-5.png)

4.  将显示在 Azure 云服务。 查找**存储帐户**，然后单击箭头以展开你的帐户的左侧。

    ![打开存储帐户](images/AzureLabs-Lab8-23.png)

5.  展开后，新创建**存储帐户**应可用。 单击你的存储，左侧的箭头，然后后，已展开，找到**表**，然后单击箭头旁边的以显示**表**在最后一章中创建。 双击您**表**。

    ![打开的场景对象表](images/AzureLabs-Lab8-24.png)

6.  将在 Visual Studio 窗口的中心中打开您的表。 单击与表图标 **+** （加上） 在其上。

    ![添加新表](images/AzureLabs-Lab8-25.png)

7.  你能够将出现一个窗口提示*添加实体*。 总的来说，每个都有多个属性，将创建三个实体。 您会注意*PartitionKey*并*RowKey*已提供了，因为需要使用这些表以查找你的数据。 

    ![分区键和行键](images/AzureLabs-Lab8-26.png)

8. 更新*值*的**PartitionKey**和**RowKey** ，如下所示 (请记住，若要执行此操作的每个行属性添加，但每次递增 RowKey):

    ![添加正确的值](images/AzureLabs-Lab8-26-5.png)

9.  单击**将属性添加**添加额外的数据行。 使匹配在第一个空表下表。

10. 单击**确定**完成之后。

    ![完成后单击确定](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > 确保您已更改**类型**的**X**， **Y**，以及**Z**，条目**Double**。 

11. 您会注意到您的表现在具有一行数据。 单击 **+** （+） 图标重新添加另一个实体。

    ![第一行](images/AzureLabs-Lab8-27-5.png)

12. 创建附加属性，并设置新的实体，以匹配下面所示的值。

    ![添加多维数据集](images/AzureLabs-Lab8-28.png)

13. 重复最后一个步骤以添加另一个实体。 将此实体的值设置为下面所示。

    ![添加圆柱图](images/AzureLabs-Lab8-29.png)

14. 您的表现在应类似于下面所示。

    ![完整的表](images/AzureLabs-Lab8-30.png)

15. 已完成这一章。 请务必保存。

## <a name="chapter-6---create-an-azure-function-app"></a>章 6-创建 Azure Function App

创建一个 Azure Function App，若要更新的桌面应用程序将调用**表**服务，并发送通过通知**通知中心**。

首先，需要创建一个文件，将允许您的 Azure 函数以加载所需的库。

1.  打开**记事本**（按 Windows 键和类型记事本）。

    ![打开记事本](images/AzureLabs-Lab8-31.png)

2.  使用记事本打开，将插入到其中的以下 JSON 结构。 完成后，将其保存为您的桌面上**project.json**。 非常重要的是正确的命名： 确保与其**不具有.txt**文件扩展名。 此文件定义的库将使用你的函数，如果你已使用 NuGet 将很熟悉。

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  登录到[Azure 门户](https://portal.azure.com)。

4.  你登录后，单击**新建**在左上角，并搜索**Function App**，按**Enter**。

    ![搜索函数应用](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > 单词**新建**可能已替换**创建资源**，较新的门户网站中。

5.  该新页面将提供的说明**Function App**服务。 在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。

    ![function app 实例](images/AzureLabs-Lab8-33.png)

6.  一旦你单击**创建**，填写以下：

    1. 有关**应用名称**，插入此服务实例所需的名称。

    2. 选择**订阅**。

    3. 选择定价层适合你，如果这是首次创建**Function App 服务**，应可供你免费层。

    4. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。

        > 如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 有关**OS**，单击 Windows，因为这是预期的平台。

    6. 选择**托管计划**(使用本教程**消耗计划**。

    7. 选择**位置** **（上一步中选择与已生成的存储相同的位置）**

    8. 有关**存储**部分中，**必须选择在上一步中创建的存储服务**。

    9. 您不需要*Application Insights*在此应用中，所以请随意将其留**关闭**。

    10. 单击“创建”  。

        ![创建新的实例](images/AzureLabs-Lab8-34.png)

7.  一旦你单击**创建**必须要等待的时间来创建服务，这可能需要一分钟的时间。

8.  创建服务实例后，在门户中将显示一条通知。

    ![新的通知](images/AzureLabs-Lab8-35.png)

9.  单击通知以了解新的服务实例。

10. 单击**转到资源**通知探索新的服务实例中的按钮。 

    ![转到资源](images/AzureLabs-Lab8-36.png)

11. 单击 **+** （加号） 旁边的图标*函数*到*新建*。

    ![添加新函数](images/AzureLabs-Lab8-37.png)

12. 在中间面板**函数**创建窗口将显示。 忽略在面板的上半部分中的信息，并单击**自定义函数**，位于底部 （在蓝色区域，如下所示）。

    ![自定义函数](images/AzureLabs-Lab8-38.png)

13. 在窗口中的新页面将显示各种函数类型。 向下滚动以查看紫色类型，并单击**HTTP PUT**元素。

    ![http put 链接](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > 可能需要进一步向下滚动一页 （和此映像可能不尽相同，如果 Azure 门户更新发生），但是，要查找名为的元素*HTTP PUT*。

14. **HTTP PUT**窗口将显示，需要配置函数 （请参阅下面的图像）。

    1.  有关**语言中，** 使用下拉列表菜单中，选择 C\#。

    2.  有关**名称，** 输入适当的名称。

    3.  在中**身份验证级别**下拉列表菜单中，选择**函数**。

    4.  有关**表名称**部分中，您需要使用的确切名称，用于创建你**表**服务之前 （包括相同的字母大小写）。

    5.  内**存储帐户连接**部分中，使用下拉列表菜单，并从此处选择你的存储帐户。 如果不存在，单击**新建**与节标题，以显示另一个面板，其中应列出你的存储帐户的超链接。

        ![新的存储](images/AzureLabs-Lab8-40.png)

15. 单击**创建**，您将收到通知已成功更新你的设置。

    ![创建函数](images/AzureLabs-Lab8-41.png)

16. 单击后**创建**，你将重定向到在函数编辑器。

    ![更新函数代码](images/AzureLabs-Lab8-42.png)

17. （替换函数中的代码） 在函数编辑器中插入以下代码：

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > 使用包含的库，该函数收到的名称和位置被移动的对象的 Unity 场景中 (作为C#对象，调用**UnityGameObject**)。 然后使用此对象来更新对象参数中创建的表。 接着，该函数将为你创建的通知中心服务，这将告知所有已订阅的应用程序调用。

18. 使用的代码中的位置，单击**保存**。

19. 接下来，单击 **\<** （箭头） 图标，在页面的右侧。

    ![打开上传面板](images/AzureLabs-Lab8-43.png)

20. 一个面板，将从右侧滑中。 在该面板中，单击**上传**，并且将显示文件浏览器。

21. 导航到，然后单击， **project.json**中创建的文件**记事本**以前，然后单击**打开**按钮。 此文件定义函数将使用的库。

    ![上传 json](images/AzureLabs-Lab8-44.png)

22. 当完成上传文件时，它会在右侧面板中显示。 单击它即可打开它内**函数**编辑器。 它必须看起来**完全**（下面步骤 23） 的下一步映像相同。

23. 然后，在左侧面板下方**函数**，单击**集成**链接。

    ![将集成函数](images/AzureLabs-Lab8-45.png)

24. 在下一页上，在右上角，单击**高级的编辑器**（如下所示）。

    ![打开高级编辑器](images/AzureLabs-Lab8-46.png)

25. 一个**function.json**文件将在中心窗格中，需要替换为以下代码片段中打开。 这将定义要生成的函数和参数传递到函数。

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. 你的编辑器现在应类似于下图中所示：

    ![返回到标准编辑器](images/AzureLabs-Lab8-47.png)

27. 您可能注意到你刚插入的输入的参数可能与你表和存储的详细信息不匹配，因此将需要使用你的信息进行更新。 **不这样做此处**，如接下来介绍了。 只需单击**标准编辑器**链接，可在页上，若要返回的右上角。

28. 回到**标准编辑器**，单击**Azure 表存储 （表）** 下**输入**。 
    
    ![表输入](images/AzureLabs-Lab8-47-5.png)

29. 确保与以下匹配**你**信息，因为它们可能是不同 （不存在以下步骤的下面的图像）：

    1.  **表名**： 你的 Azure 存储，表服务中创建的表的名称。

    2.  **存储帐户连接：** 单击**新**、 将显示此旁的下拉列表菜单，和一个面板将显示在窗口右侧。

        ![新的存储](images/AzureLabs-Lab8-48.png)

        1.  选择你**存储帐户**，到主机之前创建**函数应用。**

        2. 您会注意**存储帐户**创建连接值。

        3. 请务必按**保存**完成后。

    3.  **输入**页现在应与下面显示**您**信息。

        ![输入完成](images/AzureLabs-Lab8-49.png)

30. 接下来，单击**Azure 通知中心 （通知）** -下**输出**。 请确保以下与匹配**你**信息，因为它们可能是不同 （不存在以下步骤的下面的图像）：

    1.  **通知中心名称**： 这是名称你**通知中心**之前创建的服务实例。

    2.  **通知中心命名空间连接**： 单击**新**，该下拉列表菜单一起出现。

        ![检查输出](images/AzureLabs-Lab8-50.png)

    3. **连接**弹出窗口将显示 （请参阅下图所示），您需要选择**Namespace**的**通知中心**，以前设置的。

    4. 选择你**通知中心**中间的下拉列表菜单中的名称。

    5.  设置**策略**下拉列表菜单**DefaultFullSharedAccessSignature**。

    6. 单击**选择**按钮可返回。

        ![输出更新](images/AzureLabs-Lab8-51.png)

31.  **输出**页现在应与下面，但与**您**信息改为。 请务必按**保存**。

> [!WARNING]
> *不要直接编辑的通知中心名称*(这应完成使用**高级编辑器**、 提供正确地按照前面的步骤。

![完整的输出](images/AzureLabs-Lab8-50.png)

32. 此时，应测试函数，以确保它正在运行。 要实现此目的，请执行以下操作： 

    1. 一次导航到函数页：

        ![完整的输出](images/AzureLabs-Lab8-50-1.png)

    2. 返回在函数页上，单击**测试**页面上，以打开最右侧的选项卡*测试*边栏选项卡：

        ![完整的输出](images/AzureLabs-Lab8-50-2.png)

    3. 内**请求正文**文本框的边栏选项卡上，粘贴以下代码：

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. 测试代码，然后单击**运行**按钮，位于靠下右对齐，并测试将会运行。 测试的输出日志显示在控制台区域中，下面的函数代码。

        ![完整的输出](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > 如果上述测试失败，则需要仔细检查确实如此，遵循上述步骤尤其是中的设置**集成面板**。 

## <a name="chapter-7---set-up-desktop-unity-project"></a>第 7 章 — 设置桌面 Unity 项目

> [!IMPORTANT]
> 桌面应用程序，现在要创建，**将不会**在 Unity 编辑器中工作。 它需要外部编辑器，按照使用 Visual Studio 的应用程序 （或已部署的应用程序） 的生成运行。 

以下是一组典型使用 Unity 进行开发和混合的现实，并在这种情况下，是合适的模板的其他项目。

设置和测试您的混合的现实沉浸式头戴式。

> [!NOTE] 
> 你将**不**此课程需要运动控制器。 如果你需要支持沉浸式头戴式设置，请遵循此[k 了解如何设置 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  打开**Unity**然后单击**新建**。

    ![新的 unity 项目](images/AzureLabs-Lab8-52.png)

2.  需要提供 Unity 项目名称，插入**UnityDesktopNotifHub**。 请确保项目类型设置为**3D**。 设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![创建项目](images/AzureLabs-Lab8-53.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑** > **首选项**，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![组外部的 VS 工具](images/AzureLabs-Lab8-54.png)

4.  接下来，请转到**文件** > **生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。

    ![交换机平台](images/AzureLabs-Lab8-55.png)

5.  在仍处于**文件** > **生成设置**，请确保：

    1.  **设备为目标**设置为**任一设备**

        > 此应用程序将为您的桌面，因此必须**任一设备**

    2.  **生成的类型**设置为**D3D**

    3.  **SDK**设置为**最新安装**

    4.  **Visual Studio 版本**设置为**最新安装**

    5.  **生成并运行**设置为**本地计算机**

    6.  在此，仪表是值得保存场景，并将其添加到生成。

        1. 选择执行此**添加打开场景**。 保存窗口将显示。

            ![添加打开场景](images/AzureLabs-Lab8-56.png)

        2. 创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![新的场景文件夹](images/AzureLabs-Lab8-57.png)

        3. 打开新建**场景**文件夹，然后在**文件名：** 文本字段中，键入**NH\_桌面\_场景**，然后按**保存**。

            ![新 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  中的剩余设置，**生成设置**，应暂时保留为默认值。

6.  在同一窗口中单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。

7.  在此面板中，需要验证几个设置：

    1.  在中**其他设置**选项卡：

        1.  **脚本运行时版本**应为**实验 （.NET 4.6 等效）**

        2. **脚本编写后端**应为 **.NET**

        3. **API 兼容性级别**应为 **.NET 4.6**

            ![4.6 的.net 版本](images/AzureLabs-Lab8-59.png)

    2.  内**发布设置**选项卡上，在**功能**，检查：

        - **InternetClient**

            ![刻度线 internet 客户端](images/AzureLabs-Lab8-60.png)

8.  回到**生成设置** *Unity C\#项目*不再灰显; 选中它旁边的复选框。

9.  关闭**生成设置**窗口。

10. 保存您的场景和项目**文件** > **保存场景文件** > **保存项目**。

    > [!IMPORTANT]
    > 如果你想要跳过*Unity 设置*组件为此项目 （桌面应用），并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。  你将需要添加脚本组件。

## <a name="chapter-8---importing-the-dlls-in-unity"></a>第 8 章-导入 Unity 中的 Dll

您将使用 Azure 存储于 Unity （其本身使用.Net 的 Azure SDK）。 有关详细信息，请遵循此[有关 Unity 的 Azure 存储链接](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。

这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。 这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。

若要导入您自己的项目的 SDK，请确保已下载最新[ **.unitypackage** ](https://aka.ms/azstorage-unitysdk)从 GitHub。 然后，执行以下操作：

1.  添加 **.unitypackage**到使用 Unity**资产\>导入包\>自定义包**菜单选项。

2.  在中**导入 Unity 程序包**框，弹出，你可以选择下的所有内容 * **插件* \> * 存储 * * *。  取消选中其他任何内容，因为它不需要此课程。

    ![导入包](images/AzureLabs-Lab8-61.png)

3.  单击***导入***按钮将项添加到你的项目。

4.  转到**存储**下的文件夹**插件**项目中查看并选择以下插件*仅*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![取消选中任何平台](images/AzureLabs-Lab8-62.png)

5.  与*这些特定插件*选择，**取消选中** **Any 平台**并**取消选中** **WSAPlayer**然后单击**应用**。

    ![应用平台 dll](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > 我们将会使这些特定的插件，只使用在 Unity 编辑器中。 这是因为存在不同版本的项目会导出从 Unity 后，将使用 WSA 文件夹中的同一个插件。

6.  在中**存储**插件文件夹中，只选择：

    -   Microsoft.Data.Services.Client

        ![组不处理的 dll](images/AzureLabs-Lab8-64.png)

7.  检查**不进程**框下**平台设置**然后单击***应用***。

    ![应用不会进行处理](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > 我们会将标记此插件"不处理"，因为 Unity 程序集 patcher 有处理此插件的难度。 即使未处理，该插件仍将起作用。

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>章 9-桌面 Unity 项目中创建 TableToScene 类

现在需要创建包含要运行此应用程序的代码的脚本。

您需要创建的第一个脚本是**TableToScene**，负责：

-   读取 Azure 表中的实体。
-   使用表数据，确定哪些对象来生成，以及在哪个位置。

若要创建所需的第二个脚本是**CloudScene**，负责：

-   正在注册左键单击事件，以允许用户拖动对象周围场景。
-   序列化对象数据从此 Unity 场景中，并将其发送到 Azure Function App。

若要创建此类：

1.  在中右击**资产**文件夹中项目面板中，位于**创建** > **文件夹**。 将文件夹命名为**脚本**。

    ![创建脚本的文件夹](images/AzureLabs-Lab8-66.png)

    ![创建脚本文件夹 2](images/AzureLabs-Lab8-67.png)

2.  双击刚创建的文件夹，以将其打开。

3.  内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。 脚本命名为**TableToScene**。

    ![新的 c# 脚本](images/AzureLabs-Lab8-68.png)
    ![TableToScene 重命名](images/AzureLabs-Lab8-69.png)

4.  双击要在 Visual Studio 2017 中打开它的脚本。

5.  添加以下命名空间：

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  在类中，插入以下变量：

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > Substitute **accountName**值与你的 Azure 存储服务名称和**accountKey**值与在 Azure 门户 （请参阅下图） 中的 Azure 存储服务中找到的密钥值。 
    >
    > ![提取帐户密钥](images/AzureLabs-Lab8-70.png)

7.  现在，添加**start （)** 并**Awake()** 初始化类的方法。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  内**TableToScene**类中，添加将从 Azure 表中检索值并使用它们来生成场景中的相应基元的方法。

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  外侧**TableToScene**类，您需要定义应用程序用于序列化和反序列化的类**表实体**。

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. 请确保您**保存**之前追溯到 Unity 编辑器中。

11. 单击**Main Camera**从**层次结构**面板中，以便其属性将显示在**Inspector**。

12. 与**脚本**文件夹中打开，选择的脚本**TableToScene 文件**并将其拖动到**Main Camera**。 结果应如下所示：

    ![将脚本添加到主照相机](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>章 10-在桌面 Unity 项目中创建 CloudScene 类

若要创建所需的第二个脚本是**CloudScene**，负责：

-   正在注册左键单击事件，以允许用户拖动对象周围场景。

-   序列化对象数据从此 Unity 场景中，并将其发送到 Azure Function App。

若要创建第二个脚本：

1.  内右击**脚本**文件夹中，单击**创建**， **C\#脚本**。 脚本命名为**CloudScene**
    
    ![新的 c# 脚本](images/AzureLabs-Lab8-72.png)
    ![重命名 CloudScene](images/AzureLabs-Lab8-73.png)

2.  添加以下命名空间：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  插入以下变量：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Substitute **azureFunctionEndpoint**值与你在服务中找到 Azure 函数应用，在 Azure 门户中，如下图中所示的 Azure 函数应用 URL:

    ![获取函数 URL](images/AzureLabs-Lab8-74.png)

5.  现在，添加**start （)** 并**Awake()** 初始化类的方法。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  内**update （)** 方法中，添加以下代码，它会检测到鼠标输入并拖动，又将场景中移动 Gameobject。 如果用户具有拖动并删除一个对象，它将向方法传递的名称和对象的坐标**UpdateCloudScene()** ，这将调用 Azure 函数应用服务，这将更新 Azure 表和触发器通知。

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  现在，添加**UpdateCloudScene()** 方法，如下所示：

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  保存代码，并返回到 Unity

9.  拖动**CloudScene**拖动到脚本**Main Camera**。 

    1. 单击**Main Camera**从**层次结构**面板中，以便其属性将显示在**Inspector**。 

    2. 与**脚本**文件夹中，打开，选择**CloudScene**脚本并将其拖动到**Main Camera**。 结果应如下所示：

        > ![将云脚本拖动到主照相机上](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>第 11 章 — 生成桌面到 UWP 项目

此项目的 Unity 部分所需的所有内容现在已完成。

1.  导航到**生成设置**(**文件** > **生成设置**)。

2.  从**生成设置**窗口中，单击**生成**。

    ![生成项目](images/AzureLabs-Lab8-76.png)

3.  一个**文件资源管理器**将弹出窗口，提示您输入到生成的位置。 创建一个新文件夹 (通过单击**新文件夹**左上角)，并将其命名**生成**。

    ![生成新的文件夹](images/AzureLabs-Lab8-77.png)

    1.  打开新**生成**文件夹，并创建另一个文件夹 (使用**新的文件夹**一次)，并将其命名**NH\_桌面\_应用**。

        ![文件夹名称 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  与**NH\_桌面\_应用**选定。 单击**选择文件夹**。 该项目将花大约一分钟生成。

4.  以下生成，**文件资源管理器**将显示新项目的位置。 无需打开它，尽管根据需要创建其他 Unity 项目首先，在接下来的几个章节。


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>第 12 章 — 设置混合现实 Unity 项目

以下是一组典型使用混合现实中，进行开发，并在这种情况下，是合适的模板的其他项目。

1.  打开**Unity**然后单击**新建**。

    ![新的 unity 项目](images/AzureLabs-Lab8-79.png)

2.  现在将需要提供 Unity 项目的名称，插入**UnityMRNotifHub**。 请确保项目类型设置为**3D**。 设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑** > **首选项**，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![vs 设置外部编辑器](images/AzureLabs-Lab8-81.png)

4.  接下来，请转到**文件** > **生成设置**，并切换到平台**通用 Windows 平台**，通过单击**切换平台**按钮。

    ![切换到 UWP 的平台](images/AzureLabs-Lab8-82.png)

5.  转到**文件** > **生成设置**并确保选中：

    1.  **设备为目标**设置为**任一设备**

        > 对于 Microsoft HoloLens，设置**目标设备**到*HoloLens*。

    2.  **生成的类型**设置为**D3D**

    3.  **SDK**设置为**最新安装**

    4.  **Visual Studio 版本**设置为**最新安装**

    5.  **生成并运行**设置为**本地计算机**

    6.  在此，仪表是值得保存场景，并将其添加到生成。

        1. 选择执行此**添加打开场景**。 保存窗口将显示。

            ![添加打开场景](images/AzureLabs-Lab8-83.png)

        2. 创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![新的场景文件夹](images/AzureLabs-Lab8-84.png)

        3. 打开新建**场景**文件夹，然后在**文件名：** 文本字段中，键入**NH\_MR\_场景**，然后按**保存**。

            ![新的场景-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  中的剩余设置，**生成设置**，应暂时保留为默认值。

6.  在同一窗口中单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。    

    ![打开播放器设置](images/AzureLabs-Lab8-86.png)

7.  在此面板中，需要验证几个设置：

    1.  在中**其他设置**选项卡：

        1.  **脚本运行时版本**应**实验**（.NET 4.6 等效）
        2.  **脚本编写后端**应为 ***.NET***
        3.  **API 兼容性级别**应为 **.NET 4.6**

            ![api 兼容性](images/AzureLabs-Lab8-87.png)

    2.  中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加

        ![更新 xr 设置](images/AzureLabs-Lab8-88.png)        

    3.  内**发布设置**选项卡上，在**功能**，为了增加点乐趣：

        - **InternetClient**           

            ![刻度线 internet 客户端](images/AzureLabs-Lab8-89.png)

8.  回到**生成设置**， **UnityC#项目**不再灰显： 选中此旁边的复选框。

9.  完成这些更改，关闭生成设置窗口。

10. 保存您的场景和项目**文件** > **保存场景文件** > **保存项目**。

    > [!IMPORTANT]
    > 如果你想要跳过*Unity 设置*组件为此项目中 （混合现实应用），并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)。 你将需要添加脚本组件。

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>第 13 章 — 导入混合的现实 Unity 项目中的 Dll

您将使用 Azure 存储于 Unity 库 （它使用 azure.Net SDK）。 请遵循此[如何配合使用 Unity 和 Azure 存储链接](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。
这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。 这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。

若要导入您自己的项目的 SDK，请确保已下载最新[.unitypackage](https://aka.ms/azstorage-unitysdk)。 然后，执行以下操作：

1.  添加从以上下载到使用 Unity.unitypackage**资产** > **导入包** > **自定义包**菜单选项.

2.  在中**导入 Unity 程序包**框，弹出，你可以选择下的所有内容**插件** > **存储**。

    ![导入包](images/AzureLabs-Lab8-90.png)

3.  单击**导入**按钮将项添加到你的项目。

4.  转到**存储**下的文件夹**插件**项目中查看并选择以下插件*仅*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![选择插件](images/AzureLabs-Lab8-91.png)

5.  与*这些特定插件*选择，**取消选中** **Any 平台**并**取消选中** **WSAPlayer**然后单击**应用**。

    ![应用平台更改](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > 在标注这些特定的插件，只使用在 Unity 编辑器中。 这是因为存在不同版本的项目会导出从 Unity 后，将使用 WSA 文件夹中的同一个插件。

6.  在中**存储**插件文件夹中，只选择：

    -   Microsoft.Data.Services.Client

        ![选择数据服务客户端](images/AzureLabs-Lab8-93.png)

7.  检查**不进程**框下**平台设置**然后单击**应用**。

    ![不处理](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > 您要标记此插件"不处理"因为 Unity 程序集 patcher 有处理此插件的难度。 即使它不会得到处理，该插件仍将起作用。

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>第 14 章 — 在混合的现实 Unity 项目中创建 TableToScene 类

**TableToScene**类是等同于代码中所述[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。 在混合现实中所述的相同过程在 Unity 项目中创建相同的类[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。

完成本章节中，这两个后你**Unity 项目**将具有在 Main Camera 上设置了此类。

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>第 15 章 — 在混合现实 Unity 项目中创建 NotificationReceiver 类

若要创建所需的第二个脚本是**NotificationReceiver**，负责：

-   在初始化通知中心注册该应用。
-   侦听来自通知中心将通知。
-   反序列化中接收通知的对象数据。
-   在场景中，基于反序列化数据中移动 Gameobject。

若要创建**NotificationReceiver**脚本：

1.  内右击**脚本**文件夹中，单击**创建**， **C\#脚本**。 脚本命名为**NotificationReceiver**。

    ![创建新的 c# 脚本](images/AzureLabs-Lab8-95.png)
    ![其命名为 NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  双击该脚本以将其打开。

3.  添加以下命名空间：

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  插入以下变量：

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Substitute **hubName**值替换为通知中心服务名称，并**hubListenEndpoint**值与在 Azure 通知中心服务，的访问策略选项卡中找到的终结点值Azure 门户 （请参阅下图所示）。

    ![插入通知中心策略终结点](images/AzureLabs-Lab8-97.png)

6.  现在，添加**start （)** 并**Awake()** 初始化类的方法。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  添加**WaitForNotification**方法，以允许应用程序以从通知中心库接收通知，而无需与主线程冲突：

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  下面的方法， **InitNotificationAsync()** ，将与通知中心服务在初始化时注册该应用程序。 代码注释掉，如 Unity 将不能生成项目。 导入 Visual Studio 中的 Azure 消息传送 Nuget 包时，将删除注释。

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  下面的处理程序，**通道\_PushNotificationReceived()** ，每次收到通知时，将触发。 它将反序列化的通知，它已被移动桌面应用程序，Azure 表实体，然后将相应的 GameObject MR 场景中移动到相同的位置。 
    
    > [!IMPORTANT]
    > 代码注释掉，因为该代码引用 Azure 消息传送库，将生成使用 Nuget 包管理器中，Visual Studio 中的 Unity 项目后添加。 在这种情况下，Unity 项目将不能生成，除非它已被注释掉。请注意，是否应生成你的项目，然后希望返回到 Unity，你将需要**重新加上注释**该代码。

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. 请记住之前追溯到 Unity 编辑器中保存所做的更改。

11. 单击**Main Camera**从**层次结构**面板中，以便其属性将显示在**Inspector**。

12. 与**脚本**文件夹中，打开，选择**NotificationReceiver**脚本并将其拖动到**Main Camera**。 结果应如下所示：

    ![将通知收件人脚本拖到相机](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > 如果正在为 Microsoft HoloLens 开发，您需要更新**Main Camera**的*照相机*组件，以便：
    > - 清除标志：纯色
    > - 背景：黑色

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>第 16 章 — 生成混合的现实项目到 UWP

此章节都是相同，以生成前一项目的过程。 此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。

1.  导航到**生成设置**(**文件** > **生成设置**)。

2.  从**生成设置**菜单上，确保**UnityC#项目*** 勾选了 （这将允许您编辑后生成此项目中的脚本）。

3.  此操作完成后，单击**生成**。

    ![生成项目](images/AzureLabs-Lab8-99.png)

4.  一个**文件资源管理器**将弹出窗口，提示您输入到生成的位置。 创建一个新文件夹 (通过单击**新文件夹**左上角)，并将其命名**生成**。

    ![创建内部版本文件夹](images/AzureLabs-Lab8-100.png)

    1.  打开新**生成**文件夹，并创建另一个文件夹 (使用**新的文件夹**一次)，并将其命名**NH\_MR\_应用**。

        ![创建 NH_MR_Apps 文件夹](images/AzureLabs-Lab8-101.png)

    2.  与**NH\_MR\_应用**选定。 单击**选择文件夹**。 该项目将花大约一分钟生成。

5.  以下生成，**文件资源管理器**窗口将打开新项目的位置。



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>第 17 章 — 将 NuGet 包添加到 UnityMRNotifHub 解决方案

> [!WARNING] 
> 请记住，添加以下 NuGet 包后 (并取消注释在接下来的代码[章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class))，代码，在 Unity 项目中，重新打开时将显示错误。 如果你想要返回并继续编辑在 Unity 编辑器中，你将需要注释 errosome 代码，然后，取消注释再次更高版本，一旦您重新登录 Visual Studio。 

混合的现实生成完成后，导航到混合的现实项目，生成示例，请然后双击该文件夹，以使用 Visual Studio 2017 中打开你的解决方案中的解决方案 (.sln) 文件。
现在需要添加**WindowsAzure.Messaging.managed** NuGet 程序包; 这是一个库，用于从通知中心接收通知。

若要导入 NuGet 包：

1.  在中**解决方案资源管理器**，右键单击你的解决方案

2.  单击**管理 NuGet 包**。

    ![打开 nuget 管理器](images/AzureLabs-Lab8-102.png)

3.  选择***浏览***选项卡并搜索**WindowsAzure.Messaging.managed**。

    ![查找 windows azure 消息传送包](images/AzureLabs-Lab8-103.png)

4.  选择结果 （如下所示），并在右侧窗口中，选中的复选框旁边**项目**。 这会将一个对勾置于相应的复选框旁边**项目**，以及旁边的复选框**程序集 CSharp**并**UnityMRNotifHub**项目。

    ![选中所有项目](images/AzureLabs-Lab8-104.png)

5.  最初提供的版本**可能不会**与此项目兼容。 因此，请单击下拉列表菜单旁边**版本**，然后单击**版本 0.1.7.9**，然后单击**安装**。

6.  现在，已安装的 NuGet 包。 查找注释的代码中输入**NotificationReceiver**类，并删除注释...



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>第 18 章 — 编辑 UnityMRNotifHub 应用程序、 NotificationReceiver 类

添加了以下**NuGet 包**，你将需要*取消注释*中的代码的一些**NotificationReceiver**类。

这包括：

1. 在顶部命名空间：

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. 中的所有代码**InitNotificationsAsync()** 方法：

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> 上面的代码中有一条注释： 请确保不会意外*取消注释*的注释 （如代码将不会编译有 ！）。

3. 和最后**Channel_PushNotificationReceived**事件：

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

与这些取消注释中，确保您保存，然后，转到下一章。

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>第 19 章 — 将关联到应用商店应用程序的混合的现实项目

现在需要将相关联**混合现实**到应用商店应用中的实验室之初创建的项目。

1.  打开的解决方案。

2.  右键单击 UWP 应用项目在解决方案资源管理器窗格中，转到**应用商店**，和**将应用与应用商店关联...** .

    ![打开应用商店关联](images/AzureLabs-Lab8-105.png)

3.  将出现一个新窗口调用**将应用与 Windows 应用商店关联**。 单击“下一步”  。

    ![转到下一个屏幕](images/AzureLabs-Lab8-106.png)

4.  它会加载与已登录的帐户相关联的所有应用程序的运行。 如果您未登录到你的帐户，则可以**日志中**此页上。

5.  查找**应用商店应用程序名称**本教程开始时创建并选择它。 然后，单击“下一步”  。

    ![找到并选择你的存储区名称](images/AzureLabs-Lab8-107.png)

6.  单击**相关联**。

    ![将应用程序](images/AzureLabs-Lab8-108.png)

7.  您的应用程序现**关联**与应用商店应用程序。 这是必要的通知。

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>第 20 章 — 部署 UnityMRNotifHub 和 UnityDesktopNotifHub 应用程序

根据结果将包括同时运行的应用，桌面，您的计算机上的一个正在运行，另一个在您的沉浸式头戴式，本章可能会更方便中与两个用户。

沉浸式头戴式应用正在等待接收对场景 （的本地 Gameobject 的位置变化）、 更改和桌面应用程序将对其本地场景 （位置的更改），将共享到 MR 应用进行更改。 最好首先部署 MR 应用，以便接收方可以开始侦听跟桌面应用。

若要部署**UnityMRNotifHub**在本地计算机上的应用：

1.  打开解决方案文件的应用**UnityMRNotifHub**中的应用**Visual Studio 2017**。

2.  在中**解决方案平台**，选择**x86，本地计算机**。

3.  在中**解决方案配置**选择**调试**。

    ![设置项目配置](images/AzureLabs-Lab8-109.png)

4.  转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。

5.  你的应用现在应出现在已安装的应用，准备好启动列表中。

若要部署**UnityDesktopNotifHub**本地计算机上的应用：

1.  打开解决方案文件的应用**UnityDesktopNotifHub**中的应用**Visual Studio 2017**。

2.  在中**解决方案平台**，选择**x86，本地计算机**。

3.  在中**解决方案配置**选择**调试**。

    ![设置项目配置](images/AzureLabs-Lab8-110.png)

4.  转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。

5.  你的应用现在应出现在已安装的应用，准备好启动列表中。

6.  启动混合的现实应用程序，跟在桌面应用程序。

这两个运行的应用程序，桌面 （使用左鼠标按钮） 的场景中移动对象。 这些位置的更改将本地进行，序列化，并发送到函数应用服务。 Function App 服务然后将更新的表和通知中心。 具有收到的更新，通知中心将更新后的数据将直接发送到所有已注册应用程序 （在此情况下沉浸式头戴式应用），然后反序列化传入的数据，并将新的位置数据应用于本地对象，在场景中移动它们。


## <a name="your-finished-your-azure-notification-hubs-application"></a>你完成 Azure 通知中心应用程序
 
祝贺你，构建利用 Azure 通知中心服务，并允许应用程序之间的通信的混合的现实应用程序。
 
![最终产品的最终](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

您可以推断出如何更改的 GameObjects 颜色并将该通知发送到其他应用查看场景？

### <a name="exercise-2"></a>练习 2

您可以向 MR 应用添加的 GameObjects 移动和桌面应用程序中看到更新的场景？
