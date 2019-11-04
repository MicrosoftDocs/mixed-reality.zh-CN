---
title: 免提
description: 优化你的应用程序以进行无人参与
author: liamartinez
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 混合现实，无人参与，注视，注视目标，交互，设计
ms.openlocfilehash: b2405f5dca19838271363f53ca377c4f90ca1b36
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435072"
---
# <a name="hands-free"></a>免提

## <a name="scenarios"></a>场景

如[交互模型概述](interaction-fundamentals.md)中所述，一旦确定了用户及其目标，就可以在工作完成任务时询问自己面临的环境或环境挑战。 例如，许多用户都需要使用自己的动手来实现其真实目标，并且与基于动手的接口的接口交互很困难。 

一些具体的方案包括： 
* 通过任务进行指导，而用户的工作繁忙
* 用户的手忙时引用材料
* 手动疲劳
* 无法跟踪的手套
* 动手携带东西
* 社交 awkwardness 来执行大型手势
* 紧密型空格


## <a name="hands-free-modalities"></a>无人参与情态

### <a name="voice-inputvoice-inputmd"></a>[语音输入](voice-input.md)

使用语音执行命令和控制接口提供了一种便捷的方式来操作，并使用快捷方式灵活地跳过多个步骤（如果需要）。 使用语音输入，用户只需将任何按钮的名称放在一起即可激活 _（"查看它，说这一点"）_ ，并与可以完成任务的数字代理进行对话。


### <a name="gaze-and-dwellgaze-and-dwellmd"></a>[凝视和停留](gaze-and-dwell.md)

在某些免提情况下，使用语音并不理想或甚至可能。 很大的工厂环境、隐私或社会规范都可以进行限制。 "注视 + 停留" 模型允许用户在没有任何其他输入的情况下从其眼睛或打印头导航到应用：用户只需在目标位置保留 gazing （具有其头或眼睛），并在一段时间内 lingers。 若要详细了解注视和停留的各个设计注意事项，请查看[眼睛和停留和眼睛](gaze-and-dwell-eyes.md) [+ 停留](gaze-and-dwell-head.md)。


## <a name="transitioning-in-and-out-of-hands-free"></a>转换为无干预

在这些情况下，让你可以轻松地与用于发出命令和导航的全息影像交互，范围可能是对应用程序进行端到端操作的绝对要求，而不是用户可以在任何阶段. 

如果应用程序的要求是始终使用免提，无论是通过使用停留、自定义语音命令还是使用单个语音命令，"选择"，都请确保在用户界面中提供合适的便利。 

如果你的目标用户需要能够自行从手切换到无人参与，则必须考虑以下原则。

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>假设用户已处于要切换到的模式
例如，如果用户在工厂地面上，观看其 HoloLens 上的视频参考，并决定提起扳手开始工作，则她很可能会开始免费工作，而无需将扳手按下按钮。 她应能够使用语音命令调用语音会话，停留在已可见的 UI 上，开始停留，或说 "选择" 一词。

用户应该能够： 
* 在无人参与的情况下切换到无人参与
* 用双手切换
* 使用控制器切换到控制器 

### <a name="create-redundant-ways-to-switch-modes"></a>创建冗余方式来切换模式
第一个原则就是访问，另一个原则就是可用性。 不应该只是一种在模式中执行转换的方法。 

以下是一些示例： 
* 用于开始语音交互的按钮
* 用于转换到的语音命令，使用打印头和停留

### <a name="add-a-dash-of-drama"></a>添加 drama 的短划线
模式切换是一项很重要的事情，这一点很重要，在这些过渡发生时，它们是一种明显的、甚至是一个巨大的交换机，让用户知道发生了什么情况。 


## <a name="usability-checklist"></a>可用性清单

**用户可以执行所有操作，也可以从端到端免费完成，**
* 每个种不可交互应可随时访问
* 确保所有自定义手势都有替换，如调整大小、放置、swipes、点击等。
* 确保用户完全控制 UI 的存在、位置和详细程度
    * 正在获取 UI
    * 对超出视图（FOV）的 UI 进行寻址
    * 我看到了多少，

**与正确的实用一起教授和加强的交互的机制是什么？**

用户了解 。
* ...它们处于哪种模式？
* ...在此模式下可以执行哪些操作？
* ...什么是当前状态？
* ...如何转换？
    
**UI 是否经过优化，无人参与？**   

* 示例：停留实用不内置于典型的2D 模式
* 示例：语音目标更适合对象突出显示
* 示例：对于需要打开的标题，语音交互更好


## <a name="see-also"></a>另请参阅
* [HoloLens 2 上的目视跟踪](eye-tracking.md)
* [注视并提交](gaze-and-commit.md)
* [凝视和停留](gaze-and-dwell.md)
* [直接操作](direct-manipulation.md)
* [动手手势](gaze-and-commit.md#composite-gestures)
* [动手并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)
