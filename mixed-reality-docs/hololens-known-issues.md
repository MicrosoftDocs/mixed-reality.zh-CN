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
# <a name="hololens-known-issues"></a><span data-ttu-id="5dce8-104">HoloLens 已知问题</span><span class="sxs-lookup"><span data-stu-id="5dce8-104">HoloLens known issues</span></span>

<span data-ttu-id="5dce8-105">这是针对 HoloLens 影响开发人员的已知问题的最新列表。</span><span class="sxs-lookup"><span data-stu-id="5dce8-105">This is the current list of known issues for HoloLens affecting developers.</span></span> <span data-ttu-id="5dce8-106">如果看到的是奇怪的行为, 请先查看此处。</span><span class="sxs-lookup"><span data-stu-id="5dce8-106">Check here first if you are seeing an odd behavior.</span></span> <span data-ttu-id="5dce8-107">此列表将在发现或报告新问题时进行更新, 或者在将来的 HoloLens 软件更新中解决问题。</span><span class="sxs-lookup"><span data-stu-id="5dce8-107">This list will be kept updated as new issues are discovered or reported, or as issues are addressed in future HoloLens software updates.</span></span>

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a><span data-ttu-id="5dce8-108">无法通过 Visual Studio 进行连接和部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="5dce8-108">Unable to connect and deploy to HoloLens through Visual Studio</span></span>

>[!NOTE]
><span data-ttu-id="5dce8-109">上次更新:8/8 @ 5: 晚上11点-Visual Studio 已发布 VS 2019 版本 16.2, 其中包括对此问题的修复。</span><span class="sxs-lookup"><span data-stu-id="5dce8-109">Last Update: 8/8 @ 5:11PM - Visual Studio has released VS 2019 Version 16.2 which includes a fix to this issue.</span></span> <span data-ttu-id="5dce8-110">建议更新到此最新版本, 以避免出现此错误。</span><span class="sxs-lookup"><span data-stu-id="5dce8-110">We recommend updating to this newest version to avoid experiencing this error.</span></span>

<span data-ttu-id="5dce8-111">Visual Studio 发布了 VS 2019 版本 16.2, 其中包括对此问题的修复。</span><span class="sxs-lookup"><span data-stu-id="5dce8-111">Visual Studio has released VS 2019 Version 16.2 which includes a fix to this issue.</span></span> <span data-ttu-id="5dce8-112">建议更新到此最新版本, 以避免出现此错误。</span><span class="sxs-lookup"><span data-stu-id="5dce8-112">We recommend updating to this newest version to avoid experiencing this error.</span></span>

<span data-ttu-id="5dce8-113">问题根本原因:使用 Visual Studio 2015 或早期版本的 Visual Studio 2017 的用户在其 HoloLens 上部署和调试应用程序, 然后使用同一 HoloLens 的最新版本的 Visual Studio 2017 或 Visual Studio 2019 将受到影响。</span><span class="sxs-lookup"><span data-stu-id="5dce8-113">Issue root-cause: Users who used Visual Studio 2015 or early releases of Visual Studio 2017 to deploy and debug applications on their HoloLens and then subsequently used the latest versions of Visual Studio 2017 or Visual Studio 2019 with the same HoloLens will be affected.</span></span> <span data-ttu-id="5dce8-114">较新版本的 Visual Studio 部署了新版本的组件, 但较旧版本中的文件仍保留在设备上, 导致较新版本失败。</span><span class="sxs-lookup"><span data-stu-id="5dce8-114">The newer releases of Visual Studio deploy a new version of a component, but files from the older version are left over on the device, causing the newer version to fail.</span></span>  <span data-ttu-id="5dce8-115">这会导致出现以下错误消息:DEP0100:请确保目标设备已启用开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="5dce8-115">This causes the following error message: DEP0100: Please ensure that target device has developer mode enabled.</span></span> <span data-ttu-id="5dce8-116"><ip>由于错误 80004005, 无法获取开发人员许可证。</span><span class="sxs-lookup"><span data-stu-id="5dce8-116">Could not obtain a developer license on <ip> due to error 80004005.</span></span>
 
<span data-ttu-id="5dce8-117">**解决方法**：</span><span class="sxs-lookup"><span data-stu-id="5dce8-117">**Workaround**:</span></span> 

<span data-ttu-id="5dce8-118">我们的团队当前正在努力解决问题。</span><span class="sxs-lookup"><span data-stu-id="5dce8-118">Our team is currently working on a fix.</span></span> <span data-ttu-id="5dce8-119">同时, 你可以使用以下步骤来解决此问题, 并帮助取消阻止部署和调试:</span><span class="sxs-lookup"><span data-stu-id="5dce8-119">In the meantime, you can use the following steps to work around the issue and help unblock deployment and debugging:</span></span>  
1. <span data-ttu-id="5dce8-120">打开 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5dce8-120">Open Visual Studio</span></span>
2. <span data-ttu-id="5dce8-121">文件-> > 项目</span><span class="sxs-lookup"><span data-stu-id="5dce8-121">File -> New -> Project</span></span>
3. <span data-ttu-id="5dce8-122">Visual C# -> Windows Desktop > 控制台应用 (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="5dce8-122">Visual C# -> Windows Desktop -> Console App (.NET Framework)</span></span>
4. <span data-ttu-id="5dce8-123">为项目指定一个名称 (例如 HoloLensDeploymentFix), 并确保框架至少设置为 .NET Framework 4.5, 然后单击 "确定"。</span><span class="sxs-lookup"><span data-stu-id="5dce8-123">Give the project a name (e.g. HoloLensDeploymentFix) and make sure the Framework is set to at least .NET Framework 4.5 then click OK.</span></span>
5. <span data-ttu-id="5dce8-124">右键单击解决方案资源管理器中的 "引用" 节点, 然后添加以下引用 (单击 "浏览" 部分, 然后单击 "浏览 ..."按钮):</span><span class="sxs-lookup"><span data-stu-id="5dce8-124">Right-click on the References node in Solution Explorer and add the following references (click to the 'Browse' section and click the 'Browse...' button):</span></span>
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    ><span data-ttu-id="5dce8-125">如果尚未安装 10.0.18362.0, 请使用最新版本。</span><span class="sxs-lookup"><span data-stu-id="5dce8-125">If you don't have 10.0.18362.0 installed, use the most recent version that you have.</span></span>
 
6. <span data-ttu-id="5dce8-126">右键单击 "解决方案资源管理器中的项目, 然后选择" > 现有项 "。</span><span class="sxs-lookup"><span data-stu-id="5dce8-126">Right-click on the project in Solution Explorer and choose Add -> Existing Item.</span></span>
 
7. <span data-ttu-id="5dce8-127">浏览到 C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86, 并将筛选器更改为 "所有\*文件\*(.)"</span><span class="sxs-lookup"><span data-stu-id="5dce8-127">Browse to C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86 and change the filter to "All Files (\*.\*)"</span></span>
 
8. <span data-ttu-id="5dce8-128">选中 "SirepClient" 和 "SshClient", 然后单击 "添加"。</span><span class="sxs-lookup"><span data-stu-id="5dce8-128">Select both SirepClient.dll and SshClient.dll and click "Add".</span></span>
 
9. <span data-ttu-id="5dce8-129">在解决方案资源管理器中找到两个文件 (这些文件应位于文件列表的底部), 并将属性窗口中的 "复制到输出目录" 更改为 "始终复制"</span><span class="sxs-lookup"><span data-stu-id="5dce8-129">Locate and select both files in Solution Explorer (they should be at the bottom of the list of files) and change "Copy to Output Directory" in the Properties window to "Copy always"</span></span>
 
10. <span data-ttu-id="5dce8-130">在该文件的顶部, 将以下内容添加到现有的 "using" 语句列表中:</span><span class="sxs-lookup"><span data-stu-id="5dce8-130">At the top of the file, add the following to the existing list of 'using' statements:</span></span> 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. <span data-ttu-id="5dce8-131">在 "static void Main (...)" 内部, 添加以下代码:</span><span class="sxs-lookup"><span data-stu-id="5dce8-131">Inside of “static void Main(...)”, add the following code:</span></span>
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. <span data-ttu-id="5dce8-132">生成-> 生成解决方案</span><span class="sxs-lookup"><span data-stu-id="5dce8-132">Build -> Build Solution</span></span>
 
13. <span data-ttu-id="5dce8-133">在包含已编译程序的文件夹 (例如 C:\MyProjects\HoloLensDeploymentFix\bin\Debug) 上打开命令提示符</span><span class="sxs-lookup"><span data-stu-id="5dce8-133">Open a command prompt to the folder that contains the compiled .exe (e.g. C:\MyProjects\HoloLensDeploymentFix\bin\Debug)</span></span>
 
14. <span data-ttu-id="5dce8-134">运行可执行文件, 并提供设备的 IP 地址作为命令行参数。</span><span class="sxs-lookup"><span data-stu-id="5dce8-134">Run the executable and provide the device's IP address as a command-line argument.</span></span>  <span data-ttu-id="5dce8-135">(如果通过 USB 连接, 则可以使用 127.0.0.1, 否则使用设备的 WiFi IP 地址。)例如, "HoloLensDeploymentFix 127.0.0.1"</span><span class="sxs-lookup"><span data-stu-id="5dce8-135">(If connected via USB, you can use 127.0.0.1, otherwise use the device’s WiFi IP address.)  For example, "HoloLensDeploymentFix 127.0.0.1"</span></span>
 
15. <span data-ttu-id="5dce8-136">退出该工具而不使用任何消息 (这只需要几秒钟) 后, 你将能够从 Visual Studio 2017 或更高版本进行部署和调试。</span><span class="sxs-lookup"><span data-stu-id="5dce8-136">Once the tool has exited without any messages (this should only take a few seconds), you will now be able to deploy and debug from Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="5dce8-137">不需要继续使用该工具。</span><span class="sxs-lookup"><span data-stu-id="5dce8-137">Continued use of the tool is not necessary.</span></span>

<span data-ttu-id="5dce8-138">我们将在可用时提供更多更新。</span><span class="sxs-lookup"><span data-stu-id="5dce8-138">We will provide further updates as they become available.</span></span>

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a><span data-ttu-id="5dce8-139">在 HoloLens 上启动 Microsoft Store 和应用时出现的问题</span><span class="sxs-lookup"><span data-stu-id="5dce8-139">Issues launching the Microsoft Store and apps on HoloLens</span></span>

>[!NOTE]
><span data-ttu-id="5dce8-140">上次更新:4/2 @ 10 AM-已解决问题。</span><span class="sxs-lookup"><span data-stu-id="5dce8-140">Last Update: 4/2 @ 10 AM - Issue resolved.</span></span> 

<span data-ttu-id="5dce8-141">尝试在 HoloLens 上启动 Microsoft Store 和应用时可能会遇到问题。</span><span class="sxs-lookup"><span data-stu-id="5dce8-141">You may experience issues when trying to launch the Microsoft Store and apps on HoloLens.</span></span> <span data-ttu-id="5dce8-142">我们确定, 当后台应用程序更新在特定序列中部署较新版本的框架包, 而其一个或多个从属应用仍在运行时, 会出现此问题。</span><span class="sxs-lookup"><span data-stu-id="5dce8-142">We've determined that the issue occurs when background app updates deploy a newer version of framework packages in specific sequences while one or more of their dependent apps are still running.</span></span> <span data-ttu-id="5dce8-143">在这种情况下, 自动应用更新将 .NET Native Framework (版本10.0.25531 到 10.0.27413) 的新版本传递给正在运行的应用, 以使使用以前版本的 Framework 的所有正在运行的应用都无法正确更新。</span><span class="sxs-lookup"><span data-stu-id="5dce8-143">In this case,  an automatic app update delivered a new version of the .NET Native Framework (version 10.0.25531 to 10.0.27413) caused the apps that are running to not correctly update for all running apps consuming the prior version of the framework.</span></span>  <span data-ttu-id="5dce8-144">用于框架更新的流程如下所示:</span><span class="sxs-lookup"><span data-stu-id="5dce8-144">The flow for framework update is as follows: -</span></span>

1.  <span data-ttu-id="5dce8-145">将从应用商店下载并安装新的框架包</span><span class="sxs-lookup"><span data-stu-id="5dce8-145">The new framework package is downloaded from the store and installed</span></span>
2.  <span data-ttu-id="5dce8-146">使用较旧框架的所有应用程序都 "更新" 为使用较新版本</span><span class="sxs-lookup"><span data-stu-id="5dce8-146">All apps using the older framework are ‘updated’ to use the newer version</span></span>

<span data-ttu-id="5dce8-147">如果步骤2在完成之前中断, 则未注册新框架的任何应用都将无法从 "开始" 菜单启动。</span><span class="sxs-lookup"><span data-stu-id="5dce8-147">If step 2 is interrupted before completion then any apps for which the newer framework wasn’t registered will fail to launch from the start menu.</span></span>  <span data-ttu-id="5dce8-148">我们相信, HoloLens 上的任何应用都可能会受到此问题的影响。</span><span class="sxs-lookup"><span data-stu-id="5dce8-148">We believe any app on HoloLens could be affected by this issue.</span></span>

<span data-ttu-id="5dce8-149">某些用户已报告关闭挂起的应用程序并启动其他应用程序 (如反馈中心、三维查看器或照片) 解决了这些问题-但是, 这不能在 100% 的时间运行。</span><span class="sxs-lookup"><span data-stu-id="5dce8-149">Some users have reported that closing hung apps and launching other apps such as Feedback Hub, 3D Viewer or Photos resolves the issue for them - however, this does not work 100% of the time.</span></span>

<span data-ttu-id="5dce8-150">我们有根本原因导致此问题不是由更新本身引起的, 而是操作系统中导致 .NET Native framework 更新处理不正确的 bug。</span><span class="sxs-lookup"><span data-stu-id="5dce8-150">We have root caused that this issue was not caused the update itself, but a bug in the OS that resulted in the .NET Native framework update being handled incorrectly.</span></span> <span data-ttu-id="5dce8-151">我们很高兴地宣布, 我们已确定修复, 并发布了包含该修补程序的更新 (操作系统版本 17763.380)。</span><span class="sxs-lookup"><span data-stu-id="5dce8-151">We are pleased to announce that we have identified a fix and have released an update (OS version 17763.380) containing the fix.</span></span> 

<span data-ttu-id="5dce8-152">若要查看设备是否可以进行更新, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="5dce8-152">To see if your device can take the update please:</span></span>

1.  <span data-ttu-id="5dce8-153">中转到 "设置" 应用并打开 "更新 & 安全性"</span><span class="sxs-lookup"><span data-stu-id="5dce8-153">Go to the “Settings” app and open “Update & Security”</span></span>
2.  <span data-ttu-id="5dce8-154">单击 "检查更新"</span><span class="sxs-lookup"><span data-stu-id="5dce8-154">Click “Check for Updates”</span></span>
3.  <span data-ttu-id="5dce8-155">如果更新到 17763.380, 请更新到此版本以接收应用挂起 bug 的修补程序</span><span class="sxs-lookup"><span data-stu-id="5dce8-155">If update to 17763.380 is available, please update to this build to receive the fix for the App Hang bug</span></span>
4.  <span data-ttu-id="5dce8-156">更新到此版本的操作系统时, 应用程序应按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="5dce8-156">Upon updating to this version of the OS, the Apps should work as expected.</span></span>

<span data-ttu-id="5dce8-157">此外, 与每个 HoloLens OS 版本一样, 我们已将 FFU 图像发布到 Microsoft 下载中心 https://aka.ms/hololensdownload/10.0.17763.380 。</span><span class="sxs-lookup"><span data-stu-id="5dce8-157">Additionally, as we do with every HoloLens OS release, we have posted the FFU image to the Microsoft Download Center at https://aka.ms/hololensdownload/10.0.17763.380.</span></span> 

<span data-ttu-id="5dce8-158">如果你不想进行更新, 我们发布了 3/29 Microsoft Store UWP 应用的新版本。</span><span class="sxs-lookup"><span data-stu-id="5dce8-158">If you would not like to take the update, we have released a new version of the Microsoft Store UWP app as of 3/29.</span></span> <span data-ttu-id="5dce8-159">获得应用商店的更新版本后:</span><span class="sxs-lookup"><span data-stu-id="5dce8-159">Once you have the updated version of the Store:</span></span>

1) <span data-ttu-id="5dce8-160">打开应用商店并确认它已加载。</span><span class="sxs-lookup"><span data-stu-id="5dce8-160">Open the Store and confirm that it loads.</span></span>
2) <span data-ttu-id="5dce8-161">使用布隆笔势打开菜单。</span><span class="sxs-lookup"><span data-stu-id="5dce8-161">Use the Bloom Gesture to open the menu.</span></span>
3) <span data-ttu-id="5dce8-162">尝试打开以前中断的应用</span><span class="sxs-lookup"><span data-stu-id="5dce8-162">Attempt to open previously broken apps</span></span>
3) <span data-ttu-id="5dce8-163">如果仍无法启动, 请点击并按住损坏的应用程序的图标, 然后选择 "卸载"。</span><span class="sxs-lookup"><span data-stu-id="5dce8-163">If it still cannot be launched, tap and hold the icon of the broken app and select uninstall.</span></span>
4) <span data-ttu-id="5dce8-164">从应用商店 Resinstall 这些应用。</span><span class="sxs-lookup"><span data-stu-id="5dce8-164">Resinstall these apps from the store.</span></span>

<span data-ttu-id="5dce8-165">如果你的设备仍无法加载应用, 你可以通过以下方式通过下载中心旁加载 .NET Native Framework 和运行时的版本:</span><span class="sxs-lookup"><span data-stu-id="5dce8-165">If your device is still unable to load apps, you can sideload a version of the .NET Native Framework and Runtime through the download center by doing:</span></span>

1)  <span data-ttu-id="5dce8-166">请从 Microsoft 下载中心下载[此 zip 文件](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)。</span><span class="sxs-lookup"><span data-stu-id="5dce8-166">Please download [this zip file](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) from the Microsoft Download Center.</span></span>  <span data-ttu-id="5dce8-167">解压缩会生成两个文件。</span><span class="sxs-lookup"><span data-stu-id="5dce8-167">Unzipping will produce two files.</span></span>  <span data-ttu-id="5dce8-168">。 .Appx. .appx. .appx. .appx. .appx. .appx. .appx</span><span class="sxs-lookup"><span data-stu-id="5dce8-168">Microsoft.NET.Native.Runtime.1.7.appx and Microsoft.NET.Native.Framework.1.7.appx</span></span>
2)  <span data-ttu-id="5dce8-169">请验证你的设备是否已进行开发解锁。</span><span class="sxs-lookup"><span data-stu-id="5dce8-169">Please verify that your device is dev unlocked.</span></span>  <span data-ttu-id="5dce8-170">如果尚未执行此操作, 请参阅[此处](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)的说明。</span><span class="sxs-lookup"><span data-stu-id="5dce8-170">If you haven’t done that before the instructions to do that are [here](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).</span></span>
3)  <span data-ttu-id="5dce8-171">然后, 你需要进入 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="5dce8-171">You then want to get into the Windows Device Portal.</span></span>  <span data-ttu-id="5dce8-172">我们的建议是通过 USB 来完成此操作, 可以通过在浏览 http://127.0.0.1:10080 器中键入来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="5dce8-172">Our recommendation is to do this over USB and you would do that by typing http://127.0.0.1:10080 into your browser.</span></span>  
4)  <span data-ttu-id="5dce8-173">完成 Windows 设备门户后, 我们需要你将下载的两个文件 "侧加载"。</span><span class="sxs-lookup"><span data-stu-id="5dce8-173">Once you have the Windows Device Portal up we need you to “side load” the two files that you downloaded.</span></span>  <span data-ttu-id="5dce8-174">若要执行此操作, 需要向下滚动到 "应用" 部分, 并单击 "应用"。</span><span class="sxs-lookup"><span data-stu-id="5dce8-174">To do that you need to go down the left side bar until you get to the “Apps” section and click on “Apps”.</span></span>
5)  <span data-ttu-id="5dce8-175">随后会看到类似于下面的屏幕。</span><span class="sxs-lookup"><span data-stu-id="5dce8-175">You will then see a screen that is similar to the below.</span></span>  <span data-ttu-id="5dce8-176">要转到显示 "安装应用程序" 的部分, 并浏览到解压这两个 APPX 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="5dce8-176">You want to go to the section that says “Install App” and browse to where you unzipped those two APPX files.</span></span>  <span data-ttu-id="5dce8-177">你一次只能执行一个操作, 因此在选择第一个项后, 在 "部署" 部分下单击 "开始"。</span><span class="sxs-lookup"><span data-stu-id="5dce8-177">You can only do one at a time, so after you select the first one, then click on “Go” under the Deploy section.</span></span>  <span data-ttu-id="5dce8-178">然后对第二个 APPX 文件执行此操作。</span><span class="sxs-lookup"><span data-stu-id="5dce8-178">Then do this for the second APPX file.</span></span> 
  <span data-ttu-id="5dce8-179">![用于安装加载端应用的 Windows 设备门户](images/20190322-DevicePortal.png)</span><span class="sxs-lookup"><span data-stu-id="5dce8-179">![Windows Device Portal to Install Side-Loaded app](images/20190322-DevicePortal.png)</span></span><br>
6)  <span data-ttu-id="5dce8-180">此时, 我们相信您的应用程序应再次开始工作, 您也可以访问应用商店。</span><span class="sxs-lookup"><span data-stu-id="5dce8-180">At this point we believe your applications should start working again and that you can also get to the Store.</span></span>
7)  <span data-ttu-id="5dce8-181">在某些情况下, 在启动受影响的应用程序之前, 需要运行额外的步骤来启动3D 查看器应用程序。</span><span class="sxs-lookup"><span data-stu-id="5dce8-181">In some cases, it is necessary run the additional step of launching the 3D Viewer app before affected apps will launch.</span></span> 

<span data-ttu-id="5dce8-182">我们非常感谢你的耐心, 因为我们已经完成了解决此问题的过程, 我们期待继续与我们的社区合作, 以创建成功的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="5dce8-182">We appreciate your patience as we have gone through the process to get this issue resolved, and we look forward to continued working with our community to create successful Mixed Reality experiences.</span></span>

## <a name="connecting-to-wifi"></a><span data-ttu-id="5dce8-183">连接到 WiFi</span><span class="sxs-lookup"><span data-stu-id="5dce8-183">Connecting to WiFi</span></span>

<span data-ttu-id="5dce8-184">在 OOBE & 设置期间, 凭据超时为2分钟。</span><span class="sxs-lookup"><span data-stu-id="5dce8-184">During OOBE & Settings, there is a credential timeout of 2 mins.</span></span> <span data-ttu-id="5dce8-185">用户名/密码需要在2分钟内输入, 否则 "用户名" 字段会自动清除。</span><span class="sxs-lookup"><span data-stu-id="5dce8-185">The username/password needs to be entered within 2 mins otherwise the username field will be automatically cleared.</span></span>

<span data-ttu-id="5dce8-186">建议使用蓝牙键盘输入长密码。</span><span class="sxs-lookup"><span data-stu-id="5dce8-186">We recommend using a Bluetooth keyboard for entering long passwords.</span></span>

## <a name="device-update"></a><span data-ttu-id="5dce8-187">设备更新</span><span class="sxs-lookup"><span data-stu-id="5dce8-187">Device Update</span></span>
* <span data-ttu-id="5dce8-188">30秒后, shell 可能会消失一次。</span><span class="sxs-lookup"><span data-stu-id="5dce8-188">30 seconds after a new update, the shell may disappear one time.</span></span> <span data-ttu-id="5dce8-189">请执行**布隆**手势以恢复会话。</span><span class="sxs-lookup"><span data-stu-id="5dce8-189">Please perform the **bloom** gesture to resume your session.</span></span>

## <a name="visual-studio"></a><span data-ttu-id="5dce8-190">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5dce8-190">Visual Studio</span></span>
* <span data-ttu-id="5dce8-191">请参阅安装适用于 HoloLens 开发的 Visual Studio 的最新版本的[工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5dce8-191">See [Install the tools](install-the-tools.md) for the most up-to-date version of Visual Studio recommended for HoloLens development.</span></span>
* <span data-ttu-id="5dce8-192">在将应用程序从 Visual Studio 部署到 HoloLens 时, 可能会看到以下错误:**无法对已打开用户映射的文件执行所请求的操作。（HRESULT 中的异常：0x800704C8)** 。</span><span class="sxs-lookup"><span data-stu-id="5dce8-192">When deploying an app from Visual Studio to your HoloLens, you may see the error: **The requested operation cannot be performed on a file with a user-mapped section open. (Exception from HRESULT: 0x800704C8)**.</span></span> <span data-ttu-id="5dce8-193">如果发生这种情况, 请重试, 部署通常会成功。</span><span class="sxs-lookup"><span data-stu-id="5dce8-193">If this happens, try again and your deployment will generally succeed.</span></span>

## <a name="emulator"></a><span data-ttu-id="5dce8-194">仿真</span><span class="sxs-lookup"><span data-stu-id="5dce8-194">Emulator</span></span>
* <span data-ttu-id="5dce8-195">并非 Microsoft Store 中的所有应用都与模拟器兼容。</span><span class="sxs-lookup"><span data-stu-id="5dce8-195">Not all apps in the Microsoft Store are compatible with the emulator.</span></span> <span data-ttu-id="5dce8-196">例如, 不能在模拟器上播放年轻人 Conker 和片段。</span><span class="sxs-lookup"><span data-stu-id="5dce8-196">For example, Young Conker and Fragments are not playable on the emulator.</span></span>
* <span data-ttu-id="5dce8-197">无法在仿真程序中使用 PC 网络摄像机。</span><span class="sxs-lookup"><span data-stu-id="5dce8-197">You cannot use the PC webcam in the Emulator.</span></span>
* <span data-ttu-id="5dce8-198">Windows 设备门户的实时预览功能不适用于模拟器。</span><span class="sxs-lookup"><span data-stu-id="5dce8-198">The Live Preview feature of the Windows Device Portal does not work with the emulator.</span></span> <span data-ttu-id="5dce8-199">你仍可以捕获混合现实视频和图像。</span><span class="sxs-lookup"><span data-stu-id="5dce8-199">You can still capture Mixed Reality videos and images.</span></span>

## <a name="unity"></a><span data-ttu-id="5dce8-200">Unity</span><span class="sxs-lookup"><span data-stu-id="5dce8-200">Unity</span></span>
* <span data-ttu-id="5dce8-201">请参阅安装适用于 HoloLens 开发的最新 Unity 版本的[工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5dce8-201">See [Install the tools](install-the-tools.md) for the most up-to-date version of Unity recommended for HoloLens development.</span></span>
* <span data-ttu-id="5dce8-202">[Hololens unity 论坛](http://forum.unity3d.com/threads/known-issues.394627/)中介绍了 Unity Hololens Technical Preview 的已知问题。</span><span class="sxs-lookup"><span data-stu-id="5dce8-202">Known issues with the Unity HoloLens Technical Preview are documented in the [HoloLens Unity forums](http://forum.unity3d.com/threads/known-issues.394627/).</span></span>

## <a name="windows-device-portal"></a><span data-ttu-id="5dce8-203">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="5dce8-203">Windows Device Portal</span></span>
* <span data-ttu-id="5dce8-204">混合现实捕获中的实时预览功能可能会出现几秒钟的延迟。</span><span class="sxs-lookup"><span data-stu-id="5dce8-204">The Live Preview feature in Mixed Reality capture may exhibit several seconds of latency.</span></span>
* <span data-ttu-id="5dce8-205">在 "虚拟输入" 页上, "虚拟手势" 部分下的手势和滚动控件不起作用。</span><span class="sxs-lookup"><span data-stu-id="5dce8-205">On the Virtual Input page, the Gesture and Scroll controls under the Virtual Gestures section are not functional.</span></span> <span data-ttu-id="5dce8-206">使用它们将不起作用。</span><span class="sxs-lookup"><span data-stu-id="5dce8-206">Using them will have no effect.</span></span> <span data-ttu-id="5dce8-207">同一页面上的虚拟键盘工作正常。</span><span class="sxs-lookup"><span data-stu-id="5dce8-207">The virtual keyboard on the same page works correctly.</span></span>
* <span data-ttu-id="5dce8-208">在设置中启用 "开发人员模式" 后, 可能需要几秒钟才能打开设备门户。</span><span class="sxs-lookup"><span data-stu-id="5dce8-208">After enabling Developer Mode in Settings, it may take a few seconds before the switch to turn on the Device Portal is enabled.</span></span>

## <a name="api"></a><span data-ttu-id="5dce8-209">API</span><span class="sxs-lookup"><span data-stu-id="5dce8-209">API</span></span>
* <span data-ttu-id="5dce8-210">如果应用程序将[焦点](focus-point-in-unity.md)置于用户后面或 "正常" 设置为 "摄像", 则全息体将不会在混合现实捕获照片或视频中出现。</span><span class="sxs-lookup"><span data-stu-id="5dce8-210">If the application sets the [focus point](focus-point-in-unity.md) behind the user or the normal to camera.forward, holograms will not appear in Mixed Reality Capture photos or videos.</span></span> <span data-ttu-id="5dce8-211">在 Windows 中修复此 bug 之前, 如果应用程序主动设置了[焦点](focus-point-in-unity.md), 则这些应用程序应确保将平面法线设置为相对相机前进 (例如 normal =-摄像)。</span><span class="sxs-lookup"><span data-stu-id="5dce8-211">Until this bug is fixed in Windows, if applications actively set the [focus point](focus-point-in-unity.md) they should ensure the plane normal is set opposite camera-forward (e.g. normal = -camera.forward).</span></span>

## <a name="xbox-wireless-controller"></a><span data-ttu-id="5dce8-212">Xbox 无线控制器</span><span class="sxs-lookup"><span data-stu-id="5dce8-212">Xbox Wireless Controller</span></span>
* <span data-ttu-id="5dce8-213">必须先更新 Xbox 无线控制器, 然后才能将其与 HoloLens 配合使用。</span><span class="sxs-lookup"><span data-stu-id="5dce8-213">Xbox Wireless Controller S must be updated before it can be used with HoloLens.</span></span> <span data-ttu-id="5dce8-214">请确保在尝试将控制器与 HoloLens 配对之前处于[最新状态](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)。</span><span class="sxs-lookup"><span data-stu-id="5dce8-214">Ensure you are [up to date](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) before attempting to pair your controller with a HoloLens.</span></span>
* <span data-ttu-id="5dce8-215">如果在连接 Xbox 无线控制器时重新启动 HoloLens, 控制器将不会自动重新连接到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5dce8-215">If you reboot your HoloLens while the Xbox Wireless Controller is connected, the controller will not automatically reconnect to HoloLens.</span></span> <span data-ttu-id="5dce8-216">在3分钟后控制器关闭之前, "指南" 按钮指示灯会慢慢闪烁。</span><span class="sxs-lookup"><span data-stu-id="5dce8-216">The Guide button light will flash slowly until the controller powers off after 3 minutes.</span></span> <span data-ttu-id="5dce8-217">若要立即重新连接控制器, 请关闭控制器电源, 方法是按住 "指南" 按钮, 直到指示灯亮起。</span><span class="sxs-lookup"><span data-stu-id="5dce8-217">To reconnect your controller immediately, power off the controller by holding the Guide button until the light turns off.</span></span> <span data-ttu-id="5dce8-218">再次打开控制器时, 它将重新连接到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5dce8-218">When you power your controller on again, it will reconnect to HoloLens.</span></span>
* <span data-ttu-id="5dce8-219">如果在连接 Xbox 无线控制器时, HoloLens 进入待机状态, 则控制器上的任何输入都将唤醒 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5dce8-219">If your HoloLens enters standby while the Xbox Wireless Controller is connected, any input on the controller will wake the HoloLens.</span></span> <span data-ttu-id="5dce8-220">使用完控制器后, 可以通过关闭控制器来阻止此操作。</span><span class="sxs-lookup"><span data-stu-id="5dce8-220">You can prevent this by powering off your controller when you are done using it.</span></span>
