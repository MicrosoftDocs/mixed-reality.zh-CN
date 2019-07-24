---
title: 应用质量标准
description: 本文档介绍影响混合现实应用质量的主要因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 应用质量标准, 混合现实, 混合现实应用
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024492"
---
# <a name="app-quality-criteria"></a>应用质量标准

本文档介绍影响混合现实应用质量的主要因素。 对于每个因素, 提供以下信息
* 概述-质量因素的简短说明及其重要原因。
* 设备影响-影响哪种类型的窗口混合现实设备。
* 质量标准–如何评估质量因素。
* 如何度量–衡量问题 (或体验) 的方法。
* 建议-概述提供更好的用户体验的方法。
* 资源-相关的开发人员和设计资源有助于创建更好的应用程序体验。

## <a name="frame-rate"></a>帧速率

帧速率是全息图稳定性和用户舒适的第一个支柱。 低于建议目标的帧速率可能导致全息影像出现抖动, 对体验的 believability 产生负面影响, 并可能导致目视疲劳。 针对 Windows Mixed Reality 沉浸式耳机的目标帧速率为60Hz 或 90Hz, 具体取决于你想要支持的与 Windows Mixed Reality 兼容的电脑。 对于 HoloLens, 目标帧速率为60Hz。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
| 应用一致地满足目标设备的每秒帧数 (FPS) 目标:HoloLens 上的 60fps;超计算机上的 90fps;并60fps。 | 应用有间歇性的帧不会阻碍核心体验;或 FPS 一直低于所需的目标, 但不会妨碍应用程序的体验。 | 此应用在每10秒或更短时间内遇到帧速率下降。 |

### <a name="how-to-measure"></a>如何度量

* 实时帧速率图通过[Windows 设备门户](using-the-windows-device-portal.md#system-performance)在 "系统性能" 下提供。
* 对于开发调试, 请将帧速率诊断计数器添加到应用中。 查看示例计数器的资源。
* 当应用程序运行时, 可以在设备中体验到帧速率下降。 如果全息图显示意外的抖动运动, 则帧速率较低或稳定性平面可能是原因。

### <a name="recommendations"></a>建议

* 在开发工作开始时添加帧速率计数器。
* 应评估出现帧速率下降的更改, 并适当地将其解析为性能 bug。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [全息图稳定性和帧速率](hologram-stability.md#frame-rate)
* [资产性能预算](asset-creation-process.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MRToolkit, FPS 计数器显示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, 着色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>外部引用

* [Unity, 优化移动应用程序](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>全息影像稳定性

稳定的全息影像会提高应用程序的可用性和 believability, 并为用户创建更舒适的查看体验。 全息图稳定性的质量是良好的应用程序开发和设备了解 (跟踪) 其环境的能力。 尽管帧速率是稳定性的第一支柱, 但其他因素可能会影响稳定性, 其中包括:

* 使用 "稳定" 平面
* 与空间锚的距离
* 字距

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
|  全息影像显示稳定。 | 辅助内容展示意外移动;或意外移动不会妨碍总体应用程序体验。 | 帧中的主要内容表现出意外移动。 |

### <a name="how-to-measure"></a>如何度量

戴设备并观看体验:

* 从一侧到另一侧移动您的头, 如果全息影像显示意外的移动, 稳定的稳定性平面与焦距平面之间的不正确对齐就是可能的原因。
* 四处移动影像和环境, 查找泳道和 jumpiness 等行为。 此类动作可能由设备不跟踪环境或到空间锚点的距离引起。
* 如果帧中有大的或多个全息影像, 请在不同的深度观察全息影像行为, 同时从一侧到另一侧, 如果出现抖动, 这可能是由稳定平面导致的。

### <a name="recomendations"></a>建议

* 在开发工作开始时添加帧速率计数器。
* 使用 "稳定" 平面。
* 始终在其定位点的3米以内呈现定位的全息影像。
* 请确保您的环境设置正确跟踪。
* 设计你的体验, 以避免帧内处于不同焦点级别的全息影像。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [全息图稳定性和帧速率](hologram-stability.md#frame-rate)
* [使用 "稳定" 平面进行案例研究](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
* [空间定位点](spatial-anchors.md)
* [处理跟踪错误](coordinate-systems.md#handling-tracking-errors)
* [固定的引用框架](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR 配套包, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>实面上的全息影像位置

使用物理对象 (如果要彼此相关) 的 Misalignments, 可以清楚地指示全息影像和真实世界的非联合。 位置的准确性应与方案的需求相关;例如, 常规表面布局可以使用空间图, 但更准确的放置需要使用标记和校准。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
| 全息图通常以厘米到英寸的范围对齐。 如果需要更高的准确性, 应用应在所需的应用规范内提供高效的协作方式。 | NA | 通过断开 surface 平面或远离表面, 全息影像将与物理目标对象显示不对齐。 如果需要准确性, 全息影像应满足方案的邻近规范。 | 

### <a name="how-to-measure"></a>如何度量

* 放置在空间地图上的全息影像不会显得明显地浮动在表面上方或下方。
* 需要精确放置的全息影像应具有某种形式的标记和校准系统, 这种系统对于方案的要求是准确的。

### <a name="recommendations"></a>建议

* 空间映射适用于在不需要精度时将对象放置在图面上。
* 为了获得最佳的精度, 请使用标记或海报来设置全息影像, 并使用 Xbox 控制器 (或某种手动对齐机制) 来进行最终校准。
* 考虑将超大型全息图分解为逻辑部件, 并将每个部件与图面对齐。
* 错误设置的 interpupilary 距离 (IPD) 还会影响全息图对齐。 始终将 HoloLens 配置为用户的 IPD。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [空间映射放置](spatial-mapping.md#placement)
* [房间扫描过程](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [空间锚定最佳做法](spatial-anchors.md#best-practices)
* [处理跟踪错误](coordinate-systems.md#handling-tracking-errors)
* [Unity 中的空间映射](spatial-mapping-in-unity.md)
* [Vuforia 开发概述](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR 空间 230：空间映射](holograms-230.md)
* [MR 工具包, 空间映射库](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR 配套包, 海报校准示例](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR 配套包, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>外部引用

* [Lowes 案例研究, 精度调整](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>轻松查看区域

应用开发人员通过在不同的深度放置内容和全息影像来控制用户的眼睛汇聚。 戴 HoloLens 的用户将始终适应 2.0 m 以保持清晰的图像, 因为在与用户相比, 与用户相比, 在大约2.0 个位置固定了 HoloLens 显示。 内容深度不正确可能会导致 visual discomfort 或疲劳。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

<table>
<tr>
<td> 确切 </td><td><ul>
<li>将内容放置在2m。</li><li>如果无法在2m 中放置全息影像并且无法避免聚合和便利设施之间发生冲突, 则全息图位置的最佳区域介于 1.25 m 和5分钟之间。</li><li>在每种情况下, 设计器都应该构建内容来鼓励用户与 1 + m 交互 (例如, 调整内容大小和默认位置参数)。</li><li>除非方案特别不需要, 否则应使用从1m 开始的 fadeout 实现剪辑平面。</li><li>如果需要更密切地观察 motionless 全息图, 内容不应比50cm 更接近。</li>
</ul></td>
</tr><tr>
<td> 适合</td><td> 内容在查看和运动指导范围内, 但不恰当地使用或不使用剪辑平面。</td>
</tr><tr>
<td> 失败 </td><td> 内容显示太近 (通常&lt;为 1.25 m 或&lt;50cm, 适用于需要更密切观察的静止全息影像。)</td>
</tr>
</table>

### <a name="how-to-measure"></a>如何度量

* 内容通常应 2m, 但不能比5分钟更接近1.25 或更远。
* 在少数例外情况下, 将在从1m 开始, 为 fadeout 的内容设置为85CM。 接近内容并记下剪辑平面效果。
* 固定内容不应比50cm 更近。

### <a name="recommendations"></a>建议

* 设计内容以获取2m 的最佳视图距离。
* 将剪辑呈现距离设置为 85cm, 并将 fadeout 的内容从1m 开始。
* 对于需要更近查看的静止全息影像, 剪辑平面应不会比30cm 更近, fadeout 应该至少从剪裁平面开始10cm。

### <a name="resources"></a>资源

* [呈现距离](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦点](focus-point-in-unity.md)
* [进行大规模试验](scale.md#experimenting-with-scale)
* [文本, 建议的字号](typography.md#recommended-font-size)

## <a name="depth-switching"></a>深度切换

无论查看舒适问题的区域如何, 用户在接近和远的焦距对象 (包括全息影像和真实内容) 之间进行频繁或快速切换都可能会导致 oculomotor 疲劳和 general discomfort。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
|  不会导致用户 unnaturally refocus 的有限或自然深度切换。 | 突然深度切换这是核心的, 设计为应用程序体验, 或由于意外的实际内容而产生的突然深度切换。 | 一致的深度切换或对应用程序体验不必要或核心的突然深度切换。 | 

### <a name="how-to-measure"></a>如何度量

* 如果应用要求用户持续和/或突然改变深度焦点, 则会出现深度切换问题。

### <a name="recommendations"></a>建议

* 保持主要内容处于一致的焦点平面上, 并确保 "稳定" 平面与焦点平面匹配。 这将减少 oculomotor 疲劳和意外的全息图移动。

### <a name="resources"></a>资源

* [呈现距离](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦点](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>使用空间音效

在 Windows Mixed Reality 中, 音频引擎通过使用方向、距离和环境模拟模拟3D 声音, 提供混合现实体验的听觉组件。 在应用程序中使用空间音效使开发人员能够在整个用户的 convincingly 中放置声音。 然后, 这些声音看起来就像是来自真实的物理对象, 或是用户的环境中的混合现实影像。 空间音效是用于混合现实应用程序中的浸入式、可访问性和 UX 设计的强大工具。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
|  声音以逻辑方式 spatialized, 并适当地使用声音来帮助进行对象发现和用户反馈。 声音非常自然, 与对象相关, 并在整个方案中标准化。 | 空间音频适用于 believability, 但它不能帮助用户提供反馈和发现。 | 听不到预期的声音, 并且/或缺少声音来帮助用户在 UX 中 spatialized。 或在方案设计中不考虑或使用空间音频。 | 

### <a name="how-to-measure"></a>如何度量

* 通常, 相关声音应从目标全息影像发出 (例如, 吠声音来自全息狗。)
* 应在整个 UX 中使用声音提示, 以帮助用户在全息帧外提供反馈或了解操作。

### <a name="recommendations"></a>建议

* 使用空间音频来帮助对象发现和用户界面。
* 真实声音比合成或非自然声音更好。
* 大多数声音应为 spatialized。
* 避免不可见的发射器。
* 避免空间屏蔽。
* 规范化所有声音。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [空间音效](spatial-sound.md)
* [空间音效设计](spatial-sound-design.md)
* [Unity 中的空间音效](spatial-sound-in-unity.md)
* [案例研究, HoloTour 的空间音效](case-study-spatial-sound-design-for-holotour.md)
* [案例研究, 在 RoboRaid 中使用空间音效](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR 空间 220：空间音效](holograms-220.md)
* [MRToolkit, 空间音频](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>专注于全息帧 (FOV) 边界

设计良好的用户体验可以创建和维护围绕用户扩展的虚拟环境的有用上下文。 缓解 FOV 边界的影响涉及到精心设计的内容规模和上下文、使用空间音频、指导系统和用户的位置。 如果完成了正确的操作, 该用户将感到不受 FOV 边界的影响, 同时具有舒适的应用程序体验。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
|  用户永远不会失去上下文和查看。 为大对象提供了上下文帮助。 为框架外的对象提供了可发现性和查看指南。 通常, 动画的动画设计和规模调整适用于舒适的观看体验。 | 用户永远不会丢失上下文, 但在有限的情况下, 可能需要额外的颈部运动。 在有限的情况下, 规模会导致动态影像中断垂直或水平的帧, 导致某些颈部运动查看全息影像。 | 若要查看全息影像, 用户可能丢失上下文和/或一致的颈部运动。 如果没有适用于大全息对象的上下文指南, 则可以轻松地在帧外移动对象, 而无需发现指引, 或者需要定期移动影像来查看。 | 

### <a name="how-to-measure"></a>如何度量

* 由于在边界处裁剪, (大) 全息图的上下文丢失或无法理解。
* 由于缺少引起注意的控制器或可快速移入和移出全息帧的内容, 因此很难找到全息影像的位置。
* 方案需要定期和重复的向上和向下移动, 才能完全查看疲劳的全息图。

### <a name="recommendations"></a>建议

* 开始体验适合 FOV 的小对象, 然后将视觉提示转换为较大版本。
* 使用空间音频和注意控制器来帮助用户查找 FOV 之外的内容。
* 尽可能避免在垂直剪裁 FOV 的全息影像。
* 为用户提供应用内指南以获得最佳观看位置。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [全息帧](holographic-frame.md)
* [案例研究, HoloStudio UI 和交互设计知识](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [对象和环境的规模](scale.md)
* [游标, 直观提示](cursors.md#visual-cues)

#### <a name="external-references"></a>外部引用

* [关于 FOV 的 ado](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>内容对用户位置的响应

全息影像应以与 "实际" 对象相同的方式对用户位置做出反应。 一个值得注意的设计注意事项是 UI 元素, 这些元素不一定会假设用户的位置为静止, 并适应用户的动作。 设计可正确适应用户位置的应用将创建更可信的体验, 并使其更易于使用。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

<table>
<tr>
<td> 确切 </td><td> 内容和 UI 适应用户位置, 使用户能够在预期用户移动范围内自然地与内容交互。</td>
</tr><tr>
<td> 适合 </td><td> UI 适应用户位置, 但可能会妨碍关键内容的查看, 要求用户调整其位置。</td>
</tr><tr>
<td> 失败 </td><td><ol>
<li>UI 元素在移动过程中丢失或锁定, 导致用户 unnaturally 返回 (或查找) 控件。</li><li>UI 元素限制主要内容的视图。</li><li>UI 移动不是针对查看距离和动力而优化的, 尤其是在<a href="billboarding-and-tag-along.md">标记沿</a>ui 元素上。</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>如何度量

* 所有度量值都应在合理的方案范围内完成。 当用户移动发生变化时, 不要尝试通过极端的用户移动来诱骗应用。
* 对于 UI 元素, 不管用户移动如何, 相关控件都应可用。 例如, 如果用户正在使用缩放功能查看和浏览三维地图, 则无论位置如何, 缩放控件都应立即可供用户使用。

### <a name="recommendations"></a>建议

* 用户是相机, 它们控制移动。 让它们驱动器。
* 对于文本和 menuing 系统, 请考虑 billboarding, 如果用户要四处移动, 则可能会被全局锁定或遮住。
* 同时对需要关注用户的内容使用标记, 同时允许用户查看它们前面的内容。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [交互设计](hologram.md)
* [颜色、光线和材料](color,-light-and-materials.md)
* [公告和尾随](billboarding-and-tag-along.md)
* [本能交互](interaction-fundamentals.md)
* [自移动和用户 locomotion](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR 输入 210：凝视](holograms-210.md)

## <a name="input-interaction-clarity"></a>输入交互清晰度

输入交互清晰度对于应用可用性至关重要, 其中包括输入一致性、设计、交互方法的可发现性。 用户应能够在不 relearning 的情况下使用平台范围的常见交互。 如果应用具有自定义输入, 则应该清楚地传达并演示。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
|  输入交互方法与 Windows Mixed Reality 提供的[指南](interaction-fundamentals.md)一致。 任何自定义输入都不应对标准输入冗余 (而不是使用标准交互), 必须清楚地传达并向用户演示。 | 与最佳方法相似, 但自定义输入对于标准输入方法是冗余的。 用户仍可通过应用体验实现目标和进度。 | 难以理解输入法或按钮映射。 输入进行了大量自定义, 不支持标准输入、无说明或可能会导致疲劳和舒适的问题。 | 

### <a name="how-to-measure"></a>如何度量

* 应用使用一致[的标准输入法。](interaction-fundamentals.md)
* 如果应用有时候输入, 则会通过以下方法清楚地传达此内容:
* 首次运行体验
* 介绍屏幕
* 工具提示
* 手动指导
* 帮助部分
* 语音

### <a name="recommendations"></a>建议

* 尽可能使用标准输入方法。
* 为非标准输入法提供演示、教程和工具提示。
* 在整个应用程序中使用一致的交互模型。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [本能交互](interaction-fundamentals.md)
* [种不可交互对象](interactable-object.md)
* [头部凝视和停留](gaze-and-dwell.md)
* [光标](cursors.md)
* [舒适, 注视](comfort.md#gaze-direction)
* [手势](gestures.md)
* [语音输入](voice-input.md)
* [语音命令](voice-design.md)
* [运动控制器](motion-controllers.md)
* [Unity 的输入移植指南](input-porting-guide-for-unity.md)
* [Unity 中的键盘输入](keyboard-input-in-unity.md)
* [Unity 中的凝视](gaze-in-unity.md)
* [Unity 中的手势和运动控制器](gestures-and-motion-controllers-in-unity.md)
* [Unity 中的语音输入](voice-input-in-unity.md)
* [DirectX 中的键盘、鼠标和控制器输入](keyboard,-mouse,-and-controller-input-in-directx.md)
* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的语音输入](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [案例研究:更多的个人计算能力](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [强制转换研究:HoloStudio UI 和交互设计知识](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [示例应用:元素的周期性表](periodic-table-of-the-elements.md)
* [示例应用:农历模块](lunar-module.md)
* [MR 输入 210：凝视](holograms-210.md)
* [MR 输入 211：笔势](holograms-211.md)
* [MR 输入 212：语音](holograms-212.md)

## <a name="interactable-objects"></a>种不可交互对象

"Button" 是一种用于在二维抽象环境中触发事件的比喻。 在这三维混合现实世界中, 我们不必再局限于这种抽象领域。 任何内容都可以是触发事件的种不可交互对象。 种不可交互对象可表示为从桌子上的咖啡杯到悬浮的球标的任何内容。 无论采用何种形式, 用户都应该通过视觉对象和音频提示清楚地识别种不可交互对象。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
|  无论采用何种形式, 都可以通过视觉对象和音频提示在三种状态下识别种不可交互对象: 空闲、目标和选择。 "看起来, 说它" 是显而易见的, 始终在整个体验中使用。 对象经过缩放和分布, 以允许错误释放目标。 | 用户可以通过音频或视觉对象反馈将对象识别为种不可交互, 并可以定位和激活对象。 | 如果没有任何视觉对象或音频提示, 用户将无法识别种不可交互对象。 交互是由于对象比例或对象之间的距离而容易出错。 | 

### <a name="how-to-measure"></a>如何度量

* 种不可交互对象可识别为 "种不可交互";包括按钮、菜单和特定于应用的内容。 根据经验法则, 在面向种不可交互对象时, 应该有视觉和音频提示。

### <a name="recommendations"></a>建议

* 使用视觉和音频反馈进行交互。
* 对于每个输入状态 (空闲、目标、选定), 可视反馈应该是有差异的
* 应缩放种不可交互对象, 并将其放置在错误释放目标位置。
* 分组的种不可交互对象 (如菜单栏或列表) 应具有正确的目标间距。
* 支持语音命令的按钮和菜单应为命令关键字提供文本标签 ("请参阅它)"

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [可交互对象](interactable-object.md)
* [Unity 中的文本](text-in-unity.md)
* [边界框和应用栏](app-bar-and-bounding-box.md)
* [语音命令](voice-design.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [混合现实工具包-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>房间扫描

需要空间映射数据的应用程序依赖于设备在一段时间内和跨会话自动收集此数据, 因为用户浏览其环境中的设备处于活动状态。 此数据的完整性和质量取决于多个因素, 包括用户的探索量、从浏览开始起经过的时间, 以及从设备扫描区域以来是否移动了家具和门等对象。 许多应用程序会在体验开始时分析空间映射数据, 以判断用户是否应执行额外的步骤来改善空间映射的完整性和质量。 如果用户需要扫描环境, 请在扫描体验期间提供明确的指南。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
|  空间网格的可视化通知用户正在进行扫描。 用户清楚地了解要执行的操作以及扫描开始和停止的时间。 | 已提供空间网格的可视化效果, 但用户可能并不清楚地知道要执行什么操作, 并且不会提供任何进度信息。 | 没有网格的可视化效果。 没有向用户提供有关在何处查找或开始扫描的指导信息。 |

### <a name="how-to-measure"></a>如何度量

* 在所需的空间扫描过程中, 会提供视觉和音频指南, 指示在何处进行查找以及何时开始和停止扫描。

### <a name="recommendations"></a>建议

* 指示用户附近的用户总数需要成为体验的一部分。
* 在扫描开始和停止 (例如进度指示器) 时进行通信。
* 在扫描过程中使用网格的可视化效果。
* 提供视觉和音频提示, 以鼓励用户在房间内查找和移动。
* 通知用户要在何处进行数据改进。 在许多情况下, 最好告诉用户需要执行的操作 (例如, 查看家具上的天花板), 以便获得必要的扫描质量。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [房间扫描可视化](room-scan-visualization.md)
* [案例研究:扩展 HoloLens 的空间映射功能](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [案例研究:HoloTour 的空间音效设计](case-study-spatial-sound-design-for-holotour.md)
* [案例研究:在片段中创建沉浸式体验](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [混合现实工具包-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>方向指示器

在混合现实应用中, 内容可能在视图字段之外或由真实的对象封闭像素。 设计良好的应用可使用户更轻松地查找不可见内容。 方向指示器向用户提醒重要内容, 并为内容提供与用户位置相关的指导。 不可见内容的指南可以采用声音发射器、双向箭头或直接视觉提示的形式。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
|  视觉对象和音频提示直接指导用户查看视图外的相关内容。 | 在内容的常规方向上指向用户的箭头或某个指示器。 | 相关内容超出了视图的范围, 用户未提供不良或无位置指南。 | 

### <a name="how-to-measure"></a>如何度量

* 视图的 user 字段之外的相关内容可通过视觉对象和/或音频提示来发现。

### <a name="recommendations"></a>建议

* 当相关内容在用户的 "视图" 字段之外时, 请使用方向指示器和音频提示来引导用户使用内容。 在许多情况下, 可通过方向箭头首选直接直观的指南。
* 方向指示器不应内置于游标中。

### <a name="resources"></a>资源

* [全息帧](holographic-frame.md)

## <a name="data-loading"></a>数据加载

进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。 这可能意味着, 当进度指示器可见时, 用户无法与应用程序交互, 还可以指示等待时间的长短。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  确切  |  适合 |  失败 |
--- | --- | ---
|  动画视觉对象指示器, 其形式为进度栏或振铃, 显示任何数据加载或处理过程中的进度。 视觉对象指示器提供有关等待时间的指导。 | 用户通知用户正在进行数据加载, 但没有指示等待的时间。 | 用于任务的数据加载或处理指示器超过5秒。 |

### <a name="how-to-measure"></a>如何度量

* 在数据加载过程中, 不会有超过5秒的空白状态。

### <a name="recommendations"></a>建议

* 当用户可能认为此应用已停止或崩溃时, 提供一种 animator 的数据加载。 合理的经验法则是任何可能需要5秒以上的 "正在进行" 的活动。

### <a name="resources"></a>资源

* [显示进度](progress.md)
