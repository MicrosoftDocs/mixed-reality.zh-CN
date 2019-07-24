---
title: 发行说明-5 月2016
description: Windows 全息版的 HoloLens 发行说明可能为2016更新。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 发行说明, 操作系统, 功能, 生成, 平台
ms.openlocfilehash: bc4e09c36a3ab6643be1144873a624fc5ed66e37
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524577"
---
# <a name="release-notes---may-2016"></a><span data-ttu-id="5cd27-104">发行说明-5 月2016</span><span class="sxs-lookup"><span data-stu-id="5cd27-104">Release notes - May 2016</span></span>

<span data-ttu-id="5cd27-105">HoloLens 团队致力于通过 Windows 预览体验计划为您提供最新的功能开发和主要修补程序的更新。</span><span class="sxs-lookup"><span data-stu-id="5cd27-105">The HoloLens team is committed to provide you with an update on our latest feature development and major fixes through the Windows Insider Program.</span></span> <span data-ttu-id="5cd27-106">感谢你的所有建议, 我们会将你的反馈反馈给你。</span><span class="sxs-lookup"><span data-stu-id="5cd27-106">Thanks to all your suggestions, we take your feedback to heart.</span></span> <span data-ttu-id="5cd27-107">[请通过@HoloLens](https://twitter.com/hololens)反馈中心、[开发人员论坛](https://forums.hololens.com)和 Twitter 继续向[我们提供反馈](give-us-feedback.md)。</span><span class="sxs-lookup"><span data-stu-id="5cd27-107">Please continue to [give us feedback](give-us-feedback.md) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span>

<span data-ttu-id="5cd27-108">**发布版本:** Windows 全息版可能为2016更新 (**10.0.14342.1016**)</span><span class="sxs-lookup"><span data-stu-id="5cd27-108">**Release version:** Windows Holographic May 2016 Update (**10.0.14342.1016**)</span></span>

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

<span data-ttu-id="5cd27-109">若要更新到当前版本, 请打开 "*设置*" 应用, 中转到 "*更新 & 安全性*", 然后选择 "*检查更新*" 按钮。</span><span class="sxs-lookup"><span data-stu-id="5cd27-109">To update to the current release, open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="5cd27-110">新增功能</span><span class="sxs-lookup"><span data-stu-id="5cd27-110">New features</span></span>

* <span data-ttu-id="5cd27-111">你现在可以**同时在2d 视图中运行最多三个应用**。</span><span class="sxs-lookup"><span data-stu-id="5cd27-111">You can now **run up to three apps in 2D view simultaneously**.</span></span> <span data-ttu-id="5cd27-112">这为 HoloLens 中的多任务启用了无限用例。</span><span class="sxs-lookup"><span data-stu-id="5cd27-112">This enables endless use cases for multi-tasking in HoloLens.</span></span> <span data-ttu-id="5cd27-113">浏览此航班上的新功能时, 将新的反馈中心与知识探寻点列表打开。</span><span class="sxs-lookup"><span data-stu-id="5cd27-113">Have the new Feedback Hub with the list of Quests open while exploring the new features on this flight.</span></span>

  <span data-ttu-id="5cd27-114">![HoloLens 可以同时运行三个应用](images/img-3625-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5cd27-114">![HoloLens can run three apps at the same time](images/img-3625-400px.jpg)</span></span><br>
  <span data-ttu-id="5cd27-115">同时在2D 视图中运行最多三个应用</span><span class="sxs-lookup"><span data-stu-id="5cd27-115">Run up to three apps in 2D view simultaneously</span></span>

* <span data-ttu-id="5cd27-116">我们添加了新的**语音命令**:</span><span class="sxs-lookup"><span data-stu-id="5cd27-116">We've added new **voice commands**:</span></span>
   * <span data-ttu-id="5cd27-117">尝试查看全息图并通过 "面部我" 来旋转</span><span class="sxs-lookup"><span data-stu-id="5cd27-117">Try looking at a hologram and rotate it by saying "face me"</span></span>
   * <span data-ttu-id="5cd27-118">使用 "更大" 或 "小" 来更改其大小</span><span class="sxs-lookup"><span data-stu-id="5cd27-118">Change its size by saying "bigger" or "smaller"</span></span>
   * <span data-ttu-id="5cd27-119">通过说 "你好 Cortana, 将*应用名称*移动到此处" 移动应用。</span><span class="sxs-lookup"><span data-stu-id="5cd27-119">Move an app by saying "Hey Cortana, move *app name* here."</span></span>
* <span data-ttu-id="5cd27-120">我们**更轻松地进行开发**。</span><span class="sxs-lookup"><span data-stu-id="5cd27-120">We've made **developing on HoloLens easier**.</span></span> <span data-ttu-id="5cd27-121">你现在可以通过[Windows 设备门户](using-the-windows-device-portal.md)浏览、上传和下载文件。</span><span class="sxs-lookup"><span data-stu-id="5cd27-121">You can now browse, upload, and download files through the [Windows Device Portal](using-the-windows-device-portal.md).</span></span> <span data-ttu-id="5cd27-122">您可以访问 "文档" 文件夹、"图片" 文件夹, 以及通过 Visual Studio 加载或部署的任何应用的本地存储。</span><span class="sxs-lookup"><span data-stu-id="5cd27-122">You can access the Documents folder, Pictures folder, and the local storage for any app you side-loaded or deployed through Visual Studio.</span></span>
* <span data-ttu-id="5cd27-123">**仿真器现在支持使用 Microsoft 帐户进行登录**, 就像在实际的 HoloLens 中一样。</span><span class="sxs-lookup"><span data-stu-id="5cd27-123">The **emulator now supports log-in with a Microsoft Account** just like you would on a real HoloLens.</span></span> <span data-ttu-id="5cd27-124">你可以从 "其他工具" 菜单的 "> >" 启用此工具。</span><span class="sxs-lookup"><span data-stu-id="5cd27-124">You can enable this from the Additional Tools menu ">>".</span></span>
* <span data-ttu-id="5cd27-125">**二维应用现在会在观看视频全屏时隐藏应用栏和光标**以避免干扰。</span><span class="sxs-lookup"><span data-stu-id="5cd27-125">**2D Apps now hide the app bar and cursor when watching video full screen** to avoid distraction.</span></span> <span data-ttu-id="5cd27-126">这样一来, 您的视频观看体验就更有可能在 HoloLens 上更愉快。</span><span class="sxs-lookup"><span data-stu-id="5cd27-126">With this, your video watching experience will be even more enjoyable on HoloLens.</span></span>
* <span data-ttu-id="5cd27-127">你还可以在**没有应用栏的情况下固定照片**。</span><span class="sxs-lookup"><span data-stu-id="5cd27-127">You can also **pin photos without the app bar** in your world .</span></span>

  <span data-ttu-id="5cd27-128">![对于诸如照片的2D 应用, 可以隐藏应用栏](images/img-3626-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5cd27-128">![The app bar can be hidden for 2D apps like photos](images/img-3626-400px.jpg)</span></span><br>
  <span data-ttu-id="5cd27-129">对于具有2D 视图的应用 (如照片), 可以隐藏应用栏</span><span class="sxs-lookup"><span data-stu-id="5cd27-129">The app bar can be hidden for apps with a 2D view, like Photos</span></span>
  
* <span data-ttu-id="5cd27-130">**文件选取器**的工作方式与在 HoloLens 上的预期一样。</span><span class="sxs-lookup"><span data-stu-id="5cd27-130">**File picker** works just like you expect it to on HoloLens.</span></span>
* <span data-ttu-id="5cd27-131">更新了**Edge 浏览器**, 以通过桌面和电话映射统一的用户体验。</span><span class="sxs-lookup"><span data-stu-id="5cd27-131">Updated **Edge browser** to map unified user experience with desktop and phone.</span></span> <span data-ttu-id="5cd27-132">我们启用了多个浏览器实例、自定义的 HoloLens 新选项卡页、选项卡速览, 并在新窗口中打开, 同时增强了电源 & 性能。</span><span class="sxs-lookup"><span data-stu-id="5cd27-132">We enabled multiple instances of your browser, custom HoloLens new tab page, tab peek, and open in new windows, along with power & performance improvements.</span></span>
* <span data-ttu-id="5cd27-133">**Groove 音乐**应用现已在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="5cd27-133">**Groove Music** app is now on HoloLens.</span></span> <span data-ttu-id="5cd27-134">访问应用商店进行下载, 并尝试在后台播放。</span><span class="sxs-lookup"><span data-stu-id="5cd27-134">Visit the store to download it and try playing in the background.</span></span>
* <span data-ttu-id="5cd27-135">您可以轻松地自定义应用在您的世界中的排列方式。</span><span class="sxs-lookup"><span data-stu-id="5cd27-135">You can easily customize how apps are arranged in your world.</span></span> <span data-ttu-id="5cd27-136">通过只需单击并拖动中间垂直线框中的圆圈, 尝试在调整模式下**旋转全息影像**。</span><span class="sxs-lookup"><span data-stu-id="5cd27-136">Try **rotating your holograms** in adjust mode by simply click and drag on circle in the middle vertical wireframes.</span></span> <span data-ttu-id="5cd27-137">你可能会注意到, 全息影像具有更**严格的拟合边界框**, 以确保最大化交互。</span><span class="sxs-lookup"><span data-stu-id="5cd27-137">You might notice holograms have **tighter fitted bounding boxes** to ensure maximized interaction.</span></span> <span data-ttu-id="5cd27-138">还可以垂直调整所有平面应用的大小 (照片和全息图应用除外)。</span><span class="sxs-lookup"><span data-stu-id="5cd27-138">You can also resize all flat apps vertically (except Photos and Hologram apps).</span></span>

  <span data-ttu-id="5cd27-139">![将全息影像置于世界](images/img-3627-400px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5cd27-139">![Holograms can be rotated after you place them in the world](images/img-3627-400px.jpg)</span></span><br>
  <span data-ttu-id="5cd27-140">将全息影像置于世界中后旋转</span><span class="sxs-lookup"><span data-stu-id="5cd27-140">Rotate holograms after you place them in your world</span></span>

* <span data-ttu-id="5cd27-141">我们在此航班中做了大量的**输入改进**。</span><span class="sxs-lookup"><span data-stu-id="5cd27-141">We've made a lot of **input improvement** in this flight.</span></span> <span data-ttu-id="5cd27-142">可以将常规蓝牙鼠标连接到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5cd27-142">You can connect a regular Bluetooth mouse to HoloLens.</span></span> <span data-ttu-id="5cd27-143">已对 clicker 进行了微调, 以便 & 通过 clicker 移动全息影像。</span><span class="sxs-lookup"><span data-stu-id="5cd27-143">The clicker has been fine tuned to enable resizing & moving holograms with a clicker.</span></span> <span data-ttu-id="5cd27-144">键盘的运行效果也比以往更好。</span><span class="sxs-lookup"><span data-stu-id="5cd27-144">Keyboard is also running better than ever.</span></span>
* <span data-ttu-id="5cd27-145">现在, 只需同时按向上键和向下键, 即可获得**混合现实图片**。</span><span class="sxs-lookup"><span data-stu-id="5cd27-145">Now you can take **mixed reality pictures** by simply pressing down the volume up + volume down simultaneously.</span></span> <span data-ttu-id="5cd27-146">你还可以将混合现实捕获的照片 & 视频共享到 Facebook、Twitter 和 YouTube。</span><span class="sxs-lookup"><span data-stu-id="5cd27-146">You can also share your mixed reality captured photos & videos to Facebook, Twitter and YouTube.</span></span>
* <span data-ttu-id="5cd27-147">**混合现实视频**的最大记录长度已增加到五分钟。</span><span class="sxs-lookup"><span data-stu-id="5cd27-147">The maximum recording length of **mixed reality videos** has been increased to five minutes.</span></span>
* <span data-ttu-id="5cd27-148">**照片应用**现在可从 OneDrive 流式传输视频, 而无需在播放前下载整个视频。</span><span class="sxs-lookup"><span data-stu-id="5cd27-148">**Photos app** now streams videos from OneDrive instead of having to download the entire video before playback.</span></span>
* <span data-ttu-id="5cd27-149">我们已改进了你**离开全息影像的**方式。</span><span class="sxs-lookup"><span data-stu-id="5cd27-149">We've improved how your **holograms will be right where you left them**.</span></span> <span data-ttu-id="5cd27-150">你还将看到重新连接到 Wi-fi 的选项, 并且如果 HoloLens 无法检测到这些位置, 请重试。</span><span class="sxs-lookup"><span data-stu-id="5cd27-150">You will also be presented the option to re-connect to Wi-Fi and try again if HoloLens cannot detect where they are.</span></span>
* <span data-ttu-id="5cd27-151">键盘提供了一个**用于输入电子邮件地址的布局**, 其中的密钥允许您通过单击即可输入最受欢迎的电子邮件域。</span><span class="sxs-lookup"><span data-stu-id="5cd27-151">The keyboard has an **improved layout for entering email address** with keys that allow you to enter the most popular email domains with a single click.</span></span>
* <span data-ttu-id="5cd27-152">在 OOBE 期间加快**应用注册**和时区的**自动检测**, 为你提供最佳的第一个用户体验。</span><span class="sxs-lookup"><span data-stu-id="5cd27-152">Faster **app registration** and **auto detection of time zone** during OOBE, giving you the best first user experience.</span></span>
* <span data-ttu-id="5cd27-153">通过**存储感知**, 你可以在 "设置" 应用中查看系统和应用的剩余和已用磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="5cd27-153">**Storage sense** allows you to view remaining and used disk space by the system and apps in the settings app.</span></span>
* <span data-ttu-id="5cd27-154">我们已将反馈应用和内部集线器集中到一个应用**反馈中心**, 该中心将作为向**我们提供反馈**、你喜欢的功能、你可以执行哪些功能的功能, 或者在某些情况下可能更好的情况。</span><span class="sxs-lookup"><span data-stu-id="5cd27-154">We have converged Feedback App and Inside Hub into a single app **Feedback Hub** that will be the go-to tool for **giving us feedback**, which features you love, which features you could do without, or when something could be better.</span></span> <span data-ttu-id="5cd27-155">加入有问必答计划后, 你可以随时**获取最新的内幕资讯**、**评级版本**, 并从反馈中心**知识探寻点反馈**。</span><span class="sxs-lookup"><span data-stu-id="5cd27-155">When you join the Insider Program, you can keep up on **get latest Insider news**, **rate builds** and go on **feedback quests** from Feedback Hub.</span></span>
* <span data-ttu-id="5cd27-156">我们还[发布了更新的 HoloLens 模拟器](install-the-tools.md)生成。</span><span class="sxs-lookup"><span data-stu-id="5cd27-156">We've also [published an updated HoloLens Emulator](install-the-tools.md) build.</span></span>
* <span data-ttu-id="5cd27-157">由于自动**视频抖动**, 混合现实视频现在看起来更好。</span><span class="sxs-lookup"><span data-stu-id="5cd27-157">Your mixed reality videos now look better due to automatic **video stabilization**.</span></span>

## <a name="major-fixes"></a><span data-ttu-id="5cd27-158">主要修补程序</span><span class="sxs-lookup"><span data-stu-id="5cd27-158">Major fixes</span></span>

<span data-ttu-id="5cd27-159">我们修复了全息图空间的问题, 其中的空间速度较慢或检测不正确。</span><span class="sxs-lookup"><span data-stu-id="5cd27-159">We fixed issues with hologram spaces where the spaces would be slow or incorrectly detected.</span></span> <span data-ttu-id="5cd27-160">修复了关机问题, 此问题可能会继续尝试在关闭过程中启动 shell。</span><span class="sxs-lookup"><span data-stu-id="5cd27-160">We fixed a shutdown issue that could continue to try launching the shell during shutdown.</span></span>

<span data-ttu-id="5cd27-161">解决了问题</span><span class="sxs-lookup"><span data-stu-id="5cd27-161">We fixed an issue</span></span>
* <span data-ttu-id="5cd27-162">这会阻止恢复 XAML 应用程序的功能。</span><span class="sxs-lookup"><span data-stu-id="5cd27-162">that blocks the ability to resume a XAML application.</span></span>
* <span data-ttu-id="5cd27-163">出现故障时, 会导致黑屏和一些锯齿线条。</span><span class="sxs-lookup"><span data-stu-id="5cd27-163">where a crash would leave a black screen and some jagged lines.</span></span>
* <span data-ttu-id="5cd27-164">使用某些应用时, 滚动有时会出现错误的方向。</span><span class="sxs-lookup"><span data-stu-id="5cd27-164">scrolling would sometimes stick in the wrong direction when using some apps.</span></span>
* <span data-ttu-id="5cd27-165">当设备仍处于打开状态时, 电源 Led 可能指示为关闭状态。</span><span class="sxs-lookup"><span data-stu-id="5cd27-165">the power LEDs could indicate an off state when the device was still on.</span></span>
* <span data-ttu-id="5cd27-166">从待机状态恢复后, WiFi 可能会关闭。</span><span class="sxs-lookup"><span data-stu-id="5cd27-166">WiFi could get turned off after resuming from standby.</span></span>
* <span data-ttu-id="5cd27-167">Xbox 标识提供程序提供玩家代号设置, 并停滞在循环中。</span><span class="sxs-lookup"><span data-stu-id="5cd27-167">the Xbox identity provider offers gamertag setup and then gets stuck in a loop.</span></span>
* <span data-ttu-id="5cd27-168">如果在 OneDrive 文件选取器中选择下载的文件, Shell 有时会崩溃。</span><span class="sxs-lookup"><span data-stu-id="5cd27-168">the Shell occasionally crashes when selecting a downloaded file in the OneDrive File Picker.</span></span>
* <span data-ttu-id="5cd27-169">按住链接有时会打开一个新的、断开的选项卡并打开上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="5cd27-169">pressing and holding on a link sometimes both opens a new, broken tab and opens a context menu.</span></span>
* <span data-ttu-id="5cd27-170">windows 设备门户不允许从50到80的 IPD 调整</span><span class="sxs-lookup"><span data-stu-id="5cd27-170">where windows device portal didn’t allow IPD adjustments from 50 to 80</span></span>

<span data-ttu-id="5cd27-171">修复了照片问题</span><span class="sxs-lookup"><span data-stu-id="5cd27-171">We fixed issues with Photos where</span></span>
* <span data-ttu-id="5cd27-172">由于忽略 EXIF 方向属性, 图像有时会显示旋转。</span><span class="sxs-lookup"><span data-stu-id="5cd27-172">an image would occasionally display rotated due to ignoring the EXIF orientation property.</span></span>
* <span data-ttu-id="5cd27-173">在启动固定照片时, 它可能会崩溃。</span><span class="sxs-lookup"><span data-stu-id="5cd27-173">it could crash during start-up on pinned Photos.</span></span>
* <span data-ttu-id="5cd27-174">视频会在暂停后重新启动, 而不会从上次暂停的位置继续。</span><span class="sxs-lookup"><span data-stu-id="5cd27-174">videos would restart after pausing instead of continuing from where last paused.</span></span>
* <span data-ttu-id="5cd27-175">如果共享视频是在播放时共享的, 则可能会阻止其重播。</span><span class="sxs-lookup"><span data-stu-id="5cd27-175">replay of a shared video could be prevented if it was shared while playing.</span></span>
* <span data-ttu-id="5cd27-176">混合现实捕获记录将从仅音频源的 0.5-1 秒开始。</span><span class="sxs-lookup"><span data-stu-id="5cd27-176">Mixed Reality Capture recordings would begin with 0.5-1 second of audio only feed.</span></span>
* <span data-ttu-id="5cd27-177">"同步" 按钮在初始 OneDrive 同步过程中消失。</span><span class="sxs-lookup"><span data-stu-id="5cd27-177">the Sync button disappears during initial OneDrive sync.</span></span>

<span data-ttu-id="5cd27-178">已解决设置问题, 其中</span><span class="sxs-lookup"><span data-stu-id="5cd27-178">We fixed issues with settings where</span></span>
* <span data-ttu-id="5cd27-179">环境更改时需要进行刷新。</span><span class="sxs-lookup"><span data-stu-id="5cd27-179">a refresh was needed when the environment changes.</span></span>
* <span data-ttu-id="5cd27-180">键盘上的 "Enter" 不起作用, 如在某些对话框中单击 "下一步"。</span><span class="sxs-lookup"><span data-stu-id="5cd27-180">'Enter' on keyboard would not behave like clicking Next in some dialogs.</span></span>
* <span data-ttu-id="5cd27-181">很难知道 clicker 失败的配对。</span><span class="sxs-lookup"><span data-stu-id="5cd27-181">it was hard to know when the clicker failed pairing.</span></span>
* <span data-ttu-id="5cd27-182">它可能会因为 WiFi 断开连接和连接而无法响应。</span><span class="sxs-lookup"><span data-stu-id="5cd27-182">it could become unresponsive with WiFi disconnect and connect.</span></span>

<span data-ttu-id="5cd27-183">已修复 Cortana 问题,</span><span class="sxs-lookup"><span data-stu-id="5cd27-183">We fixed issues with Cortana where</span></span>
* <span data-ttu-id="5cd27-184">它可能会停滞显示侦听 UI。</span><span class="sxs-lookup"><span data-stu-id="5cd27-184">it could get stuck displaying the Listening UI.</span></span>
* <span data-ttu-id="5cd27-185">如果你回答 "是" 或 "否" 以退出应用程序的请求, 请在独占模式应用中询问 "你好 Cortana, 我会说什么"。</span><span class="sxs-lookup"><span data-stu-id="5cd27-185">asking "Hey Cortana, what can I say" from an exclusive mode app would get stuck if you answered maybe rather yes/no to the request to exit the app.</span></span>
* <span data-ttu-id="5cd27-186">如果要求 Cortana 进入睡眠状态, 然后再继续, Cortana 侦听 UI 将无法正确恢复。</span><span class="sxs-lookup"><span data-stu-id="5cd27-186">the Cortana listening UI doesn't resume correctly if you ask Cortana to go to sleep and then resume.</span></span>
* <span data-ttu-id="5cd27-187">查询 "我连接到哪些网络？"</span><span class="sxs-lookup"><span data-stu-id="5cd27-187">the queries "What network am I connected to?"</span></span> <span data-ttu-id="5cd27-188">"我已连接"。</span><span class="sxs-lookup"><span data-stu-id="5cd27-188">and the "Am I connected?"</span></span> <span data-ttu-id="5cd27-189">当第一个网络配置文件返回无连接时, 可能会失败。</span><span class="sxs-lookup"><span data-stu-id="5cd27-189">could fail when the first network profile comes back with no connectivity.</span></span>
* <span data-ttu-id="5cd27-190">用户界面冻结 "正在侦听", 但在退出应用程序后, 将立即开始执行语音识别。</span><span class="sxs-lookup"><span data-stu-id="5cd27-190">the UI froze on "Listening" but upon exiting an app would immediately began doing speech recognition again.</span></span>
* <span data-ttu-id="5cd27-191">从 Cortana 应用注销时, 无让你重新登录, 直到重新启动。</span><span class="sxs-lookup"><span data-stu-id="5cd27-191">where signing out of the Cortana app wouldn't let you sign back into it until a reboot.</span></span>
* <span data-ttu-id="5cd27-192">当混合现实捕获 UI 处于活动状态时, 它不会启动。</span><span class="sxs-lookup"><span data-stu-id="5cd27-192">it would not launch when Mixed Reality Capture UI was active.</span></span>

<span data-ttu-id="5cd27-193">修复了 Visual Studio 的问题, 其中</span><span class="sxs-lookup"><span data-stu-id="5cd27-193">We fixed issues with Visual Studio where</span></span>
* <span data-ttu-id="5cd27-194">后台任务调试不起作用。</span><span class="sxs-lookup"><span data-stu-id="5cd27-194">background task debugging did not work.</span></span>
* <span data-ttu-id="5cd27-195">图形调试器中的帧分析不起作用。</span><span class="sxs-lookup"><span data-stu-id="5cd27-195">frame analysis in the graphics debugger did not work.</span></span>
* <span data-ttu-id="5cd27-196">如果项目的 TargetPlatformVersion 设置为 10240, 则 HoloLens 模拟器不会出现在 Visual Studio 的下拉列表中。</span><span class="sxs-lookup"><span data-stu-id="5cd27-196">the HoloLens Emulator did not appear in the drop-down list for Visual Studio unless your project's TargetPlatformVersion was set to 10240.</span></span>

## <a name="changes-from-previous-release"></a><span data-ttu-id="5cd27-197">以前版本中的更改</span><span class="sxs-lookup"><span data-stu-id="5cd27-197">Changes from previous release</span></span>
* <span data-ttu-id="5cd27-198">Cortana 命令**你好 cortana, 重新启动设备**不起作用。</span><span class="sxs-lookup"><span data-stu-id="5cd27-198">The Cortana command **Hey Cortana, reboot the device** does not work.</span></span> <span data-ttu-id="5cd27-199">用户可以说 **"你好 cortana"、"重新启动**" 或 "不**是" cortana, 重新启动设备**。</span><span class="sxs-lookup"><span data-stu-id="5cd27-199">User can say **Hey Cortana, restart** or **Hey Cortana, restart the device**.</span></span>
* <span data-ttu-id="5cd27-200">已从产品中删除展台模式。</span><span class="sxs-lookup"><span data-stu-id="5cd27-200">Kiosk mode has been removed from the product.</span></span>

## <a name="prior-release-notes"></a><span data-ttu-id="5cd27-201">以前的发行说明</span><span class="sxs-lookup"><span data-stu-id="5cd27-201">Prior release notes</span></span>
* [<span data-ttu-id="5cd27-202">发行说明 - 2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="5cd27-202">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="5cd27-203">请参阅</span><span class="sxs-lookup"><span data-stu-id="5cd27-203">See also</span></span>
* [<span data-ttu-id="5cd27-204">HoloLens 已知问题</span><span class="sxs-lookup"><span data-stu-id="5cd27-204">HoloLens known issues</span></span>](hololens-known-issues.md)
* [<span data-ttu-id="5cd27-205">安装工具</span><span class="sxs-lookup"><span data-stu-id="5cd27-205">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="5cd27-206">Shell</span><span class="sxs-lookup"><span data-stu-id="5cd27-206">Shell</span></span>](navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="5cd27-207">更新混合现实的 2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="5cd27-207">Updating 2D UWP apps for mixed reality</span></span>](building-2d-apps.md)
* [<span data-ttu-id="5cd27-208">硬件配件</span><span class="sxs-lookup"><span data-stu-id="5cd27-208">Hardware accessories</span></span>](hardware-accessories.md)
* [<span data-ttu-id="5cd27-209">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="5cd27-209">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="5cd27-210">语音输入</span><span class="sxs-lookup"><span data-stu-id="5cd27-210">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="5cd27-211">向 Windows 应用商店提交应用程序</span><span class="sxs-lookup"><span data-stu-id="5cd27-211">Submitting an app to the Windows Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="5cd27-212">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="5cd27-212">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
