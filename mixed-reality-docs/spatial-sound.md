---
title: 空间音效
description: 混合的现实应用程序中使用空间的声音，可将声音 convincingly 放置在 3D 空间中。
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 空间声音、 环绕声、 3d 音频、 3d 声音、 空间音频
ms.openlocfilehash: ccb236a8b53e757ba632a1c7c6cb2d4f07735910
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592146"
---
# <a name="spatial-sound"></a>空间音效

当对象超出我们直通时，我们可以认为这怎么回事周围的方法之一是通过声音。 在 Windows Mixed Reality 音频引擎提供混合现实体验的语音组件通过模拟使用方向、 距离和环境模拟三维声音。 应用程序中使用空间声音各地用户允许开发人员将声音 convincingly 放在 3 个维空间 （球体）。 这些听起来然后将看起来像其视为来自用户的环境中混合的现实全息或实际的物理对象。 鉴于[全息](hologram.md)对象进行的光线和有时声音，声音组件可以帮助地面全息使它们更可信并创建更多沉浸式体验。

尽管全息其中指向用户的视线移动只能以可视方式出现，但你的应用的声音可来自于所有方向;更高版本，下面，后面，到端，等等。此功能可用于吸引人们关注可能不在当前在用户的视图内的对象。 用户所能觉察出声音，以从混合现实世界中的源方面。 例如，用户更接近于一个对象或对象更接近于它们时，会增加该卷。 同样，当移动对象时围绕用户，或反之，空间声音错觉声音即将直接从该对象。

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>

<td> 空间音效</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ （使用耳机）</td>

</tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>模拟的感知到的位置和距离的声音

通过分析如何声音达到这两个我们的耳朵，我们的大脑确定距离和方向的对象发出声音。 HRTF （或 Head 相关传输函数） 通过建模 ear 如何接收来自点在空间中的声音的特点是光谱响应来模拟这种交互。 空间音频引擎使用个性化的 HRTFs 展开混合的现实体验，并模拟来自各种方向和距离的声音。

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

左或向右音频 （方位） 提示来自在每个 ear 到达声音的时间之间的差异。 向上和向下提示来自光谱由外部 ear 形状 (pinnae) 生成的更改。 通过指定音频的来源，其中系统可以模拟声音到我们的耳朵在不同时间到达的体验。 请注意，在 HoloLens，虽然方位 spatialization 进行个性化设置，提升模拟基于 anthropometrics 平均集。 因此，可能不太准确方位准确性比提升准确性。

声音的特征也根据所在的环境更改。 例如，在山洞地大喊大叫将导致您的声音弹开地面、 墙壁和上限，创建回显效果。 空间声音的房间模型设置会重现这些反射放置在特定音频环境中的声音。 可以使用此设置以匹配用户的实际位置模拟该空间中的音频来创建更多沉浸式的音频体验。

## <a name="integrating-spatial-sound"></a>将集成空间的声音

因为混合现实的一般原则是接地[全息](hologram.md)应在用户的物理环境或虚拟环境中，spatialized 全息中的大多数声音。 HoloLens 上, 有自然 CPU 和内存预算方面的考虑，但使用少于 ~ 12%的 CPU （~ 70%的一个四个核心) 时，可以使用 10-12 空间声音语音存在。 建议的用于空间声音语音包括：
* 注视混合 （突出显示对象，尤其是当出视野之外）。 当一张全息图需要用户注意时，该全息图上播放声音 （例如，具有虚拟 dog 虚张声势）。 这有助于用户查找全息图不在视图中时。
* 音频 Haptics （被动音频 touchless 之间的交互）。 例如，当用户的手或动画控制器进入并退出手势帧时播放声音。 或在用户选择一张全息图时播放声音。
* 浸入式 （用户周围环境声音）。

还有一点需要注意，而混合使用空间声音标准立体声声音可以是在创建实际环境中有效，立体声声音应相对安静以留出空间声音，如反射 （的细微方面距离提示），可能很难在嘈杂的环境。

Windows 的空间声音引擎仅支持一个 48 k 采样率进行播放。 大多数中间件，例如 Unity，自动将声音文件转换为受支持的格式，但直接使用 Windows 音频 Api 时请匹配受影响的格式对内容的格式。

## <a name="see-also"></a>请参阅
* [MR Spatial 220](holograms-220.md)
* [在 Unity 中的空间声音](spatial-sound-in-unity.md)
* [在 DirectX 空间声音](spatial-sound-in-directx.md)
* [空间合理的设计](spatial-sound-design.md)
