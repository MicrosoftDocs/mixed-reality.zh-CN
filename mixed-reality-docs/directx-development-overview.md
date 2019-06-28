---
title: DirectX 开发概述
description: 生成基于 DirectX 的混合的现实引擎直接使用 Windows 混合现实 Api。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全息呈现，本机、 本机应用，WinRT，WinRT 应用平台 Api，自定义引擎，中间件
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414385"
---
# <a name="directx-development-overview"></a>DirectX 开发概述


Windows Mixed Reality 应用程序使用[全息呈现](rendering.md)，[注视](gaze.md)，[手势](gestures.md)，[运动控制器](motion-controllers.md)， [语音](voice-input.md)，并[空间映射](spatial-mapping.md)Api 生成[混合现实](mixed-reality.md)HoloLens 和耳机沉浸式体验。 您可以创建混合的现实应用程序使用 3D 引擎，如[Unity](unity-development-overview.md)，或者也可以直接使用 DirectX 11 或 DirectX 12 Windows 混合现实 api。 如果您直接利用该平台，实质上要构建自己的中间件或框架。 Windows Api 支持在这种编写的应用程序C++和C#。 如果您选择使用C#，你的应用程序可以利用[SharpDX](http://sharpdx.org/)开放源代码软件库。


支持 Windows Mixed Reality[两种类型的应用](app-views.md):
* **混合现实应用程序**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)呈现[沉浸式视图](app-views.md)填充耳机显示的用户。
* **2D 应用**(UWP) 的使用 DirectX、 XAML 或其他框架来呈现[2D 视图](app-views.md#2d-views)Windows Mixed Reality 家庭中的平板电脑上。


DirectX 开发之间的差异[2D 视图和沉浸式视图](app-views.md)是主要与全息呈现和空间的输入。 在 UWP 应用程序[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 应用程序的 HWND 是必需的并保持很大程度上是相同的 WinRT Api 可用于应用程序一样。 但是，必须使用这些 Api 的另一个子集以充分利用全息版的功能。 例如，为 holographic appslications 的系统管理交换链。 使用 HolographicSpace API 而不是到 DXGI[呈现帧](rendering-in-directx.md)。

若要开始开发沉浸式应用程序：
* 有关**UWP 应用**，[创建新的 UWP 项目使用 Visual Studio 中的模板](creating-a-holographic-directx-project.md)。 根据你的语言，**可视化C++** 或**Visual C#** ，可以找到下的 UWP 模板**Windows 通用** >  **Holographic**。
* 有关**Win32 应用程序**，[从头*BasicHologram* Win32 示例](creating-a-holographic-directx-project.md#creating-a-win32-project)。

这是获取您需要将全息呈现支持添加到现有的应用程序或引擎的代码的好办法。 代码和概念的模板中的实时交互式软件开发人员熟悉的方式呈现。


## <a name="getting-started"></a>即刻体验

以下主题讨论 Windows Mixed Reality 支持添加到基于 DirectX 的中间件的基本要求：

* [创建全息版的 DirectX 项目](creating-a-holographic-directx-project.md):结合文档全息版的应用程序模板显示习惯于以及一台设备，其设计目的函数将在您头上时引入的特殊要求之间的差异。
* [获取 HolographicSpace](getting-a-holographicspace.md):首先需要创建将提供你的应用程序的表示从其将呈现的每个头位置的 HolographicFrame 对象序列 HolographicSpace。
* [在 DirectX 呈现](rendering-in-directx.md):由于 holographic 交换链具有两个呈现器目标，你将需要对你的应用程序中的呈现的方式进行一些更改。
* [在 DirectX 的坐标系统](coordinate-systems-in-directx.md):Windows Mixed Reality 学习并更新其了解的全球如周围将指导用户。 这提供了空间坐标系统的应用程序使用来推断用户的环境，包括空间的定位点和用户定义的空间阶段。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>添加混合的现实功能和输入

若要启用的沉浸式 appslication 用户可能的最佳体验，你将想要支持以下主要构建基块：

* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的语音输入](voice-input-in-directx.md)
* [DirectX 中的空间音效](spatial-sound-in-directx.md)
* [DirectX 中的空间映射](spatial-mapping-in-directx.md)


有很多沉浸式应用程序将想要使用还向 DirectX 应用程序公开的其他主要功能：

* [DirectX 中的共享空间定位点](shared-spatial-anchors-in-directx.md)
* [DirectX 中的可定位相机](locatable-camera-in-directx.md)
* [DirectX 中的键盘、鼠标和控制器输入](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>请参阅
* [应用模型](app-model.md)
* [应用视图](app-views.md)
