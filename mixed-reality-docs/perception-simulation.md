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
# <a name="perception-simulation"></a>Perception 模拟

若要生成你的应用的自动的测试吗？ 超越组件级的单元测试和实际练习你的应用程序端到端测试吗？ Perception 模拟是要查找的内容。 Perception 模拟库将发送人和世界输入到您的应用程序的数据，这样可以自动执行测试。 例如，可以模拟人类查找到特定的可重复的位置，然后执行一个手势或使用运动控制器的输入。

Perception 模拟可以将此类模拟的输入发送到物理 HoloLens，HoloLens 仿真程序 （第 1 代） HoloLens 2 个仿真程序，或者使用混合现实门户 PC 安装。 Perception 模拟绕过混合现实设备上的实时传感器并发送模拟设备上运行的应用程序的输入。 应用程序接收这些输入的事件通过相同的 Api，它们始终使用和不能确定它们与实际传感器与运行与 Perception 模拟运行之间的区别。 Perception 模拟是 HoloLens 仿真程序用于发送模拟的输入到 HoloLens 虚拟机的相同技术。

若要开始在代码中使用模拟，请先创建 IPerceptionSimulationManager 对象。 从该对象，您可以发出命令来控制属性的模拟"人"，包括头位置、 手位置和手势，并可以启用和操作动作控制器。

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>为 Perception 模拟设置 Visual Studio 项目
1. [安装 HoloLens 模拟器](install-the-tools.md)开发计算机上。 在仿真程序包含将用于对模拟的库。
2. 创建新的 Visual StudioC#桌面 （控制台项目运行良好开始） 的项目。
3. 将以下二进制文件作为引用添加到你的项目 (项目-> 添加-> 引用...)。您可以找到它们在 %programfiles (x86) %\Microsoft XDE\\（版本），如 **%programfiles (x86) %\Microsoft XDE\\10.0.18362.0** HoloLens 2 仿真程序。  (注意： 尽管这些二进制文件是 HoloLens 2 仿真程序的一部分，但它们也适用于 Windows Mixed Reality 在桌面上。)一个。 PerceptionSimulationManager.Interop.dll-管理C#Perception 模拟的包装器。
    b. PerceptionSimulationRest.dll-设置 web 套接字通信通道到 HoloLens 或仿真器的库。
    c. SimulationStream.Interop.dll-共享类型进行模拟。
4. 将实现添加到你的项目二进制 PerceptionSimulationManager.dll。 首先将其作为二进制文件添加到项目 (项目-> 添加-> 现有项...)。将其保存为一个链接，以便它不会将其复制到你的项目源文件夹。 ![向项目的链接的形式添加 PerceptionSimulationManager.dll](images/saveaslink.png) b。 请确保它获取的复制到生成输出文件夹。 这是二进制文件的属性表中。 ![将标记 PerceptionSimulationManager.dll 将复制到输出目录](images/copyalways.png)
5. 将活动解决方案平台设置为 x64。  （使用配置管理器，以创建适用于 x64 的平台项，如果一个尚不存在）。

## <a name="creating-an-iperceptionsimulation-manager-object"></a>创建 IPerceptionSimulation Manager 对象

若要控制模拟，将从 IPerceptionSimulationManager 对象检索到的对象发布更新。 第一步是获取该对象，并将其连接到目标设备或仿真程序。 可以通过单击在设备门户按钮获取仿真程序的 IP 地址[工具栏](using-the-hololens-emulator.md)

![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**:在仿真器中打开 HoloLens OS 的 Windows 设备门户。  为 Windows Mixed Reality，这可以检索在设置应用"更新和安全性"，然后，"对于开发人员"中"使用连接:"部分下"启用设备门户。"  请务必记下的 IP 地址和端口。

首先，将调用 RestSimulationStreamSink.Create 获取 RestSimulationStreamSink 对象。 这是目标设备或仿真程序将控制通过 http 连接。 将传递给你的命令，并将其由处理[Windows Device Portal](using-the-windows-device-portal.md)设备或仿真器上运行。 将需要创建一个对象的四个参数是：
* Uri uri-目标设备的 IP 地址 (例如，"http://123.123.123.123"或"http://123.123.123.123:50080")
* System.Net.NetworkCredential 凭据-用户名/密码用于连接到[Windows Device Portal](using-the-windows-device-portal.md)目标设备或仿真程序上。 如果您要连接到仿真程序通过其本地地址 (例如，168。 *。* 。 *) 将在同一台 PC 上接受任何凭据。
* 正常情况-bool 的普通优先级低优先级为 false，则返回 True。 你通常想要将其设置为 *，则返回 true*的测试方案，它允许测试控制。  仿真程序和 Windows Mixed Reality 模拟使用低优先级服务连接。  如果你的测试还使用低优先级服务连接，大多数最近创建的连接将在控件中。
* System.Threading.CancellationToken 令牌-令牌取消异步操作。

其次，您将创建 IPerceptionSimulationManager。 这是用于控制模拟的对象。 请注意这必须还将完成的异步方法中。

## <a name="control-the-simulated-human"></a>控制模拟的用户

IPerceptionSimulationManager 有一个人属性可返回 ISimulatedHuman 对象。 若要控制模拟的用户，请执行此对象上的操作。 例如：

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>基本示例C#控制台应用程序

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

## <a name="extended-sample-c-console-application"></a>扩展示例C#控制台应用程序

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

## <a name="note-on-6-dof-controllers"></a>请注意 6 DOF 控制器上

在调用之前的任何属性上的模拟的 6 DOF 控制器上的方法，必须激活该控制器。  不执行此操作将导致异常。  从 Windows 10 开始可能 2019年更新，可以安装和激活的状态属性设置为 SimulatedSixDofControllerStatus.Active ISimulatedSixDofController 对象上模拟的 6 DOF 控制器。
在 Windows 10 2018 年 10 月更新和更早版本，您必须单独安装模拟的 6 DOF 控制器首先通过调用 PerceptionSimulationDevice 工具 \Windows\System32 文件夹中。  此工具的用法如下所示：


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

例如

```
    PerceptionSimulationDevice.exe i 6dof 1
```

支持的操作是：
* 我 = install
* 问: = 查询
* r = 删除

支持的实例是：
* 1 = 左的 6 DOF 控制器
* 2 = 右 6 DOF 控制器

（零返回值） 的成功或失败 （非零返回值），将指示进程的退出代码。  当使用 q 操作来查询该值指示安装了控制器，返回值将为零 (0)，如果尚未安装在控制器或一 （1） 如果安装了控制器。

当删除控制器在 Windows 10 2018 年 10 月更新或更早版本，其将状态设置为 Off 通过 API 第一次，然后调用 PerceptionSimulationDevice 工具。

请注意，必须以管理员身份运行此工具。




## <a name="api-reference"></a>API 参考

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

介绍一种模拟的设备类型

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

虚构引用设备的默认值为 PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

头跟踪器模式下运行

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

默认跟踪头。 这意味着，系统可能会选择跟踪模式下运行时条件基于最佳头。

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

方向仅头跟踪。 这意味着跟踪的位置可能不可靠，并依赖于头位置某些功能可能不可用。

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

位置头跟踪。 这意味着，跟踪头位置和方向都是可靠

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

介绍模拟的手势

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

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

用来指示没有手势的 sentinel 值。

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

手指按下手势。

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

手指发布手势。

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

主页/系统笔势。

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

最大有效的手势。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

模拟的 6 DOF 控制器了可能的状态。

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

6 DOF 控制器处于关闭状态。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

6 DOF 控制器已打开，并跟踪。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

6 DOF 控制器处于开启状态，但不能跟踪。

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

模拟的 6 DOF 控制器上受支持的按钮。

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

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

用来指示没有按钮的 sentinel 值。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

已按下主页按钮。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

按下菜单按钮。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

按下手柄按钮。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

触摸板已按下。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

选择按钮已按下。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

使用触摸板。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

摇杆已按下。

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

最大有效按钮。


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState

模拟眼睛的校准状态

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**

眼睛校准不可用。

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**

眼睛已校准。  这是默认值。

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**

眼睛是正在校准。

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**

眼睛需要校验一次。

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

跟踪准确性的手形图标的联接。

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

不跟踪联合。

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

推断的联合的位置。

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

完全跟踪联合。

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

跟踪准确性的手形图标的联接。

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

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

手形图标的手指关节配置为反映已关闭的姿势。

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

手形图标的手指关节配置以反映打开姿势。

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

手形图标的手指关节配置以反映指针姿势。

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

手形图标的手指关节配置以反映捏指姿势。

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

SimulatedHandPose 最大有效值。


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

描述状态的播放。

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

记录当前处于已停止，并准备好进行播放。

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

当前播放该录制。

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

当前已暂停录制。

**Microsoft.PerceptionSimulation.PlaybackState.End**

记录已到达末尾。

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

介绍了 3 个组件矢量，可能会描述一个点或 3D 空间中的向量。

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

向量的 X 分量。

**Microsoft.PerceptionSimulation.Vector3.Y**

向量的 Y 分量。

**Microsoft.PerceptionSimulation.Vector3.Z**

向量的 Z 分量。

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

构造新 Vector3。

Parameters
* x 轴向量的 x 分量。
* y 轴向量的 y 分量。
* z-矢量的 z 分量。

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

描述的 3 个组件旋转。

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

间距组成部分旋转、 绕 X 轴向下。

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

右围绕 Y 轴的旋转角度偏航组件。

**Microsoft.PerceptionSimulation.Rotation3.Roll**

右围绕 Z 轴的旋转角度汇总组件。

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

构造新 Rotation3。

Parameters
* 间距的旋转的音调组件。
* 偏航-旋转偏航组件。
* 将鼠标移-旋转的汇总组件。

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

在模拟手的形状上介绍的接合的配置。

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

联合的位置。

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

联合的旋转。

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

跟踪准确性的联合。


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

描述视图截锥，通常使用照相机。

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

截锥中包含的最小距离。

**Microsoft.PerceptionSimulation.Frustum.Far**

截锥中包含的最大距离。

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

水平视图的字段的截锥，以弧度为单位 （小于 PI）。

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

水平视角为垂直的视野比率。

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

用于生成用来控制设备的数据包的根。

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

检索将解释模拟的人类和模拟的世界的模拟的设备对象。

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

检索控制模拟的人类的对象。

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

将模拟重置为其默认状态。

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

接口描述将解释模拟的世界和模拟的用户的设备

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

从模拟设备中检索头跟踪器。

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

从模拟设备中检索的现有跟踪器。

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

设置模拟设备以提供的设备类型匹配的属性。

Parameters
* 键入的新类型的模拟设备

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

接口描述跟踪的模拟人类的模拟设备的部分。

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

检索并设置当前头跟踪器模式。

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

描述跟踪的模拟用户的手中的模拟设备的部分接口

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

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

检索与世界里，相关的节点以米为单位的位置。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

检索和设置的模拟的手动跟踪程序，位置相对于头的中心。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

检索和设置的模拟的手动跟踪器的向下音调。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

检索和设置是否忽略模拟的手动跟踪器的截锥。 如果忽略，将始终显示两只手。 当不忽略 （默认值） 内手动跟踪器的截锥时才可见手。

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

检索和设置用于确定指针是否对模拟的手动跟踪器可见的截锥属性。

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

用于控制模拟的人类的顶部级别接口。

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

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

检索并与世界中，以米为单位相关设置的节点的位置。 位置对应于人类的英尺位于中心点。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

检索并在世界中模拟的人脸设置方向。 0 弧度朝下负 Z 轴。 正弧度围绕 Y 轴顺时针旋转。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

检索和设置的模拟用户的高度，以米为单位。

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

检索模拟人类的左侧。

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

检索模拟人类的右侧。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

检索模拟人类的开头。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

将模拟的人类移动相对于其当前的位置，以米为单位。

Parameters
* 翻译的移动，相对于当前的位置的翻译。

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

模拟的人类相对于其当前方向，围绕 Y 轴顺时针旋转

Parameters
* 弧度-要围绕 Y 轴旋转的量。

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedHuman2

其他属性均可通过强制转换到 ISimulatedHuman2 ISimulatedHuman

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**

检索左的 6 DOF 控制器。

**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**

检索正确的 6 DOF 控制器。


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

接口描述模拟用户的手的形状

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

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

检索与世界里，相关的节点以米为单位的位置。

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

检索和设置以米为单位的相对于人，模拟手形图标的位置。

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

检索和设置是否手形图标当前处于激活状态。

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

检索当前可见 （即，是在一个位置可检测到的 HandTracker） SimulatedDevice 手形图标是否。

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

移动手形图标，以便对 SimulatedDevice 可见。

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

移动模拟手的位置，相对于其当前的位置，以米为单位。

Parameters
* 翻译-模拟的手的平移量。

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

执行使用模拟的手手势。  它就只会检测到系统手形图标已启用。

Parameters
* 笔势-要执行的笔势。

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

其他属性均可通过强制转换到 ISimulatedHand2 ISimulatedHand。
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

检索或设置模拟手的旋转。  查看该轴时，正弧度为单位的顺时针旋转。

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

其他属性均可通过强制转换到 ISimulatedHand3 ISimulatedHand
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

获取指定的联合的联合配置。

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

设置指定的联合的联合配置。

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

设置为与要进行动画处理的可选标志已知姿势手形图标。  注意： 进行动画处理不会导致关节立即反映其最终的联合配置。


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

接口描述模拟人类的开头。

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

检索与世界里，相关的节点以米为单位的位置。

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

检索模拟头的旋转。 查看该轴时，正弧度为单位的顺时针旋转。

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

检索模拟的头直径。 此值用于确定 head 的中心 （旋转的点）。

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

旋转模拟的头相对于其当前的旋转。 查看该轴时，正弧度为单位的顺时针旋转。

Parameters
* 旋转-要旋转的量。

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

其他属性均可通过强制转换到 ISimulatedHead2 ISimulatedHead

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

检索模拟人类的眼。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

描述与模拟的用户相关联的 6 DOF 控制器的接口。

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

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

检索与世界里，相关的节点以米为单位的位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

检索或设置控制器的当前状态。  控制器状态必须设置为一个值，而不关闭要移动、 旋转或按进行任何调用之前按钮将会成功。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

检索或设置相对于用户的模拟控制器的位置，以米为单位。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

检索或设置模拟控制器的方向。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

将模拟的控制器的位置移动相对于其当前的位置，以米为单位。

Parameters
* 翻译-模拟的控制器的平移量。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

模拟的控制器上按一个按钮。  它就只会检测到系统已启用控制器。

Parameters
* 按钮的按钮按下。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

释放模拟控制器上的按钮。  它就只会检测到系统已启用控制器。

Parameters
* 按钮的发布按钮。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**

获取为模拟指模拟的控制器的触摸板上的位置。

Parameters
* x 的手指水平位置。
* y 的手指垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**

设置模拟的控制器的触摸板模拟手指的位置。

Parameters
* x 的手指水平位置。
* y 的手指垂直位置。

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

其他属性和方法均可通过强制转换到 ISimulatedSixDofController2 ISimulatedSixDofController

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**

获取模拟摇杆模拟控制器上的位置。

Parameters
* x 的摇杆水平位置。
* y 的摇杆垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**

模拟的控制器上设置的模拟摇杆位置。

Parameters
* x 的摇杆水平位置。
* y 的摇杆垂直位置。

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

检索或设置模拟控制器的电池电量水平。  值必须大于 0.0 且小于或等于 100.0。


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

描述模拟人类的眼的接口。

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

检索模拟眼睛的旋转。 查看该轴时，正弧度为单位的顺时针旋转。

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

旋转模拟的眼睛相对于其当前的旋转。 查看该轴时，正弧度为单位的顺时针旋转。

Parameters
* 旋转-要旋转的量。

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

获取或设置的模拟眼睛的校准状态。

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

检索与世界里，相关的节点以米为单位的位置。


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

加载与单个记录进行交互的接口中进行播放。

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

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

检索在记录中的数据类型的列表。

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

检索记录的当前状态。

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

开始播放。 从暂停的位置; 如果暂停录制后，将恢复播放如果停止，将开头开始播放。 如果已在播放，则忽略此调用。

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

暂停播放在其当前的位置。 如果停止录制，则将忽略此调用。

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

查找在指定的时间 （以 100 纳秒间隔从一开始） 记录，并在该位置暂停。 如果所记录的末尾之外的时间，它会暂停在最后一帧。

Parameters
* 计时周期数-要查找的时间。

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

停止播放和位置重置到开头。

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

在播放期间接收状态更改的接口。

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

ISimulationRecording 播放状态发生更改时调用。

Parameters
* newState-记录的新状态。

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

根对象，用于创建 Perception 模拟对象。

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

创建用于生成模拟的数据包并将它们传递到提供的接收器对象上。

Parameters
* 接收器的接收器将接收生成的所有数据包。

返回值

创建管理器。

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

创建接收器将接收的所有数据包存储在指定的路径的文件中。

Parameters
* 路径-要创建的文件的路径。

返回值

创建的接收器。

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

从指定的文件加载录制。

Parameters
* 路径-要加载的文件的路径。
* 工厂-记录用于创建 ISimulationStreamSink 时所需的工厂。

返回值

加载的记录。

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory，Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

从指定的文件加载录制。

Parameters
* 路径-要加载的文件的路径。
* 工厂-记录用于创建 ISimulationStreamSink 时所需的工厂。
* callback-回调接收更新 regrading 录制的状态。

返回值

加载的记录。

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

介绍不同类型的流数据。

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

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

用来指示没有流数据类型的 sentinel 值。

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Stream 的位置和方向的头有关的数据。

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

有关位置和手势动手操作的数据的 Stream。

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

有关环境的空间映射的数据的 Stream。

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

有关设备的校准数据 Stream。 通过在远程模式下的系统仅接受校准数据包。

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

有关设备的环境数据的 Stream。

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

用来指示所有记录的数据类型的 sentinel 值。

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

从模拟流接收数据包的对象。

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**

接收单个数据包，这是在内部类型和版本控制。

Parameters
* length-数据包的长度。
* 数据包的数据包的数据。

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

一个对象，创建 ISimulationStreamSink。

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

创建 ISimulationStreamSink 的单一实例。

返回值

创建的接收器。
