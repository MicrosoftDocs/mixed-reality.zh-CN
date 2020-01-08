---
title: Unity 中的焦点
description: 通过设置焦点在 Unity 中手动优化全息影像稳定性
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，焦点，焦点平面，稳定平面，稳定点，reprojection，LSR，深度缓冲区
ms.openlocfilehash: 9a7f30b552242b24a9a7b260b6574690a27d2c1d
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502618"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="bd823-104">Unity 中的焦点</span><span class="sxs-lookup"><span data-stu-id="bd823-104">Focus point in Unity</span></span>

<span data-ttu-id="bd823-105">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="bd823-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="bd823-106">**类型**： *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="bd823-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="bd823-107">可以将[焦点](hologram-stability.md#reprojection)设置为提供有关如何在当前显示的全息影像上最好地执行稳定的提示。</span><span class="sxs-lookup"><span data-stu-id="bd823-107">The [focus point](hologram-stability.md#reprojection) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="bd823-108">如果要在 Unity 中设置焦点，则需要使用*HolographicSettings. SetFocusPointForFrame （）* 设置每个框架。</span><span class="sxs-lookup"><span data-stu-id="bd823-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="bd823-109">如果未为帧设置焦点，则将使用默认的稳定平面。</span><span class="sxs-lookup"><span data-stu-id="bd823-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="bd823-110">默认情况下，新的 Unity 项目设置了 "启用深度缓冲共享" 选项。</span><span class="sxs-lookup"><span data-stu-id="bd823-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="bd823-111">使用此选项时，在沉浸式桌面耳机上运行的 Unity 应用或运行 Windows 10 4 月2018更新（RS4）或更高版本的 HoloLens 将向 Windows 提交深度缓冲区以自动优化全息影像稳定性，无需应用指定焦点：</span><span class="sxs-lookup"><span data-stu-id="bd823-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="bd823-112">在沉浸式桌面耳机上，这将启用基于像素深度的 reprojection。</span><span class="sxs-lookup"><span data-stu-id="bd823-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="bd823-113">在运行 Windows 10 4 月2018更新或更高版本的 HoloLens 上，这将分析深度缓冲区以自动选择最佳的稳定平面。</span><span class="sxs-lookup"><span data-stu-id="bd823-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="bd823-114">这两种方法都应该提供更好的图像质量，而无需由您的应用程序显式工作，从而为每个帧选择焦点。</span><span class="sxs-lookup"><span data-stu-id="bd823-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="bd823-115">请注意，如果你确实手动提供了焦点，这将替代上述自动行为，并且通常会降低全息图的稳定性。</span><span class="sxs-lookup"><span data-stu-id="bd823-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="bd823-116">通常，仅当你的应用在尚未更新到 Windows 10 4 2018 月版更新的 HoloLens 上运行时，才应指定手动焦点点。</span><span class="sxs-lookup"><span data-stu-id="bd823-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="bd823-117">示例</span><span class="sxs-lookup"><span data-stu-id="bd823-117">Example</span></span>

<span data-ttu-id="bd823-118">有多种方法可设置焦点，如*SetFocusPointForFrame*静态函数上的可用重载所建议的那样。</span><span class="sxs-lookup"><span data-stu-id="bd823-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="bd823-119">下面提供了一个简单的示例，可将焦点平面设置为每个帧的提供的对象：</span><span class="sxs-lookup"><span data-stu-id="bd823-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="bd823-120">请注意，如果焦点对象最终出现在用户后面，则上述简单代码可能最终会降低全息体稳定性。</span><span class="sxs-lookup"><span data-stu-id="bd823-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="bd823-121">这就是通常应设置 "启用深度缓冲区共享" 而不是手动指定焦点的原因。</span><span class="sxs-lookup"><span data-stu-id="bd823-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="bd823-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd823-122">See also</span></span>
* [<span data-ttu-id="bd823-123">稳定平面</span><span class="sxs-lookup"><span data-stu-id="bd823-123">Stabilization plane</span></span>](hologram-stability.md#reprojection)
