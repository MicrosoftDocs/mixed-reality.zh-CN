---
title: DirectX 中的键盘、鼠标和控制器输入
description: 说明如何创建使用键盘、鼠标和游戏控制器的 Windows Mixed Reality 应用。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，键盘，鼠标，游戏控制器，xbox 控制器，HoloLens，桌面，演练，示例代码
ms.openlocfilehash: 27f1bf72435ce6889ba3f7b83664367a4440b162
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278085"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="f7d38-104">DirectX 中的键盘、鼠标和控制器输入</span><span class="sxs-lookup"><span data-stu-id="f7d38-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="f7d38-105">对于 Windows Mixed Reality 设备，键盘、鼠标和游戏控制器都可以提供非常有用的输入形式。</span><span class="sxs-lookup"><span data-stu-id="f7d38-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="f7d38-106">在 HoloLens 上支持蓝牙键盘和鼠标，用于调试你的应用程序或作为输入的备用形式。</span><span class="sxs-lookup"><span data-stu-id="f7d38-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="f7d38-107">Windows Mixed Reality 还支持附加到电脑的沉浸式耳机，其中鼠标、键盘和游戏控制器一直是标准的。</span><span class="sxs-lookup"><span data-stu-id="f7d38-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="f7d38-108">若要在 HoloLens 上使用键盘输入，请将蓝牙键盘与设备配对，或通过 Windows 设备门户使用虚拟输入。</span><span class="sxs-lookup"><span data-stu-id="f7d38-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="f7d38-109">若要在戴上 Windows Mixed Reality 沉浸式耳机时使用键盘输入，请将输入焦点置于设备上，或者使用 Windows 键 + Y 键盘组合将输入焦点分配给混合现实。</span><span class="sxs-lookup"><span data-stu-id="f7d38-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="f7d38-110">请记住，适用于 HoloLens 的应用必须提供未连接这些设备的功能。</span><span class="sxs-lookup"><span data-stu-id="f7d38-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="f7d38-111">本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT，这与全息项目模板中使用的不同。</span><span class="sxs-lookup"><span data-stu-id="f7d38-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="f7d38-112">概念对于C++/WinRT 项目是等效的，但你将需要转换代码。</span><span class="sxs-lookup"><span data-stu-id="f7d38-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="f7d38-113">订阅 CoreWindow 输入事件</span><span class="sxs-lookup"><span data-stu-id="f7d38-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="f7d38-114">键盘输入</span><span class="sxs-lookup"><span data-stu-id="f7d38-114">Keyboard input</span></span>

<span data-ttu-id="f7d38-115">在 Windows 全息应用程序模板中，为键盘输入添加了一个事件处理程序，就像其他任何 UWP 应用一样。</span><span class="sxs-lookup"><span data-stu-id="f7d38-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="f7d38-116">应用在 Windows Mixed Reality 中采用相同的方式使用键盘输入数据。</span><span class="sxs-lookup"><span data-stu-id="f7d38-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="f7d38-117">从 AppView：</span><span class="sxs-lookup"><span data-stu-id="f7d38-117">From AppView.cpp:</span></span>

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a><span data-ttu-id="f7d38-118">虚拟键盘输入</span><span class="sxs-lookup"><span data-stu-id="f7d38-118">Virtual keyboard input</span></span>
<span data-ttu-id="f7d38-119">对于沉浸式桌面耳机，还可以支持 Windows 通过沉浸式视图呈现的虚拟键盘。</span><span class="sxs-lookup"><span data-stu-id="f7d38-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="f7d38-120">为了支持这一点，你的应用程序可以实现**CoreTextEditContext**。</span><span class="sxs-lookup"><span data-stu-id="f7d38-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="f7d38-121">这样，Windows 便可以了解你自己的应用呈现的文本框的状态，因此虚拟键盘可以正确地参与到文本中。</span><span class="sxs-lookup"><span data-stu-id="f7d38-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="f7d38-122">有关实现 CoreTextEditContext 支持的详细信息，请参阅[CoreTextEditContext 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。</span><span class="sxs-lookup"><span data-stu-id="f7d38-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="f7d38-123">鼠标输入</span><span class="sxs-lookup"><span data-stu-id="f7d38-123">Mouse Input</span></span>

<span data-ttu-id="f7d38-124">还可以通过 UWP CoreWindow 输入事件处理程序再次使用鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="f7d38-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="f7d38-125">下面介绍了如何修改 Windows 全息应用程序模板，以支持通过与按下手势相同的方式进行鼠标单击。</span><span class="sxs-lookup"><span data-stu-id="f7d38-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="f7d38-126">进行此修改后，在戴上沉浸式耳机设备时，单击鼠标将重新定位该多维数据集。</span><span class="sxs-lookup"><span data-stu-id="f7d38-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="f7d38-127">请注意，UWP 应用还可以通过使用[MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API 获取鼠标的原始 XY 数据。</span><span class="sxs-lookup"><span data-stu-id="f7d38-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="f7d38-128">首先在 AppView 中声明新的 OnPointerPressed 处理程序：</span><span class="sxs-lookup"><span data-stu-id="f7d38-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="f7d38-129">在 AppView 中，将以下代码添加到 SetWindow：</span><span class="sxs-lookup"><span data-stu-id="f7d38-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="f7d38-130">然后将此定义 OnPointerPressed 到文件底部：</span><span class="sxs-lookup"><span data-stu-id="f7d38-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

<span data-ttu-id="f7d38-131">我们刚刚添加的事件处理程序是模板主类的传递。</span><span class="sxs-lookup"><span data-stu-id="f7d38-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="f7d38-132">让我们修改主类以支持此传递。</span><span class="sxs-lookup"><span data-stu-id="f7d38-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="f7d38-133">将此公共方法声明添加到头文件中：</span><span class="sxs-lookup"><span data-stu-id="f7d38-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="f7d38-134">还需要此私有成员变量：</span><span class="sxs-lookup"><span data-stu-id="f7d38-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="f7d38-135">最后，我们将用新逻辑更新主类，以支持鼠标单击。</span><span class="sxs-lookup"><span data-stu-id="f7d38-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="f7d38-136">首先添加此事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="f7d38-136">Start by adding this event handler.</span></span> <span data-ttu-id="f7d38-137">请确保更新类名称：</span><span class="sxs-lookup"><span data-stu-id="f7d38-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="f7d38-138">现在，在 Update 方法中，将现有逻辑替换为包含以下内容的指针：</span><span class="sxs-lookup"><span data-stu-id="f7d38-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="f7d38-139">重新编译和重新部署。</span><span class="sxs-lookup"><span data-stu-id="f7d38-139">Recompile and redeploy.</span></span> <span data-ttu-id="f7d38-140">你应注意到，鼠标单击现在会通过连接蓝牙鼠标在沉浸式耳机或 HoloLens 中重新定位该立方体。</span><span class="sxs-lookup"><span data-stu-id="f7d38-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="f7d38-141">游戏控制器支持</span><span class="sxs-lookup"><span data-stu-id="f7d38-141">Game controller support</span></span>

<span data-ttu-id="f7d38-142">游戏控制器是允许用户控制沉浸式 Windows Mixed Reality 体验的一种有趣且方便的方式。</span><span class="sxs-lookup"><span data-stu-id="f7d38-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="f7d38-143">向 Windows 全息应用程序模板添加游戏控制器支持的第一步是将以下私有成员声明添加到主文件的标头类中：</span><span class="sxs-lookup"><span data-stu-id="f7d38-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

<span data-ttu-id="f7d38-144">在主类的构造函数中初始化游戏板事件和当前附加的任何 gamepads：</span><span class="sxs-lookup"><span data-stu-id="f7d38-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

<span data-ttu-id="f7d38-145">将这些事件处理程序添加到您的主类。</span><span class="sxs-lookup"><span data-stu-id="f7d38-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="f7d38-146">请确保更新类名称：</span><span class="sxs-lookup"><span data-stu-id="f7d38-146">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

<span data-ttu-id="f7d38-147">最后，更新输入逻辑以识别控制器状态的更改。</span><span class="sxs-lookup"><span data-stu-id="f7d38-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="f7d38-148">此处，我们使用上述部分中讨论的同一个 m_pointerPressed 变量来添加鼠标事件。</span><span class="sxs-lookup"><span data-stu-id="f7d38-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="f7d38-149">将此添加到 Update 方法，就像它在何处检查 SpatialPointerPose：</span><span class="sxs-lookup"><span data-stu-id="f7d38-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

<span data-ttu-id="f7d38-150">清理主类时，请不要忘记取消注册事件：</span><span class="sxs-lookup"><span data-stu-id="f7d38-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

<span data-ttu-id="f7d38-151">重新编译和重新部署。</span><span class="sxs-lookup"><span data-stu-id="f7d38-151">Recompile, and redeploy.</span></span> <span data-ttu-id="f7d38-152">你现在可以附加或配对游戏控制器，并使用它来重新定位旋转立方体。</span><span class="sxs-lookup"><span data-stu-id="f7d38-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="f7d38-153">键盘和鼠标输入的重要指导原则</span><span class="sxs-lookup"><span data-stu-id="f7d38-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="f7d38-154">此代码在 Microsoft HoloLens 上的使用方式有一些重要差异–这是一个主要依赖于自然用户输入的设备，与支持 Windows Mixed Reality 的 PC 上提供的内容有关。</span><span class="sxs-lookup"><span data-stu-id="f7d38-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="f7d38-155">不能依靠键盘或鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="f7d38-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="f7d38-156">你的所有应用程序功能都必须使用注视、手势和语音输入。</span><span class="sxs-lookup"><span data-stu-id="f7d38-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="f7d38-157">连接蓝牙键盘时，为你的应用程序可能要求的任何文本启用键盘输入会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="f7d38-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="f7d38-158">例如，这可以是一个很好的听写补充。</span><span class="sxs-lookup"><span data-stu-id="f7d38-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="f7d38-159">设计应用程序时，不要依赖（例如）游戏的 WASD 和鼠标外观控件。</span><span class="sxs-lookup"><span data-stu-id="f7d38-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="f7d38-160">HoloLens 旨在使用户能够浏览聊天室。</span><span class="sxs-lookup"><span data-stu-id="f7d38-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="f7d38-161">在这种情况下，用户直接控制相机。</span><span class="sxs-lookup"><span data-stu-id="f7d38-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="f7d38-162">使用移动/外观控制来围绕房间来驱动照相机的接口不能提供相同的体验。</span><span class="sxs-lookup"><span data-stu-id="f7d38-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="f7d38-163">键盘输入可以很好地控制应用或游戏引擎的调试方面，尤其是因为用户不需要使用键盘。</span><span class="sxs-lookup"><span data-stu-id="f7d38-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="f7d38-164">将其与你一起使用，与 CoreWindow 事件 Api 相同。</span><span class="sxs-lookup"><span data-stu-id="f7d38-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="f7d38-165">在这种情况下，你可以选择实现一种方法，以将你的应用程序配置为在调试会话期间将键盘事件路由到 "仅调试输入" 模式。</span><span class="sxs-lookup"><span data-stu-id="f7d38-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="f7d38-166">蓝牙控制器也能正常工作。</span><span class="sxs-lookup"><span data-stu-id="f7d38-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7d38-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7d38-167">See also</span></span>
* [<span data-ttu-id="f7d38-168">硬件配件</span><span class="sxs-lookup"><span data-stu-id="f7d38-168">Hardware accessories</span></span>](hardware-accessories.md)
