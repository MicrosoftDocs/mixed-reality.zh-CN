---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326656"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="f30f2-104">同步共享对象移动</span><span class="sxs-lookup"><span data-stu-id="f30f2-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="f30f2-105">在本课中，我们将了解如何共享对象的移动，以便共享会话的所有参与者都可以共同协作，并查看其他用户交互。</span><span class="sxs-lookup"><span data-stu-id="f30f2-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="f30f2-106">本课基于阴历作为的一部分而构建的启动器[基本模块教程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="f30f2-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="f30f2-107">目标：</span><span class="sxs-lookup"><span data-stu-id="f30f2-107">Objectives:</span></span>

- <span data-ttu-id="f30f2-108">作为要共享的三维模型导入已完成阴历启动器</span><span class="sxs-lookup"><span data-stu-id="f30f2-108">Import the completed Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="f30f2-109">将项目配置为共享的移动的三维模型。</span><span class="sxs-lookup"><span data-stu-id="f30f2-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="f30f2-110">了解如何生成基本的多用户协作应用程序</span><span class="sxs-lookup"><span data-stu-id="f30f2-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="f30f2-111">说明</span><span class="sxs-lookup"><span data-stu-id="f30f2-111">Instructions</span></span>

1. <span data-ttu-id="f30f2-112">从上一课 （控制 + S） 保存场景。</span><span class="sxs-lookup"><span data-stu-id="f30f2-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="f30f2-113">您可能它命名为"HLSharedProjectMainPart4.unity"以便更轻松地找到时再需要它。</span><span class="sxs-lookup"><span data-stu-id="f30f2-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="f30f2-114">删除"NetworkLobby"对象 （通过选择它并按 delete 键）。</span><span class="sxs-lookup"><span data-stu-id="f30f2-114">Delete the "NetworkLobby" object (by selecting it and pressing delete).</span></span> <span data-ttu-id="f30f2-115">此外，从第 2 课转到"预设"文件夹，然后从此处也删除"NetworkLobby"预设。</span><span class="sxs-lookup"><span data-stu-id="f30f2-115">Also, go into the "prefabs" folder from lesson 2 and delete the "NetworkLobby" prefab from there as well.</span></span>

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. <span data-ttu-id="f30f2-117">导入新的自定义包 （例如，从第 2 课的步骤 2） 和导入[LunarModule.unitypackage](linkforModule1 lesson with the lunar module)和[NetworkLobbyReplacement.unitypackage。](linkforNetworklobbyreplacement package here)</span><span class="sxs-lookup"><span data-stu-id="f30f2-117">Import a new custom package (like step 2 from the lesson 2) and import the [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) and the [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span></span>

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. <span data-ttu-id="f30f2-119">现在，在"预设"文件夹中，将新的"NetworkLobby"预设拖到层次结构。</span><span class="sxs-lookup"><span data-stu-id="f30f2-119">Now, in the "prefabs" folder, drag the new "NetworkLobby" prefab into the hierarchy .</span></span> 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> <span data-ttu-id="f30f2-121">注意： 我们在前面的步骤中导入的两个包更新"NetworkLobby"预设。</span><span class="sxs-lookup"><span data-stu-id="f30f2-121">note: the two packages we imported in the previous steps updated the "NetworkLobby" prefab.</span></span> <span data-ttu-id="f30f2-122">它使您许多键入内容 ！</span><span class="sxs-lookup"><span data-stu-id="f30f2-122">It saves you from a lot of typing!</span></span>

5. <span data-ttu-id="f30f2-123">现在，单击"MixedRealityPlayspace"左侧的箭头，并将子游戏对象"MainCamera"向下移动到"SharedPlayground"预设。</span><span class="sxs-lookup"><span data-stu-id="f30f2-123">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="f30f2-124">然后，删除 prefab"MixedRealityPlayspace"（若要删除，选择预设可在键盘上点击"删除"）。</span><span class="sxs-lookup"><span data-stu-id="f30f2-124">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. <span data-ttu-id="f30f2-126">创建新的游戏对象作为子对象设置为"SharedPlayground"父对象 （若要创建新的对象，父对象中，右键单击并选择"创建空"）。</span><span class="sxs-lookup"><span data-stu-id="f30f2-126">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span>
7. <span data-ttu-id="f30f2-127">与你的层次结构中选择的新对象，将对象的名称更改为"TableAnchor"检查器面板中。</span><span class="sxs-lookup"><span data-stu-id="f30f2-127">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="f30f2-128">此外，单击"添加组件"，搜索"TableAnchor"组件。</span><span class="sxs-lookup"><span data-stu-id="f30f2-128">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="f30f2-129">选择它并将其添加到该对象。</span><span class="sxs-lookup"><span data-stu-id="f30f2-129">Select it and add it to the object.</span></span>

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="f30f2-131">注意： 设置定位到 x = 1，y = 0.55 和 z = 2。</span><span class="sxs-lookup"><span data-stu-id="f30f2-131">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="f30f2-132">此外，将旋转设置为 y = 90。</span><span class="sxs-lookup"><span data-stu-id="f30f2-132">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. <span data-ttu-id="f30f2-134">现在在项目面板中，在"预设"文件夹中，将"表"预设到刚创建的"TableAnchor"子对象。</span><span class="sxs-lookup"><span data-stu-id="f30f2-134">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. <span data-ttu-id="f30f2-136">选择"NetworkRoom，""NetworkLobby"下的子对象，在层次结构，并单击"添加组件"，在检查器面板和"PhotonView"的搜索中，将脚本添加到"*NetworkRoom*"对象。</span><span class="sxs-lookup"><span data-stu-id="f30f2-136">Select "NetworkRoom," a child object under "NetworkLobby" in the hierachy, and click "add component" in the inspector panel and search for "PhotonView" and add the script to the "*NetworkRoom*" object.</span></span>

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. <span data-ttu-id="f30f2-138">最后，"DebugWindow"对象中更改为 80 和高度为 10 的宽度。</span><span class="sxs-lookup"><span data-stu-id="f30f2-138">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="f30f2-140">祝贺</span><span class="sxs-lookup"><span data-stu-id="f30f2-140">Congratulations</span></span>

<span data-ttu-id="f30f2-141">完成此操作，加入你的 Unity 项目的所有用户可以都移动阴历启动器。</span><span class="sxs-lookup"><span data-stu-id="f30f2-141">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="f30f2-142">所有移动都同步，以便每个用户可以看到其他用户交互。</span><span class="sxs-lookup"><span data-stu-id="f30f2-142">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="f30f2-143">这些概念充当用于全面共享的协作体验的基础构建块。</span><span class="sxs-lookup"><span data-stu-id="f30f2-143">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="f30f2-144">虽然所有用户连接的共享体验的一部分，并且所见的相对移动的对象，该应用程序是仍无法准确地对齐虚拟形象和对象，以便本地用户看到彼此，并在物理内的同一位置中的对象世界。</span><span class="sxs-lookup"><span data-stu-id="f30f2-144">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="f30f2-145">若要定位到本地共享的体验，每个设备需要物理环境的了解。</span><span class="sxs-lookup"><span data-stu-id="f30f2-145">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="f30f2-146">在此模块中，我们将使用实现此目的[Azure 空间的定位点](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，这将在下一课中实现。</span><span class="sxs-lookup"><span data-stu-id="f30f2-146">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="f30f2-147">在继续之前为下一课中，我们将需要完成 ASA 学习模块，将介绍 ASA 基础知识，需要 Azure 帐户和资源创建和其他基本建筑物块之前我们可以将此集成到我们的共享体验。</span><span class="sxs-lookup"><span data-stu-id="f30f2-147">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="f30f2-148">[下一课：第 5 课 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="f30f2-148">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

