---
title: MR 和 Azure 302-计算机视觉
description: 完成本课程, 了解如何使用 Azure 计算机视觉在混合现实应用程序中识别所提供的映像中的视觉内容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合现实, 学院, unity, 教程, api, 计算机视觉, hololens, 沉浸, vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63552328"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR 和 Azure 302:计算机视觉

在本课程中, 你将了解如何在混合现实应用程序中使用 Azure 计算机视觉功能识别所提供的映像中的视觉内容。

识别结果将显示为描述性标记。 您可以使用此服务, 无需训练机器学习模型。 如果实现需要训练机器学习模型, 请参阅[MR And Azure 302b](mr-azure-302b.md)。

![实验室结果](images/AzureLabs-Lab2-000.png)

Microsoft 计算机视觉是一组 Api, 旨在向开发人员提供使用高级算法的图像处理和分析 (使用返回信息), 所有这些都来自云。 开发人员可上传图像或图像 URL, Microsoft 计算机视觉 API 算法将根据输入的输入来分析视觉内容, 然后, 该用户可以返回信息, 包括标识图像的类型和质量、检测人脸 (返回它们的坐标)、标记或分类图像。 有关详细信息, 请访问[Azure 计算机视觉 API 页](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。

完成本课程后, 你将拥有一个混合现实 HoloLens 应用程序, 该应用程序将能够执行以下操作:

1.  使用点击手势, HoloLens 的照相机将捕获图像。
2.  映像将发送到 Azure 计算机视觉 API 服务。 
3.  识别的对象将在位于 Unity 场景中的一个简单 UI 组中列出。

在您的应用程序中, 您将由您来决定如何将结果与您的设计相集成。 本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。 您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 302:计算机视觉</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要侧重于 HoloLens, 但你也可以将本课程中学习的内容应用于 Windows Mixed Reality 沉浸 (VR) 耳机。 由于沉浸式 (VR) 耳机没有可访问的摄像机, 因此需要连接到电脑的外部照相机。 在本课程中, 您将看到有关支持沉浸式 (VR) 耳机时可能需要执行的任何更改的说明。

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
- 连接到电脑的相机 (适用于沉浸式耳机开发)
- Azure 安装和计算机视觉 API 检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

1.  为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。
2.  设置并测试你的 HoloLens。 如果需要支持设置 HoloLens, 请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  在开始开发新的 HoloLens 应用程序时, 最好执行校准和传感器调整 (有时它可以帮助为每个用户执行这些任务)。 

有关校准的帮助信息, 请单击此链接, 了解[到 HoloLens 校准文章](calibration.md#hololens)。

有关传感器优化的帮助, 请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。

## <a name="chapter-1--the-azure-portal"></a>第1章-Azure 门户

若要在 Azure 中使用*计算机视觉 API*服务, 你将需要配置服务的实例, 使其可用于你的应用程序。

1.  首先, 登录到[Azure 门户](https://portal.azure.com)。 

    > [!NOTE]
    > 如果还没有 Azure 帐户, 则需要创建一个。 如果在课堂或实验室中按照本教程进行学习, 请咨询教师或 proctors, 以获得设置新帐户的帮助。

2.  登录后, 单击左上角的 "**新建**", 搜索 "*计算机视觉 API*", 然后单击 " **Enter**"。

    ![在 Azure 中创建新资源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 在较新的门户中, 可能已将 "**新建**" 一词替换为 "**创建资源**"。
 
3.  新页将提供*计算机视觉 API*服务的说明。 在此页的左下角, 选择 "**创建**" 按钮以创建与此服务的关联。

    ![关于计算机视觉 api 服务](images/AzureLabs-Lab2-01.png)
 
4.  单击 "**创建**" 后:

    1. 为此服务实例插入所需的**名称**。
    2. 选择**订阅**。
    3. 选择适合你的**定价层**, 如果这是第一次创建*计算机视觉 API*服务, 则你应该可以使用免费层 (名为 F0)。
    4. 选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务 (例如这些实验室) 保存在一个公共资源组中。 

        > 若要了解有关 Azure 资源组的详细信息, 请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 确定资源组的位置 (如果要创建新的资源组)。 此位置理想情况下会在应用程序运行所在的区域中。 某些 Azure 资产仅在特定区域提供。

    6. 还需要确认是否已了解应用于此服务的条款和条件。
    7. 单击 "创建"。

        ![服务创建信息](images/AzureLabs-Lab2-02.png)

5.  单击 "**创建**" 后, 需要等待创建服务, 这可能需要一分钟时间。
6.  创建服务实例后, 门户中将显示一个通知。

    ![查看新服务的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  单击通知以浏览新服务实例。 

    ![选择 "中转到资源" 按钮。](images/AzureLabs-Lab2-04.png)
 
8. 单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。 你将转到新的计算机视觉 API 服务实例。 

    ![新的计算机视觉 API 服务](images/AzureLabs-Lab2-05.png)
 
9.  在本教程中, 你的应用程序将需要调用你的服务, 这是通过使用你的服务的订阅密钥来完成的。
10. 在*计算机视觉 API*服务的 "*快速启动*" 页上, 导航到第一步,*获取你的密钥*, 然后单击 "**密钥**" (也可以通过单击位于 "服务" 导航菜单中的蓝色超链接项来实现此目的)。由键图标表示)。 这会显示你的服务*密钥*。
11. 复制其中一个所显示的密钥, 因为稍后会在项目中使用此密钥。 

12. 返回到 "*快速启动*" 页, 从该处获取终结点。 请注意, 你可能会有所不同, 具体取决于你所在的区域 (如果是, 你将需要在以后对代码进行更改)。 获取此终结点的副本供以后使用:

    ![新的计算机视觉 API 服务](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > 可在[此处](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)检查各种终结点。 

## <a name="chapter-2--set-up-the-unity-project"></a>第2章–设置 Unity 项目

下面是用于使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。

1.  打开*Unity* , 并单击 "**新建**"。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab2-06.png)

2.  现在需要提供 Unity 项目名称。 插入**MR_ComputerVision**。 请确保 "项目类型" 设置为 " **3d**"。 将位置设置为合适的**位置**(请记住, 更接近根目录更好)。 然后单击 "**创建项目**"。

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab2-07.png)

3.  当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "**编辑 > 首选项**", 然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab2-08.png)

4.  接下来, 转到 "**文件 > 生成设置**", 选择 "**通用 Windows 平台**", 然后单击 "**切换平台**" 按钮以应用所选内容。

    ![生成设置窗口, 将平台切换到 UWP。](images/AzureLabs-Lab2-10.png)

5.  尽管仍处于**文件 > 生成设置**, 但请确保:

    1. **目标设备**设置为**HoloLens**

        > 对于沉浸式耳机, 将 "**目标设备**" 设置为 "*任何设备*"。

    2. **生成类型**设置为**D3D**
    3. **SDK**设置为 "**最新安装**"
    4. **Visual Studio 版本**设置为 "**最新安装**"
    5. "**生成并运行**" 设置为 "**本地计算机**"
    6. 保存场景并将其添加到生成中。

        1. 通过选择 "**添加打开的场景**" 来执行此操作。 将显示 "保存" 窗口。
        
            ![单击 "添加打开的场景" 按钮](images/AzureLabs-Lab2-11.png)

        2. 为此创建新文件夹, 并为将来的任何场景创建一个新文件夹, 然后选择 "**新建文件夹**" 按钮以创建新文件夹, 将其命名为**场景**。

            !["创建新脚本" 文件夹](images/AzureLabs-Lab2-12.png)

        3. 打开新创建的**场景**文件夹, 然后在 "文件名 *: 文本*" 字段中, 键入**MR_ComputerVisionScene**, 然后单击 "**保存**"。

            ![为新场景指定名称。](images/AzureLabs-Lab2-13.png)

            > 请注意, 必须将 Unity 场景保存在 "*资产*" 文件夹中, 因为它们必须与 Unity 项目相关联。 创建场景文件夹 (以及其他类似文件夹) 是构造 Unity 项目的典型方式。

    7. 现在, "*生成设置*" 中的其余设置应保留为默认值。

6. 在 "*生成设置*" 窗口中, 单击 "**播放机设置**" 按钮, 这会在*检查器*所在的空间中打开相关面板。 

    ![打开播放机设置。](images/AzureLabs-Lab2-14.png)

7. 在此面板中, 需要验证几项设置:

    1. 在 "**其他设置**" 选项卡中:

        1. **脚本运行时版本**应**稳定**(与 .net 3.5 等效)。
        2. **脚本编写后端**应为 **.net**
        3. **API 兼容级别**应为 **.net 4.6**

            ![更新其他设置。](images/AzureLabs-Lab2-15.png)
      
    2. 在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:

        1. **InternetClient**
        2. **摄像头**

            ![正在更新发布设置。](images/AzureLabs-Lab2-16.png)

    3. 在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 在 "**支持的虚拟现实**" 下, 确保已添加**Windows Mixed reality SDK** 。

        ![更新 X R 设置。](images/AzureLabs-Lab2-17.png)

8.  "返回*生成设置* _" C# Unity_项目不再灰显;勾选此的旁边的复选框。 
9.  关闭 "生成设置" 窗口。
10. 保存场景和项目 (**file > SAVE 场景/file > SAVE Project**)。

## <a name="chapter-3--main-camera-setup"></a>第3章–照相机设置

> [!IMPORTANT]
> 如果希望跳过本课程的*Unity 设置*组件, 并继续直接进入代码, 可以下载[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), 将其作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目, 然后从[第5章](#chapter-5--create-the-resultslabel-class)继续。

1.  在 "*层次结构" 面板*中, 选择 "**摄像机**"。 
2.  选择后, 你将能够在 "*检查器" 面板*中看到**主相机**的所有组件。

    1. **照相机对象**必须命名为 "**主相机**" (请注意拼写正确!)
    2. 必须将主相机**标记**设置为**MainCamera** (请注意拼写!)
    3. 请确保将**转换位置**设置为**0, 0, 0**
    4. 将**清除标志**设置为**纯色**(对于沉浸式耳机, 请忽略此设置)。
    5. 将相机组件的**背景**色设置为**黑色、Alpha 0 (十六进制代码: #00000000)** (对沉浸式耳机忽略此颜色)。

        ![更新照相机组件。](images/AzureLabs-Lab2-18.png)
 
3.  接下来, 必须创建一个附加到**主相机**的简单 "Cursor" 对象, 这将帮助你在应用程序运行时定位图像分析输出。 此光标将确定相机焦点的中心点。

创建游标:

1.  在 "*层次结构" 面板*中, 右键单击**主相机**。 在 " **3D 对象**" 下, 单击 "**球面**"。

    ![选择 Cursor 对象。](images/AzureLabs-Lab2-19.png)
 
2.  将**球体**重命名为**光标**(双击光标对象或按选定对象的 "F2" 键盘按钮), 并确保它位于**主相机**的子项中。

3.  在 "*层次结构" 面板*中, 左键单击**光标**。 选择光标后, 在 "*检查器" 面板*中调整以下变量:

    1. 将*转换位置*设置为**0、0、5**
    2. 将*刻度*设置为**0.02、0.02、0.02**

        ![更新转换位置和缩放比例。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>第4章–设置标签系统

使用 HoloLens 相机捕获映像后, 该映像将发送到*Azure 计算机视觉 API*服务实例进行分析。 

此分析的结果将是被识别对象 (称为**标记**) 的列表。 

您将使用标签 (作为世界空间中的3D 文本) 在拍摄照片的位置显示这些标记。

以下步骤将演示如何设置**标签**对象。

1.  右键单击 "层次结构" 面板中的任意位置 (此时位置并不重要), 在 "**三维对象**" 下添加**3d 文本**。 将其命名为**LabelText**。

    ![创建3D 文本对象。](images/AzureLabs-Lab2-21.png)
 
2.  在 "*层次结构" 面板*中, 单击**LabelText**。 选择**LabelText**后, 在 "*检查器" 面板*中调整以下变量:

    1. 将**位置**设置为**0, 0, 0**
    2. 将**刻度**设置为**0.01、0.01、0.01**
    3. 在组件**文本网格**中:
    4. 将**文本**中的所有文本替换为 "..."        
    5. 将**定位点**设置为**中间中心**
    6. 将**对齐方式**设置为**居中**
    7. 将**选项卡大小**设置为**4**
    8. 将**字体大小**设置为**50**
    9. 将**颜色**设置为 **#FFFFFFFF**

    ![文本组件](images/AzureLabs-Lab2-21-5.png)

3.  将**LabelText**从 "*层次结构" 面板*中拖到 "*资源" 文件夹*内的 "*项目" 面板*中。 这会将**LabelText**设置为 Prefab, 以便可以在代码中对其进行实例化。

    ![创建 LabelText 对象的 prefab。](images/AzureLabs-Lab2-22.png)
 
4.  你应从 "*层次结构" 面板*中删除**LabelText** , 以使其不会在打开场景中显示。 由于它现在是一个 prefab, 你将从资产文件夹中的单个实例上调用, 无需将其保存在场景中。 
5.  "*层次结构" 面板*中的最后一个对象结构应类似于下图所示:

    ![层次结构面板的最终结构。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>第5章–创建 ResultsLabel 类

需要创建的第一个脚本是*ResultsLabel*类, 该类负责以下操作: 

- 在适当的世界空间中创建标签, 相对于照相机的位置。
- 显示图像 Analysis 中的标记。

若要创建此类: 

1.  右键单击 "*项目" 面板*, 然后**创建 > 文件夹**。 命名文件夹**脚本**。 

    ![创建脚本文件夹。](images/AzureLabs-Lab2-24.png)

2.  在 "**脚本**" 文件夹中, 双击以打开。 在该文件夹中, 右键单击, 然后选择 "**创建 >** 然后**C#** 选择" 脚本 "。 将脚本命名为*ResultsLabel*。 

3.  双击新的*ResultsLabel*脚本以通过**Visual Studio**打开它。

4.  在类中, 在*ResultsLabel*类中插入以下代码:

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

6.  在返回到*Unity*之前, 请务必保存*Visual Studio*中所做的更改。
7.  返回*Unity 编辑器*, 单击 "**脚本**" 文件夹中的*ResultsLabel*类并将其拖到 "*层次结构" 面板*中的**主相机**对象。
8.  单击**主摄像机**, 查看*检查器面板*。

你会注意到, 从刚才拖到摄像机的脚本中, 有两个字段:**光标**和**标签 Prefab**。

9.  将名为**cursor**的对象从 "*层次结构" 面板*拖动到名为 " **cursor**" 的槽中, 如下图所示。
10. 将名为**LabelText**的对象从 "*项目" 面板*中的 "*资产" 文件夹*拖到名为**Label Prefab**的槽中, 如下图所示。 

    ![在 Unity 中设置引用目标。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>第6章–创建 ImageCapture 类

要创建的下一个类是*ImageCapture*类。 此类负责:

-   使用 HoloLens 相机捕获映像, 并将其存储在 App 文件夹中。
-   正在捕获用户的点击手势。

若要创建此类: 

1.  中转到前面创建的 "**脚本**" 文件夹。 
2.  右键单击文件夹内部,**创建 > C#脚本**。 调用脚本*ImageCapture*。 
3.  双击新的*ImageCapture*脚本以通过**Visual Studio**打开它。
4.  将以下命名空间添加到文件顶部:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  然后, 将以下变量添加到*ImageCapture*类中的*Start ()* 方法之上:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount**变量将存储从用户捕获的攻丝手势的数目。 此编号用于捕获的映像的命名。

6.  现在需要添加*唤醒 ()* 和*Start ()* 方法的代码。 当类初始化时, 将调用以下内容:

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

7.  实现一个处理程序, 该处理程序将在出现分流手势时调用。 

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
 
*TapHandler ()* 方法会递增从用户捕获的点击次数, 并使用当前光标位置确定新标签的位置。

然后, 此方法会调用*ExecuteImageCaptureAndAnalysis ()* 方法来开始此应用程序的核心功能。

8.  捕获并存储映像后, 将调用以下处理程序。 如果该过程成功, 则会将结果传递给要分析的*VisionManager* (尚未创建)。

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
 
9.  然后添加应用程序用于启动映像捕获进程并存储映像的方法。

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
> 此时, 你会注意到在*Unity 编辑器控制台面板*中出现错误。 这是因为代码引用了将在下一章中创建的*VisionManager*类。

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>第7章–调用 Azure 和映像分析

需要创建的最后一个脚本是*VisionManager*类。 

此类负责:

-   加载作为字节数组捕获的最新映像。
-   将字节数组发送给*Azure 计算机视觉 API*服务实例进行分析。
-   接收 JSON 字符串形式的响应。
-   反序列化响应并将生成的标记传递给*ResultsLabel*类。
 
若要创建此类:

1.  双击 "**脚本**" 文件夹以将其打开。 
2.  右键单击 "**脚本**" 文件夹中, 单击 "**创建C# > 脚本**"。 将脚本命名为*VisionManager*。 
3.  双击新脚本以通过 Visual Studio 打开它。
4.  在*VisionManager*类的顶部, 将命名空间更新为与以下相同:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  在脚本的*顶部, 在* *VisionManager*类 (位于*Start ()* 方法的上面) 中, 现在需要创建两个*类*来表示来自 Azure 的反序列化 JSON 响应:

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
    > *TagData*和*AnalysedObject*类需要添加 *[system.exception]* 特性, 然后才能使用 Unity 库反序列化声明。

6.  在 VisionManager 类中, 应添加以下变量:

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
    > 请确保将**身份验证密钥**插入到**authorizationKey**变量。 你将在本课程开头注明**身份验证密钥**,[第1章](#chapter-1--the-azure-portal)。

    > [!WARNING] 
    > **VisionAnalysisEndpoint**变量可能不同于在此示例中指定的变量。 "**美国西部**" 严格指为 "美国西部" 区域创建的服务实例。 用[终结点 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)更新此值;下面是一些可能的示例:
    > - 西欧:`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 东南亚:`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 澳大利亚东部:`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  现在需要添加用于唤醒的代码。 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  接下来, 添加协同程序 (使用其下面的静态流方法), 该方法将获取*ImageCapture*类捕获的映像的分析结果。 

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

9.  在返回到*Unity*之前, 请务必保存*Visual Studio*中所做的更改。
10. 返回 Unity 编辑器, 单击 "**脚本**" 文件夹中的*VisionManager*和*ImageCapture*类, 然后将其拖到*层次结构面板*中的**主相机**对象。 

## <a name="chapter-8--before-building"></a>第8章–生成之前

若要对应用程序进行全面测试, 需要将其旁加载到 HoloLens。
在执行此操作之前, 请确保:

-   [第2章](#chapter-2--set-up-the-unity-project)中提到的所有设置都已正确设置。 
-   所有脚本都附加到**相机**对象上。 
-   *主相机检查器面板*中的所有字段均已正确分配。
-   请确保将**身份验证密钥**插入到**authorizationKey**变量。
-   确保你还在*VisionManager*脚本中检查了你的终结点, 并且它与*你*的区域保持一致 (本文档默认使用*美国西部*)。

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>第9章–构建 UWP 解决方案并旁加载应用程序
此项目的 Unity 部分所需的所有内容现在均已完成, 因此可以从 Unity 构建它。

1.  导航到 "*生成设置* - "**文件 > 生成设置 ...**
2.  在*生成设置*窗口中, 单击 "**生成**"。

    ![从 Unity 生成应用](images/AzureLabs-Lab2-26.png)

3.  如果尚未这样做, 请勾选**Unity C#项目**。
4.  单击“生成” 。 Unity 将启动*文件资源管理器*窗口, 在该窗口中, 需要创建一个文件夹, 然后选择要在其中生成应用的文件夹。 立即创建该文件夹并将其命名为*应用*。 选择*应用*文件夹后, 按 "**选择文件夹**"。 
5.  Unity 将开始向*应用*文件夹生成项目。 
6.  Unity 完成生成 (可能需要一些时间) 后, 它会在生成的位置打开 "*文件资源管理器*" 窗口 (检查任务栏, 因为它可能不会始终出现在窗口之上, 但会通知你添加了一个新窗口)。

## <a name="chapter-10--deploy-to-hololens"></a>第10章–部署到 HoloLens

在 HoloLens 上部署:

1.  你将需要 HoloLens 的 IP 地址 (用于远程部署), 并确保你的 HoloLens 处于**开发人员模式**。 要实现此目的，请执行以下操作：

    1. 在戴上 HoloLens 的同时, 请打开**设置**。
    2. 中转到**网络 & Internet > wi-fi > 高级选项**
    3. 记下**IPv4**地址。
    4. 接下来, 导航回 "**设置**", 然后为**开发人员更新 & Security >** 
    5. 设置开发人员模式。

2.  导航到新的 Unity 生成 (*应用*文件夹), 并在*Visual Studio*中打开解决方案文件。
3.  在解决方案配置中, 选择 "**调试**"。
4.  在解决方案平台中, 选择 " **x86**,**远程计算机**"。 

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab2-27.png)
 
5.  请在 "**生成" 菜单**中, 单击 "**部署解决方案**", 将应用程序旁加载到 HoloLens。
6.  应用现在应显示在你的 HoloLens 上已安装的应用列表中, 可以启动了!

> [!NOTE]
> 若要部署到沉浸式耳机, 请将 "**解决方案平台**" 设置为 "*本地计算机*", 并将**配置**设置为 "*调试*", 将 " *x86* " 设置为**平台**。 然后, 使用 "**生成" 菜单**选择 "*部署解决方案*", 将部署到本地计算机。 

## <a name="your-finished-computer-vision-api-application"></a>已完成的计算机视觉 API 应用程序

恭喜, 你构建了一个使用 Azure 计算机视觉 API 来识别真实世界对象的混合现实应用, 并清楚地显示了所见的内容。

![实验室结果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

正如使用*标记*参数 (在*VisionManager*中使用的*终结点*中的出现), 扩展应用程序以检测其他信息;查看你可以访问的其他[参数。](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)

### <a name="exercise-2"></a>练习2

显示返回的 Azure 数据, 其显示方式更多, 而且可能会隐藏数字。 如机器人可能对用户讲话。
