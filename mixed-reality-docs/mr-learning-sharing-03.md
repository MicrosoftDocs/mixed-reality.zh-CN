---
title: 多用户功能教程 - 3. 连接多个用户
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 56bd4e251d11e39d5495d3fcaf4e3c5fc4e087de
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304812"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="6384d-105">3.连接多个用户</span><span class="sxs-lookup"><span data-stu-id="6384d-105">3. Connecting multiple users</span></span>

<span data-ttu-id="6384d-106">本教程介绍如何将多个用户连接为实时共享体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="6384d-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="6384d-107">在本教程结束时，你将能够在多台设备上运行应用，并让每位用户都能实时看到其他用户的头像移动。</span><span class="sxs-lookup"><span data-stu-id="6384d-107">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="6384d-108">目标</span><span class="sxs-lookup"><span data-stu-id="6384d-108">Objectives</span></span>

* <span data-ttu-id="6384d-109">了解如何在共享体验中连接多个用户</span><span class="sxs-lookup"><span data-stu-id="6384d-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="6384d-110">准备场景</span><span class="sxs-lookup"><span data-stu-id="6384d-110">Preparing the scene</span></span>

<span data-ttu-id="6384d-111">在本部分，你将通过添加一些教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="6384d-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="6384d-112">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “预制件”文件夹，然后单击以下预制件并将其拖动到“层次结构”窗口中，从而将其添加到场景中  ：</span><span class="sxs-lookup"><span data-stu-id="6384d-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="6384d-113">NetworkLobby 预制件</span><span class="sxs-lookup"><span data-stu-id="6384d-113">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="6384d-114">SharedPlayground 预制件</span><span class="sxs-lookup"><span data-stu-id="6384d-114">**SharedPlayground** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="6384d-116">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹，然后单击以下预制件并将其拖动到“层次结构”窗口中，从而将其添加到场景中  ：</span><span class="sxs-lookup"><span data-stu-id="6384d-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="6384d-117">DebugWindow 预制件</span><span class="sxs-lookup"><span data-stu-id="6384d-117">**DebugWindow** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="6384d-119">创建用户预制件</span><span class="sxs-lookup"><span data-stu-id="6384d-119">Creating the user prefab</span></span>

<span data-ttu-id="6384d-120">在本部分中，你将创建一个预制件，用于表示共享体验中的用户。</span><span class="sxs-lookup"><span data-stu-id="6384d-120">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="6384d-121">1.创建和配置用户</span><span class="sxs-lookup"><span data-stu-id="6384d-121">1. Create and configure the user</span></span>

<span data-ttu-id="6384d-122">在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”将空对象添加到场景中，将该对象命名为“PhotonUser”，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="6384d-122">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="6384d-123">请确保将变换位置设置为 X = 0，Y = 0，Z = 0：</span><span class="sxs-lookup"><span data-stu-id="6384d-123">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="6384d-125">在“层次结构”窗口中，选择“PhotonUser”对象，然后在检查器窗口中，使用“添加组件”按钮将“Photon 用户(脚本)”组件添加到 PhotonUser 对象：  </span><span class="sxs-lookup"><span data-stu-id="6384d-125">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="6384d-127">在检查器窗口中，使用“添加组件”按钮将“通用网络同步(脚本)”组件添加到 PhotonUser 对象，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="6384d-127">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6384d-128">选中“是用户”复选框</span><span class="sxs-lookup"><span data-stu-id="6384d-128">Check the **Is User** checkbox</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="6384d-130">在检查器窗口中，使用“添加组件”按钮将“Photon 视图(脚本)”组件添加到 PhotonUser 对象，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="6384d-130">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6384d-131">向“观察到的组件”字段分配“通用网络同步(脚本)”组件 </span><span class="sxs-lookup"><span data-stu-id="6384d-131">To the **Observed Components** field, assign the **Generic Net Sync (Script)** component</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="6384d-133">2.创建头像</span><span class="sxs-lookup"><span data-stu-id="6384d-133">2. Create the avatar</span></span>

<span data-ttu-id="6384d-134">在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “StandardAssets” > “材料”文件夹，找到 MRTK 材料    。</span><span class="sxs-lookup"><span data-stu-id="6384d-134">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="6384d-135">然后，在“层次结构”窗口中，右键单击 PhotonUser 对象，然后选择“3D 对象” > “球体”来创建一个球体对象作为 PhotonUser 对象的子项，并按如下所示对它进行配置  ：</span><span class="sxs-lookup"><span data-stu-id="6384d-135">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6384d-136">请确保将变换位置设置为 X = 0，Y = 0，Z = 0</span><span class="sxs-lookup"><span data-stu-id="6384d-136">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="6384d-137">将变换标度更改为适当的大小，例如 X = 0.15，Y = 0.15，Z = 0.15</span><span class="sxs-lookup"><span data-stu-id="6384d-137">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="6384d-138">在“MeshRenderer”>“材料”>“元素 0”字段中，指定 MRTK_Standard_White 材料 </span><span class="sxs-lookup"><span data-stu-id="6384d-138">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="6384d-140">3.创建预制件</span><span class="sxs-lookup"><span data-stu-id="6384d-140">3. Create the prefab</span></span>

<span data-ttu-id="6384d-141">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹：  </span><span class="sxs-lookup"><span data-stu-id="6384d-141">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="6384d-143">在“资源”文件夹仍处于选定状态的情况下，单击“层次结构”窗口中的“PhotonUser”对象并将其拖动到“资源”文件夹，以使 PhotonUser 对象成为预制件：  </span><span class="sxs-lookup"><span data-stu-id="6384d-143">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="6384d-145">在“层次结构”窗口中，右键单击“PhotonUser”对象，然后选择“删除”将其从场景中删除：</span><span class="sxs-lookup"><span data-stu-id="6384d-145">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="6384d-147">配置 PUN 以将用户预制件实例化</span><span class="sxs-lookup"><span data-stu-id="6384d-147">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="6384d-148">在本部分中，你将配置项目以使用在上一部分中创建的 PhotonUser 预制件。</span><span class="sxs-lookup"><span data-stu-id="6384d-148">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="6384d-149">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。  </span><span class="sxs-lookup"><span data-stu-id="6384d-149">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="6384d-150">在“层次结构”窗口中，展开“NetworkLobby”对象并选择“NetworkRoom”子对象，然后在检查器窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="6384d-150">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="6384d-151">向“Photon 用户预制件”字段中分配来自“资源”文件夹的“PhotonUser”预制件</span><span class="sxs-lookup"><span data-stu-id="6384d-151">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="6384d-153">尝试包含多个用户的体验</span><span class="sxs-lookup"><span data-stu-id="6384d-153">Trying the experience with multiple users</span></span>

<span data-ttu-id="6384d-154">如果现在生成 Unity 项目并将其部署到 HoloLens，然后回到 Unity，并在应用运行于 HoloLens 上时进入“游戏”模式，那么当你来回晃动头部 (HoloLens) 时，你将看到 HoloLens 用户头像移动：</span><span class="sxs-lookup"><span data-stu-id="6384d-154">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="6384d-156">要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="6384d-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="6384d-157">应用需要连接到 Photon，因此请确保计算机/设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="6384d-157">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6384d-158">祝贺</span><span class="sxs-lookup"><span data-stu-id="6384d-158">Congratulations</span></span>

<span data-ttu-id="6384d-159">你已成功将项目配置为允许多个用户连接到相同体验并可看到彼此的移动。</span><span class="sxs-lookup"><span data-stu-id="6384d-159">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="6384d-160">在下一教程中，你将实现功能，以使对象的移动也可以在多个设备之间共享。</span><span class="sxs-lookup"><span data-stu-id="6384d-160">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

[<span data-ttu-id="6384d-161">下一教程：4.与多个用户共享对象移动</span><span class="sxs-lookup"><span data-stu-id="6384d-161">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
