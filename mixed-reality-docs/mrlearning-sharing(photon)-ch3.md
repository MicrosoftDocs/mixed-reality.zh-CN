---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326986"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="658a2-104">**将多个用户连接**</span><span class="sxs-lookup"><span data-stu-id="658a2-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="658a2-105">在本课中，我们将了解如何将多个用户连接作为实时共享体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="658a2-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="658a2-106">本课程结束时，你将能够打开多个设备上的应用程序并查看"虚拟形象"表示每个人员的联接 （表示球体的头像。）</span><span class="sxs-lookup"><span data-stu-id="658a2-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="658a2-107">目标：</span><span class="sxs-lookup"><span data-stu-id="658a2-107">Objectives:</span></span>

- <span data-ttu-id="658a2-108">在应用程序中配置双关语</span><span class="sxs-lookup"><span data-stu-id="658a2-108">Configure PUN within your application</span></span>
- <span data-ttu-id="658a2-109">配置播放机</span><span class="sxs-lookup"><span data-stu-id="658a2-109">Configure players</span></span>
- <span data-ttu-id="658a2-110">了解如何连接的共享体验中的多个用户</span><span class="sxs-lookup"><span data-stu-id="658a2-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="658a2-111">说明</span><span class="sxs-lookup"><span data-stu-id="658a2-111">Instructions</span></span>

1. <span data-ttu-id="658a2-112">在资产中 > 资源 > 预设文件夹的项目面板的拖放"NetworkLobby"预设中的层次结构，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="658a2-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="658a2-114">在展开 prefab"NetworkLobby"时，应会看到名为"NetworkRoom。"的子对象</span><span class="sxs-lookup"><span data-stu-id="658a2-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="658a2-115">使用它选择，请转到检查器面板并单击"添加组件"。</span><span class="sxs-lookup"><span data-stu-id="658a2-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="658a2-116">搜索"PhotonView"并添加该组件。</span><span class="sxs-lookup"><span data-stu-id="658a2-116">Search for "PhotonView" and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="658a2-118">在层次结构中创建一个新的空游戏对象 （右键单击层次结构中并从上下文菜单中选择"空"）。</span><span class="sxs-lookup"><span data-stu-id="658a2-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="658a2-119">确保将位置设置为 x = 0，y = 0，z = 0，命名该对象，"PhotonUser。"</span><span class="sxs-lookup"><span data-stu-id="658a2-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="658a2-121">接下来，我们想要创建球体来表示每个联接的共享的体验的人员。</span><span class="sxs-lookup"><span data-stu-id="658a2-121">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="658a2-122">右键单击刚创建的"PhotonUser"对象，转到"3D 对象"，然后单击"球体"。</span><span class="sxs-lookup"><span data-stu-id="658a2-122">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="658a2-123">这将创建球游戏对象作为 PhotonUser 对象的子级。</span><span class="sxs-lookup"><span data-stu-id="658a2-123">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. <span data-ttu-id="658a2-125">缩放 x 到球体 = 0.06，y = 0.06，ad z = 0.06。</span><span class="sxs-lookup"><span data-stu-id="658a2-125">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. <span data-ttu-id="658a2-127">将"PhotonUser"游戏对象拖到项目面板中的"预设"文件夹。</span><span class="sxs-lookup"><span data-stu-id="658a2-127">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="658a2-128">然后，删除从场景。</span><span class="sxs-lookup"><span data-stu-id="658a2-128">Then, delete it from the scene.</span></span> <span data-ttu-id="658a2-129">我们现在已创建生成或实例化新供应商的共享体验时，将使用的预设。</span><span class="sxs-lookup"><span data-stu-id="658a2-129">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="658a2-131">注意： 确保游戏对象已成功复制到"prefabs"文件夹之前从层次结构中删除它。</span><span class="sxs-lookup"><span data-stu-id="658a2-131">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

7. <span data-ttu-id="658a2-132">（使用类似的步骤 3 的说明），在层次结构中创建一个新的对象并将其命名为"SharedPlayground。"</span><span class="sxs-lookup"><span data-stu-id="658a2-132">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="658a2-133">然后，单击"添加组件"并搜索"通用网络管理器"并单击它以添加泛型网络管理器组件。</span><span class="sxs-lookup"><span data-stu-id="658a2-133">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="658a2-134">将对象的位置更改为 x = 0，y = 0，并且 z = 0。</span><span class="sxs-lookup"><span data-stu-id="658a2-134">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="658a2-136">祝贺</span><span class="sxs-lookup"><span data-stu-id="658a2-136">Congratulations</span></span>

<span data-ttu-id="658a2-137">上述所有步骤都均已完成，并生成过程后，按播放按钮并连接 HoloLens 2 时，你应看到球体移动时您四处移动 ！</span><span class="sxs-lookup"><span data-stu-id="658a2-137">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="658a2-138">这将显示的任意用户的加入你的 Unity 项目 ！</span><span class="sxs-lookup"><span data-stu-id="658a2-138">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="658a2-139">[下一课：第 4 课 Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="658a2-139">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

