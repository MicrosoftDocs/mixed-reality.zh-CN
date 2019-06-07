---
title: 开始使用 MRTK 版本 2
description: 新开发人员感兴趣利用 MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality 测试，混合现实工具包、 MRTK 版本 2、 MRTK、 工具、 SDK、 HoloLens、 HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750363"
---
# <a name="getting-started-with-mrtk-v2"></a>开始使用 MRTK v2

## <a name="mrtk-getting-started-guide"></a>MRTK 入门指南
请参阅[MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)有关如何开始使用 MRTK V2 的信息。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>什么是混合现实工具包 (MRTK)？
MRTK 是令人惊叹的开放源代码工具包，以来已经过围绕 HoloLens 首次发布，并且不会目前的状况而无需我们的开发人员社区向其提供了大量工作。 在过去 3 年中，我们有侦听到我们的开发人员社区的反馈，并生成 MRTK v2 要着重考虑的最大的问题。  

使用 Unity MRTK v2 是混合的现实应用程序的一个开放源代码跨平台开发工具包。  MRTK 版本 2 旨在加速开发针对 Microsoft HoloLens，Windows Mixed Reality 沉浸式 (VR) 耳机，以及 OpenVR 平台的应用程序。 项目功能旨在减少到条目创建混合的现实应用程序并提供回社区，随着我们所有的发展的障碍。 


请参阅[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)若要了解详细信息。

## <a name="feature-areas"></a>功能区

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="在输入的系统" width="105"> 在输入的系统 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="手动跟踪 (HoloLens 2)" width="105"> 手动跟踪 (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="眼睛追踪 (HoloLens 2)" width="105">
    眼睛追踪 (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="语音命令" width="105"> 语音命令
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="注视 + 选择 (HoloLens （第 1 代）)" width="105">
    注视 + 选择 (HoloLens （第 1 代）)
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
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="解算器和交互" width="105"> 解算器和交互
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="控制器可视化效果" width="105"> 控制器可视化效果
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="空间了解" width="105"> 空间了解
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
    一个按钮控件，它支持各种输入的方法包括 HoloLens 2 明确的手 <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="边界框" width="250"><br>
    **边界框**<br>
    用于处理 3D 空间中的对象的标准用户界面 <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作处理程序" width="250"><br>
    **操作处理程序**<br>
    用于操作具有一个或两个指针的对象的脚本 <a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="静态图像" width="250"><br>
    **静态图像** <br>
    2D 样式平面支持滚动明确的手动输入 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="系统键盘" width="250"><br>
    **系统键盘**<br>
    在 Unity 中使用系统键盘的示例脚本 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="种交互" width="250"><br>
     **Interactable** <br>
     用于使对象的可视状态和主题支持使用种交互的脚本 <a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="解算器" width="250"><br>
    **Solver** <br>
    各种对象定位行为，例如尾随、 正文锁、 常量视图大小和图面消除 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="对象集合" width="250"><br>
    **对象集合**<br>
    在三维形状中的对象的数组布局的脚本 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="工具提示" width="250">  <br>
    **Tooltip**<br>
    批注 UI 与灵活的定位点/枢轴系统可用于标记运动控制器和对象 <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="应用栏" width="250"><br>
    **App Bar**<br>
    边界框手动激活的用户界面 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="指针" width="250"><br>
    **指针**<br>
    了解有关各种类型的指针 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="指尖可视化效果" width="250"><br>
     **指尖可视化效果**<br>
     这将提高直接交互的置信度指尖上可视化功能的可见性： <a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    **滑块**<br>
    用于调整滑块 UI 值支持直接手动跟踪交互 <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 标准着色器" width="250"><br>
    **MRTK 标准着色器**<br>
    MRTK 的标准着色器支持与性能的各种 Fluent 设计元素 <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手联合 Chaser" width="250"><br>
     **手联合 Chaser**<br>
     演示如何使用解算器将对象附加到的现有连接 <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="眼睛追踪：选择目标" width="250"><br>
    **眼睛追踪：选择目标**<br>
    结合使用眼睛、 语音和手动输入快速高效地在您的场景之间选择全息 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="眼睛追踪：导航" width="250"><br>
    **眼睛追踪：导航**<br>
    了解如何自动滚动文本或流畅缩放到根据你正在查看的内容的已设定焦点内容 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="眼睛追踪：热度地图" width="250"><br>
    **眼睛追踪：热度地图**<br>
    有关日志记录的示例，加载和可视化的哪些用户已经了解了应用程序中 <a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>对于 MRTK v2 的最低要求
* Unity 2018.3.x
* Microsoft Visual Studio 2017 或更高版本
* Windows SDK 18362+ 
* Windows 10 1803年或更高版本

## <a name="new-with-mrtk-v2"></a>新功能 MRTK v2
我们想要强调我们对这些平台工具的承诺。  事实上，我们就利用了 MRTK 版本 2 开发我们收件箱的体验，例如安装体验 (OOBE) 和混合现实学习应用程序。  则可能要查看新 HoloLens 2 功能通过 MRTK 首次公开，因为我们认为它是在我们的平台上进行开发的最佳方式。 

### <a name="modular"></a>采用模块化结构
以便不需要考虑该工具包的每一位到你的项目，我们有模块化方式，构建它。  有此实际几个优点。  它使您的项目规模较小，以及轻松地管理。  除此之外，因为它用可编写脚本的对象生成，并且驱动的界面，它还有可能更换附带你自己，以支持其他服务、 系统和平台的组件。


### <a name="cross-platform"></a>跨平台
说到其他平台，它提供了跨平台支持。  而这并不意味着每个单个平台支持的功能，我们已确保的工具包代码都不会中断生成目标切换到其他平台时。  可靠性和可扩展性的模块化设计设置您上能够支持多个平台，例如 ARCore、 ARKit，以及 OpenVR 的好方法。


### <a name="performant"></a>高性能
我们在使用的移动平台，构造它与性能方面的考虑。  这是非常重要，我们想要确保这些工具不会对您工作。


## <a name="see-also"></a>请参阅
* [MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 文档主页](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [安装工具](install-the-tools.md)
* [从 HTK/MRTK 移植到 MRTK 版本 2](mrtk-porting-guide.md)
