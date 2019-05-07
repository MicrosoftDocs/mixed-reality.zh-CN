---
title: 案例研究-通查在现实中的漏洞
description: 本案例研究介绍如何实现对 HoloLens，允许用户查看墙壁、 floor、 下和其实际环境中的虚拟空缺到后面的"神奇窗口"影响。
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality HoloLens，神奇的窗口中，视差
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873929"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>案例研究-通查在现实中的漏洞

人们考虑混合的现实，他们可以使用 Microsoft HoloLens 所执行的操作，它们通常坚持问题如"什么对象添加到我的房间？" 或者"什么可以我基于我的空间？" 我想要突出显示您可以考虑的另一个区域 — 实质上是一招，使用相同的技术来查找到或通过围绕你的实际的物理对象。

## <a name="the-tech"></a>技术人员

如果您已遵循外星人，因为他们可以突破中挂历 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**，解锁安全的墙**[片段](case-study-creating-an-immersive-experience-in-fragments.md)**，或已足够幸运若要查看在 UNSC 无穷大 hangar  **[Halo 5 体验在 E3 中 2015年](https://www.youtube.com/watch?v=QDw5QjDtFy8)**，则您已了解我所讲述的内容。 根据您的想象力，来临时漏洞置于你砌干墙或隐藏在松散 floorboard 体系，可以使用此 visual 技巧。

![RoboRaid 添加三维管道和其他结构背后挂历，仅通过创建入侵者破坏漏洞可见。](images/roboraid-640px.png)

RoboRaid 添加三维管道和其他结构背后挂历，仅通过创建入侵者破坏漏洞可见。

在 HoloLens 上使用这些唯一全息之一，应用可以现实通过实际窗口显示的相同方法中提供内容，您墙壁后面或通过您的场所视觉的效果。 自行保留，移动，可以看到任何位于右侧。 获取更接近，并可以看到的所有内容的更多一些。 主要区别是，实际漏洞允许你通过，而您的场所仍会顽固地不会让您通过攀升至该神奇 holographic 内容。 （我将添加一项任务到积压工作。）

## <a name="behind-the-scenes"></a>幕后

此技巧是两个效果的组合。 首先，holographic 内容固定到世界上使用"空间定位点"。 使用定位点以使该内容"world 锁定"意味着，您正在寻找的内容并不直观地偏移离开物理对象附近，即使当你移动控件或基础空间映射系统更新你的聊天室其三维模型。

其次，该全息版的内容仅限于以可视方式非常特定的空间，因此您可以仅通过漏洞在现实中看到。 该封闭有必要需要仔细逻辑漏洞、 窗口或通道，销售技巧。 而无需阻止大多数视图的某些内容，对机密罗纪维度空间破裂只是看起来像效果不佳放置恢复不复存在。

![这不是实际的屏幕截图，但举例说明了从 MR 基础知识 101 机密 underworld 在 HoloLens 上的外观。 黑色的机箱不显示，但您所见的内容经过一个虚拟的孔。 （查看通过实际设备，floor 这看起来更消失，因为你自己的焦点在进一步距离如如果找不到甚至。）](images/origamiholecomposited-640px.png)

这不是实际的屏幕截图，但举例说明了如何从机密 underworld [MR 基础知识 101](holograms-101.md)在 HoloLens 上的外观。 黑色的机箱不显示，但您所见的内容经过一个虚拟的孔。 （查看通过实际设备，floor 这看起来更消失，因为你自己的焦点在进一步距离如如果找不到甚至。）

### <a name="world-locking-holographic-content"></a>世界锁定 holographic 内容

在 Unity 中，从而导致 holographic 内容保持世界锁定非常简单，只添加 WorldAnchor 组件：

```
myObject.AddComponent<WorldAnchor>();
```

WorldAnchor 组件不断将调整的位置和轮换其的 GameObject （以及任何其他层次结构中该对象之下） 以使其保持稳定相对于邻近的物理对象。 在创作时你的内容，则创建它的方式，在此虚拟孔居中对象的根数据透视。 （如果在墙上插座的深度中对象的透视，位置和旋转其细微调整将更加明显，并且漏洞不可能看起来非常稳定。）

### <a name="occluding-everything-but-the-virtual-hole"></a>Occluding 虚拟孔以外的所有内容

有多种方式来选择性地阻止到什么在挂历中隐藏的视图。 最简单的一个充分利用这一事实 HoloLens 使用累加性的显示模式，这意味着，完全黑色对象会出现不可见。 你可以在 Unity 中而无需执行任何特殊的着色器或材料技巧-只需创建黑色材料，并将其分配给你的内容中的对象。 如果您不想进行三维模型，只需使用少量的四核的默认对象并略有重叠。 有多种，此方法的缺点，但它是最快的方法，以便让某项工作，并获取低保真概念证明概念工作是太好了，即使你怀疑你可能想要更高版本重构。

上面的"黑盒"方法的一个主要缺点是不好拍照。 虽然看完美通过 HoloLens 的显示效果，您采取任何屏幕截图将显示而不是剩下的墙或下限的大黑色对象。 这样做的原因是，物理硬件和屏幕截图复合全息与现实以不同的方式。 让我们 detour 片刻到一些伪数学...

*伪数学警报 ！这些数字和公式是用来演示的点，不是任何类型的准确指标 ！*

您看到的内容通过 HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

您看到的内容中屏幕截图和视频：

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

英语：通过 HoloLens 看到的内容是简单的变暗现实情况 （例如，通过太阳镜） 和任何组合全息应用要显示。 但时拍摄屏幕快照，与每像素透明度值根据应用的全息混合照相机的映像。

若要避免这一问题的一种方法是更改"黑盒"材料以仅写入深度缓冲区，并与所有其他不透明材料进行排序。 有关此示例，请查看[MixedRealityToolkit 在 GitHub 上的 WindowOcclusion.shader 文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)。 相关行复制到此处：

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(请注意"偏移量 50，100"行是不相关的问题，因此可能最好省略的一些处理。)

类似的实现不可见的阻挡物材料将使您的应用程序绘制看起来和混合现实屏幕截图中显示正确的框。 对于奖励积分，可以尝试通过执行聪明操作绘制甚至更少的不可见像素，提高该框更进一步的性能但，实际上可以掌握井水并且通常不会有必要。

![下面是从 MR 基础知识 101 机密 underworld 如 Unity 绘制它的 occluding 框外部的部分除外。 请注意，underworld 的透视的框中，这有助于保持孔相对于实际 floor 尽可能。](images/underworld-occluded-640px.png)

下面是从机密 underworld [MR 基础知识 101](holograms-101.md)如 Unity 绘制它的 occluding 框外部的部分除外。 请注意，underworld 的透视的框中，这有助于保持孔相对于实际 floor 尽可能。

## <a name="do-it-yourself"></a>就自己动手

具有 HoloLens 和想要自行尝试效果？ 您可以执行 （无需编码） 的最简单操作是安装免费的三维查看器应用，然后加载[我已在 GitHub 提供的下载 the.fbx 文件](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow)在聊天室中查看花卉 pot 模型。 将其加载 HoloLens 上,，可以看到在工作效果。 该模型的前面时，只能看到插入小孔，其他所有内容均不可见。 从任何其他方查看模型，它将完全消失。 使用移动、 旋转和缩放控件的三维查看器来定位针对任何垂直的图面，您可以将生成的一些观点虚拟漏洞 ！

![在 Unity 编辑器中查看此模型将显示 flowerpot 周围的大黑色框。 HoloLens 上, 消失后框中，为提供为神奇窗口效果的方式。](images/magicwindowflowerpotineditor.png)

在 Unity 编辑器中查看此模型将显示 flowerpot 周围的大黑色框。 HoloLens 上, 消失后框中，为提供为神奇窗口效果的方式。

如果你想要生成使用此技术的应用程序，请查看[MR 基础知识 101 教程](holograms-101.md)中[混合现实教程](tutorials.md)。 第 7 章结尾中显示 （如图上面所示） 隐藏的 underworld 你 floor 爆炸式增长。 谁说教程必须令人厌烦？

以下是一些建议的位置执行这一想法下一步：
* 想一想如何使虚拟小孔里面的内容交互。 让你有超出其留言板一些影响的用户可以真正提高不足为奇了这一技巧可以提供有意义。
* 研究的方法，以查看通过返回到已知区域的对象。 例如，如何 holographic 孔置于咖啡表并查看其下的你 floor？

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>高级软件工程师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅
* [MR 基础知识 101：使用设备完成项目](holograms-101.md)
* [坐标系统](coordinate-systems.md)
* [空间定位点](spatial-anchors.md)
* [空间映射](spatial-mapping.md)
