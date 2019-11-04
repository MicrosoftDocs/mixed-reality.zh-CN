---
title: MRTK 101-如何将混合现实工具包 Unity 用于基本交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
description: 如何将混合现实工具包 Unity 用于基本交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens，MRTK，混合现实工具包，Windows Mixed Reality，设计，示例应用，控件
ms.openlocfilehash: 95c81442cc390da8ac7c9a8de218341cb5e7c948
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439648"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101：如何将混合现实工具包 Unity 用于基本交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）

![MRTK](images/MRTK101/MRTK101Cover.png)

了解如何使用 MRTK 在混合现实中实现最广泛使用的常见交互模式。

- 如何在 Unity 编辑器中模拟输入交互？
- 如何获取和移动对象？
- 如何调整对象的大小？
- 如何以精确方式移动或旋转对象？
- 如何使对象响应输入事件？
- 如何添加视觉反馈？
- 如何添加音频反馈？
- 如何使用 HoloLens 2 样式按钮 prototyping？
- 如何使对象符合您的需要？
- 如何制作对象？

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>如何在 Unity 编辑器中模拟输入交互？
MRTK 支持编辑器内输入模拟。 只需单击 Unity 的 "播放" 按钮即可运行场景。 使用这些密钥来模拟输入。
按 W、A、S、D 键移动相机。
按住鼠标右键，并移动鼠标以进行浏览。
若要启动模拟的操作，请按空格键（右手）或左移键（左移）以在视图中继续模拟，按 T 或 Y 键旋转模拟手势，按 Q 或 E （水平）

- [在 MRTK 文档中了解有关输入模拟的详细信息](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>如何获取和移动对象？
若要使对象 grabbable，请分配以下两个脚本： ManipulationHandler.cs 和 NearInteractionGrabbable （对于带有清晰的手动跟踪输入的直接抓取） ManipulationHandler 同时支持近距离和远距离交互。 您可以使用 HoloLens 2 的可表述的手动跟踪输入（附近）、一种手 ray （far）、运动控制器的无线横梁（far）、HoloLens 注视光标 & 的空中点来获取和移动对象。

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>如何调整对象的大小？
ManipulationHandler.cs 支持双向缩放/旋转。 这适用于各种输入类型，例如，HoloLens 2 的有向右输入、HoloLens 1 的注视 + 手势输入和 Windows Mixed Reality 沉浸式耳机的运动控制器输入。

- [在 MRTK 文档中详细了解操作处理程序](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>如何以精确方式移动或旋转对象？
将 BoundingBox.cs 分配给对象以使用边界框，这是用于缩放和旋转对象的接口。 默认情况下，它会显示1个 HoloLens 样式的蓝色控点和线路。 若要使用基于的 HoloLens 2 样式邻近动画句柄，需要分配 prototyping 和材料。 有关配置详细信息，请参阅边界框文档和 BoundingBoxExamples 场景。

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [在 MRTK 文档中了解有关边界框的详细信息](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>如何使对象响应输入事件？
将 PointerHandler.cs 分配给对象。 在检查器中，你将能够使用事件 OnPointerDown （）、OnPointerUp （）、OnPointerClicked （）、OnPointerDragged （）在脚本中使用这些事件，实现 IMixedRealityPointerHandler。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [在 MRTK 文档中了解有关输入系统的详细信息](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>如何添加视觉反馈？
将 Interactable.cs 分配给对象。 在检查器中创建一个新主题。 使用种不可交互的主题配置文件，你可以轻松地将视觉反馈添加到所有可用的输入交互状态。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


种不可交互提供各种类型的主题，其中包括着色器主题，可用于控制每个交互状态着色器的属性。

- [在 MRTK 文档中了解有关种不可交互的详细信息](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

用于可视反馈的另一个重要的构建基块是 MRTK 标准着色器。 借助 MRTK 标准着色器，你可以轻松地添加视觉对象反馈效果，如悬停光线和邻近性光线。 由于 MRTK 标准着色器比 Unity 标准着色器执行的计算要少得多，因此您可以创建性能良好的体验。

创建新的材料，并选择着色器的混合现实工具包 > 标准 "。 或者，您可以选择使用 MRTK 标准着色器的现有材料之一。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [有关 MRTK 标准着色器的详细信息，请参阅 MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>如何添加音频反馈？
将 AudioSource 添加到对象。 然后，在公开输入事件的脚本（例如 Interactable.cs 或 PointerHandler.cs）中，将对象分配给该事件，并选择 AudioSource。 PlayOneShot （）。 可以使用音频剪辑，或从 MRTK 的音频资产中进行选择。

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>如何使用 HoloLens 2 样式按钮 prototyping？
MRTK 提供各种类型的 HoloLens 2 shell （OS）样式按钮。 它提供了复杂的视觉对象反馈，例如邻近感应、压缩框和按钮表面上的波纹效果。

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

只需将其中一个 HoloLens 2 样式的 pressable 按钮拖放到场景中即可。 Prefab 使用上面介绍的 Interactable.cs。 可以在种不可交互中使用已公开的事件（如 OnClick （））来触发操作。

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [在 MRTK 文档中了解有关按钮 prototyping 的详细信息](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>如何使对象符合您的需要？
将 RadialView.cs 脚本分配给对象。 它是规划求解脚本系列的一部分，可用于在三维空间中实现各种类型的对象定位。 将自动添加 SolverHandler.cs。
下面是 RadialView 配置的一个示例，用于实现 "延迟跟随" 标记和操作，就像使用 HoloLens shell 中的 "开始" 菜单。 您可以指定最小/最大距离和最小/最大视图度。 下面的示例演示了如何在15°内将对象放置在 0.4 m 和 0.8 m 范围之间。 调整 Lerp 时间值，以使位置更新速度更快或更慢。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [在 MRTK 文档中了解有关 Solvers 的详细信息](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>如何制作对象？
将 Billboard.cs 脚本分配给对象。 无论您的位置如何，都将始终面对您。 您可以指定 "轴" 选项。

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


准备好为混合现实创建令人惊叹的体验？ 访问以下页面，了解有关 MRTK 和混合现实的详细信息。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon 停车场</b><br>UX 设计器 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅

* [混合现实工具包-Unity （MRTK） GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [入门与 MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HoloToolkit to MRTK 移植指导原则](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
