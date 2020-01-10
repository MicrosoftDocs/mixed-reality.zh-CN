---
title: Billboarding 和标记
description: 具有 billboarding 的对象始终向用户提供正面的定向。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，billboarding，连同标记
ms.openlocfilehash: 24c4ca8bdc3c6ea1081311102204d4a7f5a95425
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723176"
---
# <a name="billboarding-and-tag-along"></a>Billboarding 和标记

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>什么是 billboarding？

Billboarding 是一种可应用于混合现实中的对象的行为概念。 具有 billboarding 的对象始终向用户提供正面的定向。 这对于文本和 menuing 系统特别有用，在这种情况下，如果用户要四处移动，用户环境（全球锁定）中放置的静态对象将被掩盖或无法读取。

启用了 billboarding 的对象可以在用户的环境中自由旋转。 它们还可以根据设计注意事项限制为单个轴。 请记住，如果 billboarded 对象置于其他对象之前太近，或在 HoloLens 中太接近扫描面，则它们可能会被剪裁或遮蔽。 为避免出现这种情况，请考虑在为 billboarding 启用轴旋转时对象可能产生的总空间。

<br>

---
## <a name="what-is-a-tag-along"></a>什么是标记？

标记-一起是可以添加到全息影像的行为概念。 标记靠后的对象试图停留在允许用户轻松交互的范围内。

![的 "HoloLens 引脚" 面板是有关标记的行为方式的很好示例](images/tagalong-1000px.jpg)<br>
*HoloLens "开始" 菜单是一个更好的标记和行为示例*

标记靠对象具有可对其行为方式进行微调的参数。 当用户在其环境中移动时，可以根据需要将内容移入或移出用户的行为。 用户移动时，内容将尝试在用户的绕中移动，并向视图边缘滑动，具体取决于用户的移动速度，可能会使内容暂时消失。 当用户 gazes 沿标记的对象时，它会更全面地进入视图。 将内容视为始终 "一目了然"，这样用户就不会忘记内容的方向。

其他参数可以通过橡皮带来使标记沿着对象的外观附加到用户的头。 抑制加速或减速为对象提供权重，使其感觉更真实地出现。 此春季行为是一种 affordance，可帮助用户构建准确的心理模型，说明如何进行标记。 当用户在标记沿模式下具有对象时，音频有助于提供附加的实用。 音频应强化移动速度;迅速走下来应提供更为明显的声音效果，同时，如果有任何效果，自然速度应具有最小的音频。

与真正的 head 锁定的内容一样，如果对象在用户的视图中变得很大或太过太多，则这些对象可能会 nauseating。 用户浏览并快速停止时，他们的感知告诉他们已停止。 它们的平衡通知他们打印头已停止转动，并使其视觉效果看起来很好。 但是，如果在用户停止时仍继续进行标记，则可能会混淆其感知。

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>用于 Unity 的 MRTK （混合现实工具包）中的 Billboarding 和标记
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为 Billboarding 和标记的行为提供脚本。 只需将 Billboard.cs 脚本分配到任何对象即可添加 billboarding 行为，并使对象始终为你。 若要添加标记和行为，请使用 RadialView.cs 脚本。 可以调整各种选项，如 lerping 时间、距离和角度。

* [MRTK-径向视图规划求解](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [MRTK-布告栏脚本](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>另请参阅

* [光标](cursors.md)
* [手部射线](point-and-commit.md)
* [Button](button.md)
* [可交互对象](interactable-object.md)
* [边界框和应用栏](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手动菜单](hand-menu.md)
* [追踪菜单](near-menu.md)
* [对象集合](object-collection.md)
* [语音命令](voice-input.md)
* [键盘](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑块](slider.md)
* [着色器](shader.md)
* [公告和尾随](billboarding-and-tag-along.md)
* [显示进度](progress.md)
* [表面磁吸](surface-magnetism.md)
