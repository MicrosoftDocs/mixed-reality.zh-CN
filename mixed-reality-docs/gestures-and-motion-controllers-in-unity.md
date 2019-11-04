---
title: Unity 中的手势和运动控制器
description: 您可以通过两种主要方式在 Unity、手型手势和运动控制器中执行操作。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手势，运动控制器，unity，注视，输入
ms.openlocfilehash: a7ca5a895015ba0458f0f64f1422612e797f5067
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435225"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Unity 中的手势和运动控制器

您可以通过两种主要方式在您的[HMD 中进行](gaze-in-unity.md)操作，在 HoloLens 和沉浸式的中的[手势](gaze-and-commit.md#composite-gestures)和[运动控制器](motion-controllers.md)。 可以通过 Unity 中的相同 Api 访问空间输入的两个源的数据。

Unity 提供了两种主要方法来访问 Windows Mixed Reality 的空间输入数据、跨多个 Unity XR Sdk 工作的*GetButton/GetAxis* *api，* 以及特定于公开一组可用空间输入数据的 Windows 混合现实。

## <a name="unity-buttonaxis-mapping-table"></a>Unity 按钮/轴映射表

下表中的 button 和 axis Id 通过*GetButton/GetAxis* Api 在 Unity 的 "Windows Mixed Reality 运动控制器" 的输入管理器中受支持，而 "windows MR 特定" 列是指可用的属性*InteractionSourceState*类型。 以下各节将详细介绍其中的每个 Api。

Windows Mixed Reality 的按钮/轴 ID 映射通常与 Oculus 按钮/轴 Id 匹配。

Windows Mixed Reality 的按钮/轴 ID 映射在以下两个方面不同于 OpenVR 的映射：
1. 该映射使用不同于操纵杆的触摸板 Id，以支持同时具有 thumbsticks 和触摸板的控制器。
2. 映射可避免对菜单按钮的 A 和 X 按钮 Id 进行重载，以使它们可用于物理 ABXY 按钮。

<table>
<tr>
<th rowspan="2">Input </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">公共 Unity Api</a><br />（GetButton/GetAxis） </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 专用输入 API</a><br />XR.WSA.送</th>
</tr><tr>
<th> 左手 </th><th> 右手</th>
</tr><tr>
<td> 选择触发按下 </td><td> 轴 9 = 1。0 </td><td> 轴 10 = 1。0 </td><td> selectPressed</td>
</tr><tr>
<td> 选择触发器模拟值 </td><td> 轴9 </td><td> 轴10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 选择触发器部分按下 </td><td> 按钮 14 <i>（游戏板兼容）</i> </td><td> 按钮 15 <i>（游戏板兼容）</i> </td><td> selectPressedAmount &gt; 0。0</td>
</tr><tr>
<td> 按下菜单按钮 </td><td> 按钮 6 * </td><td> 按钮 7 * </td><td> menuPressed</td>
</tr><tr>
<td> 按下手柄按钮 </td><td> Axis 11 = 1.0 （无模拟值）<br />按钮 4 <i>（游戏板兼容）</i> </td><td> 轴 12 = 1.0 （无模拟值）<br />按钮 5 <i>（游戏板兼容）</i> </td><td> grasped</td>
</tr><tr>
<td> 操纵杆 X <i>（左：-1.0，右：1.0）</i> </td><td> 轴1 </td><td> 轴4 </td><td> thumbstickPosition</td>
</tr><tr>
<td> 操纵杆 Y <i>（顶部：-1.0，底端：1.0）</i> </td><td> 轴2 </td><td> 轴5 </td><td> thumbstickPosition</td>
</tr><tr>
<td> 已按下操纵杆 </td><td> 按钮8 </td><td> 按钮9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> 触摸板 X <i>（左：-1.0，右：1.0）</i> </td><td> 轴 17 * </td><td> 轴 19 * </td><td> touchpadPosition</td>
</tr><tr>
<td> 触摸板 Y <i>（顶部：-1.0，底端：1.0）</i> </td><td> Axis 18 * </td><td> 轴 20 * </td><td> touchpadPosition</td>
</tr><tr>
<td> 接触触摸板 </td><td> 按钮 18 * </td><td> 按钮 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> 已按触摸板 </td><td> 按钮 16 * </td><td> 按钮 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 手柄姿势或指针姿势 </td><td colspan="2"> 仅限<i>抓握</i>： <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> Pass<i>手柄</i>或<i>指针</i>作为参数： SourceState. sourcePose. TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 跟踪状态 </td><td colspan="2"> <i>位置准确性和源丢失风险仅通过 MR 专用 API 提供</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>这些按钮/轴 Id 不同于 Unity 用于 OpenVR 的 Id，因为 gamepads、Oculus 触控和 OpenVR 所使用的映射中出现冲突。

## <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指针姿势

Windows Mixed Reality 支持多种形式的运动控制器，其中每个控制器的设计在用户的手位置和自然的 "前进" 方向上不同，应用程序在呈现控制器.

为了更好地表示这些控制器，可以针对每个交互源来调查两种类型的姿势，**手柄姿势**和**指针姿势**。 手柄姿势和指针姿势坐标都由全局 Unity 世界坐标中的所有 Unity Api 表示。

### <a name="grip-pose"></a>抓握姿势

**手柄姿势**表示由 HoloLens 检测到的掌托的位置，或包含运动控制器的掌托的位置。

在沉浸式耳机上，手柄姿势最适合用于呈现**用户的手**或**持有用户的对象**，例如剑或机枪。 可视化运动控制器时也使用手柄姿势，因为用于运动控制器的 Windows 提供的**呈现模型**使用手柄姿势作为原点和旋转中心。

手柄姿势的定义具体如下：
* **手柄位置**：在固定控制器时，掌上质心，向左或向右调整以使其在手柄内居中。 在 Windows Mixed Reality 运动控制器上，此位置通常与 "抓住" 按钮对齐。
* **手柄方向的右轴**：当你完全打开手形成一个平面的5指形姿势时，它是一种普通于手掌的光线（从左到右，从右手掌向前）
* **抓握方向的正向轴**：在部分合上（就像持有控制器一样），通过非拇指指的电子管来指向 "转发" 的射线。
* **手柄方向的上轴**：向右和向后定义隐含的上轴。

可以通过 Unity 的跨供应商输入 API （XR）访问抓握姿势 *[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/轮换*），或通过 WINDOWS MR 专用 API （*sourceState*，为**抓握**节点请求数据）。

### <a name="pointer-pose"></a>指针姿势

**指针姿势**代表着控制器的末端。

系统提供的指针姿势最适合用于在**呈现控制器模型本身**时进行 raycast。 如果要渲染某个其他虚拟对象来替代控制器（如虚拟压力），则应使用该虚拟对象的最自然的光线，如沿应用定义的机枪模型的桶向下移动的射线。 由于用户可以看到虚拟对象，而不是物理控制器，因此，使用虚拟对象指向虚拟对象可能会更自然地使用应用。

目前，指针姿势仅通过 Windows MR 专用 API TryGetPosition/轮换提供，并传入 InteractionSourceNode 作为参数传递 。 *sourceState/sourcePose。*

## <a name="controller-tracking-state"></a>控制器跟踪状态

与耳机一样，Windows Mixed Reality 运动控制器不需要外部跟踪传感器的设置。 相反，控制器由耳机本身中的传感器跟踪。

如果用户将控制器移出耳机的视图，则在大多数情况下，Windows 将继续推断控制器位置，并将其提供给应用。 如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。

此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。 许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。

为此，最好的方法是亲自尝试一下。 查看此视频，其中包含可在各种跟踪状态下使用运动控制器的沉浸式内容的示例：

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>显式跟踪状态的推理

希望根据跟踪状态以不同方式对位置进行处理的应用可能会进一步检查控制器状态的属性，如*SourceLossRisk*和*PositionAccuracy*：

<table>
<tr>
<th> 跟踪状态 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高准确度</b> </td><td style="background-color: green; color: white"> &lt; 1。0 </td><td style="background-color: green; color: white"> “高” </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精度（存在丢失的风险）</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: green; color: white"> “高” </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>准确度</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>无位置</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: orange"> false</td>
</tr>
</table>

这些运动控制器跟踪状态的定义如下：
* **高准确度：** 尽管运动控制器位于耳机的视图中，但它通常会根据视觉对象跟踪提供高准确性位置。 请注意，在暂时离开耳机传感器时，移动控制器（如用户的另一方面）将继续根据控制器的惯性跟踪来返回较短的长时间（例如，用户）自动.
* **高精度（存在丢失的风险）：** 当用户将运动控制器移出耳机的视图边缘后，耳机不久就无法直观地跟踪控制器的位置。 此应用通过查看**SourceLossRisk**到1.0，来了解控制器何时到达此 FOV 边界。 此时，应用程序可以选择暂停需要稳定的高质量姿势流的控制器手势。
* **近似准确性：** 如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。 此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。 许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。 输入要求更高的应用可通过检查**PositionAccuracy**属性，从**高**准确度到**接近**准确性，并为用户提供更宽松的 hitbox在此期间。
* **无位置：** 尽管控制器可以在很长时间内正常运行，但有时系统也知道，甚至在目前不会有任何意义。 例如，刚刚打开的控制器可能从未被直观观察，或者用户可能会关闭控制器，然后由其他人选取。 在这种情况下，系统不会提供应用程序的任何位置，并且*TryGetPosition*将返回 false。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>常见 Unity Api （GetButton/GetAxis）

**命名空间：** *UnityEngine*、 *UnityEngine. XR*<br>
**类型**：*输入*， *XR。InputTracking*

Unity 目前使用其常规*输入. GetButton/GetAxis* Api 公开[Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)和 Windows Mixed Reality 的输入，包括双手和运动控制器。 如果你的应用程序使用这些 Api 进行输入，则它可以在多个 XR Sdk （包括 Windows Mixed Reality）中轻松支持运动控制器。

### <a name="getting-a-logical-buttons-pressed-state"></a>获取逻辑按钮的按下状态

若要使用一般 Unity 输入 Api，通常先将按钮和轴向上滑到[Unity 输入管理器](https://docs.unity3d.com/Manual/ConventionalGameInput.html)中的逻辑名称，然后将按钮或轴 id 绑定到每个名称。 然后，你可以编写引用该逻辑按钮/轴名称的代码。

例如，若要将左运动控制器的触发器按钮映射到 "提交" 操作，请在 Unity 内执行 "**编辑 > 项目设置" > 输入**，然后展开 "轴" 下 "提交" 部分的属性。 更改 "**正整数" 按钮**或 " **Alt 正向按钮**" 属性以阅读**游戏杆按钮 14**，如下所示：

![Unity 的 InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

然后，你的脚本可以使用*GetButton*检查提交操作：

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
可以通过在 "**轴**" 下更改 " **Size** " 属性来添加更多逻辑按钮。

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>直接获取物理按钮的按下状态

你还可以使用*GetKey*，通过其完全限定的名称手动访问按钮：

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>获取手或运动控制器的姿势

可以使用 XR 访问控制器的位置和旋转 *。InputTracking*：

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

请注意，这代表控制器的手柄姿势（其中包含控制器），这对于渲染用户的剑或压力或控制器本身的模型非常有用。

请注意，在此手柄之间的关系（控制器的笔尖指向的指针）可能会因控制器而异。 目前，仅通过 MR 专用输入 API （在以下各节中介绍）才能访问控制器的指针姿势。

## <a name="windows-specific-apis-xrwsainput"></a>特定于 Windows 的 Api （XR。WSA.送

**命名空间：** *UnityEngine. XR*<br>
**类型**： *InteractionManager*、 *InteractionSourceState*、 *InteractionSource*、 *InteractionSourceProperties*、 *InteractionSourceKind*、 *InteractionSourceLocation*

若要获取有关 Windows Mixed Reality 手型输入（适用于 HoloLens）和运动控制器的更多详细信息，可以选择在*UnityEngine*命名空间下使用特定于 Windows 的空间输入 api。 这样，你就可以访问其他信息，例如位置准确性或源种类，使你可以区分手和控制器。

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>对双手和运动控制器的状态进行轮询

可以使用*GetCurrentReading*方法轮询每个交互源（手形或运动控制器）的此帧状态。

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

返回的每个*InteractionSourceState*表示当前时刻的交互源。 *InteractionSourceState*显示如下信息：
* 发生了哪些[类型的按下](motion-controllers.md)（选择/菜单/抓住/触摸板/操纵杆）

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* 其他特定于运动控制器的数据，例如触摸板和/或操纵杆的 XY 坐标和接触状态

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* 要了解源是手型还是运动控制器的 InteractionSourceKind

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>轮询前向预测呈现姿势

* 当轮询来自双手和控制器的交互源数据时，您获得的是向前预测的，这是框架的 photons 将达到用户的眼睛。  这些向前预测的姿势最适合用于**呈现**控制器或每个帧的持有对象。  如果你使用的是针对控制器的给定按下或发布，则如果你使用下面所述的历史事件 Api，则会最为准确。

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* 你还可以获取此当前帧的前推预测 head。  与源姿势一样，这对于**呈现**游标非常有用，但如果你使用下面所述的历史事件 api，则以给定的按下或释放为目标是最准确的。

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

若要在输入事件的准确历史记录数据发生时处理输入事件，可处理交互源事件，而不是轮询。

处理交互源事件：
* 注册*InteractionManager*输入事件。 对于你感兴趣的每种类型的交互事件，你需要订阅该事件。

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* 处理事件。 订阅交互事件后，会在适当的时候获取回调。 在*SourcePressed*示例中，这会在检测到源后、发布或丢失之前。

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

### <a name="how-to-stop-handling-an-event"></a>如何停止处理事件

如果不再对事件感兴趣或正在销毁已订阅事件的对象，则需要停止处理事件。 若要停止处理事件，请取消订阅该事件。

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>交互源事件的列表

可用的交互源事件包括：
* *InteractionSourceDetected* （源变为活动状态）
* *InteractionSourceLost* （变为非活动状态）
* *InteractionSourcePressed* （点击，按下按钮或 "选择" 失措）
* *InteractionSourceReleased* （点击、松开按钮或 "Select" 失措结束）
* *InteractionSourceUpdated* （移动或以其他方式更改某种状态）

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>最准确地匹配新闻或发布的历史目标姿势的事件

前面所述的轮询 Api 为应用程序带来了前推预测的姿势。  尽管这些预测的姿势最适用于渲染控制器或虚拟手持对象，但出于以下两个重要原因，未来的姿势并不是最佳目标：
* 当用户按下控制器上的按钮时，可能会在系统接收到印刷机之前，20毫秒通过蓝牙的无线延迟。
* 然后，如果您使用的是前推预测型，则会有另一个20毫秒的向前预测应用于当前帧的 photons 将达到用户眼睛的时间。

这意味着，轮询会为你提供40ms 的源姿势或 head 型，这是从用户的负责人和手在按下或释放时实际返回的位置。  对于 HoloLens 手写输入，在没有无线传输延迟的情况下，可以使用类似的处理延迟来检测按键。

若要精确地根据用户的原始意图或按下控制器，应使用来自该*InteractionSourcePressed*或*InteractionSourceReleased*输入事件的历史源姿势或 head 姿势。

你可以从用户的头或其控制器使用历史姿势数据作为新闻或发布的目标：
* 当该笔势或控制器按下时，头姿势会出现，**可用于确定**用户的[gazing](gaze-and-commit.md) ：

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

* 当运动控制器按下时，源会出现，这可用于确定用户在何处定位控制器的**目标**。  这将是遇到按下的控制器的状态。  如果要渲染控制器本身，可以请求指针，而不是手柄姿势，以从用户将考虑呈现的控制器的自然提示的那种情况下，

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高级复合手势 Api （GestureRecognizer）

**命名空间：** *UnityEngine. XR*<br>
**类型**： *GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*

您的应用程序还可以识别空间输入源、点击、保持、操作和导航笔势的更高级复合手势。 您可以使用 GestureRecognizer 在[手](gaze-and-commit.md#composite-gestures)和[运动控制器](motion-controllers.md)中识别这些组合手势。

GestureRecognizer 上的每个手势事件都提供输入的 SourceKind，以及事件发生时的目标 head 射线。 某些事件提供其他特定于上下文的信息。

使用手势识别器捕获手势只需几个步骤：
1. 创建新的手势识别器
2. 指定要监视的手势
3. 订阅这些手势的事件
4. 开始捕获手势

### <a name="create-a-new-gesture-recognizer"></a>创建新的手势识别器

若要使用*GestureRecognizer*，必须创建*GestureRecognizer*：

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>指定要监视的手势

通过*SetRecognizableGestures （）* 指定你感兴趣的手势：

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>订阅这些手势的事件

订阅感兴趣的手势的事件。

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
>导航和操作手势在*GestureRecognizer*的实例上互相排斥。

### <a name="start-capturing-gestures"></a>开始捕获手势

默认情况下，在调用*StartCapturingGestures （）* 之前， *GestureRecognizer*不监视输入。 如果在处理*StopCapturingGestures （）* 的帧之前执行了输入，则可能会在调用*StopCapturingGestures （）* 后生成笔势事件。 *GestureRecognizer*将记得在实际发生该笔势的 previou 帧期间，它是处于打开还是关闭状态，因此，根据此帧的注视目标启动和停止手势监视是可靠的。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>停止捕获手势

停止手势识别：

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>删除手势识别器

请记住，在销毁*GestureRecognizer*对象之前，取消订阅已订阅的事件。

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>在 Unity 中呈现运动控制器模型

![运动控制器模型和 teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*运动控制器模型和 teleportation*

若要在应用中渲染与用户所持有的物理控制器相匹配的运动控制器，并在按下各种按钮时进行解释，可以在[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/)中使用**MotionController prefab** 。  此 prefab 从系统的已安装运动控制器驱动程序在运行时动态加载正确的 glTF 模型。  必须动态加载这些模型，而不是在编辑器中手动导入它们，以便您的应用程序能够显示您的用户可能拥有的任何当前和未来控制器的物理上准确的3D 模型。

1. 按照[入门](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)说明下载混合现实工具包，并将其添加到 Unity 项目。
2. 如果在入门步骤中将相机替换为*MixedRealityCameraParent* prefab，则准备就绪！  该 prefab 包括运动控制器呈现。  否则，请从 "项目" 窗格中将*资产/HoloToolkit/Input/prototyping/MotionControllers*添加到场景中。  你需要将该 prefab 添加为你用来移动相机的任何父对象的子对象，以使该用户在场景中 teleports 时，使控制器与用户一起工作。  如果应用不涉及 teleporting，只需在场景的根目录中添加 prefab。

## <a name="throwing-objects"></a>引发对象

在虚拟现实中引发对象是一项困难的问题，因此可能会出现问题。 与大多数基于物理的交互一样，当游戏中的抛出意外时，它会立即出现，并打破浸入式。 我们花了一些时间来了解如何表示物理上正确的引发行为，并通过我们的平台的更新启用了一些准则，我们想要与你共享。

可在[此处](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到如何实现引发的示例。 此示例遵循以下四个准则：
* **使用控制器的*速度*（而不是位置**）。 在11月的 Windows 更新中，我们引入了["近似" 位置跟踪状态](motion-controllers.md#controller-tracking-state)下的行为更改。 在此状态下，只要我们认为它是高准确度，就会继续报告关于控制器的速度信息，这通常比位置长。
* **合并控制器的*角度速度*** 。 此逻辑全部包含在 `GetThrownObjectVelAngVel` 静态方法的 `throwing.cs` 文件中，位于上面链接的包中：
   1. 在角度速度为 conserved 的情况下，引发的对象必须保持与抛出时相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. 由于引发的对象很大范围可能不会成为手柄姿势的中心，因此它可能具有不同的速度，而控制器在用户的引用框架中。 以这种方式提供的对象速度的部分是围绕控制器原点的已抛出对象的质量的瞬间相切速度。 此相切速度是控制器角度速度的叉积，向量表示控制器原点与所引发对象的质量中心之间的距离。
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. 因此，已引发对象的总速度是控制器的速度和此相切速度的总和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* 密切**关注我们应用速度的*时间*** 。 按下某个按钮后，最多可能需要20毫秒该事件才能通过蓝牙向上向上冒泡到操作系统。 这意味着，如果你将控制器状态更改从按下状态更改为未按下，反之亦然，控制器会提供你获取的信息。 接下来，轮询 API 所提供的控制器可能是向前预测的，以反映在帧显示时可能出现的情况，这可能会在未来20毫秒。 这适用于*呈现*已保存的对象，但会在计算用户释放其引发的时间轨迹时，为*目标*对象提供时间问题。 幸运的是，在11月更新中，当发送 Unity 事件（如*InteractionSourcePressed*或*InteractionSourceReleased* ）时，该状态会在实际按下或释放按钮时，包含历史记录数据。  若要在引发期间获得最准确的控制器呈现和控制器目标，则必须根据需要正确使用轮询和事件：
   * 对于每个帧的**控制器呈现**，你的应用程序应将控制器的*GameObject*放在前预测的控制器上，为当前帧的 photon 时间提供。  可以从 XR 等 Unity 轮询 Api 获取此数据 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。WSA.InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* 。
   * 对于**控制器**针对按下或释放的目标，应用程序应基于该按下或释放事件的历史控制器提出的 raycast 和计算轨迹。  可以从 Unity 事件 Api 获取此数据，如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 。
* **使用手柄姿势**。 相对于手柄姿势报告角度速度和速度，而不是指针姿势。

在将来的 Windows 更新中，引发将继续改进，你可以在此处找到详细信息。

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>MRTK v2 中的手势和运动控制器

可以从输入管理器访问笔势和运动控制器。 
* [MRTK v2 中的手势](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [MRTK v2 中的运动控制器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>遵循教程

混合现实学院中提供了更详细的自定义示例的分步教程：

- [MR 输入211：手势](holograms-211.md)
- [MR 输入213：运动控制器](mixed-reality-213.md)

[![MR 输入 213-运动控制器](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR 输入 213-运动控制器*

## <a name="see-also"></a>另请参阅

* [头部凝视并提交](gaze-and-commit.md)
* [运动控制器](motion-controllers.md)


