---
title: 使用 Windows Device Portal
description: HoloLens Windows Device Portal 允许您配置和通过 Wi-fi 或 USB 远程管理你的设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包括许多工具，可帮助您管理您的 HoloLens 和调试和优化你的应用。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows Device Portal HoloLens
ms.openlocfilehash: 79a4a1f99125028fcaf71e185eb00093aa8c742f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694586"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="c810c-106">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="c810c-106">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="c810c-107">功能</span><span class="sxs-lookup"><span data-stu-id="c810c-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="c810c-108"><a href="hololens-hardware-details.md">HoloLens（第一代）</a></span><span class="sxs-lookup"><span data-stu-id="c810c-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="c810c-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c810c-109">HoloLens 2</span></span></th><th style="width:150px"><span data-ttu-id="c810c-110"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="c810c-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c810c-111">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="c810c-111">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="c810c-112">✔️</span><span class="sxs-lookup"><span data-stu-id="c810c-112">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c810c-113">✔️</span><span class="sxs-lookup"><span data-stu-id="c810c-113">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="c810c-114">HoloLens Windows Device Portal 允许您配置和通过 Wi-fi 或 USB 远程管理你的设备。</span><span class="sxs-lookup"><span data-stu-id="c810c-114">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="c810c-115">Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。</span><span class="sxs-lookup"><span data-stu-id="c810c-115">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="c810c-116">设备门户包括许多工具，可帮助您管理您的 HoloLens 和调试和优化你的应用。</span><span class="sxs-lookup"><span data-stu-id="c810c-116">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="c810c-117">本文档将专门介绍 HoloLens Windows Device Portal。</span><span class="sxs-lookup"><span data-stu-id="c810c-117">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="c810c-118">若要为桌面 （包括 Windows Mixed Reality） 使用 Windows 设备门户，请参阅[Windows Device Portal 概述](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="c810c-118">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="c810c-119">设置 HoloLens 以使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="c810c-119">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="c810c-120">打开 HoloLens 的电源，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="c810c-120">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="c810c-121">执行[绽放](gestures.md#bloom)手势来启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="c810c-121">Perform the [bloom](gestures.md#bloom) gesture to launch the main menu.</span></span>
3. <span data-ttu-id="c810c-122">注视**设置**磁贴，并执行[air 点击](gestures.md#air-tap)手势。</span><span class="sxs-lookup"><span data-stu-id="c810c-122">Gaze at the **Settings** tile and perform the [air-tap](gestures.md#air-tap) gesture.</span></span> <span data-ttu-id="c810c-123">执行第二个的 air-点击以在你的环境中将此应用程序。</span><span class="sxs-lookup"><span data-stu-id="c810c-123">Perform a second air-tap to place the app in your environment.</span></span> <span data-ttu-id="c810c-124">在放置“设置”应用后，将启动该应用。</span><span class="sxs-lookup"><span data-stu-id="c810c-124">The Settings app will launch after you place it.</span></span>
4. <span data-ttu-id="c810c-125">选择“更新”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="c810c-125">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="c810c-126">选择“面向开发人员”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="c810c-126">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="c810c-127">启用“开发人员模式”  。</span><span class="sxs-lookup"><span data-stu-id="c810c-127">Enable **Developer Mode**.</span></span>
7. <span data-ttu-id="c810c-128">[向下滚动](gestures.md#composite-gestures)并启用**设备门户**。</span><span class="sxs-lookup"><span data-stu-id="c810c-128">[Scroll down](gestures.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="c810c-129">如果您设置了 Windows Device Portal 以便可以将应用部署到此 HoloLens 通过 USB 或 Wi-fi，请单击**对**到[生成一个配对的 PIN](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="c810c-129">If you are setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, click **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="c810c-130">到 Visual Studio PIN 输入在第一个部署过程之前，请将设置应用保留 PIN 弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="c810c-130">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

   ![设置应用于 Windows Holographic 中启用开发人员模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="c810c-132">通过 Wi-fi 连接</span><span class="sxs-lookup"><span data-stu-id="c810c-132">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="c810c-133">[连接到 Wi-fi 你 HoloLens](connecting-to-wi-fi-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="c810c-133">[Connect your HoloLens to Wi-Fi](connecting-to-wi-fi-on-hololens.md).</span></span>
2. <span data-ttu-id="c810c-134">查找你的设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c810c-134">Look up your device's IP address.</span></span>
   * <span data-ttu-id="c810c-135">在设备上找到的 IP 地址**设置 > 网络和 Internet > Wi-fi > 高级选项**。</span><span class="sxs-lookup"><span data-stu-id="c810c-135">Find the IP address on the device under **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
3. <span data-ttu-id="c810c-136">从 web 浏览器中您的 PC 上，请转到 https://<YOUR_HOLOLENS_IP_ADDRESS></span><span class="sxs-lookup"><span data-stu-id="c810c-136">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="c810c-137">在浏览器将显示以下消息："没有此网站的安全证书有问题"。</span><span class="sxs-lookup"><span data-stu-id="c810c-137">The browser will display the following message: "There’s a problem with this website’s security certificate".</span></span> <span data-ttu-id="c810c-138">由于颁发给 Device Portal 的证书是测试证书，因此会显示上述消息。</span><span class="sxs-lookup"><span data-stu-id="c810c-138">This happens because the certificate which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="c810c-139">你可以暂时忽略此证书错误并继续。</span><span class="sxs-lookup"><span data-stu-id="c810c-139">You can ignore this certificate error for now and proceed.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="c810c-140">通过 USB 连接</span><span class="sxs-lookup"><span data-stu-id="c810c-140">Connecting over USB</span></span>

1. <span data-ttu-id="c810c-141">[安装工具](install-the-tools.md)以确保您查看您的 PC 上安装了 Windows 10 开发人员工具与 Visual Studio Update 1。</span><span class="sxs-lookup"><span data-stu-id="c810c-141">[Install the tools](install-the-tools.md) to make sure you have Visual Studio Update 1 with the Windows 10 developer tools installed on your PC.</span></span> <span data-ttu-id="c810c-142">这支持 USB 连接。</span><span class="sxs-lookup"><span data-stu-id="c810c-142">This enables USB connectivity.</span></span>
2. <span data-ttu-id="c810c-143">使用微型 USB 电缆将 HoloLens 连接到电脑。</span><span class="sxs-lookup"><span data-stu-id="c810c-143">Connect your HoloLens to your PC with a micro-USB cable.</span></span>
3. <span data-ttu-id="c810c-144">通过电脑上的 Web 浏览器，转到 http://127.0.0.1:10080 。</span><span class="sxs-lookup"><span data-stu-id="c810c-144">From a web browser on your PC, go to http://127.0.0.1:10080.</span></span>

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="c810c-145">连接到模拟器</span><span class="sxs-lookup"><span data-stu-id="c810c-145">Connecting to an emulator</span></span>

<span data-ttu-id="c810c-146">也可以将 Device Portal 与仿真器结合使用。</span><span class="sxs-lookup"><span data-stu-id="c810c-146">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="c810c-147">若要连接到设备门户，请使用[工具栏](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="c810c-147">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="c810c-148">单击此图标：![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**:在仿真器中打开 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="c810c-148">Click on this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="c810c-149">创建用户名和密码</span><span class="sxs-lookup"><span data-stu-id="c810c-149">Creating a Username and Password</span></span>

<span data-ttu-id="c810c-150">![设置对 Windows Device Portal 访问权限](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-150">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-151">*设置对 Windows Device Portal 访问权限*</span><span class="sxs-lookup"><span data-stu-id="c810c-151">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="c810c-152">首次连接到 HoloLens 上的 Device Portal 时，需要创建用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="c810c-152">The first time you connect to the Device Portal on your HoloLens, you will need to create a username and password.</span></span>
1. <span data-ttu-id="c810c-153">在电脑上的 Web 浏览器中，输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c810c-153">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="c810c-154">将打开“设置访问”页面。</span><span class="sxs-lookup"><span data-stu-id="c810c-154">The Set up access page opens.</span></span>
2. <span data-ttu-id="c810c-155">单击或点击**请求 pin**并查看 HoloLens 显示效果以获取生成的 PIN。</span><span class="sxs-lookup"><span data-stu-id="c810c-155">Click or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="c810c-156">输入在 PIN**在设备上显示 PIN**文本框中。</span><span class="sxs-lookup"><span data-stu-id="c810c-156">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="c810c-157">输入将用于连接到 Device Portal 的用户名。</span><span class="sxs-lookup"><span data-stu-id="c810c-157">Enter the user name you will use to connect to the Device Portal.</span></span> <span data-ttu-id="c810c-158">无需使用 Microsoft 帐户 (MSA) 名称或域名作为用户名。</span><span class="sxs-lookup"><span data-stu-id="c810c-158">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="c810c-159">输入密码并进行确认。</span><span class="sxs-lookup"><span data-stu-id="c810c-159">Enter a password and confirm it.</span></span> <span data-ttu-id="c810c-160">密码长度必须至少为七个字符。</span><span class="sxs-lookup"><span data-stu-id="c810c-160">The password must be at least seven characters in length.</span></span> <span data-ttu-id="c810c-161">无需使用 MSA 密码或域密码作为密码。</span><span class="sxs-lookup"><span data-stu-id="c810c-161">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="c810c-162">单击**对**连接到 Windows Device Portal HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="c810c-162">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="c810c-163">如果你想要在任何时候更改此用户名或密码，您可以通过访问通过导航到设备安全页中重复此过程： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm。</span><span class="sxs-lookup"><span data-stu-id="c810c-163">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="c810c-164">安全证书</span><span class="sxs-lookup"><span data-stu-id="c810c-164">Security certificate</span></span>

<span data-ttu-id="c810c-165">如果你在浏览器中看到“证书错误”，可以通过创建与该设备的信任关系来修复该错误。</span><span class="sxs-lookup"><span data-stu-id="c810c-165">If you are see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="c810c-166">每个 HoloLens 会生成唯一的自签名证书以供其 SSL 连接使用。</span><span class="sxs-lookup"><span data-stu-id="c810c-166">Each HoloLens generates a unique self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="c810c-167">默认情况下，此证书不受电脑的 Web 浏览器信任，因此你可能会看到“证书错误”。</span><span class="sxs-lookup"><span data-stu-id="c810c-167">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="c810c-168">通过从你的 HoloLens 下载此证书（借助 USB 或信任的 WLAN 网络）并在你的电脑上信任该证书，可以安全地连接到设备。</span><span class="sxs-lookup"><span data-stu-id="c810c-168">By downloading this certificate from your HoloLens (over USB or a Wi-Fi network you trust) and trusting it on your PC, you can securely connect to your device.</span></span>
1. <span data-ttu-id="c810c-169">**请确保你位于安全网络 （USB 或您信任的 Wi-fi 网络）。**</span><span class="sxs-lookup"><span data-stu-id="c810c-169">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="c810c-170">从设备门户上的"安全"页面下载此设备的证书。</span><span class="sxs-lookup"><span data-stu-id="c810c-170">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="c810c-171">导航到： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="c810c-171">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
3. <span data-ttu-id="c810c-172">安装在"受信任的根证书颁发机构"存储在 PC 的证书。</span><span class="sxs-lookup"><span data-stu-id="c810c-172">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="c810c-173">从 Windows 菜单中，键入：管理计算机证书和启动小程序。</span><span class="sxs-lookup"><span data-stu-id="c810c-173">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="c810c-174">展开**受信任的根证书颁发机构**文件夹。</span><span class="sxs-lookup"><span data-stu-id="c810c-174">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="c810c-175">单击**证书**文件夹。</span><span class="sxs-lookup"><span data-stu-id="c810c-175">Click on the **Certificates** folder.</span></span>
   * <span data-ttu-id="c810c-176">从操作菜单中选择：所有任务 > 导入...</span><span class="sxs-lookup"><span data-stu-id="c810c-176">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="c810c-177">使用从 Device Portal 下载的证书文件，完成“证书导入向导”。</span><span class="sxs-lookup"><span data-stu-id="c810c-177">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="c810c-178">重新启动浏览器。</span><span class="sxs-lookup"><span data-stu-id="c810c-178">Restart the browser.</span></span>

## <a name="device-portal-pages"></a><span data-ttu-id="c810c-179">Device Portal 页面</span><span class="sxs-lookup"><span data-stu-id="c810c-179">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="c810c-180">主页</span><span class="sxs-lookup"><span data-stu-id="c810c-180">Home</span></span>

<span data-ttu-id="c810c-181">![Windows Device Portal 主页上，在 Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-181">![Windows Device Portal home page on Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-182">*Windows Device Portal 主页上，在 Microsoft HoloLens*</span><span class="sxs-lookup"><span data-stu-id="c810c-182">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-183">Device Portal 会话从主页开始。</span><span class="sxs-lookup"><span data-stu-id="c810c-183">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="c810c-184">可从主页的左侧导航栏访问其他页面。</span><span class="sxs-lookup"><span data-stu-id="c810c-184">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="c810c-185">主页顶部的工具栏提供对常用状态和功能的访问。</span><span class="sxs-lookup"><span data-stu-id="c810c-185">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="c810c-186">**联机**:指示是否将设备连接到 Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="c810c-186">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="c810c-187">**关闭**:关闭设备。</span><span class="sxs-lookup"><span data-stu-id="c810c-187">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="c810c-188">**重新启动**:在设备上关闭后再打开。</span><span class="sxs-lookup"><span data-stu-id="c810c-188">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="c810c-189">**安全**：将打开设备安全页。</span><span class="sxs-lookup"><span data-stu-id="c810c-189">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="c810c-190">**冷**:指示设备的温度。</span><span class="sxs-lookup"><span data-stu-id="c810c-190">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="c810c-191">**A/C**:指示是否在插入设备和收费。</span><span class="sxs-lookup"><span data-stu-id="c810c-191">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="c810c-192">**帮助**:将打开的 REST 接口文档页。</span><span class="sxs-lookup"><span data-stu-id="c810c-192">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="c810c-193">主页将显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="c810c-193">The home page shows the following info:</span></span>
* <span data-ttu-id="c810c-194">**设备状态：** 监视你的设备的运行状况，并报告严重错误。</span><span class="sxs-lookup"><span data-stu-id="c810c-194">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="c810c-195">**Windows 信息：** 显示 HoloLens 的名称和当前安装的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="c810c-195">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="c810c-196">**首选项**部分包含以下设置：</span><span class="sxs-lookup"><span data-stu-id="c810c-196">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="c810c-197">**IPD**:以毫米为单位的用户的瞳孔直接向前查找时在中心之间设置 interpupillary 距离 (IPD)，是的距离。</span><span class="sxs-lookup"><span data-stu-id="c810c-197">**IPD**: Sets the interpupillary distance (IPD), which is the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="c810c-198">该设置将立即生效。</span><span class="sxs-lookup"><span data-stu-id="c810c-198">The setting takes effect immediately.</span></span> <span data-ttu-id="c810c-199">在设置你的设备时，会自动计算该默认值。</span><span class="sxs-lookup"><span data-stu-id="c810c-199">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="c810c-200">**设备名称**:将一个名称分配到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c810c-200">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="c810c-201">更改此值后，必须重新启动设备才能使该值生效。</span><span class="sxs-lookup"><span data-stu-id="c810c-201">You must reboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="c810c-202">单击后**保存**，对话框将询问你是否想要立即重新启动设备，或稍后重新启动。</span><span class="sxs-lookup"><span data-stu-id="c810c-202">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="c810c-203">**睡眠设置**:设置要在设备进入睡眠状态时插入之前和它在由电池供电时等待时间的长度。</span><span class="sxs-lookup"><span data-stu-id="c810c-203">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="c810c-204">3D 视图</span><span class="sxs-lookup"><span data-stu-id="c810c-204">3D View</span></span>

<span data-ttu-id="c810c-205">![在 Microsoft HoloLens 上 Windows Device Portal 中的 3D 视图页](images/3dview-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-205">![3D View page in Windows Device Portal on Microsoft HoloLens](images/3dview-1000px.png)</span></span><br>
<span data-ttu-id="c810c-206">*在 Microsoft HoloLens 上 Windows Device Portal 中的 3D 视图页*</span><span class="sxs-lookup"><span data-stu-id="c810c-206">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-207">使用“3D 视图”页面可查看 HoloLens 感知周围环境的方式。</span><span class="sxs-lookup"><span data-stu-id="c810c-207">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="c810c-208">使用鼠标即可导览该视图：</span><span class="sxs-lookup"><span data-stu-id="c810c-208">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="c810c-209">旋转： 单击鼠标左键和鼠标;</span><span class="sxs-lookup"><span data-stu-id="c810c-209">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="c810c-210">平移： 右键单击 + 鼠标;</span><span class="sxs-lookup"><span data-stu-id="c810c-210">Pan: right click + mouse;</span></span>
* <span data-ttu-id="c810c-211">缩放： 鼠标滚动。</span><span class="sxs-lookup"><span data-stu-id="c810c-211">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="c810c-212">**跟踪选项**</span><span class="sxs-lookup"><span data-stu-id="c810c-212">**Tracking options**</span></span>
   * <span data-ttu-id="c810c-213">通过检查启用连续 visual 跟踪**强制 visual 跟踪**。</span><span class="sxs-lookup"><span data-stu-id="c810c-213">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="c810c-214">**暂停**直观跟踪将停止。</span><span class="sxs-lookup"><span data-stu-id="c810c-214">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="c810c-215">**查看选项**:设置对 3D 视图选项：</span><span class="sxs-lookup"><span data-stu-id="c810c-215">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="c810c-216">**跟踪**:指示 visual 跟踪是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="c810c-216">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="c810c-217">**显示基底**:显示越过方格形终点的 floor 平面。</span><span class="sxs-lookup"><span data-stu-id="c810c-217">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="c810c-218">**显示截锥**:显示视图截锥。</span><span class="sxs-lookup"><span data-stu-id="c810c-218">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="c810c-219">**显示稳定平面**:显示稳定动作用于 HoloLens 的平面。</span><span class="sxs-lookup"><span data-stu-id="c810c-219">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="c810c-220">**显示网格**:显示空间映射网格表示周围的环境。</span><span class="sxs-lookup"><span data-stu-id="c810c-220">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="c810c-221">**显示空间定位标记**:有关活动的应用程序的显示空间定位点。</span><span class="sxs-lookup"><span data-stu-id="c810c-221">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="c810c-222">您必须单击更新按钮以获取和刷新的定位点。</span><span class="sxs-lookup"><span data-stu-id="c810c-222">You must click the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="c810c-223">**显示详细信息**:显示分发位置、 头旋转的四元数和设备源向量实时变化。</span><span class="sxs-lookup"><span data-stu-id="c810c-223">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="c810c-224">**全屏幕按钮**:在全屏幕模式下显示三维视图。</span><span class="sxs-lookup"><span data-stu-id="c810c-224">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="c810c-225">按 ESC 键可退出全屏视图。</span><span class="sxs-lookup"><span data-stu-id="c810c-225">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="c810c-226">**显示重新构造**:单击或点击**更新**以显示最新空间的映射网格从该设备。</span><span class="sxs-lookup"><span data-stu-id="c810c-226">**Surface reconstruction**: Click or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="c810c-227">完成全面检查可能需要一些时间，最多只需几秒钟。</span><span class="sxs-lookup"><span data-stu-id="c810c-227">A full pass may take some time to complete, up to a few seconds.</span></span> <span data-ttu-id="c810c-228">网格不会在 3D 视图中，会自动更新，你必须手动单击**更新**以从设备获取最新的网格。</span><span class="sxs-lookup"><span data-stu-id="c810c-228">The mesh does not update automatically in the 3D view, and you must manually click **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="c810c-229">单击**保存**将当前空间映射网格另存为您的 PC 上的 obj 文件。</span><span class="sxs-lookup"><span data-stu-id="c810c-229">Click **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="c810c-230">**空间的定位点**:单击更新以显示或更新活动的应用程序与空间标记。</span><span class="sxs-lookup"><span data-stu-id="c810c-230">**Spatial anchors**: Click Update to display or update the spatial anchors for the active app.</span></span>

### <a name="mixed-reality-capture"></a><span data-ttu-id="c810c-231">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="c810c-231">Mixed Reality Capture</span></span>

<span data-ttu-id="c810c-232">![在 Windows Device Portal 上 Microsoft HoloLens 混合的现实捕获页](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-232">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-233">*在 Windows Device Portal 上 Microsoft HoloLens 混合的现实捕获页*</span><span class="sxs-lookup"><span data-stu-id="c810c-233">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-234">使用“混合现实捕获”页面可保存 HoloLens 中的媒体流。</span><span class="sxs-lookup"><span data-stu-id="c810c-234">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="c810c-235">**设置**:控制通过检查以下设置捕获媒体流：</span><span class="sxs-lookup"><span data-stu-id="c810c-235">**Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="c810c-236">**全息**:捕获视频流中的 holographic 内容。</span><span class="sxs-lookup"><span data-stu-id="c810c-236">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="c810c-237">呈现全息图时使用的是单声道，而不是立体声。</span><span class="sxs-lookup"><span data-stu-id="c810c-237">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="c810c-238">**PV 照相机**:捕获照片/视频摄像机的视频流。</span><span class="sxs-lookup"><span data-stu-id="c810c-238">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="c810c-239">**Mic 音频**:捕获音频从麦克风阵列。</span><span class="sxs-lookup"><span data-stu-id="c810c-239">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="c810c-240">**应用音频**:从当前正在运行的应用捕获音频。</span><span class="sxs-lookup"><span data-stu-id="c810c-240">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="c810c-241">**从照相机呈现**:对齐捕获照片/视频摄像机视角为如果[支持的正在运行的应用](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)(仅 HoloLens 2)。</span><span class="sxs-lookup"><span data-stu-id="c810c-241">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="c810c-242">**实时预览质量**:选择屏幕分辨率、 帧速率和流式处理速率的实时预览。</span><span class="sxs-lookup"><span data-stu-id="c810c-242">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="c810c-243">单击或点击**实时预览**按钮可显示捕获流。</span><span class="sxs-lookup"><span data-stu-id="c810c-243">Click or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="c810c-244">**停止实时预览**停止捕获流式传输。</span><span class="sxs-lookup"><span data-stu-id="c810c-244">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="c810c-245">单击或点击**记录**开始录制混合现实流，使用指定的设置。</span><span class="sxs-lookup"><span data-stu-id="c810c-245">Click or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="c810c-246">**停止录制**结束记录并将其保存。</span><span class="sxs-lookup"><span data-stu-id="c810c-246">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="c810c-247">单击或点击**Take 照片**从捕获流才能静止图像。</span><span class="sxs-lookup"><span data-stu-id="c810c-247">Click or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="c810c-248">**视频和照片**:显示视频和照片捕获在设备上执行的列表。</span><span class="sxs-lookup"><span data-stu-id="c810c-248">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="c810c-249">有[限制同时 MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span><span class="sxs-lookup"><span data-stu-id="c810c-249">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="c810c-250">如果应用程序尝试访问照片/视频照相机，而 Windows Device Portal 录制视频时，将停止视频录制。</span><span class="sxs-lookup"><span data-stu-id="c810c-250">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="c810c-251">HoloLens 2 将不会停止录制视频，如果应用 acesses 照片/视频照相机 SharedReadOnly 模式。</span><span class="sxs-lookup"><span data-stu-id="c810c-251">HoloLens 2 will not stop recording video if the app acesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="c810c-252">如果应用正在主动使用照片/视频摄像机，就能够拍摄照片或视频记录 Windows Device Portal。</span><span class="sxs-lookup"><span data-stu-id="c810c-252">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="c810c-253">实时传送视频流：</span><span class="sxs-lookup"><span data-stu-id="c810c-253">Live streaming:</span></span>
>   * <span data-ttu-id="c810c-254">HoloLens （第 1 代） 将阻止应用在实时流式处理从 Windows Device Portal 访问照片/视频摄像机。</span><span class="sxs-lookup"><span data-stu-id="c810c-254">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="c810c-255">HoloLens （第 1 代） 将无法实时流，如果应用正在主动使用照片/视频摄像机。</span><span class="sxs-lookup"><span data-stu-id="c810c-255">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="c810c-256">HoloLens 2 将自动停止实时传送视频流应用程序尝试访问 ExclusiveControl 模式中的照片/视频照相机时。</span><span class="sxs-lookup"><span data-stu-id="c810c-256">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="c810c-257">HoloLens 2 可启动实时流，同时应用正在主动使用 PV 照相机。</span><span class="sxs-lookup"><span data-stu-id="c810c-257">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="c810c-258">性能跟踪</span><span class="sxs-lookup"><span data-stu-id="c810c-258">Performance Tracing</span></span>

<span data-ttu-id="c810c-259">![性能跟踪 Microsoft HoloLens 上 Windows Device Portal 中的页](images/windows-device-portal-performance-tracing-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-259">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-260">*性能跟踪 Microsoft HoloLens 上 Windows Device Portal 中的页*</span><span class="sxs-lookup"><span data-stu-id="c810c-260">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-261">捕获[Windows 性能记录器](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx)来自你 HoloLens (WPR) 跟踪。</span><span class="sxs-lookup"><span data-stu-id="c810c-261">Capture [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="c810c-262">**可用的配置文件**:从下拉列表中，然后单击或点击选择 WPR 配置文件**启动**要启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="c810c-262">**Available profiles**: Select the WPR profile from the dropdown, and click or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="c810c-263">**自定义配置文件**:单击或点击**浏览**WPR 配置文件选择你的 PC 中。</span><span class="sxs-lookup"><span data-stu-id="c810c-263">**Custom profiles**: Click or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="c810c-264">单击或点击**上载并启动**以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="c810c-264">Click or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="c810c-265">若要停止跟踪，请单击停止链接。</span><span class="sxs-lookup"><span data-stu-id="c810c-265">To stop the trace click on the stop link.</span></span> <span data-ttu-id="c810c-266">跟踪文件完成下载之前离开此页面。</span><span class="sxs-lookup"><span data-stu-id="c810c-266">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="c810c-267">可以打开捕获的 ETL 文件以供在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中进行分析。</span><span class="sxs-lookup"><span data-stu-id="c810c-267">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).</span></span>

### <a name="processes"></a><span data-ttu-id="c810c-268">进程</span><span class="sxs-lookup"><span data-stu-id="c810c-268">Processes</span></span>

<span data-ttu-id="c810c-269">![在 Microsoft HoloLens 上 Windows Device Portal 中进程页](images/windows-device-portal-running-processes-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-269">![Processes page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-270">*在 Microsoft HoloLens 上 Windows Device Portal 中进程页*</span><span class="sxs-lookup"><span data-stu-id="c810c-270">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-271">显示有关当前正在运行的进程的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c810c-271">Shows details about currently running processes.</span></span> <span data-ttu-id="c810c-272">这包括应用和系统进程。</span><span class="sxs-lookup"><span data-stu-id="c810c-272">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="c810c-273">系统性能</span><span class="sxs-lookup"><span data-stu-id="c810c-273">System Performance</span></span>

<span data-ttu-id="c810c-274">![Microsoft HoloLens 上 Windows Device Portal 中的系统性能页面](images/windows-device-portal-system-performance-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-274">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-275">*Microsoft HoloLens 上 Windows Device Portal 中的系统性能页面*</span><span class="sxs-lookup"><span data-stu-id="c810c-275">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-276">显示系统诊断信息的实时图形，如电源使用情况、帧速率和 CPU 负载。</span><span class="sxs-lookup"><span data-stu-id="c810c-276">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="c810c-277">可用的指标如下所示：</span><span class="sxs-lookup"><span data-stu-id="c810c-277">These are the available metrics:</span></span>
* <span data-ttu-id="c810c-278">**SoC power**:即时片上系统电源利用率，取一分钟的平均值</span><span class="sxs-lookup"><span data-stu-id="c810c-278">**SoC power**: Instantaneous system-on-chip power utilization, averaged over one minute</span></span>
* <span data-ttu-id="c810c-279">**系统电源**:即时系统电源利用率，取一分钟的平均值</span><span class="sxs-lookup"><span data-stu-id="c810c-279">**System power**: Instantaneous system power utilization, averaged over one minute</span></span>
* <span data-ttu-id="c810c-280">**帧速率**:每秒帧数达不到每秒，VBlanks 和连续丢失的 VBlanks</span><span class="sxs-lookup"><span data-stu-id="c810c-280">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="c810c-281">**GPU**:GPU 引擎使用率，可用的总百分比</span><span class="sxs-lookup"><span data-stu-id="c810c-281">**GPU**: GPU engine utilization, percent of total available</span></span>
* <span data-ttu-id="c810c-282">**CPU**： 可用的总百分比</span><span class="sxs-lookup"><span data-stu-id="c810c-282">**CPU**: percent of total available</span></span>
* <span data-ttu-id="c810c-283">**I/O**:读取和写入</span><span class="sxs-lookup"><span data-stu-id="c810c-283">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="c810c-284">**网络**：接收和发送</span><span class="sxs-lookup"><span data-stu-id="c810c-284">**Network**: Received and sent</span></span>
* <span data-ttu-id="c810c-285">**内存**:总计，在使用中，已提交，页面，和非页面缓冲</span><span class="sxs-lookup"><span data-stu-id="c810c-285">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="c810c-286">应用</span><span class="sxs-lookup"><span data-stu-id="c810c-286">Apps</span></span>

<span data-ttu-id="c810c-287">![在 Microsoft HoloLens 上 Windows Device Portal 中应用页](images/windows-device-portal-apps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-287">![Apps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-288">*在 Microsoft HoloLens 上 Windows Device Portal 中应用页*</span><span class="sxs-lookup"><span data-stu-id="c810c-288">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-289">管理在 HoloLens 安装的应用。</span><span class="sxs-lookup"><span data-stu-id="c810c-289">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="c810c-290">**已安装的应用**:删除并启动应用。</span><span class="sxs-lookup"><span data-stu-id="c810c-290">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="c810c-291">**正在运行的应用**:列出当前正在运行的应用。</span><span class="sxs-lookup"><span data-stu-id="c810c-291">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="c810c-292">**安装应用**:从您的计算机/网络上的文件夹中选择安装的应用的程序包。</span><span class="sxs-lookup"><span data-stu-id="c810c-292">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="c810c-293">**依赖项**:添加要安装的应用的依赖项。</span><span class="sxs-lookup"><span data-stu-id="c810c-293">**Dependency**: Add dependencies for the app you are going to install.</span></span>
* <span data-ttu-id="c810c-294">**部署**:将所选的应用 + 依赖项部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c810c-294">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="c810c-295">应用程序故障转储</span><span class="sxs-lookup"><span data-stu-id="c810c-295">App Crash Dumps</span></span>

<span data-ttu-id="c810c-296">![应用 Windows Device Portal 上 Microsoft HoloLens Crash Dumps 页](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-296">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-297">*应用 Windows Device Portal 上 Microsoft HoloLens Crash Dumps 页*</span><span class="sxs-lookup"><span data-stu-id="c810c-297">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-298">此页面允许你收集旁加载应用的故障转储。</span><span class="sxs-lookup"><span data-stu-id="c810c-298">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="c810c-299">检查**启用崩溃转储**你想要收集崩溃转储每个应用对应的复选框。</span><span class="sxs-lookup"><span data-stu-id="c810c-299">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="c810c-300">返回到此页面可收集故障转储。</span><span class="sxs-lookup"><span data-stu-id="c810c-300">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="c810c-301">转储文件可能很[Visual Studio 中打开以进行调试](https://msdn.microsoft.com/library/d5zhxt22.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c810c-301">Dump files can be [opened in Visual Studio for debugging](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="c810c-302">文件资源管理器</span><span class="sxs-lookup"><span data-stu-id="c810c-302">File Explorer</span></span>

<span data-ttu-id="c810c-303">![在 Microsoft HoloLens 上 Windows Device Portal 中的文件资源管理器页](images/fileexplorer-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-303">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/fileexplorer-1000px.png)</span></span><br>
<span data-ttu-id="c810c-304">*在 Microsoft HoloLens 上 Windows Device Portal 中的文件资源管理器页*</span><span class="sxs-lookup"><span data-stu-id="c810c-304">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-305">使用文件资源管理器来浏览、 上载和下载文件。</span><span class="sxs-lookup"><span data-stu-id="c810c-305">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="c810c-306">您可以处理和本地存储文件夹中文档文件夹，图片文件夹中，从 Visual Studio 或设备门户部署的应用程序的文件。</span><span class="sxs-lookup"><span data-stu-id="c810c-306">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="c810c-307">展台模式</span><span class="sxs-lookup"><span data-stu-id="c810c-307">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="c810c-308">展台模式时才可以使用[Microsoft HoloLens 商业套件](commercial-features.md)。</span><span class="sxs-lookup"><span data-stu-id="c810c-308">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](commercial-features.md).</span></span>

<span data-ttu-id="c810c-309">请检查[在展台模式下设置了 HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803)有关启用通过 Windows Device Portal 展台模式的最新说明 Windows IT 专业人员中心中的文章。</span><span class="sxs-lookup"><span data-stu-id="c810c-309">Please check the [Set up HoloLens in kiosk mode](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="c810c-310">日志记录</span><span class="sxs-lookup"><span data-stu-id="c810c-310">Logging</span></span>

<span data-ttu-id="c810c-311">![Microsoft HoloLens 上 Windows Device Portal 中的日志记录页](images/windows-device-portal-logging-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-311">![Logging page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-312">*Microsoft HoloLens 上 Windows Device Portal 中的日志记录页*</span><span class="sxs-lookup"><span data-stu-id="c810c-312">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-313">管理实时事件跟踪 Windows (ETW) 在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="c810c-313">Manages realtime Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="c810c-314">检查**隐藏提供程序**以显示**事件**仅列出。</span><span class="sxs-lookup"><span data-stu-id="c810c-314">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="c810c-315">**注册的提供程序**:选择 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="c810c-315">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="c810c-316">跟踪级别是以下值之一：</span><span class="sxs-lookup"><span data-stu-id="c810c-316">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="c810c-317">异常退出或终止</span><span class="sxs-lookup"><span data-stu-id="c810c-317">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="c810c-318">严重错误</span><span class="sxs-lookup"><span data-stu-id="c810c-318">Severe errors</span></span>
   3. <span data-ttu-id="c810c-319">警告</span><span class="sxs-lookup"><span data-stu-id="c810c-319">Warnings</span></span>
   4. <span data-ttu-id="c810c-320">非错误警告</span><span class="sxs-lookup"><span data-stu-id="c810c-320">Non-error warnings</span></span>

<span data-ttu-id="c810c-321">单击或点击**启用**以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="c810c-321">Click or tap **Enable** to start tracing.</span></span> <span data-ttu-id="c810c-322">提供程序将添加到**已启用的提供程序**下拉列表。</span><span class="sxs-lookup"><span data-stu-id="c810c-322">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="c810c-323">**自定义提供程序**:选择自定义的 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="c810c-323">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="c810c-324">根据其 GUDI 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="c810c-324">Identify the provider by its GUID.</span></span> <span data-ttu-id="c810c-325">不要在 GUID 中包含括号。</span><span class="sxs-lookup"><span data-stu-id="c810c-325">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="c810c-326">**已启用提供程序**:列出了已启用提供程序。</span><span class="sxs-lookup"><span data-stu-id="c810c-326">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="c810c-327">从下拉列表中选择一个提供程序，然后单击或点击**禁用**来停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="c810c-327">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="c810c-328">单击或点击**全部停止**来暂停所有跟踪。</span><span class="sxs-lookup"><span data-stu-id="c810c-328">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="c810c-329">**提供程序历史记录**:显示当前会话过程中启用 ETW 提供程序。</span><span class="sxs-lookup"><span data-stu-id="c810c-329">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="c810c-330">单击或点击**启用**来激活已禁用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="c810c-330">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="c810c-331">单击或点击**清除**来清除历史记录。</span><span class="sxs-lookup"><span data-stu-id="c810c-331">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="c810c-332">**事件**:列出了从表格格式中的所选提供程序的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="c810c-332">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="c810c-333">此表将实时更新。</span><span class="sxs-lookup"><span data-stu-id="c810c-333">This table is updated in real time.</span></span> <span data-ttu-id="c810c-334">下表中，单击**清除**按钮以从表中删除所有 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="c810c-334">Beneath the table, click on the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="c810c-335">这不会禁用任何提供程序。</span><span class="sxs-lookup"><span data-stu-id="c810c-335">This does not disable any providers.</span></span> <span data-ttu-id="c810c-336">你可以单击**保存到文件**来将当前收集的 ETW 事件本地导出到 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="c810c-336">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="c810c-337">**筛选器**:可用于筛选通过 ID、 关键字、 级别、 提供程序名称、 任务名称或文本收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="c810c-337">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="c810c-338">可以将多个条件组合在一起：</span><span class="sxs-lookup"><span data-stu-id="c810c-338">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="c810c-339">对于条件应用到相同属性的事件可以满足这些条件的任何一个显示。</span><span class="sxs-lookup"><span data-stu-id="c810c-339">For criteria applying to the same property - events can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="c810c-340">条件将应用于不同的属性的事件必须满足所有条件</span><span class="sxs-lookup"><span data-stu-id="c810c-340">For criteria applying to different property - events must satisfy all of the criteria</span></span>

<span data-ttu-id="c810c-341">例如，您可以指定的条件 *（任务名称包含 Foo 或栏） 和 （文本包含 error 或警告）*</span><span class="sxs-lookup"><span data-stu-id="c810c-341">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="c810c-342">模拟</span><span class="sxs-lookup"><span data-stu-id="c810c-342">Simulation</span></span>

<span data-ttu-id="c810c-343">![Microsoft HoloLens 上 Windows Device Portal 中的模拟页面](images/windows-device-portal-simulation-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-343">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-344">*Microsoft HoloLens 上 Windows Device Portal 中的模拟页面*</span><span class="sxs-lookup"><span data-stu-id="c810c-344">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-345">允许你记录和播放用于测试的输入数据。</span><span class="sxs-lookup"><span data-stu-id="c810c-345">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="c810c-346">**捕获聊天室**:用于下载模拟的聊天室文件，其中包含用户的环境空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="c810c-346">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="c810c-347">命名空间，然后单击**捕获**将数据保存为您的 PC 上的.xef 文件。</span><span class="sxs-lookup"><span data-stu-id="c810c-347">Name the room and then click **Capture** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="c810c-348">此房间文件可以加载到 HoloLens 仿真器中。</span><span class="sxs-lookup"><span data-stu-id="c810c-348">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="c810c-349">**录制**:检查流记录、 命名录制，然后单击或点击**记录**开始重新编码。</span><span class="sxs-lookup"><span data-stu-id="c810c-349">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="c810c-350">通过在 HoloLens 执行的操作，然后依次**停止**将数据保存为您的 PC 上的.xef 文件。</span><span class="sxs-lookup"><span data-stu-id="c810c-350">Perform actions with your HoloLens and then click **Stop** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="c810c-351">可以在 HoloLens 仿真器或设备上加载此文件。</span><span class="sxs-lookup"><span data-stu-id="c810c-351">This file can be loaded on the HoloLens emulator or device.</span></span>
* <span data-ttu-id="c810c-352">**播放**:单击或点击**上传录制**从您的 PC 选择 xef 文件并将数据发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c810c-352">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="c810c-353">**控件模式**:选择**默认**或**模拟**从下拉列表中，然后单击或点击**设置**按钮以选择在 HoloLens 上的模式。</span><span class="sxs-lookup"><span data-stu-id="c810c-353">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="c810c-354">相反，选择“模拟”会禁用 HoloLens 上的真实传感器，并使用已上载的模拟数据。</span><span class="sxs-lookup"><span data-stu-id="c810c-354">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="c810c-355">如果切换到“模拟”，HoloLens 将不会响应真实用户，除非切换回“默认”。</span><span class="sxs-lookup"><span data-stu-id="c810c-355">If you switch to "Simulation", your HoloLens will not respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="c810c-356">网络</span><span class="sxs-lookup"><span data-stu-id="c810c-356">Networking</span></span>

<span data-ttu-id="c810c-357">![Microsoft HoloLens 上 Windows Device Portal 中的网络页](images/windows-device-portal-networking-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-357">![Networking page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-358">*Microsoft HoloLens 上 Windows Device Portal 中的网络页*</span><span class="sxs-lookup"><span data-stu-id="c810c-358">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-359">管理在 HoloLens 上的 Wi-fi 连接。</span><span class="sxs-lookup"><span data-stu-id="c810c-359">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="c810c-360">**WiFi 适配器**:通过使用下拉控件选择 Wi-fi 适配器和配置文件。</span><span class="sxs-lookup"><span data-stu-id="c810c-360">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="c810c-361">单击或点击**Connect**以使用所选的适配器。</span><span class="sxs-lookup"><span data-stu-id="c810c-361">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="c810c-362">**可用网络**:列出了 HoloLens 可以连接到 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="c810c-362">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="c810c-363">单击或点击**刷新**更新列表。</span><span class="sxs-lookup"><span data-stu-id="c810c-363">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="c810c-364">**IP 配置**:显示的 IP 地址和网络连接的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="c810c-364">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="c810c-365">虚拟输入</span><span class="sxs-lookup"><span data-stu-id="c810c-365">Virtual Input</span></span>

<span data-ttu-id="c810c-366">![Microsoft HoloLens 上 Windows Device Portal 中的虚拟输入页](images/windows-device-portal-virtual-input-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c810c-366">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)</span></span><br>
<span data-ttu-id="c810c-367">*Microsoft HoloLens 上 Windows Device Portal 中的虚拟输入页*</span><span class="sxs-lookup"><span data-stu-id="c810c-367">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="c810c-368">将键盘输入从远程计算机发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c810c-368">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="c810c-369">单击或点击的区域下**虚拟键盘**若要启用到 HoloLens 发送击键。</span><span class="sxs-lookup"><span data-stu-id="c810c-369">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="c810c-370">在键入**输入文本**文本框中，然后单击或点击**发送**将击键发送到活动的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c810c-370">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="c810c-371">设备门户 REST API</span><span class="sxs-lookup"><span data-stu-id="c810c-371">Device Portal REST API's</span></span>

<span data-ttu-id="c810c-372">设备门户中的所有内容之上构建[REST API](device-portal-api-reference.md) ，您将可以选择使用，来访问数据，并以编程方式控制你的设备。</span><span class="sxs-lookup"><span data-stu-id="c810c-372">Everything in the device portal is built on top of [REST API's](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>
