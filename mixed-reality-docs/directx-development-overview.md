---
title: DirectX 开发概述
description: 直接使用 Windows Mixed Reality Api 构建基于 DirectX 的混合现实引擎。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全息呈现，本机，本机应用，WinRT，WinRT 应用，平台 Api，自定义引擎，中间件
ms.openlocfilehash: 0af73314c3c93d230ef87ed468f718f5b3e1813c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926630"
---
# <a name="directx-development-overview"></a>DirectX 开发概述


Windows Mixed Reality 应用程序使用[全息渲染](rendering.md)、[注视](gaze-and-commit.md)、[手势](gaze-and-commit.md#composite-gestures)、[运动控制器](motion-controllers.md)、[语音](voice-input.md)和[空间映射](spatial-mapping.md)api，为 HoloLens 构建[混合现实](mixed-reality.md)体验和沉浸式耳机。 可以使用三维引擎（如[Unity](unity-development-overview.md)）创建混合现实应用程序，也可以使用 directx 11 或 directx 12 直接向 Windows Mixed reality api 进行编码。 如果直接利用该平台，则会实质上构建自己的中间件或框架。 Windows Api 支持在C++和C#中编写的应用程序。 如果你选择使用C#，你的应用程序可以利用[SharpDX](https://sharpdx.org/)开源软件库。


Windows Mixed Reality 支持[两种类型的应用](app-views.md)：
* **混合现实应用程序**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)将[沉浸式视图](app-views.md)呈现给用户，以填充耳机显示。
* 使用 DirectX、XAML 或其他框架在 Windows Mixed Reality 主页上的清单上呈现[2d 视图](app-views.md#2d-views)的**2d 应用**（UWP）。


[2d 视图和沉浸式视图](app-views.md)的 DirectX 开发之间的差异主要与全息呈现和空间输入有关。 UWP 应用程序的[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 应用程序的 HWND 是必需的，并且与应用程序可使用的 WinRT api 相同。 但是，必须使用这些 Api 的不同子集才能利用全息版功能。 例如，交换链由适用于全息应用程序的系统管理。 使用 HolographicSpace API，而不是使用 DXGI 来[呈现帧](rendering-in-directx.md)。

开始开发沉浸式应用程序：
* 对于**UWP 应用**，请[使用 Visual Studio 中的模板创建新的 UWP 项目](creating-a-holographic-directx-project.md)。 根据语言、**视觉C++对象**或**视觉对象C#** ，可以在**Windows 通用** > **全息**版下查找 UWP 模板。
* 对于**Win32 应用程序**，请[从*BasicHologram* Win32 示例开始](creating-a-holographic-directx-project.md#creating-a-win32-project)。

这是一种很好的方法，可用于获取将全息呈现支持添加到现有应用程序或引擎所需的代码。 在模板中，代码和概念的显示方式与实时交互式软件的任何开发人员都非常熟悉。


## <a name="getting-started"></a>即刻体验

以下主题讨论向基于 DirectX 的中间件添加 Windows Mixed Reality 支持的基本要求：

* [创建全息版 DirectX 项目](creating-a-holographic-directx-project.md)：全息应用程序模板与文档一起显示你所使用的内容之间的差异，以及设计为运行的设备所引入的特殊要求停留在打印头上。
* [获取 HolographicSpace](getting-a-holographicspace.md)：首先需要创建一个 HolographicSpace，它将为你的应用程序提供一个 HolographicFrame 对象的序列，这些对象表示你将呈现的每个头位置。
* [在 DirectX 中呈现](rendering-in-directx.md)：由于全息交换链有两个呈现目标，因此你需要对应用程序的呈现方式进行一些更改。
* [在 DirectX 中协调系统](coordinate-systems-in-directx.md)： Windows Mixed Reality 在用户浏览时了解并更新对世界的了解。 这会提供应用程序用于确定用户周围环境的空间坐标系统，其中包括空间锚和用户定义的空间阶段。

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>添加混合现实功能和输入

若要为沉浸式应用程序的用户提供可能的最佳体验，你需要支持以下关键构建基块：

* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的语音输入](voice-input-in-directx.md)
* [空间音效](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [DirectX 中的空间映射](spatial-mapping-in-directx.md)


许多沉浸式应用程序都要使用其他重要功能，这些功能也会向 DirectX 应用程序公开：

* [DirectX 中的共享空间定位点](shared-spatial-anchors-in-directx.md)
* [DirectX 中的键盘、鼠标和控制器输入](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>另请参阅
* [应用模型](app-model.md)
* [应用视图](app-views.md)
