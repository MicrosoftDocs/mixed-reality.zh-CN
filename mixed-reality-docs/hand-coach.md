---
title: MRTK 手型指导设计指南
description: 当系统未检测到用户的手以帮助提供帮助时，将触发3D 指针。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality，设计，手型指导，沉浸式耳机，MRTK，双手，帮助
ms.openlocfilehash: dc04f8f77548b226a822576befd60be107f4d3fb
ms.sourcegitcommit: 87aca9c2b73b0e83cb70a46443dcdb08c3621005
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77373518"
---
# <a name="hand-coach-design-guidance"></a>手动指导设计指南

手动指导是指在系统未检测到用户的手时触发的三维建模手。 这是作为 "教学" 组件实现的，该组件可帮助引导用户在未教授手势时进行引导。 如果用户未在某个时间段内完成指定的手势，则会循环一段时间。 手型指导可用于表示按下按钮或选取全息图标。  


![示例：手型指导](images/HandCoach/MRTK_handCoach.jpg)<br>
*MRTK 中的 HandCoach 示例*

## <a name="hand-coach-provided"></a>手写指导

当前交互模型表示各种手势控件，例如滚动、远选和点击显示。 下面是<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets">MRTK</a>中提供的现有手型手势的完整列表：

:::row:::
    :::column:::
       接近 Select](images/HandCoach/NearSelect.gif) ![示例<br>
       **接近选择使用的示例显示如何选择按钮或关闭种不可交互对象**<br>
    :::column-end:::
    :::column:::
       ](images/HandCoach/AirTap.gif) ![示例<br>
        **空中点击的示例-用于显示如何选择远距离的对象**<br>
    :::column-end:::
    :::column:::
       Move](images/HandCoach/Move.gif) ![示例<br>
       **将对象移动到空间的示例-用于显示如何在空间中移动全息图**<br>
    :::column-end:::
    :::column:::
       旋转的 ![示例](images/HandCoach/Rotate.gif)<br>
       **旋转示例-用于演示如何旋转全息影像或对象**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       Scale](images/HandCoach/Scale.gif) ![示例<br>
       **缩放示例-用于显示如何操作更大或更小的全息影像**<br>
    :::column-end:::
    :::column:::
       手掌](images/HandCoach/PalmUp.gif) 的 ![示例<br>
        **掌上-建议使用的示例，用于引入手菜单**<br>
    :::column-end:::
    :::column:::
       HandFlip](images/HandCoach/HandFlip.gif) ![示例<br>
       **示例-用于打开手形菜单的另一种方式**<br>
    :::column-end:::
    :::column:::
       滚动](images/HandCoach/Scoll.gif) 的 ![示例<br>
       **滚动示例–用于滚动列表或长文档**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>设计概念

对于 Hololens2，我们基于 instinctual 和自然手势设计出了手动交互。 我们相信它们对于大多数用户来说是直观的，因此不会创建专用的手势学习时间。 相反，我们创建了一本手形指导，帮助可能遇到的问题，或者不熟悉与全息影像交互的用户了解这些手势。 如果没有学习，我们认为向用户展示如何执行操作，这是最佳选择。 在我们的研究中，我们发现用户能够找出手势，但需要一些指导。 如果检测到某个用户在某个时间段内没有与某个对象进行交互，则会触发一则手指导，说明正确的抓手和手指位置。 

### <a name="intuitive"></a>直观

动画处理时，应该很明显，shoudn't 会造成混淆。 指针的动画是您尝试调用它用户了解其用途的手势的表示形式。 

例如，如果希望用户按下某个按钮，则会触发按下按钮的一只手。

![示例：点击点击](images/HandCoach/NearSelect_unity.gif)<br>
*演示附近点击 Gem 的指导*  

### <a name="hand-scale"></a>手动缩放

我们使用 UI 菜单测试了各种手大小，并感觉到，如果想要调整其大小，就会发现 menacing，但如果它们太小，则很难看到和理解手势。 

**语音和手**

不要指望用户可以通过语音来侦听一组说明，并通过手动指导观看不同说明。 序列化说明，帮助用户专注于争用，从而减少传感器的过载。


## <a name="can-i-create-my-own"></a>我能创建自己的吗？

可以！ 我们鼓励你为游戏创建自己的独特手势，并向社区提供反馈！
我们提供了可用于你的应用的 Maya 文件 Rigged，可在此处下载：<a href="files/HandCoach_MRTK.zip">下载 HandCoach_MRTK .zip</a>

![Maya 中的动画的示例](images/HandCoach/MayaSelect_Gif.gif)<br>
*Maya 中闲逛的动画手形的示例*


**推荐的创作工具**

在三维音乐家之间，很多选择使用[Autodesk 的 Maya，它本身能够使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)来转换资产的创建方式。 提供的免提文件是一个 Maya 二进制文件，因此建议使用 Maya 来动画和导出手。 如果希望使用其他三维程序，请单击此处<b>。FBX</b>：<a href="files/HandCoachMRTK_FBX.zip">下载 HandCoachMRTK_FBX .zip</a> ，创建自己的控制器设置。 

如果使用提供的可下载 maya 手型文件，则建议将 unity 向下扩展到0.6。

![示例： Maya 中的](images/HandCoach/MayaExample.png) 手型测试机组<br>
*Rigged*

### <a name="technical-specs"></a>技术规格

*   Maya Ascii 格式提供两个文件
*    Right 和左手提供 Maya 二进制格式
*   将 Maya 文件设置为 24 FPS
*   在该文件中，有一个左手的右手，可用于两个右手或单直接手势。 仅在默认情况下，才会显示右手。
*   建议在淡化的开头和结尾留出大约10帧的缓冲区
*   如果对具有指定目标的对象进行动画处理，则其最佳方案为动态到默认框或 Null。
*   如果要对物理对象（例如 box）进行动画处理，最佳做法是不在 Maya 中对转换进行动画处理，而是等待在 Unity 中或代码中对其进行动画处理。
*   对于要传达的任何有意义的信息，可见动画应为1.5 秒
*   如果你对动画感到满意：
    *   选择所有接头和制作关键帧
    *   删除控制器，选择接头和网格，并将其导出为 FBX
    *  如果有多个动画，可以使用 Maya 的内置游戏导出程序： https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>从 Maya 导出

对动画满意后
* 选择所有接头：选择 > 层次结构

     ![示例：菜单位置](images/HandCoach/Hierarchy.png)<br>
* 制作动画：切换到动画 > 键 > 制作动画

     ![示例：菜单位置](images/HandCoach/BakeAnimation.png)<br>
* 删除控制器远程测试机组： Outliner > MainR_Grp 或 MainL_Grp

     ![示例：菜单位置](images/HandCoach/ControllerRig.png)<br>

* 导出为 FBX：选择 .JNT + 网格： File > 导出选定内容（选项框） > 导出选定内容

     ![示例：菜单位置](images/HandCoach/OptionBox.png)<br>

     ![示例：菜单位置](images/HandCoach/SelectionExport.png)<br>

     ![示例：菜单位置](images/HandCoach/FBXSelection.png)<br>


 导出为 FBX 并将其放入 Unity 时，将指针向下缩放到0.6。 我们发现这非常适合显示手。 

![示例： Unity 设置](images/HandCoach/HandHintScale.png)<br>
*在 MRTK 中找到 HandCoach_R prefab 的 Unity 设置*


## <a name="implementing-hands-into-your-unity-project"></a>实现对 Unity 项目的动手

### <a name="best-practices"></a>最佳实践
*    建议将 unity 向下扩展到0。6
*   应播放两次，如果未完成，则连续循环，直到手势完成。 应循环访问两次，以确保用户有时间注册并查看手势。 指针应在循环之间淡入和淡出。 
 *  如果用户的手在 HL2 摄像头中可见，但用户并未执行所需的交互操作，则会在10秒后出现。
*   如果 HL2 照相机看不到用户的手，则会在5秒后出现指针。  
*   如果动画中间的 HL2 相机明显跟踪用户的手，动画将完成并淡出。
*   如果要包括语音，则建议将其对应于手的手势。
*   如果你至少已经教授了一次，只需在其检测到用户停滞的情况下重复该笔势。
*   如果特定的 finger 位置是关键的，请确保用户可以清楚地查看动画中的这些差异。 尝试右倾，以清楚地显示最重要的部分。 
* 如果你注意到了手上的扭曲，则需要转为 Unity 的质量设置来增加骨骼量。 
 请参阅 Unity 的编辑 > 项目设置 > Quality > 其他 > Blend 权重。 请确保选择 "4 骨骼" 以查看平滑联接。 

   ![示例：菜单位置](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a>要避免的情况
* 将指针放大太大
* 将指针放在靠近用户的附近
* 只需教授一次。 优于教授会导致混淆和麻烦
*   将它引入 Unity，请在此处下载最新的 MRTK： https://github.com/microsoft/MixedRealityToolkit-Unity
    *   材料： Teaching_Hand2
    *   脚本：请参阅<a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">MRTK 手型指导</a>的 MRTK 准则
    *   每项目设置
        *   场景设置为 UWP：可在[配置 Unity 项目](Configure-Unity-Project.md)中找到 Windows Mixed Reality 的说明

## <a name="see-also"></a>另请参阅
* [交互-基础](interaction-fundamentals.md)
* [资产创建过程](asset-creation-process.md)
* [手势](gestures.md)
* [安装工具](install-the-tools.md)
* [配置 Unity 项目](Configure-Unity-Project.md)
* [Unity 开发概述](unity-development-overview.md)
* [MRTK 101](mrtk-101.md)
