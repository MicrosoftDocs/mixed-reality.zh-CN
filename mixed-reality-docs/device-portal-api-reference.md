---
title: 设备门户 API 参考
description: HoloLens 上 Windows 设备门户的 API 参考
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、Windows 设备门户、API
ms.openlocfilehash: 17268c9a20d3da0ee90e5d6cead4342d3badf800
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451322"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="6d03a-104">设备门户 API 参考</span><span class="sxs-lookup"><span data-stu-id="6d03a-104">Device portal API reference</span></span>

<span data-ttu-id="6d03a-105">[Windows 设备门户](using-the-windows-device-portal.md)中的所有内容都是在 REST API 的基础之上构建的，你可以使用它以编程方式访问数据和控制设备。</span><span class="sxs-lookup"><span data-stu-id="6d03a-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="6d03a-106">应用常见问题</span><span class="sxs-lookup"><span data-stu-id="6d03a-106">App deloyment</span></span>

<span data-ttu-id="6d03a-107">**/api/app/packagemanager/package （删除）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="6d03a-108">卸载应用</span><span class="sxs-lookup"><span data-stu-id="6d03a-108">Uninstalls an app</span></span>

<span data-ttu-id="6d03a-109">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-109">Parameters</span></span>
* <span data-ttu-id="6d03a-110">package：要卸载的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="6d03a-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="6d03a-111">**/api/app/packagemanager/package （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="6d03a-112">安装应用程序</span><span class="sxs-lookup"><span data-stu-id="6d03a-112">Installs an App</span></span>

<span data-ttu-id="6d03a-113">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-113">Parameters</span></span>
* <span data-ttu-id="6d03a-114">package：要安装的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="6d03a-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="6d03a-115">Payload</span><span class="sxs-lookup"><span data-stu-id="6d03a-115">Payload</span></span>
* <span data-ttu-id="6d03a-116">多部分相容的 http 正文</span><span class="sxs-lookup"><span data-stu-id="6d03a-116">multi-part conforming http body</span></span>

<span data-ttu-id="6d03a-117">**/api/app/packagemanager/packages （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="6d03a-118">检索系统上已安装应用的列表，详细信息</span><span class="sxs-lookup"><span data-stu-id="6d03a-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="6d03a-119">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-119">Return data</span></span>
* <span data-ttu-id="6d03a-120">包含详细信息的已安装包列表</span><span class="sxs-lookup"><span data-stu-id="6d03a-120">List of installed packages with details</span></span>

<span data-ttu-id="6d03a-121">**/api/app/packagemanager/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="6d03a-122">获取正在进行的应用安装的状态</span><span class="sxs-lookup"><span data-stu-id="6d03a-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="6d03a-123">转储集合</span><span class="sxs-lookup"><span data-stu-id="6d03a-123">Dump collection</span></span>

<span data-ttu-id="6d03a-124">**/api/debug/dump/usermode/crashcontrol （删除）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="6d03a-125">为旁加载应用禁用故障转储收集</span><span class="sxs-lookup"><span data-stu-id="6d03a-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="6d03a-126">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-126">Parameters</span></span>
* <span data-ttu-id="6d03a-127">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="6d03a-127">packageFullname : package name</span></span>

<span data-ttu-id="6d03a-128">**/api/debug/dump/usermode/crashcontrol （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="6d03a-129">获取旁加载应用故障转储收集的设置</span><span class="sxs-lookup"><span data-stu-id="6d03a-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="6d03a-130">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-130">Parameters</span></span>
* <span data-ttu-id="6d03a-131">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="6d03a-131">packageFullname : package name</span></span>

<span data-ttu-id="6d03a-132">**/api/debug/dump/usermode/crashcontrol （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="6d03a-133">启用和设置旁加载应用的转储控件设置</span><span class="sxs-lookup"><span data-stu-id="6d03a-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="6d03a-134">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-134">Parameters</span></span>
* <span data-ttu-id="6d03a-135">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="6d03a-135">packageFullname : package name</span></span>

<span data-ttu-id="6d03a-136">**/api/debug/dump/usermode/crashdump （删除）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="6d03a-137">删除旁加载应用程序的故障转储</span><span class="sxs-lookup"><span data-stu-id="6d03a-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="6d03a-138">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-138">Parameters</span></span>
* <span data-ttu-id="6d03a-139">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="6d03a-139">packageFullname : package name</span></span>
* <span data-ttu-id="6d03a-140">文件名：转储文件名</span><span class="sxs-lookup"><span data-stu-id="6d03a-140">fileName : dump file name</span></span>

<span data-ttu-id="6d03a-141">**/api/debug/dump/usermode/crashdump （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="6d03a-142">检索旁加载应用的故障转储</span><span class="sxs-lookup"><span data-stu-id="6d03a-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="6d03a-143">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-143">Parameters</span></span>
* <span data-ttu-id="6d03a-144">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="6d03a-144">packageFullname : package name</span></span>
* <span data-ttu-id="6d03a-145">文件名：转储文件名</span><span class="sxs-lookup"><span data-stu-id="6d03a-145">fileName : dump file name</span></span>

<span data-ttu-id="6d03a-146">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-146">Return data</span></span>
* <span data-ttu-id="6d03a-147">转储文件。</span><span class="sxs-lookup"><span data-stu-id="6d03a-147">Dump file.</span></span> <span data-ttu-id="6d03a-148">与 WinDbg 或 Visual Studio 一起检查</span><span class="sxs-lookup"><span data-stu-id="6d03a-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="6d03a-149">**/api/debug/dump/usermode/dumps （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="6d03a-150">返回旁加载应用的所有崩溃转储的列表</span><span class="sxs-lookup"><span data-stu-id="6d03a-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="6d03a-151">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-151">Return data</span></span>
* <span data-ttu-id="6d03a-152">每端加载的应用的故障转储列表</span><span class="sxs-lookup"><span data-stu-id="6d03a-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="6d03a-153">ETW</span><span class="sxs-lookup"><span data-stu-id="6d03a-153">ETW</span></span>

<span data-ttu-id="6d03a-154">**/api/etw/providers （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="6d03a-155">枚举注册的提供程序</span><span class="sxs-lookup"><span data-stu-id="6d03a-155">Enumerates registered providers</span></span>

<span data-ttu-id="6d03a-156">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-156">Return data</span></span>
* <span data-ttu-id="6d03a-157">提供程序列表、友好名称和 GUID</span><span class="sxs-lookup"><span data-stu-id="6d03a-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="6d03a-158">**/api/etw/session/realtime （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="6d03a-159">创建实时 ETW 会话;通过 websocket 进行管理。</span><span class="sxs-lookup"><span data-stu-id="6d03a-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="6d03a-160">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-160">Return data</span></span>
* <span data-ttu-id="6d03a-161">已启用的提供程序中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="6d03a-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="6d03a-162">全息操作系统</span><span class="sxs-lookup"><span data-stu-id="6d03a-162">Holographic OS</span></span>

<span data-ttu-id="6d03a-163">**/api/holographic/os/etw/customproviders （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="6d03a-164">返回未向系统注册的 HoloLens 特定 ETW 提供程序的列表</span><span class="sxs-lookup"><span data-stu-id="6d03a-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="6d03a-165">**/api/holographic/os/services （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="6d03a-166">返回所有正在运行的服务的状态。</span><span class="sxs-lookup"><span data-stu-id="6d03a-166">Returns the states of all services running.</span></span>

<span data-ttu-id="6d03a-167">**/api/holographic/os/settings/ipd （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="6d03a-168">获取存储的 IPD （Interpupillary 距离）（以毫米为单位）</span><span class="sxs-lookup"><span data-stu-id="6d03a-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="6d03a-169">**/api/holographic/os/settings/ipd （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="6d03a-170">设置 IPD</span><span class="sxs-lookup"><span data-stu-id="6d03a-170">Sets the IPD</span></span>

<span data-ttu-id="6d03a-171">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-171">Parameters</span></span>
* <span data-ttu-id="6d03a-172">ipd：要设置的新 IPD 值（以毫米为单位）</span><span class="sxs-lookup"><span data-stu-id="6d03a-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="6d03a-173">**/api/holographic/os/webmanagement/settings/https （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="6d03a-174">获取设备门户的 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="6d03a-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="6d03a-175">**/api/holographic/os/webmanagement/settings/https （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="6d03a-176">为设备门户设置 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="6d03a-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="6d03a-177">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-177">Parameters</span></span>
* <span data-ttu-id="6d03a-178">必需：是、否或默认值</span><span class="sxs-lookup"><span data-stu-id="6d03a-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="6d03a-179">全息认知</span><span class="sxs-lookup"><span data-stu-id="6d03a-179">Holographic Perception</span></span>

<span data-ttu-id="6d03a-180">**/api/holographic/perception/client （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="6d03a-181">接受 websocket 升级，并运行以 30 fps 发送更新的感知客户端。</span><span class="sxs-lookup"><span data-stu-id="6d03a-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="6d03a-182">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-182">Parameters</span></span>
* <span data-ttu-id="6d03a-183">clientmode： "active" 强制在无法被动建立时强制视觉跟踪模式</span><span class="sxs-lookup"><span data-stu-id="6d03a-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="6d03a-184">全息热量</span><span class="sxs-lookup"><span data-stu-id="6d03a-184">Holographic Thermal</span></span>

<span data-ttu-id="6d03a-185">**/api/holographic/thermal/stage （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="6d03a-186">获取设备的热阶段（0正常，1温，2严重）</span><span class="sxs-lookup"><span data-stu-id="6d03a-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="6d03a-187">感知模拟控制</span><span class="sxs-lookup"><span data-stu-id="6d03a-187">Perception Simulation Control</span></span>

<span data-ttu-id="6d03a-188">**/api/holographic/simulation/control/mode （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="6d03a-189">获取模拟模式</span><span class="sxs-lookup"><span data-stu-id="6d03a-189">Get the simulation mode</span></span>

<span data-ttu-id="6d03a-190">**/api/holographic/simulation/control/mode （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="6d03a-191">设置模拟模式</span><span class="sxs-lookup"><span data-stu-id="6d03a-191">Set the simulation mode</span></span>

<span data-ttu-id="6d03a-192">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-192">Parameters</span></span>
* <span data-ttu-id="6d03a-193">模式：模拟模式：默认、模拟、远程、旧</span><span class="sxs-lookup"><span data-stu-id="6d03a-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="6d03a-194">**/api/holographic/simulation/control/stream （删除）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="6d03a-195">删除控件流。</span><span class="sxs-lookup"><span data-stu-id="6d03a-195">Delete a control stream.</span></span>

<span data-ttu-id="6d03a-196">**/api/holographic/simulation/control/stream （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="6d03a-197">为控制流打开 web 套接字连接。</span><span class="sxs-lookup"><span data-stu-id="6d03a-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="6d03a-198">**/api/holographic/simulation/control/stream （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="6d03a-199">创建控制流（需要优先级），或将数据发送到创建的流（需要 streamId）。</span><span class="sxs-lookup"><span data-stu-id="6d03a-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="6d03a-200">已发布的数据的类型应为 "application/八进制流"。</span><span class="sxs-lookup"><span data-stu-id="6d03a-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="6d03a-201">**/api/holographic/simulation/display/stream （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="6d03a-202">请求模拟视频流，其中包含在处于 "模拟" 模式时呈现给系统的内容。</span><span class="sxs-lookup"><span data-stu-id="6d03a-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="6d03a-203">首先发送一个简单的格式说明符标头，然后再发送一个-264 编码的纹理，每个纹理前面都有一个标头，指示眼睛索引和纹理大小。</span><span class="sxs-lookup"><span data-stu-id="6d03a-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="6d03a-204">感知播放</span><span class="sxs-lookup"><span data-stu-id="6d03a-204">Perception Simulation Playback</span></span>

<span data-ttu-id="6d03a-205">**/api/holographic/simulation/playback/file （删除）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="6d03a-206">删除记录。</span><span class="sxs-lookup"><span data-stu-id="6d03a-206">Delete a recording.</span></span>

<span data-ttu-id="6d03a-207">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-207">Parameters</span></span>
* <span data-ttu-id="6d03a-208">录制：要删除的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="6d03a-209">**/api/holographic/simulation/playback/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="6d03a-210">上传记录。</span><span class="sxs-lookup"><span data-stu-id="6d03a-210">Upload a recording.</span></span>

<span data-ttu-id="6d03a-211">**/api/holographic/simulation/playback/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="6d03a-212">获取所有记录。</span><span class="sxs-lookup"><span data-stu-id="6d03a-212">Get all recordings.</span></span>

<span data-ttu-id="6d03a-213">**/api/holographic/simulation/playback/session （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="6d03a-214">获取记录的当前播放状态。</span><span class="sxs-lookup"><span data-stu-id="6d03a-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="6d03a-215">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-215">Parameters</span></span>
* <span data-ttu-id="6d03a-216">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-216">recording : Name of recording.</span></span>

<span data-ttu-id="6d03a-217">**/api/holographic/simulation/playback/session/file （删除）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="6d03a-218">卸载记录。</span><span class="sxs-lookup"><span data-stu-id="6d03a-218">Unload a recording.</span></span>

<span data-ttu-id="6d03a-219">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-219">Parameters</span></span>
* <span data-ttu-id="6d03a-220">录制：要卸载的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="6d03a-221">**/api/holographic/simulation/playback/session/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="6d03a-222">加载记录。</span><span class="sxs-lookup"><span data-stu-id="6d03a-222">Load a recording.</span></span>

<span data-ttu-id="6d03a-223">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-223">Parameters</span></span>
* <span data-ttu-id="6d03a-224">录制：要加载的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="6d03a-225">**/api/holographic/simulation/playback/session/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="6d03a-226">获取所有加载的记录。</span><span class="sxs-lookup"><span data-stu-id="6d03a-226">Get all loaded recordings.</span></span>

<span data-ttu-id="6d03a-227">**/api/holographic/simulation/playback/session/pause （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="6d03a-228">暂停录制。</span><span class="sxs-lookup"><span data-stu-id="6d03a-228">Pause a recording.</span></span>

<span data-ttu-id="6d03a-229">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-229">Parameters</span></span>
* <span data-ttu-id="6d03a-230">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-230">recording : Name of recording.</span></span>

<span data-ttu-id="6d03a-231">**/api/holographic/simulation/playback/session/play （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="6d03a-232">播放录制。</span><span class="sxs-lookup"><span data-stu-id="6d03a-232">Play a recording.</span></span>

<span data-ttu-id="6d03a-233">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-233">Parameters</span></span>
* <span data-ttu-id="6d03a-234">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-234">recording : Name of recording.</span></span>

<span data-ttu-id="6d03a-235">**/api/holographic/simulation/playback/session/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="6d03a-236">停止录制。</span><span class="sxs-lookup"><span data-stu-id="6d03a-236">Stop a recording.</span></span>

<span data-ttu-id="6d03a-237">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-237">Parameters</span></span>
* <span data-ttu-id="6d03a-238">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-238">recording : Name of recording.</span></span>

<span data-ttu-id="6d03a-239">**/api/holographic/simulation/playback/session/types （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="6d03a-240">获取已加载记录中数据的类型。</span><span class="sxs-lookup"><span data-stu-id="6d03a-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="6d03a-241">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-241">Parameters</span></span>
* <span data-ttu-id="6d03a-242">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="6d03a-243">感知模拟记录</span><span class="sxs-lookup"><span data-stu-id="6d03a-243">Perception Simulation Recording</span></span>

<span data-ttu-id="6d03a-244">**/api/holographic/simulation/recording/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="6d03a-245">开始记录。</span><span class="sxs-lookup"><span data-stu-id="6d03a-245">Start a recording.</span></span> <span data-ttu-id="6d03a-246">一次只能有一个记录处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="6d03a-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="6d03a-247">必须设置 head、双手、spatialMapping 或环境之一。</span><span class="sxs-lookup"><span data-stu-id="6d03a-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="6d03a-248">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-248">Parameters</span></span>
* <span data-ttu-id="6d03a-249">head：设置为1以记录头数据。</span><span class="sxs-lookup"><span data-stu-id="6d03a-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="6d03a-250">动手：设置为1以记录手型数据。</span><span class="sxs-lookup"><span data-stu-id="6d03a-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="6d03a-251">spatialMapping：设置为1以记录空间映射。</span><span class="sxs-lookup"><span data-stu-id="6d03a-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="6d03a-252">环境：设置为1以记录环境数据。</span><span class="sxs-lookup"><span data-stu-id="6d03a-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="6d03a-253">name：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-253">name : Name of the recording.</span></span>
* <span data-ttu-id="6d03a-254">singleSpatialMappingFrame：设置为1将仅记录单个空间映射框架。</span><span class="sxs-lookup"><span data-stu-id="6d03a-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="6d03a-255">**/api/holographic/simulation/recording/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="6d03a-256">获取记录状态。</span><span class="sxs-lookup"><span data-stu-id="6d03a-256">Get recording state.</span></span>

<span data-ttu-id="6d03a-257">**/api/holographic/simulation/recording/stop （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="6d03a-258">停止当前记录。</span><span class="sxs-lookup"><span data-stu-id="6d03a-258">Stop the current recording.</span></span> <span data-ttu-id="6d03a-259">记录将以文件的形式返回。</span><span class="sxs-lookup"><span data-stu-id="6d03a-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="6d03a-260">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="6d03a-260">Mixed Reality Capture</span></span>

<span data-ttu-id="6d03a-261">**/api/holographic/mrc/file （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="6d03a-262">从设备下载混合现实文件。</span><span class="sxs-lookup"><span data-stu-id="6d03a-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="6d03a-263">使用 op = stream query 参数进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="6d03a-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="6d03a-264">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-264">Parameters</span></span>
* <span data-ttu-id="6d03a-265">filename：要获取的视频文件的名称、hex64 编码</span><span class="sxs-lookup"><span data-stu-id="6d03a-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="6d03a-266">op： stream</span><span class="sxs-lookup"><span data-stu-id="6d03a-266">op : stream</span></span>

<span data-ttu-id="6d03a-267">**/api/holographic/mrc/file （删除）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="6d03a-268">从设备中删除混合现实记录。</span><span class="sxs-lookup"><span data-stu-id="6d03a-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="6d03a-269">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-269">Parameters</span></span>
* <span data-ttu-id="6d03a-270">filename：要删除的文件的名称，hex64 已编码</span><span class="sxs-lookup"><span data-stu-id="6d03a-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="6d03a-271">**/api/holographic/mrc/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="6d03a-272">返回存储在设备上的混合现实文件的列表</span><span class="sxs-lookup"><span data-stu-id="6d03a-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="6d03a-273">**/api/holographic/mrc/photo （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="6d03a-274">采用混合现实照片，并在设备上创建文件</span><span class="sxs-lookup"><span data-stu-id="6d03a-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="6d03a-275">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-275">Parameters</span></span>
* <span data-ttu-id="6d03a-276">holo：捕获全息影像： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="6d03a-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="6d03a-277">pv：捕获 PV 摄像机： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="6d03a-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="6d03a-278">RenderFromCamera：（仅限 HoloLens 2）从照片/视频相机的角度呈现： true 或 false （默认为 true）</span><span class="sxs-lookup"><span data-stu-id="6d03a-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="6d03a-279">**/api/holographic/mrc/settings （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="6d03a-280">获取默认的混合现实捕获设置</span><span class="sxs-lookup"><span data-stu-id="6d03a-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="6d03a-281">**/api/holographic/mrc/settings （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="6d03a-282">设置默认的混合现实捕获设置。</span><span class="sxs-lookup"><span data-stu-id="6d03a-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="6d03a-283">其中一些设置适用于系统的 MRC 照片和视频捕获。</span><span class="sxs-lookup"><span data-stu-id="6d03a-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="6d03a-284">**/api/holographic/mrc/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="6d03a-285">获取 Windows 设备门户内混合现实捕获的状态。</span><span class="sxs-lookup"><span data-stu-id="6d03a-285">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="6d03a-286">***响应***</span><span class="sxs-lookup"><span data-stu-id="6d03a-286">***Response***</span></span>

<span data-ttu-id="6d03a-287">响应包含一个 JSON 属性，用于指示 Windows 设备门户是否正在录制视频。</span><span class="sxs-lookup"><span data-stu-id="6d03a-287">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="6d03a-288">**/api/holographic/mrc/thumbnail （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-288">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="6d03a-289">获取指定文件的缩略图图像。</span><span class="sxs-lookup"><span data-stu-id="6d03a-289">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="6d03a-290">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-290">Parameters</span></span>
* <span data-ttu-id="6d03a-291">文件名：要为其请求缩略图的文件的名称，hex64 已编码</span><span class="sxs-lookup"><span data-stu-id="6d03a-291">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="6d03a-292">**/api/holographic/mrc/video/control/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-292">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="6d03a-293">启动混合现实记录</span><span class="sxs-lookup"><span data-stu-id="6d03a-293">Starts a mixed reality recording</span></span>

<span data-ttu-id="6d03a-294">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-294">Parameters</span></span>
* <span data-ttu-id="6d03a-295">holo：捕获全息影像： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="6d03a-295">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="6d03a-296">pv：捕获 PV 摄像机： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="6d03a-296">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="6d03a-297">mic：捕获麦克风： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="6d03a-297">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="6d03a-298">环回：捕获应用音频： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="6d03a-298">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="6d03a-299">RenderFromCamera：（仅限 HoloLens 2）从照片/视频相机的角度呈现： true 或 false （默认为 true）</span><span class="sxs-lookup"><span data-stu-id="6d03a-299">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="6d03a-300">vstab：（仅限 HoloLens 2）启用视频抖动： true 或 false （默认为 true）</span><span class="sxs-lookup"><span data-stu-id="6d03a-300">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="6d03a-301">vstabbuffer：（仅限 HoloLens 2）视频抖动缓冲区延迟：0到30帧（默认为15帧）</span><span class="sxs-lookup"><span data-stu-id="6d03a-301">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="6d03a-302">**/api/holographic/mrc/video/control/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-302">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="6d03a-303">停止当前混合现实记录</span><span class="sxs-lookup"><span data-stu-id="6d03a-303">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="6d03a-304">混合现实流式处理</span><span class="sxs-lookup"><span data-stu-id="6d03a-304">Mixed Reality Streaming</span></span>

<span data-ttu-id="6d03a-305">HoloLens 支持混合现实的实时预览，通过块区下载零碎的工作方式。</span><span class="sxs-lookup"><span data-stu-id="6d03a-305">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="6d03a-306">混合现实流共享相同的参数集来控制捕获的内容：</span><span class="sxs-lookup"><span data-stu-id="6d03a-306">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="6d03a-307">holo：捕获全息影像： true 或 false</span><span class="sxs-lookup"><span data-stu-id="6d03a-307">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="6d03a-308">pv：捕获 PV 摄像机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="6d03a-308">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="6d03a-309">mic：捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="6d03a-309">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="6d03a-310">环回：捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="6d03a-310">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="6d03a-311">如果未指定任何内容：将捕获全息影像、照片/视频相机和应用音频</span><span class="sxs-lookup"><span data-stu-id="6d03a-311">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="6d03a-312">如果已指定任何参数：未指定的参数将默认为 false</span><span class="sxs-lookup"><span data-stu-id="6d03a-312">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="6d03a-313">可选参数（仅限 HoloLens 2）</span><span class="sxs-lookup"><span data-stu-id="6d03a-313">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="6d03a-314">RenderFromCamera：从照片/视频相机的角度呈现： true 或 false （默认为 true）</span><span class="sxs-lookup"><span data-stu-id="6d03a-314">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="6d03a-315">vstab：启用视频抖动： true 或 false （默认为 false）</span><span class="sxs-lookup"><span data-stu-id="6d03a-315">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="6d03a-316">vstabbuffer：视频稳定缓冲区延迟：0到30帧（默认为15帧）</span><span class="sxs-lookup"><span data-stu-id="6d03a-316">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="6d03a-317">**/api/holographic/stream/live.mp4 （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-317">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="6d03a-318">1280x720p 30fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="6d03a-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="6d03a-319">**/api/holographic/stream/live_high （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-319">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="6d03a-320">1280x720p 30fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="6d03a-320">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="6d03a-321">**/api/holographic/stream/live_med （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-321">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="6d03a-322">854x480p 30fps 2.5 Mbit stream。</span><span class="sxs-lookup"><span data-stu-id="6d03a-322">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="6d03a-323">**/api/holographic/stream/live_low （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-323">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="6d03a-324">428x240p 15fps 0.6 Mbit stream。</span><span class="sxs-lookup"><span data-stu-id="6d03a-324">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="6d03a-325">网络</span><span class="sxs-lookup"><span data-stu-id="6d03a-325">Networking</span></span>

<span data-ttu-id="6d03a-326">**/api/networking/ipconfig （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-326">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="6d03a-327">获取当前 ip 配置</span><span class="sxs-lookup"><span data-stu-id="6d03a-327">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="6d03a-328">操作系统信息</span><span class="sxs-lookup"><span data-stu-id="6d03a-328">OS Information</span></span>

<span data-ttu-id="6d03a-329">**/api/os/info （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-329">**/api/os/info (GET)**</span></span>

<span data-ttu-id="6d03a-330">获取操作系统信息</span><span class="sxs-lookup"><span data-stu-id="6d03a-330">Gets operating system information</span></span>

<span data-ttu-id="6d03a-331">**/api/os/machinename （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-331">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="6d03a-332">获取计算机名称</span><span class="sxs-lookup"><span data-stu-id="6d03a-332">Gets the machine name</span></span>

<span data-ttu-id="6d03a-333">**/api/os/machinename （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-333">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="6d03a-334">设置计算机名称</span><span class="sxs-lookup"><span data-stu-id="6d03a-334">Sets the machine name</span></span>

<span data-ttu-id="6d03a-335">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-335">Parameters</span></span>
* <span data-ttu-id="6d03a-336">名称：要设置为的新计算机名称，hex64 编码为</span><span class="sxs-lookup"><span data-stu-id="6d03a-336">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="6d03a-337">性能数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-337">Performance data</span></span>

<span data-ttu-id="6d03a-338">**/api/resourcemanager/processes （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-338">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="6d03a-339">返回正在运行的进程的列表以及详细信息</span><span class="sxs-lookup"><span data-stu-id="6d03a-339">Returns the list of running processes with details</span></span>

<span data-ttu-id="6d03a-340">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-340">Return data</span></span>
* <span data-ttu-id="6d03a-341">JSON，包含进程列表和每个进程的详细信息</span><span class="sxs-lookup"><span data-stu-id="6d03a-341">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="6d03a-342">**/api/resourcemanager/systemperf （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-342">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="6d03a-343">返回系统性能统计信息（i/o 读/写、内存统计信息等。</span><span class="sxs-lookup"><span data-stu-id="6d03a-343">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="6d03a-344">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-344">Return data</span></span>
* <span data-ttu-id="6d03a-345">包含系统信息的 JSON： CPU、GPU、内存、网络、IO</span><span class="sxs-lookup"><span data-stu-id="6d03a-345">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="6d03a-346">强力</span><span class="sxs-lookup"><span data-stu-id="6d03a-346">Power</span></span>

<span data-ttu-id="6d03a-347">**/api/power/battery （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-347">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="6d03a-348">获取当前电池状态</span><span class="sxs-lookup"><span data-stu-id="6d03a-348">Gets the current battery state</span></span>

<span data-ttu-id="6d03a-349">**/api/power/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-349">**/api/power/state (GET)**</span></span>

<span data-ttu-id="6d03a-350">检查系统是否处于低功耗状态</span><span class="sxs-lookup"><span data-stu-id="6d03a-350">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="6d03a-351">远程控制</span><span class="sxs-lookup"><span data-stu-id="6d03a-351">Remote Control</span></span>

<span data-ttu-id="6d03a-352">**/api/control/restart （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-352">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="6d03a-353">重新启动目标设备</span><span class="sxs-lookup"><span data-stu-id="6d03a-353">Restarts the target device</span></span>

<span data-ttu-id="6d03a-354">**/api/control/shutdown （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-354">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="6d03a-355">关闭目标设备</span><span class="sxs-lookup"><span data-stu-id="6d03a-355">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="6d03a-356">任务管理器</span><span class="sxs-lookup"><span data-stu-id="6d03a-356">Task Manager</span></span>

<span data-ttu-id="6d03a-357">**/api/taskmanager/app （删除）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-357">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="6d03a-358">停止现代应用</span><span class="sxs-lookup"><span data-stu-id="6d03a-358">Stops a modern app</span></span>

<span data-ttu-id="6d03a-359">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-359">Parameters</span></span>
* <span data-ttu-id="6d03a-360">包：应用包的完整名称，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="6d03a-360">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="6d03a-361">forcestop：强制停止所有进程（= 是）</span><span class="sxs-lookup"><span data-stu-id="6d03a-361">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="6d03a-362">**/api/taskmanager/app （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-362">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="6d03a-363">启动新式应用</span><span class="sxs-lookup"><span data-stu-id="6d03a-363">Starts a modern app</span></span>

<span data-ttu-id="6d03a-364">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-364">Parameters</span></span>
* <span data-ttu-id="6d03a-365">appid：要启动的应用的 PRAID，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="6d03a-365">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="6d03a-366">包：应用包的完整名称，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="6d03a-366">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="6d03a-367">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="6d03a-367">WiFi Management</span></span>

<span data-ttu-id="6d03a-368">**/api/wifi/interfaces （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-368">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="6d03a-369">枚举无线网络接口</span><span class="sxs-lookup"><span data-stu-id="6d03a-369">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="6d03a-370">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-370">Return data</span></span>
* <span data-ttu-id="6d03a-371">包含详细信息的无线接口列表（GUID、说明等）</span><span class="sxs-lookup"><span data-stu-id="6d03a-371">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="6d03a-372">**/api/wifi/network （删除）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-372">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="6d03a-373">删除与指定接口上的网络相关联的配置文件</span><span class="sxs-lookup"><span data-stu-id="6d03a-373">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="6d03a-374">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-374">Parameters</span></span>
* <span data-ttu-id="6d03a-375">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="6d03a-375">interface : network interface guid</span></span>
* <span data-ttu-id="6d03a-376">配置文件：配置文件名称</span><span class="sxs-lookup"><span data-stu-id="6d03a-376">profile : profile name</span></span>

<span data-ttu-id="6d03a-377">**/api/wifi/networks （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-377">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="6d03a-378">枚举指定网络接口上的无线网络</span><span class="sxs-lookup"><span data-stu-id="6d03a-378">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="6d03a-379">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-379">Parameters</span></span>
* <span data-ttu-id="6d03a-380">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="6d03a-380">interface : network interface guid</span></span>

<span data-ttu-id="6d03a-381">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-381">Return data</span></span>
* <span data-ttu-id="6d03a-382">网络接口上发现的无线网络的列表，详细信息</span><span class="sxs-lookup"><span data-stu-id="6d03a-382">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="6d03a-383">**/api/wifi/network （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-383">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="6d03a-384">连接或断开指定接口上的网络连接</span><span class="sxs-lookup"><span data-stu-id="6d03a-384">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="6d03a-385">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-385">Parameters</span></span>
* <span data-ttu-id="6d03a-386">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="6d03a-386">interface : network interface guid</span></span>
* <span data-ttu-id="6d03a-387">ssid： ssid，hex64 编码，用于连接到</span><span class="sxs-lookup"><span data-stu-id="6d03a-387">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="6d03a-388">op：连接或断开连接</span><span class="sxs-lookup"><span data-stu-id="6d03a-388">op : connect or disconnect</span></span>
* <span data-ttu-id="6d03a-389">createprofile： yes 或 no</span><span class="sxs-lookup"><span data-stu-id="6d03a-389">createprofile : yes or no</span></span>
* <span data-ttu-id="6d03a-390">key：共享密钥，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="6d03a-390">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="6d03a-391">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="6d03a-391">Windows Performance Recorder</span></span>

<span data-ttu-id="6d03a-392">**/api/wpr/customtrace （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-392">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="6d03a-393">上传 "配置文件，并使用上传的配置文件开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="6d03a-393">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="6d03a-394">Payload</span><span class="sxs-lookup"><span data-stu-id="6d03a-394">Payload</span></span>
* <span data-ttu-id="6d03a-395">多部分相容的 http 正文</span><span class="sxs-lookup"><span data-stu-id="6d03a-395">multi-part conforming http body</span></span>

<span data-ttu-id="6d03a-396">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-396">Return data</span></span>
* <span data-ttu-id="6d03a-397">返回 "会话状态。</span><span class="sxs-lookup"><span data-stu-id="6d03a-397">Returns the WPR session status.</span></span>

<span data-ttu-id="6d03a-398">**/api/wpr/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-398">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="6d03a-399">检索 "会话的状态</span><span class="sxs-lookup"><span data-stu-id="6d03a-399">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="6d03a-400">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-400">Return data</span></span>
* <span data-ttu-id="6d03a-401">"会话状态。</span><span class="sxs-lookup"><span data-stu-id="6d03a-401">WPR session status.</span></span>

<span data-ttu-id="6d03a-402">**/api/wpr/trace （GET）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-402">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="6d03a-403">停止 "（性能）跟踪会话</span><span class="sxs-lookup"><span data-stu-id="6d03a-403">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="6d03a-404">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-404">Return data</span></span>
* <span data-ttu-id="6d03a-405">返回跟踪 ETL 文件</span><span class="sxs-lookup"><span data-stu-id="6d03a-405">Returns the trace ETL file</span></span>

<span data-ttu-id="6d03a-406">**/api/wpr/trace （POST）**</span><span class="sxs-lookup"><span data-stu-id="6d03a-406">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="6d03a-407">启动 "（性能）跟踪会话</span><span class="sxs-lookup"><span data-stu-id="6d03a-407">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="6d03a-408">参数</span><span class="sxs-lookup"><span data-stu-id="6d03a-408">Parameters</span></span>
* <span data-ttu-id="6d03a-409">配置文件：配置文件名称。</span><span class="sxs-lookup"><span data-stu-id="6d03a-409">profile : Profile name.</span></span> <span data-ttu-id="6d03a-410">可用的配置文件存储在 perfprofiles/配置文件中。 json</span><span class="sxs-lookup"><span data-stu-id="6d03a-410">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="6d03a-411">返回数据</span><span class="sxs-lookup"><span data-stu-id="6d03a-411">Return data</span></span>
* <span data-ttu-id="6d03a-412">在 "开始" 中，返回 "会话状态。</span><span class="sxs-lookup"><span data-stu-id="6d03a-412">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d03a-413">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d03a-413">See also</span></span>
* [<span data-ttu-id="6d03a-414">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="6d03a-414">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="6d03a-415">设备门户核心 API 参考（UWP）</span><span class="sxs-lookup"><span data-stu-id="6d03a-415">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
