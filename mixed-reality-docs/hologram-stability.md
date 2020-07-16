---
title: 全息影像稳定性
description: HoloLens 自动稳定了全息影像，但开发人员可以进一步提高全息影像稳定性。
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: 全息影像，稳定性，hololens
appliesto:
- HoloLens
ms.openlocfilehash: 4a489c923138808e3afb545097c314f354b5ad2a
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408205"
---
# <a name="hologram-stability"></a>全息影像稳定性

## <a name="overview"></a>概述

为实现稳定的全息影像，HoloLens 提供内置的图像稳定性管道。 稳定管道在后台自动运行，因此不需要执行任何额外的步骤来启用它。 但是，您应运用改善全息影像稳定性的技术，避免降低稳定性的方案。

## <a name="hologram-quality-terminology"></a>全息影像质量术语

全息影像的质量是良好的环境和良好的应用程序开发。 在 HoloLens 可以跟踪周围的环境中，每秒在常量60帧上运行的应用可确保全息影像和匹配坐标系处于同步状态。从用户的角度来看，要保持静止的全息影像不会相对于环境移动。

以下术语可帮助你确定环境问题、不一致的呈现速率或任何其他内容。
* **准确性.** 在全局锁定全息图并将其放置在现实世界中后，它应保留相对于周围环境的位置，并独立于用户运动或小型和稀疏环境更改。 如果在意外的位置出现全息图，则这是一个*准确性*问题。 如果两个不同的房间看起来相同，则可能会发生这种情况。
* **抖动.** 用户将抖动视为全息图的高频握手，这在跟踪环境时可能会发生这种情况。 对于用户，解决方案正在运行[传感器调整](sensor-tuning.md)。
* **Judder.** 低渲染频率会导致动画的不均匀运动和双图像。 Judder 在动态影像中尤其明显。 开发人员需要维护[常量 60 FPS](hologram-stability.md#frame-rate)。
* **光标.** 用户在出现全息图后会看到偏移，使其远离其最初放置位置。 在离[空间锚](spatial-anchors.md)，而不是完全映射的环境部分中时，会发生偏移。 创建与空间锚接近的全息影像会降低偏移的可能性。
* **Jumpiness.** 如果不是，则不会偶尔从其位置 "弹出" 或 "跳转"。 当跟踪调整全息影像以匹配更新的环境时，会发生 Jumpiness。
* **泳道.** 当 sway 与用户的头运动相对应时，会出现一个全息图。 当应用程序未完全实现[reprojection](hologram-stability.md#reprojection)，并且没有为当前用户[校准](calibration.md)HoloLens 时，会发生泳道。 用户可以重新运行[校准](calibration.md)应用程序以解决此问题。 开发人员可以更新稳定平面，以进一步增强稳定性。
* **颜色分离。** HoloLens 中的显示是彩色顺序显示的，它们在 60 Hz 处以红色绿色-蓝绿色的彩色通道闪烁（各个颜色字段以 240 Hz 显示）。 无论用户何时使用其眼睛跟踪移动的全息图，都将在其构成颜色中分离出全息图的前导和尾随边缘，从而产生彩虹效果。 分离程度取决于全息图的速度。 在某些罕见情况下，在查看固定全息图的同时迅速移动打印头也会导致彩虹效果，这称为*[颜色分离](hologram-stability.md#color-separation)*。

## <a name="frame-rate"></a>帧速率

帧速率是全息图稳定性的第一个支柱。 要使全息影像在世界中显得稳定，提供给用户的每个图像都必须在正确的位置中绘制出全息影像。 每秒显示一次 HoloLens 刷新240，为每个新呈现的图像显示四个单独的颜色字段，导致用户体验 60 FPS （每秒帧数）。 若要提供最佳体验，应用程序开发人员必须维护 60 FPS，这将转换为每16毫秒向操作系统持续提供一次新映像。

**60 FPS**为了绘出全息影像，使其看起来像是真实世界，需要从用户的位置呈现图像。 由于图像渲染需要时间，因此在显示器中显示图像时，HoloLens 会预测用户的头。 但是，此预测算法是近似值。 HoloLens 有一些硬件，可调整呈现的图像，以考虑预测的头位置与实际头位置之间的差异。 调整会使用户看到的图像看起来就像是从正确位置呈现的一样，而全息影像却是稳定的。 映像更新最适合进行少量更改，它无法完全修复呈现的图像（如视差）中的某些项。

通过在 60 FPS 的情况下呈现，你将执行以下三项操作来帮助实现稳定的全息影像：
1. 最大程度地降低渲染图像和用户查看图像之间的总体延迟。 在具有游戏的引擎和在一脉相承中运行的渲染线程中，在30FPS 上运行可能会增加 33.3 ms 的额外延迟。 减少延迟可减少预测错误并增加全息影像稳定性。
2. 这样，每个图像都能达到用户的眼睛，并具有一致的延迟时间。 如果以 30 fps 的速度呈现，则显示的图像仍为 60 FPS，这意味着相同的图像会在一行中显示两次。 第二个16.6 帧比第一帧的延迟时间更长，并将不得不更正更明显的错误量。 这种错误的不一致会导致不需要的 60 Hz judder。
3. 减轻视觉上的抖动，其特征是运动不均衡和重影。 全息影像运动速度越快且渲染速率越低，抖动就越明显。 努力始终维护 60 FPS，将有助于避免给定移动全息图的 judder。

**帧速率一致性**帧速率一致性与高帧/秒一样重要。 对于任何内容丰富的应用程序，偶尔丢弃的帧都是不可避免的，而且 HoloLens 实现了一些复杂的算法来从偶然的故障中恢复。 但是，对于用户而言，持续波动的帧比以较低的帧速率持续运行要多得多。 例如，对于五帧（在这五个帧的持续时间内为 60 FPS）呈现的应用程序，然后每隔一帧在下10帧（对于这10帧的持续时间都为 30 FPS）的情况下，将会显得更不稳定。

在相关说明中，当[混合现实捕获](mixed-reality-capture.md)正在运行时，操作系统将应用程序限制为 30 FPS。

**性能分析**可以使用不同种类的工具来基准应用程序帧速率，例如：
* GPUView
* Visual Studio 图形调试器
* 内置于三维引擎（如 Unity）的探查器

## <a name="hologram-render-distances"></a>全息图呈现距离

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

当 fixates 和专注于某个对象时，该视觉对象系统会集成多个距离相关的信号。
* [便利设施](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)-单个眼睛的重点。
* [收敛](https://en.wikipedia.org/wiki/Convergence_(eye))-两个眼睛向内或向外移动到对象的中心。
* [望远镜视觉](https://en.wikipedia.org/wiki/Stereopsis)对象-在与固定点远离某个对象距离的左侧和右侧图像之间发达国家。
* 底纹、相对角度大小和其他 monocular （单一眼睛）提示。

会合和便利的独特之处在于，它们的视网膜提示与眼睛如何变化以不同的距离感知对象相关。 在自然查看中，聚合和便利设施均已链接。 当眼睛接近时（例如，鼻子），眼睛交叉并适应近点。 当眼睛查看无穷时，眼睛会成为平行的，眼睛可容纳无限大。 

戴 HoloLens 的用户将始终适应 2.0 m 以维护一个清晰的图像，因为 HoloLens 显示的固定距离离用户约2.0 米。 应用开发人员通过在不同的深度放置内容和全息影像来控制用户的眼睛汇聚。 当用户容纳并聚合到不同的距离时，两个提示之间的自然链接会断开，这可能会导致 visual discomfort 或疲劳，特别是当冲突量大时。 

如果尽可能将混合内容保持在 2.0 m 2.0 附近（即，在一个场景中，有很多深度，如有可能），可通过将最接近 m 的内容 Discomfort，来避免或最小化 vergence。 当内容不能放在 2.0 m 附近时，当用户在不同距离之间来回注视时，discomfort 会出现 vergence 冲突。 换句话说，查看远离50厘米的静止全息图比查看在一段时间内走走或远离您的全息图 50 cm 更为熟悉。

将内容放置在 2.0 m 也是有益的，因为这两个显示器的设计目的是完全重叠。 对于放置在此平面之外的图像，当它们移出全息帧的一侧时，它们将显示在一个显示器上，同时仍然可见。 此望远镜 rivalry 可能会对 holorgam 的深度认知造成中断。

**全息影像与用户之间的最佳距离**

![全息影像与用户之间的最佳距离](images/distanceguiderendering-750px.png)

**剪辑平面**为了最大限度地获取舒适，我们建议在85厘米剪辑渲染距离，从 1 m 开始的内容淡化。 在全息影像和用户均为静止的应用程序中，可以轻松地查看全息影像，如50厘米。在这种情况下，应用程序应将不超过30厘米的剪辑平面置于离剪裁平面至少10厘米的位置。 只要内容比85厘米更近，就必须确保用户不会频繁地从全息影像中移近或远离用户，否则，在这些情况下，这种情况很可能会导致 discomfort 的 vergence 冲突。 内容的设计目的是为了最大程度地减少从用户交互到 85 cm 的需要，但当内容必须比85厘米更近时，适用于开发人员的很好的经验法则是设计这样的方案：用户和/或全息影像不会在超过25% 的时间内移动。

**最佳做法**如果无法将全息影像置于 2 m 个位置，并且无法避免聚合和便利设施之间发生冲突，则全息图位置的最佳区域为 1.25 m 和 5 m。 在每种情况下，设计器都应该构建内容来鼓励用户与 1 + m 交互（例如，调整内容大小和默认位置参数）。

## <a name="reprojection"></a>Reprojection
HoloLens 会执行一种复杂的硬件辅助全息稳定技术（称为 reprojection）。 Reprojection 在场景动画处理时，会考虑运动和变化点（CameraPose），而用户则会移动其头。  应用程序需要执行特定操作才能充分利用 reprojection。


有四种主要类型的 reprojection
* **深度 Reprojection：** 从应用程序生成最少工作量的最佳结果。  呈现的场景的所有部分都基于用户与用户之间的距离进行了单独的稳定。  某些呈现项目在深度变化时可能会可见。  此选项仅在 HoloLens 2 和沉浸式耳机上可用。
* **平面 Reprojection：** 允许应用程序精确控制稳定。  平面由应用程序设置，该平面上的所有内容将是场景中最稳定的部分。  全息图离飞机的更好，就是不太稳定。  此选项在所有 Windows MR 平台上可用。
* **自动平面 Reprojection：** 系统使用深度缓冲区中的信息设置稳定平面。  此选项在 HoloLens 第1代和 HoloLens 2 上可用。
* **无：** 如果应用程序不执行任何操作，则会在用户的打印头注视方向上，将平面 Reprojection 与以2米固定的稳定平面一起使用，通常会生成未达标准的结果。

应用程序需要执行特定操作才能启用不同类型的 reprojection
* **深度 Reprojection：** 应用程序将每个呈现的帧的深度缓冲区提交给系统。  在 Unity 上，在 " **XR 插件管理**" 下的 " **Windows Mixed Reality 设置**" 窗格中，通过 "**共享深度缓冲区**" 选项完成深度 Reprojection。  DirectX 应用调用 CommitDirect3D11DepthBuffer。  应用程序不应调用 SetFocusPoint。
* **平面 Reprojection：** 在每个帧上，应用程序会告诉系统要稳定的平面位置。  Unity 应用程序调用 SetFocusPointForFrame，并应禁用**共享深度缓冲**。  DirectX 应用调用 SetFocusPoint，不应调用 CommitDirect3D11DepthBuffer。
* **自动平面 Reprojection：** 若要启用，应用程序需要将其深度缓冲区提交给系统，因为它们的深度 Reprojection。  在 HoloLens 2 上，应用程序需要在每个帧上 SetFocusPoint 一个点，0，0。  对于 HoloLens 第1代，应用程序不应调用 SetFocusPoint。

### <a name="choosing-reprojection-technique"></a>选择 Reprojection 技术

稳定类型 |    沉浸式耳机 |    HoloLens 第1代 | HoloLens 2
--- | --- | --- | ---
深度 Reprojection |    建议 |   不适用 |   建议<br/><br/>Unity 应用程序必须使用 Unity 2018.4.12 或更高版本或 Unity 2019.3 或更高版本。 否则，请使用自动平面 Reprojection。
自动平面 Reprojection | 不适用 |   建议默认值 |   如果深度 Reprojection 未提供最佳结果，建议使用<br/><br/>建议 unity 应用程序使用 Unity 2018.4.12 或更高版本或 Unity 2019.3 或更高版本。  以前的 Unity 版本将使用略微降级的 reprojection 结果。
平面 Reprojection |   不建议 |   如果自动平面未提供最佳结果，建议使用 | 如果两个深度选项都不能获得所需的结果，请使用    

### <a name="verifying-depth-is-set-correctly"></a>验证深度设置正确
            
当 reprojection 方法使用深度缓冲区时，验证深度缓冲区的内容是否表示应用程序的呈现场景很重要。  许多因素可能导致问题。 例如，如果有另一个相机用于渲染用户界面覆盖，则可能会覆盖实际视图中的所有深度信息。  透明对象通常不会设置深度。  某些文本呈现默认情况下不设置深度。  当深度与呈现的全息影像不匹配时，呈现会出现明显的难题。
            
HoloLens 2 有一个可视化工具，用于显示深度的位置和未设置，可从设备门户启用。  在 "**查看**  >  **全息图稳定性**" 选项卡上，选择 "**在耳机中显示深度可视化**" 复选框。  深度设置正确的区域将为蓝色。  没有深度集的呈现项将标记为红色，需要修复。  

> [!NOTE]
> 视觉对象的视觉对象将不会在混合现实捕获中显示。  它仅在设备上可见。
            
某些 GPU 查看工具将允许可视化深度缓冲区。  应用程序开发人员可以使用这些工具来确保正确设置深度。  请参阅应用程序工具的文档。

### <a name="using-planar-reprojection"></a>使用平面 Reprojection
> [!NOTE]
> 对于桌面沉浸式耳机，设置稳定面通常会提高效率，因为它提供的视觉质量不如向系统提供应用的深度缓冲区来启用基于深度的 reprojection。 除非在 HoloLens 上运行，否则通常应避免设置稳定平面。

![三维对象的稳定平面](images/stab-plane-500px.jpg)

设备将自动尝试选择此平面，但应用程序应通过选择场景中的焦点来提供帮助。 在 HoloLens 上运行的 Unity 应用应根据场景选择最佳关注点，并将其传递到[SetFocusPoint （）](focus-point-in-unity.md)。 默认的旋转多维数据集模板中包含了在 DirectX 中设置焦点的示例。

当你在连接到台式计算机的沉浸式耳机上运行应用时，Unity 将向 Windows 提交深度缓冲区以启用每像素 reprojection，这可提供更好的图像质量，无需应用显式工作。 仅当应用程序在 HoloLens 上运行时，才应提供焦点，否则会重写每像素 reprojection。


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

焦点的位置很大程度上取决于全息图所查看的内容。 应用具有用于引用的 "注视" 向量，应用设计器知道他们希望用户看到哪些内容。

开发人员可对稳定全息影像执行的最重要的一项操作是以 60 FPS 的帧呈现。 如果低于 60 FPS，将大大减少全息图稳定性，无论是什么稳定性平面优化。

**最佳做法**没有通用的方法来设置稳定平面，它是特定于应用的。 我们的主要建议是试验并了解哪种方法最适合你的方案。 但是，请尽量将稳定平面与尽可能多的内容对齐，因为此平面上的所有内容都是完美稳定的。

例如：
* 如果只有平面内容（读取应用程序、视频播放应用程序），请将 "稳定" 平面与包含内容的平面对齐。
* 如果有三个小球体处于世界锁定状态，则会使 "稳定" 平面成为当前用户视图中所有球的中心。
* 如果场景的内容在深度上非常不同，则更倾向于获取更多对象。
* 确保调整每个帧的稳定点，使其与用户正在查看的全息图一致

**要避免的问题**稳定面是实现稳定的全息影像的极佳工具，但如果误用它，可能会导致严重的映像不稳定。
* 别忘了。 最终，用户可以使用稳定平面，或将其附加到不再位于用户视图中的对象。 确保稳定平面正常设置为相对相机（如-摄像机）
* 不要在两个极端之间来回更改稳定平面
* 不要将稳定平面设置为固定距离/方向
* 不要让稳定面贯穿用户
* 在台式计算机上运行时，请勿设置焦点，而不是使用基于像素的深度 reprojection。

## <a name="color-separation"></a>颜色分离 

由于 HoloLens 显示的性质，有时会出现名为 "颜色分离" 的项目。 它将以图像形式表现为单独的基本颜色（红色、绿色和蓝色）。 当显示白色对象时，项目尤其可见，因为它们有大量的红色、绿色和蓝色。 当用户以较快的速度在全息帧上移动时，最明显的是用户。 项目的另一种方式是对象的扭曲/变形。 如果对象具有高对比度和/或纯色，如红色、绿色、蓝色，则会将颜色分隔视为对象的不同部分的弯曲。

**打印头锁定空心轮光标的颜色分离的示例可能类似于用户将其头旋转到侧面：**

![打印头锁定空心轮光标的颜色分离的示例可能类似于用户将其头旋转到一边。](images/colorseparationofroundwhitecursor-300px.png)

尽管很难完全避免颜色分离，但有几种方法可用于缓解这种情况。

**可以在以下项上查看颜色分隔：**
* 正在快速移动的对象，包括 head 锁定对象，如[光标](cursors.md)。
* 远离[稳定平面](hologram-stability.md#reprojection)的对象。

**衰减颜色分离的效果：**
* 使对象滞后用户。 它应显示为具有某种惯性，并附加到注视 "on 弹簧"。 这种方法减缓了游标的速度（减少了分离距离），并将其放在用户可能的注视点之后。 只要用户停止改变其看起来就会很自然。
* 如果你确实想要移动一张全息图，如果你希望用户跟随其眼睛，请尝试将其移动速度保持在5度/秒以下。
* 使用*光*而不是*几何图形*作为光标。 附加到注视的虚拟照明源会被视为交互式指针，但不会导致颜色分离。
* 调整 "稳定" 平面，使其与用户正在 gazing 的全息影像匹配。
* 使对象变为红色、绿色或蓝色。
* 切换到内容的模糊版本。 例如，可以将一个圆形白色光标更改为在运动方向上稍微模糊的线条。

与之前一样，在 60 FPS 和设置 "稳定" 平面的情况下，最重要的技术是全息图稳定性。 如果有明显的颜色分离，请首先确保帧速率符合预期。

## <a name="see-also"></a>另请参阅
* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [颜色、光线和材料](color,-light-and-materials.md)
* [本能交互](interaction-fundamentals.md)
* [MRTK 全息影像稳定性](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html)
