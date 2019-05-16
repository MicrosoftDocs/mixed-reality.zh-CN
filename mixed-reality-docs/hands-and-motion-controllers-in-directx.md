---
title: 双手和动作中 DirectX 的控制器
description: 在本机 DirectX 应用中使用手动跟踪和动作控制器的开发人员指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: 手、 运动控制器、 directx、 输入、 全息
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629640"
---
# <a name="hands-and-motion-controllers-in-directx"></a>双手和动作中 DirectX 的控制器

在 Windows 混合现实中，同时传递并[运动控制器](motion-controllers.md)中找到的空间输入 Api，通过处理输入[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)命名空间。 这使你能够轻松处理常见操作，例如**选择**跨双手和动作控制器按相同的方式。

## <a name="getting-started"></a>即刻体验

在 Windows Mixed Reality 中输入要访问空间，开始与 SpatialInteractionManager 接口。  可以通过调用来访问此界面[SpatialInteractionManager::GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)、 在应用启动期间通常一段时间内。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager 的工作是提供访问权限[SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)，其表示的输入源。  有三种类型的 SpatialInteractionSources 系统中提供。
* **手**表示检测到的用户的手。 手源提供了基于在 HoloLens 上基本手势到清楚手动跟踪 HoloLens 2 上的范围的设备的不同功能。 
* **控制器**表示配对的运动控制器。 运动控制器可以提供的各种功能。  例如：选择触发器、 菜单按钮、 掌握按钮、 触摸板和 thumbsticks。
* **语音**表示谈到系统检测到关键字的用户的声音。 例如，此源将注入选择按下并释放时用户所讲的"选择"。

每个帧数据源以表示[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)接口。 有两种不同的方式来访问此数据，具体取决于是否想要在应用程序中使用事件驱动的或基于轮询的模型。

### <a name="event-driven-input"></a>事件驱动的输入
SpatialInteractionManager 提供您的应用程序可以侦听的事件数。  一些示例包括[SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)， [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)并[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)。

例如，下面的代码挂接事件处理程序调用 MyApp::OnSourcePressed SourcePressed 事件。  这可让应用来检测任何类型的交互源上，按下按钮。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

此按下的事件发送到您的应用程序以异步方式，以及在按下了发生的时相应 SpatialInteractionSourceState。 你的应用或游戏引擎可能需要执行一些处理立即或你可能想要在输入处理例程中的事件数据进行排队。 下面是 SourcePressed 事件，其中说明了如何检查是否选择按钮曾按下一个事件处理程序函数。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

上面的代码仅检查 Select press，它对应于在设备上的主要操作。 示例包括执行 HoloLens 上的 AirTap 或拉取运动控制器上的触发器。  在 select，按下按钮表示用户的意图激活它们面向的全息图。  SourcePressed 事件将激发为许多不同的按钮和手势，并可以检查 SpatialInteractionSource 要测试这种情况下上的其他属性。

### <a name="polling-based-input"></a>基于轮询的输入
SpatialInteractionManager 还可用于轮询的输入的当前状态的每一帧。  若要执行此操作，只需调用[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp)每一帧。  此函数返回一个数组，包含一个[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)对于每个活动[SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)。 如果最近失措 select 命令，这意味着分别为每个活动的运动控制器，每个被跟踪的指针和语音。 到应用程序可以检查每个驱动器输入 SpatialInteractionSourceState 上的属性。 

下面是如何检查使用轮询方法 select 操作的示例。 请注意，*预测*变量表示[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)对象，可以从获取[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

每个 SpatialInteractionSource 有一个 ID，用于标识新的源和关联帧之间的现有源。  每次它们保持，然后输入 FOV，控制器 Id 的会话的持续时间内保持不变，但手分配一个新的 ID。  您可以使用事件上 SpatialInteractionManager 如[SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected)并[SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)、 时手进入或离开设备做出反应的查看，或当运动控制器打开/关闭或配对/不成对。

### <a name="predicted-vs-historical-poses"></a>与历史带来预测
请注意，GetDetectedSourcesAtTimestamp 时间戳参数。 这使您可以请求状态，并且会带来可以预测的数据或历史记录，让您关联与其他输入源的空间交互。 例如，当呈现当前帧中的手形图标的位置，您可以传递中提供的预测时间戳[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。 这使系统以正向预测的手的位置与呈现的帧输出中，最大程度减少感知到的延迟紧密地保持一致。

但是，此类预测的姿势不会生成与交互源定位理想指针 ray。 例如，motion 控制器按钮按下时，可能需要最多 20 毫秒向上冒泡通过蓝牙操作系统到该事件。 同样，用户执行手动手势后，系统检测到笔势和应用程序，然后为其轮询之前，可能会通过一段时间。 时您的应用程序轮询状态更改，头节点和现有带来用于映射到在过去实际上发生交互的目标。 如果你面向通过将当前 HolographicFrame 的时间戳传递给 GetDetectedSourcesAtTimestamp，姿势将改为向前预测到的目标的射线时将显示在帧，这在将来可能会超过 20 毫秒。 此将来姿势适合*呈现*交互源，但会构成我们时间问题*面向*交互，如用户的目标发生在过去。

幸运的是， [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)， [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)并[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)事件提供历史[状态](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)与相关联每个输入事件。  这直接包括可通过历史头节点和现有带来[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)，以及历史[时间戳](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp)可传递给其他 Api 将与此事件相关联。

这产生了以下最佳实践时呈现和与双手和控制器针对每个帧：
* 有关**手/控制器呈现**每个帧，您的应用程序应**轮询**有关**进预测**在当前帧的 photon 时带来的交互的每个源。  可以通过调用轮询交互的所有源[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp)中提供的预测时间戳传递每个帧[HolographicFrame::CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)。
* 有关**手/控制器面向**按或版本，您的应用程序应处理按下/释放**事件**，光线投射的细节基于**历史**的头或手动姿势该事件。 通过处理获取此目标 ray [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)或[SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)事件时，获取[状态](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)属性从事件参数，并调用其[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)方法。

## <a name="cross-device-input-properties"></a>跨设备输入的属性
SpatialInteractionSource API 支持控制器和手动跟踪系统与大范围的功能。 很多这些功能之间是通用的设备类型。 例如，手动跟踪和动作控制器这两种都提供 select 操作和 3D 的位置。 如有可能，API 将这些常见功能映射到 SpatialInteractionSource 上的相同属性。  这使应用程序可以更轻松地支持各种输入类型。 下表描述的属性的支持，以及它们如何在输入类型进行比较。

| 属性 | 描述 | HoloLens 手势 | 运动控制器 | 明确的手|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**左右手使用习惯**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | 右侧或左侧 / 控制器。 | 不支持 | 支持 | 支持 |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 主要按钮的当前状态。 | 敲击 | 触发器 | 宽松空气点击 （竖直的情况下捏合） |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | 随取即行按钮的当前状态。 | 不支持 | 获取按钮 | 捏合或已关闭的手 |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | 菜单按钮的当前状态。    | 不支持 | 菜单按钮 | 不支持 |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | 在控制器上的手形或手柄位置的 x y Z 位置。 | Palm 位置 | 手柄姿势位置 | Palm 位置 |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | 四元数，表示手形或手柄的方向会造成在控制器上。 | 不支持 | 手柄姿势方向 | Palm 方向 |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | 指针的射线的原点。 | 不支持 | 支持 | 支持 |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | 指针的射线的方向。 | 不支持 | 支持 | 支持 |

某些上述属性不在所有设备上可用，该 API 提供了一种方法来对此进行测试。 例如，您可以检查[SpatialInteractionSource::IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported)属性来确定源是否提供了掌握现有操作。

### <a name="grip-pose-vs-pointing-pose"></a>与指针姿势手柄姿势

Windows Mixed Reality 支持各种外形规格的运动控制器。  它还支持明确的手动跟踪系统。  所有这些系统具有不同的手位置和应用程序应使用的用户的手中的指向或 rendreing 对象的自然"转发"方向之间的关系。  若要支持所有这些，有两种类型的三维带来的两个手动跟踪和动作控制器提供。  第一种是手柄姿势，表示用户的手位置。  第二个指向姿势，表示指针射线源自用户的手或控制器。 因此，如果你想要呈现**用户的手**或**对象保存在用户的手中**，如双刃剑或手段，使用手柄姿势。 如果希望从控制器或手的形状，例如，如果用户是 raycast**指向 UI** ，使用指针姿势。

您可以访问**手柄姿势**通过[SpatialInteractionSourceState::Properties::TryGetLocation(...)](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).它定义，如下所示：
* **抓住位置**:Palm 质心时保存在控制器正常情况下，调整左侧或右侧居中手柄内的位置。
* **抓住方向的右轴**:完全打开您的手以形成平面 5 手指姿势，ray 的时您的手掌接触到正常 （从左 palm，向右 palm 从后向前）
* **抓住正轴方向的**:当您关闭您的手部分 （就像按控制器），"forward"通过管通过非 thumb 手指点与射线。
* **抓住方向沿轴向上**:权限隐含的权限和转发定义最多轴。

您可以访问**指针姿势**通过[SpatialInteractionSourceState::Properties::TryGetLocation （...）:: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或[SpatialInteractionSourceState::TryGetPointerPose （...）:: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)。

## <a name="controller-specific-input-properties"></a>特定于控制器的输入的属性
对于控制器，SpatialInteractionSource 具有通过附加功能的控制器属性。
* **HasThumbstick:** 如果为 true，则控制器有摇杆。 检查[ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) SpatialInteractionSourceState 获取摇杆属性 x 和 y 值 （ThumbstickX 和 ThumbstickY），以及其按下的状态 (IsThumbstickPressed)。
* **HasTouchpad:** 如果为 true，则控制器具有触摸板。 检查 SpatialInteractionSourceState 获取触摸板的 ControllerProperties 属性 x 和 y 值 （TouchpadX 和 TouchpadY），并了解如果用户触摸板 (IsTouchpadTouched)，并且它们按下 （触摸板IsTouchpadPressed)。
* **SimpleHapticsController:** 在控制器 SimpleHapticsController API 允许你检查控制器的 haptics 功能并允许您控制 haptic 反馈。

请注意触摸板和摇杆的范围是-1 到 1 的两个轴 （从底部到顶部，和从左到右）。 对于模拟的触发器，请访问使用 SpatialInteractionSourceState::SelectPressedValue 属性，该范围提供一系列的 0 到 1。 值为 1 的关联与 IsSelectPressed 等于 true;任何其他值将等于 false 的 IsSelectPressed 与相关联。

## <a name="articulated-hand-tracking"></a>明确的手动跟踪
Windows 混合现实 API 为明确手动跟踪，例如 HoloLens 2 上提供完整支持。 明确的手动跟踪可用于在应用程序中实现直接操作和点提交输入的模型。 此外可以用于创建完全自定义的交互。

### <a name="hand-skeleton"></a>手框架
明确的手动跟踪提供了一个 25 联合框架，使许多不同类型的交互。  框架提供的索引/中间/环/小手指 5 关节、 thumb，4 关节和 1 手腕联合。  手腕联合可作为层次结构的基础。 下图演示了框架的布局。

![手框架](images/hand-skeleton.png)

在大多数情况下，每个联合是名为基于它所代表的骨骼。  由于在每个联合没有两个基本，我们使用的命名子终日在该位置上基于每个联合的约定。  子骨骼被定义为最荒谬不过手腕终日。  例如，"索引 Proximal"联合包含索引 proximal 骨骼的开始位置和该骨骼的方向。  它不包含终日的结束位置。  如果您需要的则会得到它与下一个联合中的层次结构，"索引中间"联合。

除了 25 分层连接符和系统提供的手掌接触联接。  Palm 通常不考虑了框架结构的一部分。  它只能作为方便地获取手形图标的整体位置和方向提供。

可以为每个联合提供以下信息：

| 名称 | 描述 |
|--- |--- |
|位置 | 接合，任何请求的坐标系统中可用的三维位置。 |
|Orientation | 三维方向的骨骼，可以在任何请求的坐标系统。 |
|半径 | 到图面中的联合位置的外观的距离。 这有助于优化直接交互或依赖于手指宽度的可视化效果。 |
|准确性 | 有关此联合的信息系统大家都有多大把握上提供的提示。 |

你可以访问手主干数据通过函数的指针上[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。  调用的函数[TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)，并返回一个名为对象[HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)。  如果源不支持明确的手，此函数将返回 null。  HandPose 后，你可以通过调用来获取当前联合数据[TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)，联合的名称与你感兴趣。  作为返回的数据[JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose)结构。  以下代码获取食指提示的位置。 在变量*currentState*表示的实例[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>手网格

为了使完全 deformable 三角形手网格允许明确的手动跟踪 API。  此网格可以 deform 实时以及现有的主干中，并可用于可视化效果以及高级的物理技术。  若要访问现有网格，您需要首先创建[HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver)对象通过调用[TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)上[SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)。  此操作仅需执行一次每个源，通常您看到的第一个时间。  这意味着将调用此函数可创建 HandMeshObserver 对象，无论何时手的形状进入 FOV。  请注意，这是异步函数，因此您必须进行少量的此处并发处理。  一旦可用，则可以要求 HandMeshObserver 对象的三角形索引缓冲区通过调用[GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)。  索引不更改段帧，以便您可以一次获取上述信息和源的生存期内对其进行缓存。  顺时针缠绕顺序中提供了索引。

下面的代码启动创建网格观察者分离 std::thread 并可用的网络观察程序后提取索引缓冲区。  它首先创建一个名为变量*currentState*，即实例[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)表示跟踪手的形状。

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
正在启动的已分离的线程是一个选项来处理异步调用。  或者，您可以使用新[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)支持的功能C++/WinRT。

HandMeshObserver 对象后，您应保存到其相应 SpatialInteractionSource 处于活动状态的持续时间。  然后每个帧，则可以要求它通过调用表示手形图标的最新顶点缓冲区[GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose)并传入[HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)实例，它表示所需的顶点姿势有关。  每个顶点缓冲区中的具有位置和常规。  下面是如何获取当前的一组顶点的手网格的示例。  像以前那样*currentState*变量所表示的实例[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

与主干关节手网格 API 不允许您指定用于顶点的坐标系统。  相反， [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate)指定中提供了顶点的坐标系统。  然后可以通过调用获取网格转换[TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_)并指定所需的坐标系统。  你将需要使用此网格转换，每当使用顶点。  此方法降低了 CPU 开销，尤其是如果您仅使用用于呈现网格。

## <a name="gaze-and-commit-composite-gestures"></a>注视并提交复合手势
特别是在 HoloLens 上使用的视线移动提交输入的模型中，为应用程序 （第一代） 空间输入 API 提供了一个可选[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) ，可以用于启用基础上构建的复合手势选择事件。  通过从 SpatialInteractionManager 到一张全息图 SpatialGestureRecognizer 路由交互，应用可以检测到点击、 按住、 操作和导航事件统一跨手、 语音和空间的输入的设备，而无需处理，按下按钮并手动释放。

SpatialGestureRecognizer 执行仅之间的一套手势你请求的最小消除歧义。 例如，如果请求只需点击，用户可能会按他们的手指下，只要他们喜欢和点击仍会发生。 如果请求同时点击并按住后约一秒钟的按下他们的手指，手势将升级到某个保留，都不会出现一个分流点。

若要使用 SpatialGestureRecognizer，处理 SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)事件和随取即行 SpatialPointerPose 那里公开。 使用此姿势从用户的头的视线移动 ray 与全息相交并在用户的环境中网格以确定用户打算与之交互的图面。 然后，将 SpatialInteraction 路由到目标 hologram SpatialGestureRecognizer 事件参数中使用其[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)方法。 这将启动解释根据该交互[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings)上的识别器设置，可以在创建时的或通过[TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)。

HoloLens 上 (首先 gen)，其目标从用户的头的视线移动，而不是非试着来呈现或直接在现有的位置进行交互的交互和手势通常应派生。 一旦启动交互，相对动作的手可能用于控制手势，如同操作或导航笔势。

## <a name="see-also"></a>请参阅
* [在 DirectX 中的头节点和关注视线移动](gaze-in-directx.md)
* [直接操作输入的模型](direct-manipulation.md)
* [点提交输入的模型](point-and-commit.md)
* [视线移动和提交的输入的模型](gaze-and-commit.md)
* [运动控制器](motion-controllers.md)
