---
title: 免提
description: 优化你的应用程序以进行无人参与
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 混合现实, 无人参与, 注视, 注视目标, 交互, 设计
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414396"
---
# <a name="hands-free"></a>免提



## <a name="scenarios"></a>方案

如[交互模型概述](interaction-fundamentals.md)中所述, 一旦确定了用户及其目标, 就可以在工作完成任务时询问自己面临的环境或环境挑战。 例如, 许多用户都需要使用他们的手来完成其真实的目标, 并且难以与基于手工控制器的界面进行交互。 

某些特定情况可能如下: 
* 正在通过任务进行指导, 而实际情况却非常繁忙
* 在您的计算机忙时引用材料
* 手动疲劳
* 无法跟踪的手套
* 携带东西


## <a name="hands-free-modalities"></a>无人参与情态

### <a name="voice-commandingvoice-designmd"></a>[语音命令](voice-design.md)

使用语音执行命令和控制接口不仅可允许用户操作 handsfree, 还可以跳过多个步骤。 这种形式的使用范围包括允许用户只需大声地阅读任何按钮名称以激活它, 如中所示, 可以使用可以完成任务的代理。



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[头部凝视和停留](gaze-and-dwell.md)

在某些免提情况下, 使用语音并不理想或甚至可能。 很大的工厂环境、隐私或社会规范都可以进行限制。 使用 head + 停留模型, 用户可以通过使用其头向量在应用中导航, 而延迟或按钮上的 dwelling 会在一段时间后激活它, 通常为1秒左右。 


## <a name="transitioning-in-and-out-of-hands-free"></a>转换为无干预

在这些情况下, 让你可以轻松地与用于发出命令和导航的全息影像交互, 范围可能是对应用程序进行端到端操作的绝对要求, 而不是用户可以在任何阶段. 

如果应用程序的要求是始终使用免提, 无论是使用停留、语音命令还是单个语音命令 "select", 都请确保在用户界面中设置适当的 accomodations。 

如果你的目标用户需要能够自行从手切换到无人参与, 则必须考虑以下原则。

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>假设用户已处于要切换到的模式
例如, 如果用户在工厂地面上, 观看其 Hololens 上的视频参考, 并决定选取一个扳手开始工作, 那么她很可能会开始在 handsfree 中工作, 而无需将扳手按下某个按钮。 她应能够使用语音命令调用语音会话, 停留在已可见的 UI 上, 开始停留, 或说 "选择" 一词。

用户应该能够: 
* 在无人参与的情况下切换到无人参与
* 用双手切换
* 使用控制器切换到控制器 

### <a name="create-redundant-ways-to-switch-modes"></a>创建冗余方式来切换模式
第一个原则就是访问, 另一个原则就是可用性。 不应该只是一种在模式中执行转换的方法。 

以下是一些示例: 
* 用于开始语音交互的按钮
* 用注视 + 停留转换为的语音命令

### <a name="add-a-dash-of-drama"></a>添加 drama 的短划线
模式切换是一项很重要的事情, 这一点很重要, 在这些过渡发生时, 它们是一种显式甚至巨大的交换机, 让用户知道发生了什么情况。 


## <a name="usability-checklist"></a>可用性清单

**用户可以执行所有操作, 也可以从端到端免费完成,**
* 每个 interactible 应可随时访问
* 确保所有自定义手势都有替换, 如调整大小、放置、swipes、点击等。
* 确保用户完全控制 UI 的存在、位置和详细程度
    * 正在获取 UI
    * 对超出视图 (FOV) 的 UI 进行寻址
    * 我看到了多少,

**与正确的实用一起教授和加强的交互的机制是什么？**

用户了解 。
* ...它们处于哪种模式？
* ...在此模式下可以执行哪些操作？
* ...什么是当前状态？
* ...如何转换？
    
**UI 是否经过优化, 无人参与？**   

* 例如：停留实用不能内置于典型的2D 模式
* 例如：对象突出显示效果更佳
* 例如：与必须打开的字幕相比, 语音交互更好


## <a name="see-also"></a>请参阅
* [头部凝视并提交](gaze-and-commit.md)
* [使用手直接操作](direct-manipulation.md)
* [使用手指向和提交](point-and-commit.md)
