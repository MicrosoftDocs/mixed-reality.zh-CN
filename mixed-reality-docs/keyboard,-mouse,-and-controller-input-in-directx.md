---
title: 键盘、 鼠标和 DirectX 中的控制器输入
description: 介绍如何创建适用于使用键盘、 鼠标和游戏控制器的 Windows Mixed Reality 应用。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 键盘、 鼠标、 游戏控制器、 xbox 控制器，HoloLens，台式计算机、 演练、 示例代码
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593065"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="25aeb-104">键盘、 鼠标和 DirectX 中的控制器输入</span><span class="sxs-lookup"><span data-stu-id="25aeb-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="25aeb-105">键盘、 鼠标和游戏控制器所有可以是输入的用于 Windows Mixed Reality 设备的有用窗体。</span><span class="sxs-lookup"><span data-stu-id="25aeb-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="25aeb-106">蓝牙键盘和鼠标是同时支持 HoloLens，使用具有调试您的应用程序或作为输入的替代形式。</span><span class="sxs-lookup"><span data-stu-id="25aeb-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="25aeb-107">Windows Mixed Reality 还支持附加至 Pc-其中鼠标、 键盘和游戏控制器就是长久以来一种规范的沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="25aeb-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="25aeb-108">若要针对 HoloLens，对向你的设备的蓝牙键盘使用键盘输入，或使用通过 Windows Device Portal 虚拟输入。</span><span class="sxs-lookup"><span data-stu-id="25aeb-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="25aeb-109">若要戴上的 Windows Mixed Reality 沉浸式头戴式耳机时使用键盘输入，请将其放在设备上或使用 Windows 键 + Y 的键盘组合分配混合现实输入的焦点。</span><span class="sxs-lookup"><span data-stu-id="25aeb-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="25aeb-110">请注意用于 HoloLens 的应用程序都必须提供功能，而无需连接这些设备。</span><span class="sxs-lookup"><span data-stu-id="25aeb-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="25aeb-111">这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="25aeb-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="25aeb-112">这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。</span><span class="sxs-lookup"><span data-stu-id="25aeb-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="25aeb-113">对于 CoreWindow 的输入事件订阅</span><span class="sxs-lookup"><span data-stu-id="25aeb-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="25aeb-114">键盘输入</span><span class="sxs-lookup"><span data-stu-id="25aeb-114">Keyboard input</span></span>

<span data-ttu-id="25aeb-115">在 Windows 全息版的应用程序模板中，我们包括键盘输入，就像任何其他 UWP 应用的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="25aeb-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="25aeb-116">您的应用程序使用键盘输入的数据 Windows Mixed Reality 同样的方式。</span><span class="sxs-lookup"><span data-stu-id="25aeb-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="25aeb-117">从 AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="25aeb-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="25aeb-118">虚拟键盘输入</span><span class="sxs-lookup"><span data-stu-id="25aeb-118">Virtual keyboard input</span></span>
<span data-ttu-id="25aeb-119">为沉浸式桌面耳机，还可以支持对沉浸式视图呈现的 Windows 的虚拟键盘。</span><span class="sxs-lookup"><span data-stu-id="25aeb-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="25aeb-120">若要支持此功能，您的应用程序可以实现**CoreTextEditContext**。</span><span class="sxs-lookup"><span data-stu-id="25aeb-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="25aeb-121">这允许 Windows 了解自己应用程序呈现的文本框的状态，因此虚拟键盘可以正确参与存在的文本。</span><span class="sxs-lookup"><span data-stu-id="25aeb-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="25aeb-122">有关实现 CoreTextEditContext 支持的详细信息，请参阅[CoreTextEditContext 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。</span><span class="sxs-lookup"><span data-stu-id="25aeb-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="25aeb-123">鼠标输入</span><span class="sxs-lookup"><span data-stu-id="25aeb-123">Mouse Input</span></span>

<span data-ttu-id="25aeb-124">此外可以使用鼠标输入，再次通过 UWP CoreWindow 输入的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="25aeb-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="25aeb-125">下面介绍了如何修改 Windows 全息版的应用程序模板，以在相同的方式按下手势支持鼠标单击。</span><span class="sxs-lookup"><span data-stu-id="25aeb-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="25aeb-126">后进行这种修改，戴上沉浸式头戴式耳机设备时单击鼠标将重新定位该多维数据集。</span><span class="sxs-lookup"><span data-stu-id="25aeb-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="25aeb-127">请注意，UWP 应用还可以通过使用获取原始 XY 数据鼠标[MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API。</span><span class="sxs-lookup"><span data-stu-id="25aeb-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="25aeb-128">首先声明 AppView.h 中的新 OnPointerPressed 处理程序：</span><span class="sxs-lookup"><span data-stu-id="25aeb-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="25aeb-129">在 AppView.cpp，到 SetWindow 中添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="25aeb-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="25aeb-130">然后将此定义，OnPointerPressed 放在该文件的底部：</span><span class="sxs-lookup"><span data-stu-id="25aeb-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="25aeb-131">我们刚添加的事件处理程序是传递到模板的主类。</span><span class="sxs-lookup"><span data-stu-id="25aeb-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="25aeb-132">让我们修改以支持此传递的主类。</span><span class="sxs-lookup"><span data-stu-id="25aeb-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="25aeb-133">将此公共方法声明添加到标头文件：</span><span class="sxs-lookup"><span data-stu-id="25aeb-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="25aeb-134">你将需要此私有成员变量，以及：</span><span class="sxs-lookup"><span data-stu-id="25aeb-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="25aeb-135">最后，我们将使用新的逻辑，以支持鼠标单击更新的主类。</span><span class="sxs-lookup"><span data-stu-id="25aeb-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="25aeb-136">首先，通过添加此事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="25aeb-136">Start by adding this event handler.</span></span> <span data-ttu-id="25aeb-137">请确保更新的类名：</span><span class="sxs-lookup"><span data-stu-id="25aeb-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="25aeb-138">现在，在更新方法中，将为用于获取与此指针姿势现有的逻辑：</span><span class="sxs-lookup"><span data-stu-id="25aeb-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="25aeb-139">重新编译和重新部署。</span><span class="sxs-lookup"><span data-stu-id="25aeb-139">Recompile and redeploy.</span></span> <span data-ttu-id="25aeb-140">您会注意到鼠标单击与连接的蓝牙鼠标将现在重新在沉浸式头戴式-或 HoloLens 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="25aeb-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="25aeb-141">游戏控制器支持</span><span class="sxs-lookup"><span data-stu-id="25aeb-141">Game controller support</span></span>

<span data-ttu-id="25aeb-142">游戏控制器可以是一种有趣且方便方法是允许用户控制的沉浸式 Windows Mixed Reality 体验。</span><span class="sxs-lookup"><span data-stu-id="25aeb-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="25aeb-143">将游戏控制器支持添加到的 Windows 全息版的应用程序模板的第一步是将以下私有成员声明添加到主文件的标头类：</span><span class="sxs-lookup"><span data-stu-id="25aeb-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="25aeb-144">初始化游戏板事件和任何游戏了当前连接，您的主类的构造函数中：</span><span class="sxs-lookup"><span data-stu-id="25aeb-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="25aeb-145">将这些事件处理程序添加到您的主类。</span><span class="sxs-lookup"><span data-stu-id="25aeb-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="25aeb-146">请确保更新的类名：</span><span class="sxs-lookup"><span data-stu-id="25aeb-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="25aeb-147">最后，更新输入的逻辑以识别更改控制器状态中。</span><span class="sxs-lookup"><span data-stu-id="25aeb-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="25aeb-148">在这里，我们使用相同的 m_pointerPressed 变量部分所述的上面添加鼠标事件。</span><span class="sxs-lookup"><span data-stu-id="25aeb-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="25aeb-149">添加到更新方法，它在其中检查 SpatialPointerPose 之前：</span><span class="sxs-lookup"><span data-stu-id="25aeb-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="25aeb-150">别忘了撤消注册事件时清理的主类：</span><span class="sxs-lookup"><span data-stu-id="25aeb-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="25aeb-151">重新编译，并重新部署。</span><span class="sxs-lookup"><span data-stu-id="25aeb-151">Recompile, and redeploy.</span></span> <span data-ttu-id="25aeb-152">你现在可以将附加，或对，游戏控制器并使用它来重新定位旋转多维数据集。</span><span class="sxs-lookup"><span data-stu-id="25aeb-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="25aeb-153">键盘和鼠标输入的重要指南</span><span class="sxs-lookup"><span data-stu-id="25aeb-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="25aeb-154">有一些如何在 Microsoft HoloLens – 这是主要依赖于自然用户输入 – 与启用了 Windows Mixed Reality 的 PC 上可用的设备上使用此代码的主要差异。</span><span class="sxs-lookup"><span data-stu-id="25aeb-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="25aeb-155">不能依赖于键盘或鼠标输入必须存在。</span><span class="sxs-lookup"><span data-stu-id="25aeb-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="25aeb-156">所有应用的功能必须使用提供注视、 手势和语音输入。</span><span class="sxs-lookup"><span data-stu-id="25aeb-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="25aeb-157">附加蓝牙键盘，它可以是启用您的应用程序可能会问的任何文本的键盘输入非常有帮助。</span><span class="sxs-lookup"><span data-stu-id="25aeb-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="25aeb-158">例如，这可以是听写的绝佳补充。</span><span class="sxs-lookup"><span data-stu-id="25aeb-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="25aeb-159">设计您的应用程序时，不要依赖于 （例如） WASD 和鼠标查找您的游戏控件。</span><span class="sxs-lookup"><span data-stu-id="25aeb-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="25aeb-160">HoloLens 专为用户在聊天室中四处走动。</span><span class="sxs-lookup"><span data-stu-id="25aeb-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="25aeb-161">在这种情况下，用户将直接控制照相机。</span><span class="sxs-lookup"><span data-stu-id="25aeb-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="25aeb-162">用于与移动/查看控件的房间内推动照相机的接口不会提供相同的体验。</span><span class="sxs-lookup"><span data-stu-id="25aeb-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="25aeb-163">键盘输入可以是特别是因为不会要求用户使用键盘控制您的应用或游戏引擎的调试方面的极佳途径。</span><span class="sxs-lookup"><span data-stu-id="25aeb-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="25aeb-164">将其连接设置是相同的如您所习惯，与 CoreWindow 事件 Api。</span><span class="sxs-lookup"><span data-stu-id="25aeb-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="25aeb-165">在此方案中，您可以选择实现一种方法来配置调试会话期间将键盘事件路由到"调试仅输入"模式下应用。</span><span class="sxs-lookup"><span data-stu-id="25aeb-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="25aeb-166">蓝牙控制器正常运行。</span><span class="sxs-lookup"><span data-stu-id="25aeb-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="25aeb-167">请参阅</span><span class="sxs-lookup"><span data-stu-id="25aeb-167">See also</span></span>
* [<span data-ttu-id="25aeb-168">硬件附件</span><span class="sxs-lookup"><span data-stu-id="25aeb-168">Hardware accessories</span></span>](hardware-accessories.md)
