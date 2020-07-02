---
title: 使用 Windows 设备门户
description: 使用适用于 HoloLens 的 Windows 设备门户可以通过 Wi-Fi 或 USB 远程配置和管理设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包含许多工具，可帮助你管理 HoloLens 以及调试和优化应用。
author: hamalawi
ms.author: moelhama
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 设备门户，HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 234f8a5f2550c4437445ec3ac2726a3588f8bdbe
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441835"
---
# <a name="using-the-windows-device-portal"></a>使用 Windows 设备门户

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens（第一代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> Windows 设备门户</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

使用适用于 HoloLens 的 Windows 设备门户可以通过 Wi-Fi 或 USB 远程配置和管理设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包含许多工具，可帮助你管理 HoloLens 以及调试和优化应用。

本文档专门介绍适用于 HoloLens 的 Windows 设备门户。 若要使用适用于桌面（包括 Windows Mixed Reality）的 Windows 设备门户，请参阅 [Windows 设备门户概述](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>将 HoloLens 设置为使用 Windows 设备门户

1. 打开 HoloLens 的电源，然后戴上设备。
2. 针对 HoloLens2 执行[开始手势](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)，或者在 HoloLens（第一代）上执行[开花手势](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)，以启动主菜单。 
3. 凝视“设置”磁贴，然后在 HoloLens（第一代）上执行[隔空敲击](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)手势，或者在 HoloLens 2 上通过[触摸或手部射线](https://docs.microsoft.com/hololens/hololens2-basic-usage)选择该磁贴。 
4. 选择“更新”菜单项。
5. 选择“面向开发人员”菜单项。
6. 启用“开发人员模式”。
7. [向下滚动](gaze-and-commit.md#composite-gestures)并启用“设备门户”。
8. 如果要设置 Windows 设备门户以便可以通过 USB 或 Wi-Fi 将应用部署到此 HoloLens，请单击“配对”以[生成配对 PIN](using-visual-studio.md)。 在首次部署期间，请在“PIN”弹出窗口中保持打开“设置”应用，直到在 Visual Studio 中输入了 PIN 才将它关闭。

   ![在 Windows Holographic 的“设置”应用中启用开发人员模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>通过 Wi-Fi 进行连接

1. [将 HoloLens 连接到 Wi-Fi](connecting-to-wi-fi-on-hololens.md)。
2. 通过以下任一方法查找设备的 IP 地址：
   * 依次转到“设置”>“网络和 Internet”>“Wi-Fi”>“高级选项”。
   * 转到“设置”>“网络和 Internet”，然后选择“硬件属性” 。

![HoloLens 2 设置](images/windows-device-portal-img-16.png)

3. 在电脑上的 Web 浏览器中，转到 https://<HOLOLENS IP 地址>
   * 浏览器中将显示以下消息：“此网站的安全证书有问题。” 由于颁发给 Device Portal 的证书是测试证书，因此会显示上述消息。 你可以暂时忽略此证书错误并继续。

## <a name="connecting-over-usb"></a>通过 USB 进行连接

1. [安装所需的工具](install-the-tools.md)，确保在电脑上安装包含 Windows 10 开发人员工具的 Visual Studio Update 1。 这支持 USB 连接。
2. 使用适用于 HoloLens（第一代）的 micro-USB 数据线或适用于 HoloLens 2 的 USB-C 数据线将 HoloLens 连接到电脑。
3. 在电脑上的 Web 浏览器中，转到 [https://127.0.0.1:10080](https://127.0.0.1:10080)。

## <a name="connecting-to-an-emulator"></a>连接到仿真器

也可以将 Device Portal 与仿真器结合使用。 若要连接到设备门户，请使用[工具栏](using-the-hololens-emulator.md)。 单击此图标：![“打开设备门户”图标](images/emulator-deviceportal.png) **打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。

## <a name="creating-a-username-and-password"></a>创建用户名和密码

![设置对 Windows 设备门户的访问](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*设置对 Windows 设备门户的访问*

首次连接到 HoloLens 上的 Device Portal 时，需要创建用户名和密码。
1. 在电脑上的 Web 浏览器中，输入 HoloLens 的 IP 地址。 将打开“设置访问”页面。
2. 单击或敲击“请求 PIN”，然后查看 HoloLens 屏幕以获取生成的 PIN。
3. 在“设备上显示的 PIN”文本框中输入该 PIN。
4. 输入将用于连接到 Device Portal 的用户名。 无需使用 Microsoft 帐户 (MSA) 名称或域名作为用户名。
5. 输入密码并进行确认。 密码长度必须至少为七个字符。 无需使用 MSA 密码或域密码作为密码。
6. 单击“配对”以连接到 HoloLens 上的 Windows 设备门户。

今后如果你想要更改此用户名和密码，可以导航到 https://<HOLOLENS IP 地址>/devicepair.htm 来访问设备安全性页，然后重复上述过程。

## <a name="security-certificate"></a>安全证书

如果在浏览器中看到“证书错误”，可以通过创建与该设备的信任关系来修复该错误。

每个 HoloLens 会生成唯一的自签名证书以供其 SSL 连接使用。 默认情况下，此证书不受电脑的 Web 浏览器信任，因此你可能会看到“证书错误”。 通过从你的 HoloLens 下载此证书（借助 USB 或信任的 WLAN 网络）并在你的电脑上信任该证书，可以安全地连接到设备。
1. **确保在安全网络（USB 或信任的 Wi-Fi 网络）中操作。**
2. 从设备门户上的“安全性”页下载此设备的证书。
   * 导航到 https://<HOLOLENS IP 地址>/devicepair.htm
   * 打开“系统”>“首选项”对应的节点。 
   * 向下滚动到“设备安全性”，然后单击“下载此设备的证书”按钮。
3. 在电脑上安装“受信任的根证书颁发机构”存储中的证书。
   * 在 Windows 菜单中键入：管理计算机证书并启动小程序。
   * 展开“受信任的根证书颁发机构”文件夹。
   * 单击“证书”文件夹。
   * 在“操作”菜单中选择：“所有任务”>“导入...”
   * 使用从 Device Portal 下载的证书文件，完成“证书导入向导”。
4. 重新启动浏览器。

>[!NOTE]
> 此证书仅在该设备上受信任，如果刷写了设备，用户必须再次执行此过程。


## <a name="device-portal-pages"></a>Device Portal 页面

### <a name="home"></a>主页

![Microsoft HoloLens 上的 Windows 设备门户主页](images/windows-device-portal-home-page-1000px.png)<br>
*Microsoft HoloLens 上的 Windows 设备门户主页*

Device Portal 会话从主页开始。 可从主页的左侧导航栏访问其他页面。

主页顶部的工具栏提供对常用状态和功能的访问。
* **联机**：指示设备是否已连接到 Wi-Fi。
* **关机**：关闭设备。
* **重启**：关闭再打开设备的电源。
* **安全**：打开“设备安全性”页。
* **冷**：指示设备的温度。
* **交流电源**：指示设备是否已接上电源并正在充电。
* **帮助**：打开 REST 接口文档页。

主页将显示以下信息：
* **设备状态：** 监视设备的运行状况并报告严重错误。
* **Windows 信息：** 显示 HoloLens 的名称，以及当前安装的 Windows 版本。
* **首选项**部分包含以下设置：
   * **IPD**：设置瞳孔间距 (IPD)，它是在用户直视前方时两个瞳孔中心之间的距离，以毫米为单位。 该设置将立即生效。 在设置你的设备时，会自动计算该默认值。
   * **设备名称**：为 HoloLens 指定一个名称。 更改此值后，必须重新启动设备才能使该值生效。 单击“保存”后，对话框将询问是要立即重新启动还是稍后重新启动设备。
   * **睡眠设置**：设置当设备已接上电源并使用电池时进入睡眠状态之前要等待的时长。

### <a name="3d-view"></a>3D 视图

![Microsoft HoloLens 上 Windows 设备门户中的“3D 视图”页](images/3dview-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“3D 视图”页*

使用“3D 视图”页面可查看 HoloLens 感知周围环境的方式。 使用鼠标即可导览该视图：
* 旋转：单击左键并移动鼠标；
* 平移：单击右键并移动鼠标；
* 缩放：滑动鼠标滚轮。
* **跟踪选项**
   * 通过选中“强制视觉跟踪”可打开持续视觉跟踪。 
   * “暂停”会停止视觉跟踪。
* **视图选项**：设置 3D 视图中的选项：
  * **跟踪**：指示视觉跟踪是否处于活动状态。
  * **显示地面**：显示方格形式的地平面。
  * **显示锥体**：显示视锥。
  * **显示防抖动平面**：显示 HoloLens 用于稳定动作的平面。
  * **显示网格**：显示代表周围环境的空间映射网格。
  * **显示空间定位点**：显示活动应用的空间定位点。 必须单击“更新”按钮才能获取和刷新定位点。
  * **显示细节**：显示手的位置、头部旋转四元数，以及设备原点矢量的实时变化。
  * **全屏按钮**：以全屏模式显示 3D 视图。 按 ESC 键可退出全屏视图。
* **图面重构**：单击或敲击“更新”可显示设备的最新空间映射网格。 完成整个过程可能需要一些时间（但最多只需几秒钟）。 在 3D 视图中，网格不会自动更新，必须手动单击“更新”才能获取设备的最新网格。 单击“保存”可在电脑上将当前的空间映射网格保存为 obj 文件。
* **空间定位点**：单击“更新”可显示或更新活动应用的空间定位点。

### <a name="mixed-reality-capture"></a>混合现实捕获

![Microsoft HoloLens 上 Windows 设备门户中的“混合现实捕获”页](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“混合现实捕获”页*

使用“混合现实捕获”页面可保存 HoloLens 中的媒体流。
* **捕获设置**：通过检查以下设置来控制捕获的媒体流：
  * **全息影像**：捕获视频流中的全息内容。 呈现全息图时使用的是单声道，而不是立体声。
  * **PV 相机**：捕获照片/视频相机中的视频流。
  * **麦克风音频**：捕获麦克风阵列中的音频。
  * **应用音频**：捕获当前正在运行的应用中的音频。
  * **从相机渲染**：从照片/视频相机的角度对齐捕获内容，前提是[正在运行的应用支持此功能](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)（仅限 HoloLens 2）。
  * **实时预览质量**：选择用于实时预览的屏幕分辨率、帧速率和流处理速率。
* **音频设置**（仅限 HoloLens 2）：
  * **音频媒介类别**：选择在处理麦克风时使用的类别。 “默认值”将包括某些环境，这些环境中的“通信”会应用背景噪音消除。 
  * **应用音频增益**：应用于应用音频音量的增益。
  * **麦克风音频增益**：应用于麦克风音频音量的增益。
* **照片和视频设置**（HoloLens 2，版本 2004 或更高版本）：
  * **捕获配置文件**：选择拍摄照片和视频时使用的配置文件。 配置文件决定可用的分辨率和帧速率。
  * **照片分辨率**：拍摄照片时使用的分辨率。
  * **视频分辨率和帧速率**：拍摄视频时使用的分辨率和帧速率。
  * **视频稳定缓冲区**：拍摄视频时使用的缓冲区大小。 此值越大，弥补快速移动的效果越好。
* 单击或敲击“实时预览”按钮可显示捕获流。 “停止实时预览”会停止捕获流。
* 单击或敲击“录制”可使用指定的设置开始录制混合现实流。 “停止录制”会结束录制，并保存录制内容。
* 单击或敲击“拍摄照片”可从捕获流中捕获静止图像。
* 单击或点击“还原默认设置”，可还原音频、照片和视频设置的默认设置。
* **视频和照片**：显示在设备上捕获的视频和照片列表。

此页面上的所有设置都适用于使用 Windows 设备门户完成的捕获，但一些设置还适用于系统 MRC（“开始”菜单、硬件按钮、全局语音命令、Miracast）和自定义 MRC 记录器。

|  设置  |  适用于系统 MRC  |  适用于自定义 MRC 记录器 |
|----------|----------|----------|
|  全息影像  |  否  |  否 |
|  PV 摄像头  |  否  |  否 |
|  麦克风音频  |  否  |  否 |
|  应用音频  |  否  |  否 |
|  从摄像头渲染  |  是    |  是（可以重写） |
|  实时预览质量  |  否  |  否 |
|  音频媒介类别  |  是  |  否 |
|  应用音频增益  |  是  |  是（可以重写） |
|  麦克风音频增益  |  是  |  是（可以重写） |
|  捕获配置文件  |  是  |  否 |
|  照片分辨率  |  是  |  否 |
|  视频分辨率和帧速率  |  是  |  否 |
|  视频稳定缓冲区  |  是  |  是（可以重写） |

> [!NOTE]
> [同步 MRC 存在限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)：
> * 如果当 Windows 设备门户正在录制视频时某个应用尝试访问照片/视频相机，则视频录制将会停止。
>   * 如果应用以 SharedReadOnly 模式访问照片/视频相机，HoloLens 2 将不会停止视频录制。
> * 如果应用正在使用照片/视频相机，则 Windows 设备门户可以拍摄照片或录制视频。
> * 实时传送视频流：
>   * 从 Windows 设备门户实时传送视频流时，HoloLens（第一代）会阻止应用访问照片/视频相机。
>   * 如果应用正在使用照片/视频相机，则 HoloLens（第一代）将无法实时传送视频流。
>   * 当应用尝试以 ExclusiveControl 模式访问照片/视频相机时，HoloLens 2 会自动停止实时传送视频流。
>   * 当应用正在使用 PV 相机时，HoloLens 2 可以启动实时传送视频流。

### <a name="performance-tracing"></a>性能跟踪

![Microsoft HoloLens 上 Windows 设备门户中的“性能跟踪”页](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“性能跟踪”页*

从 HoloLens 中捕获 [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) 跟踪。
* **可用配置文件**：从下拉列表中选择 WPR 配置文件，然后单击或敲击“开始”以开始跟踪。
* **自定义配置文件**：单击或敲击“浏览”以从电脑中选择 WPR 配置文件。 单击或敲击“上传并启动”以开始跟踪。

若要停止跟踪，请单击“停止”链接。 请保持打开此页，直到跟踪文件完成下载。

可以打开捕获的 ETL 文件以供在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中进行分析。

### <a name="processes"></a>进程

![Microsoft HoloLens 上 Windows 设备门户中的“进程”页](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“进程”页*

显示有关当前正在运行的进程的详细信息。 这包括应用和系统进程。

### <a name="system-performance"></a>系统性能

![Microsoft HoloLens 上 Windows 设备门户中的“系统性能”页](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“系统性能”页*

显示系统诊断信息的实时图形，如电源使用情况、帧速率和 CPU 负载。

可用的指标如下所示：
* **SoC 电源**：片上系统的瞬时用电量，为一分钟平均值
* **系统电源**：系统的瞬时用电量，为一分钟平均值
* **帧速率**：每秒帧数、每秒丢失的垂直消隐数和连续丢失的垂直消隐数
* **GPU**：GPU 引擎利用率、总可用量的百分比
* **CPU**：总可用量的百分比
* **I/O**：读取和写入次数
* **网络**：接收和发送数据量
* **内存**：总计、已用、已提交、已分页和未分页

### <a name="apps"></a>“应用”

![Microsoft HoloLens 上 Windows 设备门户中的“应用”页](images/windows-device-portal-apps-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“应用”页*

管理 HoloLens 上安装的应用。
* **已安装的应用**：删除和启动应用。
* **正在运行的应用**：列出当前正在运行的应用。
* **安装应用**：从计算机/网络上的文件夹中选择应用包进行安装。
* **依赖项**：为要安装的应用添加依赖项。
* **部署**：将所选应用和依赖项部署到 HoloLens。

### <a name="app-crash-dumps"></a>应用故障转储

![Microsoft HoloLens 上 Windows 设备门户中的“应用故障转储”页](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“应用故障转储”页*

此页面允许你收集旁加载应用的故障转储。 对于要收集其故障转储的每个应用，请选中对应的“已启用故障转储”复选框。 返回到此页面可收集故障转储。 可[在 Visual Studio 中打开转储文件进行调试](https://msdn.microsoft.com/library/d5zhxt22.aspx)。

### <a name="file-explorer"></a>文件资源浏览器

![Microsoft HoloLens 上 Windows 设备门户中的“文件资源浏览器”页](images/fileexplorer-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“文件资源浏览器”页*

使用文件资源管理器可以浏览、上传和下载文件。 对于从 Visual Studio 或设备门户部署的应用，可以处理“文档”文件夹、“图片”文件夹和本地存储文件夹中的文件。

### <a name="kiosk-mode"></a>展台模式

>[!NOTE]
>展台模式仅适用于 [Microsoft HoloLens Commercial Suite](commercial-features.md)。

有关如何通过 Windows 设备门户启用展台模式的最新说明，请查看 Windows IT 专业人员中心内的[在展台模式下设置 HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 一文。

### <a name="logging"></a>日志记录

![Microsoft HoloLens 上 Windows 设备门户中的“日志记录”页](images/windows-device-portal-logging-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“日志记录”页*

管理 HoloLens 上的实时 Windows 事件跟踪 (ETW)。

选中“隐藏提供程序”以仅显示“事件”列表。 
* **已注册的提供程序**：选择 ETW 提供程序和跟踪级别。 跟踪级别是以下值之一：
   1. 异常退出或终止
   2. 严重错误
   3. 警告
   4. 非错误警告

单击或敲击“启用”以开始跟踪。 提供程序将添加到“已启用的提供程序”下拉列表。
* **自定义提供程序**：选择自定义 ETW 提供程序和跟踪级别。 根据其 GUDI 标识提供程序。 不要在 GUID 中包含括号。
* **已启用的提供程序**：列出已启用的提供程序。 从下拉列表中选择一个提供程序，然后单击或敲击“禁用”可停止跟踪。 单击或敲击“全部停止”会暂停所有跟踪。
* **提供程序历史记录**：显示已在当前会话期间启用的 ETW 提供程序。 单击或敲击“启用”可激活已禁用的提供程序。 单击或敲击“清除”可清除历史记录。
* **事件**：以表格格式列出来自选定提供程序的 ETW 事件。 此表将实时更新。 在该表格下方，单击“清除”按钮可删除其中的所有 ETW 事件。 这不会禁用任何提供程序。 可以单击“保存到文件”以将当前收集的 ETW 事件本地导出到 CSV 文件。
* **筛选器**：用于按 ID、关键字、级别、提供程序名称、任务名称或文本筛选收集的 ETW 事件。 可将多个条件组合在一起：
   1. 对于应用到同一属性的条件，将显示可满足其中任何一个条件的事件。
   2. 对于应用到不同属性的条件，事件必须满足所有条件

例如，可以指定条件 *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*

### <a name="simulation"></a>模拟

![Microsoft HoloLens 上 Windows 设备门户中的“模拟”页](images/windows-device-portal-simulation-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“模拟”页*

允许你记录和播放用于测试的输入数据。
* **捕获房间**：用于下载模拟房间文件，该文件包含用户周围环境的空间映射网格。 为该房间命名，然后单击“捕获”以在电脑上将该数据保存为 .xef 文件。 此房间文件可以加载到 HoloLens 仿真器中。
* **录制**：选中要录制的流、为录制内容命名，然后单击或敲击“录制”开始录制。 使用 HoloLens 执行操作，然后单击“停止”在电脑上将数据保存为 .xef 文件。 可以在 HoloLens 仿真器或设备上加载此文件。
* **播放**：单击或敲击“上传录制内容”可从电脑中选择 xef 文件，然后将数据发送到 HoloLens。
* **控制模式**：在 HoloLens 上，从下拉列表中选择“默认”或“模拟”，然后单击或敲击“设置”按钮选中该模式。   相反，选择“模拟”会禁用 HoloLens 上的真实传感器，并使用已上载的模拟数据。 如果切换到“模拟”，HoloLens 将不会响应真实用户，除非切换回“默认”。

### <a name="networking"></a>网络

![Microsoft HoloLens 上 Windows 设备门户中的“网络”页](images/windows-device-portal-networking-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“网络”页*

管理 HoloLens 上的 Wi-Fi 连接。
* **WiFi 适配器**：使用下拉控件选择 Wi-Fi 适配器和配置文件。 单击或敲击“连接”以使用选定的适配器。
* **可用网络**：列出 HoloLens 可连接到的 Wi-Fi 网络。 单击或敲击“刷新”可更新列表。
* **IP 配置**：显示网络连接的 IP 地址和其他详细信息。

### <a name="virtual-input"></a>虚拟输入

![Microsoft HoloLens 上 Windows 设备门户中的“虚拟输入”页](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的“虚拟输入”页*

将键盘输入从远程计算机发送到 HoloLens。

单击或敲击**虚拟键盘**下的区域可将键击发送到 HoloLens。 在“输入文本”文本框中键入内容，然后单击或敲击“发送”可将键击发送到活动应用。 

## <a name="device-portal-rest-apis"></a>设备门户 REST API

设备门户中的所有内容都是基于 [REST API](device-portal-api-reference.md) 创建的，你可以选择性地使用这些 API 来访问数据和以编程方式控制设备。
