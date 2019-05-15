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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593014"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="14d0c-105">案例研究-混合现实中创建 galaxy</span><span class="sxs-lookup"><span data-stu-id="14d0c-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="14d0c-106">Microsoft HoloLens 之前，我们询问我们的开发人员社区应用哪种他们想要查看生成的新设备的资深内部团队。</span><span class="sxs-lookup"><span data-stu-id="14d0c-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="14d0c-107">共享 5000 个以上的想法，并后 24 小时 Twitter 轮询，获胜者是名为的想法[Galaxy 资源管理器](galaxy-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="14d0c-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="14d0c-108">Andy Zibits，项目，该艺术潜在顾客和 Karim Luccin，团队的图形工程师讨论之间这门艺术和银河系银河系 Galaxy 资源管理器中的准确、 交互式表示形式创建的工程伊始就展开协作。</span><span class="sxs-lookup"><span data-stu-id="14d0c-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="14d0c-109">技术人员</span><span class="sxs-lookup"><span data-stu-id="14d0c-109">The Tech</span></span>

<span data-ttu-id="14d0c-110">[我们的团队](galaxy-explorer.md#meet-the-team)-组成的两个设计器、 三个开发人员、 四个艺术家、 生成者和一个测试人员，有六个星期来生成一个完全正常运行的应用程序，这将使人们能够了解和探索 vastness 和我们银河系 Galaxy 的优点。</span><span class="sxs-lookup"><span data-stu-id="14d0c-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="14d0c-111">我们想要充分利用 HoloLens 能够呈现直接在你的生活空间中三维对象，因此我们决定我们想要创建实际外观 galaxy 人员将能够放大关闭它们，查看各个星自己轨迹上的每个.</span><span class="sxs-lookup"><span data-stu-id="14d0c-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="14d0c-112">开发的第一周，我们想到了几个目标银河系 Galaxy 我们表示形式：需要有深度、 移动和容量耗尽感觉它 — 完整有助于形成 galaxy 星。</span><span class="sxs-lookup"><span data-stu-id="14d0c-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="14d0c-113">创建具有星的数十亿个动画的 galaxy 问题是，需要更新的单个元素的个数会太大，每一帧 HoloLens，若要使用 CPU 进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="14d0c-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="14d0c-114">我们的解决方案涉及复杂混合门艺术和科学。</span><span class="sxs-lookup"><span data-stu-id="14d0c-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="14d0c-115">幕后</span><span class="sxs-lookup"><span data-stu-id="14d0c-115">Behind the scenes</span></span>

<span data-ttu-id="14d0c-116">若要允许用户浏览各个星，我们第一步是找出多少粒子我们可以立即呈现。</span><span class="sxs-lookup"><span data-stu-id="14d0c-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="14d0c-117">呈现的粒子</span><span class="sxs-lookup"><span data-stu-id="14d0c-117">Rendering particles</span></span>

<span data-ttu-id="14d0c-118">当前 Cpu 非常适合处理串行任务和多达几个并行任务在一次 （具体取决于内核数它们有），但 Gpu 是能更有效地处理数千个并行操作。</span><span class="sxs-lookup"><span data-stu-id="14d0c-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="14d0c-119">但是，因为它们通常不共享相同的内存的 cpu，CPU <> GPU 之间交换数据可以会很快成为瓶颈。</span><span class="sxs-lookup"><span data-stu-id="14d0c-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="14d0c-120">我们的解决方案是使 galaxy 在 GPU 上，它必须完全存在于 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="14d0c-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="14d0c-121">我们开始使用数以千计的各种模式中的点粒子的压力测试。</span><span class="sxs-lookup"><span data-stu-id="14d0c-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="14d0c-122">这使我们能够获取 galaxy 上 HoloLens，若要查看已提交和问题。</span><span class="sxs-lookup"><span data-stu-id="14d0c-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="14d0c-123">创建的星级的位置</span><span class="sxs-lookup"><span data-stu-id="14d0c-123">Creating the position of the stars</span></span>

<span data-ttu-id="14d0c-124">我们的团队成员之一已编写C#会生成其初始位置处的星的代码。</span><span class="sxs-lookup"><span data-stu-id="14d0c-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="14d0c-125">星形上一个椭圆，并且可通过描述它们的位置 (**curveOffset**， **ellipseSize**，**提升**) 其中**curveOffset**是沿椭圆，在星型以角度**ellipseSize**是维度的椭圆形沿 X 和 Z，并提升银河系中的星号的适当权限提升。</span><span class="sxs-lookup"><span data-stu-id="14d0c-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="14d0c-126">因此，我们可以创建一个缓冲区 ([Unity 的 ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html))，将使用每个星型属性进行初始化，并将其发送它将实时体验的其余部分在 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="14d0c-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="14d0c-127">若要绘制此缓冲区，我们使用[Unity 的 DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html)表示允许为运行着色器 （在 GPU 上代码） 一组任意点而无需表示 galaxy 实际网格：</span><span class="sxs-lookup"><span data-stu-id="14d0c-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="14d0c-128">**CPU:**</span><span class="sxs-lookup"><span data-stu-id="14d0c-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="14d0c-129">**GPU:**</span><span class="sxs-lookup"><span data-stu-id="14d0c-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="14d0c-130">我们开始使用具有数千个粒子的原始循环模式。</span><span class="sxs-lookup"><span data-stu-id="14d0c-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="14d0c-131">这为我们提供我们需要我们可以管理多个粒子并运行它以高性能的速度，但我们并不满意 galaxy 的整体形状的证明。</span><span class="sxs-lookup"><span data-stu-id="14d0c-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="14d0c-132">若要提高该形状，我们尝试各种模式和旋转的粒子系统。</span><span class="sxs-lookup"><span data-stu-id="14d0c-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="14d0c-133">这些是已最初很有前景的因为粒子和性能的数量保持不一致，但该形状中心附近细分和星形所发出的表面上是不现实。</span><span class="sxs-lookup"><span data-stu-id="14d0c-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="14d0c-134">我们需要使我们能够将处理时间和具有实际上，移动粒子发出循环以往更接近于 galaxy 的中心。</span><span class="sxs-lookup"><span data-stu-id="14d0c-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![我们尝试各种模式和旋转，类似这样的粒子系统。](images/galaxy-patterns-500px.png)

<span data-ttu-id="14d0c-136">我们尝试各种模式和旋转，类似这样的粒子系统。</span><span class="sxs-lookup"><span data-stu-id="14d0c-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="14d0c-137">我们的团队未方式星系函数有关的一些研究和我们所做的自定义粒子系统中的专门为 galaxy，以便我们可以基于椭圆移动粒子"[密度批理论](https://en.wikipedia.org/wiki/Density_wave_theory)，"这 theorizes 的武器galaxy 个方面的更高的密度，但在常量不断变化，例如交通堵塞。</span><span class="sxs-lookup"><span data-stu-id="14d0c-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="14d0c-138">它显示稳定和可靠，但随着沿其各自的省略号，星形实际移入和移出武器。</span><span class="sxs-lookup"><span data-stu-id="14d0c-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="14d0c-139">在我们的系统上的粒子永远不会存在在 CPU 上 — 我们生成卡和定位其所有在 GPU 上，因此整个系统是只是初始状态 + 的时间。</span><span class="sxs-lookup"><span data-stu-id="14d0c-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="14d0c-140">它的发展如下：</span><span class="sxs-lookup"><span data-stu-id="14d0c-140">It progressed like this:</span></span>

![粒子系统中使用 GPU 呈现的进度](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="14d0c-142">粒子系统中使用 GPU 呈现的进度</span><span class="sxs-lookup"><span data-stu-id="14d0c-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="14d0c-143">足够省略号添加，且设置为旋转后, 星系开始到窗体"arm"其中的星级移动聚合。</span><span class="sxs-lookup"><span data-stu-id="14d0c-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="14d0c-144">每个椭圆路径上的星的间距提供了一些随机性和每个星型有少量的添加位置随机性。</span><span class="sxs-lookup"><span data-stu-id="14d0c-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="14d0c-145">这创建自然得多的移动和 arm 星形美观分发。</span><span class="sxs-lookup"><span data-stu-id="14d0c-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="14d0c-146">最后，我们增加了功能为驱动器颜色基于中心的距离。</span><span class="sxs-lookup"><span data-stu-id="14d0c-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="14d0c-147">创建的星级的动作</span><span class="sxs-lookup"><span data-stu-id="14d0c-147">Creating the motion of the stars</span></span>

<span data-ttu-id="14d0c-148">要进行动画处理的常规的星型动作，我们需要添加每个帧常量角度并获取星级移动，再沿其省略号径向常量的速率。</span><span class="sxs-lookup"><span data-stu-id="14d0c-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="14d0c-149">这是使用的主要原因**curveOffset**。</span><span class="sxs-lookup"><span data-stu-id="14d0c-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="14d0c-150">这不是从技术上讲正确，因为星号将沿长边的省略号，更快地移动，但常规动作感觉很好。</span><span class="sxs-lookup"><span data-stu-id="14d0c-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![星更快地移动上长弧线，速度较慢的边缘上。](images/ellipse-movement.jpg)

<span data-ttu-id="14d0c-152">星更快地移动上长弧线，速度较慢的边缘上。</span><span class="sxs-lookup"><span data-stu-id="14d0c-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="14d0c-153">这样，每个星型完全描述通过 (**curveOffset**， **ellipseSize**，**提升**，**年龄**) 其中**年龄**是自加载场景以来经过的总时间的累积。</span><span class="sxs-lookup"><span data-stu-id="14d0c-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="14d0c-154">这使我们能够生成数万个星级的应用程序，开始时一次，然后我们经过动画处理的一组一个沿建立曲线星。</span><span class="sxs-lookup"><span data-stu-id="14d0c-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="14d0c-155">由于所有内容均在 GPU 上，系统可以进行免费访问 CPU 的并行中的所有星星动画都处理。</span><span class="sxs-lookup"><span data-stu-id="14d0c-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![下面是其外观时绘制白色四边形。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="14d0c-157">下面是其外观时绘制白色四边形。</span><span class="sxs-lookup"><span data-stu-id="14d0c-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="14d0c-158">若要使每个四核的人脸照相机，我们使用几何着色器来转换到 2D 矩形将包含我们星型纹理在屏幕上每个星型位置。</span><span class="sxs-lookup"><span data-stu-id="14d0c-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![而不是四边形方块。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="14d0c-160">而不是四边形方块。</span><span class="sxs-lookup"><span data-stu-id="14d0c-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="14d0c-161">因为我们想要限制过度绘制 （次数将处理一个像素） 尽可能多地，我们旋转我们四边形，使其将具有较少重叠。</span><span class="sxs-lookup"><span data-stu-id="14d0c-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="14d0c-162">添加云</span><span class="sxs-lookup"><span data-stu-id="14d0c-162">Adding clouds</span></span>

<span data-ttu-id="14d0c-163">有许多方法来获取与粒子容量耗尽感觉 — 从 ray 绘制任意多个粒子，以模拟云到 marching 内部卷。</span><span class="sxs-lookup"><span data-stu-id="14d0c-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="14d0c-164">实时 ray marching 将非常昂贵且难以作者，因此我们首先尝试构建冒名顶替者的系统使用一种方法用于在游戏中呈现林 — 包含大量的树对着相机的 2D 图像。</span><span class="sxs-lookup"><span data-stu-id="14d0c-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="14d0c-165">当我们执行此操作在游戏中时，我们可以具有旋转周围，保存所有这些映像，并在运行时为每个布告栏卡的摄像机从呈现树的纹理，选择匹配的视图方向的映像。</span><span class="sxs-lookup"><span data-stu-id="14d0c-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="14d0c-166">这不起作用也全息映像时。</span><span class="sxs-lookup"><span data-stu-id="14d0c-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="14d0c-167">左侧的眼睛和右侧的眼睛之间的差异，以便我们需要较多高的分辨率，否则它看起来扁平，有了别名，使其或重复。</span><span class="sxs-lookup"><span data-stu-id="14d0c-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="14d0c-168">在我们的第二次尝试，我们会尝试尽可能具有任意数量的粒子。</span><span class="sxs-lookup"><span data-stu-id="14d0c-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="14d0c-169">当我们附加绘制粒子和模糊之前将它们添加到场景来实现最佳的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="14d0c-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="14d0c-170">这种方法的典型问题是我们无法一次绘制到多少相关的粒子和多少屏幕它们同时仍维护 60 fps 覆盖的区域。</span><span class="sxs-lookup"><span data-stu-id="14d0c-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="14d0c-171">模糊处理生成的映像，以获取您感到此云通常是非常高昂的操作。</span><span class="sxs-lookup"><span data-stu-id="14d0c-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![而无需纹理，这是云 2%不透明度为如下。](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="14d0c-173">而无需纹理，这是云 2%不透明度为如下。</span><span class="sxs-lookup"><span data-stu-id="14d0c-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="14d0c-174">要附加的有很多这些意味着，我们将具有多个四边形彼此，反复明暗度的同一像素。</span><span class="sxs-lookup"><span data-stu-id="14d0c-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="14d0c-175">在 galaxy 的中央，同一像素有数百个彼此的四边形，并正在完成整个屏幕，这会造成大量成本。</span><span class="sxs-lookup"><span data-stu-id="14d0c-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="14d0c-176">执行全屏幕云，并且使它们变得模糊就已一个好主意，因此，我们决定让我们完成工作的硬件。</span><span class="sxs-lookup"><span data-stu-id="14d0c-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="14d0c-177">上下文的前一个位。</span><span class="sxs-lookup"><span data-stu-id="14d0c-177">A bit of context first</span></span>

<span data-ttu-id="14d0c-178">在游戏中使用的纹理时纹理大小将很少与匹配的区域，我们想要使用它，但我们可以使用不同类型的纹理筛选，以获取图形卡来内插我们想要从纹理的像素的颜色 ([纹理筛选](https://msdn.microsoft.com/library/dn642451.aspx))。</span><span class="sxs-lookup"><span data-stu-id="14d0c-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="14d0c-179">我们感兴趣，筛选[双线性筛选](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)将计算使用最近近邻 4 任何像素的值。</span><span class="sxs-lookup"><span data-stu-id="14d0c-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![原始再进行筛选](images/texture-1.png)

![筛选之后](images/texture-2.png)

<span data-ttu-id="14d0c-182">使用此属性，我们可以看到，我们尝试到两倍大，一个区域中绘制纹理每次地进行模糊结果。</span><span class="sxs-lookup"><span data-stu-id="14d0c-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="14d0c-183">而不是全屏幕上呈现，并会丢失这些宝贵的毫秒数，我们可能会花费在别的事情，我们呈现到屏幕的小版本。</span><span class="sxs-lookup"><span data-stu-id="14d0c-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="14d0c-184">然后，通过复制此纹理并不对其进行延伸到原来的 2 几次，我们会与全屏幕模糊过程中的内容时。</span><span class="sxs-lookup"><span data-stu-id="14d0c-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 放大返回到完整的解决方法。](images/galaxy-resolutions-300px.png)

<span data-ttu-id="14d0c-186">x3 放大返回到完整的解决方法。</span><span class="sxs-lookup"><span data-stu-id="14d0c-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="14d0c-187">这使我们能够获取与仅的原始成本的一小部分的云部分。</span><span class="sxs-lookup"><span data-stu-id="14d0c-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="14d0c-188">而不是添加云上的完整分辨率，我们仅画图 1/64th 的像素为单位，这只延伸到高分辨率的纹理。</span><span class="sxs-lookup"><span data-stu-id="14d0c-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![左侧，具有高端 1/8 到完全解决功能;和向右、 高端 3 使用 2 的幂。](images/stars-upscaled-300px.jpg)

<span data-ttu-id="14d0c-190">左侧，具有高端 1/8 到完全解决功能;和向右、 高端 3 使用 2 的幂。</span><span class="sxs-lookup"><span data-stu-id="14d0c-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="14d0c-191">请注意该尝试从 1/64th 到完整大小的一次性的大小将看起来完全不同，因为图形卡仍然可以使用 4 个像素在我们的设置来为较大区域添加底纹和项目开始显示。</span><span class="sxs-lookup"><span data-stu-id="14d0c-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="14d0c-192">然后，如果我们有较小的卡添加完整分辨率星，我们获取完整 galaxy:</span><span class="sxs-lookup"><span data-stu-id="14d0c-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![附近星系呈现使用全分辨率星的最终结果](images/full-galaxy-500px.png)

<span data-ttu-id="14d0c-194">一旦我们已与该形状的右轨上，我们添加了一层的云，换出的临时点与我们在 Photoshop 中，绘制并添加了一些其他的颜色。</span><span class="sxs-lookup"><span data-stu-id="14d0c-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="14d0c-195">结果是银河系 Galaxy 我们艺术和工程这两个团队认为的好处以及它符合我们的目标的深度、 卷和动作 — 所有不浪费 CPU。</span><span class="sxs-lookup"><span data-stu-id="14d0c-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![在 3D 我们最终银河系 Galaxy。](images/final-galaxy-500px.jpg)

<span data-ttu-id="14d0c-197">在 3D 我们最终银河系 Galaxy。</span><span class="sxs-lookup"><span data-stu-id="14d0c-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="14d0c-198">了解更多内容</span><span class="sxs-lookup"><span data-stu-id="14d0c-198">More to explore</span></span>

<span data-ttu-id="14d0c-199">我们已开放源代码 Galaxy 资源管理器应用程序的代码并使其能够在[GitHub](https://github.com/Microsoft/GalaxyExplorer)开发人员可以构建。</span><span class="sxs-lookup"><span data-stu-id="14d0c-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="14d0c-200">是否有兴趣了解有关在开发过程的详细信息 Galaxy 资源管理器？</span><span class="sxs-lookup"><span data-stu-id="14d0c-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="14d0c-201">请查看所有我们过去项目上的更新[Microsoft HoloLens YouTube 频道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)。</span><span class="sxs-lookup"><span data-stu-id="14d0c-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="14d0c-202">关于作者</span><span class="sxs-lookup"><span data-stu-id="14d0c-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="14d0c-203"><b>Karim Luccin</b>是软件工程师和精美的视觉对象酷爱钻研技术。</span><span class="sxs-lookup"><span data-stu-id="14d0c-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="14d0c-204">他是 Galaxy 资源管理器图形工程师。</span><span class="sxs-lookup"><span data-stu-id="14d0c-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="14d0c-205"><b>Andy Zibits</b>是 for Galaxy 资源管理器管理三维建模团队，并遵循有关更多粒子艺术潜在顾客和空间爱好者。</span><span class="sxs-lookup"><span data-stu-id="14d0c-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="14d0c-206">请参阅</span><span class="sxs-lookup"><span data-stu-id="14d0c-206">See also</span></span>
* [<span data-ttu-id="14d0c-207">Galaxy GitHub 上的资源管理器</span><span class="sxs-lookup"><span data-stu-id="14d0c-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="14d0c-208">YouTube 上的 Galaxy 资源管理器项目更新</span><span class="sxs-lookup"><span data-stu-id="14d0c-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
