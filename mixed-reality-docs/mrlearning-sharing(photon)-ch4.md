---
title: 多用户功能教程 - 4. 与多个用户共享对象运动
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031250"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="13b54-105">4.与多个用户共享对象运动</span><span class="sxs-lookup"><span data-stu-id="13b54-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="13b54-106">本教程介绍如何共享对象的运动，使共享会话的所有参与者可以展开协作并查看彼此的交互。</span><span class="sxs-lookup"><span data-stu-id="13b54-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="13b54-107">本课程基于[基础模块教程](mrlearning-base.md)中生成的月球探测器发射器。</span><span class="sxs-lookup"><span data-stu-id="13b54-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="13b54-108">目标</span><span class="sxs-lookup"><span data-stu-id="13b54-108">Objectives</span></span>

- <span data-ttu-id="13b54-109">以 3D 模型的形式引入要共享的月球探测器发射器</span><span class="sxs-lookup"><span data-stu-id="13b54-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="13b54-110">将项目配置为共享 3D 模型的运动</span><span class="sxs-lookup"><span data-stu-id="13b54-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="13b54-111">了解如何生成基本的多用户协作应用程序</span><span class="sxs-lookup"><span data-stu-id="13b54-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="13b54-112">说明</span><span class="sxs-lookup"><span data-stu-id="13b54-112">Instructions</span></span>

1. <span data-ttu-id="13b54-113">保存上一课程中创建的场景 (Ctrl+S)。</span><span class="sxs-lookup"><span data-stu-id="13b54-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="13b54-114">可将其命名为 HLSharedProjectMainPart4.unity，以便在需要时轻松找到它。</span><span class="sxs-lookup"><span data-stu-id="13b54-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="13b54-115">在“项目”窗口中，双击“资产”->“脚本”文件夹中的“GenericNetSync”，在 Visual Studio 或所用的其他代码编辑器中将其打开。</span><span class="sxs-lookup"><span data-stu-id="13b54-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="13b54-117">在第 34 和 38 行中，删除“//”以激活要在本课程中使用的工作台的代码。</span><span class="sxs-lookup"><span data-stu-id="13b54-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="13b54-118">接下来保存该文件。</span><span class="sxs-lookup"><span data-stu-id="13b54-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="13b54-120">在“项目”窗口中，双击“资产”>“脚本”文件夹中的“PhotonRoom.cs”文件，在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="13b54-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="13b54-122">与在步骤 3 中一样，需要删除“//”以激活第 25、26 和 106 行中的代码。</span><span class="sxs-lookup"><span data-stu-id="13b54-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="13b54-125">在“层次结构”视图中选择“NetworkRoom”对象。</span><span class="sxs-lookup"><span data-stu-id="13b54-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="13b54-127">在“项目”视图中，导航到“资产”->“资源”->“预制件”。</span><span class="sxs-lookup"><span data-stu-id="13b54-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="13b54-128">首先，将 Table 预制件拖放到 PhotonRoom 类中的 Tableprefab 槽。</span><span class="sxs-lookup"><span data-stu-id="13b54-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="13b54-129">接下来，将 RocketLauncherCompleteVariantprefab 拖放到 PhotonRoom 类中的 Module Prefab 槽。</span><span class="sxs-lookup"><span data-stu-id="13b54-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="13b54-131">如果单击某个预制件对象并松开鼠标，检查器将切换到该对象。</span><span class="sxs-lookup"><span data-stu-id="13b54-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="13b54-132">单击每个对象并将其拖放到相应的槽，然后松开鼠标。</span><span class="sxs-lookup"><span data-stu-id="13b54-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="13b54-133">单击 MixedRealityPlayspace 左侧的箭头，并将子游戏对象 MainCamera 下移到 SharedPlayground 预制件。</span><span class="sxs-lookup"><span data-stu-id="13b54-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="13b54-134">接下来，选择 MixedRealityPlayspace 预制件，然后按 Delete 键将其删除。</span><span class="sxs-lookup"><span data-stu-id="13b54-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="13b54-136">确保主相机和 SharedPlayground 位置均设置为 0,0,0。</span><span class="sxs-lookup"><span data-stu-id="13b54-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="13b54-137">选择“SharedPlayground”对象，然后单击鼠标右键并选择“创建空对象”选项，以创建一个空游戏对象作为“SharedPlayground”游戏对象的子级。</span><span class="sxs-lookup"><span data-stu-id="13b54-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="13b54-139">在层次结构中选择该新对象后，在“检查器”面板中将该对象的名称更改为 TableAnchor。</span><span class="sxs-lookup"><span data-stu-id="13b54-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="13b54-140">另外，单击“添加组件”并搜索 TableAnchor 组件。</span><span class="sxs-lookup"><span data-stu-id="13b54-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="13b54-141">选择该组件并将其添加到对象。</span><span class="sxs-lookup"><span data-stu-id="13b54-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="13b54-143">在“项目”面板中的“预制件”文件夹内，将 Table 预制件拖放到刚刚创建的“TableAnchor”子对象中。</span><span class="sxs-lookup"><span data-stu-id="13b54-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a><span data-ttu-id="13b54-145">祝贺</span><span class="sxs-lookup"><span data-stu-id="13b54-145">Congratulations</span></span>

<span data-ttu-id="13b54-146">完成此过程后，找到登月舱。</span><span class="sxs-lookup"><span data-stu-id="13b54-146">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="13b54-147">此时，参与 Unity 项目的所有用户都可以四处移动月球探测器发射器。</span><span class="sxs-lookup"><span data-stu-id="13b54-147">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="13b54-148">所有运动都是同步的，因此每个用户都可以看到彼此的交互。</span><span class="sxs-lookup"><span data-stu-id="13b54-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="13b54-149">这些概念是全功能共享协作体验的构建基块。</span><span class="sxs-lookup"><span data-stu-id="13b54-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="13b54-150">尽管所有用户已作为共享体验的一部分进行连接，并且可以看到对象的相对运动，但应用程序仍然无法准确对齐头像和对象，因此本地用户无法在现实世界中的同一位置看到彼此和对象。</span><span class="sxs-lookup"><span data-stu-id="13b54-150">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="13b54-151">若要定位点定本地共享体验，每个设备都需要对物理环境有一个共识。</span><span class="sxs-lookup"><span data-stu-id="13b54-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="13b54-152">在本模块中，我们将使用下一课程中要实现的 [Azure 空间定位点](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) 来达到这种共识。</span><span class="sxs-lookup"><span data-stu-id="13b54-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="13b54-153">在继续学习下一课程之前，需要先完成 ASA 学习模块，其中介绍了 ASA 基础知识、Azure 帐户和资源的创建，以及在可将此模块集成到共享体验之前所需的其他构建基块。</span><span class="sxs-lookup"><span data-stu-id="13b54-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="13b54-154">[下一课：5.将 Azure 空间定位点集成到共享体验中](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="13b54-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
