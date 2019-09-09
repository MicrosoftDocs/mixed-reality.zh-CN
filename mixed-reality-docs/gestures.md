---
title: 笔势
description: 手动手势允许用户在混合现实中采取措施。
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实、手势、交互、设计
ms.openlocfilehash: 70b03c6fa327bd987a681bba59abb725c3ddc6b4
ms.sourcegitcommit: e5b677f92ac4b1dff9aad6c329345a5aca4fcef5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2019
ms.locfileid: "69020213"
---
# <a name="gestures"></a><span data-ttu-id="41260-104">笔势</span><span class="sxs-lookup"><span data-stu-id="41260-104">Gestures</span></span>

<span data-ttu-id="41260-105">手动手势允许用户在混合现实中采取措施。</span><span class="sxs-lookup"><span data-stu-id="41260-105">Hand gestures allow users to take action in mixed reality.</span></span> <span data-ttu-id="41260-106">交互是根据**注视**目标和**手势**或**声音**构建的，以处理任何已设定的元素。</span><span class="sxs-lookup"><span data-stu-id="41260-106">Interaction is built on **gaze** to target and **gesture** or **voice** to act upon whatever element has been targeted.</span></span> <span data-ttu-id="41260-107">手势不能在空间中提供精确的位置，但将其投入到 HoloLens 上并立即与内容交互可使用户无需任何其他附件即可工作。</span><span class="sxs-lookup"><span data-stu-id="41260-107">Hand gestures do not provide a precise location in space, but the simplicity of putting on a HoloLens and immediately interacting with content allows users to get to work without any other accessories.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a><span data-ttu-id="41260-108">设备支持</span><span class="sxs-lookup"><span data-stu-id="41260-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="41260-109"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="41260-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="41260-110"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="41260-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="41260-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="41260-111"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="41260-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="41260-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="41260-113">笔势</span><span class="sxs-lookup"><span data-stu-id="41260-113">Gestures</span></span></td>
        <td><span data-ttu-id="41260-114">✔️</span><span class="sxs-lookup"><span data-stu-id="41260-114">✔️</span></span></td>
        <td><span data-ttu-id="41260-115">✔️</span><span class="sxs-lookup"><span data-stu-id="41260-115">✔️</span></span></td>
        <td><span data-ttu-id="41260-116">❌</span><span class="sxs-lookup"><span data-stu-id="41260-116">❌</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="41260-117">明确表述</span><span class="sxs-lookup"><span data-stu-id="41260-117">Articulated hands</span></span></td>
        <td><span data-ttu-id="41260-118">❌</span><span class="sxs-lookup"><span data-stu-id="41260-118">❌</span></span></td>
        <td><span data-ttu-id="41260-119">✔️</span><span class="sxs-lookup"><span data-stu-id="41260-119">✔️</span></span></td>
        <td><span data-ttu-id="41260-120">❌</span><span class="sxs-lookup"><span data-stu-id="41260-120">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="41260-121">即将[推出](index.md#news-and-notes)特定于 HoloLens 2 的更多指导。</span><span class="sxs-lookup"><span data-stu-id="41260-121">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gaze-and-commit"></a><span data-ttu-id="41260-122">注视并提交</span><span class="sxs-lookup"><span data-stu-id="41260-122">Gaze-and-commit</span></span>

<span data-ttu-id="41260-123">若要执行操作，[请使用手型](gaze.md)作为目标机制。</span><span class="sxs-lookup"><span data-stu-id="41260-123">To take actions, hand gestures use [head gaze](gaze.md) as the targeting mechanism.</span></span> <span data-ttu-id="41260-124">"**注视**" 和 " **Air** " 手势的组合会导致 "**注视并提交**" 交互。</span><span class="sxs-lookup"><span data-stu-id="41260-124">The combination of **Gaze** and the **Air tap** gesture results in a **gaze-and-commit** interaction.</span></span> <span data-ttu-id="41260-125">可通过[运动控制器](motion-controllers.md)启用**点到提交**功能，这是一种用于确认的替代方法。</span><span class="sxs-lookup"><span data-stu-id="41260-125">An alternative to gaze-and-commit is **point-and-commit**, enabled by [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="41260-126">在 HoloLens 上运行的应用程序只需支持 "注视并提交"，因为 HoloLens 不支持运动控制器。</span><span class="sxs-lookup"><span data-stu-id="41260-126">Apps that run on HoloLens only need to support gaze-and-commit since HoloLens does not support motion controllers.</span></span> <span data-ttu-id="41260-127">在 HoloLens 和沉浸式耳机上运行的应用程序应同时支持注视驱动和指向驱动的交互，使用户能够选择他们使用的输入设备。</span><span class="sxs-lookup"><span data-stu-id="41260-127">Apps that run on both HoloLens and immersive headsets should support both gaze-driven and pointing-driven interactions, to give users choice in what input device they use.</span></span>

## <a name="the-two-core-gestures-of-hololens"></a><span data-ttu-id="41260-128">HoloLens 的两个核心手势</span><span class="sxs-lookup"><span data-stu-id="41260-128">The two core gestures of HoloLens</span></span>

<span data-ttu-id="41260-129">HoloLens 目前识别了两个核心组件手势-**空中分流**和**布隆**。</span><span class="sxs-lookup"><span data-stu-id="41260-129">HoloLens currently recognizes two core component gestures - **Air tap** and **Bloom**.</span></span> <span data-ttu-id="41260-130">这两个核心交互是开发人员可以访问的空间输入数据的最低级别。</span><span class="sxs-lookup"><span data-stu-id="41260-130">These two core interactions are the lowest level of spatial input data that a developer can access.</span></span> <span data-ttu-id="41260-131">它们构成了各种可能的用户操作的基础。</span><span class="sxs-lookup"><span data-stu-id="41260-131">They form the foundation for a variety of possible user actions.</span></span>

### <a name="air-tap"></a><span data-ttu-id="41260-132">隔空敲击</span><span class="sxs-lookup"><span data-stu-id="41260-132">Air tap</span></span>

<span data-ttu-id="41260-133">空中点击是指手直立的攻指，类似于鼠标单击或选择。</span><span class="sxs-lookup"><span data-stu-id="41260-133">Air tap is a tapping gesture with the hand held upright, similar to a mouse click or select.</span></span> <span data-ttu-id="41260-134">这适用于最[常使用的](gaze.md)一种在 UI 元素上 "单击" 的</span><span class="sxs-lookup"><span data-stu-id="41260-134">This is used in most HoloLens experiences for the equivalent of a "click" on a UI element after targeting it with [Gaze](gaze.md).</span></span> <span data-ttu-id="41260-135">这是一种通用操作，你只需要了解一次，然后应用于所有应用。</span><span class="sxs-lookup"><span data-stu-id="41260-135">It is a universal action that you learn once and then apply across all your apps.</span></span> <span data-ttu-id="41260-136">执行 select 的其他方法是按下一次使用[HoloLens Clicker](hardware-accessories.md#hololens-clicker)上的按钮，或者通过语音命令 "select"。</span><span class="sxs-lookup"><span data-stu-id="41260-136">Other ways to perform select are by pressing the single button on a [HoloLens Clicker](hardware-accessories.md#hololens-clicker) or by speaking the voice command "Select".</span></span>

<span data-ttu-id="41260-137">![HoloLens 上手写笔势的就绪状态](images/image9.png)</span><span class="sxs-lookup"><span data-stu-id="41260-137">![Ready state for hand gestures on HoloLens](images/image9.png)</span></span><br>
<span data-ttu-id="41260-138">*HoloLens 的空中点击的就绪状态。*</span><span class="sxs-lookup"><span data-stu-id="41260-138">*Ready state for Air tap on HoloLens.*</span></span>

<span data-ttu-id="41260-139">Air 是一种离散的手势。</span><span class="sxs-lookup"><span data-stu-id="41260-139">Air tap is a discrete gesture.</span></span> <span data-ttu-id="41260-140">选择是 "已完成" 或 "不是"，并且不会在经验中执行操作。</span><span class="sxs-lookup"><span data-stu-id="41260-140">A selection is either completed or it is not, an action is or is not taken within an experience.</span></span> <span data-ttu-id="41260-141">尽管不建议这样做，但不建议这样做，而是通过主要组件组合（例如，双击笔势来表示与单点不同的内容）来创建其他离散手势。</span><span class="sxs-lookup"><span data-stu-id="41260-141">It is possible, though not recommended without some specific purpose, to create other discrete gestures from combinations of the main components (e.g. a double-tap gesture to mean something different than a single-tap).</span></span>

<span data-ttu-id="41260-142">![手指置于 "就绪" 位置，然后点击或点击 "运动"](images/readyandpress.jpg)</span><span class="sxs-lookup"><span data-stu-id="41260-142">![Finger in the ready position and then a tap or click motion](images/readyandpress.jpg)</span></span><br>
<span data-ttu-id="41260-143">*如何执行分流：将您的食指向下移动到 "就绪" 位置，按下手指以点击或选择，然后备份到发布。*</span><span class="sxs-lookup"><span data-stu-id="41260-143">*How to perform an Air tap: Raise your index finger to the ready position, press your finger down to tap or select and then back up to release.*</span></span>

### <a name="bloom"></a><span data-ttu-id="41260-144">布隆</span><span class="sxs-lookup"><span data-stu-id="41260-144">Bloom</span></span>

<span data-ttu-id="41260-145">布隆是 "home" 手势，为单独手势预留。</span><span class="sxs-lookup"><span data-stu-id="41260-145">Bloom is the "home" gesture and is reserved for that alone.</span></span> <span data-ttu-id="41260-146">这是一种特殊的系统操作，用于返回到 "开始" 菜单。</span><span class="sxs-lookup"><span data-stu-id="41260-146">It is a special system action that is used to go back to the Start Menu.</span></span> <span data-ttu-id="41260-147">它相当于按键盘上的 Windows 键或 Xbox 控制器上的 Xbox 按钮。</span><span class="sxs-lookup"><span data-stu-id="41260-147">It is equivalent to pressing the Windows key on a keyboard or the Xbox button on an Xbox controller.</span></span> <span data-ttu-id="41260-148">用户可以使用任一手型。</span><span class="sxs-lookup"><span data-stu-id="41260-148">The user can use either hand.</span></span>

![HoloLens 上的布隆手势](images/image10-640px.png)

<span data-ttu-id="41260-150">若要在 HoloLens 上执行布隆手势，请将你的手拿在一起，让你能够轻松地在一起。</span><span class="sxs-lookup"><span data-stu-id="41260-150">To do the bloom gesture on HoloLens, hold out your hand, palm up, with your fingertips together.</span></span> <span data-ttu-id="41260-151">然后打开手。</span><span class="sxs-lookup"><span data-stu-id="41260-151">Then open your hand.</span></span> <span data-ttu-id="41260-152">请注意，你还可以通过说 "你好 Cortana，回家" 开始。</span><span class="sxs-lookup"><span data-stu-id="41260-152">Note, you can also always return to Start by saying "Hey Cortana, Go Home".</span></span> <span data-ttu-id="41260-153">应用程序无法专门对 home 操作做出反应，因为系统会对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="41260-153">Apps cannot react specifically to a home action, as these are handled by the system.</span></span>

<span data-ttu-id="41260-154">![布隆手势](images/bloom-giphy.gif)</span><span class="sxs-lookup"><span data-stu-id="41260-154">![Bloom gesture](images/bloom-giphy.gif)</span></span><br>
<span data-ttu-id="41260-155">*如何在 HoloLens 上执行布隆手势。*</span><span class="sxs-lookup"><span data-stu-id="41260-155">*How to perform the bloom gesture on HoloLens.*</span></span>

## <a name="composite-gestures"></a><span data-ttu-id="41260-156">复合手势</span><span class="sxs-lookup"><span data-stu-id="41260-156">Composite gestures</span></span>

<span data-ttu-id="41260-157">应用不只可以识别单独的点击手势。</span><span class="sxs-lookup"><span data-stu-id="41260-157">Apps can recognize more than just individual taps.</span></span> <span data-ttu-id="41260-158">通过将点击、保持和释放与手部移动结合，可以执行更复杂的复合手势。</span><span class="sxs-lookup"><span data-stu-id="41260-158">By combining tap, hold and release with the movement of the hand, more complex composite gestures can be performed.</span></span> <span data-ttu-id="41260-159">这些复合手势或高级手势建立在开发人员可以访问的低级别空间输入数据（基于隔空敲击和使用开花手势）之上。</span><span class="sxs-lookup"><span data-stu-id="41260-159">These composite or high-level gestures build on the low-level spatial input data (from Air tap and Bloom) that developers have access to.</span></span>

<table>
<tr>
<th> <span data-ttu-id="41260-160">复合手势</span><span class="sxs-lookup"><span data-stu-id="41260-160">Composite gesture</span></span></th><th> <span data-ttu-id="41260-161">如何应用</span><span class="sxs-lookup"><span data-stu-id="41260-161">How to apply</span></span></th>
</tr><tr>
<td><span data-ttu-id="41260-162">隔空敲击</span><span class="sxs-lookup"><span data-stu-id="41260-162">Air tap</span></span></td><td><span data-ttu-id="41260-163">隔空敲击手势（以及下面的其他手势）只对特定的点击做出反应。</span><span class="sxs-lookup"><span data-stu-id="41260-163">The Air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="41260-164">若要检测其他点击，例如菜单或抓取，应用必须直接使用上面两个关键成分手势部分中描述的较低级别的互动。</span><span class="sxs-lookup"><span data-stu-id="41260-164">To detect other taps, such as Menu or Grasp, your app must directly use the lower-level interactions described in two key component gestures section above.</span></span></td>
</tr><tr>
<td><span data-ttu-id="41260-165">Tap and hold</span><span class="sxs-lookup"><span data-stu-id="41260-165">Tap and hold</span></span></td><td><p><span data-ttu-id="41260-166">按住是指保持隔空敲击手指向下的位置。</span><span class="sxs-lookup"><span data-stu-id="41260-166">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="41260-167">通过点击和保持的组合，可以在与 arm 移动（如&quot;选取对象，&quot;而不是激活对象或&quot;mousedown&quot; ）结合使用时，使用各种更复杂的单击和拖动交互辅助交互，如显示上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="41260-167">The combination of air tap and hold allows for a variety of more complex &quot;click and drag&quot; interactions when combined with arm movement such as picking up an object instead of activating it or &quot;mousedown&quot; secondary interactions such as showing a context menu.</span></span></p><p><span data-ttu-id="41260-168">但在设计此手势时请务必小心，因为用户在做出任何扩展手势的过程都很可能放松手部姿势。</span><span class="sxs-lookup"><span data-stu-id="41260-168">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span></p></td>
</tr><tr>
<td><span data-ttu-id="41260-169">操作</span><span class="sxs-lookup"><span data-stu-id="41260-169">Manipulation</span></span></td><td><p><span data-ttu-id="41260-170">如果想让全息图对用户&#39;的手移动做出1:1 反应，可以使用操作手势移动、调整或旋转全息图。</span><span class="sxs-lookup"><span data-stu-id="41260-170">Manipulation gestures can be used to move, resize or rotate a hologram when you want the hologram to react 1:1 to the user&#39;s hand movements.</span></span> <span data-ttu-id="41260-171">此类 1:1 运动可让用户进行实际绘制或绘画。</span><span class="sxs-lookup"><span data-stu-id="41260-171">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span></p><p><span data-ttu-id="41260-172">操作手势的初始定位应通过凝视或指向来完成。</span><span class="sxs-lookup"><span data-stu-id="41260-172">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="41260-173">开始点击并按住后，对象的任何操作都将通过手部运动来处理，从而使用户可以在操作时环顾四周。</span><span class="sxs-lookup"><span data-stu-id="41260-173">Once the tap and hold starts, any manipulation of the object is then handled by hand movements, freeing the user to look around while they manipulate.</span></span></p></td>
</tr><tr>
<td><span data-ttu-id="41260-174">导航</span><span class="sxs-lookup"><span data-stu-id="41260-174">Navigation</span></span></td><td><p><span data-ttu-id="41260-175">导航手势就像一个虚拟游戏杆，可用于导航 UI 小组件（如径向菜单）。</span><span class="sxs-lookup"><span data-stu-id="41260-175">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="41260-176">点击并按住以开始手势，然后在标准化 3D 立方体中以初始按压位置为中心移动手部。</span><span class="sxs-lookup"><span data-stu-id="41260-176">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="41260-177">可以沿 X、Y 或 Z 轴移动，起点为 0，移动范围为 -1 到 1。</span><span class="sxs-lookup"><span data-stu-id="41260-177">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span></p><p><span data-ttu-id="41260-178">导航可用于生成基于速度的连续滚动或缩放手势，类似于通过单击鼠标按钮然后上下移动鼠标来滚动 2D UI。</span><span class="sxs-lookup"><span data-stu-id="41260-178">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span></p><p><span data-ttu-id="41260-179">轨道导航是指识别某个轴上的运动，直到达到该轴的特定阈值。</span><span class="sxs-lookup"><span data-stu-id="41260-179">Navigation with rails refers to the ability of recognizing movements in certain axis until certain threshold is reached on that axis.</span></span> <span data-ttu-id="41260-180">只有当开发人员在应用程序中启用多个轴中的移动时，轨道导航才有用，例如，如果应用程序被配置为能够识别 X 轴、Y 轴上的导航手势，并指定 X 轴包含轨道。</span><span class="sxs-lookup"><span data-stu-id="41260-180">This is only useful, when movement in more than one axis is enabled in an application by the developer, e.g. if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="41260-181">在这种情况下，如果 X 轴和 Y 轴上都出现了手部运动，则只要手部运动保持在 X 轴上的假想轨道（导轨）内，系统就可识别 X 轴上的手部运动。</span><span class="sxs-lookup"><span data-stu-id="41260-181">In this case system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on X axis, if hand movement also occurs Y axis.</span></span></p><p><span data-ttu-id="41260-182">在 2D 应用中，用户可以使用垂直导航手势在应用内进行滚动、缩放或拖动。</span><span class="sxs-lookup"><span data-stu-id="41260-182">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="41260-183">这会向应用注入虚拟手指触摸，以模拟相同类型的触摸手势。</span><span class="sxs-lookup"><span data-stu-id="41260-183">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="41260-184">用户可以通过选择按钮&#39; &lt;或口述 "滚动/拖/缩放&gt; " 工具&#39;，在应用上方的工具栏上通过切换来选择要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="41260-184">Users can select which of these actions take place by toggling between the tools on the bar above the app, either by selecting the button or saying &#39;&lt;Scroll/Drag/Zoom&gt; Tool&#39;.</span></span></p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a><span data-ttu-id="41260-185">手势识别器</span><span class="sxs-lookup"><span data-stu-id="41260-185">Gesture recognizers</span></span>

<span data-ttu-id="41260-186">使用手势识别的一个好处是可以专门为当前目标全息影像可接受的手势配置一个手势识别器。</span><span class="sxs-lookup"><span data-stu-id="41260-186">One benefit of using gesture recognition is that you can configure a gesture recognizer just for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="41260-187">该平台只会进行区分这些特定受支持手势所必需的消除歧义。</span><span class="sxs-lookup"><span data-stu-id="41260-187">The platform will do only the disambiguation necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="41260-188">这样，仅支持隔空敲击的全息影像允许在按下和释放之间经历任意时长，而同时支持点击和按住的全息影像可在经历保持时间阈值之后将点击提升为按住状态。</span><span class="sxs-lookup"><span data-stu-id="41260-188">That way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="41260-189">手部识别</span><span class="sxs-lookup"><span data-stu-id="41260-189">Hand recognition</span></span>

<span data-ttu-id="41260-190">HoloLens 通过跟踪设备可识别的一只手或双手的位置来识别手势。</span><span class="sxs-lookup"><span data-stu-id="41260-190">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="41260-191">HoloLens 处于 "**就绪" 状态**时（即，具有索引指针的正面朝上）或 "**按下" 状态**（向下的食指向下移动），会看到手形。</span><span class="sxs-lookup"><span data-stu-id="41260-191">HoloLens sees hands when they are in either the **ready state** (back of the hand facing you with index finger up) or the **pressed state** (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="41260-192">当手处于其他姿势时，HoloLens 将忽略它们。</span><span class="sxs-lookup"><span data-stu-id="41260-192">When hands are in other poses, the HoloLens will ignore them.</span></span>

<span data-ttu-id="41260-193">对于 HoloLens 检测到的每只手，可访问其位置（无方向）及其按下状态。</span><span class="sxs-lookup"><span data-stu-id="41260-193">For each hand that HoloLens detects, you can access its position (without orientation) and its pressed state.</span></span> <span data-ttu-id="41260-194">当手接近手势范围的边缘时，可看到一个方向向量，可向用户显示该方向向量，以便他们知道如何将手移回 HoloLens 可检测的范围。</span><span class="sxs-lookup"><span data-stu-id="41260-194">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="41260-195">手势范围</span><span class="sxs-lookup"><span data-stu-id="41260-195">Gesture frame</span></span>

<span data-ttu-id="41260-196">对 HoloLens 做出手势时，手必须在“手势范围”内，即手势感应摄像头可以适当检测到的范围内（大致从鼻子到腰部，两肩之间）。</span><span class="sxs-lookup"><span data-stu-id="41260-196">For gestures on HoloLens, the hand must be within a “gesture frame”, in a range that the gesture-sensing cameras can see appropriately (very roughly from nose to waist, and between the shoulders).</span></span> <span data-ttu-id="41260-197">用户需要接受有关识别此区域的培训，以便成功且舒适地完成动作（许多用户最初认为手势范围必须在其通过 HoloLens 看到的视野内，并且为了进行交互以不舒服的姿势举起手臂）。</span><span class="sxs-lookup"><span data-stu-id="41260-197">Users need to be trained on this area of recognition both for success of action and for their own comfort (many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact).</span></span> <span data-ttu-id="41260-198">在使用 HoloLens 控制器时，手不需要在手势范围内。</span><span class="sxs-lookup"><span data-stu-id="41260-198">When using the HoloLens Clicker, your hands do not need to be within the gesture frame.</span></span>

<span data-ttu-id="41260-199">特别是在使用连续手势时，用户在手势进行到一半时可能将手移出手势范围（例如移动某些全息对象），无法获得预期结果。</span><span class="sxs-lookup"><span data-stu-id="41260-199">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture (while moving some holographic object, for example), and losing their intended outcome.</span></span>

<span data-ttu-id="41260-200">应考虑以下三个事项：</span><span class="sxs-lookup"><span data-stu-id="41260-200">There are three things that you should consider:</span></span>
* <span data-ttu-id="41260-201">用户应接受关于手势范围位置和近似边界的培训（在 HoloLens 安装期间教授）。</span><span class="sxs-lookup"><span data-stu-id="41260-201">User education on the gesture frame's existence and approximate boundaries (this is taught during HoloLens setup).</span></span>
* <span data-ttu-id="41260-202">在用户的手势接近/穿过应用程序的手势范围边界时通知用户，避免因丢失手势导致无法获得预期结果。</span><span class="sxs-lookup"><span data-stu-id="41260-202">Notifying users when their gestures are nearing/breaking the gesture frame boundaries within an application, to the degree that a lost gesture will lead to undesired outcomes.</span></span> <span data-ttu-id="41260-203">研究表明了此类通知系统的关键能力，而 HoloLens shell 提供了此类通知的一个良好示例（显示在中央光标处，指示超出边界的方向）。</span><span class="sxs-lookup"><span data-stu-id="41260-203">Research has shown the key qualities of such a notification system, and the HoloLens shell provides a good example of this type of notification (visual, on the central cursor, indicating the direction in which boundary crossing is taking place).</span></span>
* <span data-ttu-id="41260-204">应尽可能避免穿过手势范围的边界。</span><span class="sxs-lookup"><span data-stu-id="41260-204">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="41260-205">一般而言，这意味着手势应在边界处停止，而不是反转。</span><span class="sxs-lookup"><span data-stu-id="41260-205">In general, this means that the outcome of a gesture should be stopped at the boundary, but not reversed.</span></span> <span data-ttu-id="41260-206">例如，如果用户在房间内移动某个全息对象，则在该笔势帧被破坏后，移动应停止，但**不**会返回到开始点。</span><span class="sxs-lookup"><span data-stu-id="41260-206">For example, if a user is moving some holographic object across a room, movement should stop when the gesture frame is breached, but **not** be returned to the starting point.</span></span> <span data-ttu-id="41260-207">用户可能会遇到一些挫折，但可能更快理解边界，而不必每次都重新开始其完整的预期操作。</span><span class="sxs-lookup"><span data-stu-id="41260-207">The user may experience some frustration then, but may more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>

## <a name="see-also"></a><span data-ttu-id="41260-208">请参阅</span><span class="sxs-lookup"><span data-stu-id="41260-208">See also</span></span>
* [<span data-ttu-id="41260-209">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="41260-209">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="41260-210">语音设计</span><span class="sxs-lookup"><span data-stu-id="41260-210">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="41260-211">MR 输入 211：手势</span><span class="sxs-lookup"><span data-stu-id="41260-211">MR Input 211: Gesture</span></span>](holograms-211.md)
* [<span data-ttu-id="41260-212">Unity 中的手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="41260-212">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="41260-213">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="41260-213">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="41260-214">运动控制器</span><span class="sxs-lookup"><span data-stu-id="41260-214">Motion controllers</span></span>](motion-controllers.md)
