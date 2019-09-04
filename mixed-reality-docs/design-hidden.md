---
layout: LandingPage
title: 开始设计和原型制作
description: 我已准备好创建内容。 了解开始设计和原型制作所需的基本概念。
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 发现, 分发, 索引, 登陆页, 设计, 开发, 教程, 示例应用, 基础知识, 案例研究, 资源, HoloLens 操作指南, 开源项目
ms.openlocfilehash: 3efb411425d18a8f50a209b69b00bfa038d594f1
ms.sourcegitcommit: 183b6248807f600fe7d83daa13a6fe0b0f0dc846
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2019
ms.locfileid: "70148010"
---
# <a name="start-designing-and-prototyping"></a>开始设计和原型制作


![构建基块](images/text_in_unity_viewingangle.jpg)

## <a name="what-are-the-core-concepts-of-an-experience"></a>体验的核心概念有哪些？

### <a name="keep-the-user-comfortable---comfortcomfortmd"></a>[使用户舒适 -（舒适）](comfort.md)
为了确保头戴式显示器的舒适度最佳，设计人员和开发人员务必需要以一种模拟这些提示如何在自然世界中运行的方式来创建和展示内容。

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frameholographic-framemd"></a>[考虑用户如何看到世界 -（全息框）](holographic-frame.md)
用户通过其头戴显示设备支持的矩形视区来看到混合现实的世界。 在 HoloLens 上，此矩形区域称为全息框，它可让用户看到覆盖在他们周围现实世界上的数字内容。

<br>

### <a name="making-holographic-objects-feel-real---spatial-mappingspatial-mappingmd"></a>[使全息对象感觉真实 -（空间映射）](spatial-mapping.md)
利用空间映射，可以将对象放置在真实的图面上。 这有助于在用户的世界中锚定对象，并利用真实世界的深度提示。

<br>

### <a name="suggesting-the-scale-of-an-object---scalescalemd"></a>[建议对象的比例 -（比例）](scale.md)
如果要显示看起来十分逼真的全息形式的内容，其关键是尽可能真实地模拟现实世界的视觉统计数据。 这意味着将尽可能多的、可以帮助我们（在现实世界中）了解对象的位置、大小及其组成部分的视觉提示整合在一起。

<br>

### <a name="clear-and-readable-typographytypographymd"></a>[清晰且易懂的版式](typography.md)
就像2D 屏幕上的版式一样，目标应清晰且易懂。 由于混合现实有三个维度，文本和整体用户体验甚至可能会受到更大影响。

<br>

### <a name="color-light-and-materialscolor-light-and-materialsmd"></a>[颜色、光线和材料](color,-light-and-materials.md)
为混合现实设计内容需要认真考虑在你的体验中使用的每个视觉资产的颜色、照明和材料。


<br>

---



![交互设计因素](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>要考虑的交互设计因素


### <a name="expanding-the-design-process-for-mixed-realitycase-study-expanding-the-design-process-for-mixed-realitymd"></a>[扩展混合现实的设计过程](case-study-expanding-the-design-process-for-mixed-reality.md)
随着 Microsoft 在 2016 年向热切的开发人员推出了 HoloLens，该团队已与 Microsoft 内部和外部的工作室共同合作来打造该设备的投产体验。 这些团队边做边学，在混合现实设计的新领域中寻找机会和挑战。

<br>

### <a name="types-of-mixed-reality-appstypes-of-mixed-reality-appsmd"></a>[混合现实应用的类型](types-of-mixed-reality-apps.md)
为 Windows Mixed Reality 开发应用程序的一个优点是，该平台可以支持多种体验。 从完全沉浸式的虚拟环境到用户当前环境中的光线信息分层，Windows Mixed Reality 提供了一组强大的工具，可将任何体验引入到生活中。

<br>

### <a name="choose-an-interaction-model-for-your-customerinteraction-fundamentalsmd"></a>[为客户选择交互模型](interaction-fundamentals.md)
实现简单的本能交互这一理念贯穿整个混合现实平台。 我们采取了三个步骤来确保应用程序设计人员和开发人员能够为其客户提供简单直观的交互。

<br>

### <a name="hands-and-motion-controllershands-and-toolsmd"></a>[手和运动控制器](hands-and-tools.md)
就像2D 屏幕上的版式一样，目标应清晰且易懂。 由于混合现实有三个维度，文本和整体用户体验甚至可能会受到更大影响。

<br>

### <a name="voice-commandingvoice-designmd"></a>[语音命令](voice-design.md)
使用语音命令时，凝视通常用作定位机制，无论是充当指针（“选择”）还是将命令定向到应用程序（“看到它，说出来”），都是如此。

<br>

### <a name="leveraging-the-users-eye-gazeeye-trackingmd"></a>[利用用户的眼睛凝视](eye-tracking.md)
HoloLens 2 为开发人员提供了使用用户所注视对象的相关信息的功能，将全息体验中的环境和人类理解能力提高到了一个新境界。


<br>


---

## <a name="choose-a-prototyping-option"></a>选择原型制作选项  





:::row:::
    :::column:::
        <img alt="Unity Logo" width="70" height="70" src="images/unity_logo.png">
         <a href="https://learn.unity.com/" target="">Learn Unity</a>
        Learn how to create interactive experiences with Unity
    :::column-end:::
        :::column:::
       <img alt="MRTK Logo" width="70" height="70" src="images/MRTK_Logo_Sq_Text.png">
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="">混合现实工具包</a> 使用混合现实工具包的空间交互和 UI 构建基块，可以通过 Unity 立即开始混合现实设计和开发
    :::column-end:::
    :::column:::
        <img alt="MRDL Logo" width="70" height="70" src="images/MRDL_Logo_Sq_Text.png">
         <a href="https://github.com/Microsoft/MRDL_Unity_PeriodicTable" target="">Mixed Reality Design Labs</a>
        Mixed Reality Design Lab's sample apps shows how to use MRTK's building blocks to create beautiful mixed reality experiences.
    :::column-end:::
    :::column:::
        <img alt="Maquette Logo" width="70" height="70" src="images/MicrosoftMaquette_logo_glow.png">
         <a href="https://www.maquette.ms/" target="">Microsoft Maquette</a>
        Design for VR. Microsoft Maquette makes spatial prototyping easy, quick, and immersive.
    :::column-end:::
:::row-end:::


<br>

---



## <a name="what-would-you-like-to-do-next"></a>接下来，你想做什么？


:::row:::
    :::column:::
       ![了解基础知识](images/icon-lightbulb.jpg)
        ### [Understand the basics](index-hidden.md)
        Get a better understanding of what defines mixed reality and how it’s being used.
    :::column-end:::
    :::column:::
        ![Install the tools](images/icon-design.jpg)
         ### [Install the tools](install-the-tools.md)
        Use the installation checklist to get the tools you need to build applications for Microsoft HoloLens and Windows Mixed Reality.
    :::column-end:::
    :::column:::
        ![Come to an event](images/icon-calendar.jpg)
         ### [Come to an event](sf-academy-events.md)
        See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.
    :::column-end:::
    :::column:::
        ![Start developing](images/icon-developer.jpg)
         ### [Start developing](development-hidden.md)
        Choose a development path based on your skill level, work style. or platform interest.
    :::column-end:::
:::row-end:::



