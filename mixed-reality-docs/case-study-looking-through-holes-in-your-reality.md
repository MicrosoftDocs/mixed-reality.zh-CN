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
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="e9a28-104">案例研究-通查在现实中的漏洞</span><span class="sxs-lookup"><span data-stu-id="e9a28-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="e9a28-105">人们考虑混合的现实，他们可以使用 Microsoft HoloLens 所执行的操作，它们通常坚持问题如"什么对象添加到我的房间？"</span><span class="sxs-lookup"><span data-stu-id="e9a28-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="e9a28-106">或者"什么可以我基于我的空间？"</span><span class="sxs-lookup"><span data-stu-id="e9a28-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="e9a28-107">我想要突出显示您可以考虑的另一个区域 — 实质上是一招，使用相同的技术来查找到或通过围绕你的实际的物理对象。</span><span class="sxs-lookup"><span data-stu-id="e9a28-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="e9a28-108">技术人员</span><span class="sxs-lookup"><span data-stu-id="e9a28-108">The tech</span></span>

<span data-ttu-id="e9a28-109">如果您已遵循外星人，因为他们可以突破中挂历 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**，解锁安全的墙 **[片段](case-study-creating-an-immersive-experience-in-fragments.md)**，或已足够幸运若要查看在 UNSC 无穷大 hangar **[Halo 5 体验在 E3 中 2015年](https://www.youtube.com/watch?v=QDw5QjDtFy8)**，则您已了解我所讲述的内容。</span><span class="sxs-lookup"><span data-stu-id="e9a28-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="e9a28-110">根据您的想象力，来临时漏洞置于你砌干墙或隐藏在松散 floorboard 体系，可以使用此 visual 技巧。</span><span class="sxs-lookup"><span data-stu-id="e9a28-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid 添加三维管道和其他结构背后挂历，仅通过创建入侵者破坏漏洞可见。](images/roboraid-640px.png)

<span data-ttu-id="e9a28-112">RoboRaid 添加三维管道和其他结构背后挂历，仅通过创建入侵者破坏漏洞可见。</span><span class="sxs-lookup"><span data-stu-id="e9a28-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="e9a28-113">在 HoloLens 上使用这些唯一全息之一，应用可以现实通过实际窗口显示的相同方法中提供内容，您墙壁后面或通过您的场所视觉的效果。</span><span class="sxs-lookup"><span data-stu-id="e9a28-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="e9a28-114">自行保留，移动，可以看到任何位于右侧。</span><span class="sxs-lookup"><span data-stu-id="e9a28-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="e9a28-115">获取更接近，并可以看到的所有内容的更多一些。</span><span class="sxs-lookup"><span data-stu-id="e9a28-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="e9a28-116">主要区别是，实际漏洞允许你通过，而您的场所仍会顽固地不会让您通过攀升至该神奇 holographic 内容。</span><span class="sxs-lookup"><span data-stu-id="e9a28-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="e9a28-117">（我将添加一项任务到积压工作。）</span><span class="sxs-lookup"><span data-stu-id="e9a28-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="e9a28-118">幕后</span><span class="sxs-lookup"><span data-stu-id="e9a28-118">Behind the scenes</span></span>

<span data-ttu-id="e9a28-119">此技巧是两个效果的组合。</span><span class="sxs-lookup"><span data-stu-id="e9a28-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="e9a28-120">首先，holographic 内容固定到世界上使用"空间定位点"。</span><span class="sxs-lookup"><span data-stu-id="e9a28-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="e9a28-121">使用定位点以使该内容"world 锁定"意味着，您正在寻找的内容并不直观地偏移离开物理对象附近，即使当你移动控件或基础空间映射系统更新你的聊天室其三维模型。</span><span class="sxs-lookup"><span data-stu-id="e9a28-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="e9a28-122">其次，该全息版的内容仅限于以可视方式非常特定的空间，因此您可以仅通过漏洞在现实中看到。</span><span class="sxs-lookup"><span data-stu-id="e9a28-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="e9a28-123">该封闭有必要需要仔细逻辑漏洞、 窗口或通道，销售技巧。</span><span class="sxs-lookup"><span data-stu-id="e9a28-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="e9a28-124">而无需阻止大多数视图的某些内容，对机密罗纪维度空间破裂只是看起来像效果不佳放置恢复不复存在。</span><span class="sxs-lookup"><span data-stu-id="e9a28-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![这不是实际的屏幕截图，但举例说明了从 MR 基础知识 101 机密 underworld 在 HoloLens 上的外观。](images/origamiholecomposited-640px.png)

<span data-ttu-id="e9a28-128">这不是实际的屏幕截图，但举例说明了如何从机密 underworld [MR 基础知识 101](holograms-101.md)在 HoloLens 上的外观。</span><span class="sxs-lookup"><span data-stu-id="e9a28-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="e9a28-129">黑色的机箱不显示，但您所见的内容经过一个虚拟的孔。</span><span class="sxs-lookup"><span data-stu-id="e9a28-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="e9a28-130">（查看通过实际设备，floor 这看起来更消失，因为你自己的焦点在进一步距离如如果找不到甚至。）</span><span class="sxs-lookup"><span data-stu-id="e9a28-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="e9a28-131">世界锁定 holographic 内容</span><span class="sxs-lookup"><span data-stu-id="e9a28-131">World-locking holographic content</span></span>

<span data-ttu-id="e9a28-132">在 Unity 中，从而导致 holographic 内容保持世界锁定非常简单，只添加 WorldAnchor 组件：</span><span class="sxs-lookup"><span data-stu-id="e9a28-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="e9a28-133">WorldAnchor 组件不断将调整的位置和轮换其的 GameObject （以及任何其他层次结构中该对象之下） 以使其保持稳定相对于邻近的物理对象。</span><span class="sxs-lookup"><span data-stu-id="e9a28-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="e9a28-134">在创作时你的内容，则创建它的方式，在此虚拟孔居中对象的根数据透视。</span><span class="sxs-lookup"><span data-stu-id="e9a28-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="e9a28-135">（如果在墙上插座的深度中对象的透视，位置和旋转其细微调整将更加明显，并且漏洞不可能看起来非常稳定。）</span><span class="sxs-lookup"><span data-stu-id="e9a28-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="e9a28-136">Occluding 虚拟孔以外的所有内容</span><span class="sxs-lookup"><span data-stu-id="e9a28-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="e9a28-137">有多种方式来选择性地阻止到什么在挂历中隐藏的视图。</span><span class="sxs-lookup"><span data-stu-id="e9a28-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="e9a28-138">最简单的一个充分利用这一事实 HoloLens 使用累加性的显示模式，这意味着，完全黑色对象会出现不可见。</span><span class="sxs-lookup"><span data-stu-id="e9a28-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="e9a28-139">你可以在 Unity 中而无需执行任何特殊的着色器或材料技巧-只需创建黑色材料，并将其分配给你的内容中的对象。</span><span class="sxs-lookup"><span data-stu-id="e9a28-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="e9a28-140">如果您不想进行三维模型，只需使用少量的四核的默认对象并略有重叠。</span><span class="sxs-lookup"><span data-stu-id="e9a28-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="e9a28-141">有多种，此方法的缺点，但它是最快的方法，以便让某项工作，并获取低保真概念证明概念工作是太好了，即使你怀疑你可能想要更高版本重构。</span><span class="sxs-lookup"><span data-stu-id="e9a28-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="e9a28-142">上面的"黑盒"方法的一个主要缺点是不好拍照。</span><span class="sxs-lookup"><span data-stu-id="e9a28-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="e9a28-143">虽然看完美通过 HoloLens 的显示效果，您采取任何屏幕截图将显示而不是剩下的墙或下限的大黑色对象。</span><span class="sxs-lookup"><span data-stu-id="e9a28-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="e9a28-144">这样做的原因是，物理硬件和屏幕截图复合全息与现实以不同的方式。</span><span class="sxs-lookup"><span data-stu-id="e9a28-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="e9a28-145">让我们 detour 片刻到一些伪数学...</span><span class="sxs-lookup"><span data-stu-id="e9a28-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="e9a28-146">*伪数学警报 ！这些数字和公式是用来演示的点，不是任何类型的准确指标 ！*</span><span class="sxs-lookup"><span data-stu-id="e9a28-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="e9a28-147">您看到的内容通过 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="e9a28-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="e9a28-148">您看到的内容中屏幕截图和视频：</span><span class="sxs-lookup"><span data-stu-id="e9a28-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="e9a28-149">英语：通过 HoloLens 看到的内容是简单的变暗现实情况 （例如，通过太阳镜） 和任何组合全息应用要显示。</span><span class="sxs-lookup"><span data-stu-id="e9a28-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="e9a28-150">但时拍摄屏幕快照，与每像素透明度值根据应用的全息混合照相机的映像。</span><span class="sxs-lookup"><span data-stu-id="e9a28-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="e9a28-151">若要避免这一问题的一种方法是更改"黑盒"材料以仅写入深度缓冲区，并与所有其他不透明材料进行排序。</span><span class="sxs-lookup"><span data-stu-id="e9a28-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="e9a28-152">有关此示例，请查看[MixedRealityToolkit 在 GitHub 上的 WindowOcclusion.shader 文件](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)。</span><span class="sxs-lookup"><span data-stu-id="e9a28-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="e9a28-153">相关行复制到此处：</span><span class="sxs-lookup"><span data-stu-id="e9a28-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="e9a28-154">(请注意"偏移量 50，100"行是不相关的问题，因此可能最好省略的一些处理。)</span><span class="sxs-lookup"><span data-stu-id="e9a28-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="e9a28-155">类似的实现不可见的阻挡物材料将使您的应用程序绘制看起来和混合现实屏幕截图中显示正确的框。</span><span class="sxs-lookup"><span data-stu-id="e9a28-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="e9a28-156">对于奖励积分，可以尝试通过执行聪明操作绘制甚至更少的不可见像素，提高该框更进一步的性能但，实际上可以掌握井水并且通常不会有必要。</span><span class="sxs-lookup"><span data-stu-id="e9a28-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![下面是从 MR 基础知识 101 机密 underworld 如 Unity 绘制它的 occluding 框外部的部分除外。](images/underworld-occluded-640px.png)

<span data-ttu-id="e9a28-159">下面是从机密 underworld [MR 基础知识 101](holograms-101.md)如 Unity 绘制它的 occluding 框外部的部分除外。</span><span class="sxs-lookup"><span data-stu-id="e9a28-159">Here is the secret underworld from [MR Basics 101](holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="e9a28-160">请注意，underworld 的透视的框中，这有助于保持孔相对于实际 floor 尽可能。</span><span class="sxs-lookup"><span data-stu-id="e9a28-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="e9a28-161">就自己动手</span><span class="sxs-lookup"><span data-stu-id="e9a28-161">Do it yourself</span></span>

<span data-ttu-id="e9a28-162">具有 HoloLens 和想要自行尝试效果？</span><span class="sxs-lookup"><span data-stu-id="e9a28-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="e9a28-163">您可以执行 （无需编码） 的最简单操作是安装免费的三维查看器应用，然后加载[我已在 GitHub 提供的下载 the.fbx 文件](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow)在聊天室中查看花卉 pot 模型。</span><span class="sxs-lookup"><span data-stu-id="e9a28-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="e9a28-164">将其加载 HoloLens 上,，可以看到在工作效果。</span><span class="sxs-lookup"><span data-stu-id="e9a28-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="e9a28-165">该模型的前面时，只能看到插入小孔，其他所有内容均不可见。</span><span class="sxs-lookup"><span data-stu-id="e9a28-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="e9a28-166">从任何其他方查看模型，它将完全消失。</span><span class="sxs-lookup"><span data-stu-id="e9a28-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="e9a28-167">使用移动、 旋转和缩放控件的三维查看器来定位针对任何垂直的图面，您可以将生成的一些观点虚拟漏洞 ！</span><span class="sxs-lookup"><span data-stu-id="e9a28-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![在 Unity 编辑器中查看此模型将显示 flowerpot 周围的大黑色框。](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="e9a28-170">在 Unity 编辑器中查看此模型将显示 flowerpot 周围的大黑色框。</span><span class="sxs-lookup"><span data-stu-id="e9a28-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="e9a28-171">HoloLens 上, 消失后框中，为提供为神奇窗口效果的方式。</span><span class="sxs-lookup"><span data-stu-id="e9a28-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="e9a28-172">如果你想要生成使用此技术的应用程序，请查看[MR 基础知识 101 教程](holograms-101.md)中[混合现实教程](tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="e9a28-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](holograms-101.md) in the [Mixed Reality tutorials](tutorials.md).</span></span> <span data-ttu-id="e9a28-173">第 7 章结尾中显示 （如图上面所示） 隐藏的 underworld 你 floor 爆炸式增长。</span><span class="sxs-lookup"><span data-stu-id="e9a28-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="e9a28-174">谁说教程必须令人厌烦？</span><span class="sxs-lookup"><span data-stu-id="e9a28-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="e9a28-175">以下是一些建议的位置执行这一想法下一步：</span><span class="sxs-lookup"><span data-stu-id="e9a28-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="e9a28-176">想一想如何使虚拟小孔里面的内容交互。</span><span class="sxs-lookup"><span data-stu-id="e9a28-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="e9a28-177">让你有超出其留言板一些影响的用户可以真正提高不足为奇了这一技巧可以提供有意义。</span><span class="sxs-lookup"><span data-stu-id="e9a28-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="e9a28-178">研究的方法，以查看通过返回到已知区域的对象。</span><span class="sxs-lookup"><span data-stu-id="e9a28-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="e9a28-179">例如，如何 holographic 孔置于咖啡表并查看其下的你 floor？</span><span class="sxs-lookup"><span data-stu-id="e9a28-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="e9a28-180">关于作者</span><span class="sxs-lookup"><span data-stu-id="e9a28-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="e9a28-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="e9a28-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="e9a28-182">高级软件工程师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e9a28-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="e9a28-183">请参阅</span><span class="sxs-lookup"><span data-stu-id="e9a28-183">See also</span></span>
* [<span data-ttu-id="e9a28-184">MR 基础知识 101：使用设备完成项目</span><span class="sxs-lookup"><span data-stu-id="e9a28-184">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="e9a28-185">坐标系统</span><span class="sxs-lookup"><span data-stu-id="e9a28-185">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="e9a28-186">空间定位点</span><span class="sxs-lookup"><span data-stu-id="e9a28-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="e9a28-187">空间映射</span><span class="sxs-lookup"><span data-stu-id="e9a28-187">Spatial mapping</span></span>](spatial-mapping.md)
