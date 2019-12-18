---
title: Unity 中的空间音效
description: 从 Unity 场景内的特定3D 点播放空间声音。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity，空间音效，HRTF，房间大小
ms.openlocfilehash: 3e7d0ea231545d5112d182dffbc02f217ca4a4a7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181987"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="07af4-104">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="07af4-104">Spatial sound in Unity</span></span>

<span data-ttu-id="07af4-105">此页链接到 Unity 中的空间音效资源。</span><span class="sxs-lookup"><span data-stu-id="07af4-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="07af4-106">Spatializer 选项</span><span class="sxs-lookup"><span data-stu-id="07af4-106">Spatializer options</span></span>
<span data-ttu-id="07af4-107">混合现实应用程序的 Spatializer 选项包括：</span><span class="sxs-lookup"><span data-stu-id="07af4-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="07af4-108">*MS HRTF Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="07af4-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="07af4-109">Unity 将其作为*Windows Mixed Reality*可选包的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="07af4-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="07af4-110">这会在具有较高成本的 "单一源" 体系结构的 CPU 上运行。</span><span class="sxs-lookup"><span data-stu-id="07af4-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="07af4-111">这是为了向后兼容原 HoloLens 应用程序而提供的。</span><span class="sxs-lookup"><span data-stu-id="07af4-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="07af4-112">*Microsoft Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="07af4-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="07af4-113">可从[Microsoft Spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)获取此功能。</span><span class="sxs-lookup"><span data-stu-id="07af4-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="07af4-114">这将使用较低成本的 "多源" 体系结构。</span><span class="sxs-lookup"><span data-stu-id="07af4-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="07af4-115">在 HoloLens 2 上，这会被下放到硬件加速器。</span><span class="sxs-lookup"><span data-stu-id="07af4-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="07af4-116">对于新应用程序，我们建议*Microsoft Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="07af4-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="07af4-117">启用 spatialization</span><span class="sxs-lookup"><span data-stu-id="07af4-117">Enable spatialization</span></span>

<span data-ttu-id="07af4-118">使用[NuGet For unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)安装_SpatialAudio_ ，并在项目的音频设置中选择**microsoft Spatializer** 。</span><span class="sxs-lookup"><span data-stu-id="07af4-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="07af4-119">然后：</span><span class="sxs-lookup"><span data-stu-id="07af4-119">Then:</span></span>
* <span data-ttu-id="07af4-120">将**音频源**附加到层次结构中的对象</span><span class="sxs-lookup"><span data-stu-id="07af4-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="07af4-121">选中 "**启用 spatialization** " 复选框</span><span class="sxs-lookup"><span data-stu-id="07af4-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="07af4-122">将**空间混合**滑块移动到 "1"</span><span class="sxs-lookup"><span data-stu-id="07af4-122">Move the **Spatial Blend** slider to '1'</span></span>

<span data-ttu-id="07af4-123">有关更多详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="07af4-123">For more details, see:</span></span>
* [<span data-ttu-id="07af4-124">Microsoft spatializer GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="07af4-124">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="07af4-125">Microsoft 的 spatializer 教程</span><span class="sxs-lookup"><span data-stu-id="07af4-125">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="07af4-126">Unity 的音频源文档</span><span class="sxs-lookup"><span data-stu-id="07af4-126">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="07af4-127">Unity 的 spatializer 文档</span><span class="sxs-lookup"><span data-stu-id="07af4-127">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="07af4-128">基于距离的衰减</span><span class="sxs-lookup"><span data-stu-id="07af4-128">Distance-based attenuation</span></span>
<span data-ttu-id="07af4-129">Unity 的默认基于距离的衰减的最小距离为1米，最大距离为500米，对数 rolloff。</span><span class="sxs-lookup"><span data-stu-id="07af4-129">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="07af4-130">这些设置可能适用于你的方案，你可能会发现源衰减太快或太慢。</span><span class="sxs-lookup"><span data-stu-id="07af4-130">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="07af4-131">有关更多详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="07af4-131">For more details, see:</span></span>
* <span data-ttu-id="07af4-132">[混合现实中的声音设计](spatial-sound-design.md)建议的设置。</span><span class="sxs-lookup"><span data-stu-id="07af4-132">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="07af4-133">[Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)，了解有关如何设置这些曲线的说明。</span><span class="sxs-lookup"><span data-stu-id="07af4-133">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="07af4-134">混响</span><span class="sxs-lookup"><span data-stu-id="07af4-134">Reverb</span></span>
<span data-ttu-id="07af4-135">默认情况下， _Microsoft Spatializer_禁用了 Spatializer 效果。</span><span class="sxs-lookup"><span data-stu-id="07af4-135">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="07af4-136">若要为 spatialized 源启用回响和其他效果：</span><span class="sxs-lookup"><span data-stu-id="07af4-136">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="07af4-137">将 "**房间效果发送级别**" 组件附加到每个源</span><span class="sxs-lookup"><span data-stu-id="07af4-137">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="07af4-138">调整每个源的发送级别曲线，以控制发送回图形以进行效果处理的音频的增益</span><span class="sxs-lookup"><span data-stu-id="07af4-138">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="07af4-139">有关详细信息，请参阅[spatializer 教程的第5章](unity-spatial-audio-ch5.md)。</span><span class="sxs-lookup"><span data-stu-id="07af4-139">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="07af4-140">Unity 空间声音示例</span><span class="sxs-lookup"><span data-stu-id="07af4-140">Unity spatial sound examples</span></span>
<span data-ttu-id="07af4-141">有关 Unity 中空间音效的示例，请参阅：</span><span class="sxs-lookup"><span data-stu-id="07af4-141">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="07af4-142">MRTK 演示</span><span class="sxs-lookup"><span data-stu-id="07af4-142">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="07af4-143">[Microsoft Spatializer 示例项目](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="07af4-143">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="07af4-144">后续步骤</span><span class="sxs-lookup"><span data-stu-id="07af4-144">Next steps</span></span>
* [<span data-ttu-id="07af4-145">混合现实中的声音设计</span><span class="sxs-lookup"><span data-stu-id="07af4-145">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="07af4-146">Microsoft 的 spatializer 教程</span><span class="sxs-lookup"><span data-stu-id="07af4-146">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

