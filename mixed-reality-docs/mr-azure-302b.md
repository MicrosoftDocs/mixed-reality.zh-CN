---
title: MR 和 Azure 302b-自定义视觉
description: 完成此课程以了解如何定型机器学习模型，以及如何将训练的模型来识别混合的现实应用程序中的类似对象。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 自定义影像，沉浸式、 hololens、 vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591813"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR 和 Azure 302b:自定义视觉

在本课程中，您将学习如何识别自定义可视化内容中提供的映像，在混合的现实应用程序中使用 Azure 自定义视觉功能。

此服务将允许你定型机器学习模型，使用对象映像。 然后将使用经过训练的模型来识别类似对象，提供的 Microsoft HoloLens 或照相机连接到您的 PC 以沉浸式 (VR) 耳机的相机捕捉。

![课程结果](images/AzureLabs-Lab302b-00.png)

Azure 自定义影像是一种 Microsoft 认知服务，允许开发人员可以构建自定义图像分类器。 这些分类器可以随后可用于新的映像识别，或进行分类、 设置了新的映像中的对象。 该服务提供简单、 易于使用、 联机门户以简化过程。 有关详细信息，请访问[Azure 自定义影像服务页](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。

完成本课程时，之后您将拥有一个混合的现实应用程序，将能够在两个模式下工作：

-   **分析模式**： 自定义影像服务手动设置通过将映像上传、 创建标记，并训练服务来识别不同 （在此事例的鼠标和键盘） 的对象。 然后，您将创建一个 HoloLens 应用，它将捕获映像使用相机，并尝试识别现实生活中的这些对象。

-   **训练模式**： 将实现将启用"培训模式"应用程序中的代码。 训练模式将允许您捕获使用 HoloLens 的照相机图像、 将捕获的映像上传到服务，并为自定义影像模型定型。

本课程将介绍如何将结果从自定义影像服务到基于 Unity 的示例应用程序。 它将取决于您要应用于您可能要构建一个自定义应用程序的这些概念。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 302b:自定义视觉</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 HoloLens，您还可以应用到 Windows Mixed Reality 沉浸式 (VR) 耳机本课程中学习的内容。 因为沉浸式 (VR) 耳机不具有可访问照相机，您将需要连接到您的 PC 外部照相机。 按照课程时，您将看到说明您可能需要使用以支持沉浸式 (VR) 耳机的任何更改。

## <a name="prerequisites"></a>系统必备

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。 你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。

我们建议以下硬件和软件本课程：

- 开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式
- 照相机连接到您的 PC （适用于沉浸式头戴式开发）
- Internet 访问的 Azure 设置和自定义视觉 API 检索
- 一系列的至少五 （5） 图像 （十 （10） 建议） 为你想自定义影像服务识别每个对象。 如果您愿意，可以使用[已随附此课程 （计算机鼠标和键盘） 的映像](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。

## <a name="before-you-start"></a>开始之前

1.  若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。
2.  设置和测试你 HoloLens。 如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。 

有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。

有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。

## <a name="chapter-1---the-custom-vision-service-portal"></a>第 1 章-自定义影像服务门户

若要使用*自定义影像服务*在 Azure 中，你将需要配置要成为可用于应用程序的服务的实例。

1.  首先，[导航到*自定义影像服务*主页](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  单击**开始**按钮。

    ![](images/AzureLabs-Lab302b-01.png)

3.  登录到*自定义影像服务*门户。

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

4.  登录第一次，系统会提示使用*服务条款*面板。 单击该复选框以同意这些条款。 然后单击**我同意**。

    ![](images/AzureLabs-Lab302b-03.png)

5.  具有同意这些条款，你将导航至*项目*门户的一部分。 单击**新的项目**。

    ![](images/AzureLabs-Lab302b-04.png)

6.  将提示你指定项目的某些字段的右侧将显示一个选项卡。

    1.  插入*名称*为你的项目。

    2.  插入*描述*为你的项目 (*可选*)。

    3.  选择*资源组*或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。

    4. 设置*项目类型*到**分类**
    
    5. 设置*域*作为**常规**。

        ![](images/AzureLabs-Lab302b-05.png)

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

7.  完成后，单击**创建项目**，你将重定向到自定义影像服务，项目页。

## <a name="chapter-2---training-your-custom-vision-project"></a>第 2 章-培训您的自定义视觉项目

一次在自定义视觉门户中，您的主要目标是训练你的项目以识别图像中的特定对象。 需要至少五 （5） 映像，但十 （10） 是首选方法，你想要识别您应用程序的每个对象。 [可以使用与此课程 （计算机鼠标和键盘） 提供的映像](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。 

若要训练你自定义影像服务的项目：

1.  单击**+** 按钮旁边**标记。**

    ![](images/AzureLabs-Lab302b-06.png)

2.  添加**名称**你想要识别的对象。 单击**保存**。

    ![](images/AzureLabs-Lab302b-07.png)

3.  你会注意到您**标记**已添加 （可能需要重新加载它才会显示在页面）。 如果未选中，请单击与你的新标记，该复选框。

    ![](images/AzureLabs-Lab302b-08.png)

4.  单击**添加映像**中页的中心。

    ![](images/AzureLabs-Lab302b-09.png)

5.  单击**浏览本地文件**，并搜索，然后选择你想要上传，最小为映像五 （5)。 请记住所有这些映像应包含将训练的对象。

    > [!NOTE]
    >  一次，若要上传，可以选择多个映像。

6.  一旦您所见的映像的选项卡中，选择中的适当标记**我标记**框。

    ![](images/AzureLabs-Lab302b-10.png)

7.  单击**将文件上传**。 随即开始将文件上传。 上传的确认后，单击**完成**。

    ![](images/AzureLabs-Lab302b-11.png)

8.  重复相同的过程来创建新**标记**名为**键盘**并将相应的照片上传它。 请确保**取消选中***鼠标*创建新标记，因此，若要显示后*将映像添加*窗口。

9.  设置这两个标记后，单击**训练**，并第一次训练迭代将开始构建。

    ![](images/AzureLabs-Lab302b-12.png)

10. 一旦建立，您将能够看到两个按钮名为**设为默认**并**预测 URL**。 单击**设为默认**第一次，然后单击**预测 URL**。

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > 此操作，请从提供的终结点 URL 设置为准*迭代*已被标记为默认值。 同样，如果您更高版本进行的新*迭代*和更新为默认值，不需要更改代码。

11. 一旦你单击*预测 URL*，打开*记事本*，然后复制并粘贴**URL**和**预测密钥**，以便你可以需要在代码中更高版本时进行检索。

    ![](images/AzureLabs-Lab302b-14.png)

12. 单击**嵌齿**顶部的屏幕。

    ![](images/AzureLabs-Lab302b-15.png)

13. 复制**培训键**将其粘贴到*记事本*，以供将来使用。

    ![](images/AzureLabs-Lab302b-16.png)

14. 另外，将复制你**项目 Id**，还将其粘贴到你*记事本*文件，以供将来使用。

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章 — 设置 Unity 项目

以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。

1.  打开*Unity*然后单击**新建**。

    ![](images/AzureLabs-Lab302b-17.png)

2.  现在，需要提供的 Unity 项目名称。 插入**AzureCustomVision。** 请确保项目模板设置为**3D**。 设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![](images/AzureLabs-Lab302b-18.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑* > *首选项** ，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![](images/AzureLabs-Lab302b-19.png)

4.  接下来，请转到**文件 > 生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。

    ![](images/AzureLabs-Lab302b-20.png)

5.  在仍处于**文件 > 生成设置**并确保选中：

    1.  **设备为目标**设置为**Hololens**

        > 对于沉浸式耳机，设置**目标设备**到*任一设备*。
        
    2.  **生成的类型**设置为**D3D**
    3.  **SDK**设置为**最新安装**
    4.  **Visual Studio 版本**设置为**最新安装**
    5.  **生成并运行**设置为**本地计算机**
    6.  保存场景，并将其添加到生成。 

        1. 选择执行此**添加打开场景**。 保存窗口将显示。

            ![](images/AzureLabs-Lab302b-21.png)

        2. 创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![](images/AzureLabs-Lab302b-22.png)

        3. 打开新建**场景**文件夹，然后在*文件的名称：* 文本字段中，键入**CustomVisionScene**，然后单击**保存**。

            ![](images/AzureLabs-Lab302b-23.png)

            > 请注意，必须将保存您的 Unity 场景中*资产*文件夹中，因为它们必须与 Unity 项目相关联。 创建场景文件夹 （和其他类似的文件夹） 是用于结构化的 Unity 项目的典型方式。
            
    7.  中的剩余设置，*生成设置*，应暂时保留为默认值。

        ![](images/AzureLabs-Lab302b-24.png)

6.  在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。

7. 在此面板中，需要验证几个设置：

    1.  在中**其他设置**选项卡：

        1.  **脚本运行时版本**应**实验 （.NET 4.6 等效）**，这将触发需要重新启动编辑器。

        2. **脚本编写后端**应为 **.NET**

        3. **API 兼容性级别**应为 **.NET 4.6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  内**发布设置**选项卡上，在**功能**，检查：

        1. **InternetClient**

        2.  **Webcam**

        3. **Microphone**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。

    ![](images/AzureLabs-Lab302b-27.png)

8.  回到*生成设置* *Unity C\#项目*不再灰显; 选中它旁边的复选框。

9.  关闭生成设置窗口。

10.  保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>第 4 章-导入 Unity 中 Newtonsoft DLL

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[Azure MR 302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 6 章](#chapter-6---create-the-customvisionanalyser-class)。

此课程需要使用**Newtonsoft**库，可以作为 DLL 添加到你的资产。 包包含[可以从以下链接下载此库](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)。
若要 Newtonsoft 库导入到你的项目，使用了随附此课程的 Unity 包。

1.  添加 *.unitypackage*到使用 Unity **资产* > *导入**包* > *自定义**包** 菜单选项。

2.  在中**导入 Unity 程序包**弹出框、 下 （其中包含） 确保一切**插件**处于选中状态。

    ![](images/AzureLabs-Lab302b-28.png)

3.  单击**导入**按钮将项添加到你的项目。

4.  转到**Newtonsoft**下的文件夹**插件**在项目视图中，选择*Newtonsoft.Json 插件*。

    ![](images/AzureLabs-Lab302b-29.png)

5.  与*Newtonsoft.Json 插件*选择，确保**Any 平台**是**未选中**，然后确保**WSAPlayer**也**unchecked**，然后单击**应用**。 这只是为了确认正确配置文件。

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > 将标记这些插件将它们配置为仅使用在 Unity 编辑器中。 有一组不同的它们从 Unity 项目会导出后，将使用 WSA 文件夹中。

6.  接下来，您需要打开**WSA**文件夹，在**Newtonsoft**文件夹。 您将看到刚配置的相同文件的副本。 选择的文件，然后在检查器中，确保的
    -   **任何平台**是**未选中状态** 
    -   **仅** **WSAPlayer**是**检查**
    -   **不处理**是**检查**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>第 5 章-照相机设置

1.  在层次结构窗格中，选择*Main Camera*。

2.  选择后，你将能够看到的所有组件*Main Camera*中*检查器面板*。

    1.  *照相机*对象必须命名为**Main Camera** （请注意拼写 ！）

    2.  Main Camera**标记**必须设置为**MainCamera** （请注意拼写 ！）

    3.  请确保**转换位置**设置为**0，0，0**

    4.  设置**清除标志**到**纯色**（忽略这的沉浸式头戴式耳机）。

    5.  设置**背景**相机的颜色组件**黑色、 Alpha 0 (十六进制代码: #00000000)** （忽略这的沉浸式头戴式耳机）。

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>章 6-创建 CustomVisionAnalyser 类。

此时已准备好编写一些代码。

您将首先*CustomVisionAnalyser*类。

> [!NOTE]
> 对调用**自定义影像服务**中所示的代码所做下面所用**自定义视觉 REST API**。 通过使用此，您将学会如何实现并使用此 api （适用于了解如何在您自己实现类似的内容）。 请注意，Microsoft 提供了**自定义影像服务 SDK** ，还可用于对服务进行调用。 有关详细信息，请访问[自定义影像服务 SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)一文。

此类负责：

-   正在加载最新的映像捕获为一个字节数组。

-   将字节数组发送到你的 Azure*自定义影像服务*实例以进行分析。

-   接收响应以 JSON 字符串。

-   反序列化响应并传递得到*预测*到*SceneOrganiser*类，该类将负责响应的显示方式。

若要创建此类：

1.  在中右击*资产文件夹*位于*项目面板*，然后单击**创建 > 文件夹**。 将该文件夹**脚本**。

    ![](images/AzureLabs-Lab302b-33.png)

2.  双击刚创建的文件夹，以将其打开。

3.  在文件夹中，右键单击，然后单击**创建** > **C\#脚本**。 脚本命名为*CustomVisionAnalyser*。

4.  双击新*CustomVisionAnalyser*脚本以将其与打开**Visual Studio**。

5.  更新你的文件以匹配以下顶部的命名空间：

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  在中*CustomVisionAnalyser*类中，添加以下变量：

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 请确保插入你**预测键**到**predictionKey**变量和你**预测终结点**到**predictionEndpoint**变量。 复制到*记事本*前面的课程。

7.  为代码**Awake()** 现在需要添加初始化该实例变量：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  删除方法**start （)** 并**update （)**。

9.  接下来，添加协同程序 (使用静态**GetImageAsByteArray()** 它下面的方法)，这将获取由捕获映像的分析结果*ImageCapture*类。

    > [!NOTE]
    > 在中**AnalyseImageCapture**协同程序，没有调用*SceneOrganiser*尚若要创建的类。 因此，**保留这些行注释现在**。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  请务必保存中所做的更改**Visual Studio**才会回到**Unity**。

## <a name="chapter-7---create-the-customvisionobjects-class"></a>章 7-创建 CustomVisionObjects 类

现在，您将创建的类是*CustomVisionObjects*类。

此脚本包含的对象由其他类用于序列化和反序列化对所做的调用数*自定义影像服务*。

> [!WARNING]
> 非常重要，需要记下的终结点，可自定义影像服务提供，与以下 JSON 结构已设置为使用[*自定义视觉预测 v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)。 如果您拥有的不同版本，您可能需要更新以下结构。

若要创建此类：

1.  内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。 调用脚本*CustomVisionObjects*。

2.  双击新**CustomVisionObjects**脚本以将其与打开**Visual Studio**。

3.  将以下命名空间添加到文件顶部：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  删除**start （)** 并**update （)** 中的方法*CustomVisionObjects*类; 此类应为空。

5.  添加以下类**外部** *CustomVisionObjects*类。 这些对象由*Newtonsoft*库进行序列化和反序列化响应数据：

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>章 8-创建 VoiceRecognizer 类

此类将识别用户的语音输入。

若要创建此类：

1.  内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。 调用脚本*VoiceRecognizer*。

2.  双击新**VoiceRecognizer**脚本以将其与打开**Visual Studio**。

3.  添加以下命名空间上述*VoiceRecognizer*类：

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  然后添加以下变量内的*VoiceRecognizer*类，更高版本*start （)* 方法：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  添加**Awake()** 并**start （)** 方法，后者将设置注册该用户*关键字*能够识别相关联的图像标记时：

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  删除**update （)** 方法。

7.  添加以下处理程序，每当识别语音输入时调用：

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  请务必保存中所做的更改**Visual Studio**才会回到**Unity**。

> [!NOTE]
> 不必担心可能显示为具有错误，将提供进一步的类，可以修复这些代码。

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>章 9-创建 CustomVisionTrainer 类

此类将链接的一系列 web 调用来训练*自定义影像服务*。 每次调用将代码的正上方的详细信息中所述。

若要创建此类：

1.  内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。 调用脚本*CustomVisionTrainer*。

2.  双击新*CustomVisionTrainer*脚本以将其与打开**Visual Studio**。

3.  添加以下命名空间上述*CustomVisionTrainer*类：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  然后添加以下变量内的*CustomVisionTrainer*类，更高版本**start （)** 方法。 

    > [!NOTE]
    > 中提供此处使用的培训 URL*自定义视觉训练 1.2*文档，并具有的结构： https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > 有关详细信息，请访问[ *v1.2 引用自定义视觉训练 API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。

    > [!WARNING]
    > 非常重要，需要注意的自定义影像服务提供培训模式下，为使用的 JSON 结构的终结点 (内**CustomVisionObjects**类) 已设置为使用[ *自定义视觉训练 v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。 如果您拥有的不同版本，您可能需要更新*对象*结构。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > 确保添加你**服务密钥**（培训密钥） 值和**项目 Id**值，其下前面记下; 这些都是值您[从前面的课程 （门户收集第 2 章步骤 10 及更高版本）](#chapter-2---training-your-custom-vision-oroject)。

5.  添加以下**start （)** 并**Awake()** 方法。 这些方法在初始化时调用，并包含调用以设置用户界面：

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  删除**update （)** 方法。 此类将不需要它。

7.  添加**RequestTagSelection()** 方法。 此方法是在捕获映像并将其存储在设备时要调用的第一个和现已准备好提交给*自定义影像服务*、 训练它。 此方法显示在训练 UI 中，一组用户可以使用标记已捕获映像的关键字。 它还会发出警报*VoiceRecognizer*类以开始侦听到用户的语音输入。

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  添加**VerifyTag()** 方法。 此方法将接收语音输入识别**VoiceRecognizer**类和验证其有效性，然后开始训练过程。

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  添加**SubmitImageForTraining()** 方法。 此方法将开始自定义影像服务训练过程。 第一步是检索**标记 Id**从与用户的已验证的语音输入相关联的服务。 **标记 Id**然后以及映像上传。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. 添加**TrainCustomVisionProject()** 方法。 一旦已提交并标记该映像，将调用此方法。 它将创建新的迭代，将使用提交到服务以及映像的所有以前的图像训练刚上传。 完成定型后，此方法将调用一个方法来设置新创建**迭代**作为**默认**，以便将用于分析的终结点是最新的训练的迭代。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. 添加**SetDefaultIteration()** 方法。 此方法将设置为以前创建并训练迭代*默认*。 完成后，此方法必须删除现有服务中的上一个迭代。 在编写本课程时，没有最大十 （10） 的迭代的允许在服务中同时存在限制。

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. 添加**DeletePreviousIteration()** 方法。 此方法将查找并删除之前的非默认迭代：

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. 此类中添加的最后一个方法是**GetImageAsByteArray()** 方法，用于在 web 调用要将映像捕获到的字节数组转换。

    ```csharp
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

14. 请务必保存中所做的更改**Visual Studio**才会回到**Unity**。

## <a name="chapter-10---create-the-sceneorganiser-class"></a>章 10-创建 SceneOrganiser 类

将此类：

-   创建**游标**要附加到 Main Camera 对象。

-   创建**标签**对象，该服务识别出的实际对象时，将显示对象。

-   通过附加到适当的组件设置 Main Camera。

-   在何时**分析模式**、 生成的标签，在运行时，相对于主相机的位置的适当世界空间中并显示从自定义影像服务接收的数据。

-   在何时**培训模式**，生成将显示在定型过程的不同阶段的 UI。

若要创建此类：

1.  内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。 脚本命名为*SceneOrganiser*。

2.  双击新*SceneOrganiser*脚本以将其与打开**Visual Studio**。

3.  您只需要一个命名空间，删除上面提供的其他*SceneOrganiser*类：

    ```csharp
    using UnityEngine;
    ```

4.  然后添加以下变量内的*SceneOrganiser*类，更高版本**start （)** 方法：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  删除**start （)** 并**update （)** 方法。

6.  右下方变量中，添加**Awake()** 方法，它将初始化类并设置场景。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  现在，添加**CreateCameraCursor()** 方法，用于创建将 Main Camera 光标定位并**CreateLabel()** 方法，用于创建**分析标签**对象.

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. 添加**SetCameraStatus()** 方法，它将处理适用于文本网格提供的相机的状态消息。

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. 添加**PlaceAnalysisLabel()** 并**SetTagsToLastLabel()** 方法，这将生成并向场景中显示自定义影像服务中的数据。

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. 最后，将添加**CreateTrainingUI()** 方法，将生成应用程序时在定型模式下都显示在定型过程的多个阶段的 UI。 此方法还会利用创建相机状态对象。

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. 请务必保存中所做的更改**Visual Studio**才会回到**Unity**。

> [!IMPORTANT]
> 在继续之前，打开**CustomVisionAnalyser**类，并在**AnalyseLastImageCaptured()** 方法，*取消注释*以下行：
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>章 11-创建 ImageCapture 类

要创建的下一步类是*ImageCapture*类。

此类负责：

-   捕获映像使用 HoloLens 相机并将其存储在*应用*文件夹。

-   处理来自用户的点击手势。

-   维护*Enum*值，该值确定是否运行该应用程序*Analysis*模式或*培训*模式。

若要创建此类：

1.  转到**脚本**之前创建的文件夹。

2.  在文件夹中，右键单击，然后单击**创建 > C\#脚本**。 脚本命名为*ImageCapture*。

3.  双击新**ImageCapture**脚本以将其与打开**Visual Studio**。

4.  使用以下内容替换该文件顶部的命名空间：

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然后添加以下变量内的*ImageCapture*类，更高版本**start （)** 方法：

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

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

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  实现的点击动作时将调用的处理程序。

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > 在中*分析*模式下， **TapHandler**方法充当一个开关，用于启动或停止照片捕获循环。
    >
    > 在中*培训*模式下，它将从捕获映像照相机。
    >
    > 当光标位于绿色时，这意味着照相机是可用于获取映像。
    >
    > 当光标位于红色时，这意味着照相机正忙。

8.  添加应用程序使用启动映像捕获过程并将图像存储的方法。

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  添加捕获照片和时准备好对其进行分析将调用处理程序。 然后将结果传递给*CustomVisionAnalyser*或*CustomVisionTrainer*具体取决于哪种模式上设置的代码。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 请务必保存中所做的更改**Visual Studio**才会回到**Unity**。

11. 现在，所有脚本都完成后，返回在 Unity 编辑器中，然后单击并拖动**SceneOrganiser**类派生**脚本**文件夹**Main Camera**对象中*层次结构面板*。

## <a name="chapter-12---before-building"></a>第 12 章 — 生成前

若要执行全面测试您的应用程序将需要旁加载它到在 HoloLens 上。

执行操作之前，请确保：

- 中所述的所有设置[第 2 章](#chapter-2---training-your-custom-vision-project)正确设置。

- 中的所有字段**Main Camera**，检查器面板中，正确分配。

- 该脚本**SceneOrganiser**附加到**Main Camera**对象。

- 请确保插入你**预测键**成**predictionKey**变量。

- 已插入您**预测终结点**成**predictionEndpoint**变量。

- 已插入您**培训键**成**trainingKey**变量的*CustomVisionTrainer*类。

- 已插入您**项目 ID**成**projectId**变量的*CustomVisionTrainer*类。

## <a name="chapter-13---build-and-sideload-your-application"></a>第 13 章 — 生成和旁加载应用程序

若要开始*生成*过程：

1.  转到**文件 > 生成设置**。

2.  刻度线**Unity C\#项目**。

3.  单击“生成” 。 将启动 unity**文件资源管理器**窗口中，需要创建，然后选择要生成该应用程序的文件夹。 现在，创建该文件夹并将其命名**应用**。 然后使用**应用程序**文件夹选择，单击**选择文件夹**。

4.  Unity 将开始构建您的项目**应用**文件夹。

5.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。

若要部署在 HoloLens 上：

1.  你将 （适用于远程部署），需要在 HoloLens IP 地址，以确保你 HoloLens 处于**开发人员模式**。 要实现此目的，请执行以下操作：

    1.  戴上您 HoloLens，同时打开**设置**。

    2.  转到**网络和 Internet** > **的 Wi-fi** > **高级选项**

    3.  请注意**IPv4**地址。

    4.  接下来，导航回到**设置**，然后**更新和安全** > **面向开发人员**

    5.  设置**上的开发人员模式**。

2.  导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。

3.  在中*解决方案配置*选择**调试**。

4.  在中*解决方案平台*，选择**x86，远程计算机**。 系统会提示要插入**IP 地址**的远程设备 (HoloLens，在这种情况下，记下)。

    ![](images/AzureLabs-Lab302b-34.png)

5. 转到**构建**菜单，并单击**部署解决方案**旁加载到你 HoloLens 应用程序。

6. 在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！

> [!NOTE]
> 若要将部署到沉浸式头戴式耳机，设置**解决方案平台**到*本地计算机*，并设置**配置**到*调试*，与*x86*作为**平台**。 然后将其部署到本地计算机，使用**构建**菜单项，选择*部署解决方案*。 

## <a name="to-use-the-application"></a>若要使用应用程序：

若要切换之间的应用功能*培训*模式和*预测*模式需要更新**AppMode**变量，它位于**Awake()** 方法对位于*ImageCapture*类。

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
或
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

在中*培训*模式：

- 看看**鼠标**或**键盘**，并使用**点击手势**。

- 接下来，文本将显示要求你提供一个标记。

- 指示**鼠标**或**键盘**。


在中*预测*模式：

- 查看对象，并使用**点击手势**。

- 文本将显示提供检测到，（这规范化的） 的概率最高的对象。

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>14-评估和改进您的自定义影像模型

若要使你的服务更准确，您需要继续训练用于预测的模型。 这通过使用两个新应用程序，来实现*培训*并*预测*模式下，使用后一种无需访问门户，它是这一章中涵盖的内容。 要准备好，若要再次访问你的门户很多时候，可以不断改进您的模型。

1. 同样，转到你的 Azure 自定义视觉门户并在项目中后，选择*预测*（从页面的顶部中心） 的选项卡：

    ![](images/AzureLabs-Lab302b-35.png)

2. 你将看到所有已发送到你的服务，同时你的应用程序正在运行的映像。 如果将鼠标悬停鼠标悬停在图像，他们将您提供有关该映像所做的预测：

    ![](images/AzureLabs-Lab302b-36.png)

3. 选择其中一个映像以将其打开。 一旦打开，你将看到右侧进行该图像的预测。 如果您预测正确的并且你想要将此映像添加到你的服务的训练模型中，单击*我标记*输入框，然后选择你想要将相关联的标记。 完成后，单击*保存并关闭*靠下右对齐，向按钮，然后继续学习下一幅图像。

    ![](images/AzureLabs-Lab302b-37.png)

4. 返回到网格的映像后，你会注意到已添加到标记 （并保存），映像将被删除。 如果您发现您认为不具有在其中你带标记的项的任何映像，则可以删除它们，通过单击该映像 （可以执行此操作的多个映像） 上的刻度线，然后单击*删除*网格页右上角。 在弹出窗口后面，你可以单击*可以，请删除*或*否*，以确认删除，或分别取消。 

    ![](images/AzureLabs-Lab302b-38.png)

5. 若要继续，准备就绪后，单击绿色*训练*在右上角的按钮。 你的服务模型将使用的所有映像现在已提供 （这将使其更准确） 训练。 培训完成后，请务必单击*设为默认*次，按钮，以便你*预测 URL*仍会继续使用你的服务的最新迭代。

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>完成自定义视觉 API 的应用程序

祝贺你，构建利用 Azure 自定义视觉 API 能够识别现实世界对象、 训练服务模型，并显示的内容出现的置信度的混合的现实应用。

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

训练你**自定义影像服务**识别更多的对象。

### <a name="exercise-2"></a>练习 2

作为一种方式扩展您学到了什么，完成以下练习：

识别对象时播放声音。

### <a name="exercise-3"></a>练习 3

若要重新训练你的服务使用相同的图像分析您的应用程序，因此若要使服务更准确地使用 API （执行预测和同时培训）。
