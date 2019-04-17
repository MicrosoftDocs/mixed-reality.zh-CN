---
title: 比例
description: 显示看起来真实 holographic 窗体中的内容的关键是尽可能真实地模拟现实世界的 visual 统计信息。
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，样式设计
ms.openlocfilehash: f13414bff7d84692e8e87aa2abdcded15627346f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590377"
---
# <a name="scale"></a>比例

显示看起来真实 holographic 窗体中的内容的关键是尽可能真实地模拟现实世界的 visual 统计信息。 这意味着将尽可能多的视觉提示，因为我们可以帮助我们 （在现实世界中） 中了解这些对象位于，它们是多大，因为它们由。 一个对象的小数位数是一个最重要的这些视觉提示，提供一个查看器的对象，以及提示的大小 （尤其是对于具有已知的大小的对象） 其位置。 此外，查看在实际规模较大的对象出现如密钥体验与众不同之处之一混合现实一般情况下 – 就没有可能基于屏幕的查看以前。

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>如何建议对象和环境的规模

有许多方法来建议的一个对象，小数位数其中一些有可能造成可感知的其他因素的影响。 关键是只需在真实的大小，显示对象和维护该实际大小，如用户移动。 这意味着全息将占用不同数量的用户的用户的 visual 角度和他们一起近或越远，是真实的对象执行的相同。

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>利用对象的距离，如向用户显示

一种常用方法是利用对象的距离，如向用户显示。 例如，考虑可视化用户一大系列辆汽车。 如果汽车是直接放它们在 arm 的长度，它将是太大，无法在用户的视角。 这需要用户移动其 head 和 body 了解整个对象。 如果汽车离开 （在同一房间） 放置更多，用户可以建立规模的意义上通过查看整个天线的视野中的对象然后将本身更接近移到它，以检查方面的详细信息。

[Volvo](https://www.youtube.com/watch?v=DilzwF90vec)使用这种方法创建新的汽车，利用 holographic 汽车认为现实和向用户直观的方式的小数位数的 showroom 体验。 与物理表，这样就允许用户了解的总大小和模型形状的汽车一张全息图开始体验。 更高版本中获得的体验，汽车将扩展到更大的规模 （超过设备的字段的视图的大小），但用户尚未获取较小的模型中的帧的引用，因为它们可以充分导航周围的汽车的功能。

![HoloLens Volvo 汽车体验](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
*HoloLens Volvo 汽车体验*

### <a name="use-holograms-to-modify-the-users-real-space"></a>全息用于修改用户的实际空间

另一种方法是使用全息修改用户的实际空间，用环境替换现有的墙或上限或追加洞或 windows，以允许过大的对象来看似中断-通过的物理空间。 例如，大型树可能不适合大多数用户的生活聊天室，但通过将虚拟天空放在其上限，物理空间将扩展为虚拟。 这允许用户以虚拟树中，基中四处走动和收集的小数位数如何它将出现在现实生活中，然后查找以查看其远远超过了此聊天室的物理空间扩展。

[Minecraft](https://minecraft.net/)开发使用类似的技术概念体验。 通过将虚拟窗口添加到聊天室中物理面，聊天室中的现有对象置于大得多的环境，房间的物理缩放限制之外的上下文中。

![HoloLens Minecraft 概念体验](images/800px-minecraftwindow-640px.jpg)<br>
*HoloLens Minecraft 概念体验*

## <a name="experimenting-with-scale"></a>用规模进行试验

在某些情况下，设计器体验过修改 （通过更改对象的显示的实际大小） 的规模，同时保持对象，以估计获取更近或更进一步的查看器，而无需任何实际移动的对象的单一位置。 这在某些情况下测试作为一种方法来模拟同时仍可以遵守潜在舒适限制查看虚拟内容不是建议舒适的"区域"更近的亲密接触查看项。

这可以在体验中创建几个可能的项目，但是所示：
* 对于某些对象的已知大小表示到查看器的虚拟对象，而更改的位置会导致冲突的视觉提示 – 眼睛可能仍然不更改缩放看到由于 vergence 提示某个深度处的对象 (请参阅[舒适](comfort.md)文章对此的详细信息)，但充当一个 monocular 提示，该对象可能会越来越接近目标大小。 这些冲突的提示会导致混淆认识 – 的查看者通常看到为保持在 （由于常量深度提示中） 的位置，但快速发展的对象。
* 在某些情况下，规模更改被视为临近提示改为，其中对象可能会或可能不会看到更改规模查看器中，但似乎是直接转向查看器的眼睛 （它可以是不喜欢成名）。
* 与现实世界中比较表面，这种缩放更改有时看到作为更改沿多个轴位置 – 对象可能看起来更低时删除而不是更接近移动 （在某些情况下的 3D 移动的 2D 投影中类似）。
* 最后，对于不含已知实际大小 （例如任意形状与任意大小、 UI 元素等） 的对象，更改规模作为一种方法来模拟距离中的更改可能会在功能上作用 – 的查看者不具有所依据的任意多个预先存在的自上而下的提示了解对象的实际大小或位置，以便规模可以作为一个更重要的提示进行处理。

## <a name="see-also"></a>请参阅
* [颜色、 光线和材料](color,-light-and-materials.md)
* [Typography](typography.md)
* [空间合理的设计](spatial-sound-design.md)
