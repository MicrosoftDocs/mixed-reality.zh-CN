---
title: HoloLens 已知问题
description: 这是可能影响 HoloLens 开发人员的已知问题列表。
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: 故障排除、已知问题、帮助
ms.openlocfilehash: 9ec15957b75ca3ec51dd01f5b9b4bc7371912c5a
ms.sourcegitcommit: a11999e92e4e87516a6dcceabc2c5ed7642f1fd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68887268"
---
# <a name="hololens-known-issues"></a>HoloLens 已知问题

这是针对 HoloLens 影响开发人员的已知问题的最新列表。 如果看到的是奇怪的行为, 请先查看此处。 此列表将在发现或报告新问题时进行更新, 或者在将来的 HoloLens 软件更新中解决问题。

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>无法通过 Visual Studio 进行连接和部署到 HoloLens

>[!NOTE]
>上次更新:8/8 @ 5: 晚上11点-Visual Studio 已发布 VS 2019 版本 16.2, 其中包括对此问题的修复。 建议更新到此最新版本, 以避免出现此错误。

Visual Studio 发布了 VS 2019 版本 16.2, 其中包括对此问题的修复。 建议更新到此最新版本, 以避免出现此错误。

问题根本原因:使用 Visual Studio 2015 或早期版本的 Visual Studio 2017 的用户在其 HoloLens 上部署和调试应用程序, 然后使用同一 HoloLens 的最新版本的 Visual Studio 2017 或 Visual Studio 2019 将受到影响。 较新版本的 Visual Studio 部署了新版本的组件, 但较旧版本中的文件仍保留在设备上, 导致较新版本失败。  这会导致出现以下错误消息:DEP0100:请确保目标设备已启用开发人员模式。 <ip>由于错误 80004005, 无法获取开发人员许可证。
 
**解决方法**： 

我们的团队当前正在努力解决问题。 同时, 你可以使用以下步骤来解决此问题, 并帮助取消阻止部署和调试:  
1. 打开 Visual Studio
2. 文件-> > 项目
3. Visual C# -> Windows Desktop > 控制台应用 (.NET Framework)
4. 为项目指定一个名称 (例如 HoloLensDeploymentFix), 并确保框架至少设置为 .NET Framework 4.5, 然后单击 "确定"。
5. 右键单击解决方案资源管理器中的 "引用" 节点, 然后添加以下引用 (单击 "浏览" 部分, 然后单击 "浏览 ..."按钮):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >如果尚未安装 10.0.18362.0, 请使用最新版本。
 
6. 右键单击 "解决方案资源管理器中的项目, 然后选择" > 现有项 "。
 
7. 浏览到 C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86, 并将筛选器更改为 "所有\*文件\*(.)"
 
8. 选中 "SirepClient" 和 "SshClient", 然后单击 "添加"。
 
9. 在解决方案资源管理器中找到两个文件 (这些文件应位于文件列表的底部), 并将属性窗口中的 "复制到输出目录" 更改为 "始终复制"
 
10. 在该文件的顶部, 将以下内容添加到现有的 "using" 语句列表中: 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. 在 "static void Main (...)" 内部, 添加以下代码:
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
 
13. 在包含已编译程序的文件夹 (例如 C:\MyProjects\HoloLensDeploymentFix\bin\Debug) 上打开命令提示符
 
14. 运行可执行文件, 并提供设备的 IP 地址作为命令行参数。  (如果通过 USB 连接, 则可以使用 127.0.0.1, 否则使用设备的 WiFi IP 地址。)例如, "HoloLensDeploymentFix 127.0.0.1"
 
15. 退出该工具而不使用任何消息 (这只需要几秒钟) 后, 你将能够从 Visual Studio 2017 或更高版本进行部署和调试。  不需要继续使用该工具。

我们将在可用时提供更多更新。

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>在 HoloLens 上启动 Microsoft Store 和应用时出现的问题

>[!NOTE]
>上次更新:4/2 @ 10 AM-已解决问题。 

尝试在 HoloLens 上启动 Microsoft Store 和应用时可能会遇到问题。 我们确定, 当后台应用程序更新在特定序列中部署较新版本的框架包, 而其一个或多个从属应用仍在运行时, 会出现此问题。 在这种情况下, 自动应用更新将 .NET Native Framework (版本10.0.25531 到 10.0.27413) 的新版本传递给正在运行的应用, 以使使用以前版本的 Framework 的所有正在运行的应用都无法正确更新。  用于框架更新的流程如下所示:

1.  将从应用商店下载并安装新的框架包
2.  使用较旧框架的所有应用程序都 "更新" 为使用较新版本

如果步骤2在完成之前中断, 则未注册新框架的任何应用都将无法从 "开始" 菜单启动。  我们相信, HoloLens 上的任何应用都可能会受到此问题的影响。

某些用户已报告关闭挂起的应用程序并启动其他应用程序 (如反馈中心、三维查看器或照片) 解决了这些问题-但是, 这不能在 100% 的时间运行。

我们有根本原因导致此问题不是由更新本身引起的, 而是操作系统中导致 .NET Native framework 更新处理不正确的 bug。 我们很高兴地宣布, 我们已确定修复, 并发布了包含该修补程序的更新 (操作系统版本 17763.380)。 

若要查看设备是否可以进行更新, 请执行以下操作:

1.  中转到 "设置" 应用并打开 "更新 & 安全性"
2.  单击 "检查更新"
3.  如果更新到 17763.380, 请更新到此版本以接收应用挂起 bug 的修补程序
4.  更新到此版本的操作系统时, 应用程序应按预期方式工作。

此外, 与每个 HoloLens OS 版本一样, 我们已将 FFU 图像发布到 Microsoft 下载中心 https://aka.ms/hololensdownload/10.0.17763.380 。 

如果你不想进行更新, 我们发布了 3/29 Microsoft Store UWP 应用的新版本。 获得应用商店的更新版本后:

1) 打开应用商店并确认它已加载。
2) 使用布隆笔势打开菜单。
3) 尝试打开以前中断的应用
3) 如果仍无法启动, 请点击并按住损坏的应用程序的图标, 然后选择 "卸载"。
4) 从应用商店 Resinstall 这些应用。

如果你的设备仍无法加载应用, 你可以通过以下方式通过下载中心旁加载 .NET Native Framework 和运行时的版本:

1)  请从 Microsoft 下载中心下载[此 zip 文件](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)。  解压缩会生成两个文件。  。 .Appx. .appx. .appx. .appx. .appx. .appx. .appx
2)  请验证你的设备是否已进行开发解锁。  如果尚未执行此操作, 请参阅[此处](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)的说明。
3)  然后, 你需要进入 Windows 设备门户。  我们的建议是通过 USB 来完成此操作, 可以通过在浏览 http://127.0.0.1:10080 器中键入来完成此操作。  
4)  完成 Windows 设备门户后, 我们需要你将下载的两个文件 "侧加载"。  若要执行此操作, 需要向下滚动到 "应用" 部分, 并单击 "应用"。
5)  随后会看到类似于下面的屏幕。  要转到显示 "安装应用程序" 的部分, 并浏览到解压这两个 APPX 文件的位置。  你一次只能执行一个操作, 因此在选择第一个项后, 在 "部署" 部分下单击 "开始"。  然后对第二个 APPX 文件执行此操作。 
  ![用于安装加载端应用的 Windows 设备门户](images/20190322-DevicePortal.png)<br>
6)  此时, 我们相信您的应用程序应再次开始工作, 您也可以访问应用商店。
7)  在某些情况下, 在启动受影响的应用程序之前, 需要运行额外的步骤来启动3D 查看器应用程序。 

我们非常感谢你的耐心, 因为我们已经完成了解决此问题的过程, 我们期待继续与我们的社区合作, 以创建成功的混合现实体验。

## <a name="connecting-to-wifi"></a>连接到 WiFi

在 OOBE & 设置期间, 凭据超时为2分钟。 用户名/密码需要在2分钟内输入, 否则 "用户名" 字段会自动清除。

建议使用蓝牙键盘输入长密码。

## <a name="device-update"></a>设备更新
* 30秒后, shell 可能会消失一次。 请执行**布隆**手势以恢复会话。

## <a name="visual-studio"></a>Visual Studio
* 请参阅安装适用于 HoloLens 开发的 Visual Studio 的最新版本的[工具](install-the-tools.md)。
* 在将应用程序从 Visual Studio 部署到 HoloLens 时, 可能会看到以下错误:**无法对已打开用户映射的文件执行所请求的操作。（HRESULT 中的异常：0x800704C8)** 。 如果发生这种情况, 请重试, 部署通常会成功。

## <a name="emulator"></a>仿真
* 并非 Microsoft Store 中的所有应用都与模拟器兼容。 例如, 不能在模拟器上播放年轻人 Conker 和片段。
* 无法在仿真程序中使用 PC 网络摄像机。
* Windows 设备门户的实时预览功能不适用于模拟器。 你仍可以捕获混合现实视频和图像。

## <a name="unity"></a>Unity
* 请参阅安装适用于 HoloLens 开发的最新 Unity 版本的[工具](install-the-tools.md)。
* [Hololens unity 论坛](http://forum.unity3d.com/threads/known-issues.394627/)中介绍了 Unity Hololens Technical Preview 的已知问题。

## <a name="windows-device-portal"></a>Windows Device Portal
* 混合现实捕获中的实时预览功能可能会出现几秒钟的延迟。
* 在 "虚拟输入" 页上, "虚拟手势" 部分下的手势和滚动控件不起作用。 使用它们将不起作用。 同一页面上的虚拟键盘工作正常。
* 在设置中启用 "开发人员模式" 后, 可能需要几秒钟才能打开设备门户。

## <a name="api"></a>API
* 如果应用程序将[焦点](focus-point-in-unity.md)置于用户后面或 "正常" 设置为 "摄像", 则全息体将不会在混合现实捕获照片或视频中出现。 在 Windows 中修复此 bug 之前, 如果应用程序主动设置了[焦点](focus-point-in-unity.md), 则这些应用程序应确保将平面法线设置为相对相机前进 (例如 normal =-摄像)。

## <a name="xbox-wireless-controller"></a>Xbox 无线控制器
* 必须先更新 Xbox 无线控制器, 然后才能将其与 HoloLens 配合使用。 请确保在尝试将控制器与 HoloLens 配对之前处于[最新状态](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)。
* 如果在连接 Xbox 无线控制器时重新启动 HoloLens, 控制器将不会自动重新连接到 HoloLens。 在3分钟后控制器关闭之前, "指南" 按钮指示灯会慢慢闪烁。 若要立即重新连接控制器, 请关闭控制器电源, 方法是按住 "指南" 按钮, 直到指示灯亮起。 再次打开控制器时, 它将重新连接到 HoloLens。
* 如果在连接 Xbox 无线控制器时, HoloLens 进入待机状态, 则控制器上的任何输入都将唤醒 HoloLens。 使用完控制器后, 可以通过关闭控制器来阻止此操作。
