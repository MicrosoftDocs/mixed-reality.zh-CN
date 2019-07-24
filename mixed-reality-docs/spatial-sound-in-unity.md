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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="8391f-104">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="8391f-104">Spatial sound in Unity</span></span>

<span data-ttu-id="8391f-105">本主题介绍如何在 Unity 项目中使用空间声音。</span><span class="sxs-lookup"><span data-stu-id="8391f-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="8391f-106">它包含所需的插件文件以及启用空间音效的 Unity 组件和属性。</span><span class="sxs-lookup"><span data-stu-id="8391f-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="8391f-107">在 Unity 中启用空间音效</span><span class="sxs-lookup"><span data-stu-id="8391f-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="8391f-108">使用音频 spatializer 插件启用了 Unity 中的空间音效。</span><span class="sxs-lookup"><span data-stu-id="8391f-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="8391f-109">插件文件直接捆绑到 Unity 中, 因此启用空间声音非常简单, 只需**编辑 > 音频 > 项目设置**, 然后将检查器中的**Spatializer 插件**改为**MS HRTF Spatializer**。</span><span class="sxs-lookup"><span data-stu-id="8391f-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="8391f-110">由于 Microsoft spatializer 仅支持 48000Hz, 因此还应将系统采样率设置为 48000, 以防止在系统输出设备未设置为48000的罕见情况下出现 HRTF 故障:</span><span class="sxs-lookup"><span data-stu-id="8391f-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="8391f-111">![AudioManager 的检查器](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="8391f-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="8391f-112">*AudioManager 的检查器*</span><span class="sxs-lookup"><span data-stu-id="8391f-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="8391f-113">Unity 项目现在已配置为使用空间音效。</span><span class="sxs-lookup"><span data-stu-id="8391f-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="8391f-114">如果你没有使用 Windows 10 电脑进行开发, 则不会在编辑器中或设备上获得空间音质 (即使你使用的是 Windows 10 SDK)。</span><span class="sxs-lookup"><span data-stu-id="8391f-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="8391f-115">在 Unity 中使用空间音效</span><span class="sxs-lookup"><span data-stu-id="8391f-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="8391f-116">通过在音频源组件上调整三个设置, 可在 Unity 项目中使用空间声音。</span><span class="sxs-lookup"><span data-stu-id="8391f-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="8391f-117">以下步骤将为空间音效配置音频源组件。</span><span class="sxs-lookup"><span data-stu-id="8391f-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="8391f-118">在 "**层次结构**" 面板中, 选择具有附加**音频源**的游戏对象。</span><span class="sxs-lookup"><span data-stu-id="8391f-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="8391f-119">在 "**检查器**" 面板中的 "**音频源**" 组件下</span><span class="sxs-lookup"><span data-stu-id="8391f-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="8391f-120">检查**Spatialize**选项。</span><span class="sxs-lookup"><span data-stu-id="8391f-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="8391f-121">将**空间 Blend**设置为**3d** (数值 1)。</span><span class="sxs-lookup"><span data-stu-id="8391f-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="8391f-122">为获得最佳结果, 请展开 " **3D 声音设置**", 并将**Volume Rolloff**设置为**自定义 Rolloff**。</span><span class="sxs-lookup"><span data-stu-id="8391f-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="8391f-123">![Unity 中显示音频源的检查器面板](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="8391f-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="8391f-124">*Unity 中显示音频源的检查器面板*</span><span class="sxs-lookup"><span data-stu-id="8391f-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="8391f-125">你的声音现在实际存在于你的项目环境中!</span><span class="sxs-lookup"><span data-stu-id="8391f-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="8391f-126">强烈建议您熟悉[空间音效设计准则](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="8391f-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="8391f-127">这些指南可帮助你将音频无缝集成到你的项目中, 并进一步使用户从而深入了解你创建的体验。</span><span class="sxs-lookup"><span data-stu-id="8391f-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="8391f-128">设置空间音质设置</span><span class="sxs-lookup"><span data-stu-id="8391f-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="8391f-129">Microsoft 空间声音插件提供一个附加参数, 该参数可根据每个音频源进行设置, 以允许对音频模拟进行更多的控制。</span><span class="sxs-lookup"><span data-stu-id="8391f-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="8391f-130">此参数为模拟房间的大小。</span><span class="sxs-lookup"><span data-stu-id="8391f-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="8391f-131">空间大小</span><span class="sxs-lookup"><span data-stu-id="8391f-131">Room Size</span></span>

<span data-ttu-id="8391f-132">空间音效正在模拟的空间大小。</span><span class="sxs-lookup"><span data-stu-id="8391f-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="8391f-133">房间的大致大小为;小型 (办公室到小型会议室)、中型 (大会议室) 和大 (auditorium)。</span><span class="sxs-lookup"><span data-stu-id="8391f-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="8391f-134">还可以指定 "无" 的房间大小来模拟户外环境。</span><span class="sxs-lookup"><span data-stu-id="8391f-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="8391f-135">默认房间大小为小。</span><span class="sxs-lookup"><span data-stu-id="8391f-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="8391f-136">示例</span><span class="sxs-lookup"><span data-stu-id="8391f-136">Example</span></span>

<span data-ttu-id="8391f-137">MixedRealityToolkit for Unity 提供了一个静态类, 使设置空间声音设置变得简单。</span><span class="sxs-lookup"><span data-stu-id="8391f-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="8391f-138">此类可在[MixedRealityToolkit\SpatialSound 文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)中找到, 并且可以从项目中的任何脚本中调用。</span><span class="sxs-lookup"><span data-stu-id="8391f-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="8391f-139">建议你在项目中的每个音频源组件上设置这些参数。</span><span class="sxs-lookup"><span data-stu-id="8391f-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="8391f-140">下面的示例演示如何为附加音频源选择 "介质空间大小"。</span><span class="sxs-lookup"><span data-stu-id="8391f-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="8391f-141">直接从 Unity 访问参数</span><span class="sxs-lookup"><span data-stu-id="8391f-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="8391f-142">如果不想使用 MixedRealityToolkit 中的优秀音频工具, 请参阅以下内容: 更改 HRTF 参数的方式。</span><span class="sxs-lookup"><span data-stu-id="8391f-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="8391f-143">你可以将其复制/粘贴到名为*SetHRTF.cs*的脚本中, 你需要将其附加到每个 HRTF AudioSource。</span><span class="sxs-lookup"><span data-stu-id="8391f-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="8391f-144">它使你可以更改对 HRTF 重要的参数。</span><span class="sxs-lookup"><span data-stu-id="8391f-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="8391f-145">混合现实工具包中的空间音效</span><span class="sxs-lookup"><span data-stu-id="8391f-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="8391f-146">HoloToolkit-Examples/SpatialSound/场景/UAudioManagerTest</span><span class="sxs-lookup"><span data-stu-id="8391f-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="8391f-147">混合现实工具包中的以下示例是一般的音频效果示例, 演示使用声音提高体验的方式。</span><span class="sxs-lookup"><span data-stu-id="8391f-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="8391f-148">HoloToolkit-Examples/SpatialSound/场景/AudioLoFiTest</span><span class="sxs-lookup"><span data-stu-id="8391f-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="8391f-149">HoloToolkit-Examples/SpatialSound/场景/AudioOcclusionTest</span><span class="sxs-lookup"><span data-stu-id="8391f-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="8391f-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="8391f-150">See also</span></span>
* [<span data-ttu-id="8391f-151">空间音效</span><span class="sxs-lookup"><span data-stu-id="8391f-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="8391f-152">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="8391f-152">Spatial sound design</span></span>](spatial-sound-design.md)
