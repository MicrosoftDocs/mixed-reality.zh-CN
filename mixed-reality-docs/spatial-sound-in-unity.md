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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="0bb44-104">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="0bb44-104">Spatial Sound in Unity</span></span>

<span data-ttu-id="0bb44-105">此页链接到可帮助你在 Unity 混合现实项目中使用和设计 Microsoft HRTF spatializer 的资源。</span><span class="sxs-lookup"><span data-stu-id="0bb44-105">This page links to resources to help you use and design with the Microsoft HRTF spatializer in your Unity mixed reality projects.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="0bb44-106">启用 spatialization</span><span class="sxs-lookup"><span data-stu-id="0bb44-106">Enable spatialization</span></span>

<span data-ttu-id="0bb44-107">在项目的音频设置中启用**MS HRTF Spatializer** 。</span><span class="sxs-lookup"><span data-stu-id="0bb44-107">Enable the **MS HRTF Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="0bb44-108">有关更多详细信息，请参阅[Unity 的 spatializer 文档](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)。</span><span class="sxs-lookup"><span data-stu-id="0bb44-108">For more details, see [Unity's spatializer documentation](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span></span> 

<span data-ttu-id="0bb44-109">将**音频源**附加到层次结构中的对象，并启用 spatialization，方法是选中 "**启用 spatialization** " 复选框，并将 "**空间混合**" 滑块移动到 "1"。</span><span class="sxs-lookup"><span data-stu-id="0bb44-109">Attach an **Audio Source** to an object in the hierarchy, and enable spatialization by checking the **Enable spatialization** checkbox and moving the **Spatial Blend** slider to '1'.</span></span> <span data-ttu-id="0bb44-110">有关更多详细信息，请参阅[Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)。</span><span class="sxs-lookup"><span data-stu-id="0bb44-110">For more details, see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span></span> 

## <a name="design-with-spatialization"></a><span data-ttu-id="0bb44-111">用 spatialization 进行设计</span><span class="sxs-lookup"><span data-stu-id="0bb44-111">Design with spatialization</span></span>

### <a name="distance-based-attenuation"></a><span data-ttu-id="0bb44-112">基于距离的衰减</span><span class="sxs-lookup"><span data-stu-id="0bb44-112">Distance-based attenuation</span></span>
<span data-ttu-id="0bb44-113">Unity 的默认基于距离的衰减的最小距离为1米，最大距离为500米，对数 rolloff。</span><span class="sxs-lookup"><span data-stu-id="0bb44-113">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="0bb44-114">这可能适用于你的方案，你可能会发现源衰减太快或太慢。</span><span class="sxs-lookup"><span data-stu-id="0bb44-114">This may work for your scenario, or you may find sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="0bb44-115">若要了解如何在 Unity 中设置这些曲线的信息[，请参阅](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)[混合现实中的声音设计](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="0bb44-115">See [sound design in mixed reality](spatial-sound-design.md) for recommended settings for distance decay curves, and see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for information on setting these curves in Unity.</span></span>

### <a name="environment"></a><span data-ttu-id="0bb44-116">环境</span><span class="sxs-lookup"><span data-stu-id="0bb44-116">Environment</span></span>
<span data-ttu-id="0bb44-117">**MS HRTF Spatializer**包括一个具有[四个回音设置](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment)且默认值为 "small" 的房间回音组件。</span><span class="sxs-lookup"><span data-stu-id="0bb44-117">The **MS HRTF Spatializer** includes a room reverb component with [four reverb settings](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) and a default of 'small'.</span></span> <span data-ttu-id="0bb44-118">可以通过将以下C#脚本附加到 Unity 中具有 Spatialized 音频源的每个对象，以编程方式更改每个音频源的空间设置：</span><span class="sxs-lookup"><span data-stu-id="0bb44-118">The room setting can be changed programmatically for each audio source by attaching the following C# script to each object in Unity that has a spatialized Audio Source:</span></span>

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

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="0bb44-119">Unity 空间声音示例</span><span class="sxs-lookup"><span data-stu-id="0bb44-119">Unity spatial sound examples</span></span>
<span data-ttu-id="0bb44-120">混合现实工具包（MRTK）包括在混合现实中应用音频效果的方式的示例： [MRTK 演示](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)。</span><span class="sxs-lookup"><span data-stu-id="0bb44-120">The Mixed Reality Toolkit (MRTK) includes examples of ways to apply audio effects in mixed reality: [MRTK demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span></span>

