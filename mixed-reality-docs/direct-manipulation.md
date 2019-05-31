---
title: 使用手直接操作
description: 直接操作输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实、 提供注视、 面向交互的视线移动设计，附近，手 HoloLens
ms.openlocfilehash: 6e3512eab4070680c48ee8e95240a17e9925822f
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402395"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="108d7-104">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="108d7-104">Direct manipulation with hands</span></span>
<span data-ttu-id="108d7-105">直接操作是一个输入的模型，包括触摸全息直接与您的手。</span><span class="sxs-lookup"><span data-stu-id="108d7-105">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="108d7-106">直接操作的目标是，对象的行为就像在现实生活中。</span><span class="sxs-lookup"><span data-stu-id="108d7-106">The goal with direct manipulation is that objects behave just as they do in the real world.</span></span> <span data-ttu-id="108d7-107">可以只需通过按其激活按钮、 对象可以捕获它们，选取和 2D 内容的行为类似于虚拟触摸屏。</span><span class="sxs-lookup"><span data-stu-id="108d7-107">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span>  <span data-ttu-id="108d7-108">因此，直接操作是方便用户了解，，并在它太的乐趣。</span><span class="sxs-lookup"><span data-stu-id="108d7-108">Because of this, direct manipulation is easy for users to learn, and it's fun too.</span></span>  <span data-ttu-id="108d7-109">它被视为"附近的"输入的模型，这意味着它最适用于与 arm 内达到了的内容进行交互。</span><span class="sxs-lookup"><span data-stu-id="108d7-109">It is considered a "near" input model, meaning it is best used for interacting with content that is within arms reach.</span></span>

<span data-ttu-id="108d7-110">直接操作是基于可见的这意味着用户友好。</span><span class="sxs-lookup"><span data-stu-id="108d7-110">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="108d7-111">没有符号的手势，教用户。</span><span class="sxs-lookup"><span data-stu-id="108d7-111">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="108d7-112">围绕可以接触或获取一个可见元素而构建的所有交互。</span><span class="sxs-lookup"><span data-stu-id="108d7-112">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="108d7-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="108d7-113">Device support</span></span>


| <span data-ttu-id="108d7-114">输入的模型</span><span class="sxs-lookup"><span data-stu-id="108d7-114">Input Model</span></span> | [<span data-ttu-id="108d7-115">HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="108d7-115">HoloLens (1st gen)</span></span>](hololens-hardware-details.md) | <span data-ttu-id="108d7-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="108d7-116">HoloLens 2</span></span> |[<span data-ttu-id="108d7-117">沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="108d7-117">Immersive headsets</span></span>](immersive-headset-hardware-details.md)|
|:-------- | :-------| :--------| :------------|
| <span data-ttu-id="108d7-118">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="108d7-118">Direct manipulation with hands</span></span> | <span data-ttu-id="108d7-119">不支持的 ❌</span><span class="sxs-lookup"><span data-stu-id="108d7-119">❌ Not supported</span></span> | <span data-ttu-id="108d7-120">✔️ 建议</span><span class="sxs-lookup"><span data-stu-id="108d7-120">✔️ Recommended</span></span> | <span data-ttu-id="108d7-121">一个替代方法，➕[点，并提交，并手](point-and-commit.md)建议。</span><span class="sxs-lookup"><span data-stu-id="108d7-121">➕ An alternative, [point and commit with hands](point-and-commit.md) is recommended.</span></span>

<span data-ttu-id="108d7-122">直接操作是 HoloLens 2 上的主输入的模型，并利用新的明确的手动跟踪系统。</span><span class="sxs-lookup"><span data-stu-id="108d7-122">Direct manipulation is a primary input model on HoloLens 2, and utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="108d7-123">输入的模型，还可以在通过动作控制器使用的沉浸式耳机，但不是建议为外部对象操作的交互的主要方式。</span><span class="sxs-lookup"><span data-stu-id="108d7-123">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span>  <span data-ttu-id="108d7-124">直接 manipluation 上不可用 HoloLens （第 1 代）。</span><span class="sxs-lookup"><span data-stu-id="108d7-124">Direct manipluation is not available on HoloLens (1st gen).</span></span>


## <a name="collidable-fingertip"></a><span data-ttu-id="108d7-125">Collidable 指尖</span><span class="sxs-lookup"><span data-stu-id="108d7-125">Collidable fingertip</span></span>

<span data-ttu-id="108d7-126">HoloLens 2 上用户的实际动手识别和被解释为左侧和右侧框架模型。</span><span class="sxs-lookup"><span data-stu-id="108d7-126">On HoloLens 2, the user's real hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="108d7-127">若要实现的触摸直接与手全息想法，理想情况下，5 碰撞体可以附加到 5 轻松获得相关的每个现有框架模型。</span><span class="sxs-lookup"><span data-stu-id="108d7-127">To implement the idea of touching holograms directly with hands, ideally, 5 colliders could be attached to 5 fingertips of each hand skeletal model.</span></span> <span data-ttu-id="108d7-128">但是，实际上，由于缺少触觉反馈，10 collidable 轻松访问引起的意外的且不可预测的冲突与全息。</span><span class="sxs-lookup"><span data-stu-id="108d7-128">However, practically, due to the lack of tactile feedback, 10 collidable fingertips caused unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="108d7-129">因此，我们建议仅在每个索引手指将碰撞体。</span><span class="sxs-lookup"><span data-stu-id="108d7-129">Hence, we suggest to only put a collider on each index finger.</span></span> <span data-ttu-id="108d7-130">Collidable 索引都可以看到可以仍作为涉及其他手指，如 1 手指按、 1 指点击，2 手指按和 5 手指按不同的触摸手势的活动触摸点，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="108d7-130">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as 1-finger press, 1-finger tap, 2-finger press and 5-finger press, as shown in the image below.</span></span>

![Collidable 指尖图像](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a><span data-ttu-id="108d7-132">球体碰撞体</span><span class="sxs-lookup"><span data-stu-id="108d7-132">Sphere collider</span></span>

<span data-ttu-id="108d7-133">而不是使用随机的一般形状，我们建议使用球体碰撞体，并以可视方式呈现它接近目标提供更好的提示。</span><span class="sxs-lookup"><span data-stu-id="108d7-133">Instead of using a random generic shape, we suggest to use a sphere collider and to visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="108d7-134">球的直径应匹配索引指以增加触摸的准确性的粗细。</span><span class="sxs-lookup"><span data-stu-id="108d7-134">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="108d7-135">它将很容易通过调用手 API 检索手指粗细的变量。</span><span class="sxs-lookup"><span data-stu-id="108d7-135">It will be easy to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="108d7-136">指尖游标</span><span class="sxs-lookup"><span data-stu-id="108d7-136">Fingertip cursor</span></span>

<span data-ttu-id="108d7-137">除了呈现 collidable 球体上索引指尖，我们创建了一个高级的解决方案，指尖游标，若要以交互方式实现更好的附近目标体验。</span><span class="sxs-lookup"><span data-stu-id="108d7-137">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced solution, fingertip cursor, to achieve better near-targeting experience interactively.</span></span> <span data-ttu-id="108d7-138">它是附加在索引指尖环形游标。</span><span class="sxs-lookup"><span data-stu-id="108d7-138">It is a donut-shaped cursor attached on the index fingertip.</span></span> <span data-ttu-id="108d7-139">根据邻近，动态的互动方式到的目标方向和大小，详情如下方面：</span><span class="sxs-lookup"><span data-stu-id="108d7-139">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="108d7-140">当索引手指移动到一张全息图时，游标始终是并行到全息图的图面，逐渐会相应地缩小其大小。</span><span class="sxs-lookup"><span data-stu-id="108d7-140">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface  and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="108d7-141">只要上方的手指触摸表面，光标缩小到一个点，并发出一个触摸事件。</span><span class="sxs-lookup"><span data-stu-id="108d7-141">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="108d7-142">借助交互式的反馈，用户可以实现近乎导向目标任务，例如触发的 web 内容上的超链接或按下按钮，如下所示的高精度。</span><span class="sxs-lookup"><span data-stu-id="108d7-142">With the interactive feedback, users can achieve high precision near targeting tasks, such as triggering a hyperlink on web content or pressing a button, as shown, below.</span></span> 

![指尖光标图像](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="108d7-144">边界框与邻近着色器</span><span class="sxs-lookup"><span data-stu-id="108d7-144">Bounding box with proximity shader</span></span>

<span data-ttu-id="108d7-145">全息图本身还需要提供视频和音频反馈以补偿触觉反馈缺乏的能力。</span><span class="sxs-lookup"><span data-stu-id="108d7-145">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="108d7-146">为此，我们使用邻近着色器生成的边界框的概念。</span><span class="sxs-lookup"><span data-stu-id="108d7-146">For that, we generate the concept of a bounding box with proximity shader.</span></span> <span data-ttu-id="108d7-147">边界框是包含一个三维对象的最小容量耗尽区域。</span><span class="sxs-lookup"><span data-stu-id="108d7-147">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="108d7-148">边界框提供了名为邻近着色器的交互式呈现机制。</span><span class="sxs-lookup"><span data-stu-id="108d7-148">The bounding box has an interactive rendering mechanism called proximity shader.</span></span> <span data-ttu-id="108d7-149">邻近着色器的行为：</span><span class="sxs-lookup"><span data-stu-id="108d7-149">The proximity shader behaves:</span></span>

* <span data-ttu-id="108d7-150">当索引手指范围内时，指尖聚焦被强制转换的边界框面上。</span><span class="sxs-lookup"><span data-stu-id="108d7-150">When the index finger is within a range, a fingertip spotlight is cast on the surface of bounding box.</span></span>
* <span data-ttu-id="108d7-151">时指尖更接近于图面，则会相应地将聚焦。</span><span class="sxs-lookup"><span data-stu-id="108d7-151">When the fingertip gets closer to the surface, the spotlight condenses accordingly.</span></span>
* <span data-ttu-id="108d7-152">只要指尖 touch 面，边界框的整个更改颜色，或者生成视觉效果以反映触摸状态。</span><span class="sxs-lookup"><span data-stu-id="108d7-152">As soon as the fingertip touch the surface, the whole bounding box changes the color or generate visual effect to reflect the touch state.</span></span>
* <span data-ttu-id="108d7-153">同时，可以激活声音效果来增强 visual 触摸反馈。</span><span class="sxs-lookup"><span data-stu-id="108d7-153">Meanwhile, a sound effect can be activated to enhance the visual touch feedback.</span></span>

![边界框与邻近着色器图像](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a><span data-ttu-id="108d7-155">Pressable 按钮</span><span class="sxs-lookup"><span data-stu-id="108d7-155">Pressable button</span></span>

<span data-ttu-id="108d7-156">用 collidable 指尖，用户现已准备好的非常基本 holographic UI 组件，pressable 按钮进行交互。</span><span class="sxs-lookup"><span data-stu-id="108d7-156">With a collidable fingertip, users are now ready to interact with the very fundamental holographic UI component, pressable button.</span></span> <span data-ttu-id="108d7-157">Pressable 按钮是为直接手指按量身打造的 holographic 按钮。</span><span class="sxs-lookup"><span data-stu-id="108d7-157">A pressable button is a holographic button tailored for direct finger press.</span></span> <span data-ttu-id="108d7-158">同样，由于触觉反馈缺乏 pressable 按钮提供一些机制来解决触觉反馈相关的问题。</span><span class="sxs-lookup"><span data-stu-id="108d7-158">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="108d7-159">第一种机制是边界框与邻近着色器，在上一部分中详细介绍。</span><span class="sxs-lookup"><span data-stu-id="108d7-159">The first mechanism is a bounding box with proximity shader, detailed in the previous section.</span></span> <span data-ttu-id="108d7-160">它可用于提供更好地为用户方法，使邻近按钮联系。</span><span class="sxs-lookup"><span data-stu-id="108d7-160">It serves to provide better sense of proximity for users to approach and make contact with a button.</span></span>
* <span data-ttu-id="108d7-161">第二个是困扰。</span><span class="sxs-lookup"><span data-stu-id="108d7-161">The second one is depression.</span></span> <span data-ttu-id="108d7-162">它将创建有意义的 press 后指尖联系按钮。</span><span class="sxs-lookup"><span data-stu-id="108d7-162">It creates sense of press, after a fingertip contacts the button.</span></span> <span data-ttu-id="108d7-163">机制是按钮紧密与指尖深度轴一起移动。</span><span class="sxs-lookup"><span data-stu-id="108d7-163">The mechanism is that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="108d7-164">在达到指定的深度 （按下时） 或通过它传递后使 （在发布） 的深度时，可以触发按钮。</span><span class="sxs-lookup"><span data-stu-id="108d7-164">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="108d7-165">应添加声音效果来增强的反馈，当触发按钮。</span><span class="sxs-lookup"><span data-stu-id="108d7-165">The sound effect should be added to enhance feedback, when the button is triggered.</span></span>

![Pressable 按钮图像](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="108d7-167">2D 盖板交互</span><span class="sxs-lookup"><span data-stu-id="108d7-167">2D slate interaction</span></span>

<span data-ttu-id="108d7-168">2D 盖板是 holographic 容器托管 2D 应用内容，如 web 浏览器。</span><span class="sxs-lookup"><span data-stu-id="108d7-168">A 2D slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="108d7-169">用来与通过直接操作 2D 平板式交互设计概念是利用与物理触摸屏进行交互的心理模型。</span><span class="sxs-lookup"><span data-stu-id="108d7-169">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

<span data-ttu-id="108d7-170">若要与盖板联系人进行交互：</span><span class="sxs-lookup"><span data-stu-id="108d7-170">To interact with the slate contact:</span></span>

* <span data-ttu-id="108d7-171">使用索引手指按超链接或按钮。</span><span class="sxs-lookup"><span data-stu-id="108d7-171">Use an index finger to press a hyperlink or a button.</span></span>
* <span data-ttu-id="108d7-172">使用索引手指来滚动静态内容向上和向下。</span><span class="sxs-lookup"><span data-stu-id="108d7-172">Use an index finger to scroll a slate content up and down.</span></span>
* <span data-ttu-id="108d7-173">用户使用两个索引根手指放大 in 和 out 根据相对的根手指的动作的静态内容。</span><span class="sxs-lookup"><span data-stu-id="108d7-173">Users use two index fingers to zoom in and out the slate content according to relative motion of fingers.</span></span>

![2D 盖板图像](images/2D-Slate-Interaction-720px.jpg)

<span data-ttu-id="108d7-175">用于操作 2D 平板本身：</span><span class="sxs-lookup"><span data-stu-id="108d7-175">For manipulating the 2D slate itself:</span></span>

* <span data-ttu-id="108d7-176">方法将双手边角和边缘，以显示最接近的操作等方面。</span><span class="sxs-lookup"><span data-stu-id="108d7-176">Approach your hands toward corners and edges to reveal the closest manipulation affordances.</span></span>
* <span data-ttu-id="108d7-177">获取操作等和执行通过角等统一缩放和重排通过边缘等。</span><span class="sxs-lookup"><span data-stu-id="108d7-177">Grab the manipulation affordances, and perform uniform scaling through the corner affordances and reflow via the edge affordances.</span></span>
* <span data-ttu-id="108d7-178">获取二维显示静态图像，使你迁移整个盖板顶部 holobar。</span><span class="sxs-lookup"><span data-stu-id="108d7-178">Grab the holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>

![盖板操作的图像](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a><span data-ttu-id="108d7-180">三维对象操作</span><span class="sxs-lookup"><span data-stu-id="108d7-180">3D object manipulation</span></span>

<span data-ttu-id="108d7-181">HoloLens 2，的允许用户启用其只手来直接操作通过应用于每个三维对象的边界框三维 hologramphic 对象。</span><span class="sxs-lookup"><span data-stu-id="108d7-181">HoloLens 2 lets lets users enable their hands to direct manipulate 3D hologramphic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="108d7-182">边界框提供了更好地通过其邻近着色器的深度感知。</span><span class="sxs-lookup"><span data-stu-id="108d7-182">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="108d7-183">与边界框中，有两种设计方法，以便 3D 对象进行操作。</span><span class="sxs-lookup"><span data-stu-id="108d7-183">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="108d7-184">基于功能可见性： 的操作</span><span class="sxs-lookup"><span data-stu-id="108d7-184">Affordance-based manipulation</span></span>

<span data-ttu-id="108d7-185">这允许您操作三维对象通过边界框和在其周围操作等。</span><span class="sxs-lookup"><span data-stu-id="108d7-185">This lets you manipulate the 3D object through a bounding box and the manipulation affordances around it.</span></span> <span data-ttu-id="108d7-186">只要用户的手即将于一个三维对象，边界框和接近功能可见性： 将揭示出理解。</span><span class="sxs-lookup"><span data-stu-id="108d7-186">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="108d7-187">用户可以获取要移动的整个对象、 边缘等旋转和角等均匀缩放的边界框。</span><span class="sxs-lookup"><span data-stu-id="108d7-187">Users can grab the bounding box to move the whole object, the edge affordances to rotate and the corner affordances to scale uniformly.</span></span>

![三维对象操作图像](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="108d7-189">非功能可见性： 基于操作</span><span class="sxs-lookup"><span data-stu-id="108d7-189">Non-affordance based manipulation</span></span>

<span data-ttu-id="108d7-190">在此机制中，没有功能可见性： 附加到的边界框。</span><span class="sxs-lookup"><span data-stu-id="108d7-190">In this mechanism, no affordance is attached to the bounding box.</span></span> <span data-ttu-id="108d7-191">用户可以仅显示边界框，然后直接与之交互。</span><span class="sxs-lookup"><span data-stu-id="108d7-191">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="108d7-192">如果用一只手获取边界框，平移和旋转的对象将关联到动作和方向的分值。</span><span class="sxs-lookup"><span data-stu-id="108d7-192">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="108d7-193">当对象获取与两只手中时，用户可以转换、 缩放和旋转根据相对两只手的动作。</span><span class="sxs-lookup"><span data-stu-id="108d7-193">When the object is grabbed with two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="108d7-194">执行特定操作要求精度，我们建议你使用**功能可见性： 基于操作**，因为它提供高级别的粒度。</span><span class="sxs-lookup"><span data-stu-id="108d7-194">Specific manipulation requires precision, we recommend you use **affordance-based manipulation**, because it provides a high level of granularity.</span></span> <span data-ttu-id="108d7-195">灵活操作时，我们建议你使用**非功能可见性： 操作**是因为这样可以即时和氛围体验。</span><span class="sxs-lookup"><span data-stu-id="108d7-195">For flexible manipulation, we recommend you uses **non-affordance manipulation** is as it allows for instant and playful experiences.</span></span>

## <a name="instinctual-gestures"></a><span data-ttu-id="108d7-196">Instinctual 手势</span><span class="sxs-lookup"><span data-stu-id="108d7-196">Instinctual gestures</span></span>

<span data-ttu-id="108d7-197">与 HoloLens （第 1 代），我们教用户布隆和空气点击等几个预定义的笔势。</span><span class="sxs-lookup"><span data-stu-id="108d7-197">With HoloLens (1st gen), we taught users a couple predefined gestures,such as Bloom and Air Tap.</span></span> <span data-ttu-id="108d7-198">对于 HoloLens 2，我们不要求用户记住任何符号的手势。</span><span class="sxs-lookup"><span data-stu-id="108d7-198">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="108d7-199">Instinctual 所有所需的用户笔势，用户需要与全息和内容，进行交互。</span><span class="sxs-lookup"><span data-stu-id="108d7-199">All required user gestures, users need to interact with holograms and contents, are instinctual.</span></span> <span data-ttu-id="108d7-200">要实现 instinctual 手势，方式是指导用户执行 UI 等的设计通过笔势。</span><span class="sxs-lookup"><span data-stu-id="108d7-200">The way to achieve instinctual gesture is to guide users to perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="108d7-201">例如，如果我们建议您对对象随取即行或使用双指挤压控点，该对象或控点应很小。</span><span class="sxs-lookup"><span data-stu-id="108d7-201">For example, if we encourage you to grab an object or a control point with two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="108d7-202">如果我们希望您能执行五个手指随取即行，该对象或控点应为相对较大。</span><span class="sxs-lookup"><span data-stu-id="108d7-202">If we want you to perform five finger grab, the object or the control point should be relatively big.</span></span> <span data-ttu-id="108d7-203">类似于按钮，小按钮会限制用户使用一根手指，按它，而大按钮鼓励用户使用其搁按。</span><span class="sxs-lookup"><span data-stu-id="108d7-203">Similar to buttons, a tiny button would limit users to press it with a single finger, while a huge button would encourage users to press it with their palms.</span></span>

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="108d7-204">双手和 6 DoF 控制器之间的对称设计</span><span class="sxs-lookup"><span data-stu-id="108d7-204">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="108d7-205">您可能已经注意到是现在我们可以得出手中 VR AR 和动作控制器之间的交互 parallels。</span><span class="sxs-lookup"><span data-stu-id="108d7-205">You may have noticed that there are now interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="108d7-206">这两个输入可用于触发相应的环境中的直接操作。</span><span class="sxs-lookup"><span data-stu-id="108d7-206">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="108d7-207">HoloLens 2 中获取和使用近距离中的工作原理在手拖动为随取即行按钮相同的方法类似于执行 WMR 中的动作控制器上。</span><span class="sxs-lookup"><span data-stu-id="108d7-207">In HoloLens 2, grabbing and dragging with hands at a close distance works much in the same way as the grab button does on the motion controllers in WMR.</span></span> <span data-ttu-id="108d7-208">这为用户提供了两个平台之间的交互熟悉程度，并可能会有用应决定移植到另一个您应用程序。</span><span class="sxs-lookup"><span data-stu-id="108d7-208">This provides users with interaction familiarity between the two platforms and may prove useful should you ever decide to port your app from one to the other.</span></span>

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="108d7-209">充分利用的眼跟踪与</span><span class="sxs-lookup"><span data-stu-id="108d7-209">Optimize with eye tracking</span></span>

<span data-ttu-id="108d7-210">如果它正常运行按预期运行，但也很快就如果您不能再移动您的手任意位置而不会无意中触发一张全息图，令人沮丧，直接操作可以感觉神奇。</span><span class="sxs-lookup"><span data-stu-id="108d7-210">Direct manipulation can feel magical if it works as intended, but can also quickly become frustrating if you can’t move your hand anywhere anymore without unintentionally triggering a hologram.</span></span>
<span data-ttu-id="108d7-211">眼睛追踪可能有助于更好地标识用户的意图。</span><span class="sxs-lookup"><span data-stu-id="108d7-211">Eye tracking can potentially help in better identifying what the user’s intent is.</span></span>

* <span data-ttu-id="108d7-212">**当**:减少错误地触发操作响应。</span><span class="sxs-lookup"><span data-stu-id="108d7-212">**When**: Reduce falsely triggering a manipulation response.</span></span> <span data-ttu-id="108d7-213">眼睛追踪允许更好地了解哪些用户当前参与。</span><span class="sxs-lookup"><span data-stu-id="108d7-213">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="108d7-214">例如，假设你正在阅读通过全息版的 （说明） 文本时达到超过获取实际工作的工具。</span><span class="sxs-lookup"><span data-stu-id="108d7-214">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="108d7-215">这样，您甚至没有之前 （甚至是外部用户的字段视野 (FOV) 可能） 将您注意到一些交互式 holographic 按钮跨意外移动您的手。</span><span class="sxs-lookup"><span data-stu-id="108d7-215">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (maybe it even was outside of the user's Field-of-View (FOV)).</span></span>

  <span data-ttu-id="108d7-216">长话短说：如果用户尚未探讨一张全息图一段时间，但它检测触摸或掌握现有的事件，则很可能用户实际上并不想要与该全息图进行交互。</span><span class="sxs-lookup"><span data-stu-id="108d7-216">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="108d7-217">**哪一个**:除了寻址 false 正激活，另一个示例包括更好地确定哪些全息抓取或仔细清除从你的观点可能会精确相交点，尤其是当多个全息位于接近每个其他。</span><span class="sxs-lookup"><span data-stu-id="108d7-217">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="108d7-218">HoloLens 2 上的眼跟踪具有某些限制如何准确地时它可以确定红眼的视线移动，这仍会非常有帮助的深度不一致会由于交互附近用输入一只手进行交互时。</span><span class="sxs-lookup"><span data-stu-id="108d7-218">While eye tracking on HoloLens 2 has a certain limitation on how accurately it can determine you eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span>  <span data-ttu-id="108d7-219">这意味着它是有时难以确定您的手是超前还是一张全息图，以准确地说例如获取操作小组件的前面。</span><span class="sxs-lookup"><span data-stu-id="108d7-219">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget for example.</span></span>

* <span data-ttu-id="108d7-220">**下一**:使用快速-引发手势查看哪些用户的使用信息。</span><span class="sxs-lookup"><span data-stu-id="108d7-220">**Where to**: Use information about what a user is looking at with quick- throwing gestures.</span></span> <span data-ttu-id="108d7-221">获取一张全息图，大致它将向你预期目标。</span><span class="sxs-lookup"><span data-stu-id="108d7-221">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="108d7-222">虽然这可能是有时正常、 快速执行手势的工作原理可能会导致在高度不准确的目标。</span><span class="sxs-lookup"><span data-stu-id="108d7-222">While this may sometimes works just fine, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="108d7-223">这是其中的眼跟踪可以帮助解决驱使手形图标到预期位置重新引发向量。</span><span class="sxs-lookup"><span data-stu-id="108d7-223">This is where eye tracking could help out to lean the hand throwing vector back to your intended position.</span></span>

## <a name="see-also"></a><span data-ttu-id="108d7-224">请参阅</span><span class="sxs-lookup"><span data-stu-id="108d7-224">See also</span></span>

* [<span data-ttu-id="108d7-225">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="108d7-225">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="108d7-226">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="108d7-226">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="108d7-227">本能交互</span><span class="sxs-lookup"><span data-stu-id="108d7-227">Instinctual interactions</span></span>](interaction-fundamentals.md)

