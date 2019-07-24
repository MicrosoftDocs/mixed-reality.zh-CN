---
title: HoloLens 故障排除
description: Microsoft HoloLens 的故障排除步骤。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 问题、错误、故障排除、修复、帮助、支持、HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550880"
---
# <a name="hololens-troubleshooting"></a><span data-ttu-id="843ee-104">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="843ee-104">HoloLens Troubleshooting</span></span>

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a><span data-ttu-id="843ee-105">HoloLens 无响应或不启动</span><span class="sxs-lookup"><span data-stu-id="843ee-105">My HoloLens is unresponsive or won’t boot</span></span>

<span data-ttu-id="843ee-106">如果 HoloLens 无法启动:</span><span class="sxs-lookup"><span data-stu-id="843ee-106">If your HoloLens won't boot:</span></span>
* <span data-ttu-id="843ee-107">如果电源按钮的 Led 指示灯未亮起, 或只有1个 LED 闪烁, 则您可能需要为 HoloLens 充电。</span><span class="sxs-lookup"><span data-stu-id="843ee-107">If the LEDs by the power button don't light up, or only 1 LED briefly blinks, you may need to charge your HoloLens.</span></span>
* <span data-ttu-id="843ee-108">如果在按下电源按钮时指示灯亮起但在显示器上看不到任何内容, 请按住电源按钮, 直到电源按钮关闭所有5个 Led。</span><span class="sxs-lookup"><span data-stu-id="843ee-108">If the LEDs light up when you press the power button but you can't see anything on the displays, hold the power button until all 5 of the LEDs by the power button turn off.</span></span>

<span data-ttu-id="843ee-109">如果 HoloLens 已冻结或无响应:</span><span class="sxs-lookup"><span data-stu-id="843ee-109">If your HoloLens becomes frozen or unresponsive:</span></span>
* <span data-ttu-id="843ee-110">按下电源按钮关闭 HoloLens, 直到电源按钮的所有5个 Led 关闭, 或者如果 Led 无响应, 则为10秒。</span><span class="sxs-lookup"><span data-stu-id="843ee-110">Turn off your HoloLens by pressing the power button until all 5 of the LEDs by the power button turn themselves off, or for 10 seconds if the LEDs are unresponsive.</span></span> <span data-ttu-id="843ee-111">再次按下 "电源" 按钮, 启动。</span><span class="sxs-lookup"><span data-stu-id="843ee-111">Press the power button again to boot.</span></span>

<span data-ttu-id="843ee-112">如果以下步骤不起作用:</span><span class="sxs-lookup"><span data-stu-id="843ee-112">If these steps don't work:</span></span>
* <span data-ttu-id="843ee-113">你可以尝试[恢复你的设备](reset-or-recover-your-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="843ee-113">You can try [recovering your device](reset-or-recover-your-hololens.md).</span></span>

## <a name="holograms-dont-look-good-or-are-moving-around"></a><span data-ttu-id="843ee-114">全息影像看起来不好或正在四处移动。</span><span class="sxs-lookup"><span data-stu-id="843ee-114">Holograms don't look good or are moving around.</span></span>

<span data-ttu-id="843ee-115">如果你的全息影像不稳定、jumpy 或不正确, 请尝试以下其中一项修复:</span><span class="sxs-lookup"><span data-stu-id="843ee-115">If your holograms are unstable, jumpy, or don’t look right, try one of these fixes:</span></span>
* <span data-ttu-id="843ee-116">清洗设备面板, 确保没有任何阻碍传感器的情况。</span><span class="sxs-lookup"><span data-stu-id="843ee-116">Clean your device visor and make sure nothing is obstructing the sensors.</span></span>
* <span data-ttu-id="843ee-117">请确保空间中有足够的光线。</span><span class="sxs-lookup"><span data-stu-id="843ee-117">Make sure there’s enough light in your room.</span></span>
* <span data-ttu-id="843ee-118">尝试浏览并查看你的环境, 以便 HoloLens 可以更完整地扫描它们。</span><span class="sxs-lookup"><span data-stu-id="843ee-118">Try walking around and looking at your surroundings so HoloLens can scan them more completely.</span></span>
* <span data-ttu-id="843ee-119">尝试运行校准应用。</span><span class="sxs-lookup"><span data-stu-id="843ee-119">Try running the Calibration app.</span></span> <span data-ttu-id="843ee-120">它校准你的 HoloLens, 最适合你的眼睛。</span><span class="sxs-lookup"><span data-stu-id="843ee-120">It calibrates your HoloLens to work best for your eyes.</span></span> <span data-ttu-id="843ee-121">中转到 "**设置** > " "**系统** > " "**实用工具**"。</span><span class="sxs-lookup"><span data-stu-id="843ee-121">Go to **Settings** > **System** > **Utilities**.</span></span> <span data-ttu-id="843ee-122">在校准下, 选择 "**打开校准**"。</span><span class="sxs-lookup"><span data-stu-id="843ee-122">Under Calibration, select **Open Calibration**.</span></span>
* <span data-ttu-id="843ee-123">如果运行校准应用后仍遇到问题, 请使用传感器优化应用来优化设备传感器。</span><span class="sxs-lookup"><span data-stu-id="843ee-123">If you’re still having trouble after running the Calibration app, use the Sensor Tuning app to tune your device sensors.</span></span> <span data-ttu-id="843ee-124">中转到 "**设置** > " "**系统** > " "**实用工具**"。</span><span class="sxs-lookup"><span data-stu-id="843ee-124">Go to **Settings** > **System** > **Utilities**.</span></span> <span data-ttu-id="843ee-125">在 "传感器调整" 下, 选择 "**打开传感器优化**"。</span><span class="sxs-lookup"><span data-stu-id="843ee-125">Under Sensor tuning, select **Open Sensor Tuning**.</span></span>

## <a name="hololens-doesnt-respond-to-my-gestures"></a><span data-ttu-id="843ee-126">HoloLens 未响应我的手势。</span><span class="sxs-lookup"><span data-stu-id="843ee-126">HoloLens doesn’t respond to my gestures.</span></span>

<span data-ttu-id="843ee-127">若要确保 HoloLens 能看到你的手势, 请将你的手置于手势帧中, 这会在你的任意一侧延伸几个英尺。</span><span class="sxs-lookup"><span data-stu-id="843ee-127">To make sure HoloLens can see your gestures, keep your hand in the gesture frame, which extends a couple of feet on either side of you.</span></span> <span data-ttu-id="843ee-128">当 HoloLens 能看到你的手时, 光标将从点变为圆圈。</span><span class="sxs-lookup"><span data-stu-id="843ee-128">When HoloLens can see your hand, the cursor will change from a dot to a ring.</span></span> <span data-ttu-id="843ee-129">详细了解如何使用[笔势](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="843ee-129">Learn more about using [gestures](gestures.md).</span></span>

<span data-ttu-id="843ee-130">如果你的环境太暗, 则 HoloLens 可能看不到你的手, 因此请确保有足够的光线。</span><span class="sxs-lookup"><span data-stu-id="843ee-130">If your environment is too dark, HoloLens might not see your hand, so make sure there’s enough light.</span></span>

<span data-ttu-id="843ee-131">如果你的面板具有指纹或涂抹, 请使用 HoloLens 随附的 microfiber 清洁抹布来轻轻地清理面板。</span><span class="sxs-lookup"><span data-stu-id="843ee-131">If your visor has fingerprints or smudge, please use the microfiber cleaning cloth that came with the HoloLens to clean your visor gently.</span></span>

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a><span data-ttu-id="843ee-132">HoloLens 未响应语音命令。</span><span class="sxs-lookup"><span data-stu-id="843ee-132">HoloLens doesn’t respond to my voice commands.</span></span>

<span data-ttu-id="843ee-133">如果 Cortana 没有响应语音命令, 请确保 Cortana 已打开。</span><span class="sxs-lookup"><span data-stu-id="843ee-133">If Cortana isn’t responding to your voice commands, make sure Cortana is turned on.</span></span> <span data-ttu-id="843ee-134">在 "所有应用" 列表中, 选择 "Cortana >" 菜单 > 笔记本 ">" 设置 "进行更改。</span><span class="sxs-lookup"><span data-stu-id="843ee-134">On the All apps list, select Cortana > Menu > Notebook > Settings to make changes.</span></span> <span data-ttu-id="843ee-135">若要详细了解你可以说的内容, 请参阅使用语音控制 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="843ee-135">To learn more about what you can say, see Use your voice to control HoloLens.</span></span>

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a><span data-ttu-id="843ee-136">我无法放置全息影像或查看以前放置的全息影像。</span><span class="sxs-lookup"><span data-stu-id="843ee-136">I can’t place holograms or see holograms I previously placed.</span></span>

<span data-ttu-id="843ee-137">如果 HoloLens 无法映射或加载空间, 它将进入限制模式, 并且你将无法放置全息影像或查看已放置的全息影像。</span><span class="sxs-lookup"><span data-stu-id="843ee-137">If HoloLens can’t map or load your space, it will enter Limited mode and you won’t be able to place holograms or see holograms you’ve placed.</span></span> <span data-ttu-id="843ee-138">可以尝试以下操作：</span><span class="sxs-lookup"><span data-stu-id="843ee-138">Here are some things to try:</span></span>
* <span data-ttu-id="843ee-139">请确保环境中有足够的光线, 以便 HoloLens 能够查看和映射空间。</span><span class="sxs-lookup"><span data-stu-id="843ee-139">Make sure there’s enough light in your environment so HoloLens can see and map the space.</span></span>
* <span data-ttu-id="843ee-140">请确保已连接到 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="843ee-140">Make sure you’re connected to a Wi-Fi network.</span></span> <span data-ttu-id="843ee-141">如果你未连接到 Wi-fi, 则 HoloLens 无法识别并加载已知的空间。</span><span class="sxs-lookup"><span data-stu-id="843ee-141">If you’re not connected to Wi-Fi, HoloLens can’t identify and load a known space.</span></span>
* <span data-ttu-id="843ee-142">如果需要创建新空间, 请连接到 Wi-fi, 然后重启 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="843ee-142">If you need to create a new space, connect to Wi-Fi, then restart your HoloLens.</span></span>
* <span data-ttu-id="843ee-143">若要查看正确的空间是否处于活动状态, 或要手动加载空间, 请参阅**设置** > **系统** > **空间**。</span><span class="sxs-lookup"><span data-stu-id="843ee-143">To see if the correct space is active, or to manually load a space, go to **Settings** > **System** > **Spaces**.</span></span>
* <span data-ttu-id="843ee-144">如果加载了正确的空间并且仍有问题, 则空间可能已损坏。</span><span class="sxs-lookup"><span data-stu-id="843ee-144">If the correct space is loaded and you’re still having problems, the space may be corrupt.</span></span> <span data-ttu-id="843ee-145">若要解决此问题, 请选择空间, 然后选择 "删除"。</span><span class="sxs-lookup"><span data-stu-id="843ee-145">To fix this, select the space, then select Remove.</span></span> <span data-ttu-id="843ee-146">删除空间后, HoloLens 将开始映射你的环境并创建新空间。</span><span class="sxs-lookup"><span data-stu-id="843ee-146">Once the space is removed, HoloLens will start mapping your surroundings and create a new space.</span></span>

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a><span data-ttu-id="843ee-147">我的 HoloLens 经常进入限制模式或显示 "跟踪丢失" 消息。</span><span class="sxs-lookup"><span data-stu-id="843ee-147">My HoloLens frequently enters Limited mode or shows a “Tracking lost” message.</span></span>

<span data-ttu-id="843ee-148">如果你的设备通常显示 "限制模式" 或 "跟踪丢失" 消息, 请尝试从[我的全息影像看起来不太好或正在四处移动](#holograms-dont-look-good-or-are-moving-around)。</span><span class="sxs-lookup"><span data-stu-id="843ee-148">If your device often shows a "limited mode" or "tracking lost" message, try the suggestions from [My Holograms don't look good or are moving around](#holograms-dont-look-good-or-are-moving-around).</span></span>

## <a name="my-hololens-cant-tell-what-space-im-in"></a><span data-ttu-id="843ee-149">我的 HoloLens 无法判断我所在的空间。</span><span class="sxs-lookup"><span data-stu-id="843ee-149">My HoloLens can’t tell what space I’m in.</span></span>

<span data-ttu-id="843ee-150">如果你的 HoloLens 无法自动识别并加载你所在的空间, 请确保你已连接到 Wi-fi, 房间内有充足的光线, 并且没有对周围的任何重大更改。</span><span class="sxs-lookup"><span data-stu-id="843ee-150">If your HoloLens can’t automatically identify and load the space you’re in, make sure you’re connected to Wi-Fi, there’s plenty of light in the room, and there haven’t been any major changes to the surroundings.</span></span> <span data-ttu-id="843ee-151">还可以通过转到 "**设置** > " "**系统** > **空间**" 手动加载空间或管理空间。</span><span class="sxs-lookup"><span data-stu-id="843ee-151">You can also load a space manually or manage your spaces by going to **Settings** > **System** > **Spaces**.</span></span>

## <a name="im-getting-a-low-disk-space-error"></a><span data-ttu-id="843ee-152">我收到 "磁盘空间不足" 错误。</span><span class="sxs-lookup"><span data-stu-id="843ee-152">I’m getting a “low disk space” error.</span></span>

<span data-ttu-id="843ee-153">你需要通过执行以下一项或多项操作来释放一些存储空间:</span><span class="sxs-lookup"><span data-stu-id="843ee-153">You’ll need to free up some storage space by doing one or more of the following:</span></span>
* <span data-ttu-id="843ee-154">删除某些未使用的空间。</span><span class="sxs-lookup"><span data-stu-id="843ee-154">Delete some unused spaces.</span></span> <span data-ttu-id="843ee-155">中转到 "**设置** > " "**系统** > **空间**", 选择不再需要的空间, 然后选择 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="843ee-155">Go to **Settings** > **System** > **Spaces**, select a space you no longer need, and then select **Remove**.</span></span>
* <span data-ttu-id="843ee-156">删除某些已放置的全息影像。</span><span class="sxs-lookup"><span data-stu-id="843ee-156">Remove some of the holograms you’ve placed.</span></span>
* <span data-ttu-id="843ee-157">删除照片应用中的某些图片和视频。</span><span class="sxs-lookup"><span data-stu-id="843ee-157">Delete some pictures and videos in the Photos app.</span></span>
* <span data-ttu-id="843ee-158">从 HoloLens 卸载某些应用。</span><span class="sxs-lookup"><span data-stu-id="843ee-158">Uninstall some apps from your HoloLens.</span></span> <span data-ttu-id="843ee-159">在 "所有应用" 列表中, 点击并按住你要卸载的应用, 然后选择 "**卸载**"。</span><span class="sxs-lookup"><span data-stu-id="843ee-159">In the All apps list, tap and hold the app you want to uninstall, and then select **Uninstall**.</span></span>

## <a name="my-hololens-cant-create-a-new-space"></a><span data-ttu-id="843ee-160">我的 HoloLens 无法创建新的空间。</span><span class="sxs-lookup"><span data-stu-id="843ee-160">My HoloLens can’t create a new space.</span></span>

<span data-ttu-id="843ee-161">最可能的问题是在存储空间不足的情况下运行。</span><span class="sxs-lookup"><span data-stu-id="843ee-161">The most likely problem is that you’re running low on storage space.</span></span> <span data-ttu-id="843ee-162">请尝试上述其中一个[提示](#im-getting-a-low-disk-space-error)以释放一些磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="843ee-162">Try one of the [tips above](#im-getting-a-low-disk-space-error) to free up some disk space.</span></span>
