---
title: Azure 空间锚点教程-1。 Azure 空间定位点入门
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b615f1135f5d2947f8f718e080ef45a3c1fcc576
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830849"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="7316b-105">1. Azure 空间定位点入门</span><span class="sxs-lookup"><span data-stu-id="7316b-105">1. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="7316b-106">欢迎使用 HoloLens 2 教程的第二个模块。</span><span class="sxs-lookup"><span data-stu-id="7316b-106">Welcome to the second module of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="7316b-107">在开始之前，请确保所有[先决条件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)都已完成。</span><span class="sxs-lookup"><span data-stu-id="7316b-107">Before getting started, be sure that all of the [prerequisites](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens) are completed.</span></span> <span data-ttu-id="7316b-108">如果尚未完成第一个、[基本模块](mrlearning-base.md)，则建议先完成该模块。</span><span class="sxs-lookup"><span data-stu-id="7316b-108">If you have not completed the first, [Base module](mrlearning-base.md) yet, it's recommended that you complete that module first.</span></span> <span data-ttu-id="7316b-109">如果从新的 Unity 项目开始，请在[基本模块](mrlearning-base.md)中执行新的项目创建步骤。</span><span class="sxs-lookup"><span data-stu-id="7316b-109">If you are starting from a new Unity project, follow the new project creation steps in the [Base module](mrlearning-base.md).</span></span> 

## <a name="objectives"></a><span data-ttu-id="7316b-110">目标</span><span class="sxs-lookup"><span data-stu-id="7316b-110">Objectives</span></span>

* <span data-ttu-id="7316b-111">了解通过 Azure 空间锚点与 HoloLens 2 一起开发的基础知识</span><span class="sxs-lookup"><span data-stu-id="7316b-111">Learn the fundamentals of developing with Azure Spatial Anchors with HoloLens 2</span></span>

* <span data-ttu-id="7316b-112">创建、上传和下载空间锚</span><span class="sxs-lookup"><span data-stu-id="7316b-112">Create, upload, and download spatial anchors</span></span>

## <a name="instructions"></a><span data-ttu-id="7316b-113">说明</span><span class="sxs-lookup"><span data-stu-id="7316b-113">Instructions</span></span>

### <a name="downloading-and-importing-assets"></a><span data-ttu-id="7316b-114">下载和导入资产</span><span class="sxs-lookup"><span data-stu-id="7316b-114">Downloading and importing assets</span></span>
<span data-ttu-id="7316b-115">开始之前，请先下载并导入以下资产：</span><span class="sxs-lookup"><span data-stu-id="7316b-115">Before beginning, download and import the following assets:</span></span>

[<span data-ttu-id="7316b-116">Azure 空间锚1.1。0</span><span class="sxs-lookup"><span data-stu-id="7316b-116">Azure Spatial Anchors v1.1.0</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[<span data-ttu-id="7316b-117">HoloLens2. GettingStarted. 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="7316b-117">Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

[<span data-ttu-id="7316b-118">HoloLens2. AzureSpatialAnchor. 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="7316b-118">Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchor-v2.1.0.0/Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage)

[<span data-ttu-id="7316b-119">混合现实工具包基础包2.1。0</span><span class="sxs-lookup"><span data-stu-id="7316b-119">Mixed Reality Toolkit  Foundation Package 2.1.0</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. <span data-ttu-id="7316b-120">在项目中创建新场景。</span><span class="sxs-lookup"><span data-stu-id="7316b-120">Create a new scene in your project.</span></span> <span data-ttu-id="7316b-121">右键单击场景文件夹，单击 "创建"，然后单击 "场景"。</span><span class="sxs-lookup"><span data-stu-id="7316b-121">Right-click your Scene folder, click Create, then Scene.</span></span> <span data-ttu-id="7316b-122">将新场景命名为 "ASALearningModule"。</span><span class="sxs-lookup"><span data-stu-id="7316b-122">Name the new scene as "ASALearningModule".</span></span>

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. <span data-ttu-id="7316b-124">双击 "ASALearningmodule" 场景，查看一些预定义的项以及新场景。</span><span class="sxs-lookup"><span data-stu-id="7316b-124">Double-click "ASALearningmodule" scene to see some pre-defined items to appear along with the new scene.</span></span> 
3. <span data-ttu-id="7316b-125">为混合现实开发配置场景。</span><span class="sxs-lookup"><span data-stu-id="7316b-125">Configure the scene for mixed reality development.</span></span> 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> <span data-ttu-id="7316b-127">注意：你可能会看到一个弹出对话框，用于选择[混合现实工具包的配置文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。</span><span class="sxs-lookup"><span data-stu-id="7316b-127">Note: You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="7316b-128">双击名为*DefaultHoloLens2ConfigurationProfile*的配置文件，将其选中。</span><span class="sxs-lookup"><span data-stu-id="7316b-128">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

4. <span data-ttu-id="7316b-129">选择 MRTK 的文件时，请选择 "DefaultMixedRealityToolkitConfigurationProfile"。</span><span class="sxs-lookup"><span data-stu-id="7316b-129">When choosing a file for the MRTK, select DefaultMixedRealityToolkitConfigurationProfile.</span></span>

> <span data-ttu-id="7316b-130">注意：如果你有自己的配置文件，可以改为随意使用该配置文件。</span><span class="sxs-lookup"><span data-stu-id="7316b-130">Note: If you have your own configuration profile, feel free to use that instead.</span></span>
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

<span data-ttu-id="7316b-132">现在为混合现实配置场景。</span><span class="sxs-lookup"><span data-stu-id="7316b-132">The scene is now configured for mixed reality.</span></span> <span data-ttu-id="7316b-133">请确保保存场景（使用 control/command + S 执行此操作，或单击 "文件"，然后单击 "保存"）。</span><span class="sxs-lookup"><span data-stu-id="7316b-133">Make sure you save your scene (do this with either control/command+S or click on file, followed by Save).</span></span> 

5. <span data-ttu-id="7316b-134">导入在步骤1中下载的[Azure 空间锚 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity 包。</span><span class="sxs-lookup"><span data-stu-id="7316b-134">Import the [Azure Spatial Anchors v1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) unity package that we downloaded in step 1.</span></span> <span data-ttu-id="7316b-135">为此，请单击 "资产"、"导入包"，然后单击 "自定义包 ..."您的计算机文件将打开。</span><span class="sxs-lookup"><span data-stu-id="7316b-135">For that, click Assets, go down to Import Package and then click Custom Package... Your computer files will open.</span></span> <span data-ttu-id="7316b-136">当他们执行此操作时，请在 Azure 空间锚定包的保存位置，并将其选中。</span><span class="sxs-lookup"><span data-stu-id="7316b-136">When they do, find where you saved the Azure Spatial Anchors package, and select it.</span></span> <span data-ttu-id="7316b-137">然后单击“打开”。</span><span class="sxs-lookup"><span data-stu-id="7316b-137">Then click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

<span data-ttu-id="7316b-139">此时将显示一个弹出窗口，其中提供了工具和设置的列表，并询问您要导入的内容。</span><span class="sxs-lookup"><span data-stu-id="7316b-139">A pop-up appears, providing a list of tools and settings and asking you what to import.</span></span> <span data-ttu-id="7316b-140">选择***所有***可用选项，然后单击 "导入"。</span><span class="sxs-lookup"><span data-stu-id="7316b-140">Select ***all*** of the options available, then click Import.</span></span>

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> <span data-ttu-id="7316b-142">注意：请耐心等待，导入需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="7316b-142">Note: Be patient, it will take a few minutes to import.</span></span> 

6. <span data-ttu-id="7316b-143">接下来导入[HoloLens2。 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) 。</span><span class="sxs-lookup"><span data-stu-id="7316b-143">Import [Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) next.</span></span> <span data-ttu-id="7316b-144">与步骤5类似，返回到 Unity，单击 "资产"，并将鼠标悬停在导入包上。</span><span class="sxs-lookup"><span data-stu-id="7316b-144">Much like Step 5, go back into Unity, click Assets, and hover over Import Package.</span></span> <span data-ttu-id="7316b-145">单击 "自定义包 ..."您的计算机文件将再次出现。</span><span class="sxs-lookup"><span data-stu-id="7316b-145">Click Custom Package... Your computer files will appear again.</span></span> <span data-ttu-id="7316b-146">中转到存储基本模块资产包的位置。</span><span class="sxs-lookup"><span data-stu-id="7316b-146">Go to where you stored the Base module Asset Pack.</span></span> <span data-ttu-id="7316b-147">并选择它。</span><span class="sxs-lookup"><span data-stu-id="7316b-147">and select it.</span></span> <span data-ttu-id="7316b-148">单击“打开”。</span><span class="sxs-lookup"><span data-stu-id="7316b-148">Click Open.</span></span>

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> <span data-ttu-id="7316b-150">注意：此模块后面可能需要更多资产。</span><span class="sxs-lookup"><span data-stu-id="7316b-150">Note: There might be more assets needed later in this module.</span></span> <span data-ttu-id="7316b-151">按照以下步骤导入从此点开始提到的任何资产。</span><span class="sxs-lookup"><span data-stu-id="7316b-151">Follow these steps to import any assets mentioned from this point on.</span></span> 

7. <span data-ttu-id="7316b-152">导入[ASA 模块包 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage)，使用与导入以前的包相同的步骤。</span><span class="sxs-lookup"><span data-stu-id="7316b-152">Import the [ASA module pack 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage), using the same steps as importing the previous packages.</span></span>

### <a name="configuring-your-scene"></a><span data-ttu-id="7316b-153">配置场景</span><span class="sxs-lookup"><span data-stu-id="7316b-153">Configuring your scene</span></span>

<span data-ttu-id="7316b-154">在本部分中，我们将 prototyping 和脚本添加到场景中，以创建一系列按钮，这些按钮演示了本地锚点和 Azure 空间锚点在应用程序中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="7316b-154">In this section, we will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

8. <span data-ttu-id="7316b-155">在 "项目" 选项卡上的 "资产" 文件夹下，单击 "ASAmoduleAssets"。</span><span class="sxs-lookup"><span data-stu-id="7316b-155">In the Project tab, underneath the Assets folder, click on ASAmoduleAssets.</span></span> <span data-ttu-id="7316b-156">选择后，将看到两个 prototyping： ButtonParent 和 ParentAnchor。</span><span class="sxs-lookup"><span data-stu-id="7316b-156">Once selected, you will see two prefabs: ButtonParent and ParentAnchor.</span></span>

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. <span data-ttu-id="7316b-158">将这两个 prototyping 拖放到场景中。</span><span class="sxs-lookup"><span data-stu-id="7316b-158">Drag both prefabs into the scene.</span></span> 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

<span data-ttu-id="7316b-160">注意：将 ButtonParent 添加到场景后，将显示一个弹出窗口，要求你导入 TMP 资产。</span><span class="sxs-lookup"><span data-stu-id="7316b-160">Note: After adding the ButtonParent into the scene, a pop-up will appear asking you to import TMP assets.</span></span> <span data-ttu-id="7316b-161">导入 "TMP Essentials"。</span><span class="sxs-lookup"><span data-stu-id="7316b-161">Import the "TMP Essentials".</span></span> <span data-ttu-id="7316b-162">此后，如果在场景中看到任何大字体文本，请删除 ButtonParent 对象，并从 ASAmoduleAssets 文件夹再次添加它。</span><span class="sxs-lookup"><span data-stu-id="7316b-162">After this, If you see any large font text in the scene, delete the ButtonParent object and add it again from the ASAmoduleAssets folder.</span></span>

<span data-ttu-id="7316b-163">注意：如果要检查 HoloLens 中的调试日志，可将 DebugWindow prefab 从 ASAModuleAssets 文件夹拖放到场景中。</span><span class="sxs-lookup"><span data-stu-id="7316b-163">Note: If you want to check the debug logs in the HoloLens, you can drag and drop the DebugWindow prefab from ASAModuleAssets folder into the scene.</span></span> <span data-ttu-id="7316b-164">在 DebugWindow 检查器面板中附加 DebugWindowMessaging 脚本，并启用 "调试窗口已启用" 选项。</span><span class="sxs-lookup"><span data-stu-id="7316b-164">Attach the DebugWindowMessaging script in the DebugWindow inspector panel and enable the Debug Window Enabled option.</span></span> <span data-ttu-id="7316b-165">然后，将 DebugWindow prefab 拖放到 DebugText 空字段。</span><span class="sxs-lookup"><span data-stu-id="7316b-165">After that, drag  and drop the DebugWindow prefab into the DebugText empty field.</span></span> <span data-ttu-id="7316b-166">你还可以根据需要调整 DebugWindow 位置。</span><span class="sxs-lookup"><span data-stu-id="7316b-166">You can also adjust the DebugWindow position wherever appropriate for you.</span></span>

10. <span data-ttu-id="7316b-167">为了放大到场景，请在层次结构中双击父定位点，并调整视图以查看所需的整个场景。</span><span class="sxs-lookup"><span data-stu-id="7316b-167">In order to zoom in to the scene, double-click the parent anchor in the hierarchy and adjust your view to see the entire scene as needed.</span></span> <span data-ttu-id="7316b-168">目前，ParentAnchor 是一个仅用于演示的彩色多维数据集。</span><span class="sxs-lookup"><span data-stu-id="7316b-168">Currently, ParentAnchor is a colored cube used only for demonstration purposes.</span></span> <span data-ttu-id="7316b-169">最终，我们将隐藏该多维数据集，并将内容作为 ParentAnchor 的子元素。</span><span class="sxs-lookup"><span data-stu-id="7316b-169">Eventually, we will hide the cube and place our content as a child of the ParentAnchor.</span></span> 

11. <span data-ttu-id="7316b-170">现在，让我们配置用于操作场景的按钮。</span><span class="sxs-lookup"><span data-stu-id="7316b-170">Now let's configure the buttons for operating the scene.</span></span> <span data-ttu-id="7316b-171">为此，请展开 "ButtonParent" prefab，你会注意到一些带标签的按钮，这些按钮是从 MRTK 的 PressableButton prototyping 创建的。</span><span class="sxs-lookup"><span data-stu-id="7316b-171">For that, expand the ButtonParent prefab and you'll notice several labeled buttons, which are created from the MRTK's PressableButton prefabs.</span></span> <span data-ttu-id="7316b-172">了解有关如何从[基本模块](mrlearning-base-ch2.md)创建 PressableButton 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7316b-172">Learn more about how to create PressableButton from the [Base module](mrlearning-base-ch2.md).</span></span> <span data-ttu-id="7316b-173">若要运行这些按钮，需要添加一个事件，当用户按下或选择各个按钮时，将触发该事件。</span><span class="sxs-lookup"><span data-stu-id="7316b-173">For these buttons to operate, you need to add an event which will be triggered when the user presses or selects the individual buttons.</span></span> 

- <span data-ttu-id="7316b-174">对于名为 StartAzureSession 的按钮，在 "按下" 事件触发器下创建一个新事件，并在 "单击" 事件触发器下创建一个新事件。</span><span class="sxs-lookup"><span data-stu-id="7316b-174">For the Button named StartAzureSession, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="7316b-175">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 StartAzureSession （）方法，如以下屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="7316b-175">Drag the ParentAnchor object into the empty field and assign the StartAzureSession() method from the ParentAnchor object's ASAmoduleScript component as shown in the below screenshot.</span></span>
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- <span data-ttu-id="7316b-179">对于名为 StopAzureSession 的按钮，在 "按下" 事件触发器下创建一个新事件，并在 "单击" 事件触发器下创建一个新事件。</span><span class="sxs-lookup"><span data-stu-id="7316b-179">For the Button named StopAzureSession, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="7316b-180">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 StopAzureSession （）方法。</span><span class="sxs-lookup"><span data-stu-id="7316b-180">Drag the ParentAnchor object into the empty field and assign the StopAzureSession() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="7316b-181">对于名为 CreateAnchor 的按钮，在 "按下" 事件触发器下创建一个新事件，并在 "单击" 事件触发器下创建一个新事件。</span><span class="sxs-lookup"><span data-stu-id="7316b-181">For the Button named CreateAnchor, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="7316b-182">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 CreateAzureAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="7316b-182">Drag the ParentAnchor object into the empty field and assign the CreateAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>  <span data-ttu-id="7316b-183">**然后，将 ParentAnchor 再次拖动到下一个空的 "游戏对象" 字段中。**</span><span class="sxs-lookup"><span data-stu-id="7316b-183">**After this, drag the ParentAnchor again into the next empty "Game Object" field.**</span></span>

- <span data-ttu-id="7316b-184">对于名为 "开始查找定位点" 的按钮，请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。</span><span class="sxs-lookup"><span data-stu-id="7316b-184">For the Button named Start Looking For Anchor, create a new event under the Button Press" event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="7316b-185">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 FindAzureAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="7316b-185">Drag the ParentAnchor object into the empty field and assign the FindAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

- <span data-ttu-id="7316b-186">对于名为 DeleteAzureAnchor 的按钮，在 "按下" 事件触发器下创建一个新事件，并在 "单击" 事件触发器下创建一个新事件。</span><span class="sxs-lookup"><span data-stu-id="7316b-186">For the Button named DeleteAzureAnchor, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="7316b-187">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 DeleteAzureAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="7316b-187">Drag the ParentAnchor object into the empty field and assign the DeleteAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>  

- <span data-ttu-id="7316b-188">对于名为 "删除本地定位点" 的按钮，请在 "按下" 事件触发器下创建新事件，并在 "单击" 事件触发器下创建一个新事件。</span><span class="sxs-lookup"><span data-stu-id="7316b-188">For the Button named Delete Local Anchor, create a new event under the Button Pressed event trigger, as well as the On Click event trigger.</span></span> <span data-ttu-id="7316b-189">将 ParentAnchor 对象拖到空字段，然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 RemoveLocalAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="7316b-189">Drag the ParentAnchor object into the empty field and assign the RemoveLocalAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span> <span data-ttu-id="7316b-190">**然后，将 ParentAnchor 对象再次拖动到下一个空 "游戏对象" 字段中。**</span><span class="sxs-lookup"><span data-stu-id="7316b-190">**After this, drag the ParentAnchor object again into the next empty "Game Object" field.**</span></span>

12. <span data-ttu-id="7316b-191">若要设置 Azure 空间锚，请转到 "资产" 文件夹中的 AzureSpatialAnchorsPlugin 文件夹，并导航到 "示例-> 资源-> AzureSpatialAnchorsDemoConfig 文件"。</span><span class="sxs-lookup"><span data-stu-id="7316b-191">To set up Azure spatial anchors, go to the AzureSpatialAnchorsPlugin folder in the assets folder and navigate to Examples -> Resources->AzureSpatialAnchorsDemoConfig file.</span></span> <span data-ttu-id="7316b-192">在 "检查器" 面板中，添加之前创建的 Azure 帐户 ID 和帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="7316b-192">In the inspector panel, add the Azure Account ID and Account Key that you created earlier.</span></span> <span data-ttu-id="7316b-193">如果尚未创建它们，请遵循[先决条件](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens)。</span><span class="sxs-lookup"><span data-stu-id="7316b-193">If you haven't created them or don't have the them, please follow the [Prerequisites](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span></span> 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a><span data-ttu-id="7316b-195">构建并演示基本应用程序</span><span class="sxs-lookup"><span data-stu-id="7316b-195">Build and demonstrate Base Application</span></span>

<span data-ttu-id="7316b-196">现在，你的场景已配置为演示 Azure 空间锚的基本知识，我们将构建并演示 Azure 空间锚的基本行为。</span><span class="sxs-lookup"><span data-stu-id="7316b-196">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, we will build and demonstrate the basic behavior of Azure Spatial Anchors.</span></span> 

1. <span data-ttu-id="7316b-197">转到 "文件 > 生成设置"，再次打开 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="7316b-197">Open the build settings window again, by going to File>Build Settings.</span></span>
    <span data-ttu-id="7316b-198">![mrlearning-ch1-3-步骤 1](images/mrlearning-asa-ch1-3-step1.jpg)</span><span class="sxs-lookup"><span data-stu-id="7316b-198">![mrlearning-asa-ch1-3-step1](images/mrlearning-asa-ch1-3-step1.jpg)</span></span>
2. <span data-ttu-id="7316b-199">单击 "添加打开的场景" 按钮，确保你想要尝试的场景处于 "生成" 列表中的场景中。</span><span class="sxs-lookup"><span data-stu-id="7316b-199">Ensure the scene you want to try is in the Scenes in the build list, by clicking on the Add Open Scenes button.</span></span>
3. <span data-ttu-id="7316b-200">验证平台是否设置为通用 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="7316b-200">Verify the Platform is set to the Universal Windows Platform.</span></span> <span data-ttu-id="7316b-201">否则，请将其设置为相同的。</span><span class="sxs-lookup"><span data-stu-id="7316b-201">If not, please set it to the same.</span></span>
4. <span data-ttu-id="7316b-202">按 "播放机设置" 按钮，并单击 "发布设置"。</span><span class="sxs-lookup"><span data-stu-id="7316b-202">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="7316b-203">在 "功能" 下，启用： Internet、Internet 客户端服务器、专用网络客户端服务器、可移动存储、网络摄像机、麦克风和空间感知。</span><span class="sxs-lookup"><span data-stu-id="7316b-203">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Removable Storage, Webcam, Microphone and Spatial Perception.</span></span>
5. <span data-ttu-id="7316b-204">在相同的播放机设置中，选择 "XR 设置"，并选择 "支持的虚拟现实"。</span><span class="sxs-lookup"><span data-stu-id="7316b-204">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>
6. <span data-ttu-id="7316b-205">按“生成”按钮开始生成过程。</span><span class="sxs-lookup"><span data-stu-id="7316b-205">Press the Build button to begin the build process.</span></span>
   <span data-ttu-id="7316b-206">![mrlearning-ch1-3-步骤 6](images/mrlearning-asa-ch1-3-step6.jpg)</span><span class="sxs-lookup"><span data-stu-id="7316b-206">![mrlearning-asa-ch1-3-step6](images/mrlearning-asa-ch1-3-step6.jpg)</span></span>
7. <span data-ttu-id="7316b-207">为应用程序创建一个新文件夹并为其命名。</span><span class="sxs-lookup"><span data-stu-id="7316b-207">Create and name a new folder for your application.</span></span> <span data-ttu-id="7316b-208">在下图中，创建了一个包含应用程序的名称为 "应用程序" 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7316b-208">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="7316b-209">单击 "选择文件夹"，开始生成到新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7316b-209">Click Select Folder to begin building to the newly created folder.</span></span> <span data-ttu-id="7316b-210">完成生成后，可以关闭 Unity 中的 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="7316b-210">After the build has completed, you may close the Build Setting" window in Unity.</span></span>

    ![mrlearning-ch1-step7](images/mrlearning-asa-ch1-3-step7.jpg)

    > <span data-ttu-id="7316b-212">注意：如果生成失败，请尝试重新生成或重新启动 Unity 并再次生成。</span><span class="sxs-lookup"><span data-stu-id="7316b-212">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="7316b-213">如果看到错误，如 "错误： CS0246 = 类型或命名空间名称" XX "（是否缺少 using 指令或程序集引用？），则可能需要安装[Windows 10 SDK （10.0.18362.0）](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="7316b-213">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?), you might need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span> 


8. <span data-ttu-id="7316b-214">即使在成功生成后，你可能会收到如下所示的错误，但如果生成成功，则可以忽略这些错误并继续执行后续步骤。</span><span class="sxs-lookup"><span data-stu-id="7316b-214">Even after a successful build, you might get some errors as shown below, but if the build is successful you can ignore them and proceed with next steps.</span></span>

    ![mrlearning-ch1-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. <span data-ttu-id="7316b-216">生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7316b-216">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="7316b-217">如果你在 Visual Studio 中打开解决方案文件，请双击 "MixedRealityBase" 解决方案或相应的名称（如果你使用的是项目的替代名称）。</span><span class="sxs-lookup"><span data-stu-id="7316b-217">Double-click on the“MixedRealityBase.sln" solution or the corresponding name, if you used an alternative name for your project to open the solution file in Visual Studio.</span></span>

    > <span data-ttu-id="7316b-218">注意：如果遵循前面步骤中的命名约定，请确保打开新创建的文件夹（即 App 文件夹），因为在该文件夹之外，不会与 build 文件夹内的 .sln 文件混淆，这一点类似。</span><span class="sxs-lookup"><span data-stu-id="7316b-218">Note: Be sure to open the newly created folder (i.e., the App folder, if following the naming conventions from the previous steps, as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span>

    ![mrlearning-ch1-step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > <span data-ttu-id="7316b-220">注意：如果 Visual Studio 要求安装新组件，请确保所有必备组件都按照["安装工具" 页中的](install-the-tools.md)特定方式安装</span><span class="sxs-lookup"><span data-stu-id="7316b-220">Note: If Visual Studio asks to install new components, ensure that all prerequisite components are installed as specific in [the "Install the Tools" page](install-the-tools.md)</span></span>


9. <span data-ttu-id="7316b-221">使用 USB 电缆将 HoloLens 2 插入电脑。</span><span class="sxs-lookup"><span data-stu-id="7316b-221">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="7316b-222">虽然这些课程说明假设你要使用 HoloLens 2 设备部署测试，但你也可以选择将部署到[hololens 2 模拟器](using-the-hololens-emulator.md)，或选择创建[用于旁加载的应用程序包](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="7316b-222">While these Lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

10. <span data-ttu-id="7316b-223">在生成到设备之前，请确保它处于开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="7316b-223">Before building to your device, ensure that it is in Developer Mode.</span></span> <span data-ttu-id="7316b-224">如果这是你首次部署到 HoloLens 2，则 Visual Studio 可能会要求你将 HoloLens 2 与 PIN 配对。</span><span class="sxs-lookup"><span data-stu-id="7316b-224">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a PIN.</span></span> <span data-ttu-id="7316b-225">如果需要使用 Visual Studio 启用开发人员模式或配对，请遵循[这些说明](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="7316b-225">Follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

11. <span data-ttu-id="7316b-226">将 Visual Studio 配置为通过选择 "发布" 配置和 ARM 体系结构生成到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="7316b-226">Configure Visual Studio for building to your HoloLens 2, by selecting the Release configuration as well as the ARM architecture.</span></span>

    ![mrlearning-ch1-step11](images/mrlearning-asa-ch1-3-step11.jpg)


12. <span data-ttu-id="7316b-228">最后一步是通过选择“调试”>“在不调试的情况下启动”来生成到你的设备。</span><span class="sxs-lookup"><span data-stu-id="7316b-228">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="7316b-229">选择 "启动但不调试" 会导致应用程序在成功生成时立即在设备上启动，而不会在 Visual Studio 中显示调试信息。</span><span class="sxs-lookup"><span data-stu-id="7316b-229">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="7316b-230">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="7316b-230">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="7316b-231">你还可以选择 "生成" > 部署解决方案以部署到设备，而无需应用程序自动启动。</span><span class="sxs-lookup"><span data-stu-id="7316b-231">You might also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

    ![mrlearning-ch1-step12](images/mrlearning-asa-ch1-3-step12.jpg)

><span data-ttu-id="7316b-233">注意： Azure 空间锚点使用 internet 保存和加载定位点数据，因此，在测试 ASA 应用之前，请确保你的设备已连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="7316b-233">Note: The Azure spatial anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet before testing the ASA app.</span></span>

13. <span data-ttu-id="7316b-234">按照说明操作。</span><span class="sxs-lookup"><span data-stu-id="7316b-234">Follow the instructions.</span></span> 
    <span data-ttu-id="7316b-235">当应用程序在你的设备上运行时，请按照屏幕上的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7316b-235">When the application is running on your device, follow the on-screen instructions.</span></span> <span data-ttu-id="7316b-236">按以下步骤对应的场景按钮。</span><span class="sxs-lookup"><span data-stu-id="7316b-236">Press the Scene buttons corresponding to the Steps below.</span></span> <span data-ttu-id="7316b-237">如果按照前面的步骤中所述添加了 "调试" 窗口，则可以查看单个按钮按下的反馈以及与 Azure 空间定位点相关的各个操作的进度。</span><span class="sxs-lookup"><span data-stu-id="7316b-237">If you added the debug window as mentioned in the previous steps, you can see the feedback for individual button press and the progress of individual operations related to Azure spatial anchors.</span></span>

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. <span data-ttu-id="7316b-239">启动空间锚点会话。</span><span class="sxs-lookup"><span data-stu-id="7316b-239">Start the spatial anchors session.</span></span>
    
    2. <span data-ttu-id="7316b-240">将多维数据集移到其他位置。</span><span class="sxs-lookup"><span data-stu-id="7316b-240">Move the cube to a different location.</span></span>
    
    3. <span data-ttu-id="7316b-241">将 Azure 空间锚点保存在多维数据集的位置。</span><span class="sxs-lookup"><span data-stu-id="7316b-241">Save the Azure spatial anchors at the location of the cube.</span></span>
    
    4. <span data-ttu-id="7316b-242">停止 Azure 空间锚点会话。</span><span class="sxs-lookup"><span data-stu-id="7316b-242">Stop the Azure spatial anchors session.</span></span>
    
    5. <span data-ttu-id="7316b-243">删除多维数据集上的本地定位点，以允许用户移动多维数据集。</span><span class="sxs-lookup"><span data-stu-id="7316b-243">Remove the local anchor on the cube to allow the user to move the cube.</span></span>
    
    6. <span data-ttu-id="7316b-244">将多维数据集移到其他位置。</span><span class="sxs-lookup"><span data-stu-id="7316b-244">Move the cube somewhere else.</span></span>
    
    7. <span data-ttu-id="7316b-245">启动 Azure 空间锚点会话。</span><span class="sxs-lookup"><span data-stu-id="7316b-245">Start Azure spatial anchors session.</span></span>
    
    8. <span data-ttu-id="7316b-246">查找 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="7316b-246">Find Azure Spatial Anchors.</span></span> 
    <span data-ttu-id="7316b-247">你应返回到创建定位点时将其放入的原位置。</span><span class="sxs-lookup"><span data-stu-id="7316b-247">You should go back to the original place you put it when you created the anchor.</span></span>
    
    9. <span data-ttu-id="7316b-248">删除 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="7316b-248">Delete Azure spatial anchor.</span></span>
    
    10. <span data-ttu-id="7316b-249">停止 Azure 会话。</span><span class="sxs-lookup"><span data-stu-id="7316b-249">Stop Azure session.</span></span>

### <a name="anchoring-an-experience"></a><span data-ttu-id="7316b-250">定位体验</span><span class="sxs-lookup"><span data-stu-id="7316b-250">Anchoring an experience</span></span>

<span data-ttu-id="7316b-251">在前面的部分中，已了解 Azure 空间锚的基础知识。</span><span class="sxs-lookup"><span data-stu-id="7316b-251">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="7316b-252">我们已使用多维数据集来表示父游戏对象并将其可视化。</span><span class="sxs-lookup"><span data-stu-id="7316b-252">We've used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="7316b-253">在本部分中，你将了解如何通过将整个体验作为 ParentAnchor 对象的子项来定位。</span><span class="sxs-lookup"><span data-stu-id="7316b-253">In this section, you'll learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span> <span data-ttu-id="7316b-254">在此示例中，我们使用在[基础模块第6课](mrlearning-base-ch6.md)中创建的农历模块程序集演示应用程序。</span><span class="sxs-lookup"><span data-stu-id="7316b-254">For this example, we use the lunar module Assembly demonstration application that was created during [Base module Lesson 6](mrlearning-base-ch6.md).</span></span>

1. <span data-ttu-id="7316b-255">搜索 "火箭启动器 Complete" prefab，并将其作为对象的子级拖到层次结构中（请参阅下图）。</span><span class="sxs-lookup"><span data-stu-id="7316b-255">Search for the "Rocket Launcher Complete" prefab and drag it into your hierarchy as a child of the object (see the image below).</span></span>

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. <span data-ttu-id="7316b-257">定位模块程序集体验，以使多维数据集仍公开，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="7316b-257">Position the module assembly experience so that the cube is still exposed, as shown in the image below.</span></span> <span data-ttu-id="7316b-258">在应用程序中，用户可以通过移动多维数据集来重新定位整个体验。</span><span class="sxs-lookup"><span data-stu-id="7316b-258">In the application, users may reposition the entire experience by moving the cube.</span></span> 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> <span data-ttu-id="7316b-260">注意：有各种用户体验流程可用于重定位体验，包括使用按钮切换环绕体验的边界框、使用重定位对象（如此步骤中使用的多维数据集）、位置和旋转gizmos 等。</span><span class="sxs-lookup"><span data-stu-id="7316b-260">Note: There are a variety of user experience flows for repositioning experiences, including the use of a button to toggle a bounding box that surrounds the experience, use of a repositioning object (such as the cube used in this step), the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7316b-261">祝贺</span><span class="sxs-lookup"><span data-stu-id="7316b-261">Congratulations</span></span>
<span data-ttu-id="7316b-262">在本教程中，已了解 Azure 空间锚的基础知识。</span><span class="sxs-lookup"><span data-stu-id="7316b-262">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="7316b-263">本课程提供多个按钮，使你可以浏览启动和停止 Azure 会话所需的各种步骤，以及在单个设备上创建、上传和下载 azure 锚。</span><span class="sxs-lookup"><span data-stu-id="7316b-263">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span> <span data-ttu-id="7316b-264">在下一课中，您将学习如何将 Azure 定位 Id 保存到 HoloLens 2 以便检索，甚至在应用程序重新启动后也是如此。</span><span class="sxs-lookup"><span data-stu-id="7316b-264">In the next lesson, you'll learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted.</span></span> <span data-ttu-id="7316b-265">在本系列文章中，你还将了解如何在多个设备之间传输定位点 Id 以实现空间对齐，并了解有关多用户共享会话的信息，如共享教程中所述。</span><span class="sxs-lookup"><span data-stu-id="7316b-265">During the series, you will also learn how to transfer anchor IDs between multiple devices to achieve spatial alignment and learn about multi-user shared sessions, forthcoming as part of the Sharing tutorial.</span></span>

[<span data-ttu-id="7316b-266">下一课： 2. 保存、检索和共享 Azure 空间锚</span><span class="sxs-lookup"><span data-stu-id="7316b-266">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

