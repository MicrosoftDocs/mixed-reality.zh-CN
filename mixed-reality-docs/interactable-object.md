---
title: 种交互的对象
description: 一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。 在三维混合的现实世界中，我们无需限制为抽象不再这个世界。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的现实、 控件、 交互、 ui 和 ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592221"
---
# <a name="interactable-object"></a><span data-ttu-id="f4714-105">种交互的对象</span><span class="sxs-lookup"><span data-stu-id="f4714-105">Interactable object</span></span>

<span data-ttu-id="f4714-106">一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。</span><span class="sxs-lookup"><span data-stu-id="f4714-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="f4714-107">在三维混合的现实世界中，我们无需限制为抽象不再这个世界。</span><span class="sxs-lookup"><span data-stu-id="f4714-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="f4714-108">可以是任何内容**种交互对象**触发事件。</span><span class="sxs-lookup"><span data-stu-id="f4714-108">Anything can be an **Interactable object** that triggers an event.</span></span> <span data-ttu-id="f4714-109">种交互的对象可以表示为任何从上表杯咖啡到气球状飘浮在空中。</span><span class="sxs-lookup"><span data-stu-id="f4714-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="f4714-110">我们仍进行传统按钮在某些情况下此类如下所示对话框 UI 的使用。</span><span class="sxs-lookup"><span data-stu-id="f4714-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="f4714-111">按钮的可视表示形式取决于上下文。</span><span class="sxs-lookup"><span data-stu-id="f4714-111">The visual representation of the button depends on the context.</span></span>

![Interactible 对象英雄形象](images/640px-interactibleobject-hero-640px.jpg)


<span data-ttu-id="f4714-113">在中 **[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，我们创建了一系列的 Unity 脚本并将帮助你的预设创建种交互的对象。</span><span class="sxs-lookup"><span data-stu-id="f4714-113">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, we have created a series of Unity scripts and prefabs that will help you create Interactable objects.</span></span> <span data-ttu-id="f4714-114">可以使用这些来创建任何类型的对象，用户可与之交互，使用这些标准交互状态： 观察，针对，按下。</span><span class="sxs-lookup"><span data-stu-id="f4714-114">You can use these to create any type of object that the user can interact with, using these standard interaction states: observation, targeted and pressed.</span></span> <span data-ttu-id="f4714-115">使用你自己的资产，可以轻松自定义的可视设计。</span><span class="sxs-lookup"><span data-stu-id="f4714-115">You can easily customize the visual design with your own assets.</span></span> <span data-ttu-id="f4714-116">通过创建和分配相应的动画剪辑中 Unity 的动画控制器的交互状态，或者使用偏移量和规模，可以自定义详细的动画。</span><span class="sxs-lookup"><span data-stu-id="f4714-116">Detailed animations can be customized by either creating and assigning corresponding animation clips for the interaction states in the Unity's animation controller or using offset and scale.</span></span> 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a><span data-ttu-id="f4714-117">有关不同输入的交互状态的可视反馈</span><span class="sxs-lookup"><span data-stu-id="f4714-117">Visual feedback for the different input interaction states</span></span>

<span data-ttu-id="f4714-118">混合现实中 holographic 对象相混合现实世界环境后，因为它可能会比较困难，了解这种交互的对象。</span><span class="sxs-lookup"><span data-stu-id="f4714-118">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="f4714-119">你的体验中的任何种交互对象，务必为每个输入状态提供独特的可视反馈。</span><span class="sxs-lookup"><span data-stu-id="f4714-119">For any interactable objects in your experience, it is important to provide differentiated visual feedback for each input state.</span></span> <span data-ttu-id="f4714-120">这有助于用户了解您的体验的哪个部分是种交互，并使用户确信使用一致的交互方法。</span><span class="sxs-lookup"><span data-stu-id="f4714-120">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

<span data-ttu-id="f4714-121">任何对象的该用户可以与之交互，我们建议来具有不同的可视反馈，对于这三个输入状态：</span><span class="sxs-lookup"><span data-stu-id="f4714-121">For any objects that user can interact with, we recommended to have different visual feedback for these three input states:</span></span>
* <span data-ttu-id="f4714-122">**观察**:对象的默认空闲状态。</span><span class="sxs-lookup"><span data-stu-id="f4714-122">**Observation**: Default idle state of the object.</span></span>
* <span data-ttu-id="f4714-123">**目标**:当对象被指向附带的视线移动游标时，手指邻近或动画控制器的指针。</span><span class="sxs-lookup"><span data-stu-id="f4714-123">**Targeted**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="f4714-124">**按下**:对象按下时使用-敲击手势、 手指按或运动控制器的选择按钮。</span><span class="sxs-lookup"><span data-stu-id="f4714-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="f4714-125">![Holographic 按钮](images/640px-interactibleobject-holographicbutton-650px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f4714-125">![Holographic button](images/640px-interactibleobject-holographicbutton-650px.jpg)</span></span><br>
<span data-ttu-id="f4714-126">*观察状态，目标状态，并按下状态*</span><span class="sxs-lookup"><span data-stu-id="f4714-126">*Observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="f4714-127">在 Windows Mixed Reality，可以找到的可视化开始菜单和应用程序栏按钮上的不同输入的状态的示例。</span><span class="sxs-lookup"><span data-stu-id="f4714-127">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> <span data-ttu-id="f4714-128">技术，如突出显示或缩放可用于提供给用户的输入状态的可视反馈。</span><span class="sxs-lookup"><span data-stu-id="f4714-128">You can use techniques such as highlighting or scaling to provide visual feedback to the user’s input states.</span></span>

<span data-ttu-id="f4714-129">在 HoloLens 2 中，因为它支持清楚的手动跟踪输入，我们可以提供基于手到邻近的其他提示。</span><span class="sxs-lookup"><span data-stu-id="f4714-129">In HoloLens 2, since it supports fully articulated hand tracking input, we can provide additional affordances based on the proximity to the hands.</span></span> <span data-ttu-id="f4714-130">[HoloLens 2 中的按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)显示了此示例。</span><span class="sxs-lookup"><span data-stu-id="f4714-130">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows this example.</span></span>

![Pressable 按钮](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a><span data-ttu-id="f4714-132">种交互的对象示例</span><span class="sxs-lookup"><span data-stu-id="f4714-132">Interactable object samples</span></span>

### <a name="mesh-button"></a><span data-ttu-id="f4714-133">网格按钮</span><span class="sxs-lookup"><span data-stu-id="f4714-133">Mesh button</span></span>

![网格按钮](images/640px-interactibleobject-meshbutton.jpg)

<span data-ttu-id="f4714-135">这些是作为种交互对象中使用基元和导入三维网格之上的示例。</span><span class="sxs-lookup"><span data-stu-id="f4714-135">These are examples using primitives and imported 3D meshes as Interactable objects.</span></span> <span data-ttu-id="f4714-136">您可以轻松地分配不同的规模、 偏移量和颜色值，以响应每种输入的交互状态。</span><span class="sxs-lookup"><span data-stu-id="f4714-136">You can easily assign different scale, offset and color values to respond to each input interaction state.</span></span>

### <a name="toolbar"></a><span data-ttu-id="f4714-137">工具栏</span><span class="sxs-lookup"><span data-stu-id="f4714-137">Toolbar</span></span>

![工具栏](images/640px-interactibleobject-toolbar.jpg)

<span data-ttu-id="f4714-139">工具栏是混合的现实体验中的一种广泛使用的模式。</span><span class="sxs-lookup"><span data-stu-id="f4714-139">A toolbar is a widely used pattern in mixed reality experiences.</span></span> <span data-ttu-id="f4714-140">它是一个简单的按钮与其他行为集合如[Billboarding 和尾随](billboarding-and-tag-along.md)。</span><span class="sxs-lookup"><span data-stu-id="f4714-140">It is a simple collection of buttons with additional behaviors such as [Billboarding and tag-along](billboarding-and-tag-along.md).</span></span> <span data-ttu-id="f4714-141">此示例使用从 MixedRealityToolkit Billboarding 和尾随的脚本。</span><span class="sxs-lookup"><span data-stu-id="f4714-141">This example uses a Billboarding and tag-along script from the MixedRealityToolkit.</span></span> <span data-ttu-id="f4714-142">您可以控制详细的行为包括距离，移动速度和阈值的值。</span><span class="sxs-lookup"><span data-stu-id="f4714-142">You can control detailed behaviors including distance, moving speed and threshold values.</span></span>

### <a name="traditional-button"></a><span data-ttu-id="f4714-143">传统的按钮</span><span class="sxs-lookup"><span data-stu-id="f4714-143">Traditional button</span></span>

![传统的按钮](images/640px-interactibleobject-traditionalbutton.jpg)

<span data-ttu-id="f4714-145">此示例演示一个传统的 2D 样式按钮。</span><span class="sxs-lookup"><span data-stu-id="f4714-145">This example shows a traditional 2D style button.</span></span> <span data-ttu-id="f4714-146">每个输入的状态具有略有不同的深度和动画属性。</span><span class="sxs-lookup"><span data-stu-id="f4714-146">Each input state has a slightly different depth and animation property.</span></span>

### <a name="other-examples"></a><span data-ttu-id="f4714-147">其他示例</span><span class="sxs-lookup"><span data-stu-id="f4714-147">Other examples</span></span>

<span data-ttu-id="f4714-148">![下压按钮](images/640px-interactibleobject-pushbutton.jpg)</span><span class="sxs-lookup"><span data-stu-id="f4714-148">![Push button](images/640px-interactibleobject-pushbutton.jpg)</span></span><br>
<span data-ttu-id="f4714-149">*下压按钮*</span><span class="sxs-lookup"><span data-stu-id="f4714-149">*Push button*</span></span>
<br>
<span data-ttu-id="f4714-150">![真实生活对象](images/640px-interactibleobject-reallifeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="f4714-150">![Real Life object](images/640px-interactibleobject-reallifeobject.jpg)</span></span><br>
<span data-ttu-id="f4714-151">*现实生活对象*</span><span class="sxs-lookup"><span data-stu-id="f4714-151">*Real life object*</span></span>

<span data-ttu-id="f4714-152">与 HoloLens，您可以利用的物理空间。</span><span class="sxs-lookup"><span data-stu-id="f4714-152">With HoloLens, you can leverage physical space.</span></span> <span data-ttu-id="f4714-153">假设物理墙上的 holographic 推送按钮。</span><span class="sxs-lookup"><span data-stu-id="f4714-153">Imagine a holographic push button on a physical wall.</span></span> <span data-ttu-id="f4714-154">或如何在实际表杯咖啡？</span><span class="sxs-lookup"><span data-stu-id="f4714-154">Or how about a coffee cup on a real table?</span></span> <span data-ttu-id="f4714-155">使用导入从对软件建模的三维模型，我们可以创建类似于现实生活中对象的种交互对象。</span><span class="sxs-lookup"><span data-stu-id="f4714-155">Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object.</span></span> <span data-ttu-id="f4714-156">由于它是一个数字的对象，我们可以向其添加神奇的交互。</span><span class="sxs-lookup"><span data-stu-id="f4714-156">Since it's a digital object, we can add magical interactions to it.</span></span>

## <a name="interactable-object-in-mixed-reality-toolkit"></a><span data-ttu-id="f4714-157">混合现实工具包中的种交互对象</span><span class="sxs-lookup"><span data-stu-id="f4714-157">Interactable object in Mixed Reality Toolkit</span></span>
<span data-ttu-id="f4714-158">您可以找到[混合现实工具包中对象的 Interactable 示例](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span><span class="sxs-lookup"><span data-stu-id="f4714-158">You can find the [examples of Interactable object in Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span></span>


## <a name="see-also"></a><span data-ttu-id="f4714-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="f4714-159">See also</span></span>
* [<span data-ttu-id="f4714-160">在混合的现实工具包 Unity pressable 按钮</span><span class="sxs-lookup"><span data-stu-id="f4714-160">Pressable Button on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="f4714-161">对象集合</span><span class="sxs-lookup"><span data-stu-id="f4714-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f4714-162">公告板和尾随</span><span class="sxs-lookup"><span data-stu-id="f4714-162">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
