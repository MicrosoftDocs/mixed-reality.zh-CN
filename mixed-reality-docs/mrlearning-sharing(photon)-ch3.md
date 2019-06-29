---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465217"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="75009-104">**将多个用户连接**</span><span class="sxs-lookup"><span data-stu-id="75009-104">**Connecting multiple users**</span></span> 

<span data-ttu-id="75009-105">在本课中，我们将了解如何将多个用户连接作为实时共享体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="75009-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="75009-106">本课程结束时，您可以打开多个设备上的应用程序，并查看虚拟形象，表示球体，联接每个人的表示形式。</span><span class="sxs-lookup"><span data-stu-id="75009-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="75009-107">目标：</span><span class="sxs-lookup"><span data-stu-id="75009-107">Objectives:</span></span>

- <span data-ttu-id="75009-108">在应用程序中配置双关语</span><span class="sxs-lookup"><span data-stu-id="75009-108">Configure PUN within your application</span></span>
- <span data-ttu-id="75009-109">配置播放机</span><span class="sxs-lookup"><span data-stu-id="75009-109">Configure players</span></span>
- <span data-ttu-id="75009-110">了解如何连接的共享体验中的多个用户</span><span class="sxs-lookup"><span data-stu-id="75009-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="75009-111">说明</span><span class="sxs-lookup"><span data-stu-id="75009-111">Instructions</span></span>

1. <span data-ttu-id="75009-112">在资产中-> 资源-> 在项目面板中的置入 Prefabs 文件夹中，拖放 NetworkLobby 预设可在向层次结构中如下图所示。</span><span class="sxs-lookup"><span data-stu-id="75009-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="75009-114">在展开 NetworkLobby 时，您将看到名为 NetworkRoom 的子对象。</span><span class="sxs-lookup"><span data-stu-id="75009-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="75009-115">选择 NetworkRoom，转到检查器面板中，并单击添加组件。</span><span class="sxs-lookup"><span data-stu-id="75009-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="75009-116">PhotonView 搜索并添加该组件。</span><span class="sxs-lookup"><span data-stu-id="75009-116">Search for PhotonView and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="75009-118">在层次结构中创建一个新的空游戏对象。</span><span class="sxs-lookup"><span data-stu-id="75009-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="75009-119">在层次结构中，右键单击并从上下文菜单中选择为空。</span><span class="sxs-lookup"><span data-stu-id="75009-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="75009-120">确保将位置设置为 x = 0，y = 0，z = 0，PhotonUser 对象命名为。</span><span class="sxs-lookup"><span data-stu-id="75009-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="75009-122">单击添加组件，并键入泛型 Net 同步。选择泛型 Net 同步类。</span><span class="sxs-lookup"><span data-stu-id="75009-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="75009-123">出现此类后，单击用户复选框以将其打开。</span><span class="sxs-lookup"><span data-stu-id="75009-123">When the class appears, click on the User check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="75009-125">同样，单击添加组件并键入 Photon 视图。</span><span class="sxs-lookup"><span data-stu-id="75009-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="75009-126">在下拉列表中选择出现的 Photon 视图类。</span><span class="sxs-lookup"><span data-stu-id="75009-126">Select the Photon View class that appears in the drop-down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="75009-128">单击针对泛型 Net 同步类的文件图标。</span><span class="sxs-lookup"><span data-stu-id="75009-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="75009-129">拖放 Photon 视图的观察到组件字段中。</span><span class="sxs-lookup"><span data-stu-id="75009-129">Drag and drop it in the Photon View's Observed Components field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="75009-131">接下来，我们创建球体来表示每个联接的共享的体验的人员。</span><span class="sxs-lookup"><span data-stu-id="75009-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="75009-132">右键单击刚创建的 PhotonUser 对象和到 scrolldown"3D 对象，并单击球体。</span><span class="sxs-lookup"><span data-stu-id="75009-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="75009-133">这将创建球游戏对象作为 PhotonUser 对象的子级。</span><span class="sxs-lookup"><span data-stu-id="75009-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="75009-135">缩放 x 到球体 = 0.06，y = 0.06，ad z = 0.06。</span><span class="sxs-lookup"><span data-stu-id="75009-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="75009-137">将 PhotonUser 游戏对象拖到项目面板中置入 Prefabs 文件夹，然后从场景中删除它。</span><span class="sxs-lookup"><span data-stu-id="75009-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="75009-138">我们现在已创建生成或实例化新供应商的共享体验时，可以使用预设。</span><span class="sxs-lookup"><span data-stu-id="75009-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="75009-140">注意： 确保游戏对象已成功复制到置入 Prefabs 文件夹之前从层次结构中删除它。</span><span class="sxs-lookup"><span data-stu-id="75009-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="75009-141">步骤 3 中的说明在层次结构中创建一个新的对象并将其命名 SharedPlayground。</span><span class="sxs-lookup"><span data-stu-id="75009-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="75009-142">然后，单击添加组件和一般网络管理器中，搜索并单击它以添加泛型网络管理器组件。</span><span class="sxs-lookup"><span data-stu-id="75009-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="75009-143">将对象的位置更改为 x = 0，y = 0，并且 z = 0。</span><span class="sxs-lookup"><span data-stu-id="75009-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="75009-145">祝贺</span><span class="sxs-lookup"><span data-stu-id="75009-145">Congratulations</span></span>

<span data-ttu-id="75009-146">上述所有步骤都均已完成，并在生成过程也是完成后，按播放按钮，并连接 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="75009-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="75009-147">应会看到球体移动时您四处移动。</span><span class="sxs-lookup"><span data-stu-id="75009-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="75009-148">这将显示的任意用户的加入你的 Unity 项目 ！</span><span class="sxs-lookup"><span data-stu-id="75009-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="75009-149">[下一课：第 4 课 Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="75009-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

