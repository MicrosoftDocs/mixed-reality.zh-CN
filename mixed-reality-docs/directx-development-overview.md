---
title: DirectX 开发概述
description: 生成基于 DirectX 的混合的现实引擎直接使用 Windows 混合现实 Api。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全息呈现，本机、 本机应用，WinRT，WinRT 应用平台 Api，自定义引擎，中间件
ms.openlocfilehash: 047144cb8fcf158f74375e9ec69dca92a2a1cf01
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590320"
---
# <a name="directx-development-overview"></a>DirectX 开发概述

Windows Mixed Reality 应用使用[全息呈现](rendering.md)，[注视](gaze.md)，[手势](gestures.md)，[运动控制器](motion-controllers.md)，[语音](voice-input.md)并[空间映射](spatial-mapping.md)Api 生成[混合现实](mixed-reality.md)HoloLens 和耳机沉浸式体验。 您可以创建混合的现实应用使用 3D 引擎，如[Unity](unity-development-overview.md)，也可以使用与 DirectX 11 的 Windows 混合现实 Api。 请注意，目前不支持 DirectX 12。 如果您直接利用该平台，实质上要构建自己的中间件或框架。 Windows Api 支持在这种编写的应用C++和C#。 如果你想要使用C#，你的应用程序可以利用[SharpDX](http://sharpdx.org/)开放源代码软件库。

支持 Windows Mixed Reality[两种类型的应用](app-views.md):
* **混合现实应用**（UWP 或 Win32），可使用该技术[HolographicSpace API](getting-a-holographicspace.md)呈现[沉浸式视图](app-views.md)填充耳机显示的用户。
* **2D 应用**(UWP)，其中使用 DirectX、 XAML 或其他框架来呈现[2D 视图](app-views.md#2d-views)Windows Mixed Reality 家庭中的平板电脑上。

DirectX 开发之间的差异[2D 视图和沉浸式视图](app-views.md)是主要与全息呈现和空间的输入。 在 UWP 应用的[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 应用程序的 HWND 仍然需要和保持很大程度上是相同的 WinRT Api 可用于您的应用程序一样。 但是，使用这些 Api 的另一个子集以充分利用全息版的功能。 例如，对于全息版应用，系统管理交换链和使用 HolographicSpace API 而不是到 DXGI[呈现帧](rendering-in-directx.md)。

若要开始开发沉浸式应用程序：
* 有关**UWP 应用**，[创建新的 UWP 项目使用 Visual Studio 中的模板](creating-a-holographic-directx-project.md)。 根据你的语言，**可视化C++** 或**Visual C#** ，您将找到下的 UWP 模板**Windows 通用** >  **Holographic**。
* 有关**Win32 应用**，[创建一个新的 Win32 桌面项目](creating-a-holographic-directx-project.md#creating-a-win32-project)，然后按照上的 Win32 说明[获取 HolographicSpace](getting-a-holographicspace.md)页后，可以获取 HolographicSpace。

这是获取您需要添加到现有应用或引擎全息呈现支持代码的好办法。 代码和概念的模板中的实时交互式软件开发人员熟悉的方式呈现。

## <a name="getting-started"></a>即刻体验

以下主题讨论 Windows Mixed Reality 支持添加到基于 DirectX 的中间件的基本要求：
* [创建全息版的 DirectX 项目](creating-a-holographic-directx-project.md):与文档结合使用全息版的应用程序模板将向您习惯于，和一台设备，其设计目的函数将在您头上时引入的特殊要求之间的差异。
* [获取 HolographicSpace](getting-a-holographicspace.md):首先需要创建 HolographicSpace，这将为您的应用程序提供表示从其将呈现每个头位置的 HolographicFrame 对象的序列。
* [在 DirectX 呈现](rendering-in-directx.md):由于 holographic 交换链具有两个呈现器目标，可能需要对你的应用程序中的呈现的方式进行一些更改。
* [在 DirectX 的坐标系统](coordinate-systems-in-directx.md):Windows Mixed Reality 学习并更新其对输入到世界的理解，用户审核提供应用来推断用户的环境，包括空间的定位点和用户的定义空间阶段使用的空间坐标系统。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>添加混合的现实功能和输入

若要启用的沉浸式应用程序的用户可能的最佳体验，你将想要支持以下主要构建基块：
* [提供注视、 手势和 DirectX 中的动作控制器](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [在 DirectX 语音输入](voice-input-in-directx.md)
* [在 DirectX 空间声音](spatial-sound-in-directx.md)
* [在 DirectX 空间映射](spatial-mapping-in-directx.md)

有很多沉浸式应用程序将想要使用，还公开到 DirectX 应用程序的其他主要功能：
* [共享中 DirectX 的空间定位点](shared-spatial-anchors-in-directx.md)
* [在 DirectX 可定位照相机](locatable-camera-in-directx.md)
* [键盘、 鼠标和 DirectX 中的控制器输入](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>请参阅
* [应用程序模型](app-model.md)
* [应用程序视图](app-views.md)
