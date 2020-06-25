---
title: 空间网格可视化
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合现实，HoloLens，UI 控件，交互，UI，ux，UX 设计，空间 UI，空间交互，3D UI，三维 UX
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346100"
---
# <a name="spatial-mesh"></a><span data-ttu-id="3adf6-103">空间网格</span><span class="sxs-lookup"><span data-stu-id="3adf6-103">Spatial mesh</span></span>

![空间网格](images/UX/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="3adf6-105">通过空间网格可视化，用户可以了解设备如何感觉并了解物理环境。</span><span class="sxs-lookup"><span data-stu-id="3adf6-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="3adf6-106">除了提供空间上下文，适当的空间网格可视化还可以创建不知和神奇体验。</span><span class="sxs-lookup"><span data-stu-id="3adf6-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="3adf6-107">设计准则</span><span class="sxs-lookup"><span data-stu-id="3adf6-107">Design guideline</span></span>
<span data-ttu-id="3adf6-108">由于使用户能够专注于内容并与之交互非常重要，因此，背景中的空间网格的连续和重复的可视化效果可能会分散注意力。</span><span class="sxs-lookup"><span data-stu-id="3adf6-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="3adf6-109">建议你慎用环境，只是在初始启动时，或者当用户通过定位和轻攻区来查看环境网格时出现清楚的意图。</span><span class="sxs-lookup"><span data-stu-id="3adf6-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="3adf6-110">您可以在 HoloLens shell 中观察到此行为。</span><span class="sxs-lookup"><span data-stu-id="3adf6-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="3adf6-111">适用于 Unity 的 MRTK （混合现实工具包）中的空间网格可视化</span><span class="sxs-lookup"><span data-stu-id="3adf6-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="3adf6-112">MRTK 提供了多个材料来实现空间网格可视化。</span><span class="sxs-lookup"><span data-stu-id="3adf6-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="3adf6-113">**MRTK_Wireframe，MRTK_Wireframe**的：默认静态空间网格材料，它显示网格轮廓而不显示动画。</span><span class="sxs-lookup"><span data-stu-id="3adf6-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="3adf6-114">此材料可用于调试目的，因为它显示了整个空间网格几何。</span><span class="sxs-lookup"><span data-stu-id="3adf6-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="3adf6-115">但是，不建议在生产环境中使用。</span><span class="sxs-lookup"><span data-stu-id="3adf6-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="3adf6-116">**MRTK_SurfaceReconstruction**材料：此材料在空间网格上提供动画脉冲效果。</span><span class="sxs-lookup"><span data-stu-id="3adf6-116">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="3adf6-117">你可以使用此材料在你的体验的特定时刻或用户的点击输入中直观显示环境。</span><span class="sxs-lookup"><span data-stu-id="3adf6-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="3adf6-118">有关示例，请参阅**PulseShaderExamples**场景。</span><span class="sxs-lookup"><span data-stu-id="3adf6-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="3adf6-119">有关更多详细信息，请参阅[MRTK-空间感知](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html)和[MRTK 着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html)。</span><span class="sxs-lookup"><span data-stu-id="3adf6-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="3adf6-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3adf6-120">See also</span></span>

* [<span data-ttu-id="3adf6-121">光标</span><span class="sxs-lookup"><span data-stu-id="3adf6-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="3adf6-122">手部射线</span><span class="sxs-lookup"><span data-stu-id="3adf6-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="3adf6-123">Button</span><span class="sxs-lookup"><span data-stu-id="3adf6-123">Button</span></span>](button.md)
* [<span data-ttu-id="3adf6-124">可交互对象</span><span class="sxs-lookup"><span data-stu-id="3adf6-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="3adf6-125">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="3adf6-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="3adf6-126">操作</span><span class="sxs-lookup"><span data-stu-id="3adf6-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3adf6-127">手动菜单</span><span class="sxs-lookup"><span data-stu-id="3adf6-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="3adf6-128">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="3adf6-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="3adf6-129">对象集合</span><span class="sxs-lookup"><span data-stu-id="3adf6-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="3adf6-130">语音命令</span><span class="sxs-lookup"><span data-stu-id="3adf6-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="3adf6-131">键盘</span><span class="sxs-lookup"><span data-stu-id="3adf6-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="3adf6-132">工具提示</span><span class="sxs-lookup"><span data-stu-id="3adf6-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="3adf6-133">平板</span><span class="sxs-lookup"><span data-stu-id="3adf6-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="3adf6-134">滑块</span><span class="sxs-lookup"><span data-stu-id="3adf6-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="3adf6-135">着色器</span><span class="sxs-lookup"><span data-stu-id="3adf6-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="3adf6-136">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="3adf6-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="3adf6-137">显示进度</span><span class="sxs-lookup"><span data-stu-id="3adf6-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="3adf6-138">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="3adf6-138">Surface magnetism</span></span>](surface-magnetism.md)
