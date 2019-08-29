---
title: 在 DirectX 中打印头和眼睛
description: 在本机 DirectX 应用中使用打印头和眼睛跟踪的开发人员指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 眼睛, 头盔, 打印头跟踪, 眼睛跟踪, directx, 输入, 全息影像
ms.openlocfilehash: 2197f0ba3ecb77188d532d77ba29595c380a039d
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122061"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="29648-104">DirectX 中的头盔和眼睛眼睛输入</span><span class="sxs-lookup"><span data-stu-id="29648-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="29648-105">在 Windows Mixed Reality 中, 眼睛和头盔输入用于确定用户正在查看的内容。</span><span class="sxs-lookup"><span data-stu-id="29648-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="29648-106">这可以用来驱动主要的输入模型, 如[注视和提交](gaze-and-commit.md), 还可以为交互类型提供上下文。</span><span class="sxs-lookup"><span data-stu-id="29648-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="29648-107">通过 API 可以使用两种类型的目视矢量: 打印头-注视和眼睛。</span><span class="sxs-lookup"><span data-stu-id="29648-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="29648-108">两者都作为具有原点和方向的三维射线提供。</span><span class="sxs-lookup"><span data-stu-id="29648-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="29648-109">然后, 应用程序可以 raycast 到其幕后或现实世界, 确定用户的目标。</span><span class="sxs-lookup"><span data-stu-id="29648-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="29648-110">**打印头**表示用户的头指向的方向。</span><span class="sxs-lookup"><span data-stu-id="29648-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="29648-111">将此视为设备本身的位置和正向方向, 其位置表示两个显示器之间的中心点。</span><span class="sxs-lookup"><span data-stu-id="29648-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="29648-112">打印头在所有混合现实设备上都可用。</span><span class="sxs-lookup"><span data-stu-id="29648-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="29648-113">**眼睛**表示用户眼睛正在寻找的方向。</span><span class="sxs-lookup"><span data-stu-id="29648-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="29648-114">原点位于用户的眼睛之间。</span><span class="sxs-lookup"><span data-stu-id="29648-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="29648-115">它在包含目视跟踪系统的混合现实设备上可用。</span><span class="sxs-lookup"><span data-stu-id="29648-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="29648-116">打印头和眼睛都可通过[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API 进行访问。</span><span class="sxs-lookup"><span data-stu-id="29648-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="29648-117">只需调用[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)即可在指定的时间戳和[坐标系统](coordinate-systems-in-directx.md)接收新的 SpatialPointerPose 对象。</span><span class="sxs-lookup"><span data-stu-id="29648-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="29648-118">此 SpatialPointerPose 包含一个头部和方向。</span><span class="sxs-lookup"><span data-stu-id="29648-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="29648-119">它还包含目视的原点和方向 (如果眼睛跟踪可用)。</span><span class="sxs-lookup"><span data-stu-id="29648-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="29648-120">使用打印头</span><span class="sxs-lookup"><span data-stu-id="29648-120">Using head-gaze</span></span>

<span data-ttu-id="29648-121">若要访问 head, 请首先调用[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)以接收新的 SpatialPointerPose 对象。</span><span class="sxs-lookup"><span data-stu-id="29648-121">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="29648-122">需要传递以下参数。</span><span class="sxs-lookup"><span data-stu-id="29648-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="29648-123">表示[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)的所需坐标系统的表示。</span><span class="sxs-lookup"><span data-stu-id="29648-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="29648-124">这由以下代码中的*坐标系*变量表示。</span><span class="sxs-lookup"><span data-stu-id="29648-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="29648-125">有关详细信息, 请访问我们的[坐标系统](coordinate-systems-in-directx.md)开发人员指南。</span><span class="sxs-lookup"><span data-stu-id="29648-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="29648-126">表示请求的头姿势的确切时间的[时间戳](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)。</span><span class="sxs-lookup"><span data-stu-id="29648-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="29648-127">通常, 您将使用与当前帧的显示时间对应的时间戳。</span><span class="sxs-lookup"><span data-stu-id="29648-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="29648-128">可以从[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)对象获取此预测的显示时间戳, 该对象可通过当前[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)访问。</span><span class="sxs-lookup"><span data-stu-id="29648-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="29648-129">此 HolographicFramePrediction 对象由下面代码中的*预测*变量表示。</span><span class="sxs-lookup"><span data-stu-id="29648-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="29648-130">获得有效的 SpatialPointerPose 后, 头位置和正向方向可作为属性进行访问。</span><span class="sxs-lookup"><span data-stu-id="29648-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="29648-131">下面的代码演示如何访问它们。</span><span class="sxs-lookup"><span data-stu-id="29648-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="29648-132">使用红眼</span><span class="sxs-lookup"><span data-stu-id="29648-132">Using eye-gaze</span></span>

<span data-ttu-id="29648-133">眼睛良好的 API 非常类似于打印头。</span><span class="sxs-lookup"><span data-stu-id="29648-133">The eye-gaze API is very similar to head-gaze.</span></span>  <span data-ttu-id="29648-134">它使用相同的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, 该 API 提供了一个射线原点和方向, 你可以根据场景进行 raycast。</span><span class="sxs-lookup"><span data-stu-id="29648-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="29648-135">唯一的区别是, 在使用之前, 需要显式启用目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="29648-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="29648-136">为此, 需要执行两个步骤:</span><span class="sxs-lookup"><span data-stu-id="29648-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="29648-137">请求用户在应用中使用目视跟踪的权限。</span><span class="sxs-lookup"><span data-stu-id="29648-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="29648-138">启用包清单中的 "注视输入" 功能。</span><span class="sxs-lookup"><span data-stu-id="29648-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="29648-139">正在请求访问目视输入</span><span class="sxs-lookup"><span data-stu-id="29648-139">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="29648-140">当你的应用程序启动时, 调用[EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)以请求访问目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="29648-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="29648-141">系统将在需要时提示用户, 并在授予访问权限后返回[GazeInputAccessStatus:: 允许](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)。</span><span class="sxs-lookup"><span data-stu-id="29648-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="29648-142">这是一个异步调用, 因此需要进行一些额外的管理。</span><span class="sxs-lookup"><span data-stu-id="29648-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="29648-143">下面的示例旋转分离的 std:: thread 以等待结果, 并将其存储到名为*m_isEyeTrackingEnabled*的成员变量。</span><span class="sxs-lookup"><span data-stu-id="29648-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="29648-144">启动分离的线程只是一种用于处理异步调用的选项。</span><span class="sxs-lookup"><span data-stu-id="29648-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="29648-145">或者, 可以使用C++/WinRT. 支持的新的[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)功能</span><span class="sxs-lookup"><span data-stu-id="29648-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="29648-146">下面是要求用户提供权限的另一个示例:</span><span class="sxs-lookup"><span data-stu-id="29648-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="29648-147">仅当存在目视跟踪器时, EyesPose:: IsSupported () 允许应用程序触发权限对话框。</span><span class="sxs-lookup"><span data-stu-id="29648-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="29648-148">GazeInputAccessStatus m_gazeInputAccessStatus;这是为了防止反复弹出权限提示。</span><span class="sxs-lookup"><span data-stu-id="29648-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="29648-149">声明*注视输入*功能</span><span class="sxs-lookup"><span data-stu-id="29648-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="29648-150">双击*解决方案资源管理器*中的 appxmanifest.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="29648-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="29648-151">然后导航到 "*功能*" 部分, 并检查 "*注视输入*" 功能。</span><span class="sxs-lookup"><span data-stu-id="29648-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![注视输入能力](images/gaze-input-capability.png)

<span data-ttu-id="29648-153">这会将以下行添加到 appxmanifest.xml 文件的*Package*节:</span><span class="sxs-lookup"><span data-stu-id="29648-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="29648-154">获取眼睛眼睛</span><span class="sxs-lookup"><span data-stu-id="29648-154">Getting the eye-gaze ray</span></span>
<span data-ttu-id="29648-155">接收到 ET 的访问权限后, 即可自由地抓住每个帧的眼睛。</span><span class="sxs-lookup"><span data-stu-id="29648-155">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="29648-156">正如在打印头上一样, 通过使用所需的时间戳和坐标系统调用[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)来获取[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 。</span><span class="sxs-lookup"><span data-stu-id="29648-156">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="29648-157">SpatialPointerPose 包含通过[眼睛](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)属性的[EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)对象。</span><span class="sxs-lookup"><span data-stu-id="29648-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="29648-158">只有启用了目视跟踪, 此值才为非 null。</span><span class="sxs-lookup"><span data-stu-id="29648-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="29648-159">在该处, 可以通过调用[EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)检查设备中的用户是否具有目视跟踪校准。</span><span class="sxs-lookup"><span data-stu-id="29648-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="29648-160">接下来, 使用 "[注视](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)" 属性来获取眼睛眼睛和方向的[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing。</span><span class="sxs-lookup"><span data-stu-id="29648-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye-gaze position and direction.</span></span> <span data-ttu-id="29648-161">"注视" 属性有时可以为 null, 因此请务必检查此值。</span><span class="sxs-lookup"><span data-stu-id="29648-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="29648-162">如果校准的用户暂时关闭了眼睛, 就会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="29648-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="29648-163">下面的代码演示如何访问眼睛眼睛。</span><span class="sxs-lookup"><span data-stu-id="29648-163">The following code shows how to access the eye-gaze ray.</span></span>

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
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="29648-164">将注视与其他输入关联</span><span class="sxs-lookup"><span data-stu-id="29648-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="29648-165">有时, 你可能会发现需要与过去的事件对应的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 。</span><span class="sxs-lookup"><span data-stu-id="29648-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="29648-166">例如, 如果用户执行点击, 你的应用可能需要知道他们正在查看的内容。</span><span class="sxs-lookup"><span data-stu-id="29648-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="29648-167">出于此目的, 只需将[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)与预测帧时间结合使用, 因为系统输入处理和显示时间之间存在延迟。</span><span class="sxs-lookup"><span data-stu-id="29648-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="29648-168">此外, 如果使用目视目视定位, 则即使在完成提交操作之前, 我们也可能会继续。</span><span class="sxs-lookup"><span data-stu-id="29648-168">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="29648-169">这不是简单地点击的问题, 而是将长的语音命令与快速的目视运动组合在一起, 这一点更重要。</span><span class="sxs-lookup"><span data-stu-id="29648-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="29648-170">处理这种情况的一种方法是, 使用对应于输入事件的历史时间戳对[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)进行其他调用。</span><span class="sxs-lookup"><span data-stu-id="29648-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="29648-171">但对于通过 SpatialInteractionManager 进行路由的输入, 有一种更简单的方法。</span><span class="sxs-lookup"><span data-stu-id="29648-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="29648-172">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)具有其自己的[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函数。</span><span class="sxs-lookup"><span data-stu-id="29648-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="29648-173">调用将提供完全相关的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) , 而无需猜测。</span><span class="sxs-lookup"><span data-stu-id="29648-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="29648-174">有关使用 SpatialInteractionSourceStates 的详细信息, 请参阅 DirectX 文档中的[双手和运动控制器](hands-and-motion-controllers-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="29648-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="29648-175">请参阅</span><span class="sxs-lookup"><span data-stu-id="29648-175">See also</span></span>
* [<span data-ttu-id="29648-176">打印头和提交输入模型</span><span class="sxs-lookup"><span data-stu-id="29648-176">Head-gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="29648-177">目视-注视 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="29648-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="29648-178">校准</span><span class="sxs-lookup"><span data-stu-id="29648-178">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="29648-179">DirectX 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="29648-179">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="29648-180">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="29648-180">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="29648-181">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="29648-181">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
