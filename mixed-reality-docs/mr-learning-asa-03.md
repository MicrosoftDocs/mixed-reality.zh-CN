---
title: Azure 空间定位点教程 - 3. 保存、检索和共享 Azure 空间定位点
description: 完成本课程可以了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 25676404a71daf41b6a5c7587fa9bed95ab813f6
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304168"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="7d584-105">3.保存、检索和共享 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="7d584-105">3. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="7d584-106">本教程将介绍如何通过将定位点 ID 保存到 HoloLens 2 的存储，来保存多个应用会话中的 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="7d584-106">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="7d584-107">此外，介绍如何与其他设备共享此定位点 ID，以便在多个设备上对齐定位点。</span><span class="sxs-lookup"><span data-stu-id="7d584-107">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="7d584-108">目标</span><span class="sxs-lookup"><span data-stu-id="7d584-108">Objectives</span></span>

* <span data-ttu-id="7d584-109">了解如何在多个应用会话之间实现空间对齐。</span><span class="sxs-lookup"><span data-stu-id="7d584-109">Learn how to achieve spatial alignment across multiple app sessions.</span></span>
* <span data-ttu-id="7d584-110">了解如何在多台设备之间实现空间对齐。</span><span class="sxs-lookup"><span data-stu-id="7d584-110">Learn how to achieve spatial alignment between multiple devices.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="7d584-111">准备场景</span><span class="sxs-lookup"><span data-stu-id="7d584-111">Preparing the scene</span></span>

<span data-ttu-id="7d584-112">在“层次结构”窗口中，展开“ButtonParent”对象。</span><span class="sxs-lookup"><span data-stu-id="7d584-112">In the Hierarchy window, expand the **ButtonParent** object.</span></span> <span data-ttu-id="7d584-113">选择最后四个子按钮对象。</span><span class="sxs-lookup"><span data-stu-id="7d584-113">Select the **last four child button** objects.</span></span> <span data-ttu-id="7d584-114">在“检查器”窗口中，选中“名称”字段旁的复选框以使所有对象处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="7d584-114">In the Inspector window, **check** the checkbox next to the name field to make all the objects active.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-1.png)

<span data-ttu-id="7d584-116">在“层次结构”窗口中，选择“ButtonParent”对象。</span><span class="sxs-lookup"><span data-stu-id="7d584-116">In the Hierarchy window, select the **ButtonParent** objects.</span></span> <span data-ttu-id="7d584-117">然后在“检查器”窗口中，找到 GridObjectCollection 组件并单击“更新集合”按钮，以更新所有 ButtonParent 对象的子对象的位置  。</span><span class="sxs-lookup"><span data-stu-id="7d584-117">Then in the Inspector window, locate the **GridObjectCollection** component and click the **Update Collection** button to update the position of all the **ButtonParent** object's child objects.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a><span data-ttu-id="7d584-119">在应用会话之间保留 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="7d584-119">Persisting Azure Spatial Anchors between app sessions</span></span>

<span data-ttu-id="7d584-120">本部分介绍如何在 HoloLens 2 本地磁盘中保存以及从中检索 Azure 空间定位点 ID。</span><span class="sxs-lookup"><span data-stu-id="7d584-120">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens' local disk.</span></span> <span data-ttu-id="7d584-121">通过这些操作，你可以在 Azure 中查询不同应用会话中的同一定位点 ID。</span><span class="sxs-lookup"><span data-stu-id="7d584-121">This will allow you to query Azure for the same anchor ID between different app sessions.</span></span> <span data-ttu-id="7d584-122">它使定位的全息影像能够位于上一个应用会话中的相同位置。</span><span class="sxs-lookup"><span data-stu-id="7d584-122">It will enable the anchored holograms to be positioned at the same location as in the previous app session.</span></span>

<span data-ttu-id="7d584-123">在“层次结构”窗口中，展开“ButtonParent”对象并找到名为 SaveAzureAnchorIdToDisk 和 GetAzureAnchorIdFromDisk 的两个按钮  ：</span><span class="sxs-lookup"><span data-stu-id="7d584-123">In the Hierarchy window, expand the **ButtonParent** object and locate the two buttons named **SaveAzureAnchorIdToDisk** and **GetAzureAnchorIdFromDisk**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-03-section2-step1-1.png)

<span data-ttu-id="7d584-125">遵循上一篇教程的[配置按钮以操作场景](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene)说明中的相同步骤，在这两个按钮中的每个按钮上配置“可交互(脚本)”组件：</span><span class="sxs-lookup"><span data-stu-id="7d584-125">Follow the same steps as in the [configuring the buttons to operate the scene](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="7d584-126">对于“SaveAzureAnchorIdToDisk”按钮对象，请分配“AnchorModuleScript”>“SaveAzureAnchorIdToDisk ()”函数。 </span><span class="sxs-lookup"><span data-stu-id="7d584-126">For the **SaveAzureAnchorIdToDisk** button object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="7d584-127">对于“GetAzureAnchorIdFromDisk”按钮对象，请分配“AnchorModuleScript”>“GetAzureAnchorIdFromDisk ()”函数。 </span><span class="sxs-lookup"><span data-stu-id="7d584-127">For the **GetAzureAnchorIdFromDisk** button object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="7d584-128">如果在 HoloLens 中生成更新的应用，则现在可以通过保存 Azure 定位点 ID 在不同的应用会话中保留 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="7d584-128">If you build the updated app to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="7d584-129">若要进行测试，可执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="7d584-129">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="7d584-130">将“漫游者探测器”移到所需位置</span><span class="sxs-lookup"><span data-stu-id="7d584-130">Move the Rover Explorer to the desired location</span></span>
2. <span data-ttu-id="7d584-131">启动 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="7d584-131">Start Azure Session</span></span>
3. <span data-ttu-id="7d584-132">创建 Azure 定位点（在“漫游者探测器”位置创建定位点）</span><span class="sxs-lookup"><span data-stu-id="7d584-132">Create Azure Anchor (creates anchors at the location of the Rover Explorer)</span></span>
4. <span data-ttu-id="7d584-133">将 Azure 定位点 ID 保存到磁盘</span><span class="sxs-lookup"><span data-stu-id="7d584-133">Save Azure Anchor ID to Disk</span></span>
5. <span data-ttu-id="7d584-134">重启应用</span><span class="sxs-lookup"><span data-stu-id="7d584-134">Restart the app</span></span>
6. <span data-ttu-id="7d584-135">从磁盘中获取 Azure 定位点（加载刚刚保存的定位点 ID）</span><span class="sxs-lookup"><span data-stu-id="7d584-135">Get Azure Anchor from Disk (loads the anchor ID you just saved)</span></span>
7. <span data-ttu-id="7d584-136">启动 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="7d584-136">Start Azure Session</span></span>
8. <span data-ttu-id="7d584-137">查找 Azure 定位点（将“漫游者探测器”定位到步骤 3 所述的位置）</span><span class="sxs-lookup"><span data-stu-id="7d584-137">Find Azure Anchor (positions the Rover Explorer at the location from step 3)</span></span>

> [!NOTE]
> <span data-ttu-id="7d584-138">若要完全重启应用，在退出沉浸式应用视图之后，需要先关闭混合现实主页中的应用窗口，然后从“开始”菜单重新启动应用。</span><span class="sxs-lookup"><span data-stu-id="7d584-138">To fully restart the app, after exiting the immersive app view, the app window in the mixed reality home needs to be closed before relaunching it from the Start menu.</span></span> <span data-ttu-id="7d584-139">如需更多详细信息，可以参阅[在 HoloLens 上使用应用](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)文档。</span><span class="sxs-lookup"><span data-stu-id="7d584-139">For additional details, you can refer to the [Using apps on HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens) documentation.</span></span>

## <a name="sharing-azure-spatial-anchors-between-devices"></a><span data-ttu-id="7d584-140">在设备之间共享 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="7d584-140">Sharing Azure Spatial Anchors between devices</span></span>

<span data-ttu-id="7d584-141">本部分介绍如何在多个设备之间共享 Azure 定位点 ID。</span><span class="sxs-lookup"><span data-stu-id="7d584-141">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="7d584-142">这样，多个设备便可以在 Azure 中查询同一个定位点 ID，从而可在空间上对齐定位点定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="7d584-142">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="7d584-143">空间对齐（即，在多个设备之间的同一物理位置查看相同的全息影像）是 HoloLens 2 中本地共享体验的关键所在。</span><span class="sxs-lookup"><span data-stu-id="7d584-143">Spatial alignment, i.e., seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="7d584-144">可以通过多种方法在设备之间转移 Azure 定位点 ID，包括[多用户功能教程](mr-learning-sharing-02.md)系列中所述的方法。</span><span class="sxs-lookup"><span data-stu-id="7d584-144">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the [Multi-user capabilities tutorials](mr-learning-sharing-02.md) series.</span></span> <span data-ttu-id="7d584-145">此示例将使用一个简单的 Web 服务在设备之间上传和下载定位点 ID。</span><span class="sxs-lookup"><span data-stu-id="7d584-145">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="7d584-146">在“层次结构”窗口中，展开“ButtonParent”对象。</span><span class="sxs-lookup"><span data-stu-id="7d584-146">In the Hierarchy window, expand the **ButtonParent** object.</span></span>   <span data-ttu-id="7d584-147">找到名为 ShareAzureAnchorIdToNetwork 和 GetAzureAnchorIdFromNetwork 的两个按钮 ：</span><span class="sxs-lookup"><span data-stu-id="7d584-147">Locate the two buttons named **ShareAzureAnchorIdToNetwork** and **GetAzureAnchorIdFromNetwork**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-03-section3-step1-1.png)

<span data-ttu-id="7d584-149">遵循上一篇教程的[配置按钮以操作场景](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene)说明中的相同步骤，在这两个按钮中的每个按钮上配置“可交互(脚本)”组件：</span><span class="sxs-lookup"><span data-stu-id="7d584-149">Follow the same steps as in the [configuring the buttons to operate the scene](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="7d584-150">对于“ShareAzureAnchorIdToNetwork”对象，请分配“AnchorModuleScript”>“ShareAzureAnchorIdToNetwork ()”函数。 </span><span class="sxs-lookup"><span data-stu-id="7d584-150">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="7d584-151">对于“GetAzureAnchorIdFromNetwork”对象，请分配“AnchorModuleScript”>“GetAzureAnchorIdFromNetwork ()”函数。 </span><span class="sxs-lookup"><span data-stu-id="7d584-151">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="7d584-152">如果在两个 HoloLens 设备上生成更新的应用，则现在可以通过共享 Azure 定位点 ID 来实现空间对齐。</span><span class="sxs-lookup"><span data-stu-id="7d584-152">If you build the updated app to two HoloLens devices, you can now achieve spatial alignment by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="7d584-153">若要进行测试，可执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="7d584-153">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="7d584-154">在 HoloLens 设备 1 上：将“漫游者探测器”移到所需位置。</span><span class="sxs-lookup"><span data-stu-id="7d584-154">On HoloLens device 1: Move the Rover Explorer to the desired location.</span></span>
2. <span data-ttu-id="7d584-155">在 HoloLens 设备 1 上：启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="7d584-155">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="7d584-156">在 HoloLens 设备 1 上：创建 Azure 定位点（在“漫游者探测器”位置创建定位点）。</span><span class="sxs-lookup"><span data-stu-id="7d584-156">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rover Explorer).</span></span>
4. <span data-ttu-id="7d584-157">在 HoloLens 设备 1 上：在网络中共享 Azure 定位点 ID。</span><span class="sxs-lookup"><span data-stu-id="7d584-157">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="7d584-158">在 HoloLens 设备 2 上：启动应用。</span><span class="sxs-lookup"><span data-stu-id="7d584-158">On HoloLens device 2: Start the app.</span></span>
6. <span data-ttu-id="7d584-159">在 HoloLens 设备 2 上：从网络中获取共享的定位点 ID（提取刚刚从 HoloLens 设备 1 共享的定位点 ID）。</span><span class="sxs-lookup"><span data-stu-id="7d584-159">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="7d584-160">在 HoloLens 设备 2 上：启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="7d584-160">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="7d584-161">在 HoloLens 设备 2 上：查找 Azure 定位点（将“漫游者探测器”定位到步骤 3 所述的位置）。</span><span class="sxs-lookup"><span data-stu-id="7d584-161">On HoloLens device 2: Find Azure Anchor (positions the Rover Explorer at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="7d584-162">如果只有一个 HoloLens 设备，仍可以通过重启应用来测试该功能，而无需使用另一个 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="7d584-162">If you only have one HoloLens, you can still test the functionality by restarting the app instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7d584-163">祝贺</span><span class="sxs-lookup"><span data-stu-id="7d584-163">Congratulations</span></span>

<span data-ttu-id="7d584-164">在本教程中，你已了解如何通过将 Azure 空间定位点 ID 保存到 HoloLens 上的本地磁盘，在不同的应用会话中以及每次重启应用后保留 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="7d584-164">In this tutorial, you learned how to persist Azure Spatial Anchors between app sessions and app restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="7d584-165">此外，你还了解了如何在基本多用户静态全息影像共享体验中的多个设备之间共享 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="7d584-165">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="7d584-166">下一篇教程将会介绍如何为用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="7d584-166">In the next tutorial, you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="7d584-167">此反馈包括有关定位点的创建、环境质量识别以及 Azure 会话状态的信息。</span><span class="sxs-lookup"><span data-stu-id="7d584-167">This feedback will include information about Anchor creation, the quality of environment understanding, and the Azure session's state.</span></span> <span data-ttu-id="7d584-168">如果没有反馈，用户可能不知道某个定位点是否已成功上传到 Azure，而不管环境质量是足以创建定位点还是处于当前状态。</span><span class="sxs-lookup"><span data-stu-id="7d584-168">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="7d584-169">下一教程：4.显示 Azure 空间定位点反馈</span><span class="sxs-lookup"><span data-stu-id="7d584-169">Next Tutorial: 4. Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
