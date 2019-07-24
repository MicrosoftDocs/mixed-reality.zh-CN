---
title: 在 HoloLens 上连接到 Wi-fi
description: 说明如何通过 HoloLens 连接到无线 internet, 以及如何识别设备的 IP 地址。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, 无线, internet, ip, ip 地址
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670117"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="76887-104">在 HoloLens 上连接到 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="76887-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="76887-105">HoloLens 包含一种支持 802.11 ac 的 2x2 Wi-fi 无线电。</span><span class="sxs-lookup"><span data-stu-id="76887-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="76887-106">将 HoloLens 连接到 Wi-fi 网络类似于将 Windows 10 桌面版或移动设备连接到 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="76887-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![HoloLens Wi-fi 设置](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="76887-108">在 HoloLens 上连接到 Wi-fi 网络</span><span class="sxs-lookup"><span data-stu-id="76887-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="76887-109">[布隆](gestures.md#bloom)到 "**开始**" 菜单。</span><span class="sxs-lookup"><span data-stu-id="76887-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="76887-110">从 "开始" 菜单右侧的 "开始" 或 "**所有应用**" 列表中选择 "**设置**" 应用。</span><span class="sxs-lookup"><span data-stu-id="76887-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="76887-111">"**设置**" 应用将自动置于你前面。</span><span class="sxs-lookup"><span data-stu-id="76887-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="76887-112">选择 "**网络 & Internet**"。</span><span class="sxs-lookup"><span data-stu-id="76887-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="76887-113">确保 WLAN 已打开。</span><span class="sxs-lookup"><span data-stu-id="76887-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="76887-114">从列表中选择 "Wi-fi 网络"。</span><span class="sxs-lookup"><span data-stu-id="76887-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="76887-115">键入 Wi-fi 网络密码 (如果需要)。</span><span class="sxs-lookup"><span data-stu-id="76887-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="76887-116">在 HoloLens 上禁用 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="76887-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="76887-117">在 HoloLens 上使用 "设置" 应用</span><span class="sxs-lookup"><span data-stu-id="76887-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="76887-118">[布隆](gestures.md#bloom)到 "**开始**" 菜单。</span><span class="sxs-lookup"><span data-stu-id="76887-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="76887-119">从 "开始" 菜单右侧的 "开始" 或 "**所有应用**" 列表中选择 "**设置**" 应用。</span><span class="sxs-lookup"><span data-stu-id="76887-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="76887-120">"**设置**" 应用将自动置于你前面。</span><span class="sxs-lookup"><span data-stu-id="76887-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="76887-121">选择 "**网络 & Internet**"。</span><span class="sxs-lookup"><span data-stu-id="76887-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="76887-122">选择 "Wi-fi" 滑块开关, 将其移动到 "关" 位置。</span><span class="sxs-lookup"><span data-stu-id="76887-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="76887-123">这会关闭 Wi-fi 无线电的 RF 组件, 并在 HoloLens 上禁用所有 Wi-fi 功能。</span><span class="sxs-lookup"><span data-stu-id="76887-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="76887-124">在禁用 Wi-fi 无线电时, HoloLens 将无法自动加载你的[空间](environment-considerations-for-hololens.md#WiFi fingerprint considerations)。</span><span class="sxs-lookup"><span data-stu-id="76887-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="76887-125">将滑块切换到 "打开" 位置, 打开 Wi-fi 收音机并在 Microsoft HoloLens 上还原 Wi-fi 功能。</span><span class="sxs-lookup"><span data-stu-id="76887-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="76887-126">所选的 Wi-fi 无线电状态 ("关闭") 将在重新启动后保持。</span><span class="sxs-lookup"><span data-stu-id="76887-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="76887-127">如何确认已连接到 Wi-fi 网络</span><span class="sxs-lookup"><span data-stu-id="76887-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="76887-128">[布隆](gestures.md#bloom)打开 "**开始**" 菜单。</span><span class="sxs-lookup"><span data-stu-id="76887-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="76887-129">查看 "开始" 菜单左上方的 "Wi-fi" 状态。</span><span class="sxs-lookup"><span data-stu-id="76887-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="76887-130">将显示 Wi-fi 的状态和已连接网络的 SSID。</span><span class="sxs-lookup"><span data-stu-id="76887-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="76887-131">在 Wi-fi 网络上确定 HoloLens 的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="76887-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="76887-132">使用 "设置" 应用</span><span class="sxs-lookup"><span data-stu-id="76887-132">Using the Settings app</span></span>

1. <span data-ttu-id="76887-133">[布隆](gestures.md#bloom)到 "**开始**" 菜单。</span><span class="sxs-lookup"><span data-stu-id="76887-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="76887-134">从 "开始" 菜单右侧的 "开始" 或 "**所有应用**" 列表中选择 "**设置**" 应用。</span><span class="sxs-lookup"><span data-stu-id="76887-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="76887-135">"**设置**" 应用将自动置于你前面。</span><span class="sxs-lookup"><span data-stu-id="76887-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="76887-136">选择 "**网络 & Internet**"。</span><span class="sxs-lookup"><span data-stu-id="76887-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="76887-137">向下滚动到可用 Wi-fi 网络列表下, 选择 "**硬件属性**"。</span><span class="sxs-lookup"><span data-stu-id="76887-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Wi-fi 设置中的硬件属性](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="76887-139">IP 地址将显示在 " **IPv4 地址**" 旁边。</span><span class="sxs-lookup"><span data-stu-id="76887-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="76887-140">使用 Cortana</span><span class="sxs-lookup"><span data-stu-id="76887-140">Using Cortana</span></span>

<span data-ttu-id="76887-141">说 "*你好 Cortana, 我的 IP 地址是什么？* "</span><span class="sxs-lookup"><span data-stu-id="76887-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="76887-142">Cortana 将显示并读出你的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="76887-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="76887-143">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="76887-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="76887-144">在电脑上的 web 浏览器中打开[设备门户](using-the-windows-device-portal.md#networking)。</span><span class="sxs-lookup"><span data-stu-id="76887-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="76887-145">导航到 "**网络**" 部分。</span><span class="sxs-lookup"><span data-stu-id="76887-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="76887-146">你的 IP 地址和其他网络信息将显示在此处。</span><span class="sxs-lookup"><span data-stu-id="76887-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="76887-147">此方法允许在开发电脑上轻松复制和粘贴 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="76887-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
