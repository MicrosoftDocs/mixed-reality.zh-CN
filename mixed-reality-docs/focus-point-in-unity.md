---
title: 在 Unity 中的焦点位置
description: 手动优化在 Unity 中的 hologram 稳定性通过设置焦点
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 焦点、 焦点平面、 稳定平面、 稳定点、 reprojection，LSR、 深度缓冲区
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593024"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="19b24-104">在 Unity 中的焦点位置</span><span class="sxs-lookup"><span data-stu-id="19b24-104">Focus point in Unity</span></span>

<span data-ttu-id="19b24-105">\**命名空间：\*\*\*UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="19b24-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="19b24-106">类型：*HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="19b24-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="19b24-107">[关注点](hologram-stability.md#stabilization-plane)可以设置为提供有关如何更好地执行上全息稳定，当前提示的 HoloLens 正在显示。</span><span class="sxs-lookup"><span data-stu-id="19b24-107">The [focus point](hologram-stability.md#stabilization-plane) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="19b24-108">如果你想要将焦点设置在 Unity 中，则需要使用每个帧进行设置*HolographicSettings.SetFocusPointForFrame()*。</span><span class="sxs-lookup"><span data-stu-id="19b24-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="19b24-109">如果没有为一个帧设置焦点，则将使用默认稳定平面。</span><span class="sxs-lookup"><span data-stu-id="19b24-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="19b24-110">默认情况下，新的 Unity 项目具有设置的"启用深度缓冲区共享"选项。</span><span class="sxs-lookup"><span data-stu-id="19b24-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="19b24-111">使用此选项时，令人着迷的桌面耳机或运行 Windows HoloLens 上运行的 Unity 应用 10 2018 年 4 月更新 (RS4) 或更高版本将提交到 Windows，而无需在应用指定自动优化全息图稳定性深度缓冲区焦点位置：</span><span class="sxs-lookup"><span data-stu-id="19b24-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="19b24-112">在沉浸式的桌面耳机，这将使每个像素深度基于 reprojection。</span><span class="sxs-lookup"><span data-stu-id="19b24-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="19b24-113">HoloLens 上运行 Windows 10 2018 年 4 月更新或更高版本，这将分析要自动选择最佳稳定平面的深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="19b24-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="19b24-114">这两种方法应由您选择的焦点位置的应用程序的每个帧提供更好的图像质量，而无需显式工作。</span><span class="sxs-lookup"><span data-stu-id="19b24-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="19b24-115">请注意，如果你手动提供焦点，，将重写自动行为，上面所述，通常会减少全息图稳定性。</span><span class="sxs-lookup"><span data-stu-id="19b24-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="19b24-116">通常情况下，只应指定手动焦点上尚未更新到 Windows HoloLens 运行您的应用程序时 10 2018 年 4 月更新。</span><span class="sxs-lookup"><span data-stu-id="19b24-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="19b24-117">示例</span><span class="sxs-lookup"><span data-stu-id="19b24-117">Example</span></span>

<span data-ttu-id="19b24-118">有许多方法可设置焦点，正如建议上可用的重载*SetFocusPointForFrame*静态函数。</span><span class="sxs-lookup"><span data-stu-id="19b24-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="19b24-119">以下是一个简单的示例将焦点平面设置为所提供的对象的每个帧：</span><span class="sxs-lookup"><span data-stu-id="19b24-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

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

<span data-ttu-id="19b24-120">请注意，上面的简单代码可能最终会减少全息图稳定性，如果已设定焦点的对象，该怎么办背后用户。</span><span class="sxs-lookup"><span data-stu-id="19b24-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="19b24-121">这就是原因而不是手动指定的焦点位置应通常设置"启用深度缓冲区共享"。</span><span class="sxs-lookup"><span data-stu-id="19b24-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="19b24-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="19b24-122">See also</span></span>
* [<span data-ttu-id="19b24-123">稳定平面</span><span class="sxs-lookup"><span data-stu-id="19b24-123">Stabilization plane</span></span>](hologram-stability.md#stabilization-plane)