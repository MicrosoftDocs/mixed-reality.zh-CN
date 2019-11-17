---
title: 着色器
description: ''
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合现实、控件、交互、ui、ux
ms.openlocfilehash: 23371ae5d70e5e792415fd25c0d58def0a7cefbb
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143267"
---
# <a name="shader"></a><span data-ttu-id="1ae63-103">着色器</span><span class="sxs-lookup"><span data-stu-id="1ae63-103">Shader</span></span>

![着色器](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="1ae63-105">由于全息对象与环境中的物理对象混合在一起，因此提供视觉提示在混合现实中非常重要。</span><span class="sxs-lookup"><span data-stu-id="1ae63-105">Since holographic objects are mixed with the physical ones in the environment, providing visual cue is important in mixed reality.</span></span> <span data-ttu-id="1ae63-106">MRTK 标准着色器提供各种类型的视觉效果，可与全息影像一起使用。</span><span class="sxs-lookup"><span data-stu-id="1ae63-106">MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="1ae63-107">MRTK 标准底纹系统利用单个灵活的着色器，它可以实现类似于 Unity 的标准着色器的视觉对象，实现流畅的设计系统原则，并在混合现实设备上保持高性能。</span><span class="sxs-lookup"><span data-stu-id="1ae63-107">MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implement Fluent Design System principles, and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="1ae63-108">使用 MRTK 标准着色器的视觉效果示例</span><span class="sxs-lookup"><span data-stu-id="1ae63-108">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="1ae63-109">![移动](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="1ae63-109">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="1ae63-110">**邻近感应**</span><span class="sxs-lookup"><span data-stu-id="1ae63-110">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="1ae63-111">![旋转](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="1ae63-111">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="1ae63-112">**边框细**</span><span class="sxs-lookup"><span data-stu-id="1ae63-112">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

---

## <a name="mrtk-standard-shader-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="1ae63-113">用于 Unity 的 MRTK 中的 MRTK 标准着色器（混合现实工具包）</span><span class="sxs-lookup"><span data-stu-id="1ae63-113">MRTK Standard shader in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="1ae63-114">MRTK-标准着色器</span><span class="sxs-lookup"><span data-stu-id="1ae63-114">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="1ae63-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ae63-115">See also</span></span>

* [<span data-ttu-id="1ae63-116">光标</span><span class="sxs-lookup"><span data-stu-id="1ae63-116">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1ae63-117">手动 ray</span><span class="sxs-lookup"><span data-stu-id="1ae63-117">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="1ae63-118">Button</span><span class="sxs-lookup"><span data-stu-id="1ae63-118">Button</span></span>](button.md)
* [<span data-ttu-id="1ae63-119">可交互对象</span><span class="sxs-lookup"><span data-stu-id="1ae63-119">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1ae63-120">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="1ae63-120">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="1ae63-121">起源</span><span class="sxs-lookup"><span data-stu-id="1ae63-121">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1ae63-122">手动菜单</span><span class="sxs-lookup"><span data-stu-id="1ae63-122">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="1ae63-123">邻近菜单</span><span class="sxs-lookup"><span data-stu-id="1ae63-123">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="1ae63-124">对象集合</span><span class="sxs-lookup"><span data-stu-id="1ae63-124">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="1ae63-125">语音命令</span><span class="sxs-lookup"><span data-stu-id="1ae63-125">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="1ae63-126">键盘</span><span class="sxs-lookup"><span data-stu-id="1ae63-126">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="1ae63-127">提示</span><span class="sxs-lookup"><span data-stu-id="1ae63-127">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="1ae63-128">盖板</span><span class="sxs-lookup"><span data-stu-id="1ae63-128">Slate</span></span>](slate.md)
* [<span data-ttu-id="1ae63-129">滑块</span><span class="sxs-lookup"><span data-stu-id="1ae63-129">Slider</span></span>](slider.md)
* [<span data-ttu-id="1ae63-130">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="1ae63-130">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="1ae63-131">显示进度</span><span class="sxs-lookup"><span data-stu-id="1ae63-131">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="1ae63-132">Surface 磁性</span><span class="sxs-lookup"><span data-stu-id="1ae63-132">Surface magnetism</span></span>](surface-magnetism.md)
