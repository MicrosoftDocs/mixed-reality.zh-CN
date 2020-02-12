---
title: 入门教程-6。 浏览高级输入选项
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129596"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="96ae2-105">6. 浏览高级输入选项</span><span class="sxs-lookup"><span data-stu-id="96ae2-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="96ae2-106">在本教程中，你将了解 HoloLens 2 的几个高级输入选项，包括使用语音命令、平移手势和目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="96ae2-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="96ae2-107">目标</span><span class="sxs-lookup"><span data-stu-id="96ae2-107">Objectives</span></span>

* <span data-ttu-id="96ae2-108">使用声音命令和关键字触发事件</span><span class="sxs-lookup"><span data-stu-id="96ae2-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="96ae2-109">使用跟踪的指针通过跟踪的手平移纹理和3D 对象</span><span class="sxs-lookup"><span data-stu-id="96ae2-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="96ae2-110">利用 HoloLens 2 目视跟踪功能选择对象</span><span class="sxs-lookup"><span data-stu-id="96ae2-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="96ae2-111">启用语音命令</span><span class="sxs-lookup"><span data-stu-id="96ae2-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="96ae2-112">在本部分中，你将实现一个语音命令，让用户在八对象上播放声音。</span><span class="sxs-lookup"><span data-stu-id="96ae2-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="96ae2-113">为此，您将创建一个新的语音命令，然后配置该事件，以便在口述语音命令关键字时触发所需的操作。</span><span class="sxs-lookup"><span data-stu-id="96ae2-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="96ae2-114">为实现此目的需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="96ae2-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="96ae2-115">克隆默认输入系统配置文件</span><span class="sxs-lookup"><span data-stu-id="96ae2-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="96ae2-116">克隆默认的语音命令配置文件</span><span class="sxs-lookup"><span data-stu-id="96ae2-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="96ae2-117">创建新的语音命令</span><span class="sxs-lookup"><span data-stu-id="96ae2-117">Create a new speech command</span></span>
4. <span data-ttu-id="96ae2-118">添加和配置语音输入处理程序（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="96ae2-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="96ae2-119">实现语音命令的响应事件</span><span class="sxs-lookup"><span data-stu-id="96ae2-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="96ae2-120">1. 克隆默认输入系统配置文件</span><span class="sxs-lookup"><span data-stu-id="96ae2-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="96ae2-121">在 "层次结构" 窗口中，选择 " **MixedRealityToolkit** " 对象，然后在 "检查器" 窗口中，选择 "**输入**" 选项卡并克隆**DefaultHoloLens2InputSystemProfile** ，将其替换为你自己的可自定义**输入系统配置文件**：</span><span class="sxs-lookup"><span data-stu-id="96ae2-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="96ae2-123">有关如何克隆 MRTK 配置文件的提醒，可以参阅[如何配置混合现实工具包配置文件](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)说明。</span><span class="sxs-lookup"><span data-stu-id="96ae2-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="96ae2-124">2. 克隆默认语音命令配置文件</span><span class="sxs-lookup"><span data-stu-id="96ae2-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="96ae2-125">展开 "**语音**" 部分，克隆**DefaultMixedRealitySpeechCommandsProfile**以将其替换为你自己的可自定义**语音命令配置文件**：</span><span class="sxs-lookup"><span data-stu-id="96ae2-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="96ae2-127">3. 创建新的语音命令</span><span class="sxs-lookup"><span data-stu-id="96ae2-127">3. Create a new speech command</span></span>

<span data-ttu-id="96ae2-128">在 "**语音命令**" 部分中，单击 " **+ 添加新语音命令**" 按钮，在现有语音命令列表的底部添加新的语音命令，然后在**关键字**字段中输入合适的词或短语，例如**播放音乐**：</span><span class="sxs-lookup"><span data-stu-id="96ae2-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="96ae2-130">如果您的计算机没有麦克风，并且您想要使用编辑器内模拟来测试语音命令，则可以将 KeyCode 分配给语音命令，以便在按下相应的键时触发它。</span><span class="sxs-lookup"><span data-stu-id="96ae2-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="96ae2-131">4. 添加和配置语音输入处理程序（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="96ae2-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="96ae2-132">在 "层次结构" 窗口中，选择 "**八**" 对象，并将**语音输入处理程序（脚本）** 组件添加到八对象。</span><span class="sxs-lookup"><span data-stu-id="96ae2-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="96ae2-133">然后取消选中 "**是否需要焦点**" 复选框，以便用户无需查看八对象即可触发语音命令：</span><span class="sxs-lookup"><span data-stu-id="96ae2-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="96ae2-135">5. 实现语音命令的响应事件</span><span class="sxs-lookup"><span data-stu-id="96ae2-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="96ae2-136">在语音输入处理程序（脚本）组件上，单击 "小 **+** " 按钮添加关键字，然后在 "**关键字**" 下拉列表中，选择之前创建的 "**播放音乐**" 关键字：</span><span class="sxs-lookup"><span data-stu-id="96ae2-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="96ae2-138">关键字下拉列表中的关键字根据语音命令配置文件中的 "语音命令" 列表中定义的关键字进行填充。</span><span class="sxs-lookup"><span data-stu-id="96ae2-138">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="96ae2-139">创建新的**响应（）** 事件，配置**八**对象以接收事件，将**AudioSource**定义为要触发的操作，并将适当的音频剪辑分配给**音频剪辑**字段，例如 MRTK_Gem 音频剪辑：</span><span class="sxs-lookup"><span data-stu-id="96ae2-139">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> <span data-ttu-id="96ae2-141">若要提醒如何实现事件和分配音频剪辑，可以参阅按[触控开始执行事件](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)说明。</span><span class="sxs-lookup"><span data-stu-id="96ae2-141">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="96ae2-142">平移手势</span><span class="sxs-lookup"><span data-stu-id="96ae2-142">The Pan Gesture</span></span>

<span data-ttu-id="96ae2-143">平移手势对于使用手指或手滚动内容滚动很有用。</span><span class="sxs-lookup"><span data-stu-id="96ae2-143">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="96ae2-144">在此示例中，您将首先了解如何滚动 2D UI，然后将其展开以便能够滚动浏览三维对象的集合。</span><span class="sxs-lookup"><span data-stu-id="96ae2-144">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="96ae2-145">为实现此目的需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="96ae2-145">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="96ae2-146">创建可用于平移的四个对象</span><span class="sxs-lookup"><span data-stu-id="96ae2-146">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="96ae2-147">添加 Near 交互可触摸（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="96ae2-147">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="96ae2-148">添加手写交互平移缩放（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="96ae2-148">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="96ae2-149">添加要滚动的2D 内容</span><span class="sxs-lookup"><span data-stu-id="96ae2-149">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="96ae2-150">添加三维内容滚动</span><span class="sxs-lookup"><span data-stu-id="96ae2-150">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="96ae2-151">添加带平移（脚本）组件的移动</span><span class="sxs-lookup"><span data-stu-id="96ae2-151">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="96ae2-152">带平移（脚本）组件的移动不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="96ae2-152">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="96ae2-153">本教程提供了本教程的资产。</span><span class="sxs-lookup"><span data-stu-id="96ae2-153">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="96ae2-154">1. 创建可用于平移的四个对象</span><span class="sxs-lookup"><span data-stu-id="96ae2-154">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="96ae2-155">在 "层次结构" 窗口中，右键单击空白区域，并选择 " **3D 对象** > **四**个"，将 "四个" 添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="96ae2-155">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="96ae2-156">为它提供适当的名称（例如**PanGesture**），并将其放置在合适的位置，例如 X = 0、Y =-0.2、Z = 2。</span><span class="sxs-lookup"><span data-stu-id="96ae2-156">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="96ae2-158">有关如何向场景中添加 Unity 基元（如三维四类）的提醒，可以参阅[将多维数据集添加到场景](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)说明。</span><span class="sxs-lookup"><span data-stu-id="96ae2-158">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="96ae2-159">与任何其他交互一样，平移手势还需要碰撞器。</span><span class="sxs-lookup"><span data-stu-id="96ae2-159">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="96ae2-160">默认情况下，四个网络有一个网格碰撞器。</span><span class="sxs-lookup"><span data-stu-id="96ae2-160">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="96ae2-161">但是，网格碰撞器并不理想，因为它非常精简。</span><span class="sxs-lookup"><span data-stu-id="96ae2-161">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="96ae2-162">为了使用户能够更轻松地与碰撞器进行交互，我们将使用箱碰撞器替换网格碰撞器。</span><span class="sxs-lookup"><span data-stu-id="96ae2-162">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="96ae2-163">在仍选择 PanGesture 对象的情况下，单击**网格碰撞**器组件的**设置**图标，然后选择 "**删除组件**" 以删除网格碰撞器：</span><span class="sxs-lookup"><span data-stu-id="96ae2-163">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="96ae2-165">在 "检查器" 窗口中，使用 "**添加组件**" 按钮添加一个**框碰撞**器，然后将 box 碰撞器**大小**Z 改为0.15 以增加框碰撞器的厚度：</span><span class="sxs-lookup"><span data-stu-id="96ae2-165">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="96ae2-167">2. 添加 Near 交互可触摸（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="96ae2-167">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="96ae2-168">在仍选择**PanGesture**对象的情况下，将**near 交互可触摸（脚本）** 组件添加到 PanGesture 对象，然后单击 "**修复边界**" 和 "**修复中心**" 按钮，更新接近交互可触摸（脚本）的局部中心和边界属性，使之与 BoxCollider 匹配：</span><span class="sxs-lookup"><span data-stu-id="96ae2-168">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="96ae2-170">3. 添加手写交互平移缩放（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="96ae2-170">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="96ae2-171">在仍选择**PanGesture**对象的情况下，将**手写交互平移缩放（脚本）** 组件添加到 PanGesture 对象，然后选中 "**锁定水平**" 复选框以仅允许垂直滚动：</span><span class="sxs-lookup"><span data-stu-id="96ae2-171">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="96ae2-173">4. 添加要滚动的2D 内容</span><span class="sxs-lookup"><span data-stu-id="96ae2-173">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="96ae2-174">在 "项目" 面板中，搜索**PanContent**材料，然后单击并将其拖动到**PanGesture**对象的 "网状呈现器**材料**元素 0" 属性：</span><span class="sxs-lookup"><span data-stu-id="96ae2-174">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="96ae2-176">在 "检查器" 窗口中，展开新添加的 " **PanContent**材料" 组件，然后将其 "**平铺**Y" 值更改为0.5，使其与 X 值匹配，磁贴显示为方形：</span><span class="sxs-lookup"><span data-stu-id="96ae2-176">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="96ae2-178">如果你现在进入游戏模式，则可以使用编辑器内模拟中的平移手势来测试是否滚动2D 内容：</span><span class="sxs-lookup"><span data-stu-id="96ae2-178">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="96ae2-180">5. 添加要滚动的3D 内容</span><span class="sxs-lookup"><span data-stu-id="96ae2-180">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="96ae2-181">在 "层次结构" 窗口中，将**四个多维数据集创建**为**PanContent**的子对象，并将其转换**比例**设置为 X = 0.15，Y = 0.15，Z = 0.15：</span><span class="sxs-lookup"><span data-stu-id="96ae2-181">In the Hierarchy window, **create four cubes** as a child objects of the **PanContent** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="96ae2-183">若要将多维数据集均匀地缩小，并保存一些时间，请将网格对象集合（脚本）组件添加到多维数据集的父对象（即 PanGesture 对象），并按如下所示配置网格对象集合（脚本）：</span><span class="sxs-lookup"><span data-stu-id="96ae2-183">To space the cubes out evenly, and save some time, add the Grid Object Collection (Script) component, to the cubes' parent object, i.e. the PanGesture object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="96ae2-184">将**Num 行**更改为1，使所有多维数据集在一行上对齐</span><span class="sxs-lookup"><span data-stu-id="96ae2-184">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="96ae2-185">将**单元格宽度**更改为0.25，以将行内的多维数据集变为空白</span><span class="sxs-lookup"><span data-stu-id="96ae2-185">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="96ae2-186">然后单击 "**更新集合**" 按钮应用新配置：</span><span class="sxs-lookup"><span data-stu-id="96ae2-186">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="96ae2-188">6. 添加带平移（脚本）组件的移动</span><span class="sxs-lookup"><span data-stu-id="96ae2-188">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="96ae2-189">在 "层次结构" 窗口中，选择所有**多维数据集子对象**，然后在 "检查器" 窗口中，使用 "**添加组件**" 按钮将**Move （Script）** 组件添加到所有多维数据集：</span><span class="sxs-lookup"><span data-stu-id="96ae2-189">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="96ae2-191">有关如何在 "层次结构" 窗口中选择多个对象的提醒，tou 可以参考[将操作处理程序（脚本）组件添加到所有对象](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)指令中。</span><span class="sxs-lookup"><span data-stu-id="96ae2-191">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="96ae2-192">在仍选择了所有多维数据集的情况下，单击 " **PanGesture** " 对象并将其拖至 "**平移输入源**" 字段：</span><span class="sxs-lookup"><span data-stu-id="96ae2-192">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="96ae2-194">每个多维数据集上的 "在移动时使用平移（脚本）" 组件会侦听 PanGesture 对象上的 HandInteractionPanZoom （Script）组件发送的平移更新事件，在上面的步骤中已将该对象指定为平移输入源，并更新每个多维数据集的位置并.</span><span class="sxs-lookup"><span data-stu-id="96ae2-194">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="96ae2-195">在 "层次结构" 窗口中，选择 " **PanGesture** " 对象，然后在 "检查器" 中**取消选中**"**网格呈现**器" 复选框，以禁用网格呈现器组件：</span><span class="sxs-lookup"><span data-stu-id="96ae2-195">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="96ae2-197">如果你现在进入游戏模式，则可以使用编辑器内模拟中的平移手势测试滚动3D 内容：</span><span class="sxs-lookup"><span data-stu-id="96ae2-197">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="96ae2-199">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="96ae2-199">Eye Tracking</span></span>

<span data-ttu-id="96ae2-200">在本部分中，你将了解如何在项目中启用目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="96ae2-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="96ae2-201">在此示例中，你将实现一些功能，使3DObjectCollection 中的每个对象在用户眼睛眼睛查看时慢慢旋转，并在通过 "轻敲" 或 "语音" 命令选择要查看的对象时触发故障效果。</span><span class="sxs-lookup"><span data-stu-id="96ae2-201">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="96ae2-202">为实现此目的需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="96ae2-202">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="96ae2-203">将目视跟踪目标（脚本）组件添加到所有目标对象</span><span class="sxs-lookup"><span data-stu-id="96ae2-203">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="96ae2-204">将目视跟踪教程演示（脚本）组件添加到所有目标对象</span><span class="sxs-lookup"><span data-stu-id="96ae2-204">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="96ae2-205">在查看目标事件时实现</span><span class="sxs-lookup"><span data-stu-id="96ae2-205">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="96ae2-206">实现所选事件</span><span class="sxs-lookup"><span data-stu-id="96ae2-206">Implement the On Selected event</span></span>
5. <span data-ttu-id="96ae2-207">为编辑器内模拟启用模拟的目视跟踪</span><span class="sxs-lookup"><span data-stu-id="96ae2-207">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="96ae2-208">在 Visual Studio 项目的应用功能中启用注视输入</span><span class="sxs-lookup"><span data-stu-id="96ae2-208">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="96ae2-209">1. 将目视跟踪目标（脚本）组件添加到所有目标对象</span><span class="sxs-lookup"><span data-stu-id="96ae2-209">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="96ae2-210">在 "层次结构" 窗口中，展开 " **3DObjectCollection** " 对象并选择所有**子对象**，然后在 "检查器" 窗口中，使用 "**添加组件**" 按钮将**眼睛跟踪目标（脚本）** 组件添加到所有子对象：</span><span class="sxs-lookup"><span data-stu-id="96ae2-210">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="96ae2-212">在仍选择所有**子对象**的情况下，按如下所示配置**目视跟踪目标（脚本）** 组件：</span><span class="sxs-lookup"><span data-stu-id="96ae2-212">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="96ae2-213">更改**选择操作**以**选择**，将此对象的 "空中点击" 操作定义为 "选择"</span><span class="sxs-lookup"><span data-stu-id="96ae2-213">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="96ae2-214">展开**语音选择**，将语音命令列表**大小**设置为1，然后在显示的新元素列表中，将**元素 0**更改为**选择**，以将此对象的语音命令操作定义为 "选择"</span><span class="sxs-lookup"><span data-stu-id="96ae2-214">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="96ae2-216">2. 将目视跟踪教程演示（脚本）组件添加到所有目标对象</span><span class="sxs-lookup"><span data-stu-id="96ae2-216">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="96ae2-217">在仍选择所有**子对象**的情况下，使用 "**添加组件**" 按钮将**目视跟踪教程演示（脚本）** 组件添加到所有子对象：</span><span class="sxs-lookup"><span data-stu-id="96ae2-217">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="96ae2-219">眼睛跟踪目标（脚本）组件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="96ae2-219">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="96ae2-220">本教程提供了本教程的资产。</span><span class="sxs-lookup"><span data-stu-id="96ae2-220">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="96ae2-221">3. 在查看目标事件时实现</span><span class="sxs-lookup"><span data-stu-id="96ae2-221">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="96ae2-222">在 "层次结构" 窗口中，选择 "**奶酪**" 对象，然后在 "**查看目标（）** " 事件时创建一个新的，配置**奶酪**对象以接收事件，并将**EyeTrackingTutorialDemo**定义为要触发的操作：</span><span class="sxs-lookup"><span data-stu-id="96ae2-222">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="96ae2-224">对3DObjectCollection 中的每个子对象**重复**此操作。</span><span class="sxs-lookup"><span data-stu-id="96ae2-224">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="96ae2-225">有关如何实现事件的提醒，可参阅 "[手动跟踪手势" 和 "种不可交互" 按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)说明。</span><span class="sxs-lookup"><span data-stu-id="96ae2-225">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="96ae2-226">4. 实现所选事件</span><span class="sxs-lookup"><span data-stu-id="96ae2-226">4. Implement the On Selected event</span></span>

<span data-ttu-id="96ae2-227">在 "层次结构" 窗口中，选择 "**奶酪**" 对象，然后**在所选（）事件上**创建新的，将**奶酪**对象配置为接收事件，并将**EyeTrackingTutorialDemo**定义为要触发的操作：</span><span class="sxs-lookup"><span data-stu-id="96ae2-227">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="96ae2-229">对3DObjectCollection 中的每个子对象**重复**此操作。</span><span class="sxs-lookup"><span data-stu-id="96ae2-229">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="96ae2-230">5. 为编辑器内模拟启用模拟的目视跟踪</span><span class="sxs-lookup"><span data-stu-id="96ae2-230">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="96ae2-231">在 "层次结构" 窗口中，选择 " **MixedRealityToolkit** " 对象，然后在 "检查器" 窗口中，选择 "**输入**" 选项卡，展开 "**输入数据访问接口**" 部分，然后展开 "**输入模拟服务**" 部分，并克隆**DefaultMixedRealityInputSimulationProfile** ，将其替换为你自己的可自定义**输入模拟配置文件**：</span><span class="sxs-lookup"><span data-stu-id="96ae2-231">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="96ae2-233">有关如何克隆 MRTK 配置文件的提醒，可以参阅[如何配置混合现实工具包配置文件](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)说明。</span><span class="sxs-lookup"><span data-stu-id="96ae2-233">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="96ae2-234">在 "**目视模拟**" 部分中，选中 "**模拟眼睛位置**" 复选框以启用目视跟踪模拟：</span><span class="sxs-lookup"><span data-stu-id="96ae2-234">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="96ae2-236">如果你现在进入游戏模式，则可以通过调整视图来测试你实现的旋转和故障效果，使光标点击其中一个对象，并使用 "手动交互" 或 "语音" 命令选择对象：</span><span class="sxs-lookup"><span data-stu-id="96ae2-236">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="96ae2-238">如果未使用 DefaultHoloLens2ConfigurationProfile 克隆可自定义的 MRTK 配置文件，如[配置混合现实工具包](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)说明中所述，可能无法在项目中启用目视跟踪并且需要启用。</span><span class="sxs-lookup"><span data-stu-id="96ae2-238">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="96ae2-239">为此，可以参阅[MRTK 说明中的目视跟踪](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)入门。</span><span class="sxs-lookup"><span data-stu-id="96ae2-239">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="96ae2-240">6. 在 Visual Studio 项目的应用功能中启用注视输入</span><span class="sxs-lookup"><span data-stu-id="96ae2-240">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="96ae2-241">在从 Visual Studio 生成应用并将其部署到设备之前，必须在项目的应用功能中启用 "注视输入"。</span><span class="sxs-lookup"><span data-stu-id="96ae2-241">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="96ae2-242">为此，可以按照[HoloLens 2 说明测试 Unity 应用](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="96ae2-242">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="96ae2-243">祝贺你</span><span class="sxs-lookup"><span data-stu-id="96ae2-243">Congratulations</span></span>

<span data-ttu-id="96ae2-244">已成功将基本的目视跟踪功能添加到应用程序。</span><span class="sxs-lookup"><span data-stu-id="96ae2-244">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="96ae2-245">这些操作仅为眼动跟踪实现的探索领域开了一个头。</span><span class="sxs-lookup"><span data-stu-id="96ae2-245">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="96ae2-246">在本教程中，您还了解了其他高级输入功能，如语音命令和平移手势。</span><span class="sxs-lookup"><span data-stu-id="96ae2-246">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="96ae2-247">下一课： 7. 创建农历模块示例应用程序</span><span class="sxs-lookup"><span data-stu-id="96ae2-247">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
