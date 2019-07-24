---
title: 感知模拟
description: 使用感知模拟库自动完成沉浸式应用程序模拟输入的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, 模拟, 测试
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414534"
---
# <a name="perception-simulation"></a><span data-ttu-id="f4d7e-104">感知模拟</span><span class="sxs-lookup"><span data-stu-id="f4d7e-104">Perception simulation</span></span>

<span data-ttu-id="f4d7e-105">是否要为应用生成自动测试？</span><span class="sxs-lookup"><span data-stu-id="f4d7e-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="f4d7e-106">是否希望你的测试超出组件级别的单元测试, 并真正运用端到端应用？</span><span class="sxs-lookup"><span data-stu-id="f4d7e-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="f4d7e-107">感知模拟是你要查找的内容。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="f4d7e-108">感知模拟库将人类和世界输入数据发送到你的应用, 因此你可以自动执行测试。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="f4d7e-109">例如, 可以模拟查找特定的可重复位置, 然后执行笔势或使用运动控制器的人工输入。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="f4d7e-110">感知模拟可以将此类模拟输入发送到物理 HoloLens、HoloLens 模拟器 (第一代)、HoloLens 2 模拟器或安装有混合现实门户的 PC。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="f4d7e-111">感知模拟会绕过混合现实设备上的实时传感器, 并将模拟输入发送到设备上运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="f4d7e-112">应用程序通过它们始终使用的相同 Api 来接收这些输入事件, 不能判断使用实际传感器运行与通过感知模拟运行的情况之间的区别。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="f4d7e-113">认知模拟是将模拟输入发送到 HoloLens 虚拟机所使用的一种技术。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="f4d7e-114">若要开始在代码中使用模拟, 请首先创建 IPerceptionSimulationManager 对象。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="f4d7e-115">在该对象中, 可以发出命令来控制模拟 "人体" 的属性, 包括头位置、手形位置和手势, 还可以启用和操作运动控制器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="f4d7e-116">设置用于感知模拟的 Visual Studio 项目</span><span class="sxs-lookup"><span data-stu-id="f4d7e-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="f4d7e-117">在开发电脑上[安装 HoloLens 模拟器](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="f4d7e-118">模拟器包含用于感知模拟的库。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="f4d7e-119">创建新的 Visual Studio C#桌面项目 (控制台项目非常适合入门)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="f4d7e-120">将以下二进制文件作为引用添加到你的项目中 (项目 > 添加 > 引用 ...)。可在% ProgramFiles (x86)% \ microsoft XDE\\(版本) 中找到这些文件, 如用于 HoloLens 2 模拟器的% **ProgramFiles (x86\\)% \ microsoft XDE 10.0.18362.0** 。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="f4d7e-121">(注意: 尽管二进制文件是 HoloLens 2 模拟器的一部分, 但它们也适用于桌面上的 Windows Mixed Reality。)的.</span><span class="sxs-lookup"><span data-stu-id="f4d7e-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="f4d7e-122">PerceptionSimulationManager 用于感知模拟的托管C#包装。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="f4d7e-123">b.</span><span class="sxs-lookup"><span data-stu-id="f4d7e-123">b.</span></span> <span data-ttu-id="f4d7e-124">PerceptionSimulationRest-用于设置到 HoloLens 或仿真程序的 web 套接字通信通道的库。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="f4d7e-125">c.</span><span class="sxs-lookup"><span data-stu-id="f4d7e-125">c.</span></span> <span data-ttu-id="f4d7e-126">SimulationStream-模拟的共享类型。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="f4d7e-127">将实现二进制 PerceptionSimulationManager 添加到项目 a。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="f4d7e-128">首先, 将其作为二进制文件添加到项目 (项目-> 添加 > 现有项 ...)。将其保存为链接, 使其不会将其复制到项目源文件夹。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="f4d7e-129">![将 PerceptionSimulationManager 作为链接](images/saveaslink.png) b 添加到项目。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="f4d7e-130">然后, 确保它在生成时复制到输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="f4d7e-131">这位于二进制文件的属性表中。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="f4d7e-132">![将 PerceptionSimulationManager 标记为复制到输出目录](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="f4d7e-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="f4d7e-133">将活动解决方案平台设置为 x64。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="f4d7e-134">(如果尚不存在, 请使用 Configuration Manager 为 x64 创建平台条目。)</span><span class="sxs-lookup"><span data-stu-id="f4d7e-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="f4d7e-135">创建 IPerceptionSimulation Manager 对象</span><span class="sxs-lookup"><span data-stu-id="f4d7e-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="f4d7e-136">若要控制模拟, 你将对从 IPerceptionSimulationManager 对象检索到的对象进行更新。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="f4d7e-137">第一步是获取该对象, 并将其连接到目标设备或仿真程序。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="f4d7e-138">可以通过单击[工具栏](using-the-hololens-emulator.md)中的 "设备门户" 按钮来获取仿真程序的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="f4d7e-139">![打开设备门户图标](images/emulator-deviceportal.png) **打开设备门户**:在仿真器中打开 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="f4d7e-140">对于 Windows Mixed Reality, 可以在 "设置" 应用程序中的 "更新 & 安全性" 下检索此项, 然后在 "启用设备门户" 下的 "连接使用:" 部分中的 "开发人员"。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="f4d7e-141">请务必记下 IP 地址和端口。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="f4d7e-142">首先, 调用 RestSimulationStreamSink 来获取 RestSimulationStreamSink 对象。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="f4d7e-143">这是你将通过 http 连接控制的目标设备或仿真程序。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="f4d7e-144">命令将传递到设备或模拟器上运行的[Windows 设备门户](using-the-windows-device-portal.md)并进行处理。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="f4d7e-145">创建对象需要四个参数:</span><span class="sxs-lookup"><span data-stu-id="f4d7e-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="f4d7e-146">Uri uri-目标设备的 IP 地址 (例如, "http://123.123.123.123" 或 "http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="f4d7e-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="f4d7e-147">系统 NetworkCredential 凭据-用于在目标设备或模拟器上连接到[Windows 设备门户](using-the-windows-device-portal.md)的用户名/密码。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="f4d7e-148">如果要通过其本地地址 (例如,*168 ...* \*) 在同一台计算机上, 将接受任何凭据。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="f4d7e-149">布尔标准-对于普通优先级为 True, 低优先级为 false。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="f4d7e-150">通常, 你需要将此值设置为*true* , 以便测试方案允许你的测试进行控制。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="f4d7e-151">仿真程序和 Windows Mixed Reality 模拟使用低优先级连接。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="f4d7e-152">如果你的测试也使用低优先级连接, 则最近建立的连接将处于控制中。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="f4d7e-153">CancellationToken 标记-用于取消异步操作的标记。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="f4d7e-154">然后, 将创建 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="f4d7e-155">这是用于控制模拟的对象。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="f4d7e-156">请注意, 也必须在异步方法中完成此操作。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="f4d7e-157">控制模拟的人工</span><span class="sxs-lookup"><span data-stu-id="f4d7e-157">Control the simulated Human</span></span>

<span data-ttu-id="f4d7e-158">IPerceptionSimulationManager 具有返回 ISimulatedHuman 对象的人属性。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="f4d7e-159">若要控制模拟人力, 请对此对象执行操作。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="f4d7e-160">例如：</span><span class="sxs-lookup"><span data-stu-id="f4d7e-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="f4d7e-161">基本示例C#控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="f4d7e-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="f4d7e-162">扩展示例C#控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="f4d7e-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="f4d7e-163">DOF 控制器上的注意事项</span><span class="sxs-lookup"><span data-stu-id="f4d7e-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="f4d7e-164">在模拟 DOF 控制器上调用方法的任何属性之前, 必须激活控制器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="f4d7e-165">如果不这样做, 将导致异常。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="f4d7e-166">从 Windows 10 可能2019更新开始, 可以通过将 ISimulatedSixDofController 对象的 Status 属性设置为 SimulatedSixDofControllerStatus, 来安装和激活模拟的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="f4d7e-167">在 Windows 10 2018 10 月版更新及更早版本中, 必须先通过调用 \Windows\System32 文件夹中的 PerceptionSimulationDevice 工具单独安装模拟的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="f4d7e-168">此工具的用法如下所示:</span><span class="sxs-lookup"><span data-stu-id="f4d7e-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="f4d7e-169">例如</span><span class="sxs-lookup"><span data-stu-id="f4d7e-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="f4d7e-170">支持的操作包括:</span><span class="sxs-lookup"><span data-stu-id="f4d7e-170">Supported actions are:</span></span>
* <span data-ttu-id="f4d7e-171">i = 安装</span><span class="sxs-lookup"><span data-stu-id="f4d7e-171">i = install</span></span>
* <span data-ttu-id="f4d7e-172">q = 查询</span><span class="sxs-lookup"><span data-stu-id="f4d7e-172">q = query</span></span>
* <span data-ttu-id="f4d7e-173">r = 删除</span><span class="sxs-lookup"><span data-stu-id="f4d7e-173">r = remove</span></span>

<span data-ttu-id="f4d7e-174">支持的实例包括:</span><span class="sxs-lookup"><span data-stu-id="f4d7e-174">Supported instances are:</span></span>
* <span data-ttu-id="f4d7e-175">1 = 左 6-DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="f4d7e-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="f4d7e-176">2 = 右 6-DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="f4d7e-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="f4d7e-177">该进程的退出代码将指示成功 (零返回值) 或失败 (非零返回值)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="f4d7e-178">当使用 "q" 操作来查询控制器是否已安装时, 如果尚未安装控制器, 则返回值将为零 (0); 如果已安装控制器, 则返回1。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="f4d7e-179">在 Windows 10 2018 10 月更新版或更早版本上删除控制器时, 请先通过 API 将其状态设置为 Off, 然后调用 PerceptionSimulationDevice 工具。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="f4d7e-180">请注意, 必须以管理员身份运行此工具。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="f4d7e-181">API 参考</span><span class="sxs-lookup"><span data-stu-id="f4d7e-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="f4d7e-182">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="f4d7e-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="f4d7e-183">描述模拟设备类型</span><span class="sxs-lookup"><span data-stu-id="f4d7e-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="f4d7e-184">**PerceptionSimulation. SimulatedDeviceType. 引用**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="f4d7e-185">虚构引用设备, PerceptionSimulationManager 的默认值</span><span class="sxs-lookup"><span data-stu-id="f4d7e-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="f4d7e-186">PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="f4d7e-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="f4d7e-187">描述 head 跟踪器模式</span><span class="sxs-lookup"><span data-stu-id="f4d7e-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="f4d7e-188">**PerceptionSimulation. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="f4d7e-189">默认标题跟踪。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-189">Default Head Tracking.</span></span> <span data-ttu-id="f4d7e-190">这意味着系统可能会根据运行时条件选择最佳的标题跟踪模式。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="f4d7e-191">**PerceptionSimulation. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="f4d7e-192">仅定向到头跟踪。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="f4d7e-193">这意味着跟踪的位置可能不可靠, 并且某些依赖于头位置的功能可能不可用。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="f4d7e-194">**PerceptionSimulation. HeadTrackerMode. 位置**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="f4d7e-195">位置标题跟踪。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-195">Positional Head Tracking.</span></span> <span data-ttu-id="f4d7e-196">这意味着跟踪的头位置和方向都是可靠的</span><span class="sxs-lookup"><span data-stu-id="f4d7e-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="f4d7e-197">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="f4d7e-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="f4d7e-198">描述模拟手势</span><span class="sxs-lookup"><span data-stu-id="f4d7e-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="f4d7e-199">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="f4d7e-200">用于指示没有笔势的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="f4d7e-201">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="f4d7e-202">手指按下的手势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-202">A finger pressed gesture.</span></span>

<span data-ttu-id="f4d7e-203">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="f4d7e-204">用手指释放的手势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-204">A finger released gesture.</span></span>

<span data-ttu-id="f4d7e-205">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="f4d7e-206">Home/system 手势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-206">The home/system gesture.</span></span>

<span data-ttu-id="f4d7e-207">**PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="f4d7e-208">最大有效手势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="f4d7e-209">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="f4d7e-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="f4d7e-210">模拟 6 DOF 控制器的可能状态。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="f4d7e-211">**PerceptionSimulation. SimulatedSixDofControllerStatus。**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="f4d7e-212">6-DOF 控制器已关闭。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="f4d7e-213">**PerceptionSimulation. SimulatedSixDofControllerStatus。**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="f4d7e-214">6-DOF 控制器已打开并进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="f4d7e-215">**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="f4d7e-216">6-DOF 控制器已打开, 但无法跟踪。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="f4d7e-217">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="f4d7e-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="f4d7e-218">模拟 6 DOF 控制器上支持的按钮。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="f4d7e-219">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="f4d7e-220">用于指示没有按钮的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="f4d7e-221">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="f4d7e-222">"主页" 按钮处于按下状态。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-222">The Home button is pressed.</span></span>

<span data-ttu-id="f4d7e-223">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="f4d7e-224">按下菜单按钮。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-224">The Menu button is pressed.</span></span>

<span data-ttu-id="f4d7e-225">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="f4d7e-226">按下 "手柄" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-226">The Grip button is pressed.</span></span>

<span data-ttu-id="f4d7e-227">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="f4d7e-228">触摸板已按下。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="f4d7e-229">**PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="f4d7e-230">按 "选择" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-230">The Select button is pressed.</span></span>

<span data-ttu-id="f4d7e-231">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="f4d7e-232">触摸板接触。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-232">The TouchPad is touched.</span></span>

<span data-ttu-id="f4d7e-233">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="f4d7e-234">已按下操纵杆。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="f4d7e-235">**PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="f4d7e-236">"最大有效" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="f4d7e-237">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="f4d7e-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="f4d7e-238">模拟眼睛的校准状态</span><span class="sxs-lookup"><span data-stu-id="f4d7e-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="f4d7e-239">**PerceptionSimulation. SimulatedEyesCalibrationState. 不可用**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="f4d7e-240">眼睛校准不可用。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="f4d7e-241">**PerceptionSimulation. SimulatedEyesCalibrationState。**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="f4d7e-242">眼睛已经校准。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="f4d7e-243">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-243">This is the default value.</span></span>

<span data-ttu-id="f4d7e-244">**PerceptionSimulation. SimulatedEyesCalibrationState. 配置**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="f4d7e-245">正在校准眼睛。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="f4d7e-246">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="f4d7e-247">需要校准眼睛。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="f4d7e-248">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="f4d7e-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="f4d7e-249">手的接点的跟踪准确性。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="f4d7e-250">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 不可用**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="f4d7e-251">不跟踪联合。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-251">The joint is not tracked.</span></span>

<span data-ttu-id="f4d7e-252">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="f4d7e-253">将推断联合位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-253">The joint position is inferred.</span></span>

<span data-ttu-id="f4d7e-254">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy。**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="f4d7e-255">将完全跟踪联合。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="f4d7e-256">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="f4d7e-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="f4d7e-257">手的接点的跟踪准确性。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="f4d7e-258">**PerceptionSimulation. SimulatedHandPose. 关闭**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="f4d7e-259">手的 finger 接头被配置为反映闭合的姿势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="f4d7e-260">**PerceptionSimulation. SimulatedHandPose。**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="f4d7e-261">触接头的配置以反映开放姿势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="f4d7e-262">**PerceptionSimulation. SimulatedHandPose. 点**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="f4d7e-263">触接头的配置以反映一个指示。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="f4d7e-264">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="f4d7e-265">触接头的配置以反映收缩的姿势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="f4d7e-266">**PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="f4d7e-267">SimulatedHandPose 的最大有效值。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="f4d7e-268">PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="f4d7e-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="f4d7e-269">描述播放的状态。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="f4d7e-270">**PerceptionSimulation. PlaybackState. 已停止**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="f4d7e-271">录制当前已停止, 可供播放。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="f4d7e-272">**PerceptionSimulation. PlaybackState**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="f4d7e-273">当前正在播放记录。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-273">The recording is currently playing.</span></span>

<span data-ttu-id="f4d7e-274">**PerceptionSimulation. PlaybackState. 暂停**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="f4d7e-275">当前已暂停录制。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-275">The recording is currently paused.</span></span>

<span data-ttu-id="f4d7e-276">**PerceptionSimulation. PlaybackState. 结束**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="f4d7e-277">记录已结束。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="f4d7e-278">PerceptionSimulation. System.numerics.vector2</span><span class="sxs-lookup"><span data-stu-id="f4d7e-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="f4d7e-279">介绍3个分量向量, 它可能会在三维空间中描述点或向量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="f4d7e-280">**PerceptionSimulation. System.numerics.vector2. X**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="f4d7e-281">向量的 X 分量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-281">The X component of the vector.</span></span>

<span data-ttu-id="f4d7e-282">**PerceptionSimulation. System.numerics.vector2**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="f4d7e-283">向量的 Y 分量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-283">The Y component of the vector.</span></span>

<span data-ttu-id="f4d7e-284">**PerceptionSimulation. System.numerics.vector2. Z**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="f4d7e-285">向量的 Z 分量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-285">The Z component of the vector.</span></span>

<span data-ttu-id="f4d7e-286">**PerceptionSimulation. System.numerics.vector2. #ctor (System.web, system.web, system.web)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="f4d7e-287">构造一个新的 System.numerics.vector2。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-287">Construct a new Vector3.</span></span>

<span data-ttu-id="f4d7e-288">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-288">Parameters</span></span>
* <span data-ttu-id="f4d7e-289">x-向量的 x 分量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="f4d7e-290">y-向量的 y 分量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="f4d7e-291">z-矢量的 z 分量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="f4d7e-292">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="f4d7e-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="f4d7e-293">介绍3个组件旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="f4d7e-294">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="f4d7e-295">旋转的螺距分量, 围绕 X 轴向下旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="f4d7e-296">**PerceptionSimulation. Rotation3. 偏航**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="f4d7e-297">旋转的偏航组件, 绕 Y 轴旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="f4d7e-298">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="f4d7e-299">围绕 Z 轴旋转的滚动部分。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="f4d7e-300">**PerceptionSimulation. Rotation3. #ctor (System.web, system.web, system.web)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="f4d7e-301">构造一个新的 Rotation3。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="f4d7e-302">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-302">Parameters</span></span>
* <span data-ttu-id="f4d7e-303">螺距-旋转的螺距部分。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="f4d7e-304">偏航-旋转的偏航组件。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="f4d7e-305">滚动-旋转的滚动组件。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="f4d7e-306">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="f4d7e-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="f4d7e-307">描述模拟手上的接点配置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="f4d7e-308">**PerceptionSimulation. SimulatedHandJointConfiguration. 位置**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="f4d7e-309">接点的位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-309">The position of the joint.</span></span>

<span data-ttu-id="f4d7e-310">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="f4d7e-311">接点的旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-311">The rotation of the joint.</span></span>

<span data-ttu-id="f4d7e-312">**PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="f4d7e-313">联合的跟踪准确性。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="f4d7e-314">PerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="f4d7e-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="f4d7e-315">描述通常由相机使用的视图 (如)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="f4d7e-316">**PerceptionSimulation。**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="f4d7e-317">在锥上包含的最小距离。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="f4d7e-318">**PerceptionSimulation. Far**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="f4d7e-319">在锥中包含的最大距离。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="f4d7e-320">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="f4d7e-321">以弧度表示的 (小于 PI) 的以弧度表示的视图的水平字段。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="f4d7e-322">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="f4d7e-323">视图的水平字段与视图的垂直字段的比率。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="f4d7e-324">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f4d7e-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="f4d7e-325">用于生成用于控制设备的数据包的根。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="f4d7e-326">**PerceptionSimulation. IPerceptionSimulationManager. 设备**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="f4d7e-327">检索用于解释模拟人类和模拟世界的模拟设备对象。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="f4d7e-328">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="f4d7e-329">检索控制模拟人的对象。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="f4d7e-330">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="f4d7e-331">将模拟重置为其默认状态。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="f4d7e-332">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="f4d7e-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="f4d7e-333">描述用于解释模拟世界和模拟人类的设备的接口</span><span class="sxs-lookup"><span data-stu-id="f4d7e-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="f4d7e-334">**PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="f4d7e-335">从模拟设备检索 Head 跟踪器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="f4d7e-336">**PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="f4d7e-337">从模拟设备检索手动跟踪器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="f4d7e-338">**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="f4d7e-339">设置模拟设备的属性, 使其与所提供的设备类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="f4d7e-340">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-340">Parameters</span></span>
* <span data-ttu-id="f4d7e-341">类型-新类型的模拟设备</span><span class="sxs-lookup"><span data-stu-id="f4d7e-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="f4d7e-342">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="f4d7e-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="f4d7e-343">描述模拟设备的部分的接口, 该部分跟踪模拟人的头。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="f4d7e-344">**PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="f4d7e-345">检索和设置当前 head 跟踪器模式。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="f4d7e-346">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="f4d7e-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="f4d7e-347">描述模拟设备的部分的接口, 该部分跟踪模拟人的手</span><span class="sxs-lookup"><span data-stu-id="f4d7e-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="f4d7e-348">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="f4d7e-349">检索与世界相关的节点的位置 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f4d7e-350">**PerceptionSimulation. ISimulatedHandTracker. 位置**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="f4d7e-351">检索和设置模拟手型跟踪器的位置 (相对于打印头的中心)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="f4d7e-352">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="f4d7e-353">检索和设置模拟手型跟踪器的下间距。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="f4d7e-354">**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="f4d7e-355">检索和设置是否忽略模拟手动跟踪器的 "截锥"。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="f4d7e-356">如果忽略, 则这两个指针始终可见。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="f4d7e-357">如果未被忽略 (默认值), 则只有在 "手形跟踪器" 的 "截锥" 中时才会显示。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="f4d7e-358">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="f4d7e-359">检索和设置用来确定是否对模拟手型跟踪器可见的被截锥属性。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="f4d7e-360">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="f4d7e-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="f4d7e-361">用于控制模拟人的顶级接口。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="f4d7e-362">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="f4d7e-363">检索和设置与世界相关的节点的位置 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="f4d7e-364">此位置对应于人脚的中心点。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="f4d7e-365">**PerceptionSimulation. ISimulatedHuman。**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="f4d7e-366">检索和设置模拟人脸在世界中的方向。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="f4d7e-367">0弧度朝下 Z 轴向下。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="f4d7e-368">正弧度围绕 Y 轴顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="f4d7e-369">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="f4d7e-370">检索和设置模拟人的高度 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="f4d7e-371">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="f4d7e-372">检索模拟人的左侧。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="f4d7e-373">**PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="f4d7e-374">检索模拟人的右边。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="f4d7e-375">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="f4d7e-376">检索模拟人的 head。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="f4d7e-377">**PerceptionSimulation. ISimulatedHuman (PerceptionSimulation. System.numerics.vector2)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f4d7e-378">以米为单位移动模拟人工相对于其当前位置的位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="f4d7e-379">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-379">Parameters</span></span>
* <span data-ttu-id="f4d7e-380">平移-要移动的转换, 相对于当前位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="f4d7e-381">**PerceptionSimulation. ISimulatedHuman (System.web)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="f4d7e-382">围绕 Y 轴顺时针旋转模拟人工相对于其当前方向</span><span class="sxs-lookup"><span data-stu-id="f4d7e-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="f4d7e-383">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-383">Parameters</span></span>
* <span data-ttu-id="f4d7e-384">radians-绕 Y 轴旋转的量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="f4d7e-385">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="f4d7e-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="f4d7e-386">可以通过将 ISimulatedHuman 转换为 ISimulatedHuman2 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="f4d7e-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="f4d7e-387">**PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="f4d7e-388">检索左 6-DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="f4d7e-389">**PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="f4d7e-390">检索正确的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="f4d7e-391">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="f4d7e-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="f4d7e-392">描述模拟人类</span><span class="sxs-lookup"><span data-stu-id="f4d7e-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="f4d7e-393">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="f4d7e-394">检索与世界相关的节点的位置 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f4d7e-395">**PerceptionSimulation. ISimulatedHand. 位置**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="f4d7e-396">检索和设置模拟手型相对于人类的位置 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="f4d7e-397">**PerceptionSimulation. ISimulatedHand. 已激活**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="f4d7e-398">检索和设置当前是否已激活该手型。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="f4d7e-399">**PerceptionSimulation. ISimulatedHand。**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="f4d7e-400">检索 SimulatedDevice 当前是否对可见 (即, 该手形是否处于 HandTracker 检测到的位置)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="f4d7e-401">\**PerceptionSimulation. ISimulatedHand. Ensurevisible\**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="f4d7e-402">移动手使其对 SimulatedDevice 可见。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="f4d7e-403">**PerceptionSimulation. ISimulatedHand (PerceptionSimulation. System.numerics.vector2)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f4d7e-404">以米为单位移动模拟手型相对于其当前位置的位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="f4d7e-405">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-405">Parameters</span></span>
* <span data-ttu-id="f4d7e-406">翻译-模拟手的平移量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="f4d7e-407">**PerceptionSimulation. ISimulatedHand. PerformGesture (PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="f4d7e-408">使用模拟手执行手势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="f4d7e-409">只有在启用了该功能的情况, 系统才会检测到它。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="f4d7e-410">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-410">Parameters</span></span>
* <span data-ttu-id="f4d7e-411">手势-要执行的手势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="f4d7e-412">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="f4d7e-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="f4d7e-413">可以通过将 ISimulatedHand 转换为 ISimulatedHand2 来获取其他属性。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="f4d7e-414">**PerceptionSimulation. ISimulatedHand2**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="f4d7e-415">检索或设置模拟手的旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="f4d7e-416">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="f4d7e-417">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="f4d7e-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="f4d7e-418">可以通过将 ISimulatedHand 转换为 ISimulatedHand3 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="f4d7e-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="f4d7e-419">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="f4d7e-420">获取指定的联合的联合配置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="f4d7e-421">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="f4d7e-422">设置指定的联合的联合配置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="f4d7e-423">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="f4d7e-424">使用可选的动画标志将手设置为已知姿势。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="f4d7e-425">注意: 动画效果不会立即反映其最终的联合配置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="f4d7e-426">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="f4d7e-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="f4d7e-427">描述模拟人的头的接口。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="f4d7e-428">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="f4d7e-429">检索与世界相关的节点的位置 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f4d7e-430">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="f4d7e-431">检索模拟头部的旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="f4d7e-432">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f4d7e-433">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="f4d7e-434">检索模拟头直径。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="f4d7e-435">此值用于确定头的中心 (旋转点)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="f4d7e-436">**PerceptionSimulation. ISimulatedHead (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="f4d7e-437">相对于当前旋转旋转模拟头。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="f4d7e-438">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f4d7e-439">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-439">Parameters</span></span>
* <span data-ttu-id="f4d7e-440">旋转-要旋转的量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="f4d7e-441">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="f4d7e-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="f4d7e-442">可以通过将 ISimulatedHead 转换为 ISimulatedHead2 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="f4d7e-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="f4d7e-443">**PerceptionSimulation. ISimulatedHead2**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="f4d7e-444">检索模拟人的眼睛。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="f4d7e-445">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="f4d7e-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="f4d7e-446">描述与模拟人类关联的 6 DOF 控制器的接口。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="f4d7e-447">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="f4d7e-448">检索与世界相关的节点的位置 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f4d7e-449">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="f4d7e-450">检索或设置控制器的当前状态。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="f4d7e-451">在任何调用移动、旋转或按下按钮之前, 控制器状态必须设置为 Off 以外的值。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="f4d7e-452">**PerceptionSimulation. ISimulatedSixDofController. 位置**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="f4d7e-453">检索或设置模拟控制器相对于人类的位置 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="f4d7e-454">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="f4d7e-455">检索或设置模拟控制器的方向。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="f4d7e-456">**PerceptionSimulation. ISimulatedSixDofController (PerceptionSimulation. System.numerics.vector2)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f4d7e-457">移动模拟控制器相对于其当前位置的位置 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="f4d7e-458">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-458">Parameters</span></span>
* <span data-ttu-id="f4d7e-459">翻译-模拟控制器的平移量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="f4d7e-460">**PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="f4d7e-461">按模拟控制器上的按钮。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="f4d7e-462">仅当控制器已启用时, 系统才会检测到该控制器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="f4d7e-463">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-463">Parameters</span></span>
* <span data-ttu-id="f4d7e-464">按钮-要按下的按钮。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-464">button - The button to press.</span></span>

<span data-ttu-id="f4d7e-465">**PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="f4d7e-466">释放模拟控制器上的按钮。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="f4d7e-467">仅当控制器已启用时, 系统才会检测到该控制器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="f4d7e-468">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-468">Parameters</span></span>
* <span data-ttu-id="f4d7e-469">按钮-要释放的按钮。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-469">button - The button to release.</span></span>

<span data-ttu-id="f4d7e-470">**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="f4d7e-471">获取模拟手指在模拟控制器的触摸板上的位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="f4d7e-472">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-472">Parameters</span></span>
* <span data-ttu-id="f4d7e-473">x-手指的水平位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="f4d7e-474">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="f4d7e-475">**PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="f4d7e-476">设置模拟手指在模拟控制器的触摸板上的位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="f4d7e-477">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-477">Parameters</span></span>
* <span data-ttu-id="f4d7e-478">x-手指的水平位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="f4d7e-479">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="f4d7e-480">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="f4d7e-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="f4d7e-481">可以通过将 ISimulatedSixDofController 转换为 ISimulatedSixDofController2 来提供其他属性和方法。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="f4d7e-482">**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="f4d7e-483">获取模拟操纵杆在模拟控制器上的位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="f4d7e-484">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-484">Parameters</span></span>
* <span data-ttu-id="f4d7e-485">x-操纵杆的水平位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="f4d7e-486">y-操纵杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="f4d7e-487">**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="f4d7e-488">设置模拟操纵杆在模拟控制器上的位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="f4d7e-489">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-489">Parameters</span></span>
* <span data-ttu-id="f4d7e-490">x-操纵杆的水平位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="f4d7e-491">y-操纵杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="f4d7e-492">**PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="f4d7e-493">检索或设置模拟控制器的电池电量级别。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="f4d7e-494">该值必须大于0.0 且小于或等于100.0。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="f4d7e-495">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="f4d7e-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="f4d7e-496">描述模拟人力的眼睛的接口。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="f4d7e-497">**PerceptionSimulation. ISimulatedEyes**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="f4d7e-498">检索模拟眼睛的旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="f4d7e-499">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f4d7e-500">**PerceptionSimulation. ISimulatedEyes (PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="f4d7e-501">相对于当前旋转旋转模拟眼睛。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="f4d7e-502">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f4d7e-503">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-503">Parameters</span></span>
* <span data-ttu-id="f4d7e-504">旋转-要旋转的量。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="f4d7e-505">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="f4d7e-506">检索或设置模拟眼睛的校准状态。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="f4d7e-507">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="f4d7e-508">检索与世界相关的节点的位置 (以米为单位)。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="f4d7e-509">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="f4d7e-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="f4d7e-510">用于与为播放加载的单个录制交互的接口。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="f4d7e-511">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="f4d7e-512">检索记录中数据类型的列表。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="f4d7e-513">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="f4d7e-514">检索当前记录的状态。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="f4d7e-515">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="f4d7e-516">开始播放。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-516">Start the playback.</span></span> <span data-ttu-id="f4d7e-517">如果记录已暂停, 播放将从暂停位置恢复;如果停止, 则将从开始处开始播放。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="f4d7e-518">如果已播放, 则忽略此调用。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="f4d7e-519">**PerceptionSimulation. ISimulationRecording. 暂停**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="f4d7e-520">暂停播放当前位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="f4d7e-521">如果记录已停止, 则调用将被忽略。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="f4d7e-522">**PerceptionSimulation. ISimulationRecording (system.string)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="f4d7e-523">将记录查找到指定时间 (从开头开始, 以100毫微秒为间隔), 并在该位置暂停。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="f4d7e-524">如果该时间超出了记录的结束时间, 则会在最后一帧暂停该时间。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="f4d7e-525">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-525">Parameters</span></span>
* <span data-ttu-id="f4d7e-526">计时周期-要查找的时间。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="f4d7e-527">**PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="f4d7e-528">停止播放并将位置重置为开始位置。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="f4d7e-529">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="f4d7e-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="f4d7e-530">用于在播放期间接收状态更改的接口。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="f4d7e-531">**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="f4d7e-532">当 ISimulationRecording 的播放状态发生更改时调用。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="f4d7e-533">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-533">Parameters</span></span>
* <span data-ttu-id="f4d7e-534">newState-记录的新状态。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="f4d7e-535">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f4d7e-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="f4d7e-536">用于创建感知模拟对象的根对象。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="f4d7e-537">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="f4d7e-538">针对生成模拟包并将其传送到所提供接收器的对象创建。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="f4d7e-539">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-539">Parameters</span></span>
* <span data-ttu-id="f4d7e-540">sink-接收所有生成的数据包的接收器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="f4d7e-541">返回值</span><span class="sxs-lookup"><span data-stu-id="f4d7e-541">Return value</span></span>

<span data-ttu-id="f4d7e-542">创建的管理器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-542">The created Manager.</span></span>

<span data-ttu-id="f4d7e-543">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System.string)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="f4d7e-544">创建一个接收器, 将所有接收的数据包存储在文件中的指定路径。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="f4d7e-545">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-545">Parameters</span></span>
* <span data-ttu-id="f4d7e-546">path-要创建的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-546">path - The path of the file to create.</span></span>

<span data-ttu-id="f4d7e-547">返回值</span><span class="sxs-lookup"><span data-stu-id="f4d7e-547">Return value</span></span>

<span data-ttu-id="f4d7e-548">创建的接收器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-548">The created sink.</span></span>

<span data-ttu-id="f4d7e-549">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System.string, PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="f4d7e-550">从指定的文件加载记录。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="f4d7e-551">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-551">Parameters</span></span>
* <span data-ttu-id="f4d7e-552">path-要加载的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="f4d7e-553">工厂-记录用于在需要时创建 ISimulationStreamSink 的工厂。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="f4d7e-554">返回值</span><span class="sxs-lookup"><span data-stu-id="f4d7e-554">Return value</span></span>

<span data-ttu-id="f4d7e-555">加载的记录。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-555">The loaded recording.</span></span>

<span data-ttu-id="f4d7e-556">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (PerceptionSimulation, ISimulationStreamSinkFactory,PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="f4d7e-557">从指定的文件加载记录。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="f4d7e-558">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-558">Parameters</span></span>
* <span data-ttu-id="f4d7e-559">path-要加载的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="f4d7e-560">工厂-记录用于在需要时创建 ISimulationStreamSink 的工厂。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="f4d7e-561">回叫-在记录状态 regrading 接收更新的回调。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="f4d7e-562">返回值</span><span class="sxs-lookup"><span data-stu-id="f4d7e-562">Return value</span></span>

<span data-ttu-id="f4d7e-563">加载的记录。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="f4d7e-564">PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="f4d7e-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="f4d7e-565">描述不同类型的流数据。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="f4d7e-566">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="f4d7e-567">用于指示没有流数据类型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="f4d7e-568">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="f4d7e-569">与头部位置和方向相关的数据流。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="f4d7e-570">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="f4d7e-571">有关指针位置和手势的数据流。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="f4d7e-572">**PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="f4d7e-573">有关环境的空间映射的数据流。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="f4d7e-574">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="f4d7e-575">与设备的校准相关的数据流。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="f4d7e-576">只有远程模式下的系统才会接受校准数据包。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="f4d7e-577">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="f4d7e-578">有关设备环境的数据流。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="f4d7e-579">**PerceptionSimulation. StreamDataTypes。**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="f4d7e-580">用于指示所有记录的数据类型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="f4d7e-581">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="f4d7e-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="f4d7e-582">从模拟流接收数据包的对象。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="f4d7e-583">**PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint length, byte [] packet)**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="f4d7e-584">接收单个数据包, 该数据包在内部键入并进行版本控制。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="f4d7e-585">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4d7e-585">Parameters</span></span>
* <span data-ttu-id="f4d7e-586">length-数据包的长度。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-586">length - The length of the packet.</span></span>
* <span data-ttu-id="f4d7e-587">数据包-包的数据。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="f4d7e-588">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="f4d7e-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="f4d7e-589">用于创建 ISimulationStreamSink 的对象。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="f4d7e-590">**PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="f4d7e-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="f4d7e-591">创建 ISimulationStreamSink 的单个实例。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="f4d7e-592">返回值</span><span class="sxs-lookup"><span data-stu-id="f4d7e-592">Return value</span></span>

<span data-ttu-id="f4d7e-593">创建的接收器。</span><span class="sxs-lookup"><span data-stu-id="f4d7e-593">The created sink.</span></span>
