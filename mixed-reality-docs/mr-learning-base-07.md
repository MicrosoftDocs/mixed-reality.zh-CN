---
title: 入门教程 - 7. 与 3D 对象交互
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: f02780a1b9421b814242727ce92311d62b5e3461
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376419"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="825d2-105">7.与 3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="825d2-105">7. Interacting with 3D objects</span></span>

<span data-ttu-id="825d2-106">本教程介绍如何启用 3D 对象的远近操作以及如何限制允许的操作类型。</span><span class="sxs-lookup"><span data-stu-id="825d2-106">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="825d2-107">你还将了解如何在 3D 对象周围添加边界框，以便更轻松地控制对象操作。</span><span class="sxs-lookup"><span data-stu-id="825d2-107">You will also learn how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="825d2-108">目标</span><span class="sxs-lookup"><span data-stu-id="825d2-108">Objectives</span></span>

* <span data-ttu-id="825d2-109">了解如何配置 3D 对象，以便可以与它们进行交互</span><span class="sxs-lookup"><span data-stu-id="825d2-109">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="825d2-110">了解如何将边界框添加到 3D 对象</span><span class="sxs-lookup"><span data-stu-id="825d2-110">Learn how to add bounding boxes to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="825d2-111">操作 3D 对象</span><span class="sxs-lookup"><span data-stu-id="825d2-111">Manipulating 3D objects</span></span>

<span data-ttu-id="825d2-112">在本部分中，你将添加相应功能，用于操作在教程[定位场景中的对象](mr-learning-base-04.md)期间在表格中包含的所有探测器部件。</span><span class="sxs-lookup"><span data-stu-id="825d2-112">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="825d2-113">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="825d2-113">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="825d2-114">将“对象操控器(脚本)”组件添加到所有部件对象</span><span class="sxs-lookup"><span data-stu-id="825d2-114">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="825d2-115">将“NearInteractionGrabbable”组件添加到所有部件对象</span><span class="sxs-lookup"><span data-stu-id="825d2-115">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="825d2-116">配置“对象操控器(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="825d2-116">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="825d2-117">若要**操作某个对象**，该对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="825d2-117">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="825d2-118">“碰撞体”组件，例如盒碰撞体</span><span class="sxs-lookup"><span data-stu-id="825d2-118">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="825d2-119">“对象操控器(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="825d2-119">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="825d2-120">若要使用跟踪手**操作**和**抓取某个对象**，该对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="825d2-120">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="825d2-121">“碰撞体”组件，例如盒碰撞体</span><span class="sxs-lookup"><span data-stu-id="825d2-121">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="825d2-122">“对象操控器(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="825d2-122">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="825d2-123">“NearInteractionGrabbable”组件</span><span class="sxs-lookup"><span data-stu-id="825d2-123">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="825d2-124">此外，你将配置漫游者探测器，以便能够将探测器部件放置到探测器上，使其成为完整的探测器。</span><span class="sxs-lookup"><span data-stu-id="825d2-124">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="825d2-125">在“层次结构”窗口中展开“RoverExplorer”>“RoverParts”对象并选择其所有子探测器部件对象和“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮将以下组件添加到所有选定对象  ：</span><span class="sxs-lookup"><span data-stu-id="825d2-125">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="825d2-126">“对象操控器(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="825d2-126">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="825d2-127">“NearInteractionGrabbable”组件</span><span class="sxs-lookup"><span data-stu-id="825d2-127">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="825d2-128">“部件程序集控制器(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="825d2-128">**Part Assembly Controller (Script)** component</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="825d2-130">若要选择不相邻的多个对象，请在按住 CTRL 键的同时使用鼠标选择任何对象。</span><span class="sxs-lookup"><span data-stu-id="825d2-130">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="825d2-131">在本教程中，碰撞体已添加到探测器部件中。</span><span class="sxs-lookup"><span data-stu-id="825d2-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="825d2-132">若要详细了解碰撞体，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞体</a>文档。</span><span class="sxs-lookup"><span data-stu-id="825d2-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="825d2-133">“部件程序集控制器(脚本)”并不是 MRTK 的一部分，而是属于本教程的资源。</span><span class="sxs-lookup"><span data-stu-id="825d2-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="825d2-134">在所有探测器部件对象和 RoverAssembly 对象仍处于选中状态的情况下，在“检查器”窗口中，配置“对象操控器(脚本)”组件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="825d2-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="825d2-135">从“双手操作类型”下拉列表中取消选中“缩放”，以便仅启用“移动”和“旋转”  </span><span class="sxs-lookup"><span data-stu-id="825d2-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="825d2-137">至此，已为所有探测器部件对象和 RoverAssembly 对象启用了对象操作。</span><span class="sxs-lookup"><span data-stu-id="825d2-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="825d2-138">在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “StandardAssets” > “音频”文件夹来查找音频剪辑    ：</span><span class="sxs-lookup"><span data-stu-id="825d2-138">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="825d2-140">在“层次结构”窗口中重新选择所有探测器部件对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“音频资源”组件，并按如下所述配置该组件  ：</span><span class="sxs-lookup"><span data-stu-id="825d2-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="825d2-141">将“MRTK_Scale_Start”音频剪辑分配到“AudioClip”字段 </span><span class="sxs-lookup"><span data-stu-id="825d2-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="825d2-142">取消选中“唤醒时播放”复选框</span><span class="sxs-lookup"><span data-stu-id="825d2-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="825d2-143">将“空间混合”更改为 1</span><span class="sxs-lookup"><span data-stu-id="825d2-143">Change **Spatial Blend** to 1</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="825d2-145">在“层次结构”窗口中，展开“RoverAssembly”>“RoverModel_PlacementHints_XRay”>“Parts_PlacementHints”对象以显示所有放置提示对象，然后选择第一个探测器部件，“RoverParts”>“Camera_Part”，并配置“部件程序集控制器(脚本)”组件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="825d2-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="825d2-146">将“Camera_PlacementHint”对象分配到“定位位置”字段 </span><span class="sxs-lookup"><span data-stu-id="825d2-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="825d2-148">对其余的每个探测器部件对象重复该步骤，以配置“部件程序集控制器(脚本)”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="825d2-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="825d2-149">对于“Generator_Part”，请将“Generator_PlacementHint”对象分配到“定位位置”字段  </span><span class="sxs-lookup"><span data-stu-id="825d2-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="825d2-150">对于“Lights_Part”，请将“Lights_PlacementHint”对象分配到“定位位置”字段  </span><span class="sxs-lookup"><span data-stu-id="825d2-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="825d2-151">对于“UHFAntenna_Part”，请将“UHFAntenna_PlacementHint”对象分配到“定位位置”字段  </span><span class="sxs-lookup"><span data-stu-id="825d2-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="825d2-152">对于“Spectrometer_Part”，请将“Spectrometer_PlacementHint”对象分配到“定位位置”字段  </span><span class="sxs-lookup"><span data-stu-id="825d2-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="825d2-153">对于“RoverAssembly”，将对象本身（即同一 RoverAssembly 对象）分配到“定位位置”字段  </span><span class="sxs-lookup"><span data-stu-id="825d2-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="825d2-154">在“层次结构”窗口中，选择“RoverExplorer”>“按钮”>“重置”按钮对象，然后在“检查器”窗口中配置可交互的“OnClick ()”事件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="825d2-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="825d2-155">向“无(对象)”字段分配“RoverAssembly”对象 </span><span class="sxs-lookup"><span data-stu-id="825d2-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="825d2-156">从“无函数”下拉列表中，选择“PartAssemblyController” > “ResetPlacement ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="825d2-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="825d2-158">如果现在进入“游戏”模式，就可以使用近距或远距交互将探测器部件放置到探测器上。</span><span class="sxs-lookup"><span data-stu-id="825d2-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="825d2-159">一旦部件靠近相应的放置提示，它将贴靠到位并成为探测器的一部分。</span><span class="sxs-lookup"><span data-stu-id="825d2-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="825d2-160">若要重置放置，可以按“重置”按钮：</span><span class="sxs-lookup"><span data-stu-id="825d2-160">To reset the placements, you can press the Reset button:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="825d2-162">若要详细了解“对象操控器”组件及其相关属性，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[对象操控器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)指南。</span><span class="sxs-lookup"><span data-stu-id="825d2-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="825d2-163">添加边界框</span><span class="sxs-lookup"><span data-stu-id="825d2-163">Adding bounding boxes</span></span>

<span data-ttu-id="825d2-164">边界框提供用于缩放和旋转的控点，在近距和远距交互时，使用边界框可以更轻松、更直观地单手操作对象。</span><span class="sxs-lookup"><span data-stu-id="825d2-164">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="825d2-165">在此示例中，将向 RoverExplorer 对象添加一个边界框，以便可以轻松实现整体移动、旋转和缩放。</span><span class="sxs-lookup"><span data-stu-id="825d2-165">In this example, you will add a bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="825d2-166">此外，还将配置菜单，以便可以打开和关闭边界框。</span><span class="sxs-lookup"><span data-stu-id="825d2-166">Additionally, you will configure the Menu so you can turn the Bounding Box on and off.</span></span>

<span data-ttu-id="825d2-167">在“层次结构”窗口中选择“RoverExplorer”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加以下组件 ：</span><span class="sxs-lookup"><span data-stu-id="825d2-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="825d2-168">BoundingBox 组件</span><span class="sxs-lookup"><span data-stu-id="825d2-168">**BoundingBox** component</span></span>
* <span data-ttu-id="825d2-169">“对象操控器(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="825d2-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="825d2-170">然后取消选中两个组件旁边的复选框，以使其默认为“禁用” ：</span><span class="sxs-lookup"><span data-stu-id="825d2-170">Then **uncheck** the checkbox next to both components to make them **disabled** by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="825d2-172">边界框可视化效果是在运行时创建的，因此在进入“游戏”模式之前不可见。</span><span class="sxs-lookup"><span data-stu-id="825d2-172">The Bounding Box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="825d2-173">BoundingBox 组件将在运行时自动添加 NearInteractionGrabbable 组件。</span><span class="sxs-lookup"><span data-stu-id="825d2-173">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="825d2-174">因此，无需添加此组件即可使用跟踪的双手抓取包含的对象。</span><span class="sxs-lookup"><span data-stu-id="825d2-174">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

<span data-ttu-id="825d2-175">在“层次结构”窗口中展开“菜单”>“ButtonCollection”对象以显示第四个按钮，并将第三个按钮重命名为“BoundingBox_Enable”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="825d2-175">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="825d2-176">将“主标签文本”更改为“启用” </span><span class="sxs-lookup"><span data-stu-id="825d2-176">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="825d2-177">向“无(对象)”字段分配“RoverExplorer”对象 </span><span class="sxs-lookup"><span data-stu-id="825d2-177">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="825d2-178">在“无函数”下拉列表中选择“BoundingBox” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="825d2-178">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="825d2-179">验证是否已选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="825d2-179">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="825d2-180">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="825d2-180">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="825d2-181">向“无(对象)”字段分配“RoverExplorer”对象 </span><span class="sxs-lookup"><span data-stu-id="825d2-181">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="825d2-182">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="825d2-182">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="825d2-183">验证是否已选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="825d2-183">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="825d2-184">将图标保留为“带有边界框的多维数据集”图标</span><span class="sxs-lookup"><span data-stu-id="825d2-184">Leave the **Icon** as the 'cube with bounding box' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="825d2-186">将第四个和最后一个按钮重命名为“BoundingBox_Disable”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="825d2-186">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="825d2-187">将“主标签文本”更改为“禁用” </span><span class="sxs-lookup"><span data-stu-id="825d2-187">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="825d2-188">向“无(对象)”字段分配“RoverExplorer”对象 </span><span class="sxs-lookup"><span data-stu-id="825d2-188">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="825d2-189">在“无函数”下拉列表中选择“BoundingBox” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="825d2-189">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="825d2-190">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="825d2-190">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="825d2-191">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="825d2-191">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="825d2-192">向“无(对象)”字段分配“RoverExplorer”对象 </span><span class="sxs-lookup"><span data-stu-id="825d2-192">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="825d2-193">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="825d2-193">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="825d2-194">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="825d2-194">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="825d2-195">将图标更改为“带有边界框的多维数据集”图标</span><span class="sxs-lookup"><span data-stu-id="825d2-195">Change the **Icon** to the 'cube with bounding box" icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="825d2-197">如果现在进入“游戏”模式并通过单击“启用”按钮启用边界框，则可以使用近距或远距交互来移动、旋转和缩放边界框，然后使用“禁用”按钮再次禁用边界框：</span><span class="sxs-lookup"><span data-stu-id="825d2-197">If you now enter Game mode and enable the Bounding Box by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="825d2-199">若要详细了解“边界框”组件及其相关属性，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[边界框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)指南。</span><span class="sxs-lookup"><span data-stu-id="825d2-199">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="825d2-200">祝贺</span><span class="sxs-lookup"><span data-stu-id="825d2-200">Congratulations</span></span>

<span data-ttu-id="825d2-201">在本教程中，你了解了如何为 3D 对象启用近距和远距操作，以及如何限制允许的操作类型。</span><span class="sxs-lookup"><span data-stu-id="825d2-201">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="825d2-202">还了解了如何在 3D 对象周围添加边界框，以便更轻松地控制对象操作。</span><span class="sxs-lookup"><span data-stu-id="825d2-202">You also learned how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

[<span data-ttu-id="825d2-203">下一教程：8.使用眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="825d2-203">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
