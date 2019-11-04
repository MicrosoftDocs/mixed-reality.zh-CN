---
title: 感到
description: 在自然查看过程中，人机视觉对象系统依赖多个信息源或 "提示" 来解释三维形状和对象的相对位置。
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: 混合现实，设计，舒适，HoloLens 2，HoloLens （第一代）
ms.openlocfilehash: e71b8d73a37a5d10a07d37d91cf14c88b7a85687
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436382"
---
# <a name="comfort"></a>感到

在自然查看过程中，人为视觉系统依赖多个信息源或 "提示" 来解释三维形状和对象的相对位置。 某些提示仅依赖于单个眼睛（monocular 提示），包括[线性透视](https://en.wikipedia.org/wiki/Perspective_(graphical))、[熟悉的大小](https://en.wikipedia.org/wiki/Size#Perception_of_size)、封闭、[深度字段模糊](https://en.wikipedia.org/wiki/Depth_of_field)和[便利设施](https://en.wikipedia.org/wiki/Accommodation_(eye))。 其他提示依赖于这两个眼睛（望远镜提示），并包括[vergence](https://en.wikipedia.org/wiki/Vergence) （实质上是查看对象所需的眼睛的相对旋转）和[望远镜差异](https://en.wikipedia.org/wiki/Stereopsis)（场景两个眼睛的背面。 为了确保头戴式显示器的舒适度最佳，设计人员和开发人员务必需要以一种模拟这些提示如何在自然世界中运行的方式来创建和展示内容。 从物理角度来看，设计不需要 fatiguing 或扶手的运动的内容也很重要。 在本文中，我们将继续考虑重要的注意事项，以实现这些目标。

## <a name="vergence-accommodation-conflict"></a>Vergence-住宿冲突

若要清楚地查看对象，人们必须[适应](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)对象的距离，或调整其眼睛。 同时，两种眼睛的旋转必须[收敛](https://en.wikipedia.org/wiki/Convergence_(eye))到对象的距离，以避免出现双图像。 在自然查看中，vergence 和住宿的链接。 查看附近的内容（例如，靠近鼻子的 housefly）时，眼睛交叉并适应近点。 相反，如果你查看的是光无穷（大致从6分钟开始，到一般视觉对象），眼睛就会变得平行，你的眼睛重用功能区会无限大。 

在大多数 head 装载的显示屏中，用户将始终适应显示器的焦距距离（以获取清晰的图像），但会收敛到对象的距离（以获取单个图像）。 当用户容纳并聚合到不同的距离时，两个提示之间的自然链接必须中断，这可能会导致 visual discomfort 或疲劳。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="guidance-for-holographic-devices"></a>全息设备指南

HoloLens 显示的固定速度是远离用户的光学距离。 因此，用户必须始终适应2.0 版，才能在设备上维护清晰的映像。 应用程序开发人员可以通过在不同的深度放置内容和全息影像来指导用户的眼睛汇聚。 可以通过保留用户最接近 2.0 m 的内容来避免或最大限度地减少 Discomfort 的 vergence （即，在具有很多深度的场景中，将用户感兴趣的领域置于用户附近）。 如果内容不能放置在 2.0 m 附近，则当用户的 discomfort 在不同距离之间来回切换时，vergence 冲突的情况最大。 换而言之，看看50cm 的静止全息图比查看一段时间内远离你的全息图50cm 更容易。

为用户放置全息影像 ![最佳距离。](images/distanceguiderendering-950px.png)<br>
*从用户处放置全息影像的最佳距离*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>HoloLens （第一代）和 HoloLens 2 的最佳实践

为了最大限度**地提高其位置，全息图位置的最佳区域介于 1.25 m 和5分钟之间**。 在每种情况下，设计人员应尝试构建内容场景，以鼓励用户与内容交互（例如，调整[内容大小和默认位置参数](gaze-and-commit.md)）。 

尽管内容有时可能需要比1m 更近的显示，但我们建议不要将全息影像呈现为比40cm 更近的内容。 因此，我们建议开始在**40cm 上淡化内容，并在30cm 上放置渲染修剪平面**，以避免任何接近的对象。

由于 vergence 冲突，移到深度的对象更有可能不是要生成 discomfort 的静止对象。 同样，要求用户在接近焦点和远关注点（例如，由于需要直接交互的弹出全息图）之间快速切换可能会导致视觉对象 discomfort 和疲劳。 因此，**为了最大限度地减少用户的频率，应特别小心：查看深入了解的内容; 或在近距离和远距离全息影像之间快速切换焦点**。 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>HoloLens 2 和接近交互距离的其他注意事项

在为 HoloLens 2 中的直接（近乎）交互设计内容时，或**在任何内容必须位于1m 附近的应用程序中，应特别小心以确保用户舒适**。 由于 vergence 的出现冲突，discomfort 的可能性会随着查看距离呈指数增加而降低。 此外，在接近交互距离查看内容时，用户可能会遇到增加的模糊，因此，我们建议测试在最佳全息图放置区域内呈现的内容，并将更近请确保它在查看时保持简洁明了。 

**建议为应用创建 "深度预算"，具体取决于用户期望查看接近（小于 1.0 m m）的内容和深度移动的时间**。 例如，避免在超过25% 的时间将用户放在这种情况下。 如果超出了深度预算，我们建议仔细进行用户测试，以确保它仍具有舒适的体验。 

通常，我们还建议进行仔细的测试，以确保接近交互距离的任何交互要求（例如，移动速度、可访问性等）都适合用户。 


### <a name="guidance-for-immersive-devices"></a>沉浸式设备指南

对于沉浸式设备，还适用于 HoloLens 的指导原则和最佳做法，但会根据与显示器的焦距距离来移动。 通常，与这些显示器的焦距介于 1.25 m-2.5 m 之间。 如果有疑问，请避免向用户显示感兴趣的对象，而是尝试将大多数内容保留为1m 或更远。

## <a name="interpupillary-distance-and-vertical-offset"></a>Interpupillary 距离和垂直偏移

查看 head 安装的显示屏上的数字内容时（HMD），查看者的眼睛相对于数字内容的显示位置至关重要。 具体而言，interpupillary 距离（[IPD](https://en.wikipedia.org/wiki/Pupillary_distance)）和垂直偏移（VO）对于在 HMDs 中查看数字内容非常重要。 

IPD 指单个眼睛的瞳孔或中心之间的距离。 VO 是指相对于查看器眼睛水平轴的每个眼睛显示的数字内容的可能垂直偏移量（特别是，这不同于水平偏移或望远镜差异）。 对单个用户的任何一种或两种因素的误匹配可能会恶化 discomfort 造成的 vergence 的影响，但它甚至会导致 discomfort 的冲突降到最小（例如，针对 2.0 m 焦点显示的内容）HoloLens 的距离）。 

### <a name="guidance-for-holographic-devices"></a>全息设备指南

#### <a name="hololens-1st-gen"></a>HoloLens（第 1 代）

对于 HoloLens （第一代），IPD 是在设备[校准](calibration.md)期间进行预估和设置的。 对于已设置的设备的新用户，必须运行校准或手动设置 IPD。 VO 完全取决于设备。 具体而言，若要最大程度地减少 VO，设备需要停留在用户的头上，以便显示的是其眼睛的轴。 

#### <a name="hololens-2"></a>HoloLens 2

对于 HoloLens 2，IPD 是在目视/设备[校准](calibration.md)期间进行预估和设置的。 对于已设置的设备的新用户，必须运行校准以确保正确设置 IPD。 在 HoloLens 2 中自动考虑了 VO。 

### <a name="guidance-for-immersive-devices"></a>沉浸式设备指南

Windows Mixed Reality 沉浸式 HMDs 对于 IPD 或 VO 没有自动校准。 IPD 可以在软件中手动设置（在混合现实门户设置下，请参阅[校准](calibration.md)），或某些 HMDs 具有机械滑块，用户可以使用该滑块将重用功能区的间距调整到舒适的位置（即，大致匹配其 IPD）。 

## <a name="rendering-rates"></a>呈现速率

混合现实应用是独一无二的，因为用户可以在世界各地自由移动，并与虚拟内容交互，就像它们是真实的对象一样。 若要维护这种印象，呈现全息影像非常重要，使其在世界上显得稳定并平滑。 [每秒至少60帧（FPS）的](understanding-performance-for-mixed-reality.md)渲染有助于实现此目标。 有些混合现实设备支持在 framerates 高于 60 FPS 的情况呈现，因此，强烈建议在更高的 framerates 上呈现，以提供最佳的用户体验。

**深入探讨**

若要绘制影像，使其看起来像[是在真实或虚拟世界中稳定](hologram-stability.md)的，应用程序需要从用户的位置呈现图像。 由于图像渲染需要时间，HoloLens 和其他 Windows Mixed Reality 设备将预测用户在显示器中显示图像的位置。 此预测算法是近似值。 Windows Mixed Reality 算法和硬件调整呈现的图像，以考虑预测的头位置与实际 head 位置之间的差异。 此过程会使用户看到的图像看起来就像是从正确的位置呈现的，全息影像看起来是稳定的。 这些更新最适合用于头位置的小更改，因此它们不能完全考虑某些呈现的图像差异，如视差。

**通过以 60 FPS 的最小帧速率进行渲染，你可以执行以下两项操作来帮助实现稳定的全息影像：**
1. 减少 judder 的外观，其特征是不均匀的运动和双图像。 更快的全息图运动和更小的呈现速率与更明显的 judder 相关联。 因此，努力始终维护 60 FPS （或设备的最大呈现速率）可帮助避免 judder 移动全息影像。
2. 最大程度地降低总体延迟。 在具有游戏线程的引擎和在一脉相承中运行的渲染线程中，在30FPS 上运行会添加 33.3 ms 的额外延迟。 通过减少延迟，这会减少预测误差，并增加全息影像的稳定性。

**性能分析**

可以使用多种工具来基准应用程序帧速率，如：
* GPUView
* Visual Studio 图形调试器
* 内置于三维引擎中的探查器，例如 Unity 中的帧调试器

## <a name="self-motion-and-user-locomotion"></a>自移动和用户 locomotion

唯一的限制是物理空间的大小;如果要允许用户在虚拟环境中的移动距离在其实际房间内的距离，则必须实现纯虚运动的形式。 但是，与用户实际动作并不匹配的持续的虚拟运动通常会 sickness 运动。 出现这种结果是因为，来自*虚拟世界*的的*可视提示*与来自*现实世界*的自我运动的[vestibular 提示](https://en.wikipedia.org/wiki/Vestibular_system)冲突。

幸运的是，有一些用于实现可帮助避免此问题的用户 locomotion 的技巧：
* 始终使用户控制其移动;意外的自我运动特别有问题
* 人类对重力方向非常敏感。 因此，特别应避免非用户启动的垂直动作。

### <a name="guidance-for-holographic-devices"></a>全息设备指南

允许用户移动到大型虚拟环境中的其他位置的一种方法是，使他们能够在场景中移动小对象。 可以按如下所示实现此效果：
   1. 提供一个界面，用户可在其中选择要移动的虚拟环境中的一个位置。
   2. 选择后，将场景向下减小到围绕所需位置的磁盘。
   3. 保持选中状态时，允许用户将其作为小型对象移动。 然后，用户可以将所选内容移动到其垫脚附近。
   4. 在 deselection 时，恢复呈现整个场景。

### <a name="guidance-for-immersive-devices"></a>沉浸式设备指南

上述全息设备方法在沉浸式设备中也不起作用，因为它需要应用在移动 "磁盘" 的同时呈现大型黑色失效或其他默认环境。 此处理会破坏一浸入式的意义。 沉浸式耳机中用户 locomotion 的一项技巧是 "闪烁" 方法。 此实现为用户提供了对其运动的控制，并为移动提供了短暂的印象，但使用户非常简单，因为用户不太可能 disoriented 于纯粹的虚拟自运动：
   1. 提供一个界面，用户可在其中选择要移动的虚拟环境中的一个位置。
   2. 选择后，开始向该位置进行非常快速的模拟（100 m/s）动作，同时快速淡出渲染。
   3. 完成转换后，将呈现恢复回。

## <a name="heads-up-displays"></a>打印头显示

在射击 videogames 中，打印头会直接显示（HUDs）在屏幕上直接显示的信息，如播放机健康状况、小型地图和清单。 HUDs 可以很好地让播放机得到通知，而无需 intruding 游戏体验。 在混合现实体验中，HUDs 可能会导致重大 discomfort，并且必须适应更沉浸的上下文。 具体而言，严格锁定到用户头方向的 HUDs 可能会产生 discomfort。 如果某个应用需要 HUD，则建议使用*正文*锁定，而不是使用 head 锁定。 此处理可以作为一组显示来实现，这些显示器会立即与用户一起翻译，但不会随用户的头一起旋转，直到达到旋转阈值。 一旦实现了旋转，HUD 可能会重定向，以便在用户的视图字段中显示信息。 应始终避免实现与用户头运动相关的 1:1 HUD 旋转和平移。

## <a name="text-legibility"></a>文本清晰度

最佳文本清晰度有助于降低眼睛压力并维持用户舒适，尤其是在需要用户在 HMD 中阅读的应用程序或场景中。 文本清晰度取决于各种因素，包括各种显示属性（例如，像素密度、亮度、对比度）、镜头属性（例如 chromatic aberration）和文本/字体属性（例如，特定字体权重、间距、衬线等特征、字体颜色、背景颜色）。  

通常，我们建议测试特定的应用程序的可读性，并使字体大小尽可能大，使其能够获得舒适的体验。 下面我们提供了一般的指导作为开发起点。 请注意，所有字体大小都以[视觉角度](https://en.wikipedia.org/wiki/Visual_angle)（而不是特定的物理尺寸）来报告，这为该区域内的任何距离提供了指导，使其能够获得最佳全息图位置，因为它同时反映文本大小和距离显示到查看器。 

有关更详细的指南，请参阅[Unity 页面中](text-in-unity.md)的[版式](typography.md)和文本。

### <a name="guidance-for-holographic-devices"></a>全息设备指南

对于全息设备，在白色/浅色背景上呈现黑色/深色文本会提供最一致的对比度，因为背景会遮蔽在呈现后真实世界的干扰。 在黑色/深色背景上呈现白/浅文本允许显示更多真实环境，这可能会干扰文本清晰度。 

#### <a name="hololens-1st-gen"></a>HoloLens（第 1 代）

最小清晰字体大小（从字体基线到 ascender 的测量）约为0.35 °，舒适的字体大小至少为大约0.5 °，以便将以2m 为间距显示的内容读取到用户。 

#### <a name="hololens-2"></a>HoloLens 2

最小清晰字体大小（从字体基线度量到 ascender）至少为： 
   - 45cm 上0.4 °0.5 °（直接操作距离） 
   - 0.35 °0.4 ° at 2.0 m
   
可读性最高的字体（从字体基线到 ascender）的大小至少为： 
   - 0.65 °0.8 ° at 45cm （直接操作距离）
   - 0.6 °-0.75 ° at 2。0

请注意，由于前面所述的 vergence-住宿冲突，在直接操作距离的文本上，字体大小需要稍大一点（用户的眼睛在45cm 的情况下适应 2.0 m可能对用户显示更模糊。 

### <a name="guidance-for-immersive-devices"></a>沉浸式设备指南

沉浸式设备通常具有更高的对比度，因为在封闭的外部环境中，它的对比度可能较低，但部分中的像素密度可能会下降，因为显示器正面重用功能区的放大。 

对于 Windows Mixed Reality 沉浸式 HMDs，最小清晰的垂直字体大小（从字体基线到 ascender 的度量）约为 0.7-0.9 °，且舒适的垂直字体大小约为1。0用户.

## <a name="gaze-direction"></a>注视方向

为了避免出现眼睛和颈部紧张的内容，应避免过多的眼睛和颈部运动。
* **避免**在地平线上方大于10度的注视角度（垂直移动）
* **避免**在地平线下方60度以上
* **避免**将颈部旋转大于45度-中心（水平移动）

最佳（静止）看，将被视为低于水平的10-20 度，因为 head 会略微向下倾斜，尤其是在活动期间。

![允许的视图字段（FOV），由颈部运动范围确定](images/optimal-field-of-view-2.png)<br>
*由颈部运动范围确定的允许的视图字段（FOV）*

## <a name="arm-positions"></a>Arm 位置

当预计用户需要在一段时间内就会引发一则判断力疲劳。 它还可 fatiguing，要求用户在长时间内反复进行分流手势。 因此，我们建议体验避免需要重复的重复笔势输入。 此目标可通过以下方式实现：引入短暂的中断，或者提供一种混合手势和语音输入来与应用程序进行交互。

## <a name="see-also"></a>另请参阅
* [凝视](gaze-and-commit.md)
* [全息影像稳定性](hologram-stability.md)
* [本能交互](interaction-fundamentals.md)
* [全息帧](holographic-frame.md)
* [校准](calibration.md)
