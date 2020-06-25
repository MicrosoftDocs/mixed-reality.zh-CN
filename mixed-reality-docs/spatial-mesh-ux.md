---
title: 空间网格可视化
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合现实，HoloLens，UI 控件，交互，UI，ux，UX 设计，空间 UI，空间交互，3D UI，三维 UX
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346100"
---
# <a name="spatial-mesh"></a>空间网格

![空间网格](images/UX/MRTK_PulseShader_SpatialMesh.gif)

通过空间网格可视化，用户可以了解设备如何感觉并了解物理环境。 除了提供空间上下文，适当的空间网格可视化还可以创建不知和神奇体验。  

## <a name="design-guideline"></a>设计准则
由于使用户能够专注于内容并与之交互非常重要，因此，背景中的空间网格的连续和重复的可视化效果可能会分散注意力。 建议你慎用环境，只是在初始启动时，或者当用户通过定位和轻攻区来查看环境网格时出现清楚的意图。 您可以在 HoloLens shell 中观察到此行为。
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>适用于 Unity 的 MRTK （混合现实工具包）中的空间网格可视化
MRTK 提供了多个材料来实现空间网格可视化。

- **MRTK_Wireframe，MRTK_Wireframe**的：默认静态空间网格材料，它显示网格轮廓而不显示动画。 此材料可用于调试目的，因为它显示了整个空间网格几何。 但是，不建议在生产环境中使用。
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction**材料：此材料在空间网格上提供动画脉冲效果。 你可以使用此材料在你的体验的特定时刻或用户的点击输入中直观显示环境。 有关示例，请参阅**PulseShaderExamples**场景。
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* 有关更多详细信息，请参阅[MRTK-空间感知](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html)和[MRTK 着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html)。

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
