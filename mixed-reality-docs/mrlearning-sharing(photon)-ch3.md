---
title: HoloLens 2 的 MR 教育共享模块
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 92bea1f3130f67645c10e36fe40cd4bc6f8b9151
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293656"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="cd83c-104">连接多个用户</span><span class="sxs-lookup"><span data-stu-id="cd83c-104">Connecting multiple users</span></span>

<span data-ttu-id="cd83c-105">在本课程中, 我们将了解如何将多个用户连接为实时共享体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="cd83c-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="cd83c-106">在本课结束时, 你将能够在多个设备上打开应用程序, 并查看每个加入人员的表示形式的头像 (由一个球体表示)。</span><span class="sxs-lookup"><span data-stu-id="cd83c-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="cd83c-107">目标</span><span class="sxs-lookup"><span data-stu-id="cd83c-107">Objectives:</span></span>

- <span data-ttu-id="cd83c-108">在应用程序中配置双关语</span><span class="sxs-lookup"><span data-stu-id="cd83c-108">Configure PUN within your application</span></span>
- <span data-ttu-id="cd83c-109">配置播放机</span><span class="sxs-lookup"><span data-stu-id="cd83c-109">Configure players</span></span>
- <span data-ttu-id="cd83c-110">了解如何在共享体验中连接多个用户</span><span class="sxs-lookup"><span data-stu-id="cd83c-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="cd83c-111">说明</span><span class="sxs-lookup"><span data-stu-id="cd83c-111">Instructions</span></span>

1. <span data-ttu-id="cd83c-112">在 "资产-> 资源-> Prototyping" 文件夹的 "项目" 面板中, 将 NetworkLobby prefab 拖放到层次结构中, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="cd83c-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="cd83c-114">展开 "NetworkLobby" 时, 会看到一个名为 "NetworkRoom" 的子对象。</span><span class="sxs-lookup"><span data-stu-id="cd83c-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="cd83c-115">选择 NetworkRoom 后, 进入检查器面板, 然后单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="cd83c-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="cd83c-116">搜索 PhotonView 并添加组件。</span><span class="sxs-lookup"><span data-stu-id="cd83c-116">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="cd83c-118">在层次结构中创建新的空游戏对象。</span><span class="sxs-lookup"><span data-stu-id="cd83c-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="cd83c-119">在层次结构中右键单击, 然后从上下文菜单中选择 "空"。</span><span class="sxs-lookup"><span data-stu-id="cd83c-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="cd83c-120">确保将定位设置为 x = 0、y = 0、z = 0 并将对象命名为 PhotonUser。</span><span class="sxs-lookup"><span data-stu-id="cd83c-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="cd83c-122">单击 "添加组件", 然后键入 "通用网络同步"。选择 "通用" 网络同步类。</span><span class="sxs-lookup"><span data-stu-id="cd83c-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="cd83c-123">出现类时, 单击 "用户" 复选框将其打开。</span><span class="sxs-lookup"><span data-stu-id="cd83c-123">When the class appears, click on the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="cd83c-125">再次单击 "添加组件", 然后键入 "Photon 视图"。</span><span class="sxs-lookup"><span data-stu-id="cd83c-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="cd83c-126">选择显示在下拉列表中的 Photon 视图类。</span><span class="sxs-lookup"><span data-stu-id="cd83c-126">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="cd83c-128">单击一般 Net Sync 类的文件图标。</span><span class="sxs-lookup"><span data-stu-id="cd83c-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="cd83c-129">将其拖放到 Photon 视图的 "观察的组件" 字段。</span><span class="sxs-lookup"><span data-stu-id="cd83c-129">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im .png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="cd83c-131">接下来, 我们将创建一个球来表示加入共享经验的每个人。</span><span class="sxs-lookup"><span data-stu-id="cd83c-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="cd83c-132">右键单击刚创建的 PhotonUser 对象, 并单击 "三维对象", 然后单击 "球面"。</span><span class="sxs-lookup"><span data-stu-id="cd83c-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="cd83c-133">这会将一个球游戏对象创建为 PhotonUser 对象的子对象。</span><span class="sxs-lookup"><span data-stu-id="cd83c-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="cd83c-135">将球体缩小为 x = 0.06, y = 0.06, ad z = 0.06。</span><span class="sxs-lookup"><span data-stu-id="cd83c-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="cd83c-137">将 PhotonUser 游戏对象拖到 "项目" 面板中的 "Prototyping" 文件夹, 然后将其从场景中删除。</span><span class="sxs-lookup"><span data-stu-id="cd83c-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="cd83c-138">现在, 我们创建了一个可在共享体验中生成或实例化新播放器时使用的 prefab。</span><span class="sxs-lookup"><span data-stu-id="cd83c-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="cd83c-140">注意: 在从层次结构中删除游戏对象之前, 请确保它已成功复制到 Prototyping 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="cd83c-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="cd83c-141">按照步骤3中的说明在层次结构中创建新的对象, 并将其命名为 SharedPlayground。</span><span class="sxs-lookup"><span data-stu-id="cd83c-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="cd83c-142">然后, 单击 "添加组件", 搜索 "通用网络管理器", 然后单击它以添加通用网络管理器组件。</span><span class="sxs-lookup"><span data-stu-id="cd83c-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="cd83c-143">将对象的位置更改为 x = 0、y = 0, z = 0。</span><span class="sxs-lookup"><span data-stu-id="cd83c-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="cd83c-145">祝贺</span><span class="sxs-lookup"><span data-stu-id="cd83c-145">Congratulations</span></span>

<span data-ttu-id="cd83c-146">完成上述所有步骤后, 生成过程也已完成, 按下 "播放" 按钮并连接 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="cd83c-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="cd83c-147">当您移动头时, 您应该会看到一个球四处移动。</span><span class="sxs-lookup"><span data-stu-id="cd83c-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="cd83c-148">这将显示加入 Unity 项目的任何用户!</span><span class="sxs-lookup"><span data-stu-id="cd83c-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="cd83c-149">[下一课：共享 (Photon) 第4课](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="cd83c-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

