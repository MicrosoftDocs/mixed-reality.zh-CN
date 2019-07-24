---
title: 全息远程处理播放器
description: 全息远程处理播放器是一种附属应用, 用于连接到支持全息远程处理的 PC 应用和游戏。 使用 Wi-fi 连接, 全息远程处理会实时地将 PC 中的全息内容流式处理到你的 Microsoft HoloLens。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813717"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="dccb1-105">全息远程处理播放器</span><span class="sxs-lookup"><span data-stu-id="dccb1-105">Holographic Remoting Player</span></span>

<span data-ttu-id="dccb1-106">全息远程处理播放器是一种附属应用, 用于连接到支持全息远程处理的 PC 应用和游戏。</span><span class="sxs-lookup"><span data-stu-id="dccb1-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="dccb1-107">使用 Wi-fi 连接, 全息远程处理会实时地将 PC 中的全息内容流式处理到你的 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="dccb1-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="dccb1-108">全息远程处理播放器只能与专门设计用于支持全息远程处理的 PC 应用程序一起使用。</span><span class="sxs-lookup"><span data-stu-id="dccb1-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

<span data-ttu-id="dccb1-109">全息远程处理播放器适用于 HoloLens 和 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="dccb1-109">The Holographic Remoting Player is available for both HoloLens and HoloLens 2.</span></span>  <span data-ttu-id="dccb1-110">支持通过 HoloLens 进行全息远程处理的 PC 应用需要更新, 以支持 Remtoing 和 HoloLens 2 的全息版。</span><span class="sxs-lookup"><span data-stu-id="dccb1-110">PC apps that supported Holographic Remoting with HoloLens need to be updated to support Holographic Remtoing with HoloLens 2.</span></span>  <span data-ttu-id="dccb1-111">如果你对支持哪些版本有任何疑问, 请与你的应用程序提供商联系。</span><span class="sxs-lookup"><span data-stu-id="dccb1-111">Please contact your app provider if you have questions about which versions are supported.</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="dccb1-112">连接到全息远程处理播放器</span><span class="sxs-lookup"><span data-stu-id="dccb1-112">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="dccb1-113">按照应用的说明连接到全息远程处理播放器。</span><span class="sxs-lookup"><span data-stu-id="dccb1-113">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="dccb1-114">需要输入你的 HoloLens 设备的 IP 地址, 你可以在远程处理播放机的主屏幕上看到该设备, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="dccb1-114">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![全息远程处理播放器](images/holographicremotingplayer.png)

<span data-ttu-id="dccb1-116">看到主屏幕时, 您将知道您没有连接到应用程序。</span><span class="sxs-lookup"><span data-stu-id="dccb1-116">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="dccb1-117">请注意, 全息远程处理连接**未加密**。</span><span class="sxs-lookup"><span data-stu-id="dccb1-117">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="dccb1-118">你应始终在你信任的安全 Wi-fi 连接上使用全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="dccb1-118">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="dccb1-119">质量和性能</span><span class="sxs-lookup"><span data-stu-id="dccb1-119">Quality and Performance</span></span>

<span data-ttu-id="dccb1-120">经验的质量和性能会因三个因素而异:</span><span class="sxs-lookup"><span data-stu-id="dccb1-120">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="dccb1-121">**正在运行的全息体验**-呈现高分辨率或高度详细内容的应用可能需要更快的 PC 或更快的无线连接。</span><span class="sxs-lookup"><span data-stu-id="dccb1-121">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="dccb1-122">**你的电脑硬件**-你的电脑需要能够以60帧/秒的速度运行和编码全息体验。</span><span class="sxs-lookup"><span data-stu-id="dccb1-122">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="dccb1-123">对于图形卡, 我们通常建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更高。</span><span class="sxs-lookup"><span data-stu-id="dccb1-123">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="dccb1-124">同样, 你的特定体验可能需要更高或更低端的卡。</span><span class="sxs-lookup"><span data-stu-id="dccb1-124">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="dccb1-125">**Wi-fi 连接**-你的全息体验通过 wi-fi 进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="dccb1-125">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="dccb1-126">使用具有低拥塞的快速网络来最大程度地提高质量。</span><span class="sxs-lookup"><span data-stu-id="dccb1-126">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="dccb1-127">使用通过以太网电缆而不是 Wi-fi 连接的 PC, 还可以提高质量。</span><span class="sxs-lookup"><span data-stu-id="dccb1-127">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="dccb1-128">诊断</span><span class="sxs-lookup"><span data-stu-id="dccb1-128">Diagnostics</span></span>

<span data-ttu-id="dccb1-129">若要测量连接的质量, 请在全息远程处理播放机的主屏幕上说 **"启用诊断"** 。</span><span class="sxs-lookup"><span data-stu-id="dccb1-129">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="dccb1-130">启用诊断后, 应用会显示以下信息:</span><span class="sxs-lookup"><span data-stu-id="dccb1-130">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="dccb1-131">**FPS** -远程处理播放机每秒接收和呈现的呈现帧的平均数目。</span><span class="sxs-lookup"><span data-stu-id="dccb1-131">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="dccb1-132">理想为 60 FPS。</span><span class="sxs-lookup"><span data-stu-id="dccb1-132">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="dccb1-133">**滞后**时间-帧从电脑进入 HoloLens 所需的平均时间量。</span><span class="sxs-lookup"><span data-stu-id="dccb1-133">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="dccb1-134">越低越好。</span><span class="sxs-lookup"><span data-stu-id="dccb1-134">The lower the better.</span></span> <span data-ttu-id="dccb1-135">这在很大程度上依赖于 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="dccb1-135">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="dccb1-136">在主屏幕上, 可以说 **"禁用诊断"** 以关闭诊断。</span><span class="sxs-lookup"><span data-stu-id="dccb1-136">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="dccb1-137">PC 系统要求</span><span class="sxs-lookup"><span data-stu-id="dccb1-137">PC System Requirements</span></span>
* <span data-ttu-id="dccb1-138">你的电脑**必须**运行 Windows 10 周年更新或更高版本。</span><span class="sxs-lookup"><span data-stu-id="dccb1-138">Your PC **must** be running the Windows 10 Anniversary Update or newer.</span></span>
* <span data-ttu-id="dccb1-139">建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更好的图形卡。</span><span class="sxs-lookup"><span data-stu-id="dccb1-139">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="dccb1-140">建议你通过以太网将电脑连接到网络, 以减少无线跃点的数量。</span><span class="sxs-lookup"><span data-stu-id="dccb1-140">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="dccb1-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="dccb1-141">See Also</span></span>
* [<span data-ttu-id="dccb1-142">全息远程软件许可条款</span><span class="sxs-lookup"><span data-stu-id="dccb1-142">Holographic remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="dccb1-143">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="dccb1-143">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
