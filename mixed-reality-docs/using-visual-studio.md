---
title: 使用 Visual Studio 进行部署和调试
description: 了解如何使用 Visual Studio 生成、调试和部署适用于 HoloLens 与 Windows Mixed Reality 的应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合现实, Mixed Reality, 调试, 部署
ms.openlocfilehash: 8708ca39460fbd381bd41f5887e1276291f48b07
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "81484317"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="b638a-104">使用 Visual Studio 进行部署和调试</span><span class="sxs-lookup"><span data-stu-id="b638a-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="b638a-105">无论是要使用 DirectX 还是 Unity 来开发混合现实应用，都需要使用 Visual Studio 进行调试和部署。</span><span class="sxs-lookup"><span data-stu-id="b638a-105">Whether you want to use DirectX or Unity to develop your mixed reality app, you will use Visual Studio for debugging and deploying.</span></span> <span data-ttu-id="b638a-106">本部分介绍以下操作：</span><span class="sxs-lookup"><span data-stu-id="b638a-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="b638a-107">通过 Visual Studio 将应用程序部署到 HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="b638a-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="b638a-108">使用 Visual Studio 中内置的 HoloLens 仿真器。</span><span class="sxs-lookup"><span data-stu-id="b638a-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="b638a-109">调试混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="b638a-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b638a-110">必备条件</span><span class="sxs-lookup"><span data-stu-id="b638a-110">Prerequisites</span></span>
1. <span data-ttu-id="b638a-111">有关安装说明，请参阅[安装工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="b638a-111">See [Install the Tools](install-the-tools.md) for installation instructions.</span></span>
2. <span data-ttu-id="b638a-112">在 Visual Studio 中创建新的通用 Windows 应用项目。</span><span class="sxs-lookup"><span data-stu-id="b638a-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="b638a-113">对于 HoloLens（第一代），请使用 Visual Studio 2017 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="b638a-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="b638a-114">对于 HoloLens 2，请使用 Visual Studio 2019 16.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="b638a-114">For Hololens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="b638a-115">支持 C# 和 C++。</span><span class="sxs-lookup"><span data-stu-id="b638a-115">C# and C++ are supported.</span></span> <span data-ttu-id="b638a-116">（或按说明[在 Unity 中创建应用](holograms-100.md)。）</span><span class="sxs-lookup"><span data-stu-id="b638a-116">(Or follow the instructions to [create an app in Unity](holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="b638a-117">启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="b638a-117">Enabling Developer Mode</span></span>

<span data-ttu-id="b638a-118">首先在设备上启用“开发人员模式”，使 Visual Studio 能够连接到该设备。 </span><span class="sxs-lookup"><span data-stu-id="b638a-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="b638a-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="b638a-119">HoloLens</span></span>
1. <span data-ttu-id="b638a-120">打开 HoloLens，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="b638a-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="b638a-121">执行[开始手势](system-gesture.md)以启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="b638a-121">Perform the [start gesture](system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="b638a-122">选择“设置”  磁贴，以在你的环境中启动应用。</span><span class="sxs-lookup"><span data-stu-id="b638a-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="b638a-123">选择“更新”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="b638a-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="b638a-124">选择“面向开发人员”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="b638a-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="b638a-125">启用“开发人员模式”  。</span><span class="sxs-lookup"><span data-stu-id="b638a-125">Enable **Developer Mode**.</span></span> <span data-ttu-id="b638a-126">这样，就可以[将应用从 Visual Studio 部署到](using-visual-studio.md) HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b638a-126">This will allow you to [deploy apps from Visual Studio](using-visual-studio.md) to your HoloLens.</span></span>
7. <span data-ttu-id="b638a-127">可选：向下滚动，同时启用“设备门户”。 </span><span class="sxs-lookup"><span data-stu-id="b638a-127">Optional: Scroll down and also enable **Device Portal**.</span></span> <span data-ttu-id="b638a-128">然后，也可以通过 Web 浏览器连接到 HoloLens 上的 [Windows 设备门户](using-the-windows-device-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="b638a-128">This will also allow you to connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="b638a-129">Windows 电脑</span><span class="sxs-lookup"><span data-stu-id="b638a-129">Windows PC</span></span>

<span data-ttu-id="b638a-130">如果使用已连接到电脑的 Windows Mixed Reality 头戴显示设备，则必须在电脑上启用“开发人员模式”。 </span><span class="sxs-lookup"><span data-stu-id="b638a-130">If you are working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="b638a-131">转到“设置” </span><span class="sxs-lookup"><span data-stu-id="b638a-131">Go to **Settings**</span></span>
2. <span data-ttu-id="b638a-132">选择“更新和安全” </span><span class="sxs-lookup"><span data-stu-id="b638a-132">Select **Update and Security**</span></span>
3. <span data-ttu-id="b638a-133">选择“面向开发人员” </span><span class="sxs-lookup"><span data-stu-id="b638a-133">Select **For developers**</span></span>
4. <span data-ttu-id="b638a-134">启用“开发人员模式”，阅读所选设置的免责声明，然后单击“是”以接受更改。 </span><span class="sxs-lookup"><span data-stu-id="b638a-134">Enable **Developer Mode**, read the disclaimer for the setting you chose, then click Yes to accept the change.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a><span data-ttu-id="b638a-135">通过 Wi-Fi 部署应用 - HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="b638a-135">Deploying an app over Wi-Fi - HoloLens (1st gen)</span></span>
1. <span data-ttu-id="b638a-136">为你的应用选择一个 **x86** 生成配置</span><span class="sxs-lookup"><span data-stu-id="b638a-136">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="b638a-137">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-137">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
2. <span data-ttu-id="b638a-138">在部署目标下拉菜单中选择“远程计算机” </span><span class="sxs-lookup"><span data-stu-id="b638a-138">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="b638a-139">![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-139">![Remote machine deployment target in Visual Studio](images/remotemachinesetting.png)</span></span></br>
3. <span data-ttu-id="b638a-140">对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。 </span><span class="sxs-lookup"><span data-stu-id="b638a-140">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="b638a-141">对于 C# 项目，屏幕上会自动显示一个用于配置连接的对话框。</span><span class="sxs-lookup"><span data-stu-id="b638a-141">For C# projects, a dialog will automatically appear to configure your connection.</span></span>
  <span data-ttu-id="b638a-142">a.</span><span class="sxs-lookup"><span data-stu-id="b638a-142">a.</span></span> <span data-ttu-id="b638a-143">在“地址”或“计算机名”字段中输入设备的 IP 地址。  </span><span class="sxs-lookup"><span data-stu-id="b638a-143">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> <span data-ttu-id="b638a-144">在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址，或者可以向 Cortana 提问“我的 IP 地址是什么？” </span><span class="sxs-lookup"><span data-stu-id="b638a-144">Find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**, or you can ask Cortana "What is my IP address?"</span></span>
  <span data-ttu-id="b638a-145">b.</span><span class="sxs-lookup"><span data-stu-id="b638a-145">b.</span></span> <span data-ttu-id="b638a-146">将身份验证模式设置为“通用(未加密协议)” </span><span class="sxs-lookup"><span data-stu-id="b638a-146">Set Authentication Mode to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="b638a-147">![Visual Studio 中的远程连接对话框](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-147">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
4. <span data-ttu-id="b638a-148">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="b638a-148">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="b638a-149">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-149">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="b638a-150">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="b638a-150">The first time you deploy an app to your HoloLens from your PC, you will be prompted for a PIN.</span></span> <span data-ttu-id="b638a-151">按下面的说明**配对设备**。</span><span class="sxs-lookup"><span data-stu-id="b638a-151">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a><span data-ttu-id="b638a-152">通过 Wi-Fi 部署应用 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b638a-152">Deploying an app over Wi-Fi - HoloLens 2</span></span>
1. <span data-ttu-id="b638a-153">为你的应用选择一个 **ARM** 或 **ARM64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="b638a-153">Select an **ARM** or **ARM64** build configuration for your app</span></span></br>
<span data-ttu-id="b638a-154">![Visual Studio 中的 ARM64 生成配置](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-154">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
2. <span data-ttu-id="b638a-155">在部署目标下拉菜单中选择“远程计算机” </span><span class="sxs-lookup"><span data-stu-id="b638a-155">Select **Remote Machine** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="b638a-156">![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-156">![Remote machine deployment target in Visual Studio](images/remotemachinesetting_arm64.png)</span></span></br>
3. <span data-ttu-id="b638a-157">对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。 </span><span class="sxs-lookup"><span data-stu-id="b638a-157">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="b638a-158">对于 C# 项目，屏幕上会自动显示一个用于配置连接的对话框。</span><span class="sxs-lookup"><span data-stu-id="b638a-158">For C# projects, a dialog will automatically appear to configure your connection.</span></span>
  <span data-ttu-id="b638a-159">a.</span><span class="sxs-lookup"><span data-stu-id="b638a-159">a.</span></span> <span data-ttu-id="b638a-160">在“地址”或“计算机名”字段中输入设备的 IP 地址。  </span><span class="sxs-lookup"><span data-stu-id="b638a-160">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> <span data-ttu-id="b638a-161">在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址，或者可以向 Cortana 提问“我的 IP 地址是什么？” </span><span class="sxs-lookup"><span data-stu-id="b638a-161">Find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**, or you can ask Cortana "What is my IP address?"</span></span>
  <span data-ttu-id="b638a-162">b.</span><span class="sxs-lookup"><span data-stu-id="b638a-162">b.</span></span> <span data-ttu-id="b638a-163">将身份验证模式设置为“通用(未加密协议)” </span><span class="sxs-lookup"><span data-stu-id="b638a-163">Set the Authentication Mode to **Universal (Unencrypted protocol)**</span></span></br>
  <span data-ttu-id="b638a-164">![Visual Studio 中的远程连接对话框](images/remotedeploy.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-164">![Remote connection dialog in Visual Studio](images/remotedeploy.png)</span></span></br>
4. <span data-ttu-id="b638a-165">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="b638a-165">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="b638a-166">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-166">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
5. <span data-ttu-id="b638a-167">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="b638a-167">The first time you deploy an app to your HoloLens from your PC, you will be prompted for a PIN.</span></span> <span data-ttu-id="b638a-168">按下面的说明**配对设备**。</span><span class="sxs-lookup"><span data-stu-id="b638a-168">Follow the **Pairing your device** instructions below.</span></span>

<span data-ttu-id="b638a-169">如果 HoloLens IP 地址已更改，你可以转到“项目”>“属性”>“配置属性”>“调试”来更改目标计算机的 IP 地址 </span><span class="sxs-lookup"><span data-stu-id="b638a-169">If your HoloLens IP address changes, you can change the IP address of the target machine by going to **Project > Properties > Configuration Properties > Debugging**</span></span>

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a><span data-ttu-id="b638a-170">通过 USB 部署应用 - HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="b638a-170">Deploying an app over USB - HoloLens (1st gen)</span></span>
1. <span data-ttu-id="b638a-171">为你的应用选择一个 **x86** 生成配置</span><span class="sxs-lookup"><span data-stu-id="b638a-171">Select an **x86** build configuration for your app</span></span></br>
<span data-ttu-id="b638a-172">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-172">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
2. <span data-ttu-id="b638a-173">在部署目标下拉菜单中选择“设备” </span><span class="sxs-lookup"><span data-stu-id="b638a-173">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="b638a-174">![Visual Studio 中的设备部署](images/buildsettingsusbdeploy.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-174">![Device deployment in Visual Studio](images/buildsettingsusbdeploy.png)</span></span></br>
3. <span data-ttu-id="b638a-175">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="b638a-175">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="b638a-176">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-176">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="b638a-177">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="b638a-177">The first time you deploy an app to your HoloLens from your PC, you will be prompted for a PIN.</span></span> <span data-ttu-id="b638a-178">按下面的说明**配对设备**。</span><span class="sxs-lookup"><span data-stu-id="b638a-178">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-over-usb---hololens-2"></a><span data-ttu-id="b638a-179">通过 USB 部署应用 - HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b638a-179">Deploying an app over USB - HoloLens 2</span></span>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="b638a-180">为你的应用选择一个 **ARM** 或 **ARM64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="b638a-180">Select an **ARM** or **ARM64** build configuration for your app</span></span></br>
<span data-ttu-id="b638a-181">![Visual Studio 中的 ARM64 生成配置](images/arm64setting.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-181">![ARM64 build configuration in Visual Studio](images/arm64setting.png)</span></span></br>
2. <span data-ttu-id="b638a-182">在部署目标下拉菜单中选择“设备” </span><span class="sxs-lookup"><span data-stu-id="b638a-182">Select **Device** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="b638a-183">![Visual Studio 中的设备部署](images/buildsettingsusbdeploy_arm64.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-183">![Device deployment in Visual Studio](images/buildsettingsusbdeploy_arm64.png)</span></span></br>
3. <span data-ttu-id="b638a-184">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="b638a-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="b638a-185">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-185">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>
4. <span data-ttu-id="b638a-186">首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="b638a-186">The first time you deploy an app to your HoloLens from your PC, you will be prompted for a PIN.</span></span> <span data-ttu-id="b638a-187">按下面的说明**配对设备**。</span><span class="sxs-lookup"><span data-stu-id="b638a-187">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a><span data-ttu-id="b638a-188">将应用部署到本地电脑 - 沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="b638a-188">Deploying an app to your Local PC - immersive headset</span></span>

<span data-ttu-id="b638a-189">使用与电脑或 [Mixed Reality 仿真器](using-the-windows-mixed-reality-simulator.md)连接的 Windows Mixed Reality 沉浸式头戴显示设备时，请按这些说明操作。</span><span class="sxs-lookup"><span data-stu-id="b638a-189">Follow these instructions when using a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md).</span></span> <span data-ttu-id="b638a-190">在这种情况下，只需在本地电脑上部署并运行应用即可。</span><span class="sxs-lookup"><span data-stu-id="b638a-190">In these cases, simply deploy and run your app on the local PC.</span></span>
1. <span data-ttu-id="b638a-191">为应用选择一种 **x86** 或 **x64** 生成配置</span><span class="sxs-lookup"><span data-stu-id="b638a-191">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="b638a-192">在部署目标下拉菜单中选择“本地计算机” </span><span class="sxs-lookup"><span data-stu-id="b638a-192">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="b638a-193">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="b638a-193">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="b638a-194">配对设备</span><span class="sxs-lookup"><span data-stu-id="b638a-194">Pairing your device</span></span>

<span data-ttu-id="b638a-195">首次将应用从 Visual Studio 部署到 HoloLens 时，系统会提示输入 PIN。</span><span class="sxs-lookup"><span data-stu-id="b638a-195">The first time you deploy an app from Visual Studio to your HoloLens, you will be prompted for a PIN.</span></span> <span data-ttu-id="b638a-196">在 HoloLens 上启动“设置”应用，转到“更新”>“面向开发人员”并点击“配对”，以生成 PIN。  </span><span class="sxs-lookup"><span data-stu-id="b638a-196">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers** and tap on **Pair**.</span></span> <span data-ttu-id="b638a-197">HoloLens 上会显示一个 PIN；请在 Visual Studio 中键入此 PIN。</span><span class="sxs-lookup"><span data-stu-id="b638a-197">A PIN will be displayed on your HoloLens; type this PIN in Visual Studio.</span></span> <span data-ttu-id="b638a-198">配对完成后，在 HoloLens 上点击“完成”关闭对话框。 </span><span class="sxs-lookup"><span data-stu-id="b638a-198">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="b638a-199">此电脑现已与 HoloLens 配对，接下来可以自动部署应用。</span><span class="sxs-lookup"><span data-stu-id="b638a-199">This PC is now paired with the HoloLens and you will be able to deploy apps automatically.</span></span> <span data-ttu-id="b638a-200">请针对用于将应用部署到 HoloLens 的每台后续电脑重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="b638a-200">Repeat these steps for every subsequent PC that is used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="b638a-201">若要取消 HoloLens 与所有已配对计算机的配对，请启动“设置”应用，转到“更新”>“面向开发人员”，然后点击“清除”。   </span><span class="sxs-lookup"><span data-stu-id="b638a-201">To un-pair your HoloLens from all computers it was paired with, launch the **Settings** app, go to **Update > For Developers** and tap on **Clear**.</span></span>

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a><span data-ttu-id="b638a-202">将应用部署到 HoloLens（第一代）仿真器</span><span class="sxs-lookup"><span data-stu-id="b638a-202">Deploying an app to the HoloLens (1st gen) Emulator</span></span>
1. <span data-ttu-id="b638a-203">请确保已 **[安装 HoloLens 仿真器](install-the-tools.md)** 。</span><span class="sxs-lookup"><span data-stu-id="b638a-203">Make sure you have **[installed the HoloLens Emulator](install-the-tools.md)**.</span></span>
2. <span data-ttu-id="b638a-204">为应用选择一种 **x86** 生成配置。</span><span class="sxs-lookup"><span data-stu-id="b638a-204">Select an **x86** build configuration for your app.</span></span></br>
<span data-ttu-id="b638a-205">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-205">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="b638a-206">在部署目标下拉菜单中选择“HoloLens 仿真器” </span><span class="sxs-lookup"><span data-stu-id="b638a-206">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="b638a-207">![Visual Studio 中的仿真器目标](images/deployemulator.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-207">![Emulator target in Visual Studio](images/deployemulator.png)</span></span></br>
4. <span data-ttu-id="b638a-208">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="b638a-208">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="b638a-209">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-209">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a><span data-ttu-id="b638a-210">将应用部署到 HoloLens 2 仿真器</span><span class="sxs-lookup"><span data-stu-id="b638a-210">Deploying an app to the HoloLens 2 Emulator</span></span>
1. <span data-ttu-id="b638a-211">请确保已 **[安装 HoloLens 仿真器](install-the-tools.md)** 。</span><span class="sxs-lookup"><span data-stu-id="b638a-211">Make sure you have **[installed the HoloLens Emulator](install-the-tools.md)**.</span></span>
2. <span data-ttu-id="b638a-212">为应用选择一种 **x86** 或 **x64** 生成配置。</span><span class="sxs-lookup"><span data-stu-id="b638a-212">Select an **x86** or **x64** build configuration for your app.</span></span></br>
<span data-ttu-id="b638a-213">![Visual Studio 中的 x86 生成配置](images/x86setting.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-213">![x86 build configuration in Visual Studio](images/x86setting.png)</span></span></br>
3. <span data-ttu-id="b638a-214">在部署目标下拉菜单中选择“HoloLens 2 仿真器” </span><span class="sxs-lookup"><span data-stu-id="b638a-214">Select **HoloLens 2 Emulator** in the deployment target drop-down menu</span></span></br>
<span data-ttu-id="b638a-215">![Visual Studio 中的仿真器目标](images/deployemulator2.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-215">![Emulator target in Visual Studio](images/deployemulator2.png)</span></span></br>
4. <span data-ttu-id="b638a-216">选择“调试”>“开始调试”以部署应用并开始调试 </span><span class="sxs-lookup"><span data-stu-id="b638a-216">Select **Debug > Start debugging** to deploy your app and start debugging</span></span></br>
<span data-ttu-id="b638a-217">![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</span><span class="sxs-lookup"><span data-stu-id="b638a-217">![Start Without Debugging in Visual Studio](images/deploywithdebugging.png)</span></span></br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="b638a-218">适用于 HoloLens（第一代）的图形调试器</span><span class="sxs-lookup"><span data-stu-id="b638a-218">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="b638a-219">在编写和优化全息应用时，Visual Studio 图形诊断工具非常有用。</span><span class="sxs-lookup"><span data-stu-id="b638a-219">The Visual Studio Graphics Diagnostics tools are very helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="b638a-220">有关完整详细信息，请参阅 [MSDN 上的“Visual Studio 图形诊断”](https://msdn.microsoft.com/library/hh315751.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b638a-220">See [Visual Studio Graphics Diagnostics on MSDN](https://msdn.microsoft.com/library/hh315751.aspx) for full details.</span></span>

<span data-ttu-id="b638a-221">**启动图形调试器**</span><span class="sxs-lookup"><span data-stu-id="b638a-221">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="b638a-222">按上面的说明将目标指定为设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="b638a-222">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="b638a-223">转到“调试”>“图形”>“启动诊断” </span><span class="sxs-lookup"><span data-stu-id="b638a-223">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="b638a-224">首次在 HoloLens 上执行此操作时，可能会出现“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="b638a-224">The first time you do this with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="b638a-225">请重新启动 HoloLens 以使更新的权限生效，然后重试。</span><span class="sxs-lookup"><span data-stu-id="b638a-225">Reboot your HoloLens to allow updated permissions to take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="b638a-226">分析</span><span class="sxs-lookup"><span data-stu-id="b638a-226">Profiling</span></span>

<span data-ttu-id="b638a-227">使用 Visual Studio 分析工具可以分析应用的性能和资源使用情况。</span><span class="sxs-lookup"><span data-stu-id="b638a-227">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="b638a-228">这些工具包括用于优化 CPU、内存、图形和网络使用情况的工具。</span><span class="sxs-lookup"><span data-stu-id="b638a-228">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="b638a-229">有关完整详细信息，请参阅 [MSDN 上的“运行诊断工具但不调试”](https://msdn.microsoft.com/library/dn957936.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b638a-229">See [Run diagnostic tools without debugging on MSDN](https://msdn.microsoft.com/library/dn957936.aspx) for full details.</span></span>

<span data-ttu-id="b638a-230">**在 HoloLens 上启动分析工具**</span><span class="sxs-lookup"><span data-stu-id="b638a-230">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="b638a-231">按上面的说明将目标指定为设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="b638a-231">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="b638a-232">转到“调试”>“启动诊断工具但不调试...” </span><span class="sxs-lookup"><span data-stu-id="b638a-232">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="b638a-233">选择要使用的工具</span><span class="sxs-lookup"><span data-stu-id="b638a-233">Select the tools you want to use</span></span>
4. <span data-ttu-id="b638a-234">单击“启动” </span><span class="sxs-lookup"><span data-stu-id="b638a-234">Click **Start**</span></span>
5. <span data-ttu-id="b638a-235">首次在 HoloLens 上执行此操作时，可能会出现“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="b638a-235">The first time you do this with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="b638a-236">请重新启动 HoloLens 以使更新的权限生效，然后重试。</span><span class="sxs-lookup"><span data-stu-id="b638a-236">Reboot your HoloLens to allow updated permissions to take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="b638a-237">调试已安装的或正在运行的应用</span><span class="sxs-lookup"><span data-stu-id="b638a-237">Debugging an installed or running app</span></span>

<span data-ttu-id="b638a-238">可以使用 Visual Studio 来调试已安装的通用 Windows 应用，而无需从 Visual Studio 项目部署该应用。</span><span class="sxs-lookup"><span data-stu-id="b638a-238">You can use Visual Studio to debug a Universal Windows app that's installed without deploying from a Visual Studio project.</span></span> <span data-ttu-id="b638a-239">若要调试已安装的应用包，或者要调试已运行的应用，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="b638a-239">This is useful if you want to debug an installed app package, or if you want to debug an app that's already running.</span></span>
1. <span data-ttu-id="b638a-240">转到“调试”->“其他调试目标”->“调试已安装的应用包” </span><span class="sxs-lookup"><span data-stu-id="b638a-240">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="b638a-241">为 HoloLens 选择“远程计算机”目标，或者为沉浸式头戴显示设备选择“本地计算机”。  </span><span class="sxs-lookup"><span data-stu-id="b638a-241">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="b638a-242">输入设备的 **IP 地址**</span><span class="sxs-lookup"><span data-stu-id="b638a-242">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="b638a-243">选择“通用”身份验证模式 </span><span class="sxs-lookup"><span data-stu-id="b638a-243">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="b638a-244">窗口中会显示正在运行的和非活动的应用。</span><span class="sxs-lookup"><span data-stu-id="b638a-244">The window shows both running and inactive apps.</span></span> <span data-ttu-id="b638a-245">选择要调试的应用。</span><span class="sxs-lookup"><span data-stu-id="b638a-245">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="b638a-246">选择要调试的代码类型（“托管”、“本机”、“混合”）</span><span class="sxs-lookup"><span data-stu-id="b638a-246">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="b638a-247">单击“附加”或“开始”  </span><span class="sxs-lookup"><span data-stu-id="b638a-247">Click **Attach** or **Start**</span></span>

## <a name="see-also"></a><span data-ttu-id="b638a-248">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b638a-248">See also</span></span>
* [<span data-ttu-id="b638a-249">安装工具</span><span class="sxs-lookup"><span data-stu-id="b638a-249">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="b638a-250">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="b638a-250">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="b638a-251">部署和调试通用 Windows 平台 (UWP) 应用</span><span class="sxs-lookup"><span data-stu-id="b638a-251">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [<span data-ttu-id="b638a-252">启用设备进行开发</span><span class="sxs-lookup"><span data-stu-id="b638a-252">Enable your device for development</span></span>](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
