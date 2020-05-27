---
title: 凝视和提交
description: "\"注视并提交\" 输入模型的一般概述-使用目视或头输入。"
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合现实，注视，注视目标，交互，设计，眼睛跟踪，头跟踪
ms.openlocfilehash: c44c1a75e831869a3ed4d12bb6c9e87c478daf56
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866887"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="447d8-104">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="447d8-104">Gaze and commit</span></span>

<span data-ttu-id="447d8-105">"_注视" 和 "提交_" 是一种基本的输入模型，它与使用鼠标的计算机进行交互的方式密切相关：_点 & 单击_。</span><span class="sxs-lookup"><span data-stu-id="447d8-105">_Gaze and commit_ is a fundamental input model that is closely related with the way we're interacting with our computers using the mouse: _Point & click_.</span></span>
<span data-ttu-id="447d8-106">在此页上，我们将介绍两种类型的目视输入（打印头和眼睛眼睛）以及不同类型的提交操作。</span><span class="sxs-lookup"><span data-stu-id="447d8-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> 
<span data-ttu-id="447d8-107">_注视和提交_被视为具有间接操作的最大输入模型。</span><span class="sxs-lookup"><span data-stu-id="447d8-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span>
<span data-ttu-id="447d8-108">这意味着它最适用于与不在一起的全息内容交互。</span><span class="sxs-lookup"><span data-stu-id="447d8-108">This means it is best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="447d8-109">混合现实耳机可以使用用户头部的位置和方向来确定其头向量。</span><span class="sxs-lookup"><span data-stu-id="447d8-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="447d8-110">你可以将其视为从用户两眼之间直指前方的激光。</span><span class="sxs-lookup"><span data-stu-id="447d8-110">You can think of this as a laser that points straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="447d8-111">这可粗略呈现出用户正查看的位置。</span><span class="sxs-lookup"><span data-stu-id="447d8-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="447d8-112">您的应用程序可以将此射线与虚拟或现实对象交叉，并在该位置绘制光标，以使用户了解当前的目标。</span><span class="sxs-lookup"><span data-stu-id="447d8-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they are currently targeting.</span></span>

<span data-ttu-id="447d8-113">除了注视眼睛外，某些混合现实耳机（如 HoloLens 2）还包括可生成眼睛良好矢量的眼睛跟踪系统。</span><span class="sxs-lookup"><span data-stu-id="447d8-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="447d8-114">这可精细测量用户正在查看的位置。</span><span class="sxs-lookup"><span data-stu-id="447d8-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="447d8-115">在这两种情况下，注视都表示用户意向的重要信号。</span><span class="sxs-lookup"><span data-stu-id="447d8-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="447d8-116">系统更好地解释并预测用户的预期操作，提高用户满意度，提高性能。</span><span class="sxs-lookup"><span data-stu-id="447d8-116">The better the system can interpret and predict the user's intended actions, user satisfaction increases and performance improves.</span></span>

<span data-ttu-id="447d8-117">下面是一些示例，说明混合现实开发人员如何从打印头或眼睛中获益：</span><span class="sxs-lookup"><span data-stu-id="447d8-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="447d8-118">您的应用程序可以在场景中与全息影像交叉，以确定用户注意的位置（更准确地说看注视）。</span><span class="sxs-lookup"><span data-stu-id="447d8-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="447d8-119">您的应用程序可以根据用户的 "注视" 通道手势和控制器按下，使用户能够无缝选择、激活、抓取、滚动或与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="447d8-119">Your app can channel gestures and controller presses based on the user's gaze, letting the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="447d8-120">您的应用程序可让用户在实际的表面上放置全息影像，方法是将其表面与空间映射网格进行交叉处理。</span><span class="sxs-lookup"><span data-stu-id="447d8-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="447d8-121">您的应用程序可以知道用户*不*在查找重要对象的方向时，这可能会导致您的应用程序将视觉和音频提示转换为该对象。</span><span class="sxs-lookup"><span data-stu-id="447d8-121">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="447d8-122">设备支持</span><span class="sxs-lookup"><span data-stu-id="447d8-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="447d8-123"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="447d8-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="447d8-124"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="447d8-124"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="447d8-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="447d8-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="447d8-126"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="447d8-126"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="447d8-127">头部凝视和提交</span><span class="sxs-lookup"><span data-stu-id="447d8-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="447d8-128">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="447d8-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="447d8-129">✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</span><span class="sxs-lookup"><span data-stu-id="447d8-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="447d8-130">➕ 备用选项</span><span class="sxs-lookup"><span data-stu-id="447d8-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="447d8-131">眼睛凝视和提交</span><span class="sxs-lookup"><span data-stu-id="447d8-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="447d8-132">❌不可用</span><span class="sxs-lookup"><span data-stu-id="447d8-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="447d8-133">✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</span><span class="sxs-lookup"><span data-stu-id="447d8-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="447d8-134">❌不可用</span><span class="sxs-lookup"><span data-stu-id="447d8-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="447d8-135">凝视</span><span class="sxs-lookup"><span data-stu-id="447d8-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="447d8-136">眼后看好了吗？</span><span class="sxs-lookup"><span data-stu-id="447d8-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="447d8-137">当面对问题时，需要考虑几个注意事项，无论你使用的是 "眼睛和提交" 还是 "良好和提交" 输入模型。</span><span class="sxs-lookup"><span data-stu-id="447d8-137">There are several considerations to take into account when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="447d8-138">如果要开发沉浸式头戴式耳机或 HoloLens （第一代），则选择简单：打印头和提交。</span><span class="sxs-lookup"><span data-stu-id="447d8-138">If you're developing for an immersive headset or for HoloLens (1st gen) then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="447d8-139">如果你正在开发 HoloLens 2，则所做的选择会更难，因为了解其中每个选项的优点和难题非常重要。</span><span class="sxs-lookup"><span data-stu-id="447d8-139">If you're developing for HoloLens 2, the choice becomes a little harder which is why it's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="447d8-140">在下表中，我们编译了一些广泛的专业人员和职业，以对比眼睛和眼睛的目标。</span><span class="sxs-lookup"><span data-stu-id="447d8-140">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="447d8-141">这从很大程度上来看，我们建议在此处了解各种混合现实中的眼睛目标：</span><span class="sxs-lookup"><span data-stu-id="447d8-141">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="447d8-142">[Hololens 2 上的目视跟踪](eye-tracking.md)：在 hololens 2 上提供新的目视跟踪功能（包括一些开发人员指南）。</span><span class="sxs-lookup"><span data-stu-id="447d8-142">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="447d8-143">[目视的交互](eye-gaze-interaction.md)：计划使用目视跟踪作为输入时的设计注意事项和建议。</span><span class="sxs-lookup"><span data-stu-id="447d8-143">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="447d8-144"><strong>目视瞄准目标</strong></span><span class="sxs-lookup"><span data-stu-id="447d8-144"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="447d8-145"><strong>头部凝视目标设定</strong></span><span class="sxs-lookup"><span data-stu-id="447d8-145"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="447d8-146">Fast!</span><span class="sxs-lookup"><span data-stu-id="447d8-146">Fast!</span></span></td>
        <td><span data-ttu-id="447d8-147">比较</span><span class="sxs-lookup"><span data-stu-id="447d8-147">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="447d8-148">低工作量（几乎所有必要的主体移动）</span><span class="sxs-lookup"><span data-stu-id="447d8-148">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="447d8-149">可能是 fatiguing 的 discomfort （例如，颈部紧张）</span><span class="sxs-lookup"><span data-stu-id="447d8-149">Can be fatiguing - Possible discomfort (e.g., neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="447d8-150">不需要游标，但建议使用微妙的反馈</span><span class="sxs-lookup"><span data-stu-id="447d8-150">Does not require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="447d8-151">需要显示游标</span><span class="sxs-lookup"><span data-stu-id="447d8-151">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="447d8-152">无平滑的眼睛运动-例如，不适用于绘图</span><span class="sxs-lookup"><span data-stu-id="447d8-152">No smooth eye movements – e.g., not good for drawing</span></span></td>
        <td><span data-ttu-id="447d8-153">更多受控和显式</span><span class="sxs-lookup"><span data-stu-id="447d8-153">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="447d8-154">对于非常小的目标（例如，小按钮或 weblinks）很难</span><span class="sxs-lookup"><span data-stu-id="447d8-154">Difficult for very small targets (e.g., tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="447d8-155">非常!</span><span class="sxs-lookup"><span data-stu-id="447d8-155">Reliable!</span></span> <span data-ttu-id="447d8-156">好的回退！</span><span class="sxs-lookup"><span data-stu-id="447d8-156">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="447d8-157">...</span><span class="sxs-lookup"><span data-stu-id="447d8-157">...</span></span></td>
        <td><span data-ttu-id="447d8-158">...</span><span class="sxs-lookup"><span data-stu-id="447d8-158">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="447d8-159">无论你使用的是眼睛还是目视，你的眼睛和提交输入模型都附带了不同的设计约束集，这将在[眼睛眼睛和提交](gaze-and-commit-eyes.md)和[提交](gaze-and-commit-head.md)文章中单独介绍。</span><span class="sxs-lookup"><span data-stu-id="447d8-159">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model comes with different sets of design constraints, which will be covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="447d8-160">游标</span><span class="sxs-lookup"><span data-stu-id="447d8-160">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="447d8-161">对于 "注视"，大多数应用程序都应使用[游标](cursors.md)（或其他听觉/视觉指示）来让用户信任他们要与之交互的内容。</span><span class="sxs-lookup"><span data-stu-id="447d8-161">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="447d8-162">通常将此光标置于世界上，其中其打印头看起来先与一个对象（可能是全息图或真实表面）相交。</span><span class="sxs-lookup"><span data-stu-id="447d8-162">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="447d8-163">对于眼睛，我们通常建议*不要*显示游标，因为这可能会使用户迅速变得杂乱。</span><span class="sxs-lookup"><span data-stu-id="447d8-163">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="447d8-164">相反，突出强调视觉对象目标或使用非常模糊的光标，以使用户与之交互的对象更有把握。</span><span class="sxs-lookup"><span data-stu-id="447d8-164">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="447d8-165">有关详细信息，请查看有关 HoloLens 2 上[基于目视的输入的设计指南](eye-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="447d8-165">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="447d8-166">![用于显示注视的视觉对象示例](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="447d8-166">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="447d8-167">*图像：显示注视的视觉对象光标示例*</span><span class="sxs-lookup"><span data-stu-id="447d8-167">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="447d8-168">提交</span><span class="sxs-lookup"><span data-stu-id="447d8-168">Commit</span></span>
<span data-ttu-id="447d8-169">_在谈论看一看目标_的不同方法之后，让我们更深入地谈谈 "注视" 和 "_提交_" 中的_提交_部分。</span><span class="sxs-lookup"><span data-stu-id="447d8-169">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="447d8-170">以对象或 UI 元素为目标后，用户可以使用辅助输入交互或单击此元素。</span><span class="sxs-lookup"><span data-stu-id="447d8-170">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="447d8-171">这称为输入模型的提交步骤。</span><span class="sxs-lookup"><span data-stu-id="447d8-171">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="447d8-172">支持以下提交方法：</span><span class="sxs-lookup"><span data-stu-id="447d8-172">The following commit methods are supported:</span></span>
- <span data-ttu-id="447d8-173">空中攻攻形手势（即，在您自己的前方抬起，并将您的食指和拇指结合在一起）</span><span class="sxs-lookup"><span data-stu-id="447d8-173">Air tap hand gesture (i.e., raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="447d8-174">说 _"选择"_ 或一个目标语音命令</span><span class="sxs-lookup"><span data-stu-id="447d8-174">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="447d8-175">在[HoloLens Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上按单个按钮</span><span class="sxs-lookup"><span data-stu-id="447d8-175">Press a single button on a [HoloLens Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="447d8-176">按下 Xbox 游戏板上的 "A" 按钮</span><span class="sxs-lookup"><span data-stu-id="447d8-176">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="447d8-177">按 Xbox 自适应控制器上的 "A" 按钮</span><span class="sxs-lookup"><span data-stu-id="447d8-177">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="447d8-178">注视和气攻敲击手势</span><span class="sxs-lookup"><span data-stu-id="447d8-178">Gaze and air tap gesture</span></span>
<span data-ttu-id="447d8-179">隔空敲击是一种手部直立的点击手势。</span><span class="sxs-lookup"><span data-stu-id="447d8-179">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="447d8-180">若要执行分流，请将索引向下移动到准备好的位置，然后使用拇指来凸出，并使索引抓手指返回到释放状态。</span><span class="sxs-lookup"><span data-stu-id="447d8-180">To perform an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="447d8-181">在 HoloLens （第一代）上，分流是最常见的辅助输入。</span><span class="sxs-lookup"><span data-stu-id="447d8-181">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="447d8-182">![手指处于就绪位置](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="447d8-182">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="447d8-183">**手指处于就绪位置**</span><span class="sxs-lookup"><span data-stu-id="447d8-183">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="447d8-184">![按下手指点击或单击](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="447d8-184">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="447d8-185">**按下手指点击或单击**</span><span class="sxs-lookup"><span data-stu-id="447d8-185">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="447d8-186">HoloLens 2 上也提供了空中点击。</span><span class="sxs-lookup"><span data-stu-id="447d8-186">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="447d8-187">它已从原始版本中宽松。</span><span class="sxs-lookup"><span data-stu-id="447d8-187">It has been relaxed from the original version.</span></span> <span data-ttu-id="447d8-188">几乎所有类型的 pinches 现在都受支持，只要手直立并且仍保持。</span><span class="sxs-lookup"><span data-stu-id="447d8-188">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="447d8-189">这使用户更容易学习和执行手势。</span><span class="sxs-lookup"><span data-stu-id="447d8-189">This makes it much easier for users to learn and perform the gesture.</span></span> <span data-ttu-id="447d8-190">这种新的 "air" 将通过相同的 API 替换旧的，因此，在重新编译 HoloLens 2 后，现有应用程序将自动具有新行为。</span><span class="sxs-lookup"><span data-stu-id="447d8-190">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="447d8-191">注视并单击 "选择" 语音命令</span><span class="sxs-lookup"><span data-stu-id="447d8-191">Gaze and "Select" voice command</span></span>
<span data-ttu-id="447d8-192">语音命令是混合现实中的主要交互方法之一。</span><span class="sxs-lookup"><span data-stu-id="447d8-192">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="447d8-193">它提供一种非常强大的无人参与机制来控制系统。</span><span class="sxs-lookup"><span data-stu-id="447d8-193">It provides a very powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="447d8-194">有不同类型的语音交互模型：</span><span class="sxs-lookup"><span data-stu-id="447d8-194">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="447d8-195">执行单击传动或提交作为辅助输入的一般 "Select" 命令。</span><span class="sxs-lookup"><span data-stu-id="447d8-195">The generic "Select" command that performs a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="447d8-196">对象命令（例如，"关闭" 或 "使其变大"）作为辅助输入执行并提交到操作。</span><span class="sxs-lookup"><span data-stu-id="447d8-196">Object commands (e.g., "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="447d8-197">全局命令（例如，"中转到开始"）不需要目标。</span><span class="sxs-lookup"><span data-stu-id="447d8-197">Global commands (e.g., "Go to start") don't require a target.</span></span>
- <span data-ttu-id="447d8-198">像 Cortana 这样的对话用户界面或实体具有 AI 自然语言功能。</span><span class="sxs-lookup"><span data-stu-id="447d8-198">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="447d8-199">自定义语音命令</span><span class="sxs-lookup"><span data-stu-id="447d8-199">Custom voice commands</span></span>

<span data-ttu-id="447d8-200">若要了解更多详细信息以及可用语音命令的完整列表以及如何使用这些命令，请查看我们的[语音](voice-design.md)命令指南。</span><span class="sxs-lookup"><span data-stu-id="447d8-200">To find out more details as well as a comprehensive list of available voice commands and how to use them, check out our [voice commanding](voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="447d8-201">注视和 HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="447d8-201">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="447d8-202">HoloLens Clicker 是专门为 HoloLens 构建的第一个外围设备。</span><span class="sxs-lookup"><span data-stu-id="447d8-202">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="447d8-203">它随附于 HoloLens （第一代）开发版本。</span><span class="sxs-lookup"><span data-stu-id="447d8-203">It is included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="447d8-204">通过 HoloLens Clicker，用户可单击最小手动运动，并提交为辅助输入。</span><span class="sxs-lookup"><span data-stu-id="447d8-204">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="447d8-205">HoloLens Clicker 使用蓝牙低功耗（BTLE）连接到 HoloLens （第一代）或 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="447d8-205">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="447d8-206">有关将设备配对的详细信息和说明</span><span class="sxs-lookup"><span data-stu-id="447d8-206">More information and instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="447d8-207">*映像： HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="447d8-207">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens 遥控器](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="447d8-209">注视和 Xbox 无线控制器</span><span class="sxs-lookup"><span data-stu-id="447d8-209">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="447d8-210">Xbox 无线控制器使用 "A" 按钮执行单击传动作为辅助输入。</span><span class="sxs-lookup"><span data-stu-id="447d8-210">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="447d8-211">设备映射到一组可帮助导航和控制系统的默认操作。</span><span class="sxs-lookup"><span data-stu-id="447d8-211">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="447d8-212">如果要自定义控制器，请使用 Xbox 附件应用程序来配置 Xbox 无线控制器。</span><span class="sxs-lookup"><span data-stu-id="447d8-212">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="447d8-213">如何将 Xbox 控制器与电脑配对</span><span class="sxs-lookup"><span data-stu-id="447d8-213">How to pair an Xbox controller with your PC</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="447d8-214">*映像： Xbox 无线控制器*</span><span class="sxs-lookup"><span data-stu-id="447d8-214">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox 无线控制器](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="447d8-216">注视和 Xbox 自适应控制器</span><span class="sxs-lookup"><span data-stu-id="447d8-216">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="447d8-217">Xbox 自适应控制器主要用于满足移动性有限的游戏玩家的需求，是一种统一的设备，有助于使混合现实更易于访问。</span><span class="sxs-lookup"><span data-stu-id="447d8-217">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="447d8-218">Xbox 自适应控制器使用 "A" 按钮执行单击传动作为辅助输入。</span><span class="sxs-lookup"><span data-stu-id="447d8-218">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="447d8-219">设备映射到一组可帮助导航和控制系统的默认操作。</span><span class="sxs-lookup"><span data-stu-id="447d8-219">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="447d8-220">如果要自定义控制器，请使用 Xbox 附件应用程序来配置 Xbox 自适应控制器。</span><span class="sxs-lookup"><span data-stu-id="447d8-220">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="447d8-221">![Xbox 自适应控制器](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="447d8-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="447d8-222">*Xbox 自适应控制器*</span><span class="sxs-lookup"><span data-stu-id="447d8-222">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="447d8-223">连接外部设备，如交换机、按钮、装入和操纵杆，以创建唯一的自定义控制器体验。</span><span class="sxs-lookup"><span data-stu-id="447d8-223">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="447d8-224">按钮、操纵杆和触发器输入由通过 3.5 mm 插座和 USB 端口连接的辅助设备控制。</span><span class="sxs-lookup"><span data-stu-id="447d8-224">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5mm jacks and USB ports.</span></span>

<span data-ttu-id="447d8-225">![Xbox 自适应控制器端口](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="447d8-225">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="447d8-226">*Xbox 自适应控制器端口*</span><span class="sxs-lookup"><span data-stu-id="447d8-226">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="447d8-227">设备配对说明</span><span class="sxs-lookup"><span data-stu-id="447d8-227">Instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="447d8-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 网站上提供了更多信息</a></span><span class="sxs-lookup"><span data-stu-id="447d8-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="447d8-229">复合手势</span><span class="sxs-lookup"><span data-stu-id="447d8-229">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="447d8-230">隔空敲击</span><span class="sxs-lookup"><span data-stu-id="447d8-230">Air tap</span></span>
<span data-ttu-id="447d8-231">Air 攻攻敲击手势（以及下面的其他手势）仅对特定攻丝做出反应。</span><span class="sxs-lookup"><span data-stu-id="447d8-231">The air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="447d8-232">若要检测其他点击，如菜单或抓住，你的应用程序必须直接使用上面两个关键组件手势部分中所述的低级交互。</span><span class="sxs-lookup"><span data-stu-id="447d8-232">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="447d8-233">点击并按住</span><span class="sxs-lookup"><span data-stu-id="447d8-233">Tap and hold</span></span>
<span data-ttu-id="447d8-234">按住是指保持隔空敲击手指向下的位置。</span><span class="sxs-lookup"><span data-stu-id="447d8-234">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="447d8-235">与 arm 移动（如选取对象，而不是激活对象或 mousedown 辅助交互，如显示上下文菜单）结合使用时，点击和保持的组合允许使用各种更复杂的 "单击并拖动" 交互。</span><span class="sxs-lookup"><span data-stu-id="447d8-235">The combination of air tap and hold allows for a variety of more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="447d8-236">但在设计此手势时请务必小心，因为用户在做出任何扩展手势的过程都很可能放松手部姿势。</span><span class="sxs-lookup"><span data-stu-id="447d8-236">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="447d8-237">操作</span><span class="sxs-lookup"><span data-stu-id="447d8-237">Manipulation</span></span>
<span data-ttu-id="447d8-238">当您想让全息图对用户的手的变动做出回应1:1 时，可以使用操作手势移动、调整或旋转全息图。</span><span class="sxs-lookup"><span data-stu-id="447d8-238">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="447d8-239">此类 1:1 运动可让用户进行实际绘制或绘画。</span><span class="sxs-lookup"><span data-stu-id="447d8-239">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="447d8-240">操作手势的初始定位应通过凝视或指向来完成。</span><span class="sxs-lookup"><span data-stu-id="447d8-240">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="447d8-241">点击并保持开始后，对象的任何操作都将由手动移动处理，使用户能够在操作时进行浏览。</span><span class="sxs-lookup"><span data-stu-id="447d8-241">Once the tap and hold starts, any manipulation of the object is handled by hand movements, freeing the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="447d8-242">导航</span><span class="sxs-lookup"><span data-stu-id="447d8-242">Navigation</span></span>
<span data-ttu-id="447d8-243">导航手势就像一个虚拟游戏杆，可用于导航 UI 小组件（如径向菜单）。</span><span class="sxs-lookup"><span data-stu-id="447d8-243">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="447d8-244">点击并按住以开始手势，然后在标准化 3D 立方体中以初始按压位置为中心移动手部。</span><span class="sxs-lookup"><span data-stu-id="447d8-244">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="447d8-245">可以沿 X、Y 或 Z 轴移动，起点为 0，移动范围为 -1 到 1。</span><span class="sxs-lookup"><span data-stu-id="447d8-245">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="447d8-246">导航可用于生成基于速度的连续滚动或缩放手势，类似于通过单击鼠标按钮然后上下移动鼠标来滚动 2D UI。</span><span class="sxs-lookup"><span data-stu-id="447d8-246">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="447d8-247">使用 rails 导航，是指在该轴上达到特定阈值之前识别特定轴中的运动的能力。</span><span class="sxs-lookup"><span data-stu-id="447d8-247">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="447d8-248">当开发人员在应用程序中启用多个轴的移动时，这种方法非常有用，例如，如果将应用程序配置为识别 X、Y 轴上的导航笔势，同时还指定了具有 rails 的 X 轴。</span><span class="sxs-lookup"><span data-stu-id="447d8-248">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="447d8-249">在这种情况下，系统将识别 x 轴上的手动运动，只要它们保留在 X 轴上的假想导轨（引导）内，也会在 Y 轴上进行手动移动。</span><span class="sxs-lookup"><span data-stu-id="447d8-249">In this case the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="447d8-250">在 2D 应用中，用户可以使用垂直导航手势在应用内进行滚动、缩放或拖动。</span><span class="sxs-lookup"><span data-stu-id="447d8-250">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="447d8-251">这会向应用注入虚拟手指触摸，以模拟相同类型的触摸手势。</span><span class="sxs-lookup"><span data-stu-id="447d8-251">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="447d8-252">用户可以通过选择按钮或口述 "<滚动/拖动/缩放> 工具"，来选择要执行的操作，方法是在应用程序上方的工具间切换。</span><span class="sxs-lookup"><span data-stu-id="447d8-252">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="447d8-253">有关复合手势的详细信息</span><span class="sxs-lookup"><span data-stu-id="447d8-253">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="447d8-254">手势识别器</span><span class="sxs-lookup"><span data-stu-id="447d8-254">Gesture recognizers</span></span>

<span data-ttu-id="447d8-255">使用手势识别的一个优点是，只能为当前目标全息图可以接受的手势配置笔势识别器。</span><span class="sxs-lookup"><span data-stu-id="447d8-255">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="447d8-256">平台仅根据需要消除歧义以区分这些特定支持的手势。</span><span class="sxs-lookup"><span data-stu-id="447d8-256">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="447d8-257">通过这种方式，仅支持 "分流" 的全息图可以接受按下和释放之间的任何时间长度，而同时支持点击和按住的全息影像可以在保持时间阈值后将点击提升为保留。</span><span class="sxs-lookup"><span data-stu-id="447d8-257">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="447d8-258">手部识别</span><span class="sxs-lookup"><span data-stu-id="447d8-258">Hand recognition</span></span>
<span data-ttu-id="447d8-259">HoloLens 通过跟踪设备可识别的一只手或双手的位置来识别手势。</span><span class="sxs-lookup"><span data-stu-id="447d8-259">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="447d8-260">当手处于就绪状态（手背朝向自己，食指向上）或按下状态（手背朝向自己，食指向下）时，HoloLens 可检测到手部。</span><span class="sxs-lookup"><span data-stu-id="447d8-260">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="447d8-261">当双手处于其他姿势时，HoloLens 会将其忽略。</span><span class="sxs-lookup"><span data-stu-id="447d8-261">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="447d8-262">对于 HoloLens 检测到的每一种情况，你可以访问其位置而无需方向和按下状态。</span><span class="sxs-lookup"><span data-stu-id="447d8-262">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="447d8-263">当手接近手势范围的边缘时，可看到一个方向向量，可向用户显示该方向向量，以便他们知道如何将手移回 HoloLens 可检测的范围。</span><span class="sxs-lookup"><span data-stu-id="447d8-263">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="447d8-264">手势范围</span><span class="sxs-lookup"><span data-stu-id="447d8-264">Gesture frame</span></span>
<span data-ttu-id="447d8-265">对于 HoloLens 上的手势，手型必须在笔势框架内，范围是笔势感应摄像机可以正确查看的范围，从鼻子到 waist，以及需要肩负之间。</span><span class="sxs-lookup"><span data-stu-id="447d8-265">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="447d8-266">用户需要在这一认知领域进行培训，以实现操作的成功，并为他们提供便利。</span><span class="sxs-lookup"><span data-stu-id="447d8-266">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="447d8-267">许多用户最初会假设该笔势帧必须在其视图中通过 HoloLens 显示，并将其 uncomfortably，以便进行交互。</span><span class="sxs-lookup"><span data-stu-id="447d8-267">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact.</span></span> <span data-ttu-id="447d8-268">使用 HoloLens Clicker 时，不一定要将指针放在手势帧中。</span><span class="sxs-lookup"><span data-stu-id="447d8-268">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="447d8-269">特别是连续的手势时，用户在移动全息对象时，可能会有这样的风险：将其指针移到手势帧外，而在移动全息对象时，还会失去预期结果。</span><span class="sxs-lookup"><span data-stu-id="447d8-269">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="447d8-270">应考虑以下三个事项：</span><span class="sxs-lookup"><span data-stu-id="447d8-270">There are three things that you should consider:</span></span>

- <span data-ttu-id="447d8-271">手势帧存在和大致边界的用户教育。</span><span class="sxs-lookup"><span data-stu-id="447d8-271">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="447d8-272">这会在安装 HoloLens 期间进行。</span><span class="sxs-lookup"><span data-stu-id="447d8-272">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="447d8-273">当用户的手势接近或中断应用程序内的手势帧边界时，通知用户，使丢失的手势导致意外的结果。</span><span class="sxs-lookup"><span data-stu-id="447d8-273">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="447d8-274">研究显示了此类通知系统的重要质量。</span><span class="sxs-lookup"><span data-stu-id="447d8-274">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="447d8-275">在中心游标上，HoloLens shell 提供此类通知的很好的示例，指示边界交叉的发生方向。</span><span class="sxs-lookup"><span data-stu-id="447d8-275">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="447d8-276">应尽可能避免穿过手势范围的边界。</span><span class="sxs-lookup"><span data-stu-id="447d8-276">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="447d8-277">通常，这意味着应在边界停止笔势的结果，而不是反转。</span><span class="sxs-lookup"><span data-stu-id="447d8-277">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="447d8-278">例如，如果用户在房间内移动某个全息对象，则在该笔势帧被破坏时，移动应停止，并且不会返回到开始点。</span><span class="sxs-lookup"><span data-stu-id="447d8-278">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="447d8-279">用户可能会遇到一些挫折，但可能会更快地了解边界，无需每次都重新启动其全部预期操作。</span><span class="sxs-lookup"><span data-stu-id="447d8-279">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="447d8-280">另请参阅</span><span class="sxs-lookup"><span data-stu-id="447d8-280">See also</span></span>
* [<span data-ttu-id="447d8-281">基于眼睛的交互</span><span class="sxs-lookup"><span data-stu-id="447d8-281">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="447d8-282">HoloLens 2 中的眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="447d8-282">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="447d8-283">凝视和停留</span><span class="sxs-lookup"><span data-stu-id="447d8-283">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="447d8-284">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="447d8-284">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="447d8-285">手 - 手势</span><span class="sxs-lookup"><span data-stu-id="447d8-285">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="447d8-286">手 - 指向并提交</span><span class="sxs-lookup"><span data-stu-id="447d8-286">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="447d8-287">本能交互</span><span class="sxs-lookup"><span data-stu-id="447d8-287">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="447d8-288">语音输入</span><span class="sxs-lookup"><span data-stu-id="447d8-288">Voice input</span></span>](voice-input.md)

