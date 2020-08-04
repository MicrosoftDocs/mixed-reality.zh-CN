---
title: 多用户功能教程 - 4. 与多个用户共享对象运动
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7dbe25cd1b0329e366fcbd567074018025032f9e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376559"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="fc25a-105">4.与多个用户共享对象运动</span><span class="sxs-lookup"><span data-stu-id="fc25a-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="fc25a-106">本教程介绍如何共享对象的运动，使共享体验的所有参与者可以展开协作并查看彼此的交互。</span><span class="sxs-lookup"><span data-stu-id="fc25a-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each other's interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="fc25a-107">目标</span><span class="sxs-lookup"><span data-stu-id="fc25a-107">Objectives</span></span>

* <span data-ttu-id="fc25a-108">配置项目以共享对象的运动</span><span class="sxs-lookup"><span data-stu-id="fc25a-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="fc25a-109">了解如何生成基本的多用户协作应用</span><span class="sxs-lookup"><span data-stu-id="fc25a-109">Learn how to build a basic multi-user collaborative app</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="fc25a-110">准备场景</span><span class="sxs-lookup"><span data-stu-id="fc25a-110">Preparing the scene</span></span>

<span data-ttu-id="fc25a-111">在本部分，你将通过添加教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="fc25a-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="fc25a-112">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “预制件”文件夹，然后将“TableAnchor”预制件拖动到“层次结构”窗口中“SharedPlayground”对象上，以将其作为 SharedPlayground 对象的子项添加到场景    ：</span><span class="sxs-lookup"><span data-stu-id="fc25a-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab onto the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="fc25a-114">配置 PUN 以将对象实例化</span><span class="sxs-lookup"><span data-stu-id="fc25a-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="fc25a-115">在本部分，你将配置项目以使用在[入门教程](mr-learning-base-01.md)中创建的“探测车浏览器”体验，并定义在哪里将其实例化。</span><span class="sxs-lookup"><span data-stu-id="fc25a-115">In this section, you will configure the project to use the Rover Explorer experience created during the [Getting started tutorials](mr-learning-base-01.md) and define where it will be instantiated.</span></span>

<span data-ttu-id="fc25a-116">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。  </span><span class="sxs-lookup"><span data-stu-id="fc25a-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="fc25a-117">在“层次结构”窗口中，展开“NetworkLobby”对象并选择“NetworkRoom”子对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="fc25a-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="fc25a-118">向“探测车浏览器预制件”字段分配来自“资源”文件夹的“RoverExplorer_Complete_Variant”预制件 </span><span class="sxs-lookup"><span data-stu-id="fc25a-118">To the **Rover Explorer Prefab** field, assign the **RoverExplorer_Complete_Variant** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

<span data-ttu-id="fc25a-120">在“NetworkRoom”子对象仍处于选中状态的情况下，在“层次结构”窗口中展开“TableAnchor”对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：  </span><span class="sxs-lookup"><span data-stu-id="fc25a-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="fc25a-121">向“探测车浏览器位置”字段中分配来自“层次结构”窗口的“TableAnchor”>“Table”子对象 </span><span class="sxs-lookup"><span data-stu-id="fc25a-121">To the **Rover Explorer Location** field, assign the TableAnchor > **Table** child object from the Hierarchy window</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="fc25a-123">尝试带有共享对象移动的体验</span><span class="sxs-lookup"><span data-stu-id="fc25a-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="fc25a-124">如果现在生成了 Unity 项目并将其部署到 HoloLens，然后返回到 Unity，并且在应用运行于 HoloLens 上时按“玩游戏”按钮以进入“游戏”模式，那么，当你在 HoloLens 中移动对象时，你将看到对象在 Unity 中移动：</span><span class="sxs-lookup"><span data-stu-id="fc25a-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the app is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="fc25a-126">祝贺</span><span class="sxs-lookup"><span data-stu-id="fc25a-126">Congratulations</span></span>

<span data-ttu-id="fc25a-127">你已成功将项目配置为同步对象移动，因此用户可以在其他用户移动对象时看到对象移动。</span><span class="sxs-lookup"><span data-stu-id="fc25a-127">You have successfully configured your project to synchronize object movements so users can see the objects move when other users move them.</span></span> <span data-ttu-id="fc25a-128">在下一教程中，你将实现协调物理世界体验的功能。</span><span class="sxs-lookup"><span data-stu-id="fc25a-128">In the next tutorial, you will implement functionality to align the experience in the physical world.</span></span> <span data-ttu-id="fc25a-129">这将确保用户可以看到各自的实际物理位置，让对象在所有用户看来都处于同一物理位置并同步旋转。</span><span class="sxs-lookup"><span data-stu-id="fc25a-129">This will ensure the users see each other in their actual physical location, and so the objects appear in the same physical position and rotation for all users.</span></span>

[<span data-ttu-id="fc25a-130">下一教程：5.将 Azure 空间定位点集成到共享体验中</span><span class="sxs-lookup"><span data-stu-id="fc25a-130">Next Tutorial: 5. Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)
