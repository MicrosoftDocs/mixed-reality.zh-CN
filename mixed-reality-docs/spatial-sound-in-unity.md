---
title: Unity 中的空间音效
description: 播放来自 Unity 场景中特定三维点的空间声音。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 空间音效, HRTF, 房间大小
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549084"
---
# <a name="spatial-sound-in-unity"></a>Unity 中的空间音效

本主题介绍如何在 Unity 项目中使用空间声音。 它包含所需的插件文件以及启用空间音效的 Unity 组件和属性。

## <a name="enabling-spatial-sound-in-unity"></a>在 Unity 中启用空间音效

使用音频 spatializer 插件启用了 Unity 中的空间音效。 插件文件直接捆绑到 Unity 中, 因此启用空间声音非常简单, 只需**编辑 > 音频 > 项目设置**, 然后将检查器中的**Spatializer 插件**改为**MS HRTF Spatializer**。 由于 Microsoft spatializer 仅支持 48000Hz, 因此还应将系统采样率设置为 48000, 以防止在系统输出设备未设置为48000的罕见情况下出现 HRTF 故障:

![AudioManager 的检查器](images/audio-250px.png)<br>
*AudioManager 的检查器*

Unity 项目现在已配置为使用空间音效。

>[!NOTE]
>如果你没有使用 Windows 10 电脑进行开发, 则不会在编辑器中或设备上获得空间音质 (即使你使用的是 Windows 10 SDK)。

## <a name="using-spatial-sound-in-unity"></a>在 Unity 中使用空间音效

通过在音频源组件上调整三个设置, 可在 Unity 项目中使用空间声音。 以下步骤将为空间音效配置音频源组件。
* 在 "**层次结构**" 面板中, 选择具有附加**音频源**的游戏对象。
* 在 "**检查器**" 面板中的 "**音频源**" 组件下
    * 检查**Spatialize**选项。
    * 将**空间 Blend**设置为**3d** (数值 1)。
    * 为获得最佳结果, 请展开 " **3D 声音设置**", 并将**Volume Rolloff**设置为**自定义 Rolloff**。

![Unity 中显示音频源的检查器面板](images/audiosource.png)<br>
*Unity 中显示音频源的检查器面板*

你的声音现在实际存在于你的项目环境中!

强烈建议您熟悉[空间音效设计准则](spatial-sound-design.md)。 这些指南可帮助你将音频无缝集成到你的项目中, 并进一步使用户从而深入了解你创建的体验。

## <a name="setting-spatial-sound-settings"></a>设置空间音质设置

Microsoft 空间声音插件提供一个附加参数, 该参数可根据每个音频源进行设置, 以允许对音频模拟进行更多的控制。 此参数为模拟房间的大小。

### <a name="room-size"></a>空间大小

空间音效正在模拟的空间大小。 房间的大致大小为;小型 (办公室到小型会议室)、中型 (大会议室) 和大 (auditorium)。 还可以指定 "无" 的房间大小来模拟户外环境。 默认房间大小为小。

### <a name="example"></a>示例

MixedRealityToolkit for Unity 提供了一个静态类, 使设置空间声音设置变得简单。 此类可在[MixedRealityToolkit\SpatialSound 文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)中找到, 并且可以从项目中的任何脚本中调用。 建议你在项目中的每个音频源组件上设置这些参数。 下面的示例演示如何为附加音频源选择 "介质空间大小"。

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>直接从 Unity 访问参数

如果不想使用 MixedRealityToolkit 中的优秀音频工具, 请参阅以下内容: 更改 HRTF 参数的方式。 你可以将其复制/粘贴到名为*SetHRTF.cs*的脚本中, 你需要将其附加到每个 HRTF AudioSource。 它使你可以更改对 HRTF 重要的参数。

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>混合现实工具包中的空间音效
- [HoloToolkit-Examples/SpatialSound/场景/UAudioManagerTest](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

混合现实工具包中的以下示例是一般的音频效果示例, 演示使用声音提高体验的方式。
- [HoloToolkit-Examples/SpatialSound/场景/AudioLoFiTest](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/场景/AudioOcclusionTest](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>请参阅
* [空间音效](spatial-sound.md)
* [空间音效设计](spatial-sound-design.md)
