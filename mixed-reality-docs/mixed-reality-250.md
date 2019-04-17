---
title: 共享 250 的 HoloLens 和沉浸式耳机 MR
description: 遵循此编码使用 Unity、 Visual Studio、 HoloLens、 和 Windows Mixed Reality 耳机若要了解详细信息的共享全息混合的现实设备之间的演练。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit unity，令人着迷，动作控制器、 共享、 xbox 控制器、 网络、 跨设备
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590203"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>共享 250 MR:HoloLens 和沉浸式耳机

灵活的通用 Windows 平台 (UWP) 中，很容易创建跨越多个设备的应用程序。 使用这种灵活性，我们可以创建利用优势的每个设备的体验。 本教程将介绍基本的共享的体验 HoloLens 和 Windows Mixed Reality 沉浸式耳机上运行。 最初，此内容已传递华盛顿州西雅图市的 Microsoft Build 2017 大会上。

**在本教程中，我们将：**

* 设置使用 UNET 的网络。
* 在混合的现实设备之间共享全息。
* 建立应用程序，具体取决于使用混合的现实设备的不同视图。
* 创建其中 HoloLens 用户指南沉浸式耳机用户可通过一些简单的填数游戏的共享的体验。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>共享 250 MR:HoloLens 和沉浸式耳机</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>先决条件

* 使用 Windows 10 电脑[必要开发工具](install-the-tools.md)并[配置为支持 Windows Mixed Reality 沉浸式头戴式](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。
* 适用于您的 PC 一个 Xbox 控制器。
* 至少一个 HoloLens 设备和一个沉浸式头戴式耳机。
* 这允许发现的 UDP 广播网络。

### <a name="project-files"></a>项目文件

* 下载[文件](https://github.com/Microsoft/MixedReality250/archive/master.zip)所需的项目。 将文件解压缩到易记的位置。
* 此项目需要[Windows Mixed Reality 支持建议的版本的 Unity](install-the-tools.md)。

>[!NOTE]
>如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/MixedReality250)。

## <a name="chapter-1---holo-world"></a>第 1 章-Holo 世界

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>目标

请确保在开发环境已准备好使用一个简单的项目。

### <a name="what-we-will-build"></a>我们将生成

HoloLens 或 Windows Mixed Reality 沉浸式头戴式显示一张全息图应用程序。

### <a name="steps"></a>步骤
* 打开 Unity。
    * 选择**打开**。
    * 导航到解压缩项目文件。
    * 单击“选择文件夹”。
    * *将需要一段也用于 Unity 处理第一次的项目。*
* 检查在 Unity 中启用混合现实。
    * 打开生成设置对话框 (**控制 + Shift + B**或**文件 > 生成设置...**).
    * 选择**通用 Windows 平台**然后单击**交换机平台**。
    * 选择**编辑 > 播放器设置**。
    * 在中**Inspector**上的右侧面板中，展开**XR 设置**。
    * 检查**受支持的虚拟现实**框。
    * *Windows Mixed Reality 应虚拟现实 SDK。*
* 创建一个场景。
    * 在中**层次结构**右键单击**Main Camera**选择**删除**。
    * 从**HoloToolkit > 输入 > 预设**拖动**MixedRealityCameraParent**到**层次结构**。
* 向场景添加全息
    * 从**AppPrefabs**拖动**Skybox**到**场景视图**。
    * 从**AppPrefabs**拖动**经理**到**层次结构**。
    * 从**AppPrefabs**拖动**岛**到**层次结构**。
* 保存并生成
    * 保存 (任一**控制 + S**或**文件 > 保存场景**)
    * 由于这是新的场景，你将需要其命名。 名称并不重要，但我们使用 SharedMixedReality。
* 将导出到 Visual Studio
    * 打开生成菜单 (**控制 + Shift + B**或**文件 > 生成设置**)
    * 单击**添加打开的场景。**
    * 检查**UnityC#项目**
    * 单击“生成” 。
    * 在文件资源管理器窗口中显示，创建名为的新文件夹**应用**。
    * 单击一下**应用**文件夹。
    * 按**选择文件夹。**
    * **等待生成完成**
    * 在文件资源管理器窗口中显示，导航到**应用**文件夹。
    * 双击**SharedMixedReality.sln**以启动 Visual Studio
* 从 Visual Studio 生成
    * 使用顶部的工具栏更改到目标**发行**并**x86**。
    * 单击箭头旁边**本地计算机**，然后选择**设备**将部署到 HoloLens
    * 单击箭头旁边**设备**，然后选择**本地计算机**部署混合的现实耳机。
    * 单击**调试-> 启动但不调试**或**控制 + F5**启动应用程序。

### <a name="digging-into-the-code"></a>深入探讨代码

在项目面板中，导航到**Assets\HoloToolkit\Input\Scripts\Utilities**然后双击**MixedRealityCameraManager.cs**以将其打开。

**概述：** MixedRealityCameraManager.cs 是一个简单的脚本，可调整基于设备的质量级别和背景设置。 是 HolographicSettings.IsDisplayOpaque，允许脚本以检测设备是否处于 HoloLens （IsDisplayOpaque 返回 false） 或沉浸式头戴式 （IsDisplayOpaque 返回 true）。

### <a name="enjoy-your-progress"></a>享受您的进度

此时应用程序只需将呈现一张全息图。 我们将在稍后添加到全息图交互。 这两种设备将呈现全息图相同。 沉浸式头戴式还会呈现蓝色天空和云背景。

## <a name="chapter-2---interaction"></a>第 2 章-交互

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>目标

演示如何处理 Windows Mixed Reality 应用程序的输入。

### <a name="what-we-will-build"></a>我们将生成

第 1 章提供的应用程序上构建，我们将添加功能，可允许用户选取全息图，并将其放置在 HoloLens 现实世界图面上或在沉浸式头戴式中对虚拟表。

**输入刷新程序：** 选择手势是在 HoloLens**敲击**。 在沉浸式耳机，我们将使用**A** Xbox 控制器上的按钮。 有关详细信息输入[从这里开始](gestures.md)。

### <a name="steps"></a>步骤
* 添加输入管理器
    * 从**HoloToolkit > 输入 > 预设**拖动**InputManager**到**层次结构**的小孩**经理**。
    * 从**HoloToolkit > 输入 > 预设 > 游标**拖动**光标**到**层次结构**。
* 添加空间映射
    * 从**HoloToolkit > SpatialMapping > 预设**拖动**SpatialMapping**到**层次结构**。
* 添加虚拟 Playspace
    * 在中**层次结构**展开**MixedRealityCameraParent**选择**边界**
    * 在中**Inspector**面板中选中复选框以启用**边界**
    * 从**AppPrefabs**拖动**VRRoom**到**层次结构**。
* 添加 WorldAnchorManager
    * 在中**层次结构**，选择**经理**。
    * 在中**Inspector**，单击**添加组件**。
    * 类型**世界定位点管理器**。
    * 选择**世界定位点管理器**以将其添加。
* 将 TapToPlace 添加到岛
    * 在中**层次结构**，展开**岛**。
    * 选择**MixedRealityLand**。
    * 在中**Inspector**，单击**添加组件**。
    * 类型**点击位置**并将其选中。
    * 检查**父置于点击**。
    * 设置**放置偏移量**到 **（0，0.1，0）**。
* 保存并像以前那样生成

### <a name="digging-into-the-code"></a>深入探讨代码

**Script 1 - GamepadInput.cs**

在项目面板中导航到**Assets\HoloToolkit\Input\Scripts\InputSources**然后双击**GamepadInput.cs**以将其打开。 从项目面板中的相同路径，双击**InteractionSourceInputSource.cs**。

请注意，这两个脚本具有一个公共基类，BaseInputSource。

BaseInputSource 保留对 InputManager，允许触发事件的脚本的引用。 在这种情况下，InputClicked 事件是相关的。 这将是一定要记住，当我们获取到脚本 2，TapToPlace。 对于 GamePadInput，我们轮询按下，在控制器上的一个按钮，然后我们引发 InputClicked 事件。 对于 InteractionSourceInputSource，我们引发响应 TappedEvent InputClicked 事件。

**脚本 2-TapToPlace.cs**

在项目面板中导航到**Assets\HoloToolkit\SpatialMapping\Scripts**然后双击**TapToPlace.cs**以将其打开。

许多开发人员想要实现创建全息版的应用程序时的第一个操作移动全息手势输入。 在这种情况下，我们已 endeavored 进行全面注释此脚本。 值得强调本教程中的一些事项。

首先，请注意 TapToPlace 实现 IInputClickHandler。 IInputClickHandler 公开函数，用于处理由 GamePadInput.cs 或 InteractionSourceInputSource.cs 引发的 InputClicked 事件。 OnInputClicked 时 BaseInputSource 检测单击具有 TapToPlace 对象处于焦点时调用。 是 airtapping 上 HoloLens 或 Xbox 控制器上按一个按钮将触发该事件。

第二个是执行更新，请参阅是否图面正在调查以便我们可以将游戏对象放在表面，类似于表中的代码。 因此沉浸式头戴式没有概念实际应用层协议，该对象表示表顶部 (Vroom > TableThingy > 多维数据集) 已被标记为 SpatialMapping 物理层，因此在更新中强制转换的射线将与虚拟表顶部发生冲突。

### <a name="enjoy-your-progress"></a>享受您的进度

这一次可以选择岛以将其移动。 HoloLens 上可以将岛移到实际的图面。 在沉浸式头戴式可以将岛移到我们添加的虚拟表。

## <a name="chapter-3---sharing"></a>第 3 章 — 共享

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>目标

确保已正确配置的网络，并且详细介绍如何在设备之间共享空间的定位点。

### <a name="what-we-will-build"></a>我们将生成

我们会将我们的项目转换到多玩家项目。 我们会将 UI 和逻辑添加到主机或联接会话。 HoloLens 用户将看到每个其他云会话中通过头、 和沉浸式头戴式用户有接近定位点所在的云。 在沉浸式耳机的用户将看到相对于场景的原点的 HoloLens 用户。 HoloLens 用户将看到在同一位置岛的全息图。 请注意沉浸式耳机中的用户将不会在岛上这一章，但将行为非常相似到 HoloLens，岛的鸟密切关注视图至关重要。

### <a name="steps"></a>步骤
* 删除岛和 VRRoom
    * 在中**层次结构**右键单击**岛**选择**删除**
    * 在中**层次结构**右键单击**VRRoom**选择**删除**
* 添加 Usland
    * 从**AppPrefabs**拖动**Usland**到**层次结构**。
* 从**AppPrefabs**拖到下面每一**层次结构**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* 保存并像以前那样生成

### <a name="digging-into-the-code"></a>深入探讨代码

在项目面板中，导航到**Assets\AppPrefabs\Support\SharingWithUnet\Scripts** ，并双击**UnetAnchorManager.cs**。 一个 HoloLens 与另一个 HoloLens 共享跟踪信息，以便这两种设备可以共享相同的空间的功能即将达到神奇。 混合现实的强大功能处于活动状态时两个或更多的人可以使用相同的数字数据进行协作。

需要指出此脚本中的一些事项：

在开始函数中，请注意，检查是否有**IsDisplayOpaque**。 在这种情况下，我们假设建立定位点。 这是因为沉浸式耳机不会公开一种方法来导入或导出的定位点。 如果我们在 HoloLens 上运行，但是，此脚本实现设备之间共享的定位点。 启动会话的设备将创建用于导出的定位点。 加入会话时的设备将从设备启动会话的请求定位点。

**导出：**

当用户创建一个会话时，NetworkDiscoveryWithAnchors 将调用 UNETAnchorManagers CreateAnchor 函数。 让我们按照 CreateAnchor 流。

我们首先执行一些保养工作，清除任何数据，我们有可能收集的上一个定位点。 然后我们会检查是否有要加载的缓存的密钥。 定位点数据往往介于 5 到 20 个 MB，以便重复使用缓存的定位点可以在保存的数据，我们需要通过网络进行传输的量。 我们将看到此工作方式有点更高版本。 即使我们要重新使用定位点，我们需要获取数据准备新的客户端加入的情况下不具有的定位点定位点。

谈到准备定位点数据，WorldAnchorTransferBatch 类公开的功能来准备要定位数据发送到另一台设备或应用程序和功能，若要导入的定位点数据。 由于我们是在导出路径上，我们会将我们的定位点添加到 WorldAnchorTransferBatch 并调用 ExportAsync 函数。 为生成导出的数据，ExportAsync 然后将调用 WriteBuffer 回调。 导出的所有数据后将调用 ExportComplete。 WriteBuffer 中我们将数据块添加到我们将继续保留用于导出的列表。 ExportComplete 中我们将列表转换为数组。 AnchorName 变量也设置，这将触发其他设备以请求定位点，如果他们没有它。

在某些情况下，定位点不会导出或将创建极少的数据，我们将重试。 此处我们只需 CreateAnchor 再次调用。

导出路径中的最后一个函数是 AnchorFoundRemotely。 当另一台设备发现了定位点时，该设备将告诉主机和主机将使用的作为定位点是"良好定位点"的信号，并可以缓存。

**导入：**

当 HoloLens 加入会话时，它需要导入定位点。 在 UNETAnchorManager 的更新函数中，AnchorName 被轮询一次。 定位点名称更改时，导入过程开始。 首先，我们尝试从本地的定位点存储加载具有指定名称的定位点。 如果我们已经有了它，我们可以使用它而无需再次下载数据。 如果我们没有它，然后我们调用 WaitForAnchor 将启动下载。

完成下载后，调用 NetworkTransmitter_dataReadyEvent。 这将指示更新循环以使用下载的数据调用 ImportAsync。 导入过程完成后，ImportAsync 将调用 ImportComplete。 如果导入成功，定位点将保存在本地播放机应用商店。 PlayerController.cs 实际上可以调用 AnchorFoundRemotely 以让主机知道已建立良好的定位点。

### <a name="enjoy-your-progress"></a>享受您的进度

这一次用户与 HoloLens 将承载会话使用**启动会话**在 UI 中的按钮。 其他用户，同时在 HoloLens 或沉浸式头戴式耳机，将选择该会话，然后选择**加入会话**在 UI 中的按钮。 如果有多个用户与 HoloLens 设备，他们将对着头看有红色的云。 此外将每个沉浸式头戴式耳机，蓝色云朵不过蓝色云将不是上面耳机，因为耳机不尝试查找与 HoloLens 设备相同的世界坐标空间。

此项目中的点是一个包含共享的应用程序;它不多，并可作为比较基准。 在下一步的章节中，我们将开始生成的人们能够享受的体验。 若要获取进一步上共享的体验设计指南，请转到此处。

## <a name="chapter-4---immersion-and-teleporting"></a>第 4 章-浸入式和 teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>目标

在面向到每种类型的混合的现实设备的体验。

### <a name="what-we-will-build"></a>我们将生成

我们将更新应用程序将在沉浸式视图岛上的沉浸式头戴式用户。 HoloLens 用户将仍然可以岛的鸟瞰视图。 每个设备类型的用户可以看到其他用户，世界中的显示方式。 例如，沉浸式头戴式用户可以看到岛上的其他路径上的其他虚拟形象和 HoloLens 用户看作上面岛的巨大云。 如果 HoloLens 用户正在查看岛，沉浸式头戴式用户也会看到 HoloLens 用户视线移动射线的光标。 HoloLens 用户将在岛来表示每个沉浸式头戴式用户上看到头像。

**沉浸式设备的更新的输入：**
* Xbox 控制器上的左侧缓冲器和右缓冲器按钮旋转播放机
* 保存 Xbox 控制器上的 Y 按钮将启用[teleport](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)游标。 如果释放 Y 按钮时，游标将有一个旋转箭头指示符，将为 teleported 到游标的位置。

### <a name="steps"></a>步骤
* 添加到 MixedRealityCameraParent MixedRealityTeleport
    * 在中**层次结构**，选择**Usland**。
    * 在中**Inspector**，启用**级别控制**。
    * 在中**层次结构**，选择**MixedRealityCameraParent**。
    * 在中**Inspector**，单击**添加组件**。
    * 类型**混合现实 Teleport**并将其选中。

### <a name="digging-into-the-code"></a>深入探讨代码

沉浸式头戴式用户将已接入到他们的 Pc 电缆，但我们岛较大的电缆是长时间。 若要补偿，我们需要移动独立于用户的运动相机的功能。 请参阅[舒适页](comfort.md)设计混合的现实应用程序 （特别是自运动和 locomotion） 有关详细信息。

为了说明此过程将需要定义两个术语。 首先，**运输车**将从用户独立移动相机的对象。 一个子游戏对象**运输车**将为**主照相机**。 主照相机被附加到用户的头。

在项目面板中，导航到**Assets\AppPrefabs\Support\Scripts\GameLogic** ，并双击**MixedRealityTeleport.cs**。

MixedRealityTeleport 具有两个作业。 首先，它可以处理使用缓冲器旋转。 在更新函数中我们轮询 LeftBumper 和 RightBumper ButtonUp。 GetButtonUp 仅返回 true 之后又被向下按钮已启动第一个框架上。 如果未引发任一按钮，我们知道用户需要进行旋转。

我们旋转时我们执行淡入淡出和淡入使用一个简单的脚本名为 fade 控件。 我们这样做可以防止用户看到的不自然的位移，这可能导致不适。 淡入淡出和签出的效果是相当简单。 我们有挂起的前面黑色四**主照相机**。 淡我们转换从 0 到 1 的 alpha 值。 这将逐渐导致四来呈现并会掩盖其背后提供支持的任何内容的黑色像素。 当返回淡出我们过渡的 alpha 值为零。

当我们计算旋转时，请注意，我们要轮替我们**运输车**但计算绕旋转**主照相机**。 这是重要，因为较远**主照相机**离开 0,0,0，是不太准确绕运输车旋转将成为从用户的角度。 事实上，如果不旋转照相机的位置附近，用户将移动上一段弧线，围绕**运输车**而不是旋转。

MixedRealityTeleport 的第二个作业将处理移动**运输车**。 这是在 SetWorldPosition。 SetWorldPosition 采用所需的世界位置，用户希望 percieve 它们占据的位置。 我们需要将我们**运输车**减去的本地位置的该位置**主照相机**，因为该偏移量就会添加每个帧。

第二个脚本调用 SetWorldPosition。 让我们看一下该脚本。 在项目面板中，导航到**Assets\AppPrefabs\Support\Scripts\GameLogic** ，并双击**TeleportScript.cs**。

此脚本是比 MixedRealityTeleport 有点复杂。 正在检查 Xbox 控制器上的 Y 按钮，以按下的脚本。 持有该按钮时光标呈现 teleport 下和脚本将从用户的视线移动位置 ray 强制转换。 如果该射线与增加或减少正的表面上有冲突，指向在图面将被视为到 teleport，良好的图面，将启用对 teleport 游标动画。 如果该射线不与图面，增加或减少指针冲突，则将禁用对游标的动画。 时发布的 Y 按钮和计算的射线的点是有效的位置，则脚本将调用 SetWorldPosition 与射线相交的位置。

### <a name="enjoy-your-progress"></a>享受您的进度

这一次你需要找到一位朋友。

再次重申，具有 HoloLens 的用户将承载会话。 其他用户将加入会话。 应用程序会将前三个用户从一个岛上的三个路径上沉浸式头戴式加入。 随意浏览在本部分中岛。

需要注意的详细信息：
1. 您可以看到人脸在云中，从而可帮助 immersed 的用户可以查看 HoloLens 用户正在查找的方向。
2. 头像岛上的具有 necks 旋转。 它们不会按照用户的作用是 （我们没有该信息） 的真实现实，但它具有很好的体验。
3. 如果 HoloLens 用户正在查看岛，immersed 的用户可以看到其光标。
4. 表示 HoloLens 用户的云转换阴影。

## <a name="chapter-5---finale"></a>第 5 章-最终方法

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>目标

创建两个设备类型之间的协作交互式体验。

### <a name="what-we-will-build"></a>我们将生成

当沉浸式头戴式具有的用户在岛上获取附近填数游戏的基础上第 4 章，HoloLens 用户将获得带给出测验题的线索的工具提示。 一旦所有沉浸式头戴式用户火箭房间中获取过去的其填数游戏和到"准备板"上，将启动火箭。

### <a name="steps"></a>步骤
* 在中**层次结构**，选择**Usland**。
* 在中**Inspector**，在**级别控制**，检查**启用协作**。

### <a name="digging-into-the-code"></a>深入探讨代码

现在让我们看一下 LevelControl.cs。 此脚本是游戏逻辑核心，并维护游戏状态。 由于这是使用 UNET 的多玩家游戏我们需要了解的数据流动方式，至少也足够修改本教程。 UNET 的更完整概述，请参阅 Unity 的文档。

在项目面板中，导航到**Assets\AppPrefabs\Support\Scripts\GameLogic** ，并双击**LevelControl.cs**。

让我们了解一下如何沉浸式头戴式指示它们可供火箭启动。 列表中的对应于岛上的三个路径的布尔设置三个布尔的其中一个可传达火箭启动准备情况。 当分配给路径的用户基础火箭房间内的棕色板上时，将设置路径的布尔值。 好了，现在我们来详细信息。

我们会在 update （） 函数中。 您将注意有备' 函数。 我们用它在开发过程中来测试火箭启动和重置序列。 它无法在多用户体验。 希望按时间消化理解以下信息可以使其工作。 请参阅是否我们应耍了花招，我们检查后，我们检查以查看是否沉浸本地播放机。 我们想要专注于我们发现我们所处的目标。 在 if （沉浸） 检查，没有调用来隐藏 CheckGoal **EnableCollaboration** bool。 这对应于完成这一章的步骤同时选中该复选框。 内部 EnableCollaboration 我们可以看到对 CheckGoal() 的调用。

CheckGoal 执行某些数学运算来确定我们是否增加或减少现有板上。 当我们，我们 Debug.Log"已到达目标"，然后我们调用 SendAtGoalMessage()。 在 SendAtGoalMessage 我们调用 playerController.SendAtGoal。 为你节省一些时间，下面是代码：

```cs
private void CmdSendAtGoal(int GoalIndex)
       {
           levelState.SetGoalIndex(GoalIndex);
       }
```

```cs
public void SendAtGoal(int GoalIndex)
       {
           if (isLocalPlayer)
           {
               Debug.Log("sending at goal " + GoalIndex);
               CmdSendAtGoal(GoalIndex);
           }
       }
```

请注意 SendAtGoalMessage 调用 CmdSendAtGoal，哪些调用 levelState.SetGoalIndex，LevelControl.cs 已恢复。 乍一看这似乎有点奇怪。 为什么不只是调用 SetGoalIndex 而不是这很奇怪，player 控制器通过路由？ 原因是我们符合到 UNET 用于使数据保持同步的数据模型。为防止作弊和抖动，UNET 要求每个对象都有权更改已同步的变量的用户。 此外，主机 （启动会话的用户） 可以直接更改数据。 用户不是主机，但具有颁发机构，需要将 command 发送到的主机，这将更改该变量。 默认情况下主机具有颁发机构对所有对象，生成来表示用户的对象除外。 在本例中此对象具有 playercontroller 脚本。 一种方法来请求对象的颁发机构，然后进行更改，但我们选择利用这一事实，player 控制器已通过，player 控制器的自我颁发机构和路由命令。

换句话说，我们发现我们自己在我们的目标时，播放机需要告诉主机，主机将告诉其他人。

返回在 LevelControl.cs SetGoalIndex 看。 此处我们将在 synclist (AtGoal) 中设置的值的值。 请记住，我们是在主机的上下文中时执行此操作。 类似于命令，RPC 是主机可以发出的内容将导致所有客户端运行一些代码。 此处我们调用 RpcCheckAllGoals。 每个客户端将逐个检查以查看是否设置所有三个 AtGoals，并且如果是这样，启动火箭。

### <a name="enjoy-your-progress"></a>享受您的进度

基于上一章，我们将开始在与之前的会话。 这次是对在其路径中，这个"门"沉浸式头戴式 get 中的用户作为工具提示将显示仅 HoloLens 用户可以看到。 HoloLens 用户负责通信向在沉浸式头戴式用户此线索。 火山中其相应棕色板上每个虚拟形象具有单步执行后，火箭将启动到空间。 场景在 60 秒之后将重置以便可以再次执行它。

## <a name="see-also"></a>请参阅
* [MR 输入 213:运动控制器](mixed-reality-213.md)
