---
title: Billboarding 和标记
description: 具有 billboarding 的对象始终向用户提供正面的定向。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, billboarding, 连同标记
ms.openlocfilehash: e33ab0121398742b2e48553c9cbf2c1debdc6abf
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974790"
---
# <a name="billboarding-and-tag-along"></a>Billboarding 和标记

Billboarding 是一种可应用于混合现实中的对象的行为概念。 具有 billboarding 的对象始终向用户提供正面的定向。 这对于文本和 menuing 系统特别有用, 在这种情况下, 如果用户要四处移动, 用户环境 (全球锁定) 中放置的静态对象将被掩盖或无法读取。

![始终面向用户的菜单系统的 HoloLens 透视](images/billboarding-fragments.gif)<br>
*始终面向用户的菜单系统的 HoloLens 透视*

启用了 billboarding 的对象可以在用户的环境中自由旋转。 它们还可以根据设计注意事项限制为单个轴。 请记住, 如果 billboarded 对象置于其他对象之前太近, 或在 HoloLens 中太接近扫描面, 则它们可能会被剪裁或遮蔽。 为避免出现这种情况, 请考虑在为 billboarding 启用轴旋转时对象可能产生的总空间。

## <a name="what-is-a-tag-along"></a>什么是标记？

标记-一起是可以添加到影像的行为概念, 包括 billboarded 对象。 这种交互是实现 head 锁定内容效果的更自然且友好的方式。 标记靠后的对象将不会离开用户的视图。 这样, 用户就可以自由地与其前面的内容交互, 同时还会看到其直接视图外的全息影像。

![HoloLens 引脚面板是如何在标签上表现出的一个很好的示例](images/tagalong-1000px.jpg)<br>
*HoloLens "开始" 菜单是一个更好的标记和行为示例*

标记靠对象具有可对其行为方式进行微调的参数。 当用户在其环境中移动时, 可以根据需要将内容移入或移出用户的行为。 用户移动时, 内容将尝试在用户的绕中移动, 并向视图边缘滑动, 具体取决于用户的移动速度, 可能会使内容暂时消失。 当用户 gazes 沿标记的对象时, 它会更全面地进入视图。 将内容视为始终 "一目了然", 这样用户就不会忘记内容的方向。

其他参数可以通过橡皮带来使标记沿着对象的外观附加到用户的头。 抑制加速或减速为对象提供权重, 使其感觉更真实地出现。 此春季行为是一种 affordance, 可帮助用户构建准确的心理模型, 说明如何进行标记。 当用户在标记沿模式下具有对象时, 音频有助于提供附加的实用。 音频应强化移动速度;迅速走下来应提供更为明显的声音效果, 同时, 如果有任何效果, 自然速度应具有最小的音频。

与真正的 head 锁定的内容一样, 如果对象在用户的视图中变得很大或太过太多, 则这些对象可能会 nauseating。 用户浏览并快速停止时, 他们的感知告诉他们已停止。 它们的平衡通知他们打印头已停止转动, 并使其视觉效果看起来很好。 但是, 如果在用户停止时仍继续进行标记, 则可能会混淆其感知。

## <a name="see-also"></a>请参阅
* [光标](cursors.md)
* [本能交互](interaction-fundamentals.md)
* [舒适](comfort.md)
