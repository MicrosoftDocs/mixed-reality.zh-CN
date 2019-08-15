---
title: 可交互对象
description: "\"Button\" 是一种用于在二维抽象环境中触发事件的比喻。 在这三维混合现实世界中, 我们不必再局限于这种抽象领域。"
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 混合现实、控件、交互、ui、ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415288"
---
# <a name="interactable-object"></a>可交互对象

"Button" 是一种用于在二维抽象环境中触发事件的比喻。 在这三维混合现实世界中, 我们不必再局限于这种抽象领域。 任何内容都可以是触发事件的**可交互对象**。 可交互对象可表示为从桌子上的咖啡杯到悬浮的球标的任何内容。 在某些情况下 (例如, 在对话框 UI 中), 我们仍要使用传统按钮。 按钮的可视化表示形式取决于上下文。

![Interactible 对象](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>可交互对象的重要属性

### <a name="visual-cue"></a>视觉提示

视觉提示是视觉对象的视觉对象系统中的眼睛传感器提示, 由视觉对象系统处理。 由于视觉对象系统在很多物种中是主导的, 尤其是在人们看来, 直观提示是了解世界上的信息。

在混合现实中, 由于全息对象与真实环境混合, 因此很难理解哪些对象是可交互的。 对于你的体验中的任何可交互对象, 为每个输入状态提供不同的视觉提示非常重要。 这可以帮助用户了解你的体验的哪个部分是可交互的, 并使用户能够通过一致的交互方法进行自信。

#### <a name="far-interactions"></a>远距离交互

对于用户可与 "注视"、"手形" 和 "运动控制器" 射线交互的任何对象, 我们建议对这三个输入状态使用不同的视觉提示:
* **默认值 (观察)** :对象的默认空闲状态。
* **目标 (悬停)** :当对象面向注视光标时, 指的是指邻近的或运动控制器的指针。
* **按下**:按下了 "按压" 手势时, 按下或运动控制器的选择按钮。

您可以使用诸如突出显示或缩放等方法为用户输入状态提供视觉提示。 在 Windows Mixed Reality 中, 可以在 "开始" 菜单和应用栏按钮上查找可视化不同输入状态的示例。 

![可视化观察状态、目标状态和按下状态的示例](images/640px-interactibleobject-states.png)<br>
*可视化观察状态、目标状态和按下状态的示例*

![全息按钮上的观察状态、目标状态和按下状态](images/MRTK_InteractableState.png)<br>
*全息按钮上的观察状态、目标状态和按下状态*

#### <a name="neardirect-interactions"></a>接近 (直接) 交互

HoloLens 2 支持已表述的手动跟踪输入, 可用于与对象进行交互。 如果没有 haptic 的反馈和完美的深度理解, 有时很难判断你手中的距离是来自对象, 还是要接触。 务必提供足够多的可视提示来传达对象的状态, 特别是与全息影像相关。

使用视觉反馈传达以下内容:
* **默认值 (观察)** :对象的默认空闲状态。
* **悬停**:当手位于全息图附近时, 更改视觉对象以传达此局的目标是全息影像。 
* **交互的距离和点**: 作为现有方法的方法, 设计反馈可传达投影的交互点, 以及手指的对象距离
* **联系人开始**:更改视觉对象 (浅色、颜色) 以传达触摸已发生的情况
* **Grasped**:当对象为 grasped 时, 更改视觉对象 (浅色、颜色)。
* **联系人结尾**:触摸已结束时更改视觉对象 (浅色、颜色)。

![可视化接近交互状态的示例](images/640px-interactibleobject-states-near.jpg)<br>
*可视化接近交互状态的示例*

[HoloLens 2 中的按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)显示了可视化不同输入交互状态的示例。

![HoloLens 2 中 pressable 按钮的示例](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*HoloLens 2 中 pressable 按钮的示例*

在 HoloLens 2 中, 有一个其他视觉提示, 可提高用户对深度认知的置信度。 当手指更接近对象时, 手指上的圆圈会显示并缩小。 该环最终汇聚为按下状态的点。 此视觉对象 affordance 可帮助用户了解与对象之间的距离。

![手指环形可视化](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*HoloLens 2 中的手指环可视化*

![视觉对象反馈](images/HoloLens2_Proximity.gif)<br>
*基于邻近边界框的视觉反馈示例*


### <a name="audio-cue"></a>音频提示
对于直接交互, 可通过适当的音频反馈来大幅改善用户体验。 使用音频反馈来传达以下内容:
* **联系人开始**:触摸开始时播放声音
* **联系人结尾**:在 touch 端上播放声音
* **开始**操作:开始抓取时播放声音
* **抓取结束**:在抓取结束时播放声音

### <a name="voice-command"></a>语音命令
对于任何可交互对象, 支持替代交互选项非常重要。 默认情况下, 建议为可交互的任何对象支持语音命令。 若要改进可发现性, 你可以提供悬停状态的工具提示。

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="语音命令的工具提示" width="350"><br/>*语音命令的工具提示*

## <a name="sizing"></a>大小调整
为了确保用户可以轻松地接触到所有可交互对象, 我们建议您确保可交互的大小达到最小值 (通常以视觉弧线度量的视觉角度), 这取决于从用户的距离。 视觉角度基于用户眼睛与对象之间的距离并保持不变, 而目标的物理大小可能会随用户更改的距离而更改。 若要根据用户的距离确定对象的必要物理大小, 请尝试使用视觉角度计算器 (如[此](http://elvers.us/perception/visualAngle/)类)。

下面是有关可交互内容的最小大小建议。

### <a name="target-size-for-direct-hand-interaction"></a>直接手动交互的目标大小
| 长途 | 查看角度 | Size |
|---------|---------|---------|
| 45cm  | 不小于2° | 1.6 x 1.6 厘米 |

![直接手动交互的目标大小](images/TargetSizingNear.jpg)<br>
*直接手动交互的目标大小*

创建直接交互的按钮时, 建议使用较大的最小 3.2 x 3.2 厘米, 以确保有足够的空间来包含图标, 并有可能出现一些文本 * *

| 长途 | 最小大小 |
|---------|---------|
| 45cm  | 3.2 x 3.2 厘米 |

![按钮的目标大小](images/TargetSizingButtons.png)<br>
*按钮的目标大小*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>手动 ray 或注视交互的目标大小
| 长途 | 查看角度 | Size |
|---------|---------|---------|
| 2m  | 不小于1° | 3.5 x 3.5 厘米 |

![手动 ray 或注视交互的目标大小](images/TargetSizingFar.jpg)<br>
*手动 ray 或注视交互的目标大小*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>利用混合现实工具包创建可交互对象 (MRTK)

在 **[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 中, 可以找到可帮助你创建可交互对象的一系列 Unity 脚本和 prototyping。 您可以使用这些对象来对各种类型的输入交互状态进行响应。

* [可交互](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [手动交互示例场景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit 的标准着色器提供了各种选项 **, 例如**, 可帮助您创建视觉对象和音频提示。
* [MRTK 标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>请参阅

* [边界框](app-bar-and-bounding-box.md)
* [对象集合](object-collection.md)
* [公告和尾随](billboarding-and-tag-along.md)
