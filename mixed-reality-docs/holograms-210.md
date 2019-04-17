---
title: MR 输入 210-的视线移动
description: 遵循此编码使用 Unity、 Visual Studio 和 HoloLens 若要了解的视线移动概念的详细信息的演练。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity，学院，教程，提供注视
ms.openlocfilehash: 63c55e8a7a348f2a3e0cc29a9795d7fabcef5df0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591562"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

# <a name="mr-input-210-gaze"></a>MR 输入 210:凝视

[注视](gaze.md)是第一种形式的输入和显示用户的意图和感知。 MR 输入 210 （也称为项目资源管理器） 是为 Windows Mixed Reality 为提供注视相关概念的深入探讨。 我们将添加的上下文感知到我们的光标和全息，充分利用您的应用程序有关的视线移动用户的信息可以了解的内容。

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

我们具有友好顶级此处可帮助你了解的视线移动概念。 在中[MR 基础知识 101](holograms-101.md)，我们有一个简单的游标，只需遵循你的视线移动。 今天我们要搬走局限于简单的游标：

* 我们正在进行的游标和我们全息的视线移动感知： 同时将更改基于位置查找用户-或用户所在*不*查找。 这使它们上下文感知。
* 我们将添加到我们的光标和全息为用户提供更多上下文上的目标的反馈。 这种反馈可以是音频和可视化。
* 我们将展示你的目标的技术来帮助用户按较小的目标。
* 我们将向您展示如何为你使用方向指示器全息突出用户的。
* 我们将指导您使用的用户需要在全息，因为她在您的世界中移动的技术。

>[!IMPORTANT]
>使用 Unity 和混合现实工具包的较旧版本记录中的以下章节每个嵌入的视频。 准确且最新的分步说明时，可能会看到脚本和已过期的相应视频中的视觉对象。 保持为长期的视频和因为涵盖了概念仍然适用。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>MR 输入 210:凝视</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>系统必备

* 使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。
* 一些基本C#编程功能。
* 您应当已完成[MR 基础知识 101](holograms-101.md)。
* HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)所需的项目。 需要 Unity 2017.2 或更高版本。
* 取消存档到您的桌面或其他轻松地访问位置的文件。

>[!NOTE]
>如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)。

### <a name="errata-and-notes"></a>勘误表和说明

* "仅我的代码"必须是在 Visual Studio 中，在工具 （未选中） 已禁用-> 选项-> 以命中断点在代码中的调试。

## <a name="chapter-1---unity-setup"></a>第 1 章-Unity 安装程序

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>目标

* 优化 HoloLens 开发 Unity。
* 导入资产和设置场景。
* HoloLens 中查看顶级。

### <a name="instructions"></a>说明

1. 启动 Unity。
2. 选择**新的项目**。
3. 将项目命名**ModelExplorer**。
4. 输入与位置**注视**文件夹你之前未存档。
5. 请确保项目设置为**3D**。
6. 单击**创建项目**。

### <a name="unity-settings-for-hololens"></a>HoloLens 的 unity 设置

我们需要让 Unity 知道我们尝试导出该应用应创建[沉浸式视图](app-views.md)而不是二维视图。 我们通过将 HoloLens 添加为虚拟现实设备执行该操作。

1. 转到**编辑 > 项目设置 > 播放机**。
2. 在中**检查器面板**对于播放机设置，选择**Windows 应用商店**图标。
3. 展开**XR 设置**组。
4. 在中**呈现**部分中，选择**受支持的虚拟现实**复选框以添加新**虚拟现实 Sdk**列表。
5. 确认**Windows Mixed Reality**出现在列表中。 如果没有，请选择**+** 按钮在列表的底部，然后选择**Windows Holographic**。

接下来，我们需要将我们的脚本编写后端设置为.NET。

1. 转到**编辑 > 项目设置 > 播放机**（你可能仍需要这从上一步）。
2. 在中**检查器面板**对于播放机设置，选择**Windows 应用商店**图标。
3. 在中**其他设置**配置部分中，请确保**脚本编写后端**设置为 **.NET**

最后，我们将更新我们的质量设置，以实现在 HoloLens 上的快速性能。

1. 转到**编辑 > 项目设置 > 质量**。
2. 中的向下箭头上单击**默认**Windows 应用商店图标下面的行。
3. 选择**最快**有关**Windows 应用商店应用程序**。

### <a name="import-project-assets"></a>导入项目资产

1. 右键单击**资产**中的文件夹**项目**面板。
2. 单击**导入包 > 自定义包**。
3. 导航到下载的项目文件并单击**ModelExplorer.unitypackage**。
4. 单击“打开” 。
5. 包加载后，单击**导入**按钮。

### <a name="setup-the-scene"></a>设置场景

1. 在层次结构中删除**Main Camera**。
2. 在中**HoloToolkit**文件夹中，打开**输入**文件夹，然后打开**预设**文件夹。
3. 拖放到**MixedRealityCameraParent**从预设**预设**文件夹导入到**层次结构**。
4. 右键单击**定向光**在层次结构中，选择**删除**。
5. 在中**全息**文件夹中，拖放到的根以下资产**层次结构**:
    * **AstroMan**
    * **灯**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. 启动**播放模式下**▶ 查看顶级。
7. 单击**播放模式下**▶ 再次向**停止**。
8. 在中**全息**文件夹中，找到**Fitbox**资产并将其拖到的根**层次结构**。
9. 选择**Fitbox**中**层次结构**面板。
10. 拖动**AstroMan**从集合**层次结构**到**Hologram 集合**属性中 Fitbox**检查器**面板。

### <a name="save-the-project"></a>保存项目

1. 保存新的场景：**文件 > 另存为场景**。
2. 单击**新文件夹**，然后将文件夹**场景**。
3. 将文件"**ModelExplorer**"并将其保存在**场景**文件夹。

### <a name="build-the-project"></a>生成项目

1. 在 Unity 中，选择**文件 > 生成设置**。
2. 单击**添加打开场景**添加场景。
3. 选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**。
4. 如果您专门为 HoloLens 开发，设置**目标设备**到**HoloLens**。 否则，将其保持打开**任何设备**。
5. 请确保**生成类型**设置为**D3D**并**SDK**设置为**最新安装**（应为 16299 或更高版本的 SDK）。
6. 单击“生成” 。
7. 创建**新文件夹**名为"应用"。
8. 单击一下**应用**文件夹。
9. 按**选择文件夹**。

Unity 完成操作后，将出现一个文件资源管理器窗口。

1. 打开**应用**文件夹。
2. 打开**ModelExplorer Visual Studio 解决方案**。

如果部署到 HoloLens:

1. 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x86**。
2. 单击向下箭头旁边的本地计算机按钮，然后选择**远程计算机**。
3. 输入**HoloLens 设备 IP 地址**并将身份验证模式设置为**通用 （未加密的协议）**。 单击**选择**。 如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**。
4. 在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。 如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。
5. 当部署应用时，消除**Fitbox**与**选择手势**。

如果部署到沉浸式头戴式：

1. 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x64**。
2. 请确保部署目标设置为**本地计算机**。
3. 在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。
4. 当部署应用时，消除**Fitbox**拉开运动控制器上的触发器。

## <a name="chapter-2---cursor-and-target-feedback"></a>第 2 章-光标和目标的反馈

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>目标

* 光标视觉设计和行为。
* 视线移动基于游标的反馈。
* 基于的视线移动的 hologram 反馈。

我们要即基础的一些游标设计原则，我们的工作：

* 光标始终存在。
* 不要让获取太小或最大的光标。
* 避免不阻止的内容。

### <a name="instructions"></a>说明

1. 在中**HoloToolkit\Input\Prefabs**文件夹中，找到**InputManager**资产。
2. 拖放到**InputManager**拖动到**层次结构**。
3. 在中**HoloToolkit\Input\Prefabs**文件夹中，找到**光标**资产。
4. 拖放到**游标**拖动到**层次结构**。
5. 选择**InputManager**对象中**层次结构**。
6. 拖动**游标**对象从**层次结构**到 InputManager **SimpleSinglePointerSelector**的**游标**字段中，在底部**Inspector**。

![简单单指针选择器设置](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>生成和部署

1. 重新生成该应用程序从**文件 > 生成设置**。
2. 打开**应用程序文件夹**。
3. 打开**ModelExplorer Visual Studio 解决方案**。
4. 单击**调试-> 启动不调试**或按**Ctrl + F5**。
5. 观察如何绘制光标，及其如何更改外观，如果它触摸一张全息图。

### <a name="instructions"></a>说明

1. 在中**层次结构**面板中，展开**AstroMan**->**GEO_G**->**Back_Center**对象。
2. 双击**Interactible.cs**若要在 Visual Studio 中打开它。
3. 取消注释中的行**IFocusable.OnFocusEnter()** 并**IFocusable.OnFocusExit()** 中的回调**Interactible.cs**。 当焦点 （不管是通过提供注视或控制器指向） 进入和退出特定 GameObject 碰撞体由混合现实工具包 InputManager 调用。

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>我们使用`EnableKeyword`和`DisableKeyword`上面。 为了使这些与标准的工具包的着色器应用中使用，将需要遵循[Unity 指导原则，用于访问通过脚本材料](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。 在这种情况下，我们已经提供了[突出显示的材料的三个变体](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)所需的资源文件夹 （查找名称中的突出显示的三个材料） 中。

### <a name="build-and-deploy"></a>生成和部署

1. 与前面一样，生成项目，并将部署到 HoloLens。
2. 观察提供注视旨在对象时会发生什么情况，它不是。

## <a name="chapter-3---targeting-techniques"></a>第 3 章-面向技术

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>目标

* 使其更易于目标全息。
* 稳定自然头移动。

### <a name="instructions"></a>说明

1. 在中**层次结构**面板中，选择**InputManager**对象。
2. 在中**Inspector**面板中，找到**注视稳定器**脚本。 如果你想要查看，请单击它以在 Visual Studio 中打开。
    * 此脚本循环访问示例 Raycast 数据，并有助于稳定精度面向用户的视线移动。
3. 在中**Inspector**，可以编辑**存储稳定性示例**值。 此值表示稳定器循环访问到计算经过稳定的值的样本的数。

## <a name="chapter-4---directional-indicator"></a>第 4 章-方向指示器

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>目标

* 添加对游标来帮助查找全息方向指示器。

### <a name="instructions"></a>说明

我们将使用**DirectionIndicator.cs**文件将该文件：

1. 如果用户不在全息观望显示方向指示器。
2. 在全息观望用户的情况下隐藏方向指示器。
3. 更新为指向全息方向指示器。

让我们开始吧。

1. 单击**AstroMan**对象中**层次结构**面板并**单击箭头**以将其展开。
2. 在中**层次结构**面板中，选择**DirectionalIndicator**对象下**AstroMan**。
3. 在中**Inspector**面板中，单击**添加组件**按钮。
4. 在菜单中，在搜索框中键入**方向指示器**。 选择搜索结果。
5. 在**层次结构**面板中，拖放**光标**对象拖到**游标**中的属性**检查器**。
6. 在中**项目**面板**全息**文件夹的拖放**DirectionalIndicator**拖到资产**方向指示器**中的属性**Inspector**。
7. 生成和部署应用程序。
8. 观看方向指示器对象如何帮助你查找顶级。

## <a name="chapter-5---billboarding"></a>第 5 章-公告板

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>目标

* 使用公告板可使全息始终面临面向使用者。

我们将使用**Billboard.cs**要保留一个 GameObject，面向，以便在任何时候，它对着用户文件。

1. 在中**层次结构**面板中，选择**AstroMan**对象。
2. 在中**Inspector**面板中，单击**添加组件**按钮。
3. 在菜单中，在搜索框中键入**布告栏**。 选择搜索结果。
4. 在中**Inspector**设置**枢轴**到**Y**。
5. 试试看吧！ 生成和部署之前为应用。
6. 请参阅如何宣传位置对象的人脸，无论您如何更改视区。
7. 删除从脚本**AstroMan**现在。

## <a name="chapter-6---tag-along"></a>第 6 章-尾随

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>目标

* 使用尾随我们全息关注我们周围的空间。

当我们在此问题，我们本教程介绍以下设计约束：

* 内容应始终为快速消失。
* 内容不应为的方式。
* Head 锁定内容不舒服。

此处使用的解决方案是使用"尾随"方法。

尾随对象永远不会完全离开用户的视图。 您可以将橡胶带尾随对象为其附加到用户的头。 当用户移动时，内容将保留在轻松浏览通过滑动指向视图的边缘，无需完全离开。 时用户 gazes 针对尾随对象，它更充分发挥视图。

我们将使用**SimpleTagalong.cs**文件将该文件：

1. 确定是否尾随对象是相机的边界内。
2. 如果没有在视图截锥，定位到尾随视图截锥内的部分。
3. 否则，将默认距离的尾随定位从用户中。

若要执行此操作，我们首先必须更改**Interactible.cs**脚本，以调用**TagalongAction**。

1. 编辑**Interactible.cs**通过完成编码练习 6.a （取消注释行到第 87 84）。

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

**InteractibleAction.cs**脚本，与配对**Interactible.cs**全息上点击时执行自定义操作。 在这种情况下，我们将使用一个专用于尾随。

* 在中**脚本**上的文件夹中单击**TagalongAction.cs**资产，以便在 Visual Studio 中打开。
* 完成编码练习，或将它更改为：
  * 在顶部**层次结构**，在搜索栏中键入**ChestButton_Center**和选择的结果。
  * 在中**Inspector**面板中，单击**添加组件**按钮。
  * 在菜单中，在搜索框中键入**免除操作**。 选择搜索结果。
  * 在中**全息**文件夹查找**免除**资产。
  * 选择**ChestButton_Center**对象中**层次结构**。 拖放到**免除**对象从**项目**面板拖到**检查器**到**对象到免除**属性。
  * 拖动**免除操作**对象从**Inspector**到**Interactible 操作**字段**Interactible**脚本。
* 双击**TagalongAction**脚本以在 Visual Studio 中打开它。

![Interactible 设置](images/holograms210-interactible.png)

我们需要添加下列代码：

* 将功能添加到 （继承自 InteractibleAction） TagalongAction 脚本中的 PerformAction 函数。
* 添加公告板 gazed 时对象，并将枢轴设置为 XY。
* 然后将简单尾随添加到该对象。

下面是我们的解决方案，从**TagalongAction.cs**:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* 试试看吧！ 生成和部署应用程序。
* 观看的内容如何遵循的视线移动点的中心，但不是持续并且不会阻止它。
