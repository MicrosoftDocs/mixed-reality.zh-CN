---
title: 使用 Windows Device Portal
description: HoloLens Windows Device Portal 允许您配置和通过 Wi-fi 或 USB 远程管理你的设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包括许多工具，可帮助您管理您的 HoloLens 和调试和优化你的应用。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows Device Portal HoloLens
ms.openlocfilehash: f4319e1efa94d90bfb8cc4e5815ffa87fc865a7f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830005"
---
# <a name="using-the-windows-device-portal"></a>使用 Windows Device Portal

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens（第一代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

HoloLens Windows Device Portal 允许您配置和通过 Wi-fi 或 USB 远程管理你的设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包括许多工具，可帮助您管理您的 HoloLens 和调试和优化你的应用。

本文档将专门介绍 HoloLens Windows Device Portal。 若要为桌面 （包括 Windows Mixed Reality） 使用 Windows 设备门户，请参阅[Windows Device Portal 概述](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>设置 HoloLens 以使用 Windows Device Portal

1. 打开 HoloLens 的电源，然后戴上设备。
2. 执行[绽放](gestures.md#bloom)手势来启动主菜单。
3. 注视**设置**磁贴，并执行[air 点击](gestures.md#air-tap)手势。 执行第二个的 air-点击以在你的环境中将此应用程序。 在放置“设置”应用后，将启动该应用。
4. 选择“更新”  菜单项。
5. 选择“面向开发人员”  菜单项。
6. 启用“开发人员模式”  。
7. [向下滚动](gestures.md#composite-gestures)并启用**设备门户**。
8. 如果您设置了 Windows Device Portal 以便可以将应用部署到此 HoloLens 通过 USB 或 Wi-fi，请单击**对**到[生成一个配对的 PIN](using-visual-studio.md)。 到 Visual Studio PIN 输入在第一个部署过程之前，请将设置应用保留 PIN 弹出窗口。

   ![设置应用于 Windows Holographic 中启用开发人员模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>通过 Wi-fi 连接

1. [连接到 Wi-fi 你 HoloLens](connecting-to-wi-fi-on-hololens.md)。
2. 查找你的设备的 IP 地址。
   * 在设备上找到的 IP 地址**设置 > 网络和 Internet > Wi-fi > 高级选项**。
3. 从 web 浏览器中您的 PC 上，请转到 https://<YOUR_HOLOLENS_IP_ADDRESS>
   * 在浏览器将显示以下消息："没有此网站的安全证书有问题"。 由于颁发给 Device Portal 的证书是测试证书，因此会显示上述消息。 你可以暂时忽略此证书错误并继续。

## <a name="connecting-over-usb"></a>通过 USB 连接

1. [安装工具](install-the-tools.md)以确保您查看您的 PC 上安装了 Windows 10 开发人员工具与 Visual Studio Update 1。 这支持 USB 连接。
2. 使用微型 USB 电缆将 HoloLens 连接到电脑。
3. 通过电脑上的 Web 浏览器，转到 http://127.0.0.1:10080。

## <a name="connecting-to-an-emulator"></a>连接到模拟器

也可以将 Device Portal 与仿真器结合使用。 若要连接到设备门户，请使用[工具栏](using-the-hololens-emulator.md)。 单击此图标：![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**:在仿真器中打开 HoloLens OS 的 Windows 设备门户。

## <a name="creating-a-username-and-password"></a>创建用户名和密码

![设置对 Windows Device Portal 访问权限](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*设置对 Windows Device Portal 访问权限*

首次连接到 HoloLens 上的 Device Portal 时，需要创建用户名和密码。
1. 在电脑上的 Web 浏览器中，输入 HoloLens 的 IP 地址。 将打开“设置访问”页面。
2. 单击或点击**请求 pin**并查看 HoloLens 显示效果以获取生成的 PIN。
3. 输入在 PIN**在设备上显示 PIN**文本框中。
4. 输入将用于连接到 Device Portal 的用户名。 无需使用 Microsoft 帐户 (MSA) 名称或域名作为用户名。
5. 输入密码并进行确认。 密码长度必须至少为七个字符。 无需使用 MSA 密码或域密码作为密码。
6. 单击**对**连接到 Windows Device Portal HoloLens 上。

如果你想要在任何时候更改此用户名或密码，您可以通过访问通过导航到设备安全页中重复此过程： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm。

## <a name="security-certificate"></a>安全证书

如果你在浏览器中看到“证书错误”，可以通过创建与该设备的信任关系来修复该错误。

每个 HoloLens 会生成唯一的自签名证书以供其 SSL 连接使用。 默认情况下，此证书不受电脑的 Web 浏览器信任，因此你可能会看到“证书错误”。 通过从你的 HoloLens 下载此证书（借助 USB 或信任的 WLAN 网络）并在你的电脑上信任该证书，可以安全地连接到设备。
1. **请确保你位于安全网络 （USB 或您信任的 Wi-fi 网络）。**
2. 从设备门户上的"安全"页面下载此设备的证书。
   * 导航到： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm
3. 安装在"受信任的根证书颁发机构"存储在 PC 的证书。
   * 从 Windows 菜单中，键入：管理计算机证书和启动小程序。
   * 展开**受信任的根证书颁发机构**文件夹。
   * 单击**证书**文件夹。
   * 从操作菜单中选择：所有任务 > 导入...
   * 使用从 Device Portal 下载的证书文件，完成“证书导入向导”。
4. 重新启动浏览器。

## <a name="device-portal-pages"></a>Device Portal 页面

### <a name="home"></a>主页

![Windows Device Portal 主页上，在 Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*Windows Device Portal 主页上，在 Microsoft HoloLens*

Device Portal 会话从主页开始。 可从主页的左侧导航栏访问其他页面。

主页顶部的工具栏提供对常用状态和功能的访问。
* **联机**:指示是否将设备连接到 Wi-fi。
* **关闭**:关闭设备。
* **重新启动**:在设备上关闭后再打开。
* **安全**：将打开设备安全页。
* **冷**:指示设备的温度。
* **A/C**:指示是否在插入设备和收费。
* **帮助**:将打开的 REST 接口文档页。

主页将显示以下信息：
* **设备状态：** 监视你的设备的运行状况，并报告严重错误。
* **Windows 信息：** 显示 HoloLens 的名称和当前安装的 Windows 版本。
* **首选项**部分包含以下设置：
   * **IPD**:以毫米为单位的用户的瞳孔直接向前查找时在中心之间设置 interpupillary 距离 (IPD)，是的距离。 该设置将立即生效。 在设置你的设备时，会自动计算该默认值。
   * **设备名称**:将一个名称分配到 HoloLens。 更改此值后，必须重新启动设备才能使该值生效。 单击后**保存**，对话框将询问你是否想要立即重新启动设备，或稍后重新启动。
   * **睡眠设置**:设置要在设备进入睡眠状态时插入之前和它在由电池供电时等待时间的长度。

### <a name="3d-view"></a>3D 视图

![在 Microsoft HoloLens 上 Windows Device Portal 中的 3D 视图页](images/3dview-1000px.png)<br>
*在 Microsoft HoloLens 上 Windows Device Portal 中的 3D 视图页*

使用“3D 视图”页面可查看 HoloLens 感知周围环境的方式。 使用鼠标即可导览该视图：
* 旋转： 单击鼠标左键和鼠标;
* 平移： 右键单击 + 鼠标;
* 缩放： 鼠标滚动。
* **跟踪选项**
   * 通过检查启用连续 visual 跟踪**强制 visual 跟踪**。 
   * **暂停**直观跟踪将停止。
* **查看选项**:设置对 3D 视图选项：
  * **跟踪**:指示 visual 跟踪是否处于活动状态。
  * **显示基底**:显示越过方格形终点的 floor 平面。
  * **显示截锥**:显示视图截锥。
  * **显示稳定平面**:显示稳定动作用于 HoloLens 的平面。
  * **显示网格**:显示空间映射网格表示周围的环境。
  * **显示空间定位标记**:有关活动的应用程序的显示空间定位点。 您必须单击更新按钮以获取和刷新的定位点。
  * **显示详细信息**:显示分发位置、 头旋转的四元数和设备源向量实时变化。
  * **全屏幕按钮**:在全屏幕模式下显示三维视图。 按 ESC 键可退出全屏视图。
* **显示重新构造**:单击或点击**更新**以显示最新空间的映射网格从该设备。 完成全面检查可能需要一些时间，最多只需几秒钟。 网格不会在 3D 视图中，会自动更新，你必须手动单击**更新**以从设备获取最新的网格。 单击**保存**将当前空间映射网格另存为您的 PC 上的 obj 文件。
* **空间的定位点**:单击更新以显示或更新活动的应用程序与空间标记。

### <a name="mixed-reality-capture"></a>混合现实捕获

![在 Windows Device Portal 上 Microsoft HoloLens 混合的现实捕获页](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*在 Windows Device Portal 上 Microsoft HoloLens 混合的现实捕获页*

使用[混合现实捕获](mixed-reality-capture.md)页后，可以从 HoloLens 保存媒体流。
* **设置**:控制通过检查以下设置捕获媒体流：
  * **全息**:捕获视频流中的 holographic 内容。 呈现全息图时使用的是单声道，而不是立体声。
  * **PV 照相机**:捕获照片/视频摄像机的视频流。
  * **Mic 音频**:捕获音频从麦克风阵列。
  * **应用音频**:从当前正在运行的应用捕获音频。
  * **实时预览质量**:选择屏幕分辨率、 帧速率和流式处理速率的实时预览。
* 单击或点击**实时预览**按钮可显示捕获流。 **停止实时预览**停止捕获流式传输。
* 单击或点击**记录**开始录制混合现实流，使用指定的设置。 **停止录制**结束记录并将其保存。
* 单击或点击**Take 照片**从捕获流才能静止图像。
* **视频和照片**:显示视频和照片捕获在设备上执行的列表。

请注意，当你正从 Device Portal 中录制或流处理实时预览时，HoloLens 应用将无法捕获 MRC 照片或视频。

### <a name="performance-tracing"></a>性能跟踪

![性能跟踪 Microsoft HoloLens 上 Windows Device Portal 中的页](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*性能跟踪 Microsoft HoloLens 上 Windows Device Portal 中的页*

捕获[Windows 性能记录器](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx)来自你 HoloLens (WPR) 跟踪。
* **可用的配置文件**:从下拉列表中，然后单击或点击选择 WPR 配置文件**启动**要启动跟踪。
* **自定义配置文件**:单击或点击**浏览**WPR 配置文件选择你的 PC 中。 单击或点击**上载并启动**以开始跟踪。

若要停止跟踪，请单击停止链接。 跟踪文件完成下载之前离开此页面。

可以打开捕获的 ETL 文件以供在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中进行分析。

### <a name="processes"></a>进程

![在 Microsoft HoloLens 上 Windows Device Portal 中进程页](images/windows-device-portal-running-processes-page-1000px.png)<br>
*在 Microsoft HoloLens 上 Windows Device Portal 中进程页*

显示有关当前正在运行的进程的详细信息。 这包括应用和系统进程。

### <a name="system-performance"></a>系统性能

![Microsoft HoloLens 上 Windows Device Portal 中的系统性能页面](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows Device Portal 中的系统性能页面*

显示系统诊断信息的实时图形，如电源使用情况、帧速率和 CPU 负载。

可用的指标如下所示：
* **SoC power**:即时片上系统电源利用率，取一分钟的平均值
* **系统电源**:即时系统电源利用率，取一分钟的平均值
* **帧速率**:每秒帧数达不到每秒，VBlanks 和连续丢失的 VBlanks
* **GPU**:GPU 引擎使用率，可用的总百分比
* **CPU**： 可用的总百分比
* **I/O**:读取和写入
* **网络**：接收和发送
* **内存**:总计，在使用中，已提交，页面，和非页面缓冲

### <a name="apps"></a>应用

![在 Microsoft HoloLens 上 Windows Device Portal 中应用页](images/windows-device-portal-apps-page-1000px.png)<br>
*在 Microsoft HoloLens 上 Windows Device Portal 中应用页*

管理在 HoloLens 安装的应用。
* **已安装的应用**:删除并启动应用。
* **正在运行的应用**:列出当前正在运行的应用。
* **安装应用**:从您的计算机/网络上的文件夹中选择安装的应用的程序包。
* **依赖项**:添加要安装的应用的依赖项。
* **部署**:将所选的应用 + 依赖项部署到 HoloLens。

### <a name="app-crash-dumps"></a>应用程序故障转储

![应用 Windows Device Portal 上 Microsoft HoloLens Crash Dumps 页](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*应用 Windows Device Portal 上 Microsoft HoloLens Crash Dumps 页*

此页面允许你收集旁加载应用的故障转储。 检查**启用崩溃转储**你想要收集崩溃转储每个应用对应的复选框。 返回到此页面可收集故障转储。 转储文件可能很[Visual Studio 中打开以进行调试](https://msdn.microsoft.com/library/d5zhxt22.aspx)。

### <a name="file-explorer"></a>文件资源管理器

![在 Microsoft HoloLens 上 Windows Device Portal 中的文件资源管理器页](images/fileexplorer-1000px.png)<br>
*在 Microsoft HoloLens 上 Windows Device Portal 中的文件资源管理器页*

使用文件资源管理器来浏览、 上载和下载文件。 您可以处理和本地存储文件夹中文档文件夹，图片文件夹中，从 Visual Studio 或设备门户部署的应用程序的文件。

### <a name="kiosk-mode"></a>展台模式

>[!NOTE]
>展台模式时才可以使用[Microsoft HoloLens 商业套件](commercial-features.md)。

请检查[在展台模式下设置了 HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803)有关启用通过 Windows Device Portal 展台模式的最新说明 Windows IT 专业人员中心中的文章。

### <a name="logging"></a>日志记录

![Microsoft HoloLens 上 Windows Device Portal 中的日志记录页](images/windows-device-portal-logging-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows Device Portal 中的日志记录页*

管理实时事件跟踪 Windows (ETW) 在 HoloLens 上。

检查**隐藏提供程序**以显示**事件**仅列出。
* **注册的提供程序**:选择 ETW 提供程序和跟踪级别。 跟踪级别是以下值之一：
   1. 异常退出或终止
   2. 严重错误
   3. 警告
   4. 非错误警告

单击或点击**启用**以开始跟踪。 提供程序将添加到**已启用的提供程序**下拉列表。
* **自定义提供程序**:选择自定义的 ETW 提供程序和跟踪级别。 根据其 GUDI 标识提供程序。 不要在 GUID 中包含括号。
* **已启用提供程序**:列出了已启用提供程序。 从下拉列表中选择一个提供程序，然后单击或点击**禁用**来停止跟踪。 单击或点击**全部停止**来暂停所有跟踪。
* **提供程序历史记录**:显示当前会话过程中启用 ETW 提供程序。 单击或点击**启用**来激活已禁用的提供程序。 单击或点击**清除**来清除历史记录。
* **事件**:列出了从表格格式中的所选提供程序的 ETW 事件。 此表将实时更新。 下表中，单击**清除**按钮以从表中删除所有 ETW 事件。 这不会禁用任何提供程序。 你可以单击**保存到文件**来将当前收集的 ETW 事件本地导出到 CSV 文件。
* **筛选器**:可用于筛选通过 ID、 关键字、 级别、 提供程序名称、 任务名称或文本收集的 ETW 事件。 可以将多个条件组合在一起：
   1. 对于条件应用到相同属性的事件可以满足这些条件的任何一个显示。
   2. 条件将应用于不同的属性的事件必须满足所有条件

例如，您可以指定的条件 *（任务名称包含 Foo 或栏） 和 （文本包含 error 或警告）*

### <a name="simulation"></a>模拟

![Microsoft HoloLens 上 Windows Device Portal 中的模拟页面](images/windows-device-portal-simulation-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows Device Portal 中的模拟页面*

允许你记录和播放用于测试的输入数据。
* **捕获聊天室**:用于下载模拟的聊天室文件，其中包含用户的环境空间映射网格。 命名空间，然后单击**捕获**将数据保存为您的 PC 上的.xef 文件。 此房间文件可以加载到 HoloLens 仿真器中。
* **录制**:检查流记录、 命名录制，然后单击或点击**记录**开始重新编码。 通过在 HoloLens 执行的操作，然后依次**停止**将数据保存为您的 PC 上的.xef 文件。 可以在 HoloLens 仿真器或设备上加载此文件。
* **播放**:单击或点击**上传录制**从您的 PC 选择 xef 文件并将数据发送到 HoloLens。
* **控件模式**:选择**默认**或**模拟**从下拉列表中，然后单击或点击**设置**按钮以选择在 HoloLens 上的模式。 相反，选择“模拟”会禁用 HoloLens 上的真实传感器，并使用已上载的模拟数据。 如果切换到“模拟”，HoloLens 将不会响应真实用户，除非切换回“默认”。

### <a name="networking"></a>网络

![Microsoft HoloLens 上 Windows Device Portal 中的网络页](images/windows-device-portal-networking-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows Device Portal 中的网络页*

管理在 HoloLens 上的 Wi-fi 连接。
* **WiFi 适配器**:通过使用下拉控件选择 Wi-fi 适配器和配置文件。 单击或点击**Connect**以使用所选的适配器。
* **可用网络**:列出了 HoloLens 可以连接到 Wi-fi 网络。 单击或点击**刷新**更新列表。
* **IP 配置**:显示的 IP 地址和网络连接的其他详细信息。

### <a name="virtual-input"></a>虚拟输入

![Microsoft HoloLens 上 Windows Device Portal 中的虚拟输入页](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows Device Portal 中的虚拟输入页*

将键盘输入从远程计算机发送到 HoloLens。

单击或点击的区域下**虚拟键盘**若要启用到 HoloLens 发送击键。 在键入**输入文本**文本框中，然后单击或点击**发送**将击键发送到活动的应用程序。

## <a name="device-portal-rest-apis"></a>设备门户 REST API

设备门户中的所有内容之上构建[REST API](device-portal-api-reference.md) ，您将可以选择使用，来访问数据，并以编程方式控制你的设备。
