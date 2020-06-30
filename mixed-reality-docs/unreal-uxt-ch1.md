---
title: 1. 入门
description: 教程系列第 1 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 39e4e7218341dcc69eacf01f43b5e0721e76031b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720373"
---
# <a name="1-getting-started"></a>1.入门

无论你是混合现实新手还是经验丰富的专业人员，都可以使用 [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) 和 [Unreal Engine](https://www.unrealengine.com/en-US/) 开始你的体验之旅。 本系列教程将为你提供有关如何使用 [UX Tools 插件](https://github.com/microsoft/MixedReality-UXTools-Unreal)构建交互式象棋应用的分步指南，该插件是 [Unreal 混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unreal)的一部分。 该插件将帮助你通过代码、蓝图和示例将常见的 UX 功能添加到项目中。 

![在视口中结束场景](images/unreal-uxt/5-endscene.PNG)

在本系列文章结束时，你将拥有以下方面的实操经验：
* 开始新项目
* 设置混合现实
* 使用用户输入
* 添加按钮
* 在模拟器或设备上播放

如果有任何疑问，请查看我们的 [Unreal 开发概述](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)。

## <a name="prerequisites"></a>必备条件
在开始之前，请确保满足以下要求：
* Windows 10 1809 或更高版本
* Windows 10 SDK 10.0.18362.0 或更高版本
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 或更高版本
* [针对开发配置](using-visual-studio.md#enabling-developer-mode)的 Microsoft HoloLens 2 设备，或仿真器
* 具有以下工作负载的 Visual Studio 2019

### <a name="installing-visual-studio-2019"></a>安装 Visual Studio 2019
最后一步是设置 Visual Studio，如下所示：
1. 安装最新版本的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
2. 安装以下[工作负载](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads)：
    * 使用 C++ 的桌面开发
    * .NET 桌面开发
    * 通用 Windows 平台开发

3. 安装以下[组件](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components)：
    * 编译器、生成工具和运行时 > MSVC v142 - VS 2019 C++ ARM64 生成工具（最新版本）

就这么简单！ 一切准备就绪，现在可以开始象棋应用项目了。

[下一节：2.初始化你的项目和第一个应用程序](unreal-uxt-ch2.md)