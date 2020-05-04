---
title: 多用户功能教程 - 4. 与多个用户共享对象运动
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610635"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="1c45d-105">3.与多个用户共享对象运动</span><span class="sxs-lookup"><span data-stu-id="1c45d-105">3. Sharing object movements with multiple users</span></span>

<span data-ttu-id="1c45d-106">本教程介绍如何共享对象的运动，使共享体验的所有参与者可以展开协作并查看彼此的交互。</span><span class="sxs-lookup"><span data-stu-id="1c45d-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each others' interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="1c45d-107">目标</span><span class="sxs-lookup"><span data-stu-id="1c45d-107">Objectives</span></span>

* <span data-ttu-id="1c45d-108">配置项目以共享对象的运动</span><span class="sxs-lookup"><span data-stu-id="1c45d-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="1c45d-109">了解如何生成基本的多用户协作应用程序</span><span class="sxs-lookup"><span data-stu-id="1c45d-109">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="1c45d-110">准备场景</span><span class="sxs-lookup"><span data-stu-id="1c45d-110">Preparing the scene</span></span>

<span data-ttu-id="1c45d-111">在本部分，你将通过添加教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="1c45d-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="1c45d-112">在“项目”窗口中，导航到“资产”   > “MRTK.Tutorials.MultiUserCapabilities”   > “预制件”  文件夹，然后将“TableAnchor”  预制件拖动到“层次结构”窗口中“SharedPlayground”  对象的顶部，以将其作为 SharedPlayground 对象的子项添加到场景：</span><span class="sxs-lookup"><span data-stu-id="1c45d-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab on top of the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="1c45d-114">配置 PUN 以将对象实例化</span><span class="sxs-lookup"><span data-stu-id="1c45d-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="1c45d-115">在本部分中，你将配置项目以使用在上一部分中创建的 RocketLauncher_Complete_Variant 预制件，并定义要将其实例化的位置。</span><span class="sxs-lookup"><span data-stu-id="1c45d-115">In this section, you will configure the project to use the RocketLauncher_Complete_Variant prefab you created in the previous section and define where it will be instantiated.</span></span>

<span data-ttu-id="1c45d-116">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。   </span><span class="sxs-lookup"><span data-stu-id="1c45d-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="1c45d-117">在“层次结构”窗口中，展开“NetworkLobby”  对象并选择“NetworkRoom”  子对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”  组件，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="1c45d-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="1c45d-118">向“Photon 用户预制件”  字段中分配来自“资源”文件夹的“PhotonUser”  预制件</span><span class="sxs-lookup"><span data-stu-id="1c45d-118">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

<span data-ttu-id="1c45d-120">在“NetworkRoom”子对象仍处于选中状态的情况下，在“层次结构”窗口中展开“TableAnchor”对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：   </span><span class="sxs-lookup"><span data-stu-id="1c45d-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="1c45d-121">向“火箭发射器位置”  字段中分配来自“层次结构”窗口的“Table”  子对象</span><span class="sxs-lookup"><span data-stu-id="1c45d-121">To the **Rocket Launcher Location** field, assign the **Table** child object from the Hierarchy window</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="1c45d-123">尝试带有共享对象移动的体验</span><span class="sxs-lookup"><span data-stu-id="1c45d-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="1c45d-124">如果现在生成了 Unity 项目并将其部署到 HoloLens，然后返回到 Unity，并且在应用程序运行于 HoloLens 上时按“玩游戏”按钮以进入“游戏”模式，那么，当你在 HoloLens 中移动对象时，你将看到对象在 Unity 中移动：</span><span class="sxs-lookup"><span data-stu-id="1c45d-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="1c45d-126">祝贺</span><span class="sxs-lookup"><span data-stu-id="1c45d-126">Congratulations</span></span>

<span data-ttu-id="1c45d-127">你已成功配置了项目，因此对象移动已同步，用户可以在其他用户移动对象时看到对象移动。</span><span class="sxs-lookup"><span data-stu-id="1c45d-127">You have successfully configured your project so object movements are synchronized and users can see the objects move when other users move the objects.</span></span> <span data-ttu-id="1c45d-128">在下一教程中，你将实现功能，以使共享体验与物理环境相符，使用户在其实际的物理位置中看到彼此，并使对象对所有用户而言都出现在相同的物理位置和旋转角度。</span><span class="sxs-lookup"><span data-stu-id="1c45d-128">In the next tutorial, you will implement functionality so the shared experience is aligned in the physical world and the users see each other in their actual physical location and so the objects appear in the same physical position and rotation for all users.</span></span>

<span data-ttu-id="1c45d-129">[下一教程：4.将 Azure 空间定位点集成到共享体验中](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="1c45d-129">[Next tutorial: 4. Integrating Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch4.md)</span></span>
