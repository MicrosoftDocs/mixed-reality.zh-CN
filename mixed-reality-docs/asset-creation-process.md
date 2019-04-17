---
title: 资产创建过程
description: 创建混合的现实体验的资产的指导。
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: 资产、 创建、 进程、 预算、 多边形、 纹理、 着色器性能
ms.openlocfilehash: cec689ab4d44591d2d3e84679c3fe51dba161bc5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592990"
---
# <a name="asset-creation-process"></a><span data-ttu-id="70553-104">资产创建过程</span><span class="sxs-lookup"><span data-stu-id="70553-104">Asset creation process</span></span>

<span data-ttu-id="70553-105">Windows Mixed Reality 基于数十年的 Microsoft 提供了到 DirectX 的投资。</span><span class="sxs-lookup"><span data-stu-id="70553-105">Windows Mixed Reality builds on the decades of investment Microsoft has made into DirectX.</span></span> <span data-ttu-id="70553-106">这意味着所有的经验和技能的开发人员必须构建 3D 图形仍然是与 HoloLens 有价值。</span><span class="sxs-lookup"><span data-stu-id="70553-106">This means that all of the experience and skills developers have with building 3D graphics continues to be valuable with HoloLens.</span></span>

<span data-ttu-id="70553-107">为项目创建的资产有多种形式和窗体。</span><span class="sxs-lookup"><span data-stu-id="70553-107">The assets you create for a project come in many shapes and forms.</span></span> <span data-ttu-id="70553-108">它们可以包含一系列的纹理/图像、 音频、 视频、 三维模型和动画。</span><span class="sxs-lookup"><span data-stu-id="70553-108">They can be comprised of a series of textures/images, audio, video, 3D models and animations.</span></span> <span data-ttu-id="70553-109">我们无法开始介绍可用于创建不同类型的资产使用在项目中的所有工具。</span><span class="sxs-lookup"><span data-stu-id="70553-109">We can't begin to cover all the tools that are available to create the different types of assets used in a project.</span></span> <span data-ttu-id="70553-110">本文中我们将重点介绍 3D 资产创建方法。</span><span class="sxs-lookup"><span data-stu-id="70553-110">For this article we will focus on 3D asset creation methods.</span></span>

<span data-ttu-id="70553-111">![概念、 创建、 集成和迭代的流](images/concept-creation-integration-iteration-flow-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="70553-111">![Concept, creation, integration and iteration flow](images/concept-creation-integration-iteration-flow-640px.jpg)</span></span><br>
<span data-ttu-id="70553-112">*概念、 创建、 集成和迭代的流*</span><span class="sxs-lookup"><span data-stu-id="70553-112">*Concept, creation, integration and iteration flow*</span></span>

## <a name="things-to-consider"></a><span data-ttu-id="70553-113">注意事项</span><span class="sxs-lookup"><span data-stu-id="70553-113">Things to consider</span></span>

<span data-ttu-id="70553-114">当查看想要创建的体验将其作为**预算**花费以尝试创建最佳体验。</span><span class="sxs-lookup"><span data-stu-id="70553-114">When looking at the experience you're trying to create think of it as a **budget** that you can spend to try to create the best experience.</span></span> <span data-ttu-id="70553-115">数量不一定是硬性限制**多边形**或**类型的材料**在你的资产，但更权衡一预算的组中使用。</span><span class="sxs-lookup"><span data-stu-id="70553-115">There is not necessarily hard limits on the number of **polygons** or **types of materials** use in your assets but more a budgeted set of tradeoffs.</span></span>

<span data-ttu-id="70553-116">下面是示例预算为你的体验。</span><span class="sxs-lookup"><span data-stu-id="70553-116">Below is an example budget for your experience.</span></span> <span data-ttu-id="70553-117">性能通常不是单点故障，但通过千位切割每-se 死亡。</span><span class="sxs-lookup"><span data-stu-id="70553-117">Performance is usually not a single point of failure but death by a thousand cuts per-se.</span></span>
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><span data-ttu-id="70553-118"><b>资产</b></span><span class="sxs-lookup"><span data-stu-id="70553-118"><b>Assets</b></span></span></th><th style="text-align:right;"> <span data-ttu-id="70553-119">CPU</span><span class="sxs-lookup"><span data-stu-id="70553-119">CPU</span></span></th><th> <span data-ttu-id="70553-120">GPU</span><span class="sxs-lookup"><span data-stu-id="70553-120">GPU</span></span></th><th> <span data-ttu-id="70553-121">内存</span><span class="sxs-lookup"><span data-stu-id="70553-121">Memory</span></span></th>
</tr><tr>
<td> <span data-ttu-id="70553-122">多边形</span><span class="sxs-lookup"><span data-stu-id="70553-122">Polygons</span></span></td><td> <span data-ttu-id="70553-123">0%</span><span class="sxs-lookup"><span data-stu-id="70553-123">0%</span></span></td><td> <span data-ttu-id="70553-124">5%</span><span class="sxs-lookup"><span data-stu-id="70553-124">5%</span></span></td><td> <span data-ttu-id="70553-125">10%</span><span class="sxs-lookup"><span data-stu-id="70553-125">10%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="70553-126">纹理</span><span class="sxs-lookup"><span data-stu-id="70553-126">Textures</span></span></td><td> <span data-ttu-id="70553-127">5%</span><span class="sxs-lookup"><span data-stu-id="70553-127">5%</span></span></td><td> <span data-ttu-id="70553-128">15%</span><span class="sxs-lookup"><span data-stu-id="70553-128">15%</span></span></td><td><span data-ttu-id="70553-129">25%</span><span class="sxs-lookup"><span data-stu-id="70553-129">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="70553-130">着色器</span><span class="sxs-lookup"><span data-stu-id="70553-130">Shaders</span></span></td><td> <span data-ttu-id="70553-131">15%</span><span class="sxs-lookup"><span data-stu-id="70553-131">15%</span></span></td><td> <span data-ttu-id="70553-132">35%</span><span class="sxs-lookup"><span data-stu-id="70553-132">35%</span></span></td><td> <span data-ttu-id="70553-133">0%</span><span class="sxs-lookup"><span data-stu-id="70553-133">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="70553-134"><b>Dynamics</b></span><span class="sxs-lookup"><span data-stu-id="70553-134"><b>Dynamics</b></span></span></td><td></td><td></td><td></td>
</tr><tr>
<td> <span data-ttu-id="70553-135">物理引擎</span><span class="sxs-lookup"><span data-stu-id="70553-135">Physics</span></span></td><td> <span data-ttu-id="70553-136">5%</span><span class="sxs-lookup"><span data-stu-id="70553-136">5%</span></span></td><td> <span data-ttu-id="70553-137">15%</span><span class="sxs-lookup"><span data-stu-id="70553-137">15%</span></span></td><td> <span data-ttu-id="70553-138">0%</span><span class="sxs-lookup"><span data-stu-id="70553-138">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="70553-139">实时照明</span><span class="sxs-lookup"><span data-stu-id="70553-139">Realtime lighting</span></span></td><td> <span data-ttu-id="70553-140">10%</span><span class="sxs-lookup"><span data-stu-id="70553-140">10%</span></span></td><td> <span data-ttu-id="70553-141">0%</span><span class="sxs-lookup"><span data-stu-id="70553-141">0%</span></span></td><td> <span data-ttu-id="70553-142">0%</span><span class="sxs-lookup"><span data-stu-id="70553-142">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="70553-143">媒体 （音频/视频）</span><span class="sxs-lookup"><span data-stu-id="70553-143">Media (audio/video)</span></span></td><td> -</td><td> <span data-ttu-id="70553-144">15%</span><span class="sxs-lookup"><span data-stu-id="70553-144">15%</span></span></td><td> <span data-ttu-id="70553-145">25%</span><span class="sxs-lookup"><span data-stu-id="70553-145">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="70553-146">脚本/逻辑</span><span class="sxs-lookup"><span data-stu-id="70553-146">Script/logic</span></span></td><td> <span data-ttu-id="70553-147">25%</span><span class="sxs-lookup"><span data-stu-id="70553-147">25%</span></span></td><td> <span data-ttu-id="70553-148">0%</span><span class="sxs-lookup"><span data-stu-id="70553-148">0%</span></span></td><td> <span data-ttu-id="70553-149">5%</span><span class="sxs-lookup"><span data-stu-id="70553-149">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="70553-150">常规的开销</span><span class="sxs-lookup"><span data-stu-id="70553-150">General overhead</span></span></td><td> <span data-ttu-id="70553-151">5%</span><span class="sxs-lookup"><span data-stu-id="70553-151">5%</span></span></td><td> <span data-ttu-id="70553-152">5%</span><span class="sxs-lookup"><span data-stu-id="70553-152">5%</span></span></td><td> <span data-ttu-id="70553-153">5%</span><span class="sxs-lookup"><span data-stu-id="70553-153">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="70553-154"><b>总计</b></span><span class="sxs-lookup"><span data-stu-id="70553-154"><b>Total</b></span></span></td><td> <span data-ttu-id="70553-155"><b>65%</b></span><span class="sxs-lookup"><span data-stu-id="70553-155"><b>65%</b></span></span></td><td> <span data-ttu-id="70553-156"><b>90%</b></span><span class="sxs-lookup"><span data-stu-id="70553-156"><b>90%</b></span></span></td><td> <span data-ttu-id="70553-157"><b>70%</b></span><span class="sxs-lookup"><span data-stu-id="70553-157"><b>70%</b></span></span></td>
</tr>
</table>

<span data-ttu-id="70553-158">**资产的总数**</span><span class="sxs-lookup"><span data-stu-id="70553-158">**Total number of assets**</span></span>
* <span data-ttu-id="70553-159">场景中处于活动状态多少资产？</span><span class="sxs-lookup"><span data-stu-id="70553-159">How many assets are active in the scene?</span></span>

<span data-ttu-id="70553-160">**资产的复杂性**</span><span class="sxs-lookup"><span data-stu-id="70553-160">**Complexity of assets**</span></span>
* <span data-ttu-id="70553-161">多少三角形 / 多边形？</span><span class="sxs-lookup"><span data-stu-id="70553-161">How many triangles / polygons?</span></span>
* <span data-ttu-id="70553-162">复杂程度是着色器？</span><span class="sxs-lookup"><span data-stu-id="70553-162">How complex is the shader?</span></span>

<span data-ttu-id="70553-163">开发人员和艺术家不得不考虑设备和图形引擎的功能。</span><span class="sxs-lookup"><span data-stu-id="70553-163">Both the developers and artists have to consider the capabilities of the device and the graphics engine.</span></span> <span data-ttu-id="70553-164">Microsoft HoloLens 具有所有的计算和图形内置于该设备。</span><span class="sxs-lookup"><span data-stu-id="70553-164">Microsoft HoloLens has all of the computational and graphics built into the device.</span></span> <span data-ttu-id="70553-165">它会共享开发人员会发现在移动平台的功能。</span><span class="sxs-lookup"><span data-stu-id="70553-165">It shares the capabilities developers would find on a mobile platform.</span></span>

<span data-ttu-id="70553-166">资产创建过程是相同的无论您的目标的体验如何[holographic 的设备或沉浸式设备](mixed-reality.md#the-mixed-reality-spectrum)。</span><span class="sxs-lookup"><span data-stu-id="70553-166">The creation process for assets is the same regardless of whether you're targeting an experience for a [holographic device or an immersive device](mixed-reality.md#the-mixed-reality-spectrum).</span></span> <span data-ttu-id="70553-167">需要注意的主要事项就是设备功能，以及缩放如上所述，由于可以在想要维护正确的缩放范围基于体验的混合现实中看到现实世界。</span><span class="sxs-lookup"><span data-stu-id="70553-167">The primary thing to note is the device capability as mentioned above as well as scale since you can see the real world in mixed reality you will want to maintain the correct scale based on the experience.</span></span> 

## <a name="authoring-assets"></a><span data-ttu-id="70553-168">创作资产</span><span class="sxs-lookup"><span data-stu-id="70553-168">Authoring Assets</span></span>

<span data-ttu-id="70553-169">我们将开始为你的项目资产中获取的方法：</span><span class="sxs-lookup"><span data-stu-id="70553-169">We'll start with the ways to get assets for your project:</span></span>
1. <span data-ttu-id="70553-170">创建资产 （创作工具和对象捕获）</span><span class="sxs-lookup"><span data-stu-id="70553-170">Creating Assets (Authoring tools and object capture)</span></span>
2. <span data-ttu-id="70553-171">购买资产 （联机购买资产）</span><span class="sxs-lookup"><span data-stu-id="70553-171">Purchasing Assets (Buying assets online)</span></span>
3. <span data-ttu-id="70553-172">移植资产 （使用现有的资产）</span><span class="sxs-lookup"><span data-stu-id="70553-172">Porting Assets (Taking existing assets)</span></span>
4. <span data-ttu-id="70553-173">外包资产 （从第三方导入资产）</span><span class="sxs-lookup"><span data-stu-id="70553-173">Outsourcing Assets (Importing assets from 3rd parties)</span></span>

### <a name="creating-assets"></a><span data-ttu-id="70553-174">创建资产</span><span class="sxs-lookup"><span data-stu-id="70553-174">Creating assets</span></span>

<span data-ttu-id="70553-175">**创作工具**</span><span class="sxs-lookup"><span data-stu-id="70553-175">**Authoring tools**</span></span><br>
<span data-ttu-id="70553-176">首先可以通过多种不同的方式创建你自己的资产。</span><span class="sxs-lookup"><span data-stu-id="70553-176">First you can create your own assets in a number of different ways.</span></span> <span data-ttu-id="70553-177">3D 艺术家使用大量的应用程序和工具创建模型组成**网格**，**纹理**，并**材料**。</span><span class="sxs-lookup"><span data-stu-id="70553-177">3D artists use a number of applications and tools to create models which consist of **meshes**, **textures**, and **materials**.</span></span> <span data-ttu-id="70553-178">这随后保存的文件格式，可以导入或图形引擎由应用程序中，如使用 **。FBX**或 **。OBJ**。</span><span class="sxs-lookup"><span data-stu-id="70553-178">This is then saved in a file format that can be imported or used by the graphics engine used by the app, such as **.FBX** or **.OBJ**.</span></span> <span data-ttu-id="70553-179">任何工具，可生成所选的图形引擎支持的模型将着手**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="70553-179">Any tool that generates a model that your chosen graphics engine supports will work on **HoloLens**.</span></span> <span data-ttu-id="70553-180">在 3D 艺术家之间很多选择使用[Autodesk Maya 本身是能够使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)要转换的方法创建资产。</span><span class="sxs-lookup"><span data-stu-id="70553-180">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="70553-181">如果你想要在快速获取内容还可以使用[3D 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)随附 Windows 导出。在你的应用程序中使用 OBJ。</span><span class="sxs-lookup"><span data-stu-id="70553-181">If you want to get something in quick you can also use [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) that comes with Windows to export .OBJ for use in your application.</span></span>

<span data-ttu-id="70553-182">**对象捕获**</span><span class="sxs-lookup"><span data-stu-id="70553-182">**Object capture**</span></span><br>
<span data-ttu-id="70553-183">此外，还有选项以捕获以三维形式的对象。</span><span class="sxs-lookup"><span data-stu-id="70553-183">There is also the option to capture objects in 3D.</span></span> <span data-ttu-id="70553-184">捕获在 3D 死气沉沉和编辑其数字内容创建软件是 3D 打印的发展越来越受欢迎。</span><span class="sxs-lookup"><span data-stu-id="70553-184">Capturing inanimate objects in 3D and editing them with digital content creation software is increasingly popular with the rise of 3D printing.</span></span> <span data-ttu-id="70553-185">使用**Kinect 2**传感器和[3D 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)可以使用捕获功能从现实世界对象创建资产。</span><span class="sxs-lookup"><span data-stu-id="70553-185">Using the **Kinect 2** sensor and [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) you can use the capture feature to create assets from real world objects.</span></span> <span data-ttu-id="70553-186">这也是[的工具套件](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software)执行与相同**photogrammetry**通过处理一些拼接在一起和网格与纹理的图像。</span><span class="sxs-lookup"><span data-stu-id="70553-186">This is also a [suite of tools](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) to do the same with **photogrammetry** by processing a number of images to stitch together and mesh and textures.</span></span>

### <a name="purchasing-assets"></a><span data-ttu-id="70553-187">购买资产</span><span class="sxs-lookup"><span data-stu-id="70553-187">Purchasing assets</span></span>

<span data-ttu-id="70553-188">另一个极好的选择是购买你的体验的资产。</span><span class="sxs-lookup"><span data-stu-id="70553-188">Another excellent option is to purchase assets for your experience.</span></span> <span data-ttu-id="70553-189">有大量的资产可通过服务如[Unity 资产商店](https://www.assetstore.unity3d.com/)或[TurboSquid](http://www.turbosquid.com/)等等。</span><span class="sxs-lookup"><span data-stu-id="70553-189">There are a ton of assets available through services such as the [Unity Asset Store](https://www.assetstore.unity3d.com/) or [TurboSquid](http://www.turbosquid.com/) among others.</span></span>

<span data-ttu-id="70553-190">当从第三方购买资产时始终想要检查以下各项：</span><span class="sxs-lookup"><span data-stu-id="70553-190">When you purchase assets from a 3rd party you always want to check the following:</span></span>
* <span data-ttu-id="70553-191">**什么是多边形计数？**</span><span class="sxs-lookup"><span data-stu-id="70553-191">**What's the poly count?**</span></span>
  * <span data-ttu-id="70553-192">它是否适合你的预算？</span><span class="sxs-lookup"><span data-stu-id="70553-192">Does it fit within your budget?</span></span>
* <span data-ttu-id="70553-193">**是否有级别 (Lod) 的模型的详细信息？**</span><span class="sxs-lookup"><span data-stu-id="70553-193">**Are there levels of detail (LODs) for the model?**</span></span>
  * <span data-ttu-id="70553-194">模型的详细信息级别，可缩放的性能的模型的详细信息。</span><span class="sxs-lookup"><span data-stu-id="70553-194">Level of detail of a model allow you to scale the detail of a model for performance.</span></span>
* <span data-ttu-id="70553-195">**源文件是否可用？**</span><span class="sxs-lookup"><span data-stu-id="70553-195">**Is the source file available?**</span></span>
  * <span data-ttu-id="70553-196">通常不包括在[Unity 资产商店](https://www.assetstore.unity3d.com/)始终附带等服务，但[TurboSquid](http://www.turbosquid.com/)。</span><span class="sxs-lookup"><span data-stu-id="70553-196">Usually not included with [Unity Asset Store](https://www.assetstore.unity3d.com/) but always included with services like [TurboSquid](http://www.turbosquid.com/).</span></span>
  * <span data-ttu-id="70553-197">没有源代码文件的情况下你将无法修改资产。</span><span class="sxs-lookup"><span data-stu-id="70553-197">Without the source file you won't be able to modify the asset.</span></span>
  * <span data-ttu-id="70553-198">请确保你 3D 工具可以导入提供的源代码文件。</span><span class="sxs-lookup"><span data-stu-id="70553-198">Make sure the source file provided can be imported by your 3D tools.</span></span>
* <span data-ttu-id="70553-199">**知道您得到什么**</span><span class="sxs-lookup"><span data-stu-id="70553-199">**Know what you're getting**</span></span>
  * <span data-ttu-id="70553-200">提供了动画？</span><span class="sxs-lookup"><span data-stu-id="70553-200">Are animations provided?</span></span>
  * <span data-ttu-id="70553-201">请务必检查您打算购买的资产的内容列表。</span><span class="sxs-lookup"><span data-stu-id="70553-201">Make sure to check the contents list of the asset you're purchasing.</span></span>

### <a name="porting-assets"></a><span data-ttu-id="70553-202">移植资产</span><span class="sxs-lookup"><span data-stu-id="70553-202">Porting assets</span></span>

<span data-ttu-id="70553-203">在某些情况下将传递为其他设备和不同的应用程序最初生成的现有资产。</span><span class="sxs-lookup"><span data-stu-id="70553-203">In some cases you'll be handed existing assets that were originally built for other devices and different apps.</span></span> <span data-ttu-id="70553-204">在大多数情况下这些资产可以转换为使用自己的应用程序的图形引擎与兼容的格式。</span><span class="sxs-lookup"><span data-stu-id="70553-204">In most cases these assets can be converted to formats compatible with the graphics engine their app is using.</span></span>

<span data-ttu-id="70553-205">移植资产 HoloLens 应用程序中使用时，想要询问以下：</span><span class="sxs-lookup"><span data-stu-id="70553-205">When porting assets to use in your HoloLens application you will want to ask the following:</span></span>
* <span data-ttu-id="70553-206">**可以在直接导入或确实需要转换为另一种格式？**</span><span class="sxs-lookup"><span data-stu-id="70553-206">**Can you import directly or does need to be converted to another format?**</span></span> <span data-ttu-id="70553-207">检查要与图形引擎使用导入的格式。</span><span class="sxs-lookup"><span data-stu-id="70553-207">Check the format you're importing with the graphics engine you're using.</span></span>
* <span data-ttu-id="70553-208">**如果将转换为兼容的格式是任何内容丢失？**</span><span class="sxs-lookup"><span data-stu-id="70553-208">**If converting to a compatible format is anything lost?**</span></span> <span data-ttu-id="70553-209">有时可能会丢失的详细信息，或导入可能会导致需要清理 3D 创作工具中的项目。</span><span class="sxs-lookup"><span data-stu-id="70553-209">Sometimes details can be lost or importing can cause artifacts that need to be cleaned up in a 3D authoring tool.</span></span>
* <span data-ttu-id="70553-210">**什么是三角形/多边形计数为资产？**</span><span class="sxs-lookup"><span data-stu-id="70553-210">**What is the triangles / polygons count for the asset?**</span></span> <span data-ttu-id="70553-211">根据为应用程序可以使用预算[Simplygon](https://www.simplygon.com/)或类似的工具来竞技 （虽然或手动减小多边形计数） 原始的资产，以适合你的应用程序的预算。</span><span class="sxs-lookup"><span data-stu-id="70553-211">Based on the budget for you application you can use [Simplygon](https://www.simplygon.com/) or similar tools to decimate (procedurally or manually reduce poly count) the original asset to fit within your applications budget.</span></span>

### <a name="outsourcing-assets"></a><span data-ttu-id="70553-212">外包资产</span><span class="sxs-lookup"><span data-stu-id="70553-212">Outsourcing assets</span></span>

<span data-ttu-id="70553-213">需要多个资产比你的团队的较大项目的另一个选项是能够创建是外包资产创建。</span><span class="sxs-lookup"><span data-stu-id="70553-213">Another option for larger projects that require more assets than your team is equipped to create is to outsource asset creation.</span></span> <span data-ttu-id="70553-214">外包的过程涉及到查找正确的 studio 或专门的机构外包资产中。</span><span class="sxs-lookup"><span data-stu-id="70553-214">The process of outsourcing involves finding the right studio or agency that specializes in outsourcing assets.</span></span> <span data-ttu-id="70553-215">这可以最高的选项，但也是最灵活中获得的内容。</span><span class="sxs-lookup"><span data-stu-id="70553-215">This can be the most expensive option but also be the most flexible in what you get.</span></span>
* <span data-ttu-id="70553-216">**清楚地定义您的请求**</span><span class="sxs-lookup"><span data-stu-id="70553-216">**Clearly define what you're requesting**</span></span>
  * <span data-ttu-id="70553-217">尽量提供详尽的信息</span><span class="sxs-lookup"><span data-stu-id="70553-217">Provide as much detail as possible</span></span>
  * <span data-ttu-id="70553-218">前端、 端和后的概念图像</span><span class="sxs-lookup"><span data-stu-id="70553-218">Front, side and back concept images</span></span>
  * <span data-ttu-id="70553-219">在上下文中引用艺术显示资产</span><span class="sxs-lookup"><span data-stu-id="70553-219">Reference art showing asset in context</span></span>
  * <span data-ttu-id="70553-220">（通常以厘米为单位指定） 的对象的小数位数</span><span class="sxs-lookup"><span data-stu-id="70553-220">Scale of object (Usually specified in centimeters)</span></span>
* <span data-ttu-id="70553-221">**提供预算**</span><span class="sxs-lookup"><span data-stu-id="70553-221">**Provide a Budget**</span></span>
  * <span data-ttu-id="70553-222">多边形计数范围</span><span class="sxs-lookup"><span data-stu-id="70553-222">Poly count range</span></span>
  * <span data-ttu-id="70553-223">纹理数</span><span class="sxs-lookup"><span data-stu-id="70553-223">Number of textures</span></span>
  * <span data-ttu-id="70553-224">类型的着色器 （用于 Unity 和 HoloLens 您应始终默认为移动着色器第一次）</span><span class="sxs-lookup"><span data-stu-id="70553-224">Type of shader (For Unity and HoloLens you should always default to mobile shaders first)</span></span>
* <span data-ttu-id="70553-225">**了解产生的成本**</span><span class="sxs-lookup"><span data-stu-id="70553-225">**Understand the costs**</span></span>
  * <span data-ttu-id="70553-226">更改请求的外包策略是什么？</span><span class="sxs-lookup"><span data-stu-id="70553-226">What's the outsourcing policy for change requests?</span></span>

<span data-ttu-id="70553-227">外包可特别适合基于项目时间线上，但需要更多的监督功能，可保证获得正确的资产需要第一次。</span><span class="sxs-lookup"><span data-stu-id="70553-227">Outsourcing can work extremely well based on your projects timeline but requires more oversight to guarantee that you get the right assets you need the first time.</span></span>
