---
title: 在主页中启用3D 模型的放置
description: 如何在 Windows Mixed Reality 主页中放置网站或应用程序中的3D 模型
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, 模型, 在家中放置, 地点, 世界, 建模, 混合现实主页, web, 应用
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829731"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="9b5ff-104">在混合现实主页中启用3D 模型的放置</span><span class="sxs-lookup"><span data-stu-id="9b5ff-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="9b5ff-105">此功能已作为[Windows 10 2018 年4月更新](release-notes-april-2018.md)的一部分添加。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="9b5ff-106">Windows 的较早版本与此功能不兼容。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="9b5ff-107">[Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)是用户在启动应用程序之前居住的起点。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="9b5ff-108">在某些情况下, 二维应用 (如全息影像应用程序) 可将3D 模型直接放置在混合现实主页中作为装饰, 或在完整的3D 中进行进一步检查。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="9b5ff-109">使用 "*添加模型" 协议*, 可以将三维模型从你的网站或应用程序直接发送到 Windows Mixed Reality 主页, 它将在其中持久保存, 如[3d 应用程序启动器](3d-app-launcher-design-guidance.md)、二维应用和全息影像。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="9b5ff-110">例如, 如果您正在开发一个应用程序, 该应用程序显示了用于设计空间的3D 家具的目录, 则可以使用 "*添加模型" 协议*允许用户将这些3d 家具模型从目录中放置。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="9b5ff-111">一旦进入世界, 用户就可以移动、调整大小和删除这些3D 模型, 就像在家中的其他全息影像一样。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="9b5ff-112">本文概述了如何实现*添加模型协议*, 以便您可以开始使用户能够通过您的应用或 web 中的3d 对象来装饰他们的世界。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="9b5ff-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="9b5ff-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9b5ff-114"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="9b5ff-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="9b5ff-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="9b5ff-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="9b5ff-116"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="9b5ff-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9b5ff-117">添加模型协议</span><span class="sxs-lookup"><span data-stu-id="9b5ff-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="9b5ff-118">✔️</span><span class="sxs-lookup"><span data-stu-id="9b5ff-118">✔️</span></span></td>
        <td><span data-ttu-id="9b5ff-119">✔️</span><span class="sxs-lookup"><span data-stu-id="9b5ff-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="9b5ff-120">概述</span><span class="sxs-lookup"><span data-stu-id="9b5ff-120">Overview</span></span>

<span data-ttu-id="9b5ff-121">可以通过两个步骤在 Windows Mixed Reality 主页中启用3D 模型的放置:</span><span class="sxs-lookup"><span data-stu-id="9b5ff-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="9b5ff-122">[确保3d 模型与 Windows Mixed Reality 主页兼容](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="9b5ff-123">在应用程序或网页中实现*添加模型协议*(本文)。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="9b5ff-124">实现*添加模型协议*</span><span class="sxs-lookup"><span data-stu-id="9b5ff-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="9b5ff-125">获得[兼容的3d 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)后, 可以通过从任何网页或应用程序激活以下 URI 来实现*添加模型协议*:</span><span class="sxs-lookup"><span data-stu-id="9b5ff-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="9b5ff-126">如果 URI 指向远程资源, 则它将自动下载并放置在主文件夹中。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="9b5ff-127">本地资源将被复制到混合现实主页的应用数据文件夹中, 然后放入 home。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="9b5ff-128">建议在以下情况下设计你的体验: 用户可能正在运行不支持此功能的较早版本的 Windows (如有可能)。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="9b5ff-129">从通用 Windows 平台应用调用*添加模型协议*:</span><span class="sxs-lookup"><span data-stu-id="9b5ff-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="9b5ff-130">从网页调用*添加模型协议*:</span><span class="sxs-lookup"><span data-stu-id="9b5ff-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="9b5ff-131">沉浸式 (VR) 耳机注意事项</span><span class="sxs-lookup"><span data-stu-id="9b5ff-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="9b5ff-132">对于沉浸式 (VR) 耳机, 在调用*添加模型协议*之前, 混合现实门户无需运行。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="9b5ff-133">在这种情况下, "*添加模型" 协议*将启动混合现实门户, 并将对象直接放置在头戴显示在混合现实中的位置。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="9b5ff-134">当在已运行混合现实门户的情况下从桌面调用 "*添加模型" 协议*时, 请确保头戴式耳机处于 "唤醒" 状态。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="9b5ff-135">否则, 放置将不会成功。</span><span class="sxs-lookup"><span data-stu-id="9b5ff-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="9b5ff-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b5ff-136">See also</span></span>

* [<span data-ttu-id="9b5ff-137">创建用于 Windows Mixed Reality 主页的3D 模型</span><span class="sxs-lookup"><span data-stu-id="9b5ff-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="9b5ff-138">导航 Windows Mixed Reality 主页</span><span class="sxs-lookup"><span data-stu-id="9b5ff-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
