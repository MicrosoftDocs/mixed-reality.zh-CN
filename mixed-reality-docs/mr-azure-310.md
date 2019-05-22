---
title: MR 和 Azure 310-对象检测
description: 完成此课程以了解如何定型机器学习模型，以及如何将训练的模型来识别类似对象和混合的现实应用程序中从现实世界中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 中，自定义视觉对象检测，混合现实、 学院、 unity、 教程、 api、 hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590124"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

# <a name="mr-and-azure-310-object-detection"></a>Mr 和 Azure 310:对象检测

在本课程中，您将学习如何识别自定义视觉对象的内容和其空间位置中提供的映像，使用 Azure 自定义影像混合的现实应用程序中的"对象检测"功能。

此服务将允许你定型机器学习模型，使用对象映像。 随后将使用经过训练的模型来识别类似对象和大约在现实生活中，其位置提供的 Microsoft HoloLens 相机捕捉或照相机连接到 PC 的沉浸式 (VR) 耳机。

![课程结果](images/AzureLabs-Lab310-00.png)

**Azure 自定义影像、 对象检测**是 Microsoft 服务，允许开发人员可以构建自定义图像分类器。 这些分类器可以随后可用于新的映像来检测该新映像中的对象，从而**框边界**于映像自身之中。 该服务提供一个简单、 易于使用、 在线门户，可简化此过程。 有关详细信息，请访问以下链接：

* [Azure 自定义视觉页](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [限制和配额](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

完成本课程时，之后您将拥有一个混合的现实应用程序，将能够执行以下操作：

1. 用户将能够*注视*在它们具有经过培训的使用 Azure 自定义影像服务，对象检测的对象。 
2. 用户将使用*点击*手势来捕获它们正在查看的内容的映像。
3. 应用程序将映像发送到 Azure 自定义影像服务。
4. 将会显示为世界空间文本识别结果的服务的答复。 这将通过利用 Microsoft HoloLens 的空间，作为跟踪的了解已识别的对象，世界位置，然后使用一种方法来实现*标记*与什么检测到在图中，为相关联提供的标签文本。

课程还将介绍手动上传的映像，创建标记，以及培训服务，可识别不同对象 （在提供的示例中，一杯），通过设置*边界框*提交的映像中。 

> [!IMPORTANT]
> 以下的创建和使用应用，开发人员应导航回 Azure 自定义影像服务，并识别的预测进行了服务，并确定是否是正确还是不 (通过标记任何服务丢失，和调整*边界框*)。 该服务可以然后重新训练，这将提高它识别现实世界对象的可能性。

本课程将介绍如何将结果从 Azure 自定义影像服务，对象检测到基于 Unity 的示例应用程序。 它将取决于您要应用于您可能要构建一个自定义应用程序的这些概念。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 310:对象检测</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>系统必备

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。 你可以随意使用最新的软件，如中所列[安装的工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。

我们建议以下硬件和软件本课程：

- 开发计算机
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [最新的 Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- 一个[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)启用开发人员模式
- 为 Azure 安装和自定义影像服务检索的 Internet 访问权限
-  一系列至少十五 （15） 图像是必需的） 为你想自定义视觉识别每个对象。 如果愿意，可以使用与本课程中，已提供的映像[的 cup 的一系列](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

## <a name="before-you-start"></a>开始之前

1.  若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。
2.  设置和测试你 HoloLens。 如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。 

有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。

有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。

## <a name="chapter-1---the-custom-vision-portal"></a>第 1 章-自定义影像门户

若要使用**Azure 自定义影像服务**，将需要配置它以可供你的应用程序的实例。

1.  导航[到**自定义影像服务**主页](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  单击**入门**。

    ![](images/AzureLabs-Lab310-01.png)

3.  登录到自定义影像门户。

    ![](images/AzureLabs-Lab310-02.png)

4.  如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

5.  登录第一次，系统会提示使用*服务条款*面板。 单击复选框*即表示同意条款*。 然后单击**我同意**。

    ![](images/AzureLabs-Lab310-03.png)

6.  具有同意这些条款，你现在处于*我的项目*部分。 单击**新的项目**。

    ![](images/AzureLabs-Lab310-04.png)

7.  将提示你指定项目的某些字段的右侧将显示一个选项卡。

    1.  插入你的项目的名称

    2.  插入你的项目的说明 (**可选**)

    3.  选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些课程） 相关联的所有 Azure 服务）。

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > 如果想要对[阅读更多有关 Azure 资源组中，导航到相关联的文档](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  设置**项目类型**作为**对象检测 （预览版）**。

8.  完成后，单击**创建项目**，并且将重定向到自定义影像服务项目页。


## <a name="chapter-2---training-your-custom-vision-project"></a>第 2 章-培训您的自定义视觉项目

一次在自定义视觉门户中，您的主要目标是训练你的项目以识别图像中的特定对象。

你想要识别您应用程序的每个对象需要至少 15 （15） 映像。 可以使用与本课程提供的映像 ([的 cup 的一系列](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

若要训练你的自定义视觉项目：

1.  单击 **+** 按钮旁边**标记**。

    ![](images/AzureLabs-Lab310-06.png)

2.  添加**名称**将用于将与映像相关联的标记。 在此示例中我们是用于识别，因此具有称为标记为此，使用的 cup 的映像**杯**。 单击**保存**一次完成。

    ![](images/AzureLabs-Lab310-07.png)

3.  你会注意到您**标记**已添加 （可能需要重新加载它才会显示在页面）。 

    ![](images/AzureLabs-Lab310-08.png)

4.  单击**将图像添加**中页的中心。

    ![](images/AzureLabs-Lab310-09.png)

5.  单击**浏览本地文件**，并浏览到你想要为一个对象，最小正在十五 (15) 上传的映像。

    > [!TIP]
    >  一次，若要上传，可以选择多个映像。

    ![](images/AzureLabs-Lab310-10.png)

6.  按**将文件上传**选择所有映像后你想要训练的项目。 随即开始将文件上传。 上传的确认后，单击**完成**。

    ![](images/AzureLabs-Lab310-11.png)

7.  此时你的映像上传，但不是会标记。

    ![](images/AzureLabs-Lab310-12.png)

8.  若要标记你的映像，使用鼠标。 将鼠标指针悬停在图像上，选择突出显示将帮助您通过自动绘制围绕你的对象选择。 如果不准确，则可以绘制自己。 这一点通过持有鼠标左键单击和拖动所选区域，以包含您的对象。 

    ![](images/AzureLabs-Lab310-13.png) 

9. 以下图像中对象的所选内容，小提示将要求你能够*添加区域标记*。 选择你以前创建的标记 （创新杯，在上面的示例），或者如果在添加更多标记，类型中，单击 **+ （加）** 按钮。

    ![](images/AzureLabs-Lab310-14.png) 

10. 若要标记的下一步的映像，可以单击边栏选项卡中，右侧的箭头，或关闭标记边栏选项卡 (通过单击**X**边栏选项卡的右上角)，然后单击下一幅图像。 下一步的映像准备就绪后，重复相同的过程。 已上传，直到它们所有标记的所有映像执行此都操作。 

    > [!NOTE]
    >  在同一个映像，类似于下图中，可以选择多个对象： 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. 一旦已标记所有这些，则单击**标记**按钮左侧的屏幕上，以显示标记的映像。 

    ![](images/AzureLabs-Lab310-16.png)

12. 现在您就可以训练你的服务。 单击**训练**按钮和第一次训练迭代将开始。

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. 一旦建立，您将能够看到两个按钮名为**设为默认**并**预测 URL**。 单击**设为默认**第一次，然后单击**预测 URL**。

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > 此操作，请从提供的终结点设置为准*迭代*已被标记为默认值。 同样，如果您更高版本进行的新*迭代*和更新为默认值，不需要更改代码。

14. 一旦你单击**预测 URL**，打开*记事本*，然后复制并粘贴**URL** (也称为你**预测终结点**)并**服务预测密钥**，以便可在需要更高版本在代码中时进行检索。

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章 — 设置 Unity 项目

以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。

1.  打开**Unity**然后单击**新建**。

    ![](images/AzureLabs-Lab310-21.png)

2.  现在，需要提供的 Unity 项目名称。 插入**CustomVisionObjDetection**。 请确保项目类型设置为**三维**，并设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![](images/AzureLabs-Lab310-22.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到 **编辑* > *首选项** ，然后在新窗口中，导航到 **外部工具** 。 更改**外部脚本编辑器**到**Visual Studio**。 关闭**首选项**窗口。

    ![](images/AzureLabs-Lab310-23.png)

4.  接下来，请转到**文件 > 生成设置**，并切换**平台**到*通用 Windows 平台*，然后单击**切换平台**按钮。

    ![](images/AzureLabs-Lab310-24.png)

5.  在同一**生成设置**窗口中，确保将以下项设置：

    1.  **设备为目标**设置为**HoloLens**        
    2.  **生成的类型**设置为**D3D**
    3.  **SDK**设置为**最新安装**
    4.  **Visual Studio 版本**设置为**最新安装**
    5.  **生成并运行**设置为**本地计算机**            
    6.  中的剩余设置，**生成设置**，应暂时保留为默认值。

        ![](images/AzureLabs-Lab310-25.png)

6.  在同一**生成设置**窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。

7. 在此面板中，需要验证几个设置：

    1.  在中**其他设置**选项卡：

        1.  **脚本运行时版本**应**实验**（.NET 4.6 等效），这将触发需要重新启动编辑器。

        2. **脚本编写后端**应 **.NET**。

        3. **API 兼容性级别**应 **.NET 4.6**。

            ![](images/AzureLabs-Lab310-26.png)

    2.  内**发布设置**选项卡上，在**功能**，检查：

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，然后确保**Windows 混合现实 SDK**添加。

        ![](images/AzureLabs-Lab310-29.png)

8.  回到**生成设置**， *Unity C\#项目*不再灰显： 选中此旁边的复选框。

9.  关闭**生成设置**窗口。

10. 在中**编辑器**，单击**编辑** > **项目设置** > **图形**。

    ![](images/AzureLabs-Lab310-30.png)

11. 在中**检查器面板***图形设置*则会打开。 向下滚动直到您看到名为的数组**始终包括着色器**。 通过增加添加槽**大小**由一个变量 (在此示例中，它是 8 以便我们进行 9)。 新的槽将显示，在该数组的最后一个位置，如下所示：

    ![](images/AzureLabs-Lab310-31.png)

12. 在槽中，单击旁边的槽以打开着色器的列表的较小的目标圆形。 寻找**旧版着色器/透明/漫射**着色器，然后双击它。 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>第 4 章-导入 CustomVisionObjDetection Unity 程序包

为名为 Unity 资产包向您提供本课程**Azure MR 310.unitypackage**。 

> [提示]支持 Unity，包括整个场景的任何对象可以打包到 **.unitypackage**文件，并导出 / 导入在其他项目中。 它是不同之间移动资产的最安全的且最有效方法**Unity 项目**。

您可以找到[需要在此处下载 Azure MR 310 包](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。

1.  准备好 Unity 仪表板中，单击**资产**在屏幕顶部的菜单，然后单击**导入包 > 自定义包**。

    ![](images/AzureLabs-Lab310-33.png)

2.  使用文件选取器选择**Azure MR 310.unitypackage**程序包，再单击**打开**。 将向你显示此资产的组件的列表。 通过单击确认导入**导入**按钮。

    ![](images/AzureLabs-Lab310-34.png)

3.  完成导入后，会注意到，从包文件夹现在已添加到您**资产**文件夹。 此类文件夹结构是典型的 Unity 项目。

    ![](images/AzureLabs-Lab310-35.png)

    1.  **材料**文件夹包含由使用的材料**注视游标**。 

    2.  **插件**文件夹包含 Newtonsoft DLL 代码用于反序列化服务的 web 响应。 两个 （2） 不同版本的文件夹和子文件夹中包含所需允许使用和生成的 Unity 编辑器和 UWP 生成的库。 

    3.  **预设**文件夹包含在场景中包含预设。 这些情况包括：

        1.  **GazeCursor**，应用程序中使用的光标。 将工作以及 SpatialMapping 预设可以基于物理对象在场景中放置。
        2.  **标签**，是用于在需要时在场景中显示的对象标记的用户界面对象。
        3.  **SpatialMapping**，这是创建虚拟映射中，使用 Microsoft HoloLens ' 空间跟踪使应用程序使用的对象。

    4.  **场景**文件夹当前包含本课程的预建的场景。

4.  打开**场景**文件夹，请在**项目面板**，然后双击**ObjDetectionScene**、 要加载的场景的将用于此课程。

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **不不包含任何代码**，将按照本课程中编写的代码。

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>章节 5-创建 CustomVisionAnalyser 类。

此时已准备好编写一些代码。 您将首先**CustomVisionAnalyser**类。

> [!NOTE]
> 对调用**自定义影像服务**，如下所示的代码中，所用**自定义视觉 REST API**。 通过使用此，您将学会如何实现并使用此 api （适用于了解如何在您自己实现类似的内容）。 请注意，Microsoft 提供了**自定义视觉 SDK** ，还可用于对服务进行调用。 有关详细信息，请访问[自定义视觉 SDK 文章](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。

此类负责：

- 正在加载最新的映像捕获为一个字节数组。

- 将字节数组发送到你的 Azure**自定义影像服务**实例以进行分析。

- 接收响应以 JSON 字符串。

- 反序列化响应并传递得到**预测**到**SceneOrganiser**类，该类将负责响应的显示方式。

若要创建此类：

1.  在中右击**资产文件夹**，它位于**项目面板**，然后单击**创建** > **文件夹**。 将该文件夹**脚本**。

    ![](images/AzureLabs-Lab310-37.png)

2.  双击新创建的文件夹，以将其打开。

3.  在文件夹中，右键单击，然后单击**创建** > **C\#脚本**。 脚本命名为**CustomVisionAnalyser。**

4.  双击新**CustomVisionAnalyser**脚本以将其与打开**Visual Studio。**

5.  请确保具有以下命名空间引用该文件顶部：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  在中**CustomVisionAnalyser**类中，添加以下变量：

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 请确保插入你**服务预测密钥**到**predictionKey**变量和你**预测终结点**到**predictionEndpoint**变量。 复制到[记事本更早版本，在第 2 章，步骤 14](#chapter-2---training-your-custom-vision-project)。

7.  为代码**Awake()** 现在需要添加初始化该实例变量：

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  添加协同程序 (使用静态**GetImageAsByteArray()** 它下面的方法)，这将获取由捕获的图像的分析结果**ImageCapture**类。

    > [!NOTE]
    > 在中**AnalyseImageCapture**协同程序，没有调用**SceneOrganiser**尚若要创建的类。 因此，**保留这些行注释现在**。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. 删除**start （)** 并**update （)** 方法，因为它们不会使用。 

10.  请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。

> [!IMPORTANT]
> 前面曾提到，不必担心可能显示为具有错误，因为您将进一步提供类，也可解决这些代码。

## <a name="chapter-6---create-the-customvisionobjects-class"></a>章 6-创建 CustomVisionObjects 类

现在，您将创建的类是**CustomVisionObjects**类。

此脚本包含多个对象由其他类用于序列化和反序列化对自定义影像服务所做的调用。

若要创建此类：

1.  内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。 调用脚本**CustomVisionObjects。**

2.  双击新**CustomVisionObjects**脚本以将其与打开**Visual Studio。**

3.  请确保具有以下命名空间引用该文件顶部：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  删除**start （)** 并**update （)** 中的方法**CustomVisionObjects**类，该类现在应为空。

    > [!WARNING]
    > 请务必仔细按照下一条指令。 如果将放在新的类声明**CustomVisionObjects**类，您将在出现编译错误[第 10 章](#chapter-10---create-the-imagecapture-class)，指出该**AnalysisRootObject**和**BoundingBox**找不到。

5.  添加以下类*外部* **CustomVisionObjects**类。 这些对象由**Newtonsoft**库进行序列化和反序列化响应数据：

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。

## <a name="chapter-7---create-the-spatialmapping-class"></a>章 7-创建 SpatialMapping 类

此类将设置**空间映射碰撞体**场景，因此，若要能够检测到虚拟对象与真实的对象之间的冲突中。

若要创建此类：

1.  内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。 调用脚本**SpatialMapping。**

2.  双击新**SpatialMapping**脚本以将其与打开**Visual Studio。**

3.  请确保具有上面引用的以下命名空间**SpatialMapping**类：

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  然后，添加以下变量内的**SpatialMapping**类，更高版本**start （)** 方法：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  添加**Awake()** 并**start （)**:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  删除**update （)** 方法。

7.  请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。


## <a name="chapter-8---create-the-gazecursor-class"></a>章 8-创建 GazeCursor 类

此类负责在实际空间中，正确的位置设置游标通过利用**SpatialMappingCollider**上一章中创建。

若要创建此类：

1.  内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。 调用脚本**GazeCursor**

2.  双击新**GazeCursor**脚本以将其与打开**Visual Studio。**

3.  请确保具有上面引用的以下命名空间**GazeCursor**类：

    ```csharp
    using UnityEngine;
    ```

4.  然后添加以下变量内的**GazeCursor**类，更高版本**start （)** 方法。 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  更新**start （)** 方法使用以下代码：

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  更新**update （)** 方法使用以下代码：

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > 有关的错误，请不要担心**SceneOrganiser**类找不到，您将在下一章中创建它。

7. 请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。

## <a name="chapter-9---create-the-sceneorganiser-class"></a>章 9-创建 SceneOrganiser 类

将此类：

-   设置*Main Camera*通过附加到适当的组件。

-   检测到一个对象时，它将负责计算它的实际和位置中的位置**标记标签**附近使用相应**标记名称**。    

若要创建此类：

1.  内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。 脚本命名为**SceneOrganiser**。

2.  双击新**SceneOrganiser**脚本以将其与打开**Visual Studio。**

3.  请确保具有上面引用的以下命名空间**SceneOrganiser**类：

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  然后添加以下变量内的**SceneOrganiser**类，更高版本**start （)** 方法：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  删除**start （)** 并**update （)** 方法。

6.  变量后下, 添加**Awake()** 方法，它将初始化类并设置场景。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  添加**PlaceAnalysisLabel()** 方法，将*实例化*场景 （即现在用户看不到） 中的标签。 它还会提供四 （还不可见） 映像放置，以及与现实世界重叠。 这非常重要，因为分析追溯到此四确定现实世界中的对象的近似位置后，从服务检索框坐标。 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  添加**FinaliseLabel()** 方法。 它负责：

    *   设置*标签*带有文本*标记*的最高的信心十足地预测。
    *   调用的计算*边界框*以前，定位的四部分对象和将标签放在场景中。
    *   通过使用针对 Raycast 调整标签深度*边界框*，这应碰撞现实世界中的对象。
    * 正在重置，捕获进程才能允许用户以捕获另一个映像。

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  添加**CalculateBoundingBoxPosition()** 方法，它托管的转换所必需的计算数量*边界框*坐标从服务检索和重新创建它们按比例上四。

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. 请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。

    > [!IMPORTANT]
    > 在继续之前，打开**CustomVisionAnalyser**类，并在**AnalyseLastImageCaptured()** 方法，*取消注释*以下行：
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> 不要担心**ImageCapture**类无法找到消息中，你将在下一章中创建它。


## <a name="chapter-10---create-the-imagecapture-class"></a>章 10-创建 ImageCapture 类

要创建的下一步类是**ImageCapture**类。

此类负责：

*   捕获映像使用 HoloLens 相机并将其存储在*应用*文件夹。
*   处理*点击*用户手势。

若要创建此类：

1.  转到**脚本**之前创建的文件夹。

2.  在文件夹中，右键单击，然后单击**创建** > **C\#脚本**。 脚本命名为**ImageCapture**。

3.  双击新**ImageCapture**脚本以将其与打开**Visual Studio。**

4.  使用以下内容替换该文件顶部的命名空间：

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然后添加以下变量内的**ImageCapture**类，更高版本**start （)** 方法：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  为代码**Awake()** 并**start （)** 方法现在需要添加：

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  实现的点击动作时将调用的处理程序：

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > 当光标位于**绿色**，则意味着照相机是可用于获取映像。 当光标位于**红色**，这意味着照相机正忙。

8.  添加应用程序使用启动映像捕获过程并将图像存储的方法：

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  添加捕获照片和时准备好对其进行分析将调用处理程序。 然后将结果传递给**CustomVisionAnalyser**进行分析。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>第 11 章 — 设置场景中的脚本

现在，您编写所有此项目所必需，是代码的时候若要设置在场景中和在预设，才能正常运行的脚本。

1.  内**Unity 编辑器**，在**层次结构面板**，选择**Main Camera**。
2.  在中**检查器面板**，使用**Main Camera**上处于选中状态，单击**添加组件**，然后搜索**SceneOrganiser**脚本和双击，以将其添加。

    ![](images/AzureLabs-Lab310-38.png)

3.  在**项目面板**，打开**置入 Prefabs 文件夹**，拖动**标签**到 prefab*标签*空引用目标中的输入区域中，**SceneOrganiser**刚添加到脚本*Main Camera*，如下图中所示：

    ![](images/AzureLabs-Lab310-39.png)

4.  在中**层次结构面板**，选择**GazeCursor**的子**Main Camera**。
5.  在中**检查器面板**，使用**GazeCursor**上处于选中状态，单击**添加组件**，然后搜索**GazeCursor**脚本和双击，以将其添加。

    ![](images/AzureLabs-Lab310-40.png)

6.  同样，在**层次结构面板**，选择**SpatialMapping**的子**Main Camera**。
7.  在中**检查器面板**，使用**SpatialMapping**上处于选中状态，单击**添加组件**，然后搜索**SpatialMapping**脚本然后双击，以将其添加。

    ![](images/AzureLabs-Lab310-41.png)

其余的您的脚本具有不会添加组中的代码**SceneOrganiser**脚本，在运行时。

## <a name="chapter-12---before-building"></a>第 12 章 — 生成前

若要执行全面测试您的应用程序将需要旁加载它到 Microsoft HoloLens 上。

执行操作之前，请确保：

-  中所述的所有设置[第 3 章](#chapter-3---set-up-the-unity-project)正确设置。
- 该脚本**SceneOrganiser**附加到**Main Camera**对象。
- 该脚本**GazeCursor**附加到**GazeCursor**对象。
- 该脚本**SpatialMapping**附加到**SpatialMapping**对象。
- 在中[第 5 章：](#chapter-5---create-the-customvisionanalyser-class)，步骤 6:

    - 请确保插入你**服务预测密钥**成**predictionKey**变量。
    - 已插入您**预测终结点**成**predictionEndpoint**类。

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>章 13-生成的 UWP 解决方案和旁加载应用程序

现在您就可以生成应用程序作为一个 UWP 解决方案，你将能够部署到 Microsoft HoloLens。 若要开始生成过程：

1.  转到**文件 > 生成设置**。

2.  刻度线**Unity C\#项目**。

3.  单击**添加打开场景**。 这将添加到生成的当前打开的场景。

    ![](images/AzureLabs-Lab310-42.png)

4.  单击“生成” 。 将启动 unity*文件资源管理器*窗口中，需要创建，然后选择要生成该应用程序的文件夹。 现在，创建该文件夹并将其命名**应用**。 然后使用**应用程序**文件夹选择，单击**选择文件夹**。

5.  Unity 将开始构建您的项目**应用**文件夹。

6.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。

7.  若要部署到 Microsoft HoloLens，都需要该设备的 IP 地址 （适用于远程部署），并且以确保其还具有**开发人员模式**设置。 要实现此目的，请执行以下操作：

    1.  戴上您 HoloLens，同时打开**设置**。

    2.  转到**网络和 Internet** > **的 Wi-fi** > **高级选项**

    3.  请注意**IPv4**地址。

    4.  接下来，导航回到**设置**，然后**更新和安全** > **面向开发人员**

    5.  设置**开发人员模式***上*。

8.  导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。

9.  在解决方案配置中，选择**调试**。

10. 在解决方案平台中，选择**x86，远程计算机**。 系统会提示要插入**IP 地址**的远程设备 (Microsoft HoloLens，在这种情况下，记下)。

    ![](images/AzureLabs-Lab310-43.png)

11. 转到**构建**菜单，并单击**部署解决方案**旁加载到你 HoloLens 应用程序。

12. 在准备好启动您 Microsoft HoloLens 上安装的应用列表中，现在应显示你的应用 ！

### <a name="to-use-the-application"></a>若要使用应用程序：

* 看一看一个对象，它使用训练你**Azure 自定义影像服务、 对象检测**，并使用**点击手势**。
* 如果该对象已成功检测到，世界空间*标签文本*将显示为带有标记名称。

> [!IMPORTANT]
> 每次捕获照片并将其发送到服务，可以返回到服务页并重新训练新捕获的映像的服务。 在开始时，您将可能还需要更正*边界框*更准确和重新训练服务。

> [!NOTE]
> 放置标签文本可能不会显示附近对象 Microsoft HoloLens 传感器和/或在 Unity 中的 SpatialTrackingComponent 失败将相应的碰撞体，相对于现实世界对象时。 请尝试使用不同的图面上的应用程序，如果是这种情况。

## <a name="your-custom-vision-object-detection-application"></a>你的自定义愿景，对象检测应用程序

祝贺你，构建利用 Azure 自定义视觉对象检测 API，它可以识别图像中的对象，然后提供在 3D 空间中的近似位置以该对象的混合的现实应用。

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

将添加到文本标签，使用半透明的多维数据集以将实际对象封装在一个三维*边界框*。

### <a name="exercise-2"></a>练习 2

训练你自定义影像服务能够识别更多的对象。

### <a name="exercise-3"></a>练习 3

识别对象时播放声音。

### <a name="exercise-4"></a>练习 4

若要重新训练你的服务使用相同的图像分析您的应用程序，因此若要使服务更准确地使用 API （执行预测和同时培训）。
