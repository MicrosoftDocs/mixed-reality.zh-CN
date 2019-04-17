---
title: 连接到 HoloLens 的 Wi-fi
description: 有关如何连接到无线 internet 与 HoloLens 以及如何确定设备的 IP 地址的说明。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens、 wifi、 无线、 internet、 ip、 ip 地址
ms.openlocfilehash: 0440c3dad48d73db51e7d730e79d6eb1e74a5694
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592864"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="c8c42-104">连接到 HoloLens 的 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="c8c42-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="c8c42-105">HoloLens 包含 802.11ac 的支持，2 x 2 个 Wi-fi 无线电。</span><span class="sxs-lookup"><span data-stu-id="c8c42-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="c8c42-106">连接到 Wi-fi 网络的 HoloLens 是类似于 Windows 10 桌面或移动设备连接到 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="c8c42-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![HoloLens 的 Wi-fi 设置](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="c8c42-108">连接到 HoloLens 上的 Wi-fi 网络</span><span class="sxs-lookup"><span data-stu-id="c8c42-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="c8c42-109">[布隆](gestures.md#bloom)到**启动**菜单。</span><span class="sxs-lookup"><span data-stu-id="c8c42-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="c8c42-110">选择**设置**应用程序从开始或从**的所有应用**开始菜单右侧的列表。</span><span class="sxs-lookup"><span data-stu-id="c8c42-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="c8c42-111">**设置**应用将自动放置在您的前面。</span><span class="sxs-lookup"><span data-stu-id="c8c42-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="c8c42-112">选择**网络和 Internet**。</span><span class="sxs-lookup"><span data-stu-id="c8c42-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="c8c42-113">确保 WLAN 已打开。</span><span class="sxs-lookup"><span data-stu-id="c8c42-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="c8c42-114">从列表中选择的 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="c8c42-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="c8c42-115">键入的 Wi-fi 网络密码 （如果需要）。</span><span class="sxs-lookup"><span data-stu-id="c8c42-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="c8c42-116">禁用 HoloLens 的 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="c8c42-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="c8c42-117">在 HoloLens 上使用设置应用</span><span class="sxs-lookup"><span data-stu-id="c8c42-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="c8c42-118">[布隆](gestures.md#bloom)到**启动**菜单。</span><span class="sxs-lookup"><span data-stu-id="c8c42-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="c8c42-119">选择**设置**应用程序从开始或从**的所有应用**开始菜单右侧的列表。</span><span class="sxs-lookup"><span data-stu-id="c8c42-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="c8c42-120">**设置**应用将自动放置在您的前面。</span><span class="sxs-lookup"><span data-stu-id="c8c42-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="c8c42-121">选择**网络和 Internet**。</span><span class="sxs-lookup"><span data-stu-id="c8c42-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="c8c42-122">选择将其移到"Off"位置的 Wi-fi 滑块交换机。</span><span class="sxs-lookup"><span data-stu-id="c8c42-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="c8c42-123">这将关闭 Wi-fi 无线电的 RF 组件并禁用所有 HoloLens 的 Wi-fi 功能。</span><span class="sxs-lookup"><span data-stu-id="c8c42-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="c8c42-124">HoloLens 将不能自动加载你[空格](environment-considerations-for-hololens.md#spaces)Wi-fi 无线电被禁用时。</span><span class="sxs-lookup"><span data-stu-id="c8c42-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#spaces) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="c8c42-125">将滑块开关移到"开"位置来启用 Wi-fi 无线电和还原 Microsoft HoloLens 上的 Wi-fi 功能。</span><span class="sxs-lookup"><span data-stu-id="c8c42-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="c8c42-126">所选的 Wi-fi 无线电的状态 （"开"的"关"） 将在重新启动后保留。</span><span class="sxs-lookup"><span data-stu-id="c8c42-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="c8c42-127">如何确认你连接到 Wi-fi 网络</span><span class="sxs-lookup"><span data-stu-id="c8c42-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="c8c42-128">[布隆](gestures.md#bloom)以打开**启动**菜单。</span><span class="sxs-lookup"><span data-stu-id="c8c42-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="c8c42-129">查看其中前角的开始菜单中的 Wi-fi 状态。</span><span class="sxs-lookup"><span data-stu-id="c8c42-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="c8c42-130">将显示状态的 Wi-fi 和连接的网络的 SSID。</span><span class="sxs-lookup"><span data-stu-id="c8c42-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="c8c42-131">识别你 HoloLens 的 Wi-fi 网络上的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="c8c42-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="c8c42-132">使用设置应用</span><span class="sxs-lookup"><span data-stu-id="c8c42-132">Using the Settings app</span></span>

1. <span data-ttu-id="c8c42-133">[布隆](gestures.md#bloom)到**启动**菜单。</span><span class="sxs-lookup"><span data-stu-id="c8c42-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="c8c42-134">选择**设置**应用程序从开始或从**的所有应用**开始菜单右侧的列表。</span><span class="sxs-lookup"><span data-stu-id="c8c42-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="c8c42-135">**设置**应用将自动放置在您的前面。</span><span class="sxs-lookup"><span data-stu-id="c8c42-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="c8c42-136">选择**网络和 Internet**。</span><span class="sxs-lookup"><span data-stu-id="c8c42-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="c8c42-137">向下滚动到下可用的 Wi-fi 网络的列表，然后选择**硬件属性**。</span><span class="sxs-lookup"><span data-stu-id="c8c42-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![硬件属性中的 Wi-fi 设置](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="c8c42-139">将下一步所示的 IP 地址**IPv4 地址**。</span><span class="sxs-lookup"><span data-stu-id="c8c42-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="c8c42-140">使用 Cortana</span><span class="sxs-lookup"><span data-stu-id="c8c42-140">Using Cortana</span></span>

<span data-ttu-id="c8c42-141">说"*你好，小娜，我的 IP 地址是什么？*"</span><span class="sxs-lookup"><span data-stu-id="c8c42-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="c8c42-142">Cortana 将显示并读取你的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="c8c42-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="c8c42-143">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="c8c42-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="c8c42-144">打开[设备门户](using-the-windows-device-portal.md#networking)在您的 PC 上的 web 浏览器中。</span><span class="sxs-lookup"><span data-stu-id="c8c42-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="c8c42-145">导航到**网络**部分。</span><span class="sxs-lookup"><span data-stu-id="c8c42-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="c8c42-146">你的 IP 地址和其他网络信息将会显示在该处。</span><span class="sxs-lookup"><span data-stu-id="c8c42-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="c8c42-147">此方法允许开发 PC 上的 IP 地址的简单复制和粘贴。</span><span class="sxs-lookup"><span data-stu-id="c8c42-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
