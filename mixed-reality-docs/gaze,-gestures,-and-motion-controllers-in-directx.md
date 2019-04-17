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
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a>提供注视、 手势和 DirectX 中的动作控制器

如果您打算在平台上直接生成，您将需要处理输入的来自用户-例如，用户正在通过[头注视](gaze.md)，且用户已选择与[手势](gestures.md)或[动作控制器](motion-controllers.md)。 将这些形式的输入相结合，可以使用户能够将放[全息图](hologram.md)应用程序中。 [全息版的应用程序模板](creating-a-holographic-directx-project.md)有一个易于使用的示例。

>[!NOTE]
>这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。  这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。

## <a name="gaze-input"></a>凝视输入

若要访问用户的[头注视](gaze.md)，则使用[SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx)类型。 全息版的应用程序模板包括了解的视线移动的基本代码。 此代码提供了一个向量，介于 （考虑到设备的位置和方向中的用户的眼睛） 转发指向给定[坐标系](coordinate-systems-in-directx.md)。




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

你可能有类似："但坐标系统来自何处？"

让我们回答这个问题。 在我们 AppMain**更新**函数，我们通过它为我们 StationaryFrameOfReference 获取相对于坐标系统处理空间的输入的事件。 回想一下，当我们建立时已创建 StationaryFrameOfReference [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)，和坐标系统已开始时获取[更新](rendering-in-directx.md)。




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

请注意，将数据绑定到某种类型的指针的状态。 我们从空间的输入事件获取此信息。 事件数据对象包括坐标系，以便则始终可以与任何所需的空间坐标系统相关事件的时间所在的视线移动的方向。 事实上，您必须执行以获取指针姿势。

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。

## <a name="gesture-and-motion-controller-input"></a>输入笔势和动作控制器

在 Windows 混合现实中，同时传递[手势](gestures.md)并[动作控制器](motion-controllers.md)中找到对同一空间输入 Api，通过处理[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)命名空间。 这使你能够轻松处理常见操作，例如**选择**跨双手和动作控制器按相同的方式。

有两个级别的 API 可以处理手势或运动控制器混合现实中时为目标：
* [交互](gestures.md#the-two-core-gestures-of-hololens)([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx)， [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx)并[SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx))，可使用[SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)
* [复合手势](gestures.md#composite-gestures)([点击](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx)，保存、 操作、 导航)，可使用[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a>选择/菜单/掌握/触摸板/摇杆交互：SpatialInteractionManager

若要跨双手和输入的设备在 Windows Mixed Reality 检测低级别，按下按钮、 版本和更新，则启动从[SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)。 SpatialInteractionManager 有一个事件，以通知应用程序时手的形状或运动控制器已检测到输入。

有三种密钥类型的 SpatialInteractionSource，每个由不同的 SpatialInteractionSourceKind 值：
* **手**表示检测到的用户的手。 手源是仅在 HoloLens 上可用。
* **控制器**表示配对的运动控制器。 运动控制器可以提供的各种功能，例如：选择触发器、 菜单按钮、 掌握按钮、 触摸板和 thumbsticks。
* **语音**表示谈到系统检测到关键字的用户的声音。 这将注入选择按下并释放时用户所讲的"选择"。

若要检测可跨任何这些交互源，按下按钮，可以处理在 SpatialInputHandler.cpp SpatialInteractionManager SourcePressed 事件：


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

此按下的事件以异步方式发送到您的应用程序。 你的应用或游戏引擎可能需要执行一些处理立即或你可能想要在输入处理例程中的事件数据进行排队。

该模板包含帮助您入门的帮助器类。 此模板 forgoes 设计的简单性任何处理。 帮助器类跟踪的一个或多个**Pressed**自上次以来发生的事件**更新**调用。 从 SpatialInputHandler.cpp:




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

如果有，则返回[SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)的下一次更新期间的最新输入事件。 从 SpatialInputHandler.cpp:




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

请注意上面的代码会将所有按相同的方式，无论用户正在执行主**选择**按也非辅助**菜单**或**掌握**按。 **选择**按是交互都支持的手、 运动控制器和语音，触发通过手动执行以无线方式点击，按下时使用其主触发器/按钮的运动控制器或用户的主窗体语音说"Select"。 选择按下按钮可以表示用户的意图激活它们面向的全息图。

若要按哪种类型推断发生，我们将修改 SpatialInteractionManager::SourceUpdated 事件处理程序。 我们的代码将检测掌握，按下 （如果可用），并使用它们来重新定位该多维数据集。 如果掌握不可用，我们将使用选择按。

将以下私有成员声明添加到 SpatialInputHandler.h: 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

Open SpatialInputHandler.cpp. 将以下事件注册添加到构造函数： 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

这是事件处理程序代码。 如果输入的源遇到掌握，指针姿势将存储为下一个更新循环中。 否则，它将检查选择按相反。 从 SpatialInputHandler.cpp:




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

请确保要注销的析构函数中的事件处理程序。 从 SpatialInputHandler.cpp:


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

重新编译，并重新部署。 你的模板项目现在应能够识别掌握交互来重新定位旋转多维数据集。

SpatialInteractionSource API 支持各种功能的域控制器。 在上面所示示例中，我们检查掌握尝试使用它之前是否受支持。 SpatialInteractionSource 支持通用超出以下可选功能**选择**按：
* **菜单按钮：** 通过检查 IsMenuSupported 属性检查的支持。 支持时，检查[SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)属性要找出菜单按钮被按下。
* **掌握按钮：** 通过检查 IsGraspSupported 属性检查的支持。 支持时，检查[SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx)要查找已激活了掌握现有属性。

对于控制器，SpatialInteractionSource 具有通过附加功能的控制器属性。
* **HasThumbstick:** 如果为 true，则控制器有摇杆。 检查[ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) SpatialInteractionSourceState 获取摇杆属性 x 和 y 值 （ThumbstickX 和 ThumbstickY），以及其按下的状态 (IsThumbstickPressed)。
* **HasTouchpad:** 如果为 true，则控制器具有触摸板。 检查 SpatialInteractionSourceState 获取触摸板的 ControllerProperties 属性 x 和 y 值 （TouchpadX 和 TouchpadY），并了解如果用户触摸板 (IsTouchpadTouched)，并且它们按下 （触摸板IsTouchpadPressed)。
* **SimpleHapticsController:** 在控制器 SimpleHapticsController API 允许你检查控制器的 haptics 功能并允许您控制 haptic 反馈。

请注意，触摸板和摇杆从-1 到 1 表示两个轴 （从底部到顶部，和从左到右） 的范围。 对于模拟的触发器，请访问使用 SpatialInteractionSourceState::SelectPressedValue 属性，该范围提供一系列的 0 到 1。 值为 1 的关联与 IsSelectPressed 等于 true;任何其他值将等于 false 的 IsSelectPressed 与相关联。

请注意，对于手的形状和一个控制器，使用 SpatialInteractionSourceState::Properties::TryGetLocation 将提供用户的手位置-这是与表示控制器的指针 ray 指针姿势不同的名称。 如果你想要在现有位置绘制一些内容，使用 TryGetLocation。 如果您希望 raycast 从控制器的提示，请从 TryGetInteractionSourcePose SpatialPointerPose 上获取指针 ray。

此外可以使用上 SpatialInteractionManager，如 SourceDetected 和 SourceLost，其他事件做出反应时手进入或离开设备的视图，或当它们将移入或移出准备就绪的位置 （索引手指与转发 palm 引发），或当动作打开/关闭控制器或配对/不成对。

### <a name="grip-pose-vs-pointing-pose"></a>与指针姿势手柄姿势

Windows Mixed Reality 支持不同的外形规格运动控制器，使用每个控制器设计各不相同，"转发"方向该应用的自然用户的手位置之间的关系应为使用指向呈现时控制器。

若要更好地表示这些控制器，有两种类型的可以为每个交互源调查的带来：
* **手柄姿势**，表示检测到的 HoloLens 手的形状的手掌或手掌持有运动控制器的位置。
    * 在沉浸式耳机，此姿势最适合用于呈现**用户的手**或**对象保存在用户的手中**，例如双刃剑或手段。
    * **抓住位置**:Palm 质心时保存在控制器正常情况下，调整左侧或右侧居中手柄内的位置。
    * **抓住方向的右轴**:完全打开您的手以形成平面 5 手指姿势，ray 的时您的手掌接触到正常 （从左 palm，向右 palm 从后向前）
    * **抓住正轴方向的**:当您关闭您的手部分 （就像按控制器），"forward"通过管通过非 thumb 手指点与射线。
    * **抓住方向沿轴向上**:权限隐含的权限和转发定义最多轴。
    * 您可以访问通过手柄姿势[SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).
* **指针姿势**，表示指向转发的控制器的提示。
    * 此姿势最习惯 raycast 时**指向 UI**时呈现控制器模型本身。
    * 您可以访问通过指针姿势[SpatialInteractionSourceState.Properties.TryGetLocation(...)。SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或[SpatialInteractionSourceState.TryGetPointerPose(...)。TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)。

### <a name="composite-gestures-spatialgesturerecognizer"></a>复合手势：SpatialGestureRecognizer

一个[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)解释使用其头的视线移动的用户目标的图面上的空间手势事件，从手、 运动控制器和"选择"语音命令的用户交互。

空间手势是输入的一种关键 Windows Mixed Reality 应用。 通过从 SpatialInteractionManager 到一张全息图 SpatialGestureRecognizer 路由交互，应用可以检测到点击、 按住、 操作和导航事件统一跨手、 语音和空间的输入的设备，而无需处理，按下按钮并手动释放。

SpatialGestureRecognizer 执行仅之间的一套手势你请求的最小消除歧义。 例如，如果请求只需点击，用户可能会按他们的手指下，只要他们喜欢和点击仍会发生。 如果请求同时点击并按住后约一秒钟的按下他们的手指，手势将升级到某个保留，都不会出现一个分流点。

若要使用 SpatialGestureRecognizer，处理 SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)事件和随取即行 SpatialPointerPose 那里公开。 使用此姿势从用户的头的视线移动 ray 与全息相交并在用户的环境中网格以确定用户打算与之交互的图面。 然后，将 SpatialInteraction 路由到目标 hologram SpatialGestureRecognizer 事件参数中使用其[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)方法。 这将启动解释根据该交互[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings)上的识别器设置，可以在创建时的或通过[TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)。

上 HoloLens，交互和手势应通常派生其目标从用户的头的视线移动，而不是非试着来呈现或直接在现有的位置进行交互。 一旦启动交互，相对动作的手可能用于控制手势，如同操作或导航笔势。

## <a name="see-also"></a>请参阅
* [Gaze](gaze.md)
* [手势](gestures.md)
* [运动控制器](motion-controllers.md)
