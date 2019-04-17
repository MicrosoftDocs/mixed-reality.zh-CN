---
title: Unity 游戏模式
description: 使用在 Unity 编辑器中播放模式下，若要预览设备上所做的更改，无需部署应用程序。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 远程处理、 全息版的远程处理、 全息版的远程处理的播放机
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590159"
---
# <a name="unity-play-mode"></a><span data-ttu-id="da648-104">Unity 游戏模式</span><span class="sxs-lookup"><span data-stu-id="da648-104">Unity Play Mode</span></span>

<span data-ttu-id="da648-105">处理你的 Unity 项目的快捷方法是使用"播放模式"。</span><span class="sxs-lookup"><span data-stu-id="da648-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="da648-106">此应用程序在本地运行 Unity 编辑器中您的 PC 上。</span><span class="sxs-lookup"><span data-stu-id="da648-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="da648-107">Unity 使用 Holographic 远程处理提供预览真实的 HoloLens 设备中的内容的快速方法。</span><span class="sxs-lookup"><span data-stu-id="da648-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="da648-108">全息版的远程处理与 unity 游戏模式</span><span class="sxs-lookup"><span data-stu-id="da648-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="da648-109">使用 Holographic 远程处理，您可能会在 Unity 编辑器中运行你的 PC 上遇到 HoloLens，对应用程序。</span><span class="sxs-lookup"><span data-stu-id="da648-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="da648-110">提供注视、 手势、 语音和输入的空间映射在 HoloLens 从您的电脑发送。</span><span class="sxs-lookup"><span data-stu-id="da648-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="da648-111">呈现的帧然后发回给你 HoloLens 中。</span><span class="sxs-lookup"><span data-stu-id="da648-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="da648-112">这是快速而无需构建和部署完整的项目中调试您的应用程序的好办法。</span><span class="sxs-lookup"><span data-stu-id="da648-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="da648-113">在你 HoloLens 上转到**Microsoft Store**并安装 **[Holographic 远程处理播放器](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="da648-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="da648-114">在你 HoloLens 上启动**Holographic 远程处理的播放机**应用。</span><span class="sxs-lookup"><span data-stu-id="da648-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="da648-115">在 Unity 中，转到**窗口**菜单，然后选择**Holographic 仿真**。</span><span class="sxs-lookup"><span data-stu-id="da648-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="da648-116">设置**仿真模式**到**远程连接到设备**。</span><span class="sxs-lookup"><span data-stu-id="da648-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="da648-117">有关**远程计算机**，输入你 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="da648-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="da648-118">单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="da648-118">Click **Connect**.</span></span> <span data-ttu-id="da648-119">应会看到**连接状态**更改为**已连接**，变为空白 HoloLens 中显示屏幕。</span><span class="sxs-lookup"><span data-stu-id="da648-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="da648-120">单击**播放**按钮以开始播放模式下，并体验在 HoloLens 上的应用程序。</span><span class="sxs-lookup"><span data-stu-id="da648-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="da648-121">全息版的远程处理需要快速的 PC 和 Wi-fi 连接。</span><span class="sxs-lookup"><span data-stu-id="da648-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="da648-122">请参阅[Holographic 远程处理的播放机](holographic-remoting-player.md)有关完整详细信息。</span><span class="sxs-lookup"><span data-stu-id="da648-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="da648-123">为获得最佳结果，请确保正确设置你的应用[关注点](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="da648-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="da648-124">这有助于 Holographic 远程处理来最好地调整您的无线连接的延迟到您的场景。</span><span class="sxs-lookup"><span data-stu-id="da648-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="da648-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="da648-125">See Also</span></span>
* [<span data-ttu-id="da648-126">全息版的远程处理的播放机</span><span class="sxs-lookup"><span data-stu-id="da648-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
