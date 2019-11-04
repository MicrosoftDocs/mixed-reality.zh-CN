---
title: 尊敬的共享 250-HoloLens 和沉浸式耳机
description: 使用 Unity、Visual Studio、HoloLens 和 Windows Mixed Reality 耳机执行此编码演练，了解在混合现实设备之间共享全息影像的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、沉浸式、运动控制器、共享、xbox 控制器、网络、跨设备
ms.openlocfilehash: c8d341f75424887ca1b0994c8a4d16a0bded671e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437871"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。  因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。  这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR 共享250： HoloLens 和沉浸式耳机

通过通用 Windows 平台（UWP）的灵活性，可以轻松创建跨多个设备的应用程序。 通过这种灵活性，我们可以创建利用每个设备的优势的体验。 本教程将介绍在 HoloLens 和 Windows Mixed Reality 沉浸式耳机上运行的基本共享体验。 此内容最初在华盛顿州西雅图的 Microsoft Build 2017 大会上交付。

**在本教程中，我们将：**

* 使用 UNET 设置网络。
* 跨混合现实设备共享全息影像。
* 根据正在使用的混合现实设备，建立不同的应用程序视图。
* 通过一些简单的测验题，为 HoloLens 用户指导沉浸式耳机用户。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 共享250： HoloLens 和沉浸式耳机</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>必备条件

* 带有[必要的开发工具](install-the-tools.md)且[已配置为支持 windows Mixed Reality 沉浸式耳机](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的 Windows 10 电脑。
* 适用于你的电脑的 Xbox 控制器。
* 至少一个 HoloLens 设备和一个沉浸式耳机。
* 允许 UDP 广播进行发现的网络。

### <a name="project-files"></a>项目文件

* 下载项目所需的[文件](https://github.com/Microsoft/MixedReality250/archive/master.zip)。 将文件提取到易于记忆的位置。
* 此项目需要[具有 Windows Mixed Reality 支持的推荐版本的 Unity](install-the-tools.md)。

>[!NOTE]
>如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/MixedReality250)找到。

## <a name="chapter-1---holo-world"></a>第1章-Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>目标

请确保开发环境已准备好使用简单项目。

### <a name="what-we-will-build"></a>要生成的内容

在 HoloLens 或 Windows Mixed Reality 沉浸式耳机上显示全息图的应用程序。

### <a name="steps"></a>步骤

* 打开 Unity。
    * 选择 "**打开**"。
    * 导航到在其中提取项目文件的位置。
    * 单击“选择文件夹”。
    * *Unity 第一次处理项目需要一些时间。*
* 检查 Unity 中是否已启用混合现实。
    * 打开 "生成设置" 对话框（**ctrl + Shift + B**或 "**文件 > 生成设置 ...** "）。
    * 选择**通用 Windows 平台**然后单击 "**切换平台**"。
    * 选择 "**编辑 > 播放机设置**"。
    * 在右侧的**检查器**面板中，展开 " **XR 设置**"。
    * 选中 "**支持虚拟现实**" 框。
    * *Windows Mixed Reality 应为虚拟现实 SDK。*
* 创建场景。
    * 在**层次结构**中右键单击 "**主相机**"，然后选择 "**删除**"。
    * 从**HoloToolkit > 输入 > prototyping**将**MixedRealityCameraParent**拖到**层次结构**中。
* 向场景中添加全息影像
    * From **AppPrefabs**将**Skybox**拖到**场景视图**。
    * From **AppPrefabs**将**经理**拖到**层次结构**中。
    * From **AppPrefabs**将**岛**拖到**层次结构**中。
* 保存并生成
    * 保存（ **Control + S**或**File > save 场景**）
    * 由于这是新场景，因此需要将其命名为。 名称并不重要，但我们使用的是 SharedMixedReality。
* 导出到 Visual Studio
    * 打开 "生成" 菜单（**ctrl + Shift + B**或**File > 生成设置**）
    * 单击 "**添加打开的场景"。**
    * 检查**Unity C#项目**
    * 单击**生成**。
    * 在出现的 "文件资源管理器" 窗口中，创建一个名为 "**应用**" 的新文件夹。
    * 单击**应用**文件夹。
    * 按 "**选择文件夹"。**
    * **等待生成完成**
    * 在出现的 "文件资源管理器" 窗口中，导航到 "**应用**" 文件夹。
    * 双击 " **SharedMixedReality** " 以启动 Visual Studio
* 从 Visual Studio 生成
    * 使用顶部工具栏将目标更改为 "**发布**" 和 " **x86**"。
    * 单击 "**本地计算机**" 旁边的箭头，并选择 "要部署到 HoloLens 的**设备**"
    * 单击 "**设备**" 旁边的箭头，并选择 "要为混合现实耳机部署的**本地计算机**"。
    * 单击 "**调试"-> "无调试开始**" 或按**F5**启动应用程序。

### <a name="digging-into-the-code"></a>深入到代码中

在 "项目" 面板中，导航到 " **Assets\HoloToolkit\Input\Scripts\Utilities** "，然后双击 " **MixedRealityCameraManager.cs** " 将其打开。

**概述：** MixedRealityCameraManager.cs 是一个简单的脚本，可根据设备调整质量级别和背景设置。 此处的密钥为 HolographicSettings。 IsDisplayOpaque，它允许脚本检测设备是 HoloLens （IsDisplayOpaque 返回 false）还是沉浸式耳机（IsDisplayOpaque 返回 true）。

### <a name="enjoy-your-progress"></a>欣赏你的进度

此时，应用程序将只呈现一个全息图。 稍后我们将向全息图添加交互。 这两个设备会将两个全息图呈现相同的。 沉浸式耳机还会呈现蓝天和云背景。

## <a name="chapter-2---interaction"></a>第2章-交互

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>目标

演示如何处理 Windows Mixed Reality 应用程序的输入。

### <a name="what-we-will-build"></a>要生成的内容

基于第1章中的应用程序，我们将添加功能，使用户能够选择全息影像，并将其放在 HoloLens 的真实表面上，或将其放置在沉浸式耳机中的虚拟表上。

**输入刷新器：** 在 HoloLens 上，选择手势是**点击**。 在沉浸式耳机上，我们将使用 Xbox 控制器上**的按钮。** 有关详细信息，请查看[交互模型概述](interaction-fundamentals.md)。

### <a name="steps"></a>步骤

* 添加输入管理器
    * 从**HoloToolkit > 输入 > prototyping**将**InputManager**作为**经理**的子项拖到**层次结构**中。
    * 从**HoloToolkit > 输入 > prototyping > 光标**将**光标**拖到**层次结构**中。
* 添加空间映射
    * From **HoloToolkit > SpatialMapping > prototyping**将**SpatialMapping**拖到**层次结构**中。
* 添加虚拟 Playspace
    * 在**层次结构**中展开**MixedRealityCameraParent**选择**边界**
    * 检查**器**面板中的复选框以启用**边界**
    * From **AppPrefabs**将**VRRoom**拖到**层次结构**中。
* 添加 WorldAnchorManager
    * 在**层次结构**中，选择 "**管理器**"。
    * 在**检查器**中，单击 "**添加组件**"。
    * 键入 "**世界定位管理器**"。
    * 选择 "**世界锚管理器**" 以添加它。
* 将 TapToPlace 添加到岛
    * 在**层次结构**中，展开 "**岛**"。
    * 选择**MixedRealityLand**。
    * 在**检查器**中，单击 "**添加组件**"。
    * 键入 "**点击" 以将**其选中。
    * **在点击时选中 "父项"** 。
    * 将**放置偏移**设置为 **（0，0.1，0）** 。
* 像以前一样保存并生成

### <a name="digging-into-the-code"></a>深入到代码中

**脚本 1-GamepadInput.cs**

在 "项目" 面板中，导航到 " **Assets\HoloToolkit\Input\Scripts\InputSources** "，然后双击 " **GamepadInput.cs** " 将其打开。 在 "项目" 面板的同一路径中，双击 " **InteractionSourceInputSource.cs**"。

请注意，这两个脚本都有一个公共的基类 BaseInputSource。

BaseInputSource 保留对 InputManager 的引用，这允许脚本触发事件。 在这种情况下，InputClicked 事件是相关的。 当我们进入脚本 2 TapToPlace 时，请务必记住这一点。 对于 GamePadInput，我们轮询控制器上要按下的按钮，然后引发 InputClicked 事件。 对于 InteractionSourceInputSource，我们将引发 InputClicked 事件以响应 TappedEvent。

**脚本 2-TapToPlace.cs**

在 "项目" 面板中，导航到 " **Assets\HoloToolkit\SpatialMapping\Scripts** "，然后双击 " **TapToPlace.cs** " 将其打开。

许多开发人员在创建全息应用程序时要实现的第一件事是使用手势输入来移动全息影像。 同样，我们已 endeavored 对此脚本进行全面注释。 对于本教程，有几个值得注意的事项。

首先，请注意，TapToPlace 实现了 IInputClickHandler。 IInputClickHandler 公开处理 GamePadInput.cs 或 InteractionSourceInputSource.cs 引发的 InputClicked 事件的函数。 当 BaseInputSource 检测到具有 TapToPlace 的对象时，将调用 OnInputClicked。 在 HoloLens 上 airtapping 或按下 Xbox 控制器上的一个按钮将触发该事件。

第二是在更新中执行代码以查看是否正在查看某个面，以便我们可以将游戏对象放置在图面上，如表。 沉浸式头戴式耳机没有实面的概念，因此表示表顶部的对象（Vroom > TableThingy > 多维数据集）已使用 SpatialMapping 物理学层进行标记，因此更新中的 ray 强制转换会与虚拟表的顶部发生冲突。

### <a name="enjoy-your-progress"></a>欣赏你的进度

这一次，您可以选择要移动的岛。 在 HoloLens 上，你可以将岛移动到真实表面。 在沉浸式耳机中，你可以将岛移动到我们添加的虚拟表。

## <a name="chapter-3---sharing"></a>第3章-共享

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>目标

确保已正确配置网络，并详细说明如何在设备之间共享空间锚。

### <a name="what-we-will-build"></a>要生成的内容

我们会将项目转换为多玩家项目。 我们会将 UI 和逻辑添加到主机或加入会话。 HoloLens 用户会在会话中使用其打印头上的云查看彼此，并且沉浸式头戴式耳机用户在锚定到的位置附近有云。 沉浸式耳机中的用户将看到 HoloLens 用户相对场景的原点。 HoloLens 用户将在同一位置看到岛的全息影像。 需要注意的是，沉浸式耳机中的用户将不会在本章节中的岛上出现，但会表现得非常类似于 HoloLens，并具有岛的鸟瞰视图。

### <a name="steps"></a>步骤

* 删除岛和 VRRoom
    * 在**层次结构**中右键单击**岛**选择**删除**
    * 在**层次结构**中右键单击**VRRoom**选择**删除**
* 添加 Usland
    * From **AppPrefabs**将**Usland**拖到**层次结构**中。
* 从**AppPrefabs**将以下各项拖动到**层次结构**：
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* 像以前一样保存并生成

### <a name="digging-into-the-code"></a>深入到代码中

在 "项目" 面板中，导航到 " **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** "，然后双击 " **UnetAnchorManager.cs**"。 一个 HoloLens 与另一个 HoloLens 共享跟踪信息，使这两个设备可以共享相同空间的功能在神奇附近。 当两个或多个用户可以使用相同的数字数据进行协作时，混合现实的强大功能将处于活动状态。

在此脚本中需要指出的几点：

在 start 函数中，请注意对**IsDisplayOpaque**的检查。 在这种情况下，我们假设已建立定位点。 这是因为沉浸式耳机不公开导入或导出锚的方式。 但是，如果我们在 HoloLens 上运行，则此脚本在设备之间实现共享锚。 启动会话的设备将创建用于导出的定位点。 加入会话的设备将从启动会话的设备请求定位点。

**输出**

当用户创建会话时，NetworkDiscoveryWithAnchors 将调用 UNETAnchorManagers CreateAnchor 函数。 我们来看看 CreateAnchor flow。

首先，我们会进行一些内务处理，清除我们为先前定位点收集的任何数据。 然后检查是否有要加载的缓存锚。 定位点数据的大小通常介于5到 20 MB 之间，因此重复使用缓存的定位点可以节省需要通过网络传输的数据量。 稍后我们将介绍此功能的工作原理。 即使我们正在重用定位点，我们也需要在没有定位点的新客户端联接的情况下获取定位点数据。

说到定位点数据已准备就绪，WorldAnchorTransferBatch 类公开了准备用于发送到其他设备或应用程序的定位点数据的功能，并提供了导入定位数据的功能。 由于我们的是导出路径，因此，我们会将定位点添加到 WorldAnchorTransferBatch 并调用 ExportAsync 函数。 然后，ExportAsync 将调用 WriteBuffer 回调，因为它会生成导出的数据。 导出所有数据后，将调用 ExportComplete。 在 WriteBuffer 中，我们将数据块添加到要导出的列表。 在 ExportComplete 中，我们将列表转换为数组。 还设置了 AnchorName 变量，这会触发其他设备请求定位点（如果没有）。

在某些情况下，定位点将不会导出或创建很少的数据，我们将重试。 这里我们再次调用 CreateAnchor。

导出路径中的 final 函数为 AnchorFoundRemotely。 当另一个设备找到定位点时，该设备将通知主机，主机会将其用作信号，指示锚点为 "良好锚定" 并可缓存。

**导入**

当 HoloLens 加入会话时，它需要导入一个定位点。 在 UNETAnchorManager 的 Update 函数中，将对 AnchorName 进行轮询。 定位点名称更改时，导入过程开始。 首先，我们尝试从本地定位点存储中加载具有指定名称的定位点。 如果已有该数据，则可以使用它，而无需再次下载数据。 如果没有，请调用 WaitForAnchor，这将启动下载。

下载完成后，将调用 NetworkTransmitter_dataReadyEvent。 这会向更新循环发出信号，以便对下载的数据调用 ImportAsync。 导入过程完成后，ImportAsync 将调用 ImportComplete。 如果导入成功，定位点将保存在本地播放机存储区中。 PlayerController.cs 实际上会调用 AnchorFoundRemotely，让主机知道已经建立好锚。

### <a name="enjoy-your-progress"></a>欣赏你的进度

这次使用 HoloLens 的用户将使用用户界面中的 "**启动会话**" 按钮来托管会话。 在 HoloLens 或沉浸式耳机上，其他用户将选择该会话，然后在 UI 中选择 "**加入会话**" 按钮。 如果有多个用户使用 HoloLens 设备，它们会在其打印头上包含红色的云。 对于每个沉浸式耳机，还会有一个蓝色的云，但蓝色云不会位于耳机上方，因为耳机不会尝试查找与 HoloLens 设备相同的世界坐标空间。

项目中的这一点是包含共享应用程序;这并不是很多，而且可以充当基线。 在接下来的章节中，我们将开始为用户带来体验。 若要获取有关共享体验设计的更多指导，请转到此处。

## <a name="chapter-4---immersion-and-teleporting"></a>第4章-浸入式和 teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>目标

为每种类型的混合现实设备满足经验。

### <a name="what-we-will-build"></a>要生成的内容

我们将更新应用程序，以通过沉浸式视图将沉浸式头戴式耳机用户置于岛中。 HoloLens 用户仍将获得岛的鸟瞰视图。 每种设备类型的用户可以看到其他用户出现在世界中。 例如，沉浸式耳机用户可以查看岛上其他路径上的其他头像，并在岛上看到 HoloLens 用户为巨大的云。 如果 HoloLens 用户正在查看岛，则沉浸式耳机用户也会看到 HoloLens 用户的 "注视" 的光标。 HoloLens 用户将看到岛上的头像来表示每个沉浸式耳机用户。

**已更新沉浸式设备的输入：**

* Xbox 控制器上的左缓冲器和右缓冲器按钮将旋转播放机
* 按住 Xbox 控制器上的 Y 按钮将启用[传送](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)光标。 如果在释放 Y 按钮时光标有旋转箭头指示器，则会 teleported 光标所在的位置。

### <a name="steps"></a>步骤

* 将 MixedRealityTeleport 添加到 MixedRealityCameraParent
    * 在**层次结构**中，选择**Usland**。
    * 在**检查器**中，启用**级别控制**。
    * 在**层次结构**中，选择**MixedRealityCameraParent**。
    * 在**检查器**中，单击 "**添加组件**"。
    * 键入**混合现实传送**并将其选中。

### <a name="digging-into-the-code"></a>深入到代码中

沉浸式耳机用户将通过电缆受限到其电脑上，但岛比电缆长。 若要进行补偿，我们需要能够独立于用户的动作移动相机。 有关设计混合现实应用程序的详细信息，请参阅[舒适页面](comfort.md)（特别是自运动和 locomotion）。

若要描述此过程，请定义两个术语。 首先， **dolly**将是独立于用户移动相机的对象。 **Dolly**的子游戏对象将是**主摄像机**。 将相机连接到用户的头。

在 "项目" 面板中，导航到 " **Assets\AppPrefabs\Support\Scripts\GameLogic** "，然后双击 " **MixedRealityTeleport.cs**"。

MixedRealityTeleport 有两个作业。 首先，它使用缓冲器处理旋转。 在更新函数中，我们轮询 LeftBumper 和 RightBumper 上的 "ButtonUp"。 GetButtonUp 仅在第一帧上返回 true，按钮在关闭后就会正常运行。 如果引发了任一按钮，则我们知道用户需要旋转。

旋转时，我们使用名为 "淡化 control" 的简单脚本，进行淡出并淡出。 这样做是为了防止用户看到可能导致 discomfort 的非自然移动。 淡入和淡出效果非常简单。 在**摄像机**前面有一个黑色的故障诊断。 淡出时，将从0到1转换 alpha 值。 这会逐渐导致四个黑色像素渲染和遮蔽。 当淡化后，转换后的 alpha 值将返回零。

计算旋转时，请注意，我们要旋转**dolly** ，但计算出**摄像机**周围的旋转。 这一点很重要，因为在**摄像机**远离0，0，0时，dolly 的旋转就会从用户的角度来看。 事实上，如果不围绕相机位置旋转，用户将在**dolly**上移动，而不是旋转。

MixedRealityTeleport 的第二个作业是处理移动**dolly**。 这是在 SetWorldPosition 中完成的。 SetWorldPosition 采用所需的世界位置，该位置是用户想要 percieve 具有的位置。 我们需要将**dolly**置于该位置，而不是**主摄像机**的本地位置，因为每帧都会添加该偏移量。

第二个脚本调用 SetWorldPosition。 让我们看看该脚本。 在 "项目" 面板中，导航到 " **Assets\AppPrefabs\Support\Scripts\GameLogic** "，然后双击 " **TeleportScript.cs**"。

此脚本比 MixedRealityTeleport 更复杂一些。 脚本正在检查 Xbox 控制器上的 Y 按钮是否已关闭。 当按钮被按下时，将呈现一个传送光标，并且该脚本将从用户的注视位置转换一条射线。 如果该射线与更多或更少地指向的图面冲突，则会将该图面视为传送到的一个好图面，并将启用传送光标上的动画。 如果该射线不会与某个面上更多或更少的向上箭头发生冲突，则将禁用游标上的动画。 当 "Y" 按钮被释放并且射线的计算点为有效位置时，该脚本将使用与该射线相交的位置来调用 SetWorldPosition。

### <a name="enjoy-your-progress"></a>欣赏你的进度

这次您需要查找朋友。

同样，具有 HoloLens 的用户将托管一个会话。 其他用户将加入会话。 应用程序将把前三名用户加入到岛上三个路径之一上的沉浸式耳机上。 请随时浏览本部分中的岛。

要注意的详细信息：

1. 你可以在云中看到人脸，这有助于沉浸用户查看 HoloLens 用户正在寻找的方向。
2. 岛上的头像具有旋转 necks。 它们不会遵循用户正在执行的操作，而是真正的现实情况（我们不会提供此信息），但它可以提供良好的体验。
3. 如果 HoloLens 用户正在查看岛，沉浸用户会看到其光标。
4. 表示 HoloLens 用户投影的云。

## <a name="chapter-5---finale"></a>第5章-Finale

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>目标

在这两种设备类型之间创建协作式交互式体验。

### <a name="what-we-will-build"></a>要生成的内容

在第4章，当具有沉浸式耳机的用户在岛上出现谜题附近时，HoloLens 用户将收到一条工具提示，其中包含对测验题的线索。 所有沉浸式耳机用户都在火箭房间内进入了测验题后，就会启动火箭。

### <a name="steps"></a>步骤

* 在**层次结构**中，选择**Usland**。
* 在**检查器**的 "**级别控制**" 中，选中 "**启用协作**"。

### <a name="digging-into-the-code"></a>深入到代码中

现在让我们看看 LevelControl.cs。 此脚本是游戏逻辑的核心，并且保持游戏状态。 由于这是一个使用 UNET 的多玩家游戏，我们需要了解数据的流动方式，至少足以修改本教程。 有关 UNET 的更完整概述，请参阅 Unity 的文档。

在 "项目" 面板中，导航到 " **Assets\AppPrefabs\Support\Scripts\GameLogic** "，然后双击 " **LevelControl.cs**"。

让我们了解沉浸式耳机如何指示它们已准备好进行火箭启动。 通过在与岛上的三个路径相对应的布尔列表中设置三个布尔之一，可以传达火箭的启动准备情况。 当分配到路径的用户在火箭房间内的棕色垫的顶部时，将设置路径的 bool。 好了，现在来了解详细信息。

我们将从 Update （）函数开始。 你会注意到有一个 "使用" 函数。 我们在开发过程中使用这种测试火箭启动和重置顺序。 它在多用户体验中不起作用。 但愿您内在化以下信息可以使其正常工作。 检查是否应该是，我们会检查是否已沉浸本地播放器。 我们想要重点介绍我们的目标。 在 if （沉浸）检查内部，调用 CheckGoal 隐藏在**EnableCollaboration** bool 后面。 这对应于完成本章中的步骤时选中的复选框。 在 EnableCollaboration 内部，我们看到对 CheckGoal （）的调用。

CheckGoal 进行一些数学计算，看看是否有更多或更少的时间。 当我们进行调试时，我们将进行调试。记录 "到达目标"，然后调用 "SendAtGoalMessage （）"。 在 SendAtGoalMessage 中，我们调用 playerController. SendAtGoal。 为节省时间，请参阅以下代码：

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

请注意，SendAtGoalMessage 调用 CmdSendAtGoal，后者会调用中的 levelState。 乍一看，这似乎很奇怪。 为什么不只调用 SetGoalIndex 而不是通过播放机控制器进行这种奇怪的路由？ 原因是我们符合数据模型，UNET 使用该数据来使数据保持同步。若要防止作弊和抖动，UNET 要求每个对象都有一个有权更改同步变量的用户。 此外，只有主机（启动会话的用户）可以直接更改数据。 如果用户不是宿主但具有权限，则需要将 "command" 发送到将更改变量的主机。 默认情况下，主机拥有所有对象的权限，但生成的对象除外表示用户。 在本例中，此对象具有 playercontroller 脚本。 有一种方法可以为对象请求授权，然后进行更改，但我们选择利用这一事实：播放机控制器具有己方授权，并通过播放机控制器路由命令。

另一种方法是，当我们以我们的目标找到自己时，玩家需要告诉主机，主机会告诉所有其他人。

返回 LevelControl.cs 查看 SetGoalIndex。 这里，我们要设置 synclist （AtGoal）中值的值。 请记住，在执行此操作时，我们处于主机的上下文中。 与命令相似，RPC 是指主机可以发出的，这会导致所有客户端运行一些代码。 这里我们称之为 "RpcCheckAllGoals"。 每个客户端将分别检查是否设置了所有三个 AtGoals，如果已设置，则启动火箭。

### <a name="enjoy-your-progress"></a>欣赏你的进度

在上一章中生成，我们将像以前一样启动会话。 这一次，沉浸式头戴显示设备上的用户到达其路径上的 "门" 时，会出现一个工具提示，只有 HoloLens 用户可以看到。 HoloLens 用户负责将此线索传达给沉浸式耳机中的用户。 一旦每个虚拟形象在火山内的相应的棕色垫上火箭，就会启动空间。 场景将在60秒后重置，因此你可以重新执行此操作。

## <a name="see-also"></a>另请参阅

* [MR 输入213：运动控制器](mixed-reality-213.md)
