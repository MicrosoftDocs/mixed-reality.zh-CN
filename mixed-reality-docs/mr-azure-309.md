---
title: MR 和 Azure 309-Application insights
description: 完成本课程，了解如何使用 Azure 应用程序 Insights 服务在混合现实应用程序内收集有关用户行为的分析。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，application insights，hololens，沉浸，vr
ms.openlocfilehash: 481fe3fc16ada06085a64c86867a1a892c76f2ad
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926899"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。  因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。  这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR 和 Azure 309： Application insights

![最终产品-启动](images/AzureLabs-Lab309-00.png)

在本课程中，您将学习如何使用 Azure 应用程序 Insights API 来收集有关用户行为的分析，将 Application Insights 功能添加到混合现实应用程序中。

Application Insights 是一项 Microsoft 服务，它允许开发人员从其应用程序中收集分析，并从易于使用的门户对其进行管理。 分析可以是从性能到你想要收集的自定义信息。 有关详细信息，请访问[Application Insights 页](https://azure.microsoft.com/services/application-insights/)。

完成本课程后，你将拥有一个混合现实沉浸式耳机应用程序，该应用程序将能够执行以下操作：

1.  允许用户注视并四处移动场景。
2.  通过使用注视并接近场景内对象来触发将分析发送到*Application Insights 服务*。
3.  该应用还将在服务上调用，并在过去24小时内获取有关用户最接近哪个对象的信息。 该对象会将其颜色更改为绿色。

本课程将介绍如何将 Application Insights 服务的结果获取到基于 Unity 的示例应用程序。 您可以将这些概念应用到您可能生成的自定义应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 309： Application insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要侧重于 Windows Mixed Reality 沉浸（VR）耳机，但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。 在本课程中，你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。 使用 HoloLens 时，可能会在语音捕获过程中注意到某些回声。

## <a name="prerequisites"></a>必备条件

> [!NOTE]
> 本教程面向具有 Unity 和C#的基本经验的开发人员。 另外，请注意，本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容（2018年7月）。 你可以随意使用最新的软件（如[安装工具](install-the-tools.md)一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件：

- [与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发
- [Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式](install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017。4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- 启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 带有内置麦克风的一组耳机（如果耳机没有内置麦克风和扬声器）
- Azure 安装和 Application Insights 数据检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。

> [!WARNING] 
> 请注意，转到*Application Insights*的数据需要一些时间，因此请耐心等待。 如果要检查服务是否已收到数据，请查看第[14 章](#chapter-14---the-application-insights-service-portal)，其中显示了如何导航门户。

## <a name="chapter-1---the-azure-portal"></a>第1章-Azure 门户

若要使用*Application Insights*，你将需要在 Azure 门户中创建和配置*Application Insights 服务*。

1.  登录到[Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。

2.  登录后，单击左上角的 "**新建**"，搜索 " *Application Insights*"，然后单击 " **Enter**"。

    > [!NOTE]
    > 在较新的门户中，可能已将 "**新建**" 一词替换为 "**创建资源**"。

    ![Azure 门户](images/AzureLabs-Lab309-01.png)

3.  向右的新页将提供*Azure 应用程序 Insights*服务的说明。 在此页的左下角，选择 "**创建**" 按钮以创建与此服务的关联。

    ![Azure 门户](images/AzureLabs-Lab309-02.png)

4.  单击 "**创建**" 后：

    1.  为此服务实例插入所需的**名称**。

    2.  对于 "**应用程序类型**"，选择 "**常规**"。

    3.  选择相应的**订阅**。

    4.  选择一个**资源组**，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。

        > 若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5.  选择一个**位置**。

    6.  还需要确认是否已了解应用于此服务的条款和条件。

    7.  选择“创建”。

        ![Azure 门户](images/AzureLabs-Lab309-03.png)

5.  单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。

6.  创建服务实例后，门户中将显示一个通知。

    ![Azure 门户](images/AzureLabs-Lab309-04.png)

7.  单击通知以浏览新服务实例。

    ![Azure 门户](images/AzureLabs-Lab309-05.png)

8.  单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。 你将转到新的*Application Insights 服务*实例。

    ![Azure 门户](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  使此网页保持打开状态且易于访问，你会经常回来查看收集的数据。

    > [!IMPORTANT]
    > 若要实现 Application Insights，你将需要使用三个（3）个特定值：**检测密钥**、**应用程序 ID**和**API 密钥**。 下面你将了解如何从服务中检索这些值。 请确保在空白*记事本*页面上记下这些值，因为在代码中不久会用到它们。

9.  若要查找**检测密钥**，你将需要向下滚动服务功能列表，然后单击 "**属性**"，显示的选项卡将显示**服务密钥**。

    ![Azure 门户](images/AzureLabs-Lab309-07.png)

10. 下面是一些**属性**，你将发现需要单击的**API 访问权限**。 右侧面板将提供应用的**应用程序 ID** 。

    ![Azure 门户](images/AzureLabs-Lab309-08.png)

11. 在**应用程序 ID**面板仍处于打开状态的情况下，单击 "**创建 api 密钥**"，这将打开 "*创建 api 密钥*" 面板。

    ![Azure 门户](images/AzureLabs-Lab309-09.png)

12. 在现在打开 "*创建 API 密钥*" 面板中，键入说明，并**勾选三个框**。

13. 单击 "**生成密钥**"。 将创建并显示你的**API 密钥**。 

    ![Azure 门户](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > 这是你的**服务密钥**的唯一显示时间，因此请确保现在复制它。

## <a name="chapter-2---set-up-the-unity-project"></a>第2章-设置 Unity 项目

下面是使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。

1.  打开*Unity* ，并单击 "**新建**"。

    ![设置 Unity 项目](images/AzureLabs-Lab309-11.png)

2.  现在需要提供 Unity 项目名称，将**MR\_Azure\_应用程序\_Insights**。 请确保将*模板*设置为**3d**。 将位置设置为合适的*位置*（请记住，更接近根目录更好）。 然后单击 "**创建项目**"。

    ![设置 Unity 项目](images/AzureLabs-Lab309-12.png)

3.  当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "**编辑 \> 首选项**"，然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

    ![设置 Unity 项目](images/AzureLabs-Lab309-13.png)

4.  接下来，通过单击 "**切换平台**" 按钮转到 "**文件 \> 生成设置**"，并将平台切换到**通用 Windows 平台**。

    ![设置 Unity 项目](images/AzureLabs-Lab309-14.png)

5.  请参阅**文件 \> 生成设置**，并确保：

    1.  **目标设备**设置为**任何设备**

        > 对于 Microsoft HoloLens，将 "**目标设备**" 设置为 " *hololens*"。

    2.  **生成类型**设置为**D3D**

    3.  **SDK**设置为 "**最新安装**"

    4.  "**生成并运行**" 设置为 "**本地计算机**"

    5.  保存场景并将其添加到生成中。

        1.  通过选择 "**添加打开的场景**" 来执行此操作。 将显示 "保存" 窗口。

            ![设置 Unity 项目](images/AzureLabs-Lab309-15.png)

        2. 为此创建新的文件夹，并在将来的任何场景中，单击 "**新建文件夹**" 按钮，创建一个新文件夹，将其命名为**场景**。

            ![设置 Unity 项目](images/AzureLabs-Lab309-16.png)

        3. 打开新创建的**场景**文件夹，然后在 "文件名 *：* 文本" 字段中，键入**ApplicationInsightsScene**，然后单击 "**保存**"。

            ![设置 Unity 项目](images/AzureLabs-Lab309-17.png)

6.  现在，"**生成设置**" 中的其余设置应保留为默认值。

7.  在 "**生成设置**" 窗口中，单击 "**播放机设置**" 按钮，这会在**检查器**所在的空间中打开相关面板。

    ![设置 Unity 项目](images/AzureLabs-Lab309-18.png)

8. 在此面板中，需要验证几项设置：

    1.  在 "**其他设置**" 选项卡中：

        1.  **脚本** **运行时版本**应为试验性的 **（.net 4.6 等效项）** ，这会触发重新启动编辑器的需要。

        2.  **脚本编写后端**应为 **.net**

        3.  **API 兼容级别**应为 **.net 4.6**

        ![设置 Unity 项目](images/AzureLabs-Lab309-19.png)

    2.  在 "**发布设置**" 选项卡的 "**功能**" 下，检查：

        - **InternetClient**     

            ![设置 Unity 项目](images/AzureLabs-Lab309-20.png)

    3.  在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK** 。

        ![设置 Unity 项目](images/AzureLabs-Lab309-21.png)

9.  返回**生成设置**， **Unity C#项目**不再灰显;勾选此的旁边的复选框。

10.  关闭 "生成设置" 窗口。

11.  保存场景和项目（**file** > **SAVE 场景/FILE** > **save Project**）。


## <a name="chapter-3---import-the-unity-package"></a>第3章-导入 Unity 包

> [!IMPORTANT]
> 如果要跳过*Unity 设置*本课程的组件，并继续直接进入代码，请随时下载此[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)，并将其作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入到项目中。 这还将包含下一章中的 Dll。 导入后，继续[**第6章**](#chapter-6---create-the-applicationinsightstracker-class)。

> [!IMPORTANT]
> 若要在 Unity 内使用 Application Insights，需要为其导入 DLL 以及 Newtonsoft.json DLL。 当前 Unity 中存在一个已知问题，需要在导入后重新配置插件。 解决 bug 后，将不再需要这些步骤（本部分中的 4-7）。

若要将 Application Insights 导入到自己的项目中，请确保已[下载包含插件的 ". unitypackage"](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)。 然后，执行以下操作：

1.  使用 "**资产 \> 导入包 \> 自定义包**" 菜单选项将**Unitypackage**添加到 Unity。

2.  在弹出的 "**导入 Unity 包**" 框中，确保选择了 "所有" （并包括）**插件**。

    ![导入 Unity 包](images/AzureLabs-Lab309-22.png)

3.  单击 "**导入**" 按钮，将项添加到项目。

4.  在项目视图中，在 "**插件**" 下中转到 " **Insights** " 文件夹，并*仅*选择以下插件：

    -   Applicationinsights.config

    ![导入 Unity 包](images/AzureLabs-Lab309-23.png)

5.  选择此*插件*后，请确保**未选中** **任何平台**，然后确保**WSAPlayer**未被**选中**，然后单击 "**应用**"。 这样做只是为了确认正确配置了文件。

    ![导入 Unity 包](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > 标记此类插件，将它们配置为仅在 Unity 编辑器中使用。 WSA 文件夹中有一组不同的 Dll，将在从 Unity 导出项目后使用。

6.  接下来，需要在**Insights**文件夹内打开**WSA**文件夹。 你将看到刚才配置的同一文件的副本。 选择此文件，然后在 "检查器" 中，确保**未选中** **任何平台**，然后确保**只** **选中**" **WSAPlayer** "。 单击**应用**。

    ![导入 Unity 包](images/AzureLabs-Lab309-25.png)

7. 你现在需要遵循**步骤 4-6**，但要改为*newtonsoft.json*插件。 若要查看结果，请参阅下面的屏幕截图。

    ![导入 Unity 包](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>第4章-设置照相机和用户控件

在本章中，你将设置照相机和控件，以允许用户在场景中查看和移动。

1.  右键单击 "层次结构" 面板中的空白区域，然后在 "**创建** > **空**"。

    ![设置照相机和用户控件](images/AzureLabs-Lab309-26.png)

2.  将新的空 GameObject 重命名为**相机父项**。

    ![设置照相机和用户控件](images/AzureLabs-Lab309-27.png)

3.  右键单击 "层次结构" 面板中的空白区域，然后在 "**三维对象**" 上右键单击，然后单击 "**球面**"。

4.  将球体重命名为**右手**。

5.  将右侧的**转换比例**设置为**0.1、0.1、0.1**

    ![设置照相机和用户控件](images/AzureLabs-Lab309-28.png)

6.  单击 "*球碰撞*器" 组件中的**齿轮**，然后单击 "**删除组件**"，从右侧删除**球碰撞**器组件。

    ![设置照相机和用户控件](images/AzureLabs-Lab309-29.png)

7.  在 "层次结构" 面板中，将**主相机**和**右手**的对象拖到**相机父**对象上。

    ![设置照相机和用户控件](images/AzureLabs-Lab309-30.png)

8.  将**主相机**和**右侧**对象的**变换位置**设置为**0，0，0**。

    ![设置照相机和用户控件](images/AzureLabs-Lab309-31.png)

    ![设置照相机和用户控件](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>第5章-在 Unity 场景中设置对象

现在，您将为您的场景创建一些基本形状，使用户能够与之进行交互。

1.  右键单击 "*层次结构" 面板*中的空白区域，然后在**3d 对象**上单击，然后选择 "**平面**"。

2.  将平面**转换位置**设置为**0，-1，0**。

3.  将平面**转换比例**设置为**5、1、5**。

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-33.png)

4.  创建要用于**飞机**对象的基本材料，以便更易于查看其他形状。 导航到*项目面板*，右键单击，然后选择 "**创建**"，然后单击 "**文件夹**"，创建一个新文件夹。 命名 it**材料**。

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-34.png) ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-35.png)

5.  打开**材料**文件夹，然后右键单击，单击 "**创建**"，然后单击 "**材料**" 创建新材料。 将其命名为**蓝色**。

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-36.png) ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-37.png)

6.  选择新的**蓝色**材料后，查看*检查器*，并单击矩形窗口和**Albedo**。 选择蓝色（下图是**十六进制颜色： \#3592FFFF**）。 选择后，单击 "关闭" 按钮。

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-38.png)

7.  将新材料从 "**材料**" 文件夹拖到场景内新创建的**平面**上（或将其放置在*层次结构*内的**平面**对象上）。

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-39.png)

8.  右键单击 "*层次结构" 面板*中的空白区域，然后在**3d 对象**上单击 "胶囊"。

    -  选择**胶囊**后，将其**转换***位置*更改为： **-10，1，0**。

9.  右键单击 "*层次结构" 面板*中的空白区域，然后单击 "**三维对象"、"多维数据集**"。

    -  选择**多维数据集**后，将**其转换***位置*更改为： **0，0，10**。

10. 右键单击 "*层次结构" 面板*中的空白区域，然后单击 "**三维对象" "球面**"。

    -  选择**球**后，将其**转换***位置*更改为： **10，0，0**。

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > 这些*位置*值是*建议*。 您可以自由地将对象的位置设置为您想要的任何内容，但如果对象距离离照相机的距离不是太远，那么应用程序的用户会更容易。

11. 当你的应用程序正在运行时，它需要能够识别场景中的对象。若要实现此目的，需要对其进行标记。 选择其中一个对象，然后在 "*检查器*" 面板中，单击 "**添加标记 ...** "，它会将*检查器*与 "**标记" & "层**" 面板。

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. 单击 " **+" （加号）** 符号，并将标记名称键入为 " **ObjectInScene**"。

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > 如果为标记使用了不同的名称，则需要确保此更改也会成为*DataFromAnalytics*、 *ObjectTrigger*和*注视*、脚本，以便在场景中找到并检测到你的对象。

13. 创建标记后，现在需要将其应用于所有三个对象。 在*层次结构*中，按住**Shift**键，然后单击**胶囊**、 **Cube**和**球体**、对象，然后在*检查器*中单击下拉菜单和**标记**，然后单击创建的*ObjectInScene*标记。

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>第6章-创建 ApplicationInsightsTracker 类

需要创建的第一个脚本是**ApplicationInsightsTracker**，它负责：

1.  基于用户交互创建事件以提交到 Azure 应用程序 Insights。

2. 创建相应的事件名称，具体取决于用户交互。

3. 正在将事件提交到 Application Insights 服务实例。

若要创建此类：

1.  右键单击 "*项目" 面板*，然后**创建** > **文件夹**。 命名文件夹**脚本**。

    ![创建 ApplicationInsightsTracker 类](images/AzureLabs-Lab309-46.png)  ![创建 ApplicationInsightsTracker 类](images/AzureLabs-Lab309-47.png)

2.  创建**脚本**文件夹后，双击它以打开。 然后，在该文件夹中，右键单击，**创建** >  **C#脚本**。 将脚本命名为**ApplicationInsightsTracker**。

3.  双击新的**ApplicationInsightsTracker**脚本以通过**Visual Studio**打开它。

4.  更新脚本顶部的命名空间，如下所示：

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  在类中插入以下变量：

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > 按照第[1 章第 1](#chapter-1---the-azure-portal)步中所述，使用 Azure 门户中的*服务密钥*，正确设置**instrumentationKey、applicationId 和 API_Key**值。

6.  然后添加**Start （）** 和**唤醒（）** 方法，在类初始化时将调用该方法：

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  添加负责发送应用程序注册的事件和度量值的方法：

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-7---create-the-gaze-script"></a>第7章-创建注视脚本

要创建的下一个脚本是**注视**脚本。 此脚本负责创建将从*主相机*向前投影的*Raycast* ，以检测用户正在查看的对象。 在这种情况下， *Raycast*需要确定用户是否正在使用**ObjectInScene**标记查看对象，然后计算用户在该对象上的*gazes* 。

1.  双击 "**脚本**" 文件夹以将其打开。

2.  右键单击 "**脚本**" 文件夹中，单击 "**创建** >  **C#脚本**"。 将脚本命名为 "**注视**"。

3.  双击脚本以通过 Visual Studio 打开它。

4.  将现有代码替换为以下代码：

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  现在需要添加**唤醒（）** 和**Start （）** 方法的代码。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  在 "**注视**" 类中，将以下代码添加到**Update （）** 方法中以投影*Raycast*并检测目标命中：

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  添加**ResetFocusedObject （）** 方法，以便在用户查看对象时将数据发送到**Application Insights** 。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  你现在已经完成了**注视**脚本。 在返回到*Unity*之前，在*Visual Studio*中保存更改。

## <a name="chapter-8---create-the-objecttrigger-class"></a>第8章-创建 ObjectTrigger 类

需要创建的下一个脚本是**ObjectTrigger**，它负责：

- 向主相机添加冲突所需的组件。
- 检测照相机是否位于标记为 " **ObjectInScene**" 的对象附近。

创建脚本：

1.  双击 "**脚本**" 文件夹以将其打开。

2.  右键单击 "**脚本**" 文件夹中，单击 "**创建** >  **C#脚本**"。 将脚本命名为**ObjectTrigger**。

3.  双击脚本以通过 Visual Studio 打开它。 将现有代码替换为以下代码：

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-9---create-the-datafromanalytics-class"></a>第9章-创建 DataFromAnalytics 类

现在，你将需要创建**DataFromAnalytics**脚本，该脚本负责：

- 正在获取有关照相机最接近哪个对象的分析数据。
- 使用*服务密钥*，这允许与 Azure 应用程序 Insights 服务实例通信。
- 根据具有最高事件计数的场景中的对象进行排序。
- 将最接近的对象的材料颜色更改为*绿色*。

创建脚本：

1.  双击 "**脚本**" 文件夹以将其打开。

2.  右键单击 "**脚本**" 文件夹中，单击 "**创建** >  **C#脚本**"。 将脚本命名为**DataFromAnalytics**。

3.  双击脚本以通过 Visual Studio 打开它。

4.  插入以下命名空间：

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  在脚本中，插入以下内容：

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  在**DataFromAnalytics**类中，在**Start （）** 方法的后面添加以下名为**FetchAnalytics （）** 的方法。 此方法负责填充键值对的列表，其中包含*GameObject*和占位符事件计数号。 然后初始化**GetWebRequest （）** 协同程序。 在此方法中，还可以找到对*Application Insights*的调用的查询结构，作为*查询 URL*终结点。

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  在**FetchAnalytics （）** 方法的下方，添加一个名为**GetWebRequest （）** 的方法，该方法将返回*IEnumerator*。 此方法负责请求在*Application Insights*中调用与特定*GameObject*对应的事件次数。 所有发送的查询都返回后，将调用**DetermineWinner （）** 方法。

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  下一方法为**DetermineWinner （）** ，该方法根据最大事件计数对*GameObject*和*Int*对的列表进行排序。 然后，它会将该*GameObject*的材料颜色更改为*绿色*（作为其最大计数的反馈）。 这将显示一条包含分析结果的消息。

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  添加用来反序列化从*Application Insights*接收的 JSON 对象的类结构。 将这些类添加到类定义**之外**的**DataFromAnalytics**类文件的最底部。

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. 在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-10---create-the-movement-class"></a>第10章-创建移动类

**移动**脚本是需要创建的下一个脚本。 它负责：

- 根据相机正在寻找的方向移动主摄像机。
- 将所有其他脚本添加到场景对象。

创建脚本：

1.  双击 "**脚本**" 文件夹以将其打开。

2.  右键单击 "**脚本**" 文件夹中，单击 "**创建** >  **C#脚本**"。 命名脚本**移动**。

3.  双击脚本以通过*Visual Studio*打开它。

4.  将现有代码替换为以下代码：

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  在**移动**类中的空**Update （）** 方法*下*，插入以下允许用户使用手形控制器移动到虚拟空间中的方法：

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  最后，在**Update （）** 方法内添加方法调用。

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。

## <a name="chapter-11---setting-up-the-scripts-references"></a>第11章-设置脚本引用

在本章中，需要将**移动**脚本放到**相机父节点**上，并设置其引用目标。 然后，该脚本会处理需要的其他脚本。

1.  从 "*项目" 面板*的 "**脚本**" 文件夹中，将**移动**脚本拖到 "*层次结构" 面板*中的 "**相机父**对象"。

    ![设置 Unity 场景中的脚本引用](images/AzureLabs-Lab309-48.png)

2.  单击 "**照相机" 父项**。 在 "*层次结构" 面板*中，将**右侧**对象从 "*层次结构" 面板*拖动到 "*检查器" 面板*中的引用目标**控制器**。 将**用户速度**设置为**5**，如下图所示。

    ![设置 Unity 场景中的脚本引用](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>第12章-生成 Unity 项目

此项目的 Unity 部分所需的所有内容现在均已完成，因此可以从 Unity 构建它。

1.  导航到 "**生成设置**" （**文件** > **生成设置**）。

2.  在**生成设置**窗口中，单击 "**生成**"。

    ![将 Unity 项目生成到 UWP 解决方案](images/AzureLabs-Lab309-50.png)

3.  将弹出一个 "**文件资源管理器**" 窗口，提示你输入生成的位置。 在左上角单击 "**新建文件夹**"，创建一个新文件夹，并将其命名为 "**生成**"。

    ![将 Unity 项目生成到 UWP 解决方案](images/AzureLabs-Lab309-51.png)

    1.  打开 "新建**生成**" 文件夹，并创建另一个文件夹（使用 "**新文件夹**"），并将其命名为 " **MR\_Azure\_application\_Insights**"。

        ![将 Unity 项目生成到 UWP 解决方案](images/AzureLabs-Lab309-52.png)

    2.  选中 "**尊敬的\_Azure\_应用程序\_Insights** " 文件夹，单击 "**选择文件夹**"。 项目将需要一分钟或更长时间才能生成。

4.  以下*生成*将显示**文件资源管理器**，显示新项目的位置。

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a>第13章-将 MR_Azure_Application_Insights 应用部署到计算机

若要在本地计算机上部署**Azure\_应用程序\_的 MR\_** ，请执行以下操作：

1.  在**Visual Studio**中打开**Azure\_application\_Insights 应用的 MR\_** 解决方案文件。

2.  在**解决方案平台**中，选择 " **X86，本地计算机**"。

3.  在**解决方案配置**中，选择 "**调试**"。

    ![将 Unity 项目生成到 UWP 解决方案](images/AzureLabs-Lab309-53.png)

4.  中转到 "**生成" 菜单**，然后单击 "**部署解决方案**"，将应用程序旁加载到计算机上。

5.  应用现在应显示在已安装的应用列表中，可以启动。

6. 启动混合现实应用程序。

7. 在场景中四处移动，接近对象并进行查看，当*Azure 见解服务*收集了足够的事件数据时，它会将最接近绿色的对象设置为最接近绿色的对象。

> [!IMPORTANT] 
> 尽管服务收集*事件和指标*的平均等待时间大约需要15分钟，但在某些情况下，可能需要长达1小时的时间。

## <a name="chapter-14---the-application-insights-service-portal"></a>第14章-Application Insights 服务门户

漫游场景并在多个对象上 gazed 时，可以看到*Application Insights 服务*门户中收集的数据。

1.  返回 Application Insights 服务门户。

2.  单击*指标资源管理器*。

    ![查看收集的数据](images/AzureLabs-Lab309-54.png)

3.  它将在一个包含关系图的选项卡中打开，该图形表示与应用程序相关的*事件和指标*。 如上所述，在图形中显示数据可能需要一些时间（最长为1小时）

    ![查看收集的数据](images/AzureLabs-Lab309-55.png)

4.  单击 "按应用程序版本列出的*事件总数*" 中的 "*事件*"，以查看事件及其名称的详细明细。

    ![查看收集的数据](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>已完成 Application Insights 服务应用程序

恭喜，你构建了一个混合现实应用，它利用 Application Insights 服务来监视你的应用中的用户活动。

![课程结果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>额外练习

**练习1**

尝试生成，而不是手动创建 ObjectInScene 对象，并在脚本内的平面上设置它们的坐标。 通过这种方式，你可以询问 Azure 最常见的对象是什么（从注视或邻近的结果）并生成一个*额外*的对象。

**练习2**

按时间对 Application Insights 结果进行排序，以便获取最相关的数据，并在应用程序中实现该时间敏感的数据。

