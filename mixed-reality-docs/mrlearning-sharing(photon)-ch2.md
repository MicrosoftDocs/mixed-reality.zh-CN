---
title: 多用户功能教程 - 3. 连接多个用户
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610933"
---
# <a name="2-connecting-multiple-users"></a><span data-ttu-id="6b0ca-105">2.连接多个用户</span><span class="sxs-lookup"><span data-stu-id="6b0ca-105">2. Connecting multiple users</span></span>

<span data-ttu-id="6b0ca-106">本教程介绍如何将多个用户连接为实时共享体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="6b0ca-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="6b0ca-107">在本教程结束时，你将能够在多个设备上运行应用程序，并让每个用户都能实时看到其他用户的头像移动。</span><span class="sxs-lookup"><span data-stu-id="6b0ca-107">By the end of the tutorial you will be able to run the application on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="6b0ca-108">目标</span><span class="sxs-lookup"><span data-stu-id="6b0ca-108">Objectives</span></span>

* <span data-ttu-id="6b0ca-109">了解如何在共享体验中连接多个用户</span><span class="sxs-lookup"><span data-stu-id="6b0ca-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="6b0ca-110">准备场景</span><span class="sxs-lookup"><span data-stu-id="6b0ca-110">Preparing the scene</span></span>

<span data-ttu-id="6b0ca-111">在本部分，你将通过添加一些教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="6b0ca-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="6b0ca-112">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “预制件”文件夹。   </span><span class="sxs-lookup"><span data-stu-id="6b0ca-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder.</span></span> <span data-ttu-id="6b0ca-113">在按住 CTRL 按钮的同时，单击“DebugWindow”  、“NetworkLobby”和  “SharedPlayground”，  以便选择这三个预制件：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-113">While holding down the CTRL button, click on **DebugWindow**, **NetworkLobby**, and **SharedPlayground** to select the three prefabs:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

<span data-ttu-id="6b0ca-115">在仍选中了这三个预制件的情况下，将其拖动到“层次结构”窗口中，以将其添加到场景：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-115">With the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="6b0ca-117">创建用户预制件</span><span class="sxs-lookup"><span data-stu-id="6b0ca-117">Creating the user prefab</span></span>

<span data-ttu-id="6b0ca-118">在本部分中，你将创建一个预制件，用于表示共享体验中的用户。</span><span class="sxs-lookup"><span data-stu-id="6b0ca-118">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="6b0ca-119">1.创建和配置用户</span><span class="sxs-lookup"><span data-stu-id="6b0ca-119">1. Create and configure the user</span></span>

<span data-ttu-id="6b0ca-120">在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”  将空对象添加到场景中，将该对象命名为“PhotonUser”  ，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-120">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="6b0ca-121">请确保将变换位置  设置为 X = 0，Y = 0，Z = 0：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-121">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

<span data-ttu-id="6b0ca-123">在仍选中了“PhotonUser”对象的情况下，在“检查器”窗口中，使用“添加组件”按钮将“Photon 用户(脚本)”组件添加到 PhotonUser 对象：   </span><span class="sxs-lookup"><span data-stu-id="6b0ca-123">With the **PhotonUser** object still selected, in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

<span data-ttu-id="6b0ca-125">在“检查器”窗口中，使用“添加组件”  按钮将“通用网络同步(脚本)”  组件添加到 PhotonUser 对象，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-125">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6b0ca-126">选中“是用户”  复选框</span><span class="sxs-lookup"><span data-stu-id="6b0ca-126">Check the **Is User** checkbox</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

<span data-ttu-id="6b0ca-128">在“检查器”窗口中，使用“添加组件”  按钮将“Photon 视图(脚本)”  组件添加到 PhotonUser 对象，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-128">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6b0ca-129">向“观察到的组件”  字段中分配“通用网络同步(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="6b0ca-129">To the **Observed Components** field, assign the Generic Net Sync (Script) component</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="6b0ca-131">2.创建头像</span><span class="sxs-lookup"><span data-stu-id="6b0ca-131">2. Create the avatar</span></span>

<span data-ttu-id="6b0ca-132">在“层次结构”窗口中，右键单击“PhotonUser”  对象，然后选择“3D 对象”   >   “球体”创建一个作为 PhotonUser 对象的子项的球体对象，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-132">In the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6b0ca-133">请确保将变换位置  设置为 X = 0，Y = 0，Z = 0</span><span class="sxs-lookup"><span data-stu-id="6b0ca-133">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="6b0ca-134">将变换标度  更改为适当的大小，例如 X = 0.15，Y = 0.15，Z = 0.15</span><span class="sxs-lookup"><span data-stu-id="6b0ca-134">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="6b0ca-136">3.创建预制件</span><span class="sxs-lookup"><span data-stu-id="6b0ca-136">3. Create the prefab</span></span>

<span data-ttu-id="6b0ca-137">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹：   </span><span class="sxs-lookup"><span data-stu-id="6b0ca-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

<span data-ttu-id="6b0ca-139">在“资源”文件夹仍处于选定状态的情况下，单击“层次结构”窗口中的“PhotonUser”对象并将其拖动到“资源”文件夹，以使 PhotonUser 对象成为预制件：   </span><span class="sxs-lookup"><span data-stu-id="6b0ca-139">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

<span data-ttu-id="6b0ca-141">在“层次结构”窗口中，右键单击“PhotonUser”  对象，然后选择“删除”  将其从场景中删除：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-141">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="6b0ca-143">配置 PUN 以将用户预制件实例化</span><span class="sxs-lookup"><span data-stu-id="6b0ca-143">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="6b0ca-144">在本部分中，你将配置项目以使用在上一部分中创建的 PhotonUser 预制件。</span><span class="sxs-lookup"><span data-stu-id="6b0ca-144">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="6b0ca-145">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。   </span><span class="sxs-lookup"><span data-stu-id="6b0ca-145">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="6b0ca-146">在“层次结构”窗口中，展开“NetworkLobby”  对象并选择“NetworkRoom”  子对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”  组件，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-146">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="6b0ca-147">向“Photon 用户预制件”  字段中分配来自“资源”文件夹的“PhotonUser”  预制件</span><span class="sxs-lookup"><span data-stu-id="6b0ca-147">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="6b0ca-149">尝试包含多个用户的体验</span><span class="sxs-lookup"><span data-stu-id="6b0ca-149">Trying the experience with multiple users</span></span>

<span data-ttu-id="6b0ca-150">如果现在生成了 Unity 项目并将其部署到 HoloLens，然后返回到 Unity，并且在应用程序运行于 HoloLens 上时按“玩游戏”按钮以进入“游戏”模式，那么，当你来回晃动头部 (HoloLens) 时，你将看到 HoloLens 用户头像移动：</span><span class="sxs-lookup"><span data-stu-id="6b0ca-150">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="6b0ca-152">有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)中的说明。</span><span class="sxs-lookup"><span data-stu-id="6b0ca-152">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="6b0ca-153">应用程序需要连接到 Photon，因此请确保计算机/设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="6b0ca-153">The application needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6b0ca-154">祝贺</span><span class="sxs-lookup"><span data-stu-id="6b0ca-154">Congratulations</span></span>

<span data-ttu-id="6b0ca-155">你已成功将项目配置为允许多个用户连接到相同体验并可看到彼此的移动。</span><span class="sxs-lookup"><span data-stu-id="6b0ca-155">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="6b0ca-156">在下一教程中，你将实现功能，以使对象的移动也可以在多个设备之间共享。</span><span class="sxs-lookup"><span data-stu-id="6b0ca-156">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

<span data-ttu-id="6b0ca-157">[下一教程：2.与多个用户共享对象移动](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="6b0ca-157">[Next tutorial: 2. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
