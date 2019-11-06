---
title: 混合现实中的音频
description: 混合现实中的音频可以提高用户 UI 交互的用户信心，并从而深入了解用户体验。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空间音效，环绕声，3d 音频，3d 声音，空间音频
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641109"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="1176b-104">混合现实中的音频</span><span class="sxs-lookup"><span data-stu-id="1176b-104">Audio in Mixed Reality</span></span>
<span data-ttu-id="1176b-105">音频是混合现实中设计和生产力的必不可少部分，可以：</span><span class="sxs-lookup"><span data-stu-id="1176b-105">Audio is an essential part of design and productivity in mixed reality, and can:</span></span>
* <span data-ttu-id="1176b-106">提高用户在手势和基于语音的交互中的置信度</span><span class="sxs-lookup"><span data-stu-id="1176b-106">Increase user confidence in gesture- and voice-based interactions</span></span>
* <span data-ttu-id="1176b-107">指导用户接下来的步骤</span><span class="sxs-lookup"><span data-stu-id="1176b-107">Guide users to next steps</span></span>
* <span data-ttu-id="1176b-108">有效地将虚拟对象与现实世界组合</span><span class="sxs-lookup"><span data-stu-id="1176b-108">Effectively combine virtual objects with the real world</span></span>

<span data-ttu-id="1176b-109">混合现实耳机的低延迟头跟踪（包括 HoloLens）允许使用高质量的基于 HRTF 的 spatialization。</span><span class="sxs-lookup"><span data-stu-id="1176b-109">The low-latency head tracking of mixed reality headsets, including HoloLens, enables the use of high quality HRTF-based spatialization.</span></span> <span data-ttu-id="1176b-110">应用程序中的 Spatializing 音频可以：</span><span class="sxs-lookup"><span data-stu-id="1176b-110">Spatializing audio in your application can:</span></span>
* <span data-ttu-id="1176b-111">注意视觉对象</span><span class="sxs-lookup"><span data-stu-id="1176b-111">Call attention to visual elements</span></span>
* <span data-ttu-id="1176b-112">帮助用户维护其真实环境的认知度</span><span class="sxs-lookup"><span data-stu-id="1176b-112">Help users maintain awareness of their real-world surroundings</span></span>

<span data-ttu-id="1176b-113">添加噪声更深入地连接到混合世界，并可提供有关环境和对象状态的提示。</span><span class="sxs-lookup"><span data-stu-id="1176b-113">Adding acoustics more deeply connects holograms to the mixed world, and can provide cues about the environment and object state.</span></span>

<span data-ttu-id="1176b-114">有关使用音频设计的更详细示例，请参阅[声音设计](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="1176b-114">For more detailed examples of design using audio, see [sound design](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="1176b-115">设备支持</span><span class="sxs-lookup"><span data-stu-id="1176b-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1176b-116"><strong>具有</strong></span><span class="sxs-lookup"><span data-stu-id="1176b-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1176b-117"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="1176b-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1176b-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1176b-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1176b-119"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="1176b-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1176b-120">Spatialization</span><span class="sxs-lookup"><span data-stu-id="1176b-120">Spatialization</span></span></td>
        <td><span data-ttu-id="1176b-121">✔️</span><span class="sxs-lookup"><span data-stu-id="1176b-121">✔️</span></span></td>
        <td><span data-ttu-id="1176b-122">✔️</span><span class="sxs-lookup"><span data-stu-id="1176b-122">✔️</span></span></td>
        <td><span data-ttu-id="1176b-123">✔️</span><span class="sxs-lookup"><span data-stu-id="1176b-123">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1176b-124">Spatialization 硬件加速</span><span class="sxs-lookup"><span data-stu-id="1176b-124">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="1176b-125">✔️</span><span class="sxs-lookup"><span data-stu-id="1176b-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a><span data-ttu-id="1176b-126">在混合现实中使用声音</span><span class="sxs-lookup"><span data-stu-id="1176b-126">Using sounds in mixed reality</span></span>
<span data-ttu-id="1176b-127">[在混合现实中使用声音](spatial-sound-design.md)可能需要不同于触摸和键盘和鼠标应用程序的方法。</span><span class="sxs-lookup"><span data-stu-id="1176b-127">[Using sounds in mixed reality](spatial-sound-design.md) can require a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="1176b-128">关键的设计决策包括哪些声音要 spatialize 以及哪些 sonify 交互。</span><span class="sxs-lookup"><span data-stu-id="1176b-128">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="1176b-129">这些决策可能会对用户置信度、工作效率和学习曲线产生很大影响。</span><span class="sxs-lookup"><span data-stu-id="1176b-129">These decisions can have a strong effect on user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="1176b-130">案例研究</span><span class="sxs-lookup"><span data-stu-id="1176b-130">Case studies</span></span>
<span data-ttu-id="1176b-131">HoloTour 几乎使用户能够在世界各地旅游和历史站点。</span><span class="sxs-lookup"><span data-stu-id="1176b-131">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="1176b-132">以下案例研究介绍了 HoloTour： HoloTour 的声音[设计](case-study-spatial-sound-design-for-holotour.md)。</span><span class="sxs-lookup"><span data-stu-id="1176b-132">The following case study describes the sound design for HoloTour: [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md).</span></span> <span data-ttu-id="1176b-133">使用特殊的麦克风和渲染设置来捕获使用者空间。</span><span class="sxs-lookup"><span data-stu-id="1176b-133">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="1176b-134">RoboRaid 是一种射击的高能耗。</span><span class="sxs-lookup"><span data-stu-id="1176b-134">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="1176b-135">以下案例研究介绍了用于确保空间音频最大效果的设计选择：[适用于 RoboRaid 的声音设计](case-study-using-spatial-sound-in-roboraid.md)。</span><span class="sxs-lookup"><span data-stu-id="1176b-135">The following case study describes the design choices made to ensure spatial audio was used to fullest dramatic effect: [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span></span>

## <a name="spatialization"></a><span data-ttu-id="1176b-136">Spatialization</span><span class="sxs-lookup"><span data-stu-id="1176b-136">Spatialization</span></span>
<span data-ttu-id="1176b-137">Spatialization 是空间音频的方向性组件。</span><span class="sxs-lookup"><span data-stu-id="1176b-137">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="1176b-138">使用7.1 家庭影院设置时，spatialization 非常简单，只是在高音扬声器之间进行平移。</span><span class="sxs-lookup"><span data-stu-id="1176b-138">When using a 7.1 home theater setup, spatialization is as simple as panning between loud speakers.</span></span> <span data-ttu-id="1176b-139">但对于混合现实中的耳机，使用基于 HRTF 的技术是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="1176b-139">But with headphones in mixed reality it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="1176b-140">Windows 提供基于 HRTF 的 spatialization，这种支持在 HoloLens 2 上是硬件加速的。</span><span class="sxs-lookup"><span data-stu-id="1176b-140">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="1176b-141">我应该 spatialize 吗？</span><span class="sxs-lookup"><span data-stu-id="1176b-141">Should I spatialize?</span></span>
<span data-ttu-id="1176b-142">混合现实应用程序中的许多声音都受益于 spatialization，这会从侦听器的头部发出声音，并将其放在世界各地。</span><span class="sxs-lookup"><span data-stu-id="1176b-142">Many sounds in mixed reality applications benefit from spatialization, which takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="1176b-143">有关在应用程序中最有效地使用 spatialization 的建议，请参阅[空间音效设计](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="1176b-143">Refer to [Spatial Sound Design](spatial-sound-design.md) for suggestions on the most effective uses of spatialization in your application.</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="1176b-144">Spatializer 个性化</span><span class="sxs-lookup"><span data-stu-id="1176b-144">Spatializer personalization</span></span>
<span data-ttu-id="1176b-145">HRTFs 跨频率范围控制耳之间的级别和阶段差异。</span><span class="sxs-lookup"><span data-stu-id="1176b-145">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="1176b-146">它们基于物理型号和人机头、torso 和 ear （pinnae）的度量。</span><span class="sxs-lookup"><span data-stu-id="1176b-146">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="1176b-147">我们的大脑对这些差异做出了响应，从而提高了声音方向的认知度。</span><span class="sxs-lookup"><span data-stu-id="1176b-147">Our brains respond to these differences to give rise to a perception of direction in sound.</span></span> 

<span data-ttu-id="1176b-148">每个人都有独特的耳形状、头大小和耳位置，因此最好的 HRTFs 是符合您的需要。</span><span class="sxs-lookup"><span data-stu-id="1176b-148">Every individual has a unique ear shape, head size, and ear position, so the best HRTFs are those that conform to you.</span></span> <span data-ttu-id="1176b-149">HoloLens 通过使用头戴显示在 spatialization 的距离（IPD）来调整头大小的 HRTFs。</span><span class="sxs-lookup"><span data-stu-id="1176b-149">HoloLens increases spatialization accuracy by using your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="1176b-150">Spatializer 平台支持</span><span class="sxs-lookup"><span data-stu-id="1176b-150">Spatializer platform support</span></span>
<span data-ttu-id="1176b-151">Windows 通过[ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 HRTFs。</span><span class="sxs-lookup"><span data-stu-id="1176b-151">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="1176b-152">此 API 向应用程序公开 HoloLens 2 HRTF 硬件加速。</span><span class="sxs-lookup"><span data-stu-id="1176b-152">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="1176b-153">Spatializer 中间件支持</span><span class="sxs-lookup"><span data-stu-id="1176b-153">Spatializer middleware support</span></span>
<span data-ttu-id="1176b-154">对于某些第三方音频引擎，支持 Windows HRTFs：</span><span class="sxs-lookup"><span data-stu-id="1176b-154">Support for Windows' HRTFs is available for some 3rd-party audio engines:</span></span>
* <span data-ttu-id="1176b-155">[Unity 音频引擎](spatial-sound-in-unity.md)插件调用 HRTF XAPO</span><span class="sxs-lookup"><span data-stu-id="1176b-155">A [Unity audio engine](spatial-sound-in-unity.md) plugin calls the HRTF XAPO</span></span>
* <span data-ttu-id="1176b-156">[Wwise 音频引擎插件](https://www.audiokinetic.com/products/plug-ins/msspatial/)调用 ISpatialAudioClient API</span><span class="sxs-lookup"><span data-stu-id="1176b-156">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/) calls the ISpatialAudioClient API</span></span>

## <a name="acoustics"></a><span data-ttu-id="1176b-157">噪声</span><span class="sxs-lookup"><span data-stu-id="1176b-157">Acoustics</span></span>
<span data-ttu-id="1176b-158">空间音频可能超出方向。</span><span class="sxs-lookup"><span data-stu-id="1176b-158">Spatial audio can be about more than direction.</span></span> <span data-ttu-id="1176b-159">其他维度，包括封闭、障碍物、回音、portalling 和源建模，统称为 "噪声"。</span><span class="sxs-lookup"><span data-stu-id="1176b-159">Other dimensions, including occlusion, obstruction, reverb, portalling, and source modelling, are collectively referred to as 'acoustics'.</span></span> <span data-ttu-id="1176b-160">如果没有噪声，spatialized 听起来就没有距离。</span><span class="sxs-lookup"><span data-stu-id="1176b-160">Without acoustics, spatialized sounds lack a perceived distance.</span></span>

<span data-ttu-id="1176b-161">噪声处理范围从简单到非常复杂。</span><span class="sxs-lookup"><span data-stu-id="1176b-161">Acoustics treatment can range from simple to very complex.</span></span> <span data-ttu-id="1176b-162">使用简单的回音，如任何音频引擎所支持的回音，你可以将 spatialized 的声音推送到侦听器周围的环境中。</span><span class="sxs-lookup"><span data-stu-id="1176b-162">By using a simple reverb, such as that supported by any audio engine, you can push spatialized sounds out into the environment surrounding the listener.</span></span> <span data-ttu-id="1176b-163">可以从噪声系统（如[项目噪声](https://aka.ms/acoustics)）获得更丰富且更具吸引力的噪声处理。</span><span class="sxs-lookup"><span data-stu-id="1176b-163">Richer and more compelling acoustics treatment is available from acoustics systems such as [Project Acoustics](https://aka.ms/acoustics).</span></span> <span data-ttu-id="1176b-164">项目噪声可以对墙壁、门和其他场景几何的效果进行建模，这是在开发时了解相关场景几何的情况的有效选项。</span><span class="sxs-lookup"><span data-stu-id="1176b-164">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound, and is an effective option for cases where the relevant scene geometry is known at development time.</span></span>

