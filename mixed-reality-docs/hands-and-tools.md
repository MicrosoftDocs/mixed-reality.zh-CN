---
title: 双手和运动控制器
description: 双手和运动控制器交互概述
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 混合现实, 动手, 运动控制器, 交互, 设计
ms.openlocfilehash: b6efb0a9651cad8eee9b80bb130aa1a85b9a9941
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507872"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="700cf-104">双手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="700cf-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="700cf-105">方案</span><span class="sxs-lookup"><span data-stu-id="700cf-105">Scenarios</span></span>
<span data-ttu-id="700cf-106">如果在阅读[设计准则](interaction-fundamentals.md)后选择采用此交互模型, 这意味着您正在开发一个应用程序, 要求用户使用两次手与全息世界交互。</span><span class="sxs-lookup"><span data-stu-id="700cf-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="700cf-107">您的应用程序将实现删除虚拟与物理之间的 boundry 的目标。</span><span class="sxs-lookup"><span data-stu-id="700cf-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="700cf-108">某些特定情况可能如下:</span><span class="sxs-lookup"><span data-stu-id="700cf-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="700cf-109">为信息工作者提供2D 虚拟屏幕和 Ui 以显示和控制内容</span><span class="sxs-lookup"><span data-stu-id="700cf-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="700cf-110">在工厂组装行中提供第一行工作人员教程和指南</span><span class="sxs-lookup"><span data-stu-id="700cf-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="700cf-111">开发用于帮助和教育医疗专业人员的专业工具</span><span class="sxs-lookup"><span data-stu-id="700cf-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="700cf-112">使用3D 虚拟对象装饰现实世界, 或创建另一个世界</span><span class="sxs-lookup"><span data-stu-id="700cf-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="700cf-113">使用现实世界作为背景创建基于位置的服务和游戏</span><span class="sxs-lookup"><span data-stu-id="700cf-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="700cf-114">双手和运动控制器情态</span><span class="sxs-lookup"><span data-stu-id="700cf-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="700cf-115">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="700cf-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="700cf-116">这是一种使用手的强大功能的模态, 用户可以直接接触和操作全息影像。</span><span class="sxs-lookup"><span data-stu-id="700cf-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="700cf-117">通过 leaveraging 日常生活经验并提供适当的视觉实用, 用户可以使用与虚拟对象交互的相同方式来与虚拟对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="700cf-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="700cf-118">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="700cf-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="700cf-119">这种模态使用户能够在远处与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="700cf-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="700cf-120">它使用户能够充分利用环境。</span><span class="sxs-lookup"><span data-stu-id="700cf-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="700cf-121">用户可以在任何位置放置全息影像, 还可以从任意距离访问。</span><span class="sxs-lookup"><span data-stu-id="700cf-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="700cf-122">用于控制和操作2D 和3D 全息影像的心理模型和手势与直接操作的情况有关。</span><span class="sxs-lookup"><span data-stu-id="700cf-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="700cf-123">运动控制器</span><span class="sxs-lookup"><span data-stu-id="700cf-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="700cf-124">运动控制器是通过在使用一种或两种手时跨大量距离提供精确交互来扩展用户的物理功能的工具。</span><span class="sxs-lookup"><span data-stu-id="700cf-124">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="700cf-125">这些硬件附件提供了许多常用交互的快捷方式, 并为各种操作提供了 surefooted、tactile 的反馈。</span><span class="sxs-lookup"><span data-stu-id="700cf-125">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="700cf-126">目前, 运动控制器仅适用于 Windows Mixed Reality (WMR) 方案。</span><span class="sxs-lookup"><span data-stu-id="700cf-126">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 

![双手和运动控制器的比较情态](images/Hands-and-controllers-720px.jpg)<br>

<span data-ttu-id="700cf-128">*双手和运动控制器的比较情态*</span><span class="sxs-lookup"><span data-stu-id="700cf-128">*Comparison of hands and motion controllers modalities*</span></span>

## <a name="see-also"></a><span data-ttu-id="700cf-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="700cf-129">See also</span></span>
* [<span data-ttu-id="700cf-130">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="700cf-130">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="700cf-131">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="700cf-131">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="700cf-132">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="700cf-132">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="700cf-133">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="700cf-133">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="700cf-134">免动手操作</span><span class="sxs-lookup"><span data-stu-id="700cf-134">Hands-free</span></span>](hands-free.md)
