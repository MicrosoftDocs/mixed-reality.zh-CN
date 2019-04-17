---
title: MR 基础知识 100-开始使用 Unity
description: 了解如何创建第一个基本的混合的现实"你好 world"应用程序。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合现实，Windows Mixed Reality 开始 HoloLens，令人着迷，vr，先生，，全息图，学院，教程
ms.openlocfilehash: 1f4a5490383671fba694b386015ff6742d37241b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590106"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>MR 基础知识 100:开始使用 Unity

本教程将引导你完成创建使用 Unity 构建的基本混合的现实应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>MR 基础知识 100:开始使用 Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>先决条件

* 使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。

## <a name="chapter-1---create-a-new-project"></a>第 1 章-创建新项目

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

若要生成使用 Unity 应用，首先需要创建一个项目。 此项目划分为几个文件夹，其中最重要的是你的资产文件夹。 这是包含从 Maya、 最大影院 4d 或 Photoshop，使用 Visual Studio 或你最喜欢的代码编辑器中，创建的所有代码等的数字内容创建工具导入的所有资产的文件夹和任意数量的 Unity 创建你的内容文件撰写场景动画和在编辑器中的其他 Unity 资产类型。

若要生成和部署 UWP 应用，Unity 可以导出为 Visual Studio 解决方案将包含所有必需的资产和代码文件的项目。

1. 启动 Unity
2. 选择**新**
3. 输入项目名称 （例如"MixedRealityIntroduction")
4. 输入用于保存你的项目的位置
5. 请确保**3D**切换处于选中状态
6. 选择**创建项目**

恭喜，您将所有安装程序以立即开始使用混合的现实自定义设置。

## <a name="chapter-2---setup-the-camera"></a>第 2 章-安装照相机

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity Main Camera 处理跟踪的头节点和立体呈现。 有一些更改以进行到 Main Camera 以用于混合现实。
1. 选择文件 > 新的场景

首先，它将是更轻松地布置您的应用程序，如果您想象为用户的起始位置 (**X**:0， **Y**:0， **Z**:0). 因为 Main Camera 正在跟踪的用户的头移动，可以通过设置 Main Camera 的起始位置设置用户的起始位置。
1. 选择**Main Camera**中**层次结构**面板
2. 在中**Inspector**面板中，找到**转换**组件，并更改**位置**从 (**X**:0， **Y**:1， **Z**:-10) 到 (**X**:0， **Y**:0， **Z**:0)

其次，默认照相机背景需要思考一下。

**对于 HoloLens 应用程序**，实际应显示隐藏的所有内容照相机呈现时，不 Skybox 纹理。
1. 与**Main Camera**仍然中选择**层次结构**面板中，找到**照相机**组件**检查器**面板和更改**清除标志**下拉列表从**Skybox**到**纯色**。
2. 选择**背景**颜色选取器和更改**RGBA**值到 （0，0，0，0）

**对于混合的现实应用程序针对沉浸式耳机**，我们可以使用 Unity 提供了默认 Skybox 纹理。
1. 与**Main Camera**仍然中选择**层次结构**面板中，找到**照相机**组件**检查器**面板和保留**清除标志**下拉列表中**Skybox**。

第三，让我们考虑在 Unity 中的剪辑近视且阻止对象被呈现太靠近用户的眼睛用户接近对象或对象接近用户。

**对于 HoloLens 应用程序**，几乎剪裁平面可设置为[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 计量。
1. 与**Main Camera**仍然中选择**层次结构**面板中，找到**照相机**组件**检查器**面板和更改**附近剪裁平面**字段从默认**0.3**到建议 HoloLens **0.85**。

**对于混合的现实应用程序针对沉浸式耳机**，我们可以使用 Unity 提供的默认设置。
1. 与**Main Camera**仍然中选择**层次结构**面板中，找到**照相机**组件**检查器**面板和保留**附近剪裁平面**字段为默认值**0.3**。

最后，让我们到目前为止保存我们的进度。 若要保存场景更改，请选择**文件 > 场景另存为**，命名该场景**Main**，然后选择**保存**。

## <a name="chapter-3---setup-the-project-settings"></a>第 3 章-安装程序项目设置

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

在本章中，我们将帮助我们一些 Unity 项目设置目标用于开发的 Windows 全息版 SDK。 我们还将为我们的应用程序设置一些质量设置。 最后，我们将确保我们生成目标设置为 Windows 应用商店。

### <a name="unity-performance-and-quality-settings"></a>Unity 的性能和质量设置

**HoloLens 的 unity 质量设置**

![HoloLens 的 unity 质量设置](images/qualitysettings.png) 

由于维护在 HoloLens 上的高帧速率是很重要，我们需要的最快的性能优化的质量设置。 有关更多详细性能信息[Unity 的性能建议](performance-recommendations-for-unity.md)。
1. 选择**编辑 > 项目设置 > 质量**
2. 选择**下拉列表中**下**Windows 应用商店**徽标，然后选择**非常低**。 你将了解中的 Windows 应用商店列和最快的行的框为绿色时正确地应用设置。

**混合的现实针对的应用程序到封闭的像素显示**，可以将质量设置保留到其默认值。

### <a name="target-windows-10-sdk"></a>面向 Windows 10 SDK

**目标 Windows 全息版 SDK**

![目标 Windows 全息版 SDK](images/xrsettings.png) 

我们需要让 Unity 知道我们尝试导出该应用应创建[沉浸式视图](app-views.md)而不是二维视图。 为此，我们启用上 Unity 虚拟现实支持面向 Windows 10 SDK。
1. 转到**编辑 > 项目设置 > 播放机**。
2. 在中**检查器面板**对于播放机设置，选择**Windows 应用商店**图标。
3. 展开**XR 设置**组。
4. 在中**呈现**部分中，选择**受支持的虚拟现实**复选框以添加新**虚拟现实 Sdk**列表。
5. 确认**Windows Mixed Reality**出现在列表中。 如果没有，请选择**+** 按钮在列表的底部，然后选择**Windows Mixed Reality**。

>[!NOTE]
>如果没有看到**Windows 应用商店**图标，仔细检查以确保选择 Windows 应用商店.NET 脚本编写后端之前安装。 否则，可能需要使用正确的 Windows 安装重新安装 Unity。

**验证.NET 配置**

![验证.NET 配置](images/configoptions-375px.png)

1. 转到**编辑 > 项目设置 > 播放机**（你可能仍需要这从上一步）。
2. 在中**检查器面板**对于播放机设置，选择**Windows 应用商店**图标。
3. 在中**其他设置**配置部分中，请确保**脚本编写后端**设置为 **.NET**

获取应用的所有项目设置的太好了作业。 接下来，让我们添加一张全息图 ！

## <a name="chapter-4---create-a-cube"></a>章 4-创建多维数据集

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

在 Unity 项目中创建多维数据集就像在 Unity 中创建任何其他对象。 将用户的多维数据集非常简单，因为 Unity 的坐标系统映射到实际的其中一个指示器在 Unity 中是大约一米现实世界中。
1. 中的左上角**层次结构**面板中，选择**创建**下拉列表中选择**三维对象 > 多维数据集**。
2. 选择新建**多维数据集**中**层次结构**面板
3. 在中**Inspector**查找**转换**组件，并更改**位置**到 (**X**:0， **Y**:0， **Z**:2). *此选项会将该多维数据集 2 米定位用户的起始位置的前面。*
4. 在中**转换**组件，更改**旋转**到 (**X**:45 **Y**:45 **Z**:45） 和更改**规模**到 (**X**:0.25， **Y**:0.25， **Z**:0.25). *这会缩放至 0.25 米多维数据集。*
5. 若要保存场景更改，请选择**文件 > 保存场景**。

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>章节 5-验证在设备上从 Unity 编辑器

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

现在，我们创建了我们的多维数据集，就可以执行一个快速检查设备中。 你可以直接从 Unity 编辑器中。

### <a name="initial-setup"></a>初始设置
1. 在您的开发 PC 上，在 Unity 中，打开**文件 > 生成设置**窗口。
2. 更改**平台**到**通用 Windows 平台**单击**交换机平台**

### <a name="for-hololens-use-unity-remoting"></a>对于 HoloLens 使用 Unity 远程处理
1. 在你 HoloLens 上安装并运行[Holographic 远程处理的播放机](holographic-remoting-player.md)，可从 Windows 应用商店。 启动应用程序在设备上，并且它将进入等待状态，并显示设备的 IP 地址。 请记下 IP。
2. 打开**窗口 > XR > Holographic 仿真**。
3. 更改**仿真模式**从**None**到**远程连接到设备**。
4. 在中**远程计算机**，输入前面记下你 HoloLens 的 IP 地址。
5. 单击“连接”。
6. 请确保**连接状态**更改为绿色**已连接**。
7. 现在，你现在可以单击**播放**Unity 编辑器中。

现在，你将能够看到在设备和在编辑器中的多维数据集。 可以暂停、 检查对象，并调试就像在编辑器中，运行应用，因为这实质上是发生什么情况，但与视频、 音频和通过网络在主机计算机和设备之间来回传输设备输入。

### <a name="for-other-mixed-reality-supported-headsets"></a>对于其他混合现实支持耳机

1. 将耳机连接到开发电脑使用 USB 电缆和 HDMI 或显示端口电缆。
2. 启动**混合现实门户**，并确保已完成第一次运行的体验。
3. 从 Unity 中，现在可以按播放按钮。

现在，您将能够看到在混合的现实耳机，并在编辑器中的多维数据集呈现。

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>第 6-章生成，并从 Visual Studio 部署到设备

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

现在我们就可以编译到 Visual Studio 项目并将其部署到我们的目标设备。

### <a name="export-to-the-visual-studio-solution"></a>将导出到 Visual Studio 解决方案
1.  打开**文件 > 生成设置**窗口。
2.  单击**添加打开场景**添加场景。
3.  更改**平台**到**通用 Windows 平台**然后单击**切换平台**。
4.  在中**Windows 应用商店**确保设置，请**SDK**是**通用 10**。
5.  对于目标设备，请保留**任一设备**封闭的像素显示或切换到**HoloLens**。
6.  **UWP 生成类型**应**D3D**。
7.  **UWP SDK**无法将其保留为**最新安装**。
8.  检查**UnityC#项目**在调试下。
9.  单击“生成” 。
10. 在文件资源管理器，单击**新文件夹**，然后将文件夹 **"应用"**。
11. 与**应用程序**文件夹选择，单击**选择文件夹**按钮。
12. 当完成 Unity 构建，将出现一个 Windows 文件资源管理器窗口。
13. 打开**应用**文件夹在文件资源管理器。
14. 打开生成的 Visual Studio 解决方案 (在此示例中 MixedRealityIntroduction.sln)

### <a name="compile-the-visual-studio-solution"></a>编译的 Visual Studio 解决方案

最后，我们将编译导出 Visual Studio 解决方案，部署方式，并在设备上进行试用。
1. 在 Visual Studio 中，使用顶部的工具栏更改从目标**调试**到**发行**来回**ARM**到**X86**。

对于部署到仿真程序与设备不同的说明。 按照与你的设置相匹配的说明。

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>通过 Wi-fi 将部署到混合的现实设备
1. 旁边的箭头上单击**本地计算机**按钮，然后更改到部署目标**远程计算机**。
2. 输入你的混合的现实设备的 IP 地址并将更改**身份验证模式**为通用 （未加密的协议） 的 HoloLens 和**Windows**为其他设备。
3. 单击**调试 > 启动但不调试**。

**对于 HoloLens**，如果这是首次部署到你的设备，你将需要对[使用 Visual Studio](using-visual-studio.md)。

### <a name="deploy-to-mixed-reality-device-over-usb"></a>通过 USB 将部署到混合的现实设备

请确保在通过 USB 电缆插入您的设备。
1. **对于 HoloLens**，单击旁边的箭头**本地计算机**按钮，并更改部署到目标**设备**。
2. **针对连接到您的 PC 的封闭的像素设备**，保留到本地计算机的设置。 请确保您具有**混合现实门户**运行。
3. 单击**调试 > 启动但不调试**。

### <a name="deploy-to-emulator"></a>将部署到仿真程序
1. 旁边的箭头上单击**设备**按钮，并从下拉列表中，选择**HoloLens 模拟器**。
2. 单击**调试 > 启动但不调试**。

### <a name="try-out-your-app"></a>试用您的应用程序

现在，部署您的应用程序，尝试移动各地多维数据集并观察它保持在准备好世界中。

## <a name="see-also"></a>请参阅
* [Unity 开发概述](unity-development-overview.md)
* [使用 Unity 和 Visual Studio 的最佳实践](best-practices-for-working-with-unity-and-visual-studio.md)
* [MR 基础知识 101](holograms-101.md)
* [MR 基础知识 101E](holograms-101e.md)
