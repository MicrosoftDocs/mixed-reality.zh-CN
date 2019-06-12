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
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>启用主混合现实中的三维模型的位置

> [!NOTE]
> 此功能已添加的一部分[Windows 10 2018 年 4 月更新](release-notes-april-2018.md)。 较旧版本的 Windows 不使用此功能兼容。

[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)是用户启动应用程序之前登陆的位置的起始点。 在某些情况下，2D 应用 （如全息应用中） 作为修饰或进一步检查完整三维启用三维模型直接放置混合的现实主页。 *添加模型协议*喜欢其中它将保持不变，可从你的网站或直接在 Windows Mixed Reality 主页、 应用程序发送的三维模型[三维应用启动器上](3d-app-launcher-design-guidance.md)，2D 应用和全息。 

例如，如果要开发应用程序的目录的设计空间的 3D 家具呈现，则可以使用*添加模型协议*以允许用户将放那些 3D 家具模型从目录。 放置在世界中，用户可以移动、 调整大小，和在主页中删除这些三维模型，就像其他全息一样。 本文提供的实现概述*添加模型协议*，以便可以开始使用户能够修饰他们使用从您的应用程序或 web 的三维对象的世界。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
    </tr>
     <tr>
        <td>添加模型协议</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>概述

需要向 Windows Mixed Reality 家庭中的三维模型的位置，使两个步骤：
1. [确保三维模型与 Windows Mixed Reality 家庭兼容](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。
2. 实现*添加模型协议*中你的应用程序或网页 （详见本文）。

## <a name="implementing-the-add-model-protocol"></a>实现*添加模型协议*

一旦您有[兼容的三维模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)，可以实现*添加模型协议*通过激活从任何网页或应用程序的以下 URI:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

如果 URI 指向远程资源，然后它将自动下载并置于主页。 将复制到混合的现实主页的应用程序数据文件夹之前，在家里放置的本地资源。 我们建议正确设计您的体验到的情况下，用户可能会运行较旧版本的 Windows 不支持此功能通过隐藏按钮或在可能的情况禁用的帐户。 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>调用*添加模型协议*从通用 Windows 平台应用：

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>调用*添加模型协议*网页中：

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>沉浸式 (VR) 耳机的注意事项

* 沉浸式 (VR) 耳机，混合现实门户不需要调用之前运行*添加模型协议*。 在这种情况下，*添加模型协议*启动混合现实门户，并将直接其中耳机查找后到达主混合现实中的对象。 
* 调用时*添加模型协议*从使用混合现实门户已在运行桌面，请确保将耳机会"唤醒"。 如果没有，位置将不会成功。 

## <a name="see-also"></a>请参阅

* [在 Windows Mixed Reality 主页中创建用于 3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [导航 Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)
