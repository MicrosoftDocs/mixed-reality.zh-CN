---
title: 多用户功能教程-5。 将 Azure 空间锚点集成到共享体验中
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b83c7ac39d522fc2b799591fa02608d5fc5cc930
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437566"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="626f5-105">5. 将 Azure 空间锚点集成到共享体验中</span><span class="sxs-lookup"><span data-stu-id="626f5-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="626f5-106">在本课程中，我们将了解如何将 Azure 空间锚点（ASA）集成到我们的共享体验中。</span><span class="sxs-lookup"><span data-stu-id="626f5-106">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="626f5-107">如果其物理环境要锚定虚拟体验，使多个归置的设备在其物理环境中能够看到相同的物理位置中的对象，则可以使用这些设备。</span><span class="sxs-lookup"><span data-stu-id="626f5-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="626f5-108">在继续学习本课程之前，我们需要完成 ASA 学习模块，该模块将涵盖 ASA 基础知识、Azure 帐户和资源创建，以及在我们可以将 ASA 集成到我们的共享体验之前所需的其他基本建筑物块。</span><span class="sxs-lookup"><span data-stu-id="626f5-108">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="626f5-109">目标</span><span class="sxs-lookup"><span data-stu-id="626f5-109">Objectives:</span></span>

- <span data-ttu-id="626f5-110">将 ASA 集成到多设备对齐的共享体验。</span><span class="sxs-lookup"><span data-stu-id="626f5-110">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="626f5-111">了解 ASA 在本地共享体验环境中的工作原理的基础知识。</span><span class="sxs-lookup"><span data-stu-id="626f5-111">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="626f5-112">说明</span><span class="sxs-lookup"><span data-stu-id="626f5-112">Instructions</span></span>

1. <span data-ttu-id="626f5-113">保存上一课中的项目（ctrl + S）并将其命名为 "HLSharedProjectMainPart5"，以便在再次需要时更轻松地找到它。</span><span class="sxs-lookup"><span data-stu-id="626f5-113">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="626f5-114">选择 MixedRealityPlayspace 父对象下的 TableAnchor prefab，并将其删除。</span><span class="sxs-lookup"><span data-stu-id="626f5-114">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="626f5-116">在 "项目" 视图中，中转到 "资产-> 资源-> Prototyping"，然后将 TableAnchor prefab 拖到 SharedPlayground 对象的顶部，使其成为子对象。</span><span class="sxs-lookup"><span data-stu-id="626f5-116">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="626f5-117">展开 MixedRealityPlayspace 父对象 TableAnchor 对象，并同时展开 "按钮" 对象。</span><span class="sxs-lookup"><span data-stu-id="626f5-117">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="626f5-119">现在，在层次结构中，选择 "ShareAzureAnchorButton"，并将注意力移动到 "Inaspector" 面板。</span><span class="sxs-lookup"><span data-stu-id="626f5-119">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="626f5-120">向下滚动到下图所示的下拉菜单中，选择 "AnchorModuleScript"，然后单击 "ShareAnchorNetework" （）。</span><span class="sxs-lookup"><span data-stu-id="626f5-120">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="626f5-122">选择 GetAzureAnchorButton （请参阅步骤4），并将你的注意力移回到检查器面板。</span><span class="sxs-lookup"><span data-stu-id="626f5-122">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="626f5-123">向下滚动到下图所示的下拉菜单中，选择 "AnchorModuleScript"，并单击 "GetSharedAnchorNetwork" （），然后单击 "保存"。</span><span class="sxs-lookup"><span data-stu-id="626f5-123">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="626f5-125">若要测试共享模块，请单击 "启动 azure ASA 会话" 按钮，该按钮将启动 azure 空间锚点会话，然后通过单击 "创建 Azure 锚点" 按钮创建 azure 锚点。</span><span class="sxs-lookup"><span data-stu-id="626f5-125">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="626f5-126">等待 azure 定位符创建完成。</span><span class="sxs-lookup"><span data-stu-id="626f5-126">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="626f5-127">创建 azure 定位点后，请单击 "共享 Azure 锚点" 按钮，从 HoloLens 共享创建的 azure 定位点。</span><span class="sxs-lookup"><span data-stu-id="626f5-127">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="626f5-128">若要在另一个 HoloLens 中接收共享的 azure 定位点，请单击 "启动 Azure ASA 会话" 以启动并进入当前 ASA 会话</span><span class="sxs-lookup"><span data-stu-id="626f5-128">To recieve the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

8. <span data-ttu-id="626f5-129">单击 "获取 Azure 锚点" 按钮，从另一个 HoloLens 获取共享的 azure 定位点。</span><span class="sxs-lookup"><span data-stu-id="626f5-129">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="626f5-130">注意：各个按钮上对应操作的所有详细信息都将显示在调试窗口中。</span><span class="sxs-lookup"><span data-stu-id="626f5-130">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="626f5-131">祝贺</span><span class="sxs-lookup"><span data-stu-id="626f5-131">Congratulations</span></span>

<span data-ttu-id="626f5-132">在本课程中，你学习了如何集成 Azure 强大的新空间锚点，以便在共享体验中协调归置设备！</span><span class="sxs-lookup"><span data-stu-id="626f5-132">In this lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="626f5-133">这也会结束共享模块。</span><span class="sxs-lookup"><span data-stu-id="626f5-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="626f5-134">我们学习了如何设置新的 Photon 帐户，将 Photon 和双关语集成到新的 Unity 应用程序中，配置头像和 shared 对象，并最终使用 ASA 协调多个参与者。</span><span class="sxs-lookup"><span data-stu-id="626f5-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span> 

