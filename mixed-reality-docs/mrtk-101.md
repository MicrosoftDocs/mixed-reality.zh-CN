---
title: MRTK 101 - 如何使用混合现实工具包 Unity 进行基本的交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
description: 如何使用混合现实工具包 Unity 进行基本的交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, 混合现实工具包, Windows Mixed Reality, 设计, 示例应用, 控件
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028314"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101：如何使用混合现实工具包 Unity 进行基本的交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）

![MRTK](images/MRTK101/MRTK101Cover.png)

了解如何使用 MRTK 在混合现实中实现最常用的交互模式。

- 如何在 Unity 编辑器中模拟输入交互？
- 如何抓取和移动对象？
- 如何调整对象的大小？
- 如何精确移动或旋转对象？
- 如何使对象响应输入事件？
- 如何添加视觉反馈？
- 如何添加音频反馈？
- 如何使用 HoloLens 2 样式按钮预制件？
- 如何使对象跟随你？
- 如何使对象朝向你？

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>如何在 Unity 编辑器中模拟输入交互？
MRTK 支持编辑器中的输入模拟。 只需单击 Unity 的播放按钮即可运行场景。 请使用这些键来模拟输入。
按 W、A、S、D 键可移动相机。
在按住鼠标右键的同时移动鼠标可以四处浏览。
若要显示模拟手形图标，请按空格键（右手）或左 Shift 键（左手）。若要在视图中保留模拟手形图标，请按 T 或 Y 键。若要旋转模拟手形图标，请按 Q 或 E（水平旋转）/R 或 F（垂直旋转）

- [在 MRTK 文档中详细了解输入模拟](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>如何抓取和移动对象？
若要使对象可抓取，请分配以下两个脚本：ManipulationHandler.cs 和 NearInteractionGrabbable.cs（根据精确手动跟踪输入直接抓取）。ManipulationHandler 支持近距交互和远距交互。 可以使用 HoloLens 2 的精确手动跟踪输入（近距）、手部射线（远距）、运动控制器光束（远距）、HoloLens 凝视光标和隔空敲击（远距）来抓取和移动对象。

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>如何调整对象的大小？
ManipulationHandler.cs 支持双手缩放/旋转。 此功能适用于各种输入类型，例如 HoloLens 2 的精确手动输入、HoloLens 1 的凝视 + 手势输入，以及 Windows Mixed Reality 沉浸式头戴显示设备的运动控制器输入。

- [在 MRTK 文档中详细了解操作处理程序](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>如何精确移动或旋转对象？
将 BoundingBox.cs 分配到某个对象以使用边界框（用于缩放和旋转对象的界面）。 默认情况下，该脚本会显示 HoloLens 1 样式的蓝色控点和线条。 若要使用基于 HoloLens 2 样式邻近性的动画控点，需要分配预制件和材料。 有关配置详细信息，请参阅[边界框文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)和 BoundingBoxExamples.unity 场景。

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [在 MRTK 文档中详细了解边界框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>如何使对象响应输入事件？
将 PointerHandler.cs 分配到某个对象。 在检查器中，可以使用事件 OnPointerDown()、OnPointerUp()、OnPointerClicked() 和 OnPointerDragged()。若要在脚本中使用这些事件，请实现 IMixedRealityPointerHandler。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [在 MRTK 文档中详细了解输入系统](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>如何添加视觉反馈？
将 Interactable.cs 分配到某个对象。 在检查器中创建一个新主题。 使用 Interactable 的主题配置文件可以轻松将视觉反馈添加到所有可用的输入交互状态。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable 提供各种类型的主题，包括着色器主题，该主题可用于控制每种交互状态的着色器的属性。

- [在 MRTK 文档中详细了解 Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

视觉反馈的另一个重要构建基块是 MRTK 标准着色器。 使用 MRTK 标准着色器可以轻松添加视觉反馈效果，例如悬停光线和邻近光线。 由于 MRTK 标准着色器占用的计算资源要比 Unity 标准着色器少得多，因此你可以创建高性能的体验。

创建新材料，然后选择着色器的“混合现实工具包”>“标准”。 或者，可以选择某个使用 MRTK 标准着色器的现有材料。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [在 MRTK 文档中详细了解 MRTK 标准着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>如何添加音频反馈？
将 AudioSource 添加到某个对象。 然后，在公开输入事件的脚本（例如 Interactable.cs 或 PointerHandler.cs）中，将该对象分配到该事件，并选择“AudioSource.PlayOneShot()”。 可以使用自己的音频剪辑，或从 MRTK 的音频资产中进行选择。

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>如何使用 HoloLens 2 样式按钮预制件？
MRTK 提供各种类型的 HoloLens 2 shell (OS) 样式按钮。 它可以在按钮表面上提供复杂的视觉反馈，例如邻近光线、压缩框和波纹效果。

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

只需将某个 HoloLens 2 样式的可按按钮预制件拖放到场景中即可。 该预制件将使用前面介绍的 Interactable.cs。 可以使用 Interactable 中公开的事件（例如 OnClick()）来触发操作。

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [在 MRTK 文档中详细了解按钮预制件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>如何使对象跟随你？
将 RadialView.cs 脚本分配到某个对象。 此脚本是解算器脚本系列的一部分，可用于在 3D 空间中实现各种类型的对象定位。 将自动添加 SolverHandler.cs。
下面是 RadialView 配置的一个示例，它可以实现“惰性跟踪”追随行为，就如同使用 HoloLens shell 中的“开始”菜单一样。 可以指定最小/最大距离和最小/最大视图角度。 以下示例演示如何在 0.4 到 0.8 米范围内以 15° 的视图角度定位对象。 调整“线性插值时间”值，以加快或减慢定位更新的速度。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [在 MRTK 文档中详细了解解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>如何使对象朝向你？
将 Billboard.cs 脚本分配到某个对象。 不管你处于哪个位置，该对象都会朝向你。 可以指定枢轴选项。

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


准备好创建令人惊叹的混合现实体验了吗？ 请访问以下页面来详细了解 MRTK 和混合现实。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>用户体验设计师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅

* [混合现实工具包 - Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [MRTK 入门](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HoloToolkit 到 MRTK 的移植指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
