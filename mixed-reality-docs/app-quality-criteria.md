---
title: 应用程序质量准则
description: 本文档介绍顶部因素影响混合的现实应用程序的质量。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 应用程序质量标准，混合现实，混合现实应用
ms.openlocfilehash: dfa1390190fad8d84982171dfbcfa101b20501dc
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750316"
---
# <a name="app-quality-criteria"></a>应用程序质量准则

本文档介绍顶部因素影响混合的现实应用程序的质量。 对于每个因素提供了以下信息
* 概述-的质量因子以及为何它很重要的简短说明。
* 设备的影响-哪种类型的窗口混合现实设备会受到影响。
* 质量标准 – 如何评估的质量因子。
* 如何测量 – 度量值 （或体验） 问题的方法。
* 建议 – 摘要的某些方法来提供更好的用户体验。
* 资源 – 相关的开发人员和设计资源都有可用于创建更好的应用体验。

## <a name="frame-rate"></a>帧速率

帧速率是全息图稳定性和用户舒适的第一个支柱。 帧速率低于建议的目标可能会导致全息出现抖动，造成负面影响的体验 believability 并可能会引起眼睛疲劳。 Windows Mixed Reality 沉浸式耳机的体验的目标帧速率将 60 Hz 或你想要支持具体取决于哪些 Windows 混合现实兼容 Pc 90 Hz。 对于 HoloLens 目标帧速率是 60 Hz。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
| 应用一致地满足每个目标设备的第二个 (FPS) 目标帧：HoloLens; 上的 60 fps超高电脑; 上 90 fps和 60 fps 主流的 Pc 上。 | 该应用程序有间歇性帧删除不妨碍核心体验中;或每秒帧数一致地低于所需目标，但不会妨碍应用程序体验。 | 应用程序在遇到平均每隔十秒或更少的帧速率下降。 |

### <a name="how-to-measure"></a>如何测量

* 实时帧速率图通过提供由[Windows Device Portal](using-the-windows-device-portal.md#system-performance)下"系统性能"。
* 对于开发调试，将添加到应用的帧速率诊断计数器。 示例计数器，请参阅资源。
* 移动您从左到右运行应用时，可以在设备中遇到帧速率下降。 如果全息图显示了意外的抖动移动，然后较低的帧速率或稳定性平面是可能的原因。

### <a name="recommendations"></a>建议

* 开发工作的开头添加一个帧速率计数器。
* 应计算并相应地解决的性能 bug 会导致帧速率下降的更改。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [混合现实的了解性能](understanding-performance-for-mixed-reality.md)
* [全息图稳定性和帧速率](hologram-stability.md#frame-rate)
* [资产的性能预算](asset-creation-process.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MRToolkit，每秒帧数计数器显示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit，着色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>外部引用

* [Unity 中，优化移动应用程序](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>全息图稳定性

稳定全息将提高可用性和 believability 您的应用程序，并创建用户提供更舒适的查看体验。 全息图稳定性的质量是很好的应用程序开发和设备的功能，若要了解 （跟踪） 的结果及其环境。 稳定性，首先必须按时帧速率时，其他因素可以影响稳定性包括：

* 稳定平面的使用
* 空间的定位点的距离
* 跟踪

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
|  全息总是出现稳定。 | 辅助内容表现出意外的移动;或意外的移动不会影响总体应用程序体验。 | 在帧中的主要内容表现出意外的移动。 |

### <a name="how-to-measure"></a>如何测量

尽管戴上设备并查看体验：

* 移动您从左到右，如果全息显示意外的移动然后较低的帧速率或到焦平面稳定性平面的不正确的对齐方式是可能的原因。
* 移动全息和环境中，查找行为如泳道和 jumpiness。 导致这种类型的运动的原因可能不是跟踪对空间定位点的环境或距离的设备。
* 如果大型或多个全息框架中，观察在各种深入探索全息图行为，而移动头位置从左到右，如果不显示这是有可能引起的稳定平面。

### <a name="recomendations"></a>建议

* 开发工作的开头添加帧速率计数器。
* 使用稳定平面。
* 始终呈现定位的全息内 3 米的其定位点。
* 请确保环境已设置为正确的跟踪。
* 设计你的体验，以避免全息在范围内的各个重要深度级别。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [全息图稳定性和帧速率](hologram-stability.md#frame-rate)
* [案例研究中，使用稳定平面](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [混合现实的了解性能](understanding-performance-for-mixed-reality.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
* [空间定位点](spatial-anchors.md)
* [处理跟踪错误](coordinate-systems.md#handling-tracking-errors)
* [固定参考框架](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR 配套工具包，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>全息真实的图面上的位置

与物理对象 （如果要相对于另一个放置） 全息 misalignments 是明确表示的非联合，全息和实际。 位置的准确性应相对于的方案; 需要例如，常规的图面上放置可使用空间的映射，但更准确地放置将需要一些使用标记和校准。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
| 全息对齐到英寸范围通常以厘米为单位的面。 如果需要更精确，应用应为所需的应用规范内的协作提供一种有效方式。 | NA | 全息出现重大的图面上的平面或使其不显示浮动离开面与物理目标对象未对齐。 如果需要准确性，全息应满足方案的邻近性规范。 | 

### <a name="how-to-measure"></a>如何测量

* 空间代码图放置的全息不应出现显著浮动的上方或下方的图面。
* 需要准确放置全息应具有某种形式的标记和校准系统是准确的方案的要求。

### <a name="recommendations"></a>建议

* 空间映射是适用于精度不需要时图面上放置对象。
* 最佳的精度，使用标记或海报设置全息和 Xbox 控制器 （或某些手动对齐机制） 的最终校准。
* 请考虑将超大型全息分成逻辑部分以及对齐到图面每个部分。
* 未正确设定 interpupilary 的距离 (IPD) 还可以影响全息图对齐方式。 始终配置为用户的 IPD HoloLens。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [空间映射放置](spatial-mapping.md#placement)
* [扫描进程的房间](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [空间的定位点的最佳做法](spatial-anchors.md#best-practices)
* [处理跟踪错误](coordinate-systems.md#handling-tracking-errors)
* [Unity 中的空间映射](spatial-mapping-in-unity.md)
* [Vuforia 开发概述](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR 空间 230：空间映射](holograms-230.md)
* [MR 工具包，空间映射库](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR 配套工具包，海报校准示例](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR 配套工具包，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>外部引用

* [Lowes 案例研究，精度对齐方式](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>查看区域的舒适

通过将内容和全息放置在各种深入探索聚合用户的眼睛，其中应用开发人员控制。 戴上 HoloLens 的用户将始终允许到 2.0 m 来维护清晰的图像因为 HoloLens 显示固定为光学的距离大约 2.0 m 背朝用户。 不正确的内容深度可能会导致 visual 不适或疲劳。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

<table>
<tr>
<td> 最佳 </td><td><ul>
<li>将内容放在 2 分钟。</li><li>当聚合和便利设施之间的冲突无法避免全息不能放在 2 分钟，全息图放置的最佳区域为 1.25 m 到 5 分钟。</li><li>设计器应在所有情况下，结构内容鼓励用户交互 1 + 米的位置 （例如调整内容大小和默认的位置参数）。</li><li>具体而言不需要的方案，除非修剪平面应与 fadeout 开始 1 百万的实现。</li><li>在更接近观测到的静止不动全息图需要的情况下，内容不应为 50 cm 比更接近。</li>
</ul></td>
</tr><tr>
<td> 符合</td><td> 内容是在查看和动作的指导，但不正当使用或不使用剪裁平面。</td>
</tr><tr>
<td> 失败 </td><td> 内容显示太靠近 (通常&lt;1.25 m 或&lt;为静止状态全息需要仔细观察 50 cm。)</td>
</tr>
</table>

### <a name="how-to-measure"></a>如何测量

* 内容通常应该是 2 分离开，但之间的距离大于 1.25 或关注 5 分钟。
* 有几个例外，HoloLens 剪辑呈现距离应与 fadeout 开始 1 百万的内容设置为.85CM。 方法的内容并记下剪辑平面效果。
* 静态内容不应接近 50 cm 消失。

### <a name="recommendations"></a>建议

* 设计 2 分钟的最佳观看距离的内容。
* 将剪辑呈现距离设置为 85 cm 与 fadeout 开始 1 百万的内容。
* 对于需要更接近查看的静态全息，修剪平面应为之间的距离大于 30 的 cm 和 fadeout 应开始在至少 10 个 cm 离开修剪平面。

### <a name="resources"></a>资源

* [呈现距离](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦点](focus-point-in-unity.md)
* [用规模进行试验](scale.md#experimenting-with-scale)
* [文本，建议字体大小](typography.md#recommended-font-size)

## <a name="depth-switching"></a>深度切换

而不考虑查看区域的舒适的问题，要求用户之间进行切换频繁或快速附近，以及最重要的对象 （包括全息和实际内容） 可能导致 oculomotor 疲劳症和常规不安。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
|  有限的或自然深度切换，不会导致用户可以重新 unnaturally 集中。 | 突然深度开关，这是核心，设计应用体验或引起意外的实际内容的突然深度开关。 | 一致的深度交换机或突然深度切换并不是必需的或应用程序体验的核心。 | 

### <a name="how-to-measure"></a>如何测量

* 如果应用需要用户持续和/或突然更改深度焦点，则切换问题的深度。

### <a name="recommendations"></a>建议

* 主内容保持一致的焦平面，并确保稳定平面与匹配焦平面。 这将缓解 oculomotor 疲劳和意外的 hologram 移动。

### <a name="resources"></a>资源

* [呈现距离](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦点](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>使用的空间声音

在 Windows Mixed Reality 音频引擎提供的混合的现实体验的语音组件通过模拟 3D 声音使用方向、 距离和环境模拟。 应用程序中使用空间声音各地用户允许开发人员将声音 convincingly 放在 3 个维空间 （球体）。 这些听起来然后将看起来像其视为来自用户的环境中混合的现实全息或实际的物理对象。 声音空间是用于浸入式、 可访问性，并在混合的现实应用程序中的用户体验设计的强大工具。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
|  以逻辑方式 spatialized 声音，并 UX 适当地使用声音来帮助进行对象发现和用户反馈。 声音方案中均自然和相关对象和规范化。 | 空间音频未适当地用于 believability 作为方式可帮助用户反馈和可发现性。 | 按预期运行，不 spatialized 声音和/或缺少的声音，以帮助用户中的用户体验。 或空间音频不视为或未在该方案的设计中使用。 | 

### <a name="how-to-measure"></a>如何测量

* 一般情况下，相关的声音应发出从目标全息 (例如。，虚张声势发出的声音 holographic dog。)
* 声音提示应使用整个用户体验，以帮助用户有任何反馈或了解 holographic 框架之外的操作。

### <a name="recommendations"></a>建议

* 使用空间的音频以协助对象发现和用户接口。
* 实际声音效果更佳合成或非自然的声音。
* 应 spatialized 大多数声音。
* 避免不可见发射器。
* 避免空间屏蔽。
* 规范化听上去。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [空间音效](spatial-sound.md)
* [空间音效设计](spatial-sound-design.md)
* [Unity 中的空间音效](spatial-sound-in-unity.md)
* [案例研究，空间 HoloTour 的声音](case-study-spatial-sound-design-for-holotour.md)
* [案例研究，在 RoboRaid 中使用空间的声音](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR 空间 220：空间音效](holograms-220.md)
* [MRToolkit，空间音频](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>专注于 holographic 帧 (FOV) 边界

设计良好的用户体验可以创建和维护的虚拟环境的扩展围绕用户有用的上下文。 缓解 FOV 边界的效果涉及精心设计的内容的缩放和上下文信息，请使用的空间音频、 指导系统和用户的位置。 如果正确操作后，用户将可以小于被削弱 FOV 边界的同时轻松应用体验。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
|  用户永远不会丢失上下文，轻松查看。 为大型对象提供上下文帮助。 可发现性和查看指导提供框架之外的对象。 一般情况下，motion 设计和全息的小数位数是适用于舒适地观看体验。 | 用户永远不会丢失上下文，但额外颈部动作可能需要在有限的环境。 在有限的环境规模会导致全息中断或者导致某些颈部动作，若要查看全息垂直或水平帧。 | 用户可能会丢失上下文和/或一致颈部运动需要查看全息。 对于大型 holographic 对象，将对象移易被不带任何可发现性的指南或高全息框架之外没有上下文的指南要求若要查看的正则颈部运动。 | 

### <a name="how-to-measure"></a>如何测量

* 丢失或不理解由于进行剪裁边界上下文 （大） 全息图。
* 全息的位置很难找到由于缺乏关注主管或快速将移入和移出 holographic 帧的内容。
* 方案需要常规和重复向上和向下头动作以完全看到一张全息图，从而导致颈部疲劳。

### <a name="recommendations"></a>建议

* 使用的小型对象的符合 FOV，那转换到更大版本的视觉提示与启动体验。
* 使用空间的音频和关注主管帮助 FOV 之外的用户查找内容。
* 尽可能多地，避免垂直剪辑 FOV 全息。
* 向用户提供最佳的视觉位置的应用程序内指南。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [全息帧](holographic-frame.md)
* [案例研究、 HoloStudio UI 和交互设计经验](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [对象和环境的规模](scale.md)
* [光标、 可视提示](cursors.md#visual-cues)

#### <a name="external-references"></a>外部引用

* [有关 FOV 的 ado](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>用户位置的内容做出响应

全息应大致"真实"对象执行的相同方法中的用户位置做出反应。 值得注意的设计注意事项，并且一定不能假定用户的位置的 UI 元素保持静止时适应用户的动作。 设计的应用程序正确调整到用户的位置将创建更可信的体验，并使其易于使用。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

<table>
<tr>
<td> 最佳 </td><td> 内容和 UI 适应允许用户与预期的用户移动的范围内的内容自然交互的用户位置。</td>
</tr><tr>
<td> 符合 </td><td> UI 可适应用户位置，但可能会阻碍要求用户调整其位置的关键内容的视图。</td>
</tr><tr>
<td> 失败 </td><td><ol>
<li>丢失或在移动导致用户 unnaturally 返回到 （或查找） 控件过程中锁定 UI 元素。</li><li>UI 元素限制主内容的视图。</li><li>用于查看距离和动量，尤其是对于不优化 UI 移动<a href="billboarding-and-tag-along.md">尾随</a>UI 元素。</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>如何测量

* 应在此方案的合理范围内完成所有度量值。 虽然将不同用户移动，请勿尝试欺骗极端用户移动与该应用程序。
* 对于 UI 元素相关的控件应该是无论用户移动。 例如，如果用户是查看并围绕 3D 映射与 zoom 的每个步骤时，缩放控件应随时可供用户而不考虑位置。

### <a name="recommendations"></a>建议

* 用户是照相机和它们控制移动。 让这些驱动器。
* 请考虑文本公告板和面前系统，否则为将世界锁定或者被遮盖，如果用户已移动。
* 使用尾随需要遵循用户，同时仍允许用户查看新增内容在它们的前面的内容。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [交互设计](hologram.md)
* [颜色、 灯光和材料](color,-light-and-materials.md)
* [公告和尾随](billboarding-and-tag-along.md)
* [本能交互](interaction-fundamentals.md)
* [自动作和用户 locomotion](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR 输入 210：凝视](holograms-210.md)

## <a name="input-interaction-clarity"></a>输入的交互清晰度

输入的交互清楚起见对应用程序的可用性至关重要，包括输入的一致性、 简单性和直接性、 可发现性的交互方法。 用户应该能够使用而无需重新学习的常见平台范围的交互。 如果应用具有自定义输入，应清楚地传达并演示了。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
|  输入的交互方法是与 Windows Mixed Reality 提供一致[指导](interaction-fundamentals.md)。 任何自定义的输入不应为冗余的标准输入 （而不是使用标准交互） 和必须清楚地传达并向用户演示。 | 类似于最佳，但自定义输入是冗余的标准输入方法。 用户仍可以实现的目标和通过应用体验的进度。 | 难以理解输入的方法或按钮映射。 输入大量自定义，不支持标准的输入，没有说明，或可能会导致疲劳、 感觉更舒适的问题。 | 

### <a name="how-to-measure"></a>如何测量

* 该应用使用一致[标准输入方法。](interaction-fundamentals.md)
* 如果应用具有自定义输入，它是清楚地表达通过：
* 首次运行体验
* 介绍性屏幕
* 工具提示
* 手教练
* 帮助部分
* 语音朗读

### <a name="recommendations"></a>建议

* 使用标准输入的方法只要有可能。
* 为非标准的输入方法提供演示、 教程和工具提示。
* 使用在整个应用一致的交互模型。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [本能交互](interaction-fundamentals.md)
* [种交互的对象](interactable-object.md)
* [头部凝视和停留](gaze-and-dwell.md)
* [光标](cursors.md)
* [舒适度和的视线移动](comfort.md#gaze-direction)
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

* [案例研究：追求更多个人计算](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [强制转换研究：HoloStudio UI 和交互设计经验](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [应用程序示例：定期表的元素](periodic-table-of-the-elements.md)
* [应用程序示例：农历模块](lunar-module.md)
* [MR 输入 210：凝视](holograms-210.md)
* [MR 输入 211：手势](holograms-211.md)
* [MR 输入 212：语音](holograms-212.md)

## <a name="interactable-objects"></a>种交互的对象

一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。 在三维混合的现实世界中，我们无需限制为抽象不再这个世界。 任何可以是一个种交互的对象，将触发一个事件。 种交互的对象可以表示为任何从上表杯咖啡到气球状飘浮在空中。 无论窗体中，应通过视频和音频提示用户清楚地识别种交互的对象。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
|  无论窗体，种交互对象都是通过视频和音频提示可识别跨三种状态： 空闲，设定目标，并选择。 "到它，请说"清晰、 一致地使用整个体验。 缩放对象并将其分发以便免费目标错误。 | 用户可以将对象识别为种交互通过音频或可视反馈和可以为目标并激活对象。 | 给定没有直观或音频提示，用户不能识别种交互的对象。 交互是由于对象规模或对象之间的距离容易出错。 | 

### <a name="how-to-measure"></a>如何测量

* 种交互的对象是识别为种交互';其中包括按钮、 菜单和应用程序特定的内容。 作为经验法则存在时应为视频和音频提示指向种交互的对象。

### <a name="recommendations"></a>建议

* 使用视频和音频反馈进行交互。
* 对于每个输入 （空闲、 目标、 所选） 的状态应区分可视反馈
* 应缩放并放置错误免费面向种交互的对象。
* 分组种交互对象 （如菜单栏或列表） 应具有针对适当的间距。
* 按钮和菜单支持语音命令应为命令关键字提供文本标签 （"来看，说"）

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [可交互对象](interactable-object.md)
* [Unity 中的文本](text-in-unity.md)
* [应用栏和边界框](app-bar-and-bounding-box.md)
* [语音命令](voice-design.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [混合的现实工具包-用户体验](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>扫描的房间

需要空间映射数据的应用程序依赖于设备要自动随着时间的推移收集这些数据，并跨会话作为用户与设备 active 探讨其环境。 完整性和此数据的质量取决于多种因素，包括用户已经进行了数量、 探索以来经过多少时间和家具和门之类的对象是否具有移动设备扫描区域之后。 许多应用程序将分析了体验，以判断用户是否应该执行附加步骤以提高完整性和质量空间映射的开头处的空间映射数据。 如果用户需要扫描环境中，清除应扫描体验期间提供的指导。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
|  空间网格的可视化效果告诉用户扫描正在进行中。 用户清楚地知道要执行的操作和扫描的启动和停止时。 | 提供空间网格的可视化效果，但用户不清楚地知道要执行的操作并提供进度的信息。 | 网格的任何可视化效果。 没有为用户提供有关在何处查找或当扫描启动/停止提供指导信息。 |

### <a name="how-to-measure"></a>如何测量

* 在所需的空间扫描期间，该值指示哪儿去，以及何时启动和停止扫描提供视频和音频指导。

### <a name="recommendations"></a>建议

* 指示用户邻近范围中的总卷大小必须是体验的一部分。
* 进行通信时在扫描开始和停止进度指示器等。
* 使用网格的扫描期间的可视化效果。
* 提供视觉和声音鼓励用户查找和移动的房间内的提示。
* 通知用户转到以提高数据的位置。 在许多情况下，可能是最好地告知用户他们需要执行操作 （例如回顾上限，在查找家具），以获取必要的扫描质量。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [房间扫描可视化](room-scan-visualization.md)
* [案例研究：扩展 HoloLens 的空间映射功能](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [案例研究：有关 HoloTour 空间合理的设计](case-study-spatial-sound-design-for-holotour.md)
* [案例研究：在片段中创建的沉浸式体验](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [混合的现实工具包-用户体验](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>方向指示器

在混合的现实应用中，内容可能不在视图的字段或封闭的实际对象。 设计良好的应用程序将便于用户查找不可见的内容。 方向指示器重要内容向用户发出警报，并提供指导以相对于用户的位置的内容。 非可见内容的指南可以采用声音发射器、 方向箭头或直接视觉提示的形式。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
|  视频和音频提示直接引导到外部的视图的字段的相关内容的用户。 | 一个箭头或指向内容的常规方向中的用户某个指示器。 | 相关内容是外部视野，以及较差或没有位置的指南提供给用户。 | 

### <a name="how-to-measure"></a>如何测量

* 外部用户视角的相关内容是通过 visual 和/或音频提示发现。

### <a name="recommendations"></a>建议

* 外部用户的视角相关的内容时，请使用方向指示器和音频提示来指导用户到达的内容。 在许多情况下，直接的可视指南优于方向箭头。
* 方向指示器不应内置光标。

### <a name="resources"></a>资源

* [全息帧](holographic-frame.md)

## <a name="data-loading"></a>数据加载

进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。 它可能表示用户不能与应用交互，当进度指示器可见，并且还可以指示等待时间可能是多长时间。

### <a name="device-impact"></a>设备的影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量准则

|  最佳  |  符合 |  失败 |
--- | --- | ---
|  经过动画处理的可视指示器，进度栏或环，在任何数据加载或处理期间显示进度的窗体中。 可视的指示器多长时间等待可能是提供指导。 | 数据加载过程中，但不会指示的时间可能是在等待时通知用户。 | 无数据加载或过程的时间超过 5 秒的任务的指示符。 |

### <a name="how-to-measure"></a>如何测量

* 在数据加载过程中验证多个 5 秒后没有任何空白状态。

### <a name="recommendations"></a>建议

* 提供在任何情况下显示进度时用户可能会觉察到此应用程序已停止或已崩溃数据加载动画器。 合理的经验法则是可能需要超过 5 秒的任何正在加载的活动。

### <a name="resources"></a>资源

* [显示进度](progress.md)
