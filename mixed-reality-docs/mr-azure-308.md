---
title: MR 和 Azure 308-跨设备通知
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure 通知中心、Azure Functions 以及 Azure 存储和表。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合现实, 学院, unity, 教程, api, 通知, 函数, 表, 通知中心, hololens, 沉浸, vr
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694604"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR 和 Azure 308:跨设备通知

![最终产品-启动](images/AzureLabs-Lab8-00.png)

在本课程中, 你将学习如何使用 Azure 通知中心、Azure 表和 Azure Functions 向混合现实应用程序添加通知中心功能。

**Azure 通知中心**是一种 Microsoft 服务, 它允许开发人员将有针对性的个性化推送通知发送到所有平台, 并将其放入云中。 这可以有效地允许开发人员与最终用户通信, 甚至可以在各种应用程序之间进行通信, 具体取决于方案。 有关详细信息, 请访问**Azure 通知中心**[页](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)。

**Azure Functions**是一项 Microsoft 服务, 它允许开发人员在 Azure 中运行少量的代码 "函数"。 这提供了一种方法, 可将工作委托给云, 而不是本地应用程序, 这可能有很多好处。 **Azure Functions**支持多种开发语言, 包括 C\#、F\#、node.js、Java 和 PHP。 有关详细信息, 请访问**Azure Functions** [页](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

**Azure 表**是一种 Microsoft 云服务, 可让开发人员在云中存储结构化非 SQL 数据, 使其在任何地方都可以轻松访问。 该服务的设计无架构, 可根据需要进行表的发展, 因此非常灵活。 有关详细信息, 请访问**Azure 表**[页](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

完成本课程后, 你将拥有一个混合现实沉浸式头戴式耳机应用程序和一个台式 PC 应用程序, 该应用程序将能够执行以下操作:

1. 桌面电脑应用将允许用户使用鼠标移动2D 空间 (X 和 Y) 中的对象。

2. 电脑应用内对象的移动将使用 JSON 发送到云, 该程序采用字符串形式, 其中包含对象 ID、类型和转换信息 (X 和 Y 坐标)。 

3. 对于桌面应用程序具有相同场景的混合现实应用, 会收到有关对象移动的通知, 从通知中心服务 (刚刚由桌面 PC 应用程序更新)。 

4. 收到包含对象 ID、类型和转换信息的通知后, 混合现实应用会将接收到的信息应用到其自身的场景。

在您的应用程序中, 您将由您来决定如何将结果与您的设计相集成。 本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。 您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。 本课程是一个自包含教程, 并不直接涉及任何其他混合现实实验室。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 308:跨设备通知</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要侧重于 Windows Mixed Reality 沉浸 (VR) 耳机, 但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。 在本课程中, 你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。 使用 HoloLens 时, 可能会在语音捕获过程中注意到某些回声。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程面向具有 Unity 和C#的基本经验的开发人员。 另外请注意, 本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容 (5 月 2018)。 您可以随意使用最新的软件 (如[安装工具](install-the-tools.md)一文中所述), 但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件:

- [与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC, 用于沉浸式 (VR) 耳机开发
- [Windows 10 秋季创意者更新 (或更高版本) 已启用开发人员模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 启用了开发人员模式的[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- Azure 安装和访问通知中心的 Internet 访问

## <a name="before-you-start"></a>开始之前

- 为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。
- 你必须是 Microsoft 开发人员门户和应用程序注册门户的所有者, 否则你将不具有访问[第2章](#chapter-2---retrieve-your-new-apps-credentials)中的应用的权限。

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>第1章-在 Microsoft 开发人员门户中创建应用程序

若要使用**Azure 通知中心**服务, 你将需要在 Microsoft 开发人员门户中创建一个应用程序, 因为你的应用程序将需要注册, 以便它能够发送和接收通知。

1.  登录到[Microsoft 开发人员门户](https://developer.microsoft.com/dashboard)。

    > 你将需要登录到你的 Microsoft 帐户。

2.  在仪表板中, 单击 "**创建新应用**"。

    ![创建应用](images/AzureLabs-Lab8-01.png)

3.  将显示一个弹出窗口, 需要为新应用保留一个名称。 在文本框中, 插入一个适当的名称;如果所选名称可用, 则勾选标记将显示在文本框的右侧。 插入可用名称后, 单击弹出窗口左下角的 "**保留产品名称**" 按钮。

    ![反转名称](images/AzureLabs-Lab8-02.png)

4.  创建应用后, 你可以转到下一章节。

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>第2章-检索新的应用凭据

登录到应用程序注册门户, 其中将列出新应用程序, 并检索将用于在**Azure 门户**中设置**通知中心服务**的凭据。

1.  导航到[应用程序注册门户](http://apps.dev.microsoft.com)。

    ![应用程序注册门户](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > 你将需要使用 Microsoft 帐户进行登录。  
    > 这**必须**是上一[章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)使用 Windows 应用商店开发人员门户时使用的 Microsoft 帐户。

2.  你将在 "**我的应用程序**" 部分下找到你的应用程序。 找到后, 单击它, 随即会转到新页面, 其中包含应用名称和**注册**。

    ![新注册的应用](images/AzureLabs-Lab8-04.png)

3.  向下滚动注册页面, 找到**应用程序的机密**部分和**包 SID** 。 复制这两个用于在下一章中设置**Azure 通知中心服务**。

    ![应用程序机密](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>第3章-设置 Azure 门户: 创建通知中心服务

检索应用凭据后, 你将需要在 Azure 门户中创建 Azure 通知中心服务。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE] 
    > 如果还没有 Azure 帐户, 则需要创建一个。 如果在课堂或实验室中按照本教程进行学习, 请咨询教师或 proctors, 以获得设置新帐户的帮助。

2.  登录后, 单击左上角的 "**新建**", 搜索 "**通知中心**", 然后单击 "***输入***"。

    ![搜索通知中心](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > 在较新的门户中, 可能已将 "***新建***" 一词替换为 "**创建资源**"。

3.  新页将提供*通知中心*服务的说明。 在此提示符下, 选择 "**创建**" 按钮以创建与此服务的关联。

    ![创建通知中心实例](images/AzureLabs-Lab8-07.png)

4.  单击 "***创建***" 后:

    1.  为此服务实例插入所需的名称。

    2.  提供可与此应用关联的**命名空间**。

    3.  选择一个**位置。**

    4.  选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务 (例如这些实验室) 保存在一个公共资源组中。

        > 如果希望了解有关 Azure 资源组的详细信息, 请参阅此[链接, 了解如何管理资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。 

    5.  选择相应的**订阅**。

    6.  还需要确认是否已了解应用于此服务的条款和条件。

    7. 选择“创建”。

        ![填写服务详细信息](images/AzureLabs-Lab8-08.png)

5.  单击 "**创建**" 后, 需要等待创建服务, 这可能需要一分钟时间。

6.  创建服务实例后, 门户中将显示一个通知。

    ![通知](images/AzureLabs-Lab8-09.png)

7.  单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。 你将转到新的**通知中心**服务实例。

    ![中转到资源](images/AzureLabs-Lab8-10.png)
    
8.  从 "概述" 页中, 单击 "Windows (WNS)", 然后单击 " **Windows (WNS)"。** 右侧面板将更改为显示两个文本字段, 它们需要你之前设置的应用中的**包 SID**和**安全密钥**。

    ![新创建的集线器服务](images/AzureLabs-Lab8-11.png)

9. 将详细信息复制到正确的字段后, 请单击 "**保存**", 在成功更新通知中心后, 将收到通知。

    ![复制安全详细信息](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>第4章-设置 Azure 门户: 创建表服务

创建通知中心服务实例后, 请导航回 Azure 门户, 以便通过创建存储资源来创建 Azure 表服务。

1.  如果尚未登录, 请登录到[Azure 门户](https://portal.azure.com)。

2.  登录后, 单击左上角的 "**新建**", 然后搜索 "**存储帐户**", 然后单击 " **Enter**"。

    > [!NOTE] 
    > 在较新的门户中, 可能已将 "***新建***" 一词替换为 "**创建资源**"。

3.  从列表中选择 "**存储帐户-blob、文件、表、队列**"。

    ![搜索存储帐户](images/AzureLabs-Lab8-13.png)

4.  新页将提供**存储帐户**服务的说明。 在此提示符下, 选择 "**创建**" 按钮, 创建此服务的实例。

    ![创建存储实例](images/AzureLabs-Lab8-14.png)

5.  单击 "**创建**" 后, 将显示一个面板:

    1. 为此服务实例插入所需的**名称**(必须全部小写)。

    2. 对于**部署模型**, 单击 "**资源管理器**"。

    3.  对于 "**帐户类型**", 请使用下拉菜单选择 "**存储 (常规用途 v1)** "。

    4. 选择适当的**位置**。
    
    5.  对于 "**复制**" 下拉菜单, 选择 "**读取-访问-异地冗余存储 (GRS)** "。

    6.  对于 "**性能**", 请单击 "**标准**"。

    7.  在 "**需要安全传输**" 部分中, 选择 "**禁用**"。

    8.  从 "**订阅**" 下拉菜单中, 选择相应的订阅。

    9.  选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务 (例如这些实验室) 保存在一个公共资源组中。

        > 如果希望了解有关 Azure 资源组的详细信息, 请参阅此[链接, 了解如何管理资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    10. 如果这是一个选项, 请将**虚拟网络**保持为**禁用状态**。

    11. 单击“创建”。

        ![填写存储详细信息](images/AzureLabs-Lab8-15.png)

6.  单击 "**创建**" 后, 需要等待创建服务, 这可能需要一分钟时间。

7.  创建服务实例后, 门户中将显示一个通知。 单击通知以浏览新服务实例。

    ![新存储通知](images/AzureLabs-Lab8-16.png)

8.  单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。 你将转到新的存储服务实例概述页。

    ![中转到资源](images/AzureLabs-Lab8-17.PNG)

9. 在 "概述" 页中, 单击右侧的 "**表**"。
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. 右侧面板将更改为显示**表服务**信息, 你需要添加一个新表。 单击左上角的 " **+** **表**" 按钮即可执行此操作。

    ![打开表](images/AzureLabs-Lab8-19.png)

11. 将显示一个新页, 需要在其中输入**表名称**。 这是将在后面章节中用于引用应用程序中的数据的名称。 插入适当的名称, 然后单击 **"确定"** 。

    ![创建新表](images/AzureLabs-Lab8-20.png)    

12. 创建新表后, 可以在 "**表服务**" 页 (底部) 中查看它。

    ![已创建新表](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>第5章-完成 Visual Studio 中的 Azure 表

由于已设置了**表服务**存储帐户, 因此可以向其添加数据, 这将用于存储和检索信息。 可以通过**Visual Studio**来编辑表。

1.  打开**Visual Studio**。

2.  从菜单中, 单击 "**查看** > **Cloud Explorer**"。

    ![打开 cloud explorer](images/AzureLabs-Lab8-22.png)

3.  **Cloud Explorer**将作为停靠项打开 (患者, 因为加载可能需要一些时间)。

    > [!NOTE] 
    > 如果用于创建*存储帐户*的订阅不可见, 请确保: 
    > - 已登录到与 Azure 门户一起使用的帐户。
    > - 从 "帐户管理" 页中选择了你的订阅 (你可能需要从帐户设置应用筛选器):  
    >
    >   ![查找订阅](images/AzureLabs-Lab8-22-5.png)

4.  将显示你的 Azure 云服务。 查找**存储帐户**, 并单击其左侧的箭头以展开你的帐户。

    ![打开存储帐户](images/AzureLabs-Lab8-23.png)

5.  展开后, 新创建的**存储帐户**应该可用。 单击存储左侧的箭头, 然后在展开后, 查找 "**表**" 并单击该按钮旁边的箭头, 以显示在上一章中创建的**表**。 双击**表**。

    ![打开场景对象表](images/AzureLabs-Lab8-24.png)

6.  您的表将在您的 Visual Studio 窗口的中心打开。 单击与表图标 **+** （加上） 在其上。

    ![添加新表](images/AzureLabs-Lab8-25.png)

7.  将显示一个窗口, 提示你*添加实体*。 您将创建三个实体, 每个实体都有多个属性。 你会注意到已提供了*PartitionKey*和*RowKey* , 因为表使用这些方法来查找数据。 

    ![分区和行键](images/AzureLabs-Lab8-26.png)

8. 按如下所示更新**PartitionKey**和**RowKey**的*值*(请记得为你添加的每个行属性执行此操作, 但每次都递增 RowKey):

    ![添加正确的值](images/AzureLabs-Lab8-26-5.png)

9.  单击 "**添加属性**" 以添加额外的数据行。 使第一个空表与下表匹配。

10. 完成后, 单击 **"确定"** 。

    ![完成后单击 "确定"](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > 确保将**X**、 **Y**和**Z**条目的**类型**更改为**Double**。 

11. 你会注意到, 你的表现在具有一行数据。 再次单击 **+** (加号) 图标以添加另一个实体。

    ![第一行](images/AzureLabs-Lab8-27-5.png)

12. 创建其他属性, 然后将新实体的值设置为与下面显示的值相匹配。

    ![添加多维数据集](images/AzureLabs-Lab8-28.png)

13. 重复上一步以添加另一个实体。 将此实体的值设置为下面显示的值。

    ![添加圆柱体](images/AzureLabs-Lab8-29.png)

14. 现在, 你的表应如下所示。

    ![表完成](images/AzureLabs-Lab8-30.png)

15. 你已完成本章节。 请确保保存。

## <a name="chapter-6---create-an-azure-function-app"></a>第6章-创建 Azure Function App

创建一个 Azure Function App, 桌面应用程序将调用该来更新**表**服务, 并通过**通知中心**发送通知。

首先, 需要创建一个文件, 该文件允许 Azure 函数加载所需的库。

1.  打开**记事本**(按 Windows 键, 然后键入 Notepad)。

    ![打开记事本](images/AzureLabs-Lab8-31.png)

2.  打开记事本后, 将下面的 JSON 结构插入其中。 完成此操作后, 将其以**项目 json**的形式保存在桌面上。 命名正确, 这一点很重要: 确保它没有 **.txt**文件扩展名。 此文件定义你的函数将使用的库, 如果你使用了 NuGet, 则该文件将非常熟悉。

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

4.  登录后, 单击左上角的 "**新建**", 然后搜索 " **Function App**", 按**enter**。

    ![搜索函数应用](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > 在较新的门户中, 可能已将 "**新建**" 一词替换为 "**创建资源**"。

5.  新页将提供**Function App**服务的说明。 在此提示符下, 选择 "**创建**" 按钮以创建与此服务的关联。

    ![function app 实例](images/AzureLabs-Lab8-33.png)

6.  单击 "**创建**" 后, 请填写以下内容:

    1. 对于 "**应用名称**", 请为此服务实例插入所需的名称。

    2. 选择**订阅**。

    3. 选择适合你的定价层, 如果这是第一次创建**Function App 服务**, 则应提供免费层。

    4. 选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务 (例如这些实验室) 保存在一个公共资源组中。

        > 如果希望了解有关 Azure 资源组的详细信息, 请参阅此[链接, 了解如何管理资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 对于**操作系统**, 请单击 "Windows", 因为这是预期的平台。

    6. 选择**托管计划**(本教程使用**消耗计划**。

    7. 选择**位置** **(选择与在上一步骤中生成的存储相同的位置)**

    8. 对于 "**存储**" 部分,**你必须选择在上一步中创建的存储服务**。

    9. 在此应用中不需要*Application Insights* , 因此可随意将其**关闭**。

    10. 单击“创建”。

        ![创建新实例](images/AzureLabs-Lab8-34.png)

7.  单击 "**创建**" 后, 将需要等待服务创建完成, 这可能需要一分钟时间。

8.  创建服务实例后, 门户中将显示一个通知。

    ![新建通知](images/AzureLabs-Lab8-35.png)

9.  单击通知以浏览新服务实例。

10. 单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。 

    ![中转到资源](images/AzureLabs-Lab8-36.png)

11. 单击 " **+** *函数*" 旁边的加号图标, 以*创建新*的。

    ![添加新函数](images/AzureLabs-Lab8-37.png)

12. 在中央面板中, 将显示 "**函数**创建" 窗口。 忽略面板上半部分中的信息, 然后单击位于底部附近的 "**自定义函数**" (蓝色区域中的), 如下所示。

    ![自定义函数](images/AzureLabs-Lab8-38.png)

13. 窗口中的新页面将显示各种函数类型。 向下滚动以查看紫色类型, 然后单击 " **HTTP PUT**元素"。

    ![http put 链接](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > 但是, 你可能需要向下滚动页面 (如果已发生 Azure 门户更新, 此映像可能看起来不完全相同), 但你正在寻找称为*HTTP PUT*的元素。

14. 此时将显示 " **HTTP PUT** " 窗口, 需要在其中配置函数 (请参阅下面的 "图像")。

    1.  对于 "**语言",** 使用下拉菜单选择 "C\#"。

    2.  对于 **"名称", 请**输入适当的名称。

    3.  在 "**身份验证级别**" 下拉菜单中, 选择 "**函数**"。

    4.  对于 "**表名**" 部分, 需要使用以前用于创建**表**服务的确切名称 (包括相同的字母大小写)。

    5.  在 "**存储帐户连接**" 部分中, 使用下拉菜单, 并从该处选择存储帐户。 如果没有, 请单击部分标题旁边的**新**超链接, 以显示另一个面板, 应在其中列出你的存储帐户。

        ![新存储](images/AzureLabs-Lab8-40.png)

15. 单击 "**创建**", 你将收到通知, 告知你的设置已成功更新。

    ![create 函数](images/AzureLabs-Lab8-41.png)

16. 单击 "**创建**" 后, 将重定向到函数编辑器。

    ![更新函数代码](images/AzureLabs-Lab8-42.png)

17. 将以下代码插入函数编辑器中 (替换函数中的代码):

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
    > 使用包含的库, 函数接收在 Unity 场景中移动的对象的名称和位置 (作为C#对象, 称为**UnityGameObject**)。 然后, 此对象用于更新创建的表中的对象参数。 遵循此功能后, 该函数将调用你创建的通知中心服务, 这会通知所有已订阅的应用程序。

18. 在代码准备就绪后, 单击 "**保存**"。

19. 接下来，单击 **\<** （箭头） 图标，在页面的右侧。

    ![打开上传面板](images/AzureLabs-Lab8-43.png)

20. 面板会从右侧滑入。 在该面板中, 单击 "**上载**", 将显示文件浏览器。

21. 导航到, 然后单击 "您之前在**记事本**中创建的**项目 json**文件", 然后单击 "**打开**" 按钮。 此文件定义函数将使用的库。

    ![上传 json](images/AzureLabs-Lab8-44.png)

22. 文件上传后, 它将显示在右侧的面板中。 单击它会在**函数**编辑器中打开它。 它必须与下一个图像**完全**相同 (低于步骤 23)。

23. 然后, 在左侧面板的 "**函数**" 下, 单击 "**集成**" 链接。

    ![集成函数](images/AzureLabs-Lab8-45.png)

24. 在下一页上, 单击右上角的 "**高级编辑器**" (如下所示)。

    ![打开高级编辑器](images/AzureLabs-Lab8-46.png)

25. 将在中心面板中打开**函数 json**文件, 需要将其替换为以下代码片段。 这会定义正在生成的函数和传递到函数的参数。

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

26. 编辑器现在应如下图所示:

    ![返回到标准编辑器](images/AzureLabs-Lab8-47.png)

27. 你可能会注意到, 你刚插入的输入参数可能与你的表和存储详细信息不匹配, 因此将需要使用你的信息更新。 请不要**在此处执行此操作**, 如下所述。 只需单击页面右上角的 "**标准编辑器**" 链接, 返回即可。

28. 返回到**标准编辑器**, 单击 "**输入**" 下的 " **Azure 表存储 (表)** "。 
    
    ![表输入](images/AzureLabs-Lab8-47-5.png)

29. 请确保对**你**的信息的以下匹配项, 因为它们可能不同 (下面的步骤中有一个映像):

    1.  **表名**: 在 Azure 存储中创建的表的名称, 表服务。

    2.  **存储帐户连接:** 单击 "**新建**" (显示在下拉菜单旁), 此时会在窗口的右侧显示一个面板。

        ![新存储](images/AzureLabs-Lab8-48.png)

        1.  选择之前创建的**存储帐户**以托管**函数应用。**

        2. 你会注意到已创建**存储帐户**连接值。

        3. 完成后, 请务必按 "**保存**"。

    3.  "**输入**" 页现在应与下面的内容匹配, 并显示**你的**信息。

        ![输入完成](images/AzureLabs-Lab8-49.png)

30. 接下来, 在 "**输出**" 下单击 " **Azure 通知中心 (通知)** "。 请确保以下各项与**你**的信息匹配, 因为它们可能不同 (下面的步骤中有一个映像):

    1.  **通知中心名称**: 这是你之前创建的**通知中心**服务实例的名称。

    2.  **通知中心命名空间连接**: 单击 "**新建**", 随即出现下拉菜单。

        ![检查输出](images/AzureLabs-Lab8-50.png)

    3. 此时将显示**连接**弹出窗口 (请参阅下图), 需要在其中选择之前设置的**通知中心**的**命名空间**。

    4. 从中间的下拉菜单中选择**通知中心**名称。

    5.  将**策略**下拉菜单设置为**DefaultFullSharedAccessSignature**。

    6. 单击 "**选择**" 按钮返回。

        ![输出更新](images/AzureLabs-Lab8-51.png)

31.  "**输出**" 页现在应与下面的内容匹配, 但会改为替换为**您**的信息。 请确保按 "**保存**"。

> [!WARNING]
> *不要直接编辑通知中心名称*(应使用**高级编辑器**完成此操作, 前提是已正确执行前面的步骤。

![输出完成](images/AzureLabs-Lab8-50.png)

32. 此时, 应测试函数, 以确保其正常运行。 要实现此目的，请执行以下操作： 

    1. 再次导航到函数页:

        ![输出完成](images/AzureLabs-Lab8-50-1.png)

    2. 返回到 "函数" 页, 单击页最右侧的 "**测试**" 选项卡以打开 "*测试*" 边栏选项卡:

        ![输出完成](images/AzureLabs-Lab8-50-2.png)

    3. 在边栏选项卡的 "**请求正文**" 文本框中, 粘贴以下代码:

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

    4. 测试代码准备就绪后, 单击右下角的 "**运行**" 按钮, 将运行测试。 测试的输出日志将显示在功能代码下方的控制台区域中。

        ![输出完成](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > 如果上述测试失败, 则需要仔细检查是否已按照上述步骤执行操作, 尤其是**集成面板**中的设置。 

## <a name="chapter-7---set-up-desktop-unity-project"></a>第7章-设置桌面 Unity 项目

> [!IMPORTANT]
> 你现在正在创建的桌面应用程序**将不**能在 Unity 编辑器中运行。 它需要在使用 Visual Studio (或已部署的应用程序) 生成应用程序后, 在编辑器之外运行。 

下面是用于使用 Unity 和混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。

设置并测试混合现实沉浸式耳机。

> [!NOTE] 
> 本课程**不**需要移动控制器。 如果需要支持设置沉浸式耳机, 请参阅此链接,[了解如何设置 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  打开**Unity** , 并单击 "**新建**"。

    ![新建 unity 项目](images/AzureLabs-Lab8-52.png)

2.  需要提供 Unity 项目名称, 插入**UnityDesktopNotifHub**。 请确保 "项目类型" 设置为 " **3d**"。 将位置设置为合适的**位置**(请记住, 更接近根目录更好)。 然后单击 "**创建项目**"。

    ![创建项目](images/AzureLabs-Lab8-53.png)

3.  当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "**编辑** > **首选项**", 然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

    ![设置外部 VS 工具](images/AzureLabs-Lab8-54.png)

4.  接下来, 转到 "**文件** > " "**生成设置**" 并选择 "**通用 Windows 平台**", 然后单击 "**切换平台**" 按钮以应用你的选择。

    ![交换机平台](images/AzureLabs-Lab8-55.png)

5.  仍在**文件** > **生成设置**中时, 请确保:

    1.  **目标设备**设置为**任何设备**

        > 此应用程序将用于桌面, 因此必须是**任何设备**

    2.  **生成类型**设置为**D3D**

    3.  **SDK**设置为 "**最新安装**"

    4.  **Visual Studio 版本**设置为 "**最新安装**"

    5.  "**生成并运行**" 设置为 "**本地计算机**"

    6.  在此过程中, 需要保存场景, 并将其添加到生成中。

        1. 通过选择 "**添加打开的场景**" 来执行此操作。 将显示 "保存" 窗口。

            ![添加打开的场景](images/AzureLabs-Lab8-56.png)

        2. 为此创建新文件夹, 并为将来的任何场景创建一个新文件夹, 然后选择 "**新建文件夹**" 按钮以创建新文件夹, 将其命名为**场景**。

            ![新的场景文件夹](images/AzureLabs-Lab8-57.png)

        3. 打开新创建的**场景**文件夹, 然后在 "文件名 **:** 文本" 字段中, 键入 **"\_NH\_Desktop 场景**", 并按 "**保存**"。

            ![新 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  现在, "**生成设置**" 中的其余设置应保留为默认值。

6.  在同一窗口中, 单击 "**播放机设置**" 按钮, 这会在**检查器**所在的空间中打开相关的面板。

7.  在此面板中, 需要验证几项设置:

    1.  在 "**其他设置**" 选项卡中:

        1.  **脚本运行时版本**应为试验性的 **(.Net 4.6 等效项)**

        2. **脚本编写后端**应为 **.net**

        3. **API 兼容级别**应为 **.net 4.6**

            ![4.6 net 版本](images/AzureLabs-Lab8-59.png)

    2.  在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:

        - **InternetClient**

            ![刻度 internet 客户端](images/AzureLabs-Lab8-60.png)

8.  返回**生成设置** *Unity\# C 项目*不再灰显; 勾选此的旁边的复选框。

9.  关闭 "**生成设置**" 窗口。

10. 保存场景和项目**文件** > **保存场景/文件** > **保存项目**。

    > [!IMPORTANT]
    > 如果要跳过此项目的*Unity 设置*组件 (桌面应用程序), 并继续直接进入代码, 请随时[下载此 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), 将其作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目, 然后继续从[章节9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。  你仍需添加脚本组件。

## <a name="chapter-8---importing-the-dlls-in-unity"></a>第8章-在 Unity 中导入 Dll

你将使用适用于 Unity 的 Azure 存储 (它本身利用 .Net SDK for Azure)。 有关详细信息, 请[参阅此链接, 了解有关适用于 Unity 的 Azure 存储](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。

当前 Unity 中存在一个已知问题, 需要在导入后重新配置插件。 解决 bug 后, 将不再需要这些步骤 (本部分中的 4-7)。

若要将 SDK 导入到自己的项目中, 请确保已从 GitHub 下载最新的[**unitypackage**](https://aka.ms/azstorage-unitysdk) 。 然后, 执行以下操作:

1.  使用 "  **\>资产导入包\>自定义包**" 菜单选项将**unitypackage**添加到 Unity。

2.  在弹出的 "**导入 Unity 包**" 框中, 可以选择 "*插件* \> * 存储" 下的所有内容 * * *。  取消选中所有其他内容, 因为本课程不需要这样做。

    ![导入到包](images/AzureLabs-Lab8-61.png)

3.  单击 "***导入***" 按钮, 将项添加到项目。

4.  在项目视图中, 在 "**插件**" 下, 选择 "**存储**" 文件夹, 并*仅*选择以下插件:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Windowsazure.storage
    -   Newtonsoft.Json
    -   System.Spatial

![取消选中任何平台](images/AzureLabs-Lab8-62.png)

5.  选择*这些特定插件*后,**取消选中** **任何平台**并**取消选中**" **WSAPlayer** ", 然后单击 "**应用**"。

    ![应用平台 dll](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > 我们正在将这些特定插件标记为仅在 Unity 编辑器中使用。 这是因为在从 Unity 导出项目后, 将使用 WSA 文件夹中的相同插件的不同版本。

6.  在**存储**插件文件夹中, 只选择:

    -   Microsoft。

        ![为 dll 设置不处理](images/AzureLabs-Lab8-64.png)

7.  选中 "**平台设置**" 下的 "**不处理**" 框, 并单击 "***应用***"。

    ![不应用处理](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > 我们正在将此插件标记为 "不处理", 因为 Unity 程序集 patcher 在处理此插件时遇到困难。 即使未处理插件, 该插件仍可正常工作。

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>第9章-创建桌面 Unity 项目中的 TableToScene 类

现在, 需要创建包含代码的脚本来运行此应用程序。

需要创建的第一个脚本是**TableToScene**, 它负责:

-   读取 Azure 表中的实体。
-   使用表数据确定要生成的对象, 以及在哪个位置生成的对象。

需要创建的第二个脚本是**CloudScene**, 它负责:

-   注册左键单击事件, 使用户能够在场景周围拖动对象。
-   将此 Unity 场景中的对象数据序列化, 并将其发送到 Azure Function App。

若要创建此类:

1.  右键单击位于 "项目" 面板中的 "**资产**" 文件夹, 然后单击 "**创建** > **文件夹**"。 命名文件夹**脚本**。

    ![创建脚本文件夹](images/AzureLabs-Lab8-66.png)

    ![创建脚本文件夹2](images/AzureLabs-Lab8-67.png)

2.  双击刚创建的文件夹以将其打开。

3.  右键单击 "**脚本**" 文件夹中, 单击 "**创建** >   **C#脚本**"。 将脚本命名为**TableToScene**。

    ![新的 c](images/AzureLabs-Lab8-68.png)
    # 脚本![TableToScene 重命名](images/AzureLabs-Lab8-69.png)

4.  双击脚本, 在 Visual Studio 2017 中将其打开。

5.  添加以下命名空间:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  在类中, 插入以下变量:

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
    > 将**accountName**值替换为 Azure 存储服务名称, 将**accountKey**值替换为 azure 门户中的 Azure 存储服务 (请参阅下图) 中的密钥值。 
    >
    > ![提取帐户密钥](images/AzureLabs-Lab8-70.png)

7.  现在, 请添加**Start ()** 和**唤醒 ()** 方法来初始化类。

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

8.  在**TableToScene**类中, 添加方法, 该方法将检索 Azure 表中的值, 并使用这些值在场景中生成相应的基元。

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

9.  在**TableToScene**类之外, 需要定义应用程序用于序列化和反序列化**表实体**的类。

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

10. 请确保在返回到 Unity 编辑器之前**保存**。

11. 单击 "**层次结构**" 面板中的**主摄像机**, 使其属性显示在**检查器**中。

12. 在 "**脚本**" 文件夹打开的情况下, 选择脚本**TableToScene 文件**, 然后将其拖到**主摄像机**。 结果应如下所示:

    ![向主相机添加脚本](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>第10章-创建桌面 Unity 项目中的 CloudScene 类

需要创建的第二个脚本是**CloudScene**, 它负责:

-   注册左键单击事件, 使用户能够在场景周围拖动对象。

-   将此 Unity 场景中的对象数据序列化, 并将其发送到 Azure Function App。

创建第二个脚本:

1.  右键单击 "**脚本**" 文件夹中, 单击 "**创建**, **C\#脚本**"。 将脚本命名为**CloudScene**
    
    ![新的 c](images/AzureLabs-Lab8-72.png)
    # 脚本![重命名 CloudScene](images/AzureLabs-Lab8-73.png)

2.  添加以下命名空间:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  插入以下变量:

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

4.  将**azureFunctionEndpoint**值替换为 azure 门户中 Azure Function App 服务中找到的 AZURE Function App URL, 如下图所示:

    ![获取函数 URL](images/AzureLabs-Lab8-74.png)

5.  现在, 请添加**Start ()** 和**唤醒 ()** 方法来初始化类。

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

6.  在**Update ()** 方法中, 添加下面的代码, 用于检测鼠标输入并拖动, 这反过来会移动场景中的 gameobject。 如果用户已拖放了一个对象, 它会将该对象的名称和坐标传递给**UpdateCloudScene ()** 方法, 后者将调用 azure Function App 服务, 该服务将更新 azure 表并触发通知。

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

7.  现在, 请添加**UpdateCloudScene ()** 方法, 如下所示:

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

8.  保存代码并返回到 Unity

9.  将**CloudScene**脚本拖到**主照相机**上。 

    1. 单击 "**层次结构**" 面板中的**主摄像机**, 使其属性显示在**检查器**中。 

    2. 在 "**脚本**" 文件夹打开的情况下, 选择**CloudScene**脚本, 并将其拖动到**主相机**上。 结果应如下所示:

        > ![将云脚本拖到主相机上](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>第11章-将桌面项目构建到 UWP

此项目的 Unity 部分所需的所有内容现在都已完成。

1.  导航到 "**生成设置**" ("**文件** > **生成设置**")。

2.  在**生成设置**窗口中, 单击 "**生成**"。

    ![生成项目](images/AzureLabs-Lab8-76.png)

3.  将弹出一个**文件资源管理器**窗口, 提示你提供要生成的位置。 在左上角单击 "**新建文件夹**", 创建一个新文件夹, 并将其命名为 "**生成**"。

    ![用于生成的新文件夹](images/AzureLabs-Lab8-77.png)

    1.  打开 "新建**生成**" 文件夹, 并创建另一个文件夹 (使用 "**新建文件夹**"), 并将其命名为 " **\_NH 桌面\_应用**"。

        ![文件夹名称 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  选中 " **NH\_桌面\_" 应用**。 单击 "**选择文件夹**"。 项目将需要一分钟或更长时间才能生成。

4.  以下生成将显示**文件资源管理器**, 显示新项目的位置。 无需打开它, 因为在接下来的几章中, 你需要先创建另一个 Unity 项目。


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>第12章-设置混合现实 Unity 项目

下面是使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。

1.  打开**Unity** , 并单击 "**新建**"。

    ![新建 unity 项目](images/AzureLabs-Lab8-79.png)

2.  你现在需要提供 Unity 项目名称, 请插入**UnityMRNotifHub**。 请确保 "项目类型" 设置为 " **3d**"。 将位置设置为合适的**位置**(请记住, 更接近根目录更好)。 然后单击 "**创建项目**"。

    ![名称 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "**编辑** > **首选项**", 然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

    ![将外部编辑器设置为 VS](images/AzureLabs-Lab8-81.png)

4.  接下来, 转到 "**文件** > **生成设置**", 并通过单击 "**切换平台**" 按钮将平台切换到**通用 Windows 平台**。

    ![将平台切换到 UWP](images/AzureLabs-Lab8-82.png)

5.  中转到 "**文件** > " "**生成设置**", 并确保:

    1.  **目标设备**设置为**任何设备**

        > 对于 Microsoft HoloLens, 将 "**目标设备**" 设置为 " *hololens*"。

    2.  **生成类型**设置为**D3D**

    3.  **SDK**设置为 "**最新安装**"

    4.  **Visual Studio 版本**设置为 "**最新安装**"

    5.  "**生成并运行**" 设置为 "**本地计算机**"

    6.  在此过程中, 需要保存场景, 并将其添加到生成中。

        1. 通过选择 "**添加打开的场景**" 来执行此操作。 将显示 "保存" 窗口。

            ![添加打开的场景](images/AzureLabs-Lab8-83.png)

        2. 为此创建新文件夹, 并为将来的任何场景创建一个新文件夹, 然后选择 "**新建文件夹**" 按钮以创建新文件夹, 将其命名为**场景**。

            ![新的场景文件夹](images/AzureLabs-Lab8-84.png)

        3. 打开新创建的**场景**文件夹, 然后在 "文件名 **:** 文本" 字段中, 键入**NH\_MR\_场景**, 并按 "**保存**"。

            ![新场景-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  现在, "**生成设置**" 中的其余设置应保留为默认值。

6.  在同一窗口中, 单击 "**播放机设置**" 按钮, 这会在**检查器**所在的空间中打开相关的面板。    

    ![打开播放机设置](images/AzureLabs-Lab8-86.png)

7.  在此面板中, 需要验证几项设置:

    1.  在 "**其他设置**" 选项卡中:

        1.  **脚本运行时版本**应为**试验**性的 (.net 4.6 等效项)
        2.  **脚本编写后端**应为 ***.net***
        3.  **API 兼容级别**应为 **.net 4.6**

            ![api 兼容性](images/AzureLabs-Lab8-87.png)

    2.  在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 在 "**支持的虚拟现实**" 下, 确保已添加**Windows Mixed reality SDK**

        ![更新 xr 设置](images/AzureLabs-Lab8-88.png)        

    3.  在 "**发布设置**" 选项卡中, 在 "**功能**" 下面:

        - **InternetClient**           

            ![刻度 internet 客户端](images/AzureLabs-Lab8-89.png)

8.  返回**生成设置**, **Unity C#项目**不再灰显: 勾选此旁边的复选框。

9.  完成这些更改后, 关闭 "生成设置" 窗口。

10. 保存场景和项目**文件** > **保存场景/文件** > **保存项目**。

    > [!IMPORTANT]
    > 如果要跳过此项目的*Unity 设置*组件 (混合现实应用), 并继续直接进入代码, 请随时[下载此 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), 将其作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目, 然后继续从[第14章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project): 你仍需添加脚本组件。

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>第13章-导入混合现实 Unity 项目中的 Dll

你将使用适用于 Unity 的 Azure 存储库 (使用 .Net SDK for Azure)。 请单击以下[链接, 了解如何通过 Unity 使用 Azure 存储](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。
当前 Unity 中存在一个已知问题, 需要在导入后重新配置插件。 解决 bug 后, 将不再需要这些步骤 (本部分中的 4-7)。

若要将 SDK 导入到自己的项目中, 请确保已下载最新的[unitypackage](https://aka.ms/azstorage-unitysdk)。 然后, 执行以下操作:

1.  使用 "**资产** > **导入包** > **自定义包**" 菜单选项将从上 unitypackage 下载的文件添加到 Unity。

2.  在弹出的 "**导入 Unity 包**" 框中, 可以选择 "**插件** > " "**存储**" 下的所有内容。

    ![导入包](images/AzureLabs-Lab8-90.png)

3.  单击 "**导入**" 按钮, 将项添加到项目。

4.  在项目视图中, 在 "**插件**" 下, 选择 "**存储**" 文件夹, 并*仅*选择以下插件:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Windowsazure.storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![选择插件](images/AzureLabs-Lab8-91.png)

5.  选择*这些特定插件*后,**取消选中** **任何平台**并**取消选中**" **WSAPlayer** ", 然后单击 "**应用**"。

    ![应用平台更改](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > 你要将这些特定插件标记为仅在 Unity 编辑器中使用。 这是因为在从 Unity 导出项目后, 将使用 WSA 文件夹中的相同插件的不同版本。

6.  在**存储**插件文件夹中, 只选择:

    -   Microsoft。

        ![选择数据服务客户端](images/AzureLabs-Lab8-93.png)

7.  选中 "**平台设置**" 下的 "**不处理**" 框, 并单击 "**应用**"。

    ![不处理](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > 你正在将此插件标记为 "不处理", 因为 Unity 程序集 patcher 在处理此插件时遇到困难。 即使未处理插件, 该插件仍可正常工作。

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>第14章-在混合现实 Unity 项目中创建 TableToScene 类

**TableToScene**类与第[9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)中所述的类完全相同。 按照第[9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)所述的相同过程, 在混合现实 Unity 项目中创建相同的类。

完成本章后, 这两个**Unity 项目**将在主摄像机上设置此类。

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>第15章-在混合现实 Unity 项目中创建 NotificationReceiver 类

需要创建的第二个脚本是**NotificationReceiver**, 它负责:

-   在初始化时向通知中心注册应用。
-   正在侦听来自通知中心的通知。
-   从收到的通知反序列化对象数据。
-   基于反序列化的数据移动场景中的 Gameobject。

创建**NotificationReceiver**脚本:

1.  右键单击 "**脚本**" 文件夹中, 单击 "**创建**, **C\#脚本**"。 将脚本命名为**NotificationReceiver**。

    ![创建新的 c](images/AzureLabs-Lab8-95.png)
    # 脚本![名称 NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  双击脚本将其打开。

3.  添加以下命名空间:

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

4.  插入以下变量:

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

5.  将**hubName**值替换为你的通知中心服务名称, 将**hubListenEndpoint**值替换为在 azure 门户中的 "访问策略" 选项卡 (请参阅下图) 中的 "访问策略" 选项卡中找到的终结点值。

    ![插入通知中心策略终结点](images/AzureLabs-Lab8-97.png)

6.  现在, 请添加**Start ()** 和**唤醒 ()** 方法来初始化类。

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

7.  添加**WaitForNotification**方法, 以允许该应用从通知中心库接收通知, 而无需冲突主线程:

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

8.  下面的**InitNotificationAsync ()** 方法在初始化时将应用程序注册到通知中心服务。 代码已注释掉, 因为 Unity 将不能生成项目。 在 Visual Studio 中导入 Azure 消息传递 Nuget 包时, 将删除注释。

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

9.  每次收到通知时, 将触发以下处理程序 **\_PushNotificationReceived ()** 。 它将反序列化通知, 该通知将是已移动到桌面应用程序中的 Azure 表实体, 然后将 MR 场景中的相应 GameObject 移到相同的位置。 
    
    > [!IMPORTANT]
    > 代码已被注释掉, 因为代码引用 Azure 消息库, 你将在 Visual Studio 中使用 Nuget 包管理器生成 Unity 项目后添加该消息库。 因此, 除非已注释掉, 否则 Unity 项目将无法生成。请注意, 如果你生成项目, 然后希望返回到 Unity, 你将需要**重新注释**该代码。

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

10. 请记住在返回到 Unity 编辑器之前保存更改。

11. 单击 "**层次结构**" 面板中的**主摄像机**, 使其属性显示在**检查器**中。

12. 在 "**脚本**" 文件夹打开的情况下, 选择**NotificationReceiver**脚本, 并将其拖动到**主相机**上。 结果应如下所示:

    ![将通知接收方脚本拖到照相机](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > 如果你要为 Microsoft HoloLens 开发此内容, 则需要更新**摄像机**的*相机*组件, 以便:
    > - 清除标志:纯色
    > - 背景：黑色

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>第16章-将混合现实项目构建到 UWP

本章与上一个项目的生成过程完全相同。 此项目的 Unity 部分所需的所有内容现在均已完成, 因此可以从 Unity 构建它。

1.  导航到 "**生成设置**" ("**文件** > **生成设置**")。

2.  从 "**生成设置**" 菜单中, 确保**Unity C#项目*** 为勾选 (这将允许您在生成后编辑此项目中的脚本)。

3.  完成此操作后, 单击 "**生成**"。

    ![生成项目](images/AzureLabs-Lab8-99.png)

4.  将弹出一个**文件资源管理器**窗口, 提示你提供要生成的位置。 在左上角单击 "**新建文件夹**", 创建一个新文件夹, 并将其命名为 "**生成**"。

    ![创建生成文件夹](images/AzureLabs-Lab8-100.png)

    1.  打开 "新建**生成**" 文件夹, 并创建另一个文件夹 (使用 "**新文件夹**"), 并将其命名为 " **\_NH MR\_应用**"。

        ![创建 NH_MR_Apps 文件夹](images/AzureLabs-Lab8-101.png)

    2.  已选择**NH\_MR\_应用**。 单击 "**选择文件夹**"。 项目将需要一分钟或更长时间才能生成。

5.  生成后, 将在新项目的位置打开**文件资源管理器**窗口。



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>第17章-将 NuGet 包添加到 UnityMRNotifHub 解决方案

> [!WARNING] 
> 请记住, 一旦你添加了以下 NuGet 包 (并取消注释下一[章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)中的代码), 在 Unity 项目中重新打开时, 代码将显示错误。 如果希望返回并继续在 Unity 编辑器中进行编辑, 则需要 errosome 代码的注释, 稍后在 Visual Studio 中重新注释。 

混合现实生成完成后, 导航到你构建的混合现实项目, 并双击该文件夹内的解决方案 (.sln) 文件, 以通过 Visual Studio 2017 打开解决方案。
你现在需要添加**Windowsazure.storage** NuGet 包;这是一个用于从通知中心接收通知的库。

导入 NuGet 包:

1.  在**解决方案资源管理器**中, 右键单击你的解决方案

2.  单击 "**管理 NuGet 包**"。

    ![打开 nuget 管理器](images/AzureLabs-Lab8-102.png)

3.  选择 "***浏览***" 选项卡并搜索**windowsazure.storage**。

    ![查找 windows azure 消息包](images/AzureLabs-Lab8-103.png)

4.  选择结果 (如下所示), 并在右侧的窗口中选择 "**项目**" 旁边的复选框。 这会在 "**项目**" 旁边的复选框中放置一个勾选标记, 并在 " **Assembly-CSharp** " 和 " **UnityMRNotifHub** " 项目旁边放置一个复选框。

    ![勾选所有项目](images/AzureLabs-Lab8-104.png)

5.  最初提供的版本**可能**与此项目不兼容。 因此, 请单击 "**版本**" 旁边的下拉菜单, 单击 "**版本 0.1.7.9**", 然后单击 "**安装**"。

6.  你现在已经完成了 NuGet 包的安装。 查找在**NotificationReceiver**类中输入的注释代码, 并删除注释。



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>第18章-编辑 UnityMRNotifHub 应用程序, NotificationReceiver 类

添加**NuGet 包**后, 需要*取消注释* **NotificationReceiver**类中的某些代码。

这包括：

1. 位于顶部的命名空间:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. **InitNotificationsAsync ()** 方法中的所有代码:

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
> 上面的代码中包含注释: 确保你未意外*取消注释*该注释 (如果你有!, 代码将不会编译)。

3. 最后是**Channel_PushNotificationReceived**事件:

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

在这些取消注释中, 请确保保存, 然后转到下一章节。

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>第19章-将混合现实项目关联到应用商店应用

现在需要将**混合现实**项目关联到在实验室开始时创建的应用商店应用。

1.  打开解决方案。

2.  右键单击 "解决方案资源管理器面板" 中的 UWP 应用项目, 单击 "前往应用**商店**", 并**将应用与应用商店关联 ...** 。

    ![打开存储关联](images/AzureLabs-Lab8-105.png)

3.  将显示一个新窗口 **, 称为 "将应用与 Windows 应用商店关联"** 。 单击“下一步” 。

    ![切换到下一个屏幕](images/AzureLabs-Lab8-106.png)

4.  它将加载与已登录的帐户相关联的所有应用程序。 如果你未登录到你的帐户, 则可以在此页上**登录**。

5.  查找你在本教程开始时创建的**应用商店应用名称**, 然后选择它。 然后，单击“下一步”。

    ![查找并选择你的商店名称](images/AzureLabs-Lab8-107.png)

6.  单击 "**关联**"。

    ![关联应用](images/AzureLabs-Lab8-108.png)

7.  应用现已与应用商店应用**相关联**。 这是启用通知所必需的。

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>第20章-部署 UnityMRNotifHub 和 UnityDesktopNotifHub 应用程序

这一章可能更便于两人, 因为这样做会包括运行的应用程序、在计算机桌面上运行的应用程序, 以及沉浸式耳机中的其他应用程序。

沉浸式耳机应用正在等待接收对场景 (本地 Gameobject 的位置更改) 的更改, 并且桌面应用将更改其本地场景 (位置更改), 这将与 MR 应用共享。 首先部署 MR 应用, 然后部署桌面应用, 以便接收方可以开始侦听。

若要在本地计算机上部署**UnityMRNotifHub**应用, 请执行以下操作:

1.  在**Visual Studio 2017**中打开**UnityMRNotifHub**应用程序的解决方案文件。

2.  在**解决方案平台**中, 选择 " **X86, 本地计算机**"。

3.  在**解决方案配置**中, 选择 "**调试**"。

    ![设置项目配置](images/AzureLabs-Lab8-109.png)

4.  中转到 "**生成" 菜单**, 然后单击 "**部署解决方案**", 将应用程序旁加载到计算机上。

5.  应用现在应显示在已安装的应用列表中, 可以启动。

在本地计算机上部署**UnityDesktopNotifHub**应用程序:

1.  在**Visual Studio 2017**中打开**UnityDesktopNotifHub**应用程序的解决方案文件。

2.  在**解决方案平台**中, 选择 " **X86, 本地计算机**"。

3.  在**解决方案配置**中, 选择 "**调试**"。

    ![设置项目配置](images/AzureLabs-Lab8-110.png)

4.  中转到 "**生成" 菜单**, 然后单击 "**部署解决方案**", 将应用程序旁加载到计算机上。

5.  应用现在应显示在已安装的应用列表中, 可以启动。

6.  启动混合现实应用程序, 后跟桌面应用程序。

在这两个应用程序都运行的情况下, 将对象移动到桌面场景 (使用鼠标左键) 中。 这些位置更改将在本地进行、序列化并发送到 Function App 服务。 然后, Function App 服务将与通知中心一起更新表。 收到更新后, 通知中心会将更新的数据直接发送到所有已注册的应用程序 (在本例中为沉浸式头戴显示式应用程序), 该应用程序随后将反序列化传入的数据, 并将新位置数据应用于本地对象。在场景中移动它们。


## <a name="your-finished-your-azure-notification-hubs-application"></a>已完成 Azure 通知中心应用程序
 
恭喜, 你构建了一个利用 Azure 通知中心服务的混合现实应用, 并允许在应用之间进行通信。
 
![最终产品-结束](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

能否使用如何更改 Gameobject 的颜色并将该通知发送到其他应用程序查看场景？

### <a name="exercise-2"></a>练习2

能否将 Gameobject 移动到 MR 应用并在桌面应用中看到更新的场景？
