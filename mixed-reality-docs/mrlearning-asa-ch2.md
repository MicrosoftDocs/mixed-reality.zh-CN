---
title: MR 学习 ASA 模块 Azure HoloLens 2 上的空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: f8a52660fe05b6ed4508321ed246b8e299b75bca
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523332"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="9acc3-104">2.保存、 检索和共享 Azure 空间的定位点</span><span class="sxs-lookup"><span data-stu-id="9acc3-104">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="9acc3-105">在本教程中，我们将了解如何在多个应用程序会话之间保存我们 Azure 空间的定位点，通过将我们定位点的信息保存到 HoloLens 2 的磁盘。</span><span class="sxs-lookup"><span data-stu-id="9acc3-105">In this tutorial, we will learn how to save our Azure Spatial Anchors across multiple app sessions by saving our anchor information to the HoloLens 2's disk.</span></span> <span data-ttu-id="9acc3-106">我们还将了解如何共享此定位点的信息对其他设备的多设备定位点对齐方式。</span><span class="sxs-lookup"><span data-stu-id="9acc3-106">We will also learn how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="9acc3-107">目标</span><span class="sxs-lookup"><span data-stu-id="9acc3-107">Objectives</span></span>

* <span data-ttu-id="9acc3-108">了解如何保存和检索 Azure 空间的定位点信息从 HoloLens 2 本地磁盘，以便进行应用程序会话之间保留</span><span class="sxs-lookup"><span data-stu-id="9acc3-108">Learn how to save and retrieve Azure Spatial Anchor information from the HoloLens 2 local disk, for persistence between app sessions</span></span>

* <span data-ttu-id="9acc3-109">了解如何在 Azure 空间的定位点之间共享信息的多设备方案中的用户</span><span class="sxs-lookup"><span data-stu-id="9acc3-109">Learn how to share Azure Spatial Anchor information between users in a multi-device scenario</span></span>

  

## <a name="instructions"></a><span data-ttu-id="9acc3-110">说明</span><span class="sxs-lookup"><span data-stu-id="9acc3-110">Instructions</span></span>

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="9acc3-111">保留应用程序会话的保存到磁盘的锚点 ID 之间的 Azure 定位点</span><span class="sxs-lookup"><span data-stu-id="9acc3-111">Persist Azure Anchors Between App Sessions - Save Anchor ID to Disk</span></span>

1. <span data-ttu-id="9acc3-112">搜索并将 SaveAnchorToDisk 预设可添加到您的场景。</span><span class="sxs-lookup"><span data-stu-id="9acc3-112">Search for and add the SaveAnchorToDisk prefab to your scene.</span></span> <span data-ttu-id="9acc3-113">其中包括两个按钮、 一个按钮用于将任何可用的 Azure 定位标记 Id 保存到 HoloLens 2 磁盘，另一个用于从磁盘检索任何 Id。</span><span class="sxs-lookup"><span data-stu-id="9acc3-113">These include two buttons, one button for saving any available Azure Anchor IDs to the HoloLens 2 disk, and another for retrieving any IDs from the disk.</span></span>

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. <span data-ttu-id="9acc3-115">配置下面的说明根据每个按钮</span><span class="sxs-lookup"><span data-stu-id="9acc3-115">Configure Each button according to the instructions below</span></span>
   - <span data-ttu-id="9acc3-116">对于名为 SaveToDisk 按钮，创建新的事件下按下按钮事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="9acc3-116">For the Button named SaveToDisk, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="9acc3-117">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 SaveAzureAnchorIDToDisk() 方法。</span><span class="sxs-lookup"><span data-stu-id="9acc3-117">Drag the ParentAnchor object into the empty field, and assign the SaveAzureAnchorIDToDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>
   
     > <span data-ttu-id="9acc3-118">注意： 某些按钮可能会出现重叠的场景中的其他按钮。</span><span class="sxs-lookup"><span data-stu-id="9acc3-118">Note: some of the buttons may appear overlapping the other buttons in the scene.</span></span> <span data-ttu-id="9acc3-119">随意调整按钮的位置。</span><span class="sxs-lookup"><span data-stu-id="9acc3-119">Feel free to adjust the button's positioning.</span></span>
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - <span data-ttu-id="9acc3-123">对于名为 GetFromDisk 按钮，创建新的事件下按下按钮事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="9acc3-123">For the Button named GetFromDisk, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="9acc3-124">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 LoadAzureAnchorIDsFromDisk() 方法。</span><span class="sxs-lookup"><span data-stu-id="9acc3-124">Drag the ParentAnchor object into the empty field, and assign the LoadAzureAnchorIDsFromDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="9acc3-125">从 Tutoiral 1 以构建到你的设备更新的应用程序按照的说明。</span><span class="sxs-lookup"><span data-stu-id="9acc3-125">Follow the instructions from Tutoiral 1 to build the updated application to your device.</span></span> <span data-ttu-id="9acc3-126">按创建 Azure 定位点按钮之后, 就像在上一课中现在可以保存 Azure 锚点 ID 到磁盘按保存到磁盘按钮。</span><span class="sxs-lookup"><span data-stu-id="9acc3-126">After pressing the Create Azure Anchor button, as you did in the previous lesson, you may now save the Azure Anchor ID to disk by pressing the save to disk button.</span></span>

4. <span data-ttu-id="9acc3-127">重新启动该应用程序，启动 Azure 会话，按负载锚点 ID，然后按找到 Azure 定位点定位与我们保存到磁盘的 ID 相关联的定位点。</span><span class="sxs-lookup"><span data-stu-id="9acc3-127">Restart the application, start the Azure Session, Press Load Anchor ID, and then press Locate Azure Anchor to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="9acc3-128">在整个场景现在应对齐到位，在位置定位点以前保存 ！</span><span class="sxs-lookup"><span data-stu-id="9acc3-128">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

### <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="9acc3-129">在多个设备之间共享 Azure 的定位点</span><span class="sxs-lookup"><span data-stu-id="9acc3-129">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="9acc3-130">在本部分中，我们将了解如何共享多个设备之间的 Azure 锚点 ID。</span><span class="sxs-lookup"><span data-stu-id="9acc3-130">In this section, we'll learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="9acc3-131">这将允许多个设备查询相同的锚点 ID，Azure 允许我们锚定的全息和场景论据在空间上对齐。</span><span class="sxs-lookup"><span data-stu-id="9acc3-131">This will allow multiple devices to query Azure for the same anchor ID, allowing our anchored holograms and scenes to be spatially aligned.</span></span> <span data-ttu-id="9acc3-132">空间对齐方式 （请参阅在多个设备之间的相同物理位置相同的全息） 是 HoloLens 2 中的密钥到本地共享的体验。</span><span class="sxs-lookup"><span data-stu-id="9acc3-132">Spatial alignment (seeing the same holograms in the same physical location between multiple devices) is key to local shared experiences in the HoloLens 2.</span></span> <span data-ttu-id="9acc3-133">有很多种传输设备，包括方法之间的相关 azure Id 中 Azure 空间的定位点的共享体验教程所述的信息 (TODO： 添加链接。)此示例使用简单的 web 服务上传和下载设备之间的定位标记 Id。</span><span class="sxs-lookup"><span data-stu-id="9acc3-133">There are many ways to transfer information regarding azure IDs between devices, including methods outlined in the Azure Spatial Anchors shared experiences tutorials (TODO: add link.) This example uses a simple web service to upload and download Anchor IDs between devices.</span></span>

1. <span data-ttu-id="9acc3-134">将添加到你的层次结构 ShareAnchor 预设。</span><span class="sxs-lookup"><span data-stu-id="9acc3-134">Add the ShareAnchor prefab into your hierarchy.</span></span> <span data-ttu-id="9acc3-135">此预设可将两个新按钮添加到您的场景;一个用于上传锚点 ID 信息，另一个用于下载的定位点 ID 信息。</span><span class="sxs-lookup"><span data-stu-id="9acc3-135">This prefab adds two new buttons to your scene; one for uploading anchor ID information and another for downloading anchor ID information.</span></span> 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. <span data-ttu-id="9acc3-137">配置下面的说明根据每个按钮</span><span class="sxs-lookup"><span data-stu-id="9acc3-137">Configure Each button according to the instructions below</span></span>

   - <span data-ttu-id="9acc3-138">对于名为 SendSharedAnchor，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="9acc3-138">For the Button named, SendSharedAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="9acc3-139">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 ShareAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="9acc3-139">Drag the ParentAnchor object into the empty field, and assign the ShareAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - <span data-ttu-id="9acc3-142">对于名为 GetSharedAnchor，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="9acc3-142">For the Button named, GetSharedAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="9acc3-143">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 GetSharedAzureAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="9acc3-143">Drag the ParentAnchor object into the empty field, and assign the GetSharedAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="9acc3-144">请按照中的说明[教程 1](mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="9acc3-144">Follow the instructions from [Tutorial 1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="9acc3-145">若要构建到你的设备更新的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9acc3-145">to build the updated application to your device.</span></span> <span data-ttu-id="9acc3-146">按创建 Azure 定位点按钮之后, 就像在上一课中现在，您可能会共享 Azure 锚点 ID 与其他设备通过按共享到其他设备按钮。</span><span class="sxs-lookup"><span data-stu-id="9acc3-146">After pressing the Create Azure Anchor button, as you did in the previous lesson, you may now share the Azure Anchor ID to other devices by pressing the Share To Other Device button.</span></span>

   > <span data-ttu-id="9acc3-147">注意：选择父定位点和向下的滚动至父定位点脚本。</span><span class="sxs-lookup"><span data-stu-id="9acc3-147">Note: Select the parent anchor and scroll down to the parent anchor script.</span></span> <span data-ttu-id="9acc3-148">请确保公共共享 pin 是唯一的以便共享时，您知道它是你要共享。</span><span class="sxs-lookup"><span data-stu-id="9acc3-148">Ensure that your public sharing pin is unique, so that when you share it, you know it is yours that you are sharing.</span></span> <span data-ttu-id="9acc3-149">可能有数千个用户共享其 Azure 的定位点，以便执行此操作将允许您以确保您要共享的正确 Azure 定位点。</span><span class="sxs-lookup"><span data-stu-id="9acc3-149">There could be thousands of users sharing their Azure anchors, so doing this will allow you to ensure you are sharing the correct Azure anchors.</span></span>

4. <span data-ttu-id="9acc3-150">如果你有其他 HoloLens 2 设备，启动该应用程序，然后启动 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="9acc3-150">If you have another HoloLens 2 device, start the application and then start the Azure Session.</span></span> <span data-ttu-id="9acc3-151">按获取共享的锚点 ID 按钮，然后按找到 Azure 定位点按钮以找到与我们保存到磁盘的 ID 相关联的定位点。</span><span class="sxs-lookup"><span data-stu-id="9acc3-151">Press the Get Shared Anchor ID button, and then press the Locate Azure Anchor button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="9acc3-152">在整个场景现在应对齐到位，放置在另一 HoloLens 2 台设备上查看 where ！</span><span class="sxs-lookup"><span data-stu-id="9acc3-152">The entire scene should now snap into position, at the where it was placed on the other HoloLens 2 device!</span></span> <span data-ttu-id="9acc3-153">如果你只有一个 HoloLens 2，您可能仍测试功能通过重新启动该应用程序，启动 Azure 会话，然后按"获取共享的锚点 ID"按钮，然后按找到 Azure 定位点按钮以找到定位点与相关联我们将保存到磁盘的 ID。</span><span class="sxs-lookup"><span data-stu-id="9acc3-153">If you only have one HoloLens 2, you may still test functionality by restarting the application, starting the Azure Session, and then Press the "Get Shared Anchor ID" button button, and then press the Locate Azure Anchor button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="9acc3-154">在整个场景现在应对齐到位，在位置定位点以前保存 ！</span><span class="sxs-lookup"><span data-stu-id="9acc3-154">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

## <a name="congratulations"></a><span data-ttu-id="9acc3-155">祝贺</span><span class="sxs-lookup"><span data-stu-id="9acc3-155">Congratulations</span></span>
<span data-ttu-id="9acc3-156">本课程中您学习了如何通过将 Azure 空间锚点 ID 保存到本地磁盘，在 HoloLens 2 上应用程序重新启动应用程序会话之间保留 Azure 空间的定位点。</span><span class="sxs-lookup"><span data-stu-id="9acc3-156">In this Lesson you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens 2.</span></span> <span data-ttu-id="9acc3-157">您还学习了如何为用户提供基本的多用户、 静态全息图共享体验的多个设备之间共享 Azure 空间的定位点。</span><span class="sxs-lookup"><span data-stu-id="9acc3-157">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="9acc3-158">我们了解如何实现 Azure 空间的定位点在最后一课中的共享模块的完全交互式的本地共享体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="9acc3-158">We learn how to implement Azure Spatial Anchors as part of a fully interactive local shared experience during the final lesson of the Sharing Module.</span></span> <span data-ttu-id="9acc3-159">本地共享体验可能包括功能，例如为每个用户已同步的三维对象位置、 旋转和缩放、 标识符和共享应用程序状态。</span><span class="sxs-lookup"><span data-stu-id="9acc3-159">A local sharing experience may include functionality such as synchronized 3D object position, rotation, and scale, identifiers for each user, and shared application states.</span></span> <span data-ttu-id="9acc3-160">Azure 空间的定位点的每个参与者提供常见的定位点，可让所有用户看到的相同物理位置中的虚拟对象，从而增强了这些共享的方案。</span><span class="sxs-lookup"><span data-stu-id="9acc3-160">Azure Spatial Anchors enhances these shared scenarios by providing each participant with a common anchor that lets all users see virtual objects in the same physical location.</span></span> <span data-ttu-id="9acc3-161">这适用于一系列的设备平台，包括 HoloLens、 Android 和 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="9acc3-161">This is true across a range of device platforms, including HoloLens, Android, and iOS devices.</span></span> <span data-ttu-id="9acc3-162">若要了解如何开发共享的体验，完成共享模块中的所有课程。</span><span class="sxs-lookup"><span data-stu-id="9acc3-162">To learn how to develop a shared experience, complete all lessons in the Sharing module.</span></span>

<span data-ttu-id="9acc3-163">在下一课中，我们将了解如何向用户提供实时反馈。</span><span class="sxs-lookup"><span data-stu-id="9acc3-163">In the next Lesson, we will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="9acc3-164">此反馈将包括有关定位点创建、 环境了解质量和 Azure 的会话的状态信息。</span><span class="sxs-lookup"><span data-stu-id="9acc3-164">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="9acc3-165">而无需反馈，用户可能不知道是否定位点已成功上的传到 Azure，环境的质量是否足以满足定位点创建过程中或当前状态。</span><span class="sxs-lookup"><span data-stu-id="9acc3-165">Without feedback, users may not know whether an anchor has successfully been upload to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="9acc3-166">下一课：ASA 教程 3</span><span class="sxs-lookup"><span data-stu-id="9acc3-166">Next Lesson: ASA Tutorial 3</span></span>](mrlearning-asa-ch3.md)

