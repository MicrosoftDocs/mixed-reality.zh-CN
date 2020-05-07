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
# <a name="hand-tracking"></a><span data-ttu-id="61d1b-104">手动跟踪</span><span class="sxs-lookup"><span data-stu-id="61d1b-104">Hand Tracking</span></span>

<span data-ttu-id="61d1b-105">手动跟踪系统使用用户的不要和手指作为 Unreal 的输入。</span><span class="sxs-lookup"><span data-stu-id="61d1b-105">The hand tracking system uses a person’s palms and fingers as input to Unreal.</span></span> <span data-ttu-id="61d1b-106">开发人员可以获得每个手指的位置和旋转、整个手掌，甚至是在自己的代码中使用的手势。</span><span class="sxs-lookup"><span data-stu-id="61d1b-106">A developer can get every finger’s position and rotation, the entire palm, and even hand gestures to use in their own code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="61d1b-107">举手</span><span class="sxs-lookup"><span data-stu-id="61d1b-107">Hand Pose</span></span>

<span data-ttu-id="61d1b-108">使用举手，开发人员可以将活动用户的手和手指作为输入进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="61d1b-108">Using the hand pose, developers can track the hands and fingers of the active user as input.</span></span> <span data-ttu-id="61d1b-109">此系统通过蓝图和 c + + 公开。</span><span class="sxs-lookup"><span data-stu-id="61d1b-109">This system is exposed through both Blueprints and C++.</span></span> <span data-ttu-id="61d1b-110">技术详细信息位于对应的 WinRT 类[HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose)中。 "Unreal API" 以 Unreal 的坐标系统格式提供数据，而 "时钟周期" 与 Unreal 引擎同步。</span><span class="sxs-lookup"><span data-stu-id="61d1b-110">Technical details are in the corresponding WinRT class [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) This Unreal API provides the data in the format of Unreal’s coordinate system and ticks are synchronised with the Unreal Engine.</span></span>

### <a name="enum"></a><span data-ttu-id="61d1b-111">枚举</span><span class="sxs-lookup"><span data-stu-id="61d1b-111">Enum</span></span>

<span data-ttu-id="61d1b-112">EWMRHandKeypoint 介绍了手形的骨骼层次结构。</span><span class="sxs-lookup"><span data-stu-id="61d1b-112">EWMRHandKeypoint describes the Hand’s bone hierarchy.</span></span> 

<span data-ttu-id="61d1b-113">建立</span><span class="sxs-lookup"><span data-stu-id="61d1b-113">Blueprint:</span></span>

![手动 Keypoint 最佳实践](images/unreal/hand-keypoint-bp.png)
 
<span data-ttu-id="61d1b-115">C++：</span><span class="sxs-lookup"><span data-stu-id="61d1b-115">C++:</span></span>
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

<span data-ttu-id="61d1b-117">可以在[HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)表中找到这些数值。</span><span class="sxs-lookup"><span data-stu-id="61d1b-117">The numerical values can be found in the table [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span></span>
 
### <a name="functions"></a><span data-ttu-id="61d1b-118">函数</span><span class="sxs-lookup"><span data-stu-id="61d1b-118">Functions</span></span>

<span data-ttu-id="61d1b-119">若要在蓝图中使用手跟踪功能，请打开 "手跟踪/Windows Mixed Reality"</span><span class="sxs-lookup"><span data-stu-id="61d1b-119">To use hand tracking functions in Blueprints, open "Hand Tracking/Windows Mixed Reality"</span></span>

![手动跟踪最佳实践](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="61d1b-121">对于 c + + 函数，包括 "WindowsMixedRealityHandTrackingFunctionLibrary"</span><span class="sxs-lookup"><span data-stu-id="61d1b-121">For C++ functions, include "WindowsMixedRealityHandTrackingFunctionLibrary.h"</span></span>

<span data-ttu-id="61d1b-122">最佳</span><span class="sxs-lookup"><span data-stu-id="61d1b-122">BP:</span></span>

![支持手动跟踪最佳实践](images/unreal/supports-hand-tracking-bp.png)
 
<span data-ttu-id="61d1b-124">C++：</span><span class="sxs-lookup"><span data-stu-id="61d1b-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

<span data-ttu-id="61d1b-125">如果设备支持手动跟踪，则返回 true; 如果没有手写跟踪，则返回 false。</span><span class="sxs-lookup"><span data-stu-id="61d1b-125">Returns true if hand tracking is supported on the device, false if hand tracking is not available.</span></span>

<span data-ttu-id="61d1b-126">最佳</span><span class="sxs-lookup"><span data-stu-id="61d1b-126">BP:</span></span>

![获取手动联合转换](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="61d1b-128">C++：</span><span class="sxs-lookup"><span data-stu-id="61d1b-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="61d1b-129">此函数返回手型的空间数据。</span><span class="sxs-lookup"><span data-stu-id="61d1b-129">This function returns spatial data of the hand.</span></span> <span data-ttu-id="61d1b-130">数据将更新框架中的每个帧，返回的值将被缓存。</span><span class="sxs-lookup"><span data-stu-id="61d1b-130">The data updates every frame, inside a frame the returned values are cached.</span></span> <span data-ttu-id="61d1b-131">出于性能方面的考虑，不建议在此函数上使用繁重的逻辑。</span><span class="sxs-lookup"><span data-stu-id="61d1b-131">It is not recommended to have heavy logic on this function for performance reasons.</span></span> 

* <span data-ttu-id="61d1b-132">用户**的手边，** 可以是左侧或右侧</span><span class="sxs-lookup"><span data-stu-id="61d1b-132">**Hand** – hand of the user, may be left or right</span></span>
* <span data-ttu-id="61d1b-133">**Keypoint** –手型的骨骼。</span><span class="sxs-lookup"><span data-stu-id="61d1b-133">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="61d1b-134">**转换**–骨骼基的坐标和方向。</span><span class="sxs-lookup"><span data-stu-id="61d1b-134">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="61d1b-135">若要获取骨骼末尾的转换数据，应请求下一个骨骼的基。</span><span class="sxs-lookup"><span data-stu-id="61d1b-135">To get the transform data for the end of a bone, the base of the next bone should be requested.</span></span> <span data-ttu-id="61d1b-136">特殊的 Tip 骨骼提供 distal 的结尾。</span><span class="sxs-lookup"><span data-stu-id="61d1b-136">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="61d1b-137">**半径**-骨骼基的半径。</span><span class="sxs-lookup"><span data-stu-id="61d1b-137">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="61d1b-138">**返回值**-如果在此帧中跟踪了骨骼，则为 true; 如果未跟踪骨骼，则为 false。</span><span class="sxs-lookup"><span data-stu-id="61d1b-138">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="61d1b-139">手动实时链接动画</span><span class="sxs-lookup"><span data-stu-id="61d1b-139">Hand Live Link Animation</span></span>
<span data-ttu-id="61d1b-140">使用实时链接插件向动画显示手姿势。</span><span class="sxs-lookup"><span data-stu-id="61d1b-140">Hand poses are exposed to Animation using the Live Link plugin.</span></span> <span data-ttu-id="61d1b-141">[此处](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)提供了插件文档</span><span class="sxs-lookup"><span data-stu-id="61d1b-141">The plugin documentation is [here](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span></span>

<span data-ttu-id="61d1b-142">如果启用了 Windows Mixed Reality 和 Live Link 插件，请跳到**Window > Live link**打开 "实时链接编辑器" 窗口。</span><span class="sxs-lookup"><span data-stu-id="61d1b-142">If the Windows Mixed Reality and Live Link plugins are enabled, go to **Window > Live Link** to open the Live Link editor window.</span></span> <span data-ttu-id="61d1b-143">单击 " **+ 源" 按钮**并启用 Windows Mixed Reality 手动跟踪源</span><span class="sxs-lookup"><span data-stu-id="61d1b-143">Click the **+ Source button** and enable Windows Mixed Reality Hand Tracking Source</span></span>

![实时链接源](images/unreal/live-link-source.png)
 
<span data-ttu-id="61d1b-145">启用源并打开任何动画资产后，动画的 "预览场景" 选项卡将具有以下附加选项（详细信息位于 Unreal 的实时链接文档中，因为插件已在 beta 中，此过程稍后可能会更改）</span><span class="sxs-lookup"><span data-stu-id="61d1b-145">After you enable the source and open any animation asset, the Preview Scene tab of Animation will have the following additional options (the details are in Unreal’s Live Link documentation- as the plugin is in beta, the process may change later)</span></span>

![实时链接动画](images/unreal/live-link-animation.png)
 
<span data-ttu-id="61d1b-147">手型动画层次结构与在 EWMRHandKeypoint 中的层次结构相同。</span><span class="sxs-lookup"><span data-stu-id="61d1b-147">The hand animation hierarchy is the same as in EWMRHandKeypoint.</span></span> <span data-ttu-id="61d1b-148">可以使用 WindowsMixedRealityHandTrackingLiveLinkRemapAsset 重定向动画。</span><span class="sxs-lookup"><span data-stu-id="61d1b-148">Animation can be retargeted using WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span></span> 

![实时链接动画2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="61d1b-150">它可以在编辑器中进行子类化</span><span class="sxs-lookup"><span data-stu-id="61d1b-150">It can be subclassed in the editor</span></span>

![实时链接重新映射](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a><span data-ttu-id="61d1b-152">手写网格</span><span class="sxs-lookup"><span data-stu-id="61d1b-152">Hand Mesh</span></span>
<span data-ttu-id="61d1b-153">表示用户指针的网格。</span><span class="sxs-lookup"><span data-stu-id="61d1b-153">Mesh representing the user hands.</span></span> 

![手写网格](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a><span data-ttu-id="61d1b-155">如何启用和配置</span><span class="sxs-lookup"><span data-stu-id="61d1b-155">How to enable and configure</span></span>

<span data-ttu-id="61d1b-156">开发人员可以直接访问手动网格，以实现自己的目的。</span><span class="sxs-lookup"><span data-stu-id="61d1b-156">Developers can get direct access to hand meshes for their own purposes.</span></span> <span data-ttu-id="61d1b-157">必须在 ARSessionConfig 中启用此访问： AR 设置-> 世界映射-> 从跟踪的几何图形生成网格数据。</span><span class="sxs-lookup"><span data-stu-id="61d1b-157">This access must be enabled in ARSessionConfig: AR Settings -> World Mapping -> Generate Mesh Data from Tracked Geometry.</span></span> 

<span data-ttu-id="61d1b-158">下面是网格的默认参数：</span><span class="sxs-lookup"><span data-stu-id="61d1b-158">Here are the default parameters for meshes:</span></span>

1.  <span data-ttu-id="61d1b-159">将网格数据用于封闭</span><span class="sxs-lookup"><span data-stu-id="61d1b-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="61d1b-160">为网格数据生成冲突</span><span class="sxs-lookup"><span data-stu-id="61d1b-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="61d1b-161">为网格数据生成导航网格</span><span class="sxs-lookup"><span data-stu-id="61d1b-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="61d1b-162">以线框–用于显示生成的网格的 debug 参数呈现网格数据</span><span class="sxs-lookup"><span data-stu-id="61d1b-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="61d1b-163">对于混合现实项目，这些参数值将用作空间映射网格和手写网格默认值。</span><span class="sxs-lookup"><span data-stu-id="61d1b-163">For mixed reality projects, these parameter values will be used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="61d1b-164">开发人员可以在任何特定网格的 BP 或代码中更改它们。</span><span class="sxs-lookup"><span data-stu-id="61d1b-164">Developers can change them in BP or code for any particular mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="61d1b-165">C + + API 参考</span><span class="sxs-lookup"><span data-stu-id="61d1b-165">C++ API Reference</span></span> 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

<span data-ttu-id="61d1b-166">此值是所有以可跟踪对象中的手写网格。</span><span class="sxs-lookup"><span data-stu-id="61d1b-166">This value is the hand mesh among all trackable objects.</span></span>

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

<span data-ttu-id="61d1b-167">当系统检测到任何以可跟踪对象（包括手写网格）时，将调用这些委托。</span><span class="sxs-lookup"><span data-stu-id="61d1b-167">These delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
<span data-ttu-id="61d1b-168">委托的处理程序应具有以下签名：</span><span class="sxs-lookup"><span data-stu-id="61d1b-168">Handlers to the delegates should have the following signature:</span></span>
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

<span data-ttu-id="61d1b-169">可以通过访问网格数据`UARTrackedGeometry::GetUnderlyingMesh`</span><span class="sxs-lookup"><span data-stu-id="61d1b-169">Mesh data can be accessed by `UARTrackedGeometry::GetUnderlyingMesh`</span></span>

### <a name="blueprint-api-reference"></a><span data-ttu-id="61d1b-170">蓝图 API 参考</span><span class="sxs-lookup"><span data-stu-id="61d1b-170">Blueprint API Reference</span></span>

<span data-ttu-id="61d1b-171">开发人员应将 AR 以可跟踪通知组件添加到蓝图参与者</span><span class="sxs-lookup"><span data-stu-id="61d1b-171">Developers should add an AR Trackable Notify Component to a Blueprint actor</span></span>

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
<span data-ttu-id="61d1b-173">然后，请前往组件的详细信息</span><span class="sxs-lookup"><span data-stu-id="61d1b-173">Then go to the component’s details</span></span> 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
<span data-ttu-id="61d1b-175">并在添加/更新/删除跟踪的几何图形上覆盖，代码如下所示：</span><span class="sxs-lookup"><span data-stu-id="61d1b-175">And overwrite On Add/Update/Remove Tracked Geometry with code like the below:</span></span>

![在 ARTrackable 通知上](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="61d1b-177">手写光线</span><span class="sxs-lookup"><span data-stu-id="61d1b-177">Hand Rays</span></span>

<span data-ttu-id="61d1b-178">开发人员可以使用手型作为指针设备。</span><span class="sxs-lookup"><span data-stu-id="61d1b-178">Developers can use a hand ray as a pointing device.</span></span> <span data-ttu-id="61d1b-179">系统可在 c + + 和蓝图中使用。</span><span class="sxs-lookup"><span data-stu-id="61d1b-179">The system is available in C++ and Blueprint.</span></span> <span data-ttu-id="61d1b-180">从技术上说，它公开了[SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span><span class="sxs-lookup"><span data-stu-id="61d1b-180">Technically it exposes [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span></span>

<span data-ttu-id="61d1b-181">必须指出的是，由于所有函数的结果都更改每个帧，因此它们都是可调用的。</span><span class="sxs-lookup"><span data-stu-id="61d1b-181">It’s important to mention that since the results of all the functions changes every frame, they are all made callable.</span></span> <span data-ttu-id="61d1b-182">有关纯 vs 非纯或可调用函数的详细信息，请参阅[。](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span><span class="sxs-lookup"><span data-stu-id="61d1b-182">For more information about pure vs impure or callable functions, see [that](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="61d1b-183">对于蓝图，打开 "Windows Mixed Reality HMD"</span><span class="sxs-lookup"><span data-stu-id="61d1b-183">For Blueprint open “Windows Mixed Reality HMD”</span></span>

![手动射线最佳实践](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="61d1b-185">C + + 包含 "WindowsMixedRealityFunctionLibrary"</span><span class="sxs-lookup"><span data-stu-id="61d1b-185">For C++ include "WindowsMixedRealityFunctionLibrary.h"</span></span>

### <a name="enum"></a><span data-ttu-id="61d1b-186">枚举</span><span class="sxs-lookup"><span data-stu-id="61d1b-186">Enum</span></span>

![输入控制器按钮](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* <span data-ttu-id="61d1b-188">**Select** --用户触发的 select 事件，可通过 airtap 或 "注视并提交" 在 HoloLens 2 中触发。</span><span class="sxs-lookup"><span data-stu-id="61d1b-188">**Select** -– User triggered Select event, which can be triggered in HoloLens 2 by airtap or gaze and commit.</span></span> <span data-ttu-id="61d1b-189">触发此事件的另一种方法是说 "Select"。</span><span class="sxs-lookup"><span data-stu-id="61d1b-189">Another way to trigger this event is to say “Select”.</span></span> 
* <span data-ttu-id="61d1b-190">**抓住**–用户触发的抓住事件，该事件在 HoloLens 2 中通过将用户的手指关闭到全息图上触发。</span><span class="sxs-lookup"><span data-stu-id="61d1b-190">**Grasp** -– User triggered Grasp event, which is triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* <span data-ttu-id="61d1b-191">**NotTracked** –手写不可见</span><span class="sxs-lookup"><span data-stu-id="61d1b-191">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="61d1b-192">**跟踪**–完全跟踪</span><span class="sxs-lookup"><span data-stu-id="61d1b-192">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="61d1b-193">结构</span><span class="sxs-lookup"><span data-stu-id="61d1b-193">Struct</span></span>

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
* <span data-ttu-id="61d1b-195">**源**–现有的原点</span><span class="sxs-lookup"><span data-stu-id="61d1b-195">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="61d1b-196">**方向**–手型方向</span><span class="sxs-lookup"><span data-stu-id="61d1b-196">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="61d1b-197">**向上**–向上向量</span><span class="sxs-lookup"><span data-stu-id="61d1b-197">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="61d1b-198">**方向**-方向四元数</span><span class="sxs-lookup"><span data-stu-id="61d1b-198">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="61d1b-199">**跟踪状态**-当前跟踪状态</span><span class="sxs-lookup"><span data-stu-id="61d1b-199">**Tracking Status** – current tracking status</span></span>

### <a name="functions"></a><span data-ttu-id="61d1b-200">函数</span><span class="sxs-lookup"><span data-stu-id="61d1b-200">Functions</span></span>

<span data-ttu-id="61d1b-201">所有函数都应该可在每个帧上调用，以便进行持续监视。</span><span class="sxs-lookup"><span data-stu-id="61d1b-201">All the functions should be callable on every frame for continuous monitoring.</span></span> 

![获取指针姿势信息](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
<span data-ttu-id="61d1b-203">该函数返回有关此帧中的现货方向的完整信息。</span><span class="sxs-lookup"><span data-stu-id="61d1b-203">The function returns the full information about the hand ray direction in this frame.</span></span> 

![是 Grasped 的最佳实践](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
<span data-ttu-id="61d1b-205">如果在此帧中 grasped，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="61d1b-205">Returns true if the hand is grasped in this frame.</span></span> 

![选择按下的 BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
<span data-ttu-id="61d1b-207">如果用户在此帧中触发了 Select，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="61d1b-207">Returns true if the user triggered Select in this frame.</span></span>

![按钮是否已单击 BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
<span data-ttu-id="61d1b-209">如果在此帧中触发事件/按钮，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="61d1b-209">Returns true if the event/button is triggered in this frame.</span></span>

![获取控制器跟踪状态 BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
<span data-ttu-id="61d1b-211">返回此帧中的跟踪状态。</span><span class="sxs-lookup"><span data-stu-id="61d1b-211">Returns the tracking status in this frame.</span></span>

## <a name="gestures"></a><span data-ttu-id="61d1b-212">笔势</span><span class="sxs-lookup"><span data-stu-id="61d1b-212">Gestures</span></span>

<span data-ttu-id="61d1b-213">Hololens 2 可以跟踪空间手势。</span><span class="sxs-lookup"><span data-stu-id="61d1b-213">The Hololens 2 can track spatial gestures.</span></span> <span data-ttu-id="61d1b-214">有关这些手势的详细信息，开发人员可以将它们捕获为其混合现实应用[程序的输入](https://docs.microsoft.com/hololens/hololens2-basic-usage)。</span><span class="sxs-lookup"><span data-stu-id="61d1b-214">Details about these gestures are [here](https://docs.microsoft.com/hololens/hololens2-basic-usage) A developer can capture them as input to their mixed reality application.</span></span> 

<span data-ttu-id="61d1b-215">C + + 函数位于 "WindowsMixedRealitySpatialInputFunctionLibrary" 中</span><span class="sxs-lookup"><span data-stu-id="61d1b-215">The C++ function is in "WindowsMixedRealitySpatialInputFunctionLibrary.h"</span></span>

<span data-ttu-id="61d1b-216">蓝图函数位于 Windows Mixed Reality 空间输入中</span><span class="sxs-lookup"><span data-stu-id="61d1b-216">The Blueprint function is in Windows Mixed Reality Spatial Input</span></span>

![捕获手势](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="61d1b-218">枚举</span><span class="sxs-lookup"><span data-stu-id="61d1b-218">Enum</span></span>

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
<span data-ttu-id="61d1b-220">此枚举描述空间轴笔势。</span><span class="sxs-lookup"><span data-stu-id="61d1b-220">This enum describes spatial axis gestures.</span></span> <span data-ttu-id="61d1b-221">可在[此处](holograms-211.md)阅读相关信息</span><span class="sxs-lookup"><span data-stu-id="61d1b-221">You can read about them [here](holograms-211.md)</span></span>

### <a name="function"></a><span data-ttu-id="61d1b-222">函数</span><span class="sxs-lookup"><span data-stu-id="61d1b-222">Function</span></span>

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
<span data-ttu-id="61d1b-224">函数启用和禁用对笔势的捕获。</span><span class="sxs-lookup"><span data-stu-id="61d1b-224">The function enables and disables capturing of gestures.</span></span> <span data-ttu-id="61d1b-225">启用的笔势会引发输入事件。</span><span class="sxs-lookup"><span data-stu-id="61d1b-225">The enabled gestures fire input events.</span></span> <span data-ttu-id="61d1b-226">如果启用手势捕获成功，则返回 true; 如果出现错误，则返回 false。</span><span class="sxs-lookup"><span data-stu-id="61d1b-226">It returns true if enabling gesture capture succeeded and false if there's an error.</span></span>
<span data-ttu-id="61d1b-227">关键事件</span><span class="sxs-lookup"><span data-stu-id="61d1b-227">Key Events</span></span>

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
<span data-ttu-id="61d1b-230">如果已启用该笔势，事件将开始激发。</span><span class="sxs-lookup"><span data-stu-id="61d1b-230">If the gesture is enabled, the events begin firing.</span></span> 

