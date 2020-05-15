---
title: 6. 打包并部署到设备或仿真器
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 6 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 35b18e4bb289438f94433827846e94d1014385db
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840376"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="46dd4-104">6.打包并部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="46dd4-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="46dd4-105">本部分将指导你完成在 HoloLens 2 设备或仿真器上运行应用的准备步骤。</span><span class="sxs-lookup"><span data-stu-id="46dd4-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="46dd4-106">如果你有设备，则可以从计算机流式传输到设备，或者打包应用，以便直接在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="46dd4-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="46dd4-107">如果没有设备，则需要打包应用，使其在仿真器上运行。</span><span class="sxs-lookup"><span data-stu-id="46dd4-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="46dd4-108">目标</span><span class="sxs-lookup"><span data-stu-id="46dd4-108">Objectives</span></span>

* <span data-ttu-id="46dd4-109">[仅设备] 通过全息应用远程处理将应用流式传输到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="46dd4-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="46dd4-110">打包应用并将其部署到 HoloLens 2 设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="46dd4-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="46dd4-111">[仅设备] 流式传输</span><span class="sxs-lookup"><span data-stu-id="46dd4-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="46dd4-112">在 HoloLens 2 上从 Microsoft Store 安装并运行“全息远程处理播放器” </span><span class="sxs-lookup"><span data-stu-id="46dd4-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="46dd4-113">转到“编辑”>“项目设置”  。</span><span class="sxs-lookup"><span data-stu-id="46dd4-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="46dd4-114">在“全息远程处理”部分中，选中复选框以启用远程处理并重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="46dd4-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="46dd4-115">输入设备的 IP 地址，并单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="46dd4-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="46dd4-116">连接后，在 UE4 Editor 中，单击“播放”按钮右侧的下拉箭头，然后选择“VR 预览”。</span><span class="sxs-lookup"><span data-stu-id="46dd4-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="46dd4-117">打包和部署应用</span><span class="sxs-lookup"><span data-stu-id="46dd4-117">Package and deploy your app</span></span> 

1.  <span data-ttu-id="46dd4-118">转到“编辑”>“项目设置”  。</span><span class="sxs-lookup"><span data-stu-id="46dd4-118">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="46dd4-119">在“项目”>“描述”>“关于”>“项目名称”  下，为项目指定名称。</span><span class="sxs-lookup"><span data-stu-id="46dd4-119">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="46dd4-120">在“项目”>“描述”>“发布者”>“公司可分辨名称”  下，输入“CN={INSERT COMPANY NAME}”。</span><span class="sxs-lookup"><span data-stu-id="46dd4-120">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="46dd4-121">将其中任一字段留空将导致错误。</span><span class="sxs-lookup"><span data-stu-id="46dd4-121">Leaving either of these fields blank will result in an error.</span></span> 

![项目设置 - 描述](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="46dd4-123">在“平台”>“HoloLens”  下，根据所需的目标，选择“模拟”和/或“设备”。</span><span class="sxs-lookup"><span data-stu-id="46dd4-123">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="46dd4-124">在“打包”  部分的“签名证书”  旁，单击“生成新证书”  按钮生成新的签名证书。</span><span class="sxs-lookup"><span data-stu-id="46dd4-124">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="46dd4-125">返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="46dd4-125">Return to the Main window.</span></span>

![项目设置 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="46dd4-127">转到“文件”>“包项目”  并选择“HoloLens”  。</span><span class="sxs-lookup"><span data-stu-id="46dd4-127">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="46dd4-128">创建新文件夹以保存包，并单击“选择文件夹”  。</span><span class="sxs-lookup"><span data-stu-id="46dd4-128">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="46dd4-129">成功打包应用后，请打开“Windows 设备门户”  ，转到“视图”>“应用”  ，并找到“部署应用”  部分。</span><span class="sxs-lookup"><span data-stu-id="46dd4-129">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="46dd4-130">单击“浏览...”  并导航到“ChessApp.appxbundle”  文件。</span><span class="sxs-lookup"><span data-stu-id="46dd4-130">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="46dd4-131">单击“打开”  。</span><span class="sxs-lookup"><span data-stu-id="46dd4-131">Click **Open**.</span></span> 

    * <span data-ttu-id="46dd4-132">如果这是你第一次在设备上安装应用，请选中“允许我选择框架包”  旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="46dd4-132">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="46dd4-133">在下一个对话框中，包含相应的 VCLibs appx 文件（arm64 用于设备，x64 用于仿真器）。</span><span class="sxs-lookup"><span data-stu-id="46dd4-133">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="46dd4-134">单击“安装” </span><span class="sxs-lookup"><span data-stu-id="46dd4-134">Click **Install**</span></span>

<span data-ttu-id="46dd4-135">祝贺你学完本教程！</span><span class="sxs-lookup"><span data-stu-id="46dd4-135">Congratulations on finishing this tutorial!</span></span>  