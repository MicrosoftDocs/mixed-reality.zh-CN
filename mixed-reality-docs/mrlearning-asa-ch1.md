---
title: MR 学习 ASA 模块 Azure HoloLens 2 上的空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326443"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a><span data-ttu-id="42fc6-104">开始使用 HoloLens 2 上的 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="42fc6-104">Getting Started with Azure Spatial Anchors on HoloLens 2</span></span>

<span data-ttu-id="42fc6-105">欢迎使用 HoloLens 2 教程的第二个模块 ！</span><span class="sxs-lookup"><span data-stu-id="42fc6-105">Welcome to the second module of the HoloLens 2 Tutorial!</span></span> <span data-ttu-id="42fc6-106">开始之前，请确保所有的[先决条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)都已完成。</span><span class="sxs-lookup"><span data-stu-id="42fc6-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="42fc6-107">如果您尚未完成第一种[的基本模块](mrlearning-base.md)，我们强烈建议您完成该第一个。</span><span class="sxs-lookup"><span data-stu-id="42fc6-107">If you have not completed the first, [base module](mrlearning-base.md) yet, we highly recommend that you complete that first.</span></span> <span data-ttu-id="42fc6-108">如果要从新的 unity 项目开始，按照中的新项目创建步骤[的基本模块](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="42fc6-108">If you are starting from a new unity project, follow the new project creation steps in the [base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="42fc6-109">目标</span><span class="sxs-lookup"><span data-stu-id="42fc6-109">Objectives</span></span>

* <span data-ttu-id="42fc6-110">了解使用 Azure HoloLens 2 的空间定位点进行开发基础的知识</span><span class="sxs-lookup"><span data-stu-id="42fc6-110">Learn the fundamentals of developing with Azure Spatial Anchors with the HoloLens 2</span></span>

* <span data-ttu-id="42fc6-111">创建、 上传和下载空间的定位点</span><span class="sxs-lookup"><span data-stu-id="42fc6-111">Create, Upload, and Download Spatial Anchors</span></span>

  

## <a name="instructions"></a><span data-ttu-id="42fc6-112">说明</span><span class="sxs-lookup"><span data-stu-id="42fc6-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="42fc6-113">下载和导入资产</span><span class="sxs-lookup"><span data-stu-id="42fc6-113">Downloading and Importing Assets</span></span>
<span data-ttu-id="42fc6-114">在开始之前，必须下载并导入以下资产：</span><span class="sxs-lookup"><span data-stu-id="42fc6-114">Before beginning, you must download and import the following assets:</span></span>

[<span data-ttu-id="42fc6-115">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="42fc6-115">Azure Spatial Anchors</span></span>](https://github.com/azure/azure-spatial-anchors-samples/releases)

[<span data-ttu-id="42fc6-116">MR 基本模块资产包</span><span class="sxs-lookup"><span data-stu-id="42fc6-116">MR Base module Asset Pack</span></span>](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[<span data-ttu-id="42fc6-117">ASA 模块资产包</span><span class="sxs-lookup"><span data-stu-id="42fc6-117">ASA module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[<span data-ttu-id="42fc6-118">混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="42fc6-118">Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> <span data-ttu-id="42fc6-119">注意： 有关如何导入 Azure 空间的定位点、 第 6 步有关具体说明 MR 基本模块资产包和步骤 3-4，有关具体说明混合现实工具包，请参阅有关具体说明的步骤 5。</span><span class="sxs-lookup"><span data-stu-id="42fc6-119">Note: see step 5 for specific instructions on how to import the Azure Spatial Anchors, step 6 for specific instructions on the MR Base module Asset Pack, and steps 3-4 for specific instructions on the Mixed Reality Toolkit.</span></span>

1. <span data-ttu-id="42fc6-120">在项目中创建新的场景。</span><span class="sxs-lookup"><span data-stu-id="42fc6-120">create a new scene in your project.</span></span> <span data-ttu-id="42fc6-121">右键单击场景文件夹中，单击"创建"然后场景。</span><span class="sxs-lookup"><span data-stu-id="42fc6-121">Right click your scene folder, click "create," then scene.</span></span> <span data-ttu-id="42fc6-122">命名新的场景"ASALearningmodule。"</span><span class="sxs-lookup"><span data-stu-id="42fc6-122">Name the new scene "ASALearningmodule."</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="42fc6-124">双击"ASALearningmodule"到某些预定义的项显示以及新的场景，请参阅。</span><span class="sxs-lookup"><span data-stu-id="42fc6-124">Double click "ASALearningmodule" to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="42fc6-125">配置用于混合的现实开发场景。</span><span class="sxs-lookup"><span data-stu-id="42fc6-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="42fc6-127">注意：显示弹出窗口，指出，"您必须选择一个文件的混合现实工具包。"</span><span class="sxs-lookup"><span data-stu-id="42fc6-127">Note: You will see a pop-up that says, "you must choose a file for the Mixed Reality Toolkit."</span></span> <span data-ttu-id="42fc6-128">单击"确定"将转到步骤 4。</span><span class="sxs-lookup"><span data-stu-id="42fc6-128">Clicking "ok" will bring you to step 4.</span></span>

4. <span data-ttu-id="42fc6-129">当为混合现实工具包中选择一个文件，选择，"DefaultMixedRealityToolkitConfigurationProfile。"</span><span class="sxs-lookup"><span data-stu-id="42fc6-129">When choosing a file for the Mixed Reality Toolkit, select, "DefaultMixedRealityToolkitConfigurationProfile."</span></span>

   > <span data-ttu-id="42fc6-130">注意：如果你有自己配置配置文件可随时使用该副本。</span><span class="sxs-lookup"><span data-stu-id="42fc6-130">Note: If you have your own configuration profile feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="42fc6-132">现在场景配置为使用混合现实。</span><span class="sxs-lookup"><span data-stu-id="42fc6-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="42fc6-133">请确保保存您的场景 （执行此操作与任一控件 / 命令 + S，或单击文件，然后单击保存）。</span><span class="sxs-lookup"><span data-stu-id="42fc6-133">Make sure you save your scene (do this with either control/command+S, or click on file, then click on save).</span></span> 

5. <span data-ttu-id="42fc6-134">导入[Azure 空间的定位点](https://github.com/azure/azure-spatial-anchors-samples/releases)。</span><span class="sxs-lookup"><span data-stu-id="42fc6-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="42fc6-135">若要使用空间的定位点，必须导入此资产。</span><span class="sxs-lookup"><span data-stu-id="42fc6-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="42fc6-136">因此，请单击上面的链接并右键单击"AzureSpatialAnchors.unitypackage。"</span><span class="sxs-lookup"><span data-stu-id="42fc6-136">So, click on the link above and right click on "AzureSpatialAnchors.unitypackage."</span></span> <span data-ttu-id="42fc6-137">单击"目标另存为"并将其保存到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="42fc6-137">Click on "save target as" and save it to your computer.</span></span> 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   <span data-ttu-id="42fc6-139">然后，保存后，请返回到 unity 中，单击"资产"转到"导入包"，然后单击"自定义包..."将打开你的计算机文件。</span><span class="sxs-lookup"><span data-stu-id="42fc6-139">Then, after it's saved, go back into unity, click "assets," go down to "import package," then click "custom package..." Your computer files will open up.</span></span> <span data-ttu-id="42fc6-140">一次它们执行操作，查找 Azure 空间的定位点包的保存位置并选择它。</span><span class="sxs-lookup"><span data-stu-id="42fc6-140">Once they do, find where you saved the Azure Spatial Anchors package and select it.</span></span> <span data-ttu-id="42fc6-141">然后单击"打开"。</span><span class="sxs-lookup"><span data-stu-id="42fc6-141">Then click "open."</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   <span data-ttu-id="42fc6-143">现在将有一个弹出窗口，为提供的工具和设置，询问您要导入列表。</span><span class="sxs-lookup"><span data-stu-id="42fc6-143">Now there will be a popup giving a list of tools and settings, asking you what to import.</span></span> <span data-ttu-id="42fc6-144">选择***所有***的可用的选项，然后单击"导入"。</span><span class="sxs-lookup"><span data-stu-id="42fc6-144">Select ***all*** of the options available, then click "import."</span></span>

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > <span data-ttu-id="42fc6-146">注意： 它将需要几分钟来导入，因此请耐心等待。</span><span class="sxs-lookup"><span data-stu-id="42fc6-146">note: it will take a few minutes to import, so please be patient.</span></span> 

   6. <span data-ttu-id="42fc6-147">导入[MR 基本模块资产包](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)下一步。</span><span class="sxs-lookup"><span data-stu-id="42fc6-147">Import [MR Base module Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) next.</span></span> <span data-ttu-id="42fc6-148">类似于步骤 5 中，单击上面的链接，然后右键单击"BasemoduleAssetsV1 1.unitypackage"并单击"目标另存为"并将其保存到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="42fc6-148">Much like step 5, click the link above, then right click "BasemoduleAssetsV1 1.unitypackage" and click "save target as" and save it to your computer.</span></span>

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > <span data-ttu-id="42fc6-150">提示：将所有这些资产保存在同一文件夹，以便可以更轻松地查找和有权访问。</span><span class="sxs-lookup"><span data-stu-id="42fc6-150">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="42fc6-151">它将保留所有内容和组织更好 ！</span><span class="sxs-lookup"><span data-stu-id="42fc6-151">It will keep everything nice and organized!</span></span>

   <span data-ttu-id="42fc6-152">就像步骤 5 中，转回到到 unity 中，单击"资产"悬停"导入包"，然后单击"自定义包..."你的计算机文件应会再次出现，因此请转到你在其中存储的基本模块资产包并选择它。</span><span class="sxs-lookup"><span data-stu-id="42fc6-152">Just like step 5, go back in to unity, click "assets," hover over "import package" then click "custom package..." Your computer files should appear again, so go to where you stored the Base module Asset Pack and select it.</span></span> <span data-ttu-id="42fc6-153">然后单击"打开"。</span><span class="sxs-lookup"><span data-stu-id="42fc6-153">Then click "open."</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > <span data-ttu-id="42fc6-155">注意： 可能有更高版本中此模块需要的多个资产。</span><span class="sxs-lookup"><span data-stu-id="42fc6-155">Note: there may be more assets needed later in this module.</span></span> <span data-ttu-id="42fc6-156">按照这些步骤导入所述从该点上的任何资产。</span><span class="sxs-lookup"><span data-stu-id="42fc6-156">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="42fc6-157">导入 ASA 模块使用相同的方法与导入之前的包的包。</span><span class="sxs-lookup"><span data-stu-id="42fc6-157">Import the ASA module Pack using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="42fc6-158">配置您的场景</span><span class="sxs-lookup"><span data-stu-id="42fc6-158">Configuring your scene</span></span>

<span data-ttu-id="42fc6-159">在本部分中，我们将添加预设和脚本向场景来创建一系列演示应用程序中本地定位点和 Azure 空间的定位点的行为方式的基础知识的按钮。</span><span class="sxs-lookup"><span data-stu-id="42fc6-159">In this section, we will be adding prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

7. <span data-ttu-id="42fc6-160">在"项目"选项卡上，下面的"资产"文件夹，单击"ASAmoduleAssets。"</span><span class="sxs-lookup"><span data-stu-id="42fc6-160">In the "project" tab, underneath the "assets" folder, click on "ASAmoduleAssets."</span></span> <span data-ttu-id="42fc6-161">选择后，你将看到 2 个预设，"ButtonParent"和"ParentAnchor。"</span><span class="sxs-lookup"><span data-stu-id="42fc6-161">Once selected you will see 2 prefabs, "ButtonParent" and "ParentAnchor."</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. <span data-ttu-id="42fc6-163">将这两个预设拖到场景。</span><span class="sxs-lookup"><span data-stu-id="42fc6-163">Drag both of the prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. <span data-ttu-id="42fc6-165">双击父定位点，以将其选中。</span><span class="sxs-lookup"><span data-stu-id="42fc6-165">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="42fc6-166">您可能需要调整视图若要查看整个场景，因此，根据需要调整您的场景。</span><span class="sxs-lookup"><span data-stu-id="42fc6-166">You may need to adjust your view to see the entire scene, so adjust your scene as needed.</span></span>

    <span data-ttu-id="42fc6-167">自行熟悉 ParentAnchor 预设。</span><span class="sxs-lookup"><span data-stu-id="42fc6-167">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="42fc6-168">目前，游戏对象名为"ParentAnchor"是彩色多维数据集，用于演示目的。</span><span class="sxs-lookup"><span data-stu-id="42fc6-168">Currently, the game object named "ParentAnchor" is a colored cube, for demonstration purposes.</span></span> <span data-ttu-id="42fc6-169">最终，我们将隐藏该多维数据集，并将它们作为子级 ParentAnchor 放置我们的内容。</span><span class="sxs-lookup"><span data-stu-id="42fc6-169">Eventually, we will hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="42fc6-170">此预设可包括 AzureSpatialAnchorsDemoWrapper.cs 脚本 （包含在 ASA SDK） 和 ParentAnchor 对象 ASAmoduleScript.cs 脚本 （包含作为此模块的一部分）。</span><span class="sxs-lookup"><span data-stu-id="42fc6-170">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK) and the ASAmoduleScript.cs script (included as part of this module) to the ParentAnchor object.</span></span> 

10. <span data-ttu-id="42fc6-171">配置按钮。</span><span class="sxs-lookup"><span data-stu-id="42fc6-171">Configure Buttons.</span></span> <span data-ttu-id="42fc6-172">下 ParentAnchor 预设中，您会注意到多个标记的按钮。</span><span class="sxs-lookup"><span data-stu-id="42fc6-172">Under the ParentAnchor prefab, you will notice several labeled buttons.</span></span> <span data-ttu-id="42fc6-173">从 MRTK PressableButton 预设，则创建这些按钮。</span><span class="sxs-lookup"><span data-stu-id="42fc6-173">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="42fc6-174">了解有关如何创建从 Pressable 按钮的详细信息[的基本模块](mrlearning-base-ch2.md)。</span><span class="sxs-lookup"><span data-stu-id="42fc6-174">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="42fc6-175">每个按钮，将添加在用户按下或选择根据下面的列表按钮时，将触发的事件。</span><span class="sxs-lookup"><span data-stu-id="42fc6-175">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="42fc6-176">对于名为"StartAzureSession"按钮，创建新的事件下的"按钮按下"事件触发器，以及"单击"事件触发器。</span><span class="sxs-lookup"><span data-stu-id="42fc6-176">For the Button named "StartAzureSession", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="42fc6-177">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 StartAzureSession() 方法。</span><span class="sxs-lookup"><span data-stu-id="42fc6-177">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="42fc6-181">对于名为"StopAzureSession"按钮，创建新的事件下的"按钮按下"事件触发器，以及"单击"事件触发器。</span><span class="sxs-lookup"><span data-stu-id="42fc6-181">For the Button named "StopAzureSession", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="42fc6-182">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 StopAzureSession() 方法。</span><span class="sxs-lookup"><span data-stu-id="42fc6-182">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="42fc6-183">对于名为"CreateAnchor"按钮，创建新的事件下的"按钮按下"事件触发器，以及"单击"事件触发器。</span><span class="sxs-lookup"><span data-stu-id="42fc6-183">For the Button named "CreateAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="42fc6-184">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 CreateAzureAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="42fc6-184">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="42fc6-185">对于名为"开始查找的定位点"按钮，创建新的事件下的"按钮按下"事件触发器，以及"单击"事件触发器。</span><span class="sxs-lookup"><span data-stu-id="42fc6-185">For the Button named "Start Looking For Anchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="42fc6-186">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 FindAzureAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="42fc6-186">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="42fc6-187">对于名为"DeleteAzureAnchor"按钮，创建新的事件下的"按钮按下"事件触发器，以及"单击"事件触发器。</span><span class="sxs-lookup"><span data-stu-id="42fc6-187">For the Button named "DeleteAzureAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="42fc6-188">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 DeleteAzureAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="42fc6-188">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="42fc6-189">对于名为"删除本地定位点"按钮，创建新的事件下的"按钮按下"事件触发器，以及"单击"事件触发器。</span><span class="sxs-lookup"><span data-stu-id="42fc6-189">For the Button named "Delete Local Anchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="42fc6-190">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 RemoveLocalAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="42fc6-190">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="42fc6-191">生成并演示基本应用程序</span><span class="sxs-lookup"><span data-stu-id="42fc6-191">Build and Demonstrate Base Application</span></span>

<span data-ttu-id="42fc6-192">现在，您的场景配置来演示 Azure 空间的定位点的基础知识，我们将生成并演示 Azure 空间的定位点的基本行为。</span><span class="sxs-lookup"><span data-stu-id="42fc6-192">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="42fc6-193">如果在前面的部分关闭了“生成设置”窗口，请转到“文件”>“生成设置”，再次打开生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="42fc6-193">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="42fc6-194">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="42fc6-194">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="42fc6-195">通过单击“添加打开的场景”按钮，确保要尝试的场景位于“生成中的场景”列表中。</span><span class="sxs-lookup"><span data-stu-id="42fc6-195">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="42fc6-196">按“生成”按钮开始生成过程。</span><span class="sxs-lookup"><span data-stu-id="42fc6-196">Press the Build button to begin the build process.</span></span>
    <span data-ttu-id="42fc6-197">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="42fc6-197">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="42fc6-198">为应用程序创建一个新文件夹并为其命名。</span><span class="sxs-lookup"><span data-stu-id="42fc6-198">Create and name a new folder for your application.</span></span> <span data-ttu-id="42fc6-199">在下图中，创建了一个名为“应用”的文件夹以包含该应用程序。</span><span class="sxs-lookup"><span data-stu-id="42fc6-199">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="42fc6-200">单击“选择文件夹”，开始生成新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="42fc6-200">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="42fc6-201">生成完成后，可以关闭 Unity 中的“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="42fc6-201">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 
    <span data-ttu-id="42fc6-202">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="42fc6-202">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="42fc6-203">注意：如果生成失败，尝试再次生成或重启 Unity 并再次生成。</span><span class="sxs-lookup"><span data-stu-id="42fc6-203">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="42fc6-204">如果看到错误，如“错误：CS0246 = 找不到"XX"键入或命名空间名称 (是否缺少 using 指令或程序集引用？)"，则需要安装[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="42fc6-204">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="42fc6-205">生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="42fc6-205">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="42fc6-206">双击“MixedRealityBase.sln”解决方案（或相应的名称，如果你使用项目的替代名称）在 Visual Studio 中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="42fc6-206">Double click on the “MixedRealityBase.sln” solution (or the corresponding name, if you used an alternative name for your project) to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="42fc6-207">注意：请务必打开新创建的文件夹（即“应用”文件夹，如果遵循前面步骤中的命名约定），因为在该文件夹之外会有一个类似名称的 .sln 文件，不能将其与“生成”文件夹内的 .sln 文件混淆。</span><span class="sxs-lookup"><span data-stu-id="42fc6-207">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > <span data-ttu-id="42fc6-209">注意：如果 visual studio 会要求安装新组件，请花点时间以确保安装所有必备组件中的具体["安装工具"页](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="42fc6-209">Note: If visual studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="42fc6-210">使用 USB 电缆将 HoloLens 2 插入电脑。</span><span class="sxs-lookup"><span data-stu-id="42fc6-210">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="42fc6-211">虽然这些课程说明假设将部署使用 HoloLens 2 设备进行测试，但是您还可选择将部署到[HoloLens 2 模拟器](using-the-hololens-emulator.md)或选择创建[的旁加载应用包](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="42fc6-211">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="42fc6-212">在生成到设备之前，请确保设备处于开发者模式。</span><span class="sxs-lookup"><span data-stu-id="42fc6-212">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="42fc6-213">如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。</span><span class="sxs-lookup"><span data-stu-id="42fc6-213">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="42fc6-214">如果需要启用开发者模式或与 Visual Studio 配对，请按照[这些说明](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)进行操作。</span><span class="sxs-lookup"><span data-stu-id="42fc6-214">Please follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="42fc6-215">通过选择“发布”配置和“ARM”体系结构，配置 Visual Studio 以生成到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="42fc6-215">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>
    <span data-ttu-id="42fc6-216">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="42fc6-216">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
    
9. <span data-ttu-id="42fc6-217">最后一步是向你的设备通过选择生成调试 > 启动但不调试。</span><span class="sxs-lookup"><span data-stu-id="42fc6-217">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="42fc6-218">选择“在不调试的情况下启动”将导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中显示调试信息。</span><span class="sxs-lookup"><span data-stu-id="42fc6-218">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="42fc6-219">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="42fc6-219">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="42fc6-220">也可以选择“生成”>“部署解决方案”以部署到你的设备，而无需自动启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="42fc6-220">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
    <span data-ttu-id="42fc6-221">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="42fc6-221">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
    
10. <span data-ttu-id="42fc6-222">当在设备上运行应用程序时，请按照屏幕上的说明。</span><span class="sxs-lookup"><span data-stu-id="42fc6-222">When the application is running on your device, please follow the on-screen instructions.</span></span> <span data-ttu-id="42fc6-223">请按场景按钮对应于下面的步骤。</span><span class="sxs-lookup"><span data-stu-id="42fc6-223">Please press the scene buttons corresponding to the Steps below.</span></span>
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="42fc6-225">启动 Azure 空间的定位点会话。</span><span class="sxs-lookup"><span data-stu-id="42fc6-225">Start the Azure spatial anchors session.</span></span>
    
    2. <span data-ttu-id="42fc6-226">将多维数据集移到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="42fc6-226">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="42fc6-227">保存该多维数据集的位置的 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="42fc6-227">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="42fc6-228">停止 Azure 空间的定位点会话。</span><span class="sxs-lookup"><span data-stu-id="42fc6-228">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="42fc6-229">删除多维数据集以允许用户移动该多维数据集上的本地定位点。</span><span class="sxs-lookup"><span data-stu-id="42fc6-229">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    6. <span data-ttu-id="42fc6-230">将移动到其他位置的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="42fc6-230">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="42fc6-231">启动 Azure 空间的定位点会话。</span><span class="sxs-lookup"><span data-stu-id="42fc6-231">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="42fc6-232">查找 Azure 空间的定位点。</span><span class="sxs-lookup"><span data-stu-id="42fc6-232">Find Azure spatial anchors.</span></span>
    <span data-ttu-id="42fc6-233">（多维数据集应返回到原始位置现在您将其置于您在创建定位点时）。</span><span class="sxs-lookup"><span data-stu-id="42fc6-233">(now cube should go back to the original place you put it when you created the anchor).</span></span>
    9. <span data-ttu-id="42fc6-234">删除 Azure 空间的定位点。</span><span class="sxs-lookup"><span data-stu-id="42fc6-234">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="42fc6-235">停止 Azure 的会话。</span><span class="sxs-lookup"><span data-stu-id="42fc6-235">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="42fc6-236">锚定的体验</span><span class="sxs-lookup"><span data-stu-id="42fc6-236">Anchoring an experience</span></span>

<span data-ttu-id="42fc6-237">在前面部分中，您学习了 Azure 空间的定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="42fc6-237">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="42fc6-238">我们使用多维数据集来表示和可视化父级游戏对象使用附加的定位点。</span><span class="sxs-lookup"><span data-stu-id="42fc6-238">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="42fc6-239">在本部分中，您 wiill 了解如何通过将其放置 ParentAnchor 对象的子级作为定位整个体验。</span><span class="sxs-lookup"><span data-stu-id="42fc6-239">In this section, you wiill learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="42fc6-240">对于此示例中，我们将农历模块程序集演示应用程序的过程中创建[第 6 课中的基本模块](mrlearning-base-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="42fc6-240">For this example, we will use the Lunar module Assembly demo app that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="42fc6-241">搜索农历模块程序集完整预设并将其拖动到你的层次结构作为子 AnchorParent gameobject，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="42fc6-241">Search for the Lunar module Assembly Complete prefab and drag it into your heirarchy as a child of the AnchorParent gameobject, as shown in the image below.</span></span>

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="42fc6-243">下图中所示的方式，仍会公开多维数据集，定位模块程序集体验。</span><span class="sxs-lookup"><span data-stu-id="42fc6-243">Position the module assembly experience in such a way that the cube is still exposed, as shown in the image below.</span></span> <span data-ttu-id="42fc6-244">在应用程序中，用户可能会重新定位整个体验通过移动该多维数据集。</span><span class="sxs-lookup"><span data-stu-id="42fc6-244">In the application, users may reposition the entire experience by moving the cube.</span></span> 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > <span data-ttu-id="42fc6-246">注意：有多种以重新定位体验，包括要切换一个边框环绕体验，请使用 （如多维数据集在此步骤中使用），重新放置对象的位置和旋转 gizmos，请使用一个按钮使用的用户体验流和的详细信息。</span><span class="sxs-lookup"><span data-stu-id="42fc6-246">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="42fc6-247">祝贺</span><span class="sxs-lookup"><span data-stu-id="42fc6-247">Congratulations</span></span>
<span data-ttu-id="42fc6-248">在本课程中，已了解 Azure 空间的定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="42fc6-248">In this Lesson, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="42fc6-249">本课程为你提供了几个按钮，您可以浏览各个步骤所需启动和停止 Azure 的会话，并创建、 上载和下载单个设备上的 azure 定位点。</span><span class="sxs-lookup"><span data-stu-id="42fc6-249">This Lesson provided you with several buttons allowing you to explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="42fc6-250">在下一课中，我们将了解如何将 Azure 的定位标记 Id 保存到检索，在 HoloLens 2，即使重新启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="42fc6-250">In the next Lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="42fc6-251">系列中，你将还了解如何实现空间对齐方式的多个设备之间传输锚点 Id 和最终了解多用户共享会话 （即将发布的共享模块一部分）。</span><span class="sxs-lookup"><span data-stu-id="42fc6-251">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and eventually learn about multi-user shared sessions (forthcoming as part of sharing module.)</span></span>

[<span data-ttu-id="42fc6-252">下一课：ASA Lesson 2</span><span class="sxs-lookup"><span data-stu-id="42fc6-252">Next Lesson: ASA Lesson 2</span></span>](mrlearning-asa-ch2.md)
