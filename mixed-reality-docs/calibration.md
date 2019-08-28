---
title: 校准
description: 校准 IPD (interpupillary 距离) 可以提高视觉对象的质量。 HoloLens 和 Windows Mixed Reality 沉浸式耳机提供自定义 IPD 的方式。
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 校准, 舒适, 视觉对象, 质量, ipd
ms.openlocfilehash: 1fc3904f4b3e441a967616f20e4287dbc7f08835
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047055"
---
# <a name="improve-visual-quality-and-comfort"></a><span data-ttu-id="d3cd8-105">改善视觉质量和舒适</span><span class="sxs-lookup"><span data-stu-id="d3cd8-105">Improve visual quality and comfort</span></span>
<span data-ttu-id="d3cd8-106">HoloLens、HoloLens 2 和 Windows Mixed Reality 沉浸式耳机提供不同的方法来改善视觉体验的质量。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-106">HoloLens, HoloLens 2 and Windows Mixed Reality immersive headsets offer different ways to improve the quality of the visual experience.</span></span> 

## <a name="hololens-2"></a><span data-ttu-id="d3cd8-107">Hololens 2</span><span class="sxs-lookup"><span data-stu-id="d3cd8-107">Hololens 2</span></span>

### <a name="calibration"></a><span data-ttu-id="d3cd8-108">校准</span><span class="sxs-lookup"><span data-stu-id="d3cd8-108">Calibration</span></span>

<span data-ttu-id="d3cd8-109">Hololens 2 旨在为客户提供最高质量的视觉图像和舒适。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-109">Hololens 2 is designed to provide the highest quality visual imagery and comfort for our customers.</span></span> <span data-ttu-id="d3cd8-110">使用目视跟踪技术来改善查看和与虚拟环境交互的用户体验。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-110">Eye tracking technology is used to improve the user experience of seeing and interacting with the virtual environment.</span></span>  
<span data-ttu-id="d3cd8-111">在 HoloLens 2 上, 系统会提示你在设备安装过程中校准你的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-111">On HoloLens 2, you'll be prompted to calibrate your visuals during device setup.</span></span> <span data-ttu-id="d3cd8-112">要求用户查看固定目标集。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-112">Users are asked to look at the set of fixation targets.</span></span> <span data-ttu-id="d3cd8-113">这允许设备为用户调整全息影像渲染, 以确保准确定位全息影像、舒适的3D 查看体验和改进的显示质量。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-113">This allows the device to adjust hologram rendering for the user to ensure accurately positioned holograms, comfortable 3D viewing experience and improved display quality.</span></span> <span data-ttu-id="d3cd8-114">所有调整都是动态发生的, 无需手动优化。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-114">All adjustments happen on the fly without a need for manual tuning.</span></span> <span data-ttu-id="d3cd8-115">通过使用眼睛作为特征点, 可调整设备, 使每个用户和视觉对象经过调整, 因为耳机会略微使用。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-115">By using the eyes as landmarks, the device is adjusted for every user and visuals are tuned as the headset shifts slightly throughout use.</span></span> <span data-ttu-id="d3cd8-116">目视跟踪由系统在内部使用, 开发人员无需执行任何操作即可利用此功能。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-116">Eye position tracking is used internally by the system and developers don’t need to do anything to leverage this capability.</span></span> <span data-ttu-id="d3cd8-117">此信息不适用于开发人员。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-117">This information is not available to developers.</span></span> <span data-ttu-id="d3cd8-118">在 Hololens 2 上, 执行校准还可以确保为每个用户准确地目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-118">On Hololens 2, performing calibration also ensures accurate eye gaze tracking for every user.</span></span> <span data-ttu-id="d3cd8-119">眼动跟踪可让应用程序实时跟踪用户正在注视的位置。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-119">Eye tracking enables applications to track where the user is looking in real time.</span></span> <span data-ttu-id="d3cd8-120">这是开发人员可利用的主要功能, 实现全新级别的上下文、人工理解和智能体验中的交互。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-120">This is the main capability developers can leverage to enable a whole new level of context, human understanding and interactions within the Holographic experience.</span></span>  
<span data-ttu-id="d3cd8-121">校准以本地方式存储在设备上, 并且不与任何帐户信息关联。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-121">Calibration is stored locally on the device and is not associated with any account information.</span></span> <span data-ttu-id="d3cd8-122">没有已使用该设备的用户没有校准的记录。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-122">There is no record of who has used the device without calibration.</span></span> <span data-ttu-id="d3cd8-123">这意味着新用户首次使用设备时, 系统将提示用户校准视觉对象, 以及以前选择退出校准的用户或校准未成功的用户。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-123">This mean new users will get prompted to calibrate visuals when they use the device for the first time, as well as users who opted out of calibration previously or if calibration was unsuccessful.</span></span> <span data-ttu-id="d3cd8-124">在**设置** > 隐私保护跟踪 > 程序中, 始终可以从设备中删除校准。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-124">Calibration can always be deleted from the device in **Settings** > **Privacy** > **Eye Tracker**.</span></span> 

### <a name="calibration-failures"></a><span data-ttu-id="d3cd8-125">校准失败</span><span class="sxs-lookup"><span data-stu-id="d3cd8-125">Calibration failures</span></span>

<span data-ttu-id="d3cd8-126">校准应该适用于大多数用户, 但在某些情况下, 用户可能无法成功校准。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-126">Calibration should work for most users, but there are cases in which the user might be unable to calibrate successfully.</span></span>  
<span data-ttu-id="d3cd8-127">校准失败的一些示例如下:</span><span class="sxs-lookup"><span data-stu-id="d3cd8-127">Some examples of calibration failures are due to:</span></span>
- <span data-ttu-id="d3cd8-128">在校准体验过程中, 用户发生了注意力, 未关注校准目标</span><span class="sxs-lookup"><span data-stu-id="d3cd8-128">User getting distracted and not following the calibration targets during calibration experience</span></span>
- <span data-ttu-id="d3cd8-129">脏或有划痕的设备面板或设备面板未正确定位</span><span class="sxs-lookup"><span data-stu-id="d3cd8-129">Dirty or scratched device visor or device visor not positioned properly</span></span> 
- <span data-ttu-id="d3cd8-130">有脏或有划痕</span><span class="sxs-lookup"><span data-stu-id="d3cd8-130">Dirty or scratched glasses</span></span>
- <span data-ttu-id="d3cd8-131">某些类型的 contact 重用功能区和眼镜 (彩色触点重用功能区、toric contact 重用功能区、红外阻挡眼镜、和等)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-131">Certain types of contact lenses and glasses (colored contact lenses, some toric contact lenses, IR blocking glasses, some high prescription glasses, sunglasses, etc.)</span></span>
- <span data-ttu-id="d3cd8-132">更明显的组成部分, 一些 eyelash 扩展</span><span class="sxs-lookup"><span data-stu-id="d3cd8-132">More-pronounced makeup, some eyelash extensions</span></span>
- <span data-ttu-id="d3cd8-133">眼睛和/或设备面板的 Occlusions (眼镜)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-133">Occlusions of eye and/or device visor (hair, some thick eyeglass frames)</span></span>
- <span data-ttu-id="d3cd8-134">眼睛 physiology, 某些眼睛情况和/或目视外科 (一些狭窄的眼睛、长 eyelashes、amblyopia、nystagmus、LASIK 或其他眼睛 surgeries 等的一些情况)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-134">Eye physiology, certain eye conditions and/or eye surgery (some narrow eyes, long eyelashes, amblyopia, nystagmus, some cases of LASIK or other eye surgeries, etc.)</span></span>

<span data-ttu-id="d3cd8-135">如果校准失败, 请尝试以下修复之一:</span><span class="sxs-lookup"><span data-stu-id="d3cd8-135">If calibration is unsuccessful try one of these fixes:</span></span> 
- <span data-ttu-id="d3cd8-136">清理设备面板</span><span class="sxs-lookup"><span data-stu-id="d3cd8-136">Clean your device visor</span></span>
- <span data-ttu-id="d3cd8-137">清理眼镜</span><span class="sxs-lookup"><span data-stu-id="d3cd8-137">Clean your glasses</span></span>
- <span data-ttu-id="d3cd8-138">将设备面板一直推送到</span><span class="sxs-lookup"><span data-stu-id="d3cd8-138">Push your device visor all the way in</span></span>
- <span data-ttu-id="d3cd8-139">确保没有阻碍传感器或眼睛 (例如头发)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-139">Make sure nothing is obstructing the sensors or your eyes (e.g. hair)</span></span> 
- <span data-ttu-id="d3cd8-140">请确保房间内有足够的光线, 并且不受直射直射</span><span class="sxs-lookup"><span data-stu-id="d3cd8-140">Make sure there is enough light in your room and that you are not under direct sunlight</span></span>
- <span data-ttu-id="d3cd8-141">请确保在校准过程中仔细关注目标</span><span class="sxs-lookup"><span data-stu-id="d3cd8-141">Make sure you are carefully following the targets during calibration</span></span>

<span data-ttu-id="d3cd8-142">如果你遵循了所有准则, 并且校准仍失败, 则可以在 "**设置** > " "**系统** > **校准**" 中禁用校准提示。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-142">If you followed all guidelines and calibration is still failing, you can disable calibration prompt in **Settings** > **System** > **Calibration**.</span></span> <span data-ttu-id="d3cd8-143">' 当新用户使用此 Hololens 时, 会自动要求运行 "目视校准"。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-143">‘When a new person uses this Hololens, automatically ask to run eye calibration’ should be tuned off.</span></span> <span data-ttu-id="d3cd8-144">请注意, 这可能会导致更糟的全息图呈现质量和 discomfort。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-144">Please understand that this might result in worse hologram rendering quality and discomfort.</span></span>

### <a name="launching-the-calibration-app-from-settings"></a><span data-ttu-id="d3cd8-145">从设置启动校准应用</span><span class="sxs-lookup"><span data-stu-id="d3cd8-145">Launching the Calibration app from Settings</span></span>
1. <span data-ttu-id="d3cd8-146">使用 "开始手势" 转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-146">Use Start Gesture to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="d3cd8-147">如果未固定**设置**, 请选择 "**所有应用**" 以查看所有应用。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-147">Select **All Apps** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="d3cd8-148">启动**设置**。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-148">Launch **Settings**.</span></span>
4. <span data-ttu-id="d3cd8-149">导航到**系统** > 校准 > **目视校准**, 并选择 "**运行目视校准**"。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-149">Navigate to **System** > **Calibration** > **Eye Calibration** and select **Run Eye Calibration**.</span></span>

### <a name="calibration-when-sharing-a-devicesession"></a><span data-ttu-id="d3cd8-150">共享设备/会话时的校准</span><span class="sxs-lookup"><span data-stu-id="d3cd8-150">Calibration when sharing a device/session</span></span>

<span data-ttu-id="d3cd8-151">Hololens 2 可以在人员之间共享, 无需每个人进行设备设置。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-151">Hololens 2 can be shared between people, without a need for each person to go through device setup.</span></span> <span data-ttu-id="d3cd8-152">如果用户是设备的新用户, 则在将设备放在 head 上时, Hololens 2 将提示用户校准视觉对象。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-152">Hololens 2 will prompt the user to calibrate visuals when the device is put on the head if the user is new to the device.</span></span> <span data-ttu-id="d3cd8-153">如果用户之前在设备上校准了视觉对象, 则在用户将设备放在打印头上时, 显示器将无缝调整以获得质量和舒适的观看体验。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-153">If the user has previously calibrated visuals on the device, the display will be seamlessly adjusted for quality and a comfortable viewing experience when the user puts the device on the head.</span></span> 


## <a name="hololens-v1"></a><span data-ttu-id="d3cd8-154">Hololens (v1)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-154">Hololens (v1)</span></span>

<span data-ttu-id="d3cd8-155">校准 IPD (interpupillary 距离) 可以提高视觉对象的质量。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-155">Calibrating your IPD (interpupillary distance) can improve the quality of your visuals.</span></span>

### <a name="during-setup"></a><span data-ttu-id="d3cd8-156">安装期间</span><span class="sxs-lookup"><span data-stu-id="d3cd8-156">During setup</span></span>

![第二步的 IPD finger 对齐屏幕](images/ipd-finger-alignment-300px.jpg)<br>

<span data-ttu-id="d3cd8-158">*第二步的 IPD finger 对齐屏幕*</span><span class="sxs-lookup"><span data-stu-id="d3cd8-158">*IPD finger-alignment screen at second step*</span></span>

<span data-ttu-id="d3cd8-159">在 HoloLens 上, 系统会在安装过程中提示你校准视觉对象。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-159">On HoloLens, you'll be prompted to calibrate your visuals during setup.</span></span> <span data-ttu-id="d3cd8-160">这允许设备根据用户的[interpupillary 距离](https://en.wikipedia.org/wiki/Interpupillary_distance)(IPD) 调整全息图显示。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-160">This allows the device to adjust hologram display according to the user's [interpupillary distance](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span></span> <span data-ttu-id="d3cd8-161">使用不正确的 IPD 时, 全息影像可能出现不稳定或距离不正确。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-161">With an incorrect IPD, holograms may appear unstable or at an incorrect distance.</span></span>

<span data-ttu-id="d3cd8-162">Cortana 引入后, 第一个安装步骤是校准。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-162">After Cortana introduces herself, the first setup step is calibration.</span></span> <span data-ttu-id="d3cd8-163">建议你在此设置阶段完成校准步骤, 但可以通过等待 Cortana 提示你说 "跳过" 来跳转到。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-163">It's recommended that you complete the calibration step during this setup phase, but it can be skipped by waiting until Cortana prompts you to say "Skip" to move on.</span></span>

<span data-ttu-id="d3cd8-164">要求用户将其手指与每个眼睛一系列六个目标对齐。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-164">Users are asked to align their finger with a series of six targets per eye.</span></span> <span data-ttu-id="d3cd8-165">在此过程中, HoloLens 为用户设置了正确的 IPD。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-165">Through this process, HoloLens sets the correct IPD for the user.</span></span> <span data-ttu-id="d3cd8-166">如果需要更新或调整新用户的校准, 可以使用校准应用在安装程序外运行。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-166">If the calibration needs to be updated or adjusted for a new user, it can be run outside of setup using the Calibration app.</span></span>

### <a name="calibration-app"></a><span data-ttu-id="d3cd8-167">校准应用</span><span class="sxs-lookup"><span data-stu-id="d3cd8-167">Calibration app</span></span>

<span data-ttu-id="d3cd8-168">可随时通过校准应用执行校准。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-168">Calibration can be performed any time through the Calibration app.</span></span> <span data-ttu-id="d3cd8-169">校准应用默认安装, 并可通过 "开始" 菜单或 "设置" 应用进行访问。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-169">The Calibration app is installed by default and may be accessed from the Start menu, or through the Settings app.</span></span> <span data-ttu-id="d3cd8-170">如果要改善视觉对象的质量或为新用户校准视觉对象, 则建议使用校准。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-170">Calibration is recommended if you'd like to improve the quality of your visuals or calibrate visuals for a new user.</span></span>

<span data-ttu-id="d3cd8-171">**启动应用程序开始**</span><span class="sxs-lookup"><span data-stu-id="d3cd8-171">**Launching the app from Start**</span></span>
1. <span data-ttu-id="d3cd8-172">使用[布隆](gestures.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-172">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="d3cd8-173">选择 **+** 若要查看所有应用。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-173">Select **+** to view all apps.</span></span>
3. <span data-ttu-id="d3cd8-174">启动**校准**。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-174">Launch **Calibration**.</span></span>

![从 shell 访问校准应用程序](images/calibration-shell.png)

![启动后显示为活动多维数据集的校准应用](images/calibration-livecube-200px.png)

<span data-ttu-id="d3cd8-177">**从设置启动应用**</span><span class="sxs-lookup"><span data-stu-id="d3cd8-177">**Launching the app from Settings**</span></span>
1. <span data-ttu-id="d3cd8-178">使用[布隆](gestures.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-178">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="d3cd8-179">选择 **+** 若要查看所有应用，如果**设置**不固定到开始。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-179">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="d3cd8-180">启动**设置**。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-180">Launch **Settings**.</span></span>
4. <span data-ttu-id="d3cd8-181">导航到 "**系统** > **实用程序**" 并选择 "**打开校准**"。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-181">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

![从 "设置" 应用启动校准应用](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a><span data-ttu-id="d3cd8-183">沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="d3cd8-183">Immersive headsets</span></span>

<span data-ttu-id="d3cd8-184">若要更改耳机内的 IPD, 请打开设置应用并导航到**混合现实** > **耳机显示**, 并移动滑块控件。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-184">To change IPD within your headset, open the Settings app and navigate to **Mixed reality** > **Headset display** and move the slider control.</span></span> <span data-ttu-id="d3cd8-185">你将在你的耳机上实时看到更改。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-185">You’ll see the changes in real time in your headset.</span></span> <span data-ttu-id="d3cd8-186">如果你知道 IPD, 可能是由于访问 optometrist, 你也可以直接输入。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-186">If you know your IPD, maybe from a visit to the optometrist, you can enter it directly as well.</span></span>

<span data-ttu-id="d3cd8-187">你还可以通过转到电脑上的 "**设置** > "**混合现实** > **耳机显示**来调整此设置。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-187">You can also adjust this setting by going to **Settings** > **Mixed reality** > **Headset display** on your PC.</span></span>

<span data-ttu-id="d3cd8-188">如果头戴显示设备不支持 IPD 自定义, 则会禁用此设置。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-188">If your headset does not support IPD customization, this setting will be disabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3cd8-189">请参阅</span><span class="sxs-lookup"><span data-stu-id="d3cd8-189">See also</span></span>
* [<span data-ttu-id="d3cd8-190">HoloLens 的环境注意事项</span><span class="sxs-lookup"><span data-stu-id="d3cd8-190">Environment considerations for HoloLens</span></span>](environment-considerations-for-hololens.md)
