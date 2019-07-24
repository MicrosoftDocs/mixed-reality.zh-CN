---
title: 立即开始行动
description: 本指南概述了开始和运行混合现实开发的最快方法。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 入门, 基础知识, HoloLens, 沉浸式耳机, ar, vr, unity, visual studio, 快速入门, 如何
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873962"
---
# <a name="get-started"></a>立即开始行动

欢迎使用混合现实发展世界! 如果你不熟悉 MR, 本指南将使你的中心尽快启动并运行。 我们将帮助你将电脑设置为进行开发, 使你的设备准备就绪, 并安装可加快 MR 开发过程的工具。 

## <a name="intro-to-mixed-reality"></a>混合现实简介

你可能会遇到 "mixed reality" 的一些问题, 以及它是如何与扩充现实 (AR) 和虚拟现实 (VR) 相关的。 简而言之, 混合现实是将物理世界与数字世界混合起来, 因此, 这是一项广泛的功能, 其中包括所有内容, 从增加的现实到现实世界, 到虚拟现实 (真实世界几乎完全一样)由数字替换。 

![支持 HoloLens 和沉浸式 (VR) 耳机的混合现实应用的示例](images/mr-island.png)<br>
*混合现实应用可支持 HoloLens 和沉浸式 (VR) 耳机*

我们将 Windows Mixed Reality 创建为单一开发平台和一组可涵盖 MR 系列的工具, 并且我们目前支持两种涵盖相同色谱的设备类型:[Microsoft HoloLens](https://www.microsoft.com/hololens), 世界上第一个独立的全息耳机, [Windows Mixed Reality 沉浸式耳机和运动控制器](https://www.microsoft.com/windows/windows-mixed-reality), 它们连接到 PC 以获得强大的虚拟现实体验。 您可以查看 "混合现实" 是什么？(如果感兴趣, 请详细了解相关信息。

## <a name="choose-your-development-path"></a>选择开发路径

开发混合现实应用程序的最简单方法是使用[Unity](https://unity3d.com), 这是一个功能强大的常用中间件工具, 通常用于游戏开发。 如果要使用自定义引擎, 还可以[针对 DirectX 进行构建](directx-development-overview.md), 但大多数 MR 开发人员将 Unity 用于其游戏和应用。 使用 Unity, 你将能够创建面向 HoloLens、沉浸式 (VR) 耳机或两者的混合现实应用!

## <a name="prepare-your-pc-and-devices-for-development"></a>准备 PC 和设备进行开发

无论是要构建面向 HoloLens、沉浸式 (VR) 耳机还是同时使用这两者的混合现实应用, 都将使用一组常用的工具和 Api。 还需要确保您的 PC 的功能足以满足您的开发需要。 

>[!NOTE]
>可以在 "[安装工具](install-the-tools.md)" 一文中找到有关开发 PC 规格、支持的每个软件工具的版本的建议、每个软件工具的相关设置或配置说明。 安装以下工具之前, 请查看此文章。

要安装的工具:
* [Unity](https://store.unity.com/download)
* [Visual Studio (适用于 Windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [适用于 Unity 的混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

还需要将[目标设备置于开发人员模式并配置 Visual Studio, 以便将应用程序部署到目标设备](using-visual-studio.md)。

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>有关 Unity 混合现实工具包的注释

![Unity 的 MRTK](images/mrtkandunity.png)<br>

***YOYO, 请将其充实, 告诉每个人为什么 MRTK 是如此惊人的东西, 并且它在:)***

混合现实工具包是一个脚本和组件的集合, 旨在加速开发面向 Microsoft HoloLens 和 Windows Mixed Reality 耳机的应用程序。 该项目旨在降低创建混合现实应用程序的门槛，并在我们共同成长的过程中回馈社区。

## <a name="start-your-first-mr-project"></a>开始第一位 MR 项目

现在你的电脑和设备已设置完毕, 你可以在 Unity 中创建第一个混合现实项目。 遵循我们的第一位 mr 学院课程[, 先生/女士 100:Unity](holograms-100.md)入门后, 最终你将在混合现实耳机中启动并运行多维数据集。

![混合现实 Unity 项目中的多维数据集的屏幕截图](images/mr-cube.PNG)<br>
*Unity 中的第一个混合现实项目-hello world!*

## <a name="learn-more-and-get-help"></a>了解详细信息并获得帮助

现在, 你已成功创建了第一个 MR 项目, 你可能会有更多的需求! 下面是一些应帮助的资源:
* [混合现实开发人员文档](mixed-reality.md)-您已经在这里, 但还有更多的内容需要查看, 包括技术文档、设计指南、示例项目和案例研究。
* [混合现实教程](tutorials.md)-按照介绍设置项目、实现核心 MR 构建块 (将 Azure 云服务集成到 MR 应用) 的所有内容的教程进行操作。
* [了解 unity](https://unity3d.com/learn) -unity 的网站在学习的每个阶段为创建者提供教程、项目和实时培训会话。

你还可以从这些强大的社区资源获取帮助:
* [混合现实开发人员论坛](https://forums.hololens.com/)-适用于混合现实开发人员提出和回答问题的官方论坛, 并直接阅读 MICROSOFT 的 MR 开发新闻。
* [HoloDevelopers 宽延时间通道](https://holodevelopersslack.azurewebsites.net/)-最稳健、更丰富的外部混合现实开发渠道;此处的开发人员是一种非常丰富的知识。
* [Unity 论坛](https://forum.unity3d.com/)-unity 的官方论坛。
