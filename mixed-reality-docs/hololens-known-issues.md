---
title: HoloLens 的已知问题
description: 这是可能会影响 HoloLens 开发人员的已知问题的列表。
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: 进行故障排除，已知问题，帮助
ms.openlocfilehash: 1ef9e9f411e16d2f604930f3146ede1d03d7c0f6
ms.sourcegitcommit: c36b8c8573f51afa79504c4a17084e4f55d2f664
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67789482"
---
# <a name="hololens-known-issues"></a>HoloLens 的已知问题

这是面向 HoloLens 影响开发人员的已知问题的当前列表。 首先请查看此处如果看到异常行为。 随着新问题的发现或报告，或在将来的 HoloLens 软件更新中解决问题的方式都将保留此列表已更新。

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>无法连接并将其部署到 HoloLens 通过 Visual Studio

>[!NOTE]
>上次更新时间：7/8 @ 7:25 PM-团队已确定根本原因，目前正在修复上。 以下可用的解决方法。 

我们都能发现此问题的根本原因。 使用 Visual Studio 2015 或 Visual Studio 2017 的早期版本来部署和调试其 HoloLens 上的应用程序，然后使用相同的 HoloLens 随后使用最新版本的 Visual Studio 2017 或 Visual Studio 2019 的用户将会受到影响。 

较新版本的 Visual Studio 部署新版本的组件，但从较旧版本的文件中留下导致失败的较新版本的设备上。  这将导致以下错误消息：DEP0100:请确保目标设备已启用的开发人员模式。 无法获取开发人员许可证上<ip>由于错误 80004005。
 
**解决方法**： 

我们的团队目前正在从事一个修复。 在此期间，可以使用以下步骤来解决此问题并帮助解除阻止部署和调试：  
1. 打开 Visual Studio
2. 文件-> 新建-> 项目
3. Visual C# -> Windows 桌面-> 控制台应用 (.NET Framework)
4. 为项目提供名称 (例如 HoloLensDeploymentFix)，并确保框架至少设置为.NET Framework 4.5，然后单击确定。
5. 右键单击解决方案资源管理器中的引用节点，然后添加以下引用 （单击浏览部分，单击浏览...按钮）：
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >如果没有安装 10.0.18362.0，使用你拥有的最新版本。
 
6. 右键单击解决方案资源管理器中的项目，然后选择添加-> 现有项。
 
7. 浏览到 C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86 并更改到筛选器"的所有文件 (\*。\*)"
 
8. 选择 SirepClient.dll 和 SshClient.dll 并单击"添加"。
 
9. 找到并选择这两个文件在解决方案资源管理器 （它们应位于的文件列表的底部） 并将"复制到输出目录"中属性窗口更改为"始终复制"
 
10. 在文件的顶部，以下代码添加到现有列表的 using 语句： 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. 在"静态 void Main(...)"，添加以下代码：
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. 生成-> 生成解决方案
 
13. 打开命令提示符向包含已编译的.exe (例如 C:\MyProjects\HoloLensDeploymentFix\bin\Debug) 的文件夹
 
14. 运行可执行文件并提供设备的 IP 地址作为命令行参数。  （如果通过 USB 连接，您可以使用 127.0.0.1，否则，请使用设备的 WiFi IP 地址。）例如，"HoloLensDeploymentFix 127.0.0.1"
 
15. 一旦该工具已退出并且没有任何消息 （这应只需几秒钟），您现在将能够部署和调试从 Visual Studio 2017 或更高版本。  继续的使用该工具不是必需的。

我们将提供进一步更新可用时。

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>启动的 Microsoft Store 和 HoloLens 上的应用程序的问题

>[!NOTE]
>上次更新时间：4/2 @ 上午 10 点-解决问题。 

尝试启动的 Microsoft Store 和 HoloLens 上的应用程序时，可能会遇到问题。 我们已确定后台应用程序更新部署时一个特定序列中的框架包的较新版本或多个其依赖的应用程序仍在运行时，会出现此问题。 在这种情况下，自动应用更新提供新版本的.NET 本机框架 （版本 10.0.25531 到 10.0.27413） 引起的不正确的所有正在运行的应用使用以前版本的 framework 的更新运行的应用。  Framework 更新流程如下所示:-

1.  从应用商店下载并安装新的 framework 包
2.  使用较旧框架的所有应用都更新以使用较新版本

如果在完成之前中断步骤 2 然后为其注册的更新的框架不是任何应用将无法从开始菜单中启动。  我们认为此问题可能会影响在 HoloLens 上的任何应用。

一些用户的已报告，关闭挂起的应用程序并启动其他应用如反馈中心，3D 查看器或照片解决了问题为它们-但是，这不起作用 100%的时间。

我们具有根导致此问题不导致更新本身，但一个 bug 导致.NET Native 处理不正确的 framework 更新在 OS 中的。 我们很高兴地宣布我们确定了修补程序，并且已发布的更新 (OS 版本 17763.380) 包含此修补程序。 

若要查看你的设备是否可能请需要更新：

1.  转到"设置"应用并打开"更新和安全"
2.  单击"检查更新"
3.  如果提供了 17763.380 更新，请更新到此版本，以接收应用程序挂起 bug 的修复程序
4.  在更新到此版本的操作系统时，应用应按预期方式工作。

此外，我们使用每个 HoloLens OS 版本执行的操作，因为我们已发布 FFU 映像到从 Microsoft 下载中心获得 https://aka.ms/hololensdownload/10.0.17763.380 。 

如果不想要执行更新，我们发布了截至 3/29 的 Microsoft Store UWP 应用的新版本。 一旦有更新的版本的存储：

1) 打开存储区并确认它在加载时。
2) 布隆手势用于打开的菜单。
3) 尝试打开应用程序以前损坏
3) 如果仍无法启动，点击并按住中断应用程序的图标并选择卸载。
4) Resinstall 这些应用商店中的。

如果你的设备仍无法加载应用，你通过这样做可以旁加载版本的.NET 本机框架和运行时通过从下载中心获得：

1)  请下载[此 zip 文件](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)从 Microsoft 下载中心获得。  解压缩将生成两个文件。  Microsoft.NET.Native.Runtime.1.7.appx 和 Microsoft.NET.Native.Framework.1.7.appx
2)  请验证你的设备适用于开发人员解锁。  如果您没有这样做之前执行此操作的说明[此处](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)。
3)  随后想要将导入 Windows Device Portal。  建议在执行此操作通过 USB 和将会通过键入 http://127.0.0.1:10080 到浏览器。  
4)  Windows Device Portal 了我们需要你为"端加载"后的两个文件下载的。  若要执行此操作，需要停机的左侧和右侧栏，直到转到"应用"部分并单击"应用"。
5)  然后，您将看到一个屏幕，类似于下面。  你想要转到显示"安装应用"部分，并浏览到你在其中解压缩这两个 APPX 文件。  可以仅执行一次一个地操作，因此后选择第一个，然后单击"转到"下的部署部分。  然后执行此操作的第二个 APPX 文件。 
  ![Windows Device Portal 安装旁加载的应用](images/20190322-DevicePortal.png)<br>
6)  此时我们认为您的应用程序应会再次开始工作，您还可以获取对应用商店。
7)  在某些情况下，有必要运行受影响的应用将启动之前启动 3D 的查看器应用额外的步骤。 

我们非常感谢你的耐心等待，因为我们已进行解决，此问题的过程，并希望继续使用我们的社区创建成功的混合现实体验。

## <a name="connecting-to-wifi"></a>连接到 WiFi

OOBE 设置 （&），在没有凭据超时为 2 分钟。 需要在 2 分钟否则为会自动清除用户名字段中输入用户名/密码。

我们建议使用蓝牙键盘来输入长密码。

## <a name="device-update"></a>设备更新
* 在新的更新后的 30 秒 shell 可能消失，一次。 请执行**布隆**手势来恢复您的会话。

## <a name="visual-studio"></a>Visual Studio
* 请参阅[安装的工具](install-the-tools.md)建议 HoloLens 开发的 Visual Studio 的最新版本。
* 部署到你 HoloLens 从 Visual Studio 应用程序，可能会看到错误：**不能在具有用户映射部分打开的文件上执行请求的操作。（HRESULT 中的异常：0x800704C8)** 。 如果发生这种情况，重试，而你的部署通常会成功。

## <a name="emulator"></a>仿真程序
* 在 Microsoft Store 中的并非所有应用都都在仿真程序与兼容。 例如，Young Conker 和片段不是在模拟器上播放。
* 无法在仿真程序中使用的 PC 是网络摄像头。
* Windows Device Portal 的实时预览功能并不适用于仿真程序。 你仍然可以捕获混合现实视频和图像。

## <a name="unity"></a>Unity
* 请参阅[安装的工具](install-the-tools.md)Unity 建议 HoloLens 开发的最新版本。
* 中介绍了 Unity HoloLens Technical Preview 的已知的问题[HoloLens Unity 论坛](http://forum.unity3d.com/threads/known-issues.394627/)。

## <a name="windows-device-portal"></a>Windows Device Portal
* 混合现实捕获中的实时预览功能可能会出现几秒钟的延迟。
* 在虚拟输入页上，虚拟手势部分下的手势和滚动控件不起作用。 使用它们会产生任何影响。 在同一页上的虚拟键盘正常工作。
* 在启用之后设置中的开发人员模式下，可能需要几秒钟才会启用开关后，若要打开设备门户。

## <a name="api"></a>API
* 如果应用程序设置[关注点](focus-point-in-unity.md)用户或垂直于 camera.forward，后面全息不会出现在混合现实捕获照片或视频。 如果应用程序正在设置，修复此 bug 后使用的 Windows，直到[关注点](focus-point-in-unity.md)它们应确保平面正常设置相反的照相机正向 (例如正常 =-camera.forward)。

## <a name="xbox-wireless-controller"></a>Xbox 无线控制器
* Xbox 无线控制器 S 之前必须先更新用于 HoloLens。 确保您[最新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)然后再尝试对你的控制器与 HoloLens。
* 如果 Xbox 无线控制器连接时重新启动你 HoloLens，控制器将不会自动重新连接到 HoloLens。 指南按钮灯将闪烁缓慢直到控制器关闭后 3 分钟。 若要重新连接你的控制器立即，通过保留指南按钮，直到指示灯会关闭控制器关闭电源。 当你开启你的控制器再次时，它将重新连接到 HoloLens。
* 如果你 HoloLens 进入待机 Xbox 无线控制器连接时，在控制器上的任何输入将唤醒 HoloLens。 您可以禁止此行为通过关闭你的控制器，完成后使用它。
