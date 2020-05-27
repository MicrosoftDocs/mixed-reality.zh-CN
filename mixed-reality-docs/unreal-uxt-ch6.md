---
title: 6. 打包并部署到设备或仿真器
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 6 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519960"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="9ddcc-104">6.打包并部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="9ddcc-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="9ddcc-105">本部分将指导你完成在 HoloLens 2 设备或仿真器上运行应用的准备步骤。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="9ddcc-106">如果你有设备，则可以从计算机流式传输到设备，或者打包应用，以便直接在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="9ddcc-107">如果没有设备，则需要打包应用，使其在仿真器上运行。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="9ddcc-108">目标</span><span class="sxs-lookup"><span data-stu-id="9ddcc-108">Objectives</span></span>

* <span data-ttu-id="9ddcc-109">[仅设备] 通过全息应用远程处理将应用流式传输到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9ddcc-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="9ddcc-110">打包应用并将其部署到 HoloLens 2 设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="9ddcc-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="9ddcc-111">[仅设备] 流式传输</span><span class="sxs-lookup"><span data-stu-id="9ddcc-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="9ddcc-112">在 HoloLens 2 上从 Microsoft Store 安装并运行“全息远程处理播放器”</span><span class="sxs-lookup"><span data-stu-id="9ddcc-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="9ddcc-113">转到“编辑”>“项目设置”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="9ddcc-114">在“全息远程处理”部分中，选中复选框以启用远程处理并重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="9ddcc-115">输入设备的 IP 地址，并单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="9ddcc-116">连接后，在 UE4 Editor 中，单击“播放”按钮右侧的下拉箭头，然后选择“VR 预览”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="9ddcc-117">打包和部署应用</span><span class="sxs-lookup"><span data-stu-id="9ddcc-117">Package and deploy your app</span></span> 

>[!NOTE]
><span data-ttu-id="9ddcc-118">如果这是你第一次为 HoloLens 打包 Unreal 应用，则需要从 Epic Launcher 下载支持文件。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-118">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> <span data-ttu-id="9ddcc-119">为此，请在 Epic Games Launcher 中转到“库”选项卡。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-119">To do so, go to the **Library** tab in the Epic Games Launcher.</span></span> <span data-ttu-id="9ddcc-120">选择“启动”旁边的下拉箭头，然后选择“选项”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-120">Select the dropdown arrow next to **Launch** and select **Options**.</span></span> <span data-ttu-id="9ddcc-121">在“目标平台”下，选择“HoloLens 2”，然后单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-121">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="9ddcc-122">![项目设置 - 描述](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="9ddcc-122">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="9ddcc-123">转到“编辑”>“项目设置”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-123">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="9ddcc-124">在“项目”>“描述”>“关于”>“项目名称”下，为项目指定名称。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-124">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="9ddcc-125">在“项目”>“描述”>“发布者”>“公司可分辨名称”下，输入“CN={INSERT COMPANY NAME}”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-125">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="9ddcc-126">将其中任一字段留空将导致错误。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-126">Leaving either of these fields blank will result in an error.</span></span> 

![项目设置 - 描述](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="9ddcc-128">在“平台”>“HoloLens”下，根据所需的目标，选择“模拟”和/或“设备”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-128">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="9ddcc-129">在“打包”部分的“签名证书”旁，单击“生成新证书”按钮生成新的签名证书。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-129">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="9ddcc-130">返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-130">Return to the Main window.</span></span>

![项目设置 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="9ddcc-132">转到“文件”>“包项目”并选择“HoloLens”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-132">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="9ddcc-133">创建新文件夹以保存包，并单击“选择文件夹”。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-133">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="9ddcc-134">成功打包应用后，请打开“Windows 设备门户”，转到“视图”>“应用”，并找到“部署应用”部分。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-134">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="9ddcc-135">单击“浏览...”并导航到“ChessApp.appxbundle”文件。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-135">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="9ddcc-136">单击“打开” 。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-136">Click **Open**.</span></span> 

    * <span data-ttu-id="9ddcc-137">如果这是你第一次在设备上安装应用，请选中“允许我选择框架包”旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-137">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="9ddcc-138">在下一个对话框中，包含相应的 VCLibs appx 文件（arm64 用于设备，x64 用于仿真器）。</span><span class="sxs-lookup"><span data-stu-id="9ddcc-138">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="9ddcc-139">单击“安装” </span><span class="sxs-lookup"><span data-stu-id="9ddcc-139">Click **Install**</span></span>

<span data-ttu-id="9ddcc-140">祝贺你学完本教程！</span><span class="sxs-lookup"><span data-stu-id="9ddcc-140">Congratulations on finishing this tutorial!</span></span>  