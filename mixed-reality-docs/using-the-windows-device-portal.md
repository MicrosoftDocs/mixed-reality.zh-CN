---
title: 使用 Windows 设备门户
description: 通过用于 HoloLens 的 Windows 设备门户，你可以通过 Wi-fi 或 USB 远程配置和管理你的设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包含许多工具，可帮助你管理 HoloLens 并调试和优化你的应用程序。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 设备门户、HoloLens
ms.openlocfilehash: 9bb8116330d88c532b955ef497d29fe98c86fddb
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182017"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="e76a1-106">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="e76a1-106">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="e76a1-107">功能</span><span class="sxs-lookup"><span data-stu-id="e76a1-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="e76a1-108"><a href="hololens-hardware-details.md">HoloLens（第一代）</a></span><span class="sxs-lookup"><span data-stu-id="e76a1-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="e76a1-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e76a1-109">HoloLens 2</span></span></th><th style="width:150px"><span data-ttu-id="e76a1-110"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="e76a1-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e76a1-111">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="e76a1-111">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="e76a1-112">✔️</span><span class="sxs-lookup"><span data-stu-id="e76a1-112">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e76a1-113">✔️</span><span class="sxs-lookup"><span data-stu-id="e76a1-113">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="e76a1-114">通过用于 HoloLens 的 Windows 设备门户，你可以通过 Wi-fi 或 USB 远程配置和管理你的设备。</span><span class="sxs-lookup"><span data-stu-id="e76a1-114">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="e76a1-115">Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。</span><span class="sxs-lookup"><span data-stu-id="e76a1-115">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="e76a1-116">设备门户包含许多工具，可帮助你管理 HoloLens 并调试和优化你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e76a1-116">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="e76a1-117">本文档专门介绍适用于 HoloLens 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="e76a1-117">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="e76a1-118">若要使用适用于桌面的 Windows 设备门户（包括 Windows Mixed Reality），请参阅[Windows 设备门户概述](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="e76a1-118">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="e76a1-119">将 HoloLens 设置为使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="e76a1-119">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="e76a1-120">打开 HoloLens 的电源，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="e76a1-120">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="e76a1-121">在 HoloLens 上执行 HoloLens2 或[布隆](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)的[启动笔势](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)（第一代）以启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="e76a1-121">Perform the [Start gesture](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) for HoloLens2 or [Bloom](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (1st Gen) to launch the main menu.</span></span> 
3. <span data-ttu-id="e76a1-122">查看 "**设置**" 磁贴，并在 hololens （第一代）上执行 "[轻敲](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)" 手势，或在 hololens 2 上通过[触摸或使用手](https://docs.microsoft.com/hololens/hololens2-basic-usage)中选择它。</span><span class="sxs-lookup"><span data-stu-id="e76a1-122">Gaze at the **Settings** tile and perform the [air-tap](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) gesture on HoloLens (1st Gen) or select it on HoloLens 2 by [touching it or using a Hand ray](https://docs.microsoft.com/hololens/hololens2-basic-usage).</span></span> 
4. <span data-ttu-id="e76a1-123">选择“更新”菜单项。</span><span class="sxs-lookup"><span data-stu-id="e76a1-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="e76a1-124">选择“面向开发人员”菜单项。</span><span class="sxs-lookup"><span data-stu-id="e76a1-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="e76a1-125">启用“开发人员模式”。</span><span class="sxs-lookup"><span data-stu-id="e76a1-125">Enable **Developer Mode**.</span></span>
7. <span data-ttu-id="e76a1-126">[向下滚动](gaze-and-commit.md#composite-gestures)并启用**设备门户**。</span><span class="sxs-lookup"><span data-stu-id="e76a1-126">[Scroll down](gaze-and-commit.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="e76a1-127">如果要设置 Windows 设备门户，以便可以通过 USB 或 Wi-fi 将应用部署到此 HoloLens，请单击 "**配对**" 以[生成配对 PIN](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e76a1-127">If you are setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, click **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="e76a1-128">在第一次部署过程中，将 "设置" 应用保留在 "PIN" 弹出窗口中，直到输入到 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="e76a1-128">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

   ![在 Windows 全息版的设置应用中启用开发人员模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="e76a1-130">通过 Wi-fi 连接</span><span class="sxs-lookup"><span data-stu-id="e76a1-130">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="e76a1-131">[将 HoloLens 连接到 wi-fi](connecting-to-wi-fi-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="e76a1-131">[Connect your HoloLens to Wi-Fi](connecting-to-wi-fi-on-hololens.md).</span></span>
2. <span data-ttu-id="e76a1-132">查找设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e76a1-132">Look up your device's IP address.</span></span>
   * <span data-ttu-id="e76a1-133">在 "**设置" > Network & > > Internet**"下的" 设置 "中找到设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e76a1-133">Find the IP address on the device under **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
3. <span data-ttu-id="e76a1-134">从电脑上的 web 浏览器中转到 https：//< YOUR_HOLOLENS_IP_ADDRESS ></span><span class="sxs-lookup"><span data-stu-id="e76a1-134">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="e76a1-135">浏览器将显示以下消息： "此网站的安全证书有问题"。</span><span class="sxs-lookup"><span data-stu-id="e76a1-135">The browser will display the following message: "There’s a problem with this website’s security certificate".</span></span> <span data-ttu-id="e76a1-136">由于颁发给设备门户的证书是测试证书，因此会显示上述消息。</span><span class="sxs-lookup"><span data-stu-id="e76a1-136">This happens because the certificate which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="e76a1-137">你可以暂时忽略此证书错误并继续。</span><span class="sxs-lookup"><span data-stu-id="e76a1-137">You can ignore this certificate error for now and proceed.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="e76a1-138">通过 USB 连接</span><span class="sxs-lookup"><span data-stu-id="e76a1-138">Connecting over USB</span></span>

1. <span data-ttu-id="e76a1-139">[安装这些工具](install-the-tools.md)，确保你的 Visual Studio Update 1 具有安装在你的电脑上的 Windows 10 开发人员工具。</span><span class="sxs-lookup"><span data-stu-id="e76a1-139">[Install the tools](install-the-tools.md) to make sure you have Visual Studio Update 1 with the Windows 10 developer tools installed on your PC.</span></span> <span data-ttu-id="e76a1-140">这支持 USB 连接。</span><span class="sxs-lookup"><span data-stu-id="e76a1-140">This enables USB connectivity.</span></span>
2. <span data-ttu-id="e76a1-141">使用微型 USB 电缆将 HoloLens 连接到电脑。</span><span class="sxs-lookup"><span data-stu-id="e76a1-141">Connect your HoloLens to your PC with a micro-USB cable.</span></span>
3. <span data-ttu-id="e76a1-142">在电脑上的 web 浏览器中转到[https://127.0.0.1:10080](https://127.0.0.1:10080)。</span><span class="sxs-lookup"><span data-stu-id="e76a1-142">From a web browser on your PC, go to [https://127.0.0.1:10080](https://127.0.0.1:10080).</span></span>

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="e76a1-143">连接到模拟器</span><span class="sxs-lookup"><span data-stu-id="e76a1-143">Connecting to an emulator</span></span>

<span data-ttu-id="e76a1-144">也可以将设备门户与仿真器结合使用。</span><span class="sxs-lookup"><span data-stu-id="e76a1-144">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="e76a1-145">若要连接到设备门户，请使用[工具栏](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="e76a1-145">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="e76a1-146">单击此图标： ![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**：在模拟器中打开用于 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="e76a1-146">Click on this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="e76a1-147">创建用户名和密码</span><span class="sxs-lookup"><span data-stu-id="e76a1-147">Creating a Username and Password</span></span>

<span data-ttu-id="e76a1-148">![设置对 Windows 设备门户的访问权限](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-148">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-149">*设置对 Windows 设备门户的访问*</span><span class="sxs-lookup"><span data-stu-id="e76a1-149">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="e76a1-150">首次连接到 HoloLens 上的设备门户时，需要创建用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="e76a1-150">The first time you connect to the Device Portal on your HoloLens, you will need to create a username and password.</span></span>
1. <span data-ttu-id="e76a1-151">在电脑上的 Web 浏览器中，输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e76a1-151">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="e76a1-152">将打开“设置访问”页面。</span><span class="sxs-lookup"><span data-stu-id="e76a1-152">The Set up access page opens.</span></span>
2. <span data-ttu-id="e76a1-153">单击或点击 "**请求 pin** "，并查看 HoloLens 显示以获取生成的 pin。</span><span class="sxs-lookup"><span data-stu-id="e76a1-153">Click or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="e76a1-154">在 "设备" 文本框中**显示的 pin**中输入 pin。</span><span class="sxs-lookup"><span data-stu-id="e76a1-154">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="e76a1-155">输入将用于连接到设备门户的用户名。</span><span class="sxs-lookup"><span data-stu-id="e76a1-155">Enter the user name you will use to connect to the Device Portal.</span></span> <span data-ttu-id="e76a1-156">无需使用 Microsoft 帐户 (MSA) 名称或域名作为用户名。</span><span class="sxs-lookup"><span data-stu-id="e76a1-156">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="e76a1-157">输入密码并进行确认。</span><span class="sxs-lookup"><span data-stu-id="e76a1-157">Enter a password and confirm it.</span></span> <span data-ttu-id="e76a1-158">密码长度必须至少为七个字符。</span><span class="sxs-lookup"><span data-stu-id="e76a1-158">The password must be at least seven characters in length.</span></span> <span data-ttu-id="e76a1-159">无需使用 MSA 密码或域密码作为密码。</span><span class="sxs-lookup"><span data-stu-id="e76a1-159">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="e76a1-160">单击 "**配对**" 以连接到 HoloLens 上的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="e76a1-160">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="e76a1-161">如果你想要随时更改此用户名或密码，可以通过以下方式来重复此过程：访问设备安全页：通过导航到： https：//< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm。</span><span class="sxs-lookup"><span data-stu-id="e76a1-161">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="e76a1-162">安全证书</span><span class="sxs-lookup"><span data-stu-id="e76a1-162">Security certificate</span></span>

<span data-ttu-id="e76a1-163">如果你在浏览器中看到“证书错误”，可以通过创建与该设备的信任关系来修复该错误。</span><span class="sxs-lookup"><span data-stu-id="e76a1-163">If you are see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="e76a1-164">每个 HoloLens 会生成唯一的自签名证书以供其 SSL 连接使用。</span><span class="sxs-lookup"><span data-stu-id="e76a1-164">Each HoloLens generates a unique self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="e76a1-165">默认情况下，此证书不受电脑的 Web 浏览器信任，因此你可能会看到“证书错误”。</span><span class="sxs-lookup"><span data-stu-id="e76a1-165">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="e76a1-166">通过从你的 HoloLens 下载此证书（借助 USB 或信任的 WLAN 网络）并在你的电脑上信任该证书，可以安全地连接到设备。</span><span class="sxs-lookup"><span data-stu-id="e76a1-166">By downloading this certificate from your HoloLens (over USB or a Wi-Fi network you trust) and trusting it on your PC, you can securely connect to your device.</span></span>
1. <span data-ttu-id="e76a1-167">**请确保使用的是安全网络（USB 或你信任的 Wi-fi 网络）。**</span><span class="sxs-lookup"><span data-stu-id="e76a1-167">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="e76a1-168">从设备门户上的 "安全性" 页下载此设备的证书。</span><span class="sxs-lookup"><span data-stu-id="e76a1-168">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="e76a1-169">导航到： https：//< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="e76a1-169">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
3. <span data-ttu-id="e76a1-170">在电脑上的 "受信任的根证书颁发机构" 存储中安装证书。</span><span class="sxs-lookup"><span data-stu-id="e76a1-170">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="e76a1-171">在 Windows 菜单中，键入： "管理计算机证书" 并启动小程序。</span><span class="sxs-lookup"><span data-stu-id="e76a1-171">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="e76a1-172">展开 "**受信任的根证书颁发机构**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e76a1-172">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="e76a1-173">单击 "**证书**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e76a1-173">Click on the **Certificates** folder.</span></span>
   * <span data-ttu-id="e76a1-174">从“操作”菜单中，依次选择“所有任务”&gt;“导入...”</span><span class="sxs-lookup"><span data-stu-id="e76a1-174">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="e76a1-175">使用从设备门户下载的证书文件，完成“证书导入向导”。</span><span class="sxs-lookup"><span data-stu-id="e76a1-175">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="e76a1-176">重新启动浏览器。</span><span class="sxs-lookup"><span data-stu-id="e76a1-176">Restart the browser.</span></span>

## <a name="device-portal-pages"></a><span data-ttu-id="e76a1-177">设备门户页面</span><span class="sxs-lookup"><span data-stu-id="e76a1-177">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="e76a1-178">“主页”</span><span class="sxs-lookup"><span data-stu-id="e76a1-178">Home</span></span>

<span data-ttu-id="e76a1-179">![Microsoft HoloLens 上的 Windows 设备门户主页](images/windows-device-portal-home-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-179">![Windows Device Portal home page on Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-180">*Microsoft HoloLens 上的 Windows 设备门户主页*</span><span class="sxs-lookup"><span data-stu-id="e76a1-180">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-181">设备门户会话从主页开始。</span><span class="sxs-lookup"><span data-stu-id="e76a1-181">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="e76a1-182">可从主页的左侧导航栏访问其他页面。</span><span class="sxs-lookup"><span data-stu-id="e76a1-182">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="e76a1-183">主页顶部的工具栏提供对常用状态和功能的访问。</span><span class="sxs-lookup"><span data-stu-id="e76a1-183">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="e76a1-184">**联机**：指示设备是否已连接到 WLAN。</span><span class="sxs-lookup"><span data-stu-id="e76a1-184">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="e76a1-185">**关机**：关闭设备。</span><span class="sxs-lookup"><span data-stu-id="e76a1-185">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="e76a1-186">**重启**：重新接通设备的电源。</span><span class="sxs-lookup"><span data-stu-id="e76a1-186">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="e76a1-187">**安全**：打开“设备安全”页面。</span><span class="sxs-lookup"><span data-stu-id="e76a1-187">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="e76a1-188">**冷**：指示设备的温度。</span><span class="sxs-lookup"><span data-stu-id="e76a1-188">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="e76a1-189">**交流电源**：指示设备是否已接通电源并正在充电。</span><span class="sxs-lookup"><span data-stu-id="e76a1-189">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="e76a1-190">**帮助**：打开 REST 接口文档页面。</span><span class="sxs-lookup"><span data-stu-id="e76a1-190">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="e76a1-191">主页将显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="e76a1-191">The home page shows the following info:</span></span>
* <span data-ttu-id="e76a1-192">**设备状态：** 监视设备的运行状况，并报告严重错误。</span><span class="sxs-lookup"><span data-stu-id="e76a1-192">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="e76a1-193">**Windows 信息：** 显示 HoloLens 的名称和当前安装的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="e76a1-193">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="e76a1-194">**首选项**部分包含以下设置：</span><span class="sxs-lookup"><span data-stu-id="e76a1-194">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="e76a1-195">**IPD**：设置瞳孔间距 (IPD)，它是在用户直视前方时两个瞳孔中心之间的距离，以毫米为单位。</span><span class="sxs-lookup"><span data-stu-id="e76a1-195">**IPD**: Sets the interpupillary distance (IPD), which is the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="e76a1-196">该设置将立即生效。</span><span class="sxs-lookup"><span data-stu-id="e76a1-196">The setting takes effect immediately.</span></span> <span data-ttu-id="e76a1-197">在设置你的设备时，会自动计算该默认值。</span><span class="sxs-lookup"><span data-stu-id="e76a1-197">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="e76a1-198">**设备名称**：为 HoloLens 分配一个名称。</span><span class="sxs-lookup"><span data-stu-id="e76a1-198">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="e76a1-199">更改此值后，必须重新启动设备才能使该值生效。</span><span class="sxs-lookup"><span data-stu-id="e76a1-199">You must reboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="e76a1-200">单击 "**保存**" 后，对话会询问你是要立即重启设备还是稍后重新启动。</span><span class="sxs-lookup"><span data-stu-id="e76a1-200">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="e76a1-201">**睡眠设置**：当设备已接通电源并使用电池时，设置该设备进入睡眠状态之前要等待的时长。</span><span class="sxs-lookup"><span data-stu-id="e76a1-201">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="e76a1-202">3D 视图</span><span class="sxs-lookup"><span data-stu-id="e76a1-202">3D View</span></span>

<span data-ttu-id="e76a1-203">Microsoft HoloLens 上 Windows 设备门户中 ![3D 视图页面](images/3dview-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-203">![3D View page in Windows Device Portal on Microsoft HoloLens](images/3dview-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-204">*Microsoft HoloLens 上 Windows 设备门户中的3D 视图页面*</span><span class="sxs-lookup"><span data-stu-id="e76a1-204">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-205">使用“3D 视图”页面可查看 HoloLens 感知周围环境的方式。</span><span class="sxs-lookup"><span data-stu-id="e76a1-205">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="e76a1-206">使用鼠标即可导览该视图：</span><span class="sxs-lookup"><span data-stu-id="e76a1-206">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="e76a1-207">旋转：左键单击 + 鼠标;</span><span class="sxs-lookup"><span data-stu-id="e76a1-207">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="e76a1-208">平移：右键单击 + 鼠标;</span><span class="sxs-lookup"><span data-stu-id="e76a1-208">Pan: right click + mouse;</span></span>
* <span data-ttu-id="e76a1-209">Zoom：鼠标滚动。</span><span class="sxs-lookup"><span data-stu-id="e76a1-209">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="e76a1-210">**跟踪选项**</span><span class="sxs-lookup"><span data-stu-id="e76a1-210">**Tracking options**</span></span>
   * <span data-ttu-id="e76a1-211">通过检查**强制视觉对象跟踪**打开连续的视觉跟踪。</span><span class="sxs-lookup"><span data-stu-id="e76a1-211">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="e76a1-212">**暂停**停止视觉对象跟踪。</span><span class="sxs-lookup"><span data-stu-id="e76a1-212">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="e76a1-213">**视图选项**：在三维视图上设置选项：</span><span class="sxs-lookup"><span data-stu-id="e76a1-213">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="e76a1-214">**跟踪**：指示视觉跟踪是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="e76a1-214">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="e76a1-215">**显示地面**：显示方格形式的地平面。</span><span class="sxs-lookup"><span data-stu-id="e76a1-215">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="e76a1-216">**显示锥体**：显示视锥。</span><span class="sxs-lookup"><span data-stu-id="e76a1-216">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="e76a1-217">**显示防抖动平面**：显示 HoloLens 用于稳定动作的平面。</span><span class="sxs-lookup"><span data-stu-id="e76a1-217">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="e76a1-218">**显示网格**：显示表示你的环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="e76a1-218">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="e76a1-219">**显示空间锚**：显示活动应用的空间锚。</span><span class="sxs-lookup"><span data-stu-id="e76a1-219">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="e76a1-220">必须单击 "更新" 按钮，才能获取和刷新锚。</span><span class="sxs-lookup"><span data-stu-id="e76a1-220">You must click the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="e76a1-221">**显示详细信息**：实时显示手的位置、头部旋转四元数和设备原点矢量的变化。</span><span class="sxs-lookup"><span data-stu-id="e76a1-221">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="e76a1-222">**“全屏”按钮**：以全屏模式显示 3D 视图。</span><span class="sxs-lookup"><span data-stu-id="e76a1-222">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="e76a1-223">按 ESC 键可退出全屏视图。</span><span class="sxs-lookup"><span data-stu-id="e76a1-223">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="e76a1-224">**Surface 重构**：单击或点击 "**更新**" 以显示设备的最新空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="e76a1-224">**Surface reconstruction**: Click or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="e76a1-225">完成全面检查可能需要一些时间，最多只需几秒钟。</span><span class="sxs-lookup"><span data-stu-id="e76a1-225">A full pass may take some time to complete, up to a few seconds.</span></span> <span data-ttu-id="e76a1-226">网格不会在三维视图中自动更新，您必须手动单击 "**更新**" 以从设备获取最新的网格。</span><span class="sxs-lookup"><span data-stu-id="e76a1-226">The mesh does not update automatically in the 3D view, and you must manually click **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="e76a1-227">单击 "**保存**" 可将当前空间映射网格作为 obj 文件保存到电脑上。</span><span class="sxs-lookup"><span data-stu-id="e76a1-227">Click **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="e76a1-228">**空间锚**：单击 "更新" 可显示或更新活动应用的空间锚。</span><span class="sxs-lookup"><span data-stu-id="e76a1-228">**Spatial anchors**: Click Update to display or update the spatial anchors for the active app.</span></span>

### <a name="mixed-reality-capture"></a><span data-ttu-id="e76a1-229">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="e76a1-229">Mixed Reality Capture</span></span>

<span data-ttu-id="e76a1-230">Microsoft HoloLens 上 Windows 设备门户中 ![Mixed Reality 捕获页面](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-230">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-231">*Microsoft HoloLens 上 Windows 设备门户中的混合现实捕获页面*</span><span class="sxs-lookup"><span data-stu-id="e76a1-231">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-232">使用“混合现实捕获”页面可保存 HoloLens 中的媒体流。</span><span class="sxs-lookup"><span data-stu-id="e76a1-232">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="e76a1-233">**设置**：通过检查以下设置来控制捕获的媒体流：</span><span class="sxs-lookup"><span data-stu-id="e76a1-233">**Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="e76a1-234">**全息影像**：捕获视频流中的全息内容。</span><span class="sxs-lookup"><span data-stu-id="e76a1-234">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="e76a1-235">呈现全息图时使用的是单声道，而不是立体声。</span><span class="sxs-lookup"><span data-stu-id="e76a1-235">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="e76a1-236">**PV 相机**：捕获照片/视频相机中的视频流。</span><span class="sxs-lookup"><span data-stu-id="e76a1-236">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="e76a1-237">**麦克风音频**：捕获麦克风阵列中的音频。</span><span class="sxs-lookup"><span data-stu-id="e76a1-237">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="e76a1-238">**应用音频**：捕获当前正在运行的应用中的音频。</span><span class="sxs-lookup"><span data-stu-id="e76a1-238">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="e76a1-239">**从照相机渲染**：如果[正在运行的应用支持](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，则将捕获与照片/视频摄像机的透视图对齐：</span><span class="sxs-lookup"><span data-stu-id="e76a1-239">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="e76a1-240">**实时预览质量**：选择用于实时预览的屏幕分辨率、帧速率和流处理速率。</span><span class="sxs-lookup"><span data-stu-id="e76a1-240">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="e76a1-241">单击或点击 "**实时预览**" 按钮，以显示捕获流。</span><span class="sxs-lookup"><span data-stu-id="e76a1-241">Click or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="e76a1-242">**停止实时预览**停止捕获流。</span><span class="sxs-lookup"><span data-stu-id="e76a1-242">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="e76a1-243">单击或点击 "**记录**"，使用指定的设置开始记录混合现实流。</span><span class="sxs-lookup"><span data-stu-id="e76a1-243">Click or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="e76a1-244">**停止录制**将结束录制并保存。</span><span class="sxs-lookup"><span data-stu-id="e76a1-244">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="e76a1-245">单击或点击 "**拍摄照片**"，拍摄捕获流中的静止图像。</span><span class="sxs-lookup"><span data-stu-id="e76a1-245">Click or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="e76a1-246">**视频和照片**：显示在设备上捕获的视频和照片列表。</span><span class="sxs-lookup"><span data-stu-id="e76a1-246">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="e76a1-247">同时提供了一些[限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)：</span><span class="sxs-lookup"><span data-stu-id="e76a1-247">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="e76a1-248">如果应用在 Windows 设备门户录制视频时尝试访问 photo/视频摄像机，视频录制将停止。</span><span class="sxs-lookup"><span data-stu-id="e76a1-248">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="e76a1-249">如果应用访问带有 SharedReadOnly 模式的照片/视频摄像机，则 HoloLens 2 不会停止录制视频。</span><span class="sxs-lookup"><span data-stu-id="e76a1-249">HoloLens 2 will not stop recording video if the app accesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="e76a1-250">如果应用正在使用照片/视频摄像机，Windows 设备门户可以拍摄照片或录制视频。</span><span class="sxs-lookup"><span data-stu-id="e76a1-250">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="e76a1-251">实时流式处理：</span><span class="sxs-lookup"><span data-stu-id="e76a1-251">Live streaming:</span></span>
>   * <span data-ttu-id="e76a1-252">HoloLens （第一代）会阻止应用从 Windows 设备门户实时传送视频时访问照片/视频摄像机。</span><span class="sxs-lookup"><span data-stu-id="e76a1-252">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="e76a1-253">如果应用正在使用 photo/视频摄像机，则 HoloLens （第一代）将无法实时传输。</span><span class="sxs-lookup"><span data-stu-id="e76a1-253">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="e76a1-254">在应用尝试以 ExclusiveControl 模式访问照片/视频摄像机时，HoloLens 2 自动停止实时流式处理。</span><span class="sxs-lookup"><span data-stu-id="e76a1-254">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="e76a1-255">在应用主动使用 PV 摄像机时，HoloLens 2 可以启动实时流。</span><span class="sxs-lookup"><span data-stu-id="e76a1-255">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="e76a1-256">性能跟踪</span><span class="sxs-lookup"><span data-stu-id="e76a1-256">Performance Tracing</span></span>

<span data-ttu-id="e76a1-257">Microsoft HoloLens 上 Windows 设备门户中 ![性能跟踪页面](images/windows-device-portal-performance-tracing-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-257">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-258">*Microsoft HoloLens 上 Windows 设备门户中的 "性能跟踪" 页*</span><span class="sxs-lookup"><span data-stu-id="e76a1-258">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-259">从 HoloLens 捕获[Windows 性能记录器](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx)（"）跟踪。</span><span class="sxs-lookup"><span data-stu-id="e76a1-259">Capture [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="e76a1-260">**可用配置文件**：从下拉列表中选择 WPR 配置文件，然后单击或点击**开始**以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="e76a1-260">**Available profiles**: Select the WPR profile from the dropdown, and click or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="e76a1-261">**自定义配置文件**：单击或点击**浏览**以从电脑中选择 WPR 配置文件。</span><span class="sxs-lookup"><span data-stu-id="e76a1-261">**Custom profiles**: Click or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="e76a1-262">单击或点击**上载并启动**以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="e76a1-262">Click or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="e76a1-263">若要停止跟踪，请单击 "停止" 链接。</span><span class="sxs-lookup"><span data-stu-id="e76a1-263">To stop the trace click on the stop link.</span></span> <span data-ttu-id="e76a1-264">一直在此页上，直到跟踪文件下载完成。</span><span class="sxs-lookup"><span data-stu-id="e76a1-264">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="e76a1-265">可以打开捕获的 ETL 文件以供在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中进行分析。</span><span class="sxs-lookup"><span data-stu-id="e76a1-265">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).</span></span>

### <a name="processes"></a><span data-ttu-id="e76a1-266">进程</span><span class="sxs-lookup"><span data-stu-id="e76a1-266">Processes</span></span>

<span data-ttu-id="e76a1-267">Microsoft HoloLens 上 Windows 设备门户中 ![进程 "页面](images/windows-device-portal-running-processes-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-267">![Processes page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-268">*Microsoft HoloLens 上 Windows 设备门户中的 "进程" 页*</span><span class="sxs-lookup"><span data-stu-id="e76a1-268">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-269">显示有关当前正在运行的进程的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e76a1-269">Shows details about currently running processes.</span></span> <span data-ttu-id="e76a1-270">这包括应用和系统进程。</span><span class="sxs-lookup"><span data-stu-id="e76a1-270">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="e76a1-271">系统性能</span><span class="sxs-lookup"><span data-stu-id="e76a1-271">System Performance</span></span>

<span data-ttu-id="e76a1-272">Microsoft HoloLens 上 Windows 设备门户中 ![系统性能 "页面](images/windows-device-portal-system-performance-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-272">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-273">*Microsoft HoloLens 上 Windows 设备门户中的 "系统性能" 页*</span><span class="sxs-lookup"><span data-stu-id="e76a1-273">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-274">显示系统诊断信息的实时图形，如电源使用情况、帧速率和 CPU 负载。</span><span class="sxs-lookup"><span data-stu-id="e76a1-274">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="e76a1-275">可用的指标如下所示：</span><span class="sxs-lookup"><span data-stu-id="e76a1-275">These are the available metrics:</span></span>
* <span data-ttu-id="e76a1-276">**SoC 电源**：瞬时片上系统电源使用率，平均超过一分钟</span><span class="sxs-lookup"><span data-stu-id="e76a1-276">**SoC power**: Instantaneous system-on-chip power utilization, averaged over one minute</span></span>
* <span data-ttu-id="e76a1-277">**系统电源**：瞬时系统电源使用率，平均超过一分钟</span><span class="sxs-lookup"><span data-stu-id="e76a1-277">**System power**: Instantaneous system power utilization, averaged over one minute</span></span>
* <span data-ttu-id="e76a1-278">**帧速率**：每秒帧数、每秒丢失的垂直消隐数和连续丢失的垂直消隐数</span><span class="sxs-lookup"><span data-stu-id="e76a1-278">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="e76a1-279">**GPU**：GPU 引擎使用率、总可用量的百分比</span><span class="sxs-lookup"><span data-stu-id="e76a1-279">**GPU**: GPU engine utilization, percent of total available</span></span>
* <span data-ttu-id="e76a1-280">**CPU**：可用总数百分比</span><span class="sxs-lookup"><span data-stu-id="e76a1-280">**CPU**: percent of total available</span></span>
* <span data-ttu-id="e76a1-281">**I/O**：读取和写入</span><span class="sxs-lookup"><span data-stu-id="e76a1-281">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="e76a1-282">**网络**：已接收和已发送</span><span class="sxs-lookup"><span data-stu-id="e76a1-282">**Network**: Received and sent</span></span>
* <span data-ttu-id="e76a1-283">**内存**：总计、已用、已提交、分页和非分页</span><span class="sxs-lookup"><span data-stu-id="e76a1-283">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="e76a1-284">“应用”</span><span class="sxs-lookup"><span data-stu-id="e76a1-284">Apps</span></span>

<span data-ttu-id="e76a1-285">Microsoft HoloLens 上 Windows 设备门户中 ![应用 "页面](images/windows-device-portal-apps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-285">![Apps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-286">*Microsoft HoloLens 上 Windows 设备门户中的 "应用" 页*</span><span class="sxs-lookup"><span data-stu-id="e76a1-286">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-287">管理 HoloLens 上安装的应用。</span><span class="sxs-lookup"><span data-stu-id="e76a1-287">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="e76a1-288">**已安装的应用**：删除和启动应用。</span><span class="sxs-lookup"><span data-stu-id="e76a1-288">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="e76a1-289">**正在运行的应用**：列出当前正在运行的应用。</span><span class="sxs-lookup"><span data-stu-id="e76a1-289">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="e76a1-290">**安装应用**：从计算机/网络上的文件夹中选择要安装的应用包。</span><span class="sxs-lookup"><span data-stu-id="e76a1-290">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="e76a1-291">**依赖项**：为要安装的应用添加依赖项。</span><span class="sxs-lookup"><span data-stu-id="e76a1-291">**Dependency**: Add dependencies for the app you are going to install.</span></span>
* <span data-ttu-id="e76a1-292">**部署**：将所选应用程序和依赖项部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e76a1-292">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="e76a1-293">应用故障转储</span><span class="sxs-lookup"><span data-stu-id="e76a1-293">App Crash Dumps</span></span>

<span data-ttu-id="e76a1-294">Microsoft HoloLens 上 Windows 设备门户中 ![应用崩溃转储页面](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-294">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-295">*Microsoft HoloLens 上 Windows 设备门户中的应用故障转储页面*</span><span class="sxs-lookup"><span data-stu-id="e76a1-295">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-296">此页面允许你收集旁加载应用的故障转储。</span><span class="sxs-lookup"><span data-stu-id="e76a1-296">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="e76a1-297">对于要为其收集故障转储的每个应用，选中 "**已启用故障转储**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="e76a1-297">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="e76a1-298">返回到此页面可收集故障转储。</span><span class="sxs-lookup"><span data-stu-id="e76a1-298">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="e76a1-299">可[在 Visual Studio 中打开转储文件以进行调试](https://msdn.microsoft.com/library/d5zhxt22.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e76a1-299">Dump files can be [opened in Visual Studio for debugging](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="e76a1-300">“文件资源管理器”</span><span class="sxs-lookup"><span data-stu-id="e76a1-300">File Explorer</span></span>

<span data-ttu-id="e76a1-301">![Microsoft HoloLens 上 Windows 设备门户中的文件资源管理器页面](images/fileexplorer-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-301">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/fileexplorer-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-302">*Microsoft HoloLens 上 Windows 设备门户中的文件资源管理器页*</span><span class="sxs-lookup"><span data-stu-id="e76a1-302">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-303">使用文件资源管理器浏览、上传和下载文件。</span><span class="sxs-lookup"><span data-stu-id="e76a1-303">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="e76a1-304">对于从 Visual Studio 或设备门户部署的应用，可以在 "文档" 文件夹、"图片" 文件夹和 "本地存储文件夹" 中处理文件。</span><span class="sxs-lookup"><span data-stu-id="e76a1-304">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="e76a1-305">展台模式</span><span class="sxs-lookup"><span data-stu-id="e76a1-305">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="e76a1-306">展台模式仅适用于[Microsoft HoloLens 商业套件](commercial-features.md)。</span><span class="sxs-lookup"><span data-stu-id="e76a1-306">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](commercial-features.md).</span></span>

<span data-ttu-id="e76a1-307">有关通过 Windows 设备门户启用展台模式的最新说明，请参阅 Windows IT 专业人员中心中的在[展台模式下设置 HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 。</span><span class="sxs-lookup"><span data-stu-id="e76a1-307">Please check the [Set up HoloLens in kiosk mode](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="e76a1-308">日志记录</span><span class="sxs-lookup"><span data-stu-id="e76a1-308">Logging</span></span>

<span data-ttu-id="e76a1-309">Microsoft HoloLens 上 Windows 设备门户中 ![日志记录页面](images/windows-device-portal-logging-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-309">![Logging page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-310">*Microsoft HoloLens 上 Windows 设备门户中的 "日志记录" 页*</span><span class="sxs-lookup"><span data-stu-id="e76a1-310">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-311">管理 HoloLens 上 Windows （ETW）的实时事件跟踪。</span><span class="sxs-lookup"><span data-stu-id="e76a1-311">Manages realtime Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="e76a1-312">选中 "**隐藏提供程序**" 以仅显示**事件**列表。</span><span class="sxs-lookup"><span data-stu-id="e76a1-312">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="e76a1-313">**注册的提供程序**：选择 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="e76a1-313">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="e76a1-314">跟踪级别是以下值之一：</span><span class="sxs-lookup"><span data-stu-id="e76a1-314">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="e76a1-315">异常退出或终止</span><span class="sxs-lookup"><span data-stu-id="e76a1-315">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="e76a1-316">严重错误</span><span class="sxs-lookup"><span data-stu-id="e76a1-316">Severe errors</span></span>
   3. <span data-ttu-id="e76a1-317">警告</span><span class="sxs-lookup"><span data-stu-id="e76a1-317">Warnings</span></span>
   4. <span data-ttu-id="e76a1-318">非错误警告</span><span class="sxs-lookup"><span data-stu-id="e76a1-318">Non-error warnings</span></span>

<span data-ttu-id="e76a1-319">单击或点击**启用**以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="e76a1-319">Click or tap **Enable** to start tracing.</span></span> <span data-ttu-id="e76a1-320">提供程序将添加到**已启用的提供程序**下拉列表。</span><span class="sxs-lookup"><span data-stu-id="e76a1-320">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="e76a1-321">**自定义提供程序**：选择自定义 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="e76a1-321">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="e76a1-322">根据其 GUDI 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="e76a1-322">Identify the provider by its GUID.</span></span> <span data-ttu-id="e76a1-323">不要在 GUID 中包含括号。</span><span class="sxs-lookup"><span data-stu-id="e76a1-323">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="e76a1-324">**已启用的提供程序**：列出已启用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="e76a1-324">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="e76a1-325">从下拉列表中选择一个提供程序，然后单击或点击**禁用**来停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="e76a1-325">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="e76a1-326">单击或点击**全部停止**来暂停所有跟踪。</span><span class="sxs-lookup"><span data-stu-id="e76a1-326">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="e76a1-327">**提供程序历史记录**：显示已在当前会话期间启用的 ETW 提供程序。</span><span class="sxs-lookup"><span data-stu-id="e76a1-327">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="e76a1-328">单击或点击**启用**来激活已禁用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="e76a1-328">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="e76a1-329">单击或点击**清除**来清除历史记录。</span><span class="sxs-lookup"><span data-stu-id="e76a1-329">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="e76a1-330">**事件**：以表格的形式列出来自选定提供程序的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="e76a1-330">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="e76a1-331">此表将实时更新。</span><span class="sxs-lookup"><span data-stu-id="e76a1-331">This table is updated in real time.</span></span> <span data-ttu-id="e76a1-332">在表的下方，单击 "**清除**" 按钮，以从表中删除所有 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="e76a1-332">Beneath the table, click on the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="e76a1-333">这不会禁用任何提供程序。</span><span class="sxs-lookup"><span data-stu-id="e76a1-333">This does not disable any providers.</span></span> <span data-ttu-id="e76a1-334">你可以单击**保存到文件**来将当前收集的 ETW 事件本地导出到 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="e76a1-334">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="e76a1-335">**筛选器**：允许你筛选由 ID、关键字、级别、提供程序名称、任务名称或文本收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="e76a1-335">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="e76a1-336">可以将多个条件组合在一起：</span><span class="sxs-lookup"><span data-stu-id="e76a1-336">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="e76a1-337">对于应用到相同属性的条件，可以满足这些条件中的任何一个。</span><span class="sxs-lookup"><span data-stu-id="e76a1-337">For criteria applying to the same property - events can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="e76a1-338">适用于不同属性事件的条件必须满足所有条件</span><span class="sxs-lookup"><span data-stu-id="e76a1-338">For criteria applying to different property - events must satisfy all of the criteria</span></span>

<span data-ttu-id="e76a1-339">例如，你可以指定条件 *（任务名称包含 "Foo" 或 "Bar"）以及（文本包含 "错误" 或 "警告"）*</span><span class="sxs-lookup"><span data-stu-id="e76a1-339">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="e76a1-340">模拟</span><span class="sxs-lookup"><span data-stu-id="e76a1-340">Simulation</span></span>

<span data-ttu-id="e76a1-341">Microsoft HoloLens 上 Windows 设备门户中 ![模拟页面](images/windows-device-portal-simulation-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-341">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-342">*Microsoft HoloLens 上 Windows 设备门户中的模拟页面*</span><span class="sxs-lookup"><span data-stu-id="e76a1-342">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-343">允许你记录和播放用于测试的输入数据。</span><span class="sxs-lookup"><span data-stu-id="e76a1-343">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="e76a1-344">**捕获房间**：用于下载模拟房间文件，该文件包含用于用户周围环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="e76a1-344">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="e76a1-345">命名聊天室，然后单击 "**捕获**"，将数据以 xef 文件的形式保存在电脑上。</span><span class="sxs-lookup"><span data-stu-id="e76a1-345">Name the room and then click **Capture** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="e76a1-346">此房间文件可以加载到 HoloLens 仿真器中。</span><span class="sxs-lookup"><span data-stu-id="e76a1-346">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="e76a1-347">**记录**：检查要录制的流，为录制命名，然后单击或点击 "**记录**" 以开始重编码。</span><span class="sxs-lookup"><span data-stu-id="e76a1-347">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="e76a1-348">使用 HoloLens 执行操作，然后单击 "**停止**" 将数据作为 xef 文件保存在电脑上。</span><span class="sxs-lookup"><span data-stu-id="e76a1-348">Perform actions with your HoloLens and then click **Stop** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="e76a1-349">可以在 HoloLens 仿真器或设备上加载此文件。</span><span class="sxs-lookup"><span data-stu-id="e76a1-349">This file can be loaded on the HoloLens emulator or device.</span></span>
* <span data-ttu-id="e76a1-350">**播放**：单击或点击 "**上传记录**"，从电脑选择 xef 文件，并将数据发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e76a1-350">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="e76a1-351">**控制模式**：从下拉列表中选择 "**默认**" 或 "**模拟**"，然后单击或点击 "**设置**" 按钮以在 HoloLens 上选择模式。</span><span class="sxs-lookup"><span data-stu-id="e76a1-351">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="e76a1-352">相反，选择“模拟”会禁用 HoloLens 上的真实传感器，并使用已上载的模拟数据。</span><span class="sxs-lookup"><span data-stu-id="e76a1-352">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="e76a1-353">如果切换到“模拟”，HoloLens 将不会响应真实用户，除非切换回“默认”。</span><span class="sxs-lookup"><span data-stu-id="e76a1-353">If you switch to "Simulation", your HoloLens will not respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="e76a1-354">网络</span><span class="sxs-lookup"><span data-stu-id="e76a1-354">Networking</span></span>

<span data-ttu-id="e76a1-355">Microsoft HoloLens 上 Windows 设备门户中的 ![网络 "页面](images/windows-device-portal-networking-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-355">![Networking page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-356">*Microsoft HoloLens 上 Windows 设备门户中的 "网络" 页*</span><span class="sxs-lookup"><span data-stu-id="e76a1-356">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-357">管理 HoloLens 上的 Wi-fi 连接。</span><span class="sxs-lookup"><span data-stu-id="e76a1-357">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="e76a1-358">**WiFi 适配器**：使用下拉控件选择 wi-fi 适配器和配置文件。</span><span class="sxs-lookup"><span data-stu-id="e76a1-358">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="e76a1-359">单击或点击 "**连接**" 以使用所选适配器。</span><span class="sxs-lookup"><span data-stu-id="e76a1-359">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="e76a1-360">**可用网络**：列出了 HoloLens 可以连接到的 wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="e76a1-360">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="e76a1-361">单击或点击 "**刷新**" 以更新列表。</span><span class="sxs-lookup"><span data-stu-id="e76a1-361">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="e76a1-362">**Ip 配置**：显示网络连接的 ip 地址和其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="e76a1-362">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="e76a1-363">虚拟输入</span><span class="sxs-lookup"><span data-stu-id="e76a1-363">Virtual Input</span></span>

<span data-ttu-id="e76a1-364">Microsoft HoloLens 上 Windows 设备门户中 ![虚拟输入页面](images/windows-device-portal-virtual-input-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e76a1-364">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)</span></span><br>
<span data-ttu-id="e76a1-365">*Microsoft HoloLens 上 Windows 设备门户中的虚拟输入页面*</span><span class="sxs-lookup"><span data-stu-id="e76a1-365">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="e76a1-366">将键盘输入从远程计算机发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e76a1-366">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="e76a1-367">单击或点击 "**虚拟键盘**" 下的区域，以允许向 HoloLens 发送击键。</span><span class="sxs-lookup"><span data-stu-id="e76a1-367">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="e76a1-368">在 "**输入文本**" 文本框中键入，然后单击或点击 "**发送**"，将击键发送到活动的应用。</span><span class="sxs-lookup"><span data-stu-id="e76a1-368">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="e76a1-369">设备门户 REST API</span><span class="sxs-lookup"><span data-stu-id="e76a1-369">Device Portal REST API's</span></span>

<span data-ttu-id="e76a1-370">设备门户中的所有内容都是在[REST API](device-portal-api-reference.md)的基础之上构建的，你可以选择使用它来访问数据并以编程方式控制设备。</span><span class="sxs-lookup"><span data-stu-id="e76a1-370">Everything in the device portal is built on top of [REST API's](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>
