---
title: MR 学习 ASA 模块 Azure HoloLens 2 上的空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: c120d22f955d366042bbcb9ac73eaa4f13dc20e9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415270"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a><span data-ttu-id="47e56-104">开始使用 Azure HoloLens 2 上的空间定位点</span><span class="sxs-lookup"><span data-stu-id="47e56-104">Getting started with Azure Spatial Anchors on HoloLens 2</span></span>

<span data-ttu-id="47e56-105">欢迎使用 HoloLens 2 教程的第二个模块。</span><span class="sxs-lookup"><span data-stu-id="47e56-105">Welcome to the second module of the HoloLens 2 Tutorial.</span></span> <span data-ttu-id="47e56-106">开始之前，请确保所有的[先决条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)都已完成。</span><span class="sxs-lookup"><span data-stu-id="47e56-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="47e56-107">如果您尚未完成第一种[的基本模块](mrlearning-base.md)尚，建议您首先完成该模块。</span><span class="sxs-lookup"><span data-stu-id="47e56-107">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="47e56-108">如果要从新的 Unity 项目开始，按照中的新项目创建步骤[的基本模块](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="47e56-108">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="47e56-109">目标</span><span class="sxs-lookup"><span data-stu-id="47e56-109">Objectives</span></span>

* <span data-ttu-id="47e56-110">了解使用 Azure HoloLens 2 的空间定位点进行开发基础的知识</span><span class="sxs-lookup"><span data-stu-id="47e56-110">Learn the fundamentals of developing with Azure Spatial Anchors with the HoloLens 2</span></span>

* <span data-ttu-id="47e56-111">创建、 上传和下载空间的定位点</span><span class="sxs-lookup"><span data-stu-id="47e56-111">Create, Upload, and Download Spatial Anchors</span></span>

  

## <a name="instructions"></a><span data-ttu-id="47e56-112">说明</span><span class="sxs-lookup"><span data-stu-id="47e56-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="47e56-113">下载和导入资产</span><span class="sxs-lookup"><span data-stu-id="47e56-113">Downloading and importing assets</span></span>
<span data-ttu-id="47e56-114">开始时之前, 下载并导入以下资产：</span><span class="sxs-lookup"><span data-stu-id="47e56-114">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="47e56-115">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="47e56-115">Azure Spatial Anchors</span></span>](https://github.com/azure/azure-spatial-anchors-samples/releases)

[<span data-ttu-id="47e56-116">MR 基本模块资产包</span><span class="sxs-lookup"><span data-stu-id="47e56-116">MR Base module Asset Pack</span></span>](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[<span data-ttu-id="47e56-117">ASA 模块资产包</span><span class="sxs-lookup"><span data-stu-id="47e56-117">ASA module Asset Pack</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[<span data-ttu-id="47e56-118">混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="47e56-118">Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> <span data-ttu-id="47e56-119">注意：有关如何导入 Azure 空间的定位点、 MR 基本模块资产包的具体说明的步骤 6 和步骤 3 到 4 有关具体说明混合现实工具包 (MRKT) 的特定说明，请参阅步骤 5。</span><span class="sxs-lookup"><span data-stu-id="47e56-119">Note: See Step 5 for specific instructions on how to import Azure Spatial Anchors, Step 6 for specific instructions on the MR Base module Asset Pack, and steps 3 through 4 for specific instructions on the Mixed Reality Toolkit (MRKT).</span></span>

1. <span data-ttu-id="47e56-120">在项目中创建新的场景。</span><span class="sxs-lookup"><span data-stu-id="47e56-120">Create a new scene in your project.</span></span> <span data-ttu-id="47e56-121">右键单击场景文件夹中，单击"创建，"然后场景。</span><span class="sxs-lookup"><span data-stu-id="47e56-121">Right click your Scene folder, click "Create," then Scene.</span></span> <span data-ttu-id="47e56-122">命名新的场景 ASALearningmodule。</span><span class="sxs-lookup"><span data-stu-id="47e56-122">Name the new scene ASALearningmodule.</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="47e56-124">双击 ASALearningmodule 若要查看某些预定义的项目显示以及新的场景。</span><span class="sxs-lookup"><span data-stu-id="47e56-124">Double click ASALearningmodule to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="47e56-125">配置用于混合的现实开发场景。</span><span class="sxs-lookup"><span data-stu-id="47e56-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="47e56-127">注意：显示弹出窗口，指出，"您必须选择一个文件的混合现实工具包。"</span><span class="sxs-lookup"><span data-stu-id="47e56-127">Note: You will see a pop-up that says, "You must choose a file for the Mixed Reality Toolkit."</span></span> <span data-ttu-id="47e56-128">单击确定转到步骤 4。</span><span class="sxs-lookup"><span data-stu-id="47e56-128">Clicking Ok brings you to Step 4.</span></span>

4. <span data-ttu-id="47e56-129">当为 MRTK 选择一个文件，选择，DefaultMixedRealityToolkitConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="47e56-129">When choosing a file for the MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.</span></span>

   > <span data-ttu-id="47e56-130">注意：如果必须自己配置的配置文件，请随意使用该副本。</span><span class="sxs-lookup"><span data-stu-id="47e56-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="47e56-132">现在场景配置为使用混合现实。</span><span class="sxs-lookup"><span data-stu-id="47e56-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="47e56-133">请确保保存您的场景 (执行此操作与任一控件 / 命令 + S 或单击文件，然后单击保存)。</span><span class="sxs-lookup"><span data-stu-id="47e56-133">Make sure you save your scene (do this with either control/command+S or click on file, then click on Save).</span></span> 

5. <span data-ttu-id="47e56-134">导入[Azure 空间的定位点](https://github.com/azure/azure-spatial-anchors-samples/releases)。</span><span class="sxs-lookup"><span data-stu-id="47e56-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="47e56-135">若要使用空间的定位点，必须导入此资产。</span><span class="sxs-lookup"><span data-stu-id="47e56-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="47e56-136">单击上面的链接并右键单击 AzureSpatialAnchors.unitypackage。</span><span class="sxs-lookup"><span data-stu-id="47e56-136">Click on the link above and right click on AzureSpatialAnchors.unitypackage.</span></span> <span data-ttu-id="47e56-137">在目标另存为上单击，并将其保存到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="47e56-137">Click on Save Target As and save it to your computer.</span></span> 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   <span data-ttu-id="47e56-139">保存后，请转回 Unity 中，单击资产，转到导入包。</span><span class="sxs-lookup"><span data-stu-id="47e56-139">After it's saved, go back into Unity, click Assets, go down to Import Package.</span></span> <span data-ttu-id="47e56-140">然后单击自定义包...将打开你的计算机文件。</span><span class="sxs-lookup"><span data-stu-id="47e56-140">Then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="47e56-141">当它们执行操作，查找 Azure 空间的定位点包的保存位置并选择它。</span><span class="sxs-lookup"><span data-stu-id="47e56-141">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="47e56-142">然后单击打开。</span><span class="sxs-lookup"><span data-stu-id="47e56-142">Then click Open.</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   <span data-ttu-id="47e56-144">弹出一个窗口，providingg 工具和设置，并询问您要导入的列表。</span><span class="sxs-lookup"><span data-stu-id="47e56-144">A pop-up appears, providingg a list of tools and settings, and asking you what to import.</span></span> <span data-ttu-id="47e56-145">选择***所有***的可用的选项，然后单击导入。</span><span class="sxs-lookup"><span data-stu-id="47e56-145">Select ***all*** of the options available, then click Import.</span></span>

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > <span data-ttu-id="47e56-147">注意：请耐心等待，它将需要几分钟来导入。</span><span class="sxs-lookup"><span data-stu-id="47e56-147">Note: Be patient, it will take a few minutes to import.</span></span> 

   6. <span data-ttu-id="47e56-148">导入[MR 基本模块资产包](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)下一步。</span><span class="sxs-lookup"><span data-stu-id="47e56-148">Import [MR Base module Asset Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) next.</span></span> <span data-ttu-id="47e56-149">更像步骤 5 中，单击上面的链接。</span><span class="sxs-lookup"><span data-stu-id="47e56-149">Much like Step 5, click the link above.</span></span> <span data-ttu-id="47e56-150">然后右键单击 BasemoduleAssetsV1 1.unitypackag，并单击目标另存为，并将其保存到您的计算机。</span><span class="sxs-lookup"><span data-stu-id="47e56-150">Then right click BasemoduleAssetsV1 1.unitypackag, and click Save Target As, and save it to your computer.</span></span>

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > <span data-ttu-id="47e56-152">提示：将所有这些资产保存在同一文件夹，以便可以更轻松地查找和有权访问。</span><span class="sxs-lookup"><span data-stu-id="47e56-152">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="47e56-153">它会保留所有内容和组织更好。</span><span class="sxs-lookup"><span data-stu-id="47e56-153">It keeps everything nice and organized.</span></span>

   <span data-ttu-id="47e56-154">就像步骤 5 中，返回到 Unity、 单击资源，并悬停在导入包。</span><span class="sxs-lookup"><span data-stu-id="47e56-154">Just like Step 5, go back in to Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="47e56-155">单击自定义包...你的计算机文件将会再次出现。</span><span class="sxs-lookup"><span data-stu-id="47e56-155">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="47e56-156">请转到你在其中存储的基本模块资产包。</span><span class="sxs-lookup"><span data-stu-id="47e56-156">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="47e56-157">然后选择它。</span><span class="sxs-lookup"><span data-stu-id="47e56-157">and select it.</span></span> <span data-ttu-id="47e56-158">单击“打开”。</span><span class="sxs-lookup"><span data-stu-id="47e56-158">Click Open.</span></span>

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > <span data-ttu-id="47e56-160">注意：可能需要更高版本在此模块中的多个资产。</span><span class="sxs-lookup"><span data-stu-id="47e56-160">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="47e56-161">按照这些步骤导入所述从该点上的任何资产。</span><span class="sxs-lookup"><span data-stu-id="47e56-161">Follow these steps to import any assets mentioned from this point on.</span></span> 
                                                                                                                                                                                                                    
7. <span data-ttu-id="47e56-162">导入 ASA 模块确认作为导入之前的包使用相同的方法。</span><span class="sxs-lookup"><span data-stu-id="47e56-162">Import the ASA module ack using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="47e56-163">配置您的场景</span><span class="sxs-lookup"><span data-stu-id="47e56-163">Configuring your scene</span></span>

<span data-ttu-id="47e56-164">在本部分中，我们会将预设和脚本添加到场景中，从而创建一系列演示应用程序中本地定位点和 Azure 空间的定位点的行为方式的基础知识的按钮。</span><span class="sxs-lookup"><span data-stu-id="47e56-164">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

7. <span data-ttu-id="47e56-165">在项目选项卡下的资产文件夹中，单击 ASAmoduleAssets。</span><span class="sxs-lookup"><span data-stu-id="47e56-165">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="47e56-166">选择后，你将看到两个预设：ButtonParent 和 ParentAnchor。</span><span class="sxs-lookup"><span data-stu-id="47e56-166">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. <span data-ttu-id="47e56-168">将这两个预设拖到场景。</span><span class="sxs-lookup"><span data-stu-id="47e56-168">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. <span data-ttu-id="47e56-170">双击父定位点，以将其选中。</span><span class="sxs-lookup"><span data-stu-id="47e56-170">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="47e56-171">您可能需要调整视图以查看整个场景。</span><span class="sxs-lookup"><span data-stu-id="47e56-171">You might need to adjust your view to see the entire scene.</span></span> <span data-ttu-id="47e56-172">根据需要调整您的场景。</span><span class="sxs-lookup"><span data-stu-id="47e56-172">Adjust your scene as needed.</span></span>

    <span data-ttu-id="47e56-173">自行熟悉 ParentAnchor 预设。</span><span class="sxs-lookup"><span data-stu-id="47e56-173">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="47e56-174">目前，游戏对象命名，ParentAnchor，是出于演示目的的彩色多维数据集。</span><span class="sxs-lookup"><span data-stu-id="47e56-174">Currently, the game object named, ParentAnchor, is a colored cube for demonstration purposes.</span></span> <span data-ttu-id="47e56-175">最终，我们，ll 隐藏该多维数据集并将它们作为子级 ParentAnchor 放置我们的内容。</span><span class="sxs-lookup"><span data-stu-id="47e56-175">Eventually, we',ll hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="47e56-176">此预设可包括 AzureSpatialAnchorsDemoWrapper.cs 脚本 （包含在 ASA SDK），以及作为 ParentAnchor 对象到此模块的一部分包含的 ASAmoduleScript.cs 脚本。</span><span class="sxs-lookup"><span data-stu-id="47e56-176">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK), and the ASAmoduleScript.cs script, included as part of this module to the ParentAnchor object.</span></span> 

10. <span data-ttu-id="47e56-177">配置按钮。</span><span class="sxs-lookup"><span data-stu-id="47e56-177">Configure buttons.</span></span> <span data-ttu-id="47e56-178">下 ParentAnchor 预设，请注意，多个标记的按钮。</span><span class="sxs-lookup"><span data-stu-id="47e56-178">Under the ParentAnchor prefab, notice several labeled buttons.</span></span> <span data-ttu-id="47e56-179">从 MRTK PressableButton 预设，则创建这些按钮。</span><span class="sxs-lookup"><span data-stu-id="47e56-179">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="47e56-180">了解有关如何创建从 Pressable 按钮的详细信息[的基本模块](mrlearning-base-ch2.md)。</span><span class="sxs-lookup"><span data-stu-id="47e56-180">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="47e56-181">每个按钮，将添加在用户按下或选择根据下面的列表按钮时，将触发的事件。</span><span class="sxs-lookup"><span data-stu-id="47e56-181">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="47e56-182">对于名为 StartAzureSession，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="47e56-182">For the Button named, StartAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47e56-183">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 StartAzureSession() 方法。</span><span class="sxs-lookup"><span data-stu-id="47e56-183">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="47e56-187">对于按钮名称，StopAzureSession，创建新的事件下按下按钮事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="47e56-187">For the Button name, StopAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47e56-188">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 StopAzureSession() 方法。</span><span class="sxs-lookup"><span data-stu-id="47e56-188">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="47e56-189">对于名为 CreateAnchor，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="47e56-189">For the Button named, CreateAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47e56-190">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 CreateAzureAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="47e56-190">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="47e56-191">按钮命名为，开始查找的定位点，创建一个新按钮按下的事件"事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="47e56-191">For the Button named, Start Looking For Anchor, create a new event under the Button Presse" event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47e56-192">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 FindAzureAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="47e56-192">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="47e56-193">对于名为 DeleteAzureAnchor，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="47e56-193">For the Button named, DeleteAzureAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47e56-194">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 DeleteAzureAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="47e56-194">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="47e56-195">对于名为，删除本地定位点，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。</span><span class="sxs-lookup"><span data-stu-id="47e56-195">For the Button named, Delete Local Anchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="47e56-196">将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 RemoveLocalAnchor() 方法。</span><span class="sxs-lookup"><span data-stu-id="47e56-196">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="47e56-197">生成并演示基本应用程序</span><span class="sxs-lookup"><span data-stu-id="47e56-197">Build and demonstrate Base Application</span></span>

<span data-ttu-id="47e56-198">现在，您的场景配置来演示 Azure 空间的定位点的基础知识，我们将生成并演示 Azure 空间的定位点的基本行为。</span><span class="sxs-lookup"><span data-stu-id="47e56-198">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="47e56-199">如果在前面的部分关闭了“生成设置”窗口，请转到“文件”>“生成设置”，再次打开生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="47e56-199">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
    <span data-ttu-id="47e56-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="47e56-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="47e56-201">请确保你想要尝试的场景是在生成列表中的场景中通过单击添加打开场景按钮。</span><span class="sxs-lookup"><span data-stu-id="47e56-201">Ensure the scene you want to try is in the Scenes in Build list by clicking on the Add Open Scenes button.</span></span>

3. <span data-ttu-id="47e56-202">按“生成”按钮开始生成过程。</span><span class="sxs-lookup"><span data-stu-id="47e56-202">Press the Build button to begin the build process.</span></span>
    <span data-ttu-id="47e56-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="47e56-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="47e56-204">为应用程序创建一个新文件夹并为其命名。</span><span class="sxs-lookup"><span data-stu-id="47e56-204">Create and name a new folder for your application.</span></span> <span data-ttu-id="47e56-205">在下图中，创建具有名称应用的文件夹以包含应用程序。</span><span class="sxs-lookup"><span data-stu-id="47e56-205">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="47e56-206">单击选择文件夹若要开始新创建的文件夹中生成。</span><span class="sxs-lookup"><span data-stu-id="47e56-206">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="47e56-207">在 Unity 中完成生成后，你可以关闭生成设置"窗口。</span><span class="sxs-lookup"><span data-stu-id="47e56-207">After the build has completed, you may close the Build Setting" window in Unity.</span></span> 
    <span data-ttu-id="47e56-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="47e56-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="47e56-209">注意：如果生成失败，尝试再次生成或重启 Unity 并再次生成。</span><span class="sxs-lookup"><span data-stu-id="47e56-209">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="47e56-210">如果看到错误，如“错误：CS0246 = 找不到"XX"键入或命名空间名称 (是否缺少 using 指令或程序集引用？)。</span><span class="sxs-lookup"><span data-stu-id="47e56-210">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="47e56-211">可能需要安装[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="47e56-211">You might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="47e56-212">生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="47e56-212">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="47e56-213">双击 the"MixedRealityBase.sln 解决方案或相应的名称。</span><span class="sxs-lookup"><span data-stu-id="47e56-213">Double click on the“MixedRealityBase.sln solution or the corresponding name.</span></span> <span data-ttu-id="47e56-214">如果你的项目的替代名称用于在 Visual Studio 中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="47e56-214">if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="47e56-215">注意：请务必打开新创建的文件夹 （即，应用程序文件夹，如果从前面的步骤遵循命名约定，因为外部不会与生成文件夹中的.sln 文件混淆，该文件夹的类似名称的.sln 文件。</span><span class="sxs-lookup"><span data-stu-id="47e56-215">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps because there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > <span data-ttu-id="47e56-217">注意：如果 Visual Studio 要求安装新组件，请花点时间以确保安装所有必备组件中的具体["安装工具"页](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="47e56-217">Note: If Visual Studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="47e56-218">使用 USB 电缆将 HoloLens 2 插入电脑。</span><span class="sxs-lookup"><span data-stu-id="47e56-218">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="47e56-219">虽然这些课程说明假设将部署使用 HoloLens 2 设备进行测试，但是您还可选择将部署到[HoloLens 2 模拟器](using-the-hololens-emulator.md)或选择创建[的旁加载应用包](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="47e56-219">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="47e56-220">在生成到设备之前，请确保设备处于开发者模式。</span><span class="sxs-lookup"><span data-stu-id="47e56-220">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="47e56-221">如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。</span><span class="sxs-lookup"><span data-stu-id="47e56-221">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="47e56-222">请按照[这些说明](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)如果你需要启用开发人员模式或与 Visual Studio 配对。</span><span class="sxs-lookup"><span data-stu-id="47e56-222">Follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="47e56-223">通过选择发布配置和"RM"体系结构为构建到 HoloLens 2 配置 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="47e56-223">Configure Visual Studio for building to your HoloLens 2 by selecting the Release configuration and the “RM” architecture.</span></span>
    <span data-ttu-id="47e56-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="47e56-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
   
9. <span data-ttu-id="47e56-225">最后一步是向你的设备通过选择生成调试 > 启动但不调试。</span><span class="sxs-lookup"><span data-stu-id="47e56-225">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="47e56-226">选择但不调试的启动将导致应用程序以使其不显示在 Visual Studio 中的成功生成 ithout 调试信息时在设备上立即启动。</span><span class="sxs-lookup"><span data-stu-id="47e56-226">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build ithout Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="47e56-227">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="47e56-227">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="47e56-228">您还可能选择生成 > 部署解决方案，而无需自动启动该应用程序部署到你的设备。</span><span class="sxs-lookup"><span data-stu-id="47e56-228">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
    <span data-ttu-id="47e56-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="47e56-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
    
<span data-ttu-id="47e56-230">10.按照的说明。</span><span class="sxs-lookup"><span data-stu-id="47e56-230">10.Follow the instructions.</span></span> <span data-ttu-id="47e56-231">当在设备上运行应用程序时，请按照屏幕上的说明。</span><span class="sxs-lookup"><span data-stu-id="47e56-231">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="47e56-232">按场景按钮对应于下面的步骤。</span><span class="sxs-lookup"><span data-stu-id="47e56-232">Press the Scene buttons corresponding to the Steps below.</span></span>
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="47e56-233">启动空间的定位点会话。</span><span class="sxs-lookup"><span data-stu-id="47e56-233">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="47e56-234">将多维数据集移到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="47e56-234">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="47e56-235">保存该多维数据集的位置的 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="47e56-235">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="47e56-236">停止 Azure 空间的定位点会话。</span><span class="sxs-lookup"><span data-stu-id="47e56-236">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="47e56-237">删除多维数据集以允许用户移动该多维数据集上的本地定位点。</span><span class="sxs-lookup"><span data-stu-id="47e56-237">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    6. <span data-ttu-id="47e56-238">将移动到其他位置的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="47e56-238">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="47e56-239">启动 Azure 空间的定位点会话。</span><span class="sxs-lookup"><span data-stu-id="47e56-239">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="47e56-240">查找 Azure 空间 aachors。</span><span class="sxs-lookup"><span data-stu-id="47e56-240">Find Azure Spatial aachors.</span></span> 
    
    <span data-ttu-id="47e56-241">e 您应返回到原始位置，将其放在创建定位点时）。</span><span class="sxs-lookup"><span data-stu-id="47e56-241">e You should go back to the original place you put it when you created the anchor).</span></span>
    9. <span data-ttu-id="47e56-242">删除 Azure 空间的定位点。</span><span class="sxs-lookup"><span data-stu-id="47e56-242">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="47e56-243">停止 Azure 的会话。</span><span class="sxs-lookup"><span data-stu-id="47e56-243">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="47e56-244">锚定的体验</span><span class="sxs-lookup"><span data-stu-id="47e56-244">Anchoring an experience</span></span>

<span data-ttu-id="47e56-245">在前面部分中，您学习了 Azure 空间的定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="47e56-245">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="47e56-246">我们使用多维数据集来表示和可视化父级游戏对象使用附加的定位点。</span><span class="sxs-lookup"><span data-stu-id="47e56-246">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="47e56-247">在本部分中，您将学习如何通过将其放置 ParentAnchor 对象的子级作为定位整个体验。</span><span class="sxs-lookup"><span data-stu-id="47e56-247">In this section, you learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="47e56-248">对于此示例中，我们使用农历模块程序集演示应用程序创建期间[第 6 课中的基本模块](mrlearning-base-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="47e56-248">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="47e56-249">搜索农历模块程序集完整预设，并将其拖动到你的层次结构作为子 AnchorParent gameobject 中如下图所示。</span><span class="sxs-lookup"><span data-stu-id="47e56-249">Search for the Lunar Module Assembly Complete prefab, and drag it into your heirarchy as a child of the AnchorParent gameobject as shown in the image below.</span></span>

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="47e56-251">模块程序集位置体验，以便在多维数据集中所显示下图中所示。</span><span class="sxs-lookup"><span data-stu-id="47e56-251">Position the module assembly experience so that the cube is still exposed as shown in the image below.</span></span> <span data-ttu-id="47e56-252">在应用程序中，用户可能会重新定位整个体验通过移动该多维数据集。</span><span class="sxs-lookup"><span data-stu-id="47e56-252">In the application, users may reposition the entire experience by moving the cube.</span></span> 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > <span data-ttu-id="47e56-254">注意：有多种以重新定位体验，包括要切换一个边框环绕体验，请使用 （如多维数据集在此步骤中使用），重新放置对象的位置和旋转 gizmos，请使用一个按钮使用的用户体验流和的详细信息。</span><span class="sxs-lookup"><span data-stu-id="47e56-254">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="47e56-255">祝贺</span><span class="sxs-lookup"><span data-stu-id="47e56-255">Congratulations</span></span>
<span data-ttu-id="47e56-256">在本课程中，您学习了 Azure 空间的定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="47e56-256">In this lesson, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="47e56-257">此 esson 提供了几个按钮，您可以了解启动和停止 Azure 的会话，并创建、 上载和下载单个设备上的 azure 定位点所需的各种步骤。</span><span class="sxs-lookup"><span data-stu-id="47e56-257">This esson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="47e56-258">在下一课中，我们将了解如何将 Azure 的定位标记 Id 保存到检索，在 HoloLens 2，即使重新启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="47e56-258">In the next lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="47e56-259">在系列中，您还将了解如何实现空间对齐方式，并了解有关共享会话 （即将发布的共享模块一部分） 的多用户信息的多个设备之间传输锚点 Id</span><span class="sxs-lookup"><span data-stu-id="47e56-259">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and learn about multi-user shared sessions (forthcoming as part of sharing module.)</span></span>

[<span data-ttu-id="47e56-260">下一课：ASA Lesson 2</span><span class="sxs-lookup"><span data-stu-id="47e56-260">Next Lesson: ASA Lesson 2</span></span>](mrlearning-asa-ch2.md)

