---
title: 种交互的对象
description: 一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。 在三维混合的现实世界中，我们无需限制为抽象不再这个世界。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的现实、 控件、 交互、 ui 和 ux
ms.openlocfilehash: eea7eff6c591a9319b920936ce2be511cecb7496
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813815"
---
# <a name="interactable-object"></a>种交互的对象

一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。 在三维混合的现实世界中，我们无需限制为抽象不再这个世界。 可以是任何内容**种交互对象**触发事件。 种交互的对象可以表示为任何从上表杯咖啡到气球状飘浮在空中。 我们仍进行传统按钮在某些情况下此类如下所示对话框 UI 的使用。 按钮的可视表示形式取决于上下文。

![Interactible 对象](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>种交互的对象的重要属性

### <a name="visual-cue"></a>视觉提示

视觉提示是通过目测光的窗体中由接收和处理 visual 系统期间视觉感知传感器的提示。 由于 visual 系统是基准中许多种类，尤其是人类视觉提示的大的源代码中如何看待世界的信息。

混合现实中 holographic 对象相混合现实世界环境后，因为它可能会比较困难，了解这种交互的对象。 你的体验中的任何种交互对象，务必为每个输入状态提供独特的视觉提示。 这有助于用户了解您的体验的哪个部分是种交互，并使用户确信使用一致的交互方法。

#### <a name="far-interactions"></a>远端交互

任何对象该用户可以进行交互提供注视、 手 ray 与运动控制器的射线，我们建议具有不同的视觉提示，为这三种输入状态：
* **默认值 （观察）** :对象的默认空闲状态。
* **目标 （悬停）** :当对象被指向附带的视线移动游标时，手指邻近或动画控制器的指针。
* **按下**:对象按下时使用-敲击手势、 手指按或运动控制器的选择按钮。

技术，如突出显示或缩放可用于提供给用户的输入状态的视觉提示。 在 Windows Mixed Reality，可以找到的可视化开始菜单和应用程序栏按钮上的不同输入的状态的示例。 

![示例可视化观察状态，目标状态，并按下状态](images/640px-interactibleobject-states.png)<br>
*示例可视化观察状态，目标状态，并按下状态*

![观察状态，目标状态，和 holographic 按钮按下状态](images/MRTK_InteractableState.png)<br>
*观察状态，目标状态，和 holographic 按钮按下状态*

#### <a name="neardirect-interactions"></a>Near(direct) 交互

HoloLens 2 支持明确的手动跟踪输入可用于与对象进行交互。 而无需 haptic 反馈和完美深度感知有时可能难以告诉您的手距离是从对象，或是否会接触。 请务必提供足够的视觉提示进行通信的对象，您的掌控之中相对于全息具体的状态。

使用可视反馈进行以下通信：
* **默认值 （观察）** :对象的默认空闲状态。
* **将鼠标悬停在**:当手动一张全息图，更改视觉对象进行通信的手附近定目标到全息图。 
* **距离和交互点**: 随着手接近全息图，设计进行通信的预计的点的交互，以及如何当对象远上方的手指的反馈
* **请联系 Begin**:更改视觉对象 （光，颜色） 进行通信的触摸屏输入已发生
* **由于**:更改视觉对象 （light、 颜色） 时获取对象。
* **请联系最终**:更改视觉对象 （light、 颜色） 时触摸屏输入已结束。

![示例中的可视化附近交互状态](images/640px-interactibleobject-states-near.jpg)<br>
*示例中的可视化附近交互状态*

[HoloLens 2 中的按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)显示可视化不同输入的交互状态的示例。

![Pressable 按钮 HoloLens 2 中的示例](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*Pressable 按钮 HoloLens 2 中的示例*

在 HoloLens 2 中，没有其他的可视化提示可提高用户的置信度在深度感知。 在指尖环会出现，如指尖更接近于该对象向下缩放。 环最终汇聚到一个点上按下状态。 此 visual 功能可见性： 可帮助用户了解对象的距离。

![指尖环可视化效果](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*指尖环 HoloLens 2 中的可视化效果*

![在手动邻近的可视反馈](images/HoloLens2_Proximity.gif)<br>
*可视反馈的邻近的边界框示例*


### <a name="audio-cue"></a>则音频提示
直接手动交互，正确的音频反馈可以极大地改善用户体验。 音频反馈用于以下通信：
* **请联系开始**:开始触摸时播放声音
* **联系人结束**:触摸屏输入端上播放声音
* **随取即行开始**:随取即行启动时播放声音
* **获取结束**:随取即行结束上播放声音

### <a name="voice-command"></a>语音命令
对于任何种交互的对象，务必以支持其他交互选项。 默认情况下，建议对于的任何对象都是种交互支持语音命令。 若要提高可发现性，你可以提供工具提示处于悬停状态。

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="语音命令的工具提示" width="350"><br/>*语音命令的工具提示*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>创建混合现实工具包 (MRTK) 的种交互的对象

在中 **[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，可以找到的 Unity 脚本一系列和预设将帮助你创建种交互的对象。 您可以使用这些响应输入的交互状态的各种类型的对象。

* **[Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)**
* **[按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)**
* **[手动交互示例场景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)**

MixedRealityToolkit 的标准着色器提供了各种选项，例如**邻近 light** ，可帮助您创建视觉和声音提示。
* **[MRTK 标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)**


## <a name="see-also"></a>请参阅

* **[边界框](app-bar-and-bounding-box.md)**
* **[对象集合](object-collection.md)**
* **[公告板和尾随](billboarding-and-tag-along.md)**
