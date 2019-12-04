---
title: 本能交互
description: 了解简单本能交互的理念，这一理念贯穿整个混合现实平台。
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 凝视, 设定凝视目标, 交互, 设计, hololens, MMR, 多模式
ms.openlocfilehash: 6b54d6e844c1b501a0835fc3a48deb4932ba551d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539721"
---
# <a name="introducing-instinctual-interactions"></a>本能交互简介

![用手进行远操作](images/04_InteractionFundamentals.png)

实现简单的本能交互这一理念贯穿整个混合现实 (MR) 平台。 我们采取了三个步骤来确保应用程序设计人员和开发人员能够为其客户提供简单直观的交互。 

首先，确保将我们的传感器和输入技术（包括手部跟踪、眼动跟踪和自然语言输入）融入无缝多模式交互模型。  
基于在多模框架中的研究、设计和开发，而不是单个输入，是建立本能体验的关键所在。

其次，我们已认识到，许多开发人员以多种 HoloLens 设备（例如 HoloLens 2 和 HoloLens 第 1 代）或 HoloLens 和 VR 为目标。  
因此，我们设计了可跨设备工作的交互模型，即使每个设备上的输入技术不同。  
例如，具有 6DoF 控制器的 Windows 沉浸式头戴显示设备上的远距交互和 HoloLens 2 上的远距交互都使用相同的视觉元素和模式，可轻松实现跨设备应用程序开发，并为用户的交互提供自然感受。 

虽然我们认识到 MR 中有成千上万种有效且吸引力十足的神奇交互，但是我们发现有意地在应用程序中衔接使用单个交互模型是确保用户成功并获得良好体验的最佳方法。 为此，我们在交互指南中提供了三项内容：
* 围绕三个主要交互模型以及每个模型所需的组件和模式的特定指南。
* 有关平台提供的其他优势的补充指南。
* 常规指南，用于选择适合开发方案的交互模型。

## <a name="multimodal-interaction-models"></a>多模式交互模型

根据我们的研究以及与客户的反馈，我们发现，有三个主要交互模型适合大多数混合现实体验。 在许多方面，交互模型是用户的心理模型，旨在阐述如何完成某个工作流。 每个交互模型都针对一组客户需求进行了优化，便于使用、功能强大且用途广泛（在正确使用的前提下）。 

下图是简化概述。 本页下方通过链接提供了有关使用每个交互模型的详细信息以及相关图像和代码示例。 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Model</strong></td>
        <td><strong>示例方案</strong></td>
        <td><strong>适合</strong></td>
        <td><strong>硬件</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">手和运动控制器</a></td>
        <td>3D 空间体验，例如空间布局和设计、内容操作或模拟。</td>
        <td>非常适合新用户，可与语音、眼动跟踪或头部凝视结合使用。 可轻易掌握。 跨手部跟踪和 6DoF 控制器使用一致的 UX 。</td>
        <td>HoloLens 2<br>沉浸式头戴显示设备</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">免动手操作</a></td>
        <td>用户双手不空时的情境体验，例如在职学习和维护。</td>
        <td>必需进行一些学习。 如果无法用手，设备可以配合使用语音和自然语言。</td>
        <td>HoloLens 2<br>HoloLens（第 1 代）<br>沉浸式头戴显示设备</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">凝视和提交</a></td>
        <td>点击式体验，例如 3D 演示文稿、演示。</td>
        <td>需要接受有关 HMD 的培训，但无需进行有关移动设备的培训。 最适合可访问控制器。 最适合 HoloLens（第 1 代）。</td>
        <td>HoloLens 2<br>HoloLens（第 1 代）<br>沉浸式头戴显示设备<br>移动 AR</td>
    </tr>
</table>
<br>

为了确保用户交互体验中不存在差距，最好是从头到尾遵循单个模型的指南。

以下部分将会介绍选择和实现其中一种交互模型的步骤。  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>查看完本页后，你将了解有关以下方面的指南：
 
* 为你的客户选择交互模型
* 实现交互模型
* 在交互模型之间转换
* 设计后续步骤


## <a name="choose-an-interaction-model-for-your-customer"></a>为你的客户选择交互模型

通常，开发人员和创作者已经全盘考虑了其客户可能使用的交互类型。 为了鼓励实现以客户为中心的设计，建议遵循以下指导选择针对客户进行了优化的交互模型。

### <a name="why-follow-this-guidance"></a>为什么要遵循以下指南？

* 我们的交互模型针对客观和主观标准（例如身体和认知努力、直觉和学习能力）进行了测试。 
* 由于交互不同，各交互模型的视觉/音频元素以及对象行为也可能不同。  
* 将多个交互模型的各个部分组合在一起可能会产生竞争性视觉元素的风险，例如同时出现手部射线和头部凝视光标， 这可能会使用户感到不知所措和混淆。

以下是一些如何针对每种交互模型优化可视线索和行为的示例。 我们经常看到新用户提出类似的问题，例如“我怎样才能知道系统是否在正常工作”、“我怎样才能知道我可以做什么”，以及“我怎样才能知道它是否理解我刚刚做了什么？”   

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Model</strong></td>
        <td><strong>我怎样才能知道它是否在正常工作？</strong></td>
        <td><strong>我怎样才能知道我可以做什么？</strong></td>
        <td><strong>我怎样才能知道刚才的操作？</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">手和运动控制器</a></td>
        <td>我看到一个手部网格，以及一个指尖视觉元素或手/控制器射线。</td>
        <td>当我的手靠近对象时，我看到可抓握的手柄或边界框出现。</td>
        <td>我听到有声音调，看到抓取和释放的动画。</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">头部凝视并提交</a></td>
        <td>我在视野中央看到一个光标。</td>
        <td>在光标置于某些对象上时，其状态会发生改变。</td>
        <td>当我执行动作时，我会看到/听到视觉和听觉确认。</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">解放双手（头部凝视和停留）</a></td>
        <td>我在视野中央看到一个光标。</td>
        <td>当我停留在一个可交互对象上时，我会看到一个进度指示器。</td>
        <td>当我执行动作时，我会看到/听到视觉和听觉确认。</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">（语音命令）</a></td>
        <td>我看到一个侦听指示器和字幕，显示系统听到的内容。</td>
        <td>我获得了语音提示。 当我说：“我可以说什么？” 我看到了反馈。</td>
        <td>当我发出命令时，我看到/听到视觉和听觉确认，或者在需要时得到消除歧义 UX。</a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a>以下问题可帮助团队选择交互模型：
 
1.  问:用户是否想要触控全息影像并执行精确的全息操作？<br><br>
答：如果是，请查看手部和运动控制器交互模型，以便进行精确定位和操作。
 
2.  问:用户是否需要因真实世界的任务而保持双手空闲？<br><br>
答：如果是，请查看解放双手交互模型，该模型通过基于凝视和语音的交互提供出色的解放双手体验。
 
3.  问:用户是否有时间学习 MR 应用程序的交互，或者他们是否需要尽可能轻松的掌握交互知识？<br><br>
答：建议使用手部和运动控制器模型，以便用户尽可能轻松地掌握相关知识并进行最直观的交互（只要用户能够用双手进行交互）。
 
4.  问:用户是否使用运动控制器进行指向和操作？<br><br>
答：手部和运动控制器模型包含了有关使用运动控制器实现出色体验的所有指导。
 
5.  问:用户是否使用辅助功能控制器或常用蓝牙控制器，例如遥控器？<br><br>
答：建议对所有非跟踪控制器使用头部凝视和提交模型。 它可让用户使用简单的“目标和提交”机制遍历全部体验。 
 
6.  问:用户是否仅通过“点击”来进行逐步体验（例如在类似 3D 幻灯片的环境中），而不是导航密集的 UI 控件布局？<br><br>
答：如果用户不需要控制大量 UI，则其可学习使用头部凝视和提交，无需担心如何进行定位。 
 
7.  问:用户是否同时使用 HoloLens（第 1 代）和 HoloLens 2/Windows Mixed Reality 沉浸式头戴显示设备 (VR)？<br><br>
答：由于头部凝视和提交是适用于 HoloLens（第 1 代）的交互模型，因此建议支持 HoloLens（第 1 代）的创意者对用户在 HoloLens（第 1 代）头戴显示设备上使用的任何功能或模式使用头部凝视和提交。 有关为多代 HoloLens 打造出色体验的详细信息，请参阅下面的“转换交互模型”部分  。
 
8.  问:与经常在单个空间中工作的用户相比，时常移动的用户（覆盖大空间或在各空间之间移动）可使用哪些交互模型？<br><br>
答：任何交互模型都适用于这些用户。  

> [!NOTE]
> [即将推出](news.md)有关应用设计的更多指南。


## <a name="transitioning-interaction-models"></a>转换交互模型
还有一些用例可能要求利用多个交互模型。 例如，应用程序的创建流程使用“手部和运动控制器”交互模型，但你想要为现场技术人员使用解放双手模式。 
如果你的体验确实需要多个交互模型，请注意，许多用户可能会在从一个模型转换到另一个模型时遇到困难，特别是刚接触混合现实的用户。

> [!Note]
> 我们正在持续为开发人员和设计人员编写更多的指南，以告知他们如何、何时以及为何使用多个 MR 交互模型。
 

## <a name="see-also"></a>另请参阅
* [舒适](comfort.md)
* [基于眼睛的交互](eye-gaze-interaction.md)
* [HoloLens 2 中的眼动跟踪](eye-tracking.md)
* [凝视和提交](gaze-and-commit.md)
* [凝视和停留](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手势](gaze-and-commit.md#composite-gestures)
* [手 - 指向并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [运动控制器](motion-controllers.md)
* [空间映射](spatial-mapping.md)
* [空间音效设计](spatial-sound-design.md)
* [语音输入](voice-input.md)


