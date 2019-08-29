---
title: 校准
description: 校准 IPD (interpupillary 距离) 可以提高视觉对象的质量。 HoloLens 和 Windows Mixed Reality 沉浸式耳机提供自定义 IPD 的方式。
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 校准, 舒适, 视觉对象, 质量, ipd
ms.openlocfilehash: e86319dadeda02f71427b87980268eaf18942c49
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122082"
---
# <a name="improve-visual-quality-and-comfort"></a><span data-ttu-id="06ef0-105">改善视觉质量和舒适</span><span class="sxs-lookup"><span data-stu-id="06ef0-105">Improve visual quality and comfort</span></span>
<span data-ttu-id="06ef0-106">HoloLens、HoloLens 2 和 Windows Mixed Reality 沉浸式耳机提供不同的方法来改善视觉体验的质量。</span><span class="sxs-lookup"><span data-stu-id="06ef0-106">HoloLens, HoloLens 2 and Windows Mixed Reality immersive headsets offer different ways to improve the quality of the visual experience.</span></span> 

## <a name="hololens-2"></a><span data-ttu-id="06ef0-107">Hololens 2</span><span class="sxs-lookup"><span data-stu-id="06ef0-107">Hololens 2</span></span>

### <a name="calibration"></a><span data-ttu-id="06ef0-108">校准</span><span class="sxs-lookup"><span data-stu-id="06ef0-108">Calibration</span></span>

<span data-ttu-id="06ef0-109">Hololens 2 旨在为客户提供最高质量的视觉图像和舒适。</span><span class="sxs-lookup"><span data-stu-id="06ef0-109">Hololens 2 is designed to provide the highest quality visual imagery and comfort for our customers.</span></span> <span data-ttu-id="06ef0-110">使用目视跟踪技术来改善查看和与虚拟环境交互的用户体验。</span><span class="sxs-lookup"><span data-stu-id="06ef0-110">Eye tracking technology is used to improve the user experience of seeing and interacting with the virtual environment.</span></span>  

<span data-ttu-id="06ef0-111">在 HoloLens 2 上, 系统会提示你在设备安装过程中校准你的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="06ef0-111">On HoloLens 2, you'll be prompted to calibrate your visuals during device setup.</span></span> <span data-ttu-id="06ef0-112">要求用户查看一组固定目标。</span><span class="sxs-lookup"><span data-stu-id="06ef0-112">Users are asked to look at a set of fixation targets.</span></span> <span data-ttu-id="06ef0-113">这允许设备将全息图调整为用户, 以确保准确定位全息影像、舒适的3D 查看体验和改进的显示质量。</span><span class="sxs-lookup"><span data-stu-id="06ef0-113">This allows the device to adjust the rendering of holograms to the user to ensure accurately positioned holograms, a comfortable 3D viewing experience and improved display quality.</span></span> <span data-ttu-id="06ef0-114">所有调整都是动态进行的, 无需手动优化。</span><span class="sxs-lookup"><span data-stu-id="06ef0-114">All adjustments happen on-the-fly without the need for manual tuning.</span></span> <span data-ttu-id="06ef0-115">通过使用眼睛作为特征点, 设备会单独调整到每个用户, 并且视觉对象随着耳机变化的使用而进行调整。</span><span class="sxs-lookup"><span data-stu-id="06ef0-115">By using the eyes as landmarks, the device is individually adjusted to every user, and visuals are tuned as the headset shifts slightly throughout use.</span></span> <span data-ttu-id="06ef0-116">目视跟踪由系统在内部使用, 开发人员无需执行任何操作即可利用此功能。</span><span class="sxs-lookup"><span data-stu-id="06ef0-116">Eye position tracking is used internally by the system and developers don’t need to do anything to leverage this capability.</span></span> <span data-ttu-id="06ef0-117">事实上, 开发人员不能使用此信息。</span><span class="sxs-lookup"><span data-stu-id="06ef0-117">In fact, this information is not available to developers.</span></span>
<span data-ttu-id="06ef0-118">请参阅[目视跟踪 api](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) , 了解有关目视跟踪系统为开发人员提供的数据类型的详细信息。</span><span class="sxs-lookup"><span data-stu-id="06ef0-118">Please refer to the [Eye Tracking APIs](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) to learn more about the type of data the eye tracking system provides to developers.</span></span>

<span data-ttu-id="06ef0-119">在 Hololens 2 上, 执行校准还可以确保为每个用户提供准确的目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="06ef0-119">On Hololens 2, performing the calibration also ensures accurate eye-gaze tracking for every user.</span></span> <span data-ttu-id="06ef0-120">眼动跟踪可让应用程序实时跟踪用户正在注视的位置。</span><span class="sxs-lookup"><span data-stu-id="06ef0-120">Eye tracking enables applications to track where the user is looking in real time.</span></span> <span data-ttu-id="06ef0-121">这是开发人员可利用的主要功能, 实现全新级别的上下文、人工理解和智能体验中的交互。</span><span class="sxs-lookup"><span data-stu-id="06ef0-121">This is the main capability developers can leverage to enable a whole new level of context, human understanding and interactions within the holographic experience.</span></span>  

<span data-ttu-id="06ef0-122">校准数据存储在本地设备上, 且不与任何帐户信息关联。</span><span class="sxs-lookup"><span data-stu-id="06ef0-122">The calibration data is stored locally on the device and is not associated with any account information.</span></span> <span data-ttu-id="06ef0-123">没有已使用该设备的用户没有校准的记录。</span><span class="sxs-lookup"><span data-stu-id="06ef0-123">There is no record of who has used the device without calibration.</span></span> <span data-ttu-id="06ef0-124">这意味着, 用户首次使用设备时, 将提示用户进行校准, 还会提示选择 "之前" 或 "校准不成功" 的用户。</span><span class="sxs-lookup"><span data-stu-id="06ef0-124">This means that users will get prompted to calibrate when they use the device for the first time, as well as users who opted out of calibration previously or if the calibration was unsuccessful.</span></span> <span data-ttu-id="06ef0-125">在 "**设置** > " "**隐私** > "**跟踪**器中, 始终可以从设备中删除校准数据。</span><span class="sxs-lookup"><span data-stu-id="06ef0-125">The calibration data can always be deleted from the device in **Settings** > **Privacy** > **Eye Tracker**.</span></span> 

### <a name="calibration-failures"></a><span data-ttu-id="06ef0-126">校准失败</span><span class="sxs-lookup"><span data-stu-id="06ef0-126">Calibration failures</span></span>
<span data-ttu-id="06ef0-127">校准应该适用于大多数用户, 但在某些情况下, 用户可能无法成功校准。</span><span class="sxs-lookup"><span data-stu-id="06ef0-127">Calibration should work for most users, but there are cases in which the user might be unable to calibrate successfully.</span></span>  
<span data-ttu-id="06ef0-128">校准失败的一些示例如下:</span><span class="sxs-lookup"><span data-stu-id="06ef0-128">Some examples of calibration failures are due to:</span></span>
- <span data-ttu-id="06ef0-129">用户发生了分散注意力, 并没有在校准体验期间查看校准目标</span><span class="sxs-lookup"><span data-stu-id="06ef0-129">The user got distracted and didn't look at the calibration targets during the calibration experience</span></span>
- <span data-ttu-id="06ef0-130">脏或有划痕的设备面板或设备面板未正确定位</span><span class="sxs-lookup"><span data-stu-id="06ef0-130">Dirty or scratched device visor or device visor not positioned properly</span></span> 
- <span data-ttu-id="06ef0-131">某些类型的 contact 重用功能区和眼镜 (彩色触点重用功能区、toric contact 重用功能区、红外阻挡眼镜、和等)</span><span class="sxs-lookup"><span data-stu-id="06ef0-131">Certain types of contact lenses and glasses (colored contact lenses, some toric contact lenses, IR blocking glasses, some high prescription glasses, sunglasses, etc.)</span></span>
- <span data-ttu-id="06ef0-132">有脏或有划痕</span><span class="sxs-lookup"><span data-stu-id="06ef0-132">Dirty or scratched glasses</span></span>
- <span data-ttu-id="06ef0-133">更明显的组成部分, 一些 eyelash 扩展</span><span class="sxs-lookup"><span data-stu-id="06ef0-133">More pronounced makeup, some eyelash extensions</span></span>
- <span data-ttu-id="06ef0-134">眼睛和/或设备面板的 Occlusions (眼镜)</span><span class="sxs-lookup"><span data-stu-id="06ef0-134">Occlusions of eye and/or device visor (hair, some thick eyeglasses frames)</span></span>
- <span data-ttu-id="06ef0-135">眼睛 physiology, 某些眼睛情况和/或目视外科 (一些狭窄的眼睛、长 eyelashes、amblyopia、nystagmus、LASIK 或其他眼睛 surgeries 等的一些情况)</span><span class="sxs-lookup"><span data-stu-id="06ef0-135">Eye physiology, certain eye conditions and/or eye surgery (some narrow eyes, long eyelashes, amblyopia, nystagmus, some cases of LASIK or other eye surgeries, etc.)</span></span>

<span data-ttu-id="06ef0-136">如果校准失败, 请尝试以下修复之一:</span><span class="sxs-lookup"><span data-stu-id="06ef0-136">If calibration is unsuccessful, try one of these fixes:</span></span> 
- <span data-ttu-id="06ef0-137">清理设备面板</span><span class="sxs-lookup"><span data-stu-id="06ef0-137">Clean your device visor</span></span>
- <span data-ttu-id="06ef0-138">清理眼镜</span><span class="sxs-lookup"><span data-stu-id="06ef0-138">Clean your glasses</span></span>
- <span data-ttu-id="06ef0-139">将设备面板一直推送到</span><span class="sxs-lookup"><span data-stu-id="06ef0-139">Push your device visor all the way in</span></span>
- <span data-ttu-id="06ef0-140">请确保不会阻碍传感器或眼睛 (例如头发)</span><span class="sxs-lookup"><span data-stu-id="06ef0-140">Make sure nothing is obstructing the sensors or your eyes (e.g., hair)</span></span> 
- <span data-ttu-id="06ef0-141">请确保房间内有足够的光线, 并且不受直射直射</span><span class="sxs-lookup"><span data-stu-id="06ef0-141">Make sure there is enough light in your room and that you are not under direct sunlight</span></span>
- <span data-ttu-id="06ef0-142">请确保在校准过程中仔细关注目标</span><span class="sxs-lookup"><span data-stu-id="06ef0-142">Make sure you are carefully following the targets during calibration</span></span>

<span data-ttu-id="06ef0-143">如果你遵循了所有准则, 并且校准仍失败, 则可以在 "**设置** > " "**系统** > **校准**" 中禁用校准提示: *"如果新用户使用此 Hololens, 则会自动要求运行目视校准"* 。</span><span class="sxs-lookup"><span data-stu-id="06ef0-143">If you followed all guidelines and the calibration is still failing, you can disable the calibration prompt in **Settings** > **System** > **Calibration**: *"When a new person uses this Hololens, automatically ask to run eye calibration"* should be turned off.</span></span> <span data-ttu-id="06ef0-144">请注意, 这可能会导致更糟的全息图呈现质量和 discomfort。</span><span class="sxs-lookup"><span data-stu-id="06ef0-144">Please understand that this might result in worse hologram rendering quality and discomfort.</span></span>

### <a name="launching-the-calibration-app-from-settings"></a><span data-ttu-id="06ef0-145">从设置启动校准应用</span><span class="sxs-lookup"><span data-stu-id="06ef0-145">Launching the calibration app from Settings</span></span>
1. <span data-ttu-id="06ef0-146">前往 HoloLens 2 上的 "设置" 页</span><span class="sxs-lookup"><span data-stu-id="06ef0-146">Go to the Settings page on your HoloLens 2</span></span>
    * <span data-ttu-id="06ef0-147">使用 *"开始手势"* 打开 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="06ef0-147">Use the *"Start Gesture"* to bring up the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span> <span data-ttu-id="06ef0-148">或者, 您也可以直接说 *"开始"* 。</span><span class="sxs-lookup"><span data-stu-id="06ef0-148">Alternatively, you can also simply say *"go to start"*.</span></span>
    * <span data-ttu-id="06ef0-149">如果**设置**未固定到 "开始", 请选择 "**所有应用**" 以查看所有应用</span><span class="sxs-lookup"><span data-stu-id="06ef0-149">If **Settings** isn't pinned to Start, select **All Apps** to view all apps</span></span>
    * <span data-ttu-id="06ef0-150">启动**设置**</span><span class="sxs-lookup"><span data-stu-id="06ef0-150">Launch **Settings**</span></span>
2. <span data-ttu-id="06ef0-151">导航到**系统** > 校准 > **目视校准**, 并选择 "**运行目视校准**"</span><span class="sxs-lookup"><span data-stu-id="06ef0-151">Navigate to **System** > **Calibration** > **Eye Calibration** and select **Run eye calibration**</span></span>


### <a name="calibration-when-sharing-a-devicesession"></a><span data-ttu-id="06ef0-152">共享设备/会话时的校准</span><span class="sxs-lookup"><span data-stu-id="06ef0-152">Calibration when sharing a device/session</span></span>
<span data-ttu-id="06ef0-153">Hololens 2 可以在不同人员之间共享, 而无需每个人完成设备设置体验。</span><span class="sxs-lookup"><span data-stu-id="06ef0-153">Hololens 2 can be shared between people without the need for each person to go through the device setup experience.</span></span>
<span data-ttu-id="06ef0-154">如果用户是设备的新用户, 则在将设备放在 head 上时, Hololens 2 将提示用户校准视觉对象。</span><span class="sxs-lookup"><span data-stu-id="06ef0-154">Hololens 2 will prompt the user to calibrate visuals when the device is put on the head if the user is new to the device.</span></span> <span data-ttu-id="06ef0-155">如果用户之前在设备上校准了视觉对象, 则在用户将设备放在打印头上时, 显示器将无缝调整以获得质量和舒适的观看体验。</span><span class="sxs-lookup"><span data-stu-id="06ef0-155">If the user has previously calibrated visuals on the device, the display will be seamlessly adjusted for quality and a comfortable viewing experience when the user puts the device on the head.</span></span> 


## <a name="hololens-v1"></a><span data-ttu-id="06ef0-156">HoloLens (v1)</span><span class="sxs-lookup"><span data-stu-id="06ef0-156">HoloLens (v1)</span></span>
<span data-ttu-id="06ef0-157">校准 IPD (interpupillary 距离) 可以提高视觉对象的质量。</span><span class="sxs-lookup"><span data-stu-id="06ef0-157">Calibrating your IPD (interpupillary distance) can improve the quality of your visuals.</span></span>

### <a name="during-setup"></a><span data-ttu-id="06ef0-158">安装期间</span><span class="sxs-lookup"><span data-stu-id="06ef0-158">During setup</span></span>

![第二步的 IPD finger 对齐屏幕](images/ipd-finger-alignment-300px.jpg)<br>

<span data-ttu-id="06ef0-160">*第二步的 IPD finger 对齐屏幕*</span><span class="sxs-lookup"><span data-stu-id="06ef0-160">*IPD finger-alignment screen at second step*</span></span>

<span data-ttu-id="06ef0-161">在 HoloLens 上, 系统会在安装过程中提示你校准视觉对象。</span><span class="sxs-lookup"><span data-stu-id="06ef0-161">On HoloLens, you'll be prompted to calibrate your visuals during setup.</span></span> <span data-ttu-id="06ef0-162">这允许设备根据用户的[interpupillary 距离](https://en.wikipedia.org/wiki/Interpupillary_distance)(IPD) 调整全息图显示。</span><span class="sxs-lookup"><span data-stu-id="06ef0-162">This allows the device to adjust hologram display according to the user's [interpupillary distance](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span></span> <span data-ttu-id="06ef0-163">使用不正确的 IPD 时, 全息影像可能出现不稳定或距离不正确。</span><span class="sxs-lookup"><span data-stu-id="06ef0-163">With an incorrect IPD, holograms may appear unstable or at an incorrect distance.</span></span>

<span data-ttu-id="06ef0-164">Cortana 引入后, 第一个安装步骤是校准。</span><span class="sxs-lookup"><span data-stu-id="06ef0-164">After Cortana introduces herself, the first setup step is calibration.</span></span> <span data-ttu-id="06ef0-165">建议你在此设置阶段完成校准步骤, 但可以通过等待 Cortana 提示你说 "跳过" 来跳转到。</span><span class="sxs-lookup"><span data-stu-id="06ef0-165">It's recommended that you complete the calibration step during this setup phase, but it can be skipped by waiting until Cortana prompts you to say "Skip" to move on.</span></span>

<span data-ttu-id="06ef0-166">要求用户将其手指与每个眼睛一系列六个目标对齐。</span><span class="sxs-lookup"><span data-stu-id="06ef0-166">Users are asked to align their finger with a series of six targets per eye.</span></span> <span data-ttu-id="06ef0-167">在此过程中, HoloLens 为用户设置了正确的 IPD。</span><span class="sxs-lookup"><span data-stu-id="06ef0-167">Through this process, HoloLens sets the correct IPD for the user.</span></span> <span data-ttu-id="06ef0-168">如果需要更新或调整新用户的校准, 可以使用校准应用在安装程序外运行。</span><span class="sxs-lookup"><span data-stu-id="06ef0-168">If the calibration needs to be updated or adjusted for a new user, it can be run outside of setup using the Calibration app.</span></span>

### <a name="calibration-app"></a><span data-ttu-id="06ef0-169">校准应用</span><span class="sxs-lookup"><span data-stu-id="06ef0-169">Calibration app</span></span>

<span data-ttu-id="06ef0-170">可随时通过校准应用执行校准。</span><span class="sxs-lookup"><span data-stu-id="06ef0-170">Calibration can be performed any time through the Calibration app.</span></span> <span data-ttu-id="06ef0-171">校准应用默认安装, 并可通过 "开始" 菜单或 "设置" 应用进行访问。</span><span class="sxs-lookup"><span data-stu-id="06ef0-171">The Calibration app is installed by default and may be accessed from the Start menu, or through the Settings app.</span></span> <span data-ttu-id="06ef0-172">如果要改善视觉对象的质量或为新用户校准视觉对象, 则建议使用校准。</span><span class="sxs-lookup"><span data-stu-id="06ef0-172">Calibration is recommended if you'd like to improve the quality of your visuals or calibrate visuals for a new user.</span></span>

<span data-ttu-id="06ef0-173">**启动应用程序开始**</span><span class="sxs-lookup"><span data-stu-id="06ef0-173">**Launching the app from Start**</span></span>
1. <span data-ttu-id="06ef0-174">使用[布隆](gestures.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="06ef0-174">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="06ef0-175">选择 **+** 若要查看所有应用。</span><span class="sxs-lookup"><span data-stu-id="06ef0-175">Select **+** to view all apps.</span></span>
3. <span data-ttu-id="06ef0-176">启动**校准**。</span><span class="sxs-lookup"><span data-stu-id="06ef0-176">Launch **Calibration**.</span></span>

![从 shell 访问校准应用程序](images/calibration-shell.png)

![启动后显示为活动多维数据集的校准应用](images/calibration-livecube-200px.png)

<span data-ttu-id="06ef0-179">**从设置启动应用**</span><span class="sxs-lookup"><span data-stu-id="06ef0-179">**Launching the app from Settings**</span></span>
1. <span data-ttu-id="06ef0-180">使用[布隆](gestures.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)。</span><span class="sxs-lookup"><span data-stu-id="06ef0-180">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="06ef0-181">选择 **+** 若要查看所有应用，如果**设置**不固定到开始。</span><span class="sxs-lookup"><span data-stu-id="06ef0-181">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="06ef0-182">启动**设置**。</span><span class="sxs-lookup"><span data-stu-id="06ef0-182">Launch **Settings**.</span></span>
4. <span data-ttu-id="06ef0-183">导航到 "**系统** > **实用程序**" 并选择 "**打开校准**"。</span><span class="sxs-lookup"><span data-stu-id="06ef0-183">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

![从 "设置" 应用启动校准应用](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a><span data-ttu-id="06ef0-185">沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="06ef0-185">Immersive headsets</span></span>

<span data-ttu-id="06ef0-186">若要更改耳机内的 IPD, 请打开设置应用并导航到**混合现实** > **耳机显示**, 并移动滑块控件。</span><span class="sxs-lookup"><span data-stu-id="06ef0-186">To change IPD within your headset, open the Settings app and navigate to **Mixed reality** > **Headset display** and move the slider control.</span></span> <span data-ttu-id="06ef0-187">你将在你的耳机上实时看到更改。</span><span class="sxs-lookup"><span data-stu-id="06ef0-187">You’ll see the changes in real time in your headset.</span></span> <span data-ttu-id="06ef0-188">如果你知道 IPD, 可能是由于访问 optometrist, 你也可以直接输入。</span><span class="sxs-lookup"><span data-stu-id="06ef0-188">If you know your IPD, maybe from a visit to the optometrist, you can enter it directly as well.</span></span>

<span data-ttu-id="06ef0-189">你还可以通过转到电脑上的 "**设置** > "**混合现实** > **耳机显示**来调整此设置。</span><span class="sxs-lookup"><span data-stu-id="06ef0-189">You can also adjust this setting by going to **Settings** > **Mixed reality** > **Headset display** on your PC.</span></span>

<span data-ttu-id="06ef0-190">如果头戴显示设备不支持 IPD 自定义, 则会禁用此设置。</span><span class="sxs-lookup"><span data-stu-id="06ef0-190">If your headset does not support IPD customization, this setting will be disabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="06ef0-191">请参阅</span><span class="sxs-lookup"><span data-stu-id="06ef0-191">See also</span></span>
* [<span data-ttu-id="06ef0-192">HoloLens 的环境注意事项</span><span class="sxs-lookup"><span data-stu-id="06ef0-192">Environment considerations for HoloLens</span></span>](environment-considerations-for-hololens.md)
