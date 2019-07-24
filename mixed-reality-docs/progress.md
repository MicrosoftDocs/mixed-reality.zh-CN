---
title: 显示进度
description: 进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 设计, 控件, ui, ux
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523260"
---
# <a name="displaying-progress"></a><span data-ttu-id="ee276-104">显示进度</span><span class="sxs-lookup"><span data-stu-id="ee276-104">Displaying progress</span></span>

<span data-ttu-id="ee276-105">进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。</span><span class="sxs-lookup"><span data-stu-id="ee276-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="ee276-106">这意味着，在进度指示器可见，并且还可以根据所使用的指示器指示等待时长时，用户无法与该应用交互。</span><span class="sxs-lookup"><span data-stu-id="ee276-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="ee276-107">![HoloLens 中的进度环示例](images/HoloLens2_Loader.gif)</span><span class="sxs-lookup"><span data-stu-id="ee276-107">![Progress ring example in HoloLens](images/HoloLens2_Loader.gif)</span></span><br>
<span data-ttu-id="ee276-108">*HoloLens 中的进度环示例*</span><span class="sxs-lookup"><span data-stu-id="ee276-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="ee276-109">进度类型</span><span class="sxs-lookup"><span data-stu-id="ee276-109">Types of progress</span></span>

<span data-ttu-id="ee276-110">向用户提供有关发生的情况的信息非常重要。</span><span class="sxs-lookup"><span data-stu-id="ee276-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="ee276-111">在混合现实中, 如果你的应用程序没有提供良好的视觉反馈, 则可以轻松地在物理环境或对象上对其进行工作。</span><span class="sxs-lookup"><span data-stu-id="ee276-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="ee276-112">对于需要几秒钟时间的情况, 例如, 当加载数据或场景正在更新时, 最好是显示可视指示器。</span><span class="sxs-lookup"><span data-stu-id="ee276-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="ee276-113">有两个选项可用于向用户显示操作正在进行–**进度栏**或**进度环**。</span><span class="sxs-lookup"><span data-stu-id="ee276-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="ee276-114">进度栏</span><span class="sxs-lookup"><span data-stu-id="ee276-114">Progress bar</span></span>

![HoloLens 中的进度栏示例](images/640px-progressbar.jpg)

<span data-ttu-id="ee276-116">进度栏显示任务完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="ee276-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="ee276-117">它应在持续时间已知 (确定性) 的操作过程中使用, 但是不应阻止用户与应用程序交互。</span><span class="sxs-lookup"><span data-stu-id="ee276-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="ee276-118">进度环</span><span class="sxs-lookup"><span data-stu-id="ee276-118">Progress ring</span></span>

![HoloLens 中的进度环示例](images/640px-progressring.jpg)

<span data-ttu-id="ee276-120">进度环仅具有不确定状态, 并且在操作完成之前阻止任何其他用户交互时使用。</span><span class="sxs-lookup"><span data-stu-id="ee276-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="ee276-121">自定义对象的进度</span><span class="sxs-lookup"><span data-stu-id="ee276-121">Progress with a custom object</span></span>

![HoloLens 中的自定义网格示例的进度](images/640px-progresscustom.jpg)

<span data-ttu-id="ee276-123">你可以通过使用你自己的自定义 2D/3D 对象自定义进度控件来添加到应用的个性和品牌标识。</span><span class="sxs-lookup"><span data-stu-id="ee276-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="ee276-124">最佳实践</span><span class="sxs-lookup"><span data-stu-id="ee276-124">Best practices</span></span>
* <span data-ttu-id="ee276-125">将[billboarding 或标记一起](billboarding-and-tag-along.md)紧密地转换为进度的显示, 因为用户可以轻松地将其标头移到空空间, 并丢失上下文。</span><span class="sxs-lookup"><span data-stu-id="ee276-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="ee276-126">如果用户无法看到任何内容, 你的应用可能看起来好像已崩溃。</span><span class="sxs-lookup"><span data-stu-id="ee276-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="ee276-127">Billboarding 和标记一起内置于 prefab 中。</span><span class="sxs-lookup"><span data-stu-id="ee276-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="ee276-128">提供有关用户发生的情况的状态信息始终是好的。</span><span class="sxs-lookup"><span data-stu-id="ee276-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="ee276-129">进度 prefab 提供了各种视觉样式, 包括用于提供状态的 Windows 标准环形类型进度。</span><span class="sxs-lookup"><span data-stu-id="ee276-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="ee276-130">如果希望进度的样式与应用的品牌保持一致, 还可以将自定义网格与动画一起使用。</span><span class="sxs-lookup"><span data-stu-id="ee276-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee276-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="ee276-131">See also</span></span>
* [<span data-ttu-id="ee276-132">混合现实工具包的进度脚本和 prototyping</span><span class="sxs-lookup"><span data-stu-id="ee276-132">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="ee276-133">边界框</span><span class="sxs-lookup"><span data-stu-id="ee276-133">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ee276-134">可交互对象</span><span class="sxs-lookup"><span data-stu-id="ee276-134">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ee276-135">对象集合</span><span class="sxs-lookup"><span data-stu-id="ee276-135">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="ee276-136">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="ee276-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
