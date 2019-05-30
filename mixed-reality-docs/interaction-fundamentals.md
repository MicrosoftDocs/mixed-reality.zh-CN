---
title: 多模式交互概述
description: 多模式交互的概述
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实、 提供注视、 视线移动目标交互，设计、 hololens，MMR，multimodal
ms.openlocfilehash: d018179e20d26ee8b7b24bc74d7c1711bc788282
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270386"
---
# <a name="introducing-instinctual-interactions"></a>引入 instinctual 交互

简单、 instinctual 交互的基本原理是整个 Microsoft 混合现实 (MMR) 平台，从硬件到软件织物。

这些 instinctual 交互利用所有可用的输入的技术，包括无缝多模式交互模型中的内而外跟踪、 跟踪的手、 眼睛追踪和自然语言。 根据我们的研究，设计和开发 multimodals，并且不基于单个输入至关重要时创建本能的体验。

跨设备类型还很自然地对齐 Instinctual 交互模型。  例如，为 6 的自由 (DoF) 控制器在沉浸式头戴式远端交互和 HoloLens 2 上的远端交互使用相同的提示、 模式和行为。  不只是这方便，为开发人员和设计器中，但它感觉自然向最终用户。


最后，虽然我们已经认识到，有数千个有效、 富有吸引力神奇的交互可能 MR 中，我们已找到该有意采用单个交互模型中端到端应用程序就是确保用户是成功的最佳方法和获得完美的体验。  为此，我们提供了此交互指南中的三个操作：
* 我们已结构化围绕三个主要交互模型的组件和模式所需的每个本指南
* 我们提供了我们平台提供了其他权益的补充指南
* 我们提供了指导，以帮助选择适合您的方案的相应交互模型

## <a name="multimodal-interaction-models"></a>多模式交互模型

根据我们的研究和使用日期的客户，我们已发现满足大多数混合现实体验的三个主要交互模型。  

这些交互模型视为完成他们的流的用户的思维模式。

每个这些交互模型是方便、 强大且可在自己的权限中使用，所有客户需求的一组针对进行了优化。 查看图表下方、 方案、 示例和每个交互模型的好处的。  

**Model** | **[双手和动作控制器](hands-and-tools.md)** | **[免提](hands-free.md)** | **[Head 注视和提交](gaze-and-commit.md)**
|--------- | --------------| ------------| ---------|
**示例方案** | 3D 空间的体验，例如空间布局和设计，内容操作或模拟 | 上下文体验，其中用户的手都被占用，例如学习，维护作业| 点击体验，例如 3D 演示文稿、 演示材料
**合适大小** | 非常适用于新用户，耦合的 wit 语音眼睛跟踪或头的视线移动。 低学习曲线。 在手动跟踪和 6 DoF 控制器之间的一致用户体验。 | 一些学习所需。 如果为对也不可用语音和自然语言 | 需要培训 HMDs 上但不是移动设备上。 最适合可访问的控制器。 最适合 HoloLens （第 1 代）。 |
**硬件** | HoloLens 2 <br>沉浸式头戴显示设备 | HoloLens 2 <br>HoloLens （第 1 代） <br>沉浸式头戴显示设备 | HoloLens 2 <br>沉浸式头戴显示设备 | HoloLens 2 <br>HoloLens （第 1 代） <br>沉浸式头戴显示设备 <br>移动 AR |

在每个交互模型中无缝地配合使用所有可用输入的详细的信息是按照图例和从我们 Unity MRTK 示例内容的链接以及页面上。


## <a name="choose-an-interaction-model-for-your-customer"></a>选择为您的客户交互模型


很可能，开发人员和创建者也已有的一些观点记住他们想要其用户的交互体验种类。
鼓励客户为中心的方法来设计，我们建议遵循以下指南来选择适合您的客户的交互模型。

### <a name="why-follow-this-guidance"></a>为什么要遵循以下指南？

* 测试我们的交互模型为目标和物理和认知工作量、 intuitiveness 和 learnability 等的主观标准。 
* 因为交互不同，视频和音频提示和对象行为可能之间的交互模型也不同。  
* 组合在一起的多个交互模型部分会竞争等，如同时进行手动大气和 head 视线移动游标，这会倾覆并使用户感到困惑的风险。

下面是针对每个交互模型提供和行为进行了优化的一些示例。  我们通常看到新的用户类似的问题，如"如何知道系统工作，如何知道我可以做什么，以及如何知道是否理解刚才的操作？"

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
        <td><strong>如何知道是否正常工作？</strong></td>
        <td><strong>如何知道我可以做什么？</strong></td>
        <td><strong>如何知道刚才的操作？</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">手和运动控制器</a></td>
        <td>我看到 mesh 手的形状，我看到指尖功能可见性： 或手动 / 控制器光线。</td>
        <td>我看到 grabbable 句柄或即将达到我的手时，将显示边界框。</td>
        <td>我听到声音声音，并在随取即行和发布到动画。</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">头部凝视并提交</a></td>
        <td>我看到我的视野中心中的游标。</td>
        <td>Head 视线移动游标时对特定对象的状态更改。</td>
        <td>我看到/听到视频和音频确认时我采取措施。</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">无 （Head 注视和停留）</a></td>
        <td>我看到我的视野中心中的游标。</td>
        <td>当我在此再次详述种交互的对象时，我看到一个进度指示器。</td>
        <td>我看到/听到视频和音频确认时我采取措施。</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">无 （语音命令）</a></td>
        <td>我看到一个侦听的指示符和显示系统听到的隐藏式字幕。</td>
        <td>获取语音提示和提示。  当我说"我可以说什么？" 我看到的反馈。</td>
        <td>我看到/听到视频和音频确认为提供一个命令，或获取消除歧义时所需的用户体验时。</a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a>以下是，我们发现，帮助团队选择交互模型的问题：
 
1.  问:我的用户是否想要触摸全息并执行精度 holographic 操作？<br><br>
答：如果是这样，请查看精度目标以及与手或运动控制器操作的双手和工具交互模型。
 
2.  问:我的用户是否需要保留其手中免费的实际的任务？<br><br>
答：如果是这样，看一看无交互模型，它提供更完美的动手体验通过基于的视线移动和语音的交互。
 
3.  问:我的用户拥有时间来学习我混合的现实的应用程序的交互或他们是否需要与最小的学习曲线之间的交互可能？<br><br>
答：我们建议的最低的学习曲线和最直观交互的双手和工具模型，只要用户就能够使用太多的事情进行交互。
 
4.  问:我的用户是否为指向和操作使用 motion 控制器？<br><br>
答：双手和工具模型包括所有指南与运动控制器更完美的体验。
 
5.  问:是否可访问性控制器或常见的蓝牙控制器，例如 clicker 使用我的用户？<br><br>
答：我们建议为所有非跟踪控制器的 Head 注视和提交模型。  它旨在使用户能够遍历整个简单的"目标和提交"技工经验。 
 
6.  问:我的用户仅进行体验"通过单击"（例如在 3d 类似于幻灯片放映的环境中），而不是导航的 UI 控件的密集布局？<br><br>
答：如果用户不需要控制 UI 的很多，Head 注视和提交提供了其中的用户不需要担心如何面向 learnable 选项。 
 
7.  问:我的用户使用这两个 HoloLens （第 1 代） 和 HoloLens 2 / Windows 沉浸式 （VR 耳机）<br><br>
答：由于头注视和提交是 HoloLens 交互模型 （第 1 代），我们建议，创作者支持 HoloLens （第 1 代） 使用 Head 视线移动，并提交的任何功能或用户可能会遇到 HoloLens 的模式 （第 1 代） 耳机。  请参阅下面的下一步部分上*转换交互模型*有关更多 HoloLens 代为很好的体验的详细信息。
 
8.  问:怎么办对于用户而言通常移动 （涉及大型空间或空间之间移动），而不是往往会在单个的空间内工作的用户？<br><br>
答：交互模型中的任何适用于这些用户。  

> [!NOTE]
> 特定于应用程序设计的更多指导[即将推出](index.md#news-and-notes)。


## <a name="transition-interaction-models"></a>转换交互模型
此外，还有用例可能需要利用多个交互模型的情况。  例如，你的应用的"创建流"利用双手和工具交互模型，但你想要对现场技术人员采用无模式。  

如果您的体验确实需要多个交互模型，我们发现许多最终用户可能会遇到转换从一个模型到另一个-尤其是最终用户的新 MR 的难度。

> [!Note]
> 为了帮助指南设计人员和开发人员通过在 MR 将非常困难的选择，我们正致力于使用多个交互模型的详细指南。
 

## <a name="see-also"></a>请参阅
* [头部凝视并提交](gaze-and-commit.md)
* [头部凝视和停留](gaze-and-dwell.md)
* [使用手直接操作](direct-manipulation.md)
* [使用手指向和提交](point-and-commit.md)
* [手势](gestures.md)
* [语音命令](voice-design.md)
* [运动控制器](motion-controllers.md)
* [空间音效设计](spatial-sound-design.md)
* [空间映射设计](spatial-mapping-design.md)
* [舒适](comfort.md)

