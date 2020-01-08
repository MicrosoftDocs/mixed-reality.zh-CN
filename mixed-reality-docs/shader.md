---
title: 着色器
description: MRTK 标准着色器提供各种类型的视觉效果，可与全息影像一起使用。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合现实、控件、交互、ui、ux
ms.openlocfilehash: 4d95e335b3f7020766beae916423d0588ee66572
ms.sourcegitcommit: 270ca09ec61e1153a83cf44942d7ba3783ef1805
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694161"
---
# <a name="shader"></a><span data-ttu-id="585c0-104">着色器</span><span class="sxs-lookup"><span data-stu-id="585c0-104">Shader</span></span>

![着色器](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="585c0-106">由于全息对象与环境中的物理对象混合在一起，因此在混合现实中提供视觉提示非常重要。</span><span class="sxs-lookup"><span data-stu-id="585c0-106">Since holographic objects are mixed with the physical ones in the environment, it's important to provide visual cues in mixed reality.</span></span> <span data-ttu-id="585c0-107">MRTK 标准着色器提供各种类型的视觉效果，可与全息影像一起使用。</span><span class="sxs-lookup"><span data-stu-id="585c0-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="585c0-108">MRTK 标准着色系统利用可实现类似于 Unity 标准着色器的视觉对象，实现[流畅的设计系统原则](https://www.microsoft.com/design/fluent/#/)，并使混合现实设备保持高性能。</span><span class="sxs-lookup"><span data-stu-id="585c0-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="585c0-109">使用 MRTK 标准着色器的视觉效果示例</span><span class="sxs-lookup"><span data-stu-id="585c0-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="585c0-110">![移动](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="585c0-110">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="585c0-111">**邻近感应**</span><span class="sxs-lookup"><span data-stu-id="585c0-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="585c0-112">![旋转](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="585c0-112">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="585c0-113">**边框细**</span><span class="sxs-lookup"><span data-stu-id="585c0-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="585c0-114">用于 Unity 的 MRTK 中的 MRTK 标准着色器（混合现实工具包）</span><span class="sxs-lookup"><span data-stu-id="585c0-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="585c0-115">MRTK-标准着色器</span><span class="sxs-lookup"><span data-stu-id="585c0-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="585c0-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="585c0-116">See also</span></span>

* [<span data-ttu-id="585c0-117">光标</span><span class="sxs-lookup"><span data-stu-id="585c0-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="585c0-118">手部射线</span><span class="sxs-lookup"><span data-stu-id="585c0-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="585c0-119">Button</span><span class="sxs-lookup"><span data-stu-id="585c0-119">Button</span></span>](button.md)
* [<span data-ttu-id="585c0-120">可交互对象</span><span class="sxs-lookup"><span data-stu-id="585c0-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="585c0-121">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="585c0-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="585c0-122">操作</span><span class="sxs-lookup"><span data-stu-id="585c0-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="585c0-123">手动菜单</span><span class="sxs-lookup"><span data-stu-id="585c0-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="585c0-124">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="585c0-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="585c0-125">对象集合</span><span class="sxs-lookup"><span data-stu-id="585c0-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="585c0-126">语音命令</span><span class="sxs-lookup"><span data-stu-id="585c0-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="585c0-127">键盘</span><span class="sxs-lookup"><span data-stu-id="585c0-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="585c0-128">工具提示</span><span class="sxs-lookup"><span data-stu-id="585c0-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="585c0-129">平板</span><span class="sxs-lookup"><span data-stu-id="585c0-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="585c0-130">滑块</span><span class="sxs-lookup"><span data-stu-id="585c0-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="585c0-131">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="585c0-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="585c0-132">显示进度</span><span class="sxs-lookup"><span data-stu-id="585c0-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="585c0-133">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="585c0-133">Surface magnetism</span></span>](surface-magnetism.md)
