---
title: MRTK 版本2入门
description: 对于对利用 MRTK 感兴趣的新开发人员
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, 测试, 混合现实工具包, MRTK 版本 2, MRTK, 工具, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: c785498e1533b2117249d3b21952ff56190126c0
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937089"
---
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2 入门

## <a name="mrtk-getting-started-guide"></a>MRTK 入门指南
有关 MRTK V2 入门的信息, 请参阅[MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>什么是混合现实工具包 (MRTK)？
MRTK 是一种令人惊叹的开源工具包, 它是自2015首次发布后开始的, 并不是我们的开发人员社区的硬性工作, 而是目前为止。 过去3年来, 我们已听取开发人员社区的反馈, 并构建了 MRTK v2, 以考虑最大的问题。  

使用 Unity 的 MRTK v2 是适用于混合现实应用程序的开源跨平台开发工具包。  MRTK 版本2旨在加速开发面向 Microsoft HoloLens、Windows Mixed Reality 沉浸 (VR) 耳机和 OpenVR 平台的应用程序。 该项目旨在降低创建混合现实应用程序的门槛，并在我们共同成长的过程中回馈社区。 


有关详细信息, 请参阅[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。

## <a name="feature-areas"></a>功能区域

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="输入系统" width="105"> 输入系统 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="手动跟踪 (HoloLens 2)" width="105"> 手动跟踪 (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="目视跟踪 (HoloLens 2)" width="105">
    目视跟踪 (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="语音命令" width="105"> 语音命令
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="注视 + Select (HoloLens (第一代))" width="105">
    注视 + Select (HoloLens (第一代))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> Teleportation
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI 控件" width="105"> UI 控件
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="规划求解和交互" width="105"> 规划求解和交互
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="控制器可视化" width="105"> 控制器可视化
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="空间理解" width="105"> 空间理解
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="诊断工具" width="105"> 诊断工具
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 标准着色器" width="105"> MRTK 标准着色器
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>UI 和交互构建基块

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Button" width="250"><br>
    **Button**<br>
    支持各种输入法 (包括 HoloLens 2 的有向右说明) 的 button 控件<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="边界框" width="250"><br>
    **边界框**<br>
    用于在三维空间中操作对象的标准 UI<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作处理程序" width="250"><br>
    **操作处理程序**<br>
    用一或两次手操作对象的脚本<a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="盖板" width="250"><br>
    **盖板** <br>
    支持用有向右输入滚动的2D 样式平面<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="系统键盘" width="250"><br>
    **系统键盘**<br>
    在 Unity 中使用系统键盘的示例脚本<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="种不可交互" width="250"><br>
     **种不可交互** <br>
     用于使对象种不可交互可视状态和主题支持的脚本<a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="求" width="250"><br>
    **求** <br>
    各种对象定位行为, 如标记、正文锁定、常量视图大小和表面磁性<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="对象集合" width="250"><br>
    **对象集合**<br>
    用于在三维形状中布局对象数组的脚本<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="工具提示" width="250">  <br>
    **提示**<br>
    具有灵活的定位点/透视系统的批注 UI, 可用于标记运动控制器和对象<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="应用栏" width="250"><br>
    **应用栏**<br>
    边界框手动激活的 UI<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="指针" width="250"><br>
    **指针**<br>
    了解各种类型的指针<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="手指可视化" width="250"><br>
     **手指可视化**<br>
     手指上的视觉对象 affordance, 可改善直接交互的置信度<a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    **滑块**<br>
    用于调整支持直接跟踪交互的值的滑块 UI<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 标准着色器" width="250"><br>
    **MRTK 标准着色器**<br>
    MRTK 的标准着色器支持各种流畅的设计元素和性能<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手型接点 Chaser" width="250"><br>
     **手型接点 Chaser**<br>
     演示如何使用规划求解将对象附加到手中<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="目视跟踪:目标选择" width="250"><br>
    **目视跟踪:目标选择**<br>
    将眼睛、语音和手写输入与您的场景一起快速轻松地选择全息影像<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="目视跟踪:导航" width="250"><br>
    **目视跟踪:导航**<br>
    了解如何根据要查看的内容自动滚动文本或流畅地缩放到聚焦内容<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="目视跟踪:热度地图" width="250"><br>
    **目视跟踪:热度地图**<br>
    记录、加载和可视化用户在应用中查看的内容的示例<a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>MRTK v2 的最低要求
* Unity 2018。4
* Microsoft Visual Studio 2017 或更高版本
* Windows SDK 18362 + 
* Windows 10 1803 或更高版本

## <a name="new-with-mrtk-v2"></a>新的 MRTK v2
我们想要对这些平台工具的承诺施加压力。  事实上, 我们利用 MRTK 版本2来开发收件箱体验, 例如安装体验 (OOBE) 和混合现实学习应用程序。  你还可以看到新的 HoloLens 2 功能首次通过 MRTK 公开, 因为我们认为这是在我们的平台上进行开发的最佳方式。 

### <a name="modular"></a>模块化
我们采用模块化方式构建了它, 因此您无需将该工具包的每个套件都引入到您的项目中。  这样做实际上只有几个优点。  它可以使项目大小保持较小, 并使其更易于管理。  基于这一点, 因为它是用可编写脚本的对象构建的, 并且是接口驱动的, 所以还可以替换您自己的组件, 以支持其他服务、系统和平台。


### <a name="cross-platform"></a>跨平台
说到其他平台, 它具有跨平台支持。  虽然这并不意味着每个平台都受支持, 但我们确保在将生成目标切换到其他平台时, 不会中断任何工具包代码。  模块化设计的可靠性和扩展性使你能够支持多个平台, 如 ARCore、ARKit 和 OpenVR。


### <a name="performant"></a>高性能
使用移动平台时, 我们构建了性能方面的考虑因素。  这非常重要, 我们想要确保这些工具不会与你一起工作。


## <a name="see-also"></a>请参阅
* [MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 文档主页](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [安装工具](install-the-tools.md)
* [从 HTK/MRTK 迁移到 MRTK 版本2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
