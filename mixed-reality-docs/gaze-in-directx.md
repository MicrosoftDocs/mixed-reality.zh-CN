---
title: 在 DirectX 中的头节点和关注视线移动
description: 有关使用头的视线移动和眼睛追踪本机 DirectX 应用中的开发人员指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 提供注视、 头的视线移动、 头跟踪、 眼睛追踪、 directx、 输入、 全息
ms.openlocfilehash: f9764132df0ca4ae2f02d8f9a5740530676eb4f5
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629610"
---
# <a name="head-and-eye-gaze-in-directx"></a><span data-ttu-id="f3e4c-104">在 DirectX 中的头节点和关注视线移动</span><span class="sxs-lookup"><span data-stu-id="f3e4c-104">Head and eye gaze in DirectX</span></span>

<span data-ttu-id="f3e4c-105">在 Windows Mixed Reality 注视输入用于确定用户在查看。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-105">In Windows Mixed Reality, gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="f3e4c-106">这可用于驱动主输入的模型，如[注视并提交](gaze-and-commit.md)，并还提供上下文的类型的交互。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-106">This can be used to drive primary input models such as [gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="f3e4c-107">有两种类型的视线移动矢量通过 API 可用： 头的视线移动和关注的视线移动。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="f3e4c-108">二者均提供作为三个维 ray 使用源和方向。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="f3e4c-109">应用程序然后可以 raycast 到其场景或现实生活中，并确定用户目标。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="f3e4c-110">**Head 注视**表示用户的 head 指向中的方向。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="f3e4c-111">将此视为位置和设备本身的向前方向，与表示在中心的位置点在两个显示器之间。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="f3e4c-112">Head 的视线移动是所有混合现实设备上可用。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="f3e4c-113">**关注的视线移动**表示要在用户的眼睛的方向。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="f3e4c-114">原点位于用户的眼球之间。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="f3e4c-115">它是包含密切关注跟踪系统的混合现实设备上可用。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="f3e4c-116">Head 和关注的视线移动光线是可通过访问[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="f3e4c-117">只需调用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)接收新 SpatialPointerPose 对象在指定时间戳处并[坐标系](coordinate-systems-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to recieve a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="f3e4c-118">此 SpatialPointerPose 包含头的视线移动起点和方向。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="f3e4c-119">它还包含眼睛的视线移动起点和方向的眼跟踪是否可用。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="f3e4c-120">使用头的视线移动</span><span class="sxs-lookup"><span data-stu-id="f3e4c-120">Using head gaze</span></span>

<span data-ttu-id="f3e4c-121">若要访问头的视线移动，开始通过调用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)接收新 SpatialPointerPose 对象。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to recieve a new SpatialPointerPose object.</span></span> <span data-ttu-id="f3e4c-122">您需要传递以下参数。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="f3e4c-123">一个[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)表示头的视线移动所需的坐标系统。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="f3e4c-124">这由*坐标系*变量在下面的代码。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="f3e4c-125">有关详细信息，请访问我们[坐标系](coordinate-systems-in-directx.md)开发人员指南。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="f3e4c-126">一个[时间戳](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)表示头部姿势请求的确切时间。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="f3e4c-127">通常将使用对应于何时能够显示当前帧的时间的时间戳。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="f3e4c-128">可以获取来自此预计的显示时间戳[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)对象，它是可通过当前访问[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="f3e4c-129">此 HolographicFramePrediction 对象表示由*预测*变量在下面的代码。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="f3e4c-130">有效 SpatialPointerPose 后，头位置和正向是属性的可访问性。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="f3e4c-131">下面的代码演示如何对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-131">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="f3e4c-132">使用关注的视线移动</span><span class="sxs-lookup"><span data-stu-id="f3e4c-132">Using eye gaze</span></span>

<span data-ttu-id="f3e4c-133">关注的视线移动 API 是非常类似于头的视线移动。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="f3e4c-134">它使用相同[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API，它提供一条射线原点和针对您的场景可以 raycast 的方向。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="f3e4c-135">唯一的区别是您需要以显式方式启用跟踪，再使用它通过请求访问的关注。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-135">The only difference is you need to explicitly enable eye tracking before using it by requesting access.</span></span>

### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="f3e4c-136">声明*注视输入*功能</span><span class="sxs-lookup"><span data-stu-id="f3e4c-136">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="f3e4c-137">双击的 appxmanifest 文件中*解决方案资源管理器*。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-137">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="f3e4c-138">然后导航到*功能*部分，并检查*注视输入*功能。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-138">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![注视输入的功能](images/gaze-input-capability.png)

<span data-ttu-id="f3e4c-140">这将添加以下行*包*appxmanifest 文件中的部分：</span><span class="sxs-lookup"><span data-stu-id="f3e4c-140">This adds the following lines to the *Package* section in the  appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="f3e4c-141">请求访问注视输入</span><span class="sxs-lookup"><span data-stu-id="f3e4c-141">Requesting access to gaze input</span></span>
<span data-ttu-id="f3e4c-142">当您的应用程序正在启动时，调用[EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)眼跟踪请求访问。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-142">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="f3e4c-143">系统将提示用户如果需要并返回[GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)后授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-143">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="f3e4c-144">这是管理的异步调用，因此它需要进行一些额外。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-144">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="f3e4c-145">下面的示例启动时要等待的结果，并将其存储到名为的成员变量分离 std::thread *m_isEyeTrackingEnabled*。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-145">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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

<span data-ttu-id="f3e4c-146">正在启动的已分离的线程是一个选项来处理异步调用。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-146">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="f3e4c-147">或者，您可以使用新[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)支持的功能C++/WinRT。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-147">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="f3e4c-148">获取关注的视线移动 ray</span><span class="sxs-lookup"><span data-stu-id="f3e4c-148">Getting the eye gaze ray</span></span>

<span data-ttu-id="f3e4c-149">一旦收到对等的访问，你可以随意获取关注的视线移动 ray 每一帧。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-149">Once you have recieved access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="f3e4c-150">与头的视线移动，获得[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose)通过调用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)与所需的时间戳和坐标系统。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-150">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="f3e4c-151">包含 SpatialPointerPose [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)对象，通过[眼睛](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)属性。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-151">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="f3e4c-152">这为非 null 才启用的眼跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-152">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="f3e4c-153">从此处可以检查设备中的用户是否通过调用跟踪校准关注[EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-153">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="f3e4c-154">接下来，使用[注视](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)属性来获取[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing 眼睛看一下位置和方向。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-154">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="f3e4c-155">视线移动属性可以有时为 null，因此请确保对此进行检查。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-155">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="f3e4c-156">这可能发生。 如果已校准的用户暂时关闭自己眼</span><span class="sxs-lookup"><span data-stu-id="f3e4c-156">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="f3e4c-157">下面的代码演示如何访问关注的视线移动 ray。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-157">The following code shows how to access the eye gaze ray.</span></span>

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

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="f3e4c-158">关联的视线移动的其他输入</span><span class="sxs-lookup"><span data-stu-id="f3e4c-158">Correlating gaze with other inputs</span></span>

<span data-ttu-id="f3e4c-159">有时可能会发现您需要[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)过去与事件对应。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-159">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="f3e4c-160">例如，如果用户执行以无线方式点击，您的应用程序可能想要知道他们已查看的内容。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-160">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="f3e4c-161">为此，只需使用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)与预测帧时间是不准确的由于系统输入的处理和显示时间之间的延迟。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-161">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span>

<span data-ttu-id="f3e4c-162">若要处理这种情况的一种方法是发出其他调用到[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)，使用对应于输入事件的历史时间戳。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-162">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  <span data-ttu-id="f3e4c-163">但是，对于通过 SpatialInteractionManager 路由的输入，没有更简单的方法。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-163">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="f3e4c-164">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)具有其自己[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函数。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-164">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="f3e4c-165">调用将提供完全相关[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)而无需猜测。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-165">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="f3e4c-166">有关如何使用 SpatialInteractionSourceStates 的详细信息，看一看[双手和 DirectX 中动作控制器](hands-and-motion-controllers-in-directx.md)文档。</span><span class="sxs-lookup"><span data-stu-id="f3e4c-166">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3e4c-167">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3e4c-167">See also</span></span>
* [<span data-ttu-id="f3e4c-168">双手和动作中 DirectX 的控制器</span><span class="sxs-lookup"><span data-stu-id="f3e4c-168">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="f3e4c-169">DirectX 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="f3e4c-169">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="f3e4c-170">视线移动和提交的输入的模型</span><span class="sxs-lookup"><span data-stu-id="f3e4c-170">Gaze and commit input model</span></span>](gaze-and-commit.md)

