---
title: 提供注视、 手势和 DirectX 中的动作控制器
description: 将输入的来自提供注视、 手势和动作控制器相结合，可以使用户能够将一张全息图放在应用中。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 提供注视、 手势、 运动控制器、 directx、 输入、 全息
ms.openlocfilehash: 7cee3d3d7fbcd903eae0376e205034b9cc4ead3b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593066"
---
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a><span data-ttu-id="d8ea2-104">提供注视、 手势和 DirectX 中的动作控制器</span><span class="sxs-lookup"><span data-stu-id="d8ea2-104">Gaze, gestures, and motion controllers in DirectX</span></span>

<span data-ttu-id="d8ea2-105">如果您打算在平台上直接生成，您将需要处理输入的来自用户-例如，用户正在通过[头注视](gaze.md)，且用户已选择与[手势](gestures.md)或[动作控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-105">If you're going to build directly on top of the platform, you will have to handle input coming from the user - such as where the user is looking via [head gaze](gaze.md) and what the user has selected with [gestures](gestures.md) or [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="d8ea2-106">将这些形式的输入相结合，可以使用户能够将放[全息图](hologram.md)应用程序中。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-106">Combining these forms of input, you can enable a user to place a [hologram](hologram.md) in your app.</span></span> <span data-ttu-id="d8ea2-107">[全息版的应用程序模板](creating-a-holographic-directx-project.md)有一个易于使用的示例。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-107">The [holographic app template](creating-a-holographic-directx-project.md) has an easy to use example.</span></span>

>[!NOTE]
><span data-ttu-id="d8ea2-108">这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="d8ea2-109">这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="gaze-input"></a><span data-ttu-id="d8ea2-110">凝视输入</span><span class="sxs-lookup"><span data-stu-id="d8ea2-110">Gaze input</span></span>

<span data-ttu-id="d8ea2-111">若要访问用户的[头注视](gaze.md)，则使用[SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx)类型。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-111">To access the user's [head gaze](gaze.md), you use the [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) type.</span></span> <span data-ttu-id="d8ea2-112">全息版的应用程序模板包括了解的视线移动的基本代码。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-112">The holographic app template includes basic code for understanding gaze.</span></span> <span data-ttu-id="d8ea2-113">此代码提供了一个向量，介于 （考虑到设备的位置和方向中的用户的眼睛） 转发指向给定[坐标系](coordinate-systems-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-113">This code provides a vector pointing forward from between the user's eyes, taking into account the device's position and orientation in a given [coordinate system](coordinate-systems-in-directx.md).</span></span>




```cpp
void SpinningCubeRenderer::PositionHologram(SpatialPointerPose^ pointerPose)
{
    if (pointerPose != nullptr)
    {
        // Get the gaze direction relative to the given coordinate system.
        const float3 headPosition    = pointerPose->Head->Position;
        const float3 headDirection   = pointerPose->Head->ForwardDirection;
    
        // The hologram is positioned two meters along the user's gaze direction.
        static const float distanceFromUser = 2.0f; // meters
        const float3 gazeAtTwoMeters        = headPosition + (distanceFromUser * headDirection);
    
        // This will be used as the translation component of the hologram's
        // model transform.
        SetPosition(gazeAtTwoMeters);
    }
}
```

<span data-ttu-id="d8ea2-114">你可能有类似："但坐标系统来自何处？"</span><span class="sxs-lookup"><span data-stu-id="d8ea2-114">You may find yourself asking: "But where does the coordinate system come from?"</span></span>

<span data-ttu-id="d8ea2-115">让我们回答这个问题。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-115">Let's answer that question.</span></span> <span data-ttu-id="d8ea2-116">在我们 AppMain**更新**函数，我们通过它为我们 StationaryFrameOfReference 获取相对于坐标系统处理空间的输入的事件。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-116">In our AppMain's **Update** function, we processed a spatial input event by acquiring it relative to the coordinate system for our StationaryFrameOfReference.</span></span> <span data-ttu-id="d8ea2-117">回想一下，当我们建立时已创建 StationaryFrameOfReference [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)，和坐标系统已开始时获取[更新](rendering-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-117">Recall that the StationaryFrameOfReference was created when we set up the [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), and the coordinate system was acquired at the start of [Update](rendering-in-directx.md).</span></span>




```cpp
// Check for new input state since the last frame.
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
if (pointerState != nullptr)
{
    // When a Pressed gesture is detected, the sample hologram will be repositioned
    // two meters in front of the user.
    m_spinningCubeRenderer->PositionHologram(
        pointerState->TryGetPointerPose(currentCoordinateSystem)
        );
}
```

<span data-ttu-id="d8ea2-118">请注意，将数据绑定到某种类型的指针的状态。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-118">Note that the data is tied to a pointer state of some kind.</span></span> <span data-ttu-id="d8ea2-119">我们从空间的输入事件获取此信息。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-119">We get this from a spatial input event.</span></span> <span data-ttu-id="d8ea2-120">事件数据对象包括坐标系，以便则始终可以与任何所需的空间坐标系统相关事件的时间所在的视线移动的方向。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-120">The event data object includes a coordinate system, so that you can always relate the gaze direction at the time of the event to whatever spatial coordinate system you need.</span></span> <span data-ttu-id="d8ea2-121">事实上，您必须执行以获取指针姿势。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-121">In fact, you must do so in order to get the pointer pose.</span></span>

> [!NOTE]
> <span data-ttu-id="d8ea2-122">特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-122">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gesture-and-motion-controller-input"></a><span data-ttu-id="d8ea2-123">输入笔势和动作控制器</span><span class="sxs-lookup"><span data-stu-id="d8ea2-123">Gesture and motion controller input</span></span>

<span data-ttu-id="d8ea2-124">在 Windows 混合现实中，同时传递[手势](gestures.md)并[动作控制器](motion-controllers.md)中找到对同一空间输入 Api，通过处理[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)命名空间。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-124">In Windows Mixed Reality, both hand [gestures](gestures.md) and [motion controllers](motion-controllers.md) are handled through the same spatial input APIs, found in the [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span></span> <span data-ttu-id="d8ea2-125">这使你能够轻松处理常见操作，例如**选择**跨双手和动作控制器按相同的方式。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-125">This enables you to easily handle common actions like **Select** presses the same way across both hands and motion controllers.</span></span>

<span data-ttu-id="d8ea2-126">有两个级别的 API 可以处理手势或运动控制器混合现实中时为目标：</span><span class="sxs-lookup"><span data-stu-id="d8ea2-126">There are two levels of API you can target when handling gestures or motion controllers in mixed reality:</span></span>
* <span data-ttu-id="d8ea2-127">[交互](gestures.md#the-two-core-gestures-of-hololens)([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx)， [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx)并[SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx))，可使用[SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span><span class="sxs-lookup"><span data-stu-id="d8ea2-127">[Interactions](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) and [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), accessed using a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span></span>
* <span data-ttu-id="d8ea2-128">[复合手势](gestures.md#composite-gestures)([点击](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx)，保存、 操作、 导航)，可使用[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span><span class="sxs-lookup"><span data-stu-id="d8ea2-128">[Composite gestures](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), Hold, Manipulation, Navigation), accessed using a [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span></span>

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a><span data-ttu-id="d8ea2-129">选择/菜单/掌握/触摸板/摇杆交互：SpatialInteractionManager</span><span class="sxs-lookup"><span data-stu-id="d8ea2-129">Select/Menu/Grasp/Touchpad/Thumbstick interactions: SpatialInteractionManager</span></span>

<span data-ttu-id="d8ea2-130">若要跨双手和输入的设备在 Windows Mixed Reality 检测低级别，按下按钮、 版本和更新，则启动从[SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-130">To detect low-level presses, releases and updates across hands and input devices in Windows Mixed Reality, you start from a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span></span> <span data-ttu-id="d8ea2-131">SpatialInteractionManager 有一个事件，以通知应用程序时手的形状或运动控制器已检测到输入。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-131">The SpatialInteractionManager has an event that informs the app when a hand or motion controller has detected input.</span></span>

<span data-ttu-id="d8ea2-132">有三种密钥类型的 SpatialInteractionSource，每个由不同的 SpatialInteractionSourceKind 值：</span><span class="sxs-lookup"><span data-stu-id="d8ea2-132">There are three key kinds of SpatialInteractionSource, each represented by a different SpatialInteractionSourceKind value:</span></span>
* <span data-ttu-id="d8ea2-133">**手**表示检测到的用户的手。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-133">**Hand** represents a user's detected hand.</span></span> <span data-ttu-id="d8ea2-134">手源是仅在 HoloLens 上可用。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-134">Hand sources are available only on HoloLens.</span></span>
* <span data-ttu-id="d8ea2-135">**控制器**表示配对的运动控制器。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-135">**Controller** represents a paired motion controller.</span></span> <span data-ttu-id="d8ea2-136">运动控制器可以提供的各种功能，例如：选择触发器、 菜单按钮、 掌握按钮、 触摸板和 thumbsticks。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-136">Motion controllers can offer a variety of capabilities, for example: Select triggers, Menu buttons, Grasp buttons, touchpads and thumbsticks.</span></span>
* <span data-ttu-id="d8ea2-137">**语音**表示谈到系统检测到关键字的用户的声音。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-137">**Voice** represents the user's voice speaking system-detected keywords.</span></span> <span data-ttu-id="d8ea2-138">这将注入选择按下并释放时用户所讲的"选择"。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-138">This will inject a Select press and release whenever the user says "Select".</span></span>

<span data-ttu-id="d8ea2-139">若要检测可跨任何这些交互源，按下按钮，可以处理在 SpatialInputHandler.cpp SpatialInteractionManager SourcePressed 事件：</span><span class="sxs-lookup"><span data-stu-id="d8ea2-139">To detect presses across any of these interaction sources, you can handle the SourcePressed event on SpatialInteractionManager in SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

<span data-ttu-id="d8ea2-140">此按下的事件以异步方式发送到您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-140">This pressed event is sent to your app asynchronously.</span></span> <span data-ttu-id="d8ea2-141">你的应用或游戏引擎可能需要执行一些处理立即或你可能想要在输入处理例程中的事件数据进行排队。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-141">Your app or game engine may want to perform some processing right away or you may want to queue up the event data in your input processing routine.</span></span>

<span data-ttu-id="d8ea2-142">该模板包含帮助您入门的帮助器类。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-142">The template includes a helper class to get you started.</span></span> <span data-ttu-id="d8ea2-143">此模板 forgoes 设计的简单性任何处理。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-143">This template forgoes any processing for simplicity of design.</span></span> <span data-ttu-id="d8ea2-144">帮助器类跟踪的一个或多个**Pressed**自上次以来发生的事件**更新**调用。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-144">The helper class keeps track of whether one or more **Pressed** events occurred since the last **Update** call.</span></span> <span data-ttu-id="d8ea2-145">从 SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="d8ea2-145">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourcePressed(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    m_sourceState = args->State;
    
    //
    // TODO: In your app or game engine, rewrite this method to queue
    //       input events in your input class or event handler.
    //
}
```

<span data-ttu-id="d8ea2-146">如果有，则返回[SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)的下一次更新期间的最新输入事件。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-146">If so, it returns the [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) for the most recent input event during the next Update.</span></span> <span data-ttu-id="d8ea2-147">从 SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="d8ea2-147">From SpatialInputHandler.cpp:</span></span>




```cpp
// Checks if the user performed an input gesture since the last call to this method.
// Allows the main update loop to check for asynchronous changes to the user
// input state.
SpatialInteractionSourceState^ SpatialInputHandler::CheckForInput()
{
    SpatialInteractionSourceState^ sourceState = m_sourceState;
    m_sourceState = nullptr;
    return sourceState;
}
```

<span data-ttu-id="d8ea2-148">请注意上面的代码会将所有按相同的方式，无论用户正在执行主**选择**按也非辅助**菜单**或**掌握**按。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-148">Note that the code above will treat all presses the same way, whether the user is performing a primary **Select** press or a secondary **Menu** or **Grasp** press.</span></span> <span data-ttu-id="d8ea2-149">**选择**按是交互都支持的手、 运动控制器和语音，触发通过手动执行以无线方式点击，按下时使用其主触发器/按钮的运动控制器或用户的主窗体语音说"Select"。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-149">The **Select** press is a primary form of interaction supported across hands, motion controllers and voice, triggered either by a hand performing an air-tap, a motion controller with its primary trigger/button pressed, or the user's voice saying "Select".</span></span> <span data-ttu-id="d8ea2-150">选择按下按钮可以表示用户的意图激活它们面向的全息图。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-150">Select presses represent the user's intention to activate the hologram they are targeting.</span></span>

<span data-ttu-id="d8ea2-151">若要按哪种类型推断发生，我们将修改 SpatialInteractionManager::SourceUpdated 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-151">To reason about which kind of press is occurring, we will modify the SpatialInteractionManager::SourceUpdated event handler.</span></span> <span data-ttu-id="d8ea2-152">我们的代码将检测掌握，按下 （如果可用），并使用它们来重新定位该多维数据集。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-152">Our code will detect Grasp presses (where available) and use them to reposition the cube.</span></span> <span data-ttu-id="d8ea2-153">如果掌握不可用，我们将使用选择按。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-153">If Grasp is not available, we will use Select presses instead.</span></span>

<span data-ttu-id="d8ea2-154">将以下私有成员声明添加到 SpatialInputHandler.h:</span><span class="sxs-lookup"><span data-stu-id="d8ea2-154">Add the following private member declarations to SpatialInputHandler.h:</span></span> 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

<span data-ttu-id="d8ea2-155">Open SpatialInputHandler.cpp.</span><span class="sxs-lookup"><span data-stu-id="d8ea2-155">Open SpatialInputHandler.cpp.</span></span> <span data-ttu-id="d8ea2-156">将以下事件注册添加到构造函数：</span><span class="sxs-lookup"><span data-stu-id="d8ea2-156">Add the following event registration to the constructor:</span></span> 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

<span data-ttu-id="d8ea2-157">这是事件处理程序代码。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-157">This is the event handler code.</span></span> <span data-ttu-id="d8ea2-158">如果输入的源遇到掌握，指针姿势将存储为下一个更新循环中。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-158">If the input source is experiencing a Grasp, the pointer pose will be stored for the next update loop.</span></span> <span data-ttu-id="d8ea2-159">否则，它将检查选择按相反。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-159">Otherwise, it will check for a Select press instead.</span></span> <span data-ttu-id="d8ea2-160">从 SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="d8ea2-160">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourceUpdated(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    if (args->State->Source->IsGraspSupported)
    {
        if (args->State->IsGrasped)
        {
            m_sourceState = args->State;
        }
    }
    else
    {
        if (args->State->IsSelectPressed)
        {
            m_sourceState = args->State;
        }
    }
}
```

<span data-ttu-id="d8ea2-161">请确保要注销的析构函数中的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-161">Make sure to unregister the event handler in the destructor.</span></span> <span data-ttu-id="d8ea2-162">从 SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="d8ea2-162">From SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

<span data-ttu-id="d8ea2-163">重新编译，并重新部署。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-163">Recompile, and then redeploy.</span></span> <span data-ttu-id="d8ea2-164">你的模板项目现在应能够识别掌握交互来重新定位旋转多维数据集。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-164">Your template project should now be able to recognize Grasp interactions to reposition the spinning cube.</span></span>

<span data-ttu-id="d8ea2-165">SpatialInteractionSource API 支持各种功能的域控制器。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-165">The SpatialInteractionSource API supports controllers with a wide range of capabilities.</span></span> <span data-ttu-id="d8ea2-166">在上面所示示例中，我们检查掌握尝试使用它之前是否受支持。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-166">In the example shown above, we check to see if Grasp is supported before trying to use it.</span></span> <span data-ttu-id="d8ea2-167">SpatialInteractionSource 支持通用超出以下可选功能**选择**按：</span><span class="sxs-lookup"><span data-stu-id="d8ea2-167">The SpatialInteractionSource supports the following optional features beyond the common **Select** press:</span></span>
* <span data-ttu-id="d8ea2-168">**菜单按钮：** 通过检查 IsMenuSupported 属性检查的支持。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-168">**Menu button:** Check support by inspecting the IsMenuSupported property.</span></span> <span data-ttu-id="d8ea2-169">支持时，检查[SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)属性要找出菜单按钮被按下。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-169">When supported, check the [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if the menu button is pressed.</span></span>
* <span data-ttu-id="d8ea2-170">**掌握按钮：** 通过检查 IsGraspSupported 属性检查的支持。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-170">**Grasp button:** Check support by inspecting the IsGraspSupported property.</span></span> <span data-ttu-id="d8ea2-171">支持时，检查[SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)要查找已激活了掌握现有属性。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-171">When supported, check the [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if grasp is activated.</span></span>

<span data-ttu-id="d8ea2-172">对于控制器，SpatialInteractionSource 具有通过附加功能的控制器属性。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-172">For controllers, the SpatialInteractionSource has a Controller property with additional capabilities.</span></span>
* <span data-ttu-id="d8ea2-173">**HasThumbstick:** 如果为 true，则控制器有摇杆。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-173">**HasThumbstick:** If true, the controller has a thumbstick.</span></span> <span data-ttu-id="d8ea2-174">检查[ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) SpatialInteractionSourceState 获取摇杆属性 x 和 y 值 （ThumbstickX 和 ThumbstickY），以及其按下的状态 (IsThumbstickPressed)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-174">Inspect the [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) property of the SpatialInteractionSourceState to acquire the thumbstick x and y values (ThumbstickX and ThumbstickY), as well as its pressed state (IsThumbstickPressed).</span></span>
* <span data-ttu-id="d8ea2-175">**HasTouchpad:** 如果为 true，则控制器具有触摸板。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-175">**HasTouchpad:** If true, the controller has a touchpad.</span></span> <span data-ttu-id="d8ea2-176">检查 SpatialInteractionSourceState 获取触摸板的 ControllerProperties 属性 x 和 y 值 （TouchpadX 和 TouchpadY），并了解如果用户触摸板 (IsTouchpadTouched)，并且它们按下 （触摸板IsTouchpadPressed)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-176">Inspect the ControllerProperties property of the SpatialInteractionSourceState to acquire the touchpad x and y values (TouchpadX and TouchpadY), and to know if the user is touching the pad (IsTouchpadTouched) and if they are pressing the touchpad down (IsTouchpadPressed).</span></span>
* <span data-ttu-id="d8ea2-177">**SimpleHapticsController:** 在控制器 SimpleHapticsController API 允许你检查控制器的 haptics 功能并允许您控制 haptic 反馈。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-177">**SimpleHapticsController:** The SimpleHapticsController API for the controller allows you to inspect the haptics capabilities of the controller, and it also allows you to control haptic feedback.</span></span>

<span data-ttu-id="d8ea2-178">请注意，触摸板和摇杆从-1 到 1 表示两个轴 （从底部到顶部，和从左到右） 的范围。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-178">Note that the range for touchpad and thumbstick from -1 to 1 for both axes (from bottom to top, and from left to right).</span></span> <span data-ttu-id="d8ea2-179">对于模拟的触发器，请访问使用 SpatialInteractionSourceState::SelectPressedValue 属性，该范围提供一系列的 0 到 1。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-179">The range for the analog trigger, which is accessed using the SpatialInteractionSourceState::SelectPressedValue property, has a range of 0 to 1.</span></span> <span data-ttu-id="d8ea2-180">值为 1 的关联与 IsSelectPressed 等于 true;任何其他值将等于 false 的 IsSelectPressed 与相关联。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-180">A value of 1 correlates with IsSelectPressed being equal to true; any other value correlates with IsSelectPressed being equal to false.</span></span>

<span data-ttu-id="d8ea2-181">请注意，对于手的形状和一个控制器，使用 SpatialInteractionSourceState::Properties::TryGetLocation 将提供用户的手位置-这是与表示控制器的指针 ray 指针姿势不同的名称。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-181">Note that for both a hand and a controller, using SpatialInteractionSourceState::Properties::TryGetLocation will provide the user's hand position - this is distinct from the pointer pose representing the controller's pointing ray.</span></span> <span data-ttu-id="d8ea2-182">如果你想要在现有位置绘制一些内容，使用 TryGetLocation。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-182">If you want to draw something at the hand location, use TryGetLocation.</span></span> <span data-ttu-id="d8ea2-183">如果您希望 raycast 从控制器的提示，请从 TryGetInteractionSourcePose SpatialPointerPose 上获取指针 ray。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-183">If you want to raycast from the tip of the controller, get the pointing ray from TryGetInteractionSourcePose on the SpatialPointerPose.</span></span>

<span data-ttu-id="d8ea2-184">此外可以使用上 SpatialInteractionManager，如 SourceDetected 和 SourceLost，其他事件做出反应时手进入或离开设备的视图，或当它们将移入或移出准备就绪的位置 （索引手指与转发 palm 引发），或当动作打开/关闭控制器或配对/不成对。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-184">You can also use the other events on SpatialInteractionManager, such as SourceDetected and SourceLost, to react when hands enter or leave the device's view or when they move in or out of the ready position (index finger raised with palm forward), or when motion controllers are turned on/off or are paired/unpaired.</span></span>

### <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="d8ea2-185">与指针姿势手柄姿势</span><span class="sxs-lookup"><span data-stu-id="d8ea2-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="d8ea2-186">Windows Mixed Reality 支持不同的外形规格运动控制器，使用每个控制器设计各不相同，"转发"方向该应用的自然用户的手位置之间的关系应为使用指向呈现时控制器。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="d8ea2-187">若要更好地表示这些控制器，有两种类型的可以为每个交互源调查的带来：</span><span class="sxs-lookup"><span data-stu-id="d8ea2-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>
* <span data-ttu-id="d8ea2-188">**手柄姿势**，表示检测到的 HoloLens 手的形状的手掌或手掌持有运动控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-188">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="d8ea2-189">在沉浸式耳机，此姿势最适合用于呈现**用户的手**或**对象保存在用户的手中**，例如双刃剑或手段。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-189">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="d8ea2-190">**抓住位置**:Palm 质心时保存在控制器正常情况下，调整左侧或右侧居中手柄内的位置。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-190">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="d8ea2-191">**抓住方向的右轴**:完全打开您的手以形成平面 5 手指姿势，ray 的时您的手掌接触到正常 （从左 palm，向右 palm 从后向前）</span><span class="sxs-lookup"><span data-stu-id="d8ea2-191">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="d8ea2-192">**抓住正轴方向的**:当您关闭您的手部分 （就像按控制器），"forward"通过管通过非 thumb 手指点与射线。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-192">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="d8ea2-193">**抓住方向沿轴向上**:权限隐含的权限和转发定义最多轴。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-193">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="d8ea2-194">您可以访问通过手柄姿势[SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span><span class="sxs-lookup"><span data-stu-id="d8ea2-194">You can access the grip pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span></span>
* <span data-ttu-id="d8ea2-195">**指针姿势**，表示指向转发的控制器的提示。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-195">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="d8ea2-196">此姿势最习惯 raycast 时**指向 UI**时呈现控制器模型本身。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-196">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="d8ea2-197">您可以访问通过指针姿势[SpatialInteractionSourceState.Properties.TryGetLocation(...)。SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或[SpatialInteractionSourceState.TryGetPointerPose(...)。TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-197">You can access the pointer pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...).SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) or [SpatialInteractionSourceState.TryGetPointerPose(...).TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span></span>

### <a name="composite-gestures-spatialgesturerecognizer"></a><span data-ttu-id="d8ea2-198">复合手势：SpatialGestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="d8ea2-198">Composite gestures: SpatialGestureRecognizer</span></span>

<span data-ttu-id="d8ea2-199">一个[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)解释使用其头的视线移动的用户目标的图面上的空间手势事件，从手、 运动控制器和"选择"语音命令的用户交互。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interprets user interactions from hands, motion controllers, and the "Select" voice command to surface spatial gesture events, which users target using their head gaze.</span></span>

<span data-ttu-id="d8ea2-200">空间手势是输入的一种关键 Windows Mixed Reality 应用。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-200">Spatial gestures are a key form of input for Windows Mixed Reality apps.</span></span> <span data-ttu-id="d8ea2-201">通过从 SpatialInteractionManager 到一张全息图 SpatialGestureRecognizer 路由交互，应用可以检测到点击、 按住、 操作和导航事件统一跨手、 语音和空间的输入的设备，而无需处理，按下按钮并手动释放。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-201">By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.</span></span>

<span data-ttu-id="d8ea2-202">SpatialGestureRecognizer 执行仅之间的一套手势你请求的最小消除歧义。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-202">SpatialGestureRecognizer performs only the minimal disambiguation between the set of gestures that you request.</span></span> <span data-ttu-id="d8ea2-203">例如，如果请求只需点击，用户可能会按他们的手指下，只要他们喜欢和点击仍会发生。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-203">For example, if you request just Tap, the user may hold their finger down as long as they like and a Tap will still occur.</span></span> <span data-ttu-id="d8ea2-204">如果请求同时点击并按住后约一秒钟的按下他们的手指，手势将升级到某个保留，都不会出现一个分流点。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-204">If you request both Tap and Hold, after about a second of holding down their finger, the gesture will promote to a Hold and a Tap will no longer occur.</span></span>

<span data-ttu-id="d8ea2-205">若要使用 SpatialGestureRecognizer，处理 SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)事件和随取即行 SpatialPointerPose 那里公开。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-205">To use SpatialGestureRecognizer, handle the SpatialInteractionManager's [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) event and grab the SpatialPointerPose exposed there.</span></span> <span data-ttu-id="d8ea2-206">使用此姿势从用户的头的视线移动 ray 与全息相交并在用户的环境中网格以确定用户打算与之交互的图面。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-206">Use the user's head gaze ray from this pose to intersect with the holograms and surface meshes in the user's surroundings, in order to determine what the user is intending to interact with.</span></span> <span data-ttu-id="d8ea2-207">然后，将 SpatialInteraction 路由到目标 hologram SpatialGestureRecognizer 事件参数中使用其[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)方法。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-207">Then, route the SpatialInteraction in the event arguments to the target hologram's SpatialGestureRecognizer, using its [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) method.</span></span> <span data-ttu-id="d8ea2-208">这将启动解释根据该交互[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings)上的识别器设置，可以在创建时的或通过[TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-208">This starts interpreting that interaction according to the [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) set on that recognizer at creation time - or by [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span></span>

<span data-ttu-id="d8ea2-209">上 HoloLens，交互和手势应通常派生其目标从用户的头的视线移动，而不是非试着来呈现或直接在现有的位置进行交互。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-209">On HoloLens, interactions and gestures should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="d8ea2-210">一旦启动交互，相对动作的手可能用于控制手势，如同操作或导航笔势。</span><span class="sxs-lookup"><span data-stu-id="d8ea2-210">Once an interaction has started, relative motions of the hand may be used to control the gesture, as with the Manipulation or Navigation gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8ea2-211">请参阅</span><span class="sxs-lookup"><span data-stu-id="d8ea2-211">See also</span></span>
* [<span data-ttu-id="d8ea2-212">Gaze</span><span class="sxs-lookup"><span data-stu-id="d8ea2-212">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="d8ea2-213">手势</span><span class="sxs-lookup"><span data-stu-id="d8ea2-213">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="d8ea2-214">运动控制器</span><span class="sxs-lookup"><span data-stu-id="d8ea2-214">Motion controllers</span></span>](motion-controllers.md)
