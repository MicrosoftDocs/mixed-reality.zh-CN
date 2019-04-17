---
title: 在 Unity 中的空间声音
description: 播放空间声音来自于您的 Unity 场景中的特定 3D 点。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity 中，空间声音 HRTF，空间大小
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590097"
---
# <a name="spatial-sound-in-unity"></a>在 Unity 中的空间声音

本主题介绍如何在您的 Unity 项目中使用空间声音。 它介绍了必需的插件文件，以及 Unity 组件和启用空间声音的属性。

## <a name="enabling-spatial-sound-in-unity"></a>启用在 Unity 中的空间声音

空间声音，在 Unity 中，使用音频 spatializer 插件启用。 插件文件捆绑到 Unity 直接以便启用空间声音非常简单，只转到**编辑 > 项目设置 > 音频**并更改**Spatializer 插件**到检查器中**MS HRTF Spatializer**。 由于 Microsoft spatializer 当前仅支持 48000 Hz，还应设置你系统采样率为 48000 以防止在极少数的情况下，你的系统输出设备未设置为 48000 已 HRTF 失败：

![AudioManager 的检查器](images/audio-250px.png)<br>
*AudioManager 的检查器*

你的 Unity 项目现在已配置为使用空间声音。

>[!NOTE]
>如果不使用 Windows 10 电脑进行开发，则不会获得空间声音在编辑器中，也不在设备上 （即使使用的 Windows 10 SDK）。

## <a name="using-spatial-sound-in-unity"></a>在 Unity 中使用空间的声音

空间声音调整音频源组件上的三个设置使用在 Unity 项目中。 以下步骤将配置为空间的声音将音频源组件。
* 在中**层次结构**面板中，选择具有一个附加的游戏对象**音频源**。
* 在中**Inspector**面板下**音频源**组件
    * 检查**Spatialize**选项。
    * 设置**空间 Blend**到**3D** （数字值 1）。
    * 为获得最佳结果，展开**3D 声音设置**并设置**卷卷绕**到**自定义卷绕**。

![在 Unity 中显示音频源的检查器面板](images/audiosource.png)<br>
*在 Unity 中显示音频源的检查器面板*

将声音现在实际上存在于项目的环境内 ！

强烈建议你熟悉[空间声音设计准则](spatial-sound-design.md)。 这些准则有助于将您的音频无缝集成到你的项目并进一步可你的用户访问这个到已创建的体验。

## <a name="setting-spatial-sound-settings"></a>设置空间声音设置

Microsoft 空间声音插件提供了一个额外的参数可设置，在每个音频源的基础，以允许音频模拟的更多控制。 此参数是模拟房间的大小。

### <a name="room-size"></a>空间大小

正在通过空间声音来模拟的空间大小。 聊天室的近似大小是;小 (到小型会议室 office)、 中 （大型会议房间） 和大型 （会堂）。 此外可以指定的空间大小为 none 以模拟户外环境。 默认的空间大小很小。

### <a name="example"></a>示例

为 Unity MixedRealityToolkit 提供了使设置空间声音设置简单的静态类。 此类可在[MixedRealityToolkit\SpatialSound 文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)，可以从你的项目中的任何脚本调用。 建议在项目中这些参数在每个音频源组件上设置。 下面的示例演示用于连接的音频源选择中等空间大小。

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>直接访问 Unity 中的参数

如果不想要使用的极好的音频工具在 MixedRealityToolkit，下面是如何将 HRTF 参数。 您可以复制/粘贴此到一个名为脚本*SetHRTF.cs*想要将附加到每个 HRTF AudioSource。 它允许您为 HRTF 更改重要的参数。

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>混合的现实工具包中的空间声音
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

混合现实工具包中的以下示例是常规的音频效果示例演示如何通过使用声音，使你的体验更多沉浸式的。
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>请参阅
* [空间声音](spatial-sound.md)
* [空间合理的设计](spatial-sound-design.md)
