---
title: 导出和生成 Unity Visual Studio 解决方案
description: 本文概述如何从 Unity 导出混合现实项目，以便可以在 Visual Studio 中生成和部署。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity，visual studio，导出，生成，部署
ms.openlocfilehash: 752a9dd002d27d24d9b80a1a97cb07a44237b9e0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435562"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>导出和生成 Unity Visual Studio 解决方案

如果你不打算在应用程序中使用系统键盘，我们建议使用*D3D* ，因为你的应用程序将使用略微少的内存，并且启动时间更快。 如果在项目中使用 TouchScreenKeyboard API 来使用系统键盘，则需要导出为*XAML*。

## <a name="how-to-export-from-unity"></a>如何从 Unity 导出

![Unity 生成设置](images/unitybuildsettings-300px.png)<br>
*Unity 生成设置*

1. 如果已准备好从 Unity 导出项目，请打开 "**文件**" 菜单，然后选择 "**生成设置 ...** "
2. 单击 "**添加打开的场景**"，将场景添加到生成中。
3. 在 "**生成设置**" 对话框中，选择以下要为 HoloLens 导出的选项：
   * **平台：** *通用 Windows 平台*，并确保选择 "**切换平台**" 以使选择生效。
   * **SDK：** *通用 10*。
   * **UWP 生成类型：** *D3D*。
4. **可选**： **Unity C#项目：** 已选中。

>[!NOTE]
>选中此框后，您可以：
>* 在 Visual Studio 远程调试器中调试你的应用程序。
>* 使用 IntelliSense for WinRT Api C#时编辑 Unity 项目中的脚本。

5. 从 "**生成设置 ...** " 窗口中，打开 "**播放机设置 ...** "
6. 选择通用 Windows 平台 "选项卡的"**设置**"。
7. 展开 " **XR 设置**" 组。
8. 在 " **XR 设置**" 部分中，选中 "**受支持的虚拟现实**" 复选框，以添加新的**虚拟现实设备**列表，并确认 **"Windows Mixed Reality"** 列为受支持的设备。
9. 返回到 "**生成设置**" 对话框。
10. 选择 "**生成**"。
11. 在出现的 "Windows 资源管理器" 对话框中，创建一个新文件夹来保存 Unity 的生成输出。 通常，将文件夹命名为 "App"。
12. 选择新创建的文件夹，然后单击 "**选择文件夹**"。
13. Unity 完成生成后，将打开项目根目录的 Windows 资源管理器窗口。 导航到新创建的文件夹。
14. 打开位于此文件夹中的生成的 Visual Studio 解决方案文件。

## <a name="when-to-re-export-from-unity"></a>何时从 Unity 重新导出

在从 UnityC#导出应用程序时选中 "项目" 复选框会创建一个包含所有 Unity 脚本文件的 Visual Studio 解决方案。 这允许您在不从 Unity 重新导出的情况下循环访问您的脚本。 但是，如果要更改不只是更改脚本内容的项目，则需要从 Unity 重新导出。 需要从 Unity 重新导出的一些时间示例如下：
* 您可以在 "项目" 选项卡中添加或删除资产。
* 您可以在 "检查器" 选项卡中更改任何值。
* 您可以在 "层次结构" 选项卡中添加或删除对象。
* 更改任何 Unity 项目设置

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>生成和部署 Unity Visual Studio 解决方案

在[Visual Studio](using-visual-studio.md)中生成和部署应用程序的其余部分。 你将需要指定 Unity 生成配置。 Unity 的命名约定可能不同于 Visual Studio 中通常使用的内容：

|  配置  |  说明 | 
|----------|----------|
|  调试  |  禁用所有优化，并启用探查器。 用于调试脚本。 | 
|  主机  |  启用所有优化并禁用探查器。 用于将应用提交到应用商店。 | 
|  发布版本  |  启用所有优化，并启用探查器。 用于评估应用程序性能。 | 

请注意，上面的列表是常见触发器的一个子集，将导致需要生成 Visual Studio 项目。 通常，在 Visual Studio 中编辑 .cs 文件不需要从 Unity 内重新生成项目。

## <a name="troubleshooting"></a>“疑难解答”

如果你发现你的 Visual Studio 项目中未识别对 .cs 文件的编辑，请确保在从 Unity 的 " C#生成" 菜单生成 VS 项目时选中 "Unity 项目"。
