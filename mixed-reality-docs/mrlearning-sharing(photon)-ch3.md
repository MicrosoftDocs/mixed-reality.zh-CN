---
title: 多用户功能教程 - 3. 连接多个用户
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031230"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="ced04-105">3.连接多个用户</span><span class="sxs-lookup"><span data-stu-id="ced04-105">3. Connecting multiple users</span></span>

<span data-ttu-id="ced04-106">本课程介绍如何将多个用户连接为实时共享体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="ced04-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="ced04-107">在本课程结束时，你将可以在多个设备上打开应用程序，并查看每个参与该体验的人员的头像（以球体表示）。</span><span class="sxs-lookup"><span data-stu-id="ced04-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="ced04-108">目标</span><span class="sxs-lookup"><span data-stu-id="ced04-108">Objectives</span></span>

* <span data-ttu-id="ced04-109">在应用程序中配置 PUN</span><span class="sxs-lookup"><span data-stu-id="ced04-109">Configure PUN within your application</span></span>
* <span data-ttu-id="ced04-110">配置播放器</span><span class="sxs-lookup"><span data-stu-id="ced04-110">Configure players</span></span>
* <span data-ttu-id="ced04-111">了解如何在共享体验中连接多个用户</span><span class="sxs-lookup"><span data-stu-id="ced04-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="ced04-112">说明</span><span class="sxs-lookup"><span data-stu-id="ced04-112">Instructions</span></span>

1. <span data-ttu-id="ced04-113">在“项目”面板的“资产”->“资源”->“预制件”文件夹中，将 NetworkLobby 预制件拖放到层次结构中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="ced04-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="ced04-115">展开 NetworkLobby 时，会看到名为 NetworkRoom 的子对象。</span><span class="sxs-lookup"><span data-stu-id="ced04-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="ced04-116">选择 NetworkRoom 后，进入“检查器”面板，然后单击“添加组件”。</span><span class="sxs-lookup"><span data-stu-id="ced04-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="ced04-117">搜索 PhotonView 并添加该组件。</span><span class="sxs-lookup"><span data-stu-id="ced04-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="ced04-119">在层次结构中新建一个空游戏对象。</span><span class="sxs-lookup"><span data-stu-id="ced04-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="ced04-120">在层次结构中单击右键，然后从上下文菜单中选择“空”。</span><span class="sxs-lookup"><span data-stu-id="ced04-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="ced04-121">确保位置设置为 x=0，y=0，z=0，将对象命名为 PhotonUser。</span><span class="sxs-lookup"><span data-stu-id="ced04-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="ced04-123">单击“添加组件”并键入“通用网络同步”。选择“通用网络同步”类。</span><span class="sxs-lookup"><span data-stu-id="ced04-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="ced04-124">显示该类后，单击“用户”复选框将其启用。</span><span class="sxs-lookup"><span data-stu-id="ced04-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="ced04-126">再次单击“添加组件”并键入“Photon 视图”。</span><span class="sxs-lookup"><span data-stu-id="ced04-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="ced04-127">选择下拉列表中显示的“Photon 视图”类。</span><span class="sxs-lookup"><span data-stu-id="ced04-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="ced04-129">单击“通用网络同步”类对应的“文件”图标。</span><span class="sxs-lookup"><span data-stu-id="ced04-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="ced04-130">将此类拖放到“Photon 视图”的“观察到的组件”字段中。</span><span class="sxs-lookup"><span data-stu-id="ced04-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="ced04-132">接下来，我们将创建一个球体来表示参与共享体验的每个人员。</span><span class="sxs-lookup"><span data-stu-id="ced04-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="ced04-133">右键单击刚刚创建的 PhotonUser 对象，向下滚动到“3D 对象”并单击“球体”。</span><span class="sxs-lookup"><span data-stu-id="ced04-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="ced04-134">这会创建一个球体游戏对象作为 PhotonUser 对象的子级。</span><span class="sxs-lookup"><span data-stu-id="ced04-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="ced04-136">将球体缩小为 x=0.06，y=0.06，z=0.06。</span><span class="sxs-lookup"><span data-stu-id="ced04-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="ced04-138">将 PhotonUser 游戏对象拖放到“项目”面板中的“预制件”文件夹，然后将其从场景中删除。</span><span class="sxs-lookup"><span data-stu-id="ced04-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="ced04-139">现已创建一个预制件，在共享体验中生成或实例化新的玩家时，可以使用该预制件。</span><span class="sxs-lookup"><span data-stu-id="ced04-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="ced04-141">在从层次结构中删除该游戏对象之前，请确保已将它成功复制到“预制件”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="ced04-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="ced04-142">根据步骤 3 中的说明在层次结构中创建一个新对象，并将其命名为 SharedPlayground。</span><span class="sxs-lookup"><span data-stu-id="ced04-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="ced04-143">然后单击“添加组件”并搜索“通用网络管理器”。</span><span class="sxs-lookup"><span data-stu-id="ced04-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="ced04-144">再次单击“添加组件”以添加“通用网络管理器”组件。</span><span class="sxs-lookup"><span data-stu-id="ced04-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="ced04-145">将对象位置更改为 x=0，y=0，z=0。</span><span class="sxs-lookup"><span data-stu-id="ced04-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="ced04-147">祝贺</span><span class="sxs-lookup"><span data-stu-id="ced04-147">Congratulations</span></span>

<span data-ttu-id="ced04-148">完成上述所有步骤后，生成过程也已完成。请按“播放”按钮并连接 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="ced04-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="ced04-149">晃头时，将会看到一个球体也随着移动。</span><span class="sxs-lookup"><span data-stu-id="ced04-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="ced04-150">此球体表示参与 Unity 项目的任何用户！</span><span class="sxs-lookup"><span data-stu-id="ced04-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="ced04-151">[下一课：4.与多个用户共享对象移动](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="ced04-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>
