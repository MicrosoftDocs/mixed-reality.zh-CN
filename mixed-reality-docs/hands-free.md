---
title: 免提
description: 优化应用程序进行无
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 混合现实，无需手动、 注视、 注视目标交互，设计
ms.openlocfilehash: 4d21fa10eabb446565bddebccdbde5e2e7bcc72a
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326154"
---
# <a name="hands-free"></a>免提



## <a name="scenarios"></a>方案

中所述[交互模型概述](interaction-fundamentals.md)，一旦您已确定用户和他们的目标，问问自己环境或态势处理来完成其任务，它们可能会遇到的挑战。 例如，许多用户需要使用太多的事情来完成实际的目标，并将有困难手控制器基于接口与之进行交互。 

某些特定方案可能是： 
* 虽然为忙正在指导您完成一个任务，
* 虽然都在忙于手引用材料
* 手疲劳
* 无法跟踪手套
* 执行的内容


## <a name="hands-free-modalities"></a>无模式

### <a name="voice-commandingvoice-designmd"></a>[语音命令](voice-design.md)

使用语音命令和控制接口可以不只是允许用户运行 handsfree，但还跳过多个步骤。 此模式的使用情况的范围可以从允许用户只需读取大声读出要激活它，如下所示，请参阅 it-say-it，活跃的可以为您完成任务代理的任何按钮的名称。



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[头部凝视和停留](gaze-and-dwell.md)

在某些无需干预的情况下，使用您的声音不是理想之选或甚至可能。 大声工厂环境、 隐私或社交标准所有可以进行限制。 头注视 + 会仔细斟酌模型允许用户使用其头矢量点时延迟，导航应用程序或抛开按钮将激活它在一段时间，通常大约 1 秒钟左右后。 


## <a name="transitioning-in-and-out-of-hands-freey"></a>转换入和移出手 freey

对于这些情况下，释放与命令和导航全息交互手范围可以为要到运行该应用程序，端到端到一种方便性的用户可以在任何转换中是绝对要求时间。 

如果应用程序的要求是，它将始终使用无，通过使用停留、 语音命令或单个语音命令，"select"，然后请务必在 UI 中进行相应的住宿部。 

如果目标用户需要能够从手中切换到无自行，然后务必考虑以下原则。

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>假定用户已在他们想要切换到的模式
例如，如果用户是在工厂车间上观看她 hololens 的视频引用，并决定选取扳手以开始使用，她很可能会在中开始工作 handsfree 而无需放下扳手按一个按钮。 她应该能够调用语音会话使用语音命令，开始停留，已经可见 UI 在此再次详述或假设单词"select"。

用户应具有的功能： 
* 切换到 handsfree handsfree 时
* 切换到用手向提供
* 切换到使用控制器的控制器 

### <a name="create-redundant-ways-to-switch-modes"></a>创建冗余的方式，若要切换模式
有关访问的第一个原则时，第二个是有关可用性。 存在不应只需为转换入和移出一种模式有一种方法。 

将一些示例： 
* 按钮以开始的语音交互
* 使用提供注视 + 停留转换语音命令

### <a name="add-a-dash-of-drama"></a>添加短划线 drama
一种模式切换很了不起-非常重要，这些转换发生时它们是显式、 甚至显著交换机，以让用户知道发生了什么情况。 


## <a name="usability-checklist"></a>可用性核对清单

**用户可以做的所有内容和无、 端到端的任何内容？**
* 每个 interactible 应可访问无
* 确保所有的自定义笔势，例如重设大小、 放置、 扫，点击等的替换。
* 确保用户始终可以确信控制的 UI 状态、 位置和详细级别
    * 获取 UI 开
    * 寻址超出视野 (FOV) 的 UI
    * 我看到多少，其中时,

**是的交互机制正在讲授和强化与正确的提示？**

用户了解...
* ...它们是哪种模式中？
* ...就像在此模式下？
* ...当前状态是怎样的？
* ...他们如何可以向外转换？
    
**UI 适用于无？**   

* 例如：停留提供不是内置于典型的 2D 模式
* 例如：语音目标是更好地与对象突出显示
* 例如：语音交互是更好地与已启用的隐藏式字幕


## <a name="see-also"></a>请参阅
* [头部凝视并提交](gaze-and-commit.md)
* [直接操作](direct-manipulation.md)
* [指向并提交](point-and-commit.md)
