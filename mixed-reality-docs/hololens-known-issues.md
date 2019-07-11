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
# <a name="hololens-known-issues"></a><span data-ttu-id="531c2-104">HoloLens 的已知问题</span><span class="sxs-lookup"><span data-stu-id="531c2-104">HoloLens known issues</span></span>

<span data-ttu-id="531c2-105">这是面向 HoloLens 影响开发人员的已知问题的当前列表。</span><span class="sxs-lookup"><span data-stu-id="531c2-105">This is the current list of known issues for HoloLens affecting developers.</span></span> <span data-ttu-id="531c2-106">首先请查看此处如果看到异常行为。</span><span class="sxs-lookup"><span data-stu-id="531c2-106">Check here first if you are seeing an odd behavior.</span></span> <span data-ttu-id="531c2-107">随着新问题的发现或报告，或在将来的 HoloLens 软件更新中解决问题的方式都将保留此列表已更新。</span><span class="sxs-lookup"><span data-stu-id="531c2-107">This list will be kept updated as new issues are discovered or reported, or as issues are addressed in future HoloLens software updates.</span></span>

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a><span data-ttu-id="531c2-108">无法连接并将其部署到 HoloLens 通过 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="531c2-108">Unable to connect and deploy to HoloLens through Visual Studio</span></span>

>[!NOTE]
><span data-ttu-id="531c2-109">上次更新时间：7/8 @ 7:25 PM-团队已确定根本原因，目前正在修复上。</span><span class="sxs-lookup"><span data-stu-id="531c2-109">Last Update: 7/8 @ 7:25PM - The team has identified the root cause and is currently working on fix.</span></span> <span data-ttu-id="531c2-110">以下可用的解决方法。</span><span class="sxs-lookup"><span data-stu-id="531c2-110">Workaround available below.</span></span> 

<span data-ttu-id="531c2-111">我们都能发现此问题的根本原因。</span><span class="sxs-lookup"><span data-stu-id="531c2-111">We were able to identify the root cause of this issue.</span></span> <span data-ttu-id="531c2-112">使用 Visual Studio 2015 或 Visual Studio 2017 的早期版本来部署和调试其 HoloLens 上的应用程序，然后使用相同的 HoloLens 随后使用最新版本的 Visual Studio 2017 或 Visual Studio 2019 的用户将会受到影响。</span><span class="sxs-lookup"><span data-stu-id="531c2-112">Users who used Visual Studio 2015 or early releases of Visual Studio 2017 to deploy and debug applications on their HoloLens and then subsequently used the latest versions of Visual Studio 2017 or Visual Studio 2019 with the same HoloLens will be affected.</span></span> 

<span data-ttu-id="531c2-113">较新版本的 Visual Studio 部署新版本的组件，但从较旧版本的文件中留下导致失败的较新版本的设备上。</span><span class="sxs-lookup"><span data-stu-id="531c2-113">The newer releases of Visual Studio deploy a new version of a component, but files from the older version are left over on the device, causing the newer version to fail.</span></span>  <span data-ttu-id="531c2-114">这将导致以下错误消息：DEP0100:请确保目标设备已启用的开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="531c2-114">This causes the following error message: DEP0100: Please ensure that target device has developer mode enabled.</span></span> <span data-ttu-id="531c2-115">无法获取开发人员许可证上<ip>由于错误 80004005。</span><span class="sxs-lookup"><span data-stu-id="531c2-115">Could not obtain a developer license on <ip> due to error 80004005.</span></span>
 
<span data-ttu-id="531c2-116">**解决方法**：</span><span class="sxs-lookup"><span data-stu-id="531c2-116">**Workaround**:</span></span> 

<span data-ttu-id="531c2-117">我们的团队目前正在从事一个修复。</span><span class="sxs-lookup"><span data-stu-id="531c2-117">Our team is currently working on a fix.</span></span> <span data-ttu-id="531c2-118">在此期间，可以使用以下步骤来解决此问题并帮助解除阻止部署和调试：</span><span class="sxs-lookup"><span data-stu-id="531c2-118">In the meantime, you can use the following steps to work around the issue and help unblock deployment and debugging:</span></span>  
1. <span data-ttu-id="531c2-119">打开 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="531c2-119">Open Visual Studio</span></span>
2. <span data-ttu-id="531c2-120">文件-> 新建-> 项目</span><span class="sxs-lookup"><span data-stu-id="531c2-120">File -> New -> Project</span></span>
3. <span data-ttu-id="531c2-121">Visual C# -> Windows 桌面-> 控制台应用 (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="531c2-121">Visual C# -> Windows Desktop -> Console App (.NET Framework)</span></span>
4. <span data-ttu-id="531c2-122">为项目提供名称 (例如 HoloLensDeploymentFix)，并确保框架至少设置为.NET Framework 4.5，然后单击确定。</span><span class="sxs-lookup"><span data-stu-id="531c2-122">Give the project a name (e.g. HoloLensDeploymentFix) and make sure the Framework is set to at least .NET Framework 4.5 then click OK.</span></span>
5. <span data-ttu-id="531c2-123">右键单击解决方案资源管理器中的引用节点，然后添加以下引用 （单击浏览部分，单击浏览...按钮）：</span><span class="sxs-lookup"><span data-stu-id="531c2-123">Right-click on the References node in Solution Explorer and add the following references (click to the 'Browse' section and click the 'Browse...' button):</span></span>
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    ><span data-ttu-id="531c2-124">如果没有安装 10.0.18362.0，使用你拥有的最新版本。</span><span class="sxs-lookup"><span data-stu-id="531c2-124">If you don't have 10.0.18362.0 installed, use the most recent version that you have.</span></span>
 
6. <span data-ttu-id="531c2-125">右键单击解决方案资源管理器中的项目，然后选择添加-> 现有项。</span><span class="sxs-lookup"><span data-stu-id="531c2-125">Right-click on the project in Solution Explorer and choose Add -> Existing Item.</span></span>
 
7. <span data-ttu-id="531c2-126">浏览到 C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86 并更改到筛选器"的所有文件 (\*。\*)"</span><span class="sxs-lookup"><span data-stu-id="531c2-126">Browse to C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86 and change the filter to "All Files (\*.\*)"</span></span>
 
8. <span data-ttu-id="531c2-127">选择 SirepClient.dll 和 SshClient.dll 并单击"添加"。</span><span class="sxs-lookup"><span data-stu-id="531c2-127">Select both SirepClient.dll and SshClient.dll and click "Add".</span></span>
 
9. <span data-ttu-id="531c2-128">找到并选择这两个文件在解决方案资源管理器 （它们应位于的文件列表的底部） 并将"复制到输出目录"中属性窗口更改为"始终复制"</span><span class="sxs-lookup"><span data-stu-id="531c2-128">Locate and select both files in Solution Explorer (they should be at the bottom of the list of files) and change "Copy to Output Directory" in the Properties window to "Copy always"</span></span>
 
10. <span data-ttu-id="531c2-129">在文件的顶部，以下代码添加到现有列表的 using 语句：</span><span class="sxs-lookup"><span data-stu-id="531c2-129">At the top of the file, add the following to the existing list of 'using' statements:</span></span> 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. <span data-ttu-id="531c2-130">在"静态 void Main(...)"，添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="531c2-130">Inside of “static void Main(...)”, add the following code:</span></span>
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. <span data-ttu-id="531c2-131">生成-> 生成解决方案</span><span class="sxs-lookup"><span data-stu-id="531c2-131">Build -> Build Solution</span></span>
 
13. <span data-ttu-id="531c2-132">打开命令提示符向包含已编译的.exe (例如 C:\MyProjects\HoloLensDeploymentFix\bin\Debug) 的文件夹</span><span class="sxs-lookup"><span data-stu-id="531c2-132">Open a command prompt to the folder that contains the compiled .exe (e.g. C:\MyProjects\HoloLensDeploymentFix\bin\Debug)</span></span>
 
14. <span data-ttu-id="531c2-133">运行可执行文件并提供设备的 IP 地址作为命令行参数。</span><span class="sxs-lookup"><span data-stu-id="531c2-133">Run the executable and provide the device's IP address as a command-line argument.</span></span>  <span data-ttu-id="531c2-134">（如果通过 USB 连接，您可以使用 127.0.0.1，否则，请使用设备的 WiFi IP 地址。）例如，"HoloLensDeploymentFix 127.0.0.1"</span><span class="sxs-lookup"><span data-stu-id="531c2-134">(If connected via USB, you can use 127.0.0.1, otherwise use the device’s WiFi IP address.)  For example, "HoloLensDeploymentFix 127.0.0.1"</span></span>
 
15. <span data-ttu-id="531c2-135">一旦该工具已退出并且没有任何消息 （这应只需几秒钟），您现在将能够部署和调试从 Visual Studio 2017 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="531c2-135">Once the tool has exited without any messages (this should only take a few seconds), you will now be able to deploy and debug from Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="531c2-136">继续的使用该工具不是必需的。</span><span class="sxs-lookup"><span data-stu-id="531c2-136">Continued use of the tool is not necessary.</span></span>

<span data-ttu-id="531c2-137">我们将提供进一步更新可用时。</span><span class="sxs-lookup"><span data-stu-id="531c2-137">We will provide further updates as they become available.</span></span>

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a><span data-ttu-id="531c2-138">启动的 Microsoft Store 和 HoloLens 上的应用程序的问题</span><span class="sxs-lookup"><span data-stu-id="531c2-138">Issues launching the Microsoft Store and apps on HoloLens</span></span>

>[!NOTE]
><span data-ttu-id="531c2-139">上次更新时间：4/2 @ 上午 10 点-解决问题。</span><span class="sxs-lookup"><span data-stu-id="531c2-139">Last Update: 4/2 @ 10 AM - Issue resolved.</span></span> 

<span data-ttu-id="531c2-140">尝试启动的 Microsoft Store 和 HoloLens 上的应用程序时，可能会遇到问题。</span><span class="sxs-lookup"><span data-stu-id="531c2-140">You may experience issues when trying to launch the Microsoft Store and apps on HoloLens.</span></span> <span data-ttu-id="531c2-141">我们已确定后台应用程序更新部署时一个特定序列中的框架包的较新版本或多个其依赖的应用程序仍在运行时，会出现此问题。</span><span class="sxs-lookup"><span data-stu-id="531c2-141">We've determined that the issue occurs when background app updates deploy a newer version of framework packages in specific sequences while one or more of their dependent apps are still running.</span></span> <span data-ttu-id="531c2-142">在这种情况下，自动应用更新提供新版本的.NET 本机框架 （版本 10.0.25531 到 10.0.27413） 引起的不正确的所有正在运行的应用使用以前版本的 framework 的更新运行的应用。</span><span class="sxs-lookup"><span data-stu-id="531c2-142">In this case,  an automatic app update delivered a new version of the .NET Native Framework (version 10.0.25531 to 10.0.27413) caused the apps that are running to not correctly update for all running apps consuming the prior version of the framework.</span></span>  <span data-ttu-id="531c2-143">Framework 更新流程如下所示:-</span><span class="sxs-lookup"><span data-stu-id="531c2-143">The flow for framework update is as follows: -</span></span>

1.  <span data-ttu-id="531c2-144">从应用商店下载并安装新的 framework 包</span><span class="sxs-lookup"><span data-stu-id="531c2-144">The new framework package is downloaded from the store and installed</span></span>
2.  <span data-ttu-id="531c2-145">使用较旧框架的所有应用都更新以使用较新版本</span><span class="sxs-lookup"><span data-stu-id="531c2-145">All apps using the older framework are ‘updated’ to use the newer version</span></span>

<span data-ttu-id="531c2-146">如果在完成之前中断步骤 2 然后为其注册的更新的框架不是任何应用将无法从开始菜单中启动。</span><span class="sxs-lookup"><span data-stu-id="531c2-146">If step 2 is interrupted before completion then any apps for which the newer framework wasn’t registered will fail to launch from the start menu.</span></span>  <span data-ttu-id="531c2-147">我们认为此问题可能会影响在 HoloLens 上的任何应用。</span><span class="sxs-lookup"><span data-stu-id="531c2-147">We believe any app on HoloLens could be affected by this issue.</span></span>

<span data-ttu-id="531c2-148">一些用户的已报告，关闭挂起的应用程序并启动其他应用如反馈中心，3D 查看器或照片解决了问题为它们-但是，这不起作用 100%的时间。</span><span class="sxs-lookup"><span data-stu-id="531c2-148">Some users have reported that closing hung apps and launching other apps such as Feedback Hub, 3D Viewer or Photos resolves the issue for them - however, this does not work 100% of the time.</span></span>

<span data-ttu-id="531c2-149">我们具有根导致此问题不导致更新本身，但一个 bug 导致.NET Native 处理不正确的 framework 更新在 OS 中的。</span><span class="sxs-lookup"><span data-stu-id="531c2-149">We have root caused that this issue was not caused the update itself, but a bug in the OS that resulted in the .NET Native framework update being handled incorrectly.</span></span> <span data-ttu-id="531c2-150">我们很高兴地宣布我们确定了修补程序，并且已发布的更新 (OS 版本 17763.380) 包含此修补程序。</span><span class="sxs-lookup"><span data-stu-id="531c2-150">We are pleased to announce that we have identified a fix and have released an update (OS version 17763.380) containing the fix.</span></span> 

<span data-ttu-id="531c2-151">若要查看你的设备是否可能请需要更新：</span><span class="sxs-lookup"><span data-stu-id="531c2-151">To see if your device can take the update please:</span></span>

1.  <span data-ttu-id="531c2-152">转到"设置"应用并打开"更新和安全"</span><span class="sxs-lookup"><span data-stu-id="531c2-152">Go to the “Settings” app and open “Update & Security”</span></span>
2.  <span data-ttu-id="531c2-153">单击"检查更新"</span><span class="sxs-lookup"><span data-stu-id="531c2-153">Click “Check for Updates”</span></span>
3.  <span data-ttu-id="531c2-154">如果提供了 17763.380 更新，请更新到此版本，以接收应用程序挂起 bug 的修复程序</span><span class="sxs-lookup"><span data-stu-id="531c2-154">If update to 17763.380 is available, please update to this build to receive the fix for the App Hang bug</span></span>
4.  <span data-ttu-id="531c2-155">在更新到此版本的操作系统时，应用应按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="531c2-155">Upon updating to this version of the OS, the Apps should work as expected.</span></span>

<span data-ttu-id="531c2-156">此外，我们使用每个 HoloLens OS 版本执行的操作，因为我们已发布 FFU 映像到从 Microsoft 下载中心获得 https://aka.ms/hololensdownload/10.0.17763.380 。</span><span class="sxs-lookup"><span data-stu-id="531c2-156">Additionally, as we do with every HoloLens OS release, we have posted the FFU image to the Microsoft Download Center at https://aka.ms/hololensdownload/10.0.17763.380.</span></span> 

<span data-ttu-id="531c2-157">如果不想要执行更新，我们发布了截至 3/29 的 Microsoft Store UWP 应用的新版本。</span><span class="sxs-lookup"><span data-stu-id="531c2-157">If you would not like to take the update, we have released a new version of the Microsoft Store UWP app as of 3/29.</span></span> <span data-ttu-id="531c2-158">一旦有更新的版本的存储：</span><span class="sxs-lookup"><span data-stu-id="531c2-158">Once you have the updated version of the Store:</span></span>

1) <span data-ttu-id="531c2-159">打开存储区并确认它在加载时。</span><span class="sxs-lookup"><span data-stu-id="531c2-159">Open the Store and confirm that it loads.</span></span>
2) <span data-ttu-id="531c2-160">布隆手势用于打开的菜单。</span><span class="sxs-lookup"><span data-stu-id="531c2-160">Use the Bloom Gesture to open the menu.</span></span>
3) <span data-ttu-id="531c2-161">尝试打开应用程序以前损坏</span><span class="sxs-lookup"><span data-stu-id="531c2-161">Attempt to open previously broken apps</span></span>
3) <span data-ttu-id="531c2-162">如果仍无法启动，点击并按住中断应用程序的图标并选择卸载。</span><span class="sxs-lookup"><span data-stu-id="531c2-162">If it still cannot be launched, tap and hold the icon of the broken app and select uninstall.</span></span>
4) <span data-ttu-id="531c2-163">Resinstall 这些应用商店中的。</span><span class="sxs-lookup"><span data-stu-id="531c2-163">Resinstall these apps from the store.</span></span>

<span data-ttu-id="531c2-164">如果你的设备仍无法加载应用，你通过这样做可以旁加载版本的.NET 本机框架和运行时通过从下载中心获得：</span><span class="sxs-lookup"><span data-stu-id="531c2-164">If your device is still unable to load apps, you can sideload a version of the .NET Native Framework and Runtime through the download center by doing:</span></span>

1)  <span data-ttu-id="531c2-165">请下载[此 zip 文件](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip)从 Microsoft 下载中心获得。</span><span class="sxs-lookup"><span data-stu-id="531c2-165">Please download [this zip file](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) from the Microsoft Download Center.</span></span>  <span data-ttu-id="531c2-166">解压缩将生成两个文件。</span><span class="sxs-lookup"><span data-stu-id="531c2-166">Unzipping will produce two files.</span></span>  <span data-ttu-id="531c2-167">Microsoft.NET.Native.Runtime.1.7.appx 和 Microsoft.NET.Native.Framework.1.7.appx</span><span class="sxs-lookup"><span data-stu-id="531c2-167">Microsoft.NET.Native.Runtime.1.7.appx and Microsoft.NET.Native.Framework.1.7.appx</span></span>
2)  <span data-ttu-id="531c2-168">请验证你的设备适用于开发人员解锁。</span><span class="sxs-lookup"><span data-stu-id="531c2-168">Please verify that your device is dev unlocked.</span></span>  <span data-ttu-id="531c2-169">如果您没有这样做之前执行此操作的说明[此处](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)。</span><span class="sxs-lookup"><span data-stu-id="531c2-169">If you haven’t done that before the instructions to do that are [here](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).</span></span>
3)  <span data-ttu-id="531c2-170">随后想要将导入 Windows Device Portal。</span><span class="sxs-lookup"><span data-stu-id="531c2-170">You then want to get into the Windows Device Portal.</span></span>  <span data-ttu-id="531c2-171">建议在执行此操作通过 USB 和将会通过键入 http://127.0.0.1:10080 到浏览器。</span><span class="sxs-lookup"><span data-stu-id="531c2-171">Our recommendation is to do this over USB and you would do that by typing http://127.0.0.1:10080 into your browser.</span></span>  
4)  <span data-ttu-id="531c2-172">Windows Device Portal 了我们需要你为"端加载"后的两个文件下载的。</span><span class="sxs-lookup"><span data-stu-id="531c2-172">Once you have the Windows Device Portal up we need you to “side load” the two files that you downloaded.</span></span>  <span data-ttu-id="531c2-173">若要执行此操作，需要停机的左侧和右侧栏，直到转到"应用"部分并单击"应用"。</span><span class="sxs-lookup"><span data-stu-id="531c2-173">To do that you need to go down the left side bar until you get to the “Apps” section and click on “Apps”.</span></span>
5)  <span data-ttu-id="531c2-174">然后，您将看到一个屏幕，类似于下面。</span><span class="sxs-lookup"><span data-stu-id="531c2-174">You will then see a screen that is similar to the below.</span></span>  <span data-ttu-id="531c2-175">你想要转到显示"安装应用"部分，并浏览到你在其中解压缩这两个 APPX 文件。</span><span class="sxs-lookup"><span data-stu-id="531c2-175">You want to go to the section that says “Install App” and browse to where you unzipped those two APPX files.</span></span>  <span data-ttu-id="531c2-176">可以仅执行一次一个地操作，因此后选择第一个，然后单击"转到"下的部署部分。</span><span class="sxs-lookup"><span data-stu-id="531c2-176">You can only do one at a time, so after you select the first one, then click on “Go” under the Deploy section.</span></span>  <span data-ttu-id="531c2-177">然后执行此操作的第二个 APPX 文件。</span><span class="sxs-lookup"><span data-stu-id="531c2-177">Then do this for the second APPX file.</span></span> 
  <span data-ttu-id="531c2-178">![Windows Device Portal 安装旁加载的应用](images/20190322-DevicePortal.png)</span><span class="sxs-lookup"><span data-stu-id="531c2-178">![Windows Device Portal to Install Side-Loaded app](images/20190322-DevicePortal.png)</span></span><br>
6)  <span data-ttu-id="531c2-179">此时我们认为您的应用程序应会再次开始工作，您还可以获取对应用商店。</span><span class="sxs-lookup"><span data-stu-id="531c2-179">At this point we believe your applications should start working again and that you can also get to the Store.</span></span>
7)  <span data-ttu-id="531c2-180">在某些情况下，有必要运行受影响的应用将启动之前启动 3D 的查看器应用额外的步骤。</span><span class="sxs-lookup"><span data-stu-id="531c2-180">In some cases, it is necessary run the additional step of launching the 3D Viewer app before affected apps will launch.</span></span> 

<span data-ttu-id="531c2-181">我们非常感谢你的耐心等待，因为我们已进行解决，此问题的过程，并希望继续使用我们的社区创建成功的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="531c2-181">We appreciate your patience as we have gone through the process to get this issue resolved, and we look forward to continued working with our community to create successful Mixed Reality experiences.</span></span>

## <a name="connecting-to-wifi"></a><span data-ttu-id="531c2-182">连接到 WiFi</span><span class="sxs-lookup"><span data-stu-id="531c2-182">Connecting to WiFi</span></span>

<span data-ttu-id="531c2-183">OOBE 设置 （&），在没有凭据超时为 2 分钟。</span><span class="sxs-lookup"><span data-stu-id="531c2-183">During OOBE & Settings, there is a credential timeout of 2 mins.</span></span> <span data-ttu-id="531c2-184">需要在 2 分钟否则为会自动清除用户名字段中输入用户名/密码。</span><span class="sxs-lookup"><span data-stu-id="531c2-184">The username/password needs to be entered within 2 mins otherwise the username field will be automatically cleared.</span></span>

<span data-ttu-id="531c2-185">我们建议使用蓝牙键盘来输入长密码。</span><span class="sxs-lookup"><span data-stu-id="531c2-185">We recommend using a Bluetooth keyboard for entering long passwords.</span></span>

## <a name="device-update"></a><span data-ttu-id="531c2-186">设备更新</span><span class="sxs-lookup"><span data-stu-id="531c2-186">Device Update</span></span>
* <span data-ttu-id="531c2-187">在新的更新后的 30 秒 shell 可能消失，一次。</span><span class="sxs-lookup"><span data-stu-id="531c2-187">30 seconds after a new update, the shell may disappear one time.</span></span> <span data-ttu-id="531c2-188">请执行**布隆**手势来恢复您的会话。</span><span class="sxs-lookup"><span data-stu-id="531c2-188">Please perform the **bloom** gesture to resume your session.</span></span>

## <a name="visual-studio"></a><span data-ttu-id="531c2-189">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="531c2-189">Visual Studio</span></span>
* <span data-ttu-id="531c2-190">请参阅[安装的工具](install-the-tools.md)建议 HoloLens 开发的 Visual Studio 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="531c2-190">See [Install the tools](install-the-tools.md) for the most up-to-date version of Visual Studio recommended for HoloLens development.</span></span>
* <span data-ttu-id="531c2-191">部署到你 HoloLens 从 Visual Studio 应用程序，可能会看到错误：**不能在具有用户映射部分打开的文件上执行请求的操作。（HRESULT 中的异常：0x800704C8)** 。</span><span class="sxs-lookup"><span data-stu-id="531c2-191">When deploying an app from Visual Studio to your HoloLens, you may see the error: **The requested operation cannot be performed on a file with a user-mapped section open. (Exception from HRESULT: 0x800704C8)**.</span></span> <span data-ttu-id="531c2-192">如果发生这种情况，重试，而你的部署通常会成功。</span><span class="sxs-lookup"><span data-stu-id="531c2-192">If this happens, try again and your deployment will generally succeed.</span></span>

## <a name="emulator"></a><span data-ttu-id="531c2-193">仿真程序</span><span class="sxs-lookup"><span data-stu-id="531c2-193">Emulator</span></span>
* <span data-ttu-id="531c2-194">在 Microsoft Store 中的并非所有应用都都在仿真程序与兼容。</span><span class="sxs-lookup"><span data-stu-id="531c2-194">Not all apps in the Microsoft Store are compatible with the emulator.</span></span> <span data-ttu-id="531c2-195">例如，Young Conker 和片段不是在模拟器上播放。</span><span class="sxs-lookup"><span data-stu-id="531c2-195">For example, Young Conker and Fragments are not playable on the emulator.</span></span>
* <span data-ttu-id="531c2-196">无法在仿真程序中使用的 PC 是网络摄像头。</span><span class="sxs-lookup"><span data-stu-id="531c2-196">You cannot use the PC webcam in the Emulator.</span></span>
* <span data-ttu-id="531c2-197">Windows Device Portal 的实时预览功能并不适用于仿真程序。</span><span class="sxs-lookup"><span data-stu-id="531c2-197">The Live Preview feature of the Windows Device Portal does not work with the emulator.</span></span> <span data-ttu-id="531c2-198">你仍然可以捕获混合现实视频和图像。</span><span class="sxs-lookup"><span data-stu-id="531c2-198">You can still capture Mixed Reality videos and images.</span></span>

## <a name="unity"></a><span data-ttu-id="531c2-199">Unity</span><span class="sxs-lookup"><span data-stu-id="531c2-199">Unity</span></span>
* <span data-ttu-id="531c2-200">请参阅[安装的工具](install-the-tools.md)Unity 建议 HoloLens 开发的最新版本。</span><span class="sxs-lookup"><span data-stu-id="531c2-200">See [Install the tools](install-the-tools.md) for the most up-to-date version of Unity recommended for HoloLens development.</span></span>
* <span data-ttu-id="531c2-201">中介绍了 Unity HoloLens Technical Preview 的已知的问题[HoloLens Unity 论坛](http://forum.unity3d.com/threads/known-issues.394627/)。</span><span class="sxs-lookup"><span data-stu-id="531c2-201">Known issues with the Unity HoloLens Technical Preview are documented in the [HoloLens Unity forums](http://forum.unity3d.com/threads/known-issues.394627/).</span></span>

## <a name="windows-device-portal"></a><span data-ttu-id="531c2-202">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="531c2-202">Windows Device Portal</span></span>
* <span data-ttu-id="531c2-203">混合现实捕获中的实时预览功能可能会出现几秒钟的延迟。</span><span class="sxs-lookup"><span data-stu-id="531c2-203">The Live Preview feature in Mixed Reality capture may exhibit several seconds of latency.</span></span>
* <span data-ttu-id="531c2-204">在虚拟输入页上，虚拟手势部分下的手势和滚动控件不起作用。</span><span class="sxs-lookup"><span data-stu-id="531c2-204">On the Virtual Input page, the Gesture and Scroll controls under the Virtual Gestures section are not functional.</span></span> <span data-ttu-id="531c2-205">使用它们会产生任何影响。</span><span class="sxs-lookup"><span data-stu-id="531c2-205">Using them will have no effect.</span></span> <span data-ttu-id="531c2-206">在同一页上的虚拟键盘正常工作。</span><span class="sxs-lookup"><span data-stu-id="531c2-206">The virtual keyboard on the same page works correctly.</span></span>
* <span data-ttu-id="531c2-207">在启用之后设置中的开发人员模式下，可能需要几秒钟才会启用开关后，若要打开设备门户。</span><span class="sxs-lookup"><span data-stu-id="531c2-207">After enabling Developer Mode in Settings, it may take a few seconds before the switch to turn on the Device Portal is enabled.</span></span>

## <a name="api"></a><span data-ttu-id="531c2-208">API</span><span class="sxs-lookup"><span data-stu-id="531c2-208">API</span></span>
* <span data-ttu-id="531c2-209">如果应用程序设置[关注点](focus-point-in-unity.md)用户或垂直于 camera.forward，后面全息不会出现在混合现实捕获照片或视频。</span><span class="sxs-lookup"><span data-stu-id="531c2-209">If the application sets the [focus point](focus-point-in-unity.md) behind the user or the normal to camera.forward, holograms will not appear in Mixed Reality Capture photos or videos.</span></span> <span data-ttu-id="531c2-210">如果应用程序正在设置，修复此 bug 后使用的 Windows，直到[关注点](focus-point-in-unity.md)它们应确保平面正常设置相反的照相机正向 (例如正常 =-camera.forward)。</span><span class="sxs-lookup"><span data-stu-id="531c2-210">Until this bug is fixed in Windows, if applications actively set the [focus point](focus-point-in-unity.md) they should ensure the plane normal is set opposite camera-forward (e.g. normal = -camera.forward).</span></span>

## <a name="xbox-wireless-controller"></a><span data-ttu-id="531c2-211">Xbox 无线控制器</span><span class="sxs-lookup"><span data-stu-id="531c2-211">Xbox Wireless Controller</span></span>
* <span data-ttu-id="531c2-212">Xbox 无线控制器 S 之前必须先更新用于 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="531c2-212">Xbox Wireless Controller S must be updated before it can be used with HoloLens.</span></span> <span data-ttu-id="531c2-213">确保您[最新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)然后再尝试对你的控制器与 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="531c2-213">Ensure you are [up to date](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) before attempting to pair your controller with a HoloLens.</span></span>
* <span data-ttu-id="531c2-214">如果 Xbox 无线控制器连接时重新启动你 HoloLens，控制器将不会自动重新连接到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="531c2-214">If you reboot your HoloLens while the Xbox Wireless Controller is connected, the controller will not automatically reconnect to HoloLens.</span></span> <span data-ttu-id="531c2-215">指南按钮灯将闪烁缓慢直到控制器关闭后 3 分钟。</span><span class="sxs-lookup"><span data-stu-id="531c2-215">The Guide button light will flash slowly until the controller powers off after 3 minutes.</span></span> <span data-ttu-id="531c2-216">若要重新连接你的控制器立即，通过保留指南按钮，直到指示灯会关闭控制器关闭电源。</span><span class="sxs-lookup"><span data-stu-id="531c2-216">To reconnect your controller immediately, power off the controller by holding the Guide button until the light turns off.</span></span> <span data-ttu-id="531c2-217">当你开启你的控制器再次时，它将重新连接到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="531c2-217">When you power your controller on again, it will reconnect to HoloLens.</span></span>
* <span data-ttu-id="531c2-218">如果你 HoloLens 进入待机 Xbox 无线控制器连接时，在控制器上的任何输入将唤醒 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="531c2-218">If your HoloLens enters standby while the Xbox Wireless Controller is connected, any input on the controller will wake the HoloLens.</span></span> <span data-ttu-id="531c2-219">您可以禁止此行为通过关闭你的控制器，完成后使用它。</span><span class="sxs-lookup"><span data-stu-id="531c2-219">You can prevent this by powering off your controller when you are done using it.</span></span>
