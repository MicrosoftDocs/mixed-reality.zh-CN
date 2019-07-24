---
title: 使用 Windows 设备门户
description: 通过用于 HoloLens 的 Windows 设备门户, 你可以通过 Wi-fi 或 USB 远程配置和管理你的设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包含许多工具, 可帮助你管理 HoloLens 并调试和优化你的应用程序。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 设备门户、HoloLens
ms.openlocfilehash: 79a4a1f99125028fcaf71e185eb00093aa8c742f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694586"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="00e68-106">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="00e68-106">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="00e68-107">功能</span><span class="sxs-lookup"><span data-stu-id="00e68-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="00e68-108"><a href="hololens-hardware-details.md">HoloLens（第一代）</a></span><span class="sxs-lookup"><span data-stu-id="00e68-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="00e68-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="00e68-109">HoloLens 2</span></span></th><th style="width:150px"><span data-ttu-id="00e68-110"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="00e68-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="00e68-111">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="00e68-111">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="00e68-112">✔️</span><span class="sxs-lookup"><span data-stu-id="00e68-112">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="00e68-113">✔️</span><span class="sxs-lookup"><span data-stu-id="00e68-113">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="00e68-114">通过用于 HoloLens 的 Windows 设备门户, 你可以通过 Wi-fi 或 USB 远程配置和管理你的设备。</span><span class="sxs-lookup"><span data-stu-id="00e68-114">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="00e68-115">Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。</span><span class="sxs-lookup"><span data-stu-id="00e68-115">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="00e68-116">设备门户包含许多工具, 可帮助你管理 HoloLens 并调试和优化你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="00e68-116">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="00e68-117">本文档专门介绍适用于 HoloLens 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="00e68-117">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="00e68-118">若要使用适用于桌面的 Windows 设备门户 (包括 Windows Mixed Reality), 请参阅[Windows 设备门户概述](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="00e68-118">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="00e68-119">将 HoloLens 设置为使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="00e68-119">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="00e68-120">打开 HoloLens 的电源，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="00e68-120">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="00e68-121">执行[绽放](gestures.md#bloom)手势来启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="00e68-121">Perform the [bloom](gestures.md#bloom) gesture to launch the main menu.</span></span>
3. <span data-ttu-id="00e68-122">查看 "**设置**" 磁贴, 然后执行 "[空气分流](gestures.md#air-tap)" 手势。</span><span class="sxs-lookup"><span data-stu-id="00e68-122">Gaze at the **Settings** tile and perform the [air-tap](gestures.md#air-tap) gesture.</span></span> <span data-ttu-id="00e68-123">再执行一次点击, 将应用放在环境中。</span><span class="sxs-lookup"><span data-stu-id="00e68-123">Perform a second air-tap to place the app in your environment.</span></span> <span data-ttu-id="00e68-124">在放置“设置”应用后，将启动该应用。</span><span class="sxs-lookup"><span data-stu-id="00e68-124">The Settings app will launch after you place it.</span></span>
4. <span data-ttu-id="00e68-125">选择“更新”菜单项。</span><span class="sxs-lookup"><span data-stu-id="00e68-125">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="00e68-126">选择“面向开发人员”菜单项。</span><span class="sxs-lookup"><span data-stu-id="00e68-126">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="00e68-127">启用“开发人员模式”。</span><span class="sxs-lookup"><span data-stu-id="00e68-127">Enable **Developer Mode**.</span></span>
7. <span data-ttu-id="00e68-128">[向下滚动](gestures.md#composite-gestures)并启用**设备门户**。</span><span class="sxs-lookup"><span data-stu-id="00e68-128">[Scroll down](gestures.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="00e68-129">如果要设置 Windows 设备门户, 以便可以通过 USB 或 Wi-fi 将应用部署到此 HoloLens, 请单击 "**配对**" 以[生成配对 PIN](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="00e68-129">If you are setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, click **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="00e68-130">在第一次部署过程中, 将 "设置" 应用保留在 "PIN" 弹出窗口中, 直到输入到 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="00e68-130">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

   ![在 Windows 全息版的设置应用中启用开发人员模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="00e68-132">通过 Wi-fi 连接</span><span class="sxs-lookup"><span data-stu-id="00e68-132">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="00e68-133">[将 HoloLens 连接到 wi-fi](connecting-to-wi-fi-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="00e68-133">[Connect your HoloLens to Wi-Fi](connecting-to-wi-fi-on-hololens.md).</span></span>
2. <span data-ttu-id="00e68-134">查找设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="00e68-134">Look up your device's IP address.</span></span>
   * <span data-ttu-id="00e68-135">在 "**设置" > Network & > > Internet**"下的" 设置 "中找到设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="00e68-135">Find the IP address on the device under **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
3. <span data-ttu-id="00e68-136">在电脑上的 web 浏览器中转到 https://< YOUR_HOLOLENS_IP_ADDRESS ></span><span class="sxs-lookup"><span data-stu-id="00e68-136">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="00e68-137">浏览器将显示以下消息:"此网站的安全证书有问题"。</span><span class="sxs-lookup"><span data-stu-id="00e68-137">The browser will display the following message: "There’s a problem with this website’s security certificate".</span></span> <span data-ttu-id="00e68-138">由于颁发给 Device Portal 的证书是测试证书，因此会显示上述消息。</span><span class="sxs-lookup"><span data-stu-id="00e68-138">This happens because the certificate which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="00e68-139">你可以暂时忽略此证书错误并继续。</span><span class="sxs-lookup"><span data-stu-id="00e68-139">You can ignore this certificate error for now and proceed.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="00e68-140">通过 USB 连接</span><span class="sxs-lookup"><span data-stu-id="00e68-140">Connecting over USB</span></span>

1. <span data-ttu-id="00e68-141">[安装这些工具](install-the-tools.md), 确保你的 Visual Studio Update 1 具有安装在你的电脑上的 Windows 10 开发人员工具。</span><span class="sxs-lookup"><span data-stu-id="00e68-141">[Install the tools](install-the-tools.md) to make sure you have Visual Studio Update 1 with the Windows 10 developer tools installed on your PC.</span></span> <span data-ttu-id="00e68-142">这支持 USB 连接。</span><span class="sxs-lookup"><span data-stu-id="00e68-142">This enables USB connectivity.</span></span>
2. <span data-ttu-id="00e68-143">使用微型 USB 电缆将 HoloLens 连接到电脑。</span><span class="sxs-lookup"><span data-stu-id="00e68-143">Connect your HoloLens to your PC with a micro-USB cable.</span></span>
3. <span data-ttu-id="00e68-144">通过电脑上的 Web 浏览器，转到 http://127.0.0.1:10080 。</span><span class="sxs-lookup"><span data-stu-id="00e68-144">From a web browser on your PC, go to http://127.0.0.1:10080.</span></span>

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="00e68-145">连接到模拟器</span><span class="sxs-lookup"><span data-stu-id="00e68-145">Connecting to an emulator</span></span>

<span data-ttu-id="00e68-146">也可以将 Device Portal 与仿真器结合使用。</span><span class="sxs-lookup"><span data-stu-id="00e68-146">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="00e68-147">若要连接到设备门户, 请使用[工具栏](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="00e68-147">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="00e68-148">单击此图标：![打开设备门户图标](images/emulator-deviceportal.png) **打开设备门户**:在仿真器中打开 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="00e68-148">Click on this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="00e68-149">创建用户名和密码</span><span class="sxs-lookup"><span data-stu-id="00e68-149">Creating a Username and Password</span></span>

<span data-ttu-id="00e68-150">![设置对 Windows 设备门户的访问](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-150">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-151">*设置对 Windows 设备门户的访问*</span><span class="sxs-lookup"><span data-stu-id="00e68-151">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="00e68-152">首次连接到 HoloLens 上的 Device Portal 时，需要创建用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="00e68-152">The first time you connect to the Device Portal on your HoloLens, you will need to create a username and password.</span></span>
1. <span data-ttu-id="00e68-153">在电脑上的 Web 浏览器中，输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="00e68-153">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="00e68-154">将打开“设置访问”页面。</span><span class="sxs-lookup"><span data-stu-id="00e68-154">The Set up access page opens.</span></span>
2. <span data-ttu-id="00e68-155">单击或点击 "**请求 pin** ", 并查看 HoloLens 显示以获取生成的 pin。</span><span class="sxs-lookup"><span data-stu-id="00e68-155">Click or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="00e68-156">在 "设备" 文本框中**显示的 pin**中输入 pin。</span><span class="sxs-lookup"><span data-stu-id="00e68-156">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="00e68-157">输入将用于连接到 Device Portal 的用户名。</span><span class="sxs-lookup"><span data-stu-id="00e68-157">Enter the user name you will use to connect to the Device Portal.</span></span> <span data-ttu-id="00e68-158">无需使用 Microsoft 帐户 (MSA) 名称或域名作为用户名。</span><span class="sxs-lookup"><span data-stu-id="00e68-158">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="00e68-159">输入密码并进行确认。</span><span class="sxs-lookup"><span data-stu-id="00e68-159">Enter a password and confirm it.</span></span> <span data-ttu-id="00e68-160">密码长度必须至少为七个字符。</span><span class="sxs-lookup"><span data-stu-id="00e68-160">The password must be at least seven characters in length.</span></span> <span data-ttu-id="00e68-161">无需使用 MSA 密码或域密码作为密码。</span><span class="sxs-lookup"><span data-stu-id="00e68-161">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="00e68-162">单击 "**配对**" 以连接到 HoloLens 上的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="00e68-162">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="00e68-163">如果你想要随时更改此用户名或密码, 可以通过以下方式来重复此过程: 访问设备安全页: 通过导航到: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm。</span><span class="sxs-lookup"><span data-stu-id="00e68-163">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="00e68-164">安全证书</span><span class="sxs-lookup"><span data-stu-id="00e68-164">Security certificate</span></span>

<span data-ttu-id="00e68-165">如果你在浏览器中看到“证书错误”，可以通过创建与该设备的信任关系来修复该错误。</span><span class="sxs-lookup"><span data-stu-id="00e68-165">If you are see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="00e68-166">每个 HoloLens 会生成唯一的自签名证书以供其 SSL 连接使用。</span><span class="sxs-lookup"><span data-stu-id="00e68-166">Each HoloLens generates a unique self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="00e68-167">默认情况下，此证书不受电脑的 Web 浏览器信任，因此你可能会看到“证书错误”。</span><span class="sxs-lookup"><span data-stu-id="00e68-167">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="00e68-168">通过从你的 HoloLens 下载此证书（借助 USB 或信任的 WLAN 网络）并在你的电脑上信任该证书，可以安全地连接到设备。</span><span class="sxs-lookup"><span data-stu-id="00e68-168">By downloading this certificate from your HoloLens (over USB or a Wi-Fi network you trust) and trusting it on your PC, you can securely connect to your device.</span></span>
1. <span data-ttu-id="00e68-169">**请确保使用的是安全网络 (USB 或你信任的 Wi-fi 网络)。**</span><span class="sxs-lookup"><span data-stu-id="00e68-169">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="00e68-170">从设备门户上的 "安全性" 页下载此设备的证书。</span><span class="sxs-lookup"><span data-stu-id="00e68-170">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="00e68-171">导航到: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="00e68-171">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
3. <span data-ttu-id="00e68-172">在电脑上的 "受信任的根证书颁发机构" 存储中安装证书。</span><span class="sxs-lookup"><span data-stu-id="00e68-172">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="00e68-173">在 Windows 菜单中键入:管理计算机证书并启动小程序。</span><span class="sxs-lookup"><span data-stu-id="00e68-173">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="00e68-174">展开 "**受信任的根证书颁发机构**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="00e68-174">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="00e68-175">单击 "**证书**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="00e68-175">Click on the **Certificates** folder.</span></span>
   * <span data-ttu-id="00e68-176">从 "操作" 菜单中, 选择:所有任务 > 导入 。</span><span class="sxs-lookup"><span data-stu-id="00e68-176">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="00e68-177">使用从 Device Portal 下载的证书文件，完成“证书导入向导”。</span><span class="sxs-lookup"><span data-stu-id="00e68-177">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="00e68-178">重新启动浏览器。</span><span class="sxs-lookup"><span data-stu-id="00e68-178">Restart the browser.</span></span>

## <a name="device-portal-pages"></a><span data-ttu-id="00e68-179">Device Portal 页面</span><span class="sxs-lookup"><span data-stu-id="00e68-179">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="00e68-180">主页</span><span class="sxs-lookup"><span data-stu-id="00e68-180">Home</span></span>

<span data-ttu-id="00e68-181">![Microsoft HoloLens 上的 Windows 设备门户主页](images/windows-device-portal-home-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-181">![Windows Device Portal home page on Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-182">*Microsoft HoloLens 上的 Windows 设备门户主页*</span><span class="sxs-lookup"><span data-stu-id="00e68-182">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-183">Device Portal 会话从主页开始。</span><span class="sxs-lookup"><span data-stu-id="00e68-183">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="00e68-184">可从主页的左侧导航栏访问其他页面。</span><span class="sxs-lookup"><span data-stu-id="00e68-184">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="00e68-185">主页顶部的工具栏提供对常用状态和功能的访问。</span><span class="sxs-lookup"><span data-stu-id="00e68-185">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="00e68-186">**联机**:指示设备是否已连接到 Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="00e68-186">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="00e68-187">**关闭**:关闭设备。</span><span class="sxs-lookup"><span data-stu-id="00e68-187">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="00e68-188">**重新启动**:在设备上循环电源。</span><span class="sxs-lookup"><span data-stu-id="00e68-188">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="00e68-189">**安全**：打开 "设备安全" 页。</span><span class="sxs-lookup"><span data-stu-id="00e68-189">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="00e68-190">**酷**:指示设备的温度。</span><span class="sxs-lookup"><span data-stu-id="00e68-190">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="00e68-191">**A/C**:指示设备是否已插入并正在充电。</span><span class="sxs-lookup"><span data-stu-id="00e68-191">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="00e68-192">**帮助**:打开 REST 接口文档页。</span><span class="sxs-lookup"><span data-stu-id="00e68-192">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="00e68-193">主页将显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="00e68-193">The home page shows the following info:</span></span>
* <span data-ttu-id="00e68-194">**设备状态:** 监视设备的运行状况, 并报告严重错误。</span><span class="sxs-lookup"><span data-stu-id="00e68-194">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="00e68-195">**Windows 信息:** 显示 HoloLens 的名称和当前安装的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="00e68-195">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="00e68-196">**首选项**部分包含以下设置：</span><span class="sxs-lookup"><span data-stu-id="00e68-196">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="00e68-197">**IPD**:设置 interpupillary 距离 (IPD), 即在直接查找时, 用户的瞳孔中心之间的距离 (以毫米为单位)。</span><span class="sxs-lookup"><span data-stu-id="00e68-197">**IPD**: Sets the interpupillary distance (IPD), which is the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="00e68-198">该设置将立即生效。</span><span class="sxs-lookup"><span data-stu-id="00e68-198">The setting takes effect immediately.</span></span> <span data-ttu-id="00e68-199">在设置你的设备时，会自动计算该默认值。</span><span class="sxs-lookup"><span data-stu-id="00e68-199">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="00e68-200">**设备名称**:为 HoloLens 分配一个名称。</span><span class="sxs-lookup"><span data-stu-id="00e68-200">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="00e68-201">更改此值后，必须重新启动设备才能使该值生效。</span><span class="sxs-lookup"><span data-stu-id="00e68-201">You must reboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="00e68-202">单击 "**保存**" 后, 对话会询问你是要立即重启设备还是稍后重新启动。</span><span class="sxs-lookup"><span data-stu-id="00e68-202">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="00e68-203">**睡眠设置**:设置设备进入睡眠状态的时间, 在设备进入睡眠状态时等待的时间长度。</span><span class="sxs-lookup"><span data-stu-id="00e68-203">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="00e68-204">3D 视图</span><span class="sxs-lookup"><span data-stu-id="00e68-204">3D View</span></span>

<span data-ttu-id="00e68-205">![Microsoft HoloLens 上 Windows 设备门户中的3D 视图页面](images/3dview-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-205">![3D View page in Windows Device Portal on Microsoft HoloLens](images/3dview-1000px.png)</span></span><br>
<span data-ttu-id="00e68-206">*Microsoft HoloLens 上 Windows 设备门户中的3D 视图页面*</span><span class="sxs-lookup"><span data-stu-id="00e68-206">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-207">使用“3D 视图”页面可查看 HoloLens 感知周围环境的方式。</span><span class="sxs-lookup"><span data-stu-id="00e68-207">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="00e68-208">使用鼠标即可导览该视图：</span><span class="sxs-lookup"><span data-stu-id="00e68-208">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="00e68-209">旋转: 左键单击 + 鼠标;</span><span class="sxs-lookup"><span data-stu-id="00e68-209">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="00e68-210">平移: 右键单击 + 鼠标;</span><span class="sxs-lookup"><span data-stu-id="00e68-210">Pan: right click + mouse;</span></span>
* <span data-ttu-id="00e68-211">Zoom: 鼠标滚动。</span><span class="sxs-lookup"><span data-stu-id="00e68-211">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="00e68-212">**跟踪选项**</span><span class="sxs-lookup"><span data-stu-id="00e68-212">**Tracking options**</span></span>
   * <span data-ttu-id="00e68-213">通过检查**强制视觉对象跟踪**打开连续的视觉跟踪。</span><span class="sxs-lookup"><span data-stu-id="00e68-213">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="00e68-214">**暂停**停止视觉对象跟踪。</span><span class="sxs-lookup"><span data-stu-id="00e68-214">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="00e68-215">**视图选项**:设置3D 视图上的选项:</span><span class="sxs-lookup"><span data-stu-id="00e68-215">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="00e68-216">**跟踪**:指示视觉跟踪是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="00e68-216">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="00e68-217">**显示楼层**:显示棋盘楼层。</span><span class="sxs-lookup"><span data-stu-id="00e68-217">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="00e68-218">**显示**如下:显示视图 "截锥"。</span><span class="sxs-lookup"><span data-stu-id="00e68-218">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="00e68-219">**显示稳定平面**:显示 HoloLens 用于稳定运动的平面。</span><span class="sxs-lookup"><span data-stu-id="00e68-219">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="00e68-220">**显示网格**:显示表示你的环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="00e68-220">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="00e68-221">**显示空间锚**:显示活动应用的空间锚。</span><span class="sxs-lookup"><span data-stu-id="00e68-221">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="00e68-222">必须单击 "更新" 按钮, 才能获取和刷新锚。</span><span class="sxs-lookup"><span data-stu-id="00e68-222">You must click the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="00e68-223">**显示详细信息**:在实时更改时显示手形位置、头旋转四元数和设备原点矢量。</span><span class="sxs-lookup"><span data-stu-id="00e68-223">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="00e68-224">全屏**按钮**:以全屏模式显示3D 视图。</span><span class="sxs-lookup"><span data-stu-id="00e68-224">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="00e68-225">按 ESC 键可退出全屏视图。</span><span class="sxs-lookup"><span data-stu-id="00e68-225">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="00e68-226">**曲面重构**:单击或点击 "**更新**" 以显示设备的最新空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="00e68-226">**Surface reconstruction**: Click or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="00e68-227">完成全面检查可能需要一些时间，最多只需几秒钟。</span><span class="sxs-lookup"><span data-stu-id="00e68-227">A full pass may take some time to complete, up to a few seconds.</span></span> <span data-ttu-id="00e68-228">网格不会在三维视图中自动更新, 您必须手动单击 "**更新**" 以从设备获取最新的网格。</span><span class="sxs-lookup"><span data-stu-id="00e68-228">The mesh does not update automatically in the 3D view, and you must manually click **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="00e68-229">单击 "**保存**" 可将当前空间映射网格作为 obj 文件保存到电脑上。</span><span class="sxs-lookup"><span data-stu-id="00e68-229">Click **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="00e68-230">**空间锚**:单击 "更新" 可显示或更新活动应用的空间锚。</span><span class="sxs-lookup"><span data-stu-id="00e68-230">**Spatial anchors**: Click Update to display or update the spatial anchors for the active app.</span></span>

### <a name="mixed-reality-capture"></a><span data-ttu-id="00e68-231">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="00e68-231">Mixed Reality Capture</span></span>

<span data-ttu-id="00e68-232">![Microsoft HoloLens 上 Windows 设备门户中的混合现实捕获页面](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-232">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-233">*Microsoft HoloLens 上 Windows 设备门户中的混合现实捕获页面*</span><span class="sxs-lookup"><span data-stu-id="00e68-233">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-234">使用“混合现实捕获”页面可保存 HoloLens 中的媒体流。</span><span class="sxs-lookup"><span data-stu-id="00e68-234">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="00e68-235">**设置**:通过检查以下设置来控制捕获的媒体流:</span><span class="sxs-lookup"><span data-stu-id="00e68-235">**Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="00e68-236">**全息影像**:捕获视频流中的全息内容。</span><span class="sxs-lookup"><span data-stu-id="00e68-236">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="00e68-237">呈现全息图时使用的是单声道，而不是立体声。</span><span class="sxs-lookup"><span data-stu-id="00e68-237">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="00e68-238">**PV 照相机**:从照片/视频摄像机捕获视频流。</span><span class="sxs-lookup"><span data-stu-id="00e68-238">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="00e68-239">**Mic 音频**:从麦克风阵列捕获音频。</span><span class="sxs-lookup"><span data-stu-id="00e68-239">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="00e68-240">**应用音频**:从当前运行的应用捕获音频。</span><span class="sxs-lookup"><span data-stu-id="00e68-240">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="00e68-241">**从照相机呈现**:如果[正在运行的应用程序支持](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), 则将捕获与照片/视频摄像机的透视图对齐: 仅限 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="00e68-241">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="00e68-242">**实时预览质量**:选择实时预览的屏幕分辨率、帧速率和流式处理速率。</span><span class="sxs-lookup"><span data-stu-id="00e68-242">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="00e68-243">单击或点击 "**实时预览**" 按钮, 以显示捕获流。</span><span class="sxs-lookup"><span data-stu-id="00e68-243">Click or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="00e68-244">**停止实时预览**停止捕获流。</span><span class="sxs-lookup"><span data-stu-id="00e68-244">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="00e68-245">单击或点击 "**记录**", 使用指定的设置开始记录混合现实流。</span><span class="sxs-lookup"><span data-stu-id="00e68-245">Click or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="00e68-246">**停止录制**将结束录制并保存。</span><span class="sxs-lookup"><span data-stu-id="00e68-246">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="00e68-247">单击或点击 "**拍摄照片**", 拍摄捕获流中的静止图像。</span><span class="sxs-lookup"><span data-stu-id="00e68-247">Click or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="00e68-248">**视频和照片**:显示在设备上拍摄的视频和照片捕获的列表。</span><span class="sxs-lookup"><span data-stu-id="00e68-248">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="00e68-249">同时提供了一些[限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span><span class="sxs-lookup"><span data-stu-id="00e68-249">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="00e68-250">如果应用在 Windows 设备门户录制视频时尝试访问 photo/视频摄像机, 视频录制将停止。</span><span class="sxs-lookup"><span data-stu-id="00e68-250">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="00e68-251">如果应用在 SharedReadOnly 模式下 acesses 照片/视频相机, 则 HoloLens 2 不会停止录制视频。</span><span class="sxs-lookup"><span data-stu-id="00e68-251">HoloLens 2 will not stop recording video if the app acesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="00e68-252">如果应用正在使用照片/视频摄像机, Windows 设备门户可以拍摄照片或录制视频。</span><span class="sxs-lookup"><span data-stu-id="00e68-252">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="00e68-253">实时流式处理:</span><span class="sxs-lookup"><span data-stu-id="00e68-253">Live streaming:</span></span>
>   * <span data-ttu-id="00e68-254">HoloLens (第一代) 会阻止应用从 Windows 设备门户实时传送视频时访问照片/视频摄像机。</span><span class="sxs-lookup"><span data-stu-id="00e68-254">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="00e68-255">如果应用正在使用 photo/视频摄像机, 则 HoloLens (第一代) 将无法实时传输。</span><span class="sxs-lookup"><span data-stu-id="00e68-255">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="00e68-256">在应用尝试以 ExclusiveControl 模式访问照片/视频摄像机时, HoloLens 2 自动停止实时流式处理。</span><span class="sxs-lookup"><span data-stu-id="00e68-256">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="00e68-257">在应用主动使用 PV 摄像机时, HoloLens 2 可以启动实时流。</span><span class="sxs-lookup"><span data-stu-id="00e68-257">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="00e68-258">性能跟踪</span><span class="sxs-lookup"><span data-stu-id="00e68-258">Performance Tracing</span></span>

<span data-ttu-id="00e68-259">![Microsoft HoloLens 上 Windows 设备门户中的 "性能跟踪" 页](images/windows-device-portal-performance-tracing-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-259">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-260">*Microsoft HoloLens 上 Windows 设备门户中的 "性能跟踪" 页*</span><span class="sxs-lookup"><span data-stu-id="00e68-260">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-261">从 HoloLens 捕获[Windows 性能记录器](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx)(") 跟踪。</span><span class="sxs-lookup"><span data-stu-id="00e68-261">Capture [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="00e68-262">**可用配置文件**:从下拉列表中选择 "" "配置文件, 然后单击或点击"**启动**"以启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="00e68-262">**Available profiles**: Select the WPR profile from the dropdown, and click or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="00e68-263">**自定义配置文件**:单击或点击 "**浏览**", 从电脑选择 "配置文件。</span><span class="sxs-lookup"><span data-stu-id="00e68-263">**Custom profiles**: Click or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="00e68-264">单击或点击**上载并启动**以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="00e68-264">Click or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="00e68-265">若要停止跟踪, 请单击 "停止" 链接。</span><span class="sxs-lookup"><span data-stu-id="00e68-265">To stop the trace click on the stop link.</span></span> <span data-ttu-id="00e68-266">一直在此页上, 直到跟踪文件下载完成。</span><span class="sxs-lookup"><span data-stu-id="00e68-266">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="00e68-267">可以打开捕获的 ETL 文件以供在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中进行分析。</span><span class="sxs-lookup"><span data-stu-id="00e68-267">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).</span></span>

### <a name="processes"></a><span data-ttu-id="00e68-268">进程</span><span class="sxs-lookup"><span data-stu-id="00e68-268">Processes</span></span>

<span data-ttu-id="00e68-269">![Microsoft HoloLens 上 Windows 设备门户中的 "进程" 页](images/windows-device-portal-running-processes-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-269">![Processes page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-270">*Microsoft HoloLens 上 Windows 设备门户中的 "进程" 页*</span><span class="sxs-lookup"><span data-stu-id="00e68-270">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-271">显示有关当前正在运行的进程的详细信息。</span><span class="sxs-lookup"><span data-stu-id="00e68-271">Shows details about currently running processes.</span></span> <span data-ttu-id="00e68-272">这包括应用和系统进程。</span><span class="sxs-lookup"><span data-stu-id="00e68-272">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="00e68-273">系统性能</span><span class="sxs-lookup"><span data-stu-id="00e68-273">System Performance</span></span>

<span data-ttu-id="00e68-274">![Microsoft HoloLens 上 Windows 设备门户中的 "系统性能" 页](images/windows-device-portal-system-performance-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-274">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-275">*Microsoft HoloLens 上 Windows 设备门户中的 "系统性能" 页*</span><span class="sxs-lookup"><span data-stu-id="00e68-275">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-276">显示系统诊断信息的实时图形，如电源使用情况、帧速率和 CPU 负载。</span><span class="sxs-lookup"><span data-stu-id="00e68-276">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="00e68-277">可用的指标如下所示：</span><span class="sxs-lookup"><span data-stu-id="00e68-277">These are the available metrics:</span></span>
* <span data-ttu-id="00e68-278">**SoC 电源**:瞬时系统芯片电源利用率, 平均值超过一分钟</span><span class="sxs-lookup"><span data-stu-id="00e68-278">**SoC power**: Instantaneous system-on-chip power utilization, averaged over one minute</span></span>
* <span data-ttu-id="00e68-279">**系统电源**:瞬间系统电源利用率, 平均值超过一分钟</span><span class="sxs-lookup"><span data-stu-id="00e68-279">**System power**: Instantaneous system power utilization, averaged over one minute</span></span>
* <span data-ttu-id="00e68-280">**帧速率**:每秒帧数、每秒丢失的 VBlanks 和连续丢失的 VBlanks</span><span class="sxs-lookup"><span data-stu-id="00e68-280">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="00e68-281">**GPU**:GPU 引擎利用率, 总可用百分比</span><span class="sxs-lookup"><span data-stu-id="00e68-281">**GPU**: GPU engine utilization, percent of total available</span></span>
* <span data-ttu-id="00e68-282">**CPU**: 可用总数百分比</span><span class="sxs-lookup"><span data-stu-id="00e68-282">**CPU**: percent of total available</span></span>
* <span data-ttu-id="00e68-283">**I/O**:读取和写入</span><span class="sxs-lookup"><span data-stu-id="00e68-283">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="00e68-284">**网络**：接收和发送</span><span class="sxs-lookup"><span data-stu-id="00e68-284">**Network**: Received and sent</span></span>
* <span data-ttu-id="00e68-285">**内存**:总计、已用、已提交、分页和非分页</span><span class="sxs-lookup"><span data-stu-id="00e68-285">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="00e68-286">应用</span><span class="sxs-lookup"><span data-stu-id="00e68-286">Apps</span></span>

<span data-ttu-id="00e68-287">![Microsoft HoloLens 上 Windows 设备门户中的 "应用" 页](images/windows-device-portal-apps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-287">![Apps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-288">*Microsoft HoloLens 上 Windows 设备门户中的 "应用" 页*</span><span class="sxs-lookup"><span data-stu-id="00e68-288">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-289">管理 HoloLens 上安装的应用。</span><span class="sxs-lookup"><span data-stu-id="00e68-289">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="00e68-290">**已安装的应用**:删除和启动应用。</span><span class="sxs-lookup"><span data-stu-id="00e68-290">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="00e68-291">**正在运行的应用**:列出当前正在运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="00e68-291">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="00e68-292">**安装应用程序**:从计算机/网络上的文件夹中选择要安装的应用包。</span><span class="sxs-lookup"><span data-stu-id="00e68-292">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="00e68-293">**依赖项**:添加要安装的应用的依赖项。</span><span class="sxs-lookup"><span data-stu-id="00e68-293">**Dependency**: Add dependencies for the app you are going to install.</span></span>
* <span data-ttu-id="00e68-294">**部署**:将所选应用程序和依赖项部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="00e68-294">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="00e68-295">应用故障转储</span><span class="sxs-lookup"><span data-stu-id="00e68-295">App Crash Dumps</span></span>

<span data-ttu-id="00e68-296">![Microsoft HoloLens 上 Windows 设备门户中的应用故障转储页面](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-296">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-297">*Microsoft HoloLens 上 Windows 设备门户中的应用故障转储页面*</span><span class="sxs-lookup"><span data-stu-id="00e68-297">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-298">此页面允许你收集旁加载应用的故障转储。</span><span class="sxs-lookup"><span data-stu-id="00e68-298">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="00e68-299">对于要为其收集故障转储的每个应用, 选中 "**已启用故障转储**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="00e68-299">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="00e68-300">返回到此页面可收集故障转储。</span><span class="sxs-lookup"><span data-stu-id="00e68-300">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="00e68-301">可[在 Visual Studio 中打开转储文件以进行调试](https://msdn.microsoft.com/library/d5zhxt22.aspx)。</span><span class="sxs-lookup"><span data-stu-id="00e68-301">Dump files can be [opened in Visual Studio for debugging](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="00e68-302">文件资源管理器</span><span class="sxs-lookup"><span data-stu-id="00e68-302">File Explorer</span></span>

<span data-ttu-id="00e68-303">![Microsoft HoloLens 上 Windows 设备门户中的文件资源管理器页](images/fileexplorer-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-303">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/fileexplorer-1000px.png)</span></span><br>
<span data-ttu-id="00e68-304">*Microsoft HoloLens 上 Windows 设备门户中的文件资源管理器页*</span><span class="sxs-lookup"><span data-stu-id="00e68-304">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-305">使用文件资源管理器浏览、上传和下载文件。</span><span class="sxs-lookup"><span data-stu-id="00e68-305">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="00e68-306">对于从 Visual Studio 或设备门户部署的应用, 可以在 "文档" 文件夹、"图片" 文件夹和 "本地存储文件夹" 中处理文件。</span><span class="sxs-lookup"><span data-stu-id="00e68-306">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="00e68-307">展台模式</span><span class="sxs-lookup"><span data-stu-id="00e68-307">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="00e68-308">展台模式仅适用于[Microsoft HoloLens 商业套件](commercial-features.md)。</span><span class="sxs-lookup"><span data-stu-id="00e68-308">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](commercial-features.md).</span></span>

<span data-ttu-id="00e68-309">有关通过 Windows 设备门户启用展台模式的最新说明, 请参阅 Windows IT 专业人员中心中的在[展台模式下设置 HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 。</span><span class="sxs-lookup"><span data-stu-id="00e68-309">Please check the [Set up HoloLens in kiosk mode](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="00e68-310">日志记录</span><span class="sxs-lookup"><span data-stu-id="00e68-310">Logging</span></span>

<span data-ttu-id="00e68-311">![Microsoft HoloLens 上 Windows 设备门户中的 "日志记录" 页](images/windows-device-portal-logging-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-311">![Logging page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-312">*Microsoft HoloLens 上 Windows 设备门户中的 "日志记录" 页*</span><span class="sxs-lookup"><span data-stu-id="00e68-312">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-313">管理 HoloLens 上 Windows (ETW) 的实时事件跟踪。</span><span class="sxs-lookup"><span data-stu-id="00e68-313">Manages realtime Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="00e68-314">选中 "**隐藏提供程序**" 以仅显示**事件**列表。</span><span class="sxs-lookup"><span data-stu-id="00e68-314">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="00e68-315">**已注册的提供程序**:选择 "ETW 提供程序" 和 "跟踪级别"。</span><span class="sxs-lookup"><span data-stu-id="00e68-315">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="00e68-316">跟踪级别是以下值之一：</span><span class="sxs-lookup"><span data-stu-id="00e68-316">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="00e68-317">异常退出或终止</span><span class="sxs-lookup"><span data-stu-id="00e68-317">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="00e68-318">严重错误</span><span class="sxs-lookup"><span data-stu-id="00e68-318">Severe errors</span></span>
   3. <span data-ttu-id="00e68-319">警告</span><span class="sxs-lookup"><span data-stu-id="00e68-319">Warnings</span></span>
   4. <span data-ttu-id="00e68-320">非错误警告</span><span class="sxs-lookup"><span data-stu-id="00e68-320">Non-error warnings</span></span>

<span data-ttu-id="00e68-321">单击或点击**启用**以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="00e68-321">Click or tap **Enable** to start tracing.</span></span> <span data-ttu-id="00e68-322">提供程序将添加到**已启用的提供程序**下拉列表。</span><span class="sxs-lookup"><span data-stu-id="00e68-322">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="00e68-323">**自定义提供程序**:选择一个自定义 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="00e68-323">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="00e68-324">根据其 GUDI 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="00e68-324">Identify the provider by its GUID.</span></span> <span data-ttu-id="00e68-325">不要在 GUID 中包含括号。</span><span class="sxs-lookup"><span data-stu-id="00e68-325">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="00e68-326">**已启用的提供程序**:列出已启用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="00e68-326">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="00e68-327">从下拉列表中选择一个提供程序，然后单击或点击**禁用**来停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="00e68-327">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="00e68-328">单击或点击**全部停止**来暂停所有跟踪。</span><span class="sxs-lookup"><span data-stu-id="00e68-328">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="00e68-329">**提供程序历史记录**:显示在当前会话期间启用的 ETW 提供程序。</span><span class="sxs-lookup"><span data-stu-id="00e68-329">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="00e68-330">单击或点击**启用**来激活已禁用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="00e68-330">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="00e68-331">单击或点击**清除**来清除历史记录。</span><span class="sxs-lookup"><span data-stu-id="00e68-331">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="00e68-332">**事件**:按表格式列出所选提供程序中的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="00e68-332">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="00e68-333">此表将实时更新。</span><span class="sxs-lookup"><span data-stu-id="00e68-333">This table is updated in real time.</span></span> <span data-ttu-id="00e68-334">在表的下方, 单击 "**清除**" 按钮, 以从表中删除所有 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="00e68-334">Beneath the table, click on the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="00e68-335">这不会禁用任何提供程序。</span><span class="sxs-lookup"><span data-stu-id="00e68-335">This does not disable any providers.</span></span> <span data-ttu-id="00e68-336">你可以单击**保存到文件**来将当前收集的 ETW 事件本地导出到 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="00e68-336">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="00e68-337">**筛选器**:允许你筛选由 ID、关键字、级别、提供程序名称、任务名称或文本收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="00e68-337">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="00e68-338">可以将多个条件组合在一起:</span><span class="sxs-lookup"><span data-stu-id="00e68-338">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="00e68-339">对于应用到相同属性的条件, 可以满足这些条件中的任何一个。</span><span class="sxs-lookup"><span data-stu-id="00e68-339">For criteria applying to the same property - events can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="00e68-340">适用于不同属性事件的条件必须满足所有条件</span><span class="sxs-lookup"><span data-stu-id="00e68-340">For criteria applying to different property - events must satisfy all of the criteria</span></span>

<span data-ttu-id="00e68-341">例如, 你可以指定条件 *(任务名称包含 "Foo" 或 "Bar") 以及 (文本包含 "错误" 或 "警告")*</span><span class="sxs-lookup"><span data-stu-id="00e68-341">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="00e68-342">模拟</span><span class="sxs-lookup"><span data-stu-id="00e68-342">Simulation</span></span>

<span data-ttu-id="00e68-343">![Microsoft HoloLens 上 Windows 设备门户中的模拟页面](images/windows-device-portal-simulation-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-343">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-344">*Microsoft HoloLens 上 Windows 设备门户中的模拟页面*</span><span class="sxs-lookup"><span data-stu-id="00e68-344">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-345">允许你记录和播放用于测试的输入数据。</span><span class="sxs-lookup"><span data-stu-id="00e68-345">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="00e68-346">**捕获会议室**:用于下载模拟房间文件, 其中包含用户的环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="00e68-346">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="00e68-347">命名聊天室, 然后单击 "**捕获**", 将数据以 xef 文件的形式保存在电脑上。</span><span class="sxs-lookup"><span data-stu-id="00e68-347">Name the room and then click **Capture** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="00e68-348">此房间文件可以加载到 HoloLens 仿真器中。</span><span class="sxs-lookup"><span data-stu-id="00e68-348">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="00e68-349">**记录**:检查要录制的流, 命名该记录, 然后单击或点击 "**记录**" 以开始进行编码。</span><span class="sxs-lookup"><span data-stu-id="00e68-349">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="00e68-350">使用 HoloLens 执行操作, 然后单击 "**停止**" 将数据作为 xef 文件保存在电脑上。</span><span class="sxs-lookup"><span data-stu-id="00e68-350">Perform actions with your HoloLens and then click **Stop** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="00e68-351">可以在 HoloLens 仿真器或设备上加载此文件。</span><span class="sxs-lookup"><span data-stu-id="00e68-351">This file can be loaded on the HoloLens emulator or device.</span></span>
* <span data-ttu-id="00e68-352">**播放**:单击或点击 "**上传记录**", 从电脑选择 xef 文件, 并将数据发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="00e68-352">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="00e68-353">**控制模式**:从下拉列表中选择 "**默认**" 或 "**模拟**", 然后单击或点击 "**设置**" 按钮以在 HoloLens 上选择模式。</span><span class="sxs-lookup"><span data-stu-id="00e68-353">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="00e68-354">相反，选择“模拟”会禁用 HoloLens 上的真实传感器，并使用已上载的模拟数据。</span><span class="sxs-lookup"><span data-stu-id="00e68-354">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="00e68-355">如果切换到“模拟”，HoloLens 将不会响应真实用户，除非切换回“默认”。</span><span class="sxs-lookup"><span data-stu-id="00e68-355">If you switch to "Simulation", your HoloLens will not respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="00e68-356">网络</span><span class="sxs-lookup"><span data-stu-id="00e68-356">Networking</span></span>

<span data-ttu-id="00e68-357">![Microsoft HoloLens 上 Windows 设备门户中的 "网络" 页](images/windows-device-portal-networking-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-357">![Networking page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-358">*Microsoft HoloLens 上 Windows 设备门户中的 "网络" 页*</span><span class="sxs-lookup"><span data-stu-id="00e68-358">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-359">管理 HoloLens 上的 Wi-fi 连接。</span><span class="sxs-lookup"><span data-stu-id="00e68-359">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="00e68-360">**WiFi 适配器**:使用下拉控件选择 Wi-fi 适配器和配置文件。</span><span class="sxs-lookup"><span data-stu-id="00e68-360">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="00e68-361">单击或点击 "**连接**" 以使用所选适配器。</span><span class="sxs-lookup"><span data-stu-id="00e68-361">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="00e68-362">**可用网络**:列出了 HoloLens 可以连接到的 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="00e68-362">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="00e68-363">单击或点击 "**刷新**" 以更新列表。</span><span class="sxs-lookup"><span data-stu-id="00e68-363">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="00e68-364">**IP 配置**:显示网络连接的 IP 地址和其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="00e68-364">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="00e68-365">虚拟输入</span><span class="sxs-lookup"><span data-stu-id="00e68-365">Virtual Input</span></span>

<span data-ttu-id="00e68-366">![Microsoft HoloLens 上 Windows 设备门户中的虚拟输入页面](images/windows-device-portal-virtual-input-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="00e68-366">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)</span></span><br>
<span data-ttu-id="00e68-367">*Microsoft HoloLens 上 Windows 设备门户中的虚拟输入页面*</span><span class="sxs-lookup"><span data-stu-id="00e68-367">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="00e68-368">将键盘输入从远程计算机发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="00e68-368">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="00e68-369">单击或点击 "**虚拟键盘**" 下的区域, 以允许向 HoloLens 发送击键。</span><span class="sxs-lookup"><span data-stu-id="00e68-369">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="00e68-370">在 "**输入文本**" 文本框中键入, 然后单击或点击 "**发送**", 将击键发送到活动的应用。</span><span class="sxs-lookup"><span data-stu-id="00e68-370">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="00e68-371">设备门户 REST API</span><span class="sxs-lookup"><span data-stu-id="00e68-371">Device Portal REST API's</span></span>

<span data-ttu-id="00e68-372">设备门户中的所有内容都是在[REST API](device-portal-api-reference.md)的基础之上构建的, 你可以选择使用它来访问数据并以编程方式控制设备。</span><span class="sxs-lookup"><span data-stu-id="00e68-372">Everything in the device portal is built on top of [REST API's](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>
