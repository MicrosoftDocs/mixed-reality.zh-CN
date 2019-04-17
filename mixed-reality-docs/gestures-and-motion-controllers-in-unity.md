---
title: 手势和 Unity 中的动作控制器
description: 有两种主要方式，在你的视线移动中 Unity、 手势和动作控制器上执行操作。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手势、 运动控制器、 unity、 输入的视线移动
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590125"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>手势和 Unity 中的动作控制器

有两种主要方式，若要对其执行操作您[对此 Unity](gaze-in-unity.md)，[传递手势](gestures.md)并[动作控制器](motion-controllers.md)。 通过在 Unity 中相同的 Api 访问空间输入这两个源的数据。

Unity 提供了两种主要方式，若要访问的 Windows Mixed Reality，常见的输入的空间数据*Input.GetButton/Input.GetAxis*跨多个 Unity XR Sdk 工作的 Api 和*InteractionManager /GestureRecognizer* API 特定于 Windows Mixed Reality 公开完整的可用空间的输入数据集。

## <a name="unity-buttonaxis-mapping-table"></a>Unity 按钮/轴映射表

下表中的按钮和轴 Id 支持 Unity 的输入管理器中通过 Windows Mixed Reality 运动控制器*Input.GetButton/GetAxis* Api，而"特定于 Windows MR 的"列属性可用的中断*InteractionSourceState*类型。 以下各节中详细描述每个这些 Api。

Windows Mixed Reality 的按钮/轴 ID 映射通常与 Oculus 按钮/轴 Id 相匹配。

Windows Mixed Reality 的按钮/轴 ID 映射不同的两种方式 OpenVR 的映射：
1. 映射使用触摸板 Id 进行不同于摇杆，以支持 thumbsticks 和触摸板的域控制器。
2. 映射可避免重载菜单按钮的 Id，以保留这些适用于物理 ABXY 按钮中的 A 和 X 按钮。

<table>
<tr>
<th rowspan="2">Input </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">常见的 Unity Api</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">特定于 Windows MR 的输入的 API</a><br />(XR.WSA.Input)</th>
</tr><tr>
<th> 左侧显示 </th><th> 右侧</th>
</tr><tr>
<td> 选择按下的触发器 </td><td> 轴 9 = 1.0 </td><td> 轴 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> 选择触发器模拟值 </td><td> 轴 9 </td><td> 轴 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 按下的部分选择触发器 </td><td> 按钮 14 <i>（游戏板兼容性）</i> </td><td> 按钮 15 <i>（游戏板兼容性）</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> 按下菜单按钮 </td><td> 按钮 6 * </td><td> 按钮 7 * </td><td> menuPressed</td>
</tr><tr>
<td> 按下的手柄按钮 </td><td> 11 = 1.0 （未模拟值） 轴<br />按钮 4 <i>（游戏板兼容性）</i> </td><td> 12 = 1.0 （未模拟值） 轴<br />按钮 5 <i>（游戏板兼容性）</i> </td><td> 由于</td>
</tr><tr>
<td> 摇杆 X <i>(左:-1.0，正确：1.0)</i> </td><td> 轴 1 </td><td> 轴 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> 摇杆 Y <i>(顶部:-1.0，底部：1.0)</i> </td><td> 轴 2 </td><td> 轴 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> 按下的摇杆 </td><td> 按钮 8 </td><td> 按钮 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> 触摸板 X <i>(左:-1.0，正确：1.0)</i> </td><td> 轴 17 * </td><td> 轴 19 * </td><td> touchpadPosition.x</td>
</tr><tr>
<td> 触摸板 Y <i>(顶部:-1.0，底部：1.0)</i> </td><td> 轴 18 * </td><td> 轴 20 * </td><td> touchpadPosition.y</td>
</tr><tr>
<td> 触摸板接触 </td><td> 按钮 18 * </td><td> 按钮 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> 按下触摸板 </td><td> 按钮 16 * </td><td> 按钮 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 手柄姿势或指针姿势 </td><td colspan="2"> <i>手柄</i>只会造成：<a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> 传递<i>手柄</i>或<i>指针</i>作为参数： sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 跟踪状态 </td><td colspan="2"> <i>位置准确性和源丢失风险，仅可通过特定于 MR 的 API</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>这些按钮/轴 Id 不同于用于由于游戏板，Oculus 触摸和 OpenVR 所使用的映射中的冲突而 OpenVR Unity 的 Id。

## <a name="grip-pose-vs-pointing-pose"></a>与指针姿势手柄姿势

Windows Mixed Reality 支持不同的外形规格运动控制器，使用每个控制器设计各不相同，"转发"方向该应用的自然用户的手位置之间的关系应为使用指向呈现时控制器。

若要更好地表示这些控制器，有两种类型的可以为每个交互源，调查的带来**手柄姿势**并**指针姿势**。 手柄姿势和指针姿势坐标来表示通过以全局 Unity 世界坐标表示的所有 Unity Api。

### <a name="grip-pose"></a>手柄姿势

**手柄姿势**表示检测到的 HoloLens 手的形状的手掌或手掌持有运动控制器的位置。

在沉浸式耳机手柄姿势最适合用于呈现**用户的手**或**对象保存在用户的手中**，例如双刃剑或手段。 作为可视化的运动控制器，也会使用手柄姿势**可呈现模型**提供由 Windows 动作控制器使用手柄姿势作为其起点和旋转中心。

手柄姿势定义具体而言，如下所示：
* **抓住位置**:Palm 质心时保存在控制器正常情况下，调整左侧或右侧居中手柄内的位置。 Windows Mixed Reality 动作在控制器上，此位置通常与掌握按钮对齐。
* **抓住方向的右轴**:完全打开您的手以形成平面 5 手指姿势，ray 的时您的手掌接触到正常 （从左 palm，向右 palm 从后向前）
* **抓住正轴方向的**:当您关闭您的手部分 （就像按控制器），"forward"通过管通过非 thumb 手指点与射线。
* **抓住方向沿轴向上**:权限隐含的权限和转发定义最多轴。

您可以通过任一 Unity 跨供应商输入 API 访问手柄姿势 (*[XR。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation*) 或通过特定于 Windows MR 的 API (*sourceState.sourcePose.TryGetPosition/Rotation*，请求会带来数据**手柄**节点)。

### <a name="pointer-pose"></a>指针姿势

**指针姿势**表示转发指向控制器的提示。

你是，到 raycast 最合适使用系统提供的指针姿势**呈现控制器模型本身**。 当您呈现某些其他虚拟对象代替控制器，例如虚拟手段，您应点与最自然会为该虚拟对象，如应用程序定义枪模型的笔杆都沿着一条射线。 由于用户可以看到虚拟对象，而不是物理的控制器，指向与虚拟对象可能会使那些使用您的应用程序更加自然。

目前，指针姿势现已推出只能通过特定于 Windows MR 的 API，Unity *sourceState.sourcePose.TryGetPosition/Rotation*，并传入*InteractionSourceNode.Pointer*为自变量。

## <a name="controller-tracking-state"></a>控制器跟踪状态

耳机，如 Windows Mixed Reality 运动控制器不需要外部跟踪传感器的任何设置。 相反，控制器会跟踪耳机本身中的传感器。

如果用户移出耳机的字段的视图控制器，在大多数情况下 Windows 会继续推断控制器位置并将它们提供给应用程序。 当控制器已失去时长不足，控制器的位置将会断开与近似准确性位置可视化跟踪。

此时，系统会将主体锁定的用户，跟踪用户的位置，随着对象移动，同时仍提供的控制器，则返回 true 方向使用其内部方向传感器到控制器。 使用控制器指向并激活用户界面元素的许多应用程序可以无需用户注意到正常运行中近似的准确性。

为此感到的最佳方式是亲自尝试一下。 请查看此视频中通过跨各种跟踪状态适用于运动控制器的沉浸式内容的示例：

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>有关显式跟踪状态的推论

想要将基于跟踪状态以不同方式的位置的应用程序可能会更进一步，如检查控制器的状态的属性*SourceLossRisk*并*PositionAccuracy*:

<table>
<tr>
<th> 跟踪状态 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高精度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>（在丢失的风险） 的高精度</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>近似值的准确性</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>不到位置</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: orange"> false</td>
</tr>
</table>

这些动作控制器跟踪状态定义，如下所示：
* **高精度：** 在 motion 控制器耳机的字段的视图中时，它通常将提供高准确性位置，基于可视化跟踪。 请注意，移动控制器的暂时离开视图的字段或暂时不可用遮盖耳机传感器 (例如，用户的另一只手) 将继续返回高准确性带来基于控制器的惯性跟踪在短时间本身。
* **（在丢失的风险） 的高精度：** 当用户移动的运动控制器超过耳机的视角的边缘时，耳机很快将无法直观地跟踪控制器的位置。 应用已知道控制器当通过查看达到此 FOV 边界**SourceLossRisk**达到 1.0。 此时，应用程序可以选择暂停需要稳定的高质量带来的控制器手势。
* **近似值的准确性：** 当控制器已失去时长不足，控制器的位置将会断开与近似准确性位置可视化跟踪。 此时，系统会将主体锁定的用户，跟踪用户的位置，随着对象移动，同时仍提供的控制器，则返回 true 方向使用其内部方向传感器到控制器。 控制器用于指向并激活用户界面元素的许多应用程序可以作为正常段中近似的准确性在运行而无需用户注意到。 具有较输入要求的应用可以选择感应从此下降**高**精度为**近似**准确性通过检查**PositionAccuracy**属性，用于可以向用户授予在允许较大 hitbox 屏外目标在此期间的示例。
* **不到位置：** 控制器可以长时间运行近似值的准确性，而有时系统就知道目前没有意义甚至正文锁定的位置。 例如，只需开启控制器可能永远不会观察到以可视方式，或者用户可能放下一个控制器，然后选取其他人。 在这些情况下，系统将不会提供到应用程序中的任意位置并*TryGetPosition*将返回 false。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>常见的 Unity Api (Input.GetButton/GetAxis)

**命名空间：***UnityEngine*， *UnityEngine.XR*<br>
**类型**:*输入*， *XR。InputTracking*

Unity 当前使用其常规*Input.GetButton/Input.GetAxis* Api 来公开的输入[Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)， [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)和 Windows Mixed Reality 包括双手和动作控制器。 如果您的应用程序使用这些 Api 作为输入，它可以轻松地跨多个 XR Sdk，包括 Windows Mixed Reality 支持运动控制器。

### <a name="getting-a-logical-buttons-pressed-state"></a>获取逻辑按钮的按下的状态

若要使用的常规 Unity 输入 Api，则通常先接通按钮和轴中的逻辑名称[Unity 输入管理器](https://docs.unity3d.com/Manual/ConventionalGameInput.html)，绑定到每个名称的按钮或轴 Id。 然后可以编写该逻辑的按钮轴名称引用的代码。

例如，若要将左的运动控制器的触发器按钮映射到提交操作，请访问**编辑 > 项目设置 > 输入**在 Unity 中，展开提交部分下轴的属性。 更改**表扬按钮**或**Alt 正按钮**属性以读取**游戏杆按钮 14**，如下所示：

![Unity 的 InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

然后，您的脚本可以检查提交操作使用*Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
您可以通过更改添加更多逻辑按钮**大小**下的属性**轴**。

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>直接获取的物理按钮按下的状态

您还可以访问按钮手动通过其完全限定名称，使用*Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>获取手形或运动控制器姿势

您可以访问的位置和旋转的控制器，使用*XR。InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

请注意，这表示控制器的手柄姿势 （其中的用户都包含在控制器），可用于呈现双刃剑或用户的手或控制器本身的模型中的手段。

请注意此手柄姿势和指针姿势 （其中指向控制器的提示） 之间的关系可能会因控制器。 此时，访问控制器的指针姿势才可通过特定于 MR 的输入 API，在以下各节所述。

## <a name="windows-specific-apis-xrwsainput"></a>特定于 Windows 的 Api (XR。WSA。输入）

**命名空间：***UnityEngine.XR.WSA.Input*<br>
**类型**:*InteractionManager*， *InteractionSourceState*， *InteractionSource*， *InteractionSourceProperties*， *InteractionSourceKind*， *InteractionSourceLocation*

若要获取更多详细信息 （对于 HoloLens) 的 Windows Mixed Reality 手动输入和动作控制器，你可以选择使用特定于 Windows 的空间输入的 Api 下*UnityEngine.XR.WSA.Input*命名空间。 这允许您访问其他信息，如位置准确性或源类型，让您告诉双手和控制器分离。

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>轮询双手和动作控制器的状态

可以针对每个交互源 （手动或动画控制器） 使用此帧状态轮询*GetCurrentReading*方法。

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

每个*InteractionSourceState*您获取在当前时刻后表示交互源。 *InteractionSourceState*如公开信息：
* 这[类型的按下](motion-controllers.md)发生 （选择/菜单/掌握/触摸板/摇杆）

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* 其他特定于运动控制器，此类的触摸板和/或摇杆的 XY 坐标和接触的状态的数据

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* 若要了解是否源是手的形状或运动控制器 InteractionSourceKind

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>正向预测呈现带来轮询

* 轮询以查找从手和控制器交互源数据，您获取的带来时，正向预测带来的时刻，当此帧 photons 将到达用户的眼球。  这些正向预测带来最适合用于**呈现**控制器或保持对象的每个帧。  如果你是针对给定的按还是发布与控制器，将获得更加准确，如果您使用历史事件如下所述的 Api。

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* 此外可以获取此当前帧的正向预测头部姿势。  由于与源姿势，这是用于**呈现**一个游标，但以给定的按或发布目标将是最准确，如果您使用历史事件如下所述的 Api。

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>处理交互源事件

若要使用其准确历史姿势数据发生时处理输入的事件，可以处理交互源事件，而不是轮询。

若要处理的交互的源事件：
* 注册，以便*InteractionManager*输入的事件。 对于每个类型的交互事件感兴趣，您需要订阅它。

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* 处理的事件。 一旦您订阅的交互事件，你将收到回调在适当的时候。 在中*SourcePressed*示例中，这将是检测到源后，在发布或丢失之前。

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>如何停止处理的事件

需要停止时您将不再对感兴趣事件或确实要销毁已订阅该事件的对象处理事件。 若要停止处理事件，您随时取消订阅事件。

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>交互源事件的列表

可进行的交互源事件是：
* *InteractionSourceDetected* （源变为活动状态）
* *InteractionSourceLost* （变为非活动状态）
* *InteractionSourcePressed* （点击、 按下按钮，或"选择"失措）
* *InteractionSourceReleased* （点击、 释放或"Select"失措末尾的结尾）
* *InteractionSourceUpdated* （移动或更改某些状态）

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>最能准确匹配按或发布的历史记录目标带来的事件

前面所述的轮询 Api 提供您的应用程序正向预测带来。  虽然这些预测的带来最适合于呈现的控制器或虚拟的手持对象，未来带来不适合面向两个主要原因：
* 当用户按下控制器上的按钮时，可以有大约 20 毫秒的无线延迟通过蓝牙之前系统收到按下了。
* 然后，如果您使用的正向预测姿势存在将另一个 10-20 毫秒的正向预测应用以面向当前帧的 photons 时将到达用户的眼球的时间。

这意味着轮询为您提供了源姿势或头部姿势从其中用户的 head 和手实际上是按或发布完成的操作时，它是 30 40ms年进。  对于 HoloLens 手动输入，而没有任何无线传输延迟，没有类似的处理延迟，以检测按下了。

准确地基于用户的原始意图的手形或控制器按下的目标，应使用的历史源姿势或从该头部姿势*InteractionSourcePressed*或*InteractionSourceReleased*输入的事件。

可以针对按下的某个或发布与来自用户的头或其控制器的历史姿势数据：
* 头部姿势手势或控制器在按下时的时间时刻发生，可以使用该**面向**来确定用户已[观望](gaze.md)处：

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* 在 motion 控制器在按下时的时刻源姿势发生，可以使用该**面向**来确定哪些用户指向位于控制器。  这将是遇到按下了控制器的状态。  如果呈现控制器本身，则可以请求指针姿势而不是以投篮机会控制在从用户将考虑的内容的呈现控制器的自然提示的目标射线手柄姿势：

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>事件处理程序示例

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高级复合手势 Api (GestureRecognizer)

**命名空间：***UnityEngine.XR.WSA.Input*<br>
**类型**:*GestureRecognizer*， *GestureSettings*， *InteractionSourceKind*

您的应用程序还可以识别空间输入的源，Tap 中，保持状态、 操作和导航笔势的更高级别的复合操作。 您可以在两者之间识别这些复合笔势[手](gestures.md)并[动作控制器](motion-controllers.md)使用 GestureRecognizer。

GestureRecognizer 上的每个手势事件提供事件的时间在输入以及目标头 ray SourceKind。 一些事件提供附加上下文特定信息。

有仅几个步骤所需捕获使用笔势识别器手势：
1. 创建新的笔势识别器
2. 指定要监视的手势
3. 订阅的这些手势事件
4. 开始捕获手势

### <a name="create-a-new-gesture-recognizer"></a>创建新的笔势识别器

若要使用*GestureRecognizer*，您必须创建*GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>指定要监视的手势

指定你感兴趣通过这些手势*SetRecognizableGestures()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>订阅的这些手势事件

订阅的事件感兴趣的笔势。

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>导航和操作手势是互斥的实例上*GestureRecognizer*。

### <a name="start-capturing-gestures"></a>开始捕获手势

默认情况下*GestureRecognizer*不会监视输入直到*StartCapturingGestures()* 调用。 可能的手势事件可能会生成后*StopCapturingGestures()* 如果输入之前在帧已执行，则调用其中*StopCapturingGestures()* 已处理。 *GestureRecognizer*会记住是否它已打开或关闭在其中实际发生手势，在早期帧期间因此它是可靠地启动和停止手势监视基于目标的此帧的视线移动。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>停止捕获手势

若要停止手势识别：

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>删除的手势识别程序

请记住要销毁之前取消订阅已订阅事件*GestureRecognizer*对象。

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>呈现在 Unity 中的动作控制器模型

![运动控制器模型和 teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*运动控制器模型和 teleportation*

若要呈现匹配你的用户持有并清楚地表述的各种按钮被按下物理控制器的运动控制器应用程序中，可以使用**MotionController 预设**中[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  此预设可从系统的已安装的运动控制器驱动程序动态加载在运行时的正确 glTF 模型。  务必要动态加载这些模型而不是手动导入它们在编辑器中，以便您的应用程序会显示以物理方式准确的三维模型的所有当前和未来控制器以你的用户可能有。

1. 请按照[Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)说明下载混合现实工具包并将其添加到你的 Unity 项目。
2. 如果替换使用照相机*MixedRealityCameraParent*预设作为入门教程步骤的一部分，您就可以开始 ！  该预设可包括运动控制器呈现。  否则，添加*Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab*到您从项目窗格中的场景。  你将想要添加任何父对象的子级为 prefab 用于围绕时使照相机在场景中的用户 teleports，以便在控制器都会随用户。  如果您的应用程序并不涉及 teleporting，只需添加预设可在您的场景的根目录。

## <a name="throwing-objects"></a>引发对象

虚拟现实中引发的对象是棘手的问题，则它可能最初看起来。 如使用最以物理方式根据交互，引发在游戏的行为以意外方式时，它非常直观，并将深入探讨。 我们花费了有关如何表示以物理方式正确引发行为，并提出了一些指导原则，我们的平台，我们想要与你共享的更新通过启用深度一些时间来研究。

您可以找到相关的建议来实现引发示例[此处](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)。 此示例按下列四个原则：
* **使用控制器的*速度*而不是位置**。 在 Windows 的年 11 月更新，我们引入了行为发生变化时在['近似' 位置跟踪状态](motion-controllers.md#controller-tracking-state)。 在此状态下，速度有关控制器的信息将继续，只要我们都很高的准确性，通常是时间比位置一直保持高精度时间长的报告。
* **将合并*角速度*控制器的**。 此逻辑都包含在`throwing.cs`文件中`GetThrownObjectVelAngVel`以上链接的包中的静态方法：
   1. 如角速度供电来节约，则引发该异常的对象必须维护相同角速度因为它会引发目前有： `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. 可能不手柄姿势原点，它可能具有不同的速度就在那时，在控制器中的用户的参考框架则引发该异常对象的质心的原样。 以这种方式提供的对象的部分是质的对象的速度的围绕控制器源引发心的即时叙事速度。 此叙事速度是对象的角速度控制器与表示控制器源引发的质心的之间的距离矢量的叉积。
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. 则引发该异常对象的总速度因此是控制器的速度和此叙事速度的总和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **密切关注*时间*我们的应用速度**。 按下按钮时，可能需要最多 20 毫秒向上冒泡通过蓝牙操作系统到该事件。 这意味着，如果未按下状态轮询的控制器状态更改为按下或反之亦然，使用它获取的控制器姿势信息实际上就会领先于此状态中的更改。 此外，主讲人我们轮询 API 控制器姿势向前预测以反映在帧将显示在将来可能是从多个然后 20 毫秒的时间可能姿势。 此方案的好处*呈现*保存对象，但也会增加为我们时间问题*面向*对象我们目前计算轨迹用户发布其抛出。 幸运的是，通过年 11 月更新，如果 Unity 事件喜欢*InteractionSourcePressed*或*InteractionSourceReleased*发送，该状态包括历史姿势数据从后何时按钮为实际按下或释放。  若要获取最准确的控制器呈现和过程，则会引发目标控制器，必须根据需要正确使用轮询和事件处理:
   * 有关**控制器呈现**每个帧，您的应用程序应放置在控制器*GameObject*进预测控制器级别会带来的当前帧的 photon 时间。  从 Unity 轮询的 Api，例如获取此数据*[XR。InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。WSA。Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。
   * 有关**控制器面向**按或版本，您的应用程序应 raycast 和计算基础按或发布事件的历史控制器姿势的轨迹。  你收到此数据从 Unity eventing Api，如 *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。
* **使用手柄姿势**。 相对于手柄姿势不指针姿势报告角速度和速度。

引发将继续改进未来的 Windows 更新，并且，你可能需要对其在此处找到更多信息。

## <a name="accelerate-development-with-mixed-reality-toolkit"></a>加速开发的混合现实工具包

有两个有关 InputManager 和 MotionController Unity 中的示例场景。 通过这些场景中，可以了解如何使用 MRTK 的 InputManager 和通过动作控制器按钮来访问数据处理事件。

- [HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [技术详细信息的自述文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

![输入 MRTK 中的示例场景](images/MRTK_ExampleScene_Input.png)<br>
*输入 MRTK 中的示例场景*

### <a name="automatic-scene-setup"></a>自动场景安装程序

当您导入[MRTK 发布 Unity 包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或从克隆项目[GitHub 存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，要在 Unity 中查找新菜单混合现实工具包。 在配置菜单中，你会看到菜单应用混合现实场景设置。 当您单击它时，它默认照相机中删除，并添加基础组件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，并[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。

![MRTK 场景设置菜单](images/MRTK_Input_Menu.png)<br>
*MRTK 场景设置菜单*

![自动场景中 MRTK 的安装程序](images/MRTK_HowTo_Input1.png)<br>
*自动场景中 MRTK 的安装程序*

### <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera 预设

您可以手动添加这些项目面板中。 您可以找到这些组件作为预设。 当您搜索**MixedRealityCamera**，你将能够看到两个不同的照相机预设。 其差异是， **MixedRealityCamera**才照相机 prefab 而**MixedRealityCameraParent**包括如 Teleportation，Motion 沉浸式耳机的其他组件控制器和，边界。

![在 MRTK 照相机预设](images/MRTK_HowTo_Input2.png)<br>
*在 MRTK 照相机预设*

**MixedRealtyCamera**支持 HoloLens 和沉浸式头戴式耳机。 它检测到的设备类型，并优化了清除标志和 Skybox 等属性。 可以在下面查找一些有用的属性可以自定义光标，Motion 控制器模型，如自定义和 Floor。

![游标和 Floor 运动控制器属性](images/MRTK_HowTo_Input3.png)<br>
*游标和 Floor 运动控制器属性*

## <a name="follow-along-with-tutorials"></a>按照教程

混合现实学院中提供了分步教程，使用更多详细的自定义示例：

- [MR 输入 211:手势](holograms-211.md)
- [MR 输入 213:运动控制器](mixed-reality-213.md)

[![MR 输入 213-运动控制器](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR 输入 213-运动控制器*

## <a name="see-also"></a>请参阅

* [手势](gestures.md)
* [运动控制器](motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [InteractionInputSource.cs MixedRealityToolkit Unity 中](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
