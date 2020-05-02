---
title: 使用 Windows 设备门户
description: 使用适用于 HoloLens 的 Windows 设备门户可以通过 Wi-Fi 或 USB 远程配置和管理设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包含许多工具，可帮助你管理 HoloLens 以及调试和优化应用。
author: jonmlyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 设备门户，HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 9cd9b33fed12802e5b41afa3fee850356911a989
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "81278025"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="e37f3-106">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="e37f3-106">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="e37f3-107">功能</span><span class="sxs-lookup"><span data-stu-id="e37f3-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="e37f3-108"><a href="hololens-hardware-details.md">HoloLens（第一代）</a></span><span class="sxs-lookup"><span data-stu-id="e37f3-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="e37f3-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e37f3-109">HoloLens 2</span></span></th><th style="width:150px"><span data-ttu-id="e37f3-110"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="e37f3-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e37f3-111">Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="e37f3-111">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="e37f3-112">✔️</span><span class="sxs-lookup"><span data-stu-id="e37f3-112">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e37f3-113">✔️</span><span class="sxs-lookup"><span data-stu-id="e37f3-113">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="e37f3-114">使用适用于 HoloLens 的 Windows 设备门户可以通过 Wi-Fi 或 USB 远程配置和管理设备。</span><span class="sxs-lookup"><span data-stu-id="e37f3-114">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="e37f3-115">Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。</span><span class="sxs-lookup"><span data-stu-id="e37f3-115">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="e37f3-116">设备门户包含许多工具，可帮助你管理 HoloLens 以及调试和优化应用。</span><span class="sxs-lookup"><span data-stu-id="e37f3-116">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="e37f3-117">本文档专门介绍适用于 HoloLens 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="e37f3-117">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="e37f3-118">若要使用适用于桌面（包括 Windows Mixed Reality）的 Windows 设备门户，请参阅 [Windows 设备门户概述](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="e37f3-118">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="e37f3-119">将 HoloLens 设置为使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="e37f3-119">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="e37f3-120">打开 HoloLens 的电源，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="e37f3-120">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="e37f3-121">针对 HoloLens2 执行[开始手势](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)，或者在 HoloLens（第一代）上执行[开花手势](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)，以启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="e37f3-121">Perform the [Start gesture](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) for HoloLens2 or [Bloom](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (1st Gen) to launch the main menu.</span></span> 
3. <span data-ttu-id="e37f3-122">凝视“设置”磁贴，然后在 HoloLens（第一代）上执行[隔空敲击](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)手势，或者在 HoloLens 2 上通过[触摸或手部射线](https://docs.microsoft.com/hololens/hololens2-basic-usage)选择该磁贴。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-122">Gaze at the **Settings** tile and perform the [air-tap](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) gesture on HoloLens (1st Gen) or select it on HoloLens 2 by [touching it or using a Hand ray](https://docs.microsoft.com/hololens/hololens2-basic-usage).</span></span> 
4. <span data-ttu-id="e37f3-123">选择“更新”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="e37f3-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="e37f3-124">选择“面向开发人员”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="e37f3-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="e37f3-125">启用“开发人员模式”  。</span><span class="sxs-lookup"><span data-stu-id="e37f3-125">Enable **Developer Mode**.</span></span>
7. <span data-ttu-id="e37f3-126">[向下滚动](gaze-and-commit.md#composite-gestures)并启用“设备门户”。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-126">[Scroll down](gaze-and-commit.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="e37f3-127">如果要设置 Windows 设备门户以便可以通过 USB 或 Wi-Fi 将应用部署到此 HoloLens，请单击“配对”以[生成配对 PIN](using-visual-studio.md)。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-127">If you are setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, click **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="e37f3-128">在首次部署期间，请在“PIN”弹出窗口中保持打开“设置”应用，直到在 Visual Studio 中输入了 PIN 才将它关闭。</span><span class="sxs-lookup"><span data-stu-id="e37f3-128">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

   ![在 Windows Holographic 的“设置”应用中启用开发人员模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="e37f3-130">通过 Wi-Fi 进行连接</span><span class="sxs-lookup"><span data-stu-id="e37f3-130">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="e37f3-131">[将 HoloLens 连接到 Wi-Fi](connecting-to-wi-fi-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="e37f3-131">[Connect your HoloLens to Wi-Fi](connecting-to-wi-fi-on-hololens.md).</span></span>
2. <span data-ttu-id="e37f3-132">查找设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e37f3-132">Look up your device's IP address.</span></span>
   * <span data-ttu-id="e37f3-133">在设备上的“设置”>“网络和 Internet”>“Wi-Fi”>“高级选项”下查找 IP 地址。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-133">Find the IP address on the device under **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
3. <span data-ttu-id="e37f3-134">在电脑上的 Web 浏览器中，转到 https://<HOLOLENS IP 地址></span><span class="sxs-lookup"><span data-stu-id="e37f3-134">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="e37f3-135">浏览器中将显示以下消息：“此网站的安全证书有问题。”</span><span class="sxs-lookup"><span data-stu-id="e37f3-135">The browser will display the following message: "There's a problem with this website's security certificate".</span></span> <span data-ttu-id="e37f3-136">由于颁发给 Device Portal 的证书是测试证书，因此会显示上述消息。</span><span class="sxs-lookup"><span data-stu-id="e37f3-136">This happens because the certificate which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="e37f3-137">你可以暂时忽略此证书错误并继续。</span><span class="sxs-lookup"><span data-stu-id="e37f3-137">You can ignore this certificate error for now and proceed.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="e37f3-138">通过 USB 进行连接</span><span class="sxs-lookup"><span data-stu-id="e37f3-138">Connecting over USB</span></span>

1. <span data-ttu-id="e37f3-139">[安装所需的工具](install-the-tools.md)，确保在电脑上安装包含 Windows 10 开发人员工具的 Visual Studio Update 1。</span><span class="sxs-lookup"><span data-stu-id="e37f3-139">[Install the tools](install-the-tools.md) to make sure you have Visual Studio Update 1 with the Windows 10 developer tools installed on your PC.</span></span> <span data-ttu-id="e37f3-140">这支持 USB 连接。</span><span class="sxs-lookup"><span data-stu-id="e37f3-140">This enables USB connectivity.</span></span>
2. <span data-ttu-id="e37f3-141">使用适用于 HoloLens（第一代）的 micro-USB 数据线或适用于 HoloLens 2 的 USB-C 数据线将 HoloLens 连接到电脑。</span><span class="sxs-lookup"><span data-stu-id="e37f3-141">Connect your HoloLens to your PC with a micro-USB cable for HoloLens (1st Gen) or USB-C for HoloLens 2.</span></span>
3. <span data-ttu-id="e37f3-142">在电脑上的 Web 浏览器中，转到 [https://127.0.0.1:10080](https://127.0.0.1:10080)。</span><span class="sxs-lookup"><span data-stu-id="e37f3-142">From a web browser on your PC, go to [https://127.0.0.1:10080](https://127.0.0.1:10080).</span></span>

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="e37f3-143">连接到仿真器</span><span class="sxs-lookup"><span data-stu-id="e37f3-143">Connecting to an emulator</span></span>

<span data-ttu-id="e37f3-144">也可以将 Device Portal 与仿真器结合使用。</span><span class="sxs-lookup"><span data-stu-id="e37f3-144">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="e37f3-145">若要连接到设备门户，请使用[工具栏](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="e37f3-145">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="e37f3-146">单击此图标：![“打开设备门户”图标](images/emulator-deviceportal.png) **打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="e37f3-146">Click on this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="e37f3-147">创建用户名和密码</span><span class="sxs-lookup"><span data-stu-id="e37f3-147">Creating a Username and Password</span></span>

<span data-ttu-id="e37f3-148">![设置对 Windows 设备门户的访问](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-148">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-149">*设置对 Windows 设备门户的访问*</span><span class="sxs-lookup"><span data-stu-id="e37f3-149">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="e37f3-150">首次连接到 HoloLens 上的 Device Portal 时，需要创建用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="e37f3-150">The first time you connect to the Device Portal on your HoloLens, you will need to create a username and password.</span></span>
1. <span data-ttu-id="e37f3-151">在电脑上的 Web 浏览器中，输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e37f3-151">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="e37f3-152">将打开“设置访问”页面。</span><span class="sxs-lookup"><span data-stu-id="e37f3-152">The Set up access page opens.</span></span>
2. <span data-ttu-id="e37f3-153">单击或敲击“请求 PIN”，然后查看 HoloLens 屏幕以获取生成的 PIN。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-153">Click or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="e37f3-154">在“设备上显示的 PIN”文本框中输入该 PIN。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-154">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="e37f3-155">输入将用于连接到 Device Portal 的用户名。</span><span class="sxs-lookup"><span data-stu-id="e37f3-155">Enter the user name you will use to connect to the Device Portal.</span></span> <span data-ttu-id="e37f3-156">无需使用 Microsoft 帐户 (MSA) 名称或域名作为用户名。</span><span class="sxs-lookup"><span data-stu-id="e37f3-156">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="e37f3-157">输入密码并进行确认。</span><span class="sxs-lookup"><span data-stu-id="e37f3-157">Enter a password and confirm it.</span></span> <span data-ttu-id="e37f3-158">密码长度必须至少为七个字符。</span><span class="sxs-lookup"><span data-stu-id="e37f3-158">The password must be at least seven characters in length.</span></span> <span data-ttu-id="e37f3-159">无需使用 MSA 密码或域密码作为密码。</span><span class="sxs-lookup"><span data-stu-id="e37f3-159">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="e37f3-160">单击“配对”以连接到 HoloLens 上的 Windows 设备门户。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-160">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="e37f3-161">今后如果你想要更改此用户名和密码，可以导航到 https://<HOLOLENS IP 地址>/devicepair.htm 来访问设备安全性页，然后重复上述过程。</span><span class="sxs-lookup"><span data-stu-id="e37f3-161">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="e37f3-162">安全证书</span><span class="sxs-lookup"><span data-stu-id="e37f3-162">Security certificate</span></span>

<span data-ttu-id="e37f3-163">如果在浏览器中看到“证书错误”，可以通过创建与该设备的信任关系来修复该错误。</span><span class="sxs-lookup"><span data-stu-id="e37f3-163">If you see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="e37f3-164">每个 HoloLens 会生成唯一的自签名证书以供其 SSL 连接使用。</span><span class="sxs-lookup"><span data-stu-id="e37f3-164">Each HoloLens generates a unique self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="e37f3-165">默认情况下，此证书不受电脑的 Web 浏览器信任，因此你可能会看到“证书错误”。</span><span class="sxs-lookup"><span data-stu-id="e37f3-165">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="e37f3-166">通过从你的 HoloLens 下载此证书（借助 USB 或信任的 WLAN 网络）并在你的电脑上信任该证书，可以安全地连接到设备。</span><span class="sxs-lookup"><span data-stu-id="e37f3-166">By downloading this certificate from your HoloLens (over USB or a Wi-Fi network you trust) and trusting it on your PC, you can securely connect to your device.</span></span>
1. <span data-ttu-id="e37f3-167">**确保在安全网络（USB 或信任的 Wi-Fi 网络）中操作。**</span><span class="sxs-lookup"><span data-stu-id="e37f3-167">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="e37f3-168">从设备门户上的“安全性”页下载此设备的证书。</span><span class="sxs-lookup"><span data-stu-id="e37f3-168">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="e37f3-169">导航到 https://<HOLOLENS IP 地址>/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="e37f3-169">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
   * <span data-ttu-id="e37f3-170">打开“系统”>“首选项”对应的节点。</span><span class="sxs-lookup"><span data-stu-id="e37f3-170">Open the node for System > Preferences.</span></span> 
   * <span data-ttu-id="e37f3-171">向下滚动到“设备安全性”，然后单击“下载此设备的证书”按钮。</span><span class="sxs-lookup"><span data-stu-id="e37f3-171">Scroll down to Device Security, click the "Download this device's certificate" button.</span></span>
3. <span data-ttu-id="e37f3-172">在电脑上安装“受信任的根证书颁发机构”存储中的证书。</span><span class="sxs-lookup"><span data-stu-id="e37f3-172">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="e37f3-173">在 Windows 菜单中键入：管理计算机证书并启动小程序。</span><span class="sxs-lookup"><span data-stu-id="e37f3-173">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="e37f3-174">展开“受信任的根证书颁发机构”文件夹。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-174">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="e37f3-175">单击“证书”文件夹。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-175">Click the **Certificates** folder.</span></span>
   * <span data-ttu-id="e37f3-176">在“操作”菜单中选择：“所有任务”>“导入...”</span><span class="sxs-lookup"><span data-stu-id="e37f3-176">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="e37f3-177">使用从 Device Portal 下载的证书文件，完成“证书导入向导”。</span><span class="sxs-lookup"><span data-stu-id="e37f3-177">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="e37f3-178">重新启动浏览器。</span><span class="sxs-lookup"><span data-stu-id="e37f3-178">Restart the browser.</span></span>

>[!NOTE]
> <span data-ttu-id="e37f3-179">此证书仅在该设备上受信任，如果刷写了设备，用户必须再次执行此过程。</span><span class="sxs-lookup"><span data-stu-id="e37f3-179">This certificate will only be trusted for the device and the user will have to go through the process again if the device is flashed.</span></span>


## <a name="device-portal-pages"></a><span data-ttu-id="e37f3-180">Device Portal 页面</span><span class="sxs-lookup"><span data-stu-id="e37f3-180">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="e37f3-181">主页</span><span class="sxs-lookup"><span data-stu-id="e37f3-181">Home</span></span>

<span data-ttu-id="e37f3-182">![Microsoft HoloLens 上的 Windows 设备门户主页](images/windows-device-portal-home-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-182">![Windows Device Portal home page on Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-183">*Microsoft HoloLens 上的 Windows 设备门户主页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-183">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-184">Device Portal 会话从主页开始。</span><span class="sxs-lookup"><span data-stu-id="e37f3-184">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="e37f3-185">可从主页的左侧导航栏访问其他页面。</span><span class="sxs-lookup"><span data-stu-id="e37f3-185">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="e37f3-186">主页顶部的工具栏提供对常用状态和功能的访问。</span><span class="sxs-lookup"><span data-stu-id="e37f3-186">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="e37f3-187">**联机**：指示设备是否已连接到 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="e37f3-187">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="e37f3-188">**关机**：关闭设备。</span><span class="sxs-lookup"><span data-stu-id="e37f3-188">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="e37f3-189">**重启**：关闭再打开设备的电源。</span><span class="sxs-lookup"><span data-stu-id="e37f3-189">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="e37f3-190">**安全**：打开“设备安全性”页。</span><span class="sxs-lookup"><span data-stu-id="e37f3-190">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="e37f3-191">**冷**：指示设备的温度。</span><span class="sxs-lookup"><span data-stu-id="e37f3-191">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="e37f3-192">**交流电源**：指示设备是否已接上电源并正在充电。</span><span class="sxs-lookup"><span data-stu-id="e37f3-192">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="e37f3-193">**帮助**：打开 REST 接口文档页。</span><span class="sxs-lookup"><span data-stu-id="e37f3-193">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="e37f3-194">主页将显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="e37f3-194">The home page shows the following info:</span></span>
* <span data-ttu-id="e37f3-195">**设备状态：** 监视设备的运行状况并报告严重错误。</span><span class="sxs-lookup"><span data-stu-id="e37f3-195">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="e37f3-196">**Windows 信息：** 显示 HoloLens 的名称，以及当前安装的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="e37f3-196">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="e37f3-197">**首选项**部分包含以下设置：</span><span class="sxs-lookup"><span data-stu-id="e37f3-197">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="e37f3-198">**IPD**：设置瞳孔间距 (IPD)，它是在用户直视前方时两个瞳孔中心之间的距离，以毫米为单位。</span><span class="sxs-lookup"><span data-stu-id="e37f3-198">**IPD**: Sets the interpupillary distance (IPD), which is the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="e37f3-199">该设置将立即生效。</span><span class="sxs-lookup"><span data-stu-id="e37f3-199">The setting takes effect immediately.</span></span> <span data-ttu-id="e37f3-200">在设置你的设备时，会自动计算该默认值。</span><span class="sxs-lookup"><span data-stu-id="e37f3-200">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="e37f3-201">**设备名称**：为 HoloLens 指定一个名称。</span><span class="sxs-lookup"><span data-stu-id="e37f3-201">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="e37f3-202">更改此值后，必须重新启动设备才能使该值生效。</span><span class="sxs-lookup"><span data-stu-id="e37f3-202">You must reboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="e37f3-203">单击“保存”后，对话框将询问是要立即重新启动还是稍后重新启动设备。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-203">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="e37f3-204">**睡眠设置**：设置当设备已接上电源并使用电池时进入睡眠状态之前要等待的时长。</span><span class="sxs-lookup"><span data-stu-id="e37f3-204">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="e37f3-205">3D 视图</span><span class="sxs-lookup"><span data-stu-id="e37f3-205">3D View</span></span>

<span data-ttu-id="e37f3-206">![Microsoft HoloLens 上 Windows 设备门户中的“3D 视图”页](images/3dview-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-206">![3D View page in Windows Device Portal on Microsoft HoloLens](images/3dview-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-207">*Microsoft HoloLens 上 Windows 设备门户中的“3D 视图”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-207">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-208">使用“3D 视图”页面可查看 HoloLens 感知周围环境的方式。</span><span class="sxs-lookup"><span data-stu-id="e37f3-208">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="e37f3-209">使用鼠标即可导览该视图：</span><span class="sxs-lookup"><span data-stu-id="e37f3-209">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="e37f3-210">旋转：单击左键并移动鼠标；</span><span class="sxs-lookup"><span data-stu-id="e37f3-210">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="e37f3-211">平移：单击右键并移动鼠标；</span><span class="sxs-lookup"><span data-stu-id="e37f3-211">Pan: right click + mouse;</span></span>
* <span data-ttu-id="e37f3-212">缩放：滑动鼠标滚轮。</span><span class="sxs-lookup"><span data-stu-id="e37f3-212">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="e37f3-213">**跟踪选项**</span><span class="sxs-lookup"><span data-stu-id="e37f3-213">**Tracking options**</span></span>
   * <span data-ttu-id="e37f3-214">通过选中“强制视觉跟踪”可打开持续视觉跟踪。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-214">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="e37f3-215">“暂停”会停止视觉跟踪。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-215">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="e37f3-216">**视图选项**：设置 3D 视图中的选项：</span><span class="sxs-lookup"><span data-stu-id="e37f3-216">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="e37f3-217">**跟踪**：指示视觉跟踪是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="e37f3-217">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="e37f3-218">**显示地面**：显示方格形式的地平面。</span><span class="sxs-lookup"><span data-stu-id="e37f3-218">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="e37f3-219">**显示锥体**：显示视锥。</span><span class="sxs-lookup"><span data-stu-id="e37f3-219">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="e37f3-220">**显示防抖动平面**：显示 HoloLens 用于稳定动作的平面。</span><span class="sxs-lookup"><span data-stu-id="e37f3-220">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="e37f3-221">**显示网格**：显示代表周围环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="e37f3-221">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="e37f3-222">**显示空间定位点**：显示活动应用的空间定位点。</span><span class="sxs-lookup"><span data-stu-id="e37f3-222">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="e37f3-223">必须单击“更新”按钮才能获取和刷新定位点。</span><span class="sxs-lookup"><span data-stu-id="e37f3-223">You must click the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="e37f3-224">**显示细节**：显示手的位置、头部旋转四元数，以及设备原点矢量的实时变化。</span><span class="sxs-lookup"><span data-stu-id="e37f3-224">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="e37f3-225">**全屏按钮**：以全屏模式显示 3D 视图。</span><span class="sxs-lookup"><span data-stu-id="e37f3-225">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="e37f3-226">按 ESC 键可退出全屏视图。</span><span class="sxs-lookup"><span data-stu-id="e37f3-226">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="e37f3-227">**图面重构**：单击或敲击“更新”可显示设备的最新空间映射网格。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-227">**Surface reconstruction**: Click or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="e37f3-228">完成整个过程可能需要一些时间（但最多只需几秒钟）。</span><span class="sxs-lookup"><span data-stu-id="e37f3-228">A full pass may take some time to complete (up to a few seconds).</span></span> <span data-ttu-id="e37f3-229">在 3D 视图中，网格不会自动更新，必须手动单击“更新”才能获取设备的最新网格。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-229">The mesh does not update automatically in the 3D view, and you must manually click **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="e37f3-230">单击“保存”可在电脑上将当前的空间映射网格保存为 obj 文件。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-230">Click **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="e37f3-231">**空间定位点**：单击“更新”可显示或更新活动应用的空间定位点。</span><span class="sxs-lookup"><span data-stu-id="e37f3-231">**Spatial anchors**: Click Update to display or update the spatial anchors for the active app.</span></span>

### <a name="mixed-reality-capture"></a><span data-ttu-id="e37f3-232">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="e37f3-232">Mixed Reality Capture</span></span>

<span data-ttu-id="e37f3-233">![Microsoft HoloLens 上 Windows 设备门户中的“混合现实捕获”页](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-233">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-234">*Microsoft HoloLens 上 Windows 设备门户中的“混合现实捕获”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-234">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-235">使用“混合现实捕获”页面可保存 HoloLens 中的媒体流。</span><span class="sxs-lookup"><span data-stu-id="e37f3-235">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="e37f3-236">**设置**：通过检查以下设置来控制捕获的媒体流：</span><span class="sxs-lookup"><span data-stu-id="e37f3-236">**Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="e37f3-237">**全息影像**：捕获视频流中的全息内容。</span><span class="sxs-lookup"><span data-stu-id="e37f3-237">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="e37f3-238">呈现全息图时使用的是单声道，而不是立体声。</span><span class="sxs-lookup"><span data-stu-id="e37f3-238">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="e37f3-239">**PV 相机**：捕获照片/视频相机中的视频流。</span><span class="sxs-lookup"><span data-stu-id="e37f3-239">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="e37f3-240">**麦克风音频**：捕获麦克风阵列中的音频。</span><span class="sxs-lookup"><span data-stu-id="e37f3-240">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="e37f3-241">**应用音频**：捕获当前正在运行的应用中的音频。</span><span class="sxs-lookup"><span data-stu-id="e37f3-241">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="e37f3-242">**从相机渲染**：从照片/视频相机的角度对齐捕获内容，前提是[正在运行的应用支持此功能](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)（仅限 HoloLens 2）。</span><span class="sxs-lookup"><span data-stu-id="e37f3-242">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="e37f3-243">**实时预览质量**：选择用于实时预览的屏幕分辨率、帧速率和流处理速率。</span><span class="sxs-lookup"><span data-stu-id="e37f3-243">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="e37f3-244">单击或敲击“实时预览”按钮可显示捕获流。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-244">Click or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="e37f3-245">“停止实时预览”会停止捕获流。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-245">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="e37f3-246">单击或敲击“录制”可使用指定的设置开始录制混合现实流。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-246">Click or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="e37f3-247">“停止录制”会结束录制，并保存录制内容。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-247">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="e37f3-248">单击或敲击“拍摄照片”可从捕获流中捕获静止图像。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-248">Click or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="e37f3-249">**视频和照片**：显示在设备上捕获的视频和照片列表。</span><span class="sxs-lookup"><span data-stu-id="e37f3-249">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="e37f3-250">[同步 MRC 存在限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)：</span><span class="sxs-lookup"><span data-stu-id="e37f3-250">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="e37f3-251">如果当 Windows 设备门户正在录制视频时某个应用尝试访问照片/视频相机，则视频录制将会停止。</span><span class="sxs-lookup"><span data-stu-id="e37f3-251">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="e37f3-252">如果应用以 SharedReadOnly 模式访问照片/视频相机，HoloLens 2 将不会停止视频录制。</span><span class="sxs-lookup"><span data-stu-id="e37f3-252">HoloLens 2 will not stop recording video if the app accesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="e37f3-253">如果应用正在使用照片/视频相机，则 Windows 设备门户可以拍摄照片或录制视频。</span><span class="sxs-lookup"><span data-stu-id="e37f3-253">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="e37f3-254">实时传送视频流：</span><span class="sxs-lookup"><span data-stu-id="e37f3-254">Live streaming:</span></span>
>   * <span data-ttu-id="e37f3-255">从 Windows 设备门户实时传送视频流时，HoloLens（第一代）会阻止应用访问照片/视频相机。</span><span class="sxs-lookup"><span data-stu-id="e37f3-255">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="e37f3-256">如果应用正在使用照片/视频相机，则 HoloLens（第一代）将无法实时传送视频流。</span><span class="sxs-lookup"><span data-stu-id="e37f3-256">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="e37f3-257">当应用尝试以 ExclusiveControl 模式访问照片/视频相机时，HoloLens 2 会自动停止实时传送视频流。</span><span class="sxs-lookup"><span data-stu-id="e37f3-257">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="e37f3-258">当应用正在使用 PV 相机时，HoloLens 2 可以启动实时传送视频流。</span><span class="sxs-lookup"><span data-stu-id="e37f3-258">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="e37f3-259">性能跟踪</span><span class="sxs-lookup"><span data-stu-id="e37f3-259">Performance Tracing</span></span>

<span data-ttu-id="e37f3-260">![Microsoft HoloLens 上 Windows 设备门户中的“性能跟踪”页](images/windows-device-portal-performance-tracing-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-260">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-261">*Microsoft HoloLens 上 Windows 设备门户中的“性能跟踪”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-261">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-262">从 HoloLens 中捕获 [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) 跟踪。</span><span class="sxs-lookup"><span data-stu-id="e37f3-262">Capture [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="e37f3-263">**可用配置文件**：从下拉列表中选择 WPR 配置文件，然后单击或敲击“开始”以开始跟踪。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-263">**Available profiles**: Select the WPR profile from the dropdown, and click or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="e37f3-264">**自定义配置文件**：单击或敲击“浏览”以从电脑中选择 WPR 配置文件。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-264">**Custom profiles**: Click or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="e37f3-265">单击或敲击“上传并启动”以开始跟踪。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-265">Click or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="e37f3-266">若要停止跟踪，请单击“停止”链接。</span><span class="sxs-lookup"><span data-stu-id="e37f3-266">To stop the trace, click the stop link.</span></span> <span data-ttu-id="e37f3-267">请保持打开此页，直到跟踪文件完成下载。</span><span class="sxs-lookup"><span data-stu-id="e37f3-267">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="e37f3-268">可以打开捕获的 ETL 文件以供在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中进行分析。</span><span class="sxs-lookup"><span data-stu-id="e37f3-268">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).</span></span>

### <a name="processes"></a><span data-ttu-id="e37f3-269">进程</span><span class="sxs-lookup"><span data-stu-id="e37f3-269">Processes</span></span>

<span data-ttu-id="e37f3-270">![Microsoft HoloLens 上 Windows 设备门户中的“进程”页](images/windows-device-portal-running-processes-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-270">![Processes page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-271">*Microsoft HoloLens 上 Windows 设备门户中的“进程”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-271">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-272">显示有关当前正在运行的进程的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e37f3-272">Shows details about currently running processes.</span></span> <span data-ttu-id="e37f3-273">这包括应用和系统进程。</span><span class="sxs-lookup"><span data-stu-id="e37f3-273">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="e37f3-274">系统性能</span><span class="sxs-lookup"><span data-stu-id="e37f3-274">System Performance</span></span>

<span data-ttu-id="e37f3-275">![Microsoft HoloLens 上 Windows 设备门户中的“系统性能”页](images/windows-device-portal-system-performance-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-275">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-276">*Microsoft HoloLens 上 Windows 设备门户中的“系统性能”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-276">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-277">显示系统诊断信息的实时图形，如电源使用情况、帧速率和 CPU 负载。</span><span class="sxs-lookup"><span data-stu-id="e37f3-277">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="e37f3-278">可用的指标如下所示：</span><span class="sxs-lookup"><span data-stu-id="e37f3-278">These are the available metrics:</span></span>
* <span data-ttu-id="e37f3-279">**SoC 电源**：片上系统的瞬时用电量，为一分钟平均值</span><span class="sxs-lookup"><span data-stu-id="e37f3-279">**SoC power**: Instantaneous system-on-chip power utilization, averaged over one minute</span></span>
* <span data-ttu-id="e37f3-280">**系统电源**：系统的瞬时用电量，为一分钟平均值</span><span class="sxs-lookup"><span data-stu-id="e37f3-280">**System power**: Instantaneous system power utilization, averaged over one minute</span></span>
* <span data-ttu-id="e37f3-281">**帧速率**：每秒帧数、每秒丢失的垂直消隐数和连续丢失的垂直消隐数</span><span class="sxs-lookup"><span data-stu-id="e37f3-281">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="e37f3-282">**GPU**：GPU 引擎利用率、总可用量的百分比</span><span class="sxs-lookup"><span data-stu-id="e37f3-282">**GPU**: GPU engine utilization, percent of total available</span></span>
* <span data-ttu-id="e37f3-283">**CPU**：总可用量的百分比</span><span class="sxs-lookup"><span data-stu-id="e37f3-283">**CPU**: percent of total available</span></span>
* <span data-ttu-id="e37f3-284">**I/O**：读取和写入次数</span><span class="sxs-lookup"><span data-stu-id="e37f3-284">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="e37f3-285">**网络**：接收和发送数据量</span><span class="sxs-lookup"><span data-stu-id="e37f3-285">**Network**: Received and sent</span></span>
* <span data-ttu-id="e37f3-286">**内存**：总计、已用、已提交、已分页和未分页</span><span class="sxs-lookup"><span data-stu-id="e37f3-286">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="e37f3-287">“应用”</span><span class="sxs-lookup"><span data-stu-id="e37f3-287">Apps</span></span>

<span data-ttu-id="e37f3-288">![Microsoft HoloLens 上 Windows 设备门户中的“应用”页](images/windows-device-portal-apps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-288">![Apps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-289">*Microsoft HoloLens 上 Windows 设备门户中的“应用”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-289">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-290">管理 HoloLens 上安装的应用。</span><span class="sxs-lookup"><span data-stu-id="e37f3-290">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="e37f3-291">**已安装的应用**：删除和启动应用。</span><span class="sxs-lookup"><span data-stu-id="e37f3-291">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="e37f3-292">**正在运行的应用**：列出当前正在运行的应用。</span><span class="sxs-lookup"><span data-stu-id="e37f3-292">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="e37f3-293">**安装应用**：从计算机/网络上的文件夹中选择应用包进行安装。</span><span class="sxs-lookup"><span data-stu-id="e37f3-293">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="e37f3-294">**依赖项**：为要安装的应用添加依赖项。</span><span class="sxs-lookup"><span data-stu-id="e37f3-294">**Dependency**: Add dependencies for the app you are going to install.</span></span>
* <span data-ttu-id="e37f3-295">**部署**：将所选应用和依赖项部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e37f3-295">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="e37f3-296">应用故障转储</span><span class="sxs-lookup"><span data-stu-id="e37f3-296">App Crash Dumps</span></span>

<span data-ttu-id="e37f3-297">![Microsoft HoloLens 上 Windows 设备门户中的“应用故障转储”页](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-297">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-298">*Microsoft HoloLens 上 Windows 设备门户中的“应用故障转储”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-298">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-299">此页面允许你收集旁加载应用的故障转储。</span><span class="sxs-lookup"><span data-stu-id="e37f3-299">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="e37f3-300">对于要收集其故障转储的每个应用，请选中对应的“已启用故障转储”复选框。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-300">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="e37f3-301">返回到此页面可收集故障转储。</span><span class="sxs-lookup"><span data-stu-id="e37f3-301">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="e37f3-302">可[在 Visual Studio 中打开转储文件进行调试](https://msdn.microsoft.com/library/d5zhxt22.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e37f3-302">Dump files can be [opened in Visual Studio for debugging](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="e37f3-303">文件资源浏览器</span><span class="sxs-lookup"><span data-stu-id="e37f3-303">File Explorer</span></span>

<span data-ttu-id="e37f3-304">![Microsoft HoloLens 上 Windows 设备门户中的“文件资源浏览器”页](images/fileexplorer-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-304">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/fileexplorer-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-305">*Microsoft HoloLens 上 Windows 设备门户中的“文件资源浏览器”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-305">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-306">使用文件资源管理器可以浏览、上传和下载文件。</span><span class="sxs-lookup"><span data-stu-id="e37f3-306">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="e37f3-307">对于从 Visual Studio 或设备门户部署的应用，可以处理“文档”文件夹、“图片”文件夹和本地存储文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="e37f3-307">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="e37f3-308">展台模式</span><span class="sxs-lookup"><span data-stu-id="e37f3-308">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="e37f3-309">展台模式仅适用于 [Microsoft HoloLens Commercial Suite](commercial-features.md)。</span><span class="sxs-lookup"><span data-stu-id="e37f3-309">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](commercial-features.md).</span></span>

<span data-ttu-id="e37f3-310">有关如何通过 Windows 设备门户启用展台模式的最新说明，请查看 Windows IT 专业人员中心内的[在展台模式下设置 HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 一文。</span><span class="sxs-lookup"><span data-stu-id="e37f3-310">Check the [Set up HoloLens in kiosk mode](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="e37f3-311">日志记录</span><span class="sxs-lookup"><span data-stu-id="e37f3-311">Logging</span></span>

<span data-ttu-id="e37f3-312">![Microsoft HoloLens 上 Windows 设备门户中的“日志记录”页](images/windows-device-portal-logging-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-312">![Logging page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-313">*Microsoft HoloLens 上 Windows 设备门户中的“日志记录”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-313">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-314">管理 HoloLens 上的实时 Windows 事件跟踪 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="e37f3-314">Manages realtime Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="e37f3-315">选中“隐藏提供程序”以仅显示“事件”列表。  </span><span class="sxs-lookup"><span data-stu-id="e37f3-315">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="e37f3-316">**已注册的提供程序**：选择 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="e37f3-316">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="e37f3-317">跟踪级别是以下值之一：</span><span class="sxs-lookup"><span data-stu-id="e37f3-317">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="e37f3-318">异常退出或终止</span><span class="sxs-lookup"><span data-stu-id="e37f3-318">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="e37f3-319">严重错误</span><span class="sxs-lookup"><span data-stu-id="e37f3-319">Severe errors</span></span>
   3. <span data-ttu-id="e37f3-320">警告</span><span class="sxs-lookup"><span data-stu-id="e37f3-320">Warnings</span></span>
   4. <span data-ttu-id="e37f3-321">非错误警告</span><span class="sxs-lookup"><span data-stu-id="e37f3-321">Non-error warnings</span></span>

<span data-ttu-id="e37f3-322">单击或敲击“启用”以开始跟踪。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-322">Click or tap **Enable** to start tracing.</span></span> <span data-ttu-id="e37f3-323">提供程序将添加到“已启用的提供程序”下拉列表。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-323">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="e37f3-324">**自定义提供程序**：选择自定义 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="e37f3-324">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="e37f3-325">根据其 GUDI 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="e37f3-325">Identify the provider by its GUID.</span></span> <span data-ttu-id="e37f3-326">不要在 GUID 中包含括号。</span><span class="sxs-lookup"><span data-stu-id="e37f3-326">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="e37f3-327">**已启用的提供程序**：列出已启用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="e37f3-327">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="e37f3-328">从下拉列表中选择一个提供程序，然后单击或敲击“禁用”可停止跟踪。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-328">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="e37f3-329">单击或敲击“全部停止”会暂停所有跟踪。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-329">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="e37f3-330">**提供程序历史记录**：显示已在当前会话期间启用的 ETW 提供程序。</span><span class="sxs-lookup"><span data-stu-id="e37f3-330">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="e37f3-331">单击或敲击“启用”可激活已禁用的提供程序。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-331">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="e37f3-332">单击或敲击“清除”可清除历史记录。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-332">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="e37f3-333">**事件**：以表格格式列出来自选定提供程序的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="e37f3-333">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="e37f3-334">此表将实时更新。</span><span class="sxs-lookup"><span data-stu-id="e37f3-334">This table is updated in real time.</span></span> <span data-ttu-id="e37f3-335">在该表格下方，单击“清除”按钮可删除其中的所有 ETW 事件。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-335">Beneath the table, click the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="e37f3-336">这不会禁用任何提供程序。</span><span class="sxs-lookup"><span data-stu-id="e37f3-336">This does not disable any providers.</span></span> <span data-ttu-id="e37f3-337">可以单击“保存到文件”以将当前收集的 ETW 事件本地导出到 CSV 文件。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-337">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="e37f3-338">**筛选器**：用于按 ID、关键字、级别、提供程序名称、任务名称或文本筛选收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="e37f3-338">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="e37f3-339">可将多个条件组合在一起：</span><span class="sxs-lookup"><span data-stu-id="e37f3-339">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="e37f3-340">对于应用到同一属性的条件，将显示可满足其中任何一个条件的事件。</span><span class="sxs-lookup"><span data-stu-id="e37f3-340">For criteria applying to the same property, events that can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="e37f3-341">对于应用到不同属性的条件，事件必须满足所有条件</span><span class="sxs-lookup"><span data-stu-id="e37f3-341">For criteria applying to a different property, events must satisfy all of the criteria</span></span>

<span data-ttu-id="e37f3-342">例如，可以指定条件 *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span><span class="sxs-lookup"><span data-stu-id="e37f3-342">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="e37f3-343">模拟</span><span class="sxs-lookup"><span data-stu-id="e37f3-343">Simulation</span></span>

<span data-ttu-id="e37f3-344">![Microsoft HoloLens 上 Windows 设备门户中的“模拟”页](images/windows-device-portal-simulation-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-344">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-345">*Microsoft HoloLens 上 Windows 设备门户中的“模拟”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-345">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-346">允许你记录和播放用于测试的输入数据。</span><span class="sxs-lookup"><span data-stu-id="e37f3-346">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="e37f3-347">**捕获房间**：用于下载模拟房间文件，该文件包含用户周围环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="e37f3-347">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="e37f3-348">为该房间命名，然后单击“捕获”以在电脑上将该数据保存为 .xef 文件。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-348">Name the room and then click **Capture** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="e37f3-349">此房间文件可以加载到 HoloLens 仿真器中。</span><span class="sxs-lookup"><span data-stu-id="e37f3-349">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="e37f3-350">**录制**：选中要录制的流、为录制内容命名，然后单击或敲击“录制”开始录制。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-350">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="e37f3-351">使用 HoloLens 执行操作，然后单击“停止”在电脑上将数据保存为 .xef 文件。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-351">Perform actions with your HoloLens and then click **Stop** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="e37f3-352">可以在 HoloLens 仿真器或设备上加载此文件。</span><span class="sxs-lookup"><span data-stu-id="e37f3-352">This file can be loaded on the HoloLens emulator or device.</span></span>
* <span data-ttu-id="e37f3-353">**播放**：单击或敲击“上传录制内容”可从电脑中选择 xef 文件，然后将数据发送到 HoloLens。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-353">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="e37f3-354">**控制模式**：在 HoloLens 上，从下拉列表中选择“默认”或“模拟”，然后单击或敲击“设置”按钮选中该模式。   </span><span class="sxs-lookup"><span data-stu-id="e37f3-354">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="e37f3-355">相反，选择“模拟”会禁用 HoloLens 上的真实传感器，并使用已上载的模拟数据。</span><span class="sxs-lookup"><span data-stu-id="e37f3-355">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="e37f3-356">如果切换到“模拟”，HoloLens 将不会响应真实用户，除非切换回“默认”。</span><span class="sxs-lookup"><span data-stu-id="e37f3-356">If you switch to "Simulation", your HoloLens will not respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="e37f3-357">网络</span><span class="sxs-lookup"><span data-stu-id="e37f3-357">Networking</span></span>

<span data-ttu-id="e37f3-358">![Microsoft HoloLens 上 Windows 设备门户中的“网络”页](images/windows-device-portal-networking-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-358">![Networking page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-359">*Microsoft HoloLens 上 Windows 设备门户中的“网络”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-359">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-360">管理 HoloLens 上的 Wi-Fi 连接。</span><span class="sxs-lookup"><span data-stu-id="e37f3-360">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="e37f3-361">**WiFi 适配器**：使用下拉控件选择 Wi-Fi 适配器和配置文件。</span><span class="sxs-lookup"><span data-stu-id="e37f3-361">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="e37f3-362">单击或敲击“连接”以使用选定的适配器。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-362">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="e37f3-363">**可用网络**：列出 HoloLens 可连接到的 Wi-Fi 网络。</span><span class="sxs-lookup"><span data-stu-id="e37f3-363">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="e37f3-364">单击或敲击“刷新”可更新列表。 </span><span class="sxs-lookup"><span data-stu-id="e37f3-364">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="e37f3-365">**IP 配置**：显示网络连接的 IP 地址和其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="e37f3-365">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="e37f3-366">虚拟输入</span><span class="sxs-lookup"><span data-stu-id="e37f3-366">Virtual Input</span></span>

<span data-ttu-id="e37f3-367">![Microsoft HoloLens 上 Windows 设备门户中的“虚拟输入”页](images/windows-device-portal-virtual-input-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e37f3-367">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)</span></span><br>
<span data-ttu-id="e37f3-368">*Microsoft HoloLens 上 Windows 设备门户中的“虚拟输入”页*</span><span class="sxs-lookup"><span data-stu-id="e37f3-368">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e37f3-369">将键盘输入从远程计算机发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e37f3-369">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="e37f3-370">单击或敲击**虚拟键盘**下的区域可将键击发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e37f3-370">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="e37f3-371">在“输入文本”文本框中键入内容，然后单击或敲击“发送”可将键击发送到活动应用。  </span><span class="sxs-lookup"><span data-stu-id="e37f3-371">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="e37f3-372">设备门户 REST API</span><span class="sxs-lookup"><span data-stu-id="e37f3-372">Device Portal REST API's</span></span>

<span data-ttu-id="e37f3-373">设备门户中的所有内容都是基于 [REST API](device-portal-api-reference.md) 创建的，你可以选择性地使用这些 API 来访问数据和以编程方式控制设备。</span><span class="sxs-lookup"><span data-stu-id="e37f3-373">Everything in the device portal is built on top of [REST API's](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>
