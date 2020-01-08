---
title: MR 和 Azure 307-机器学习
description: 完成本课程以了解如何在混合现实应用程序中实现 Azure 机器学习 Studio （经典）。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，机器学习，ml，机器学习工作室，hololens，沉浸，vr
ms.openlocfilehash: d1692faef825d0ee20be4cfc8d8333bcccd754e1
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75333822"
---
>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们**不会**在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR 和 Azure 307：机器学习

![最终产品-启动](images/AzureLabs-Lab7-0.png)

在本课程中，你将学习如何使用 Azure 机器学习 Studio （经典）将机器学习（ML）功能添加到混合现实应用程序。

*Azure 机器学习 Studio （经典）* 是一项 Microsoft 服务，它为开发人员提供了大量机器学习算法，可帮助进行数据输入、输出、准备和可视化。 然后，可以通过这些组件开发预测分析试验，对其进行循环访问，并使用它来训练模型。 完成培训后，可以在 Azure 云中操作模型，使其可以对新数据进行评分。 有关详细信息，请访问[Azure 机器学习 Studio （经典）页](https://azure.microsoft.com/services/machine-learning-studio/)。

完成本课程后，你将拥有一个混合现实沉浸式耳机式应用程序，并将了解如何执行以下操作：

1.  向*Azure 机器学习 Studio （经典）* 门户提供销售数据表，并设计一个算法来预测未来的热门项目的销售情况。
2.  创建可从 ML 服务接收和解释预测数据的**Unity 项目**。
3.  通过在货位上提供最常用的销售项，直观显示**Unity 项目**中的断言而数据。

在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。 本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。 您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。

本课程是一个自包含教程，并不直接涉及任何其他混合现实实验室。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 307：机器学习</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要侧重于 Windows Mixed Reality 沉浸（VR）耳机，但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。 在本课程中，你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。 使用 HoloLens 时，可能会在语音捕获过程中注意到某些回声。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程面向具有 Unity 和C#的基本经验的开发人员。 另外请注意，本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容（5月2018）。 您可以随意使用最新的软件（如[安装工具一文](install-the-tools.md)中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件：

- [与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发
- [Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- Azure 安装和 ML 数据检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。 

## <a name="chapter-1---azure-storage-account-setup"></a>第1章-Azure 存储帐户设置

若要使用 Azure Translator API，你将需要配置服务的实例，使其可用于你的应用程序。
1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。

2.  登录后，单击左侧菜单中的 "**存储帐户**"。

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > 在较新的门户中，可能已将 "**新建**" 一词替换为 "**创建资源**"。

3.  在 "**存储帐户**" 选项卡上，单击 "**添加**"。

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-2.png)

4.  在 "**创建存储帐户**" 面板中：

    1.  插入帐户的**名称**，请注意，此字段仅接受数字和小写字母。
    2.  对于**部署模型，选择 "** **资源管理器**"。
    3.  对于 "**帐户类型**"，请选择 "**存储（常规用途 v1）** "。
    4.  对于“性能”，请选择“标准”。
    5.  对于**复制**，请选择 "**读取-访问-异地冗余存储（GRS）** "。
    6.  使**安全传输**保持**禁用状态**。
    7.  选择一个订阅。
    4. 选择一个**资源组**，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务（例如这些实验室）保存在一个公共资源组中。

        > 若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。
    
    5.  确定资源组的**位置**（如果要创建新的资源组）。 此位置理想情况下会在应用程序运行所在的区域中。 某些 Azure 资产仅在特定区域提供。

5.  还需要确认是否已了解应用于此服务的条款和条件。

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-3.png)

6.  单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。

7.  创建服务实例后，门户中将显示一个通知。

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio--classic"></a>第2章-Azure 机器学习 Studio （经典）

若要使用*Azure 机器学习*，需要配置机器学习服务的实例，使其可用于你的应用程序。

1.  在 Azure 门户中，单击左上角的 "**新建**"，然后搜索**机器学习 Studio 工作区**，按**enter**。

    ![Azure 机器学习 Studio （经典）](images/AzureLabs-Lab7-5.png)

2.  新页将提供**机器学习 Studio 工作区**服务的说明。 在此提示符的左下方，单击 "**创建**" 按钮以创建与此服务的关联。

3.  单击 "**创建**" 后，将显示一个面板，需要在其中提供有关新**机器学习 Studio 服务**的一些详细信息：

    1.  为此服务实例插入所需的**工作区名称**。

    2.  选择一个订阅。

    3. 选择一个**资源组**，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务（例如这些实验室）保存在一个公共资源组中。 

        > 若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  确定资源组的**位置**（如果要创建新的资源组）。 此位置理想情况下会在应用程序运行所在的区域中。 某些 Azure 资产仅在特定区域提供。 应使用在上一章中用于创建 Azure 存储的同一资源组。

    5.  对于 "**存储帐户**" 部分，单击 "**使用现有**项"，然后单击下拉菜单，然后从那里单击你在上一章中创建的**存储帐户**。

    6.  从下拉菜单中选择合适的**工作区定价层**。

    7.  在 " **Web 服务计划**" 部分中 **，单击 "** **新建"，** 然后在 "文本" 字段中插入它的名称。

    8.  从 " **Web 服务计划定价层**" 部分，选择所选的价格层。 名为**开发测试 Standard**的开发测试层应免费提供给您。

    9.  还需要确认是否已了解应用于此服务的条款和条件。

    10. 单击**创建**。

        ![Azure 机器学习 Studio （经典）](images/AzureLabs-Lab7-6.png)

4.  单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。

5.  创建服务实例后，门户中将显示一个通知。

    ![Azure 机器学习 Studio （经典）](images/AzureLabs-Lab7-7.png)

6.  单击通知以浏览新服务实例。

    ![Azure 机器学习 Studio （经典）](images/AzureLabs-Lab7-8.png)

7.  单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。

8.  在显示的页面的 "**其他链接**" 部分下，单击 "**启动机器学习 Studio**"，这会将浏览器定向到**机器学习 studio**门户。

    ![Azure 机器学习 Studio （经典）](images/AzureLabs-Lab7-9.png)

9.  使用右上角的 "**登录**" 按钮登录到机器学习 Studio （经典）。

    ![Azure 机器学习 Studio （经典）](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-classic-dataset-setup"></a>第3章-机器学习 Studio （经典）：数据集设置

机器学习算法的一种方法是分析现有数据，然后根据现有数据集尝试预测未来结果。 这通常意味着您拥有的现有数据越多，算法的预测未来结果就越好。

本课程提供了一个示例表，此课程称为 ProductsTableCSV，[可在此处下载](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。

> [!IMPORTANT]
> 上述 .zip 文件包含**ProductsTableCSV**和**unitypackage**，这将在[第6章](#chapter-6---importing-the-mlproducts-unity-package)中需要。 这一章中也提供了此包，但它与 csv 文件分离。

此示例数据集包含2017年每一天的每个小时的最佳销售对象的记录。
        
![机器学习 Studio （经典）：数据集设置](images/AzureLabs-Lab7-11.png)

例如，在2017的第1天（每小时13点），最佳销售物品是 salt 和辣椒。

此示例表包含9998个条目。

1.  返回到**机器学习 Studio （经典）** 门户，并将此表添加为 ML 的**数据集**。 单击屏幕左下角的 " **+ 新建**" 按钮即可执行此操作。

    ![机器学习 Studio （经典）：数据集设置](images/AzureLabs-Lab7-12.png)

2.  部分将从底部开始，并在左侧有导航面板。 单击 "数据集"，然后依次单击 "**数据集**"、"**本地文件**"。

    ![机器学习 Studio （经典）：数据集设置](images/AzureLabs-Lab7-13.png)

3.  按照以下步骤上传新的**数据集**：

    1. 此时将显示 "上传" 窗口，您可以在其中**浏览**硬盘驱动器以查找新的数据集。

        ![机器学习 Studio （经典）：数据集设置](images/AzureLabs-Lab7-14.png)

    2.  选择后，返回到 "上传" 窗口，将复选框保留为 "未选中"。

    3.  在下面的文本字段中，输入**ProductsTableCSV**作为数据集的名称（但应自动添加）。

    4.  使用**类型**的下拉菜单，选择**带有标头的通用 CSV 文件（.csv）** 。

    5.  按上传窗口右下角的勾选标记，将上传**数据集**。

## <a name="chapter-4---the-machine-learning-studio-classic-the-experiment"></a>第4章-机器学习 Studio （经典）：试验

在构建机器学习系统之前，你需要构建一个试验来验证你的数据的理论。 在结果中，你将知道是否需要更多数据，或者数据与可能的结果之间是否没有关联。

开始创建试验：

1.  再次单击页面左下角的 " **+ 新建**" 按钮，然后单击**试验** > **空白实验**。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-15.png)

2.  将显示一个新页面，其中包含一个空白实验：

3.  在左侧面板中，展开 "**保存的数据集**" >  **"我的数据集**"，并将**ProductsTableCSV**拖到**试验画布**上。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-16.png)

4.  在左侧面板中，展开 "**数据转换**" > "**示例" 和 "拆分**"。 然后将**拆分**数据项拖到**试验画布**中。 拆分数据项会将数据集拆分为两个部分。 用于训练机器学习算法的部分。 第二部分将用于计算生成的算法的准确性。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-17.png)

5.  在右侧面板中（选择了画布上的 Split 数据项时），将**第一个输出数据集中的行的小数部分**编辑为**0.7**。 这会将数据拆分为两个部分，第一部分将为70% 的数据，第二个部分将是剩余的30%。 若要确保数据随机拆分，请确保**随机拆分**复选框保持选中状态。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-18.png)

6.  将连接从画布上**ProductsTableCSV**项的基拖到拆分数据项的顶部。 这会将这些项连接起来，并将**ProductsTableCSV**数据集输出（数据）发送到拆分数据输入。  

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-19.png)

7.  在左侧的**试验**面板中，展开 "**机器学习** > **训练**"。 将**训练模型**项拖出到试验画布。 画布应与下面的外观相同。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-20.png)

8.  从 "**拆分数据项**" 的左下***方***将连接拖到 "**定型模型**" 项的**右上方**。 定型模型将使用数据集中的第一个70% 拆分来训练该算法。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-21.png)

9.  在画布上选择 "**训练模型**" 项，然后在 "**属性**" 面板（位于浏览器窗口的右侧）中，单击 "**启动列选择器**" 按钮。

10. 在文本框中键入**product** ，然后按**enter**，*产品*将设置为用于定型预测的列。 在此之后，单击右下角的**勾选标记**以关闭选择对话框。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-22.png)

11. 你将定型**多类逻辑回归**算法，根据一天中的小时和日期预测最销售的**产品**。 此文档超出了本文档的讨论范围，可以说明 Azure 机器学习 studio 提供的不同算法的详细信息，但你可以从[机器学习算法](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)备忘单中了解详细信息

12. 在左侧的 "试验项" 面板中，展开 "**机器学习** > **初始化模型** > **分类**，然后将"**多类逻辑回归**"项拖到试验画布上。

13. 将**多类逻辑回归**的底部的输出连接到**定型模型**项的左上方输入。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-23.png)

14. 在左侧面板中的实验项列表中，展开 "**机器学习** > **评分**"，然后将 "**评分模型**" 项拖到画布上。

15. 将来自**定型模型**底部的输出连接到**评分模型**的左上方输入。

16. 将从**拆分数据**向右下的输出连接到**评分模型**项的右上方输入。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-24.png)

17. 在左侧面板中的**实验**项列表中，展开 "**机器学习** > "**评估**"，然后将"**评估模型**"项拖到画布上。

18. 将**评分模型**的输出连接到**评估模型**的左上方输入。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-25.png)

19. 您已经生成了第一个机器学习试验。 你现在可以保存并运行试验。 在页面底部的菜单中，单击 "**保存**" 按钮以保存实验，并单击 "**运行**" 开始试验。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-26.png)

20. 可以在画布的右上方查看试验**状态**。 请稍等片刻，等待试验结束。

    > 如果有大型（现实）数据集，可能会有可能需要数小时才能运行试验。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-27.png)

21. 右键单击画布中的 "**评估模型**" 项，然后从上下文菜单中将鼠标悬停在 "**评估结果**" 上，然后选择 "**可视化**"。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-28.png)

22. 将显示计算结果，显示预测结果与实际结果。 这将使用之前拆分的原始数据集的30% 来计算模型。 您可以看到，结果并不是很好，理想情况下，每行中的最大数目是列中突出显示的项。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-29.png)

23. 关闭**结果**。

24. 若要使用新训练的机器学习模型，你需要将其公开为**Web 服务**。 为此，请单击页面底部菜单中的 "**设置 Web 服务**" 菜单项，然后单击 "**预测 Web 服务**"。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-30.png)

25. 将创建一个新选项卡，并合并定型模型以创建新的 web 服务。 

26. 在页面底部的菜单中，单击 "**保存**"，然后单击 "**运行**"。 你将在实验画布的右上角显示状态 "已更新"。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-31.png)

27. 运行完毕后，将在页面底部显示 "**部署 Web 服务**" 按钮。 你已准备好部署 web 服务。 单击页面底部菜单中的 "**部署 Web 服务**（经典）"。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-32.png)

    > 你的浏览器可能会提示你允许弹出窗口（你应该**允许**这样做），尽管你可能需要再次按 "**部署 Web 服务**" （如果未显示 "部署" 页）。 

28. 一旦创建了实验，你会被重定向到 "**仪表板**" 页面，你将在其中显示**API 密钥**。 将其复制到记事本中，你将很快在代码中需要它。 记下 API 密钥后，请单击密钥下面的 "**默认终结点**" 部分中的 "**请求/响应**" 按钮。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > 如果单击此页中的 "测试"，将能够输入输入数据并查看输出。 输入**日期** **和时间**。 将**产品**条目留空。 然后单击 "**确认**" 按钮。 页面底部的输出将显示 JSON，表示每个产品选择的可能性。

29. 随即打开一个新网页，其中显示了有关机器学习 Studio （经典）所需的请求结构的说明和示例。 将此页中显示的**请求 URI**复制到记事本中。

    ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-34.png)

现在，你已构建了一个机器学习系统，它提供了最有可能使用的产品，这些产品是基于历史购买数据销售的，并与一天中的时间和日期相关联。

若要调用 web 服务，你将需要服务终结点的 URL 和服务的 API 密钥。 单击顶部菜单中的 "**使用**" 选项卡。

"**消耗**信息" 页将显示从代码中调用 web 服务所需的信息。 获取**主密钥**和**请求-响应**URL 的副本。 下一章将需要这些项。

## <a name="chapter-5---setting-up-the-unity-project"></a>第5章-设置 Unity 项目

设置并测试混合现实沉浸式耳机。

> [!NOTE]
>  本课程**不**需要移动控制器。 如果需要支持设置沉浸式耳机，请单击[此处](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  打开**unity**并创建名为**MR\_Default-machinelearning-southcentralus**的新 Unity 项目。 请确保 "项目类型" 设置为 " **3d**"。

2.  当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "**编辑** > **首选项**"，然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

3.  接下来，通过单击 "***切换平台***" 按钮转到 "**文件** > **生成设置**"，并将平台切换到**通用 Windows 平台**。

4.  另外，请确保：

    1.  "**目标设备**" 设置为 "**任何设备**"。

        > 对于 Microsoft HoloLens，将 "**目标设备**" 设置为 " *hololens*"。

    2.  **生成类型**设置为**D3D**。

    3.  **SDK**设置为 "**最新安装**"。

    4.  **Visual Studio 版本**设置为 "**最新安装**"。

    5.  "**生成并运行**" 设置为 "**本地计算机**"。

    6.  请不要担心现在设置**场景**，因为稍后会提供这些信息。

    7.  其余设置应保留为默认值。

        ![设置 Unity 项目](images/AzureLabs-Lab7-35.png)

5.  在 "**生成设置**" 窗口中，单击 "**播放机设置**" 按钮，这会在**检查器**所在的空间中打开相关面板。 

6. 在此面板中，需要验证几项设置：

    1.  在 "**其他设置**" 选项卡中：

        1.  **脚本** **运行时版本**应为**试验**性的（.net 4.6 等效项）

        2. **脚本编写后端**应为 ***.net***

        3. **API 兼容级别**应为 **.net 4.6**

            ![设置 Unity 项目](images/AzureLabs-Lab7-36.png)

    2.  在 "**发布设置**" 选项卡的 "**功能**" 下，检查：

        - **InternetClient**

            ![设置 Unity 项目](images/AzureLabs-Lab7-37.png)

    3.  在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK**

        ![设置 Unity 项目](images/AzureLabs-Lab7-38.png)

    

6.  "返回**生成设置** *" C# Unity*项目不再灰显;勾选此的旁边的复选框。 

7.  关闭 "生成设置" 窗口。

8.  保存项目（**文件 > 保存项目**）。

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>第6章-导入 MLProducts Unity 包

在本课程中，你将需要下载名为[**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)的 Unity 资产包。 此包随场景一起提供，其中的所有对象都是预先构建的，因此你可以专注于使其正常工作。 尽管仅出于场景设置结构的目的保留公共变量，但提供了**ShelfKeeper**脚本。 您将需要执行所有其他部分。 

导入此包：

1.  在您前面的 "Unity" 面板中，单击屏幕顶部菜单中的 "**资产**"，然后单击 "**导入包、自定义包**"。

    ![导入 MLProducts Unity 包](images/AzureLabs-Lab7-39.png)

2.  使用文件选取器选择**unitypackage**包，并单击 "**打开**"。

3.  此时将显示此资产的组件列表。 单击 "**导入**" 确认导入。

    ![导入 MLProducts Unity 包](images/AzureLabs-Lab7-40.png)

4.  导入完成后，你会注意到某些新文件夹已显示在 Unity**项目面板**中。 这些是三维模型和各自的材料，它们是您将处理的预先准备的场景的组成部分。 在本课程中，您将编写大部分代码。

    ![导入 MLProducts Unity 包](images/AzureLabs-Lab7-41.png)

5.  在 "**项目面板**" 文件夹中，单击 "**场景**" 文件夹，然后双击（称为**MR_MachineLearningScene**）中的场景。 屏幕将打开（请参阅下图）。 如果缺少红色菱形，只需单击**游戏面板**右上角的 " **Gizmos** " 按钮。

    ![导入 MLProducts Unity 包](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>第7章-检查 Unity 中的 Dll

若要利用 JSON 库（用于序列化和反序列化），已使用中的包实现了 Newtonsoft.json DLL。 库应具有正确的配置，尽管需要检查它（特别是在代码不工作时遇到的问题）。 

执行此操作的步骤：

-  左键单击 "插件" 文件夹中的 Newtonsoft.json 文件，并查看 "**检查器" 面板**。 请确保勾选**任何平台**。 请在 " **UWP" 选项卡上**，确保**不勾选进程**。

    ![导入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>第8章-创建 ShelfKeeper 类

**ShelfKeeper**类承载控制在场景中生成的 UI 和产品的方法。

作为导入包的一部分，你将获得此类，但它是不完整的。 现在可以完成该类：

1.  双击**Scripts**文件夹中的**ShelfKeeper**脚本，通过**Visual Studio 2017**将其打开。

2.  将脚本中的所有现有代码替换为以下代码，这会设置时间和日期，并具有显示产品的方法。

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  在返回到**Unity**之前，请务必保存**Visual Studio**中所做的更改。

4.  返回 Unity 编辑器，检查**ShelfKeeper**类是否如下所示：

    ![创建 ShelfKeeper 类](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > 如果脚本没有引用目标（即*日期（文本网格）* ），只需将相应的对象从 "**层次结构" 面板**拖动到目标字段。 如有必要，请参阅下面的说明：
    > 
    > 1.  在**ShelfKeeper**组件脚本中，通过左键单击**生成点**数组，将其打开。 子节将出现 "**大小**"，指示数组的大小。 在 "**大小**" 旁边的文本框中键入**3** ，按**enter**，然后将创建三个槽。
    > 2. 在**层次结构**中，展开 "**时间显示**" 对象（通过左键单击其旁边的箭头）。 接下来，单击**层次结构**中的***主摄像机***，使**检查器**显示其信息。
    > 3. 选择 "**层次结构" 面板**中的**主相机**。 将 "**日期**和**时间**" 对象从 **"层次结构" 面板**拖动到 " **ShelfKeeper** " 组件中的**主摄像机** **检查器**内的**日期文本**和**时间文本**槽。
    > 4. 将 "**层次结构" 面板**（位于*货位*对象下）中的**生成点**拖到**生成点**数组下的**3**个**元素**引用目标，如图中所示。
    > 
    >     ![创建 ShelfKeeper 类](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>第9章-创建 ProductPrediction 类

要创建的下一个类是**ProductPrediction**类。

此类负责：

-   查询**机器学习服务**实例，同时提供当前日期和时间。

-   将 JSON 响应反序列化为可用的数据。

-   解释数据，检索3个推荐的产品。

-   调用**ShelfKeeper**类方法以在场景中显示数据。

若要创建此类：

1.  在 "**项目" 面板**中，打开 "**脚本**" 文件夹。

2.  右键单击文件夹内部，**创建** >  **C#脚本**。 调用脚本**ProductPrediction**。

3.  双击新的**ProductPrediction**脚本以通过**Visual Studio 2017**将其打开。

4.  如果弹出了**文件修改**对话框，请单击 "**重新加载解决方案**"。

5.  将以下命名空间添加到 ProductPrediction 类的顶部：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  在**ProductPrediction**类中，插入以下两个由若干嵌套类组成的对象。 这些类用于序列化和反序列化机器学习服务的 JSON。

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  然后，将以下变量添加到前面的代码上（以便 JSON 相关的代码位于脚本底部，在所有其他代码的下面，并在所有其他代码之外）：

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > 请确保将机器学习门户中的**主密钥**和**请求-响应终结点**插入到此处的变量中。 以下图像显示了从何处获取密钥和终结点的位置。 
    >  
    > ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-53-1.png)
    >
    > ![机器学习 Studio （经典）：试验](images/AzureLabs-Lab7-53-2.png)

8.  将此代码插入**Start （）** 方法内。 当类初始化时，将调用**Start （）** 方法：

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  下面是收集 Windows 中的日期和时间，并将其转换为机器学习试验可用于与表中存储的数据进行比较的格式的方法。

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. 您可以**删除** **Update （）** 方法，因为此类将不会使用它。

11. 添加以下方法，该方法将当前日期和时间传递到机器学习终结点，并接收 JSON 格式的响应。

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. 添加以下方法，该方法负责反序列化 JSON 响应，并将反序列化的结果传递给**ShelfKeeper**类。 此结果将是预测在当前日期和时间销售的三个项目的名称。 将下面的代码插入到前面方法下面的**ProductPrediction**类中。

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. 保存**Visual Studio**并返回到**Unity**。

14. 将**ProductPrediction**类脚本从**脚本**文件夹拖到**主相机**对象上。

15. 保存场景和项目**文件**， > **保存场景/文件** > **保存项目**。

## <a name="chapter-10---build-the-uwp-solution"></a>第10章-构建 UWP 解决方案

现在可以将项目构建为 UWP 解决方案，使其可以作为独立的应用程序运行。

若要生成：

1.  单击 "**文件**" > **保存场景**，保存当前场景。

2.  中转到**File** > **生成设置**

3.  选中 "名为**Unity C#项目**的" 框（这一点很重要，因为它将允许您在生成完成后编辑类）。

4.  单击 "**添加打开的场景**"，

5.  单击**生成**。

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-54.png)

6.  系统将提示您选择要在其中生成解决方案的文件夹。

7.  创建一个**生成**文件夹，在该文件夹中创建另一个文件夹，其中包含所选的适当名称。

8.  单击新文件夹，然后单击 "**选择文件夹**"，在该位置开始生成。

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-55.png)

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-56.png)

9.  Unity 完成生成（可能需要一些时间）后，它会在生成的位置打开 "**文件资源管理器**" 窗口（检查任务栏，因为它可能不会始终出现在窗口之上，但会通知你添加了一个新窗口）。

## <a name="chapter-11---deploy-your-application"></a>第11章-部署应用程序

若要部署应用程序：

1.  导航到新的 Unity 生成（**应用**文件夹），并在**Visual Studio**中打开解决方案文件。

2.  在 Visual Studio 打开的情况下，你需要还原 NuGet 包，可以通过右键单击 MachineLearningLab_Build 解决方案来完成此操作，方法是在解决方案资源管理器（位于 Visual Studio 的右侧），然后单击 "还原 NuGet 包"：

    ![添加 NuGet 包](images/AzureLabs-Lab7-57.png)

3.  在解决方案配置中，选择 "**调试**"。

4.  在解决方案平台中，选择 " **x86**，**本地计算机**"。 

    > 对于 Microsoft HoloLens，你可能会发现将其设置为*远程计算机*会更容易，因此你不会受限到计算机上。 不过，还需要执行以下操作：
    > - 知道您的 HoloLens 的**IP 地址**，可在 "*设置" > 网络 & Internet > > "高级选项*" 中找到;IPv4 是应使用的地址。 
    > - 确保**开发人员模式**已**打开**;在 "设置" 中找到 *> 更新开发人员 & 安全 >* 。

    ![添加 NuGet 包](images/AzureLabs-Lab7-58.png)

5.  中转到 "**生成" 菜单**，然后单击 "**部署解决方案**"，将应用程序旁加载到你的电脑。

6.  应用现在应显示在已安装的应用列表中，可以启动。

运行混合现实应用程序时，你将看到在 Unity 场景中设置的工作台，并从初始化中获取在 Azure 中设置的数据。 数据将在应用程序中进行反序列化，当前日期和时间的三个最顶部结果将以直观的形式提供，作为工作台上的三个模型。


## <a name="your-finished-machine-learning-application"></a>已完成的机器学习应用程序
 
恭喜，你构建了一个混合现实应用，它利用 Azure 机器学习来进行数据预测，并将其显示在你的场景中。

![添加 NuGet 包](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>练习

**练习1**

试验您的应用程序的排序顺序并使这三个最低预测出现在货位上，因为此数据可能也很有用。

**练习2**

使用**Azure 表**时，将使用天气信息填充新表，并使用数据创建新试验。
