---
title: HoloLens 故障排除
description: 对于 Microsoft HoloLens 的故障排除步骤。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 问题、 bug、 进行故障排除、 修复、 帮助、 支持、 HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590109"
---
# <a name="hololens-troubleshooting"></a><span data-ttu-id="13e1c-104">HoloLens 故障排除</span><span class="sxs-lookup"><span data-stu-id="13e1c-104">HoloLens Troubleshooting</span></span>

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a><span data-ttu-id="13e1c-105">我 HoloLens 无响应或无法启动</span><span class="sxs-lookup"><span data-stu-id="13e1c-105">My HoloLens is unresponsive or won’t boot</span></span>

<span data-ttu-id="13e1c-106">如果你 HoloLens 无法启动：</span><span class="sxs-lookup"><span data-stu-id="13e1c-106">If your HoloLens won't boot:</span></span>
* <span data-ttu-id="13e1c-107">如果由电源按钮不指示灯都会保持运行，或只有 1 LED 短暂地闪烁，您可能需要从你 HoloLens 收取相关费用。</span><span class="sxs-lookup"><span data-stu-id="13e1c-107">If the LEDs by the power button don't light up, or only 1 LED briefly blinks, you may need to charge your HoloLens.</span></span>
* <span data-ttu-id="13e1c-108">如果指示灯亮起时按下电源按钮，但您不能在显示器上看到任何内容，，保留电源按钮，直到所有 5 个 Led 的电源按钮都将关闭。</span><span class="sxs-lookup"><span data-stu-id="13e1c-108">If the LEDs light up when you press the power button but you can't see anything on the displays, hold the power button until all 5 of the LEDs by the power button turn off.</span></span>

<span data-ttu-id="13e1c-109">如果你 HoloLens 变得冻结或无响应：</span><span class="sxs-lookup"><span data-stu-id="13e1c-109">If your HoloLens becomes frozen or unresponsive:</span></span>
* <span data-ttu-id="13e1c-110">通过按电源按钮，直到所有 5 个 Led 的电源按钮本身，打开或关闭 10 秒钟，如果的 Led 为无响应关闭你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="13e1c-110">Turn off your HoloLens by pressing the power button until all 5 of the LEDs by the power button turn themselves off, or for 10 seconds if the LEDs are unresponsive.</span></span> <span data-ttu-id="13e1c-111">按下电源按钮再次启动。</span><span class="sxs-lookup"><span data-stu-id="13e1c-111">Press the power button again to boot.</span></span>

<span data-ttu-id="13e1c-112">如果这些步骤不起作用：</span><span class="sxs-lookup"><span data-stu-id="13e1c-112">If these steps don't work:</span></span>
* <span data-ttu-id="13e1c-113">你可以尝试[恢复你的设备](reset-or-recover-your-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="13e1c-113">You can try [recovering your device](reset-or-recover-your-hololens.md).</span></span>

## <a name="holograms-dont-look-good-or-are-moving-around"></a><span data-ttu-id="13e1c-114">全息看起来不好或四处移动。</span><span class="sxs-lookup"><span data-stu-id="13e1c-114">Holograms don't look good or are moving around.</span></span>

<span data-ttu-id="13e1c-115">如果你全息不稳定、 动摇，或者看起来不合适，请尝试这些修复程序之一：</span><span class="sxs-lookup"><span data-stu-id="13e1c-115">If your holograms are unstable, jumpy, or don’t look right, try one of these fixes:</span></span>
* <span data-ttu-id="13e1c-116">清理设备面板，并确保执行任何操作都不阻止传感器。</span><span class="sxs-lookup"><span data-stu-id="13e1c-116">Clean your device visor and make sure nothing is obstructing the sensors.</span></span>
* <span data-ttu-id="13e1c-117">请确保你的聊天室中没有足够 light。</span><span class="sxs-lookup"><span data-stu-id="13e1c-117">Make sure there’s enough light in your room.</span></span>
* <span data-ttu-id="13e1c-118">请尝试移动办公了并查看周围的环境是 HoloLens 可以对其进行扫描更完整地。</span><span class="sxs-lookup"><span data-stu-id="13e1c-118">Try walking around and looking at your surroundings so HoloLens can scan them more completely.</span></span>
* <span data-ttu-id="13e1c-119">尝试运行校准应用。</span><span class="sxs-lookup"><span data-stu-id="13e1c-119">Try running the Calibration app.</span></span> <span data-ttu-id="13e1c-120">它并校验适合你自己在 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="13e1c-120">It calibrates your HoloLens to work best for your eyes.</span></span> <span data-ttu-id="13e1c-121">转到**设置** > **系统** > **实用程序**。</span><span class="sxs-lookup"><span data-stu-id="13e1c-121">Go to **Settings** > **System** > **Utilities**.</span></span> <span data-ttu-id="13e1c-122">在下校准，选择**打开校准**。</span><span class="sxs-lookup"><span data-stu-id="13e1c-122">Under Calibration, select **Open Calibration**.</span></span>
* <span data-ttu-id="13e1c-123">如果仍在运行校准应用程序后遇到问题，可以使用传感器优化应用程序来优化设备传感器。</span><span class="sxs-lookup"><span data-stu-id="13e1c-123">If you’re still having trouble after running the Calibration app, use the Sensor Tuning app to tune your device sensors.</span></span> <span data-ttu-id="13e1c-124">转到**设置** > **系统** > **实用程序**。</span><span class="sxs-lookup"><span data-stu-id="13e1c-124">Go to **Settings** > **System** > **Utilities**.</span></span> <span data-ttu-id="13e1c-125">在下传感器优化，选择**打开传感器优化**。</span><span class="sxs-lookup"><span data-stu-id="13e1c-125">Under Sensor tuning, select **Open Sensor Tuning**.</span></span>

## <a name="hololens-doesnt-respond-to-my-gestures"></a><span data-ttu-id="13e1c-126">HoloLens 不响应我笔势。</span><span class="sxs-lookup"><span data-stu-id="13e1c-126">HoloLens doesn’t respond to my gestures.</span></span>

<span data-ttu-id="13e1c-127">若要确保 HoloLens 可以看到你笔势，请在手势框架中，扩展了几个立足于您的任何一侧保留您的手。</span><span class="sxs-lookup"><span data-stu-id="13e1c-127">To make sure HoloLens can see your gestures, keep your hand in the gesture frame, which extends a couple of feet on either side of you.</span></span> <span data-ttu-id="13e1c-128">时 HoloLens 可以看到您的手，光标就会将更改从一个圆点为一个环。</span><span class="sxs-lookup"><span data-stu-id="13e1c-128">When HoloLens can see your hand, the cursor will change from a dot to a ring.</span></span> <span data-ttu-id="13e1c-129">深入了解如何使用[手势](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="13e1c-129">Learn more about using [gestures](gestures.md).</span></span>

<span data-ttu-id="13e1c-130">如果你的环境是否太暗，HoloLens 不可能会看到您的手，因此请确保足够指示灯亮起。</span><span class="sxs-lookup"><span data-stu-id="13e1c-130">If your environment is too dark, HoloLens might not see your hand, so make sure there’s enough light.</span></span>

<span data-ttu-id="13e1c-131">如果你面板具有指纹或涂抹，请使用清洁随附 HoloLens 轻轻地清理在面板的布种微纤维。</span><span class="sxs-lookup"><span data-stu-id="13e1c-131">If your visor has fingerprints or smudge, please use the microfiber cleaning cloth that came with the HoloLens to clean your visor gently.</span></span>

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a><span data-ttu-id="13e1c-132">HoloLens 不应对我语音命令。</span><span class="sxs-lookup"><span data-stu-id="13e1c-132">HoloLens doesn’t respond to my voice commands.</span></span>

<span data-ttu-id="13e1c-133">如果 Cortana 语音命令没有响应，请确保启用 Cortana。</span><span class="sxs-lookup"><span data-stu-id="13e1c-133">If Cortana isn’t responding to your voice commands, make sure Cortana is turned on.</span></span> <span data-ttu-id="13e1c-134">在所有应用列表中，选择 Cortana > 菜单 > 笔记本 > 设置进行更改。</span><span class="sxs-lookup"><span data-stu-id="13e1c-134">On the All apps list, select Cortana > Menu > Notebook > Settings to make changes.</span></span> <span data-ttu-id="13e1c-135">若要了解有关您可以说的详细信息，请参阅使用语音控制 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="13e1c-135">To learn more about what you can say, see Use your voice to control HoloLens.</span></span>

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a><span data-ttu-id="13e1c-136">无法将放置全息或请参阅我以前放置的全息。</span><span class="sxs-lookup"><span data-stu-id="13e1c-136">I can’t place holograms or see holograms I previously placed.</span></span>

<span data-ttu-id="13e1c-137">如果 HoloLens 不能映射或加载你的空间，它将进入 Limited 模式下，并将无法放置全息或请参阅的全息已放置。</span><span class="sxs-lookup"><span data-stu-id="13e1c-137">If HoloLens can’t map or load your space, it will enter Limited mode and you won’t be able to place holograms or see holograms you’ve placed.</span></span> <span data-ttu-id="13e1c-138">可以尝试以下操作：</span><span class="sxs-lookup"><span data-stu-id="13e1c-138">Here are some things to try:</span></span>
* <span data-ttu-id="13e1c-139">请确保有足以阐明您的环境中使 HoloLens 可看到并映射空间。</span><span class="sxs-lookup"><span data-stu-id="13e1c-139">Make sure there’s enough light in your environment so HoloLens can see and map the space.</span></span>
* <span data-ttu-id="13e1c-140">请确保已连接到 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="13e1c-140">Make sure you’re connected to a Wi-Fi network.</span></span> <span data-ttu-id="13e1c-141">如果您没有连接到 Wi-fi，HoloLens 不能标识和加载已知的空间。</span><span class="sxs-lookup"><span data-stu-id="13e1c-141">If you’re not connected to Wi-Fi, HoloLens can’t identify and load a known space.</span></span>
* <span data-ttu-id="13e1c-142">如果需要创建一个新的空间，连接到 Wi-fi，然后重新启动你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="13e1c-142">If you need to create a new space, connect to Wi-Fi, then restart your HoloLens.</span></span>
* <span data-ttu-id="13e1c-143">若要查看正确的空间是否处于活动状态，或手动加载一个空格，请转到**设置** > **系统** > **空格**。</span><span class="sxs-lookup"><span data-stu-id="13e1c-143">To see if the correct space is active, or to manually load a space, go to **Settings** > **System** > **Spaces**.</span></span>
* <span data-ttu-id="13e1c-144">如果加载正确的空间，并且仍遇到问题，空间可能已损坏。</span><span class="sxs-lookup"><span data-stu-id="13e1c-144">If the correct space is loaded and you’re still having problems, the space may be corrupt.</span></span> <span data-ttu-id="13e1c-145">若要解决此问题，选择的空间，然后选择删除。</span><span class="sxs-lookup"><span data-stu-id="13e1c-145">To fix this, select the space, then select Remove.</span></span> <span data-ttu-id="13e1c-146">一旦删除了空格，HoloLens 将开始映射周围的环境并创建一个新的空间。</span><span class="sxs-lookup"><span data-stu-id="13e1c-146">Once the space is removed, HoloLens will start mapping your surroundings and create a new space.</span></span>

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a><span data-ttu-id="13e1c-147">我 HoloLens 频繁进入 Limited 模式下，或者会显示"跟踪丢失"消息。</span><span class="sxs-lookup"><span data-stu-id="13e1c-147">My HoloLens frequently enters Limited mode or shows a “Tracking lost” message.</span></span>

<span data-ttu-id="13e1c-148">如果你的设备通常会显示"限制的模式"或"跟踪丢失"消息，请尝试从建议[我全息看起来不好或四处移动](#holograms-dont-look-good-or-are-moving-around)。</span><span class="sxs-lookup"><span data-stu-id="13e1c-148">If your device often shows a "limited mode" or "tracking lost" message, try the suggestions from [My Holograms don't look good or are moving around](#holograms-dont-look-good-or-are-moving-around).</span></span>

## <a name="my-hololens-cant-tell-what-space-im-in"></a><span data-ttu-id="13e1c-149">我 HoloLens 不能告诉我在何种空间。</span><span class="sxs-lookup"><span data-stu-id="13e1c-149">My HoloLens can’t tell what space I’m in.</span></span>

<span data-ttu-id="13e1c-150">如果你 HoloLens 无法自动识别并加载您在的空间，请确保已连接到的 Wi-fi、 有很多的空间中的光和未存在于环境的任何重大更改。</span><span class="sxs-lookup"><span data-stu-id="13e1c-150">If your HoloLens can’t automatically identify and load the space you’re in, make sure you’re connected to Wi-Fi, there’s plenty of light in the room, and there haven’t been any major changes to the surroundings.</span></span> <span data-ttu-id="13e1c-151">此外可以手动加载一个空格，或通过转到管理你空格**设置** > **系统** > **空格**。</span><span class="sxs-lookup"><span data-stu-id="13e1c-151">You can also load a space manually or manage your spaces by going to **Settings** > **System** > **Spaces**.</span></span>

## <a name="im-getting-a-low-disk-space-error"></a><span data-ttu-id="13e1c-152">我收到"磁盘空间不足"错误。</span><span class="sxs-lookup"><span data-stu-id="13e1c-152">I’m getting a “low disk space” error.</span></span>

<span data-ttu-id="13e1c-153">你将需要释放一些存储空间，通过执行一个或多个以下操作：</span><span class="sxs-lookup"><span data-stu-id="13e1c-153">You’ll need to free up some storage space by doing one or more of the following:</span></span>
* <span data-ttu-id="13e1c-154">删除一些未使用的空间。</span><span class="sxs-lookup"><span data-stu-id="13e1c-154">Delete some unused spaces.</span></span> <span data-ttu-id="13e1c-155">转到**设置** > **系统** > **空间**，选择一个空格，也不再需要并选择**删除**.</span><span class="sxs-lookup"><span data-stu-id="13e1c-155">Go to **Settings** > **System** > **Spaces**, select a space you no longer need, and then select **Remove**.</span></span>
* <span data-ttu-id="13e1c-156">删除一些已放置的全息。</span><span class="sxs-lookup"><span data-stu-id="13e1c-156">Remove some of the holograms you’ve placed.</span></span>
* <span data-ttu-id="13e1c-157">删除某些图片和视频的照片应用中。</span><span class="sxs-lookup"><span data-stu-id="13e1c-157">Delete some pictures and videos in the Photos app.</span></span>
* <span data-ttu-id="13e1c-158">从你 HoloLens 卸载某些应用程序。</span><span class="sxs-lookup"><span data-stu-id="13e1c-158">Uninstall some apps from your HoloLens.</span></span> <span data-ttu-id="13e1c-159">在所有应用程序列表中，点击并按住应用的程序想要卸载，然后选择**卸载**。</span><span class="sxs-lookup"><span data-stu-id="13e1c-159">In the All apps list, tap and hold the app you want to uninstall, and then select **Uninstall**.</span></span>

## <a name="my-hololens-cant-create-a-new-space"></a><span data-ttu-id="13e1c-160">我 HoloLens 不能创建一个新的空间。</span><span class="sxs-lookup"><span data-stu-id="13e1c-160">My HoloLens can’t create a new space.</span></span>

<span data-ttu-id="13e1c-161">最可能的问题是，您要运行存储空间不足。</span><span class="sxs-lookup"><span data-stu-id="13e1c-161">The most likely problem is that you’re running low on storage space.</span></span> <span data-ttu-id="13e1c-162">请尝试之一[上述提示](#im-getting-a-low-disk-space-error)以释放一些磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="13e1c-162">Try one of the [tips above](#im-getting-a-low-disk-space-error) to free up some disk space.</span></span>
