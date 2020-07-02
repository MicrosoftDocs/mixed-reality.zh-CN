---
title: 6. 打包并部署到设备或仿真器
description: 教程系列第 6 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 99407a4069f914bf077e6323dde3e12978f6b765
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345687"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="ae795-104">6.打包并部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="ae795-104">6. Packaging & deploying to device or emulator</span></span>

## <a name="overview"></a><span data-ttu-id="ae795-105">概述</span><span class="sxs-lookup"><span data-stu-id="ae795-105">Overview</span></span>

<span data-ttu-id="ae795-106">在上一个教程中，你添加了一个简单的按钮，来将象棋棋子重置到原始位置。</span><span class="sxs-lookup"><span data-stu-id="ae795-106">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="ae795-107">这是最后一个部分，介绍了如何将此应用准备就绪，以在 HoloLens 2 或仿真器中运行它。</span><span class="sxs-lookup"><span data-stu-id="ae795-107">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="ae795-108">如果你有 HoloLens 2，则可以从计算机进行流式传输，或者打包应用，以便直接在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="ae795-108">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="ae795-109">如果没有设备，则打包应用，以便在仿真器上运行它。</span><span class="sxs-lookup"><span data-stu-id="ae795-109">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="ae795-110">本部分结束时，你将拥有一个已部署的混合现实应用，你可以通过交互和 UI 充分利用它。</span><span class="sxs-lookup"><span data-stu-id="ae795-110">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="ae795-111">目标</span><span class="sxs-lookup"><span data-stu-id="ae795-111">Objectives</span></span>

* <span data-ttu-id="ae795-112">[仅设备] 通过全息应用远程处理流式传输到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ae795-112">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="ae795-113">打包应用并将其部署到 HoloLens 2 设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="ae795-113">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="ae795-114">[仅设备] 流式传输</span><span class="sxs-lookup"><span data-stu-id="ae795-114">[Device Only] Streaming</span></span>
<span data-ttu-id="ae795-115">在这种情况下，[全息远程处理](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting)是指将数据从电脑或独立 UWP 设备流式传输到 HoloLens 2，而非切换通道。</span><span class="sxs-lookup"><span data-stu-id="ae795-115">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) in this case means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="ae795-116">这种方法的工作方式是，远程处理主机应用从 HoloLens 接收输入数据流，在虚拟沉浸式视图中呈现内容，并通过 Wi-Fi 将内容帧流式传输回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ae795-116">The way this works is a remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="ae795-117">通过流式处理，可以将远程沉浸式视图添加到现有的台式电脑软件中，并可访问更多系统资源。</span><span class="sxs-lookup"><span data-stu-id="ae795-117">Streaming allows you to add remote immersive views into existing desktop PC software and has access to more system resources.</span></span> 

<span data-ttu-id="ae795-118">如果要将此方法用于该象棋应用，需要完成以下事项：</span><span class="sxs-lookup"><span data-stu-id="ae795-118">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="ae795-119">在 HoloLens 2 上从 Microsoft Store 安装并运行“全息远程处理播放器”。</span><span class="sxs-lookup"><span data-stu-id="ae795-119">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span>

2.  <span data-ttu-id="ae795-120">转到“编辑 > 项目设置”，然后选中“全息远程处理”部分中的“启用远程处理”。  </span><span class="sxs-lookup"><span data-stu-id="ae795-120">Go to **Edit > Project Settings** and check **enable remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="ae795-121">重新启动编辑器，[找到设备的 IP 地址](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi)，并输入该地址，然后单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="ae795-121">Restart the editor, [find your device's IP address](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi) and enter it, then click **Connect**.</span></span>

<span data-ttu-id="ae795-122">连接后，单击“开始”按钮右侧的下拉箭头，然后选择“VR 预览”。 </span><span class="sxs-lookup"><span data-stu-id="ae795-122">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="ae795-123">此操作将在“VR 预览”窗口中运行应用，该窗口将流式传输到 HoloLens 头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="ae795-123">This will run the app in the VR Preview Window, which is streamed to the HoloLens headset.</span></span> 

## <a name="packaging-and-deploying-the-app"></a><span data-ttu-id="ae795-124">打包和部署应用</span><span class="sxs-lookup"><span data-stu-id="ae795-124">Packaging and deploying the app</span></span> 

>[!NOTE]
><span data-ttu-id="ae795-125">如果这是你第一次为 HoloLens 打包 Unreal 应用，则需要从 Epic Launcher 下载支持文件。</span><span class="sxs-lookup"><span data-stu-id="ae795-125">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> 
>- <span data-ttu-id="ae795-126">转到 Epic Games Launcher 的“库”选项卡，选择“启动”旁的下拉箭头，然后单击“选项”。  </span><span class="sxs-lookup"><span data-stu-id="ae795-126">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span> 
>- <span data-ttu-id="ae795-127">在“目标平台”下，选择“HoloLens 2”，然后单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="ae795-127">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="ae795-128">![项目设置 - 描述](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="ae795-128">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="ae795-129">转到“编辑”>“项目设置”。</span><span class="sxs-lookup"><span data-stu-id="ae795-129">Go to **Edit > Project Settings**.</span></span> 
    * <span data-ttu-id="ae795-130">在“项目 > 描述 > 关于 > 项目名称”下，添加项目名称。</span><span class="sxs-lookup"><span data-stu-id="ae795-130">Add a project name under **Project > Description > About > Project Name**.</span></span> 
    * <span data-ttu-id="ae795-131">在“项目”>“描述”>“发布者”>“公司可分辨名称”下，添加“CN=YourCompanyName” 。</span><span class="sxs-lookup"><span data-stu-id="ae795-131">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae795-132">如果将这些字段中的任一字段留空，那么当你在步骤 3 中尝试生成新证书时将遇到错误。</span><span class="sxs-lookup"><span data-stu-id="ae795-132">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ae795-133">发布者的名称必须采用 [LADPv3 可分辨名称格式](https://www.ietf.org/rfc/rfc2253.txt)。</span><span class="sxs-lookup"><span data-stu-id="ae795-133">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="ae795-134">格式不正确的发布者名称会导致在打包时出现“找不到签名密钥。</span><span class="sxs-lookup"><span data-stu-id="ae795-134">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="ae795-135">无法对应用进行数字签名。”</span><span class="sxs-lookup"><span data-stu-id="ae795-135">The app could not be digitally signed."</span></span> <span data-ttu-id="ae795-136">错误。</span><span class="sxs-lookup"><span data-stu-id="ae795-136">error upon packaging.</span></span>

![项目设置 - 描述](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="ae795-138">在“平台 > HoloLens”下，启用“为 HoloLens 仿真生成”和/或“为 HoloLens 设备生成”。  </span><span class="sxs-lookup"><span data-stu-id="ae795-138">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="ae795-139">单击“打包”部分（在“签名证书”旁）中的“生成新的”  。</span><span class="sxs-lookup"><span data-stu-id="ae795-139">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae795-140">如果使用的是已生成的证书，证书的发布者名称则必须与应用程序的发布者名称相同。</span><span class="sxs-lookup"><span data-stu-id="ae795-140">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="ae795-141">否则，会导致“找不到签名密钥。</span><span class="sxs-lookup"><span data-stu-id="ae795-141">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="ae795-142">无法对应用进行数字签名。”</span><span class="sxs-lookup"><span data-stu-id="ae795-142">The app could not be digitally signed."</span></span> <span data-ttu-id="ae795-143">error。</span><span class="sxs-lookup"><span data-stu-id="ae795-143">error.</span></span>

![项目设置 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="ae795-145">当系统提示你创建私钥密码时，出于测试目的，请单击“无”。</span><span class="sxs-lookup"><span data-stu-id="ae795-145">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![正在生成新证书](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="ae795-147">转到“文件”>“包项目”并选择“HoloLens”。</span><span class="sxs-lookup"><span data-stu-id="ae795-147">Go to **File > Package Project** and select **HoloLens**.</span></span> 
    * <span data-ttu-id="ae795-148">创建新文件夹以保存包，并单击“选择文件夹”。</span><span class="sxs-lookup"><span data-stu-id="ae795-148">Create a new folder to save your package in and click **Select Folder**.</span></span> 

6.  <span data-ttu-id="ae795-149">打包应用后，请打开 [Windows 设备门户](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)，转到“视图 > 应用”，并找到“部署应用”部分。</span><span class="sxs-lookup"><span data-stu-id="ae795-149">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="ae795-150">单击“浏览...”，转到“ChessApp.appxbundle”文件，然后单击“打开”。  </span><span class="sxs-lookup"><span data-stu-id="ae795-150">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span> 

    * <span data-ttu-id="ae795-151">如果这是你第一次在设备上安装应用，请选中“允许我选择框架包”旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="ae795-151">Check the box next to **Allow me to select framework packages** if this is the first time you're installing the app on your device.</span></span> 
    * <span data-ttu-id="ae795-152">在下一个对话框中，包含相应的 VCLibs 和 appx 文件（arm64 用于设备，x64 用于仿真器）。 </span><span class="sxs-lookup"><span data-stu-id="ae795-152">In the next dialogue, include the appropriate **VCLibs** and **appx** files (arm64 for device, x64 for emulator).</span></span> <span data-ttu-id="ae795-153">在保存包的文件夹中，可以从 HoloLens 下找到这些文件。</span><span class="sxs-lookup"><span data-stu-id="ae795-153">You can find these under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="ae795-154">单击“安装” </span><span class="sxs-lookup"><span data-stu-id="ae795-154">Click **Install**</span></span>
    * <span data-ttu-id="ae795-155">现在可以转到“所有应用”，并点击新安装的应用来运行它，或者可以直接从 Windows 设备门户启动应用。 </span><span class="sxs-lookup"><span data-stu-id="ae795-155">You can now go to **All Apps** and tap the the newly installed app to run it, or you can start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="ae795-156">恭喜！</span><span class="sxs-lookup"><span data-stu-id="ae795-156">Congratulations!</span></span> <span data-ttu-id="ae795-157">你的 HoloLens 混合现实应用程序已完成，并且可随时运行。</span><span class="sxs-lookup"><span data-stu-id="ae795-157">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="ae795-158">不过，这不是旅途的尽头。</span><span class="sxs-lookup"><span data-stu-id="ae795-158">However, this isn't the end of the road.</span></span> <span data-ttu-id="ae795-159">MRTK 有许多独立功能，你可以将其添加到项目中，其中包括空间映射、凝视和语音输入甚至 QR 码。</span><span class="sxs-lookup"><span data-stu-id="ae795-159">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="ae795-160">有关这些功能的详细信息，请参阅 [Unreal 开发概述](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)。</span><span class="sxs-lookup"><span data-stu-id="ae795-160">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>
