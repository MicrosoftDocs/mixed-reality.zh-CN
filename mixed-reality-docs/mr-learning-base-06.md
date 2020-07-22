---
title: 入门教程 - 6. 创建用户界面
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: a7c4ea140a9c27f1a92680da6bbe1fb3a4bdc233
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304261"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="3b1e0-105">6.创建用户界面</span><span class="sxs-lookup"><span data-stu-id="3b1e0-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="3b1e0-106">概述</span><span class="sxs-lookup"><span data-stu-id="3b1e0-106">Overview</span></span>

<span data-ttu-id="3b1e0-107">本教程介绍如何使用 MRTK 的按钮和菜单预制件以及 Unity 的 TextMeshPro 组件来创建简单的用户界面。</span><span class="sxs-lookup"><span data-stu-id="3b1e0-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="3b1e0-108">还介绍如何配置这些按钮以触发事件，并添加动态工具提示 UI 元素以向用户提供其他信息。</span><span class="sxs-lookup"><span data-stu-id="3b1e0-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="3b1e0-109">目标</span><span class="sxs-lookup"><span data-stu-id="3b1e0-109">Objectives</span></span>

* <span data-ttu-id="3b1e0-110">了解如何组织集合中的按钮</span><span class="sxs-lookup"><span data-stu-id="3b1e0-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="3b1e0-111">了解如何使用 MRTK 的菜单预制件</span><span class="sxs-lookup"><span data-stu-id="3b1e0-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="3b1e0-112">了解如何使用 UI 菜单和按钮来与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="3b1e0-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="3b1e0-113">了解如何添加文本元素</span><span class="sxs-lookup"><span data-stu-id="3b1e0-113">Learn how to add text elements</span></span>
* <span data-ttu-id="3b1e0-114">了解如何在对象上动态生成工具提示</span><span class="sxs-lookup"><span data-stu-id="3b1e0-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="3b1e0-115">创建按钮的静态面板</span><span class="sxs-lookup"><span data-stu-id="3b1e0-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="3b1e0-116">在“层次结构”窗口中，右键单击“RoverExplorer”对象，然后选择“创建空白项”添加一个空对象作为 RoverExplorer 的子对象，将该对象命名为“Buttons”，并按如下所述配置“转换”组件   ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="3b1e0-117">**位置**：X = -0.6，Y = 0.036，Z = -0.5</span><span class="sxs-lookup"><span data-stu-id="3b1e0-117">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="3b1e0-118">**旋转**：X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="3b1e0-118">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="3b1e0-119">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="3b1e0-119">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="3b1e0-121">在“项目”窗口中，导航至“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”文件夹，然后单击“PressableRoundButton”预制件并将其拖动到 Buttons 对象上，然后右键单击“PressableRoundButton”并选择“重复”以创建副本，重复此操作，直到共有三个 PressableRoundButton 对象     ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="3b1e0-123">在“层次结构”窗口中选择“Buttons”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“GridObjectCollection”组件，并按如下所述配置该组件  ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="3b1e0-124">**排序类型**：子顺序</span><span class="sxs-lookup"><span data-stu-id="3b1e0-124">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="3b1e0-125">**布局**：水平</span><span class="sxs-lookup"><span data-stu-id="3b1e0-125">**Layout**: Horizontal</span></span>
* <span data-ttu-id="3b1e0-126">**单元格宽度**：0.2</span><span class="sxs-lookup"><span data-stu-id="3b1e0-126">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="3b1e0-127">**定位点**：中部左对齐</span><span class="sxs-lookup"><span data-stu-id="3b1e0-127">**Anchor**: Middle Left</span></span>

<span data-ttu-id="3b1e0-128">然后单击“更新集合”按钮以更新 Buttons 对象的子对象的位置：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="3b1e0-130">在“层次结构”窗口中，将按钮命名为“提示”、“分解”和“重置”  。</span><span class="sxs-lookup"><span data-stu-id="3b1e0-130">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="3b1e0-131">为每个按钮选择“SeeItaysLabel” > “TextMeshPro”子对象，然后在“检查器”窗口中，更改相应的“TextMeshPro - Text”组件文本以匹配按钮名称  ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="3b1e0-133">完成后，折叠按钮对象的子对象。</span><span class="sxs-lookup"><span data-stu-id="3b1e0-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="3b1e0-134">在“层次结构”窗口中，选择“提示”按钮对象，然后在“检查器”窗口中配置可交互“OnClick ()”事件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="3b1e0-135">向“无(对象)”字段分配“RoverAssembly”对象 </span><span class="sxs-lookup"><span data-stu-id="3b1e0-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="3b1e0-136">从“无函数”下拉列表中，选择“PlacementHintsController” > “TogglePlacementHints ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-5.png)

<span data-ttu-id="3b1e0-138">在“层次结构”窗口中，选择“分解”按钮对象，然后在“检查器”窗口中配置可交互“OnClick ()”事件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-138">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="3b1e0-139">向“无(对象)”字段分配“RoverAssembly”对象 </span><span class="sxs-lookup"><span data-stu-id="3b1e0-139">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="3b1e0-140">从“无函数”下拉列表中，选择“ExplodedViewController” > “ToggleExplodedView ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-140">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="3b1e0-142">按“播放”按钮进入游戏模式，然后按住空格键以激活操作手，然后使用鼠标按“提示”按钮来切换放置提示对象的可见性：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-142">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="3b1e0-144">然后按“分解”按钮以启用或关闭“分解”视图：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-144">and the **Explode** button to toggle the exploded view on and off:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="3b1e0-146">创建跟随用户的动态菜单</span><span class="sxs-lookup"><span data-stu-id="3b1e0-146">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="3b1e0-147">在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “UX” > “预制件” > “菜单”文件夹，单击“NearMenu4x1”预制件并将其拖动到“层次结构”窗口中，然后将其“转换”位置设置为 X = 0、Y = -0.4、Z = 0 并按如下所述进行配置       ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-147">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="3b1e0-148">验证 SolverHandler 组件的“跟踪的目标类型”是否设置为“头部”  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-148">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="3b1e0-149">选中“RadialView”解算器旁的复选框，使其默认为启用</span><span class="sxs-lookup"><span data-stu-id="3b1e0-149">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="3b1e0-151">在“层次结构”窗口中，将对象重命名为“Menu”，然后展开其 ButtonCollection 子对象以显示四个按钮 ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-151">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="3b1e0-153">将第一个按钮重命名为“指示器”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-153">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="3b1e0-154">更改主标签文本以匹配按钮的名称</span><span class="sxs-lookup"><span data-stu-id="3b1e0-154">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="3b1e0-155">向“无(对象)”字段分配“Indicator”对象 </span><span class="sxs-lookup"><span data-stu-id="3b1e0-155">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="3b1e0-156">从“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-156">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="3b1e0-157">验证是否已选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="3b1e0-157">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="3b1e0-158">将图标更改为“搜索”图标</span><span class="sxs-lookup"><span data-stu-id="3b1e0-158">Change the **Icon** to the 'search' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="3b1e0-160">在“层次结构”窗口中，选择“Indicator”对象，然后在“检查器”窗口中，取消选中其名称旁边的复选框，以使其默认处于非活动状态：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-160">In the Hierarchy window, select the **Indicator** object, then in the Inspector window, uncheck the checkbox next to its name to make it inactive by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="3b1e0-162">现在，当应用程序启动时，会默认禁用指示器，并且可以通过按“指标器”按钮来启用。</span><span class="sxs-lookup"><span data-stu-id="3b1e0-162">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="3b1e0-163">将第二个按钮重命名为“TapToPlace”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-163">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="3b1e0-164">更改主标签文本以匹配按钮的名称</span><span class="sxs-lookup"><span data-stu-id="3b1e0-164">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="3b1e0-165">向“无(对象)”字段分配“RoverExplorer”>“RoverAssembly”对象 </span><span class="sxs-lookup"><span data-stu-id="3b1e0-165">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="3b1e0-166">在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-166">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="3b1e0-167">验证是否已选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="3b1e0-167">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="3b1e0-168">将图标更改为“带有射线的手”图标</span><span class="sxs-lookup"><span data-stu-id="3b1e0-168">Change the **Icon** to the 'hand with ray' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="3b1e0-170">在“层次结构”窗口中选择“RoverAssembly”对象，然后在“检查器”窗口中配置“点击放置(脚本)”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-170">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="3b1e0-171">取消选中其名称旁的复选框，以使其在默认情况下处于非活动状态</span><span class="sxs-lookup"><span data-stu-id="3b1e0-171">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="3b1e0-172">在“On Placing Started ()”事件部分中，单击 + 图标以添加新事件 ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-172">In the **On Placing Started ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="3b1e0-173">向“无(对象)”字段分配“RoverExplorer”>“RoverAssembly”对象 </span><span class="sxs-lookup"><span data-stu-id="3b1e0-173">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="3b1e0-174">在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-174">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="3b1e0-175">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="3b1e0-175">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="3b1e0-177">现在，当应用程序启动时，默认情况下会禁用“点击放置”功能，并且可以通过按“点击放置”按钮来启用。</span><span class="sxs-lookup"><span data-stu-id="3b1e0-177">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="3b1e0-178">此外，当“点击放置”完成时，它会自动禁用。</span><span class="sxs-lookup"><span data-stu-id="3b1e0-178">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="3b1e0-179">向场景添加文本</span><span class="sxs-lookup"><span data-stu-id="3b1e0-179">Adding text to the scene</span></span>

<span data-ttu-id="3b1e0-180">在“层次结构”窗口中，右键单击“Table”对象，然后选择“3D 对象” > “Text - TextMeshPro”添加一个文本对象作为 Table 的子对象，然后在“检查器”窗口中按如下所述配置“矩形转换”组件   ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-180">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="3b1e0-181">将“位置 Y”更改为 1</span><span class="sxs-lookup"><span data-stu-id="3b1e0-181">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="3b1e0-182">将“宽度”更改为 1</span><span class="sxs-lookup"><span data-stu-id="3b1e0-182">Change **Width** to 1</span></span>
* <span data-ttu-id="3b1e0-183">将“高度”更改为 1</span><span class="sxs-lookup"><span data-stu-id="3b1e0-183">Change **Height** to 1</span></span>
* <span data-ttu-id="3b1e0-184">将“旋转 X”更改为 90</span><span class="sxs-lookup"><span data-stu-id="3b1e0-184">Change **Rotation X** to 90</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="3b1e0-186">然后按如下所述配置“TextMeshPro - Text”组件：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-186">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="3b1e0-187">将“文本”更改为漫游者探测器</span><span class="sxs-lookup"><span data-stu-id="3b1e0-187">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="3b1e0-188">将“字形”更改为粗体</span><span class="sxs-lookup"><span data-stu-id="3b1e0-188">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="3b1e0-189">将“字体大小”更改为 1</span><span class="sxs-lookup"><span data-stu-id="3b1e0-189">Change **Font Size** to 1</span></span>
* <span data-ttu-id="3b1e0-190">将“额外设置”>“边距”更改为 0.03</span><span class="sxs-lookup"><span data-stu-id="3b1e0-190">Change Extra Settings > **Margins** to 0.03</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="3b1e0-192">添加工具提示</span><span class="sxs-lookup"><span data-stu-id="3b1e0-192">Adding tooltips</span></span>

<span data-ttu-id="3b1e0-193">在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “功能” > “UX” > “预制件” > “工具提示”文件夹，以查找工具提示预制件      ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-193">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="3b1e0-195">在“层次结构”窗口中展开“RoverExplorer”>“RoverParts”对象并选择其所有子探测器部件对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“ToolTipSpawner”组件并按如下所述配置  ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-195">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="3b1e0-196">确保选中“启用焦点”复选框，以要求用户查看部件以显示工具提示</span><span class="sxs-lookup"><span data-stu-id="3b1e0-196">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="3b1e0-197">从“项目”窗口中将“简单行工具提示”预制件分配给“工具提示预制件”字段 </span><span class="sxs-lookup"><span data-stu-id="3b1e0-197">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="3b1e0-198">将“工具提示替代设置”>“设置模式”更改为“替代” </span><span class="sxs-lookup"><span data-stu-id="3b1e0-198">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="3b1e0-199">将“工具提示替代设置”>“手动透视定位位置 Y”更改为 1.5 </span><span class="sxs-lookup"><span data-stu-id="3b1e0-199">Change the ToolTip Override Settings > **Manual Pivot Location Position Y** to **1.5**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="3b1e0-201">在“层次结构”窗口中选择第一个探测器部件，“RoverParts”>“Camera_Part”，并按如下所述配置“ToolTipSpawner”组件 ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-201">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="3b1e0-202">更改“工具提示文本”以反映部件的名称，即“照相机” </span><span class="sxs-lookup"><span data-stu-id="3b1e0-202">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="3b1e0-204">对每个探测器部件对象重复此步骤以配置“ToolTipSpawner”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-204">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="3b1e0-205">对于 Generator_Part，请将“工具提示文本”更改为“生成器”  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-205">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="3b1e0-206">对于 Lights_Part，请将“工具提示文本”更改为“灯光”  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-206">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="3b1e0-207">对于 UHFAntenna_Part，请将“工具提示文本”更改为“UHF 天线”字段  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-207">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="3b1e0-208">对于 Spectrometer_Part，请将“工具提示文本”更改为“分光仪”  </span><span class="sxs-lookup"><span data-stu-id="3b1e0-208">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="3b1e0-209">按下“播放”按钮进入“游戏”模式，然后在按住鼠标右键的同时移动鼠标，直到视线瞄准部件之一，并将显示该部件的工具提示：</span><span class="sxs-lookup"><span data-stu-id="3b1e0-209">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="3b1e0-211">祝贺</span><span class="sxs-lookup"><span data-stu-id="3b1e0-211">Congratulations</span></span>

<span data-ttu-id="3b1e0-212">在本教程中，你了解了如何使用 MRTK 提供的按钮和菜单预制件以及 Unity 的 TextMeshPro 组件来创建简单的用户界面，以及如何配置按钮以在按下按钮时触发事件。</span><span class="sxs-lookup"><span data-stu-id="3b1e0-212">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="3b1e0-213">还了解了如何添加动态工具提示 UI 元素以向用户提供其他信息。</span><span class="sxs-lookup"><span data-stu-id="3b1e0-213">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="3b1e0-214">下一教程：7.与 3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="3b1e0-214">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)
