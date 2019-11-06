---
title: 混合现实中的音频
description: 混合现实中的音频可以提高用户 UI 交互的用户信心，并从而深入了解用户体验。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空间音效，环绕声，3d 音频，3d 声音，空间音频
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641109"
---
# <a name="audio-in-mixed-reality"></a>混合现实中的音频
音频是混合现实中设计和生产力的必不可少部分，可以：
* 提高用户在手势和基于语音的交互中的置信度
* 指导用户接下来的步骤
* 有效地将虚拟对象与现实世界组合

混合现实耳机的低延迟头跟踪（包括 HoloLens）允许使用高质量的基于 HRTF 的 spatialization。 应用程序中的 Spatializing 音频可以：
* 注意视觉对象
* 帮助用户维护其真实环境的认知度

添加噪声更深入地连接到混合世界，并可提供有关环境和对象状态的提示。

有关使用音频设计的更详细示例，请参阅[声音设计](spatial-sound-design.md)。

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
        <td><strong>具有</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
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

## <a name="using-sounds-in-mixed-reality"></a>在混合现实中使用声音
[在混合现实中使用声音](spatial-sound-design.md)可能需要不同于触摸和键盘和鼠标应用程序的方法。 关键的设计决策包括哪些声音要 spatialize 以及哪些 sonify 交互。 这些决策可能会对用户置信度、工作效率和学习曲线产生很大影响。

### <a name="case-studies"></a>案例研究
HoloTour 几乎使用户能够在世界各地旅游和历史站点。 以下案例研究介绍了 HoloTour： HoloTour 的声音[设计](case-study-spatial-sound-design-for-holotour.md)。 使用特殊的麦克风和渲染设置来捕获使用者空间。

RoboRaid 是一种射击的高能耗。 以下案例研究介绍了用于确保空间音频最大效果的设计选择：[适用于 RoboRaid 的声音设计](case-study-using-spatial-sound-in-roboraid.md)。

## <a name="spatialization"></a>Spatialization
Spatialization 是空间音频的方向性组件。 使用7.1 家庭影院设置时，spatialization 非常简单，只是在高音扬声器之间进行平移。 但对于混合现实中的耳机，使用基于 HRTF 的技术是非常重要的。 Windows 提供基于 HRTF 的 spatialization，这种支持在 HoloLens 2 上是硬件加速的。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>我应该 spatialize 吗？
混合现实应用程序中的许多声音都受益于 spatialization，这会从侦听器的头部发出声音，并将其放在世界各地。 有关在应用程序中最有效地使用 spatialization 的建议，请参阅[空间音效设计](spatial-sound-design.md)。

### <a name="spatializer-personalization"></a>Spatializer 个性化
HRTFs 跨频率范围控制耳之间的级别和阶段差异。 它们基于物理型号和人机头、torso 和 ear （pinnae）的度量。 我们的大脑对这些差异做出了响应，从而提高了声音方向的认知度。 

每个人都有独特的耳形状、头大小和耳位置，因此最好的 HRTFs 是符合您的需要。 HoloLens 通过使用头戴显示在 spatialization 的距离（IPD）来调整头大小的 HRTFs。

### <a name="spatializer-platform-support"></a>Spatializer 平台支持
Windows 通过[ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 HRTFs。 此 API 向应用程序公开 HoloLens 2 HRTF 硬件加速。

### <a name="spatializer-middleware-support"></a>Spatializer 中间件支持
对于某些第三方音频引擎，支持 Windows HRTFs：
* [Unity 音频引擎](spatial-sound-in-unity.md)插件调用 HRTF XAPO
* [Wwise 音频引擎插件](https://www.audiokinetic.com/products/plug-ins/msspatial/)调用 ISpatialAudioClient API

## <a name="acoustics"></a>噪声
空间音频可能超出方向。 其他维度，包括封闭、障碍物、回音、portalling 和源建模，统称为 "噪声"。 如果没有噪声，spatialized 听起来就没有距离。

噪声处理范围从简单到非常复杂。 使用简单的回音，如任何音频引擎所支持的回音，你可以将 spatialized 的声音推送到侦听器周围的环境中。 可以从噪声系统（如[项目噪声](https://aka.ms/acoustics)）获得更丰富且更具吸引力的噪声处理。 项目噪声可以对墙壁、门和其他场景几何的效果进行建模，这是在开发时了解相关场景几何的情况的有效选项。

