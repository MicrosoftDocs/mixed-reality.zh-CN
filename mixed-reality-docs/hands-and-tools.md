---
title: 双手和动作控制器
description: 双手和动作控制器交互的概述
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 混合现实，手、 运动控制器、 交互，设计
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039168"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="0068e-104">双手和动作控制器</span><span class="sxs-lookup"><span data-stu-id="0068e-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="0068e-105">方案</span><span class="sxs-lookup"><span data-stu-id="0068e-105">Scenarios</span></span>
<span data-ttu-id="0068e-106">如果选择读取后采用此交互模型[设计准则](interaction-fundamentals.md)，这意味着您在开发应用程序要求用户使用两只手进行与 holographic 世界交互。</span><span class="sxs-lookup"><span data-stu-id="0068e-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="0068e-107">你的应用程序要实现删除之间虚拟和物理边界的目标。</span><span class="sxs-lookup"><span data-stu-id="0068e-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="0068e-108">某些特定方案可能是：</span><span class="sxs-lookup"><span data-stu-id="0068e-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="0068e-109">提供信息工作人员 2D 虚拟屏幕和 Ui 用于显示和控制内容</span><span class="sxs-lookup"><span data-stu-id="0068e-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="0068e-110">提供第一个行辅助角色教程和工厂的程序集行中的指南</span><span class="sxs-lookup"><span data-stu-id="0068e-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="0068e-111">开发用于协助和培训医疗专业人员的专业工具</span><span class="sxs-lookup"><span data-stu-id="0068e-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="0068e-112">使用 3D 虚拟对象来修饰现实世界，或若要创建第二个世界</span><span class="sxs-lookup"><span data-stu-id="0068e-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="0068e-113">创建位置基于服务和作为背景中使用实际的游戏</span><span class="sxs-lookup"><span data-stu-id="0068e-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="0068e-114">双手和动作控制器模式</span><span class="sxs-lookup"><span data-stu-id="0068e-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="0068e-115">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="0068e-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="0068e-116">这是利用的手，用户了支持的触摸和直接操作全息模态。</span><span class="sxs-lookup"><span data-stu-id="0068e-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="0068e-117">通过 leaveraging 日常生活体验和提供适当的可视化提示，用户就能够使用相同的方法来操作现实世界对象与虚拟的交互。</span><span class="sxs-lookup"><span data-stu-id="0068e-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="0068e-118">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="0068e-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="0068e-119">此模式使用户能够在距离全息与之交互。</span><span class="sxs-lookup"><span data-stu-id="0068e-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="0068e-120">它使用户能够充分利用的周围的环境。</span><span class="sxs-lookup"><span data-stu-id="0068e-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="0068e-121">用户可以在任意位置全息和仍可以从任何距离访问它们。</span><span class="sxs-lookup"><span data-stu-id="0068e-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="0068e-122">心理模型和用于控制和操作 2D 和 3D 全息手势是高度与同步的直接操作。</span><span class="sxs-lookup"><span data-stu-id="0068e-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="0068e-123">运动控制器</span><span class="sxs-lookup"><span data-stu-id="0068e-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="0068e-124">运动控制器是通过使用一个或两个指针时为单位的距离大范围内提供精确交互来扩展用户的物理功能的工具。</span><span class="sxs-lookup"><span data-stu-id="0068e-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="0068e-125">这些硬件附件提供了许多常用的交互，并提供 surefooted、 触觉反馈的各种操作的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="0068e-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="0068e-126">目前，motion 控制器是仅适用于 WMR 方案。</span><span class="sxs-lookup"><span data-stu-id="0068e-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="0068e-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="0068e-127">See also</span></span>
* [<span data-ttu-id="0068e-128">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="0068e-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0068e-129">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="0068e-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="0068e-130">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="0068e-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0068e-131">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="0068e-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="0068e-132">免动手操作</span><span class="sxs-lookup"><span data-stu-id="0068e-132">Hands-free</span></span>](hands-free.md)
