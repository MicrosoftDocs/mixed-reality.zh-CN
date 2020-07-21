---
title: 什么是混合现实？
description: 本文提供混合现实的定义，并说明简单的 AR 和 VR 设备，以及 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式头戴显示设备等 Windows Mixed Reality 设备在混合现实范畴中所处的位置。
author: brandonbray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: 混合现实, 全息, ar, vr, mr, xr, 增强现实, 虚拟现实, 说明
ms.localizationpriority: high
ms.openlocfilehash: 541752ef32149f64f9b85616883c284b33bb8fed
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447903"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="30224-104">什么是混合现实？</span><span class="sxs-lookup"><span data-stu-id="30224-104">What is mixed reality?</span></span>

![在 HoloLens 2 用手进行点选和提交](images/02_MixedRealitySlashMixedReality.png)

<span data-ttu-id="30224-106">混合现实是将物理世界与数字世界相混合的结果。</span><span class="sxs-lookup"><span data-stu-id="30224-106">Mixed reality is the result of blending the physical world with the digital world.</span></span> <span data-ttu-id="30224-107">混合现实是人类、计算机和环境交互方面的下一次演进，它解锁了此前受限于我们想象力的可能性。</span><span class="sxs-lookup"><span data-stu-id="30224-107">Mixed reality is the next evolution in human, computer, and environment interaction and unlocks possibilities that before now were restricted to our imaginations.</span></span> <span data-ttu-id="30224-108">它是随着计算机视觉、图形处理能力、显示技术和输入系统的进步应运而生的。</span><span class="sxs-lookup"><span data-stu-id="30224-108">It is made possible by advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="30224-109">“混合实现”一词最初由 Paul Milgram 和 Fumio Kishino 在其 1994 年发表的论文 [A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)（混合现实视频显示的分类法）中提到。 </span><span class="sxs-lookup"><span data-stu-id="30224-109">The term *mixed reality* was originally introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)."</span></span> <span data-ttu-id="30224-110">此论文介绍了“虚拟连续体”的概念，并重点说明了如何对显示内容应用类别分类法。 </span><span class="sxs-lookup"><span data-stu-id="30224-110">Their paper introduced the concept of the *virtuality continuum*, and focused on how the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="30224-111">从那此后，混合现实的应用已经超越了显示内容。</span><span class="sxs-lookup"><span data-stu-id="30224-111">Since then, the application of mixed reality goes beyond displays.</span></span> <span data-ttu-id="30224-112">现在它还涵盖环境输入、空间音效和定位。</span><span class="sxs-lookup"><span data-stu-id="30224-112">It also includes environmental input, spatial sound, and location.</span></span>

<span data-ttu-id="30224-113">![混合现实范围](images/mixedrealityspectrum-worlds.png)</span><span class="sxs-lookup"><span data-stu-id="30224-113">![The mixed reality spectrum](images/mixedrealityspectrum-worlds.png)</span></span><br>
<span data-ttu-id="30224-114">插图：  混合现实是将物理世界与数字世界相融合的结果。</span><span class="sxs-lookup"><span data-stu-id="30224-114">*Image: Mixed reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="30224-115">环境输入和感知</span><span class="sxs-lookup"><span data-stu-id="30224-115">Environmental input and perception</span></span>

<span data-ttu-id="30224-116">过去几十年来，人类输入与计算机输入之间的关系已得到充分的探讨。</span><span class="sxs-lookup"><span data-stu-id="30224-116">Over the past several decades, the relationship between human and computer input has been well explored.</span></span> <span data-ttu-id="30224-117">甚至还出现了一个拥有众多研究人员的学科，称作“人机交互”(HCI)。 </span><span class="sxs-lookup"><span data-stu-id="30224-117">It even has a widely studied discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="30224-118">人类输入是通过多种方式进行的，包括键盘、鼠标、触摸、笔迹、语音，甚至 Kinect 框架跟踪。</span><span class="sxs-lookup"><span data-stu-id="30224-118">Human input happens through a variety of means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="30224-119">传感器和处理技术的进步使计算机环境输入发展到了全新的高度。</span><span class="sxs-lookup"><span data-stu-id="30224-119">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="30224-120">计算机与环境之间的交互实际上是对环境的理解或认知。 </span><span class="sxs-lookup"><span data-stu-id="30224-120">The interaction between computers and environments is effectively environmental understanding or *perception*.</span></span> <span data-ttu-id="30224-121">因此，Windows 中显示环境信息的 API 称作[感知 API](https://docs.microsoft.com/uwp/api/Windows.Perception)。</span><span class="sxs-lookup"><span data-stu-id="30224-121">Hence the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="30224-122">环境输入捕获如下所述的信息：用户在世界上的位置（例如[头部跟踪](coordinate-systems.md)）、表面和边界（例如[空间映射](spatial-mapping.md)和[场景理解](scene-understanding.md)）、环境照明、环境音效、对象识别和定位。</span><span class="sxs-lookup"><span data-stu-id="30224-122">Environmental input captures things like a person's position in the world (e.g. [head tracking](coordinate-systems.md)), surfaces and boundaries (e.g. [spatial mapping](spatial-mapping.md) and [scene understanding](scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>

<span data-ttu-id="30224-123">![显示计算机、人类与环境之间的交互的文氏图](images/mixed-reality-venn-diagram-300px.png)</span><span class="sxs-lookup"><span data-stu-id="30224-123">![Venn diagram showing interactions between computers, humans and environments](images/mixed-reality-venn-diagram-300px.png)</span></span><br><span data-ttu-id="30224-124"> \
*插图\：* 计算机、人类与环境之间的交互。</span><span class="sxs-lookup"><span data-stu-id="30224-124"> \
*Image: The interactions between between computers, humans and environments.*</span></span>

<br>

<span data-ttu-id="30224-125">现在，**计算机处理、人类输入和环境输入**这三者的组合为创建真正的混合现实体验创造了机会。</span><span class="sxs-lookup"><span data-stu-id="30224-125">Now, the combination of all three--**computer processing, human input, and environmental input**--sets the opportunity to create true mixed reality experiences.</span></span> <span data-ttu-id="30224-126">物理世界中的运动可以转换为数字世界中的运动。</span><span class="sxs-lookup"><span data-stu-id="30224-126">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="30224-127">物理世界中的边界可以影响数字世界中的应用体验，例如玩游戏。</span><span class="sxs-lookup"><span data-stu-id="30224-127">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="30224-128">如果没有环境输入，体验就无法在物理现实与数字现实之间进行融合。</span><span class="sxs-lookup"><span data-stu-id="30224-128">Without environmental input, experiences cannot blend between physical and digital realities.</span></span><br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="30224-129">混合现实范围</span><span class="sxs-lookup"><span data-stu-id="30224-129">The mixed reality spectrum</span></span>

<span data-ttu-id="30224-130">由于混合现实融合了物理世界和数字世界，这两种现实定义了称作“虚拟连续体”的范围的两个极端。</span><span class="sxs-lookup"><span data-stu-id="30224-130">Since mixed reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="30224-131">为方便起见，我们将此范围称作“混合现实范围”。 </span><span class="sxs-lookup"><span data-stu-id="30224-131">For simplicity, we refer to this as the *mixed reality spectrum*.</span></span> <span data-ttu-id="30224-132">左侧是物理现实，是人类所在的环境；右侧是对应的数字现实。</span><span class="sxs-lookup"><span data-stu-id="30224-132">On the left-hand side we have physical reality in which we, humans, exist; on the right-hand side we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="30224-133">增强现实与虚拟现实</span><span class="sxs-lookup"><span data-stu-id="30224-133">Augmented vs. virtual reality</span></span>

<span data-ttu-id="30224-134">目前市场上的大多数手机几乎都不具备环境理解功能。</span><span class="sxs-lookup"><span data-stu-id="30224-134">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="30224-135">因此，它们提供的体验无法在物理现实与数字现实之间进行混合。</span><span class="sxs-lookup"><span data-stu-id="30224-135">Thus the experiences they offer cannot mix between physical and digital realities.</span></span> <span data-ttu-id="30224-136">在物理世界的视频流中叠加图形的体验是“增强现实”。 </span><span class="sxs-lookup"><span data-stu-id="30224-136">The experiences that overlay graphics on video streams of the physical world are *augmented reality*.</span></span> <span data-ttu-id="30224-137">遮挡视图以呈现数字体验的体验是“虚拟现实”。 </span><span class="sxs-lookup"><span data-stu-id="30224-137">The experiences that occlude your view to present a digital experience are *virtual reality*.</span></span> <span data-ttu-id="30224-138">可以看到，在这两个极端之间实现的体验是“混合现实”： </span><span class="sxs-lookup"><span data-stu-id="30224-138">As you can see, the experiences enabled between these two extremes is *mixed reality*:</span></span>
* <span data-ttu-id="30224-139">从物理世界开始，我们可以放置一个数字对象（例如全息影像），就如同它确实在那里一样。</span><span class="sxs-lookup"><span data-stu-id="30224-139">Starting with the physical world, placing a digital object, such as a hologram, as if it was really there.</span></span>
* <span data-ttu-id="30224-140">从物理世界开始，另一人（头像）的数字表示形式会显示他（她）在留下便条时所处的位置。</span><span class="sxs-lookup"><span data-stu-id="30224-140">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="30224-141">换而言之，这种体验代表不同时间点的异步协作。</span><span class="sxs-lookup"><span data-stu-id="30224-141">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="30224-142">从数字世界开始，物理世界中的物理边界（例如墙壁和家具）在体验中以数字形式显示，以帮助用户避开物理对象。</span><span class="sxs-lookup"><span data-stu-id="30224-142">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>


<br>

<span data-ttu-id="30224-143">![混合现实范围](images/mixedrealityspectrum.png)</span><span class="sxs-lookup"><span data-stu-id="30224-143">![The mixed reality spectrum](images/mixedrealityspectrum.png)</span></span><br>
<span data-ttu-id="30224-144">插图：  混合现实范围</span><span class="sxs-lookup"><span data-stu-id="30224-144">*Image: The mixed reality spectrum*</span></span>

<br>

<span data-ttu-id="30224-145">当今的大部分增强现实和虚拟现实产品/服务仅代表了此范围的极小一部分。</span><span class="sxs-lookup"><span data-stu-id="30224-145">Most augmented reality and virtual reality offerings available today represent a very small part of this spectrum.</span></span> <span data-ttu-id="30224-146">但是，它们是较大混合现实范围的子集。</span><span class="sxs-lookup"><span data-stu-id="30224-146">They are, however, subsets of the larger mixed reality spectrum.</span></span> <span data-ttu-id="30224-147">Windows 10 的开发考虑到了整个范围，可以融合现实世界中人员、地点和物品的数字表示形式。</span><span class="sxs-lookup"><span data-stu-id="30224-147">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>




## <a name="devices-and-experiences"></a><span data-ttu-id="30224-148">设备和体验</span><span class="sxs-lookup"><span data-stu-id="30224-148">Devices and experiences</span></span>


<span data-ttu-id="30224-149">有两种主要类型的设备可以提供 Windows Mixed Reality 体验：</span><span class="sxs-lookup"><span data-stu-id="30224-149">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="30224-150">**全息设备。**</span><span class="sxs-lookup"><span data-stu-id="30224-150">**Holographic devices.**</span></span> <span data-ttu-id="30224-151">这些设备的特征是能够将数字内容放入真实世界，就像是这些内容确实在那里。</span><span class="sxs-lookup"><span data-stu-id="30224-151">These are characterized by the device's ability to place digital content in the real world as if it were really there.</span></span>
2. <span data-ttu-id="30224-152">**沉浸式设备。**</span><span class="sxs-lookup"><span data-stu-id="30224-152">**Immersive devices.**</span></span> <span data-ttu-id="30224-153">这些设备的特征是能够创建“存在感”-- 隐藏物理世界，将其替换为数字体验。</span><span class="sxs-lookup"><span data-stu-id="30224-153">These are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="30%"> <span data-ttu-id="30224-154">特征</span><span class="sxs-lookup"><span data-stu-id="30224-154">Characteristic</span></span></th><th width="35%"> <span data-ttu-id="30224-155">全息设备</span><span class="sxs-lookup"><span data-stu-id="30224-155">Holographic devices</span></span></th><th width="35%"> <span data-ttu-id="30224-156">沉浸式设备</span><span class="sxs-lookup"><span data-stu-id="30224-156">Immersive devices</span></span></th>
</tr><tr>
<td><span data-ttu-id="30224-157"><strong>示例设备</strong></span><span class="sxs-lookup"><span data-stu-id="30224-157"><strong>Example device</strong></span></span></td><td> <span data-ttu-id="30224-158">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="30224-158">Microsoft HoloLens</span></span><br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> <span data-ttu-id="30224-159">Samsung HMD Odyssey+</span><span class="sxs-lookup"><span data-stu-id="30224-159">Samsung HMD Odyssey+</span></span><br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><span data-ttu-id="30224-160"><strong>显示器</strong></span><span class="sxs-lookup"><span data-stu-id="30224-160"><strong>Display</strong></span></span></td><td> <span data-ttu-id="30224-161">看透显示内容。</span><span class="sxs-lookup"><span data-stu-id="30224-161">See-through display.</span></span> <span data-ttu-id="30224-162">可让用户在戴上头戴显示设备时观看物理环境。</span><span class="sxs-lookup"><span data-stu-id="30224-162">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="30224-163">不透明显示。</span><span class="sxs-lookup"><span data-stu-id="30224-163">Opaque display.</span></span> <span data-ttu-id="30224-164">在戴上头戴显示设备时阻挡物理环境。</span><span class="sxs-lookup"><span data-stu-id="30224-164">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td><span data-ttu-id="30224-165"><strong>运动</strong></span><span class="sxs-lookup"><span data-stu-id="30224-165"><strong>Movement</strong></span></span></td><td> <span data-ttu-id="30224-166">六度自由全方位运动，支持旋转和平移。</span><span class="sxs-lookup"><span data-stu-id="30224-166">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="30224-167">六度自由全方位运动，支持旋转和平移。</span><span class="sxs-lookup"><span data-stu-id="30224-167">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table>



<span data-ttu-id="30224-168">请注意，设备是与单独的电脑保持连接或拴定状态（通过 USB 数据线或 Wi-Fi）还是保持独立状态（断开连接），并不能反映设备是全息设备还是沉浸式设备。</span><span class="sxs-lookup"><span data-stu-id="30224-168">Note, whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) does not reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="30224-169">可改善运动性的功能肯定会改善体验，而全息设备和沉浸式设备都可以保持连接或断开连接状态。</span><span class="sxs-lookup"><span data-stu-id="30224-169">Certainly, features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>


<span data-ttu-id="30224-170">技术的进步是实现混合现实体验的基础。</span><span class="sxs-lookup"><span data-stu-id="30224-170">Technological advancement is what has enabled mixed reality experiences.</span></span> <span data-ttu-id="30224-171">当今没有任何设备可以运行整个范围内的体验。</span><span class="sxs-lookup"><span data-stu-id="30224-171">There are no devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="30224-172">但是，Windows 10 为设备制造商和开发人员提供了一个通用的混合现实平台。</span><span class="sxs-lookup"><span data-stu-id="30224-172">However, Windows 10 provides a common mixed reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="30224-173">当今的设备可以支持混合现实范围内的某个特定部分。</span><span class="sxs-lookup"><span data-stu-id="30224-173">Devices today can support a specific range within the mixed reality spectrum.</span></span> <span data-ttu-id="30224-174">随着时间的推移，新设备会扩展该部分。</span><span class="sxs-lookup"><span data-stu-id="30224-174">Over time, new devices will expand that range.</span></span> <span data-ttu-id="30224-175">未来，全息设备将变得更有沉浸感，而沉浸式设备也将变得更有全息感。</span><span class="sxs-lookup"><span data-stu-id="30224-175">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

<br>

<span data-ttu-id="30224-176">![混合现实范围内的设备类型](images/Final_WhatIsMixedReality07.png)</span><span class="sxs-lookup"><span data-stu-id="30224-176">![Device types in the mixed reality spectrum](images/Final_WhatIsMixedReality07.png)</span></span><br>
<span data-ttu-id="30224-177">插图：  设备在混合现实范围内所处的位置</span><span class="sxs-lookup"><span data-stu-id="30224-177">*Image: Where devices exist on the mixed reality spectrum*</span></span>

<span data-ttu-id="30224-178">通常，最好是考虑应用程序或游戏开发人员想要创建的体验类型。</span><span class="sxs-lookup"><span data-stu-id="30224-178">Often, it is best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="30224-179">体验往往面向混合现实范围内的特定点或部分。</span><span class="sxs-lookup"><span data-stu-id="30224-179">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="30224-180">然后，开发人员应考虑所要面向的设备功能。</span><span class="sxs-lookup"><span data-stu-id="30224-180">Then, developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="30224-181">例如，依赖于物理世界的体验最好是在 HoloLens 上运行。</span><span class="sxs-lookup"><span data-stu-id="30224-181">For example, experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="30224-182">**向左（接近物理现实）。**</span><span class="sxs-lookup"><span data-stu-id="30224-182">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="30224-183">用户保留在其物理环境中，永远不相信他们已离开该环境。</span><span class="sxs-lookup"><span data-stu-id="30224-183">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="30224-184">**中间（完全混合现实）。**</span><span class="sxs-lookup"><span data-stu-id="30224-184">**In the middle (fully mixed reality).**</span></span> <span data-ttu-id="30224-185">这些体验融合了真实世界和数字世界。</span><span class="sxs-lookup"><span data-stu-id="30224-185">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="30224-186">电影[勇敢者的游戏](https://en.wikipedia.org/wiki/Jumanji)的观众能够适应故事发生地的房子与丛林环境融合后的物理结构。</span><span class="sxs-lookup"><span data-stu-id="30224-186">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="30224-187">**向右（接近数字现实）。**</span><span class="sxs-lookup"><span data-stu-id="30224-187">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="30224-188">用户将完全体验到一个数字环境，并且不会意识到其周围物理环境中发生的情况。</span><span class="sxs-lookup"><span data-stu-id="30224-188">Users experience a completely digital environment, and are unaware of what occurs in the physical environment around them.</span></span>


## <a name="see-also"></a><span data-ttu-id="30224-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30224-189">See also</span></span>

* [<span data-ttu-id="30224-190">什么是全息图？</span><span class="sxs-lookup"><span data-stu-id="30224-190">What is a hologram?</span></span>](hologram.md)
* [<span data-ttu-id="30224-191">了解混合现实的基础知识</span><span class="sxs-lookup"><span data-stu-id="30224-191">Understand the basics of mixed reality</span></span>](get-started-with-mr.md#understand-the-basics)
* [<span data-ttu-id="30224-192">开始创建和制作原型</span><span class="sxs-lookup"><span data-stu-id="30224-192">Start creating and prototyping</span></span>](design.md)
* [<span data-ttu-id="30224-193">了解工具和体系结构</span><span class="sxs-lookup"><span data-stu-id="30224-193">Learn the tools and architecture</span></span>](development.md)

