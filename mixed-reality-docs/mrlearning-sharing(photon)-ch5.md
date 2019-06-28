---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 941bdc64ed614d5ce71f58f05585d0dfc86c3bb7
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415928"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="8e28e-104">Azure 空间的定位点和分享的经验</span><span class="sxs-lookup"><span data-stu-id="8e28e-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="8e28e-105">在本课中，我们将了解如何将 Azure 空间的定位点 (ASA) 集成到我们的共享体验。</span><span class="sxs-lookup"><span data-stu-id="8e28e-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="8e28e-106">ASA 允许多个共置的设备具有达成共识，如果其物理环境以定位虚拟体验，以便所有参与者都看到同一个物理位置中的对象。</span><span class="sxs-lookup"><span data-stu-id="8e28e-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="8e28e-107">在继续之前本课程中，我们将需要完成 ASA 学习模块，将介绍 ASA 基础知识、 Azure 帐户和资源创建和其他基本建筑物块之前我们可以将 ASA 集成到我们的共享体验所需的。</span><span class="sxs-lookup"><span data-stu-id="8e28e-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="8e28e-108">目标：</span><span class="sxs-lookup"><span data-stu-id="8e28e-108">Objectives:</span></span>

- <span data-ttu-id="8e28e-109">将 ASA 集成到多设备对齐方式的共享体验</span><span class="sxs-lookup"><span data-stu-id="8e28e-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="8e28e-110">了解 ASA 本地共享体验的上下文中的工作原理的基础知识</span><span class="sxs-lookup"><span data-stu-id="8e28e-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="8e28e-111">说明</span><span class="sxs-lookup"><span data-stu-id="8e28e-111">Instructions</span></span>

1. <span data-ttu-id="8e28e-112">从上一课 （控制 + S） 保存项目并将其命名"HLSharedProjectMainPart5.unity"以便更轻松地查找当你再次需要。</span><span class="sxs-lookup"><span data-stu-id="8e28e-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="8e28e-113">选择 TableAnchor 预设可下方"MixedRealityPlayspace"父对象，并将其删除。</span><span class="sxs-lookup"><span data-stu-id="8e28e-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="8e28e-115">在项目视图，转到资产 > 资源 > 预设和拖动 TableAnchor prefab SharedPlayground 对象以使其成为子之上。</span><span class="sxs-lookup"><span data-stu-id="8e28e-115">In the Project view go to Assets > Resources > Prefabs and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="8e28e-116">展开"MixedRealityPlayspace"父对象，则"TableAnchor"对象，并展开"按钮"对象。</span><span class="sxs-lookup"><span data-stu-id="8e28e-116">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="8e28e-118">现在在层次结构中，选择"ShareAzureAnchorButton"并移动到检查器面板关注。</span><span class="sxs-lookup"><span data-stu-id="8e28e-118">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="8e28e-119">向下滚动到，如下图所示的下拉列表菜单并选择"AnchorModuleScript"，然后单击"ShareAnchorNetework()。"</span><span class="sxs-lookup"><span data-stu-id="8e28e-119">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="8e28e-121">类似于步骤 4 中，选择"GetAzureAnchorButton"并将返回到检查器面板关注。</span><span class="sxs-lookup"><span data-stu-id="8e28e-121">Much like step 4, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="8e28e-122">向下滚动到，如下图所示的下拉列表菜单并选择"AnchorModuleScript"，然后单击"GetSharedAnchorNetwork()。"</span><span class="sxs-lookup"><span data-stu-id="8e28e-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="8e28e-123">然后保存。</span><span class="sxs-lookup"><span data-stu-id="8e28e-123">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="8e28e-125">祝贺</span><span class="sxs-lookup"><span data-stu-id="8e28e-125">Congratulations</span></span>

<span data-ttu-id="8e28e-126">本课程中您学习了如何将集成 Azure 的功能强大的新空间定位标记对齐归置的设备中的共享体验 ！</span><span class="sxs-lookup"><span data-stu-id="8e28e-126">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="8e28e-127">本课程还得出结论共享模块。</span><span class="sxs-lookup"><span data-stu-id="8e28e-127">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="8e28e-128">配置虚拟形象和共享的对象，并最后对齐多个参与者使用 ASA，我们了解到如何设置新的 Photon 帐户，请将 Photon 和俏皮话集成到新的 Unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="8e28e-128">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

