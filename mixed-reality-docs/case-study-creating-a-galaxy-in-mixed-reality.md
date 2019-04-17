---
title: 案例研究-混合现实中创建 galaxy
description: Microsoft HoloLens 之前，我们询问我们的开发人员社区应用哪种他们想要查看生成的新设备的资深内部团队。 共享 5000 个以上的想法，并在 24 小时 Twitter 投票中后, 入选方就称为"Galaxy 资源管理器。"了解
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy 资源管理器、 HoloLens、 Windows Mixed Reality 分享您的意见，案例研究
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593014"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>案例研究-混合现实中创建 galaxy

Microsoft HoloLens 之前，我们询问我们的开发人员社区应用哪种他们想要查看生成的新设备的资深内部团队。 共享 5000 个以上的想法，并后 24 小时 Twitter 轮询，获胜者是名为的想法[Galaxy 资源管理器](galaxy-explorer.md)。

Andy Zibits，项目，该艺术潜在顾客和 Karim Luccin，团队的图形工程师讨论之间这门艺术和银河系银河系 Galaxy 资源管理器中的准确、 交互式表示形式创建的工程伊始就展开协作。

## <a name="the-tech"></a>技术人员

[我们的团队](galaxy-explorer.md#meet-the-team)-组成的两个设计器、 三个开发人员、 四个艺术家、 生成者和一个测试人员，有六个星期来生成一个完全正常运行的应用程序，这将使人们能够了解和探索 vastness 和我们银河系 Galaxy 的优点。

我们想要充分利用 HoloLens 能够呈现直接在你的生活空间中三维对象，因此我们决定我们想要创建实际外观 galaxy 人员将能够放大关闭它们，查看各个星自己轨迹上的每个.

开发的第一周，我们想到了几个目标银河系 Galaxy 我们表示形式：需要有深度、 移动和容量耗尽感觉它 — 完整有助于形成 galaxy 星。

创建具有星的数十亿个动画的 galaxy 问题是，需要更新的单个元素的个数会太大，每一帧 HoloLens，若要使用 CPU 进行动画处理。 我们的解决方案涉及复杂混合门艺术和科学。

## <a name="behind-the-scenes"></a>幕后

若要允许用户浏览各个星，我们第一步是找出多少粒子我们可以立即呈现。

### <a name="rendering-particles"></a>呈现的粒子

当前 Cpu 非常适合处理串行任务和多达几个并行任务在一次 （具体取决于内核数它们有），但 Gpu 是能更有效地处理数千个并行操作。 但是，因为它们通常不共享相同的内存的 cpu，CPU <> GPU 之间交换数据可以会很快成为瓶颈。 我们的解决方案是使 galaxy 在 GPU 上，它必须完全存在于 GPU 上。

我们开始使用数以千计的各种模式中的点粒子的压力测试。 这使我们能够获取 galaxy 上 HoloLens，若要查看已提交和问题。

### <a name="creating-the-position-of-the-stars"></a>创建的星级的位置

我们的团队成员之一已编写C#会生成其初始位置处的星的代码。 星形上一个椭圆，并且可通过描述它们的位置 (**curveOffset**， **ellipseSize**，**提升**) 其中**curveOffset**是沿椭圆，在星型以角度**ellipseSize**是维度的椭圆形沿 X 和 Z，并提升银河系中的星号的适当权限提升。 因此，我们可以创建一个缓冲区 ([Unity 的 ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html))，将使用每个星型属性进行初始化，并将其发送它将实时体验的其余部分在 GPU 上。 若要绘制此缓冲区，我们使用[Unity 的 DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html)表示允许为运行着色器 （在 GPU 上代码） 一组任意点而无需表示 galaxy 实际网格：

**CPU:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

我们开始使用具有数千个粒子的原始循环模式。 这为我们提供我们需要我们可以管理多个粒子并运行它以高性能的速度，但我们并不满意 galaxy 的整体形状的证明。 若要提高该形状，我们尝试各种模式和旋转的粒子系统。 这些是已最初很有前景的因为粒子和性能的数量保持不一致，但该形状中心附近细分和星形所发出的表面上是不现实。 我们需要使我们能够将处理时间和具有实际上，移动粒子发出循环以往更接近于 galaxy 的中心。

![我们尝试各种模式和旋转，类似这样的粒子系统。](images/galaxy-patterns-500px.png)

我们尝试各种模式和旋转，类似这样的粒子系统。

我们的团队未方式星系函数有关的一些研究和我们所做的自定义粒子系统中的专门为 galaxy，以便我们可以基于椭圆移动粒子"[密度批理论](https://en.wikipedia.org/wiki/Density_wave_theory)，"这 theorizes 的武器galaxy 个方面的更高的密度，但在常量不断变化，例如交通堵塞。 它显示稳定和可靠，但随着沿其各自的省略号，星形实际移入和移出武器。 在我们的系统上的粒子永远不会存在在 CPU 上 — 我们生成卡和定位其所有在 GPU 上，因此整个系统是只是初始状态 + 的时间。 它的发展如下：

![粒子系统中使用 GPU 呈现的进度](images/spiral-galaxy-arms-500px.jpg)

粒子系统中使用 GPU 呈现的进度


足够省略号添加，且设置为旋转后, 星系开始到窗体"arm"其中的星级移动聚合。 每个椭圆路径上的星的间距提供了一些随机性和每个星型有少量的添加位置随机性。 这创建自然得多的移动和 arm 星形美观分发。 最后，我们增加了功能为驱动器颜色基于中心的距离。

### <a name="creating-the-motion-of-the-stars"></a>创建的星级的动作

要进行动画处理的常规的星型动作，我们需要添加每个帧常量角度并获取星级移动，再沿其省略号径向常量的速率。 这是使用的主要原因**curveOffset**。 这不是从技术上讲正确，因为星号将沿长边的省略号，更快地移动，但常规动作感觉很好。

![星更快地移动上长弧线，速度较慢的边缘上。](images/ellipse-movement.jpg)

星更快地移动上长弧线，速度较慢的边缘上。


这样，每个星型完全描述通过 (**curveOffset**， **ellipseSize**，**提升**，**年龄**) 其中**年龄**是自加载场景以来经过的总时间的累积。




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

这使我们能够生成数万个星级的应用程序，开始时一次，然后我们经过动画处理的一组一个沿建立曲线星。 由于所有内容均在 GPU 上，系统可以进行免费访问 CPU 的并行中的所有星星动画都处理。

![下面是其外观时绘制白色四边形。](images/drawing-white-quads-300px.jpg)

下面是其外观时绘制白色四边形。



若要使每个四核的人脸照相机，我们使用几何着色器来转换到 2D 矩形将包含我们星型纹理在屏幕上每个星型位置。

![而不是四边形方块。](images/drawing-white-quads-300px.jpg)

而不是四边形方块。


因为我们想要限制过度绘制 （次数将处理一个像素） 尽可能多地，我们旋转我们四边形，使其将具有较少重叠。

### <a name="adding-clouds"></a>添加云

有许多方法来获取与粒子容量耗尽感觉 — 从 ray 绘制任意多个粒子，以模拟云到 marching 内部卷。 实时 ray marching 将非常昂贵且难以作者，因此我们首先尝试构建冒名顶替者的系统使用一种方法用于在游戏中呈现林 — 包含大量的树对着相机的 2D 图像。 当我们执行此操作在游戏中时，我们可以具有旋转周围，保存所有这些映像，并在运行时为每个布告栏卡的摄像机从呈现树的纹理，选择匹配的视图方向的映像。 这不起作用也全息映像时。 左侧的眼睛和右侧的眼睛之间的差异，以便我们需要较多高的分辨率，否则它看起来扁平，有了别名，使其或重复。

在我们的第二次尝试，我们会尝试尽可能具有任意数量的粒子。 当我们附加绘制粒子和模糊之前将它们添加到场景来实现最佳的视觉对象。 这种方法的典型问题是我们无法一次绘制到多少相关的粒子和多少屏幕它们同时仍维护 60 fps 覆盖的区域。 模糊处理生成的映像，以获取您感到此云通常是非常高昂的操作。

![而无需纹理，这是云 2%不透明度为如下。](images/clouds-without-texture-300px.jpg)

而无需纹理，这是云 2%不透明度为如下。



要附加的有很多这些意味着，我们将具有多个四边形彼此，反复明暗度的同一像素。 在 galaxy 的中央，同一像素有数百个彼此的四边形，并正在完成整个屏幕，这会造成大量成本。

执行全屏幕云，并且使它们变得模糊就已一个好主意，因此，我们决定让我们完成工作的硬件。

### <a name="a-bit-of-context-first"></a>上下文的前一个位。

在游戏中使用的纹理时纹理大小将很少与匹配的区域，我们想要使用它，但我们可以使用不同类型的纹理筛选，以获取图形卡来内插我们想要从纹理的像素的颜色 ([纹理筛选<c3/1>)。 我们感兴趣，筛选[双线性筛选](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)将计算使用最近近邻 4 任何像素的值。

![原始再进行筛选](images/texture-1.png)

![筛选之后](images/texture-2.png)

使用此属性，我们可以看到，我们尝试到两倍大，一个区域中绘制纹理每次地进行模糊结果。

而不是全屏幕上呈现，并会丢失这些宝贵的毫秒数，我们可能会花费在别的事情，我们呈现到屏幕的小版本。 然后，通过复制此纹理并不对其进行延伸到原来的 2 几次，我们会与全屏幕模糊过程中的内容时。

![x3 放大返回到完整的解决方法。](images/galaxy-resolutions-300px.png)

x3 放大返回到完整的解决方法。



这使我们能够获取与仅的原始成本的一小部分的云部分。 而不是添加云上的完整分辨率，我们仅画图 1/64th 的像素为单位，这只延伸到高分辨率的纹理。

![左侧，具有高端 1/8 到完全解决功能;和向右、 高端 3 使用 2 的幂。](images/stars-upscaled-300px.jpg)

左侧，具有高端 1/8 到完全解决功能;和向右、 高端 3 使用 2 的幂。


请注意该尝试从 1/64th 到完整大小的一次性的大小将看起来完全不同，因为图形卡仍然可以使用 4 个像素在我们的设置来为较大区域添加底纹和项目开始显示。

然后，如果我们有较小的卡添加完整分辨率星，我们获取完整 galaxy:

![附近星系呈现使用全分辨率星的最终结果](images/full-galaxy-500px.png)

一旦我们已与该形状的右轨上，我们添加了一层的云，换出的临时点与我们在 Photoshop 中，绘制并添加了一些其他的颜色。 结果是银河系 Galaxy 我们艺术和工程这两个团队认为的好处以及它符合我们的目标的深度、 卷和动作 — 所有不浪费 CPU。

![在 3D 我们最终银河系 Galaxy。](images/final-galaxy-500px.jpg)

在 3D 我们最终银河系 Galaxy。


### <a name="more-to-explore"></a>了解更多内容

我们已开放源代码 Galaxy 资源管理器应用程序的代码并使其能够在[GitHub](https://github.com/Microsoft/GalaxyExplorer)开发人员可以构建。

是否有兴趣了解有关在开发过程的详细信息 Galaxy 资源管理器？ 请查看所有我们过去项目上的更新[Microsoft HoloLens YouTube 频道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)。

## <a name="about-the-authors"></a>关于作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b>是软件工程师和精美的视觉对象酷爱钻研技术。 他是 Galaxy 资源管理器图形工程师。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b>是 for Galaxy 资源管理器管理三维建模团队，并遵循有关更多粒子艺术潜在顾客和空间爱好者。</td>
</tr>
</table>


## <a name="see-also"></a>请参阅
* [Galaxy GitHub 上的资源管理器](https://github.com/Microsoft/GalaxyExplorer)
* [YouTube 上的 Galaxy 资源管理器项目更新](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
