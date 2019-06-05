---
title: MR 和 Azure 307-机器学习
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 机器学习工作室。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 机器学习，机器学习，机器学习工作室，hololens，沉浸式、 vr
ms.openlocfilehash: 93263817df0fd809a09b32c1b34a636eab7026a1
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516039"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR 和 Azure 307:机器学习

![最终产品-启动](images/AzureLabs-Lab7-0.png)

在本课程中，您将学习如何将机器学习 (ML) 功能添加到使用 Azure 机器学习工作室的混合的现实应用程序。

*Azure 机器学习工作室*是 Microsoft 服务，开发人员提供了大量的机器学习算法，它可以帮助数据输入、 输出、 准备和可视化效果。 这些组件，就能开发预测分析试验、 循环访问它，并使用它来训练模型。 以下培训，可以使您的模型操作在 Azure 云中，因此，然后新数据评分。 有关详细信息，请访问[Azure 机器学习工作室页](https://azure.microsoft.com/en-au/services/machine-learning-studio/)。

已完成本课程，将具有混合的现实耳机沉浸式应用程序中，并将已了解如何执行以下操作：

1.  提供对销售数据的表*Azure 机器学习工作室*门户中，并设计一种算法来预测未来的销售额的热门项目。
2.  创建**Unity 项目**，其可接收和解释预测从机器学习服务的数据。
3.  中直观地显示断言而数据**Unity 项目**，通过架子上提供的最受欢迎的销售项。

在您的应用程序，它是取决于您关于如何将与您的设计集成结果。 本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。 它是作业以使用此课程以增强混合的现实应用程序中获取的知识。

此过程是不直接涉及任何其他混合现实实验室的自包含的教程。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 307:机器学习</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。 按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。 使用 HoloLens，您可能注意到某些 echo 语音捕获过程。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。 你可以随意使用最新的软件，如中所列[安装工具一文](install-the-tools.md)，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.

我们建议以下硬件和软件本课程：

- 开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式
- Internet 访问的 Azure 设置和机器学习数据检索

## <a name="before-you-start"></a>开始之前

若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。 

## <a name="chapter-1---azure-storage-account-setup"></a>第 1 章-设置 Azure 存储帐户

若要使用 Azure 翻译 API，你需要配置要成为可用于应用程序的服务的实例。
1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**存储帐户**在左侧菜单中。

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > 单词**新建**可能已替换**创建资源**，较新的门户网站中。

3.  上**存储帐户**选项卡上，单击**添加**。

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-2.png)

4.  在中**创建存储帐户**面板：

    1.  插入**名称**对于你的帐户，请注意此字段仅接受数字和小写字母。
    2.  有关**部署模型**选择**资源管理器**。
    3.  有关**帐户类型**，选择**存储 (常规用途 v1)** 。
    4.  有关**性能**，选择**标准**。
    5.  有关**复制**选择**读取-访问-异地冗余存储 (RA-GRS)** 。
    6.  将保留**需要安全传输**作为**禁用**。
    7.  选择**订阅**。
    4. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。
    
    5.  确定**位置**为资源组 （如果要创建新的资源组）。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。

5.  您还需要确认你已了解的条款和条件应用于此服务。

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-3.png)

6.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。

7.  创建服务实例后，在门户中将显示一条通知。

    ![Azure 存储帐户设置](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>第 2 章-Azure 机器学习工作室

若要使用*Azure 机器学习*，将需要配置要成为可用于应用程序的机器学习服务的实例。

1.  在 Azure 门户中，单击**新建**在左上角，并搜索**机器学习工作室工作区**，按**Enter**。

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-5.png)

2.  该新页面将提供的说明**机器学习工作室工作区**服务。 在左下角此提示，请单击**创建**按钮，以创建与此服务的关联。

3.  一旦你单击**创建**，将显示一个面板，需要提供一些有关您的新详细信息**机器学习工作室服务**:

    1.  插入所需**工作区名称**此服务实例。

    2.  选择**订阅**。

    3. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。 

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  确定**位置**为资源组 （如果要创建新的资源组）。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。 应使用在上一章中创建 Azure 存储使用的同一资源组。

    5.  有关**存储帐户**部分中，单击**使用现有**，然后单击下拉列表菜单，并在此处，单击**存储帐户**在最后一章中创建。

    6.  选择适当**工作区定价层**为你从下拉菜单。

    7.  内**Web 服务计划**部分中，单击**创建** **新的、** 然后在文本字段中插入它的名称。

    8.  从**Web 服务计划定价层**部分中，选择所选的价格层。 开发测试层称为**开发测试标准**应可供无需任何费用。

    9.  您还需要确认你已了解的条款和条件应用于此服务。

    10. 单击“创建”  。

        ![Azure 机器学习工作室](images/AzureLabs-Lab7-6.png)

4.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。

5.  创建服务实例后，在门户中将显示一条通知。

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-7.png)

6.  单击通知以了解新的服务实例。

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-8.png)

7.  单击**转到资源**通知探索新的服务实例中的按钮。

8.  在页中显示，在**其他链接**部分中，单击**启动机器学习工作室**，这会将你的浏览器定向**机器学习工作室**门户。

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-9.png)

9.  使用**Sign In**按钮，在右上角或中心，能够登录到你的机器学习工作室中。

    ![Azure 机器学习工作室](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>第 3 章-机器学习工作室：数据集设置

一个机器学习算法工作的方式是通过分析现有数据，然后尝试预测未来结果基于现有数据集。 这通常意味着，您有更好的算法预测未来的结果将是更现有数据。

示例表为提供给您，本课程中，调用[ProductsTableCSV 并且可以在此处下载](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。

> [!IMPORTANT]
> 上面的.zip 文件包含这两**ProductsTableCSV**并 **.unitypackage**，将会在需要[第 6 章](#chapter-6---importing-the-mlproducts-unity-package)。 尽管单独的 csv 文件中的相关章节，还提供此包。

此示例数据集包含在一 2017 年中的每一天每隔一小时的最畅销的对象记录。
        
![机器学习工作室：数据集设置](images/AzureLabs-Lab7-11.png)

例如，在 2017年的第 1 天，在下午 1 点 （13 小时），最畅销的项是佩珀中士。

此示例表包含 9998 条目。

1.  回到**机器学习工作室**门户中，并添加此表作为**数据集**在机器学习。 执行此操作通过单击 **+ 新建**中屏幕的左下角的按钮。

    ![机器学习工作室：数据集设置](images/AzureLabs-Lab7-12.png)

2.  部分将显示底部，并在左侧是导航面板中。 单击**数据集**，然后，右侧**从本地文件**。

    ![机器学习工作室：数据集设置](images/AzureLabs-Lab7-13.png)

3.  上传新**数据集**通过执行以下步骤：

    1. 将显示上传窗口中，您可以在其中**浏览**硬盘空间用于新的数据集。

        ![机器学习工作室：数据集设置](images/AzureLabs-Lab7-14.png)

    2.  一旦选择，并且在上传窗口后，将保持未选中的复选框。

    3.  在下面的文本字段中，输入**ProductsTableCSV.csv**作为数据集的名称 （尽管应会自动添加）。

    4.  使用下拉列表菜单**类型**，选择**标头 (.csv) 的一般 CSV 文件**。

    5.  按上传窗口右下角中的刻度线和你**数据集**将上传。

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>第 4 章-机器学习工作室：实验

您可以构建机器学习系统之前，需要构建试验，以验证在理论上有关你的数据。 结果，您将知道是否需要更多数据，或如果没有数据和可能结果之间的相关性。

若要开始创建试验：

1.  请再次单击 **+ 新建**按钮在左下角的页上，然后单击**实验** > **的空白实验**。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-15.png)

2.  一个新页面将显示具有空白实验：

3.  在左侧面板中展开 **保存的数据集* > *我的数据集** 拖到**ProductsTableCSV**到**试验画布**。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-16.png)

4.  在左侧面板中，展开**Data Transformation** > **样本和拆分**。 然后将拖**拆分数据**中的项到**试验画布**。 拆分数据项将拆分为两个部分的数据集。 一个部分将使用用于定型的机器学习算法。 第二部分将用于评估生成的算法的准确性。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-17.png)

5.  在右侧面板中 （在选择在画布上的项的拆分数据） 时，编辑**中第一个输出数据集的行部分**到**0.7**。 这会将数据拆分为两个部分，第一部分将为 70%的数据，并且第二个部分将在剩下的 30%。 若要确保数据随机拆分，请确保**随机拆分**复选框保持选中状态。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-18.png)

6.  将连接从的基**ProductsTableCSV**拆分数据项顶部到画布上的项。 这将连接项并发送**ProductsTableCSV**拆分数据输入到数据集输出 （数据）。  

    ![机器学习工作室：实验](images/AzureLabs-Lab7-19.png)

7.  在中**试验**左侧和右侧面板中，展开 **机器学习*> * 训练 * *。 拖动**训练模型**到试验画布中签出项。 画布应为相同的外观如下。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-20.png)

8.  从***靠下左对齐***的**拆分数据**项拖动到的连接**右上方**的**训练模型**项。 训练模型将使用从数据集中的第一个 70%拆分用于训练算法。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-21.png)

9.  选择**训练模型**项在画布上，并在**属性**面板中 （在浏览器窗口的右侧） 上单击**启动列选择器**按钮。

10. 在文本框中键入**产品**，然后按**Enter**，*产品*将设置为列定型预测。 接着，单击**刻度线**右下角以关闭选择对话框中。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-22.png)

11. 想要训练**多类逻辑回归**算法来预测最售出**产品**基于日期和日期的小时。 它不在本文档介绍了 Azure 机器学习工作室，不过，所提供的不同算法的详细信息的范围内你可了解详细信息从[机器学习算法备忘单](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. 从左侧的试验项目面板中，展开 * **机器学习* > *初始化模型*> * 分类 * * *，然后拖动**多类逻辑回归**到试验画布上的项。

13. 连接输出中，从底部**多类逻辑回归**，到的顶部左侧输入**训练模型**项。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-23.png)

14. 在左侧面板中的试验项目的列表中，展开 **机器学习*> * 分数 * *，并将其拖**评分模型**到画布上的项。

15. 连接输出中，从底部**训练模型**，到的顶部左侧输入**评分模型**。

16. 连接的底部右侧输出**拆分数据**，到右上角输入 **评分模型*项*。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-24.png)

17. 在列表中**实验**在左侧面板中的项展开 * **机器学习*> * 评估 * * *，然后拖动**评估模型**项拖动到画布上的。

18. 连接的输出**评分模型**到的顶部左侧输入**评估模型**。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-25.png)

19. 构建了第一个机器学习试验。 你现在可以保存并运行此试验。 在页面底部的菜单中，单击**保存**按钮以保存你的试验，然后单击**运行**开始试验。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-26.png)

20. 您可以看到**状态**的右上角画布中的实验。 稍等片刻实验来完成。

    > 如果你有大 （实际） 数据集很可能试验可能需要小时才能运行。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-27.png)

21. 右键单击**评估模型**项画布中并从上下文菜单悬停通过鼠标**评估结果**，然后选择**可视化**。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-28.png)

22. 将显示实际结果与这些预测的结果显示的评估结果。 这将使用原始数据集，用于评估该模型更早版本，拆分的 30%。 您可以看到的结果不太好了，理想情况下您最大的数字在每个行位于列中突出显示的项。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-29.png)

23. 关闭**结果**。

24. 若要使用你需要将它作为新训练的机器学习模型**Web 服务**。 若要执行此操作，单击**设置 Web 服务**菜单项底部的页上，在菜单中，然后单击**预测 Web 服务**。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-30.png)

25. 将创建一个新选项卡，并训练模型合并以创建新的 web 服务。 

26. 在页面底部的菜单中单击**保存**，然后单击**运行**。 您将看到在实验画布的右上角中更新的状态。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-31.png)

27. 运行完成后**部署 Web 服务**按钮将出现在页面底部。 已准备好部署 web 服务。 单击**部署 Web 服务**（经典） 在页面底部的菜单中。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-32.png)

    > 在浏览器可能会提示允许弹出窗口中，您应该**允许**中使用，但可能需要按**部署 Web 服务**同样，如果未显示部署页。 

28. 创建试验后你将重定向到**仪表板**页面，其中有你**API 密钥**显示。 暂时将其复制到记事本中，你将需要它在代码中非常快。 一旦你已记下 API 密钥，则单击**请求/响应**按钮**默认终结点**键下面的部分。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > 如果在此页中单击测试，你将能够输入的输入的数据，然后查看输出。 输入**天**并**小时**。 将保留**产品**条目保留为空。 然后单击**确认**按钮。 在页面底部的输出将显示的 JSON 表示正在选择每个产品的可能性。

29. 新的 web 页面将打开，显示的说明和所需的机器学习工作室的请求结构有关的一些示例。 复制**请求 URI**显示在此页上，到在记事本。

    ![机器学习工作室：实验](images/AzureLabs-Lab7-34.png)

现在已构建的机器学习系统，它提供最有可能的产品销售根据历史购买数据、 相关的天和年的某一天的时间。

若要调用 web 服务，将服务终结点和一个 API 密钥，该服务需要 URL。 单击**使用**选项卡上，从顶部菜单中。

**消耗**信息页将显示你将需要从代码中调用 web 服务的信息。 需要一份**主键**并**请求-响应**URL。 你将需要这些在下一章。

## <a name="chapter-5---setting-up-the-unity-project"></a>第 5 章-设置 Unity 项目

设置和测试在混合现实沉浸式头戴式。

> [!NOTE]
>  你将**不**此课程需要运动控制器。 如果你需要支持沉浸式头戴式设置，请单击[此处](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  打开**Unity**并创建一个名为的新的 Unity 项目**MR\_MachineLearning。** 请确保项目类型设置为**3D**。

2.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到 ***编辑* > *首选项*** ，然后在新窗口中，导航到 **外部工具** 。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

3.  接下来，请转到 ***文件* > *生成设置*** 并切换到平台**通用 Windows 平台**，通过单击***交换机平台***按钮。

4.  此外，请确保：

    1.  **设备为目标**设置为**任一设备**。

        > 对于 Microsoft HoloLens，设置**目标设备**到*HoloLens*。

    2.  **生成的类型**设置为**D3D**。

    3.  **SDK**设置为**最新安装**。

    4.  **Visual Studio 版本**设置为**最新安装**。

    5.  **生成并运行**设置为**本地计算机**。

    6.  有关设置的信息，请不要担心**场景**稍后再试，因为这些提供更高版本。

    7.  现在，应为默认值保留剩余的设置。

        ![设置 Unity 项目](images/AzureLabs-Lab7-35.png)

5.  在**生成设置**窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。 

6. 在此面板中，需要验证几个设置：

    1.  在中**其他设置**选项卡：

        1.  **脚本编写** **运行时版本**应**实验**（.NET 4.6 等效）

        2. **脚本编写后端**应为 ***.NET***

        3. **API 兼容性级别**应为 **.NET 4.6**

            ![设置 Unity 项目](images/AzureLabs-Lab7-36.png)

    2.  内**发布设置**选项卡上，在**功能**，检查：

        - **InternetClient**

            ![设置 Unity 项目](images/AzureLabs-Lab7-37.png)

    3.  中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加

        ![设置 Unity 项目](images/AzureLabs-Lab7-38.png)

    

6.  回到**生成设置** *Unity C#* 项目不再灰显; 选中它旁边的复选框。 

7.  关闭生成设置窗口。

8.  保存项目 (**文件 > 保存项目**)。

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>第 6 章-导入 MLProducts Unity 程序包

本课程中，你将需要下载名为的 Unity 资产包[ **Azure MR 307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)。 此包提供完整的场景，与中的所有对象的预构建，因此您可以集中精力获取其所有工作。 **ShelfKeeper**提供脚本，但只包含公共变量，用于场景安装程序结构。 你将需要执行所有其他部分。 

若要导入此包：

1.  准备好 Unity 仪表板中，单击**资产**在屏幕顶部的菜单，然后单击**导入包、 自定义包**。

    ![导入 MLProducts Unity 程序包](images/AzureLabs-Lab7-39.png)

2.  使用文件选取器选择**Azure MR 307.unitypackage**程序包，再单击**打开**。

3.  将向你显示此资产的组件的列表。 通过单击确认导入**导入**。

    ![导入 MLProducts Unity 程序包](images/AzureLabs-Lab7-40.png)

4.  完成导入后，你会注意到一些新文件夹刊登在您的 Unity**项目面板**。 这些都是三维模型和相应的材料的预制场景将处理的部分。 在本课程中，你将编写的大部分代码。

    ![导入 MLProducts Unity 程序包](images/AzureLabs-Lab7-41.png)

5.  内**项目面板**文件夹中，单击**场景**场景中单击文件夹并双击 (称为**MR_MachineLearningScene**)。 场景会打开 （请参阅下图所示）。 如果丢失了红色方块，只需单击**gizmos，请**顶部的按钮，角**游戏面板**。

    ![导入 MLProducts Unity 程序包](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>第 7 章-检查在 Unity 中的 Dll

若要利用 JSON 库 （用于序列化和反序列化） 的使用，Newtonsoft DLL 已实现与包中引入。 库应具有正确的配置，但最好检查 （特别是在遇到问题的代码不起作用）。 

为此，请执行以下操作：

-  左键单击插件文件夹内对 Newtonsoft 文件，并查看**检查器面板**。 请确保**Any 平台**勾选了。 转到**UWP 选项卡**并确保**不处理**勾选了。

    ![导入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>章 8-创建 ShelfKeeper 类

**ShelfKeeper**类承载方法，用于控制用户界面和生成在场景中的产品。

作为导入的包的一部分，你将拥有对此类，但不完整。 它现在是时候完成此类：

1.  双击**ShelfKeeper**编写脚本内**脚本**文件夹，将其与打开**Visual Studio 2017**。

2.  替换现有的脚本使用以下代码，用于设置日期和时间，并有一个方法来显示产品中的所有代码。

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

3.  请务必保存中所做的更改**Visual Studio**才会回到**Unity**。

4.  返回在 Unity 编辑器中，检查**ShelfKeeper**类看起来像如下：

    ![创建 ShelfKeeper 类](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > 如果您的脚本不具有引用目标 (即 *（文本网格） 的日期*)，只需将中的相应对象拖**层次结构面板**，相应的目标字段中。 请参阅下面有关说明，如果需要：
    > 
    > 1.  打开**衍生点**数组内**ShelfKeeper**组件脚本将按左键单击它。 子部分将显示名为**大小**，指示数组的大小。 类型**3**旁边的文本框**大小**然后按**Enter**，并将下创建三个插槽。
    > 2. 内**层次结构**展开**时间显示**（通过单击鼠标左键其旁边的箭头） 的对象。 接下来，单击***Main Camera***内**层次结构**，以便**Inspector**显示其信息。
    > 3. 选择**主照相机**中**层次结构面板**。 拖动**日期**并**时间**中的对象**层次结构面板**到**日期文本**并**时文本**在槽**Inspector**的**Main Camera**中**ShelfKeeper**组件。
    > 4. 拖动**Spawn 点**从**层次结构面板**(下方*货架*对象) 到**3** **元素**引用下的目标**衍生点**数组，如图所示。
    > 
    >     ![创建 ShelfKeeper 类](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>章 9-创建 ProductPrediction 类

要创建的下一步类是**ProductPrediction**类。

此类负责：

-   查询**机器学习服务**提供当前日期和时间的实例。

-   反 JSON 响应序列化使用的数据。

-   解释的数据，检索的三个推荐的产品。

-   调用**ShelfKeeper**类方法来显示场景中的数据。

若要创建此类：

1.  转到**脚本**文件夹，请在**项目面板**。

2.  在文件夹中，右键单击**创建** > **C\#脚本**。 调用脚本**ProductPrediction**。

3.  双击新**ProductPrediction**脚本以将其与打开**Visual Studio 2017**。

4.  如果**检测到文件修改**对话框弹出，单击 ***重载解决方案**。

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

6.  内部**ProductPrediction**类插入组成了多个嵌套类的以下两个对象。 这些类用于序列化和反序列化的机器学习服务的 JSON。

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

7.  （以便 JSON 相关的代码是在脚本中，下面的所有其他代码，并不碍事底部），然后添加以下变量前面的代码上方：

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
    > 确保插入**主键**并**请求响应终结点**，从机器学习门户，到这里的变量。 下图显示其中您所需的键和从终结点。 
    >  
    > ![机器学习工作室：实验](images/AzureLabs-Lab7-53-1.png)
    >
    > ![机器学习工作室：实验](images/AzureLabs-Lab7-53-2.png)

8.  此代码中的插入**start （)** 方法。 **Start （)** 类初始化时调用方法：

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

9.  下面是从 Windows 中收集的日期和时间，并将其转换为我们的机器学习实验可用于与表中存储的数据进行比较的格式的方法。

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

10. 你可以**删除** **update （)** 方法因为此类不会使用它。

11. 添加以下方法将当前日期和时间的机器学习终结点进行通信并接收 JSON 格式的响应。

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

            // Serialise the request
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

12. 添加以下方法，它负责反序列化 JSON 响应，以及通信到反序列化的结果**ShelfKeeper**类。 此结果将是预测销售在当前日期和时间最多的三个项的名称。 将下面的代码插入**ProductPrediction**类，在上一方法的下方。

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

13. 保存**Visual Studio**和回到**Unity**。

14. 拖动**ProductPrediction**类中的脚本**脚本**文件夹中，拖动到**Main Camera**对象。

15. 保存您的场景和项目**文件** >  ***保存场景* / *文件***  >  **保存项目**。

## <a name="chapter-10---build-the-uwp-solution"></a>第 10 章 — 生成 UWP 解决方案

就现在可以将项目生成为一个 UWP 的解决方案，以便它可以作为独立应用程序运行。

若要生成：

1.  通过单击保存当前场景**文件** **保存场景**。

2.  转到**文件** **生成设置**

3.  选中复选框调用**Unity C\#项目**（这是重要因为这可以使您可以编辑类生成完成后）。

4.  单击**添加打开场景**，

5.  单击“生成”  。

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-54.png)

6.  系统将提示您选择你想要生成解决方案的文件夹。

7.  创建**生成**文件夹并在该文件夹中创建另一个文件夹，与所选的适当的名称。

8.  单击新文件夹，然后单击**选择文件夹**，若要开始在该位置的生成。

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-55.png)

    ![构建 UWP 解决方案](images/AzureLabs-Lab7-56.png)

9.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。

## <a name="chapter-11---deploy-your-application"></a>章 11-部署应用程序

若要部署你的应用程序：

1.  导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。

2.  使用 Visual Studio 中打开，您需要还原 NuGet 包，这可以通过右键单击 MachineLearningLab_Build 解决方案，从解决方案资源管理器 （Visual Studio 的右侧找到），然后单击还原 NuGet 包：

    ![添加 NuGet 包](images/AzureLabs-Lab7-57.png)

3.  在解决方案配置中，选择**调试**。

4.  在解决方案平台中，选择**x86**，**本地计算机**。 

    > 对于 Microsoft HoloLens，您可能会发现它更轻松地将其设置为*远程计算机*，因此您不已接入到你的计算机。 不过，需要还执行以下操作：
    > - 知道**IP 地址**的你 HoloLens，在中找到*设置 > 网络和 Internet > Wi-fi > 高级选项*; IPv4 是应使用的地址。 
    > - 请确保**开发人员模式**是**上**; 中找到*设置 > 更新和安全 > 面向开发人员*。

    ![添加 NuGet 包](images/AzureLabs-Lab7-58.png)

5.  转到**生成菜单**，然后单击**部署解决方案**旁加载到您的 PC 应用程序。

6.  你的应用现在应出现在已安装的应用，准备好启动列表中。

运行混合现实应用程序时，你将看到您的 Unity 场景中设置工作台和从初始化时，设置在 Azure 中提取的数据。 数据将反序列化应用程序中，并将作为工作台上的三个模型，以可视方式提供当前日期和时间前的三个结果。


## <a name="your-finished-machine-learning-application"></a>完成的机器学习应用程序
 
祝贺你，构建利用 Azure 机器学习来进行数据预测并将其显示在您的场景的混合的现实应用。

![添加 NuGet 包](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>练习

**练习 1**

试着你的应用程序的排序顺序并根据此数据可能会有用也已上架显示的三个底部预测。

**练习 2**

使用**Azure 表**填充包含天气信息的新表并创建新的实验使用的数据。
