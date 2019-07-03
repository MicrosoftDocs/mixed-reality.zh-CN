---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 2a4ea599fd4887f30589c2d839be305d3dc8d1bd
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523191"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="5eefc-104">4.与多个用户共享对象移动</span><span class="sxs-lookup"><span data-stu-id="5eefc-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="5eefc-105">在本教程中，我们将了解如何共享对象的移动，以便共享会话的所有参与者都可以共同协作，并查看其他用户交互。</span><span class="sxs-lookup"><span data-stu-id="5eefc-105">In this Tutorial, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="5eefc-106">本课基于阴历作为的一部分而构建的启动器[基本模块教程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="5eefc-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="5eefc-107">目标：</span><span class="sxs-lookup"><span data-stu-id="5eefc-107">Objectives:</span></span>

- <span data-ttu-id="5eefc-108">引入阴历启动器为三维模型来共享</span><span class="sxs-lookup"><span data-stu-id="5eefc-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="5eefc-109">将项目配置为共享的移动的三维模型。</span><span class="sxs-lookup"><span data-stu-id="5eefc-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="5eefc-110">了解如何生成基本的多用户协作应用程序</span><span class="sxs-lookup"><span data-stu-id="5eefc-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="5eefc-111">说明</span><span class="sxs-lookup"><span data-stu-id="5eefc-111">Instructions</span></span>


1. <span data-ttu-id="5eefc-112">从上一课 (控制 + S) 保存场景。</span><span class="sxs-lookup"><span data-stu-id="5eefc-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="5eefc-113">您可以将其命名，HLSharedProjectMainPart4.unity，以便更轻松地找到所需的时。</span><span class="sxs-lookup"><span data-stu-id="5eefc-113">You can name it, HLSharedProjectMainPart4.unity, so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="5eefc-114">从项目窗口中，在资产中-> 脚本文件夹，双击 GenericNetSync 在 Visual Studio 或其曾经代码正在使用的编辑器中打开它。</span><span class="sxs-lookup"><span data-stu-id="5eefc-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="5eefc-115">在行 34 和 38，删除 / / 若要激活的表，我们将在本课程中使用的代码。</span><span class="sxs-lookup"><span data-stu-id="5eefc-115">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="5eefc-116">接下来，将该文件。</span><span class="sxs-lookup"><span data-stu-id="5eefc-116">next, Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="5eefc-117">在项目窗口中，双击 PhotonRoom.cs 文件的资产中-> 若要在 Visual Studio 中打开脚本文件夹。</span><span class="sxs-lookup"><span data-stu-id="5eefc-117">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="5eefc-118">就像在步骤 3 中，我们需要删除 / / 若要激活的 25、 26，以及 106 行处的代码。![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="5eefc-118">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="5eefc-119">在层次结构视图中，选择 NetworkRoom 对象。![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="5eefc-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="5eefc-120">在项目视图中，导航到资产-> 资源-> 预设。</span><span class="sxs-lookup"><span data-stu-id="5eefc-120">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="5eefc-121">首先，拖放表预设到 Tableprefab 槽 PhotonRoom 类上。</span><span class="sxs-lookup"><span data-stu-id="5eefc-121">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="5eefc-122">接下来拖放 LunarModule 预设到 PhotonRoom 类上的模块 Prefab 槽。</span><span class="sxs-lookup"><span data-stu-id="5eefc-122">Next drag and drop the LunarModule prefab to the Module Prefab slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="5eefc-123">注意：如果单击其中一个 prefab 对象和版本上，该检查器将切换到该对象。</span><span class="sxs-lookup"><span data-stu-id="5eefc-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="5eefc-124">单击、 拖动、 删除和发布到其相应的槽的每个对象。</span><span class="sxs-lookup"><span data-stu-id="5eefc-124">Click, drag, drop, and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="5eefc-125">单击左侧的 MixedRealityPlayspace，箭头并将子游戏对象，MainCamera 向下移动到 SharedPlayground 预设。</span><span class="sxs-lookup"><span data-stu-id="5eefc-125">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="5eefc-126">接下来，删除预设可 MixedRealityPlayspace，删除、 选择预设，并在键盘上点击"删除"）。</span><span class="sxs-lookup"><span data-stu-id="5eefc-126">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="5eefc-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="5eefc-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

<span data-ttu-id="5eefc-128">注意：请确保主相机和 SharedPlayground 位置将设置为 0,0,0。</span><span class="sxs-lookup"><span data-stu-id="5eefc-128">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="5eefc-129">创建新的游戏对象设置为子对象为 SharedPlayground 父对象以创建一个新的对象。</span><span class="sxs-lookup"><span data-stu-id="5eefc-129">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="5eefc-130">父对象中，右键单击并选择创建空白。</span><span class="sxs-lookup"><span data-stu-id="5eefc-130">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="5eefc-131">使用你的层次结构中选择的新对象，将对象的名称更改为 TableAnchor 检查器面板中。</span><span class="sxs-lookup"><span data-stu-id="5eefc-131">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="5eefc-132">此外，单击添加组件，搜索 TableAnchor 组件。</span><span class="sxs-lookup"><span data-stu-id="5eefc-132">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="5eefc-133">选择它并将其添加到该对象。</span><span class="sxs-lookup"><span data-stu-id="5eefc-133">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="5eefc-135">注意：设置定位到 x = 1，y = 0.55 和 z = 2。</span><span class="sxs-lookup"><span data-stu-id="5eefc-135">Note: Set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="5eefc-136">此外，将旋转设置为 y = 90。</span><span class="sxs-lookup"><span data-stu-id="5eefc-136">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="5eefc-138">现在从置入 Prefabs 文件夹中的项目面板中，将拖动表预设到刚创建的"TableAnchor"子对象。</span><span class="sxs-lookup"><span data-stu-id="5eefc-138">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="5eefc-140">最后，DebugWindow 对象中更改为 80 和高度为 10 的宽度。</span><span class="sxs-lookup"><span data-stu-id="5eefc-140">Finally, in the DebugWindow object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="5eefc-142">祝贺</span><span class="sxs-lookup"><span data-stu-id="5eefc-142">Congratulations</span></span>


<span data-ttu-id="5eefc-143">完成此操作，加入你的 Unity 项目的所有用户可以都移动阴历启动器。</span><span class="sxs-lookup"><span data-stu-id="5eefc-143">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="5eefc-144">所有移动都同步，以便每个用户可以看到其他用户交互。</span><span class="sxs-lookup"><span data-stu-id="5eefc-144">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="5eefc-145">这些概念充当用于全功能、 共享的协作体验的基础构建块。</span><span class="sxs-lookup"><span data-stu-id="5eefc-145">These concepts serve as the foundational building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="5eefc-146">虽然所有用户连接的共享体验的一部分，并且所见的相对移动的对象，该应用程序是仍无法准确地对齐虚拟形象和对象，以便本地用户看到彼此，并在物理内的同一位置中的对象世界。</span><span class="sxs-lookup"><span data-stu-id="5eefc-146">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="5eefc-147">若要定位到本地共享的体验，每个设备需要物理环境的了解。</span><span class="sxs-lookup"><span data-stu-id="5eefc-147">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="5eefc-148">在此模块中，我们将通过实现此目的使用[Azure 空间的定位点](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，将在下一课中实现。</span><span class="sxs-lookup"><span data-stu-id="5eefc-148">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="5eefc-149">在继续之前为下一课中，我们将需要完成 ASA 学习模块涵盖 ASA 基础知识，需要 Azure 帐户和资源创建和其他基本建筑物块之前我们可以将此集成到我们的共享体验。</span><span class="sxs-lookup"><span data-stu-id="5eefc-149">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="5eefc-150">[下一课：第 5 课 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="5eefc-150">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

