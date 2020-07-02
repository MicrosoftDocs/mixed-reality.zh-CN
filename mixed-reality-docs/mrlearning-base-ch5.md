---
title: 入门教程 - 6. 探索高级输入选项
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 9a19ad59e520a2743aafd954910f43c6f51d6c8a
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441854"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="a9603-105">6.探索高级输入选项</span><span class="sxs-lookup"><span data-stu-id="a9603-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="a9603-106">本教程探讨 HoloLens 2 的几个高级输入选项，包括语音命令、平移手势和眼动跟踪的用法。</span><span class="sxs-lookup"><span data-stu-id="a9603-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="a9603-107">目标</span><span class="sxs-lookup"><span data-stu-id="a9603-107">Objectives</span></span>

* <span data-ttu-id="a9603-108">使用语音命令和关键字触发事件</span><span class="sxs-lookup"><span data-stu-id="a9603-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="a9603-109">使用跟踪手平移纹理和 3D 对象</span><span class="sxs-lookup"><span data-stu-id="a9603-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="a9603-110">利用 HoloLens 2 眼动跟踪功能选择对象</span><span class="sxs-lookup"><span data-stu-id="a9603-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="a9603-111">启用语音命令</span><span class="sxs-lookup"><span data-stu-id="a9603-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="a9603-112">在本部分，你将实现一个语音命令来让用户在 Octa 对象中播放声音。</span><span class="sxs-lookup"><span data-stu-id="a9603-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="a9603-113">为此，你将创建一个新的语音命令，然后配置事件，以便在讲出语音命令关键字时触发所需的操作。</span><span class="sxs-lookup"><span data-stu-id="a9603-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="a9603-114">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="a9603-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="a9603-115">克隆默认的输入系统配置文件</span><span class="sxs-lookup"><span data-stu-id="a9603-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="a9603-116">克隆默认的语音命令配置文件</span><span class="sxs-lookup"><span data-stu-id="a9603-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="a9603-117">创建新的语音命令</span><span class="sxs-lookup"><span data-stu-id="a9603-117">Create a new speech command</span></span>
4. <span data-ttu-id="a9603-118">添加并配置“语音输入处理程序(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="a9603-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="a9603-119">实现语音命令的响应事件</span><span class="sxs-lookup"><span data-stu-id="a9603-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="a9603-120">1.克隆默认的输入系统配置文件</span><span class="sxs-lookup"><span data-stu-id="a9603-120">1. Clone the default Input System Profile</span></span>
<span data-ttu-id="a9603-121">在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“输入”选项卡，并克隆“DefaultHoloLens2InputSystemProfile”，以将其替换为你自己的可自定义**输入系统配置文件**：  </span><span class="sxs-lookup"><span data-stu-id="a9603-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a9603-123">如果使用的是 MRTK 2.4.0 或更高版本：</span><span class="sxs-lookup"><span data-stu-id="a9603-123">If you're using MRTK 2.4.0 or later:</span></span>
> * <span data-ttu-id="a9603-124">从“层次结构”选项卡中选择“MixedRealityToolkit”对象，在“检查器”窗口中单击“输入”选项卡，然后展开“指针”部分  。</span><span class="sxs-lookup"><span data-stu-id="a9603-124">Select the **MixedRealityToolkit** object from the Hierarchy tab, then click the **Input** tab in the Inspector window and expand the **Pointers** section.</span></span> 
> * <span data-ttu-id="a9603-125">克隆“DefaultMixedRealityInputPointerProfile”，并将它替换为你自己的可自定义输入指针配置文件 。</span><span class="sxs-lookup"><span data-stu-id="a9603-125">Clone the **DefaultMixedRealityInputPointerProfile** and replace it with your own customizable **Input Pointer Profile**.</span></span>
> * <span data-ttu-id="a9603-126">在“凝视设置”部分中检查“是否已启用眼动跟踪”是否为 true 。</span><span class="sxs-lookup"><span data-stu-id="a9603-126">Check that **Is Eye Tracked Enabled** is true in the **Gaze Settings** section.</span></span> 

> [!TIP]
> <span data-ttu-id="a9603-127">有关如何克隆 MRTK 配置文件的提示，可参阅[如何配置混合现实工具包配置文件](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明。</span><span class="sxs-lookup"><span data-stu-id="a9603-127">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="a9603-128">2.克隆默认的语音命令配置文件</span><span class="sxs-lookup"><span data-stu-id="a9603-128">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="a9603-129">展开“语音”部分，克隆“DefaultMixedRealitySpeechCommandsProfile”以将其替换为你自己的可自定义**语音命令配置文件**： </span><span class="sxs-lookup"><span data-stu-id="a9603-129">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="a9603-131">3.创建新的语音命令</span><span class="sxs-lookup"><span data-stu-id="a9603-131">3. Create a new speech command</span></span>

<span data-ttu-id="a9603-132">在“语音命令”部分，单击“+ 添加新的语音命令”按钮以在现有语音命令列表的底部添加一个新的语音命令，然后在“关键字”字段中输入适当的单词或短语，例如“播放音乐”：   </span><span class="sxs-lookup"><span data-stu-id="a9603-132">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="a9603-134">如果计算机上没有麦克风，而你想要使用编辑器中的模拟功能来测试语音命令，可将一个 KeyCode 分配到语音命令，以便在按下相应的键时触发该命令。</span><span class="sxs-lookup"><span data-stu-id="a9603-134">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="a9603-135">4.添加并配置“语音输入处理程序(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="a9603-135">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="a9603-136">在“层次结构”窗口中选择“Octa”对象，并将“语音输入处理程序(脚本)”组件添加到该 Octa 对象。 </span><span class="sxs-lookup"><span data-stu-id="a9603-136">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="a9603-137">然后取消选中“需要焦点”复选框，使用户无需查看 Octa 对象即可触发语音命令：</span><span class="sxs-lookup"><span data-stu-id="a9603-137">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="a9603-139">5.实现语音命令的响应事件</span><span class="sxs-lookup"><span data-stu-id="a9603-139">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="a9603-140">在“语音输入处理程序(脚本)”组件中，单击 **+** 小按钮将一个关键字元素添加到关键字列表中：</span><span class="sxs-lookup"><span data-stu-id="a9603-140">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="a9603-142">单击新建的“元素 0”将其展开，然后从“关键字”下拉列表中，选择前面创建的“播放音乐”关键字：  </span><span class="sxs-lookup"><span data-stu-id="a9603-142">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="a9603-144">关键字下拉列表中的关键字是根据语音命令配置文件中“语音命令”列表内定义的关键字填充的。</span><span class="sxs-lookup"><span data-stu-id="a9603-144">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="a9603-145">创建新的 **Response ()** 事件，配置 **Octa** 对象用于接收该事件，将 **AudioSource.PlayOneShot** 定义为要触发的操作，然后将适当的音频剪辑（例如 MRTK_Gem 音频剪辑）分配到“音频剪辑”字段：</span><span class="sxs-lookup"><span data-stu-id="a9603-145">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="a9603-147">有关如何实现事件和分配音频剪辑的提示，可参阅[实现 On Touch Started 事件](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)中的说明。</span><span class="sxs-lookup"><span data-stu-id="a9603-147">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="a9603-148">平移手势</span><span class="sxs-lookup"><span data-stu-id="a9603-148">The Pan Gesture</span></span>

<span data-ttu-id="a9603-149">平移手势非常有用，可让你用手指或手滚动浏览内容。</span><span class="sxs-lookup"><span data-stu-id="a9603-149">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="a9603-150">此示例首先演示如何滚动 2D UI，然后演示如何将其展开，以便能够滚动浏览 3D 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="a9603-150">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="a9603-151">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="a9603-151">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="a9603-152">创建可用于平移的 Quad 对象</span><span class="sxs-lookup"><span data-stu-id="a9603-152">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="a9603-153">添加“近距交互可触摸对象(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="a9603-153">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="a9603-154">添加“手动交互平移缩放(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="a9603-154">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="a9603-155">添加要滚动的 2D 内容</span><span class="sxs-lookup"><span data-stu-id="a9603-155">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="a9603-156">添加要滚动的 3D 内容</span><span class="sxs-lookup"><span data-stu-id="a9603-156">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="a9603-157">添加“平移移动(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="a9603-157">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="a9603-158">MRTK 中未包含“平移移动(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="a9603-158">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a9603-159">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="a9603-159">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="a9603-160">1.创建可用于平移的 Quad 对象</span><span class="sxs-lookup"><span data-stu-id="a9603-160">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="a9603-161">在“层次结构”窗口中右键单击某个空白区域，然后选择“3D 对象” > “Quad”，将一个四面体添加到场景中。 </span><span class="sxs-lookup"><span data-stu-id="a9603-161">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="a9603-162">为此对象指定适当的名称（例如 **PanGesture**），并将其定位在合适的位置，例如 X = 0，Y = -0.2，Z = 2。</span><span class="sxs-lookup"><span data-stu-id="a9603-162">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="a9603-164">有关如何在场景中添加 Unity 基元（例如 3D 四面体）的提示，可参阅[将立方体添加到场景](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)中的说明。</span><span class="sxs-lookup"><span data-stu-id="a9603-164">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="a9603-165">与任何其他交互方式一样，平移手势也需要一个碰撞体。</span><span class="sxs-lookup"><span data-stu-id="a9603-165">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="a9603-166">默认情况下，四面体具有网格碰撞体。</span><span class="sxs-lookup"><span data-stu-id="a9603-166">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="a9603-167">但是，该网格碰撞体并不理想，因为它非常小。</span><span class="sxs-lookup"><span data-stu-id="a9603-167">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="a9603-168">为使用户能够更轻松地与碰撞体交互，我们将使用一个盒碰撞体替换网格碰撞体。</span><span class="sxs-lookup"><span data-stu-id="a9603-168">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="a9603-169">在仍选中了 PanGesture 对象的情况下，单击“网格碰撞体”组件的“设置”图标，然后选择“删除组件”以删除网格碰撞体：  </span><span class="sxs-lookup"><span data-stu-id="a9603-169">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="a9603-171">在“检查器”窗口中，使用“添加组件”按钮添加一个**盒碰撞体**，然后将盒碰撞体的 Z 轴“大小”更改为 0.15，以增大盒碰撞体的厚度： </span><span class="sxs-lookup"><span data-stu-id="a9603-171">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="a9603-173">2.添加“近距交互可触摸对象(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="a9603-173">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="a9603-174">在仍选中了“PanGesture”对象的情况下，将“近距交互可触摸(脚本)”组件添加到 PanGesture 对象，然后单击“拟合边界”和“拟合中点”按钮，以更新“近距交互可触摸(脚本)”组件的“局部中点”和“边界”属性，使之与 BoxCollider 匹配：   </span><span class="sxs-lookup"><span data-stu-id="a9603-174">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="a9603-176">3.添加“手动交互平移缩放(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="a9603-176">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="a9603-177">在仍选中了“PanGesture”对象的情况下，将“手动交互平移缩放(脚本)”组件添加到 PanGesture 对象，然后选中“水平锁定”复选框，以便仅允许垂直滚动：  </span><span class="sxs-lookup"><span data-stu-id="a9603-177">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="a9603-179">4.添加要滚动的 2D 内容</span><span class="sxs-lookup"><span data-stu-id="a9603-179">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="a9603-180">在“项目”面板中搜索 **PanContent** 材料，然后单击并将其拖放到“PanGesture”对象的网格渲染器“材料”元素 0 属性： </span><span class="sxs-lookup"><span data-stu-id="a9603-180">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="a9603-182">在“检查器”窗口中，展开新添加的“PanContent”材料组件，然后将其“图块”Y 轴值更改为 0.5，使之与 X 轴值匹配，并使图块显示为正方形： </span><span class="sxs-lookup"><span data-stu-id="a9603-182">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="a9603-184">如果现在进入“游戏”模式，可以使用编辑器中模拟功能的平移手势来测试滚动 2D 内容：</span><span class="sxs-lookup"><span data-stu-id="a9603-184">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="a9603-186">5.添加要滚动的 3D 内容</span><span class="sxs-lookup"><span data-stu-id="a9603-186">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="a9603-187">在“层次结构”窗口中，**创建四个立方体**作为 **PanGesture** 对象的子对象，并将其变换**标度**设置为 X = 0.15，Y = 0.15，Z = 0.15：</span><span class="sxs-lookup"><span data-stu-id="a9603-187">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="a9603-189">若要均匀隔开立方体并节省时间，请将“网格对象集合(脚本)”组件添加到立方体的父对象（即 **PanGesture** 对象），并按如下所述配置“网格对象集合(脚本)”：</span><span class="sxs-lookup"><span data-stu-id="a9603-189">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="a9603-190">将“行数”更改为 1，使所有立方体在一行中对齐</span><span class="sxs-lookup"><span data-stu-id="a9603-190">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="a9603-191">将“单元格宽度”更改为 0.25，以隔开行中的立方体</span><span class="sxs-lookup"><span data-stu-id="a9603-191">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="a9603-192">然后单击“更新集合”按钮以应用新配置：</span><span class="sxs-lookup"><span data-stu-id="a9603-192">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="a9603-194">6.添加“平移移动(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="a9603-194">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="a9603-195">在“层次结构”窗口中选择所有**立方体子对象**，然后在“检查器”窗口中，使用“添加组件”按钮将“平移移动(脚本)”组件添加到所有立方体： </span><span class="sxs-lookup"><span data-stu-id="a9603-195">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="a9603-197">有关如何在“层次结构”窗口中选择多个对象的提示，可参阅[将“操作处理程序(脚本)”组件添加到所有对象](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)中的说明。</span><span class="sxs-lookup"><span data-stu-id="a9603-197">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="a9603-198">在仍选中了所有立方体的情况下，单击“PanGesture”对象并将其拖放到“平移输入源”字段中： </span><span class="sxs-lookup"><span data-stu-id="a9603-198">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="a9603-200">每个立方体上的“平移移动(脚本)”组件将会侦听 PanGesture 对象（在上一步骤中已将其分配为“平移输入源”）上的“HandInteractionPanZoom (脚本)”组件发送的 Pan Updated 事件，并相应地更新每个立方体的位置。</span><span class="sxs-lookup"><span data-stu-id="a9603-200">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="a9603-201">在“层次结构”窗口中选择“PanGesture”对象，然后在“检查器”中**取消选中**“网格渲染器”复选框，以禁用“网格渲染器”组件： </span><span class="sxs-lookup"><span data-stu-id="a9603-201">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="a9603-203">如果现在进入“游戏”模式，可以使用编辑器中模拟功能的平移手势来测试滚动 3D 内容：</span><span class="sxs-lookup"><span data-stu-id="a9603-203">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="a9603-205">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="a9603-205">Eye Tracking</span></span>

<span data-ttu-id="a9603-206">本部分探讨如何在项目中启用眼动跟踪。</span><span class="sxs-lookup"><span data-stu-id="a9603-206">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="a9603-207">此示例将实现相应的功能，使 3DObjectCollection 中的每个对象在用户视线的注视下缓慢旋转，并在通过隔空敲击或语音命令选择要注视的对象时触发光点效果。</span><span class="sxs-lookup"><span data-stu-id="a9603-207">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="a9603-208">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="a9603-208">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="a9603-209">将“眼动跟踪目标(脚本)”组件添加到所有目标对象</span><span class="sxs-lookup"><span data-stu-id="a9603-209">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="a9603-210">将“眼动跟踪教程演示(脚本)”组件添加到所有目标对象</span><span class="sxs-lookup"><span data-stu-id="a9603-210">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="a9603-211">实现 While Looking At Target 事件</span><span class="sxs-lookup"><span data-stu-id="a9603-211">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="a9603-212">实现 On Selected 事件</span><span class="sxs-lookup"><span data-stu-id="a9603-212">Implement the On Selected event</span></span>
5. <span data-ttu-id="a9603-213">为编辑器中的模拟启用模拟眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="a9603-213">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="a9603-214">在 Visual Studio 项目的应用功能中启用视线输入</span><span class="sxs-lookup"><span data-stu-id="a9603-214">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="a9603-215">1.将“眼动跟踪目标(脚本)”组件添加到所有目标对象</span><span class="sxs-lookup"><span data-stu-id="a9603-215">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="a9603-216">在“层次结构”窗口中展开“3DObjectCollection”对象并选择所有**子对象**，然后在“检查器”窗口中，使用“添加组件”按钮将“眼动跟踪目标(脚本)”组件添加到所有子对象：  </span><span class="sxs-lookup"><span data-stu-id="a9603-216">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="a9603-218">在仍选中了所有**子对象**的情况下，按如下所述配置“眼动跟踪目标(脚本)”组件：</span><span class="sxs-lookup"><span data-stu-id="a9603-218">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="a9603-219">将“选择操作”更改为“选择”，以将此对象的隔空敲击操作定义为“选择” </span><span class="sxs-lookup"><span data-stu-id="a9603-219">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="a9603-220">展开“语音选择”并将语音命令列表的“大小”设置为 1，然后在显示的新元素列表中，将“元素 0”更改为“选择”，以将此对象的语音命令操作定义为“选择”   </span><span class="sxs-lookup"><span data-stu-id="a9603-220">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="a9603-222">2.将“眼动跟踪教程演示(脚本)”组件添加到所有目标对象</span><span class="sxs-lookup"><span data-stu-id="a9603-222">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="a9603-223">在仍选中了所有**子对象**的情况下，使用“添加组件”按钮将“眼动跟踪教程演示(脚本)”组件添加到所有子对象： </span><span class="sxs-lookup"><span data-stu-id="a9603-223">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="a9603-225">MRTK 中不包含“眼动跟踪目标(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="a9603-225">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a9603-226">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="a9603-226">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="a9603-227">3.实现 While Looking At Target 事件</span><span class="sxs-lookup"><span data-stu-id="a9603-227">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="a9603-228">在“层次结构”窗口中选择“Cheese”对象，创建一个新的 **While Looking At Target ()** 事件，将“Cheese”对象配置为接收该事件，然后将“EyeTrackingTutorialDemo.RotateTarget”定义为要触发的操作：  </span><span class="sxs-lookup"><span data-stu-id="a9603-228">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="a9603-230">针对 3DObjectCollection 中的每个子对象**重复**上述步骤。</span><span class="sxs-lookup"><span data-stu-id="a9603-230">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="a9603-231">有关如何实现事件的提示，可参阅[手动跟踪手势和可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)中的说明。</span><span class="sxs-lookup"><span data-stu-id="a9603-231">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="a9603-232">4.实现 On Selected 事件</span><span class="sxs-lookup"><span data-stu-id="a9603-232">4. Implement the On Selected event</span></span>

<span data-ttu-id="a9603-233">在“层次结构”窗口中选择“Cheese”对象，创建一个新的 **On Selected ()** 事件，将“Cheese”对象配置为接收该事件，然后将“EyeTrackingTutorialDemo.BlipTarget”定义为要触发的操作：  </span><span class="sxs-lookup"><span data-stu-id="a9603-233">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="a9603-235">针对 3DObjectCollection 中的每个子对象**重复**上述步骤。</span><span class="sxs-lookup"><span data-stu-id="a9603-235">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="a9603-236">5.为编辑器中的模拟启用模拟眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="a9603-236">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="a9603-237">在“层次结构”窗口中选择“MixedRealityToolkit”对象，在“检查器”窗口中选择“输入”选项卡，展开“输入数据提供程序”部分，展开“输入模拟服务”部分，然后克隆“DefaultMixedRealityInputSimulationProfile”，以将其替换为你自己的可自定义**输入模拟配置文件**：    </span><span class="sxs-lookup"><span data-stu-id="a9603-237">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="a9603-239">有关如何克隆 MRTK 配置文件的提示，可参阅[如何配置混合现实工具包配置文件](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明。</span><span class="sxs-lookup"><span data-stu-id="a9603-239">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="a9603-240">在“眼动模拟”部分，选中“模拟眼睛位置”复选框以启用眼动跟踪模拟： </span><span class="sxs-lookup"><span data-stu-id="a9603-240">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="a9603-242">如果现在进入“游戏”模式，可以测试实现的旋转和光点效果，方法是调整视图，使游标位于某个对象上，然后使用手动交互或语音命令来选择对象：</span><span class="sxs-lookup"><span data-stu-id="a9603-242">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="a9603-244">如果尚未根据[配置混合现实工具包](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)中的说明使用 DefaultHoloLens2ConfigurationProfile 克隆可自定义的 MRTK 配置配置文件，则眼动跟踪可能未在项目中启用，现在需要启用。</span><span class="sxs-lookup"><span data-stu-id="a9603-244">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="a9603-245">为此，可参阅 [MRTK 中的眼动跟踪入门](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)中的说明。</span><span class="sxs-lookup"><span data-stu-id="a9603-245">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="a9603-246">6.在 Visual Studio 项目的应用功能中启用视线输入</span><span class="sxs-lookup"><span data-stu-id="a9603-246">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="a9603-247">在从 Visual Studio 生成应用并将其部署到设备之前，必须在项目的应用功能中启用“视线输入”。</span><span class="sxs-lookup"><span data-stu-id="a9603-247">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="a9603-248">为此，可以按照[在 HoloLens 2 上测试 Unity 应用](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="a9603-248">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a9603-249">祝贺</span><span class="sxs-lookup"><span data-stu-id="a9603-249">Congratulations</span></span>

<span data-ttu-id="a9603-250">现已将基本的眼动跟踪功能成功添加到应用程序。</span><span class="sxs-lookup"><span data-stu-id="a9603-250">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="a9603-251">这些操作仅为眼动跟踪实现的探索领域开了一个头。</span><span class="sxs-lookup"><span data-stu-id="a9603-251">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="a9603-252">本教程还介绍了其他高级输入功能，例如语音命令和平移手势。</span><span class="sxs-lookup"><span data-stu-id="a9603-252">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="a9603-253">下一课：7.创建农历模块示例应用程序</span><span class="sxs-lookup"><span data-stu-id="a9603-253">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
