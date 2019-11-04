---
title: MR 和 Azure 301-语言翻译
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure 文本翻译 API。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，translator 文本，hololens，沉浸，vr
ms.openlocfilehash: 012eb5522c866e9e0f1caf5e4024305af07e298c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438524"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。  因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。  这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR 和 Azure 301：语言翻译

在本课程中，你将学习如何使用 Azure 认知服务将翻译功能添加到混合现实应用程序，并提供文本翻译 API。

![最终产品](images/AzureLabs-Lab1-00.png)

文本翻译 API 是一项近乎实时的翻译服务。 该服务是基于云的，并且使用 REST API 调用，应用程序可以使用神经计算机翻译技术将文本转换为其他语言。 有关详细信息，请访问[Azure 文本翻译 API 页](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。

完成本课程后，你将拥有一个混合现实应用程序，该应用程序将能够执行以下操作：

1.  用户将进入连接到沉浸式（VR）耳机（或 HoloLens 内置麦克风）的麦克风。
2.  此应用将捕获听写，并将其发送到 Azure 文本翻译 API。
3.  翻译结果将显示在 Unity 场景中的一个简单 UI 组中。

本课程将介绍如何从翻译人员服务获取结果到基于 Unity 的示例应用程序。 您可以将这些概念应用到您可能生成的自定义应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 301：语言翻译</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要侧重于 Windows Mixed Reality 沉浸（VR）耳机，但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。 在本课程中，你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。 使用 HoloLens 时，可能会在语音捕获过程中注意到某些回声。

## <a name="prerequisites"></a>必备条件

> [!NOTE]
> 本教程面向具有 Unity 和C#的基本经验的开发人员。 另外请注意，本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容（5月2018）。 您可以随意使用最新的软件（如[安装工具](install-the-tools.md)一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件：

- [与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发
- [Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 带有内置麦克风的一组耳机（如果耳机没有内置麦克风和扬声器）
- Azure 安装和翻译检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

- 为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。
- 本教程中的代码允许您从连接到您的 PC 的默认麦克风设备进行录制。 请确保将默认麦克风设备设置为计划用于捕获语音的设备。
- 若要允许你的电脑启用听写，请转到 "**设置" > 隐私 > 语音 "、" 墨迹书写 & 键入**"，然后选择按钮"**打开语音服务并键入建议**"。
- 如果你使用的是连接到（或内置于）耳机的麦克风和耳机，请确保在 "设置" 中打开 "在我磨损耳机、切换到耳机麦克风" **> 混合现实 > 音频和语音**。

   ![混合现实设置](images/AzureLabs-Lab1-00-5.png)

   ![麦克风设置](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> 请注意，如果你要为此实验室开发沉浸式耳机，你可能会遇到音频输出设备问题。 这是由 Unity 中的问题引起的，它在更高版本的 Unity （Unity 2018.2）中是固定的。 此问题可防止 Unity 在运行时更改默认音频输出设备。 作为解决方法，请确保已完成上述步骤，并在此问题自行显示时关闭并重新打开编辑器。

## <a name="chapter-1--the-azure-portal"></a>第1章-Azure 门户

若要使用 Azure Translator API，你将需要配置服务的实例，使其可用于你的应用程序。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。

2.  登录后，单击左上角的 "**新建**"，搜索 "文本翻译 API"。 选择**Enter**。

    ![新资源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 在较新的门户中，可能已将 "**新建**" 一词替换为 "**创建资源**"。

3.  新页将提供*文本翻译 API*服务的说明。 在此页的左下角，选择 "**创建**" 按钮以创建与此服务的关联。

    ![创建文本翻译 API 服务](images/AzureLabs-Lab1-03.png)

4.  单击 "**创建**" 后：

    1. 为此服务实例插入所需的**名称**。
    2. 选择相应的**订阅**。
    3. 选择适合你的**定价层**，如果这是第一次创建*文本翻译服务*，则你应该可以使用免费层（名为 F0）。
    4. 选择一个**资源组**，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务（例如这些实验室）保存在一个公共资源组中。

        > 若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 确定资源组的**位置**（如果要创建新的资源组）。 此位置理想情况下会在应用程序运行所在的区域中。 某些 Azure 资产仅在特定区域提供。
    6. 还需要确认是否已了解应用于此服务的条款和条件。
    7. 选择“创建”。

        ![选择 "创建" 按钮。](images/AzureLabs-Lab1-04.png)

5.  单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。
6.  创建服务实例后，门户中将显示一个通知。 

    ![Azure 服务创建通知](images/AzureLabs-Lab1-05.png)

7.  单击通知以浏览新服务实例。 

    ![中转到资源弹出。](images/AzureLabs-Lab1-06.png)

8.  单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。 你将转到新的文本翻译 API 服务实例。 

    ![文本翻译 API 服务页](images/AzureLabs-Lab1-07.png)

9.  在本教程中，你的应用程序将需要调用你的服务，这是通过使用你的服务的订阅密钥来完成的。 
10. 在*文本翻译*服务的 "*快速启动*" 页上，导航到第一步，*获取你的密钥*，然后单击 "**密钥**" （也可以通过单击位于 "服务" 导航菜单中的蓝色超链接项来实现此目的）。由键图标表示）。 这会显示你的服务*密钥*。
11. 复制其中一个所显示的密钥，因为稍后会在项目中使用此密钥。 

## <a name="chapter-2--set-up-the-unity-project"></a>第2章–设置 Unity 项目

设置并测试混合现实沉浸式耳机。

> [!NOTE]
> 本课程不需要移动控制器。 如果需要支持设置沉浸式耳机，请[遵循以下步骤](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

下面是使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板：

1.  打开*Unity* ，并单击 "**新建**"。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab1-08.png)

2.  现在需要提供 Unity 项目名称。 插入**MR_Translation**。 请确保 "项目类型" 设置为 " **3d**"。 将位置设置为合适的*位置*（请记住，更接近根目录更好）。 然后单击 "**创建项目**"。

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab1-09.png)

3.  当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "**编辑 > 首选项**"，然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab1-10.png)

4.  接下来，通过单击 "**切换平台**" 按钮转到 "**文件 > 生成设置**"，并将平台切换到**通用 Windows 平台**。

    ![生成设置窗口，将平台切换到 UWP。](images/AzureLabs-Lab1-11.png)

5.  请参阅**文件 > 生成设置**，并确保：

    1. "**目标设备**" 设置为 "**任何设备**"。

        > 对于 Microsoft HoloLens，将 "**目标设备**" 设置为 " *hololens*"。

    2. **生成类型**设置为**D3D**
    3. **SDK**设置为 "**最新安装**"
    4. **Visual Studio 版本**设置为 "**最新安装**"
    5. "**生成并运行**" 设置为 "**本地计算机**"
    6. 保存场景并将其添加到生成中。

        1. 通过选择 "**添加打开的场景**" 来执行此操作。 将显示 "保存" 窗口。

            ![单击 "添加打开的场景" 按钮](images/AzureLabs-Lab1-12.png)

        2. 为此创建新文件夹，并为将来的任何场景创建一个新文件夹，然后选择 "**新建文件夹**" 按钮以创建新文件夹，将其命名为**场景**。

            !["创建新脚本" 文件夹](images/AzureLabs-Lab1-13.png)

        3. 打开新创建的**场景**文件夹，然后*在 "文件名：文本" 字段*中，键入**MR_TranslationScene**，然后按 "**保存**"。

            ![为新场景指定名称。](images/AzureLabs-Lab1-14.png)

            > 请注意，必须将 Unity 场景保存在 "*资产*" 文件夹中，因为它们必须与 Unity 项目相关联。 创建场景文件夹（以及其他类似文件夹）是构造 Unity 项目的典型方式。

    7. 现在，"*生成设置*" 中的其余设置应保留为默认值。

6. 在 "*生成设置*" 窗口中，单击 "**播放机设置**" 按钮，这会在*检查器*所在的空间中打开相关面板。 

    ![打开播放机设置。](images/AzureLabs-Lab1-15.png)

7. 在此面板中，需要验证几项设置：

    1. 在 "**其他设置**" 选项卡中：

        1. **脚本运行时版本**应**稳定**（与 .net 3.5 等效）。
        2. **脚本编写后端**应为 **.net**
        3. **API 兼容级别**应为 **.net 4.6**

            ![更新其他设置。](images/AzureLabs-Lab1-16.png)
      
    2. 在 "**发布设置**" 选项卡的 "**功能**" 下，检查：

        1. **InternetClient**
        2. **十分**

            ![正在更新发布设置。](images/AzureLabs-Lab1-17.png)

    3. 在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK** 。

        ![更新 X R 设置。](images/AzureLabs-Lab1-18.png)

8.  返回**生成设置**， *Unity C#项目*不再灰显;勾选此的旁边的复选框。 
9.  关闭 "生成设置" 窗口。
10. 保存场景和项目（**file > SAVE 场景/file > SAVE Project**）。

## <a name="chapter-3--main-camera-setup"></a>第3章–照相机设置

> [!IMPORTANT]
> 如果希望跳过本课程的*Unity 设置*组件，并继续直接进入代码，可以[下载 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)，将其作为[*自定义包*](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后从[第5章](#chapter-5--create-the-results-class)继续。 你仍需要创建一个 Unity 项目。

1.  在 "*层次结构" 面板*中，你会看到一个名为 "**主相机**" 的对象，此对象表示你在应用程序中 "内部" 后的 "头" 点。
2.  在您前面的 Unity 仪表板中，选择 " **GameObject" 主摄像机**。 你会注意到，"*检查器" 面板*（通常位于仪表板中）将显示该*GameObject*的各种组件，其中的 "*转换*" 位于顶部，后面跟有*相机*和一些其他组件。 需要重置主摄像机的转换，以便正确定位。
3.  为此，请选择相机*转换*组件旁边的**齿轮**图标，然后选择 "**重置**"。 

    ![重置照相机转换。](images/AzureLabs-Lab1-19.png)
 
4.  *转换*组件如下所示：

    1. *位置*设置为**0，0，0**
    2. *旋转*设置为**0，0，0**
    3. "*小数位数*" 设置为1、1 **、1**

        ![照相机的转换信息](images/AzureLabs-Lab1-20.png)

5.  接下来，选择了 "**相机**" 对象，并查看位于 "*检查器" 面板*底部的 "**添加组件**" 按钮。 
6.  选择该按钮，然后搜索（通过在搜索字段中键入 "*音频源*" 或 "导航" 部分）来查找称为 "**音频源**" 的组件，并选择它（按 enter 键也能正常运行）。
7.  *音频源*组件将添加到**摄像机**，如下所示。

    ![添加音频源组件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > 对于 Microsoft HoloLens，你还需要更改以下内容，这是你**的摄像机上** **相机**组件的一部分：
    > - **清除标志：** 纯色。
    > - **背景**"黑色，Alpha 0" –十六进制颜色： #00000000。

## <a name="chapter-4--setup-debug-canvas"></a>第4章-安装调试画布

若要显示转换的输入和输出，需要创建一个基本 UI。 在本课程中，您将创建一个画布 UI 对象，其中包含多个 "Text" 对象来显示数据。

1.  右键单击 "*层次结构" 面板*的空白区域，在 " **UI**" 下，添加**画布**。

    ![添加新的画布 UI 对象。](images/AzureLabs-Lab1-22.png)

2.  选中 Canvas 对象后，在 "*检查器" 面板*（位于 "画布" 组件中）将 "**渲染模式**" 更改为 "**世界上空间**"。 
3.  接下来，在 "*检查器" 面板的 Rect 转换*中更改以下参数：

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *宽度*-500
    3. *高度*-300
    4. *缩放* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![更新画布的 rect 转换。](images/AzureLabs-Lab1-23.png)
 
4.  右键单击 "*层次结构" 面板*中的 " **UI**" 下的**画布**，然后添加**面板**。 此**面板**将提供您将在场景中显示的文本的背景。
5.  右键单击 "*层次结构" 面板*中的 " **UI**" 下的**面板**，然后添加一个**文本对象**。 重复相同的过程，直到总共创建了四个 UI 文本对象（提示：如果已选择第一个 "文本" 对象，则只需按 **"Ctrl" + "d"** 即可复制该对象，直到总共有四个）。 
6.  对于每个**文本对象**，请选择它，并使用下表在 "*检查器" 面板*中设置参数。

    1. 对于*Rect 转换*组件：

        | 名称                   | 转换*位置*             | 宽度      | Height    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. 对于**文本（脚本）** 组件：


        | 名称                   | 文本               | 字号    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | 麦克风状态： | 20           |
        | AzureResponseLabel     | Azure Web 响应 | 20           |
        | DictationLabel         |   您刚才说：   | 20           |
        | TranslationResultLabel |    换算    | 20           |

        ![为 UI 标签输入相应的值。](images/AzureLabs-Lab1-24.png)

    3. 同时，将字体样式设置为**粗体**。 这会使文本更易于阅读。

        ![粗体。](images/AzureLabs-Lab1-25.png)

7.  对于[第5章](#chapter-5--create-the-results-class)中创建的每个*UI 文本对象*，创建新的*子* **UI 文本对象**。 这些子级将显示应用程序的输出。 右键单击目标父对象（例如*MicrophoneStatusLabel*），然后选择 "**用户界面**"，然后选择 "**文本**"，创建*子*对象。
8.  对于其中的每个子项，请选择它，并使用下表在 "检查器" 面板中设置参数。

    1. 对于**Rect 转换**组件：

        | 名称                  | 转换*位置* | 宽度      | Height    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y-30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y-30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y-30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y-30 Z 0          | 300        | 30        |

    2. 对于**文本（脚本）** 组件：

        | 名称                  | 文本          | 字号    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 接下来，为每个文本组件选择 "中心" 对齐选项：

    ![对齐文本。](images/AzureLabs-Lab1-26.png)

10. 若要确保**子 UI 文本**对象易于阅读，请更改其*颜色*。 通过单击 "*颜色*" 旁边的栏（当前为 "黑色"）来执行此操作。 

    ![输入 UI 文本输出的相应值。](images/AzureLabs-Lab1-27.png)
 
11. 然后，在新的、小的*颜色*窗口中，将*Hex 颜色*改为： **0032EAFF**

    ![将颜色更新为蓝色。](images/AzureLabs-Lab1-28.png)
 
12. 下面是**UI**的外观。
    1.  在 "*层次结构" 面板*中：

        ![具有所提供的结构中的层次结构。](images/AzureLabs-Lab1-29.png)

    2.  在*场景*和*游戏视图*中：

        ![使场景和游戏视图位于同一结构中。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>第5章–创建结果类

需要创建的第一个脚本是*结果*类，该类负责提供一种方式来查看翻译结果。 类存储并显示以下内容： 

- 来自 Azure 的响应结果。
- 麦克风状态。 
- 听写（语音到文本）的结果。
- 转换的结果。

若要创建此类： 

1.  右键单击 "*项目" 面板*，然后**创建 > 文件夹**。 命名文件夹**脚本**。 
 
    ![创建脚本文件夹。](images/AzureLabs-Lab1-31.png)

    ![打开 "脚本" 文件夹。](images/AzureLabs-Lab1-32.png)
 
2.  在 "**脚本**" 文件夹中，双击以打开。 在该文件夹中，右键单击，然后选择 "**创建 >** 然后**C#** 选择" 脚本 "。 为脚本*结果*命名。 

    ![创建第一个脚本。](images/AzureLabs-Lab1-33.png)
 
3.  双击新*结果*脚本以通过**Visual Studio**打开它。
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

6.  然后添加*唤醒（）* 方法，在类初始化时将调用此方法。 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  最后，添加负责将各种结果信息输出到 UI 的方法。 

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

8.  在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-6--create-the-microphonemanager-class"></a>第6章–创建*MicrophoneManager*类

要创建的第二个类是*MicrophoneManager*。

此类负责：

- 检测连接到耳机或计算机的记录设备（以默认值为准）。
- 捕获音频（语音）并使用听写将其存储为字符串。
- 暂停语音后，将听写提交给转换器类。
- 承载一个方法，该方法可以在需要时停止语音捕获。

若要创建此类： 
1.  双击 "**脚本**" 文件夹以将其打开。 
2.  右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。 将脚本命名为*MicrophoneManager*。 
3.  双击新脚本以通过 Visual Studio 打开它。
4.  在*MicrophoneManager*类的顶部，将命名空间更新为与以下相同：

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  然后，在*MicrophoneManager*类中添加以下变量：

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

6.  现在需要添加*唤醒（）* 和*Start （）* 方法的代码。 当类初始化时，将调用以下内容：

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

7.  您可以*删除* *Update （）* 方法，因为此类将不会使用它。
8.  现在，你需要应用程序用来启动和停止语音捕获，并将其传递给*Translator*类的方法。 复制以下代码，并将其粘贴到*Start （）* 方法下。

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
    > 虽然此应用程序将不会使用它，但在此还提供了*StopCapturingAudio （）* 方法，因此，如果要实现在应用程序中停止捕获音频的功能，则也是如此。

9.  现在需要添加语音停止时将调用的听写处理程序。 此方法随后将听写的文本传递到*转换器*类。

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

10. 在返回到 Unity 之前，请务必保存 Visual Studio 中所做的更改。

> [!WARNING]  
> 此时，你会注意到在*Unity 编辑器控制台*面板中出现错误（"名称" 转换器不存在 ... "）。 这是因为代码引用了将在下一章中创建的*转换器*类。

## <a name="chapter-7--call-to-azure-and-translator-service"></a>第7章–调用 Azure 和转换器服务

需要创建的最后一个脚本是*转换器*类。 

此类负责：

-   使用*Azure*对**身份验证令牌**进行身份验证。
-   使用**身份验证令牌**提交要翻译的文本（从*MicrophoneManager*类收到）。
-   接收转换后的结果，并将其传递到要在 UI 中可视化的*结果*类。

若要创建此类： 
1.  中转到前面创建的 "**脚本**" 文件夹。 
2.  右键单击 "**项目" 面板**，  **C#创建 > 脚本**。 调用脚本*转换器*。
3.  双击新的*转换器*脚本以**通过 Visual Studio**打开它。
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  然后在*转换器*类中添加以下变量：

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
    > - 插入语言**枚举**中的语言只是示例。 如果需要，可以随意添加更多内容;此[API 支持超过60种语言](https://docs.microsoft.com/azure/cognitive-services/translator/languages)（包括克）！
    > - 还有一个[涵盖可用语言的更交互式页面](https://www.microsoft.com/translator/business/languages/)，不过，当站点语言设置为 "" 时，此页仅显示为 "" （Microsoft 网站可能会重定向到你的本地语言）。 您可以在页面底部或通过更改 URL 来更改站点语言。
    > - 在上述代码片段中， **authorizationKey**值必须是在订阅*Azure 文本翻译 API*时收到的**密钥**。 [第1章](#chapter-1--the-azure-portal)中对此进行了介绍。

6.  现在需要添加*唤醒（）* 和*Start （）* 方法的代码。 
7.  在这种情况下，代码将使用授权密钥调用*Azure*以获取*令牌*。

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
    > 该令牌将在10分钟后过期。 根据应用的方案，可能需要多次进行相同的协同程序调用。

8.  获取令牌的协同程序如下所示：

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
    > 如果编辑 IEnumerator 方法**GetTokenCoroutine （）** 的名称，则需要更新上述代码中的*StartCoroutine*和*StopCoroutine*调用字符串值。 [按照 Unity 文档](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)，若要停止特定的*协同程序*，需要使用字符串值方法。

9.  接下来，添加协同程序（在其下方提供 "支持" 流方法），以获取*MicrophoneManager*类收到的文本的翻译。 此代码将创建一个要发送到*Azure 文本翻译 API*的查询字符串，然后使用内部 Unity UnityWebRequest 类通过查询字符串对终结点进行 "Get" 调用。 然后，将使用该结果在结果对象中设置翻译。 下面的代码显示了实现：

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

10. 在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-8--configure-the-unity-scene"></a>第8章–配置 Unity 场景

1.  返回 Unity 编辑器，单击 "*结果*" 类并将其*从*"**脚本**" 文件夹拖到 "*层次结构" 面板*中的 "**照相机**" 对象。
2.  单击**主摄像机**，查看*检查器面板*。 你会注意到，在新添加的*脚本*组件中，有四个字段包含空值。 这些是对代码中的属性的输出引用。 
3.  将相应的**文本**对象从 "*层次结构" 面板*拖动到这四个槽，如下图所示。

    ![用指定的值更新目标引用。](images/AzureLabs-Lab1-34.png)
  
4.  接下来，在 "**脚本**" 文件夹中单击 "*转换器*" 类并将其拖到 "*层次结构" 面板*中的 "**照相机**" 对象。 
5.  然后，在 "*层次结构" 面板*中单击 "**脚本**" 文件夹中的*MicrophoneManager*类，并将其拖到**主相机**对象。 
6.  最后，单击**主摄像机**，查看*检查器面板*。 你会注意到，在所拖动的脚本中，有两个下拉框可用于设置语言。
 
    ![确保预期的翻译语言为输入。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>第9章–在混合现实中测试

此时，需要测试场景是否已正确实现。

请确保：

- [第1章](#chapter-1--the-azure-portal)中提到的所有设置都已正确设置。 
- *结果*、*转换器*和*MicrophoneManager*将脚本附加到**摄像机的主**对象。 
- 已将*Azure 文本翻译 API*服务**密钥**放置在*转换器*脚本内的**authorizationKey**变量中。  
- *主相机检查器面板*中的所有字段均已正确分配。
- 你的麦克风在运行场景时工作（如果没有，请检查你的已连接麦克风是否为*默认*设备，以及你是否在[Windows 中正确设置了它](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)）。

可以通过在*Unity 编辑器*中按 "**播放**" 按钮来测试沉浸式头戴式耳机。
该应用应通过附加的沉浸式耳机来运行。

> [!WARNING]  
> 如果在 Unity 控制台中看到有关默认音频设备变化的错误，场景可能无法按预期方式工作。 这是因为混合现实门户使用内置麦克风处理随附的耳机的方式。 如果看到此错误，只需停止场景并再次启动，应按预期方式工作。

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>第10章–在本地计算机上构建 UWP 解决方案和旁加载

此项目的 Unity 部分所需的所有内容现在均已完成，因此可以从 Unity 构建它。

1.  导航到 "**生成设置**：**文件 > 生成设置 ...** "
2.  在**生成设置**窗口中，单击 "**生成**"。

    ![构建 Unity 场景。](images/AzureLabs-Lab1-36.png)
  
3.  如果尚未这样做，请勾选**Unity C#项目**。
4.  单击**生成**。 Unity 将启动*文件资源管理器*窗口，在该窗口中，需要创建一个文件夹，然后选择要在其中生成应用的文件夹。 立即创建该文件夹并将其命名为*应用*。 选择*应用*文件夹后，按 "**选择文件夹**"。 
5.  Unity 将开始向*应用*文件夹生成项目。 
6.  Unity 完成生成（可能需要一些时间）后，它会在生成的位置打开 "*文件资源管理器*" 窗口（检查任务栏，因为它可能不会始终出现在窗口之上，但会通知你添加了一个新窗口）。

## <a name="chapter-11--deploy-your-application"></a>第11章-部署应用程序

若要部署应用程序：

1.  导航到新的 Unity 生成（*应用*文件夹），并在*Visual Studio*中打开解决方案文件。
2.  在解决方案配置中，选择 "**调试**"。
3.  在解决方案平台中，选择 " **x86**，**本地计算机**"。 

    > 对于 Microsoft HoloLens，你可能会发现将其设置为*远程计算机*会更容易，因此你不会受限到计算机上。 不过，还需要执行以下操作：
    > - 知道您的 HoloLens 的**IP 地址**，可在 "*设置" > 网络 & Internet > > "高级选项*" 中找到;IPv4 是应使用的地址。 
    > - 确保*开发人员模式*已**打开**;在 "设置" 中找到 *> 更新开发人员 & 安全 >* 。

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab1-37.png)
    
 
4.  中转到 "**生成" 菜单**，然后单击 "**部署解决方案**"，将应用程序旁加载到你的电脑。
5.  应用现在应显示在已安装的应用列表中，可以启动。
6.  启动后，应用会提示你授权访问麦克风。 请确保单击 **"是"** 按钮。
7.  你现在已准备好开始翻译！

## <a name="your-finished-translation-text-api-application"></a>已完成的翻译文本 API 应用程序

恭喜，你构建了一个混合现实应用，它利用 Azure 翻译文本 API 将语音转换为翻译文本。

![最终产品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

是否可以向应用程序中添加文本到语音功能，以使返回的文本被朗读？

### <a name="exercise-2"></a>练习2

使用户能够在应用程序中更改源和输出语言（"从" 和 "到"），因此在每次需要更改语言时无需重新生成应用程序。
