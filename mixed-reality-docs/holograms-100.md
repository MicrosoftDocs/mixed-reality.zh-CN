---
title: MR 要点 100-Unity 入门
description: 了解如何创建第一个基本的混合现实的 "hello world" 应用程序。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实，Windows Mixed Reality，HoloLens，沉浸，，vr，先生，入门，全息影像，学院，教程
ms.openlocfilehash: 58a1785ef74872c633cf65d6a32e24d517367359
ms.sourcegitcommit: f523b74a549721b6bec69cb5d2eca5b7673a793c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2020
ms.locfileid: "85570307"
---
# <a name="mr-basics-100-getting-started-with-unity"></a>MR 基础知识 100：Unity 入门

>[!IMPORTANT]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们**不会**在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 已经为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。

本教程将指导你创建使用 Unity 构建的基本混合现实应用。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 基础知识 100：Unity 入门</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>先决条件

* 配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。

## <a name="chapter-1---create-a-new-project"></a>第1章-创建新项目

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

若要使用 Unity 构建应用，首先需要创建一个项目。 此项目组织为多个文件夹，其中最重要的文件夹是 "资产" 文件夹。 此文件夹包含从数字内容创建工具（如 Maya、最大电影院4D 或 Photoshop）中导入的所有资产、你用 Visual Studio 创建的所有代码或你最喜欢的代码编辑器，以及 Unity 在编辑器中编写场景、动画和其他 Unity 资产类型时创建的任意数量的内容文件。

若要生成和部署 UWP 应用，Unity 可将项目导出为 Visual Studio 解决方案，该解决方案将包含所有必需的资产和代码文件。

1. 启动 Unity
2. 选择**新**
3. 输入项目名称（例如 "MixedRealityIntroduction"）
4. 输入用于保存项目的位置
5. 确保选择了**3d**切换
6. 选择 "**创建项目**"

恭喜，你可以立即开始进行混合现实自定义。

## <a name="chapter-2---setup-the-camera"></a>第2章-设置照相机

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity 摄像机处理头跟踪和 stereoscopic 呈现。 需要对主摄像机进行一些更改，以将其用于混合现实。

1. 选择文件 > 新建场景

首先，如果您将用户的起始位置想像为（**X**：0， **Y**：0， **Z**：0），则可以更容易地对应用程序进行布局。 由于摄像机正在跟踪用户的头移动，因此可以通过设置主摄像机的开始位置来设置用户的起始位置。

1. 选择 "**层次结构**" 面板中的 "**主相机**"
2. 在**检查器**面板中，找到**转换**组件，并将**位置**（**x**：0， **Y**：1， **Z**：-10）更改为（**x**：0， **Y**：0， **Z**：0）

其次，默认相机背景需要一些想法。

**对于 HoloLens 应用程序**，实际情况应该出现在照相机呈现的所有内容上，而不是 Skybox 的纹理。

1. 在 "**层次结构**" 面板中，在 "层次结构" 面板中**选择 "相机** **" 组件，并将 "** **清除标志**" 下拉列表**从 "** **Skybox** " 更改为 "**纯色**"。
2. 选择**背景**色选取器并将**RGBA**值更改为（0，0，0，0）

**对于以沉浸式耳机为目标的混合现实应用程序**，我们可以使用 Unity 提供的默认 Skybox 纹理。

1. 在 "**层次结构**" 面板中选择了**主相机**后，在 "**检查器**" 面板中查找**相机**组件，并将 "**清除标志**" 下拉列表保留为 " **Skybox**"。

第三，让我们在 Unity 中考虑近剪裁平面，并防止用户在用户接近对象或对象时向用户眼睛呈现对象。

**对于 hololens 应用程序**，near 剪辑平面可以设置为[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 米。

1. 在 "层次结构" 面板中，**在 "** **层次结构**" 面板中**选择 "相机** **" 组件，** 并将 "附近的**剪辑平面**" 字段从默认的0.3 更改为 " **0.3** **0.85**"。

**对于以沉浸式耳机为目标的混合现实应用程序**，可以使用 Unity 提供的默认设置。

1. 如果仍在 "**层次结构**" 面板中选择了**主相机**，请在 "**检查器**" 面板中查找**相机**组件，并将 "**近处剪裁飞机**" 字段保留为默认值**0.3**。

最后，让我们来保存迄今为止的进度。 若要保存场景更改，请选择 "**文件" > "将场景另存为**"，为场景**主**命名，然后选择 "**保存**"。

## <a name="chapter-3---setup-the-project-settings"></a>第3章-设置项目设置

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

在本章中，我们将设置一些 Unity 项目设置，这些设置可帮助我们面向 Windows 全息 SDK 进行开发。 我们还将设置应用程序的质量设置。 最后，我们将确保生成目标设置为通用 Windows 平台。

### <a name="unity-performance-and-quality-settings"></a>Unity 性能和质量设置

**HoloLens 的 Unity 质量设置**

![HoloLens 的 Unity 质量设置](images/qualitysettings.png)

由于在 HoloLens 上维护高的帧率非常重要，因此我们希望优化质量设置以实现最高性能。 有关性能的详细信息，请查看[Unity 的性能建议](performance-recommendations-for-unity.md)。

1. 选择 "**编辑 > 项目设置 > 质量**"
2. 选择**通用 Windows 平台**徽标下的**下拉列表**，并选择 "**非常低**"。 当 "通用 Windows 平台" 列中的框为绿色**时，将**知道设置正确应用。

**对于目标为封闭像素的混合现实应用程序**，你可以将质量设置保留为其默认值。

### <a name="target-windows-10-sdk"></a>面向 Windows 10 SDK

**面向 Windows 全息 SDK**

![面向 Windows 全息 SDK](images/xrsettings.png)

我们需要让 Unity 知道我们要导出的应用程序应创建[沉浸式视图](app-views.md)而不是2d 视图。 为此，我们将在针对 Windows 10 SDK 的 Unity 上启用虚拟现实支持。

1. 请参阅 "**编辑 > 项目设置" > Player**"。
2. 在 "播放器设置" 的**检查器面板**中，选择 "**通用 Windows 平台**" 图标。
3. 展开“XR 设置”组。
4. 在 "**呈现**" 部分中，选中 "**支持虚拟现实**" 复选框，以添加新的**虚拟现实 sdk**列表。
5. 验证列表中是否显示“Windows 混合现实”。 如果没有，请选择列表底部的“+”按钮，然后选择“Windows 混合现实” 。

>[!NOTE]
>如果看不到 "**通用 Windows 平台**" 图标，请仔细检查以确保在安装过程中选择通用 Windows 平台生成支持。 如果没有，可能需要使用正确的 Windows 安装重新安装 Unity。

获取应用了所有项目设置的出色作业。 接下来，让我们添加全息影像！

## <a name="chapter-4---create-a-cube"></a>第4章-创建多维数据集

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

在 Unity 项目中创建多维数据集类似于在 Unity 中创建任何其他对象。 将多维数据集放在用户前面非常简单，因为 Unity 的坐标系统会映射到现实世界-其中，Unity 中的一种指示器约为现实中的一个计量。

1. 在**层次结构**面板的左上角，选择 "**创建**" 下拉列表，然后选择 " **3D 对象 > 多维数据集**"。
2. 在 "**层次结构**" 面板中选择新创建的**多维数据集**
3. 在**检查器**中查找**转换**组件，并**将位置**更改为（**X**：0， **Y**：0， **Z**：2）。 *这会将 cube 2 计量置于用户的起始位置之前。*
4. 在**转换**组件中，将**旋转**更改为 **（x**：45， **Y**：45， **Z**：45），将**刻度**更改为（**x**：0.25， **Y**：0.25， **Z**：0.25）。 *这会将多维数据集缩放到0.25 米。*
5. 若要保存场景更改，请选择 "**文件" > 保存场景**"。

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>第5章-从 Unity 编辑器验证设备

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

现在，我们已经创建了多维数据集，可以在设备中快速完成检查了。 可以直接从 Unity 编辑器中执行此操作。

### <a name="initial-setup"></a>初始设置

1. 在开发 PC 的 Unity 中，打开 "**文件 > 生成设置**" 窗口。
2. 将**平台**更改为 "**通用 Windows 平台**"，然后单击 "**切换平台**"

### <a name="for-hololens-use-unity-remoting"></a>对于 HoloLens，使用 Unity 远程处理

1. 在 HoloLens 上，安装并运行 Windows 应用商店提供的[全息远程处理播放器](holographic-remoting-player.md)。 在设备上启动应用程序，该应用程序将进入等待状态并显示设备的 IP 地址。 记下 IP。
2. **> 全息仿真打开 > XR 的窗口**。
3. 将**仿真模式**从**None**更改为**远程到设备**。
4. 在**远程计算机**上，输入你之前记下的 HOLOLENS 的 IP 地址。
5. 单击“连接”。
6. 确保**连接状态**更改为 "**已连接**绿色"。
7. 现在，你可以在 Unity 编辑器中单击 "**播放**"。

现在，可以在设备和编辑器中查看多维数据集。 您可以暂停、检查对象和调试，就像您在编辑器中运行应用一样，因为这实质上是发生的事情，但使用视频、音频和设备输入通过网络在主机和设备之间来回传输。

### <a name="for-other-mixed-reality-supported-headsets"></a>适用于其他混合现实支持的耳机

1. 使用 USB 电缆和 HDMI 或显示器端口电缆将耳机连接到开发 PC。
2. 启动**混合现实门户**并确保已完成首次运行体验。
3. 现在，可以从 Unity 按下 "播放" 按钮。

现在，你将能够在混合现实耳机和编辑器中看到多维数据集呈现。

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>第6章-从 Visual Studio 生成并部署到设备

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

现在，我们已准备好将项目编译到 Visual Studio 并部署到我们的目标设备。

### <a name="export-to-the-visual-studio-solution"></a>导出到 Visual Studio 解决方案

1. 打开**文件 > 生成设置**"窗口。
1. 单击 "**添加打开的场景**" 添加场景。
1. 将**平台**更改为 "**通用 Windows 平台**"，然后单击 "**切换平台**"。
1. 在**通用 Windows 平台**设置 "中，确保**SDK**为**通用 10**。
1. 对于 "目标设备"，请将封闭像素的**任何设备**保留为 "显示" 或 "切换到**HoloLens**"。
1. **UWP 生成类型**应为**D3D**。
1. **UWP SDK**可以保持**最新安装的版本**。
1. 单击“生成”****。
1. 在文件资源管理器中，单击 "**新建文件夹**"，然后将文件夹命名为 **"App"**。
1. 选择**应用**文件夹后，单击 "**选择文件夹**" 按钮。
1. 当 Unity 完成生成后，将显示一个 Windows 文件资源管理器窗口。
1. 在文件资源管理器中打开**应用程序**文件夹。
1. 打开生成的 Visual Studio 解决方案（在本示例中为 MixedRealityIntroduction）

### <a name="compile-the-visual-studio-solution"></a>编译 Visual Studio 解决方案

最后，我们将编译导出的 Visual Studio 解决方案，对其进行部署，然后在设备上试用。

1. 使用 Visual Studio 中的顶部工具栏，将目标从 "**调试**" 更改为 "**发布**"，将 "从**ARM** " 更改为 " **X86**"。

有关部署到设备与模拟器的说明有所不同。 按照与你的设置相匹配的说明进行操作。

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>通过 Wi-fi 部署到混合现实设备

1. 单击 "**本地计算机**" 按钮旁边的箭头，将部署目标更改为 "**远程计算机**"。
2. 输入混合现实设备的 IP 地址，并将 "**身份验证模式**" 更改为 "适用于 HoloLens 的通用（未加密的协议）" 和 " **Windows** " 作为其他设备。
3. 单击 "**调试" > "开始（不调试**）"。

**对于 HoloLens**，如果这是首次部署到设备，则需要[使用 Visual Studio](using-visual-studio.md)进行配对。

### <a name="deploy-to-mixed-reality-device-over-usb"></a>通过 USB 部署到混合现实设备

确保设备通过 USB 电缆接通电源。

1. **对于 HoloLens**，单击 "**本地计算机**" 按钮旁边的箭头，然后将 "部署目标" 更改为 "**设备**"。
2. **对于连接到电脑的封闭像素设备**，请将设置保留为 "本地计算机"。 确保已运行**混合现实门户**。
3. 单击 "**调试" > "开始（不调试**）"。

### <a name="deploy-to-emulator"></a>部署到模拟器

1. 单击 "**设备**" 按钮旁边的箭头，并从下拉菜单中选择 " **HoloLens 模拟器**"。
2. 单击 "**调试" > "开始（不调试**）"。

### <a name="try-out-your-app"></a>试用你的应用

部署你的应用后，请尝试四处移动该多维数据集，并观察它是否在世界各地。

## <a name="see-also"></a>请参阅

* [Unity 开发概述](unity-development-overview.md)
* [使用 Unity 和 Visual Studio 的最佳做法](best-practices-for-working-with-unity-and-visual-studio.md)
* [MR 基础知识 101](holograms-101.md)
* [MR 基础知识 101E](holograms-101e.md)
