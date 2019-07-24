---
title: 更新适用于 Windows Mixed Reality 的 SteamVR 应用程序
description: 更新 SteamVR 应用程序以最大程度地提高 Windows Mixed Reality 耳机的最佳实践。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, 兼容性
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548679"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a><span data-ttu-id="876b8-104">更新适用于 Windows Mixed Reality 的 SteamVR 应用程序</span><span class="sxs-lookup"><span data-stu-id="876b8-104">Updating your SteamVR application for Windows Mixed Reality</span></span>

<span data-ttu-id="876b8-105">我们鼓励开发人员测试并优化其 SteamVR 体验, 以便在 Windows Mixed Reality 耳机上运行。</span><span class="sxs-lookup"><span data-stu-id="876b8-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="876b8-106">本文档介绍了开发人员可以执行的一些常见改进, 以确保其体验在 Windows Mixed Reality 上运行良好。</span><span class="sxs-lookup"><span data-stu-id="876b8-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="876b8-107">初始设置说明</span><span class="sxs-lookup"><span data-stu-id="876b8-107">Initial setup instructions</span></span>

<span data-ttu-id="876b8-108">若要在 Windows Mixed Reality 上开始测试您的游戏或应用程序, 请确保先遵循我们的[入门指南。](http://aka.ms/WindowsMixedRealitySteamVR)</span><span class="sxs-lookup"><span data-stu-id="876b8-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](http://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="876b8-109">控制器型号</span><span class="sxs-lookup"><span data-stu-id="876b8-109">Controller Models</span></span>
1. <span data-ttu-id="876b8-110">如果应用呈现控制器模型:</span><span class="sxs-lookup"><span data-stu-id="876b8-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="876b8-111">使用[Windows Mixed Reality 运动控制器模型](motion-controllers.md#rendering-the-motion-controller-model)</span><span class="sxs-lookup"><span data-stu-id="876b8-111">Use the [Windows Mixed Reality motion controller models](motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="876b8-112">使用 IVRRenderModel:: GetComponentState 获取对组件部件的本地转换 (例如</span><span class="sxs-lookup"><span data-stu-id="876b8-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="876b8-113">指针姿势)</span><span class="sxs-lookup"><span data-stu-id="876b8-113">Pointer pose)</span></span>
2. <span data-ttu-id="876b8-114">具有左右手使用习惯概念的经验应从输入 Api 获取提示以区分控制器[(Unity 示例)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="876b8-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="876b8-115">Controls</span><span class="sxs-lookup"><span data-stu-id="876b8-115">Controls</span></span>

<span data-ttu-id="876b8-116">设计或调整控件布局时, 请记住以下保留命令集:</span><span class="sxs-lookup"><span data-stu-id="876b8-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="876b8-117">在**左侧和右侧的模拟操纵杆**中, 会保留在 "**流" 仪表板**中。</span><span class="sxs-lookup"><span data-stu-id="876b8-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard**.</span></span>
2. <span data-ttu-id="876b8-118">**Windows 按钮**将始终向 Windows Mixed Reality 主页返回用户。</span><span class="sxs-lookup"><span data-stu-id="876b8-118">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="876b8-119">如果可能, 则默认为基于拇指的 teleportation, 以匹配[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation 行为</span><span class="sxs-lookup"><span data-stu-id="876b8-119">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="876b8-120">工具提示和 UI</span><span class="sxs-lookup"><span data-stu-id="876b8-120">Tooltips and UI</span></span>

<span data-ttu-id="876b8-121">许多 VR 游戏都利用了运动控制器工具提示和覆盖向用户讲授其游戏或应用程序的最重要命令。</span><span class="sxs-lookup"><span data-stu-id="876b8-121">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="876b8-122">优化 Windows Mixed reality 应用程序时, 我们建议查看此部分体验, 确保工具提示映射到 Windows 控制器模型。</span><span class="sxs-lookup"><span data-stu-id="876b8-122">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="876b8-123">此外, 如果你在其中显示了控制器图像的任何点, 请确保使用 Windows Mixed Reality 运动控制器提供更新的图像。</span><span class="sxs-lookup"><span data-stu-id="876b8-123">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="876b8-124">Haptics</span><span class="sxs-lookup"><span data-stu-id="876b8-124">Haptics</span></span>

<span data-ttu-id="876b8-125">从[windows 10 2018 年4月的更新](release-notes-april-2018.md)开始, 现在支持 Haptics 在 Windows Mixed Reality 上的 SteamVR 体验。</span><span class="sxs-lookup"><span data-stu-id="876b8-125">Beginning with the [Windows 10 April 2018 Update](release-notes-april-2018.md), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="876b8-126">如果你的 SteamVR 应用或游戏已包含对 haptics 的支持, 则它现在应可以使用[Windows Mixed Reality 运动控制器](motion-controllers.md)(无需其他工作)。</span><span class="sxs-lookup"><span data-stu-id="876b8-126">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](motion-controllers.md).</span></span>

<span data-ttu-id="876b8-127">Windows Mixed Reality 运动控制器使用标准的 haptics 马达, 而不是在其他 SteamVR 运动控制器中找到的线性传动装置, 这可能会导致用户体验略有不同。</span><span class="sxs-lookup"><span data-stu-id="876b8-127">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="876b8-128">因此, 建议通过 Windows Mixed Reality 运动控制器来测试和优化 haptics 设计。</span><span class="sxs-lookup"><span data-stu-id="876b8-128">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="876b8-129">例如, 在 Windows Mixed Reality 运动控制器上, 有时短 haptic 脉冲 (5-10 ms) 不太明显。</span><span class="sxs-lookup"><span data-stu-id="876b8-129">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="876b8-130">若要生成更明显的脉冲, 请尝试发送更长的 "单击" (40-70ms), 以便让马达更长时间转动, 然后再将其关闭。</span><span class="sxs-lookup"><span data-stu-id="876b8-130">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="876b8-131">从 Windows Mixed Reality 开始菜单启动 SteamVR 应用</span><span class="sxs-lookup"><span data-stu-id="876b8-131">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="876b8-132">对于通过流发布的 VR 体验, 我们已[更新了适用于 SteamVR Beta 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新的[windows 有问必答](https://insider.windows.com)RS5 航班, 以便 SteamVR 标题现在显示在 "所有应用" 中的 Windows Mixed reality 开始菜单中自动列出。</span><span class="sxs-lookup"><span data-stu-id="876b8-132">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="876b8-133">安装这些软件版本后, 客户现在可以直接从 Windows Mixed Reality 家里开始 SteamVR 标题, 无需删除耳机。</span><span class="sxs-lookup"><span data-stu-id="876b8-133">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="876b8-134">Windows Mixed Reality 徽标</span><span class="sxs-lookup"><span data-stu-id="876b8-134">Windows Mixed Reality logo</span></span>

<span data-ttu-id="876b8-135">若要为标题显示 Windows Mixed Reality 支持, 请转到应用登录页上的 "编辑存储页" 链接, 单击 "基本信息" 选项卡, 然后向下滚动到 "虚拟现实"。</span><span class="sxs-lookup"><span data-stu-id="876b8-135">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="876b8-136">取消选中 "隐藏 Windows Mixed Reality", 然后发布到应用商店。</span><span class="sxs-lookup"><span data-stu-id="876b8-136">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="876b8-137">Bug 和反馈</span><span class="sxs-lookup"><span data-stu-id="876b8-137">Bugs and feedback</span></span>

<span data-ttu-id="876b8-138">如果要改善 Windows Mixed Reality SteamVR 体验, 你的反馈非常有用。</span><span class="sxs-lookup"><span data-stu-id="876b8-138">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="876b8-139">请通过[Windows 反馈中心](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)提交所有反馈和 bug。</span><span class="sxs-lookup"><span data-stu-id="876b8-139">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="876b8-140">下面是[有关如何使你的 SteamVR 反馈尽可能有用](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)的一些提示。</span><span class="sxs-lookup"><span data-stu-id="876b8-140">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="876b8-141">如果你有任何疑问或意见要分享, 你也可以通过我们的[流论坛](http://steamcommunity.com/app/719950/discussions/)联系我们。</span><span class="sxs-lookup"><span data-stu-id="876b8-141">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="876b8-142">常见问题和疑难解答</span><span class="sxs-lookup"><span data-stu-id="876b8-142">FAQs and troubleshooting</span></span>

<span data-ttu-id="876b8-143">如果正在运行设置或播放体验的一般问题, 请[查看最新的故障排除步骤](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。</span><span class="sxs-lookup"><span data-stu-id="876b8-143">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="876b8-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="876b8-144">See also</span></span>
* [<span data-ttu-id="876b8-145">安装工具</span><span class="sxs-lookup"><span data-stu-id="876b8-145">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="876b8-146">耳机和运动控制器驱动程序历史记录</span><span class="sxs-lookup"><span data-stu-id="876b8-146">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="876b8-147">Windows Mixed Reality 最小电脑硬件兼容性指南</span><span class="sxs-lookup"><span data-stu-id="876b8-147">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
