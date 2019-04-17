---
title: 移植指南 Unity 的输入
description: 了解如何处理在 Unity 中的 Windows Mixed Reality 的输入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 输入、 unity、 移植
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592543"
---
# <a name="input-porting-guide-for-unity"></a><span data-ttu-id="5aa97-104">移植指南 Unity 的输入</span><span class="sxs-lookup"><span data-stu-id="5aa97-104">Input porting guide for Unity</span></span>

<span data-ttu-id="5aa97-105">可以移植到 Windows Mixed Reality 使用两种方法，跨多个平台，Unity 的常规 Input.GetButton/GetAxis Api 或特定于 Windows 的 XR 之一你输入的逻辑。WSA。输入产品/服务专为运动控制器和 HoloLens 手更丰富的数据的 Api。</span><span class="sxs-lookup"><span data-stu-id="5aa97-105">You can port your input logic to Windows Mixed Reality using one of two approaches, Unity's general Input.GetButton/GetAxis APIs that span across multiple platforms, or the Windows-specific XR.WSA.Input APIs that offer richer data specifically for motion controllers and HoloLens hands.</span></span>

## <a name="general-inputgetbuttongetaxis-apis"></a><span data-ttu-id="5aa97-106">常规 Input.GetButton/GetAxis Api</span><span class="sxs-lookup"><span data-stu-id="5aa97-106">General Input.GetButton/GetAxis APIs</span></span>

<span data-ttu-id="5aa97-107">Unity 当前使用其常规 Input.GetButton/Input.GetAxis Api 公开的输入[Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)并[OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)。</span><span class="sxs-lookup"><span data-stu-id="5aa97-107">Unity currently uses its general Input.GetButton/Input.GetAxis APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) and [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html).</span></span> <span data-ttu-id="5aa97-108">如果您的应用程序已在使用这些 Api 的输入，这是以支持 Windows Mixed Reality 中的动作控制器的最简单路径： 只需重新映射按钮和轴中输入管理器。</span><span class="sxs-lookup"><span data-stu-id="5aa97-108">If your apps are already using these APIs for input, this is the easiest path for supporting motion controllers in Windows Mixed Reality: you should just need to remap buttons and axes in the Input Manager.</span></span>

<span data-ttu-id="5aa97-109">有关详细信息，请参阅[Unity 按钮/轴映射表](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)并[常见的 Unity Api 概述](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。</span><span class="sxs-lookup"><span data-stu-id="5aa97-109">For more information, see the [Unity button/axis mapping table](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) and the [overview of the common Unity APIs](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).</span></span>

## <a name="windows-specific-xrwsainput-apis"></a><span data-ttu-id="5aa97-110">Windows-specific XR.WSA.Input APIs</span><span class="sxs-lookup"><span data-stu-id="5aa97-110">Windows-specific XR.WSA.Input APIs</span></span>

<span data-ttu-id="5aa97-111">如果你的应用程序已生成的每个平台的自定义输入的逻辑，你可以选择使用特定于 Windows 的空间输入的 Api 下**UnityEngine.XR.WSA.Input**命名空间。</span><span class="sxs-lookup"><span data-stu-id="5aa97-111">If your app already builds custom input logic for each platform, you can choose to use the Windows-specific spatial input APIs under the **UnityEngine.XR.WSA.Input** namespace.</span></span> <span data-ttu-id="5aa97-112">这允许您访问其他信息，如位置准确性或源类型，让你在 HoloLens 上告诉双手和控制器分离。</span><span class="sxs-lookup"><span data-stu-id="5aa97-112">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart on HoloLens.</span></span>

<span data-ttu-id="5aa97-113">有关详细信息，请参阅[UnityEngine.XR.WSA.Input Api 概述](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。</span><span class="sxs-lookup"><span data-stu-id="5aa97-113">For more information, see the [overview of the UnityEngine.XR.WSA.Input APIs](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="5aa97-114">与指针姿势手柄姿势</span><span class="sxs-lookup"><span data-stu-id="5aa97-114">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="5aa97-115">Windows Mixed Reality 支持不同的外形规格运动控制器，使用每个控制器设计各不相同，"转发"方向该应用的自然用户的手位置之间的关系应为使用指向呈现时控制器。</span><span class="sxs-lookup"><span data-stu-id="5aa97-115">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="5aa97-116">若要更好地表示这些控制器，有两种类型的可以为每个交互源调查的带来：</span><span class="sxs-lookup"><span data-stu-id="5aa97-116">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>

* <span data-ttu-id="5aa97-117">**手柄姿势**，表示检测到的 HoloLens 手的形状的手掌或手掌持有运动控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="5aa97-117">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="5aa97-118">在沉浸式耳机，此姿势最适合用于呈现**用户的手**或**对象保存在用户的手中**，例如双刃剑或手段。</span><span class="sxs-lookup"><span data-stu-id="5aa97-118">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="5aa97-119">**抓住位置**:Palm 质心时保存在控制器正常情况下，调整左侧或右侧居中手柄内的位置。</span><span class="sxs-lookup"><span data-stu-id="5aa97-119">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="5aa97-120">**抓住方向的右轴**:完全打开您的手以形成平面 5 手指姿势，ray 的时您的手掌接触到正常 （从左 palm，向右 palm 从后向前）</span><span class="sxs-lookup"><span data-stu-id="5aa97-120">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="5aa97-121">**抓住正轴方向的**:当您关闭您的手部分 （就像按控制器），"forward"通过管通过非 thumb 手指点与射线。</span><span class="sxs-lookup"><span data-stu-id="5aa97-121">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="5aa97-122">**抓住方向沿轴向上**:权限隐含的权限和转发定义最多轴。</span><span class="sxs-lookup"><span data-stu-id="5aa97-122">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="5aa97-123">您可以通过任一 Unity 跨供应商输入 API 访问手柄姿势 (**[XR。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation**) 或通过特定于 Windows 的 API (**sourceState.sourcePose.TryGetPosition/Rotation**，请求手柄姿势)。</span><span class="sxs-lookup"><span data-stu-id="5aa97-123">You can access the grip pose through either Unity's cross-vendor input API (**[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation**) or through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Grip pose).</span></span>
* <span data-ttu-id="5aa97-124">**指针姿势**，表示指向转发的控制器的提示。</span><span class="sxs-lookup"><span data-stu-id="5aa97-124">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="5aa97-125">此姿势最习惯 raycast 时**指向 UI**时呈现控制器模型本身。</span><span class="sxs-lookup"><span data-stu-id="5aa97-125">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="5aa97-126">目前，指针姿势目前仅通过特定于 Windows 的 API (**sourceState.sourcePose.TryGetPosition/Rotation**，请求指针姿势)。</span><span class="sxs-lookup"><span data-stu-id="5aa97-126">Currently, the pointer pose is available only through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Pointer pose).</span></span>

<span data-ttu-id="5aa97-127">这些姿势坐标都表示在 Unity 世界坐标。</span><span class="sxs-lookup"><span data-stu-id="5aa97-127">These pose coordinates are all expressed in Unity world coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="5aa97-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="5aa97-128">See also</span></span>
* [<span data-ttu-id="5aa97-129">运动控制器</span><span class="sxs-lookup"><span data-stu-id="5aa97-129">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="5aa97-130">手势和 Unity 中的动作控制器</span><span class="sxs-lookup"><span data-stu-id="5aa97-130">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="5aa97-131">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="5aa97-131">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="5aa97-132">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="5aa97-132">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="5aa97-133">移植指南</span><span class="sxs-lookup"><span data-stu-id="5aa97-133">Porting guides</span></span>](porting-guides.md)
