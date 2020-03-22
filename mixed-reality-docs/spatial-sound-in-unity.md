---
title: Unity 中的空间音效
description: 从 Unity 场景内的特定3D 点播放空间声音。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity，空间音效，HRTF，房间大小
ms.openlocfilehash: af3f1486c3e931ad93d7b8960d822653ec740c12
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082044"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="fa298-104">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="fa298-104">Spatial sound in Unity</span></span>

<span data-ttu-id="fa298-105">此页链接到 Unity 中的空间音效资源。</span><span class="sxs-lookup"><span data-stu-id="fa298-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="fa298-106">Spatializer 选项</span><span class="sxs-lookup"><span data-stu-id="fa298-106">Spatializer options</span></span>
<span data-ttu-id="fa298-107">混合现实应用程序的 Spatializer 选项包括：</span><span class="sxs-lookup"><span data-stu-id="fa298-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="fa298-108">*MS HRTF Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="fa298-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="fa298-109">Unity 将其作为*Windows Mixed Reality*可选包的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="fa298-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="fa298-110">这会在具有较高成本的 "单一源" 体系结构的 CPU 上运行。</span><span class="sxs-lookup"><span data-stu-id="fa298-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="fa298-111">这是为了向后兼容原 HoloLens 应用程序而提供的。</span><span class="sxs-lookup"><span data-stu-id="fa298-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="fa298-112">*Microsoft Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="fa298-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="fa298-113">可从[Microsoft Spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)获取此功能。</span><span class="sxs-lookup"><span data-stu-id="fa298-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="fa298-114">这将使用较低成本的 "多源" 体系结构。</span><span class="sxs-lookup"><span data-stu-id="fa298-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="fa298-115">在 HoloLens 2 上，这会被下放到硬件加速器。</span><span class="sxs-lookup"><span data-stu-id="fa298-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="fa298-116">对于新应用程序，我们建议*Microsoft Spatializer*。</span><span class="sxs-lookup"><span data-stu-id="fa298-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="fa298-117">启用 spatialization</span><span class="sxs-lookup"><span data-stu-id="fa298-117">Enable spatialization</span></span>

<span data-ttu-id="fa298-118">使用[NuGet For unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)安装_SpatialAudio_ ，并在项目的音频设置中选择**microsoft Spatializer** 。</span><span class="sxs-lookup"><span data-stu-id="fa298-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="fa298-119">然后：</span><span class="sxs-lookup"><span data-stu-id="fa298-119">Then:</span></span>
* <span data-ttu-id="fa298-120">将**音频源**附加到层次结构中的对象</span><span class="sxs-lookup"><span data-stu-id="fa298-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="fa298-121">选中 "**启用 spatialization** " 复选框</span><span class="sxs-lookup"><span data-stu-id="fa298-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="fa298-122">将**空间混合**滑块移动到 "1"</span><span class="sxs-lookup"><span data-stu-id="fa298-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="fa298-123">确保已在开发人员工作站上启用空间音频。</span><span class="sxs-lookup"><span data-stu-id="fa298-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="fa298-124">右键单击任务栏上的 "音量" 图标，并确保 "空间" "声音" 设置为 "关闭"，以启用它。</span><span class="sxs-lookup"><span data-stu-id="fa298-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="fa298-125">若要获取有关在 HoloLens 2 上收到的内容的最佳表示，请选择 " **Windows Sonic" 作为耳机**。</span><span class="sxs-lookup"><span data-stu-id="fa298-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones**.</span></span>

>[!NOTE]
><span data-ttu-id="fa298-126">如果在 Unity 中由于缺少某个依赖项而无法加载 SpatialAudio，请检查你的电脑上是否已安装最新版本的[Microsoft Visual C++可再发行组件](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)。</span><span class="sxs-lookup"><span data-stu-id="fa298-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="fa298-127">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="fa298-127">For more details, see:</span></span>
* [<span data-ttu-id="fa298-128">Microsoft spatializer GitHub 存储库</span><span class="sxs-lookup"><span data-stu-id="fa298-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="fa298-129">Microsoft 的 spatializer 教程</span><span class="sxs-lookup"><span data-stu-id="fa298-129">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="fa298-130">Unity 的音频源文档</span><span class="sxs-lookup"><span data-stu-id="fa298-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="fa298-131">Unity 的 spatializer 文档</span><span class="sxs-lookup"><span data-stu-id="fa298-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="fa298-132">基于距离的衰减</span><span class="sxs-lookup"><span data-stu-id="fa298-132">Distance-based attenuation</span></span>
<span data-ttu-id="fa298-133">Unity 的默认基于距离的衰减的最小距离为1米，最大距离为500米，对数 rolloff。</span><span class="sxs-lookup"><span data-stu-id="fa298-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="fa298-134">这些设置可能适用于你的方案，你可能会发现源衰减太快或太慢。</span><span class="sxs-lookup"><span data-stu-id="fa298-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="fa298-135">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="fa298-135">For more details, see:</span></span>
* <span data-ttu-id="fa298-136">[混合现实中的声音设计](spatial-sound-design.md)建议的设置。</span><span class="sxs-lookup"><span data-stu-id="fa298-136">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="fa298-137">[Unity 的音频源文档](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)，了解有关如何设置这些曲线的说明。</span><span class="sxs-lookup"><span data-stu-id="fa298-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="fa298-138">混响</span><span class="sxs-lookup"><span data-stu-id="fa298-138">Reverb</span></span>
<span data-ttu-id="fa298-139">默认情况下， _Microsoft Spatializer_禁用了 Spatializer 效果。</span><span class="sxs-lookup"><span data-stu-id="fa298-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="fa298-140">若要为 spatialized 源启用回响和其他效果：</span><span class="sxs-lookup"><span data-stu-id="fa298-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="fa298-141">将 "**房间效果发送级别**" 组件附加到每个源</span><span class="sxs-lookup"><span data-stu-id="fa298-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="fa298-142">调整每个源的发送级别曲线，以控制发送回图形以进行效果处理的音频的增益</span><span class="sxs-lookup"><span data-stu-id="fa298-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="fa298-143">有关详细信息，请参阅[spatializer 教程的第5章](unity-spatial-audio-ch5.md)。</span><span class="sxs-lookup"><span data-stu-id="fa298-143">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="fa298-144">Unity 空间声音示例</span><span class="sxs-lookup"><span data-stu-id="fa298-144">Unity spatial sound examples</span></span>
<span data-ttu-id="fa298-145">有关 Unity 中空间音效的示例，请参阅：</span><span class="sxs-lookup"><span data-stu-id="fa298-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="fa298-146">MRTK 演示</span><span class="sxs-lookup"><span data-stu-id="fa298-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="fa298-147">[Microsoft Spatializer 示例项目](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="fa298-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="fa298-148">后续步骤</span><span class="sxs-lookup"><span data-stu-id="fa298-148">Next steps</span></span>
* [<span data-ttu-id="fa298-149">混合现实中的声音设计</span><span class="sxs-lookup"><span data-stu-id="fa298-149">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="fa298-150">Microsoft 的 spatializer 教程</span><span class="sxs-lookup"><span data-stu-id="fa298-150">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

