---
title: Unreal 中的流式传输
description: 从 Unreal 中流式传输到 HoloLens 2 的指南
author: suwu
ms.author: suwu
ms.date: 6/8/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 流式传输, 电脑, 全息应用远程处理, 全息远程处理播放器, 文档
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 78a019f5b74b254c1f32ec85dc639df47648555f
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84888908"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="a541e-104">Unreal 中的流式传输</span><span class="sxs-lookup"><span data-stu-id="a541e-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="a541e-105">概述</span><span class="sxs-lookup"><span data-stu-id="a541e-105">Overview</span></span>
<span data-ttu-id="a541e-106">从电脑流式传输到 HoloLens 提供了两大优势：</span><span class="sxs-lookup"><span data-stu-id="a541e-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="a541e-107">它使混合现实应用可以利用电脑的计算能力。</span><span class="sxs-lookup"><span data-stu-id="a541e-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="a541e-108">它有助于加快开发迭代的时间。</span><span class="sxs-lookup"><span data-stu-id="a541e-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="a541e-109">首先，需要将[全息远程处理播放器](holographic-remoting-player.md)下载到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="a541e-109">To get started, you'll need to download the [Holographic Remoting Player](holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="a541e-110">这使你的应用能够从以下来源直接流式传输到 HoloLens 上的远程处理播放器：</span><span class="sxs-lookup"><span data-stu-id="a541e-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="a541e-111">Unreal Engine 编辑器</span><span class="sxs-lookup"><span data-stu-id="a541e-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="a541e-112">打包的 Windows 可执行文件</span><span class="sxs-lookup"><span data-stu-id="a541e-112">A packaged Windows executable</span></span> 

<span data-ttu-id="a541e-113">进行流式传输时，你可以访问几乎所有相同的 HoloLens 功能，就像你在设备上运行应用程序时一样。</span><span class="sxs-lookup"><span data-stu-id="a541e-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="a541e-114">这包括[手关节跟踪](unreal-hand-tracking.md)（如果使用的是 HoloLens 2）、[空间映射](unreal-spatial-mapping.md)和[空间定位点](unreal-spatial-anchors.md)，但此[限制列表](holographic-remoting-troubleshooting.md)上的功能除外。</span><span class="sxs-lookup"><span data-stu-id="a541e-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> <span data-ttu-id="a541e-115">流式传输的质量严重依赖于 wifi 网络的强度。</span><span class="sxs-lookup"><span data-stu-id="a541e-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>

## <a name="device-support"></a><span data-ttu-id="a541e-116">设备支持</span><span class="sxs-lookup"><span data-stu-id="a541e-116">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a541e-117"><strong>源</strong></span><span class="sxs-lookup"><span data-stu-id="a541e-117"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="a541e-118"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第 1 代</strong></a></span><span class="sxs-lookup"><span data-stu-id="a541e-118"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="a541e-119"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="a541e-119"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="a541e-120"><strong>沉浸式头戴显示设备</strong></span><span class="sxs-lookup"><span data-stu-id="a541e-120"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a541e-121">Unreal 编辑器</span><span class="sxs-lookup"><span data-stu-id="a541e-121">Unreal editor</span></span></td>
        <td><span data-ttu-id="a541e-122">✔</span><span class="sxs-lookup"><span data-stu-id="a541e-122">✔</span></span></td>
        <td><span data-ttu-id="a541e-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a541e-123">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="a541e-124">Windows 包</span><span class="sxs-lookup"><span data-stu-id="a541e-124">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a541e-125">✔️</span><span class="sxs-lookup"><span data-stu-id="a541e-125">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="a541e-126">从 Unreal 编辑器进行流式传输</span><span class="sxs-lookup"><span data-stu-id="a541e-126">Streaming from the Unreal editor</span></span>

<span data-ttu-id="a541e-127">作为开发人员，你会发现从 Unreal 编辑器流式传输到 HoloLens 设备在测试时会提供很大的好处，也就是说，你无需再等待你的应用生成和部署完成后才尝试更新。</span><span class="sxs-lookup"><span data-stu-id="a541e-127">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="a541e-128">可以在“Unreal 入门”教程系列的最后一部分中找到有关[从 Unreal 编辑器进行流式传输](unreal-uxt-ch6.md#device-only-streaming)的详细说明。</span><span class="sxs-lookup"><span data-stu-id="a541e-128">You can find detailed instructions on [streaming from the Unreal editor](unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="a541e-129">从打包的 Windows 可执行文件进行流式传输</span><span class="sxs-lookup"><span data-stu-id="a541e-129">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="a541e-130">从 Unreal 4.25.1 开始，可以通过执行以下步骤将应用从打包的 Windows 可执行文件流式传输到 HoloLens 2 设备：</span><span class="sxs-lookup"><span data-stu-id="a541e-130">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="a541e-131">转到编辑器菜单中的“文件”>“包项目”>“Windows”。</span><span class="sxs-lookup"><span data-stu-id="a541e-131">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="a541e-132">选择要保存包的位置，然后单击“选择文件夹”。</span><span class="sxs-lookup"><span data-stu-id="a541e-132">Choose a location to save your package and click **Select Folder**.</span></span>

2. <span data-ttu-id="a541e-133">包生成完成后，请打开 HoloLens 2 上的“全息远程处理播放器”，并记下 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a541e-133">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="a541e-134">使“全息远程处理播放器”保持打开状态，然后使用命令行提示符执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a541e-134">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="a541e-135">将 cd 插入到保存包的本地目录。</span><span class="sxs-lookup"><span data-stu-id="a541e-135">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="a541e-136">输入以下命令：```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="a541e-136">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="a541e-137">项目设置中的应用程序名称应自动用于创建 Windows 包。</span><span class="sxs-lookup"><span data-stu-id="a541e-137">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="a541e-138">如果名称因某些原因而有所不同，请在命令提示符下使用 Windows 可执行文件名称。</span><span class="sxs-lookup"><span data-stu-id="a541e-138">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="a541e-139">按 Enter 键，随即将看到应用程序开始进行流式传输了！</span><span class="sxs-lookup"><span data-stu-id="a541e-139">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="a541e-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a541e-140">See also</span></span>
* [<span data-ttu-id="a541e-141">全息远程处理版本历史记录</span><span class="sxs-lookup"><span data-stu-id="a541e-141">Holographic remoting version history</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="a541e-142">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="a541e-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="a541e-143">使用全息远程处理建立安全连接</span><span class="sxs-lookup"><span data-stu-id="a541e-143">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
