---
title: 在 DirectX 中的头节点和关注视线移动
description: 有关使用头的视线移动和眼睛追踪本机 DirectX 应用中的开发人员指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 提供注视、 头的视线移动、 头跟踪、 眼睛追踪、 directx、 输入、 全息
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414410"
---
# <a name="head-and-eye-gaze-input-in-directx"></a>头节点和关注注视中 DirectX 的输入

在 Windows Mixed Reality、 关注和头注视输入用于确定用户在查看。 这可用于驱动主输入的模型，如[头的视线移动并提交](gaze-and-commit.md)，并还提供上下文的类型的交互。 有两种类型的视线移动矢量通过 API 可用： 头的视线移动和关注的视线移动。  二者均提供作为三个维 ray 使用源和方向。 应用程序然后可以 raycast 到其场景或现实生活中，并确定用户目标。

**Head 注视**表示用户的 head 指向中的方向。 将此视为位置和设备本身的向前方向，与表示在中心的位置点在两个显示器之间。  Head 的视线移动是所有混合现实设备上可用。

**关注的视线移动**表示要在用户的眼睛的方向。 原点位于用户的眼球之间。  它是包含密切关注跟踪系统的混合现实设备上可用。

Head 和关注的视线移动光线是可通过访问[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API。 只需调用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)接收新 SpatialPointerPose 对象在指定时间戳处并[坐标系](coordinate-systems-in-directx.md)。 此 SpatialPointerPose 包含头的视线移动起点和方向。 它还包含眼睛的视线移动起点和方向的眼跟踪是否可用。

## <a name="using-head-gaze"></a>使用头的视线移动

若要访问头的视线移动，开始通过调用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)接收新 SpatialPointerPose 对象。 您需要传递以下参数。
 - 一个[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)表示头的视线移动所需的坐标系统。 这由*坐标系*变量在下面的代码。 有关详细信息，请访问我们[坐标系](coordinate-systems-in-directx.md)开发人员指南。
 - 一个[时间戳](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)表示头部姿势请求的确切时间。  通常将使用对应于何时能够显示当前帧的时间的时间戳。 可以获取来自此预计的显示时间戳[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)对象，它是可通过当前访问[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。  此 HolographicFramePrediction 对象表示由*预测*变量在下面的代码。

 有效 SpatialPointerPose 后，头位置和正向是属性的可访问性。  下面的代码演示如何对其进行访问。

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a>使用关注的视线移动

关注的视线移动 API 是非常类似于头的视线移动。  它使用相同[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API，它提供一条射线原点和针对您的场景可以 raycast 的方向。  唯一的区别是，您需要显式启用使用之前的眼跟踪。 为此，您需要执行两个步骤：
1. 请求使用的眼跟踪应用程序中的用户权限。
2. 启用包清单中的"注视输入"功能。

### <a name="requesting-access-to-gaze-input"></a>请求访问注视输入
当您的应用程序正在启动时，调用[EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)眼跟踪请求访问。 系统将提示用户如果需要并返回[GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)后授予访问权限。 这是管理的异步调用，因此它需要进行一些额外。 下面的示例启动时要等待的结果，并将其存储到名为的成员变量分离 std::thread *m_isEyeTrackingEnabled*。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
正在启动的已分离的线程是一个选项来处理异步调用。  或者，您可以使用新[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)支持的功能C++/WinRT。
下面是请求用户权限的另一个示例：
-   EyesPose::IsSupported() 允许应用程序触发权限对话框中才关注跟踪器。
-   GazeInputAccessStatus m_gazeInputAccessStatus;这是为了防止反复地弹出权限提示。

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a>声明*注视输入*功能

双击的 appxmanifest 文件中*解决方案资源管理器*。  然后导航到*功能*部分，并检查*注视输入*功能。 

![注视输入的功能](images/gaze-input-capability.png)

这将添加以下行*包*appxmanifest 文件中的部分：
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>获取关注的视线移动 ray
一旦收到对等的访问，你可以随意获取关注的视线移动 ray 每一帧。  与头的视线移动，获得[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose)通过调用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)与所需的时间戳和坐标系统。 包含 SpatialPointerPose [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)对象，通过[眼睛](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)属性。 这为非 null 才启用的眼跟踪。 从此处可以检查设备中的用户是否通过调用跟踪校准关注[EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)。  接下来，使用[注视](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)属性来获取[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing 眼睛看一下位置和方向。 视线移动属性可以有时为 null，因此请确保对此进行检查。 这可能发生。 如果已校准的用户暂时关闭自己眼

下面的代码演示如何访问关注的视线移动 ray。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a>关联的视线移动的其他输入

有时可能会发现您需要[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)过去与事件对应。 例如，如果用户执行以无线方式点击，您的应用程序可能想要知道他们已查看的内容。 为此，只需使用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)与预测帧时间是不准确的由于系统输入的处理和显示时间之间的延迟。 此外，如果使用为目标的眼睛的视线移动，竞争对手的动态往往会移动甚至在完成提交操作之前。 这是不是个问题的简单空气点击，但与快速关注移动合并长语音命令时变得越来越重要。 若要处理这种情况的一种方法是发出其他调用到[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)，使用对应于输入事件的历史时间戳。  

但是，对于通过 SpatialInteractionManager 路由的输入，没有更简单的方法。 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)具有其自己[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函数。 调用将提供完全相关[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)而无需猜测。 有关如何使用 SpatialInteractionSourceStates 的详细信息，看一看[双手和 DirectX 中动作控制器](hands-and-motion-controllers-in-directx.md)文档。

## <a name="see-also"></a>请参阅
* [请提供注视，提交输入的模型](gaze-and-commit.md)
* [关注注视 HoloLens 2 上](eye-tracking.md)
* [DirectX 中的坐标系统](coordinate-systems-in-directx.md)
* [在 DirectX 语音输入](voice-input-in-directx.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
