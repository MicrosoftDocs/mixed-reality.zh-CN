---
title: 设备门户 API 参考
description: HoloLens 上 Windows 设备门户的 API 参考
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、Windows 设备门户、API
ms.openlocfilehash: 236de35c2c736fc5a0289b7be1f1548f0a08fa26
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278235"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="67e33-104">设备门户 API 参考</span><span class="sxs-lookup"><span data-stu-id="67e33-104">Device portal API reference</span></span>

<span data-ttu-id="67e33-105">[Windows 设备门户](using-the-windows-device-portal.md)中的所有内容都是在 REST API 的基础之上构建的，你可以使用它以编程方式访问数据和控制设备。</span><span class="sxs-lookup"><span data-stu-id="67e33-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="67e33-106">应用常见问题</span><span class="sxs-lookup"><span data-stu-id="67e33-106">App deloyment</span></span>

<span data-ttu-id="67e33-107">**/api/app/packagemanager/package （删除）**</span><span class="sxs-lookup"><span data-stu-id="67e33-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="67e33-108">卸载应用</span><span class="sxs-lookup"><span data-stu-id="67e33-108">Uninstalls an app</span></span>

<span data-ttu-id="67e33-109">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-109">Parameters</span></span>
* <span data-ttu-id="67e33-110">package：要卸载的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="67e33-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="67e33-111">**/api/app/packagemanager/package （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="67e33-112">安装应用程序</span><span class="sxs-lookup"><span data-stu-id="67e33-112">Installs an App</span></span>

<span data-ttu-id="67e33-113">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-113">Parameters</span></span>
* <span data-ttu-id="67e33-114">package：要安装的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="67e33-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="67e33-115">负载</span><span class="sxs-lookup"><span data-stu-id="67e33-115">Payload</span></span>
* <span data-ttu-id="67e33-116">多部分相容的 http 正文</span><span class="sxs-lookup"><span data-stu-id="67e33-116">multi-part conforming http body</span></span>

<span data-ttu-id="67e33-117">**/api/app/packagemanager/packages （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="67e33-118">检索系统上已安装应用的列表，详细信息</span><span class="sxs-lookup"><span data-stu-id="67e33-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="67e33-119">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-119">Return data</span></span>
* <span data-ttu-id="67e33-120">包含详细信息的已安装包列表</span><span class="sxs-lookup"><span data-stu-id="67e33-120">List of installed packages with details</span></span>

<span data-ttu-id="67e33-121">**/api/app/packagemanager/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="67e33-122">获取正在进行的应用安装的状态</span><span class="sxs-lookup"><span data-stu-id="67e33-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="67e33-123">转储集合</span><span class="sxs-lookup"><span data-stu-id="67e33-123">Dump collection</span></span>

<span data-ttu-id="67e33-124">**/api/debug/dump/usermode/crashcontrol （删除）**</span><span class="sxs-lookup"><span data-stu-id="67e33-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="67e33-125">为旁加载应用禁用故障转储收集</span><span class="sxs-lookup"><span data-stu-id="67e33-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="67e33-126">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-126">Parameters</span></span>
* <span data-ttu-id="67e33-127">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="67e33-127">packageFullname : package name</span></span>

<span data-ttu-id="67e33-128">**/api/debug/dump/usermode/crashcontrol （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="67e33-129">获取旁加载应用故障转储收集的设置</span><span class="sxs-lookup"><span data-stu-id="67e33-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="67e33-130">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-130">Parameters</span></span>
* <span data-ttu-id="67e33-131">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="67e33-131">packageFullname : package name</span></span>

<span data-ttu-id="67e33-132">**/api/debug/dump/usermode/crashcontrol （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="67e33-133">启用和设置旁加载应用的转储控件设置</span><span class="sxs-lookup"><span data-stu-id="67e33-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="67e33-134">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-134">Parameters</span></span>
* <span data-ttu-id="67e33-135">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="67e33-135">packageFullname : package name</span></span>

<span data-ttu-id="67e33-136">**/api/debug/dump/usermode/crashdump （删除）**</span><span class="sxs-lookup"><span data-stu-id="67e33-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="67e33-137">删除旁加载应用程序的故障转储</span><span class="sxs-lookup"><span data-stu-id="67e33-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="67e33-138">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-138">Parameters</span></span>
* <span data-ttu-id="67e33-139">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="67e33-139">packageFullname : package name</span></span>
* <span data-ttu-id="67e33-140">文件名：转储文件名</span><span class="sxs-lookup"><span data-stu-id="67e33-140">fileName : dump file name</span></span>

<span data-ttu-id="67e33-141">**/api/debug/dump/usermode/crashdump （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="67e33-142">检索旁加载应用的故障转储</span><span class="sxs-lookup"><span data-stu-id="67e33-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="67e33-143">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-143">Parameters</span></span>
* <span data-ttu-id="67e33-144">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="67e33-144">packageFullname : package name</span></span>
* <span data-ttu-id="67e33-145">文件名：转储文件名</span><span class="sxs-lookup"><span data-stu-id="67e33-145">fileName : dump file name</span></span>

<span data-ttu-id="67e33-146">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-146">Return data</span></span>
* <span data-ttu-id="67e33-147">转储文件。</span><span class="sxs-lookup"><span data-stu-id="67e33-147">Dump file.</span></span> <span data-ttu-id="67e33-148">与 WinDbg 或 Visual Studio 一起检查</span><span class="sxs-lookup"><span data-stu-id="67e33-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="67e33-149">**/api/debug/dump/usermode/dumps （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="67e33-150">返回旁加载应用的所有崩溃转储的列表</span><span class="sxs-lookup"><span data-stu-id="67e33-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="67e33-151">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-151">Return data</span></span>
* <span data-ttu-id="67e33-152">每端加载的应用的故障转储列表</span><span class="sxs-lookup"><span data-stu-id="67e33-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="67e33-153">ETW</span><span class="sxs-lookup"><span data-stu-id="67e33-153">ETW</span></span>

<span data-ttu-id="67e33-154">**/api/etw/providers （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="67e33-155">枚举注册的提供程序</span><span class="sxs-lookup"><span data-stu-id="67e33-155">Enumerates registered providers</span></span>

<span data-ttu-id="67e33-156">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-156">Return data</span></span>
* <span data-ttu-id="67e33-157">提供程序列表、友好名称和 GUID</span><span class="sxs-lookup"><span data-stu-id="67e33-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="67e33-158">**/api/etw/session/realtime （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="67e33-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="67e33-159">创建实时 ETW 会话;通过 websocket 进行管理。</span><span class="sxs-lookup"><span data-stu-id="67e33-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="67e33-160">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-160">Return data</span></span>
* <span data-ttu-id="67e33-161">已启用的提供程序中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="67e33-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="67e33-162">全息操作系统</span><span class="sxs-lookup"><span data-stu-id="67e33-162">Holographic OS</span></span>

<span data-ttu-id="67e33-163">**/api/holographic/os/etw/customproviders （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="67e33-164">返回未向系统注册的 HoloLens 特定 ETW 提供程序的列表</span><span class="sxs-lookup"><span data-stu-id="67e33-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="67e33-165">**/api/holographic/os/services （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="67e33-166">返回所有正在运行的服务的状态。</span><span class="sxs-lookup"><span data-stu-id="67e33-166">Returns the states of all services running.</span></span>

<span data-ttu-id="67e33-167">**/api/holographic/os/settings/ipd （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="67e33-168">获取存储的 IPD （Interpupillary 距离）（以毫米为单位）</span><span class="sxs-lookup"><span data-stu-id="67e33-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="67e33-169">**/api/holographic/os/settings/ipd （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="67e33-170">设置 IPD</span><span class="sxs-lookup"><span data-stu-id="67e33-170">Sets the IPD</span></span>

<span data-ttu-id="67e33-171">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-171">Parameters</span></span>
* <span data-ttu-id="67e33-172">ipd：要设置的新 IPD 值（以毫米为单位）</span><span class="sxs-lookup"><span data-stu-id="67e33-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="67e33-173">**/api/holographic/os/webmanagement/settings/https （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="67e33-174">获取 Device Portal 的 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="67e33-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="67e33-175">**/api/holographic/os/webmanagement/settings/https （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="67e33-176">为设备门户设置 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="67e33-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="67e33-177">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-177">Parameters</span></span>
* <span data-ttu-id="67e33-178">必需：是、否或默认值</span><span class="sxs-lookup"><span data-stu-id="67e33-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="67e33-179">全息认知</span><span class="sxs-lookup"><span data-stu-id="67e33-179">Holographic Perception</span></span>

<span data-ttu-id="67e33-180">**/api/holographic/perception/client （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="67e33-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="67e33-181">接受 websocket 升级，并运行以 30 fps 发送更新的感知客户端。</span><span class="sxs-lookup"><span data-stu-id="67e33-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="67e33-182">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-182">Parameters</span></span>
* <span data-ttu-id="67e33-183">clientmode： "active" 强制在无法被动建立时强制视觉跟踪模式</span><span class="sxs-lookup"><span data-stu-id="67e33-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="67e33-184">全息热量</span><span class="sxs-lookup"><span data-stu-id="67e33-184">Holographic Thermal</span></span>

<span data-ttu-id="67e33-185">**/api/holographic/thermal/stage （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="67e33-186">获取设备的热阶段（0正常，1温，2严重）</span><span class="sxs-lookup"><span data-stu-id="67e33-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="67e33-187">感知模拟控制</span><span class="sxs-lookup"><span data-stu-id="67e33-187">Perception Simulation Control</span></span>

<span data-ttu-id="67e33-188">**/api/holographic/simulation/control/mode （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="67e33-189">获取模拟模式</span><span class="sxs-lookup"><span data-stu-id="67e33-189">Get the simulation mode</span></span>

<span data-ttu-id="67e33-190">**/api/holographic/simulation/control/mode （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="67e33-191">设置模拟模式</span><span class="sxs-lookup"><span data-stu-id="67e33-191">Set the simulation mode</span></span>

<span data-ttu-id="67e33-192">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-192">Parameters</span></span>
* <span data-ttu-id="67e33-193">模式：模拟模式：默认、模拟、远程、旧</span><span class="sxs-lookup"><span data-stu-id="67e33-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="67e33-194">**/api/holographic/simulation/control/stream （删除）**</span><span class="sxs-lookup"><span data-stu-id="67e33-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="67e33-195">删除控件流。</span><span class="sxs-lookup"><span data-stu-id="67e33-195">Delete a control stream.</span></span>

<span data-ttu-id="67e33-196">**/api/holographic/simulation/control/stream （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="67e33-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="67e33-197">为控制流打开 web 套接字连接。</span><span class="sxs-lookup"><span data-stu-id="67e33-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="67e33-198">**/api/holographic/simulation/control/stream （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="67e33-199">创建控制流（需要优先级），或将数据发送到创建的流（需要 streamId）。</span><span class="sxs-lookup"><span data-stu-id="67e33-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="67e33-200">已发布的数据的类型应为 "application/八进制流"。</span><span class="sxs-lookup"><span data-stu-id="67e33-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="67e33-201">感知播放</span><span class="sxs-lookup"><span data-stu-id="67e33-201">Perception Simulation Playback</span></span>

<span data-ttu-id="67e33-202">**/api/holographic/simulation/playback/file （删除）**</span><span class="sxs-lookup"><span data-stu-id="67e33-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="67e33-203">删除记录。</span><span class="sxs-lookup"><span data-stu-id="67e33-203">Delete a recording.</span></span>

<span data-ttu-id="67e33-204">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-204">Parameters</span></span>
* <span data-ttu-id="67e33-205">录制：要删除的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="67e33-206">**/api/holographic/simulation/playback/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="67e33-207">上传记录。</span><span class="sxs-lookup"><span data-stu-id="67e33-207">Upload a recording.</span></span>

<span data-ttu-id="67e33-208">**/api/holographic/simulation/playback/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="67e33-209">获取所有记录。</span><span class="sxs-lookup"><span data-stu-id="67e33-209">Get all recordings.</span></span>

<span data-ttu-id="67e33-210">**/api/holographic/simulation/playback/session （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="67e33-211">获取记录的当前播放状态。</span><span class="sxs-lookup"><span data-stu-id="67e33-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="67e33-212">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-212">Parameters</span></span>
* <span data-ttu-id="67e33-213">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-213">recording : Name of recording.</span></span>

<span data-ttu-id="67e33-214">**/api/holographic/simulation/playback/session/file （删除）**</span><span class="sxs-lookup"><span data-stu-id="67e33-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="67e33-215">卸载记录。</span><span class="sxs-lookup"><span data-stu-id="67e33-215">Unload a recording.</span></span>

<span data-ttu-id="67e33-216">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-216">Parameters</span></span>
* <span data-ttu-id="67e33-217">录制：要卸载的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="67e33-218">**/api/holographic/simulation/playback/session/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="67e33-219">加载记录。</span><span class="sxs-lookup"><span data-stu-id="67e33-219">Load a recording.</span></span>

<span data-ttu-id="67e33-220">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-220">Parameters</span></span>
* <span data-ttu-id="67e33-221">录制：要加载的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="67e33-222">**/api/holographic/simulation/playback/session/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="67e33-223">获取所有加载的记录。</span><span class="sxs-lookup"><span data-stu-id="67e33-223">Get all loaded recordings.</span></span>

<span data-ttu-id="67e33-224">**/api/holographic/simulation/playback/session/pause （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="67e33-225">暂停录制。</span><span class="sxs-lookup"><span data-stu-id="67e33-225">Pause a recording.</span></span>

<span data-ttu-id="67e33-226">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-226">Parameters</span></span>
* <span data-ttu-id="67e33-227">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-227">recording : Name of recording.</span></span>

<span data-ttu-id="67e33-228">**/api/holographic/simulation/playback/session/play （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="67e33-229">播放录制。</span><span class="sxs-lookup"><span data-stu-id="67e33-229">Play a recording.</span></span>

<span data-ttu-id="67e33-230">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-230">Parameters</span></span>
* <span data-ttu-id="67e33-231">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-231">recording : Name of recording.</span></span>

<span data-ttu-id="67e33-232">**/api/holographic/simulation/playback/session/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="67e33-233">停止录制。</span><span class="sxs-lookup"><span data-stu-id="67e33-233">Stop a recording.</span></span>

<span data-ttu-id="67e33-234">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-234">Parameters</span></span>
* <span data-ttu-id="67e33-235">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-235">recording : Name of recording.</span></span>

<span data-ttu-id="67e33-236">**/api/holographic/simulation/playback/session/types （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="67e33-237">获取已加载记录中数据的类型。</span><span class="sxs-lookup"><span data-stu-id="67e33-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="67e33-238">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-238">Parameters</span></span>
* <span data-ttu-id="67e33-239">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="67e33-240">感知模拟记录</span><span class="sxs-lookup"><span data-stu-id="67e33-240">Perception Simulation Recording</span></span>

<span data-ttu-id="67e33-241">**/api/holographic/simulation/recording/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="67e33-242">开始记录。</span><span class="sxs-lookup"><span data-stu-id="67e33-242">Start a recording.</span></span> <span data-ttu-id="67e33-243">一次只能有一个记录处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="67e33-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="67e33-244">必须设置 head、双手、spatialMapping 或环境之一。</span><span class="sxs-lookup"><span data-stu-id="67e33-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="67e33-245">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-245">Parameters</span></span>
* <span data-ttu-id="67e33-246">head：设置为1以记录头数据。</span><span class="sxs-lookup"><span data-stu-id="67e33-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="67e33-247">动手：设置为1以记录手型数据。</span><span class="sxs-lookup"><span data-stu-id="67e33-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="67e33-248">spatialMapping：设置为1以记录空间映射。</span><span class="sxs-lookup"><span data-stu-id="67e33-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="67e33-249">环境：设置为1以记录环境数据。</span><span class="sxs-lookup"><span data-stu-id="67e33-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="67e33-250">name：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-250">name : Name of the recording.</span></span>
* <span data-ttu-id="67e33-251">singleSpatialMappingFrame：设置为1将仅记录单个空间映射框架。</span><span class="sxs-lookup"><span data-stu-id="67e33-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="67e33-252">**/api/holographic/simulation/recording/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="67e33-253">获取记录状态。</span><span class="sxs-lookup"><span data-stu-id="67e33-253">Get recording state.</span></span>

<span data-ttu-id="67e33-254">**/api/holographic/simulation/recording/stop （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="67e33-255">停止当前记录。</span><span class="sxs-lookup"><span data-stu-id="67e33-255">Stop the current recording.</span></span> <span data-ttu-id="67e33-256">记录将以文件的形式返回。</span><span class="sxs-lookup"><span data-stu-id="67e33-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="67e33-257">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="67e33-257">Mixed Reality Capture</span></span>

<span data-ttu-id="67e33-258">**/api/holographic/mrc/file （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="67e33-259">从设备下载混合现实文件。</span><span class="sxs-lookup"><span data-stu-id="67e33-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="67e33-260">使用 op = stream query 参数进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="67e33-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="67e33-261">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-261">Parameters</span></span>
* <span data-ttu-id="67e33-262">filename：要获取的视频文件的名称、hex64 编码</span><span class="sxs-lookup"><span data-stu-id="67e33-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="67e33-263">op： stream</span><span class="sxs-lookup"><span data-stu-id="67e33-263">op : stream</span></span>

<span data-ttu-id="67e33-264">**/api/holographic/mrc/file （删除）**</span><span class="sxs-lookup"><span data-stu-id="67e33-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="67e33-265">从设备中删除混合现实记录。</span><span class="sxs-lookup"><span data-stu-id="67e33-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="67e33-266">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-266">Parameters</span></span>
* <span data-ttu-id="67e33-267">filename：要删除的文件的名称，hex64 已编码</span><span class="sxs-lookup"><span data-stu-id="67e33-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="67e33-268">**/api/holographic/mrc/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="67e33-269">返回存储在设备上的混合现实文件的列表</span><span class="sxs-lookup"><span data-stu-id="67e33-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="67e33-270">**/api/holographic/mrc/photo （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="67e33-271">采用混合现实照片，并在设备上创建文件</span><span class="sxs-lookup"><span data-stu-id="67e33-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="67e33-272">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-272">Parameters</span></span>
* <span data-ttu-id="67e33-273">holo：捕获全息影像： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="67e33-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="67e33-274">pv：捕获 PV 摄像机： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="67e33-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="67e33-275">RenderFromCamera：（仅限 HoloLens 2）从照片/视频相机的角度呈现： true 或 false （默认为 true）</span><span class="sxs-lookup"><span data-stu-id="67e33-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="67e33-276">**/api/holographic/mrc/settings （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="67e33-277">获取默认的混合现实捕获设置</span><span class="sxs-lookup"><span data-stu-id="67e33-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="67e33-278">**/api/holographic/mrc/settings （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="67e33-279">设置默认的混合现实捕获设置。</span><span class="sxs-lookup"><span data-stu-id="67e33-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="67e33-280">其中一些设置适用于系统的 MRC 照片和视频捕获。</span><span class="sxs-lookup"><span data-stu-id="67e33-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="67e33-281">**/api/holographic/mrc/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="67e33-282">获取记录的混合现实的状态（正在运行、已停止）</span><span class="sxs-lookup"><span data-stu-id="67e33-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="67e33-283">**/api/holographic/mrc/thumbnail （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="67e33-284">获取指定文件的缩略图图像。</span><span class="sxs-lookup"><span data-stu-id="67e33-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="67e33-285">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-285">Parameters</span></span>
* <span data-ttu-id="67e33-286">文件名：要为其请求缩略图的文件的名称，hex64 已编码</span><span class="sxs-lookup"><span data-stu-id="67e33-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="67e33-287">**/api/holographic/mrc/video/control/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="67e33-288">启动混合现实记录</span><span class="sxs-lookup"><span data-stu-id="67e33-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="67e33-289">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-289">Parameters</span></span>
* <span data-ttu-id="67e33-290">holo：捕获全息影像： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="67e33-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="67e33-291">pv：捕获 PV 摄像机： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="67e33-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="67e33-292">mic：捕获麦克风： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="67e33-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="67e33-293">环回：捕获应用音频： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="67e33-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="67e33-294">RenderFromCamera：（仅限 HoloLens 2）从照片/视频相机的角度呈现： true 或 false （默认为 true）</span><span class="sxs-lookup"><span data-stu-id="67e33-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="67e33-295">vstab：（仅限 HoloLens 2）启用视频抖动： true 或 false （默认为 true）</span><span class="sxs-lookup"><span data-stu-id="67e33-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="67e33-296">vstabbuffer：（仅限 HoloLens 2）视频抖动缓冲区延迟：0到30帧（默认为15帧）</span><span class="sxs-lookup"><span data-stu-id="67e33-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="67e33-297">**/api/holographic/mrc/video/control/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="67e33-298">停止当前混合现实记录</span><span class="sxs-lookup"><span data-stu-id="67e33-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="67e33-299">混合现实流式处理</span><span class="sxs-lookup"><span data-stu-id="67e33-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="67e33-300">HoloLens 支持混合现实的实时预览，通过块区下载零碎的工作方式。</span><span class="sxs-lookup"><span data-stu-id="67e33-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="67e33-301">混合现实流共享相同的参数集来控制捕获的内容：</span><span class="sxs-lookup"><span data-stu-id="67e33-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="67e33-302">holo：捕获全息影像： true 或 false</span><span class="sxs-lookup"><span data-stu-id="67e33-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="67e33-303">pv：捕获 PV 摄像机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="67e33-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="67e33-304">mic：捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="67e33-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="67e33-305">环回：捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="67e33-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="67e33-306">如果未指定任何内容：将捕获全息影像、照片/视频相机和应用音频</span><span class="sxs-lookup"><span data-stu-id="67e33-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="67e33-307">如果已指定任何参数：未指定的参数将默认为 false</span><span class="sxs-lookup"><span data-stu-id="67e33-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="67e33-308">可选参数（仅限 HoloLens 2）</span><span class="sxs-lookup"><span data-stu-id="67e33-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="67e33-309">RenderFromCamera：从照片/视频相机的角度呈现： true 或 false （默认为 true）</span><span class="sxs-lookup"><span data-stu-id="67e33-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="67e33-310">vstab：启用视频抖动： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="67e33-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="67e33-311">vstabbuffer：视频稳定缓冲区延迟：0到30帧（默认为15帧）</span><span class="sxs-lookup"><span data-stu-id="67e33-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="67e33-312">**/api/holographic/stream/live.mp4 （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="67e33-313">1280x720p 30fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="67e33-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="67e33-314">**/api/holographic/stream/live_high （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="67e33-315">1280x720p 30fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="67e33-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="67e33-316">**/api/holographic/stream/live_med （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="67e33-317">854x480p 30fps 2.5 Mbit stream。</span><span class="sxs-lookup"><span data-stu-id="67e33-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="67e33-318">**/api/holographic/stream/live_low （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="67e33-319">428x240p 15fps 0.6 Mbit stream。</span><span class="sxs-lookup"><span data-stu-id="67e33-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="67e33-320">联网</span><span class="sxs-lookup"><span data-stu-id="67e33-320">Networking</span></span>

<span data-ttu-id="67e33-321">**/api/networking/ipconfig （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="67e33-322">获取当前 ip 配置</span><span class="sxs-lookup"><span data-stu-id="67e33-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="67e33-323">操作系统信息</span><span class="sxs-lookup"><span data-stu-id="67e33-323">OS Information</span></span>

<span data-ttu-id="67e33-324">**/api/os/info （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="67e33-325">获取操作系统信息</span><span class="sxs-lookup"><span data-stu-id="67e33-325">Gets operating system information</span></span>

<span data-ttu-id="67e33-326">**/api/os/machinename （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="67e33-327">获取计算机名称</span><span class="sxs-lookup"><span data-stu-id="67e33-327">Gets the machine name</span></span>

<span data-ttu-id="67e33-328">**/api/os/machinename （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="67e33-329">设置计算机名称</span><span class="sxs-lookup"><span data-stu-id="67e33-329">Sets the machine name</span></span>

<span data-ttu-id="67e33-330">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-330">Parameters</span></span>
* <span data-ttu-id="67e33-331">名称：要设置为的新计算机名称，hex64 编码为</span><span class="sxs-lookup"><span data-stu-id="67e33-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="67e33-332">性能数据</span><span class="sxs-lookup"><span data-stu-id="67e33-332">Performance data</span></span>

<span data-ttu-id="67e33-333">**/api/resourcemanager/processes （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="67e33-334">返回正在运行的进程的列表以及详细信息</span><span class="sxs-lookup"><span data-stu-id="67e33-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="67e33-335">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-335">Return data</span></span>
* <span data-ttu-id="67e33-336">JSON，包含进程列表和每个进程的详细信息</span><span class="sxs-lookup"><span data-stu-id="67e33-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="67e33-337">**/api/resourcemanager/systemperf （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="67e33-338">返回系统性能统计信息（i/o 读/写、内存统计信息等。</span><span class="sxs-lookup"><span data-stu-id="67e33-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="67e33-339">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-339">Return data</span></span>
* <span data-ttu-id="67e33-340">包含系统信息的 JSON： CPU、GPU、内存、网络、IO</span><span class="sxs-lookup"><span data-stu-id="67e33-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="67e33-341">电源</span><span class="sxs-lookup"><span data-stu-id="67e33-341">Power</span></span>

<span data-ttu-id="67e33-342">**/api/power/battery （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="67e33-343">获取当前电池状态</span><span class="sxs-lookup"><span data-stu-id="67e33-343">Gets the current battery state</span></span>

<span data-ttu-id="67e33-344">**/api/power/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="67e33-345">检查系统是否处于低功耗状态</span><span class="sxs-lookup"><span data-stu-id="67e33-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="67e33-346">远程控制</span><span class="sxs-lookup"><span data-stu-id="67e33-346">Remote Control</span></span>

<span data-ttu-id="67e33-347">**/api/control/restart （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="67e33-348">重新启动目标设备</span><span class="sxs-lookup"><span data-stu-id="67e33-348">Restarts the target device</span></span>

<span data-ttu-id="67e33-349">**/api/control/shutdown （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="67e33-350">关闭目标设备</span><span class="sxs-lookup"><span data-stu-id="67e33-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="67e33-351">任务管理器</span><span class="sxs-lookup"><span data-stu-id="67e33-351">Task Manager</span></span>

<span data-ttu-id="67e33-352">**/api/taskmanager/app （删除）**</span><span class="sxs-lookup"><span data-stu-id="67e33-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="67e33-353">停止现代应用</span><span class="sxs-lookup"><span data-stu-id="67e33-353">Stops a modern app</span></span>

<span data-ttu-id="67e33-354">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-354">Parameters</span></span>
* <span data-ttu-id="67e33-355">包：应用包的完整名称，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="67e33-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="67e33-356">forcestop：强制停止所有进程（= 是）</span><span class="sxs-lookup"><span data-stu-id="67e33-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="67e33-357">**/api/taskmanager/app （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="67e33-358">启动新式应用</span><span class="sxs-lookup"><span data-stu-id="67e33-358">Starts a modern app</span></span>

<span data-ttu-id="67e33-359">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-359">Parameters</span></span>
* <span data-ttu-id="67e33-360">appid：要启动的应用的 PRAID，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="67e33-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="67e33-361">包：应用包的完整名称，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="67e33-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="67e33-362">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="67e33-362">WiFi Management</span></span>

<span data-ttu-id="67e33-363">**/api/wifi/interfaces （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="67e33-364">枚举无线网络接口</span><span class="sxs-lookup"><span data-stu-id="67e33-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="67e33-365">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-365">Return data</span></span>
* <span data-ttu-id="67e33-366">包含详细信息的无线接口列表（GUID、说明等）</span><span class="sxs-lookup"><span data-stu-id="67e33-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="67e33-367">**/api/wifi/network （删除）**</span><span class="sxs-lookup"><span data-stu-id="67e33-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="67e33-368">删除与指定接口上的网络相关联的配置文件</span><span class="sxs-lookup"><span data-stu-id="67e33-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="67e33-369">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-369">Parameters</span></span>
* <span data-ttu-id="67e33-370">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="67e33-370">interface : network interface guid</span></span>
* <span data-ttu-id="67e33-371">配置文件：配置文件名称</span><span class="sxs-lookup"><span data-stu-id="67e33-371">profile : profile name</span></span>

<span data-ttu-id="67e33-372">**/api/wifi/networks （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="67e33-373">枚举指定网络接口上的无线网络</span><span class="sxs-lookup"><span data-stu-id="67e33-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="67e33-374">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-374">Parameters</span></span>
* <span data-ttu-id="67e33-375">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="67e33-375">interface : network interface guid</span></span>

<span data-ttu-id="67e33-376">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-376">Return data</span></span>
* <span data-ttu-id="67e33-377">网络接口上发现的无线网络的列表，详细信息</span><span class="sxs-lookup"><span data-stu-id="67e33-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="67e33-378">**/api/wifi/network （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="67e33-379">连接或断开指定接口上的网络连接</span><span class="sxs-lookup"><span data-stu-id="67e33-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="67e33-380">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-380">Parameters</span></span>
* <span data-ttu-id="67e33-381">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="67e33-381">interface : network interface guid</span></span>
* <span data-ttu-id="67e33-382">ssid： ssid，hex64 编码，用于连接到</span><span class="sxs-lookup"><span data-stu-id="67e33-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="67e33-383">op：连接或断开连接</span><span class="sxs-lookup"><span data-stu-id="67e33-383">op : connect or disconnect</span></span>
* <span data-ttu-id="67e33-384">createprofile： yes 或 no</span><span class="sxs-lookup"><span data-stu-id="67e33-384">createprofile : yes or no</span></span>
* <span data-ttu-id="67e33-385">key：共享密钥，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="67e33-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="67e33-386">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="67e33-386">Windows Performance Recorder</span></span>

<span data-ttu-id="67e33-387">**/api/wpr/customtrace （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="67e33-388">上传 "配置文件，并使用上传的配置文件开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="67e33-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="67e33-389">负载</span><span class="sxs-lookup"><span data-stu-id="67e33-389">Payload</span></span>
* <span data-ttu-id="67e33-390">多部分相容的 http 正文</span><span class="sxs-lookup"><span data-stu-id="67e33-390">multi-part conforming http body</span></span>

<span data-ttu-id="67e33-391">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-391">Return data</span></span>
* <span data-ttu-id="67e33-392">返回 "会话状态。</span><span class="sxs-lookup"><span data-stu-id="67e33-392">Returns the WPR session status.</span></span>

<span data-ttu-id="67e33-393">**/api/wpr/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="67e33-394">检索 "会话的状态</span><span class="sxs-lookup"><span data-stu-id="67e33-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="67e33-395">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-395">Return data</span></span>
* <span data-ttu-id="67e33-396">"会话状态。</span><span class="sxs-lookup"><span data-stu-id="67e33-396">WPR session status.</span></span>

<span data-ttu-id="67e33-397">**/api/wpr/trace （GET）**</span><span class="sxs-lookup"><span data-stu-id="67e33-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="67e33-398">停止 "（性能）跟踪会话</span><span class="sxs-lookup"><span data-stu-id="67e33-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="67e33-399">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-399">Return data</span></span>
* <span data-ttu-id="67e33-400">返回跟踪 ETL 文件</span><span class="sxs-lookup"><span data-stu-id="67e33-400">Returns the trace ETL file</span></span>

<span data-ttu-id="67e33-401">**/api/wpr/trace （POST）**</span><span class="sxs-lookup"><span data-stu-id="67e33-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="67e33-402">启动 "（性能）跟踪会话</span><span class="sxs-lookup"><span data-stu-id="67e33-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="67e33-403">参数</span><span class="sxs-lookup"><span data-stu-id="67e33-403">Parameters</span></span>
* <span data-ttu-id="67e33-404">配置文件：配置文件名称。</span><span class="sxs-lookup"><span data-stu-id="67e33-404">profile : Profile name.</span></span> <span data-ttu-id="67e33-405">可用的配置文件存储在 perfprofiles/配置文件中。 json</span><span class="sxs-lookup"><span data-stu-id="67e33-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="67e33-406">返回数据</span><span class="sxs-lookup"><span data-stu-id="67e33-406">Return data</span></span>
* <span data-ttu-id="67e33-407">在 "开始" 中，返回 "会话状态。</span><span class="sxs-lookup"><span data-stu-id="67e33-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="67e33-408">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67e33-408">See also</span></span>
* [<span data-ttu-id="67e33-409">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="67e33-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="67e33-410">设备门户核心 API 参考（UWP）</span><span class="sxs-lookup"><span data-stu-id="67e33-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
