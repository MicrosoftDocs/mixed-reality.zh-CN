---
title: 案例研究-在混合现实中创建 galaxy
description: 在发布 Microsoft HoloLens 之前，我们会询问开发人员社区要为新设备查看有经验的内部团队构建的应用类型。 共享了5000多个想法，在24小时的 Twitter 投票后，入选方是一个称为 "Galaxy 资源管理器" 的概念。
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy 资源管理器，HoloLens，Windows Mixed Reality，分享你的想法，案例研究
ms.openlocfilehash: f13395250c8a73718408c051ab95d2ec4bf62014
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278175"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>案例研究-在混合现实中创建 galaxy

在发布 Microsoft HoloLens 之前，我们会询问开发人员社区要为新设备查看有经验的内部团队构建的应用类型。 共享了5000多个想法，在24小时的 Twitter 投票后，入选方是一个称为[Galaxy 资源管理器](galaxy-explorer.md)的概念。

Zibits 是项目上的艺术线索，Karim Luccin，团队的图形工程师谈论的是在 "Galaxy 资源管理器" 中创建银河方法的精确、交互式表示形式的艺术与工程之间的协作工作。

## <a name="the-tech"></a>技术人员

[我们的团队](galaxy-explorer.md#meet-the-team)组成了两个开发人员：三个开发人员、四个艺术家、一个制造者和一个测试人员-有六周时间来构建一个完全功能的应用程序，该应用程序允许用户了解并探索银河的 vastness 和美。

我们想要充分利用 HoloLens 功能，以便在生活空间中直接呈现3D 对象，因此我们决定创建一个真实的 galaxy，用户可以在其中放大并查看单个星形，每个星都在各自的轨迹上。

在开发的第一周，我们提出了几个目标来实现银河的工作方式： Galaxy：它需要具有深度、移动和感觉容量耗尽，这将有助于创建 Galaxy 的形状。

创建具有数十亿星的动画 galaxy 的问题在于，每帧上需要更新的单个元素的数量可能会太大，而无法使用 CPU 进行动画处理。 我们的解决方案涉及复杂的艺术和科学组合。

## <a name="behind-the-scenes"></a>幕后

为了让人们能够浏览各个星，我们的第一步是确定我们可以一次呈现多少粒子。

### <a name="rendering-particles"></a>呈现粒子

当前 Cpu 非常适合用于处理串行任务，一次最多可执行几个并行任务（具体取决于它们具有的内核数），但 Gpu 在并行处理上千个操作时更为有效。 不过，由于它们通常不与 CPU 共享同一内存，因此在 CPU < > GPU 之间交换数据可能会很快成为瓶颈。 我们的解决方案是将 galaxy 置于 GPU 上，并且它必须完全在 GPU 上运行。

我们在各种模式中开始为成千上万点粒子进行压力测试。 这样，我们就可以在 HoloLens 上获得 galaxy，以查看工作情况和内容。

### <a name="creating-the-position-of-the-stars"></a>创建星形位置

我们的一位团队成员已经编写了C#在其最初位置生成星形的代码。 星形位于一个椭圆上，并且其位置可由（**curveOffset**， **ellipseSize**，**仰角**）描述，其中**curveOffset**是沿椭圆的星形的角度， **ellipseSize**是沿 X 和 Z 的椭圆的尺寸，并提升 galaxy 内星形的适当提升。 这样，我们可以创建一个缓冲区（[Unity 的 ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)），它将使用每个星型属性进行初始化，并将其发送到 GPU 上，以实现其余的体验。 若要绘制此缓冲区，我们使用[Unity 的 DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) ，它允许在任意一组点上运行着色器（代码），而无需使用表示 galaxy 的实际网格：

**CPU**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

我们从具有数千个粒子的原始循环模式开始。 这为我们提供了我们所需的证明，我们可以管理许多粒子，并以高性能的速度运行 为了改进形状，我们尝试了各种模式和粒子系统进行旋转。 最初，这是因为粒子数和性能保持一致，但形状会在靠近中心处分解，而星形却发出表面，但这并不切合现实。 我们需要一个发射，使我们能够处理时间，并使粒子真实地移动，这种循环会更接近 galaxy 中心。

![我们尝试了多个旋转的模式和粒子系统，如下所示。](images/galaxy-patterns-500px.png)

我们尝试了多个旋转的模式和粒子系统，如下所示。

我们的团队对 galaxies 函数的方式进行了一些研究，我们为 galaxy 专门提供了一个自定义的粒子系统，以便我们可以基于 "[密度波理论](https://en.wikipedia.org/wiki/Density_wave_theory)" 移动省略号，这 theorizes 了 galaxy 的作用是密度较高的区域，如流量堵塞。 它看起来稳定稳定，但当星形沿着各自的椭圆移动时，它们实际上会移入和移出扶手。 在我们的系统中，粒子永远不会存在于 CPU 上-我们会生成卡并在 GPU 上调整它们的方向，因此整个系统只是初始状态和时间。 如下所示：

![具有 GPU 呈现的粒子系统的进度](images/spiral-galaxy-arms-500px.jpg)

具有 GPU 呈现的粒子系统的进度


一旦添加了足够的省略号，并将其设置为旋转，galaxies 就会开始形成 "扶手"，其中星形的运动。 每个椭圆路径上的星形间距被赋予了一些随机性，并为每个星形增加了一个位置随机性。 这创建了一个更自然的星形运动和 arm 形状分布。 最后，我们添加了根据中心距离来驱动颜色的功能。

### <a name="creating-the-motion-of-the-stars"></a>创建星形运动

若要对一般星形运动进行动画处理，需要为每个帧添加一个恒定角度，并使星形沿着其椭圆沿固定径向速度移动。 这是使用**curveOffset**的主要原因。 从技术上看，这并不正确，因为星形会沿着省略号的长边移动

![在较长的弧线上，星形移动速度更快，但边缘速度更慢。](images/ellipse-movement.jpg)

在较长的弧线上，星形移动速度更快，但边缘速度更慢。


这样一来，每个星都由（**curveOffset**， **ellipseSize**，**提升**， **age**）全面描述，其中**Age**是自场景加载以来经过的总时间的累计。




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

这样一来，我们就可以在应用程序开始时生成数十个星，并沿着已建立的曲线对一组单的星形进行动画处理。 由于所有内容都在 GPU 上，因此系统可以将所有的星形并行动态地动态显示给 CPU。

![下面是绘制白色四边形时的样子。](images/drawing-white-quads-300px.jpg)

下面是绘制白色四边形时的样子。



为了使每个四颗面都为相机，我们使用几何着色器将每个星形位置转换为屏幕上将包含星形纹理的2D 矩形。

![菱形而不是四边形。](images/drawing-white-quads-300px.jpg)

菱形而不是四边形。


由于我们希望限制过度绘制（处理像素的次数），因此我们将四边形旋转，使其重叠越少。

### <a name="adding-clouds"></a>添加云

有很多方法可让你从一个卷内的 ray marching 中获取容量耗尽的感受，以尽可能多地绘制粒子来模拟云。 实时 ray marching 的成本太高，因此很难创作，因此，我们首先尝试使用一种用于在游戏中呈现林的方法来构建冒名顶替系统，这种方法适用于照相机。 当我们在游戏中执行此操作时，我们可以从相机中呈现出一个旋转的树纹理，保存所有这些图像，并在每个布告栏上运行时，选择与视图方向匹配的图像。 如果图像是全息影像，这也不起作用。 左眼和合适的眼睛之间的区别在于，这使得我们需要更高的分辨率，否则它只是平面、化名或重复。

第二次尝试时，尝试尽可能多的粒子。 最佳视觉对象是在将微粒添加到场景之前，添加性地绘制粒子并模糊。 此方法的典型问题与我们可以同时绘制多少粒子相关，同时还会保持60fps 的屏幕区域。 模糊生成的映像，使此云感觉通常是一种非常昂贵的操作。

![如果没有纹理，这就是云的外观，其中2% 不透明度。](images/clouds-without-texture-300px.jpg)

如果没有纹理，这就是云的外观，其中2% 不透明度。



如果是累加性的，其中有很多表示每个四边形有多个，则会对同一像素重复着色。 在 galaxy 的中心，相同的像素彼此之上有数百个四边形，在全屏显示时，这会产生巨大的成本。

执行全屏云并尝试对其进行模糊处理是一种不好的做法，因此，我们决定让硬件为我们完成工作。

### <a name="a-bit-of-context-first"></a>首先是一个上下文

当在游戏中使用纹理时，纹理大小很少与我们要在中使用的区域匹配，但我们可以使用不同种类的纹理筛选来使图形卡从纹理像素（[纹理筛选](https://msdn.microsoft.com/library/dn642451.aspx)）中插入所需的颜色。 对我们感兴趣的筛选是[双线性筛选](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)器，它将使用最接近的邻居计算任何像素的值。

![筛选前的原始](images/texture-1.png)

![筛选后的结果](images/texture-2.png)

使用此属性，我们发现每次尝试将纹理绘制到一个区域的两倍时，它将使结果模糊。

我们可能会在其他内容上进行操作，而不是呈现为全屏，而是不会出现在屏幕上，而是呈现给屏幕的小版本。 然后，通过复制此纹理并按2次因子拉伸它，我们将返回全屏，同时模糊处理过程中的内容。

![x3 upscale 返回到完整解决方案。](images/galaxy-resolutions-300px.png)

x3 upscale 返回到完整解决方案。



这样，我们就可以只使用一小部分原始成本来获取云部件。 我们只需绘制像素的 1/64th，而不是在完整的分辨率下添加云，只需将纹理拉伸回完整分辨率即可。

![Left，其中 upscale 从 1/8 到完全解析;右，使用2的幂2进行 3 upscale。](images/stars-upscaled-300px.jpg)

Left，其中 upscale 从 1/8 到完全解析;右，使用2的幂2进行 3 upscale。


请注意，尝试从大小的 1/64th 到一次的全尺寸看上去完全不同，因为图形卡仍会在我们的设置中使用4个像素来向更大的区域着色，并使项目开始显示。

然后，如果我们添加具有较小卡片的完整分辨率，则会获得完整的 galaxy：

![使用全分辨率星形的 galaxy 渲染接近最终结果](images/full-galaxy-500px.png)

完成形状的右跟踪后，我们添加了一层云，并将临时点换出到 Photoshop 中绘制的点，并添加了一些其他颜色。 结果就是一种银河的方法，Galaxy 我们的艺术和工程团队都认为是非常好的，并满足我们对 CPU 产生深刻的目标。

![三维中的最终银河方法。](images/final-galaxy-500px.jpg)

三维中的最终银河方法。


### <a name="more-to-explore"></a>了解更多

我们已经为 Galaxy 资源管理器应用程序提供了公开代码，并使其在[GitHub](https://github.com/Microsoft/GalaxyExplorer)上可供开发人员使用。

想要了解有关 Galaxy 资源管理器开发过程的详细信息？ 查看[Microsoft HoloLens YouTube 频道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)上的所有过去的项目更新。

## <a name="about-the-authors"></a>关于作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b>是一种软件工程师和别致的视觉对象爱好者。 他是用于 Galaxy 资源管理器的图形工程师。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Zibits</b>是一位艺术的线索和空间发烧，负责管理用于 Galaxy 资源管理器和孜孜以求的3d 建模团队，甚至更多粒子。</td>
</tr>
</table>


## <a name="see-also"></a>另请参阅
* [GitHub 上的 Galaxy 资源管理器](https://github.com/Microsoft/GalaxyExplorer)
* [YouTube 上的 Galaxy 资源管理器项目更新](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
