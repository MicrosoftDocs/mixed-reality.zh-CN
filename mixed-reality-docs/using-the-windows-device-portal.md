---
title: 使用 Windows 设备门户
description: 通过用于 HoloLens 的 Windows 设备门户，你可以通过 Wi-fi 或 USB 远程配置和管理你的设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包含许多工具，可帮助你管理 HoloLens 并调试和优化你的应用程序。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 设备门户、HoloLens
ms.openlocfilehash: 17ed27653c8e3ec19c8c42b625fbd12cde2c5d84
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623323"
---
# <a name="using-the-windows-device-portal"></a>使用 Windows 设备门户

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens（第一代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

通过用于 HoloLens 的 Windows 设备门户，你可以通过 Wi-fi 或 USB 远程配置和管理你的设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包含许多工具，可帮助你管理 HoloLens 并调试和优化你的应用程序。

本文档专门介绍适用于 HoloLens 的 Windows 设备门户。 若要使用适用于桌面的 Windows 设备门户（包括 Windows Mixed Reality），请参阅[Windows 设备门户概述](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>将 HoloLens 设置为使用 Windows 设备门户

1. 打开 HoloLens 的电源，然后戴上设备。
2. 在 HoloLens 上执行 HoloLens2 或[布隆](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)的[启动笔势](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)（第一代）以启动主菜单。 
3. 查看 "**设置**" 磁贴，并在 hololens （第一代）上执行 "[轻敲](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)" 手势，或在 hololens 2 上通过[触摸或使用手](https://docs.microsoft.com/hololens/hololens2-basic-usage)中选择它。 
4. 选择“更新”菜单项。
5. 选择“面向开发人员”菜单项。
6. 启用“开发人员模式”。
7. [向下滚动](gaze-and-commit.md#composite-gestures)并启用**设备门户**。
8. 如果要设置 Windows 设备门户，以便可以通过 USB 或 Wi-fi 将应用部署到此 HoloLens，请单击 "**配对**" 以[生成配对 PIN](using-visual-studio.md)。 在第一次部署过程中，将 "设置" 应用保留在 "PIN" 弹出窗口中，直到输入到 Visual Studio 中。

   ![在 Windows 全息版的设置应用中启用开发人员模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>通过 Wi-fi 连接

1. [将 HoloLens 连接到 wi-fi](connecting-to-wi-fi-on-hololens.md)。
2. 查找设备的 IP 地址。
   * 在 "**设置" > Network & > > Internet**"下的" 设置 "中找到设备的 IP 地址。
3. 从电脑上的 web 浏览器中转到 https：//< YOUR_HOLOLENS_IP_ADDRESS >
   * 浏览器将显示以下消息： "此网站的安全证书有问题"。 由于颁发给设备门户的证书是测试证书，因此会显示上述消息。 你可以暂时忽略此证书错误并继续。

## <a name="connecting-over-usb"></a>通过 USB 连接

1. [安装这些工具](install-the-tools.md)，确保你的 Visual Studio Update 1 具有安装在你的电脑上的 Windows 10 开发人员工具。 这支持 USB 连接。
2. 使用微型 USB 电缆将 HoloLens 连接到电脑。
3. 在电脑上的 web 浏览器中转到[https://127.0.0.1:10080](https://127.0.0.1:10080)。

## <a name="connecting-to-an-emulator"></a>连接到模拟器

也可以将设备门户与仿真器结合使用。 若要连接到设备门户，请使用[工具栏](using-the-hololens-emulator.md)。 单击此图标： ![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**：在模拟器中打开用于 HoloLens OS 的 Windows 设备门户。

## <a name="creating-a-username-and-password"></a>创建用户名和密码

![设置对 Windows 设备门户的访问权限](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*设置对 Windows 设备门户的访问*

首次连接到 HoloLens 上的设备门户时，需要创建用户名和密码。
1. 在电脑上的 Web 浏览器中，输入 HoloLens 的 IP 地址。 将打开“设置访问”页面。
2. 单击或点击 "**请求 pin** "，并查看 HoloLens 显示以获取生成的 pin。
3. 在 "设备" 文本框中**显示的 pin**中输入 pin。
4. 输入将用于连接到设备门户的用户名。 无需使用 Microsoft 帐户 (MSA) 名称或域名作为用户名。
5. 输入密码并进行确认。 密码长度必须至少为七个字符。 无需使用 MSA 密码或域密码作为密码。
6. 单击 "**配对**" 以连接到 HoloLens 上的 Windows 设备门户。

如果你想要随时更改此用户名或密码，可以通过以下方式来重复此过程：访问设备安全页：通过导航到： https：//< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm。

## <a name="security-certificate"></a>安全证书

如果你在浏览器中看到 "证书错误"，则可以通过创建与设备的信任关系来修复该错误。

每个 HoloLens 会生成唯一的自签名证书以供其 SSL 连接使用。 默认情况下，此证书不受电脑的 Web 浏览器信任，因此你可能会看到“证书错误”。 通过从你的 HoloLens 下载此证书（借助 USB 或信任的 WLAN 网络）并在你的电脑上信任该证书，可以安全地连接到设备。
1. **请确保使用的是安全网络（USB 或你信任的 Wi-fi 网络）。**
2. 从设备门户上的 "安全性" 页下载此设备的证书。
   * 导航到： https：//< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm
3. 在电脑上的 "受信任的根证书颁发机构" 存储中安装证书。
   * 在 Windows 菜单中，键入： "管理计算机证书" 并启动小程序。
   * 展开 "**受信任的根证书颁发机构**" 文件夹。
   * 单击 "**证书**" 文件夹。
   * 从“操作”菜单中，依次选择“所有任务”&gt;“导入...”
   * 使用从设备门户下载的证书文件，完成“证书导入向导”。
4. 重新启动浏览器。

## <a name="device-portal-pages"></a>设备门户页面

### <a name="home"></a>“主页”

![Microsoft HoloLens 上的 Windows 设备门户主页](images/windows-device-portal-home-page-1000px.png)<br>
*Microsoft HoloLens 上的 Windows 设备门户主页*

设备门户会话从主页开始。 可从主页的左侧导航栏访问其他页面。

主页顶部的工具栏提供对常用状态和功能的访问。
* **联机**：指示设备是否已连接到 WLAN。
* **关机**：关闭设备。
* **重启**：重新接通设备的电源。
* **安全**：打开“设备安全”页面。
* **冷**：指示设备的温度。
* **交流电源**：指示设备是否已接通电源并正在充电。
* **帮助**：打开 REST 接口文档页面。

主页将显示以下信息：
* **设备状态：** 监视设备的运行状况，并报告严重错误。
* **Windows 信息：** 显示 HoloLens 的名称和当前安装的 Windows 版本。
* **首选项**部分包含以下设置：
   * **IPD**：设置瞳孔间距 (IPD)，它是在用户直视前方时两个瞳孔中心之间的距离，以毫米为单位。 该设置将立即生效。 在设置你的设备时，会自动计算该默认值。
   * **设备名称**：为 HoloLens 分配一个名称。 更改此值后，必须重新启动设备才能使该值生效。 单击 "**保存**" 后，对话会询问你是要立即重启设备还是稍后重新启动。
   * **睡眠设置**：当设备已接通电源并使用电池时，设置该设备进入睡眠状态之前要等待的时长。

### <a name="3d-view"></a>3D 视图

Microsoft HoloLens 上 Windows 设备门户中 ![3D 视图页面](images/3dview-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的3D 视图页面*

使用“3D 视图”页面可查看 HoloLens 感知周围环境的方式。 使用鼠标即可导览该视图：
* 旋转：左键单击 + 鼠标;
* 平移：右键单击 + 鼠标;
* Zoom：鼠标滚动。
* **跟踪选项**
   * 通过检查**强制视觉对象跟踪**打开连续的视觉跟踪。 
   * **暂停**停止视觉对象跟踪。
* **视图选项**：在三维视图上设置选项：
  * **跟踪**：指示视觉跟踪是否处于活动状态。
  * **显示地面**：显示方格形式的地平面。
  * **显示锥体**：显示视锥。
  * **显示防抖动平面**：显示 HoloLens 用于稳定动作的平面。
  * **显示网格**：显示表示你的环境的空间映射网格。
  * **显示空间锚**：显示活动应用的空间锚。 必须单击 "更新" 按钮，才能获取和刷新锚。
  * **显示详细信息**：实时显示手的位置、头部旋转四元数和设备原点矢量的变化。
  * **“全屏”按钮**：以全屏模式显示 3D 视图。 按 ESC 键可退出全屏视图。
* **Surface 重构**：单击或点击 "**更新**" 以显示设备的最新空间映射网格。 完全传递可能需要一些时间才能完成（长达几秒钟）。 网格不会在三维视图中自动更新，您必须手动单击 "**更新**" 以从设备获取最新的网格。 单击 "**保存**" 可将当前空间映射网格作为 obj 文件保存到电脑上。
* **空间锚**：单击 "更新" 可显示或更新活动应用的空间锚。

### <a name="mixed-reality-capture"></a>混合现实捕获

Microsoft HoloLens 上 Windows 设备门户中 ![Mixed Reality 捕获页面](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的混合现实捕获页面*

使用“混合现实捕获”页面可保存 HoloLens 中的媒体流。
* **设置**：通过检查以下设置来控制捕获的媒体流：
  * **全息影像**：捕获视频流中的全息内容。 呈现全息图时使用的是单声道，而不是立体声。
  * **PV 相机**：捕获照片/视频相机中的视频流。
  * **麦克风音频**：捕获麦克风阵列中的音频。
  * **应用音频**：捕获当前正在运行的应用中的音频。
  * **从照相机渲染**：如果[正在运行的应用支持](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，则将捕获与照片/视频摄像机的透视图对齐：
  * **实时预览质量**：选择用于实时预览的屏幕分辨率、帧速率和流处理速率。
* 单击或点击 "**实时预览**" 按钮，以显示捕获流。 **停止实时预览**停止捕获流。
* 单击或点击 "**记录**"，使用指定的设置开始记录混合现实流。 **停止录制**将结束录制并保存。
* 单击或点击 "**拍摄照片**"，拍摄捕获流中的静止图像。
* **视频和照片**：显示在设备上捕获的视频和照片列表。

> [!NOTE]
> 同时提供了一些[限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)：
> * 如果应用在 Windows 设备门户录制视频时尝试访问 photo/视频摄像机，视频录制将停止。
>   * 如果应用访问带有 SharedReadOnly 模式的照片/视频摄像机，则 HoloLens 2 不会停止录制视频。
> * 如果应用正在使用照片/视频摄像机，Windows 设备门户可以拍摄照片或录制视频。
> * 实时流式处理：
>   * HoloLens （第一代）会阻止应用从 Windows 设备门户实时传送视频时访问照片/视频摄像机。
>   * 如果应用正在使用 photo/视频摄像机，则 HoloLens （第一代）将无法实时传输。
>   * 在应用尝试以 ExclusiveControl 模式访问照片/视频摄像机时，HoloLens 2 自动停止实时流式处理。
>   * 在应用主动使用 PV 摄像机时，HoloLens 2 可以启动实时流。

### <a name="performance-tracing"></a>性能跟踪

Microsoft HoloLens 上 Windows 设备门户中 ![性能跟踪页面](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的 "性能跟踪" 页*

从 HoloLens 捕获[Windows 性能记录器](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx)（"）跟踪。
* **可用配置文件**：从下拉列表中选择 WPR 配置文件，然后单击或点击**开始**以开始跟踪。
* **自定义配置文件**：单击或点击**浏览**以从电脑中选择 WPR 配置文件。 单击或点击**上载并启动**以开始跟踪。

若要停止跟踪，请单击 "停止" 链接。 一直在此页上，直到跟踪文件下载完成。

可以打开捕获的 ETL 文件以供在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中进行分析。

### <a name="processes"></a>进程

Microsoft HoloLens 上 Windows 设备门户中 ![进程 "页面](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的 "进程" 页*

显示有关当前正在运行的进程的详细信息。 这包括应用和系统进程。

### <a name="system-performance"></a>系统性能

Microsoft HoloLens 上 Windows 设备门户中 ![系统性能 "页面](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的 "系统性能" 页*

显示系统诊断信息的实时图形，如电源使用情况、帧速率和 CPU 负载。

可用的指标如下所示：
* **SoC 电源**：瞬时片上系统电源使用率，平均超过一分钟
* **系统电源**：瞬时系统电源使用率，平均超过一分钟
* **帧速率**：每秒帧数、每秒丢失的垂直消隐数和连续丢失的垂直消隐数
* **GPU**：GPU 引擎使用率、总可用量的百分比
* **CPU**：可用总数百分比
* **I/O**：读取和写入
* **网络**：已接收和已发送
* **内存**：总计、已用、已提交、分页和非分页

### <a name="apps"></a>“应用”

Microsoft HoloLens 上 Windows 设备门户中 ![应用 "页面](images/windows-device-portal-apps-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的 "应用" 页*

管理 HoloLens 上安装的应用。
* **已安装的应用**：删除和启动应用。
* **正在运行的应用**：列出当前正在运行的应用。
* **安装应用**：从计算机/网络上的文件夹中选择要安装的应用包。
* **依赖项**：为要安装的应用添加依赖项。
* **部署**：将所选应用程序和依赖项部署到 HoloLens。

### <a name="app-crash-dumps"></a>应用故障转储

Microsoft HoloLens 上 Windows 设备门户中 ![应用崩溃转储页面](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的应用故障转储页面*

此页面允许你收集旁加载应用的故障转储。 对于要为其收集故障转储的每个应用，选中 "**已启用故障转储**" 复选框。 返回到此页面可收集故障转储。 可[在 Visual Studio 中打开转储文件以进行调试](https://msdn.microsoft.com/library/d5zhxt22.aspx)。

### <a name="file-explorer"></a>“文件资源管理器”

![Microsoft HoloLens 上 Windows 设备门户中的文件资源管理器页面](images/fileexplorer-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的文件资源管理器页*

使用文件资源管理器浏览、上传和下载文件。 对于从 Visual Studio 或设备门户部署的应用，可以在 "文档" 文件夹、"图片" 文件夹和 "本地存储文件夹" 中处理文件。

### <a name="kiosk-mode"></a>展台模式

>[!NOTE]
>展台模式仅适用于[Microsoft HoloLens 商业套件](commercial-features.md)。

有关通过 Windows 设备门户启用展台模式的最新说明，请查看 Windows IT 专业中心中的 "[在展台模式下设置 HoloLens" 一](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803)文。

### <a name="logging"></a>日志记录

Microsoft HoloLens 上 Windows 设备门户中 ![日志记录页面](images/windows-device-portal-logging-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的 "日志记录" 页*

管理 HoloLens 上 Windows （ETW）的实时事件跟踪。

选中 "**隐藏提供程序**" 以仅显示**事件**列表。
* **注册的提供程序**：选择 ETW 提供程序和跟踪级别。 跟踪级别是以下值之一：
   1. 异常退出或终止
   2. 严重错误
   3. 警告
   4. 非错误警告

单击或点击**启用**以开始跟踪。 提供程序将添加到**已启用的提供程序**下拉列表。
* **自定义提供程序**：选择自定义 ETW 提供程序和跟踪级别。 根据其 GUDI 标识提供程序。 不要在 GUID 中包含括号。
* **已启用的提供程序**：列出已启用的提供程序。 从下拉列表中选择一个提供程序，然后单击或点击**禁用**来停止跟踪。 单击或点击**全部停止**来暂停所有跟踪。
* **提供程序历史记录**：显示已在当前会话期间启用的 ETW 提供程序。 单击或点击**启用**来激活已禁用的提供程序。 单击或点击**清除**来清除历史记录。
* **事件**：以表格的形式列出来自选定提供程序的 ETW 事件。 此表将实时更新。 在该表下方，单击**清除**按钮可删除表中的所有 ETW 事件。 这不会禁用任何提供程序。 你可以单击**保存到文件**来将当前收集的 ETW 事件本地导出到 CSV 文件。
* **筛选器**：允许你筛选由 ID、关键字、级别、提供程序名称、任务名称或文本收集的 ETW 事件。 可以将多个条件组合在一起：
   1. 对于应用于相同属性的条件，将显示可满足这些条件之一的事件。
   2. 对于应用到其他属性的条件，事件必须满足所有条件

例如，你可以指定条件 *（任务名称包含 "Foo" 或 "Bar"）以及（文本包含 "错误" 或 "警告"）*

### <a name="simulation"></a>模拟

Microsoft HoloLens 上 Windows 设备门户中 ![模拟页面](images/windows-device-portal-simulation-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的模拟页面*

允许你记录和播放用于测试的输入数据。
* **捕获房间**：用于下载模拟房间文件，该文件包含用于用户周围环境的空间映射网格。 命名聊天室，然后单击 "**捕获**"，将数据以 xef 文件的形式保存在电脑上。 此房间文件可以加载到 HoloLens 仿真器中。
* **记录**：检查要录制的流，为录制命名，然后单击或点击 "**记录**" 以开始重编码。 使用 HoloLens 执行操作，然后单击 "**停止**" 将数据作为 xef 文件保存在电脑上。 可以在 HoloLens 仿真器或设备上加载此文件。
* **播放**：单击或点击 "**上传记录**"，从电脑选择 xef 文件，并将数据发送到 HoloLens。
* **控制模式**：从下拉列表中选择 "**默认**" 或 "**模拟**"，然后单击或点击 "**设置**" 按钮以在 HoloLens 上选择模式。 相反，选择“模拟”会禁用 HoloLens 上的真实传感器，并使用已上载的模拟数据。 如果切换到“模拟”，HoloLens 将不会响应真实用户，除非切换回“默认”。

### <a name="networking"></a>网络

Microsoft HoloLens 上 Windows 设备门户中的 ![网络 "页面](images/windows-device-portal-networking-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的 "网络" 页*

管理 HoloLens 上的 Wi-fi 连接。
* **WiFi 适配器**：使用下拉控件选择 wi-fi 适配器和配置文件。 单击或点击 "**连接**" 以使用所选适配器。
* **可用网络**：列出了 HoloLens 可以连接到的 wi-fi 网络。 单击或点击 "**刷新**" 以更新列表。
* **Ip 配置**：显示网络连接的 ip 地址和其他详细信息。

### <a name="virtual-input"></a>虚拟输入

Microsoft HoloLens 上 Windows 设备门户中 ![虚拟输入页面](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 设备门户中的虚拟输入页面*

将键盘输入从远程计算机发送到 HoloLens。

单击或点击 "**虚拟键盘**" 下的区域，以允许向 HoloLens 发送击键。 在 "**输入文本**" 文本框中键入，然后单击或点击 "**发送**"，将击键发送到活动的应用。

## <a name="device-portal-rest-apis"></a>设备门户 REST API

设备门户中的所有内容都是在[REST API](device-portal-api-reference.md)的基础之上构建的，你可以选择使用它来访问数据并以编程方式控制设备。
