---
title: MR 和 Azure 302-计算机视觉
description: 完成此课程以了解如何识别中提供的映像，在混合的现实应用程序中使用 Azure 计算机视觉的可视内容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 计算机视觉、 沉浸式、 hololens、 vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590172"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR 和 Azure 302:计算机视觉

在本课程中，您将学习如何识别可视内容中提供的映像，在混合的现实应用程序中使用 Azure 计算机视觉功能。

识别结果将显示为描述性标记。 可用于此服务而无需定型的机器学习模型。 如果您的实现需要定型的机器学习模型，请参阅[MR 和 Azure 302b](mr-azure-302b.md)。

![实验结果](images/AzureLabs-Lab2-000.png)

Microsoft 计算机视觉是一组 Api，可让开发人员提供图像处理和分析 （并返回信息），所有这些操作通过在云中使用高级的算法。 开发人员上传图像或图像 URL 和 Microsoft 计算机视觉 API 算法分析视觉内容中，基于所选用户，然后可以返回的信息，请输入包括标识的类型和质量的图像的检测人脸 （返回其坐标），并标记，或对图像分类。 有关详细信息，请访问[Azure 计算机视觉 API 页](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。

已完成本课程，您将具有混合的现实 HoloLens 应用程序，将能够执行以下操作：

1.  使用手势，HoloLens 的照相机将捕获映像。
2.  图像将发送到 Azure 的计算机视觉 API 服务。 
3.  将在 Unity 场景中定位的简单用户界面组中列出识别的对象。

在您的应用程序，它是取决于您关于如何将与您的设计集成结果。 本课程旨在教您如何将 Azure 服务集成与你的 Unity 项目。 它是作业以使用此课程以增强混合的现实应用程序中获取的知识。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 302:计算机视觉</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 HoloLens，您还可以应用到 Windows Mixed Reality 沉浸式 (VR) 耳机本课程中学习的内容。 因为沉浸式 (VR) 耳机不具有可访问照相机，您将需要连接到您的 PC 外部照相机。 按照课程时，您将看到说明您可能需要使用以支持沉浸式 (VR) 耳机的任何更改。

## <a name="prerequisites"></a>系统必备

> [!NOTE]
> 本教程专为开发人员已基本熟悉 Unity 和C#。 此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。 你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.

我们建议以下硬件和软件本课程：

- 开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发
- [Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式
- 照相机连接到您的 PC （适用于沉浸式头戴式开发）
- Internet 访问的 Azure 设置和计算机视觉 API 检索

## <a name="before-you-start"></a>开始之前

1.  若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。
2.  设置和测试你 HoloLens。 如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。 

有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。

有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。

## <a name="chapter-1--the-azure-portal"></a>第 1 章 – Azure 门户

若要使用*计算机视觉 API*服务在 Azure 中，你将需要配置要成为可用于应用程序的服务的实例。

1.  首先，登录到[Azure 门户](https://portal.azure.com)。 

    > [!NOTE]
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**新建**在左上角，并搜索*计算机视觉 API*，然后单击**Enter**。

    ![在 Azure 中创建新的资源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 单词**新建**可能已替换**创建资源**，较新的门户网站中。
 
3.  该新页面将提供的说明*计算机视觉 API*服务。 在左下角此页上，选择**创建**按钮，以创建与此服务的关联。

    ![有关计算机视觉 api 服务](images/AzureLabs-Lab2-01.png)
 
4.  一旦你单击**创建**:

    1. 插入所需**名称**此服务实例。
    2. 选择**订阅**。
    3. 选择**定价层**适合您，如果这是首次创建*计算机视觉 API*服务，应可供你免费层 （名为 F0）。
    4. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。 

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. （如果要创建新的资源组） 确定你的资源组的位置。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。

    6. 您还需要确认你已了解的条款和条件应用于此服务。
    7. 单击创建。

        ![服务创建信息](images/AzureLabs-Lab2-02.png)

5.  一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。
6.  创建服务实例后，在门户中将显示一条通知。

    ![请参阅您的新服务的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  单击通知以了解新的服务实例。 

    ![选择转到资源按钮。](images/AzureLabs-Lab2-04.png)
 
8. 单击**转到资源**通知探索新的服务实例中的按钮。 你将转到新的计算机视觉 API 服务实例。 

    ![新的计算机视觉 API 服务](images/AzureLabs-Lab2-05.png)
 
9.  在本教程中，你的应用程序将需要对你的服务，通过使用服务的订阅密钥来完成进行调用。
10. 从*快速入门*页上的你*计算机视觉 API*服务，，请导航到的第一步*捕捉密钥*，然后单击**密钥**(也可以在此通过单击蓝色超链接密钥，位于服务导航菜单中，由密钥图标表示）。 此时会显示你的服务*密钥*。
11. 需要一份某个显示的密钥，因为你将需要此更高版本中您的项目。 

12. 返回到*快速入门*页上，并从中提取你的终结点。 请注意您可能会有所不同，具体取决于你的区域 (这是，如果需要更高版本对代码进行更改)。 获取供以后使用此终结点的副本：

    ![新的计算机视觉 API 服务](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > 你可以检查各个终结点是什么[此处](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。 

## <a name="chapter-2--set-up-the-unity-project"></a>第 2 章-设置 Unity 项目

以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。

1.  打开*Unity*然后单击**新建**。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab2-06.png)

2.  现在，需要提供 Unity 项目的名称。 插入**MR_ComputerVision**。 请确保项目类型设置为**3D**。 设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![提供新的 Unity 项目的详细信息。](images/AzureLabs-Lab2-07.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab2-08.png)

4.  接下来，请转到**文件 > 生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。

    ![生成设置窗口中，切换到 UWP 的平台。](images/AzureLabs-Lab2-10.png)

5.  在仍处于**文件 > 生成设置**并确保选中：

    1. **设备为目标**设置为**HoloLens**

        > 对于沉浸式耳机，设置**目标设备**到*任一设备*。

    2. **生成的类型**设置为**D3D**
    3. **SDK**设置为**最新安装**
    4. **Visual Studio 版本**设置为**最新安装**
    5. **生成并运行**设置为**本地计算机**
    6. 保存场景，并将其添加到生成。

        1. 选择执行此**添加打开场景**。 保存窗口将显示。
        
            ![单击添加打开场景按钮](images/AzureLabs-Lab2-11.png)

        2. 创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![创建新的 scripts 文件夹](images/AzureLabs-Lab2-12.png)

        3. 打开新建**场景**文件夹，然后在*文件名*： 文本字段中，键入**MR_ComputerVisionScene**，然后单击**保存**.

            ![为新的场景提供一个名称。](images/AzureLabs-Lab2-13.png)

            > 请注意，必须将保存您的 Unity 场景中*资产*文件夹中，因为它们必须与 Unity 项目相关联。 创建场景文件夹 （和其他类似的文件夹） 是用于结构化的 Unity 项目的典型方式。

    7. 中的剩余设置，*生成设置*，应暂时保留为默认值。

6. 在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。 

    ![打开播放器设置。](images/AzureLabs-Lab2-14.png)

7. 在此面板中，需要验证几个设置：

    1. 在中**其他设置**选项卡：

        1. **脚本运行时版本**应**稳定**（.NET 3.5 等效）。
        2. **脚本编写后端**应为 **.NET**
        3. **API 兼容性级别**应为 **.NET 4.6**

            ![更新其他设置。](images/AzureLabs-Lab2-15.png)
      
    2. 内**发布设置**选项卡上，在**功能**，检查：

        1. **InternetClient**
        2. **Webcam**

            ![正在更新的发布设置。](images/AzureLabs-Lab2-16.png)

    3. 中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。

        ![更新的 X R 设置。](images/AzureLabs-Lab2-17.png)

8.  回到*生成设置* _Unity C#_ 项目不再灰显; 选中它旁边的复选框。 
9.  关闭生成设置窗口。
10. 保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。

## <a name="chapter-3--main-camera-setup"></a>第 3 章 – 主照相机设置

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)，将其导入项目中，作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 5 章：](#chapter-5--create-the-resultslabel-class)。

1.  在中*层次结构面板*，选择**Main Camera**。 
2.  选择后，你将能够看到的所有组件**Main Camera**中*检查器面板*。

    1. **相机对象**必须命名为**Main Camera** （请注意拼写 ！）
    2. Main Camera**标记**必须设置为**MainCamera** （请注意拼写 ！）
    3. 请确保**转换位置**设置为**0，0，0**
    4. 设置**清除标志**到**纯色**（忽略这的沉浸式头戴式耳机）。
    5. 设置**背景**照相机组件到色**黑色、 Alpha 0 (十六进制代码: #00000000)** （忽略这的沉浸式头戴式耳机）。

        ![更新相机组件。](images/AzureLabs-Lab2-18.png)
 
3.  接下来，需要创建附加到一个简单的"游标"对象**Main Camera**，这将帮助你放置图像分析输出运行该应用程序。 此游标将确定摄像机焦点的中心点。

若要创建该游标：

1.  在中*层次结构面板*，右键单击**Main Camera**。 下**3D 物体**，单击**球体**。

    ![选择光标对象。](images/AzureLabs-Lab2-19.png)
 
2.  重命名**球体**到**光标**（双击光标对象或与所选对象按 F2 键盘按钮），并确保它位于作为子级**Main Camera**.

3.  在中*层次结构面板*，在单击鼠标左键**光标**。 选择光标，调整中的以下变量*检查器面板*:

    1. 设置*转换位置*到**0，0，5**
    2. 设置*规模*到**0.02、 0.02、 0.02**

        ![更新的转换位置和小数位数。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>第 4 章-设置标签系统

该映像后使用 HoloLens 的照相机中捕获了映像，将发送到您*Azure 计算机视觉 API*服务实例以进行分析。 

该分析的结果将是一系列已识别的对象调用**标记**。 

将使用标签 （作为全局空间中三维文字），要在拍摄照片的位置显示这些标记。

以下步骤将演示如何设置**标签**对象。

1.  在层次结构窗格中 （位置并不重要此时），在任意位置右击**3D 物体**，添加**三维文字**。 其命名为**LabelText**。

    ![创建三维文本对象。](images/AzureLabs-Lab2-21.png)
 
2.  在中*层次结构面板*，在单击鼠标左键**LabelText**。 与**LabelText**选择，调整中的以下变量*检查器面板*:

    1. 设置**位置**到**0,0,0**
    2. 设置**规模**到**0.01，0.01，0.01**
    3. 组件中**文本 Mesh**:
    4. 替换中的所有文本**文本**，使用"..."        
    5. 设置**定位点**到**中间 Center**
    6. 设置**对齐**到**Center**
    7. 设置**选项卡大小**到**4**
    8. 设置**字号**到**50**
    9. 设置**颜色**到 **#FFFFFFFF**

    ![文本组件](images/AzureLabs-Lab2-21-5.png)

3.  拖动**LabelText**从*层次结构面板*，为*资产文件夹*，在中*项目面板*。 这将使**LabelText**预设，因此它可以在代码中实例化。

    ![创建 LabelText 对象的预设。](images/AzureLabs-Lab2-22.png)
 
4.  应删除**LabelText**从*层次结构面板*，以便打开场景中将不会显示。 因为它现在是预设，您将从资产文件夹调用的单独实例，没有无需将其保持在场景。 
5.  中的最后一个对象结构*层次结构面板*应类似于下图中所示：

    ![层次结构面板的最终结构。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>第 5 章-创建 ResultsLabel 类

您需要创建的第一个脚本是*ResultsLabel*类，该类负责以下： 

- 在适当的世界空间中，相对于照相机的位置中创建标签。
- 显示从映像解放标记。

若要创建此类： 

1.  在中右击*项目面板*，然后**创建 > 文件夹**。 将文件夹命名为**脚本**。 

    ![创建脚本的文件夹。](images/AzureLabs-Lab2-24.png)

2.  与**脚本**文件夹中创建，双击它打开。 然后在该文件夹，右键单击，并选择**创建 >** 然后**C#脚本**。 脚本命名为*ResultsLabel*。 

3.  双击新*ResultsLabel*脚本以将其与打开**Visual Studio**。

4.  在类中插入下面的代码*ResultsLabel*类：

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。
7.  回到*Unity 编辑器*，单击并拖动*ResultsLabel*类**脚本**文件夹**Main Camera**中对象*层次结构面板*。
8.  单击**Main Camera**并查看*检查器面板*。

您将注意到，您只需拖放到相机的脚本，还有两个字段：**游标**并**标签 Prefab**。

9.  拖动对象调用**游标**从*层次结构面板*到名为槽**游标**，如下图中所示。
10. 拖动对象调用**LabelText**从*Assets 文件夹*中*项目面板*到名为槽**标签 Prefab**，如中所示下图所示。 

    ![设置在 Unity 中的引用目标。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>第 6 章-创建 ImageCapture 类

要创建的下一步类是*ImageCapture*类。 此类负责：

-   捕获映像使用 HoloLens 相机并将其存储在应用程序文件夹中。
-   捕获来自用户的点击手势。

若要创建此类： 

1.  转到**脚本**之前创建的文件夹。 
2.  在文件夹中，右键单击**创建 >C#脚本**。 调用脚本*ImageCapture*。 
3.  双击新*ImageCapture*脚本以将其与打开**Visual Studio**。
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  然后添加以下变量内的*ImageCapture*类，更高版本*start （)* 方法：

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount**变量将存储捕获来自用户的点击手势的号。 此编号使用命名的捕获的映像中。

6.  为代码*Awake()* 并*start （)* 方法现在需要添加。 类初始化时将会调用：

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  实现的点击动作时将调用的处理程序。 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
*TapHandler()* 方法递增捕获来自用户的点击数，并使用当前光标位置以确定要将新的标签位置。

然后，此方法调用*ExecuteImageCaptureAndAnalysis()* 方法开始此应用程序的核心功能。

8.  一旦已捕获并存储映像，将调用以下处理程序。 如果该过程成功，将结果传递给*VisionManager* （即你尚未创建） 以进行分析。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  然后添加该应用程序使用启动映像捕获过程并存储映像的方法。

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> 此时你会注意到出现在错误*Unity 编辑器控制台面板*。 这是因为该代码引用*VisionManager*将在下一章中创建的类。

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>第 7 章 – 对 Azure 和图像分析的调用

若要创建所需的最后一个脚本是*VisionManager*类。 

此类负责：

-   正在加载最新的映像捕获为一个字节数组。
-   发送到的字节数组你*Azure 计算机视觉 API*服务实例以进行分析。
-   接收响应以 JSON 字符串。
-   反序列化响应并将传递到生成的标记*ResultsLabel*类。
 
若要创建此类：

1.  双击**脚本**文件夹，将其打开。 
2.  内右击**脚本**文件夹中，单击**创建 >C#脚本**。 脚本命名为*VisionManager*。 
3.  双击要使用 Visual Studio 中打开的新脚本。
4.  更新命名空间，如下所示，在顶部相同*VisionManager*类：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  在脚本顶部*内* *VisionManager*类 (上面*start （)* 方法)，现在需要创建两个*类*，将表示 Azure 的反序列化的 JSON 响应：

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > *TagData*并*AnalysedObject*类都必须具有 *[System.Serializable]* 的声明，以便能够使用 Unity 进行反序列化之前添加属性库。

6.  在 VisionManager 类中，应添加以下变量：

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > 请确保插入你**身份验证密钥**成**authorizationKey**变量。 你将已记下你**身份验证密钥**在本课程中，开头[第 1 章](#chapter-1--the-azure-portal)。

    > [!WARNING] 
    > **VisionAnalysisEndpoint**变量可能不同于在此示例中指定。 **西部-我们**严格地指的是为美国西部区域创建的服务实例。 更新此与您[终结点 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); 此处的一些示例可能如下所示的是：
    > - 欧洲西部： `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 亚洲东南部： `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 澳大利亚东部： `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Awake 现在需要添加代码。 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  接下来，添加协同程序 （使用其下方的静态流方法），将获取由捕获映像的分析结果*ImageCapture*类。 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。
10. 返回在 Unity 编辑器中，单击并拖动*VisionManager*并*ImageCapture*类**脚本**文件夹到**Main Camera**中的对象*层次结构面板*。 

## <a name="chapter-8--before-building"></a>第 8 章 – 生成前

若要执行全面测试您的应用程序将需要旁加载它到在 HoloLens 上。
执行操作之前，请确保：

-   中所述的所有设置[第 2 章](#chapter-2--set-up-the-unity-project)正确设置。 
-   所有脚本都附加到**Main Camera**对象。 
-   中的所有字段*主相机检查器面板*正确分配。
-   请确保插入你**身份验证密钥**成**authorizationKey**变量。
-   确保具有还检查你的终结点您*VisionManager*脚本，并与对齐*你*区域 (本文档使用*西-我们*默认情况下)。

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>章 9 – 生成 UWP 解决方案和旁加载应用程序
此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。

1.  导航到*生成设置* - **文件 > 生成设置...**
2.  从*生成设置*窗口中，单击**生成**。

    ![从 Unity 构建应用程序](images/AzureLabs-Lab2-26.png)

3.  如果尚不存在，则勾选**UnityC#项目**。
4.  单击“生成” 。 将启动 unity*文件资源管理器*窗口中，需要创建，然后选择要生成该应用程序的文件夹。 现在，创建该文件夹并将其命名*应用*。 然后使用*应用程序*文件夹选择，按**选择文件夹**。 
5.  Unity 将开始构建您的项目*应用*文件夹。 
6.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开*文件资源管理器*窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。

## <a name="chapter-10--deploy-to-hololens"></a>第 10 章将部署到 HoloLens

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

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab2-27.png)
 
5.  转到**生成菜单**，然后单击**部署解决方案**旁, 加载到你 HoloLens 应用程序。
6.  在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！

> [!NOTE]
> 若要将部署到沉浸式头戴式耳机，设置**解决方案平台**到*本地计算机*，并设置**配置**到*调试*，与*x86*作为**平台**。 然后将其部署到本地计算机，使用**生成菜单**，选择*部署解决方案*。 

## <a name="your-finished-computer-vision-api-application"></a>完成的计算机视觉 API 的应用程序

祝贺你，构建利用 Azure 计算机视觉 API 能够识别现实世界对象，并显示的内容出现的置信度的混合的现实应用。

![实验结果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

正如您使用过*标记*参数 (如内*终结点*中使用*VisionManager*)，扩展应用程序以检测其他信息; 我们来看一下有权访问的其他参数[此处](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。

### <a name="exercise-2"></a>练习 2

显示返回的 Azure 数据，以更便于交谈，和可读的方式，可能隐藏的数字。 像智能机器人应用程序可能会对用户说话。
