---
title: DirectX 中的双手和运动控制器
description: 在本机 DirectX 应用中使用手动跟踪和运动控制器的开发人员指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: 双手、运动控制器、directx、输入、全息影像
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629640"
---
# <a name="hands-and-motion-controllers-in-directx"></a>DirectX 中的双手和运动控制器

在 Windows Mixed Reality 中, 手动和[运动控制器](motion-controllers.md)输入都是通过空间输入 api 处理的, 该空间输入 Api 位于[Windows. input](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)命名空间中。 这使您能够轻松地处理常见的操作, 例如在双手和运动控制器中**选择**"按相同方式"。

## <a name="getting-started"></a>即刻体验

若要访问 Windows Mixed Reality 中的空间输入, 请从 SpatialInteractionManager 接口开始。  可以通过调用[SpatialInteractionManager:: GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)访问此接口, 通常在应用启动期间进行。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager 的作业是提供对[SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)(表示输入源) 的访问权限。  系统中提供了三种 SpatialInteractionSources。
* **手型**表示用户检测到的手。 手动源根据设备提供不同的功能, 范围从 HoloLens 上的基本手势到 HoloLens 2 上的完全表述的手动跟踪。 
* **控制器**表示配对的运动控制器。 运动控制器可以提供多种功能。  例如：选择触发器、菜单按钮、"抓住按钮"、"触摸板" 和 "thumbsticks"。
* **语音**表示用户在系统中检测到的语音关键字。 例如, 每当用户显示 "选择" 时, 此源都会注入一个选择按下和释放。

源的每帧数据由[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)接口表示。 可以通过两种不同的方式来访问此数据, 这取决于您是要在应用程序中使用基于事件驱动或基于轮询的模型。

### <a name="event-driven-input"></a>事件驱动的输入
SpatialInteractionManager 提供了多个应用可以侦听的事件。  一些示例包括[SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、 [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)和[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)。

例如, 下面的代码将名为 MyApp:: OnSourcePressed 的事件处理程序挂接到 SourcePressed 事件。  这允许你的应用检测任何类型的交互源的按下操作。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

此按下的事件将在按下时与相应的 SpatialInteractionSourceState 一起异步发送到您的应用程序。 你的应用程序或游戏引擎可能需要立即执行一些处理, 或者你可能想要将事件数据排队到输入处理例程中。 下面是 SourcePressed 事件的事件处理程序函数, 该函数显示了如何检查是否已按 "选择" 按钮。

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

上述代码仅检查 "Select" 按下, 它对应于设备上的主要操作。 示例包括在 HoloLens 上执行 AirTap 或在运动控制器上拉取触发器。  "选择" 按下表示用户激活其目标全息图的意图。  将为多个不同的按钮和手势触发 SourcePressed 事件, 您可以检查 SpatialInteractionSource 上的其他属性, 以测试这些情况。

### <a name="polling-based-input"></a>基于轮询的输入
还可以使用 SpatialInteractionManager 轮询每个帧的当前输入状态。  为此, 只需对每个帧调用[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 。  此函数返回一个数组, 其中包含每个活动[SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)的一个[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 。 这意味着每个活动的运动控制器有一个, 每次被跟踪, 一个用于语音, 另一个用于语音。 然后, 你可以检查每个 SpatialInteractionSourceState 上的属性以将输入驱动到你的应用程序中。 

下面的示例演示如何使用轮询方法检查 "select" 操作。 请注意, 此*预测*变量表示可从[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)中获取的[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)对象。

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

每个 SpatialInteractionSource 都有一个 ID, 可用于标识新源并将现有源从帧关联到帧。  每次离开并输入 FOV 时, 都会为其分配一个新的 ID, 但在会话期间, 控制器 Id 保持为静态。  您可以使用 SpatialInteractionManager (如[SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected)和[SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)) 上的事件来做出手动输入或离开设备的视图, 或者当动作控制器开启/关闭或配对/不成对时做出反应。

### <a name="predicted-vs-historical-poses"></a>预测与历史记录
请注意, GetDetectedSourcesAtTimestamp 有一个时间戳参数。 这使您可以请求状态并引发预测或历史数据, 从而使您可以将空间交互与其他输入源关联起来。 例如, 在呈现当前帧中的位置时, 可以传入由[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)提供的预测时间戳。 这样一来, 系统就可以向前预测该位置, 使其与呈现的帧输出保持一致, 从而最大程度地减少感觉滞后时间。

但是, 这种预测的姿势不会生成适合于交互源的最佳定点光线。 例如, 按下运动控制器按钮时, 该事件最多可能需要20毫秒, 才能通过蓝牙向上向上冒泡到操作系统。 同样, 在用户执行手形笔势后, 在系统检测到该笔势之前一定会经历一定的时间, 然后应用程序会轮询该手势。 当应用程序轮询状态更改时, 使用的是过去发生的这种交互的头和手。 如果目标是通过将当前 HolographicFrame 的时间戳传递给 GetDetectedSourcesAtTimestamp, 则会在显示帧时将姿势预测到目标射线, 这可能会在将来显示为20毫秒。 这种未来的理由适用于*渲染*交互源, 但会因为用户在过去发生的目标问题而为*交互提供了*时间问题。

幸运的是, [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、 [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)和[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)事件提供与每个输入事件关联的历史[状态](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)。  这直接包括通过[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)提供的历史头和手中的内容, 以及可传递给其他 api 以与此事件关联的历史[时间戳](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp)。

这会在每个帧呈现和定位时提供以下最佳做法:
* 对于呈现每个帧的**手动/控制器**, 应用应按照当前帧的 photon 时间**轮询**每个交互源的**前预测**姿势。  可以通过调用每个帧的[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp)来轮询所有交互源, 并传入[HolographicFrame:: CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)提供的预测时间戳。
* 对于在按下或释放时的**手动/控制器目标**, 你的应用程序应处理按下/已释放的**事件**, raycasting 基于该事件**的打印头或**手。 可以通过以下方式获取此目标射线: 处理[SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)或[SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)事件, 从事件参数获取[状态](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)属性, 然后调用其[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)方法。

## <a name="cross-device-input-properties"></a>跨设备输入属性
SpatialInteractionSource API 支持使用各种功能的控制器和手动跟踪系统。 许多这些功能在设备类型之间是通用的。 例如, 手动跟踪和运动控制器都提供 "选择" 操作和三维位置。 只要有可能, API 就会将这些常见功能映射到 SpatialInteractionSource 上的相同属性。  这使应用程序能够更轻松地支持各种输入类型。 下表介绍了支持的属性, 以及它们如何跨输入类型进行比较。

| 属性 | 描述 | HoloLens 手势 | 运动控制器 | 明确表述|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**左右手使用习惯**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Right 或 left 右手/controller。 | 不支持 | 支持 | 支持 |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 主要按钮的当前状态。 | Air | 界限 | 宽松分流点 (直立的喷) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | 抓取按钮的当前状态。 | 不支持 | 抓取按钮 | 挤压或合上 |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | 菜单按钮的当前状态。    | 不支持 | 菜单按钮 | 不支持 |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | 控制器上的抓手或抓握位置的 XYZ 位置。 | 掌上位置 | 抓握姿势位置 | 掌上位置 |
| [SpatialInteractionSourceLocation::**取向**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | 表示手柄在控制器上的方向的四元数。 | 不支持 | 抓住姿势方向 | 棕榈方向 |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | 指针射线的原点。 | 不支持 | 支持 | 支持 |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | 指向射线的方向。 | 不支持 | 支持 | 支持 |

以上一些属性在所有设备上都不可用, API 提供了一种方法来测试这一点。 例如, 你可以检查[SpatialInteractionSource:: IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported)属性以确定源是否提供了 "获取" 操作。

### <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指针姿势

Windows Mixed Reality 支持各种外形规格的运动控制器。  它还支持已表述的手动跟踪系统。  这些系统中的所有系统都具有不同的位置和自然的 "前进" 方向, 应用应在用户的手中使用该方向或 rendreing 对象。  为支持所有此类情况, 可为手动跟踪和运动控制器提供两种类型的3D 姿势。  第一种是手柄姿势, 表示用户的手位置。  第二个是指姿势, 它表示源自用户的手或控制器的一个指针。 因此, 如果想要呈现**用户的手**或**某个对象**(例如剑或机枪), 请使用抓握姿势。 如果要从控制器或 raycast (例如, 当用户**指向 UI**时) 进行, 请使用指针姿势。

可以通过[SpatialInteractionSourceState::P r):: TryGetLocation (...)](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_)访问**抓握姿势**。定义方式如下:
* **手柄的位置**:直接按住控制器时, 掌上质心, 向左或向右调整以使其在手柄内居中。
* **手柄方向的右轴**:当你完全打开手形成一个平面的5指形姿势时, 它是一种普通于手掌的光线 (从左到右, 从右手掌向后转送)
* **手柄方向的正向轴**:部分合上时 (如同持有控制器一样), 通过非拇指指的电子管来指向 "转发" 的射线。
* **手柄方向的上轴**:向右和向后定义隐含的上轴。

可以通过[SpatialInteractionSourceState::P r):: TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或[SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)访问**指针姿势**.

## <a name="controller-specific-input-properties"></a>控制器特定的输入属性
对于控制器, SpatialInteractionSource 具有具有其他功能的控制器属性。
* **HasThumbstick:** 如果为 true, 则控制器具有操纵杆。 检查 SpatialInteractionSourceState 的[ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties)属性以获取操纵杆 x 和 y 值 (ThumbstickX 和 ThumbstickY) 以及其按下状态 (IsThumbstickPressed)。
* **HasTouchpad:** 如果为 true, 则控制器具有触摸板。 检查 SpatialInteractionSourceState 的 ControllerProperties 属性以获取触摸板 x 和 y 值 (TouchpadX 和 TouchpadY), 并了解用户是否触摸 pad (IsTouchpadTouched) 以及是否按下了触摸板 (IsTouchpadPressed).
* **SimpleHapticsController:** 控制器的 SimpleHapticsController API 可用于检查控制器的 haptics 功能, 还可用于控制 haptic 反馈。

请注意, 对于两个轴 (从下到上, 以及从左到右), 触摸板和操纵杆的范围为-1 到1。 使用 SpatialInteractionSourceState:: SelectPressedValue 属性访问的模拟触发器的范围的范围为0到1。 值为1时, 与 IsSelectPressed 等于 true;与 IsSelectPressed 关联的任何其他值将等于 false。

## <a name="articulated-hand-tracking"></a>已表述的手动跟踪
Windows Mixed Reality API 为已表述的手动跟踪提供完全支持, 例如在 HoloLens 2 上。 可在应用程序中使用可表述的手动跟踪来实现直接操作和点到提交输入模型。 它还可用于创作完全自定义交互。

### <a name="hand-skeleton"></a>手写框架
已表述的手动跟踪提供了一个允许多种不同类型的交互的25个接合式主干。  骨架为索引/中间/环/小手指提供5个接头, 为拇指提供4个接头, 并为1个手腕接头提供1个接点。  手腕接头作为层次结构的基础。 下图说明了主干的布局。

![手写框架](images/hand-skeleton.png)

在大多数情况下, 每个接点都基于它所表示的骨骼来命名。  由于每个接合都有两个骨骼, 因此我们使用基于该位置的子骨骼命名每个接合的约定。  将子骨骼定义为手腕中的骨骼。  例如, "Index 最近" 联合包含 Index 最近骨骼的开始位置和该骨骼的方向。  它不包含骨骼的结束位置。  如果需要, 您可以从层次结构中的下一个联合获得, 即 "索引中间" 联合。

除了25个层次联接外, 系统还提供了一种手掌接点。  Palm 通常不被视为主干结构的一部分。  提供此方法只是一种方便的方法, 用于获取手的整体位置和方向。

为每个接点提供以下信息:

| 名称 | 描述 |
|--- |--- |
|位置 | 联合的3D 位置, 可用于任何请求的坐标系。 |
|Orientation | 骨骼的3D 方向, 可用于任何请求的坐标系。 |
|半径 | 位于接合位置的外观的距离。 用于优化依赖于手指宽度的直接交互或可视化效果。 |
|准确性 | 提供有关系统如何自信地了解此共同信息的提示。 |

可以通过[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)上的函数访问手写框架数据。  函数被称为[TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose), 并返回一个名为[HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)的对象。  如果源不支持明确表述, 则此函数将返回 null。  有了 HandPose 后, 就可以通过调用[TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)来获取当前的联合数据, 并使用感兴趣的联合的名称。  数据返回为[JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose)结构。  下面的代码获取索引 finger 笔尖的位置。 变量*currentState*表示[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)的实例。

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

### <a name="hand-mesh"></a>手写网格

已表述的手动跟踪 API 允许使用完全 deformable 的三角手写网格。  此网格可以与手形框架实时变形, 并可用于可视化和高级物理学技术。  若要访问手写网格, 需要先通过对[SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)调用[TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)来创建一个[HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver)对象。  每个源仅需执行一次此操作, 通常是第一次出现此操作。  这意味着, 只要手进入 FOV, 就会调用此函数创建 HandMeshObserver 对象。  请注意, 这是一个异步函数, 因此你必须在此处处理一些并发操作。  在可用时, 可以通过调用[GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)来请求三角形索引缓冲区的 HandMeshObserver 对象。  索引不会在帧之间更改帧, 因此你可以获得一次框架, 并将其缓存在源的生存期内。  以顺时针缠绕顺序提供索引。

下面的代码将向上旋转分离的 std:: thread 来创建网格观察器并在网格观察器可用后提取索引缓冲区。  它从名为*currentState*的变量开始, 该变量是表示跟踪手的[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)的实例。

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
启动分离的线程只是一种用于处理异步调用的选项。  或者, 可以使用C++/WinRT. 支持的新的[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)功能

获得 HandMeshObserver 对象后, 应在其对应的 SpatialInteractionSource 处于活动状态的持续时间内保留该对象。  然后, 每个帧都可以通过调用[GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose)并传入表示想要使用顶点的[HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)实例的最新顶点缓冲区来请求该缓冲区。  缓冲区中的每个顶点都有一个位置和一个法线。  下面的示例演示如何获取手写网格的当前顶点集。  与前面一样, *currentState*变量表示[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)的实例。

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

与骨架接点不同, 手动网格 API 不允许为顶点指定坐标系统。  相反, [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate)指定在其中提供顶点的坐标系统。  然后, 可以通过调用[TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_)并指定所需的坐标系统来获取网格转换。  使用顶点时, 需要使用此网格转换。  此方法减少了 CPU 开销, 尤其是在使用网格进行呈现的情况下。

## <a name="gaze-and-commit-composite-gestures"></a>注视并提交复合手势
对于使用注视输入模式的应用程序, 尤其是在 HoloLens (第一代) 上, 空间输入 API 提供了一个可选的[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) , 可用于启用在 "select" 事件之上构建的复合手势。  通过将 SpatialInteractionManager 的交互路由到全息图的 SpatialGestureRecognizer, 应用可以跨手、语音和空间输入设备统一检测点击、保持、操作和导航事件, 而无需处理按下操作并手动释放。

SpatialGestureRecognizer 仅执行你请求的笔势集之间的最小消除歧义。 例如, 如果只需点击一下, 用户就可以随时按下手指, 而只需点击一下即可。 如果你同时请求点击和按住, 请在大约一秒后按下手指, 手势将提升为保留, 并且点击将不再出现。

若要使用 SpatialGestureRecognizer, 请处理 SpatialInteractionManager 的[InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)事件, 并抓住该处公开的 SpatialPointerPose。 使用此姿势中的用户的头看, 使其与用户的环境中的全息影像和 surface 网格相交, 以确定用户打算与之交互的用户。 然后, 使用[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)方法将事件参数中的 SpatialInteraction 路由到目标全息影像的 SpatialGestureRecognizer。 这将根据在创建时或由[TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)在该识别器上设置的[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings)开始解释该交互。

在 HoloLens (第一代) 上, 交互和手势通常应从用户的头盔获得目标, 而不是尝试直接在该位置上呈现或交互。 开始交互后, 可以使用该手型的相对运动来控制该笔势, 如操作或导航手势。

## <a name="see-also"></a>请参阅
* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [直接操作输入模型](direct-manipulation.md)
* [点和提交输入模型](point-and-commit.md)
* [注视并提交输入模型](gaze-and-commit.md)
* [运动控制器](motion-controllers.md)
