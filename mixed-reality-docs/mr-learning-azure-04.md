---
title: Azure 云教程 - 4. 集成 Azure 空间定位点
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, hololens 2, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: 4eac2b96519abeebc277a53ad83d1b6dec8d61fd
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304163"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="6502e-105">4.集成 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="6502e-105">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="6502e-106">在本教程中，你将了解如何使用 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="6502e-106">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="6502e-107">并将跟踪对象的位置存储为 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="6502e-107">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="6502e-108">然后，你将查询并向用户显示指向该位置的引导箭头。</span><span class="sxs-lookup"><span data-stu-id="6502e-108">Then you will query and present the user with a guiding arrow pointing to the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="6502e-109">目标</span><span class="sxs-lookup"><span data-stu-id="6502e-109">Objectives</span></span>

* <span data-ttu-id="6502e-110">了解 Azure 空间定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="6502e-110">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="6502e-111">了解如何将场景设置为使用此项目中的 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="6502e-111">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="6502e-112">了解如何集成存储和查询位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-112">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="6502e-113">了解 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="6502e-113">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="6502e-114">Azure 空间定位点是 Azure 云服务系列的一部分，用于保存定位点位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-114">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="6502e-115">可根据定位点 ID 从云中检索保存的定位点位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-115">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="6502e-116">多种平台的设备（如 HoloLens、iOS 和 Android 设备）均可共享和访问此定位点位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-116">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="6502e-117">详细了解 [Azure 空间定位点](https://docs.microsoft.com/azure/spatial-anchors/overview)。</span><span class="sxs-lookup"><span data-stu-id="6502e-117">Learn more about [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="6502e-118">准备 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="6502e-118">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="6502e-119">在开始之前，需要在 Azure 门户中创建一个空间定位点资源。</span><span class="sxs-lookup"><span data-stu-id="6502e-119">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="6502e-120">了解如何创建[空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)。</span><span class="sxs-lookup"><span data-stu-id="6502e-120">Learn how to make a [spatial anchor resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="6502e-121">准备场景</span><span class="sxs-lookup"><span data-stu-id="6502e-121">Preparing the scene</span></span>

<span data-ttu-id="6502e-122">本部分介绍如何配置场景并进行必要的更改。</span><span class="sxs-lookup"><span data-stu-id="6502e-122">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="6502e-123">在“项目”窗口中，依次导航至“资产”>“MRTK.Tutorials.AzureCloudServices”>“预制件”>“管理器”</span><span class="sxs-lookup"><span data-stu-id="6502e-123">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="6502e-125">在“管理器”文件夹中，将预制件“定位点管理器”拖放到场景层次结构中 。</span><span class="sxs-lookup"><span data-stu-id="6502e-125">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="6502e-126">在层次结构中选择“空间定位点管理器”GameObject，然后在“检查器”部分找到“空间定位点管理器”（脚本） 。</span><span class="sxs-lookup"><span data-stu-id="6502e-126">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="6502e-127">查找“帐户 ID”和“密钥”字段，并添加在前一阶段的先决条件部分创建的凭据。</span><span class="sxs-lookup"><span data-stu-id="6502e-127">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="6502e-129">现在，在场景层次结构中找到 Scene Controller 对象并选择它。</span><span class="sxs-lookup"><span data-stu-id="6502e-129">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="6502e-130">此时将显示“场景控制器”检查器。</span><span class="sxs-lookup"><span data-stu-id="6502e-130">You will see the **Scene Controller** Inspector.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="6502e-132">你将注意到“场景控制器”组件的“定位点管理器”字段为空，此时将“定位点管理器”从场景的层次结构拖放到该字段中，并保存场景  。</span><span class="sxs-lookup"><span data-stu-id="6502e-132">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="6502e-133">生成应用并将其部署到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6502e-133">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="6502e-134">Azure 空间定位点不能在 Unity 中运行，因此，若要测试 Azure 空间定位点功能，需将项目部署到设备。</span><span class="sxs-lookup"><span data-stu-id="6502e-134">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="6502e-135">有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[在设备上生成应用程序](mr-learning-base-ch1.md#build-your-application-to-your-device)中的说明。</span><span class="sxs-lookup"><span data-stu-id="6502e-135">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mr-learning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="6502e-136">在 HoloLens 2 上运行该应用，并按照应用中的说明进行操作</span><span class="sxs-lookup"><span data-stu-id="6502e-136">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="6502e-137">创建一个用于存储位置的定位点</span><span class="sxs-lookup"><span data-stu-id="6502e-137">Create an anchor to store a location</span></span>

<span data-ttu-id="6502e-138">本部分介绍如何保存对象位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-138">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="6502e-139">运行应用程序，然后在主菜单中单击“设置对象”。</span><span class="sxs-lookup"><span data-stu-id="6502e-139">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="6502e-140">提供要保存的对象的名称，然后单击“设置对象”以继续 。</span><span class="sxs-lookup"><span data-stu-id="6502e-140">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="6502e-141">若要添加有关对象的详细信息，请选择“图像”，并描述此对象。</span><span class="sxs-lookup"><span data-stu-id="6502e-141">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="6502e-142">若要保存位置，请单击“保存位置”</span><span class="sxs-lookup"><span data-stu-id="6502e-142">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="6502e-143">你将看到一个定位点指针，可以移动它并将其放置到要保存的位置上。</span><span class="sxs-lookup"><span data-stu-id="6502e-143">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="6502e-144">之后，你将看到一个“确认”弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="6502e-144">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="6502e-145">如果要确认并保存位置，请单击“是”；否则，可以通过单击“否”并再次选择位置来更改位置 。</span><span class="sxs-lookup"><span data-stu-id="6502e-145">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="6502e-146">单击“是”确认位置后，该位置和定位点 ID 将保存到 Azure 云存储中。</span><span class="sxs-lookup"><span data-stu-id="6502e-146">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="6502e-147">保存后，定位点中会显示对象标记以及该对象的名称。</span><span class="sxs-lookup"><span data-stu-id="6502e-147">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="6502e-148">现在已成功保存对象位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-148">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="6502e-149">用于查找定位点位置的查询</span><span class="sxs-lookup"><span data-stu-id="6502e-149">Query for finding an anchor location</span></span>

<span data-ttu-id="6502e-150">成功保存定位点位置后，即可通过在主菜单中选择“搜索对象”来找到定位点位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-150">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="6502e-151">单击“搜索对象”后，将弹出一个新窗口，需要在该窗口中指定要搜索的对象的名称。</span><span class="sxs-lookup"><span data-stu-id="6502e-151">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="6502e-152">输入对象的名称，然后单击“搜索对象”。</span><span class="sxs-lookup"><span data-stu-id="6502e-152">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="6502e-153">如果以前保存了该对象，并且可在数据库中找到该对象，你会得到对象卡，其中包含之前保存的对象的所有详细信息。</span><span class="sxs-lookup"><span data-stu-id="6502e-153">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="6502e-154">现在可通过单击“显示位置”来查找对象。</span><span class="sxs-lookup"><span data-stu-id="6502e-154">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="6502e-155">单击“显示位置”后，系统将从云存储中查询对象地址。</span><span class="sxs-lookup"><span data-stu-id="6502e-155">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="6502e-156">成功检索位置后，将出现一个箭头，引导你找到对象位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-156">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="6502e-157">按照箭头标记操作，直到找到对象的位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-157">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="6502e-158">找到对象后，对象名称将显示在顶部，箭头标记将消失，现在可以单击“对象标记”，查看对象的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6502e-158">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6502e-159">祝贺</span><span class="sxs-lookup"><span data-stu-id="6502e-159">Congratulations</span></span>

<span data-ttu-id="6502e-160">在本教程中，你了解了 Azure 空间定位点如何在 Hololense 2 上保存和检索对象位置。</span><span class="sxs-lookup"><span data-stu-id="6502e-160">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="6502e-161">最后一个教程将介绍如何使用 Azure 机器人服务为我们的应用程序添加自然语言作为新的交互方法。</span><span class="sxs-lookup"><span data-stu-id="6502e-161">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

[<span data-ttu-id="6502e-162">下一教程：5.将 Azure 机器人服务与 LUIS 集成</span><span class="sxs-lookup"><span data-stu-id="6502e-162">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
