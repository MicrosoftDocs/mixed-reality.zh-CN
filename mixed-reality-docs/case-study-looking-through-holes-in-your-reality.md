---
title: 案例研究-查看现实中的洞
description: 此案例研究介绍了如何在 HoloLens 上实现 "神奇窗口" 效果, 使用户能够在其实际环境中的墙壁后面、在地面下和虚拟空缺之间进行观看。
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 幻窗口, 视差
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873929"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="76d23-104">案例研究-查看现实中的洞</span><span class="sxs-lookup"><span data-stu-id="76d23-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="76d23-105">当人们考虑混合现实以及他们可以通过 Microsoft HoloLens 实现哪些功能时, 他们通常会坚持 "我可以将哪些对象添加到我的聊天室？" 之类的问题。</span><span class="sxs-lookup"><span data-stu-id="76d23-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="76d23-106">或者 "我可以在我的空间之上分层什么？"</span><span class="sxs-lookup"><span data-stu-id="76d23-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="76d23-107">我想突出显示另一个可以考虑的领域, 这是一种非常神奇的技巧, 使用相同的技术来查找或通过围绕您的真实物理对象。</span><span class="sxs-lookup"><span data-stu-id="76d23-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="76d23-108">技术人员</span><span class="sxs-lookup"><span data-stu-id="76d23-108">The tech</span></span>

<span data-ttu-id="76d23-109">如果您已遵循外星人，因为他们可以突破中挂历 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** ，解锁安全的墙 **[片段](case-study-creating-an-immersive-experience-in-fragments.md)** ，或已足够幸运若要查看在 UNSC 无穷大 hangar **[Halo 5 体验在 E3 中 2015年](https://www.youtube.com/watch?v=QDw5QjDtFy8)** ，则您已了解我所讲述的内容。</span><span class="sxs-lookup"><span data-stu-id="76d23-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="76d23-110">根据您的想像, 此视觉对象可用于在您的饰面中放置临时孔, 或在松散 floorboard 下隐藏世界。</span><span class="sxs-lookup"><span data-stu-id="76d23-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid 将三维管道和其他结构添加到墙壁后面, 只能通过创建为太空 break 的孔进行查看。](images/roboraid-640px.png)

<span data-ttu-id="76d23-112">RoboRaid 将三维管道和其他结构添加到墙壁后面, 只能通过创建为太空 break 的孔进行查看。</span><span class="sxs-lookup"><span data-stu-id="76d23-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="76d23-113">在 HoloLens 上使用其中一个独特的全息影像, 应用程序可以通过实际的窗口以真实表现的方式为你的墙壁或地面提供内容的错觉。</span><span class="sxs-lookup"><span data-stu-id="76d23-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="76d23-114">向左移动, 您可以看到右侧的内容。</span><span class="sxs-lookup"><span data-stu-id="76d23-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="76d23-115">深入了解, 你可以更深入地了解所有内容。</span><span class="sxs-lookup"><span data-stu-id="76d23-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="76d23-116">主要区别在于真实的洞能让你完成, 而地面顽固地不会让你经过神奇全息内容。</span><span class="sxs-lookup"><span data-stu-id="76d23-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="76d23-117">(我会将任务添加到积压工作 (backlog)。)</span><span class="sxs-lookup"><span data-stu-id="76d23-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="76d23-118">幕后</span><span class="sxs-lookup"><span data-stu-id="76d23-118">Behind the scenes</span></span>

<span data-ttu-id="76d23-119">这一技巧组合了两个效果。</span><span class="sxs-lookup"><span data-stu-id="76d23-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="76d23-120">首先, 使用 "空间锚点" 将全息内容固定到世界。</span><span class="sxs-lookup"><span data-stu-id="76d23-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="76d23-121">使用定位点来使内容 "世界锁定" 意味着你要查看的内容不会在视觉上偏离其附近的物理对象, 即使你移动或基础空间映射系统会更新其3D 模型。</span><span class="sxs-lookup"><span data-stu-id="76d23-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="76d23-122">其次, 全息内容在外观上仅限于特定空间, 因此, 你只能在现实中看到该洞。</span><span class="sxs-lookup"><span data-stu-id="76d23-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="76d23-123">这封闭是需要通过逻辑洞、窗户或门口 (销售这一墩) 来进行的。</span><span class="sxs-lookup"><span data-stu-id="76d23-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="76d23-124">如果没有任何内容阻碍了视图, 则将空间破解到机密 Jurassic 维度可能看起来就像是一个不良的分块。</span><span class="sxs-lookup"><span data-stu-id="76d23-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![这并不是实际的屏幕截图, 而是说明来自 MR underworld 的机密如何101在 HoloLens 上的外观。](images/origamiholecomposited-640px.png)

<span data-ttu-id="76d23-128">这并不是实际的屏幕截图, 而是对来自[MR 基础知识 101](holograms-101.md)的机密 underworld 的说明。</span><span class="sxs-lookup"><span data-stu-id="76d23-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="76d23-129">黑色机箱未显示, 但你可以通过虚拟孔查看内容。</span><span class="sxs-lookup"><span data-stu-id="76d23-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="76d23-130">(在查找实际设备时, 地面似乎会消失, 因为你的眼睛会显得更远一点, 就像根本不会那样。)</span><span class="sxs-lookup"><span data-stu-id="76d23-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="76d23-131">全球锁定全息内容</span><span class="sxs-lookup"><span data-stu-id="76d23-131">World-locking holographic content</span></span>

<span data-ttu-id="76d23-132">在 Unity 中, 导致全息内容保持世界锁定状态与添加 WorldAnchor 组件一样简单:</span><span class="sxs-lookup"><span data-stu-id="76d23-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="76d23-133">WorldAnchor 组件将不断调整其 GameObject 的位置和旋转 (以及该对象在层次结构中的任何其他内容), 使其相对于附近的物理对象保持稳定。</span><span class="sxs-lookup"><span data-stu-id="76d23-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="76d23-134">创作你的内容时, 请以这种方式创建你的对象的根透视, 使其在此虚拟洞上居中。</span><span class="sxs-lookup"><span data-stu-id="76d23-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="76d23-135">(如果您的对象的透视是墙中的深度, 则其位置和旋转的轻微调整会更明显, 并且该孔可能看起来不稳定。)</span><span class="sxs-lookup"><span data-stu-id="76d23-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="76d23-136">Occluding 除虚拟洞以外的所有内容</span><span class="sxs-lookup"><span data-stu-id="76d23-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="76d23-137">有多种方法可以有选择地阻止在墙壁中隐藏的内容。</span><span class="sxs-lookup"><span data-stu-id="76d23-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="76d23-138">最简单的一种方法是使用 HoloLens 使用加法显示这一事实, 这意味着完全的黑色对象会显示为不可见。</span><span class="sxs-lookup"><span data-stu-id="76d23-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="76d23-139">您可以在 Unity 中执行此操作, 而无需执行任何特殊着色器或材料技巧—只需创建黑色材料, 并将其分配给内容中的框。</span><span class="sxs-lookup"><span data-stu-id="76d23-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="76d23-140">如果你不想进行3D 建模, 只需使用少量的默认四个对象并略微重叠它们。</span><span class="sxs-lookup"><span data-stu-id="76d23-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="76d23-141">这种方法有很多缺点, 但它是实现工作的最快方法, 即使您怀疑以后可能需要重构它, 也可以使用最快的概念证明。</span><span class="sxs-lookup"><span data-stu-id="76d23-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="76d23-142">上面的 "黑箱" 方法的一个主要缺点是它没有太好的照片。</span><span class="sxs-lookup"><span data-stu-id="76d23-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="76d23-143">尽管你的效果可能会通过显示 HoloLens 看起来很完美, 但你所做的任何屏幕截图都将显示较大的黑色对象, 而不是墙或地面的内容。</span><span class="sxs-lookup"><span data-stu-id="76d23-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="76d23-144">导致这种情况的原因是物理硬件和屏幕截图的组合影像和实际情况有所不同。</span><span class="sxs-lookup"><span data-stu-id="76d23-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="76d23-145">让我们 detour 一些虚假的数学 。</span><span class="sxs-lookup"><span data-stu-id="76d23-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="76d23-146">*伪数学警报!这些数字和公式旨在说明点, 而不是任何种类的准确指标!*</span><span class="sxs-lookup"><span data-stu-id="76d23-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="76d23-147">通过 HoloLens 查看的内容:</span><span class="sxs-lookup"><span data-stu-id="76d23-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="76d23-148">在屏幕截图和视频中看到的内容:</span><span class="sxs-lookup"><span data-stu-id="76d23-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="76d23-149">英文:通过 HoloLens 看到的内容是变暗现实 (如通过太阳镜) 和应用想要显示的任何全息影像的简单组合。</span><span class="sxs-lookup"><span data-stu-id="76d23-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="76d23-150">但在拍摄屏幕截图时, 照相机的图像会根据每像素的透明度值与应用的全息影像混合。</span><span class="sxs-lookup"><span data-stu-id="76d23-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="76d23-151">解决这种情况的一种方法是将 "黑色框" 材料改为仅写入深度缓冲区, 并将所有其他的不透明材料进行排序。</span><span class="sxs-lookup"><span data-stu-id="76d23-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="76d23-152">有关这种情况的示例, 请查看[GitHub 上的 MixedRealityToolkit 中的 WindowOcclusion 文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)。</span><span class="sxs-lookup"><span data-stu-id="76d23-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="76d23-153">相关行复制如下:</span><span class="sxs-lookup"><span data-stu-id="76d23-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="76d23-154">(请注意, "偏移 50, 100" 行用于处理不相关的问题, 因此, 可能有必要将其退出。)</span><span class="sxs-lookup"><span data-stu-id="76d23-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="76d23-155">实现一种不可见的封闭材料, 使您的应用程序能够绘制一个在显示和混合现实屏幕截图中显示正确的框。</span><span class="sxs-lookup"><span data-stu-id="76d23-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="76d23-156">对于附赠点, 您可以尝试进一步提高此框的性能, 方法是通过进行巧妙地绘制更少的不可见像素来更好地绘制, 但这种方法实际上不是必需的。</span><span class="sxs-lookup"><span data-stu-id="76d23-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![下面是来自 MR 基础知识101的机密 underworld, 因为 Unity 会绘制该机密, 但 occluding 框的外部部分除外。](images/underworld-occluded-640px.png)

<span data-ttu-id="76d23-159">下面是来自[MR 基础知识 101](holograms-101.md)的机密 underworld, 因为 Unity 会绘制该机密, 但 occluding 框的外部部分除外。</span><span class="sxs-lookup"><span data-stu-id="76d23-159">Here is the secret underworld from [MR Basics 101](holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="76d23-160">请注意, underworld 的透视是在该框的中心, 这有助于使洞相对于实际楼层尽可能稳定。</span><span class="sxs-lookup"><span data-stu-id="76d23-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="76d23-161">自行完成</span><span class="sxs-lookup"><span data-stu-id="76d23-161">Do it yourself</span></span>

<span data-ttu-id="76d23-162">有一个 HoloLens, 想要亲自尝试自己的效果吗？</span><span class="sxs-lookup"><span data-stu-id="76d23-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="76d23-163">您可以执行的最简单操作 (无需编码) 是安装免费的3D 查看器应用程序, 然后加载在[GitHub 上提供的 fbx 文件](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow), 以便在房间中查看花卉模型。</span><span class="sxs-lookup"><span data-stu-id="76d23-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="76d23-164">将其加载到 HoloLens 上, 你可以看到工作的错觉。</span><span class="sxs-lookup"><span data-stu-id="76d23-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="76d23-165">在模型的前面, 只能看到 "小" 洞面, 其他所有内容都不可见。</span><span class="sxs-lookup"><span data-stu-id="76d23-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="76d23-166">从任何其他端查看模型, 它将完全消失。</span><span class="sxs-lookup"><span data-stu-id="76d23-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="76d23-167">使用3D 查看器的移动、旋转和缩放控件, 将虚拟孔洞定位到可以考虑生成某些创意的任何垂直表面上!</span><span class="sxs-lookup"><span data-stu-id="76d23-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![在 Unity 编辑器中查看此模型将在 flowerpot 周围显示大的黑色框。](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="76d23-170">在 Unity 编辑器中查看此模型将在 flowerpot 周围显示大的黑色框。</span><span class="sxs-lookup"><span data-stu-id="76d23-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="76d23-171">在 HoloLens 上, 此框消失, 为神奇窗口效果提供。</span><span class="sxs-lookup"><span data-stu-id="76d23-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="76d23-172">如果要构建使用此技术的应用, 请在[混合现实教程](tutorials.md)中查看[MR 基本101教程](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="76d23-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](holograms-101.md) in the [Mixed Reality tutorials](tutorials.md).</span></span> <span data-ttu-id="76d23-173">第7章以地面分离, 其中显示了隐藏的 underworld (如上图所示)。</span><span class="sxs-lookup"><span data-stu-id="76d23-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="76d23-174">谁说教程必须是枯燥的呢？</span><span class="sxs-lookup"><span data-stu-id="76d23-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="76d23-175">下面是一些你可以在其中执行此操作的一些建议:</span><span class="sxs-lookup"><span data-stu-id="76d23-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="76d23-176">考虑使虚拟洞内内容成为交互的方式。</span><span class="sxs-lookup"><span data-stu-id="76d23-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="76d23-177">让您的用户在其墙外产生一定的影响, 可以真正提高此技巧可以提供的意义。</span><span class="sxs-lookup"><span data-stu-id="76d23-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="76d23-178">考虑通过对象查看到已知区域的方法。</span><span class="sxs-lookup"><span data-stu-id="76d23-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="76d23-179">例如, 如何在咖啡表中放入全息孔并查看其下的地面？</span><span class="sxs-lookup"><span data-stu-id="76d23-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="76d23-180">关于作者</span><span class="sxs-lookup"><span data-stu-id="76d23-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="76d23-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="76d23-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="76d23-182">高级软件工程师@Microsoft</span><span class="sxs-lookup"><span data-stu-id="76d23-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="76d23-183">请参阅</span><span class="sxs-lookup"><span data-stu-id="76d23-183">See also</span></span>
* [<span data-ttu-id="76d23-184">MR 基础知识 101：使用设备完成项目</span><span class="sxs-lookup"><span data-stu-id="76d23-184">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="76d23-185">坐标系统</span><span class="sxs-lookup"><span data-stu-id="76d23-185">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="76d23-186">空间定位点</span><span class="sxs-lookup"><span data-stu-id="76d23-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="76d23-187">空间映射</span><span class="sxs-lookup"><span data-stu-id="76d23-187">Spatial mapping</span></span>](spatial-mapping.md)
