---
title: Unreal 中的手动跟踪
description: 说明如何在 Unreal 中使用手动跟踪
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，手动跟踪
ms.openlocfilehash: 3f7f4dd1eb62cb707eaaf8632a2ba3c280a4ac31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835363"
---
# <a name="hand-tracking"></a>手动跟踪

手动跟踪系统使用用户的不要和手指作为 Unreal 的输入。 开发人员可以获得每个手指的位置和旋转、整个手掌，甚至是在自己的代码中使用的手势。 

## <a name="hand-pose"></a>举手

使用举手，开发人员可以将活动用户的手和手指作为输入进行跟踪。 此系统通过蓝图和 c + + 公开。 技术详细信息位于对应的 WinRT 类[HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose)中。 "Unreal API" 以 Unreal 的坐标系统格式提供数据，而 "时钟周期" 与 Unreal 引擎同步。

### <a name="enum"></a>枚举

EWMRHandKeypoint 介绍了手形的骨骼层次结构。 

建立

![手动 Keypoint 最佳实践](images/unreal/hand-keypoint-bp.png)
 
C++：
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

![手写框架](images/hand-skeleton.png)

可以在[HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)表中找到这些数值。
 
### <a name="functions"></a>函数

若要在蓝图中使用手跟踪功能，请打开 "手跟踪/Windows Mixed Reality"

![手动跟踪最佳实践](images/unreal/hand-tracking-bp.png)

对于 c + + 函数，包括 "WindowsMixedRealityHandTrackingFunctionLibrary"

最佳

![支持手动跟踪最佳实践](images/unreal/supports-hand-tracking-bp.png)
 
C++：
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

如果设备支持手动跟踪，则返回 true; 如果没有手写跟踪，则返回 false。

最佳

![获取手动联合转换](images/unreal/get-hand-joint-transform.png)
 
C++：
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

此函数返回手型的空间数据。 数据将更新框架中的每个帧，返回的值将被缓存。 出于性能方面的考虑，不建议在此函数上使用繁重的逻辑。 

* 用户**的手边，** 可以是左侧或右侧
* **Keypoint** –手型的骨骼。 
* **转换**–骨骼基的坐标和方向。 若要获取骨骼末尾的转换数据，应请求下一个骨骼的基。 特殊的 Tip 骨骼提供 distal 的结尾。 
* **半径**-骨骼基的半径。
* **返回值**-如果在此帧中跟踪了骨骼，则为 true; 如果未跟踪骨骼，则为 false。

## <a name="hand-live-link-animation"></a>手动实时链接动画
使用实时链接插件向动画显示手姿势。 [此处](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)提供了插件文档

如果启用了 Windows Mixed Reality 和 Live Link 插件，请跳到**Window > Live link**打开 "实时链接编辑器" 窗口。 单击 " **+ 源" 按钮**并启用 Windows Mixed Reality 手动跟踪源

![实时链接源](images/unreal/live-link-source.png)
 
启用源并打开任何动画资产后，动画的 "预览场景" 选项卡将具有以下附加选项（详细信息位于 Unreal 的实时链接文档中，因为插件已在 beta 中，此过程稍后可能会更改）

![实时链接动画](images/unreal/live-link-animation.png)
 
手型动画层次结构与在 EWMRHandKeypoint 中的层次结构相同。 可以使用 WindowsMixedRealityHandTrackingLiveLinkRemapAsset 重定向动画。 

![实时链接动画2](images/unreal/live-link-animation2.png)
 
它可以在编辑器中进行子类化

![实时链接重新映射](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a>手写网格
表示用户指针的网格。 

![手写网格](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a>如何启用和配置

开发人员可以直接访问手动网格，以实现自己的目的。 必须在 ARSessionConfig 中启用此访问： AR 设置-> 世界映射-> 从跟踪的几何图形生成网格数据。 

下面是网格的默认参数：

1.  将网格数据用于封闭
2.  为网格数据生成冲突
3.  为网格数据生成导航网格
4.  以线框–用于显示生成的网格的 debug 参数呈现网格数据

对于混合现实项目，这些参数值将用作空间映射网格和手写网格默认值。 开发人员可以在任何特定网格的 BP 或代码中更改它们。

### <a name="c-api-reference"></a>C + + API 参考 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

此值是所有以可跟踪对象中的手写网格。

```cpp
class FARSupportInterface 
{
public:
// other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

当系统检测到任何以可跟踪对象（包括手写网格）时，将调用这些委托。 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
委托的处理程序应具有以下签名：
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

可以通过访问网格数据`UARTrackedGeometry::GetUnderlyingMesh`

### <a name="blueprint-api-reference"></a>蓝图 API 参考

开发人员应将 AR 以可跟踪通知组件添加到蓝图参与者

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
然后，请前往组件的详细信息 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
并在添加/更新/删除跟踪的几何图形上覆盖，代码如下所示：

![在 ARTrackable 通知上](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>手写光线

开发人员可以使用手型作为指针设备。 系统可在 c + + 和蓝图中使用。 从技术上说，它公开了[SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)

必须指出的是，由于所有函数的结果都更改每个帧，因此它们都是可调用的。 有关纯 vs 非纯或可调用函数的详细信息，请参阅[。](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

对于蓝图，打开 "Windows Mixed Reality HMD"

![手动射线最佳实践](images/unreal/hand-rays-bp.png)
 
C + + 包含 "WindowsMixedRealityFunctionLibrary"

### <a name="enum"></a>枚举

![输入控制器按钮](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* **Select** --用户触发的 select 事件，可通过 airtap 或 "注视并提交" 在 HoloLens 2 中触发。 触发此事件的另一种方法是说 "Select"。 
* **抓住**–用户触发的抓住事件，该事件在 HoloLens 2 中通过将用户的手指关闭到全息图上触发。 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* **NotTracked** –手写不可见
* **跟踪**–完全跟踪

### <a name="struct"></a>结构

![指针姿势信息最佳实践](images/unreal/pointer-pose-info-bp.png)
```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```
* **源**–现有的原点
* **方向**–手型方向
* **向上**–向上向量
* **方向**-方向四元数 
* **跟踪状态**-当前跟踪状态

### <a name="functions"></a>函数

所有函数都应该可在每个帧上调用，以便进行持续监视。 

![获取指针姿势信息](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
该函数返回有关此帧中的现货方向的完整信息。 

![是 Grasped 的最佳实践](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
如果在此帧中 grasped，则返回 true。 

![选择按下的 BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
如果用户在此帧中触发了 Select，则返回 true。

![按钮是否已单击 BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
如果在此帧中触发事件/按钮，则返回 true。

![获取控制器跟踪状态 BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
返回此帧中的跟踪状态。

## <a name="gestures"></a>笔势

Hololens 2 可以跟踪空间手势。 有关这些手势的详细信息，开发人员可以将它们捕获为其混合现实应用[程序的输入](https://docs.microsoft.com/hololens/hololens2-basic-usage)。 

C + + 函数位于 "WindowsMixedRealitySpatialInputFunctionLibrary" 中

蓝图函数位于 Windows Mixed Reality 空间输入中

![捕获手势](images/unreal/capture-gestures.png)

### <a name="enum"></a>枚举

![手势类型](images/unreal/gesture-type.png)
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```
此枚举描述空间轴笔势。 可在[此处](holograms-211.md)阅读相关信息

### <a name="function"></a>函数

![捕获手势最佳实践](images/unreal/capture-gestures-bp.png)
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```
函数启用和禁用对笔势的捕获。 启用的笔势会引发输入事件。 如果启用手势捕获成功，则返回 true; 如果出现错误，则返回 false。
关键事件

![关键事件](images/unreal/key-events.png)

![关键事件2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```
如果已启用该笔势，事件将开始激发。 

