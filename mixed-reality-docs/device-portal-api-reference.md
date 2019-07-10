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
# <a name="device-portal-api-reference"></a>设备门户 API 参考

中的所有内容[Windows Device Portal](using-the-windows-device-portal.md)为基础构建 REST API 可用于访问数据，并以编程方式控制你的设备。

## <a name="app-deloyment"></a>应用程序出现的常见问题

**/api/app/packagemanager/package (DELETE)**

卸载应用

Parameters
* 包：要卸载的包的文件名。

**/api/app/packagemanager/package (POST)**

安装应用

Parameters
* 包：要安装的包的文件名。

有效负载
* 多部分符合标准的 http 正文

**/api/app/packagemanager/packages (GET)**

检索具有详细信息的系统上已安装应用的列表

返回数据
* 已安装程序包的详细信息列表

**/api/app/packagemanager/state (GET)**

获取正在进行应用安装中的状态

## <a name="dump-collection"></a>转储集合

**/api/debug/dump/usermode/crashcontrol (DELETE)**

禁用的故障转储集合旁加载应用

Parameters
* packageFullname： 包名称

**/api/debug/dump/usermode/crashcontrol (GET)**

获取旁加载应用设置故障转储收集

Parameters
* packageFullname： 包名称

**/api/debug/dump/usermode/crashcontrol (POST)**

启用并设置旁加载应用程序的转储控制设置

Parameters
* packageFullname： 包名称

**/api/debug/dump/usermode/crashdump (DELETE)**

删除旁加载应用程序的故障转储

Parameters
* packageFullname： 包名称
* fileName： 转储文件的名称

**/api/debug/dump/usermode/crashdump (GET)**

检索的故障转储的旁加载应用

Parameters
* packageFullname： 包名称
* fileName： 转储文件的名称

返回数据
* 转储文件。 检查使用 WinDbg 或 Visual Studio

**/api/debug/dump/usermode/dumps (GET)**

返回所有的故障转储的旁加载应用的列表

返回数据
* 每个端加载应用的列表中的故障转储

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

枚举已注册的提供程序

返回数据
* 提供程序、 友好名称和 GUID 的列表

**/api/etw/session/realtime (GET/WebSocket)**

创建实时的 ETW 会话;通过 websocket 进行管理。

返回数据
* 从已启用提供程序的 ETW 事件

## <a name="holographic-os"></a>全息操作系统

**/api/holographic/os/etw/customproviders (GET)**

返回一系列 HoloLens 特定 ETW 提供程序未注册与系统

**/api/holographic/os/services (GET)**

返回运行的所有服务的状态。

**/api/holographic/os/settings/ipd (GET)**

获取以毫米为单位存储的 IPD （Interpupillary 距离）

**/api/holographic/os/settings/ipd (POST)**

设置 IPD

Parameters
* ipd:要以毫米为单位设置的新 IPD 值

**/api/holographic/os/webmanagement/settings/https (GET)**

获取 Device Portal 的 HTTPS 要求

**/api/holographic/os/webmanagement/settings/https (POST)**

设置 HTTPS 要求设备门户

Parameters
* 必需： yes、 no 或默认值

## <a name="holographic-perception"></a>Holographic 感知

**/api/holographic/perception/client (GET/WebSocket)**

接受 websocket 升级并运行 30 fps 时发送更新的感知客户端。

Parameters
* clientmode:"活动"时强制进行可视化跟踪模式下无法被动建立

## <a name="holographic-thermal"></a>Holographic 温度

**/api/holographic/thermal/stage (GET)**

获取设备 （0 正常，1 热，关键 2） 的热量阶段

## <a name="perception-simulation-control"></a>Perception 模拟控件

**/api/holographic/simulation/control/mode (GET)**

获取的模拟模式

**/api/holographic/simulation/control/mode (POST)**

设置模拟模式

Parameters
* 模式： 模拟模式： 默认、 模拟、 远程，旧

**/api/holographic/simulation/control/stream （删除）**

删除控制流。

**/api/holographic/simulation/control/stream (GET/WebSocket)**

打开的控制流的 web 套接字连接。

**/api/holographic/simulation/control/stream (POST)**

创建控制流 （优先级是必需的） 或将数据发布到创建的流 (所需的 streamId)。 已发布的数据应为类型应用程序/八进制流。

## <a name="perception-simulation-playback"></a>Perception 模拟播放

**/api/holographic/simulation/playback/file (DELETE)**

删除录制。

Parameters
* 录制：若要删除的记录的名称。

**/api/holographic/simulation/playback/file (POST)**

将录制内容上传。

**/api/holographic/simulation/playback/files (GET)**

获取所有录制。

**/api/holographic/simulation/playback/session (GET)**

获取记录的当前播放状态。

Parameters
* 录制：录制的名称。

**/api/holographic/simulation/playback/session/file (DELETE)**

卸载录制。

Parameters
* 录制：记录要卸载的名称。

**/api/holographic/simulation/playback/session/file (POST)**

加载录制。

Parameters
* 录制：记录要加载的名称。

**/api/holographic/simulation/playback/session/files (GET)**

获取所有已加载的记录。

**/api/holographic/simulation/playback/session/pause (POST)**

暂停录制。

Parameters
* 录制：录制的名称。

**/api/holographic/simulation/playback/session/play (POST)**

播放录制内容。

Parameters
* 录制：录制的名称。

**/api/holographic/simulation/playback/session/stop (POST)**

停止录制。

Parameters
* 录制：录制的名称。

**/api/holographic/simulation/playback/session/types (GET)**

获取加载录制中的数据类型。

Parameters
* 录制：录制的名称。

## <a name="perception-simulation-recording"></a>Perception 模拟录制

**/api/holographic/simulation/recording/start (POST)**

开始录制。 仅单个记录可以同时处于活动状态。 必须设置为 head、 手、 spatialMapping 或环境。

Parameters
* 头：将设置为 1 到记录头数据。
* 手：设置为 1 以记录现有数据。
* spatialMapping:设置为 1 来记录空间映射。
* 环境：设置为 1 以记录环境数据。
* 名称：记录的名称。
* singleSpatialMappingFrame:设置为 1 来记录仅一个空间映射框架。

**/api/holographic/simulation/recording/status (GET)**

获取正在记录状态。

**/api/holographic/simulation/recording/stop (GET)**

停止当前录制。 录制将返回为一个文件。

## <a name="mixed-reality-capture"></a>混合现实捕获

**/api/holographic/mrc/file (GET)**

从设备下载混合的现实文件。 使用 op = 流式处理的流查询参数。

Parameters
* 文件名：编码的要获取的视频文件的名称，hex64
* 操作： 流

**/api/holographic/mrc/file (DELETE)**

删除设备中记录了混合的现实。

Parameters
* 文件名：编码的要删除的文件的名称，hex64

**/api/holographic/mrc/files (GET)**

返回存储在设备上的混合的现实文件列表

**/api/holographic/mrc/photo (POST)**

采用混合的现实照片，并创建在设备上的文件

Parameters
* holo： 捕获全息： true 或 false （默认值为 false）
* pv： 捕获 PV 照相机： true 或 false （默认值为 false）
* RenderFromCamera:从照片/视频摄像机角度来看 (仅 HoloLens 2) 呈现器： true 或 false （默认值为 true）

**/api/holographic/mrc/settings (GET)**

获取默认混合现实捕获设置

**/api/holographic/mrc/settings (POST)**

设置默认混合现实捕获设置。  其中某些设置将应用于系统的 MRC 照片和视频捕获。

**/api/holographic/mrc/status (GET)**

获取混合现实的记录 （运行、 已停止） 状态

**/api/holographic/mrc/thumbnail (GET)**

获取指定的文件的缩略图。

Parameters
* 文件名：编码为其请求缩略图的文件的名称，hex64

**/api/holographic/mrc/video/control/start (POST)**

启动混合的现实录制

Parameters
* holo： 捕获全息： true 或 false （默认值为 false）
* pv： 捕获 PV 照相机： true 或 false （默认值为 false）
* mic： 捕获麦克风： true 或 false （默认值为 false）
* 环回： 捕获应用音频： true 或 false （默认值为 false）
* RenderFromCamera:从照片/视频摄像机角度来看 (仅 HoloLens 2) 呈现器： true 或 false （默认值为 true）
* vstab:(仅 HoloLens 2) 启用视频防抖动： true 或 false （默认值为 true）
* vstabbuffer:(仅 HoloLens 2) 视频防抖动缓冲区滞后时间：0 到 30 帧 （默认为 15 帧）

**/api/holographic/mrc/video/control/stop (POST)**

停止当前混合现实录制

## <a name="mixed-reality-streaming"></a>流式处理的混合的现实

HoloLens 支持混合现实通过成块下载的分片 mp4 的实时预览。

混合的现实流共享同一组参数来控制捕获内容：
* holo： 捕获全息： true 或 false
* pv： 捕获 PV 照相机： true 或 false
* mic： 捕获麦克风： true 或 false
* 环回： 捕获应用音频： true 或 false

如果未指定任何这些： 将捕获全息、 照片/视频摄像机和应用音频<br>
如果指定了任何： 未指定的参数将默认为 false

可选参数 (仅 HoloLens 2)
* RenderFromCamera: 从照片/视频摄像机的角度来看呈现: true 或 false （默认值为 true）
* vstab： 启用视频防抖动： true 或 false （默认值为 false）
* vstabbuffer： 视频防抖动缓冲区延迟：0 到 30 帧 （默认为 15 帧）

**/api/holographic/stream/live.mp4 (GET)**

1280x720p 30 fps 5Mbit 流。

**/api/holographic/stream/live_high.mp4 (GET)**

1280x720p 30 fps 5Mbit 流。

**/api/holographic/stream/live_med.mp4 (GET)**

854x480p 30 fps 2.5Mbit 流。

**/api/holographic/stream/live_low.mp4 (GET)**

428x240p 15 fps 0.6Mbit 流。

## <a name="networking"></a>网络

**/api/networking/ipconfig (GET)**

获取当前的 ip 配置

## <a name="os-information"></a>OS 信息

**/api/os/info (GET)**

获取操作系统信息

**/api/os/machinename (GET)**

获取计算机名称

**/api/os/machinename (POST)**

设置计算机名称

Parameters
* 名称：新的计算机名称，hex64 编码，将设置为

## <a name="performance-data"></a>性能数据

**/api/resourcemanager/processes (GET)**

返回正在运行进程的详细信息的列表

返回数据
* 与进程和每个进程的详细信息的列表的 JSON

**/api/resourcemanager/systemperf (GET)**

返回系统性能统计信息 （I/O 读/写、 内存统计信息等。

返回数据
* 系统信息的 JSON:CPU、 GPU、 内存、 网络、 IO

## <a name="power"></a>电源

**/api/power/battery (GET)**

获取当前的电池状态

**/api/power/state (GET)**

检查系统是否在低功耗状态

## <a name="remote-control"></a>远程控制

**/api/control/restart (POST)**

重新启动目标设备

**/api/control/shutdown （文章）**

关闭目标设备

## <a name="task-manager"></a>任务管理器

**/api/taskmanager/app (DELETE)**

停止新型应用程序

Parameters
* 包：完整应用程序包，hex64 编码名称
* 强制停止：强制停止所有进程 （= 是）

**/api/taskmanager/app (POST)**

启动新式应用

Parameters
* appid:若要启动的应用程序的 PRAID，hex64 编码
* 包：完整应用程序包，hex64 编码名称

## <a name="wifi-management"></a>WiFi 管理

**/api/wifi/interfaces (GET)**

枚举无线网络接口

返回数据
* 无线接口的详细信息 （GUID、 description 等） 的列表

**/api/wifi/network (DELETE)**

删除与指定接口上的网络相关联的配置文件

Parameters
* 接口： 网络接口的 guid
* 配置文件： 配置文件名称

**/api/wifi/networks (GET)**

枚举指定的网络接口上的无线网络

Parameters
* 接口： 网络接口的 guid

返回数据
* 找到详细信息的网络接口上的无线网络的列表

**/api/wifi/network (POST)**

连接或断开到指定的接口上的网络

Parameters
* 接口： 网络接口的 guid
* ssid: ssid，hex64 编码，以连接到
* 操作： 连接或断开连接
* createprofile: yes 或 no
* 密钥： 共享密钥，hex64 编码

## <a name="windows-performance-recorder"></a>Windows Performance Recorder

**/api/wpr/customtrace (POST)**

上传 WPR 配置文件并启动跟踪使用已上传配置文件。

有效负载
* 多部分符合标准的 http 正文

返回数据
* 返回 WPR 会话状态。

**/api/wpr/status (GET)**

检索 WPR 会话的状态

返回数据
* WPR 会话状态。

**/api/wpr/trace (GET)**

停止 WPR （性能） 跟踪会话

返回数据
* 返回跟踪 ETL 文件

**/api/wpr/trace (POST)**

启动跟踪会话 WPR （性能）

Parameters
* 配置文件：配置文件名称。 可用的配置文件存储在 perfprofiles/profiles.json

返回数据
* 启动时，返回 WPR 会话状态。

## <a name="see-also"></a>请参阅
* [使用 Windows 设备门户](using-the-windows-device-portal.md)
* [设备门户 core API 参考 (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
