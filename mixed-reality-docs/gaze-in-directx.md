---
title: 在 DirectX 中打印头和眼睛
description: 在本机 DirectX 应用中使用打印头和眼睛跟踪的开发人员指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 注视, 眼睛, 打印头跟踪, 眼睛跟踪, directx, 输入, 全息影像
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414410"
---
# <a name="head-and-eye-gaze-input-in-directx"></a>DirectX 中的头和眼睛眼睛输入

在 Windows Mixed Reality 中, 眼睛和头盔输入用于确定用户正在查看的内容。 这可以用于驱动诸如[打印头和提交](gaze-and-commit.md)等主要输入模型, 还可以为交互类型提供上下文。 可通过 API 使用两种注视向量: 打印头注视和眼睛。  两者都作为具有原点和方向的三维射线提供。 然后, 应用程序可以 raycast 到其幕后或现实世界, 确定用户的目标。

**打印头**看表示用户头指向的方向。 将此视为设备本身的位置和正向方向, 其位置表示两个显示器之间的中心点。  机头在所有混合现实设备上都可用。

**眼睛**看表示用户眼睛的方向。 原点位于用户的眼睛之间。  它在包含目视跟踪系统的混合现实设备上可用。

打印头和眼睛都可通过[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API 进行访问。 只需调用[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)即可在指定的时间戳和[坐标系统](coordinate-systems-in-directx.md)接收新的 SpatialPointerPose 对象。 此 SpatialPointerPose 包含一个注视原点和方向。 如果眼睛跟踪可用, 它还包含眼睛眼睛原点和方向。

## <a name="using-head-gaze"></a>使用打印头

若要访问打印头, 请首先调用[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)来接收新的 SpatialPointerPose 对象。 需要传递以下参数。
 - 一个[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , 表示打印头所需的坐标系统。 这由以下代码中的*坐标系*变量表示。 有关详细信息, 请访问我们的[坐标系统](coordinate-systems-in-directx.md)开发人员指南。
 - 表示请求的头姿势的确切时间的[时间戳](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)。  通常, 您将使用与当前帧的显示时间对应的时间戳。 可以从[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)对象获取此预测的显示时间戳, 该对象可通过当前[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)访问。  此 HolographicFramePrediction 对象由下面代码中的*预测*变量表示。

 获得有效的 SpatialPointerPose 后, 头位置和正向方向可作为属性进行访问。  下面的代码演示如何访问它们。

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

## <a name="using-eye-gaze"></a>使用目视注视

眼睛良好的 API 非常类似于打印头。  它使用相同的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, 该 API 提供了一个射线原点和方向, 你可以根据场景进行 raycast。  唯一的区别是, 在使用之前, 需要显式启用目视跟踪。 为此, 需要执行两个步骤:
1. 请求用户在应用中使用目视跟踪的权限。
2. 启用包清单中的 "注视输入" 功能。

### <a name="requesting-access-to-gaze-input"></a>正在请求访问注视输入
当你的应用程序启动时, 调用[EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)以请求访问目视跟踪。 系统将在需要时提示用户, 并在授予访问权限后返回[GazeInputAccessStatus:: 允许](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)。 这是一个异步调用, 因此需要进行一些额外的管理。 下面的示例旋转分离的 std:: thread 以等待结果, 并将其存储到名为*m_isEyeTrackingEnabled*的成员变量。

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
启动分离的线程只是一种用于处理异步调用的选项。  或者, 可以使用C++/WinRT. 支持的新的[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)功能
下面是要求用户提供权限的另一个示例:
-   仅当存在目视跟踪器时, EyesPose:: IsSupported () 允许应用程序触发权限对话框。
-   GazeInputAccessStatus m_gazeInputAccessStatus;这是为了防止反复弹出权限提示。

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

双击*解决方案资源管理器*中的 appxmanifest.xml 文件。  然后导航到 "*功能*" 部分, 并检查 "*注视输入*" 功能。 

![注视输入能力](images/gaze-input-capability.png)

这会将以下行添加到 appxmanifest.xml 文件的*Package*节:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>正在获取眼睛眼睛
接收到 ET 的访问权限后, 可以自由地获取每个帧的眼睛。  正如使用 head 注视一样, 通过使用所需的时间戳和坐标系统调用[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)获取[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 。 SpatialPointerPose 包含通过[眼睛](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)属性的[EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)对象。 只有启用了目视跟踪, 此值才为非 null。 在该处, 可以通过调用[EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)检查设备中的用户是否具有目视跟踪校准。  接下来, 使用 "[注视](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)" 属性获取[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing 的眼睛位置和方向。 "注视" 属性有时可以为 null, 因此请务必检查此值。 如果校准的用户暂时关闭了眼睛, 就会发生这种情况。

下面的代码演示如何访问眼睛眼睛。

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

## <a name="correlating-gaze-with-other-inputs"></a>将注视与其他输入关联

有时, 你可能会发现需要与过去的事件对应的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 。 例如, 如果用户执行点击, 你的应用可能需要知道他们正在查看的内容。 出于此目的, 只需将[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)与预测帧时间结合使用, 因为系统输入处理和显示时间之间存在延迟。 此外, 如果使用目视注视来设定目标, 则在完成提交操作之前, 我们的眼睛常常会继续。 这不是简单地点击的问题, 而是将长的语音命令与快速的目视运动组合在一起, 这一点更重要。 处理这种情况的一种方法是, 使用对应于输入事件的历史时间戳对[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)进行其他调用。  

但对于通过 SpatialInteractionManager 进行路由的输入, 有一种更简单的方法。 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)具有其自己的[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函数。 调用将提供完全相关的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) , 而无需猜测。 有关使用 SpatialInteractionSourceStates 的详细信息, 请参阅 DirectX 文档中的[双手和运动控制器](hands-and-motion-controllers-in-directx.md)。

## <a name="see-also"></a>请参阅
* [打印头和提交输入模型](gaze-and-commit.md)
* [目视-注视 HoloLens 2](eye-tracking.md)
* [DirectX 中的坐标系统](coordinate-systems-in-directx.md)
* [DirectX 中的语音输入](voice-input-in-directx.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
