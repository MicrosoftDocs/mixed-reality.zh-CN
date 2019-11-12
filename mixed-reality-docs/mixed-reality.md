---
title: 什么是混合现实？
description: 本文定义了混合现实，并展示了简单的 AR 和 VR 设备以及 Windows Mixed Reality 设备（如 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式耳机）在混合现实范围内的位置。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality，全息，ar，vr，先生，xr，扩充现实，虚拟现实，说明
ms.openlocfilehash: 601e42c03e827f0f531f9dcf937a0dd34b008dc3
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926776"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="d4310-104">什么是混合现实？</span><span class="sxs-lookup"><span data-stu-id="d4310-104">What is mixed reality?</span></span>

<span data-ttu-id="d4310-105">混合现实是将物理世界与数字世界相混合的结果。</span><span class="sxs-lookup"><span data-stu-id="d4310-105">Mixed reality is the result of blending the physical world with the digital world.</span></span> <span data-ttu-id="d4310-106">混合现实是人类、计算机和环境交互方面的下一次演进，它解锁了此前受限于我们想象力的可能性。</span><span class="sxs-lookup"><span data-stu-id="d4310-106">Mixed reality is the next evolution in human, computer, and environment interaction and unlocks possibilities that before now were restricted to our imaginations.</span></span> <span data-ttu-id="d4310-107">这是通过计算机视觉、图形处理能力、显示技术和输入系统的进步来实现的。</span><span class="sxs-lookup"><span data-stu-id="d4310-107">It is made possible by advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="d4310-108">术语*混合现实*1994 最初是通过 Paul Milgram 和 Fumio Kishino，"[一种混合现实视觉对象的分类](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)。"</span><span class="sxs-lookup"><span data-stu-id="d4310-108">The term *mixed reality* was originally introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)."</span></span> <span data-ttu-id="d4310-109">他们的白皮书介绍了*virtuality*的一种概念，重点介绍如何应用分类分类。</span><span class="sxs-lookup"><span data-stu-id="d4310-109">Their paper introduced the concept of the *virtuality continuum*, and focused on how the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="d4310-110">此后，混合现实的应用程序会超出显示范围。</span><span class="sxs-lookup"><span data-stu-id="d4310-110">Since then, the application of mixed reality goes beyond displays.</span></span> <span data-ttu-id="d4310-111">它还包括环境输入、空间音质和位置。</span><span class="sxs-lookup"><span data-stu-id="d4310-111">It also includes environmental input, spatial sound, and location.</span></span>

<span data-ttu-id="d4310-112">![混合现实频谱](images/MixedRealitySpectrum-worlds.jpg)</span><span class="sxs-lookup"><span data-stu-id="d4310-112">![The mixed reality spectrum](images/MixedRealitySpectrum-worlds.jpg)</span></span><br>
<span data-ttu-id="d4310-113">*混合现实是将物理世界与数字世界混合的结果。*</span><span class="sxs-lookup"><span data-stu-id="d4310-113">*Mixed reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="d4310-114">环境输入和感知</span><span class="sxs-lookup"><span data-stu-id="d4310-114">Environmental input and perception</span></span>

<span data-ttu-id="d4310-115">过去几十年来，人们和计算机输入之间的关系已经过充分的探讨。</span><span class="sxs-lookup"><span data-stu-id="d4310-115">Over the past several decades, the relationship between human and computer input has been well explored.</span></span> <span data-ttu-id="d4310-116">甚至还具有一种称为人员*计算机交互*或 HCI 的广泛研究的原则。</span><span class="sxs-lookup"><span data-stu-id="d4310-116">It even has a widely studied discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="d4310-117">人工输入是通过多种方式进行的，包括键盘、鼠标、触摸、墨迹、语音，甚至 Kinect 框架跟踪。</span><span class="sxs-lookup"><span data-stu-id="d4310-117">Human input happens through a variety of means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="d4310-118">传感器和处理方面的进步是从环境到新的计算机输入领域。</span><span class="sxs-lookup"><span data-stu-id="d4310-118">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="d4310-119">计算机和环境之间的交互实际上是环境理解或*认知*。</span><span class="sxs-lookup"><span data-stu-id="d4310-119">The interaction between computers and environments is effectively environmental understanding or *perception*.</span></span> <span data-ttu-id="d4310-120">因此，Windows 中显示环境信息的 API 名称称为 "[感知 api](https://docs.microsoft.com/uwp/api/Windows.Perception)"。</span><span class="sxs-lookup"><span data-stu-id="d4310-120">Hence the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="d4310-121">环境输入会捕获用户在世界上的位置（例如，[打印头跟踪](coordinate-systems.md)）、表面和边界（例如，[空间映射](spatial-mapping.md)和[场景理解](scene-understanding.md)）、环境照明、环境声音、对象识别和位置。</span><span class="sxs-lookup"><span data-stu-id="d4310-121">Environmental input captures things like a person's position in the world (e.g. [head tracking](coordinate-systems.md)), surfaces and boundaries (e.g. [spatial mapping](spatial-mapping.md) and [scene understanding](scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>



:::row:::
    :::column:::
        <span data-ttu-id="d4310-122">现在，所有三个--**计算机处理、人工输入和环境输入**的组合都可用于创建真正的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="d4310-122">Now, the combination of all three--**computer processing, human input, and environmental input**--sets the opportunity to create true mixed reality experiences.</span></span> <span data-ttu-id="d4310-123">在现实世界中的移动可以转换为数字世界中的运动。</span><span class="sxs-lookup"><span data-stu-id="d4310-123">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="d4310-124">现实世界中的边界可能会影响数字世界中的应用程序体验，例如游戏播放。</span><span class="sxs-lookup"><span data-stu-id="d4310-124">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="d4310-125">如果没有环境输入，体验就不能在物理和数字现实之间融合。</span><span class="sxs-lookup"><span data-stu-id="d4310-125">Without environmental input, experiences cannot blend between physical and digital realities.</span></span><br>
        <br>
        <span data-ttu-id="d4310-126">*Image：计算机、人类和环境之间的交互。*</span><span class="sxs-lookup"><span data-stu-id="d4310-126">*Image: The interactions between between computers, humans and environments.*</span></span>
    :::column-end:::
        :::column:::
       ![显示计算机、人类和环境之间的交互的维恩图](images/mixed-reality-venn-diagram-300px.png)<br> 
    :::column-end:::
:::row-end:::

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="d4310-128">混合现实范围</span><span class="sxs-lookup"><span data-stu-id="d4310-128">The mixed reality spectrum</span></span>

<span data-ttu-id="d4310-129">因为混合现实混合了物理和数字世界，所以这两个现实定义了一种称为 virtuality continuum 的极有极端的端。</span><span class="sxs-lookup"><span data-stu-id="d4310-129">Since mixed reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="d4310-130">为简单起见，我们将此视为*混合现实频谱*。</span><span class="sxs-lookup"><span data-stu-id="d4310-130">For simplicity, we refer to this as the *mixed reality spectrum*.</span></span> <span data-ttu-id="d4310-131">在左侧，我们的现实生活中存在;在右侧，我们有相应的数码现实。</span><span class="sxs-lookup"><span data-stu-id="d4310-131">On the left-hand side we have physical reality in which we, humans, exist; on the right-hand side we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="d4310-132">扩充与虚拟现实</span><span class="sxs-lookup"><span data-stu-id="d4310-132">Augmented vs. virtual reality</span></span>

<span data-ttu-id="d4310-133">目前市场上的大多数移动电话几乎没有环境理解功能。</span><span class="sxs-lookup"><span data-stu-id="d4310-133">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="d4310-134">因此，它们所提供的体验不能在物理和数字现实之间混合使用。</span><span class="sxs-lookup"><span data-stu-id="d4310-134">Thus the experiences they offer cannot mix between physical and digital realities.</span></span> <span data-ttu-id="d4310-135">在物理世界的视频流上覆盖图形的*经验得以增加。*</span><span class="sxs-lookup"><span data-stu-id="d4310-135">The experiences that overlay graphics on video streams of the physical world are *augmented reality*.</span></span> <span data-ttu-id="d4310-136">遮蔽你的视图呈现数字体验的体验是*虚拟现实*。</span><span class="sxs-lookup"><span data-stu-id="d4310-136">The experiences that occlude your view to present a digital experience are *virtual reality*.</span></span> <span data-ttu-id="d4310-137">正如您所看到的，在这两种极端情况下启用的体验是*混合的现实*：</span><span class="sxs-lookup"><span data-stu-id="d4310-137">As you can see, the experiences enabled between these two extremes is *mixed reality*:</span></span>
* <span data-ttu-id="d4310-138">从物理世界开始，放入数字对象（如全息图），就像它确实如此。</span><span class="sxs-lookup"><span data-stu-id="d4310-138">Starting with the physical world, placing a digital object, such as a hologram, as if it was really there.</span></span>
* <span data-ttu-id="d4310-139">从身体开始，另一个用户（即头像）的数字表示形式，显示离开笔记时的位置。</span><span class="sxs-lookup"><span data-stu-id="d4310-139">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="d4310-140">换句话说，在不同时间点表示异步协作的经验。</span><span class="sxs-lookup"><span data-stu-id="d4310-140">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="d4310-141">从数字世界开始，来自实物世界的物理边界（如墙壁和家具）在体验中以数字形式显示，以帮助用户避免物理对象。</span><span class="sxs-lookup"><span data-stu-id="d4310-141">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>


<br>

<span data-ttu-id="d4310-142">![混合现实频谱](images/MixedRealitySpectrum.jpg)</span><span class="sxs-lookup"><span data-stu-id="d4310-142">![The mixed reality spectrum](images/MixedRealitySpectrum.jpg)</span></span><br>
<span data-ttu-id="d4310-143">*混合现实范围*</span><span class="sxs-lookup"><span data-stu-id="d4310-143">*The mixed reality spectrum*</span></span>

<br>

<span data-ttu-id="d4310-144">目前提供的大多数增加的现实和虚拟现实产品都代表了这种色谱的一小部分。</span><span class="sxs-lookup"><span data-stu-id="d4310-144">Most augmented reality and virtual reality offerings available today represent a very small part of this spectrum.</span></span> <span data-ttu-id="d4310-145">但它们是较大混合现实范围的子集。</span><span class="sxs-lookup"><span data-stu-id="d4310-145">They are, however, subsets of the larger mixed reality spectrum.</span></span> <span data-ttu-id="d4310-146">Windows 10 在构建时考虑了整个频谱，并允许在现实世界中混合人员、地点和物品的数字表示形式。</span><span class="sxs-lookup"><span data-stu-id="d4310-146">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>




## <a name="devices-and-experiences"></a><span data-ttu-id="d4310-147">设备和体验</span><span class="sxs-lookup"><span data-stu-id="d4310-147">Devices and experiences</span></span>


<span data-ttu-id="d4310-148">有两种主要类型的设备可提供 Windows Mixed Reality 体验：</span><span class="sxs-lookup"><span data-stu-id="d4310-148">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="d4310-149">**全息设备。**</span><span class="sxs-lookup"><span data-stu-id="d4310-149">**Holographic devices.**</span></span> <span data-ttu-id="d4310-150">这些特征的特征在于设备能够将数字内容置于真实世界中，就像确实如此。</span><span class="sxs-lookup"><span data-stu-id="d4310-150">These are characterized by the device's ability to place digital content in the real world as if it were really there.</span></span>
2. <span data-ttu-id="d4310-151">**沉浸式设备。**</span><span class="sxs-lookup"><span data-stu-id="d4310-151">**Immersive devices.**</span></span> <span data-ttu-id="d4310-152">这些特征的特征是设备能够创建 "状态"--隐藏物理世界，并将其替换为数字体验。</span><span class="sxs-lookup"><span data-stu-id="d4310-152">These are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="20%"> <span data-ttu-id="d4310-153">特征</span><span class="sxs-lookup"><span data-stu-id="d4310-153">Characteristic</span></span></th><th width="40%"> <span data-ttu-id="d4310-154">全息设备</span><span class="sxs-lookup"><span data-stu-id="d4310-154">Holographic Devices</span></span></th><th width="40%"> <span data-ttu-id="d4310-155">沉浸式设备</span><span class="sxs-lookup"><span data-stu-id="d4310-155">Immersive Devices</span></span></th>
</tr><tr>
<td> <span data-ttu-id="d4310-156">示例设备</span><span class="sxs-lookup"><span data-stu-id="d4310-156">Example Device</span></span></td><td> <span data-ttu-id="d4310-157">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="d4310-157">Microsoft HoloLens</span></span><br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> <span data-ttu-id="d4310-158">Acer Windows Mixed Reality 开发版</span><span class="sxs-lookup"><span data-stu-id="d4310-158">Acer Windows Mixed Reality Development Edition</span></span><br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> <span data-ttu-id="d4310-159">“显示”</span><span class="sxs-lookup"><span data-stu-id="d4310-159">Display</span></span></td><td> <span data-ttu-id="d4310-160"><i>查看-通过显示。</i></span><span class="sxs-lookup"><span data-stu-id="d4310-160"><i>See-through display.</i></span></span> <span data-ttu-id="d4310-161">允许用户在戴上耳机时查看物理环境。</span><span class="sxs-lookup"><span data-stu-id="d4310-161">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="d4310-162"><i>不透明显示。</i></span><span class="sxs-lookup"><span data-stu-id="d4310-162"><i>Opaque display.</i></span></span> <span data-ttu-id="d4310-163">在戴上耳机时阻塞物理环境。</span><span class="sxs-lookup"><span data-stu-id="d4310-163">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d4310-164">搬家</span><span class="sxs-lookup"><span data-stu-id="d4310-164">Movement</span></span></td><td> <span data-ttu-id="d4310-165">旋转和平移都具有全部六个自由度。</span><span class="sxs-lookup"><span data-stu-id="d4310-165">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="d4310-166">旋转和平移都具有全部六个自由度。</span><span class="sxs-lookup"><span data-stu-id="d4310-166">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table>

<span data-ttu-id="d4310-167">请注意，设备是连接到单独的 PC 还是受限（通过 USB 电缆或 Wi-fi）或自包含设备（untethered），并不反映设备是全息设备还是沉浸式设备。</span><span class="sxs-lookup"><span data-stu-id="d4310-167">Note, whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) does not reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="d4310-168">当然，改进移动性的功能会导致更好的体验，而全息和沉浸式设备可能是受限或 untethered。</span><span class="sxs-lookup"><span data-stu-id="d4310-168">Certainly, features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>


<span data-ttu-id="d4310-169">技术进步已经实现了混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="d4310-169">Technological advancement is what has enabled mixed reality experiences.</span></span> <span data-ttu-id="d4310-170">目前没有可在整个范围内运行体验的设备。</span><span class="sxs-lookup"><span data-stu-id="d4310-170">There are no devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="d4310-171">但是，Windows 10 为设备制造商和开发人员提供了共同的混合现实平台。</span><span class="sxs-lookup"><span data-stu-id="d4310-171">However, Windows 10 provides a common mixed reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="d4310-172">目前的设备可以支持混合现实范围内的特定范围。</span><span class="sxs-lookup"><span data-stu-id="d4310-172">Devices today can support a specific range within the mixed reality spectrum.</span></span> <span data-ttu-id="d4310-173">随着时间的推移，新设备将扩展此范围。</span><span class="sxs-lookup"><span data-stu-id="d4310-173">Over time, new devices will expand that range.</span></span> <span data-ttu-id="d4310-174">未来，全息设备将变得更加引人入胜，沉浸式设备将会变得更全息。</span><span class="sxs-lookup"><span data-stu-id="d4310-174">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

<br>

<span data-ttu-id="d4310-175">混合现实频谱中的 ![设备类型](images/MixedRealitySpectrum-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="d4310-175">![Device types in the mixed reality spectrum](images/MixedRealitySpectrum-devices.jpg)</span></span><br>
<span data-ttu-id="d4310-176">*混合现实范围内的设备*</span><span class="sxs-lookup"><span data-stu-id="d4310-176">*Where devices exist on the mixed reality spectrum*</span></span>

<span data-ttu-id="d4310-177">通常，最好考虑应用程序或游戏开发人员要创建的体验类型。</span><span class="sxs-lookup"><span data-stu-id="d4310-177">Often, it is best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="d4310-178">这些体验通常面向特定的点或部分。</span><span class="sxs-lookup"><span data-stu-id="d4310-178">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="d4310-179">然后，开发人员应考虑要面向的设备的功能。</span><span class="sxs-lookup"><span data-stu-id="d4310-179">Then, developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="d4310-180">例如，依赖于现实世界的体验将在 HoloLens 上运行最佳。</span><span class="sxs-lookup"><span data-stu-id="d4310-180">For example, experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="d4310-181">**向左（接近物理事实）。**</span><span class="sxs-lookup"><span data-stu-id="d4310-181">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="d4310-182">用户仍在其物理环境中存在，永远不会相信他们已离开该环境。</span><span class="sxs-lookup"><span data-stu-id="d4310-182">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="d4310-183">**中间（完全混合现实）。**</span><span class="sxs-lookup"><span data-stu-id="d4310-183">**In the middle (fully mixed reality).**</span></span> <span data-ttu-id="d4310-184">这些经验融合了真实世界和数字世界。</span><span class="sxs-lookup"><span data-stu-id="d4310-184">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="d4310-185">观看了电影[Jumanji](https://en.wikipedia.org/wiki/Jumanji)的观看者可以协调出故事发生的物理结构与蛙鸣环境的混合方式。</span><span class="sxs-lookup"><span data-stu-id="d4310-185">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="d4310-186">**向右（接近数字事实）。**</span><span class="sxs-lookup"><span data-stu-id="d4310-186">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="d4310-187">用户体验到完全数字环境，并不知道其周围的物理环境发生了什么情况。</span><span class="sxs-lookup"><span data-stu-id="d4310-187">Users experience a completely digital environment, and are unaware of what occurs in the physical environment around them.</span></span>


## <a name="see-also"></a><span data-ttu-id="d4310-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4310-188">See also</span></span>

* [<span data-ttu-id="d4310-189">什么是全息图？</span><span class="sxs-lookup"><span data-stu-id="d4310-189">What is a hologram?</span></span>](hologram.md)
* [<span data-ttu-id="d4310-190">了解混合现实的基本知识</span><span class="sxs-lookup"><span data-stu-id="d4310-190">Understand the basics of mixed reality</span></span>](index.md#understand-the-basics)
* [<span data-ttu-id="d4310-191">开始创建和原型设计</span><span class="sxs-lookup"><span data-stu-id="d4310-191">Start creating and prototyping</span></span>](design.md)
* [<span data-ttu-id="d4310-192">了解工具和体系结构</span><span class="sxs-lookup"><span data-stu-id="d4310-192">Learn the tools and architecture</span></span>](development.md)

