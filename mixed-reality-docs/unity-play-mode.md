---
title: Unity 播放模式
description: 在 Unity 编辑器中使用播放模式, 无需部署应用即可在设备上预览所做的更改。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、远程处理、全息远程处理、全息远程处理播放器
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548727"
---
# <a name="unity-play-mode"></a><span data-ttu-id="eb268-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="eb268-104">Unity Play Mode</span></span>

<span data-ttu-id="eb268-105">处理 Unity 项目的快速方法是使用 "播放模式"。</span><span class="sxs-lookup"><span data-stu-id="eb268-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="eb268-106">这会在你的电脑上以本地方式在 Unity 编辑器中运行你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="eb268-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="eb268-107">Unity 使用全息远程处理提供一种在真实的 HoloLens 设备上快速预览内容的方式。</span><span class="sxs-lookup"><span data-stu-id="eb268-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="eb268-108">采用全息远程处理的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="eb268-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="eb268-109">通过全息远程处理, 你可以在 HoloLens 上体验你的应用程序, 而在你的电脑上运行 Unity 编辑器。</span><span class="sxs-lookup"><span data-stu-id="eb268-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="eb268-110">注视、手势、语音和空间映射输入将从你的 HoloLens 发送到你的电脑。</span><span class="sxs-lookup"><span data-stu-id="eb268-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="eb268-111">然后, 将呈现的帧发送回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="eb268-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="eb268-112">这是一种快速调试应用程序的绝佳方式, 无需生成和部署完整项目。</span><span class="sxs-lookup"><span data-stu-id="eb268-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="eb268-113">在 HoloLens 上, 中转到**Microsoft Store**并安装 **[全息远程处理播放器](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="eb268-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="eb268-114">在 HoloLens 上, 启动**全息远程处理播放器**应用。</span><span class="sxs-lookup"><span data-stu-id="eb268-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="eb268-115">在 Unity 中, 单击 "**窗口**" 菜单, 并选择 "**全息模拟**"。</span><span class="sxs-lookup"><span data-stu-id="eb268-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="eb268-116">将**仿真模式**设置为**远程设备**。</span><span class="sxs-lookup"><span data-stu-id="eb268-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="eb268-117">对于**远程计算机**, 请输入 HOLOLENS 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="eb268-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="eb268-118">单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="eb268-118">Click **Connect**.</span></span> <span data-ttu-id="eb268-119">应会看到**连接状态**更改为 "**已连接**", 并且会在 HoloLens 中看到屏幕显示为空白。</span><span class="sxs-lookup"><span data-stu-id="eb268-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="eb268-120">单击 "**播放**" 按钮以启动播放模式, 并在 HoloLens 上体验应用。</span><span class="sxs-lookup"><span data-stu-id="eb268-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="eb268-121">全息远程处理需要快速的 PC 和 Wi-fi 连接。</span><span class="sxs-lookup"><span data-stu-id="eb268-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="eb268-122">有关完整详细信息, 请参阅[全息远程处理播放器](holographic-remoting-player.md)。</span><span class="sxs-lookup"><span data-stu-id="eb268-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="eb268-123">为了获得最佳结果, 请确保应用正确设置了[焦点](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="eb268-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="eb268-124">这有助于全息远程处理最好地使场景适应无线连接的延迟。</span><span class="sxs-lookup"><span data-stu-id="eb268-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb268-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="eb268-125">See Also</span></span>
* [<span data-ttu-id="eb268-126">全息远程播放器</span><span class="sxs-lookup"><span data-stu-id="eb268-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
