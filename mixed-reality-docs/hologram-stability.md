---
title: 全息影像稳定性
description: HoloLens 自动稳定了全息影像，但开发人员可以进一步提高全息影像稳定性。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 全息影像，稳定性，hololens
ms.openlocfilehash: ad48d057ee55d4d0d9ae3080d8030a481aef130f
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375774"
---
# <a name="hologram-stability"></a>全息影像稳定性

为实现稳定的全息影像，HoloLens 提供内置的图像稳定性管道。 稳定管道在后台自动运行，因此不需要执行额外的步骤来启用它。 但是，开发人员应运用改善全息影像稳定性的技术，避免降低稳定性的方案。

## <a name="hologram-quality-terminology"></a>全息影像质量术语

全息影像的质量是良好的环境和良好的应用程序开发。 在 HoloLens 可以跟踪周围的环境中，每秒遇到常量60帧的应用将确保全息影像和匹配坐标系处于同步。从用户的角度来看，要保持静止的全息影像不会相对于环境移动。

出现环境问题、不一致或较低的呈现速率或其他应用程序问题时，以下术语对于识别问题很有帮助。
* **准确性.** 一旦将全息图全局锁定并放置在现实世界中，就应将它放置在相对于周围环境的位置，与用户运动或小型和稀疏环境更改无关。 如果在意外的位置出现全息图，则这是一个*准确性*问题。 如果两个不同的房间看起来相同，则可能会发生这种情况。
* **抖动.** 用户将其视为全息影像的高频握手。 跟踪环境时可能会发生这种情况。 对于用户，解决方案正在运行[传感器调整](sensor-tuning.md)。
* **Judder.** 低渲染频率会导致动画的不均匀运动和双图像。 这在动态影像中尤其明显。 开发人员需要维护[常量 60 FPS](hologram-stability.md#frame-rate)。
* **光标.** 用户会看到此屏幕显示为一个全息图，以使其远离最初放置的位置。 如果在离[空间锚](spatial-anchors.md)，而不是完全映射的环境部分中放置全息影像，则会发生这种情况。 创建与空间锚接近的全息影像会降低偏移的可能性。
* **Jumpiness.** 如果不是，则不会偶尔从其位置 "弹出" 或 "跳转"。 这种情况可能会发生，因为跟踪会调整全息影像，以匹配更新的环境。
* **泳道.** 当 sway 与用户的头运动相对应时，会出现一个全息图。 如果应用程序未完全实现[reprojection](hologram-stability.md#reprojection)，并且没有为当前用户[校准](calibration.md)HoloLens，则会发生这种情况。 用户可以重新运行[校准](calibration.md)应用程序以解决此问题。 开发人员可以更新稳定平面，以进一步增强稳定性。
* **颜色分离。** HoloLens 中的显示是一种颜色顺序显示，它以60Hz 为绿色的红绿蓝绿色的颜色通道（在240Hz 上显示单个颜色字段）。 无论用户何时使用其眼睛跟踪搬迁全息图，都将在其构成颜色中分离出全息图的前导和尾随边缘，从而产生彩虹效果。 分离程度取决于全息图的速度。 在某些罕见情况下，在查看固定全息图的同时迅速移动打印头也会导致彩虹效果。 这称为 *[颜色分离](hologram-stability.md#color-separation)* 。

## <a name="frame-rate"></a>帧速率

帧速率是全息图稳定性的第一个支柱。 要使全息影像在世界中显得稳定，提供给用户的每个图像都必须在正确的位置中绘制出全息影像。 每秒显示一次 HoloLens 刷新240，为每个新呈现的图像显示四个单独的颜色字段，导致用户体验 60 FPS （每秒帧数）。 若要提供最佳体验，应用程序开发人员必须维护 60 FPS，这将转换为每16毫秒向操作系统持续提供一次新映像。

**60 FPS**为了绘出全息影像，使其看起来像是真实世界，需要从用户的位置呈现图像。 由于图像渲染需要时间，因此在显示器中显示图像时，HoloLens 会预测用户的头。 此预测算法采取近似值。 HoloLens 有一些硬件，可调整呈现的图像，以考虑预测的头位置与实际头位置之间的差异。 这会使用户看到的图像看起来就像是从正确位置呈现的一样，而全息影像却是稳定的。 映像更新最适合进行少量更改，它无法完全修复呈现的图像（如视差）中的某些项。

通过在 60 FPS 的情况下呈现，你可以执行三项操作来帮助实现稳定的全息影像：
1. 最大程度地降低渲染图像和用户查看图像之间的总体延迟。 在以一致步调运行游戏线程和渲染线程的引擎中，以 30FPS 运行可能会额外增加 33.3 毫秒的延迟。 减小延迟会降低预测误差，并提高全息影像的稳定性。
2. 这样，每个图像都能达到用户的眼睛，并具有一致的延迟时间。 如果在30fps 上呈现，则显示的图像仍以 60 FPS 显示。 这意味着同一映像将在一行中显示两次。 第二个帧比第一帧具有 16.6 ms 的延迟时间，并将不得不更正更明显的错误量。 这种错误的不一致会导致不需要的 judder。
3. 减轻视觉上的抖动，其特征是运动不均衡和重影。 全息影像运动速度越快且渲染速率越低，抖动就越明显。 因此，在任何时候都努力维持 60 FPS，将有助于避免给定移动全息图的 judder。

**帧速率一致性**帧速率一致性与高帧/秒一样重要。 对于任何内容丰富的应用程序，偶尔丢弃的帧都是不可避免的，而且 HoloLens 实现了一些复杂的算法来从偶然的故障中恢复。 但是，对于用户而言，持续波动的帧比以较低的帧速率持续运行要多得多。 例如，对于5帧（在这5帧的持续时间内为 60 FPS）呈现的应用程序，然后每隔一帧删除下10帧（30 FPS，持续时间为30帧）以 30 FPS 的速度呈现。

在相关说明中，当[混合现实捕获](mixed-reality-capture.md)正在运行时，操作系统会将应用程序限制为 30 FPS。

**性能分析**可以使用多种工具来基准应用程序帧速率，例如：
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

收敛和便利设施是唯一的，因为它们是视网膜的提示，与眼睛在不同距离上感知对象的方式相关。 在自然查看中，聚合和便利设施均已链接。 当眼睛接近时（例如，鼻子），眼睛交叉并适应近点。 当眼睛查看无穷时，眼睛会成为平行的，眼睛可容纳无限大。 戴 HoloLens 的用户将始终适应 2.0 m 以维护一个清晰的图像，因为 HoloLens 显示固定在远离用户的光纤上。 应用开发人员通过在不同的深度放置内容和全息影像来控制用户的眼睛汇聚。 当用户容纳并聚合到不同的距离时，两个提示之间的自然链接会断开，这可能会导致视觉对象 discomfort 或疲劳，特别是当冲突量大时。 通过保留用户最接近 2.0 m 的内容（例如，在具有很多深度的场景中，如有可能），可避免或最小化 vergence 的 Discomfort。 当内容不能放置在 2.0 m 附近时，当用户在不同距离之间来回注视时，discomfort 会出现 vergence 冲突。 换而言之，观看 50 厘米远的静态全息影像，比观看 50 厘米远的前后不断移动的全息影像要舒适得多。

将内容置于 2.0 m 也是有好处的，因为这两个显示器被设计为完全重叠。 对于放置在此平面之外的图像，当它们移出全息帧的一侧时，它们会从一次显示中消失，同时仍然可见。 此望远镜 rivalry 可能会对全息图的深度认知造成中断。

**全息影像与用户之间的最佳距离**

![从用户处放置全息影像的最佳距离](images/distanceguiderendering-750px.png)

**剪辑平面**为获得最大舒适，我们建议在85cm 上剪辑渲染距离，fadeout 的内容从1m 开始。 在全息影像和用户均为静止的应用程序中，可以轻松地查看全息影像，就像50cm 一样。 在这种情况下，应用程序应放置一个离30cm 更近的剪辑平面，并从剪切面至少开始10cm。 只要内容比85cm 更近，就必须确保用户不会频繁地从全息影像移近或远离用户，否则，在这些情况下，这种情况很可能导致 discomfortvergence-住宿冲突。 内容应旨在最大程度地减少对用户交互的需要，但当内容必须比85cm 更接近时，适用于开发人员的经验法则是设计一些方案，用户和/或全息影像不会在超过25% 的时间内移动。

**最佳做法**如果无法在2m 中放置全息影像并且无法避免聚合和便利设施之间发生冲突，则全息图位置的最佳区域介于 1.25 m 和5分钟之间。 在每种情况下，设计器都应该构建内容来鼓励用户与 1 + m 交互（例如，调整内容大小和默认位置参数）。

## <a name="reprojection"></a>Reprojection
HoloLens 会执行一种复杂的硬件辅助全息稳定技术（称为 reprojection）。 这会在场景动画处理时考虑运动和变化点（CameraPose），并使用户移动其头。  应用程序需要执行特定操作才能充分利用 reprojection。


有四种主要类型的 reprojection
* **深度 Reprojection：** 这将生成应用程序所需的最少工作量。  呈现的场景的所有部分都基于用户与用户之间的距离进行了单独的稳定。  某些呈现项目在深度变化时可能会可见。  此选项仅在 HoloLens 2 和沉浸式耳机上可用。
* **平面 Reprojection：** 这使应用程序能够精确控制稳定。  平面由应用程序设置，该平面上的所有内容将是场景中最稳定的部分。  全息图离飞机的更好，就是不太稳定。  此选项在所有 Windows MR 平台上可用。
* **自动平面 Reprojection：** 系统使用深度缓冲区中的信息设置稳定平面。  此选项在 HoloLens 第1代和 HoloLens 2 上可用。
* **无：** 如果应用程序不执行任何操作，则会将平面 Reprojection 用于在用户打印头注视方向上按2米固定的稳定平面。  这通常会产生未达标准结果。

应用程序需要执行特定操作才能启用不同类型的 reprojection
* **深度 Reprojection：** 应用程序将每个呈现的帧的深度缓冲区提交给系统。  在 Unity 上，这是使用 "播放机设置" 窗格中的 "启用深度缓冲共享" 选项来完成的。  DirectX 应用调用 CommitDirect3D11DepthBuffer。  应用程序不应调用 SetFocusPoint。
* **平面 Reprojection：** 在每个帧上，应用程序会告诉系统要稳定的平面位置。  Unity 应用程序调用 SetFocusPointForFrame，并应禁用 "启用深度缓冲区共享"。  DirectX 应用调用 SetFocusPoint，不应调用 CommitDirect3D11DepthBuffer。
* **自动平面 Reprojection：** 为实现此要求，应用程序需要将其深度缓冲区提交给系统，就像用于深度 Reprojection。  在 HoloLens 2 上，应用程序需要在每个帧上 SetFocusPoint 一个点，0，0。  对于 HoloLens 第1代，应用程序不应调用 SetFocusPoint。

### <a name="choosing-reprojection-technique"></a>选择 Reprojection 技术

稳定类型 |    沉浸式耳机 |    HoloLens 第1代 | HoloLens 2
--- | --- | --- | ---
深度 Reprojection |    推荐 |   不可用 |   推荐<br/><br/>Unity 应用程序必须使用 Unity 2018.4.12 或更高版本或 Unity 2019.3 或更高版本。 否则，请使用自动平面 Reprojection。
自动平面 Reprojection | 不可用 |   建议默认值 |   如果深度 Reprojection 未提供最佳结果，建议使用<br/><br/>建议 unity 应用程序使用 Unity 2018.4.12 或更高版本或 Unity 2019.3 或更高版本。  以前的 Unity 版本将使用略微降级的 reprojection 结果。
平面 Reprojection |   不建议 |   如果自动平面未提供最佳结果，建议使用 |    如果两个深度选项都不能获得所需的结果，请使用    

### <a name="verifying-depth-is-set-correctly"></a>验证深度设置正确
            
当 reprojection 方法使用深度缓冲区时，验证深度缓冲区的内容是否表示应用程序的呈现场景很重要。  许多因素可能导致问题。  例如，如果有另一个相机用于渲染用户界面覆盖，则可能会覆盖实际视图中的所有深度信息。  透明对象通常不会设置深度。  默认情况下，某些文本呈现功能不会设置深度。  当深度与呈现的全息影像不匹配时，呈现会出现明显的难题。
            
HoloLens 2 有一个可视化工具，用于显示深度为，未设置。  从设备门户启用此端口。  在 "**视图** > **全息图稳定性**" 选项卡上，选择 "**在耳机中显示深度可视化**" 复选框。  深度设置正确的区域将为蓝色。  不具有深度集的呈现项将为红色，因此需要修复。  请注意，将不会在混合现实捕获中显示深度的视觉对象。  它仅在设备上可见。
            
某些 GPU 查看工具将允许可视化深度缓冲区。  应用程序开发人员可以使用这些工具来确保正确设置深度。  请参阅应用程序工具的文档。

### <a name="using-planar-reprojection"></a>使用平面 Reprojection
> [!NOTE]
> 对于桌面沉浸式耳机，设置稳定面通常会提高效率，因为它提供的视觉质量不如向系统提供应用的深度缓冲区来启用基于深度的 reprojection。 除非在 HoloLens 上运行，否则通常应避免设置稳定平面。

![三维对象的稳定平面](images/stab-plane-500px.jpg)

设备将自动尝试选择此平面，但应用程序应通过选择场景中的焦点来帮助完成此过程。 在 HoloLens 上运行的 Unity 应用应根据场景选择最佳关注点，并将其传递到[SetFocusPoint （）](focus-point-in-unity.md)。 默认的旋转多维数据集模板中包含了在 DirectX 中设置焦点的示例。

请注意，当 Unity 应用在连接到台式计算机的沉浸式耳机上运行时，Unity 将向 Windows 提交深度缓冲区以启用每像素 reprojection，这通常会提供更好的图像质量，无需应用显式工作。 如果你提供了焦点，则将重写每像素 reprojection，因此，仅当你的应用程序在 HoloLens 上运行时，才应这样做。




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

开发人员可对稳定全息影像执行的最重要的一项操作是以 60 FPS 的帧呈现。 如果低于 60 FPS，将大大减少全息图稳定性，而不考虑稳定性平面优化。

**最佳做法**没有通用的方法来设置稳定面，它是特定于应用的，因此，主要建议是试验并了解最适合你的方案的情况。 但是，请尽量将稳定平面与尽可能多的内容对齐，因为此平面上的所有内容都是完美稳定的。

例如：
* 如果只有平面内容（读取应用程序、视频播放应用程序），请将 "稳定" 平面与包含内容的平面对齐。
* 如果有3个小球体处于世界锁定状态，请将 "稳定" 平面视为当前位于用户视图中的所有球的中心。
* 如果场景的内容在深度上非常不同，则更倾向于获取更多对象。
* 确保调整每个帧的稳定点，使其与用户正在查看的全息图一致

**要避免的问题**稳定面是实现稳定的全息影像的极佳工具，但如果误用它，可能会导致严重的映像不稳定。
* 不要 "火灾"，因为最终会出现用户之后的稳定平面，或连接到不再位于用户视图中的对象。 确保稳定平面正常设置为相对相机前进（例如，照相机）
* 不要在两个极端之间来回更改稳定平面
* 不要将稳定平面设置为固定距离/方向
* 不要让稳定面贯穿用户
* 在台式计算机上运行时，请勿设置焦点，而不是使用基于像素的深度 reprojection。

## <a name="color-separation"></a>颜色分离 

由于 HoloLens 显示的性质，有时会出现名为 "颜色分离" 的项目。 它将以图像形式表现为单独的基本颜色（红色、绿色和蓝色）。 当显示白色对象时，项目尤其可见，因为它们有大量的红色、绿色和蓝色。 当用户以快速方式跟踪在全息帧上移动的全息影像时，最有可能的。 项目的另一种方式是对象的扭曲/变形。 如果对象具有高对比度和/或纯颜色（红色、绿色、蓝色），则颜色分隔会被视为对象的不同部分的弯曲。

**打印头锁定空心轮光标的颜色分离的示例可能类似于用户将其头旋转到侧面：**

![打印头锁定空心轮光标的颜色分离的示例可能类似于用户将其头旋转到一边。](images/colorseparationofroundwhitecursor-300px.png)

尽管很难完全避免颜色分离，但有几种方法可用于缓解这种情况。

**可以在以下项上查看颜色分隔：**
* 正在快速移动的对象，包括 head 锁定对象，如[光标](cursors.md)。
* 远离[稳定平面](hologram-stability.md#reprojection)的对象。

**衰减颜色分离的效果：**
* 使对象滞后用户。 它应显示为具有某种惯性，并附加到注视 "on 弹簧"。 这会减慢游标的速度（减少分离距离），并将其放在用户可能的注视点之后。 只要用户停止移动其看起来就会很自然。
* 如果你确实想要移动一张全息图，如果预计用户会将其带到其眼睛下，请尽量使其移动速度低于5度/秒。
* 使用*光*而不是*几何图形*作为光标。 附加到注视的虚拟照明源将被视为交互式指针，但不会导致颜色分离。
* 调整 "稳定" 平面，使其与用户正在 gazing 的全息影像匹配。
* 使对象变为红色、绿色或蓝色。
* 切换到内容的模糊版本。 例如，可以将一个圆形白色光标更改为在运动方向上稍微模糊的线条。

与之前一样，在 60 FPS 和设置 "稳定" 平面的情况下，最重要的技术是全息图稳定性。 如果有明显的颜色分离，请首先确保帧速率符合预期。

## <a name="see-also"></a>另请参阅
* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [颜色、光线和材料](color,-light-and-materials.md)
* [本能交互](interaction-fundamentals.md)
* [MRTK 全息影像稳定性](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html)
