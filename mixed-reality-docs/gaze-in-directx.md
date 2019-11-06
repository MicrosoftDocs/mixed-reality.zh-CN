---
title: 在 DirectX 中打印头和眼睛
description: 在本机 DirectX 应用中使用打印头和眼睛跟踪的开发人员指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 眼睛，头盔，打印头跟踪，眼睛跟踪，directx，输入，全息影像
ms.openlocfilehash: 48188cc8c886b371847357701b42249f486bceac
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641122"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="7e8e7-104">DirectX 中的头盔和眼睛眼睛输入</span><span class="sxs-lookup"><span data-stu-id="7e8e7-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="7e8e7-105">在 Windows Mixed Reality 中，眼睛和头盔输入用于确定用户正在查看的内容。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="7e8e7-106">这可以用来驱动主要的输入模型，如[注视和提交](gaze-and-commit.md)，还可以为交互类型提供上下文。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="7e8e7-107">通过 API 可以使用两种类型的目视矢量：打印头-注视和眼睛。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="7e8e7-108">两者都作为具有原点和方向的三维射线提供。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="7e8e7-109">然后，应用程序可以 raycast 到其幕后或现实世界，确定用户的目标。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="7e8e7-110">**打印头**表示用户的头指向的方向。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="7e8e7-111">将此视为设备本身的位置和正向方向，其位置表示两个显示器之间的中心点。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="7e8e7-112">打印头在所有混合现实设备上都可用。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="7e8e7-113">**眼睛**表示用户眼睛正在寻找的方向。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="7e8e7-114">原点位于用户的眼睛之间。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="7e8e7-115">它在包含目视跟踪系统的混合现实设备上可用。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="7e8e7-116">打印头和眼睛都可通过[SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API 进行访问。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="7e8e7-117">只需调用[SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)即可在指定的时间戳和[坐标系统](coordinate-systems-in-directx.md)接收新的 SpatialPointerPose 对象。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="7e8e7-118">此 SpatialPointerPose 包含一个头部和方向。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="7e8e7-119">它还包含目视的原点和方向（如果眼睛跟踪可用）。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

### <a name="device-support"></a><span data-ttu-id="7e8e7-120">设备支持</span><span class="sxs-lookup"><span data-stu-id="7e8e7-120">Device support</span></span>
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="7e8e7-121"><strong>具有</strong></span><span class="sxs-lookup"><span data-stu-id="7e8e7-121"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="7e8e7-122"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e8e7-122"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="7e8e7-123"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7e8e7-123"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="7e8e7-124"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e8e7-124"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="7e8e7-125">头部凝视</span><span class="sxs-lookup"><span data-stu-id="7e8e7-125">Head-gaze</span></span></td>
     <td><span data-ttu-id="7e8e7-126">✔️</span><span class="sxs-lookup"><span data-stu-id="7e8e7-126">✔️</span></span></td>
     <td><span data-ttu-id="7e8e7-127">✔️</span><span class="sxs-lookup"><span data-stu-id="7e8e7-127">✔️</span></span></td>
     <td><span data-ttu-id="7e8e7-128">✔️</span><span class="sxs-lookup"><span data-stu-id="7e8e7-128">✔️</span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="7e8e7-129">眼睛-注视</span><span class="sxs-lookup"><span data-stu-id="7e8e7-129">Eye-gaze</span></span></td>
     <td>❌</td>
     <td><span data-ttu-id="7e8e7-130">✔️</span><span class="sxs-lookup"><span data-stu-id="7e8e7-130">✔️</span></span></td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a><span data-ttu-id="7e8e7-131">使用打印头</span><span class="sxs-lookup"><span data-stu-id="7e8e7-131">Using head-gaze</span></span>

<span data-ttu-id="7e8e7-132">若要访问 head，请首先调用[SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)以接收新的 SpatialPointerPose 对象。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-132">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="7e8e7-133">需要传递以下参数。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-133">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="7e8e7-134">表示[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem)的所需坐标系统的表示。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-134">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="7e8e7-135">这由以下代码中的*坐标系*变量表示。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-135">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="7e8e7-136">有关详细信息，请访问我们的[坐标系统](coordinate-systems-in-directx.md)开发人员指南。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-136">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="7e8e7-137">表示请求的头姿势的确切时间的[时间戳](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-137">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="7e8e7-138">通常，您将使用与当前帧的显示时间对应的时间戳。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-138">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="7e8e7-139">可以从[HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)对象获取此预测的显示时间戳，该对象可通过当前[HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)访问。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-139">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="7e8e7-140">此 HolographicFramePrediction 对象由下面代码中的*预测*变量表示。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-140">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="7e8e7-141">获得有效的 SpatialPointerPose 后，头位置和正向方向可作为属性进行访问。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-141">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="7e8e7-142">下面的代码演示如何访问它们。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-142">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="7e8e7-143">使用红眼</span><span class="sxs-lookup"><span data-stu-id="7e8e7-143">Using eye-gaze</span></span>

<span data-ttu-id="7e8e7-144">请注意，为了让用户使用目视输入，每个用户首次使用设备时必须进行[跟踪跟踪用户校准](calibration.md)。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-144">Please note that for your users to use eye-gaze input, each user has to go through an [eye tracking user calibration](calibration.md) the first time they use the device.</span></span> <span data-ttu-id="7e8e7-145">眼睛良好的 API 非常类似于打印头。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-145">The eye-gaze API is very similar to head-gaze.</span></span>
<span data-ttu-id="7e8e7-146">它使用相同的[SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API，该 API 提供了一个射线原点和方向，你可以根据场景进行 raycast。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-146">It uses the same [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="7e8e7-147">唯一的区别是，在使用之前，需要显式启用目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-147">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="7e8e7-148">为此，需要执行两个步骤：</span><span class="sxs-lookup"><span data-stu-id="7e8e7-148">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="7e8e7-149">请求用户在应用中使用目视跟踪的权限。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-149">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="7e8e7-150">启用包清单中的 "注视输入" 功能。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-150">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="7e8e7-151">正在请求访问目视输入</span><span class="sxs-lookup"><span data-stu-id="7e8e7-151">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="7e8e7-152">当你的应用程序启动时，调用[EyesPose：： RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)以请求访问目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-152">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="7e8e7-153">系统将在需要时提示用户，并在授予访问权限后返回[GazeInputAccessStatus：：允许](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus)。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-153">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="7e8e7-154">这是一个异步调用，因此需要进行一些额外的管理。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-154">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="7e8e7-155">下面的示例旋转分离的 std：： thread 以等待结果，并将其存储到名为*m_isEyeTrackingEnabled*的成员变量。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-155">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="7e8e7-156">启动分离的线程只是一种用于处理异步调用的选项。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-156">Starting a detached thread is just one option for handling async calls.</span></span> <span data-ttu-id="7e8e7-157">或者，可以使用C++/WinRT. 支持的新的[co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency)功能</span><span class="sxs-lookup"><span data-stu-id="7e8e7-157">Alternatively, you could use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="7e8e7-158">下面是要求用户提供权限的另一个示例：</span><span class="sxs-lookup"><span data-stu-id="7e8e7-158">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="7e8e7-159">仅当存在目视跟踪器时，EyesPose：： IsSupported （）允许应用程序触发权限对话框。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-159">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="7e8e7-160">GazeInputAccessStatus m_gazeInputAccessStatus;这是为了防止反复弹出权限提示。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-160">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="7e8e7-161">声明*注视输入*功能</span><span class="sxs-lookup"><span data-stu-id="7e8e7-161">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="7e8e7-162">双击*解决方案资源管理器*中的 appxmanifest.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-162">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="7e8e7-163">然后导航到 "*功能*" 部分，并检查 "*注视输入*" 功能。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-163">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![注视输入能力](images/gaze-input-capability.png)

<span data-ttu-id="7e8e7-165">这会将以下行添加到 appxmanifest.xml 文件的*Package*节：</span><span class="sxs-lookup"><span data-stu-id="7e8e7-165">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="7e8e7-166">获取眼睛眼睛</span><span class="sxs-lookup"><span data-stu-id="7e8e7-166">Getting the eye-gaze ray</span></span>
<span data-ttu-id="7e8e7-167">接收到 ET 的访问权限后，即可自由地抓住每个帧的眼睛。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-167">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="7e8e7-168">正如在打印头上一样，通过使用所需的时间戳和坐标系统调用[SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)来获取[SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-168">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="7e8e7-169">SpatialPointerPose 包含通过[眼睛](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)属性的[EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose)对象。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-169">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="7e8e7-170">只有启用了目视跟踪，此值才为非 null。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-170">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="7e8e7-171">在该处，可以通过调用[EyesPose：： IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)检查设备中的用户是否具有目视跟踪校准。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-171">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="7e8e7-172">接下来，使用 "[注视](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)" 属性来获取眼睛眼睛和方向的[SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) contianing。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-172">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) contianing the eye-gaze position and direction.</span></span> <span data-ttu-id="7e8e7-173">"注视" 属性有时可以为 null，因此请务必检查此值。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-173">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="7e8e7-174">如果校准的用户暂时关闭了眼睛，就会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-174">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="7e8e7-175">下面的代码演示如何访问眼睛眼睛。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-175">The following code shows how to access the eye-gaze ray.</span></span>

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

## <a name="fallback-when-eye-tracking-is-not-available"></a><span data-ttu-id="7e8e7-176">当目视跟踪不可用时回退</span><span class="sxs-lookup"><span data-stu-id="7e8e7-176">Fallback when eye tracking is not available</span></span>
<span data-ttu-id="7e8e7-177">如我们的[眼睛跟踪设计文档](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available)中所述，设计人员和开发人员都应注意到，可能存在一些可能无法用于应用程序的目视跟踪数据的实例。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-177">As mentioned in our [eye tracking design docs](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), both designers as well as developers should be aware that there may be instances in which eye tracking data may not be available to your app.</span></span>
<span data-ttu-id="7e8e7-178">这种情况的原因有很多，包括用户不进行校准，用户拒绝了应用程序访问其眼睛跟踪数据或临时 interferences （例如，在 HoloLens 面板上出现污迹或用户眼睛 occluding）。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-178">There are various reasons for this ranging from a user not being calibrated, the user having denied the app access to his/her eye tracking data or simply temporary interferences (such as smudges on the HoloLens visor or hair occluding the user's eyes).</span></span> <span data-ttu-id="7e8e7-179">虽然本文档中已提到了某些 Api，但在下面的部分中，我们提供了有关如何检测目视跟踪是否可用作快速参考的摘要：</span><span class="sxs-lookup"><span data-stu-id="7e8e7-179">While some of the APIs have already been mentioned in this document, in the following, we provide a summary of how to detect that eye tracking is available as a quick reference:</span></span> 

* <span data-ttu-id="7e8e7-180">检查系统是否完全支持目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-180">Check that the system supports eye tracking at all.</span></span> <span data-ttu-id="7e8e7-181">调用以下*方法*： [EyesPose. IsSupported （）](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span><span class="sxs-lookup"><span data-stu-id="7e8e7-181">Call the following *method*: [Windows.Perception.People.EyesPose.IsSupported()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)</span></span>

* <span data-ttu-id="7e8e7-182">检查是否校准了用户。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-182">Check that the user is calibrated.</span></span> <span data-ttu-id="7e8e7-183">调用以下*属性*： [EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span><span class="sxs-lookup"><span data-stu-id="7e8e7-183">Call the following *property*: [Windows.Perception.People.EyesPose.IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)</span></span> 

* <span data-ttu-id="7e8e7-184">检查用户是否已授予你的应用程序权限以使用其目视跟踪数据：检索当前的 _"GazeInputAccessStatus"_ 。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-184">Check that the user has given your app permission to use their eye tracking data: Retrieve the current _'GazeInputAccessStatus'_.</span></span> <span data-ttu-id="7e8e7-185">有关如何执行此操作的示例，请参阅[请求访问注视输入](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-185">An example on how to do this is explained at [Requesting access to gaze input](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).</span></span>   

<span data-ttu-id="7e8e7-186">此外，你可能需要通过在收到的目视跟踪数据更新之间添加超时，并以其他方式回退到下面所述的打印头来检查眼睛跟踪数据是否过时。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-186">In addition, you may want to check that your eye tracking data is not stale by adding a timeout between received eye tracking data updates and otherwise fallback to head-gaze as discussed below.</span></span>  
<span data-ttu-id="7e8e7-187">有关详细信息，请访问我们的[回退设计注意事项](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available)。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-187">Please visit our [fallback design considerations](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) for more information.</span></span>

<br>

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="7e8e7-188">将注视与其他输入关联</span><span class="sxs-lookup"><span data-stu-id="7e8e7-188">Correlating gaze with other inputs</span></span>
<span data-ttu-id="7e8e7-189">有时，你可能会发现需要与过去的事件对应的[SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) 。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-189">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="7e8e7-190">例如，如果用户执行点击，你的应用可能需要知道他们正在查看的内容。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-190">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="7e8e7-191">出于此目的，只需将[SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)与预测帧时间结合使用，因为系统输入处理和显示时间之间存在延迟。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-191">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="7e8e7-192">此外，如果使用目视目视定位，则即使在完成提交操作之前，我们也可能会继续。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-192">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="7e8e7-193">这不是简单地点击的问题，而是将长的语音命令与快速的目视运动组合在一起，这一点更重要。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-193">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="7e8e7-194">处理这种情况的一种方法是，使用对应于输入事件的历史时间戳对[SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)进行其他调用。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-194">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="7e8e7-195">但对于通过 SpatialInteractionManager 进行路由的输入，有一种更简单的方法。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-195">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="7e8e7-196">[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)具有其自己的[TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函数。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-196">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="7e8e7-197">调用将提供完全相关的[SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) ，而无需猜测。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-197">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="7e8e7-198">有关使用 SpatialInteractionSourceStates 的详细信息，请参阅 DirectX 文档中的[双手和运动控制器](hands-and-motion-controllers-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-198">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

<br>

## <a name="calibration"></a><span data-ttu-id="7e8e7-199">校准</span><span class="sxs-lookup"><span data-stu-id="7e8e7-199">Calibration</span></span>
<span data-ttu-id="7e8e7-200">为了使目视跟踪能准确地工作，每个用户都需要经历[跟踪用户校准](calibration.md)。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-200">For eye tracking to work accurately, each user is required to go through an [eye tracking user calibration](calibration.md).</span></span> <span data-ttu-id="7e8e7-201">这允许设备调整系统，以便为用户提供更舒适和更高的质量查看体验，并确保同时进行准确的目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-201">This allows the device to adjust the system for a more comfortable and higher quality viewing experience for the user and to ensure accurate eye tracking at the same time.</span></span> <span data-ttu-id="7e8e7-202">开发人员无需执行任何操作即可管理用户校准。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-202">Developers don’t need to do anything on their end to manage user calibration.</span></span> <span data-ttu-id="7e8e7-203">系统将在以下情况下确保系统提示用户校准设备： \* 用户第一次使用设备 \* \* 用户以前选择退出校准过程 \* 校准过程未成功完成最后一次用户使用设备的时间</span><span class="sxs-lookup"><span data-stu-id="7e8e7-203">The system will ensure that the user gets prompted to calibrate the device under the following circumstances: \*The user is using the device for the first time \*The user previously opted out of the calibration process \*The calibration process did not succeed the last time the user used the device</span></span>

<span data-ttu-id="7e8e7-204">开发人员应确保为可能无法提供目视跟踪数据的用户提供足够的支持。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-204">Developers should make sure to provide adequate support for users for whom eye tracking data may not be available.</span></span> <span data-ttu-id="7e8e7-205">详细了解[Hololens 2 上的目视跟踪](eye-tracking.md)中的备用解决方案注意事项。</span><span class="sxs-lookup"><span data-stu-id="7e8e7-205">Learn more about considerations for fallback solutions at [Eye tracking on Hololens 2](eye-tracking.md).</span></span>

<br>

## <a name="see-also"></a><span data-ttu-id="7e8e7-206">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e8e7-206">See also</span></span>
* [<span data-ttu-id="7e8e7-207">校准</span><span class="sxs-lookup"><span data-stu-id="7e8e7-207">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="7e8e7-208">DirectX 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="7e8e7-208">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="7e8e7-209">目视-注视 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7e8e7-209">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="7e8e7-210">注视并提交输入模型</span><span class="sxs-lookup"><span data-stu-id="7e8e7-210">Gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="7e8e7-211">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="7e8e7-211">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="7e8e7-212">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="7e8e7-212">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
