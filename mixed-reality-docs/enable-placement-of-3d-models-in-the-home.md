---
title: 启用在家中的三维模型的位置
description: 如何在 Windows Mixed Reality 家庭中将从你的网站或应用程序的三维模型
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D、 模型、 家中的位置、 位置、 世界、 建模、 混合的现实家庭、 web、 应用
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829731"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="e5df1-104">启用主混合现实中的三维模型的位置</span><span class="sxs-lookup"><span data-stu-id="e5df1-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="e5df1-105">此功能已添加的一部分[Windows 10 2018 年 4 月更新](release-notes-april-2018.md)。</span><span class="sxs-lookup"><span data-stu-id="e5df1-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="e5df1-106">较旧版本的 Windows 不使用此功能兼容。</span><span class="sxs-lookup"><span data-stu-id="e5df1-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="e5df1-107">[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)是用户启动应用程序之前登陆的位置的起始点。</span><span class="sxs-lookup"><span data-stu-id="e5df1-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="e5df1-108">在某些情况下，2D 应用 （如全息应用中） 作为修饰或进一步检查完整三维启用三维模型直接放置混合的现实主页。</span><span class="sxs-lookup"><span data-stu-id="e5df1-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="e5df1-109">*添加模型协议*喜欢其中它将保持不变，可从你的网站或直接在 Windows Mixed Reality 主页、 应用程序发送的三维模型[三维应用启动器上](3d-app-launcher-design-guidance.md)，2D 应用和全息。</span><span class="sxs-lookup"><span data-stu-id="e5df1-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="e5df1-110">例如，如果要开发应用程序的目录的设计空间的 3D 家具呈现，则可以使用*添加模型协议*以允许用户将放那些 3D 家具模型从目录。</span><span class="sxs-lookup"><span data-stu-id="e5df1-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="e5df1-111">放置在世界中，用户可以移动、 调整大小，和在主页中删除这些三维模型，就像其他全息一样。</span><span class="sxs-lookup"><span data-stu-id="e5df1-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="e5df1-112">本文提供的实现概述*添加模型协议*，以便可以开始使用户能够修饰他们使用从您的应用程序或 web 的三维对象的世界。</span><span class="sxs-lookup"><span data-stu-id="e5df1-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="e5df1-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="e5df1-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e5df1-114"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="e5df1-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="e5df1-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="e5df1-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="e5df1-116"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></span><span class="sxs-lookup"><span data-stu-id="e5df1-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e5df1-117">添加模型协议</span><span class="sxs-lookup"><span data-stu-id="e5df1-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="e5df1-118">✔️</span><span class="sxs-lookup"><span data-stu-id="e5df1-118">✔️</span></span></td>
        <td><span data-ttu-id="e5df1-119">✔️</span><span class="sxs-lookup"><span data-stu-id="e5df1-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="e5df1-120">概述</span><span class="sxs-lookup"><span data-stu-id="e5df1-120">Overview</span></span>

<span data-ttu-id="e5df1-121">需要向 Windows Mixed Reality 家庭中的三维模型的位置，使两个步骤：</span><span class="sxs-lookup"><span data-stu-id="e5df1-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="e5df1-122">[确保三维模型与 Windows Mixed Reality 家庭兼容](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。</span><span class="sxs-lookup"><span data-stu-id="e5df1-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="e5df1-123">实现*添加模型协议*中你的应用程序或网页 （详见本文）。</span><span class="sxs-lookup"><span data-stu-id="e5df1-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="e5df1-124">实现*添加模型协议*</span><span class="sxs-lookup"><span data-stu-id="e5df1-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="e5df1-125">一旦您有[兼容的三维模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)，可以实现*添加模型协议*通过激活从任何网页或应用程序的以下 URI:</span><span class="sxs-lookup"><span data-stu-id="e5df1-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="e5df1-126">如果 URI 指向远程资源，然后它将自动下载并置于主页。</span><span class="sxs-lookup"><span data-stu-id="e5df1-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="e5df1-127">将复制到混合的现实主页的应用程序数据文件夹之前，在家里放置的本地资源。</span><span class="sxs-lookup"><span data-stu-id="e5df1-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="e5df1-128">我们建议正确设计您的体验到的情况下，用户可能会运行较旧版本的 Windows 不支持此功能通过隐藏按钮或在可能的情况禁用的帐户。</span><span class="sxs-lookup"><span data-stu-id="e5df1-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="e5df1-129">调用*添加模型协议*从通用 Windows 平台应用：</span><span class="sxs-lookup"><span data-stu-id="e5df1-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="e5df1-130">调用*添加模型协议*网页中：</span><span class="sxs-lookup"><span data-stu-id="e5df1-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="e5df1-131">沉浸式 (VR) 耳机的注意事项</span><span class="sxs-lookup"><span data-stu-id="e5df1-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="e5df1-132">沉浸式 (VR) 耳机，混合现实门户不需要调用之前运行*添加模型协议*。</span><span class="sxs-lookup"><span data-stu-id="e5df1-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="e5df1-133">在这种情况下，*添加模型协议*启动混合现实门户，并将直接其中耳机查找后到达主混合现实中的对象。</span><span class="sxs-lookup"><span data-stu-id="e5df1-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="e5df1-134">调用时*添加模型协议*从使用混合现实门户已在运行桌面，请确保将耳机会"唤醒"。</span><span class="sxs-lookup"><span data-stu-id="e5df1-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="e5df1-135">如果没有，位置将不会成功。</span><span class="sxs-lookup"><span data-stu-id="e5df1-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="e5df1-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="e5df1-136">See also</span></span>

* [<span data-ttu-id="e5df1-137">在 Windows Mixed Reality 主页中创建用于 3D 模型</span><span class="sxs-lookup"><span data-stu-id="e5df1-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="e5df1-138">导航 Windows Mixed Reality 主页</span><span class="sxs-lookup"><span data-stu-id="e5df1-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
