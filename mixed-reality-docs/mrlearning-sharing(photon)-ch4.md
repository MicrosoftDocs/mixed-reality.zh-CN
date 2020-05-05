---
title: 多用户功能教程 - 5. 将 Azure 空间定位点集成到共享体验中
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604968"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="7c747-105">4.将 Azure 空间定位点集成到共享体验中</span><span class="sxs-lookup"><span data-stu-id="7c747-105">4. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="7c747-106">本教程介绍如何将 Azure 空间定位点 (ASA) 集成到共享体验中。</span><span class="sxs-lookup"><span data-stu-id="7c747-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="7c747-107">ASA 允许多台设备具有一个对物理环境的共同引用，从而使用户能够在其实际物理位置看到彼此，并看到同一位置中的共享体验。</span><span class="sxs-lookup"><span data-stu-id="7c747-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="7c747-108">目标</span><span class="sxs-lookup"><span data-stu-id="7c747-108">Objectives</span></span>

* <span data-ttu-id="7c747-109">将 ASA 集成到共享体验，以实现多设备空间配准</span><span class="sxs-lookup"><span data-stu-id="7c747-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="7c747-110">了解 ASA 在本地共享体验上下文中的基本工作原理</span><span class="sxs-lookup"><span data-stu-id="7c747-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="7c747-111">准备场景</span><span class="sxs-lookup"><span data-stu-id="7c747-111">Preparing the scene</span></span>

<span data-ttu-id="7c747-112">在“层次结构”窗口中，展开“SharedPlayground”  对象，然后展开“TableAnchor”  对象以公开其子对象：</span><span class="sxs-lookup"><span data-stu-id="7c747-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

<span data-ttu-id="7c747-114">在“项目”窗口中，导航到“资产”   > “MRTK.Tutorials.MultiUserCapabilities”   > “预制件”  文件夹，然后将“Buttons”  预制件拖动到“层次结构”窗口中“TableAnchor”  子对象的顶部，以将其作为 TableAnchor 对象的子项添加到场景：</span><span class="sxs-lookup"><span data-stu-id="7c747-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab on top of the **TableAnchor** child object in the Hierarchy window to add it to your scene as a child of the TableAnchor object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="7c747-116">配置按钮以操作场景</span><span class="sxs-lookup"><span data-stu-id="7c747-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="7c747-117">在本部分中，你将配置一系列按钮事件，用于演示如何使用 Azure 空间定位点实现共享体验中的空间配准。</span><span class="sxs-lookup"><span data-stu-id="7c747-117">In this section, you will configure a series of button events that demonstrate the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="7c747-118">在“层次结构”窗口中展开“Button”对象，然后选择名为“StartAzureSession”的第一个子按钮对象：  </span><span class="sxs-lookup"><span data-stu-id="7c747-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

<span data-ttu-id="7c747-120">在“检查器”窗口中，找到“可交互(脚本)”  组件，并按如下所示配置 OnClick ()  事件：</span><span class="sxs-lookup"><span data-stu-id="7c747-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="7c747-121">向“无(对象)”  字段中分配“TableAnchor”  对象</span><span class="sxs-lookup"><span data-stu-id="7c747-121">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="7c747-122">从“无函数”  下拉列表中，选择“AnchorModuleScript”   > “StartAzureSession ()”  函数</span><span class="sxs-lookup"><span data-stu-id="7c747-122">From **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

<span data-ttu-id="7c747-124">在“层次结构”窗口中，选择名为“CreateAzureAnchor”  的第二个子按钮对象，然后在“检查器”窗口中，找到“可交互(脚本)”  组件，并按如下所示配置 OnClick ()  事件：</span><span class="sxs-lookup"><span data-stu-id="7c747-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="7c747-125">向“无(对象)”  字段中分配“TableAnchor”  对象</span><span class="sxs-lookup"><span data-stu-id="7c747-125">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="7c747-126">从“无函数”  下拉列表中，选择“AnchorModuleScript”   > “CreateAzureAnchor ()”  函数</span><span class="sxs-lookup"><span data-stu-id="7c747-126">From **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="7c747-127">向出现的新“无(游戏对象)”  字段中分配“TableAnchor”  对象</span><span class="sxs-lookup"><span data-stu-id="7c747-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

<span data-ttu-id="7c747-129">在“层次结构”窗口中，选择名为“ShareAzureAnchor”  的第三个子按钮对象，然后在“检查器”窗口中，找到“可交互(脚本)”  组件，并按如下所示配置 OnClick ()  事件：</span><span class="sxs-lookup"><span data-stu-id="7c747-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="7c747-130">向“无(对象)”  字段中分配“TableAnchor”  对象</span><span class="sxs-lookup"><span data-stu-id="7c747-130">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="7c747-131">从“无函数”  下拉列表中，选择“SharingModuleScript”   > “ShareAzureAnchor ()”  函数</span><span class="sxs-lookup"><span data-stu-id="7c747-131">From **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

<span data-ttu-id="7c747-133">在“层次结构”窗口中，选择名为“GetAzureAnchor”  的第四个子按钮对象，然后在“检查器”窗口中，找到“可交互(脚本)”  组件，并按如下所示配置 OnClick ()  事件：</span><span class="sxs-lookup"><span data-stu-id="7c747-133">In the Hierarchy window, select the forth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="7c747-134">向“无(对象)”  字段中分配“TableAnchor”  对象</span><span class="sxs-lookup"><span data-stu-id="7c747-134">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="7c747-135">从“无函数”  下拉列表中，选择“SharingModuleScript”   > “GetAzureAnchor ()”  函数</span><span class="sxs-lookup"><span data-stu-id="7c747-135">From **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="7c747-137">将场景连接到 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="7c747-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="7c747-138">在“层次结构”窗口中，展开“SharedPlayground”  对象，然后选择“TableAnchor”  对象。</span><span class="sxs-lookup"><span data-stu-id="7c747-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span> <span data-ttu-id="7c747-139">然后，在“检查器”窗口中，找到“空间定位点管理器(脚本)”  组件，并使用来自 Azure 空间定位点帐户（该帐户作为本教程系列[必备条件](mrlearning-sharing(photon)-ch1.md#prerequisites)的一部分创建）的凭据配置“凭据”  部分：</span><span class="sxs-lookup"><span data-stu-id="7c747-139">Then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mrlearning-sharing(photon)-ch1.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="7c747-140">在“空间定位点帐户 ID”  字段中，粘贴来自你的 Azure 空间定位点帐户的“帐户 ID” </span><span class="sxs-lookup"><span data-stu-id="7c747-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="7c747-141">在“空间定位点帐户密钥”  字段中，  粘贴来自你的 Azure 空间定位点帐户的主“访问密钥”或辅助“访问密钥”</span><span class="sxs-lookup"><span data-stu-id="7c747-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

<span data-ttu-id="7c747-143">在仍选中“TableAnchor”  对象的情况下，在“检查器”窗口中，确保已启用所有脚本组件：</span><span class="sxs-lookup"><span data-stu-id="7c747-143">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are enabled:</span></span>

* <span data-ttu-id="7c747-144">选中“空间定位点管理器(脚本)”组件旁边的复选框以启用该组件 </span><span class="sxs-lookup"><span data-stu-id="7c747-144">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="7c747-145">选中“空间模块脚本(脚本)”组件旁边的复选框以启用该组件 </span><span class="sxs-lookup"><span data-stu-id="7c747-145">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="7c747-146">选中“共享模块脚本(脚本)”组件旁边的复选框以启用该组件 </span><span class="sxs-lookup"><span data-stu-id="7c747-146">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="7c747-148">尝试带有空间配准的体验</span><span class="sxs-lookup"><span data-stu-id="7c747-148">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="7c747-149">Azure 空间定位点不能在 Unity 中运行。</span><span class="sxs-lookup"><span data-stu-id="7c747-149">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="7c747-150">因此，若要测试 Azure 空间定位点功能，需将项目部署到至少两个 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="7c747-150">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two HoloLens devices.</span></span>

<span data-ttu-id="7c747-151">如果现在生成 Unity 项目并将其部署到两个 HoloLens 设备，则可以通过共享 Azure 定位点 ID 在设备之间实现空间配准。</span><span class="sxs-lookup"><span data-stu-id="7c747-151">If you now build and deploy the Unity project to two HoloLens devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="7c747-152">若要进行测试，可执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="7c747-152">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="7c747-153">在 HoloLens 设备 1 上：**启动应用程序**（火箭发射器已实例化并置于台子上）</span><span class="sxs-lookup"><span data-stu-id="7c747-153">On HoloLens device 1: **Start the application** (the Rocket Launcher is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="7c747-154">在 HoloLens 设备 2 上：**启动应用程序**（这两个用户都看到带有火箭启动器的台子，但是，该台子未出现在同一位置，用户头像未出现在用户所在的位置）</span><span class="sxs-lookup"><span data-stu-id="7c747-154">On HoloLens device 2: **Start the application** (both users see the table with the Rocket Launcher, however, the table does not appear in the same place and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="7c747-155">在 HoloLens 设备 1 上：按“启动 Azure 会话”  按钮</span><span class="sxs-lookup"><span data-stu-id="7c747-155">On HoloLens device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="7c747-156">在 HoloLens 设备 1 上：按“创建 Azure 定位点”  按钮（在 TableAnchor 对象的位置创建定位点，并将定位点信息存储在 Azure 资源中）。</span><span class="sxs-lookup"><span data-stu-id="7c747-156">On HoloLens device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="7c747-157">在 HoloLens 设备 1 上：按“共享 Azure 定位点”  按钮（与其他用户实时共享定位点 ID）</span><span class="sxs-lookup"><span data-stu-id="7c747-157">On HoloLens device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="7c747-158">在 HoloLens 设备 2 上：按“启动 Azure 会话”  按钮</span><span class="sxs-lookup"><span data-stu-id="7c747-158">On HoloLens device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="7c747-159">在 HoloLens 设备 2 上：按“获取 Azure 定位点”  按钮（连接到 Azure 资源以检索共享定位点 ID 的定位点信息，然后将 TableAnchor 对象移到通过 HoloLens 设备 1 创建定位点的位置）</span><span class="sxs-lookup"><span data-stu-id="7c747-159">On HoloLens device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the HoloLens device 1)</span></span>

## <a name="congratulations"></a><span data-ttu-id="7c747-160">祝贺</span><span class="sxs-lookup"><span data-stu-id="7c747-160">Congratulations</span></span>

<span data-ttu-id="7c747-161">在本教程中，你已了解如何集成 Azure 中强大的空间定位点功能，以在共享体验中为设备实现空间配准。</span><span class="sxs-lookup"><span data-stu-id="7c747-161">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span> <span data-ttu-id="7c747-162">这也是此教程系列的总结。在此教程系列中，你已学会了如何设置 Photon 帐户、将 Photon 和 PUN 集成到 Unity 应用程序中、配置用户头像和共享的对象，并最终使用 ASA 来为多个参与者实现空间配准。</span><span class="sxs-lookup"><span data-stu-id="7c747-162">This also concludes this tutorial series where you have learned how to set up a Photon account and application, integrate Photon and PUN into a Unity application, configure user avatars and shared objects, and finally align multiple participants using ASA.</span></span>
