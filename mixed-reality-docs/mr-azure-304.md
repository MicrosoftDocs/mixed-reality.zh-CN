---
title: MR 和 Azure 304-人脸识别
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 人脸识别。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实、 学院、 unity、 教程、 api、 人脸识别，沉浸式、 hololens、 vr
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592789"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR 和 Azure 304:人脸识别

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

在本课程中您将了解如何将人脸识别功能添加到混合的现实应用程序，Azure 认知服务，与 Microsoft 人脸 API 结合使用。

*Azure 的人脸 API*是 Microsoft 服务，开发人员提供最先进的人脸算法，所有在云中。 *人脸 API*具有两个主要功能： 人脸属性后，检测和人脸识别。 这允许开发人员只需设置一组人脸的组，然后，查询图像向服务发送更高版本，以确定人脸属于其。 有关详细信息，请访问[Azure 人脸识别页](https://azure.microsoft.com/services/cognitive-services/face/)。

已完成本课程，您将具有混合的现实 HoloLens 应用程序，将能够执行以下操作：

1. 使用**点击手势**初始化使用板载 HoloLens 相机的图像的捕获。 
2. 发送到捕获的映像*Azure 人脸 API*服务。
3. 收到的结果*人脸 API*算法。
4. 使用简单的用户界面，以显示匹配的人的名称。

这将教您如何将结果从人脸 API 服务到基于 Unity 的混合的现实应用程序。

在您的应用程序，它是取决于您关于如何将与您的设计集成结果。 本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。 它是作业以使用此课程以增强混合的现实应用程序中获取的知识。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 304:人脸识别</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 HoloLens，您还可以应用到 Windows Mixed Reality 沉浸式 (VR) 耳机本课程中学习的内容。 因为沉浸式 (VR) 耳机不具有可访问照相机，您将需要连接到您的 PC 外部照相机。 按照课程时，您将看到说明您可能需要使用以支持沉浸式 (VR) 耳机的任何更改。

## <a name="prerequisites"></a>系统必备

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。 你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.

我们建议以下硬件和软件本课程：

- 开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md)
- [最新的 Windows 10 SDK](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- 一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式
- 照相机连接到您的 PC （适用于沉浸式头戴式开发）
- Internet 访问的 Azure 设置和人脸 API 检索

## <a name="before-you-start"></a>开始之前

1.  若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。
2.  设置和测试你 HoloLens。 如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。 

有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。

有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。

## <a name="chapter-1---the-azure-portal"></a>第 1 章-Azure 门户

若要使用*人脸 API*服务在 Azure 中，你将需要配置要成为可用于应用程序的服务的实例。

1.  首先，登录到[Azure 门户](https://portal.azure.com)。 

    > [!NOTE]
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**新建**在左上角，并搜索*人脸 API*，按**Enter**。

    ![搜索人脸 api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 单词**新建**可能已替换**创建资源**，较新的门户网站中。

3.  该新页面将提供的说明*人脸 API*服务。 在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。

    ![人脸 api 信息](images/AzureLabs-Lab4-02.png)

4.  一旦你单击**创建**:

    1. 插入此服务实例所需的名称。

    2. 选择一个订阅。

    3. 选择定价层适合你，如果这是首次创建*人脸 API 服务*，应可供你免费层 （名为 F0）。

    4. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。 

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. UWP 应用后，**人员 Maker**，更高版本，使用该位置需要使用美国西部。

    6. 您还需要确认你已了解的条款和条件应用于此服务。

    7. 选择**创建*。**

        ![创建人脸 api 服务](images/AzureLabs-Lab4-03.png)

5.  一旦你单击 **创建*** 必须要等待的时间来创建服务，这可能需要一分钟的时间。

6.  创建服务实例后，在门户中将显示一条通知。

    ![服务创建通知](images/AzureLabs-Lab4-04.png)

7.  单击通知以了解新的服务实例。

    ![请转到资源通知](images/AzureLabs-Lab4-05.png)

8.  准备就绪后，单击**转到资源**通知探索新的服务实例中的按钮。

    ![访问人脸 api 密钥](images/AzureLabs-Lab4-06.png)

9.  在本教程中，你的应用程序将需要对你的服务，是通过使用服务的订阅密钥进行调用。 从*快速入门*页上的你*人脸 API*服务，第一个点是为其编号为 1，*捕捉密钥。*

10. 上*服务*页上，选择任一蓝色**密钥**超链接 （如果已打开快速启动页），或**密钥**服务导航菜单中的链接 (位于左侧、 为由键图标)，以显示你的密钥。

    > [!NOTE] 
    > 请记下的任何一个密钥并保护它，因为稍后将需要它。

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>第 2 章-使用人员 Maker UWP 应用程序

请务必下载预生成的 UWP 应用程序调用[人员 Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)。 此应用不是本课程中，只是一个工具，可帮助您创建在 Azure 的条目，将依赖于更高版本的项目最终产品。

**人员 Maker**允许你创建 Azure 的条目，它们是与人员和人员组相关联。 应用程序会将所有所需的信息，然后更高版本来 FaceAPI，以识别其已添加人员人脸的格式。 

> [重要]**人员 Maker**使用一些基本的限制，来帮助确保不超过每分钟的服务调用数**免费订阅层**。 在顶部的绿色文本将变为红色并更新为活动时出现了限制;如果这种情况，只需等待应用程序 （它将等待，直到它接下来可以继续访问该人脸服务，可以再次使用它更新为在活动）。

此应用程序使用*Microsoft.ProjectOxford.Face*库，这样就可以进行完整的人脸 API 使用。 此库是可免费获得作为 NuGet 包。 有关详细信息，了解相关信息，以及类似，Api[请务必访问的 API 参考文章](https://docs.microsoft.com/azure/cognitive-services/face/apireference)。

> [!NOTE] 
> 这些是只是所需的步骤，说明如何执行这些操作是进一步文档。 **人员 Maker**应用将允许您为：
>
> - 创建*人员组*，后者由一组组成的多个用户想要将与之关联。 使用 Azure 帐户可以托管多个人员组。
>
> - 创建*人员*，这是一个人员组的成员。 每个人都有大量*人脸*与之关联的映像。
>
> -  将分配*人脸图像*到*人员*，以允许 Azure 人脸 API 服务以识别*人员*对应*人脸*。
>
> -  *训练*你*Azure 人脸 API 服务*。

注意，因此若要训练此应用程序中识别人，您需要十 （10） 特写照片的每个人员想要将添加到人员组。 Windows 10 网络摄像机，应用可以帮助你为将这些。 必须确保每张照片是清除 （避免模糊、 遮蔽，或使用者正在太远），与没有较大的图像文件大小 jpg 或 png 文件格式，具有照片**4MB**，和不少于**1KB**.

> [!NOTE]
> 在您按照本教程，请不要用于你自己的人脸的培训，如 HoloLens 时，您不能在您自己。 使用人脸的同事或人员的学生。

运行**人员 Maker**:

1.  打开**PersonMaker**文件夹并双击*PersonMaker 解决方案*以打开其与*Visual Studio*。

2.  一次*PersonMaker 解决方案*打开，请确保：

    1. *解决方案配置*设置为**调试**。

    2. *解决方案平台*设置为**x86**

    3. *目标平台*是**本地计算机**。

    4.  你还可能需要*还原 NuGet 包*(右键单击*解决方案*，然后选择**还原 NuGet 包**)。

3.  单击*本地计算机*和应用程序将启动。 注意，在较小屏幕上，所有内容可能不都会显示，尽管您可以滚动进一步向下键查看它。

    ![人员 maker 用户界面](images/AzureLabs-Lab4-07.png)

4.  插入您**Azure 身份验证密钥**，其中应包含，从你*人脸 API*服务在 Azure 中。

5.  插入：

    1. *ID*想要分配给*人员组*。 ID 必须为小写，且没有空格。 记下此 ID，因为它将在 Unity 项目中的更高版本所必需。
    2. *名称*想要分配给*人员组*（可以包含空格）。


6.  按**创建人员组**按钮。 下面的按钮应显示一条确认消息。

> [!NOTE]
> 如果有拒绝访问错误，检查设置为 Azure 服务的位置。 如上面所述，此应用专为美国西部。

> [!IMPORTANT]
> 你会注意到，您可以单击**提取已知组**按钮： 如果你已创建一个人使用，而不是创建一个新的组，并且想这是用于。 请注意，如果单击*创建人员组*与已知组，这还将获得一个组。

7.  插入*名称*的*人员*你想要创建。

    1. 单击**创建 Person**按钮。

    2. 下面的按钮应显示一条确认消息。

    3. 如果想要删除一个人之前已创建，你可以编写到文本框，并按名称**删除人**

8.  请确保你知道你想要添加到组的人员的照片十 （10） 的位置。

9.  按**创建和打开文件夹**到关联的人员的文件夹中打开 Windows 资源管理器。 在文件夹中添加十 （10） 映像。 这些必须属于*JPG*或*PNG*文件格式。

10. 单击**提交到 Azure**。 计数器将显示你的提交，完成后跟一条消息的状态。

11. 单击该计数器已完成并显示确认消息后**训练**来训练你的服务。

过程完成后，已准备好移动到 Unity。

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章 — 设置 Unity 项目

以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。

1.  打开*Unity*然后单击**新建**。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab4-08.png)

2.  现在，需要提供 Unity 项目的名称。 插入**MR_FaceRecognition**。 请确保项目类型设置为**3D**。 设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![提供新的 Unity 项目的详细信息。](images/AzureLabs-Lab4-09.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab4-10.png)

4.  接下来，请转到**文件 > 生成设置**，并切换到平台**通用 Windows 平台**，单击**切换平台**按钮。

    ![生成设置窗口中，切换到 UWP 的平台。](images/AzureLabs-Lab4-11.png)

5.  转到**文件 > 生成设置**并确保选中：

    1. **设备为目标**设置为**HoloLens**

        > 对于沉浸式耳机，设置**目标设备**到*任一设备*。

    2. **生成的类型**设置为**D3D**
    3. **SDK**设置为**最新安装**
    4. **Visual Studio 版本**设置为**最新安装**
    5. **生成并运行**设置为**本地计算机**
    6. 保存场景，并将其添加到生成。 

        1. 选择执行此**添加打开场景**。 保存窗口将显示。

            ![单击添加打开场景按钮](images/AzureLabs-Lab4-12.png)

        2. 选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![创建新的 scripts 文件夹](images/AzureLabs-Lab4-13.png)

        3. 打开新建**场景**文件夹，然后在**文件名**： 文本字段中，键入**FaceRecScene**，然后按**保存**。

            ![为新的场景提供一个名称。](images/AzureLabs-Lab4-14.png)

    7. 中的剩余设置，*生成设置*，应暂时保留为默认值。

6. 在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。 

    ![打开播放器设置。](images/AzureLabs-Lab4-15.png)

7. 在此面板中，需要验证几个设置：

    1. 在中**其他设置**选项卡：

        1. **脚本编写** **运行时版本**应**实验**（.NET 4.6 等效）。 此更改将触发需要重新启动编辑器。
        2. **脚本编写后端**应为 **.NET**
        3. **API 兼容性级别**应为 **.NET 4.6**

            ![更新其他设置。](images/AzureLabs-Lab4-16.png)
      
    2. 内**发布设置**选项卡上，在**功能**，检查：

        - **InternetClient**
        - **Webcam**

            ![正在更新的发布设置。](images/AzureLabs-Lab4-17.png)

    3. 中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。

        ![更新的 X R 设置。](images/AzureLabs-Lab4-18.png)

8.  回到*生成设置*， **UnityC#项目**不再灰显; 选中它旁边的复选框。 
9.  关闭生成设置窗口。
10. 保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。

## <a name="chapter-4---main-camera-setup"></a>第 4 章-主照相机设置

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)，并将其导入项目中，作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)。 请注意，此包还包含在导入*Newtonsoft DLL*中所述[第 5 章：](#chapter-5--import-the-newtonsoft.json-library)。 与此导入，您可以继续从[第 6 章](#chapter-6-create-the-faceanalysis-class)。

1.  在中*层次结构*面板中，选择**Main Camera**。

2.  选择后，你将能够看到的所有组件**Main Camera**中*检查器面板*。

    1. **相机对象**必须命名为**Main Camera** （请注意拼写 ！）

    2. Main Camera**标记**必须设置为**MainCamera** （请注意拼写 ！）

    3. 请确保**转换位置**设置为**0，0，0**

    4. 设置**清除标志**到**纯色**

    5. 设置**背景**照相机组件到色**黑色、 Alpha 0 (十六进制代码: #00000000)**

        ![设置照相机组件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>第 5 章-将 Newtonsoft.Json 库导入

> [!IMPORTANT]
> 如果在中导入.unitypackage'[最后一章](#chapter-4--main-camera-setup)，可以跳过这一章。

若要帮助您反序列化和序列化对象接收和发送到机器人服务需要下载*Newtonsoft.Json*库。 将查找兼容的版本已具有正确的 Unity 文件夹结构中组织[Unity 包文件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)。 

若要导入的库：

1.  下载 Unity 包。
2.  单击**资产**，**导入包**，**自定义包**。

    ![将 Newtonsoft.Json 库导入](images/AzureLabs-Lab4-20.png)

3.  查找已下载 Unity 包，然后单击打开。
4.  请确保包的所有组件都勾选，单击**导入**。

    ![将 Newtonsoft.Json 库导入](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>章 6-创建 FaceAnalysis 类

FaceAnalysis 类旨在托管你的 Azure 人脸识别服务通信所需的方法。 

- 发送后该服务捕获映像，它将分析它，并识别，人脸和确定是否任何属于已知的人员。 
- 如果找到一个已知的人，则此类将显示其名称为场景中的 UI 文本。

若要创建*FaceAnalysis*类：

 1. 在中右击*Assets 文件夹*位于项目面板，然后单击**创建** > **文件夹**。 将该文件夹**脚本**。 

    ![创建 FaceAnalysis 类。](images/AzureLabs-Lab4-22.png)

2.  双击刚创建的文件夹，以将其打开。 
3.  在文件夹中，右键单击，然后单击**创建** >   **C#脚本**。 调用脚本*FaceAnalysis*。 
4.  双击新*FaceAnalysis*脚本以使用 Visual Studio 2017 中打开它。
5.  输入以下命名空间上述*FaceAnalysis*类：

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  现在需要添加的所有对象将用于 deserialising。 这些对象需要添加**外部**的*FaceAnalysis* （下方底部大括号） 的脚本。 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. *Start （)* 并*update （)* 方法不会使用，因此现在将其删除。 

8.  内部*FaceAnalysis*类中，添加以下变量：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > 替换**键**并**personGroupId**你的服务密钥和之前创建的组的 Id。

9.  添加*Awake()* 方法，initialises 类，添加*ImageCapture*到 Main Camera 类并调用标签创建方法：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. 添加*CreateLabel()* 方法，用于创建*标签*对象以显示分析结果：

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. 添加*DetectFacesFromImage()* 并*GetImageAsByteArray()* 方法。 前者将请求要在已提交的图中，检测任何可能的人脸，而后者是必须要捕获的映像转换为字节数组的人脸识别服务：

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. 添加*IdentifyFaces()* 方法，请求*人脸识别服务*来标识以前提交的图像中检测到任何已知人脸。 该请求将返回的 id 标识的用户而不是名称为：

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. 添加*GetPerson()* 方法。 通过提供用户 id，此方法然后请求*人脸识别服务*返回标识的人员的姓名：

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  请记住**保存**之前追溯到 Unity 编辑器中所做的更改。
15.  在 Unity 编辑器中，将 FaceAnalysis 脚本从项目面板中的 Scripts 文件夹拖动到中的 Main Camera 对象*层次结构面板*。 新脚本组件将因此添加到 Main Camera。 

![将放置到主照相机上 FaceAnalysis](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>章 7-创建 ImageCapture 类

目的*ImageCapture*类是托管通信所需的方法您*Azure 人脸识别服务*分析将捕获，请确定中它的人脸的图像和确定它是否属于已知的人员。 如果找到一个已知的人，则此类将显示其名称为场景中的 UI 文本。

若要创建*ImageCapture*类：
 
1.  内右击**脚本**文件夹之前，创建，然后单击**创建**，  **C#脚本**。 调用脚本*ImageCapture*。 
2.  双击新*ImageCapture*脚本以使用 Visual Studio 2017 中打开它。
3.  输入上面 ImageCapture 类的以下命名空间：

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  内部*ImageCapture*类中，添加以下变量：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  添加*Awake()* 并*start （)* 初始化类和允许 HoloLens 以捕获用户的操作所需的方法：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  添加*TapHandler()* 用户执行时调用*点击*手势：

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  添加*ExecuteImageCaptureAndAnalysis()* 方法，它将开始捕获映像的过程：

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  添加照片捕获进程完成时，将调用处理程序：

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. 请记住**保存**之前追溯到 Unity 编辑器中所做的更改。

## <a name="chapter-8---building-the-solution"></a>第 8 章 — 构建解决方案

若要执行全面测试您的应用程序将需要旁加载它到在 HoloLens 上。

执行操作之前，请确保：

-   第 3 章中所述的所有设置都正确都设置。 
-   该脚本*FaceAnalysis*附加到 Main Camera 对象。 
-   这两个**身份验证密钥**并**组 Id**中设置*FaceAnalysis*脚本。

这为你指出现在即可生成解决方案。 生成解决方案之后, 你将准备好部署应用程序。

若要开始生成过程：

1.  通过在文件中，单击保存当前场景。
2.  转到文件，生成设置，单击添加打开场景。
3.  请确保为时钟周期 UnityC#项目。

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab4-24.png)

4.  按生成。 在此过程中，Unity 将启动文件资源管理器窗口中，需要创建，然后选择要生成该应用程序的文件夹。 在 Unity 项目中，现在，创建该文件夹，并对其应用程序。 然后应用文件夹后，按选择文件夹。 
5.  Unity 将开始构建您的项目，到应用程序文件夹。 
6.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开文件资源管理器窗口在生成的位置。

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab4-25.png)

7.  打开应用程序文件夹，并打开新的项目解决方案 （如上面 MR_FaceRecognition.sln 所示）。


## <a name="chapter-9---deploying-your-application"></a>第 9 章 — 部署应用程序

若要部署在 HoloLens 上：

1.  你将 （适用于远程部署），需要在 HoloLens IP 地址，以确保你 HoloLens 处于**开发人员模式**。 要实现此目的，请执行以下操作：

    1. 戴上您 HoloLens，同时打开**设置**。
    2. 转到**网络和 Internet > 的 Wi-fi > 高级选项**
    3. 请注意**IPv4**地址。
    4. 接下来，导航回到**设置**，然后**更新和安全 > 适用于开发人员** 
    5. 设置开发人员模式。

2.  导航到新的 Unity 生成 (*应用程序*文件夹)，然后打开解决方案文件与*Visual Studio*。
3.  在解决方案配置中，选择**调试**。
4.  在解决方案平台中，选择**x86**，**远程计算机**。 

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab4-26.png)
 
5.  转到**生成菜单**，然后单击**部署解决方案**旁, 加载到你 HoloLens 应用程序。
6.  在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！

> [!NOTE]
> 若要将部署到沉浸式头戴式耳机，设置**解决方案平台**到*本地计算机*，并设置**配置**到*调试*，与*x86*作为**平台**。 然后将其部署到本地计算机，使用**生成菜单**，选择*部署解决方案*。 


## <a name="chapter-10---using-the-application"></a>第 10 章 — 使用应用程序

1.  戴上 HoloLens，启动应用。
2.  看一看使用注册的人员*人脸 API*。 请确保：

    -  人脸不是太遥远和清楚地显示
    -  环境照明不是太深

3.  使用手势来捕获此人的照片。
4.  等待应用程序将分析请求发送和接收响应。
5.  如果已成功识别用户，该用户的名称将显示为 UI 文本。
6.  可以重复使用每隔几秒钟的点击动作在捕获过程。

## <a name="your-finished-azure-face-api-application"></a>完成的 Azure 人脸 API 的应用程序

祝贺你，构建利用 Azure 人脸识别服务来检测对映像中的人脸并识别任何已知的人脸的混合的现实应用。

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

**Azure 人脸 API**是功能强大，足以检测到单个映像中的最多 64 个的人脸。 扩展应用程序，以便它可以识别两个或三个人脸，在许多其他人之间。

### <a name="exercise-2"></a>练习 2

**Azure 人脸 API**它还可以提供返回所有种类的属性信息。 将此集成到应用程序。 这可能是更有趣的内容，再加上[情感 API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)。
