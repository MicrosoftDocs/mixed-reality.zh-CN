---
layout: LandingPage
title: 开始设计和原型制作
description: 如果已做好创建方面的准备工作，请了解开始设计和原型制作所需的基本概念。
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 发现, 分发, 索引, 登陆页, 设计, 开发, 教程, 示例应用, 基础知识, 案例研究, 资源, HoloLens 操作指南, 开源项目, 核心概念, 交互
ms.openlocfilehash: 2bd2b3fef713bfe74f91714be100c7a02e46f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435729"
---
# <a name="start-designing-and-prototyping"></a>开始设计和原型制作


![核心概念](images/text_in_unity_viewingangle.jpg)

## <a name="expand-your-design-processcase-study-expanding-the-design-process-for-mixed-realitymd"></a>[扩展设计过程](case-study-expanding-the-design-process-for-mixed-reality.md)

随着 Microsoft 在 2016 年向热切的开发人员推出了 HoloLens，该团队已与 Microsoft 内部和外部的工作室共同合作来打造该设备的投产体验。 这些团队边做边学，在混合现实设计的新领域中寻找机会和挑战。 [阅读详细信息](case-study-expanding-the-design-process-for-mixed-reality.md)

<br>

---

## <a name="what-are-the-core-concepts-of-an-experience"></a>体验的核心概念有哪些？

### <a name="keep-the-user-comfortable---comfortcomfortmd"></a>[使用户舒适 -（舒适）](comfort.md)
为了确保头戴式显示器的舒适度最佳，设计人员和开发人员务必需要以一种模拟这些提示如何在自然世界中运行的方式来创建和展示内容。

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frameholographic-framemd"></a>[考虑用户如何看到世界 -（全息框）](holographic-frame.md)
用户通过其头戴显示设备支持的矩形视区来看到混合现实的世界。 在 HoloLens 上，此矩形区域称为全息框，它可让用户看到覆盖在他们周围现实世界上的数字内容。

<br>

### <a name="types-of-mixed-reality-appstypes-of-mixed-reality-appsmd"></a>[混合现实应用的类型](types-of-mixed-reality-apps.md)
针对混合现实开发应用的一个优点是，该平台可以支持多种体验。 从完全沉浸式的虚拟环境到用户当前环境中的光线信息分层，混合现实提供了一组强大的工具，可将任何体验引入到生活中。

<br>

### <a name="keeping-holograms-in-place---coordinate-systemscoordinate-systemsmd"></a>[保持全息影像的位置 -（坐标系统）](coordinate-systems.md)
混合现实应用的核心功能是能够将全息影像置于你的世界中，使之看起来和听起来就像真实的物体一样。 这涉及到将这些全息影像精确地置于世界上对用户有意义的各个位置，该位置可能是用户的物理室，也可能是你创建的某个虚拟领域。

<br>

### <a name="making-holographic-objects-feel-real---spatial-mappingspatial-mappingmd"></a>[使全息对象感觉真实 -（空间映射）](spatial-mapping.md)
利用空间映射，可以将对象放置在真实的图面上。 这有助于在用户的世界中锚定对象，并利用真实世界的深度提示。

<br>


---

<br>

![交互设计因素](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>要考虑的交互设计因素


### <a name="choose-an-interaction-model-for-your-customerinteraction-fundamentalsmd"></a>[为客户选择交互模型](interaction-fundamentals.md)
实现简单的本能交互这一理念贯穿整个混合现实平台。 我们采取了三个步骤来确保应用程序设计人员和开发人员能够为其客户提供简单直观的交互。

<br>

### <a name="hands-and-motion-controllershands-and-toolsmd"></a>[手和运动控制器](hands-and-tools.md)
用户可以直接使用单手或双手来触摸和操作全息影像，就跟对待现实世界的物体一样。 也可使用运动控制器跨很大的距离范围提供精确的交互，扩展用户的物理能力。

<br>

### <a name="directly-commanding-objects-with-voice-inputvoice-inputmd"></a>[使用语音输入直接命令对象](voice-input.md)
在 HoloLens 上，语音是重要输入形式之一。 可以通过它直接命令某个全息影像，不需使用手势。 可以将语音输入作为一种传达意图的自然方式。

<br>

### <a name="leveraging-the-users-eye-gazeeye-trackingmd"></a>[利用用户的眼睛凝视](eye-tracking.md)
HoloLens 2 为开发人员提供了使用用户所注视对象的相关信息的功能，将全息体验中的环境和人类理解能力提高到了一个新境界。

<br>

### <a name="color-light-and-materialscolor-light-and-materialsmd"></a>[颜色、光线和材料](color,-light-and-materials.md)
为混合现实设计内容需要认真考虑在你的体验中使用的每个视觉资产的颜色、照明和材料。

<br>

### <a name="suggesting-the-scale-of-an-objectscalemd"></a>[建议对象的比例](scale.md)
如果要显示看起来十分逼真的全息形式的内容，其关键是尽可能真实地模拟现实世界的视觉特征。 这意味着将尽可能多的、可以帮助我们（在现实世界中）了解对象的位置、大小及其组成部分的视觉提示整合在一起。

<br>

### <a name="clear-and-readable-typographytypographymd"></a>[清晰且易懂的版式](typography.md)
就像2D 屏幕上的版式一样，目标应清晰且易懂。 由于混合现实有三个维度，文本和整体用户体验甚至可能会受到更大影响。

<br>


---

## <a name="choose-a-prototyping-option"></a>选择原型制作选项  

:::row:::   
    :::column:::    
       [![了解 Unity](images/unity_logo.png)](https://learn.unity.com/)<br>
        **[了解 Unity](https://learn.unity.com/)**<br>
        了解如何使用 Unity 创建交互式体验。 从头至尾从实践中学习。
    :::column-end:::    
    :::column:::    
        [![混合现实工具包 (MRTK)](images/MRTK-small_logo.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[混合现实工具包 (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        使用空间交互和 UI 构建基块，通过 Unity 立即开始混合现实设计和开发。   
    :::column-end:::
    :::column:::    
        [![混合现实设计实验室](images/MRDL_logo.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[混合现实设计实验室](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        获取示例应用，这些应用会演示如何使用 MRTK 的构建基块来创建美好的混合现实体验。
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/Maquette_logo.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        为 VR 而设计。 可以使用 Microsoft Maquette 快速便捷地进行沉浸式空间原型制作。 
    :::column-end:::    
:::row-end:::

<br>

---



## <a name="what-would-you-like-to-do-next"></a>接下来，你想做什么？

:::row:::
    :::column:::
       [![了解基础知识](images/icon-lightbulb.jpg)](index.md#understand-the-basics)<br>
        **[了解基础知识](index.md#understand-the-basics)**<br>
        更好地了解是什么定义了混合现实，以及如何使用混合现实。
    :::column-end:::
    :::column:::
        [![参加活动](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[参加活动](sf-academy-events.md)**<br>
        查看硬件并获取动手教程，以便创建第一个 HoloLens 2 应用程序。
    :::column-end:::
    :::column:::
        [![安装工具](images/icon-design.jpg)](install-the-tools.md)<br>
         **[安装工具](install-the-tools.md)**<br>
        使用安装清单获取为 HoloLens 和混合现实构建应用所需的工具。
    :::column-end:::
    :::column:::
        [![开始开发](images/icon-developer.jpg)](development.md)<br>
        **[开始开发](development.md)**<br>
        根据技能水平、工作风格或平台兴趣选择开发路径。
    :::column-end:::
:::row-end:::


<br>

<br>


