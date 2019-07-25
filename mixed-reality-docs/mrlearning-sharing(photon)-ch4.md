---
title: HoloLens 2 的 MR 教育共享模块
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 529a888dfa00180ca908fbc7f4c62f9a9086c661
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460321"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="a1045-104">4.与多个用户共享对象移动</span><span class="sxs-lookup"><span data-stu-id="a1045-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="a1045-105">在本教程中, 我们将了解如何共享对象的移动, 以便共享会话的所有参与者都可以协同协作并彼此查看交互。</span><span class="sxs-lookup"><span data-stu-id="a1045-105">In this Tutorial, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="a1045-106">本课基于[基本模块教程](mrlearning-base.md)中构建的农历启动器构建。</span><span class="sxs-lookup"><span data-stu-id="a1045-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="a1045-107">目标</span><span class="sxs-lookup"><span data-stu-id="a1045-107">Objectives:</span></span>

- <span data-ttu-id="a1045-108">将农历启动器作为要共享的3D 模型</span><span class="sxs-lookup"><span data-stu-id="a1045-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="a1045-109">将项目配置为共享三维模型的变动。</span><span class="sxs-lookup"><span data-stu-id="a1045-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="a1045-110">了解如何构建基本的多用户协作应用程序</span><span class="sxs-lookup"><span data-stu-id="a1045-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="a1045-111">说明</span><span class="sxs-lookup"><span data-stu-id="a1045-111">Instructions</span></span>


1. <span data-ttu-id="a1045-112">从上一课 (Ctrl + S) 保存场景。</span><span class="sxs-lookup"><span data-stu-id="a1045-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="a1045-113">可以将其命名为 HLSharedProjectMainPart4, 以便在需要时更轻松地找到它。</span><span class="sxs-lookup"><span data-stu-id="a1045-113">You can name it, HLSharedProjectMainPart4.unity, so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="a1045-114">在 "项目" 窗口的 "资产-> 脚本" 文件夹中, 双击 GenericNetSync 以在 Visual Studio 中打开它, 或使用的代码编辑器。</span><span class="sxs-lookup"><span data-stu-id="a1045-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="a1045-116">在34行和38行上, 删除//以激活将在本课中使用的表的代码。</span><span class="sxs-lookup"><span data-stu-id="a1045-116">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="a1045-117">接下来, 保存该文件。</span><span class="sxs-lookup"><span data-stu-id="a1045-117">next, Save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="a1045-119">在 "项目" 窗口中, 双击 "资产 > 脚本" 文件夹中的 PhotonRoom.cs 文件, 在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="a1045-119">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="a1045-121">如步骤3中所示, 我们需要删除//以在第25行、第26行和第106行激活代码。</span><span class="sxs-lookup"><span data-stu-id="a1045-121">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="a1045-124">在层次结构视图中, 选择 "NetworkRoom" 对象。</span><span class="sxs-lookup"><span data-stu-id="a1045-124">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="a1045-126">在 "项目" 视图中, 导航到 "资产-> 资源-> Prototyping"。</span><span class="sxs-lookup"><span data-stu-id="a1045-126">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="a1045-127">首先, 将表 prefab 拖放到 PhotonRoom 类中的 Tableprefab 槽。</span><span class="sxs-lookup"><span data-stu-id="a1045-127">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="a1045-128">接下来, 将 RocketLauncherCompleteVariantprefab 拖放到 PhotonRoom 类中的模块 Prefab 槽。</span><span class="sxs-lookup"><span data-stu-id="a1045-128">Next drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   <span data-ttu-id="a1045-130">注意:如果单击其中一个 prefab 对象并发布, 检查器将切换到该对象。</span><span class="sxs-lookup"><span data-stu-id="a1045-130">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="a1045-131">单击、拖放, 然后将每个对象发布到相应的槽。</span><span class="sxs-lookup"><span data-stu-id="a1045-131">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="a1045-132">单击 "MixedRealityPlayspace" 左侧的箭头, 将子游戏对象移到 "SharedPlayground prefab" 中。</span><span class="sxs-lookup"><span data-stu-id="a1045-132">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="a1045-133">接下来, 删除要删除的 prefab, MixedRealityPlayspace, 选择 prefab, 然后点击键盘上的 "删除"。</span><span class="sxs-lookup"><span data-stu-id="a1045-133">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="a1045-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="a1045-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="a1045-135">注意:请确保摄像机和 SharedPlayground 位置均设置为0、0和0。</span><span class="sxs-lookup"><span data-stu-id="a1045-135">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="a1045-136">创建新的游戏对象, 并将其设置为 SharedPlayground 父对象的子对象, 以创建新的对象。</span><span class="sxs-lookup"><span data-stu-id="a1045-136">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="a1045-137">右键单击父对象, 然后选择 "创建空"。</span><span class="sxs-lookup"><span data-stu-id="a1045-137">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="a1045-138">在层次结构中选择新对象后, 请在 "检查器" 面板中将对象的名称更改为 TableAnchor。</span><span class="sxs-lookup"><span data-stu-id="a1045-138">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="a1045-139">另外, 单击 "添加组件", 然后搜索 "TableAnchor" 组件。</span><span class="sxs-lookup"><span data-stu-id="a1045-139">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="a1045-140">选择它并将其添加到对象。</span><span class="sxs-lookup"><span data-stu-id="a1045-140">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="a1045-142">现在, 在 Prototyping 文件夹中的 "项目" 面板中, 将 "prefab" 表拖入刚刚创建的 "TableAnchor" 子对象。</span><span class="sxs-lookup"><span data-stu-id="a1045-142">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="a1045-144">最后, 在 DebugWindow 对象中, 将 width 改为 50, 将其高度更改为20。</span><span class="sxs-lookup"><span data-stu-id="a1045-144">Finally, in the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="a1045-146">祝贺</span><span class="sxs-lookup"><span data-stu-id="a1045-146">Congratulations</span></span>


<span data-ttu-id="a1045-147">完成此工作后, 加入 Unity 项目的所有用户都可以绕过阴历启动器。</span><span class="sxs-lookup"><span data-stu-id="a1045-147">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="a1045-148">所有移动都将同步, 以便每个用户都可以看到彼此的交互。</span><span class="sxs-lookup"><span data-stu-id="a1045-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="a1045-149">这些概念用作功能齐全的共享协作体验的基本构建基块。</span><span class="sxs-lookup"><span data-stu-id="a1045-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="a1045-150">尽管所有用户都作为共享体验的一部分进行连接, 并且可以看到对象的相对运动, 但是应用程序仍然无法准确地调整头像和对象, 以便本地用户在物理world.</span><span class="sxs-lookup"><span data-stu-id="a1045-150">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="a1045-151">为了定位本地共享体验, 每个设备都需要对物理环境有一个共同的了解。</span><span class="sxs-lookup"><span data-stu-id="a1045-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="a1045-152">在此模块中, 我们将使用将在下一课中实施的[Azure 空间锚点](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA) 来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="a1045-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="a1045-153">在继续学习下一课之前, 我们需要先完成 ASA 学习模块, 其中包含 ASA 基础知识、Azure 帐户和资源创建, 以及在我们可以将其集成到我们的共享体验之前所需的其他基本建筑块。</span><span class="sxs-lookup"><span data-stu-id="a1045-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="a1045-154">[下一课：共享 (Photon) 第5课](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="a1045-154">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

