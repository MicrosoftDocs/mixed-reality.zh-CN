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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>键盘、 鼠标和 DirectX 中的控制器输入

键盘、 鼠标和游戏控制器所有可以是输入的用于 Windows Mixed Reality 设备的有用窗体。 蓝牙键盘和鼠标是同时支持 HoloLens，使用具有调试您的应用程序或作为输入的替代形式。 Windows Mixed Reality 还支持附加至 Pc-其中鼠标、 键盘和游戏控制器就是长久以来一种规范的沉浸式耳机。

若要针对 HoloLens，对向你的设备的蓝牙键盘使用键盘输入，或使用通过 Windows Device Portal 虚拟输入。 若要戴上的 Windows Mixed Reality 沉浸式头戴式耳机时使用键盘输入，请将其放在设备上或使用 Windows 键 + Y 的键盘组合分配混合现实输入的焦点。 请注意用于 HoloLens 的应用程序都必须提供功能，而无需连接这些设备。

>[!NOTE]
>这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。  这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。

## <a name="subscribe-for-corewindow-input-events"></a>对于 CoreWindow 的输入事件订阅

### <a name="keyboard-input"></a>键盘输入

在 Windows 全息版的应用程序模板中，我们包括键盘输入，就像任何其他 UWP 应用的事件处理程序。 您的应用程序使用键盘输入的数据 Windows Mixed Reality 同样的方式。

从 AppView.cpp:

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

### <a name="virtual-keyboard-input"></a>虚拟键盘输入
为沉浸式桌面耳机，还可以支持对沉浸式视图呈现的 Windows 的虚拟键盘。 若要支持此功能，您的应用程序可以实现**CoreTextEditContext**。 这允许 Windows 了解自己应用程序呈现的文本框的状态，因此虚拟键盘可以正确参与存在的文本。

有关实现 CoreTextEditContext 支持的详细信息，请参阅[CoreTextEditContext 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)。

### <a name="mouse-input"></a>鼠标输入

此外可以使用鼠标输入，再次通过 UWP CoreWindow 输入的事件处理程序。 下面介绍了如何修改 Windows 全息版的应用程序模板，以在相同的方式按下手势支持鼠标单击。 后进行这种修改，戴上沉浸式头戴式耳机设备时单击鼠标将重新定位该多维数据集。

请注意，UWP 应用还可以通过使用获取原始 XY 数据鼠标[MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API。

首先声明 AppView.h 中的新 OnPointerPressed 处理程序：

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

在 AppView.cpp，到 SetWindow 中添加以下代码：

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

然后将此定义，OnPointerPressed 放在该文件的底部：

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

我们刚添加的事件处理程序是传递到模板的主类。 让我们修改以支持此传递的主类。 将此公共方法声明添加到标头文件：

```
// Handle mouse input.
       void OnPointerPressed();
```

你将需要此私有成员变量，以及：

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

最后，我们将使用新的逻辑，以支持鼠标单击更新的主类。 首先，通过添加此事件处理程序。 请确保更新的类名：

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

现在，在更新方法中，将为用于获取与此指针姿势现有的逻辑：

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

重新编译和重新部署。 您会注意到鼠标单击与连接的蓝牙鼠标将现在重新在沉浸式头戴式-或 HoloLens 多维数据集。

### <a name="game-controller-support"></a>游戏控制器支持

游戏控制器可以是一种有趣且方便方法是允许用户控制的沉浸式 Windows Mixed Reality 体验。

将游戏控制器支持添加到的 Windows 全息版的应用程序模板的第一步是将以下私有成员声明添加到主文件的标头类：

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

初始化游戏板事件和任何游戏了当前连接，您的主类的构造函数中：

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

将这些事件处理程序添加到您的主类。 请确保更新的类名：

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

最后，更新输入的逻辑以识别更改控制器状态中。 在这里，我们使用相同的 m_pointerPressed 变量部分所述的上面添加鼠标事件。 添加到更新方法，它在其中检查 SpatialPointerPose 之前：

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

别忘了撤消注册事件时清理的主类：

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

重新编译，并重新部署。 你现在可以将附加，或对，游戏控制器并使用它来重新定位旋转多维数据集。

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>键盘和鼠标输入的重要指南

有一些如何在 Microsoft HoloLens – 这是主要依赖于自然用户输入 – 与启用了 Windows Mixed Reality 的 PC 上可用的设备上使用此代码的主要差异。
* 不能依赖于键盘或鼠标输入必须存在。 所有应用的功能必须使用提供注视、 手势和语音输入。
* 附加蓝牙键盘，它可以是启用您的应用程序可能会问的任何文本的键盘输入非常有帮助。 例如，这可以是听写的绝佳补充。
* 设计您的应用程序时，不要依赖于 （例如） WASD 和鼠标查找您的游戏控件。 HoloLens 专为用户在聊天室中四处走动。 在这种情况下，用户将直接控制照相机。 用于与移动/查看控件的房间内推动照相机的接口不会提供相同的体验。
* 键盘输入可以是特别是因为不会要求用户使用键盘控制您的应用或游戏引擎的调试方面的极佳途径。 将其连接设置是相同的如您所习惯，与 CoreWindow 事件 Api。 在此方案中，您可以选择实现一种方法来配置调试会话期间将键盘事件路由到"调试仅输入"模式下应用。
* 蓝牙控制器正常运行。

## <a name="see-also"></a>请参阅
* [硬件附件](hardware-accessories.md)
