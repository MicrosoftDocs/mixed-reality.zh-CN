---
title: MR 和 Azure 304-人脸识别
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合现实, 学院, unity, 教程, api, 人脸识别, hololens, 沉浸, vr
ms.openlocfilehash: 7cd2a6683c80279129934c619a9b9cb857badf67
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047186"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR 和 Azure 304:人脸识别

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

在本课程中, 你将了解如何使用 Azure 认知服务和 Microsoft 人脸 API 将人脸识别功能添加到混合现实应用程序中。

*Azure 人脸 API*是一项 Microsoft 服务, 它为开发人员提供了最先进的面部算法, 一切都在云中。 该*人脸 API*有两个主要功能: 具有属性的面部检测和人脸识别。 这使开发人员可以简单地设置一组人脸, 然后在以后将查询图像发送到该服务, 以确定人脸属于哪个组。 有关详细信息, 请访问[Azure 面部识别页](https://azure.microsoft.com/services/cognitive-services/face/)。

完成本课程后, 你将拥有一个混合现实 HoloLens 应用程序, 该应用程序将能够执行以下操作:

1. 使用 "**点击" 笔势**来启动使用板载 HoloLens 相机捕获映像。 
2. 将捕获的映像发送到*Azure 人脸 API*服务。
3. 接收*人脸 API*算法的结果。
4. 使用简单的用户界面, 显示匹配人员的名称。

这会教你如何将人脸 API 服务的结果获取到基于 Unity 的混合现实应用程序中。

在您的应用程序中, 您将由您来决定如何将结果与您的设计相集成。 本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。 您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 304:人脸识别</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要侧重于 HoloLens, 但你也可以将本课程中学习的内容应用于 Windows Mixed Reality 沉浸 (VR) 耳机。 由于沉浸式 (VR) 耳机没有可访问的摄像机, 因此需要连接到电脑的外部照相机。 在本课程中, 您将看到有关支持沉浸式 (VR) 耳机时可能需要执行的任何更改的说明。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程面向具有 Unity 和C#的基本经验的开发人员。 另外请注意, 本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容 (5 月 2018)。 您可以随意使用最新的软件 (如[安装工具](install-the-tools.md)一文中所述), 但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件:

- [与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC, 用于沉浸式 (VR) 耳机开发
- [Windows 10 秋季创意者更新 (或更高版本) 已启用开发人员模式](install-the-tools.md)
- [最新的 Windows 10 SDK](install-the-tools.md)
- [Unity 2017。4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- 启用了开发人员模式的[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)
- 连接到电脑的相机 (适用于沉浸式耳机开发)
- Azure 安装和人脸 API 检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

1.  为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。
2.  设置并测试你的 HoloLens。 如果需要支持设置 HoloLens, 请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  在开始开发新的 HoloLens 应用程序时, 最好执行校准和传感器调整 (有时它可以帮助为每个用户执行这些任务)。 

有关校准的帮助信息, 请单击此链接, 了解[到 HoloLens 校准文章](calibration.md#hololens-2)。

有关传感器优化的帮助, 请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。

## <a name="chapter-1---the-azure-portal"></a>第1章-Azure 门户

若要在 Azure 中使用*人脸 API*服务, 你将需要配置服务的实例, 使其可用于你的应用程序。

1.  首先, 登录到[Azure 门户](https://portal.azure.com)。 

    > [!NOTE]
    > 如果还没有 Azure 帐户, 则需要创建一个。 如果在课堂或实验室中按照本教程进行学习, 请咨询教师或 proctors, 以获得设置新帐户的帮助。

2.  登录后, 单击左上角的 "**新建**", 然后搜索 "*人脸 API*", 按**enter**。

    ![搜索人脸 api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 在较新的门户中, 可能已将 "**新建**" 一词替换为 "**创建资源**"。

3.  新页将提供*人脸 API*服务的说明。 在此提示符下, 选择 "**创建**" 按钮以创建与此服务的关联。

    ![人脸 api 信息](images/AzureLabs-Lab4-02.png)

4.  单击 "**创建**" 后:

    1. 为此服务实例插入所需的名称。

    2. 选择订阅。

    3. 选择适合你的定价层, 如果这是第一次创建*人脸 API 服务*, 则你应该可以使用免费层 (名为 F0)。

    4. 选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务 (例如这些实验室) 保存在一个公共资源组中。 

        > 若要了解有关 Azure 资源组的详细信息, 请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

    5. 你稍后使用的 UWP 应用 (**人员 Maker**) 要求使用 "美国西部" 作为位置。

    6. 还需要确认是否已了解应用于此服务的条款和条件。

    7. 选择**创建*。**

        ![创建人脸 api 服务](images/AzureLabs-Lab4-03.png)

5.  一旦你单击 **创建*** 必须要等待的时间来创建服务，这可能需要一分钟的时间。

6.  创建服务实例后, 门户中将显示一个通知。

    ![服务创建通知](images/AzureLabs-Lab4-04.png)

7.  单击通知以浏览新服务实例。

    ![中转到资源通知](images/AzureLabs-Lab4-05.png)

8.  准备就绪后, 请单击通知中的 "**中转到资源**" 按钮, 以浏览新服务实例。

    ![访问人脸 api 密钥](images/AzureLabs-Lab4-06.png)

9.  在本教程中, 你的应用程序将需要调用你的服务, 这是通过使用你的服务的订阅 "密钥" 来完成的。 从 "*人脸 API*服务" 的 "*快速启动*" 页中, 第一个点为数字 1, 以*获取密钥。*

10. 在 "*服务*" 页上, 选择 "蓝色**键**" 超链接 (如果在 "快速启动" 页上), 或选择 "服务" 导航菜单中的 "**密钥**" 链接 (位于左侧, 由 "密钥" 图标表示), 以显示你的密钥。

    > [!NOTE] 
    > 记下其中一个密钥并对其进行保护, 因为稍后需要用到它。

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>第2章-使用 "人员 Maker" UWP 应用程序

请确保下载名为[Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)的预生成的 UWP 应用程序。 此应用并不是本课程的最终产品, 只是一种工具, 可帮助你创建 Azure 条目, 后面的项目将依赖于这些条目。

**人员制造商**允许您创建与人员和人员组相关联的 Azure 条目。 应用程序会将所需的所有信息以一种格式放置在以后由 FaceAPI 使用的格式, 以便识别已添加的人员的人脸。 

> 无关紧要**人员 Maker**使用一些基本限制, 以帮助确保没有超过**免费订阅层**每分钟的服务调用数。 当发生限制时, 顶部的绿色文本将更改为红色, 并更新为 "活动"。如果是这种情况, 只需等待应用程序 (它将等待, 直到接下来可以继续访问面部服务, 并在可以再次使用它时将其更新为 "活动中"。

此应用程序使用*microsoft.projectoxford.face*库, 可让你充分利用人脸 API。 此库以 NuGet 包的形式提供。 有关此情况的详细信息以及类似的 Api, 请[确保访问 api 参考文章](https://docs.microsoft.com/azure/cognitive-services/face/apireference)。

> [!NOTE] 
> 这些只是所需的步骤, 有关如何执行这些操作的说明, 请查看该文档。 **人员 Maker**应用允许你:
>
> - 创建一个*用户组*, 该组由要与之关联的多个用户组成。 利用 Azure 帐户, 可以托管多个人员组。
>
> - 创建作为人员组成员的*人员*。 每个人都有多个与之关联的人*脸*图像。
>
> -  将人*脸图像*分配给某个*人*, 使 Azure 人脸 API 服务能够按相应的人*脸*识别该*人*。
>
> -  *训练* *Azure 人脸 API 服务*。

请注意, 若要训练此应用以识别用户, 你需要将每个用户的 10 (10) 张近照片照片添加到你的人员组。 Windows 10 Cam 应用可帮助你获取这些信息。 您必须确保每张照片清晰 (避免模糊、遮蔽, 或远离使用者), 将照片设置为 jpg 或 png 文件格式, 图像文件大小不能超过**4 MB**, 且不能小于**1 KB**。

> [!NOTE]
> 如果按照本教程进行操作, 请不要使用自己的人脸进行定型, 因为当你将 HoloLens 投入使用时, 你将无法亲自寻找。 使用同事或学生。

正在运行**人员制造商**:

1.  打开**PersonMaker**文件夹, 然后双击*PersonMaker 解决方案*以通过*Visual Studio*打开它。

2.  *PersonMaker 解决方案*打开后, 请确保:

    1. *解决方案配置*设置为 "**调试**"。

    2. *解决方案平台*设置为**x86**

    3. *目标平台*为**本地计算机**。

    4.  你还可能需要*还原 NuGet 包*(右键单击*解决方案*并选择 "**还原 NuGet 包**")。

3.  单击 "*本地计算机*", 应用程序将启动。 请注意, 在较小屏幕上, 所有内容可能都不可见, 不过您可以向下滚动查看。

    ![人员制造商用户界面](images/AzureLabs-Lab4-07.png)

4.  从 Azure 中的*人脸 API*服务插入你应该具有的**Azure 身份验证密钥**。

5.  &

    1. 要分配给*人员组*的*ID* 。 ID 必须是小写, 且不能包含空格。 记下此 ID, 因为稍后会在 Unity 项目中需要它。
    2. 要分配给*人员组*的*名称*(可以有空格)。


6.  按 "**创建人员组**" 按钮。 此按钮下应显示一条确认消息。

> [!NOTE]
> 如果出现 "拒绝访问" 错误, 请检查为 Azure 服务设置的位置。 如上所述, 此应用程序是为 "美国西部" 设计的。

> [!IMPORTANT]
> 你会注意到, 你也可以单击 "**提取已知组**" 按钮: 这适用于你是否已创建人员组, 而不是创建新人员组。 请注意, 如果单击 "创建具有已知组的*人员组*", 则还会提取组。

7.  插入要创建的*人员*的*名称*。

    1. 单击 "**创建人员**" 按钮。

    2. 此按钮下应显示一条确认消息。

    3. 如果要删除先前创建的用户, 可以将该名称写入 textbox 并按**Delete person**

8.  请确保知道要添加到组中的用户的 10 (10) 个照片的位置。

9.  按 "**创建并打开文件夹**", 打开 Windows 资源管理器, 使其与该人员关联。 在文件夹中添加十 (10) 个图像。 它们必须是*JPG*或*PNG*文件格式。

10. 单击 "**提交到 Azure**"。 计数器将显示提交状态, 后跟消息完成后的消息。

11. 计数器完成并显示一条确认消息后, 单击 "**训练**" 以训练你的服务。

完成此过程后, 就可以开始迁移到 Unity。

## <a name="chapter-3---set-up-the-unity-project"></a>第3章-设置 Unity 项目

下面是用于使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。

1.  打开*Unity* , 并单击 "**新建**"。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab4-08.png)

2.  现在需要提供 Unity 项目名称。 插入**MR_FaceRecognition**。 请确保 "项目类型" 设置为 " **3d**"。 将位置设置为合适的**位置**(请记住, 更接近根目录更好)。 然后单击 "**创建项目**"。

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab4-09.png)

3.  当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 "**编辑 > 首选项**", 然后在新窗口中导航到 "**外部工具**"。 将**外部脚本编辑器**更改为**Visual Studio 2017**。 关闭 "**首选项**" 窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab4-10.png)

4.  接下来, 通过单击 "**切换平台**" 按钮转到 "**文件 > 生成设置**", 并将平台切换到**通用 Windows 平台**。

    ![生成设置窗口, 将平台切换到 UWP。](images/AzureLabs-Lab4-11.png)

5.  请参阅**文件 > 生成设置**, 并确保:

    1. **目标设备**设置为**HoloLens**

        > 对于沉浸式耳机, 将 "**目标设备**" 设置为 "*任何设备*"。

    2. **生成类型**设置为**D3D**
    3. **SDK**设置为 "**最新安装**"
    4. **Visual Studio 版本**设置为 "**最新安装**"
    5. "**生成并运行**" 设置为 "**本地计算机**"
    6. 保存场景并将其添加到生成中。 

        1. 通过选择 "**添加打开的场景**" 来执行此操作。 将显示 "保存" 窗口。

            ![单击 "添加打开的场景" 按钮](images/AzureLabs-Lab4-12.png)

        2. 选择 "**新建文件夹**" 按钮, 创建一个新文件夹, 将其命名为**场景**。

            !["创建新脚本" 文件夹](images/AzureLabs-Lab4-13.png)

        3. 打开新创建的**场景**文件夹, 然后在 "文件名: 文本" 字段中, 键入**FaceRecScene**, 然后按 "**保存**"。

            ![为新场景指定名称。](images/AzureLabs-Lab4-14.png)

    7. 现在, "*生成设置*" 中的其余设置应保留为默认值。

6. 在 "*生成设置*" 窗口中, 单击 "**播放机设置**" 按钮, 这会在*检查器*所在的空间中打开相关面板。 

    ![打开播放机设置。](images/AzureLabs-Lab4-15.png)

7. 在此面板中, 需要验证几项设置:

    1. 在 "**其他设置**" 选项卡中:

        1. **脚本编写** **运行时版本**应**实验**（.NET 4.6 等效）。 更改此将触发需要重新启动编辑器。
        2. **脚本编写后端**应为 **.net**
        3. **API 兼容级别**应为 **.net 4.6**

            ![更新其他设置。](images/AzureLabs-Lab4-16.png)
      
    2. 在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:

        - **InternetClient**
        - **摄像头**

            ![正在更新发布设置。](images/AzureLabs-Lab4-17.png)

    3. 在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 在 "**支持的虚拟现实**" 下, 确保已添加**Windows Mixed reality SDK** 。

        ![更新 X R 设置。](images/AzureLabs-Lab4-18.png)

8.  返回*生成设置*, **Unity C#项目**不再灰显;勾选此的旁边的复选框。 
9.  关闭 "生成设置" 窗口。
10. 保存场景和项目 (**file > SAVE 场景/file > SAVE Project**)。

## <a name="chapter-4---main-camera-setup"></a>第4章-照相机设置

> [!IMPORTANT]
> 如果希望跳过本课程的*Unity 设置*组件, 并继续直接进入代码, 可以[下载 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), 并将其作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)导入到项目中。 请注意, 此包还包含[第5章](#chapter-5--import-the-newtonsoftjson-library)中介绍的*newtonsoft.json DLL*的导入。 导入后, 你可以继续[第6章](#chapter-6---create-the-faceanalysis-class)。

1.  在 "*层次结构*" 面板中, 选择 "**摄像机**"。

2.  选择后, 你将能够在 "*检查器" 面板*中看到**主相机**的所有组件。

    1. **照相机对象**必须命名为 "**主相机**" (请注意拼写正确!)

    2. 必须将主相机**标记**设置为**MainCamera** (请注意拼写!)

    3. 请确保将**转换位置**设置为**0, 0, 0**

    4. 将**清除标志**设置为**纯色**

    5. 将相机组件的**背景**色设置为**黑色、Alpha 0 (十六进制代码: #00000000)**

        ![设置照相机组件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>第5章–导入 Newtonsoft.json 库

> [!IMPORTANT]
> 如果在[上一章](#chapter-4---main-camera-setup)中导入了 "unitypackage", 则可以跳过本章。

若要帮助您反序列化和序列化接收并发送到机器人服务的对象, 您需要下载*newtonsoft.json*库。 你将发现已使用此[unity 包文件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)中的正确 Unity 文件夹结构组织的兼容版本。 

导入库:

1.  下载 Unity 包。
2.  单击 "**资产**、**导入包**、**自定义包**"。

    ![导入 Newtonsoft.json 库](images/AzureLabs-Lab4-20.png)

3.  查找已下载的 Unity 包, 并单击 "打开"。
4.  确保包的所有组件都是勾选, 并单击 "**导入**"。

    ![导入 Newtonsoft.json 库](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>第6章-创建 FaceAnalysis 类

FaceAnalysis 类的目的是托管与 Azure 面部识别服务进行通信所需的方法。 

- 在将该服务发送到捕获映像后, 它将分析它并标识中的人脸, 并确定是否有任何一个属于已知人员。 
- 如果找到了一个已知人员, 此类会将其名称作为 UI 文本显示在场景中。

若要创建*FaceAnalysis*类:

 1. 右键单击位于 "项目" 面板中的 "*资产" 文件夹*, 然后单击 "**创建** > **文件夹**"。 调用文件夹**脚本**。 

    ![创建 FaceAnalysis 类。](images/AzureLabs-Lab4-22.png)

2.  双击刚创建的文件夹以将其打开。 
3.  右键单击文件夹内, 然后单击 "**创建** >   **C#脚本**"。 调用脚本*FaceAnalysis*。 
4.  双击新的*FaceAnalysis*脚本以通过 Visual Studio 2017 将其打开。
5.  在*FaceAnalysis*类上输入以下命名空间:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  现在需要添加用于 deserialising 的所有对象。 需要将这些对象添加到*FaceAnalysis*脚本**之外**(下花括号下)。 

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
7. 不会使用*Start ()* 和*Update ()* 方法, 因此请立即将其删除。 

8.  在*FaceAnalysis*类中, 添加以下变量:

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
    > 将**密钥**和**personGroupId**替换为你的服务密钥, 并将其 Id 替换为之前创建的组的 Id。

9.  添加*唤醒 ()* 方法, 该方法 initialises 类, 将*ImageCapture*类添加到主相机并调用标签创建方法:

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

10. 添加*CreateLabel ()* 方法, 该方法创建*标签*对象以显示分析结果:

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

11. 添加*DetectFacesFromImage ()* 和*GetImageAsByteArray ()* 方法。 前者会请求面部识别服务检测提交的图像中任何可能的人脸, 而后者则需要将捕获的图像转换为字节数组:

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

12. 添加*IdentifyFaces ()* 方法, 该方法请求*面部识别服务*识别以前在提交的图像中检测到的任何已知人脸。 请求将返回标识的人员的 id, 但不返回名称:

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

13. 添加*GetPerson ()* 方法。 通过提供人员 id, 此方法会请求*面部识别服务*返回标识的人员的姓名:

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

14.  请记住在返回到 Unity 编辑器之前**保存**更改。
15.  在 Unity 编辑器中, 将 "FaceAnalysis" 脚本从 "项目" 面板中的 "脚本" 文件夹拖到 "*层次结构" 面板*中的主相机对象。 新的脚本组件将添加到主摄像机。 

![将 FaceAnalysis 放到主相机上](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>第7章-创建 ImageCapture 类

*ImageCapture*类的目的是托管与*Azure 面部识别服务*进行通信所需的方法, 以分析要捕获的映像, 确定其面部并确定它是否属于某个已知人员。 如果找到了一个已知人员, 此类会将其名称作为 UI 文本显示在场景中。

若要创建*ImageCapture*类:
 
1.  在之前创建的**脚本**文件夹中右键单击, 然后单击 "**创建**" 和 "  **C#脚本**"。 调用脚本*ImageCapture*。 
2.  双击新的*ImageCapture*脚本以通过 Visual Studio 2017 将其打开。
3.  在 ImageCapture 类上输入以下命名空间:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  在*ImageCapture*类中, 添加以下变量:

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

5.  添加初始化类所需的*唤醒 ()* 和*Start ()* 方法, 并允许 HoloLens 捕获用户的手势:

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

6.  添加在用户执行*攻*指操作时调用的*TapHandler ()* :

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

7.  添加*ExecuteImageCaptureAndAnalysis ()* 方法, 该方法将开始映像捕获过程:

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

8.  添加完成照片捕获过程时调用的处理程序:

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

9. 请记住在返回到 Unity 编辑器之前**保存**更改。

## <a name="chapter-8---building-the-solution"></a>第8章-构建解决方案

若要对应用程序进行全面测试, 需要将其旁加载到 HoloLens。

在执行此操作之前, 请确保:

-   第3章中提到的所有设置都已正确设置。 
-   脚本*FaceAnalysis*已附加到摄像机主对象。 
-   已在*FaceAnalysis*脚本中设置**身份验证密钥**和**组 Id** 。

答: 您已准备好生成解决方案。 构建解决方案后, 就可以开始部署应用程序了。

开始生成过程:

1.  单击 "文件"、"保存" 保存当前场景。
2.  依次单击 "文件"、"生成设置"、"添加打开的场景"。
3.  请确保对 Unity C#项目进行计时。

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab4-24.png)

4.  按 "生成"。 完成此操作后, Unity 将启动 "文件资源管理器" 窗口, 需要在其中创建应用程序, 然后选择要将应用程序生成到其中的文件夹。 现在, 在 Unity 项目中创建该文件夹, 然后调用它应用。 选择应用文件夹后, 按 "选择文件夹"。 
5.  Unity 将开始生成您的项目, 而不是应用程序文件夹。 
6.  Unity 完成生成后 (可能需要一些时间), 将在生成的位置打开文件资源管理器窗口。

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab4-25.png)

7.  打开应用文件夹, 然后打开新的项目解决方案 (如上所示, MR_FaceRecognition)。


## <a name="chapter-9---deploying-your-application"></a>第9章-部署应用程序

在 HoloLens 上部署:

1.  你将需要 HoloLens 的 IP 地址 (用于远程部署), 并确保你的 HoloLens 处于**开发人员模式**。 为此，请执行以下操作:

    1. 在戴上 HoloLens 的同时, 请打开**设置**。
    2. 中转到**网络 & Internet > wi-fi > 高级选项**
    3. 记下**IPv4**地址。
    4. 接下来, 导航回 "**设置**", 然后为**开发人员更新 & Security >** 
    5. 设置开发人员模式。

2.  导航到新的 Unity 生成 (*应用*文件夹), 并在*Visual Studio*中打开解决方案文件。
3.  在解决方案配置中, 选择 "**调试**"。
4.  在解决方案平台中, 选择 " **x86**,**远程计算机**"。 

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab4-26.png)
 
5.  请在 "**生成" 菜单**中, 单击 "**部署解决方案**", 将应用程序旁加载到 HoloLens。
6.  应用现在应显示在你的 HoloLens 上已安装的应用列表中, 可以启动了!

> [!NOTE]
> 若要部署到沉浸式耳机, 请将 "**解决方案平台**" 设置为 "*本地计算机*", 并将**配置**设置为 "*调试*", 将 " *x86* " 设置为**平台**。 然后, 使用 "**生成" 菜单**选择 "*部署解决方案*", 将部署到本地计算机。 


## <a name="chapter-10---using-the-application"></a>第10章-使用应用程序

1.  戴上 HoloLens, 启动应用。
2.  查看在*人脸 API*注册的人。 请确保：

    -  人脸不太遥远并且明显可见
    -  环境照明不太暗

3.  使用点击手势来捕获人员的照片。
4.  等待应用发送分析请求并接收响应。
5.  如果用户已成功识别, 则该人员的名称将显示为 UI 文本。
6.  可以每隔几秒钟使用点击手势重复捕获过程。

## <a name="your-finished-azure-face-api-application"></a>已完成的 Azure 人脸 API 应用程序

恭喜, 你构建了一个混合现实应用, 它利用 Azure 面部识别服务检测图像中的人脸, 并识别所有已知的人脸。

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

**Azure 人脸 API**的强大功能足以在单个映像中检测到64面。 扩展应用程序, 使其能够识别多个其他人的两个或三个面。

### <a name="exercise-2"></a>练习2

**Azure 人脸 API**还可以提供返回各种类型的属性信息。 将此集成到应用程序中。 与[情感 API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)结合时, 这可能更加有趣。
