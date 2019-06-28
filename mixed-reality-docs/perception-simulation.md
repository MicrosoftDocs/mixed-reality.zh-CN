---
title: Perception 模拟
description: 如何使用 Perception 模拟库来自动执行模拟的输入的沉浸式应用程序的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens，模拟，测试
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414534"
---
# <a name="perception-simulation"></a><span data-ttu-id="ea55a-104">Perception 模拟</span><span class="sxs-lookup"><span data-stu-id="ea55a-104">Perception simulation</span></span>

<span data-ttu-id="ea55a-105">若要生成你的应用的自动的测试吗？</span><span class="sxs-lookup"><span data-stu-id="ea55a-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="ea55a-106">超越组件级的单元测试和实际练习你的应用程序端到端测试吗？</span><span class="sxs-lookup"><span data-stu-id="ea55a-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="ea55a-107">Perception 模拟是要查找的内容。</span><span class="sxs-lookup"><span data-stu-id="ea55a-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="ea55a-108">Perception 模拟库将发送人和世界输入到您的应用程序的数据，这样可以自动执行测试。</span><span class="sxs-lookup"><span data-stu-id="ea55a-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="ea55a-109">例如，可以模拟人类查找到特定的可重复的位置，然后执行一个手势或使用运动控制器的输入。</span><span class="sxs-lookup"><span data-stu-id="ea55a-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="ea55a-110">Perception 模拟可以将此类模拟的输入发送到物理 HoloLens，HoloLens 仿真程序 （第 1 代） HoloLens 2 个仿真程序，或者使用混合现实门户 PC 安装。</span><span class="sxs-lookup"><span data-stu-id="ea55a-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="ea55a-111">Perception 模拟绕过混合现实设备上的实时传感器并发送模拟设备上运行的应用程序的输入。</span><span class="sxs-lookup"><span data-stu-id="ea55a-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="ea55a-112">应用程序接收这些输入的事件通过相同的 Api，它们始终使用和不能确定它们与实际传感器与运行与 Perception 模拟运行之间的区别。</span><span class="sxs-lookup"><span data-stu-id="ea55a-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="ea55a-113">Perception 模拟是 HoloLens 仿真程序用于发送模拟的输入到 HoloLens 虚拟机的相同技术。</span><span class="sxs-lookup"><span data-stu-id="ea55a-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="ea55a-114">若要开始在代码中使用模拟，请先创建 IPerceptionSimulationManager 对象。</span><span class="sxs-lookup"><span data-stu-id="ea55a-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="ea55a-115">从该对象，您可以发出命令来控制属性的模拟"人"，包括头位置、 手位置和手势，并可以启用和操作动作控制器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="ea55a-116">为 Perception 模拟设置 Visual Studio 项目</span><span class="sxs-lookup"><span data-stu-id="ea55a-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="ea55a-117">[安装 HoloLens 模拟器](install-the-tools.md)开发计算机上。</span><span class="sxs-lookup"><span data-stu-id="ea55a-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="ea55a-118">在仿真程序包含将用于对模拟的库。</span><span class="sxs-lookup"><span data-stu-id="ea55a-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="ea55a-119">创建新的 Visual StudioC#桌面 （控制台项目运行良好开始） 的项目。</span><span class="sxs-lookup"><span data-stu-id="ea55a-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="ea55a-120">将以下二进制文件作为引用添加到你的项目 (项目-> 添加-> 引用...)。您可以找到它们在 %programfiles (x86) %\Microsoft XDE\\（版本），如 **%programfiles (x86) %\Microsoft XDE\\10.0.18362.0** HoloLens 2 仿真程序。</span><span class="sxs-lookup"><span data-stu-id="ea55a-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="ea55a-121">(注意： 尽管这些二进制文件是 HoloLens 2 仿真程序的一部分，但它们也适用于 Windows Mixed Reality 在桌面上。)一个。</span><span class="sxs-lookup"><span data-stu-id="ea55a-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="ea55a-122">PerceptionSimulationManager.Interop.dll-管理C#Perception 模拟的包装器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="ea55a-123">b.</span><span class="sxs-lookup"><span data-stu-id="ea55a-123">b.</span></span> <span data-ttu-id="ea55a-124">PerceptionSimulationRest.dll-设置 web 套接字通信通道到 HoloLens 或仿真器的库。</span><span class="sxs-lookup"><span data-stu-id="ea55a-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="ea55a-125">c.</span><span class="sxs-lookup"><span data-stu-id="ea55a-125">c.</span></span> <span data-ttu-id="ea55a-126">SimulationStream.Interop.dll-共享类型进行模拟。</span><span class="sxs-lookup"><span data-stu-id="ea55a-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="ea55a-127">将实现添加到你的项目二进制 PerceptionSimulationManager.dll。</span><span class="sxs-lookup"><span data-stu-id="ea55a-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="ea55a-128">首先将其作为二进制文件添加到项目 (项目-> 添加-> 现有项...)。将其保存为一个链接，以便它不会将其复制到你的项目源文件夹。</span><span class="sxs-lookup"><span data-stu-id="ea55a-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="ea55a-129">![向项目的链接的形式添加 PerceptionSimulationManager.dll](images/saveaslink.png) b。</span><span class="sxs-lookup"><span data-stu-id="ea55a-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="ea55a-130">请确保它获取的复制到生成输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="ea55a-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="ea55a-131">这是二进制文件的属性表中。</span><span class="sxs-lookup"><span data-stu-id="ea55a-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="ea55a-132">![将标记 PerceptionSimulationManager.dll 将复制到输出目录](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="ea55a-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="ea55a-133">将活动解决方案平台设置为 x64。</span><span class="sxs-lookup"><span data-stu-id="ea55a-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="ea55a-134">（使用配置管理器，以创建适用于 x64 的平台项，如果一个尚不存在）。</span><span class="sxs-lookup"><span data-stu-id="ea55a-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="ea55a-135">创建 IPerceptionSimulation Manager 对象</span><span class="sxs-lookup"><span data-stu-id="ea55a-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="ea55a-136">若要控制模拟，将从 IPerceptionSimulationManager 对象检索到的对象发布更新。</span><span class="sxs-lookup"><span data-stu-id="ea55a-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="ea55a-137">第一步是获取该对象，并将其连接到目标设备或仿真程序。</span><span class="sxs-lookup"><span data-stu-id="ea55a-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="ea55a-138">可以通过单击在设备门户按钮获取仿真程序的 IP 地址[工具栏](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="ea55a-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="ea55a-139">![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**:在仿真器中打开 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="ea55a-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="ea55a-140">为 Windows Mixed Reality，这可以检索在设置应用"更新和安全性"，然后，"对于开发人员"中"使用连接:"部分下"启用设备门户。"</span><span class="sxs-lookup"><span data-stu-id="ea55a-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="ea55a-141">请务必记下的 IP 地址和端口。</span><span class="sxs-lookup"><span data-stu-id="ea55a-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="ea55a-142">首先，将调用 RestSimulationStreamSink.Create 获取 RestSimulationStreamSink 对象。</span><span class="sxs-lookup"><span data-stu-id="ea55a-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="ea55a-143">这是目标设备或仿真程序将控制通过 http 连接。</span><span class="sxs-lookup"><span data-stu-id="ea55a-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="ea55a-144">将传递给你的命令，并将其由处理[Windows Device Portal](using-the-windows-device-portal.md)设备或仿真器上运行。</span><span class="sxs-lookup"><span data-stu-id="ea55a-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="ea55a-145">将需要创建一个对象的四个参数是：</span><span class="sxs-lookup"><span data-stu-id="ea55a-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="ea55a-146">Uri uri-目标设备的 IP 地址 (例如，"http://123.123.123.123"或"http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="ea55a-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="ea55a-147">System.Net.NetworkCredential 凭据-用户名/密码用于连接到[Windows Device Portal](using-the-windows-device-portal.md)目标设备或仿真程序上。</span><span class="sxs-lookup"><span data-stu-id="ea55a-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="ea55a-148">如果您要连接到仿真程序通过其本地地址 (例如，168。 *。* 。 \*) 将在同一台 PC 上接受任何凭据。</span><span class="sxs-lookup"><span data-stu-id="ea55a-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="ea55a-149">正常情况-bool 的普通优先级低优先级为 false，则返回 True。</span><span class="sxs-lookup"><span data-stu-id="ea55a-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="ea55a-150">你通常想要将其设置为 *，则返回 true*的测试方案，它允许测试控制。</span><span class="sxs-lookup"><span data-stu-id="ea55a-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="ea55a-151">仿真程序和 Windows Mixed Reality 模拟使用低优先级服务连接。</span><span class="sxs-lookup"><span data-stu-id="ea55a-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="ea55a-152">如果你的测试还使用低优先级服务连接，大多数最近创建的连接将在控件中。</span><span class="sxs-lookup"><span data-stu-id="ea55a-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="ea55a-153">System.Threading.CancellationToken 令牌-令牌取消异步操作。</span><span class="sxs-lookup"><span data-stu-id="ea55a-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="ea55a-154">其次，您将创建 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="ea55a-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="ea55a-155">这是用于控制模拟的对象。</span><span class="sxs-lookup"><span data-stu-id="ea55a-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="ea55a-156">请注意这必须还将完成的异步方法中。</span><span class="sxs-lookup"><span data-stu-id="ea55a-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="ea55a-157">控制模拟的用户</span><span class="sxs-lookup"><span data-stu-id="ea55a-157">Control the simulated Human</span></span>

<span data-ttu-id="ea55a-158">IPerceptionSimulationManager 有一个人属性可返回 ISimulatedHuman 对象。</span><span class="sxs-lookup"><span data-stu-id="ea55a-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="ea55a-159">若要控制模拟的用户，请执行此对象上的操作。</span><span class="sxs-lookup"><span data-stu-id="ea55a-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="ea55a-160">例如：</span><span class="sxs-lookup"><span data-stu-id="ea55a-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="ea55a-161">基本示例C#控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="ea55a-161">Basic Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="ea55a-162">扩展示例C#控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="ea55a-162">Extended Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="ea55a-163">请注意 6 DOF 控制器上</span><span class="sxs-lookup"><span data-stu-id="ea55a-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="ea55a-164">在调用之前的任何属性上的模拟的 6 DOF 控制器上的方法，必须激活该控制器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="ea55a-165">不执行此操作将导致异常。</span><span class="sxs-lookup"><span data-stu-id="ea55a-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="ea55a-166">从 Windows 10 开始可能 2019年更新，可以安装和激活的状态属性设置为 SimulatedSixDofControllerStatus.Active ISimulatedSixDofController 对象上模拟的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="ea55a-167">在 Windows 10 2018 年 10 月更新和更早版本，您必须单独安装模拟的 6 DOF 控制器首先通过调用 PerceptionSimulationDevice 工具 \Windows\System32 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="ea55a-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="ea55a-168">此工具的用法如下所示：</span><span class="sxs-lookup"><span data-stu-id="ea55a-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="ea55a-169">例如</span><span class="sxs-lookup"><span data-stu-id="ea55a-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="ea55a-170">支持的操作是：</span><span class="sxs-lookup"><span data-stu-id="ea55a-170">Supported actions are:</span></span>
* <span data-ttu-id="ea55a-171">我 = install</span><span class="sxs-lookup"><span data-stu-id="ea55a-171">i = install</span></span>
* <span data-ttu-id="ea55a-172">问: = 查询</span><span class="sxs-lookup"><span data-stu-id="ea55a-172">q = query</span></span>
* <span data-ttu-id="ea55a-173">r = 删除</span><span class="sxs-lookup"><span data-stu-id="ea55a-173">r = remove</span></span>

<span data-ttu-id="ea55a-174">支持的实例是：</span><span class="sxs-lookup"><span data-stu-id="ea55a-174">Supported instances are:</span></span>
* <span data-ttu-id="ea55a-175">1 = 左的 6 DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="ea55a-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="ea55a-176">2 = 右 6 DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="ea55a-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="ea55a-177">（零返回值） 的成功或失败 （非零返回值），将指示进程的退出代码。</span><span class="sxs-lookup"><span data-stu-id="ea55a-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="ea55a-178">当使用 q 操作来查询该值指示安装了控制器，返回值将为零 (0)，如果尚未安装在控制器或一 （1） 如果安装了控制器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="ea55a-179">当删除控制器在 Windows 10 2018 年 10 月更新或更早版本，其将状态设置为 Off 通过 API 第一次，然后调用 PerceptionSimulationDevice 工具。</span><span class="sxs-lookup"><span data-stu-id="ea55a-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="ea55a-180">请注意，必须以管理员身份运行此工具。</span><span class="sxs-lookup"><span data-stu-id="ea55a-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="ea55a-181">API 参考</span><span class="sxs-lookup"><span data-stu-id="ea55a-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="ea55a-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="ea55a-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="ea55a-183">介绍一种模拟的设备类型</span><span class="sxs-lookup"><span data-stu-id="ea55a-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="ea55a-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="ea55a-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="ea55a-185">虚构引用设备的默认值为 PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="ea55a-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="ea55a-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="ea55a-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="ea55a-187">头跟踪器模式下运行</span><span class="sxs-lookup"><span data-stu-id="ea55a-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="ea55a-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="ea55a-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="ea55a-189">默认跟踪头。</span><span class="sxs-lookup"><span data-stu-id="ea55a-189">Default Head Tracking.</span></span> <span data-ttu-id="ea55a-190">这意味着，系统可能会选择跟踪模式下运行时条件基于最佳头。</span><span class="sxs-lookup"><span data-stu-id="ea55a-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="ea55a-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="ea55a-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="ea55a-192">方向仅头跟踪。</span><span class="sxs-lookup"><span data-stu-id="ea55a-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="ea55a-193">这意味着跟踪的位置可能不可靠，并依赖于头位置某些功能可能不可用。</span><span class="sxs-lookup"><span data-stu-id="ea55a-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="ea55a-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="ea55a-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="ea55a-195">位置头跟踪。</span><span class="sxs-lookup"><span data-stu-id="ea55a-195">Positional Head Tracking.</span></span> <span data-ttu-id="ea55a-196">这意味着，跟踪头位置和方向都是可靠</span><span class="sxs-lookup"><span data-stu-id="ea55a-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="ea55a-197">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="ea55a-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="ea55a-198">介绍模拟的手势</span><span class="sxs-lookup"><span data-stu-id="ea55a-198">Describes a simulated gesture</span></span>

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

<span data-ttu-id="ea55a-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="ea55a-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="ea55a-200">用来指示没有手势的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="ea55a-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="ea55a-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="ea55a-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="ea55a-202">手指按下手势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-202">A finger pressed gesture.</span></span>

<span data-ttu-id="ea55a-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="ea55a-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="ea55a-204">手指发布手势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-204">A finger released gesture.</span></span>

<span data-ttu-id="ea55a-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="ea55a-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="ea55a-206">主页/系统笔势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-206">The home/system gesture.</span></span>

<span data-ttu-id="ea55a-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="ea55a-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="ea55a-208">最大有效的手势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="ea55a-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="ea55a-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="ea55a-210">模拟的 6 DOF 控制器了可能的状态。</span><span class="sxs-lookup"><span data-stu-id="ea55a-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="ea55a-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span><span class="sxs-lookup"><span data-stu-id="ea55a-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="ea55a-212">6 DOF 控制器处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="ea55a-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="ea55a-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span><span class="sxs-lookup"><span data-stu-id="ea55a-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="ea55a-214">6 DOF 控制器已打开，并跟踪。</span><span class="sxs-lookup"><span data-stu-id="ea55a-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="ea55a-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="ea55a-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="ea55a-216">6 DOF 控制器处于开启状态，但不能跟踪。</span><span class="sxs-lookup"><span data-stu-id="ea55a-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="ea55a-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="ea55a-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="ea55a-218">模拟的 6 DOF 控制器上受支持的按钮。</span><span class="sxs-lookup"><span data-stu-id="ea55a-218">The supported buttons on a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

<span data-ttu-id="ea55a-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span><span class="sxs-lookup"><span data-stu-id="ea55a-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="ea55a-220">用来指示没有按钮的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="ea55a-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="ea55a-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span><span class="sxs-lookup"><span data-stu-id="ea55a-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="ea55a-222">已按下主页按钮。</span><span class="sxs-lookup"><span data-stu-id="ea55a-222">The Home button is pressed.</span></span>

<span data-ttu-id="ea55a-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span><span class="sxs-lookup"><span data-stu-id="ea55a-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="ea55a-224">按下菜单按钮。</span><span class="sxs-lookup"><span data-stu-id="ea55a-224">The Menu button is pressed.</span></span>

<span data-ttu-id="ea55a-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span><span class="sxs-lookup"><span data-stu-id="ea55a-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="ea55a-226">按下手柄按钮。</span><span class="sxs-lookup"><span data-stu-id="ea55a-226">The Grip button is pressed.</span></span>

<span data-ttu-id="ea55a-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="ea55a-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="ea55a-228">触摸板已按下。</span><span class="sxs-lookup"><span data-stu-id="ea55a-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="ea55a-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span><span class="sxs-lookup"><span data-stu-id="ea55a-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="ea55a-230">选择按钮已按下。</span><span class="sxs-lookup"><span data-stu-id="ea55a-230">The Select button is pressed.</span></span>

<span data-ttu-id="ea55a-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="ea55a-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="ea55a-232">使用触摸板。</span><span class="sxs-lookup"><span data-stu-id="ea55a-232">The TouchPad is touched.</span></span>

<span data-ttu-id="ea55a-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="ea55a-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="ea55a-234">摇杆已按下。</span><span class="sxs-lookup"><span data-stu-id="ea55a-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="ea55a-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span><span class="sxs-lookup"><span data-stu-id="ea55a-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="ea55a-236">最大有效按钮。</span><span class="sxs-lookup"><span data-stu-id="ea55a-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="ea55a-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="ea55a-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="ea55a-238">模拟眼睛的校准状态</span><span class="sxs-lookup"><span data-stu-id="ea55a-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="ea55a-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="ea55a-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="ea55a-240">眼睛校准不可用。</span><span class="sxs-lookup"><span data-stu-id="ea55a-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="ea55a-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span><span class="sxs-lookup"><span data-stu-id="ea55a-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="ea55a-242">眼睛已校准。</span><span class="sxs-lookup"><span data-stu-id="ea55a-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="ea55a-243">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="ea55a-243">This is the default value.</span></span>

<span data-ttu-id="ea55a-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="ea55a-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="ea55a-245">眼睛是正在校准。</span><span class="sxs-lookup"><span data-stu-id="ea55a-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="ea55a-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="ea55a-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="ea55a-247">眼睛需要校验一次。</span><span class="sxs-lookup"><span data-stu-id="ea55a-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="ea55a-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="ea55a-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="ea55a-249">跟踪准确性的手形图标的联接。</span><span class="sxs-lookup"><span data-stu-id="ea55a-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="ea55a-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="ea55a-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="ea55a-251">不跟踪联合。</span><span class="sxs-lookup"><span data-stu-id="ea55a-251">The joint is not tracked.</span></span>

<span data-ttu-id="ea55a-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span><span class="sxs-lookup"><span data-stu-id="ea55a-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="ea55a-253">推断的联合的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-253">The joint position is inferred.</span></span>

<span data-ttu-id="ea55a-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span><span class="sxs-lookup"><span data-stu-id="ea55a-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="ea55a-255">完全跟踪联合。</span><span class="sxs-lookup"><span data-stu-id="ea55a-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="ea55a-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="ea55a-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="ea55a-257">跟踪准确性的手形图标的联接。</span><span class="sxs-lookup"><span data-stu-id="ea55a-257">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

<span data-ttu-id="ea55a-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span><span class="sxs-lookup"><span data-stu-id="ea55a-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="ea55a-259">手形图标的手指关节配置为反映已关闭的姿势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="ea55a-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span><span class="sxs-lookup"><span data-stu-id="ea55a-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="ea55a-261">手形图标的手指关节配置以反映打开姿势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="ea55a-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span><span class="sxs-lookup"><span data-stu-id="ea55a-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="ea55a-263">手形图标的手指关节配置以反映指针姿势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="ea55a-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span><span class="sxs-lookup"><span data-stu-id="ea55a-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="ea55a-265">手形图标的手指关节配置以反映捏指姿势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="ea55a-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span><span class="sxs-lookup"><span data-stu-id="ea55a-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="ea55a-267">SimulatedHandPose 最大有效值。</span><span class="sxs-lookup"><span data-stu-id="ea55a-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="ea55a-268">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="ea55a-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="ea55a-269">描述状态的播放。</span><span class="sxs-lookup"><span data-stu-id="ea55a-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="ea55a-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="ea55a-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="ea55a-271">记录当前处于已停止，并准备好进行播放。</span><span class="sxs-lookup"><span data-stu-id="ea55a-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="ea55a-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="ea55a-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="ea55a-273">当前播放该录制。</span><span class="sxs-lookup"><span data-stu-id="ea55a-273">The recording is currently playing.</span></span>

<span data-ttu-id="ea55a-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="ea55a-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="ea55a-275">当前已暂停录制。</span><span class="sxs-lookup"><span data-stu-id="ea55a-275">The recording is currently paused.</span></span>

<span data-ttu-id="ea55a-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="ea55a-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="ea55a-277">记录已到达末尾。</span><span class="sxs-lookup"><span data-stu-id="ea55a-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="ea55a-278">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="ea55a-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="ea55a-279">介绍了 3 个组件矢量，可能会描述一个点或 3D 空间中的向量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="ea55a-280">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="ea55a-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="ea55a-281">向量的 X 分量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-281">The X component of the vector.</span></span>

<span data-ttu-id="ea55a-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="ea55a-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="ea55a-283">向量的 Y 分量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-283">The Y component of the vector.</span></span>

<span data-ttu-id="ea55a-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="ea55a-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="ea55a-285">向量的 Z 分量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-285">The Z component of the vector.</span></span>

<span data-ttu-id="ea55a-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="ea55a-287">构造新 Vector3。</span><span class="sxs-lookup"><span data-stu-id="ea55a-287">Construct a new Vector3.</span></span>

<span data-ttu-id="ea55a-288">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-288">Parameters</span></span>
* <span data-ttu-id="ea55a-289">x 轴向量的 x 分量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="ea55a-290">y 轴向量的 y 分量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="ea55a-291">z-矢量的 z 分量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="ea55a-292">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="ea55a-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="ea55a-293">描述的 3 个组件旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="ea55a-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="ea55a-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="ea55a-295">间距组成部分旋转、 绕 X 轴向下。</span><span class="sxs-lookup"><span data-stu-id="ea55a-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="ea55a-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="ea55a-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="ea55a-297">右围绕 Y 轴的旋转角度偏航组件。</span><span class="sxs-lookup"><span data-stu-id="ea55a-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="ea55a-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="ea55a-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="ea55a-299">右围绕 Z 轴的旋转角度汇总组件。</span><span class="sxs-lookup"><span data-stu-id="ea55a-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="ea55a-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="ea55a-301">构造新 Rotation3。</span><span class="sxs-lookup"><span data-stu-id="ea55a-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="ea55a-302">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-302">Parameters</span></span>
* <span data-ttu-id="ea55a-303">间距的旋转的音调组件。</span><span class="sxs-lookup"><span data-stu-id="ea55a-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="ea55a-304">偏航-旋转偏航组件。</span><span class="sxs-lookup"><span data-stu-id="ea55a-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="ea55a-305">将鼠标移-旋转的汇总组件。</span><span class="sxs-lookup"><span data-stu-id="ea55a-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="ea55a-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="ea55a-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="ea55a-307">在模拟手的形状上介绍的接合的配置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="ea55a-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span><span class="sxs-lookup"><span data-stu-id="ea55a-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="ea55a-309">联合的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-309">The position of the joint.</span></span>

<span data-ttu-id="ea55a-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span><span class="sxs-lookup"><span data-stu-id="ea55a-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="ea55a-311">联合的旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-311">The rotation of the joint.</span></span>

<span data-ttu-id="ea55a-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="ea55a-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="ea55a-313">跟踪准确性的联合。</span><span class="sxs-lookup"><span data-stu-id="ea55a-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="ea55a-314">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="ea55a-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="ea55a-315">描述视图截锥，通常使用照相机。</span><span class="sxs-lookup"><span data-stu-id="ea55a-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="ea55a-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="ea55a-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="ea55a-317">截锥中包含的最小距离。</span><span class="sxs-lookup"><span data-stu-id="ea55a-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="ea55a-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="ea55a-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="ea55a-319">截锥中包含的最大距离。</span><span class="sxs-lookup"><span data-stu-id="ea55a-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="ea55a-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="ea55a-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="ea55a-321">水平视图的字段的截锥，以弧度为单位 （小于 PI）。</span><span class="sxs-lookup"><span data-stu-id="ea55a-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="ea55a-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="ea55a-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="ea55a-323">水平视角为垂直的视野比率。</span><span class="sxs-lookup"><span data-stu-id="ea55a-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="ea55a-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="ea55a-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="ea55a-325">用于生成用来控制设备的数据包的根。</span><span class="sxs-lookup"><span data-stu-id="ea55a-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="ea55a-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="ea55a-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="ea55a-327">检索将解释模拟的人类和模拟的世界的模拟的设备对象。</span><span class="sxs-lookup"><span data-stu-id="ea55a-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="ea55a-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="ea55a-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="ea55a-329">检索控制模拟的人类的对象。</span><span class="sxs-lookup"><span data-stu-id="ea55a-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="ea55a-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="ea55a-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="ea55a-331">将模拟重置为其默认状态。</span><span class="sxs-lookup"><span data-stu-id="ea55a-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="ea55a-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="ea55a-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="ea55a-333">接口描述将解释模拟的世界和模拟的用户的设备</span><span class="sxs-lookup"><span data-stu-id="ea55a-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="ea55a-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="ea55a-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="ea55a-335">从模拟设备中检索头跟踪器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="ea55a-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="ea55a-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="ea55a-337">从模拟设备中检索的现有跟踪器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="ea55a-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="ea55a-339">设置模拟设备以提供的设备类型匹配的属性。</span><span class="sxs-lookup"><span data-stu-id="ea55a-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="ea55a-340">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-340">Parameters</span></span>
* <span data-ttu-id="ea55a-341">键入的新类型的模拟设备</span><span class="sxs-lookup"><span data-stu-id="ea55a-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="ea55a-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="ea55a-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="ea55a-343">接口描述跟踪的模拟人类的模拟设备的部分。</span><span class="sxs-lookup"><span data-stu-id="ea55a-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="ea55a-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="ea55a-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="ea55a-345">检索并设置当前头跟踪器模式。</span><span class="sxs-lookup"><span data-stu-id="ea55a-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="ea55a-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="ea55a-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="ea55a-347">描述跟踪的模拟用户的手中的模拟设备的部分接口</span><span class="sxs-lookup"><span data-stu-id="ea55a-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

<span data-ttu-id="ea55a-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ea55a-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="ea55a-349">检索与世界里，相关的节点以米为单位的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ea55a-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="ea55a-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="ea55a-351">检索和设置的模拟的手动跟踪程序，位置相对于头的中心。</span><span class="sxs-lookup"><span data-stu-id="ea55a-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="ea55a-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="ea55a-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="ea55a-353">检索和设置的模拟的手动跟踪器的向下音调。</span><span class="sxs-lookup"><span data-stu-id="ea55a-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="ea55a-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="ea55a-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="ea55a-355">检索和设置是否忽略模拟的手动跟踪器的截锥。</span><span class="sxs-lookup"><span data-stu-id="ea55a-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="ea55a-356">如果忽略，将始终显示两只手。</span><span class="sxs-lookup"><span data-stu-id="ea55a-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="ea55a-357">当不忽略 （默认值） 内手动跟踪器的截锥时才可见手。</span><span class="sxs-lookup"><span data-stu-id="ea55a-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="ea55a-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="ea55a-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="ea55a-359">检索和设置用于确定指针是否对模拟的手动跟踪器可见的截锥属性。</span><span class="sxs-lookup"><span data-stu-id="ea55a-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="ea55a-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="ea55a-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="ea55a-361">用于控制模拟的人类的顶部级别接口。</span><span class="sxs-lookup"><span data-stu-id="ea55a-361">Top level interface for controlling the simulated human.</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="ea55a-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ea55a-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="ea55a-363">检索并与世界中，以米为单位相关设置的节点的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="ea55a-364">位置对应于人类的英尺位于中心点。</span><span class="sxs-lookup"><span data-stu-id="ea55a-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="ea55a-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="ea55a-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="ea55a-366">检索并在世界中模拟的人脸设置方向。</span><span class="sxs-lookup"><span data-stu-id="ea55a-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="ea55a-367">0 弧度朝下负 Z 轴。</span><span class="sxs-lookup"><span data-stu-id="ea55a-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="ea55a-368">正弧度围绕 Y 轴顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="ea55a-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="ea55a-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="ea55a-370">检索和设置的模拟用户的高度，以米为单位。</span><span class="sxs-lookup"><span data-stu-id="ea55a-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="ea55a-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="ea55a-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="ea55a-372">检索模拟人类的左侧。</span><span class="sxs-lookup"><span data-stu-id="ea55a-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="ea55a-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="ea55a-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="ea55a-374">检索模拟人类的右侧。</span><span class="sxs-lookup"><span data-stu-id="ea55a-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="ea55a-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="ea55a-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="ea55a-376">检索模拟人类的开头。</span><span class="sxs-lookup"><span data-stu-id="ea55a-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="ea55a-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="ea55a-378">将模拟的人类移动相对于其当前的位置，以米为单位。</span><span class="sxs-lookup"><span data-stu-id="ea55a-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="ea55a-379">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-379">Parameters</span></span>
* <span data-ttu-id="ea55a-380">翻译的移动，相对于当前的位置的翻译。</span><span class="sxs-lookup"><span data-stu-id="ea55a-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="ea55a-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="ea55a-382">模拟的人类相对于其当前方向，围绕 Y 轴顺时针旋转</span><span class="sxs-lookup"><span data-stu-id="ea55a-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="ea55a-383">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-383">Parameters</span></span>
* <span data-ttu-id="ea55a-384">弧度-要围绕 Y 轴旋转的量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="ea55a-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="ea55a-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="ea55a-386">其他属性均可通过强制转换到 ISimulatedHuman2 ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="ea55a-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="ea55a-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span><span class="sxs-lookup"><span data-stu-id="ea55a-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="ea55a-388">检索左的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="ea55a-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span><span class="sxs-lookup"><span data-stu-id="ea55a-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="ea55a-390">检索正确的 6 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="ea55a-391">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="ea55a-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="ea55a-392">接口描述模拟用户的手的形状</span><span class="sxs-lookup"><span data-stu-id="ea55a-392">Interface describing a hand of the simulated human</span></span>

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

<span data-ttu-id="ea55a-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ea55a-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="ea55a-394">检索与世界里，相关的节点以米为单位的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ea55a-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="ea55a-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="ea55a-396">检索和设置以米为单位的相对于人，模拟手形图标的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="ea55a-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="ea55a-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="ea55a-398">检索和设置是否手形图标当前处于激活状态。</span><span class="sxs-lookup"><span data-stu-id="ea55a-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="ea55a-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="ea55a-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="ea55a-400">检索当前可见 （即，是在一个位置可检测到的 HandTracker） SimulatedDevice 手形图标是否。</span><span class="sxs-lookup"><span data-stu-id="ea55a-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="ea55a-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="ea55a-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="ea55a-402">移动手形图标，以便对 SimulatedDevice 可见。</span><span class="sxs-lookup"><span data-stu-id="ea55a-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="ea55a-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="ea55a-404">移动模拟手的位置，相对于其当前的位置，以米为单位。</span><span class="sxs-lookup"><span data-stu-id="ea55a-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="ea55a-405">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-405">Parameters</span></span>
* <span data-ttu-id="ea55a-406">翻译-模拟的手的平移量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="ea55a-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="ea55a-408">执行使用模拟的手手势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="ea55a-409">它就只会检测到系统手形图标已启用。</span><span class="sxs-lookup"><span data-stu-id="ea55a-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="ea55a-410">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-410">Parameters</span></span>
* <span data-ttu-id="ea55a-411">笔势-要执行的笔势。</span><span class="sxs-lookup"><span data-stu-id="ea55a-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="ea55a-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="ea55a-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="ea55a-413">其他属性均可通过强制转换到 ISimulatedHand2 ISimulatedHand。</span><span class="sxs-lookup"><span data-stu-id="ea55a-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="ea55a-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span><span class="sxs-lookup"><span data-stu-id="ea55a-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="ea55a-415">检索或设置模拟手的旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="ea55a-416">查看该轴时，正弧度为单位的顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="ea55a-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="ea55a-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="ea55a-418">其他属性均可通过强制转换到 ISimulatedHand3 ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="ea55a-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="ea55a-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="ea55a-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="ea55a-420">获取指定的联合的联合配置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="ea55a-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="ea55a-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="ea55a-422">设置指定的联合的联合配置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="ea55a-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="ea55a-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="ea55a-424">设置为与要进行动画处理的可选标志已知姿势手形图标。</span><span class="sxs-lookup"><span data-stu-id="ea55a-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="ea55a-425">注意： 进行动画处理不会导致关节立即反映其最终的联合配置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="ea55a-426">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="ea55a-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="ea55a-427">接口描述模拟人类的开头。</span><span class="sxs-lookup"><span data-stu-id="ea55a-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="ea55a-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ea55a-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="ea55a-429">检索与世界里，相关的节点以米为单位的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ea55a-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="ea55a-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="ea55a-431">检索模拟头的旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="ea55a-432">查看该轴时，正弧度为单位的顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ea55a-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="ea55a-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="ea55a-434">检索模拟的头直径。</span><span class="sxs-lookup"><span data-stu-id="ea55a-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="ea55a-435">此值用于确定 head 的中心 （旋转的点）。</span><span class="sxs-lookup"><span data-stu-id="ea55a-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="ea55a-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="ea55a-437">旋转模拟的头相对于其当前的旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="ea55a-438">查看该轴时，正弧度为单位的顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ea55a-439">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-439">Parameters</span></span>
* <span data-ttu-id="ea55a-440">旋转-要旋转的量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="ea55a-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="ea55a-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="ea55a-442">其他属性均可通过强制转换到 ISimulatedHead2 ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="ea55a-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="ea55a-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span><span class="sxs-lookup"><span data-stu-id="ea55a-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="ea55a-444">检索模拟人类的眼。</span><span class="sxs-lookup"><span data-stu-id="ea55a-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="ea55a-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="ea55a-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="ea55a-446">描述与模拟的用户相关联的 6 DOF 控制器的接口。</span><span class="sxs-lookup"><span data-stu-id="ea55a-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

<span data-ttu-id="ea55a-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ea55a-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="ea55a-448">检索与世界里，相关的节点以米为单位的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ea55a-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span><span class="sxs-lookup"><span data-stu-id="ea55a-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="ea55a-450">检索或设置控制器的当前状态。</span><span class="sxs-lookup"><span data-stu-id="ea55a-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="ea55a-451">控制器状态必须设置为一个值，而不关闭要移动、 旋转或按进行任何调用之前按钮将会成功。</span><span class="sxs-lookup"><span data-stu-id="ea55a-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="ea55a-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span><span class="sxs-lookup"><span data-stu-id="ea55a-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="ea55a-453">检索或设置相对于用户的模拟控制器的位置，以米为单位。</span><span class="sxs-lookup"><span data-stu-id="ea55a-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="ea55a-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span><span class="sxs-lookup"><span data-stu-id="ea55a-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="ea55a-455">检索或设置模拟控制器的方向。</span><span class="sxs-lookup"><span data-stu-id="ea55a-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="ea55a-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="ea55a-457">将模拟的控制器的位置移动相对于其当前的位置，以米为单位。</span><span class="sxs-lookup"><span data-stu-id="ea55a-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="ea55a-458">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-458">Parameters</span></span>
* <span data-ttu-id="ea55a-459">翻译-模拟的控制器的平移量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="ea55a-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="ea55a-461">模拟的控制器上按一个按钮。</span><span class="sxs-lookup"><span data-stu-id="ea55a-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="ea55a-462">它就只会检测到系统已启用控制器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="ea55a-463">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-463">Parameters</span></span>
* <span data-ttu-id="ea55a-464">按钮的按钮按下。</span><span class="sxs-lookup"><span data-stu-id="ea55a-464">button - The button to press.</span></span>

<span data-ttu-id="ea55a-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="ea55a-466">释放模拟控制器上的按钮。</span><span class="sxs-lookup"><span data-stu-id="ea55a-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="ea55a-467">它就只会检测到系统已启用控制器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="ea55a-468">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-468">Parameters</span></span>
* <span data-ttu-id="ea55a-469">按钮的发布按钮。</span><span class="sxs-lookup"><span data-stu-id="ea55a-469">button - The button to release.</span></span>

<span data-ttu-id="ea55a-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="ea55a-471">获取为模拟指模拟的控制器的触摸板上的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="ea55a-472">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-472">Parameters</span></span>
* <span data-ttu-id="ea55a-473">x 的手指水平位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="ea55a-474">y 的手指垂直位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="ea55a-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="ea55a-476">设置模拟的控制器的触摸板模拟手指的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="ea55a-477">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-477">Parameters</span></span>
* <span data-ttu-id="ea55a-478">x 的手指水平位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="ea55a-479">y 的手指垂直位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="ea55a-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="ea55a-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="ea55a-481">其他属性和方法均可通过强制转换到 ISimulatedSixDofController2 ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="ea55a-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="ea55a-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="ea55a-483">获取模拟摇杆模拟控制器上的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="ea55a-484">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-484">Parameters</span></span>
* <span data-ttu-id="ea55a-485">x 的摇杆水平位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="ea55a-486">y 的摇杆垂直位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="ea55a-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="ea55a-488">模拟的控制器上设置的模拟摇杆位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="ea55a-489">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-489">Parameters</span></span>
* <span data-ttu-id="ea55a-490">x 的摇杆水平位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="ea55a-491">y 的摇杆垂直位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="ea55a-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="ea55a-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="ea55a-493">检索或设置模拟控制器的电池电量水平。</span><span class="sxs-lookup"><span data-stu-id="ea55a-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="ea55a-494">值必须大于 0.0 且小于或等于 100.0。</span><span class="sxs-lookup"><span data-stu-id="ea55a-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="ea55a-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="ea55a-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="ea55a-496">描述模拟人类的眼的接口。</span><span class="sxs-lookup"><span data-stu-id="ea55a-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="ea55a-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span><span class="sxs-lookup"><span data-stu-id="ea55a-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="ea55a-498">检索模拟眼睛的旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="ea55a-499">查看该轴时，正弧度为单位的顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ea55a-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="ea55a-501">旋转模拟的眼睛相对于其当前的旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="ea55a-502">查看该轴时，正弧度为单位的顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="ea55a-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ea55a-503">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-503">Parameters</span></span>
* <span data-ttu-id="ea55a-504">旋转-要旋转的量。</span><span class="sxs-lookup"><span data-stu-id="ea55a-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="ea55a-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="ea55a-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="ea55a-506">获取或设置的模拟眼睛的校准状态。</span><span class="sxs-lookup"><span data-stu-id="ea55a-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="ea55a-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="ea55a-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="ea55a-508">检索与世界里，相关的节点以米为单位的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="ea55a-509">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="ea55a-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="ea55a-510">加载与单个记录进行交互的接口中进行播放。</span><span class="sxs-lookup"><span data-stu-id="ea55a-510">Interface for interacting with a single recording loaded for playback.</span></span>

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

<span data-ttu-id="ea55a-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="ea55a-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="ea55a-512">检索在记录中的数据类型的列表。</span><span class="sxs-lookup"><span data-stu-id="ea55a-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="ea55a-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="ea55a-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="ea55a-514">检索记录的当前状态。</span><span class="sxs-lookup"><span data-stu-id="ea55a-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="ea55a-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="ea55a-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="ea55a-516">开始播放。</span><span class="sxs-lookup"><span data-stu-id="ea55a-516">Start the playback.</span></span> <span data-ttu-id="ea55a-517">从暂停的位置; 如果暂停录制后，将恢复播放如果停止，将开头开始播放。</span><span class="sxs-lookup"><span data-stu-id="ea55a-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="ea55a-518">如果已在播放，则忽略此调用。</span><span class="sxs-lookup"><span data-stu-id="ea55a-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="ea55a-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="ea55a-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="ea55a-520">暂停播放在其当前的位置。</span><span class="sxs-lookup"><span data-stu-id="ea55a-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="ea55a-521">如果停止录制，则将忽略此调用。</span><span class="sxs-lookup"><span data-stu-id="ea55a-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="ea55a-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="ea55a-523">查找在指定的时间 （以 100 纳秒间隔从一开始） 记录，并在该位置暂停。</span><span class="sxs-lookup"><span data-stu-id="ea55a-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="ea55a-524">如果所记录的末尾之外的时间，它会暂停在最后一帧。</span><span class="sxs-lookup"><span data-stu-id="ea55a-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="ea55a-525">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-525">Parameters</span></span>
* <span data-ttu-id="ea55a-526">计时周期数-要查找的时间。</span><span class="sxs-lookup"><span data-stu-id="ea55a-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="ea55a-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="ea55a-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="ea55a-528">停止播放和位置重置到开头。</span><span class="sxs-lookup"><span data-stu-id="ea55a-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="ea55a-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="ea55a-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="ea55a-530">在播放期间接收状态更改的接口。</span><span class="sxs-lookup"><span data-stu-id="ea55a-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="ea55a-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="ea55a-532">ISimulationRecording 播放状态发生更改时调用。</span><span class="sxs-lookup"><span data-stu-id="ea55a-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="ea55a-533">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-533">Parameters</span></span>
* <span data-ttu-id="ea55a-534">newState-记录的新状态。</span><span class="sxs-lookup"><span data-stu-id="ea55a-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="ea55a-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="ea55a-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="ea55a-536">根对象，用于创建 Perception 模拟对象。</span><span class="sxs-lookup"><span data-stu-id="ea55a-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="ea55a-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="ea55a-538">创建用于生成模拟的数据包并将它们传递到提供的接收器对象上。</span><span class="sxs-lookup"><span data-stu-id="ea55a-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="ea55a-539">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-539">Parameters</span></span>
* <span data-ttu-id="ea55a-540">接收器的接收器将接收生成的所有数据包。</span><span class="sxs-lookup"><span data-stu-id="ea55a-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="ea55a-541">返回值</span><span class="sxs-lookup"><span data-stu-id="ea55a-541">Return value</span></span>

<span data-ttu-id="ea55a-542">创建管理器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-542">The created Manager.</span></span>

<span data-ttu-id="ea55a-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="ea55a-544">创建接收器将接收的所有数据包存储在指定的路径的文件中。</span><span class="sxs-lookup"><span data-stu-id="ea55a-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="ea55a-545">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-545">Parameters</span></span>
* <span data-ttu-id="ea55a-546">路径-要创建的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="ea55a-546">path - The path of the file to create.</span></span>

<span data-ttu-id="ea55a-547">返回值</span><span class="sxs-lookup"><span data-stu-id="ea55a-547">Return value</span></span>

<span data-ttu-id="ea55a-548">创建的接收器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-548">The created sink.</span></span>

<span data-ttu-id="ea55a-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="ea55a-550">从指定的文件加载录制。</span><span class="sxs-lookup"><span data-stu-id="ea55a-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="ea55a-551">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-551">Parameters</span></span>
* <span data-ttu-id="ea55a-552">路径-要加载的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="ea55a-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="ea55a-553">工厂-记录用于创建 ISimulationStreamSink 时所需的工厂。</span><span class="sxs-lookup"><span data-stu-id="ea55a-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="ea55a-554">返回值</span><span class="sxs-lookup"><span data-stu-id="ea55a-554">Return value</span></span>

<span data-ttu-id="ea55a-555">加载的记录。</span><span class="sxs-lookup"><span data-stu-id="ea55a-555">The loaded recording.</span></span>

<span data-ttu-id="ea55a-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory，Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="ea55a-557">从指定的文件加载录制。</span><span class="sxs-lookup"><span data-stu-id="ea55a-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="ea55a-558">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-558">Parameters</span></span>
* <span data-ttu-id="ea55a-559">路径-要加载的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="ea55a-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="ea55a-560">工厂-记录用于创建 ISimulationStreamSink 时所需的工厂。</span><span class="sxs-lookup"><span data-stu-id="ea55a-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="ea55a-561">callback-回调接收更新 regrading 录制的状态。</span><span class="sxs-lookup"><span data-stu-id="ea55a-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="ea55a-562">返回值</span><span class="sxs-lookup"><span data-stu-id="ea55a-562">Return value</span></span>

<span data-ttu-id="ea55a-563">加载的记录。</span><span class="sxs-lookup"><span data-stu-id="ea55a-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="ea55a-564">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="ea55a-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="ea55a-565">介绍不同类型的流数据。</span><span class="sxs-lookup"><span data-stu-id="ea55a-565">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    All = None | Head | Hands | SpatialMapping | Calibration | Environment
}
```

<span data-ttu-id="ea55a-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="ea55a-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="ea55a-567">用来指示没有流数据类型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="ea55a-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="ea55a-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="ea55a-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="ea55a-569">Stream 的位置和方向的头有关的数据。</span><span class="sxs-lookup"><span data-stu-id="ea55a-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="ea55a-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="ea55a-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="ea55a-571">有关位置和手势动手操作的数据的 Stream。</span><span class="sxs-lookup"><span data-stu-id="ea55a-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="ea55a-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="ea55a-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="ea55a-573">有关环境的空间映射的数据的 Stream。</span><span class="sxs-lookup"><span data-stu-id="ea55a-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="ea55a-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="ea55a-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="ea55a-575">有关设备的校准数据 Stream。</span><span class="sxs-lookup"><span data-stu-id="ea55a-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="ea55a-576">通过在远程模式下的系统仅接受校准数据包。</span><span class="sxs-lookup"><span data-stu-id="ea55a-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="ea55a-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="ea55a-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="ea55a-578">有关设备的环境数据的 Stream。</span><span class="sxs-lookup"><span data-stu-id="ea55a-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="ea55a-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="ea55a-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="ea55a-580">用来指示所有记录的数据类型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="ea55a-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="ea55a-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="ea55a-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="ea55a-582">从模拟流接收数据包的对象。</span><span class="sxs-lookup"><span data-stu-id="ea55a-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="ea55a-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="ea55a-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="ea55a-584">接收单个数据包，这是在内部类型和版本控制。</span><span class="sxs-lookup"><span data-stu-id="ea55a-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="ea55a-585">Parameters</span><span class="sxs-lookup"><span data-stu-id="ea55a-585">Parameters</span></span>
* <span data-ttu-id="ea55a-586">length-数据包的长度。</span><span class="sxs-lookup"><span data-stu-id="ea55a-586">length - The length of the packet.</span></span>
* <span data-ttu-id="ea55a-587">数据包的数据包的数据。</span><span class="sxs-lookup"><span data-stu-id="ea55a-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="ea55a-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="ea55a-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="ea55a-589">一个对象，创建 ISimulationStreamSink。</span><span class="sxs-lookup"><span data-stu-id="ea55a-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="ea55a-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="ea55a-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="ea55a-591">创建 ISimulationStreamSink 的单一实例。</span><span class="sxs-lookup"><span data-stu-id="ea55a-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="ea55a-592">返回值</span><span class="sxs-lookup"><span data-stu-id="ea55a-592">Return value</span></span>

<span data-ttu-id="ea55a-593">创建的接收器。</span><span class="sxs-lookup"><span data-stu-id="ea55a-593">The created sink.</span></span>
