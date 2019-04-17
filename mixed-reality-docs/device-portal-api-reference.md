---
title: 设备门户 API 参考
description: Windows Device Portal HoloLens 上的 API 参考
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，Windows Device Portal API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592656"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="2ca67-104">设备门户 API 参考</span><span class="sxs-lookup"><span data-stu-id="2ca67-104">Device portal API reference</span></span>

<span data-ttu-id="2ca67-105">中的所有内容[Windows Device Portal](using-the-windows-device-portal.md)为基础构建 REST API 可用于访问数据，并以编程方式控制你的设备。</span><span class="sxs-lookup"><span data-stu-id="2ca67-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="2ca67-106">应用程序出现的常见问题</span><span class="sxs-lookup"><span data-stu-id="2ca67-106">App deloyment</span></span>

<span data-ttu-id="2ca67-107">**/api/app/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="2ca67-108">卸载应用</span><span class="sxs-lookup"><span data-stu-id="2ca67-108">Uninstalls an app</span></span>

<span data-ttu-id="2ca67-109">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-109">Parameters</span></span>
* <span data-ttu-id="2ca67-110">包：要卸载的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="2ca67-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="2ca67-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="2ca67-112">安装应用</span><span class="sxs-lookup"><span data-stu-id="2ca67-112">Installs an App</span></span>

<span data-ttu-id="2ca67-113">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-113">Parameters</span></span>
* <span data-ttu-id="2ca67-114">包：要安装的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="2ca67-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="2ca67-115">有效负载</span><span class="sxs-lookup"><span data-stu-id="2ca67-115">Payload</span></span>
* <span data-ttu-id="2ca67-116">多部分符合标准的 http 正文</span><span class="sxs-lookup"><span data-stu-id="2ca67-116">multi-part conforming http body</span></span>

<span data-ttu-id="2ca67-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="2ca67-118">检索具有详细信息的系统上已安装应用的列表</span><span class="sxs-lookup"><span data-stu-id="2ca67-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="2ca67-119">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-119">Return data</span></span>
* <span data-ttu-id="2ca67-120">已安装程序包的详细信息列表</span><span class="sxs-lookup"><span data-stu-id="2ca67-120">List of installed packages with details</span></span>

<span data-ttu-id="2ca67-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="2ca67-122">获取正在进行应用安装中的状态</span><span class="sxs-lookup"><span data-stu-id="2ca67-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="2ca67-123">转储集合</span><span class="sxs-lookup"><span data-stu-id="2ca67-123">Dump collection</span></span>

<span data-ttu-id="2ca67-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="2ca67-125">禁用的故障转储集合旁加载应用</span><span class="sxs-lookup"><span data-stu-id="2ca67-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="2ca67-126">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-126">Parameters</span></span>
* <span data-ttu-id="2ca67-127">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-127">packageFullname : package name</span></span>

<span data-ttu-id="2ca67-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="2ca67-129">获取旁加载应用设置故障转储收集</span><span class="sxs-lookup"><span data-stu-id="2ca67-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="2ca67-130">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-130">Parameters</span></span>
* <span data-ttu-id="2ca67-131">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-131">packageFullname : package name</span></span>

<span data-ttu-id="2ca67-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="2ca67-133">启用并设置旁加载应用程序的转储控制设置</span><span class="sxs-lookup"><span data-stu-id="2ca67-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="2ca67-134">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-134">Parameters</span></span>
* <span data-ttu-id="2ca67-135">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-135">packageFullname : package name</span></span>

<span data-ttu-id="2ca67-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="2ca67-137">删除旁加载应用程序的故障转储</span><span class="sxs-lookup"><span data-stu-id="2ca67-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="2ca67-138">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-138">Parameters</span></span>
* <span data-ttu-id="2ca67-139">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-139">packageFullname : package name</span></span>
* <span data-ttu-id="2ca67-140">fileName： 转储文件的名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-140">fileName : dump file name</span></span>

<span data-ttu-id="2ca67-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="2ca67-142">检索的故障转储的旁加载应用</span><span class="sxs-lookup"><span data-stu-id="2ca67-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="2ca67-143">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-143">Parameters</span></span>
* <span data-ttu-id="2ca67-144">packageFullname： 包名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-144">packageFullname : package name</span></span>
* <span data-ttu-id="2ca67-145">fileName： 转储文件的名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-145">fileName : dump file name</span></span>

<span data-ttu-id="2ca67-146">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-146">Return data</span></span>
* <span data-ttu-id="2ca67-147">转储文件。</span><span class="sxs-lookup"><span data-stu-id="2ca67-147">Dump file.</span></span> <span data-ttu-id="2ca67-148">检查使用 WinDbg 或 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ca67-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="2ca67-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="2ca67-150">返回所有的故障转储的旁加载应用的列表</span><span class="sxs-lookup"><span data-stu-id="2ca67-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="2ca67-151">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-151">Return data</span></span>
* <span data-ttu-id="2ca67-152">每个端加载应用的列表中的故障转储</span><span class="sxs-lookup"><span data-stu-id="2ca67-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="2ca67-153">ETW</span><span class="sxs-lookup"><span data-stu-id="2ca67-153">ETW</span></span>

<span data-ttu-id="2ca67-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="2ca67-155">枚举已注册的提供程序</span><span class="sxs-lookup"><span data-stu-id="2ca67-155">Enumerates registered providers</span></span>

<span data-ttu-id="2ca67-156">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-156">Return data</span></span>
* <span data-ttu-id="2ca67-157">提供程序、 友好名称和 GUID 的列表</span><span class="sxs-lookup"><span data-stu-id="2ca67-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="2ca67-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="2ca67-159">创建实时的 ETW 会话;通过 websocket 进行管理。</span><span class="sxs-lookup"><span data-stu-id="2ca67-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="2ca67-160">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-160">Return data</span></span>
* <span data-ttu-id="2ca67-161">从已启用提供程序的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="2ca67-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="2ca67-162">全息操作系统</span><span class="sxs-lookup"><span data-stu-id="2ca67-162">Holographic OS</span></span>

<span data-ttu-id="2ca67-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="2ca67-164">返回一系列 HoloLens 特定 ETW 提供程序未注册与系统</span><span class="sxs-lookup"><span data-stu-id="2ca67-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="2ca67-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="2ca67-166">返回运行的所有服务的状态。</span><span class="sxs-lookup"><span data-stu-id="2ca67-166">Returns the states of all services running.</span></span>

<span data-ttu-id="2ca67-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="2ca67-168">获取以毫米为单位存储的 IPD （Interpupillary 距离）</span><span class="sxs-lookup"><span data-stu-id="2ca67-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="2ca67-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="2ca67-170">设置 IPD</span><span class="sxs-lookup"><span data-stu-id="2ca67-170">Sets the IPD</span></span>

<span data-ttu-id="2ca67-171">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-171">Parameters</span></span>
* <span data-ttu-id="2ca67-172">ipd:要以毫米为单位设置的新 IPD 值</span><span class="sxs-lookup"><span data-stu-id="2ca67-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="2ca67-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="2ca67-174">获取 Device Portal 的 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="2ca67-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="2ca67-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="2ca67-176">设置 HTTPS 要求设备门户</span><span class="sxs-lookup"><span data-stu-id="2ca67-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="2ca67-177">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-177">Parameters</span></span>
* <span data-ttu-id="2ca67-178">必需： yes、 no 或默认值</span><span class="sxs-lookup"><span data-stu-id="2ca67-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="2ca67-179">Holographic 感知</span><span class="sxs-lookup"><span data-stu-id="2ca67-179">Holographic Perception</span></span>

<span data-ttu-id="2ca67-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="2ca67-181">接受 websocket 升级并运行 30 fps 时发送更新的感知客户端。</span><span class="sxs-lookup"><span data-stu-id="2ca67-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="2ca67-182">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-182">Parameters</span></span>
* <span data-ttu-id="2ca67-183">clientmode:"活动"时强制进行可视化跟踪模式下无法被动建立</span><span class="sxs-lookup"><span data-stu-id="2ca67-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="2ca67-184">Holographic 温度</span><span class="sxs-lookup"><span data-stu-id="2ca67-184">Holographic Thermal</span></span>

<span data-ttu-id="2ca67-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="2ca67-186">获取设备 （0 正常，1 热，关键 2） 的热量阶段</span><span class="sxs-lookup"><span data-stu-id="2ca67-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="2ca67-187">Perception 模拟控件</span><span class="sxs-lookup"><span data-stu-id="2ca67-187">Perception Simulation Control</span></span>

<span data-ttu-id="2ca67-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="2ca67-189">获取的模拟模式</span><span class="sxs-lookup"><span data-stu-id="2ca67-189">Get the simulation mode</span></span>

<span data-ttu-id="2ca67-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="2ca67-191">设置模拟模式</span><span class="sxs-lookup"><span data-stu-id="2ca67-191">Set the simulation mode</span></span>

<span data-ttu-id="2ca67-192">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-192">Parameters</span></span>
* <span data-ttu-id="2ca67-193">模式： 模拟模式： 默认、 模拟、 远程，旧</span><span class="sxs-lookup"><span data-stu-id="2ca67-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="2ca67-194">**/api/holographic/simulation/control/stream （删除）**</span><span class="sxs-lookup"><span data-stu-id="2ca67-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="2ca67-195">删除控制流。</span><span class="sxs-lookup"><span data-stu-id="2ca67-195">Delete a control stream.</span></span>

<span data-ttu-id="2ca67-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="2ca67-197">打开的控制流的 web 套接字连接。</span><span class="sxs-lookup"><span data-stu-id="2ca67-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="2ca67-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="2ca67-199">创建控制流 （优先级是必需的） 或将数据发布到创建的流 (所需的 streamId)。</span><span class="sxs-lookup"><span data-stu-id="2ca67-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="2ca67-200">已发布的数据应为类型应用程序/八进制流。</span><span class="sxs-lookup"><span data-stu-id="2ca67-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="2ca67-201">Perception 模拟播放</span><span class="sxs-lookup"><span data-stu-id="2ca67-201">Perception Simulation Playback</span></span>

<span data-ttu-id="2ca67-202">**/api/holographic/simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="2ca67-203">删除录制。</span><span class="sxs-lookup"><span data-stu-id="2ca67-203">Delete a recording.</span></span>

<span data-ttu-id="2ca67-204">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-204">Parameters</span></span>
* <span data-ttu-id="2ca67-205">录制：若要删除的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="2ca67-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="2ca67-207">将录制内容上传。</span><span class="sxs-lookup"><span data-stu-id="2ca67-207">Upload a recording.</span></span>

<span data-ttu-id="2ca67-208">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="2ca67-209">获取所有录制。</span><span class="sxs-lookup"><span data-stu-id="2ca67-209">Get all recordings.</span></span>

<span data-ttu-id="2ca67-210">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="2ca67-211">获取记录的当前播放状态。</span><span class="sxs-lookup"><span data-stu-id="2ca67-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="2ca67-212">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-212">Parameters</span></span>
* <span data-ttu-id="2ca67-213">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-213">recording : Name of recording.</span></span>

<span data-ttu-id="2ca67-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="2ca67-215">卸载录制。</span><span class="sxs-lookup"><span data-stu-id="2ca67-215">Unload a recording.</span></span>

<span data-ttu-id="2ca67-216">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-216">Parameters</span></span>
* <span data-ttu-id="2ca67-217">录制：记录要卸载的名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="2ca67-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="2ca67-219">加载录制。</span><span class="sxs-lookup"><span data-stu-id="2ca67-219">Load a recording.</span></span>

<span data-ttu-id="2ca67-220">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-220">Parameters</span></span>
* <span data-ttu-id="2ca67-221">录制：记录要加载的名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="2ca67-222">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="2ca67-223">获取所有已加载的记录。</span><span class="sxs-lookup"><span data-stu-id="2ca67-223">Get all loaded recordings.</span></span>

<span data-ttu-id="2ca67-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="2ca67-225">暂停录制。</span><span class="sxs-lookup"><span data-stu-id="2ca67-225">Pause a recording.</span></span>

<span data-ttu-id="2ca67-226">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-226">Parameters</span></span>
* <span data-ttu-id="2ca67-227">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-227">recording : Name of recording.</span></span>

<span data-ttu-id="2ca67-228">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="2ca67-229">播放录制内容。</span><span class="sxs-lookup"><span data-stu-id="2ca67-229">Play a recording.</span></span>

<span data-ttu-id="2ca67-230">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-230">Parameters</span></span>
* <span data-ttu-id="2ca67-231">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-231">recording : Name of recording.</span></span>

<span data-ttu-id="2ca67-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="2ca67-233">停止录制。</span><span class="sxs-lookup"><span data-stu-id="2ca67-233">Stop a recording.</span></span>

<span data-ttu-id="2ca67-234">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-234">Parameters</span></span>
* <span data-ttu-id="2ca67-235">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-235">recording : Name of recording.</span></span>

<span data-ttu-id="2ca67-236">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="2ca67-237">获取加载录制中的数据类型。</span><span class="sxs-lookup"><span data-stu-id="2ca67-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="2ca67-238">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-238">Parameters</span></span>
* <span data-ttu-id="2ca67-239">录制：录制的名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="2ca67-240">Perception 模拟录制</span><span class="sxs-lookup"><span data-stu-id="2ca67-240">Perception Simulation Recording</span></span>

<span data-ttu-id="2ca67-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="2ca67-242">开始录制。</span><span class="sxs-lookup"><span data-stu-id="2ca67-242">Start a recording.</span></span> <span data-ttu-id="2ca67-243">仅单个记录可以同时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="2ca67-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="2ca67-244">必须设置为 head、 手、 spatialMapping 或环境。</span><span class="sxs-lookup"><span data-stu-id="2ca67-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="2ca67-245">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-245">Parameters</span></span>
* <span data-ttu-id="2ca67-246">头：将设置为 1 到记录头数据。</span><span class="sxs-lookup"><span data-stu-id="2ca67-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="2ca67-247">手：设置为 1 以记录现有数据。</span><span class="sxs-lookup"><span data-stu-id="2ca67-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="2ca67-248">spatialMapping:设置为 1 来记录空间映射。</span><span class="sxs-lookup"><span data-stu-id="2ca67-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="2ca67-249">环境：设置为 1 以记录环境数据。</span><span class="sxs-lookup"><span data-stu-id="2ca67-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="2ca67-250">名称：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-250">name : Name of the recording.</span></span>
* <span data-ttu-id="2ca67-251">singleSpatialMappingFrame:设置为 1 来记录仅一个空间映射框架。</span><span class="sxs-lookup"><span data-stu-id="2ca67-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="2ca67-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="2ca67-253">获取正在记录状态。</span><span class="sxs-lookup"><span data-stu-id="2ca67-253">Get recording state.</span></span>

<span data-ttu-id="2ca67-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="2ca67-255">停止当前录制。</span><span class="sxs-lookup"><span data-stu-id="2ca67-255">Stop the current recording.</span></span> <span data-ttu-id="2ca67-256">录制将返回为一个文件。</span><span class="sxs-lookup"><span data-stu-id="2ca67-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="2ca67-257">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="2ca67-257">Mixed Reality Capture</span></span>

<span data-ttu-id="2ca67-258">**/api/holographic/mrc/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-258">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="2ca67-259">删除设备中记录了混合的现实。</span><span class="sxs-lookup"><span data-stu-id="2ca67-259">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="2ca67-260">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-260">Parameters</span></span>
* <span data-ttu-id="2ca67-261">文件名：编码的要删除的文件的名称，hex64</span><span class="sxs-lookup"><span data-stu-id="2ca67-261">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="2ca67-262">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-262">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="2ca67-263">获取默认混合现实捕获设置</span><span class="sxs-lookup"><span data-stu-id="2ca67-263">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="2ca67-264">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-264">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="2ca67-265">从设备下载混合的现实文件。</span><span class="sxs-lookup"><span data-stu-id="2ca67-265">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="2ca67-266">使用 op = 流式处理的流查询参数。</span><span class="sxs-lookup"><span data-stu-id="2ca67-266">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="2ca67-267">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-267">Parameters</span></span>
* <span data-ttu-id="2ca67-268">文件名：编码的要获取的视频文件的名称，hex64</span><span class="sxs-lookup"><span data-stu-id="2ca67-268">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="2ca67-269">操作： 流</span><span class="sxs-lookup"><span data-stu-id="2ca67-269">op : stream</span></span>

<span data-ttu-id="2ca67-270">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-270">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="2ca67-271">获取指定的文件的缩略图。</span><span class="sxs-lookup"><span data-stu-id="2ca67-271">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="2ca67-272">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-272">Parameters</span></span>
* <span data-ttu-id="2ca67-273">文件名：编码为其请求缩略图的文件的名称，hex64</span><span class="sxs-lookup"><span data-stu-id="2ca67-273">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="2ca67-274">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-274">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="2ca67-275">获取混合现实的记录 （运行、 已停止） 状态</span><span class="sxs-lookup"><span data-stu-id="2ca67-275">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="2ca67-276">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-276">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="2ca67-277">返回存储在设备上的混合的现实文件列表</span><span class="sxs-lookup"><span data-stu-id="2ca67-277">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="2ca67-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="2ca67-279">设置默认混合现实捕获设置</span><span class="sxs-lookup"><span data-stu-id="2ca67-279">Sets the default mixed reality capture settings</span></span>

<span data-ttu-id="2ca67-280">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-280">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="2ca67-281">启动混合的现实录制</span><span class="sxs-lookup"><span data-stu-id="2ca67-281">Starts a mixed reality recording</span></span>

<span data-ttu-id="2ca67-282">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-282">Parameters</span></span>
* <span data-ttu-id="2ca67-283">holo： 捕获全息： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-283">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="2ca67-284">pv： 捕获 PV 照相机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-284">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="2ca67-285">mic： 捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-285">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="2ca67-286">环回： 捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-286">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="2ca67-287">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-287">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="2ca67-288">停止当前混合现实录制</span><span class="sxs-lookup"><span data-stu-id="2ca67-288">Stops the current mixed reality recording</span></span>

<span data-ttu-id="2ca67-289">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-289">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="2ca67-290">采用混合的现实照片，并创建在设备上的文件</span><span class="sxs-lookup"><span data-stu-id="2ca67-290">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="2ca67-291">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-291">Parameters</span></span>
* <span data-ttu-id="2ca67-292">holo： 捕获全息： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-292">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="2ca67-293">pv： 捕获 PV 照相机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-293">pv : capture PV camera: true or false</span></span>

<span data-ttu-id="2ca67-294">流式处理的混合的现实</span><span class="sxs-lookup"><span data-stu-id="2ca67-294">Mixed Reality Streaming</span></span>

<span data-ttu-id="2ca67-295">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-295">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="2ca67-296">启动碎片 mp4 的分块下载</span><span class="sxs-lookup"><span data-stu-id="2ca67-296">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="2ca67-297">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-297">Parameters</span></span>
* <span data-ttu-id="2ca67-298">holo： 捕获全息： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-298">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="2ca67-299">pv： 捕获 PV 照相机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-299">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="2ca67-300">mic： 捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-300">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="2ca67-301">环回： 捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-301">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="2ca67-302">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-302">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="2ca67-303">启动碎片 mp4 的分块下载</span><span class="sxs-lookup"><span data-stu-id="2ca67-303">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="2ca67-304">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-304">Parameters</span></span>
* <span data-ttu-id="2ca67-305">holo： 捕获全息： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="2ca67-306">pv： 捕获 PV 照相机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="2ca67-307">mic： 捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="2ca67-308">环回： 捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="2ca67-309">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-309">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="2ca67-310">启动碎片 mp4 的分块下载</span><span class="sxs-lookup"><span data-stu-id="2ca67-310">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="2ca67-311">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-311">Parameters</span></span>
* <span data-ttu-id="2ca67-312">holo： 捕获全息： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-312">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="2ca67-313">pv： 捕获 PV 照相机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-313">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="2ca67-314">mic： 捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-314">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="2ca67-315">环回： 捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-315">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="2ca67-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="2ca67-317">启动碎片 mp4 的分块下载</span><span class="sxs-lookup"><span data-stu-id="2ca67-317">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="2ca67-318">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-318">Parameters</span></span>
* <span data-ttu-id="2ca67-319">holo： 捕获全息： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-319">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="2ca67-320">pv： 捕获 PV 照相机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-320">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="2ca67-321">mic： 捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-321">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="2ca67-322">环回： 捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="2ca67-322">loopback : capture app audio: true or false</span></span>

## <a name="networking"></a><span data-ttu-id="2ca67-323">网络</span><span class="sxs-lookup"><span data-stu-id="2ca67-323">Networking</span></span>

<span data-ttu-id="2ca67-324">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="2ca67-325">获取当前的 ip 配置</span><span class="sxs-lookup"><span data-stu-id="2ca67-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="2ca67-326">OS 信息</span><span class="sxs-lookup"><span data-stu-id="2ca67-326">OS Information</span></span>

<span data-ttu-id="2ca67-327">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="2ca67-328">获取操作系统信息</span><span class="sxs-lookup"><span data-stu-id="2ca67-328">Gets operating system information</span></span>

<span data-ttu-id="2ca67-329">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="2ca67-330">获取计算机名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-330">Gets the machine name</span></span>

<span data-ttu-id="2ca67-331">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="2ca67-332">设置计算机名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-332">Sets the machine name</span></span>

<span data-ttu-id="2ca67-333">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-333">Parameters</span></span>
* <span data-ttu-id="2ca67-334">名称：新的计算机名称，hex64 编码，将设置为</span><span class="sxs-lookup"><span data-stu-id="2ca67-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="2ca67-335">性能数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-335">Performance data</span></span>

<span data-ttu-id="2ca67-336">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="2ca67-337">返回正在运行进程的详细信息的列表</span><span class="sxs-lookup"><span data-stu-id="2ca67-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="2ca67-338">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-338">Return data</span></span>
* <span data-ttu-id="2ca67-339">与进程和每个进程的详细信息的列表的 JSON</span><span class="sxs-lookup"><span data-stu-id="2ca67-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="2ca67-340">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="2ca67-341">返回系统性能统计信息 （I/O 读/写、 内存统计信息等。</span><span class="sxs-lookup"><span data-stu-id="2ca67-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="2ca67-342">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-342">Return data</span></span>
* <span data-ttu-id="2ca67-343">系统信息的 JSON:CPU、 GPU、 内存、 网络、 IO</span><span class="sxs-lookup"><span data-stu-id="2ca67-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="2ca67-344">电源</span><span class="sxs-lookup"><span data-stu-id="2ca67-344">Power</span></span>

<span data-ttu-id="2ca67-345">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="2ca67-346">获取当前的电池状态</span><span class="sxs-lookup"><span data-stu-id="2ca67-346">Gets the current battery state</span></span>

<span data-ttu-id="2ca67-347">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="2ca67-348">检查系统是否在低功耗状态</span><span class="sxs-lookup"><span data-stu-id="2ca67-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="2ca67-349">远程控制</span><span class="sxs-lookup"><span data-stu-id="2ca67-349">Remote Control</span></span>

<span data-ttu-id="2ca67-350">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="2ca67-351">重新启动目标设备</span><span class="sxs-lookup"><span data-stu-id="2ca67-351">Restarts the target device</span></span>

<span data-ttu-id="2ca67-352">**/api/control/shutdown （文章）**</span><span class="sxs-lookup"><span data-stu-id="2ca67-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="2ca67-353">关闭目标设备</span><span class="sxs-lookup"><span data-stu-id="2ca67-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="2ca67-354">任务管理器</span><span class="sxs-lookup"><span data-stu-id="2ca67-354">Task Manager</span></span>

<span data-ttu-id="2ca67-355">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="2ca67-356">停止新型应用程序</span><span class="sxs-lookup"><span data-stu-id="2ca67-356">Stops a modern app</span></span>

<span data-ttu-id="2ca67-357">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-357">Parameters</span></span>
* <span data-ttu-id="2ca67-358">包：完整应用程序包，hex64 编码名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="2ca67-359">强制停止：强制停止所有进程 （= 是）</span><span class="sxs-lookup"><span data-stu-id="2ca67-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="2ca67-360">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="2ca67-361">启动新式应用</span><span class="sxs-lookup"><span data-stu-id="2ca67-361">Starts a modern app</span></span>

<span data-ttu-id="2ca67-362">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-362">Parameters</span></span>
* <span data-ttu-id="2ca67-363">appid:若要启动的应用程序的 PRAID，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="2ca67-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="2ca67-364">包：完整应用程序包，hex64 编码名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="2ca67-365">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="2ca67-365">WiFi Management</span></span>

<span data-ttu-id="2ca67-366">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="2ca67-367">枚举无线网络接口</span><span class="sxs-lookup"><span data-stu-id="2ca67-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="2ca67-368">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-368">Return data</span></span>
* <span data-ttu-id="2ca67-369">无线接口的详细信息 （GUID、 description 等） 的列表</span><span class="sxs-lookup"><span data-stu-id="2ca67-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="2ca67-370">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="2ca67-371">删除与指定接口上的网络相关联的配置文件</span><span class="sxs-lookup"><span data-stu-id="2ca67-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="2ca67-372">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-372">Parameters</span></span>
* <span data-ttu-id="2ca67-373">接口： 网络接口的 guid</span><span class="sxs-lookup"><span data-stu-id="2ca67-373">interface : network interface guid</span></span>
* <span data-ttu-id="2ca67-374">配置文件： 配置文件名称</span><span class="sxs-lookup"><span data-stu-id="2ca67-374">profile : profile name</span></span>

<span data-ttu-id="2ca67-375">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="2ca67-376">枚举指定的网络接口上的无线网络</span><span class="sxs-lookup"><span data-stu-id="2ca67-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="2ca67-377">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-377">Parameters</span></span>
* <span data-ttu-id="2ca67-378">接口： 网络接口的 guid</span><span class="sxs-lookup"><span data-stu-id="2ca67-378">interface : network interface guid</span></span>

<span data-ttu-id="2ca67-379">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-379">Return data</span></span>
* <span data-ttu-id="2ca67-380">找到详细信息的网络接口上的无线网络的列表</span><span class="sxs-lookup"><span data-stu-id="2ca67-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="2ca67-381">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="2ca67-382">连接或断开到指定的接口上的网络</span><span class="sxs-lookup"><span data-stu-id="2ca67-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="2ca67-383">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-383">Parameters</span></span>
* <span data-ttu-id="2ca67-384">接口： 网络接口的 guid</span><span class="sxs-lookup"><span data-stu-id="2ca67-384">interface : network interface guid</span></span>
* <span data-ttu-id="2ca67-385">ssid: ssid，hex64 编码，以连接到</span><span class="sxs-lookup"><span data-stu-id="2ca67-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="2ca67-386">操作： 连接或断开连接</span><span class="sxs-lookup"><span data-stu-id="2ca67-386">op : connect or disconnect</span></span>
* <span data-ttu-id="2ca67-387">createprofile: yes 或 no</span><span class="sxs-lookup"><span data-stu-id="2ca67-387">createprofile : yes or no</span></span>
* <span data-ttu-id="2ca67-388">密钥： 共享密钥，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="2ca67-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="2ca67-389">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="2ca67-389">Windows Performance Recorder</span></span>

<span data-ttu-id="2ca67-390">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="2ca67-391">上传 WPR 配置文件并启动跟踪使用已上传配置文件。</span><span class="sxs-lookup"><span data-stu-id="2ca67-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="2ca67-392">有效负载</span><span class="sxs-lookup"><span data-stu-id="2ca67-392">Payload</span></span>
* <span data-ttu-id="2ca67-393">多部分符合标准的 http 正文</span><span class="sxs-lookup"><span data-stu-id="2ca67-393">multi-part conforming http body</span></span>

<span data-ttu-id="2ca67-394">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-394">Return data</span></span>
* <span data-ttu-id="2ca67-395">返回 WPR 会话状态。</span><span class="sxs-lookup"><span data-stu-id="2ca67-395">Returns the WPR session status.</span></span>

<span data-ttu-id="2ca67-396">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="2ca67-397">检索 WPR 会话的状态</span><span class="sxs-lookup"><span data-stu-id="2ca67-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="2ca67-398">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-398">Return data</span></span>
* <span data-ttu-id="2ca67-399">WPR 会话状态。</span><span class="sxs-lookup"><span data-stu-id="2ca67-399">WPR session status.</span></span>

<span data-ttu-id="2ca67-400">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="2ca67-401">停止 WPR （性能） 跟踪会话</span><span class="sxs-lookup"><span data-stu-id="2ca67-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="2ca67-402">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-402">Return data</span></span>
* <span data-ttu-id="2ca67-403">返回跟踪 ETL 文件</span><span class="sxs-lookup"><span data-stu-id="2ca67-403">Returns the trace ETL file</span></span>

<span data-ttu-id="2ca67-404">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="2ca67-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="2ca67-405">启动跟踪会话 WPR （性能）</span><span class="sxs-lookup"><span data-stu-id="2ca67-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="2ca67-406">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ca67-406">Parameters</span></span>
* <span data-ttu-id="2ca67-407">配置文件：配置文件名称。</span><span class="sxs-lookup"><span data-stu-id="2ca67-407">profile : Profile name.</span></span> <span data-ttu-id="2ca67-408">可用的配置文件存储在 perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="2ca67-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="2ca67-409">返回数据</span><span class="sxs-lookup"><span data-stu-id="2ca67-409">Return data</span></span>
* <span data-ttu-id="2ca67-410">启动时，返回 WPR 会话状态。</span><span class="sxs-lookup"><span data-stu-id="2ca67-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ca67-411">请参阅</span><span class="sxs-lookup"><span data-stu-id="2ca67-411">See also</span></span>
* [<span data-ttu-id="2ca67-412">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="2ca67-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="2ca67-413">设备门户 core API 参考 (UWP)</span><span class="sxs-lookup"><span data-stu-id="2ca67-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
