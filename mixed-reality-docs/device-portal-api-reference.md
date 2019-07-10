---
title: 设备门户 API 参考
description: Windows Device Portal HoloLens 上的 API 参考
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，Windows Device Portal API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694438"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="9de7c-104">设备门户 API 参考</span><span class="sxs-lookup"><span data-stu-id="9de7c-104">Device portal API reference</span></span>

<span data-ttu-id="9de7c-105">中的所有内容[Windows Device Portal](using-the-windows-device-portal.md)为基础构建 REST API 可用于访问数据，并以编程方式控制你的设备。</span><span class="sxs-lookup"><span data-stu-id="9de7c-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="9de7c-106">应用程序出现的常见问题</span><span class="sxs-lookup"><span data-stu-id="9de7c-106">App deloyment</span></span>

<span data-ttu-id="9de7c-107">**/api/app/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="9de7c-108">卸载应用</span><span class="sxs-lookup"><span data-stu-id="9de7c-108">Uninstalls an app</span></span>

<span data-ttu-id="9de7c-109">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-109">Parameters</span></span>
* <span data-ttu-id="9de7c-110">包：要卸载的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="9de7c-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="9de7c-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="9de7c-112">安装应用</span><span class="sxs-lookup"><span data-stu-id="9de7c-112">Installs an App</span></span>

<span data-ttu-id="9de7c-113">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-113">Parameters</span></span>
* <span data-ttu-id="9de7c-114">包：要安装的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="9de7c-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="9de7c-115">有效负载</span><span class="sxs-lookup"><span data-stu-id="9de7c-115">Payload</span></span>
* <span data-ttu-id="9de7c-116">多部分符合标准的 http 正文</span><span class="sxs-lookup"><span data-stu-id="9de7c-116">multi-part conforming http body</span></span>

<span data-ttu-id="9de7c-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="9de7c-118">检索具有详细信息的系统上已安装应用的列表</span><span class="sxs-lookup"><span data-stu-id="9de7c-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="9de7c-119">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-119">Return data</span></span>
* <span data-ttu-id="9de7c-120">已安装程序包的详细信息列表</span><span class="sxs-lookup"><span data-stu-id="9de7c-120">List of installed packages with details</span></span>

<span data-ttu-id="9de7c-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="9de7c-122">获取正在进行应用安装中的状态</span><span class="sxs-lookup"><span data-stu-id="9de7c-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="9de7c-123">转储集合</span><span class="sxs-lookup"><span data-stu-id="9de7c-123">Dump collection</span></span>

<span data-ttu-id="9de7c-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="9de7c-125">禁用的故障转储集合旁加载应用</span><span class="sxs-lookup"><span data-stu-id="9de7c-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="9de7c-126">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-126">Parameters</span></span>
* <span data-ttu-id="9de7c-127">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-127">packageFullname : package name</span></span>

<span data-ttu-id="9de7c-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="9de7c-129">获取旁加载应用设置故障转储收集</span><span class="sxs-lookup"><span data-stu-id="9de7c-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="9de7c-130">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-130">Parameters</span></span>
* <span data-ttu-id="9de7c-131">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-131">packageFullname : package name</span></span>

<span data-ttu-id="9de7c-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="9de7c-133">启用并设置旁加载应用程序的转储控制设置</span><span class="sxs-lookup"><span data-stu-id="9de7c-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="9de7c-134">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-134">Parameters</span></span>
* <span data-ttu-id="9de7c-135">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-135">packageFullname : package name</span></span>

<span data-ttu-id="9de7c-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="9de7c-137">删除旁加载应用程序的故障转储</span><span class="sxs-lookup"><span data-stu-id="9de7c-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="9de7c-138">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-138">Parameters</span></span>
* <span data-ttu-id="9de7c-139">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-139">packageFullname : package name</span></span>
* <span data-ttu-id="9de7c-140">fileName： 转储文件的名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-140">fileName : dump file name</span></span>

<span data-ttu-id="9de7c-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="9de7c-142">检索的故障转储的旁加载应用</span><span class="sxs-lookup"><span data-stu-id="9de7c-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="9de7c-143">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-143">Parameters</span></span>
* <span data-ttu-id="9de7c-144">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-144">packageFullname : package name</span></span>
* <span data-ttu-id="9de7c-145">fileName： 转储文件的名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-145">fileName : dump file name</span></span>

<span data-ttu-id="9de7c-146">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-146">Return data</span></span>
* <span data-ttu-id="9de7c-147">转储文件。</span><span class="sxs-lookup"><span data-stu-id="9de7c-147">Dump file.</span></span> <span data-ttu-id="9de7c-148">检查使用 WinDbg 或 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9de7c-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="9de7c-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="9de7c-150">返回所有的故障转储的旁加载应用的列表</span><span class="sxs-lookup"><span data-stu-id="9de7c-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="9de7c-151">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-151">Return data</span></span>
* <span data-ttu-id="9de7c-152">每个端加载应用的列表中的故障转储</span><span class="sxs-lookup"><span data-stu-id="9de7c-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="9de7c-153">ETW</span><span class="sxs-lookup"><span data-stu-id="9de7c-153">ETW</span></span>

<span data-ttu-id="9de7c-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="9de7c-155">枚举已注册的提供程序</span><span class="sxs-lookup"><span data-stu-id="9de7c-155">Enumerates registered providers</span></span>

<span data-ttu-id="9de7c-156">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-156">Return data</span></span>
* <span data-ttu-id="9de7c-157">提供程序、 友好名称和 GUID 的列表</span><span class="sxs-lookup"><span data-stu-id="9de7c-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="9de7c-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="9de7c-159">创建实时的 ETW 会话;通过 websocket 进行管理。</span><span class="sxs-lookup"><span data-stu-id="9de7c-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="9de7c-160">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-160">Return data</span></span>
* <span data-ttu-id="9de7c-161">从已启用提供程序的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="9de7c-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="9de7c-162">全息操作系统</span><span class="sxs-lookup"><span data-stu-id="9de7c-162">Holographic OS</span></span>

<span data-ttu-id="9de7c-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="9de7c-164">返回一系列 HoloLens 特定 ETW 提供程序未注册与系统</span><span class="sxs-lookup"><span data-stu-id="9de7c-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="9de7c-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="9de7c-166">返回运行的所有服务的状态。</span><span class="sxs-lookup"><span data-stu-id="9de7c-166">Returns the states of all services running.</span></span>

<span data-ttu-id="9de7c-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="9de7c-168">获取以毫米为单位存储的 IPD （Interpupillary 距离）</span><span class="sxs-lookup"><span data-stu-id="9de7c-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="9de7c-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="9de7c-170">设置 IPD</span><span class="sxs-lookup"><span data-stu-id="9de7c-170">Sets the IPD</span></span>

<span data-ttu-id="9de7c-171">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-171">Parameters</span></span>
* <span data-ttu-id="9de7c-172">ipd:要以毫米为单位设置的新 IPD 值</span><span class="sxs-lookup"><span data-stu-id="9de7c-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="9de7c-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="9de7c-174">获取 Device Portal 的 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="9de7c-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="9de7c-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="9de7c-176">设置 HTTPS 要求设备门户</span><span class="sxs-lookup"><span data-stu-id="9de7c-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="9de7c-177">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-177">Parameters</span></span>
* <span data-ttu-id="9de7c-178">必需： yes、 no 或默认值</span><span class="sxs-lookup"><span data-stu-id="9de7c-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="9de7c-179">Holographic 感知</span><span class="sxs-lookup"><span data-stu-id="9de7c-179">Holographic Perception</span></span>

<span data-ttu-id="9de7c-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="9de7c-181">接受 websocket 升级并运行 30 fps 时发送更新的感知客户端。</span><span class="sxs-lookup"><span data-stu-id="9de7c-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="9de7c-182">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-182">Parameters</span></span>
* <span data-ttu-id="9de7c-183">clientmode:"活动"时强制进行可视化跟踪模式下无法被动建立</span><span class="sxs-lookup"><span data-stu-id="9de7c-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="9de7c-184">Holographic 温度</span><span class="sxs-lookup"><span data-stu-id="9de7c-184">Holographic Thermal</span></span>

<span data-ttu-id="9de7c-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="9de7c-186">获取设备 （0 正常，1 热，关键 2） 的热量阶段</span><span class="sxs-lookup"><span data-stu-id="9de7c-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="9de7c-187">Perception 模拟控件</span><span class="sxs-lookup"><span data-stu-id="9de7c-187">Perception Simulation Control</span></span>

<span data-ttu-id="9de7c-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="9de7c-189">获取的模拟模式</span><span class="sxs-lookup"><span data-stu-id="9de7c-189">Get the simulation mode</span></span>

<span data-ttu-id="9de7c-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="9de7c-191">设置模拟模式</span><span class="sxs-lookup"><span data-stu-id="9de7c-191">Set the simulation mode</span></span>

<span data-ttu-id="9de7c-192">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-192">Parameters</span></span>
* <span data-ttu-id="9de7c-193">模式： 模拟模式： 默认、 模拟、 远程，旧</span><span class="sxs-lookup"><span data-stu-id="9de7c-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="9de7c-194">**/api/holographic/simulation/control/stream （删除）**</span><span class="sxs-lookup"><span data-stu-id="9de7c-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="9de7c-195">删除控制流。</span><span class="sxs-lookup"><span data-stu-id="9de7c-195">Delete a control stream.</span></span>

<span data-ttu-id="9de7c-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="9de7c-197">打开的控制流的 web 套接字连接。</span><span class="sxs-lookup"><span data-stu-id="9de7c-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="9de7c-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="9de7c-199">创建控制流 （优先级是必需的） 或将数据发布到创建的流 (所需的 streamId)。</span><span class="sxs-lookup"><span data-stu-id="9de7c-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="9de7c-200">已发布的数据应为类型应用程序/八进制流。</span><span class="sxs-lookup"><span data-stu-id="9de7c-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="9de7c-201">Perception 模拟播放</span><span class="sxs-lookup"><span data-stu-id="9de7c-201">Perception Simulation Playback</span></span>

<span data-ttu-id="9de7c-202">**/api/holographic/simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="9de7c-203">删除录制。</span><span class="sxs-lookup"><span data-stu-id="9de7c-203">Delete a recording.</span></span>

<span data-ttu-id="9de7c-204">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-204">Parameters</span></span>
* <span data-ttu-id="9de7c-205">录制：若要删除的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="9de7c-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="9de7c-207">将录制内容上传。</span><span class="sxs-lookup"><span data-stu-id="9de7c-207">Upload a recording.</span></span>

<span data-ttu-id="9de7c-208">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="9de7c-209">获取所有录制。</span><span class="sxs-lookup"><span data-stu-id="9de7c-209">Get all recordings.</span></span>

<span data-ttu-id="9de7c-210">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="9de7c-211">获取记录的当前播放状态。</span><span class="sxs-lookup"><span data-stu-id="9de7c-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="9de7c-212">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-212">Parameters</span></span>
* <span data-ttu-id="9de7c-213">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-213">recording : Name of recording.</span></span>

<span data-ttu-id="9de7c-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="9de7c-215">卸载录制。</span><span class="sxs-lookup"><span data-stu-id="9de7c-215">Unload a recording.</span></span>

<span data-ttu-id="9de7c-216">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-216">Parameters</span></span>
* <span data-ttu-id="9de7c-217">录制：记录要卸载的名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="9de7c-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="9de7c-219">加载录制。</span><span class="sxs-lookup"><span data-stu-id="9de7c-219">Load a recording.</span></span>

<span data-ttu-id="9de7c-220">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-220">Parameters</span></span>
* <span data-ttu-id="9de7c-221">录制：记录要加载的名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="9de7c-222">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="9de7c-223">获取所有已加载的记录。</span><span class="sxs-lookup"><span data-stu-id="9de7c-223">Get all loaded recordings.</span></span>

<span data-ttu-id="9de7c-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="9de7c-225">暂停录制。</span><span class="sxs-lookup"><span data-stu-id="9de7c-225">Pause a recording.</span></span>

<span data-ttu-id="9de7c-226">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-226">Parameters</span></span>
* <span data-ttu-id="9de7c-227">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-227">recording : Name of recording.</span></span>

<span data-ttu-id="9de7c-228">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="9de7c-229">播放录制内容。</span><span class="sxs-lookup"><span data-stu-id="9de7c-229">Play a recording.</span></span>

<span data-ttu-id="9de7c-230">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-230">Parameters</span></span>
* <span data-ttu-id="9de7c-231">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-231">recording : Name of recording.</span></span>

<span data-ttu-id="9de7c-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="9de7c-233">停止录制。</span><span class="sxs-lookup"><span data-stu-id="9de7c-233">Stop a recording.</span></span>

<span data-ttu-id="9de7c-234">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-234">Parameters</span></span>
* <span data-ttu-id="9de7c-235">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-235">recording : Name of recording.</span></span>

<span data-ttu-id="9de7c-236">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="9de7c-237">获取加载录制中的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9de7c-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="9de7c-238">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-238">Parameters</span></span>
* <span data-ttu-id="9de7c-239">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="9de7c-240">Perception 模拟录制</span><span class="sxs-lookup"><span data-stu-id="9de7c-240">Perception Simulation Recording</span></span>

<span data-ttu-id="9de7c-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="9de7c-242">开始录制。</span><span class="sxs-lookup"><span data-stu-id="9de7c-242">Start a recording.</span></span> <span data-ttu-id="9de7c-243">仅单个记录可以同时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="9de7c-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="9de7c-244">必须设置为 head、 手、 spatialMapping 或环境。</span><span class="sxs-lookup"><span data-stu-id="9de7c-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="9de7c-245">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-245">Parameters</span></span>
* <span data-ttu-id="9de7c-246">头：将设置为 1 到记录头数据。</span><span class="sxs-lookup"><span data-stu-id="9de7c-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="9de7c-247">手：设置为 1 以记录现有数据。</span><span class="sxs-lookup"><span data-stu-id="9de7c-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="9de7c-248">spatialMapping:设置为 1 来记录空间映射。</span><span class="sxs-lookup"><span data-stu-id="9de7c-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="9de7c-249">环境：设置为 1 以记录环境数据。</span><span class="sxs-lookup"><span data-stu-id="9de7c-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="9de7c-250">名称：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-250">name : Name of the recording.</span></span>
* <span data-ttu-id="9de7c-251">singleSpatialMappingFrame:设置为 1 来记录仅一个空间映射框架。</span><span class="sxs-lookup"><span data-stu-id="9de7c-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="9de7c-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="9de7c-253">获取正在记录状态。</span><span class="sxs-lookup"><span data-stu-id="9de7c-253">Get recording state.</span></span>

<span data-ttu-id="9de7c-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="9de7c-255">停止当前录制。</span><span class="sxs-lookup"><span data-stu-id="9de7c-255">Stop the current recording.</span></span> <span data-ttu-id="9de7c-256">录制将返回为一个文件。</span><span class="sxs-lookup"><span data-stu-id="9de7c-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="9de7c-257">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="9de7c-257">Mixed Reality Capture</span></span>

<span data-ttu-id="9de7c-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="9de7c-259">从设备下载混合的现实文件。</span><span class="sxs-lookup"><span data-stu-id="9de7c-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="9de7c-260">使用 op = 流式处理的流查询参数。</span><span class="sxs-lookup"><span data-stu-id="9de7c-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="9de7c-261">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-261">Parameters</span></span>
* <span data-ttu-id="9de7c-262">文件名：编码的要获取的视频文件的名称，hex64</span><span class="sxs-lookup"><span data-stu-id="9de7c-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="9de7c-263">操作： 流</span><span class="sxs-lookup"><span data-stu-id="9de7c-263">op : stream</span></span>

<span data-ttu-id="9de7c-264">**/api/holographic/mrc/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="9de7c-265">删除设备中记录了混合的现实。</span><span class="sxs-lookup"><span data-stu-id="9de7c-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="9de7c-266">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-266">Parameters</span></span>
* <span data-ttu-id="9de7c-267">文件名：编码的要删除的文件的名称，hex64</span><span class="sxs-lookup"><span data-stu-id="9de7c-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="9de7c-268">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="9de7c-269">返回存储在设备上的混合的现实文件列表</span><span class="sxs-lookup"><span data-stu-id="9de7c-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="9de7c-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="9de7c-271">采用混合的现实照片，并创建在设备上的文件</span><span class="sxs-lookup"><span data-stu-id="9de7c-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="9de7c-272">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-272">Parameters</span></span>
* <span data-ttu-id="9de7c-273">holo： 捕获全息： true 或 false （默认值为 false）</span><span class="sxs-lookup"><span data-stu-id="9de7c-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="9de7c-274">pv： 捕获 PV 照相机： true 或 false （默认值为 false）</span><span class="sxs-lookup"><span data-stu-id="9de7c-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="9de7c-275">RenderFromCamera:从照片/视频摄像机角度来看 (仅 HoloLens 2) 呈现器： true 或 false （默认值为 true）</span><span class="sxs-lookup"><span data-stu-id="9de7c-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="9de7c-276">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="9de7c-277">获取默认混合现实捕获设置</span><span class="sxs-lookup"><span data-stu-id="9de7c-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="9de7c-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="9de7c-279">设置默认混合现实捕获设置。</span><span class="sxs-lookup"><span data-stu-id="9de7c-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="9de7c-280">其中某些设置将应用于系统的 MRC 照片和视频捕获。</span><span class="sxs-lookup"><span data-stu-id="9de7c-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="9de7c-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="9de7c-282">获取混合现实的记录 （运行、 已停止） 状态</span><span class="sxs-lookup"><span data-stu-id="9de7c-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="9de7c-283">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="9de7c-284">获取指定的文件的缩略图。</span><span class="sxs-lookup"><span data-stu-id="9de7c-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="9de7c-285">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-285">Parameters</span></span>
* <span data-ttu-id="9de7c-286">文件名：编码为其请求缩略图的文件的名称，hex64</span><span class="sxs-lookup"><span data-stu-id="9de7c-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="9de7c-287">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="9de7c-288">启动混合的现实录制</span><span class="sxs-lookup"><span data-stu-id="9de7c-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="9de7c-289">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-289">Parameters</span></span>
* <span data-ttu-id="9de7c-290">holo： 捕获全息： true 或 false （默认值为 false）</span><span class="sxs-lookup"><span data-stu-id="9de7c-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="9de7c-291">pv： 捕获 PV 照相机： true 或 false （默认值为 false）</span><span class="sxs-lookup"><span data-stu-id="9de7c-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="9de7c-292">mic： 捕获麦克风： true 或 false （默认值为 false）</span><span class="sxs-lookup"><span data-stu-id="9de7c-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="9de7c-293">环回： 捕获应用音频： true 或 false （默认值为 false）</span><span class="sxs-lookup"><span data-stu-id="9de7c-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="9de7c-294">RenderFromCamera:从照片/视频摄像机角度来看 (仅 HoloLens 2) 呈现器： true 或 false （默认值为 true）</span><span class="sxs-lookup"><span data-stu-id="9de7c-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="9de7c-295">vstab:(仅 HoloLens 2) 启用视频防抖动： true 或 false （默认值为 true）</span><span class="sxs-lookup"><span data-stu-id="9de7c-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="9de7c-296">vstabbuffer:(仅 HoloLens 2) 视频防抖动缓冲区滞后时间：0 到 30 帧 （默认为 15 帧）</span><span class="sxs-lookup"><span data-stu-id="9de7c-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="9de7c-297">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="9de7c-298">停止当前混合现实录制</span><span class="sxs-lookup"><span data-stu-id="9de7c-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="9de7c-299">流式处理的混合的现实</span><span class="sxs-lookup"><span data-stu-id="9de7c-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="9de7c-300">HoloLens 支持混合现实通过成块下载的分片 mp4 的实时预览。</span><span class="sxs-lookup"><span data-stu-id="9de7c-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="9de7c-301">混合的现实流共享同一组参数来控制捕获内容：</span><span class="sxs-lookup"><span data-stu-id="9de7c-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="9de7c-302">holo： 捕获全息： true 或 false</span><span class="sxs-lookup"><span data-stu-id="9de7c-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="9de7c-303">pv： 捕获 PV 照相机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="9de7c-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="9de7c-304">mic： 捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="9de7c-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="9de7c-305">环回： 捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="9de7c-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="9de7c-306">如果未指定任何这些： 将捕获全息、 照片/视频摄像机和应用音频</span><span class="sxs-lookup"><span data-stu-id="9de7c-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="9de7c-307">如果指定了任何： 未指定的参数将默认为 false</span><span class="sxs-lookup"><span data-stu-id="9de7c-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="9de7c-308">可选参数 (仅 HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="9de7c-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="9de7c-309">RenderFromCamera: 从照片/视频摄像机的角度来看呈现: true 或 false （默认值为 true）</span><span class="sxs-lookup"><span data-stu-id="9de7c-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="9de7c-310">vstab： 启用视频防抖动： true 或 false （默认值为 false）</span><span class="sxs-lookup"><span data-stu-id="9de7c-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="9de7c-311">vstabbuffer： 视频防抖动缓冲区延迟：0 到 30 帧 （默认为 15 帧）</span><span class="sxs-lookup"><span data-stu-id="9de7c-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="9de7c-312">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="9de7c-313">1280x720p 30 fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="9de7c-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="9de7c-314">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="9de7c-315">1280x720p 30 fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="9de7c-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="9de7c-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="9de7c-317">854x480p 30 fps 2.5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="9de7c-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="9de7c-318">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="9de7c-319">428x240p 15 fps 0.6Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="9de7c-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="9de7c-320">网络</span><span class="sxs-lookup"><span data-stu-id="9de7c-320">Networking</span></span>

<span data-ttu-id="9de7c-321">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="9de7c-322">获取当前的 ip 配置</span><span class="sxs-lookup"><span data-stu-id="9de7c-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="9de7c-323">OS 信息</span><span class="sxs-lookup"><span data-stu-id="9de7c-323">OS Information</span></span>

<span data-ttu-id="9de7c-324">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="9de7c-325">获取操作系统信息</span><span class="sxs-lookup"><span data-stu-id="9de7c-325">Gets operating system information</span></span>

<span data-ttu-id="9de7c-326">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="9de7c-327">获取计算机名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-327">Gets the machine name</span></span>

<span data-ttu-id="9de7c-328">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="9de7c-329">设置计算机名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-329">Sets the machine name</span></span>

<span data-ttu-id="9de7c-330">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-330">Parameters</span></span>
* <span data-ttu-id="9de7c-331">名称：新的计算机名称，hex64 编码，将设置为</span><span class="sxs-lookup"><span data-stu-id="9de7c-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="9de7c-332">性能数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-332">Performance data</span></span>

<span data-ttu-id="9de7c-333">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="9de7c-334">返回正在运行进程的详细信息的列表</span><span class="sxs-lookup"><span data-stu-id="9de7c-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="9de7c-335">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-335">Return data</span></span>
* <span data-ttu-id="9de7c-336">与进程和每个进程的详细信息的列表的 JSON</span><span class="sxs-lookup"><span data-stu-id="9de7c-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="9de7c-337">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="9de7c-338">返回系统性能统计信息 （I/O 读/写、 内存统计信息等。</span><span class="sxs-lookup"><span data-stu-id="9de7c-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="9de7c-339">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-339">Return data</span></span>
* <span data-ttu-id="9de7c-340">系统信息的 JSON:CPU、 GPU、 内存、 网络、 IO</span><span class="sxs-lookup"><span data-stu-id="9de7c-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="9de7c-341">电源</span><span class="sxs-lookup"><span data-stu-id="9de7c-341">Power</span></span>

<span data-ttu-id="9de7c-342">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="9de7c-343">获取当前的电池状态</span><span class="sxs-lookup"><span data-stu-id="9de7c-343">Gets the current battery state</span></span>

<span data-ttu-id="9de7c-344">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="9de7c-345">检查系统是否在低功耗状态</span><span class="sxs-lookup"><span data-stu-id="9de7c-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="9de7c-346">远程控制</span><span class="sxs-lookup"><span data-stu-id="9de7c-346">Remote Control</span></span>

<span data-ttu-id="9de7c-347">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="9de7c-348">重新启动目标设备</span><span class="sxs-lookup"><span data-stu-id="9de7c-348">Restarts the target device</span></span>

<span data-ttu-id="9de7c-349">**/api/control/shutdown （文章）**</span><span class="sxs-lookup"><span data-stu-id="9de7c-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="9de7c-350">关闭目标设备</span><span class="sxs-lookup"><span data-stu-id="9de7c-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="9de7c-351">任务管理器</span><span class="sxs-lookup"><span data-stu-id="9de7c-351">Task Manager</span></span>

<span data-ttu-id="9de7c-352">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="9de7c-353">停止新型应用程序</span><span class="sxs-lookup"><span data-stu-id="9de7c-353">Stops a modern app</span></span>

<span data-ttu-id="9de7c-354">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-354">Parameters</span></span>
* <span data-ttu-id="9de7c-355">包：完整应用程序包，hex64 编码名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="9de7c-356">强制停止：强制停止所有进程 （= 是）</span><span class="sxs-lookup"><span data-stu-id="9de7c-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="9de7c-357">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="9de7c-358">启动新式应用</span><span class="sxs-lookup"><span data-stu-id="9de7c-358">Starts a modern app</span></span>

<span data-ttu-id="9de7c-359">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-359">Parameters</span></span>
* <span data-ttu-id="9de7c-360">appid:若要启动的应用程序的 PRAID，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="9de7c-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="9de7c-361">包：完整应用程序包，hex64 编码名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="9de7c-362">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="9de7c-362">WiFi Management</span></span>

<span data-ttu-id="9de7c-363">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="9de7c-364">枚举无线网络接口</span><span class="sxs-lookup"><span data-stu-id="9de7c-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="9de7c-365">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-365">Return data</span></span>
* <span data-ttu-id="9de7c-366">无线接口的详细信息 （GUID、 description 等） 的列表</span><span class="sxs-lookup"><span data-stu-id="9de7c-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="9de7c-367">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="9de7c-368">删除与指定接口上的网络相关联的配置文件</span><span class="sxs-lookup"><span data-stu-id="9de7c-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="9de7c-369">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-369">Parameters</span></span>
* <span data-ttu-id="9de7c-370">接口： 网络接口的 guid</span><span class="sxs-lookup"><span data-stu-id="9de7c-370">interface : network interface guid</span></span>
* <span data-ttu-id="9de7c-371">配置文件： 配置文件名称</span><span class="sxs-lookup"><span data-stu-id="9de7c-371">profile : profile name</span></span>

<span data-ttu-id="9de7c-372">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="9de7c-373">枚举指定的网络接口上的无线网络</span><span class="sxs-lookup"><span data-stu-id="9de7c-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="9de7c-374">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-374">Parameters</span></span>
* <span data-ttu-id="9de7c-375">接口： 网络接口的 guid</span><span class="sxs-lookup"><span data-stu-id="9de7c-375">interface : network interface guid</span></span>

<span data-ttu-id="9de7c-376">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-376">Return data</span></span>
* <span data-ttu-id="9de7c-377">找到详细信息的网络接口上的无线网络的列表</span><span class="sxs-lookup"><span data-stu-id="9de7c-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="9de7c-378">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="9de7c-379">连接或断开到指定的接口上的网络</span><span class="sxs-lookup"><span data-stu-id="9de7c-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="9de7c-380">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-380">Parameters</span></span>
* <span data-ttu-id="9de7c-381">接口： 网络接口的 guid</span><span class="sxs-lookup"><span data-stu-id="9de7c-381">interface : network interface guid</span></span>
* <span data-ttu-id="9de7c-382">ssid: ssid，hex64 编码，以连接到</span><span class="sxs-lookup"><span data-stu-id="9de7c-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="9de7c-383">操作： 连接或断开连接</span><span class="sxs-lookup"><span data-stu-id="9de7c-383">op : connect or disconnect</span></span>
* <span data-ttu-id="9de7c-384">createprofile: yes 或 no</span><span class="sxs-lookup"><span data-stu-id="9de7c-384">createprofile : yes or no</span></span>
* <span data-ttu-id="9de7c-385">密钥： 共享密钥，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="9de7c-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="9de7c-386">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="9de7c-386">Windows Performance Recorder</span></span>

<span data-ttu-id="9de7c-387">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="9de7c-388">上传 WPR 配置文件并启动跟踪使用已上传配置文件。</span><span class="sxs-lookup"><span data-stu-id="9de7c-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="9de7c-389">有效负载</span><span class="sxs-lookup"><span data-stu-id="9de7c-389">Payload</span></span>
* <span data-ttu-id="9de7c-390">多部分符合标准的 http 正文</span><span class="sxs-lookup"><span data-stu-id="9de7c-390">multi-part conforming http body</span></span>

<span data-ttu-id="9de7c-391">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-391">Return data</span></span>
* <span data-ttu-id="9de7c-392">返回 WPR 会话状态。</span><span class="sxs-lookup"><span data-stu-id="9de7c-392">Returns the WPR session status.</span></span>

<span data-ttu-id="9de7c-393">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="9de7c-394">检索 WPR 会话的状态</span><span class="sxs-lookup"><span data-stu-id="9de7c-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="9de7c-395">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-395">Return data</span></span>
* <span data-ttu-id="9de7c-396">WPR 会话状态。</span><span class="sxs-lookup"><span data-stu-id="9de7c-396">WPR session status.</span></span>

<span data-ttu-id="9de7c-397">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="9de7c-398">停止 WPR （性能） 跟踪会话</span><span class="sxs-lookup"><span data-stu-id="9de7c-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="9de7c-399">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-399">Return data</span></span>
* <span data-ttu-id="9de7c-400">返回跟踪 ETL 文件</span><span class="sxs-lookup"><span data-stu-id="9de7c-400">Returns the trace ETL file</span></span>

<span data-ttu-id="9de7c-401">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="9de7c-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="9de7c-402">启动跟踪会话 WPR （性能）</span><span class="sxs-lookup"><span data-stu-id="9de7c-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="9de7c-403">Parameters</span><span class="sxs-lookup"><span data-stu-id="9de7c-403">Parameters</span></span>
* <span data-ttu-id="9de7c-404">配置文件：配置文件名称。</span><span class="sxs-lookup"><span data-stu-id="9de7c-404">profile : Profile name.</span></span> <span data-ttu-id="9de7c-405">可用的配置文件存储在 perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="9de7c-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="9de7c-406">返回数据</span><span class="sxs-lookup"><span data-stu-id="9de7c-406">Return data</span></span>
* <span data-ttu-id="9de7c-407">启动时，返回 WPR 会话状态。</span><span class="sxs-lookup"><span data-stu-id="9de7c-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="9de7c-408">请参阅</span><span class="sxs-lookup"><span data-stu-id="9de7c-408">See also</span></span>
* [<span data-ttu-id="9de7c-409">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="9de7c-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="9de7c-410">设备门户 core API 参考 (UWP)</span><span class="sxs-lookup"><span data-stu-id="9de7c-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
