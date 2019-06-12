---
title: 导出和构建 Unity 的 Visual Studio 解决方案
description: 本文概述了从 Unity 导出你的混合的现实项目，以便您可以生成和部署在 Visual Studio 中。
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity 中，visual studio 中，导出、 构建、 部署
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592761"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>导出和构建 Unity 的 Visual Studio 解决方案

如果你不想在应用程序中使用系统键盘，我们的建议是使用*D3D*如你的应用程序会使用略有较少的内存，并可能稍快的启动时间。 如果在项目中使用 TouchScreenKeyboard API 使用系统键盘，则需要将导出为*XAML*。

## <a name="how-to-export-from-unity"></a>如何从 Unity 导出

![Unity 生成设置](images/unitybuildsettings-300px.png)<br>
*Unity 生成设置*

1. 当你准备好从 Unity 导出你的项目，打开**文件**菜单，然后选择**生成设置...**
2. 单击**添加打开场景**将场景添加到生成。
3. 在中**生成设置**对话框中，选择以下选项可将 HoloLens 的导出：
   * **平台：** *通用 Windows 平台* 并确保选择 **交换机平台** 为所选内容才会生效。
   * **SDK:**  *通用 10*。
   * **UWP 生成类型：**  *D3D*。
4. **可选**：**UnityC#项目：** 检查。

>[!NOTE]
>选中此复选框，您可以：
>* 调试 Visual Studio 远程调试器中的应用。
>* Unity 中编辑脚本C#项目时的 WinRT Api 使用 IntelliSense。

5. 从**生成设置...** 窗口中，打开**播放器设置...**
6. 选择**通用 Windows 平台的设置**选项卡。
7. 展开**XR 设置**组。
8. 在**XR 设置**部分中，选择**受支持的虚拟现实**复选框以添加新**虚拟现实设备**列出并确认 **"Windows 混合Reality"** 被列为受支持的设备。
9. 返回到**生成设置**对话框。
10. 选择**生成**。
11. 在 Windows 资源管理器对话框中显示，创建一个新文件夹来保存 Unity 的生成输出。 通常情况下，我们命名的文件夹"应用"。
12. 选择新创建的文件夹，然后单击**选择文件夹**。
13. Unity 已完成构建，Windows 资源管理器窗口将打开到项目根目录。 导航到新创建的文件夹。
14. 打开位于在此文件夹中生成 Visual Studio 解决方案文件。

## <a name="when-to-re-export-from-unity"></a>何时重新导出从 Unity

检查"C#项目"复选框时从 Unity 导出您的应用程序创建 Visual Studio 解决方案，包括你的 Unity 脚本文件。 这使您循环访问您的脚本，而无需从 Unity 重新导出。 但是，如果你想要对你不只需更改的脚本的内容的项目进行更改，你将需要从 Unity 重新导出。 有时您也需要重新导出从 Unity 的一些示例包括：
* 添加或删除资产，在项目选项卡中。
* 更改检查器选项卡中的任何值。
* 添加或从层次结构选项卡中删除对象。
* 更改任何 Unity 项目设置

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>生成和部署的 Unity 的 Visual Studio 解决方案

构建和部署应用程序的其余部分中会发生的情况[Visual Studio](using-visual-studio.md)。 您需要指定 Unity 生成配置。 Unity 的命名约定可能不同于您在 Visual Studio 中通常用于：

|  配置  |  说明 | 
|----------|----------|
|  调试  |  启用了关闭的所有优化和探查器。 用于调试脚本。 | 
|  主机  |  所有优化已都打开，并且禁用探查器。 用于将应用提交到应用商店。 | 
|  发行版本  |  所有优化已都打开，并且已启用探查器。 用于评估应用程序性能。 | 

请注意，上面的列表是将导致 Visual Studio 项目以生成所需的常见触发器的子集。 一般情况下，编辑从 Visual Studio 中的.cs 文件将不需要从在 Unity 中重新生成项目。

## <a name="troubleshooting"></a>疑难解答

如果您发现无法识别对你的.cs 文件的编辑 Visual Studio 项目中，确保"UnityC#项目"从 Unity 的生成菜单生成 VS 项目时检查。
