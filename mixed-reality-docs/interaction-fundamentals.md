---
title: 交互基础知识
description: 如我们构建了跨 HoloLens 体验 （第 1 代） HoloLens 2 和沉浸式耳机，我们已经开始写下我们发现用于共享的一些事项。
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实，交互设计
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590104"
---
# <a name="interaction-fundamentals"></a><span data-ttu-id="ad401-104">交互基础知识</span><span class="sxs-lookup"><span data-stu-id="ad401-104">Interaction fundamentals</span></span>

<span data-ttu-id="ad401-105">在跨 HoloLens 和沉浸式耳机，我们已构建的体验，我们已经开始写下我们发现用于共享的一些事项。</span><span class="sxs-lookup"><span data-stu-id="ad401-105">As we've built experiences across HoloLens and immersive headsets, we've started writing down some things we found useful to share.</span></span> <span data-ttu-id="ad401-106">将它们视为用于混合的现实交互设计的基本构建块。</span><span class="sxs-lookup"><span data-stu-id="ad401-106">Think of these as the fundamental building blocks for mixed reality interaction design.</span></span>

## <a name="device-support"></a><span data-ttu-id="ad401-107">设备支持</span><span class="sxs-lookup"><span data-stu-id="ad401-107">Device support</span></span>

<span data-ttu-id="ad401-108">下面是适用于可用的交互设计文章的设备类型或类型的概述。</span><span class="sxs-lookup"><span data-stu-id="ad401-108">Here's an outline of the available Interaction design articles and which device type or types they apply to.</span></span>
<br>

<table>

<th>
<tr>

<td style="width:150px;"><span data-ttu-id="ad401-109"><strong>输入</strong></span><span class="sxs-lookup"><span data-stu-id="ad401-109"><strong>Input</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="ad401-110"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="ad401-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="ad401-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="ad401-111"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="ad401-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></span><span class="sxs-lookup"><span data-stu-id="ad401-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
 
<tr>
<td> <span data-ttu-id="ad401-113"><a href="gestures.md">明确的手</a></span><span class="sxs-lookup"><span data-stu-id="ad401-113"><a href="gestures.md">Articulated hands</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="ad401-114">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-114">✔️</span></span></td><td></td>

</tr><tr>
<td> <span data-ttu-id="ad401-115"><a href="gaze-targeting.md">密切关注面向</a></span><span class="sxs-lookup"><span data-stu-id="ad401-115"><a href="gaze-targeting.md">Eye targeting</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="ad401-116">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-116">✔️</span></span></td><td style="text-align: center;"></td>
</tr><tr>
<td> <span data-ttu-id="ad401-117"><a href="gaze-targeting.md">目标的视线移动</a></span><span class="sxs-lookup"><span data-stu-id="ad401-117"><a href="gaze-targeting.md">Gaze targeting</a></span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-118">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-118">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-119">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-119">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-120">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-120">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ad401-121"><a href="gestures.md">手势</a></span><span class="sxs-lookup"><span data-stu-id="ad401-121"><a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-122">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-122">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-123">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-123">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="ad401-124"><a href="voice-design.md">语音设计</a></span><span class="sxs-lookup"><span data-stu-id="ad401-124"><a href="voice-design.md">Voice design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-125">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-125">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-126">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-127">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-127">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ad401-128">游戏板</span><span class="sxs-lookup"><span data-stu-id="ad401-128">Gamepad</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-129">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-130">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-131">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-131">✔️</span></span></td>
</tr>
<tr>
<td> <span data-ttu-id="ad401-132"><a href="motion-controllers.md">运动控制器</a></span><span class="sxs-lookup"><span data-stu-id="ad401-132"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="ad401-133">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-133">✔️</span></span></td>

</tr>
<th>
<tr>
<td style="width:150px;"><span data-ttu-id="ad401-134"><strong>认知和空间功能</strong></span><span class="sxs-lookup"><span data-stu-id="ad401-134"><strong>Perception and spatial features</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="ad401-135"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="ad401-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="ad401-136"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="ad401-136"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="ad401-137"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></span><span class="sxs-lookup"><span data-stu-id="ad401-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
<tr>

<td> <span data-ttu-id="ad401-138"><a href="spatial-sound-design.md">空间合理的设计</a></span><span class="sxs-lookup"><span data-stu-id="ad401-138"><a href="spatial-sound-design.md">Spatial sound design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-139">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-139">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-140">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-140">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-141">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-141">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="ad401-142"><a href="spatial-mapping-design.md">空间映射设计</a></span><span class="sxs-lookup"><span data-stu-id="ad401-142"><a href="spatial-mapping-design.md">Spatial mapping design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-143">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-144">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-144">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="ad401-145"><a href="hologram.md">全息</a></span><span class="sxs-lookup"><span data-stu-id="ad401-145"><a href="hologram.md">Holograms</a></span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-146">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-146">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ad401-147">✔️</span><span class="sxs-lookup"><span data-stu-id="ad401-147">✔️</span></span></td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a><span data-ttu-id="ad401-148">用户是照相机</span><span class="sxs-lookup"><span data-stu-id="ad401-148">The user is the camera</span></span>

![用户是照相机](images/useriscamera-640px.jpg)

<span data-ttu-id="ad401-150">始终考虑设计的用户的角度来看，随着有关其实际和虚拟世界。</span><span class="sxs-lookup"><span data-stu-id="ad401-150">Always think about design for your user's point of view as they move about their real and virtual worlds.</span></span>

<span data-ttu-id="ad401-151">**要提出的一些问题**</span><span class="sxs-lookup"><span data-stu-id="ad401-151">**Some questions to ask**</span></span>
* <span data-ttu-id="ad401-152">用户、 倾斜度、 站着，还是使用您的体验时的每个步骤？</span><span class="sxs-lookup"><span data-stu-id="ad401-152">Is the user sitting, reclining, standing, or walking while using your experience?</span></span>
* <span data-ttu-id="ad401-153">你的内容 does 如何调整到不同的位置？</span><span class="sxs-lookup"><span data-stu-id="ad401-153">How does your content adjust to different positions?</span></span>
* <span data-ttu-id="ad401-154">用户可以调整它？</span><span class="sxs-lookup"><span data-stu-id="ad401-154">Can the user adjust it?</span></span>
* <span data-ttu-id="ad401-155">用户是熟练使用您的应用程序？</span><span class="sxs-lookup"><span data-stu-id="ad401-155">Will the user be comfortable using your app?</span></span>

<span data-ttu-id="ad401-156">**最佳做法**</span><span class="sxs-lookup"><span data-stu-id="ad401-156">**Best practices**</span></span>
* <span data-ttu-id="ad401-157">用户是照相机和它们控制移动。</span><span class="sxs-lookup"><span data-stu-id="ad401-157">The user is the camera and they control the movement.</span></span> <span data-ttu-id="ad401-158">让这些驱动器。</span><span class="sxs-lookup"><span data-stu-id="ad401-158">Let them drive.</span></span>
* <span data-ttu-id="ad401-159">如果你需要几乎传输用户，是对 vestibular 不适围绕这些问题的敏感。</span><span class="sxs-lookup"><span data-stu-id="ad401-159">If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.</span></span>
* <span data-ttu-id="ad401-160">使用较短的动画</span><span class="sxs-lookup"><span data-stu-id="ad401-160">Use shorter animations</span></span>
* <span data-ttu-id="ad401-161">向下/左/右从进行动画处理或淡入，而不是 Z</span><span class="sxs-lookup"><span data-stu-id="ad401-161">Animate from down/left/right or fade in instead of Z</span></span>
* <span data-ttu-id="ad401-162">计时变慢</span><span class="sxs-lookup"><span data-stu-id="ad401-162">Slow down timing</span></span>
* <span data-ttu-id="ad401-163">允许用户查看在后台世界</span><span class="sxs-lookup"><span data-stu-id="ad401-163">Allow user to see the world in the background</span></span>

<span data-ttu-id="ad401-164">**要避免的问题**</span><span class="sxs-lookup"><span data-stu-id="ad401-164">**What to avoid**</span></span>
* <span data-ttu-id="ad401-165">不要摇动照相机或有意将其锁定到 3DOF 仅方向 (未转换），它可以让用户感到不安。</span><span class="sxs-lookup"><span data-stu-id="ad401-165">Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.</span></span>
* <span data-ttu-id="ad401-166">无突然移动。</span><span class="sxs-lookup"><span data-stu-id="ad401-166">No abrupt movement.</span></span> <span data-ttu-id="ad401-167">如果你需要将内容与用户，将其移动速度慢、 更流畅地向其最大舒适。</span><span class="sxs-lookup"><span data-stu-id="ad401-167">If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.</span></span> <span data-ttu-id="ad401-168">用户将对大型菜单在它们即将做出反应。</span><span class="sxs-lookup"><span data-stu-id="ad401-168">Users will react to large menus coming at them.</span></span>
* <span data-ttu-id="ad401-169">不加速或启用用户的照相机。</span><span class="sxs-lookup"><span data-stu-id="ad401-169">Don't accelerate or turn the user's camera.</span></span> <span data-ttu-id="ad401-170">用户很敏感加速 （angular 和平移）。</span><span class="sxs-lookup"><span data-stu-id="ad401-170">Users are sensitive to acceleration (both angular and translational).</span></span>

## <a name="leverage-the-users-perspective"></a><span data-ttu-id="ad401-171">利用用户的角度来看</span><span class="sxs-lookup"><span data-stu-id="ad401-171">Leverage the user's perspective</span></span>

<span data-ttu-id="ad401-172">用户在沉浸式和全息版的设备上看到显示通过混合现实的世界。</span><span class="sxs-lookup"><span data-stu-id="ad401-172">Users see the world of mixed reality through displays on immersive and holographic devices.</span></span> <span data-ttu-id="ad401-173">在 HoloLens 上此效果称为[holographic 帧](holographic-frame.md)。</span><span class="sxs-lookup"><span data-stu-id="ad401-173">On the HoloLens, this display is called the [holographic frame](holographic-frame.md).</span></span>

<span data-ttu-id="ad401-174">在 2D 开发中，频繁访问的内容和设置可能会位于屏幕以使其可以轻松进行访问的角。</span><span class="sxs-lookup"><span data-stu-id="ad401-174">In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible.</span></span> <span data-ttu-id="ad401-175">但是，在全息版应用中，用户的视图的角落中的内容可能会不喜欢以访问。</span><span class="sxs-lookup"><span data-stu-id="ad401-175">However, in holographic apps, content in the corners of the user's view may be uncomfortable to access.</span></span> <span data-ttu-id="ad401-176">在这种情况下，holographic 帧的中心是有关内容的主要位置。</span><span class="sxs-lookup"><span data-stu-id="ad401-176">In this case, the center of the holographic frame is the prime location for content.</span></span>

<span data-ttu-id="ad401-177">用户可能需要指导来帮助查找重要的事件或对象超出其即时视图。</span><span class="sxs-lookup"><span data-stu-id="ad401-177">The user may need to be guided to help locate important events or objects beyond their immediate view.</span></span> <span data-ttu-id="ad401-178">可以使用箭头、 光线跟踪信息、 字符磁头运动、 思想气泡、 指针、 空间声音和语音提示以帮助并指导用户到应用程序中的重要内容。</span><span class="sxs-lookup"><span data-stu-id="ad401-178">You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.</span></span>

<span data-ttu-id="ad401-179">建议对未锁定内容到用户的舒适的屏幕。</span><span class="sxs-lookup"><span data-stu-id="ad401-179">It is recommended to not lock content to the screen for the user's comfort.</span></span> <span data-ttu-id="ad401-180">如果你需要保留内容视图中，将其放在世界上并进行"尾随"类似开始菜单的内容。</span><span class="sxs-lookup"><span data-stu-id="ad401-180">If you need to keep content in view, place it in the world and make the content "tag-along" like the Start menu.</span></span> <span data-ttu-id="ad401-181">获取用户的角度来看以及提取的内容会感觉更自然的环境中。</span><span class="sxs-lookup"><span data-stu-id="ad401-181">Content that gets pulled along with the user's perspective will feel more natural in the environment.</span></span>

<span data-ttu-id="ad401-182">![开始菜单在到达帧的边缘时遵循的用户视图](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ad401-182">![The start menu follows the user's view when it reaches the edge of the frame](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="ad401-183">*开始菜单在到达帧的边缘时遵循的用户视图*</span><span class="sxs-lookup"><span data-stu-id="ad401-183">*The Start menu follows the user's view when it reaches the edge of the frame*</span></span>

<span data-ttu-id="ad401-184">上 HoloLens，全息感觉实际时由于它们不被切断适合 holographic 范围内。</span><span class="sxs-lookup"><span data-stu-id="ad401-184">On HoloLens, holograms feel real when they fit within the holographic frame since they don't get cut off.</span></span> <span data-ttu-id="ad401-185">若要查看在框架内一张全息图的边界将移动用户。</span><span class="sxs-lookup"><span data-stu-id="ad401-185">Users will move in order to see the bounds of a hologram within the frame.</span></span> <span data-ttu-id="ad401-186">在 HoloLens，务必简化您的 UI，使其适合用户的视图中专注于主要操作。</span><span class="sxs-lookup"><span data-stu-id="ad401-186">On HoloLens, it's important to simplify your UI to fit within the user's view and keep your focus on the main action.</span></span> <span data-ttu-id="ad401-187">沉浸式耳机，务必维护持久虚拟世界中设备的视野效果。</span><span class="sxs-lookup"><span data-stu-id="ad401-187">For immersive headsets, it's important to maintain the illusion of a persistent virtual world within the device's field of view.</span></span>

## <a name="user-comfort"></a><span data-ttu-id="ad401-188">用户舒适</span><span class="sxs-lookup"><span data-stu-id="ad401-188">User comfort</span></span>

<span data-ttu-id="ad401-189">若要确保最大[舒适](comfort.md)头装载显示器上非常重要的设计人员和开发人员创建和显示内容中一种方法，以模拟人类如何解释 3D 形状和自然的对象的相对位置世界。</span><span class="sxs-lookup"><span data-stu-id="ad401-189">To ensure maximum [comfort](comfort.md) on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world.</span></span> <span data-ttu-id="ad401-190">从物理角度看，也很重要设计不需要的颈部或手臂 fatiguing 动作的内容。</span><span class="sxs-lookup"><span data-stu-id="ad401-190">From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.</span></span>

<span data-ttu-id="ad401-191">无论开发 HoloLens 或沉浸式耳机，务必要呈现两只眼睛的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="ad401-191">Whether developing for HoloLens or immersive headsets, it is important to render visuals for both eyes.</span></span> <span data-ttu-id="ad401-192">呈现危险警告显示一眼中仅可以使界面难以理解，以及导致 uneasiness 到用户的关注和大脑。</span><span class="sxs-lookup"><span data-stu-id="ad401-192">Rendering a heads-up display in one eye only can make an interface hard to understand, as well as causing uneasiness to the user's eye and brain.</span></span>

## <a name="share-your-experience"></a><span data-ttu-id="ad401-193">共享你的体验</span><span class="sxs-lookup"><span data-stu-id="ad401-193">Share your experience</span></span>

<span data-ttu-id="ad401-194">使用[混合现实捕获](mixed-reality-capture.md)，用户可以捕获照片或视频的任何时候用户体验。</span><span class="sxs-lookup"><span data-stu-id="ad401-194">Using [mixed reality capture](mixed-reality-capture.md), users can capture a photo or video of their experience at any time.</span></span> <span data-ttu-id="ad401-195">请考虑你可能想要鼓励快照或视频应用程序中的体验。</span><span class="sxs-lookup"><span data-stu-id="ad401-195">Consider experiences in your app where you may want to encourage snapshots or videos.</span></span>

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a><span data-ttu-id="ad401-196">利用 Windows Mixed Reality 家庭的基本 UI 元素</span><span class="sxs-lookup"><span data-stu-id="ad401-196">Leverage basic UI elements of the Windows Mixed Reality home</span></span>

<span data-ttu-id="ad401-197">就像 Windows PC 体验始于桌面、 Windows Mixed Reality 开头主页。</span><span class="sxs-lookup"><span data-stu-id="ad401-197">Just like the Windows PC experience starts with the desktop, Windows Mixed Reality starts with the home.</span></span> <span data-ttu-id="ad401-198">[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)利用理解和导航三维位置我们与生俱来的能力。</span><span class="sxs-lookup"><span data-stu-id="ad401-198">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) leverages our innate ability to understand and navigate 3D places.</span></span> <span data-ttu-id="ad401-199">HoloLens，与您在家是物理空间。</span><span class="sxs-lookup"><span data-stu-id="ad401-199">With HoloLens, your home is your physical space.</span></span> <span data-ttu-id="ad401-200">沉浸式耳机，与您在家是一个虚拟位置。</span><span class="sxs-lookup"><span data-stu-id="ad401-200">With immersive headsets, your home is a virtual place.</span></span>

<span data-ttu-id="ad401-201">您家也是在其中将使用开始菜单打开和放置应用程序和内容。</span><span class="sxs-lookup"><span data-stu-id="ad401-201">Your home is also where you’ll use the Start menu to open and place apps and content.</span></span> <span data-ttu-id="ad401-202">可以使用混合的现实内容填充您家并同时使用多个应用程序执行多任务。</span><span class="sxs-lookup"><span data-stu-id="ad401-202">You can fill your home with mixed reality content and multitask by using multiple apps at the same time.</span></span> <span data-ttu-id="ad401-203">在家中放置的内容继续保留在那里，即使您重新启动你的设备。</span><span class="sxs-lookup"><span data-stu-id="ad401-203">The things you place in your home stay there, even if you restart your device.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad401-204">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad401-204">See also</span></span>
* [<span data-ttu-id="ad401-205">目标的视线移动</span><span class="sxs-lookup"><span data-stu-id="ad401-205">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="ad401-206">手势</span><span class="sxs-lookup"><span data-stu-id="ad401-206">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="ad401-207">语音设计</span><span class="sxs-lookup"><span data-stu-id="ad401-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="ad401-208">运动控制器</span><span class="sxs-lookup"><span data-stu-id="ad401-208">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="ad401-209">空间合理的设计</span><span class="sxs-lookup"><span data-stu-id="ad401-209">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="ad401-210">空间映射设计</span><span class="sxs-lookup"><span data-stu-id="ad401-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="ad401-211">Comfort</span><span class="sxs-lookup"><span data-stu-id="ad401-211">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="ad401-212">导航 Windows Mixed Reality 主页</span><span class="sxs-lookup"><span data-stu-id="ad401-212">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
