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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="019b2-104">在 Unity 中的空间声音</span><span class="sxs-lookup"><span data-stu-id="019b2-104">Spatial sound in Unity</span></span>

<span data-ttu-id="019b2-105">本主题介绍如何在您的 Unity 项目中使用空间声音。</span><span class="sxs-lookup"><span data-stu-id="019b2-105">This topic describes how to use Spatial Sound in your Unity projects.</span></span> <span data-ttu-id="019b2-106">它介绍了必需的插件文件，以及 Unity 组件和启用空间声音的属性。</span><span class="sxs-lookup"><span data-stu-id="019b2-106">It covers the required plugin files as well as the Unity components and properties that enable Spatial Sound.</span></span>

## <a name="enabling-spatial-sound-in-unity"></a><span data-ttu-id="019b2-107">启用在 Unity 中的空间声音</span><span class="sxs-lookup"><span data-stu-id="019b2-107">Enabling Spatial Sound in Unity</span></span>

<span data-ttu-id="019b2-108">空间声音，在 Unity 中，使用音频 spatializer 插件启用。</span><span class="sxs-lookup"><span data-stu-id="019b2-108">Spatial Sound, in Unity, is enabled using an audio spatializer plugin.</span></span> <span data-ttu-id="019b2-109">插件文件捆绑到 Unity 直接以便启用空间声音非常简单，只转到**编辑 > 项目设置 > 音频**并更改**Spatializer 插件**到检查器中**MS HRTF Spatializer**。</span><span class="sxs-lookup"><span data-stu-id="019b2-109">The plugin files are bundled directly into Unity so enabling spatial sound is as easy as going to **Edit > Project Settings > Audio** and changing the **Spatializer Plugin** in the Inspector to the **MS HRTF Spatializer**.</span></span> <span data-ttu-id="019b2-110">由于 Microsoft spatializer 当前仅支持 48000 Hz，还应设置你系统采样率为 48000 以防止在极少数的情况下，你的系统输出设备未设置为 48000 已 HRTF 失败：</span><span class="sxs-lookup"><span data-stu-id="019b2-110">Since the Microsoft spatializer only supports 48000Hz currently, you should also set your System Sample Rate to 48000 to prevent an HRTF failure in the rare case that your system output device is not set to 48000 already:</span></span>

<span data-ttu-id="019b2-111">![AudioManager 的检查器](images/audio-250px.png)</span><span class="sxs-lookup"><span data-stu-id="019b2-111">![Inspector for AudioManager](images/audio-250px.png)</span></span><br>
<span data-ttu-id="019b2-112">*AudioManager 的检查器*</span><span class="sxs-lookup"><span data-stu-id="019b2-112">*Inspector for AudioManager*</span></span>

<span data-ttu-id="019b2-113">你的 Unity 项目现在已配置为使用空间声音。</span><span class="sxs-lookup"><span data-stu-id="019b2-113">Your Unity project is now configured to use Spatial Sound.</span></span>

>[!NOTE]
><span data-ttu-id="019b2-114">如果不使用 Windows 10 电脑进行开发，则不会获得空间声音在编辑器中，也不在设备上 （即使使用的 Windows 10 SDK）。</span><span class="sxs-lookup"><span data-stu-id="019b2-114">If you aren't using a Windows 10 PC for development, you won't get Spatial Sound in the editor nor on the device (even if you're using the Windows 10 SDK).</span></span>

## <a name="using-spatial-sound-in-unity"></a><span data-ttu-id="019b2-115">在 Unity 中使用空间的声音</span><span class="sxs-lookup"><span data-stu-id="019b2-115">Using Spatial Sound in Unity</span></span>

<span data-ttu-id="019b2-116">空间声音调整音频源组件上的三个设置使用在 Unity 项目中。</span><span class="sxs-lookup"><span data-stu-id="019b2-116">Spatial Sound is used in your Unity project by adjusting three settings on your Audio Source components.</span></span> <span data-ttu-id="019b2-117">以下步骤将配置为空间的声音将音频源组件。</span><span class="sxs-lookup"><span data-stu-id="019b2-117">The following steps will configure your Audio Source components for Spatial Sound.</span></span>
* <span data-ttu-id="019b2-118">在中**层次结构**面板中，选择具有一个附加的游戏对象**音频源**。</span><span class="sxs-lookup"><span data-stu-id="019b2-118">In the **Hierarchy** panel, select the game object that has an attached **Audio Source**.</span></span>
* <span data-ttu-id="019b2-119">在中**Inspector**面板下**音频源**组件</span><span class="sxs-lookup"><span data-stu-id="019b2-119">In the **Inspector** panel, under the **Audio Source** component</span></span>
    * <span data-ttu-id="019b2-120">检查**Spatialize**选项。</span><span class="sxs-lookup"><span data-stu-id="019b2-120">Check the **Spatialize** option.</span></span>
    * <span data-ttu-id="019b2-121">设置**空间 Blend**到**3D** （数字值 1）。</span><span class="sxs-lookup"><span data-stu-id="019b2-121">Set **Spatial Blend** to **3D** (numeric value 1).</span></span>
    * <span data-ttu-id="019b2-122">为获得最佳结果，展开**3D 声音设置**并设置**卷卷绕**到**自定义卷绕**。</span><span class="sxs-lookup"><span data-stu-id="019b2-122">For best results, expand **3D Sound Settings** and set **Volume Rolloff** to **Custom Rolloff**.</span></span>

<span data-ttu-id="019b2-123">![在 Unity 中显示音频源的检查器面板](images/audiosource.png)</span><span class="sxs-lookup"><span data-stu-id="019b2-123">![Inspector panel in Unity showing the Audio Source](images/audiosource.png)</span></span><br>
<span data-ttu-id="019b2-124">*在 Unity 中显示音频源的检查器面板*</span><span class="sxs-lookup"><span data-stu-id="019b2-124">*Inspector panel in Unity showing the Audio Source*</span></span>

<span data-ttu-id="019b2-125">将声音现在实际上存在于项目的环境内 ！</span><span class="sxs-lookup"><span data-stu-id="019b2-125">Your sounds now realistically exist inside your project's environment!</span></span>

<span data-ttu-id="019b2-126">强烈建议你熟悉[空间声音设计准则](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="019b2-126">It is strongly recommended that you become familiar with the [Spatial Sound design guidelines](spatial-sound-design.md).</span></span> <span data-ttu-id="019b2-127">这些准则有助于将您的音频无缝集成到你的项目并进一步可你的用户访问这个到已创建的体验。</span><span class="sxs-lookup"><span data-stu-id="019b2-127">These guidelines help to integrate your audio seamlessly into your project and to further immerse your users into the experience you have created.</span></span>

## <a name="setting-spatial-sound-settings"></a><span data-ttu-id="019b2-128">设置空间声音设置</span><span class="sxs-lookup"><span data-stu-id="019b2-128">Setting Spatial Sound Settings</span></span>

<span data-ttu-id="019b2-129">Microsoft 空间声音插件提供了一个额外的参数可设置，在每个音频源的基础，以允许音频模拟的更多控制。</span><span class="sxs-lookup"><span data-stu-id="019b2-129">The Microsoft Spatial Sound plugin provides an additional parameter that can be set, on a per Audio Source basis, to allow additional control of the audio simulation.</span></span> <span data-ttu-id="019b2-130">此参数是模拟房间的大小。</span><span class="sxs-lookup"><span data-stu-id="019b2-130">This parameter is the size of the simulated room.</span></span>

### <a name="room-size"></a><span data-ttu-id="019b2-131">空间大小</span><span class="sxs-lookup"><span data-stu-id="019b2-131">Room Size</span></span>

<span data-ttu-id="019b2-132">正在通过空间声音来模拟的空间大小。</span><span class="sxs-lookup"><span data-stu-id="019b2-132">The size of room that is being simulated by Spatial Sound.</span></span> <span data-ttu-id="019b2-133">聊天室的近似大小是;小 (到小型会议室 office)、 中 （大型会议房间） 和大型 （会堂）。</span><span class="sxs-lookup"><span data-stu-id="019b2-133">The approximate sizes of the rooms are; small (an office to a small conference room), medium (a large conference room) and large (an auditorium).</span></span> <span data-ttu-id="019b2-134">此外可以指定的空间大小为 none 以模拟户外环境。</span><span class="sxs-lookup"><span data-stu-id="019b2-134">You can also specify a room size of none to simulate an outdoor environment.</span></span> <span data-ttu-id="019b2-135">默认的空间大小很小。</span><span class="sxs-lookup"><span data-stu-id="019b2-135">The default room size is small.</span></span>

### <a name="example"></a><span data-ttu-id="019b2-136">示例</span><span class="sxs-lookup"><span data-stu-id="019b2-136">Example</span></span>

<span data-ttu-id="019b2-137">为 Unity MixedRealityToolkit 提供了使设置空间声音设置简单的静态类。</span><span class="sxs-lookup"><span data-stu-id="019b2-137">The MixedRealityToolkit for Unity provides a static class that makes setting the Spatial Sound settings easy.</span></span> <span data-ttu-id="019b2-138">此类可在[MixedRealityToolkit\SpatialSound 文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound)，可以从你的项目中的任何脚本调用。</span><span class="sxs-lookup"><span data-stu-id="019b2-138">This class can be found in the [MixedRealityToolkit\SpatialSound folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) and can be called from any script in your project.</span></span> <span data-ttu-id="019b2-139">建议在项目中这些参数在每个音频源组件上设置。</span><span class="sxs-lookup"><span data-stu-id="019b2-139">It is recommended that you set these parameters on each Audio Source component in your project.</span></span> <span data-ttu-id="019b2-140">下面的示例演示用于连接的音频源选择中等空间大小。</span><span class="sxs-lookup"><span data-stu-id="019b2-140">The following example shows selecting the medium room size for an attached Audio Source.</span></span>

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a><span data-ttu-id="019b2-141">直接访问 Unity 中的参数</span><span class="sxs-lookup"><span data-stu-id="019b2-141">Directly Accessing Parameters from Unity</span></span>

<span data-ttu-id="019b2-142">如果不想要使用的极好的音频工具在 MixedRealityToolkit，下面是如何将 HRTF 参数。</span><span class="sxs-lookup"><span data-stu-id="019b2-142">If you don't want to use the excellent Audio tools in the MixedRealityToolkit, here is how you would change HRTF Parameters.</span></span> <span data-ttu-id="019b2-143">您可以复制/粘贴此到一个名为脚本*SetHRTF.cs*想要将附加到每个 HRTF AudioSource。</span><span class="sxs-lookup"><span data-stu-id="019b2-143">You can copy/paste this into a script called *SetHRTF.cs* that you will want to attach to every HRTF AudioSource.</span></span> <span data-ttu-id="019b2-144">它允许您为 HRTF 更改重要的参数。</span><span class="sxs-lookup"><span data-stu-id="019b2-144">It lets you change parameters important to HRTF.</span></span>

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a><span data-ttu-id="019b2-145">混合的现实工具包中的空间声音</span><span class="sxs-lookup"><span data-stu-id="019b2-145">Spatial Sound in Mixed Reality Toolkit</span></span>
- [<span data-ttu-id="019b2-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="019b2-146">HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

<span data-ttu-id="019b2-147">混合现实工具包中的以下示例是常规的音频效果示例演示如何通过使用声音，使你的体验更多沉浸式的。</span><span class="sxs-lookup"><span data-stu-id="019b2-147">The following examples from the Mixed Reality Toolkit are general audio effect examples that demonstrate ways to make your experiences more immersive by using sound.</span></span>
- [<span data-ttu-id="019b2-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span><span class="sxs-lookup"><span data-stu-id="019b2-148">HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [<span data-ttu-id="019b2-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span><span class="sxs-lookup"><span data-stu-id="019b2-149">HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a><span data-ttu-id="019b2-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="019b2-150">See also</span></span>
* [<span data-ttu-id="019b2-151">空间声音</span><span class="sxs-lookup"><span data-stu-id="019b2-151">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="019b2-152">空间合理的设计</span><span class="sxs-lookup"><span data-stu-id="019b2-152">Spatial sound design</span></span>](spatial-sound-design.md)
