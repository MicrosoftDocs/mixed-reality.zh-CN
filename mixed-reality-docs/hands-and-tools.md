---
title: 双手和运动控制器
description: 双手和运动控制器交互概述
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 混合现实, 动手, 运动控制器, 交互, 设计
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039168"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="e5dc6-104">双手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="e5dc6-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="e5dc6-105">方案</span><span class="sxs-lookup"><span data-stu-id="e5dc6-105">Scenarios</span></span>
<span data-ttu-id="e5dc6-106">如果在阅读[设计准则](interaction-fundamentals.md)后选择采用此交互模型, 这意味着您正在开发一个应用程序, 要求用户使用两次手与全息世界交互。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="e5dc6-107">您的应用程序将实现删除虚拟与物理之间的 boundry 的目标。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="e5dc6-108">某些特定情况可能如下:</span><span class="sxs-lookup"><span data-stu-id="e5dc6-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="e5dc6-109">为信息工作者提供2D 虚拟屏幕和 Ui 以显示和控制内容</span><span class="sxs-lookup"><span data-stu-id="e5dc6-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="e5dc6-110">在工厂组装行中提供第一行工作人员教程和指南</span><span class="sxs-lookup"><span data-stu-id="e5dc6-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="e5dc6-111">开发用于帮助和教育医疗专业人员的专业工具</span><span class="sxs-lookup"><span data-stu-id="e5dc6-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="e5dc6-112">使用3D 虚拟对象装饰现实世界, 或创建另一个世界</span><span class="sxs-lookup"><span data-stu-id="e5dc6-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="e5dc6-113">使用现实世界作为背景创建基于位置的服务和游戏</span><span class="sxs-lookup"><span data-stu-id="e5dc6-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="e5dc6-114">双手和运动控制器情态</span><span class="sxs-lookup"><span data-stu-id="e5dc6-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="e5dc6-115">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="e5dc6-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="e5dc6-116">这是一种使用手的强大功能的模态, 用户可以直接接触和操作全息影像。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="e5dc6-117">通过 leaveraging 日常生活经验并提供适当的视觉实用, 用户可以使用与虚拟对象交互的相同方式来与虚拟对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="e5dc6-118">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="e5dc6-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="e5dc6-119">这种模态使用户能够在远处与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="e5dc6-120">它使用户能够充分利用环境。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="e5dc6-121">用户可以在任何位置放置全息影像, 还可以从任意距离访问。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="e5dc6-122">用于控制和操作2D 和3D 全息影像的心理模型和手势与直接操作的情况有关。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="e5dc6-123">运动控制器</span><span class="sxs-lookup"><span data-stu-id="e5dc6-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="e5dc6-124">运动控制器是通过在使用一种或两种手时跨大量距离提供精确交互来扩展用户的物理功能的工具。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="e5dc6-125">这些硬件附件提供了许多常用交互的快捷方式, 并为各种操作提供了 surefooted、tactile 的反馈。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="e5dc6-126">目前, 运动控制器仅适用于 WMR 方案。</span><span class="sxs-lookup"><span data-stu-id="e5dc6-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="e5dc6-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="e5dc6-127">See also</span></span>
* [<span data-ttu-id="e5dc6-128">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="e5dc6-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e5dc6-129">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="e5dc6-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e5dc6-130">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="e5dc6-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e5dc6-131">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="e5dc6-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="e5dc6-132">免动手操作</span><span class="sxs-lookup"><span data-stu-id="e5dc6-132">Hands-free</span></span>](hands-free.md)
