---
title: Perception 模拟
description: 如何使用 Perception 模拟库来自动执行模拟的输入的沉浸式应用程序的指南
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，模拟，测试
ms.openlocfilehash: 693750eb753bd11cbe7d7cfb47e04f1a3506ca9a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592426"
---
# <a name="perception-simulation"></a><span data-ttu-id="f129b-104">Perception 模拟</span><span class="sxs-lookup"><span data-stu-id="f129b-104">Perception simulation</span></span>

<span data-ttu-id="f129b-105">若要生成你的应用的自动的测试吗？</span><span class="sxs-lookup"><span data-stu-id="f129b-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="f129b-106">超越组件级的单元测试和实际练习你的应用程序端到端测试吗？</span><span class="sxs-lookup"><span data-stu-id="f129b-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="f129b-107">Perception 模拟是要查找的内容。</span><span class="sxs-lookup"><span data-stu-id="f129b-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="f129b-108">这样可以自动执行测试，Perception 模拟库会向应用发送假人工和世界的输入的数据。</span><span class="sxs-lookup"><span data-stu-id="f129b-108">The Perception Simulation library sends fake human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="f129b-109">例如，可以模拟人查找左右，然后再执行一个手势的输入。</span><span class="sxs-lookup"><span data-stu-id="f129b-109">For example, you can simulate the input of a human looking left and right and then performing a gesture.</span></span>

<span data-ttu-id="f129b-110">Perception 模拟可以将此类的模拟的输入发送到物理 HoloLens、 HoloLens 仿真程序中或安装的混合现实门户的 PC。</span><span class="sxs-lookup"><span data-stu-id="f129b-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="f129b-111">Perception 模拟绕过混合现实设备上的实时传感器并发送模拟设备上运行的应用程序的输入。</span><span class="sxs-lookup"><span data-stu-id="f129b-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="f129b-112">应用程序收到这些假的输入的事件，通过它们始终使用和不能确定它们与实际传感器与运行与 Perception 模拟运行之间的区别相同的 Api。</span><span class="sxs-lookup"><span data-stu-id="f129b-112">Applications receive these fake input events through the same APIs they always use, and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="f129b-113">Perception 模拟是 HoloLens 仿真程序用于发送模拟的输入到 HoloLens 虚拟机的相同技术。</span><span class="sxs-lookup"><span data-stu-id="f129b-113">Perception Simulation is the same technology used by the HoloLens emulator to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="f129b-114">通过创建 IPerceptionSimulationManager 对象启动模拟。</span><span class="sxs-lookup"><span data-stu-id="f129b-114">Simulation starts by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="f129b-115">从该对象，您可以发出命令来控制模拟"人"，包括头位置、 手位置和手势的属性。</span><span class="sxs-lookup"><span data-stu-id="f129b-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="f129b-116">为 Perception 模拟设置 Visual Studio 项目</span><span class="sxs-lookup"><span data-stu-id="f129b-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="f129b-117">[安装 HoloLens 模拟器](install-the-tools.md)开发计算机上。</span><span class="sxs-lookup"><span data-stu-id="f129b-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="f129b-118">在仿真程序包含将用于对模拟的库。</span><span class="sxs-lookup"><span data-stu-id="f129b-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="f129b-119">创建新的 Visual StudioC#桌面 （控制台项目运行良好开始） 的项目。</span><span class="sxs-lookup"><span data-stu-id="f129b-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="f129b-120">将以下二进制文件作为引用添加到你的项目 (项目-> 添加-> 引用...)。您可以找到它们中 **%programfiles (x86) %\Microsoft XDE\10.0.11082.0** 。</span><span class="sxs-lookup"><span data-stu-id="f129b-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in **%ProgramFiles(x86)%\Microsoft XDE\10.0.11082.0** a.</span></span> <span data-ttu-id="f129b-121">PerceptionSimulationManager.Interop.dll-管理C#Perception 模拟的包装器。</span><span class="sxs-lookup"><span data-stu-id="f129b-121">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="f129b-122">b.</span><span class="sxs-lookup"><span data-stu-id="f129b-122">b.</span></span> <span data-ttu-id="f129b-123">PerceptionSimulationRest.dll-设置 web 套接字通信通道到 HoloLens 或仿真器的库。</span><span class="sxs-lookup"><span data-stu-id="f129b-123">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="f129b-124">c.</span><span class="sxs-lookup"><span data-stu-id="f129b-124">c.</span></span> <span data-ttu-id="f129b-125">SimulationStream.Interop.dll-共享类型进行模拟。</span><span class="sxs-lookup"><span data-stu-id="f129b-125">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="f129b-126">将实现添加到你的项目二进制 PerceptionSimulationManager.dll。</span><span class="sxs-lookup"><span data-stu-id="f129b-126">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="f129b-127">首先将其作为二进制文件添加到项目 (项目-> 添加-> 现有项...)。将其保存为一个链接，以便它不会将其复制到你的项目源文件夹。</span><span class="sxs-lookup"><span data-stu-id="f129b-127">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="f129b-128">![向项目的链接的形式添加 PerceptionSimulationManager.dll](images/saveaslink.png) b。</span><span class="sxs-lookup"><span data-stu-id="f129b-128">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="f129b-129">请确保它获取的复制到生成输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f129b-129">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="f129b-130">这是二进制文件的属性表中。</span><span class="sxs-lookup"><span data-stu-id="f129b-130">This is in the property sheet for the binary .</span></span> <span data-ttu-id="f129b-131">![将标记 PerceptionSimulationManager.dll 将复制到输出目录](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="f129b-131">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="f129b-132">创建 IPerceptionSimulation Manager 对象</span><span class="sxs-lookup"><span data-stu-id="f129b-132">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="f129b-133">若要控制模拟，将从 IPerceptionSimulationManager 对象检索到的对象发布更新。</span><span class="sxs-lookup"><span data-stu-id="f129b-133">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="f129b-134">第一步是获取该对象，并将其连接到目标设备或仿真程序。</span><span class="sxs-lookup"><span data-stu-id="f129b-134">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="f129b-135">可以通过单击在设备门户按钮获取仿真程序的 IP 地址[工具栏](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span><span class="sxs-lookup"><span data-stu-id="f129b-135">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span></span>

<span data-ttu-id="f129b-136">![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**:为 HoloLens 操作系统在模拟器中打开 Windows Device Portal。</span><span class="sxs-lookup"><span data-stu-id="f129b-136">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

<span data-ttu-id="f129b-137">首先，将调用 RestSimulationStreamSink.Create 获取 RestSimulationStreamSink 对象。</span><span class="sxs-lookup"><span data-stu-id="f129b-137">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="f129b-138">这是目标设备或仿真程序将控制通过 http 连接。</span><span class="sxs-lookup"><span data-stu-id="f129b-138">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="f129b-139">将传递给你的命令，并将其由处理[Windows Device Portal](using-the-windows-device-portal.md)设备或仿真器上运行。</span><span class="sxs-lookup"><span data-stu-id="f129b-139">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="f129b-140">将需要创建一个对象的四个参数是：</span><span class="sxs-lookup"><span data-stu-id="f129b-140">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="f129b-141">Uri uri-目标设备的 IP 地址 (例如，"http://123.123.123.123")</span><span class="sxs-lookup"><span data-stu-id="f129b-141">Uri uri - IP address of the target device (e.g., "http://123.123.123.123")</span></span>
* <span data-ttu-id="f129b-142">System.Net.NetworkCredential 凭据-用户名/密码用于连接到[Windows Device Portal](using-the-windows-device-portal.md)目标设备或仿真程序上。</span><span class="sxs-lookup"><span data-stu-id="f129b-142">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="f129b-143">如果要连接到其本地 168 通过仿真程序。*.*。 \* 地址将在同一台 PC 上接受任何凭据。</span><span class="sxs-lookup"><span data-stu-id="f129b-143">If you are connecting to the emulator via its local 168.*.*.\* address on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="f129b-144">正常情况-bool 的普通优先级低优先级为 false，则返回 True。</span><span class="sxs-lookup"><span data-stu-id="f129b-144">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="f129b-145">你通常想要将其设置为 *，则返回 true*的测试方案。</span><span class="sxs-lookup"><span data-stu-id="f129b-145">You generally want to set this to *true* for test scenarios.</span></span>
* <span data-ttu-id="f129b-146">System.Threading.CancellationToken 令牌-令牌取消异步操作。</span><span class="sxs-lookup"><span data-stu-id="f129b-146">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="f129b-147">其次，您将创建 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="f129b-147">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="f129b-148">这是用于控制模拟的对象。</span><span class="sxs-lookup"><span data-stu-id="f129b-148">This is the object you use to control simulation.</span></span> <span data-ttu-id="f129b-149">请注意这必须还将完成的异步方法中。</span><span class="sxs-lookup"><span data-stu-id="f129b-149">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="f129b-150">控制模拟的用户</span><span class="sxs-lookup"><span data-stu-id="f129b-150">Control the simulated Human</span></span>

<span data-ttu-id="f129b-151">IPerceptionSimulationManager 有一个人属性可返回 ISimulatedHuman 对象。</span><span class="sxs-lookup"><span data-stu-id="f129b-151">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="f129b-152">若要控制模拟的用户，请执行此对象上的操作。</span><span class="sxs-lookup"><span data-stu-id="f129b-152">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="f129b-153">例如：</span><span class="sxs-lookup"><span data-stu-id="f129b-153">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="f129b-154">基本示例C#控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="f129b-154">Basic Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="f129b-155">扩展示例C#控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="f129b-155">Extended Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

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
        }
    }
}
```

## <a name="api-reference"></a><span data-ttu-id="f129b-156">API 参考</span><span class="sxs-lookup"><span data-stu-id="f129b-156">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="f129b-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="f129b-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="f129b-158">介绍一种模拟的设备类型</span><span class="sxs-lookup"><span data-stu-id="f129b-158">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="f129b-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="f129b-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="f129b-160">虚构引用设备的默认值为 PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f129b-160">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="f129b-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="f129b-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="f129b-162">头跟踪器模式下运行</span><span class="sxs-lookup"><span data-stu-id="f129b-162">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="f129b-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="f129b-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="f129b-164">默认跟踪头。</span><span class="sxs-lookup"><span data-stu-id="f129b-164">Default Head Tracking.</span></span> <span data-ttu-id="f129b-165">这意味着，系统可能会选择跟踪模式下运行时条件基于最佳头。</span><span class="sxs-lookup"><span data-stu-id="f129b-165">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="f129b-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="f129b-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="f129b-167">方向仅头跟踪。</span><span class="sxs-lookup"><span data-stu-id="f129b-167">Orientation Only Head Tracking.</span></span> <span data-ttu-id="f129b-168">这意味着跟踪的位置可能不可靠，并依赖于头位置某些功能可能不可用。</span><span class="sxs-lookup"><span data-stu-id="f129b-168">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="f129b-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="f129b-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="f129b-170">位置头跟踪。</span><span class="sxs-lookup"><span data-stu-id="f129b-170">Positional Head Tracking.</span></span> <span data-ttu-id="f129b-171">这意味着，跟踪头位置和方向都是可靠</span><span class="sxs-lookup"><span data-stu-id="f129b-171">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="f129b-172">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="f129b-172">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="f129b-173">介绍模拟的手势</span><span class="sxs-lookup"><span data-stu-id="f129b-173">Describes a simulated gesture</span></span>

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

<span data-ttu-id="f129b-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="f129b-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="f129b-175">用来指示没有手势的 sentinel 值</span><span class="sxs-lookup"><span data-stu-id="f129b-175">A sentinel value used to indicate no gestures</span></span>

<span data-ttu-id="f129b-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="f129b-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="f129b-177">手指按下的手势</span><span class="sxs-lookup"><span data-stu-id="f129b-177">A finger pressed gesture</span></span>

<span data-ttu-id="f129b-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="f129b-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="f129b-179">发布的手指手势</span><span class="sxs-lookup"><span data-stu-id="f129b-179">A finger released gesture</span></span>

<span data-ttu-id="f129b-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="f129b-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="f129b-181">家庭手势</span><span class="sxs-lookup"><span data-stu-id="f129b-181">The home gesture</span></span>

<span data-ttu-id="f129b-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="f129b-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="f129b-183">最大有效的手势</span><span class="sxs-lookup"><span data-stu-id="f129b-183">The maximum valid gesture</span></span>

### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="f129b-184">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="f129b-184">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="f129b-185">描述状态的播放</span><span class="sxs-lookup"><span data-stu-id="f129b-185">Describes the state of a playback</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="f129b-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="f129b-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="f129b-187">记录当前处于已停止，并准备好进行播放</span><span class="sxs-lookup"><span data-stu-id="f129b-187">The recording is currently stopped and ready for playback</span></span>

<span data-ttu-id="f129b-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="f129b-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="f129b-189">当前播放该录制</span><span class="sxs-lookup"><span data-stu-id="f129b-189">The recording is currently playing</span></span>

<span data-ttu-id="f129b-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="f129b-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="f129b-191">当前已暂停录制</span><span class="sxs-lookup"><span data-stu-id="f129b-191">The recording is currently paused</span></span>

<span data-ttu-id="f129b-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="f129b-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="f129b-193">记录已达到末尾</span><span class="sxs-lookup"><span data-stu-id="f129b-193">The recording has reached the end</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="f129b-194">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="f129b-194">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="f129b-195">介绍了 3 个组件矢量，可能会描述一个点或 3D 空间中的矢量</span><span class="sxs-lookup"><span data-stu-id="f129b-195">Describes a 3 components vector, which might describe a point or a vector in 3D space</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="f129b-196">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="f129b-196">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="f129b-197">向量的 X 分量</span><span class="sxs-lookup"><span data-stu-id="f129b-197">The X component of the vector</span></span>

<span data-ttu-id="f129b-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="f129b-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="f129b-199">向量的 Y 分量</span><span class="sxs-lookup"><span data-stu-id="f129b-199">The Y component of the vector</span></span>

<span data-ttu-id="f129b-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="f129b-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="f129b-201">向量的 Z 分量</span><span class="sxs-lookup"><span data-stu-id="f129b-201">The Z component of the vector</span></span>

<span data-ttu-id="f129b-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="f129b-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="f129b-203">构造新 Vector3</span><span class="sxs-lookup"><span data-stu-id="f129b-203">Construct a new Vector3</span></span>

<span data-ttu-id="f129b-204">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-204">Parameters</span></span>
* <span data-ttu-id="f129b-205">x 轴向量的 x 分量</span><span class="sxs-lookup"><span data-stu-id="f129b-205">x - The x component of the vector</span></span>
* <span data-ttu-id="f129b-206">y-y 分量的向量</span><span class="sxs-lookup"><span data-stu-id="f129b-206">y - The y component of the vector</span></span>
* <span data-ttu-id="f129b-207">z-矢量的 z 分量</span><span class="sxs-lookup"><span data-stu-id="f129b-207">z - The z component of the vector</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="f129b-208">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="f129b-208">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="f129b-209">描述的 3 个组件旋转</span><span class="sxs-lookup"><span data-stu-id="f129b-209">Describes a 3 components rotation</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="f129b-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="f129b-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="f129b-211">间距组成部分旋转、 绕 X 轴向下</span><span class="sxs-lookup"><span data-stu-id="f129b-211">The Pitch component of the Rotation, down around the X axis</span></span>

<span data-ttu-id="f129b-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="f129b-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="f129b-213">直接绕 Y 轴的旋转该偏航组件</span><span class="sxs-lookup"><span data-stu-id="f129b-213">The Yaw component of the Rotation, right around the Y axis</span></span>

<span data-ttu-id="f129b-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="f129b-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="f129b-215">直接绕 Z 轴旋转该汇总组件</span><span class="sxs-lookup"><span data-stu-id="f129b-215">The Roll component of the Rotation, right around the Z axis</span></span>

<span data-ttu-id="f129b-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="f129b-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="f129b-217">构造新 Rotation3</span><span class="sxs-lookup"><span data-stu-id="f129b-217">Construct a new Rotation3</span></span>

<span data-ttu-id="f129b-218">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-218">Parameters</span></span>
* <span data-ttu-id="f129b-219">间距的旋转的音调组件</span><span class="sxs-lookup"><span data-stu-id="f129b-219">pitch - The pitch component of the Rotation</span></span>
* <span data-ttu-id="f129b-220">偏航-旋转偏航组件</span><span class="sxs-lookup"><span data-stu-id="f129b-220">yaw - The yaw component of the Rotation</span></span>
* <span data-ttu-id="f129b-221">回滚的旋转的汇总组件</span><span class="sxs-lookup"><span data-stu-id="f129b-221">roll - The roll component of the Rotation</span></span>

### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="f129b-222">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="f129b-222">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="f129b-223">描述视图截锥，通常使用照相机</span><span class="sxs-lookup"><span data-stu-id="f129b-223">Describes a view frustum, as typically used by a camera</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="f129b-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="f129b-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="f129b-225">截锥中包含的最小距离</span><span class="sxs-lookup"><span data-stu-id="f129b-225">The minimum distance that is contained in the frustum</span></span>

<span data-ttu-id="f129b-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="f129b-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="f129b-227">截锥中包含的最大距离</span><span class="sxs-lookup"><span data-stu-id="f129b-227">The maximum distance that is contained in the frustum</span></span>

<span data-ttu-id="f129b-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="f129b-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="f129b-229">水平视图的字段的截锥，以弧度为单位 （小于 PI）</span><span class="sxs-lookup"><span data-stu-id="f129b-229">The horizontal field of view of the frustum, in radians (less than PI)</span></span>

<span data-ttu-id="f129b-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="f129b-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="f129b-231">水平视角为垂直的视野比率</span><span class="sxs-lookup"><span data-stu-id="f129b-231">The ratio of horizontal field of view to vertical field of view</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="f129b-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f129b-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="f129b-233">用于生成用来控制设备的数据包的根</span><span class="sxs-lookup"><span data-stu-id="f129b-233">Root for generating the packets used to control a device</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="f129b-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="f129b-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="f129b-235">检索将解释模拟的人类和模拟的世界的模拟的设备对象。</span><span class="sxs-lookup"><span data-stu-id="f129b-235">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="f129b-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="f129b-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="f129b-237">检索控制模拟的人类的对象。</span><span class="sxs-lookup"><span data-stu-id="f129b-237">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="f129b-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="f129b-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="f129b-239">将模拟重置为其默认状态。</span><span class="sxs-lookup"><span data-stu-id="f129b-239">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="f129b-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="f129b-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="f129b-241">接口描述将解释模拟的世界和模拟的用户的设备</span><span class="sxs-lookup"><span data-stu-id="f129b-241">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="f129b-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="f129b-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="f129b-243">从模拟设备中检索头跟踪器。</span><span class="sxs-lookup"><span data-stu-id="f129b-243">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="f129b-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="f129b-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="f129b-245">从模拟设备中检索的现有跟踪器。</span><span class="sxs-lookup"><span data-stu-id="f129b-245">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="f129b-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="f129b-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="f129b-247">设置模拟设备以提供的设备类型匹配的属性。</span><span class="sxs-lookup"><span data-stu-id="f129b-247">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="f129b-248">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-248">Parameters</span></span>
* <span data-ttu-id="f129b-249">键入的新类型的模拟设备</span><span class="sxs-lookup"><span data-stu-id="f129b-249">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="f129b-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="f129b-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="f129b-251">描述跟踪的模拟人类的模拟设备的部分接口</span><span class="sxs-lookup"><span data-stu-id="f129b-251">Interface describing the portion of the simulated device that tracks the head of the simulated human</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="f129b-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="f129b-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="f129b-253">检索并设置当前头跟踪器模式。</span><span class="sxs-lookup"><span data-stu-id="f129b-253">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="f129b-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="f129b-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="f129b-255">描述跟踪的模拟用户的手中的模拟设备的部分接口</span><span class="sxs-lookup"><span data-stu-id="f129b-255">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="f129b-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f129b-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="f129b-257">检索与世界里，相关的节点以米为单位的位置</span><span class="sxs-lookup"><span data-stu-id="f129b-257">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="f129b-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="f129b-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="f129b-259">检索和设置的模拟的手动跟踪程序，位置相对于头的中心。</span><span class="sxs-lookup"><span data-stu-id="f129b-259">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="f129b-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="f129b-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="f129b-261">检索和设置的模拟的手动跟踪器的向下音调</span><span class="sxs-lookup"><span data-stu-id="f129b-261">Retrieve and set the downward pitch of the simulated hand tracker</span></span>

<span data-ttu-id="f129b-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="f129b-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="f129b-263">检索和设置是否忽略模拟的手动跟踪器的截锥。</span><span class="sxs-lookup"><span data-stu-id="f129b-263">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="f129b-264">如果忽略，将始终显示两只手。</span><span class="sxs-lookup"><span data-stu-id="f129b-264">When ignored, both hands are always visible.</span></span> <span data-ttu-id="f129b-265">当不忽略 （默认值） 内手动跟踪器的截锥时才可见手。</span><span class="sxs-lookup"><span data-stu-id="f129b-265">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="f129b-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="f129b-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="f129b-267">检索和设置用于确定指针是否对模拟的手动跟踪器可见的截锥属性。</span><span class="sxs-lookup"><span data-stu-id="f129b-267">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="f129b-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="f129b-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="f129b-269">用于控制模拟的人类的顶部级别接口</span><span class="sxs-lookup"><span data-stu-id="f129b-269">Top level interface for controlling the simulated human</span></span>

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

<span data-ttu-id="f129b-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f129b-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="f129b-271">检索并与世界中，以米为单位相关设置的节点的位置。</span><span class="sxs-lookup"><span data-stu-id="f129b-271">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="f129b-272">位置对应于人类的英尺位于中心点。</span><span class="sxs-lookup"><span data-stu-id="f129b-272">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="f129b-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="f129b-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="f129b-274">检索并在世界中模拟的人脸设置方向。</span><span class="sxs-lookup"><span data-stu-id="f129b-274">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="f129b-275">0 弧度朝下负 Z 轴。</span><span class="sxs-lookup"><span data-stu-id="f129b-275">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="f129b-276">正弧度围绕 Y 轴顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="f129b-276">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="f129b-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="f129b-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="f129b-278">检索和设置的模拟用户的高度以米为单位</span><span class="sxs-lookup"><span data-stu-id="f129b-278">Retrieve and set the height of the simulated human, in meters</span></span>

<span data-ttu-id="f129b-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="f129b-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="f129b-280">检索模拟人类的左侧</span><span class="sxs-lookup"><span data-stu-id="f129b-280">Retrieve the left hand of the simulated human</span></span>

<span data-ttu-id="f129b-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="f129b-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="f129b-282">检索模拟人类的右侧</span><span class="sxs-lookup"><span data-stu-id="f129b-282">Retrieve the right hand of the simulated human</span></span>

<span data-ttu-id="f129b-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="f129b-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="f129b-284">检索模拟人类的开头</span><span class="sxs-lookup"><span data-stu-id="f129b-284">Retrieve the head of the simulated human</span></span>

<span data-ttu-id="f129b-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="f129b-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f129b-286">将模拟的人类移动相对于其当前的位置，以米为单位</span><span class="sxs-lookup"><span data-stu-id="f129b-286">Move the simulated human relative to its current position, in meters</span></span>

<span data-ttu-id="f129b-287">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-287">Parameters</span></span>
* <span data-ttu-id="f129b-288">翻译的移动，相对于当前的位置的翻译</span><span class="sxs-lookup"><span data-stu-id="f129b-288">translation - The translation to move, relative to current position</span></span>

<span data-ttu-id="f129b-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="f129b-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="f129b-290">模拟的人类相对于其当前方向，围绕 Y 轴顺时针旋转</span><span class="sxs-lookup"><span data-stu-id="f129b-290">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="f129b-291">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-291">Parameters</span></span>
* <span data-ttu-id="f129b-292">弧度-要围绕 Y 轴旋转的量</span><span class="sxs-lookup"><span data-stu-id="f129b-292">radians - The amount to rotate around the Y axis</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="f129b-293">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="f129b-293">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="f129b-294">接口描述模拟用户的手的形状</span><span class="sxs-lookup"><span data-stu-id="f129b-294">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="f129b-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f129b-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="f129b-296">检索与世界里，相关的节点以米为单位的位置</span><span class="sxs-lookup"><span data-stu-id="f129b-296">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="f129b-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="f129b-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="f129b-298">检索和设置以米为单位的相对于人，模拟手形图标的位置。</span><span class="sxs-lookup"><span data-stu-id="f129b-298">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="f129b-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="f129b-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="f129b-300">检索和设置是否手形图标当前处于激活状态。</span><span class="sxs-lookup"><span data-stu-id="f129b-300">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="f129b-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="f129b-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="f129b-302">检索当前可见 （即，是在一个位置可检测到的 HandTracker） SimulatedDevice 手形图标是否。</span><span class="sxs-lookup"><span data-stu-id="f129b-302">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="f129b-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="f129b-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="f129b-304">移动手形图标，以便对 SimulatedDevice 可见。</span><span class="sxs-lookup"><span data-stu-id="f129b-304">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="f129b-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="f129b-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f129b-306">移动模拟手的位置，相对于其当前的位置，以米为单位。</span><span class="sxs-lookup"><span data-stu-id="f129b-306">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="f129b-307">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-307">Parameters</span></span>
* <span data-ttu-id="f129b-308">翻译-模拟的手的平移量</span><span class="sxs-lookup"><span data-stu-id="f129b-308">translation - The amount to translate the simulated hand</span></span>

<span data-ttu-id="f129b-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="f129b-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="f129b-310">执行笔势使用模拟的手 （它就只会检测到系统手形图标已启用）。</span><span class="sxs-lookup"><span data-stu-id="f129b-310">Perform a gesture using the simulated hand (it will only be detected by the system if the hand is enabled).</span></span>

<span data-ttu-id="f129b-311">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-311">Parameters</span></span>
* <span data-ttu-id="f129b-312">手势-要执行的笔势</span><span class="sxs-lookup"><span data-stu-id="f129b-312">gesture - The gesture to perform</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="f129b-313">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="f129b-313">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="f129b-314">接口描述模拟人类的开头</span><span class="sxs-lookup"><span data-stu-id="f129b-314">Interface describing the head of the simulated human</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="f129b-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f129b-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="f129b-316">检索与世界里，相关的节点以米为单位的位置</span><span class="sxs-lookup"><span data-stu-id="f129b-316">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="f129b-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="f129b-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="f129b-318">检索模拟头的旋转。</span><span class="sxs-lookup"><span data-stu-id="f129b-318">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="f129b-319">查看该轴时，正弧度为单位的顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="f129b-319">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f129b-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="f129b-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="f129b-321">检索模拟的头直径。</span><span class="sxs-lookup"><span data-stu-id="f129b-321">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="f129b-322">此值用于确定 head 的中心 （旋转的点）。</span><span class="sxs-lookup"><span data-stu-id="f129b-322">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="f129b-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="f129b-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="f129b-324">旋转模拟的头相对于其当前的旋转。</span><span class="sxs-lookup"><span data-stu-id="f129b-324">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="f129b-325">查看该轴时，正弧度为单位的顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="f129b-325">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f129b-326">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-326">Parameters</span></span>
* <span data-ttu-id="f129b-327">旋转-要旋转的量</span><span class="sxs-lookup"><span data-stu-id="f129b-327">rotation - The amount to rotate</span></span>

### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="f129b-328">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="f129b-328">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="f129b-329">加载与单个记录进行交互的接口中进行播放。</span><span class="sxs-lookup"><span data-stu-id="f129b-329">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="f129b-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="f129b-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="f129b-331">检索在记录中的数据类型的列表。</span><span class="sxs-lookup"><span data-stu-id="f129b-331">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="f129b-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="f129b-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="f129b-333">检索记录的当前状态。</span><span class="sxs-lookup"><span data-stu-id="f129b-333">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="f129b-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="f129b-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="f129b-335">开始播放。</span><span class="sxs-lookup"><span data-stu-id="f129b-335">Start the playback.</span></span> <span data-ttu-id="f129b-336">从暂停的位置; 如果暂停录制后，将恢复播放如果停止，将开头开始播放。</span><span class="sxs-lookup"><span data-stu-id="f129b-336">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="f129b-337">如果已在播放，则忽略此调用。</span><span class="sxs-lookup"><span data-stu-id="f129b-337">If already playing, this call is ignored.</span></span>

<span data-ttu-id="f129b-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="f129b-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="f129b-339">暂停播放在其当前的位置。</span><span class="sxs-lookup"><span data-stu-id="f129b-339">Pauses the playback at its current location.</span></span> <span data-ttu-id="f129b-340">如果停止录制，则将忽略此调用。</span><span class="sxs-lookup"><span data-stu-id="f129b-340">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="f129b-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="f129b-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="f129b-342">查找在指定的时间 （以 100 纳秒间隔从一开始） 记录，并在该位置暂停。</span><span class="sxs-lookup"><span data-stu-id="f129b-342">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="f129b-343">如果所记录的末尾之外的时间，它会暂停在最后一帧。</span><span class="sxs-lookup"><span data-stu-id="f129b-343">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="f129b-344">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-344">Parameters</span></span>
* <span data-ttu-id="f129b-345">计时周期数-要查找的时间</span><span class="sxs-lookup"><span data-stu-id="f129b-345">ticks - The time to which to seek</span></span>

<span data-ttu-id="f129b-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="f129b-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="f129b-347">停止播放和位置重置到开头</span><span class="sxs-lookup"><span data-stu-id="f129b-347">Stops the playback and resets the position to the beginning</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="f129b-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="f129b-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="f129b-349">在播放期间接收状态更改的接口</span><span class="sxs-lookup"><span data-stu-id="f129b-349">Interface for receiving state changes during playback</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="f129b-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="f129b-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="f129b-351">ISimulationRecording 播放状态发生更改时调用</span><span class="sxs-lookup"><span data-stu-id="f129b-351">Called when an ISimulationRecording's playback state has changed</span></span>

<span data-ttu-id="f129b-352">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-352">Parameters</span></span>
* <span data-ttu-id="f129b-353">newState-记录的新状态</span><span class="sxs-lookup"><span data-stu-id="f129b-353">newState - The new state of the recording</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="f129b-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f129b-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="f129b-355">根对象，用于创建 Perception 模拟对象</span><span class="sxs-lookup"><span data-stu-id="f129b-355">Root object for creating Perception Simulation objects</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="f129b-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="f129b-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="f129b-357">创建用于生成模拟的数据包并将它们传递到提供的接收器对象上。</span><span class="sxs-lookup"><span data-stu-id="f129b-357">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="f129b-358">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-358">Parameters</span></span>
* <span data-ttu-id="f129b-359">接收器的接收器将接收生成的所有数据包</span><span class="sxs-lookup"><span data-stu-id="f129b-359">sink - The sink that will receive all generated packets</span></span>

<span data-ttu-id="f129b-360">返回值</span><span class="sxs-lookup"><span data-stu-id="f129b-360">Return value</span></span>

<span data-ttu-id="f129b-361">创建管理器</span><span class="sxs-lookup"><span data-stu-id="f129b-361">The created Manager</span></span>

<span data-ttu-id="f129b-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="f129b-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="f129b-363">创建接收器将接收的所有数据包存储在指定的路径的文件中。</span><span class="sxs-lookup"><span data-stu-id="f129b-363">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="f129b-364">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-364">Parameters</span></span>
* <span data-ttu-id="f129b-365">路径-要创建的文件的路径</span><span class="sxs-lookup"><span data-stu-id="f129b-365">path - The path of the file to create</span></span>

<span data-ttu-id="f129b-366">返回值</span><span class="sxs-lookup"><span data-stu-id="f129b-366">Return value</span></span>

<span data-ttu-id="f129b-367">创建的接收器</span><span class="sxs-lookup"><span data-stu-id="f129b-367">The created sink</span></span>

<span data-ttu-id="f129b-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="f129b-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="f129b-369">从指定的文件加载录制</span><span class="sxs-lookup"><span data-stu-id="f129b-369">Load a recording from the specified file</span></span>

<span data-ttu-id="f129b-370">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-370">Parameters</span></span>
* <span data-ttu-id="f129b-371">路径-要加载的文件的路径</span><span class="sxs-lookup"><span data-stu-id="f129b-371">path - The path of the file to load</span></span>
* <span data-ttu-id="f129b-372">工厂-记录用于创建 ISimulationStreamSink 时所需的工厂</span><span class="sxs-lookup"><span data-stu-id="f129b-372">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>

<span data-ttu-id="f129b-373">返回值</span><span class="sxs-lookup"><span data-stu-id="f129b-373">Return value</span></span>

<span data-ttu-id="f129b-374">加载的记录</span><span class="sxs-lookup"><span data-stu-id="f129b-374">The loaded recording</span></span>

<span data-ttu-id="f129b-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory，Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="f129b-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="f129b-376">从指定的文件加载录制</span><span class="sxs-lookup"><span data-stu-id="f129b-376">Load a recording from the specified file</span></span>

<span data-ttu-id="f129b-377">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-377">Parameters</span></span>
* <span data-ttu-id="f129b-378">路径-要加载的文件的路径</span><span class="sxs-lookup"><span data-stu-id="f129b-378">path - The path of the file to load</span></span>
* <span data-ttu-id="f129b-379">工厂-记录用于创建 ISimulationStreamSink 时所需的工厂</span><span class="sxs-lookup"><span data-stu-id="f129b-379">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>
* <span data-ttu-id="f129b-380">callback-回调接收更新 regrading 录制的状态</span><span class="sxs-lookup"><span data-stu-id="f129b-380">callback - A callback which receives updates regrading the recording's status</span></span>

<span data-ttu-id="f129b-381">返回值</span><span class="sxs-lookup"><span data-stu-id="f129b-381">Return value</span></span>

<span data-ttu-id="f129b-382">加载的记录</span><span class="sxs-lookup"><span data-stu-id="f129b-382">The loaded recording</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="f129b-383">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="f129b-383">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="f129b-384">介绍不同类型的数据进行流式传输</span><span class="sxs-lookup"><span data-stu-id="f129b-384">Describes the different types of stream data</span></span>

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

<span data-ttu-id="f129b-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="f129b-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="f129b-386">用来指示没有流数据类型的 sentinel 值</span><span class="sxs-lookup"><span data-stu-id="f129b-386">A sentinel value used to indicate no stream data types</span></span>

<span data-ttu-id="f129b-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="f129b-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="f129b-388">Stream 的位置和方向头有关的数据</span><span class="sxs-lookup"><span data-stu-id="f129b-388">Stream of data regarding the position and orientation of the head</span></span>

<span data-ttu-id="f129b-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="f129b-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="f129b-390">Stream 的有关位置和手势动手操作的数据</span><span class="sxs-lookup"><span data-stu-id="f129b-390">Stream of data regarding the position and gestures of hands</span></span>

<span data-ttu-id="f129b-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="f129b-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="f129b-392">有关环境的空间映射的数据的 Stream</span><span class="sxs-lookup"><span data-stu-id="f129b-392">Stream of data regarding spatial mapping of the environment</span></span>

<span data-ttu-id="f129b-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="f129b-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="f129b-394">有关设备的校准数据 Stream。</span><span class="sxs-lookup"><span data-stu-id="f129b-394">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="f129b-395">通过在远程模式下的系统仅接受校准数据包。</span><span class="sxs-lookup"><span data-stu-id="f129b-395">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="f129b-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="f129b-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="f129b-397">Stream 的有关设备的环境数据</span><span class="sxs-lookup"><span data-stu-id="f129b-397">Stream of data regarding the environment of the device</span></span>

<span data-ttu-id="f129b-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="f129b-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="f129b-399">用来指示所有记录的数据类型的 sentinel 值</span><span class="sxs-lookup"><span data-stu-id="f129b-399">A sentinel value used to indicate all recorded data types</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="f129b-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="f129b-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="f129b-401">从模拟流接收数据包的对象</span><span class="sxs-lookup"><span data-stu-id="f129b-401">An object that receives data packets from a simulation stream</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="f129b-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="f129b-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="f129b-403">接收单个数据包，这是在内部类型和版本控制</span><span class="sxs-lookup"><span data-stu-id="f129b-403">Receives a single packet, which is internally typed and versioned</span></span>

<span data-ttu-id="f129b-404">Parameters</span><span class="sxs-lookup"><span data-stu-id="f129b-404">Parameters</span></span>
* <span data-ttu-id="f129b-405">length-数据包的长度</span><span class="sxs-lookup"><span data-stu-id="f129b-405">length - The length of the packet</span></span>
* <span data-ttu-id="f129b-406">数据包的数据包的数据</span><span class="sxs-lookup"><span data-stu-id="f129b-406">packet - The data of the packet</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="f129b-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="f129b-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="f129b-408">一个对象，创建 ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="f129b-408">An object that creates ISimulationStreamSink</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="f129b-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="f129b-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="f129b-410">创建 ISimulationStreamSink 的单一实例</span><span class="sxs-lookup"><span data-stu-id="f129b-410">Creates a single instance of ISimulationStreamSink</span></span>

<span data-ttu-id="f129b-411">返回值</span><span class="sxs-lookup"><span data-stu-id="f129b-411">Return value</span></span>

<span data-ttu-id="f129b-412">创建的接收器</span><span class="sxs-lookup"><span data-stu-id="f129b-412">The created sink</span></span>
