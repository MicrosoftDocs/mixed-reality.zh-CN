---
title: 在 Unity 中的文本
description: 若要显示的文本在 Unity 中，有两种类型的文本组件可以使用-UI 文本和三维文本网格。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality，设计，用于控制字体、 版式、 ui、 用户体验
ms.openlocfilehash: f57b04c7d57219b7426793879004ef010d2b1ea8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415435"
---
# <a name="text-in-unity"></a><span data-ttu-id="86675-104">在 Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="86675-104">Text in Unity</span></span>

<span data-ttu-id="86675-105">文本是全息版应用中的最重要的组件之一。</span><span class="sxs-lookup"><span data-stu-id="86675-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="86675-106">若要显示的文本在 Unity 中，有三种类型的文本组件可以使用-UI 文本三维文本网格和文本 Mesh Pro。</span><span class="sxs-lookup"><span data-stu-id="86675-106">To display text in Unity, there are three types of text components you can use — UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="86675-107">默认情况下 UI 文本和三维文本网格显示模糊，太大。</span><span class="sxs-lookup"><span data-stu-id="86675-107">By default UI Text and 3D Text Mesh appear blurry and are too big.</span></span> <span data-ttu-id="86675-108">您需要调整几个变量，以获得 sharp、 高质量的文本中 HoloLens 有合理的大小。</span><span class="sxs-lookup"><span data-stu-id="86675-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="86675-109">可以通过应用缩放因子来获取正确的尺寸，使用 UI 文本和三维文本网格组件时，获得更好地呈现质量。</span><span class="sxs-lookup"><span data-stu-id="86675-109">By applying scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="86675-110">![如何获得 sharp 和美观的文本](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="86675-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="86675-111">*在 Unity 中的模糊的默认文本*</span><span class="sxs-lookup"><span data-stu-id="86675-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a><span data-ttu-id="86675-112">使用 Unity 的三维文字 （文本网格） 和 UI 文本</span><span class="sxs-lookup"><span data-stu-id="86675-112">Working with Unity's 3D Text(Text Mesh) and UI Text</span></span>

<span data-ttu-id="86675-113">Unity 假定所有的新元素添加到场景中大小或可以转换为大约 1 米 HoloLens 上的 100%转换小数位数 1 Unity 单元。</span><span class="sxs-lookup"><span data-stu-id="86675-113">Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="86675-114">在字体的情况下的边界框三维 TextMesh 有默认情况下在大约 1 米的高度。</span><span class="sxs-lookup"><span data-stu-id="86675-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="86675-115">![使用 Unity 中的字体](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="86675-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="86675-116">*默认 Unity 三维文字 (文本 Mesh) 占用 1 Unity 单元即 1 米*</span><span class="sxs-lookup"><span data-stu-id="86675-116">*Default Unity 3D Text (Text Mesh) occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="86675-117">大多数的可视化设计器使用点来定义在现实生活中的字体大小。</span><span class="sxs-lookup"><span data-stu-id="86675-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="86675-118">有大约 2835 (2,834.645666399962) 中 1 米的点。</span><span class="sxs-lookup"><span data-stu-id="86675-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="86675-119">根据点系统转换为 1 米以及 Unity 的默认文本 Mesh 字体大小的 13，13 除以 2835年等于 0.0046 (0.004586111116 确切地) 的简单数学开始提供合适的标准扩展 （一些可能想要为 0.005 舍入）。</span><span class="sxs-lookup"><span data-stu-id="86675-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="86675-120">缩放文本对象或对这些值的容器将仅允许 1 对 1 转换字体的大小在设计程序中，但还提供了一个标准，因此您可以在你的体验整个维护一致性。</span><span class="sxs-lookup"><span data-stu-id="86675-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="86675-121">![Unity 3D 文本网格使用不同的字体大小](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="86675-121">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="86675-122">*Unity 3D 文本和 UI 文本的缩放值*</span><span class="sxs-lookup"><span data-stu-id="86675-122">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<span data-ttu-id="86675-123">![Unity 3D 文本网格使用不同的字体大小](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="86675-123">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="86675-124">*Unity 3D 文本网格使用优化的值*</span><span class="sxs-lookup"><span data-stu-id="86675-124">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="86675-125">当将用户界面或画布的基于的文本元素添加到场景中，大小不一致会仍然为更高版本。</span><span class="sxs-lookup"><span data-stu-id="86675-125">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="86675-126">两种大小的差异是大约 1000年%，这会基于 UI 文本组件到 0.00046 (0.0004586111116 确切地) 显示比例系数或 0.0005 的舍入值。</span><span class="sxs-lookup"><span data-stu-id="86675-126">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="86675-127">![每单位值的不同动态像素与 unity UI 文本](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="86675-127">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="86675-128">*使用优化值的 unity UI 文本*</span><span class="sxs-lookup"><span data-stu-id="86675-128">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="86675-129">相应的字体的默认值可能会受到该字体或字体如何导入 Unity 的纹理大小。</span><span class="sxs-lookup"><span data-stu-id="86675-129">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="86675-130">这些测试已执行基于在 Unity 中，默认 Arial 字体，以及其他已导入的一种字体。</span><span class="sxs-lookup"><span data-stu-id="86675-130">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="86675-131">使用文本 Mesh Pro</span><span class="sxs-lookup"><span data-stu-id="86675-131">Working with Text Mesh Pro</span></span>

<span data-ttu-id="86675-132">使用 Unity 的文本 Mesh Pro，可以保护的文本呈现质量。</span><span class="sxs-lookup"><span data-stu-id="86675-132">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="86675-133">它支持无论距离使用清晰的文本轮廓[SDF （签名距离字段）](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)技术。</span><span class="sxs-lookup"><span data-stu-id="86675-133">It supports crisp text outline regardless of the distance using the [SDF(Signed Distance Field)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="86675-134">使用相同的我们上面使用的三维文本网格和 UI 文本的计算方法，我们可以找到正确的缩放值，使用传统版式点。</span><span class="sxs-lookup"><span data-stu-id="86675-134">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find proper scaling values to use conventional typographic Point.</span></span> <span data-ttu-id="86675-135">由于默认三维网格 Pro 文本字体大小 36 所示的 2.5 Unity Unit(2.5m) 边界，我们可以使用缩放值 0.005 使用点大小。</span><span class="sxs-lookup"><span data-stu-id="86675-135">Since the default 3D Text Mesh Pro font with the size 36 shows the bounding of 2.5 Unity Unit(2.5m), we can use scaling value 0.005 to use the Point size.</span></span> <span data-ttu-id="86675-136">文本 Mesh Pro UI 菜单下有边界的 25 Unity Unit(25m) 大小的默认值。</span><span class="sxs-lookup"><span data-stu-id="86675-136">The Text Mesh Pro under UI menu has the default bounding size of 25 Unity Unit(25m).</span></span> <span data-ttu-id="86675-137">这样，我们 0.0005 的缩放值。</span><span class="sxs-lookup"><span data-stu-id="86675-137">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="86675-138">![Unity 3D 文本网格使用不同的字体大小](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="86675-138">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="86675-139">*Unity 3D 文本和 UI 文本的缩放值*</span><span class="sxs-lookup"><span data-stu-id="86675-139">*Scaling values for the Unity 3D Text and UI Text*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="86675-140">建议的文本大小</span><span class="sxs-lookup"><span data-stu-id="86675-140">Recommended text size</span></span>
<span data-ttu-id="86675-141">正如您期望的我们使用一台 PC 或平板电脑设备 （通常为 12 – 32pt) 的类型大小相当小看 2 米的距离。</span><span class="sxs-lookup"><span data-stu-id="86675-141">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="86675-142">这取决于每个字体的特征但一般情况下查看角度和可读性较高的字体高度推荐的最小围绕 0.35°-0.4°/12.21-13.97mm 基于我们用户调查研究。</span><span class="sxs-lookup"><span data-stu-id="86675-142">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="86675-143">而是关于 35 40pt 与上面介绍的缩放因子。</span><span class="sxs-lookup"><span data-stu-id="86675-143">It is about 35-40pt with the scaling factor introduced above.</span></span> 

<span data-ttu-id="86675-144">对于在 0.45m(45cm) 的近交互，最小清晰字体的视角和高度为 0.4 °-0.5 ° / 3.14 – 3.9 mm。</span><span class="sxs-lookup"><span data-stu-id="86675-144">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="86675-145">而是关于 9 12 磅与上面介绍的缩放因子。</span><span class="sxs-lookup"><span data-stu-id="86675-145">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="86675-146">![近和远的交互范围](images/typography-distance-1000px.jpg)
*内容在近和远的交互范围*</span><span class="sxs-lookup"><span data-stu-id="86675-146">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="86675-147">最小清晰的字体大小</span><span class="sxs-lookup"><span data-stu-id="86675-147">The minimum legible font size</span></span>
| <span data-ttu-id="86675-148">距离</span><span class="sxs-lookup"><span data-stu-id="86675-148">Distance</span></span> | <span data-ttu-id="86675-149">视角</span><span class="sxs-lookup"><span data-stu-id="86675-149">Viewing angle</span></span> | <span data-ttu-id="86675-150">文本高度</span><span class="sxs-lookup"><span data-stu-id="86675-150">Text height</span></span> | <span data-ttu-id="86675-151">字体大小</span><span class="sxs-lookup"><span data-stu-id="86675-151">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="86675-152">45 cm （直接操作距离）</span><span class="sxs-lookup"><span data-stu-id="86675-152">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="86675-153">0.4°-0.5°</span><span class="sxs-lookup"><span data-stu-id="86675-153">0.4°-0.5°</span></span> | <span data-ttu-id="86675-154">3.14–3.9mm</span><span class="sxs-lookup"><span data-stu-id="86675-154">3.14–3.9mm</span></span> | <span data-ttu-id="86675-155">8.9–11.13pt</span><span class="sxs-lookup"><span data-stu-id="86675-155">8.9–11.13pt</span></span> |
| <span data-ttu-id="86675-156">2m</span><span class="sxs-lookup"><span data-stu-id="86675-156">2m</span></span> | <span data-ttu-id="86675-157">0.35°-0.4°</span><span class="sxs-lookup"><span data-stu-id="86675-157">0.35°-0.4°</span></span> | <span data-ttu-id="86675-158">12.21–13.97mm</span><span class="sxs-lookup"><span data-stu-id="86675-158">12.21–13.97mm</span></span> | <span data-ttu-id="86675-159">34.63-39.58pt</span><span class="sxs-lookup"><span data-stu-id="86675-159">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="86675-160">轻松清晰的字体大小</span><span class="sxs-lookup"><span data-stu-id="86675-160">The comfortably legible font size</span></span>
| <span data-ttu-id="86675-161">距离</span><span class="sxs-lookup"><span data-stu-id="86675-161">Distance</span></span> | <span data-ttu-id="86675-162">视角</span><span class="sxs-lookup"><span data-stu-id="86675-162">Viewing angle</span></span> | <span data-ttu-id="86675-163">文本高度</span><span class="sxs-lookup"><span data-stu-id="86675-163">Text height</span></span> | <span data-ttu-id="86675-164">字体大小</span><span class="sxs-lookup"><span data-stu-id="86675-164">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="86675-165">45 cm （直接操作距离）</span><span class="sxs-lookup"><span data-stu-id="86675-165">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="86675-166">0.65°-0.8°</span><span class="sxs-lookup"><span data-stu-id="86675-166">0.65°-0.8°</span></span> | <span data-ttu-id="86675-167">5.1-6.3mm</span><span class="sxs-lookup"><span data-stu-id="86675-167">5.1-6.3mm</span></span> | <span data-ttu-id="86675-168">14.47-17.8pt</span><span class="sxs-lookup"><span data-stu-id="86675-168">14.47-17.8pt</span></span> |
| <span data-ttu-id="86675-169">2m</span><span class="sxs-lookup"><span data-stu-id="86675-169">2m</span></span> | <span data-ttu-id="86675-170">0.6°-0.75°</span><span class="sxs-lookup"><span data-stu-id="86675-170">0.6°-0.75°</span></span> | <span data-ttu-id="86675-171">20.9-26.2mm</span><span class="sxs-lookup"><span data-stu-id="86675-171">20.9-26.2mm</span></span> | <span data-ttu-id="86675-172">59.4-74.2pt</span><span class="sxs-lookup"><span data-stu-id="86675-172">59.4-74.2pt</span></span> |

<span data-ttu-id="86675-173">Segoe UI （Windows 默认字体） 非常适合大多数情况。</span><span class="sxs-lookup"><span data-stu-id="86675-173">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="86675-174">但是，避免使用 light 或半浅色字体系列以小的尺寸，由于精简垂直笔画将振动，它将会降低以增强可读性。</span><span class="sxs-lookup"><span data-stu-id="86675-174">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="86675-175">最新版本，如果有足够笔画粗细能正常工作。</span><span class="sxs-lookup"><span data-stu-id="86675-175">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="86675-176">例如，Helvetica，Arial 查看丰富多彩和 HoloLens 中非常清晰的常规或加粗的权重。</span><span class="sxs-lookup"><span data-stu-id="86675-176">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>


<span data-ttu-id="86675-177">![查看角度](images/Text_In_Unity_ViewingAngle.jpg)
*查看距离、 角度和文本的高度*</span><span class="sxs-lookup"><span data-stu-id="86675-177">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="86675-178">尖锐文本呈现质量与正确的维度</span><span class="sxs-lookup"><span data-stu-id="86675-178">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="86675-179">根据这些缩放比例系数，我们创建了[UI 文本和三维文本 Mesh 文本预设](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)。</span><span class="sxs-lookup"><span data-stu-id="86675-179">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="86675-180">开发人员可以利用这些预设可以清晰的文本和一致的字体大小。</span><span class="sxs-lookup"><span data-stu-id="86675-180">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="86675-181">![尖锐文本呈现质量与正确的维度](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="86675-181">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="86675-182">*尖锐文本呈现质量与正确的维度*</span><span class="sxs-lookup"><span data-stu-id="86675-182">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="86675-183">与封闭支持的着色器</span><span class="sxs-lookup"><span data-stu-id="86675-183">Shader with occlusion support</span></span>

<span data-ttu-id="86675-184">Unity 的默认字体材料不支持的阻挡物。</span><span class="sxs-lookup"><span data-stu-id="86675-184">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="86675-185">因此，将默认情况下看到对象后面的文本。</span><span class="sxs-lookup"><span data-stu-id="86675-185">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="86675-186">我们包含了一个简单[支持是封闭的着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)。</span><span class="sxs-lookup"><span data-stu-id="86675-186">We have included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="86675-187">下图显示了与默认字体材料 （左） 文本以及用正确的阻挡物 （右） 的文本。</span><span class="sxs-lookup"><span data-stu-id="86675-187">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="86675-188">![与封闭支持的着色器](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="86675-188">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="86675-189">*与封闭支持的着色器*</span><span class="sxs-lookup"><span data-stu-id="86675-189">*Shader with occlusion support*</span></span>


## <a name="see-also"></a><span data-ttu-id="86675-190">请参阅</span><span class="sxs-lookup"><span data-stu-id="86675-190">See also</span></span>
* [<span data-ttu-id="86675-191">在 MRTK 文本预设</span><span class="sxs-lookup"><span data-stu-id="86675-191">Text Prefab in the MRTK</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="86675-192">版式</span><span class="sxs-lookup"><span data-stu-id="86675-192">Typography</span></span>](typography.md)

 
