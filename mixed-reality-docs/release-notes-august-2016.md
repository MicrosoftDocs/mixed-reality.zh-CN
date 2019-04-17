---
title: 发行说明-2016 年 8 月
description: HoloLens 的 Windows 10 周年版本 (2016 年秋季) 发行说明
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，发行说明、 操作系统、 平台、 功能、 商业套件
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592753"
---
# <a name="release-notes---august-2016"></a><span data-ttu-id="4e673-104">发行说明-2016 年 8 月</span><span class="sxs-lookup"><span data-stu-id="4e673-104">Release notes - August 2016</span></span>

<span data-ttu-id="4e673-105">HoloLens 团队正在侦听从开发人员的 Windows 预览体验计划，以确定工作的优先级的反馈。</span><span class="sxs-lookup"><span data-stu-id="4e673-105">The HoloLens team is listening to feedback from developers in the Windows Insider Program to prioritize our work.</span></span> <span data-ttu-id="4e673-106">请继续执行[向我们提供反馈](give-us-feedback.md)反馈中心，通过[开发人员论坛](https://forums.hololens.com)并[通过 Twitter @HoloLens ](https://twitter.com/hololens)。</span><span class="sxs-lookup"><span data-stu-id="4e673-106">Please continue to [give us feedback](give-us-feedback.md) through the Feedback Hub, the [developer forums](https://forums.hololens.com) and [Twitter via @HoloLens](https://twitter.com/hololens).</span></span> <span data-ttu-id="4e673-107">为 Windows 10 周年更新中，HoloLens 团队令人满意地交付的接受，进一步提高全息版体验。</span><span class="sxs-lookup"><span data-stu-id="4e673-107">As Windows 10 embraces the Anniversary Update, the HoloLens team is happy to deliver further improve to the holographic experience.</span></span> <span data-ttu-id="4e673-108">在此更新中，我们侧重于主要的修补程序、 改进和简介请求由企业和 Microsoft HoloLens 商业套件中提供的功能。</span><span class="sxs-lookup"><span data-stu-id="4e673-108">In this update, we focused on major fixes, improvements, and introducing features requested by businesses and available in the Microsoft HoloLens Commercial Suite.</span></span>

<span data-ttu-id="4e673-109">**最新版本：** Windows 全息版 2016 年 8 月更新 (**10.0.14393.0**，Windows 10 周年纪念版)</span><span class="sxs-lookup"><span data-stu-id="4e673-109">**Latest release:** Windows Holographic August 2016 Update (**10.0.14393.0**, Windows 10 Anniversary Release)</span></span>

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

<span data-ttu-id="4e673-110">向[更新到当前版本](updating-hololens.md)，打开*设置*应用程序中，转到*更新和安全*，然后选择*检查更新*按钮。</span><span class="sxs-lookup"><span data-stu-id="4e673-110">To [update to the current release](updating-hololens.md), open the *Settings* app, go to *Update & Security*, then select the *Check for updates* button.</span></span>

## <a name="new-features"></a><span data-ttu-id="4e673-111">新增功能</span><span class="sxs-lookup"><span data-stu-id="4e673-111">New features</span></span>

<span data-ttu-id="4e673-112">**附加到进程调试**HoloLens 现在支持附加到进程进行调试。</span><span class="sxs-lookup"><span data-stu-id="4e673-112">**Attach To Process Debugging** HoloLens now supports attach-to-process debugging.</span></span> <span data-ttu-id="4e673-113">可以使用 Visual Studio 2015 Update 3 连接到在 HoloLens 上正在运行的应用和[开始调试它](using-visual-studio.md#debugging-an-installed-or-running-app)。</span><span class="sxs-lookup"><span data-stu-id="4e673-113">You can use Visual Studio 2015 Update 3 to connect to a running app on a HoloLens and [start debugging it](using-visual-studio.md#debugging-an-installed-or-running-app).</span></span> <span data-ttu-id="4e673-114">这适用于无需从 Visual Studio 项目中进行部署。</span><span class="sxs-lookup"><span data-stu-id="4e673-114">This works without the need to deploy from a Visual Studio project.</span></span>

<span data-ttu-id="4e673-115">**更新 HoloLens 模拟器**我们还发布了 HoloLens 仿真程序的更新的版本。</span><span class="sxs-lookup"><span data-stu-id="4e673-115">**Updated HoloLens Emulator** We've also released an updated version of the HoloLens Emulator.</span></span>

<span data-ttu-id="4e673-116">**游戏板支持**现在可以搭配使用，并使用 HoloLens 蓝牙游戏板 ！</span><span class="sxs-lookup"><span data-stu-id="4e673-116">**Gamepad Support** You can now pair and use Bluetooth gamepads with HoloLens!</span></span> <span data-ttu-id="4e673-117">新发布的 Xbox 无线控制器 S 可用于播放您最喜欢的游戏板启用游戏和应用程序和功能蓝牙功能。</span><span class="sxs-lookup"><span data-stu-id="4e673-117">The newly released Xbox Wireless Controller S features Bluetooth capabilities and can be used to play your favorite gamepad-enabled games and apps.</span></span> <span data-ttu-id="4e673-118">一个[控制器更新](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)之前你可以使用 HoloLens 连接 Xbox 无线控制器 S 必须应用。</span><span class="sxs-lookup"><span data-stu-id="4e673-118">A [controller update](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) must be applied before you can connect the Xbox Wireless Controller S with HoloLens.</span></span> <span data-ttu-id="4e673-119">支持 Xbox 无线控制器 S [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)并[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) Api。</span><span class="sxs-lookup"><span data-stu-id="4e673-119">The Xbox Wireless Controller S is supported by [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) and [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) APIs.</span></span> <span data-ttu-id="4e673-120">蓝牙控制器的其他模型可能通过访问[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API。</span><span class="sxs-lookup"><span data-stu-id="4e673-120">Additional models of Bluetooth controllers may be accessed through the [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.</span></span>

## <a name="improvements-and-fixes"></a><span data-ttu-id="4e673-121">改进和修复</span><span class="sxs-lookup"><span data-stu-id="4e673-121">Improvements and fixes</span></span>

<span data-ttu-id="4e673-122">因此，除了 Hololens 特定的修补程序，您还将接收的全部优势从 Windows 更新以增加平台可靠性和性能，我们已与 Windows 10 周年更新中，其余部分同步。</span><span class="sxs-lookup"><span data-stu-id="4e673-122">We are in sync with the rest of the Windows 10 Anniversary update, so in addition to the Hololens specific fixes, you are also receiving all the goodness from the Windows update to increase platform reliability and performance.</span></span> <span data-ttu-id="4e673-123">你的反馈是高值和设置优先级的版本中修复。</span><span class="sxs-lookup"><span data-stu-id="4e673-123">Your feedback is highly valued and prioritized for fixes in the release.</span></span>

<span data-ttu-id="4e673-124">我们改进了以下体验：</span><span class="sxs-lookup"><span data-stu-id="4e673-124">We've improved the following experiences:</span></span>
* <span data-ttu-id="4e673-125">登录体验。</span><span class="sxs-lookup"><span data-stu-id="4e673-125">log in experiences.</span></span>
* <span data-ttu-id="4e673-126">加入工作区。</span><span class="sxs-lookup"><span data-stu-id="4e673-126">workplace join.</span></span>
* <span data-ttu-id="4e673-127">设备电源状态转换的电源效率。</span><span class="sxs-lookup"><span data-stu-id="4e673-127">power efficiency for device power state transitions.</span></span>
* <span data-ttu-id="4e673-128">使用混合现实捕获的稳定性。</span><span class="sxs-lookup"><span data-stu-id="4e673-128">stability with Mixed Reality Captures.</span></span>
* <span data-ttu-id="4e673-129">蓝牙连接的可靠性</span><span class="sxs-lookup"><span data-stu-id="4e673-129">reliability for Bluetooth connectivity</span></span>
* <span data-ttu-id="4e673-130">多应用程序方案中的 hologram 持久性。</span><span class="sxs-lookup"><span data-stu-id="4e673-130">hologram persistence in multi app scenario.</span></span>

<span data-ttu-id="4e673-131">我们还修复了以下问题：</span><span class="sxs-lookup"><span data-stu-id="4e673-131">We've fixed the following issues:</span></span>
* <span data-ttu-id="4e673-132">Visual Studio 探查器和图形调试器无法进行连接。</span><span class="sxs-lookup"><span data-stu-id="4e673-132">the Visual Studio profilers and graphics debugger fail to connect.</span></span>
* <span data-ttu-id="4e673-133">照片和文档根本不显示在设备门户中的文件资源管理器中。</span><span class="sxs-lookup"><span data-stu-id="4e673-133">photos & documents do not show up in the file explorer in the device portal.</span></span>
* <span data-ttu-id="4e673-134">将光标放置在它在调整模式下时，可以闪烁应用程序栏。</span><span class="sxs-lookup"><span data-stu-id="4e673-134">the App Bar can flash when the cursor is placed above it while in Adjust mode.</span></span>
* <span data-ttu-id="4e673-135">在调整模式下，关注的视线移动圆点光标将更改为 4 箭头光标一段时间速度更慢。</span><span class="sxs-lookup"><span data-stu-id="4e673-135">When in Adjust mode, the eye gaze dot cursor will change to the 4-arrow cursor sometime more slowly.</span></span>
* <span data-ttu-id="4e673-136">"您好 Cortana 播放音乐"不启动 Groove。</span><span class="sxs-lookup"><span data-stu-id="4e673-136">"Hey Cortana play music" does not launch Groove.</span></span>
* <span data-ttu-id="4e673-137">上一更新后，说"转到主页"不 pin 面板中正确显示。</span><span class="sxs-lookup"><span data-stu-id="4e673-137">after the previous update, saying "Go Home" does not display the pins panel correctly.</span></span>

## <a name="introducing-microsoft-hololens-commercial-suite"></a><span data-ttu-id="4e673-138">Microsoft HoloLens 商业套件简介</span><span class="sxs-lookup"><span data-stu-id="4e673-138">Introducing Microsoft HoloLens Commercial Suite</span></span>

<span data-ttu-id="4e673-139">Microsoft HoloLens 商业套件是准备好进行企业部署。</span><span class="sxs-lookup"><span data-stu-id="4e673-139">The Microsoft HoloLens Commercial Suite is ready for enterprise deployment.</span></span> <span data-ttu-id="4e673-140">我们添加了多个高度请求[商业功能](commercial-features.md)从我们早期的业务合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="4e673-140">We've added several highly requested [commercial features](commercial-features.md) from our early business partners.</span></span>

<span data-ttu-id="4e673-141">请联系您当地的 Microsoft 客户经理以购买 Microsoft HoloLens 商业套件。</span><span class="sxs-lookup"><span data-stu-id="4e673-141">Please contact your local Microsoft account manager to purchase the Microsoft HoloLens Commercial Suite.</span></span>

### <a name="key-commercial-features"></a><span data-ttu-id="4e673-142">主要的商业功能</span><span class="sxs-lookup"><span data-stu-id="4e673-142">Key Commercial Features</span></span> 

* <span data-ttu-id="4e673-143">**展台模式。**</span><span class="sxs-lookup"><span data-stu-id="4e673-143">**Kiosk mode.**</span></span> <span data-ttu-id="4e673-144">HoloLens 展台模式下，您可以限制哪些应用程序运行，以启用演示或展示体验。</span><span class="sxs-lookup"><span data-stu-id="4e673-144">With HoloLens kiosk mode, you can limit which apps to run to enable demo or showcase experiences.</span></span><br>
  <span data-ttu-id="4e673-145">![展台模式下，HoloLens 直接到所选的应用程序将启动。](images/201608-kioskmode-400px.png)</span><span class="sxs-lookup"><span data-stu-id="4e673-145">![With kiosk mode, HoloLens launches directly into the app of your choice.](images/201608-kioskmode-400px.png)</span></span>
* <span data-ttu-id="4e673-146">**HoloLens 的移动设备管理 (MDM)。**</span><span class="sxs-lookup"><span data-stu-id="4e673-146">**Mobile Device Management (MDM) for HoloLens.**</span></span> <span data-ttu-id="4e673-147">你的 IT 部门可以管理多个同时使用解决方案，如 Microsoft Intune 的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="4e673-147">Your IT department can manage multiple HoloLens devices simultaneously using solutions like Microsoft Intune.</span></span> <span data-ttu-id="4e673-148">你将能够管理设置，选择要安装的应用，并设置根据你的组织需要定制的安全配置。</span><span class="sxs-lookup"><span data-stu-id="4e673-148">You will be able to manage settings, select apps to install and set security configurations tailored to your organization's need.</span></span><br>
  <span data-ttu-id="4e673-149">![HoloLens 上的移动设备管理提供了跨多个设备的企业级设备管理。](images/201608-enterprisemanagement-400px.png)</span><span class="sxs-lookup"><span data-stu-id="4e673-149">![Mobile Device Management on HoloLens provides enterprise grade device management across multiple devices.](images/201608-enterprisemanagement-400px.png)</span></span>
* <span data-ttu-id="4e673-150">**适用于企业的 Windows 更新。**</span><span class="sxs-lookup"><span data-stu-id="4e673-150">**Windows Update for Business.**</span></span> <span data-ttu-id="4e673-151">控制设备和对长期服务分支的支持的操作系统更新。</span><span class="sxs-lookup"><span data-stu-id="4e673-151">Controlled operating system updates to devices and support for long term servicing branch.</span></span>
* <span data-ttu-id="4e673-152">**数据安全性。**</span><span class="sxs-lookup"><span data-stu-id="4e673-152">**Data security.**</span></span> <span data-ttu-id="4e673-153">HoloLens 上启用 BitLocker 数据加密来提供相同级别的任何其他 Windows 设备的安全保护。</span><span class="sxs-lookup"><span data-stu-id="4e673-153">BitLocker data encryption is enabled on HoloLens to provide the same level of security protection as any other Windows device.</span></span>
* <span data-ttu-id="4e673-154">**工作单位访问。**</span><span class="sxs-lookup"><span data-stu-id="4e673-154">**Work access.**</span></span> <span data-ttu-id="4e673-155">你的组织中的任何人可以远程连接到通过虚拟专用网络上 HoloLens 企业网络。</span><span class="sxs-lookup"><span data-stu-id="4e673-155">Anyone in your organization can remotely connect to the corporate network through virtual private network on a HoloLens.</span></span> <span data-ttu-id="4e673-156">HoloLens 还可以访问需要凭据的 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="4e673-156">HoloLens can also access Wi-Fi networks that require credentials.</span></span>
* <span data-ttu-id="4e673-157">**企业的 Microsoft Store。**</span><span class="sxs-lookup"><span data-stu-id="4e673-157">**Microsoft Store for Business.**</span></span> <span data-ttu-id="4e673-158">你的 IT 部门还可以设置企业专用应用商店，其中包含仅适用于特定的 HoloLens 使用公司的应用。</span><span class="sxs-lookup"><span data-stu-id="4e673-158">Your IT department can also set up an enterprise private store, containing only your company’s apps for your specific HoloLens usage.</span></span> <span data-ttu-id="4e673-159">安全地在企业软件分发到所选企业用户组。</span><span class="sxs-lookup"><span data-stu-id="4e673-159">Securely distribute your enterprise software to selected group of enterprise users.</span></span>

### <a name="development-edition-vs-commercial-suite"></a><span data-ttu-id="4e673-160">开发版本 vs。商业套件</span><span class="sxs-lookup"><span data-stu-id="4e673-160">Development Edition vs. Commercial Suite</span></span>

<table>
<tr>
<th><span data-ttu-id="4e673-161">功能</span><span class="sxs-lookup"><span data-stu-id="4e673-161">Features</span></span></th><th><span data-ttu-id="4e673-162">Development Edition</span><span class="sxs-lookup"><span data-stu-id="4e673-162">Development Edition</span></span></th><th><span data-ttu-id="4e673-163">商业套件</span><span class="sxs-lookup"><span data-stu-id="4e673-163">Commercial Suite</span></span></th>
</tr><tr>
<td><span data-ttu-id="4e673-164">设备加密 (Bitlocker)</span><span class="sxs-lookup"><span data-stu-id="4e673-164">Device Encryption (Bitlocker)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="4e673-165">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-165">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-166">虚拟专用网络 (VPN)</span><span class="sxs-lookup"><span data-stu-id="4e673-166">Virtual Private Network (VPN)</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="4e673-167">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-167">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-168"><a href="using-the-windows-device-portal.md#kiosk-mode">展台模式</a></span><span class="sxs-lookup"><span data-stu-id="4e673-168"><a href="using-the-windows-device-portal.md#kiosk-mode">Kiosk mode</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="4e673-169">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-169">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="4e673-170">管理和部署</span><span class="sxs-lookup"><span data-stu-id="4e673-170">Management and deployment</span></span></th>
</tr><tr>
<td><span data-ttu-id="4e673-171">移动设备管理 (MDM)</span><span class="sxs-lookup"><span data-stu-id="4e673-171">Mobile Device Management (MDM)</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="4e673-172">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-172">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-173">阻止取消注册功能</span><span class="sxs-lookup"><span data-stu-id="4e673-173">Ability to block un-enrollment</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="4e673-174">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-174">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-175">基于证书的公司的 Wi-fi 访问权限</span><span class="sxs-lookup"><span data-stu-id="4e673-175">Cert Based Corporate Wi-Fi Access</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="4e673-176">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-176">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-177">Microsoft Store （使用者）</span><span class="sxs-lookup"><span data-stu-id="4e673-177">Microsoft Store (Consumer)</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-178">使用者</span><span class="sxs-lookup"><span data-stu-id="4e673-178">Consumer</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-179">通过 MDM 进行筛选</span><span class="sxs-lookup"><span data-stu-id="4e673-179">Filtering via MDM</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">业务应用商店门户</a></span><span class="sxs-lookup"><span data-stu-id="4e673-180"><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Business Store Portal</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="4e673-181">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-181">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="4e673-182">安全和标识</span><span class="sxs-lookup"><span data-stu-id="4e673-182">Security and Identity</span></span></th>
</tr><tr>
<td><span data-ttu-id="4e673-183">使用 Azure Active Directory (AAD) 的登录名</span><span class="sxs-lookup"><span data-stu-id="4e673-183">Login with Azure Active Directory (AAD)</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-184">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-184">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-185">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-185">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-186">使用 Microsoft 帐户 (MSA) 登录</span><span class="sxs-lookup"><span data-stu-id="4e673-186">Login with Microsoft Account (MSA)</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-187">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-187">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-188">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-188">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-189">下一代凭据使用 PIN 解锁</span><span class="sxs-lookup"><span data-stu-id="4e673-189">Next Generation Credentials with PIN unlock</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-190">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-190">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-191">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-191">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">安全启动</a></span><span class="sxs-lookup"><span data-stu-id="4e673-192"><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Secure boot</a></span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-193">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-193">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-194">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-194">✔️</span></span></td>
</tr><tr>
<th colspan="3" style="text-align: left;"> <span data-ttu-id="4e673-195">服务和支持</span><span class="sxs-lookup"><span data-stu-id="4e673-195">Servicing and Support</span></span></th>
</tr><tr>
<td><span data-ttu-id="4e673-196">自动系统更新它们到达时</span><span class="sxs-lookup"><span data-stu-id="4e673-196">Automatic system updates as they arrive</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-197">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-197">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4e673-198">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-198">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">适用于企业的 Windows 更新</a></span><span class="sxs-lookup"><span data-stu-id="4e673-199"><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update for Business</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="4e673-200">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-200">✔️</span></span></td>
</tr><tr>
<td><span data-ttu-id="4e673-201">长期服务分支</span><span class="sxs-lookup"><span data-stu-id="4e673-201">Long term servicing branch</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="4e673-202">✔️</span><span class="sxs-lookup"><span data-stu-id="4e673-202">✔️</span></span></td>
</tr>
</table>

## <a name="prior-release-notes"></a><span data-ttu-id="4e673-203">以前的发行说明</span><span class="sxs-lookup"><span data-stu-id="4e673-203">Prior release notes</span></span>
* [<span data-ttu-id="4e673-204">发行说明-2016 年 5 月</span><span class="sxs-lookup"><span data-stu-id="4e673-204">Release notes - May 2016</span></span>](release-notes-may-2016.md)
* [<span data-ttu-id="4e673-205">发行说明-2016 年 3 月</span><span class="sxs-lookup"><span data-stu-id="4e673-205">Release notes - March 2016</span></span>](release-notes-march-2016.md)

## <a name="see-also"></a><span data-ttu-id="4e673-206">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e673-206">See also</span></span>
* [<span data-ttu-id="4e673-207">HoloLens 的已知问题</span><span class="sxs-lookup"><span data-stu-id="4e673-207">HoloLens known issues</span></span>](hololens-known-issues.md)
* [<span data-ttu-id="4e673-208">商业特性</span><span class="sxs-lookup"><span data-stu-id="4e673-208">Commercial features</span></span>](commercial-features.md)
* [<span data-ttu-id="4e673-209">安装工具</span><span class="sxs-lookup"><span data-stu-id="4e673-209">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="4e673-210">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="4e673-210">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
