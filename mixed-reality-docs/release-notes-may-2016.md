---
title: 发行说明-2016 年 5 月
description: 2016 可能会更新适用于 Windows Holographic HoloLens 发行说明。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，发行说明、 操作系统、 功能、 生成、 平台
ms.openlocfilehash: bc4e09c36a3ab6643be1144873a624fc5ed66e37
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592785"
---
# <a name="release-notes---may-2016"></a><span data-ttu-id="83071-104">发行说明-2016 年 5 月</span><span class="sxs-lookup"><span data-stu-id="83071-104">Release notes - May 2016</span></span>

<span data-ttu-id="83071-105">HoloLens 团队已致力于为您提供的更新，我们的最新功能开发和通过 Windows 预览体验计划的主要修补程序。</span><span class="sxs-lookup"><span data-stu-id="83071-105">The HoloLens team is committed to provide you with an update on our latest feature development and major fixes through the Windows Insider Program.</span></span> <span data-ttu-id="83071-106">感谢您的所有建议，我们需要你的反馈到核心。</span><span class="sxs-lookup"><span data-stu-id="83071-106">Thanks to all your suggestions, we take your feedback to heart.</span></span> <span data-ttu-id="83071-107">请继续执行[向我们提供反馈](give-us-feedback.md)反馈中心，通过[开发人员论坛](https://forums.hololens.com)并[通过 Twitter @HoloLens ](https://twitter.com/hololens)。</span><span class="sxs-lookup"><span data-stu-id="83071-107">Please continue to [give us feedback](give-us-feedback.md) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span>

<span data-ttu-id="83071-108">**发布版本：** Windows 全息版 2016 年 5 月更新 (**10.0.14342.1016**)</span><span class="sxs-lookup"><span data-stu-id="83071-108">**Release version:** Windows Holographic May 2016 Update (**10.0.14342.1016**)</span></span>

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

<span data-ttu-id="83071-109">若要更新到当前版本中，打开*设置*应用程序中，转到*更新和安全*，然后选择*检查更新*按钮。</span><span class="sxs-lookup"><span data-stu-id="83071-109">To update to the current release, open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="83071-110">新增功能</span><span class="sxs-lookup"><span data-stu-id="83071-110">New features</span></span>

* <span data-ttu-id="83071-111">现在可以**同时在二维视图中运行最多三个应用**。</span><span class="sxs-lookup"><span data-stu-id="83071-111">You can now **run up to three apps in 2D view simultaneously**.</span></span> <span data-ttu-id="83071-112">这使多任务处理在 HoloLens 无限的用例。</span><span class="sxs-lookup"><span data-stu-id="83071-112">This enables endless use cases for multi-tasking in HoloLens.</span></span> <span data-ttu-id="83071-113">具有新的反馈中心此航班上浏览新功能时打开的寻找过程的列表。</span><span class="sxs-lookup"><span data-stu-id="83071-113">Have the new Feedback Hub with the list of Quests open while exploring the new features on this flight.</span></span>

  <span data-ttu-id="83071-114">![HoloLens 可以在同一时间运行的三个应用](images/img-3625-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="83071-114">![HoloLens can run three apps at the same time](images/img-3625-400px.jpg)</span></span><br>
  <span data-ttu-id="83071-115">同时在二维视图中运行最多三个应用程序</span><span class="sxs-lookup"><span data-stu-id="83071-115">Run up to three apps in 2D view simultaneously</span></span>

* <span data-ttu-id="83071-116">我们已添加新**语音命令**:</span><span class="sxs-lookup"><span data-stu-id="83071-116">We've added new **voice commands**:</span></span>
   * <span data-ttu-id="83071-117">请尝试查找在一张全息图并将其旋转通过说"我遇到"</span><span class="sxs-lookup"><span data-stu-id="83071-117">Try looking at a hologram and rotate it by saying "face me"</span></span>
   * <span data-ttu-id="83071-118">通过依次选择"放大"或"缩小"更改其大小</span><span class="sxs-lookup"><span data-stu-id="83071-118">Change its size by saying "bigger" or "smaller"</span></span>
   * <span data-ttu-id="83071-119">移动应用，显示"你好，小娜移动*应用名称*此处。"</span><span class="sxs-lookup"><span data-stu-id="83071-119">Move an app by saying "Hey Cortana, move *app name* here."</span></span>
* <span data-ttu-id="83071-120">我们不应当**上更轻松的 HoloLens 开发**。</span><span class="sxs-lookup"><span data-stu-id="83071-120">We've made **developing on HoloLens easier**.</span></span> <span data-ttu-id="83071-121">现在可以浏览、 上载和下载文件通过[Windows Device Portal](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="83071-121">You can now browse, upload, and download files through the [Windows Device Portal](using-the-windows-device-portal.md).</span></span> <span data-ttu-id="83071-122">可以通过 Visual Studio 访问文档文件夹、 Pictures 文件夹和旁加载或部署任何应用的本地存储。</span><span class="sxs-lookup"><span data-stu-id="83071-122">You can access the Documents folder, Pictures folder, and the local storage for any app you side-loaded or deployed through Visual Studio.</span></span>
* <span data-ttu-id="83071-123">**仿真程序现在支持登录名使用 Microsoft 帐户**就像在真实 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="83071-123">The **emulator now supports log-in with a Microsoft Account** just like you would on a real HoloLens.</span></span> <span data-ttu-id="83071-124">可以启用此功能从其他工具菜单">>"。</span><span class="sxs-lookup"><span data-stu-id="83071-124">You can enable this from the Additional Tools menu ">>".</span></span>
* <span data-ttu-id="83071-125">**2D 应用现在隐藏应用栏和游标观看视频的全屏幕时**以避免干扰。</span><span class="sxs-lookup"><span data-stu-id="83071-125">**2D Apps now hide the app bar and cursor when watching video full screen** to avoid distraction.</span></span> <span data-ttu-id="83071-126">这样，您视频的观看体验将 HoloLens 上变得甚至更加有趣。</span><span class="sxs-lookup"><span data-stu-id="83071-126">With this, your video watching experience will be even more enjoyable on HoloLens.</span></span>
* <span data-ttu-id="83071-127">此外可以**固定照片而无需在应用栏**在您的世界。</span><span class="sxs-lookup"><span data-stu-id="83071-127">You can also **pin photos without the app bar** in your world .</span></span>

  <span data-ttu-id="83071-128">![可以对 2D 应用如 photos 隐藏应用栏](images/img-3626-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="83071-128">![The app bar can be hidden for 2D apps like photos](images/img-3626-400px.jpg)</span></span><br>
  <span data-ttu-id="83071-129">可以使用二维视图，如 Photos 为应用隐藏应用栏</span><span class="sxs-lookup"><span data-stu-id="83071-129">The app bar can be hidden for apps with a 2D view, like Photos</span></span>
  
* <span data-ttu-id="83071-130">**文件选取器**工作方式就像在 HoloLens 上预期的一样。</span><span class="sxs-lookup"><span data-stu-id="83071-130">**File picker** works just like you expect it to on HoloLens.</span></span>
* <span data-ttu-id="83071-131">更新**Edge 浏览器**将映射与台式机和手机的统一的用户体验。</span><span class="sxs-lookup"><span data-stu-id="83071-131">Updated **Edge browser** to map unified user experience with desktop and phone.</span></span> <span data-ttu-id="83071-132">我们启用了浏览器、 自定义 HoloLens 新选项卡页、 选项卡查看和打开新的 windows，除了电力和性能改进中的多个实例。</span><span class="sxs-lookup"><span data-stu-id="83071-132">We enabled multiple instances of your browser, custom HoloLens new tab page, tab peek, and open in new windows, along with power & performance improvements.</span></span>
* <span data-ttu-id="83071-133">**Groove 音乐**应用现已在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="83071-133">**Groove Music** app is now on HoloLens.</span></span> <span data-ttu-id="83071-134">访问应用商店进行下载，请尝试在后台播放。</span><span class="sxs-lookup"><span data-stu-id="83071-134">Visit the store to download it and try playing in the background.</span></span>
* <span data-ttu-id="83071-135">您可以轻松地自定义应用程序在您的世界中的排列方式。</span><span class="sxs-lookup"><span data-stu-id="83071-135">You can easily customize how apps are arranged in your world.</span></span> <span data-ttu-id="83071-136">请尝试**旋转你全息**中调整模式，只需单击和拖动的中间垂直线框中的圆圈。</span><span class="sxs-lookup"><span data-stu-id="83071-136">Try **rotating your holograms** in adjust mode by simply click and drag on circle in the middle vertical wireframes.</span></span> <span data-ttu-id="83071-137">您可能注意到有全息**加强条拟合的边界框**以确保能够以最大化模式的交互。</span><span class="sxs-lookup"><span data-stu-id="83071-137">You might notice holograms have **tighter fitted bounding boxes** to ensure maximized interaction.</span></span> <span data-ttu-id="83071-138">您还可以垂直调整平面的所有应用 (除照片和全息图应用)。</span><span class="sxs-lookup"><span data-stu-id="83071-138">You can also resize all flat apps vertically (except Photos and Hologram apps).</span></span>

  <span data-ttu-id="83071-139">![将它们放在世界上后，可以旋转全息](images/img-3627-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="83071-139">![Holograms can be rotated after you place them in the world](images/img-3627-400px.jpg)</span></span><br>
  <span data-ttu-id="83071-140">旋转全息后将其放在您的世界</span><span class="sxs-lookup"><span data-stu-id="83071-140">Rotate holograms after you place them in your world</span></span>

* <span data-ttu-id="83071-141">我们已进行了大量**输入改善**中此航班。</span><span class="sxs-lookup"><span data-stu-id="83071-141">We've made a lot of **input improvement** in this flight.</span></span> <span data-ttu-id="83071-142">你可以连接到 HoloLens 的正则蓝牙鼠标。</span><span class="sxs-lookup"><span data-stu-id="83071-142">You can connect a regular Bluetooth mouse to HoloLens.</span></span> <span data-ttu-id="83071-143">已正常 clicker 经过优化，可启用重设大小和移动与 clicker 全息。</span><span class="sxs-lookup"><span data-stu-id="83071-143">The clicker has been fine tuned to enable resizing & moving holograms with a clicker.</span></span> <span data-ttu-id="83071-144">键盘也可以运行比以前更好。</span><span class="sxs-lookup"><span data-stu-id="83071-144">Keyboard is also running better than ever.</span></span>
* <span data-ttu-id="83071-145">现在，您可以采取**混合现实图片**，只需按向下调高音量 + 调低音量同时。</span><span class="sxs-lookup"><span data-stu-id="83071-145">Now you can take **mixed reality pictures** by simply pressing down the volume up + volume down simultaneously.</span></span> <span data-ttu-id="83071-146">此外可以共享你的混合的现实捕获照片和视频到 Facebook、 Twitter 和 YouTube。</span><span class="sxs-lookup"><span data-stu-id="83071-146">You can also share your mixed reality captured photos & videos to Facebook, Twitter and YouTube.</span></span>
* <span data-ttu-id="83071-147">最大记录长度**混合现实视频**已增加到 5 分钟内。</span><span class="sxs-lookup"><span data-stu-id="83071-147">The maximum recording length of **mixed reality videos** has been increased to five minutes.</span></span>
* <span data-ttu-id="83071-148">**照片应用**现在而无需下载整个之前播放视频流从 OneDrive 的视频。</span><span class="sxs-lookup"><span data-stu-id="83071-148">**Photos app** now streams videos from OneDrive instead of having to download the entire video before playback.</span></span>
* <span data-ttu-id="83071-149">我们改进了如何在**全息正适合在您离开的位置**。</span><span class="sxs-lookup"><span data-stu-id="83071-149">We've improved how your **holograms will be right where you left them**.</span></span> <span data-ttu-id="83071-150">您还将显示选项以重新连接到的 Wi-fi，然后重试，如果 HoloLens 无法检测到它们的位置。</span><span class="sxs-lookup"><span data-stu-id="83071-150">You will also be presented the option to re-connect to Wi-Fi and try again if HoloLens cannot detect where they are.</span></span>
* <span data-ttu-id="83071-151">具有键盘**输入电子邮件地址的改进了的布局**密钥，可用于输入的最受欢迎的电子邮件域与一个单击。</span><span class="sxs-lookup"><span data-stu-id="83071-151">The keyboard has an **improved layout for entering email address** with keys that allow you to enter the most popular email domains with a single click.</span></span>
* <span data-ttu-id="83071-152">更快地**应用程序注册**并**自动检测到的时区**期间 OOBE，为您提供最佳的第一个用户体验。</span><span class="sxs-lookup"><span data-stu-id="83071-152">Faster **app registration** and **auto detection of time zone** during OOBE, giving you the best first user experience.</span></span>
* <span data-ttu-id="83071-153">**存储感知**可以设置应用中查看由系统和应用程序的剩余和已用磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="83071-153">**Storage sense** allows you to view remaining and used disk space by the system and apps in the settings app.</span></span>
* <span data-ttu-id="83071-154">我们已经转换为单个应用聚合反馈应用和内部集线器**反馈中心**将用于的转到工具**从而为我们提供反馈**，哪些功能你所喜爱的而不，或当无法执行哪些功能某些内容可能是更好。</span><span class="sxs-lookup"><span data-stu-id="83071-154">We have converged Feedback App and Inside Hub into a single app **Feedback Hub** that will be the go-to tool for **giving us feedback**, which features you love, which features you could do without, or when something could be better.</span></span> <span data-ttu-id="83071-155">加入预览体验计划时，您可以随时**获取最新 Insider 新闻**，**评级生成**，然后选择**反馈的寻找过程**从反馈中心。</span><span class="sxs-lookup"><span data-stu-id="83071-155">When you join the Insider Program, you can keep up on **get latest Insider news**, **rate builds** and go on **feedback quests** from Feedback Hub.</span></span>
* <span data-ttu-id="83071-156">我们还[发布更新后的 HoloLens 模拟器](install-the-tools.md)生成。</span><span class="sxs-lookup"><span data-stu-id="83071-156">We've also [published an updated HoloLens Emulator](install-the-tools.md) build.</span></span>
* <span data-ttu-id="83071-157">混合的现实视频现在看起来更好地自动由于**视频防抖动**。</span><span class="sxs-lookup"><span data-stu-id="83071-157">Your mixed reality videos now look better due to automatic **video stabilization**.</span></span>

## <a name="major-fixes"></a><span data-ttu-id="83071-158">主要的修补程序</span><span class="sxs-lookup"><span data-stu-id="83071-158">Major fixes</span></span>

<span data-ttu-id="83071-159">我们使用全息图空间时会空间可能会较慢或未正确检测到解决问题。</span><span class="sxs-lookup"><span data-stu-id="83071-159">We fixed issues with hologram spaces where the spaces would be slow or incorrectly detected.</span></span> <span data-ttu-id="83071-160">我们修复了关闭问题，可以继续尝试在关闭过程中启动 shell。</span><span class="sxs-lookup"><span data-stu-id="83071-160">We fixed a shutdown issue that could continue to try launching the shell during shutdown.</span></span>

<span data-ttu-id="83071-161">修复了以下问题</span><span class="sxs-lookup"><span data-stu-id="83071-161">We fixed an issue</span></span>
* <span data-ttu-id="83071-162">阻止恢复 XAML 应用程序的功能。</span><span class="sxs-lookup"><span data-stu-id="83071-162">that blocks the ability to resume a XAML application.</span></span>
* <span data-ttu-id="83071-163">其中崩溃后导致黑屏和一些参差不齐的行。</span><span class="sxs-lookup"><span data-stu-id="83071-163">where a crash would leave a black screen and some jagged lines.</span></span>
* <span data-ttu-id="83071-164">滚动将有时只讨论了错误的方向时使用某些应用程序。</span><span class="sxs-lookup"><span data-stu-id="83071-164">scrolling would sometimes stick in the wrong direction when using some apps.</span></span>
* <span data-ttu-id="83071-165">电源设备仍在使用时，Led 可能表示关闭状态。</span><span class="sxs-lookup"><span data-stu-id="83071-165">the power LEDs could indicate an off state when the device was still on.</span></span>
* <span data-ttu-id="83071-166">从待机状态恢复后，无法获取关闭 WiFi。</span><span class="sxs-lookup"><span data-stu-id="83071-166">WiFi could get turned off after resuming from standby.</span></span>
* <span data-ttu-id="83071-167">Xbox 标识提供者提供玩家代号安装程序，然后获取陷在循环。</span><span class="sxs-lookup"><span data-stu-id="83071-167">the Xbox identity provider offers gamertag setup and then gets stuck in a loop.</span></span>
* <span data-ttu-id="83071-168">OneDrive 文件选取器中选择已下载的文件时，偶尔会发生崩溃 Shell。</span><span class="sxs-lookup"><span data-stu-id="83071-168">the Shell occasionally crashes when selecting a downloaded file in the OneDrive File Picker.</span></span>
* <span data-ttu-id="83071-169">按下并保持在链接上有时同时会打开新的、 断开选项卡并打开上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="83071-169">pressing and holding on a link sometimes both opens a new, broken tab and opens a context menu.</span></span>
* <span data-ttu-id="83071-170">其中 windows 设备门户不允许从 50 到 80 的 IPD 调整</span><span class="sxs-lookup"><span data-stu-id="83071-170">where windows device portal didn’t allow IPD adjustments from 50 to 80</span></span>

<span data-ttu-id="83071-171">我们修复问题的照片，</span><span class="sxs-lookup"><span data-stu-id="83071-171">We fixed issues with Photos where</span></span>
* <span data-ttu-id="83071-172">有时会显示图像旋转由于忽略 EXIF orientation 属性。</span><span class="sxs-lookup"><span data-stu-id="83071-172">an image would occasionally display rotated due to ignoring the EXIF orientation property.</span></span>
* <span data-ttu-id="83071-173">在启动时对固定的照片，它可能导致崩溃。</span><span class="sxs-lookup"><span data-stu-id="83071-173">it could crash during start-up on pinned Photos.</span></span>
* <span data-ttu-id="83071-174">视频将而不在上次暂停继续从暂停后重新启动。</span><span class="sxs-lookup"><span data-stu-id="83071-174">videos would restart after pausing instead of continuing from where last paused.</span></span>
* <span data-ttu-id="83071-175">如果共享播放时无法阻止共享视频的重播。</span><span class="sxs-lookup"><span data-stu-id="83071-175">replay of a shared video could be prevented if it was shared while playing.</span></span>
* <span data-ttu-id="83071-176">混合的现实捕获录制将以 0.5 1 开头的音频仅源第二个。</span><span class="sxs-lookup"><span data-stu-id="83071-176">Mixed Reality Capture recordings would begin with 0.5-1 second of audio only feed.</span></span>
* <span data-ttu-id="83071-177">在初始 OneDrive 同步期间，同步按钮将消失。</span><span class="sxs-lookup"><span data-stu-id="83071-177">the Sync button disappears during initial OneDrive sync.</span></span>

<span data-ttu-id="83071-178">我们修复设置问题，</span><span class="sxs-lookup"><span data-stu-id="83071-178">We fixed issues with settings where</span></span>
* <span data-ttu-id="83071-179">在环境更改时需要刷新。</span><span class="sxs-lookup"><span data-stu-id="83071-179">a refresh was needed when the environment changes.</span></span>
* <span data-ttu-id="83071-180">输入键盘将不行为类似于在一些对话框中单击下一步。</span><span class="sxs-lookup"><span data-stu-id="83071-180">'Enter' on keyboard would not behave like clicking Next in some dialogs.</span></span>
* <span data-ttu-id="83071-181">会很难知道 clicker 失败配对。</span><span class="sxs-lookup"><span data-stu-id="83071-181">it was hard to know when the clicker failed pairing.</span></span>
* <span data-ttu-id="83071-182">它可能变得不响应与 WiFi 断开连接，并连接。</span><span class="sxs-lookup"><span data-stu-id="83071-182">it could become unresponsive with WiFi disconnect and connect.</span></span>

<span data-ttu-id="83071-183">我们使用 Cortana 修复问题，</span><span class="sxs-lookup"><span data-stu-id="83071-183">We fixed issues with Cortana where</span></span>
* <span data-ttu-id="83071-184">它将停留显示侦听 UI。</span><span class="sxs-lookup"><span data-stu-id="83071-184">it could get stuck displaying the Listening UI.</span></span>
* <span data-ttu-id="83071-185">询问"您好 Cortana，我可以说什么"独占模式下从应用程序将陷入僵局，如果您的回答可能相当是/否请求退出该应用。</span><span class="sxs-lookup"><span data-stu-id="83071-185">asking "Hey Cortana, what can I say" from an exclusive mode app would get stuck if you answered maybe rather yes/no to the request to exit the app.</span></span>
* <span data-ttu-id="83071-186">如果你问 Cortana 进入睡眠状态，然后继续侦听 UI 不会正确恢复 Cortana。</span><span class="sxs-lookup"><span data-stu-id="83071-186">the Cortana listening UI doesn't resume correctly if you ask Cortana to go to sleep and then resume.</span></span>
* <span data-ttu-id="83071-187">查询"哪些网络我连接到？"</span><span class="sxs-lookup"><span data-stu-id="83071-187">the queries "What network am I connected to?"</span></span> <span data-ttu-id="83071-188">和"Am 我连接？"</span><span class="sxs-lookup"><span data-stu-id="83071-188">and the "Am I connected?"</span></span> <span data-ttu-id="83071-189">当第一个网络配置文件返回未连接到可能会失败。</span><span class="sxs-lookup"><span data-stu-id="83071-189">could fail when the first network profile comes back with no connectivity.</span></span>
* <span data-ttu-id="83071-190">UI 冻结上"侦听"，但在退出应用程序时将立即开始再次执行语音识别。</span><span class="sxs-lookup"><span data-stu-id="83071-190">the UI froze on "Listening" but upon exiting an app would immediately began doing speech recognition again.</span></span>
* <span data-ttu-id="83071-191">其中从 Cortana 应用注销不会让你注册回它直到重新启动。</span><span class="sxs-lookup"><span data-stu-id="83071-191">where signing out of the Cortana app wouldn't let you sign back into it until a reboot.</span></span>
* <span data-ttu-id="83071-192">混合现实捕获 UI 处于活动状态时，它不会启动。</span><span class="sxs-lookup"><span data-stu-id="83071-192">it would not launch when Mixed Reality Capture UI was active.</span></span>

<span data-ttu-id="83071-193">我们使用 Visual Studio 修复问题，</span><span class="sxs-lookup"><span data-stu-id="83071-193">We fixed issues with Visual Studio where</span></span>
* <span data-ttu-id="83071-194">后台任务调试未解决问题。</span><span class="sxs-lookup"><span data-stu-id="83071-194">background task debugging did not work.</span></span>
* <span data-ttu-id="83071-195">图形调试器中的帧分析未解决问题。</span><span class="sxs-lookup"><span data-stu-id="83071-195">frame analysis in the graphics debugger did not work.</span></span>
* <span data-ttu-id="83071-196">HoloLens 仿真程序未显示在下拉列表中为 Visual Studio 除非您的项目的 TargetPlatformVersion 已设置为 10240。</span><span class="sxs-lookup"><span data-stu-id="83071-196">the HoloLens Emulator did not appear in the drop-down list for Visual Studio unless your project's TargetPlatformVersion was set to 10240.</span></span>

## <a name="changes-from-previous-release"></a><span data-ttu-id="83071-197">从以前的版本中的更改</span><span class="sxs-lookup"><span data-stu-id="83071-197">Changes from previous release</span></span>
* <span data-ttu-id="83071-198">Cortana 命令**你好，小娜重新启动设备**不起作用。</span><span class="sxs-lookup"><span data-stu-id="83071-198">The Cortana command **Hey Cortana, reboot the device** does not work.</span></span> <span data-ttu-id="83071-199">用户可以说**你好，小娜重启**或**你好，小娜重启设备**。</span><span class="sxs-lookup"><span data-stu-id="83071-199">User can say **Hey Cortana, restart** or **Hey Cortana, restart the device**.</span></span>
* <span data-ttu-id="83071-200">展台模式已从产品中删除。</span><span class="sxs-lookup"><span data-stu-id="83071-200">Kiosk mode has been removed from the product.</span></span>

## <a name="prior-release-notes"></a><span data-ttu-id="83071-201">以前的发行说明</span><span class="sxs-lookup"><span data-stu-id="83071-201">Prior release notes</span></span>
* [<span data-ttu-id="83071-202">发行说明-2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="83071-202">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="83071-203">请参阅</span><span class="sxs-lookup"><span data-stu-id="83071-203">See also</span></span>
* [<span data-ttu-id="83071-204">HoloLens 的已知问题</span><span class="sxs-lookup"><span data-stu-id="83071-204">HoloLens known issues</span></span>](hololens-known-issues.md)
* [<span data-ttu-id="83071-205">安装工具</span><span class="sxs-lookup"><span data-stu-id="83071-205">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="83071-206">Shell</span><span class="sxs-lookup"><span data-stu-id="83071-206">Shell</span></span>](navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="83071-207">更新适用于混合现实的 2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="83071-207">Updating 2D UWP apps for mixed reality</span></span>](building-2d-apps.md)
* [<span data-ttu-id="83071-208">硬件附件</span><span class="sxs-lookup"><span data-stu-id="83071-208">Hardware accessories</span></span>](hardware-accessories.md)
* [<span data-ttu-id="83071-209">混合的现实捕获</span><span class="sxs-lookup"><span data-stu-id="83071-209">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="83071-210">语音输入</span><span class="sxs-lookup"><span data-stu-id="83071-210">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="83071-211">提交到 Windows 应用商店应用</span><span class="sxs-lookup"><span data-stu-id="83071-211">Submitting an app to the Windows Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="83071-212">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="83071-212">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
