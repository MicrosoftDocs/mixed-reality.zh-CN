---
title: 感知模拟
description: 使用感知模拟库自动完成沉浸式应用程序模拟输入的指南
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens，模拟，测试
ms.openlocfilehash: 701fd39490d87b70df9bd68cc99da6482d41b676
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228022"
---
# <a name="perception-simulation"></a><span data-ttu-id="666c5-104">感知模拟</span><span class="sxs-lookup"><span data-stu-id="666c5-104">Perception simulation</span></span>

<span data-ttu-id="666c5-105">是否要为应用生成自动测试？</span><span class="sxs-lookup"><span data-stu-id="666c5-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="666c5-106">是否希望你的测试超出组件级别的单元测试，并真正运用端到端应用？</span><span class="sxs-lookup"><span data-stu-id="666c5-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="666c5-107">感知模拟是你要查找的内容。</span><span class="sxs-lookup"><span data-stu-id="666c5-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="666c5-108">感知模拟库将人类和世界输入数据发送到你的应用，因此你可以自动执行测试。</span><span class="sxs-lookup"><span data-stu-id="666c5-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="666c5-109">例如，可以模拟查找特定的可重复位置，然后执行笔势或使用运动控制器的人工输入。</span><span class="sxs-lookup"><span data-stu-id="666c5-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="666c5-110">感知模拟可以将此类模拟输入发送到物理 HoloLens、HoloLens 模拟器（第一代）、HoloLens 2 模拟器或安装有混合现实门户的 PC。</span><span class="sxs-lookup"><span data-stu-id="666c5-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="666c5-111">感知模拟会绕过混合现实设备上的实时传感器，并将模拟输入发送到设备上运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="666c5-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="666c5-112">应用程序通过它们始终使用的相同 Api 来接收这些输入事件，不能判断使用实际传感器运行与通过感知模拟运行的情况之间的区别。</span><span class="sxs-lookup"><span data-stu-id="666c5-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="666c5-113">认知模拟是将模拟输入发送到 HoloLens 虚拟机所使用的一种技术。</span><span class="sxs-lookup"><span data-stu-id="666c5-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="666c5-114">若要开始在代码中使用模拟，请首先创建 IPerceptionSimulationManager 对象。</span><span class="sxs-lookup"><span data-stu-id="666c5-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="666c5-115">在该对象中，可以发出命令来控制模拟 "人体" 的属性，包括头位置、手形位置和手势，还可以启用和操作运动控制器。</span><span class="sxs-lookup"><span data-stu-id="666c5-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="666c5-116">设置用于感知模拟的 Visual Studio 项目</span><span class="sxs-lookup"><span data-stu-id="666c5-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="666c5-117">在开发电脑上[安装 HoloLens 模拟器](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="666c5-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="666c5-118">模拟器包含用于感知模拟的库。</span><span class="sxs-lookup"><span data-stu-id="666c5-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="666c5-119">创建新的 Visual Studio c # 桌面项目（控制台项目非常适合入门）。</span><span class="sxs-lookup"><span data-stu-id="666c5-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="666c5-120">将以下二进制文件作为引用添加到你的项目中（项目 >添加 >引用 ...）。可在% ProgramFiles （x86）% \ Microsoft XDE （版本）中找到这些文件 \\ ，如用于 HoloLens 2 模拟器的% **ProgramFiles （x86）% \ microsoft XDE \\ 10.0.18362.0** 。</span><span class="sxs-lookup"><span data-stu-id="666c5-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="666c5-121">（注意：尽管二进制文件是 HoloLens 2 模拟器的一部分，但它们也适用于桌面上的 Windows Mixed Reality。）的.</span><span class="sxs-lookup"><span data-stu-id="666c5-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="666c5-122">PerceptionSimulationManager 用于感知模拟的 c # 托管封装。</span><span class="sxs-lookup"><span data-stu-id="666c5-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="666c5-123">b.</span><span class="sxs-lookup"><span data-stu-id="666c5-123">b.</span></span> <span data-ttu-id="666c5-124">PerceptionSimulationRest-用于设置到 HoloLens 或仿真程序的 web 套接字通信通道的库。</span><span class="sxs-lookup"><span data-stu-id="666c5-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="666c5-125">c.</span><span class="sxs-lookup"><span data-stu-id="666c5-125">c.</span></span> <span data-ttu-id="666c5-126">SimulationStream-模拟的共享类型。</span><span class="sxs-lookup"><span data-stu-id="666c5-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="666c5-127">将实现二进制 PerceptionSimulationManager 添加到项目 a。</span><span class="sxs-lookup"><span data-stu-id="666c5-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="666c5-128">首先，将其作为二进制文件添加到项目（项目->添加 >现有项 ...）。将其保存为链接，使其不会将其复制到项目源文件夹。</span><span class="sxs-lookup"><span data-stu-id="666c5-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="666c5-129">![将 PerceptionSimulationManager 作为链接 b 添加到项目 ](images/saveaslink.png) 。</span><span class="sxs-lookup"><span data-stu-id="666c5-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="666c5-130">然后，确保它在生成时复制到输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="666c5-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="666c5-131">这位于二进制文件的属性表中。</span><span class="sxs-lookup"><span data-stu-id="666c5-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="666c5-132">![将 PerceptionSimulationManager 标记为复制到输出目录](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="666c5-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="666c5-133">将活动解决方案平台设置为 x64。</span><span class="sxs-lookup"><span data-stu-id="666c5-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="666c5-134">（如果尚不存在，请使用 Configuration Manager 为 x64 创建平台条目。）</span><span class="sxs-lookup"><span data-stu-id="666c5-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="666c5-135">创建 IPerceptionSimulation Manager 对象</span><span class="sxs-lookup"><span data-stu-id="666c5-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="666c5-136">若要控制模拟，你将对从 IPerceptionSimulationManager 对象检索到的对象进行更新。</span><span class="sxs-lookup"><span data-stu-id="666c5-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="666c5-137">第一步是获取该对象，并将其连接到目标设备或仿真程序。</span><span class="sxs-lookup"><span data-stu-id="666c5-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="666c5-138">可以通过单击[工具栏](using-the-hololens-emulator.md)中的 "设备门户" 按钮来获取仿真程序的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="666c5-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="666c5-139">![打开设备门户图标 ](images/emulator-deviceportal.png) **打开设备门户**：在模拟器中打开用于 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="666c5-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="666c5-140">对于 Windows Mixed Reality，可以在 "设置" 应用程序中的 "更新 & 安全性" 下检索此项，然后在 "启用设备门户" 下的 "连接使用：" 部分中的 "开发人员"。</span><span class="sxs-lookup"><span data-stu-id="666c5-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="666c5-141">请务必记下 IP 地址和端口。</span><span class="sxs-lookup"><span data-stu-id="666c5-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="666c5-142">首先，调用 RestSimulationStreamSink 来获取 RestSimulationStreamSink 对象。</span><span class="sxs-lookup"><span data-stu-id="666c5-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="666c5-143">这是你将通过 http 连接控制的目标设备或仿真程序。</span><span class="sxs-lookup"><span data-stu-id="666c5-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="666c5-144">命令将传递到设备或模拟器上运行的[Windows 设备门户](using-the-windows-device-portal.md)并进行处理。</span><span class="sxs-lookup"><span data-stu-id="666c5-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="666c5-145">创建对象需要四个参数：</span><span class="sxs-lookup"><span data-stu-id="666c5-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="666c5-146">Uri uri-目标设备的 IP 地址（例如，" https://123.123.123.123 " 或 " https://123.123.123.123:50080 "）</span><span class="sxs-lookup"><span data-stu-id="666c5-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="666c5-147">系统 NetworkCredential 凭据-用于在目标设备或模拟器上连接到[Windows 设备门户](using-the-windows-device-portal.md)的用户名/密码。</span><span class="sxs-lookup"><span data-stu-id="666c5-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="666c5-148">如果要通过其本地地址（例如，\*168 ...\*\*）在同一台计算机上，将接受任何凭据。</span><span class="sxs-lookup"><span data-stu-id="666c5-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="666c5-149">布尔标准-对于普通优先级为 True，低优先级为 false。</span><span class="sxs-lookup"><span data-stu-id="666c5-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="666c5-150">通常，你需要将此值设置为*true* ，以便测试方案允许你的测试进行控制。</span><span class="sxs-lookup"><span data-stu-id="666c5-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="666c5-151">仿真程序和 Windows Mixed Reality 模拟使用低优先级连接。</span><span class="sxs-lookup"><span data-stu-id="666c5-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="666c5-152">如果你的测试也使用低优先级连接，则最近建立的连接将处于控制中。</span><span class="sxs-lookup"><span data-stu-id="666c5-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="666c5-153">CancellationToken 标记-用于取消异步操作的标记。</span><span class="sxs-lookup"><span data-stu-id="666c5-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="666c5-154">然后，将创建 IPerceptionSimulationManager。</span><span class="sxs-lookup"><span data-stu-id="666c5-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="666c5-155">这是用于控制模拟的对象。</span><span class="sxs-lookup"><span data-stu-id="666c5-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="666c5-156">请注意，也必须在异步方法中完成此操作。</span><span class="sxs-lookup"><span data-stu-id="666c5-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="666c5-157">控制模拟的人工</span><span class="sxs-lookup"><span data-stu-id="666c5-157">Control the simulated Human</span></span>

<span data-ttu-id="666c5-158">IPerceptionSimulationManager 具有返回 ISimulatedHuman 对象的人属性。</span><span class="sxs-lookup"><span data-stu-id="666c5-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="666c5-159">若要控制模拟人力，请对此对象执行操作。</span><span class="sxs-lookup"><span data-stu-id="666c5-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="666c5-160">例如：</span><span class="sxs-lookup"><span data-stu-id="666c5-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="666c5-161">基本示例 c # 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="666c5-161">Basic Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="666c5-162">扩展的示例 c # 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="666c5-162">Extended Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="666c5-163">DOF 控制器上的注意事项</span><span class="sxs-lookup"><span data-stu-id="666c5-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="666c5-164">在模拟 DOF 控制器上调用方法的任何属性之前，必须激活控制器。</span><span class="sxs-lookup"><span data-stu-id="666c5-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="666c5-165">如果不这样做，将导致异常。</span><span class="sxs-lookup"><span data-stu-id="666c5-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="666c5-166">从 Windows 10 可能2019更新开始，可以通过将 ISimulatedSixDofController 对象的 Status 属性设置为 SimulatedSixDofControllerStatus，来安装和激活模拟的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="666c5-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="666c5-167">在 Windows 10 2018 10 月版更新及更早版本中，必须先通过调用 \Windows\System32 文件夹中的 PerceptionSimulationDevice 工具单独安装模拟的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="666c5-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="666c5-168">此工具的用法如下所示：</span><span class="sxs-lookup"><span data-stu-id="666c5-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="666c5-169">例如</span><span class="sxs-lookup"><span data-stu-id="666c5-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="666c5-170">支持的操作包括：</span><span class="sxs-lookup"><span data-stu-id="666c5-170">Supported actions are:</span></span>
* <span data-ttu-id="666c5-171">i = 安装</span><span class="sxs-lookup"><span data-stu-id="666c5-171">i = install</span></span>
* <span data-ttu-id="666c5-172">q = 查询</span><span class="sxs-lookup"><span data-stu-id="666c5-172">q = query</span></span>
* <span data-ttu-id="666c5-173">r = 删除</span><span class="sxs-lookup"><span data-stu-id="666c5-173">r = remove</span></span>

<span data-ttu-id="666c5-174">支持的实例包括：</span><span class="sxs-lookup"><span data-stu-id="666c5-174">Supported instances are:</span></span>
* <span data-ttu-id="666c5-175">1 = 左 6-DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="666c5-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="666c5-176">2 = 右 6-DOF 控制器</span><span class="sxs-lookup"><span data-stu-id="666c5-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="666c5-177">该进程的退出代码将指示成功（零返回值）或失败（非零返回值）。</span><span class="sxs-lookup"><span data-stu-id="666c5-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="666c5-178">当使用 "q" 操作来查询控制器是否已安装时，如果尚未安装控制器，则返回值将为零（0）; 如果已安装控制器，则返回1。</span><span class="sxs-lookup"><span data-stu-id="666c5-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="666c5-179">在 Windows 10 2018 10 月更新版或更早版本上删除控制器时，请先通过 API 将其状态设置为 Off，然后调用 PerceptionSimulationDevice 工具。</span><span class="sxs-lookup"><span data-stu-id="666c5-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="666c5-180">请注意，必须以管理员身份运行此工具。</span><span class="sxs-lookup"><span data-stu-id="666c5-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="666c5-181">API 参考</span><span class="sxs-lookup"><span data-stu-id="666c5-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="666c5-182">PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="666c5-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="666c5-183">描述模拟设备类型</span><span class="sxs-lookup"><span data-stu-id="666c5-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="666c5-184">**PerceptionSimulation. SimulatedDeviceType. 引用**</span><span class="sxs-lookup"><span data-stu-id="666c5-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="666c5-185">虚构引用设备，PerceptionSimulationManager 的默认值</span><span class="sxs-lookup"><span data-stu-id="666c5-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="666c5-186">PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="666c5-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="666c5-187">描述 head 跟踪器模式</span><span class="sxs-lookup"><span data-stu-id="666c5-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="666c5-188">**PerceptionSimulation. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="666c5-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="666c5-189">默认标题跟踪。</span><span class="sxs-lookup"><span data-stu-id="666c5-189">Default Head Tracking.</span></span> <span data-ttu-id="666c5-190">这意味着系统可能会根据运行时条件选择最佳的标题跟踪模式。</span><span class="sxs-lookup"><span data-stu-id="666c5-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="666c5-191">**PerceptionSimulation. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="666c5-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="666c5-192">仅定向到头跟踪。</span><span class="sxs-lookup"><span data-stu-id="666c5-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="666c5-193">这意味着跟踪的位置可能不可靠，并且某些依赖于头位置的功能可能不可用。</span><span class="sxs-lookup"><span data-stu-id="666c5-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="666c5-194">**PerceptionSimulation. HeadTrackerMode. 位置**</span><span class="sxs-lookup"><span data-stu-id="666c5-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="666c5-195">位置标题跟踪。</span><span class="sxs-lookup"><span data-stu-id="666c5-195">Positional Head Tracking.</span></span> <span data-ttu-id="666c5-196">这意味着跟踪的头位置和方向都是可靠的</span><span class="sxs-lookup"><span data-stu-id="666c5-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="666c5-197">PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="666c5-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="666c5-198">描述模拟手势</span><span class="sxs-lookup"><span data-stu-id="666c5-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="666c5-199">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="666c5-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="666c5-200">用于指示没有笔势的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="666c5-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="666c5-201">**PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="666c5-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="666c5-202">手指按下的手势。</span><span class="sxs-lookup"><span data-stu-id="666c5-202">A finger pressed gesture.</span></span>

<span data-ttu-id="666c5-203">**PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="666c5-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="666c5-204">用手指释放的手势。</span><span class="sxs-lookup"><span data-stu-id="666c5-204">A finger released gesture.</span></span>

<span data-ttu-id="666c5-205">**PerceptionSimulation. SimulatedGesture**</span><span class="sxs-lookup"><span data-stu-id="666c5-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="666c5-206">Home/system 手势。</span><span class="sxs-lookup"><span data-stu-id="666c5-206">The home/system gesture.</span></span>

<span data-ttu-id="666c5-207">**PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="666c5-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="666c5-208">最大有效手势。</span><span class="sxs-lookup"><span data-stu-id="666c5-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="666c5-209">PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="666c5-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="666c5-210">模拟 6 DOF 控制器的可能状态。</span><span class="sxs-lookup"><span data-stu-id="666c5-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="666c5-211">**PerceptionSimulation. SimulatedSixDofControllerStatus。**</span><span class="sxs-lookup"><span data-stu-id="666c5-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="666c5-212">6-DOF 控制器已关闭。</span><span class="sxs-lookup"><span data-stu-id="666c5-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="666c5-213">**PerceptionSimulation. SimulatedSixDofControllerStatus。**</span><span class="sxs-lookup"><span data-stu-id="666c5-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="666c5-214">6-DOF 控制器已打开并进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="666c5-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="666c5-215">**PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="666c5-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="666c5-216">6-DOF 控制器已打开，但无法跟踪。</span><span class="sxs-lookup"><span data-stu-id="666c5-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="666c5-217">PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="666c5-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="666c5-218">模拟 6 DOF 控制器上支持的按钮。</span><span class="sxs-lookup"><span data-stu-id="666c5-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="666c5-219">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="666c5-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="666c5-220">用于指示没有按钮的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="666c5-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="666c5-221">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="666c5-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="666c5-222">"主页" 按钮处于按下状态。</span><span class="sxs-lookup"><span data-stu-id="666c5-222">The Home button is pressed.</span></span>

<span data-ttu-id="666c5-223">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="666c5-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="666c5-224">按下菜单按钮。</span><span class="sxs-lookup"><span data-stu-id="666c5-224">The Menu button is pressed.</span></span>

<span data-ttu-id="666c5-225">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="666c5-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="666c5-226">按下 "手柄" 按钮。</span><span class="sxs-lookup"><span data-stu-id="666c5-226">The Grip button is pressed.</span></span>

<span data-ttu-id="666c5-227">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="666c5-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="666c5-228">触摸板已按下。</span><span class="sxs-lookup"><span data-stu-id="666c5-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="666c5-229">**PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="666c5-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="666c5-230">按 "选择" 按钮。</span><span class="sxs-lookup"><span data-stu-id="666c5-230">The Select button is pressed.</span></span>

<span data-ttu-id="666c5-231">**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="666c5-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="666c5-232">触摸板接触。</span><span class="sxs-lookup"><span data-stu-id="666c5-232">The TouchPad is touched.</span></span>

<span data-ttu-id="666c5-233">**PerceptionSimulation. SimulatedSixDofControllerButton**</span><span class="sxs-lookup"><span data-stu-id="666c5-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="666c5-234">已按下操纵杆。</span><span class="sxs-lookup"><span data-stu-id="666c5-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="666c5-235">**PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="666c5-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="666c5-236">"最大有效" 按钮。</span><span class="sxs-lookup"><span data-stu-id="666c5-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="666c5-237">PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="666c5-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="666c5-238">模拟眼睛的校准状态</span><span class="sxs-lookup"><span data-stu-id="666c5-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="666c5-239">**PerceptionSimulation. SimulatedEyesCalibrationState. 不可用**</span><span class="sxs-lookup"><span data-stu-id="666c5-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="666c5-240">眼睛校准不可用。</span><span class="sxs-lookup"><span data-stu-id="666c5-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="666c5-241">**PerceptionSimulation. SimulatedEyesCalibrationState。**</span><span class="sxs-lookup"><span data-stu-id="666c5-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="666c5-242">眼睛已经校准。</span><span class="sxs-lookup"><span data-stu-id="666c5-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="666c5-243">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="666c5-243">This is the default value.</span></span>

<span data-ttu-id="666c5-244">**PerceptionSimulation. SimulatedEyesCalibrationState. 配置**</span><span class="sxs-lookup"><span data-stu-id="666c5-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="666c5-245">正在校准眼睛。</span><span class="sxs-lookup"><span data-stu-id="666c5-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="666c5-246">**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="666c5-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="666c5-247">需要校准眼睛。</span><span class="sxs-lookup"><span data-stu-id="666c5-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="666c5-248">PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="666c5-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="666c5-249">手的接点的跟踪准确性。</span><span class="sxs-lookup"><span data-stu-id="666c5-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="666c5-250">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy. 不可用**</span><span class="sxs-lookup"><span data-stu-id="666c5-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="666c5-251">不跟踪联合。</span><span class="sxs-lookup"><span data-stu-id="666c5-251">The joint is not tracked.</span></span>

<span data-ttu-id="666c5-252">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="666c5-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="666c5-253">将推断联合位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-253">The joint position is inferred.</span></span>

<span data-ttu-id="666c5-254">**PerceptionSimulation. SimulatedHandJointTrackingAccuracy。**</span><span class="sxs-lookup"><span data-stu-id="666c5-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="666c5-255">将完全跟踪联合。</span><span class="sxs-lookup"><span data-stu-id="666c5-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="666c5-256">PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="666c5-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="666c5-257">手的接点的跟踪准确性。</span><span class="sxs-lookup"><span data-stu-id="666c5-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="666c5-258">**PerceptionSimulation. SimulatedHandPose. 关闭**</span><span class="sxs-lookup"><span data-stu-id="666c5-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="666c5-259">手的 finger 接头被配置为反映闭合的姿势。</span><span class="sxs-lookup"><span data-stu-id="666c5-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="666c5-260">**PerceptionSimulation. SimulatedHandPose。**</span><span class="sxs-lookup"><span data-stu-id="666c5-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="666c5-261">触接头的配置以反映开放姿势。</span><span class="sxs-lookup"><span data-stu-id="666c5-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="666c5-262">**PerceptionSimulation. SimulatedHandPose. 点**</span><span class="sxs-lookup"><span data-stu-id="666c5-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="666c5-263">触接头的配置以反映一个指示。</span><span class="sxs-lookup"><span data-stu-id="666c5-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="666c5-264">**PerceptionSimulation. SimulatedHandPose**</span><span class="sxs-lookup"><span data-stu-id="666c5-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="666c5-265">触接头的配置以反映收缩的姿势。</span><span class="sxs-lookup"><span data-stu-id="666c5-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="666c5-266">**PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="666c5-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="666c5-267">SimulatedHandPose 的最大有效值。</span><span class="sxs-lookup"><span data-stu-id="666c5-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="666c5-268">PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="666c5-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="666c5-269">描述播放的状态。</span><span class="sxs-lookup"><span data-stu-id="666c5-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="666c5-270">**PerceptionSimulation. PlaybackState. 已停止**</span><span class="sxs-lookup"><span data-stu-id="666c5-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="666c5-271">录制当前已停止，可供播放。</span><span class="sxs-lookup"><span data-stu-id="666c5-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="666c5-272">**PerceptionSimulation. PlaybackState**</span><span class="sxs-lookup"><span data-stu-id="666c5-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="666c5-273">当前正在播放记录。</span><span class="sxs-lookup"><span data-stu-id="666c5-273">The recording is currently playing.</span></span>

<span data-ttu-id="666c5-274">**PerceptionSimulation. PlaybackState. 暂停**</span><span class="sxs-lookup"><span data-stu-id="666c5-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="666c5-275">当前已暂停录制。</span><span class="sxs-lookup"><span data-stu-id="666c5-275">The recording is currently paused.</span></span>

<span data-ttu-id="666c5-276">**PerceptionSimulation. PlaybackState. 结束**</span><span class="sxs-lookup"><span data-stu-id="666c5-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="666c5-277">记录已结束。</span><span class="sxs-lookup"><span data-stu-id="666c5-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="666c5-278">PerceptionSimulation. System.numerics.vector2</span><span class="sxs-lookup"><span data-stu-id="666c5-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="666c5-279">介绍3个分量向量，它可能会在三维空间中描述点或向量。</span><span class="sxs-lookup"><span data-stu-id="666c5-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="666c5-280">**PerceptionSimulation. System.numerics.vector2. X**</span><span class="sxs-lookup"><span data-stu-id="666c5-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="666c5-281">向量的 X 分量。</span><span class="sxs-lookup"><span data-stu-id="666c5-281">The X component of the vector.</span></span>

<span data-ttu-id="666c5-282">**PerceptionSimulation. System.numerics.vector2**</span><span class="sxs-lookup"><span data-stu-id="666c5-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="666c5-283">向量的 Y 分量。</span><span class="sxs-lookup"><span data-stu-id="666c5-283">The Y component of the vector.</span></span>

<span data-ttu-id="666c5-284">**PerceptionSimulation. System.numerics.vector2. Z**</span><span class="sxs-lookup"><span data-stu-id="666c5-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="666c5-285">向量的 Z 分量。</span><span class="sxs-lookup"><span data-stu-id="666c5-285">The Z component of the vector.</span></span>

<span data-ttu-id="666c5-286">**PerceptionSimulation. System.numerics.vector2. #ctor （System.web，system.web，system.web）**</span><span class="sxs-lookup"><span data-stu-id="666c5-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="666c5-287">构造一个新的 System.numerics.vector2。</span><span class="sxs-lookup"><span data-stu-id="666c5-287">Construct a new Vector3.</span></span>

<span data-ttu-id="666c5-288">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-288">Parameters</span></span>
* <span data-ttu-id="666c5-289">x-向量的 x 分量。</span><span class="sxs-lookup"><span data-stu-id="666c5-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="666c5-290">y-向量的 y 分量。</span><span class="sxs-lookup"><span data-stu-id="666c5-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="666c5-291">z-矢量的 z 分量。</span><span class="sxs-lookup"><span data-stu-id="666c5-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="666c5-292">PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="666c5-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="666c5-293">介绍3个组件旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="666c5-294">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="666c5-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="666c5-295">旋转的螺距分量，围绕 X 轴向下旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="666c5-296">**PerceptionSimulation. Rotation3. 偏航**</span><span class="sxs-lookup"><span data-stu-id="666c5-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="666c5-297">旋转的偏航组件，绕 Y 轴旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="666c5-298">**PerceptionSimulation. Rotation3**</span><span class="sxs-lookup"><span data-stu-id="666c5-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="666c5-299">围绕 Z 轴旋转的滚动部分。</span><span class="sxs-lookup"><span data-stu-id="666c5-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="666c5-300">**PerceptionSimulation. Rotation3. #ctor （System.web，system.web，system.web）**</span><span class="sxs-lookup"><span data-stu-id="666c5-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="666c5-301">构造一个新的 Rotation3。</span><span class="sxs-lookup"><span data-stu-id="666c5-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="666c5-302">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-302">Parameters</span></span>
* <span data-ttu-id="666c5-303">螺距-旋转的螺距部分。</span><span class="sxs-lookup"><span data-stu-id="666c5-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="666c5-304">偏航-旋转的偏航组件。</span><span class="sxs-lookup"><span data-stu-id="666c5-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="666c5-305">滚动-旋转的滚动组件。</span><span class="sxs-lookup"><span data-stu-id="666c5-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="666c5-306">PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="666c5-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="666c5-307">描述模拟手上的接点配置。</span><span class="sxs-lookup"><span data-stu-id="666c5-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="666c5-308">**PerceptionSimulation. SimulatedHandJointConfiguration. 位置**</span><span class="sxs-lookup"><span data-stu-id="666c5-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="666c5-309">接点的位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-309">The position of the joint.</span></span>

<span data-ttu-id="666c5-310">**PerceptionSimulation. SimulatedHandJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="666c5-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="666c5-311">接点的旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-311">The rotation of the joint.</span></span>

<span data-ttu-id="666c5-312">**PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="666c5-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="666c5-313">联合的跟踪准确性。</span><span class="sxs-lookup"><span data-stu-id="666c5-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="666c5-314">PerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="666c5-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="666c5-315">描述通常由相机使用的视图（如）。</span><span class="sxs-lookup"><span data-stu-id="666c5-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="666c5-316">**PerceptionSimulation。**</span><span class="sxs-lookup"><span data-stu-id="666c5-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="666c5-317">在锥上包含的最小距离。</span><span class="sxs-lookup"><span data-stu-id="666c5-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="666c5-318">**PerceptionSimulation. Far**</span><span class="sxs-lookup"><span data-stu-id="666c5-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="666c5-319">在锥中包含的最大距离。</span><span class="sxs-lookup"><span data-stu-id="666c5-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="666c5-320">**PerceptionSimulation. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="666c5-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="666c5-321">以弧度表示的（小于 PI）的以弧度表示的视图的水平字段。</span><span class="sxs-lookup"><span data-stu-id="666c5-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="666c5-322">**PerceptionSimulation. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="666c5-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="666c5-323">视图的水平字段与视图的垂直字段的比率。</span><span class="sxs-lookup"><span data-stu-id="666c5-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="666c5-324">PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="666c5-324">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="666c5-325">描述模拟耳机显示的配置。</span><span class="sxs-lookup"><span data-stu-id="666c5-325">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="666c5-326">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="666c5-326">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="666c5-327">从头部中心到左边的转换是为了实现立体声渲染。</span><span class="sxs-lookup"><span data-stu-id="666c5-327">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="666c5-328">**PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="666c5-328">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="666c5-329">用于立体声呈现的左侧方式的旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-329">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="666c5-330">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="666c5-330">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="666c5-331">从头部中心到正确眼睛的转换是为了实现立体声渲染。</span><span class="sxs-lookup"><span data-stu-id="666c5-331">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="666c5-332">**PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="666c5-332">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="666c5-333">为了实现立体声渲染，正确的眼睛旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-333">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="666c5-334">**PerceptionSimulation. SimulatedDisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="666c5-334">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="666c5-335">系统报告的 Ipd 值用于立体声渲染。</span><span class="sxs-lookup"><span data-stu-id="666c5-335">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="666c5-336">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="666c5-336">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="666c5-337">是否应将为左和右眼转换提供的值视为有效并应用于正在运行的系统。</span><span class="sxs-lookup"><span data-stu-id="666c5-337">Whether or not the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="666c5-338">**PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="666c5-338">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="666c5-339">是否应将为 Ipd 提供的值视为有效，并将其应用于正在运行的系统。</span><span class="sxs-lookup"><span data-stu-id="666c5-339">Whether or not the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="666c5-340">PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="666c5-340">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="666c5-341">用于生成用于控制设备的数据包的根。</span><span class="sxs-lookup"><span data-stu-id="666c5-341">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="666c5-342">**PerceptionSimulation. IPerceptionSimulationManager. 设备**</span><span class="sxs-lookup"><span data-stu-id="666c5-342">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="666c5-343">检索用于解释模拟人类和模拟世界的模拟设备对象。</span><span class="sxs-lookup"><span data-stu-id="666c5-343">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="666c5-344">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="666c5-344">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="666c5-345">检索控制模拟人的对象。</span><span class="sxs-lookup"><span data-stu-id="666c5-345">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="666c5-346">**PerceptionSimulation. IPerceptionSimulationManager**</span><span class="sxs-lookup"><span data-stu-id="666c5-346">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="666c5-347">将模拟重置为其默认状态。</span><span class="sxs-lookup"><span data-stu-id="666c5-347">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="666c5-348">PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="666c5-348">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="666c5-349">描述用于解释模拟世界和模拟人类的设备的接口</span><span class="sxs-lookup"><span data-stu-id="666c5-349">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="666c5-350">**PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="666c5-350">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="666c5-351">从模拟设备检索 Head 跟踪器。</span><span class="sxs-lookup"><span data-stu-id="666c5-351">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="666c5-352">**PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="666c5-352">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="666c5-353">从模拟设备检索手动跟踪器。</span><span class="sxs-lookup"><span data-stu-id="666c5-353">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="666c5-354">**PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType （PerceptionSimulation. SimulatedDeviceType）**</span><span class="sxs-lookup"><span data-stu-id="666c5-354">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="666c5-355">设置模拟设备的属性，使其与所提供的设备类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="666c5-355">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="666c5-356">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-356">Parameters</span></span>
* <span data-ttu-id="666c5-357">类型-新类型的模拟设备</span><span class="sxs-lookup"><span data-stu-id="666c5-357">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="666c5-358">PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="666c5-358">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="666c5-359">可以通过将 ISimulatedDevice 转换为 ISimulatedDevice2 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="666c5-359">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="666c5-360">**PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="666c5-360">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="666c5-361">检索或设置模拟人力是否正在积极地戴上耳机。</span><span class="sxs-lookup"><span data-stu-id="666c5-361">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="666c5-362">**PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="666c5-362">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="666c5-363">检索或设置模拟的显示的属性。</span><span class="sxs-lookup"><span data-stu-id="666c5-363">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="666c5-364">PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="666c5-364">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="666c5-365">描述模拟设备的部分的接口，该部分跟踪模拟人的头。</span><span class="sxs-lookup"><span data-stu-id="666c5-365">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="666c5-366">**PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="666c5-366">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="666c5-367">检索和设置当前 head 跟踪器模式。</span><span class="sxs-lookup"><span data-stu-id="666c5-367">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="666c5-368">PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="666c5-368">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="666c5-369">描述模拟设备的部分的接口，该部分跟踪模拟人的手</span><span class="sxs-lookup"><span data-stu-id="666c5-369">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="666c5-370">**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="666c5-370">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="666c5-371">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-371">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="666c5-372">**PerceptionSimulation. ISimulatedHandTracker. 位置**</span><span class="sxs-lookup"><span data-stu-id="666c5-372">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="666c5-373">检索和设置模拟手型跟踪器的位置（相对于打印头的中心）。</span><span class="sxs-lookup"><span data-stu-id="666c5-373">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="666c5-374">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="666c5-374">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="666c5-375">检索和设置模拟手型跟踪器的下间距。</span><span class="sxs-lookup"><span data-stu-id="666c5-375">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="666c5-376">**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="666c5-376">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="666c5-377">检索和设置是否忽略模拟手动跟踪器的 "截锥"。</span><span class="sxs-lookup"><span data-stu-id="666c5-377">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="666c5-378">如果忽略，则这两个指针始终可见。</span><span class="sxs-lookup"><span data-stu-id="666c5-378">When ignored, both hands are always visible.</span></span> <span data-ttu-id="666c5-379">如果未被忽略（默认值），则只有在 "手形跟踪器" 的 "截锥" 中时才会显示。</span><span class="sxs-lookup"><span data-stu-id="666c5-379">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="666c5-380">**PerceptionSimulation. ISimulatedHandTracker**</span><span class="sxs-lookup"><span data-stu-id="666c5-380">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="666c5-381">检索和设置用来确定是否对模拟手型跟踪器可见的被截锥属性。</span><span class="sxs-lookup"><span data-stu-id="666c5-381">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="666c5-382">PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="666c5-382">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="666c5-383">用于控制模拟人的顶级接口。</span><span class="sxs-lookup"><span data-stu-id="666c5-383">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="666c5-384">**PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="666c5-384">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="666c5-385">检索和设置与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-385">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="666c5-386">此位置对应于人脚的中心点。</span><span class="sxs-lookup"><span data-stu-id="666c5-386">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="666c5-387">**PerceptionSimulation. ISimulatedHuman。**</span><span class="sxs-lookup"><span data-stu-id="666c5-387">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="666c5-388">检索和设置模拟人脸在世界中的方向。</span><span class="sxs-lookup"><span data-stu-id="666c5-388">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="666c5-389">0弧度朝下 Z 轴向下。</span><span class="sxs-lookup"><span data-stu-id="666c5-389">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="666c5-390">正弧度围绕 Y 轴顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-390">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="666c5-391">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="666c5-391">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="666c5-392">检索和设置模拟人的高度（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-392">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="666c5-393">**PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="666c5-393">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="666c5-394">检索模拟人的左侧。</span><span class="sxs-lookup"><span data-stu-id="666c5-394">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="666c5-395">**PerceptionSimulation. ISimulatedHuman. RightHand**</span><span class="sxs-lookup"><span data-stu-id="666c5-395">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="666c5-396">检索模拟人的右边。</span><span class="sxs-lookup"><span data-stu-id="666c5-396">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="666c5-397">**PerceptionSimulation. ISimulatedHuman**</span><span class="sxs-lookup"><span data-stu-id="666c5-397">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="666c5-398">检索模拟人的 head。</span><span class="sxs-lookup"><span data-stu-id="666c5-398">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="666c5-399">**PerceptionSimulation. ISimulatedHuman （PerceptionSimulation. System.numerics.vector2）**</span><span class="sxs-lookup"><span data-stu-id="666c5-399">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="666c5-400">以米为单位移动模拟人工相对于其当前位置的位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-400">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="666c5-401">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-401">Parameters</span></span>
* <span data-ttu-id="666c5-402">平移-要移动的转换，相对于当前位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-402">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="666c5-403">**PerceptionSimulation. ISimulatedHuman （System.web）**</span><span class="sxs-lookup"><span data-stu-id="666c5-403">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="666c5-404">围绕 Y 轴顺时针旋转模拟人工相对于其当前方向</span><span class="sxs-lookup"><span data-stu-id="666c5-404">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="666c5-405">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-405">Parameters</span></span>
* <span data-ttu-id="666c5-406">radians-绕 Y 轴旋转的量。</span><span class="sxs-lookup"><span data-stu-id="666c5-406">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="666c5-407">PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="666c5-407">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="666c5-408">可以通过将 ISimulatedHuman 转换为 ISimulatedHuman2 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="666c5-408">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="666c5-409">**PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="666c5-409">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="666c5-410">检索左 6-DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="666c5-410">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="666c5-411">**PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="666c5-411">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="666c5-412">检索正确的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="666c5-412">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="666c5-413">PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="666c5-413">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="666c5-414">描述模拟人类</span><span class="sxs-lookup"><span data-stu-id="666c5-414">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="666c5-415">**PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="666c5-415">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="666c5-416">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-416">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="666c5-417">**PerceptionSimulation. ISimulatedHand. 位置**</span><span class="sxs-lookup"><span data-stu-id="666c5-417">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="666c5-418">检索和设置模拟手型相对于人类的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-418">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="666c5-419">**PerceptionSimulation. ISimulatedHand. 已激活**</span><span class="sxs-lookup"><span data-stu-id="666c5-419">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="666c5-420">检索和设置当前是否已激活该手型。</span><span class="sxs-lookup"><span data-stu-id="666c5-420">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="666c5-421">**PerceptionSimulation. ISimulatedHand。**</span><span class="sxs-lookup"><span data-stu-id="666c5-421">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="666c5-422">检索 SimulatedDevice 当前是否对可见（即，该手形是否处于 HandTracker 检测到的位置）。</span><span class="sxs-lookup"><span data-stu-id="666c5-422">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="666c5-423">\**PerceptionSimulation. ISimulatedHand. Ensurevisible\**</span><span class="sxs-lookup"><span data-stu-id="666c5-423">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="666c5-424">移动手使其对 SimulatedDevice 可见。</span><span class="sxs-lookup"><span data-stu-id="666c5-424">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="666c5-425">**PerceptionSimulation. ISimulatedHand （PerceptionSimulation. System.numerics.vector2）**</span><span class="sxs-lookup"><span data-stu-id="666c5-425">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="666c5-426">以米为单位移动模拟手型相对于其当前位置的位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-426">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="666c5-427">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-427">Parameters</span></span>
* <span data-ttu-id="666c5-428">翻译-模拟手的平移量。</span><span class="sxs-lookup"><span data-stu-id="666c5-428">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="666c5-429">**PerceptionSimulation. ISimulatedHand. PerformGesture （PerceptionSimulation. SimulatedGesture）**</span><span class="sxs-lookup"><span data-stu-id="666c5-429">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="666c5-430">使用模拟手执行手势。</span><span class="sxs-lookup"><span data-stu-id="666c5-430">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="666c5-431">只有在启用了该功能的情况，系统才会检测到它。</span><span class="sxs-lookup"><span data-stu-id="666c5-431">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="666c5-432">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-432">Parameters</span></span>
* <span data-ttu-id="666c5-433">手势-要执行的手势。</span><span class="sxs-lookup"><span data-stu-id="666c5-433">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="666c5-434">PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="666c5-434">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="666c5-435">可以通过将 ISimulatedHand 转换为 ISimulatedHand2 来获取其他属性。</span><span class="sxs-lookup"><span data-stu-id="666c5-435">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="666c5-436">**PerceptionSimulation. ISimulatedHand2**</span><span class="sxs-lookup"><span data-stu-id="666c5-436">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="666c5-437">检索或设置模拟手的旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-437">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="666c5-438">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-438">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="666c5-439">PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="666c5-439">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="666c5-440">可以通过将 ISimulatedHand 转换为 ISimulatedHand3 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="666c5-440">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="666c5-441">**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="666c5-441">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="666c5-442">获取指定的联合的联合配置。</span><span class="sxs-lookup"><span data-stu-id="666c5-442">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="666c5-443">**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="666c5-443">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="666c5-444">设置指定的联合的联合配置。</span><span class="sxs-lookup"><span data-stu-id="666c5-444">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="666c5-445">**PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="666c5-445">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="666c5-446">使用可选的动画标志将手设置为已知姿势。</span><span class="sxs-lookup"><span data-stu-id="666c5-446">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="666c5-447">注意：动画效果不会立即反映其最终的联合配置。</span><span class="sxs-lookup"><span data-stu-id="666c5-447">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="666c5-448">PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="666c5-448">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="666c5-449">描述模拟人的头的接口。</span><span class="sxs-lookup"><span data-stu-id="666c5-449">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="666c5-450">**PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="666c5-450">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="666c5-451">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-451">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="666c5-452">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="666c5-452">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="666c5-453">检索模拟头部的旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-453">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="666c5-454">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-454">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="666c5-455">**PerceptionSimulation. ISimulatedHead**</span><span class="sxs-lookup"><span data-stu-id="666c5-455">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="666c5-456">检索模拟头直径。</span><span class="sxs-lookup"><span data-stu-id="666c5-456">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="666c5-457">此值用于确定头的中心（旋转点）。</span><span class="sxs-lookup"><span data-stu-id="666c5-457">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="666c5-458">**PerceptionSimulation. ISimulatedHead （PerceptionSimulation. Rotation3）**</span><span class="sxs-lookup"><span data-stu-id="666c5-458">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="666c5-459">相对于当前旋转旋转模拟头。</span><span class="sxs-lookup"><span data-stu-id="666c5-459">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="666c5-460">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-460">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="666c5-461">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-461">Parameters</span></span>
* <span data-ttu-id="666c5-462">旋转-要旋转的量。</span><span class="sxs-lookup"><span data-stu-id="666c5-462">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="666c5-463">PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="666c5-463">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="666c5-464">可以通过将 ISimulatedHead 转换为 ISimulatedHead2 提供其他属性</span><span class="sxs-lookup"><span data-stu-id="666c5-464">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="666c5-465">**PerceptionSimulation. ISimulatedHead2**</span><span class="sxs-lookup"><span data-stu-id="666c5-465">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="666c5-466">检索模拟人的眼睛。</span><span class="sxs-lookup"><span data-stu-id="666c5-466">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="666c5-467">PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="666c5-467">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="666c5-468">描述与模拟人类关联的 6 DOF 控制器的接口。</span><span class="sxs-lookup"><span data-stu-id="666c5-468">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="666c5-469">**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="666c5-469">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="666c5-470">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-470">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="666c5-471">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="666c5-471">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="666c5-472">检索或设置控制器的当前状态。</span><span class="sxs-lookup"><span data-stu-id="666c5-472">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="666c5-473">在任何调用移动、旋转或按下按钮之前，控制器状态必须设置为 Off 以外的值。</span><span class="sxs-lookup"><span data-stu-id="666c5-473">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="666c5-474">**PerceptionSimulation. ISimulatedSixDofController. 位置**</span><span class="sxs-lookup"><span data-stu-id="666c5-474">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="666c5-475">检索或设置模拟控制器相对于人类的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-475">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="666c5-476">**PerceptionSimulation. ISimulatedSixDofController**</span><span class="sxs-lookup"><span data-stu-id="666c5-476">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="666c5-477">检索或设置模拟控制器的方向。</span><span class="sxs-lookup"><span data-stu-id="666c5-477">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="666c5-478">**PerceptionSimulation. ISimulatedSixDofController （PerceptionSimulation. System.numerics.vector2）**</span><span class="sxs-lookup"><span data-stu-id="666c5-478">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="666c5-479">移动模拟控制器相对于其当前位置的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-479">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="666c5-480">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-480">Parameters</span></span>
* <span data-ttu-id="666c5-481">翻译-模拟控制器的平移量。</span><span class="sxs-lookup"><span data-stu-id="666c5-481">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="666c5-482">**PerceptionSimulation. ISimulatedSixDofController. PressButton （SimulatedSixDofControllerButton）**</span><span class="sxs-lookup"><span data-stu-id="666c5-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="666c5-483">按模拟控制器上的按钮。</span><span class="sxs-lookup"><span data-stu-id="666c5-483">Press a button on the simulated controller.</span></span>  <span data-ttu-id="666c5-484">仅当控制器已启用时，系统才会检测到该控制器。</span><span class="sxs-lookup"><span data-stu-id="666c5-484">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="666c5-485">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-485">Parameters</span></span>
* <span data-ttu-id="666c5-486">按钮-要按下的按钮。</span><span class="sxs-lookup"><span data-stu-id="666c5-486">button - The button to press.</span></span>

<span data-ttu-id="666c5-487">**PerceptionSimulation. ISimulatedSixDofController. ReleaseButton （SimulatedSixDofControllerButton）**</span><span class="sxs-lookup"><span data-stu-id="666c5-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="666c5-488">释放模拟控制器上的按钮。</span><span class="sxs-lookup"><span data-stu-id="666c5-488">Release a button on the simulated controller.</span></span>  <span data-ttu-id="666c5-489">仅当控制器已启用时，系统才会检测到该控制器。</span><span class="sxs-lookup"><span data-stu-id="666c5-489">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="666c5-490">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-490">Parameters</span></span>
* <span data-ttu-id="666c5-491">按钮-要释放的按钮。</span><span class="sxs-lookup"><span data-stu-id="666c5-491">button - The button to release.</span></span>

<span data-ttu-id="666c5-492">**PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition （out float，out float）**</span><span class="sxs-lookup"><span data-stu-id="666c5-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="666c5-493">获取模拟手指在模拟控制器的触摸板上的位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-493">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="666c5-494">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-494">Parameters</span></span>
* <span data-ttu-id="666c5-495">x-手指的水平位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-495">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="666c5-496">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-496">y - The vertical position of the finger.</span></span>

<span data-ttu-id="666c5-497">**PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition （float，float）**</span><span class="sxs-lookup"><span data-stu-id="666c5-497">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="666c5-498">设置模拟手指在模拟控制器的触摸板上的位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-498">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="666c5-499">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-499">Parameters</span></span>
* <span data-ttu-id="666c5-500">x-手指的水平位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-500">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="666c5-501">y-手指的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-501">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="666c5-502">PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="666c5-502">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="666c5-503">可以通过将 ISimulatedSixDofController 转换为 ISimulatedSixDofController2 来提供其他属性和方法。</span><span class="sxs-lookup"><span data-stu-id="666c5-503">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="666c5-504">**PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition （out float，out float）**</span><span class="sxs-lookup"><span data-stu-id="666c5-504">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="666c5-505">获取模拟操纵杆在模拟控制器上的位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-505">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="666c5-506">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-506">Parameters</span></span>
* <span data-ttu-id="666c5-507">x-操纵杆的水平位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-507">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="666c5-508">y-操纵杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-508">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="666c5-509">**PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition （float，float）**</span><span class="sxs-lookup"><span data-stu-id="666c5-509">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="666c5-510">设置模拟操纵杆在模拟控制器上的位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-510">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="666c5-511">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-511">Parameters</span></span>
* <span data-ttu-id="666c5-512">x-操纵杆的水平位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-512">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="666c5-513">y-操纵杆的垂直位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-513">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="666c5-514">**PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="666c5-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="666c5-515">检索或设置模拟控制器的电池电量级别。</span><span class="sxs-lookup"><span data-stu-id="666c5-515">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="666c5-516">该值必须大于0.0 且小于或等于100.0。</span><span class="sxs-lookup"><span data-stu-id="666c5-516">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="666c5-517">PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="666c5-517">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="666c5-518">描述模拟人力的眼睛的接口。</span><span class="sxs-lookup"><span data-stu-id="666c5-518">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="666c5-519">**PerceptionSimulation. ISimulatedEyes**</span><span class="sxs-lookup"><span data-stu-id="666c5-519">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="666c5-520">检索模拟眼睛的旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-520">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="666c5-521">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-521">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="666c5-522">**PerceptionSimulation. ISimulatedEyes （PerceptionSimulation. Rotation3）**</span><span class="sxs-lookup"><span data-stu-id="666c5-522">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="666c5-523">相对于当前旋转旋转模拟眼睛。</span><span class="sxs-lookup"><span data-stu-id="666c5-523">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="666c5-524">正弧度沿轴旋转时顺时针旋转。</span><span class="sxs-lookup"><span data-stu-id="666c5-524">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="666c5-525">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-525">Parameters</span></span>
* <span data-ttu-id="666c5-526">旋转-要旋转的量。</span><span class="sxs-lookup"><span data-stu-id="666c5-526">rotation - The amount to rotate.</span></span>

<span data-ttu-id="666c5-527">**PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="666c5-527">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="666c5-528">检索或设置模拟眼睛的校准状态。</span><span class="sxs-lookup"><span data-stu-id="666c5-528">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="666c5-529">**PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="666c5-529">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="666c5-530">检索与世界相关的节点的位置（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="666c5-530">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="666c5-531">PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="666c5-531">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="666c5-532">用于与为播放加载的单个录制交互的接口。</span><span class="sxs-lookup"><span data-stu-id="666c5-532">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="666c5-533">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="666c5-533">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="666c5-534">检索记录中数据类型的列表。</span><span class="sxs-lookup"><span data-stu-id="666c5-534">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="666c5-535">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="666c5-535">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="666c5-536">检索当前记录的状态。</span><span class="sxs-lookup"><span data-stu-id="666c5-536">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="666c5-537">**PerceptionSimulation. ISimulationRecording**</span><span class="sxs-lookup"><span data-stu-id="666c5-537">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="666c5-538">开始播放。</span><span class="sxs-lookup"><span data-stu-id="666c5-538">Start the playback.</span></span> <span data-ttu-id="666c5-539">如果记录已暂停，播放将从暂停位置恢复;如果停止，则将从开始处开始播放。</span><span class="sxs-lookup"><span data-stu-id="666c5-539">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="666c5-540">如果已播放，则忽略此调用。</span><span class="sxs-lookup"><span data-stu-id="666c5-540">If already playing, this call is ignored.</span></span>

<span data-ttu-id="666c5-541">**PerceptionSimulation. ISimulationRecording. 暂停**</span><span class="sxs-lookup"><span data-stu-id="666c5-541">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="666c5-542">暂停播放当前位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-542">Pauses the playback at its current location.</span></span> <span data-ttu-id="666c5-543">如果记录已停止，则调用将被忽略。</span><span class="sxs-lookup"><span data-stu-id="666c5-543">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="666c5-544">**PerceptionSimulation. ISimulationRecording （system.string）**</span><span class="sxs-lookup"><span data-stu-id="666c5-544">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="666c5-545">将记录查找到指定时间（从开头开始，以100毫微秒为间隔），并在该位置暂停。</span><span class="sxs-lookup"><span data-stu-id="666c5-545">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="666c5-546">如果该时间超出了记录的结束时间，则会在最后一帧暂停该时间。</span><span class="sxs-lookup"><span data-stu-id="666c5-546">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="666c5-547">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-547">Parameters</span></span>
* <span data-ttu-id="666c5-548">计时周期-要查找的时间。</span><span class="sxs-lookup"><span data-stu-id="666c5-548">ticks - The time to which to seek.</span></span>

<span data-ttu-id="666c5-549">**PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="666c5-549">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="666c5-550">停止播放并将位置重置为开始位置。</span><span class="sxs-lookup"><span data-stu-id="666c5-550">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="666c5-551">PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="666c5-551">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="666c5-552">用于在播放期间接收状态更改的接口。</span><span class="sxs-lookup"><span data-stu-id="666c5-552">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="666c5-553">**PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged （PerceptionSimulation. PlaybackState）**</span><span class="sxs-lookup"><span data-stu-id="666c5-553">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="666c5-554">当 ISimulationRecording 的播放状态发生更改时调用。</span><span class="sxs-lookup"><span data-stu-id="666c5-554">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="666c5-555">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-555">Parameters</span></span>
* <span data-ttu-id="666c5-556">newState-记录的新状态。</span><span class="sxs-lookup"><span data-stu-id="666c5-556">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="666c5-557">PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="666c5-557">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="666c5-558">用于创建感知模拟对象的根对象。</span><span class="sxs-lookup"><span data-stu-id="666c5-558">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="666c5-559">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager （PerceptionSimulation. ISimulationStreamSink）**</span><span class="sxs-lookup"><span data-stu-id="666c5-559">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="666c5-560">针对生成模拟包并将其传送到所提供接收器的对象创建。</span><span class="sxs-lookup"><span data-stu-id="666c5-560">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="666c5-561">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-561">Parameters</span></span>
* <span data-ttu-id="666c5-562">sink-接收所有生成的数据包的接收器。</span><span class="sxs-lookup"><span data-stu-id="666c5-562">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="666c5-563">返回值</span><span class="sxs-lookup"><span data-stu-id="666c5-563">Return value</span></span>

<span data-ttu-id="666c5-564">创建的管理器。</span><span class="sxs-lookup"><span data-stu-id="666c5-564">The created Manager.</span></span>

<span data-ttu-id="666c5-565">**PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording （System.string）**</span><span class="sxs-lookup"><span data-stu-id="666c5-565">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="666c5-566">创建一个接收器，将所有接收的数据包存储在文件中的指定路径。</span><span class="sxs-lookup"><span data-stu-id="666c5-566">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="666c5-567">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-567">Parameters</span></span>
* <span data-ttu-id="666c5-568">path-要创建的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="666c5-568">path - The path of the file to create.</span></span>

<span data-ttu-id="666c5-569">返回值</span><span class="sxs-lookup"><span data-stu-id="666c5-569">Return value</span></span>

<span data-ttu-id="666c5-570">创建的接收器。</span><span class="sxs-lookup"><span data-stu-id="666c5-570">The created sink.</span></span>

<span data-ttu-id="666c5-571">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording （System.string，PerceptionSimulation. ISimulationStreamSinkFactory）**</span><span class="sxs-lookup"><span data-stu-id="666c5-571">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="666c5-572">从指定的文件加载记录。</span><span class="sxs-lookup"><span data-stu-id="666c5-572">Load a recording from the specified file.</span></span>

<span data-ttu-id="666c5-573">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-573">Parameters</span></span>
* <span data-ttu-id="666c5-574">path-要加载的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="666c5-574">path - The path of the file to load.</span></span>
* <span data-ttu-id="666c5-575">工厂-记录用于在需要时创建 ISimulationStreamSink 的工厂。</span><span class="sxs-lookup"><span data-stu-id="666c5-575">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="666c5-576">返回值</span><span class="sxs-lookup"><span data-stu-id="666c5-576">Return value</span></span>

<span data-ttu-id="666c5-577">加载的记录。</span><span class="sxs-lookup"><span data-stu-id="666c5-577">The loaded recording.</span></span>

<span data-ttu-id="666c5-578">**PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording （PerceptionSimulation，ISimulationStreamSinkFactory，PerceptionSimulation，ISimulationRecordingCallback，）**</span><span class="sxs-lookup"><span data-stu-id="666c5-578">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="666c5-579">从指定的文件加载记录。</span><span class="sxs-lookup"><span data-stu-id="666c5-579">Load a recording from the specified file.</span></span>

<span data-ttu-id="666c5-580">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-580">Parameters</span></span>
* <span data-ttu-id="666c5-581">path-要加载的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="666c5-581">path - The path of the file to load.</span></span>
* <span data-ttu-id="666c5-582">工厂-记录用于在需要时创建 ISimulationStreamSink 的工厂。</span><span class="sxs-lookup"><span data-stu-id="666c5-582">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="666c5-583">回叫-在记录状态 regrading 接收更新的回调。</span><span class="sxs-lookup"><span data-stu-id="666c5-583">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="666c5-584">返回值</span><span class="sxs-lookup"><span data-stu-id="666c5-584">Return value</span></span>

<span data-ttu-id="666c5-585">加载的记录。</span><span class="sxs-lookup"><span data-stu-id="666c5-585">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="666c5-586">PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="666c5-586">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="666c5-587">描述不同类型的流数据。</span><span class="sxs-lookup"><span data-stu-id="666c5-587">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="666c5-588">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="666c5-588">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="666c5-589">用于指示没有流数据类型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="666c5-589">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="666c5-590">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="666c5-590">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="666c5-591">与头部位置和方向相关的数据流。</span><span class="sxs-lookup"><span data-stu-id="666c5-591">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="666c5-592">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="666c5-592">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="666c5-593">有关指针位置和手势的数据流。</span><span class="sxs-lookup"><span data-stu-id="666c5-593">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="666c5-594">**PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="666c5-594">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="666c5-595">有关环境的空间映射的数据流。</span><span class="sxs-lookup"><span data-stu-id="666c5-595">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="666c5-596">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="666c5-596">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="666c5-597">与设备的校准相关的数据流。</span><span class="sxs-lookup"><span data-stu-id="666c5-597">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="666c5-598">只有远程模式下的系统才会接受校准数据包。</span><span class="sxs-lookup"><span data-stu-id="666c5-598">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="666c5-599">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="666c5-599">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="666c5-600">有关设备环境的数据流。</span><span class="sxs-lookup"><span data-stu-id="666c5-600">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="666c5-601">**PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="666c5-601">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="666c5-602">有关运动控制器的数据流。</span><span class="sxs-lookup"><span data-stu-id="666c5-602">Stream of data regarding motion controllers.</span></span>

<span data-ttu-id="666c5-603">**PerceptionSimulation. StreamDataTypes**</span><span class="sxs-lookup"><span data-stu-id="666c5-603">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="666c5-604">与模拟人类的眼睛相关的数据流。</span><span class="sxs-lookup"><span data-stu-id="666c5-604">Stream of data regarding the eyes of the simulated human.</span></span>

<span data-ttu-id="666c5-605">**PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="666c5-605">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="666c5-606">有关设备显示配置的数据流。</span><span class="sxs-lookup"><span data-stu-id="666c5-606">Stream of data regarding the display configuration of the device.</span></span>

<span data-ttu-id="666c5-607">**PerceptionSimulation. StreamDataTypes。**</span><span class="sxs-lookup"><span data-stu-id="666c5-607">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="666c5-608">用于指示所有记录的数据类型的 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="666c5-608">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="666c5-609">PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="666c5-609">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="666c5-610">从模拟流接收数据包的对象。</span><span class="sxs-lookup"><span data-stu-id="666c5-610">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="666c5-611">**PerceptionSimulation. ISimulationStreamSink. OnPacketReceived （uint length，byte [] packet）**</span><span class="sxs-lookup"><span data-stu-id="666c5-611">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="666c5-612">接收单个数据包，该数据包在内部键入并进行版本控制。</span><span class="sxs-lookup"><span data-stu-id="666c5-612">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="666c5-613">参数</span><span class="sxs-lookup"><span data-stu-id="666c5-613">Parameters</span></span>
* <span data-ttu-id="666c5-614">length-数据包的长度。</span><span class="sxs-lookup"><span data-stu-id="666c5-614">length - The length of the packet.</span></span>
* <span data-ttu-id="666c5-615">数据包-包的数据。</span><span class="sxs-lookup"><span data-stu-id="666c5-615">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="666c5-616">PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="666c5-616">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="666c5-617">用于创建 ISimulationStreamSink 的对象。</span><span class="sxs-lookup"><span data-stu-id="666c5-617">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="666c5-618">**PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink （）**</span><span class="sxs-lookup"><span data-stu-id="666c5-618">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="666c5-619">创建 ISimulationStreamSink 的单个实例。</span><span class="sxs-lookup"><span data-stu-id="666c5-619">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="666c5-620">返回值</span><span class="sxs-lookup"><span data-stu-id="666c5-620">Return value</span></span>

<span data-ttu-id="666c5-621">创建的接收器。</span><span class="sxs-lookup"><span data-stu-id="666c5-621">The created sink.</span></span>
