---
title: 本机开发概述
description: 直接使用 Windows Mixed Reality Api 构建基于 DirectX 的混合现实引擎。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全息呈现，本机，本机应用，WinRT，WinRT 应用，平台 Api，自定义引擎，中间件
ms.openlocfilehash: 5c61739ea6c90b4547c5c9927cf2129304650926
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80159991"
---
# <a name="native-development-overview"></a>本机开发概述

Windows Mixed Reality 应用程序使用以下 Api 为 HoloLens 和其他沉浸式耳机构建[混合现实](mixed-reality.md)体验：

 - [全息渲染](rendering.md)
 - [凝视](gaze-and-commit.md)
 - [姿态](gaze-and-commit.md#composite-gestures)
 - [运动控制器](motion-controllers.md)
 - [语音](voice-input.md)
 - [空间映射](spatial-mapping.md)

可以使用三维引擎（如[Unity](unity-development-overview.md)）创建混合现实应用程序。 或者，你可以通过使用 DirectX 11 或 DirectX 12 直接向 Windows Mixed Reality Api 进行编码。 如果直接利用该平台，则会实质上构建自己的中间件或框架。 Windows Api 支持在C++和C#中编写的应用程序。 如果使用C#，你的应用程序可以利用[SharpDX](https://sharpdx.org/)开源软件库。

Windows Mixed Reality 支持[两种类型的应用](app-views.md)：
* **混合现实应用程序**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)或[OpenXR api](openxr.md)将[沉浸式视图](app-views.md)呈现给填充耳机显示的用户
* 使用 DirectX、XAML 或其他框架在 Windows Mixed Reality 主页上的清单上呈现[2d 视图](app-views.md#2d-views)的**2d 应用**（UWP）

[2d 视图和沉浸式视图](app-views.md)的 DirectX 开发之间的差异主要涉及全息呈现和空间输入。 UWP 应用程序的[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 应用程序的 HWND 是必需的，并且保持基本相同。 适用于应用程序的 WinRT Api 也是如此。 但您必须使用这些 Api 的不同子集才能利用全息功能。 例如，存在和帧的存在由系统为全息应用程序管理，以便启用姿势预测帧循环。

## <a name="get-started-with-openxr"></a>OpenXR 入门

可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 上的 Windows Mixed 耳机上进行开发。  如果你无权访问耳机，则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。

若要开始为 HoloLens 2 或沉浸式 Windows Mixed Reality 耳机开发 OpenXR 应用程序，请参阅[如何开始 OpenXR 开发](openxr-getting-started.md)。

## <a name="get-started-with-winrt"></a>WinRT 入门

开始开发沉浸式应用程序：
* 对于**UWP 应用**，请[使用 Visual Studio 中的模板创建新的 UWP 项目](creating-a-holographic-directx-project.md)。 根据语言C++ 、视觉对象或视觉对象C#，在**Windows 通用** > **全息**版下查找 UWP 模板。
* 对于**Win32 应用程序**，请[从*BasicHologram* Win32 示例开始](creating-a-holographic-directx-project.md#creating-a-win32-project)。

此步骤是获取将全息呈现支持添加到现有应用程序或引擎所需的代码的好方法。 在模板中，代码和概念的显示方式与实时交互式软件的任何开发人员都非常熟悉。

以下主题介绍了向基于 DirectX 的中间件添加 Windows Mixed Reality 支持时的基本要求。

* [创建全息版 DirectX 项目](creating-a-holographic-directx-project.md)：全息应用程序模板与文档一起显示与你使用的不同之处。 还介绍了在打印头上运行时设计的设备的特殊要求。
* [获取 HolographicSpace](getting-a-holographicspace.md)：首先需要创建一个 HolographicSpace，它为应用程序提供了一个 HolographicFrame 对象的序列，这些对象表示你将呈现的每个头位置。
* [在 DirectX 中呈现](rendering-in-directx.md)：由于全息存在具有两个呈现目标，因此你必须对应用呈现的方式进行一些更改。
* [在 DirectX 中协调系统](coordinate-systems-in-directx.md)： Windows Mixed Reality 在用户浏览时了解并更新对世界的了解。 这会提供应用程序用于确定用户周围环境的空间坐标系统，其中包括空间锚和用户定义的空间阶段。

## <a name="add-mixed-reality-capabilities-and-inputs"></a>添加混合现实功能和输入

若要为沉浸式应用程序的用户提供可能的最佳体验，应支持以下关键构建基块：

* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的语音输入](voice-input-in-directx.md)
* [空间音效](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [DirectX 中的空间映射](spatial-mapping-in-directx.md)

这些是许多沉浸式应用程序所使用的其他主要功能，这些功能也会公开给 DirectX 应用程序：

* [DirectX 中的共享空间定位点](shared-spatial-anchors-in-directx.md)
* [DirectX 中的键盘、鼠标和控制器输入](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a>另请参阅
* [应用模型](app-model.md)
* [应用视图](app-views.md)
