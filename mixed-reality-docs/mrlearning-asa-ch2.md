---
title: Azure 空间定位点教程 - 2. 保存、检索和共享 Azure 空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362008"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="89562-105">2.保存、检索和共享 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="89562-105">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="89562-106">本教程将介绍如何通过将定位点 ID 保存到 HoloLens 2 的存储，来保存多个应用会话中的 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="89562-106">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="89562-107">此外，介绍如何与其他设备共享此定位点 ID，以便在多个设备上对齐定位点。</span><span class="sxs-lookup"><span data-stu-id="89562-107">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="89562-108">目标</span><span class="sxs-lookup"><span data-stu-id="89562-108">Objectives</span></span>

* <span data-ttu-id="89562-109">了解如何在 HoloLens 2 本地磁盘中保存以及从中检索 Azure 空间定位点 ID，以便在不同的应用会话中持久保留这些 ID。</span><span class="sxs-lookup"><span data-stu-id="89562-109">Learn how to save and retrieve Azure Spatial Anchor IDs to and from the HoloLens 2 local disk, for persistence between app sessions</span></span>
* <span data-ttu-id="89562-110">了解如何在多设备方案中的用户之间共享 Azure 空间定位点 ID</span><span class="sxs-lookup"><span data-stu-id="89562-110">Learn how to share Azure Spatial Anchor IDs between users in a multi-device scenario</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="89562-111">准备场景</span><span class="sxs-lookup"><span data-stu-id="89562-111">Preparing the scene</span></span>

<span data-ttu-id="89562-112">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹。   </span><span class="sxs-lookup"><span data-stu-id="89562-112">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="89562-113">在按住 CTRL 键的同时单击“ButtonParent_SaveAnchorId”和“ButtonParent_ShareAnchorId”以选择这两个预制件，然后将其拖放到“层次结构”窗口，以将其添加到场景中：  </span><span class="sxs-lookup"><span data-stu-id="89562-113">While holding down the CTRL button, click on **ButtonParent_SaveAnchorId** and **ButtonParent_ShareAnchorId** to select the two prefabs, then drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="89562-115">在不同的应用会话中保留 Azure 定位点 - 将定位点 ID 保存到磁盘</span><span class="sxs-lookup"><span data-stu-id="89562-115">Persist Azure Anchors between app sessions - Save anchor ID to disk</span></span>
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

<span data-ttu-id="89562-116">本部分介绍如何在 HoloLens 2 本地磁盘中保存以及从中检索 Azure 空间定位点 ID。</span><span class="sxs-lookup"><span data-stu-id="89562-116">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens 2 local disk.</span></span> <span data-ttu-id="89562-117">这样，你便可以在 Azure 中查询不同应用会话使用的同一定位点 ID，使定位点定的全息影像定位在上一个应用会话中所处的同一位置。</span><span class="sxs-lookup"><span data-stu-id="89562-117">This will allow you to query Azure for the same anchor ID between different app sessions, allowing the anchored holograms to be position at the same location as in the previous app session.</span></span>

<span data-ttu-id="89562-118">在“层次结构”窗口中展开“ButtonParent_SaveAnchorId”对象，该对象包含两个按钮，一个按钮用于将 Azure 定位点 ID 保存到 HoloLens 2 存储，另一个按钮用于从磁盘中检索保存的 ID： </span><span class="sxs-lookup"><span data-stu-id="89562-118">In the Hierarchy window, expand the **ButtonParent_SaveAnchorId** object which contains two buttons, one button for saving the Azure Anchor ID to the HoloLens 2 storage and another for retrieving the saved ID from the disk:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

<span data-ttu-id="89562-120">遵循上一篇教程的[配置按钮以操作场景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)说明中的相同步骤，在这两个按钮中的每个按钮上配置“可按按钮 Holo Lens 2 (脚本)”组件“可交互(脚本)”组件：  </span><span class="sxs-lookup"><span data-stu-id="89562-120">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="89562-121">对于“SaveAzureAnchorIdToDisk”对象，请分配“AnchorModuleScript”>“SaveAzureAnchorIdToDisk ()”函数。  </span><span class="sxs-lookup"><span data-stu-id="89562-121">For the **SaveAzureAnchorIdToDisk** object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="89562-122">对于“GetAzureAnchorIdFromDisk”对象，请分配“AnchorModuleScript”>“GetAzureAnchorIdFromDisk ()”函数。  </span><span class="sxs-lookup"><span data-stu-id="89562-122">For the **GetAzureAnchorIdFromDisk** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="89562-123">如果在 HoloLens 中生成更新的应用程序，则现在可以通过保存 Azure 定位点 ID 在不同的应用会话中保留 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="89562-123">If you build the updated application to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="89562-124">若要进行测试，可执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="89562-124">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="89562-125">将“火箭发射器”体验移到所需位置。</span><span class="sxs-lookup"><span data-stu-id="89562-125">Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="89562-126">启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="89562-126">Start Azure Session.</span></span>
3. <span data-ttu-id="89562-127">创建 Azure 定位点（在“火箭发射器”体验位置创建定位点）。</span><span class="sxs-lookup"><span data-stu-id="89562-127">Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="89562-128">将 Azure 定位点 ID 保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="89562-128">Save Azure Anchor ID to Disk.</span></span>
5. <span data-ttu-id="89562-129">重启应用程序。</span><span class="sxs-lookup"><span data-stu-id="89562-129">Restart the application.</span></span>
6. <span data-ttu-id="89562-130">从磁盘中获取 Azure 定位点（加载刚刚保存的定位点 ID）。</span><span class="sxs-lookup"><span data-stu-id="89562-130">Get Azure Anchor from Disk (loads the anchor ID you just saved).</span></span>
7. <span data-ttu-id="89562-131">启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="89562-131">Start Azure Session.</span></span>
8. <span data-ttu-id="89562-132">查找 Azure 定位点（将“火箭发射器”体验定位在步骤 3 所述的位置）。</span><span class="sxs-lookup"><span data-stu-id="89562-132">Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!NOTE]
> <span data-ttu-id="89562-133">若要完全重启应用程序，在退出沉浸式应用视图之后，需要先关闭混合现实主页中的应用窗口，然后从“开始”菜单重新启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="89562-133">To fully restart the application, after exiting the immersive app view, the app window in the mixed reality home needs to be closed before relaunching the application from the Start menu.</span></span> <span data-ttu-id="89562-134">如需更多详细信息，可以参阅[在 HoloLens 上使用应用](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)文档。</span><span class="sxs-lookup"><span data-stu-id="89562-134">For additional details, you can refer to the [Using apps on HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens) documentation.</span></span>

## <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="89562-135">在多个设备之间共享 Azure 定位点</span><span class="sxs-lookup"><span data-stu-id="89562-135">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="89562-136">本部分介绍如何在多个设备之间共享 Azure 定位点 ID。</span><span class="sxs-lookup"><span data-stu-id="89562-136">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="89562-137">这样，多个设备便可以在 Azure 中查询同一个定位点 ID，从而可在空间上对齐定位点定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="89562-137">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="89562-138">空间对齐（即，在多个设备之间的同一物理位置查看相同的全息影像）是 HoloLens 2 中本地共享体验的关键所在。</span><span class="sxs-lookup"><span data-stu-id="89562-138">Spatial alignment, i.e. seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="89562-139">可以通过多种方法在设备之间转移 Azure 定位点 ID，包括[多用户功能教程](mrlearning-sharing(photon)-ch1.md)系列中所述的方法。</span><span class="sxs-lookup"><span data-stu-id="89562-139">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the the [Multi-user capabilities tutorials](mrlearning-sharing(photon)-ch1.md) series.</span></span> <span data-ttu-id="89562-140">此示例将使用一个简单的 Web 服务在设备之间上传和下载定位点 ID。</span><span class="sxs-lookup"><span data-stu-id="89562-140">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="89562-141">在“层次结构”窗口中展开“ButtonParent_ShareAnchorId”对象，该对象包含两个按钮，一个按钮用于将 Azure 定位点 ID 上传到 Web 服务器，另一个按钮用于从 Web 服务器下载该 ID： </span><span class="sxs-lookup"><span data-stu-id="89562-141">In the Hierarchy window, expand the **ButtonParent_ShareAnchorId** object which contains two buttons; one button for uploading the Azure Anchor ID to the web server, and another for downloading the ID from the web server:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

<span data-ttu-id="89562-143">遵循上一篇教程的[配置按钮以操作场景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)说明中的相同步骤，在这两个按钮中的每个按钮上配置“可按按钮 Holo Lens 2 (脚本)”组件“可交互(脚本)”组件：  </span><span class="sxs-lookup"><span data-stu-id="89562-143">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="89562-144">对于“ShareAzureAnchorIdToNetwork”对象，请分配“AnchorModuleScript”>“ShareAzureAnchorIdToNetwork ()”函数。  </span><span class="sxs-lookup"><span data-stu-id="89562-144">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="89562-145">对于“GetAzureAnchorIdFromNetwork”对象，请分配“AnchorModuleScript”>“GetAzureAnchorIdFromNetwork ()”函数。  </span><span class="sxs-lookup"><span data-stu-id="89562-145">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="89562-146">如果在两个 HoloLens 设备上生成更新的应用程序，则现在可以通过共享 Azure 定位点 ID 来实现设备之间的空间对齐。</span><span class="sxs-lookup"><span data-stu-id="89562-146">If you build the updated application to two HoloLens devices, you can now achieve spatial alignment between them by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="89562-147">若要进行测试，可执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="89562-147">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="89562-148">在 HoloLens 设备 1 上：将“火箭发射器”体验移到所需位置。</span><span class="sxs-lookup"><span data-stu-id="89562-148">On HoloLens device 1: Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="89562-149">在 HoloLens 设备 1 上：启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="89562-149">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="89562-150">在 HoloLens 设备 1 上：创建 Azure 定位点（在“火箭发射器”体验位置创建定位点）。</span><span class="sxs-lookup"><span data-stu-id="89562-150">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="89562-151">在 HoloLens 设备 1 上：在网络中共享 Azure 定位点 ID。</span><span class="sxs-lookup"><span data-stu-id="89562-151">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="89562-152">在 HoloLens 设备 2 上：启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="89562-152">On HoloLens device 2: Start the application.</span></span>
6. <span data-ttu-id="89562-153">在 HoloLens 设备 2 上：从网络中获取共享的定位点 ID（提取刚刚从 HoloLens 设备 1 共享的定位点 ID）。</span><span class="sxs-lookup"><span data-stu-id="89562-153">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="89562-154">在 HoloLens 设备 2 上：启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="89562-154">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="89562-155">在 HoloLens 设备 2 上：查找 Azure 定位点（将“火箭发射器”体验定位在步骤 3 所述的位置）。</span><span class="sxs-lookup"><span data-stu-id="89562-155">On HoloLens device 2: Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="89562-156">如果只有一个 HoloLens 设备，仍可以通过重启应用程序来测试该功能，而无需使用另一个 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="89562-156">If you only have one HoloLens, you can still test the functionality by restarting the application instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="89562-157">祝贺</span><span class="sxs-lookup"><span data-stu-id="89562-157">Congratulations</span></span>

<span data-ttu-id="89562-158">在本教程中，你已了解如何通过将 Azure 空间定位点 ID 保存到 HoloLens 上的本地磁盘，在不同的应用程序会话中以及每次重启应用程序后保留 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="89562-158">In this tutorial you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="89562-159">此外，你还了解了如何在基本多用户静态全息影像共享体验中的多个设备之间共享 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="89562-159">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="89562-160">下一篇教程将会介绍如何为用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="89562-160">In the next tutorial you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="89562-161">此反馈包括有关定位点的创建、环境质量识别以及 Azure 会话状态的信息。</span><span class="sxs-lookup"><span data-stu-id="89562-161">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="89562-162">如果没有反馈，用户可能不知道某个定位点是否已成功上传到 Azure，而不管环境质量是足以创建定位点还是处于当前状态。</span><span class="sxs-lookup"><span data-stu-id="89562-162">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="89562-163">下一课：3.显示 Azure 空间定位点反馈</span><span class="sxs-lookup"><span data-stu-id="89562-163">Next Lesson: 3. Displaying Azure Spatial Anchor feedback</span></span>](mrlearning-asa-ch3.md)
