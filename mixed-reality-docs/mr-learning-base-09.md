---
title: 入门教程 - 9. 使用语音命令
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0b9771d9569d100a354af96a34cd20ef2a3d7c4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376589"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="b967b-105">9.使用语音命令</span><span class="sxs-lookup"><span data-stu-id="b967b-105">9. Using speech commands</span></span>

## <a name="overview"></a><span data-ttu-id="b967b-106">概述</span><span class="sxs-lookup"><span data-stu-id="b967b-106">Overview</span></span>

<span data-ttu-id="b967b-107">本教程将介绍如何创建语音命令，以及如何在全局范围内对其进行控制。</span><span class="sxs-lookup"><span data-stu-id="b967b-107">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="b967b-108">还将介绍如何控制需要用户查看控制语音命令的对象的本地语音命令。</span><span class="sxs-lookup"><span data-stu-id="b967b-108">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="b967b-109">目标</span><span class="sxs-lookup"><span data-stu-id="b967b-109">Objectives</span></span>

* <span data-ttu-id="b967b-110">了解如何创建语音命令</span><span class="sxs-lookup"><span data-stu-id="b967b-110">Learn how to create speech commands</span></span>
* <span data-ttu-id="b967b-111">了解如何在全局和本地控制语音命令</span><span class="sxs-lookup"><span data-stu-id="b967b-111">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="b967b-112">确保启用麦克风功能</span><span class="sxs-lookup"><span data-stu-id="b967b-112">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="b967b-113">在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：</span><span class="sxs-lookup"><span data-stu-id="b967b-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b967b-115">在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings)指令期间，应该已经启用了麦克风功能。</span><span class="sxs-lookup"><span data-stu-id="b967b-115">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="b967b-116">但如果未启用此功能，请确保立即启用。</span><span class="sxs-lookup"><span data-stu-id="b967b-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="b967b-117">创建语音命令</span><span class="sxs-lookup"><span data-stu-id="b967b-117">Creating speech commands</span></span>

<span data-ttu-id="b967b-118">在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：</span><span class="sxs-lookup"><span data-stu-id="b967b-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="b967b-119">展开“语音”部分</span><span class="sxs-lookup"><span data-stu-id="b967b-119">Expand the **Speech** section</span></span>
* <span data-ttu-id="b967b-120">克隆 DefaultMixedRealitySpeechCommandsProfile 并为其指定一个适当的名称，例如 GettingStarted_MixedRealitySpeechCommandsProfile</span><span class="sxs-lookup"><span data-stu-id="b967b-120">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="b967b-121">验证“启动行为”是否设置为“自动启动” </span><span class="sxs-lookup"><span data-stu-id="b967b-121">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="b967b-123">有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="b967b-123">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="b967b-124">在“语音”>“语音命令”部分，单击“+ 添加新的语音命令”按钮四次，以在现有语音命令列表种添加四个新的语音命令，然后在“关键字”字段中输入以下短语  ：</span><span class="sxs-lookup"><span data-stu-id="b967b-124">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="b967b-125">启用指示器</span><span class="sxs-lookup"><span data-stu-id="b967b-125">Enable Indicator</span></span>
* <span data-ttu-id="b967b-126">启用点击放置</span><span class="sxs-lookup"><span data-stu-id="b967b-126">Enable Tap to Place</span></span>
* <span data-ttu-id="b967b-127">启用边界框</span><span class="sxs-lookup"><span data-stu-id="b967b-127">Enable Bounding Box</span></span>
* <span data-ttu-id="b967b-128">禁用边界框</span><span class="sxs-lookup"><span data-stu-id="b967b-128">Disable Bounding Box</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="b967b-130">如果计算机没有麦克风，可向语音命令分配一个 KeyCode，以便在按下相应的键时触发它们。</span><span class="sxs-lookup"><span data-stu-id="b967b-130">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="b967b-131">控制语音命令</span><span class="sxs-lookup"><span data-stu-id="b967b-131">Controlling speech commands</span></span>

<span data-ttu-id="b967b-132">在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “功能” > “UX” > “预制件” > “工具提示”文件夹，以查找工具提示预制件      ：</span><span class="sxs-lookup"><span data-stu-id="b967b-132">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="b967b-134">在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”，将空对象添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="b967b-134">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="b967b-135">将对象命名为 SpeechInputHandler_Global，然后在“检查器”窗口中，使用“添加组件”按钮添加 SpeechInputHandler 组件，并按如下所示对其进行配置  ：</span><span class="sxs-lookup"><span data-stu-id="b967b-135">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="b967b-136">取消选中“需要焦点”复选框，使用户无需查看带有 SpeechInputHandler 组件的对象即可触发语音命令 </span><span class="sxs-lookup"><span data-stu-id="b967b-136">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="b967b-137">从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 </span><span class="sxs-lookup"><span data-stu-id="b967b-137">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="b967b-139">在 SpeechInputHandler 组件上，单击小 + 图标三次，添加三个关键字元素：</span><span class="sxs-lookup"><span data-stu-id="b967b-139">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="b967b-141">展开“元素 0”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="b967b-141">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="b967b-142">在“关键字”字段中，输入“启用指示器”，以引用在上一部分中创建的“启用指示器”语音命令 </span><span class="sxs-lookup"><span data-stu-id="b967b-142">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="b967b-143">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="b967b-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b967b-144">从“层次结构”窗口中，向“无(对象)”字段分配 Indicator 对象 </span><span class="sxs-lookup"><span data-stu-id="b967b-144">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b967b-145">从“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="b967b-145">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="b967b-146">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="b967b-146">Check the argument checkbox, so it is **checked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="b967b-148">展开“元素 1”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="b967b-148">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="b967b-149">在“关键字”字段中，输入“启用边界框”，以引用在上一部分中创建的“启用边界框”命令 </span><span class="sxs-lookup"><span data-stu-id="b967b-149">In the **Keyword** field, enter **Enable Bounding Box**, to reference the Enable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="b967b-150">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="b967b-150">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b967b-151">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="b967b-151">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b967b-152">在“无函数”下拉列表中选择“BoundingBox” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="b967b-152">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b967b-153">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="b967b-153">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="b967b-154">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="b967b-154">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="b967b-155">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="b967b-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b967b-156">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="b967b-156">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b967b-157">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="b967b-157">Check the argument checkbox, so it is **checked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="b967b-159">展开“元素 2”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="b967b-159">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="b967b-160">在“关键字”字段中，输入“禁用边界框”，以引用在上一部分中创建的“禁用边界框”命令 </span><span class="sxs-lookup"><span data-stu-id="b967b-160">In the **Keyword** field, enter **Disable Bounding Box**, to reference the Disable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="b967b-161">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="b967b-161">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b967b-162">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="b967b-162">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b967b-163">在“无函数”下拉列表中选择“BoundingBox” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="b967b-163">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b967b-164">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="b967b-164">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="b967b-165">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="b967b-165">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="b967b-166">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="b967b-166">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b967b-167">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="b967b-167">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b967b-168">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="b967b-168">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="b967b-170">在“层次结构”窗口中依次选择“RoverExplorer”>“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“SpeechInputHandler”组件，并按如下所述配置该组件：  </span><span class="sxs-lookup"><span data-stu-id="b967b-170">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="b967b-171">验证是否已选中“需要焦点”复选框，使用户需要查看带有 SpeechInputHandler 组件的对象才可触发语音命令 </span><span class="sxs-lookup"><span data-stu-id="b967b-171">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="b967b-172">从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 </span><span class="sxs-lookup"><span data-stu-id="b967b-172">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="b967b-174">在 SpeechInputHandler 组件上，单击小 + 图标以添加关键字元素，展开新创建的元素，然后按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="b967b-174">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="b967b-175">在“关键字”字段中，输入“启用点击放置”，以引用在上一部分中创建的“启用点击放置”命令 </span><span class="sxs-lookup"><span data-stu-id="b967b-175">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="b967b-176">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="b967b-176">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b967b-177">从“层次结构”窗口中，将对象本身（即 RoverAssembly 对象）分配给“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="b967b-177">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="b967b-178">在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="b967b-178">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b967b-179">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="b967b-179">Check the argument checkbox, so it is **checked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="b967b-181">祝贺</span><span class="sxs-lookup"><span data-stu-id="b967b-181">Congratulations</span></span>

<span data-ttu-id="b967b-182">在本教程中，你学习了如何创建语音命令，以及如何在全局范围内对其进行控制。</span><span class="sxs-lookup"><span data-stu-id="b967b-182">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="b967b-183">还了解了如何控制需要用户查看控制语音命令的对象的本地语音命令。</span><span class="sxs-lookup"><span data-stu-id="b967b-183">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="b967b-184">[入门教程](mr-learning-base-01.md)系列到此也就结束了。</span><span class="sxs-lookup"><span data-stu-id="b967b-184">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="b967b-185">通过这些教程，你成功使用 MRTK 从头构建了一个完整的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="b967b-185">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="b967b-186">接下来的 [Azure 空间定位点](mr-learning-asa-01.md)和[多用户功能教程](mr-learning-sharing-01.md)这两个教程系列将首先介绍如何将 Azure 空间定位点集成到你的项目中，以定位在现实世界中创建的漫游者探测器体验。</span><span class="sxs-lookup"><span data-stu-id="b967b-186">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="b967b-187">然后，将介绍如何将多用户功能添加到你的项目，以实时共享用户和对象的移动情况。</span><span class="sxs-lookup"><span data-stu-id="b967b-187">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>
