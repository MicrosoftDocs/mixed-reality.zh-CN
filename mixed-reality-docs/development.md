---
layout: LandingPage
title: 了解工具和体系结构
description: 适用于 HoloLens 和沉浸式头戴显示设备的混合现实开发人员文档。
author: grbury
ms.author: grbury
ms.date: 04/27/2020
ms.topic: overview
ms.localizationpriority: high
keywords: 混合现实, 开发, HoloLens, unity, unreal, directx
ms.openlocfilehash: 3c874e45e555ec6defa611bd5404abbb18e6612e
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447853"
---
# <a name="learn-the-tools-and-architecture"></a>了解工具和体系结构

![抽象三维球体](images/07_Development.png)

## <a name="expand-your-design-process"></a>[扩展设计过程](case-study-expanding-the-design-process-for-mixed-reality.md)

随着 Microsoft 在 2016 年向热切的开发人员推出了 HoloLens，该团队已与 Microsoft 内部和外部的工作室共同合作来打造该设备的投产体验。 这些团队边做边学，在混合现实设计的新领域中寻找机会和挑战。 [阅读详细信息](case-study-expanding-the-design-process-for-mixed-reality.md)


<br>

---


## <a name="what-technology-path-are-you-interested-in"></a>你对哪一技术路径感兴趣？ 


:::row:::   
    :::column:::    
       [![Unity](images/unity_logo.png)](development.md#unity)<br>
        **[Unity](development.md#unity)**<br>   
        使用 Unity 构建跨平台、功能齐全的混合现实应用。
    :::column-end:::    
    :::column:::    
        [![Unreal](images/Unreal_logo.png)](development.md#unreal)<br>
        **[Unreal](development.md#unreal)**<br> 
        通过 Unreal Engine 中的生产就绪支持创造出色的混合现实体验。 
    :::column-end:::
    :::column:::    
        [![JavaScript](images/web-logo.png)](development.md#javascript)<br>
        **[JavaScript](development.md#javascript)**<br>
        JavaScript 和 WebXR 设备 API 是一种开放的规范，利用它可以在任何平台中通过浏览器来体验混合现实。    
    :::column-end:::        
    :::column:::    
        [![Native](images/VisualStudio-small_logo.png)](development.md#native)<br>
        **[Native](development.md#native)**<br> 
        直接针对 Windows Mixed Reality API 进行编码，以这种方式创建混合现实应用。 
    :::column-end:::    
:::row-end:::

<br>

---

## <a name="unity"></a>Unity


### <a name="unity-development-overview"></a>[Unity 开发概述](unity-development-overview.md)
建议你花一些时间浏览 Unity 教程。 如果你需要资产，Unity 有一个包罗万象的资产商店。 

<br>

### <a name="microsofts-mixed-reality-toolkit-mrtk-for-unity"></a>[适用于 Unity 的 Microsoft 混合现实工具包 (MRTK)](mrtk-getting-started.md)
适用于 Unity 的 MRTK v2 是一个面向混合现实应用程序的开源跨平台开发工具包。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。

<br>

### <a name="open-source-sample-apps-and-step-by-step-tutorials"></a>[开源示例应用和分步教程](tutorials.md)
HoloLens 2 教程旨在帮助开发人员了解用于开发混合现实应用程序的技术和最佳实践。 本教程基于混合现实工具包 2.0 (MRTK 2.0)。

<br>

### <a name="hand-interaction-examples-scene-mrtk-for-unity"></a>[用于 Unity 的手动交互示例场景 (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#open-and-run-the-handinteractionexamples-scene-in-editor)
HandInteractionExamples.unity 示例场景包含各种类型的交互和 UI 控件，可以突出显示明确表达的手动输入。
>[!NOTE]
>需要安装 MRTK Foundation 和示例 Unity 包。

### <a name="eye-tracking-examples-mrtk-for-unity"></a>[用于 Unity 的眼动跟踪示例 (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_ExamplesOverview.html)
此页面介绍如何在我们提供的 MRTK 眼动跟踪示例的基础上进行构建，以便快速完成在 MRTK 中使用眼动跟踪的入门。
>[!NOTE]
>需要安装 MRTK Foundation 和示例 Unity 包。

<br>

---

## <a name="unreal"></a>Unreal

### <a name="unreal-development-overview"></a>[Unreal 开发概述](unreal-development-overview.md)
了解如何使用 Unreal 构建混合现实应用。

<br>

### <a name="microsofts-mixed-reality-toolkit-mrtk-for-unreal"></a>[适用于 Unreal 的 Microsoft 混合现实工具包 (MRTK)](https://github.com/microsoft/MixedRealityToolkit-Unreal)
适用于 Unreal 的混合现实工具包 (MRTK-Unreal) 是一组组件，包含插件、示例和文档，旨在加快使用 Unreal Engine 开发混合现实应用程序的速度。

<br>

### <a name="open-source-sample-apps-and-a-step-by-step-tutorial"></a>[开源示例应用和分步教程](unreal-uxt-ch1.md)
这个有关 Unreal 中混合现实开发的入门教程可指导开发人员端到端地完成使用[适用于 Unreal v0.8 的 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) 创建 HoloLens 2 应用的过程。

<br>

---

## <a name="javascript"></a>JavaScript   

### <a name="javascript-development-overview"></a>[JavaScript 开发概述](javascript-development-overview.md)   
了解如何使用 JavaScript 构建适用于任何平台的混合现实应用。

<br>

---

## <a name="native"></a>本机


### <a name="native-development-overview"></a>[本机开发概述](directx-development-overview.md)
构建本机混合现实应用的最快途径。

<br>

### <a name="directx-uwp-app-templates-for-mixed-reality"></a>[用于混合现实的 DirectX UWP 应用模板](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)
开始使用 DirectX 编写混合现实应用所需的一切基本东西。

<br>

---


## <a name="what-would-you-like-to-do-next"></a>接下来，你想做什么？


:::row:::
    :::column:::
       [![了解基础知识](images/icon-lightbulb.png)](get-started-with-mr.md#understand-the-basics)<br>
        **[了解基础知识](get-started-with-mr.md#understand-the-basics)**<br>
        更好地了解是什么定义了混合现实，以及如何使用混合现实。
    :::column-end:::
    :::column:::
        [![成为创建者](images/icon-design.jpg)](design.md)<br>
         **[成为创建者](design.md)**<br>
        了解开始设计和原型制作所需的基本概念。
    :::column-end:::
    :::column:::
        [![安装工具](images/icon-developer.jpg)](install-the-tools.md)<br>
         **[安装工具](install-the-tools.md)**<br>
        使用安装清单获取为 HoloLens 和混合现实构建应用所需的工具。
    :::column-end:::
    :::column:::
        [![参加活动](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[参加活动](sf-academy-events.md)**<br>
        查看硬件并获取动手教程，以便创建第一个 HoloLens 2 应用程序。
    :::column-end:::
:::row-end:::


<br>

<br>
