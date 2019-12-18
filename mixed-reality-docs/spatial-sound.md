---
title: 混合现实中的音频
description: 混合现实中的音频可以提高用户 UI 交互的用户信心，并从而深入了解用户体验。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空间音效，环绕声，3d 音频，3d 声音，空间音频
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181977"
---
# <a name="audio-in-mixed-reality"></a>混合现实中的音频
音频是混合现实中设计和生产力的必不可少部分。 声音可以：
* 提高用户在手势和语音交互中的置信度。
* 指导用户接下来的步骤。
* 有效地将虚拟对象与现实世界组合在一起。

混合现实耳机的低延迟标题跟踪（包括 HoloLens）支持高质量的基于 HRTF 的 spatialization。 你可以在应用程序中 spatialize 音频，以执行以下操作：
* 注意视觉对象。
* 帮助用户保持对真实世界环境的认知。

噪声更深入地连接到混合现实世界。 它提供有关环境和对象状态的提示。

请参阅[使用音频的设计的详细示例](spatial-sound-design.md)。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第一代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>Spatialization</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Spatialization 硬件加速</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>在混合现实中使用声音
[混合现实中使用声音](spatial-sound-design.md)需要不同于触摸和键盘和鼠标应用程序的方法。 关键的设计决策包括哪些声音要 spatialize 以及哪些 sonify 交互。 这些决策会大大影响用户的置信度、生产力和学习曲线。

### <a name="case-studies"></a>案例研究
HoloTour 几乎使用户能够在世界各地旅游和历史站点。 请参阅 HoloTour 案例研究的[声音设计](case-study-spatial-sound-design-for-holotour.md)。 使用特殊的麦克风和渲染设置来捕获使用者空间。

RoboRaid 是一种射击的高能耗。 RoboRaid 案例研究的[声音设计](case-study-using-spatial-sound-in-roboraid.md)介绍了用于确保空间音频最大效果的设计选择。

## <a name="spatialization"></a>Spatialization
Spatialization 是空间音频的方向性组件。 对于7.1 家庭影院设置，spatialization 与 loudspeakers 之间的平移非常简单。 但对于混合现实中的耳机，使用基于 HRTF 的技术是非常重要的。 Windows 提供基于 HRTF 的 spatialization，这种支持在 HoloLens 2 上是硬件加速的。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>我应该 spatialize 吗？
Spatialization 可以改进混合现实应用程序中的许多声音。 Spatialization 从侦听器的头中取出声音，并将其放在世界各地。 有关在应用程序中有效使用 spatialization 的建议，请参阅[空间音效设计](spatial-sound-design.md)。

### <a name="spatializer-personalization"></a>Spatializer 个性化
HRTFs 跨频率范围控制耳之间的级别和阶段差异。 它们基于物理型号和人机头、torso 和 ear （pinnae）的度量。 我们大脑对这些差异做出了响应，以提供合理的声音方向。

每个人都有独特的耳形状、头大小和耳位置。 因此，最佳 HRTFs 与你相符。 为了提高 spatialization 准确度，HoloLens 使用头戴显示在 pupilary 距离（IPD）来调整头大小的 HRTFs。

### <a name="spatializer-platform-support"></a>Spatializer 平台支持
Windows 通过[ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 HRTFs。 此 API 向应用程序公开 HoloLens 2 HRTF 硬件加速。

### <a name="spatializer-middleware-support"></a>Spatializer 中间件支持
以下第三方音频引擎提供对 Windows "HRTFs 的支持。
* [Unity 音频引擎插件](spatial-sound-in-unity.md)
* [Wwise 音频引擎插件](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>噪声
空间音频约为方向。 其他维度包括封闭、障碍、回音、portalling 和源建模。 这些维度统称为 "*噪声*"。 如果没有噪声，spatialized 声音就会缺少距离。

噪声治疗范围从简单到非常复杂。 可以使用任何音频引擎支持的简单回音，将 spatialized 的声音推送到侦听器的环境中。 诸如[项目噪声](https://aka.ms/acoustics)等噪声系统提供更丰富且更具吸引力的噪声处理。 项目噪声可以为声音上的墙壁、门和其他场景几何的效果建模。 这是一个有效的选项，适用于在开发时了解相关场景几何图形的情况。

## <a name="next-steps"></a>后续步骤
- [Unity 中的空间音效](spatial-sound-in-unity.md)
- [如何在混合现实应用程序中使用声音](spatial-sound-design.md)
