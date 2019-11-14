---
title: 入门教程-6。 浏览高级输入选项
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b740c463e3d73d5df9b996562e9ff0a1952703f0
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064318"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="9c5aa-105">6. 浏览高级输入选项</span><span class="sxs-lookup"><span data-stu-id="9c5aa-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="9c5aa-106">在本教程中，将探索 HoloLens 2 的几个高级输入选项，包括使用语音命令、平移手势和目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-106">In this tutorial, several advanced input options for HoloLens 2 are explored, including the use of voice commands, panning gesture, and eye tracking.</span></span> 

## <a name="objectives"></a><span data-ttu-id="9c5aa-107">目标</span><span class="sxs-lookup"><span data-stu-id="9c5aa-107">Objectives</span></span>

- <span data-ttu-id="9c5aa-108">使用声音命令和关键字触发事件</span><span class="sxs-lookup"><span data-stu-id="9c5aa-108">Trigger events using voice commands and keywords</span></span>
- <span data-ttu-id="9c5aa-109">使用跟踪的指针通过跟踪的手平移纹理和3D 对象</span><span class="sxs-lookup"><span data-stu-id="9c5aa-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
- <span data-ttu-id="9c5aa-110">利用 HoloLens 2 目视跟踪功能选择对象</span><span class="sxs-lookup"><span data-stu-id="9c5aa-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="instructions"></a><span data-ttu-id="9c5aa-111">说明</span><span class="sxs-lookup"><span data-stu-id="9c5aa-111">Instructions</span></span>

### <a name="enabling-voice-commands"></a><span data-ttu-id="9c5aa-112">启用语音命令</span><span class="sxs-lookup"><span data-stu-id="9c5aa-112">Enabling Voice Commands</span></span>

<span data-ttu-id="9c5aa-113">本部分实现了两个语音命令。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-113">In this section, two voice commands are implemented.</span></span> <span data-ttu-id="9c5aa-114">首先，通过显示 "切换诊断"，可以切换帧速率诊断面板。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-114">First, the ability to toggle the frame rate diagnostics panel is introduced by saying "toggle diagnostics".</span></span> <span data-ttu-id="9c5aa-115">其次，可以通过语音命令播放声音。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-115">Second, the ability to play a sound with a voice command is explored.</span></span> <span data-ttu-id="9c5aa-116">首先查看负责配置语音命令的 MRTK 配置文件和设置。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-116">The MRTK profiles and settings responsible for configuring voice commands is reviewed first.</span></span>

1. <span data-ttu-id="9c5aa-117">在 BaseScene 层次结构中，选择 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-117">In the BaseScene hierarchy, select MixedRealityToolkit.</span></span> <span data-ttu-id="9c5aa-118">然后，在 "检查器" 面板中，选择 "输入"，然后单击 "DefaultMixedRealityInputSystemProfile" 左侧的 "小克隆" 按钮，以打开 "克隆配置文件" 弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-118">Then, in the Inspector panel, select Input and click the small Clone button to the left of the DefaultMixedRealityInputSystemProfile to open the Clone Profile popup.</span></span> <span data-ttu-id="9c5aa-119">在弹出窗口中，单击 "克隆" 以创建新的配置文件 MixedRealityInputSystemProfile。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-119">In the popup click Clone to create a new profile MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1a .png](images/mrlearning-base-ch5-1-step1a.png)

    <span data-ttu-id="9c5aa-121">这也会自动填充 MixedRealityToolkitConfigurationProfile 和新创建的 MixedRealityInputSystemProfile。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-121">This will also auto-populate the MixedRealityToolkitConfigurationProfile with the newly created MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1b .png](images/mrlearning-base-ch5-1-step1b.png)

2. <span data-ttu-id="9c5aa-123">在输入系统配置文件中，有各种设置。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-123">In the input system profile, there are a variety of settings.</span></span> <span data-ttu-id="9c5aa-124">对于语音命令，展开 "语音" 部分并按照上一步骤中所述的过程进行操作，以克隆 DefaultMixedRealitySpeechCommandsProfile 并将其替换为你自己的可编辑副本。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-124">For voice commands, expand the Speech section and follow the same process as in the previous step to clone the DefaultMixedRealitySpeechCommandsProfile and replace it with your own editable copy.</span></span>

    ![mrlearning-base-ch5-1-step2 .png](images/mrlearning-base-ch5-1-step2.png)

    <span data-ttu-id="9c5aa-126">在语音命令配置文件中，你会注意到一系列设置。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-126">In the speech command profile, you’ll notice a range of settings.</span></span> <span data-ttu-id="9c5aa-127">有关这些设置的完整说明，请参阅[MRTK speech 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-127">For a full description of these settings, refer to the [MRTK speech documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>).</span></span>

    <span data-ttu-id="9c5aa-128">默认情况下，一般行为是自动启动。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-128">By default, the general behavior is auto-start.</span></span> <span data-ttu-id="9c5aa-129">如果需要，可以将其更改为手动-启动。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-129">This can be changed to manual-start, if desired.</span></span> <span data-ttu-id="9c5aa-130">但在此示例中，请将其保留为自动启动。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-130">But for this example, keep it on auto-start.</span></span> <span data-ttu-id="9c5aa-131">MRTK 附带了几个默认的语音命令，如菜单、切换诊断和切换探查器。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-131">The MRTK comes with several default voice commands, such as menu, toggle diagnostics and toggle profiler.</span></span> <span data-ttu-id="9c5aa-132">我们将使用关键字 "切换诊断" 来打开和关闭 "诊断帧速率" 计数器。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-132">We will use the keyword “toggle diagnostics,” in order to turn on and off the diagnostics framerate counter.</span></span> <span data-ttu-id="9c5aa-133">在以下步骤中，我们还将添加一个新的语音命令。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-133">We will also add a new voice command in the steps below.</span></span>

3. <span data-ttu-id="9c5aa-134">添加新的语音命令。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-134">Add a new voice command.</span></span> <span data-ttu-id="9c5aa-135">为此，请单击 "+ 添加新的语音命令" 按钮。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-135">To do this, click the + Add a New Speech Command button.</span></span> <span data-ttu-id="9c5aa-136">你将看到一个新行，出现在现有语音命令列表下。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-136">You'll see a new line that appears below the list of existing voice commands.</span></span> <span data-ttu-id="9c5aa-137">键入要使用的语音命令。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-137">Type the voice command you want to use.</span></span> <span data-ttu-id="9c5aa-138">在此示例中，使用命令 "播放音乐"。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-138">In this example, use the command “play music".</span></span>

    ![mrlearning-base-ch5-1-step3 .png](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    ><span data-ttu-id="9c5aa-140">还可为语音命令设置键码。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-140">You can also set a keycode for speech commands.</span></span> <span data-ttu-id="9c5aa-141">这允许语音命令在按键时触发事件。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-141">This allows for voice commands to trigger events upon the press of a keyboard key.</span></span>

4. <span data-ttu-id="9c5aa-142">添加响应语音命令的功能。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-142">Add the ability to respond to voice commands.</span></span> <span data-ttu-id="9c5aa-143">选择 BaseScene 层次结构中未附加任何其他输入脚本的任何对象，例如 MixedRealityPlayspace 游戏对象。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-143">Select any object in the BaseScene hierarchy that does not have any other input scripts attached to it, for example, the MixedRealityPlayspace game object.</span></span> <span data-ttu-id="9c5aa-144">在检查器面板中，单击 "添加组件"，搜索 "语音"，然后选择语音输入处理程序脚本。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-144">In the Inspector panel, click Add Component, search for "speech", and select the Speech Input Handler script.</span></span>

    ![mrlearning-base-ch5-1-step4 .png](images/mrlearning-base-ch5-1-step4.png)

    <span data-ttu-id="9c5aa-146">默认情况下，你将看到两个复选框。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-146">By default, you will see two checkboxes.</span></span> <span data-ttu-id="9c5aa-147">其中一个是 "是否需要焦点" 复选框。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-147">One is the Is Focus Required checkbox.</span></span> <span data-ttu-id="9c5aa-148">因此，只要您将鼠标指针指向具有眼睛眼睛、看好、看看或手工看的对象，就会触发语音命令。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-148">So, as long as you are pointing at the object with a ray-eye-gaze, head-gaze, controller-gaze, or hand-gaze, the voice command will be triggered.</span></span> <span data-ttu-id="9c5aa-149">取消选中此复选框，以便用户不必查看对象即可使用语音命令。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-149">Uncheck this checkbox so that the user does not have to look at the object to use the voice command.</span></span>

5. <span data-ttu-id="9c5aa-150">添加响应语音命令的功能。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-150">Add the ability to respond to a voice command.</span></span> <span data-ttu-id="9c5aa-151">为此，请单击语音输入处理程序中的 "+" 按钮。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-151">To do this, click the + button that’s in the Speech Input Handler.</span></span>

    ![mrlearning-base-ch5-1-step5 .png](images/mrlearning-base-ch5-1-step5.png)

6. <span data-ttu-id="9c5aa-153">在关键字旁边，可以看到一个下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-153">Next to Keyword, you'll see a dropdown menu.</span></span> <span data-ttu-id="9c5aa-154">选择 "切换诊断"，以便每当用户显示短语 "切换诊断" 时，都会触发一个操作。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-154">Select Toggle Diagnostics so that whenever the user says the phrase “toggle diagnostics”, it triggers an action.</span></span> <span data-ttu-id="9c5aa-155">请注意，您可能需要通过按下箭头旁边的箭头来展开元素0。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-155">Note that you might need to expand Element 0 by pressing the arrow next to it.</span></span>

    ![mrlearning-base-ch5-1-step6 .png](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    ><span data-ttu-id="9c5aa-157">根据你在步骤3中编辑的配置文件填充这些关键字。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-157">These keywords are populated, based on the profile you edited in the step 3.</span></span>

7. <span data-ttu-id="9c5aa-158">添加 "诊断系统" 语音控件脚本，以打开和关闭计数器计数器诊断。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-158">Add the Diagnostics System Voice Controls script to toggle the framerate counter diagnostic on and off.</span></span> <span data-ttu-id="9c5aa-159">为此，请按 "添加组件"，搜索 "诊断系统语音控制脚本"，然后从菜单添加它。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-159">To do this, press Add Component, search for Diagnostics System Voice Controls script and add it from the menu.</span></span> <span data-ttu-id="9c5aa-160">此脚本可添加到任何对象，但为了简单起见，我们将其添加到语音输入处理程序所在的同一对象。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-160">This script can be added to any object, but for simplicity, we will add it to the same object as the speech input handler.</span></span>

    ![mrlearning-base-ch5-1-step7 .png](images/mrlearning-base-ch5-1-step7.png)

8. <span data-ttu-id="9c5aa-162">在语音输入处理程序中添加新的响应。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-162">Add a new response in the speech input handler.</span></span> <span data-ttu-id="9c5aa-163">为此，请单击 "+" 图标，将新响应添加到响应列表。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-163">To do this, click the "+" icon to add a new response to the response list.</span></span>

    ![mrlearning-base-ch5-1-step8 .png](images/mrlearning-base-ch5-1-step8.png)

9. <span data-ttu-id="9c5aa-165">将具有诊断系统语音控制脚本的对象拖到您在上一步中刚创建的新响应。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-165">Drag the object that has the Diagnostics System Voice Controls script to the new response you just created in the previous step.</span></span>

    ![mrlearning-base-ch5-1-step9 .png](images/mrlearning-base-ch5-1-step9.png)

10. <span data-ttu-id="9c5aa-167">单击 "函数" 下拉列表（其中不显示 "函数"），然后选择 "诊断系统语音控制"，然后选择 ToggleDiagnostics （）函数，以打开和关闭诊断。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-167">Click the function dropdown (where it says No Function), then Diagnostics System Voice Controls, and select the ToggleDiagnostics () function which toggles your diagnostics on and off.</span></span>

    ![mrlearning-base-ch5-1-step10 .png](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > <span data-ttu-id="9c5aa-169">在生成到设备之前，你需要启用 mic 设置。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-169">Before building to your device, you need to enable mic settings.</span></span> <span data-ttu-id="9c5aa-170">为此，请单击 "文件"，然后依次单击 "生成设置" 和 "播放机设置"，并确保已设置麦克风功能。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-170">To do this, click File and go to Build Settings, Player Settings and ensure that the microphone capability is set.</span></span>

    <span data-ttu-id="9c5aa-171">接下来，使用八对象添加从语音命令播放音频文件的功能。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-171">Next, add the ability to play an audio file from voice command using the Octa object.</span></span> <span data-ttu-id="9c5aa-172">从[第4课](mrlearning-base-ch4.md)中回忆，已添加了从触摸八对象播放音频剪辑的能力。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-172">Recall from [lesson 4](mrlearning-base-ch4.md) that the ability to play an audio clip from touching the Octa object was added.</span></span> <span data-ttu-id="9c5aa-173">我们会将此音频源同样用于音乐语音命令。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-173">We will leverage this same audio source for our music voice command.</span></span>

11. <span data-ttu-id="9c5aa-174">选择 BaseScene 层次结构中的八对象。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-174">Select the Octa object in the BaseScene hierarchy.</span></span>

12. <span data-ttu-id="9c5aa-175">添加另一个语音输入处理程序（重复步骤4和5），但包含八对象。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-175">Add another speech input handler (repeat Steps 4 and 5), but with the octa object.</span></span>

13. <span data-ttu-id="9c5aa-176">添加 "播放音乐" 语音命令，而不是从步骤6添加 "切换诊断语音" 命令，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-176">Instead of adding the Toggle Diagnostics voice command from step 6, add the Play Music voice command as shown in the image below.</span></span>

    ![mrlearning-base-ch5-1-step13 .png](images/mrlearning-base-ch5-1-step13.png)

14. <span data-ttu-id="9c5aa-178">对于步骤8和9，添加一个新的响应，并将八对象（具有诊断系统语音控制脚本的对象）添加到空的响应槽。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-178">As with Steps 8 and 9, add a new response and drag the Octa object, the object that has the Diagnostics System Voice Controls script on it, to the empty response slot.</span></span>

15. <span data-ttu-id="9c5aa-179">选择不显示函数的下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-179">Select the dropdown menu that says No Function.</span></span> <span data-ttu-id="9c5aa-180">然后选择 "音频源"，然后选择 "PlayOneShot" （AudioClip）。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-180">Then select Audio Source, followed by PlayOneShot (AudioClip).</span></span>

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. <span data-ttu-id="9c5aa-182">在此示例中，我们将使用[第4课](mrlearning-base-ch4.md)中的相同音频剪辑。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-182">For this example, we are going to use the same audio clip from [Lesson 4](mrlearning-base-ch4.md).</span></span> <span data-ttu-id="9c5aa-183">进入项目面板，搜索 "MRTK_Gem" 音频剪辑，并将其拖动到音频源槽，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-183">Go into your Project panel, search for “MRTK_Gem” audio clip and drag it into the audio source slot as shown in the image below.</span></span> <span data-ttu-id="9c5aa-184">现在，你的应用程序将响应语音命令 "切换诊断" 以切换 "帧速率" 计数器面板，并播放音乐来播放 MRTK_Gem 的歌曲。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-184">Now your application will respond to the voice commands “toggle diagnostics” to toggle the Frame Rate Counter panel and Play Music to play the MRTK_Gem song.</span></span>

    ![Lesson5 Chapter1.txt Step16im](images/Lesson5_chapter1_step16im.PNG)

### <a name="the-pan-gesture"></a><span data-ttu-id="9c5aa-186">平移手势</span><span class="sxs-lookup"><span data-stu-id="9c5aa-186">The Pan Gesture</span></span>

<span data-ttu-id="9c5aa-187">在本部分中，你将学习如何使用平移手势。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-187">In this section, you will learn how to use the pan gesture.</span></span> <span data-ttu-id="9c5aa-188">这适用于使用手指或手滚动内容滚动。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-188">This is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="9c5aa-189">你还可以使用平移手势来旋转对象、循环浏览三维对象的集合，甚至滚动 2D UI。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-189">You can also use the pan gesture to rotate objects, cycle through a collection of 3D objects, or even to scroll a 2D UI.</span></span>

1. <span data-ttu-id="9c5aa-190">创建一个四面体。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-190">Create a quad.</span></span> <span data-ttu-id="9c5aa-191">在 BaseScene 层次结构中，右键单击，选择 "3D 对象"，然后选择 "四个"。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-191">In your BaseScene hierarchy, right-click, select "3D Object" followed by Quad.</span></span>

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. <span data-ttu-id="9c5aa-193">根据需要重定位四部分。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-193">Reposition the quad, as appropriate.</span></span> <span data-ttu-id="9c5aa-194">对于我们的示例，我们将 x = 0、y = 0 和 z = 1.5 远离相机，以实现从 HoloLens 2 获得的舒适位置。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-194">For our example, we set the x = 0, the y = 0 and the z = 1.5 away from the camera for a comfortable position from HoloLens 2.</span></span>

    >[!NOTE]
    ><span data-ttu-id="9c5aa-195">如果故障诊断块或位于前一课中的任何内容之前，请务必将其移动，使其不会阻止其他任何对象。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-195">If the quad blocks or is in front of any content from the previous lessons, be sure to move it so that it doesn’t block any of the other objects.</span></span>

3. <span data-ttu-id="9c5aa-196">将材料应用到四面体。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-196">Apply a material to the quad.</span></span> <span data-ttu-id="9c5aa-197">此材料将是使用平移手势滚动的内容。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-197">This material will be what we will be scrolling through with the pan gesture.</span></span>

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. <span data-ttu-id="9c5aa-199">在 "项目" 面板的 "搜索" 框中键入 "平移内容"。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-199">In your Projects panel, type “pan content” in the Search box.</span></span> <span data-ttu-id="9c5aa-200">将该材料拖到场景中的四个部分。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-200">Drag that material onto the quad in your scene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="9c5aa-201">PanContent 资料不是 MRTK 的一部分，而是在上一课中导入的 BaseModuleAssets 资产中包含。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-201">The PanContent material is not part of MRTK but included with the BaseModuleAssets asset imported in the previous lesson.</span></span>

    <span data-ttu-id="9c5aa-202">若要使用平移手势，需要在对象中添加一个碰撞体。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-202">To use the pan gesture, you will need a collider on your object.</span></span> <span data-ttu-id="9c5aa-203">你可能会看到，四面体已有一个网格碰撞体。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-203">You may see the quad already has a mesh collider.</span></span> <span data-ttu-id="9c5aa-204">但是，该网格碰撞体并不理想，因为它非常小，很难将其选中。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-204">However, the mesh collider is not ideal, because it is extremely thin and difficult to select.</span></span> <span data-ttu-id="9c5aa-205">我们建议将网格碰撞体替换为盒碰撞体。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-205">We suggest replacing the mesh collider with a box collider.</span></span>

5. <span data-ttu-id="9c5aa-206">右键单击 "检查器" 面板上的 "故障诊断" 中的网格碰撞器。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-206">Right-click the mesh collider that’s on the quad from the Inspector panel.</span></span> <span data-ttu-id="9c5aa-207">然后单击 "删除组件" 将其删除。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-207">Then remove it by clicking Remove Component.</span></span>

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. <span data-ttu-id="9c5aa-209">现在，通过单击 "添加组件" 并搜索 "box 碰撞器" 来添加框碰撞器。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-209">Now add the box collider by clicking Add Component and searching “box collider”.</span></span> <span data-ttu-id="9c5aa-210">默认添加的框碰撞器仍然太小，因此请单击 "编辑碰撞器" 按钮进行编辑。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-210">The default added box collider is still too thin, so click the Edit Collider button to edit.</span></span> <span data-ttu-id="9c5aa-211">按下该对象后，可以使用 x、y 和 z 值或场景编辑器中的元素来调整其大小。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-211">When it’s pressed in, you can adjust the size using the x, y and z values or the elements in the scene editor.</span></span> <span data-ttu-id="9c5aa-212">对于本示例，我们希望盒碰撞体稍微靠在四面体的后面。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-212">For our example, we want to extend the box collider a little behind the quad.</span></span> <span data-ttu-id="9c5aa-213">在场景编辑器中，将盒碰撞体往后朝外拖动（参考下图）。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-213">In the scene editor, drag the box collider from the back, outwards (see the image below).</span></span> <span data-ttu-id="9c5aa-214">这样，用户不仅可以使用手指，而且能滚动整个手。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-214">This lets the user not only use their finger, but their entire hand to scroll.</span></span>

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. <span data-ttu-id="9c5aa-216">使对象具有交互能力。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-216">Make it interactive.</span></span> <span data-ttu-id="9c5aa-217">由于我们希望直接与四个部分交互，我们想要使用在第4课中使用的近乎交互可触摸组件来播放八对象中的音乐。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-217">Since we want to interact with the quad directly, we want to use the Near Interaction Touchable component that we used this in Lesson 4 for playing music from the Octa object.</span></span> <span data-ttu-id="9c5aa-218">单击 "添加组件"，搜索 "near 交互可触摸" 并将其选中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-218">Click Add Component, search for “near interaction touchable” and select it as shown in the images below.</span></span>

    ![mrlearning-base-ch5-2-step7a .png](images/mrlearning-base-ch5-2-step7a.png)

    <span data-ttu-id="9c5aa-220">如果你看到有关边界和/或中心与 BoxCollider 大小和/或中心不匹配的黄色警告，请单击 "修复边界" 和/或 "修复中心" 按钮，更新中心和边界值。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-220">If you see a yellow warning about bounds and/or center not matching the BoxCollider's size and/or center, click the Fix Bounds and/or Fix Center buttons to update the center and bounds values.</span></span>

    ![mrlearning-base-ch5-2-step7b .png](images/mrlearning-base-ch5-2-step7b.png)

8. <span data-ttu-id="9c5aa-222">添加识别平移手势的功能。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-222">Add the ability to recognize the pan gesture.</span></span> <span data-ttu-id="9c5aa-223">单击 "添加组件"，在搜索字段中键入 "手工交互"，然后添加 "手写交互平移缩放脚本" 组件。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-223">Click Add Component, type “hand interaction” in the search field and add the Hand Interaction Pan Zoom script component.</span></span>

    ![mrlearning-base-ch5-2-step8a .png](images/mrlearning-base-ch5-2-step8a.png)

    <span data-ttu-id="9c5aa-225">这样就可以使用启用了平移的四核。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-225">And with that, you have a pan-enabled quad.</span></span>

    <span data-ttu-id="9c5aa-226">正如您所看到的，手动交互平移缩放脚本组件具有各种设置，作为可选的练习，您可以自由地使用它们。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-226">As you can see, the Hand Interaction Pan Zoom script component has various settings, as an optional exercise, feel free to play around with them.</span></span>

    ![mrlearning-base-ch5-2-step8b .png](images/mrlearning-base-ch5-2-step8b.png)

9. <span data-ttu-id="9c5aa-228">接下来，我们了解如何平移 3D 对象。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-228">Next, we will learn how to pan 3D objects.</span></span>

    <span data-ttu-id="9c5aa-229">在层次结构中，右键单击 "四个对象"，打开上下文弹出菜单，然后选择 "**三维对象** > **多维数据集**" 将多维数据集添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-229">In the Hierarchy, right-click the Quad object, to open the contextual popup menu, then select **3D Object** > **Cube** to add a cube to your scene.</span></span>

    <span data-ttu-id="9c5aa-230">确保将多维数据集的**位置**设置为_0，0，0，_ 使其在四部分中整齐放置。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-230">Ensure the Cube's **Position** is set to  _0, 0, 0_ so it's positioned neatly within the Quad.</span></span> <span data-ttu-id="9c5aa-231">将多维数据集缩小为_0.1、0.1、0.1_的**小数位数**。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-231">Scale the Cube down to a **Scale** of _0.1, 0.1, 0.1_.</span></span>

    ![mrlearning-base-ch5-2-step9 .png](images/mrlearning-base-ch5-2-step9.png)

    <span data-ttu-id="9c5aa-233">右键单击多维数据集，打开上下文快捷菜单并选择 "**复制**"，从而将多维数据集重复三次。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-233">Duplicate the Cube three times by right-clicking the Cube, to open the contextual popup menu, and selecting **Duplicate**.</span></span>

    <span data-ttu-id="9c5aa-234">将多维数据集均匀隔开。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-234">Space the cubes out evenly.</span></span> <span data-ttu-id="9c5aa-235">场景应类似于下图。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-235">Your scene should look similar to the image below.</span></span>

10. <span data-ttu-id="9c5aa-236">按住 CTRL 键的同时选择 "层次结构" 面板中的每个**多维数据集**对象，将 MoveWithPan 脚本添加到所有多维数据集。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-236">Add the MoveWithPan script to all the cubes by holding down the CTRL key while selecting each **Cube** object in the Hierarchy panel.</span></span> <span data-ttu-id="9c5aa-237">在 "检查器" 面板中，单击 "添加组件"，然后搜索并选择 "**移动以平移**脚本"，将其添加到所有多维数据集。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-237">In the Inspector panel, click Add Component, and search for and select the **Move With Pan** script to add it to all the cubes.</span></span>

    ![mrlearning-base-ch5-2-step10a .png](images/mrlearning-base-ch5-2-step10a.png)

    >[!NOTE]
    ><span data-ttu-id="9c5aa-239">MoveWithPan 脚本不是 MRTK 的一部分，而是在上一课中导入的 BaseModuleAssets 资产中包含。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-239">The MoveWithPan script is not part of MRTK but included with the BaseModuleAssets asset imported in the previous lesson.</span></span>

    <span data-ttu-id="9c5aa-240">在仍选中多维数据集的情况下，将 "层次结构" 面板中的 "**四**个对象" 拖到 "**带平移的移动**脚本" 组件的 "**平移输入源**" 字段</span><span class="sxs-lookup"><span data-stu-id="9c5aa-240">With the cubes still selected, drag the **Quad** object from the Hierarchy panel into the **Pan Input Source** field of the **Move With Pan** script component.</span></span>

    ![mrlearning-base-ch5-2-step10b .png](images/mrlearning-base-ch5-2-step10b.png)

    <span data-ttu-id="9c5aa-242">现在，多维数据集将随平移手势一起移动。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-242">Now, the cubes will move with your pan gesture.</span></span>

    >[!TIP]
    ><span data-ttu-id="9c5aa-243">每个多维数据集上的 MoveWithPan 实例侦听从四个对象上的 HandInteractionPanZoom 实例发送的 PanUpdated 事件，这些事件已添加到每个多维数据集上的 "平移输入源" 字段中，并相应地更新相应的多维数据集对象的位置。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-243">The MoveWithPan instance on each cube listens for the PanUpdated event sent from the HandInteractionPanZoom instance on the Quad object, that we added to the Pan Input Source field on each of the cubes, and updates the respective cube object's position accordingly.</span></span>

    <span data-ttu-id="9c5aa-244">如果仍选中多维数据集，则将它们沿其 Z 轴向前移动，使每个多维数据集的网格位于**四**个**箱的碰撞**器中，方法是将其**位置 Z**值更改为_0.7_。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-244">With the cubes still selected, move them forward along their Z axis so each cube's mesh is inside the **Quad**'s **Box Collider** by changing their **Position Z** values to _0.7_.</span></span>

    ![mrlearning-base-ch5-2-step10c .png](images/mrlearning-base-ch5-2-step10c.png)

    <span data-ttu-id="9c5aa-246">现在，如果通过在 "检查器" 面板中取消选中并禁用**四**个 "**网格呈现**器" 组件，则会看到一个不可见的四个部分，可在其中平移3d 对象的列表。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-246">Now, if you disable the **Quad**'s **Mesh Renderer** component by un-checking it in the Inspector panel, you will have an invisible quad where you can pan through a list of 3D objects.</span></span>

    ![mrlearning-base-ch5-2-step10d .png](images/mrlearning-base-ch5-2-step10d.png)

### <a name="eye-tracking"></a><span data-ttu-id="9c5aa-248">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="9c5aa-248">Eye Tracking</span></span>

<span data-ttu-id="9c5aa-249">在本部分中，我们将探讨如何在演示中启用目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-249">In this section, we will explore how to enable eye tracking in our demo.</span></span> <span data-ttu-id="9c5aa-250">当您的3D 菜单项 gazed 时，我们将慢慢旋转它们。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-250">We will slowly spin our 3D menu items when they are being gazed upon with your eye gaze.</span></span> <span data-ttu-id="9c5aa-251">此外，在选择所凝视的项时，我们还会触发一种有趣的效果。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-251">We will also trigger a fun effect when the gazed-upon item is selected.</span></span>

1. <span data-ttu-id="9c5aa-252">确保为目视跟踪正确配置 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-252">Ensure the MRTK profiles are properly configured for eye tracking.</span></span> <span data-ttu-id="9c5aa-253">若要执行此操作，请转到[MRTK 说明中的目视跟踪](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)入门，并通过查看[设置目视跟踪分步](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step)部分中的步骤来验证是否正确配置了目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-253">To do this, go to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions and verify that eye tracking is properly configured by reviewing the steps in the [Setting up eye tracking step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) section.</span></span> <span data-ttu-id="9c5aa-254">完成文档中的所有剩余步骤。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-254">Complete any remaining steps in the documentation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="9c5aa-255">如果使用 DefaultHoloLens2InputSystemProfile （如[配置混合现实工具包](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit)课程中所述）来克隆自定义 MRTK 配置文件，则默认情况下会在 unity 项目中启用目视跟踪，但仍需为 unity 编辑器设置目视跟踪模拟，并将 Visual Studio 配置为允许对生成进行目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-255">If you used the DefaultHoloLens2InputSystemProfile, as instructed in the [Configure the Mixed Reality Toolkit](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) lesson, to clone your custom MRTK configuration profile, eye tracking is enabled by default in the Unity project but you will still have to set up eye tracking simulation for the Unity editor and configure Visual Studio to allow eye tracking for the build.</span></span>

    <span data-ttu-id="9c5aa-256">上述链接提供了有关以下操作的简要说明：</span><span class="sxs-lookup"><span data-stu-id="9c5aa-256">The link above provides brief instructions for:</span></span>

    - <span data-ttu-id="9c5aa-257">创建 Windows Mixed Reality 眼睛数据提供程序以在 MRTK 配置文件中使用</span><span class="sxs-lookup"><span data-stu-id="9c5aa-257">Creating the Windows Mixed Reality Eye Gaze Data Provider for use in the MRTK profile</span></span>
    - <span data-ttu-id="9c5aa-258">在连接到相机的目视提供者中启用目视跟踪</span><span class="sxs-lookup"><span data-stu-id="9c5aa-258">Enabling eye tracking in the Gaze Provider attached to the camera</span></span>
    - <span data-ttu-id="9c5aa-259">在 Unity 编辑器中设置目视跟踪模拟</span><span class="sxs-lookup"><span data-stu-id="9c5aa-259">Setting up an eye tracking simulation in the Unity editor</span></span>
    - <span data-ttu-id="9c5aa-260">编辑 Visual Studio 解决方案的功能，以便在生成的应用程序中进行眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="9c5aa-260">Editing the Visual Studio solution's capabilities to allow eye tracking in the built application</span></span>

2. <span data-ttu-id="9c5aa-261">将眼动跟踪目标组件添加到目标对象。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-261">Add the Eye Tracking Target component to target objects.</span></span> <span data-ttu-id="9c5aa-262">若要允许对象响应眼睛眼睛事件，我们需要使用目视注视将 EyeTrackingTarget 组件添加到要与之交互的每个对象上。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-262">To allow an object to respond to eye gaze events, we'll need to add the EyeTrackingTarget component on each object that we want to interact with by using eye gaze.</span></span> <span data-ttu-id="9c5aa-263">将此组件添加到网格集合中的每个（共九个）3D 对象。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-263">Add this component to each of the nine 3D objects that are part of the grid collection.</span></span>

    >[!TIP]
    ><span data-ttu-id="9c5aa-264">你可以使用 Shift 和/或 CRTL 键选择层次结构中的多个项，然后大容量添加 EyeTrackingTarget 组件。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-264">You can use the Shift and/or CRTL keys to select multiple items in the Hierarchy and then bulk-add the EyeTrackingTarget component.</span></span>

    ![Lesson5 Chapter3 步骤2](images/Lesson5Chapter3Step2.JPG)

3. <span data-ttu-id="9c5aa-266">接下来，我们将为一些激动人心的交互添加 EyeTrackingTutorialDemo 脚本。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-266">Next, we will add the EyeTrackingTutorialDemo script for some exciting interactions.</span></span> <span data-ttu-id="9c5aa-267">对于网格集合中的每个三维对象，通过在 "添加组件" 菜单中搜索组件来添加 EyeTrackingTutorialDemo 脚本。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-267">For each 3D object in the grid collection, add the EyeTrackingTutorialDemo script by searching for the component in the Add Component menu.</span></span>

    ![Lesson5 Chapter3 步骤3](images/Lesson5Chapter3Step3.JPG)

    >[!NOTE]
    ><span data-ttu-id="9c5aa-269">EyeTrackingTutorialDemo 脚本材料不是 MRTK 的一部分，而是在上一课中导入的 BaseModuleAssets 资产中包含。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-269">The EyeTrackingTutorialDemo script material is not part of MRTK but included with the BaseModuleAssets asset imported in the previous lesson.</span></span>

4. <span data-ttu-id="9c5aa-270">在注视目标的同时旋转对象。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-270">Spin the object while looking at the target.</span></span> <span data-ttu-id="9c5aa-271">我们想要在查看三维对象时将其配置为旋转。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-271">We want to configure our 3D objects to spin while we are looking at them.</span></span> <span data-ttu-id="9c5aa-272">为此，请在 "EyeTrackingTarget" 组件的 "查看目标" 部分中插入一个新字段，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-272">To do this, insert a new field in the While Looking At Target() section of the EyeTrackingTarget component, as shown in the image below.</span></span>

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    <span data-ttu-id="9c5aa-274">在新创建的字段中，将当前游戏对象添加到空字段，然后选择 EyeTrackingTutorialDemo > RotateTarget （），如下图所示。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-274">In the newly-created field, add the current Game Object to the empty field, and select EyeTrackingTutorialDemo>RotateTarget(), as shown in the image below.</span></span> <span data-ttu-id="9c5aa-275">现在，该 3D 对象已配置为在使用眼动跟踪凝视它时会自动旋转。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-275">Now the 3D object is configured to spin when it is being gazed upon with eye tracking.</span></span>

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. <span data-ttu-id="9c5aa-277">添加 "故障目标" 的功能，即通过使用 "gazed" 选择的 "选择"。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-277">Add in the ability to “blip target” that is being gazed at upon select by air-tap or saying “select”.</span></span> <span data-ttu-id="9c5aa-278">与步骤4类似，我们想要通过将 EyeTrackingTutorialDemo 分配给 EyeTrackingTarget 组件的游戏对象的 Select （）字段来触发 > BlipTarget （），如下图所示。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-278">Similar to Step 4, we want to trigger EyeTrackingTutorialDemo>BlipTarget() by assigning it to the game object’s Select() field of the EyeTrackingTarget component, as shown in the figure below.</span></span> <span data-ttu-id="9c5aa-279">现在已配置此配置，每当触发选择操作（例如，分流或语音命令 "select"）时，就会注意到游戏对象中的故障。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-279">With this now configured, you will notice a slight blip in the game object whenever you trigger a select action, such as air-tap or the voice command “select”.</span></span>

    ![Lesson5 Chapter3 步骤5](images/Lesson5Chapter3Step5.JPG)

6. <span data-ttu-id="9c5aa-281">在 HoloLens 2 中生成之前，请确保已正确配置眼动跟踪功能。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-281">Ensure eye tracking capabilities are properly configured before building to HoloLens 2.</span></span> <span data-ttu-id="9c5aa-282">在撰写本文时，Unity 尚不能为眼睛跟踪功能设置注视输入。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-282">As of this writing, Unity does not yet have the ability to set the gaze input for eye tracking capabilities.</span></span> <span data-ttu-id="9c5aa-283">若要在 HoloLens 2 中使用目视跟踪，需要设置此功能。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-283">Setting this capability is required for eye tracking to work in HoloLens 2.</span></span> <span data-ttu-id="9c5aa-284">按照[HoloLens 2 说明测试 Unity 应用](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)，以启用 "注视输入" 功能。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-284">Follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions to enable the gaze input capability.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9c5aa-285">祝贺</span><span class="sxs-lookup"><span data-stu-id="9c5aa-285">Congratulations</span></span>

<span data-ttu-id="9c5aa-286">已成功将基本的目视跟踪功能添加到应用程序。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-286">You’ve successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="9c5aa-287">这些操作仅为眼动跟踪实现的探索领域开了一个头。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-287">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="9c5aa-288">本章还结束第5课，其中介绍了高级输入功能，如语音命令、平移手势和目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="9c5aa-288">This chapter also concludes Lesson 5, where we learned about advanced input functionality, such as voice commands, panning gestures, and eye tracking.</span></span>

[<span data-ttu-id="9c5aa-289">下一课： 7. 创建农历模块示例应用程序</span><span class="sxs-lookup"><span data-stu-id="9c5aa-289">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
