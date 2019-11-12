---
title: Azure 空间锚点教程-2。 保存、检索和共享 Azure 空间锚
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: a24d15f0c0fff045c01f6070027b7defa87c2416
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914458"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="d6a13-105">2. 保存、检索和共享 Azure 空间锚</span><span class="sxs-lookup"><span data-stu-id="d6a13-105">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="d6a13-106">在本教程中，我们将了解如何通过将定位信息保存到 HoloLens 2 的存储来跨多个应用会话保存 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="d6a13-106">In this tutorial, we will learn how to save our Azure Spatial Anchors across multiple app sessions by saving our anchor information to the HoloLens 2's storage.</span></span> <span data-ttu-id="d6a13-107">我们还将了解如何将此定位点信息共享到其他设备，以实现多设备锚点对齐。</span><span class="sxs-lookup"><span data-stu-id="d6a13-107">We will also learn how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="d6a13-108">目标</span><span class="sxs-lookup"><span data-stu-id="d6a13-108">Objectives</span></span>

* <span data-ttu-id="d6a13-109">了解如何保存和检索 HoloLens 2 本地磁盘中的 Azure 空间锚定信息，以便在应用会话之间保持持久性</span><span class="sxs-lookup"><span data-stu-id="d6a13-109">Learn how to save and retrieve Azure Spatial Anchor information from the HoloLens 2 local disk, for persistence between app sessions</span></span>

* <span data-ttu-id="d6a13-110">了解如何在多设备方案中的用户之间共享 Azure 空间锚点信息</span><span class="sxs-lookup"><span data-stu-id="d6a13-110">Learn how to share Azure Spatial Anchor information between users in a multi-device scenario</span></span>

## <a name="instructions"></a><span data-ttu-id="d6a13-111">说明</span><span class="sxs-lookup"><span data-stu-id="d6a13-111">Instructions</span></span>

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="d6a13-112">在应用会话之间保留 Azure 锚点-将定位点 ID 保存到磁盘</span><span class="sxs-lookup"><span data-stu-id="d6a13-112">Persist Azure anchors between app sessions - Save anchor ID to Disk</span></span>

1. <span data-ttu-id="d6a13-113">搜索并将 SaveAnchorToDisk prefab 添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="d6a13-113">Search for and add the SaveAnchorToDisk prefab to your scene.</span></span> <span data-ttu-id="d6a13-114">其中包括两个按钮，一个按钮用于将所有可用的 Azure 定位 Id 保存到 HoloLens 2 存储，另一个用于从磁盘检索任何 Id。</span><span class="sxs-lookup"><span data-stu-id="d6a13-114">These include two buttons, one button for saving any available Azure Anchor IDs to the HoloLens 2 storage, and another for retrieving any IDs from the disk.</span></span>

![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. <span data-ttu-id="d6a13-116">根据下面的说明配置每个按钮</span><span class="sxs-lookup"><span data-stu-id="d6a13-116">Configure Each button according to the instructions below</span></span>

   - <span data-ttu-id="d6a13-117">对于名为 SaveToDisk 的按钮，在 "按下" 事件触发器和 On Click 事件触发器下创建一个新事件。</span><span class="sxs-lookup"><span data-stu-id="d6a13-117">For the Button named SaveToDisk, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="d6a13-118">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 SaveAzureAnchorIDToDisk （）方法。</span><span class="sxs-lookup"><span data-stu-id="d6a13-118">Drag the ParentAnchor object into the empty field, and assign the SaveAzureAnchorIDToDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>
   
     > <span data-ttu-id="d6a13-119">注意：某些按钮可能会与场景中的其他按钮重叠。</span><span class="sxs-lookup"><span data-stu-id="d6a13-119">Note: some of the buttons may appear overlapping the other buttons in the scene.</span></span> <span data-ttu-id="d6a13-120">随意调整按钮的定位。</span><span class="sxs-lookup"><span data-stu-id="d6a13-120">Feel free to adjust the button's positioning.</span></span>

![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)


   - <span data-ttu-id="d6a13-124">对于名为 GetFromDisk 的按钮，在 "按下" 事件触发器和 On Click 事件触发器下创建一个新事件。</span><span class="sxs-lookup"><span data-stu-id="d6a13-124">For the Button named GetFromDisk, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="d6a13-125">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 LoadAzureAnchorIDsFromDisk （）方法。</span><span class="sxs-lookup"><span data-stu-id="d6a13-125">Drag the ParentAnchor object into the empty field, and assign the LoadAzureAnchorIDsFromDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="d6a13-126">按照教程1中的说明，将更新后的应用程序生成到你的设备。</span><span class="sxs-lookup"><span data-stu-id="d6a13-126">Follow the instructions from Tutorial 1 to build the updated application to your device.</span></span> <span data-ttu-id="d6a13-127">按下一课所述，按 "创建 Azure 锚点" 按钮后，现在可以通过按 "保存到磁盘" 按钮将 Azure 定位 ID 保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="d6a13-127">After pressing the Create Azure Anchor button, as you did in the previous lesson, you may now save the Azure Anchor ID to disk by pressing the save to disk button.</span></span>

4. <span data-ttu-id="d6a13-128">重新启动应用程序，启动 Azure 会话，按 "加载定位点 ID"，然后按 "查找 Azure 定位点"，找到与我们保存到磁盘的 ID 相关联的定位点。</span><span class="sxs-lookup"><span data-stu-id="d6a13-128">Restart the application, start the Azure Session, Press Load Anchor ID, and then press Locate Azure Anchor to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="d6a13-129">整个场景现在应在您之前保存锚点的位置上对齐！</span><span class="sxs-lookup"><span data-stu-id="d6a13-129">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

### <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="d6a13-130">在多个设备之间共享 Azure 锚</span><span class="sxs-lookup"><span data-stu-id="d6a13-130">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="d6a13-131">在本部分中，我们将了解如何在多个设备之间共享 Azure 锚 ID。</span><span class="sxs-lookup"><span data-stu-id="d6a13-131">In this section, we'll learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="d6a13-132">这将允许多个设备在 Azure 中查询相同的定位 ID，以允许我们的定位全息影像和场景进行立体调整。</span><span class="sxs-lookup"><span data-stu-id="d6a13-132">This will allow multiple devices to query Azure for the same anchor ID, allowing our anchored holograms and scenes to be spatially aligned.</span></span> <span data-ttu-id="d6a13-133">空间对齐（在多个设备之间的同一物理位置查看相同的全息影像）是 HoloLens 2 中的本地共享体验的关键所在。</span><span class="sxs-lookup"><span data-stu-id="d6a13-133">Spatial alignment (seeing the same holograms in the same physical location between multiple devices) is key to local shared experiences in the HoloLens 2.</span></span> <span data-ttu-id="d6a13-134">可以通过多种方式在设备之间传输有关 azure Id 的信息，包括 Azure 空间锚式共享体验教程[教程](mrlearning-sharing(photon)-ch1.md)中所述的方法。</span><span class="sxs-lookup"><span data-stu-id="d6a13-134">There are many ways to transfer information regarding azure IDs between devices, including methods outlined in the Azure Spatial Anchors shared experiences tutorials [Tutorials](mrlearning-sharing(photon)-ch1.md).</span></span> <span data-ttu-id="d6a13-135">此示例使用简单的 web 服务在设备之间上传和下载定位点 Id。</span><span class="sxs-lookup"><span data-stu-id="d6a13-135">This example uses a simple web service to upload and download Anchor IDs between devices.</span></span>

1. <span data-ttu-id="d6a13-136">将 ShareAnchor prefab 添加到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="d6a13-136">Add the ShareAnchor prefab into your hierarchy.</span></span> <span data-ttu-id="d6a13-137">此 prefab 将两个新按钮添加到场景中，一个用于上传定位点 ID 信息，另一个用于下载定位点 ID 信息。</span><span class="sxs-lookup"><span data-stu-id="d6a13-137">This prefab adds two new buttons to your scene, one for uploading anchor ID information and another for downloading anchor ID information.</span></span> 

![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. <span data-ttu-id="d6a13-139">根据下面的说明配置每个按钮</span><span class="sxs-lookup"><span data-stu-id="d6a13-139">Configure Each button according to the instructions below</span></span>

   - <span data-ttu-id="d6a13-140">对于名为 "SendSharedAnchor" 的按钮，请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。</span><span class="sxs-lookup"><span data-stu-id="d6a13-140">For the Button named, SendSharedAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="d6a13-141">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 ShareAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="d6a13-141">Drag the ParentAnchor object into the empty field, and assign the ShareAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

   - <span data-ttu-id="d6a13-144">对于名为 "GetSharedAnchor" 的按钮，请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。</span><span class="sxs-lookup"><span data-stu-id="d6a13-144">For the Button named, GetSharedAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="d6a13-145">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 GetSharedAzureAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="d6a13-145">Drag the ParentAnchor object into the empty field, and assign the GetSharedAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="d6a13-146">按照[教程 1](mrlearning-base-ch1.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="d6a13-146">Follow the instructions from [Tutorial 1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="d6a13-147">将更新后的应用程序生成到你的设备。</span><span class="sxs-lookup"><span data-stu-id="d6a13-147">to build the updated application to your device.</span></span> <span data-ttu-id="d6a13-148">按下一课中所述，按 "创建 Azure 锚点" 按钮后，现在可以通过按 "共享到其他设备" 按钮将 Azure 锚 ID 共享到其他设备。</span><span class="sxs-lookup"><span data-stu-id="d6a13-148">After pressing the Create Azure Anchor button, as you did in the previous lesson, you may now share the Azure Anchor ID to other devices by pressing the Share To Other Device button.</span></span>

   > <span data-ttu-id="d6a13-149">注意：选择父定位点并向下滚动到父定位点脚本。</span><span class="sxs-lookup"><span data-stu-id="d6a13-149">Note: Select the parent anchor and scroll down to the parent anchor script.</span></span> <span data-ttu-id="d6a13-150">确保你的公共共享 pin 是唯一的（你可以将 pin 更改为其他号码），以便在共享时知道你的共享。</span><span class="sxs-lookup"><span data-stu-id="d6a13-150">Ensure that your public sharing pin is unique (You can change the pin to some other number), so that when you share it, you know it is yours that you are sharing.</span></span> <span data-ttu-id="d6a13-151">可能有成千上万用户共享其 Azure 定位点，因此这样做可以确保共享正确的 Azure 锚。</span><span class="sxs-lookup"><span data-stu-id="d6a13-151">There could be thousands of users sharing their Azure anchors, so doing this will allow you to ensure you are sharing the correct Azure anchors.</span></span>
   > 

![module2chapter2step7bim](images/module2chapter2step7bim.PNG)

4. <span data-ttu-id="d6a13-153">如果有另一个 HoloLens 2 设备，则启动该应用程序，然后启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="d6a13-153">If you have another HoloLens 2 device, start the application and then start the Azure Session.</span></span> <span data-ttu-id="d6a13-154">按 "获取共享定位点 ID" 按钮，然后按 "查找 Azure 定位点" 按钮，找到与我们使用 web 服务共享的 ID 相关联的定位点。</span><span class="sxs-lookup"><span data-stu-id="d6a13-154">Press the Get Shared Anchor ID button, and then press the Locate Azure Anchor button to locate the anchor associated with the ID we shared using the web service.</span></span> <span data-ttu-id="d6a13-155">整个场景现在应靠下放置在另一个 HoloLens 2 设备上的位置！</span><span class="sxs-lookup"><span data-stu-id="d6a13-155">The entire scene should now snap into position, at where it was placed on the other HoloLens 2 device!</span></span> <span data-ttu-id="d6a13-156">如果只有一个 HoloLens 2，则仍可通过以下方式测试功能：重新启动应用程序、启动 Azure 会话，然后按 "获取共享定位点 ID" 按钮，然后按 "查找 Azure 定位点" 按钮，找到与我们的 ID 相关联的定位点，保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="d6a13-156">If you only have one HoloLens 2, you may still test functionality by restarting the application, starting the Azure Session, and then press the "Get Shared Anchor ID" button, and then press the "Locate Azure Anchor button" to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="d6a13-157">整个场景现在应在您之前保存锚点的位置上对齐！</span><span class="sxs-lookup"><span data-stu-id="d6a13-157">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

## <a name="congratulations"></a><span data-ttu-id="d6a13-158">祝贺</span><span class="sxs-lookup"><span data-stu-id="d6a13-158">Congratulations</span></span>
<span data-ttu-id="d6a13-159">在本课程中，你学习了如何通过将 Azure 空间锚定 ID 保存到 HoloLens 2 上的本地磁盘，在应用程序会话和应用程序重启之间保持 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="d6a13-159">In this Lesson you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens 2.</span></span> <span data-ttu-id="d6a13-160">还了解了如何在多个设备之间共享 Azure 空间锚，以实现基本的多用户静态全息图共享体验。</span><span class="sxs-lookup"><span data-stu-id="d6a13-160">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="d6a13-161">本文介绍如何在共享模块的最后一课中，将 Azure 空间锚点作为完全交互式本地共享体验的一部分实现。</span><span class="sxs-lookup"><span data-stu-id="d6a13-161">We learn how to implement Azure Spatial Anchors as part of a fully interactive local shared experience during the final lesson of the Sharing Module.</span></span> <span data-ttu-id="d6a13-162">本地共享体验可能包括同步的3D 对象位置、旋转和缩放、每个用户的标识符以及共享应用程序状态等功能。</span><span class="sxs-lookup"><span data-stu-id="d6a13-162">A local sharing experience may include functionality such as synchronized 3D object position, rotation, and scale, identifiers for each user, and shared application states.</span></span> <span data-ttu-id="d6a13-163">Azure 空间锚点为每个参与者提供一个公共锚，使所有用户都能看到同一物理位置中的虚拟对象，从而增强了这些共享方案。</span><span class="sxs-lookup"><span data-stu-id="d6a13-163">Azure Spatial Anchors enhances these shared scenarios by providing each participant with a common anchor that lets all users see virtual objects in the same physical location.</span></span> <span data-ttu-id="d6a13-164">这适用于各种设备平台，包括 HoloLens、Android 和 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="d6a13-164">This is true across a range of device platforms, including HoloLens, Android, and iOS devices.</span></span> <span data-ttu-id="d6a13-165">若要了解如何开发共享体验，请完成共享模块中的所有课程。</span><span class="sxs-lookup"><span data-stu-id="d6a13-165">To learn how to develop a shared experience, complete all lessons in the Sharing module.</span></span>

<span data-ttu-id="d6a13-166">在下一课中，我们将学习如何向用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="d6a13-166">In the next Lesson, we will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="d6a13-167">此反馈将包括有关定位点创建、环境理解质量以及 Azure 会话状态的信息。</span><span class="sxs-lookup"><span data-stu-id="d6a13-167">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="d6a13-168">如果没有反馈，用户可能不知道某个定位点是否已成功上传到 Azure，无论该环境的质量是否足以用于创建定位点或当前状态。</span><span class="sxs-lookup"><span data-stu-id="d6a13-168">Without feedback, users may not know whether an anchor has successfully been upload to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="d6a13-169">下一课： 3. 显示 Azure 空间锚点反馈</span><span class="sxs-lookup"><span data-stu-id="d6a13-169">Next Lesson: 3. Displaying Azure Spatial Anchor feedback</span></span>](mrlearning-asa-ch3.md)

