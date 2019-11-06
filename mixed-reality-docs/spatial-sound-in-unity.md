---
title: Unity 中的空间音效
description: 播放来自 Unity 场景中特定三维点的空间声音。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity，空间音效，HRTF，房间大小
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641075"
---
# <a name="spatial-sound-in-unity"></a>Unity 中的空间音效

此页链接到可帮助你在 Unity 混合现实项目中使用和设计 Microsoft HRTF spatializer 的资源。

## <a name="enable-spatialization"></a>启用 spatialization

在项目的音频设置中启用**MS HRTF Spatializer** 。 有关更多详细信息，请参阅[Unity 的 spatializer 文档](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)。 

将**音频源**附加到层次结构中的对象，并启用 spatialization，方法是选中 "**启用 spatialization** " 复选框，并将 "**空间混合**" 滑块移动到 "1"。 有关更多详细信息，请参阅[Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)。 

## <a name="design-with-spatialization"></a>用 spatialization 进行设计

### <a name="distance-based-attenuation"></a>基于距离的衰减
Unity 的默认基于距离的衰减的最小距离为1米，最大距离为500米，对数 rolloff。 这可能适用于你的方案，你可能会发现源衰减太快或太慢。 若要了解如何在 Unity 中设置这些曲线的信息[，请参阅](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)[混合现实中的声音设计](spatial-sound-design.md)。

### <a name="environment"></a>环境
**MS HRTF Spatializer**包括一个具有[四个回音设置](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment)且默认值为 "small" 的房间回音组件。 可以通过将以下C#脚本附加到 Unity 中具有 Spatialized 音频源的每个对象，以编程方式更改每个音频源的空间设置：

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

## <a name="unity-spatial-sound-examples"></a>Unity 空间声音示例
混合现实工具包（MRTK）包括在混合现实中应用音频效果的方式的示例： [MRTK 演示](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)。

