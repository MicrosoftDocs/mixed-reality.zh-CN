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
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="6aac2-104">手势和 Unity 中的动作控制器</span><span class="sxs-lookup"><span data-stu-id="6aac2-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="6aac2-105">有两种主要方式，若要对其执行操作您[对此 Unity](gaze-in-unity.md)，[传递手势](gestures.md)并[动作控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="6aac2-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="6aac2-106">通过在 Unity 中相同的 Api 访问空间输入这两个源的数据。</span><span class="sxs-lookup"><span data-stu-id="6aac2-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="6aac2-107">Unity 提供了两种主要方式，若要访问的 Windows Mixed Reality，常见的输入的空间数据*Input.GetButton/Input.GetAxis*跨多个 Unity XR Sdk 工作的 Api 和*InteractionManager /GestureRecognizer* API 特定于 Windows Mixed Reality 公开完整的可用空间的输入数据集。</span><span class="sxs-lookup"><span data-stu-id="6aac2-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="6aac2-108">Unity 按钮/轴映射表</span><span class="sxs-lookup"><span data-stu-id="6aac2-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="6aac2-109">下表中的按钮和轴 Id 支持 Unity 的输入管理器中通过 Windows Mixed Reality 运动控制器*Input.GetButton/GetAxis* Api，而"特定于 Windows MR 的"列属性可用的中断*InteractionSourceState*类型。</span><span class="sxs-lookup"><span data-stu-id="6aac2-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="6aac2-110">以下各节中详细描述每个这些 Api。</span><span class="sxs-lookup"><span data-stu-id="6aac2-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="6aac2-111">Windows Mixed Reality 的按钮/轴 ID 映射通常与 Oculus 按钮/轴 Id 相匹配。</span><span class="sxs-lookup"><span data-stu-id="6aac2-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="6aac2-112">Windows Mixed Reality 的按钮/轴 ID 映射不同的两种方式 OpenVR 的映射：</span><span class="sxs-lookup"><span data-stu-id="6aac2-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="6aac2-113">映射使用触摸板 Id 进行不同于摇杆，以支持 thumbsticks 和触摸板的域控制器。</span><span class="sxs-lookup"><span data-stu-id="6aac2-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="6aac2-114">映射可避免重载菜单按钮的 Id，以保留这些适用于物理 ABXY 按钮中的 A 和 X 按钮。</span><span class="sxs-lookup"><span data-stu-id="6aac2-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="6aac2-115">Input</span><span class="sxs-lookup"><span data-stu-id="6aac2-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="6aac2-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">常见的 Unity Api</a></span><span class="sxs-lookup"><span data-stu-id="6aac2-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="6aac2-117">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="6aac2-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="6aac2-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">特定于 Windows MR 的输入的 API</a></span><span class="sxs-lookup"><span data-stu-id="6aac2-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="6aac2-119">(XR.WSA.Input)</span><span class="sxs-lookup"><span data-stu-id="6aac2-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="6aac2-120">左侧显示</span><span class="sxs-lookup"><span data-stu-id="6aac2-120">Left hand</span></span> </th><th> <span data-ttu-id="6aac2-121">右侧</span><span class="sxs-lookup"><span data-stu-id="6aac2-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="6aac2-122">选择按下的触发器</span><span class="sxs-lookup"><span data-stu-id="6aac2-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="6aac2-123">轴 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="6aac2-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="6aac2-124">轴 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="6aac2-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="6aac2-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="6aac2-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-126">选择触发器模拟值</span><span class="sxs-lookup"><span data-stu-id="6aac2-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="6aac2-127">轴 9</span><span class="sxs-lookup"><span data-stu-id="6aac2-127">Axis 9</span></span> </td><td> <span data-ttu-id="6aac2-128">轴 10</span><span class="sxs-lookup"><span data-stu-id="6aac2-128">Axis 10</span></span> </td><td> <span data-ttu-id="6aac2-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="6aac2-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-130">按下的部分选择触发器</span><span class="sxs-lookup"><span data-stu-id="6aac2-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="6aac2-131">按钮 14 <i>（游戏板兼容性）</i> </span><span class="sxs-lookup"><span data-stu-id="6aac2-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="6aac2-132">按钮 15 <i>（游戏板兼容性）</i> </span><span class="sxs-lookup"><span data-stu-id="6aac2-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="6aac2-133">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="6aac2-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-134">按下菜单按钮</span><span class="sxs-lookup"><span data-stu-id="6aac2-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="6aac2-135">按钮 6 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-135">Button 6\*</span></span> </td><td> <span data-ttu-id="6aac2-136">按钮 7 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-136">Button 7\*</span></span> </td><td> <span data-ttu-id="6aac2-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="6aac2-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-138">按下的手柄按钮</span><span class="sxs-lookup"><span data-stu-id="6aac2-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="6aac2-139">11 = 1.0 （未模拟值） 轴</span><span class="sxs-lookup"><span data-stu-id="6aac2-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="6aac2-140">按钮 4 <i>（游戏板兼容性）</i> </span><span class="sxs-lookup"><span data-stu-id="6aac2-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="6aac2-141">12 = 1.0 （未模拟值） 轴</span><span class="sxs-lookup"><span data-stu-id="6aac2-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="6aac2-142">按钮 5 <i>（游戏板兼容性）</i> </span><span class="sxs-lookup"><span data-stu-id="6aac2-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="6aac2-143">由于</span><span class="sxs-lookup"><span data-stu-id="6aac2-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-144">摇杆 X <i>(左:-1.0，正确：1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="6aac2-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="6aac2-145">轴 1</span><span class="sxs-lookup"><span data-stu-id="6aac2-145">Axis 1</span></span> </td><td> <span data-ttu-id="6aac2-146">轴 4</span><span class="sxs-lookup"><span data-stu-id="6aac2-146">Axis 4</span></span> </td><td> <span data-ttu-id="6aac2-147">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="6aac2-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-148">摇杆 Y <i>(顶部:-1.0，底部：1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="6aac2-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="6aac2-149">轴 2</span><span class="sxs-lookup"><span data-stu-id="6aac2-149">Axis 2</span></span> </td><td> <span data-ttu-id="6aac2-150">轴 5</span><span class="sxs-lookup"><span data-stu-id="6aac2-150">Axis 5</span></span> </td><td> <span data-ttu-id="6aac2-151">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="6aac2-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-152">按下的摇杆</span><span class="sxs-lookup"><span data-stu-id="6aac2-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="6aac2-153">按钮 8</span><span class="sxs-lookup"><span data-stu-id="6aac2-153">Button 8</span></span> </td><td> <span data-ttu-id="6aac2-154">按钮 9</span><span class="sxs-lookup"><span data-stu-id="6aac2-154">Button 9</span></span> </td><td> <span data-ttu-id="6aac2-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="6aac2-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-156">触摸板 X <i>(左:-1.0，正确：1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="6aac2-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="6aac2-157">轴 17 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="6aac2-158">轴 19 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="6aac2-159">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="6aac2-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-160">触摸板 Y <i>(顶部:-1.0，底部：1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="6aac2-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="6aac2-161">轴 18 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="6aac2-162">轴 20 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="6aac2-163">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="6aac2-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-164">触摸板接触</span><span class="sxs-lookup"><span data-stu-id="6aac2-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="6aac2-165">按钮 18 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-165">Button 18\*</span></span> </td><td> <span data-ttu-id="6aac2-166">按钮 19 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-166">Button 19\*</span></span> </td><td> <span data-ttu-id="6aac2-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="6aac2-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-168">按下触摸板</span><span class="sxs-lookup"><span data-stu-id="6aac2-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="6aac2-169">按钮 16 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-169">Button 16\*</span></span> </td><td> <span data-ttu-id="6aac2-170">按钮 17 \*</span><span class="sxs-lookup"><span data-stu-id="6aac2-170">Button 17\*</span></span> </td><td> <span data-ttu-id="6aac2-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="6aac2-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-172">6DoF 手柄姿势或指针姿势</span><span class="sxs-lookup"><span data-stu-id="6aac2-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="6aac2-173"><i>手柄</i>只会造成：<a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="6aac2-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="6aac2-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="6aac2-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="6aac2-175">传递<i>手柄</i>或<i>指针</i>作为参数： sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="6aac2-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="6aac2-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="6aac2-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-177">跟踪状态</span><span class="sxs-lookup"><span data-stu-id="6aac2-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="6aac2-178"><i>位置准确性和源丢失风险，仅可通过特定于 MR 的 API</i> </span><span class="sxs-lookup"><span data-stu-id="6aac2-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="6aac2-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="6aac2-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="6aac2-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="6aac2-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="6aac2-181">这些按钮/轴 Id 不同于用于由于游戏板，Oculus 触摸和 OpenVR 所使用的映射中的冲突而 OpenVR Unity 的 Id。</span><span class="sxs-lookup"><span data-stu-id="6aac2-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="6aac2-182">与指针姿势手柄姿势</span><span class="sxs-lookup"><span data-stu-id="6aac2-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="6aac2-183">Windows Mixed Reality 支持不同的外形规格运动控制器，使用每个控制器设计各不相同，"转发"方向该应用的自然用户的手位置之间的关系应为使用指向呈现时控制器。</span><span class="sxs-lookup"><span data-stu-id="6aac2-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="6aac2-184">若要更好地表示这些控制器，有两种类型的可以为每个交互源，调查的带来**手柄姿势**并**指针姿势**。</span><span class="sxs-lookup"><span data-stu-id="6aac2-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="6aac2-185">手柄姿势和指针姿势坐标来表示通过以全局 Unity 世界坐标表示的所有 Unity Api。</span><span class="sxs-lookup"><span data-stu-id="6aac2-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="6aac2-186">手柄姿势</span><span class="sxs-lookup"><span data-stu-id="6aac2-186">Grip pose</span></span>

<span data-ttu-id="6aac2-187">**手柄姿势**表示检测到的 HoloLens 手的形状的手掌或手掌持有运动控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="6aac2-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="6aac2-188">在沉浸式耳机手柄姿势最适合用于呈现**用户的手**或**对象保存在用户的手中**，例如双刃剑或手段。</span><span class="sxs-lookup"><span data-stu-id="6aac2-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="6aac2-189">作为可视化的运动控制器，也会使用手柄姿势**可呈现模型**提供由 Windows 动作控制器使用手柄姿势作为其起点和旋转中心。</span><span class="sxs-lookup"><span data-stu-id="6aac2-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="6aac2-190">手柄姿势定义具体而言，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6aac2-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="6aac2-191">**抓住位置**:Palm 质心时保存在控制器正常情况下，调整左侧或右侧居中手柄内的位置。</span><span class="sxs-lookup"><span data-stu-id="6aac2-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="6aac2-192">Windows Mixed Reality 动作在控制器上，此位置通常与掌握按钮对齐。</span><span class="sxs-lookup"><span data-stu-id="6aac2-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="6aac2-193">**抓住方向的右轴**:完全打开您的手以形成平面 5 手指姿势，ray 的时您的手掌接触到正常 （从左 palm，向右 palm 从后向前）</span><span class="sxs-lookup"><span data-stu-id="6aac2-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="6aac2-194">**抓住正轴方向的**:当您关闭您的手部分 （就像按控制器），"forward"通过管通过非 thumb 手指点与射线。</span><span class="sxs-lookup"><span data-stu-id="6aac2-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="6aac2-195">**抓住方向沿轴向上**:权限隐含的权限和转发定义最多轴。</span><span class="sxs-lookup"><span data-stu-id="6aac2-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="6aac2-196">您可以通过任一 Unity 跨供应商输入 API 访问手柄姿势 (*[XR。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation*) 或通过特定于 Windows MR 的 API (*sourceState.sourcePose.TryGetPosition/Rotation*，请求会带来数据**手柄**节点)。</span><span class="sxs-lookup"><span data-stu-id="6aac2-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="6aac2-197">指针姿势</span><span class="sxs-lookup"><span data-stu-id="6aac2-197">Pointer pose</span></span>

<span data-ttu-id="6aac2-198">**指针姿势**表示转发指向控制器的提示。</span><span class="sxs-lookup"><span data-stu-id="6aac2-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="6aac2-199">你是，到 raycast 最合适使用系统提供的指针姿势**呈现控制器模型本身**。</span><span class="sxs-lookup"><span data-stu-id="6aac2-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="6aac2-200">当您呈现某些其他虚拟对象代替控制器，例如虚拟手段，您应点与最自然会为该虚拟对象，如应用程序定义枪模型的笔杆都沿着一条射线。</span><span class="sxs-lookup"><span data-stu-id="6aac2-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="6aac2-201">由于用户可以看到虚拟对象，而不是物理的控制器，指向与虚拟对象可能会使那些使用您的应用程序更加自然。</span><span class="sxs-lookup"><span data-stu-id="6aac2-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="6aac2-202">目前，指针姿势现已推出只能通过特定于 Windows MR 的 API，Unity *sourceState.sourcePose.TryGetPosition/Rotation*，并传入*InteractionSourceNode.Pointer*为自变量。</span><span class="sxs-lookup"><span data-stu-id="6aac2-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="6aac2-203">控制器跟踪状态</span><span class="sxs-lookup"><span data-stu-id="6aac2-203">Controller tracking state</span></span>

<span data-ttu-id="6aac2-204">耳机，如 Windows Mixed Reality 运动控制器不需要外部跟踪传感器的任何设置。</span><span class="sxs-lookup"><span data-stu-id="6aac2-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="6aac2-205">相反，控制器会跟踪耳机本身中的传感器。</span><span class="sxs-lookup"><span data-stu-id="6aac2-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="6aac2-206">如果用户移出耳机的字段的视图控制器，在大多数情况下 Windows 会继续推断控制器位置并将它们提供给应用程序。</span><span class="sxs-lookup"><span data-stu-id="6aac2-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="6aac2-207">当控制器已失去时长不足，控制器的位置将会断开与近似准确性位置可视化跟踪。</span><span class="sxs-lookup"><span data-stu-id="6aac2-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="6aac2-208">此时，系统会将主体锁定的用户，跟踪用户的位置，随着对象移动，同时仍提供的控制器，则返回 true 方向使用其内部方向传感器到控制器。</span><span class="sxs-lookup"><span data-stu-id="6aac2-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="6aac2-209">使用控制器指向并激活用户界面元素的许多应用程序可以无需用户注意到正常运行中近似的准确性。</span><span class="sxs-lookup"><span data-stu-id="6aac2-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="6aac2-210">为此感到的最佳方式是亲自尝试一下。</span><span class="sxs-lookup"><span data-stu-id="6aac2-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="6aac2-211">请查看此视频中通过跨各种跟踪状态适用于运动控制器的沉浸式内容的示例：</span><span class="sxs-lookup"><span data-stu-id="6aac2-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="6aac2-212">有关显式跟踪状态的推论</span><span class="sxs-lookup"><span data-stu-id="6aac2-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="6aac2-213">想要将基于跟踪状态以不同方式的位置的应用程序可能会更进一步，如检查控制器的状态的属性*SourceLossRisk*并*PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="6aac2-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="6aac2-214">跟踪状态</span><span class="sxs-lookup"><span data-stu-id="6aac2-214">Tracking state</span></span> </th><th> <span data-ttu-id="6aac2-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="6aac2-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="6aac2-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="6aac2-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="6aac2-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="6aac2-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="6aac2-218"><b>高精度</b> </span><span class="sxs-lookup"><span data-stu-id="6aac2-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="6aac2-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="6aac2-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="6aac2-220">高</span><span class="sxs-lookup"><span data-stu-id="6aac2-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="6aac2-221">true</span><span class="sxs-lookup"><span data-stu-id="6aac2-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-222"><b>（在丢失的风险） 的高精度</b> </span><span class="sxs-lookup"><span data-stu-id="6aac2-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="6aac2-223">== 1.0</span><span class="sxs-lookup"><span data-stu-id="6aac2-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="6aac2-224">高</span><span class="sxs-lookup"><span data-stu-id="6aac2-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="6aac2-225">true</span><span class="sxs-lookup"><span data-stu-id="6aac2-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-226"><b>近似值的准确性</b> </span><span class="sxs-lookup"><span data-stu-id="6aac2-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="6aac2-227">== 1.0</span><span class="sxs-lookup"><span data-stu-id="6aac2-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="6aac2-228">近似</span><span class="sxs-lookup"><span data-stu-id="6aac2-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="6aac2-229">true</span><span class="sxs-lookup"><span data-stu-id="6aac2-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6aac2-230"><b>不到位置</b> </span><span class="sxs-lookup"><span data-stu-id="6aac2-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="6aac2-231">== 1.0</span><span class="sxs-lookup"><span data-stu-id="6aac2-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="6aac2-232">近似</span><span class="sxs-lookup"><span data-stu-id="6aac2-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="6aac2-233">false</span><span class="sxs-lookup"><span data-stu-id="6aac2-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="6aac2-234">这些动作控制器跟踪状态定义，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6aac2-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="6aac2-235">**高精度：** 在 motion 控制器耳机的字段的视图中时，它通常将提供高准确性位置，基于可视化跟踪。</span><span class="sxs-lookup"><span data-stu-id="6aac2-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="6aac2-236">请注意，移动控制器的暂时离开视图的字段或暂时不可用遮盖耳机传感器 (例如，用户的另一只手) 将继续返回高准确性带来基于控制器的惯性跟踪在短时间本身。</span><span class="sxs-lookup"><span data-stu-id="6aac2-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="6aac2-237">**（在丢失的风险） 的高精度：** 当用户移动的运动控制器超过耳机的视角的边缘时，耳机很快将无法直观地跟踪控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="6aac2-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="6aac2-238">应用已知道控制器当通过查看达到此 FOV 边界**SourceLossRisk**达到 1.0。</span><span class="sxs-lookup"><span data-stu-id="6aac2-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="6aac2-239">此时，应用程序可以选择暂停需要稳定的高质量带来的控制器手势。</span><span class="sxs-lookup"><span data-stu-id="6aac2-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="6aac2-240">**近似值的准确性：** 当控制器已失去时长不足，控制器的位置将会断开与近似准确性位置可视化跟踪。</span><span class="sxs-lookup"><span data-stu-id="6aac2-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="6aac2-241">此时，系统会将主体锁定的用户，跟踪用户的位置，随着对象移动，同时仍提供的控制器，则返回 true 方向使用其内部方向传感器到控制器。</span><span class="sxs-lookup"><span data-stu-id="6aac2-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="6aac2-242">控制器用于指向并激活用户界面元素的许多应用程序可以作为正常段中近似的准确性在运行而无需用户注意到。</span><span class="sxs-lookup"><span data-stu-id="6aac2-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="6aac2-243">具有较输入要求的应用可以选择感应从此下降**高**精度为**近似**准确性通过检查**PositionAccuracy**属性，用于可以向用户授予在允许较大 hitbox 屏外目标在此期间的示例。</span><span class="sxs-lookup"><span data-stu-id="6aac2-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="6aac2-244">**不到位置：** 控制器可以长时间运行近似值的准确性，而有时系统就知道目前没有意义甚至正文锁定的位置。</span><span class="sxs-lookup"><span data-stu-id="6aac2-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="6aac2-245">例如，只需开启控制器可能永远不会观察到以可视方式，或者用户可能放下一个控制器，然后选取其他人。</span><span class="sxs-lookup"><span data-stu-id="6aac2-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="6aac2-246">在这些情况下，系统将不会提供到应用程序中的任意位置并*TryGetPosition*将返回 false。</span><span class="sxs-lookup"><span data-stu-id="6aac2-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="6aac2-247">常见的 Unity Api (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="6aac2-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="6aac2-248">\**命名空间：\*\*\*UnityEngine*， *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="6aac2-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="6aac2-249">**类型**:*输入*， *XR。InputTracking*</span><span class="sxs-lookup"><span data-stu-id="6aac2-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="6aac2-250">Unity 当前使用其常规*Input.GetButton/Input.GetAxis* Api 来公开的输入[Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)， [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)和 Windows Mixed Reality 包括双手和动作控制器。</span><span class="sxs-lookup"><span data-stu-id="6aac2-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="6aac2-251">如果您的应用程序使用这些 Api 作为输入，它可以轻松地跨多个 XR Sdk，包括 Windows Mixed Reality 支持运动控制器。</span><span class="sxs-lookup"><span data-stu-id="6aac2-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="6aac2-252">获取逻辑按钮的按下的状态</span><span class="sxs-lookup"><span data-stu-id="6aac2-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="6aac2-253">若要使用的常规 Unity 输入 Api，则通常先接通按钮和轴中的逻辑名称[Unity 输入管理器](https://docs.unity3d.com/Manual/ConventionalGameInput.html)，绑定到每个名称的按钮或轴 Id。</span><span class="sxs-lookup"><span data-stu-id="6aac2-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="6aac2-254">然后可以编写该逻辑的按钮轴名称引用的代码。</span><span class="sxs-lookup"><span data-stu-id="6aac2-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="6aac2-255">例如，若要将左的运动控制器的触发器按钮映射到提交操作，请访问**编辑 > 项目设置 > 输入**在 Unity 中，展开提交部分下轴的属性。</span><span class="sxs-lookup"><span data-stu-id="6aac2-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="6aac2-256">更改**表扬按钮**或**Alt 正按钮**属性以读取**游戏杆按钮 14**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6aac2-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="6aac2-257">![Unity 的 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="6aac2-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="6aac2-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="6aac2-258">*Unity InputManager*</span></span>

<span data-ttu-id="6aac2-259">然后，您的脚本可以检查提交操作使用*Input.GetButton*:</span><span class="sxs-lookup"><span data-stu-id="6aac2-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="6aac2-260">您可以通过更改添加更多逻辑按钮**大小**下的属性**轴**。</span><span class="sxs-lookup"><span data-stu-id="6aac2-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="6aac2-261">直接获取的物理按钮按下的状态</span><span class="sxs-lookup"><span data-stu-id="6aac2-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="6aac2-262">您还可以访问按钮手动通过其完全限定名称，使用*Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="6aac2-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="6aac2-263">获取手形或运动控制器姿势</span><span class="sxs-lookup"><span data-stu-id="6aac2-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="6aac2-264">您可以访问的位置和旋转的控制器，使用*XR。InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="6aac2-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="6aac2-265">请注意，这表示控制器的手柄姿势 （其中的用户都包含在控制器），可用于呈现双刃剑或用户的手或控制器本身的模型中的手段。</span><span class="sxs-lookup"><span data-stu-id="6aac2-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="6aac2-266">请注意此手柄姿势和指针姿势 （其中指向控制器的提示） 之间的关系可能会因控制器。</span><span class="sxs-lookup"><span data-stu-id="6aac2-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="6aac2-267">此时，访问控制器的指针姿势才可通过特定于 MR 的输入 API，在以下各节所述。</span><span class="sxs-lookup"><span data-stu-id="6aac2-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="6aac2-268">特定于 Windows 的 Api (XR。WSA。输入）</span><span class="sxs-lookup"><span data-stu-id="6aac2-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="6aac2-269">\**命名空间：\*\*\*UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="6aac2-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="6aac2-270">**类型**:*InteractionManager*， *InteractionSourceState*， *InteractionSource*， *InteractionSourceProperties*， *InteractionSourceKind*， *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="6aac2-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="6aac2-271">若要获取更多详细信息 （对于 HoloLens) 的 Windows Mixed Reality 手动输入和动作控制器，你可以选择使用特定于 Windows 的空间输入的 Api 下*UnityEngine.XR.WSA.Input*命名空间。</span><span class="sxs-lookup"><span data-stu-id="6aac2-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="6aac2-272">这允许您访问其他信息，如位置准确性或源类型，让您告诉双手和控制器分离。</span><span class="sxs-lookup"><span data-stu-id="6aac2-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="6aac2-273">轮询双手和动作控制器的状态</span><span class="sxs-lookup"><span data-stu-id="6aac2-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="6aac2-274">可以针对每个交互源 （手动或动画控制器） 使用此帧状态轮询*GetCurrentReading*方法。</span><span class="sxs-lookup"><span data-stu-id="6aac2-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="6aac2-275">每个*InteractionSourceState*您获取在当前时刻后表示交互源。</span><span class="sxs-lookup"><span data-stu-id="6aac2-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="6aac2-276">*InteractionSourceState*如公开信息：</span><span class="sxs-lookup"><span data-stu-id="6aac2-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="6aac2-277">这[类型的按下](motion-controllers.md)发生 （选择/菜单/掌握/触摸板/摇杆）</span><span class="sxs-lookup"><span data-stu-id="6aac2-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="6aac2-278">其他特定于运动控制器，此类的触摸板和/或摇杆的 XY 坐标和接触的状态的数据</span><span class="sxs-lookup"><span data-stu-id="6aac2-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="6aac2-279">若要了解是否源是手的形状或运动控制器 InteractionSourceKind</span><span class="sxs-lookup"><span data-stu-id="6aac2-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="6aac2-280">正向预测呈现带来轮询</span><span class="sxs-lookup"><span data-stu-id="6aac2-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="6aac2-281">轮询以查找从手和控制器交互源数据，您获取的带来时，正向预测带来的时刻，当此帧 photons 将到达用户的眼球。</span><span class="sxs-lookup"><span data-stu-id="6aac2-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="6aac2-282">这些正向预测带来最适合用于**呈现**控制器或保持对象的每个帧。</span><span class="sxs-lookup"><span data-stu-id="6aac2-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="6aac2-283">如果你是针对给定的按还是发布与控制器，将获得更加准确，如果您使用历史事件如下所述的 Api。</span><span class="sxs-lookup"><span data-stu-id="6aac2-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="6aac2-284">此外可以获取此当前帧的正向预测头部姿势。</span><span class="sxs-lookup"><span data-stu-id="6aac2-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="6aac2-285">由于与源姿势，这是用于**呈现**一个游标，但以给定的按或发布目标将是最准确，如果您使用历史事件如下所述的 Api。</span><span class="sxs-lookup"><span data-stu-id="6aac2-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="6aac2-286">处理交互源事件</span><span class="sxs-lookup"><span data-stu-id="6aac2-286">Handling interaction source events</span></span>

<span data-ttu-id="6aac2-287">若要使用其准确历史姿势数据发生时处理输入的事件，可以处理交互源事件，而不是轮询。</span><span class="sxs-lookup"><span data-stu-id="6aac2-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="6aac2-288">若要处理的交互的源事件：</span><span class="sxs-lookup"><span data-stu-id="6aac2-288">To handle interaction source events:</span></span>
* <span data-ttu-id="6aac2-289">注册，以便*InteractionManager*输入的事件。</span><span class="sxs-lookup"><span data-stu-id="6aac2-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="6aac2-290">对于每个类型的交互事件感兴趣，您需要订阅它。</span><span class="sxs-lookup"><span data-stu-id="6aac2-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="6aac2-291">处理的事件。</span><span class="sxs-lookup"><span data-stu-id="6aac2-291">Handle the event.</span></span> <span data-ttu-id="6aac2-292">一旦您订阅的交互事件，你将收到回调在适当的时候。</span><span class="sxs-lookup"><span data-stu-id="6aac2-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="6aac2-293">在中*SourcePressed*示例中，这将是检测到源后，在发布或丢失之前。</span><span class="sxs-lookup"><span data-stu-id="6aac2-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="6aac2-294">如何停止处理的事件</span><span class="sxs-lookup"><span data-stu-id="6aac2-294">How to stop handling an event</span></span>

<span data-ttu-id="6aac2-295">需要停止时您将不再对感兴趣事件或确实要销毁已订阅该事件的对象处理事件。</span><span class="sxs-lookup"><span data-stu-id="6aac2-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="6aac2-296">若要停止处理事件，您随时取消订阅事件。</span><span class="sxs-lookup"><span data-stu-id="6aac2-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="6aac2-297">交互源事件的列表</span><span class="sxs-lookup"><span data-stu-id="6aac2-297">List of interaction source events</span></span>

<span data-ttu-id="6aac2-298">可进行的交互源事件是：</span><span class="sxs-lookup"><span data-stu-id="6aac2-298">The available interaction source events are:</span></span>
* <span data-ttu-id="6aac2-299">*InteractionSourceDetected* （源变为活动状态）</span><span class="sxs-lookup"><span data-stu-id="6aac2-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="6aac2-300">*InteractionSourceLost* （变为非活动状态）</span><span class="sxs-lookup"><span data-stu-id="6aac2-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="6aac2-301">*InteractionSourcePressed* （点击、 按下按钮，或"选择"失措）</span><span class="sxs-lookup"><span data-stu-id="6aac2-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="6aac2-302">*InteractionSourceReleased* （点击、 释放或"Select"失措末尾的结尾）</span><span class="sxs-lookup"><span data-stu-id="6aac2-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="6aac2-303">*InteractionSourceUpdated* （移动或更改某些状态）</span><span class="sxs-lookup"><span data-stu-id="6aac2-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="6aac2-304">最能准确匹配按或发布的历史记录目标带来的事件</span><span class="sxs-lookup"><span data-stu-id="6aac2-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="6aac2-305">前面所述的轮询 Api 提供您的应用程序正向预测带来。</span><span class="sxs-lookup"><span data-stu-id="6aac2-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="6aac2-306">虽然这些预测的带来最适合于呈现的控制器或虚拟的手持对象，未来带来不适合面向两个主要原因：</span><span class="sxs-lookup"><span data-stu-id="6aac2-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="6aac2-307">当用户按下控制器上的按钮时，可以有大约 20 毫秒的无线延迟通过蓝牙之前系统收到按下了。</span><span class="sxs-lookup"><span data-stu-id="6aac2-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="6aac2-308">然后，如果您使用的正向预测姿势存在将另一个 10-20 毫秒的正向预测应用以面向当前帧的 photons 时将到达用户的眼球的时间。</span><span class="sxs-lookup"><span data-stu-id="6aac2-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="6aac2-309">这意味着轮询为您提供了源姿势或头部姿势从其中用户的 head 和手实际上是按或发布完成的操作时，它是 30 40ms年进。</span><span class="sxs-lookup"><span data-stu-id="6aac2-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="6aac2-310">对于 HoloLens 手动输入，而没有任何无线传输延迟，没有类似的处理延迟，以检测按下了。</span><span class="sxs-lookup"><span data-stu-id="6aac2-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="6aac2-311">准确地基于用户的原始意图的手形或控制器按下的目标，应使用的历史源姿势或从该头部姿势*InteractionSourcePressed*或*InteractionSourceReleased*输入的事件。</span><span class="sxs-lookup"><span data-stu-id="6aac2-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="6aac2-312">可以针对按下的某个或发布与来自用户的头或其控制器的历史姿势数据：</span><span class="sxs-lookup"><span data-stu-id="6aac2-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="6aac2-313">头部姿势手势或控制器在按下时的时间时刻发生，可以使用该**面向**来确定用户已[观望](gaze.md)处：</span><span class="sxs-lookup"><span data-stu-id="6aac2-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

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

* <span data-ttu-id="6aac2-314">在 motion 控制器在按下时的时刻源姿势发生，可以使用该**面向**来确定哪些用户指向位于控制器。</span><span class="sxs-lookup"><span data-stu-id="6aac2-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="6aac2-315">这将是遇到按下了控制器的状态。</span><span class="sxs-lookup"><span data-stu-id="6aac2-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="6aac2-316">如果呈现控制器本身，则可以请求指针姿势而不是以投篮机会控制在从用户将考虑的内容的呈现控制器的自然提示的目标射线手柄姿势：</span><span class="sxs-lookup"><span data-stu-id="6aac2-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="6aac2-317">事件处理程序示例</span><span class="sxs-lookup"><span data-stu-id="6aac2-317">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="6aac2-318">高级复合手势 Api (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="6aac2-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="6aac2-319">\**命名空间：\*\*\*UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="6aac2-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="6aac2-320">**类型**:*GestureRecognizer*， *GestureSettings*， *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="6aac2-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="6aac2-321">您的应用程序还可以识别空间输入的源，Tap 中，保持状态、 操作和导航笔势的更高级别的复合操作。</span><span class="sxs-lookup"><span data-stu-id="6aac2-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="6aac2-322">您可以在两者之间识别这些复合笔势[手](gestures.md)并[动作控制器](motion-controllers.md)使用 GestureRecognizer。</span><span class="sxs-lookup"><span data-stu-id="6aac2-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="6aac2-323">GestureRecognizer 上的每个手势事件提供事件的时间在输入以及目标头 ray SourceKind。</span><span class="sxs-lookup"><span data-stu-id="6aac2-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="6aac2-324">一些事件提供附加上下文特定信息。</span><span class="sxs-lookup"><span data-stu-id="6aac2-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="6aac2-325">有仅几个步骤所需捕获使用笔势识别器手势：</span><span class="sxs-lookup"><span data-stu-id="6aac2-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="6aac2-326">创建新的笔势识别器</span><span class="sxs-lookup"><span data-stu-id="6aac2-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="6aac2-327">指定要监视的手势</span><span class="sxs-lookup"><span data-stu-id="6aac2-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="6aac2-328">订阅的这些手势事件</span><span class="sxs-lookup"><span data-stu-id="6aac2-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="6aac2-329">开始捕获手势</span><span class="sxs-lookup"><span data-stu-id="6aac2-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="6aac2-330">创建新的笔势识别器</span><span class="sxs-lookup"><span data-stu-id="6aac2-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="6aac2-331">若要使用*GestureRecognizer*，您必须创建*GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="6aac2-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="6aac2-332">指定要监视的手势</span><span class="sxs-lookup"><span data-stu-id="6aac2-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="6aac2-333">指定你感兴趣通过这些手势*SetRecognizableGestures()*:</span><span class="sxs-lookup"><span data-stu-id="6aac2-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="6aac2-334">订阅的这些手势事件</span><span class="sxs-lookup"><span data-stu-id="6aac2-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="6aac2-335">订阅的事件感兴趣的笔势。</span><span class="sxs-lookup"><span data-stu-id="6aac2-335">Subscribe to events for the gestures you are interested in.</span></span>

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
><span data-ttu-id="6aac2-336">导航和操作手势是互斥的实例上*GestureRecognizer*。</span><span class="sxs-lookup"><span data-stu-id="6aac2-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="6aac2-337">开始捕获手势</span><span class="sxs-lookup"><span data-stu-id="6aac2-337">Start capturing gestures</span></span>

<span data-ttu-id="6aac2-338">默认情况下*GestureRecognizer*不会监视输入直到*StartCapturingGestures()* 调用。</span><span class="sxs-lookup"><span data-stu-id="6aac2-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="6aac2-339">可能的手势事件可能会生成后*StopCapturingGestures()* 如果输入之前在帧已执行，则调用其中*StopCapturingGestures()* 已处理。</span><span class="sxs-lookup"><span data-stu-id="6aac2-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="6aac2-340">*GestureRecognizer*会记住是否它已打开或关闭在其中实际发生手势，在早期帧期间因此它是可靠地启动和停止手势监视基于目标的此帧的视线移动。</span><span class="sxs-lookup"><span data-stu-id="6aac2-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="6aac2-341">停止捕获手势</span><span class="sxs-lookup"><span data-stu-id="6aac2-341">Stop capturing gestures</span></span>

<span data-ttu-id="6aac2-342">若要停止手势识别：</span><span class="sxs-lookup"><span data-stu-id="6aac2-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="6aac2-343">删除的手势识别程序</span><span class="sxs-lookup"><span data-stu-id="6aac2-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="6aac2-344">请记住要销毁之前取消订阅已订阅事件*GestureRecognizer*对象。</span><span class="sxs-lookup"><span data-stu-id="6aac2-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="6aac2-345">呈现在 Unity 中的动作控制器模型</span><span class="sxs-lookup"><span data-stu-id="6aac2-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="6aac2-346">![运动控制器模型和 teleportation](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6aac2-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="6aac2-347">*运动控制器模型和 teleportation*</span><span class="sxs-lookup"><span data-stu-id="6aac2-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="6aac2-348">若要呈现匹配你的用户持有并清楚地表述的各种按钮被按下物理控制器的运动控制器应用程序中，可以使用**MotionController 预设**中[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="6aac2-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="6aac2-349">此预设可从系统的已安装的运动控制器驱动程序动态加载在运行时的正确 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="6aac2-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="6aac2-350">务必要动态加载这些模型而不是手动导入它们在编辑器中，以便您的应用程序会显示以物理方式准确的三维模型的所有当前和未来控制器以你的用户可能有。</span><span class="sxs-lookup"><span data-stu-id="6aac2-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="6aac2-351">请按照[Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)说明下载混合现实工具包并将其添加到你的 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="6aac2-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="6aac2-352">如果替换使用照相机*MixedRealityCameraParent*预设作为入门教程步骤的一部分，您就可以开始 ！</span><span class="sxs-lookup"><span data-stu-id="6aac2-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="6aac2-353">该预设可包括运动控制器呈现。</span><span class="sxs-lookup"><span data-stu-id="6aac2-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="6aac2-354">否则，添加*Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab*到您从项目窗格中的场景。</span><span class="sxs-lookup"><span data-stu-id="6aac2-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="6aac2-355">你将想要添加任何父对象的子级为 prefab 用于围绕时使照相机在场景中的用户 teleports，以便在控制器都会随用户。</span><span class="sxs-lookup"><span data-stu-id="6aac2-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="6aac2-356">如果您的应用程序并不涉及 teleporting，只需添加预设可在您的场景的根目录。</span><span class="sxs-lookup"><span data-stu-id="6aac2-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="6aac2-357">引发对象</span><span class="sxs-lookup"><span data-stu-id="6aac2-357">Throwing objects</span></span>

<span data-ttu-id="6aac2-358">虚拟现实中引发的对象是棘手的问题，则它可能最初看起来。</span><span class="sxs-lookup"><span data-stu-id="6aac2-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="6aac2-359">如使用最以物理方式根据交互，引发在游戏的行为以意外方式时，它非常直观，并将深入探讨。</span><span class="sxs-lookup"><span data-stu-id="6aac2-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="6aac2-360">我们花费了有关如何表示以物理方式正确引发行为，并提出了一些指导原则，我们的平台，我们想要与你共享的更新通过启用深度一些时间来研究。</span><span class="sxs-lookup"><span data-stu-id="6aac2-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="6aac2-361">您可以找到相关的建议来实现引发示例[此处](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="6aac2-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="6aac2-362">此示例按下列四个原则：</span><span class="sxs-lookup"><span data-stu-id="6aac2-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="6aac2-363">**使用控制器的*速度*而不是位置**。</span><span class="sxs-lookup"><span data-stu-id="6aac2-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="6aac2-364">在 Windows 的年 11 月更新，我们引入了行为发生变化时在['近似' 位置跟踪状态](motion-controllers.md#controller-tracking-state)。</span><span class="sxs-lookup"><span data-stu-id="6aac2-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="6aac2-365">在此状态下，速度有关控制器的信息将继续，只要我们都很高的准确性，通常是时间比位置一直保持高精度时间长的报告。</span><span class="sxs-lookup"><span data-stu-id="6aac2-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="6aac2-366">**将合并*角速度*控制器的**。</span><span class="sxs-lookup"><span data-stu-id="6aac2-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="6aac2-367">此逻辑都包含在`throwing.cs`文件中`GetThrownObjectVelAngVel`以上链接的包中的静态方法：</span><span class="sxs-lookup"><span data-stu-id="6aac2-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="6aac2-368">如角速度供电来节约，则引发该异常的对象必须维护相同角速度因为它会引发目前有： `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="6aac2-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="6aac2-369">可能不手柄姿势原点，它可能具有不同的速度就在那时，在控制器中的用户的参考框架则引发该异常对象的质心的原样。</span><span class="sxs-lookup"><span data-stu-id="6aac2-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="6aac2-370">以这种方式提供的对象的部分是质的对象的速度的围绕控制器源引发心的即时叙事速度。</span><span class="sxs-lookup"><span data-stu-id="6aac2-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="6aac2-371">此叙事速度是对象的角速度控制器与表示控制器源引发的质心的之间的距离矢量的叉积。</span><span class="sxs-lookup"><span data-stu-id="6aac2-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="6aac2-372">则引发该异常对象的总速度因此是控制器的速度和此叙事速度的总和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="6aac2-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="6aac2-373">**密切关注*时间*我们的应用速度**。</span><span class="sxs-lookup"><span data-stu-id="6aac2-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="6aac2-374">按下按钮时，可能需要最多 20 毫秒向上冒泡通过蓝牙操作系统到该事件。</span><span class="sxs-lookup"><span data-stu-id="6aac2-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="6aac2-375">这意味着，如果未按下状态轮询的控制器状态更改为按下或反之亦然，使用它获取的控制器姿势信息实际上就会领先于此状态中的更改。</span><span class="sxs-lookup"><span data-stu-id="6aac2-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="6aac2-376">此外，主讲人我们轮询 API 控制器姿势向前预测以反映在帧将显示在将来可能是从多个然后 20 毫秒的时间可能姿势。</span><span class="sxs-lookup"><span data-stu-id="6aac2-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="6aac2-377">此方案的好处*呈现*保存对象，但也会增加为我们时间问题*面向*对象我们目前计算轨迹用户发布其抛出。</span><span class="sxs-lookup"><span data-stu-id="6aac2-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="6aac2-378">幸运的是，通过年 11 月更新，如果 Unity 事件喜欢*InteractionSourcePressed*或*InteractionSourceReleased*发送，该状态包括历史姿势数据从后何时按钮为实际按下或释放。</span><span class="sxs-lookup"><span data-stu-id="6aac2-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="6aac2-379">若要获取最准确的控制器呈现和过程，则会引发目标控制器，必须根据需要正确使用轮询和事件处理:</span><span class="sxs-lookup"><span data-stu-id="6aac2-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="6aac2-380">有关**控制器呈现**每个帧，您的应用程序应放置在控制器*GameObject*进预测控制器级别会带来的当前帧的 photon 时间。</span><span class="sxs-lookup"><span data-stu-id="6aac2-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="6aac2-381">从 Unity 轮询的 Api，例如获取此数据*[XR。InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。WSA。Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。</span><span class="sxs-lookup"><span data-stu-id="6aac2-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="6aac2-382">有关**控制器面向**按或版本，您的应用程序应 raycast 和计算基础按或发布事件的历史控制器姿势的轨迹。</span><span class="sxs-lookup"><span data-stu-id="6aac2-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="6aac2-383">你收到此数据从 Unity eventing Api，如 *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。</span><span class="sxs-lookup"><span data-stu-id="6aac2-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="6aac2-384">**使用手柄姿势**。</span><span class="sxs-lookup"><span data-stu-id="6aac2-384">**Use the grip pose**.</span></span> <span data-ttu-id="6aac2-385">相对于手柄姿势不指针姿势报告角速度和速度。</span><span class="sxs-lookup"><span data-stu-id="6aac2-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="6aac2-386">引发将继续改进未来的 Windows 更新，并且，你可能需要对其在此处找到更多信息。</span><span class="sxs-lookup"><span data-stu-id="6aac2-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="accelerate-development-with-mixed-reality-toolkit"></a><span data-ttu-id="6aac2-387">加速开发的混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="6aac2-387">Accelerate development with Mixed Reality Toolkit</span></span>

<span data-ttu-id="6aac2-388">有两个有关 InputManager 和 MotionController Unity 中的示例场景。</span><span class="sxs-lookup"><span data-stu-id="6aac2-388">There are two example scenes about InputManager and MotionController in Unity.</span></span> <span data-ttu-id="6aac2-389">通过这些场景中，可以了解如何使用 MRTK 的 InputManager 和通过动作控制器按钮来访问数据处理事件。</span><span class="sxs-lookup"><span data-stu-id="6aac2-389">Through these scenes, you can learn how to use MRTK's InputManager and access data handle events from the motion controller buttons.</span></span>

- [<span data-ttu-id="6aac2-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="6aac2-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [<span data-ttu-id="6aac2-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span><span class="sxs-lookup"><span data-stu-id="6aac2-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [<span data-ttu-id="6aac2-392">技术详细信息的自述文件</span><span class="sxs-lookup"><span data-stu-id="6aac2-392">Technical details README File</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

<span data-ttu-id="6aac2-393">![输入 MRTK 中的示例场景](images/MRTK_ExampleScene_Input.png)</span><span class="sxs-lookup"><span data-stu-id="6aac2-393">![Input example scenes in MRTK](images/MRTK_ExampleScene_Input.png)</span></span><br>
<span data-ttu-id="6aac2-394">*输入 MRTK 中的示例场景*</span><span class="sxs-lookup"><span data-stu-id="6aac2-394">*Input example scenes in MRTK*</span></span>

### <a name="automatic-scene-setup"></a><span data-ttu-id="6aac2-395">自动场景安装程序</span><span class="sxs-lookup"><span data-stu-id="6aac2-395">Automatic scene setup</span></span>

<span data-ttu-id="6aac2-396">当您导入[MRTK 发布 Unity 包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或从克隆项目[GitHub 存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，要在 Unity 中查找新菜单混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="6aac2-396">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="6aac2-397">在配置菜单中，你会看到菜单应用混合现实场景设置。</span><span class="sxs-lookup"><span data-stu-id="6aac2-397">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="6aac2-398">当您单击它时，它默认照相机中删除，并添加基础组件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，并[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。</span><span class="sxs-lookup"><span data-stu-id="6aac2-398">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="6aac2-399">![MRTK 场景设置菜单](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="6aac2-399">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="6aac2-400">*MRTK 场景设置菜单*</span><span class="sxs-lookup"><span data-stu-id="6aac2-400">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="6aac2-401">![自动场景中 MRTK 的安装程序](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="6aac2-401">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="6aac2-402">*自动场景中 MRTK 的安装程序*</span><span class="sxs-lookup"><span data-stu-id="6aac2-402">*Automatic scene setup in MRTK*</span></span>

### <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="6aac2-403">MixedRealityCamera 预设</span><span class="sxs-lookup"><span data-stu-id="6aac2-403">MixedRealityCamera prefab</span></span>

<span data-ttu-id="6aac2-404">您可以手动添加这些项目面板中。</span><span class="sxs-lookup"><span data-stu-id="6aac2-404">You can also manually add these from the project panel.</span></span> <span data-ttu-id="6aac2-405">您可以找到这些组件作为预设。</span><span class="sxs-lookup"><span data-stu-id="6aac2-405">You can find these components as prefabs.</span></span> <span data-ttu-id="6aac2-406">当您搜索**MixedRealityCamera**，你将能够看到两个不同的照相机预设。</span><span class="sxs-lookup"><span data-stu-id="6aac2-406">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="6aac2-407">其差异是， **MixedRealityCamera**才照相机 prefab 而**MixedRealityCameraParent**包括如 Teleportation，Motion 沉浸式耳机的其他组件控制器和，边界。</span><span class="sxs-lookup"><span data-stu-id="6aac2-407">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="6aac2-408">![在 MRTK 照相机预设](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="6aac2-408">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="6aac2-409">*在 MRTK 照相机预设*</span><span class="sxs-lookup"><span data-stu-id="6aac2-409">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="6aac2-410">**MixedRealtyCamera**支持 HoloLens 和沉浸式头戴式耳机。</span><span class="sxs-lookup"><span data-stu-id="6aac2-410">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="6aac2-411">它检测到的设备类型，并优化了清除标志和 Skybox 等属性。</span><span class="sxs-lookup"><span data-stu-id="6aac2-411">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="6aac2-412">可以在下面查找一些有用的属性可以自定义光标，Motion 控制器模型，如自定义和 Floor。</span><span class="sxs-lookup"><span data-stu-id="6aac2-412">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="6aac2-413">![游标和 Floor 运动控制器属性](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="6aac2-413">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="6aac2-414">*游标和 Floor 运动控制器属性*</span><span class="sxs-lookup"><span data-stu-id="6aac2-414">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="6aac2-415">按照教程</span><span class="sxs-lookup"><span data-stu-id="6aac2-415">Follow along with tutorials</span></span>

<span data-ttu-id="6aac2-416">混合现实学院中提供了分步教程，使用更多详细的自定义示例：</span><span class="sxs-lookup"><span data-stu-id="6aac2-416">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="6aac2-417">MR 输入 211:手势</span><span class="sxs-lookup"><span data-stu-id="6aac2-417">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="6aac2-418">MR 输入 213:运动控制器</span><span class="sxs-lookup"><span data-stu-id="6aac2-418">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="6aac2-419">[![MR 输入 213-运动控制器](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="6aac2-419">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="6aac2-420">*MR 输入 213-运动控制器*</span><span class="sxs-lookup"><span data-stu-id="6aac2-420">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="6aac2-421">请参阅</span><span class="sxs-lookup"><span data-stu-id="6aac2-421">See also</span></span>

* [<span data-ttu-id="6aac2-422">手势</span><span class="sxs-lookup"><span data-stu-id="6aac2-422">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="6aac2-423">运动控制器</span><span class="sxs-lookup"><span data-stu-id="6aac2-423">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="6aac2-424">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="6aac2-424">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="6aac2-425">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="6aac2-425">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="6aac2-426">InteractionInputSource.cs MixedRealityToolkit Unity 中</span><span class="sxs-lookup"><span data-stu-id="6aac2-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
