---
title: 显示进度
description: 进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，控件，ui，ux
ms.openlocfilehash: aafcd8eebbabfc5b53d09348d513f62def909da6
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105983"
---
# <a name="progress-indicator"></a><span data-ttu-id="989a0-104">进度指示器</span><span class="sxs-lookup"><span data-stu-id="989a0-104">Progress indicator</span></span>

<br>

<img src="images/UX/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="989a0-105">进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。</span><span class="sxs-lookup"><span data-stu-id="989a0-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="989a0-106">这意味着，在进度指示器可见，并且还可以根据所使用的指示器指示等待时长时，用户无法与该应用交互。</span><span class="sxs-lookup"><span data-stu-id="989a0-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="989a0-107">进度类型</span><span class="sxs-lookup"><span data-stu-id="989a0-107">Types of progress</span></span>

<span data-ttu-id="989a0-108">向用户提供有关发生的情况的信息非常重要。</span><span class="sxs-lookup"><span data-stu-id="989a0-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="989a0-109">在混合现实中，如果你的应用程序没有提供良好的视觉反馈，则可以轻松地在物理环境或对象上对其进行工作。</span><span class="sxs-lookup"><span data-stu-id="989a0-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="989a0-110">对于需要几秒钟时间的情况，例如，当加载数据或场景正在更新时，最好是显示可视指示器。</span><span class="sxs-lookup"><span data-stu-id="989a0-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="989a0-111">有两个选项可用于向用户显示操作正在进行–**进度栏**或**进度环**。</span><span class="sxs-lookup"><span data-stu-id="989a0-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="989a0-112">进度条</span><span class="sxs-lookup"><span data-stu-id="989a0-112">Progress bar</span></span><br>
        <span data-ttu-id="989a0-113">进度栏显示任务完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="989a0-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="989a0-114">它应在持续时间已知（确定性）的操作过程中使用，但是不应阻止用户与应用程序交互。</span><span class="sxs-lookup"><span data-stu-id="989a0-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="989a0-115">*图像： HoloLens 中的进度栏示例*</span><span class="sxs-lookup"><span data-stu-id="989a0-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="989a0-116">![空间](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="989a0-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="989a0-117">HoloLens](images/640px-progressbar.jpg) 中的 ![进度栏示例</span><span class="sxs-lookup"><span data-stu-id="989a0-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="989a0-118">进度环</span><span class="sxs-lookup"><span data-stu-id="989a0-118">Progress ring</span></span><br>
        <span data-ttu-id="989a0-119">进度环仅具有不确定状态，并且在操作完成之前阻止任何其他用户交互时使用。</span><span class="sxs-lookup"><span data-stu-id="989a0-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="989a0-120">*图像： HoloLens 中的进度环形示例*</span><span class="sxs-lookup"><span data-stu-id="989a0-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="989a0-121">![空间](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="989a0-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="989a0-122">HoloLens 中的 ![进度环示例](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="989a0-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="989a0-123">自定义对象的进度</span><span class="sxs-lookup"><span data-stu-id="989a0-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="989a0-124">你可以通过使用你自己的自定义 2D/3D 对象自定义进度控件来添加到应用的个性和品牌标识。</span><span class="sxs-lookup"><span data-stu-id="989a0-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="989a0-125">*Image：自定义网格示例（HoloLens）的进度*</span><span class="sxs-lookup"><span data-stu-id="989a0-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="989a0-126">![空间](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="989a0-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="989a0-127">在 HoloLens 中 ![自定义网格示例的进度](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="989a0-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="989a0-128">最佳做法</span><span class="sxs-lookup"><span data-stu-id="989a0-128">Best practices</span></span>
* <span data-ttu-id="989a0-129">将[billboarding 或标记一起](billboarding-and-tag-along.md)紧密地转换为进度的显示，因为用户可以轻松地将其标头移到空空间，并丢失上下文。</span><span class="sxs-lookup"><span data-stu-id="989a0-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="989a0-130">如果用户无法看到任何内容，你的应用可能看起来好像已崩溃。</span><span class="sxs-lookup"><span data-stu-id="989a0-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="989a0-131">Billboarding 和标记一起内置于 prefab 中。</span><span class="sxs-lookup"><span data-stu-id="989a0-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="989a0-132">提供有关用户发生的情况的状态信息始终是好的。</span><span class="sxs-lookup"><span data-stu-id="989a0-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="989a0-133">进度 prefab 提供了各种视觉样式，包括用于提供状态的 Windows 标准环形类型进度。</span><span class="sxs-lookup"><span data-stu-id="989a0-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="989a0-134">如果希望进度的样式与应用的品牌保持一致，还可以将自定义网格与动画一起使用。</span><span class="sxs-lookup"><span data-stu-id="989a0-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="989a0-135">Unity 的 MRTK （混合现实工具包）中的进度指示器</span><span class="sxs-lookup"><span data-stu-id="989a0-135">Progress indicator in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="989a0-136">MRTK-进度指示器 prototyping</span><span class="sxs-lookup"><span data-stu-id="989a0-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="989a0-137">MRTK-场景转换服务</span><span class="sxs-lookup"><span data-stu-id="989a0-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="989a0-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="989a0-138">See also</span></span>

* [<span data-ttu-id="989a0-139">光标</span><span class="sxs-lookup"><span data-stu-id="989a0-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="989a0-140">手动 ray</span><span class="sxs-lookup"><span data-stu-id="989a0-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="989a0-141">Button</span><span class="sxs-lookup"><span data-stu-id="989a0-141">Button</span></span>](button.md)
* [<span data-ttu-id="989a0-142">可交互对象</span><span class="sxs-lookup"><span data-stu-id="989a0-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="989a0-143">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="989a0-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="989a0-144">起源</span><span class="sxs-lookup"><span data-stu-id="989a0-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="989a0-145">手动菜单</span><span class="sxs-lookup"><span data-stu-id="989a0-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="989a0-146">邻近菜单</span><span class="sxs-lookup"><span data-stu-id="989a0-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="989a0-147">对象集合</span><span class="sxs-lookup"><span data-stu-id="989a0-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="989a0-148">语音命令</span><span class="sxs-lookup"><span data-stu-id="989a0-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="989a0-149">键盘</span><span class="sxs-lookup"><span data-stu-id="989a0-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="989a0-150">提示</span><span class="sxs-lookup"><span data-stu-id="989a0-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="989a0-151">盖板</span><span class="sxs-lookup"><span data-stu-id="989a0-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="989a0-152">滑块</span><span class="sxs-lookup"><span data-stu-id="989a0-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="989a0-153">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="989a0-153">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="989a0-154">显示进度</span><span class="sxs-lookup"><span data-stu-id="989a0-154">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="989a0-155">Surface 磁性</span><span class="sxs-lookup"><span data-stu-id="989a0-155">Surface magnetism</span></span>](surface-magnetism.md)
