---
title: 手动指导
description: 当系统未检测到用户的手以帮助提供帮助时，将触发3D 指针。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality，设计，手型指导，沉浸式耳机，MRTK，双手，帮助
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345658"
---
# <a name="hand-coach"></a><span data-ttu-id="5b7ba-104">手动指导</span><span class="sxs-lookup"><span data-stu-id="5b7ba-104">Hand coach</span></span>
![示例：手型指导](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="5b7ba-106">手动指导是指在系统未检测到用户的手时触发的三维建模手。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-106">Hand coach is 3D modeled hands that are triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="5b7ba-107">这是作为 "教学" 组件实现的，该组件可帮助引导用户在未教授手势时进行引导。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-107">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="5b7ba-108">如果用户未在某个时间段内完成指定的手势，则会循环一段时间。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-108">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="5b7ba-109">手型指导可用于表示按下按钮或选取全息图标。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="5b7ba-110">手写指导</span><span class="sxs-lookup"><span data-stu-id="5b7ba-110">Hand coach provided</span></span>

<span data-ttu-id="5b7ba-111">当前交互模型表示各种手势控件，例如滚动、远选和点击显示。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="5b7ba-112">下面是<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets">MRTK</a>中提供的现有手型手势的完整列表：</span><span class="sxs-lookup"><span data-stu-id="5b7ba-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="5b7ba-113">![接近选择的示例](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="5b7ba-114">**接近选择使用的示例显示如何选择按钮或关闭种不可交互对象**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5b7ba-115">![空中点击的示例](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="5b7ba-116">**空中点击的示例-用于显示如何选择远距离的对象**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5b7ba-117">![移动示例](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="5b7ba-118">**将对象移动到空间的示例-用于显示如何在空间中移动全息图**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5b7ba-119">![旋转示例](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="5b7ba-120">**旋转示例-用于演示如何旋转全息影像或对象**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="5b7ba-121">![缩放示例](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="5b7ba-122">**缩放示例-用于显示如何操作更大或更小的全息影像**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5b7ba-123">![手掌的示例](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="5b7ba-124">**掌上-建议使用的示例，用于引入手菜单**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5b7ba-125">![HandFlip 的示例](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="5b7ba-126">**示例-用于打开手形菜单的另一种方式**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5b7ba-127">![滚动示例](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="5b7ba-128">**滚动示例–用于滚动列表或长文档**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="5b7ba-129">设计概念</span><span class="sxs-lookup"><span data-stu-id="5b7ba-129">Design concepts</span></span>

<span data-ttu-id="5b7ba-130">对于 Hololens2，我们基于 instinctual 和自然手势设计出了手动交互。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="5b7ba-131">我们相信它们对于大多数用户来说是直观的，因此不会创建专用的手势学习时间。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-131">We believe these to be intuitive to most users and thus did not create dedicated gesture learning moments.</span></span> <span data-ttu-id="5b7ba-132">相反，我们创建了一本手形指导，帮助可能遇到的问题，或者不熟悉与全息影像交互的用户了解这些手势。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-132">Instead, we created the hand coach to help users who might get stuck or are unfamiliar with interacting with holograms learn about these gestures.</span></span> <span data-ttu-id="5b7ba-133">如果没有学习，我们认为向用户展示如何执行操作，这是最佳选择。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="5b7ba-134">在我们的研究中，我们发现用户能够找出手势，但需要一些指导。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-134">In our studies, we found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="5b7ba-135">如果检测到某个用户在某个时间段内没有与某个对象进行交互，则会触发一则手指导，说明正确的抓手和手指位置。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-135">If we detect that a user does not interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="5b7ba-136">直观</span><span class="sxs-lookup"><span data-stu-id="5b7ba-136">Intuitive</span></span>

<span data-ttu-id="5b7ba-137">动画处理时，应该很明显，shoudn't 会造成混淆。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-137">When animating hands, it should be obvious and shoudn't cause any confusion.</span></span> <span data-ttu-id="5b7ba-138">指针的动画是您尝试调用它用户了解其用途的手势的表示形式。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-138">The animation of the hands is a representation of the gesture your trying to evoke to the user to understand it's purpose.</span></span> 

<span data-ttu-id="5b7ba-139">例如，如果希望用户按下某个按钮，则会触发按下按钮的一只手。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="5b7ba-140">![示例：点击点击](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="5b7ba-141">*演示附近点击 Gem 的指导*</span><span class="sxs-lookup"><span data-stu-id="5b7ba-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="5b7ba-142">手动缩放</span><span class="sxs-lookup"><span data-stu-id="5b7ba-142">Hand scale</span></span>

<span data-ttu-id="5b7ba-143">我们使用 UI 菜单测试了各种手大小，并感觉到，如果想要调整其大小，就会发现 menacing，但如果它们太小，则很难看到和理解手势。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling but if they were too small then it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="5b7ba-144">**语音和手**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-144">**Voice over and hands**</span></span>

<span data-ttu-id="5b7ba-145">不要指望用户可以通过语音来侦听一组说明，并通过手动指导观看不同说明。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-145">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="5b7ba-146">序列化说明，帮助用户专注于争用，从而减少传感器的过载。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-146">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="5b7ba-147">我能创建自己的吗？</span><span class="sxs-lookup"><span data-stu-id="5b7ba-147">Can I create my own?</span></span>

<span data-ttu-id="5b7ba-148">能！</span><span class="sxs-lookup"><span data-stu-id="5b7ba-148">Yes!</span></span> <span data-ttu-id="5b7ba-149">我们鼓励你为游戏创建自己的独特手势，并向社区提供反馈！</span><span class="sxs-lookup"><span data-stu-id="5b7ba-149">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="5b7ba-150">我们提供了可用于你的应用的 Maya 文件 Rigged，可在此处下载<a href="files/HandCoach_MRTK.zip">HandCoach_MRTK.zip</a></span><span class="sxs-lookup"><span data-stu-id="5b7ba-150">We have provided a Maya file of a Rigged hand that can be used for your app which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip</a></span></span>

<span data-ttu-id="5b7ba-151">![在 Maya 中进行动画处理的示例](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-151">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="5b7ba-152">*Maya 中闲逛的动画手形的示例*</span><span class="sxs-lookup"><span data-stu-id="5b7ba-152">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="5b7ba-153">**推荐的创作工具**</span><span class="sxs-lookup"><span data-stu-id="5b7ba-153">**Recommended authoring tool**</span></span>

<span data-ttu-id="5b7ba-154">在三维音乐家之间，很多选择使用[Autodesk 的 Maya，它本身能够使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)来转换资产的创建方式。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-154">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="5b7ba-155">提供的免提文件是一个 Maya 二进制文件，因此建议使用 Maya 来动画和导出手。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-155">The hands file provided is a Maya Binary File, so it is recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="5b7ba-156">如果希望使用其他三维程序，请单击此处<b>。FBX</b>：<a href="files/HandCoachMRTK_FBX.zip">下载 HandCoachMRTK_FBX.zip</a>来创建自己的控制器设置。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-156">If you prefer to use another 3D program, here is a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">           Download HandCoachMRTK_FBX.zip</a> to create your own controller setup.</span></span> 

<span data-ttu-id="5b7ba-157">如果使用提供的可下载 maya 手型文件，则建议将 unity 向下扩展到0.6。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-157">If using the downloadable maya Hand File provided, it is suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="5b7ba-158">![示例： Maya 中的手型指导远程测试机组](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-158">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="5b7ba-159">*Rigged*</span><span class="sxs-lookup"><span data-stu-id="5b7ba-159">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="5b7ba-160">技术规格</span><span class="sxs-lookup"><span data-stu-id="5b7ba-160">Technical Specs</span></span>

*   <span data-ttu-id="5b7ba-161">Maya Ascii 格式提供两个文件</span><span class="sxs-lookup"><span data-stu-id="5b7ba-161">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="5b7ba-162">Right 和左手提供 Maya 二进制格式</span><span class="sxs-lookup"><span data-stu-id="5b7ba-162">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="5b7ba-163">将 Maya 文件设置为 24 FPS</span><span class="sxs-lookup"><span data-stu-id="5b7ba-163">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="5b7ba-164">在该文件中，有一个左手的右手，可用于两个右手或单直接手势。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-164">Within the file, there is a left and right hand which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="5b7ba-165">仅在默认情况下，才会显示右手。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-165">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="5b7ba-166">建议在淡化的开头和结尾留出大约10帧的缓冲区</span><span class="sxs-lookup"><span data-stu-id="5b7ba-166">It is suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="5b7ba-167">如果对具有指定目标的对象进行动画处理，则其最佳方案为动态到默认框或 Null。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-167">If animating a object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="5b7ba-168">如果要对物理对象（例如 box）进行动画处理，最佳做法是不在 Maya 中对转换进行动画处理，而是等待在 Unity 中或代码中对其进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-168">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="5b7ba-169">对于要传达的任何有意义的信息，可见动画应为1.5 秒</span><span class="sxs-lookup"><span data-stu-id="5b7ba-169">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="5b7ba-170">如果你对动画感到满意：</span><span class="sxs-lookup"><span data-stu-id="5b7ba-170">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="5b7ba-171">选择所有接头和制作关键帧</span><span class="sxs-lookup"><span data-stu-id="5b7ba-171">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="5b7ba-172">删除控制器，选择接头和网格，并将其导出为 FBX</span><span class="sxs-lookup"><span data-stu-id="5b7ba-172">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="5b7ba-173">如果有多个动画，可以使用 Maya 的内置游戏导出程序：https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="5b7ba-173">If there are Multiple Animations, you can use Maya’s built in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="5b7ba-174">从 Maya 导出</span><span class="sxs-lookup"><span data-stu-id="5b7ba-174">Exporting from Maya</span></span>

<span data-ttu-id="5b7ba-175">对动画满意后</span><span class="sxs-lookup"><span data-stu-id="5b7ba-175">After you are satisfied with your animation</span></span>
* <span data-ttu-id="5b7ba-176">选择所有接头：选择 > 层次结构</span><span class="sxs-lookup"><span data-stu-id="5b7ba-176">Select all joints: Select > Hierarchy</span></span>

     ![示例：菜单位置](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="5b7ba-178">制作动画：切换到动画 > 键 > 制作动画</span><span class="sxs-lookup"><span data-stu-id="5b7ba-178">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![示例：菜单位置](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="5b7ba-180">删除控制器远程测试机组： Outliner > MainR_Grp 或 MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="5b7ba-180">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![示例：菜单位置](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="5b7ba-182">导出为 FBX：选择 .JNT + 网格： File > 导出选定内容（选项框） > 导出选定内容</span><span class="sxs-lookup"><span data-stu-id="5b7ba-182">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![示例：菜单位置](images/HandCoach/OptionBox.png)<br>

     ![示例：菜单位置](images/HandCoach/SelectionExport.png)<br>

     ![示例：菜单位置](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="5b7ba-186">导出为 FBX 并将其放入 Unity 时，将指针向下缩放到0.6。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-186">When exporting as a FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="5b7ba-187">我们发现这非常适合显示手。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-187">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="5b7ba-188">![示例： Unity 设置](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="5b7ba-188">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="5b7ba-189">*在 MRTK 中找到 HandCoach_R prefab 的 Unity 设置*</span><span class="sxs-lookup"><span data-stu-id="5b7ba-189">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="5b7ba-190">实现对 Unity 项目的动手</span><span class="sxs-lookup"><span data-stu-id="5b7ba-190">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="5b7ba-191">最佳实践</span><span class="sxs-lookup"><span data-stu-id="5b7ba-191">Best practices</span></span>
*    <span data-ttu-id="5b7ba-192">建议将 unity 向下扩展到0。6</span><span class="sxs-lookup"><span data-stu-id="5b7ba-192">It is suggested to scale down the hands in unity to 0.6</span></span>
*   <span data-ttu-id="5b7ba-193">应播放两次，如果未完成，则连续循环，直到手势完成。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-193">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="5b7ba-194">应循环访问两次，以确保用户有时间注册并查看手势。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-194">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="5b7ba-195">指针应在循环之间淡入和淡出。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-195">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="5b7ba-196">如果用户的手在 HL2 摄像头中可见，但用户并未执行所需的交互操作，则会在10秒后出现。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-196">If user’s hands are visible by HL2 cameras but users are not doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="5b7ba-197">如果 HL2 照相机看不到用户的手，则会在5秒后出现指针。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-197">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="5b7ba-198">如果动画中间的 HL2 相机明显跟踪用户的手，动画将完成并淡出。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-198">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="5b7ba-199">如果要包括语音，则建议将其对应于手的手势。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-199">If you are including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="5b7ba-200">如果你至少已经教授了一次，只需在其检测到用户停滞的情况下重复该笔势。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-200">If you have taught the hands at least once, only repeat the gesture if its detected that the user is stuck.</span></span>
*   <span data-ttu-id="5b7ba-201">如果特定的 finger 位置是关键的，请确保用户可以清楚地查看动画中的这些差异。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-201">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="5b7ba-202">尝试右倾，以清楚地显示最重要的部分。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-202">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="5b7ba-203">如果你注意到了手上的扭曲，则需要转为 Unity 的质量设置来增加骨骼量。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-203">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the amount of bones.</span></span> 
 <span data-ttu-id="5b7ba-204">请参阅 Unity 的编辑 > 项目设置 > Quality > 其他 > Blend 权重。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-204">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="5b7ba-205">请确保选择 "4 骨骼" 以查看平滑联接。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-205">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![示例：菜单位置](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a><span data-ttu-id="5b7ba-207">要避免的内容</span><span class="sxs-lookup"><span data-stu-id="5b7ba-207">What to avoid</span></span>
* <span data-ttu-id="5b7ba-208">将指针放大太大</span><span class="sxs-lookup"><span data-stu-id="5b7ba-208">Scaling the Hands too large</span></span>
* <span data-ttu-id="5b7ba-209">将指针放在靠近用户的附近</span><span class="sxs-lookup"><span data-stu-id="5b7ba-209">placing the Hands too close to the user</span></span>
* <span data-ttu-id="5b7ba-210">只需教授一次。</span><span class="sxs-lookup"><span data-stu-id="5b7ba-210">Hands should only be taught once.</span></span> <span data-ttu-id="5b7ba-211">优于教授会导致混淆和麻烦</span><span class="sxs-lookup"><span data-stu-id="5b7ba-211">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="5b7ba-212">将它引入 Unity，请在此处下载最新的 MRTK：https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="5b7ba-212">Bringing it into Unity, please download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="5b7ba-213">材料： Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="5b7ba-213">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="5b7ba-214">脚本：请参阅<a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">MRTK 手型指导</a>的 MRTK 准则</span><span class="sxs-lookup"><span data-stu-id="5b7ba-214">Scripts: Refer to MRTK guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="5b7ba-215">每项目设置</span><span class="sxs-lookup"><span data-stu-id="5b7ba-215">Per- project setting</span></span>
        *   <span data-ttu-id="5b7ba-216">场景设置为 UWP：可在[配置 Unity 项目](Configure-Unity-Project.md)中找到 Windows Mixed Reality 的说明</span><span class="sxs-lookup"><span data-stu-id="5b7ba-216">Scene set to UWP: Instruction can be found on the [Configure Unity Project](Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="5b7ba-217">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b7ba-217">See also</span></span>
* [<span data-ttu-id="5b7ba-218">交互-基础</span><span class="sxs-lookup"><span data-stu-id="5b7ba-218">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="5b7ba-219">资产创建过程</span><span class="sxs-lookup"><span data-stu-id="5b7ba-219">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="5b7ba-220">笔势</span><span class="sxs-lookup"><span data-stu-id="5b7ba-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="5b7ba-221">安装工具</span><span class="sxs-lookup"><span data-stu-id="5b7ba-221">Install the Tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="5b7ba-222">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="5b7ba-222">Configure Unity Project</span></span>](Configure-Unity-Project.md)
* [<span data-ttu-id="5b7ba-223">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="5b7ba-223">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="5b7ba-224">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="5b7ba-224">MRTK 101</span></span>](mrtk-101.md)
