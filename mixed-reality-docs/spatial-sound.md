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
# <a name="spatial-sound"></a><span data-ttu-id="aa8d7-104">空间音效</span><span class="sxs-lookup"><span data-stu-id="aa8d7-104">Spatial sound</span></span>

<span data-ttu-id="aa8d7-105">当对象不在我们的视觉对象中时，我们可以通过声音来了解我们的进展情况。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-105">When objects are out of our line of sight, one of the ways that we can perceive what's going on around us is through sound.</span></span> <span data-ttu-id="aa8d7-106">在 Windows Mixed Reality 中，音频引擎通过使用方向、距离和环境模拟模拟3D 声音，提供混合现实体验的听觉组件。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-106">In Windows Mixed Reality, the audio engine provides the aural component of the mixed-reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="aa8d7-107">在应用程序中使用空间音效使开发人员能够在整个用户的 convincingly 中放置声音。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-107">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="aa8d7-108">然后，这些声音看起来就像是来自真实的物理对象，或是用户的环境中的混合现实影像。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-108">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="aa8d7-109">由于[全息影像](hologram.md)是使对象变得很淡，有时很声音，sound 组件可帮助地面影像，使其更可信，并创建更多的沉浸式体验。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-109">Given that [holograms](hologram.md) are objects made of light and sometimes sound, the sound component helps ground holograms making them more believable and creating a more immersive experience.</span></span>

<span data-ttu-id="aa8d7-110">尽管只能直观地显示用户注视的位置，但你的应用程序的声音可能来自所有方向;上方、下方、后面、边缘等。您可以使用此功能来吸引用户当前不在用户视图中的对象。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-110">Although holograms can only appear visually where the user's gaze is pointing, your app's sound can come from all directions; above, below, behind, to the side, etc. You can use this feature to draw attention to an object that might not currently be in the user's view.</span></span> <span data-ttu-id="aa8d7-111">用户可以在混合现实世界中感觉到 emanating 的声音。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-111">A user can perceive sounds to be emanating from a source in the mixed-reality world.</span></span> <span data-ttu-id="aa8d7-112">例如，当用户接近对象或对象越接近时，卷就会增加。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-112">For example, as the user gets closer to an object or the object gets closer to them, the volume increases.</span></span> <span data-ttu-id="aa8d7-113">同样，当对象围绕用户移动时，或相反，空间声音会使声音直接来自对象。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-113">Similarly, as objects move around a user, or vice versa, spatial sounds give the illusion that sounds are coming directly from the object.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="aa8d7-114">设备支持</span><span class="sxs-lookup"><span data-stu-id="aa8d7-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="aa8d7-115"><strong>具有</strong></span><span class="sxs-lookup"><span data-stu-id="aa8d7-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="aa8d7-116"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="aa8d7-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="aa8d7-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="aa8d7-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="aa8d7-118"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="aa8d7-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="aa8d7-119">空间音效</span><span class="sxs-lookup"><span data-stu-id="aa8d7-119">Spatial sound</span></span></td>
        <td><span data-ttu-id="aa8d7-120">✔️</span><span class="sxs-lookup"><span data-stu-id="aa8d7-120">✔️</span></span></td>
        <td><span data-ttu-id="aa8d7-121">✔️</span><span class="sxs-lookup"><span data-stu-id="aa8d7-121">✔️</span></span></td>
        <td><span data-ttu-id="aa8d7-122">✔️（带耳机）</span><span class="sxs-lookup"><span data-stu-id="aa8d7-122">✔️ (with headphones)</span></span></td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a><span data-ttu-id="aa8d7-123">模拟声音的已知位置和距离</span><span class="sxs-lookup"><span data-stu-id="aa8d7-123">Simulating the perceived location and distance of sounds</span></span>

<span data-ttu-id="aa8d7-124">通过分析声音如何进入我们的耳，大脑确定发出声音的对象的距离和方向。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-124">By analyzing how sound reaches both our ears, our brain determines the distance and direction of the object emitting the sound.</span></span> <span data-ttu-id="aa8d7-125">HRTF （或头相关传输函数）通过对 spectral 响应进行建模来模拟这种交互，这些响应反映了耳如何从空间的某个点接收声音。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-125">An HRTF (or Head Related Transfer Function) simulates this interaction by modeling the spectral response that characterizes how an ear receives sound from a point in space.</span></span> <span data-ttu-id="aa8d7-126">空间音频引擎使用个性化的 HRTFs 来展开混合现实体验，并模拟来自各种方向和距离的声音。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-126">The spatial audio engine uses personalized HRTFs to expand the mixed reality experience, and simulate sounds that are coming from various directions and distances.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="aa8d7-127">左或右音频（azimuth）提示源自每个耳上的声音到达时的差异。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-127">Left or right audio (azimuth) cues originate from differences in the time sound arrives at each ear.</span></span> <span data-ttu-id="aa8d7-128">向上和向下提示源自外部 ear 形状（pinnae）生成的 spectral 更改。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-128">Up and down cues originate from spectral changes produced by the outer ear shape (pinnae).</span></span> <span data-ttu-id="aa8d7-129">通过指定音频的来源，系统可以模拟在不同时间到达我们的耳的声音体验。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-129">By designating where audio is coming from, the system can simulate the experience of sound arriving at different times to our ears.</span></span> <span data-ttu-id="aa8d7-130">请注意，在 HoloLens 上，azimuth spatialization 是个性化的，而提升的模拟基于一组平均的 anthropometrics。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-130">Note that on HoloLens, while azimuth spatialization is personalized, the simulation of elevation is based on an average set of anthropometrics.</span></span> <span data-ttu-id="aa8d7-131">因此，提升准确性可能低于 azimuth 准确性。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-131">Thus, elevation accuracy may be less accurate than azimuth accuracy.</span></span>

<span data-ttu-id="aa8d7-132">声音的特征也会根据其存在的环境而变化。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-132">The characteristics of sounds also change based on the environment in which they exist.</span></span> <span data-ttu-id="aa8d7-133">例如，洞穴中的驯养将导致你的声音弹到墙壁、地面和上限，从而产生回声效果。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-133">For instance, shouting in a cave will cause your voice to bounce off the walls, floors, and ceilings, creating an echo effect.</span></span> <span data-ttu-id="aa8d7-134">空间音效的房间模型设置会重现这些反射，以将声音置于特定音频环境中。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-134">The room model setting of spatial sound reproduces these reflections to place sounds in a particular audio environment.</span></span> <span data-ttu-id="aa8d7-135">您可以使用此设置来匹配用户在该空间中模拟声音的实际位置，以创建更沉浸的音频体验。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-135">You can use this setting to match the user's actual location for simulation of sounds in that space to create a more immersive audio experience.</span></span>

## <a name="integrating-spatial-sound"></a><span data-ttu-id="aa8d7-136">集成空间音效</span><span class="sxs-lookup"><span data-stu-id="aa8d7-136">Integrating spatial sound</span></span>

<span data-ttu-id="aa8d7-137">由于混合现实的一般原则是在用户的物理环境或虚拟环境中地面[影像](hologram.md)，因此来自全息影像的大多数声音都应该是 spatialized。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-137">Because the general principle of mixed reality is to ground [holograms](hologram.md) in the user's physical world or virtual environment, most sounds from holograms should be spatialized.</span></span> <span data-ttu-id="aa8d7-138">在 HoloLens 上，有自然的 CPU 和内存预算注意事项，但在使用小于 ~ 12% 的 CPU （大约四个核心中的一个70%）时，可以使用10-12 空间声音。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-138">On HoloLens, there are naturally CPU and memory budget considerations, but you can use 10-12 spatial sound voices there while using less than ~12% of the CPU (~70% of one of the four cores).</span></span> <span data-ttu-id="aa8d7-139">适用于空间音效的建议用途包括：</span><span class="sxs-lookup"><span data-stu-id="aa8d7-139">Recommended use for spatial sound voices include:</span></span>
* <span data-ttu-id="aa8d7-140">注视（突出显示对象，尤其是在离开视图时）。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-140">Gaze Mixing (highlighting objects, particularly when out of view).</span></span> <span data-ttu-id="aa8d7-141">当全息图需要用户注意时，请在该全息图上播放声音（例如，具有虚拟狗吠）。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-141">When a hologram needs a user's attention, play a sound on that hologram (e.g. have a virtual dog bark).</span></span> <span data-ttu-id="aa8d7-142">这可帮助用户在不处于视图中时查找全息影像。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-142">This helps the user to find the hologram when it is not in view.</span></span>
* <span data-ttu-id="aa8d7-143">音频 Haptics （反应音频 touchless 交互）。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-143">Audio Haptics (reactive audio for touchless interactions).</span></span> <span data-ttu-id="aa8d7-144">例如，当用户的手或运动控制器进入并退出该笔势帧时播放声音。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-144">For example, play a sound when the user's hand or motion controller enters and exits the gesture frame.</span></span> <span data-ttu-id="aa8d7-145">或在用户选择全息影像时播放声音。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-145">Or play a sound when the user selects a hologram.</span></span>
* <span data-ttu-id="aa8d7-146">浸入式（用户周围的环境声音）。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-146">Immersion (ambient sounds surrounding the user).</span></span>

<span data-ttu-id="aa8d7-147">另外还要注意的是，尽管将标准立体声声音与空间音效混合在创建逼真的环境中，但立体声声音应该相对安静，以便留出空间声音微妙的空间（如反射）距离提示），这种情况很难在干扰环境中听到。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-147">It is also important to note that while blending standard stereo sounds with spatial sound can be effective in creating realistic environments, the stereo sounds should be relatively quiet to leave room for the subtle aspects of spatial sound, such as reflections (distance cues) that can be difficult to hear in a noisy environment.</span></span>

<span data-ttu-id="aa8d7-148">Windows 空间音效引擎仅支持播放的48k 采样速率。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-148">Windows' spatial sound engine only supports a 48k sample rate for playback.</span></span> <span data-ttu-id="aa8d7-149">大多数中间件（如 Unity）会自动将声音文件转换为受支持的格式，但在使用 Windows 音频 Api 时，请将内容格式与该效果支持的格式相匹配。</span><span class="sxs-lookup"><span data-stu-id="aa8d7-149">Most middleware, such as Unity, will automatically convert sound files into the supported format, but when using Windows Audio APIs directly please match the format of the content to the format supported by the effect.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa8d7-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa8d7-150">See also</span></span>
* [<span data-ttu-id="aa8d7-151">MR 空间220</span><span class="sxs-lookup"><span data-stu-id="aa8d7-151">MR Spatial 220</span></span>](holograms-220.md)
* [<span data-ttu-id="aa8d7-152">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="aa8d7-152">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="aa8d7-153">DirectX 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="aa8d7-153">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="aa8d7-154">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="aa8d7-154">Spatial sound design</span></span>](spatial-sound-design.md)
