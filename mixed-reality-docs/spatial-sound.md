---
title: 空间音效
description: 混合的现实应用程序中使用空间的声音，可将声音 convincingly 放置在 3D 空间中。
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 空间声音、 环绕声、 3d 音频、 3d 声音、 空间音频
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829924"
---
# <a name="spatial-sound"></a><span data-ttu-id="f3311-104">空间音效</span><span class="sxs-lookup"><span data-stu-id="f3311-104">Spatial sound</span></span>

<span data-ttu-id="f3311-105">当对象超出我们直通时，我们可以认为这怎么回事周围的方法之一是通过声音。</span><span class="sxs-lookup"><span data-stu-id="f3311-105">When objects are out of our line of sight, one of the ways that we can perceive what's going on around us is through sound.</span></span> <span data-ttu-id="f3311-106">在 Windows Mixed Reality 音频引擎提供混合现实体验的语音组件通过模拟使用方向、 距离和环境模拟三维声音。</span><span class="sxs-lookup"><span data-stu-id="f3311-106">In Windows Mixed Reality, the audio engine provides the aural component of the mixed-reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="f3311-107">应用程序中使用空间声音各地用户允许开发人员将声音 convincingly 放在 3 个维空间 （球体）。</span><span class="sxs-lookup"><span data-stu-id="f3311-107">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="f3311-108">这些听起来然后将看起来像其视为来自用户的环境中混合的现实全息或实际的物理对象。</span><span class="sxs-lookup"><span data-stu-id="f3311-108">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="f3311-109">鉴于[全息](hologram.md)对象进行的光线和有时声音，声音组件可以帮助地面全息使它们更可信并创建更多沉浸式体验。</span><span class="sxs-lookup"><span data-stu-id="f3311-109">Given that [holograms](hologram.md) are objects made of light and sometimes sound, the sound component helps ground holograms making them more believable and creating a more immersive experience.</span></span>

<span data-ttu-id="f3311-110">尽管全息其中指向用户的视线移动只能以可视方式出现，但你的应用的声音可来自于所有方向;更高版本，下面，后面，到端，等等。此功能可用于吸引人们关注可能不在当前在用户的视图内的对象。</span><span class="sxs-lookup"><span data-stu-id="f3311-110">Although holograms can only appear visually where the user's gaze is pointing, your app's sound can come from all directions; above, below, behind, to the side, etc. You can use this feature to draw attention to an object that might not currently be in the user's view.</span></span> <span data-ttu-id="f3311-111">用户所能觉察出声音，以从混合现实世界中的源方面。</span><span class="sxs-lookup"><span data-stu-id="f3311-111">A user can perceive sounds to be emanating from a source in the mixed-reality world.</span></span> <span data-ttu-id="f3311-112">例如，用户更接近于一个对象或对象更接近于它们时，会增加该卷。</span><span class="sxs-lookup"><span data-stu-id="f3311-112">For example, as the user gets closer to an object or the object gets closer to them, the volume increases.</span></span> <span data-ttu-id="f3311-113">同样，当移动对象时围绕用户，或反之，空间声音错觉声音即将直接从该对象。</span><span class="sxs-lookup"><span data-stu-id="f3311-113">Similarly, as objects move around a user, or vice versa, spatial sounds give the illusion that sounds are coming directly from the object.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

## <a name="device-support"></a><span data-ttu-id="f3311-114">设备支持</span><span class="sxs-lookup"><span data-stu-id="f3311-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3311-115"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="f3311-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f3311-116"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3311-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f3311-117"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f3311-117"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f3311-118"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3311-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3311-119">空间音效</span><span class="sxs-lookup"><span data-stu-id="f3311-119">Spatial sound</span></span></td>
        <td><span data-ttu-id="f3311-120">✔️</span><span class="sxs-lookup"><span data-stu-id="f3311-120">✔️</span></span></td>
        <td><span data-ttu-id="f3311-121">✔️</span><span class="sxs-lookup"><span data-stu-id="f3311-121">✔️</span></span></td>
        <td><span data-ttu-id="f3311-122">✔️ （使用耳机）</span><span class="sxs-lookup"><span data-stu-id="f3311-122">✔️ (with headphones)</span></span></td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a><span data-ttu-id="f3311-123">模拟的感知到的位置和距离的声音</span><span class="sxs-lookup"><span data-stu-id="f3311-123">Simulating the perceived location and distance of sounds</span></span>

<span data-ttu-id="f3311-124">通过分析如何声音达到这两个我们的耳朵，我们的大脑确定距离和方向的对象发出声音。</span><span class="sxs-lookup"><span data-stu-id="f3311-124">By analyzing how sound reaches both our ears, our brain determines the distance and direction of the object emitting the sound.</span></span> <span data-ttu-id="f3311-125">HRTF （或 Head 相关传输函数） 通过建模 ear 如何接收来自点在空间中的声音的特点是光谱响应来模拟这种交互。</span><span class="sxs-lookup"><span data-stu-id="f3311-125">An HRTF (or Head Related Transfer Function) simulates this interaction by modeling the spectral response that characterizes how an ear receives sound from a point in space.</span></span> <span data-ttu-id="f3311-126">空间音频引擎使用个性化的 HRTFs 展开混合的现实体验，并模拟来自各种方向和距离的声音。</span><span class="sxs-lookup"><span data-stu-id="f3311-126">The spatial audio engine uses personalized HRTFs to expand the mixed reality experience, and simulate sounds that are coming from various directions and distances.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

<span data-ttu-id="f3311-127">左或向右音频 （方位） 提示来自在每个 ear 到达声音的时间之间的差异。</span><span class="sxs-lookup"><span data-stu-id="f3311-127">Left or right audio (azimuth) cues originate from differences in the time sound arrives at each ear.</span></span> <span data-ttu-id="f3311-128">向上和向下提示来自光谱由外部 ear 形状 (pinnae) 生成的更改。</span><span class="sxs-lookup"><span data-stu-id="f3311-128">Up and down cues originate from spectral changes produced by the outer ear shape (pinnae).</span></span> <span data-ttu-id="f3311-129">通过指定音频的来源，其中系统可以模拟声音到我们的耳朵在不同时间到达的体验。</span><span class="sxs-lookup"><span data-stu-id="f3311-129">By designating where audio is coming from, the system can simulate the experience of sound arriving at different times to our ears.</span></span> <span data-ttu-id="f3311-130">请注意，在 HoloLens，虽然方位 spatialization 进行个性化设置，提升模拟基于 anthropometrics 平均集。</span><span class="sxs-lookup"><span data-stu-id="f3311-130">Note that on HoloLens, while azimuth spatialization is personalized, the simulation of elevation is based on an average set of anthropometrics.</span></span> <span data-ttu-id="f3311-131">因此，可能不太准确方位准确性比提升准确性。</span><span class="sxs-lookup"><span data-stu-id="f3311-131">Thus, elevation accuracy may be less accurate than azimuth accuracy.</span></span>

<span data-ttu-id="f3311-132">声音的特征也根据所在的环境更改。</span><span class="sxs-lookup"><span data-stu-id="f3311-132">The characteristics of sounds also change based on the environment in which they exist.</span></span> <span data-ttu-id="f3311-133">例如，在山洞地大喊大叫将导致您的声音弹开地面、 墙壁和上限，创建回显效果。</span><span class="sxs-lookup"><span data-stu-id="f3311-133">For instance, shouting in a cave will cause your voice to bounce off the walls, floors, and ceilings, creating an echo effect.</span></span> <span data-ttu-id="f3311-134">空间声音的房间模型设置会重现这些反射放置在特定音频环境中的声音。</span><span class="sxs-lookup"><span data-stu-id="f3311-134">The room model setting of spatial sound reproduces these reflections to place sounds in a particular audio environment.</span></span> <span data-ttu-id="f3311-135">可以使用此设置以匹配用户的实际位置模拟该空间中的音频来创建更多沉浸式的音频体验。</span><span class="sxs-lookup"><span data-stu-id="f3311-135">You can use this setting to match the user's actual location for simulation of sounds in that space to create a more immersive audio experience.</span></span>

## <a name="integrating-spatial-sound"></a><span data-ttu-id="f3311-136">将集成空间的声音</span><span class="sxs-lookup"><span data-stu-id="f3311-136">Integrating spatial sound</span></span>

<span data-ttu-id="f3311-137">因为混合现实的一般原则是接地[全息](hologram.md)应在用户的物理环境或虚拟环境中，spatialized 全息中的大多数声音。</span><span class="sxs-lookup"><span data-stu-id="f3311-137">Because the general principle of mixed reality is to ground [holograms](hologram.md) in the user's physical world or virtual environment, most sounds from holograms should be spatialized.</span></span> <span data-ttu-id="f3311-138">HoloLens 上, 有自然 CPU 和内存预算方面的考虑，但使用少于 ~ 12%的 CPU （~ 70%的一个四个核心) 时，可以使用 10-12 空间声音语音存在。</span><span class="sxs-lookup"><span data-stu-id="f3311-138">On HoloLens, there are naturally CPU and memory budget considerations, but you can use 10-12 spatial sound voices there while using less than ~12% of the CPU (~70% of one of the four cores).</span></span> <span data-ttu-id="f3311-139">建议的用于空间声音语音包括：</span><span class="sxs-lookup"><span data-stu-id="f3311-139">Recommended use for spatial sound voices include:</span></span>
* <span data-ttu-id="f3311-140">注视混合 （突出显示对象，尤其是当出视野之外）。</span><span class="sxs-lookup"><span data-stu-id="f3311-140">Gaze Mixing (highlighting objects, particularly when out of view).</span></span> <span data-ttu-id="f3311-141">当一张全息图需要用户注意时，该全息图上播放声音 （例如，具有虚拟 dog 虚张声势）。</span><span class="sxs-lookup"><span data-stu-id="f3311-141">When a hologram needs a user's attention, play a sound on that hologram (e.g. have a virtual dog bark).</span></span> <span data-ttu-id="f3311-142">这有助于用户查找全息图不在视图中时。</span><span class="sxs-lookup"><span data-stu-id="f3311-142">This helps the user to find the hologram when it is not in view.</span></span>
* <span data-ttu-id="f3311-143">音频 Haptics （被动音频 touchless 之间的交互）。</span><span class="sxs-lookup"><span data-stu-id="f3311-143">Audio Haptics (reactive audio for touchless interactions).</span></span> <span data-ttu-id="f3311-144">例如，当用户的手或动画控制器进入并退出手势帧时播放声音。</span><span class="sxs-lookup"><span data-stu-id="f3311-144">For example, play a sound when the user's hand or motion controller enters and exits the gesture frame.</span></span> <span data-ttu-id="f3311-145">或在用户选择一张全息图时播放声音。</span><span class="sxs-lookup"><span data-stu-id="f3311-145">Or play a sound when the user selects a hologram.</span></span>
* <span data-ttu-id="f3311-146">浸入式 （用户周围环境声音）。</span><span class="sxs-lookup"><span data-stu-id="f3311-146">Immersion (ambient sounds surrounding the user).</span></span>

<span data-ttu-id="f3311-147">还有一点需要注意，而混合使用空间声音标准立体声声音可以是在创建实际环境中有效，立体声声音应相对安静以留出空间声音，如反射 （的细微方面距离提示），可能很难在嘈杂的环境。</span><span class="sxs-lookup"><span data-stu-id="f3311-147">It is also important to note that while blending standard stereo sounds with spatial sound can be effective in creating realistic environments, the stereo sounds should be relatively quiet to leave room for the subtle aspects of spatial sound, such as reflections (distance cues) that can be difficult to hear in a noisy environment.</span></span>

<span data-ttu-id="f3311-148">Windows 的空间声音引擎仅支持一个 48 k 采样率进行播放。</span><span class="sxs-lookup"><span data-stu-id="f3311-148">Windows' spatial sound engine only supports a 48k sample rate for playback.</span></span> <span data-ttu-id="f3311-149">大多数中间件，例如 Unity，自动将声音文件转换为受支持的格式，但直接使用 Windows 音频 Api 时请匹配受影响的格式对内容的格式。</span><span class="sxs-lookup"><span data-stu-id="f3311-149">Most middleware, such as Unity, will automatically convert sound files into the supported format, but when using Windows Audio APIs directly please match the format of the content to the format supported by the effect.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3311-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3311-150">See also</span></span>
* [<span data-ttu-id="f3311-151">MR Spatial 220</span><span class="sxs-lookup"><span data-stu-id="f3311-151">MR Spatial 220</span></span>](holograms-220.md)
* [<span data-ttu-id="f3311-152">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="f3311-152">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="f3311-153">DirectX 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="f3311-153">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="f3311-154">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="f3311-154">Spatial sound design</span></span>](spatial-sound-design.md)
