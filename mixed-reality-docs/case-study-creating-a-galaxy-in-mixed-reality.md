---
title: 案例研究-在混合现实中创建 galaxy
description: 在发布 Microsoft HoloLens 之前, 我们会询问开发人员社区要为新设备查看有经验的内部团队构建的应用类型。 共享了5000多个想法, 在24小时的 Twitter 投票后, 入选方是一个称为 "Galaxy 资源管理器" 的概念。
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy 资源管理器, HoloLens, Windows Mixed Reality, 分享你的想法, 案例研究
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523771"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="5efcf-105">案例研究-在混合现实中创建 galaxy</span><span class="sxs-lookup"><span data-stu-id="5efcf-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="5efcf-106">在发布 Microsoft HoloLens 之前, 我们会询问开发人员社区要为新设备查看有经验的内部团队构建的应用类型。</span><span class="sxs-lookup"><span data-stu-id="5efcf-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="5efcf-107">共享了5000多个想法, 在24小时的 Twitter 投票后, 入选方是一个称为[Galaxy 资源管理器](galaxy-explorer.md)的概念。</span><span class="sxs-lookup"><span data-stu-id="5efcf-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="5efcf-108">Zibits 是项目上的艺术线索, Karim Luccin, 团队的图形工程师谈论的是在 "Galaxy 资源管理器" 中创建银河方法的精确、交互式表示形式的艺术与工程之间的协作工作。</span><span class="sxs-lookup"><span data-stu-id="5efcf-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="5efcf-109">技术人员</span><span class="sxs-lookup"><span data-stu-id="5efcf-109">The Tech</span></span>

<span data-ttu-id="5efcf-110">[我们的团队](galaxy-explorer.md#meet-the-team)组成了两个开发人员: 三个开发人员、四个艺术家、一个制造者和一个测试人员-有六周时间来构建一个完全功能的应用程序, 该应用程序允许用户了解并探索银河的 vastness 和美。</span><span class="sxs-lookup"><span data-stu-id="5efcf-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="5efcf-111">我们想要充分利用 HoloLens 在生活空间中直接呈现3D 对象的能力, 因此我们决定创建一个真实的 galaxy, 使用户能够放大并查看单个星形, 每个星分别在各自的轨迹上.</span><span class="sxs-lookup"><span data-stu-id="5efcf-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="5efcf-112">在开发的第一周, 我们提出了几个目标来实现银河的方法:它需要容量耗尽的深度、移动和感觉, 这将有助于创建 galaxy 的形状。</span><span class="sxs-lookup"><span data-stu-id="5efcf-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="5efcf-113">创建具有数十亿星的动画 galaxy 的问题在于, 每帧上需要更新的单个元素的数量可能会太大, 而无法使用 CPU 进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="5efcf-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="5efcf-114">我们的解决方案涉及复杂的艺术和科学组合。</span><span class="sxs-lookup"><span data-stu-id="5efcf-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="5efcf-115">幕后</span><span class="sxs-lookup"><span data-stu-id="5efcf-115">Behind the scenes</span></span>

<span data-ttu-id="5efcf-116">为了让人们能够浏览各个星, 我们的第一步是确定我们可以一次呈现多少粒子。</span><span class="sxs-lookup"><span data-stu-id="5efcf-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="5efcf-117">呈现粒子</span><span class="sxs-lookup"><span data-stu-id="5efcf-117">Rendering particles</span></span>

<span data-ttu-id="5efcf-118">当前 Cpu 非常适合用于处理串行任务, 一次最多可执行几个并行任务 (具体取决于它们具有的内核数), 但 Gpu 在并行处理上千个操作时更为有效。</span><span class="sxs-lookup"><span data-stu-id="5efcf-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="5efcf-119">不过, 由于它们通常不与 CPU 共享同一内存, 因此在 CPU < > GPU 之间交换数据可能会很快成为瓶颈。</span><span class="sxs-lookup"><span data-stu-id="5efcf-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="5efcf-120">我们的解决方案是将 galaxy 置于 GPU 上, 并且它必须完全在 GPU 上运行。</span><span class="sxs-lookup"><span data-stu-id="5efcf-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="5efcf-121">我们在各种模式中开始为成千上万点粒子进行压力测试。</span><span class="sxs-lookup"><span data-stu-id="5efcf-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="5efcf-122">这样, 我们就可以在 HoloLens 上获得 galaxy, 以查看工作情况和内容。</span><span class="sxs-lookup"><span data-stu-id="5efcf-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="5efcf-123">创建星形位置</span><span class="sxs-lookup"><span data-stu-id="5efcf-123">Creating the position of the stars</span></span>

<span data-ttu-id="5efcf-124">我们的一位团队成员已经编写了C#在其最初位置生成星形的代码。</span><span class="sxs-lookup"><span data-stu-id="5efcf-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="5efcf-125">星形位于一个椭圆上, 并且其位置可由 (**curveOffset**, **ellipseSize**,**仰角**) 描述, 其中**curveOffset**是星形沿椭圆的角度, **ellipseSize**是椭圆的尺寸沿 X 和 Z, 并提升 galaxy 内星形的适当提升。</span><span class="sxs-lookup"><span data-stu-id="5efcf-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="5efcf-126">这样, 我们可以创建一个缓冲区 ([Unity 的 ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)), 它将使用每个星型属性进行初始化, 并将其发送到 GPU 上, 以实现其余的体验。</span><span class="sxs-lookup"><span data-stu-id="5efcf-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="5efcf-127">若要绘制此缓冲区, 我们使用[Unity 的 DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) , 它允许在任意一组点上运行着色器 (代码), 而无需使用表示 galaxy 的实际网格:</span><span class="sxs-lookup"><span data-stu-id="5efcf-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="5efcf-128">**CPU**</span><span class="sxs-lookup"><span data-stu-id="5efcf-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="5efcf-129">**GPU**</span><span class="sxs-lookup"><span data-stu-id="5efcf-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="5efcf-130">我们从具有数千个粒子的原始循环模式开始。</span><span class="sxs-lookup"><span data-stu-id="5efcf-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="5efcf-131">这为我们提供了我们所需的证明, 我们可以管理许多粒子, 并以高性能的速度运行</span><span class="sxs-lookup"><span data-stu-id="5efcf-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="5efcf-132">为了改进形状, 我们尝试了各种模式和粒子系统进行旋转。</span><span class="sxs-lookup"><span data-stu-id="5efcf-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="5efcf-133">最初, 这是因为粒子数和性能保持一致, 但形状会在靠近中心处分解, 而星形却发出表面, 但这并不切合现实。</span><span class="sxs-lookup"><span data-stu-id="5efcf-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="5efcf-134">我们需要一个发射, 使我们能够处理时间, 并使粒子真实地移动, 这种循环会更接近 galaxy 中心。</span><span class="sxs-lookup"><span data-stu-id="5efcf-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![我们尝试了多个旋转的模式和粒子系统, 如下所示。](images/galaxy-patterns-500px.png)

<span data-ttu-id="5efcf-136">我们尝试了多个旋转的模式和粒子系统, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="5efcf-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="5efcf-137">我们的团队对 galaxies 函数的方式进行了一些研究, 我们为 galaxy 专门提供了一个自定义粒子系统, 以便我们可以基于 "[密度波理论](https://en.wikipedia.org/wiki/Density_wave_theory)" 移动省略号, 这 theorizes 了 galaxy 的扶手是密度较高, 但 flux, 如流量堵塞。</span><span class="sxs-lookup"><span data-stu-id="5efcf-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="5efcf-138">它看起来稳定稳定, 但当星形沿着各自的椭圆移动时, 它们实际上会移入和移出扶手。</span><span class="sxs-lookup"><span data-stu-id="5efcf-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="5efcf-139">在我们的系统中, 粒子永远不会存在于 CPU 上-我们会生成卡并在 GPU 上调整它们的方向, 因此整个系统只是初始状态和时间。</span><span class="sxs-lookup"><span data-stu-id="5efcf-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="5efcf-140">如下所示:</span><span class="sxs-lookup"><span data-stu-id="5efcf-140">It progressed like this:</span></span>

![具有 GPU 呈现的粒子系统的进度](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="5efcf-142">具有 GPU 呈现的粒子系统的进度</span><span class="sxs-lookup"><span data-stu-id="5efcf-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="5efcf-143">一旦添加了足够的省略号, 并将其设置为旋转, galaxies 就会开始形成 "扶手", 其中星形的运动。</span><span class="sxs-lookup"><span data-stu-id="5efcf-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="5efcf-144">每个椭圆路径上的星形间距被赋予了一些随机性, 并为每个星形增加了一个位置随机性。</span><span class="sxs-lookup"><span data-stu-id="5efcf-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="5efcf-145">这创建了一个更自然的星形运动和 arm 形状分布。</span><span class="sxs-lookup"><span data-stu-id="5efcf-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="5efcf-146">最后, 我们添加了根据中心距离来驱动颜色的功能。</span><span class="sxs-lookup"><span data-stu-id="5efcf-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="5efcf-147">创建星形运动</span><span class="sxs-lookup"><span data-stu-id="5efcf-147">Creating the motion of the stars</span></span>

<span data-ttu-id="5efcf-148">若要对一般星形运动进行动画处理, 需要为每个帧添加一个恒定角度, 并使星形沿着其椭圆沿固定径向速度移动。</span><span class="sxs-lookup"><span data-stu-id="5efcf-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="5efcf-149">这是使用**curveOffset**的主要原因。</span><span class="sxs-lookup"><span data-stu-id="5efcf-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="5efcf-150">从技术上看, 这并不正确, 因为星形会沿着省略号的长边移动</span><span class="sxs-lookup"><span data-stu-id="5efcf-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![在较长的弧线上, 星形移动速度更快, 但边缘速度更慢。](images/ellipse-movement.jpg)

<span data-ttu-id="5efcf-152">在较长的弧线上, 星形移动速度更快, 但边缘速度更慢。</span><span class="sxs-lookup"><span data-stu-id="5efcf-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="5efcf-153">这样一来, 每个星都由 (**curveOffset**, **ellipseSize**,**提升**, **age**) 全面描述, 其中**Age**是自场景加载以来经过的总时间的累计。</span><span class="sxs-lookup"><span data-stu-id="5efcf-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="5efcf-154">这样一来, 我们就可以在应用程序开始时生成数十个星, 并沿着已建立的曲线对一组单的星形进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="5efcf-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="5efcf-155">由于所有内容都在 GPU 上, 因此系统可以将所有的星形并行动态地动态显示给 CPU。</span><span class="sxs-lookup"><span data-stu-id="5efcf-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![下面是绘制白色四边形时的样子。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="5efcf-157">下面是绘制白色四边形时的样子。</span><span class="sxs-lookup"><span data-stu-id="5efcf-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="5efcf-158">为了使每个四颗面都为相机, 我们使用几何着色器将每个星形位置转换为屏幕上将包含星形纹理的2D 矩形。</span><span class="sxs-lookup"><span data-stu-id="5efcf-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![菱形而不是四边形。](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="5efcf-160">菱形而不是四边形。</span><span class="sxs-lookup"><span data-stu-id="5efcf-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="5efcf-161">由于我们希望限制过度绘制 (处理像素的次数), 因此我们将四边形旋转, 使其重叠越少。</span><span class="sxs-lookup"><span data-stu-id="5efcf-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="5efcf-162">添加云</span><span class="sxs-lookup"><span data-stu-id="5efcf-162">Adding clouds</span></span>

<span data-ttu-id="5efcf-163">有很多方法可让你从一个卷内的 ray marching 中获取容量耗尽的感受, 以尽可能多地绘制粒子来模拟云。</span><span class="sxs-lookup"><span data-stu-id="5efcf-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="5efcf-164">实时 ray marching 的成本太高, 因此很难创作, 因此, 我们首先尝试使用一种用于在游戏中呈现林的方法来构建冒名顶替系统, 这种方法适用于照相机。</span><span class="sxs-lookup"><span data-stu-id="5efcf-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="5efcf-165">当我们在游戏中执行此操作时, 我们可以从相机中呈现出一个旋转的树纹理, 保存所有这些图像, 并在每个布告栏上运行时, 选择与视图方向匹配的图像。</span><span class="sxs-lookup"><span data-stu-id="5efcf-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="5efcf-166">如果图像是全息影像, 这也不起作用。</span><span class="sxs-lookup"><span data-stu-id="5efcf-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="5efcf-167">左眼和合适的眼睛之间的区别在于, 这使得我们需要更高的分辨率, 否则它只是平面、化名或重复。</span><span class="sxs-lookup"><span data-stu-id="5efcf-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="5efcf-168">第二次尝试时, 尝试尽可能多的粒子。</span><span class="sxs-lookup"><span data-stu-id="5efcf-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="5efcf-169">最佳视觉对象是在将微粒添加到场景之前, 添加性地绘制粒子并模糊。</span><span class="sxs-lookup"><span data-stu-id="5efcf-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="5efcf-170">此方法的典型问题与我们可以同时绘制多少粒子相关, 同时还会保持60fps 的屏幕区域。</span><span class="sxs-lookup"><span data-stu-id="5efcf-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="5efcf-171">模糊生成的映像, 使此云感觉通常是一种非常昂贵的操作。</span><span class="sxs-lookup"><span data-stu-id="5efcf-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![如果没有纹理, 这就是云的外观, 其中 2% 不透明度。](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="5efcf-173">如果没有纹理, 这就是云的外观, 其中 2% 不透明度。</span><span class="sxs-lookup"><span data-stu-id="5efcf-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="5efcf-174">如果是累加性的, 其中有很多表示每个四边形有多个, 则会对同一像素重复着色。</span><span class="sxs-lookup"><span data-stu-id="5efcf-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="5efcf-175">在 galaxy 的中心, 相同的像素彼此之上有数百个四边形, 在全屏显示时, 这会产生巨大的成本。</span><span class="sxs-lookup"><span data-stu-id="5efcf-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="5efcf-176">执行全屏云并尝试对其进行模糊处理是一种不好的做法, 因此, 我们决定让硬件为我们完成工作。</span><span class="sxs-lookup"><span data-stu-id="5efcf-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="5efcf-177">首先是一个上下文</span><span class="sxs-lookup"><span data-stu-id="5efcf-177">A bit of context first</span></span>

<span data-ttu-id="5efcf-178">当在游戏中使用纹理时, 纹理大小很少与我们要在中使用的区域匹配, 但我们可以使用不同种类的纹理筛选来使图形卡从纹理像素 ([纹理筛选](https://msdn.microsoft.com/library/dn642451.aspx)) 中插入所需的颜色。</span><span class="sxs-lookup"><span data-stu-id="5efcf-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="5efcf-179">我们感兴趣，筛选[双线性筛选](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx)将计算使用最近近邻 4 任何像素的值。</span><span class="sxs-lookup"><span data-stu-id="5efcf-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![筛选前的原始](images/texture-1.png)

![筛选后的结果](images/texture-2.png)

<span data-ttu-id="5efcf-182">使用此属性, 我们发现每次尝试将纹理绘制到一个区域的两倍时, 它将使结果模糊。</span><span class="sxs-lookup"><span data-stu-id="5efcf-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="5efcf-183">我们可能会在其他内容上进行操作, 而不是呈现为全屏, 而是不会出现在屏幕上, 而是呈现给屏幕的小版本。</span><span class="sxs-lookup"><span data-stu-id="5efcf-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="5efcf-184">然后, 通过复制此纹理并按2次因子拉伸它, 我们将返回全屏, 同时模糊处理过程中的内容。</span><span class="sxs-lookup"><span data-stu-id="5efcf-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 upscale 返回到完整解决方案。](images/galaxy-resolutions-300px.png)

<span data-ttu-id="5efcf-186">x3 upscale 返回到完整解决方案。</span><span class="sxs-lookup"><span data-stu-id="5efcf-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="5efcf-187">这样, 我们就可以只使用一小部分原始成本来获取云部件。</span><span class="sxs-lookup"><span data-stu-id="5efcf-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="5efcf-188">我们只需绘制像素的 1/64th, 而不是在完整的分辨率下添加云, 只需将纹理拉伸回完整分辨率即可。</span><span class="sxs-lookup"><span data-stu-id="5efcf-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Left, 其中 upscale 从 1/8 到完全解析;右, 使用2的幂2进行 3 upscale。](images/stars-upscaled-300px.jpg)

<span data-ttu-id="5efcf-190">Left, 其中 upscale 从 1/8 到完全解析;右, 使用2的幂2进行 3 upscale。</span><span class="sxs-lookup"><span data-stu-id="5efcf-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="5efcf-191">请注意, 尝试从大小的 1/64th 到一次的全尺寸看上去完全不同, 因为图形卡仍会在我们的设置中使用4个像素来向更大的区域着色, 并使项目开始显示。</span><span class="sxs-lookup"><span data-stu-id="5efcf-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="5efcf-192">然后, 如果我们添加具有较小卡片的完整分辨率, 则会获得完整的 galaxy:</span><span class="sxs-lookup"><span data-stu-id="5efcf-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![使用全分辨率星形的 galaxy 渲染接近最终结果](images/full-galaxy-500px.png)

<span data-ttu-id="5efcf-194">完成形状的右跟踪后, 我们添加了一层云, 并将临时点换出到 Photoshop 中绘制的点, 并添加了一些其他颜色。</span><span class="sxs-lookup"><span data-stu-id="5efcf-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="5efcf-195">结果就是一种银河的方法, Galaxy 我们的艺术和工程团队都认为是非常好的, 并满足我们对 CPU 产生深刻的目标。</span><span class="sxs-lookup"><span data-stu-id="5efcf-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![三维中的最终银河方法。](images/final-galaxy-500px.jpg)

<span data-ttu-id="5efcf-197">三维中的最终银河方法。</span><span class="sxs-lookup"><span data-stu-id="5efcf-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="5efcf-198">了解更多</span><span class="sxs-lookup"><span data-stu-id="5efcf-198">More to explore</span></span>

<span data-ttu-id="5efcf-199">我们已经为 Galaxy 资源管理器应用程序提供了公开代码, 并使其在[GitHub](https://github.com/Microsoft/GalaxyExplorer)上可供开发人员使用。</span><span class="sxs-lookup"><span data-stu-id="5efcf-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="5efcf-200">想要了解有关 Galaxy 资源管理器开发过程的详细信息？</span><span class="sxs-lookup"><span data-stu-id="5efcf-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="5efcf-201">查看[Microsoft HoloLens YouTube 频道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)上的所有过去的项目更新。</span><span class="sxs-lookup"><span data-stu-id="5efcf-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="5efcf-202">关于作者</span><span class="sxs-lookup"><span data-stu-id="5efcf-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="5efcf-203"><b>Karim Luccin</b>是一种软件工程师和别致的视觉对象爱好者。</span><span class="sxs-lookup"><span data-stu-id="5efcf-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="5efcf-204">他是用于 Galaxy 资源管理器的图形工程师。</span><span class="sxs-lookup"><span data-stu-id="5efcf-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="5efcf-205"><b>Zibits</b>是一位艺术的线索和空间发烧, 负责管理用于 Galaxy 资源管理器和孜孜以求的3d 建模团队, 甚至更多粒子。</span><span class="sxs-lookup"><span data-stu-id="5efcf-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="5efcf-206">请参阅</span><span class="sxs-lookup"><span data-stu-id="5efcf-206">See also</span></span>
* [<span data-ttu-id="5efcf-207">GitHub 上的 Galaxy 资源管理器</span><span class="sxs-lookup"><span data-stu-id="5efcf-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="5efcf-208">YouTube 上的 Galaxy 资源管理器项目更新</span><span class="sxs-lookup"><span data-stu-id="5efcf-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
