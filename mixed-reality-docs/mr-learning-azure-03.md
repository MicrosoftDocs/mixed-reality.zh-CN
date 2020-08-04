---
title: Azure 云教程 - 3. 集成 Azure 自定义视觉
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现 Azure 自定义视觉。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, 实用工具, 教程, hololens, hololens 2, azure 自定义视觉, azure 认知服务
ms.localizationpriority: high
ms.openlocfilehash: 0fc3793315dd05f91a6193b68343205f53a3092a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376459"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="503c8-105">3.集成 Azure 自定义视觉</span><span class="sxs-lookup"><span data-stu-id="503c8-105">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="503c8-106">在本教程中，你将了解如何使用 Azure 自定义视觉。你将上传一组照片，将其与被跟踪对象关联，然后再上传到“自定义视觉”服务并开始训练过程。</span><span class="sxs-lookup"><span data-stu-id="503c8-106">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="503c8-107">然后，通过从网络摄像头源捕获照片，使用该服务来检测被跟踪对象。</span><span class="sxs-lookup"><span data-stu-id="503c8-107">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="503c8-108">目标</span><span class="sxs-lookup"><span data-stu-id="503c8-108">Objectives</span></span>

* <span data-ttu-id="503c8-109">了解有关 Azure 自定义视觉的基础知识</span><span class="sxs-lookup"><span data-stu-id="503c8-109">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="503c8-110">了解如何设置场景以在此项目中使用自定义视觉</span><span class="sxs-lookup"><span data-stu-id="503c8-110">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="503c8-111">了解如何集成上传、训练和检测图像</span><span class="sxs-lookup"><span data-stu-id="503c8-111">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="503c8-112">了解 Azure 自定义视觉</span><span class="sxs-lookup"><span data-stu-id="503c8-112">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="503c8-113">Azure 自定义视觉属于认知服务系列，可用于训练图像分类器 。</span><span class="sxs-lookup"><span data-stu-id="503c8-113">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="503c8-114">图像分类器是一种 AI 服务，它使用经过训练的模型来应用匹配标记。</span><span class="sxs-lookup"><span data-stu-id="503c8-114">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="503c8-115">应用程序将使用此分类功能来检测被跟踪对象。</span><span class="sxs-lookup"><span data-stu-id="503c8-115">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="503c8-116">详细了解 [Azure 自定义视觉](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。</span><span class="sxs-lookup"><span data-stu-id="503c8-116">Learn more about [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="503c8-117">为 Azure 自定义视觉做好准备</span><span class="sxs-lookup"><span data-stu-id="503c8-117">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="503c8-118">在开始之前，请创建一个自定义视觉项目，最快的方法是使用 Web 门户。</span><span class="sxs-lookup"><span data-stu-id="503c8-118">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="503c8-119">按照以下[快速入门教程](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images)中“上传和标记图像”之前的部分设置你的帐户和项目。</span><span class="sxs-lookup"><span data-stu-id="503c8-119">Follow this [quickstart tutorial](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="503c8-120">若要训练模型，至少需要 2 个标记，每个标记 5 张图像。</span><span class="sxs-lookup"><span data-stu-id="503c8-120">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="503c8-121">若要使用此应用程序，至少应创建一个涵盖 5 张图片的标记，这样之后的训练过程才不会失败。</span><span class="sxs-lookup"><span data-stu-id="503c8-121">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="503c8-122">准备场景</span><span class="sxs-lookup"><span data-stu-id="503c8-122">Preparing the scene</span></span>

<span data-ttu-id="503c8-123">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureCloudServices” > “预制件” > “管理器”文件夹   。</span><span class="sxs-lookup"><span data-stu-id="503c8-123">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="503c8-125">从此处将预制件 ObjectDetectionManager 拖到场景层次结构中。</span><span class="sxs-lookup"><span data-stu-id="503c8-125">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="503c8-127">在“层次结构”窗口中，找到并选中 ObjectDetectionManager 对象。</span><span class="sxs-lookup"><span data-stu-id="503c8-127">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="503c8-128">ObjectDetectionManager 预制件包含“ObjectDetectionManager(脚本)”组件，你可从“检查器”窗口中看到，它取决于多项设置 。</span><span class="sxs-lookup"><span data-stu-id="503c8-128">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on several settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="503c8-129">检索 Azure API 资源凭据</span><span class="sxs-lookup"><span data-stu-id="503c8-129">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="503c8-130">可从 Azure 门户和自定义视觉门户检索“ObjectDetectionManager(脚本)”设置所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="503c8-130">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="azure-portal"></a><span data-ttu-id="503c8-131">Azure 门户</span><span class="sxs-lookup"><span data-stu-id="503c8-131">Azure Portal</span></span>

<span data-ttu-id="503c8-132">查找并找到你在本教程的“准备场景”部分中创建的“认知服务”类型的自定义视觉资源。</span><span class="sxs-lookup"><span data-stu-id="503c8-132">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial.</span></span> <span data-ttu-id="503c8-133">然后，单击“密钥和终结点”，以检索所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="503c8-133">There click on *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="custom-vision-dashboard"></a><span data-ttu-id="503c8-134">自定义视觉仪表板</span><span class="sxs-lookup"><span data-stu-id="503c8-134">Custom Vision Dashboard</span></span>

<span data-ttu-id="503c8-135">在[自定义视觉](https://www.customvision.ai/projects)仪表板中，打开已为本教程创建的项目，并单击页面右上角的齿轮图标以打开“设置”页。</span><span class="sxs-lookup"><span data-stu-id="503c8-135">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="503c8-136">此时，你可在“资源”部分中找到所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="503c8-136">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="503c8-137">现在，通过“ObjectDetectionManager(脚本)”安装程序，找到并选中场景层次结构中的 SceneController 对象 。</span><span class="sxs-lookup"><span data-stu-id="503c8-137">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="503c8-139">你将看到 SceneController 组件中“对象检测管理器”字段为空，将 ObjectDetectionManager 从层次结构拖到该字段中并保存场景 。</span><span class="sxs-lookup"><span data-stu-id="503c8-139">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="503c8-141">拍摄和上传图像</span><span class="sxs-lookup"><span data-stu-id="503c8-141">Take and upload images</span></span>

<span data-ttu-id="503c8-142">运行场景并单击“设置对象”，键入在[上一课](mr-learning-azure-02.md)中创建的某一被跟踪对象的名称 。</span><span class="sxs-lookup"><span data-stu-id="503c8-142">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="503c8-143">现在，单击“计算机视觉”按钮，你可在“对象卡片”底部找到 。</span><span class="sxs-lookup"><span data-stu-id="503c8-143">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="503c8-144">此时将打开一个新窗口，请务必使用六张照片训练模型以进行图像识别。</span><span class="sxs-lookup"><span data-stu-id="503c8-144">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="503c8-145">如果想查找要跟踪的对象，请单击“相机”按钮并执行 AirTap，执行该操作六次。</span><span class="sxs-lookup"><span data-stu-id="503c8-145">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="503c8-146">若要改进模型训练，请尝试从不同角度和照明条件下拍摄每张图像。</span><span class="sxs-lookup"><span data-stu-id="503c8-146">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="503c8-147">获得足够的图像后，单击“训练”按钮，开始云中的模型训练过程。</span><span class="sxs-lookup"><span data-stu-id="503c8-147">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="503c8-148">启动训练后，系统将上传所有图像，然后开始训练，这一过程可能需要一分钟或更长时间。</span><span class="sxs-lookup"><span data-stu-id="503c8-148">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="503c8-149">菜单中一条消息会指示当前进度，一旦消息指示完成，你便可以停止应用程序</span><span class="sxs-lookup"><span data-stu-id="503c8-149">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="503c8-150">“ObjectDetectionManager(脚本)”会直接将拍摄的图像上传到自定义视觉服务。</span><span class="sxs-lookup"><span data-stu-id="503c8-150">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="503c8-151">作为一种替代方法，自定义视觉 API 接受图像 URL，你可以练习修改“ObjectDetectionManager(script)”，将图像上传到 Blob 存储。</span><span class="sxs-lookup"><span data-stu-id="503c8-151">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="503c8-152">检测对象</span><span class="sxs-lookup"><span data-stu-id="503c8-152">Detect objects</span></span>

<span data-ttu-id="503c8-153">现在，你可以测试训练后的模型，运行应用程序并从主菜单中单击“搜索对象”，然后键入相关的被跟踪对象的名称 。</span><span class="sxs-lookup"><span data-stu-id="503c8-153">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="503c8-154">随即将显示“对象卡片”，单击“自定义视觉”按钮 。</span><span class="sxs-lookup"><span data-stu-id="503c8-154">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="503c8-155">自此，ObjectDetectionManager 将开始在后台使用相机拍摄图像，菜单上将指示进度。</span><span class="sxs-lookup"><span data-stu-id="503c8-155">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="503c8-156">将相机指向你用于训练模型的对象，你将看到相机在一小段时间后会检测到对象。</span><span class="sxs-lookup"><span data-stu-id="503c8-156">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="503c8-157">祝贺</span><span class="sxs-lookup"><span data-stu-id="503c8-157">Congratulations</span></span>

<span data-ttu-id="503c8-158">在本教程中，你学习了如何使用 Azure 自定义视觉来训练图像，并使用分类服务来检测与关联的被跟踪对象匹配的图像。</span><span class="sxs-lookup"><span data-stu-id="503c8-158">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="503c8-159">在下一教程中，你将学习如何使用 Azure 空间定位点将被跟踪对象与物理世界中的某个位置关联在一起，以及如何显示一个将引导用户返回到被跟踪对象的关联位置的箭头。</span><span class="sxs-lookup"><span data-stu-id="503c8-159">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

[<span data-ttu-id="503c8-160">下一教程：4.集成 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="503c8-160">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)
