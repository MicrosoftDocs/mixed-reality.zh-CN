---
title: 更新 Windows Mixed Reality 应用 SteamVR 程序
description: 有关更新 SteamVR 应用程序，以最大程度地使用 Windows Mixed Reality 耳机的兼容性最佳实践。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR，兼容性
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590165"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a><span data-ttu-id="94b73-104">更新 Windows Mixed Reality 应用 SteamVR 程序</span><span class="sxs-lookup"><span data-stu-id="94b73-104">Updating your SteamVR application for Windows Mixed Reality</span></span>

<span data-ttu-id="94b73-105">我们建议开发人员测试并优化其 SteamVR 的体验，以在 Windows Mixed Reality 耳机上运行。</span><span class="sxs-lookup"><span data-stu-id="94b73-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="94b73-106">本文档介绍了常见开发人员可以进行以确保 Windows Mixed Reality 上出色运行他们的体验的改进。</span><span class="sxs-lookup"><span data-stu-id="94b73-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="94b73-107">初始安装说明</span><span class="sxs-lookup"><span data-stu-id="94b73-107">Initial setup instructions</span></span>

<span data-ttu-id="94b73-108">若要开始测试出游戏或应用上 Windows Mixed Reality 请确保到第一个按照我们[入门指南。](http://aka.ms/WindowsMixedRealitySteamVR)</span><span class="sxs-lookup"><span data-stu-id="94b73-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](http://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="94b73-109">控制器模型</span><span class="sxs-lookup"><span data-stu-id="94b73-109">Controller Models</span></span>
1. <span data-ttu-id="94b73-110">如果您的应用程序呈现控制器模型：</span><span class="sxs-lookup"><span data-stu-id="94b73-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="94b73-111">使用[Windows Mixed Reality 运动控制器模型](motion-controllers.md#rendering-the-motion-controller-model)</span><span class="sxs-lookup"><span data-stu-id="94b73-111">Use the [Windows Mixed Reality motion controller models](motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="94b73-112">若要获取本地的使用 IVRRenderModel::GetComponentState 将转换成组件部分 （例如。</span><span class="sxs-lookup"><span data-stu-id="94b73-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="94b73-113">指针姿势）</span><span class="sxs-lookup"><span data-stu-id="94b73-113">Pointer pose)</span></span>
2. <span data-ttu-id="94b73-114">具有表示法的左右手使用习惯的体验应从输入 Api 来区分控制器获取提示[（Unity 示例）](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="94b73-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="94b73-115">Controls</span><span class="sxs-lookup"><span data-stu-id="94b73-115">Controls</span></span>

<span data-ttu-id="94b73-116">当设计或调整控件布局记住以下保留命令集：</span><span class="sxs-lookup"><span data-stu-id="94b73-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="94b73-117">单击向下**左侧和右侧模拟摇杆**留待**Steam 仪表板**。</span><span class="sxs-lookup"><span data-stu-id="94b73-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard**.</span></span>
2. <span data-ttu-id="94b73-118">**Windows 按钮**将始终返回到 Windows Mixed Reality 家庭用户。</span><span class="sxs-lookup"><span data-stu-id="94b73-118">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="94b73-119">如果可能，默认缩略记忆棒基于 teleportation 以匹配[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)teleportation 行为</span><span class="sxs-lookup"><span data-stu-id="94b73-119">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="94b73-120">工具提示和 UI</span><span class="sxs-lookup"><span data-stu-id="94b73-120">Tooltips and UI</span></span>

<span data-ttu-id="94b73-121">许多 VR 游戏利用运动控制器工具提示和覆盖层，教用户为他们的游戏或应用程序最重要的命令。</span><span class="sxs-lookup"><span data-stu-id="94b73-121">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="94b73-122">优化 Windows 混合现实应用程序时我们建议查看您的体验，以确保将映射到 Windows 控制器模型的工具提示的这一部分。</span><span class="sxs-lookup"><span data-stu-id="94b73-122">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="94b73-123">另外如果有您的体验，其中显示图像的控制器中的任何点请确保提供更新后的映像使用 Windows Mixed Reality 运动控制器。</span><span class="sxs-lookup"><span data-stu-id="94b73-123">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="94b73-124">Haptics</span><span class="sxs-lookup"><span data-stu-id="94b73-124">Haptics</span></span>

<span data-ttu-id="94b73-125">开头[Windows 10 2018 年 4 月更新](release-notes-april-2018.md)，现在支持 haptics SteamVR 体验 Windows Mixed reality。</span><span class="sxs-lookup"><span data-stu-id="94b73-125">Beginning with the [Windows 10 April 2018 Update](release-notes-april-2018.md), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="94b73-126">如果在 SteamVR 应用或游戏已包含对 haptics 的支持，它应现在使用 （与任何额外工作） [Windows Mixed Reality 运动控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="94b73-126">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](motion-controllers.md).</span></span>

<span data-ttu-id="94b73-127">Windows Mixed Reality 运动控制器使用标准 haptics 马达，而不是在某些其他 SteamVR 运动控制器，这可能会导致略有不同超出预期的用户体验中找到线性传动装置。</span><span class="sxs-lookup"><span data-stu-id="94b73-127">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="94b73-128">因此，我们建议测试和优化 Windows Mixed Reality 运动控制器 haptics 的设计。</span><span class="sxs-lookup"><span data-stu-id="94b73-128">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="94b73-129">例如，有时短 haptic 脉冲 （5-10 毫秒） 是 Windows Mixed Reality 运动控制器上不太明显。</span><span class="sxs-lookup"><span data-stu-id="94b73-129">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="94b73-130">若要生成更明显 pulse，尝试发送较长"单击"(40-70) 能够在汽车的更多时间来启动告知电源再次之前。</span><span class="sxs-lookup"><span data-stu-id="94b73-130">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="94b73-131">从 Windows 混合现实开始菜单启动 SteamVR 应用</span><span class="sxs-lookup"><span data-stu-id="94b73-131">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="94b73-132">通过流分发 VR 体验，我们已经[SteamVR beta 更新 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新[Windows Insider](https://insider.windows.com) RS5 航班以便 SteamVR 标题现在显示在自动列出 Windows 混合现实开始菜单中"所有应用"。</span><span class="sxs-lookup"><span data-stu-id="94b73-132">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="94b73-133">与安装下列软件版本，你的客户现在可以不删除其耳机启动 Windows Mixed Reality 家庭内的直接从 SteamVR 标题。</span><span class="sxs-lookup"><span data-stu-id="94b73-133">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="94b73-134">Windows Mixed Reality 徽标</span><span class="sxs-lookup"><span data-stu-id="94b73-134">Windows Mixed Reality logo</span></span>

<span data-ttu-id="94b73-135">若要显示在标题上的 Windows Mixed Reality 支持，请转到"编辑应用商店页"链接应用登陆页面上，单击"基本信息"选项卡上，并向下滚动到"虚拟现实。"</span><span class="sxs-lookup"><span data-stu-id="94b73-135">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="94b73-136">取消选中"隐藏 Windows Mixed Reality"，然后将其发布到应用商店。</span><span class="sxs-lookup"><span data-stu-id="94b73-136">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="94b73-137">错误和反馈</span><span class="sxs-lookup"><span data-stu-id="94b73-137">Bugs and feedback</span></span>

<span data-ttu-id="94b73-138">改进 Windows 混合现实 SteamVR 体验时，你的反馈是非常有用。</span><span class="sxs-lookup"><span data-stu-id="94b73-138">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="94b73-139">请提交的所有反馈和通过的 bug [Windows 反馈中心](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)。</span><span class="sxs-lookup"><span data-stu-id="94b73-139">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="94b73-140">下面是一些[有关如何使 SteamVR 反馈尽可能为有用的提示](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)。</span><span class="sxs-lookup"><span data-stu-id="94b73-140">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="94b73-141">如果你有疑问或要共享的注释，也可以访问我们在我们[Steam 论坛](http://steamcommunity.com/app/719950/discussions/)。</span><span class="sxs-lookup"><span data-stu-id="94b73-141">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="94b73-142">常见问题和疑难解答</span><span class="sxs-lookup"><span data-stu-id="94b73-142">FAQs and troubleshooting</span></span>

<span data-ttu-id="94b73-143">如果运行的常规问题设置还是播放你的体验，[查看最新故障排除步骤](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。</span><span class="sxs-lookup"><span data-stu-id="94b73-143">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="94b73-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="94b73-144">See also</span></span>
* [<span data-ttu-id="94b73-145">安装工具</span><span class="sxs-lookup"><span data-stu-id="94b73-145">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="94b73-146">耳机和动作控制器驱动程序历史记录</span><span class="sxs-lookup"><span data-stu-id="94b73-146">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="94b73-147">Windows Mixed Reality 最小 PC 硬件兼容性指南</span><span class="sxs-lookup"><span data-stu-id="94b73-147">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
