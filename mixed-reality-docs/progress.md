---
title: 显示进度
description: 进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 控件、 ui 和 ux
ms.openlocfilehash: 9edddc7800f0d7334d1ceba97b9a06fd6d4580ac
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592640"
---
# <a name="displaying-progress"></a><span data-ttu-id="cdc7e-104">显示进度</span><span class="sxs-lookup"><span data-stu-id="cdc7e-104">Displaying progress</span></span>

<span data-ttu-id="cdc7e-105">进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="cdc7e-106">这意味着，在进度指示器可见，并且还可以根据所使用的指示器指示等待时长时，用户无法与该应用交互。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="cdc7e-107">![在 HoloLens 进度环示例](images/640px-progress-hero.jpg)</span><span class="sxs-lookup"><span data-stu-id="cdc7e-107">![Progress ring example in HoloLens](images/640px-progress-hero.jpg)</span></span><br>
<span data-ttu-id="cdc7e-108">*在 HoloLens 进度环示例*</span><span class="sxs-lookup"><span data-stu-id="cdc7e-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="cdc7e-109">进度类型</span><span class="sxs-lookup"><span data-stu-id="cdc7e-109">Types of progress</span></span>

<span data-ttu-id="cdc7e-110">请务必提供有关发生了什么情况的用户信息。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="cdc7e-111">混合现实中的用户可以轻松地分心物理环境或对象如果您的应用程序不会不提供很好可视反馈。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="cdc7e-112">对于需要几秒钟的情况下，更新此类加载数据时或场景，而是显示可视的指示器的好办法。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="cdc7e-113">有两个选项向用户显示操作正在进行 –**进度栏**或**进度环**。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="cdc7e-114">进度栏</span><span class="sxs-lookup"><span data-stu-id="cdc7e-114">Progress bar</span></span>

![在 HoloLens 的进度栏示例](images/640px-progressbar.jpg)

<span data-ttu-id="cdc7e-116">进度栏显示的任务已完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="cdc7e-117">它应在其持续时间已知 （确定），操作过程中，但其进度不应阻止与应用的用户的交互。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="cdc7e-118">进度环</span><span class="sxs-lookup"><span data-stu-id="cdc7e-118">Progress ring</span></span>

![在 HoloLens 进度环示例](images/640px-progressring.jpg)

<span data-ttu-id="cdc7e-120">采用进度环仅拥有不确定状态，并阻止任何进一步的用户交互，直到操作完成时，应使用。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="cdc7e-121">与自定义对象的进度</span><span class="sxs-lookup"><span data-stu-id="cdc7e-121">Progress with a custom object</span></span>

![使用自定义网格示例中 HoloLens 进度](images/640px-progresscustom.jpg)

<span data-ttu-id="cdc7e-123">可以通过自定义您自己自定义的二维/三维对象将进度控件添加到你的应用的个性和品牌标识。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="cdc7e-124">最佳做法</span><span class="sxs-lookup"><span data-stu-id="cdc7e-124">Best practices</span></span>
* <span data-ttu-id="cdc7e-125">紧密耦合[公告板或尾随](billboarding-and-tag-along.md)用于显示进度，因为用户可以轻松地将其头移到空白区域，并会丢失上下文。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="cdc7e-126">您的应用程序可能看起来它已崩溃如果用户无法看到任何内容。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="cdc7e-127">Billboarding 和尾随内置进度预设。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="cdc7e-128">最好始终提供有关用户所发生的状态信息。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="cdc7e-129">进度预设可提供各种视觉样式，包括提供状态的 Windows 标准的环式类型进度。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="cdc7e-130">如果您希望的样式的进度以与你的应用的品牌保持一致，还可以通过将动画使用自定义的网格。</span><span class="sxs-lookup"><span data-stu-id="cdc7e-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdc7e-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="cdc7e-131">See also</span></span>
* [<span data-ttu-id="cdc7e-132">脚本和混合现实工具包进度的预设</span><span class="sxs-lookup"><span data-stu-id="cdc7e-132">Scripts and prefabs for Progress on Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ProgressExample.md)
* [<span data-ttu-id="cdc7e-133">种交互的对象</span><span class="sxs-lookup"><span data-stu-id="cdc7e-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="cdc7e-134">对象集合</span><span class="sxs-lookup"><span data-stu-id="cdc7e-134">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="cdc7e-135">公告板和尾随</span><span class="sxs-lookup"><span data-stu-id="cdc7e-135">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
