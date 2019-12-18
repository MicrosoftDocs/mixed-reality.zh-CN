---
title: Unity 中的空间音效
description: 从 Unity 场景内的特定3D 点播放空间声音。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity，空间音效，HRTF，房间大小
ms.openlocfilehash: 3e7d0ea231545d5112d182dffbc02f217ca4a4a7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181987"
---
# <a name="spatial-sound-in-unity"></a>Unity 中的空间音效

此页链接到 Unity 中的空间音效资源。

## <a name="spatializer-options"></a>Spatializer 选项
混合现实应用程序的 Spatializer 选项包括：
* *MS HRTF Spatializer*。 Unity 将其作为*Windows Mixed Reality*可选包的一部分提供。
  * 这会在具有较高成本的 "单一源" 体系结构的 CPU 上运行。
  * 这是为了向后兼容原 HoloLens 应用程序而提供的。
* *Microsoft Spatializer*。 可从[Microsoft Spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)获取此功能。
  * 这将使用较低成本的 "多源" 体系结构。
  * 在 HoloLens 2 上，这会被下放到硬件加速器。

对于新应用程序，我们建议*Microsoft Spatializer*。

## <a name="enable-spatialization"></a>启用 spatialization

使用[NuGet For unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)安装_SpatialAudio_ ，并在项目的音频设置中选择**microsoft Spatializer** 。 然后：
* 将**音频源**附加到层次结构中的对象
* 选中 "**启用 spatialization** " 复选框
* 将**空间混合**滑块移动到 "1"

有关更多详细信息，请参阅：
* [Microsoft spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft 的 spatializer 教程](unity-spatial-audio-ch1.md)
* [Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Unity 的 spatializer 文档](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>基于距离的衰减
Unity 的默认基于距离的衰减的最小距离为1米，最大距离为500米，对数 rolloff。 这些设置可能适用于你的方案，你可能会发现源衰减太快或太慢。 有关更多详细信息，请参阅：
* [混合现实中的声音设计](spatial-sound-design.md)建议的设置。
* [Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)，了解有关如何设置这些曲线的说明。

## <a name="reverb"></a>混响
默认情况下， _Microsoft Spatializer_禁用了 Spatializer 效果。 若要为 spatialized 源启用回响和其他效果：
* 将 "**房间效果发送级别**" 组件附加到每个源
* 调整每个源的发送级别曲线，以控制发送回图形以进行效果处理的音频的增益

有关详细信息，请参阅[spatializer 教程的第5章](unity-spatial-audio-ch5.md)。

## <a name="unity-spatial-sound-examples"></a>Unity 空间声音示例
有关 Unity 中空间音效的示例，请参阅：
* [MRTK 演示](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Microsoft Spatializer 示例项目](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-steps"></a>后续步骤
* [混合现实中的声音设计](spatial-sound-design.md)
* [Microsoft 的 spatializer 教程](unity-spatial-audio-ch1.md)

