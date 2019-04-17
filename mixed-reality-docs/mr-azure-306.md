---
title: MR 和 Azure 306-流式传输视频
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 媒体服务。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api，媒体服务，流式处理视频中，360，令人着迷，vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591606"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR 和 Azure 306:流式处理视频

![最终产品-启动](images/AzureLabs-Lab6-00.png)
![最终产品-启动](images/AzureLabs-Lab6-01.png)

在本课程将了解如何连接到 Windows 混合现实 VR 体验，以允许流式处理在沉浸式耳机 360 度视频播放你的 Azure 媒体服务。 

**Azure 媒体服务**是一系列服务，可提供广播品质视频流式传输服务来访问在当今最受欢迎的移动设备上更广泛的受众。 有关详细信息，请访问[Azure 媒体服务页](https://azure.microsoft.com/services/media-services)。

已完成本课程，会创建一个混合的现实沉浸式头戴式应用程序，这将能够执行以下操作：

1. 检索来自的 360 度视频**Azure 存储**，通过**Azure 媒体服务**。

2. 显示在 Unity 场景中的检索到 360 度视频。

3. 具有两个不同的视频的两个场景之间进行导航。

在您的应用程序，它是取决于您关于如何将与您的设计集成结果。 本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。 它是作业以使用此课程以增强混合的现实应用程序中获取的知识。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 306:流式处理视频</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>系统必备

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。 你可以随意使用最新的软件，如中所列[安装工具一文](install-the-tools.md)，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.

我们建议以下硬件和软件本课程：

- 开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)
- 用于 Azure 的安装程序和数据检索的 Internet 访问权限
- 两个 mp4 格式的 360 度视频 (可以找到一些免版税的视频[在此下载页面](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>开始之前

1.  若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。
2.  设置和测试在混合现实沉浸式头戴式。

    > [!NOTE]
    > 你将**不**此课程需要运动控制器。 如果你需要支持沉浸式头戴式设置，请单击[k 了解如何设置 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>第 1 章-Azure 门户： 创建 Azure 存储帐户

若要使用**Azure 存储服务**，将需要创建和配置**存储帐户**在 Azure 门户中。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**存储帐户**在左侧菜单中。

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-02.png)

3.  上**存储帐户**选项卡上，单击**添加**。

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-03.png)

4.  在中**创建存储帐户**选项卡：

    1.  插入**名称**对于你的帐户，请注意此字段仅接受数字和小写字母。

    2.  有关**部署模型**选择**资源管理器**。

    3.  有关**帐户类型**，选择**存储 (常规用途 v1)**。

    4.  有关**性能**，选择**标准 *。**

    5.  有关**复制**选择**本地冗余存储 (LRS)**。

    6.  将保留**需要安全传输**作为**禁用**。

    7.  选择**订阅**。

    8.  选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。

    9.  确定**位置**为资源组 （如果要创建新的资源组）。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。

5.  你需要确认你已了解的条款和条件应用于此服务。

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-04.png)

6.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。

7.  创建服务实例后，在门户中将显示一条通知。

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-05.png)

8.  此时你不需要以按照该资源，只需转到下一章。

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>章 2-在 Azure 门户： 创建媒体服务

若要使用 Azure 媒体服务，你需要配置要成为可用于应用程序 （其中帐户持有者必须是管理员） 的服务的实例。

1.  在 Azure 门户中，单击**创建资源**在左上角，并搜索**媒体服务**按**Enter**。 当前所需的资源有一个粉红色的图标;单击此项，以显示新页面。

    ![在 Azure 门户](images/AzureLabs-Lab6-06.png)

2.  该新页面将提供的说明**媒体服务**。 在左下角此提示，请单击**创建**按钮，以创建与此服务的关联。

    ![在 Azure 门户](images/AzureLabs-Lab6-07.png)

3.  一旦你单击**创建**面板将显示您需要提供一些有关新的媒体服务的详细信息：

    1.  插入所需**帐户名**此服务实例。

    2.  选择**订阅**。

    3. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。 
    
    > 如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理 Azure 资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    4.  确定**位置**为资源组 （如果要创建新的资源组）。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。

    5.  有关**存储帐户**部分中，单击**请选择...** 部分，然后单击**存储帐户**在最后一章中创建。

    6.  您还需要确认你已了解的条款和条件应用于此服务。

    7.  单击“创建”。

        ![在 Azure 门户](images/AzureLabs-Lab6-08.png)

4.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。

5.  创建服务实例后，在门户中将显示一条通知。

    ![在 Azure 门户](images/AzureLabs-Lab6-09.png)

6.  单击通知以了解新的服务实例。

    ![在 Azure 门户](images/AzureLabs-Lab6-10.png)

7.  单击**转到资源**通知探索新的服务实例中的按钮。

8.  中新的媒体服务页上，在左侧面板中单击**资产**链接，这是有关中间的列表。

9.  在下一步页上的页上，在左上角中，单击**上传**。

    ![在 Azure 门户](images/AzureLabs-Lab6-11.png)

10. 单击**文件夹**图标来浏览你的文件，然后选择你想要流式传输的第一次 360 视频。 
    
    > 你可以按照这[链接以下载示例视频](https://vimeo.com/214401712)。

    ![在 Azure 门户](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> 长文件名可能会导致出现问题，与编码器： 因此若要确保视频是否有问题，请考虑缩短你的视频文件名称的长度。

11. 视频完成上传时，进度栏将变为绿色。

    ![在 Azure 门户](images/AzureLabs-Lab6-13.png)

12. 单击上面的文本 (**yourservicename-资产**) 以返回到**资产**页。

13. 您会注意到你的视频已成功上载。 单击它。

    ![在 Azure 门户](images/AzureLabs-Lab6-14.png)

14. 将重定向到的页面将显示有关你的视频的详细信息。 若要能够使用你需要进行编码，通过单击的视频**编码**页的顶部左侧的按钮。

    ![在 Azure 门户](images/AzureLabs-Lab6-15.png)

15. 一个新的面板将显示右侧，其中你将能够设置编码选项，为你的文件。 设置以下属性 （一些将已设置默认情况下）：

    1.  **媒体编码器名称*Media Encoder Standard***

    2.  **编码预设*内容自适应多比特率 MP4***

    3.  **作业名称*Video1.mp4 的 Media Encoder Standard 处理***

    4.  **输出媒体资产名称*Video1.mp4-Media Encoder Standard 编码***

        ![在 Azure 门户](images/AzureLabs-Lab6-16.png)

16. 单击“创建”按钮。

17. 你会注意到一个带条**添加的编码作业**、 单击该条形图和一个面板将显示为带有编码进度显示在它。

    ![在 Azure 门户](images/AzureLabs-Lab6-17.png)

    ![在 Azure 门户](images/AzureLabs-Lab6-18.png)

18. 等待作业完成。 完成后，随时关闭面板中的 X 右上角的该面板。

    ![在 Azure 门户](images/AzureLabs-Lab6-19.png)

    ![在 Azure 门户](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > 此操作，时间取决于你的视频的文件大小。 此过程可能需要很长时间。

19. 现在，已创建编码的视频版本，可以发布它，对其进行访问。 若要执行此操作，请单击蓝色的链接**资产**以返回到资产页上。

    ![在 Azure 门户](images/AzureLabs-Lab6-21.png)

20. 你将看到你的视频以及其他的 * * 资产类型 * 多比特率 MP4 * * *。

    ![在 Azure 门户](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > 您可能会注意到新的资产，以及初始视频，是*未知*，并且它是具有"0"字节**大小**，只需刷新您的窗口进行更新。

21. 单击此新资产。

    ![在 Azure 门户](images/AzureLabs-Lab6-23.png)

22. 你将看到一个类似于使用之前，只需这是不同的资产面板。 单击**发布**按钮位于页的顶部中央。

    ![在 Azure 门户](images/AzureLabs-Lab6-24.png)

23. 将提示您设置**定位器**，这是入口点，在你的资产中文件/秒。 对于你的方案设置以下属性：

    1.  **定位符类型** > **渐进式**。

    2.  **日期**并**时间**将设置，从当前日期，为将来的时间 （在本例中为 100 个年）。 将保留原样或将其更改为满足。

    > [!NOTE]
    > 有关定位符，并可以选择的详细信息，请访问[Azure 媒体服务文档](https://docs.microsoft.com/azure/media-services/media-services-concepts)。

24. 在该面板的底部，单击**添加**按钮。

    ![在 Azure 门户](images/AzureLabs-Lab6-25.png)

25. 你的视频现已发布，并可以通过使用其终结点进行流式处理。 进一步向下的页面**文件**部分。 这是视频的将不同的编码的版本的位置。 选择其中一个最高可能的解决方案 （在下图为 1920 x 960 文件），随后会显示右侧面板。 可以在其中找到**下载 URL**。 复制这**终结点**因为你将使用它在代码中更高版本。

    ![在 Azure 门户](images/AzureLabs-Lab6-26.png)    

    ![在 Azure 门户](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > 此外可以按**播放**按钮以播放视频，并对其进行测试。

26. 现在需要将在此实验室中将使用第二个视频上传。 按照上面的步骤，为第二个视频重复相同的过程。 确保复制第二个**终结点**还。 使用以下[链接以下载第二个视频](https://vimeo.com/214402865)。

27. 这两个视频已发布，已准备好移动到下一章。

## <a name="chapter-3---setting-up-the-unity-project"></a>第 3 章 — 设置 Unity 项目

以下是一组典型使用混合现实中，进行开发并在这种情况下，是合适的模板的其他项目。

1.  打开**Unity**然后单击**新建**。 

    ![在 Azure 门户](images/AzureLabs-Lab6-28.png)

2.  现在将需要提供 Unity 项目的名称，插入**MR\_360VideoStreaming。**。 请确保项目类型设置为**3D**。 将位置设置为适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![在 Azure 门户](images/AzureLabs-Lab6-29.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio。** 转到***编辑**首选项*** ，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![在 Azure 门户](images/AzureLabs-Lab6-30.png)

4.  接下来，请转到***文件**生成设置*** 并切换到平台**通用 Windows 平台**，通过单击**交换机平台**按钮。

5.  此外，请确保：

    1. **设备为目标**设置为**任一设备。**
    
    2.  **生成的类型**设置为**D3D。**

    3.  **SDK**设置为**最新安装。**

    4.  **Visual Studio 版本**设置为**最新安装。**

    5.  **生成并运行**设置为**本地计算机。**

    6.  有关设置的信息，请不要担心**场景**稍后再试，因为您将这些设置更高版本。

    7.  现在，应为默认值保留剩余的设置。

        ![设置 Unity 项目](images/AzureLabs-Lab6-31.png)

6.  在**生成设置**窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。 

7. 在此面板中，需要验证几个设置：

    1.  在中**其他设置**选项卡：

        1.  **脚本编写****运行时版本**应**稳定**（.NET 3.5 等效）。

        2. **脚本编写后端**应为 **.NET。**

        3. **API 兼容性级别**应为 **.NET 4.6。**

            ![设置 Unity 项目](images/AzureLabs-Lab6-32.png)

    2.  中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。

        ![设置 Unity 项目](images/AzureLabs-Lab6-33.png)

    3.  内**发布设置**选项卡上，在**功能**，检查：

        - **InternetClient**

            ![设置 Unity 项目](images/AzureLabs-Lab6-34.png)

8.  一旦进行这些更改，关闭**生成设置**窗口。

9.  保存项目 **文件** 保存项目 * *。



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>第 4 章-导入 InsideOutSphere Unity 程序包

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)，将其导入项目中，作为[ **自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从**第 5 章：**。 仍需要创建一个 Unity 项目。

为此课程需要先下载 Unity 资产包名为[ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)。

操作方法导入**unitypackage**:

1.  准备好 Unity 仪表板中，单击**资产**在屏幕顶部的菜单，然后单击**导入包 > 自定义包**。

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-35.png)

2.  使用文件选取器选择**InsideOutSphere.unitypackage**程序包，再单击**打开**。 将向你显示此资产的组件的列表。 通过单击确认导入**导入**。

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-36.png)

3.  完成导入后，你会注意到三个新文件夹**材料**，**模型**，并**预设**，已添加到你**资产**文件夹。 此类文件夹结构是典型的 Unity 项目。

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-37.png)

    1.  打开**模型**文件夹中，并且你将看到**InsideOutSphere**已导入模型。

    2.  内**材料**文件夹将为您**InsideOutSpheres**材料*lambert1*，以及名为材料*ButtonMaterial*，由 GazeButton，很快你将看到它。

    3.  **预设**文件夹包含**InsideOutSphere**其中同时包含预设**InsideOutSphere** *模型*和*GazeButton*。

    4.  **不不包含任何代码**，将按照本课程中编写的代码。


4.  内**层次结构**，选择**Main Camera**对象，并更新以下组件：

    1.  **转换**

        1.  位置 = **X**:0， **Y**:0， **Z**:0.

        2. 旋转 = **X**:0， **Y**:0， **Z**:0.

        3. 规模**X**:1， **Y**:1， **Z**:1.

    2.  **摄像头**

        1. **清除标志**:纯色。

        2.  **剪裁平面**:附近：0.1，得：6.

            ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-38.png)

5.  导航到**Prefab**文件夹，然后再拖动**InsideOutSphere**到 prefab**层次结构**面板。

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-39.png)

6.  展开**InsideOutSphere**对象内**层次结构**通过单击它旁边的小箭头。 你将看到**子**对象调用它下面**GazeButton**。 这将用于更改场景，因此视频。

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-40.png)

7.  在检查器窗口中单击**InsideOutSphere**的转换组件中，确保设置以下属性：

    |            |    转换的位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    转换的旋转   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     转换-横向     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-41.png)

8.  单击**GazeButton**子对象，并设置其**转换**，如下所示：

    |            |    转换的位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    转换的旋转   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     转换-横向     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>章节 5-创建 VideoController 类

**VideoController**类承载将使用从 Azure 媒体服务内容进行流式传输的两个视频终结点。

若要创建此类：

1.  在中右击**资产文件夹**，它位于**项目**面板中，然后单击**创建 > 文件夹**。 将文件夹命名为**脚本**。

    ![创建 VideoController 类](images/AzureLabs-Lab6-43.png)

    ![创建 VideoController 类](images/AzureLabs-Lab6-44.png)

2.  双击**脚本**文件夹将其打开。

3.  在文件夹中，右键单击，然后单击**创建 > C\#脚本**。 脚本命名为**VideoController**。

    ![创建 VideoController 类](images/AzureLabs-Lab6-45.png)

4.  双击新**VideoController**脚本以将其与打开**Visual Studio 2017。**

    ![创建 VideoController 类](images/AzureLabs-Lab6-46.png)

5.  更新代码文件顶部的命名空间，如下所示：

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  输入中的以下变量**VideoController**类，以及与**Awake()** 方法：

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  现在是时候从 Azure 媒体服务视频输入终结点：

    1.  到第一个*video1endpoint*变量。
    
    2.  到第二个*video2endpoint*变量。

    > [!WARNING]
    > 没有使用的已知的问题*https* Unity，并选择版本 2017.4.1f1 内。 如果视频 play 上提供了错误，请尝试改为使用 http。

8.  下一步， **start （)** 方法需要对其进行编辑。 每次用户通过查看对此按钮切换 （因此切换视频） 的场景时，将触发此方法。

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  遵循**start （)** 方法中，插入**PlayVideo()** *IEnumerator*方法，它将用于启动视频无缝 （以便看到没有出现断断续续的问题）。

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. 最后一种方法需要将此类是**ChangeScene()** 方法，它将用于场景之间交换。

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > **ChangeScene()** 方法使用方便 C\#功能调用*条件运算符*。 这允许要检查的条件，然后值基于返回的这项检查，在单个语句中的所有结果。 按照这[链接，了解有关条件运算符的详细信息](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)。

11. 返回到 Unity 之前，Visual Studio 中保存所做的更改。

12. 返回在 Unity 编辑器中，单击并拖动**VideoController**类 [通过] {.underline}**脚本**文件夹**Main Camera**对象中**层次结构**面板。

13. 单击**Main Camera**并查看**检查器面板**。 您将注意到，在新添加的脚本组件没有具有空值的字段。 这是引用字段，以在代码中的公共变量为目标。

14. 拖动**InsideOutSphere**对象从**层次结构面板**到**球体**槽，如下图中所示。

    ![创建 VideoController 类](images/AzureLabs-Lab6-47.png)
    ![创建 VideoController 类](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>章 6-创建的视线移动类

此类负责创建**Raycast** ，将 beprojected 转发从**Main Camera**，以检测用户查看的对象。 在这种情况下， **Raycast**需要确定如果用户寻求**GazeButton**对象在场景中，并触发一个行为。

若要创建此类：

1.  转到**脚本**之前创建的文件夹。

2.  在中右击**项目**面板中，**创建** C\#脚本 * *。 脚本命名为**注视**。

3.  双击新***注视***脚本以将其与打开**Visual Studio 2017。**

4.  确保以下命名空间顶部的脚本，并删除任何其他人：

    ```csharp
    using UnityEngine;
    ```

5.  然后添加以下变量内的**注视**类：

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  为代码**Awake()** 并**start （)** 方法现在需要添加。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  将以下代码中的添加**update （)** 方法投影 Raycast 和检测对目标的影响：

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  返回到 Unity 之前，Visual Studio 中保存所做的更改。

9.  单击并拖动**注视**从脚本文件夹中的 Main Camera 对象的类**层次结构**面板。

## <a name="chapter-7---setup-the-two-unity-scenes"></a>第 7 章 — 安装这两个 Unity 场景

此章节的目的是设置两个场景，每个托管的视频流。 以便您不需要安装它，同样，尽管将然后编辑新的场景中，将复制已创建的场景，以便*GazeButton*对象处于不同位置且具有不同的外观。 这是为了演示如何更改之间的场景。

1.  执行此操作通过转到**文件 > 将场景另存为...**.保存窗口将显示。 单击**新文件夹**按钮。

    ![第 7 章 — 安装这两个 Unity 场景](images/AzureLabs-Lab6-49.png)

2.  将文件夹命名为**场景**。

3.  **保存场景**窗口仍为打开状态。 打开新建**场景**文件夹。

4.  在中**文件的名称：** 文本字段中，键入**VideoScene1**，然后按**保存**。

5.  在 Unity 中，打开你**场景**文件夹，再左键单击你**VideoScene1**文件。 使用键盘，按**Ctrl + D**将复制该场景

    > [!TIP]
    > **重复**命令也可以通过导航到**编辑 > 重复**。

6.  Unity 将自动递增场景名称编号，但不管怎样，检查它以确保它匹配以前插入的代码。

    >  您应该**VideoScene1**并**VideoScene2**。

7.  与在两个场景，请转到**文件 > 生成设置**。 与**生成设置**窗口中打开，拖动到您的场景**生成中的场景**部分。

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > 您可以选择这两个从您的场景你**场景**通过持有锁的文件夹**Ctrl**按钮，然后单击鼠标左键每个场景，并最后拖动这两个。

8.  关闭**生成设置**窗口中，并双击**VideoScene2**。

9.  使用打开第二个场景中，单击**GazeButton**的子对象**InsideOutSphere**，并将其转换设置，如下所示：

    |            |    转换的位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    转换的旋转   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     转换-横向     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. 与**GazeButton**仍处于选中状态，查看在子**Inspector**并在**网格筛选器**。 单击小目标旁边**Mesh**引用字段：

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-51.png)

11. 一个**选择网格**弹出窗口随即出现。 双击**多维数据集**从列表中的网格**资产**。

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-52.png)

12. **网格筛选器**将更新和现在是**多维数据集**。 现在，单击**齿轮**旁边的图标**球体碰撞体**然后单击**删除组件**，若要删除此对象的碰撞体。

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-53.png)

13. 与**GazeButton**仍处于选中状态，单击**添加组件**底部的按钮**Inspector**。 在搜索字段中，键入**框**，并**盒状碰撞体**将作为一个选项，单击要添加**盒状碰撞体**到你**GazeButton**对象.

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-54.png)

14. **GazeButton**是部分更新，现在看起来不同，但是，您现在将创建一个新**材料**，以便它看上去完全不同，并更轻松地识别为不同的对象，比第一个场景中的对象。

15. 导航到您**材料**文件夹，在**项目面板**。 重复**ButtonMaterial**材料 (按**Ctrl** + **D**键盘或单击左键上**材料**，然后从**编辑**文件菜单选项，选择**重复**)。

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-55.png)
    ![章 7--设置两个 Unity 场景](images/AzureLabs-Lab6-56.png)

16. 选择新**ButtonMaterial**材料 (此处名为**ButtonMaterial 1**)，并在**检查器**，单击**Albedo**颜色窗口。 将显示一个弹出窗口，您可以在其中选择另一种颜色 （选择您喜欢的者为准），然后关闭弹出窗口。 材料将成为其自己的实例，并与其原始版本不同。

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-57.png)

17. 拖动新**材料**拖动到**GazeButton**子，以便轻松区分开来的第一个场景按钮现在完全更新其看起来。

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-58.png)

18. 现在你可以测试项目在编辑器中生成的 UWP 项目之前。

    -  按**播放**按钮**编辑器**和 wear 应用耳机。

        ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-59.png)

19. 看看这两个**GazeButton**对象第一个和第二个视频之间进行切换。

## <a name="chapter-8---build-the-uwp-solution"></a>第 8 章-生成 UWP 解决方案

后确保已在编辑器有任何错误，你就可以生成。

若要生成：

1.  通过单击保存当前场景**文件 > 保存**。

2.  选中复选框调用**Unity C\#项目**（这是重要因为这可以使您可以编辑类生成完成后）。

3.  转到**文件 > 生成设置**，单击**生成**。

4.  系统将提示您选择，您希望对 buildthe 解决方案的文件夹。

5.  创建**生成**文件夹并在该文件夹中创建另一个文件夹，与所选的适当的名称。

6.  单击新文件夹，然后单击**选择文件夹**，因此，若要选择该文件夹中，若要开始在该位置的生成。

    ![第 8 章-生成 UWP 解决方案](images/AzureLabs-Lab6-60.png)
    ![章 8-生成 UWP 解决方案](images/AzureLabs-Lab6-61.png)

7.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置。

## <a name="chapter-9---deploy-on-local-machine"></a>在本地计算机上部署一章 9-

完成生成后，**文件资源管理器**窗口将出现在生成的位置。 打开的文件夹名为并生成，然后双击该文件夹，以使用 Visual Studio 2017 中打开你的解决方案中的解决方案 (.sln) 文件。

一件事要做是将应用部署到您的计算机 (或*本地计算机*)。

若要将部署到本地计算机：

1.  在中**Visual Studio 2017**，打开刚刚创建的解决方案文件。

2.  在中**解决方案平台**，选择**x86，本地计算机**。

3.  在中**解决方案配置**选择**调试**。

    ![第 9 章-在本地计算机上部署](images/AzureLabs-Lab6-62.png)

4.  您现在需要将任何包还原到你的解决方案。 右键单击你**解决方案**，然后单击**还原解决方案的 NuGet 包...**

    > [!NOTE] 
    > 这是因为 Unity 生成的包需要将目标设定为使用你的本地计算机的引用。

5.  转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。 Visual Studio 将首先生成，然后部署应用程序。

6.  你的应用现在应出现在已安装的应用，准备好启动列表中。

    ![第 9 章-在本地计算机上部署](images/AzureLabs-Lab6-63.png)

当您运行混合现实应用程序后，你将在内**InsideOutSphere**应用中使用的模型。 将此球体将流式传输视频，提供的 360 度视图，传入的视频 （这此种类型的角度来看拍摄许可）。 不要过于惊讶如果视频需要几秒钟才能加载，您的应用程序受到您可用的 Internet 速度，如视频需要提取并随后下载，因此若要流式传输到您的应用程序。
准备就绪后，更改场景并打开第二个视频中，通过在红色球体观望 ！ 然后随时返回，在第二个场景中使用蓝色的多维数据集 ！

## <a name="your-finished-azure-media-service-application"></a>完成的 Azure 媒体服务应用程序
 
祝贺你，构建利用 Azure 媒体服务来将 360 视频流的混合的现实应用。

![实验结果](images/AzureLabs-Lab6-00.png)

![实验结果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Bonus 练习

**练习 1**

它是完全有可能只使用单个场景更改本教程中的视频。 试着你的应用程序并使它成为一个场景 ！ 可能是甚至另一个将视频添加到组合。

**练习 2**

尝试 Azure 和 Unity，并尝试实现应用程序以自动选择具有不同的文件大小，具体取决于 Internet 连接的强度的视频的功能。


