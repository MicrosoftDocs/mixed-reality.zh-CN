---
title: MR 和 Azure 301-语言翻译
description: 完成此课程以了解如何实现 Azure 文本翻译 API 混合的现实应用程序中。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 文本翻译，沉浸式、 hololens、 vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592739"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR 和 Azure 301:语言翻译

在本课程中，您将学习如何将翻译功能添加到文本翻译 api 使用 Azure 认知服务的混合的现实应用程序。

![最终产品](images/AzureLabs-Lab1-00.png)

文本翻译 API 是翻译服务最后一种接近实时的速度。 该服务是基于云的并使用 REST API 调用，可以使应用程序使用的神经网络机器翻译技术翻译为其他语言的文本。 有关详细信息，请访问[Azure 文本翻译 API 页](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。

完成本课程时，之后您将拥有一个混合的现实应用程序，将能够执行以下操作：

1.  用户将连接到沉浸式的 (VR) 耳机式麦克风 （或 HoloLens 内置麦克风） 进行朗读。
2.  应用程序将捕获听写，并将其发送到 Azure 文本翻译 API。
3.  翻译结果将显示在 Unity 场景中的简单用户界面组。

本课程将介绍如何将结果从 Translator 服务到基于 Unity 的示例应用程序。 它将取决于您要应用于您可能要构建一个自定义应用程序的这些概念。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> MR 和 Azure 301:语言翻译</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。 按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。 使用 HoloLens，您可能注意到某些 echo 语音捕获过程。

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
- 一组的耳机使用内置的麦克风 （如果耳机没有内置的麦克风和扬声器）
- 用于 Azure 的安装程序和转换检索 Internet 访问权限

## <a name="before-you-start"></a>开始之前

- 若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。
- 在本教程中的代码将允许您记录从默认麦克风设备连接到您的 PC。 请确保默认麦克风设备设置为你打算使用捕获您的声音的设备。
- 若要允许您的 PC 以启用听写，请转到**设置 > 隐私 > 语音，墨迹书写和键入**，然后选择按钮**启用语音服务和键入建议**。
- 如果您使用的麦克风和耳机连接到 （或内置于） 将耳机，请确保选择"当我 wear 我耳机时，切换到耳机式麦克风"中打开**设置 > 混合现实 > 音频和语音**。

   ![混合的现实设置](images/AzureLabs-Lab1-00-5.png)

   ![麦克风设置](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> 请注意，如果你正在开发为此实验室的沉浸式头戴式耳机，可能会遇到音频输出设备问题。 这是 unity 的因为 Unity，在更高版本 (Unity 2018.2) 中已修复的问题。 此问题可防止 Unity 在运行时更改默认音频输出设备。 来解决，确保您已完成上述步骤，和关闭并重新打开编辑器中，当此问题提供本身。

## <a name="chapter-1--the-azure-portal"></a>第 1 章 – Azure 门户

若要使用 Azure 翻译 API，你需要配置要成为可用于应用程序的服务的实例。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果你还没有 Azure 帐户，你需要创建一个。 如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。

2.  你登录后，单击**新建**右上左角并搜索"文本翻译 API。" 选择**输入**。

    ![新的资源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 单词**新建**可能已替换**创建资源**，较新的门户网站中。

3.  该新页面将提供的说明*文本翻译 API*服务。 在左下角此页上，选择**创建**按钮，以创建与此关联服务。

    ![Translator 文本 API 服务创建](images/AzureLabs-Lab1-03.png)

4.  一旦你单击**创建**:

    1. 插入所需**名称**此服务实例。
    2. 选择相应**订阅**。
    3. 选择**定价层**适合您，如果这是第一个时间来创建*Translator 文本服务*，应可供你免费层 （名为 F0）。
    4. 选择**资源组**或新建一个。 资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。 建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些实验室））。

        > 如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 确定**位置**为资源组 （如果要创建新的资源组）。 理想情况下，则位置应为该应用程序将运行的区域中。 某些 Azure 资产在特定区域才可用。
    6. 您还需要确认你已了解的条款和条件应用于此服务。
    7. 选择“创建”。

        ![选择创建按钮。](images/AzureLabs-Lab1-04.png)

5.  一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。
6.  创建服务实例后，在门户中将显示一条通知。 

    ![Azure 服务创建通知](images/AzureLabs-Lab1-05.png)

7.  单击通知以了解新的服务实例。 

    ![请转到资源弹出窗口。](images/AzureLabs-Lab1-06.png)

8.  单击**转到资源**通知探索新的服务实例中的按钮。 你将转到新的翻译文本 API 服务实例。 

    ![Translator 文本 API 服务页](images/AzureLabs-Lab1-07.png)

9.  在本教程中，你的应用程序将需要对你的服务，通过使用服务的订阅密钥来完成进行调用。 
10. 从*快速入门*页你*文本翻译*服务中，导航到的第一步*捕捉密钥*，然后单击**密钥**（也可以此外实现此目的通过单击蓝色超链接密钥，位于服务导航菜单中，由密钥图标表示）。 此时会显示你的服务*密钥*。
11. 需要一份某个显示的密钥，因为你将需要此更高版本中您的项目。 

## <a name="chapter-2--set-up-the-unity-project"></a>第 2 章-设置 Unity 项目

设置和测试您的混合的现实沉浸式头戴式。

> [!NOTE]
> 不需要此课程运动控制器。 如果需要支持沉浸式头戴式设置，请[请按照下列步骤](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。

以下是一组典型使用混合现实进行开发，在这种情况下，是很好的其他项目模板：

1.  打开*Unity*然后单击**新建**。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab1-08.png)

2.  现在，需要提供 Unity 项目的名称。 插入**MR_Translation**。 请确保项目类型设置为**3D**。 设置*位置*到适合于您的某个位置 （请记住，更接近于根目录是更好）。 然后，单击**创建项目**。

    ![提供新的 Unity 项目的详细信息。](images/AzureLabs-Lab1-09.png)

3.  使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。 转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。 更改**外部脚本编辑器**到**Visual Studio 2017**。 关闭**首选项**窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab1-10.png)

4.  接下来，请转到**文件 > 生成设置**，并切换到平台**通用 Windows 平台**，单击**切换平台**按钮。

    ![生成设置窗口中，切换到 UWP 的平台。](images/AzureLabs-Lab1-11.png)

5.  转到**文件 > 生成设置**并确保选中：

    1. **设备为目标**设置为**任一设备**。

        > 对于 Microsoft HoloLens**目标设备**到*HoloLens*。

    2. **生成的类型**设置为**D3D**
    3. **SDK**设置为**最新安装**
    4. **Visual Studio 版本**设置为**最新安装**
    5. **生成并运行**设置为**本地计算机**
    6. 保存场景，并将其添加到生成。

        1. 选择执行此**添加打开场景**。 保存窗口将显示。

            ![单击添加打开场景按钮](images/AzureLabs-Lab1-12.png)

        2. 创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。

            ![创建新的 scripts 文件夹](images/AzureLabs-Lab1-13.png)

        3. 打开新建**场景**文件夹，然后在*文件名*： 文本字段中，键入**MR_TranslationScene**，然后按**保存**。

            ![为新的场景提供一个名称。](images/AzureLabs-Lab1-14.png)

            > 请注意，必须将保存您的 Unity 场景中*资产*文件夹中，因为它们必须与 Unity 项目相关联。 创建场景文件夹 （和其他类似的文件夹） 是用于结构化的 Unity 项目的典型方式。

    7. 中的剩余设置，*生成设置*，应暂时保留为默认值。

6. 在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。 

    ![打开播放器设置。](images/AzureLabs-Lab1-15.png)

7. 在此面板中，需要验证几个设置：

    1. 在中**其他设置**选项卡：

        1. **脚本运行时版本**应**稳定**（.NET 3.5 等效）。
        2. **脚本编写后端**应为 **.NET**
        3. **API 兼容性级别**应为 **.NET 4.6**

            ![更新其他设置。](images/AzureLabs-Lab1-16.png)
      
    2. 内**发布设置**选项卡上，在**功能**，检查：

        1. **InternetClient**
        2. **Microphone**

            ![正在更新的发布设置。](images/AzureLabs-Lab1-17.png)

    3. 中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。

        ![更新的 X R 设置。](images/AzureLabs-Lab1-18.png)

8.  回到**生成设置**， *UnityC#项目*不再灰显; 选中它旁边的复选框。 
9.  关闭生成设置窗口。
10. 保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。

## <a name="chapter-3--main-camera-setup"></a>第 3 章 – 主照相机设置

> [!IMPORTANT]
> 如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)，将其导入项目中，作为[ *自定义包*](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 5 章：](#chapter-5--create-the-results-class)。 仍需要创建一个 Unity 项目。

1.  在中*层次结构面板*，您会发现一个名为对象**Main Camera**，"内部"应用程序后，此对象表示"head"的观点。
2.  准备好 Unity 仪表板中，选择**主相机 GameObject**。 您会注意*检查器面板*（通常右侧，在仪表板中找到） 将显示的各种组件*GameObject*，与*转换*在顶部后, 接*照相机*，而另一些其他组件。 你将需要重置的转换的 Main Camera，使其正确定位。
3.  若要执行此操作，请选择**齿轮**旁的摄像机*转换*组件，并选择**重置**。 

    ![重置 Main Camera 转换。](images/AzureLabs-Lab1-19.png)
 
4.  *转换*组件应如下所示：

    1. *位置*设置为**0，0，0**
    2. *旋转*设置为**0，0，0**
    3. 并*规模*设置为**1，1，1**

        ![转换用于相机的信息](images/AzureLabs-Lab1-20.png)

5.  接下来，使用**Main Camera**对象选择，请参阅**添加组件**按钮位于最底部*检查器面板*。 
6.  选择该按钮，然后搜索 (通过键入*音频源*到搜索字段或导航部分) 调用组件**音频源**，如下所示，然后选择它 (按 enter 在其上也可）。
7.  *音频源*组件将添加到**Main Camera**如下所示。

    ![添加将音频源组件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > 对于 Microsoft HoloLens，您将需要还可以更改以下内容，这属于**照相机**组件上你**Main Camera**:
    > - **清除标志：** 纯色。
    > - **背景**黑色、 Alpha 0 – 十六进制颜色: #00000000。

## <a name="chapter-4--setup-debug-canvas"></a>第 4 章-安装程序调试画布

若要显示的输入和输出的转换，需要创建一个基本 UI。 对于本课程中，将使用多个文本对象，若要显示的数据创建画布 UI 对象。

1.  在空白区域中单击右键*层次结构面板*下**UI**，将添加**画布**。

    ![添加新的画布 UI 对象。](images/AzureLabs-Lab1-22.png)

2.  与画布对象后，在*检查器面板*（在画布组件），更改**呈现模式**到**世界空间**。 
3.  接下来，更改中的以下参数*检查器面板的 Rect 转换*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *Width* -    500
    3. *Height* -   300
    4. *规模* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![更新画布的 rect 转换。](images/AzureLabs-Lab1-23.png)
 
4.  右键单击**画布**中*层次结构面板*下**UI**，并添加**面板**。 这**面板**将提供到您将在场景中显示的文本的背景。
5.  右键单击**面板**中*层次结构面板*下**UI**，并添加**文本对象**。 重复相同的过程，直到总共创建了四个 UI 文本对象 (提示： 如果具有所选的第一个文本对象，可以只需按**Ctrl + 有**、 对其进行复制，将有四个总之前)。 
6.  每个**文本对象**，选择它，使用下表设置参数*检查器面板*。

    1. 有关*Rect 转换*组件：

        | 名称                   | 转换的*位置*             | 宽度      | Height    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. 有关**文本 （脚本）** 组件：


        | 名称                   | Text               | 字号    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | 麦克风状态： | 20           |
        | AzureResponseLabel     | Azure Web 响应 | 20           |
        | DictationLabel         |   您刚才在说：   | 20           |
        | TranslationResultLabel |    转换：    | 20           |

        ![输入用户界面标签的相应值。](images/AzureLabs-Lab1-24.png)

    3. 此外，请字体样式**加粗**。 这将使文本易于阅读。

        ![粗体的字体。](images/AzureLabs-Lab1-25.png)

7.  每个*UI 文本对象*中创建[第 5 章](#chapter-5--create-the-results-class)，创建一个新*子* **UI 文本对象**。 这些子对象将显示应用程序的输出。 创建*子*通过右键单击目标的父对象 (例如*MicrophoneStatusLabel*)，然后选择**UI** ，然后选择**文本**.
8.  对于每个这些子对象，选择它，并使用下表来检查器面板中设置参数。

    1. 有关**Rect 转换**组件：

        | 名称                  | 转换的*位置* | 宽度      | Height    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. 有关**文本 （脚本）** 组件：

        | 名称                  | Text          | 字号    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 接下来，选择每个文本组件的中心对齐选项：

    ![对齐文本。](images/AzureLabs-Lab1-26.png)

10. 若要确保**子 UI 文本**对象是易于阅读、 更改其*颜色*。 执行此操作通过在栏上单击到 （当前黑色） 的下一步*颜色*。 

    ![输入相应的 UI 文本输出的值。](images/AzureLabs-Lab1-27.png)
 
11. 然后，在新，少*颜色*窗口中，更改*十六进制颜色*到：**0032EAFF**

    ![更新颜色为蓝色。](images/AzureLabs-Lab1-28.png)
 
12. 下面是如何**UI**应所示。
    1.  在中*层次结构面板*:

        ![提供的结构中具有层次结构。](images/AzureLabs-Lab1-29.png)

    2.  在中*场景*并*游戏视图*:

        ![具有同一结构中的场景和游戏视图。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>第 5 章-创建结果类

您需要创建的第一个脚本是*结果*类，该类负责提供一种方法，以查看转换的结果。 类存储并显示以下信息： 

- 从 Azure 响应结果。
- 麦克风状态。 
- 听写 （语音到文本） 的结果。
- 转换的结果。

若要创建此类： 

1.  在中右击*项目面板*，然后**创建 > 文件夹**。 将文件夹命名为**脚本**。 
 
    ![创建脚本的文件夹。](images/AzureLabs-Lab1-31.png)

    ![打开脚本文件夹。](images/AzureLabs-Lab1-32.png)
 
2.  与**脚本**文件夹中创建，双击它打开。 然后在该文件夹，右键单击，并选择**创建 >** 然后**C#脚本**。 脚本命名为*结果*。 

    ![创建第一个脚本。](images/AzureLabs-Lab1-33.png)
 
3.  双击新*结果*脚本以将其与打开**Visual Studio**。
4.  插入以下命名空间：

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  在类中插入以下变量：

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  然后添加*Awake()* 类初始化时将调用的方法。 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  最后，添加方法负责将输出到 UI 的各种结果信息。 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-6--create-the-microphonemanager-class"></a>第 6 章-创建*MicrophoneManager*类

要创建的第二个类是*MicrophoneManager*。

此类负责：

- 正在检测录制设备附加到的耳机或计算机 （无论是默认值）。
- 捕获音频 （语音），并使用听写将其存储为字符串。
- 一旦语音已暂停，提交到转换器类听写。
- 主机可以停止语音捕获所需的方法。

若要创建此类： 
1.  双击**脚本**文件夹，将其打开。 
2.  内右击**脚本**文件夹中，单击**创建 >C#脚本**。 脚本命名为*MicrophoneManager*。 
3.  双击要使用 Visual Studio 中打开的新脚本。
4.  更新命名空间，如下所示，在顶部相同*MicrophoneManager*类：

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  然后，添加以下变量内的*MicrophoneManager*类：

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  为代码*Awake()* 并*start （)* 方法现在需要添加。 类初始化时将会调用：

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  你可以*删除* *update （)* 方法因为此类不会使用它。
8.  现在，你需要应用用于启动和停止语音捕获，并将其传递给方法*转换器*类，您很快就会生成。 将以下代码复制并粘贴下方*start （)* 方法。

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > 尽管此应用程序不会使用它， *StopCapturingAudio()* 方法还提供了在这里，你应该实现停止捕获你的应用程序中的音频的功能。

9.  现在需要添加语音停止时，将调用一个听写处理程序。 然后，此方法将传递到听写的文本*转换器*类。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. 请确保在返回到 Unity 之前的 Visual Studio 中保存所做的更改。

> [!WARNING]  
> 此时你会注意到出现在错误*Unity 编辑器控制台*面板 ("name 转换器不存在...")。 这是因为该代码引用*转换器*类，该类将在下一章中创建。

## <a name="chapter-7--call-to-azure-and-translator-service"></a>第 7 章 – 对 Azure 和转换器的服务调用

若要创建所需的最后一个脚本是*转换器*类。 

此类负责：

-   进行身份验证应用程序与*Azure*，对于 exchange**身份验证令牌**。
-   使用**身份验证令牌**提交的文本 (从收到*MicrophoneManager*类) 以进行转换。
-   接收已转换的结果并将其传递给*结果*类要在 UI 中进行可视化处理。

若要创建此类： 
1.  转到**脚本**之前创建的文件夹。 
2.  在中右击**项目面板**，**创建 >C#脚本**。 调用脚本*转换器*。
3.  双击新*转换器*脚本以将其打开**使用 Visual Studio**。
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  然后添加以下变量内的*转换器*类：

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - 插入到语言的语言**枚举**只是示例。 可随意添加更多，如果您想;[API 支持 60 多个语言](https://docs.microsoft.com/azure/cognitive-services/translator/languages)（包括克林贡语） ！
    > - 没有[交互性更强的页覆盖可用语言](https://www.microsoft.com/translator/business/languages/)，不过请注意页面才会显示工作时的站点语言设置为 en-（和将可能重定向到您的母语的 Microsoft 网站）。 你可以在底部的页或通过更改 URL 的网站语言。
    > - **AuthorizationKey**值，在上面的代码片段中，必须**密钥**收到你在订阅时*Azure 文本翻译 API*。 中已包含此[第 1 章](#chapter-1--the-azure-portal)。

6.  为代码*Awake()* 并*start （)* 方法现在需要添加。 
7.  在这种情况下，代码将调用*Azure*使用授权密钥，以获取*令牌*。

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > 该令牌将在 10 分钟后过期。 根据您的应用程序的方案，可能需要进行多次调用相同协同例程。

8.  以下是协同程序获取令牌：

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > 如果编辑 IEnumerator 方法的名称**GetTokenCoroutine()**，则需要更新*StartCoroutine*并*StopCoroutine*调用上述代码中的字符串值。 [Unity 文档根据](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)，以停止特定*协同程序*，您需要使用的字符串值方法。

9.  接下来，添加 （与它正下方的"支持"流方法） 协同例程来获取接收的文本的翻译*MicrophoneManager*类。 此代码将创建一个查询字符串来将发送到*Azure 文本翻译 API*，然后使用内部的 Unity UnityWebRequest 类将调用 Get 具有查询字符串的终结点。 然后使用结果将转换结果对象中。 下面的代码演示实现过程：

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. 请务必保存中所做的更改*Visual Studio*才会回到*Unity*。

## <a name="chapter-8--configure-the-unity-scene"></a>章 8 – 配置 Unity 场景

1.  返回在 Unity 编辑器中，单击并拖动*结果*类*从***脚本**文件夹**Main Camera**中对象*层次结构面板*。
2.  单击**Main Camera**并查看*检查器面板*。 您将在新添加发现*脚本*组件，有四个字段的值为空。 这些是对在代码中的属性的输出引用。 
3.  拖动相应**文本**中的对象*层次结构面板*到四个槽，如下图中所示。

    ![使用指定的值更新目标的引用。](images/AzureLabs-Lab1-34.png)
  
4.  接下来，单击并拖动*转换器*类派生**脚本**文件夹**Main Camera**对象中*层次结构面板*。 
5.  然后，单击并拖动*MicrophoneManager*类派生**脚本**文件夹**Main Camera**对象中*层次结构面板*。 
6.  最后，单击**Main Camera**并查看*检查器面板*。 您将注意到在拖动的脚本中，有两个下拉列表框，您可以设置的语言。
 
    ![请确保输入预期的翻译语言。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>第 9 章 – 混合现实中的测试

此时您需要测试已正确地实现场景。

请确保：

- 中所述的所有设置[第 1 章](#chapter-1--the-azure-portal)正确设置。 
- *结果*，*转换器*，并*MicrophoneManager*，脚本附加到**Main Camera**对象。 
- 已放置你*Azure 文本翻译 API*服务**密钥**内**authorizationKey**变量内*转换器*脚本。  
- 中的所有字段*主相机检查器面板*正确分配。
- 您的麦克风正在运行您的场景时 (如果没有，请检查是否附加的麦克风*默认*设备，并且您具有[它正确设置了在 Windows 内](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10))。

可以通过按测试沉浸式头戴式**播放**按钮*Unity 编辑器*。
应用程序应通过附加的沉浸式头戴式正常运行。

> [!WARNING]  
> 如果看到有关更改默认音频设备 Unity 控制台中的错误，场景可能无法按预期方式。 这是由于混合的现实门户内置麦克风耳机具有它们的处理的方式。 如果看到此错误，只需停止场景并重新启动它，并且应该可以正常为预期。

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>章第 10-构建 UWP 解决方案和本地计算机上旁加载

此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。

1.  导航到**生成设置**:**文件 > 生成设置...**
2.  从**生成设置**窗口中，单击**生成**。

    ![生成 Unity 场景。](images/AzureLabs-Lab1-36.png)
  
3.  如果尚不存在，则勾选**UnityC#项目**。
4.  单击“生成” 。 将启动 unity*文件资源管理器*窗口中，需要创建，然后选择要生成该应用程序的文件夹。 现在，创建该文件夹并将其命名*应用*。 然后使用*应用程序*文件夹选择，按**选择文件夹**。 
5.  Unity 将开始构建您的项目*应用*文件夹。 
6.  一次 Unity 已完成的生成 （它可能需要一些时间），它将打开*文件资源管理器*窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。

## <a name="chapter-11--deploy-your-application"></a>第 11 章 – 部署你的应用程序

若要部署你的应用程序：

1.  导航到新的 Unity 生成 (*应用程序*文件夹)，然后打开解决方案文件与*Visual Studio*。
2.  在解决方案配置中，选择**调试**。
3.  在解决方案平台中，选择**x86**，**本地计算机**。 

    > 对于 Microsoft HoloLens，您可能会发现它更轻松地将其设置为*远程计算机*，因此您不已接入到你的计算机。 不过，需要还执行以下操作：
    > - 知道**IP 地址**的你 HoloLens，在中找到*设置 > 网络和 Internet > Wi-fi > 高级选项*; IPv4 是应使用的地址。 
    > - 请确保*开发人员模式*是**上**; 中找到*设置 > 更新和安全 > 面向开发人员*。

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab1-37.png)
    
 
4.  转到**生成菜单**，然后单击**部署解决方案**旁加载到您的 PC 应用程序。
5.  你的应用现在应出现在已安装的应用，准备好启动列表中。
6.  启动后，应用将提示你授予对麦克风访问权限。 请务必单击**是**按钮。
7.  现已准备好开始翻译 ！

## <a name="your-finished-translation-text-api-application"></a>完成的翻译文本 API 应用程序

祝贺你，构建利用 Azure 翻译文本 API 将语音转换为已翻译的文本的混合的现实应用。

![最终产品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Bonus 练习

### <a name="exercise-1"></a>练习 1

可以在文本到语音转换将功能添加到应用程序中，以便在返回的文本所说？

### <a name="exercise-2"></a>练习 2

使用户可以更改应用本身的源和输出的语言 （from 和结束），因此应用程序不需要每次想要更改语言重新生成。
