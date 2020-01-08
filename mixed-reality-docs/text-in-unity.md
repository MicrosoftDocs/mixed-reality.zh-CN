---
title: Unity 中的文本
description: 若要在 Unity 中显示文本，可以使用两种类型的文本组件： UI 文本和三维文本网格。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality，设计，控件，字体，版式，ui，ux
ms.openlocfilehash: 69b8a4bca42f3b6177a276d7773e5f1cd599d629
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597660"
---
# <a name="text-in-unity"></a><span data-ttu-id="cef38-104">Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="cef38-104">Text in Unity</span></span>

<span data-ttu-id="cef38-105">文本是全息应用中最重要的组件之一。</span><span class="sxs-lookup"><span data-stu-id="cef38-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="cef38-106">若要在 Unity 中显示文本，可使用三种类型的文本组件： UI 文本、三维文本网格和文本网格 Pro。</span><span class="sxs-lookup"><span data-stu-id="cef38-106">To display text in Unity, there are three types of text components you can use — UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="cef38-107">默认情况下，UI 文本和3D 文本网格显示模糊并且太大。</span><span class="sxs-lookup"><span data-stu-id="cef38-107">By default, UI Text and 3D Text Mesh appear blurry and are too big.</span></span> <span data-ttu-id="cef38-108">需要调整几个变量，以获取在 HoloLens 中具有可管理的大小的高质量文本。</span><span class="sxs-lookup"><span data-stu-id="cef38-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="cef38-109">通过在使用 UI 文本和3D 文本网格组件时应用缩放因子以获取适当的维度，可以获得更好的呈现质量。</span><span class="sxs-lookup"><span data-stu-id="cef38-109">By applying a scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="cef38-110">![如何获取明锐而漂亮的文本](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="cef38-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="cef38-111">*Unity 中的默认文本模糊*</span><span class="sxs-lookup"><span data-stu-id="cef38-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a><span data-ttu-id="cef38-112">使用 Unity 的3D 文本（文本网格）和 UI 文本</span><span class="sxs-lookup"><span data-stu-id="cef38-112">Working with Unity's 3D Text (Text Mesh) and UI Text</span></span>

<span data-ttu-id="cef38-113">Unity 假设添加到场景中的所有新元素都是大小为1个 Unity 单位，或100% 的转换比例，这将转换为在 HoloLens 上约1米。</span><span class="sxs-lookup"><span data-stu-id="cef38-113">Unity assumes that all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="cef38-114">对于字体，默认情况下，3D TextMesh 的边界框在大约1米的高度内进入。</span><span class="sxs-lookup"><span data-stu-id="cef38-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="cef38-115">![在 Unity 中使用字体](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="cef38-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="cef38-116">*默认 Unity 3D 文本（文本网格）占用1个的 Unity 单元*</span><span class="sxs-lookup"><span data-stu-id="cef38-116">*Default Unity 3D Text (Text Mesh) occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="cef38-117">大多数可视化设计器使用点来定义真实环境中的字体大小。</span><span class="sxs-lookup"><span data-stu-id="cef38-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="cef38-118">1米内有大约2835（2，834.645666399962）点。</span><span class="sxs-lookup"><span data-stu-id="cef38-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="cef38-119">根据点系统转换为1米和 Unity 的默认文本网格字体大小13，将13除以2835的简单数学计算为0.0046 （0.004586111116），这将提供一种开始良好的标准缩放（某些可能需要舍入到0.005）。</span><span class="sxs-lookup"><span data-stu-id="cef38-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) which provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="cef38-120">在设计程序中，将文本对象或容器缩放为这些值不仅会允许1:1 转换字体大小，而且还可以提供标准，以便您可以保持整个体验的一致性。</span><span class="sxs-lookup"><span data-stu-id="cef38-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="cef38-121">![具有不同字体大小的 Unity 3D 文本网格](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="cef38-121">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="cef38-122">*Unity 3D 文本和 UI 文本的缩放值*</span><span class="sxs-lookup"><span data-stu-id="cef38-122">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<br>

<span data-ttu-id="cef38-123">![具有不同字体大小的 Unity 3D 文本网格](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="cef38-123">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="cef38-124">*包含优化值的 Unity 3D 文本网格*</span><span class="sxs-lookup"><span data-stu-id="cef38-124">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="cef38-125">将基于 UI 或画布的文本元素添加到场景时，大小差异仍为大于。</span><span class="sxs-lookup"><span data-stu-id="cef38-125">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="cef38-126">这两种大小的差异大约为1000%，这会使基于 UI 的文本组件的缩放因子为0.00046 （0.0004586111116 为精确）或0.0005 作为舍入值。</span><span class="sxs-lookup"><span data-stu-id="cef38-126">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="cef38-127">每个单位值 ![具有不同动态像素的 Unity UI 文本](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="cef38-127">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="cef38-128">*包含优化值的 Unity UI 文本*</span><span class="sxs-lookup"><span data-stu-id="cef38-128">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="cef38-129">任何字体的默认值都可能受该字体的纹理大小或字体导入到 Unity 的方式影响。</span><span class="sxs-lookup"><span data-stu-id="cef38-129">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="cef38-130">这些测试是根据 Unity 中默认的 Arial 字体以及另一个导入的字体来执行的。</span><span class="sxs-lookup"><span data-stu-id="cef38-130">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="cef38-131">使用文本网格 Pro</span><span class="sxs-lookup"><span data-stu-id="cef38-131">Working with Text Mesh Pro</span></span>

<span data-ttu-id="cef38-132">通过 Unity 的文本网格 Pro，可以保护文本呈现质量。</span><span class="sxs-lookup"><span data-stu-id="cef38-132">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="cef38-133">它支持简洁文本轮廓，而不考虑使用[带符号距离字段（.sdf）](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)技术的距离。</span><span class="sxs-lookup"><span data-stu-id="cef38-133">It supports crisp text outlines regardless of the distance using the [Signed Distance Field (SDF)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="cef38-134">使用我们在上面用于3D 文本网格和 UI 文本的相同计算方法，我们可以找到适当的缩放值，以便与传统排字点一起使用。</span><span class="sxs-lookup"><span data-stu-id="cef38-134">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find the proper scaling values to use with conventional typographic points.</span></span> <span data-ttu-id="cef38-135">由于大小为36的默认3D 文本网格 Pro 字体的边界大小为 2.5 Unity 单位（2.5 m），因此我们可以使用 "0.005" 的缩放值获取点大小。</span><span class="sxs-lookup"><span data-stu-id="cef38-135">Since the default 3D Text Mesh Pro font with the size of 36 has a bounding size of 2.5 Unity units (2.5m), we can use a scaling value of 0.005 to get the point size.</span></span> <span data-ttu-id="cef38-136">UI 菜单下的文本网格 Pro 的默认边界大小为25个 Unity 单位（25m）。</span><span class="sxs-lookup"><span data-stu-id="cef38-136">The Text Mesh Pro under the UI menu has a default bounding size of 25 Unity units (25m).</span></span> <span data-ttu-id="cef38-137">这为缩放值提供了0.0005。</span><span class="sxs-lookup"><span data-stu-id="cef38-137">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="cef38-138">![具有不同字体大小的 Unity 3D 文本网格](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="cef38-138">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="cef38-139">*Unity 3D 文本和 UI 文本的缩放值*</span><span class="sxs-lookup"><span data-stu-id="cef38-139">*Scaling values for the Unity 3D Text and UI Text*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="cef38-140">建议的文本大小</span><span class="sxs-lookup"><span data-stu-id="cef38-140">Recommended text size</span></span>
<span data-ttu-id="cef38-141">正如你所料，在电脑或平板电脑设备上使用的类型大小（通常介于12到32pt 之间）看上去相当小，距离为2米。</span><span class="sxs-lookup"><span data-stu-id="cef38-141">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="cef38-142">这取决于每种字体的特征，但通常情况下，建议的最小查看角度和清晰度的字体高度基于用户研究研究的0.35 °/12.21-13.97mm。</span><span class="sxs-lookup"><span data-stu-id="cef38-142">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="cef38-143">大约有35个40pt，其中包含上述缩放系数。</span><span class="sxs-lookup"><span data-stu-id="cef38-143">It is about 35-40pt with the scaling factor introduced above.</span></span> 

<span data-ttu-id="cef38-144">对于 0.45 m （45cm）的接近交互，最小清晰字体的查看角度和高度为0.4 °-0.5 °/3.14 –3.9 毫米。</span><span class="sxs-lookup"><span data-stu-id="cef38-144">For the near interaction at 0.45m (45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="cef38-145">它大约为 9-12pt，其中包含上述缩放系数。</span><span class="sxs-lookup"><span data-stu-id="cef38-145">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="cef38-146">*在近和远交互范围](images/typography-distance-1000px.jpg)
内容*![近和远交互范围</span><span class="sxs-lookup"><span data-stu-id="cef38-146">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="cef38-147">最小清晰字体大小</span><span class="sxs-lookup"><span data-stu-id="cef38-147">The minimum legible font size</span></span>
| <span data-ttu-id="cef38-148">距离</span><span class="sxs-lookup"><span data-stu-id="cef38-148">Distance</span></span> | <span data-ttu-id="cef38-149">查看角度</span><span class="sxs-lookup"><span data-stu-id="cef38-149">Viewing angle</span></span> | <span data-ttu-id="cef38-150">文本高度</span><span class="sxs-lookup"><span data-stu-id="cef38-150">Text height</span></span> | <span data-ttu-id="cef38-151">字体大小</span><span class="sxs-lookup"><span data-stu-id="cef38-151">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="cef38-152">45cm （直接操作距离）</span><span class="sxs-lookup"><span data-stu-id="cef38-152">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="cef38-153">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="cef38-153">0.4°-0.5°</span></span> | <span data-ttu-id="cef38-154">3.14 –3.9 毫米</span><span class="sxs-lookup"><span data-stu-id="cef38-154">3.14–3.9mm</span></span> | <span data-ttu-id="cef38-155">8.9-11.13 pt</span><span class="sxs-lookup"><span data-stu-id="cef38-155">8.9–11.13pt</span></span> |
| <span data-ttu-id="cef38-156">2m</span><span class="sxs-lookup"><span data-stu-id="cef38-156">2m</span></span> | <span data-ttu-id="cef38-157">0.35 °0.4 °</span><span class="sxs-lookup"><span data-stu-id="cef38-157">0.35°-0.4°</span></span> | <span data-ttu-id="cef38-158">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="cef38-158">12.21–13.97mm</span></span> | <span data-ttu-id="cef38-159">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="cef38-159">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="cef38-160">可读性更清晰的字号</span><span class="sxs-lookup"><span data-stu-id="cef38-160">The comfortably legible font size</span></span>
| <span data-ttu-id="cef38-161">距离</span><span class="sxs-lookup"><span data-stu-id="cef38-161">Distance</span></span> | <span data-ttu-id="cef38-162">查看角度</span><span class="sxs-lookup"><span data-stu-id="cef38-162">Viewing angle</span></span> | <span data-ttu-id="cef38-163">文本高度</span><span class="sxs-lookup"><span data-stu-id="cef38-163">Text height</span></span> | <span data-ttu-id="cef38-164">字体大小</span><span class="sxs-lookup"><span data-stu-id="cef38-164">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="cef38-165">45cm （直接操作距离）</span><span class="sxs-lookup"><span data-stu-id="cef38-165">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="cef38-166">0.65 °0.8 °</span><span class="sxs-lookup"><span data-stu-id="cef38-166">0.65°-0.8°</span></span> | <span data-ttu-id="cef38-167">5.1-6.3 毫米</span><span class="sxs-lookup"><span data-stu-id="cef38-167">5.1-6.3mm</span></span> | <span data-ttu-id="cef38-168">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="cef38-168">14.47-17.8pt</span></span> |
| <span data-ttu-id="cef38-169">2m</span><span class="sxs-lookup"><span data-stu-id="cef38-169">2m</span></span> | <span data-ttu-id="cef38-170">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="cef38-170">0.6°-0.75°</span></span> | <span data-ttu-id="cef38-171">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="cef38-171">20.9-26.2mm</span></span> | <span data-ttu-id="cef38-172">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="cef38-172">59.4-74.2pt</span></span> |

<span data-ttu-id="cef38-173">Segoe UI （Windows 的默认字体）在大多数情况下都适用。</span><span class="sxs-lookup"><span data-stu-id="cef38-173">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="cef38-174">不过，请避免使用较小尺寸的轻型或半字形系列，因为精简垂直笔划将振动，并将降低清晰度。</span><span class="sxs-lookup"><span data-stu-id="cef38-174">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="cef38-175">具有足够笔划粗细的新式字体很好地运行。</span><span class="sxs-lookup"><span data-stu-id="cef38-175">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="cef38-176">例如，Arial 和 Arial 外观丰富多彩，在 HoloLens 中以常规或粗体权重非常清晰。</span><span class="sxs-lookup"><span data-stu-id="cef38-176">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>


<span data-ttu-id="cef38-177">![查看角度](images/Text_In_Unity_ViewingAngle.jpg)
*查看距离、角度和文本高度*</span><span class="sxs-lookup"><span data-stu-id="cef38-177">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="cef38-178">用适当的尺寸锐化文本呈现质量</span><span class="sxs-lookup"><span data-stu-id="cef38-178">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="cef38-179">根据这些缩放因素，我们已[使用 UI 文本和3D 文本网格创建了文本 prototyping](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)。</span><span class="sxs-lookup"><span data-stu-id="cef38-179">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="cef38-180">开发人员可以使用这些 prototyping 来获得清晰的文本和一致的字体大小。</span><span class="sxs-lookup"><span data-stu-id="cef38-180">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="cef38-181">用适当的尺寸 ![清晰的文本渲染质量](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="cef38-181">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="cef38-182">*用适当的尺寸锐化文本呈现质量*</span><span class="sxs-lookup"><span data-stu-id="cef38-182">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="cef38-183">具有封闭支持的着色器</span><span class="sxs-lookup"><span data-stu-id="cef38-183">Shader with occlusion support</span></span>

<span data-ttu-id="cef38-184">Unity 的默认字体材料不支持封闭。</span><span class="sxs-lookup"><span data-stu-id="cef38-184">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="cef38-185">因此，默认情况下，你会看到对象后面的文本。</span><span class="sxs-lookup"><span data-stu-id="cef38-185">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="cef38-186">我们包含了一个[支持封闭的简单着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)。</span><span class="sxs-lookup"><span data-stu-id="cef38-186">We have included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="cef38-187">下图显示了文本，其中包含默认字体材料（左侧）和具有适当封闭（右）的文本。</span><span class="sxs-lookup"><span data-stu-id="cef38-187">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="cef38-188">具有封闭支持的 ![着色器](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="cef38-188">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="cef38-189">*具有封闭支持的着色器*</span><span class="sxs-lookup"><span data-stu-id="cef38-189">*Shader with occlusion support*</span></span>


## <a name="see-also"></a><span data-ttu-id="cef38-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cef38-190">See also</span></span>
* [<span data-ttu-id="cef38-191">MRTK 中的文本 Prefab</span><span class="sxs-lookup"><span data-stu-id="cef38-191">Text Prefab in the MRTK</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="cef38-192">版式</span><span class="sxs-lookup"><span data-stu-id="cef38-192">Typography</span></span>](typography.md)

 
