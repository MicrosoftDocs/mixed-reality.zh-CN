---
title: 案例研究-查看现实中的洞
description: 此案例研究介绍了如何在 HoloLens 上实现 "神奇窗口" 效果，使用户能够在其实际环境中的墙壁后面、在地面下和虚拟空缺之间进行观看。
author: EricRehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，幻窗口，视差
ms.openlocfilehash: a1b9f0b2e576379846a867f3d3bffef7d8ec277e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436664"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>案例研究-查看现实中的洞

当人们考虑混合现实以及他们可以通过 Microsoft HoloLens 实现哪些功能时，他们通常会坚持 "我可以将哪些对象添加到我的聊天室？" 之类的问题。 或者 "我可以在我的空间之上分层什么？" 我想突出显示另一个可以考虑的领域，这是一种非常神奇的技巧，使用相同的技术来查找或通过围绕您的真实物理对象。

## <a name="the-tech"></a>技术人员

如果已孜孜以求外星人，因为它们中断了 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 中的墙壁，解锁了 **[片段](case-study-creating-an-immersive-experience-in-fragments.md)** 中的墙安全功能，或者在 **[2015 的 E3 中](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 有足够的时间来查看 hangar 的 根据您的想像，此视觉对象可用于在您的饰面中放置临时孔，或在松散 floorboard 下隐藏世界。

![RoboRaid 将三维管道和其他结构添加到墙壁后面，只能通过创建为太空 break 的孔进行查看。](images/roboraid-640px.png)

RoboRaid 将三维管道和其他结构添加到墙壁后面，只能通过创建为太空 break 的孔进行查看。

在 HoloLens 上使用其中一个独特的全息影像，应用程序可以通过实际的窗口以真实表现的方式为你的墙壁或地面提供内容的错觉。 向左移动，您可以看到右侧的内容。 深入了解，你可以更深入地了解所有内容。 主要区别在于真实的洞能让你完成，而地面顽固地不会让你经过神奇全息内容。 （我会将任务添加到积压工作（backlog）。）

## <a name="behind-the-scenes"></a>幕后

这一技巧组合了两个效果。 首先，使用 "空间锚点" 将全息内容固定到世界。 使用定位点来使内容 "世界锁定" 意味着你要查看的内容不会在视觉上偏离其附近的物理对象，即使你移动或基础空间映射系统会更新其3D 模型。

其次，全息内容在外观上仅限于特定空间，因此，你只能在现实中看到该洞。 这封闭是需要通过逻辑洞、窗户或门口（销售这一墩）来进行的。 如果没有任何内容阻碍了视图，则将空间破解到机密 Jurassic 维度可能看起来就像是一个不良的分块。

![这并不是实际的屏幕截图，而是说明来自 MR underworld 的机密如何101在 HoloLens 上的外观。 黑色机箱未显示，但你可以通过虚拟孔查看内容。 （在查找实际设备时，地面似乎会消失，因为你的眼睛会显得更远一点，就像根本不会那样。）](images/origamiholecomposited-640px.png)

这并不是实际的屏幕截图，而是对来自[MR 基础知识 101](holograms-101.md)的机密 underworld 的说明。 黑色机箱未显示，但你可以通过虚拟孔查看内容。 （在查找实际设备时，地面似乎会消失，因为你的眼睛会显得更远一点，就像根本不会那样。）

### <a name="world-locking-holographic-content"></a>全球锁定全息内容

在 Unity 中，导致全息内容保持世界锁定状态与添加 WorldAnchor 组件一样简单：

```
myObject.AddComponent<WorldAnchor>();
```

WorldAnchor 组件将不断调整其 GameObject 的位置和旋转（以及该对象在层次结构中的任何其他内容），使其相对于附近的物理对象保持稳定。 创作你的内容时，请以这种方式创建你的对象的根透视，使其在此虚拟洞上居中。 （如果您的对象的透视是墙中的深度，则其位置和旋转的轻微调整会更明显，并且该孔可能看起来不稳定。）

### <a name="occluding-everything-but-the-virtual-hole"></a>Occluding 除虚拟洞以外的所有内容

有多种方法可以有选择地阻止在墙壁中隐藏的内容。 最简单的一种方法是使用 HoloLens 使用加法显示这一事实，这意味着完全的黑色对象会显示为不可见。 您可以在 Unity 中执行此操作，而无需执行任何特殊着色器或材料技巧—只需创建黑色材料，并将其分配给内容中的框。 如果你不想进行3D 建模，只需使用少量的默认四个对象并略微重叠它们。 这种方法有很多缺点，但它是实现工作的最快方法，即使您怀疑以后可能需要重构它，也可以使用最快的概念证明。

上面的 "黑箱" 方法的一个主要缺点是它没有太好的照片。 尽管你的效果可能会通过显示 HoloLens 看起来很完美，但你所做的任何屏幕截图都将显示较大的黑色对象，而不是墙或地面的内容。 导致这种情况的原因是物理硬件和屏幕截图的组合影像和实际情况有所不同。 让我们 detour 一些虚假的数学 。

*伪数学警报！这些数字和公式旨在说明点，而不是任何种类的准确指标！*

通过 HoloLens 查看的内容：

```
( Reality * darkening_amount ) + Holograms
```

在屏幕截图和视频中看到的内容：

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

使用英语：通过 HoloLens 看到的内容是变暗的现实（如通过太阳镜）和应用想要显示的任何全息影像的简单组合。 但在拍摄屏幕截图时，照相机的图像会根据每像素的透明度值与应用的全息影像混合。

解决这种情况的一种方法是将 "黑色框" 材料改为仅写入深度缓冲区，并将所有其他的不透明材料进行排序。 有关这种情况的示例，请查看[GitHub 上的 MixedRealityToolkit 中的 WindowOcclusion 文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)。 相关行复制如下：

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

（请注意，"偏移50，100" 行用于处理不相关的问题，因此，可能有必要将其退出。）

实现一种不可见的封闭材料，使您的应用程序能够绘制一个在显示和混合现实屏幕截图中显示正确的框。 对于附赠点，您可以尝试进一步提高此框的性能，方法是通过进行巧妙地绘制更少的不可见像素来更好地绘制，但这种方法实际上不是必需的。

![下面是来自 MR 基础知识101的机密 underworld，因为 Unity 会绘制该机密，但 occluding 框的外部部分除外。 请注意，underworld 的透视是在该框的中心，这有助于使洞相对于实际楼层尽可能稳定。](images/underworld-occluded-640px.png)

下面是来自[MR 基础知识 101](holograms-101.md)的机密 underworld，因为 Unity 会绘制该机密，但 occluding 框的外部部分除外。 请注意，underworld 的透视是在该框的中心，这有助于使洞相对于实际楼层尽可能稳定。

## <a name="do-it-yourself"></a>自行完成

有一个 HoloLens，想要亲自尝试自己的效果吗？ 您可以执行的最简单操作（无需编码）是安装免费的3D 查看器应用程序，然后加载在[GitHub 上提供的 fbx 文件](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow)，以便在房间中查看花卉模型。 将其加载到 HoloLens 上，你可以看到工作的错觉。 在模型的前面，只能看到 "小" 洞面，其他所有内容都不可见。 从任何其他端查看模型，它将完全消失。 使用3D 查看器的移动、旋转和缩放控件，将虚拟孔洞定位到可以考虑生成某些创意的任何垂直表面上！

![在 Unity 编辑器中查看此模型将在 flowerpot 周围显示大的黑色框。 在 HoloLens 上，此框消失，为神奇窗口效果提供。](images/magicwindowflowerpotineditor.png)

在 Unity 编辑器中查看此模型将在 flowerpot 周围显示大的黑色框。 在 HoloLens 上，此框消失，为神奇窗口效果提供。

如果要构建使用此技术的应用，请在[混合现实教程](tutorials.md)中查看[MR 基本101教程](holograms-101.md)。 第7章以地面分离，其中显示了隐藏的 underworld （如上图所示）。 谁说教程必须是枯燥的呢？

下面是一些你可以在其中执行此操作的一些建议：
* 考虑使虚拟洞内内容成为交互的方式。 让您的用户在其墙外产生一定的影响，可以真正提高此技巧可以提供的意义。
* 考虑通过对象查看到已知区域的方法。 例如，如何在咖啡表中放入全息孔并查看其下的地面？

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>高级软件工程师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅
* [MR 基本101：通过设备完成项目](holograms-101.md)
* [坐标系统](coordinate-systems.md)
* [空间定位点](spatial-anchors.md)
* [空间映射](spatial-mapping.md)
