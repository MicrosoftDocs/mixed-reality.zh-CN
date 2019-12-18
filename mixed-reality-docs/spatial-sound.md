---
title: 混合现实中的音频
description: 混合现实中的音频可以提高用户 UI 交互的用户信心，并从而深入了解用户体验。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空间音效，环绕声，3d 音频，3d 声音，空间音频
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181977"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="679f2-104">混合现实中的音频</span><span class="sxs-lookup"><span data-stu-id="679f2-104">Audio in mixed reality</span></span>
<span data-ttu-id="679f2-105">音频是混合现实中设计和生产力的必不可少部分。</span><span class="sxs-lookup"><span data-stu-id="679f2-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="679f2-106">声音可以：</span><span class="sxs-lookup"><span data-stu-id="679f2-106">Sound can:</span></span>
* <span data-ttu-id="679f2-107">提高用户在手势和语音交互中的置信度。</span><span class="sxs-lookup"><span data-stu-id="679f2-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="679f2-108">指导用户接下来的步骤。</span><span class="sxs-lookup"><span data-stu-id="679f2-108">Guide users to next steps.</span></span>
* <span data-ttu-id="679f2-109">有效地将虚拟对象与现实世界组合在一起。</span><span class="sxs-lookup"><span data-stu-id="679f2-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="679f2-110">混合现实耳机的低延迟标题跟踪（包括 HoloLens）支持高质量的基于 HRTF 的 spatialization。</span><span class="sxs-lookup"><span data-stu-id="679f2-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="679f2-111">你可以在应用程序中 spatialize 音频，以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="679f2-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="679f2-112">注意视觉对象。</span><span class="sxs-lookup"><span data-stu-id="679f2-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="679f2-113">帮助用户保持对真实世界环境的认知。</span><span class="sxs-lookup"><span data-stu-id="679f2-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="679f2-114">噪声更深入地连接到混合现实世界。</span><span class="sxs-lookup"><span data-stu-id="679f2-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="679f2-115">它提供有关环境和对象状态的提示。</span><span class="sxs-lookup"><span data-stu-id="679f2-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="679f2-116">请参阅[使用音频的设计的详细示例](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="679f2-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="679f2-117">设备支持</span><span class="sxs-lookup"><span data-stu-id="679f2-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="679f2-118"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="679f2-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="679f2-119"><a href="hololens-hardware-details.md"><strong>HoloLens （第一代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="679f2-119"><a href="hololens-hardware-details.md"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="679f2-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="679f2-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="679f2-121"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="679f2-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="679f2-122">Spatialization</span><span class="sxs-lookup"><span data-stu-id="679f2-122">Spatialization</span></span></td>
        <td><span data-ttu-id="679f2-123">✔️</span><span class="sxs-lookup"><span data-stu-id="679f2-123">✔️</span></span></td>
        <td><span data-ttu-id="679f2-124">✔️</span><span class="sxs-lookup"><span data-stu-id="679f2-124">✔️</span></span></td>
        <td><span data-ttu-id="679f2-125">✔️</span><span class="sxs-lookup"><span data-stu-id="679f2-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="679f2-126">Spatialization 硬件加速</span><span class="sxs-lookup"><span data-stu-id="679f2-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="679f2-127">✔️</span><span class="sxs-lookup"><span data-stu-id="679f2-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="679f2-128">在混合现实中使用声音</span><span class="sxs-lookup"><span data-stu-id="679f2-128">Use of sounds in mixed reality</span></span>
<span data-ttu-id="679f2-129">[混合现实中使用声音](spatial-sound-design.md)需要不同于触摸和键盘和鼠标应用程序的方法。</span><span class="sxs-lookup"><span data-stu-id="679f2-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="679f2-130">关键的设计决策包括哪些声音要 spatialize 以及哪些 sonify 交互。</span><span class="sxs-lookup"><span data-stu-id="679f2-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="679f2-131">这些决策会大大影响用户的置信度、生产力和学习曲线。</span><span class="sxs-lookup"><span data-stu-id="679f2-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="679f2-132">案例研究</span><span class="sxs-lookup"><span data-stu-id="679f2-132">Case studies</span></span>
<span data-ttu-id="679f2-133">HoloTour 几乎使用户能够在世界各地旅游和历史站点。</span><span class="sxs-lookup"><span data-stu-id="679f2-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="679f2-134">请参阅 HoloTour 案例研究的[声音设计](case-study-spatial-sound-design-for-holotour.md)。</span><span class="sxs-lookup"><span data-stu-id="679f2-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="679f2-135">使用特殊的麦克风和渲染设置来捕获使用者空间。</span><span class="sxs-lookup"><span data-stu-id="679f2-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="679f2-136">RoboRaid 是一种射击的高能耗。</span><span class="sxs-lookup"><span data-stu-id="679f2-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="679f2-137">RoboRaid 案例研究的[声音设计](case-study-using-spatial-sound-in-roboraid.md)介绍了用于确保空间音频最大效果的设计选择。</span><span class="sxs-lookup"><span data-stu-id="679f2-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="679f2-138">Spatialization</span><span class="sxs-lookup"><span data-stu-id="679f2-138">Spatialization</span></span>
<span data-ttu-id="679f2-139">Spatialization 是空间音频的方向性组件。</span><span class="sxs-lookup"><span data-stu-id="679f2-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="679f2-140">对于7.1 家庭影院设置，spatialization 与 loudspeakers 之间的平移非常简单。</span><span class="sxs-lookup"><span data-stu-id="679f2-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="679f2-141">但对于混合现实中的耳机，使用基于 HRTF 的技术是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="679f2-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="679f2-142">Windows 提供基于 HRTF 的 spatialization，这种支持在 HoloLens 2 上是硬件加速的。</span><span class="sxs-lookup"><span data-stu-id="679f2-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="679f2-143">我应该 spatialize 吗？</span><span class="sxs-lookup"><span data-stu-id="679f2-143">Should I spatialize?</span></span>
<span data-ttu-id="679f2-144">Spatialization 可以改进混合现实应用程序中的许多声音。</span><span class="sxs-lookup"><span data-stu-id="679f2-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="679f2-145">Spatialization 从侦听器的头中取出声音，并将其放在世界各地。</span><span class="sxs-lookup"><span data-stu-id="679f2-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="679f2-146">有关在应用程序中有效使用 spatialization 的建议，请参阅[空间音效设计](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="679f2-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="679f2-147">Spatializer 个性化</span><span class="sxs-lookup"><span data-stu-id="679f2-147">Spatializer personalization</span></span>
<span data-ttu-id="679f2-148">HRTFs 跨频率范围控制耳之间的级别和阶段差异。</span><span class="sxs-lookup"><span data-stu-id="679f2-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="679f2-149">它们基于物理型号和人机头、torso 和 ear （pinnae）的度量。</span><span class="sxs-lookup"><span data-stu-id="679f2-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="679f2-150">我们大脑对这些差异做出了响应，以提供合理的声音方向。</span><span class="sxs-lookup"><span data-stu-id="679f2-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="679f2-151">每个人都有独特的耳形状、头大小和耳位置。</span><span class="sxs-lookup"><span data-stu-id="679f2-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="679f2-152">因此，最佳 HRTFs 与你相符。</span><span class="sxs-lookup"><span data-stu-id="679f2-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="679f2-153">为了提高 spatialization 准确度，HoloLens 使用头戴显示在 pupilary 距离（IPD）来调整头大小的 HRTFs。</span><span class="sxs-lookup"><span data-stu-id="679f2-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="679f2-154">Spatializer 平台支持</span><span class="sxs-lookup"><span data-stu-id="679f2-154">Spatializer platform support</span></span>
<span data-ttu-id="679f2-155">Windows 通过[ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 HRTFs。</span><span class="sxs-lookup"><span data-stu-id="679f2-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="679f2-156">此 API 向应用程序公开 HoloLens 2 HRTF 硬件加速。</span><span class="sxs-lookup"><span data-stu-id="679f2-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="679f2-157">Spatializer 中间件支持</span><span class="sxs-lookup"><span data-stu-id="679f2-157">Spatializer middleware support</span></span>
<span data-ttu-id="679f2-158">以下第三方音频引擎提供对 Windows "HRTFs 的支持。</span><span class="sxs-lookup"><span data-stu-id="679f2-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="679f2-159">[Unity 音频引擎插件](spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="679f2-159">A [Unity audio engine plugin](spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="679f2-160">[Wwise 音频引擎插件](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span><span class="sxs-lookup"><span data-stu-id="679f2-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="679f2-161">噪声</span><span class="sxs-lookup"><span data-stu-id="679f2-161">Acoustics</span></span>
<span data-ttu-id="679f2-162">空间音频约为方向。</span><span class="sxs-lookup"><span data-stu-id="679f2-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="679f2-163">其他维度包括封闭、障碍、回音、portalling 和源建模。</span><span class="sxs-lookup"><span data-stu-id="679f2-163">Other dimensions include occlusion, obstruction, reverb, portalling, and source modeling.</span></span> <span data-ttu-id="679f2-164">这些维度统称为 "*噪声*"。</span><span class="sxs-lookup"><span data-stu-id="679f2-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="679f2-165">如果没有噪声，spatialized 声音就会缺少距离。</span><span class="sxs-lookup"><span data-stu-id="679f2-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="679f2-166">噪声治疗范围从简单到非常复杂。</span><span class="sxs-lookup"><span data-stu-id="679f2-166">Acoustics treatments range from simple to very complex.</span></span> <span data-ttu-id="679f2-167">可以使用任何音频引擎支持的简单回音，将 spatialized 的声音推送到侦听器的环境中。</span><span class="sxs-lookup"><span data-stu-id="679f2-167">You can use a simple reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="679f2-168">诸如[项目噪声](https://aka.ms/acoustics)等噪声系统提供更丰富且更具吸引力的噪声处理。</span><span class="sxs-lookup"><span data-stu-id="679f2-168">Acoustics systems such as [Project Acoustics](https://aka.ms/acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="679f2-169">项目噪声可以为声音上的墙壁、门和其他场景几何的效果建模。</span><span class="sxs-lookup"><span data-stu-id="679f2-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="679f2-170">这是一个有效的选项，适用于在开发时了解相关场景几何图形的情况。</span><span class="sxs-lookup"><span data-stu-id="679f2-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="679f2-171">后续步骤</span><span class="sxs-lookup"><span data-stu-id="679f2-171">Next steps</span></span>
- [<span data-ttu-id="679f2-172">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="679f2-172">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
- [<span data-ttu-id="679f2-173">如何在混合现实应用程序中使用声音</span><span class="sxs-lookup"><span data-stu-id="679f2-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)
