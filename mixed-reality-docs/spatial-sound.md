---
title: 空间音效
description: 在混合现实应用程序中使用空间音效，可以 convincingly 将声音置于3D 空间。
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 空间音效，环绕声，3d 音频，3d 声音，空间音频
ms.openlocfilehash: 31ec8f88a060127daab9bf3afc970457ec7c90a3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437392"
---
# <a name="spatial-sound"></a>空间音效

当对象不在我们的视觉对象中时，我们可以通过声音来了解我们的进展情况。 在 Windows Mixed Reality 中，音频引擎通过使用方向、距离和环境模拟模拟3D 声音，提供混合现实体验的听觉组件。 在应用程序中使用空间音效使开发人员能够在整个用户的 convincingly 中放置声音。 然后，这些声音看起来就像是来自真实的物理对象，或是用户的环境中的混合现实影像。 由于[全息影像](hologram.md)是使对象变得很淡，有时很声音，sound 组件可帮助地面影像，使其更可信，并创建更多的沉浸式体验。

尽管只能直观地显示用户注视的位置，但你的应用程序的声音可能来自所有方向;上方、下方、后面、边缘等。您可以使用此功能来吸引用户当前不在用户视图中的对象。 用户可以在混合现实世界中感觉到 emanating 的声音。 例如，当用户接近对象或对象越接近时，卷就会增加。 同样，当对象围绕用户移动时，或相反，空间声音会使声音直接来自对象。

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
        <td>空间音效</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️（带耳机）</td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>模拟声音的已知位置和距离

通过分析声音如何进入我们的耳，大脑确定发出声音的对象的距离和方向。 HRTF （或头相关传输函数）通过对 spectral 响应进行建模来模拟这种交互，这些响应反映了耳如何从空间的某个点接收声音。 空间音频引擎使用个性化的 HRTFs 来展开混合现实体验，并模拟来自各种方向和距离的声音。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

左或右音频（azimuth）提示源自每个耳上的声音到达时的差异。 向上和向下提示源自外部 ear 形状（pinnae）生成的 spectral 更改。 通过指定音频的来源，系统可以模拟在不同时间到达我们的耳的声音体验。 请注意，在 HoloLens 上，azimuth spatialization 是个性化的，而提升的模拟基于一组平均的 anthropometrics。 因此，提升准确性可能低于 azimuth 准确性。

声音的特征也会根据其存在的环境而变化。 例如，洞穴中的驯养将导致你的声音弹到墙壁、地面和上限，从而产生回声效果。 空间音效的房间模型设置会重现这些反射，以将声音置于特定音频环境中。 您可以使用此设置来匹配用户在该空间中模拟声音的实际位置，以创建更沉浸的音频体验。

## <a name="integrating-spatial-sound"></a>集成空间音效

由于混合现实的一般原则是在用户的物理环境或虚拟环境中地面[影像](hologram.md)，因此来自全息影像的大多数声音都应该是 spatialized。 在 HoloLens 上，有自然的 CPU 和内存预算注意事项，但在使用小于 ~ 12% 的 CPU （大约四个核心中的一个70%）时，可以使用10-12 空间声音。 适用于空间音效的建议用途包括：
* 注视（突出显示对象，尤其是在离开视图时）。 当全息图需要用户注意时，请在该全息图上播放声音（例如，具有虚拟狗吠）。 这可帮助用户在不处于视图中时查找全息影像。
* 音频 Haptics （反应音频 touchless 交互）。 例如，当用户的手或运动控制器进入并退出该笔势帧时播放声音。 或在用户选择全息影像时播放声音。
* 浸入式（用户周围的环境声音）。

另外还要注意的是，尽管将标准立体声声音与空间音效混合在创建逼真的环境中，但立体声声音应该相对安静，以便留出空间声音微妙的空间（如反射）距离提示），这种情况很难在干扰环境中听到。

Windows 空间音效引擎仅支持播放的48k 采样速率。 大多数中间件（如 Unity）会自动将声音文件转换为受支持的格式，但在使用 Windows 音频 Api 时，请将内容格式与该效果支持的格式相匹配。

## <a name="see-also"></a>另请参阅
* [MR 空间220](holograms-220.md)
* [Unity 中的空间音效](spatial-sound-in-unity.md)
* [DirectX 中的空间音效](spatial-sound-in-directx.md)
* [空间音效设计](spatial-sound-design.md)
