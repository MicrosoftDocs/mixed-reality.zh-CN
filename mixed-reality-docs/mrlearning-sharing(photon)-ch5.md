---
title: 多用户功能教程 - 5. 将 Azure 空间定位点集成到共享体验中
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031695"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="12ff3-105">5.将 Azure 空间定位点集成到共享体验中</span><span class="sxs-lookup"><span data-stu-id="12ff3-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="12ff3-106">本课程介绍如何将 Azure 空间定位点 (ASA) 集成到共享体验中。</span><span class="sxs-lookup"><span data-stu-id="12ff3-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="12ff3-107">如果共置在一起的多个设备的物理环境会锚定虚拟体验，使所有参与者在同一个物理位置看到对象，则 ASA 可让这些设备获得一个公用参照点。</span><span class="sxs-lookup"><span data-stu-id="12ff3-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="12ff3-108">目标</span><span class="sxs-lookup"><span data-stu-id="12ff3-108">Objectives</span></span>

* <span data-ttu-id="12ff3-109">将 ASA 集成到共享体验，以在多个设备上实现对齐。</span><span class="sxs-lookup"><span data-stu-id="12ff3-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="12ff3-110">了解 ASA 在本地共享体验上下文中的基本工作原理。</span><span class="sxs-lookup"><span data-stu-id="12ff3-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="12ff3-111">说明</span><span class="sxs-lookup"><span data-stu-id="12ff3-111">Instructions</span></span>

1. <span data-ttu-id="12ff3-112">选择“MixedRealityPlayspace”父对象下的“TableAnchor”预制件，并将其删除。</span><span class="sxs-lookup"><span data-stu-id="12ff3-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="12ff3-114">在“项目”视图中转到“资产”->“资源”->“预制件”，将“TableAnchor”预制件拖放到“SharedPlayground”对象的顶部，使该预制件成为子级。</span><span class="sxs-lookup"><span data-stu-id="12ff3-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="12ff3-115">展开“MixedRealityPlayspace”父对象、“TableAnchor”对象和“Buttons”对象。</span><span class="sxs-lookup"><span data-stu-id="12ff3-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="12ff3-117">现在，请在层次结构中选择“ShareAzureAnchorButton”，并将注意力转移到“检查器”面板。</span><span class="sxs-lookup"><span data-stu-id="12ff3-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="12ff3-118">向下滚动到下图所示的下拉菜单中，选择“AnchorModuleScript”，然后单击“ShareAnchorNetwork()”。</span><span class="sxs-lookup"><span data-stu-id="12ff3-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="12ff3-120">选择“GetAzureAnchorButton”（参阅步骤 4），并将注意力重新转移到“检查器”面板。</span><span class="sxs-lookup"><span data-stu-id="12ff3-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="12ff3-121">向下滚动到下图所示的下拉菜单，选择“AnchorModuleScript”，单击“GetSharedAnchorNetwork()”，然后保存。</span><span class="sxs-lookup"><span data-stu-id="12ff3-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="12ff3-123">重复步骤 4，将 StartAzureSession () 函数挂接到 StartAzureSessionButton。</span><span class="sxs-lookup"><span data-stu-id="12ff3-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="12ff3-124">重复步骤 4，将 CreateAzureAnchor () 函数挂接到 CreateAzureAnchorButton，并确认 TableAnchor 对象是否已分配到该函数的“游戏对象”参数字段。</span><span class="sxs-lookup"><span data-stu-id="12ff3-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="12ff3-125">按照[将场景连接到 Azure 资源](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource)中的说明添加 Azure 空间定位点服务凭据。</span><span class="sxs-lookup"><span data-stu-id="12ff3-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="12ff3-126">若要测试共享模块，请单击“启动 Azure ASA 会话”按钮启动 Azure 空间定位点会话，然后单击“创建 Azure 定位点”按钮创建 Azure 定位点。</span><span class="sxs-lookup"><span data-stu-id="12ff3-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="12ff3-127">等待 Azure 定位点创建完成。</span><span class="sxs-lookup"><span data-stu-id="12ff3-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="12ff3-128">创建 Azure 定位点后，单击“共享 Azure 定位点”按钮从 HoloLens 共享创建的 Azure 定位点。</span><span class="sxs-lookup"><span data-stu-id="12ff3-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="12ff3-129">若要在另一个 HoloLens 中接收共享的 Azure 定位点，请单击“启动 Azure ASA 会话”以启动并进入当前的 ASA 会话</span><span class="sxs-lookup"><span data-stu-id="12ff3-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="12ff3-130">单击“获取 Azure 定位点”按钮以从另一个 HoloLens 获取共享的 Azure 定位点。</span><span class="sxs-lookup"><span data-stu-id="12ff3-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="12ff3-131">祝贺</span><span class="sxs-lookup"><span data-stu-id="12ff3-131">Congratulations</span></span>

<span data-ttu-id="12ff3-132">在本课程中，你已了解如何集成 Azure 中强大的新空间定位点功能，以在共享体验中对齐共置的设备！</span><span class="sxs-lookup"><span data-stu-id="12ff3-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="12ff3-133">共享模块教程也到此结束。</span><span class="sxs-lookup"><span data-stu-id="12ff3-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="12ff3-134">我们已学会了如何设置新的 Photon 帐户、将 Photon 和 PUN 集成到新的 Unity 应用程序中、配置头像和共享的对象，并最终使用 ASA 来对齐多个参与者。</span><span class="sxs-lookup"><span data-stu-id="12ff3-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
