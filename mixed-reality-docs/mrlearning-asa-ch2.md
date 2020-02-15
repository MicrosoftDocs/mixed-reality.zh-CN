---
title: Azure 空间锚点教程-2。 保存、检索和共享 Azure 空间锚
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250725"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="82c60-105">2. 保存、检索和共享 Azure 空间锚</span><span class="sxs-lookup"><span data-stu-id="82c60-105">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="82c60-106">在本教程中，你将了解如何通过将定位点 ID 保存到 HoloLens 2 的存储来跨多个应用会话保存 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="82c60-106">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="82c60-107">你还将了解如何将此定位点 ID 共享到其他设备，以实现多设备锚点对齐。</span><span class="sxs-lookup"><span data-stu-id="82c60-107">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="82c60-108">目标</span><span class="sxs-lookup"><span data-stu-id="82c60-108">Objectives</span></span>

* <span data-ttu-id="82c60-109">了解如何在应用程序会话之间保存和检索 HoloLens 2 本地磁盘的 Azure 空间定位点 Id</span><span class="sxs-lookup"><span data-stu-id="82c60-109">Learn how to save and retrieve Azure Spatial Anchor IDs to and from the HoloLens 2 local disk, for persistence between app sessions</span></span>
* <span data-ttu-id="82c60-110">了解如何在多设备方案中共享用户之间的 Azure 空间锚点 Id</span><span class="sxs-lookup"><span data-stu-id="82c60-110">Learn how to share Azure Spatial Anchor IDs between users in a multi-device scenario</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="82c60-111">准备场景</span><span class="sxs-lookup"><span data-stu-id="82c60-111">Preparing the scene</span></span>

<span data-ttu-id="82c60-112">在项目窗口中，导航到 "**资产**" > **MRTK "。AzureSpatialAnchors** > **prototyping**文件夹。</span><span class="sxs-lookup"><span data-stu-id="82c60-112">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="82c60-113">按住 CTRL，同时单击**ButtonParent_SaveAnchorId**并**ButtonParent_ShareAnchorId**选择两个 prototyping，然后将其拖动到 "层次结构" 窗口中，将其添加到场景：</span><span class="sxs-lookup"><span data-stu-id="82c60-113">While holding down the CTRL button, click on **ButtonParent_SaveAnchorId** and **ButtonParent_ShareAnchorId** to select the two prefabs, then drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="82c60-115">在应用会话之间保留 Azure 锚点-将定位点 ID 保存到磁盘</span><span class="sxs-lookup"><span data-stu-id="82c60-115">Persist Azure Anchors between app sessions - Save anchor ID to disk</span></span>
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

<span data-ttu-id="82c60-116">在本部分中，你将了解如何将 Azure 定位 ID 保存和检索到 HoloLens 2 本地磁盘。</span><span class="sxs-lookup"><span data-stu-id="82c60-116">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens 2 local disk.</span></span> <span data-ttu-id="82c60-117">这将允许你在 Azure 中查询不同应用会话间的相同锚 ID，从而允许定位的全息影像位于与上一个应用会话相同的位置。</span><span class="sxs-lookup"><span data-stu-id="82c60-117">This will allow you to query Azure for the same anchor ID between different app sessions, allowing the anchored holograms to be position at the same location as in the previous app session.</span></span>

<span data-ttu-id="82c60-118">在 "层次结构" 窗口中，展开包含两个按钮的 " **ButtonParent_SaveAnchorId** " 对象，一个按钮用于将 Azure 定位点 ID 保存到 HoloLens 2 存储，另一个用于从磁盘检索保存的 id：</span><span class="sxs-lookup"><span data-stu-id="82c60-118">In the Hierarchy window, expand the **ButtonParent_SaveAnchorId** object which contains two buttons, one button for saving the Azure Anchor ID to the HoloLens 2 storage and another for retrieving the saved ID from the disk:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

<span data-ttu-id="82c60-120">按照前面教程中的 "[配置按钮以操作场景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)说明" 中所述的相同步骤，在两个按钮的每个按钮上配置**Pressable 按钮 Holo Lens 2 （脚本）** 组件和**种不可交互（Script）** 组件：</span><span class="sxs-lookup"><span data-stu-id="82c60-120">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="82c60-121">对于**SaveAzureAnchorIdToDisk**对象，请将 AnchorModuleScript > **SaveAzureAnchorIdToDisk （）** 函数。</span><span class="sxs-lookup"><span data-stu-id="82c60-121">For the **SaveAzureAnchorIdToDisk** object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="82c60-122">对于**GetAzureAnchorIdFromDisk**对象，请将 AnchorModuleScript > **GetAzureAnchorIdFromDisk （）** 函数。</span><span class="sxs-lookup"><span data-stu-id="82c60-122">For the **GetAzureAnchorIdFromDisk** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="82c60-123">如果将更新后的应用程序生成到 HoloLens，你现在可以通过保存 Azure 定位点 ID 在应用会话之间保持 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="82c60-123">If you build the updated application to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="82c60-124">若要对其进行测试，你可以执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="82c60-124">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="82c60-125">将火箭启动器体验移到所需位置。</span><span class="sxs-lookup"><span data-stu-id="82c60-125">Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="82c60-126">启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="82c60-126">Start Azure Session.</span></span>
3. <span data-ttu-id="82c60-127">创建 Azure 定位点（在火箭启动器体验位置创建定位点）。</span><span class="sxs-lookup"><span data-stu-id="82c60-127">Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="82c60-128">将 Azure 定位 ID 保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="82c60-128">Save Azure Anchor ID to Disk.</span></span>
5. <span data-ttu-id="82c60-129">重新启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="82c60-129">Restart the application.</span></span>
6. <span data-ttu-id="82c60-130">从磁盘获取 Azure 定位点（加载刚刚保存的定位点 ID）。</span><span class="sxs-lookup"><span data-stu-id="82c60-130">Get Azure Anchor from Disk (loads the anchor ID you just saved).</span></span>
7. <span data-ttu-id="82c60-131">启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="82c60-131">Start Azure Session.</span></span>
8. <span data-ttu-id="82c60-132">查找 Azure 定位点（将火箭启动器体验置于步骤3的位置）。</span><span class="sxs-lookup"><span data-stu-id="82c60-132">Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

## <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="82c60-133">在多个设备之间共享 Azure 锚</span><span class="sxs-lookup"><span data-stu-id="82c60-133">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="82c60-134">在本部分中，你将了解如何在多个设备之间共享 Azure 定位 ID。</span><span class="sxs-lookup"><span data-stu-id="82c60-134">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="82c60-135">这将允许多个设备在 Azure 中查询相同的定位点 ID，从而允许锁定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="82c60-135">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="82c60-136">空间对齐，即在多个设备之间的同一物理位置查看相同的全息影像，这是 HoloLens 2 中本地共享体验的关键所在。</span><span class="sxs-lookup"><span data-stu-id="82c60-136">Spatial alignment, i.e. seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="82c60-137">可以通过多种方式在设备之间传输 Azure 锚 Id，包括[多用户功能教程](mrlearning-sharing(photon)-ch1.md)系列中所述的方法。</span><span class="sxs-lookup"><span data-stu-id="82c60-137">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the the [Multi-user capabilities tutorials](mrlearning-sharing(photon)-ch1.md) series.</span></span> <span data-ttu-id="82c60-138">在此示例中，你将使用简单的 web 服务在设备之间上传和下载定位点 Id。</span><span class="sxs-lookup"><span data-stu-id="82c60-138">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="82c60-139">在 "层次结构" 窗口中，展开包含两个按钮的**ButtonParent_ShareAnchorId**对象;一个按钮，用于将 Azure 定位点 ID 上传到 web 服务器，另一个按钮用于从 web 服务器下载 ID：</span><span class="sxs-lookup"><span data-stu-id="82c60-139">In the Hierarchy window, expand the **ButtonParent_ShareAnchorId** object which contains two buttons; one button for uploading the Azure Anchor ID to the web server, and another for downloading the ID from the web server:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

<span data-ttu-id="82c60-141">按照前面教程中的 "[配置按钮以操作场景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)说明" 中所述的相同步骤，在两个按钮的每个按钮上配置**Pressable 按钮 Holo Lens 2 （脚本）** 组件和**种不可交互（Script）** 组件：</span><span class="sxs-lookup"><span data-stu-id="82c60-141">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="82c60-142">对于**ShareAzureAnchorIdToNetwork**对象，请将 AnchorModuleScript > **ShareAzureAnchorIdToNetwork （）** 函数。</span><span class="sxs-lookup"><span data-stu-id="82c60-142">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="82c60-143">对于**GetAzureAnchorIdFromNetwork**对象，请将 AnchorModuleScript > **GetAzureAnchorIdFromNetwork （）** 函数。</span><span class="sxs-lookup"><span data-stu-id="82c60-143">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="82c60-144">如果将更新后的应用程序生成到两个 HoloLens 设备，你现在可以通过共享 Azure 定位 ID 来实现它们之间的空间对齐。</span><span class="sxs-lookup"><span data-stu-id="82c60-144">If you build the updated application to two HoloLens devices, you can now achieve spatial alignment between them by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="82c60-145">若要对其进行测试，你可以执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="82c60-145">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="82c60-146">在 HoloLens 设备1上：将火箭启动器体验移到所需的位置。</span><span class="sxs-lookup"><span data-stu-id="82c60-146">On HoloLens device 1: Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="82c60-147">在 HoloLens 设备1上：启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="82c60-147">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="82c60-148">在 HoloLens 设备1上：创建 Azure 定位点（在火箭启动器体验位置创建定位点）。</span><span class="sxs-lookup"><span data-stu-id="82c60-148">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="82c60-149">在 HoloLens 设备1上：将 Azure 定位 ID 共享到网络。</span><span class="sxs-lookup"><span data-stu-id="82c60-149">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="82c60-150">在 HoloLens 设备2上：重新启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="82c60-150">On HoloLens device 2: Restart the application.</span></span>
6. <span data-ttu-id="82c60-151">在 HoloLens 设备2：从网络获取共享的定位点 ID （获取刚刚从 HoloLens 设备1共享的定位点 ID）。</span><span class="sxs-lookup"><span data-stu-id="82c60-151">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="82c60-152">在 HoloLens 设备2上：启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="82c60-152">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="82c60-153">在 HoloLens 设备2上：查找 Azure 定位点（将火箭启动器体验置于步骤3的位置）。</span><span class="sxs-lookup"><span data-stu-id="82c60-153">On HoloLens device 2: Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="82c60-154">如果只有一个 HoloLens，则仍可通过重新启动应用程序而不是使用第二个 HoloLens 设备来测试该功能。</span><span class="sxs-lookup"><span data-stu-id="82c60-154">If you only have one HoloLens, you can still test the functionality by restarting the application instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="82c60-155">祝贺你</span><span class="sxs-lookup"><span data-stu-id="82c60-155">Congratulations</span></span>

<span data-ttu-id="82c60-156">在本教程中，你已了解如何在应用程序会话和应用程序重启之间保留 Azure 空间锚点，方法是将 Azure 空间锚 ID 保存到 HoloLens 上的本地磁盘。</span><span class="sxs-lookup"><span data-stu-id="82c60-156">In this tutorial you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="82c60-157">还了解了如何在多个设备之间共享 Azure 空间锚，以实现基本的多用户静态全息图共享体验。</span><span class="sxs-lookup"><span data-stu-id="82c60-157">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="82c60-158">在下一教程中，你将学习如何向用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="82c60-158">In the next tutorial you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="82c60-159">此反馈将包括有关定位点创建、环境理解质量以及 Azure 会话状态的信息。</span><span class="sxs-lookup"><span data-stu-id="82c60-159">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="82c60-160">如果没有反馈，用户可能不知道锚是否已成功上传到 Azure，无论环境质量是否足以用于创建定位点或当前状态。</span><span class="sxs-lookup"><span data-stu-id="82c60-160">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="82c60-161">下一课： 3. 显示 Azure 空间锚点反馈</span><span class="sxs-lookup"><span data-stu-id="82c60-161">Next Lesson: 3. Displaying Azure Spatial Anchor feedback</span></span>](mrlearning-asa-ch3.md)
