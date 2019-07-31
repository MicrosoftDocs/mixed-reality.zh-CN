---
title: 在 HoloLens 2 上学习 ASA 模块 Azure 空间锚的 MR
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 9f830bc4ead35fd308108051617c61c65d98d451
ms.sourcegitcommit: c0d5c19b756b8e6ff95ea26a4d8d2b3a53878c2e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671968"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="a8ca3-104">1.Azure 空间定位点入门</span><span class="sxs-lookup"><span data-stu-id="a8ca3-104">1. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="a8ca3-105">欢迎使用 HoloLens 2 教程的第二个模块。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-105">Welcome to the second module of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="a8ca3-106">在开始之前, 请确保所有[先决条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)都已完成。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-106">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="a8ca3-107">如果尚未完成第一个、[基本模块](mrlearning-base.md), 则建议先完成该模块。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-107">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="a8ca3-108">如果从新的 Unity 项目开始, 请在[基本模块](mrlearning-base.md)中执行新的项目创建步骤。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-108">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="a8ca3-109">目标</span><span class="sxs-lookup"><span data-stu-id="a8ca3-109">Objectives</span></span>

* <span data-ttu-id="a8ca3-110">了解通过 Azure 空间锚点与 HoloLens 2 一起开发的基础知识</span><span class="sxs-lookup"><span data-stu-id="a8ca3-110">Learn the fundamentals of developing with Azure Spatial Anchors with HoloLens 2</span></span>

* <span data-ttu-id="a8ca3-111">创建、上传和下载空间锚</span><span class="sxs-lookup"><span data-stu-id="a8ca3-111">Create, upload, and download spatial anchors</span></span>

## <a name="instructions"></a><span data-ttu-id="a8ca3-112">说明</span><span class="sxs-lookup"><span data-stu-id="a8ca3-112">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="a8ca3-113">下载和导入资产</span><span class="sxs-lookup"><span data-stu-id="a8ca3-113">Downloading and importing assets</span></span>
<span data-ttu-id="a8ca3-114">开始之前, 请先下载并导入以下资产:</span><span class="sxs-lookup"><span data-stu-id="a8ca3-114">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="a8ca3-115">Azure 空间锚1.1。0</span><span class="sxs-lookup"><span data-stu-id="a8ca3-115">Azure Spatial Anchors v1.1.0</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[<span data-ttu-id="a8ca3-116">MR 基本模块资产包版本1。2</span><span class="sxs-lookup"><span data-stu-id="a8ca3-116">MR Base module Asset Pack v1.2</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/1.2/BaseModuleAssets-1.2.unitypackage)

[<span data-ttu-id="a8ca3-117">ASA 模块资产包 v1。0</span><span class="sxs-lookup"><span data-stu-id="a8ca3-117">ASA module Asset Pack v1.0</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/v1/ASAModuleAssets_1.unitypackage)

[<span data-ttu-id="a8ca3-118">混合现实工具包 2.0.0 RC1</span><span class="sxs-lookup"><span data-stu-id="a8ca3-118">Mixed Reality Toolkit 2.0.0RC1</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)

> <span data-ttu-id="a8ca3-119">注意:有关混合现实工具包 (MRKT) 上的特定说明, 请参阅步骤5获取有关如何导入 Azure 空间锚, 步骤6的特定说明。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-119">Note: See Step 5 for specific instructions on how to import Azure Spatial Anchors, Step 6 for specific instructions on the MR Base module Asset Pack, and steps 3 through 4 for specific instructions on the Mixed Reality Toolkit (MRKT).</span></span>

1. <span data-ttu-id="a8ca3-120">在项目中创建新场景。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-120">Create a new scene in your project.</span></span> <span data-ttu-id="a8ca3-121">右键单击场景文件夹, 单击 "创建", 然后单击 "场景"。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-121">Right click your Scene folder, click Create, then Scene.</span></span> <span data-ttu-id="a8ca3-122">将新场景命名为 ASALearningmodule。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-122">Name the new scene ASALearningmodule.</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="a8ca3-124">双击 "ASALearningmodule" 以查看一些预定义的项以及新场景。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-124">Double click ASALearningmodule to see some pre-defined items appear along with the new scene.</span></span> 
3. <span data-ttu-id="a8ca3-125">为混合现实开发配置场景。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="a8ca3-127">注意:你将看到一个弹出窗口, 你必须为混合现实工具包选择一个文件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-127">Note: You will see a pop-up that says, You must choose a file for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="a8ca3-128">单击 "确定" 将转到步骤4。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-128">Clicking Ok brings you to Step 4.</span></span>

4. <span data-ttu-id="a8ca3-129">选择 MRTK 的文件时, 请选择 "DefaultMixedRealityToolkitConfigurationProfile"。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-129">When choosing a file for the MRTK, select, DefaultMixedRealityToolkitConfigurationProfile.</span></span>

> <span data-ttu-id="a8ca3-130">注意:如果你有自己的配置文件, 可以改为随意使用该配置文件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="a8ca3-132">现在为混合现实配置场景。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-132">Now the scene is configured for mixed reality.</span></span> <span data-ttu-id="a8ca3-133">请确保保存场景 (用 control/command + S 执行此操作, 或单击 "文件", 然后单击 "保存")。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-133">Make sure you save your scene (do this with either control/command+S or click on file, then click on Save).</span></span> 

5. <span data-ttu-id="a8ca3-134">导入[Azure 空间锚](https://github.com/azure/azure-spatial-anchors-samples/releases)。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-134">Import the [Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases).</span></span> <span data-ttu-id="a8ca3-135">若要使用空间锚, 必须导入此资产。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-135">In order to use spatial anchors, you must import this asset.</span></span> <span data-ttu-id="a8ca3-136">单击上面的链接, 右键单击 "AzureSpatialAnchors. unitypackage"。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-136">Click on the link above and right click on AzureSpatialAnchors.unitypackage.</span></span> <span data-ttu-id="a8ca3-137">单击 "将目标另存为" 并将其保存到计算机。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-137">Click on Save Target As and save it to your computer.</span></span> 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

<span data-ttu-id="a8ca3-139">保存后, 返回到 Unity, 单击 "资产", 进入 "导入包"。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-139">After it's saved, go back into Unity, click Assets, go down to Import Package.</span></span> <span data-ttu-id="a8ca3-140">然后单击 "自定义包 ..."您的计算机文件将打开。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-140">Then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="a8ca3-141">当他们执行此操作时, 请在 Azure 空间锚定包的保存位置, 并将其选中。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-141">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="a8ca3-142">然后单击 "打开"。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-142">Then click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

<span data-ttu-id="a8ca3-144">此时将显示一个弹出窗口, providingg 工具和设置列表, 并询问您要导入的内容。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-144">A pop-up appears, providingg a list of tools and settings, and asking you what to import.</span></span> <span data-ttu-id="a8ca3-145">选择***所有***可用选项, 然后单击 "导入"。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-145">Select ***all*** of the options available, then click Import.</span></span>

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> <span data-ttu-id="a8ca3-147">注意:请耐心等待, 导入需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-147">Note: Be patient, it will take a few minutes to import.</span></span> 

6. <span data-ttu-id="a8ca3-148">导入 [MR 基本模块资产包 https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) ] 接下来。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-148">Import [MR Base module Asset Pack]https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) next.</span></span> <span data-ttu-id="a8ca3-149">与步骤5类似, 单击上面的链接。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-149">Much like Step 5, click the link above.</span></span> <span data-ttu-id="a8ca3-150">然后右键单击 "BasemoduleAssetsV1 unitypackag", 并单击 "将目标另存为", 并将其保存到计算机。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-150">Then right click BasemoduleAssetsV1 1.unitypackag, and click Save Target As, and save it to your computer.</span></span>

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> <span data-ttu-id="a8ca3-152">提示：将所有这些资产保存在同一个文件夹中, 以使其更易于查找并有权访问。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-152">Tip: Save all these assets in the same folder so that they are easier to find and have access to.</span></span> <span data-ttu-id="a8ca3-153">它使一切保持良好和条理。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-153">It keeps everything nice and organized.</span></span>

<span data-ttu-id="a8ca3-154">与步骤5类似, 返回到 Unity, 单击 "资产", 并将鼠标悬停在 "导入包" 上方。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-154">Just like Step 5, go back in to Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="a8ca3-155">单击 "自定义包 ..."您的计算机文件将再次出现。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-155">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="a8ca3-156">中转到存储基本模块资产包的位置。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-156">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="a8ca3-157">并选择它。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-157">and select it.</span></span> <span data-ttu-id="a8ca3-158">单击“打开”。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-158">Click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> <span data-ttu-id="a8ca3-160">注意:此模块后面可能需要更多的资产。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-160">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="a8ca3-161">按照以下步骤导入从此点开始提到的任何资产。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-161">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="a8ca3-162">使用与导入先前包相同的方法导入[ASA 模块包](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1)。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-162">Import the [ASA module pack](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1) using the same approach as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="a8ca3-163">配置场景</span><span class="sxs-lookup"><span data-stu-id="a8ca3-163">Configuring your scene</span></span>

<span data-ttu-id="a8ca3-164">在本部分中, 我们将 prototyping 和脚本添加到场景中, 以创建一系列按钮, 这些按钮演示了本地锚点和 Azure 空间锚点在应用程序中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-164">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

8. <span data-ttu-id="a8ca3-165">在 "项目" 选项卡上的 "资产" 文件夹下, 单击 "ASAmoduleAssets"。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-165">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="a8ca3-166">选择后, 将看到两个 prototyping:ButtonParent 和 ParentAnchor。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-166">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. <span data-ttu-id="a8ca3-168">将这两个 prototyping 拖放到场景中。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-168">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

10. <span data-ttu-id="a8ca3-170">双击父定位点以将其选中。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-170">Double click on the parent anchor to select it.</span></span> <span data-ttu-id="a8ca3-171">你可能需要调整视图以查看整个场景。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-171">You might need to adjust your view to see the entire scene.</span></span> <span data-ttu-id="a8ca3-172">根据需要调整场景。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-172">Adjust your scene as needed.</span></span>

<span data-ttu-id="a8ca3-173">熟悉 ParentAnchor prefab。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-173">Familiarize yourself with the ParentAnchor prefab.</span></span> <span data-ttu-id="a8ca3-174">目前, 名为 ParentAnchor 的游戏对象是一个彩色多维数据集, 用于演示目的。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-174">Currently, the game object named, ParentAnchor, is a colored cube for demonstration purposes.</span></span> <span data-ttu-id="a8ca3-175">最后, 我们将隐藏该多维数据集, 并将内容作为 ParentAnchor 的子元素。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-175">Eventually, we',ll hide the cube and place our content as a child of the ParentAnchor.</span></span> <span data-ttu-id="a8ca3-176">此 prefab 包括 ASA SDK 中包含的 AzureSpatialAnchorsDemoWrapper.cs 脚本, 以及作为此模块的一部分包含到 ParentAnchor 对象的 ASAmoduleScript.cs 脚本。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-176">This prefab includes the AzureSpatialAnchorsDemoWrapper.cs script (included with the ASA SDK), and the ASAmoduleScript.cs script, included as part of this module to the ParentAnchor object.</span></span> 

11. <span data-ttu-id="a8ca3-177">配置按钮。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-177">Configure buttons.</span></span> <span data-ttu-id="a8ca3-178">在 ButtonParent prefab 下, 注意若干标记的按钮。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-178">Under the ButtonParent prefab, notice several labeled buttons.</span></span> <span data-ttu-id="a8ca3-179">这些按钮是从 MRTK 的 PressableButton prototyping 中创建的。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-179">These buttons are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="a8ca3-180">详细了解如何从[基本模块](mrlearning-base-ch2.md)创建 Pressable 按钮。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-180">Learn more about how to create Pressable Buttons from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="a8ca3-181">对于每个按钮, 添加一个事件, 当用户根据以下列表按下或选择该按钮时, 将触发该事件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-181">For each button, add an event that will be triggered when the user presses or selects the button according to the list below.</span></span> 

- <span data-ttu-id="a8ca3-182">对于名为 "StartAzureSession" 的按钮, 请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-182">For the Button named, StartAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="a8ca3-183">将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 StartAzureSession () 方法。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-183">Drag the ParentAnchor object into the empty field, and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="a8ca3-187">对于按钮名称 StopAzureSession, 请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-187">For the Button name, StopAzureSession, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="a8ca3-188">将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 StopAzureSession () 方法。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-188">Drag the ParentAnchor object into the empty field, and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="a8ca3-189">对于名为 "CreateAnchor" 的按钮, 请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-189">For the Button named, CreateAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="a8ca3-190">将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 CreateAzureAnchor () 方法。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-190">Drag the ParentAnchor object into the empty field, and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="a8ca3-191">对于名为的按钮, 请开始查找定位点, 在 "按" 事件触发器和 On Click 事件触发器下创建新事件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-191">For the Button named, Start Looking For Anchor, create a new event under the Button Presse" event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="a8ca3-192">将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 FindAzureAnchor () 方法。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-192">Drag the ParentAnchor object into the empty field, and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="a8ca3-193">对于名为 "DeleteAzureAnchor" 的按钮, 请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-193">For the Button named, DeleteAzureAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="a8ca3-194">将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 DeleteAzureAnchor () 方法。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-194">Drag the ParentAnchor object into the empty field, and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="a8ca3-195">对于名为的按钮, 删除本地定位点, 在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-195">For the Button named, Delete Local Anchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="a8ca3-196">将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 RemoveLocalAnchor () 方法。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-196">Drag the ParentAnchor object into the empty field, and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="a8ca3-197">构建并演示基本应用程序</span><span class="sxs-lookup"><span data-stu-id="a8ca3-197">Build and demonstrate Base Application</span></span>

<span data-ttu-id="a8ca3-198">现在, 你的场景已配置为演示 Azure 空间锚的基本知识, 我们将构建并演示 Azure 空间锚的基本行为。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-198">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="a8ca3-199">如果在前面的部分关闭了“生成设置”窗口，请转到“文件”>“生成设置”，再次打开生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-199">If you closed the Build Settings window from the previous sections, open the build settings window again by going to File>Build Settings.</span></span>
<span data-ttu-id="a8ca3-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="a8ca3-200">![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="a8ca3-201">单击 "添加打开的场景" 按钮, 确保你想要尝试的场景处于 "生成" 列表中的场景中。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-201">Ensure the scene you want to try is in the Scenes in Build list by clicking on the Add Open Scenes button.</span></span>

3. <span data-ttu-id="a8ca3-202">按“生成”按钮开始生成过程。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-202">Press the Build button to begin the build process.</span></span>
<span data-ttu-id="a8ca3-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="a8ca3-203">![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="a8ca3-204">为应用程序创建一个新文件夹并为其命名。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-204">Create and name a new folder for your application.</span></span> <span data-ttu-id="a8ca3-205">在下图中, 创建了一个包含应用程序的名称为 "应用程序" 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-205">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="a8ca3-206">单击 "选择文件夹", 开始生成到新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-206">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="a8ca3-207">完成生成后, 可以关闭 Unity 中的 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-207">After the build has completed, you may close the Build Setting" window in Unity.</span></span> 
<span data-ttu-id="a8ca3-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="a8ca3-208">![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

  > <span data-ttu-id="a8ca3-209">注意：如果生成失败，尝试再次生成或重启 Unity 并再次生成。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-209">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="a8ca3-210">如果看到错误，如“错误：CS0246 = 找不到键入或命名空间名称 "XX" (是否缺少 using 指令或程序集引用？)。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-210">If you see an error such as "Error: CS0246 = The tyoe or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="a8ca3-211">你可能需要安装[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="a8ca3-211">You might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span> 
  >

5. <span data-ttu-id="a8ca3-212">生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-212">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="a8ca3-213">双击 "MixedRealityBase 解决方案或对应的名称。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-213">Double click on the“MixedRealityBase.sln solution or the corresponding name.</span></span> <span data-ttu-id="a8ca3-214">如果你在 Visual Studio 中为你的项目使用了替代名称来打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-214">if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

  > <span data-ttu-id="a8ca3-215">注意:如果遵循前面步骤中的命名约定, 请确保打开新创建的文件夹 (即 App 文件夹), 因为在该文件夹外, 不会与 build 文件夹内的 .sln 文件混淆的名称类似。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-215">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps because there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> <span data-ttu-id="a8ca3-217">注意:如果 Visual Studio 要求安装新组件, 请花点时间确保所有必备组件都按照["安装工具" 页中的](install-the-tools.md)特定方式进行安装</span><span class="sxs-lookup"><span data-stu-id="a8ca3-217">Note: If Visual Studio asks to install new components, please take a moment to ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span> 

6. <span data-ttu-id="a8ca3-218">使用 USB 电缆将 HoloLens 2 插入电脑。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-218">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="a8ca3-219">虽然这些课程说明假设你要使用 HoloLens 2 设备部署测试, 但你也可以选择将部署到[hololens 2 模拟器](using-the-hololens-emulator.md), 或选择创建[用于旁加载的应用程序包](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="a8ca3-219">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="a8ca3-220">在生成到设备之前，请确保设备处于开发者模式。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-220">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="a8ca3-221">如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-221">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="a8ca3-222">如果需要使用 Visual Studio 启用开发人员模式或配对, 请遵循[这些说明](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-222">Follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="a8ca3-223">通过选择 "发布配置" 和 "RM 体系结构", 将 Visual Studio 配置为生成到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-223">Configure Visual Studio for building to your HoloLens 2 by selecting the Release configuration as well as the RM architecture.</span></span>
<span data-ttu-id="a8ca3-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="a8ca3-224">![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)</span></span>
   
9. <span data-ttu-id="a8ca3-225">最后一步是通过选择 "调试" > "开始执行 (不调试)" 来生成设备。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-225">The final Step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="a8ca3-226">如果选择 "启动但不调试", 则在 Visual Studio 中显示成功的 ithout 调试信息时, 应用程序将立即在设备上启动。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-226">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build ithout Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="a8ca3-227">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-227">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="a8ca3-228">你还可以选择 "生成" > 部署解决方案以部署到设备, 而无需应用程序自动启动。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-228">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>
<span data-ttu-id="a8ca3-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span><span class="sxs-lookup"><span data-stu-id="a8ca3-229">![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)</span></span>
   
10. <span data-ttu-id="a8ca3-230">按照说明操作。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-230">Follow the instructions.</span></span> <span data-ttu-id="a8ca3-231">当应用程序在你的设备上运行时, 请按照屏幕上的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-231">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="a8ca3-232">按以下步骤对应的场景按钮。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-232">Press the Scene buttons corresponding to the Steps below.</span></span>

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="a8ca3-234">启动空间锚点会话。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-234">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="a8ca3-235">将多维数据集移到其他位置。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-235">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="a8ca3-236">将 Azure 空间锚点保存在多维数据集的位置。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-236">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="a8ca3-237">停止 Azure 空间锚点会话。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-237">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="a8ca3-238">删除多维数据集上的本地定位点, 以允许用户移动多维数据集。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-238">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    
    6. <span data-ttu-id="a8ca3-239">将多维数据集移到其他位置。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-239">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="a8ca3-240">启动 Azure 空间锚点会话。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-240">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="a8ca3-241">查找 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-241">Find Azure Spatial Anchors.</span></span> 
    <span data-ttu-id="a8ca3-242">你应返回到创建定位点时将其放入的原位置。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-242">You should go back to the original place you put it when you created the anchor.</span></span>
    
    9. <span data-ttu-id="a8ca3-243">删除 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-243">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="a8ca3-244">停止 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-244">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="a8ca3-245">定位体验</span><span class="sxs-lookup"><span data-stu-id="a8ca3-245">Anchoring an experience</span></span>

<span data-ttu-id="a8ca3-246">在前面的部分中, 已了解 Azure 空间锚的基础知识。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-246">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a8ca3-247">我们已使用多维数据集来表示父游戏对象并将其可视化。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-247">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="a8ca3-248">在本部分中, 你将了解如何通过将整个体验放置为 ParentAnchor 对象的子项来定位整个体验。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-248">In this section, you learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="a8ca3-249">在此示例中, 我们使用在[基础模块第6课](mrlearning-base-ch6.md)中创建的农历模块程序集演示应用程序。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-249">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="a8ca3-250">搜索农历 Module Assembly Complete prefab, 并将其作为 AnchorParent gameobject 的子元素拖动到您的层次结构中, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-250">Search for the Lunar Module Assembly Complete prefab, and drag it into your heirarchy as a child of the AnchorParent gameobject as shown in the image below.</span></span>

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="a8ca3-252">定位模块程序集体验, 使多维数据集仍公开, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-252">Position the module assembly experience so that the cube is still exposed as shown in the image below.</span></span> <span data-ttu-id="a8ca3-253">在应用程序中, 用户可以通过移动多维数据集来重新定位整个体验。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-253">In the application, users may reposition the entire experience by moving the cube.</span></span> 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> <span data-ttu-id="a8ca3-255">注意:用于重定位体验的用户体验有多种, 包括使用按钮切换环绕体验的边界框、使用重定位对象 (如此步骤中使用的多维数据集)、位置和旋转 gizmos等。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-255">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a8ca3-256">祝贺</span><span class="sxs-lookup"><span data-stu-id="a8ca3-256">Congratulations</span></span>
<span data-ttu-id="a8ca3-257">在本教程中, 已了解 Azure 空间锚的基础知识。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-257">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a8ca3-258">此 esson 提供了多个按钮, 使你可以浏览启动和停止 Azure 会话所需的各种步骤, 以及在单个设备上创建、上传和下载 azure 锚。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-258">This esson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session, and create, upload, and download azure anchors on a single device.</span></span> <span data-ttu-id="a8ca3-259">在下一课中, 我们将了解如何将 Azure 定位 Id 保存到 HoloLens 2 以便检索, 甚至在应用程序重新启动后也是如此。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-259">In the next lesson, we'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="a8ca3-260">在此系列中, 你还将了解如何在多个设备之间传输定位点 Id 以实现空间对齐, 并了解多用户共享会话, 作为共享教程的一部分。</span><span class="sxs-lookup"><span data-stu-id="a8ca3-260">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment, and learn about multi-user shared sessions, forthcoming as part of Sharing tutorial.</span></span>

[<span data-ttu-id="a8ca3-261">下一课：2.保存、检索和共享 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="a8ca3-261">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

