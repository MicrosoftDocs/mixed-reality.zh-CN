---
title: 应用视图
description: 两种类型的 Windows Mixed Reality 应用中的视图是沉浸式视图和二维视图。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式视图中，2D 视图中，静态图像，应用程序
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592994"
---
# <a name="app-views"></a>应用视图

Windows 应用程序可以包含两种类型的视图**沉浸式视图**并**二维视图**。 应用可以在其不同的沉浸式视图和作为窗口或作为一台平板电脑耳机的监视器上显示其二维视图的二维视图之间切换。 具有至少一个沉浸式视图的应用分为**混合现实应用**。 永远不会有一个令人着迷的视图的应用**2D 应用**。

## <a name="immersive-views"></a>沉浸式视图

沉浸式视图使您的应用程序能够在周围世界中创建全息或可访问这个虚拟环境中的用户。 当应用在沉浸式视图中绘制时, 没有任何其他应用在同一时间绘制&mdash;全息从多个应用程序不是组合在一起。 通过不断调整的透视你[的应用呈现](rendering.md)其场景以匹配用户的头移动，您的应用程序可以呈现[世界锁定](coordinate-systems.md)全息保留在现实中的固定点世界中，也可以呈现的虚拟环境中，当用户移动时在其中保存其位置。

![在沉浸式视图中，当全息可放在周围世界。](images/designoverview.jpg)<br>
*可以在沉浸式视图中，当在周围世界中放置全息*

上[HoloLens](hololens-hardware-details.md)，您的应用程序呈现其全息基于用户的实际环境。 上[Windows Mixed Reality 沉浸式头戴式](immersive-headset-hardware-details.md)、 用户看不到现实生活中，并使您的应用程序必须呈现的所有内容，用户将看到。

[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)（包括开始菜单和全息已周围环境） 不会呈现在沉浸式每页中显示。 HoloLens，在将 cortana，呼叫中继的沉浸式视图显示时出现的任何系统通知和用户可以使用语音输入响应。

在沉浸式视图中，你的应用程序还负责处理所有的输入。 Windows Mixed Reality 中的输入组成[注视](gaze.md)，[手势](gestures.md)(仅 HoloLens)[语音](voice-input.md)并[动作控制器](motion-controllers.md)（沉浸式耳机仅）。

## <a name="2d-views"></a>二维视图

![多个二维视图布局周围的主 Windows Mixed Reality](images/teleportation-640px.png)<br>
*使用二维视图的多个应用程序周围将 Windows Mixed Reality 主页*

带有二维视图的应用程序显示在[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)（有时称为"shell"） 作为虚拟的静态图像，以及应用启动器和用户在他们的工作放入了其他全息呈现。 用户可以调整移动和缩放，此静态图像，但它仍然保持固定的分辨率，而不考虑其大小。 如果你的应用的第一个视图是二维视图，2D 内容将填充相同的静态图像用于启动该应用程序。

在桌面耳机，可以运行任何桌面监视器现在运行的通用 Windows 平台 (UWP) 应用。 这些应用目前已呈现 2D 视图，并在启动时的用户的世界中一台平板电脑上会自动显示其内容。 2D UWP 应用可以针对**Windows.Universal**设备系列运行这两个桌面耳机和 HoloLens 为平板电脑上。

一种密钥使用二维视图是显示文本的输入窗体，可以使系统键盘的使用情况。 因为 shell 之上的沉浸式视图不能呈现，该应用程序必须切换到用于显示系统键盘的二维视图。 想要接受文本输入的应用可以切换到包含在文本框中的二维视图。 该文本框有焦点，则系统会显示系统键盘，这样就允许用户输入文本。

请注意，在桌面 PC 上，应用可以有在桌面监视器上并附加耳机的 2D 视图。 例如，您可以在桌面监视器使用其主 2D 视图来查找全方位的视频上浏览边缘。 当您播放该视频时，边缘将启动耳机，若要显示的沉浸式视频内容内的辅助沉浸式视图。

## <a name="see-also"></a>请参阅

* [应用程序模型](app-model.md)
* [更新适用于混合现实的 2D UWP 应用](building-2d-apps.md)
* [获取 HolographicSpace](getting-a-holographicspace.md)
* [导航 Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)
* [类型的混合的现实应用](types-of-mixed-reality-apps.md)
