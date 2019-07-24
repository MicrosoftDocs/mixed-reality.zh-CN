---
title: MR 和 Azure 310-对象检测
description: 完成本课程, 了解如何训练机器学习模型, 然后使用训练的模型从混合现实应用程序内识别类似对象及其在现实中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 自定义视觉, 对象检测, 混合现实, 学院, unity, 教程, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544419"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

# <a name="mr-and-azure-310-object-detection"></a>Mr 和 Azure 310:对象检测

在本课程中, 你将了解如何在混合现实应用程序中使用 Azure 自定义视觉 "对象检测" 功能来识别所提供的映像中的自定义视觉对象内容及其空间位置。

此服务允许你使用对象图像训练机器学习模型。 然后, 你将使用训练的模型来识别类似对象并大致了解其在现实世界中的位置, 如 Microsoft HoloLens 的相机捕获或相机连接到用于沉浸式 (VR) 耳机的 PC。

![课程结果](images/AzureLabs-Lab310-00.png)

**Azure 自定义视觉中, 对象检测**是一种 Microsoft 服务, 它允许开发人员构建自定义映像分类器。 然后, 可以将这些分类器用于新的图像, 通过在图像本身中提供**框边界**来检测该新图像内的对象。 此服务提供简单易用的联机门户来简化此过程。 有关详细信息, 请访问以下链接:

* [Azure 自定义视觉页面](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [限制和配额](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

完成本课程后, 你将拥有一个混合现实应用程序, 该应用程序将能够执行以下操作:

1. 用户将可以*注视*使用 Azure 自定义影像服务、对象检测训练的对象。 
2. 用户将使用*点击*手势来捕获所查看内容的图像。
3. 应用会将映像发送到 Azure 自定义影像服务。
4. 此时会显示服务的答复, 该服务会将识别结果显示为世界空间文本。 这将通过利用 Microsoft HoloLens 的空间跟踪来实现, 这是为了了解识别对象的世界位置, 然后使用与图像中检测到的内容关联的*标记*来提供标签文本。

本课程还介绍了如何手动上传图像、创建标记和培训服务, 通过在提交的图像中设置*边界框*来识别不同的对象 (在提供的示例中为杯)。 

> [!IMPORTANT]
> 创建和使用应用后, 开发人员应导航回 Azure 自定义影像服务, 并确定该服务所做的预测, 并确定其是否正确 (通过标记服务丢失的任何内容) 和调整*边界框*)。 然后, 可以对服务进行重新训练, 这会增加识别真实世界对象的可能性。

本课程将介绍如何从 Azure 自定义影像服务、对象检测到基于 Unity 的示例应用程序中获取结果。 您可以将这些概念应用到您可能生成的自定义应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 310:对象检测</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程面向具有 Unity 和C#的基本经验的开发人员。 另外, 请注意, 本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容 (2018 年7月)。 你可以随意使用最新的软件 (如[安装工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)一文中所述), 但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件:

- 开发 PC
- [Windows 10 秋季创意者更新 (或更高版本) 已启用开发人员模式](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [最新的 Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- 已启用开发人员模式的[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)
- Azure 安装和自定义影像服务检索的 Internet 访问
-  对于想要自定义视觉识别的每个对象, 需要一系列至少 15 (15) 个图像。 如果需要, 可以使用本课程提供的映像,[一系列 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

## <a name="before-you-start"></a>开始之前

1.  为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。
2.  设置并测试你的 HoloLens。 如果需要支持设置 HoloLens, 请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  在开始开发新的 HoloLens 应用程序时, 最好执行校准和传感器调整 (有时它可以帮助为每个用户执行这些任务)。 

有关校准的帮助信息, 请单击此链接, 了解[到 HoloLens 校准文章](calibration.md#hololens)。

有关传感器优化的帮助, 请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。

## <a name="chapter-1---the-custom-vision-portal"></a>第1章-自定义视觉门户

若要使用**Azure 自定义影像服务**, 你将需要配置该应用程序的实例。

1.  导航[到**自定义影像服务**主页](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  单击**入门**。

    ![](images/AzureLabs-Lab310-01.png)

3.  登录到自定义视觉门户。

    ![](images/AzureLabs-Lab310-02.png)

4.  如果还没有 Azure 帐户, 则需要创建一个。 如果在课堂或实验室中按照本教程进行学习, 请咨询教师或 proctors, 以获得设置新帐户的帮助。

5.  首次登录后, 系统会提示 "*服务*" 面板。 单击复选框以*同意条款*。 然后单击 "**我同意**"。

    ![](images/AzureLabs-Lab310-03.png)

6.  如果同意这些条款, 你现在已在 "*我的项目*" 部分。 单击 "**新建项目**"。

    ![](images/AzureLabs-Lab310-04.png)

7.  右侧将显示一个选项卡, 该选项卡将提示你为项目指定某些字段。

    1.  插入项目的名称

    2.  为项目插入说明 (**可选**)

    3.  选择一个**资源组**, 或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议将所有与单个项目关联的 Azure 服务 (如这些课程) 保存在一个公共资源组中。

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > 若要[阅读有关 Azure 资源组的详细信息, 请导航到相关文档](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  将**项目类型**设置为 "**对象检测 (预览版)** "。

8.  完成后, 单击 "**创建项目**", 将重定向到 "自定义影像服务项目" 页面。


## <a name="chapter-2---training-your-custom-vision-project"></a>第2章-培训自定义视觉项目

在自定义视觉门户中, 你的主要目标是训练你的项目以识别图像中的特定对象。

对于希望应用程序识别的每个对象, 至少需要 15 (15) 个映像。 您可以使用本课程提供的映像 ([一系列 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。

训练自定义视觉项目:

1.  单击 **+** 按钮旁边**标记**。

    ![](images/AzureLabs-Lab310-06.png)

2.  添加用于将图像与相关联的标记的**名称**。 在此示例中, 我们将使用 cup 的图像进行识别, 因此已为此、**杯**命名了标记。 完成后单击 "**保存**"。

    ![](images/AzureLabs-Lab310-07.png)

3.  你将注意到已添加**标记**(可能需要重新加载页面以使其显示)。 

    ![](images/AzureLabs-Lab310-08.png)

4.  单击页中心的 "**添加图像**"。

    ![](images/AzureLabs-Lab310-09.png)

5.  单击 "**浏览本地文件**", 然后浏览到要为一个对象上传的图像, 最小值为 15 (15)。

    > [!TIP]
    >  你可以一次选择多个图像来上传。

    ![](images/AzureLabs-Lab310-10.png)

6.  选择要对项目定型的所有映像后, 按 "**上载文件**"。 文件将开始上传。 确认上传后, 单击 "**完成**"。

    ![](images/AzureLabs-Lab310-11.png)

7.  此时, 将上载映像, 但不会对其进行标记。

    ![](images/AzureLabs-Lab310-12.png)

8.  若要为图像标记, 请使用鼠标。 当你将鼠标指针悬停在图像上时, 选择突出显示将帮助你在对象周围自动绘制选定内容。 如果它不准确, 可以自行绘制。 为此, 请按住鼠标左键并拖动选择区域以包含您的对象。 

    ![](images/AzureLabs-Lab310-13.png) 

9. 选择图像中的对象之后, 会出现一个小提示符, 要求你*添加区域标记*。 选择之前创建的标记 (在上面的示例中为 "杯"), 或者如果要添加更多的标记, 请在中键入, 然后单击 " **+" (加号)** 按钮。

    ![](images/AzureLabs-Lab310-14.png) 

10. 若要标记下一个图像, 可以单击边栏选项卡右侧的箭头, 或关闭标记边栏选项卡 (单击边栏选项卡右上角的 " **X** "), 然后单击下一个图像。 下一个映像准备就绪后, 请重复相同的过程。 对已上传的所有映像执行此操作, 直到所有映像都已标记。 

    > [!NOTE]
    >  可以在同一个映像中选择多个对象, 如下图所示: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. 标记为 "全部" 后, 单击屏幕左侧的 "**标记**" 按钮, 显示标记的图像。 

    ![](images/AzureLabs-Lab310-16.png)

12. 你现在已准备好培训你的服务。 单击 "**训练**" 按钮, 将开始第一次训练迭代。

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. 构建后, 你将能够看到两个称为 "**创建默认值**和**预测 URL**" 的按钮。 先单击 "**设为默认值**", 然后单击 "**预测 URL**"。

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > 从此中提供的终结点设置为标记为默认值的任何*迭代*。 这种情况下, 如果您以后生成新的*迭代*并将其更新为默认值, 则无需更改代码。

14. 单击 "**预测 URL**" 后, 打开 "*记事本*", 复制并粘贴该**Url** (也称为**预测终结点**) 和**服务预测密钥**, 以便稍后在代码中需要时进行检索。

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第3章-设置 Unity 项目

下面是用于使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。

1.  打开**Unity** , 并单击 "**新建**"。

    ![](images/AzureLabs-Lab310-21.png)

2.  现在需要提供 Unity 项目名称。 插入**CustomVisionObjDetection**。 确保将 "项目类型" 设置为 " **3d**", 并将位置设置为合适的**位置**(请记住, 更接近根目录更好)。 然后单击 "**创建项目**"。

    ![](images/AzureLabs-Lab310-22.png)

3.  当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。 转到 **编辑* > *首选项** ，然后在新窗口中，导航到 **外部工具** 。 将**外部脚本编辑器**更改为**Visual Studio**。 关闭 "**首选项**" 窗口。

    ![](images/AzureLabs-Lab310-23.png)

4.  接下来, 转到 "文件" " **> 生成设置**", 将**平台**切换到 "*通用 Windows 平台*", 然后单击 "**切换平台**" 按钮。

    ![](images/AzureLabs-Lab310-24.png)

5.  在相同的 "**生成设置**" 窗口中, 确保已设置以下各项:

    1.  **目标设备**设置为**HoloLens**        
    2.  **生成类型**设置为**D3D**
    3.  **SDK**设置为 "**最新安装**"
    4.  **Visual Studio 版本**设置为 "**最新安装**"
    5.  "**生成并运行**" 设置为 "**本地计算机**"            
    6.  现在, "**生成设置**" 中的其余设置应保留为默认值。

        ![](images/AzureLabs-Lab310-25.png)

6.  在相同的**生成设置**窗口中, 单击 "**播放机设置**" 按钮, 这会在**检查器**所在的空间中打开相关面板。

7. 在此面板中, 需要验证几项设置:

    1.  在 "**其他设置**" 选项卡中:

        1.  **脚本运行时版本**应为**试验**性的 (.net 4.6 等效项), 这会触发重新启动编辑器的需要。

        2. **脚本编写后端**应为 **.net**。

        3. **API 兼容级别**应为 **.net 4.6**。

            ![](images/AzureLabs-Lab310-26.png)

    2.  在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:

        1. **InternetClient**

        2.  **摄像头**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 在 "**支持的虚拟现实**" 下, 确保已添加**Windows Mixed reality SDK** 。

        ![](images/AzureLabs-Lab310-29.png)

8.  返回**生成设置**, *\# Unity C 项目*不再灰显: 勾选此旁边的复选框。

9.  关闭 "**生成设置**" 窗口。

10. 在**编辑器**中, 单击 "**编辑** > **项目设置** > " "**图形**"。

    ![](images/AzureLabs-Lab310-30.png)

11. 在中 **检查器面板** *图形设置* 则会打开。 向下滚动, 直到看到一个名为 "**始终包括着色**器" 的数组。 通过增加**大小**变量来添加槽 (在本例中为 8, 因此我们将其设为 9)。 新的槽将出现在数组的最后位置, 如下所示:

    ![](images/AzureLabs-Lab310-31.png)

12. 在插槽中, 单击槽旁边的小型目标圆圈, 以打开着色器列表。 查找**旧版着色器/透明/漫射**着色器并双击它。 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>第4章-导入 CustomVisionObjDetection Unity 包

在本课程中, 我们提供了名为 " **unitypackage**" 的 Unity 资产包。 

> 提示Unity 支持的任何对象 (包括整个场景) 都可以打包到**unitypackage**文件中, 并在其他项目中导出/导入。 这是在不同的**Unity 项目**之间移动资产的最安全、最有效的方法。

你可以在[此处找到需要下载的 AZURE 尊敬的310包](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。

1.  在您前面的 "Unity" 面板中, 单击屏幕顶部菜单中的 "**资产**", 然后单击 "**导入包 > 自定义包**"。

    ![](images/AzureLabs-Lab310-33.png)

2.  使用文件选取器选择**Azure unitypackage**包, 并单击 "**打开**"。 此时将显示此资产的组件列表。 单击 "**导**入" 按钮确认导入。

    ![](images/AzureLabs-Lab310-34.png)

3.  导入完成后, 你会注意到, 包中的文件夹现在已添加到 "**资产**" 文件夹中。 这种文件夹结构是 Unity 项目的典型类型。

    ![](images/AzureLabs-Lab310-35.png)

    1.  "**材料**" 文件夹包含**注视光标**使用的材料。 

    2.  **插件**文件夹包含代码用于对服务 web 响应进行反序列化的 newtonsoft.json DLL。 文件夹和子文件夹中包含的两个 (2) 不同版本都是允许在 Unity 编辑器和 UWP 生成中使用和生成库所必需的。 

    3.  **Prototyping**文件夹包含场景中包含的 prototyping。 它们是:

        1.  在应用程序中使用的**GazeCursor**。 将与 SpatialMapping prefab 一起使用, 以将其放在物理对象顶层的场景中。
        2.  **标签**, 它是用于在需要时在场景中显示对象标记的 UI 对象。
        3.  **SpatialMapping**, 它是一个对象, 它使应用程序可以使用 Microsoft HoloLens 的空间跟踪来创建虚拟映射。

    4.  当前包含此课程的预建场景的**场景**文件夹。

4.  打开 "**场景**" 文件夹, 在 "**项目" 面板**中双击 " **ObjDetectionScene**", 加载将用于本课程的场景。

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **不包含任何代码**, 你将按照此课程编写代码。

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>第5章-创建 CustomVisionAnalyser 类。

此时, 您可以编写一些代码。 你将从**CustomVisionAnalyser**类开始。

> [!NOTE]
> 使用**自定义视觉 REST API**, 对在下面所示的代码中所做的**自定义影像服务**调用。 通过使用此功能, 您将了解如何实现和使用此 API (对于理解如何实现类似于您自己的操作非常有用)。 请注意, Microsoft 提供了一个**自定义视觉 SDK** , 该 SDK 还可用于对服务进行调用。 有关详细信息, 请访问[自定义视觉 SDK 文章](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。

此类负责:

- 加载作为字节数组捕获的最新映像。

- 将字节数组发送给 Azure**自定义影像服务**实例以进行分析。

- 接收 JSON 字符串形式的响应。

- 反序列化响应并将结果**预测**传递给**SceneOrganiser**类, 这将负责显示响应的方式。

若要创建此类:

1.  右键单击 "资产"**文件夹**, 位于 "**项目" 面板**中, 然后单击 **"创建** > **文件夹**"。 调用文件夹**脚本**。

    ![](images/AzureLabs-Lab310-37.png)

2.  双击新创建的文件夹以将其打开。

3.  右键单击文件夹内, 然后单击 "**创建** > **C\#脚本**"。 将脚本命名为**CustomVisionAnalyser。**

4.  双击新的**CustomVisionAnalyser**脚本以通过**Visual Studio**打开它。

5.  请确保在该文件的顶部引用了以下命名空间:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  在**CustomVisionAnalyser**类中, 添加以下变量:

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
    > 请确保将**服务预测密钥**插入到**predictionKey**变量中, 并将**预测终结点**插入到**predictionEndpoint**变量中。 你之前将它们复制到[记事本, 步骤14中的第2章](#chapter-2---training-your-custom-vision-project)。

7.  现在需要添加用于**唤醒 ()** 的代码以初始化实例变量:

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

8.  添加协同程序 (在其下面带有 static **GetImageAsByteArray ()** 方法), 该方法将获得**ImageCapture**类捕获的映像分析结果。

    > [!NOTE]
    > 在**AnalyseImageCapture**协同程序中, 有一个对你还需要创建的**SceneOrganiser**类的调用。 因此, 请**暂时将这些行注释为**。

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

9. 删除**Start ()** 和**Update ()** 方法, 因为它们不会被使用。 

10.  在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。

> [!IMPORTANT]
> 如前文所述, 不要担心可能出现错误的代码, 因为您很快就会提供更多的类, 这将修复这些问题。

## <a name="chapter-6---create-the-customvisionobjects-class"></a>第6章-创建 CustomVisionObjects 类

你现在将创建的类是**CustomVisionObjects**类。

此脚本包含其他类用于序列化和反序列化对自定义影像服务进行的调用的许多对象。

若要创建此类:

1.  右键单击 "**脚本**" 文件夹内, 然后单击 "**创建** > **C\#脚本**"。 调用脚本**CustomVisionObjects。**

2.  双击新的**CustomVisionObjects**脚本以通过**Visual Studio**打开它。

3.  请确保在该文件的顶部引用了以下命名空间:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  删除**CustomVisionObjects**类中的**Start ()** 和**Update ()** 方法, 此类现在应为空。

    > [!WARNING]
    > 务必认真遵循下一条指令。 如果将新的类声明放在**CustomVisionObjects**类中, 将会在第[10 章](#chapter-10---create-the-imagecapture-class)中出现编译错误, 指出找不到**AnalysisRootObject**和**BoundingBox** 。

5.  将以下类添加到**CustomVisionObjects**类的*外部*。 **Newtonsoft.json**库使用这些对象序列化和反序列化响应数据:

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

6.  在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。

## <a name="chapter-7---create-the-spatialmapping-class"></a>第7章-创建 SpatialMapping 类

此类将设置场景中的**空间映射碰撞**器, 以便能够检测虚拟对象与实际对象之间的冲突。

若要创建此类:

1.  右键单击 "**脚本**" 文件夹内, 然后单击 "**创建** > **C\#脚本**"。 调用脚本**SpatialMapping。**

2.  双击新的**SpatialMapping**脚本以通过**Visual Studio**打开它。

3.  请确保在**SpatialMapping**类的上面引用了以下命名空间:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  然后, 将以下变量添加到**SpatialMapping**类中的**Start ()** 方法之上:

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

5.  添加**唤醒 ()** 和**Start ()** :

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

6.  删除**Update ()** 方法。

7.  在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。


## <a name="chapter-8---create-the-gazecursor-class"></a>第8章-创建 GazeCursor 类

此类通过使用在前一章节中创建的**SpatialMappingCollider**, 负责在实际空间中的正确位置设置光标。

若要创建此类:

1.  右键单击 "**脚本**" 文件夹内, 然后单击 "**创建** > **C\#脚本**"。 调用脚本**GazeCursor**

2.  双击新的**GazeCursor**脚本以通过**Visual Studio**打开它。

3.  请确保在**GazeCursor**类之上引用了以下命名空间:

    ```csharp
    using UnityEngine;
    ```

4.  然后, 将以下变量添加到**GazeCursor**类中的**Start ()** 方法之上。 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  将**Start ()** 方法更新为以下代码:

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

6.  将**update ()** 方法更新为以下代码:

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
    > 不要担心找不到**SceneOrganiser**类的错误, 您将在下一章中创建它。

7. 在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。

## <a name="chapter-9---create-the-sceneorganiser-class"></a>第9章-创建 SceneOrganiser 类

此类将:

-   通过向*主摄像机*附加相应的组件来设置它。

-   当检测到某个对象时, 它将负责计算其在现实世界中的位置, 并在其旁边放置一个**标记标签**和合适的**标记名称**。    

若要创建此类:

1.  右键单击 "**脚本**" 文件夹内, 然后单击 "**创建** > **C\#脚本**"。 将脚本命名为**SceneOrganiser**。

2.  双击新的**SceneOrganiser**脚本以通过**Visual Studio**打开它。

3.  请确保在**SceneOrganiser**类的上面引用了以下命名空间:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  然后, 将以下变量添加到**SceneOrganiser**类中的**Start ()** 方法之上:

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

5.  删除**Start ()** 和**Update ()** 方法。

6.  在变量的下面添加**唤醒 ()** 方法, 该方法将初始化类并设置场景。

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

7.  添加**PlaceAnalysisLabel ()** 方法, 该方法将*实例化*场景中的标签 (此时, 它对用户不可见)。 它还会放置图像的四个部分 (也不可见), 并与真实环境重叠。 这一点很重要, 因为在分析后从服务中检索的 box 坐标将追溯到此四个部分, 以确定对象在现实世界中的大致位置。 

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

8.  添加**FinaliseLabel ()** 方法。 它负责:

    *   将*标签*文本设置为具有最高置信度的预测*标记*。
    *   在前面定位的四个对象上调用*边界框*的计算, 并在场景中放置该标签。
    *   使用 Raycast 向*边界框*调整标签深度, 这应与现实世界中的对象发生冲突。
    * 正在重置捕获进程, 以允许用户捕获其他映像。

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

9.  添加**CalculateBoundingBoxPosition ()** 方法, 该方法托管从服务中检索的*边界框*坐标所需的多种计算, 并在四个部分按比例重新创建它们。

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

10. 在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。

    > [!IMPORTANT]
    > 继续之前, 请打开**CustomVisionAnalyser**类, 并在**AnalyseLastImageCaptured ()** 方法中*取消注释*以下行:
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
> 不要担心 "找不到**ImageCapture**类" 消息, 你将在下一章中创建它。


## <a name="chapter-10---create-the-imagecapture-class"></a>第10章-创建 ImageCapture 类

要创建的下一个类是**ImageCapture**类。

此类负责:

*   使用 HoloLens 相机捕获映像, 并将其存储在*App*文件夹中。
*   处理用户的*敲击*手势。

若要创建此类:

1.  中转到前面创建的 "**脚本**" 文件夹。

2.  右键单击文件夹内, 然后单击 "**创建** > **C\#脚本**"。 将脚本命名为**ImageCapture**。

3.  双击新的**ImageCapture**脚本以通过**Visual Studio**打开它。

4.  将文件顶部的命名空间替换为以下内容:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然后, 将以下变量添加到**ImageCapture**类中的**Start ()** 方法之上:

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

6.  现在需要添加**唤醒 ()** 和**Start ()** 方法的代码:

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

7.  实现一个处理程序, 该处理程序将在出现分流手势时调用:

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
    > 如果光标为**绿色**, 则表示相机可用于拍摄映像。 如果光标为**红色**, 则表示相机处于繁忙状态。

8.  添加应用程序用于启动映像捕获过程并存储映像的方法:

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

9.  添加在捕获照片时要调用的处理程序, 并将其添加到已准备好进行分析的时间。 然后, 将结果传递给**CustomVisionAnalyser**进行分析。

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

10. 在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>第11章-在场景中设置脚本

现在, 你已经编写了此项目所需的所有代码, 是在场景中设置脚本的时候, 还是在 prototyping 上设置脚本以使它们正常运行。

1.  在**Unity 编辑器**中的 "**层次结构" 面板**中, 选择 "**主摄像机**"。
2.  在 "**检查器" 面板**中, 选择 "**摄像机**", 单击 "**添加组件**", 然后搜索 " **SceneOrganiser**脚本", 然后双击 "添加"。

    ![](images/AzureLabs-Lab310-38.png)

3.  在 "**项目" 面板**中, 打开**prototyping 文件夹**, 将 **"标签**prefab" 拖到 "标签空引用目标输入区域" 的 "*标签*为空引用目标输入区域" 中, 在刚添加到*摄像机*的**SceneOrganiser**脚本中, 如中所示下图:

    ![](images/AzureLabs-Lab310-39.png)

4.  在 "**层次结构" 面板**中, 选择**主摄像机**的**GazeCursor**子。
5.  在 "**检查器" 面板**中, 选择**GazeCursor** , 单击 "**添加组件**", 然后搜索 " **GazeCursor**脚本" 并双击, 以添加它。

    ![](images/AzureLabs-Lab310-40.png)

6.  同样, 在 "**层次结构" 面板**中, 选择**主摄像机**的**SpatialMapping**子项。
7.  在 "**检查器" 面板**中, 选择**SpatialMapping** , 单击 "**添加组件**", 然后搜索 " **SpatialMapping**脚本" 并双击, 以添加它。

    ![](images/AzureLabs-Lab310-41.png)

在运行时, **SceneOrganiser**脚本中的代码将添加未设置的其余脚本。

## <a name="chapter-12---before-building"></a>第12章-生成之前

若要对应用程序进行全面测试, 需要将其旁加载到 Microsoft HoloLens。

在执行此操作之前, 请确保:

-  [第3章](#chapter-3---set-up-the-unity-project)中提到的所有设置都已正确设置。
- 脚本**SceneOrganiser**已附加到**摄像机主**对象。
- 脚本**GazeCursor**附加到**GazeCursor**对象。
- 脚本**SpatialMapping**附加到**SpatialMapping**对象。
- 第[5 章](#chapter-5---create-the-customvisionanalyser-class)步骤 6:

    - 请确保将**服务预测密钥**插入到**predictionKey**变量。
    - 已将**预测终结点**插入到**predictionEndpoint**类中。

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>第13章-构建 UWP 解决方案并旁加载您的应用程序

现在, 你可以将应用程序构建为一个 UWP 解决方案, 你将能够将其部署到 Microsoft HoloLens。 开始生成过程:

1.  请参阅**文件 > 生成设置**。

2.  勾选**Unity C\#项目**。

3.  单击 "**添加打开的场景**"。 这会将当前打开的场景添加到生成中。

    ![](images/AzureLabs-Lab310-42.png)

4.  单击“生成” 。 Unity 将启动*文件资源管理器*窗口, 在该窗口中, 需要创建一个文件夹, 然后选择要在其中生成应用的文件夹。 立即创建该文件夹并将其命名为**应用**。 选择**应用**文件夹后, 单击 "**选择文件夹**"。

5.  Unity 将开始向**应用**文件夹生成项目。

6.  Unity 完成生成 (可能需要一些时间) 后, 它会在生成的位置打开 "**文件资源管理器**" 窗口 (检查任务栏, 因为它可能不会始终出现在窗口之上, 但会通知你添加了一个新窗口)。

7.  若要部署到 Microsoft HoloLens, 你将需要该设备的 IP 地址 (用于远程部署), 并确保它还设置了**开发人员模式**。 要实现此目的，请执行以下操作：

    1.  在戴上 HoloLens 的同时, 请打开**设置**。

    2.  中转到**网络 & Internet** > **wi-fi** > **高级选项**

    3.  记下**IPv4**地址。

    4.  接下来, 导航回 "**设置**", 然后为**开发人员** **更新 & 安全性** > 

    5.  设置 **开发人员模式** *上* 。

8.  导航到新的 Unity 生成 (**应用**文件夹), 并在**Visual Studio**中打开解决方案文件。

9.  在解决方案配置中, 选择 "**调试**"。

10. 在解决方案平台中, 选择 " **x86, 远程计算机**"。 系统将提示你插入远程设备的**IP 地址**(在本例中, 你记下了此项)。

    ![](images/AzureLabs-Lab310-43.png)

11. 请在 "**生成**" 菜单中, 单击 "**部署解决方案**", 将应用程序旁加载到 HoloLens。

12. 你的应用现在应显示在 Microsoft HoloLens 上已安装的应用列表中, 可以启动了!

### <a name="to-use-the-application"></a>使用应用程序:

* 查看已使用**Azure 自定义影像服务和对象检测**训练的对象, 并使用**点击手势**。
* 如果成功检测到该对象, 则会出现带有标记名称的世界空间*标签文本*。

> [!IMPORTANT]
> 每次捕获照片并将其发送到服务时, 您可以返回到 "服务" 页, 并使用新捕获的映像重新训练服务。 从一开始, 你可能还需要更正*边界框*, 使其更准确并重新训练服务。

> [!NOTE]
> 当 Microsoft HoloLens 传感器和/或 Unity 中的 SpatialTrackingComponent 无法放置合适的 colliders (相对于真实世界对象) 时, 放置的标签文本可能不会出现在对象附近。 如果出现这种情况, 请尝试在不同的表面上使用该应用程序。

## <a name="your-custom-vision-object-detection-application"></a>自定义视觉, 对象检测应用程序

恭喜, 你构建了一个利用 Azure 自定义视觉、对象检测 API 的混合现实应用, 该 API 可识别图像中的对象, 然后在3D 空间中为该对象提供大致位置。

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

若要添加到文本标签, 请使用半透明的多维数据集包装 3D*边界框*中的实际对象。

### <a name="exercise-2"></a>练习2

训练自定义影像服务来识别更多对象。

### <a name="exercise-3"></a>练习3

在识别对象时播放声音。

### <a name="exercise-4"></a>练习4

使用 API 来重新训练你的服务, 使其与你的应用程序正在分析的映像相同, 以便使该服务更准确 (同时执行预测和定型)。
