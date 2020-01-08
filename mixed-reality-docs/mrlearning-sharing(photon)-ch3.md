---
title: 多用户功能教程-3。 连接多个用户
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 9441cf7a9685b8a197bab1116202db4a9b026f2e
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334304"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="25554-105">3. 连接多个用户</span><span class="sxs-lookup"><span data-stu-id="25554-105">3. Connecting multiple users</span></span>

<span data-ttu-id="25554-106">在本课程中，我们将了解如何将多个用户连接为实时共享体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="25554-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="25554-107">在本课结束时，你将能够在多个设备上打开该应用程序，并查看每个加入人员的一个球表示的头像。</span><span class="sxs-lookup"><span data-stu-id="25554-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="25554-108">目标</span><span class="sxs-lookup"><span data-stu-id="25554-108">Objectives</span></span>

* <span data-ttu-id="25554-109">在应用程序中配置双关语</span><span class="sxs-lookup"><span data-stu-id="25554-109">Configure PUN within your application</span></span>
* <span data-ttu-id="25554-110">配置播放机</span><span class="sxs-lookup"><span data-stu-id="25554-110">Configure players</span></span>
* <span data-ttu-id="25554-111">了解如何在共享体验中连接多个用户</span><span class="sxs-lookup"><span data-stu-id="25554-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="25554-112">说明</span><span class="sxs-lookup"><span data-stu-id="25554-112">Instructions</span></span>

1. <span data-ttu-id="25554-113">在 "资产-> 资源-> Prototyping" 文件夹的 "项目" 面板中，将 NetworkLobby prefab 拖放到层次结构中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="25554-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="25554-115">展开 "NetworkLobby" 时，会看到一个名为 "NetworkRoom" 的子对象。</span><span class="sxs-lookup"><span data-stu-id="25554-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="25554-116">选择 NetworkRoom 后，进入检查器面板，然后单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="25554-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="25554-117">搜索 PhotonView 并添加组件。</span><span class="sxs-lookup"><span data-stu-id="25554-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="25554-119">在层次结构中创建新的空游戏对象。</span><span class="sxs-lookup"><span data-stu-id="25554-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="25554-120">在层次结构中右键单击，然后从上下文菜单中选择 "空"。</span><span class="sxs-lookup"><span data-stu-id="25554-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="25554-121">确保将定位设置为 x = 0、y = 0、z = 0 并将对象命名为 PhotonUser。</span><span class="sxs-lookup"><span data-stu-id="25554-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="25554-123">单击 "添加组件"，然后键入 "通用网络同步"。选择 "通用" 网络同步类。</span><span class="sxs-lookup"><span data-stu-id="25554-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="25554-124">出现类时，单击 "用户" 复选框将其打开。</span><span class="sxs-lookup"><span data-stu-id="25554-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="25554-126">再次单击 "添加组件"，然后键入 "Photon 视图"。</span><span class="sxs-lookup"><span data-stu-id="25554-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="25554-127">选择显示在下拉列表中的 Photon 视图类。</span><span class="sxs-lookup"><span data-stu-id="25554-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="25554-129">单击一般 Net Sync 类的文件图标。</span><span class="sxs-lookup"><span data-stu-id="25554-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="25554-130">将其拖放到 Photon 视图的 "观察的组件" 字段。</span><span class="sxs-lookup"><span data-stu-id="25554-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im .png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="25554-132">接下来，我们将创建一个球来表示加入共享经验的每个人。</span><span class="sxs-lookup"><span data-stu-id="25554-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="25554-133">右键单击刚创建的 PhotonUser 对象，向下滚动到 "3D 对象并单击球体"。</span><span class="sxs-lookup"><span data-stu-id="25554-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="25554-134">这会将一个球游戏对象创建为 PhotonUser 对象的子对象。</span><span class="sxs-lookup"><span data-stu-id="25554-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="25554-136">将球体缩小为 x = 0.06，y = 0.06，ad z = 0.06。</span><span class="sxs-lookup"><span data-stu-id="25554-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="25554-138">将 PhotonUser 游戏对象拖到 "项目" 面板中的 "Prototyping" 文件夹，然后将其从场景中删除。</span><span class="sxs-lookup"><span data-stu-id="25554-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="25554-139">现在，你已创建了一个可在共享体验中生成或实例化新播放器时使用的 prefab。</span><span class="sxs-lookup"><span data-stu-id="25554-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="25554-141">在从层次结构中删除游戏对象之前，请确保该对象已成功复制到 Prototyping 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="25554-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="25554-142">按照步骤3中的说明在层次结构中创建新的对象，并将其命名为 SharedPlayground。</span><span class="sxs-lookup"><span data-stu-id="25554-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="25554-143">然后，单击 "添加组件"，然后搜索 "通用网络管理器"。</span><span class="sxs-lookup"><span data-stu-id="25554-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="25554-144">再次单击它以添加通用网络管理器组件。</span><span class="sxs-lookup"><span data-stu-id="25554-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="25554-145">将对象的位置更改为 x = 0、y = 0，z = 0。</span><span class="sxs-lookup"><span data-stu-id="25554-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="25554-147">祝贺</span><span class="sxs-lookup"><span data-stu-id="25554-147">Congratulations</span></span>

<span data-ttu-id="25554-148">完成上述所有步骤后，生成过程也已完成，按下 "播放" 按钮，然后连接 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="25554-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="25554-149">当您移动头时，您应该会看到一个球四处移动。</span><span class="sxs-lookup"><span data-stu-id="25554-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="25554-150">这将显示加入 Unity 项目的任何用户！</span><span class="sxs-lookup"><span data-stu-id="25554-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="25554-151">[下一课： 4. 与多个用户共享对象移动](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="25554-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>
