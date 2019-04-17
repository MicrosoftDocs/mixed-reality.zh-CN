---
title: 全息版的远程处理的播放机
description: 全息版的远程处理播放器是连接到 PC 应用程序和游戏支持 Holographic 进行远程处理的配套应用程序。 全息版的远程处理从 PC 到在你 Microsoft HoloLens 的 holographic 内容流式处理实时使用 Wi-fi 连接。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，远程处理，Holographic 远程处理
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593048"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="4dfdc-105">全息版的远程处理的播放机</span><span class="sxs-lookup"><span data-stu-id="4dfdc-105">Holographic Remoting Player</span></span>

<span data-ttu-id="4dfdc-106">全息版的远程处理播放器是连接到 PC 应用程序和游戏支持 Holographic 进行远程处理的配套应用程序。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="4dfdc-107">全息版的远程处理从 PC 到在你 Microsoft HoloLens 的 holographic 内容流式处理实时使用 Wi-fi 连接。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="4dfdc-108">Holographic 远程处理的播放机仅可用于专门为支持 Holographic 远程处理的电脑应用。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="4dfdc-109">特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-109">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="4dfdc-110">连接到全息版的远程处理播放器</span><span class="sxs-lookup"><span data-stu-id="4dfdc-110">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="4dfdc-111">按照应用程序的说明连接到全息版的远程处理播放器。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-111">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="4dfdc-112">你将需要输入你可以在远程处理播放机的主屏幕看到如下所示的 HoloLens 设备的 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="4dfdc-112">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![全息版的远程处理的播放机](images/holographicremotingplayer.png)

<span data-ttu-id="4dfdc-114">每当看到主屏幕时，您将知道您没有连接的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-114">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="4dfdc-115">请注意，holographic 远程处理连接是**不会加密**。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-115">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="4dfdc-116">通过您信任的安全的 Wi-fi 连接，应始终使用 Holographic 远程处理。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-116">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="4dfdc-117">质量和性能</span><span class="sxs-lookup"><span data-stu-id="4dfdc-117">Quality and Performance</span></span>

<span data-ttu-id="4dfdc-118">质量和您的体验的性能取决于三个因素：</span><span class="sxs-lookup"><span data-stu-id="4dfdc-118">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="4dfdc-119">**正在运行的 holographic 体验**-呈现高分辨率或特别详细内容的应用可能需要更快的 PC 或速度更快的无线连接。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-119">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="4dfdc-120">**你的电脑的硬件**-您的 PC 需要能够运行并将编码每秒 60 帧全息版的经验。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-120">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="4dfdc-121">获取图形卡，我们通常建议 GeForce GTX 970 或 AMD Radeon R9 290 或更好。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-121">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="4dfdc-122">同样，您特定的体验可能需要较高或较低端的卡。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-122">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="4dfdc-123">**你的 Wi-fi 连接**-holographic 体验进行流式处理通过 Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-123">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="4dfdc-124">使用具有低拥塞快速网络最大程度提高质量。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-124">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="4dfdc-125">使用通过以太网电缆连接的电脑，而不是 Wi-fi，还可以改善质量。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-125">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="4dfdc-126">诊断</span><span class="sxs-lookup"><span data-stu-id="4dfdc-126">Diagnostics</span></span>

<span data-ttu-id="4dfdc-127">若要衡量您的连接的质量，说说 **"启用诊断"** Holographic 远程处理的播放机的主屏幕上时。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-127">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="4dfdc-128">启用诊断后，该应用将显示你：</span><span class="sxs-lookup"><span data-stu-id="4dfdc-128">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="4dfdc-129">**每秒帧数**-呈现的帧的平均数远程处理播放器是接收和每秒呈现。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-129">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="4dfdc-130">理想的情况是 60 FPS。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-130">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="4dfdc-131">**延迟**-平均帧来从您的 PC 转到 HoloLens 所需的时间量。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-131">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="4dfdc-132">越低越好。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-132">The lower the better.</span></span> <span data-ttu-id="4dfdc-133">这是很大程度上取决于你的 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-133">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="4dfdc-134">在主屏幕上，可以说 **"禁用诊断"** 关闭诊断。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-134">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="4dfdc-135">PC 系统要求</span><span class="sxs-lookup"><span data-stu-id="4dfdc-135">PC System Requirements</span></span>
* <span data-ttu-id="4dfdc-136">您的 PC**必须**运行 Windows 10 周年更新。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-136">Your PC **must** be running the Windows 10 Anniversary Update.</span></span>
* <span data-ttu-id="4dfdc-137">我们建议 GeForce GTX 970 或 AMD Radeon R9 290 或更好的图形卡。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-137">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="4dfdc-138">我们建议将电脑连接到网络通过以太网以减少无线跃点数目。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-138">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dfdc-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="4dfdc-139">See Also</span></span>
* [<span data-ttu-id="4dfdc-140">全息版的远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="4dfdc-140">Holographic remoting software license terms</span></span>](microsoft-holographic-remoting-software-license-terms.md)
* [<span data-ttu-id="4dfdc-141">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="4dfdc-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
